---
title: Aktivieren des Wartungsmodus für ein Portal | MicrosoftDocs
description: Erfahren Sie, wie Sie den Wartungsmodus mit Ihrem Portal aktivieren.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: e53380c39257645e9056a271226b6f7ef8c8c721
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976068"
---
# <a name="maintenance-mode-for-a-portal"></a>Wartungsmodus für ein Portal

Es kann vorkommen, dass Ihre Website eine geplante Wartung ist oder aufgrund eines temporären Ausfalls ausfällt. Wenn ein Kunde während der Wartung auf die Website zugreift, kann es zu unvorhersehbarem Verhalten und zeitweiliger Nichtverfügbarkeit kommen. 

Als Administrator des Portals können Sie das Portal so konfigurieren, dass es bei jedem Eintreten einer Wartungs Aktivität eine korrekte Nachricht für Kunden anzeigt (z. b. "Projektmappenpakete werden aktualisiert"). Sie können diese Funktion nutzen, indem Sie den Wartungsmodus in Ihrem Portal aktivieren. Wenn der Wartungsmodus aktiviert ist, wird eine Meldung angezeigt, und die Kunden sind daran eingeschränkt, Webseiten außer der `<portal URL>/_services/about` Seite zu durchsuchen.

> [!div class=mx-imgBorder]
> Standardmäßige wartungsmodusseite ![(Standard)](../media/default-maint-page.png "")

## <a name="enable-maintenance-mode"></a>Aktivieren des Wartungsmodus

Sie können den Wartungsmodus in Ihrem Portal aktivieren, um eine konsistente Nachricht bereitzustellen, anstatt unvorhersehbares Verhalten zu behandeln, wenn Ihre Website eine geplante Wartung durchläuft. Dadurch erhalten Sie eine bessere Leistung für Ihre Portalbenutzer.

1. Öffnen Sie das [powerapps-Portal Admin Center](admin-overview.md).

3. Wechseln Sie zu den **Portal Aktionen** > aktivieren Sie den **Wartungsmodus**.

    > [!div class=mx-imgBorder]
    > ![Aktivieren des Wartungsmodus]Aktivieren des(../media/enable-maint-mode-button.png "Wartungsmodus")

4. Geben Sie im Fenster **Wartungsmodus aktivieren** die folgenden Werte ein:
    - **Wählen Sie die zu verwendende Seite aus, wenn der Wartungsmodus aktiviert ist**: Wählen Sie einen der folgenden Werte aus:

        - **Standardseite**: Wählen Sie diesen Wert aus, wenn die Standardseite angezeigt werden soll, wenn der Wartungsmodus aktiviert ist. Diese Option ist standardmäßig ausgewählt.

        - **Benutzerdefinierte Seite**: Wählen Sie diesen Wert aus, wenn eine benutzerdefinierte HTML-Seite angezeigt werden soll, wenn der Wartungsmodus aktiviert ist.

    - **URL der benutzerdefinierten Seite**: Dieses Feld ist nur aktiviert, wenn Sie die Option zum Anzeigen einer benutzerdefinierten HTML-Seite auswählen. Sie müssen sicherstellen, dass die von Ihnen bereitgestellte Seiten-URL öffentlich zugänglich ist. Wenn die angegebene HTML-Seite nicht erreicht werden kann, wird die Standardseite mit einer Anmerkung für die Administratoren angezeigt.

5. Wählen Sie **aktivieren**aus. Während der Wartungsmodus aktiviert wird, wird das Portal neu gestartet und ist für einige Minuten nicht verfügbar. 

    > [!div class=mx-imgBorder]
    > ![Aktivieren von Wartungsmoduseinstellungen](../media/enable-maint-mode.png "Aktivieren von Wartungsmodus")

## <a name="configure-or-disable-maintenance-mode"></a>Konfigurieren oder Deaktivieren des Wartungsmodus

Nachdem Sie den Wartungsmodus für Ihr Portal aktiviert haben, können Sie die Wartungsmoduseinstellungen aktualisieren und eine andere Seite auswählen.

Sie können auch den Wartungsmodus in Ihrem Portal deaktivieren, wenn die geplante Wartung Ihrer Website beendet ist. Ihre Portalbenutzer können jetzt wie gewohnt auf alle Webseiten zugreifen und darauf zugreifen.

1. Öffnen Sie das [powerapps-Portal Admin Center](admin-overview.md).

2. Wechseln Sie zu den **Portal Aktionen** > **konfigurieren oder deaktivieren Sie den Wartungsmodus**.

    > [!div class=mx-imgBorder]
    > ![Konfigurieren]des Wartungsmodus(../media/configure-maint-mode-button.png "Konfigurieren des Wartungsmodus")

3. Ändern Sie die Einstellungen nach Bedarf, und wählen Sie **Aktualisieren**aus. Sie können z. b. die Standardseite anzeigen, wenn Sie ausgewählt haben, dass die benutzerdefinierte Seite zuvor angezeigt werden soll.

4. Wählen Sie **Deaktivieren**aus, um den Wartungsmodus zu deaktivieren. Während der Wartungsmodus aktualisiert oder deaktiviert wird, wird das Portal neu gestartet und ist für einige Minuten nicht verfügbar.

    > [!div class=mx-imgBorder]
    > ![Aktualisieren von Wartungsmoduseinstellungen](../media/configure-maint-mode.png "Aktualisieren von Wartungsmodus")

