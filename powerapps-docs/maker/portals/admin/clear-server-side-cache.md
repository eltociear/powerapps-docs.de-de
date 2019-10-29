---
title: Löschen des serverseitigen Caches für ein Portal | MicrosoftDocs
description: Anweisungen zum erzwingen, dass das Portal den Cache sofort aktualisiert.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 8351ca8d3befec80a9e97da03ca62980383b01b1
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975999"
---
# <a name="clear-the-server-side-cache-for-a-portal"></a>Löschen des serverseitigen Caches für ein Portal

Als Portaladministrator können Sie den serverseitigen Cache für das gesamte Portal löschen, sodass aktualisierte Daten aus Common Data Service sofort im Portal reflektiert werden. Updates von Common Data Service werden im asynchronen Modus an das Portal übermittelt, sodass es möglicherweise zu einer Verzögerung zwischen der Aktualisierung der Daten in Common Data Service und dem Zeitpunkt liegt, zu dem aktualisierte Daten im Portal angezeigt werden. Um diese Verzögerung zu vermeiden&mdash;beispielsweise, wenn Sie die Portal Konfiguration beeinträchtigt&mdash;können Sie das Portal zwingen, den Cache sofort zu aktualisieren.

> [!NOTE]
> Die SLA für die Cache Aktualisierung (Datenübertragung zwischen Common Data Service und dem Portal) beträgt 15 Minuten.

So löschen Sie den serverseitigen Cache

1.  Melden Sie sich beim Portal als Administrator an.

2.  Navigieren Sie wie folgt zur URL: `<portal_path>/_services/about`

3.  Wählen Sie **Cache löschen**aus. 

Der serverseitige Cache wird gelöscht, und die Daten werden aus Common Data Service erneut geladen. Beachten Sie, dass das Löschen des serverseitigen Cache Caches vorübergehend zu einer schlechten Leistung des Portals führt, während Daten aus Common Data Service neu geladen werden.

> [!div class=mx-imgBorder]
> ![Löschen des Portal]Caches(../media/clear-portal-cache.png "Löschen des Portal Caches")
