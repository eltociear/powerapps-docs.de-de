---
title: Kundenprobleme mit einem Portal identifizieren und beheben | MicrosoftDocs
description: Erfahren Sie, wie Sie Kundenprobleme mit einem Portal identifizieren und beheben können.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/24/2020
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: bbc5cc51fceadb5dfb836ca36483002f6537620b
ms.sourcegitcommit: 943672dad0041d3bab25b44cd8c4d25e88f39b93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/25/2020
ms.locfileid: "3289344"
---
# <a name="portal-checker"></a>Portalprüfer

Der Portal-Checker ist ein Self-Service-Diagnosewerkzeug, das von Portaladministratoren verwendet werden kann, um häufige Probleme in ihrem Portal zu identifizieren. Der Portal Checker hilft bei der Identifizierung von Problemen mit einem Portal, indem er verschiedene Konfigurationsparameter betrachtet und Vorschläge zu deren Behebung macht.

Wenn Sie den Portal-Checker ausführen, werden die Ergebnisse im Abschnitt **Diagnosedaten** in einem Rasterformat angezeigt. Das Ergebnistabelle hat die folgenden Spalten:

- **Problem:** Zeigt das oberste Problem eines Kunden an, z. B. Leistungsproblem.
- **Kategorie**: Zeigt den Bereich der obersten Ebene an, in dem Probleme kategorisiert werden können, z.B. Bereitstellung oder Lösungs-Upgrade.
- **Ergebnis**: Zeigt den Status der Ausgabe an, z.B. Fehler oder Warnung.

Standardmäßig werden die Informationen im Raster nach der Spalte **Ergebnis** in dieser Reihenfolge sortiert: Fehler, Warnung und Übergabe.

> [!div class=mx-imgBorder]
> ![Diagnoseergebnisse](../media/diagnostic-results.png "Diagnoseergebnisse")

Sie können ein Problem erweitern, um detaillierte Informationen und Schritte zur Fehlerbehebung anzuzeigen. Wenn die Abhilfe eine Maßnahme erfordert, sehen Sie eine Schaltfläche, die die Maßnahme ausführt. Sie können auch Feedback darüber geben, ob die Maßnahme sinnvoll war.

> [!div class=mx-imgBorder]
> ![Erweitern eines Problems in den Diagnoseergebnissen](../media/diagnostic-results-issue-expand.png "Erweitern eines Problems in den Diagnoseergebnissen")

Bei Bedarf können Sie die Diagnoseprüfungen erneut durchführen, wodurch die Ergebnisse mit aktualisierten Daten aktualisiert werden.

> [!NOTE]
> Wenn das Portal deaktiviert oder die IP-Adressfilterung aktiviert ist, werden bestimmte Diagnoseprüfungen auf Ihrem Portal nicht durchgeführt.

Eine Liste der häufigsten Probleme, die vom Portalprüfer-Tool diagnostiziert wurden, finden Sie unter [Allgemeine Probleme im Portal, die vom Portalprüfer diagnostiziert wurden, und deren bewährte Verfahren](https://docs.microsoft.com/dynamics365/customer-engagement/portals/portal-faq).

Um den Portal-Checker auszuführen:

1.  Öffnen Sie das [Admin Center für Power Apps-Portale](admin-overview.md).

2.  Gehen Sie zu **Portalprüfung ausführen**.

    > [!div class=mx-imgBorder]
    > ![Portalprüfung ausführen](../media/run-diagnostics.png "Portalprüfung ausführen")

3.  **Portalprüfung ausführen** auswählen. Die Diagnosesitzung wird gestartet und sammelt Daten über die Kundenprobleme. Die Ergebnisse werden im Abschnitt **Diagnoseergebnisse** angezeigt.

    > [!div class=mx-imgBorder]
    > ![Diagnoseergebnisse](../media/diagnostic-results.png "Diagnoseergebnisse")

4.  Um die Diagnoseprüfungen erneut durchzuführen, wählen Sie **Ergebnisse aktualisieren**.

    > [!div class=mx-imgBorder]
    > ![Diagnosedaten aktualisieren](../media/diagnostic-results-refresh.png "Diagnosedaten aktualisieren")
