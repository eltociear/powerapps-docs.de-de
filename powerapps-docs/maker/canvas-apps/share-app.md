---
title: Freigeben einer Canvas-App | Microsoft-Dokumentation
description: Geben Sie Ihre Canvas-App frei, indem Sie anderen Benutzern die Berechtigung erteilen, die App auszuführen oder zu ändern.
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 11/28/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b070dfad61f3e53e313d4e8891dc44507a910292
ms.sourcegitcommit: edf79033111b50aa3015b55929ce689474edba2d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68917430"
---
# <a name="share-a-canvas-app-in-powerapps"></a>Freigeben einer Canvas-App in PowerApps

Nachdem Sie eine Canvas-App erstellt haben, die eine geschäftliche Anforderung behandelt, geben Sie an, welche Benutzer in Ihrer Organisation die App ausführen dürfen und welche sie ändern oder sogar erneut freigeben dürfen. Geben Sie jeden Benutzer anhand seines Namens an, oder geben Sie eine Sicherheitsgruppe in Azure Active Directory an. Wenn jeder von Ihrer App profitieren würde, geben Sie an, dass Ihre gesamte Organisation diese ausführen darf.

> [!IMPORTANT]
> Damit eine freigegebene App erwartungsgemäß funktioniert, müssen Sie auch Berechtigungen für die Datenquelle oder die Quellen verwalten, auf denen die APP basiert, z. b. [Common Data Service](#common-data-service) oder [Excel](share-app-data.md). Sie müssen möglicherweise auch [andere Ressourcen freigeben](share-app-resources.md), von denen die App abhängt, z.B. Flows, Gateways oder Verbindungen.

## <a name="prerequisites"></a>Vorraussetzungen

Um eine App freizugeben, müssen Sie sie in der Cloud speichern (nicht lokal) und dann veröffentlichen.

- Geben Sie Ihrer App einen aussagekräftigen Namen und eine klare Beschreibung, damit Benutzer wissen, was die App bewirkt und sie so leicht in einer Liste finden können. Wählen Sie im Menü **Datei** in PowerApps Studio die **App-Einstellungen** aus, geben Sie einen Namen an, und tippen bzw. fügen Sie eine Beschreibung ein.

- Wenn Sie Änderungen vornehmen, müssen Sie die App speichern und erneut veröffentlichen, wenn andere Personen diese Änderungen sehen sollen.

## <a name="share-an-app"></a>Eine App freigeben

1. [Melden Sie sich bei PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an, und wählen Sie dann am linken Bildschirmrand **Apps** aus.

    ![Anzeigen der App-Liste](./media/share-app/file-apps.png)

1. Wählen Sie die APP aus, die Sie freigeben möchten, indem Sie das zugehörige Symbol auswählen.

    ![App auswählen](./media/share-app/select-app.png)

1. Wählen Sie im Banner die Option **Freigeben**aus.

    ![Geöffneter Bildschirm „Freigeben“](./media/share-app/banner-share.png)

1. Geben Sie die Benutzer oder Sicherheitsgruppen in Azure Active Directory, mit denen Sie die APP freigeben möchten, nach Namen oder Aliasnamen an.

    - Um ihrer gesamten Organisation das Ausführen der APP zu gestatten (ohne Sie zu ändern oder freizugeben), geben Sie im Freigabe Bereich **alle** ein.
    - Wenn die Elemente durch Semikolons voneinander getrennt sind, können Sie eine APP mit einer Liste von Aliasen, anzeigen Amen oder einer Kombination aus diesen Teilen (z. b.  **&lt;Jane Doe jane.doe@contoso.com>** ). Wenn mehr als eine Person denselben Namen, aber unterschiedliche Aliase hat, wird die erste gefundene Person zur Liste hinzugefügt. Eine QuickInfo wird angezeigt, wenn ein Name oder Alias bereits über eine Berechtigung verfügt oder nicht aufgelöst werden kann. 

    ![Angeben von Benutzern und Mitbesitzern](./media/share-app/share-everyone.png)

    > [!NOTE]
    > Sie können eine APP nicht für eine Verteiler Gruppe in Ihrer Organisation oder für einen Benutzer oder eine Gruppe außerhalb Ihrer Organisation freigeben.

1. Wenn Sie zulassen möchten, dass Sie die APP freigeben, um Sie zu bearbeiten und freizugeben (zusätzlich zur Ausführung), aktivieren Sie das Kontrollkästchen **Mitbesitzer** .

    Sie können einer Sicherheitsgruppe keine **Co-Owner-** Berechtigung erteilen, wenn Sie [die APP innerhalb einer Lösung erstellt](add-app-solution.md)haben.

    > [!NOTE]
    > Unabhängig von den Berechtigungen können zwei Personen eine APP nicht gleichzeitig bearbeiten. Wenn eine Person die APP für die Bearbeitung öffnet, kann Sie von anderen Personen ausgeführt, aber nicht bearbeitet werden.

1. Wenn Ihre APP eine Verbindung mit Daten herstellt, für die Benutzer Zugriffsberechtigungen benötigen, geben Sie Sie an.

    Beispielsweise kann Ihre APP eine Verbindung mit einer Entität in einer Common Data Service Datenbank herstellen. Wenn Sie eine solche APP freigeben, werden Sie im Freigabe Bereich aufgefordert, die Sicherheit für diese Entität zu verwalten.

    > [!div class="mx-imgBorder"]
    > ![Zuweisen einer Sicherheitsrolle](media/share-app/cds-assign-security-role.png)

    Weitere Informationen zum Verwalten der Sicherheit für eine Entität finden Sie weiter unten in diesem Thema unter [Verwalten von Entitäts Berechtigungen](share-app.md#manage-entity-permissions) .

1. Wenn Sie Benutzern helfen möchten, Ihre APP zu finden, aktivieren Sie das Kontrollkästchen **e-Mail an neue Benutzer senden** .

1. Wählen Sie am unteren Rand des Bereichs Freigabe die Option **Freigeben**aus.

    Alle Benutzer, für die Sie die APP freigegeben haben, können Sie in powerapps Mobile auf einem mobilen Gerät oder in appsource auf [Dynamics 365](https://home.dynamics.com) in einem Browser ausführen. Mitbesitzer können die app in [powerapps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)bearbeiten und freigeben.

    Wenn Sie eine e-Mail-Einladung gesendet haben, kann jede Person, für die Sie die APP freigegeben haben, Sie ausführen, indem Sie einen Link in der Einladung

    - Wenn ein Benutzer den Link auf einem mobilen Gerät auswählt, wird die app in powerapps Mobile geöffnet.
    - Wenn ein Benutzer den Link auf einem Desktop Computer auswählt, wird die app in einem Browser geöffnet.

    Mitbesitzer, die eine Einladung erhalten, erhalten einen weiteren Link, der die APP zum Bearbeiten in PowerApps Studio öffnet.

Sie können die Berechtigungen für einen Benutzer oder eine Sicherheitsgruppe ändern, indem Sie den Namen auswählen und dann einen der folgenden Schritte ausführen:

- Deaktivieren Sie das Kontrollkästchen **Mitbesitzer** , um den Mitbesitzern das Ausführen der APP zu gestatten, diese aber nicht mehr zu bearbeiten oder freizugeben.
- Wählen Sie das Symbol entfernen (x) aus, um die Freigabe der APP für diesen Benutzer bzw. diese Gruppe zu verhindern.

## <a name="security-group-considerations"></a>Überlegungen zu Sicherheitsgruppen

- Wenn Sie eine App für eine Sicherheitsgruppe, bestehende Mitglieder dieser Gruppe und jeden freigeben, der dieser Gruppe beitritt, verfügen alle über die von Ihnen angegebenen Berechtigungen für diese Gruppe. Jeder, der die Gruppe verlässt, verliert diese Berechtigung, es sei denn, die Person gehört noch zu einer anderen Gruppe, die über Zugriff verfügt, oder Sie verleihen der Person die Berechtigung als Einzelperson.

- Jedes Mitglied einer Sicherheitsgruppe besitzt dieselbe Berechtigung für eine App wie die Gruppe. Sie können allerdings für ein Mitglied oder mehrere Mitglieder dieser Gruppe tiefgreifendere Berechtigungen angeben, um diesen Personen besseren Zugriff zu gewähren. Beispielsweise können Sie der Sicherheitsgruppe eine Berechtigung zum Ausführen einer APP erteilen. Sie können jedoch auch den Benutzer B, der dieser Gruppe angehört, die **Mitbesitzer** Berechtigung erteilen. Jedes Mitglied der Sicherheitsgruppe kann die App ausführen, aber nur Benutzer B kann diese bearbeiten. Wenn Sie der Sicherheitsgruppe eine **Mitbesitzer** -Berechtigung erteilen und die Benutzer B Berechtigung zum Ausführen der APP besteht, kann der Benutzer die APP trotzdem bearbeiten.

## <a name="manage-entity-permissions"></a>Verwalten von Entitätsberechtigungen

### <a name="common-data-service"></a>Common Data Service

Wenn Sie eine App basierend auf Common Data Service erstellen, müssen Sie auch sicherstellen, dass die Benutzer, für die Sie die APP freigeben, über die entsprechenden Berechtigungen für die Entitäten oder Entitäten verfügen, von denen die APP abhängig ist. Insbesondere müssen diese Benutzer zu einer Sicherheitsrolle gehören, die Aufgaben wie das Erstellen, lesen, schreiben und löschen relevanter Datensätze ausführen kann. In vielen Fällen empfiehlt es sich, eine oder mehrere benutzerdefinierte Sicherheitsrollen mit den genauen Berechtigungen zu erstellen, die Benutzer zum Ausführen der APP benötigen. Anschließend können Sie jedem Benutzer eine Rolle zuweisen.

> [!NOTE]
> Zum Zeitpunkt der Erstellung dieses Artikels können Sie einzelnen Benutzern und Sicherheitsgruppen in Azure Active Directory, aber nicht in Office-Gruppen Sicherheitsrollen zuweisen.

#### <a name="prerequisite"></a>Voraussetzung

Sie müssen über **System Administrator** Berechtigungen für eine Common Data Service Datenbank verfügen, um eine Rolle zuweisen zu können.

#### <a name="assign-a-security-group-in-azure-ad-to-a-role"></a>Zuweisen einer Sicherheitsgruppe in Azure AD zu einer Rolle

1. Wählen Sie im Bereich Freigabe unter **Daten Berechtigungen**die Option **Sicherheitsrolle zuweisen** aus.

1. Wählen Sie in Common Data Service die Rolle oder Rollen aus, die Sie dem Benutzer oder der Sicherheitsgruppe in Azure AD zuweisen möchten, mit der Sie die APP freigeben möchten.

    ![Sicherheitsrollen Liste](media/share-app/cds-assign-security-role-list.png)

### <a name="common-data-service-previous-version"></a>Common Data Service (vorherige Version)

Wenn Sie eine APP freigeben, die auf einer älteren Version von Common Data Service basiert, müssen Sie die Lauf Zeit Berechtigung separat für den Dienst freigeben. Wenn Sie nicht über die entsprechende Berechtigung verfügen, finden Sie weitere Informationen unter Administrator der Umgebung.

## <a name="share-with-guests"></a>Mit Gästen teilen

> [!IMPORTANT]
> - Die Features der Vorschauversion sind nicht für Produktionszwecke gedacht und funktionieren möglicherweise nur eingeschränkt. Diese Features sind vor dem offiziellen Release verfügbar, damit Kunden einen frühzeitigen Zugriff erhalten und Feedback geben können. 
> - Vorschau Features werden durch Microsoft-Support nur eingeschränkt unterstützt und sind möglicherweise nur in ausgewählten geografischen Gebieten verfügbar. 

Powerapps-Canvas-Apps können für Gastbenutzer eines Azure Active Directory Mandanten freigegeben werden. Dadurch können externe Geschäftspartner, Auftragnehmer und Drittanbieter zum Ausführen der Canvas-apps Ihres Unternehmens eingeladen werden. 

Beachten Sie, dass Gäste für apps, die für Sie freigegeben sind, nur die Benutzerrolle und nicht die Rolle "Mitbesitzer" zugewiesen werden können.

### <a name="prerequisites"></a>Vorraussetzungen
1. Aktivieren Sie in Azure Active Directory die [externe B2B-Zusammenarbeit](https://docs.microsoft.com/en-us/azure/active-directory/b2b/delegate-invitations) für den Mandanten.  
- Diese Einstellung ist standardmäßig aktiviert. die Einstellungen können von einem Mandanten Administrator geändert werden.  
- Weitere Informationen zur Azure AD B2B-Prüfung finden Sie hier: [Was ist der Gastbenutzer Zugriff in Azure AD B2B?](https://docs.microsoft.com/en-us/azure/active-directory/b2b/what-is-b2b)  
2. Zugriff auf ein Konto, das Gastbenutzer zu einem Aad-Mandanten hinzufügen kann. Administratoren und Benutzer mit der "Guest Inviter"-Rolle können Gäste zu einem Mandanten hinzufügen.   
3. Eine powerapps-Lizenz muss dem Gastbenutzer im Mandanten zugewiesen werden, dem die freigegebene App zugeordnet ist. Vor der allgemeinen Verfügbarkeit des Gast Zugriffs auf eine Canvas-app muss Gästen mit einer powerapps-Lizenz in Ihrem Privat Mandanten keine Lizenz im Mandanten zugewiesen werden, die Sie als Gast haben.

### <a name="steps"></a>Schritte
1. Fügen Sie Gastbenutzer in Azure Active Directory hinzu.  
- Dies wird im folgenden Artikel erläutert: [Schnellstart: Fügen Sie einen neuen Gastbenutzer in](https://docs.microsoft.com/en-us/azure/active-directory/b2b/b2b-quickstart-add-guest-users-portal)Azure AD hinzu.
![Gast in Azure AD hinzufügen](media/share-app/guest_access_doc_1.png)
2. Weisen Sie dem Gastbenutzer eine Lizenz zu. 
- Dies wird in den folgenden Artikeln beschrieben: [Zuweisen von Lizenzen zu einem Benutzer](https://docs.microsoft.com/en-us/office365/admin/subscriptions-and-billing/assign-licenses-to-users?view=o365-worldwide#assign-licenses-to-one-user) oder [zuweisen oder Entfernen von Lizenzen](https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/license-users-groups) von https://admin.microsoft.com https://portal.azure.com Benutzern für bzw.  
- Beachten Sie, dass Sie möglicherweise die Microsoft 365 Admin Center-Vorschau deaktivieren müssen, um einem Gast eine Lizenz zuzuweisen. 
3. Freigeben der Canvas-app. 
- Anmelden bei https://make.powerapps.com  
- Wählen Sie eine APP aus, und klicken Sie auf freigeben. 
![Die Freigabe mit](media/share-app/guest_access_doc_2.png)
Gast![Gästen darf nur Benutzer sein.](media/share-app/guest_access_doc_3.png)
4. Gäste können apps, die für Sie freigegeben wurden, über die im Rahmen der Freigabe gesendete e-Mail ermitteln und darauf zugreifen.
![Gast-e-Mails für e-Mail erhalten](media/share-app/guest_access_doc_4.png)

### <a name="frequently-asked-questions"></a>Häufig gestellte Fragen

#### <a name="whats-the-difference-between-canvas-app-guest-access-and-powerapps-portal"></a>Worin besteht der Unterschied zwischen dem Canvas-App-Gast Zugriff und dem powerapps-Portal? 
Canvas-apps ermöglichen das Erstellen einer APP, die auf das Digitalisieren von Geschäftsprozessen zugeschnitten ist, ohne Code in einer herkömmlichen C#Programmiersprache wie zu schreiben. Der Gast Zugriff für Canvas-Apps ermöglicht Teams von Personen, die aus verschiedenen Organisationen bestehen, die an einem gemeinsamen Geschäftsprozess teilnehmen, um auf die gleichen App-Ressourcen zuzugreifen, die in eine [Vielzahl von Microsoft-und Drittanbieter Quellen](https://docs.microsoft.com/en-us/powerapps/maker/canvas-apps/connections-list)integriert werden können.

[Powerapps-Portale](https://docs.microsoft.com/en-us/powerapps/maker/portals/overview) bieten die Möglichkeit, Anwendungen mit geringem Code und reaktionsfähigen Websites zu erstellen, mit denen externe Benutzer mit den im Common Data Service gespeicherten Daten interagieren können. Dadurch können Unternehmen Websites erstellen, die entweder anonym oder über den Anmelde Anbieter Ihrer Wahl (z. b. LinkedIn, Microsoft-Konto, andere kommerzielle Anmelde Anbieter) für Benutzer außerhalb Ihrer Organisation freigegeben werden können. 

In der folgenden Tabelle werden einige grundlegende Unterschiede zwischen powerapps-Portalen und Canvas-apps erläutert.  

| | Interface | Authentifizierung | Barrierefreie Datenquellen |
|------|--------|----------|-------------------|
| Powerapps-Portale | Nur Browser | Ermöglicht anonymen und authentifizierten Zugriff | Common Data Service |
| Canvas-Apps | Browser und Mobile Apps | Erfordert die Authentifizierung über Azure AD | Alle ~ 150 out-of-Box-Connectors und alle benutzerdefinierten Connectors  |
||

#### <a name="can-guests-access-customized-forms-in-sharepoint"></a>Können Gäste auf angepasste Formulare in SharePoint zugreifen?
Ja. Jeder Benutzer, der auf eine SharePoint-Liste mit einem angepassten Formular zugreifen kann, kann Elemente in der Liste mit dem Formular ohne powerapps-Lizenz erstellen und bearbeiten.

#### <a name="can-guests-access-apps-embedded-in-sharepoint"></a>Können Gäste auf in SharePoint eingebettete apps zugreifen? 
Ja. Der Zugriff auf eigenständige Canvas-apps erfordert jedoch eine powerapps-Lizenz einschließlich eingebetteter apps. Beim Einbetten einer Canvas-app in SharePoint über das Microsoft PowerApps Einbettungs Steuerelement kopieren-fügen Sie die APP-ID ein. 

![Einbinden der Canvas-app in SharePoint für Gäste](media/share-app/guest_access_doc_5.PNG)

Wenn Sie eine Canvas-app in SharePoint über das IFRAME-HTML-Tag einbetten, verweisen Sie auf die APP, indem Sie http://make.powerapps.com den vollständigen Weblink verwenden, den Sie in > eine APP > Details > Weblink auswählen können.

![Details der Canvas-App](media/share-app/guest_access_doc_6.PNG)

#### <a name="how-come-guests-can-launch-the-app-shared-with-them-but-connections-fail-to-be-created"></a>Wie kommt es zu den Gast-apps, die für Sie freigegeben sind, aber keine Verbindungen erstellt werden?
Wie bei nicht-Gästen müssen auch die zugrunde liegenden Datenquellen, auf die die APP zugreift, für den Gast zugänglich gemacht werden.

#### <a name="what-license-must-be-assigned-to-my-guest-so-they-can-run-an-app-shared-with-them"></a>Welche Lizenz muss meinem Gast zugewiesen werden, damit Sie eine APP ausführen können, die für Sie freigegeben ist?
Die gleiche Lizenz, die für nicht-Gäste zum Ausführen einer APP erforderlich ist. Wenn die APP beispielsweise keine Premium-Verbindungsdienste verwendet, genügt eine powerapps P1-Lizenz, um dem Gast zugewiesen zu werden.  

Vor der allgemeinen Verfügbarkeit des Canvas-App-Gast Zugriffs müssen Gäste mit einer powerapps-Lizenz in Ihrem Privat Mandanten keine Lizenz in dem Mandanten zugewiesen werden, der als Gastbenutzer angemeldet ist.

|                                 | Angepasste SharePoint-Form | Eigenständige Canvas-App mit nicht-Premium-Connectors | Eigenständige Canvas-App mit Premium-Connectors | Modell gestützte App |
|---------------------------------|----------------------------|----------------------------------------------------|------------------------------------------------|------------------|
| SharePoint-Benutzer (keine PA-Lizenz) | w                          |                                                    |                                                |                  |
| In powerapps enthaltene e/As    | w                          |                                                    |                                                |                  |
| Powerapps-Plan 1                | w                          | w                                                  |                                                |                  |
| Powerapps Plan2                 | w                          | w                                                  | w                                              | w                |

#### <a name="in-powerapps-mobile-how-does-a-guest-see-apps-for-their-home-tenant"></a>Wie wird in powerapps Mobile für einen Gast Apps für seinen Heim Mandanten angezeigt?
Alle Benutzer, die auf eine Canvas-App auf Ihrem mobilen Gerät zugegriffen haben und die in einem Azure AD Mandanten veröffentlicht werden, der nicht Ihr Privat Mandant ist, müssen sich von powerapps abmelden und sich bei powerapps Mobile wieder anmelden.  

Vor der allgemeinen Verfügbarkeit des Canvas-App-Gast Zugriffs ermöglicht die Auswahl einer Organisation dem Benutzer das Ändern des Azure AD Mandanten, bei dem Sie angemeldet sind, ohne explizit von der App abgemeldet zu werden.  

#### <a name="must-a-guest-accept-the-azure-ad-guest-invitation-prior-to-sharing-an-app-with-the-guest"></a>Muss ein Gast die Azure AD Guest-Einladung annehmen, bevor er eine APP für den Gast freigibt?
Nein. Wenn ein Gast eine APP startet, die für ihn freigegeben wurde, bevor er eine Gast Einladung annimmt, wird der Gast aufgefordert, die Einladung im Rahmen der Anmelde Erfahrung beim Starten der APP zu akzeptieren.  

#### <a name="what-azure-ad-tenant-are-connections-for-a-guest-user-created-in"></a>Welche Azure AD Mandanten sind Verbindungen für einen in erstellten Gastbenutzer?
Verbindungen für eine APP werden immer im Kontext des Azure AD Mandanten hergestellt, dem die APP zugeordnet ist. Wenn z. b. eine APP im Mandanten von "Configuration Manager" erstellt wird, werden Verbindungen für interne und Gastbenutzer von "Configuration Manager" im Kontext des Mandanten von "Configuration Manager" hergestellt.

#### <a name="can-guests-use-microsoft-graph-via-microsoft-security-graph-connectorhttpsdocsmicrosoftcomen-usconnectorsmicrosoftgraphsecurity-or-a-custom-connector-using-microsoft-graph-apishttpsdevelopermicrosoftcomen-usgraph"></a>Können Gäste Microsoft Graph über den [Microsoft Security Graph-Connector](https://docs.microsoft.com/en-us/connectors/microsoftgraphsecurity/) oder einen benutzerdefinierten Connector mithilfe von [Microsoft Graph-APIs](https://developer.microsoft.com/en-us/graph)verwenden?
Nein, Azure AD Gäste können Microsoft Graph nicht Abfragen, um Informationen für einen Mandanten abzurufen, bei dem es sich um einen Gast handelt.

#### <a name="what-intune-policies-apply-to-guests-using-my-powerapps"></a>Welche InTune-Richtlinien gelten für Gäste, die meine powerapps verwenden?
InTune wendet nur Richtlinien des Privat Mandanten eines Benutzers an. Wenn beispielsweise eine Alice@Contoso.com App mit Vikram@Fabrikam.comfreigibt, wendet InTune weiterhin fabrikam.com-Richtlinien auf dem Gerät von virkam an, unabhängig von den ausgeführten powerapps.

#### <a name="what-connectors-support-guest-access"></a>Welche Connectors unterstützen den Gast Zugriff?
Alle Connectors, die keine Azure AD Authentifizierung eines Typs ausführen, unterstützen den Gast Zugriff. In der folgenden Tabelle werden alle Connectors aufgelistet, die Azure AD Authentifizierung durchführen und welche Connectors derzeit den Gast Zugriff unterstützen. Viele dieser Updates werden aktualisiert, was zu allgemeiner Verfügbarkeit führt.

| **Stecker**                                     | **Unterstützt Gast Zugriff**                                              |
|---------------------------------------------------|------------------------------------------------------------------------|
| 10to8 Appointment Scheduling                      | Nein                                                                     |
| Adobe Creative Cloud                              | Nein                                                                     |
| Adobe Sign                                        | Nein                                                                     |
| Asana                                             | Nein                                                                     |
| Atbot-Administrator                                       | Nein                                                                     |
| Atbot-Logik                                       | Nein                                                                     |
| Azure AD                                          | Ja                                                                    |
| Azure Automation                                  | Ja                                                                    |
| Azure-Container Instanz                          | Ja                                                                    |
| Azure Data Factory                                | Ja                                                                    |
| Azure Data Lake                                   | Ja                                                                    |
| Azure devops                                      | Nein                                                                     |
| Azure Event Grid                                  | Nein                                                                     |
| Azure-IOT Central                                 | Ja                                                                    |
| Azure Key Vault                                   | Nein                                                                     |
| Azure-Kusto                                       | Ja                                                                    |
| Azure Log Analytics                               | Ja                                                                    |
| Azure Resource Manager                            | Ja                                                                    |
| Basecamp 2                                        | Nein                                                                     |
| Bitbucket                                         | Nein                                                                     |
| Bitly                                             | Nein                                                                     |
| bttn                                              | Nein                                                                     |
| Buffer                                            | Nein                                                                     |
| Business Central                                  | Nein                                                                     |
| Candidatezip                                      | Nein                                                                     |
| Capsule CRM                                       | Nein                                                                     |
| Cloud-PKI-Verwaltung                              | Nein                                                                     |
| Cognito Forms                                     | Nein                                                                     |
| Common Data Service                               | Nein                                                                     |
| Common Data Service (Legacy)                      | Nein                                                                     |
| D & B-Optimierer                                     | Nein                                                                     |
| Derdack SIGNL4                                    | Nein                                                                     |
| Disqus                                            | Nein                                                                     |
| Dokument Zusammenführung                                    | Nein                                                                     |
| Dynamics 365                                      | Nein                                                                     |
| Dynamics 365 AI für Vertrieb                         | Ja                                                                    |
| Dynamics 365 for FIN & OPS                        | Nein                                                                     |
| Enadoc My Workspace                                            | Nein                                                                     |
| Eventbrite                                        | Nein                                                                     |
| Excel Online (Business)                           | Nein                                                                     |
| Excel Online (onedrive)                           | Nein                                                                     |
| Ablauf Erinnerung                               | Nein                                                                     |
| FreshBooks                                        | Nein                                                                     |
| GoToMeeting                                       | Nein                                                                     |
| GoToTraining                                      | Nein                                                                     |
| GoToWebinar                                       | Nein                                                                     |
| Harvest                                           | Nein                                                                     |
| HTTP mit Azure AD                                | Nein                                                                     |
| Infusionsoft                                      | Nein                                                                     |
| Inoreader                                         | Nein                                                                     |
| Intercom                                          | Nein                                                                     |
| JotForm                                           | Nein                                                                     |
| kintone                                           | Nein                                                                     |
| Zuzugreifen                                          | Nein                                                                     |
| Marketing-inhaltshub                             | Nein                                                                     |
| Mittel                                            | Nein                                                                     |
| Metatask                                          | Nein                                                                     |
| Microsoft Forms                                   | Nein                                                                     |
| Microsoft Forms pro                               | Nein                                                                     |
| Microsoft Graph Sicherheit                          | Nein                                                                     |
| Microsoft kaizala                                 | Nein                                                                     |
| Synchronisierung von Microsoft-Schuldaten                        | Nein                                                                     |
| Microsoft StaffHub                                | Nein                                                                     |
| Microsoft Teams                                   | Ja                                                                    |
| Microsoft to-do (Business)                        | Nein                                                                     |
| Muhimbi PDF                                       | Nein                                                                     |
| NetDocuments                                      | Nein                                                                     |
| Office 365-Gruppen                                 | Ja                                                                    |
| Office 365 Outlook                                | Nein                                                                     |
| Office 365-Benutzer                                  | Ja                                                                    |
| Office 365 Video                                  | Nein                                                                     |
| OneDrive                                          | Nein                                                                     |
| OneDrive for Business                             | Nein                                                                     |
| OneNote (Business)                                | Nein                                                                     |
| Outlook Customer Manager                          | Nein                                                                     |
| Outlook-Aufgaben                                     | Ja                                                                    |
| Outlook.com                                       | Nein                                                                     |
| Paylocity                                         | Nein                                                                     |
| Planner                                           | Nein                                                                     |
| Plumsail-Formulare                                    | Nein                                                                     |
| Power BI                                          | Ja                                                                    |
| Project Online                                    | Nein                                                                     |
| ProjectWise-Design Integration                    | Nein                                                                     |
| ProjectWise-Freigabe                                 | Nein                                                                     |
| SharePoint                                        | Ja                                                                    |
| Signnow                                           | Nein                                                                     |
| Skype for Business Online                         | Nein                                                                     |
| Soft1                                             | Nein                                                                     |
| Stormboard                                        | Nein                                                                     |
| Survey123                                         | Nein                                                                     |
| SurveyMonkey                                      | Nein                                                                     |
| Toodledo                                          | Nein                                                                     |
| Typeform                                          | Nein                                                                     |
| Vimeo                                             | Nein                                                                     |
| WebEx-Teams                                       | Nein                                                                     |
| Windows Defender Advanced Threat Protection (ATP) | Nein                                                                     |
| Word Online (Business)                            | Nein                                                                     |
