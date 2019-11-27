---
title: Verwenden der ColumnSet-Klasse (Common Data Service) | Microsoft-Dokumentation
description: <Description>
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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
ms.openlocfilehash: 0fe094ecd43483d0fb6d91d5dcabd15b87472ee7
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748681"
---
# <a name="use-the-columnset-class"></a>Verwenden der ColumnSet-Klasse

In Common Data Service können Sie die <xref:Microsoft.Xrm.Sdk.Query.ColumnSet>-Klasse verwenden, um anzugeben, welche Attribute von einer Abfrage zurückgegeben werden sollen, die mithilfe der Klassen <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> und <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute> definiert wurde. Es ist ferner ein Parameter für die <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Retrieve*> -Methode und wird als Eigenschaft in einer Reihe von Nachrichtenanforderungsklassen verwendet, welche Daten in eine <xref:Microsoft.Xrm.Sdk.EntityCollection> zurückgeben.

> [!NOTE]
> Die <xref:Microsoft.Xrm.Sdk.Query.ColumnSet>-Klasse hat eine <xref:Microsoft.Xrm.Sdk.Query.ColumnSet.AllColumns>-Eigenschaft, die angibt, dass alle Spalten der Entität zurückgegeben werden sollen. Als bewährte Methode für Leistung, sollten Sie dies nicht für den Produktionscode verwenden. Weitere Informationen: [Rufen Sie nicht alle Spalten einer Entität zur Abfrage von APIs ab](/dynamics365/customer-engagement/guidance/data/retrieve-specific-columns-entity-via-query-apis)

Das folgende Codebeispiel zeigt, wie die `ColumnSet`-Klasse verwendet wird, um anzugeben, welche Attribute aus einem Abfrageausdruck zurückgegeben werden.  
  
```csharp  
QueryExpression contactquery = new QueryExpression   
{  
   EntityName="contact",  
   ColumnSet = new ColumnSet("firstname", "lastname", "contactid")   
};  
```  
  
### <a name="see-also"></a>Siehe auch  

[Verwenden der QueryExpression-Klasse](use-queryexpression-class.md)<br />
[Erstellen von Abfragen mit QueryExpression](build-queries-with-queryexpression.md)<br />
[Verwenden der ConditionExpression-Klasse](use-conditionexpression-class.md)<br /> 
<xref:Microsoft.Xrm.Sdk.Query.QueryExpression> Klasse <br />
<xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute> Klasse <br />