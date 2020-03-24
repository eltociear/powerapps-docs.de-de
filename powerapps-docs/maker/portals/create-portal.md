---
title: Erstellen eines Portals in Power Apps | MicrosoftDocs
description: Anweisungen zu Erstellen eines Portals in Power Apps.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 02/07/2020
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 987541aff2cb3585fa19c1c9f8007ad4a79b163d
ms.sourcegitcommit: 80120b59d440bb7a3ddca93cd51154607f749f6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "3033096"
---
# <a name="create-a-common-data-service-starter-portal"></a>Erstellen eines Common Data Service-Starterportal

Mit der Funktion zum Erstellen eines Portals in Power Apps können Sie eine Website für externe und interne Benutzer erstellen. So können diese mit Daten interagieren, die in Common Data Service gespeichert sind.

Nachfolgend sind einige Vorteile des Erstellens eines Portals aufgeführt:

- Da die Daten in Common Data Service gespeichert sind, müssen Sie keine Verbindung von Power Apps erstellen, wie Sie es sonst bei Datenquellen wie SharePoint, modellgesteuerten Apps in Dynamics 365 oder Salesforce tun. Sie müssen nur die Entitäten angeben, die Sie im Portal anzeigen oder verwalten möchten.

- Sie können das Portal über das WYSIWYG-Power Apps Portal-Studio entwerfen, indem Sie Komponenten auf den Webseiten hinzufügen und konfigurieren.

Sie können ein Portel entweder in einer neuen oder in Ihrer vorhandenen Umgebung erstellen.

Wenn Sie Ihr Portal in einer neuen Umgebung über den Link **Neue Umgebung erstellen** erstellen, werden die erforderlichen Portalvoraussetzungen wie Entitäten, Daten und eine Starterportalvorlage installiert, sobald die Umgebung erstellt wird. Mit dieser Methode wird das Portal in wenigen Minuten bereitgestellt.

Wenn Sie Ihr Portal in einer vorhandenen Umgebung ohne Portalvoraussetzungen erstellen, werden zuerst die Voraussetzungen installiert und das Portal wird im Anschluss erstellt. Bei dieser Methode kann die Portalbereitstellung einige Zeit dauern. Sie werden benachrichtigt, sobald das Portal bereitgestellt wird.

Abhängig von der ausgewählten Umgebung in Power Apps können Sie ein Common Data Service-Starterportal oder ein Portal in einer Umgebung erstellen, die modellgesteuerte Apps in Dynamics 365 enthält.

> [!NOTE]
> Wenn Sie ein Portal erstellen, werden einige Lösungen installiert und Beispieldaten importiert.

Weitere Informationen zum Arbeiten mit Umgebungen finden Sie unter [Arbeiten mit Umgebungen und Microsoft Power Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-environments)

Weitere Informationen zu verfügbaren Portalvorlagen: [Portalvorlagen](portal-templates.md)

So erstellen Sie ein Portal:

1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.  

2.  Wählen Sie unter **Erstellen eigener Apps** die Option **Portal neu erstellen** aus.

3.  Wenn die ausgewählte Umgebung keine Portalvoraussetzungen enthält, wird eine Meldung im Fenster **Portal neu erstellen** angezeigt, in der vorgeschlagen wird, dass Sie eine andere Umgebung auswählen oder eine neue erstellen.

    > [!div class=mx-imgBorder]
    > ![Erstellen eine neuen Umgebungsnachricht](media/create-portal-message.png "Erstellen eine neuen Umgebungsnachricht")

4.  Wenn Sie mit der aktuellen Umgebung fortfahren möchten, geben Sie die erforderlichen Informationen in das Fenster ein, wie in den folgenden Schritten beschrieben. Wenn Sie eine neue Umgebung erstellen möchten, sehen Sie sich [Erstellen einer neuen Umgebung](#create-new-environment) an.

5.  Geben Sie im Fenster **Portal neu erstellen** einen Namen für das Portal und die Adresse für die Website ein, und wählen Sie eine Sprache aus der Dropdownliste aus. Wählen Sie **Erstellen** aus, wenn Sie fertig sind.

    > [!TIP]
    > Um ein Portal in einer anderen Sprache zu erstellen, müssen Sie zunächst [die Sprache in der Umgebung](https://docs.microsoft.com/power-platform/admin/enable-languages#enable-the-language) aktivieren, damit sie in der Dropdown-Liste für die Sprache verfügbar ist.

    > [!div class=mx-imgBorder]
    > ![Erstellen eines neuen Portals](media/create-new-portal.png "Erstellen eines neuen Portals")  

Wenn Sie **Erstellen** ausgewählt haben, beginnt das Portal mit der Bereitstellung und der Bereitstellungsstatus wird über [Benachrichtigungen](#portal-provisioning-notifications) angezeigt.

Wenn Sie das Portal in der Umgebung erstellt haben, bei der keine Portalvoraussetzungen installiert sind, wird der Bereitstellungsstatus auch im Raster angezeigt:

> [!div class=mx-imgBorder]
> ![Rasterbenachrichtigung](media/provision-progress-notif.png "Rasterbenachrichtigung")

Nachdem das Portal erfolgreich bereitgestellt wurde, wird der Status aktualisiert und das Portal im Raster angezeigt:

> [!div class=mx-imgBorder]
> ![Portalbereitstellung](media/recent-apps.png "Portalbereitstellung")

Um das Portal im Power Apps Portal-Stuido zu bearbeiten, sehen Sie sich die Informationen unter [Bearbeiten eines Portals](manage-existing-portals.md#edit) an.

> [!NOTE]
> - Von jedem Typ und für eine in einer Umgebung angelegte Sprache kann es nur ein Portal geben.
> - Wenn Sie nicht über ausreichende Rechte verfügen, um ein Portal bereitzustellen, wird ein Fehler angezeigt. Sie müssen über die Systemadministrator-Rolle in Common Data Service verfügen, um ein Portal zu erstellen. Der **Zugriffsmodus** muss auch auf **Lesen-Schreiben** unter **Informationen zur Clientzugriffslizenz (CAL)** im Benutzerdatensatz festgelegt sein.
> - Wenn Sie ein früheres Portal-Add-On erworben haben und ein Portal mit dem Add-On bereitstellen möchten, müssen Sie zur **Dynamics 365 Admin Center**-Seite gehen. Weitere Informationen: [Bereitstellen eines Portals mit dem früheren Portal-Add-On](provision-portal-add-on.md)
> - Wenn Sie ein Portal mit dem früheren Portal-Add-On bereitgestellt haben, können Sie es trotzdem noch anpassen und verwalten aus [make.powerapps.com](https://make.powerapps.com).
> - Die Bereitstellung von Portalen von [make.powerapps.com](https://make.powerapps.com) verbraucht nicht die vorherigen Portal-Add-Ons. Außerdem sind diese Portale werden nicht auf der Registerkarte **Anwendungen** auf der **Dynamics 365-Verwaltungscenter** Seite aufgelistet.
> - Ein Common Data Service Starterportal kann nicht von der **Dynamics 365-Verwaltungscenter** Seite erstellt werden.
> - Power Apps-Portale sind nicht in der Frankreich-Region verfügbar.

## <a name="create-new-environment"></a>Erstellen einer neuen Umgebung

Gehen Sie folgendermaßen vor, wenn Sie eine Umgebung mit der Option erstellen, die im Fenster **Portal neu erstellen** bereitgestellt wird.

1.  Geben Sie im Bereich **Neue Umgebung** einen Namen für die Umgebung ein, und wählen Sie dann eine Region und einen Umgebungstyp aus den Dropdownlisten aus. Sie können die Region nicht mehr ändern, nachdem die Umgebung erstellt wurde. Wählen Sie **Umgebung erstellen** aus, wenn Sie fertig sind.

    > [!div class=mx-imgBorder]
    > ![Erstellen einer neuen Umgebung](media/create-new-environment.png "Erstellen einer neuen Umgebung")  

2.  Sobald die Umgebung erstellt wurde, wird eine Bestätigungsmeldung im Dialogfeld angezeigt, und Sie werden aufgefordert, eine Datenbank zu erstellen. Wählen Sie **Datenbank erstellen** aus, um den Zugriff auf Common Data Service zu aktivieren.

    > [!NOTE]
    > Die Aufforderung zum Erstellen einer Datenbank wird möglicherweise nicht automatisch angezeigt. In diesem Fall müssen Sie zur neuen Umgebung wechseln und die Kachel **Portal neu erstellen** erneut auswählen.

    > [!div class=mx-imgBorder]
    > ![Neue Umgebung erstellt](media/new-environment-created.png "Neue Umgebung erstellt")  

3.  Wählen Sie die Währung und die Sprache für die in der Datenbank gespeicherten Daten aus. Die Währung oder die Sprache kann nicht mehr geändert werden, nachdem die Datenbank erstellt wurde. Wählen Sie **Meine Datenbank erstellen** aus, wenn Sie fertig sind. Die Datenbank wird mit dem Starterportal erstellt, durch das Sie schnell mit den Beispielinhalten starten können, sobald das Portal bereitgestellt wurde.

    > [!NOTE]
    > Die Option **Starterportal einschließen** ist nur verfügbar, wenn Sie eine Umgebung mithilfe der Option erstellen, die im Fenster **Portal neu erstellen** bereitgestellt wird. Diese Option ist nicht verfügbar, wenn Sie eine Umgebung über das Power Apps Admin Center erstellen.

    > [!div class=mx-imgBorder]
    > ![Neue Datenbank erstellen](media/create-new-database.png "Neue Datenbank erstellen") 

    Es kann einige Minuten dauern, die Datenbank bei Common Data Service zu erstellen. Sobald die Datenbank erstellt wurde, wird die neue Umgebung aus der Liste der Umgebungen auf der Power Apps-Homepage ausgewählt und die Portalverwaltungs-App erstellt. Bei dieser App handelt es sich nicht um das tatsächliche Portal, sondern um eine modellgesteuerte Begleit-App, mit der Sie erweiterte Verwaltungsaktivitäten ausführen können. Sie können jetzt mit der Erstellung des Portals zum Entwerfen der externen Website fortfahren.

    > [!div class=mx-imgBorder]
    > ![Portalverwaltungs-App](media/portal-mgmt-app.png "Portalverwaltungs-App")

4. Nachdem die Umgebung und die Datenbank erstellt wurden, wählen Sie unter **Erstellen eigener Apps** die Option **Portal neu erstellen** aus. 

    > [!NOTE]
    > Wenn die Datenbank erstellt wird und Sie weiterhin die Aufforderung zum Erstellen einer Datenbank erhalten, müssen Sie die Power Apps-Homepage aktualisieren, bevor Sie die Kachel **Portal neu erstellen** auswählen.


## <a name="portal-provisioning-notifications"></a>Benachrichtigungen über die Portalbereitstellung

Wenn Sie **Erstellen** ausgewählt haben, beginnt das Portal mit der Bereitstellung und der Bereitstellungsstatus wird über Benachrichtigungen angezeigt.

**Benachrichtigung als Popup**

Die folgende Benachrichtigung wird angezeigt, wenn Sie **Erstellen** auswählen, um das Portal bereitzustellen.

> [!div class=mx-imgBorder]
> ![Popupbenachrichtigung](media/toast-notif.png "Popupbenachrichtigung") 

**Benachrichtigungen im Benachrichtigungsbereich**

Sobald die Bereitstellungsanforderung erfolgreich platziert ist, werden folgende Benachrichtigungen im Bereich **Benachrichtigung** angezeigt.

Benachrichtigung, die für eine laufende Bereitstellung angezeigt wird

> [!div class=mx-imgBorder]
> ![Bereichsbenachrichtigung](media/pane-notif.png "Bereichsbenachrichtigung") 

Benachrichtigung, die für eine abgeschlossene Bereitstellung angezeigt wird

> [!div class=mx-imgBorder]
> ![Benachrichtigungen über erfolgreiche Bereitstellung](media/provision-complete-notif.png "Benachrichtigungen über erfolgreiche Bereitstellung") 

Wenn die Portalbereitstellung fehlschlägt, werden entsprechende Benachrichtigungen angezeigt.
  
**E-Mail-Benachrichtigungen**

Sobald die Bereitstellungsanforderung erfolgreich angeordnet ist, wird eine Bestätigungs-E-Mail-Benachrichtigung dem Benutzer gesendet, der das Portal erstellt. Außerdem wird eine E-Mail gesendet dem Benutzer gesendet, wenn die Portalbereitstellung abgeschlossen ist.

## <a name="disable-portal-creation-in-a-tenant"></a>Deaktivieren einer Portalerstellung in einem Mandanten

Wenn Sie die Portalerstellung als globaler Administrator in einem Mandanten durch Nichtadministratoren deaktivieren möchten, können Sie dies tun, indem Sie die Einstellung `disablePortalsCreationByNonAdminUsers` auf Mandantenebene über PowerShell aktivieren. Zum Ausführen von PowerShell-Cmdlets müssen Sie zuerst die erforderlichen Module installieren. Informationen zur Installation der erforderlichen PowerShell-Module finden Sie unter [Installation](https://docs.microsoft.com/power-platform/admin/powerapps-powershell#installation).

Nachdem Sie die Module installiert haben, führen Sie den folgenden Befehl in einem PowerShell Fenster aus (PowerShell als Administrator ausführen).

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $true }
```

Administratoren sind Benutzer, die eine der folgenden Azure-Rollen haben:

- Globaler -Administrator
- Dynamics 365 Service Administrator
- Power Platform-Serviceadministrator

Benutzer, die keine der oben genannten Azure-Rollen haben, werden als Nichtadministratoren betrachtet.

Wenn die Portalerstellung in einem Mandanten deaktiviert ist, wird Nichtadministratoren der folgende Fehler angezeigt:

> [!div class=mx-imgBorder]
> ![Portalerstellung Fehler gesperrt](media/portal-create-blocked-error.png "Portalerstellung Fehler gesperrt")
