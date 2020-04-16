---
title: Lösungsebenen | MicrosoftDocs
description: Erfahren Sie, wie Sie Lösungsebenen verwenden können
keywords: ''
ms.date: 02/05/2020
ms.service: powerapps
ms.custom: ''
ms.topic: article
ms.assetid: ''
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: ''
topic-status: Drafting
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1b5d71f8683b5cb86f79d90540dcf5aa99f6415d
ms.sourcegitcommit: a02b20113164acb11955d27ef4ffa421ee0fba9d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "3114220"
---
# <a name="solution-layers"></a>Lösungsebenen

Verwaltete und nicht verwaltete Lösungen existieren auf verschiedenen Ebenen innerhalb einer Common Data Service-Umgebung. In Common Data Service gibt es zwei verschiedene Ebenen:  
- Nicht verwaltete Ebene. Auf dieser Ebene sind alle importierten nicht verwalteten Lösungen und nicht verwalteten Anpassungen vorhanden. Die nicht verwaltete Ebene ist eine einzelne Ebene.  
- Verwaltete Ebene. Auf dieser Ebene sind alle importierten verwalteten Lösungen und die Systemlösung vorhanden. Wenn mehrere verwaltete Lösungen installiert werden, befindet sich die zuletzt installierte über der zuvor installierten verwalteten Lösung. Dies bedeutet, dass die zweite installierte Lösung die zuvor installierte anpassen kann. Wenn zwei verwaltete Lösungen widersprüchliche Definitionen haben, lautet das Laufzeitverhalten entweder „Letzter gewinnt“ oder es wird eine Zusammenführungslogik implementiert.  Wenn Sie eine verwaltete Lösung deinstallieren, wird die verwaltete Lösung darunter wirksam. Wenn Sie die verwaltete Lösung deinstallieren, wird das innerhalb der Systemlösung definierte Standardverhalten angewendet. Die Basis der verwalteten Ebene ist die Systemebene. Die Systemebene enthält die Entitäten und Komponenten, die für das Funktionieren der Plattform erforderlich sind. 

![Lösungsebenen](media/solution-layers.png)

## <a name="solution-merge-behavior"></a>Lösungszusammenführungsverhalten
Wenn Sie die Installation Ihrer verwalteten Lösung zur Verteilung vorbereiten, denken Sie daran, dass eine Umgebung mehrere Lösungen installiert haben kann oder dass andere Lösungen in der Zukunft installiert werden können. Erstellen Sie eine Lösung, die erfolgreich bewährten Praktiken folgt, so dass Ihre Lösung nicht andere Lösungen behindert.

Die Prozesse, die von Common Data Service verwendet werden, um Anpassungen zusammenzuführen, legt den Fokus auf die Aufrechterhaltung der Funktionalität der Lösung. Während alle Anstrengungen unternommen werden, um die Darstellung zu wahren, können Inkompatibilitäten zwischen Anpassungen es erforderlich machen, dass die gesteuerte Endpunktauflösung gewisse Darstellungsdetails zugunsten der Anpassungsfunktionalität ändert. Weitere Informationen: [Verstehen, wie verwaltete Lösungen zusammengeführt werden](../../developer/common-data-service/understand-managed-solutions-merged.md)

## <a name="view-the-solution-layers-for-a-component"></a>Zeigen Sie die Lösungsebenen für eine Lösung an
Die Lösungsebenen ermöglichen es Ihnen, alle Komponentenänderungen anzuzeigen, bei denen im Laufe der Zeit Lösungsänderungen auftreten. Innerhalb einer Lösungsebene können Sie einen Drilldown ausführen, um die bestimmten geänderten und nicht geänderten Eigenschaftendetails einer Komponente anzuzeigen. Sie können auf Lösungsebenen aus der Liste der **Komponenten** oder aus dem Dialogfeld **Abhängigkeitsdetails** im Projektmappen-Explorer zugreifen. 

Die Lösungsebenen bieten: 
-   Sie zeigen Ihnen die Reihenfolge der von einer Lösung geänderten Komponente an. 
-   Sie zeigen alle Eigenschaften einer Komponente in einer bestimmten Lösung, einschließlich der Änderungen an der Komponente. 
-   Kann verwendet werden, um die Probleme bei Abhängigkeit oder Lösungsebenen zu beheben, indem Änderungsdetails für eine Komponente angezeigt werden, die durch eine Lösungsänderung eingeführt wurden.

1. Um die Lösungsebenen aus der Liste **Komponenten** anzuzeigen, öffnen Sie den [Projektmappen-Explorer](../model-driven-apps/advanced-navigation.md#solution-explorer). In der Liste **Komponenten** wählen Sie eine Komponente aus, zum Beispiel **Firma**, und wählen Sie dann die Option **Lösungsebenen** in der Symbolleiste aus. 

   > [!div class="mx-imgBorder"] 
   > ![Lösungsebenen-Schaltfläche](media/solution-layers-toolbar.png "Lösungsebenen-Schaltfläche")

2. Die Seite mit der Lösungsebene wird angezeigt. Sie zeigt jede Ebene für die Komponente an, z. B. die Entität **Firma**, die hier anzeigt wird. Dabei steht die aktuelle Ebene oben. Um die Details für eine Lösungsebene anzuzeigen, wählen Sie sie aus. 

   > [!div class="mx-imgBorder"] 
   > ![Lösungsebenenliste](media/solution-layers-list.png "Lösungsebenenliste")

3. Im Dialogfeld **Lösungsebene** zeigt die Registerkarte **Geänderte Eigenschaften** nur die Eigenschaften an, die im Rahmen einer bestimmten Lösungsebene geändert wurden. 

   > [!div class="mx-imgBorder"] 
   > ![Von Lösungsebene geänderte Eigenschaften](media/solution-layers-change-prop.png "Von Lösungsebene geänderte Eigenschaften")

4. Wählen Sie die Registerkarte **Alle Eigenschaften** aus, einschließlich der geänderten unveränderten Eigenschaften für die Lösungsebene. 

   > [!div class="mx-imgBorder"] 
   > ![Alle Lösungsebeneneigenschaften](media/solution-layers-all-prop.png "Alle Lösungsebeneneigenschaften")

### <a name="see-also"></a>Siehe auch
[Überblick über Lösungen](solutions-overview.md)
