---
title: Entitätsbeziehungsübersicht für Common Data Service | MicrosoftDocs
ms.custom: ''
ms.date: 04/25/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
ms.assetid: c765b6d9-4d87-4c2d-aae2-5b1c3b664a71
caps.latest.revision: 28
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="entity-relationships-overview"></a>Überblick über Entitätsbeziehungen
Entitätsbeziehungen definieren, wie Datensätze in der Datenbank miteinander verknüpft werden können. Auf der einfachsten Ebene erstellt das Hinzufügen eines Suchfeldes zu einer Entität eine neue 1:n (eins-zu-viele)-Beziehung zwischen den beiden Entitäten und ermöglicht Ihnen, dieses Suchfeld in ein Formular einzusetzen. Mit dem Suchfeld können Benutzer mehrere *untergeordnete* Datensätze dieser Entität einer einzelnen *übergeordneten* Entität zuordnen.  
  
1:n-Entitätsbeziehungen definieren, wie Datensätze mit anderen Datensätzen verknüpft werden können, darüber hinaus stellen Sie Daten für die folgenden Fragen zur Verfügung:  
  
- Sollten beim Löschen eines Datensatzes auch alle mit diesem verknüpften Datensätze gelöscht werden?  
- Muss ich beim Zuweisen eines Datensatzes auch alle mit diesem verknüpften Datensätze dem neuen Besitzer zuweisen?  
- Wie kann ich den Dateneingabeprozess optimieren, wenn ich einen neuen verknüpften Datensatz im Kontext eines vorhandenen Datensatzes erstelle?  
- Wie sollten Benutzer, die einen Datensatz anzeigen, die verknüpften Datensätze anzeigen können?  
  
 Entitäten können auch an einer N:N-Beziehung teilnehmen, bei der eine Beliebige Zahl von Datensätzen für zwei Entitäten miteinander verknüpft werden kann.  

<a name="BKMK_Connections"></a>

## <a name="decide-whether-to-use-entity-relationships-or-connections"></a>Entscheiden ob Entitätsbeziehungen oder Verbindungen verwendet werden sollen 
Entitätsbeziehungen sind Metadaten, die Änderungen an der Datenbank vornehmen. Diese Beziehungen ermöglichen Abfragen zum sehr effizienten Abruf von Daten. Verwenden Sie Entitätsbeziehungen, um formale Beziehungen zu definieren, die die Entität definieren, oder die die meisten Datensätze verwenden können. Beispielsweise wäre eine Verkaufschance ohne einen potenziellen Kunden nicht sehr nützlich. Die Verkaufschancenentität verfügt auch über eine N:N-Beziehung mit der Mitbewerberentität. Dies ermöglicht das Hinzufügen mehrerer Mitbewerber zu der Verkaufschance. Möglicherweise möchten Sie diese Daten erfassen und einen Bericht anzeigen, der die Mitbewerber aufführt.  
  
Es gibt weitere, weniger formale Arten von Beziehungen zwischen Datensätzen - diese werden als *Verbindungen* bezeichnet. Beispielsweise kann es nützlich sein zu wissen, ob zwei Kontaktpersonen verheiratet oder miteinander befreundet sind, oder ob eine Kontaktperson für eine andere Firma gearbeitet hat. Die meisten Unternehmen erstellen keine Berichte mit dieser Art von Informationen oder verlangen ihre Eingabe, weshalb es sich wahrscheinlich nicht lohnt, hierfür Entitätsbeziehungen zu erstellen. Weitere Informationen: [Konfigurieren Sie Verbindungsrollen](configure-connection-roles.md)

  
<a name="BKMK_TypesOfRelationships"></a>
 
## <a name="types-of-entity-relationships"></a>Typen von Entitätsbeziehungen
Wenn Sie sich den Lösungsexplorer ansehen, denken Sie vielleicht, dass es drei Arten von Entitätsbeziehungen gibt. Tatsächlich sind es nur zwei, wie in der nachfolgenden Tabelle gezeigt.  
  
|Geschäftsbeziehungstyp|Beschreibung|  
|-----------------------|-----------------|  
|**1:n (Eins-zu-Viele)**|Eine Entitätsbeziehung, bei der ein Datensatz für die **Primäre Entität** mit mehreren anderen **Verknüpften Entitäts**-Datensätzen durch ein Suchfeld in der verknüpften Entität verknüpft werden kann.<br /><br /> Wenn Sie einen Datensatz der primären Entität anzeigen, sehen Sie eine Liste der verknüpften Datensätze, die dieser Entität zugeordnet sind.|  
|**N:N (Viele-zu-Viele)**|Eine Entitätsbeziehung, die von einer speziellen **Beziehungsentität** abhängig ist, oft als Überschneidungsentität bezeichnet, so dass mehrere Datensätze einer Entität mit mehreren Datensätzen einer anderen Entität verknüpft werden können.<br /><br /> Wenn Datensätze von verschiedenen Entitäten in einer N:N-Beziehung angezeigt werden, können Sie eine Liste aller Datensätze der anderen Entität anzeigen, die damit verknüpft sind.|  
  
Der **N:1 (many-to-one)**-Beziehungstyp besteht in der Benutzeroberfläche des Lösungsexplorers, da der Lösungsexplorer Ihnen eine nach Entitäten gruppierte Ansicht zeigt. 1:n-Beziehungen bestehen *zwischen* Entitäten und verweisen auf jede Entität entweder als **Primäre Entität**oder als **Verknüpfte Entität**. Die verknüpfte Entität, oft als *untergeordnete* Entität bezeichnet, verfügt über ein Suchfeld, in dem das Speichern eines Verweises zu einem Datensatz aus der primären Entität, oft als *übergeordnete* Entität bezeichnet, möglich ist. Eine n:1-Beziehung ist einfach eine 1:n-Beziehung aus der Perspektive der zugehörigen Entität.  
 
## <a name="entity-relationship-behavior"></a>Entitätenbeziehungsverhalten
Verhalten für verknüpfte Entitäten sind wichtig, weil sie helfen, die Datenintegrität zu gewährleisten und Geschäftsprozesse für das Unternehmen automatisieren zu können.

### <a name="preserve-data-integrity"></a>Datenintegrität erhalten
Einige Entitäten sind vorhanden, um andere Entitäten zu unterstützen. Sie können möglicherweise keinen Sinn ergeben. Sie haben in der Regel ein erforderliches Suchfeld, um mit der primären Entität verknüpft zu werden, die sie unterstützen. Was sollte geschehen, wenn der primäre Entitätsdatensatz gelöscht wird?

Sie können das Verhalten von Beziehungen verwenden, um das entsprechend den Regeln für Ihr Unternehmen zu definieren. Zwei Optionen sind:

- Vermeiden Sie es, die primäre Entität zu löschen, sod dass die damit verknüpften Entitätsdatensätze abgestimmt werden können, indem Sie einer primären anderen Entität zugeordnet sind.
- Erlauben Sie, dass die verknüpften Entitäten automatisch mit dem Löschen des Datensatzes der primären Entität gelöscht werden.

Wenn die verknüpfte Entität keine primäre Entität unterstützt, können Sie erlauben, dass die primäre Entität gelöscht werden kann und der Wert der Suche gelöscht wird.

### <a name="automate-business-processes"></a>Automatisieren von Geschäftsprozessen
Angenommen Sie haben einen neuen Vertriebsmitarbeiter und möchten diesem eine Reihe vorhandener Konten zuweisen, die derzeit noch anderen Vertriebsmitarbeitern zugewiesen sind. Jedem Firmendatensatz kann eine Reihe von Aufgabenaktivitäten zugeordnet sein. Sie können die aktiven Konten, die Sie erneut zuweisen möchten, einfach finden und dem neuen Vertriebsmitarbeiter zuweisen. Was geschieht jedoch mit den Aufgabenaktivitäten, die den Konten zugeordnet sind? Möchten Sie jede einzelne Aufgabe öffnen und entscheiden, ob sie ebenfalls dem neuen Vertriebsmitarbeiter zugewiesen werden sollen? Vermutlich nicht. Stattdessen können Sie die Beziehung automatisch einige Standardregeln anwenden lassen. Diese Regeln werden ausschließlich auf die Aufgabendatensätze angewendet, die den Konten zugeordnet sind, die Sie erneut zuweisen. Ihre Optionen sind:  
  
- Neuzuweisen aller aktiven Aufgaben.  
- Neuzuweisen aller Aufgaben. 
- Neuzuweisen keiner der Aufgaben.  
- Neuzuweisen aller dem vorherigen Besitzer der Verkaufschance zugewiesenen Konten.  
  
Die Beziehung kann steuern, wie Aktionen, die für einen Datensatz für den primären Entitätsdatensatz durchgeführt werden bis hin zu allen zugehörigen Entitätsdatensätzen weitergereicht werden.  

### <a name="behaviors"></a>Verhalten
Es gibt mehrere Verhaltensarten, die angewendet werden können, wenn bestimmte Aktionen auftreten.

|Verhalten|Beschreibung|
|--|--|
|**Aktive kaskadieren**|Durchführen der Aktion für alle aktiven verknüpften Entitätsdatensätze.|
|**Alle kaskadieren**|Durchführen der Aktion für alle verknüpften Entitätsdatensätze.|
|**Nicht kaskadieren**|Keine Aktion.|
|**Link entfernen**|Entfernen Sie den Suchenwert für alle verknüpften Datensätze.|
|**Einschränken**|Verhindern, dass der primäre Entitätsdatensatz gelöscht wird, wenn Entitätsdatensätze vorhanden sind.|
|**Benutzereigene kaskadieren**|Durchführen der Aktion für alle verknüpften Entitätsdatensätze, deren Besitzer mit dem des primären Entitätsdatensatzes identisch ist.|

### <a name="actions"></a>Aktionen
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


### <a name="parental-entity-relationships"></a>Übergeordnete Entitätsbeziehungen
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
[Übersicht über Entitäten und Metadaten](create-edit-metadata.md)<br />
[Erstellen oder Bearbeiten von 1: N (eine-zu-vielen) oder N:1 (viele-zu einer)-Entitätsbeziehungen](create-edit-1n-relationships.md)<br />
[N:N (n:n)-Beziehungen erstellen](create-edit-nn-relationships.md)

