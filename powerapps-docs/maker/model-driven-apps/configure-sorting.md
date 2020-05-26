---
title: Sortieren von Datensätzen in einer modellgesteuerten App-Ansicht in Power Apps | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/17/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 25f5aa52-56dc-4be5-884e-9346616f665f
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a89a2c4953f5a78a58ff6717f15a803a7cf58527
ms.sourcegitcommit: 3c6c5594b73abd5ff438d50f3b579d56cef7241c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2020
ms.locfileid: "3285650"
---
# <a name="sort-records-in-a-model-driven-app-view"></a>Sortieren von Datensätzen in einer Modell-angetriebenen App-Ansicht


Wenn Sie eine Ansicht erstellen oder bearbeiten, können die Sortierreihenfolge für aufsteigende oder absteigendes Optionen konfigurieren.

Um die Sortierreihenfolge im Ansichtsdesigner zu ändern, siehe [Eine öffentliche Ansicht in Power Apps](create-edit-views-app-designer.md#create-a-public-view-in-power-apps) erstellen.

## <a name="change-the-sort-order-using-solution-explorer"></a>Ändern der Sortierreihenfolge mit dem Lösungsexplorer

1.  Öffnen Sie [Lösungsexplorer](advanced-navigation.md#solution-explorer), erweitern Sie **Entitäten**, wählen Sie die gewünschte Entität, wählen Sie **Ansichten** und öffnen Sie dann die gewünschte Ansicht.

2.  Im Ansicht-Designer wählen Sie **Sortieren konfigurieren** aus.  

    > [!div class="mx-imgBorder"] 
    > ![Konfigurieren der Sortierung](media/configure-sorting.png "Konfigurieren der Sortierung")
  
3.  Wählen Sie im Dialogfeld **Sortierreihenfolge konfigurieren** in der Liste **Sortieren nach** die Spalte aus, die Sie sortieren möchten. Wählen Sie **Aufsteigende Reihenfolge** oder **Absteigende Reihenfolge** aus.  
  
4.  Wählen Sie **OK** aus, um das Dialogfeld **Sortierreihenfolge konfigurieren** zu schließen. 

    > [!IMPORTANT]
    > Raster in Apps für die einheitliche Benutzeroberfläche übernehmen die Liste der angezeigten Spalten aus dem zugrunde liegenden FetchXML der Ansicht. Wenn das FetchXML, das von Common Data Service zurückgegeben wird, keine Spalte hat, wird diese Spalte nicht angezeigt. Dies steht im Gegensatz zur klassischen Web-Anwendung, wo, wenn eine Spalte nicht in FetchXML, aber in LayoutXML vorhanden ist, eine solche Spalte automatisch zur Liste der angezeigten Spalten hinzugefügt wird. Einheitliche Benuitzeroberfläche Apps verwenden OData direkt mit FetchXML, um Daten vom Server abzurufen.

## <a name="next-steps"></a>Nächste Schritte
[Ansicht erstellen oder bearbeiten](create-edit-views.md)
[FetchXML verwenden, um Daten abzufragen](../../developer/common-data-service/use-fetchxml-construct-query.md)
