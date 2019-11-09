---
title: Herstellen einer Verbindung mit Common Data Service | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine Verbindung mit Common Data Service herstellen und zum Entwickeln von apps in powerapps verwenden.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: ''
ms.date: 04/22/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0970cbd51f351352c218dab3f220c6d5baa35435
ms.sourcegitcommit: 0f0b26122be28d674af0833247b491e9367c4932
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73897760"
---
# <a name="connect-to-common-data-service"></a>Verbindung mit Common Data Service herstellen

Sie können Ihre Geschäftsdaten sicher in Common Data Service speichern und umfangreiche apps in powerapps erstellen, damit Benutzer diese Daten verwalten können. Sie können diese Daten auch in Lösungen integrieren, die Strom Automatisierung, Power BI und Daten aus Dynamics 365 enthalten.

Standardmäßig stellt der Common Data Service-Connector eine Verbindung mit Daten in der aktuellen Umgebung Ihrer APP her. Wenn Ihre APP in eine andere Umgebung verschoben wird, stellt der Connector eine Verbindung mit Daten in der neuen Umgebung her. Dieses Verhalten eignet sich gut für eine APP, die eine einzige Umgebung oder eine APP verwendet, die einem ALM-Prozess folgt, um von der Entwicklung zum Testen in die Produktion zu wechseln.

Wenn Sie eine Datenquelle mit dem Common Data Service-Connector hinzufügen, können Sie die Umgebung ändern und dann mindestens eine Entität auswählen. Standardmäßig stellt die APP eine Verbindung mit Daten in der aktuellen Umgebung her, und die Benutzeroberfläche zeigt **(aktuell)** über der Liste der Entitäten an.

> [!div class="mx-imgBorder"]
> ![Standardumgebung](media/connection-common-data-service/common-data-service-connection-change-environment.png)

Wenn Sie **ändern**auswählen, können Sie eine andere Umgebung zum Abrufen von Daten aus der IT anstelle von oder zusätzlich zur aktuellen Umgebung angeben.

> [!div class="mx-imgBorder"]
> ![andere Umgebungen](media/connection-common-data-service/common-data-service-connection-select-environment.png)

Der Name der ausgewählten Umgebung wird unter dem Suchfeld angezeigt.

> [!div class="mx-imgBorder"]
> neue Umgebungen ![](media/connection-common-data-service/common-data-service-connection-after-change-environment.png)

Der Common Data Service-Connector ist robuster als der Dynamics 365-Connector und nähert sich der Funktions Parität.

Weitere Informationen: [Was ist Common Data Service?](../../common-data-service/data-platform-intro.md)
