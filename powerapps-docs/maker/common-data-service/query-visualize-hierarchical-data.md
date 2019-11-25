---
title: Abfrage und Visualisierung hierarchischer Daten mit PowerApps | MicrosoftDocs
description: Erfahren Sie, wie hierarchische verknüpfte Daten abgefragt und visualisiert werden
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
ms.openlocfilehash: 563c773bd2bec365a3459097e4c4e8428d624c00
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2755265"
---
# <a name="query-and-visualize-hierarchically-related-data"></a>Hierarchiebezogene Daten abfragen und visualisieren

Sie können wertvolle Unternehmenseinblicke erhalten, indem Sie hierarchisch verknüpften Daten darstellen. Die hierarchischen Modellierungs- und Visualisierungsfähigkeiten bieten Ihnen eine Reihe von Vorteilen:  
  
-   Anzeigen und Durchsuchen komplexer hierarchischer Informationen.  
  
-   Anzeigen von Key Performance Indicators (KPIs) in der Kontextansicht einer Hierarchie.  
  
-   Visuelles Analysieren wichtiger Informationen über das Internet und die Tablets hinweg.  
  
Für einige Entitäten, wie Firmen und Benutzer, werden die Visualisierungen standardmäßig zur Verfügung gestellt. Andere Entitäten, einschließlich benutzerdefinierter Entitäten, können für eine Hierarchie aktiviert werden, und Sie können die Visualisierungen für diese erstellen. Je nach Ihren Anforderungen können Sie zwischen der Verwendung einer Strukturansicht, die die gesamte Hierarchie anzeigt, und einer Kachelansicht, die eine detaillierte Ansicht eines kleineren Teils der Hierarchie wiedergibt, wählen. Beide Ansichten werden nebeneinander angezeigt. Sie können eine Hierarchie erkunden, indem Sie eine Hierarchiestruktur erweitern und reduzieren. Dieselben hierarchischen Einstellungen für Visualisierung werden einmal festgelegt, gelten jedoch sowohl für das Web als auch für mobile Clients. Auf Tablets werden die grafischen Elemente in einem für das kleinere Format geeigneten Format angezeigt. Die anpasbaren Komponenten für hierarchische Visualisierung sind lösungsspezifisch, daher können sie wie jede andere Anpassung zwischen Organisationen transportiert werden. Sie können die Attribute konfigurieren, die in der Visualisierung angezeigt werden, indem Sie eine Schnellerfassung mit dem Formular-Editor verwenden. Es ist nicht erforderlich, Code zu schreiben.  
  
<a name="BKMK_Querydata"></a>   
## <a name="query-hierarchical-data"></a>Abfragen von hierarchischen Daten  
 Mit Common Data Service werden hierarchische Datenstrukturen durch selbstreferenzierende Beziehungen der Bezugsdatensätze unterstützt. In der Vergangenheit mussten Sie die verknüpften Datensätze iterativ abfragen, um hierarchische Daten anzuzeigen. Jetzt können Sie verknüpften Daten in einem Schritt als Hierarchie abfragen. Sie können nach Entitätsdatensätzen abfragen, indem Sie die **Unter** und **Nicht Unter**-Logik verwenden. Die hierarchischen Operatoren **Unter** und **Nicht unter** werden in der erweiterten Suche und im Workfloweditor verfügbar gemacht. Weitere Informationen zum Verwenden dieser Operatoren finden Sie unter [Konfigurieren von Workflowschritten](/flow/configure-workflow-steps). Weitere Information zur erweiterten Suche finden Sie unter [Erstellen, Bearbeiten oder Speichern einer erweiterten Suche](https://docs.microsoft.com/dynamics365/customer-engagement/basics/save-advanced-find-search).  
  
 Die folgenden Beispiele illustrieren verschiedene Szenarien für das Abfragen von Hierarchien:  
  
 Firmenhierarchie abfragen  
  
 ![Firmen in der Firmenhierarchie abfragen](media/query-accounts.png "Firmen in der Firmenhierarchie abfragen")  
  
 Firmenhierarchie abfragen, einschließlich verwandter Aktitvitäten  
  
 ![Zugehörige Aktivitäten der Firma abfragen](media/query-account-related-activities.png "Zugehörige Aktivitäten der Firma abfragen")  
  
 Firmenhierarchie abfragen, einschließlich verwandter Geschäftschancen  
  
 ![Zugehörige Verkaufschancen der Firma abfragen](media/query-account-related-opportunities.png "Zugehörige Verkaufschancen der Firma abfragen")  
  
 Um die Daten als Hierarchie abzufragen, müssen Sie die auf sich selbst verweisenden Beziehungen als hierarchisch festlegen. So aktivieren Sie die Hierarchie  
  

1. Auf [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), erweitern Sie den Abschnitt **Daten** und klicken oder tippen Sie im linken Navigationsbereich **Entitäten**.

2. Klicken oder tippen Sie auf eine vorhandene Entität oder [Erstellen Sie eine neue Entität](data-platform-create-entity.md)

3. Klicken Sie auf **Beziehungen**.

4.  Wählen Sie eine auf sich selbst verweisende Beziehung.

5.  Überprüfen Sie im Bereich Beziehungsdetails **Hierarchisch**.  
  
> [!NOTE]
> - Einige der standardmäßigen Beziehungen können nicht angepasst werden. Dieses hindert Sie, diese Beziehungen als hierarchisch festzulegen.  
> - Sie können eine hierarchische Beziehung für die auf sich selbst verweisenden Beziehungen des Systems festlegen. Hierzu zählen die auf sich selbst verweisenden Beziehungen vom Systemtyp, beispielsweise die "contact_master_contact"-Beziehung.  
  
<a name="BKMK_Visualizedata"></a>   
## <a name="visualize-hierarchical-data"></a>Visualisieren von hierarchischen Daten  
 Die Systementitäten, für die Visualisierungen standardmäßig verfügbar sind, umfassen: `Account`, `Position`, `Product` und `User`. in der Rasteransicht dieser Entitäten können Sie das symbol, das das Hierarchiendiagramm darstellt, links neben dem Datensatznamen finden. Das Hierarchiensymbol ist nicht standardmäßig für alle Datensätze vorhanden. Das symbol wird für die Datensätze angezeigt, die einen übergeordneten Datensatz, einen untergeordneten Datensatz oder beides haben.  
 
 > [!div class="mx-imgBorder"] 
 > ![Aktive Firmen](media/cust-hs-active-account.png "Aktive Firmen")  
  
 Wenn Sie das Hierarchiesymbol auswählen, können Sie die Hierarchie mit der Strukturansicht auf der linken Seite der Kachelansicht auf der rechten Seite anzeigen, wie unten gezeigt:  
  
> [!div class="mx-imgBorder"] 
> ![Kontenstruktur und Kachelansicht](media/hierachy-security-accounts-tile-view.png "Kontenstruktur und Kachelansicht")  
  
 Einige weitere der vorgegebenen Systementitäten können für eine Hierarchie aktiviert werden. Diese Entitäten umfassen `Case`, `Contact`, `Opportunity`, `Order`, `Quote`, `Campaign` und `Team`. Alle benutzerdefinierten Entitäten können für eine Hierarchie aktiviert werden.  
  
> [!TIP]
>  Wenn eine Entität für eine Hierarchie aktiviert werden kann:  
>  Erweitern Sie im Projektmappen-Explorer die Entität, die Sie verwenden möchten. Die Entitätskomponente namens **Hierarchieeinstellungen** wird angezeigt. Die Entitäten, die nicht für eine Hierarchie aktiviert werden können, haben diese Komponente nicht, mit Ausnahme der Entität Dynamics 365 Sales Territory. Obwohl **Hierarchieeinstellungen** für die Vertriebsgebietsentität angezeigt wird, kann die Entität nicht für eine Hierarchie aktiviert werden.  
  
 Was Sie beachten müssen, wenn Sie Visualisierungen erstellen:  
  
-   Nur eine auf sich selbst verweisende (1: n)-Beziehung pro Entität kann als hierarchisch festgelegt werden. In dieser Beziehung müssen die primäre Entität und die verknüpfte Entität vom gleichen Typ sein, z. B. account_parent_account oder Widget_new_Widget_new_Widget.  
  
-   Derzeit ist eine Hierarchie oder Visualisierung auf nur einer Entität basiert. Sie können die Firmenhierarchie so darstellen, dass Firmen auf verschiedenen Ebenen gezeigt werden, Sie können jedoch Firmen und Kontakte nicht in derselben Hierarchienvisualisierung anzeigen.  
  
-   Die Maximalanzahl an Feldern, die in einer Kachel angezeigt werden können, ist vier. Wenn Sie einer Schnellerfassung, das für die Kachel-Ansicht verwendet wird, mehr Felder hinzufügen, werden nur die ersten vier Felder angezeigt.  
  
### <a name="visualization-example"></a>Visualisierungsbeispiel  
 Betrachten wir ein Beispiel der Erstellung der Visualisierung einer benutzerdefinierten Entität. Wir haben eine benutzerdefinierte Entität namens new_Widget erstellt, eine auf sich selbst verweisende Beziehung und diese als hierarchisch markiert, wie hier gezeigt.  
 
> [!div class="mx-imgBorder"] 
> ![Widget-Beziehungsdefinition](media/widget-relationship-definition.png "Widget-Beziehungsdefinition")  
   
 Dann wählten wir in der Rasteransicht **Hierarchien-Einstellungen** die hierarchische Beziehung **Widget_new_Widget_new_Widget** aus. Im Formular füllten wir die Pflichtfelder aus. Wenn Sie die Beziehung noch nicht als hierarchisch markiert haben, führt Sie der Link im Formular wieder zu dem klassischen Enitätseditor, in dem Sie die Beziehung auch als hierarchisch markieren können.  
  
 Für das **Schnellansichtsformular** erstellten wir ein Schnellerfassung mit der Bezeichnung **Kachelformular für Widget-Hierarchie**. In diesem Formular fügten wir vier Felder für die Anzeige in jeder Kachel hinzu.  
  
> [!div class="mx-imgBorder"] 
> ![Schnellerfassung für Widget erstellen](media/create-quickf-orm.png "Schnellerfassung für Widget erstellen")  
  
 Nachdem wir die EInrichtung abgeschlossen haben, haben wir zwei Datensätze erstellt: Standard Widget und Premium Widget. Nachdem das Premium-Widget durch Verwendung des Suchfeldes als Standardwidget festgelgt war, zeigte die new_Widget-Rasteransicht die Hierarchiesymbole, wie unten dargestellt:  
  
> [!div class="mx-imgBorder"] 
> ![Hierarchieraster des Widgets](media/widget-hierarchy-grid.png "Hierarchieraster des Widgets")  
  
> [!TIP]
>  Die Hierarchiesymbole erscheinen erst in der Datensatz-Rasteransicht, wenn die Datensätze in der Beziehung aus über- und untergeordneten Zielen zugeordnet sind.  
  
 Wenn Sie das Hierarchiesymbol auswählen, wird die new_Widget-Hierarchie mit der Strukturansicht auf der linken Seite der Kachelansicht auf der rechten Seite angezeigt, und zeigt zwei Datensätze. Jede Kachel enthält vier Felder, die wir im **Kachelformular für Widget-Hierarchie** bereitstellten.  
 
 > [!div class="mx-imgBorder"] 
 > ![Struktur- und Kachelansichten des Widgets](media/widget-tree-tiles.png "Struktur- und Kachelansichten des Widgets")  
  
## <a name="see-also"></a>Siehe auch  
 [Video: Hierarchische Sicherheitsmodellierung in](https://www.youtube.com/watch?v=kx5So32DrCo&index=10&list=PLC3591A8FE4ADBE07)   
 [Video: Hierarchievisualisierung in](https://www.youtube.com/watch?v=_dGBE6icLNw&index=9&list=PLC3591A8FE4ADBE07)
