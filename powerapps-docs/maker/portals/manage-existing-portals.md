---
title: Verwaltung bestehender Portale in Power Apps | Microsoft Docs
description: Anleitung zur Verwaltung eines Portale in Power Apps.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 3eea977cf59629c7f2b758affa145f520838b39f
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "3125307"
---
# <a name="manage-existing-portals-in-power-apps"></a>Verwaltung bestehender Portale in Power Apps.

Sobald Sie ein Portal erstellt haben, ist es unter dem Abschnitt **Aktuelle Anwendungen** auf der Startseite Power Apps sichtbar.

> [!div class=mx-imgBorder]
> ![neueste Apps](media/recent-apps.png "Neueste Apps")  

Um eine App zu verwalten, wählen Sie **Weitere Befehle** (**...**) für das Portal und wählen Sie eine Aktion aus dem Kontextmenü.

> [!div class=mx-imgBorder]
> ![Portal-App-Optionen](media/portal-app-options.png "Portal-App-Optionen")  

## <a name="edit"></a>Bearbeiten

Öffnet das [Power Apps-Portalstudio](portal-designer-anatomy.md), um die Inhalte und Komponenten des Portals zu bearbeiten.  

> [!div class=mx-imgBorder]
> ![Portalersteller](media/portal-maker.png "Portalersteller")  

## <a name="browse"></a>Durchsuchen

Öffnet das Portal, um die Website zu durchsuchen. Dies hilft Ihnen, das Portal so zu sehen, wie es für Ihre Kunden aussieht.

> [!div class=mx-imgBorder]
> ![Portalwebsite](media/portal-website.png "Portalwebsite")  

Alternativ können Sie auch das Portal öffnen, um die Website zu durchsuchen, indem Sie **Website durchsuchen** im [Power Apps-Portalstudio](portal-designer-anatomy.md) auswählen, um die Änderungen anzuzeigen, die Sie an der Website vorgenommen haben. Die Website wird in einem neuen Tab mit der URL der Website geöffnet.

## <a name="share"></a>Freigeben

Teilen Sie Ihr Portal mit internen oder externen Benutzern. Befolgen Sie die im Bereich **Freigeben dieses Portale** genannten Schritte.

> [!div class=mx-imgBorder]
> ![Portal teilen](media/share-portal.png "Portal teilen")  

### <a name="share-with-internal-users"></a>Teilen mit internen Benutzern

Um das Portal für interne Benutzer freizugeben, müssen Sie zunächst eine Sicherheitsrolle anlegen und dann Benutzer der Sicherheitsrolle zuordnen, damit sie das Portal nutzen können.

> [!NOTE]
> Wenn Sie als Benutzer unter Common Data Service keine entsprechenden Berechtigungen für Portalentitäten haben, werden Sie möglicherweise Fehler wie "Sie haben keinen Zugriff, um Lösungen in dieser Umgebung anzuzeigen" sehen. oder "Sie haben keinen Zugriff auf die Website in dieser Umgebung". Es wird empfohlen, dass Sie in der entsprechenden Common Data Service-Datenbank über die Systemadministrator-Sicherheitsrolle verfügen.

#### <a name="step-1-create-a-security-role"></a>Schritt 1: Erstellen einer Sicherheitsrolle

1.  Wählen Sie im Bereich **Dieses Portal teilen** unter **Eine Sicherheitsrolle erstellen** **Sicherheitsrollen**. Eine Liste aller konfigurierten Sicherheitsrollen wird angezeigt.

2.  Wählen Sie auf der Aktionssymbolleiste **Neu** aus.

3.  Geben Sie im Fenster **Neue Sicherheitsrolle** den Rollennamen ein.

4.  Legen Sie die Berechtigungen für alle in Ihrem Portal verwendeten Objekte fest.

5.  Wenn Sie die Konfiguration der Sicherheitsrolle abgeschlossen haben, wählen Sie in der Symbolleiste **Speichern und Schließen**.

Informationen zu Sicherheitsrollen und -privilegien finden Sie unter [Sicherheitsrollen und -privilegien](https://docs.microsoft.com/power-platform/admin/security-roles-privileges).

#### <a name="step-2-assign-users-to-the-security-role"></a>Schritt 2: Benutzer der Sicherheitsrolle zuordnen

1.  Wählen Sie im Bereich **Dieses Portal teilen** unter **Benutzer der Sicherheitsrolle zuweisen** **Benutzer**. Sie erhalten eine Liste aller Benutzer.

2.  Wählen Sie den Benutzer aus, dem Sie eine Sicherheitsrolle zuordnen möchten.

3.  Wählen Sie **Rollen verwalten** aus.

    > [!NOTE]
    > Wenn Sie die Schaltfläche **Rollen verwalten** in der Befehlsleiste nicht sehen können, müssen Sie den Client ändern, indem Sie forceUCI in der URL auf 0 setzen. Zum Beispiel https://&lt;org\_url&gt;/main.aspx?pagetype=entitylist&etn=systemuser&forceUCI=0

4.  Wählen Sie im Dialogfenster **Benutzerrollen verwalten** die zuvor erstellte Sicherheitsrolle aus und wählen Sie dann **OK**.

### <a name="share-with-external-users"></a>Teilen mit externen Benutzern

Ihr Portal sollte anonym arbeiten und für die externen Benutzer zugänglich sein. Wenn Sie erweiterte Funktionen zur Verwaltung von Rollen und Berechtigungen für externe Benutzer ausprobieren möchten, siehe [Konfiguration eines Kontakts für die Verwendung in einem Portal](configure/configure-contacts.md), [Kontakte zu Ihren Portalen einladen](configure/invite-contacts.md), [Webrollen für Portale erstellen](configure/create-web-roles.md), [Entitätsberechtigungen zuweisen](configure/assign-entity-permissions.md).  

## <a name="settings"></a>Einstellungen

Zeigt die Portaleinstellungen an und ermöglicht es Ihnen, den Namen des Portale zu ändern. Sie können auch erweiterte Aktionen durchführen, wie z. B. die Verwaltung des Portals über das Power Apps-Portal-Administratorcenter und die Arbeit mit den Site-Einstellungen. Einstellungen bietet Links zum Power Apps Portale Admin-Center und zu den Seiteneinstellungen. Mehr Informationen: [Erweiterte Portalverwaltung](admin/admin-overview.md) und [Konfigurieren von Websiteeinstellungen](configure/configure-site-settings.md).  

> [!div class=mx-imgBorder]
> ![Portaleinstellungen](media/portal-settings.png "Portaleinstellungen")  

## <a name="delete"></a>Löschen

Löscht das Portal und die bereitgestellten Ressourcen. Wenn Sie ein Portal löschen, wird seine URL unzugänglich. Das Löschen eines Portale hat keinen Einfluss auf die in Ihrer Umgebung vorhandenen Portalkonfigurationen oder Lösungen, und sie bleiben wie sie sind.
Sie müssen die Portalkonfigurationen manuell löschen, um Portalkonfigurationen vollständig aus Ihrer Umgebung zu entfernen. Verwenden Sie dazu die Anwendung Portal Management und löschen Sie den entsprechenden Website-Datensatz für das Portal.

> [!NOTE]
> Wenn Sie nicht über ausreichende Berechtigungen zum Löschen eines Portale verfügen, wird ein Fehler angezeigt. Sie müssen über die Systemadministrator-Rolle verfügen, um ein Portal zu löschen. Außerdem müssen Sie der Eigentümer der Portalanwendung in Azure Active Directory sein. Der Benutzer, der das Portal anlegt, ist standardmäßig der Eigentümer und kann ein Portal löschen. Informationen zum Hinzufügen von sich selbst als Eigentümer finden Sie unter [Sich selbst als Eigentümer der Anwendung Azure AD hinzufügen](admin/admin-overview.md#add-yourself-as-an-owner-of-the-azure-ad-application).

## <a name="details"></a>Details

Zeigt Details wie den Eigentümer des Portale, Datum und Uhrzeit der Erstellung und letzten Änderung sowie die URL des Portale an.

> [!div class=mx-imgBorder]
> ![Portal-Details](media/portal-details.png "Portal-Details")  

