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
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "74956782"
---
# <a name="run-an-app-in-a-web-browser"></a>Ausführen einer App in einem Webbrowser
Wenn Sie eine App erstellen oder jemand eine App für Sie freigibt, können Sie diese App in der mobilen Dynamics 365-App oder in einem Webbrowser auf einem Tablet ausführen. In diesem Artikel erfahren Sie, wie Sie eine Canvas-App oder eine modellgesteuerte App über die [Dynamics 365-Startseite](https://home.dynamics.com) in einem Webbrowser auf einem Tablet ausführen.

Für vollständige Funktionalität und optimierte Benutzererfahrung wird jedoch dringend die Verwendung der mobilen Dynamics 365-App für Smartphones und Tablets empfohlen. Wenn Sie Dynamics 365 für Smartphones und Tablets nicht installiert haben, können Sie trotzdem den Webbrowser auf Ihrem Tablet verwenden, sofern Ihr Gerät eine ausreichend hohe Bildschirmauflösung aufweist. Weitere Informationen finden Sie unter: [Unterstützte Funktionen](https://docs.microsoft.com/dynamics365/mobile-app/support-phones-tablets#supported-devices-for-the-mobile-app)

> [!NOTE]
> Die Verwendung des Webbrowsers auf Ihrem Smartphone zum Ausführen von modellgesteuerten Apps wird nicht unterstützt. Sie müssen die Dynamics 365-App für Smartphones verwenden.

Für diesen Schnellstart benötigen Sie Folgendes:
- Eine Power Apps-Lizenz. Diese ist in einem Power Apps-Plan wie der [Testversion für den Power Apps-Plan 2](https://docs.microsoft.com/powerapps/maker/signup-for-powerapps) oder in den [Microsoft Office 365](https://signup.microsoft.com/Signup?OfferId=467eab54-127b-42d3-b046-3844b860bebf&dl=O365_BUSINESS_PREMIUM&ali=1)- oder [Dynamics 365](https://dynamics.microsoft.com/pricing/)-Plänen enthalten, in denen Power Apps enthalten ist. 
- Zugriff auf eine App, die Sie erstellt haben oder die eine andere Person erstellt und für Sie freigegeben hat
- Zugriff auf einen unterstützten Webbrowser bzw. ein unterstütztes Betriebssystem
   - Informationen zu Canvas-Apps finden Sie unter: [Systemanforderungen, Einschränkungen und Konfigurationswerte](../maker/canvas-apps/limits-and-config.md)
   - Informationen zu modellgesteuerten Apps finden Sie unter [Unterstützte Webbrowser und Mobilgeräte](https://docs.microsoft.com/dynamics365/customer-engagement/admin/supported-web-browsers-and-mobile-devices)


## <a name="sign-in-to-dynamics-365"></a>Anmelden bei Dynamics 365
Melden Sie sich unter [https://home.dynamics.com](https://home.dynamics.com) bei Dynamics 365 an.

## <a name="find-an-app-on-the-home-page"></a>Finden einer App auf der Startseite
Die Startseite zeigt möglicherweise verschiedene Arten von Geschäfts-Apps an. Sie können nach einer bestimmten App suchen, indem Sie einen Teil des App-Namens in das Suchfeld eingeben. Sie können die Liste ebenfalls filtern, damit nur Apps angezeigt werden, die von einer bestimmten Quelle (z. B. Power Apps) erstellt wurden. Klicken oder tippen Sie dafür auf **Filter**, und wählen Sie anschließend die Quelle aus.

Wenn Sie eine App erst vor Kurzem installiert haben, wird sie möglicherweise nicht sofort in der Liste der Apps angezeigt. Wählen Sie **Synchronisieren** aus, um Ihre Apps anzuzeigen. Dieser Vorgang kann bis zu einer Minute dauern.

![](./media/run-app-browser/dynamics-365-home.png)


## <a name="run-an-app-from-a-url"></a>Ausführen einer App über eine URL
Sie können die URL einer App als Lesezeichen in dem Browser Ihres Tablets speichern und diese ausführen, indem Sie auf das Lesezeichen klicken oder tippen. Sie können eine URL ebenfalls per E-Mail als Link versenden. Wenn ein anderer Benutzer eine App erstellt und diese per E-Mail für Sie freigibt, können Sie die App über den Link in der E-Mail ausführen. Wenn Sie eine App über eine URL ausführen, werden Sie möglicherweise dazu aufgefordert, sich mit Ihren Azure Active Directory-Anmeldeinformationen anzumelden.

![](./media/run-app-browser/web-login.png)

## <a name="connect-to-data"></a>Verbinden mit Daten
Wenn eine App eine Verbindung mit einer Datenquelle oder die Berechtigung zur Nutzung von Funktionen des Geräts (z.B. Kamera oder Ortungsdienste) erfordert, müssen Sie Ihre Zustimmung erteilen, bevor Sie die App verwenden können. Normalerweise werden Sie nur beim ersten Mal dazu aufgefordert.

![Verbindung](./media/run-app-browser/app-connection.png)

## <a name="close-an-app"></a>Schließen einer App
Melden Sie sich auf der Dynamics 365-Startseite ab, um eine App zu schließen, oder öffnen Sie eine andere App.

## <a name="next-steps"></a>Nächste Schritte
In diesem Artikel haben Sie erfahren, wie Sie eine Canvas-App oder eine modellgesteuerte App in einem Webbrowser ausführen. Eine entsprechende Anleitung
- zum Ausführen einer Canvas-App auf einem mobilen Gerät finden Sie unter [Ausführen einer Canvas-App auf einem mobilen Gerät](run-app-client.md).
- zum Ausführen einer modellgesteuerten App auf einem mobilen Gerät finden Sie unter [Ausführen einer modellgesteuerten App auf einem mobilen Gerät](run-app-client-model-driven.md).
- zum Verwenden einer modellgesteuerten App finden Sie unter [Verwenden von modellgesteuerten Apps](use-model-driven-apps.md).

