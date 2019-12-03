---
title: Installieren und Konfigurieren des Beispiels „Help Desk“ für Canvas-Apps | Microsoft-Dokumentation
description: Schritt-für-Schritt-Anleitungen für, in powerapps, installieren und Konfigurieren des Helpdesk-Beispiels für Canvas-apps.
author: matthewbolanos
manager: kvivek
ms.service: powerapps
ms.topic: sample
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/29/2019
ms.author: mabolan
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 01fdadfd5ecf19d56ac115e53cef08a2cff2a254
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74729650"
---
# <a name="install-and-configure-the-help-desk-sample-in-power-apps"></a>Installieren und Konfigurieren des Helpdesk-Beispiels in powerapps

Schritt-für-Schritt-Anleitungen für, in powerapps, installieren und Konfigurieren des Helpdesk-Beispiels für Canvas-apps.

Geschätzte Dauer: **10–15 Minuten**.

> [!TIP]
> Eine Demonstration dieses Vorgangs finden Sie in diesem [Video](https://youtu.be/z4cdtD6hB_4).

## <a name="overview-of-the-sample"></a>Übersicht über das Beispiel

Der Helpdesk bietet eine benutzerfreundliche benutzerfreundliche Benutzerfreundlichkeit, um Endbenutzern eine Verbindung mit Supportmitarbeitern zu ermöglichen. Finden Sie schnell Antworten auf Ihre wichtigsten Fragen, verfolgen Sie den Fortschritt offener Tickets, und überprüfen Sie die Details vorheriger Anforderungen. Diese App erfordert ein geringes Maß an Einrichtung, um sie an Ihre Anforderungen anzupassen.

![Startbildschirm der PowerApps-App „Help Desk“](./media/help-desk-install/Login-screen.png)

> [!TIP]
> Sehen Sie sich dieses [Video](https://youtu.be/sl5fXwwnvzI) an, um mehr über die Verwendung der PowerApps-Beispiel-App „Help Desk“ zu erfahren.

## <a name="prerequisites"></a>Voraussetzungen

- [Registrieren Sie sich](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) für powerapps.
- Sie müssen über eine gültige SharePoint Online-Lizenz und Berechtigung zum Erstellen von Listen verfügen.

## <a name="create-the-helpdesk-sharepoint-list"></a>Erstellen der HelpDesk-SharePoint-Liste

In dieser Liste werden die Help Desk-Tickets gespeichert.

1. Öffnen Sie einen Webbrowser, und navigieren Sie zu https://admin.microsoft.com.
2. Melden Sie sich mit einem Konto an, das über die Berechtigung zum Erstellen von SharePoint-Listen verfügt.
3. Navigieren Sie zur Websitesammlung, in der Sie die Liste „HelpDesk“ erstellen möchten.
4. Klicken Sie auf das **Zahnradsymbol** oben rechts auf der Webseite.
5. Klicken Sie auf **Add an App** (Eine App hinzufügen).
6. Geben Sie im Textfeld **Eine App suchen** **Benutzerdefiniert** ein.
7. Klicken Sie auf das **Lupensymbol**.
8. Klicken Sie auf die App **Benutzerdefinierte Liste**.
9. Geben Sie im Textfeld **Name** den Namen **HelpDesk** ein.

    > [!IMPORTANT]
    > Wenn Sie einen anderen Namen für die Liste eingeben, schreiben Sie sich diesen auf, da Sie ihn während der Installation und Konfiguration überall dort eingeben müssen, wo „HelpDesk“ verwendet wird.

10. Klicken Sie auf **Erstellen**.

### <a name="create-description-column"></a>Erstellen der Spalte „Beschreibung“

1. Klicken Sie auf die Auslassungspunkte neben der HelpDesk-Liste, und klicken Sie auf **Einstellungen**.
2. Klicken Sie auf **Spalte erstellen**.
3. Geben Sie im Textfeld **Spaltenname** das Wort **Beschreibung** ein.
4. Klicken Sie in der Optionsfeldliste **Type of information in this column is** (Der Informationstyp dieser Spalte ist) auf **Mehrere Textzeilen**.
5. Klicken Sie in der Optionsfeldliste **Require that this column contains information** (Diese Spalte muss Informationen enthalten) auf **Ja**.
6. Wählen Sie in der Optionsfeldliste **Specify the type of text to allow** (Zu erlaubender Textyp auswählen) **Nur-Text** aus.
7. Klicken Sie auf **OK**.

### <a name="create-category-column"></a>Erstellen der Spalte „Kategorie“

1. Klicken Sie auf **Spalte erstellen**.
2. Geben Sie im Textfeld **Spaltenname** das Wort **Kategorie** ein.
3. Klicken Sie in der Optionsfeldliste **Type of information in this column is** (Der Informationstyp dieser Spalte ist) auf **Auswahl**.
4. Geben Sie im Textfeld **Geben Sie jede Auswahl in einer neuen Zeile ein** die folgenden Werte jeweils in einer neuen Zeile ein: 
    - LAPTOP/PC Geräteproblem
    - LAPTOP/PC Softwareproblem
5. Wählen Sie in der Optionsfeldliste **Eindeutige Werte erzwingen** den Wert **Nein** aus.
6. Wählen Sie in der Optionsfeldliste **Auswahl anzeigen durch** den Wert **Dropdownmenü** aus.
7. Geben Sie im Textfeld **Standardwert** den Wert **LAPTOP/PC Geräteproblem** an.
8. Klicken Sie auf **OK**.

### <a name="create-percentcomplete-column"></a>Erstellen der Spalte „% abgeschlossen“

1. Klicken Sie auf **Spalte erstellen**.
2. Geben Sie im Textfeld **Spaltenname** den Namen **% abgeschlossen** ein.
3. Klicken Sie in der Optionsfeldliste **Type of information in this column is** (Der Informationstyp dieser Spalte ist) auf **Number (1, 10, 100)** (Zahl (1, 10, 100)).
4. Klicken Sie in der Optionsfeldliste **Require that this column contains information** (Diese Spalte muss Informationen enthalten) auf **Nein**.
5. Klicken Sie auf **OK**.

### <a name="create-priority-column"></a>Erstellen der Spalte „Priorität“

1. Klicken Sie auf **Spalte erstellen**.
2. Geben Sie im Textfeld **Spaltenname** das Wort **Priorität** ein.
3. Klicken Sie in der Optionsfeldliste **Type of information in this column is** (Der Informationstyp dieser Spalte ist) auf **Auswahl**.
4. Geben Sie im Textfeld **Geben Sie jede Auswahl in einer neuen Zeile ein** die folgenden Werte jeweils in einer neuen Zeile ein: 
    - HOCH
    - Mittelalter
    - NIEDRIG
5. Wählen Sie in der Optionsfeldliste **Eindeutige Werte erzwingen** den Wert **Nein** aus.
6. Wählen Sie in der Optionsfeldliste **Auswahl anzeigen durch** den Wert **Dropdownmenü** aus.
7. Geben Sie im Textfeld **Standardwert** den Wert **NIEDRIG** ein.
8. Klicken Sie auf **OK**.

### <a name="create-taskstatus-column"></a>Erstellen der Spalte „TaskStatus“

1. Klicken Sie auf **Spalte erstellen**.
2. Geben Sie im Textfeld **Spaltenname** die Zeichenfolge **TaskStatus** ein.
3. Klicken Sie in der Optionsfeldliste **Type of information in this column is** (Der Informationstyp dieser Spalte ist) auf **Auswahl**.
4. Geben Sie im Textfeld **Geben Sie jede Auswahl in einer neuen Zeile ein** die folgenden Werte jeweils in einer neuen Zeile ein: 
    - NICHT GESTARTET
    - IN BEARBEITUNG
    - ABGESCHLOSSEN
    - ZURÜCKGESTELLT
    - WARTEN AUF CSR
5. Wählen Sie in der Optionsfeldliste **Eindeutige Werte erzwingen** den Wert **Nein** aus.
6. Wählen Sie in der Optionsfeldliste **Auswahl anzeigen durch** den Wert **Dropdownmenü** aus.
7. Geben Sie im Textfeld **Standardwert** den Wert **NICHT GESTARTET** ein.
8. Klicken Sie auf **OK**.

### <a name="create-assignedto-column"></a>Erstellen der Spalte „ZugewiesenAn“

1. Klicken Sie auf **Spalte erstellen**.
2. Geben Sie im Textfeld **Spaltenname** die Zeichenfolge **ZugewiesenAn** ein.
3. Klicken Sie in der Optionsfeldliste **Type of information in this column is** (Der Informationstyp dieser Spalte ist) auf **Person or Group** (Person oder Gruppe).
4. Klicken Sie in der Optionsfeldliste **Require that this column contains information** (Diese Spalte muss Informationen enthalten) auf **Nein**.
5. Wählen Sie in der Optionsfeldliste **Mehrfachauswahl zulassen** den Wert **NEIN** aus.
6. Klicken Sie auf **OK**.

### <a name="edit-title-column"></a>Bearbeiten der Spalte „Titel“

1. Klicken Sie auf den Link zur Spalte **Titel**.
2. Klicken Sie in der Optionsfeldliste **Require that this column contains information** (Diese Spalte muss Informationen enthalten) auf **Nein**.
3. Klicken Sie auf **OK**.

## <a name="download-the-app"></a>Herunterladen der APP

1.  [Laden](https://pappsfeprodwestuscontent.blob.core.windows.net/sampleapps/helpdesk/docs/HelpDesk(SP_List).zip) Sie das powerapps-Paket herunter, und speichern Sie es auf Ihrem Computer.

## <a name="create-connections"></a>Erstellen von Verbindungen

1.  Navigieren Sie in einem Webbrowser zu [make.powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).
2.  Melden Sie sich mit denselben Anmeldeinformationen an, die Sie bei der Registrierung verwendet haben.
3.  Wählen Sie im Menü auf der linken Seite **Daten** und dann **Verbindungen** aus.
    
### <a name="create-office-365-outlook-connection"></a>Erstellen einer Office 365 Outlook-Verbindung

1.  Klicken Sie auf **+ Neue Verbindung**.
2.  Geben Sie im **Suchfeld** die Verbindung **Office 365 Outlook** ein.
3.  Klicken Sie in der Liste auf **Office 365 Outlook**.
4.  Klicken Sie auf **Erstellen**.
5.  Wählen Sie im Popupfenster das Konto aus, mit dem Sie sich angemeldet haben.

### <a name="create-sharepoint-connection"></a>Erstellen einer SharePoint-Verbindung

1.  Klicken Sie auf **+ Neue Verbindung**.
2.  Geben Sie in das **Suchfeld** die Verbindung **SharePoint** ein.
3.  Klicken Sie in der Liste auf **SharePoint**.
4.  Klicken Sie auf **Erstellen**.
5.  Wählen Sie im Popupfenster das Konto aus, mit dem Sie sich angemeldet haben.

### <a name="create-office-365-users-connection"></a>Erstellen einer Office 365-Benutzer-Verbindung

1.  Klicken Sie auf **+ Neue Verbindung**.
2.  Geben Sie im **Suchfeld** die Verbindung **Office 365-Benutzer** ein.
3.  Wählen Sie in der Liste **Office 365-Benutzer** aus.
4.  Klicken Sie auf **Erstellen**.
5.  Wählen Sie im Popupfenster das Konto aus, mit dem Sie sich angemeldet haben.

## <a name="import-the-app"></a>Importieren der App

1. Navigieren Sie in einem Webbrowser zu https://make.powerapps.com.
2. Melden Sie sich mit denselben Anmeldeinformationen an, die Sie bei der Registrierung verwendet haben.
3. Wählen Sie im Menü auf der linken Seite **Apps** aus. 
4. Klicken Sie auf **Paket importieren (Vorschau)** .
    
   ![Anzeige „Paket importieren“](./media/help-desk-install/import-package.png)

5. Klicken Sie auf **Hochladen**, und wählen Sie das PowerApps-Paket aus, das Sie in den vorherigen Schritten heruntergeladen haben.
6. Legen Sie für die Ressourcentypen **App** und **Flow** für **IMPORTEINRICHTUNG** die Option **Als neu erstellen** fest.
7. Legen Sie für die Verbindungen **SharePoint** und **Outlook** für **IMPORTEINRICHTUNG** die Option **Beim Import auswählen** fest.
    
   ![Anzeige „Importeinstellungen“](./media/help-desk-install/import-settings.png)

8. Klicken Sie auf das **rote Symbol** für die **SharePoint-Verbindung**.
9. Klicken Sie in der Verbindungsliste auf das Element mit ihrem Benutzernamen.

   ![Anzeige „Importeinstellungen“](./media/help-desk-install/import-settings-sharepoint.png)

10. Klicken Sie auf **Speichern**.
11. Klicken Sie auf das **rote Symbol** für die **Office 365 Outlook-Verbindung**.
12. Klicken Sie in der Verbindungsliste auf das Element mit ihrem Benutzernamen.

    ![Anzeige „Importeinstellungen“](./media/help-desk-install/import-settings-office365outlook.png)

13. Klicken Sie auf **Speichern**.

    > [!TIP] 
    > Anschließend wird Folgendes auf dem Bildschirm angezeigt:

    ![Anzeige „Importeinstellungen“](./media/help-desk-install/import-settings-done.png)

14. Klicken Sie auf **Importieren**, und warten Sie, bis der Vorgang abgeschlossen ist.

    ![Anzeige „Importeinstellungen“](./media/help-desk-install/import-done.png)

## <a name="configure-the-app-to-use-the-sharepoint-list"></a>Konfigurieren der APP für die Verwendung der SharePoint-Liste

1. Klicken Sie unter „Nächste Schritte“ auf **App öffnen**.
2. Klicken Sie auf **Zulassen**, wenn Sie dazu aufgefordert werden.

### <a name="delete-connections"></a>Löschen von Verbindungen

1. Klicken Sie auf der Registerkarte **Ansicht** auf die Option **Datenquellen**.
1. Klicken Sie im Bereich **Daten** auf die Auslassungs Punkte (...) neben **Helpdesk**, und wählen Sie dann **Entfernen**aus.

### <a name="helpdesk-list"></a>HelpDesk-Liste

1. Klicken Sie auf der Registerkarte **Ansicht** auf die Option **Datenquellen**.
1. Klicken Sie im Bereich **Daten** auf **Datenquelle hinzufügen** > **Neue Verbindung** > **SharePoint** > **Erstellen**.
1. Wählen Sie in der Liste **Zuletzt geöffnete Websites** die SharePoint-Website aus, auf der Sie die HelpDesk-Liste erstellt haben.

    > [!TIP] 
    > Wenn die Website nicht in der Liste angezeigt wird, geben Sie die URL der SharePoint-Website in das Textfeld ein oder fügen Sie sie dort ein, und klicken Sie auf **Los**.

1. Geben oder fügen Sie im **Suchfeld** am oberen Rand der Liste **Helpdesk**ein.
1. Aktivieren Sie das Kontrollkästchen neben **Helpdesk**, und wählen Sie dann **verbinden**aus.

### <a name="update-admin-list"></a>Aktualisieren der Administratorliste

1. Klicken Sie auf **LoginScreen** (Startseite).
2. Wählen Sie in der Dropdownliste **OnStart** (Beim Start) aus.
3. Erweitern Sie das Formelfenster, und suchen die Sammlung **AdminList**.
4. Ersetzen Sie <strong>user@microsoft.com</strong> durch Ihre HelpDesk-Administratoren.

    ![Aktualisieren der Administratorliste](./media/help-desk-install/Change-admin.png)
    
   > [!TIP]
   > Wenn Sie über mehr als einen Administrator verfügen, verwenden Sie ein Komma, um die Liste der Administratoren zu begrenzen. Beispiel: "admin1@microsoft.com","admin2@microsoft.com".
   > Um sicherzustellen, dass die Adressen in der adminlist dem Format entsprechen, das von powerapps erwartet wird, wählen Sie > Variablen anzeigen > Global > myProfile aus, und betrachten Sie die Spalte "Mail", um das erwartete e-Mail-Format

1. Klicken Sie auf **Datei** > **Speichern** > **Veröffentlichen** > **Diese Version veröffentlichen**.

## <a name="modify-the-flow"></a>Ändern des Flows

1.  Klicken Sie links im Menü auf **Flows**.
2.  Wenn Sie dazu aufgefordert werden, melden Sie sich mit denselben Anmeldeinformationen an, die Sie bei der Registrierung verwendet haben.
3.  Wählen Sie im oberen Menü **Meine Flows** aus.
4.  Klicken Sie neben dem Flow **helpdeskflow** auf das Stift Symbol. 
 
    ![Anzeige „Flow bearbeiten“](./media/help-desk-install/edit-flow.png)

5.  Erweitern Sie die Aktion **Elemente abrufen**. 
6.  Passen Sie die **Websiteadresse** und den **Listennamen** so an, dass sie der HelpDesk-SharePoint-Liste entsprechen, die Sie erstellt haben.
    
    ![Anzeige „Flow bearbeiten“](./media/help-desk-install/edit-flow-getitems.png)

    > [!TIP] 
    > Sie müssen keine manuelle Angabe machen, sondern können in der Dropdownliste eine Auswahl treffen.

7.  Erweitern Sie den **Schalter**.
8.  Erweitern Sie den Fall **NICHT GESTARTET**.
9.  Erweitern Sie die Aktion **Case not started** (Fall nicht gestartet).
10. Ändern Sie das Feld **An**, sodass der Inhalt der E-Mail-Adresse des HelpDesk-Administrators entspricht.

    ![Anzeige „Flow bearbeiten“](./media/help-desk-install/edit-flow-condition-send-email.png) 

11. Klicken Sie auf **Flow aktualisieren**.

## <a name="play-the-app"></a>Ausführen der App

1. Klicken Sie im Webbrowser auf **Apps**.
2. Klicken Sie neben der Helpdesk-App auf die Auslassungs Punkte (...).
3. Klicken Sie auf **Öffnen**. 

> [!TIP]
> Sehen Sie sich dieses [Video](https://youtu.be/sl5fXwwnvzI) an, um mehr über die Verwendung der PowerApps-Beispiel-App „Help Desk“ zu erfahren.

## <a name="next-steps"></a>Nächste Schritte
- [Anpassen eines SharePoint-Listenformulars mit PowerApps](https://docs.microsoft.com/powerapps/maker/canvas-apps/customize-list-form)
- [Hinzufügen und Konfigurieren eines Steuerelements in PowerApps](https://docs.microsoft.com/powerapps/maker/canvas-apps/add-configure-controls)
- [Bearbeiten und Verwalten von Berechtigungen für eine SharePoint-Liste oder -Bibliothek](https://support.office.com/article/edit-and-manage-permissions-for-a-sharepoint-list-or-library-02d770f3-59eb-4910-a608-5f84cc297782)
