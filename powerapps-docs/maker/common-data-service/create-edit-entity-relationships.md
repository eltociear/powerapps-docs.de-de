---
title: Erstellen und Bearbeiten von Entitätsbeziehungen für Common Data Service für Apps | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/26/2018
ms.reviewer: ''
ms.service: crm-online
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
ms.openlocfilehash: 896b026bc72022e66e548db95f78d785e14fdf23
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39682682"
---
# <a name="create-and-edit-relationships-between-entities"></a>Erstellen und Bearbeiten von Beziehungen zwischen Entitäten 

Entitätsbeziehungen definieren, wie Datensätze in der Datenbank miteinander verknüpft werden können. Am einfachsten ist es, ein Suchfeld zu einer Entität hinzuzufügen, wodurch eine neue 1:n-Beziehung zwischen den beiden Entitäten erstellt wird und Sie dieses Suchfeld in ein Formular einfügen können. Über das Suchfeld können Benutzer einem einzelnen *übergeordneten* Entitätsdatensatz mehrere *untergeordnete* Datensätze dieser Entität zuordnen.  
  
Neben der bloßen Definition, wie Datensätze mit anderen Datensätzen verknüpft werden können, stellen 1:n-Entitätsbeziehungen außerdem Daten bereit, um die folgenden Fragen zu beantworten:  
  
- Sollen beim Löschen eines Datensatzes auch sämtliche Datensätze gelöscht werden, die mit diesem Datensatz verknüpft sind?  
- Müssen beim Zuweisen eines Datensatzes auch alle Datensätze, die mit diesem Datensatz verknüpft sind, dem neuen Besitzer zugewiesen werden?  
- Wie kann der Dateneingabeprozess optimiert werden, wenn ein neuer verknüpfter Datensatz im Kontext eines vorhandenen Datensatzes erstellt wird?  
- Wie können Benutzer, die einen Datensatz einsehen, die zugeordneten Datensätze einsehen?  
  
 Entitäten können auch Teil einer m:n-Beziehung sein, bei der eine beliebige Anzahl von Datensätzen für zwei Entitäten einander zugeordnet werden kann.  

<a name="BKMK_Connections"></a>

## <a name="decide-whether-to-use-entity-relationships-or-connections"></a>Festlegen, ob Entitätsbeziehungen oder Verbindungen verwendet werden sollen 
 
Entitätsbeziehungen sind Metadaten, die Änderungen an der Datenbank vornehmen. Durch diese Beziehungen können bei Abfragen äußerst effizient verknüpfte Daten abgerufen werden. Mithilfe von Entitätsbeziehungen können Sie formale Beziehungen definieren, die die Entität definieren oder die die meisten Datensätzen verwenden können. Eine Verkaufschance ohne einen potenziellen Kunden wäre beispielsweise nicht sehr nützlich. Die Verkaufschancenentität verfügt ebenfalls über eine m:n-Beziehung mit der Mitbewerberentität. Dadurch können der Verkaufschance mehrere Mitbewerber hinzugefügt werden. Sie sollten diese Daten erfassen und einen Bericht zu den Mitbewerbern erstellen.  
  
Es gibt andere weniger formale Arten von Beziehungen zwischen Datensätzen, die als *Verbindungen* bezeichnet werden. Beispielsweise kann es hilfreich sein, zu wissen, ob zwei Kontakte verheiratet sind, außerhalb der Arbeit eventuell Freunde sind oder ob ein Kontakt in der Vergangenheit schon mal für eine andere Firma gearbeitet hat. Die meisten Unternehmen generieren keine Berichte mit dieser Art von Informationen oder erfordern, dass diese eingegeben werden, weshalb es sich wahrscheinlich nicht lohnt, Entitätsbeziehungen zu erstellen. Weitere Informationen finden Sie unter [Konfigurieren von Verbindungsrollen](configure-connection-roles.md).

  
<a name="BKMK_TypesOfRelationships"></a>
 
## <a name="types-of-entity-relationships"></a>Arten von Entitätsbeziehungen

Wenn man den Lösungs-Explorer betrachtet, könnte man annehmen, dass es drei Typen von Entitätsbeziehungen gibt. Wie in der folgenden Tabelle dargestellt, sind es allerdings nur zwei.  
  
|Beziehungstyp|Beschreibung|  
|-----------------------|-----------------|  
|**1:n**|Eine Entitätsbeziehung, bei der ein Entitätseintrag zur **primären Entität** vielen anderen Einträgen zur **verknüpften Entität** zugewiesen werden kann, da auf der verknüpften Entität ein Nachschlagefeld verfügbar ist.<br /><br /> Wenn Sie einen Eintrag zu einer primären Entität abrufen, wird eine Liste der Einträge zu der verknüpften Entität angezeigt, die dieser zugewiesen sind.|  
|**m:n**|Eine Entitätsbeziehung, die von einer bestimmten **Beziehungsentität** (manchmal als sich überschneidende Entität bezeichnet) abhängig ist, damit mehrere Datensätze einer Entität mehreren Datensätzen einer anderen Entität zugeordnet werden können.<br /><br /> Wenn Sie die Datensätze einer beliebigen Entität in einer m:n-Beziehung anzeigen, wird eine Liste der Datensätze zu der anderen Entität angezeigt, die ihr zugeordnet sind.|  
  
Der Beziehungstyp **n:1** ist in der Benutzeroberfläche vorhanden, da der Designer Ihnen eine nach Entitäten gruppierte Ansicht anzeigt. Tatsächlich bestehen 1:n-Beziehungen *zwischen* Entitäten, und sie verweisen entweder als **primäre Entitäten** oder als **verknüpfte Entitäten** auf die einzelnen Entitäten. Die verknüpfte Entität, die manchmal als *untergeordnete* Entität bezeichnet wird, verfügt über ein Suchfeld, über das ein Verweis auf einen Datensatz aus der primären Entität, die auch als *übergeordnete* Entität bezeichnet wird, gespeichert werden kann. Aus der Sicht der verknüpften Entität ist eine n:1-Beziehung nur eine 1:n-Beziehung.  
 
## <a name="see-also"></a>Siehe auch

[Entitäten und Metadaten in Common Data Service für Apps](create-edit-metadata.md)<br />
[Erstellen von 1:n- oder n:1-Entitätsbeziehungen – Übersicht](create-edit-1n-relationships.md)<br />
[Übersicht über die Erstellung von m:n-Entitätsbeziehungen](create-edit-nn-relationships.md)

