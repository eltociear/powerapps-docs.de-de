---
title: Datenabfrage mit Web-API (Common Data Service for Apps) | Microsoft Docs
description: 'Informieren Sie sich über die verschiedenen Methoden zum Abfragen mit der Common Data Service für Apps-Daten mit dem Common Data Servce for Apps-Web-API und verschiedenen Systemabfrageoptionen, die in diesen Abfragen angewandt werden können.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: fc3ade34-9c4e-4c33-88a4-aa3842c5eee1
caps.latest.revision: 78
author: brandonsimons
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="query-data-using-the-web-api"></a>Datenabfrage mit Web-API

Wenn Sie Daten für einen Entitätssatz abrufen möchten, verwenden Sie eine `GET`-Anforderung. Wenn Sie Daten abrufen, können Sie Abfrageoptionen anwenden, um Kriterien für die gewünschten Daten und für die Entitätseigenschaften, die zurückgegeben werden sollen, festzulegen.  
    
<a name="bkmk_basicQuery"></a>
 
## <a name="basic-query-example"></a>Grundlegendes Abfragebeispiel

Dieses Beispiel fragt den Firmen-Entitätssatz ab und verwendet die `$select` und `$top`-Systemabfrageoptionen, um die Name-Eigenschaft für ersten drei Firmen zurückzugeben:  
  
 **Anforderung**

```http 
GET [Organization URI]/api/data/v9.0/accounts?$select=name&$top=3 HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
  
```  
  
**Antwort**

```http 
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
  
{  
"@odata.context": "[Organization URI]/api/data/v9.0/$metadata#accounts(name)",  
"value": [  
{  
"@odata.etag": "W/\"501097\"",  
"name": "Fourth Coffee (sample)",  
"accountid": "89390c24-9c72-e511-80d4-00155d2a68d1"  
},  
{  
"@odata.etag": "W/\"501098\"",  
"name": "Litware, Inc. (sample)",  
"accountid": "8b390c24-9c72-e511-80d4-00155d2a68d1"  
},  
{  
"@odata.etag": "W/\"501099\"",  
"name": "Adventure Works (sample)",  
"accountid": "8d390c24-9c72-e511-80d4-00155d2a68d1"  
}  
]  
}  
```  
  
<a name="bkmk_limits"></a>

## <a name="limits-on-number-of-entities-returned"></a>Beschränkungen der Zahl der zurückgegebenen Entitäten

Sofern Sie keine kleinere Seitengröße angeben, wird ein Maximum von 5000 Entitäten pro Anforderung zurückgegeben. Falls mehrere Entitäten vorhanden sind, die mit den Abfragenfilterkriterien übereinstimmen, wird eine `@odata.nextLink`-Eigenschaft mit den Ergebnissen zurückgegeben. Verwenden Sie den Wert der `@odata.nextLink`-Eigenschaft mit einer neuen `GET`-Anforderung, um die nächste Datenseite zurückzugeben.  
  
> [!NOTE]
>  Abfragen für Modellentitäten werden nicht begrenzt oder in einer Seite ausgegeben. Mehr Informationen: [Metadatenabfrage mit Web-API](query-metadata-web-api.md).  
  
<a name="bkmk_specifyNumber"></a>

## <a name="specify-the-number-of-entities-to-return-in-a-page"></a>Geben Sie die Anzahl der in einer Seite zurückzugebenden Entitäten an

Verwenden Sie den `odata.maxpagesize`-Einstellungswert, um die Anzahl der Entitäten, die in der Antwort zurückgegeben werden, anzufordern.  
  
> [!NOTE]
>  Sie können keinen `odata.maxpagesize`-Einstellungswert verwenden, der größer als 5000 ist.  
  
 Das folgende Bespiel fragt den Firmen-Entitätssatz ab und gibt die `name`-Eigenschaft für die ersten drei Firmen zurück.  
  
 **Anforderung**

```http 
GET [Organization URI]/api/data/v9.0/accounts?$select=name HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Prefer: odata.maxpagesize=3  
```  
  
 **Antwort**  

```http 
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Content-Length: 402  
Preference-Applied: odata.maxpagesize=3  
  
{  
"@odata.context": "[Organization URI]/api/data/v9.0/$metadata#accounts(name)",  
"value": [  
{  
"@odata.etag": "W/\"437194\"",  
"name": "Fourth Coffee (sample)",  
"accountid": "7d51925c-cde2-e411-80db-00155d2a68cb"  
},  
{  
"@odata.etag": "W/\"437195\"",  
"name": "Litware, Inc. (sample)",  
"accountid": "7f51925c-cde2-e411-80db-00155d2a68cb"  
},  
{  
"@odata.etag": "W/\"468026\"",  
"name": "Adventure Works (sample)",  
"accountid": "8151925c-cde2-e411-80db-00155d2a68cb"  
}  
],  
"@odata.nextLink": "[Organization URI]/api/data/v9.0/accounts?$select=name&$skiptoken=%3Ccookie%20pagenumber=%222%22%20pagingcookie=%22%253ccookie%2520page%253d%25221%2522%253e%253caccountid%2520last%253d%2522%257b8151925C-CDE2-E411-80DB-00155D2A68CB%257d%2522%2520first%253d%2522%257b7D51925C-CDE2-E411-80DB-00155D2A68CB%257d%2522%2520%252f%253e%253c%252fcookie%253e%22%20/%3E"  
}  
```  
  
Verwenden Sie den Wert der `@odata.nextLink`-Eigenschaft, um die nächste Datensatzgruppe anzufordern. Sie sollten keine zusätzlichen Systemabfrageoptionen für den Wert ändern oder anfügen. Für jede nachfolgende Anforderung weiterer Seiten sollten Sie denselben odata.maxpagesize-Einstellungswert verwenden, der sich in der ursprünglichen Anforderung verwendet wurde. Zwischenspeichern Sie auch die zurückgegebenen Ergebnisse oder den Wert der `@odata.nextLink`-Eigenschaft, sodass Sie zu zuvor abgerufenen Seiten zurückkehren können.  
  
> [!NOTE]
>  Der Wert der `@odata.nextLink`-Eigenschaft ist URI-codiert. Falls Sie den Wert vor dem Senden URI-codieren, verursachen die XML-Cookieinformationen in der URI einen Fehler.  
  
<a name="bkmk_applyqueryOptions"></a>

## <a name="apply-system-query-options"></a>Verwenden von Systemabfrageoptionen

Jede der Systemabfrageoptionen, die Sie zur URI für den Entitätssatz anfügen, wird mithilfe der Syntax für Abfragezeichenfolgen hinzugefügt. Die erste wird nach [?] angefügt und die nachfolgenden Abfrageoptionen werden mithilfe von [&] getrennt. Alle Abfrageoptionen unterscheiden zwischen Groß-/Kleinschreibung, wie im folgenden Beispiel angezeigt.  
  
```http 
GET [Organization URI]/api/data/v9.0/accounts?$select=name,revenue&$top=3&$filter=revenue gt 100000  
```  
  
<a name="bkmk_requestProperties"></a>
 
## <a name="request-specific-properties"></a>Anforderungsspezifische Eigenschaften

Verwenden Sie die `$select`-Systemabfrageoption, um die zurückgegebenen Eigenschaften zu begrenzen, wie im folgenden Beispiel angezeigt.  
  
```http 
GET [Organization URI]/api/data/v9.0/accounts?$select=name,revenue  
```  
  
> [!IMPORTANT]
>  Dies ist eine bewährte Methode für die Leistung. Wenn Eigenschaften nicht mithilfe von `$select`angegeben wurden, werden alle Eigenschaften zurückgegeben.  
  
Wenn Sie bestimmte Eigenschaftstypen anfordern, können Sie erwarten, dass zusätzliche Schreibschutzeigenschaften automatisch zurückgegeben werden.  
  
Wenn Sie einen Geldwert anfordern, wird die `_transactioncurrencyid_value`-Sucheigenschaft zurückgegeben. Diese Eigenschaft enthält nur den GUID-Wert der Transaktionswährung, daher könnten Sie diesen Wert verwenden, um Informationen über die Währung mithilfe von <xref href="Microsoft.Dynamics.CRM.transactioncurrency?text=transactioncurrency EntityType" /> abzurufen. Alternativ können Sie durch das Anfordern von Anmerkungen zusätzliche Daten in derselben Anforerung abrufen. Weitere Informationen:[Abrufen von Daten zu Sucheigenschaften](#bkmk_lookupProperty)  
  
Wenn Sie eine Eigenschaft anfordern, die Teil eines zusammengesetzten Attributs für eine Adresse ist, erhalten Sie auch die zusammengesetzte Eigenschaft. Wenn beispielsweise Ihre Abfrage die `address1_line1`-Eigenschaft für einen Kontakt anfordert, wird die `address1_composite`-Eigenschaft ebenfalls zurückgegeben. 
  
<a name="bkmk_filter"></a>
 
## <a name="filter-results"></a>Ergebnisse filtern

Verwenden Sie die `$filter`-Systemabfrageoption, um Kriterien für Entitäten festzulegen, die zurückgegeben werden sollen.  
  
<a name="bkmk_buildInFilterOperators"></a>

### <a name="standard-filter-operators"></a>Standardfilteroperatoren

Die Web-API unterstützt die OData-Standardfilteroperatoren, die in der folgenden Tabelle aufgelistet werden.  
  
|Operator|Beschreibung|Beispiel|  
|--------------|-----------------|-------------|  
|**Vergleichsoperatoren**|||  
|`eq`|Gleich|`$filter=revenue eq 100000`|  
|`ne`|Ungleich|`$filter=revenue ne 100000`|  
|`gt`|Größer als|`$filter=revenue gt 100000`|  
|`ge`|Größer als oder gleich|`$filter=revenue ge 100000`|  
|`lt`|Kleiner als|`$filter=revenue lt 100000`|  
|`le`|Kleiner oder gleich|`$filter=revenue le 100000`|  
|**Logische Operatoren**|||  
|`and`|Logisch und|`$filter=revenue lt 100000 and revenue gt 2000`|  
|`or`|Logisch oder|`$filter=contains(name,'(sample)') or contains(name,'test')`|  
|`not`|Logische Negation|`$filter=not contains(name,'sample')`|  
|**Gruppieren von Operatoren**|||  
|`( )`|Rangfolgengruppierung|`(contains(name,'sample') or contains(name,'test')) and revenue gt 5000`|  
  
> [!NOTE]
>  Dies ist eine Teilmenge von [11.2.5.1.1 Integrierte Filtervorgänge](http://docs.oasis-open.org/odata/odata/v4.0/errata02/os/complete/part1-protocol/odata-v4.0-errata02-os-part1-protocol-complete.html). Arithmetische Operatoren und der Vergleich hat Operator werden von der Web-API nicht unterstützt.  
  
<a name="bkmk_buildInQueryFunctions"></a>

### <a name="standard-query-functions"></a>Standardabfragenfunktionen

Die Web-Api unterstützt diese standardmäßigen OData-Zeichenfolgenabfragefunktionen.  
  
|Funktion|Beispiel|  
|--------------|-------------|  
|`contains`|`$filter=contains(name,'(sample)')`|  
|`endswith`|`$filter=endswith(name,'Inc.')`|  
|`startswith`|`$filter=startswith(name,'a')`|  
  
> [!NOTE]
>  Dies ist eine Teilmenge von [11.2.5.1.2 Integrierte Abfragefunktionen](http://docs.oasis-open.org/odata/odata/v4.0/errata02/os/complete/part1-protocol/odata-v4.0-errata02-os-part1-protocol-complete.html). `Date`, `Math`, `Type`, `Geo` und andere String-Funktionen werden nicht in der Web-API unterstützt.  
  
### <a name="common-data-service-for-apps-web-api-query-functions"></a>Common Data Service for Apps-Web-API-Abfragefunktionen
 
Common Data Service for Apps enthält einige spezielle Funktionen, die Parameter akzeptieren, Boolesche Werte zurückgeben und als Filterkriterium in einer Abfrage verwendet werden können. Eine Liste dieser Funktionen finden Sie unter <xref:Microsoft.Dynamics.CRM.QueryFunctionIndex>. Im Folgenden finden Sie ein Beispiel für die Suche von <xref href="Microsoft.Dynamics.CRM.Between?text=Between Function" /> nach Firmen mit einer Mitarbeiterzahl zwischen 5 und 2000.  
  
```http 
GET [Organization URI]/api/data/v9.0/accounts?$select=name,numberofemployees&$filter=Microsoft.Dynamics.CRM.Between(PropertyName='numberofemployees',PropertyValues=["5","2000"])  
```  
  
Weitere Informationen: [Verfassen einer Abfrage mit Funktionen](use-web-api-functions.md#bkmk_composeQueryWithFunctions).  
  
<a name="bkmk_order"></a>
 
## <a name="order-results"></a>Reihenfolge von Ergebnissen

Geben Sie die Reihenfolge an, in der Elemente unter Verwendung Systemabfrageoption `$orderby` zurückgegeben werden. Verwenden Sie das `asc`- oder `desc`-Suffix, um eine jeweils aufsteigende oder absteigende Reihenfolge anzugeben. Die Standardeinstellung ist aufsteigend, wenn das Suffix nicht angewendet wird. Das folgende Beispiel zeigt das Abrufen der Namens- und Umsatzeigenschaften von Firmen, sortiert nach aufsteigendem Umsatz und absteigendem Namen.  
  
```http 
GET [Organization URI]/api/data/v9.0/accounts?$select=name,revenue,&$orderby=revenue asc,name desc&$filter=revenue ne null  
```  
  
<a name="bkmk_useParameterAliases"></a>

## <a name="use-parameter-aliases-with-system-query-options"></a>Verwendung von Parameteraliasen mit Systemabfrageoptionen

Sie können Parameteraliase für `$filter`- und `$orderby`-Systemabfrageoptionen verwenden. Parameteraliase erlauben die mehrmalige Verwendung des gleichen Werts in einer Anforderung. Wenn dem Alias kein Wert zugeordnet wurde, wird angenommen, dass er NULL ist.  
  
Ohne Parameteraliasse:

```http  
GET [Organization URI]/api/data/v9.0/accounts?$select=name,revenue,&$orderby=revenue asc,name desc&$filter=revenue ne null  
```  
  
 Mit Parameteraliassen:

```http  
GET [Organization URI]/api/data/v9.0/accounts?$select=name,revenue,&$orderby=@p1 asc,@p2 desc&$filter=@p1 ne @p3&@p1=revenue&@p2=name  
```  
  
Sie können auch Parameteraliase verwenden, wenn Sie Funktionen verwenden. Weitere Informationen: [Verwenden von Web-API-Funktionen](use-web-api-functions.md)  
  
<a name="bkmk_limitResults"></a>
 
## <a name="limit-results"></a>Ergebnisse eingrenzen

Sie können die Anzahl der zurückgegebenen Ergebnisse einschränken, indem Sie die Systemabfrageoption `$top`, verwenden. Im folgenden Beispiel werden nur die ersten drei Firmenentitäten zurückgegeben.  
  
```http 
GET [Organization URI]/api/data/v9.0/accounts?$select=name,revenue&$top=3  
```  
  
> [!NOTE]
>  Durch Einschränken der Ergebnisse mit `$top` wird die Anwendung der `odata.maxpagesize`-Einstellung verhindert. Sie können die `odata.maxpagesize`-Einstellung oder `$top` verwenden, aber nicht beide gleichzeitig. Weitere Informationen zu `odata.maxpagesize` finden Sie unter [Geben Sie die Anzahl der getätigten Entitäten an, die in eine Seite zurückgegeben werden](query-data-web-api.md#bkmk_specifyNumber).  
>   
>  Sie sollten außerdem nicht `$top` mit `$count` verwenden.  
  
<a name="bkmk_retrieveCount"></a>
 
## <a name="retrieve-a-count-of-entities"></a>Abrufen einer Anzahl von Entitäten

Verwenden Sie die Systemabfrageoption `$count` mit dem Wert `true`, um eine Anzahl von Entitäten einzuschließen, die die Filterkriterien bis 5000 entsprechen.  
  
> [!NOTE]
>  Der Zählwert steht nicht für die Gesamtanzahl von Entitäten im System. Er ist durch die maximale Anzahl von Entitäten begrenzt, die zurückgegeben werden können. Weitere Informationen: [Beschränkungen der Zahl der zurückgegebenen Entitäten](#bkmk_limits)  
  
Die `@odata.count`-Antworteigenschaft enthält die Anzahl der Entitäten, die den Filterkriterien entsprechen, ungeachtet einer `odata.maxpagesize`-Einstellungsbeschränkung.  
  
> [!NOTE]
>  Sie sollten nicht `$top` mit `$count` verwenden.  
  
Das folgende Beispiel zeigt, dass zehn Firmen vorhanden sind, die den Kriterien übereinstimmen, wo der Name „Beispiel” enthält, aber nur die ersten drei Firmen zurückgegeben werden.  
  
 **Anforderung**

```http 
GET [Organization URI]/api/data/v9.0/accounts?$select=name&$filter=contains(name,'sample')&$count=true HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Prefer: odata.maxpagesize=3  
```  
  
 **Antwort** 
 
```http 
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.maxpagesize=3  
  
{  
"@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts(name)",  
"@odata.count":10,  
"value":[  
{  
"@odata.etag":"W/\"502482\"","name":"Fourth Coffee (sample)","accountid":"655eaf89-f083-e511-80d3-00155d2a68d3"  
},{  
"@odata.etag":"W/\"502483\"","name":"Litware, Inc. (sample)","accountid":"675eaf89-f083-e511-80d3-00155d2a68d3"  
},{  
"@odata.etag":"W/\"502484\"","name":"Adventure Works (sample)","accountid":"695eaf89-f083-e511-80d3-00155d2a68d3"  
}  
],"@odata.nextLink":"[Organization URI]/api/data/v9.0/accounts?$select=name&$filter=contains(name,'sample')&$skiptoken=%3Ccookie%20pagenumber=%222%22%20pagingcookie=%22%253ccookie%2520page%253d%25221%2522%253e%253caccountid%2520last%253d%2522%257b695EAF89-F083-E511-80D3-00155D2A68D3%257d%2522%2520first%253d%2522%257b655EAF89-F083-E511-80D3-00155D2A68D3%257d%2522%2520%252f%253e%253c%252fcookie%253e%22%20istracking=%22False%22%20/%3E"  
}  
  
```  
  
 Wenn Sie keine Daten bis auf die Anzahl zurückgeben möchten, können Sie `$count` auf eine beliebige Sammlung anwenden, um nur den Wert abzurufen.  
  
 **Anforderung**  

```http 
GET [Organization URI]/api/data/v9.0/accounts/$count HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```  
  
 **Antwort**  
```http 
HTTP/1.1 200 OK  
Content-Type: text/plain  
OData-Version: 4.0  
  
10  
```  
  
<a name="bkmk_includeFormattedValues"></a>

## <a name="include-formatted-values"></a>Formatierte Werte einschließen

Wenn Sie mit den Ergebnissen formatierte Werte für Eigenschaften abrufen möchten, verwenden Sie die Einstellung `odata.include-annotations` mit dem Wert `OData.Community.Display.V1.FormattedValue`. Die Antwort schließt diese Werte mit Eigenschaften ein, die mit der nächsten Namenskonvention übereinstimmen:  
  
```  
<propertyname>@OData.Community.Display.V1.FormattedValue  
```  
 Das folgende Bespiel fragt den Firmenentitätssatz ab und gibt den ersten Datensatz zurück, einschließlich Eigenschaften, die formatierte Werte unterstützen.  
  
 **Anforderung**

```http 
GET [Organization URI]/api/data/v9.0/accounts?$select=name,donotpostalmail,accountratingcode,numberofemployees,revenue&$top=1 HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Prefer: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
```  
  
 **Antwort**  
```http 
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
  
{  
"@odata.context": "[Organization URI]/api/data/v9.0/$metadata#accounts(name,donotpostalmail,accountratingcode,numberofemployees,revenue)",  
"value": [  
{  
"@odata.etag": "W/"502170"",  
"name": "Fourth Coffee (sample)",  
"donotpostalmail@OData.Community.Display.V1.FormattedValue": "Allow",  
"donotpostalmail": false,  
"accountratingcode@OData.Community.Display.V1.FormattedValue": "Default Value",  
"accountratingcode": 1,  
"numberofemployees@OData.Community.Display.V1.FormattedValue": "9,500",  
"numberofemployees": 9500,  
"revenue@OData.Community.Display.V1.FormattedValue": "$100,000.00",  
"revenue": 100000,  
"accountid": "89390c24-9c72-e511-80d4-00155d2a68d1",  
"transactioncurrencyid_value": "50b6dd7b-f16d-e511-80d0-00155db07cb1" } ]  
}    
```  
  
<a name="bkmk_lookupProperty"></a>

## <a name="retrieve-data-about-lookup-properties"></a>Abrufen von Daten zu Sucheigenschaften

Wenn die Abfrage Sucheigenschaften enthält, können Sie Anmerkungen anfordern, die zusätzliche Informationen zu den Daten dieser Eigenschaften bieten. Meistens können die gleichen Daten mit Kenntnissen der einzelbewerteten Navigationseigenschaften und der Daten, die in den verknüpften Entitäten enthalten sind, abgeleitet werden. Wenn die Eigenschaft jedoch ein Suchattribut darstellt, das auf mehr als einen Entitätstyp verweisen kann, können Ihnen diese Informationen mitteilen, auf welchen Entitätstyp die Sucheigenschaft verweist. Weitere Informationen: [Such-Eigenschaften](web-api-types-operations.md#bkmk_lookupProperties)  
  
Es gibt zwei zusätzliche Anmerkungstypen für diese Eigenschaften.  
  
|Annotation|Beschreibung|  
|----------------|-----------------|  
|Microsoft.Dynamics.CRM.associatednavigationproperty|Der Name der einzelbewerteten Navigationseigenschaft, der den Verweis auf die Entität einschließt.|  
|Microsoft.Dynamics.CRM.lookuplogicalname|Der logische Name der Entität, auf die die Suche verweist.|  
  
Diese Eigenschaften können auch formatierte Werte enthalten, wie in [Formatierte Werte einschließen](query-data-web-api.md#bkmk_includeFormattedValues) beschrieben. Genau wie formatierte Werte können Sie die anderen Anmerkungen mithilfe der `odata.include-annotations`-Einstellung zurückgeben, die auf den bestimmten gewünschten Anmerkungstyp festgelegt ist, oder Sie können den Wert auf `"*"` festlegen und alle drei zurückgeben. Das folgende Beispiel zeigt die Anforderung und Antwort zum Abrufen von Informationen über die `_customerid_value`-Sucheigenschaft der Vorfall-Entität mit eingeschlossenen Anmerkungen.  
  
 **Anforderung**  

```http 
GET [Organization URI]/api/data/v9.0/incidents(39dd0b31-ed8b-e511-80d2-00155d2a68d4)?$select=title,customerid_value&$expand=customerid_contact($select=fullname) HTTP/1.1  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Prefer: odata.include-annotations="*"  
```  
  
 **Antwort**  

```http 
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="*"  
  
{  
"@odata.context":"[Organization URI]/api/data/v9.0/$metadata#incidents(title,_customerid_value,customerid_contact(fullname))/$entity",  
"@odata.etag":"W/\"504696\"",  
"_customerid_value@Microsoft.Dynamics.CRM.associatednavigationproperty":"customerid_contact",  
"_customerid_value@Microsoft.Dynamics.CRM.lookuplogicalname":"contact",  
"_customerid_value@OData.Community.Display.V1.FormattedValue":"Susanna Stubberod (sample)",  
"_customerid_value":"7ddd0b31-ed8b-e511-80d2-00155d2a68d4",  
"incidentid":"39dd0b31-ed8b-e511-80d2-00155d2a68d4",  
"customerid_contact":{  
"@odata.etag":"W/\"503587\"",  
"fullname":"Susanna Stubberod (sample)",  
"contactid":"7ddd0b31-ed8b-e511-80d2-00155d2a68d4"  
}  
}  
```  
  
<a name="BKMK_FilterNavProperties"></a>

## <a name="filter-records-based-on-single-valued-navigation-property"></a>Filterung von Datensätzen auf Grundlage einer einzelbewerteten Navigationseigenschaft

Navigationseigenschaften ermöglichen den Zugriff auf Daten zur aktuellen Entität. *Einzelwertige* Navigationseigenschaften entsprechen Suchattributen, die viel-zu-ein-Beziehungen unterstützen und eine Referenz auf eine andere Entität einstellen dürfen. Weitere Informationen: [Navigationseigenschaften](web-api-types-operations.md#bkmk_navprops)  
  
Sie können Ihre Entitätssatzdatensätze auf Grundlage einwertiger Navigationseigenschaftswerte filtern. Zum Beispiel können Sie untergeordnete Firmen für die angegebene Firma abrufen. Sie können nur den primären Attributswert der Entität verwenden, die von einer eintwertigen navigationseigenschaft verweisen wurde, um Datensätze zu filtern.  
  
 Beispiel:  
  
-   Abrufen aller passenden Firmen für eine angegebene Kontaktkennung  
  
    **Anforderung** 
 
    ```http 
    GET [Organization URI]/api/data/v9.0/accounts?$select=name&$filter=primarycontactid/contactid%20eq%20a0dbf27c-8efb-e511-80d2-00155db07c77 HTTP/1.1  
    Accept: application/json  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    ```  
  
    **Antwort**  

    ```http 
    HTTP/1.1 200 OK  
    Content-Type: application/json; odata.metadata=minimal  
    OData-Version: 4.0  
  
    {  
    "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts(name)",  
    "value":[  
    {  
    "@odata.etag":"W/\"513479\"",  
    "name":"Adventure Works (sample)",  
    "accountid":"3adbf27c-8efb-e511-80d2-00155db07c77"  
    },{  
    "@odata.etag":"W/\"514057\"",  
    "name":"Blue Yonder Airlines (sample)",  
    "accountid":"3edbf27c-8efb-e511-80d2-00155db07c77"  
    }  
    ]  
    }  
    ```  
  
-   Rufen Sie untergeordnete Konten für die angegebene Konto-ID ab.  
  
    **Anforderung**  

    ```http 
    GET [Organization URI]/api/data/v9.0/accounts?$select=name&$filter=parentaccountid/accountid%20eq%203adbf27c-8efb-e511-80d2-00155db07c77  
    Accept: application/json  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    ```  
  
    **Antwort**  

    ```http 
    HTTP/1.1 200 OK  
    Content-Type: application/json; odata.metadata=minimal  
    OData-Version: 4.0  
  
    {  
    "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts(name)",  
    "value":[  
    {  
    "@odata.etag":"W/\"514058\"",  
    "name":"Sample Child Account 1",  
    "accountid":"915e89f5-29fc-e511-80d2-00155db07c77"  
    },{  
    "@odata.etag":"W/\"514061\"",  
    "name":"Sample Child Account 2",  
    "accountid":"03312500-2afc-e511-80d2-00155db07c77"  
    }  
    ]  
    }    
    ```  
  
<a name="bkmk_expandRelated"></a>

## <a name="retrieve-related-entities-by-expanding-navigation-properties"></a>Abrufen verwandter Entitäten durch Erweitern der Navigationseigenschaften

Verwenden Sie die `$expand`-Systemabfrageoption in den Navigationseigenschaften, um zu steuern, welche Daten von den verbundenen Entitäten zurückgegeben werden. Es gibt zwei Typen von Navigationseigenschaften:  
  
- *Einzelwertige* Navigationseigenschaften entsprechen Suchattributen, die viel-zu-ein-Beziehungen unterstützen und eine Referenz auf eine andere Entität einstellen dürfen.  
  
- *Sammlungswertige* Navigationseigenschaften entsprechen ein-zu-vielen oder viel-zu-vielen Verhältnissen.  
  
Wenn Sie nur den Namen der Navigationseigenschaft einschließen, rufen Sie alle Eigenschaften für in Verbindung stehende Datensätze ab. Sie können die Eigenschaften begrenzen, die für in Verbindung stehende Aufzeichnungen unter Verwendung der Systemabfrageoption `$select` in Klammern nach dem Namen der Navigationseigenschaft zurückgegeben werden. Verwenden Sie dieses für einzelwertige und sammlungswertige Navigationseigenschaften.  
  
> [!NOTE]
>  Um verknüpfte Entitäten für eine Entitätsinstanz abzurufen, siehe [Abrufen verwandter Entitäten für eine Entität durch Erweitern der Navigationseigenschaften](retrieve-entity-using-web-api.md#bkmk_expandRelated).  
  
- **Rufen Sie verbundene Entitäten ab, indem Sie einzelwertige Navigationseigenschaften erweitern**: Das folgende Beispiel zeigt, wie Sie den Kontakt für alle Firmendatensätze abrufen. Für die in Verbindung stehenden Kontaktdatensätze rufen wir nur die Kontaktkennung und den vollen Namen ab.  
  
     **Anforderung**  

    ```http 
    GET [Organization URI]/api/data/v9.0/accounts?$select=name&$expand=primarycontactid($select=contactid,fullname) HTTP/1.1  
    Accept: application/json  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    ```  
  
     **Antwort** 
 
    ```http 
    HTTP/1.1 200 OK  
    Content-Type: application/json; odata.metadata=minimal  
    OData-Version: 4.0  
  
    {  
    "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts(name,primarycontactid,primarycontactid(contactid,fullname))","value":[  
    {  
    "@odata.etag":"W/\"513475\"","name":"Fourth Coffee (sample)","accountid":"36dbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "contactid":"9cdbf27c-8efb-e511-80d2-00155db07c77","fullname":"Yvonne McKay (sample)"  
    }  
    },{  
    "@odata.etag":"W/\"513477\"","name":"Litware, Inc. (sample)","accountid":"38dbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "contactid":"9edbf27c-8efb-e511-80d2-00155db07c77","fullname":"Susanna Stubberod (sample)"  
    }  
    },{  
    "@odata.etag":"W/\"513479\"","name":"Adventure Works (sample)","accountid":"3adbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "contactid":"a0dbf27c-8efb-e511-80d2-00155db07c77","fullname":"Nancy Anderson (sample)"  
    }  
    },{  
    "@odata.etag":"W/\"513481\"","name":"Fabrikam, Inc. (sample)","accountid":"3cdbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "contactid":"a2dbf27c-8efb-e511-80d2-00155db07c77","fullname":"Maria Campbell (sample)"  
    }  
    },{  
    "@odata.etag":"W/\"514057\"","name":"Blue Yonder Airlines (sample)","accountid":"3edbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "contactid":"a0dbf27c-8efb-e511-80d2-00155db07c77","fullname":"Nancy Anderson (sample)"  
    }  
    },{  
    "@odata.etag":"W/\"513485\"","name":"City Power & Light (sample)","accountid":"40dbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "contactid":"a6dbf27c-8efb-e511-80d2-00155db07c77","fullname":"Scott Konersmann (sample)"  
    }  
    },{  
    "@odata.etag":"W/\"513487\"","name":"Contoso Pharmaceuticals (sample)","accountid":"42dbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "contactid":"a8dbf27c-8efb-e511-80d2-00155db07c77","fullname":"Robert Lyon (sample)"  
    }  
    },{  
    "@odata.etag":"W/\"513489\"","name":"Alpine Ski House (sample)","accountid":"44dbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "contactid":"aadbf27c-8efb-e511-80d2-00155db07c77","fullname":"Paul Cannon (sample)"  
    }  
    },{  
    "@odata.etag":"W/\"513491\"","name":"A. Datum Corporation (sample)","accountid":"46dbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "contactid":"acdbf27c-8efb-e511-80d2-00155db07c77","fullname":"Rene Valdes (sample)"  
    }  
    },{  
    "@odata.etag":"W/\"513493\"","name":"Coho Winery (sample)","accountid":"48dbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "contactid":"aedbf27c-8efb-e511-80d2-00155db07c77","fullname":"Jim Glynn (sample)"  
    }  
    }  
    ]  
    }    
    ```  

Anstatt, die verbundenen Entitäten für Entitätensätze abzurufen, können Sie auch Verweise (Verbindungen) auf die verbundenen Entitäten zurückgeben, indem Sie die einwertige Navigationseigenschaft mit der Option `$ref` erweitern. Im folgenden Beispiel werden Links zum Kontaktdatensatz für alle Firmen zurückgegeben.  
  
 **Anforderung**

```http  
    GET [Organization URI]/api/data/v9.0/accounts?$select=name&$expand=primarycontactid/$ref HTTP/1.1  
    Accept: application/json  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
```  
  
 **Antwort**
 
```http 
    HTTP/1.1 200 OK  
    Content-Type: application/json; odata.metadata=minimal  
    OData-Version: 4.0  
  
    {  
    "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts(name,primarycontactid)","value":[  
    {  
    "@odata.etag":"W/\"513475\"","name":"Fourth Coffee (sample)","_primarycontactid_value":"9cdbf27c-8efb-e511-80d2-00155db07c77","accountid":"36dbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "@odata.id":"[Organization URI]/api/data/v9.0/contacts(9cdbf27c-8efb-e511-80d2-00155db07c77)"  
    }  
    },{  
    "@odata.etag":"W/\"513477\"","name":"Litware, Inc. (sample)","_primarycontactid_value":"9edbf27c-8efb-e511-80d2-00155db07c77","accountid":"38dbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "@odata.id":"[Organization URI]/api/data/v9.0/contacts(9edbf27c-8efb-e511-80d2-00155db07c77)"  
    }  
    },{  
    "@odata.etag":"W/\"513479\"","name":"Adventure Works (sample)","_primarycontactid_value":"a0dbf27c-8efb-e511-80d2-00155db07c77","accountid":"3adbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "@odata.id":"[Organization URI]/api/data/v9.0/contacts(a0dbf27c-8efb-e511-80d2-00155db07c77)"  
    }  
    },{  
    "@odata.etag":"W/\"513481\"","name":"Fabrikam, Inc. (sample)","_primarycontactid_value":"a2dbf27c-8efb-e511-80d2-00155db07c77","accountid":"3cdbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "@odata.id":"[Organization URI]/api/data/v9.0/contacts(a2dbf27c-8efb-e511-80d2-00155db07c77)"  
    }  
    },{  
    "@odata.etag":"W/\"514057\"","name":"Blue Yonder Airlines (sample)","_primarycontactid_value":"a0dbf27c-8efb-e511-80d2-00155db07c77","accountid":"3edbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "@odata.id":"[Organization URI]/api/data/v9.0/contacts(a0dbf27c-8efb-e511-80d2-00155db07c77)"  
    }  
    },{  
    "@odata.etag":"W/\"513485\"","name":"City Power & Light (sample)","_primarycontactid_value":"a6dbf27c-8efb-e511-80d2-00155db07c77","accountid":"40dbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "@odata.id":"[Organization URI]/api/data/v9.0/contacts(a6dbf27c-8efb-e511-80d2-00155db07c77)"  
    }  
    },{  
    "@odata.etag":"W/\"513487\"","name":"Contoso Pharmaceuticals (sample)","_primarycontactid_value":"a8dbf27c-8efb-e511-80d2-00155db07c77","accountid":"42dbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "@odata.id":"[Organization URI]/api/data/v9.0/contacts(a8dbf27c-8efb-e511-80d2-00155db07c77)"  
    }  
    },{  
    "@odata.etag":"W/\"513489\"","name":"Alpine Ski House (sample)","_primarycontactid_value":"aadbf27c-8efb-e511-80d2-00155db07c77","accountid":"44dbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "@odata.id":"[Organization URI]/api/data/v9.0/contacts(aadbf27c-8efb-e511-80d2-00155db07c77)"  
    }  
    },{  
    "@odata.etag":"W/\"513491\"","name":"A. Datum Corporation (sample)","_primarycontactid_value":"acdbf27c-8efb-e511-80d2-00155db07c77","accountid":"46dbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "@odata.id":"[Organization URI]/api/data/v9.0/contacts(acdbf27c-8efb-e511-80d2-00155db07c77)"  
    }  
    },{  
    "@odata.etag":"W/\"513493\"","name":"Coho Winery (sample)","_primarycontactid_value":"aedbf27c-8efb-e511-80d2-00155db07c77","accountid":"48dbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "@odata.id":"[Organization URI]/api/data/v9.0/contacts(aedbf27c-8efb-e511-80d2-00155db07c77)"  
    }  
    }  
    ]  
    }  
```  

- **Rufen Sie verbundene Entitäten ab, indem Sie sammlungswertige Navigationseigenschaften erweitern**: Wenn Sie auf sammlungswertige Navigationsparameter erweitern, um verbundene Entitäten für Entitätssätze abzurufen, wird eine @odata.nextLink-Eigenschaft für die verbundenen Eintäten zurückgegeben. Sie sollten den Wert der @odata.nextLink-Eigenschaft mit einer neuen GET-Anforderung nutzen, um die benötigten Daten zurückzugeben.  
  
    Im folgenden Beispiel werden die Aufgaben zurückgegeben, die den Ersten 5 Firmendatensätzen zugewiesen werden.  
  
     **Anforderung**

    ```http 
        GET [Organization URI]/api/data/v9.0/accounts?$top=5&$select=name&$expand=Account_Tasks($select%20=%20subject,%20scheduledstart) HTTP/1.1  
        Accept: application/json  
        OData-MaxVersion: 4.0  
        OData-Version: 4.0  
    ```  
  
     **Antwort** 
 
    ```http 
        HTTP/1.1 200 OK  
        Content-Type: application/json; odata.metadata=minimal  
        OData-Version: 4.0  
  
        {  
        "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts(name,Account_Tasks,Account_Tasks(subject,scheduledstart))","value":[  
        {  
        "@odata.etag":"W/\"513475\"","name":"Fourth Coffee (sample)","accountid":"36dbf27c-8efb-e511-80d2-00155db07c77","Account_Tasks":[  
  
        ],"Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.0/accounts(36dbf27c-8efb-e511-80d2-00155db07c77)/Account_Tasks?$select%20=%20subject,%20scheduledstart"  
        },{  
        "@odata.etag":"W/\"513477\"","name":"Litware, Inc. (sample)","accountid":"38dbf27c-8efb-e511-80d2-00155db07c77","Account_Tasks":[  
  
        ],"Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.0/accounts(38dbf27c-8efb-e511-80d2-00155db07c77)/Account_Tasks?$select%20=%20subject,%20scheduledstart"  
        },{  
        "@odata.etag":"W/\"514074\"","name":"Adventure Works (sample)","accountid":"3adbf27c-8efb-e511-80d2-00155db07c77","Account_Tasks":[  
  
        ],"Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.0/accounts(3adbf27c-8efb-e511-80d2-00155db07c77)/Account_Tasks?$select%20=%20subject,%20scheduledstart"  
        },{  
        "@odata.etag":"W/\"513481\"","name":"Fabrikam, Inc. (sample)","accountid":"3cdbf27c-8efb-e511-80d2-00155db07c77","Account_Tasks":[  
  
        ],"Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.0/accounts(3cdbf27c-8efb-e511-80d2-00155db07c77)/Account_Tasks?$select%20=%20subject,%20scheduledstart"  
        },{  
        "@odata.etag":"W/\"514057\"","name":"Blue Yonder Airlines (sample)","accountid":"3edbf27c-8efb-e511-80d2-00155db07c77","Account_Tasks":[  
  
        ],"Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.0/accounts(3edbf27c-8efb-e511-80d2-00155db07c77)/Account_Tasks?$select%20=%20subject,%20scheduledstart"  
        }  
        ]  
        }  
    ```  
  
- **Rufen Sie verbundene Entitäten durch Erweitern von einzelwertigen und sammlungswertigen Navigationseigenschaften ab**: Das folgende Beispiel zeigt, wie Sie verbundene Entitäten für Entitätssätze unter Verwendung der einzel- und sammlungswertigen Navigationseigenschaften erweitern können. Wie zuvor erklärt, gibt die Erweiterung auf sammlungswertige Navigationseigenschaften, um verbundene Entitäten für Entitätssätze zurückzugeben eine @odata.nextLink-Eigenschaft für die verbundenen Entitäten zurück. Sie sollten den Wert der @odata.nextLink-Eigenschaft mit einer neuen GET-Anforderung nutzen, um die benötigten Daten zurückzugeben.  
  
     In diesem Beispiel rufen wir den Kontakt und die Aufgaben ab, die den ersten 3 Firmen zugewiesen werden.  
  
     **Anforderung**

    ```http 
    GET [Organization URI]/api/data/v9.0/accounts?$top=3&$select=name&$expand=primarycontactid($select=contactid,fullname),Account_Tasks($select=subject,scheduledstart)  HTTP/1.1  
    Accept: application/json  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    ```  
  
     **Antwort**  

    ```http 
    HTTP/1.1 200 OK  
    Content-Type: application/json; odata.metadata=minimal  
    OData-Version: 4.0  
  
    {  
    "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts(name,primarycontactid,Account_Tasks,primarycontactid(contactid,fullname),Account_Tasks(subject,scheduledstart))","value":[  
    {  
    "@odata.etag":"W/\"550614\"",  
    "name":"Fourth Coffee (sample)",  
    "accountid":"5b9648c3-68f7-e511-80d3-00155db53318",  
    "primarycontactid":{  
    "contactid":"c19648c3-68f7-e511-80d3-00155db53318",  
    "fullname":"Yvonne McKay (sample)"  
    },  
    "Account_Tasks":[  
  
    ],"Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.0/accounts(5b9648c3-68f7-e511-80d3-00155db53318)/Account_Tasks?$select=subject,scheduledstart"  
    },{  
    "@odata.etag":"W/\"550615\"",  
    "name":"Litware, Inc. (sample)",  
    "accountid":"5d9648c3-68f7-e511-80d3-00155db53318",  
    "primarycontactid":{  
    "contactid":"c39648c3-68f7-e511-80d3-00155db53318",  
    "fullname":"Susanna Stubberod (sample)"  
    },"Account_Tasks":[  
  
    ],"Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.0/accounts(5d9648c3-68f7-e511-80d3-00155db53318)/Account_Tasks?$select=subject,scheduledstart"  
    },{  
    "@odata.etag":"W/\"550616\"",  
    "name":"Adventure Works (sample)",  
    "accountid":"5f9648c3-68f7-e511-80d3-00155db53318",  
    "primarycontactid":{  
    "contactid":"c59648c3-68f7-e511-80d3-00155db53318",  
    "fullname":"Nancy Anderson (sample)"  
    },"Account_Tasks":[  
  
    ],"Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.0/accounts(5f9648c3-68f7-e511-80d3-00155db53318)/Account_Tasks?$select=subject,scheduledstart"  
    }  
    ]  
    }  
    ```

## <a name="filter-results-based-on-values-of-collection-valued-navigation-properties"></a>Filtern von Ergebnissen basierend auf Werten von sammlungsbewerteten Navigationseigenschaften

Sie können OData $filter nicht verwenden, um Suchkriterien festzulegen, für Werte in sammlungsbewerteten Navigationseigenschaften in einem einzelnen Vorgang gelten.
Sie haben zwei Möglichkeiten:
- Erstellen einer Abfrage unter Verwendung von FetchXML  Weitere Informationen: Benutzerdefiniertes FetchXML verwenden
- Lesen Sie über Sie die Ergebnisse nach, indem Sie einzelne Entitäten auf Grundlage der Werte in der Sammlung mit mehreren Vorgänge filtern.

Im Allgemeinen sollte die Verwendung von FetchXML eine Leistungssteigerung bieten, da der Filter auf eine Serverseite in einem einzelnen Vorgang angewendet werden kann. Das Beispiel unten zeigt, wie Filterwerte auf Sammlungseigenschaften für eine LinkEntität angewendet werden.

```xml
<fetch version="1.0" output-format="xml-platform" mapping="logical" distinct="true">
  <entity name="systemuser">
    <attribute name="fullname" />
    <attribute name="businessunitid" />
    <attribute name="title" />
    <attribute name="address1_telephone1" />
    <attribute name="positionid" />
    <attribute name="systemuserid" />
    <order attribute="fullname" descending="false" />
    <link-entity name="teammembership" from="systemuserid" to="systemuserid" visible="false" intersect="true">
      <link-entity name="team" from="teamid" to="teamid" alias="ab">
        <filter type="and">
          <condition attribute="administratorid" operator="eq-userid" />
        </filter>
      </link-entity>
    </link-entity>
  </entity>
</fetch>
```
  
### <a name="see-also"></a>Siehe auch

[Web API-Abfragedatenbeispiel (C#)](samples/query-data-csharp.md)<br />
[Web API-Abfragedatenbeispiele (clientseitiges JavaScript)](samples/query-data-client-side-javascript.md)<br />
[Vorgänge mithilfe der Web-API ausführen](perform-operations-web-api.md)<br />
[HTTP-Anforderungen verfassen und Fehler beheben](compose-http-requests-handle-errors.md)<br />
[Erstellen einer Entität mithilfe des Web-API](create-entity-web-api.md)<br />
[Abrufen einer Entität mithilfe des Web-API](retrieve-entity-using-web-api.md)<br />
[Entitäten aktualisieren und löschen mithilfe der Web API](update-delete-entities-using-web-api.md)<br />
[Entitäten zuordnen und Zuordnungen aufheben mithilfe der Web API](associate-disassociate-entities-using-web-api.md)<br />
[Nutzen von Web-API-Funktionen](use-web-api-functions.md)<br />
[Nutzen von Web-API-Aktionen](use-web-api-actions.md)<br />
[Ausführen von Batchbetrieben mithilfe der Web-API](execute-batch-operations-using-web-api.md)<br />
[Annehmen eines anderen Benutzerkontos mit Web API](impersonate-another-user-web-api.md)<br />
[Bedingte Vorgänge mithilfe der Web-API ausführen](perform-conditional-operations-using-web-api.md)
