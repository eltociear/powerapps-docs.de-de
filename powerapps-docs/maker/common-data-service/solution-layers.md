---
title: Anzeigen von Lösungsebenen | MicrosoftDocs
description: 'Erfahren Sie, wie Sie Lösungsebenen verwenden können'
keywords: null
ms.date: 04/10/2019
ms.service: powerapps
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 for Customer Engagement (online)
  - Dynamics 365 for Customer Engagement Version 9.x
  - powerapps
ms.assetid: null
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
caps.latest.revision: null
topic-status: Drafting
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="view-solution-layers"></a>Anzeigen von Lösungsebenen
Lösungsebenen ermöglichen es Ihnen, alle Komponentenänderungen anzuzeigen, bei denen im Laufe der Zeit Lösungsänderungen auftreten. Innerhalb einer Lösungsebene können Sie tiefer gehen, um die bestimmten geänderten und nicht geänderten Eigenschaftendetails einer Komponente anzuzeigen. 

Lösungsebenen bieten folgende Vorteile: 
-   Sie zeigen Ihnen die Reihenfolge der von einer Lösung geänderten Komponente an. 
-   Sie zeigen Ihnen alle Eigenschaften einer Komponente in einer bestimmten Lösung, einschließlich der Änderungen an der Komponente. 
-   Kann verwendet werden, um die Probleme bei Abhängigkeit oder Lösungsebenen zu beheben, indem Änderungsdetails für eine Komponente angezeigt werden, die durch eine Lösungsänderung eingeführt wurden.

## <a name="view-the-solution-layers-for-a-component"></a>Zeigen Sie die Lösungsebenen für eine Lösung an
Sie können auf Lösungsebenen aus der Liste der **Komponenten** oder aus dem Dialogfeld **Abhängigkeitsdetails** im Projektmappen-Explorer zugreifen. 

1. Um Lösungsebenen aus der **Komponenten**-Liste anzuzeigen, [Öffnen Sie den Projektmappen-Explorer](../model-driven-apps/advanced-navigation.md#solution-explorer), wählen Sie in der **Komponenten**-Liste eine Komponente, zum Beispiel **Konto**, aus und wählen Sie dann in der Symbolleiste **Lösungsebenen** aus. 

   > [!div class="mx-imgBorder"] 
   > ![](media/solution-layers-toolbar.png "Lösungsebenen-Schaltfläche")

2. Die Lösungsebenenseite wird angezeigt, die jede Ebene für die Komponente anzeigt, z. B. die Kontoentität, die hier anzeigt wird. Dabei steht die aktuelle Ebene oben. Um die Details für eine Lösungsebene anzuzeigen, wählen Sie sie aus. 

   > [!div class="mx-imgBorder"] 
   > ![](media/solution-layers-list.png "Lösungsebenenliste")

3. Im Dialogfeld **Lösungsebene** zeigt die Registerkarte **Geänderte Eigenschaften** nur die Eigenschaften an, die im Rahmen einer bestimmten Lösungsebene geändert wurden. 

   > [!div class="mx-imgBorder"] 
   > ![](media/solution-layers-change-prop.png "Von Lösungsebene geänderte Eigenschaften")

4. Wählen Sie die Registerkarte **Alle Eigenschaften** aus, einschließlich der geänderten unveränderten Eigenschaften für die Lösungsebene. 

   > [!div class="mx-imgBorder"] 
   > ![](media/solution-layers-all-prop.png "Alle Lösungsebeneneigenschaften")

## <a name="see-also"></a>Siehe auch
[Überblick über Lösungen](solutions-overview.md)