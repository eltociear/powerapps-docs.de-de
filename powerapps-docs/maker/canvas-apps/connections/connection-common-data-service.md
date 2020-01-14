---
title: Herstellen einer Verbindung mit Common Data Service | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine Verbindung mit Common Data Service herstellen und zum Entwickeln von apps in powerapps verwenden.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: ''
ms.date: 11/27/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e2b11b536c29a31053353f3c2616a594208e8acf
ms.sourcegitcommit: 54d52a9c3c9242f95be54f4444054d9c41ed577c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2020
ms.locfileid: "75928876"
---
# <a name="connect-to-common-data-service"></a>Verbindung mit Common Data Service herstellen

Sie können Ihre Geschäftsdaten sicher in Common Data Service speichern und umfangreiche apps in Power Apps erstellen, damit Benutzer diese Daten verwalten können. Sie können diese Daten auch in Lösungen integrieren, die Strom Automatisierung, Power BI und Daten aus Dynamics 365 enthalten.

Standardmäßig stellt der Common Data Service-Connector eine Verbindung mit Daten in der aktuellen Umgebung Ihrer APP her. Wenn Ihre APP in eine andere Umgebung verschoben wird, stellt der Connector eine Verbindung mit Daten in der neuen Umgebung her. Dieses Verhalten eignet sich gut für eine APP, die eine einzige Umgebung oder eine APP verwendet, die einem ALM-Prozess folgt, um von der Entwicklung zum Testen in die Produktion zu wechseln.

Wenn Sie eine Datenquelle mit dem Common Data Service-Connector hinzufügen, können Sie die Umgebung ändern und dann mindestens eine Entität auswählen. Standardmäßig stellt die APP eine Verbindung mit Daten in der aktuellen Umgebung her.

![Standardumgebung](media/connection-common-data-service/common-data-service-connection-change-environment.png)

Wenn Sie **ändern**auswählen, können Sie eine andere Umgebung zum Abrufen von Daten aus der IT anstelle von oder zusätzlich zur aktuellen Umgebung angeben.

![Andere Umgebungen](media/connection-common-data-service/common-data-service-connection-select-environment.png)

Der Name der ausgewählten Umgebung wird unter der Liste Entitäten angezeigt.

![Neue Umgebungen](media/connection-common-data-service/common-data-service-connection-after-change-environment.png)

Der Common Data Service-Connector ist robuster als der Dynamics 365-Connector und nähert sich der Funktions Parität.

Weitere Informationen: [Was ist Common Data Service?](../../common-data-service/data-platform-intro.md)
