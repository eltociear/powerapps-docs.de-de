---
title: Typen von Entitäten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/30/2018
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
ms.assetid: 2f3f6053-0b9e-41e7-bd94-2239351e9f4b
caps.latest.revision: 41
ms.author: matp
manager: kvivek
ms.openlocfilehash: 60e16ff8cb5c40a37cf0a5243b420f77c4a695bb
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39689714"
---
# <a name="types-of-entities"></a>Typen von Entitäten

Bevor Sie Entitäten in Common Data Service für Apps erstellen oder bearbeiten, müssen Sie wissen, dass es verschiedene Typen von Entitäten gibt. Sobald eine benutzerdefinierte Entität erstellt wurde, können diese Typen nicht mehr geändert werden. Die beiden wichtigsten Fragen sind dabei: Wer ist der Besitzer der Entität? Und handelt es sich um eine Aktivitätsentität?  
  
<a name="BKMK_EntityOwnership"></a>

## <a name="entity-ownership"></a>Besitz von Entitäten  

Der Besitz von Entitäten lässt sich in vier Typen einteilen. Wenn Sie eine benutzerdefinierte Entität erstellen, sind die einzigen verfügbaren Optionen **Im Besitz eines Benutzers oder Teams** oder **Im Besitz der Organisation**. Sie sollten jedoch beachten, dass andere Entitäten über andere Besitztypen verfügen.  
  
|Besitzer|Beschreibung|  
|---------------|-----------------|  
|**Im Besitz der Geschäftseinheit**|Daten in diesen Entitäten gehören der Geschäftseinheit. Der Zugriff auf diese Daten kann auf der Ebene der Geschäftseinheit gesteuert werden.|  
|**Keiner**|Daten, die keiner anderen Entität gehören.|  
|**Im Besitz der Organisation**|Daten, die der Organisation gehören. Der Zugriff auf diese Daten kann auf der Ebene der Organisation gesteuert werden.|  
|**Im Besitz eines Benutzers oder Teams**|Daten, die einem Benutzer oder einem Team gehören. Aktionen, die auf diese Datensätze verwendet werden können, können auf Benutzerebene gesteuert werden.|  
  
  
> [!IMPORTANT]
>  Nachdem eine Entität erstellt wurde, lässt sich der Besitzer nicht mehr ändern. Bevor Sie eine Entität erstellen, stellen Sie sicher, dass Sie den richtigen Besitztyp auswählen. Wenn Sie später feststellen, dass es sich bei Ihrer benutzerdefinierten Entität um einen anderen Typ handeln muss, müssen Sie sie löschen und eine neue Entität erstellen.
  
<a name="BKMK_ActivityEntities"></a>

## <a name="activity-entities"></a>Aktivitätsentitäten

Eine Aktivität kann eine beliebige Aktion sein, für die ein Eintrag in einem Kalender erstellt werden kann. Eine Aktivität hat Zeitdimensionen (Startzeit, Endzeit, Fälligkeitsdatum und Dauer), um zu bestimmen, wann die Aktion stattgefunden hat bzw. stattfinden wird. Aktivitäten enthalten auch Daten, die helfen zu bestimmen, welche Aktion die Aktivität darstellt (z.B. Betreff und Beschreibung). Eine Aktivität kann geöffnet, abgebrochen oder abgeschlossen werden. Dem Status „abgeschlossen“ einer Aktivität sind mehrere Unterstatuswerte zugeordnet, um zu verdeutlichen, wie die Aktivität abgeschlossen wurde.  
  
Aktivitätsentitäten können nur einem Benutzer oder einem Team gehören – keiner Organisation.  
  
Die folgende Tabelle führt die Aktivitätsentitäten auf, die in der Standardumgebung von Common Data Service für Apps verfügbar sind.
  
|Name|Beschreibung|Anzeige in Aktivitätsmenüs|Referenz|
|----------|-----------------|----------------|---------------|  
|**Appointment**|Eine Verpflichtung, die ein Zeitintervall mit einer Anfangs- und Endzeit sowie einer Dauer darstellt.|Ja|[Appointment](/powerapps/developer/common-data-service/reference/entities/appointment)|
|**Email**|Eine Aktivität, die über E-Mail-Protokolle übermittelt wird.|Ja|[E-Mail](/powerapps/developer/common-data-service/reference/entities/email)|
|**Fax**|Eine Aktivität, die Aufrufergebnisse und Seitenanzahlen für ein Fax nachverfolgt und optional eine elektronische Kopie des Elements speichert.|Ja|[Fax](/powerapps/developer/common-data-service/reference/entities/fax)|
|**Letter**|Eine Aktivität, die die Übermittlung einer Nachricht nachverfolgt. Diese Aktivität kann eine elektronische Kopie der Nachricht enthalten.|Ja|[Letter](/powerapps/developer/common-data-service/reference/entities/letter)|
|**Telefonanruf**|Eine Aktivität zum Nachverfolgen eines Anrufs.|Ja|[PhoneCall](/powerapps/developer/common-data-service/reference/entities/phonecall)|
|**Terminserie**|Der Mastertermin einer Terminserie.|Ja|[RecurringAppointmentMaster](/powerapps/developer/common-data-service/reference/entities/recurringappointmentmaster)|
|**Task**|Eine generische Aktivität, die ausstehende Arbeit darstellt.|Ja|[Task](/powerapps/developer/common-data-service/reference/entities/task)|
  
Sie können neue benutzerdefinierte Aktivitätsentitäten erstellen. Sie können beispielsweise eine benutzerdefinierte Aktivitätsentität erstellen, um Sofortnachrichten aufzuzeichnen. Das Erstellen einer Aktivitätsentität unterscheidet sich vom Erstellen einer Nichtaktivitätsentität, weil kein Hauptfeld angegeben wird. Alle Aktivitätsentitäten verfügen über ein **Hauptfeld**, das auf **Betreff** gesetzt ist, und andere allgemeine Felder, die von der Aktivitätsentität definiert werden. Dadurch können alle Typen von Aktivitäten in einer Ansicht angezeigt werden, in der nur allgemeine Felder sichtbar sind.  

> [!NOTE]
> Über das PowerApps-Portal lässt sich keine benutzerdefinierte Aktivität erstellen. Öffnen Sie den Projektmappen-Explorer über die Schaltfläche **Erweitert**.
  
Wählen Sie zum Erstellen einer benutzerdefinierten Aktivitätsentität **Als Aktivitätsentität definieren** aus. Daraufhin ist die Option **In Aktivitätsmenüs anzeigen** ausgewählt. Mit dieser Einstellung können Benutzer diesen Aktivitätstyp in den Aktivitätsmenüs erstellen. Diese Option wird nicht für Aktivitäten ausgewählt, die i.d.R. mit bestimmten Ereignissen verknüpft sind und mit Code oder einem Workflow erstellt werden. Nachdem die Entität gespeichert wurde, lassen sich diese Einstellungen nicht mehr ändern.  

### <a name="see-also"></a>Siehe auch
[Erstellen oder Bearbeiten von Entitäten](create-edit-entities.md)
