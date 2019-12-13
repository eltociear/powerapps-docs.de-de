---
title: Ausführen von Apps in einem Webbrowser | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie Apps in einem Webbrowser ausführen.
author: mduelae
ms.service: powerapps
ms.component: pa-user
ms.topic: quickstart
ms.date: 12/05/2019
ms.author: mkaur
manager: kvivek
ms.custom: ''
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8ce6cfe213817cd603857bb5ea2735b188f8cb6c
ms.sourcegitcommit: 15c6b26ff085928459ad9b3f52fb607fae4a997d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "74956782"
---
# <a name="run-an-app-in-a-web-browser"></a>Ausführen einer App in einem Webbrowser
Wenn Sie eine APP erstellen oder jemand eine APP für Sie freigibt, können Sie diese APP auf dem Dynamics 365-Mobile App oder einem Webbrowser auf einem Tablet ausführen. In diesem Thema erfahren Sie, wie Sie einen Canvas oder eine Modell gesteuerte app in einem Webbrowser auf einem Tablet auf der [Dynamics 365-Startseite](https://home.dynamics.com)ausführen.

Für eine vollständige Funktionalität und eine optimierte Funktionalität wird dringend empfohlen, dass Sie Dynamics 365 für Smartphones und Tablets Mobile App verwenden. Wenn Sie die APP Dynamics 365 für Smartphones und Tablets nicht installiert haben, können Sie weiterhin den Webbrowser auf Ihrem Tablet verwenden, sofern Ihr Gerät eine ausreichend hohe Bildschirmauflösung aufweist. Weitere Informationen finden Sie [unter: Was wird unterstützt](https://docs.microsoft.com/dynamics365/mobile-app/support-phones-tablets#supported-devices-for-the-mobile-app).

> [!NOTE]
> Die Verwendung des Webbrowsers auf Ihrem Telefon zum Ausführen von Modell gesteuerten apps wird nicht unterstützt. Sie müssen die Dynamics 365 für Smartphones-App verwenden.

Für diesen Schnellstart benötigen Sie Folgendes:
- Eine powerapps-Lizenz. Dies ist in einem powerapps-Plan verfügbar, z. b. in der [Testversion von powerapps Plan 2](https://docs.microsoft.com/powerapps/maker/signup-for-powerapps)oder einem der [Microsoft Office 365](https://signup.microsoft.com/Signup?OfferId=467eab54-127b-42d3-b046-3844b860bebf&dl=O365_BUSINESS_PREMIUM&ali=1) -oder [Dynamics 365](https://dynamics.microsoft.com/pricing/) -Pläne, die powerapps enthalten. 
- Zugriff auf eine App, die Sie erstellt haben oder die eine andere Person erstellt und für Sie freigegeben hat
- Zugriff auf einen unterstützten Webbrowser bzw. ein unterstütztes Betriebssystem
   - Für Canvas-Apps: [Systemanforderungen, Einschränkungen und Konfigurationswerte](../maker/canvas-apps/limits-and-config.md)
   - Für modellgesteuerte Apps: [Unterstützte Webbrowser und Mobilgeräte](https://docs.microsoft.com/dynamics365/customer-engagement/admin/supported-web-browsers-and-mobile-devices)


## <a name="sign-in-to-dynamics-365"></a>Anmelden bei Dynamics 365
Melden Sie sich unter [https://home.dynamics.com](https://home.dynamics.com) bei Dynamics 365 an.

## <a name="find-an-app-on-the-home-page"></a>Finden einer App auf der Startseite
Die Startseite zeigt möglicherweise verschiedene Arten von Geschäfts-Apps an. Sie können nach einer bestimmten App suchen, indem Sie einen Teil des App-Namens in das Suchfeld eingeben. Sie können die Liste auch filtern, sodass nur apps angezeigt werden, die von einer bestimmten Quelle, z. b. Power apps, erstellt wurden. Wählen Sie hierzu **Filter** aus, und wählen Sie dann die Quelle aus.

Wenn Sie eine App erst vor Kurzem installiert haben, wird sie möglicherweise nicht sofort in der Liste der Apps angezeigt. Wählen Sie **Synchronisieren** aus, um alle Ihre apps anzuzeigen. Dieser Vorgang kann bis zu einer Minute dauern.

![](./media/run-app-browser/dynamics-365-home.png)


## <a name="run-an-app-from-a-url"></a>Ausführen einer App über eine URL
Sie können die URL einer App als Lesezeichen im Browser Ihres Tablets speichern und ausführen, indem Sie das Lesezeichen auswählen, oder Sie können eine URL als Link per e-Mail senden. Wenn eine APP von einer anderen Person in einer e-Mail erstellt und für Sie freigegeben wurde, können Sie die app ausführen, indem Sie den Link in der e-Mail auswählen. Wenn Sie eine App über eine URL ausführen, werden Sie möglicherweise dazu aufgefordert, sich mit Ihren Azure Active Directory-Anmeldeinformationen anzumelden.

![](./media/run-app-browser/web-login.png)

## <a name="connect-to-data"></a>Herstellen einer Datenverbindung
Wenn eine App eine Verbindung mit einer Datenquelle oder die Berechtigung zur Nutzung von Funktionen des Geräts (z.B. Kamera oder Ortungsdienste) erfordert, müssen Sie Ihre Zustimmung erteilen, bevor Sie die App verwenden können. Normalerweise werden Sie nur beim ersten Mal aufgefordert.

![Connection](./media/run-app-browser/app-connection.png)

## <a name="close-an-app"></a>Schließen einer App
Melden Sie sich auf der Dynamics 365-Startseite ab, um eine App zu schließen, oder öffnen Sie eine andere App.

## <a name="next-steps"></a>Nächste Schritte
In diesem Artikel haben Sie erfahren, wie Sie eine Canvas-App oder eine modellgesteuerte App in einem Webbrowser ausführen. So lernen Sie Folgendes:
- Ausführen einer Canvas-App auf einem mobilen Gerät finden Sie unter [Ausführen einer Canvas-App auf einem mobilen Gerät](run-app-client.md)
- Ausführen einer Modell gesteuerten App auf einem mobilen Gerät finden Sie unter [Ausführen einer Modell gesteuerten App auf einem mobilen Gerät](run-app-client-model-driven.md) .
- Verwenden einer Modell gesteuerten App finden Sie unter [Verwenden von Modell gesteuerten apps](use-model-driven-apps.md) .

