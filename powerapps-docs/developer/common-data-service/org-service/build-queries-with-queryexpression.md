---
title: Erstellen von Abfragen mit QueryExpression (Common Data Service) | Microsoft Docs
description: 'Lesen Sie, wie Sie die QueryExpression-Klasse zum programmgesteuerten Erstellen einer Abfrage, die Datenfilter und Suchbedingungen, die den Umfang einer Datenbanksuche definieren, enthält, verwenden können.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="build-queries-with-queryexpression"></a>Erstellen von Abfragen mit QueryExpression

In Common Data Service können Sie die <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>-Klasseverwenden, um programmgesteuert eine Abfrage zu erstellen, die Datenfilter und Suchbedingungen enthält, die den Umfang einer Datenbanksuche definieren. Ein Abfrageausdruck wird für Einzelobjektsuchen verwendet. Beispielsweise können Sie eine Suche erstellen, um alle Firmen zurückzugeben, die bestimmten Suchkriterien entsprechen. Die Klasse <xref:Microsoft.Xrm.Sdk.Query.QueryBase> ist die Basisklasse für Abfrageausdrücke. Es gibt zwei abgeleitete Klassen: <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> und <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute>. Die Klasse `QueryExpression` unterstützt komplexe Abfragen. Die Klasse `QueryByAttribute` ist eine einfache Möglichkeit, um nach Entitäten zu suchen, bei denen Attribute mit angegebenen Werten übereinstimmen.  
  
 Abfrageausdrücke werden in Methoden verwendet, die mehr als einen Datensatz abfragen, z.B. die <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*> Methode, in Nachrichten, die eine Operation mit einer durch einen Abfrageausdruck spezifizierten Ergebnismenge durchführen, z.B. <xref:Microsoft.Crm.Sdk.Messages.BulkDeleteRequest> und wenn die ID für einen bestimmten Datensatz nicht bekannt ist.  
  
 Darüber hinaus gibt es ein neues Attribut für die Organisationsentität, `Organization.QuickFindRecordLimitEnabled`. Wenn dieses `Boolean` Attribut `true` ist, wird Abfragen für die Schnellsuche ein Limit auferlegt. Wenn ein Benutzer bei der Schnellsuche Suchkriterien angibt, die nicht selektiv genug sind, wird dies vom System erkannt und die Suche wird beendet. Dies unterstützt eine schnellere Form der Schnellsuche und kann einen großen Leistungsunterschied ausmachen.  
  
> [!WARNING]
>  Rufen Sie nicht alle Attribute in einer Abfrage ab, da dadurch die Leistung beeinträchtigt wird. Das trifft insbesondere zu, wenn die Abfrage als Parameter in einer Updateanforderung verwendet wird. Wenn in einem Update alle Attribute enthalten sind, werden dadurch alle Feldwerte festgelegt, selbst wenn sie unverändert sind, und häufig werden kaskadierende Updates zu untergeordneten Datensätzen ausgelöst.  
  
 Es gibt zwei weitere Möglichkeiten, Abfragen zu erstellen, um Datensätze aus Common Data Service abzurufen. FetchXML, die herstellereigene Common Data Service-Abfragesprache, kann verwendet werden, um einige Abfragen auszuführen, indem XML-basierte Abfragen verwendet werden. Weitere Informationen finden Sie unter [Abfragen erstellen mit FetchXML](/dynamics365/customer-engagement/developer/org-service/build-queries-fetchxml). Sie können auch .NET Language-Integrated Query (LINQ) zum Schreiben von Abfragen verwenden. Weitere Informationen: [Erstellen von Abfragen mit LINQ (.NET Language-Integrated Query)](build-queries-with-linq-net-language-integrated-query.md).  
  
 Um eine Abfrage zu speichern, können Sie sie in FetchXML mithilfe von <xref:Microsoft.Crm.Sdk.Messages.QueryExpressionToFetchXmlRequest> konvertieren, und sie mithilfe der `userquery`-Entität als gespeicherte Ansicht speichern.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Verwenden der QueryByAttribute-Klasse](use-querybyattribute-class.md)  
  
 [Verwenden der QueryExpression-Klasse](use-queryexpression-class.md)  
  
 [Verwenden der ColumnSet-Klasse](use-the-columnset-class.md)  
  
 [Verwenden der ConditionExpression-Klasse](use-conditionexpression-class.md)  
  
 [Verwenden der FilterExpression-Klasse](use-filterexpression-class.md)  
  
 [Verwenden einer linken äußeren Verknüpfung in QueryExpression für Abfragen nach Datensätzen, die „nicht in“ sind.](use-left-outer-join-queryexpression-query-records-not-in.md)  
  
 [Testen für einen Null-Wert](/dynamics365/customer-engagement/developer/test-null-value)  
  
 [Auslagern von umfangreichen Ergebnissätzen mit Abfrageausdruck und FetchXML](page-large-result-sets-with-queryexpression.md)  
  
 [Beispiel: Abrufen bei 1:n-Beziehung](/dynamics365/customer-engagement/developer/org-service/sample-retrieve-with-one-to-many-relationship)  
  
 [Beispiel: Abrufen von Vielfachen mit der Abfrage nach dem Attribut](/org-service/samples/retrieve-multiple-querybyattribute-class.md)  
  
 [Beispiel: Abrufen von Vielfachen mit Abfrageausdruck](/org-service/samples/retrieve-multiple-queryexpression-class.md)  
  
 [Beispiel: Verwenden von QueryExpression mit einem Auslagerungscookie](/dynamics365/customer-engagement/developer/org-service/sample-use-queryexpression-with-a-paging-cookie)  
  
## <a name="reference"></a>Referenz  
 <xref:Microsoft.Xrm.Sdk.Query.QueryBase>  
  
 <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>  
  
 <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute>  
  
 <xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*>  
  
 <xref:Microsoft.Xrm.Sdk.Query.ColumnSet>  
  
 <xref:Microsoft.Xrm.Sdk.Query.ConditionExpression>  
  
 <xref:Microsoft.Xrm.Sdk.Query.FilterExpression>  
  
 <xref:Microsoft.Xrm.Sdk.Query.PagingInfo.PagingCookie>  
  
### <a name="see-also"></a>Siehe auch  
 [Beispiel: Konvertieren von Abfragen zwischen Fetch und QueryExpression](/dynamics365/customer-engagement/developer/org-service/sample-convert-queries-fetch-queryexpression)
