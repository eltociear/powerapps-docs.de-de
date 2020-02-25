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
ms.openlocfilehash: 46bfdf070970e89cbe6eeb9aa4d3864ab493794b
ms.sourcegitcommit: 4349eefb1fd788f5e27d91319bc878ee9aba7a75
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2020
ms.locfileid: "3012659"
---
# <a name="package-a-code-component"></a>Verpacken einer Codekomponente

In diesem Thema wird beschrieben, wie Codekomponenten in Common Data Service importiert werden. Nach der Implementierung der Codekomponenten über die Power Apps CLI besteht der nächste Schritt darin, alle Codekomponenten-Elemente in einer Lösungsdatei zu bündeln und die Lösungsdatei in Common Data Service zu importieren, so dass Sie die Codekomponenten zur Laufzeit sehen können.

So erstellen und importieren Sie eine Lösungsdatei:

1. Erstellen Sie einen neuen Ordner in dem Ordner mit der `cdsproj`-Datei und nennen sie ihn **Lösungen** (oder einen beliebigen Namen Ihrer Wahl) mit dem Befehl `mkdir Solutions`. Navigieren Sie mit dem Befehl `cd Solutions` in das Verzeichnis.

2. Erstellen Sie ein neues Lösungsprojekt mit dem folgenden Befehl. Das Lösungsprojekt wird für das Verpacken einer Codekomponente in einer ZIP-Datei der Lösung verwendet, die zum Importieren in Common Data Service verwendet wird.
   
   ```CLI
   pac solution init --publisher-name <enter your publisher name> --publisher-prefix <enter your publisher prefix>
   ```

   > [!NOTE]
   > Die `publisher-name`- und `publisher-prefix`-Werte müssen in Ihrer Umgebung eindeutig sein.
 
3. Sobald das neue Lösungsprojekt erstellt ist, verweisen Sie den Ordner **Lösungen** an den Speicherort, an dem sich die erstellte Beispielkomponente befindet. Sie können den Verweis hinzufügen, indem Sie den Befehl unten verwenden. Dieser Verweis informiert das Lösungsprojekt darüber, welche Codekomponenten beim Build hinzugefügt werden sollen. Sie können Verweise auf mehrere Komponenten in einem einzelnen Lösungsprojekt hinzufügen.

   ```CLI   
    pac solution add-reference --path <path to your Power Apps component framework project>
   ```

3. Um eine ZIP-Datei aus Ihrem Lösungsprojekt zu erstellen, wechseln Sie zum Lösungsprojektverzeichnis und erstellen das Projekt mithilfe des folgenden Befehls. Dieser Befehl verwendet *MSBuild*, um das Lösungsprojekt zu erstellen, indem er die Abhängigkeiten *NuGet* als Teil der Wiederherstellung herunterfährt. Verwenden Sie das `/restore` nur beim ersten Mal, wenn das Lösungsprojekt erstellt wird. Für jeden weiteren Build können Sie danach den Befehl `msbuild` ausführen.

   ```CLI
   msbuild /t:build /restore
   ```

    > [!TIP]
    > - Wenn msbuild 15.9.* nicht der Pfad ist, öffnen Sie die Entwicklereingabeaufforderung für VS 2017, um den Befehl `msbuild` auszuführen.
    > - Das Erstellen der Lösung in der *Debugging*-Konfiguration generiert ein nicht verwaltetes Lösungspaket. Ein verwaltetes Lösungspaket wird erstellt, indem Sie die Lösung in der *Versionskonfiguration* erstellen. Diese Einstellungen können außer Kraft gesetzt werden, indem die `SolutionPackageType`-Eigenschaft in der `cdsproj`-Datei angegeben wird.
    > - Sie können die msbuild-Konfiguration auf `Release` setzen, um einen Produktionsbuild auszugeben. Beispiel: `msbuild /p:configuration=Release`
    > - Wenn die Fehlermeldung *Mehrdeutiger Projektname* beim Ausführen des Befehls `msbuild` für Ihre Lösung angezeigt wird, stellen Sie sicher, dass Ihr Lösungsname und Projektname nicht identisch sind.

4. Die erzeugten Lösungsdateien befinden sich nach erfolgreicher Erstellung im Ordner `\bin\debug\`.
5. [Importieren Sie die Lösung in Common Data Service](https://docs.microsoft.com/powerapps/maker/common-data-service/import-update-export-solutions) manuell über das Webportal oder automatisch über die [Power Apps Build Tools](https://marketplace.visualstudio.com/items?itemName=microsoft-IsvExpTools.PowerApps-BuildTools).

## <a name="connecting-to-your-environment"></a>Verbindung mit der Umgebung

Sie können die Codekomponenten direkt über die Power Apps-CLI bereitstellen, indem Sie eine Verbindung mit der Common Data Service-Umgebung herstellen und dann die aktualisierten Komponenten per Push verschieben. Führen Sie die folgenden Schritte aus, um das Authentifizierungsprofil zu erstellen, eine Verbindung zu Common Data Service herzustellen und die aktualisierten Komponenten zu übertragen. 
 
1. Erstellen Sie Ihr Authentifizierungsprofil mit dem Befehl: 
 
    ```CLI
    pac auth create --url <https://xyz.crm.dynamics.com> 
    ```
 
2. Wenn Sie zuvor ein Authentifizierungsprofil erstellt haben, können Sie mit dem Befehl alle vorhandenen Profile anzeigen: 

   ```CLI
    pac auth list 
   ```
 
3. Um zwischen den zuvor erstellten Authentifizierungsprofilen zu wechseln, verwenden Sie den Befehl: 
   
   ```CLI
    pac auth select --index <index of the active profile>
    ``` 

4. Verwenden Sie den folgenden Befehl, um die grundlegenden Informationen zur Umgebung abzurufen. Die Verbindung wird mit Hilfe des Standardauthentifizierungsprofils hergestellt. 

    ```CLI
    pac org who 
    ```
 
5. Um ein bestimmtes Authentifizierungsprofil zu löschen, verwenden Sie den Befehl `pac auth delete --index <index of the profile>`. 
6. Wenn Sie alle Authentifizierungsprofile von Ihrem lokalen Computer löschen möchten, verwenden Sie den Befehl `pac auth clear`. Diese Aktion ist irreversibel, da sie die Datei `authprofile.json` und die Token-Cachedatei auf Ihrem lokalen Computer endgültig löscht. 

## <a name="deploying-code-components"></a>Bereitstellung von Codekomponenten 

Nachdem Sie erfolgreich ein Authentifizierungsprofil erstellt haben, können Sie damit beginnen, die Codekomponenten mit den neuesten Änderungen auf die Instanz Common Data Service zu verschieben. Die `push`-Funktion beschleunigt die Inner-Entwicklerzyklusentwicklung, da sie die Codekomponenten-Versionsverwaltungsanforderungen umgeht und nicht erfordert, dass Sie die Lösung (cdsproj) erstellen, um die Codekomponente zu importieren. Um die `push`-Funktion zu verwenden, führen Sie Folgendes durch:

1. Stellen Sie sicher, dass Sie ein gültiges Authentifizierungsprofil erstellt haben.
2. Navigieren Sie zu dem Stammverzeichnis, in dem das Projekt der Codekomponente erstellt wird.
3. Führen Sie den Befehl aus.

   ```CLI
   pac pcf push --publisher-prefix <your publisher prefix>
   ```

   > [!NOTE]
   > Das Publisher-Präfix, das Sie mit dem Befehl `push` verwenden, sollte mit dem Publisher-Präfix Ihrer Lösung übereinstimmen, in dem die Komponenten enthalten sein werden.

## <a name="create-a-solution-project-based-on-an-existing-solution-in-common-data-service"></a>Erstellen Sie ein Lösungsprojekt auf der Grundlage einer vorhandenen Lösung in Common Data Service

Um ein Lösungsprojekt auf der Grundlage einer vorhandenen Lösung in Common Data Service zu erstellen, führen Sie den Befehl `pac solution clone` aus. Um dies zu tun:

1. Stellen Sie sicher, dass Sie ein gültiges Authentifizierungsprofil erstellt haben.
2. Führen Sie den Befehl aus. 

   ```CLI
   pac solution clone –name(-n) <name of the solution to be exported> --version(-v) <version of your solution> --include(-i) <settings that should be included>
   ```

Weitere Informationen: [Einstellungsoptionen](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.exportsolutionrequest?view=dynamics-general-ce-9)

## <a name="create-a-plug-in-project-and-add-a-reference-to-it-in-your-solution"></a>Erstellen Sie ein Plug-In-Projekt, und fügen Sie in Ihrer Projektmappe einen Verweis darauf hinzu 

> [!NOTE]
> Der Plug-In-Befehl befindet sich in der öffentlichen Vorschau, und Power Apps CLI unterstützt jetzt das Erstellen eines Plug-In-Projekts und das Packen in eine Lösung, indem ein Verweis auf das Plug-In-Projekt hinzugefügt wird. Der `pac plugin init`-Befehl erstellt die Vorlagendateien (csproj, Plugin.cs & ServiceHelper.cs) im Verzeichnis. Um dies zu tun: 

1.  Stellen Sie sicher, dass Sie ein gültiges Authentifizierungsprofil erstellt haben.
2.  Navigieren Sie zum Stammverzeichnis, in dem Sie das Projekt erstellen möchten.
3.  Führen Sie den Befehl aus. 

     ```CLI
     pac auth create –url <https://xyz.crm.dynamics.com>
     ```
4.  Führen Sie den Befehl aus, um das Plug-In-Projekt zu erstellen

    ```CLI
    pac plugin init
    ```

5.  Fügen Sie mit dem folgenden Befehl einen Verweis auf Ihr Lösungsprojekt hinzu, damit das Plug-In-Projekt beim Erstellen der Lösung erstellt wird.

    ```CLI
    pac solution add-reference –path <path to your plugin project>
    ```

6.  Führen Sie den Befehl aus, um die Lösung und das referenzierte Plug-In zu erstellen.
    ```CLI
    msbuild
    ```

## <a name="remove-components-from-a-solution"></a>Entfernen von Komponenten aus einer Lösung

Wenn Sie eine Codekomponente aus einer Lösungsdatei entfernen möchten:

1. Bearbeiten Sie die Datei `cdsproj` im Projektverzeichnis der Lösung und entfernen Sie die Referenzen auf die Komponente. Hier finden Sie ein Beispiel für einen Komponentenverweis:

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
[Power Apps component framework-API-Referenz](reference/index.md)<br/>
[Power Apps component framework Übersicht](overview.md)
