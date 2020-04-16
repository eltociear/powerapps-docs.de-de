---
title: Abrufen und Löschen des Verlaufs von überwachten Datenänderungen (Common Data Service) | Microsoft-Dokumentation
description: Programmgesteuert die Überwachungsänderungsgeschichte abrufen oder Prüfprotokolle deaktivieren.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: paulliew
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c42e00535df1fad95ec9b133d880b17b9dd17733
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155334"
---
# <a name="retrieve-and-delete-the-history-of-audited-data-changes"></a>Abrufen und Löschen des Verlaufs von überwachten Datenänderungen

Wenn die Überwachung aktiviert ist und Datenänderungen an diesen Entitäten und Attributen vorgenommen werden, die überwacht werden, können Sie fortfahren und den Datenänderungsverlauf abrufen. Optional können Sie die Überwachungsprotokolle löschen, nachdem Sie den Änderungsverlauf überprüft haben. Folgen Sie dem Beispielcodelink am Ende dieses Hilfethemas, um weitere Informationen zu erhalten.  
  
## <a name="retrieve-the-change-history"></a>Abrufen des Änderungsverlaufs 
 
 Es gibt mehrere Meldungsanforderungen, die verwendet werden können, um den Überwachungsänderungsverlauf abzurufen. Diese Anforderungen werden unterschieden nach der Art dessen, was sie abrufen. 
<!-- Bug 696490 should make the Audit entity public again: Refer to the topic  [Audit Entity](entities/audit.md) for a list of message requests related to auditing. -->
Über den Beispiellink am Ende dieses Themas gelangen Sie zu Beispielcode, der einige dieser Meldungsanforderungen für den Änderungsverlauf veranschaulicht.

## <a name="delete-the-change-history-for-a-record"></a>Überwachungsdatensatz-Änderungsverlauf löschen
 
 Verwenden Sie die <xref:Microsoft.Crm.Sdk.Messages.DeleteRecordChangeHistoryRequest> Nachricht, um alle Überwachungsänderungsverlaufsdatensätze für einen bestimmten Datensatz zu löschen. Hiermit können Sie die Überwachungsänderungsgeschichte für einen Datensatz löschen, anstatt alle Prüfprotokolle für einen Datumsbereich zulöschen, der im nächsten Abschnitt abgedeckt ist. Um den Überwachungsänderungsverlauf für einen Datensatz zu löschen, müssen Sie über eine Sicherheitsrolle mit dem **prvDeleteRecordChangeHistory** verfügen oder ein Systemadministrator werden.

## <a name="delete-the-change-history-for-a-date-range"></a>Überwachungsdatensatz-Änderungsverlauf löschen

 Sie können `audit`-Datensätze mithilfe der Anforderung <xref:Microsoft.Crm.Sdk.Messages.DeleteAuditDataRequest> löschen. Überwachungsdatensätze werden sequentiell vom ältesten zum neuesten Vorgang gelöscht. Die Funktionalität dieser Anforderung unterscheidet sich etwas, basierend auf der Edition von Microsoft SQL Server, die von Ihrem Common Data Service-Server verwendet wird. Common Data Service verwendet eine Enterprise Edition von SQL Server.

 Wenn der Common Data Service-Server die SQL Server Standard Edition nutzt, welche die Datenbankpartitionierungsfunktion nicht unterstützt, löscht die <xref:Microsoft.Crm.Sdk.Messages.DeleteAuditDataRequest>-Anforderung alle Überwachungsprotokolle, die bis zu dem Enddatum erstellt wurden, das in der Eigenschaft <xref:Microsoft.Crm.Sdk.Messages.DeleteAuditDataRequest.EndDate> angegeben ist.

 Wenn der Common Data Service-Server eine Enterprise Edition von SQL Server nutzt, welche Partitionierung unterstützt, löscht die <xref:Microsoft.Crm.Sdk.Messages.DeleteAuditDataRequest>-Anforderung alle Überwachungsdaten in den Partitionen, deren Enddatum vor dem Datum liegt, das in der Eigenschaft <xref:Microsoft.Crm.Sdk.Messages.DeleteAuditDataRequest.EndDate> angegeben ist. Alle leeren Partitionen werden ebenfalls gelöscht. Allerdings können weder die aktuelle (aktive) Partition noch die `audit`-Datensätze in dieser aktiven Partition gelöscht werden, indem diese Anforderung oder eine andere Anforderung verwendet wird.

 Neue Partitionen werden automatisch von der Common Data Service-Plattform auf vierteljährlicher Basis jedes Jahr erstellt. Diese Funktionalität ist nicht konfigurierbar und kann nicht geändert werden. Sie können die Liste der Partitionen mithilfe der <xref:Microsoft.Crm.Sdk.Messages.RetrieveAuditPartitionListRequest>-Anforderung abrufen. Wenn das Enddatum einer Partition nach dem aktuellen Datum liegt, können Sie diese Partition oder darin enthaltene `audit`-Datensätze nicht löschen.  

### <a name="see-also"></a>Siehe auch

 [Datenverwaltung in Dynamics 365](/dynamics365/customer-engagement/developer/manage-data)<br />
 [Überwachung von Entitätsdatenänderungen](/dynamics365/customer-engagement/developer/audit-entity-data-changes)<br />
 [Benutzerzugriff überwachen](audit-user-access.md) <br />
 [Beispiel: Überwachung von Entitätsdatenänderungen](org-service/samples/audit-entity-data-changes.md)