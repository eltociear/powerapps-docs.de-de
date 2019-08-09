---
title: Arten von Entitäten | MicrosoftDocs
ms.custom: ''
ms.date: 05/30/2018
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
ms.assetid: 2f3f6053-0b9e-41e7-bd94-2239351e9f4b
caps.latest.revision: 41
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="types-of-entities"></a>Arten von Entitäten

Bevor Sie Entitäten erstellen oder bearbeiten in Common Data Service, sollten Sie wissen, dass es verschiedene Arten von Entitäten gibt. Nachdem eine benutzerdefinierte Entität erstellt wurde, können diese Typen nicht geändert werden. Die beiden wichtigen Typen basieren auf dem Entitätsbesitz und darauf, ob es sich um aktive Entitäten handelt.  
  
<a name="BKMK_EntityOwnership"></a>

## <a name="entity-ownership"></a>Entitätsbesitz  

Es gibt vier verschiedene Arten von Entitätsbesitz. Wenn Sie eine benutzerdefinierte Entität erstellen, sind die einzigen Optionen **Im Besitz von Benutzer oder Team** oder **Im Besitz der Organisation**, aber Sie sollten beachten, dass andere Entitäten andere Besitztypen haben.  
  
|Besitz|Beschreibung|  
|---------------|-----------------|  
|**Unternehmenseigen**|Daten in diesen Entitäten gehören zur Unternehmenseinheit. Zugriff auf die Daten kann auf der Unternehmenseinheitebene gesteuert werden.|  
|**Keine**|Daten, die zu keiner anderen Entität gehören.|  
|**Im Besitz der Organisation**|Daten, die der Organisation gehören. Der Zugriff auf die Daten wird auf Organisationsebene gesteuert.|  
|**Benutzer- oder Teameigen**.|Daten, die zu einem Benutzer oder einem Team gehören. Aktionen, die für diese Datensätze ausgeführt werden, können auf Benutzerebene gesteuert werden.|  
  
  
> [!IMPORTANT]
>  Nachdem eine Entität erstellt wurde, kann das Besitzverhältnis nicht geändert werden. Bevor Sie eine Entität erstellen, müssen Sie sicherstellen, dass Sie den richtigen Besitztyp auswählen. Wenn Sie später feststellen, dass Ihre benutzerdefinierte Entität einen anderen Typs haben soll, müssen Sie sie löschen und eine neue erstellen.
  
<a name="BKMK_ActivityEntities"></a>

## <a name="activity-entities"></a>Aktivitätsentitäten

Eine Aktivität ist eine Aktion, für die ein Eintrag in einem Kalender vorgenommen werden kann. Eine Aktivität hat Zeitdimensionen (Startzeit, Endzeit, Fälligkeitsdatum und Dauer), die dabei helfen, festzulegen, wann die Aktion auftrat oder auftreten soll. Aktivitäten enthalten auch Daten, die bestimmen helfen, welche Aktion die Aktivität repräsentiert, etwa Betreff und Beschreibung. Eine Aktivität kann geöffnet, storniert oder abgeschlossen werden. Der abgeschlossene Status einer Aktivität hat verschiedene verknüpfte Substatuswerte, die klären, in welcher Weise die Aktivität abgeschlossen wurde.  
  
Aktivitätsentitäten können jeweils nur einen Benutzer oder ein Team als Besitzer haben, eine Organisation ist dafür nicht möglich.  
  
Die folgende Tabelle listet Aktivitätsentitäten auf, die in einer standardmäßigen Common Data Service-Umgebung verfügbar sind.
  
|Name|Beschreibung|In Aktivitätsmenüs anzeigen|Referenz|
|----------|-----------------|----------------|---------------|  
|**Termin**|Verpflichtung, die ein Zeitintervall mit Start-/Endzeit und Dauer darstellt.|Ja|[Termin](/powerapps/developer/common-data-service/reference/entities/appointment)|
|**Email**|Aktivität, die unter Verwendung von E-Mail-Protokollen übermittelt wird.|Ja|[Email](/powerapps/developer/common-data-service/reference/entities/email)|
|**Fax**|Aktivität, die das Anrufergebnis sowie die Anzahl der Seiten eines Fax nachverfolgt und optional eine elektronische Kopie des Dokuments speichert|Ja|[Fax](/powerapps/developer/common-data-service/reference/entities/fax)|
|**Brief**|Aktivität, die die Zustellung eines Briefs nachverfolgt. Die Aktivität kann die elektronische Kopie des Briefs enthalten.|Ja|[Brief](/powerapps/developer/common-data-service/reference/entities/letter)|
|**Telefonanruf**|Aktivität zur Nachverfolgung eines Telefonanrufs.|Ja|[PhoneCall](/powerapps/developer/common-data-service/reference/entities/phonecall)|
|**Serientermin**|Der Mastertermin einer Terminserie.|Ja|[RecurringAppointmentMaster](/powerapps/developer/common-data-service/reference/entities/recurringappointmentmaster)|
|**Aufgabe**|Allgemeine Aktivität, die die auszuführende Arbeit darstellt|Ja|[Aufgabe](/powerapps/developer/common-data-service/reference/entities/task)|
  
Sie können neue benutzerdefinierte Aktivitätsentitäten erstellen. Sie können beispielsweise eine benutzerdefinierte Aktivitätsentität zur Aufzeichnung von IM-Kommunikationen erstellen. Die Erstellung einer Aktivitätsentität unterscheidet sich vom Erstellen einer Nicht-Aktivitätsentität, da Sie kein primäres Feld angeben. Alle Aktivitätsentitäten haben ein **Primäres Feld** mit **Betreff** und andere gemeinsame Felder, die durch die Aktivitätsentität definiert werden. Dies ermöglicht, alle Aktivitätstypen in einer Ansicht anzuzeigen, in der nur die gemeinsamen Felder angezeigt werden.  

> [!NOTE]
> Sie können eine benutzerdefinierte Aktivität nicht mithilfe des PowerApps-Portals erstellen. Sie müssen den Lösungs-Explorer über die Schaltfläche **Erweitert** öffnen.
  
Wenn Sie eine benutzerdefinierte Aktivitätsentität erstellen, wählen Sie **Als Aktivitätsentität definieren** aus. Nachdem Sie diese Option ausgewählt haben, sehen Sie, dass **In Aktivitätsmenüs anzeigen** ausgewählt ist. Mit dieser Einstellung können Personen diese Aktivitätsart in den Aktivitätsmenüs erstellen. Diese Option ist nicht für Aktivitäten ausgewählt, die in der Regel mit bestimmten Ereignissen verbunden sind und im Hintergrund mit Code oder durch einen Workflow erstellt werden. Eine spätere Änderung dieser Entität ist nach dem Speichern nicht möglich.  

### <a name="see-also"></a>Siehe auch
[Erstellen oder Bearbeiten von Entitäten](create-edit-entities.md)
