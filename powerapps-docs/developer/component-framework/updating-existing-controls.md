---
title: Aktualisierung vorhandener Codekomponenten mit Power Apps component framework-Tools | Microsoft-Dokumentation
description: Aktualisieren von Komponenten mit dem Power Apps component framework-Tools
keywords: Power Apps component framework, Code-Komponente, Komponente Framework
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2cbf58a-9112-45c2-b823-2c07a310714c
ms.openlocfilehash: 0f779dbddedbf76b3c2e7f55d314a9f0fda30332
ms.sourcegitcommit: 212bd841595db0d6f41002f7ff9a1c8eb33a0724
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2019
ms.locfileid: "2909087"
---
# <a name="update-existing-code-components"></a>Aktualisieren vorhandener Codekomponenten 

Wenn Sie ein Teilnehmer der Privaten Vorschau vom Power Apps component framework für modellgesteuerte Apps sind und bereits Codekomponenten erstellt haben, müssen Sie einige kleinere Updates vornehmen, um sie mit den neuen ALM-zentrierten Projektstrukturen kompatibel zu machen. 

Einige Änderungen sind erforderlich, um das neue Power Apps CLI-Tooling mit Ihren bestehenden Power Apps component framework-Code Komponenten zu verwenden.

> [!NOTE]
> Dieses Thema ist nur zum Aktualisieren von Codekomponenten für modellgesteuerte Apps anwendbar, da die Power Apps CLI-Tools nicht bei der Privaten Vorschau für die modellgesteuerten Apps verfügbar sind.  

## <a name="creating-an-empty-project"></a>Erstellen eines leeren Projekts

Verwenden Sie die Power Apps CLI, um ein neues leeres Projekt für Ihre Codekomponente zu erstellen. Weitere Informationen: [Erstellen von Komponenten mit Hilfe von Tools](create-custom-controls-using-pcf.md)

Nachdem das Projekt erstellt wurde, migrieren Sie die Codekomponentenquelle zum neuen Projekt:

1. Kopieren oder ersetzen Sie die Komponenten-Quelldatei aus der alten Quelldatei in **index.ts**.
2. Kopieren Sie die Inhalte von **ControlManifest.xml** in die **ControlManifest.Input.xml**-Datei oder ersetzen Sie .
3. Kopieren Sie alle weiteren Zusatzkomponentenressourcen wie CSS, RESX oder IMG in den entsprechenden Unterordner des alten Projekts zum neuen Projekt.

## <a name="updating-manifest-file"></a>Aktualisieren der Manifestdatei

Die Datei `ControlManifest.xml`, die die Eigenschaften der Codekomponente definiert, wird durch die Datei `ControlManifest.Input.xml` ersetzt. Hierbei sollte es nur geringe Änderung am Schema zwischen den zwei Dateien geben.

Es gibt jedoch einige wichtige semantische Änderungen:

1. Der `code`-Ressourceneintrag muss jetzt auf die vorkompilierte Quelldatei der Codekomponente verweisen. Der Dateiname ist standardmäßig **index.ts**.

   Wenn Ihre Komponentenquelle in einer Datei mit dem Namen `MyControl.ts` implementiert wird, dann muss der Eintrag `code` in `ControlManifest.Input.xml` auf diese Datei verweisen. Die `code`-Datei muss auch eine gültige TypeScript-Datei sein. Dies steht im Gegensatz zu vorherigen Manifestdateien, die die kompilierte JS-Ausgabedatei im `code`-Eintrag angegeben haben.
2. Das `path`-Attribut vom Ressourcenelement wie `code` oder `css` verweist jetzt auf den lokalen Pfad zur Datei auf einem Datenträger. Beispiel:

    ```XML
   <resources>
    <css path="css/YourControlName" order="1"/>
    </resources>
    ```

Beim `path`-Attribut oben wird angegeben, dass sich die `YourControlName.css`-Datei im Unterordner `css` relativ zum aktuellen Verzeichnis befindet, wo sich `ControlManifest.Input.xml` auf dem Datenträger befindet.

Aktualisieren Sie die ControlManifest.Input.xml-Dateien wie folgt:

1. Bearbeiten Sie den `code`-Eintrag in `ControlManifest.Input.xml` zur vorkompilierten Quelldatei der Codekomponente (in der Regel ist dies "index.ts").
2. Bearbeiten Sie sämtliche Pfade der Ressourcen, um korrekt auf die relativen Pfade zu den Dateien auf dem Datenträger zu verweisen.

## <a name="updating-the-project-files"></a>Aktualisierung der Projektdateien

Wenn Sie eine Komponente mit der älteren Tool-Version erstellt haben und die neuesten Funktionen nutzen möchten, stellen Sie sicher, die Projektdateien wie hier gezeigt zu aktualisieren:

1. Aktualisieren Sie Ihre bestehenden Projekte, um die neuesten Module zu verwenden.
 
   - Aktualisieren Sie das Versionstag in `pcfproj`, das sich innerhalb Ihres Power Apps component framework-Projektordners befindet:

      ```XML
      <Packagereference Include="Microsoft.PowerApps.MSBuild.Pcf" Version="1.*"/>
      ```
   - Aktualisieren Sie das Versionstag in `cdsproj`, das sich innerhalb Ihres Lösungsprojektordners befindet:

      ```XML
      <Packagereference Include="Microsoft.PowerApps.MSBuild.Solution" Version="1.*"/>
      ```

      > [!NOTE] 
      > Nachdem Sie die oben beschriebenen Änderungen vorgenommen haben, führen Sie den Befehl `msbuild /t:restore` aus, um Ihr Projekt auf die korrekte Version zu aktualisieren.


   - Aktualisieren Sie das Versions-Tag in Ihrer `package.json`-Datei, die sich in Ihrem Projektordner für das Power Apps component framework befindet:

      ```JSON
      "devDependencies":{
       "pcf-scripts": "^1",
       "pcf-start": "^1"
          }
      ```
     > [!NOTE]
     > Nachdem Sie die oben beschriebenen Änderungen vorgenommen haben, führen Sie den Befehl `npm update` aus, um Ihr Projekt auf die korrekte Version zu aktualisieren.

2. Wenn Sie bereits ein Auth-Profil erstellt haben, müssen Sie es neu erstellen. Dies liegt daran, dass dem Profil eine neue Eigenschaft hinzugefügt wurde, um nicht-öffentliche Clouds zu unterstützen. Sie können dies tun, indem Sie:
 
    - den Befehl `pac auth clear` ausführen
    - den Befehl `pac auth create --url <your org url>` ausführen

## <a name="updating-your-project-with-the-latest-node-modules"></a>Aktualisierung Ihres Projekts mit den neuesten Knotenmodulen

Bei älteren Projekten müssen die neuesten npm-Module abgerufen werden, um die Vorteile der neuesten CLI-Funktionen nutzen zu können. Um die Knotenmodule, die Sie zuvor heruntergeladen haben, zu aktualisieren, gehen Sie zum Projektverzeichnis in der Entwicklereingabeaufforderung und führen Sie den Befehl `npm update` aus. 

## <a name="using-es6-module-syntax"></a>Verwenden der ES6-Modulsyntax

Die Erstellungstools erwarten, dass die Komponentenquelle mithilfe des Standard-ES6-Modulformats exportiert wird. Vorgängerkomponenten werden normalerweise als interne Module exportiert (auch als „Namespaces“ bekannt). Die Quelldatei der Komponente muss wie folgt geändert werden, um sie an die neuen Build-Tools anzupassen.

1. Öffnen Sie die Quelldatei, die die Codekomponente implementiert (z. B. index.ts).
2. Verwenden Sie ES6-Exportsyntax, indem Sie die Moduldeklaration entfernen.

     Vor:
     ```TypeScript
     module SampleNamespace
     {
    export class TSLinearInputControl implements ComponentFramework.StandardControl<InputsOutputs.IInputBag, InputsOutputs.IOutputBag> {
          <your class implementation>
           }
            }
     
      ```
    Nach:
    ```TypeScript
     export class YourControlName implements ComponentFramework.StandardControl<IInputs, IOutputs> { 
          <your class implementation>
          }
   ```

## <a name="using-generated-manifest-typing-file"></a>Verwenden der generierten Manifesttypisierungsdatei

Legacy-Projekte erfordern die manuelle Erstellung und Bearbeitung einer `inputsOutputs.d.ts`-Tippdatei, die sich typischerweise unter dem Unterordner `private_typing` befindet. Das Power Apps CLI-Tooling generiert diese Datei nun beim Build automatisch. 

Code-gen stellt sicher, dass die im Quellcode der Komponente verwendeten `type`-Definitionen mit in der Manifestdatei der Komponente definierten `types` synchron bleiben.

Die Typisierungsdatei wird zu `ManifestTypes.d.ts` umbenannt und wird jetzt in einen Unterordner namens `generated` generiert. Außerdem werden die Typen `InputsOutputs.IInputBag` und `InputsOutputs.IOutputBag` zu `IInputs` und `IOutputs` umbenannt.

So verwenden Sie eine neue Typisierungsdatei:

1. Importieren Sie die neue `ManifestTypes.d.ts`-Datei, indem Sie die folgende Zeile oben in der Komponentenquelldatei hinzufügen:

    import { IInputs, IOutputs } from `./generated/ManifestTypes`.
2. Nennen Sie alle Verweise von **InputsOutputs.IInputBag** in **IInputs** um.
3. Nennen Sie alle Verweise von **InputsOutputs.IOutputBag** in **IOutputs** um.
4. Erstellen Sie das Projekt, um mithilfe des Befehls `npm run build` eine neue **ManifestTypes.d.ts**-Datei zu generieren.


### <a name="see-also"></a>Siehe auch

[Begrenzungen des Power Apps component framework](limitations.md)<br/>
[Power Apps component framework-API-Referenz](reference/index.md)<br/>
[Power Apps component framework Übersicht](overview.md)
