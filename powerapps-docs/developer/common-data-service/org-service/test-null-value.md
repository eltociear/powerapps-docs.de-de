---
title: Test auf einen Nullwert (Common Data Service) | Microsoft Docs
description: Das folgende Beispiel zeigt den Test auf einen Nullwert mit den FilterExpression- und QueryByAttribute-Klassen.
ms.custom: ''
ms.date: 05/03/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 38a9109faf5d8ae45aa2a0bdecfb0d25037742dd
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748692"
---
# <a name="test-for-a-null-value"></a>Test auf einen Nullwert

Die folgenden Codebeispiel zeigt den Test auf einen Nullwert mit den Klassen <xref:Microsoft.Xrm.Sdk.Query.FilterExpression> und <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute>.  
  
## <a name="example"></a>Beispiel  
 Verwenden Sie diesen Code für den Gleichheitstest mit der Klasse <xref:Microsoft.Xrm.Sdk.Query.FilterExpression>.  
  
```csharp  
FilterExpression null_filter = new FilterExpression(LogicalOperator.And);   
null_filter.FilterOperator = LogicalOperator.And;   
null_filter.AddCondition("leadid", ConditionOperator.Null);  
  
```  
  
## <a name="example"></a>Beispiel  
 Verwenden Sie diesen Code für den Ungleichheitstest mit der Klasse <xref:Microsoft.Xrm.Sdk.Query.FilterExpression>.  
  
```csharp  
  
FilterExpression filter = new FilterExpression(LogicalOperator.And);   
filter.FilterOperator = LogicalOperator.And;   
filter.AddCondition("leadid", ConditionOperator.NotNull);  
```  
  
## <a name="example"></a>Beispiel  
 Verwenden Sie diesen Code für den Gleichheitstest mit der Klasse <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute>.  
  
```csharp  
  
QueryByAttribute qba = new QueryByAttribute("account");   
qba.ColumnSet = new ColumnSet("name","address1_stateorprovince");   
qba.AddAttributeValue("donotfax", null);  
```  
  
### <a name="see-also"></a>Siehe auch  
 [Erstellen von Abfragen mit QueryExpression](build-queries-with-queryexpression.md)   
 [Auslagern von umfangreichen Ergebnissätzen mit FetchXML](page-large-result-sets-with-fetchxml.md)
