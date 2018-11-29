---
title: Verfügbare Menübänder in modellgestützten Apps | Microsoft Docs
description: 'In diesem Thema wird beschrieben, wo Menübänder definiert und geändert werden.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="ribbons-available"></a>Verfügbare Menübänder

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/customize-dev/ribbons-available-microsoft-dynamics-365 -->

In diesem Thema wird beschrieben, wo Menübänder in modellgestützten Apps definiert und geändert werden.

<a name="ribbon_defs"></a>   
## <a name="ribbon-definitions"></a>Menübanddefinitionen  
 Modellgestützte Apps enthalten Stanard-`<RibbonDiffXml>`-Definitionen für jedes Menüband in der Anwendung. Sie können die aktuelle XML, die das Menübands für Ihre Organisation definiert exportieren und anzeigen, aber Sie können die XML nicht direkt aktualisieren. Sie können das Menüband anpassen, indem Sie definieren, wie es geändert werden soll. Die Änderungsdefinitionen, die Sie angeben, werden zur Laufzeit angewendet, wenn das Menübands in der Anwendung angezeigt wird. Alle Ihre Änderungen werden in den Elementen `<CustomAction>` oder `<HideCustomAction>` ausgeführt. Diese Elemente werden über die standardmäßigen Menübanddefinitionen angewendet, die von modellgestützten bereitgestellt werden.  

 Wenn Sie Ihre Änderungsdefinitionen schreiben, müssen Sie die Definitionen der Standardmenübänder häufig verweisen. Wenn sie beispielsweise ein bestimmtes Menübandelement ausblenden möchten, müssen Sie die eindeutige ID des Elements kennen. Wenn Sie ein neues Menübandelement innerhalb oder neben einem vorhandenen Menübandelement positionieren möchten, müssen Sie die ID-Werte für diese Elemente sowie die Reihenfolge kennen, die die relative Stellung der Elemente steuert.  

 Wegen dieser Anforderung ist es erforderlich, die Definitionen von vorhandenen Menübandelementen zu verweisen, es ist sehr wichtig, die aktuellen Menübanddefinitionen in Ihrer Organisation zu verstehen. Es gibt zwei Nachrichten, die Sie verwenden können, um XML-Dateien, die den aktuellen Status der Menübänder darstellen, zu exportieren. Die Definitionen enthalten alle Anpassungen, die bereits auf dem System angewendet wurden, damit Sie zuvor angewendete Menübänder anpassen können. Weitere Informationen finden Sie unter [Exportieren von Menübanddefinitionen](export-ribbon-definitions.md).  

 Um Ihnen bei den ersten Schritten zu helfen, können Sie die standardmäßigen Menübanddefnitionen für MDA von [Microsoft Downloads: ExportedRibbonXml.zip](http://download.microsoft.com/download/C/2/A/C2A79C47-DD2D-4938-A595-092CAFF32D6B/ExportedRibbonXml.zip) herunterladen. Die ExportedRibbonXml.zip-Datei enthält die Ausgabedatei, die Sie für eine Organisation mit einem Menüband, das nicht angepasst wurde, haben würden. Sie müssen keine Beispielanwendung auszuführen, um diese Daten zu exportieren. Wenn Sie ein angepasstes Menüband haben, sollten Sie die Beispielanwendung ausführen, um die Dateien in diesem Ordner mit allen zuvor angewendeten Anpassungen für Ihre Organisation zu aktualisieren.  

 Innerhalb der exportierten XML-Datei enthält die applicationRibbon.xml-Datei alle Menübänder, die nicht für eine bestimmte Entität definiert sind. Diese entsprechen der Lösungskomponente **Anwendungsmenübänder**. Für jede Entität finden Sie eine *Entitätsname*-ribbon.xml-Datei. Das entspricht der `RibbonDiffXml`, die in jeder Entität enthalten ist. Wenn Sie das Menüband für eine bestimmte Entität bearbeiten möchten, sollten Sie die Menüband-XML-Datei für diese Entität finden.  

<a name="entity_ribbons"></a>   
## <a name="entity-ribbons"></a>Entitätsmenübänder  
 Alle Entitäten verwenden eine gemeinsame Menübanddefinition genannt *Entitätsmenübandvorlage*. Die Entitätsmenüband-Vorlagendefinition befindet sich in der applicationribbon.xml-Datei. Wenn Sie eine benutzerdefinierte Entität erstellen, ist das angezeigte Menüband das das standardmäßige Menüband, das von der Entitätsmenübandvorlage definiert wird. Jede Systementität hat eine separate `<RibbonDiffXml>`-Definition, die auf der Entitätsmenüband-Vorlagendefinition aufbaut.  

 Innerhalb der applicationribbon.xml-Datei werden die folgenden Registerkarten angezeigt, die für alle Entitäten gelten:  

- `Mscrm.Form.{!EntityLogicalName}.MainTab`  

   Die Registerkarte zeigt den Anzeigenamen der Entität in der Beschriftung an.  

- `Mscrm.Form.{!EntityLogicalName}.Related`  

   Die Registerkarte hat die Beschriftung **Hinzufügen**.  

- `Mscrm.Form.{!EntityLogicalName}.Developer`  

   Die Registerkarte hat die Beschriftung **Anpassen**.  

- `Mscrm.HomepageGrid.{!EntityLogicalName}.MainTab`  

   Die Registerkarte zeigt den mehrfachen Anzeigenamen der Entität in der Beschriftung an.  

- `Mscrm.HomepageGrid.{!EntityLogicalName}.View`  

   Die Registerkarte hat die Beschriftung **Ansicht**.  

- `Mscrm.HomepageGrid.{!EntityLogicalName}.Related`  

   Die Registerkarte hat die Beschriftung **Hinzufügen**.  

- `Mscrm.HomepageGrid.{!EntityLogicalName}.Developer`  

   Die Registerkarte hat die Beschriftung **Anpassen**.  

- `Mscrm.SubGrid.{!EntityLogicalName}.ContextualTabs`  

   Wenn ein Unterraster in einem Formular oder einem Diagramm den Fokus hat, wird die Kontextregisterkarte mit der Bezeichnung **Listentools** angezeigt.  

  -   `Mscrm.SubGrid.{!EntityLogicalName}.MainTab`  

       Die Registerkarte zeigt den mehrfachen Anzeigenamen der Entität.  

  Wenn Sie die Menübanddefinitionen für eine bestimmte Entität anzeigen, sehen Sie, dass der Name der Entität in der Regel das Token `{!EntityLogicalName}` ersetzt. Wenn Sie das Token `{!EntityLogicalName}` in der Menübanddefinition für eine bestimmte Entität finden, bedeutet das, das es für diese Ressourcen keine bestimmte Definition gibt und sie einfach die Definition der Entitätsmenübandvorlage verwendet. Wenn Sie Menübänder für eine bestimmte Entität definieren, sollten Sie immer den tatsächlichen Entitätsnamen verwendeten. Menübandänderungen für eine bestimmte Entität müssen im Knoten `//ImportExportXml/Entities/Entity/RibbonDiffXml` definiert werden.  

  Sie können Änderungen, die für alle Entitäten gelten, indem die Änderungen an den Anwendungsmenübänden definieren, die das Token `{!EntityLogicalName}` anstelle eines logischen Namen der Entität im RibbonDiffXml-Knoten ersetzen. Änderungen an Anwendungsmenübänden, die für alle Entitäten definiert werden, müssen im Knoten im `ImportExportXml/RibbonDiffXml` definiert werden. Sie können nicht im Knoten RibbonDiffXml für eine bestimmte Entität definiert werden.  

### <a name="grid-ribbons"></a>Rastermenübänder  
 Das Entitätsrastermenüband ist eine Sammlung von Registerkarten, die einen ID-Attributwertanfang mit `Mscrm.HomepageGrid.<entity logical name>` haben. So lautet die Registerkarte mit dem Text "Firmen" in einem Firmenentitätsraster beispielsweise `Mscrm.HomepageGrid.account.MainTab`. Alle Registerkarten, die auf dem Firmaenentitätsraster angezeigt werden, enthalten einen ID-Wert, der mit `Mscrm.HomepageGrid.account` beginnt.  

<a name="BKMK_SubGridRibbons"></a>   
### <a name="subgrid-ribbons"></a>Unterrastermenübänder  
 Das Entitätsunterrastermenüband ist eine Kontextgruppe mit einer Sammlung von Registerkarten, die einen ID-Attributwertanfang mit `Mscrm.SubGrid.<entity logical name>` haben. So lautet die Registerkarte mit dem Text "Firmen" in einem Firmenentitätsunterraster beispielsweise `Mscrm.SubGrid.account.MainTab`.  

 Wenn eine Liste mit den Datensätzen für eine Entität in einem Unterraster im Formular einer anderen Entität oder einem Diagramm angezeigt wird, gibt es nur drei Steuerelemente, die direkt über oder in dem Unterraster verfügbar sind. Die Verhaltensweisen für diese Steuerelemente kann geändert werden, indem die Befehle geändert werden, denen sie zugeordnet sind.  

- **Hinzufügen** Das Standardverhalten des Befehls mit dem ![Schaltfläche hinzufügen](media/customization-subgrid-add.PNG "Schaltfläche hinzufügen")-Symbol hängt davon ab, ob die Datensätze im Unterraster mit dem aktuellen Datensatz verknüpft sind.  

     Wenn die Datensätze mit dem aktuellen Datensatz verknüpft sind, lautet das Standardverhalten: nach vorhandenen Datensätzen suchen. Wenn ein vorhandener Datensatz nicht gefunden werden kann oder wenn der Benutzer einfach einen neuen Datensatz erstellen möchte, kann er auf **Neue hinzufügen** klicken.  

     Wenn die Datensätze nicht mit dem aktuellen Datensatz verknüpft sind, lautet das Standardverhalten: einen neuen Datensatz hinzufügen. Falls die Entität ein Schnellerfassungsformular besitzt, wird es angezeigt; andernfalls wird ein neues ganzes Formular angezeigt.  

     Aktivitäten sind die Ausnahme bei diesem Muster. Der Hinzufügensbefehl verlangt immer zuerst den Typ der Aktivität.

     > [!NOTE]
     >  Der Offlinemodus in Dynamics 365 unterstützt keine n:n-Beziehung bei benutzerdefinierten Entitäten. Deshalb wird die Schaltfläche **Neu hinzufügen** im Dynamics 365-Offlinemodus nicht auf einem Unterraster angezeigt.

- **Liste anzeigen** Der Befehl mit dem ![Mit Schaltfläche öffnen](media/customization-open-view.PNG "Mit Schaltfläche öffnen")-Symbol wird die gesamte Liste öffnen, in der alle verfügbaren Befehle verwendet werden können.  

     Wenn das Unterraster dem aktuellen Datensatz zugeordnet wird, ist das Standardverhalten eines Befehls, die zugeordnete Ansicht zu öffnen.  

     Wenn das Unterraster dem aktuellen Datensatz nicht zugeordnet wird, ist das Standardverhalten eines Befehls, die Ansicht in der Hauptlistenansicht zu öffnen.  

- **Löschen** Das ![Symbol: Löschen der untergeordneten Liste](media/customization-subgrid-delete.PNG "Symbol: Löschen der untergeordneten Liste")-Symbol wird rechts neben der Zeile angezeigt, wenn die Beteiligten mit der Maus auf die Datensätze in der Liste zeigen.  

     Für Datensätze mit einer 1: n-Beziehung oder keiner Beziehung, ist das Standardverhalten, den Datensatz zu löschen. Die Löschung wird möglicherweise blockiert, wenn sie aufgrund der Beziehungskonfigurationen nicht zulässig ist. Offene Aktivitäten und Rechnungen sind häufige Beispiele für Datensätze, die möglicherweise aufgrund der Beziehungskonfigurationen nicht gelöscht werden.  

     Für Beziehungen, die n:n-Beziehungen anzeigen, ist das Standardverhalten, die Beziehung zu entfernen, die mit den Datensätzen verbunden sind und nicht den Datensatz selbst.  

  Sie können das Standardverhalten ändern, indem Sie die Aktionen, die dem Befehl zugewiesen sind mithilfe von `<CommandDefinition>` ändern, aber Sie können den Namen des Befehls nicht ändern. Beispielsweise können Sie den Löschvorgang ändern, sodass er den Datensatz deaktiviert, anstatt ihn zu löschen.  

  Es ist nicht möglich, die angezeigten Symbole für diese Befehle zu ändern. 
  Sie können diese Befehle ausblenden, indem Sie `<HideCustomAction>` verwenden.  

### <a name="form-ribbons"></a>Formularmenübänder  
 Jede Entität kann mehrere Formulare haben. Sie können Änderungen am Formularmenüband für alle Formulare für diese Entität definieren, indem Sie Ihre Definition auf Entitätsebene hinzufügen (`//ImportExportXml/Entities/Entity/RibbonDiffXml`).  

 Jedes Entitätsformular kann eine bestimmte Menübanddefinition haben. In der exportierten Datei customizations.xml müssen Sie Ihren geändertes `<RibbonDiffXml>` diesem Speicherort hinzufügen:`//ImportExportXml/Entities/Entity/FormXml/forms/systemform/form/RibbonDiffXml`.  

 Das Entitätsformularmenüband ist eine Sammlung von Registerkarten, die einen ID-Attributwertanfang mit `Mscrm.Form.<entity logical name>` haben. Beispielsweise ist die Registerkarte mit der Beschriftung **Firma** auf dem Firmenentitätsformular `Mscrm.Form.account.MainTab`. Alle Registerkarten, die auf dem Firmaenentitätsformular angezeigt werden, enthalten einen ID-Wert, der mit `Mscrm.Form.account` beginnt.  

<a name="BKMK_BasicHomeTab"></a>   
## <a name="basic-home-tab"></a>Standard-Startregisterkarte  
 Die Standard-Startregisterkarte wird auf dem Haupt-Anwendungsmenüband angezeigt, wenn eine alternative Registerkarte aufgrund des Entitätskontexts oder einer Anzeigenregel, die sie für bestimmte Seiten unterdrückt, nicht definiert ist. Diese Registerkarte wird beispielsweise angezeigt, wenn die MDA-**Hilfe** anzuzeigen. Die ID der Standard-Startregisterkarte ist `Mscrm.BasicHomeTab`.  

<!-- [!NOTE]-->
<!-- >  The Jewel that was shown in [!INCLUDE[pn_crm2011_and_online](../../includes/pn-crm2011-and-online.md)] is no longer displayed. Changes to the Jewel will not appear in [!INCLUDE[pn_dynamics_crm_online](../../includes/pn-dynamics-crm-online.md)]  -->

<!--<a name="outlook_ribbons"></a>   
## [!INCLUDE[pn_dynamics_crm](../../includes/pn-dynamics-crm.md)] for Microsoft Office Outlook ribbons  
 [!INCLUDE[pn_MS_Outlook_Full](../../includes/pn-ms-outlook-full.md)] 2007 do not display a ribbon. [!INCLUDE[ribbon_enum_Version_2010](../../includes/ribbon-enum-version-2010.md)] uses the ribbon. You can use [!INCLUDE[pn_dynamics_crm](../../includes/pn-dynamics-crm.md)] ribbon definitions to add controls to all of them.  -->

<!--### Microsoft Office Outlook 2007  
 The [!INCLUDE[pn_crm_for_outlook_full](../../includes/pn-crm-for-outlook-full.md)] controls to support older versions of [!INCLUDE[pn_MS_Outlook_Full](../../includes/pn-ms-outlook-full.md)] toolbars and menus are defined as tabs with the Id values of `Mscrm.LegacyOfficeToolbar` and `Mscrm.LegacyOfficeMenubar`, respectively.  -->

<!--### Microsoft Office Outlook 2010  
 The [!INCLUDE[pn_crm_for_outlook_full](../../includes/pn-crm-for-outlook-full.md)] controls to support [!INCLUDE[ribbon_enum_Version_2010](../../includes/ribbon-enum-version-2010.md)] toolbars and menus are defined as tabs with the Id values of `Mscrm.Outlook14GlobalToolbar` and `Mscrm.Outlook14GlobalMenubar`, respectively.  -->

<a name="other_ribbons"></a> ## Andere Menübänder Einige andere Menübandregisterkarten und Kontextgruppen für besondere Zwecken werden von MDA definiert.
Jede Registerkarte wird einer bestimmten <TabDisplayRule> zugeordnet, die steuert, wann sie angezeigt werden. In der folgenden Liste sind diese Registerkarten aufgeführt.  


|                 Tabstopp                  |             Stamm-ID              |                                                              Beschreibung                                                              |
|--------------------------------------|----------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
|     Seitenregisterkarte "Webressource bearbeiten".      |    `Mscrm.WebResourceEditTab`    |                                        Zeigt an, wann Webressourcen innerhalb einer Lösung bearbeitet werden.                                         |
|           Registerkarte "Formular-Editor"            |      `Mscrm.FormEditorTab`       |                               Stellt die Gruppen "Speichern", "Bearbeiten" und "Ansicht" von Aktionen für Entitätsformulare bereit.                               |
|        Registerkarte "Formular-Editor einfügen"        |   `Mscrm.FormEditorInsertTab`    |                               Stellt Schaltflächen zum Einfügen von Abschnitten, Registerkarten und Steuerelementen in Entitätsformularen bereit.                                |
|        Registerkarten "Dashboard-Homepage"        |       `Mscrm.DashboardTab`       |                                                    Wird im Arbeitsbereich angezeigt.                                                    |
| Kontextgruppe "Visualisierungs-Tool" |    `Mscrm.VisualizationTools`    |             Wird angezeigt, wenn auf die Schaltfläche **Neues Diagramm** auf der Registerkarte **Diagramme**, die im Entitätsrastermenüband angezeigt wird, geklickt wird.              |
|       Registerkarte "AptbookTab-Homepage"        |        `Mscrm.AptbookTab`        |                                    Wird angezeigt, wenn der Servicekalender im Servicebereich angezeigt wird.                                    |
|          Registerkarte "Erweiterte Suche"           |       `Mscrm.AdvancedFind`       |                                               Wird im Fenster **Erweiterte Suche** angezeigt.                                               |
|         Registerkarte "Dashboard-Editor"         |    `Mscrm.DashboardEditorTab`    |                                                  Wird angezeigt, wenn ein Dashboard bearbeitet wird.                                                   |
|            Registerkarte "Dokumente"             |       `Mscrm.DocumentsTab`       | Wird angezeigt, wenn die SharePoint-Integration für die Organisation aktiviert wurde. |
|           Registerkarte "Diagramm-Editor"           | `Mscrm.VisualizationDesignerTab` |                                       Wird angezeigt, wenn ein Diagramm aus dem Lösungsfenster bearbeitet wird.                                        |
|    Kontextgruppe "Suchwerkzeuge"     |      `Mscrm.ArticleSearch`       |                                             Wird angezeigt, wenn die `KBarticle` Entität angezeigt wird.                                             |

<a name="BKMK_RibbonsForCustomPages"></a>

## <a name="ribbons-for-custom-pages"></a>Menübänder für benutzerdefinierte Seiten

Sie können mithilfe von SiteMap benutzerdefinierte Seiten in der Anwendungsnavigation anzeigen. Diese Seiten werden immer die [Standard-Startregisterkarte](ribbons-available.md#BKMK_BasicHomeTab) (`Mscrm.BasicHomeTab`) anzeigen. 

Es ist nicht möglich, eine `<PageRule>` zu verwenden, um benutzerdefinierte Menübandkomponenten auf benutzerdefinierten Seiten anzuzeigen oder zu aktivieren.  

### <a name="see-also"></a>Siehe auch  
 [Anpassen des Menübands](customize-commands-ribbon.md)   
 [Darstellen von Befehlsleisten und Menübändern](command-bar-ribbon-presentation.md)
