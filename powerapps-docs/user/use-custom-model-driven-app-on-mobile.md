---
title: Verwenden einer modellgesteuerten App auf einem mobilen Gerät | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie eine benutzerdefinierte modellgesteuerte App auf einem mobilen Gerät verwenden.
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: quickstart
ms.date: 04/07/2020
ms.author: mkaur
ms.custom: ''
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1b1c0b6158bb19ed64bc70282aed2d4c62d07fe3
ms.sourcegitcommit: 597849e2942c88a5c54953eeb8f14c8c81ac0ae2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "3326200"
---
# <a name="user-guide-for-model-driven-apps-running-on-the-power-apps-mobile-app"></a>Benutzerhandbuch für in der mobilen Power Apps-App ausgeführte modellgesteuerte Apps

Verwenden Sie die mobile Power Apps-App, um modellgesteuerte Apps auf Ihrem mobilen Gerät auszuführen. Weitere Informationen zur Installation und zu den ersten Schritten mit einer App finden Sie unter [Ausführen von Canvas- und modellgesteuerten Apps auf einem mobilen Gerät](run-canvas-and-model-apps-on-mobile.md).

> [!IMPORTANT]
> Modellgesteuerte Apps für Dynamics 365 Sales, Dynamics 365 Customer Service und Dynamics 365 Field Service<!--For sure this list doesn't include Dynamics 365 Marketing, and Dynamics 365 Project Service Automation? That's the list of model-driven apps according to the Dynamics Style Guide.--> können in der mobilen Power Apps-App nicht ausgeführt werden. Stattdessen verwenden Sie die Dynamics 365-App für Smartphones und Tablets. Weitere Informationen finden Sie unter [Benutzerhandbuch (Dynamics 365 für Smartphones und Tablets)](https://docs.microsoft.com/dynamics365/mobile-app/dynamics-365-phones-tablets-users-guide).

## <a name="home-screen"></a>Startbildschirm 

Das Verwenden der mobilen Power Apps-Apps ist einfach und intuitiv. Auf der folgenden Abbildung werden die primären Navigationselemente auf dem Startbildschirm veranschaulicht. 

![Navigationssteuerelemente, erweiterte Ansicht](media/home_screen_iphone.png "Navigationssteuerelemente, erweiterte Ansicht")

Legende:

1. **Siteübersicht**: Öffnen Sie das Menü, und wechseln Sie z. B. zwischen Apps, rufen Sie häufig und vor Kurzem verwendete Datensätze auf, oder greifen Sie auf Einstellungen zu.
2. **Suche**: Suchen nach App-Datensätzen in Common Data Service.
3. **Schnellerfassung**: Wenn Sie einen neuen Datensatz erstellen, können Sie ohne Umschweife nahezu alle Arten von Informationen in das System eingeben.
4. **Kundenbeziehungsassistent**: Verwenden Sie den Assistenten, um tägliche Aktionen und Kommunikationen zu überwachen und zu verfolgen. Er erleichtert Ihnen mithilfe von Erkenntniskarten, die in der gesamten App an exponierter Stelle angezeigt werden und maßgeschneiderte und umsetzbare Erkenntnisse liefern, den Überblick über Ihren Tag zu behalten.

## <a name="site-map"></a>Siteübersicht 

Klicken Sie auf dem Startbildschirm auf die Siteübersicht ![Symbol „Siteübersicht“](media/pa_mobile_sitemap_icon.png "Symbol „Siteübersicht“"), um auf Entitäten, häufig oder zuletzt verwendete Datensätze, andere Apps und Einstellungen zuzugreifen.

 
   > [!div class="mx-imgBorder"]
   > ![Anzeige „Siteübersicht“](media/go_to_sitemap_iphone.gif "Diese Abbildung zeigt, wie Sie zum Bildschirm mit der Siteübersicht gelangen.")
   
 *Aktualisieren Sie die Seite, um die GIF-Aktion neu zu starten*.

Auf der folgenden Abbildung werden die primären Navigationselemente auf der Anzeige „Siteübersicht“ veranschaulicht. 

![Anzeige „Siteübersicht“](media/site_map_iphone.png "Anzeige „Siteübersicht“")

Legende

1. **App-Auswahl**: Öffnen Sie dieses Menü, um Ihre App zu schließen und zu einer anderen App zu wechseln.
2. **Startseite**: Klicken Sie auf diese Option, um zurück zum Startbildschirm zu wechseln.
3. **Profil**: Rufen Sie die Anzeige „Profil“ auf, um sich abzumelden oder die App neu zu konfigurieren. 
4. **Kürzlich verwendete Datensätze**: Sehen Sie sich eine Liste der Datensätze an, die Sie vor Kurzem verwendet haben. 
5. **Angeheftete Datensätze**: Sehen Sie sich Ihre häufig verwendeten (angehefteten) Datensätze an, und öffnen Sie sie. 
6. **Entitätsnavigator**: In diesem Bereich werden die Entitäten aufgeführt, die in der App verfügbar sind.
7. **Hilfe**: Greifen Sie auf Hilfeinhalte zu, um weitere Informationen zur Verwendung der mobilen Power Apps-App zu erhalten.
8. **Offlinestatus**: Verwenden von Daten im Offlinemodus, auch wenn Sie keinen Internet-Zugriff haben. Weitere Informationen: [Offline auf einem mobilen Gerät arbeiten](https://docs.microsoft.com/dynamics365/mobile-app/work-in-offline-mode)
9. **Einstellungen**: Greifen Sie auf die Einstellungen zu.

## <a name="pin-favorite-records"></a>Anheften häufig verwendeter Datensätze

Über die Listen **Angeheftet** und **Zuletzt verwendet** haben Sie schnellen Zugriff auf Datensätze, die Sie vor Kurzem verwendet oder als Favorit angeheftet haben. Verwenden Sie die Liste **Zuletzt verwendet**, um häufig verwendete Datensätze anzuheften.  

1. Klicken Sie auf der Siteübersicht ![Symbol „Siteübersicht“](media/pa_mobile_sitemap_icon.png "Symbol „Siteübersicht“") auf die Option **Zuletzt verwendet** ![Symbol „Zuletzt verwendet“](media/pa_mobile_recent_icon.png "Symbol für zuletzt verwendete Datensätze").

2. Klicken Sie auf der Datensatzanzeige **Zuletzt verwendet** auf das Stecknadelsymbol neben einem Datensatz, um diesen zu Ihren Favoriten (angeheftete Datensätze) hinzuzufügen.

3. Klicken Sie auf das ![Symbol „Zurück“](media/mobile_go_back_icon.png "Symbol „Zurück“"), und klicken Sie dann auf **Angeheftet** ![Symbol für angeheftete Favoriten](media/mobile_pinned_favs_icon.png "Symbol für angeheftete Favoriten"), um die neu angehefteten Datensätze anzuzeigen.


   > [!div class="mx-imgBorder"]
   > ![Anheften eines Datensatzes als Favorit](media/pin_favs.gif "Diese Abbildung zeigt, wie häufig verwendete Datensätze angeheftet werden.")
   
*Aktualisieren Sie die Seite, um die GIF-Aktion neu zu starten*.

### <a name="unpin-a-record"></a>Loslösen eines Datensatzes

1. Klicken Sie auf der Siteübersicht ![Symbol „Siteübersicht“](media/pa_mobile_sitemap_icon.png "Symbol „Siteübersicht“") auf die Option **Angeheftet** ![Symbol für angeheftete Favoriten](media/mobile_pinned_favs_icon.png "Symbol für angeheftete Favoriten").

2. Klicken Sie auf das Symbol zum Loslösen des Datensatzes ![Symbol für das Loslösen des Datensatzes](media/pa_mobile_remove_pin_icon.png "Symbol für das Loslösen eines Datensatzes") neben einem Datensatz, um ihn aus den Favoriten (angeheftete Datensätze) zu entfernen.


   > [!div class="mx-imgBorder"]
   > ![Loslösen eines Datensatzes](media/unpin_favs.gif "Diese Abbildung veranschaulicht, wie ein Datensatz losgelöst wird.")
   
*Aktualisieren Sie die Seite, um die GIF-Aktion neu zu starten*.

## <a name="change-views"></a>Ändern von Ansichten

- Klicken Sie auf dem Startbildschirm auf den Abwärtspfeil ![Symbol „Ansicht ändern“](media/mobile_view_selector_icon.png "Symbol für das Ändern einer Ansicht") neben der aktuellen Ansicht, und wählen Sie dann eine neue Ansicht aus.


   > [!div class="mx-imgBorder"]
   > ![Ändern von Ansichten](media/change_views_iphone.gif "In dieser Abbildung wird gezeigt, wie eine andere Ansicht ausgewählt wird.")

*Aktualisieren Sie die Seite, um die GIF-Aktion neu zu starten*.

## <a name="add-a-record-quickly"></a>Schnelles Hinzufügen eines Datensatzes

1. Klicken Sie auf dem Startbildschirm auf **Neu** ![Schaltfläche „Datensatz erstellen“](media/create-record-button.png "Schaltfläche „Datensatz erstellen“").
2. Füllen Sie die Felder aus, und wählen Sie dann **Speichern** aus.
3. Nachdem der Datensatz erstellt wurde, können Sie sich den neuen Datensatz ansehen. 

   > [!div class="mx-imgBorder"]
   > ![Erstellen eines Datensatzes](media/pamobile_add_record.gif "Diese Abbildung veranschaulicht, wie ein neuer Datensatz erstellt wird.")

*Aktualisieren Sie die Seite, um die GIF-Aktion neu zu starten*.

-  Wenn Sie den Datensatz, den Sie erstellt haben, speichern und öffnen möchten, klicken Sie auf **Mehr** ![Symbol „Weitere Befehle“](media/pa_mobile_more_commands_icon.png "Symbol für weitere Befehle"), und klicken Sie dann auf **Speichern und öffnen**.

- Wenn Sie den Datensatz, den Sie erstellt haben, speichern und einen weiteren erstellen möchten, klicken Sie auf **Mehr** ![Symbol „Weitere Befehle“](media/pa_mobile_more_commands_icon.png "Symbol für weitere Befehle"), und klicken Sie dann auf **Save and Create new** (Speichern und neu erstellen).

   > [!div class="mx-imgBorder"]
   > ![Erstellen eines Datensatzes](media/pa_mobile_save_create_new.gif "Diese Abbildung zeigt, wie ein Datensatz gespeichert und geöffnet oder ein neuer Datensatz erstellt und gespeichert wird.")

*Aktualisieren Sie die Seite, um die GIF-Aktion neu zu starten*.

## <a name="view-commands-for-a-record-android"></a>Anzeigen von Befehlen für einen Datensatz (Android)

1. Öffnen Sie auf dem Startbildschirm einen Datensatz.
2. Klicken Sie im geöffneten Datensatz auf **Mehr** ![Symbol für weitere Datensatzbefehle](media/access_record_commands_icon.png "Symbol für weitere Datensatzbefehle"), um Zugriff auf weitere Befehle zu erhalten.

   > [!div class="mx-imgBorder"]
   > ![Befehle für einen Datensatz](media/pa_mobile_view_record_commands.gif "Diese Abbildung zeigt, wie Sie auf weitere Befehle für einen Datensatz zugreifen.")

*Aktualisieren Sie die Seite, um die GIF-Aktion neu zu starten*.

## <a name="edit-a-record"></a>Datensatz bearbeiten

1. Öffnen Sie auf dem Startbildschirm einen Datensatz, den Sie bearbeiten möchten. 
2. Wenn Sie das Bearbeiten des Datensatzes abgeschlossen haben, klicken Sie auf **Speichern**. Um Ihre Änderungen zu verwerfen auf, klicken Sie auf **Verwerfen**.

   > [!div class="mx-imgBorder"]
   > ![Bearbeitung eines Datensatzes](media/save_on_iphone.gif "Diese Abbildung zeigt, wie ein Datensatz bearbeitet und dann gespeichert wird.")

*Aktualisieren Sie die Seite, um die GIF-Aktion neu zu starten*.

## <a name="go-back-to-the-home-screen"></a>Zurück zum Startbildschirm

- Wenn Sie sich in einem Datensatz befinden und zum Startbildschirm zurückkehren möchten, klicken Sie auf **Zurück** ![Symbol „Zurück“](media/pa_mobile_back_icon.png "Symbol „Zurück“").
- Sie können **Zurück** ![Symbol „Zurück“](media/pa_mobile_back_icon.png "Symbol „Zurück“") jederzeit drücken und gedrückt halten, um zurück auf den Startbildschirm zu gelangen. 

   > [!div class="mx-imgBorder"]
   > ![Zurück zum Startbildschirm](media/go_back_home.gif "Diese Abbildung zeigt, wie Sie durch Gedrückthalten des Symbols „Zurück“ zum Startbildschirm zurückkehren.")

*Aktualisieren Sie die Seite, um die GIF-Aktion neu zu starten*.

## <a name="sign-out"></a>Abmelden

Klicken Sie auf der Siteübersicht ![Symbol „Siteübersicht“](media/pa_mobile_sitemap_icon.png "Symbol „Siteübersicht“") auf das Profilsymbol ![Symbol „Profil“](media/profile_icon.png "Symbol „Siteübersicht“"), und klicken Sie dann auf **Abmelden**.
