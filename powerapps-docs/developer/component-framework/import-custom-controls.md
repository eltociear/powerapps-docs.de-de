---
title: Komponenten importieren | Microsoft Docs
description: Prozess zum Importieren von benutzerdefinierten Komponenten
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 06/20/2019
ms.service: powerapps
ms.suite: ''
ms.topic: article
author: Nkrb
---

# <a name="package-a-custom-component"></a>Bündeln Sie eine benutzerdefinierte Komponente

Dieses Thema zeigt, wie Sie benutzerdefinierte Komponenten in Common Data Service importieren. Nach der Entwicklung benutzerdefinierter Komponenten mithilfe der PowerApps-CLI müssen diese Komponenten als Nächstes importiert werden, sodass die Komponenten zur Laufzeit angezeigt werden.

Führen Sie die folgenden Schritte aus, um eine Lösungsdatei zu erstellen und zu importieren:

1. Erstellen Sie ein neues Lösungsprojekt im Verzeichnis Ihrer Wahl, indem Sie den Befehl `pac solution init --publisher-name <enter your publisher name> --publisher-prefix <enter your publisher name>` nach `cd <your new folder>` verwenden. Das Lösungsprojekt wird für das Verpacken einer benutzerdefinierten Komponente in einer ZIP-Datei der Lösung verwendet, die zum Importieren in Ihre Umgebung verwendet wird.

   > [!NOTE]
   > Die `publisher-name`- und `publisher-prefix`-Werte müssen in Ihrer Umgebung eindeutig sein.
 
2. Sobald das neue Lösungsprojekt erstellt ist, müssen Sie den Speicherort verweisen, an dem sich die erstellte Komponente befindet. Sie können den Verweis hinzufügen, indem Sie den Befehl unten verwenden. Dieser Verweis informiert das Lösungsprojekt, welche benutzerdefinierten Komponenten während des Builds hinzugefügt werden sollen, und Sie können Verweise zu mehreren Komponenten in einem einzelnen Lösungsprojekt hinzufügen.

    ```CLI   
    pac solution add-reference --path<path of your PowerApps component framework project on disk>
    ```

3. Um eine ZIP-Datei aus Ihrem Lösungsprojekt zu erstellen, müssen Sie `cd` im Lösungsprojektverzeichnis hinzufügen und das Projekt mithilfe des Befehls `msbuild /t:build /restore` erstellen. Dieser Befehl verwendet MSBuild, um das Lösungsprojekt zu erstellen, indem er NuGet-Abhängigkeiten im Rahmen der Wiederherstellung überträgt. Verwenden Sie das `/restore` nur beim ersten Mal, wenn das Lösungsprojekt erstellt wird. Für jeden weiteren Build können den Befehl `msbuild` ausführen.

    > [!NOTE]
    > - Wenn msbuild 15.9.* nicht der Pfad ist, öffnen Sie die Entwicklereingabeaufforderung für VS 2017, um den Befehl `msbuild` auszuführen.    
    > - Das Erstellen der Lösung in der *Debugging*-Konfiguration generiert ein nicht verwaltetes Lösungspaket. Ein verwaltetes Lösungspaket wird erstellt, indem Sie die Lösung in der *Versionskonfiguration* erstellen. Diese Einstellungen können überschrieben werden, indem Sie die SolutionPackageType-Eigenschaft in der cdsproj-Datei angeben.
    > - Sie können die msbuild-Konfiguration auf `Release` setzen, um einen Produktionsbuild auszugeben. Beispiel: `msbuild /p:configuration=Release` 

4. Die erstellten Lösungsdateien befinden sich nach dem abgeschlossenen Build in `\bin\debug\`.
5. Sie können die Lösung jetzt unter Verwendung des Webportals manuell importieren.

## <a name="how-to-remove-components-from-a-solution"></a>So entfernen Sie Komponenten aus einer Lösung

Wenn Sie eine benutzerdefinierte Komponente aus einer Lösung entfernen möchten, führen Sie die Schritte unten aus:

1.  Bearbeiten Sie die cdsproj-Datei in Ihrem Lösungsprojektverzeichnis und entfernen Sie den Verweis zur Komponente. Unten finden Sie ein Beispiel für einen Komponentenverweis:

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

2.  Ausführen eines Neuaufbaus (oder einer Bereinigung), indem Sie den Befehl ausführen
   ```CLI
   msbuild /t:rebuild
   ```

### <a name="see-also"></a>Siehe auch

[Entitäten oder Feldern Komponenten hinzufügen](add-custom-controls-to-a-field-or-entity.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](overview.md)
