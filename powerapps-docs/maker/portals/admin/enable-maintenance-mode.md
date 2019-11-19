---
title: Wartungsmodus für ein Portal aktivieren | MicrosoftDocs
description: 'Erfahren Sie, wie Sie den Wartungsmodus bei Ihrem Portal aktivieren.'
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 07/18/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="maintenance-mode-for-a-portal"></a>Wartungsmodus für ein Portal

[!include[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

Es gibt möglicherweise Zeiten, zu denen Ihre Website planmäßig gewartet wird oder aufgrund eines vorübergehenden Ausfalls nicht erreichbar ist. Wenn ein Kunde bei einer Wartung auf die Website zugreift kann es zu unvorhersehbarem Verhalten und periodischer Nichtverfügbarkeit kommen. 

Als Portaladministrator können Sie das Portal konfigurieren, um Kunden eine korrekte Nachricht anzuzeigen, wenn eine Wartungsaktivität ausgeführt wird (z. B. wenn Lösungspakete aktualisiert werden). Sie können diese Fähigkeit nutzen, indem Sie den Wartungsmodus auf Ihrem Portal aktivieren. Wenn der Wartungsmodus aktiviert wird, wird eine Nachricht angezeigt und die Kunden werden vom Durchsuchen sämtlicher Webseiten außer der `<portal URL>/_services/about` Seite abgehalten.

> [!div class=mx-imgBorder]
> ![Standardseite des Wartungsmodus](../media/default-maint-page.png "Standardseite des Wartungsmodus")

## <a name="enable-maintenance-mode"></a>Wartungsmodus aktivieren

Sie können den Wartungsmodus auf Ihrem Portal aktivieren, um eine einheitliche Nachricht bereitzustellen, anstatt sich mit unvorhersehbarem Verhalten auseinanderzusetzen, wenn die Website planmäßig gewartet wird. Dies bietet Ihren Portalbenutzern ein besseres Erlebnis.

1. Öffnen Sie das [Admin Center für PowerApps-Portale](admin-overview.md).

3. Wechseln Sie zu **Portalaktionen** > **Wartungsmodus aktivieren**.

    > [!div class=mx-imgBorder]
    > ![Aktivieren des Wartungsmodus](../media/enable-maint-mode-button.png "Aktivieren des Wartungsmodus")

4. Geben Sie im Fenster **Wartungsmodus aktivieren** die folgenden Werte ein:
    - **Wählen Sie die bei aktiviertem Wartungsmodus zu verwendende Seite aus**: Wählen Sie einen der folgenden Werte aus:

        - **Standardseite**: Wählen Sie diesen Wert aus, wenn die Standardseite angezeigt werden soll, wenn der Wartungsmodus aktiviert ist. Diese Option ist standardmäßig ausgewählt.

        - **Angepasste Seite**: Wählen Sie diesen Wert aus, wenn eine HTML-Seite angezeigt werden soll, wenn der Wartungsmodus aktiviert ist.

    - **Benutzerdefinierte Seiten-URL**: Dieses Feld wird aktiviert, wenn Sie die Option auswählen, um eine benutzerdefinierte HTML-Seite anzuzeigen. Sie müssen sicherstellen, dass Seiten-URL, die Sie bereitstellen, öffentlich zugänglich ist. Wenn die angegebene HTML-Seite nicht erreicht werden kann, wird die Standardseite mit einem Hinweis an den Administrator angezeigt.

5. Wählen Sie **Aktivieren** aus. Bei aktiviertem Wartungsmodus wird das Portal neu gestartet, und es ist für einige Minuten nicht verfügbar. 

    > [!div class=mx-imgBorder]
    > ![Aktivieren der Wartungsmodus-Einstellungen](../media/enable-maint-mode.png "Aktivieren der Wartungsmodus-Einstellungen")

## <a name="configure-or-disable-maintenance-mode"></a>Wartungsmodus konfigurieren oder deaktivieren

Nachdem Sie den Wartungsmodus für Ihr Portal aktiviert haben, können Sie die Wartungsmodus-Einstellungen aktualisieren und eine andere Seite auswählen.

Sie können außerdem auswählen, dass der Wartungsmodus auf Ihrem Portal deaktiviert wird, wenn die geplante Wartung Ihrer Website abgeschlossen ist. Ihre Portalbenutzer können nun auf alle Webseiten wie gewohnt zugreifen und sie durchsuchen.

1. Öffnen Sie das [Admin Center für PowerApps-Portale](admin-overview.md).

2. Wechseln Sie zu **Portalaktionen** > **Konfigurieren oder Deaktivieren des Wartungsmodus**.

    > [!div class=mx-imgBorder]
    > ![Wartungsmodus konfigurieren](../media/configure-maint-mode-button.png "Wartungsmodus konfigurieren")

3. Ändern Sie die Einstellungen nach Bedarf, und wählen Sie **Aktualisieren** aus. Beispielsweise wählen Sie ggf. aus, die Standardseite anzuzeigen, falls Sie zuvor ausgewählt haben, die benutzerdefinierte Seite anzuzeigen.

4. Wählen Sie **Deaktivieren** aus, um den Wartungsmodus zu deaktivieren. Bei aktualisiertem oder deaktiviertem Wartungsmodus wird das Portal neu gestartet, und es ist für einige Minuten nicht verfügbar.

    > [!div class=mx-imgBorder]
    > ![Aktualisieren der Wartungsmodus-Einstellungen](../media/configure-maint-mode.png "Aktualisieren der Wartungsmodus-Einstellungen")
