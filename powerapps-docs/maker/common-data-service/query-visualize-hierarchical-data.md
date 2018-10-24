---
title: Abfragen und Visualisieren von hierarchiebezogenen Daten mit PowerApps | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie hierarchiebezogene Daten abfragen und visualisieren.
ms.custom: ''
ms.date: 06/20/2018
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
ms.assetid: 0cf62817-5ff5-40bb-ad17-e1f6b0921720
caps.latest.revision: 42
ms.author: matp
manager: kvivek
ms.openlocfilehash: ec45f43266c1920d05301c92bdd67838b40b7734
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39683082"
---
# <a name="query-and-visualize-hierarchically-related-data"></a>Abfragen und Visualisieren von hierarchiebezogenen Daten

Sie können wertvolle Geschäftsinformationen gewinnen, indem Sie hierarchiebezogene Daten visualisieren. Die hierarchischen Modellierungs- und Visualisierungsfunktionen bieten Ihnen eine Reihe von Vorteilen:  
  
-   Anzeigen und Untersuchen von komplexen hierarchischen Informationen  
  
-   Anzeigen von Key Performance Indicators (KPIs) in der kontextbezogenen Ansicht einer Hierarchie  
  
-   Visuelles Analysieren von wichtigen Informationen über das Web und die Tablets  
  
Für einige Entitäten wie Firma und Benutzer werden integrierte Visualisierungen bereitgestellt. Andere Entitäten, einschließlich benutzerdefinierter Entitäten, können für eine Hierarchie aktiviert werden, und Sie können Visualisierungen für diese erstellen. Je nach Bedarf können Sie zwischen einer Strukturansicht, die die gesamte Hierarchie anzeigt, oder einer Kachelansicht wählen, die einen kleineren Teil der Hierarchie zeigt. Beide Ansichten werden nebeneinander angezeigt. Sie können eine Hierarchie untersuchen, indem Sie eine Hierarchiestruktur erweitern und reduzieren. Die gleichen hierarchischen Einstellungen für die Visualisierung werden einmal festgelegt, gelten jedoch für Web- und mobile Clients. Bei Tablets werden die visuellen Elemente in einem geänderten Format gerendert, das für kleinere Formfaktoren geeignet ist. Die anpassbaren Komponenten für die hierarchische Visualisierung sind lösungsfähig und können daher wie andere Anpassungen zwischen Organisationen übertragen werden. Sie können die Attribute konfigurieren, die in der Visualisierung angezeigt werden, indem Sie über den Formular-Editor eine Schnellerfassung anpassen. Das Schreiben von Code ist nicht erforderlich.  
  
<a name="BKMK_Querydata"></a>   
## <a name="query-hierarchical-data"></a>Abfragen von hierarchischen Daten  
 Bei Common Data Service für Apps werden hierarchische Datenstrukturen durch auf sich selbst verweisende 1:n-Beziehungen der verknüpften Datensätze unterstützt. In der Vergangenheit mussten Sie zum Anzeigen hierarchischer Daten iterativ die verknüpften Datensätze abfragen. Derzeit können Sie die verknüpften Daten als Hierarchie in einem Schritt abfragen. Mit der Logik **Unter** und **Nicht unter** können Sie Datensätze abfragen. Die hierarchischen Operatoren **Unter** und **Nicht unter** werden in der erweiterten Suche und im Workflow-Editor verfügbar gemacht. Weitere Informationen zur Verwendung dieser Operatoren finden Sie unter [Konfigurieren von Workflowphasen und -schritten](/flow/configure-workflow-steps). Weitere Informationen zur erweiterten Suche finden Sie unter [Erstellen, Bearbeiten oder Speichern einer erweiterten Suche](https://docs.microsoft.com/dynamics365/customer-engagement/basics/save-advanced-find-search).  
  
 Die folgenden Beispiele veranschaulichen verschiedene Szenarien zum Abfragen von Hierarchien:  
  
 Abfragen der Firmenhierarchie  
  
 ![Abfragen von Firmen in der Firmenhierarchie](media/query-accounts.png "Abfragen von Firmen in der Firmenhierarchie")  
  
 Abfragen der Firmenhierarchie, einschließlich der damit verbundenen Aktivitäten  
  
 ![Abfragen von verknüpften Aktivitäten der Firma](media/query-account-related-activities.png "Abfragen von verknüpften Aktivitäten der Firma")  
  
 Abfragen der Firmenhierarchie, einschließlich der damit verbundenen Verkaufschancen  
  
 ![Abfragen von verknüpften Verkaufschancen einer Firma](media/query-account-related-opportunities.png "Abfragen von verknüpften Verkaufschancen einer Firma")  
  
 Um die Daten als Hierarchie abzufragen, müssen Sie auf sich selbst verweisende 1:n-Beziehungen der Entität als hierarchisch festlegen. Gehen Sie zum Aktivieren der Hierarchie wie folgt vor:  
  
1.  Öffnen Sie den [Lösungs-Explorer](../model-driven-apps/advanced-navigation.md#solution-explorer). 
  
2.  Wählen Sie die gewünschte Entität aus, klicken Sie auf **1:n-Beziehungen**, und wählen Sie dann eine 1:n-Beziehung aus. 

3.  Legen Sie in der **Beziehungsdefinition** für **Hierarchisch** die Einstellung **Ja** fest.  
  
> [!NOTE]
> - Einige integrierte 1:n-Beziehungen sind nicht anpassbar. Dadurch wird verhindert, dass diese Beziehungen als hierarchisch festgelegt werden.  
> - Sie können eine hierarchische Beziehung für die Systembeziehungen angeben, die auf sich selbst verweisen. Hierzu zählen die auf sich selbst verweisenden 1:n-Beziehungen des Systemtyps, wie etwa die Beziehung „contact_master_contact“.  
  
<a name="BKMK_Visualizedata"></a>   
## <a name="visualize-hierarchical-data"></a>Visualisieren von hierarchischen Daten  
 Die Systementitäten, die über integrierte Visualisierungen verfügen, enthalten `Account`, `Position`, `Product` und `User`. In der Rasteransicht dieser Entitäten können Sie links neben dem Datensatznamen das Symbol für das Hierarchiediagramm sehen. Das Hierarchiesymbol ist in der Standardeinstellung nicht für alle Datensätze vorhanden. Das Symbol wird für die Datensätze angezeigt, die über einen übergeordneten Datensatz, einen untergeordneten Datensatz oder über beides verfügen.  
  
 ![Aktive Firmen](media/cust-hs-active-account.png "Aktive Firmen")  
  
 Wenn Sie das Hierarchiesymbol auswählen, können Sie die Hierarchie mit der Strukturansicht auf der linken Seite und der Kachelansicht auf der rechten Seite sehen. Dies wird nachfolgend dargestellt:  
  
 ![Firmenstruktur und Kachelansicht](media/hierachy-security-accounts-tile-view.png "Firmenstruktur und Kachelansicht")  
  
 Einige andere integrierte Systementitäten können für eine Hierarchie aktiviert werden. Zu diesen Entitäten zählen `Case`, `Contact`, `Opportunity`, `Order`, `Quote`, `Campaign` und `Team`. Alle benutzerdefinierten Entitäten können für eine Hierarchie aktiviert werden.  
  
> [!TIP]
>  Wenn eine Entität für eine Hierarchie aktiviert werden kann, gehen Sie wie folgt vor:  
>  Erweitern Sie im Lösungs-Explorer die gewünschte Entität. Die Entitätskomponente mit dem Namen **Hierarchieeinstellungen** wird angezeigt. Die Entitäten, die für eine Hierarchie nicht aktiviert werden können, verfügen nicht über diese Komponente, ausgenommen die Dynamics 365 Customer Engagement-Entität „Vertriebsgebiet“. Obwohl **Hierarchieeinstellungen** für die Entität „Vertriebsgebiet“ angezeigt wird, kann die Entität nicht für eine Hierarchie aktiviert werden.  
  
 Wichtige Punkte bei der Erstellung von Visualisierungen:  
  
-   Nur eine auf sich selbst verweisende 1:n-Beziehung pro Entität kann als hierarchisch festgelegt werden. In dieser Beziehung müssen die primäre Entität und die verknüpfte Entität desselben Typs sein, z.B. account_parent_account oder new_new_widget_new_widget.  
  
-   Derzeit basiert eine Hierarchie oder Visualisierung ausschließlich auf einer Entität. Sie können die Firmenhierarchie mit Firmen auf mehreren Ebenen darstellen, jedoch Firmen und Kontakte nicht in der gleichen Hierarchievisualisierung anzeigen.  
  
-   Die maximale Anzahl von Feldern, die in einer Kachel angezeigt werden können, beträgt 4. Wenn Sie weitere Felder zur Schnellerfassung hinzufügen, die für die Kachelansicht verwendet werden, werden nur die ersten vier Felder angezeigt.  
  
### <a name="visualization-example"></a>Beispiel für eine Visualisierung  
 Sehen wir uns ein Beispiel für das Erstellen einer Visualisierung für eine benutzerdefinierte Entität an. Wir haben eine benutzerdefinierte Entität namens „new_Widget“ und eine auf sich selbst verweisende 1:n-Beziehung **new_new_widget_new_widget** erstellt und sie als hierarchisch markiert, wie nachfolgend gezeigt wird.  
  
 ![Definition einer Widgetbeziehung](media/widget-relationship-definition.png "Definition einer Widgetbeziehung")  
  
 Als Nächstes haben wir in der Rasteransicht **Hierarchieeinstellungen** die hierarchische Beziehung **new_new_widget_new_widget** ausgewählt. Im Formular haben wir die Pflichtfelder ausgefüllt. Wenn Sie die 1:n-Beziehung noch nicht als hierarchisch markiert haben, leitet Sie der Link im Formular wieder zurück zum Formular zur Beziehungsdefinition weiter, in dem Sie die Beziehung als hierarchisch markieren können.  
  
 Für das **Schnellansichtsformular** haben wir eine Schnellerfassung mit der Bezeichnung **Kachelformular der Widgethierarchie** erstellt. Bei diesem Formular haben wir vier Felder hinzugefügt, die in einzelnen Kacheln angezeigt werden.  
  
 ![Erstellen einer Schnellerfassung für das Widget](media/create-quickf-orm.png "Erstellen einer Schnellerfassung für das Widget")  
  
 Nachdem wir die Einrichtung abgeschlossen haben, haben wir zwei Datensätze erstellt: das Standard-Widget und das Premium-Widget. Nachdem Sie das Premium-Widget mit dem Suchfeld zu einem übergeordneten Element des Standard-Widgets gemacht haben, hat die Rasteransicht „new_Widget“ die Hierarchiesymbole angezeigt. Dies wird nachfolgend veranschaulicht:  
  
 ![Hierarchieraster des Widgets](media/widget-hierarchy-grid.png "Hierarchieraster des Widgets")  
  
> [!TIP]
>  Die Hierarchiesymbole werden erst in der Rasteransicht des Datensatzes angezeigt, wenn die Datensätze in der Beziehung aus über- und untergeordneten Elementen miteinander verbunden werden.  
  
 Durch Klicken auf das Hierarchiesymbol wird die new_Widget-Hierarchie mit der Strukturansicht auf der linken Seite und der Kachelansicht auf der rechten Seite mit zwei Datensätzen angezeigt. Jede Kachel enthält vier Felder, die wir im **Kachelformular der Widgethierarchie** bereitgestellt haben.  
  
 ![Struktur- und Kachelansichten des Widgets](media/widget-tree-tiles.png "Struktur- und Kachelansichten des Widgets")  
  
## <a name="see-also"></a>Siehe auch  
 [Video: Modellierung hierarchischer Sicherheitsmodelle](http://www.youtube.com/watch?v=kx5So32DrCo&index=10&list=PLC3591A8FE4ADBE07)  (in englischer Sprache)  
 [Video: Visualisierung von Hierarchien](http://www.youtube.com/watch?v=_dGBE6icLNw&index=9&list=PLC3591A8FE4ADBE07) (in englischer Sprache)
