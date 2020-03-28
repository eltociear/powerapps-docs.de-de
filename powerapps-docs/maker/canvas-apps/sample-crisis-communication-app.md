---
title: App-Beispiel Vorlage für die Krisenkommunikation | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Beispiel Vorlage für die Krisenkommunikation in powerapps.
author: matthewbolanos
manager: kvivek
ms.service: powerapps
ms.topic: sample
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/25/2020
ms.author: mabolan
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 465f18474c7054467db8e22bb1702db250177395
ms.sourcegitcommit: be9b8c0f5c7c7e9992e93fa0d03e961b4ac7e3ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2020
ms.locfileid: "80375062"
---
# <a name="set-up-and-learn-about-the-crisis-communication-sample-template-in-power-apps"></a>Einrichten und Erlernen der Beispiel Vorlage für die Krisenkommunikation in Power apps

Die APP zur Krisenkommunikation bietet eine benutzerfreundliche benutzerfreundliche Benutzerfreundlichkeit, um Benutzer mit Informationen zu einer Krise zu verbinden. Holen Sie sich schnell Aktualisierungen zu internen Unternehmensnachrichten, erhalten Sie Antworten auf häufig gestellte Fragen, und erhalten Sie Zugriff auf wichtige Informationen wie Links und Notfallkontakte. Diese App erfordert ein geringes Maß an Einrichtung, um sie an Ihre Anforderungen anzupassen.

In dieser exemplarischen Vorgehensweise lernen Sie Folgendes:

- Erstellen Sie einen Speicherort für Ihre Daten.
- Importieren Sie sowohl die APP zur Krisenkommunikation als auch Ihre Administrator-app.
- Erstellen Sie Inhalte für die app.
- Importieren Sie Flows, um Benachrichtigungen an Benutzer zu senden.
- Erstellen Sie ein zentral verwaltetes Teams-Team, um Daten zu aggregieren und effektiv auf Probleme zu reagieren.

Geschätzte Zeit zum Ausführen dieser Schritte: **20&ndash;25 Minuten**.

> [!NOTE]
> Die Beispiel Vorlage für die Krisenkommunikation ist auch für die US Government-Pläne "US Government" und "Power automatisiert US Government" verfügbar. Die Dienst-URLs für Power apps und Power automatisiert US Government-Versionen unterscheiden sich von den kommerziellen Versionen. Weitere Informationen finden Sie unter [powerapps US Government-Dienst-URLs](https://docs.microsoft.com/power-platform/admin/powerapps-us-government#power-apps-us-government-service-urls) und [Power automatisiert US Government-Dienst-URLs](https://docs.microsoft.com/power-automate/us-govt#power-automate-us-government-service-urls) .

## <a name="demo-crisis-communication-app"></a>Demo: App zur Krisenkommunikation

Sehen Sie sich an, wie die Lösung zur Krisenkommunikation verwendet wird.

> [!VIDEO https://www.youtube.com/embed/23SypLXiOTw]

## <a name="prerequisites"></a>Erforderliche Komponenten

- [Registrieren Sie sich](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) für powerapps.
- Sie müssen über eine gültige SharePoint Online-Lizenz verfügen und über die Berechtigung zum Erstellen von Listen verfügen.
- Sie müssen über eine öffentliche SharePoint-Website verfügen, auf der Sie die Daten für die APP speichern können.
- Laden Sie die Assets aus [aka.ms/CrisisCommunicationSolution](https://aka.ms/CrisisCommunicationSolution)herunter.

> [!IMPORTANT]
> Wenn Sie Feedback oder Probleme im Zusammenhang mit der App zur Krisenkommunikation haben, verwenden Sie die folgenden Links:
> - **[Backs](https://aka.ms/crisis-communication-feedback)**
> - **[Probleme](https://aka.ms/crisis-communication-issues)**

## <a name="demo-build-and-deploy-the-crisis-communication-app"></a>Demo: Erstellen und Bereitstellen der App zur Krisenkommunikation

Erfahren Sie, wie Sie die APP zur Krisenkommunikation erstellen und bereitstellen.

> [!VIDEO https://www.youtube.com/embed/Wykrwf9dZ-Y]

## <a name="create-a-home-for-your-data"></a>Erstellen eines Zuhause für Ihre Daten

Die Daten für die APP werden in SharePoint-Listen gespeichert. der erste Schritt besteht also darin, eine neue SharePoint-Website zu erstellen.

### <a name="create-a-sharepoint-site"></a>Erstellen einer SharePoint-Website

1. Melden Sie sich bei [Office Online](https://www.office.com)an, und wählen Sie dann **SharePoint**aus.
1. Wählen Sie **Website erstellen**aus.

    ![Beispiel einer SharePoint-Website](media/sample-crisis-communication-app/01-Create-Site.png)

1. Wählen Sie **Team Site**aus.

    ![Team Website](media/sample-crisis-communication-app/02-Team-Site.png)

1. Geben Sie einen Namen und eine Beschreibung für die Website ein.
1. Legen Sie die **Datenschutzeinstellungen** auf " **Public** " fest, damit alle Benutzer im Unternehmen die erforderlichen Informationen erhalten können.

    ![Websiteeinstellungen](media/sample-crisis-communication-app/03-Privacy-Settings.png)

1. Klicken Sie auf **Weiter**.
1. Fügen Sie zusätzliche Besitzer für die Website hinzu (optional).
1. Wählen Sie **Fertig stellen** aus.

### <a name="create-sharepoint-lists-for-the-app"></a>Erstellen von SharePoint-Listen für die APP

Die APP verwendet mehrere Listen, um die Daten zu speichern. Sie können den deploysplists-Flow verwenden, der im heruntergeladenen [Assets-Paket](#prerequisites)verfügbar ist, um diese Listen automatisch zu erstellen.

#### <a name="import-the-sharepoint-list-deployment-flow"></a>Importieren des SharePoint-Listen Bereitstellungs Flusses

1. Wechseln Sie zu [Flow.Microsoft.com](https://flow.microsoft.com).
1. Wählen Sie im linken Navigationsbereich **meine Flows** aus.
1. Klicken Sie in der Befehlsleiste auf **importieren** .
1. " **Deploysplists. zip** " hochladen<!--edit to the file name okay, here and in the following instances?--> Paket aus dem GitHub-Repository.

    ![Paket importieren](media/sample-crisis-communication-app/import-package.png)

1. Fügen Sie eine SharePoint-Verbindung für den neuen Flow hinzu, indem Sie den Link **Select during Import** auswählen und das Formular ausfüllen.

    ![Importeinstellungen](media/sample-crisis-communication-app/import-settings.png)

1. Wenn Sie eine neue SharePoint-Verbindung erstellen möchten, wählen Sie im Bereich **Import einrichten** die Option **neu erstellen** aus.
1. Wählen Sie in der Befehlsleiste **neue Verbindung** aus.

    ![Erstellen einer neuen Verbindung](media/sample-crisis-communication-app/create-connection.png)

1. Suchen Sie nach dem Namen der Verbindung, z. b. *SharePoint*.
1. Wählen Sie die von Ihnen erstellte Verbindung aus.<!--edit okay?-->
1. Wählen Sie **Speichern** aus.
1. Wählen Sie **Importieren** aus.

#### <a name="edit-the-sharepoint-list-deployment-flow"></a>Bearbeiten des Bereitstellungs Flusses für die SharePoint-Liste

1. Nachdem der Import Vorgang abgeschlossen ist, wechseln Sie zu **meine Flows** , und aktualisieren Sie die Liste der Flows.
1. Wählen Sie den neu importierten Flow, **deploysplists**.
1. Wählen Sie in der Befehlsleiste die Option **Bearbeiten** aus.
1. Öffnen Sie die Karte **Variable – Zielwebsite für Listen** .
1. Geben Sie als **Wert**den Namen Ihrer SharePoint-Website ein.
1. Öffnen Sie die **Variable – App Name** Card.
1. Geben Sie als **Wert**den Namen Ihrer APP ein. Standardmäßig ist der Name die **Krisenkommunikation**.

    ![Fluss Parameter](media/sample-crisis-communication-app/04-Flow-Settings.png)

1. Wählen Sie **Speichern** aus.

#### <a name="run-the-sharepoint-list-deployment-flow"></a>Ausführen des Bereitstellungs Flows für die SharePoint-Liste

1. Wechseln Sie zurück zum Detailbildschirm für den **deploysplists** -Flow.
1. Wählen Sie auf der Befehlsleiste die Option **Ausführen** aus.
1. Wählen Sie **weiter**aus, und wählen Sie dann **Flow ausführen**aus.

    ![Melden Sie sich an, um den Flow auszuführen.](media/sample-crisis-communication-app/sign-in-flow.png)

    ![Ausführen des Flows](media/sample-crisis-communication-app/run-flow.png)

> [!NOTE]
> Möglicherweise wird eine Fehlermeldung mit dem Hinweis angezeigt, dass Standortdienste erforderlich sind.
Wenn dies der Fall ist, gestatten Sie Standort Diensten den Zugriff.<!--edit okay? I wasn't sure what this meant.--> Schalten Sie die Seite vor dem erneuten Versuch ein, und aktualisieren Sie Sie

Der Flow erstellt die folgenden SharePoint-Listen auf der SharePoint-Website.<!--general note; You don't need to introduce tables or graphics with colons, only lists.-->

| **Anzeige Titel**| **Zweck** | **Beschreibung** |
|-|-|-|
| CI_LogosAssets| , Um das Logo und/oder andere Bilder aufzunehmen, auf die von der APP verwiesen werden soll. Auf das Logo wird in powerapps über einen direkten Link oder über die ID-Nummer des Logos verwiesen, das Sie verwenden möchten. | Die Bibliothek für Verwandte Logos und andere Image Ressourcen für die app " *[App-Name]* ". |
| CI_configAdminSetup | Wird für die featurekonfiguration durch den Administrator der APP verwendet.<br>**Hinweis**: Diese Liste sollte für alle Mitglieder, die keine Administratoren sind, schreibgeschützt sein. | Die Administrator Konfigurationsliste für die app " *[App-Name]* ".
| CI_Contacts | Verwenden des Inhaltstyps Standard Kontakte zum Erfassen von Informationen über Kontakte. (Keine Personen Auswahl ist enthalten, daher muss diese Liste möglicherweise manuell verwaltet werden.<!--edit okay?--> um sicherzustellen, dass die Daten auf dem neuesten Stand sind.)<br>**Hinweis**: Dies hängt davon ab, dass der globale Kontakt Auflistungstyp ein Standard Inhaltstyp in der Liste ist. | Die Kontaktliste für die app " *[App-Name]* ".|
| CI_CompanyNews | Sammlung von **Unternehmens-News** Items. | Eine Liste zum Verwalten der News Items, die in der App " *[App-Name]* " angezeigt werden. Sie können die **Veraltete** Spalte verwenden, um News Items aus den App-Ansichten zu entfernen.<!--edit okay, here and below? You use this pattern ("remove ___ from the app views") in the "Helpful tips" description, and it seems a bit more descriptive than "filter ___ out of the app".-->, während Sie als Datensatz beibehalten werden. | 
| CI_FAQ  | Frequently asked questions. | Die Liste der häufig gestellten Fragen zu der App " *[App-Name]* ". Sie können die **Veraltete** Spalte verwenden, um FAQ-Elemente aus den App-Ansichten zu entfernen, während Sie als Datensatz beibehalten werden. |
| CI_UsefulLinks<!--edit okay? The sharepoint-lists.png screenshot later in this article shows it as "Usefulinks," which probably isn't correct either.--> | Nützliche Hyperlinks-Liste. | Die Liste der nützlichen Hyperlinks für die app " *[App-Name]* ". Sie können die **Veraltete** Spalte verwenden, um Hyperlink-Elemente aus den App-Ansichten zu entfernen, während Sie als Datensatz beibehalten werden. |
| CI_Employee | Der aktuelle Anwesenheitsstatus der Mitarbeiter wird nachverfolgt. Beispiele: **Arbeiten von Zuhause**, **krank**, **bei persönlichen verlassen**und **im Urlaub**.  **Hinweis**: der Status " **Arbeit** " wird angenommen und ist nicht in den Listen Optionen enthalten. | <!--Please check the following edit carefully. This cell was duplicated by mistake from the previous row. Does the note about the "Deprecated" column apply here?-->Die Liste der Nachrichten, die den Status der Anwesenheit eines Mitarbeiters für die app " *[App-Name]* " angeben. Sie können die **Veraltete** Spalte verwenden, um Statusmeldungen aus den App-Ansichten zu entfernen, während Sie als Datensatz beibehalten werden. |
| CI_HelpfulTips             | Hilfreiche Tipps, die Benutzer für Ihre Peers beigetragen haben. | Liste für die Verwaltung von freigegebenen Tipps für die app " *[App-Name]* ". Sie können die **Veraltete** Spalte verwenden, um Tipps aus den App-Ansichten zu entfernen, während Sie als Datensatz beibehalten werden.  |

> [!NOTE]
> - Alle diese Listen Spalten sollten als Abhängigkeiten angesehen werden.
    Schützt die Listen vor versehentlichen Schema Änderungen (z. b. das Hinzufügen neuer Spalten ist zulässig, das Löschen von Spalten kann jedoch die APP unterbrechen).
> - Beim Löschen von Listenelementen Vorsicht walten lassen; durch das Löschen von Listenelementen werden historische Datensätze gelöscht. Sie können den Wert für depreationvalue aktivieren. <!--Style Guide-->von **Nein** zu **Ja** , um Datensätze aus Kontakten, Nachrichten, FAQs oder Links zu löschen.<!--Should this include status messages too?-->

## <a name="import-and-set-up-the-crisis-communication-app"></a>Importieren und Einrichten der App zur Krisenkommunikation

Nachdem Sie alle SharePoint-Listen erstellt haben, können Sie die App importieren und mit ihren neuen Datenquellen verbinden.

> [!NOTE]
> Wenn Sie die admin-APP nicht verwenden möchten, können Sie diese Eigenschaften bearbeiten, indem Sie die SharePoint-Listen manuell bearbeiten.

### <a name="import-the-app"></a>Importieren der App

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.
1. Klicken Sie im linken Navigationsbereich auf **apps** .
1. Klicken Sie in der Befehlsleiste auf **importieren** .
1. Laden Sie die Datei **crisiscommunication. zip** aus dem GitHub-Repository hoch.

    > [!NOTE]
    > Wenn sich Ihr Mandant in einer gcc-Umgebung befindet, laden Sie **crisiscommunicationgcc. zip**hoch.

    ![Importieren des App-Pakets](media/sample-crisis-communication-app/31-Import-App.png)

1. Vervollständigen Sie die Verbindung Setup für **Microsoft Teams-Verbindung** und **Office 365-Benutzer** importieren, indem Sie die entsprechenden Verbindungen über den Hyperlink während des **Imports auswählen** auswählen. Sie müssen möglicherweise eine [neue Verbindung](add-data-connection.md)erstellen, wenn Sie nicht bereits vorhanden ist.
1. Wählen Sie **Importieren** aus.

### <a name="update-the-sharepoint-connections"></a>Aktualisieren der SharePoint-Verbindungen

1. Wechseln Sie zurück zur Liste der **apps** .
1. Wählen Sie **Weitere Befehle** (...) für die APP zur **Krisenkommunikation** aus.
1. Wählen Sie im Kontextmenü die Option **Bearbeiten** aus.

    ![Bearbeiten der APP](media/sample-crisis-communication-app/05-Edit-App.png)

1. Melden Sie sich an, oder erstellen Sie erforderliche Verbindungen, und klicken Sie dann auf **zulassen**.

1. Wechseln Sie zu den Datenquellen im linken Bereich.

    ![Datenquellen](media/sample-crisis-communication-app/data-sources.png)

1. Entfernen vorhandener SharePoint-Listen in der APP<!--Alternatively, this could be "Right-click the name of each existing SharePoint list, and then select **Remove**" if that's how the context menu works here. I think the graphic will be clear enough for the reader, though.-->, da Sie nicht auf Ihre aktuelle SharePoint-Website verweisen.

    ![Entfernen von Datenquellen](media/sample-crisis-communication-app/remove-data-source.png)

1. Fügen Sie die Listen von ihrer eigenen SharePoint-Website hinzu. Starten Sie, indem Sie in der Suchleiste nach **SharePoint** suchen.

    ![Nach SharePoint suchen](media/sample-crisis-communication-app/sharepoint.png)

1. Wählen Sie **SharePoint**aus, und wählen Sie dann eine Verbindung aus.

    ![SharePoint-Verbindung](media/sample-crisis-communication-app/sharepoint-connection.png)

1. Kopieren Sie die URL, und fügen Sie Sie in das Textfeld auf Ihrer SharePoint-Website ein, und wählen Sie dann **verbinden**aus.

    ![URL der SharePoint-Website](media/sample-crisis-communication-app/site-url.png)

1. Wählen Sie alle SharePoint-Listen und-Bibliotheken aus, und klicken Sie dann auf **verbinden**.

    ![Herstellen einer Verbindung mit SharePoint-Listen](media/sample-crisis-communication-app/sharepoint-lists.png)

1. Wählen Sie **Speichern**aus, und wählen Sie dann **veröffentlichen**aus.

### <a name="optional-enable-location-updates"></a>Optional: Speicherort Aktualisierungen aktivieren

Mit dieser APP können Sie den Speicherort eines Benutzers aufzeichnen und auf der SharePoint-Website speichern, wenn ein Benutzer seinen Status festlegt. Ihr Krisenmanagementteam kann diese Daten in einem Power BI Bericht anzeigen.

> [!NOTE]
> Das Aktivieren von Standort Aktualisierungen ist optional. Sie können diesen Abschnitt überspringen, wenn Sie den Benutzer Standort nicht nachverfolgen möchten.

**So aktivieren Sie Standort Aktualisierungen**

1. Suchen Sie nach dem **btndaterange** -Steuerelement.
1. Öffnen **Sie die onselect** -Eigenschaft des **btndaterange** -Steuer Elements in der Bearbeitungs Leiste.
1. Kopieren Sie den folgenden Code Ausschnitt, und fügen Sie ihn in die Bearbeitungs Leiste für die **onselect** -Eigenschaft ein.

    > [!NOTE]
    > Der folgende Code Ausschnitt soll mit Versionen der Projekt Mappe arbeiten, die älter sind als 2020.03.16.


    ```
        UpdateContext({locSaveDates: true});
    // Store the output properties of the calendar in static variables and collections.
    ClearCollect(submittedDates,Sort(Filter(selectedDates,ComponentId=CalendarComponent.Id),Date,Ascending));
    Set(varStartDate,First(submittedDates).Date);
    Set(varEndDate,First(Sort(submittedDates,Date,Descending)).Date);
    // Create a new record for work status for each date selected in the date range.
    ForAll(
        Filter(
            RenameColumns(submittedDates,"Date","DisplayDate"),
            ComponentId=CalendarComponent.Id,
            !(DisplayDate in colDates.Date)
        ),
        Patch('CI_Employee Status',Defaults('CI_Employee Status'),
            {
                Title: varUser.userPrincipalName,
                Date: DisplayDate,
                Notes: "",
                PresenceStatus: LookUp(colWorkStatus,Value=WorkStatusComponent.Selected.Value)
                
                // To implement location, add a comma to the line above and uncomment the lines below for latitude and longitude.
                // Latitude: Text(Location.Latitude),
                // Longitude: Text(Location.Longitude)
            }
        )
    );
        // Update existing dates with the new status.
        ForAll(
            AddColumns(
                Filter(
                    RenameColumns(submittedDates,"Date","DisplayDate"),
                    ComponentId=CalendarComponent.Id,
                    DisplayDate in colDates.Date
                ),
                
                // Get the current record for each existing date.
                "LookUpId",LookUp(RenameColumns(colDates,"ID","DateId"),And(Title=varUser.userPrincipalName,Date=DisplayDate)).DateId
            ),
            Patch('CI_Employee Status',LookUp('CI_Employee Status',ID=LookUpId),
                {
                    PresenceStatus: LookUp(colWorkStatus,Value=WorkStatusComponent.Selected.Value)
                }
            )
        );
        If(
            IsEmpty(Errors('CI_Employee Status')),
            
            // Update the list of work status for the logged-in user.
            ClearCollect(colDates,Filter('CI_Employee Status',Title=varUser.userPrincipalName));
            // Send an email receipt to the logged-in user.
            UpdateContext(
                {
                    locReceiptSuccess: 
                    Office365Outlook.SendEmailV2(
                        // To: send an email to oneself
                        varUser.mail,
                        // Subject
                        Proper(WorkStatusComponent.Selected.Value) & ": " & varStartDate & If(varStartDate<>varEndDate," - " & varEndDate),
                        // Body
                        WorkStatusComponent.Selected.DateRangeReceipt & ": " &
                        // Create a bulleted list of dates
                        "<ul>" & 
                            Concat(submittedDates,"<li>" & Date & Char(10)) &
                        "</ul>"
                    )
                }
            );
            If(
                locReceiptSuccess,
                Notify("You successfully submitted your work status. An email has been sent to you with a summary.",NotificationType.Success,3000),
                Notify("There was an error sending an email summary, but you successfully submitted your work status.",NotificationType.Success,3000);
            );
            
            Navigate('Share to Team Screen',LookUp(colStyles,Key="navigation_transition").Value),
            
            // Case: Error submitting work status
            Notify(varString.WorkStatusError,NotificationType.Warning)
        );
        UpdateContext({locSaveDates: false})
    ```

### <a name="optional-add-additional-work-status-messages"></a>Optional: Hinzufügen zusätzlicher Arbeitsstatus Meldungen

Wenn Sie mehr Arbeitsstatus hinzufügen möchten<!--Interesting fact: there is no plural of "status."--> Nachrichten, die nicht zu **Hause** und **außerhalb des Büros führen**, können Sie mit den folgenden Schritten ausführen. Um zu beginnen, müssen Sie die SharePoint-Website aktualisieren.

1. Wechseln Sie zurück zu Ihrer SharePoint-Website, und wählen Sie dann **Website Inhalte**aus.
1. Wählen Sie **CI_Employee Status**aus.
1. Wenn die Spalte **PresenceStatus** nicht vorhanden ist, klicken Sie auf **Spalte hinzufügen**.
1. Wählen Sie **Spalten anzeigen/ausblenden**aus.

    ![Spalten anzeigen/ausblenden](media/sample-crisis-communication-app/36-hide-show-columns.png)

1. Auswahl<!--edit okay? I didn't know what "Check" meant here.--> " **PresenceStatus**".
1. Wählen Sie **Übernehmen** aus.
1. Wählen Sie die Spalte **PresenceStatus** aus.

    ![Auswählen der Spalte "PresenceStatus"](media/sample-crisis-communication-app/37-show-presence.png)

1. Wählen Sie **Spalten Einstellungen**aus, und klicken Sie dann auf **Bearbeiten**.

    ![Bearbeiten der Spalte "PresenceStatus"](media/sample-crisis-communication-app/38-edit-column.png)

1. Fügen Sie im Feld **Auswahl** die zusätzlichen Arbeitsstatus Meldungen hinzu.

> [!NOTE]
> Notieren Sie sich den Namen Ihrer neuen Optionen. Sie werden Sie in nachfolgenden Schritten verwenden.

Nun müssen Sie einige Anpassungen an der APP vornehmen, um Ihre neuen Arbeitsstatus Meldungen anzuzeigen.

1. Öffnen Sie die app in powerapps Studio.<!--edit okay?-->.
1. Wählen Sie den Bildschirm **Arbeits Status** aus.
1. Legen Sie die Bearbeitungs Leiste auf die **onvisible** -Funktion fest.

    ![Anwesenheit anzeigen](media/sample-crisis-communication-app/39-onvisible-for-screen.png)

1. Bearbeiten Sie die folgende Vorlage, und ersetzen Sie die Werte durch ihre eigenen Werte.
<!--I took the liberty of editing these strings to use contractions, which is Microsoft style now.-->
    ```
        ,"<Name of option in SharePoint list; case sensitive>",
        Table(
            {
                Icon: <Image file>,
                DateRangeQuestion: "Select the dates you'll be <Name of status>.",
                DateRangeReceipt: "You're currently <Name of status>.",
                ShareToTeamEmail: "I'll be <Name of status> on these dates",
                AutoReplyMessage: "I'll be <Name of status> on these dates"
            }
        )
    ```

1. Ersetzen Sie die `/* TEMPLATE FOR ADDITIONAL WORK STATUS OPTIONS */` Zeichenfolge durch die Vorlage.
1. Wählen Sie **Speichern**aus, und wählen Sie dann **veröffentlichen**aus.

### <a name="update-the-request-for-help-flow"></a>Aktualisieren der Anforderung für den Hilfe Fluss

Dieser Flow sendet eine Adaptive Karte an ein zentrales Teams-Team und fordert Hilfe an.

![Hilfe anfordern](media/sample-crisis-communication-app/21-Request-Help.png)

Bevor Sie den folgenden Schritt ausführen, erstellen Sie ein Krisenmanagementteam in Teams. Nachdem Sie das Team erstellt haben, können Sie die ID für das Team erhalten und in den Flow einbringen. Weitere Informationen zum Erstellen eines Teams-Teams: Erstellen eines Teams für das [zentrale Krisenmanagementteam](#create-a-central-crisis-management-teams-team)

1. Wechseln Sie zum kanalchannel, an den Sie alle Ihre Hilfeanfragen senden möchten.
1. Wählen Sie **Weitere Optionen** (...) für den Kanal aus.
1. Wählen Sie **Link zum Kanal erhalten**aus.

    ![Einen Link zum Kanal erhalten](media/sample-crisis-communication-app/17-Get-link-to-channel.png)

1. Kopieren Sie den Link, und fügen Sie ihn in einen Texteditor ein.

    ![Team Link kopieren](media/sample-crisis-communication-app/18-Copy-link.png)

1. Extrahieren Sie die **Team-ID**. Dies ist alles nach `groupId=` und vor `&tenantId=`. <br> In der folgenden URL lautet die Kanal-ID z. b.<!--suggest using a line break here and in the next step so you don't have to include any closing punctuation.--> <br>`8bc7c0c2-0d4c-4fb8-af99-32da74c9237b`
   
   `https://teams.microsoft.com/l/channel/19%3ab2fa9fc20f3042a9b63fc5890e1813f8%40thread.tacv2/General?groupId=8bc7c0c2-0d4c-4fb8-af99-32da74c9237b&tenantId=72f988bf-86f1-41af-91ab-2d7cd011db47`
   
1. Extrahieren Sie die **Kanal-ID**, die alles nach `https://teams.microsoft.com/l/channel/` und vor `/General`ist. <br> In der folgenden URL lautet die Kanal-ID z. b.<br> `19%3ab2fa9fc20f3042a9b63fc5890e1813f8%40thread.tacv2`
   
   `https://teams.microsoft.com/l/channel/19%3ab2fa9fc20f3042a9b63fc5890e1813f8%40thread.tacv2/General?groupId=8bc7c0c2-0d4c-4fb8-af99-32da74c9237b&tenantId=72f988bf-86f1-41af-91ab-2d7cd011db47`,

1. Wechseln Sie zu [Flow.Microsoft.com](https://flow.microsoft.com).

1. Wählen Sie im linken Navigationsbereich **meine Flows** aus.

1. **Weitere Befehle** auswählen (...)  für **crisiscommunication. Request**, und wählen Sie dann **Bearbeiten**aus.

    ![Bearbeiten der Anforderung für den Hilfe Fluss](media/sample-crisis-communication-app/20-Edit-Flow.png)

1. Öffnen Sie die **TeamID** -Karte.

1. Fügen Sie die Team-ID in das **Wertfeld** ein.

1. Öffnen Sie die Karte **Channel ID** .

1. Fügen Sie die Kanal-ID in das **Wertfeld** ein.

    ![Team-und Kanal-IDs festlegen](media/sample-crisis-communication-app/22-Set-Team-IDs.png)

1. Scrollen Sie nach unten zu den Aktionen **Get Time** , und aktualisieren Sie die Aktion für **Zeit Zone konvertieren** , indem Sie die gewünschte Quell-und Ziel Zeit verwenden.

    ![Zeitzoneneinstellungen konvertieren](media/sample-crisis-communication-app/convert-time-zone.png)

## <a name="optional-configure-a-shared-inbox"></a>Optional: Konfigurieren eines freigegebenen Postfachs<a name="optional-configure-shared-inbox"></a>

Der "crisiscommunication. Request"-Flow ruft Anforderungen aus dem Posteingang ab, bevor Sie an Teams gesendet werden. Wenn Sie Anforderungs-e-Mails an einen freigegebenen Posteingang senden möchten, führen Sie die folgenden Schritte aus.

> [!NOTE]
> Sie können diesen Abschnitt überspringen, wenn Sie keine Anforderungs-e-Mails an einen freigegebenen Posteingang senden möchten.

1. Öffnen Sie den Datenfluss **crisiscommunication. Request** im Bearbeitungsmodus.
1. Wählen Sie **Weitere Befehle** (...) aus, **Wenn eine e-Mail von V3**empfangen wird.
1. Klicken Sie auf **Löschen**.

     ![Connector löschen](media/sample-crisis-communication-app/33-delete-connector.png)

1. Suchen Sie nach, und wählen Sie aus, **wann eine neue e-Mail in einem freigegebenen Postfach (v2)** eingeht.
1. Geben Sie die Adresse des freigegebenen **Posteingangs**in Post Fach Adresse ein
1. Öffnen Sie die **Kommentar** Karte.
1. Wählen Sie dynamischen Wert für **Wert** **Hinzufügen** aus.
1. Suchen Sie nach, und wählen Sie **Text**aus.

     ![Text auswählen](media/sample-crisis-communication-app/35-body.png)

1. Öffnen Sie die Karte " **Benutzerprofil Karte (v2)** ".
1. Wählen Sie **dynamischen Wert hinzufügen**aus.
1. Suchen Sie nach, und wählen Sie **aus**.

     ![Select from](media/sample-crisis-communication-app/34-from.png)

## <a name="import-and-set-up-the-admin-app"></a>Importieren und Einrichten der admin-App

Wiederholen Sie zum Verwalten der importierten APP die gleichen Schritte für die admin-app.

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.
1. Klicken Sie im linken Navigationsbereich auf **apps** .
1. Klicken Sie in der Befehlsleiste auf **importieren** .
1. Laden Sie die Datei **crisiscommunicationadmin. zip** aus dem GitHub-Repository hoch.

    ![Importieren des Admin-App-Pakets](media/sample-crisis-communication-app/import-app.png)

1. Wählen Sie **Importieren** aus.

### <a name="update-sharepoint-connections-for-the-admin-app"></a>Aktualisieren von SharePoint-Verbindungen für die admin-App

1. Wechseln Sie zurück zur Liste der **apps** .
1. Wählen Sie **Weitere Befehle** (...) für die Verwaltungs-App für die **Krisenkommunikation**aus.
1. Wählen Sie im Kontextmenü die Option **Bearbeiten** aus.

    ![Bearbeiten der admin-App](media/sample-crisis-communication-app/08-Edit-Admin-App.png)

1. Melden Sie sich an, oder erstellen Sie erforderliche Verbindungen, und klicken Sie dann auf **zulassen**.

1. Wechseln Sie zu den Datenquellen im linken Bereich.

    ![Datenquellen](media/sample-crisis-communication-app/data-sources.png)

1. Entfernen Sie vorhandene SharePoint-Listen in der APP, da Sie nicht auf Ihre aktuelle SharePoint-Website verweisen.<!--Please see previous editor's note.-->

    ![Entfernen von Datenquellen](media/sample-crisis-communication-app/remove-data-source.png)

1. Fügen Sie die Listen von ihrer eigenen SharePoint-Website hinzu. Starten Sie, indem Sie in der Suchleiste nach **SharePoint** suchen.

    ![Nach SharePoint suchen](media/sample-crisis-communication-app/sharepoint.png)

1. Wählen Sie **SharePoint**aus, und wählen Sie dann eine Verbindung aus.

    ![SharePoint-Verbindung](media/sample-crisis-communication-app/sharepoint-connection.png)

1. Kopieren Sie die URL, und fügen Sie Sie in das Textfeld auf Ihrer SharePoint-Website ein, und wählen Sie dann **verbinden**aus.

    ![URL der SharePoint-Website](media/sample-crisis-communication-app/site-url.png)

1. Wählen Sie alle SharePoint-Listen und-Bibliotheken aus, und klicken Sie dann auf **verbinden**.

    ![Herstellen einer Verbindung mit SharePoint-Listen](media/sample-crisis-communication-app/sharepoint-lists.png)

1. Wählen Sie **Speichern**aus, und wählen Sie dann **veröffentlichen**aus.

## <a name="create-initial-content-for-the-app"></a>Erstellen des anfänglichen Inhalts für die APP

An diesem Punkt haben Sie die APP für die Krisenkommunikation und Ihre Administrator-App erfolgreich importiert. Sie können nun mit dem Erstellen des anfänglichen Inhalts beginnen. Öffnen Sie zunächst die Verwaltungs-App für die Krisenkommunikation.

Wenn Sie über eine gcc-Umgebung verfügen, müssen Sie den gcc-Modus aktivieren. Weitere Informationen finden [Sie unter Konfigurieren von mobilen Clients für gcc-Umgebungen](https://docs.microsoft.com/power-platform/admin/powerapps-us-government#configure-mobile-clients).

![Die Verwaltungs-App für die Krisenkommunikation](media/sample-crisis-communication-app/09-Admin-App.png)

Sie verwenden die admin-APP, um alle Informationen in der App zur Krisenkommunikation anzupassen und die Schlüssel Einstellungen für die zugehörigen Flows zu konfigurieren.

> [!NOTE]
> Als Erinnerung&mdash;Wenn Sie die admin-APP nicht verwenden möchten, können Sie diese Eigenschaften bearbeiten, indem Sie die SharePoint-Listen manuell bearbeiten.

### <a name="set-up-key-parameters-under-admin-settings"></a>Einrichten von Schlüsselparametern unter "Administrator Einstellungen"

Um die APP zu initialisieren, müssen Sie alle erforderlichen Felder bereitstellen, indem Sie zu den **Administrator Einstellungen**navigieren.

Vervollständigen Sie alle Felder, wie in der folgenden Tabelle gezeigt, und wählen Sie dann **Speichern**aus.

| **Feldname** | **Logischer Name in SharePoint** | **Zweck** | **Beispiel** |
|-|-|-|-|
| E-Mail mit Administrator Berechtigungen | "Admincontactemail" | An dieser Stelle werden e-Mail-Anforderungen gesendet. Sie sollten auf Ihre e-Mail-Adresse festgelegt werden. Wenn Sie Benachrichtigungen an einen anderen Posteingang senden möchten, finden Sie weiter oben in diesem Artikel unter [Optionale Konfiguration für freigegebene Posteingangs](#optional-configure-shared-inbox)Informationen Weitere Informationen. | admin@contoso.com |
| Logo-URL | Logo | Das Logo Ihrer APP, das in der oberen linken Ecke angezeigt wird. | https://contoso.com/logo.png |
| Aad-Gruppen-ID | Aadgroupid | Dient zum Senden von Benachrichtigungen an Benutzer über interne Unternehmens Updates über die **Nachrichten über die Meldung "Benutzer über neue Krisen Mitteilung Benachrichtigen** ".<!--Can you rename this flow to "Notify users of new crisis communication news"? Or maybe even "Notify users of breaking news about the crisis"?--> Rom. Befolgen Sie die nachfolgenden Anweisungen, um die Azure Active Directory-ID (Azure AD) Ihrer Gruppe zu erhalten. | c0ddf873-b4fe-4602-b3a9-502dd944c8d5 |
| APP-URL | AppURL | Der Speicherort der Benutzer-APP, sodass der **Nachrichtenfluss "Benutzer bei neuer Krisen Mitteilung Benachrichtigen** " Benutzer dorthin umleiten kann, nachdem er **mehr erfahren**hat. | https://apps.preview.powerapps.com/play/<app URL>? tenantid =<tenant ID>
| RSS-Feed für Government | Governmentrssfeed | Wird verwendet, um das World News-Feature in der APP aufzufüllen. Nützlich, wenn Sie Ihren Mitarbeitern zusätzliche Informationen aus einer vertrauenswürdigen Quelle bereitstellen möchten. | https://www.who.int/rss-feeds/news-english.xml |
| Benachrichtigungs Methode | Preferredsentnotification | Wird vom Nachrichtenfluss " **Benutzer bei neuer Krisen Mitteilung Benachrichtigen** " verwendet, um zu bestimmen, welcher Verteilungs Kanal beim Versenden von Benachrichtigungen verwendet werden soll. Dieses Feld ist ein Pflichtfeld. | E-Mail, Teams-Benachrichtigung, Pushbenachrichtigung |
| Merkmals Flags | Feature1... 88 | Wird verwendet, um die einzelnen Funktionen in der Anwendung zu deaktivieren oder zu aktivieren. |  |

> [!NOTE]
> Team Benachrichtigung und Pushbenachrichtigung werden in gcc derzeit nicht unterstützt.


#### <a name="finding-the-azure-ad-id-for-your-distribution-group"></a>Ermitteln der Azure Ad-ID für die Verteiler Gruppe
<!--note from editor: The Cloud Style Guide says don't use "AAD" for "Azure AD."-->
1. Wechseln Sie zu [Aad.Portal.Azure.com](https://aad.portal.azure.com).
1. Wählen Sie im linken Navigationsbereich **Azure Active Directory** aus.
1. Wählen Sie **Gruppen**aus.
1. Suchen Sie die Verteiler Gruppe, und wählen Sie Sie aus.
1. Kopieren Sie das Feld **Objekt-ID** .

    ![Die Azure Ad-ID wird erhalten.](media/sample-crisis-communication-app/11-AAD-Group-ID.png)

1. Fügen Sie die ID in das Feld für die **Aad-Gruppen-ID** der admin-App ein.<!--Can you have this changed to "Azure AD group ID"? -->

### <a name="set-up-emergency-contacts"></a>Einrichten von Notfall Kontakten

1. Wechseln Sie zu **Unternehmens Kontakte**.
1. Wählen Sie **neuen Kontakt erstellen**aus.
1. Vervollständigen Sie das Formular mit den Kontakt Details.

*Listen Schema:*

| **Feldname** | **Logischer Name in SharePoint** | **Zweck** |
|-|-|-|
| Vollständiger Name | FullName | Der Name des Kontakts. |
| E-Mail | E-Mail | Die für den Kontakt angezeigte e-Mail-Adresse. |
| Land | Land | Das Land für den Kontakt. Dieses Feld wird verwendet, um die Kontakte zu gruppieren. Sie können andere Werte verwenden, um Kontakte nach zu gruppieren, wenn Länder für Sie nicht sinnvoll sind. |
| Comments | Comments | Zeigt zusätzliche Informationen über den Kontakt an. Es ist hilfreich zu beschreiben, wann Sie sich an diesen Kontakt wenden müssen. |
| Als veraltet markiert | Als veraltet markiert | Verwenden Sie, um einen vorhandenen Notfallkontakt auszublenden. |

### <a name="set-up-initial-company-news"></a>Einrichten von ersten Unternehmensnachrichten

1. Wechseln Sie zu **Unternehmensnachrichten**.
1. Wählen Sie **neuen Beitrag erstellen**aus.
1. Füllen Sie das Formular aus.

*Listen Schema:*

| **Feldname** | **Logischer Name in SharePoint** | **Zweck** |
|-|-|-|
| Titel | Titel | Der Titel des Updates. |
| Details | Details | Das vollständige Update. Sie können HTML in diesem Feld verwenden. |
| Blurb | Blurb | Eine kurze Nachricht über das Update. Diese wird im Nachrichtenfluss " **Benutzer bei neuer Krisen Mitteilung Benachrichtigen** " und im Katalog mit Updates verwendet. |
| Als veraltet markiert | Als veraltet markiert | Verwenden Sie, um einen vorhandenen Beitrag auszublenden. |

### <a name="set-up-helpful-tips"></a>Hilfreiche Tipps einrichten

1. Wechseln Sie zu **hilfreiche Tipps**.
1. Wählen Sie **neuer Tipp**aus.
1. Füllen Sie das Formular aus.

*Listen Schema:*

| **Feldname** | **Logischer Name in SharePoint** | **Zweck** |
|-|-|-|
| Titel | Titel | Der Titel des hilfreichen Tipps. |
| Ressourcen-URL | ResourceURL | Ein Link zu zusätzlichem Lesematerial. (Optional) |
| Untertitel | Titel | Ein Untertitel für den Tipp. (Optional) |
| Beschreibung | Beschreibung | Die vollständige Beschreibung des hilfreichen Tipps. |
| Als veraltet markiert | Als veraltet markiert | Verwenden Sie, um einen hilfreichen Tipp auszublenden. |

### <a name="set-up-links"></a>Einrichten von Links

1. Wechseln Sie zu **Links**.
1. Wählen Sie **neuen Link erstellen**aus.
1. Füllen Sie das Formular aus.

*Listen Schema:*

| **Feldname** | **Logischer Name in SharePoint** | **Zweck** |
|-|-|-|
| Titel | Titel | Der Text des Links. |
| URL | URL | Die URL des Links. |
| Beschreibung | Beschreibung | Weitere Details zum Link. (Optional) |
| Als veraltet markiert | Als veraltet markiert | Verwenden Sie, um einen Link auszublenden. |

### <a name="set-up-faqs"></a>FAQs einrichten

1. Wechseln Sie zu **FAQ**.
1. Wählen Sie **neue FAQ erstellen**aus.
1. Füllen Sie das Formular aus.

*Listen Schema:*

| **Feldname** | **Logischer Name in SharePoint** | **Zweck** |
|-|-|-|
| Titel | Titel | Die Frage in den FAQ. |
| Rang | Rang | Die Reihenfolge der Frage in den FAQ. |
| Te | Te | Die Antwort auf die Frage in den FAQ. |
| Als veraltet markiert | Als veraltet markiert | Verwenden Sie, um eine Frage in den FAQ auszublenden. |

## <a name="test-and-share-the-app"></a>Testen und Freigeben der APP

Nachdem Sie nun alle Daten erfolgreich eingerichtet haben, können Sie die APP testen, um sicherzustellen, dass Sie funktioniert.

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.
2. Klicken Sie im linken Navigationsbereich auf **apps** .
3. Wählen Sie die **Krisenkommunikation** aus, um die APP wiederzugeben

Nachdem Sie die APP erfolgreich getestet haben, können Sie Sie für alle Personen in Ihrem Unternehmen freigeben.

## <a name="import-and-set-up-the-notification-flow"></a>Importieren und Einrichten des Benachrichtigungs Flusses

Die APP verwendet einen Flow, um Benachrichtigungen an Endbenutzer zu senden, wenn ein neues Unternehmens Update vorliegt.

### <a name="import-the-news-notification-flow"></a>Importieren des Nachrichten Benachrichtigungs Flusses

1. Wechseln Sie zu [Flow.Microsoft.com](https://flow.microsoft.com).
1. Wählen Sie im linken Navigationsbereich **meine Flows** aus.
1. Klicken Sie in der Befehlsleiste auf **importieren** .
1. Laden Sie das Paket **crisiscommunicationnewsnotification. zip** aus dem GitHub-Repository hoch.

    > [!NOTE]
    > Wenn sich Ihr Mandant in einer gcc-Umgebung befindet, laden Sie **crisiscommunicationnewsnotificationgcc. zip**hoch.

    ![Crisiscommunicationnewsnotification. zip hochladen](media/sample-crisis-communication-app/upload-news-notification.png)

1. Fügen Sie Verbindungen für den neuen Flow hinzu, indem Sie für jede Verbindung den Link **Select during Import** auswählen und dann das Formular ausfüllen.

    ![Während des Imports auswählen](media/sample-crisis-communication-app/select-during-import.png)

1. Wenn Sie eine neue Verbindung erstellen müssen, wählen Sie im Bereich **Setup importieren** die Option **neu erstellen** aus.
1. Wählen Sie in der Befehlsleiste **neue Verbindung** aus.

    ![Erstellen einer neuen Verbindung](media/sample-crisis-communication-app/create-connection.png)

1. Suchen Sie nach dem Namen der Verbindung. Beispiel: **powerapps-Benachrichtigung (Vorschau)** .

    ![Beispiel für Verbindungs Name](media/sample-crisis-communication-app/notifications.png)

1. Wählen Sie die gewünschte Verbindung aus.
1. Wenn Sie eine Verbindung zu **powerapps-Benachrichtigungen (Vorschau)** erstellen, wird das Dialogfeld wie in der folgenden Abbildung dargestellt angezeigt.

    ![Benachrichtigungen (Dialogfeld)](media/sample-crisis-communication-app/notifications-dialog.png)

1. Um die ID zu erhalten, navigieren Sie zu Ihrer **App** -Liste.
1. Wählen Sie **Weitere Befehle** (...) für die APP für die **Krisenkommunikation** aus, und wählen Sie dann **Details**aus.

    ![Details für die Verbindung](media/sample-crisis-communication-app/06-App-Details.png)

1. Kopieren Sie die **App ID**.

    ![App-ID](media/sample-crisis-communication-app/07-App-ID.png)

1. Fügen Sie die APP-ID in das Dialogfeld Verbindungs Erstellung ein, und wählen Sie dann **Erstellen**aus.

    ![Erstellen einer Verbindung](media/sample-crisis-communication-app/target-app-id.png)

1. Nachdem Sie die neue Verbindung erstellt haben, wechseln Sie zurück zum Bereich **Setup importieren** , und wählen Sie dann **Liste aktualisieren**aus.
1. Die neue Verbindung sollte jetzt angezeigt werden. Wählen Sie es aus, und klicken Sie dann auf **Speichern**.
1. Nachdem Sie alle Verbindungen hinzugefügt haben, wählen Sie **importieren**aus.

    ![Importieren von Verbindungen](media/sample-crisis-communication-app/imported-connections.png)

### <a name="edit-the-news-notification-flow"></a>Bearbeiten des Nachrichten Benachrichtigungs Flusses

1. Nachdem der Import Vorgang abgeschlossen ist, wechseln Sie zu **meine Flows**.
1. Wählen Sie den neu importierten Flow aus, und Benachrichtigen Sie die **Benutzer über neue Kommunikations Nachrichten**.

    > [!NOTE]
    > Wenn Sie das gcc-Paket hochgeladen haben, benachrichtigt der flowname **Benutzer über den neuen Migrations Vorgang für die Krisenkommunikation**.

1. Wählen Sie in der Befehlsleiste die Option **Bearbeiten** aus.
1. Öffnen Sie die Karte **Wenn ein neues Element gepostet wird** .
1. Geben Sie als **Website Adresse**den Namen Ihrer SharePoint-Website ein.
1. Geben Sie für **Listen Name** **CI_CompanyNews**ein.
1. Öffnen Sie die Karte **admin config Settings-Einstellungen** .
1. Geben Sie als **Website Adresse**den Namen Ihrer SharePoint-Website ein.
1. Geben Sie für **Listen Name** **CI_configAdminSetup**ein.
1. Öffnen **Sie die Textkarte Initialize Variable – Read More Text** .
1. Geben Sie unter **Wert den Wert** **Read More** (in ihrer nativen Sprache) ein.

    ![Fluss Einstellungen](media/sample-crisis-communication-app/flow-options.png)

1. Wählen Sie **Speichern** aus.

> [!NOTE]
> Sie erhalten möglicherweise eine Fehlermeldung, wenn eine ihrer Verbindungen noch nicht autorisiert wurde.
Öffnen Sie in diesem Fall die Karte mit der nicht autorisierten Verbindung, und führen Sie eine erneute Autorisierung durch.


### <a name="optional-sending-notifications-to-more-than-5000-users"></a>Optional: Senden von Benachrichtigungen an mehr als 5000 Benutzer

Die aktuelle Aktion zum Abrufen von **Gruppenmitgliedern** ist auf das Abrufen von 5000-Benutzern für die Office-Lizenz der Energie Automatisierung beschränkt. Selbst bei der Premium-Lizenz können Sie Drosselungs Limits mit dem Teams-Connector erreichen, wenn Sie versuchen, Benachrichtigungen an zu viele Benutzer zu senden. Um an weitere Benutzer zu verteilen, können Sie in den Flow ändern, um stattdessen eine e-Mail an eine Verteilerliste zu senden.

1. Löschen Sie die folgenden Karten: **Gruppenmitglieder gruppieren** und **auf bevorzugte Sende Benachrichtigungs Einstellung wechseln**:

    ![Lösch Aktionen](media/sample-crisis-communication-app/36-delete-actions.png)

1. Fügen Sie eine neue Aktion hinzu.

1. Suchen und wählen Sie **eine e-Mail senden (v2)** :

    ![Hinzufügen einer e-Mail senden](media/sample-crisis-communication-app/37-add-send-an-email.png)

1. Geben Sie im Feld **an** den Namen der Verteiler Gruppe ein.

1. Wählen Sie im Feld **Betreff** die Schaltfläche **dynamischen Wert hinzufügen** aus, und fügen Sie das Feld **Title** von der Karte **Wenn ein Nachrichten Element gepostet wird** hinzu:

    ![Titel hinzufügen](media/sample-crisis-communication-app/38-add-title.png)

1. Wählen Sie im Feld **Text** die Schaltfläche **dynamischen Wert hinzufügen** aus, und fügen Sie das Feld **Details** der Karte **Wenn ein Nachrichten Element gepostet angezeigt wird** hinzu.

1. Wählen Sie **Speichern** aus.

### <a name="test-the-news-notification-flow"></a>Testen des nachrichtenbenachrichtigungs Flusses

Um den Nachrichtenfluss zu testen, wechseln Sie zur Administrator-APP, und erstellen Sie ein neues internes Unternehmens Update. Später erhalten alle Benutzer in der Verteilerliste von Ihrer bevorzugten Benachrichtigungs Methode ein Update.

> [!NOTE]
> Wenn Fehler auftreten, stellen Sie sicher, dass Sie die Gruppen-ID Ihrer Verteilerliste in den Einstellungen für die admin-App erfolgreich eingegeben haben.

## <a name="monitor-office-absences-with-power-bi"></a>Überwachen von Office-Abwesenheits Punkten mit Power BI

Nachdem Sie die APP bereitgestellt haben und die Benutzer mit dem Senden von Benachrichtigungen beginnen, dass Sie aus verschiedenen Gründen aus dem Büro bestehen (z. b. krank oder von Hause aus), können Sie mit einem Power BI Bericht nachverfolgen, wie viele Personen Benachrichtigungen gesendet haben und wo Sie sich befinden.  
Beachten Sie, dass Sie die [Standortüberwachung aktivieren](#optional-enable-location-updates) müssen, damit das Karten Steuerelement funktioniert. 

> [!IMPORTANT]
> Damit der Bericht Power BI funktioniert, müssen Sie mindestens einen Eintrag in der Liste **CI_Employee Status** aufweisen.

Wir benötigen einige Informationen aus der **CI_Employee Status** -SharePoint-Liste, die wir zuvor erstellt haben. Wir werden also zuerst darauf eingehen. Öffnen Sie die Liste auf Ihrer Website, und wählen Sie dann unter dem Symbol **Einstellungen** die Option **Einstellungen auflisten** aus.

![Einstellungen der Mitarbeiter Status Liste](media/sample-crisis-communication-app/001-SharePointList-ListSettings-nolines.PNG)

Notieren Sie sich den Website Namen und die Listen-ID in der Adressleiste des Browsers, wie in der folgenden Abbildung dargestellt.

![Mitarbeiter Status Liste und Website-ID](media/sample-crisis-communication-app/002-SharePointList-AddressAndId-nolines.PNG)

An diesem Punkt können wir den Power BI Bericht öffnen. Öffnen Sie Power BI, und öffnen Sie dann die **pbix-Datei des Anwesenheitsstatus Berichts** . Bewegen Sie den Mauszeiger über die Rechte Seite der **CI_Employee Status** -Datenquelle, bis die Auslassungs Punkte angezeigt werden. Wählen Sie diese Option aus, und klicken Sie dann auf **Abfrage bearbeiten**.

![Abfrage bearbeiten](media/sample-crisis-communication-app/003-PowerBI-EditQuery-nolines.PNG)

Nachdem der Power Query-Editor geöffnet wurde, klicken Sie mit der rechten Maustaste auf die **CI_Employee Status** -Datenquelle, und wählen Sie dann **Erweiterter Editor**aus.

![Power Query Erweiterter Editor](media/sample-crisis-communication-app/004-PowerQuery-AdvancedEditor-nolines.PNG)

Hier verwenden wir den Website Namen und die Listen-ID aus der SharePoint-Liste.

Kopieren Sie die neue SharePoint-Website in die Zeichenfolge "SharePoint. Tables", wie in der folgenden Abbildung dargestellt.<!--Edit okay? This is a case where the image shows information that the text doesn't, so I'm not sure how to make this descriptive enough for people who aren't looking at the graphics, or people with low vision.--> und die Listen-ID an den drei Stellen, an denen die GUID hervorgehoben ist, und wählen Sie dann **abgeschlossen**aus.

![Power Query Erweiterter Editor Updates](media/sample-crisis-communication-app/005-PowerQuery-AdvancedEditorUpdates-nolines.PNG)

Wenn nach dem Aktualisieren der Verbindungsinformationen Verbindungsfehler angezeigt werden, müssen Sie möglicherweise die Anmelde Informationen aktualisieren, die zum Herstellen einer Verbindung mit der SharePoint-Liste verwendet werden. 

**So aktualisieren Sie die Verbindung**

1. Wählen Sie im Menü **Datei** die **Option Optionen und Einstellungen**, und wählen Sie dann **Datenquellen Einstellungen**aus.

    ![Datenquelleneinstellungen](media/sample-crisis-communication-app/PBI-1-DataSourceSettings.PNG)

1. Wählen Sie **Berechtigungen bearbeiten**aus.

    ![Berechtigungen bearbeiten](media/sample-crisis-communication-app/PBI-2-DataSourceSettings-EditPermissions.PNG)

1. Stellen Sie sicher, dass der Typ **Anmelde** Informationen auf **Organisations Konto**festgelegt ist, und verwenden Sie die Anmelde Informationen für den Zugriff auf die SharePoint

    ![Berechtigungen bearbeiten](media/sample-crisis-communication-app/PBI-3-OrganizationalAccount.PNG)

Wählen Sie **& schließen** aus, um den Bericht zu aktualisieren, um Daten aus Ihrer SharePoint-Liste abzurufen.

![Power Query schließen und anwenden](media/sample-crisis-communication-app/006-PowerQuery-CloseAndApply-nolines.PNG)

Wir verfügen nun über einen Power BI Bericht, der sowohl die geografischen Informationen für die Abwesenheit von Office für den aktuellen Tag als auch einen Trend der derartigen Abwesenheits Tage im Verlauf mehrerer Tage anzeigt. Wir können den Bericht veröffentlichen, damit andere Personen in der Organisation ihn sehen können.

![Power BI veröffentlichungsbericht](media/sample-crisis-communication-app/007-PowerBI-Publish-nolines.PNG)

Der Bericht wird jetzt veröffentlicht. Sie können Sie für andere Personen in Ihrer Organisation freigeben. Sie können auch [die Berichts Aktualisierungshäufigkeit planen](https://docs.microsoft.com/power-bi/refresh-scheduled-refresh).

## <a name="integrate-your-app-into-teams"></a>Integrieren ihrer app in Teams

Nachdem Sie nun über eine funktionierende App verfügen, die für alle Benutzer freigegeben wurde, können Sie die APP bereitstellen, indem Sie ein Krisenmanagementteam innerhalb von Teams erstellen, um auf Probleme zu reagieren.

### <a name="deploy-the-app-to-the-app-bar"></a>Bereitstellen der APP auf der APP-Leiste

Wenn Sie ein Team Administrator sind, können Sie die APP per Push an alle Benutzer in der APP-Leiste des Teams übersetzen.

![App-Leiste in Teams](media/sample-crisis-communication-app/19-App-in-Teams.png)

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.
1. Klicken Sie im linken Navigationsbereich auf **apps** .
1. Wählen Sie **Weitere Befehle** (...) für die APP zur **Krisenkommunikation** aus.
1. Wählen Sie **zu Teams hinzufügen**aus.

    ![Zu Teams hinzufügen](media/sample-crisis-communication-app/24-Add-to-Teams.png)

1. Wählen Sie **app herunterladen**aus.

    ![App herunterladen](media/sample-crisis-communication-app/25-Download-App.png)

1. Öffnen Sie Teams.
1. Wechseln Sie in der APP-Leiste zu **apps** .
1. Wählen Sie **benutzerdefinierte App hochladen**aus.
1. Wenn Sie ein Team Administrator sind, können Sie eine APP für Ihren gesamten Mandanten hochladen. Wählen Sie für "" die Option " *Contoso* **hochladen" für** "Configuration Manager" aus.<!--Edit okay? The screenshot said "Contoto," which I fixed.-->.

    ![Hochladen der APP](media/sample-crisis-communication-app/26-Upload-for-Contoso.png)

1. Laden Sie die Datei hoch, die Sie aus Power apps heruntergeladen haben.
1. Wechseln Sie zum [Teams Admin Center](https://admin.teams.microsoft.com/dashboard).
1. Wählen Sie im linken Navigationsbereich unter **Teams-apps**die Option Setup- **Richtlinien**aus.

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

### <a name="create-a-central-crisis-management-team-in-teams"></a>Erstellen eines Teams für das zentrale Krisenmanagement in Teams<a name="create-a-central-crisis-management-teams-team"></a>

Um Ihre Reaktion auf Ihre Reaktion zu koordinieren, sollten Sie ein zentrales Krisenmanagementteam in Teams erstellen und es mit allen relevanten Informationen füllen. Dieses Team muss nur für das zentrale Antwort Team freigegeben werden.

1. Wechseln Sie zu Teams.
1. Wählen Sie in der linken App-Leiste **Teams** aus.
1. Wählen Sie beitreten aus, **oder erstellen Sie ein Team**.
1. Wählen Sie **Team erstellen**aus, und führen Sie dann die restlichen Schritte aus.

    ![Erstellen eines Teams](media/sample-crisis-communication-app/23-Create-Team.png)

Nachdem Sie das Team erfolgreich erstellt haben, können Sie relevante Informationen als Registerkarten anheften. Beispielsweise können Sie die "Crisis Management"-Administrator-APP oder den Power BI Bericht an Ihr Team anheften.

**So fügen Sie die Administrator-App als Registerkarte hinzu**

1. Wählen Sie die Schaltfläche **+** aus.
1. Suchen Sie nach **Power apps**, und wählen Sie Sie aus.
1. Suchen Sie nach, und wählen Sie " **Information admin**" aus

    ![Anheften der App](media/sample-crisis-communication-app/32-Pin-Teams-app.png)

1. Wählen Sie **Speichern** aus.

**So fügen Sie den Power BI Bericht als Registerkarte hinzu**

1. Wählen Sie die Schaltfläche **+** aus.
1. Suchen Sie nach **Power BI**und wählen Sie ihn aus.
1. Suchen Sie den Power BI Bericht, und wählen Sie ihn aus.
1. Wählen Sie **Speichern** aus.

## <a name="faq"></a>Häufig gestellte Fragen

* **Welche Lizenzen benötige ich, um diese Lösung auszuführen?**

    - Die Lösung in dieser APP verwendet Office-Connectors. Daher reicht eine per Seeding betriebene Power apps-Lizenz aus Office aus, um die Benutzer-und admin-apps auszuführen und wiederzugeben. Weitere Informationen finden Sie unter [Übersicht über die Power Platform-Lizenzierung](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus)
    - Wenn Sie den Power BI Bericht verwenden möchten (verpackt als Teil der Lösung), benötigen Sie eine Power BI-Lizenz. Weitere Informationen finden Sie unter [Power BI Preise](https://powerbi.microsoft.com/pricing/)

* **Wo sollte ich mich Feedback zur Lösung machen?**

    Wir freuen uns über ihre Erfahrungen mit der Bereitstellung und Anpassung dieser Lösung. Besuchen Sie [aka.ms/Crisis-Communication-Feedback](https://aka.ms/crisis-communication-feedback).

* **Es scheint einen Fehler mit der APP zu finden. wo sollte ich es tun?**

   Wechseln Sie zu [aka.ms/Crisis-Communication-Issues](https://aka.ms/crisis-communication-issues), um einen Fehler in der Lösung zu melden.

* **Welche Features werden in gcc derzeit nicht unterstützt?**

    Der Power automatisierter bot-Connector für Teams und der pushbenachrichtigungsconnector sind zurzeit nicht für gcc verfügbar. Verwenden Sie die Option e-Mail, um Benutzer über interne News Updates zu benachrichtigen.

* **Wie kann ich die Anwendung aktualisieren?**

    Wenn Sie die Anwendung aktualisieren möchten, führen Sie die unter [aka.ms/CrisisCommunicationSolution](https://aka.ms/CrisisCommunicationSolution)beschriebenen Schritte aus.

## <a name="issues-and-feedback"></a>Probleme und Feedback

- Feedback zur Beispiel Vorlage für die Krisenkommunikation finden Sie unter [aka.ms/Crisis-Communication-Feedback](https://aka.ms/crisis-communication-feedback).
- Wenn Sie ein Problem mit der App zur Krisenkommunikation melden möchten, gehen Sie zu [aka.ms/Crisis-Communication-Issues](https://aka.ms/crisis-communication-issues).

***Haftungsausschluss:*** *diese APP ist ein Beispiel und kann mit Microsoft powerapps und Teams für die Verbreitung von Referenzinformationen verwendet werden. Diese APP ist nicht für das medizinische Gerät, den klinischen Support, das Diagnosetool oder andere Technologien vorgesehen, die bei der Diagnose, beim Schutz, bei der Entschärfung, bei der Behandlung oder bei der Verhinderung von Krankheiten oder anderen Bedingungen verwendet werden sollen, und von Microsoft wird keine Lizenz oder das Recht erteilt, diese APP zu diesem Zweck zu verwenden.  Diese APP ist nicht als Ersatz für professionelle medizinische Beratung, Diagnose, Behandlung oder Beurteilung gedacht und sollte nicht als solche verwendet werden.  Der Kunde hat das alleinige Risiko und die Verantwortung für die Verwendung dieser app.  Microsoft garantiert nicht, dass die APP oder die darin enthaltenen Materialien zu medizinischen Zwecken ausreichen oder die Integritäts-oder medizinischen Anforderungen beliebiger Personen erfüllen.* 

### <a name="see-also"></a>Siehe auch
<!--note from editor: "Next steps" would work if you gave the reader some action items, but reference topics are random access by nature, so the heading is rightly "See also." -->
- [Referenz zu Formeln](formula-reference.md)
- [Referenz zu Steuerelementen](reference-properties.md)
