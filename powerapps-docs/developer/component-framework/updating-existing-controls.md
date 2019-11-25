---
title: Aktualisierung vorhandener Codekomponenten mit PowerApps component framework-Tools | Microsoft-Dokumentation
description: Aktualisieren von Komponenten mit dem PowerApps component framework-Tools
keywords: PowerApps component framework, Code-Komponente, Komponente Framework
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2cbf58a-9112-45c2-b823-2c07a310714c
ms.openlocfilehash: 05e32fb7e098dad3aabf36f2efdaf311c1bea327
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748778"
---
# <a name="update-existing-code-components"></a>Aktualisieren vorhandener Codekomponenten 

Wenn Sie ein Teilnehmer der Privaten Vorschau vom PowerApps component framework für modellgesteuerte Apps sind und bereits Codekomponenten erstellt haben, müssen Sie einige kleinere Updates vornehmen, um sie mit den neuen ALM-zentrierten Projektstrukturen kompatibel zu machen. 

Einige Änderungen sind erforderlich, um das neue PowerApps CLI-Tooling mit Ihren bestehenden PowerApps component framework-Code Komponenten zu verwenden.

> [!NOTE]
> Dieses Thema ist nur zum Aktualisieren von Codekomponenten für modellgesteuerte Apps anwendbar, da die PowerApps CLI-Tools nicht bei der Privaten Vorschau für die modellgesteuerten Apps verfügbar sind.  

## <a name="creating-an-empty-project"></a>Erstellen eines leeren Projekts

Verwenden Sie die PowerApps CLI, um ein neues leeres Projekt für Ihre Codekomponente zu erstellen. Weitere Informationen: [Erstellen von Komponenten mit Hilfe von Tools](create-custom-controls-using-pcf.md)

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
 
   - Aktualisieren Sie das Versionstag in `pcfproj`, das sich innerhalb Ihres PowerApps component framework-Projektordners befindet:

      ```XML
      <Packagereference Include="Microsoft.PowerApps.MSBuild.Pcf" Version="1.*"/>
      ```
   - Aktualisieren Sie das Versionstag in `cdsproj`, das sich innerhalb Ihres Lösungsprojektordners befindet:

      ```XML
      <Packagereference Include="Microsoft.PowerApps.MSBuild.Solution" Version="1.*"/>
      ```

      > [!NOTE] 
      > Nachdem Sie die oben beschriebenen Änderungen vorgenommen haben, führen Sie den Befehl `msbuild /t:restore` aus, um Ihr Projekt auf die korrekte Version zu aktualisieren.


   - Aktualisieren Sie das Versions-Tag in Ihrer `package.json`-Datei, die sich in Ihrem Projektordner für das PowerApps component framework befindet:

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

Legacy-Projekte erfordern die manuelle Erstellung und Bearbeitung einer `inputsOutputs.d.ts`-Tippdatei, die sich typischerweise unter dem Unterordner `private_typing` befindet. Das PowerApps CLI-Tooling generiert diese Datei nun beim Build automatisch. 

Code-gen stellt sicher, dass die im Quellcode der Komponente verwendeten `type`-Definitionen mit in der Manifestdatei der Komponente definierten `types` synchron bleiben.

Die Typisierungsdatei wird zu `ManifestTypes.d.ts` umbenannt und wird jetzt in einen Unterordner namens `generated` generiert. Außerdem werden die Typen `InputsOutputs.IInputBag` und `InputsOutputs.IOutputBag` zu `IInputs` und `IOutputs` umbenannt.

So verwenden Sie eine neue Typisierungsdatei:

1. Importieren Sie die neue `ManifestTypes.d.ts`-Datei, indem Sie die folgende Zeile oben in der Komponentenquelldatei hinzufügen:

    import { IInputs, IOutputs } from `./generated/ManifestTypes`.
2. Nennen Sie alle Verweise von **InputsOutputs.IInputBag** in **IInputs** um.
3. Nennen Sie alle Verweise von **InputsOutputs.IOutputBag** in **IOutputs** um.
4. Erstellen Sie das Projekt, um mithilfe des Befehls `npm run build` eine neue **ManifestTypes.d.ts**-Datei zu generieren.

## <a name="troubleshooting-and-workarounds"></a>Fehlerbehebung und Workarounds

1. Wenn Sie eine 1ES-Benachrichtigung erhalten, in der Sie gefragt werden, wie PCF-Skripte verwendet werden, beachten Sie, dass diese Skripte nur zum Erstellen der Codekomponenten verwendet werden, aber nicht von der resultierenden Komponente gebündelt oder verwendet werden.  
2. Wenn Sie zuvor eine Codekomponente mit Hilfe der Toolversion 0.1.817.1 oder früher erstellt haben und sicherstellen möchten, dass die aktuellen Build- und Debug-Module verwendet werden, aktualisieren Sie package.json wie gezeigt:
   
    ```JSON
     "dependencies": { "@types/node": "^10.12.18", "@types/powerapps-component-framework": "1.1.0"}, "devDependencies": { "pcf-scripts": "~0", "pcf-start": "~0" } 
    ```
3. Dem Benutzer wird die Fehlermeldung `Failed to retrieve information about Microsoft.PowerApps.MSBuild.Pcf from remote source <Feed Url>` angezeigt, wenn der Build aufgrund von Autorisierungsproblemen fehlschlägt. Hierfür gibt es eine Problemumgehung:

   - Öffnen Sie die Konfigurationsdatei NuGet von **%APPDATA%\NuGet**. Der Feed, von dem der Benutzer den Fehler erhält, sollte in dieser Datei vorhanden sein. 
   - Entfernen Sie den Feed aus der NuGet.Config-Datei oder erstellen Sie ein PAT-Token und fügen sie es der NuGet.Config-Datei hinzu. Beispiel:

     ```XML
     <?xml version="1.0" encoding="utf-8"?>  
     <configuration>  
     <packageSources>  
         <add key="CRMSharedFeed" value="https://dynamicscrm.pkgs.visualstudio.com/_packaging/CRMSharedFeed/nuget/v3/index.json" />  
      </packageSources>  
     <packageSourceCredentials>  
      <CRMSharedFeed>  
      <add key="Username" value="anything" />  
      <add key="Password" value="User PAT" />  
    </CRMSharedFeed>  
     </packageSourceCredentials>  
   </configuration>
     ```

### <a name="see-also"></a>Siehe auch

[Begrenzungen des PowerApps component framework](limitations.md)<br/>
[PowerApps component framework API-Referenz](reference/index.md)<br/>
[Übersicht über das PowerApps component framework](overview.md)
