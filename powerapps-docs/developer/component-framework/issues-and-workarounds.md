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
ms.openlocfilehash: d9a5d345204d82a1e5f6629a3f0bb7cf2159ddd7
ms.sourcegitcommit: 212bd841595db0d6f41002f7ff9a1c8eb33a0724
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2019
ms.locfileid: "2914449"
---
# <a name="common-issues-and-workarounds"></a>Allgemeine Probleme und Problemumgehungen

Im Folgenden sind einige häufig auftretende Probleme aufgeführt, die bei der Verwendung von auftreten können Power Apps component framework und Power Apps CLI.

**Msbuild-Fehler MSB4036**

1. Der Name der Aufgabe in der Projektdatei ist gleich wie der Name der Aufgabenklasse.
2. Die Aufgabenklasse ist öffentlich und implementiert die Microsoft.Build.Framework.ITask-Schnittstelle.
3. Die Aufgabe ist mit *\<UsingTask>* korrekt in der Projektdatei in den *.tasks-Dateien im Pfadverzeichnis deklariert.

**Problemumgehung**:

1. Öffnen Sie das Visual Studio-Installationsprogramm. 
1. Wählen Sie für Visual Studio 2017 **Ändern** aus. 
1. Klicken Sie auf **Einzelne Komponenten**.
1. Überprüfen Sie unter „Code-Tools“ die Option **NuGet-Ziele und Build-Aufgaben**.

> [!NOTE]
> Wir werden ständig häufige Probleme und Problemumgehungen hinzufügen, die beim Entwicklungsprozesses auftreten. Wenn Sie auf ein Problem stoßen und eine Problemumgehung haben und dies für hilfreich halten, sprechen Sie das Problem [Hier](https://powerusers.microsoft.com/t5/Power-Apps-Component-Framework/bd-p/pa_component_framework) an oder lösen eine Pull-Anforderung aus, damit wir sie überprüfen und zur Liste hinzufügen können.

**Herausgeberpräfix**

Wenn eine Komponente mit einer CLI-Version kleiner als 0.4.3 erstellt wird, tritt beim erneuten Importieren der Lösungsdatei ein Fehler auf Common Data Service. 

**Problemumgehung**:

- Löschen Sie die Lösung, die die relevante Komponente aus Common Data Service enthält. 
- Die Komponente muss aus dem Feld oder Raster entfernt werden, wenn die Komponente bereits konfiguriert ist, um Abhängigkeiten zu vermeiden.
- Importieren Sie die neue Lösung mit Updates auf die Komponente, die für die aktuelle CLI-Version erstellt wird.
- Neu importierte Komponenten können jetzt in Formularen oder Rastern konfiguriert werden.  

**Probleme beim Aktualisieren vorhandener Codekomponenten**

1. Wenn Sie eine 1ES-Benachrichtigung erhalten, in der Sie gefragt werden, wie PCF-Skripte verwendet werden, beachten Sie, dass diese Skripte nur zum Erstellen der Codekomponenten verwendet werden, aber nicht von der resultierenden Komponente gebündelt oder verwendet werden.  
2. Wenn Sie eine Codekomponente mit der CLI-Version 0.1.817.1 oder früher erstellt haben und sicherstellen möchten, dass die neuesten Build- und Debug-Module verwendet werden, nehmen Sie die Aktualisierungen an der `package.json` Datei wie unten angezeigt vor:
   
   ```JSON
   "dependencies": { "@types/node": "^10.12.18", "@types/powerapps-component-framework": "1.1.0"}, "devDependencies": { "pcf-scripts": "~0", "pcf-start": "~0" } 
   ```

3. Fehler **Fehler beim Abrufen von Informationen über Microsoft.PowerApps.MSBuild. PCF von der Remote-Quelle <Feed Url>** Wenn der Build aufgrund von Autorisierungsproblemen fehlschlägt. 

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
