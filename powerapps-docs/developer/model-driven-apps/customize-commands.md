---
title: Anpassen von Befehlen mit modellgesteuerten Apps | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Befehle mit modellgesteuerten Apps anpassen.
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: faisalmo
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/17/2018
ms.author: jdaly
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4721ba49fe227d31f539eabd863b50842e7515b6
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "42836252"
---
# <a name="customize-commands-with-model-driven-apps"></a>Anpassen von Befehlen mit modellgesteuerten Apps 

Befehle, die in der Befehlsleiste eines Formulars oder einer Liste angezeigt werden, können angepasst werden. Befehle basieren auf XML-Schemas, die in Office-Menübändern verwendet werden, daher wird weiterhin der Begriff *Menüband* verwendet. Beim Erstellen eines Befehls können Sie drei Elemente definieren:

- *Anzeigeregeln* werden ausgewertet, wenn das Formular oder die Liste geladen wird, um festzustellen, ob ein Befehl oder eine Gruppe sichtbar ist.
- *Aktivierungsregeln* steuern basierend auf verschiedenen Bedingungen, wie z.B. dem zu diesem Zeitpunkt in der Benutzeroberfläche ausgewählten Element, ob ein Befehl aktiviert ist.
- Eine *Aktion* für jeden Befehl, damit er seine Funktionen kennt. Ein Befehl kann eine URL öffnen oder eine Funktion ausführen, die in einer JavaScript-Webressource definiert ist.

Benutzerdefinierte Befehle werden basierend auf allen vorhandenen Befehlen positioniert. Sie müssen eine *benutzerdefinierte Aktion* zusammenstellen, die definiert, welche Änderungen für die vorhandenen Befehle gelten sollen. 

Für Befehle wird kein Designer bereitgestellt. Die Community hat jedoch Tools dafür bereitgestellt. Das Tool [Ribbon Workbench](http://www.develop1.net/public/rwb/ribbonworkbench.aspx) bietet eine grafische Benutzeroberfläche und ist das am häufigsten verwendete Tool zum Anpassen von Befehlen.

Weitere Informationen finden Sie unter [Entwicklerhandbuch zu Dynamics 365 Customer Engagement: Anpassen von Befehlen und des Menübands](/dynamics365/customer-engagement/developer/customize-dev/customize-commands-ribbon).


