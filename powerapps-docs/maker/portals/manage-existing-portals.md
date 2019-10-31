---
title: Verwaltung bestehender Portale in PowerApps | Microsoft Docs
description: Anleitung zur Verwaltung eines Portale in PowerApps.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 07/18/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="manage-existing-portals-in-powerapps"></a>Verwaltung bestehender Portale in PowerApps.

[!include[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Sobald Sie ein Portal erstellt haben, ist es unter dem Abschnitt **Aktuelle Anwendungen** auf der Startseite PowerApps sichtbar.

> [!div class=mx-imgBorder]
> ![neueste Apps](media/recent-apps.png "neueste Apps")  

Um eine App zu verwalten, wählen Sie **Weitere Befehle** (**...**) für das Portal und wählen Sie eine Aktion aus dem Kontextmenü.

> [!div class=mx-imgBorder]
> ![Portal-App-Optionen](media/portal-app-options.png "Portal-App-Optionen")  

## <a name="edit"></a>Bearbeiten

Öffnet den [Portaldesigner](portal-designer-anatomy.md), um die Inhalte und Komponenten des Portale zu bearbeiten.  

> [!div class=mx-imgBorder]
> ![Portalersteller](media/portal-maker.png "Portalersteller")  

## <a name="browse"></a>Durchsuchen

Öffnet das Portal, um die Website zu durchsuchen. Dies hilft Ihnen, das Portal so zu sehen, wie es für Ihre Kunden aussieht.

> [!div class=mx-imgBorder]
> ![Portalwebsite](media/portal-website.png "Portalwebsite")  

Alternativ können Sie auch das Portal öffnen, um die Website zu durchsuchen, indem Sie **Website durchsuchen** im [Portaldesigner](portal-designer-anatomy.md) wählen, um die Änderungen anzuzeigen, die Sie an der Website vorgenommen haben. Die Website wird in einem neuen Tab mit der URL der Website geöffnet.

## <a name="share"></a>Freigeben

Teilen Sie Ihr Portal mit internen oder externen Benutzern. Befolgen Sie die im Bereich **Freigeben dieses Portale** genannten Schritte.

> [!div class=mx-imgBorder]
> ![Portal teilen](media/share-portal.png "Portal teilen")  

### <a name="share-with-internal-users"></a>Teilen mit internen Benutzern

Um das Portal für interne Benutzer freizugeben, müssen Sie zunächst eine Sicherheitsrolle anlegen und dann Benutzer der Sicherheitsrolle zuordnen, damit sie das Portal nutzen können.

> [!NOTE]
> Wenn Sie als Benutzer unter Common Data Service keine entsprechenden Berechtigungen für Portalentitäten haben, werden Sie möglicherweise Fehler wie "Sie haben keinen Zugriff, um Lösungen in dieser Umgebung anzuzeigen" sehen. oder "Sie haben keinen Zugriff auf die Website in dieser Umgebung". Für diese Vorschau wird empfohlen, dass Sie sich entweder in einer **Systemadministrator** oder zumindest in einer **Systemanpasser** Sicherheitsrolle in der entsprechenden Common Data Service Datenbank befinden.

#### <a name="step-1-create-a-security-role"></a>Schritt 1: Erstellen einer Sicherheitsrolle

1.  Wählen Sie im Bereich **Dieses Portal teilen** unter **Eine Sicherheitsrolle erstellen** **Sicherheitsrollen**. Eine Liste aller konfigurierten Sicherheitsrollen wird angezeigt.

2.  Wählen Sie auf der Aktionssymbolleiste **Neu** aus.

3.  Geben Sie im Fenster **Neue Sicherheitsrolle** den Rollennamen ein.

4.  Legen Sie die Berechtigungen für alle in Ihrem Portal verwendeten Objekte fest.

5.  Wenn Sie die Konfiguration der Sicherheitsrolle abgeschlossen haben, wählen Sie in der Symbolleiste **Speichern und Schließen**.

Informationen zu Sicherheitsrollen und -privilegien finden Sie unter [Sicherheitsrollen und -privilegien](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/admin/security-roles-privileges).  

#### <a name="step-2-assign-users-to-the-security-role"></a>Schritt 2: Benutzer der Sicherheitsrolle zuordnen

1.  Wählen Sie im Bereich **Dieses Portal teilen** unter **Benutzer der Sicherheitsrolle zuweisen** **Benutzer**. Sie erhalten eine Liste aller Benutzer.

2.  Wählen Sie den Benutzer aus, dem Sie eine Sicherheitsrolle zuordnen möchten.

3.  Wählen Sie **Rollen verwalten** aus.

    > [!NOTE]
    > Wenn Sie die Schaltfläche **Rollen verwalten** in der Befehlsleiste nicht sehen können, müssen Sie den Client ändern, indem Sie forceUCI in der URL auf 0 setzen. Zum Beispiel https://&lt;org\_url&gt;/main.aspx?pagetype=entitylist&etn=systemuser&forceUCI=0

4.  Wählen Sie im Dialogfenster **Benutzerrollen verwalten** die zuvor erstellte Sicherheitsrolle aus und wählen Sie dann **OK**.

### <a name="share-with-external-users"></a>Teilen mit externen Benutzern

Ihr Portal sollte anonym arbeiten und für die externen Benutzer zugänglich sein. Wenn Sie erweiterte Funktionen zur Verwaltung von Rollen und Berechtigungen für externe Benutzer ausprobieren möchten, siehe [Konfiguration eines Kontakts für die Verwendung in einem Portal](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/configure-contacts), [Kontakte zu Ihren Portalen einladen](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/invite-contacts), [Webrollen für Portale erstellen](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/create-web-roles), [Entitätsberechtigungen zuweisen](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/assign-entity-permissions).  

## <a name="settings"></a>Einstellungen

Zeigt die Portaleinstellungen an und ermöglicht es Ihnen, den Namen des Portale zu ändern. Sie können auch erweiterte Aktionen durchführen, wie z.B. die Verwaltung des Portale über das Portal Admin Center und die Arbeit mit den Site-Einstellungen. Einstellungen bietet Links zum PowerApps Portale Admin-Center und zu den Seiteneinstellungen. Mehr Informationen: [Verwalten Sie Ihr Portal](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/manage-portal) und [Konfigurieren Sie die Seiteneinstellungen für Portale](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/configure-site-settings).  

> [!div class=mx-imgBorder]
> ![Portaleinstellungen](media/portal-settings.png "Portaleinstellungen")  

## <a name="delete"></a>Löschen

Löscht das Portal und die bereitgestellten Ressourcen. Wenn Sie ein Portal löschen, wird seine URL unzugänglich. Das Löschen eines Portale hat keinen Einfluss auf die in Ihrer Umgebung vorhandenen Portalkonfigurationen oder Lösungen, und sie bleiben wie sie sind.
Sie müssen die Portalkonfigurationen manuell löschen, um Portalkonfigurationen vollständig aus Ihrer Umgebung zu entfernen. Verwenden Sie dazu die Anwendung Portal Management und löschen Sie den entsprechenden Website-Datensatz für das Portal.

> [!NOTE]
> Wenn Sie nicht über ausreichende Berechtigungen zum Löschen eines Portale verfügen, wird ein Fehler angezeigt. Sie müssen über die Rolle Systemanpasser oder Systemadministrator verfügen, um ein Portal zu löschen. Außerdem müssen Sie der Eigentümer der Portalanwendung in Azure Active Directory sein. Der Benutzer, der das Portal anlegt, ist standardmäßig der Eigentümer und kann ein Portal löschen. Informationen zum Hinzufügen von sich selbst als Eigentümer finden Sie unter [Sich selbst als Eigentümer der Anwendung Azure AD hinzufügen](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/manage-portal#to-add-yourself-as-an-owner-of-the-azure-ad-application).

## <a name="details"></a>Details

Zeigt Details wie den Eigentümer des Portale, Datum und Uhrzeit der Erstellung und letzten Änderung sowie die URL des Portale an.

> [!div class=mx-imgBorder]
> ![Portaldetails](media/portal-details.png "Portaldetails")  

