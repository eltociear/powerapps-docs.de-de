---
title: Löschen des serverseitigen Caches für ein Portal | Microsoft-Dokumentation
description: 'Anleitungen zum Erzwingen, dass das Portal seinen Cache sofort aktualisiert.'
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 07/18/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="clear-the-server-side-cache-for-a-portal"></a>Löschen des serverseitigen Caches für ein Portal

[!include[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

Als Portaladministrator können Sie den serverseitigen Cache für das gesamte Portal löschen, damit aktualisierte Daten von Common Data Services direkt im Portal angezeigt werden. Updates von Common Data Services werden dem Portal im asynchronen Modus mitgeteilt, sodass unter Umständen eine Verzögerung zwischen dem Zeitpunkt, an dem Daten in Common Data Services aktualisiert werden, und dem Zeitpunkt, an dem diese Daten im Portal angezeigt werden, auftreten kann. Um diese Verzögerung zu eliminieren, beispielsweise, wenn sie Probleme mit der Portalkonfiguration verursacht, können Sie erzwingen, dass das Portal seinen Cache unmittelbar aktualisiert.

> [!NOTE]
> Das SLA für Cacheaktualisierung (Datenübertragung zwischen Common Data Services und Portal) ist 15 Minuten.

Löschen des serverseitigen Caches

1.  Melden Sie sich beim Portal als Administrator an.

2.  Navigieren Sie wie folgt zur URL: `<portal_path>/_services/about`

3.  Wählen Sie **Cache löschen** aus. 

Der serverseitige Cache wird gelöscht, und Daten werden von Common Data Services neu geladen. Beachten Sie, dass das Löschen des serverseitigen Portalcaches vorübergehend zu einer schlechten Portalleistung führt, wenn die Daten von Common Data Services neu geladen werden.

> [!div class=mx-imgBorder]
> ![Löschen des Portalcaches](../media/clear-portal-cache.png "Löschen des Portalcaches")
