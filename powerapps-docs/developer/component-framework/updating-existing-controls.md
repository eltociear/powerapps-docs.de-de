---
title: Aktualisieren vorhandener Code Komponenten mithilfe der Tools von powerapps Component Framework | Microsoft-Dokumentation
description: Aktualisieren von Komponenten mithilfe der Tools von powerapps Component Framework
keywords: Powerapps-Komponenten Framework, Code Komponente, Komponenten Framework
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
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340228"
---
# <a name="update-existing-code-components"></a>Aktualisieren vorhandener Code Komponenten 

Wenn Sie ein Teilnehmer für die private Vorschau von powerapps Component Framework für Modell gesteuerte apps sind und bereits Code Komponenten erstellt haben, müssen Sie einige kleinere Updates vornehmen, um die Kompatibilität mit den neuen Alm-zentrierten Projektstrukturen zu gewährleisten. 

Einige Änderungen sind erforderlich, um die neuen powerapps-CLI-Tools mit Ihren vorhandenen Code Komponenten von powerapps Component Framework zu verwenden.

> [!NOTE]
> Dieses Thema gilt nur für die Aktualisierung von Code Komponenten für Modell gesteuerte apps, da die powerapps-CLI-Tools zum Zeitpunkt der privaten Vorschau für die Modell gesteuerten apps nicht verfügbar sind.  

## <a name="creating-an-empty-project"></a>Erstellen eines leeren Projekts

Verwenden Sie powerapps CLI, um ein neues leeres Projekt für die Code Komponente zu erstellen. Weitere Informationen: [Erstellen von Komponenten mithilfe](create-custom-controls-using-pcf.md) von Tools

Nachdem das Projekt erstellt wurde, migrieren Sie die Code Komponenten Quelle zum neuen Projekt:

1. Kopieren oder ersetzen Sie die Quelldatei der Komponente aus der alten Quelldatei in **Index. TS**.
2. Kopieren oder ersetzen Sie den Inhalt von " **controlmanifest. XML** " in die Datei " **controlmanifest. Input. XML** ".
3. Kopieren Sie alle anderen Peripheriekomponenten Ressourcen wie CSS, RESX oder IMG in den entsprechenden Unterordner aus dem alten Projekt in das neue Projekt.

## <a name="updating-manifest-file"></a>Manifest-Datei wird aktualisiert

Die `ControlManifest.xml` Datei, die die Eigenschaften der Code Komponente definiert, wird durch die `ControlManifest.Input.xml`-Datei ersetzt. Andernfalls sollte das Schema zwischen den beiden Dateien sehr wenig geändert werden.

Es gibt jedoch einige wichtige semantische Änderungen:

1. Der `code`-Ressourcen Eintrag muss nun auf die vorkompilierte Quelldatei der Code Komponente verweisen. Der Dateiname ist standardmäßig auf **Index. TS**eingestellt.

   Wenn die Komponenten Quelle beispielsweise in einer Datei namens `MyControl.ts` implementiert ist, muss der `code` Eintrag in `ControlManifest.Input.xml` auf diese Datei verweisen. Die `code` Datei muss auch eine gültige typescript-Datei sein. Dies steht im Gegensatz zu Legacy-Manifest-Dateien, die die kompilierte js-Ausgabedatei im `code` Eintrag angegeben haben.
2. Das `path`-Attribut des Resource-Elements, wie `code` oder `css`, verweist jetzt auf den lokalen Pfad zur Datei auf dem Datenträger. Beispiel:

    ```XML
   <resources>
    <css path="css/YourControlName" order="1"/>
    </resources>
    ```

Das obige `path` Attribut gibt an, dass sich die `YourControlName.css` Datei im Unterordner `css` relativ zum aktuellen Verzeichnis befindet, in dem sich der `ControlManifest.Input.xml` auf dem Datenträger befindet.

Aktualisieren Sie die Dateien "controlmanifest. Input. xml" wie folgt:

1. Bearbeiten Sie den `code` Eintrag in `ControlManifest.Input.xml` in die vorkompilierte Quelldatei der Code Komponente (in der Regel Index. TS).
2. Bearbeiten Sie alle Pfade der Ressourcen, um auf die relativen Pfade zu Dateien auf dem Datenträger zu verweisen.

## <a name="updating-the-project-files"></a>Aktualisieren der Projektdateien

Wenn Sie eine Komponente mit der älteren Version der Tools erstellt haben und die neuesten Funktionen nutzen möchten, stellen Sie sicher, dass Sie Ihre Projektdateien aktualisieren, wie hier gezeigt:

1. Aktualisieren Sie Ihre vorhandenen Projekte, um die neuesten Module zu verwenden.
 
   - Aktualisieren Sie das Versionstag in Ihrem `pcfproj`, das sich in Ihrem powerapps Component Framework-Projektordner befindet, wie folgt:

      ```XML
      <Packagereference Include="Microsoft.PowerApps.MSBuild.Pcf" Version="1.*"/>
      ```
   - Aktualisieren Sie das Versionstag in Ihrem `cdsproj` in Ihrem projektmappenprojektordner wie folgt:

      ```XML
      <Packagereference Include="Microsoft.PowerApps.MSBuild.Solution" Version="1.*"/>
      ```

      > [!NOTE] 
      > Nachdem Sie die obigen Änderungen vorgenommen haben, führen Sie den Befehl `msbuild /t:restore` aus, um Ihr Projekt auf die richtige Version zu aktualisieren.


   - Aktualisieren Sie das Versionstag in der `package.json`-Datei, die sich in Ihrem powerapps Component Framework-Projektordner befindet:

      ```JSON
      "devDependencies":{
       "pcf-scripts": "^1",
       "pcf-start": "^1"
          }
      ```
     > [!NOTE]
     > Nachdem Sie die obigen Änderungen vorgenommen haben, führen Sie den `npm update` Befehl aus, um das Projekt auf die richtige Version zu aktualisieren.

2. Wenn Sie zuvor ein Authentifizierungs Profil erstellt haben, müssen Sie es neu erstellen. Dies liegt daran, dass dem Profil eine neue Eigenschaft hinzugefügt wurde, die nicht-Public Cloud unterstützt. Hierfür können Sie folgende Aufgaben ausführen:
 
    - Ausführen des Befehls `pac auth clear`.
    - Ausführen des Befehls `pac auth create --url <your org url>`.

## <a name="updating-your-project-with-the-latest-node-modules"></a>Aktualisieren Ihres Projekts mit den neuesten Knoten Modulen

Legacy Projekte erfordern, dass die neuesten NPM-Module abgerufen werden, um von den neuesten CLI-Funktionen profitieren zu können. Um die zuvor heruntergeladenen Knoten Module zu aktualisieren, wechseln Sie in der Developer-Eingabeaufforderung in Ihr Projektverzeichnis, und führen Sie den Befehl `npm update` aus. 

## <a name="using-es6-module-syntax"></a>Verwenden der ES6-Modul Syntax

Die Buildtools erwarten, dass die Komponenten Quelle mithilfe des standardmäßigen ES6-Modul Formats exportiert wird. Ältere Komponenten werden in der Regel als interne Module (auch Namespaces genannt) exportiert. Die Quelldatei der Komponente muss wie unten beschrieben geändert werden, damit Sie mit den neuen Buildtools übereinstimmen.

1. Öffnen Sie die Quelldatei, die die Code Komponente implementiert (z. b. Index. TS).
2. Verwenden Sie die Export Syntax Standard ES6, indem Sie die Modul Deklaration entfernen.

     Vor
     ```TypeScript
     module SampleNamespace
     {
    export class TSLinearInputControl implements ComponentFramework.StandardControl<InputsOutputs.IInputBag, InputsOutputs.IOutputBag> {
          <your class implementation>
           }
            }
     
      ```
    Nachdem
    ```TypeScript
     export class YourControlName implements ComponentFramework.StandardControl<IInputs, IOutputs> { 
          <your class implementation>
          }
   ```

## <a name="using-generated-manifest-typing-file"></a>Verwenden der generierten manifesteingabedatei

Legacy Projekte erfordern eine manuelle Erstellung und Bearbeitung einer `inputsOutputs.d.ts` Typisierungs Datei, die sich in der Regel unter dem `private_typing` Unterordner befindet. Die powerapps-CLI-Tools generieren diese Datei jetzt automatisch bei der Erstellung. 

Code-gen stellt sicher, dass `type` Definitionen, die im Quell Code der Komponente verwendet werden, mit `types` synchronisiert werden, die in der Komponenten Manifest-Datei definiert sind.

Die Typisierungs Datei wurde in `ManifestTypes.d.ts` umbenannt und wird jetzt in einem Unterordner mit dem Namen `generated` generiert. Außerdem werden die Typen `InputsOutputs.IInputBag` und `InputsOutputs.IOutputBag` in `IInputs` bzw. `IOutputs` umbenannt.

So verwenden Sie die neue Typisierungs Datei:

1. Importieren Sie die neue `ManifestTypes.d.ts` Datei, indem Sie die folgende Zeile am Anfang der Quelldatei der Komponente hinzufügen:

    Importieren Sie {iinputs, ioutputs} aus `./generated/ManifestTypes`.
2. Benennen Sie alle Verweise von **InputsOutputs. iinputbag** in **iinputs**um.
3. Benennen Sie alle Verweise von **InputsOutputs. ioutputbag** in **ioutputs**um.
4. Erstellen Sie das Projekt, um eine neue **ManifestTypes. d. TS-** Datei mithilfe des Befehls `npm run build` zu generieren.

## <a name="troubleshooting-and-workarounds"></a>Problembehandlung und Problem Umgehungen

1. Wenn Sie eine 1Es-Benachrichtigung erhalten, in der Sie gefragt werden, wie PCF-Skripts verwendet werden, beachten Sie, dass diese Skripts nur zum Erstellen der Code Komponenten verwendet werden, aber nicht von der resultierenden Komponente gebündelt oder verwendet werden.  
2. Wenn Sie zuvor eine Code Komponente mithilfe der Tool Version 0.1.817.1 oder früher erstellt haben und sicherstellen möchten, dass die neuesten Build-und Debugmodule verwendet werden, nehmen Sie die Aktualisierung der Datei "Package. JSON" wie folgt vor:
   
    ```JSON
     "dependencies": { "@types/node": "^10.12.18", "@types/powerapps-component-framework": "1.1.0"}, "devDependencies": { "pcf-scripts": "~0", "pcf-start": "~0" } 
    ```
3. Der Benutzer erhält den Fehler `Failed to retrieve information about Microsoft.PowerApps.MSBuild.Pcf from remote source <Feed Url>`, wenn der Buildvorgang aufgrund von Autorisierungs Problemen fehlschlägt. Im folgenden finden Sie eine Problem Umgehung:

   - Öffnen Sie die Datei "nuget. config" unter " **%AppData%\nuget**". Der Feed, von dem der Benutzer den Fehler erhält, sollte in dieser Datei vorhanden sein. 
   - Entfernen Sie den Feed aus der Datei nuget. config, oder generieren Sie ein Pat-Token, und fügen Sie es der Datei nuget. config hinzu. Beispiel:

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

[Einschränkungen für das powerapps-Komponenten Framework](limitations.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](overview.md)
