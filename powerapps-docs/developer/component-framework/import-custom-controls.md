---
title: Steuerelemente importieren | Microsoft Docs
description: 'Prozess, um benutzerdefinierten Steuerelementen zu importieren'
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 06/20/2019
ms.service: powerapps
ms.suite: ''
ms.topic: article
---

# <a name="package-a-custom-component"></a>Bündeln Sie eine benutzerdefinierte Komponente

Dieses Thema zeigt, wie Sie benutzerdefinierte Steuerelemente in Common Data Service importieren. Nach der Entwicklung benutzerdefinierter Steuerelemente mithilfe der PowerApps-CLI müssen diese Steuerelemente als Nächstes importiert werden, sodass die Steuerelemente zur Laufzeit angezeigt werden.

Führen Sie die folgenden Schritte aus, um eine Lösungsdatei zu erstellen und zu importieren:

1. Erstellen Sie ein neues Lösungsprojekt im Verzeichnis Ihrer Wahl, indem Sie den Befehl `pac solution init --publisherName <enter your publisher name> --customizationPrefix <enter your publisher name>` nach `cd <your new folder>` verwenden.

   > [!NOTE]
   > Die `publisherName`- und `cutomizationPrefix`-Werte müssen in Ihrer Umgebung eindeutig sein.
 
2. Nachdem das neue Lösungsprojekt erstellt wurde, müssen Sie den Speicherort des erstellten Steuerelements verwiesen werden. Sie können den Verweis hinzufügen, indem Sie den Befehl `pac solution add-reference --path <path of your PowerApps component framework project on disk>` verwenden
3. Um eine ZIP-Datei aus Ihrem Lösungsprojekt zu erstellen, müssen Sie `cd` im Lösungsprojektverzeichnis hinzufügen und das Projekt mithilfe des Befehls `msbuild /t:build /restore` erstellen.

    > [!NOTE]
    > - Wenn sich msbuild 15 nicht im Pfad befindet, öffnen Sie die Entwickler-Eingabeaufforderung für Version 2017, um die msbuild-Befehle auszuführen.    
    > - Das Erstellen der Lösung in der *Debugging*-Konfiguration generiert ein nicht verwaltetes Lösungspaket. Ein verwaltetes Lösungspaket wird erstellt, indem Sie die Lösung in der *Versionskonfiguration* erstellen. Diese Einstellungen können überschrieben werden, indem Sie die SolutionPackageType-Eigenschaft in der cdsproj-Datei angeben.
    > - Sie können die msbuild-Konfiguration auf `Release` setzen, um einen Produktionsbuild auszugeben. Beispiel: `msbuild /p:configuration=Release` 

4. Die erstellte Lösungsdateien befinden sich in `\bin\debug\`.
5. Sie müssen die Lösung unter Verwendung des Webportals manuell importieren.

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

[Entitäten oder Feldern Steuerelemente hinzufügen](add-custom-controls-to-a-field-or-entity.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](overview.md)
