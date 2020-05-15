---
title: Ausführen von Canvas- und modellgesteuerten Apps auf einem mobilen Gerät | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie eine Canvas-App oder eine benutzerdefinierte modellgesteuerte App auf einem mobilen Gerät ausführen.
author: mduelae
ms.service: powerapps
ms.component: pa-user
ms.topic: quickstart
ms.date: 04/30/2020
ms.author: mkaur
ms.custom: ''
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d7690cdab07c32b740e058f905ab9d96df7c1bba
ms.sourcegitcommit: 597849e2942c88a5c54953eeb8f14c8c81ac0ae2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "3326104"
---
# <a name="run-canvas-apps-and-model-driven-apps-on-a-mobile-device"></a>Ausführen von Canvas- und modellgesteuerten Apps auf einem mobilen Gerät

Wenn Sie eine App erstellen oder eine Person&mdash;entweder eine Canvas- oder eine modellgesteuerte App&dash;für Sie freigibt, können Sie diese App auf iOS- und Android-Geräten mithilfe der mobilen Power Apps-App ausführen. Wenn Sie ein Windows-Gerät verwenden, können Sie nur Canvas-Apps ausführen. Modellgesteuerte Apps werden in der mobilen Power Apps-App für Windows-Geräte nicht unterstützt. In diesem Thema erhalten Sie grundlegende Informationen zu Canvas-Apps und modellgesteuerten Apps und erfahren, wie Sie sie auf Ihrem mobilen Gerät ausführen. 

Informationen zum Verwenden modellgesteuerter Apps, die in der mobilen Power Apps -App ausgeführt werden, finden Sie unter [Benutzerhandbuch für in der mobilen Power Apps ausgeführte modellgesteuerte Apps](use-custom-model-driven-app-on-mobile.md).

> [!IMPORTANT]
> Modellgesteuerte Apps für Dynamics 365 Sales, Dynamics 365 Customer Service, Dynamics 365 Field Service, Dynamics 365 Marketing und Dynamics 365 Project Service Automation<!--Via Dynamics Style Guide. If this sentence doesn't apply to all these products, maybe only mention Sales, Customer Service, and Field Service as you do in use-custom-model-driven-app-on-mobile.md? "Dynamics verticals" is out of brand.--> können in der mobilen Power Apps-App nicht ausgeführt werden. Stattdessen verwenden Sie die Dynamics 365-App für Smartphones und Tablets. Weitere Informationen: [Benutzerhandbuch für Dynamics 365 für Smartphones und Tablets](https://docs.microsoft.com/dynamics365/mobile-app/dynamics-365-phones-tablets-users-guide)

![Smartphone Power Apps](media/powerappsmobile.png "Mobile Power Apps-Benutzeroberfläche")

Legende:

1. **Modellgestützte Apps**
2. **Canvas-Apps**

**Installieren von Smartphone Power Apps**

Wenn Sie noch nicht für Power Apps registriert sind, [registrieren Sie sich kostenlos](https://make.powerapps.com/signup?redirect=marketing&email=). Laden Sie dann Power Apps aus dem [App Store](https://itunes.apple.com/app/powerapps/id1047318566?mt=8) oder von [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.msapps) auf ein iPhone, ein iPad oder Android-Gerät mit einem [unterstützten Betriebssystem](../maker/canvas-apps/limits-and-config.md) herunter. Anschließend können Sie diese Prozedur ausführen. Überprüfen Sie außerdem, ob Sie Zugriff auf eine Canvas-App haben, die Sie erstellt haben oder die eine andere Person erstellt und für Sie freigegeben hat.


## <a name="open-power-apps-and-sign-in"></a>Öffnen von Power Apps und Anmeldung

Öffnen Sie Power Apps auf Ihrem mobilen Gerät und melden Sie sich mit Ihren Azure Active Directory-Anmeldeinformationen an.

![Anmelden bei Power Apps](media/powerapps_mobile_app_signin_screen.png "Bei Power Apps anmelden")

Wenn auf Ihrem mobilen Gerät die Microsoft Authenticator-App installiert ist, müssen Sie nur Ihren Benutzernamen eingeben, wenn Sie dazu aufgefordert werden und über die Benachrichtigung, die dann an Ihr Gerät gesendet wird, eine Genehmigung senden.


## <a name="find-the-app"></a>Finden der App

Wenn Sie sich bei der App anmelden, ist der Filter **Meine Apps** standardmäßig festgelegt. Wenn Sie die gesuchte App nicht finden können, können Sie das **Power Apps**-Menü öffnen und dann einen anderen Filter auswählen. 


![App-Filter](media/filter-menu.png "App-Filter")

Die folgenden Filter sind verfügbar:

* **Alle Apps**: Es werden alle Canvas- und modellgesteuerten Apps angezeigt, auf die Sie Zugriff haben, einschließlich von Ihnen erstellte Apps und Apps, die andere für Sie freigegeben haben.

* **Meine Apps**: Bei Canvas-Apps werden bei diesem Filter Canvas-Apps angezeigt, die Sie geöffnet haben, Apps, deren Besitzer Sie sind, und Apps, die Sie bearbeiten können. Bei modellgesteuerten Apps werden durch diesen Filter alle modellgesteuerten Apps angezeigt, auf die Sie Zugriff haben 

* **Beispiel-Apps** (nur Canvas-Apps): Zeigt Beispiel-Apps von Microsoft an, in denen reale Anwendungsszenarien mit fiktiven Daten vorgestellt werden, um Sie bei der Untersuchung von Designmöglichkeiten zu unterstützen.

* **Favoriten** (nur Canvas-Apps): Bei diesem Filter werden Canvas-Apps angezeigt, die Sie markiert haben, indem Sie auf der App-Kachel auf die Auslassungspunkte (…) geklickt und dann die Option **Favorit** ausgewählt haben. Wenn Sie eine App aus der Liste entfernen möchten, klicken Sie erst auf die Auslassungspunkte (…) auf der App-Kachel und anschließend auf **Aus Favoriten entfernen**.

    ![Markieren als Favorit](media/add_favorite_app.png "Als Favorit markieren")

* **Ausgewählte Apps** (nur Canvas-Apps): Zeigt Canvas-Apps an, die Ihr Administrator als ausgewählte Apps markiert hat.

### <a name="sort-apps"></a>Sortieren von Apps

Nachdem Sie Ihre Apps gefiltert haben, können Sie die gefilterte Liste entweder nach dem Datum, an dem die Apps das letzte Mal geöffnet oder geändert wurden, oder nach Namen sortieren. Diese Einstellungen werden beibehalten, wenn Sie Apps schließen und erneut öffnen. Sie können sowohl Canvas-Apps als auch modellgesteuerte Apps sortieren.

![Menü zur Sortierung](media/sort_apps.png "Menü zur Sortierung")

### <a name="search-apps"></a>Apps durchsuchen

Wenn Sie den Namen der App kennen, die Sie ausführen möchten, können Sie erst im oberen Bereich auf das Suchsymbol klicken und anschließend den Anfang des App-Namens in das Suchfeld eingeben. Sie können sowohl nach Canvas-Apps als auch nach modellgesteuerten Apps suchen.

![Suche nach Apps](media/search_apps.png "Suche nach Apps")

Wenn Sie Ihre Apps gefiltert haben, wird die gefilterte Liste durchsucht.

### <a name="refresh-the-list-of-apps"></a>Aktualisieren der App-Liste

Klicken Sie auf das Symbol „Aktualisieren“, ![Symbol zum Aktualisieren](media/refresh_icon.png) um die App-Liste zu aktualisieren. Dadurch wird die Liste sowohl der Canvas-Apps als auch der modellgesteuerten Apps aktualisiert. 

## <a name="pin-an-app-to-the-home-screen"></a>Anheften einer App an den Startbildschirm

Sie können sowohl Canvas- als auch modellgesteuerte Apps an den Startbildschirm Ihres Geräts anheften, um schnell darauf zugreifen zu können. Klicken Sie erst auf der App-Kachel auf die Auslassungspunkte (…), dann auf **An Startseite anheften**, und folgen Sie den Anweisungen, die daraufhin angezeigt werden.

![Anheften einer App](media/pin_to_home.png "Anheften einer App")

## <a name="see-non-production-apps"></a>Anzeigen von Nicht-Produktions-Apps

Standardmäßig werden nur modellgesteuerte Produktions-Apps in der App-Liste angezeigt.

Wenn modellgesteuerte Apps aus Nicht-Produktionsumgebungen angezeigt werden sollen, klicken Sie auf das Menü **Einstellungen** ![Symbol „Einstellungen“](media/settings_icon.png), und aktivieren Sie dann **Show non-production apps** (Nicht-Produktions-Apps anzeigen). Befolgen Sie die angezeigten Anweisungen.

![Umschalter für das Anzeigen von Nicht-Produktions-Apps](media/non_prod_toggle.png "Umschalter für das Anzeigen von Nicht-Produktions-Apps")

## <a name="run-an-app"></a>Ausführen einer App

Klicken Sie auf die App-Kachel, um eine App auf einem mobilen Gerät auszuführen. Wenn ein anderer Benutzer eine App erstellt und diese per E-Mail für Sie freigibt, können Sie die App über den Link in der E-Mail ausführen.

### <a name="run-a-canvas-app"></a>Ausführen einer Canvas-App

Wenn Sie zum ersten Mal eine Canvas-App ausführen, indem Sie die mobile Power Apps-App verwenden, wird Ihnen eine Anzeige angezeigt, auf der die Wischgesten erläutert werden.

#### <a name="close-a-canvas-app"></a>Schließen einer Canvas-App

Wenn Sie eine App schließen möchten, wischen Sie mit Ihrem Finger von links nach rechts über die App. Auf Android-Geräten können Sie auch die Taste Zurück drücken und anschließend bestätigen, dass Sie die App schließen möchten.

![Schließen einer App](media/swipe.gif "Schließen einer App")

#### <a name="pinch-and-zoom-in-on-a-canvas-app"></a>Zwei-Finger-Zoom in einer Canvas-App

![Zwei-Finger-Zoom](media/pinchtozoom.jpg "Zwei-Finger-Zoom")

#### <a name="give-consent-to-a-canvas-app"></a>Erteilen der Zustimmung für eine Canvas-App

Wenn eine App eine Verbindung mit einer Datenquelle oder die Berechtigung zur Nutzung von Funktionen des Geräts (z.B. Kamera oder Ortungsdienste) erfordert, müssen Sie Ihre Zustimmung erteilen, bevor Sie die App verwenden können. Normalerweise werden Sie nur bei erstmaliger Ausführung der App dazu aufgefordert.

![Erteilen der Zustimmung](media/give_consent_canvas.jpg "Erteilen der Zustimmung")

### <a name="run-a-model-driven-app"></a>Ausführen einer modellgesteuerten App 

Auf dem folgenden Bild sehen Sie ein Beispiel für die Anzeige einer modellgesteuerten App, nachdem Sie sich angemeldet haben. Informationen zum Verwenden modellgesteuerter Apps, die in der mobilen Power Apps -App ausgeführt werden, finden Sie unter [Benutzerhandbuch für in der mobilen Power Apps ausgeführte modellgesteuerte Apps](use-custom-model-driven-app-on-mobile.md). 

![Startseite einer modellgesteuerten App](media/model-driven-app-opened.png "Startseite einer modellgesteuerten App")

#### <a name="give-consent-to-a-model-driven-app"></a>Erteilen der Zustimmung für eine modellgesteuerte App

Wenn eine App eine Verbindung mit einer Datenquelle oder die Berechtigung zur Nutzung von Funktionen des Geräts (z.B. Kamera oder Ortungsdienste) erfordert, müssen Sie Ihre Zustimmung erteilen, bevor Sie die App verwenden können. Normalerweise werden Sie nur beim ersten Ausführen der App dazu aufgefordert.

![Erteilen der Zustimmung](media/give_consent.png "Erteilen der Zustimmung")

#### <a name="close-a-model-drive-app"></a>Schließen einer modellgesteuerten App

Klicken Sie auf „Siteübersicht“ ![Symbol „Siteübersicht“](media/pa_mobile_sitemap_icon.png "Symbol „Siteübersicht“"), und klicken Sie dann auf **Apps**.

![Schließen einer modellgesteuerten App](media/pa_mobile_close_app.png "Schließen einer modellgesteuerten App")



