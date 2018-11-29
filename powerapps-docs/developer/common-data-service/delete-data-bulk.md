---
title: Massenlöschung von Daten (Common Data Service for Apps) | Microsoft Docs
description: 'Massenlöschung von Daten hilft beim Aufrechterhalten der Datenqualität und Verwalten des Verbrauchs der Systemspeicherung, indem Daten gelöscht werden, die nicht mehr benötigt werden.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="delete-data-in-bulk"></a>Löschen von Datensätzen in einem Massenvorgang

Die *Massenlöschungs* funktion hilft Ihnen, die Datenqualität und den Verbrauch des Systemspeichers in Common Data Service (CDS) for Apps zu verwalten, indem nicht mehr benötigte Daten gelöscht werden. So können Sie beispielsweise die folgenden Daten in einem Massenvorgang löschen:  
  
- Veraltete Daten.  
  
- Daten, die irrelevant für das Unternehmen sind.  
  
- Nicht benötigter Test oder Beispieldaten.  
  
- Daten, die von anderen Systemen nicht ordnungsgemäß importiert werden.  
  
Mit Massenlöschung können Sie die folgenden Vorgänge ausführen:  
  
- Daten löschen über mehrere Entitäten.  
  
- Löschen von Datensätzen für eine bestimmte Entität.  
  
- E-Mail-Benachrichtigungen erhalten, wenn eine Massenlöschung endet.  
  
- Löschen Sie Daten in regelmäßigen Intervallen.  
  
- Planen Sie die Startzeit einer Serienmassenlöschung.  
  
- Rufen Sie die Informationen zum Fehler, die während einer Massenlöschung aufgetreten sind.  
  
## <a name="run-bulk-delete"></a>Massenlöschung durchführen

Zum Massenlöschen von Datensätzen müssen Sie einen Massenlöschungsauftrag mithilfe der <xref:Microsoft.Crm.Sdk.Messages.BulkDeleteRequest>-Meldung eingeben. Der Massenlöschungsauftrag wird asynchron im Hintergrund ausgeführt, ohne andere Aktivitäten zu blockieren. Die Abfrageausdrücke, die die Datensätze beschreiben, auf denen der Massenlöschungsauftrag ausgeführt werden soll, sind in der Eigenschaft <xref:Microsoft.Crm.Sdk.Messages.BulkDeleteRequest.QuerySet> dieser Anfrage angegeben.  
  
 Ein Massenlöschungsauftrag wird durch die Massenlöschvorgangsentität dargestellt. Der Schemaname für diese Entität ist `BulkDeleteOperation`. Ein Massenlöschungsvorgangsdatensatz enthält die folgenden Informationen:  
  
- Die Anzahl der Datensätze, die von einem Massenlöschungsauftrag gelöscht wurden.  
  
- Die Anzahl der Datensätze, die von einem Massenlöschungsauftrag nicht gelöscht werden konnten.  
  
- Ob der Massenlöschungsauftrag ein iterativer Auftrag ist oder nicht.  
  
- Die Startzeit des Massenlöschungsauftrags.  
  
  Ein Massenlöschungsauftrag löscht nur Datensätze, die vor seinem Beginn erstellt wurden.  
  
> [!NOTE]
>  Wenn ein Massenlöschungsauftrag fehlschlägt oder vorzeitig beendet wird, werde alle Datensätze, die vor dem Fehler oder dem Ende des Auftrags gelöscht wurden, nicht zurückgesetzt und bleiben gelöscht. Die Fehlschläge des `BulkDeleteOperation` werden in den `BulkDeleteFailure` gespeichert und können mit der Meldung <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest> oder <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest> abgerufen werden.  
  
 Ein Massenlöschungsauftrag löscht die angegebenen Datensätze in Übereinstimmung mit den Kaskadierungsregeln. Diese Regeln basieren auf dem Beziehungstyp zwischen den Entitäten. Weitere Informationen finden Sie unter [Verhalten von Entitätsbeziehungen](/dynamics365/customer-engagement/developer/entity-relationship-behavior).  
  
 Um einen Massenlöschungsauftrag auszuführen, müssen Benutzer über `BulkDelete` und `Delete`-Rechte für die Entitätstypen verfügen, die gelöscht werden. Der Benutzer muss auch über Leseberechtigungen für die Entitätsdatensätze verfügen, die in der Meldung <xref:Microsoft.Crm.Sdk.Messages.BulkDeleteRequest> angegeben werden. Standardmäßig verfügt ein Systemadministrator über die benötigten Berechtigungen; anderen Benutzern müssen diese Berechtigungen gewährt werden.  
  
 Sie können eine Massenlöschung für alle Entitäten ausführen, die von dem Löschvorgang unterstützt werden. Informationen zu möglichen Aktionen für Entitätsdatensätze finden Sie unter [Aktionen für Entitätsdatensätze](/dynamics365/customer-engagement/developer/introduction-entities#ActionsOnEntityRecords).  
  
 Wenn ein Plug-in oder ein Workflow (Prozess) durch den Löschvorgang für einen bestimmten Entitätstyp ausgelöst wird, wird dies jedesmal ausgelöst, wenn ein Entitätsdatensatz dieses Typs von dem Massenlöschungsvorgang gelöscht wird.  
  
## <a name="samples"></a>Beispiele

Schauen Sie sich die folgenden Beispiele für Organisationsdienste für die Massenlöschfunktion an:

- [Beispiel: Massenlöschung exportierter Datensätze](org-service/samples/bulk-delete-exported-records.md)   
- [Beispiel: Massenlöschen von Datensätzen, die allgemeinen Kriterien entsprechen](org-service/samples/bulk-delete-records-match-common-criteria.md)

### <a name="see-also"></a>Siehe auch

[BulkDeleteOperation-Entität](reference/entities/bulkdeleteoperation.md)