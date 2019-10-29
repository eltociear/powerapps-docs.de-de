---
title: Zurücksetzen eines Portals | MicrosoftDocs
description: Erfahren Sie, wie Sie ein Portal zurücksetzen.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 7b5bbc05ca7adf7fad9725215f8a7d6c06c035bb
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975723"
---
# <a name="reset-a-portal"></a>Zurücksetzen eines Portals

Nach der Bereitstellung eines Portals müssen Sie möglicherweise unter bestimmten Umständen Ressourcen aus Ihrem Portal löschen, z. b. Wenn Sie Ihre Organisation in einen anderen Mandanten oder ein anderes Daten Center verschieben oder das Portal aus Ihrer Organisation entfernen möchten.

Zu diesem Zweck können Sie Ihr Portal zurücksetzen, wodurch alle zugeordneten gehosteten Ressourcen gelöscht werden. Anschließend können Sie das Portal erneut bereitstellen. Nachdem der Zurücksetzungs Vorgang abgeschlossen ist, kann die Portal-URL nicht mehr aufgerufen werden.

Beachten Sie, dass das Zurücksetzen des Portals die Portal Konfiguration oder die in Ihrer Instanz vorhandenen Lösungen nicht entfernt und unverändert bleibt.

Sie können ein vollständig konfiguriertes Portal oder ein Portal zurücksetzen, für das die Bereitstellung oder Aktualisierung einer Instanz fehlgeschlagen ist.

So setzen Sie ein konfiguriertes Portal zurück:

1.  Öffnen Sie das [powerapps-Portal Admin Center](admin-overview.md).

2.  Wechseln Sie zu **Portal Aktionen** > **Portal zurücksetzen**.

    > [!div class=mx-imgBorder]
    > ![Zurücksetzen eines]Portals zurück(../media/reset-portal.png "setzen eines Portals")

3.  Wählen Sie im Bestätigungsfenster **Zurücksetzen** aus.

> [!NOTE]
> - Wenn Sie nicht über die entsprechenden Berechtigungen für eine zugeordnete Azure Active Directory Anwendung verfügen, wird ein Fehler angezeigt. Sie müssen sich an den globalen Administrator wenden, um die entsprechenden Berechtigungen zu erhalten.
> - Wenn Sie ein Portal mithilfe des älteren Portal-Add-ins bereitgestellt haben und das Portal erfolgreich zurückgesetzt wurde, ändert sich der Portal Name und der zugehörige Status auf der Registerkarte " **Anwendungen** " im Dynamics 365 Admin Center nicht. Wenn Ihr Portal Name und-Status z. b. Portal 1 und konfiguriert sind, werden diese Werte nach dem Zurücksetzen des Portals nicht geändert. Wenn Sie den Portal Namen ändern möchten, können Sie ihn auf der Registerkarte " **Portal Details** " im Admin Center der powerapps-Portale ändern. Der Statuswert kann jedoch nicht auf "nicht konfiguriert" zurückgesetzt werden.
> - Beachten Sie unbedingt, dass der Status des Portals auf der Registerkarte **Anwendungen** nicht den Bereitstellungs Status darstellt und sich nicht auf die Funktionsweise Ihres Portals auswirkt. Es zeigt lediglich, ob Sie schon einmal auf das powerapps-Portal Admin Center für das entsprechende Portal zugegriffen haben.

Wenn Ihr Portal nicht ordnungsgemäß bereitgestellt wurde, tritt ein Fehler auf, und der folgende Bildschirm wird angezeigt. In diesem Fall können Sie das Portal auch zurücksetzen, indem Sie auf dem Fehlerbildschirm auf **Portal zurücksetzen** klicken.

> [!div class=mx-imgBorder]
> ![Fehler beim Bereitstellen eines Portal](../media/provision-portal-error.png "Fehlers beim Bereitstellen eines Portals") .

## <a name="troubleshooting"></a>Problembehandlung

Dieser Abschnitt enthält Informationen zur Behandlung von Problemen beim Zurücksetzen eines Portals.

### <a name="reset-request-could-not-be-submitted"></a>Die Zurücksetzungs Anforderung konnte nicht übermittelt werden.

Wenn eine Anforderung zum Zurücksetzen des Portals nicht übermittelt werden konnte, wird ein Fehler angezeigt, wie in der folgenden Abbildung dargestellt. In diesem Fall müssen Sie das powerapps-Portal Admin Center schließen und erneut öffnen und versuchen, das Portal erneut zurückzusetzen. Wenn das Problem weiterhin besteht, wenden Sie sich an den Microsoft Support.

> [!div class=mx-imgBorder]
> ![Fehler beim Zurücksetzen eines Portal](../media/reset-portal-request-error.png "Fehlers beim Zurücksetzen eines Portals") .

### <a name="reset-portal-job-fails"></a>Fehler beim Zurücksetzen des Portal Auftrags

Wenn ein Auftrag zum Zurücksetzen des Portals fehlschlägt, wird eine Fehlermeldung zusammen mit der Aktion zum **Zurücksetzen des Portals** angezeigt.

> [!div class=mx-imgBorder]
> ![Fehler beim Zurücksetzen eines Portal](../media/reset-portal-error.png "Fehlers beim Zurücksetzen eines Portals") .

In der Regel handelt es sich hierbei um vorübergehende Fehler, und Sie müssen das **Portal zurücksetzen** auswählen, um den Auftrag neu Wenn das Problem weiterhin besteht, wenden Sie sich an den Microsoft Support.

