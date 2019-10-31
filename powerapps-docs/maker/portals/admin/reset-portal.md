---
title: Ein Portal zurücksetzen | MicrosoftDocs
description: 'Erfahren Sie, wie Sie ein Portal zurücksetzen.'
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 07/18/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="reset-a-portal"></a>Ein Portal zurücksetzen

[!include[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

Sobald ein Portal bereitgestellt ist, müssen Sie möglicherweise unter bestimmten Umständen Ressourcen aus Ihrem Portal löschen, z. B. wenn Sie Ihre Organisation in einen anderen Mandant oder ein anderes Rechenzentrum verlegen oder wenn Sie das Portal aus Ihrer Organisation entfernen möchten.

Um dies zu tun, können Sie das Portal zurücksetzen, wodurch alle gehosteten Ressourcen, die zugeordnet sind, gelöscht werden. Anschließend können Sie das Portal wieder verwenden. Nach dem Rücksetzungsvorgang ist Ihre Portal-URL nicht mehr verfügbar.

Es ist wichtig zu beachten, dass das Zurücksetzen Ihres Portale nicht die Portalkonfiguration oder die in Ihrer Instanz vorhandenen Lösungen entfernt und sie bleiben unverändert.

Sie können ein vollständig konfiguriertes Portal oder ein Portal zurücksetzen, bei dem die Bereitstellung oder Aktualisierung einer Instanz fehlgeschlagen ist.

Um ein konfiguriert Portal zurücksetzen:

1.  Öffnen Sie das [Admin Center für PowerApps-Portale](admin-overview.md).

2.  Öffnen Sie **Portalaktionen** > **Portal zurücksetzen**.

    > [!div class=mx-imgBorder]
    > ![Setzen Sie ein Portal zurück](../media/reset-portal.png "Setzen Sie ein Portal zurück")

3.  Klicken Sie im Bestätigungsfenster auf **Schließen**.

> [!NOTE]
> - Ohne die entsprechenden Berechtigungen einer zugeordneten Azure Active Directory-Anwendung wird ein Fehler angezeigt. Sie müssen den globalen Administrator für die entsprechenden Rechte kontaktieren.
> - Wenn das Portal erfolgreich zurückgesetzt wurde, ändern sich der Portalname und sein Status auf der Registerkarte **Anwendungen** im Admin-Center PowerApps Portale nicht. Beispielsweise wenn der Status Portalname und Portal 1 entsprechend konfiguriert wurden, ändern diese Werte nach dem Zurücksetzen des Portals nicht. Wenn Sie den Portalnamen ändern möchten, können Sie diesen unter **Portaldetails**im Portal Administratorencenter ändern. Allerdings kann der Wert nicht zu nicht konfiguriert zurückgesetzt werden.
> 
> Beachten Sie bitte, dass es wichtig ist, dass der Status des Portals auf der Registerkarte **Anwendungen** nicht den Bereitstellungsstatus darstellt und sich nicht auf das Anliegen des Portals auswirkt. Es wird nur angezeigt, ob Sie je auf das Portaladministrator-Center für den Benutzer über dieses Portal zugegriffen haben oder nicht.

Wenn das Portal nicht ordnungsgemäß bereitgestellt ist, hat es einen Fehlerstatus und der folgende Bildschirm wird angezeigt. Sie können in diesem Fall das Portal auch zurücksetzen, indem Sie **Portal zurücksetzen** auf dem Fehlerbildschirm auswählen.

> [!div class=mx-imgBorder]
> ![Fehler beim Bereitstellen des Portals](../media/provision-portal-error.png "Fehler beim Bereitstellen des Portals")

## <a name="troubleshooting"></a>Problembehandlung

Dieser Abschnitt enthält Informationen zur Problembehandlung während das Portal zurückgesetzt wird.

### <a name="reset-request-could-not-be-submitted"></a>Rücksetzungsanforderung kann nicht gesendet werden

Wenn eine Portalrücksetzungsanforderung nicht gesendet werden kann, wird ein Fehler im folgenden Bild der Ansicht angezeigt. In diesem Fall müssen Sie das Portaladministrator-Center schließen und erneut öffnen und versuchen, das Portal erneut zurückzusetzen. Falls das Problem weiterhin besteht, wenden Sie sich an den Kundensupport von Microsoft.

> [!div class=mx-imgBorder]
> ![Fehler beim Zurücksetzen des Portals](../media/reset-portal-request-error.png "Fehler beim Zurücksetzen des Portals")

### <a name="reset-portal-job-fails"></a>Portalrücksetzung ist fehlgeschlagen

Wenn ein Zurücksetzen des Portals fehlschlägt, wird eine Fehlermeldung mit der die Aktion **Portal zurücksetzen** angezeigt.

> [!div class=mx-imgBorder]
> ![Fehler beim Zurücksetzen des Portals](../media/reset-portal-error.png "Fehler beim Zurücksetzen des Portals")

In der Regel sind diese Fehler vorübergehende und Sie müssen **Portal zurücksetzen** auswählen, um die Reihenfolge neu zu starten. Falls das Problem weiterhin besteht, wenden Sie sich an den Kundensupport von Microsoft.

