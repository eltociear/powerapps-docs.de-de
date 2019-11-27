---
title: 'Erstellen oder Bearbeiten von 1: N (1: n- oder n): n: 1-) Entitätsbeziehungen (1 mithilfe des Lösungs-Explorers | MicrosoftDocs'
description: Weitere Informationen über das Erstellen von 1:n oder n:1 Entitätsbeziehungen mithilfe des PowerApps-Lösungs-Explorers
ms.custom: ''
ms.date: 10/28/2018
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
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3488b8228841f7b5323daee972472884e7c873d8
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2758146"
---
# <a name="create-and-edit-1n-one-to-many-or-n1-many-to-one-entity-relationships-using-solution-explorer"></a>Erstellen oder Bearbeiten von 1: N (eine-zu-vielen) oder N:1 (viele-zu-einer) Entitätsbeziehung mithilfe des Lösungs-Explorers 

Der Lösungs-Explorer bietet eine Möglichkeit, um 1:N (eine-zu-vielen) oder N:1 (viele-zu einer) Entitätsbeziehungen für Common Data Service zu erstellen und zu bearbeiten.

Das [PowerApps-Portal](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) ermöglicht das Konfigurieren der allgemeinen Optionen, jedoch können bestimmte Optionen nur mithilfe des Projektmappen-Explorers festgelegt werden. Weitere Informationen: 
- [1:N (1: n) oder N:1-Beziehungen erstellen](create-edit-1n-relationships.md)
- [Erstellen und Bearbeiten von 1:N (eine-zu-vielen) oder N:1 (viele-zu einer) Entitätsbeziehungen im PowerApps-Portal](create-edit-1n-relationships-portal.md)
  
## <a name="open-solution-explorer"></a>Öffnen Sie den Lösungs-Explorer

Ein Teil des Namens jeder benutzerdefinierten Entität, die Sie erstellen, ist das Anpassungspräfix. Dieser Satz basiert auf dem Lösungsherausgeber für die Lösung, in der Sie arbeiten. Wenn Ihnen das Anpassungspräfix wichtig ist, achten Sie darauf, dass Sie in einer nicht verwalteten Lösung oder der Standardlösung arbeiten, in der das Anpassungspräfix Ihren Wünschen für diese Entität entspricht. Weitere Informationen [Lösungsherausgeberpräfix ändern](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-entity-relationships"></a>Zeigen Sie Entitätsbeziehungen an

Im Lösungexplorer erweitern Sie **Entitäten** und wählen eine Entität. In der Entität wählen Sie entweder **1:N-Beziehungen** oder **N:1-Beziehungen** aus.

![Zeigen Sie Entitätsbeziehungen an](media/view-1n-entity-relationships-solution-explorer.png)

## <a name="create-relationships"></a>Beziehung erstellen

Während [Betrachtungsentitätsbeziehungen anzeigen](#view-entity-relationships), wählen Sie entweder **Neue 1:n-Beziehung** oder **Neue n:1-Beziehung** aus der Befehlsleiste aus.

> [!NOTE]
> Wenn die Befehle nicht verfügbar sind, kann die Entität keine benutzerdefinierte Beziehung erstellen.

Jede Option wird ein Formular öffnen, wie beispielsweise folgende. Der Unterschied ist, ob das Feld **Primäre Entität** oder **Verknüpfte Entität** festgelegt ist.

![Neues eines-zu-vielen-Beziehungsformular](media/new-1n-entity-relationship-form-solution-explorer.png)

- Mit **1: N-Beziehung** wird die **Primäre Entität** auf die aktuelle Entität festgelegt
- Mit **1:N-Beziehung** wird die **Verknüpfte Entität** auf die aktuelle Entität festgelegt

Die folgenden Felder müssen so festgelegt sein, um die Entitätsbeziehung zu speichern:

|Erforderliches Feld|Beschreibung|
|--|--|
|**Primäre Entität**|Diese Entität wird der Zieltyp für das Suchfeld, das für die verknüpfte Entität erstellt wird.|
|**Verknüpfte Entität**|Die Entität weist ein Suchfeld, das hinzugefügt wird, und die Entitätsdatensätze dem Datensatz der primären Entität zuzuordnen.|
|**Name**|Der Name der Beziehung. Ein Wert wird auf dem primären und dem verknüpften Entität Wert generiert. Dieses Feld wird durch den Anpassungspräfix des Lösungsherausgebers definiert.|
|**Anzeigename für das Suchfeld**|Diese Entität wird der Zieltyp für das Suchfeld, das für die verknüpfte Entität erstellt wird. Dies ist in der Regel gleich wie der Anzeigenamen für die primäre Entität. <br /> Dieses Limit kann später geändert werden.|
|**Name des Suchfelds**|Der Name für das Suchfeld, das für die verknüpfte Entität erstellt wird. Ein Wert wird basierend auf dem Wert im **Suchfeld Anzeigename** generiert. Dieses Feld wird durch den Anpassungspräfix des Lösungsherausgebers definiert.|

Sie können ![Entitätsbeziehungsschaltfläche speichern](media/save-entity-icon-solution-explorer.png) klicken, um die Entität zu speichern und die Bearbeitung fortsetzen. Weitere Informationen: [Beziehungsinformationen bearbeiten](#edit-relationships)

> [!NOTE]
> Wenn die Werte für **Name** oder **Feldname Suchen** bereits im System vorhanden sind, erhalten Sie beim Speichern eine Fehlermeldung. Bearbeiten Sie die Werte, damit sie eindeutig sind und versuchen Sie es erneut.

## <a name="edit-relationships"></a>Beziehungen bearbeiten

Während dem [Anzeigen von Entitätsbeziehungen](#view-entity-relationships) wählen Sie die Entität aus, die Sie bearbeiten möchten. Die folgenden Entitätsbeziehungseigenschaften können bearbeitet werden, wenn die Beziehung erstellt wurde.

> [!NOTE]
> Der Herausgeber einer verwalteten Lösung kann Anpassungen von Beziehungen verhindern, die Teil der Lösung sind.

### <a name="entity-relationship-properties"></a>Entitäsbeziehungseigenschaften

Diese Eigenschaften beziehen Sich auf die Beziehung.

|Feld|Beschreibung|
|--|--|
|**Durchsuchbar**|Ob diese Beziehung in der erweiterten Suche in Modell-angetriebenen Apps sichtbar sein soll. Wählen Sie **Nein** wenn es sich um eine Beziehung handelt, die nicht für ein Unternehmen von entscheidender Bedeutung ist.|
|**Hierarchisch**|Diese Option wird nur für auf sich selbst verweisende Beziehungen aktiviert. Ob dier Entität berücksichtigt wird, um eine Hierarchie für die Entität zu definieren.<br />**Wichtig**: Nachdem Sie auch diese Eigenschaften-Roll-up Felder festgelegt sind, können Ansichten abhängig von dieser Eigenschaft konfiguriert werden. Wenn Sie später diesen Wert ändern, funktionieren jene Funktionen, die von dieser Hierarchie abhängen, nicht. <br />Weitere Informationen: [Definieren und Abfragen von hierarchisch verknüpften Daten](define-query-hierarchical-data.md)|

### <a name="lookup-field"></a>Nachschlagefeld

Das sind die Eigenschaften des Suchfelds, das für die verknüpfte Entität erstellt wird. Die Eigenschaften können hier oder direkt im Suchfeld bearbeitet werden. Einige Feldeigenschaften sind nicht in der Beziehung bearbeitbar. Weitere Informationen: [Bearbeiten eines Feldes](create-edit-field-solution-explorer.md#edit-a-field)

|Feld|Beschreibung|
|--|--|
|**Anzeigename**|Diese Entität wird der Zieltyp für das Suchfeld, das für die verknüpfte Entität erstellt wird.|
|**Feldanforderung**|Ob das Feld Daten verfügen muss, damit ein Formular in einer Modell-angetriebenen App gespeichert werden kann. Weitere Informationen: [Feldanforderungsoptionen](create-edit-field-solution-explorer.md#field-requirement-options)|
|**Beschreibung**|Geben Sie Instruktionen für den Benutzer ein, um was es sich beim Feld handelt. Diese Beschreibung erscheint als Quickinfo für den Benutzer in Modell-angetriebenen Apps, wenn diese mit der Maus über die Beschriftung des Felds fahren.|

### <a name="navigation-pane-item-for-primary-entity"></a>Navigationsbereichelement für primäre Entität

Von der primären Entität können Sie zu den verknüpften Datensätzen navigieren. Diese Daten werden durch Modell-angetriebene Apps verwendet, um zu steuern, wie der verknüpfte Entitätsdatensatz angezeigt werden soll. Diese Einstellungen können Sie mithilfe des Formular-Editors auch bearbeiten.

|Feld|Beschreibung|
|--|--|
|**Anzeigeoption**|Wie die Liste der verknüpften Entität angezeigt werden soll. Weitere Informationen: [Anzeigeoptionen](#display-options)|
|**Benutzerdefiniertes Etikett**|Geben Sie den lokalisierbaren Text ein, der anstelle des Pluralnamens verwendenden wird, wenn Sie **Benutzerdefinierte Beschriftung verwenden** als **Anzeigeoption** haben.|
|**Anzeigebereich**|Wählen Sie eine der verfügbaren Gruppierungen aus, um diese Liste anzuzeigen. Die verfügbaren Optionen sind: **Details** (für die Gruppe *Allgemein* ), **Marketing**, **Vertrieb** und **Service**. |
|**Anzeigereihenfolge**|Steuert, wo das Navigationselement in dem ausgewählten Anzeigebereich eingesetzt wird. Der Bereich der zulässigen Zahlen beginnt bei 10.000. Navigationsbereichselemente mit einem niedrigeren Wert werden über anderen Beziehungen mit einem höheren Wert angezeigt.|

<!-- TODO: Not sure whether Display Area or Display Order are still used anymore. Might only be used in the Outlook client?-->

#### <a name="display-options"></a>Anzeigeoption

Dies sind die verfügbaren Anzeigenoptionen:

|Option|Beschreibung|
|--|--|
|**Nicht anzeigen**|Zeigen Sie die verknüpften Entitäten für diese Beziehung an.|
|**Benutzerdefinierte Beschriftung verwenden**|Wenn diese Option ausgewählt ist, wird das Feld **Benutzerdefinierte Beschriftung** aktiviert, damit Sie den lokalisierbaren Text anstelle des Pluralnamens angeben können.|
|**Pluralnamen verwenden**|Hiermit wird der für die verknüpfte Entität definierte Pluralname verwendet.|

### <a name="relationship-behavior"></a>Verhalten von Beziehungen

Hier können Sie Standardverhalten für verknüpfte Entitäten definieren. Diese Informationen sind wichtig, weil sie helfen, die Datenintegrität zu gewährleisten und Geschäftsprozesse für das Unternehmen automatisieren zu können.

Sehen wir uns ein Beispiel an.  
  
Angenommen Sie haben einen neuen Vertriebsmitarbeiter und möchten diesem eine Reihe vorhandener Verkaufschancen zuweisen, die derzeit noch anderen Vertriebsmitarbeitern zugewiesen sind. Jedem Verkaufschancendatensatz kann eine Reihe von Aufgabenaktivitäten zugeordnet sein. Sie können die aktiven Verkaufschancen, die Sie erneut zuweisen möchten, einfach finden und dem neuen Vertriebsmitarbeiter zuweisen. Was geschieht jedoch mit den Aufgabenaktivitäten, die den Verkaufschancen zugeordnet sind? Möchten Sie jede einzelne Aufgabe öffnen und entscheiden, ob sie ebenfalls dem neuen Vertriebsmitarbeiter zugewiesen werden sollen? Vermutlich nicht. Stattdessen können Sie die Beziehung automatisch einige Standardregeln anwenden lassen. Diese Regeln werden ausschließlich auf die Aufgabendatensätze angewendet, die den Verkaufschancen zugeordnet sind, die Sie erneut zuweisen. Ihre Optionen sind:  
  
- Neuzuweisen aller aktiven Aufgaben.  
- Neuzuweisen aller Aufgaben. 
- Neuzuweisen keiner der Aufgaben.  
- Neuzuweisen aller dem vorherigen Besitzer der Verkaufschance zugewiesenen Aufgaben.  
  
Die Beziehung kann steuern, wie Aktionen, die für einen Datensatz für den primären Entitätsdatensatz durchgeführt werden bis hin zu allen zugehörigen Entitätsdatensätzen weitergereicht werden.   

Es gibt mehrere Verhaltensarten, die angewendet werden können, wenn bestimmte Aktionen auftreten.

#### <a name="behaviors"></a>Verhalten

Dies sind die Verhalten, die zum Konfigurieren zur Verfügung stehen.

|Verhalten|Beschreibung|
|--|--|
|**Aktive kaskadieren**|Durchführen der Aktion für alle aktiven verknüpften Entitätsdatensätze.|
|**Alle kaskadieren**|Durchführen der Aktion für alle verknüpften Entitätsdatensätze.|
|**Nicht kaskadieren**|Keine Aktion.|
|**Link entfernen**|Entfernen Sie den Suchenwert für alle verknüpften Datensätze.|
|**Einschränken**|Verhindern, dass der primäre Entitätsdatensatz gelöscht wird, wenn Entitätsdatensätze vorhanden sind.|
|**Benutzereigene kaskadieren**|Durchführen der Aktion für alle verknüpften Entitätsdatensätze, deren Besitzer mit dem des primären Entitätsdatensatzes identisch ist.|

#### <a name="actions"></a>Aktionen

Dies sind die Aktionen, die dieses Verhalten auslösen können:

|Feld|Beschreibung|Optionen|
|--|--|--|
|**Zuweisen**|Was sollte geschehen, wenn der primäre Entitätsdatensatz mit einem anderen Datensatz zusammengeführt wird?|Alle kaskadieren<br />Aktive kaskadieren<br />Kaskadieren, falls gleicher Besitzer<br />Nicht kaskadieren|
|**Erneut überordnen**|Was sollte geschehen, wenn ein Suchfeldwert für eine übergeordnete Beziehung in dem primären Entitätsdatensatz geändert wird?<br />Weitere Informationen: [Übergeordnete Entitätsbeziehungen](#parental-entity-relationships)|Alle kaskadieren<br />Aktive kaskadieren<br />Kaskadieren, falls gleicher Besitzer<br />Nicht kaskadieren|
|**Freigeben**|Was sollte geschehen, wenn der primäre Entitätsdatensatz freigegeben wird?|Alle kaskadieren<br />Aktive kaskadieren<br />Kaskadieren, falls gleicher Besitzer<br />Nicht kaskadieren|
|**Löschen**|Was sollte geschehen, wenn der primäre Entitätsdatensatz gelöscht wird?|Alle kaskadieren<br />Link entfernen<br />Einschränken|
|**Freigabe aufheben**|Was sollte geschehen, wenn ein primäre Entitätsdatensatz freigegeben wird?|Alle kaskadieren<br />Aktive kaskadieren<br />Kaskadieren, falls gleicher Besitzer<br />Nicht kaskadieren|
|**Zusammenführen**|Was sollte geschehen, wenn ein primäre Entitätsdatensatz zusammengefügt wird?|Alle kaskadieren<br />Nicht kaskadieren|
|**Rollupansicht**|Welches ist das gewünschte Verhalten der Rollupansicht, die in dieser Beziehung verknüpft wird? |Alle kaskadieren<br />Aktive kaskadieren<br />Kaskadieren, falls gleicher Besitzer<br />Nicht kaskadieren|

<!-- TODO: I find no official docs related to rollup views, but plenty of hits online: https://www.google.com/search?q=Dynamics+365++%27rollup+view%27 -->



#### <a name="type-of-behavior-options"></a>Verhaltenstypoptionen

Verwenden Sie das Feld **Verhaltenstyp**, um zwischen einem Datensatz auszuwählen, oder ob sie unabhängig konfigurieren möchten. 

|Option|Beschreibung|
|--|--|
|**Übergeordnet**|Alle kaskadieren **zuweisen**<br />**Neu zordnen**: Alle kaskadieren<br />**Teilen**: Alle kaskadieren<br />**Löschen**: Alle kaskadieren<br />**Teilen aufheben**: Alle kaskadieren<br />**Zusammenführen**: Keine kaskadieren<br />**Rollup-Ansicht**: Kaskadieren Sie keine \| Alle kaskadieren<br />|
|**Referenziell**|**Zuweisen**: Keine kaskadieren<br />**Neu zordnen**: Keine kaskadieren<br />**Teilen**: Keine kaskadieren<br />**Löschen**: Link entfernen<br />**Teilen aufheben**: Keine kaskadieren<br />**Zusammenführen**: Keine kaskadieren<br />**Rollup-Ansicht**: Kaskadieren Sie keine \| Alle kaskadieren<br />|
|**Referenziell, Löschbeschränkung**|**Zuweisen**: Keine kaskadieren<br />**Neu zordnen**: Keine kaskadieren<br />**Teilen**: Keine kaskadieren<br />**Löschen**: Einschränken<br />**Teilen aufheben**: Keine kaskadieren<br />**Zusammenführen**: Keine kaskadieren<br />**Rollup-Ansicht**: Kaskadieren Sie keine \| Alle kaskadieren<br />|
|**Konfigurierbare Kaskadierung**|Sie können das Verhalten konfigurieren für jede Aktion, abhängig von der verfügbaren Optionen|

> [!NOTE]
> Sie können möglicherweise die Option **Übergeordnet** nicht auszuwählen, wenn eine der Entitäten bereits an einer übergeordneten Entitätsbeziehung beteiligt ist. Weitere Informationen: [Übergeordnete Entitätsbeziehungen](#parental-entity-relationships)
> 
> Wenn Sie die Verhaltensweisen **Kaskadieren konfigurierbar** für die Aktionen so einrichten, dass Sie den Verhaltensweisen der mit einem anderen **Verhaltenstyp** entsprechen, wenn Sie die Beziehung speichern, wird der **Verhaltenstyp** automatisch auf den entsprechenden Typ gesetzt.  



## <a name="delete-relationships"></a>Beziehungen löschen

Während [Betrachtungsentitätsbeziehungen](#view-entity-relationships) wählen Sie die Entitätsbeziehung, die Sie löschen möchten und klicken den Befehl ![Löschen](media/delete.gif).

Das Löschen der Beziehung löscht das Suchfeld der verknüpften Entität.

> [!NOTE]
> Sie können die Beziehung nicht löschen, die Abhängigkeiten enthält. Wenn Sie das Suchfeld in einem Formular für die verknüpfte Entität hinzugefügt haben, müssen Sie das Feld aus dem Formular entfernen, bevor Sie die Beziehung löschen.

## <a name="parental-entity-relationships"></a>Übergeordnete Entitätsbeziehungen

Zwischen jedem Entitätenpaar, das 1:n-Beziehung haben darf, können 1:n-Beziehungen bestehen. Dennoch kann nur eine dieser Beziehungen als übergeordnete Entitätsbeziehung gelten.

Jede übergeordnete Entitätsbeziehung ist eine 1:N Entitätsbeziehung, in der einer der kaskadierenden Optionen in der Spalte **übergeordnet** der folgenden Tabelle "true" ist.

|Aktion|Übergeordnet|Nicht übergeordnet|  
|------------|--------------|------------------|  
|**Zuweisen**|Alle kaskadieren<br />Kaskadieren, falls gleicher Besitzer<br />Aktive kaskadieren|Nicht kaskadieren|  
|**Löschen**|Alle kaskadieren|RemoveLink<br />Einschränken|  
|**Erneut überordnen**|Alle kaskadieren<br />Kaskadieren, falls gleicher Besitzer<br />Aktive kaskadieren|Nicht kaskadieren|  
|**Freigeben**|Alle kaskadieren<br />Kaskadieren, falls gleicher Besitzer<br />Aktive kaskadieren|Nicht kaskadieren|  
|**Freigabe aufheben**|Alle kaskadieren<br />Kaskadieren, falls gleicher Besitzer<br />Aktive kaskadieren|Nicht kaskadieren|  

Wenn Sie beispielsweise eine neue benutzerdefinierte Entität erstellen und der Firmenentität, bei der Ihre benutzerdefinierte Entität die verweisende Entität ist eine 1:n-Entitätsbeziehung mit hinzufügen, können Sie diese Aktionen für diese Entitätsbeziehung so konfigurieren, dass sie Optionen in der Spalte **Übergeordnet** verwenden. Wenn Sie Ihrer benutzerdefinierten Entität später eine andere 1: N-Entitätsbeziehung als verweisende Entität hinzufügen, können Sie die Aktionen nur so konfigurieren, dass die Optionen in der Spalte **Nicht übergeordnet** verwendet werden.

Normalerweise bedeutet das, dass für jedes Entitätspaar lediglich eine zugeordnete Beziehung vorliegt. Es gibt Fälle, bei denen die verweisende Entität auf dem Verweis möglicherweise einen Verweis auf mehr als einen Entitätstyp enthält.

Wenn Sie beispielsweise eine Entität mit einer Kundensuche haben, kann die entweder auf einen Kontakt oder Firmaenentität verweisen. Es gibt in diesem Fall zwei übergeordnete 1: n-Entitätsbeziehungen.

Sämtliche Aktivitätsentität hat einen ähnlichen Satz übergeordnete Entitätsbeziehungen für Entitäten, die mithilfe des Suchfelds "Bezug" zugeordnet werden.

<a name="BKMK_RelationshipBehaviorLimitations"></a>   

### <a name="limitations-on-behaviors-you-can-set"></a>Einschränkungen hinsichtlich der einstellbaren Verhaltensweisen
  
Bei übergeordneten Beziehungen gibt es einige Einschränkungen, an die Sie bei der Definition von Entitätsbeziehungen denken sollten.  
  
- Eine benutzerdefinierte Entität kann in einer Beziehung, bei der eine verknüpfte Systementität kaskadiert, nicht als primäre Entität fungieren. Das heißt, es kann keine Beziehung eingerichtet werden, wenn eine Aktion zwischen einer primären benutzerdefinierten Entität und einer verknüpften Systementität auf **Alle kaskadieren**, **Aktive kaskadieren** oder **Kaskadieren, falls gleicher Besitzer** festgelegt ist.  
- Bei keiner neuen Beziehung kann eine Aktion auf **Alle kaskadieren**, **Aktive kaskadieren** oder **Kaskadieren, falls gleicher Besitzer** festgelegt werden, wenn die verknüpfte Entität in dieser Beziehung bereits als verknüpfte Entität in einer anderen Beziehung vorhanden ist, bei der eine Aktion auf **Alle kaskadieren**, **Aktive kaskadieren** oder **Kaskadieren, falls gleicher Besitzer**. Dadurch werden Beziehungen verhindert, die aus mehreren übergeordneten Beziehungen bestehen.  

### <a name="see-also"></a>Siehe auch

[Erstellen und Bearbeiten von Beziehungen zwischen Entitäten](create-edit-entity-relationships.md)<br />
[Erstellen oder Bearbeiten von 1: N (eine-zu-vielen) oder N:1 (viele-zu einer)-Entitätsbeziehungen](create-edit-1n-relationships.md)<br />
[Erstellen und Bearbeiten von 1:N (eine-zu-vielen) oder N:1 (viele-zu einer) Entitätsbeziehungen im PowerApps-Portal](create-edit-1n-relationships-portal.md)<br />
[N:N (n:n)-Beziehungen erstellen](create-edit-nn-relationships.md)

