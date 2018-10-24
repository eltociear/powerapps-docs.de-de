---
title: Visualisieren hierarchischer Daten mit modellgesteuerten Apps | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie hierarchiebezogene Daten abfragen und visualisieren.
ms.custom: ''
ms.date: 06/02/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.author: matp
manager: kvivek
ms.openlocfilehash: bed8662d7d9475215df8e92490702b68e36574e2
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39688113"
---
# <a name="visualize-hierarchical-data-with-model-driven-apps"></a>Visualisieren hierarchischer Daten mit modellgesteuerten Apps

> [!NOTE]
> Hierarchische Datenvisualisierungen sind nur für modellgesteuerte Apps verfügbar, die für den **Webclient** konfiguriert wurden. Visualisierungen sind nicht für den Client **Einheitliche Oberfläche** verfügbar. Weitere Informationen finden Sie unter [Erstellen einer modellgesteuerten App mithilfe des App-Designers](../model-driven-apps/create-edit-app.md).

Wenn eine Entität so konfiguriert ist, dass sie eine hierarchische selbstreferenzielle Beziehung aufweist, können Sie Visualisierungen mithilfe dieser Hierarchie konfigurieren. Weitere Informationen finden Sie unter [Definieren und Abfragen von hierarchiebezogenen Daten](../common-data-service/define-query-hierarchical-data.md).

Visualisierungen sind standardmäßig für diese Entitäten verfügbar: [Konto](/powerapps/developer/common-data-service/reference/entities/account), [Position](/powerapps/developer/common-data-service/reference/entities/position) und [Benutzer](/powerapps/developer/common-data-service/reference/entities/systemuser). In der Rasteransicht dieser Entitäten sehen Sie links neben dem Datensatznamen das Symbol für das Hierarchiediagramm. Das Hierarchiesymbol ist standardmäßig nicht für alle Datensätze verfügbar. Das Symbol wird für die Datensätze angezeigt, die über die hierarchische Beziehung verknüpft sind.  
  
 ![Konten mit Hierarchien](media/account-list-with-hierarchy.png)  
  
 Wenn Sie das Hierarchiesymbol auswählen, können Sie die Hierarchie mit der Strukturansicht auf der linken Seite und der Kachelansicht auf der rechten Seite anzeigen:  
  
 ![Struktur- und Kachelansicht für „Konto“](media/hierachy-security-accounts-tile-view.png)  
  
 Einige andere Entitäten können für eine Hierarchie aktiviert werden. Dazu gehören [Kontakt](/powerapps/developer/common-data-service/reference/entities/contact) und [Team](/powerapps/developer/common-data-service/reference/entities/team). Alle benutzerdefinierten Entitäten können für eine Hierarchie aktiviert werden.  
  
Wichtige Aspekte beim Erstellen von Visualisierungen:  
  
- Nur eine selbstreferenzielle 1:n-Beziehung pro Entität kann als hierarchisch festgelegt werden. In einer selbstreferenziellen Beziehung müssen die primäre und die verknüpfte Entität vom gleichen Typ sein.  
- Eine Hierarchie bzw. Visualisierung basiert ausschließlich auf einer Entität. Sie können die Kontohierarchie mit Konten auf mehreren Ebenen darstellen, jedoch Konten und Kontakte nicht in der gleichen Hierarchievisualisierung anzeigen. 
- In einer Kachel können maximal vier Felder angezeigt werden. Wenn Sie weitere Felder zur Schnellerfassung hinzufügen, die für die Kachelansicht verwendet wird, werden nur die ersten vier Felder angezeigt. 

## <a name="hierarchy-settings"></a>Hierarchieeinstellungen

Um Visualisierungen für eine Hierarchie zu ermöglichen, müssen Sie die Hierarchie mit einem Schnellansichtsformular verknüpfen. Dies kann nur über den Projektmappen-Explorer erfolgen.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

Die Hierarchieeinstellungen sind einer Entität im Projektmappen-Explorer zugeordnet. 

1. Wählen Sie beim [Anzeigen von Entitäten](../common-data-service/create-edit-entities-solution-explorer.md#view-entities) **Hierarchieeinstellungen** aus.
2. Sie können eine vorhandene Hierarchieeinstellung bearbeiten. Andernfalls klicken Sie auf **Neu**, um eine neue Einstellung zu erstellen.
    
    > [!NOTE]
    > Wenn keine Hierarchieeinstellungen vorhanden sind, ist die Entität nicht in der Lage, eine Hierarchie zu konfigurieren.
    >Es kann nur eine Hierarchieeinstellung geben. 

1. Bestimmen Sie die Daten in den folgenden Feldern:

|Feld|Beschreibung|
|--|--|
|**Name**|*Erforderlich.* Fügen Sie einen eindeutigen Namen für die Hierarchieeinstellungen hinzu. Das ist in der Regel nur der Name der Entität. Dieser Wert enthält das Anpassungspräfix des Lösungsherausgebers.|
|**Standardmäßiges Schnellansichtsformular**|*Erforderlich.* Wählen Sie ein vorhandenes Schnellansichtsformular oder **Neu erstellen** aus, um den Schnellansichtsformular-Editor zu öffnen und ggf. ein neues Formular zu erstellen.|
|**Hierarchische Beziehung**|*Erforderlich.* Wenn für die Entität bereits eine hierarchische Beziehung definiert ist, wird hier der Wert gesetzt. Wenn kein Wert vorliegt, wählen Sie **Markieren Sie eine Beziehung als aktiviert für Hierarchien** aus, um ein Dialogfeld zu öffnen, in dem Sie eine verfügbare selbstreferenzielle Beziehung auswählen.|
|**Description** (Beschreibung)|Fügen Sie eine Beschreibung des Hierarchiezwecks hinzu, damit Benutzer, die das System in Zukunft anpassen, dies nachvollziehen können.|
    

Die gleichen hierarchischen Einstellungen für die Visualisierung werden einmalig festgelegt, gelten jedoch für Web- und mobile Clients. Bei Tablets werden die visuellen Elemente in einem geänderten Format gerendert, das für kleinere Formfaktoren geeignet ist. Die anpassbaren Komponenten für die hierarchische Visualisierung sind lösungsfähig und können daher wie andere Anpassungen zwischen Organisationen übertragen werden. Sie können die Attribute konfigurieren, die in der Visualisierung angezeigt werden, indem Sie über den Formular-Editor eine Schnellerfassung anpassen.
  
## <a name="visualization-walk-through"></a>Visualisierung: exemplarische Vorgehensweise

Sehen wir uns ein Beispiel für das Erstellen einer Visualisierung für eine benutzerdefinierte Entität an. Wir haben eine benutzerdefinierte Entität namens `new_Widget` sowie eine selbstreferenzielle (1:n-)Beziehung `new_new_widget_new_widget` erstellt und diese als hierarchisch markiert, wie hier angezeigt:  
  
![Widget für Beziehungsdefinition](media/widget-relationship-definition.png)  
  
Als Nächstes haben wir in der Rasteransicht **Hierarchieeinstellungen** die hierarchische Beziehung `new_new_widget_new_widget` ausgewählt. Im Formular wurden die Pflichtfelder ausgefüllt. Wenn Sie die 1:n-Beziehung noch nicht als hierarchisch markiert haben, gelangen Sie über den Link im Formular zurück zum Formular zur Beziehungsdefinition, in dem Sie die Beziehung als hierarchisch markieren können.  

> [!IMPORTANT]
> Jede Entität kann jeweils nur eine hierarchische Beziehung haben. Das Ändern in eine andere selbstreferenzielle Beziehung kann Konsequenzen haben. Weitere Informationen finden Sie unter [Definieren hierarchischer Daten](../common-data-service/define-query-hierarchical-data.md#define-hierarchical-data).
  
![Hierarchieeinstellungen](media/hierarchy-settings.png)  
  
Für das **Schnellansichtsformular** haben wir eine Schnellerfassung mit der Bezeichnung **Kachelformular der Widgethierarchie** erstellt. Wir haben diesem Formular vier Felder hinzugefügt, die in einzelnen Kacheln angezeigt werden.  
  
![Erstellen eines Schnellformulars für ein Widget](media/create-quickform.png)  
  
Nachdem wir die Einrichtung abgeschlossen haben, haben wir zwei Datensätze erstellt: *Standardwidget* und *Premiumwidget*. Nachdem Sie das Premiumwidget mit dem Suchfeld zu einem übergeordneten Element des Standardwidgets gemacht haben, zeigt die Rasteransicht `new_Widget` die Hierarchiesymbole an, wie hier veranschaulicht:  
  
![Hierarchieraster des Widgets](media/widget-hierarchy-grid.png)  
  
> [!NOTE]
>  Die Hierarchiesymbole werden erst in der Rasteransicht des Datensatzes angezeigt, wenn die Datensätze über die hierarchische Beziehung verknüpft sind.  
  
Wenn Sie das Hierarchiesymbol auswählen, wird die `new_Widget`-Hierarchie mit der Strukturansicht auf der linken Seite und der Kachelansicht auf der rechten Seite mit zwei Datensätzen angezeigt. Jede Kachel enthält vier Felder, die wir im **Kachelformular der Widgethierarchie** bereitgestellt haben.  
  
![Struktur- und Kachelansicht des Widgets](media/widget-tree-tiles.png)  

Je nach Bedarf können Sie zwischen einer Strukturansicht, die die gesamte Hierarchie anzeigt, und einer Kachelansicht wählen, die einen kleineren Teil der Hierarchie zeigt. Beide Ansichten werden nebeneinander angezeigt. Sie können eine Hierarchie untersuchen, indem Sie eine Hierarchiestruktur erweitern und minimieren. 

### <a name="see-also"></a>Siehe auch 

[Definieren und Abfragen von hierarchiebezogenen Daten](../common-data-service/define-query-hierarchical-data.md)<br />
[Video: Visualisierung von Hierarchien](http://www.youtube.com/watch?v=_dGBE6icLNw&index=9&list=PLC3591A8FE4ADBE07) (in englischer Sprache)