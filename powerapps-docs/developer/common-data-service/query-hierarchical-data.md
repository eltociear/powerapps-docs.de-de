---
title: Abfragen von hierarchischen Daten (Common Data Service) | Microsoft-Dokumentation
description: Lesen Sie, wie Sie die neuen Abfragebedingungsoperatoren nutzen, um Entitäten mit expliziten hierarchischen Beziehungen abzufragen.
ms.custom: ''
ms.date: 10/31/2018
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
ms.openlocfilehash: 61bcf12b58c3ce4438281adda0809dcda92c7cfa
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155358"
---
# <a name="query-hierarchical-data"></a>Abfragen von hierarchischen Daten

Sie können spezifische selbstreferenzielle Eins-zu-Viele-Entitätsbeziehungen als hierarchisch definieren. Sie können Abfragen schreiben, die verknüpfte in diesen Hierarchien zurückgeben.  
  
Sie können neue Abfragebedingungsoperatoren nutzen, um Entitäten mit expliziten hierarchischen Beziehungen abzufragen. Diese Operatoren gelten nur für die Entitätsbeziehungen, die speziell als hierarchische Beziehungen definiert sind. Sie können neue Bedingungsoperatoren verwenden, um diese hierarchischen Daten zu verwenden, wenn Sie mit <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> oder <xref:Microsoft.Xrm.Sdk.Query.FetchExpression> abfragen.  
  
<a name="BKMK_ConditionOperators"></a>   
## <a name="condition-operators-for-hierarchical-data"></a>Bedingungsoperatoren für hierarchische Daten  
 Verwenden Sie die folgenden Poeratoren, um Bedingungen festzulegen, wenn Sie hierarchische Daten abfragen.  
  
|FetchXML|ConditionOperator|Beschreibung|  
|--------------|-----------------------|-----------------|  
|`above`|`Above`|Gibt alle Datensätze in der Vorfahrenlinie des referenzierten hierarchischen Datensatzes zurück.|  
|`eq-or-above`|`AboveOrEqual`|Gibt den referenzierten Datensatz und alle Datensätze über diesem in der Hierarchie zurück.|  
|`under`|`Under`|Gibt alle untergeordneten Datensätze in dem referenzierten Datensatz in der Hierarchie zurück.|  
|`eq-or-under`|`UnderOrEqual`|Gibt den referenzierten Datensatz und allle untergeordneten Datensätze in in der Hierarchie zurück.|  
|`not-under`|`NotUnder`|Gibt alle untergeordneten Datensätze nicht unter dem referenzierten Datensatz in der Hierarchie zurück.|  
|`eq-owneduseroruserhierarchy`|`OwnedByMeOrMyReports`|Wenn hierarchische Sicherheitsmodelle verwendet werden, ist dies dem aktuellen Benutzer oder desse°n Berichterstellungshierarchie gleich|  
|`eq-useroruserhierarchyandteams`|`OwnedByMeOrMyReportsAndTeams`|Wenn hierarchische Sicherheitsmodelle verwendet werden, ist dies dem aktuellen Benutzer und seinen Teams oder seiner Berichterstellungshierarchie und deren Teams gleich|  
  
### <a name="recursion-limits-when-querying-hierarchical-data"></a>Rekursion begrenzt, wann hierarchisch Daten abgefragt werden  
 Da das Abfragen von Daten ressourcenintensiv sein kann, gibt es ein Standardlimit von 100 rekursionenszulässigen Bedingungen für hierarchische Abfragen mithilfe von `Above`, `AboveOrEqual`, `Under`, `UnderOrEqual` und `NotUnder`-Bedingungsoperatoren.  
  
 `OwnedByMeOrMyReports` und `OwnedByMeOrMyReportsAndTeams` sind hierarchische Sicherheitszustandsoperatoren, die von der **Hierarchytiefe**-Einstellung anhängen, die in **Einstellungen** > **Sicherheit** > **Hierarchiesicherheit** abhängen. Der Wert dieser Einstellung ist im `Organization.MaxDepthForHierarchicalSecurityModel`-Attribut gespeichert.  
  
<a name="BKMK_ChildCountAggregate"></a>   
## <a name="retrieve-the-number-of-hierarchically-related-child-records"></a>Rufen Sie die Anzahl von hierarchisch verknüpften untergeordneten Datensätzen ab  
 Verwenden Sie das `rowaggregate`-Attribut in einer FetchXML-basierten Abfrage, um die Anzahl von hierarchisch verknüpften untergeordneten Datensätzen abzurufen. Wenn der Wert auf `CountChildren` festgelegt ist, wird ein Wert ist, der die Gesamtanzahl von untergeordneten Datensätzen für den Datensatz enthält, in die Datei <xref:Microsoft.Xrm.Sdk.EntityCollection> eingeschlossen. Zum Beispiel schließt die folgende Abfrage einen der `AccountChildren`-Gesamtwert ein, der die Anzahl von untergeordneten Firmendatensätzen in der hierarchischen Beziehung darstellt, in der der Parameter `{0}` den `AccountId` des übergeordneten Datensatzes darstellt.  
  
```xml  
<fetch distinct='false' no-lock='false' mapping='logical'>  
  <entity name='account'>  
    <attribute name='name' />  
    <attribute name='accountid' />  
    <attribute name='accountid' rowaggregate='CountChildren' alias='AccountChildren'/>  
    <filter type='and'>  
      <condition attribute='accountid' operator='under' value='{0}' />  
    </filter>  
  </entity>  
</fetch>  
  
```  
  
> [!NOTE]
>  Der zurückgegebene Gesamtwert enthält alle untergeordneten Datensätze, einschließlich solcher, für die der Benutzer möglicherweise keinen Lesezugriff hat.  
  
 
