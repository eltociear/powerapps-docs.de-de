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
ms.openlocfilehash: 31ae1238638ed4d10401f1c0a0fb5922a95263e5
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2867189"
---
# <a name="reset-a-portal"></a>Ein Portal zurücksetzen

Sobald ein Portal bereitgestellt ist, müssen Sie möglicherweise unter bestimmten Umständen Ressourcen aus Ihrem Portal löschen, z. B. wenn Sie Ihre Organisation in einen anderen Mandant oder ein anderes Rechenzentrum verlegen oder wenn Sie das Portal aus Ihrer Organisation entfernen möchten.

Um dies zu tun, können Sie das Portal zurücksetzen, wodurch alle gehosteten Ressourcen, die zugeordnet sind, gelöscht werden. Anschließend können Sie das Portal wieder verwenden. Nach dem Rücksetzungsvorgang ist Ihre Portal-URL nicht mehr verfügbar.

Es ist wichtig zu beachten, dass das Zurücksetzen Ihres Portale nicht die Portalkonfiguration oder die in Ihrer Instanz vorhandenen Lösungen entfernt und sie bleiben unverändert.

Sie können ein vollständig konfiguriertes Portal oder ein Portal zurücksetzen, bei dem die Bereitstellung oder Aktualisierung einer Instanz fehlgeschlagen ist.

Um ein konfiguriert Portal zurücksetzen:

1.  Öffnen Sie das [Admin Center für Power Apps-Portale](admin-overview.md).

2.  Öffnen Sie **Portalaktionen** > **Portal zurücksetzen**.

    > [!div class=mx-imgBorder]
    > ![Ein Portal zurücksetzen](../media/reset-portal.png "Ein Portal zurücksetzen")

3.  Klicken Sie im Bestätigungsfenster auf **Schließen**.

> [!NOTE]
> - Ohne die entsprechenden Berechtigungen einer zugeordneten Azure Active Directory-Anwendung wird ein Fehler angezeigt. Sie müssen den globalen Administrator für die entsprechenden Rechte kontaktieren.
> - Wenn Sie ein Portal mit dem älteren Portal-Add-On bereitgestellt haben und das Portal erfolgreich zurückgesetzt wurde, werden der Portalname und sein Status auf der Registerkarte **Anwendungen** auf der Seite **Dynamics 365 Admin Center** nicht geändert. Beispielsweise wenn der Status Portalname und Portal 1 entsprechend konfiguriert wurden, ändern diese Werte nach dem Zurücksetzen des Portals nicht. Wenn Sie den Portalnamen ändern möchten, können Sie ihn auf der Registerkarte **Portaldetails** im Power Apps Portale Administrationscenter ändern. Allerdings kann der Wert nicht zu nicht konfiguriert zurückgesetzt werden.
> - Beachten Sie bitte, dass es wichtig ist, dass der Status des Portals auf der Registerkarte **Anwendungen** nicht den Bereitstellungsstatus darstellt und sich nicht auf das Anliegen des Portals auswirkt. Es wird nur angezeigt, ob Sie jemals auf das Power Apps Portale Administrationscenter für das entsprechende Portal zugegriffen haben oder nicht.

Wenn das Portal nicht ordnungsgemäß bereitgestellt ist, hat es einen Fehlerstatus und der folgende Bildschirm wird angezeigt. Sie können in diesem Fall das Portal auch zurücksetzen, indem Sie **Portal zurücksetzen** auf dem Fehlerbildschirm auswählen.

> [!div class=mx-imgBorder]
> ![Fehler beim Bereitstellen des Portals](../media/provision-portal-error.png "Fehler bei der Bereitstellung eines Portale")

## <a name="troubleshooting"></a>Problembehandlung

Dieser Abschnitt enthält Informationen zur Problembehandlung während das Portal zurückgesetzt wird.

### <a name="reset-request-could-not-be-submitted"></a>Rücksetzungsanforderung kann nicht gesendet werden

Wenn eine Portalrücksetzungsanforderung nicht gesendet werden kann, wird ein Fehler im folgenden Bild der Ansicht angezeigt. In diesem Fall müssen Sie das Power Apps Portale Administrationscenter schließen und wieder öffnen und versuchen, das Portal erneut zurückzusetzen. Falls das Problem weiterhin besteht, wenden Sie sich an den Kundensupport von Microsoft.

> [!div class=mx-imgBorder]
> ![Fehler beim Zurücksetzen des Portals](../media/reset-portal-request-error.png "Fehler beim Zurücksetzen eines Portale")

### <a name="reset-portal-job-fails"></a>Portalrücksetzung ist fehlgeschlagen

Wenn ein Zurücksetzen des Portals fehlschlägt, wird eine Fehlermeldung mit der die Aktion **Portal zurücksetzen** angezeigt.

> [!div class=mx-imgBorder]
> ![Fehler beim Zurücksetzen des Portals](../media/reset-portal-error.png "Fehler beim Zurücksetzen eines Portale")

In der Regel sind diese Fehler vorübergehende und Sie müssen **Portal zurücksetzen** auswählen, um die Reihenfolge neu zu starten. Falls das Problem weiterhin besteht, wenden Sie sich an den Kundensupport von Microsoft.

