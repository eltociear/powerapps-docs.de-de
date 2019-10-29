---
title: Identifizieren und Beheben von Kundenproblemen mithilfe eines Portals | MicrosoftDocs
description: Erfahren Sie, wie Sie Kunden Probleme mit einem Portal identifizieren und beheben können.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b361efd6a1f44485e9b7337e3e5b3a29c1a826d4
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976183"
---
# <a name="portal-checker"></a>Portal Prüfung

Die Portal Prüfung ist ein Self-Service-Diagnosetool, das von Portaladministratoren verwendet werden kann, um häufige Probleme im Portal zu identifizieren. Die Portal Prüfung hilft Ihnen dabei, Probleme mit Ihrem Portal zu identifizieren, indem Sie verschiedene Konfigurationsparameter betrachten und Vorschläge zur Behebung von Problemen bereitstellt.

Wenn Sie die Portal Prüfung ausführen, werden die Ergebnisse im Abschnitt **Diagnoseergebnisse** in einem Raster Format angezeigt. Das Ergebnis Raster weist die folgenden Spalten auf:

- **Problem**: zeigt das Problem der obersten Ebene eines Kunden an. beispielsweise Leistungsprobleme.
- **Kategorie**: zeigt den Bereich der obersten Ebene an, in dem Probleme kategorisiert werden können. beispielsweise Bereitstellung, Lösungs Upgrade und so weiter.
- **Ergebnis**: zeigt den Status des Problems an. beispielsweise "Error", "Warning" usw.

Standardmäßig werden die Informationen im Raster nach der **Ergebnis** Spalte in der folgenden Reihenfolge sortiert: Error, Warning und Pass.

> [!div class=mx-imgBorder]
> ![Diagnoseergebnisse](../media/diagnostic-results.png "Diagnoseergebnisse")

Sie können ein Problem erweitern, um ausführliche Informationen und Abhilfemaßnahmen anzuzeigen. Wenn für die Entschärfung eine Aktion erforderlich ist, wird eine Schaltfläche angezeigt, mit der die Aktion ausgeführt wird. Sie können auch Feedback geben, ob die Entschärfung nützlich war.

> [!div class=mx-imgBorder]
> ![Erweitern eines Problems in Diagnoseergebnissen](../media/diagnostic-results-issue-expand.png "Erweitern eines Problems in Diagnoseergebnissen")

Falls erforderlich, können Sie die Diagnose Überprüfungen erneut ausführen, wodurch die Ergebnisse mit aktualisierten Daten aktualisiert werden.

> [!NOTE]
> Wenn das Portal ausgeschaltet ist oder das Filtern von IP-Adressen aktiviert ist, werden bestimmte Diagnose Überprüfungen nicht in Ihrem Portal ausgeführt.

Eine Liste der häufigen Probleme, die vom Portal Überprüfungs Tool diagnostiziert werden, finden Sie unter [Allgemeine Portal Probleme, die von der Portal Prüfung diagnostiziert werden, und die bewährten Methoden](https://docs.microsoft.com/dynamics365/customer-engagement/portals/portal-faq).

So führen Sie die Portal Prüfung aus:

1.  Öffnen Sie das [powerapps-Portal Admin Center](admin-overview.md).

2.  Wechseln Sie zu **Run Portal Checker**.

    > [!div class=mx-imgBorder]
    > Portal ![Prüfung ausführen](../media/run-diagnostics.png "Portal") Prüfung ausführen

3.  Wählen Sie **Portal Prüfung ausführen**aus. Die Diagnose Sitzung wird gestartet, und es werden Daten zu den Kundenproblemen gesammelt. Die Ergebnisse werden im Abschnitt **Diagnoseergebnisse** angezeigt.

    > [!div class=mx-imgBorder]
    > ![Diagnoseergebnisse](../media/diagnostic-results.png "Diagnoseergebnisse")

4.  Um die Diagnose Überprüfungen erneut auszuführen, wählen Sie **Ergebnisse aktualisieren**aus.

    > [!div class=mx-imgBorder]
    > ![Aktualisieren der Diagnoseergebnisse](../media/diagnostic-results-refresh.png "Aktualisieren von Diagnoseergebnissen")
