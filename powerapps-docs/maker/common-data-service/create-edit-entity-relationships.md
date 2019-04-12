---
title: Erstellen und Bearbeiten von Entitäts-Beziehungen für Common Data Service | MicrosoftDocs
ms.custom: ''
ms.date: 05/26/2018
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
manager: brycho
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
 
## <a name="see-also"></a>Siehe auch

[Übersicht über Entitäten und Metadaten](create-edit-metadata.md)<br />
[Erstellen oder Bearbeiten von 1: N (eine-zu-vielen) oder N:1 (viele-zu einer)-Entitätsbeziehungen](create-edit-1n-relationships.md)<br />
[N:N (n:n)-Beziehungen erstellen](create-edit-nn-relationships.md)

