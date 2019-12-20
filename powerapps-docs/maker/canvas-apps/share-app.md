---
title: Freigeben einer Canvas-App | Microsoft-Dokumentation
description: Geben Sie Ihre Canvas-App frei, indem Sie anderen Benutzern die Berechtigung erteilen, die App auszuführen oder zu ändern.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 12/18/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 75157ecd3921476d7b527dfc5b87b0efbd308f71
ms.sourcegitcommit: 212bd841595db0d6f41002f7ff9a1c8eb33a0724
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75203971"
---
# <a name="share-a-canvas-app-in-power-apps"></a>Freigeben einer Canvas-app in Power apps

Nachdem Sie eine Canvas-App erstellt haben, die eine geschäftliche Anforderung behandelt, geben Sie an, welche Benutzer in Ihrer Organisation die App ausführen dürfen und welche sie ändern oder sogar erneut freigeben dürfen. Geben Sie jeden Benutzer anhand seines Namens an, oder geben Sie eine Sicherheitsgruppe in Azure Active Directory an. Wenn jeder von Ihrer App profitieren würde, geben Sie an, dass Ihre gesamte Organisation diese ausführen darf.

> [!IMPORTANT]
> Damit eine freigegebene App erwartungsgemäß funktioniert, müssen Sie auch Berechtigungen für die Datenquelle oder die Quellen verwalten, auf denen die APP basiert, z. b. [Common Data Service](#common-data-service) oder [Excel](share-app-data.md). Sie müssen möglicherweise auch [andere Ressourcen freigeben](share-app-resources.md), von denen die App abhängt, z.B. Flows, Gateways oder Verbindungen.

## <a name="prerequisites"></a>Voraussetzungen

Um eine App freizugeben, müssen Sie sie in der Cloud speichern (nicht lokal) und dann veröffentlichen.

- Geben Sie Ihrer App einen aussagekräftigen Namen und eine klare Beschreibung, damit Benutzer wissen, was die App bewirkt und sie so leicht in einer Liste finden können. Wählen Sie im Menü **Datei** in Power apps Studio **App-Einstellungen**aus, geben Sie einen Namen an, und geben Sie eine Beschreibung ein, oder fügen Sie Sie ein.

- Wenn Sie Änderungen vornehmen, müssen Sie die App speichern und erneut veröffentlichen, wenn andere Personen diese Änderungen sehen sollen.

## <a name="share-an-app"></a>Eine App freigeben

1. [Melden](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) Sie sich bei powerapps an, und wählen Sie dann am linken Rand die Option **apps** aus.

    ![Anzeigen der App-Liste](./media/share-app/file-apps.png)

1. Wählen Sie die APP aus, die Sie freigeben möchten, indem Sie das zugehörige Symbol auswählen.

    ![App auswählen](./media/share-app/select-app.png)

1. Wählen Sie im Banner die Option **Freigeben**aus.

    ![Geöffneter Bildschirm „Freigeben“](./media/share-app/banner-share.png)

1. Geben Sie die Benutzer oder Sicherheitsgruppen in Azure Active Directory, mit denen Sie die APP freigeben möchten, nach Namen oder Aliasnamen an.

    - Um ihrer gesamten Organisation das Ausführen der APP zu gestatten (ohne Sie zu ändern oder freizugeben), geben Sie im Freigabe Bereich **alle** ein.
    - Wenn die Elemente durch Semikolons voneinander getrennt sind, können Sie eine APP mit einer Liste von Aliasen, anzeigen Amen oder einer Kombination aus diesen Teilen (z. b. **Jane Doe &lt;jane.doe@contoso.com**). Wenn mehr als eine Person denselben Namen, aber unterschiedliche Aliase hat, wird die erste gefundene Person zur Liste hinzugefügt. Eine QuickInfo wird angezeigt, wenn ein Name oder Alias bereits über eine Berechtigung verfügt oder nicht aufgelöst werden kann. 

    ![Angeben von Benutzern und Mitbesitzern](./media/share-app/share-everyone.png)

    > [!NOTE]
    > Sie können eine APP nicht für eine Verteiler Gruppe in Ihrer Organisation oder für eine Gruppe außerhalb Ihrer Organisation freigeben.

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

    Alle Benutzer, für die Sie die APP freigegeben haben, können Sie in Power Apps Mobile auf einem mobilen Gerät oder in appsource auf [Dynamics 365](https://home.dynamics.com) in einem Browser ausführen. Mitbesitzer können die app in [powerapps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)bearbeiten und freigeben.

    Wenn Sie eine e-Mail-Einladung gesendet haben, kann jede Person, für die Sie die APP freigegeben haben, Sie ausführen, indem Sie einen Link in der Einladung

    - Wenn ein Benutzer den Link auf einem mobilen Gerät auswählt, wird die app in powerapps Mobile geöffnet.
    - Wenn ein Benutzer den Link auf einem Desktop Computer auswählt, wird die app in einem Browser geöffnet.

    Mitbesitzer, die eine Einladung erhalten, erhalten einen weiteren Link, mit dem die APP für die Bearbeitung in Power apps Studio geöffnet wird.

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
     > [!div class="mx-imgBorder"] 
     > ![Sicherheitsrollen Liste](media/share-app/cds-assign-security-role-list.png "Sicherheitsrollen Liste")

### <a name="common-data-service-previous-version"></a>Common Data Service (vorherige Version)

Wenn Sie eine APP freigeben, die auf einer älteren Version von Common Data Service basiert, müssen Sie die Lauf Zeit Berechtigung separat für den Dienst freigeben. Wenn Sie nicht über die entsprechende Berechtigung verfügen, finden Sie weitere Informationen unter Administrator der Umgebung.

## <a name="share-with-guests"></a>Mit Gästen teilen
 
Canvas-Apps für Power Apps können für Gastbenutzer eines Azure Active Directory Mandanten freigegeben werden. Dadurch können externe Geschäftspartner, Auftragnehmer und Drittanbieter zum Ausführen der Canvas-apps Ihres Unternehmens eingeladen werden. 

> [!NOTE]
> Gästen darf nur die **Benutzer** Rolle und nicht die **Mitbesitzer** Rolle für apps zugewiesen werden, die für Sie freigegeben wurden.

### <a name="prerequisites"></a>Voraussetzungen
- Aktivieren Sie in Azure Active Directory (Azure AD) die externe B2B-Zusammenarbeit für den Mandanten. Weitere Informationen: [Aktivieren der externen B2B-Zusammenarbeit und Verwalten von Gästen, die Gäste einladen dürfen](/azure/active-directory/b2b/delegate-invitations)
    - Aktivieren der externen B2B-Zusammenarbeit ist standardmäßig aktiviert. Die Einstellungen können jedoch von einem Mandanten Administrator geändert werden.  Weitere Informationen zu Azure AD B2B finden Sie unter [Was ist der Gastbenutzer Zugriff in Azure AD B2B?](/azure/active-directory/b2b/what-is-b2b)  
- Zugriff auf ein Konto, das Gastbenutzer zu einem Azure AD-Mandanten hinzufügen kann. Administratoren und Benutzer mit der Rolle "Gast einladter" können einem Mandanten Gäste hinzufügen.   
- Der Gastbenutzer muss über eine Lizenz für powerapps-Rechte verfügen, die mit der Funktion der APP übereinstimmt, die über einen der folgenden Mandanten zugewiesen wurde:
    - Der Mandant, der die freigegebene App gehostet.
    - Der privat Mandant des Gast Benutzers.

> [!NOTE]
> Powerapps pro App-Pläne sind auf apps in einer bestimmten Umgebung beschränkt, sodass Sie nicht Mandanten übergreifend erkannt werden können. In Office und powerapps pro Benutzer Plänen enthaltene Power apps sind nicht an eine bestimmte Umgebung gebunden, sodass Sie Mandanten übergreifend in Gast Szenarien erkannt werden. 

### <a name="steps-to-grant-guest-access"></a>Schritte zum Gewähren des Gast Zugriffs
1. Wählen Sie **neuer Gastbenutzer** aus, um Gastbenutzer in Azure AD hinzuzufügen. Weitere Informationen: [Schnellstart: Hinzufügen eines neuen Gast Benutzers in Azure AD](/azure/active-directory/b2b/b2b-quickstart-add-guest-users-portal).
    > [!div class="mx-imgBorder"] 
    > ![Gast in Azure AD hinzufügen](media/share-app/guest_access_doc_1.png "Gast in Azure AD hinzufügen")
2. Wenn der Gastbenutzer nicht bereits über eine Lizenz in seinem privat Mandanten verfügt, weisen Sie dem Gastbenutzer eine Lizenz zu.
   - Informationen zum Zuweisen von Gastbenutzern aus admin.Microsoft.com finden Sie unter [Zuweisen von Lizenzen zu einem Benutzer](/office365/admin/subscriptions-and-billing/assign-licenses-to-users).
   - Informationen zum Zuweisen von Gastbenutzern aus Portal.Azure.com finden Sie unter [zuweisen oder Entfernen von Lizenzen](/azure/active-directory/fundamentals/license-users-groups).
 
   > [!IMPORTANT]
   > Möglicherweise müssen Sie die Microsoft 365 Admin Center-Vorschau deaktivieren, um einem Gast eine Lizenz zuzuweisen. 

3. Freigeben der Canvas-app. 
    1. Melden Sie sich bei https://make.powerapps.com an.  
    2. Wechseln Sie zu **apps**, wählen Sie eine Canvas-App aus, und wählen Sie dann in der Befehlsleiste **Freigabe**aus. 
    3. Geben Sie eine e-Mail-Adresse für einen Gastbenutzer von einem Azure AD Mandanten ein. Weitere Informationen: [Was ist der Gastbenutzer Zugriff in Azure AD B2B?](/azure/active-directory/b2b/what-is-b2b)
          > [!div class="mx-imgBorder"] 
          > ![Für Gast freigeben](media/share-app/guest_access_doc_2.png "Für Gast freigeben")
 
Nachdem Sie eine APP für den Gast Zugriff freigegeben haben, können Gäste apps, die für Sie freigegeben wurden, über die im Rahmen der Freigabe gesendete e-Mail ermitteln und darauf zugreifen.

> [!div class="mx-imgBorder"]  
> ![Gast-e-Mails für e-Mail erhalten](media/share-app/guest_access_doc_4.png "Gast-e-Mails für e-Mail erhalten")

### <a name="frequently-asked-questions"></a>Häufig gestellte Fragen

#### <a name="whats-the-difference-between-canvas-app-guest-access-and-power-apps-portals"></a>Worin besteht der Unterschied zwischen dem Canvas-App-Gast Zugriff und Power-apps-Portalen? 
Canvas-apps ermöglichen das Erstellen einer APP, die auf das Digitalisieren von Geschäftsprozessen zugeschnitten ist, ohne Code in einer herkömmlichen C#Programmiersprache wie zu schreiben. Der Gast Zugriff für Canvas-Apps ermöglicht Teams von Personen, die aus verschiedenen Organisationen bestehen, die an einem gemeinsamen Geschäftsprozess teilnehmen, um auf die gleichen App-Ressourcen zuzugreifen, die in eine Vielzahl von Microsoft-und Drittanbieter Quellen integriert werden können. Weitere Informationen finden Sie [unter Übersicht über Canvas-App-Connectors für powerapps](/powerapps/maker/canvas-apps/connections-list).

[Power apps-Portale](/powerapps/maker/portals/overview) bieten die Möglichkeit, schnelle, reaktionsschnelle Websites zu erstellen, die externen Benutzern die Interaktion mit den in Common Data Service gespeicherten Daten ermöglichen. Dadurch können Organisationen Websites erstellen, die entweder anonym oder über den Anmelde Anbieter Ihrer Wahl (z. b. LinkedIn, Microsoft-Konto oder andere kommerzielle Anmelde Anbieter) für Benutzer außerhalb Ihrer Organisation freigegeben werden können. 

In der folgenden Tabelle werden einige grundlegende Unterschiede zwischen Power apps-Portalen und Canvas-apps erläutert.  

| | Benutzeroberfläche | Authentifizierung | Barrierefreie Datenquellen |
|------|--------|----------|-------------------|
| Power apps-Portale | Nur Browser | Ermöglicht anonymen und authentifizierten Zugriff | Common Data Service |
| Canvas-Apps | Browser und Mobile Apps | Erfordert die Authentifizierung über Azure AD | Alle ~ 150 out-of-Box-Connectors und alle benutzerdefinierten Connectors  |
||

#### <a name="can-guests-access-customized-forms-in-sharepoint"></a>Können Gäste auf angepasste Formulare in SharePoint zugreifen?
Ja. Jeder Benutzer, der auf eine SharePoint-Liste mit einem angepassten Formular zugreifen kann, kann Elemente in der Liste ohne eine powerapps-Lizenz erstellen und bearbeiten.

#### <a name="can-guests-access-apps-embedded-in-sharepoint"></a>Können Gäste auf in SharePoint eingebettete apps zugreifen? 
Ja. Der Zugriff auf eigenständige Canvas-apps erfordert jedoch eine Lizenz mit powerapps-Nutzungsrechten, die der Funktion der App entsprechen, einschließlich eingebetteter apps. Geben Sie beim Einbetten einer Canvas-app in SharePoint über das Microsoft Power apps-Einbettungs Steuerelement die APP-ID ein. Geben Sie hierzu die APP-ID in das Feld **App-Weblink oder-ID** ein. 

> [!div class="mx-imgBorder"]  
> ![Einbinden der Canvas-app in SharePoint für Gäste](media/share-app/guest_access_doc_5.PNG "Einbinden der Canvas-app in SharePoint für Gäste")

Wenn Sie eine Canvas-app in SharePoint über das IFRAME-HTML-Tag einbetten, verweisen Sie mit der vollständigen Web-URL auf die app. Wenn Sie die URL suchen möchten, klicken Sie auf https://make.powerapps.com, wählen Sie eine APP aus, und wählen Sie die Registerkarte **Details** aus, und die URL wird unter **Weblink**angezeigt.

> [!div class="mx-imgBorder"]  
> ![Details der Canvas-App](media/share-app/guest_access_doc_6.PNG "Details der Canvas-App")

#### <a name="how-come-guests-can-launch-the-app-shared-with-them-but-connections-fail-to-be-created"></a>Wie kommt es zu den Gast-apps, die für Sie freigegeben sind, aber keine Verbindungen erstellt werden?
Wie bei nicht-Gästen müssen auch die zugrunde liegenden Datenquellen, auf die die APP zugreift, für den Gast zugänglich gemacht werden.

#### <a name="what-license-must-be-assigned-to-my-guest-so-they-can-run-an-app-shared-with-them"></a>Welche Lizenz muss meinem Gast zugewiesen werden, damit Sie eine APP ausführen können, die für Sie freigegeben ist?
Die gleiche Lizenz, die für nicht-Gäste zum Ausführen einer APP erforderlich ist. Wenn die APP beispielsweise Premium-Connectoren verwendet, muss dem Gast ein App-Plan vom Typ "Power apps pro app" oder "Power apps pro Benutzer" zugewiesen werden.  

|                                 | Angepasste SharePoint-Form | Eigenständige Canvas-App mit nicht-Premium-Connectors | Eigenständige Canvas-App mit Premium-Connectors | Modell gestützte App |
|---------------------------------|----------------------------|----------------------------------------------------|------------------------------------------------|------------------|
| SharePoint-Benutzer (keine PA-Lizenz) | x                          |                                                    |                                                |                  |
| In powerapps enthaltene e/As    | x                          | x                                                  |                                                |                  |
| Powerapps pro App-Plan          | x                          | x                                                  | x                                              | x                |
| Powerapps-Plan pro Benutzer         | x                          | x                                                  | x                                              | x                |

Weitere Informationen zu den Preisen und Funktionen verschiedener Pläne finden Sie im [Lizenzierungs Handbuch zu Microsoft powerapps und zur Energie Automatisierung](https://go.microsoft.com/fwlink/?linkid=2085130).

#### <a name="in-power-apps-mobile-how-does-a-guest-see-apps-for-their-home-tenant"></a>Wie wird in Power Apps Mobile für einen Gast Apps für seinen Heim Mandanten angezeigt?
Alle Benutzer, die auf eine Canvas-App auf Ihrem mobilen Gerät zugegriffen haben und die in einem Azure AD Mandanten veröffentlicht werden, der nicht Ihr Privat Mandant ist, müssen sich bei Power apps abmelden und sich wieder bei Power Apps Mobile anmelden.  

#### <a name="must-a-guest-accept-the-azure-ad-guest-invitation-prior-to-sharing-an-app-with-the-guest"></a>Muss ein Gast die Azure AD Guest-Einladung annehmen, bevor er eine APP für den Gast freigibt?
Nein. Wenn ein Gast eine APP startet, die für ihn freigegeben wurde, bevor er eine Gast Einladung annimmt, wird der Gast aufgefordert, die Einladung im Rahmen der Anmelde Erfahrung beim Starten der APP zu akzeptieren.  

#### <a name="what-azure-ad-tenant-are-connections-for-a-guest-user-created-in"></a>Welche Azure AD Mandanten sind Verbindungen für einen in erstellten Gastbenutzer?
Verbindungen für eine APP werden immer im Kontext des Azure AD Mandanten hergestellt, dem die APP zugeordnet ist. Wenn z. b. eine APP im Mandanten von "Configuration Manager" erstellt wird, werden Verbindungen für interne und Gastbenutzer von "Configuration Manager" im Kontext des Mandanten von "Configuration Manager" hergestellt.

#### <a name="can-guests-use-microsoft-graph-via-microsoft-security-graph-connector-or-a-custom-connector-using-microsoft-graph-apis"></a>Können Gäste Microsoft Graph über den Microsoft Security Graph-Connector oder einen benutzerdefinierten Connector mithilfe von Microsoft Graph-APIs verwenden?
Nein, Azure AD Gäste können Microsoft Graph nicht Abfragen, um Informationen für einen Mandanten abzurufen, bei dem es sich um einen Gast handelt.

#### <a name="what-intune-policies-apply-to-guests-using-my-power-apps"></a>Welche InTune-Richtlinien gelten für Gäste, die meine Power Apps verwenden?
InTune wendet nur Richtlinien des Privat Mandanten eines Benutzers an. Wenn Alice@Contoso.com beispielsweise eine APP mit Vikram@Fabrikam.comgemeinsam nutzt, wendet InTune unabhängig von den ausgeführten powerapps weiterhin fabrikam.com-Richtlinien auf virkam-Geräten an.

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
