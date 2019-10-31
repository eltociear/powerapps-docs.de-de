---
title: Kundenprobleme mit einem Portal identifizieren und beheben | MicrosoftDocs
description: 'Erfahren Sie, wie Sie Kundenprobleme mit einem Portal identifizieren und beheben können.'
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="portal-checker"></a>Portalprüfer

[!include[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

Der Portal-Checker ist ein Self-Service-Diagnosewerkzeug, das von Portaladministratoren verwendet werden kann, um häufige Probleme in ihrem Portal zu identifizieren. Der Portalprüfer hilft Ihnen, Probleme mit Ihrem Portal zu identifizieren, indem er sich verschiedene Konfigurationsparameter ansieht und Vorschläge zur Behebung gibt.

Wenn Sie den Portal-Checker ausführen, werden die Ergebnisse im Abschnitt **Diagnosedaten** in einem Rasterformat angezeigt. Das Ergebnistabelle hat die folgenden Spalten:

- **Problem:** Zeigt das oberste Problem eines Kunden an, z. B. Leistungsproblem.
- **Kategorie:** Zeigt den obersten Bereich an, in dem Probleme kategorisiert werden können, z. B. Provisionierung, Lösungsupgrade usw.
- **Ergebnis:** Zeigt den Status des Problems an, z. B. Fehler, Warnung usw.

Standardmäßig werden die Informationen im Raster nach der Spalte **Ergebnis** in dieser Reihenfolge sortiert: Fehler, Warnung und Übergabe.

> [!div class=mx-imgBorder]
> ![Diagnoseergebnisse](../media/diagnostic-results.png "Diagnoseergebnisse")

Sie können ein Problem erweitern, um detaillierte Informationen und Schritte zur Fehlerbehebung anzuzeigen. Wenn die Abhilfe eine Maßnahme erfordert, sehen Sie eine Schaltfläche, die die Maßnahme ausführt. Sie können auch Feedback darüber geben, ob die Maßnahme sinnvoll war.

> [!div class=mx-imgBorder]
> ![Erweitern eines Problems in den Diagnoseergebnissen](../media/diagnostic-results-issue-expand.png "Erweitern eines Problems in den Diagnoseergebnissen")

Bei Bedarf können Sie die Diagnoseprüfungen erneut durchführen, wodurch die Ergebnisse mit aktualisierten Daten aktualisiert werden.

> [!NOTE]
> Wenn das Portal deaktiviert oder die IP-Adressfilterung aktiviert ist, werden bestimmte Diagnoseprüfungen auf Ihrem Portal nicht durchgeführt.

Eine Liste der häufigsten Probleme, die vom Portalprüfer-Tool diagnostiziert wurden, finden Sie unter [Allgemeine Probleme im Portal, die vom Portalprüfer diagnostiziert wurden, und deren bewährte Verfahren](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/portal-faq).

Um den Portal-Checker auszuführen:

1.  Öffnen Sie das [Admin Center für PowerApps-Portale](admin-overview.md).

2.  Gehen Sie zu **Portalprüfung ausführen**.

    > [!div class=mx-imgBorder]
    > ![Portal-Checker ausführen](../media/run-diagnostics.png "Portal-Checker ausführen")

3.  **Portalprüfung ausführen** auswählen. Die Diagnosesitzung wird gestartet und sammelt Daten über die Kundenprobleme. Die Ergebnisse werden im Abschnitt **Diagnoseergebnisse** angezeigt.

    > [!div class=mx-imgBorder]
    > ![Diagnoseergebnisse](../media/diagnostic-results.png "Diagnoseergebnisse")

4.  Um die Diagnoseprüfungen erneut durchzuführen, wählen Sie **Ergebnisse aktualisieren**.

    > [!div class=mx-imgBorder]
    > ![Diagnosedaten aktualisieren](../media/diagnostic-results-refresh.png "Diagnosedaten aktualisieren")
