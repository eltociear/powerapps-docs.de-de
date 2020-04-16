---
title: Erstellen von Abfragen mit QueryExpression (Common Data Service) | Microsoft Docs
description: Lesen Sie, wie Sie die QueryExpression-Klasse zum programmgesteuerten Erstellen einer Abfrage, die Datenfilter und Suchbedingungen, die den Umfang einer Datenbanksuche definieren, enthält, verwenden können.
ms.custom: ''
ms.date: 06/25/2019
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 107432081e08a662621521244f2dc5613824a28f
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156106"
---
# <a name="build-queries-with-queryexpression"></a>Erstellen von Abfragen mit QueryExpression

In Common Data Service können Sie die Klasse <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> zum programmgesteuerten Erstellen einer Abfrage verwenden, die Datenfilter und Suchbedingungen enthält, die den Umfang einer Datenbanksuche definieren. Ein Abfrageausdruck wird für Einzelobjektsuchen verwendet. Beispielsweise können Sie eine Suche erstellen, um alle Firmen zurückzugeben, die bestimmten Suchkriterien entsprechen. Die Klasse <xref:Microsoft.Xrm.Sdk.Query.QueryBase> ist die Basisklasse für Abfrageausdrücke. Es gibt drei abgeleitete Klassen: <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>, <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute> und <xref:Microsoft.Xrm.Sdk.Query.FetchExpression>. Die Klasse `QueryExpression` unterstützt komplexe Abfragen. Die Klasse `QueryByAttribute` ist eine einfache Möglichkeit, um nach Entitäten zu suchen, bei denen Attribute mit angegebenen Werten übereinstimmen. 

> [!NOTE]
> Die dritte abgeleitete Klasse, `FetchExpression`, wird mit FetchXML verwendet, die proprietäre Common Data Service-Abfragesprache kann verwendet werden, um einige Abfragen auszuführen, indem XML-basierte Abfragen verwendet werden. Weitere Informationen finden Sie unter [Verwendung von FetchXML, um eine Abfrage zu erstellen](../use-fetchxml-construct-query.md).
  
Abfrageausdrücke werden in Methoden verwendet, die mehr als einen Datensatz abfragen, z.B. die <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*> Methode, in Nachrichten, die eine Operation mit einer durch einen Abfrageausdruck spezifizierten Ergebnismenge durchführen, z.B. <xref:Microsoft.Crm.Sdk.Messages.BulkDeleteRequest> und wenn die ID für einen bestimmten Datensatz nicht bekannt ist.  

> [!WARNING]
>  Rufen Sie nicht alle Attribute in einer Abfrage ab, da dadurch die Leistung beeinträchtigt wird. Das trifft insbesondere zu, wenn die Abfrage als Parameter in einer Updateanforderung verwendet wird. Wenn in einem Update alle Attribute enthalten sind, werden dadurch alle Feldwerte festgelegt, selbst wenn sie unverändert sind, und häufig werden kaskadierende Updates zu untergeordneten Datensätzen ausgelöst.

Um eine Abfrage zur Wiederverwendung zu speichern, können Sie sie mithilfe von <xref:Microsoft.Crm.Sdk.Messages.QueryExpressionToFetchXmlRequest> in FetchXML konvertieren und sie als gespeicherte Abfrage speichern. Weitere Informationen: [Gespeicherte Abfragen](../saved-queries.md) 
 
## <a name="alternatives-to-queryexpression"></a>Alternativen für QueryExpression

Es gibt zwei weitere Möglichkeiten, Abfragen zu erstellen, um Datensätze aus Common Data Service abzurufen. 

- FetchXML, die herstellereigene Common Data Service-Abfragesprache, kann verwendet werden, um einige Abfragen auszuführen, indem XML-basierte Abfragen verwendet werden. Weitere Informationen finden Sie unter [Verwendung von FetchXML, um eine Abfrage zu erstellen](../use-fetchxml-construct-query.md). 
- .NET Language-Integrated Query (LINQ). Weitere Informationen: [Erstellen von Abfragen mit LINQ (.NET Language-Integrated Query)](build-queries-with-linq-net-language-integrated-query.md).  

<!-- This doesn't belong here. It should be in model driven app configuration -->
## <a name="configuration-for-quick-find"></a>Konfiguration für die Schnellsuche

In modellgesteuerten Apps gibt es eine Schnellsuchfunktion. Wenn ein Benutzer bei der Schnellsuche Suchkriterien angibt, die nicht selektiv genug sind, wird dies vom System erkannt und die Suche wird beendet. Dies unterstützt eine schnellere Form der Schnellsuche und kann einen großen Leistungsunterschied ausmachen. Diese wird vom Attribut der [QuickFindRecordLimitEnabled-Organisationsentität](/powerapps/developer/common-data-service/reference/entities/organization#BKMK_QuickFindRecordLimitEnabled) gesteuert. Wenn dieser `Boolean`-Attributwert `true` ist, wird Abfragen für die Schnellsuche ein Limit auferlegt.

## <a name="in-this-section"></a>In diesem Abschnitt

[Verwenden der QueryByAttribute-Klasse](use-querybyattribute-class.md)<br />
[Verwenden der QueryExpression-Klasse](use-queryexpression-class.md)<br />
[Verwenden der ColumnSet-Klasse](use-the-columnset-class.md)<br />
[Verwenden der ConditionExpression-Klasse](use-conditionexpression-class.md)<br />
[Verwenden der FilterExpression-Klasse](use-filterexpression-class.md)<br />
[Verwenden einer linken äußeren Verknüpfung in QueryExpression für Abfragen nach Datensätzen, die „nicht in“ sind.](use-left-outer-join-queryexpression-query-records-not-in.md)<br />
[Testen für einen Null-Wert](/dynamics365/customer-engagement/developer/test-null-value)<br />
[Auslagern von umfangreichen Ergebnissätzen mit Abfrageausdruck und FetchXML](page-large-result-sets-with-queryexpression.md)<br />
[Beispiel: Abrufen bei 1:n-Beziehung](/dynamics365/customer-engagement/developer/org-service/sample-retrieve-with-one-to-many-relationship)<br />
[Beispiel: Abrufen von Vielfachen mit der Abfrage nach dem Attribut](/org-service/samples/retrieve-multiple-querybyattribute-class.md)<br />
[Beispiel: Abrufen von Vielfachen mit Abfrageausdruck](/org-service/samples/retrieve-multiple-queryexpression-class.md)<br />
[Beispiel: Verwenden von QueryExpression mit einem Auslagerungscookie](/dynamics365/customer-engagement/developer/org-service/sample-use-queryexpression-with-a-paging-cookie)  
  
## <a name="reference"></a>Referenz

<xref:Microsoft.Xrm.Sdk.Query.QueryBase><br />
<xref:Microsoft.Xrm.Sdk.Query.QueryExpression><br />
<xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute><br />
<xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*><br />
<xref:Microsoft.Xrm.Sdk.Query.ColumnSet><br />
<xref:Microsoft.Xrm.Sdk.Query.ConditionExpression><br />
<xref:Microsoft.Xrm.Sdk.Query.FilterExpression><br />
<xref:Microsoft.Xrm.Sdk.Query.PagingInfo.PagingCookie><br />
  
### <a name="see-also"></a>Siehe auch

[Beispiel: Konvertieren von Abfragen zwischen Fetch und QueryExpression](/dynamics365/customer-engagement/developer/org-service/sample-convert-queries-fetch-queryexpression)
