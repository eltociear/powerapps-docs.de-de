---
title: Steuerelemente importieren | Microsoft Docs
description: 'Prozess, um benutzerdefinierten Steuerelementen zu importieren'
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.topic: article
---

# <a name="deploying-controls-into-common-data-service"></a>Bereitstellen von Steuerelementen in Common Data Service

Dieses Thema zeigt, wie Sie benutzerdefinierte Steuerelemente in Common Data Service importieren. Nach der Entwicklung benutzerdefinierter Steuerelemente mithilfe der PowerApps-CLI müssen diese Steuerelemente als Nächstes importiert werden, sodass die Steuerelemente zur Laufzeit angezeigt werden.

Führen Sie die folgenden Schritte aus, um eine Lösungsdatei zu erstellen und zu importieren:

1. Erstellen Sie ein neues Lösungsprojekt im Verzeichnis Ihrer Wahl, indem Sie den Befehl `pac solution init --publisherName <enter your publisher name> --customizationPrefix <enter your publisher name>` nach `cd <your new folder>` verwenden.

   > [!NOTE]
   > Die `publisherName`- und `cutomizationPrefix`-Werte müssen in Ihrer Umgebung eindeutig sein.
 
2. Nachdem das neue Lösungsprojekt erstellt wurde, müssen Sie den Speicherort des erstellten Steuerelements verwiesen werden. Sie können den Verweis hinzufügen, indem Sie den Befehl `pac solution add-reference --<path of your PowerApps component framework project on disk>` verwenden
3. Um eine ZIP-Datei aus Ihrem Lösungsprojekt zu erstellen, müssen Sie `cd` im Lösungsprojektverzeichnis hinzufügen und das Projekt mithilfe des Befehls `msbuild/t:restore` und `msbuild` erstellen.

    > [!NOTE]
    > Wenn sich msbuild 15 nicht im Pfad befindet, öffnen Sie die Entwickler-Eingabeaufforderung für Version 2017, um die msbuild-Befehle auszuführen.

    > [!NOTE]
    > Das Erstellen der Lösung in der Debugging-Konfiguration generiert ein nicht verwaltetes Lösungspaket. Ein verwaltetes Lösungspaket wird erstellt, indem Sie die Lösung in der Versionskonfiguration erstellen. Diese Einstellungen können überschrieben werden, indem Sie die SolutionPackageType-Eigenschaft in der cdsproj-Datei angeben.

4. Die erstellte Lösungsdateien befinden sich in `\bin\debug\`.
5. Sie müssen die Lösung unter Verwendung des Webportals manuell importieren.

## <a name="telemetry"></a>Telemetrie

Das Funktionsteam aggregiert anonymisierte Telemetrie, um zu verstehen, welche Funktionen im PowerApps-CLI am häufigsten von den Entwicklern verwendet werden. Die aggregierten Daten ermöglichen die Bereitstellung des besten Erlebnisses für die Kunden, indem Sie sich darauf konzentrieren, was wirklich ist wichtig ist.

Um die Telemetrie-Erfassung zu deaktivieren, führen Sie den Befehl `pac telemetry - -enabled false`aus. Um die Telemetrie wieder zu aktivieren, verwenden Sie den Befehl `pac telemetry- -enabled true`.

### <a name="see-also"></a>Siehe auch

[Entitäten oder Feldern Steuerelemente hinzufügen](add-custom-controls-to-a-field-or-entity.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](overview.md)