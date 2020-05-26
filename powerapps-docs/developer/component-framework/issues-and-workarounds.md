---
title: Häufige Probleme und Problemumgehungen (Power Apps component framework) | Microsoft Docs
description: Bietet Informationen zu bekannten Problemen und Problemumgehungen, die bei der Arbeit auftreten können Power Apps component framework und CLI
keywords: ''
author: Nkrb
ms.author: nabuthuk
manager: kvivek
ms.date: 11/25/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: 1d53a01d91822743311d350ddfce7733aba3f661
ms.sourcegitcommit: 6fce86edacd9bfe49f8114a2a69bc18302cd01f9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "3260660"
---
# <a name="common-issues-and-workarounds"></a>Allgemeine Probleme und Problemumgehungen

Im Folgenden sind einige häufig auftretende Probleme aufgeführt, die bei der Verwendung von auftreten können Power Apps component framework und Power Apps CLI.

## <a name="msbuild-error-msb4036"></a>Msbuild-Fehler MSB4036

- Der Name der Aufgabe in der Projektdatei ist gleich wie der Name der Aufgabenklasse.
- Die Aufgabenklasse ist öffentlich und implementiert die Microsoft.Build.Framework.ITask-Schnittstelle.
- Die Aufgabe ist mit *\<UsingTask>* korrekt in der Projektdatei in den *.tasks-Dateien im Pfadverzeichnis deklariert.

**Problemumgehung**:

- Öffnen Sie das Visual Studio-Installationsprogramm.
- Wählen Sie für Visual Studio 2017 **Ändern** aus.
- Klicken Sie auf **Einzelne Komponenten**.
- Überprüfen Sie unter „Code-Tools“ die Option **NuGet-Ziele und Build-Aufgaben**.

> [!NOTE]
> Wir werden ständig häufige Probleme und Problemumgehungen hinzufügen, die beim Entwicklungsprozesses auftreten. Wenn Sie auf ein Problem stoßen und eine Problemumgehung haben und dies für hilfreich halten, sprechen Sie das Problem [Hier](https://powerusers.microsoft.com/t5/Power-Apps-Component-Framework/bd-p/pa_component_framework) an oder lösen eine Pull-Anforderung aus, damit wir sie überprüfen und zur Liste hinzufügen können.

## <a name="publisher-prefix"></a>Herausgeberpräfix

Wenn eine Komponente mit einer CLI-Version kleiner als 0.4.3 erstellt wird, tritt beim erneuten Importieren der Lösungsdatei ein Fehler auf Common Data Service. 

**Problemumgehung**:

- Löschen Sie die Lösung, die die relevante Komponente aus Common Data Service enthält. 
- Die Komponente sollte aus dem Feld oder Raster entfernt werden, wenn die Komponente bereits konfiguriert ist, um Abhängigkeiten zu vermeiden.
- Importieren Sie die neue Lösung mit Updates auf die Komponente, die für die aktuelle CLI-Version erstellt wird.
- Neu importierte Komponenten können jetzt in Formularen oder Rastern konfiguriert werden.  

## <a name="issues-while-updating-existing-code-components"></a>Probleme beim Aktualisieren vorhandener Codekomponenten

- Wenn Sie eine 1ES-Benachrichtigung erhalten, in der Sie gefragt werden, wie PCF-Skripte verwendet werden, beachten Sie, dass diese Skripte nur zum Erstellen der Codekomponenten verwendet werden, aber nicht von der resultierenden Komponente gebündelt oder verwendet werden.
- Wenn Sie eine Codekomponente mit der CLI-Version 0.1.817.1 oder früher erstellt haben und sicherstellen möchten, dass die neuesten Build- und Debug-Module verwendet werden, nehmen Sie die Aktualisierungen an der `package.json` Datei wie unten angezeigt vor:
   
   ```JSON
   "dependencies": { "@types/node": "^10.12.18", "@types/powerapps-component-framework": "1.1.0"}, "devDependencies": { "pcf-scripts": "~0", "pcf-start": "~0" } 
   ```

## <a name="error-failed-to-retrieve-information-about-microsoftpowerappsmsbuildpcf-from-remote-source-feed-url-when-the-build-fails-for-authorization-issues"></a>Fehler: Informationen über Microsoft.PowerApps.MSBuild.Pcf von der Remote-Quelle <Feed Url> konnten nicht abgerufen werden, wenn der Build aufgrund von Autorisierungsproblemen fehlschlägt. 

   **Problemumgehung**

   - Öffnen der `NuGet.Config` Datei von **%ANWENDUNGSDATEN%\NuGet**. Der Feed, von dem der Benutzer den Fehler erhält, sollte in dieser Datei vorhanden sein. 
   - Entfernen Sie den Feed von der `NuGet.Config file` oder generieren Sie ein PAT-Token und fügen Sie es dem` Nuget.Config file` hinzu. Beispiel:

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

## <a name="web-resource-size-is-too-large"></a>Webressourcengröße ist zu groß.

Fehler **Importieren der Lösung fehlgeschlagen: Webressourceninhalt ist zu groß**.

**Problemumgehung**

- Erstellen Sie `.pcfproj` als Versionskonfiguration, die das Webpack mit dem Befehl in den Produktionsmodus versetzt. 
  ```CLI
  msbuild /property:configuration=Release
  ```
- Führen Sie den Befehl msbuild mit einer zusätzlichen Eigenschaft wie unten angezeigt aus: 
  ```CLI
  msbuild /p:PcfBuildMode=production
  ```
- Bearbeiten Sie `.pcfproj`, um das Webpack immer im Produktionsmodus zu erstellen, indem Sie die Eigenschaft `PcfBuildMode` in die Produktion festlegen:
  ```XML
  <PropertyGroup>
    <Name>TS_ReactStandardControl</Name>
    <ProjectGuid>0df84c56-2f55-4a80-ac9f-85b7a14bf378</ProjectGuid>
    <OutputPath>$(MSBuildThisFileDirectory)out\controls</OutputPath>
    <PcfBuildMode>production</PcfBuildMode>
  </PropertyGroup>
  ```

## <a name="when-running-power-apps-checker-with-the-solution-built-using-cli-tooling-in-default-configuration"></a>Beim Ausführen von Power Apps Checker mit der Lösung, die mit CLI-Tooling in der Standardkonfiguration erstellt wurde, kann der Administrator entscheiden, ob die Anwendung in den Anwendungskatalog gehört

**Fehler: Verwenden Sie nicht die Bewertungsfunktion oder ihre funktionalen Äquivalente** Diese Warnung ist beabsichtigt, da die Standardkonfiguration `msbuild` die `Configuration=Debug` ist. Dies wiederum weist Webpack (das zum Bündeln der Code-Komponente verwendet wird) an, im Entwicklungsmodus zu paketieren, der eine `eval()` ausgibt. 

**Problemumgehung**

Bauen Sie die Lösungsdatei mit einem der folgenden Befehle neu auf und importieren Sie die Lösung wieder in Common Data Service.

```CLI
msbuild/property:configuration:Release
```

```CLI
npm run build -- --buildMode production
```

## <a name="power-apps-component-framework-datasets-getvalue-by-property-alias-doesnt-work"></a>Power Apps component framework Datensätze getValue via Eigenschafts-Alias funktioniert nicht

Die getValue-Funktion der Power Apps component framework DataSet-API durchsucht Datensätze nur nach dem DataSet-Spaltennamen und nicht nach dem im Manifest festgelegten Eigenschafts-Alias. Der Versuch, den Wert nach dem Eigenschaftsalias zu erhalten, gibt einen leeren Wert zurück.

**Problemumgehung**

Verwenden Sie den Dataset-Spaltennamen (die Komponente kann den Dataset-Spaltennamen durch Suchen des Spaltenarrays mit Hilfe des Alias erhalten). 

   ***Erwartetes Verhalten*** 

   ```TypeScript
   long  = dataSet.records[currentRecordId].getValue("Longitude") //based on property set in manifest"-122.3514661"
   ```

   ***Aktuelle Abhilfe***

   ```TypeScript
   lat = dataSet.records[currentRecordId].getValue("Address_x0020_1_x003a__x0020_Latitude")//based on the dataset column name
   ```

## <a name="power-apps-component-framework-datasets-sharepoint-issue"></a>Power Apps component framework Datasets SharePoint Problem

Die Power Apps component framework Dataset zeigt derzeit die Datensätze von SharePoint nicht richtig an. Während die Netzwerkanforderung mit den korrekten zurückgegebenen Datensätzen erfolgreich ist, schlägt die Deserialisierung fehl und es wird ein leerer Datensatz zurückgegeben.

**Problemumgehung**

Keine Abhilfe ab sofort. Wir arbeiten daran, eine Lösung für unsere Bereitstellung zu finden.

