---
title: Unterrastereigenschaften für Hauptformulare in modellgesteuerten Apps in Power Apps | Microsoft-Dokumentation
description: Grundlegendes zu Unterrastereigenschaften für Hauptformulare
Keywords: Hauptformular; Eigenschaften des Unterrasters; Dynamics 365
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 03/17/2020
ms.service: powerapps
ms.topic: article
ms.assetid: 82892cd3-3436-4677-b96b-f2ccd0a4f078
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c71afbf34f2e74afbcbd31f67d9164606d80d83b
ms.sourcegitcommit: 9f2694bd14d70798310b89a4673672c1bfad989d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/26/2020
ms.locfileid: "3167012"
---
# <a name="sub-grid-properties-for-model-driven-app-main-forms-overview"></a>Unterrastereigenschaften für Hauptformulare in modellgesteuerten Apps im Überblick

Sie können ein Unterraster auf einem Formular konfigurieren, um eine Liste von Datensätzen anzuzeigen.  

Sie können auf **Unterrastereigenschaften** über die Power Apps-Website zugreifen. 
1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.

2.  Erweitern Sie **Daten** und wählen **Entitäten**, wählen Sie die Entität aus und wählen Sie die Registerkarte **Formulare**. 

3.  Öffnen Sie in der Liste der Formulare ein Formular des Typs **Haupt** und wählen Sie dann die Option **Komponenten** aus. 

4.  Wählen Sie im Bereich Komponenten die Option **Unterraster** aus.

    > [!div class="mx-imgBorder"] 
    > ![Auswählen von Unterrasteransichten](media/sub-grid-views.png "Auswählen von Unterrasteransichten")

5.  Wählen Sie in der **Entität** eine Entität aus, deren Datensätze Sie im Unterraster anzeigen möchten. Die Dropdownliste **Entität** wird gefiltert, um nur Entitäten aufzulisten, die sich auf die aktuelle Entität beziehen.

6.  Wählen Sie in der **Standardansicht** eine Standardansicht für das Unterraster aus. Dies ist die Ansicht der in der Entitätseigenschaft ausgewählten Entität, die zum Abrufen und Anzeigen der Liste der Datensätze im Unterraster verwendet wird.

7.  Wählen Sie die Option **Zugehörige Datensätze anzeigen** aus, um nur Datensätze anzuzeigen, die mit dem aktuellen Datensatz verknüpft sind, der im Formular angezeigt wird.

8.  Wählen Sie die Option **Fertig** aus, um das Unterraster zum Formular hinzuzufügen. Die Eigenschaften des Unterrasters werden im Eigenschaftenbereich angezeigt.

    > [!div class="mx-imgBorder"] 
    > ![Unterrastereigenschaften](media/newform-designer-sub-grid-properties.png "Unterrastereigenschaften")

|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|**Name**|**Erforderlich**: Der eindeutige Name für das Unterraster, der verwendet wird, wenn auf es in Skripts verwiesen wird. Der Name kann nur alphanumerische Zeichen und Unterstrichzeichen enthalten.|  
|**Bezeichnung**|**Erforderlich**: Die lokalisierbare Beschriftung für das Unterraster, die für Benutzer sichtbar ist.|  
|**Beschriftung ausblenden**|Ob die Beschriftung im Formular angezeigt werden soll. Dies ist erforderlich, wenn Sie **Suchfeld anzeigen** aktivieren. Sie können auch auswählen, dass die Bereichskopfzeilen Farbe verfügen.|  
|**Auf Telefon ausblenden**|Geben Sie an, ob der Abschnitt telefonisch vefügbar sein soll.|
|**Zeigen Sie Bezugsdatensätze an**| Unterraster zeigt nur Datensätze an, die mit dem aktuellen Datensatz verknüpft sind.<br /> Wenn Sie diese Eigenschaft nicht auswählen, werden im Unterraster Datensätze angezeigt, die nur nach der Standardansicht gefiltert wurden, oder, wenn die Ansichtsauswahl aktiviert ist, nach Ansichten, die der Benutzer auswählt.<br /><br /> Die Option, die Sie auswählen, wirkt sich auf das Verhalten des Listensteuerelements aus. Weitere Informationen: [Listenverhalten anzeigen](#show-list-behavior) |  
|**Entität**|Je nach der für **Zugehörige Datensätze anzeigen** ausgewählten Option wird in der Liste Folgendes angezeigt:<br /><br /> - Nur zugehörige Datensätze: Eine Liste von Entitäten, die mit dieser Entität verknüpft sind, mit dem Namen des Suchfelds für diese Entität, das die Beziehung in Klammern definiert.<br />- Alle Datensatztypen: Eine Liste aller Entitäten.|  
|**Standardansicht**|Wählen Sie die Ansicht aus, die standardmäßig angewendet wird. Falls nicht, aktivieren Sie andere anderen Ansichten mithilfe der Eigenschaft **Ansichtsauswahl**. Dies ist die einzige Ansicht.<br /><br /> Verwenden Sie die Schaltfläche **Bearbeiten**, um die Standardansicht für die Bearbeitung zu öffnen. Verwenden Sie die Schaltfläche **Neu**, um eine neue Ansicht zu erstellen, die für das Unterraster verwendet werden soll.|  
|**Erlauben Sie Benutzern, die Ansicht zu ändern**.|Wenn ausgewählt, können App-Benutzer von der Standardansicht zu einer anderen Ansicht der in der Entity-Eigenschaft ausgewählten Entität wechseln.|

## <a name="sub-grid-properties-for-model-driven-app-main-forms-classic"></a>Unterrastereigenschaften für Hauptformulare in modellgesteuerten Apps: Klassisch

Sie können ein Unterraster auf einem Formular mithilfe des klassischen Formulardesigners konfigurieren, um eine Liste von Datensätzen oder ein Diagramm anzuzeigen. Wählen Sie **Nur Diagramm anzeigen** auf der Registerkarte **Anzeigen**, um ein Diagramm statt der Liste anzuzeigen.

  > [!div class="mx-imgBorder"] 
  > ![Unterrastereigenschaften](media/sub-grid-properties.png "Unterrastereigenschaften")

Dies sind die Eigenschaften, die konfiguriert werden können, wenn eine Unterrasterkomponente auf einem Formular mit dem klassischen Formulardesigner verwendet wird.

|Registerkarte|Eigenschaft|Beschreibung|  
|---------|--------------|-----------------|  
|**Anzeigen**|**Name**|**Erforderlich**: Der eindeutige Name für das Unterraster, der verwendet wird, wenn auf es in Skripts verwiesen wird. Der Name kann nur alphanumerische Zeichen und Unterstrichzeichen enthalten.|  
||**Bezeichnung**|**Erforderlich**: Die lokalisierbare Beschriftung für das Unterraster, die für Benutzer sichtbar ist.|  
||**Beschriftung im Formular anzeigen**|Ob die Beschriftung im Formular angezeigt werden soll. Dies ist erforderlich, wenn Sie **Suchfeld anzeigen** aktivieren. Sie können auch auswählen, dass die Bereichskopfzeilen Farbe verfügen.|  
||**Datensätze**|Wählen Sie unter zwei Optionen aus:<br /><br /> - **Nur verknüpfte Datensätze**: Unterraster zeigt nur Datensätze an, die mit dem aktuellen Datensatz verknüpft sind.<br />- **Alle Datensatztypen**: Unterraster zeigt nur die nach der Standardansicht gefilterten Datensätze an oder, wenn die Ansichtsauswahl aktiviert ist, alle Ansichten, die der Benutzer auswählt.<br /><br /> Die Option, die Sie auswählen, wirkt sich auf das Verhalten des Listensteuerelements aus. Weitere Informationen: [Listenverhalten anzeigen](#show-list-behavior) |  
||**Entität**|Je nach der für **Datensätze** ausgewählten Option zeigt die Liste an:<br /><br /> - **Nur verknüpfte Datensätze**: Eine Liste der Entitäten, die mit dieser Entität verknüpft sind, mit dem Namen des Suchfelds auf dieser Entität, das die Beziehung definiert in Klammern.<br />- **Alle Datensatztypen**: Eine Liste aller Entitäten.|  
||**Standardansicht**|Wählen Sie die Ansicht aus, die standardmäßig angewendet wird. Falls nicht, aktivieren Sie andere anderen Ansichten mithilfe der Eigenschaft **Ansichtsauswahl**. Dies ist die einzige Ansicht.<br /><br /> Verwenden Sie die Schaltfläche **Bearbeiten**, um die Standardansicht für die Bearbeitung zu öffnen. Verwenden Sie die Schaltfläche **Neu**, um eine neue Ansicht zu erstellen, die für das Unterraster verwendet werden soll.|  
||**Suchfeld anzeigen**|Suchfeld anzeigen. Wenn diese Option ausgewählt ist, ist die Option **Beschriftung im Formular anzeigen** erforderlich.|  
||**Index anzeigen**|Nur Formulare die [Klassische Formulare](main-form-presentations.md#classic-forms) nutzen, unterstützen den Anzeigeindex.<br /><br /> Aktivieren Sie dieses Kontrollkästchen, wenn Sie der Liste einen alphabetischen Index zuordnen möchten. Damit können Sie direkt zu Datensätzen wechseln, die mit einem bestimmten Buchstaben oder einer Zahl beginnen.|  
||**Ansichtsauswahl**|Sie haben drei Möglichkeiten:<br /><br /> - **Deaktiviert**: Nur die Standardansicht kann verwendet werden.<br />- **Alle Ansichten anzeigen**: Zulassen, dass Benutzer eine Ansicht auswählen.<br />- **Ausgewählte Ansichten anzeigen**: Verwenden Sie die STRG-Taste mit dem Cursor, um auszuwählen, welche der verfügbaren Ansichten angezeigt werden soll.|  
||**Standarddiagramm**|Wählen Sie aus, welches Diagramm angezeigt wird, wenn **Nur Diagramm anzeigen** aktiviert ist.|  
||**Nur Diagramm anzeigen**|Anstelle einer Liste von Datensätzen wird ein Diagramm angezeigt.|  
||**Diagrammauswahl anzeigen**|Wenn **Nur Diagramm anzeigen** ausgewählt ist, erlauben Sie Benutzern, verschiedene Diagramme auszuwählen.|  
||**Verfügbarkeit**|Geben Sie an, ob der Abschnitt telefonisch vefügbar sein soll.|
|**Formatierung**|**Layout**|**Wählen Sie die Anzahl der Spalten, die vom Steuerelement belegt werden**.<br /><br /> Wenn der Abschnitt, der das Unterraster enthält, mehr als eine Spalte enthält, können Sie festlegen, dass das Feld die Anzahl von Spalten belegt, die der Abschnitt enthält.|  
||**Zeilenlayout**|**Anzahl der Zeilen** bestimmt, wie viele Datensätze eines Unterrasters auf einer Seite angezeigt werden.<br /><br /> Falls **Automatisch erweitern, um verfügbaren Bereich auszufüllen** aktiviert ist, bietet das Formular Platz für zwei Datensätze und erweitert den Platz, wenn mehr Datensätze hinzukommen. Wenn die Anzahl die **Anzahl der Zeilen** überschreitet, können Benutzer zu weiteren Seiten navigieren, um die Datensätze anzuzeigen.<br /><br /> Falls **Automatisch erweitern, um verfügbaren Bereich auszufüllen** nicht aktiviert ist, stellt das Formular Platz für die Anzahl der Datensätze zur Verfügung, die auch in **Anzahl der Zeilen** definiert ist, und Benutzer können auf weitere Seiten navigieren, um weitere Datensätze anzuzeigen.|  
|**Steuerelemente**|**Steuerelemente**|Wählen Sie, um Steuerelemente hinzuzufügen, so dass Sie im Web, über Telefon und Tablet verfügbar sind.|
  
 In Formularen, die [Klassische Formulare](main-form-presentations.md#classic-forms) nutzten, waren Aktionen, die in einem Unterraster ausgeführt wurden, im Menüband verfügbar. Entwickler können das Verhalten dieser Aktionen anpassen oder weitere Aktionen hinzufügen, indem sie das Menüband anpassen.  
  
 In Formularen, die [Aktualisierte Formulare](main-form-presentations.md#updated-forms) nutzen, werden Aktionen für Unterraster neben dem Unterraster platziert, was den Zugriff darauf erleichtert. Die Befehlsleiste erlaubt jedoch nicht das Hinzufügen benutzerdefinierter Aktionen. Entwickler können mithilfe des Menübands die Aktionen für die verbleibenden drei Aktionen ändern: Liste anzeigen, Datensatz hinzufügen und Datensatz löschen.  
  

## <a name="show-list-behavior"></a>Listenverhalten anzeigen  
 Bei der Anzeige einer Liste in Formularen mit [Aktualisierte Formulare](main-form-presentations.md#updated-forms) zeigt jedes Unterraster die Schaltfläche **Ansicht öffnen** ![Ansicht öffnen-Schaltfläche](media/crm-itpro-cust-openview.PNG "Mit Schaltfläche öffnen") oben rechts an, wenn die Entität auch als eine der Entitäten angezeigt wird, die im Navigationsbereich des Formulareditors enthalten sind. Durch Auswählen dieser Schaltfläche wird die Ansicht geöffnet. Die Verhaltensweise ändert sich abhängig von der für die Eigenschaft **Datensätze** ausgewählten Option.  
  
 Bei Auswahl von **Nur verknüpfte Datensätze** wird die Ansicht mithilfe einer der zugeordneten Ansichten im gleichen Fenster geöffnet. Um zum Formular zurückzukehren, verwenden Sie die Zurück-Schaltfläche, oder wählen Sie den primären Namenwert des aktuellen Datensatzes in der Navigationsleiste aus.  
  
 Bei Auswahl von **Alle Datensatztypen** wird die Ansicht in einem neuen Fenster geöffnet.  

## <a name="add-record-behavior"></a>Verhalten beim Hinzufügen von Datensätzen  
 Wird eine Liste in Formularen mit [Aktualisierte Formulare](main-form-presentations.md#updated-forms) angezeigt, zeigt jedes Unterraster die Schaltfläche **Datensatz hinzufügen** ![Hinzufügen-Schaltfläche](media/crm-itpro-cust-subgridadd.PNG "Schaltfläche "Hinzufügen"") an der oberen rechten Seite des Unterrasters an. Durch Azswählen dieser Schaltfläche können Sie einen Datensatz hinzuzufügen. Diese Verhaltensweise ändert sich je nach der für die Eigenschaft **Datensätze** ausgewählten Option, und danach, ob sich die Suche auf Aktivitätsdatensätze bezieht.  
  
 Wenn Sie **Nur verknüpfte Datensätze** auswählen, besteht das standardmäßige Verhalten darin, bestehende Datensätze hinzuzufügen. Benutzer sehen zuerst eine Inline-Suche zur Suche nach vorhandenen Datensätzen. Dadurch wird das Erstellen von doppelten Datensätzen verhindert.  Wenn sie keinen vorhandenen Datensatz finden, können sie die Option **Neu** auswählen. Wenn ein neuer Datensatz erstellt wird, werden die Feldzuordnungen, die in dieser Beziehung definiert sind, angewendet. Weitere Informationen: [Zuordnen von Entitätsfeldern](../common-data-service/map-entity-fields.md).   
  
 Wenn Sie **Alle Datensatztypen** auswählen, besteht das standardmäßige Verhalten im Hinzufügen eines neuen Datensatzes. Durch das Schnellerfassungsformular wird angezeigt, ob die Zielentität über einen Datensatz verfügt. Falls nicht, wird die Darstellung des Hauptformulars der Entität angezeigt.  
  
 Wenn das Unterraster Aktivitäten anzeigt, müssen Benutzer zuerst die Art der Aktivität auswählen; anschließend sehen sie die Verhaltensweise „Neuen Datensatz hinzufügen“.  
  
## <a name="delete-record-behavior"></a>Verhalten beim Löschen von Datensätzen  
 Wenn Sie einen Datensatz in einem Unterraster auswählen, wird die Schaltfläche **Löschen** ![Symbol für Löschen der untergeordneten Liste](media/crm-itpro-cust-subgriddelete.PNG "Symbol: Löschen der untergeordneten Liste") rechts neben der Zeile angezeigt. Die Verhaltensweisen dieser Löschaktion unterscheidet sich je nach der Art der Beziehung zur aktuellen Entität.  
  
 Wenn das Unterraster eine 1:n-Beziehung verwendet, besteht das normale Datensatzlöschverhalten darin, dass ein Bestätigungsdialogfeld angezeigt wird, bevor der Datensatz gelöscht wird.  
  
 Wenn das Unterraster eine n:n-Beziehung verwendet, wird der Datensatz in der Beziehungs- (oder Überschneidungs-) Entität in Bezug auf zwei Datensätze ohne Bestätigung gelöscht, und der Datensatz wird nicht mehr im Unterraster angezeigt. Der Datensatz, der angezeigt wurde, wird jedoch nicht gelöscht.  

## <a name="next-steps"></a>Nächste Schritte

[Verwenden des Hauptformulars und seiner Komponenten](use-main-form-and-components.md)
