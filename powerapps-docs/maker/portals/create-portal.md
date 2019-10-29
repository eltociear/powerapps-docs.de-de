---
title: Erstellen eines Portals in powerapps | Microsoft-Dokumentation
description: Anweisungen zum Erstellen eines Portals in powerapps.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 92ba08e47d3f0d657330ac3fcc6885626ff4a9e5
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975332"
---
# <a name="create-a-common-data-service-starter-portal"></a>Erstellen eines Common Data Service Starter-Portals

Mit der Funktion zum Erstellen eines Portals in powerapps können Sie eine Website für externe und interne Benutzer erstellen, die die Interaktion mit in Common Data Service gespeicherten Daten ermöglicht.

Dies sind einige Vorteile der Erstellung eines Portals:

- Da die Daten in Common Data Service gespeichert werden, müssen Sie keine Verbindung von powerapps erstellen, wie dies bei Datenquellen wie SharePoint, Modell gesteuerten apps in Dynamics 365 oder Salesforce der Fall ist. Sie müssen nur die Entitäten angeben, die Sie im Portal anzeigen oder verwalten möchten.

- Sie können das Portal über das WYSIWYG powerapps Portals Studio entwerfen, indem Sie Komponenten auf den Webseiten hinzufügen und konfigurieren.

Sie können ein Portal entweder in einer neuen Umgebung oder in der vorhandenen Umgebung erstellen.

Wenn Sie das Portal in einer neuen Umgebung erstellen, indem Sie den Link **neue Umgebung erstellen** verwenden, werden die erforderlichen Voraussetzungen für das Portal, wie z. b. Entitäten, Daten und eine Starter Portal-Vorlage, beim Erstellen der Umgebung installiert. Bei dieser Methode wird das Portal in wenigen Minuten bereitgestellt.

Wenn Sie Ihr Portal in einer vorhandenen Umgebung ohne Voraussetzungen für das Portal erstellen, werden die Voraussetzungen zuerst installiert, und anschließend wird das Portal erstellt. Bei dieser Methode kann die Portal Bereitstellung einige Zeit in Anspruch nehmen, und Sie werden benachrichtigt, wenn das Portal bereitgestellt wird.

Basierend auf der ausgewählten Umgebung können Sie in powerapps ein Common Data Service Starter-Portal oder ein Dynamics 365-Portal erstellen.

Weitere Informationen zum Arbeiten mit Umgebungen: [Arbeiten mit Umgebungen und Microsoft PowerApps](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-environments)

Weitere Informationen zu verfügbaren Portal Vorlagen: [Portal Vorlagen](portal-templates.md)

So erstellen Sie ein Portal:

1.  Melden Sie sich bei [PowerApps](http://web.powerapps.com) an.  

2.  Wählen Sie unter **eigene APP erstellen**die Option **Portal von leer aus**.

3.  Wenn die ausgewählte Umgebung keine Voraussetzungen für das Portal enthält, wird im **Portal aus dem leeren** Fenster eine Meldung angezeigt, in der Sie darauf hindeuten, dass Sie eine andere Umgebung auswählen oder eine neue erstellen.

    > [!div class=mx-imgBorder]
    > ![neue Umgebungs Nachricht]erstellen(media/create-portal-message.png "neue Umgebungs Nachricht") erstellen

4.  Wenn Sie die aktuelle Umgebung fortsetzen möchten, geben Sie die erforderlichen Informationen in das-Fenster ein, wie in den folgenden Schritten beschrieben. Wenn Sie eine neue Umgebung erstellen, finden Sie weitere Informationen unter [Erstellen einer neuen Umgebung](#create-new-environment).

5.  Geben Sie im **Portal aus dem leeren** Fenster einen Namen für das Portal und die Adresse für die Website ein, und wählen Sie eine Sprache aus der Dropdown Liste aus. Wenn Sie fertig sind, wählen Sie **Erstellen**aus.

    > [!div class=mx-imgBorder]
    > ![neues Portal]erstellen(media/create-new-portal.png "neues Portal erstellen")  

Nachdem Sie **Erstellen**ausgewählt haben, wird das Portal bereitgestellt, und der Bereitstellungs Status wird durch [Benachrichtigungen](#portal-provisioning-notifications)angezeigt.

Wenn Sie Ihr Portal in der Umgebung erstellt haben, für die keine Voraussetzungen für das Portal installiert wurden, wird der Bereitstellungs Status auch im Raster angezeigt:

> [!div class=mx-imgBorder]
> Benachrichtigung zum ![Raster Benachrichtigungs](media/provision-progress-notif.png "Raster")

Nachdem das Portal erfolgreich bereitgestellt wurde, wird der Status aktualisiert, und das Portal wird im Raster angezeigt:

> [!div class=mx-imgBorder]
> ![Portal Bereitstellung](media/recent-apps.png "des Portals bereit") gestellt

Informationen zum Bearbeiten des Portals in powerapps Portale Studio finden Sie unter [Bearbeiten eines Portals](manage-existing-portals.md#edit).

> [!NOTE]
> - In einem Mandanten können maximal fünf Portale erstellt werden. Es kann jedoch nur ein Portal für jeden Typ in einer Umgebung erstellt werden.
> - Wenn Sie nicht über ausreichende Berechtigungen zum Bereitstellen eines Portals verfügen, wird ein Fehler angezeigt. Sie müssen über die System Administrator Rolle in Common Data Service verfügen, um ein Portal erstellen zu können. Außerdem muss der **Zugriffsmodus** unter **Client Zugriffslizenz-Informationen (Client Access License, CAL)** im Benutzerdaten Satz auf **Lese-/Schreibzugriff** festgelegt sein.
> - Wenn Sie ein älteres Portal-Add-on erworben haben und ein Portal mithilfe des Add-Ins bereitstellen möchten, müssen Sie auf der Seite **Dynamics 365-Verwaltungs Center** navigieren. Weitere Informationen finden Sie unter [Bereitstellen eines Portals](https://docs.microsoft.com/en-gb/dynamics365/customer-engagement/portals/provision-portal) .
> - Wenn Sie ein Portal mithilfe des älteren Portal-Add-ins bereitgestellt haben, können Sie es dennoch über [make.powerapps.com](https://make.powerapps.com)anpassen und verwalten.
> - Die Bereitstellungs Portale von [make.powerapps.com](https://make.powerapps.com) verbrauchen nicht die älteren Portal-Add-ons. Außerdem sind diese Portale nicht auf der Registerkarte **Anwendungen** auf der Seite **Dynamics 365-Verwaltungs Center** aufgeführt.
> - Ein Common Data Service Starter-Portal kann nicht auf der Seite **Dynamics 365 Administration Center** erstellt werden.
> - Powerapps-Portale sind in der Region "Frankreich" nicht verfügbar.

## <a name="create-new-environment"></a>Neue Umgebung erstellen

Führen Sie die folgenden Schritte aus, wenn Sie eine Umgebung mit der Option erstellen, die im **Portal aus einem leeren** Fenster bereitgestellt wird.

1.  Geben Sie im **Bereich neue Umgebung** einen Namen für die Umgebung ein, und wählen Sie dann in den Dropdown Listen eine Region und einen Umgebungstyp aus. Nachdem die Umgebung erstellt wurde, können Sie die Region nicht mehr ändern. Wenn Sie fertig sind, wählen Sie **Umgebung erstellen**aus.

    > [!div class=mx-imgBorder]
    > neue ![Umgebung]erstellen(media/create-new-environment.png "neue Umgebung erstellen")  

2.  Nachdem die Umgebung erstellt wurde, erhalten Sie eine Bestätigungsmeldung im Dialogfeld, und Sie werden aufgefordert, eine Datenbank zu erstellen. Wählen Sie **Datenbank erstellen** aus, um den Zugriff auf Common Data Service zu aktivieren.

    > [!NOTE]
    > Die Eingabeaufforderung zum Erstellen einer Datenbank wird möglicherweise nicht automatisch angezeigt. In diesem Fall müssen Sie die neue Umgebung aufrufen und das **Portal erneut von der leeren** Kachel auswählen.

    > [!div class=mx-imgBorder]
    > ![neue Umgebung erstellte](media/new-environment-created.png "neue") Umgebung erstellt  

3.  Wählen Sie für die in der Datenbank gespeicherten Daten eine Währung und eine Sprache aus. Nachdem die Datenbank erstellt wurde, können Sie die Währung und die Sprache nicht mehr ändern. Wenn Sie fertig sind, wählen Sie **meine Datenbank erstellen**aus. Die Datenbank wird mit dem Starter Portal erstellt, das Ihnen den schnellen Einstieg in Beispiel Inhalt ermöglicht, nachdem das Portal bereitgestellt wurde.

    > [!NOTE]
    > Die Option **Starter Portal einschließen** ist nur verfügbar, wenn Sie eine Umgebung mithilfe der Option erstellen, die im **Portal aus einem leeren** Fenster bereitgestellt wird. Diese Option ist nicht verfügbar, wenn Sie eine Umgebung über das powerapps Admin Center erstellen.

    > [!div class=mx-imgBorder]
    > ![neue Datenbank]erstellen(media/create-new-database.png "neue Datenbank erstellen") 

    Es kann einige Minuten dauern, bis die Datenbank auf Common Data Service erstellt wird. Nachdem die Datenbank erstellt wurde, wird die neue Umgebung in der Liste der Umgebungen auf der powerapps-Startseite ausgewählt, und die Portal Verwaltungs-APP wird erstellt. Diese APP ist nicht das eigentliche Portal, sondern eine Modell gesteuerte Begleit-APP, die es Ihnen ermöglicht, Erweiterte Konfigurations Aktivitäten auszuführen. Sie können nun mit dem Erstellen des Portals zum Entwerfen der extern ausgerichteten Website fortfahren.

    > [!div class=mx-imgBorder]
    > ![Portal Verwaltung App](media/portal-mgmt-app.png "Portal Verwaltungs-App")

4. Nachdem Sie die Umgebung und die Datenbank erstellt haben, wählen Sie unter **eigene APP erstellen**die Option **Portal von leer aus**. 

    > [!NOTE]
    > Wenn die Datenbank erstellt wird und Sie immer noch die Eingabeaufforderung zum Erstellen der Datenbank erhalten, müssen Sie die powerapps-Startseite aktualisieren, bevor Sie das **Portal aus der leeren** Kachel auswählen.


## <a name="portal-provisioning-notifications"></a>Portal Bereitstellungs Benachrichtigungen

Nachdem Sie **Erstellen**ausgewählt haben, wird das Portal bereitgestellt, und der Bereitstellungs Status wird durch Benachrichtigungen angezeigt.

**Benachrichtigung als Toast**

Die folgende Benachrichtigung wird angezeigt, wenn Sie **Erstellen** auswählen, um das Portal bereitzustellen.

> [!div class=mx-imgBorder]
> Popup(media/toast-notif.png "Benachrichtigung für") Popup ![Benachrichtigung] 

**Benachrichtigungen im Benachrichtigungsbereich**

Nach dem erfolgreichen platzieren der Bereitstellungs Anforderung werden die folgenden Benachrichtigungen im **Benachrichtigungs** Bereich angezeigt.

Die Benachrichtigung zur Bereitstellung wird angezeigt.

> [!div class=mx-imgBorder]
> (media/pane-notif.png "Benachrichtigung") über Bereichs ![Benachrichtigungs]Bereich 

Die für die Bereitstellung angezeigte Benachrichtigung wurde erfolgreich abgeschlossen.

> [!div class=mx-imgBorder]
> Benachrichtigung zur erfolgreichen Bereitstellung von ![Benachrichtigungs](media/provision-complete-notif.png "Bereitstellungen") 

Wenn die Portal Bereitstellung fehlschlägt, werden die Benachrichtigungen ähnlich angezeigt.
  
**Benachrichtigungen per e-Mail**

Nachdem die Bereitstellungs Anforderung erfolgreich platziert wurde, wird eine Bestätigungs-e-Mail-Benachrichtigung an den Benutzer gesendet, der das Portal erstellt. Außerdem wird eine e-Mail an den Benutzer gesendet, nachdem die Portal Bereitstellung abgeschlossen wurde.

## <a name="disable-portal-creation-in-a-tenant"></a>Deaktivieren der Portal Erstellung in einem Mandanten

Wenn Sie als globaler Administrator die Portal Erstellung in einem Mandanten durch nicht-Administratoren deaktivieren möchten, können Sie dies durch Aktivieren der Einstellung auf `disablePortalsCreationByNonAdminUsers` Mandanten Ebene über PowerShell aktivieren. Zum Ausführen von PowerShell-Cmdlets müssen Sie zuerst die erforderlichen Module installieren. Informationen zum Installieren der erforderlichen PowerShell-Module finden Sie unter [Installation](https://docs.microsoft.com/en-us/power-platform/admin/powerapps-powershell#installation).

Führen Sie nach der Installation der Module den folgenden Befehl in einem PowerShell-Fenster aus (führen Sie PowerShell als Administrator aus).

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $true }
```

Administratoren haben eine der folgenden Azure-Rollen:

- Globaler Administrator
- Dynamics 365-Dienst Administrator
- Power Platform-Dienst Administrator

Benutzer, die über keine der oben genannten Azure-Rollen verfügen, werden als nicht Administratoren angesehen.

Wenn die Portal Erstellung in einem Mandanten deaktiviert ist, wird nicht Administratoren wie folgt ein Fehler angezeigt:

> [!div class=mx-imgBorder]
> Fehler bei der ![Portal Erstellung für blockierte Fehler](media/portal-create-blocked-error.png "Portal Erstellung")
