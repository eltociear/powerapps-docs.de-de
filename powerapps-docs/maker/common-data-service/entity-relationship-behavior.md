---
title: Entitätbeziehungsverhalten (Common Data Service) | Microsoft Docs
description: <Description>
ms.custom: ''
ms.date: 08/01/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: Mattp123
ms.author: matp
manager: kvivek
---
# <a name="entity-relationship-behavior"></a>Entitätenbeziehungsverhalten

Verhalten für verknüpfte Entitäten sind wichtig, weil sie helfen, die Datenintegrität zu gewährleisten und Geschäftsprozesse für das Unternehmen automatisieren zu können.

## <a name="preserve-data-integrity"></a>Datenintegrität erhalten

Einige Entitäten sind vorhanden, um andere Entitäten zu unterstützen. Sie können möglicherweise keinen Sinn ergeben. Sie haben in der Regel ein erforderliches Suchfeld, um mit der primären Entität verknüpft zu werden, die sie unterstützen. Was sollte geschehen, wenn der primäre Entitätsdatensatz gelöscht wird?

Sie können das Verhalten von Beziehungen verwenden, um das entsprechend den Regeln für Ihr Unternehmen zu definieren. Zwei Optionen sind:

- Vermeiden Sie es, die primäre Entität zu löschen, sod dass die damit verknüpften Entitätsdatensätze abgestimmt werden können, indem Sie einer primären anderen Entität zugeordnet sind.
- Erlauben Sie, dass die verknüpften Entitäten automatisch mit dem Löschen des Datensatzes der primären Entität gelöscht werden.

Wenn die verknüpfte Entität keine primäre Entität unterstützt, können Sie erlauben, dass die primäre Entität gelöscht werden kann und der Wert der Suche gelöscht wird.

## <a name="automate-business-processes"></a>Automatisieren von Geschäftsprozessen
  
Angenommen Sie haben einen neuen Vertriebsmitarbeiter und möchten diesem eine Reihe vorhandener Konten zuweisen, die derzeit noch anderen Vertriebsmitarbeitern zugewiesen sind. Jedem Firmendatensatz kann eine Reihe von Aufgabenaktivitäten zugeordnet sein. Sie können die aktiven Konten, die Sie erneut zuweisen möchten, einfach finden und dem neuen Vertriebsmitarbeiter zuweisen. Was geschieht jedoch mit den Aufgabenaktivitäten, die den Konten zugeordnet sind? Möchten Sie jede einzelne Aufgabe öffnen und entscheiden, ob sie ebenfalls dem neuen Vertriebsmitarbeiter zugewiesen werden sollen? Vermutlich nicht. Stattdessen können Sie die Beziehung automatisch einige Standardregeln anwenden lassen. Diese Regeln werden ausschließlich auf die Aufgabendatensätze angewendet, die den Konten zugeordnet sind, die Sie erneut zuweisen. Ihre Optionen sind:  
  
- Neuzuweisen aller aktiven Aufgaben.  
- Neuzuweisen aller Aufgaben. 
- Neuzuweisen keiner der Aufgaben.  
- Neuzuweisen aller dem vorherigen Besitzer der Verkaufschance zugewiesenen Konten.  
  
Die Beziehung kann steuern, wie Aktionen, die für einen Datensatz für den primären Entitätsdatensatz durchgeführt werden bis hin zu allen zugehörigen Entitätsdatensätzen weitergereicht werden.  

## <a name="behaviors"></a>Verhalten

Es gibt mehrere Verhaltensarten, die angewendet werden können, wenn bestimmte Aktionen auftreten.

|Verhalten|Beschreibung|
|--|--|
|**Aktive kaskadieren**|Durchführen der Aktion für alle aktiven verknüpften Entitätsdatensätze.|
|**Alle kaskadieren**|Durchführen der Aktion für alle verknüpften Entitätsdatensätze.|
|**Nicht kaskadieren**|Keine Aktion.|
|**Link entfernen**|Entfernen Sie den Suchenwert für alle verknüpften Datensätze.|
|**Einschränken**|Verhindern, dass der primäre Entitätsdatensatz gelöscht wird, wenn Entitätsdatensätze vorhanden sind.|
|**Benutzereigene kaskadieren**|Durchführen der Aktion für alle verknüpften Entitätsdatensätze, deren Besitzer mit dem des primären Entitätsdatensatzes identisch ist.|

## <a name="actions"></a>Aktionen

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

## <a name="limitations-on-behaviors-you-can-set"></a>Einschränkungen hinsichtlich der einstellbaren Verhaltensweisen
  
Bei übergeordneten Beziehungen gibt es einige Einschränkungen, an die Sie bei der Definition von Entitätsbeziehungen denken sollten.  
  
- Eine benutzerdefinierte Entität kann in einer Beziehung, bei der eine verknüpfte Systementität kaskadiert, nicht als primäre Entität fungieren. Das heißt, es kann keine Beziehung eingerichtet werden, wenn eine Aktion zwischen einer primären benutzerdefinierten Entität und einer verknüpften Systementität auf **Alle kaskadieren**, **Aktive kaskadieren** oder **Kaskadieren, falls gleicher Besitzer** festgelegt ist.  
- Bei keiner neuen Beziehung kann eine Aktion auf **Alle kaskadieren**, **Aktive kaskadieren** oder **Kaskadieren, falls gleicher Besitzer** festgelegt werden, wenn die verknüpfte Entität in dieser Beziehung bereits als verknüpfte Entität in einer anderen Beziehung vorhanden ist, bei der eine Aktion auf **Alle kaskadieren**, **Aktive kaskadieren** oder **Kaskadieren, falls gleicher Besitzer**. Dadurch werden Beziehungen verhindert, die aus mehreren übergeordneten Beziehungen bestehen.  
