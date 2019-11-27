---
title: Anzeigen von Lösungsebenen | MicrosoftDocs
description: Erfahren Sie, wie Sie Lösungsebenen verwenden können
keywords: ''
ms.date: 04/18/2019
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
ms.openlocfilehash: a5b507384b3fdf157aa029ad98d4d4203f624d8f
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2702101"
---
<!--note from editor: Best practice is that H1 title and title in metadata are different.    -->

# <a name="view-solution-layers"></a>Anzeigen von Lösungsebenen
Lösungsebenen ermöglichen es Ihnen, alle Komponentenänderungen anzuzeigen, bei denen im Laufe der Zeit Lösungsänderungen auftreten. Innerhalb einer Lösungsebene können Sie einen Drilldown ausführen, um die bestimmten geänderten und nicht geänderten Eigenschaftendetails einer Komponente anzuzeigen. 

Lösungsebenen: 
-   Sie zeigen Ihnen die Reihenfolge der von einer Lösung geänderten Komponente an. 
-   Sie zeigen Ihnen alle Eigenschaften einer Komponente in einer bestimmten Lösung, einschließlich der Änderungen an der Komponente. 
-   Kann verwendet werden, um die Probleme bei Abhängigkeit oder Lösungsebenen zu beheben, indem Änderungsdetails für eine Komponente angezeigt werden, die durch eine Lösungsänderung eingeführt wurden.

## <a name="view-the-solution-layers-for-a-component"></a>Zeigen Sie die Lösungsebenen für eine Lösung an
Sie können auf Lösungsebenen aus der Liste der **Komponenten** oder aus dem Dialogfeld **Abhängigkeitsdetails** im Projektmappen-Explorer zugreifen. 

<!--note from editor: In step 2 below, does the page display a name at top? If so, use the same capitalization in text. -->

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
