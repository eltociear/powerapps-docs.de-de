---
title: Herstellen einer Verbindung mit Common Data Service | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine Verbindung mit Common Data Service herstellen und zum Entwickeln von apps in powerapps verwenden.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/04/2020
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 227482b383acd3117cc78eddf97698ffa9146698
ms.sourcegitcommit: 56c8c7cc64695ccb00e0d021c9f98cf70b69b4a2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78845190"
---
# <a name="connect-to-common-data-service"></a>Verbindung mit Common Data Service herstellen

## <a name="overview"></a>Übersicht

Sie können Ihre Geschäftsdaten sicher in Common Data Service speichern und umfangreiche apps in Power Apps erstellen, damit Benutzer diese Daten verwalten können. Sie können diese Daten auch in Lösungen integrieren, die Strom Automatisierung, Power BI und Daten aus Dynamics 365 enthalten.

Standardmäßig stellt der Common Data Service-Connector eine Verbindung mit Daten in der aktuellen Umgebung Ihrer APP her. Wenn Ihre APP in eine andere Umgebung verschoben wird, stellt der Connector eine Verbindung mit Daten in der neuen Umgebung her. Dieses Verhalten eignet sich gut für eine APP, die eine einzige Umgebung oder eine APP verwendet, die einem ALM-Prozess folgt, um von der Entwicklung zum Testen in die Produktion zu wechseln.

Wenn Sie eine Datenquelle mit dem Common Data Service-Connector hinzufügen, können Sie die Umgebung ändern und dann mindestens eine Entität auswählen. Standardmäßig stellt die APP eine Verbindung mit Daten in der aktuellen Umgebung her.

![Standardumgebung](media/connection-common-data-service/common-data-service-connection-change-environment.png)

Wenn Sie **ändern**auswählen, können Sie eine andere Umgebung zum Abrufen von Daten aus der IT anstelle von oder zusätzlich zur aktuellen Umgebung angeben.

![Andere Umgebungen](media/connection-common-data-service/common-data-service-connection-select-environment.png)

Der Name der ausgewählten Umgebung wird unter der Liste Entitäten angezeigt.

![Neue Umgebungen](media/connection-common-data-service/common-data-service-connection-after-change-environment.png)

Der Common Data Service-Connector ist robuster als der Dynamics 365-Connector und nähert sich der Funktions Parität.

### <a name="common-data-service-and-the-improved-data-source-experience"></a>Common Data Service und die verbesserte Datenquelle

Wenn Sie eine Canvas-App mit einem Common Data Service-Connector vor dem 2019. November erstellt haben, haben Sie möglicherweise nicht den Vorteil der aktuellen Version des Common Data Service. Weitere Details und ein Upgrade der Verbindung finden Sie unter [Verbesserungen der Verbindung Common Data Service](../use-native-cds-connector.md) .