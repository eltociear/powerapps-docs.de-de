---
title: Steuerdatum und "älter als"-Datums-/Zeit-Abfrageoperatoren in FetchXML (Common Data Service) | Microsoft Docs
description: Infos zur Verwendung von konditionalen FetchXML-Steuerdatenoperatoren und &quot;älter als&quot;-Klausen für Datums- und Uhrzeitwerte
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
# <a name="fiscal-date-and-older-than-datetime-query-operators-in-fetchxml"></a>Steuerdatum und "älter als"-Datums-/Zeit-Abfrageoperatoren in FetchXML

Eine FetchXML-Abfrage in Common Data Service kann spezielle Steuerdatumswerte und *älter als*-Klauseln für Datums- und Uhrzeitwerte in Abfragen verwenden. Beispielsweise kann eine FetchXML-Abfrage alle Bestellungen finden, die im letzten Geschäftsmonat erfüllt wurden, oder dringende Anfragen mit hohem Schweregrad, die älter sind als 15 Minuten.  
  
> [!NOTE]
>  Die FetchXML-Abfrage verwendet die Einstellungen zum Geschäftsjahr der Organisation für alle Steuerdatumsabfragen.  
  
<a name="FiscalDate"></a>   
## <a name="using-fetchxml-fiscal-date-conditional-operators"></a>Verwenden von Steuerdatum-Bedingungsoperatoren in FetchXML  
 Das folgende Beispiel zeigt einen FetchXML-Ausdruck, der alle Aufträge sucht, die in der letzten Buchhaltungsperiode erfüllt wurden, entsprechend der Einstellungen zum Geschäftsjahr der Organisation. Wenn die Organisation beispielsweise Geschäftsmonate verwendet, gibt die Abfrage Aufträge zurück, die im letzten Geschäftsmonat erfüllt wurden. Wenn die Organisation beispielsweise Geschäftsquartale verwendet, gibt die Abfrage Aufträge zurück, die im letzten Geschäftsquartal erfüllt wurden. Wenn die Organisation beispielsweise Geschäftshalbjahre verwendet, gibt die Abfrage Aufträge zurück, die im letzten Geschäftshalbjahr erfüllt wurden.  
  
```xml  
<fetch>  
 <entity name="order">  
  <attribute name="name"/>  
  <filter type="and">  
   <condition attribute="datefulfilled" operator="last-fiscal-period"/>  
  </filter>  
 </entity>  
</fetch>  
```  
  
 Das folgende Beispiel zeigt einen FetchXML-Ausdruck, der alle Firmen sucht, die im Geschäftsjahr 2013 erstellt wurden.  
  
```xml  
<fetch>  
 <entity name="account">  
  <attribute name="name"/>  
  <filter type="and">  
   <condition attribute="createdon" operator="in-fiscal-year" value="2013"/>  
  </filter>  
 </entity>  
</fetch>  
```  
  
 Das folgende Beispiel zeigt einen FetchXML-Ausdruck, der alle Verkaufschancen mit einem geschätzten Abschlussdatum in den folgenden drei Geschäftsjahren sucht, basierend auf den Einstellungen zum Geschäftsjahr der Organisation. Der Wert für `x` wird im Wertattribut des Bedingungstags angegeben.  
  
```xml  
<fetch>  
 <entity name="opportunity">  
  <attribute name="name"/>  
  <filter type="and">  
   <condition attribute="estimatedclosedate" operator="next-x-fiscal-years" value="3"/>  
  </filter>  
 </entity>  
</fetch>  
```  
  
 Das folgende Beispiel zeigt einen FetchXML-Ausdruck, der alle Aufträge sucht, die in der dritten Periode eines Geschäftsjahrs erfüllt wurden, entsprechend der Einstellungen zum Geschäftsjahr der Organisation. Der Wert für die Buchhaltungsperiode wird im Wertattribut des Bedingungstags angegeben. Wenn die Organisation Geschäftsmonate verwendet, gibt die Abfrage Ergebnisse von Monat drei zurück. Wenn die Organisation Geschäftsquartale verwendet, gibt die Abfrage Ergebnisse von Quartal drei zurück. Wenn die Organisation Geschäftshalbjahre verwendet, werden keine Ergebnisse zurückgegeben; es gibt nur zwei Halbjahre, und der Wert liegt daher außerhalb des Gültigkeitsbereichs.  
  
```xml  
<fetch>  
 <entity name="order">  
  <attribute name="name"/>  
  <filter type="and">  
   <condition attribute="datefulfilled" operator="in-fiscal-period" value="3"/>  
  </filter>  
 </entity>  
</fetch>  
```  
  
 Das folgende Beispiel zeigt einen FetchXML-Ausdruck, der alle Aufträge sucht, die in der dritten Periode des Geschäftsjahrs 2013 erfüllt wurden, entsprechend der Einstellungen zum Geschäftsjahr der Organisation. Wenn die Organisation Geschäftsmonate verwendet, gibt die Abfrage Ergebnisse von Monat drei zurück. Wenn die Organisation Geschäftsquartale verwendet, gibt die Abfrage Ergebnisse von Quartal drei zurück. Wenn die Organisation Geschäftshalbjahre verwendet, werden keine Ergebnisse zurückgegeben; es gibt nur zwei Halbjahre, und der Wert liegt daher außerhalb des Gültigkeitsbereichs.  
  
```xml  
<fetch>  
 <entity name="order">  
  <attribute name="name"/>  
  <filter type="and">  
   <condition attribute="datefulfilled" operator="in-fiscal-period-and-year">  
    <value>3</value>  
    <value>2013</value>  
   </condition>  
  </filter>  
 </entity>  
</fetch>  
```  
  
 Das folgende Beispiel zeigt einen FetchXML-Aggregationsausdruck, der den Gesamtbetrag von erfüllten Aufträgen summiert und das Ergebnis nach Geschäftshalbjahr und Geschäftsjahr gruppiert.  
  
```xml  
<fetch aggregate="true">  
 <entity name="order">  
  <attribute name="totalamount" aggregate="sum" alias="total"/>  
  <attribute name="datefulfilled" groupby="true" dategrouping="fiscal-period"/>  
 </entity>  
</fetch>  
```  
  
<a name="OlderThan"></a>   
## <a name="using-older-than-clauses-for-date-and-time-values"></a>Verwenden von "älter als"-Klauseln für Datums- und Uhrzeitwerte  
 Im folgenden Beispiel wird ein FetchXML-Ausdruck gezeigt, der Vorfälle findet, die älter sind als 30 Minuten.  
  
```xml  
<fetch>  
  <entity name="incident">  
    <attribute name="title" />  
    <attribute name="ticketnumber" />  
    <attribute name="createdon" />  
    <attribute name="incidentid" />  
    <filter type="and">  
      <condition attribute="createdon" operator="olderthan-x-minutes" value="30" />  
    </filter>  
  </entity>  
</fetch>  
```  
  
 Verwenden Sie die folgende Syntax, um verschiedene *älter als*-Klauseln in einem FetchXML-Ausdruck anzugeben.  
  
 Älter als x Minuten  
 ```xml  
<condition attribute="<AttributeName>" operator="olderthan-x-minutes" value="<VALUE>" />  
```  
  
> [!NOTE]
>  Diese Klausel wird für Datums- und Zeitattribute mit `DateOnly`-Verhalten nicht unterstützt. Weitere Informationen: [Datums- und Uhrzeitabfrageoperatoren für DateOnly-Verhalten werden nicht unterstützt](/dynamics365/customer-engagement/developer/behavior-format-date-time-attribute#date-and-time-query-operators-not-supported-for-dateonly-behavior)
  
 Älter als x Stunden  
 ```xml  
<condition attribute="<AttributeName>" operator="olderthan-x-hours" value="<VALUE>" />  
```  
  
> [!NOTE]
>  Diese Klausel wird für Datums- und Zeitattribute mit `DateOnly`-Verhalten nicht unterstützt. Weitere Informationen: [Datums- und Uhrzeitabfrageoperatoren für DateOnly-Verhalten werden nicht unterstützt](/dynamics365/customer-engagement/developer/behavior-format-date-time-attribute#date-and-time-query-operators-not-supported-for-dateonly-behavior)  
  
 Älter als x Tage  
 ```xml  
<condition attribute="<AttributeName>" operator="olderthan-x-days" value="<VALUE>" />  
```  
  
 Älter als x Wochen  
 ```xml  
<condition attribute="<AttributeName>" operator="olderthan-x-weeks" value="<VALUE>" />  
```  
  
 Älter als X Monate  
 ```xml  
<condition attribute="<AttributeName>" operator="olderthan-x-months" value="<VALUE>" />  
```  
  
 Älter als x Jahre  
 ```xml  
<condition attribute="<AttributeName>" operator="olderthan-x-years" value="<VALUE>" />  
```

### <a name="see-also"></a>Siehe auch  
 [Erstellen von Abfragen zum Abrufen von Daten](/dynamics365/customer-engagement/developer/org-service/retrieve-data-queries-sdk-assemblies)   
 [Abfragen erstellen mit FetchXML](/dynamics365/customer-engagement/developer/org-service/build-queries-fetchxml)   
 [Verwenden einer linken äußeren Verknüpfung in FetchXML für Abfragen nach Datensätzen, die „nicht in“ sind.](/dynamics365/customer-engagement/developer/use-left-outer-join-fetchxml-query-records-not-in)
