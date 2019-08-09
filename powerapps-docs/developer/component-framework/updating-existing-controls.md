---
title: Aktualisieren Sie vorhandene benutzerdefinierte Komponenten mit PowerApps Komponentenframework-Tooling| Microsoft Docs
description: Aktualisieren von Komponenten mit PowerApps Komponentenframework-Tooling
keywords: 'PowerApps Komponentenframework, Benutzerdefinierte Komponente, Komponentenframework'
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2cbf58a-9112-45c2-b823-2c07a310714c
---
# <a name="updating-existing-custom-components"></a>Aktualisieren vorhandener benutzerdefinierter Komponenten 

[!INCLUDE[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Wenn Sie ein Teilnehmer an der privaten Vorschau von PowerApps Komponentenframework sind und bereits benutzerdefinierte Komponenten erstellt haben, müssen Sie einige kleinere Updates vornehmen, damit sie mit den neuen ALM-orientierten Projektstrukturen kompatibel sind. Um die neuen Erstellungstools von PowerApps Komponentenframework mit Ihrer vorhandenen benutzerdefinierten Komponentenquelle von PowerApps Komponentenframework zu verwenden, sind einige Änderungen erforderlich.

## <a name="creating-an-empty-project"></a>Erstellen eines leeren Projekts

Verwenden Sie die PowerApps-CLI, um ein neues leeres Projekt für Ihre benutzerdefinierte Komponente zu erstellen. Weitere Informationen [Erstellen von Komponenten mithilfe von Tooling](create-custom-controls-using-pcf.md)
Nachdem das Projekt erstellt wurde, migrieren Sie die benutzerdefinierte Komponentenquelle zum neuen Projekt:

1. Kopieren Sie die Komponentenquelle aus der alten Quelldatei in **index.ts** oder ersetzen Sie sie.
2. Kopieren Sie die Inhalte von **ControlManifest.xml** in die **ControlManifest.Input.xml**-Datei oder ersetzen Sie .
3. Kopieren Sie alle weiteren Zusatzkomponentenressourcen wie css, resx, img in den entsprechenden Unterordner des alten Projekts zum neuen Projekt.

## <a name="updating-manifest-file"></a>Aktualisieren der Manifestdatei

Die `ControlManifest.xml`-Datei, die die benutzerdefinierten Komponenteneigenschaften definiert, wurde durch eine `ControlManifest.Input.xml`-Datei ersetzt. Hierbei sollte es nur geringe Änderung am Schema zwischen den zwei Dateien geben.
Es gibt einige wichtige semantische Änderungen.

1. Der `code`-Ressourceneintrag muss jetzt auf die vorkompilierte Quelldatei der benutzerdefinierten Komponente weisen. Der Dateiname lautet standardmäßig **index.ts**
Wenn Ihre Komponentenquelle in einer Datei mit dem Namen `MyControl.ts` implementiert wird, dann muss der Eintrag `code` in `ControlManifest.Input.xml` auf diese Datei verweisen. Die `code`-Datei muss auch eine gültige Typescript-Datei sein. Dies steht im Gegensatz zu vorherigen Manifestdateien, die die kompilierte JS-Ausgabedatei im `code`-Eintrag angegeben haben.
2. Das `path`-Attribut vom Ressourcenelement wie `code` oder `css` verweist jetzt auf den lokalen Pfad zur Datei auf einem Datenträger. Beispielsweise

    ```XML
   <resources>
    <css path="css/YourControlName" order="1"/>
    </resources>
    ```

Beim `path`-Attribut oben wird angegeben, dass sich die `YourControlName.css`-Datei im Unterordner `css` relativ zum aktuellen Verzeichnis befindet, wo sich `ControlManifest.Input.xml` auf dem Datenträger befindet.
Aktualisieren Sie die ControlManifest.Input.xml-Dateien wie folgt:

1. Bearbeiten Sie den `code`-Eintrag in `ControlManifest.Input.xml` zur vorkompilierten Quelldatei der benutzerdefinierten Komponente (in der Regel ist dies "index.ts").
2. Bearbeiten Sie sämtliche Pfade der Ressourcen, um korrekt auf die relativen Pfade zu den Dateien auf dem Datenträger zu verweisen.

## <a name="using-es6-module-syntax"></a>Verwenden der ES6-Modulsyntax

Die Erstellungstools erwarten, dass die Komponentenquelle mithilfe des Standard-ES6-Modulformats exportiert wird. Vorherige Steuerelemente werden in der Regel auch als interne Module exportiert (Namespaces). Hinsichtlich der neuen Erstellungstools muss die Komponentenquelle wie folgt geändert werden.

1. Öffnen Sie die Quelldatei, die die benutzerdefinierte Komponente implementiert (z. B. index.ts).
2. Verwenden Sie ES6-Exportsyntax, indem Sie die Moduldeklaration entfernen

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

Bei Vorgängerprojekten muss manuell eine `inputsOutputs.d.ts`-Typisierungsdatei erstellt und bearbeitet werden. Diese Datei befindet sich normalerweise im Unterordner `private_typing`. Das neue Tooling generiert jetzt diese Datei automatisch beim Build. Code-GEN stellt sicher, dass `type`-Definitionen, die in der Komponentenquelle verwendet werden, synchron mit den `types` bleiben, die in der Komponentenmanifestdatei definiert werden.  
Die Typisierungsdatei wird zu `ManifestTypes.d.ts` umbenannt und wird jetzt in einen Unterordner namens `generated` generiert. Außerdem werden die Typen `InputsOutputs.IInputBag` und `InputsOutputs.IOutputBag` zu `IInputs` und `IOutputs` umbenannt.
So verwenden Sie eine neue Typisierungsdatei:

1. Importieren Sie die neue `ManifestTypes.d.ts`-Datei, indem Sie die folgende Zeile oben in der Komponentenquelldatei hinzufügen: import { IInputs, IOutputs } from `./generated/ManifestTypes`.
2. Nennen Sie alle Verweise von **InputsOutputs.IInputBag** in **IInputs** um.
3. Nennen Sie alle Verweisen von **InputsOutputs.IOutputBag** in IOutputs** um.
4. Erstellen Sie das Projekt, um mithilfe des Befehls `npm run build` eine neue **ManifestTypes.d.ts**-Datei zu generieren.

### <a name="see-also"></a>Siehe auch

[Einschränkungen des PowerApps-Komponentenframeworks](limitations.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](overview.md)
