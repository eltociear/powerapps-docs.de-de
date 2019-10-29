---
title: Importieren von Komponenten | Microsoft-Dokumentation
description: In diesem Thema wird beschrieben, wie Code Komponenten importiert werden.
keywords: ''
ms.author: nabuthuk
manager: kvivek
ms.date: 06/20/2019
ms.service: powerapps
ms.suite: ''
ms.topic: article
author: Nkrb
ms.openlocfilehash: 4bb581e06102ac351b3202d30fa8d418951fa291
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2019
ms.locfileid: "73025687"
---
# <a name="package-a-code-component"></a>Packen einer Code Komponente

In diesem Thema wird beschrieben, wie Code Komponenten in Common Data Service importiert werden. Nachdem Sie die Code Komponenten mithilfe der powerapps-CLI implementiert haben, besteht der nächste Schritt darin, alle Code Komponenten Elemente in eine Projektmappendatei zu bündeln und die Projektmappendatei in Common Data Service zu importieren, damit die Code Komponenten in der Laufzeit angezeigt werden können.

So erstellen und importieren Sie eine Projektmappendatei:

1. Erstellen Sie im Ordner "Sample Component" einen neuen Ordner, und nennen Sie ihn " **Solution** " (oder einen beliebigen Namen Ihrer Wahl) mithilfe des Befehls `mkdir Solutions`. Navigieren Sie mithilfe des Befehls `cd Solutions` in das Verzeichnis.

2. Erstellen Sie ein neues Projektmappenprojekt mit dem Befehl `pac solution init --publisher-name <enter your publisher name> --publisher-prefix <enter your publisher prefix>`. Das Projektmappenprojekt wird zum Bündeln der Code Komponente in eine ZIP-Datei der Projekt Mappe verwendet, die zum Importieren in Common Data Service verwendet wird.

   > [!NOTE]
   > Die `publisher-name`-und `publisher-prefix` Werte müssen für Ihre Umgebung eindeutig sein.
 
3. Nachdem das neue Projektmappenprojekt erstellt wurde, finden Sie im Projektmappenordner den Speicherort, an dem sich die erstellte Beispiel Komponente befindet. Sie können den Verweis mit dem unten gezeigten Befehl hinzufügen. Dieser Verweis informiert das Lösungs Projekt darüber, welche Code Komponenten während des Builds hinzugefügt werden sollen. Sie können Verweise auf mehrere Komponenten in einem einzelnen Projektmappenprojekt hinzufügen.

   ```CLI   
    pac solution add-reference --path <path to your PowerApps component framework project>
   ```

3. Um eine ZIP-Datei aus dem Projektmappenprojekt zu generieren, wechseln Sie in das projektmappenprojektverzeichnis, und erstellen Sie das Projekt mithilfe des Befehls `msbuild /t:build /restore`. Dieser Befehl verwendet *MSBuild* , um das Projektmappenprojekt zu erstellen, indem die *nuget* -Abhängigkeiten im Rahmen der Wiederherstellung abgerufen werden. Verwenden Sie den `/restore` nur zum ersten Mal, wenn das Projektmappenprojekt erstellt wird. Für jeden Build können Sie den Befehl `msbuild` ausführen.


    > [!NOTE]
    > - Wenn MSBuild 15,9. * nicht im Pfad ist, öffnen Sie Developer-Eingabeaufforderung für vs 2017, um die `msbuild`-Befehle auszuführen.
    > - Beim Aufbau der Projekt Mappe in der *Debugkonfiguration* wird ein nicht verwaltetes Lösungspaket generiert. Ein verwaltetes Lösungspaket wird generiert, indem die Projekt Mappe in der *Releasekonfiguration* erstellt wird. Diese Einstellungen können überschrieben werden, indem Sie die `SolutionPackageType`-Eigenschaft in der `cdsproj`-Datei angeben.
    > - Sie können die MSBuild-Konfiguration auf `Release` festlegen, um einen produktionsbuild auszugeben. Beispiel: `msbuild /p:configuration=Release`
    > - Wenn beim Ausführen des `msbuild`-Befehls für die Projekt Mappe ein Fehler auftritt, der auf einen *mehrdeutigen Projektnamen* trifft, stellen Sie sicher, dass der Projektmappenname und der Projektname nicht identisch sind.

4. Die generierten Projektmappendateien befinden sich im Ordner "`\bin\debug\`", nachdem der Buildvorgang erfolgreich war.
5. [Importieren Sie die Lösung manuell in Common Data Service](https://docs.microsoft.com/powerapps/maker/common-data-service/import-update-export-solutions) mithilfe des Webportals, oder lesen Sie die Abschnitte [Authentifizieren bei Ihrer Organisation](#authenticating-to-your-organization) und [Bereitstellung](#deploying-code-components) , um Sie mithilfe von CLI-Befehlen von powerapps zu importieren.

## <a name="authenticating-to-your-organization"></a>Authentifizieren bei Ihrer Organisation

Sie können die Code Komponenten direkt über die powerapps-CLI bereitstellen, indem Sie sich bei der Common Data Service Organisation authentifizieren und dann die aktualisierten Komponenten per Push übertragen. Verwenden Sie die folgenden Schritte, um das Authentifizierungs Profil zu erstellen, eine Verbindung mit Common Data Service herzustellen und die aktualisierten Komponenten per Push zu überführen. 
 
1. Erstellen Sie das Authentifizierungs Profil mit dem folgenden Befehl: 
 
    ```CLI
    pac auth create --url <your Common Data Service org’s url> 
    ```
 
2. Wenn Sie zuvor ein Authentifizierungs Profil erstellt haben, können Sie alle vorhandenen Profile mit dem folgenden Befehl anzeigen: 

   ```CLI
    pac auth list 
   ```
 
3. Verwenden Sie den folgenden Befehl, um zwischen den zuvor erstellten Authentifizierungs Profilen zu wechseln: 
   
   ```CLI
    Pac auth select --index <index of the active profile>
    ``` 

4. Verwenden Sie den folgenden Befehl, um die grundlegenden Informationen zur Organisation zu erhalten. Die Verbindung wird mit dem Standard Authentifizierungs Profil hergestellt. 

    ```CLI
    pac org who 
    ```
 
5. Verwenden Sie den Befehl `pac auth delete --index < index of the profile >`, um ein bestimmtes Authentifizierungs Profil zu löschen. 
6. Wenn Sie alle Authentifizierungs Profile von Ihrem lokalen Computer löschen möchten, verwenden Sie den Befehl `pac auth clear`. Diese Aktion ist nicht rückgängig, da Sie die `authprofile.json` Datei und die tokencachedatei vollständig von Ihrem lokalen Computer löscht. 

## <a name="deploying-code-components"></a>Bereitstellen von Code Komponenten 

Nachdem Sie erfolgreich ein Authentifizierungs Profil erstellt haben, können Sie die Code Komponenten mit allen aktuellen Änderungen an die Common Data Service Instanz übertragen. Die `push` Funktion beschleunigt die Entwicklung des inneren Entwicklungsprozess, da Sie die Anforderungen an die Versionsverwaltung von Code Komponenten umgeht und es nicht erfordert, dass Sie Ihre Projekt Mappe (cdsproj) zum Importieren der Code Komponente erstellen. Gehen Sie folgendermaßen vor, um die `push` Funktion zu verwenden:

1. Stellen Sie sicher, dass ein gültiges Authentifizierungs Profil erstellt wurde.
2. Navigieren Sie zum Stammverzeichnis, in dem das Code Komponenten Projekt erstellt wird.
3. Führen Sie den Befehl `pac pcf push --publisher-prefix <your publisher prefix>` aus.

   > [!NOTE]
   > Das Herausgeber Präfix, das Sie mit dem `push`-Befehl verwenden, sollte dem Herausgeber Präfix Ihrer Projekt Mappe entsprechen, in der die Komponenten enthalten sind.

## <a name="how-to-remove-components-from-a-solution"></a>Entfernen von Komponenten aus einer Projekt Mappe

Wenn Sie eine Code Komponente aus einer Projektmappendatei entfernen möchten:

1.  Bearbeiten Sie die `cdsproj`-Datei im projektmappenprojektverzeichnis, und entfernen Sie die Verweise auf die Komponente. Im folgenden finden Sie ein Beispiel für einen Komponenten Verweis:

   ```XML
   <ItemGroup>
       <Projectreference Include="..\pcf_component\pcf_component.pcfproj">
         <Project>0481bd83-ffb0-4b70-b526-e0b3dd63e7ef</Project>
         <Name>pcf_component </Name>
         <Targets>Build</Targets>
         <referenceOutputAssembly>false</referenceOutputAssembly>
         <OutputItemType>Content</OutputItemType>
         <CopyToOutputDirectory>Always</CopyToOutputDirectory>
       </Projectreference>
   </ItemGroup>
   ```

2. Führen Sie eine Neuerstellung (oder Bereinigung) mit dem folgenden Befehl aus:
   
    ```CLI
    msbuild /t:rebuild
    ```

### <a name="see-also"></a>Siehe auch

[Hinzufügen von Code Komponenten zu einem Feld oder einer Entität in Modell gesteuerten apps](add-custom-controls-to-a-field-or-entity.md)<br/>
[Hinzufügen von Komponenten zu einer Canvas-App](component-framework-for-canvas-apps.md#add-components-to-a-canvas-app)<br/>
[API-Referenz für das powerapps-Komponenten Framework](reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](overview.md)
