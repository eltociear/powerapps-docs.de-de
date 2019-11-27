---
title: Komponenten importieren | Microsoft Docs
description: In diesem Thema wird beschrieben, wie Codekomponenten importiert werden
keywords: ''
ms.author: nabuthuk
manager: kvivek
ms.date: 06/20/2019
ms.service: powerapps
ms.suite: ''
ms.topic: article
author: Nkrb
ms.openlocfilehash: 4bb581e06102ac351b3202d30fa8d418951fa291
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748481"
---
# <a name="package-a-code-component"></a>Verpacken einer Codekomponente

In diesem Thema wird beschrieben, wie Codekomponenten in Common Data Service importiert werden. Nach der Implementierung der Codekomponenten über die PowerApps CLI besteht der nächste Schritt darin, alle Codekomponenten-Elemente in einer Lösungsdatei zu bündeln und die Lösungsdatei in Common Data Service zu importieren, so dass Sie die Codekomponenten zur Laufzeit sehen können.

So erstellen und importieren Sie eine Lösungsdatei:

1. Erstellen Sie einen neuen Ordner im Beispielkomponentenordner und nennen Sie ihn **Lösung** (oder mit einem Namen Ihrer Wahl) mit dem Befehl `mkdir Solutions`. Navigieren Sie mit dem Befehl `cd Solutions` in das Verzeichnis.

2. Erstellen Sie ein neues Lösungsprojekt mit dem Befehl `pac solution init --publisher-name <enter your publisher name> --publisher-prefix <enter your publisher prefix>`. Das Lösungsprojekt wird für das Verpacken einer Codekomponente in einer ZIP-Datei der Lösung verwendet, die zum Importieren in Common Data Service verwendet wird.

   > [!NOTE]
   > Die `publisher-name`- und `publisher-prefix`-Werte müssen in Ihrer Umgebung eindeutig sein.
 
3. Sobald das neue Lösungsprojekt erstellt ist, muss der Ordner **Lösung** auf den Speicherort verweisen, an dem sich die erstellte Beispielkomponente befindet. Sie können den Verweis hinzufügen, indem Sie den Befehl unten verwenden. Dieser Verweis informiert das Lösungsprojekt darüber, welche Codekomponenten beim Build hinzugefügt werden sollen. Sie können Verweise auf mehrere Komponenten in einem einzelnen Lösungsprojekt hinzufügen.

   ```CLI   
    pac solution add-reference --path <path to your PowerApps component framework project>
   ```

3. Um eine ZIP-Datei aus dem Lösungsprojekt zu erstellen, gehen Sie zum Lösungsprojektverzeichnis und erstellen Sie das Projekt mit Hilfe des Befehls `msbuild /t:build /restore`. Dieser Befehl verwendet *MSBuild*, um das Lösungsprojekt zu erstellen, indem er die Abhängigkeiten *NuGet* als Teil der Wiederherstellung herunterfährt. Verwenden Sie das `/restore` nur beim ersten Mal, wenn das Lösungsprojekt erstellt wird. Für jeden weiteren Build können Sie danach den Befehl `msbuild` ausführen.


    > [!NOTE]
    > - Wenn msbuild 15.9.* nicht der Pfad ist, öffnen Sie die Entwicklereingabeaufforderung für VS 2017, um den Befehl `msbuild` auszuführen.
    > - Das Erstellen der Lösung in der *Debugging*-Konfiguration generiert ein nicht verwaltetes Lösungspaket. Ein verwaltetes Lösungspaket wird erstellt, indem Sie die Lösung in der *Versionskonfiguration* erstellen. Diese Einstellungen können außer Kraft gesetzt werden, indem die `SolutionPackageType`-Eigenschaft in der `cdsproj`-Datei angegeben wird.
    > - Sie können die msbuild-Konfiguration auf `Release` setzen, um einen Produktionsbuild auszugeben. Beispiel: `msbuild /p:configuration=Release`
    > - Wenn die Fehlermeldung *Mehrdeutiger Projektname* beim Ausführen des Befehls `msbuild` für Ihre Lösung angezeigt wird, stellen Sie sicher, dass Ihr Lösungsname und Projektname nicht identisch sind.

4. Die erzeugten Lösungsdateien befinden sich nach erfolgreicher Erstellung im Ordner `\bin\debug\`.
5. [Importieren Sie die Lösung in Common Data Service](https://docs.microsoft.com/powerapps/maker/common-data-service/import-update-export-solutions) manuell mit Hilfe des Webportals oder lesen Sie die Abschnitte [Authentifizierung für die Organisation](#authenticating-to-your-organization) und [Bereitstellung](#deploying-code-components), um sie mit Hilfe der PowerApps CLI-Befehle zu importieren.

## <a name="authenticating-to-your-organization"></a>Authentifizierung gegenüber Ihrem Unternehmen

Sie können die Codekomponenten direkt in der PowerApps CLI bereitstellen, indem Sie die Authentifizierung für die Common Data Service-Organisation gewährleisten und die aktualisierten Komponenten übertragen. Führen Sie die folgenden Schritte aus, um das Authentifizierungsprofil zu erstellen, eine Verbindung zu Common Data Service herzustellen und die aktualisierten Komponenten zu übertragen. 
 
1. Erstellen Sie das Authentifizierungsprofil mit Hilfe des folgenden Befehls: 
 
    ```CLI
    pac auth create --url <your Common Data Service org’s url> 
    ```
 
2. Wenn Sie bereits ein Authentifizierungsprofil erstellt haben, können Sie alle vorhandenen Profile mit Hilfe des folgenden Befehls anzeigen: 

   ```CLI
    pac auth list 
   ```
 
3. Um zwischen den zuvor erstellten Authentifizierungsprofilen zu wechseln, verwenden Sie den folgenden Befehl: 
   
   ```CLI
    Pac auth select --index <index of the active profile>
    ``` 

4. Um grundlegende Informationen über die Organisation abzurufen, verwenden Sie den folgenden Befehl. Die Verbindung wird mit Hilfe des Standardauthentifizierungsprofils hergestellt. 

    ```CLI
    pac org who 
    ```
 
5. Um ein bestimmtes Authentifizierungsprofil zu löschen, verwenden Sie den Befehl `pac auth delete --index < index of the profile >`. 
6. Wenn Sie alle Authentifizierungsprofile von Ihrem lokalen Computer löschen möchten, verwenden Sie den Befehl `pac auth clear`. Diese Aktion ist irreversibel, da sie die Datei `authprofile.json` und die Token-Cachedatei auf Ihrem lokalen Computer endgültig löscht. 

## <a name="deploying-code-components"></a>Bereitstellung von Codekomponenten 

Nachdem Sie erfolgreich ein Authentifizierungsprofil erstellt haben, können Sie damit beginnen, die Codekomponenten mit den neuesten Änderungen auf die Instanz Common Data Service zu verschieben. Die `push`-Funktion beschleunigt die Inner-Entwicklerzyklusentwicklung, da sie die Codekomponenten-Versionsverwaltungsanforderungen umgeht und nicht erfordert, dass Sie die Lösung (cdsproj) erstellen, um die Codekomponente zu importieren. Um die `push`-Funktion zu verwenden, führen Sie Folgendes durch:

1. Stellen Sie sicher, dass Sie ein gültiges Authentifizierungsprofil erstellt haben.
2. Navigieren Sie zu dem Stammverzeichnis, in dem das Projekt der Codekomponente erstellt wird.
3. Führen Sie den Befehl `pac pcf push --publisher-prefix <your publisher prefix>` aus.

   > [!NOTE]
   > Das Publisher-Präfix, das Sie mit dem Befehl `push` verwenden, sollte mit dem Publisher-Präfix Ihrer Lösung übereinstimmen, in dem die Komponenten enthalten sein werden.

## <a name="how-to-remove-components-from-a-solution"></a>So entfernen Sie Komponenten aus einer Lösung

Wenn Sie eine Codekomponente aus einer Lösungsdatei entfernen möchten:

1.  Bearbeiten Sie die Datei `cdsproj` im Projektverzeichnis der Lösung und entfernen Sie die Referenzen auf die Komponente. Hier finden Sie ein Beispiel für einen Komponentenverweis:

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

2. Führen Sie eine Neuerstellung (oder Bereinigung) durch, indem Sie den folgenden Befehl verwenden:
   
    ```CLI
    msbuild /t:rebuild
    ```

### <a name="see-also"></a>Siehe auch

[Hinzufügen von Codekomponenten zu einem Feld oder einer Entität in modellgesteuerten Apps](add-custom-controls-to-a-field-or-entity.md)<br/>
[Hinzufügen von Komponenten zu einer Canvas-App](component-framework-for-canvas-apps.md#add-components-to-a-canvas-app)<br/>
[PowerApps component framework API-Referenz](reference/index.md)<br/>
[Übersicht über das PowerApps component framework](overview.md)
