---
title: Herunterladen des öffentlichen Schlüssels eines Portals | MicrosoftDocs
description: Erfahren Sie, wie Sie den öffentlichen Schlüssel eines Portals herunterladen.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 39e909acb325bd870f73e16a72da78b4bec07c79
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975976"
---
# <a name="download-public-key-of-portal"></a>Herunterladen des öffentlichen Schlüssels eines Portals

Der öffentliche Schlüssel eines Portals wird zum Konfigurieren der Live Unterstützung für Modell gesteuerte apps in Dynamics 365 verwendet, um mit authentifizierten Besuchern für ein Portal zu arbeiten. [Live Assist](https://www.cafex.com/en/products/live-assist-dynamics-365/), von cafex, bietet eine Chat Lösung, über die Benutzer Live Chat Unterstützung in Ihrem Portal einbetten können. Weitere Informationen zur Verwendung des öffentlichen Schlüssels zum Einbetten eines Chats in einem Portal: [authentifizierte Besucher im Dynamics-Kundenportal](https://www.liveassistfor365.com/en/support/authenticated-visitors-in-the-dynamics-customer-portal/)

1. Öffnen Sie das [powerapps-Portal Admin Center](admin-overview.md).

2.  Wechseln Sie zu den **Portal Aktionen** , > **öffentlichen Schlüssel zu erhalten**. Der Schlüssel wird angezeigt.

    > [!div class=mx-imgBorder]
    > Öffentlichen ![Schlüssel eines Portals]zum(../media/get-public-key.png "öffentlichen") Schlüssel eines Portals erhalten

3.  Wählen Sie **als Text herunterladen** aus, um den Schlüssel in eine Textdatei herunterzuladen.

Alternativ können Sie den öffentlichen Schlüssel auch aufrufen, indem Sie zur URL: `<portal_base_URL>/_ services/auth/publickey` 

> [!NOTE]
> Wenn das Portal zurzeit bereitgestellt wird oder die Paketinstallation nicht in der Organisation abgeschlossen ist, wird ein Fehler angezeigt, wenn Sie versuchen, den öffentlichen Schlüssel herunterzuladen. Sie müssen warten, bis die Portal Bereitstellung fertiggestellt ist und das Portal ausgeführt wird.
