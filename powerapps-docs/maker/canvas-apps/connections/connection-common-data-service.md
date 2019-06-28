---
title: Verbinden mit Common Data Service | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine Verbindung mit Common Data Service herstellen und zum Erstellen von apps in PowerApps verwenden.
author: aftowen
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: ''
ms.date: 04/22/2019
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: da68abeec51df102647ea32a17b3d76451f2f1aa
ms.sourcegitcommit: 982cab99d84663656a8f73d48c6fae03e7517321
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/28/2019
ms.locfileid: "67456729"
---
# <a name="connect-to-common-data-service"></a>In Common Data Service herstellen

Sie können sicher speichern Ihre Geschäftsdaten in Common Data Service und rich-apps in PowerApps erstellen, sodass Benutzer Daten verwalten können. Sie können auch Daten integrieren, die in Lösungen, die Microsoft Flow und Power BI Daten aus Dynamics 365 enthalten.

Standardmäßig verbindet sich der Common Data Service-Connector auf Daten in der aktuellen Umgebung Ihrer app. Wenn Ihre app in einer anderen Umgebung verschoben wird, verbindet sich der Connector auf Daten in der neuen Umgebung. Dies eignet sich für eine app mit einer einzigen Umgebung oder eine app, die einen ALM-Prozess für das Verschieben von der Entwicklung, Test oder Produktion folgt.

Wenn Sie eine Datenquelle mit dem Common Data Service-Connector hinzufügen, können Sie die Umgebung ändern, und wählen Sie dann eine oder mehrere Entitäten. Standardmäßig verbindet sich die app Daten in der aktuellen Umgebung und die Benutzeroberfläche zeigt **(aktuellen)** über der Liste der Entitäten.

> [!div class="mx-imgBorder"]
> ![Standardumgebung](media/connection-common-data-service/common-data-service-connection-change-environment.png)

Bei Auswahl von **Änderung**, können Sie angeben eine andere Umgebung Daten daraus anstelle von oder zusätzlich zu der aktuellen Umgebung.

> [!div class="mx-imgBorder"]
> ![Andere Umgebungen](media/connection-common-data-service/common-data-service-connection-select-environment.png)

Der Name der ausgewählten Umgebung wird unter dem Suchfeld angezeigt.

> [!div class="mx-imgBorder"]
> ![Neue Umgebungen](media/connection-common-data-service/common-data-service-connection-after-change-environment.png)

Der Common Data Service-Connector ist robuster als die Dynamics 365-Connector und annähern Featureparität.

Weitere Informationen finden Sie unter: [Was ist Common Data Service?](../../common-data-service/data-platform-intro.md)
