---
title: Hierarchische Daten mit PowerApps abfragen und visualisieren | MicrosoftDocs
description: 'Erfahren Sie, wie hierarchische verknüpfte Daten abgefragt und visualisiert werden'
ms.custom: ''
ms.date: 06/20/2018
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
ms.assetid: 0cf62817-5ff5-40bb-ad17-e1f6b0921720
caps.latest.revision: 42
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="query-and-visualize-hierarchically-related-data"></a>Hierarchiebezogene Daten abfragen und visualisieren

Sie können wertvolle Unternehmenseinblicke erhalten, indem Sie hierarchisch verknüpften Daten darstellen. Die hierarchischen Modellierungs- und Visualisierungsfähigkeiten bieten Ihnen eine Reihe von Vorteilen:  
  
-   Anzeigen und Durchsuchen komplexer hierarchischer Informationen.  
  
-   Anzeigen von Key Performance Indicators (KPIs) in der Kontextansicht einer Hierarchie.  
  
-   Visuelles Analysieren wichtiger Informationen über das Internet und die Tablets hinweg.  
  
Für einige Entitäten, wie Firmen und Benutzer, werden die Visualisierungen standardmäßig zur Verfügung gestellt. Andere Entitäten, einschließlich benutzerdefinierter Entitäten, können für eine Hierarchie aktiviert werden, und Sie können die Visualisierungen für diese erstellen. Je nach Ihren Anforderungen können Sie zwischen der Verwendung einer Strukturansicht, die die gesamte Hierarchie anzeigt, und einer Kachelansicht, die eine detaillierte Ansicht eines kleineren Teils der Hierarchie wiedergibt, wählen. Beide Ansichten werden nebeneinander angezeigt. Sie können eine Hierarchie erkunden, indem Sie eine Hierarchiestruktur erweitern und reduzieren. Dieselben hierarchischen Einstellungen für Visualisierung werden einmal festgelegt, gelten jedoch sowohl für das Web als auch für mobile Clients. Auf Tablets werden die grafischen Elemente in einem für das kleinere Format geeigneten Format angezeigt. Die anpasbaren Komponenten für hierarchische Visualisierung sind lösungsspezifisch, daher können sie wie jede andere Anpassung zwischen Organisationen transportiert werden. Sie können die Attribute konfigurieren, die in der Visualisierung angezeigt werden, indem Sie eine Schnellerfassung mit dem Formular-Editor verwenden. Es ist nicht erforderlich, Code zu schreiben.  
  
<a name="BKMK_Querydata"></a>   
## <a name="query-hierarchical-data"></a>Abfragen von hierarchischen Daten  
 Mit Common Data Service werden hierarchische Datenstrukturen durch auf sich selbst verweisende Eins-zu-Viele (1: n)-Beziehungen der verknüpften Datensätze unterstützt. In der Vergangenheit mussten Sie die verknüpften Datensätze iterativ abfragen, um hierarchische Daten anzuzeigen. Jetzt können Sie verknüpften Daten in einem Schritt als Hierarchie abfragen. Sie können nach Entitätsdatensätzen abfragen, indem Sie die **Unter** und **Nicht Unter**-Logik verwenden. Die hierarchischen Operatoren **Unter** und **Nicht unter** werden in der erweiterten Suche und im Workfloweditor verfügbar gemacht. Weitere Informationen zum Verwenden dieser Operatoren finden Sie unter [Konfigurieren von Workflowschritten](/flow/configure-workflow-steps). Weitere Information zur erweiterten Suche finden Sie unter [Erstellen, Bearbeiten oder Speichern einer erweiterten Suche](https://docs.microsoft.com/dynamics365/customer-engagement/basics/save-advanced-find-search).  
  
 Die folgenden Beispiele illustrieren verschiedene Szenarien für das Abfragen von Hierarchien:  
  
 Firmenhierarchie abfragen  
  
 ![Abfragen von Firmen in der Firmenhierarchie](media/query-accounts.png "Abfragen von Firmen in der Firmenhierarchie")  
  
 Firmenhierarchie abfragen, einschließlich verwandter Aktitvitäten  
  
 ![Aktivitäten zur abgefragten Firma](media/query-account-related-activities.png "Aktivitäten zur abgefragten Firma")  
  
 Firmenhierarchie abfragen, einschließlich verwandter Geschäftschancen  
  
 ![Verkaufschancen zur abgefragten Firma](media/query-account-related-opportunities.png "Verkaufschancen zur abgefragten Firma")  
  
 Um die Daten als Hierarchie abzufragen, müssen Sie die auf sich selbst verweisenden Eins-zu-Viele (1:N)-Beziehungen als hierarchisch festlegen. So aktivieren Sie die Hierarchie  
  
1.  Öffnen Sie den [Lösungs-Explorer](../model-driven-apps/advanced-navigation.md#solution-explorer). 
  
2.  Wählen Sie die gewünschte Entität aus, wählen Sie **1:n-Beziehungen** aus, und wählen Sie dann eine (1:n)-Beziehung aus. 

3.  In **Beziehungsdefinition** legen Sie **Hierarchisch** auf **Ja** fest.  
  
> [!NOTE]
> - Einige der standardmäßigen (1:N)-Beziehungen können nicht angepasst werden. Dieses hindert Sie, diese Beziehungen als hierarchisch festzulegen.  
> - Sie können eine hierarchische Beziehung für die auf sich selbst verweisenden Beziehungen des Systems festlegen. Hierzu zählen die auf sich selbst verweisenden 1:n-Beziehungen vom Systemtyp, beispielsweise die "contact_master_contact"-Beziehung.  
  
<a name="BKMK_Visualizedata"></a>   
## <a name="visualize-hierarchical-data"></a>Visualisieren von hierarchischen Daten  
 Die Systementitäten, für die Visualisierungen standardmäßig verfügbar sind, umfassen: `Account`, `Position`, `Product` und `User`. in der Rasteransicht dieser Entitäten können Sie das symbol, das das Hierarchiendiagramm darstellt, links neben dem Datensatznamen finden. Das Hierarchiensymbol ist nicht standardmäßig für alle Datensätze vorhanden. Das symbol wird für die Datensätze angezeigt, die einen übergeordneten Datensatz, einen untergeordneten Datensatz oder beides haben.  
 
 > [!div class="mx-imgBorder"] 
 > ![Aktive Firmen](media/cust-hs-active-account.png "Aktive Firmen")  
  
 Wenn Sie das Hierarchiesymbol auswählen, können Sie die Hierarchie mit der Strukturansicht auf der linken Seite der Kachelansicht auf der rechten Seite anzeigen, wie unten gezeigt:  
  
> [!div class="mx-imgBorder"] 
> ![Firmenstruktur und Kachelansicht](media/hierachy-security-accounts-tile-view.png "Firmenstruktur und Kachelansicht")  
  
 Einige weitere der vorgegebenen Systementitäten können für eine Hierarchie aktiviert werden. Diese Entitäten umfassen `Case`, `Contact`, `Opportunity`, `Order`, `Quote`, `Campaign` und `Team`. Alle benutzerdefinierten Entitäten können für eine Hierarchie aktiviert werden.  
  
> [!TIP]
>  Wenn eine Entität für eine Hierarchie aktiviert werden kann:  
>  Erweitern Sie im Projektmappen-Explorer die Entität, die Sie verwenden möchten. Die Entitätskomponente namens **Hierarchieeinstellungen** wird angezeigt. Die Entitäten, die nicht für eine Hierarchie aktiviert werden können, verfügen nicht über diese Komponente. Ausgenommen ist die Dynamics 365 Customer Engagement-Vertriebsgebietsentität. Obwohl **Hierarchieeinstellungen** für die Vertriebsgebietsentität angezeigt wird, kann die Entität nicht für eine Hierarchie aktiviert werden.  
  
 Was Sie beachten müssen, wenn Sie Visualisierungen erstellen:  
  
-   Nur eine auf sich selbst verweisende (1: n)-Beziehung pro Entität kann als hierarchisch festgelegt werden. In dieser Beziehung müssen die primäre Entität und die verknüpfte Entität vom gleichen Typ sein, z. B. account_parent_account oder new_new_widget_new_widget.  
  
-   Derzeit ist eine Hierarchie oder Visualisierung auf nur einer Entität basiert. Sie können die Firmenhierarchie so darstellen, dass Firmen auf verschiedenen Ebenen gezeigt werden, Sie können jedoch Firmen und Kontakte nicht in derselben Hierarchienvisualisierung anzeigen.  
  
-   Die Maximalanzahl an Feldern, die in einer Kachel angezeigt werden können, ist vier. Wenn Sie einer Schnellerfassung, das für die Kachel-Ansicht verwendet wird, mehr Felder hinzufügen, werden nur die ersten vier Felder angezeigt.  
  
### <a name="visualization-example"></a>Visualisierungsbeispiel  
 Betrachten wir ein Beispiel der Erstellung der Visualisierung einer benutzerdefinierten Entität. Wir erstellten eine benutzerdefinierte Entität namens new_Widget, dann erstellten wir eine auf sich selbst verweisende (1:N)-Beziehung **new_new_widget_new_widget** und markierten diese als hierarchisch, wie hier gezeigt:  
  
 ![Widgetbeziehungsdefinition](media/widget-relationship-definition.png "Widgetbeziehungsdefinition")  
  
 Dann wählten wir in der Rasteransicht **Hierarchien-Einstellungen** die hierarchische Beziehung **new_new_widget_new_widget** aus. Im Formular füllten wir die Pflichtfelder aus. Wenn Sie die (1: N)-Beziehung noch nicht als hierarchisch markiert haben, führt Sie der Link im Formular wieder zu dem Beziehungsdefinitionsformular zurück, in dem Sie die Beziehung als hierarchisch markieren können.  
  
 Für das **Schnellansichtsformular** erstellten wir ein Schnellerfassung mit der Bezeichnung **Kachelformular für Widget-Hierarchie**. In diesem Formular fügten wir vier Felder für die Anzeige in jeder Kachel hinzu.  
  
> [!div class="mx-imgBorder"] 
> ![Schnellerfassung für Widget erstellen](media/create-quickf-orm.png "Schnellerfassung für Widget erstellen")  
  
 Nach dem Abschluss der Einrichtung, erstellten wir zwei Datensätze: Standardwidget und Premium-Widget. Nachdem das Premium-Widget durch Verwendung des Suchfeldes als Standardwidget festgelgt war, zeigte die new_Widget-Rasteransicht die Hierarchiesymbole, wie unten dargestellt:  
  
> [!div class="mx-imgBorder"] 
> ![Hierarchieraster des Widgets](media/widget-hierarchy-grid.png "Hierarchieraster des Widgets")  
  
> [!TIP]
>  Die Hierarchiesymbole erscheinen erst in der Datensatz-Rasteransicht, wenn die Datensätze in der Beziehung aus über- und untergeordneten Zielen zugeordnet sind.  
  
 Wenn Sie das Hierarchiesymbol auswählen, wird die new_Widget-Hierarchie mit der Strukturansicht auf der linken Seite der Kachelansicht auf der rechten Seite angezeigt, und zeigt zwei Datensätze. Jede Kachel enthält vier Felder, die wir im **Kachelformular für Widget-Hierarchie** bereitstellten.  
 
 > [!div class="mx-imgBorder"] 
 > ![Struktur- und des Kachelansichten von Widgets](media/widget-tree-tiles.png "Struktur- und des Kachelansichten von Widgets")  
  
## <a name="see-also"></a>Siehe auch  
 [Video: Hierarchische Sicherheitsmodellierung in](http://www.youtube.com/watch?v=kx5So32DrCo&index=10&list=PLC3591A8FE4ADBE07)   
 [Video: Hierarchievisualisierung in](http://www.youtube.com/watch?v=_dGBE6icLNw&index=9&list=PLC3591A8FE4ADBE07)
