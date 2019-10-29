---
title: Verwalten vorhandener Portale in powerapps | Microsoft-Dokumentation
description: Anweisungen zum Verwalten eines Portals in powerapps.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: f21671368bfdaf9623a294c86b113b6b62f028e7
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976436"
---
# <a name="manage-existing-portals-in-powerapps"></a>Verwalten vorhandener Portale in powerapps

Nachdem Sie ein Portal erstellt haben, wird es auf der powerapps-Startseite im Abschnitt **zuletzt verwendete apps** angezeigt.

> [!div class=mx-imgBorder]
> ![](media/recent-apps.png "zuletzt verwendete") apps  

Zum Verwalten einer APP wählen Sie **Weitere Befehle** ( **...** ) für das Portal aus, und wählen Sie im Kontextmenü eine Aktion aus.

> [!div class=mx-imgBorder]
> Portal ![App-Optionen](media/portal-app-options.png "Portal App-Optionen")  

## <a name="edit"></a>Bearbeiten

Öffnet die [powerapps-Portale Studio](portal-designer-anatomy.md) , um den Inhalt und die Komponenten des Portals zu bearbeiten.  

> [!div class=mx-imgBorder]
> ![Portal]Maker-(media/portal-maker.png "Portal")  

## <a name="browse"></a>Sen

Öffnet das Portal zum Durchsuchen der Website. Auf diese Weise können Sie das Portal sehen, wie es Ihren Kunden entspricht.

> [!div class=mx-imgBorder]
> ![Portal]Website(media/portal-website.png "Portal-Website")  

Alternativ dazu können Sie auch das Portal öffnen, um die Website zu durchsuchen, indem Sie in [powerapps Portale Studio](portal-designer-anatomy.md) **Website durchsuchen** auswählen, um die Änderungen anzuzeigen, die Sie an der Website vorgenommen haben. Die Website wird auf einer neuen Registerkarte mit der URL der Website geöffnet.

## <a name="share"></a>Freigeben

Geben Sie Ihr Portal für interne oder externe Benutzer frei. Führen Sie die im Bereich **Freigeben dieses Portals** beschriebenen Schritte aus.

> [!div class=mx-imgBorder]
> ![Freigeben des Portal](media/share-portal.png "Freigabe Portals")  

### <a name="share-with-internal-users"></a>Freigeben mit internen Benutzern

Um das Portal für interne Benutzer freizugeben, müssen Sie zunächst eine Sicherheitsrolle erstellen und dann der Sicherheitsrolle Benutzer zuweisen, damit Sie das Portal verwenden können.

> [!NOTE]
> Wenn Sie als Benutzer in Common Data Service nicht über die entsprechenden Berechtigungen für Portal Entitäten verfügen, werden möglicherweise Fehler angezeigt, z. b. "Sie haben keinen Zugriff, um Lösungen in dieser Umgebung anzuzeigen." oder "Sie haben keinen Zugriff auf die Website anzeigen". Es wird empfohlen, dass Sie sich in der entsprechenden Common Data Service Datenbank in einer System Administrator-Sicherheitsrolle befinden.

#### <a name="step-1-create-a-security-role"></a>Schritt 1: Erstellen einer Sicherheitsrolle

1.  Wählen Sie im Bereich **dieses Portal freigeben** unter **Sicherheitsrolle erstellen**die Option **Sicherheitsrollen**aus. Eine Liste aller konfigurierten Sicherheitsrollen wird angezeigt.

2.  Wählen Sie auf der Symbolleiste Aktionen die Option **neu**aus.

3.  Geben Sie im Fenster **neue Sicherheitsrolle** den Rollennamen ein.

4.  Legen Sie die Berechtigungen für alle im Portal verwendeten Entitäten fest.

5.  Wenn Sie die Konfiguration der Sicherheitsrolle abgeschlossen haben, klicken Sie auf der Symbolleiste auf **Speichern und schließen**.

Informationen zu Sicherheitsrollen und Berechtigungen finden Sie unter [Sicherheitsrollen und-Berechtigungen](https://docs.microsoft.com/dynamics365/customer-engagement/admin/security-roles-privileges).  

#### <a name="step-2-assign-users-to-the-security-role"></a>Schritt 2: Zuweisen von Benutzern zur Sicherheitsrolle

1.  Wählen Sie im Bereich **dieses Portal freigeben** unter **Benutzer der Sicherheitsrolle zuweisen die**Option **Benutzer**aus. Eine Liste aller Benutzer wird angezeigt.

2.  Wählen Sie den Benutzer aus, dem Sie eine Sicherheitsrolle zuweisen möchten.

3.  Klicken Sie auf **Rollen verwalten**.

    > [!NOTE]
    > Wenn die Schaltfläche **Rollen verwalten** in der Befehlsleiste nicht angezeigt wird, müssen Sie den Client ändern, indem Sie in der URL forceuci auf 0 festlegen. Beispiel: https://&lt;org\_URL&gt;/Main.aspx? PageType = entityList & ETN = systemuser & forceuci = 0

4.  Wählen Sie im Dialogfeld **Benutzer Rollen verwalten** die Sicherheitsrolle aus, die Sie zuvor erstellt haben, und klicken Sie dann auf **OK**.

### <a name="share-with-external-users"></a>Freigabe für externe Benutzer

Ihr Portal sollte anonym arbeiten und für externe Benutzer zugänglich sein. Wenn Sie erweiterte Funktionen für die Verwaltung von Rollen und Berechtigungen für externe Benutzer testen möchten, finden Sie weitere [Informationen unter Konfigurieren eines Kontakts für die Verwendung in einem Portal](https://docs.microsoft.com/dynamics365/customer-engagement/portals/configure-contacts), [einladen von Kontakten zu Ihren Portalen](https://docs.microsoft.com/dynamics365/customer-engagement/portals/invite-contacts), [Erstellen von Webrollen für Portale](https://docs.microsoft.com/dynamics365/customer-engagement/portals/create-web-roles), [Zuweisen von Entitäts Berechtigungen. ](https://docs.microsoft.com/dynamics365/customer-engagement/portals/assign-entity-permissions).  

## <a name="settings"></a>Einstellungen

Zeigt die Portal Einstellungen an und ermöglicht es Ihnen, den Namen des Portals zu ändern. Sie können auch erweiterte Aktionen ausführen, wie z. b. das Verwalten des Portals über das powerapps-Portal Admin Center und das Arbeiten mit Website Einstellungen. Einstellungen enthält Links zu den powerapps-Portalen Admin Center und Site Einstellungen. Weitere Informationen finden Sie unter [Erweiterte Portal Verwaltung](admin/admin-overview.md) und [Konfigurieren von Site Einstellungen](configure/configure-site-settings.md).  

> [!div class=mx-imgBorder]
> Portal ![Einstellungen](media/portal-settings.png "Portal Einstellungen")  

## <a name="delete"></a>Lösch

Löscht das Portal und die gehosteten Ressourcen. Wenn Sie ein Portal löschen, ist die zugehörige URL nicht mehr verfügbar. Das Löschen eines Portals wirkt sich nicht auf Portal Konfigurationen oder Lösungen aus, die in Ihrer Umgebung vorhanden sind, und Sie bleiben unverändert.
Sie müssen die Portal Konfigurationen manuell löschen, um die Portal Konfigurationen vollständig aus Ihrer Umgebung zu entfernen. Verwenden Sie hierzu die Portal Verwaltungs-APP, und löschen Sie den entsprechenden Website Daten Satz für das Portal.

> [!NOTE]
> Wenn Sie nicht über ausreichende Berechtigungen zum Löschen eines Portals verfügen, wird ein Fehler angezeigt. Zum Löschen eines Portals müssen Sie über die Rolle "System Administrator" verfügen. Außerdem müssen Sie der Besitzer der Portal Anwendung in Azure Active Directory sein. Der Benutzer, der das Portal erstellt, ist standardmäßig der Besitzer und kann ein Portal löschen. Informationen dazu, wie Sie sich selbst als Besitzer hinzufügen, finden Sie unter [Hinzufügen als Besitzer der Azure AD Anwendung](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/manage-portal#to-add-yourself-as-an-owner-of-the-azure-ad-application).

## <a name="details"></a>Details

Zeigt Details wie den Besitzer des Portals, das Datum und die Uhrzeit der Erstellung und die letzte Änderung und die URL des Portals an.

> [!div class=mx-imgBorder]
> Details zum ![Portal Details]-(media/portal-details.png "Portal")  

