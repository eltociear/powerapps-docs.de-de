---
title: Portal zurücksetzen | MicrosoftDocs
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
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2709537"
---
# <a name="reset-a-portal"></a>Ein Portal zurücksetzen

Sobald ein Portal bereitgestellt ist, müssen Sie möglicherweise unter bestimmten Umständen Ressourcen aus Ihrem Portal löschen, z. B. wenn Sie Ihre Organisation in einen anderen Mandant oder ein anderes Rechenzentrum verlegen oder wenn Sie das Portal aus Ihrer Organisation entfernen möchten.

Um dies zu tun, können Sie das Portal zurücksetzen, wodurch alle gehosteten Ressourcen, die zugeordnet sind, gelöscht werden. Anschließend können Sie das Portal wieder verwenden. Nach dem Rücksetzungsvorgang ist Ihre Portal-URL nicht mehr verfügbar.

Es ist wichtig zu beachten, dass das Zurücksetzen Ihres Portale nicht die Portalkonfiguration oder die in Ihrer Instanz vorhandenen Lösungen entfernt und sie bleiben unverändert.

Sie können ein vollständig konfiguriertes Portal oder ein Portal zurücksetzen, bei dem die Bereitstellung oder Aktualisierung einer Instanz fehlgeschlagen ist.

Um ein konfiguriert Portal zurücksetzen:

1.  Öffnen Sie das [Admin Center für PowerApps-Portale](admin-overview.md).

2.  Öffnen Sie **Portalaktionen** > **Portal zurücksetzen**.

    > [!div class=mx-imgBorder]
    > ![Ein Portal zurücksetzen](../media/reset-portal.png "Ein Portal zurücksetzen")

3.  Klicken Sie im Bestätigungsfenster auf **Schließen**.

> [!NOTE]
> - Ohne die entsprechenden Berechtigungen einer zugeordneten Azure Active Directory-Anwendung wird ein Fehler angezeigt. Sie müssen den globalen Administrator für die entsprechenden Rechte kontaktieren.
> - Wenn Sie ein Portal mit dem älteren Portal-Add-On bereitgestellt haben und das Portal erfolgreich zurücksetzt wurde, bleibt der Portalname und sein Status auf der Registerkarte **Anwendungen** im Dynamics 365-Administratorcenter unverändert. Beispielsweise wenn der Status Portalname und Portal 1 entsprechend konfiguriert wurden, ändern diese Werte nach dem Zurücksetzen des Portals nicht. Wenn Sie den Portalnamen ändern möchten, können Sie diesen auf der Registerkarte **Portaldetails** im PowerApps-Portal-Administratorencenter ändern. Allerdings kann der Wert nicht zu nicht konfiguriert zurückgesetzt werden.
> - Beachten Sie bitte, dass es wichtig ist, dass der Status des Portals auf der Registerkarte **Anwendungen** nicht den Bereitstellungsstatus darstellt und sich nicht auf das Anliegen des Portals auswirkt. Es wird nur angezeigt, ob Sie je auf das PowerApps-Portal-Administratorcenter für dieses entsprechende Portal zugegriffen haben oder nicht.

Wenn das Portal nicht ordnungsgemäß bereitgestellt ist, hat es einen Fehlerstatus und der folgende Bildschirm wird angezeigt. Sie können in diesem Fall das Portal auch zurücksetzen, indem Sie **Portal zurücksetzen** auf dem Fehlerbildschirm auswählen.

> [!div class=mx-imgBorder]
> ![Fehler beim Bereitstellen des Portals](../media/provision-portal-error.png "Fehler beim Bereitstellen des Portals")

## <a name="troubleshooting"></a>Problembehandlung

Dieser Abschnitt enthält Informationen zur Problembehandlung während das Portal zurückgesetzt wird.

### <a name="reset-request-could-not-be-submitted"></a>Rücksetzungsanforderung kann nicht gesendet werden

Wenn eine Portalrücksetzungsanforderung nicht gesendet werden kann, wird ein Fehler im folgenden Bild der Ansicht angezeigt. In diesem Fall müssen Sie das PowerApps-Portal-Administratorcenter schließen und erneut öffnen und versuchen, das Portal erneut zurückzusetzen. Falls das Problem weiterhin besteht, wenden Sie sich an den Kundensupport von Microsoft.

> [!div class=mx-imgBorder]
> ![Fehler beim Zurücksetzen des Portals](../media/reset-portal-request-error.png "Fehler beim Zurücksetzen des Portals")

### <a name="reset-portal-job-fails"></a>Portalrücksetzung ist fehlgeschlagen

Wenn ein Zurücksetzen des Portals fehlschlägt, wird eine Fehlermeldung mit der die Aktion **Portal zurücksetzen** angezeigt.

> [!div class=mx-imgBorder]
> ![Fehler beim Zurücksetzen des Portals](../media/reset-portal-error.png "Fehler beim Zurücksetzen des Portals")

In der Regel sind diese Fehler vorübergehende und Sie müssen **Portal zurücksetzen** auswählen, um die Reihenfolge neu zu starten. Falls das Problem weiterhin besteht, wenden Sie sich an den Kundensupport von Microsoft.

