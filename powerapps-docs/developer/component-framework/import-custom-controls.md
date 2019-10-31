---
title: Komponenten importieren | Microsoft Docs
description: Prozess zum Importieren von Codekomponenten
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 06/20/2019
ms.service: powerapps
ms.suite: ''
ms.topic: article
author: Nkrb
---

# <a name="package-a-code-component"></a>Verpacken einer Codekomponente

Dieses Thema zeigt, wie man Codekomponenten in Common Data Service importiert. Nach der Implementierung der Codekomponenten über die PowerApps CLI besteht der nächste Schritt darin, alle Codekomponenten-Elemente in einer Lösungsdatei zu bündeln und die Lösungsdatei in Common Data Service zu importieren, so dass Sie die Codekomponenten zur Laufzeit sehen können.

Führen Sie die folgenden Schritte aus, um eine Lösungsdatei zu erstellen und zu importieren:

1. Erstellen Sie einen neuen Ordner und benennen Sie ihn mit dem Befehl `mkdir Solutions` als **Lösungen** (Sie können einen beliebigen Namen wählen). Navigieren Sie mit dem Befehl `cd Solutions` in das Verzeichnis.

2. Erstellen Sie ein neues Lösungsprojekt mit dem Befehl `pac solution init --publisher-name <enter your publisher name> --publisher-prefix <enter your publisher name>`. Das Lösungsprojekt dient zur Bündelung der Codekomponente in eine Lösungs-Zip-Datei, die für den Import in Common Data Service verwendet wird.

   > [!NOTE]
   > Die `publisher-name`- und `publisher-prefix`-Werte müssen in Ihrer Umgebung eindeutig sein.
 
3. Sobald das neue Lösungsprojekt erstellt wurde, müssen Sie diesen Ordner **Lösung** an den Ort verweisen, an dem sich die erstellte Musterkomponente befindet. Sie können den Verweis hinzufügen, indem Sie den Befehl unten verwenden. Diese Referenz informiert das Lösungsprojekt darüber, welche Codekomponenten während des Build hinzugefügt werden sollen, und Sie können Referenzen auf mehrere Komponenten in einem einzigen Lösungsprojekt hinzufügen.

   ```CLI   
    pac solution add-reference --path <path to your PowerApps component framework project>
   ```

3. Um eine Zip-Datei aus dem Lösungsprojekt zu erzeugen, müssen Sie in Ihr Lösungsprojektverzeichnis gehen und das Projekt mit dem Befehl `msbuild /t:build /restore` erstellen. Dieser Befehl verwendet *MSBuild*, um das Lösungsprojekt zu erstellen, indem er die Abhängigkeiten *NuGet* als Teil der Wiederherstellung herunterfährt. Verwenden Sie das `/restore` nur beim ersten Mal, wenn das Lösungsprojekt erstellt wird. Für jeden nachfolgenden Build können Sie den Befehl `msbuild` ausführen.

    > [!NOTE]
    > - Wenn msbuild 15.9.* nicht der Pfad ist, öffnen Sie die Entwicklereingabeaufforderung für VS 2017, um den Befehl `msbuild` auszuführen.
    > - Das Erstellen der Lösung in der *Debugging*-Konfiguration generiert ein nicht verwaltetes Lösungspaket. Ein verwaltetes Lösungspaket wird erstellt, indem Sie die Lösung in der *Versionskonfiguration* erstellen. Diese Einstellungen können durch die Angabe der Eigenschaft `SolutionPackageType` in der Datei `cdsproj` überschrieben werden.
    > - Sie können die msbuild-Konfiguration auf `Release` setzen, um einen Produktionsbuild auszugeben. Beispiel: `msbuild /p:configuration=Release`.
    > - Wenn Sie beim Ausführen des Befehls `msbuild` in Ihrer Lösung auf einen Fehler stoßen, der lautet *Eindeutiger Projektname*. Überprüfen Sie dann noch einmal, ob Ihr Lösungsname und Ihr Projektname nicht identisch sind.

4. Die erzeugten Lösungsdateien befinden sich nach erfolgreicher Erstellung im Ordner `\bin\debug\`.
5. [Importieren Sie die Lösung manuell über das Webportal in Common Data Service](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/customize/import-update-upgrade-solution) oder siehe [Authentifizierung an Ihr Unternehmen](#authenticating-to-your-organization) und [Bereitstellung](#deploying-code-components) Abschnitte zum Importieren mit PowerApps CLI-Befehlen.

## <a name="authenticating-to-your-organization"></a>Authentifizierung gegenüber Ihrem Unternehmen

Sie können die Codekomponenten direkt aus der CLI PowerApps bereitstellen, indem Sie sich bei der Organisation Common Data Service authentifizieren und dann die aktualisierten Komponenten verschieben. Führen Sie die folgenden Schritte aus, um das Authentifizierungsprofil zu erstellen, eine Verbindung mit Common Data Service herzustellen und die aktualisierten Komponenten zu verschieben. 
 
1. Erstellen Sie Ihr Authentifizierungsprofil mit dem Befehl: 
 
    ```CLI
    pac auth create --url <your Common Data Service org’s url> 
    ```
 
2. Wenn Sie zuvor ein Authentifizierungsprofil erstellt haben, können Sie mit dem Befehl alle vorhandenen Profile anzeigen: 

   ```CLI
    pac auth list 
   ```
 
3. Um zwischen den zuvor erstellten Authentifizierungsprofilen zu wechseln, verwenden Sie den Befehl: 
   
   ```CLI
    Pac auth select --index <index of the active profile>
    ``` 
 
4. Um die grundlegenden Informationen über das Unternehmen zu erhalten, verwenden Sie den folgenden Befehl. Die Verbindung wird mit dem Standard-Authentifizierungsprofil hergestellt. 

    ```CLI
    pac org who 
    ```
 
5. Um ein bestimmtes Authentifizierungsprofil zu löschen, verwenden Sie den Befehl `pac auth delete --index < index of the profile >`. 
6. Wenn Sie alle Authentifizierungsprofile von Ihrem lokalen Rechner löschen möchten, verwenden Sie den Befehl `pac auth clear`. Diese Aktion ist irreversibel, da sie die Datei `authprofile.json` und die Token-Cache-Datei vollständig von Ihrem lokalen Rechner löscht. 

## <a name="deploying-code-components"></a>Bereitstellung von Codekomponenten 

Nachdem Sie erfolgreich ein Authentifizierungsprofil erstellt haben, können Sie damit beginnen, die Codekomponenten mit den neuesten Änderungen auf die Instanz Common Data Service zu verschieben. Die `push`-Funktion beschleunigt die Entwicklung des inneren Entwicklungszyklus, da sie die Anforderungen an die Versionierung der Codekomponente umgeht und nicht erfordert, dass Sie Ihre Lösung (cdsproj) erstellen, um die Codekomponente zu importieren. Um die `push`-Funktion zu nutzen, führen Sie die folgenden Schritte aus:

1. Stellen Sie sicher, dass Sie ein gültiges Authentifizierungsprofil erstellt haben.
2. Navigieren Sie zu dem Stammverzeichnis, in dem das Projekt der Codekomponente erstellt wird.
3. Führen Sie den Befehl `pac pcf push --publisher-prefix <your publisher prefix>` aus.

   > [!NOTE]
   > Das Publisher-Präfix, das Sie mit dem Befehl `push` verwenden, sollte mit dem Publisher-Präfix Ihrer Lösung übereinstimmen, in dem die Komponenten enthalten sein werden.

## <a name="how-to-remove-components-from-a-solution"></a>So entfernen Sie Komponenten aus einer Lösung

Wenn Sie eine Codekomponente aus einer Lösungsdatei entfernen möchten:

1.  Bearbeiten Sie die Datei `cdsproj` im Projektverzeichnis der Lösung und entfernen Sie die Referenzen auf die Komponente. Unten finden Sie ein Beispiel für einen Komponentenverweis:

```XML
<ItemGroup>
    <ProjectReference Include="..\pcf_component\pcf_component.pcfproj">
      <Project>0481bd83-ffb0-4b70-b526-e0b3dd63e7ef</Project>
      <Name>pcf_component </Name>
      <Targets>Build</Targets>
      <ReferenceOutputAssembly>false</ReferenceOutputAssembly>
      <OutputItemType>Content</OutputItemType>
      <CopyToOutputDirectory>Always</CopyToOutputDirectory>
    </ProjectReference>
</ItemGroup>
```

2. Führen Sie einen Rebuild (oder Clean) mit dem Befehl
   
    ```CLI
    msbuild /t:rebuild
    ```

### <a name="see-also"></a>Siehe auch

[Komponenten zu Model-Drive-Apps hinzufügen](add-custom-controls-to-a-field-or-entity.md)<br/>
[Komponenten zu einer App hinzufügen](component-framework-for-canvas-apps.md#add-components-to-a-canvas-app)<br/>
[PowerApps component framework-API-Referenz](reference/index.md)<br/>
[Übersicht über das PowerApps component framework](overview.md)
