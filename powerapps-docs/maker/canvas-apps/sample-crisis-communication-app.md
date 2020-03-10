---
title: App-Beispiel Vorlage für die Krisenkommunikation | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Beispiel Vorlage für die Krisenkommunikation in powerapps.
author: matthewbolanos
manager: kvivek
ms.service: powerapps
ms.topic: sample
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/06/2020
ms.author: mabolan
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7dd989bcd87e910812bf41509585c31c1fc107a9
ms.sourcegitcommit: a02b20113164acb11955d27ef4ffa421ee0fba9d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "78971008"
---
# <a name="set-up-and-learn-about-the-crisis-communication-sample-template-in-power-apps"></a>Einrichten und Erlernen der Beispiel Vorlage für die Krisenkommunikation in Power apps

Hier finden Sie Schritt-für-Schritt-Anleitungen zum Installieren und Konfigurieren der App zur Krisenkommunikation für Power apps.

Geschätzte Zeit zum Ausführen dieser Schritte: **20-25 Minuten**

## <a name="overview-of-the-app"></a>Übersicht über die APP

Die APP zur *Krisenkommunikation* bietet eine benutzerfreundliche benutzerfreundliche Benutzerfreundlichkeit, um Endbenutzern eine Verbindung mit Informationen zu einer Krise zu ermöglichen. Holen Sie sich schnell Aktualisierungen zu internen Unternehmensnachrichten, erhalten Sie Antworten auf häufig gestellte Fragen, und erhalten Sie Zugriff auf wichtige Informationen wie Links und Notfallkontakte. Diese App erfordert ein geringes Maß an Einrichtung, um sie an Ihre Anforderungen anzupassen.

In dieser exemplarischen Vorgehensweise lernen Sie Folgendes:
- Erstellen Sie einen Speicherort für Ihre Daten.
- Importieren Sie sowohl die APP zur Krisenkommunikation als auch Ihre Administrator-app.
- Erstellen von Inhalten für die APP
- Importieren von Flows zum Senden von Benachrichtigungen an Benutzer
- Erstellen eines zentral verwalteten Teams-Teams, um Daten zu aggregieren und effektiv auf Probleme zu reagieren

## <a name="prerequisites"></a>Erforderliche Komponenten

- [Registrieren Sie sich](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) für powerapps.
- Sie müssen über eine gültige SharePoint Online-Lizenz verfügen und über die Berechtigung zum Erstellen von Listen verfügen.
- Sie müssen über eine öffentliche SharePoint-Website verfügen, auf der Sie die Daten für die APP speichern können.
- Laden Sie die Assets aus [aka.ms/CrisisCommunicationSolution](https://aka.ms/CrisisCommunicationSolution)herunter.

## <a name="create-a-home-for-your-data"></a>Erstellen eines Zuhause für Ihre Daten

Die Daten für die APP werden in SharePoint-Listen angezeigt. Zuerst müssen wir eine neue SharePoint-Website erstellen, um zu beginnen.

### <a name="create-a-sharepoint-site"></a>Erstellen einer SharePoint-Website

1. Melden Sie sich bei [Office Online](https://www.office.com) an, und wählen Sie **SharePoint**aus.
1. Wählen Sie Website erstellen aus, und klicken Sie auf Weiter:

    ![Beispiel einer SharePoint-Website](media/sample-crisis-communication-app/01-Create-Site.png)

1. Team Website auswählen:

    ![Team Website](media/sample-crisis-communication-app/02-Team-Site.png)

1. Benennen Sie Ihre Website mit einem Namen und einer Beschreibung.
1. Legen Sie die Datenschutzeinstellungen auf "Public" fest, damit alle Benutzer im Unternehmen die erforderlichen Informationen erhalten können:

    ![Websiteeinstellungen](media/sample-crisis-communication-app/03-Privacy-Settings.png)

1. Wählen Sie Weiter aus.
1. Optional können Sie weitere Besitzer hinzufügen.
1. Wählen Sie Fertig stellen aus.

### <a name="create-the-sharepoint-lists-for-app"></a>Erstellen der SharePoint-Listen für die APP
Die APP erfordert mehrere Listen, in denen alle Daten gespeichert werden. Zum Automatisieren der Erstellung der SharePoint-Listen können Sie den *deploysplists* -Flow verwenden, der im heruntergeladenen [Assets-Paket](#prerequisites)verfügbar ist.

#### <a name="import-the-sharepoint-list-deployment-flow"></a>Importieren des SharePoint-Listen Bereitstellungs Flusses
1. Gehe zu [Flow.Microsoft.com](https://flow.microsoft.com)
1. Wählen Sie **meine Flows** im linken Navigationsbereich aus.
1. Klicken Sie in der Befehlsleiste auf die Schaltfläche **importieren** .
1. Laden Sie das Paket **deploysplist. zip** aus dem GitHub-Repository hoch.

    ![Paket importieren](media/sample-crisis-communication-app/import-package.png)

1. Fügen Sie eine SharePoint-Verbindung für den neuen Flow hinzu, indem Sie den Link **Select during Import** auswählen und das Formular ausfüllen.

    ![Importeinstellungen](media/sample-crisis-communication-app/import-settings.png)

1. Wenn Sie eine neue SharePoint-Verbindung erstellen müssen, wählen Sie im Bereich Import einrichten die Option **neu erstellen** aus.
1. Wählen Sie in der Befehlsleiste **neue Verbindung** aus:

    ![Erstellen einer neuen Verbindung](media/sample-crisis-communication-app/create-connection.png)

1. Suchen Sie nach dem Namen der Verbindung, z. b. *SharePoint*.
1. Wählen Sie die entsprechende Verbindung aus.
1. Wählen Sie **Speichern** aus.
1. Wählen Sie **Importieren** aus.

#### <a name="edit-the-sharepoint-list-deployment-flow"></a>Bearbeiten des Bereitstellungs Flusses für die SharePoint-Liste

1. Nachdem der Import abgeschlossen ist, kehren Sie zu **meine Flows** zurück, und aktualisieren Sie die Liste der Flows.
1. Wählen Sie die neu importierte Flow **deploysplist**aus.
1. Klicken Sie in der Befehlsleiste auf **Bearbeiten** .
1. Öffnen Sie die Karte **Variable – Zielwebsite für Listen**.
1. Ändern Sie den Wert in den Namen Ihrer SharePoint-Website.
1. Öffnen Sie die Karte **Variable – App Name**.
1. Ändern Sie den Wert in den Namen Ihrer APP. Standardmäßig ist dies "Krisenkommunikation".

    ![Fluss Parameter](media/sample-crisis-communication-app/04-Flow-Settings.png)

1. Wählen Sie **Speichern** , um die Änderungen zu übertragen.

#### <a name="run-the-sharepoint-list-deployment-flow"></a>Ausführen des Bereitstellungs Flows für die SharePoint-Liste

1. Wechseln Sie zurück zum Detailbildschirm für den **deploysplist-Flow.**
1. Klicken Sie in der Befehlsleiste auf **Ausführen** .
1. Wählen Sie **weiter** und dann **Flow ausführen** aus, um den Flow zu starten.

    ![Melden Sie sich an, um den Flow auszuführen.](media/sample-crisis-communication-app/sign-in-flow.png)

    ![Ausführen des Flows](media/sample-crisis-communication-app/run-flow.png)

> [!NOTE]
> Möglicherweise wird eine Fehlermeldung angezeigt, die besagt, dass Standortdienste erforderlich sind.
Wenn dies der Fall ist, gestatten Sie den Standort Diensten das Automatisieren und Aktualisieren der Seite, bevor Sie es erneut versuchen.

Der Flow erstellt dann die folgenden SharePoint-Listen auf der SharePoint-Website:

| **Anzeige Titel**| **Zweck** | **Beschreibung** |
|-|-|-|
| CI_LogosAssets| Zum Speichern von Logos und/oder anderen Bildern, auf die von der APP verwiesen werden soll. Auf das Logo wird in powerapps über einen direkten Link oder über die ID-Nummer des gewünschten Logos verwiesen. | Bibliothek für Verwandte Logos und andere Image Ressourcen für die app "[App-Name]". |
| CI_configAdminSetup | Für die featurekonfiguration durch den Administrator des Tools. **Hinweis**: Diese Liste sollte nur für alle Mitglieder gelesen werden, die keine Administratoren sind. | Die Administrator Konfigurationsliste für die app "[App-Name]".
| CI_Contacts | Verwenden des Inhaltstyps Standard Kontakte zum Erfassen von Informationen über Kontakte. (Keine Personen Auswahl eingeschlossen – daher ist eine Wartung erforderlich, um sicherzustellen, dass die Daten auf dem neuesten Stand sind.)  **Hinweis**: Dies hängt vom Typ der globalen Kontaktliste als Standard Inhaltstyp in der Liste ab. | Die Kontaktliste für die app "[App-Name]".|
| CI_CompanyNews | Sammlung von Unternehmens-News Items. | Liste für die Verwaltung von News Items, die in der App "[App-Name]" sichtbar sind. Mithilfe der veralteten Spalte können News Items aus der APP herausgefiltert werden (wobei Sie als Datensatz beibehalten werden). | 
| CI_FAQ  | Frequently asked questions. | Häufig gestellte Fragen zur App "[App-Name]". Die veraltete Spalte kann verwendet werden, um FAQ-Elemente aus der APP zu filtern (wobei Sie als Datensatz beibehalten werden). |
| CI_UsefullLinks | Liste der nützlichen Hyperlinks | Hilfreiche Hyperlinks-Liste für die app "[App-Name]". Die veraltete Spalte kann verwendet werden, um Hyperlink-Elemente aus der APP herauszufiltern (wobei Sie als Datensatz beibehalten werden). |
| CI_Employee | Der aktuelle Anwesenheitsstatus der Mitarbeiter wird nachverfolgt. Beispiele: *Arbeiten von der Startseite aus* *nicht krank*; *bei persönlichen verlassen*; und *im Urlaub*.  **Hinweis**: Es wird davon ausgegangen, dass die *Arbeit funktioniert* und nicht in den Listen Optionen enthalten ist. | Hilfreiche Hyperlinks-Liste für die app "[App-Name]". Mithilfe der veralteten Spalte können Verknüpfungs Elemente aus der APP herausgefiltert werden (wobei Sie als Datensatz beibehalten werden). |
| CI_HelpfulTips             | Benutzer können hilfreiche Tipps für Peers einbringen. | Liste für die Verwaltung von freigegebenen Tipps für die app "[App-Name]". Die veraltete Spalte kann zum Entfernen von Tipps aus den App-Ansichten verwendet werden (wobei Sie als Datensatz in SpO beibehalten werden).  |

> [!NOTE]
> - Alle oben aufgeführten Listen Spalten sollten als Abhängigkeiten angesehen werden.
    Schützen Sie die Listen vor versehentlichen Schema Änderungen (z. b. das Hinzufügen neuer Spalten ist zulässig, aber das Löschen von Spalten kann die APP unterbrechen).
> - Beim Löschen von Listenelementen Vorsicht walten lassen; durch das Löschen von Listenelementen werden historische Datensätze gelöscht. Sie können den veralnungs Wert von *Nein* auf *Ja* umschalten, um Datensätze aus Kontakten, Nachrichten, FAQs oder Links zu löschen.

## <a name="import-and-set-up-the-crisis-communication-app"></a>Importieren und Einrichten der App zur Krisenkommunikation

Nachdem Sie alle SharePoint-Listen erstellt haben, können Sie nun die App importieren und mit ihren neuen Datenquellen verbinden.

> [!NOTE]
> Wenn Sie die admin-APP nicht verwenden möchten, können Sie diese Eigenschaften auch bearbeiten, indem Sie die SharePoint-Listen manuell bearbeiten.

### <a name="import-the-app"></a>Importieren der App

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.
1. Wählen Sie im linken Navigationsbereich **apps** aus.
1. Klicken Sie in der Befehlsleiste auf **importieren** .
1. Laden Sie die Datei **crisiscommunication. zip** aus dem GitHub-Repository hoch:

    > [!NOTE]
    > Wenn sich Ihr Mandant in der gcc-Umgebung befindet, verwenden Sie **crisiscommunicationgcc. zip**.

    ![App-Paket importieren](media/sample-crisis-communication-app/31-Import-App.png)

1. Vervollständigen Sie die Verbindung Setup **für Microsoft Teams-Verbindung** und **Office 365-Benutzer** **importieren** , indem Sie die entsprechenden Verbindungen mithilfe von *Select during Import* Hyperlink auswählen. Möglicherweise müssen Sie eine [neue Verbindung](add-data-connection.md) erstellen, wenn Sie bereits vorhanden ist.
1. Wählen Sie **Importieren** aus.

### <a name="update-the-sharepoint-connections"></a>Aktualisieren der SharePoint-Verbindungen

1. Wechseln Sie zurück zur Liste der **apps** .
1. Wählen Sie **Weitere Befehle** (...) für die APP für die **Krisenkommunikation** aus.
1. Wählen Sie im Kontextmenü die Option **Bearbeiten** aus:

    ![Bearbeiten einer App](media/sample-crisis-communication-app/05-Edit-App.png)

1. **Melden Sie sich an** , oder erstellen Sie erforderliche Verbindungen, und wählen Sie **zulassen**:

    ![Verbindungen zulassen](media/sample-crisis-communication-app/allow-connections.png)

1. Navigieren Sie im linken Bereich zu den Datenquellen:

    ![Datenquellen](media/sample-crisis-communication-app/data-sources.png)

1. **Entfernen** Sie vorhandene SharePoint-Listen in der APP, da Sie nicht auf Ihre aktuelle SharePoint-Website verweisen:

    ![Entfernen von Datenquellen](media/sample-crisis-communication-app/remove-data-source.png)

1. Fügen Sie die Listen von ihrer eigenen SharePoint-Website hinzu. Starten Sie, indem Sie in der Suchleiste nach SharePoint suchen:

    ![SharePoint durchsuchen](media/sample-crisis-communication-app/sharepoint.png)

1. Wählen Sie **SharePoint** , und wählen Sie eine Verbindung aus:

    ![SharePoint-Verbindung](media/sample-crisis-communication-app/sharepoint-connection.png)

1. Kopieren Sie die URL, und fügen Sie Sie in das Textfeld ein, und wählen Sie **verbinden**aus:

    ![URL der SharePoint-Website](media/sample-crisis-communication-app/site-url.png)

1. Wählen Sie alle SharePoint-Listen und-Bibliotheken aus, und klicken Sie auf **verbinden**:

    ![Herstellen einer Verbindung mit SharePoint-Listen](media/sample-crisis-communication-app/sharepoint-lists.png)

1. **Speichern** und **veröffentlichen** Sie die app.

#### <a name="disable-location-updates"></a>Speicherort Aktualisierungen deaktivieren

Diese APP zeichnet einen Benutzer Speicherort auf und speichert ihn auf der SharePoint-Website, wenn ein Benutzer seinen Status festlegt. Dadurch kann Ihr Krisenmanagementteam diese Daten in einem Power BI Bericht anzeigen.

Um diese Funktion zu deaktivieren, führen Sie die folgenden Schritte aus:

  1. Suchen nach dem **btndaterange** -Steuerelement
  1. Öffnen **Sie die onselect** -Eigenschaft des **btndaterante** -Steuer Elements in der Bearbeitungs Leiste.
  1. Kopieren Sie den folgenden Code Ausschnitt, und fügen Sie ihn in die Bearbeitungs Leiste für die **onselect** -Eigenschaft ein:

  ```
  UpdateContext({locSaveDates: true});

// Store the output properties of the calendar in static variables and collections.
Set(varStartDate,First(Sort(Filter(selectedDates,ComponentId=CalendarDatePicker_1.Id),Date,Ascending)).Date);
Set(varEndDate,First(Sort(Filter(selectedDates,ComponentId=CalendarDatePicker_1.Id),Date,Descending)).Date);

// Create a new record for work status for each date selected in the date range.
ForAll(
    Filter(
        RenameColumns(selectedDates,"Date","DisplayDate"),
        ComponentId=CalendarDatePicker_1.Id,
        !(DisplayDate in colDates.Date)
    ),
    Patch('CI_Employee Status',Defaults('CI_Employee Status'),
        {
            Title: varUser.userPrincipalName,
            Date: DisplayDate,
            Notes: "",
            PresenceStatus: LookUp(Choices('CI_Employee Status'.PresenceStatus),Value=WorkStatus_1.Selected.Value),
            
             
            Latitude: Blank(),
            Longitude: Blank()
        }
    )
);

// Update existing dates with the new status.
ForAll(
    AddColumns(
        Filter(
            RenameColumns(selectedDates,"Date","DisplayDate"),
            ComponentId=CalendarDatePicker_1.Id,
            DisplayDate in colDates.Date
        ),
        
        // Get the current record for each existing date.
        "LookUpId",LookUp(RenameColumns(colDates,"ID","DateId"),And(Title=varUser.userPrincipalName,Date=DisplayDate)).DateId
    ),
    Patch('CI_Employee Status',LookUp('CI_Employee Status',ID=LookUpId),
        {
            PresenceStatus: LookUp(Choices('CI_Employee Status'.PresenceStatus),Value=WorkStatus_1.Selected.Value)
        }
    )
);

If(
    IsEmpty(Errors('CI_Employee Status')),
    Notify("You successfully submitted your work status.",NotificationType.Success,5000);
    
    // Update the list of work status for the logged-in user.
    ClearCollect(colDates,Filter('CI_Employee Status',Title=varUser.userPrincipalName));
    
    Navigate('Share to Team Screen',LookUp(colStyles,Key="navigation_transition").Value),
    
    Notify(
        LookUp(colTranslations,Locale=varLanguage).WorkStatusError,
        NotificationType.Warning
    )
);

UpdateContext({locSaveDates: false})
```

### <a name="update-the-request-help-flow"></a>Aktualisieren des Anforderungs Hilfe Flusses

Dieser Flow sendet eine Adaptive Karte an ein zentrales Teams-Team, das die Hilfe anfordert.

![App-Paket importieren](media/sample-crisis-communication-app/21-Request-Help.png)

Bevor Sie den folgenden Schritt ausführen, erstellen Sie zunächst ein Teams-Team für Ihr Krisenmanagementteam. Sobald Sie dies getan haben, können Sie die ID für Sie erhalten und in den Flow bringen. Wenn Sie Hilfe beim Erstellen eines Teams-Teams benötigen, fahren Sie mit dem Erstellen eines Teams für das [zentrale Krisenmanagementteam](#create-a-central-crisis-management-teams-team)fort.

1. Navigieren Sie zum kanalchannel, an den Sie alle Ihre Hilfeanfragen senden möchten.
1. Wählen Sie das Menü **...** für den Kanal aus.
1. Wählen Sie **Link zum Kanal erhalten**aus.

    ![Link zum Kanal erhalten](media/sample-crisis-communication-app/17-Get-link-to-channel.png)

1. Kopieren Sie den Link, und fügen Sie ihn in einen Texteditor ein.

    ![Link kopieren](media/sample-crisis-communication-app/18-Copy-link.png)

1. Extrahieren Sie die Team-ID. Dies ist alles nach `groupId=` und vor `&tenantId=`. <br> In der folgenden URL würde die Kanal-ID z. b. `8bc7c0c2-0d4c-4fb8-af99-32da74c9237b`lauten:
   
   `https://teams.microsoft.com/l/channel/19%3ab2fa9fc20f3042a9b63fc5890e1813f8%40thread.tacv2/General?groupId=8bc7c0c2-0d4c-4fb8-af99-32da74c9237b&tenantId=72f988bf-86f1-41af-91ab-2d7cd011db47`,
   
1. Extrahieren Sie die Kanal-ID, die alles nach `https://teams.microsoft.com/l/channel/` und vor `/General`ist. <br> In der folgenden URL würde die Kanal-ID z. b. `19%3ab2fa9fc20f3042a9b63fc5890e1813f8%40thread.tacv2`lauten:
   
   `https://teams.microsoft.com/l/channel/19%3ab2fa9fc20f3042a9b63fc5890e1813f8%40thread.tacv2/General?groupId=8bc7c0c2-0d4c-4fb8-af99-32da74c9237b&tenantId=72f988bf-86f1-41af-91ab-2d7cd011db47`,

1. Navigieren Sie zu [Flow.Microsoft.com](https://flow.microsoft.com).

1. Wählen Sie **meine Flows** im linken Navigationsbereich aus.

1. **Weitere Befehle** auswählen (...)  Wählen Sie für **crisiscommunication. Request** die Option **Bearbeiten**aus.

    ![Bearbeiten einer App](media/sample-crisis-communication-app/20-Edit-Flow.png)

1. Öffnen Sie die **TeamID** -Karte.

1. Fügen Sie die Team-ID in das **Wertfeld** ein.

1. Öffnen Sie die Karte **Channel ID** .

1. Fügen Sie die Kanal-ID in das **Wertfeld** ein.

    ![Team-IDs festlegen](media/sample-crisis-communication-app/22-Set-Team-IDs.png)

1. Führen Sie einen Bildlauf nach unten zu den Aktionen **Get Time** aus, und aktualisieren Sie die Aktion für **Zeit Zone konvertieren** in die gewünschte Quell-und Ziel Zeit:

    ![Zeitzone konvertieren](media/sample-crisis-communication-app/convert-time-zone.png)

## <a name="import-and-set-up-the-admin-app"></a>Importieren und Einrichten der admin-App

Um die APP zu verwalten, die Sie importiert haben, sollten Sie die gleichen Schritte für die admin-App wiederholen.

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.
1. Wählen Sie im linken Navigationsbereich **apps** aus.
1. Klicken Sie in der Befehlsleiste auf **importieren** .
1. Laden Sie die Datei **crisiscommunicationadminapp. zip** aus dem GitHub-Repository hoch:

    ![App-Paket importieren](media/sample-crisis-communication-app/import-app.png)

1. Wählen Sie **Importieren** aus.

### <a name="update-the-sharepoint-connections"></a>Aktualisieren der SharePoint-Verbindungen

1. Wechseln Sie zurück zur Liste der **apps** .
1. Wählen Sie **Weitere Befehle** (...) für die APP-App-App für die **Krisenkommunikation** aus.
1. Wählen Sie im Kontextmenü die Option **Bearbeiten** aus:

    ![Bearbeiten einer App](media/sample-crisis-communication-app/08-Edit-Admin-App.png)

1. **Melden Sie sich an** , oder erstellen Sie erforderliche Verbindungen, und wählen Sie **zulassen**

1. Navigieren Sie im linken Bereich zu den Datenquellen:

    ![Datenquellen](media/sample-crisis-communication-app/data-sources.png)

1. **Entfernen** Sie vorhandene SharePoint-Listen in der APP, da Sie nicht auf Ihre aktuelle SharePoint-Website verweisen:

    ![Entfernen von Datenquellen](media/sample-crisis-communication-app/remove-data-source.png)

1. Fügen Sie die Listen von ihrer eigenen SharePoint-Website hinzu. Starten Sie, indem Sie in der Suchleiste nach SharePoint suchen:

    ![SharePoint durchsuchen](media/sample-crisis-communication-app/sharepoint.png)

1. Wählen Sie **SharePoint** , und wählen Sie eine Verbindung aus:

    ![SharePoint-Verbindung](media/sample-crisis-communication-app/sharepoint-connection.png)

1. Kopieren Sie die URL, und fügen Sie Sie in das Textfeld ein, und wählen Sie **verbinden**aus:

    ![URL der SharePoint-Website](media/sample-crisis-communication-app/site-url.png)

1. Wählen Sie alle SharePoint-Listen und-Bibliotheken aus, und klicken Sie auf **verbinden**:

    ![Herstellen einer Verbindung mit SharePoint-Listen](media/sample-crisis-communication-app/sharepoint-lists.png)

1. **Speichern** und **veröffentlichen** Sie die admin-app.

## <a name="create-initial-content-for-the-app"></a>Erstellen des anfänglichen Inhalts für die APP

Sie haben die APP für die Krisenkommunikation und Ihre Administrator-App erfolgreich importiert.

Sie können nun mit dem Erstellen des anfänglichen Inhalts beginnen. Öffnen Sie zunächst die Verwaltungs-App für die Krisenkommunikation.

![Admin-App](media/sample-crisis-communication-app/09-Admin-App.png)

Mithilfe der Admin-Anwendung können Sie alle Informationen in der App zur Krisenkommunikation anpassen und die Schlüssel Einstellungen für die zugehörigen Flows einrichten.

> [!NOTE]
> Wenn Sie die admin-APP nicht verwenden möchten, können Sie die gleichen Eigenschaften auch bearbeiten, indem Sie die SharePoint-Listen manuell bearbeiten.

### <a name="setup-key-parameters-under-admin-settings"></a>Einrichten von Schlüsselparametern unter "Administrator Einstellungen"

Um die APP zu initialisieren, müssen Sie alle erforderlichen Felder bereitstellen, indem Sie zu den **Administrator Einstellungen**navigieren.

Füllen Sie alle Felder aus, und wählen Sie **Speichern**aus.

| **Feldname** | **Logischer Name in SharePoint** | **Zweck** |
|-|-|-|
| E-Mail mit Administrator Berechtigungen | "Admincontactemail" | Wird verwendet, um andere Personen zu benachrichtigen, die die Anwendung verwalten. |
| Logo-URL | Logo | Das Logo Ihrer APP, das in der linken oberen Ecke angezeigt wird. |
| Aad-Gruppen-ID | Aadgroupid | Wird zum Senden von Benachrichtigungen an Endbenutzer über interne Unternehmens Updates über den Nachrichtenfluss " *Benutzer bei neuer Krisen Mitteilung Benachrichtigen* " verwendet. |  
| APP-URL | AppURL | Der Speicherort der APP, sodass der *Nachrichtenfluss "Benutzer über neue Krisenkommunikation Benachrichtigen* " Benutzer nach Auswahl von " **Weitere**Informationen" umleiten kann. | 
| RSS-Feed für Government | Governmentrssfeed | Wird verwendet, um das World News-Feature in der APP aufzufüllen. Nützlich, wenn Sie Ihren Mitarbeitern zusätzliche Informationen aus einer vertrauenswürdigen Quelle bereitstellen möchten. |
| Benachrichtigungs Methode | Preferredsentnotification | Wird vom Nachrichtenfluss " *Benutzer bei neuer Krisen Mitteilung Benachrichtigen* " verwendet, um zu bestimmen, welcher Verteilungs Kanal beim Versenden von Benachrichtigungen verwendet werden soll. |
| Merkmals Flags | Feature1... 88 | Wird verwendet, um die einzelnen Funktionen innerhalb der Anwendung zu deaktivieren oder zu aktivieren. |

#### <a name="finding-the-aad-of-your-distribution-group"></a>Suchen der Aad-Gruppe ihrer Verteiler Gruppe
1. Navigieren Sie zu [Aad.Portal.Azure.com](https://aad.portal.azure.com)
1. Wählen Sie im linken Navigationsbereich **Azure Active Directory** aus.
1. Wählen Sie **Gruppen**aus.
1. Suchen Sie die Verteiler Gruppe, und wählen Sie Sie aus.
1. Kopieren Sie das Feld **Objekt-ID** .

    ![Die Aad-ID wird in Azure erhalten.](media/sample-crisis-communication-app/11-AAD-Group-ID.png)

1. Fügen Sie die ID in das **Aad-Gruppen-ID** -Feld innerhalb der Admin-Anwendung ein.

### <a name="setup-emergency-contacts"></a>Einrichten von Notfall Kontakten

1. Navigieren Sie zu **Unternehmens Kontakten** .
1. Wählen Sie **neuen Kontakt erstellen** aus.
1. Vervollständigen Sie das Formular mit den Kontaktinformationen.

*Listen Schema:*

| **Feldname** | **Logischer Name in SharePoint** | **Zweck** |
|-|-|-|
| Vollständiger Name | FullName | Der Name des Kontakts. |
| E-Mail | E-Mail | Die e-Mail, die für den Kontakt angezeigt wird. |
| Land | Land | Das Land für den Kontakt. Diese wird verwendet, um die Kontakte zu gruppieren, sodass Sie dieses Feld für andere Gruppierungen verwenden können, wenn Länder für Sie nicht sinnvoll sind. |
| Comments | Comments | Zeigt zusätzliche Informationen über den Kontakt an. Es ist hilfreich zu beschreiben, wann Sie sich an diesen Kontakt wenden müssen. |
| Als veraltet markiert | Als veraltet markiert | Ermöglicht es Ihnen, einen vorhandenen Notfallkontakt auszublenden. |

### <a name="setup-initial-company-news"></a>Anfängliche Unternehmensnachrichten einrichten

1. Navigieren Sie zu **Unternehmensnachrichten** .
1. Wählen Sie **neuen Beitrag erstellen** aus.
1. Füllen Sie das Formular aus.

*Listen Schema:*

| **Feldname** | **Logischer Name in SharePoint** | **Zweck** |
|-|-|-|
| Titel | Titel | Der Titel des Updates. |
| Details | Details | Das vollständige Update. Sie können HTML in diesem Feld verwenden. |
| Blurb | Blurb | Eine kurze Nachricht über das Update. Diese wird im Nachrichtenfluss " *Benutzer bei neuer Krisen Mitteilung Benachrichtigen* " und im Katalog mit Updates verwendet. |
| Als veraltet markiert | Als veraltet markiert | Ermöglicht das Ausblenden eines vorhandenen Beitrags. |

### <a name="setup-helpful-tips"></a>Hilfreiche Tipps für das Setup

1. Navigieren Sie zu **hilfreichen Tipps**.
1. Wählen Sie **neuer Tipp**aus.
1. Füllen Sie das Formular aus.

*Listen Schema:*

| **Feldname** | **Logischer Name in SharePoint** | **Zweck** |
|-|-|-|
| Titel | Titel | Der Titel des hilfreichen Tipps. |
| Ressourcen-URL | ResourceURL | Ein Link zu zusätzlichem Lesematerial. optionale |
| Untertitel | Titel | Ein Untertitel für den Tipp. optionale |
| Beschreibung | Beschreibung | Die vollständige Beschreibung des hilfreichen Tipps. |
| Als veraltet markiert | Als veraltet markiert | Ermöglicht es Ihnen, einen nützlichen Tipp auszublenden. |

### <a name="setup-links"></a>Setup Verknüpfungen

1. Navigieren Sie zu **Links**.
1. Wählen Sie **neuen Link erstellen**aus.
1. Füllen Sie das Formular aus.

*Listen Schema:*

| **Feldname** | **Logischer Name in SharePoint** | **Zweck** |
|-|-|-|
| Titel | Titel | Der Text des Links. |
| URL | URL | Die URL des Links. |
| Beschreibung | Beschreibung | Weitere Details zum Link. optionale |
| Als veraltet markiert | Als veraltet markiert | Ermöglicht das Ausblenden eines Links. |

### <a name="setup-faqs"></a>FAQs zum Setup

1. Navigieren Sie zu **FAQ**.
1. Wählen Sie **neue FAQ erstellen**aus.
1. Füllen Sie das Formular aus.

*Listen Schema:*

| **Feldname** | **Logischer Name in SharePoint** | **Zweck** |
|-|-|-|
| Titel | Titel | Die Frage der häufig gestellten Fragen. |
| Rang | Rang | Die Reihenfolge der häufig gestellten Fragen. |
| Te | Te | Die Antwort auf die häufig gestellten Fragen |
| Als veraltet markiert | Als veraltet markiert | Ermöglicht das Ausblenden von häufig gestellten Fragen. |

## <a name="test-and-share-the-app"></a>Testen und Freigeben der APP

Nachdem Sie nun alle Daten erfolgreich eingerichtet haben, können Sie die App nun testen, um sicherzustellen, dass Sie funktioniert:

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.
2. Wählen Sie im linken Navigationsbereich **apps** aus.
3. Wählen Sie die **Krisenkommunikation** aus, um die APP wiederzugeben

Nachdem Sie die APP erfolgreich getestet haben, können Sie die APP für alle Personen in Ihrem Unternehmen freigeben.

## <a name="import-and-set-up-the-notification-flow"></a>Importieren und Einrichten des Benachrichtigungs Flusses

Die APP verwendet einen Flow, um Benachrichtigungen an Endbenutzer zu senden, wenn ein neues Unternehmens Update vorliegt.

### <a name="import-the-news-notification-flow"></a>Importieren des Nachrichten Benachrichtigungs Flusses

1. Navigieren Sie zu [Flow.Microsoft.com](https://flow.microsoft.com)
1. Wählen Sie **meine Flows** im linken Navigationsbereich aus.
1. Klicken Sie in der Befehlsleiste auf die Schaltfläche **importieren** .
1. Laden Sie das Paket **crisiscommunicationnewsnotification. zip** aus dem GitHub-Repository hoch:

    > [!NOTE]
    > Wenn sich Ihr Mandant in der gcc-Umgebung befindet, verwenden Sie **crisiscommunicationnewsnotificationgcc. zip**.

    ![Crisiscommunicationnewsnotification. zip hochladen](media/sample-crisis-communication-app/upload-news-notification.png)

1. Fügen Sie Verbindungen für den neuen Flow hinzu, indem Sie für jede Verbindung den Link **Select during Import** auswählen und das Formular ausfüllen:

    ![Während des Imports auswählen](media/sample-crisis-communication-app/select-during-import.png)

1. Wenn Sie eine neue Verbindung erstellen müssen, wählen Sie im Bereich Import einrichten die Option **neu erstellen** aus.
1. Wählen Sie in der Befehlsleiste **neue Verbindung** aus:

    ![Erstellen einer neuen Verbindung](media/sample-crisis-communication-app/create-connection.png)

1. Suchen Sie nach dem Namen der Verbindung. Beispiel: **powerapps-Benachrichtigung (Vorschau)** :

    ![Benachrichtigungen](media/sample-crisis-communication-app/notifications.png)

1. Wählen Sie die entsprechende Verbindung aus.
1. Wenn Sie eine Verbindung mit **powerapps-Benachrichtigungen (Vorschau) erstellen,** wird das folgende Dialogfeld angezeigt:

    ![Dialogfeld für Benachrichtigungen](media/sample-crisis-communication-app/notifications-dialog.png)

1. Navigieren Sie zu Ihrer **App** -Liste, um die ID zu erhalten.
1. Wählen Sie die **weiteren Befehle** (...) für die APP für die **Krisenkommunikation** aus, und klicken Sie auf Details:

    ![Weitere Befehle](media/sample-crisis-communication-app/06-App-Details.png)

1. Kopieren Sie die **App-ID**:

    ![App-ID](media/sample-crisis-communication-app/07-App-ID.png)

1. Fügen Sie die **App-ID** in das Dialogfeld Verbindungs Erstellung ein, und wählen Sie **Erstellen**:

    ![APP-ID einfügen](media/sample-crisis-communication-app/target-app-id.png)

1. Nachdem Sie die neue Verbindung erstellt haben, wechseln Sie zurück zum Abschnitt **Import Setup** , und klicken Sie auf die Schaltfläche **Liste aktualisieren** .
1. Die neue Verbindung sollte nun angezeigt werden, und Sie können Sie auswählen und **Speichern**auswählen.
1. Wählen Sie **importieren** aus, sobald Sie alle Ihre Verbindungen hinzugefügt haben.

    ![Importieren von Verbindungen](media/sample-crisis-communication-app/imported-connections.png)

### <a name="edit-the-news-notification-flow"></a>Bearbeiten des Nachrichten Benachrichtigungs Flusses

1. Nachdem der Import Vorgang abgeschlossen ist, kehren Sie zu **meine Flows**zurück.
1. Wählen Sie den neu importierten Flow **Benachrichtigen von Benutzern über neue Krisen Kommunikations Nachrichten aus**.

    > [!NOTE]
    > Wenn Sie das gcc-Paket hochgeladen haben, benachrichtigt der flowname **Benutzer über den neuen Migrations-News gcc**.

1. Klicken Sie in der Befehlsleiste auf **Bearbeiten** .
1. Öffnen Sie die Karte, die aufgerufen **wird, wenn ein neues Element gepostet wird**.
1. Ändern Sie die **Standort Adresse** in den Namen Ihrer SharePoint-Website.
1. Ändern Sie den **Listennamen** in **CI_CompanyNews**.
1. Öffnen Sie die Karte **Get the admin config Settings**.
1. Ändern Sie die **Standort Adresse** in den Namen Ihrer SharePoint-Website.
1. Ändern Sie den **Listennamen** in **CI_configAdminSetup**.
1. Öffnen Sie die Karte namens **Initialize Variable – Read More Text**.
1. Ändern Sie den **Wert** in ihrer Muttersprache in "Weitere Informationen".

    ![Fluss Einstellungen](media/sample-crisis-communication-app/flow-options.png)

1. Wählen Sie **Speichern** , um die Änderungen zu übertragen.

> [!NOTE]
> Sie erhalten möglicherweise eine Fehlermeldung, wenn eine ihrer Verbindungen noch nicht autorisiert wurde.
Öffnen Sie in diesem Fall die Karte mit der nicht autorisierten Verbindung, und führen Sie eine erneute Autorisierung durch.

### <a name="test-the-news-notification-flow"></a>Testen des nachrichtenbenachrichtigungs Flusses

Wechseln Sie zur Administrator-app zurück, und erstellen Sie ein neues internes Unternehmens Update, um den Nachrichten Benachrichtigungs Fluss zu testen.
Später erhalten alle Benutzer in der Verteilerliste ein Update anhand ihrer bevorzugten Benachrichtigungs Einstellung.

> [!NOTE]
> Wenn Fehler auftreten, stellen Sie sicher, dass Sie die ID der Verteiler Gruppe in den Administrator Einstellungen innerhalb der admin-App erfolgreich eingegeben haben.

## <a name="monitor-office-absences-with-power-bi"></a>Überwachen von Office-Abwesenheits Punkten mit Power BI

Nachdem Sie die APP bereitgestellt haben und die Mitarbeiter mit der Benachrichtigung benachrichtigt werden, dass Sie aus verschiedenen Gründen aus dem Büro bestehen (z. b. krank oder von Hause aus), können Sie jetzt mithilfe eines Power BI Berichts nachverfolgen, wie viele und wo sich diese Personen befinden.

Zum starten können Sie den Beispiel Bericht "Anwesenheitsstatus Bericht. pbix" verwenden, der im heruntergeladenen [Assets-Paket](#prerequisites)verfügbar ist.
Laden Sie bei Bedarf [Power BI Desktop](https://powerbi.microsoft.com/downloads)herunter. Wir benötigen auch einige Informationen aus der bereits erstellten **CI_Employee Status** -SharePoint-Liste. Wir werden also zuerst darauf eingehen. Öffnen Sie die Liste in Ihrer Website, und wählen Sie unter dem Symbol "Einstellungen" die Option Listen Einstellungen

![Einstellungen der Mitarbeiter Status Liste](media/sample-crisis-communication-app/001-SharePointList-ListSettings-nolines.PNG)

Notieren Sie sich den **Website Namen** und die **Listen-ID** in der Adressleiste des Browsers:

![Mitarbeiter Status Liste und Website-ID](media/sample-crisis-communication-app/002-SharePointList-AddressAndId-nolines.PNG)

An diesem Punkt können wir den Power BI Bericht öffnen. Starten Sie Power BI, und öffnen Sie die **pbix-Datei des Anwesenheitsstatus Berichts** . Bewegen Sie den Mauszeiger über die Rechte Seite der **CI_Employee Status** -Datenquelle, bis Sie das Auslassungs Zeichen sehen, wählen Sie es aus, und wählen Sie die Option "Abfrage bearbeiten" aus:

![Abfrage bearbeiten](media/sample-crisis-communication-app/003-PowerBI-EditQuery-nolines.PNG)

Nachdem der Power Query-Editor geöffnet wurde, klicken Sie mit der rechten Maustaste auf die **CI_Employee Status** -Datenquelle, und wählen Sie die **Erweiterter Editor**aus:

![Power Query Erweiterter Editor](media/sample-crisis-communication-app/004-PowerQuery-AdvancedEditor-nolines.PNG)

Hier verwenden wir den Website Namen und die Listen-ID aus der SharePoint-Liste: Kopieren Sie die neue SharePoint-Website in der Tabelle und die Listen-ID an den drei Stellen, an denen eine GUID wie hervorgehoben ist, und wählen Sie dann **abgeschlossen**aus.

![Power Query Erweiterter Editor Updates](media/sample-crisis-communication-app/005-PowerQuery-AdvancedEditorUpdates-nolines.PNG)

Wenn nach dem Aktualisieren der Verbindungsinformationen Verbindungsfehler angezeigt werden, müssen Sie möglicherweise die Anmelde Informationen aktualisieren, die zum Herstellen einer Verbindung mit der SharePoint-Liste verwendet werden. Führen Sie diese Schritte aus, um die Verbindung zu aktualisieren:

1. Wählen Sie im Menü **Datei** die **Optionen und Einstellungen** aus, und wählen Sie dann **Datenquellen Einstellungen**aus:

    ![Datenquelleneinstellungen](media/sample-crisis-communication-app/PBI-1-DataSourceSettings.PNG)

1. Wählen Sie **Berechtigungen bearbeiten**:

    ![Berechtigungen bearbeiten](media/sample-crisis-communication-app/PBI-2-DataSourceSettings-EditPermissions.PNG)

1. Stellen Sie sicher, dass der Typ *Anmelde* Informationen auf *Organisations Konto*festgelegt ist, und verwenden Sie die Anmelde Informationen für den Zugriff auf die SharePoint

    ![Berechtigungen bearbeiten](media/sample-crisis-communication-app/PBI-3-OrganizationalAccount.PNG)

Wählen Sie **& schließen** aus, um den Bericht zu aktualisieren, um Daten aus Ihrer SharePoint-Liste abzurufen.

![Power Query schließen und anwenden](media/sample-crisis-communication-app/006-PowerQuery-CloseAndApply-nolines.PNG)

Wir verfügen jetzt über einen Power BI Bericht, der sowohl die geografischen Informationen für Office-Abwesenheits Informationen für den aktuellen Tag als auch einen Trend der derartigen Abwesenheit über mehrere Tage anzeigt. Wir können den Bericht jetzt veröffentlichen, damit andere Personen in der Organisation ihn sehen können.

![Power BI veröffentlichungsbericht](media/sample-crisis-communication-app/007-PowerBI-Publish-nolines.PNG)

Der Bericht wird jetzt veröffentlicht. Sie können Sie für andere Personen in Ihrer Organisation freigeben. Sie können auch [die Berichts Aktualisierungshäufigkeit planen](https://docs.microsoft.com/power-bi/refresh-scheduled-refresh).

## <a name="integrate-your-app-into-teams"></a>Integrieren ihrer app in Teams

Nachdem Sie nun über eine funktionierende App verfügen, die für alle Benutzer freigegeben wurde, können Sie die App mithilfe von Teams bereitstellen und ein Krisenmanagementteam in Microsoft Teams erstellen, um auf Probleme zu reagieren.

### <a name="deploy-the-app-to-the-app-bar"></a>Bereitstellen der APP auf der APP-Leiste

Wenn Sie ein Team Administrator sind, können Sie die APP per Push an alle Benutzer in der APP-Leiste des Teams übersetzen.

![App in Teams](media/sample-crisis-communication-app/19-App-in-Teams.png)

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.
1. Wählen Sie im linken Navigationsbereich **apps** aus.
1. Wählen Sie das Menü " **...** " für die app " **Krisenkommunikation** " aus.
1. Wählen Sie **zu Teams hinzufügen**aus.

    ![Zu Teams hinzufügen](media/sample-crisis-communication-app/24-Add-to-Teams.png)

1. Wählen Sie **app herunterladen**aus.

    ![App herunterladen](media/sample-crisis-communication-app/25-Download-App.png)

1. **Teams** öffnen
1. Navigieren Sie in der linken App-Leiste zu **apps** .
1. Wählen Sie **benutzerdefinierte App hochladen**aus.
1. Wenn Sie ein Team Administrator sind, wird Ihnen die Möglichkeit angezeigt, eine APP für Ihren gesamten Mandanten hochzuladen. Wählen Sie **Hochladen für**"Configuration Manager" aus.

    ![Hochladen](media/sample-crisis-communication-app/26-Upload-for-Contoso.png)

1. Laden Sie die Datei hoch, die Sie aus Power apps heruntergeladen haben.
1. Navigieren Sie zum [Teams Admin Center](https://admin.teams.microsoft.com/dashboard) .
1. Wählen Sie im linken Navigationsbereich unter **Teams-apps** die Option **Setup Richtlinien** aus.

    ![App-Setup Richtlinien](media/sample-crisis-communication-app/27-Setup-Policies.png)

1. Wählen Sie **Global (Organisations weites Setup)** aus.
1. Wählen Sie **apps hinzufügen**aus.

    ![App hinzufügen](media/sample-crisis-communication-app/28-Add-App.png)

1. Suchen Sie nach der hochgeladenen **Kriseninformationen** -APP, und wählen Sie Sie aus

    ![Angeheftete app hinzufügen](media/sample-crisis-communication-app/29-Add-Pinned-App.png)

1. Wählen Sie **Hinzufügen**.
1. Wählen Sie **Speichern** aus.

> [!NOTE]
> Es kann bis zu 24 Stunden dauern, bis Benutzer die APP automatisch in Ihrer APP-Leiste angeheftet sehen.

### <a name="create-a-central-crisis-management-teams-team"></a>Erstellen eines Teams für zentrale Krisenmanagement Teams

Um Ihre Reaktion auf Ihre Reaktion zu koordinieren, sollten Sie ein zentrales Teams-Team für Ihr Krisenmanagementteam erstellen und mit allen relevanten Informationen füllen.

1. Navigieren Sie zu Teams.
1. Wählen Sie in der linken App-Leiste **Teams** aus.
1. Wählen Sie beitreten aus, **oder erstellen Sie ein Team**.
1. Wählen Sie **Team erstellen** aus, und führen Sie die restlichen Schritte aus.

    ![Team erstellen](media/sample-crisis-communication-app/23-Create-Team.png)

Nachdem Sie das Team erfolgreich erstellt haben, können Sie relevante Informationen als Registerkarten anheften. Beispielsweise können Sie die "Crisis Management"-Administrator-APP oder den Power BI Bericht an Ihr Team anheften. So fügen Sie die Administrator-App als Registerkarte hinzu:

1. Wählen Sie die Schaltfläche **+** aus.
1. Suchen Sie nach **Power apps**, und wählen Sie Sie aus.
1. Suchen Sie nach, und wählen Sie " **Information admin**" aus

    ![Anheften der App](media/sample-crisis-communication-app/32-Pin-Teams-app.png)

1. Wählen Sie **Speichern** aus.

So fügen Sie den Power BI Bericht hinzu:

1. Wählen Sie die Schaltfläche **+** aus.
1. Suchen Sie nach **Power BI**und wählen Sie ihn aus.
1. Suchen Sie den Power BI Bericht, und wählen Sie ihn aus.
1. Wählen Sie **Speichern** aus.

***Haftungsausschluss:*** *diese APP ist ein Beispiel und kann mit Microsoft powerapps und Teams für die Verbreitung von Referenzinformationen verwendet werden. Diese APP ist nicht für das medizinische Gerät, den klinischen Support, das Diagnosetool oder andere Technologien vorgesehen, die bei der Diagnose, beim Schutz, bei der Entschärfung, bei der Behandlung oder bei der Verhinderung von Krankheiten oder anderen Bedingungen verwendet werden sollen, und von Microsoft wird keine Lizenz oder das Recht erteilt, diese APP zu diesem Zweck zu verwenden.  Diese APP ist nicht als Ersatz für professionelle medizinische Beratung, Diagnose, Behandlung oder Beurteilung gedacht und sollte nicht als solche verwendet werden.  Der Kunde hat das alleinige Risiko und die Verantwortung für die Verwendung dieser app.  Microsoft garantiert nicht, dass die APP oder die darin enthaltenen Materialien zu medizinischen Zwecken ausreichen oder die Integritäts-oder medizinischen Anforderungen beliebiger Personen erfüllen.*  

## <a name="next-steps"></a>Nächste Schritte

- [Referenz zu Formeln](https://docs.microsoft.com/powerapps/maker/canvas-apps/formula-reference)
- [Referenz zu Steuerelementen](https://docs.microsoft.com/powerapps/maker/canvas-apps/reference-properties)
