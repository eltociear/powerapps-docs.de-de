---
title: Die Homepage von ISV Studio | Microsoft Docs
description: Erfahren Sie mehr über die Homepagefunktionen, die vom ISV Studio-Portal bereitgestellt werden.
services: ''
suite: powerapps
documentationcenter: na
author: phecke
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.reviewer: pehecke
ms.workload: na
ms.date: 07/11/2019
ms.author: prkoduku
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 7ad26853dd63163672cd3a981251a57dd7735857
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748277"
---
# <a name="the-home-page"></a>Die Homepage

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Nach der Anmeldung eines Benutzers in ISV Studio wird ihm die Angebotsseite angezeigt, die als *Homepage* bezeichnet wird. Eine Begrüßungsnachricht wird angezeigt, die die Zielsetzung dieser Seite definiert.

Wenn ein Benutzer mehreren Herausgebern zugeordnet ist, werden alle Herausgeber angezeigt und der erste wird standardmäßig ausgewählt. Alle Metriken auf dieser Seite beziehen sich speziell auf den ausgewählten Herausgeber. Der Benutzer kann zu einem anderen Herausgebernamen wechseln, um die entsprechenden Metriken für diesen Herausgeber anzuzeigen.

![Homepage](media/isv-portal-homepage.png)

Der Homepage-Übersichtsabschnitt enthält die folgenden Diagramme und Metriken.

## <a name="successful-app-package-installs-by-tenant"></a>Erfolgreiche App-Paketinstallationen nach Mandant

Das erste Diagramm veranschaulicht die veröffentlichten Apps und Mandanten, in denen die App-Pakete installiert wurden, und sie werden in absteigender Reihenfolge nach der Nummer der Paketinstallation angezeigt.

Beim Hovern über eine Mandantenkachel im Diagramm werden die folgenden Informationen angezeigt:

1. App-Name
2. Mandantenname und Mandanten-ID
3. Anzahl der Paketinstallationen der App im Mandanten

![Paketinstallationen nach Mandant](media/isv-portal-homepage-graph1.png)

## <a name="package-install-attempts-by-app-last-28-days"></a>Paketinstallationsversuche nach App (letzte 28 Tage)

Dieses Balkendiagramm veranschaulicht veröffentlichte Apps und die Anzahl der erfolgreichen und fehlerhaften Installationen in allen Produktionsumgebungen in den letzten 28 Tagen.

Beim Hovern über eine Diagramm-App werden die folgenden Informationen angezeigt:

1. App-Name
2. Status der Paketinstallation (erfolgreich und fehlerhaft)
3. Anzahl der Paketinstallationsversuche

![Paketinstallationsversuche nach App (letzte 28 Tage)](media/isv-portal-homepage-graph2.png)

## <a name="additional-insights"></a>Weitere Erkenntnisse

Unterhalb des Übersichts-Abschnitts können Benutzer auf zusätzliche Erkenntnisse zugreifen und die Installationshistorie aus Sicht der zertifizierten Apps oder Mandanten noch detaillierter anzeigen.

**Die wichtigsten zertifizierten Apps** und **Die wichtigsten Mandanten** werden standardmäßig auf der Seite angezeigt. Der Benutzer kann auch **Alle anzeigen** auswählen, um alle Apps anzuzeigen.

Die App-Namen und -Symbole stammen von AppSource.

![Alle Apps](media/isv-portal-homepage-seeall.png)

### <a name="see-also"></a>Siehe auch

[Einführung in ISV Studio für die Power Platform](isv-app-management.md)  
[App-Seite](isv-app-management-apppage.md)  
[Mandantenseite](isv-app-management-tenantpage.md)
