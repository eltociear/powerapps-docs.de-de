---
title: Übersicht über die Excel-Verbindung | Microsoft-Dokumentation
description: Zeigen Sie Daten in Excel an, und aktualisieren Sie Daten in Excel, indem Sie die Arbeitsmappe in einem Cloudspeicherkonto speichern und anschließend aus Ihrer App eine Verbindung mit den Daten herstellen.
services: ''
suite: powerapps
documentationcenter: na
author: archnair
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/02/2016
ms.author: archanan
ms.openlocfilehash: d57d279670bf49c330b68a30bcd99a4578d3bbf9
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="connect-to-excel-from-powerapps"></a>Herstellen einer Verbindung mit Excel aus PowerApps
![Excel](./media/connection-excel/excelicon.png)

Excel stellt eine *Art von Verbindung* dar. So zeigen Sie Excel-Daten in Ihrer App an

1. [Formatieren Sie die Excel-Daten als Tabelle](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-E81AA349-B006-4F8A-9806-5AF9DF0AC664).
2. Speichern Sie die Excel-Datei in einem Cloudspeicherkonto, z.B. Box, Dropbox, Google Drive, OneDrive und OneDrive for Business.
3. [Stellen Sie eine Verbindung mit dem Cloudspeicherkonto her](../add-manage-connections.md), und fügen Sie anschließend die Excel-Tabelle als Datenquelle hinzu.
4. Zeigen Sie diese Informationen in der App an, indem Sie [automatisch eine App generieren](../get-started-create-from-data.md) oder indem Sie beispielsweise ein **Katalog**-Steuerelement hinzufügen und konfigurieren.

> [!NOTE]
> Nachdem Sie die Excel-Tabelle in PowerApps erstellt haben, wird für jede Zeile der Excel-Tabelle eine neue Spalte mit dem Namen **\_*PowerAppsId_*** mit einer eindeutigen ID erstellt.

In [Übersicht über die Cloudspeicherverbindung](cloud-storage-blob-connections.md) wird veranschaulicht, wie Sie die Verbindung hinzufügen, eine Excel-Tabelle als Datenquelle hinzufügen und die Excel-Daten in der App verwenden.

Weitere Informationen zum Herstellen von Verbindungen mit anderen Datentypen finden Sie in der [Liste der Verbindungen für PowerApps](../connections-list.md).

### <a name="known-limitations"></a>Bekannte Einschränkungen
Weitere Informationen zum Freigeben von Excel-Daten in Ihrer Organisation erhalten Sie in diesen [Ausführungen zu Einschränkungen](cloud-storage-blob-connections.md#sharing-excel-tables).
