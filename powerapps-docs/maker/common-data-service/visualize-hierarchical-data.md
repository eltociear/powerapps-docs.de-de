---
title: Visualisierung hierarchischer Daten mit modellgesteuerten Apps | MicrosoftDocs
description: 'Erfahren Sie, wie hierarchische verknüpfte Daten abgefragt und visualisiert werden'
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
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="visualize-hierarchical-data-with-model-driven-apps"></a>Visualisierung hierarchischer Daten mit modellgesteuerten Apps

> [!NOTE]
> Hierarchische Datenvisualisierungen sind nur für modellgesteuerte Anwendungen verfügbar, die für den **Web** Client konfiguriert sind. Visualisierungen sind nicht für den Client **Einheitliche Schnittstelle** verfügbar. Weitere Informationen: [Erstellen einer modellgesteuerten App mithilfe des App-Designers](../model-driven-apps/create-edit-app.md)

Wenn eine Entität so konfiguriert ist, dass sie eine hierarchische, auf sich selbst verweisende Beziehung hat, können Sie Visualisierungen mit Hilfe dieser Hierarchie konfigurieren. Weitere Informationen: [Definieren und Abfragen von hierarchisch verknüpften Daten](../common-data-service/define-query-hierarchical-data.md)

Zu den Entitäten, die standardmäßig über Visualisierungen verfügen, gehören [Firma](/powerapps/developer/common-data-service/reference/entities/account), [Position](/powerapps/developer/common-data-service/reference/entities/position) und [Benutzer](/powerapps/developer/common-data-service/reference/entities/systemuser). in der Rasteransicht dieser Entitäten können Sie das symbol, das das Hierarchiendiagramm darstellt, links neben dem Datensatznamen finden. Das Hierarchiensymbol ist nicht standardmäßig für alle Datensätze vorhanden. Das Symbol wird für die Datensätze angezeigt, die über die hierarchische Beziehung miteinander verknüpft sind.  
  
 ![Konten mit Hierarchien](media/account-list-with-hierarchy.png)  
  
 Wenn Sie das Hierarchiesymbol auswählen, können Sie die Hierarchie mit der Strukturansicht auf der linken Seite der Kachelansicht auf der rechten Seite anzeigen, wie unten gezeigt:  
  
> [!div class="mx-imgBorder"] 
> ![Kontenstruktur und Kachelansicht](media/hierachy-security-accounts-tile-view.png)  
  
 Einige andere Entitäten können für eine Hierarchie aktiviert werden. Zu diesen Entitäten gehören [Kontakt](/powerapps/developer/common-data-service/reference/entities/contact) und [Team](/powerapps/developer/common-data-service/reference/entities/team). Alle benutzerdefinierten Entitäten können für eine Hierarchie aktiviert werden.  
  
Was Sie beachten müssen, wenn Sie Visualisierungen erstellen:  
  
- Nur eine auf sich selbst verweisende (1: n)-Beziehung pro Entität kann als hierarchisch festgelegt werden. In einer auf sich selbst verweisenden Beziehung müssen die primäre Entität und die verknüpfte Entität vom gleichen Typ sein.  
- Eine Hierarchie oder Visualisierung basiert auf nur einer Entität. Sie können die Firmenhierarchie so darstellen, dass Firmen auf verschiedenen Ebenen gezeigt werden, Sie können jedoch Firmen und Kontakte nicht in derselben Hierarchienvisualisierung anzeigen. 
- Die Maximalanzahl an Feldern, die in einer Kachel angezeigt werden können, ist vier. Wenn Sie einer Schnellerfassung, das für die Kachel-Ansicht verwendet wird, mehr Felder hinzufügen, werden nur die ersten vier Felder angezeigt. 

## <a name="hierarchy-settings"></a>Hierarchieeinstellungen

Um Visualisierungen für eine Hierarchie zu ermöglichen, müssen Sie die Hierarchie mit einem Schnellansichtsformular verbinden. Dies ist nur mit dem Projektmappen-Explorer möglich.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

Die Hierarchieeinstellungen sind einer Entität im Lösungs-Explorer zugeordnet. 

1. Während Sie [Entitäten anzeigen](../common-data-service/create-edit-entities-solution-explorer.md#view-entities), wählen Sie **Hierarchieeinstellungen**.
2. Wenn eine vorhandene Hierarchieeinstellung vorhanden ist, können Sie sie ändern. Andernfalls klicken Sie auf **Neu**, um eine neue zu erstellen.
    
    > [!NOTE]
    > Wenn die Hierarchieeinstellungen nicht vorhanden sind, ist es nicht möglich, eine Hierarchie zu konfigurieren.
    >Es kann nur eine Hierarchieeinstellung geben. 

1. Stellen Sie die Daten in den folgenden Feldern ein:

|Feld|Beschreibung|
|--|--|
|**Name**|*Erforderlich.* Fügen Sie einen eindeutigen Namen für die Hierarchieeinstellungen hinzu. Dies ist in der Regel nur der Name der Entität. Dieser Wert enthält den Präfix des Lösungsherausgebers für die Anpassung.|
|**Standardmäßiges Schnellansichtsformular**|*Erforderlich.* Wählen Sie aus einem vorhandenen Schnellansichtsformular oder wählen Sie **Neu erstellen**, um den Schnellansichtsformular-Editor zu öffnen und ein neues zu erstellen.|
|**Hierarchische Beziehung**|*Erforderlich.* Wenn für die Entität bereits eine hierarchische Beziehung definiert ist, wird hier der Wert gesetzt. Wenn es keinen Wert gibt, wählen Sie **Markieren Sie eine Beziehung als aktiviert für Hierarchien**, um einen Dialog zur Auswahl einer der verfügbaren auf sich selbst verweisenden Beziehungen zu öffnen.|
|**Beschreibung**|Fügen Sie eine Beschreibung des Verwendungszwecks dieser Hierarchie hinzu, damit zukünftige Benutzer, die das System anpassen, verstehen können, warum dies geschehen ist.|
    

Dieselben hierarchischen Einstellungen für Visualisierung werden einmal festgelegt, gelten jedoch sowohl für das Web als auch für mobile Clients. Auf Tablets werden die grafischen Elemente in einem für das kleinere Format geeigneten Format angezeigt. Die anpasbaren Komponenten für hierarchische Visualisierung sind lösungsspezifisch, daher können sie wie jede andere Anpassung zwischen Organisationen transportiert werden. Sie können die Attribute konfigurieren, die in der Visualisierung angezeigt werden, indem Sie eine Schnellerfassung mit dem Formular-Editor verwenden.
  
## <a name="visualization-walk-through"></a>Exemplarische Vorgehensweise Visualisierung

Betrachten wir ein Beispiel der Erstellung der Visualisierung einer benutzerdefinierten Entität. Wir haben eine benutzerdefinierte Entität namens `new_Widget` erstellt, eine (1:N) auf sich selbst verweisende Beziehung `new_new_widget_new_widget` und diese als hierarchisch markiert, wie hier gezeigt.  
  
![Widget-Beziehungsdefinition](media/widget-relationship-definition.png)  
  
Als nächstes haben wir in der Rasteransicht **Hierarchieeinstellungen** die hierarchische Beziehung `new_new_widget_new_widget` gewählt. Im Formular füllten wir die Pflichtfelder aus. Wenn Sie die (1: N)-Beziehung noch nicht als hierarchisch markiert haben, führt Sie der Link im Formular wieder zu dem Beziehungsdefinitionsformular zurück, in dem Sie die Beziehung als hierarchisch markieren können.  

> [!IMPORTANT]
> Jede Entität kann jeweils nur eine hierarchische Beziehung haben. Eine Änderung in eine andere auf sich selbst verweisenden Beziehung kann Konsequenzen haben. Weitere Informationen: [Definieren von hierarchischen Daten](../common-data-service/define-query-hierarchical-data.md#define-hierarchical-data)

> [!div class="mx-imgBorder"] 
> ![Hierarchieeinstellungen](media/hierarchy-settings.png)  
  
Für das **Schnellansichtsformular** erstellten wir ein Schnellerfassung mit der Bezeichnung **Kachelformular für Widget-Hierarchie**. In diesem Formular fügten wir vier Felder für die Anzeige in jeder Kachel hinzu.  

> [!div class="mx-imgBorder"] 
> ![Schnellerfassung für Widget erstellen](media/create-quickform.png)  
  
Nachdem wir die EInrichtung abgeschlossen haben, haben wir zwei Datensätze erstellt: *Standard Widget* und *Premium Widget*. Nachdem das Premium-Widget durch Verwendung des Suchfeldes als Standardwidget festgelegt wurde, zeigte die Rasteransicht `new_Widget` die Hierarchiesymbole, wie unten dargestellt, an:  

> [!div class="mx-imgBorder"] 
> ![Hierarchieraster des Widgets](media/widget-hierarchy-grid.png)  
  
> [!NOTE]
>  Die Hierarchiesymbole erscheinen erst in der Datensatzrasteransicht, wenn die Datensätze über die hierarchische Beziehung miteinander verknüpft sind.  
  
Wenn Sie das Hierarchiesymbol auswählen, wird die `new_Widget`-Hierarchie mit der Strukturansicht auf der linken Seite der Kachelansicht auf der rechten Seite angezeigt und zeigt zwei Datensätze. Jede Kachel enthält vier Felder, die wir im **Kachelformular für Widget-Hierarchie** bereitstellten.  

> [!div class="mx-imgBorder"] 
> ![Struktur- und Kachelansichten des Widgets](media/widget-tree-tiles.png)  

Je nach Ihren Anforderungen können Sie zwischen der Verwendung einer Strukturansicht, die die gesamte Hierarchie anzeigt, und einer Kachelansicht, die eine detaillierte Ansicht eines kleineren Teils der Hierarchie wiedergibt, wählen. Beide Ansichten werden nebeneinander angezeigt. Sie können eine Hierarchie erkunden, indem Sie eine Hierarchiestruktur erweitern und reduzieren. 

### <a name="see-also"></a>Siehe auch 

[Definieren und Abfragen von hierarchiebezogenen Daten](../common-data-service/define-query-hierarchical-data.md)<br />
[Video: Hierarchievisualisierung in](http://www.youtube.com/watch?v=_dGBE6icLNw&index=9&list=PLC3591A8FE4ADBE07)
