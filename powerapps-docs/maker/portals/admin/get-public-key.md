---
title: Öffentlicher Schlüssel des Downloads eines Portals | MicrosoftDocs
description: Erfahren Sie, wie Sie einen öffentlichen Schlüssel von einem Portal herunterladen.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 8b74e1943e6a356884be167be033b7e633660b40
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "2977883"
---
# <a name="download-public-key-of-portal"></a>Den öffentlichen Schlüssel des Portals herunterladen

Der öffentliche Schlüssel eines Portale wird verwendet, um den Live Assist für modellgetriebene Anwendungen in Dynamics 365 zu konfigurieren, um mit authentifizierten Besuchern für ein Portal zu arbeiten. [Live Assist](https://www.cafex.com/en/products/live-assist-dynamics-365/), by CafeX, stellt eine Chat-Lösung bereit, über die Benutzer Live-Chat-Unterstützung in ihrem Portal erhalten. Weitere Informationen dazu, wie Sie den Schlüssel öffentliche verwenden, um auf einem der Chat Portale zu arbeiten [Authentifizierte Besucher im Dynamics Kunden-Portal](https://www.liveassistfor365.com/en/support/authenticated-visitors-in-the-dynamics-customer-portal/)

1. Öffnen Sie das [Admin Center für Power Apps-Portale](admin-overview.md).

2.  Öffnen Sie **Portalaktionen** > **Öffentlichen Schlüssel abrufen**. Der Schlüssel wird angezeigt.

    > [!div class=mx-imgBorder]
    > ![Abrufen von öffentlichen Schlüsseln des Portals](../media/get-public-key.png "Abrufen von öffentlichen Schlüsseln des Portals")

3.  Wählen Sie **Download als Text** aus, um den Schlüssel in einer Textdatei herunterzuladen.

Alternativ können Sie auch den öffentlichen Schlüssel erhalten, indem Sie auf die URL gehen: `<portal_base_URL>/_ services/auth/publickey` 

> [!NOTE]
> Wenn das Portal bereitgestellt wird oder die Installation des Pakets nicht abgeschlossen ist in der Organisation, wird ein Fehler angezeigt, wenn Sie versuchen, den öffentlichen Schlüssel herunterzuladen. Sie müssen warten bis die Portalbereitstellung vollständig ist und das Portal läuft.
