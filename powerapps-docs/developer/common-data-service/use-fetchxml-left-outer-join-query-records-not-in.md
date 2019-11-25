---
title: Verwenden einer linken äußeren Verknüpfung in FetchXML für Abfragen nach Datensätzen, die &bdquo;nicht in&bdquo; sind (Common Data Service) | Microsoft-Dokumentation
description: Erfahren Sie, wie eine linke äußere Verknüpfung mithilfe der FetchXML-Klasse verwendet wird, um eine Abfrage auszuführen, die die Verknüpfungstabelle filtert, und eine Abfrage zu erstellen, die Datensätze des Typs „nicht in“ in einer Gruppe findet
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
ms.openlocfilehash: e50ff095affda6c976b838b1f368026640fcb2b2
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748509"
---
# <a name="use-a-left-outer-join-in-fetchxml-to-query-for-records-not-in"></a>Verwenden einer linken äußeren Verknüpfung in FetchXML für Abfragen nach Datensätzen, die „nicht in“ sind.

Sie können eine linke äußere Verknüpfung in FetchXML verwenden, um eine Abfrage auszuführen, die auf der Verknüpfungstabelle filtert, wie zum Beispiel alle Kontakte zu suchen, bei denen in den letzten beiden Monaten keine Kampagnenaktivitäten stattfanden. Eine weitere allgemeine Verwendung dieses Abfragetyps ist das Suchen von Datensätzen, die „nicht in“ sind, wie in folgenden Fällen:  
  
- Suchen aller Leads, die über keine Tasks verfügen.  
  
- Suchen aller Firmen, die über keine Kontakte verfügen  
  
- Suchen aller Leads, die mindestens eine Task verfügen.  
  
  Eine linke äußere Verknüpfung gibt jede Zeile zurück, die der Verknüpfung der ersten Eingabe mit der zweiten Eingabe entspricht. Es werden auch alle Zeilen aus der ersten Eingabe zurückgegeben, die in der zweiten Eingabe keine Übereinstimmung haben. Die nicht übereinstimmenden Zeilen in der zweiten Eingabe werden als Nullwerte zurückgegeben.  
  
  Sie können eine linke äußere Verknüpfung in FetchXML ausführen, indem Sie das Attribut `entityname` als Bedingungsoperator verwenden. Das Attribut `entityname` ist auch für die Bedingungen, Filter und geschachtelte Filter gültig.  
  
  Sie können eine Abfrage mithilfe einer linken, äußeren Verknüpfung programmatisch erstellen und die Abfrage mithilfe von <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest> ausführen, und Sie können die Abfrage speichern, indem Sie einen `SavedQuery`-Datensatz erstellen. Sie können eine gespeicherte Abfrage öffnen, die eine linke, äußere Verknüpfung in den Editoren für die Erweiterte Suche oder Gespeicherte Abfrage in der Webanwendung enthält, und Sie können die Ergebnisse anzeigen. Manche Funktionen des Editors sind aber deaktiviert. Diese Editoren lassen Änderungen der Abfrage zu, wie beispielsweise die zurückgegebenen Spalten zu ändern. Der Editor unterstützt jedoch nicht das Ändern der linken, äußeren Verknüpfung.  
  
## <a name="example-find-all-accounts-that-have-no-leads"></a>Beispiel: Suchen Sie alle Firmen, die über keine Leads verfügen.  
 Nachfolgend wird veranschaulicht, wie die Abfrage in FetchXML erstellt wird:  
  
```xml  
<fetch mapping='logical'>  
 <entity name='account'>  
  <attribute name='name'/>  
  <link-entity name='lead'  
               from='leadid'  
               to='originatingleadid'  
               link-type='outer'/>  
  <filter type='and'>  
   <condition entityname='lead'  
              attribute='leadid'  
              operator='null'/>  
  </filter>  
 </entity>  
</fetch>  
  
```  
  
## <a name="example-find-all-leads-that-have-no-tasks-using-an-alias"></a>Beispiel: Suchen Sie alle Leads, die keine Aufgaben haben, mithilfe eines Alias  
 Nachfolgend wird veranschaulicht, wie die Abfrage in FetchXML erstellt wird:  
  
```xml  
<fetch version="1.0" output-format="xml-platform" mapping="logical" distinct="true">  
  <entity name="lead">  
    <attribute name="fullname" />  
    <link-entity name="task" from="regardingobjectid" to="leadid" alias="ab" link-type="outer">  
       <attribute name="regardingobjectid" />  
    </link-entity>  
    <filter type="and">  
        <condition entityname="ab" attribute="regardingobjectid" operator="null" />  
    </filter>  
  </entity>  
<fetch/>  
  
```  
  
 Dies ist äquivalent zu folgendem SQL:  
  
```sql  
SELECT lead.FullName  
FROM Leads as lead  
LEFT OUTER JOIN Tasks as ab  
ON (lead.leadId  =  ab.RegardingObjectId)  
WHERE ab.RegardingObjectId is null  
  
```  
  
### <a name="see-also"></a>Siehe auch  
 [Abfragen erstellen mit FetchXML](/dynamics365/customer-engagement/developer/org-service/build-queries-fetchxml)   
 [Beispiel: Verwendung von Aggregation in FetchXML](org-service/samples/use-aggregation-fetchxml.md)   
 [Verwenden von FetchXML zum Erstellen einer Abfrage](use-fetchxml-construct-query.md)   
 [Beispiel: Überprüfen und ausführen einer gespeicherten Abfrage](org-service/samples/validate-execute-saved-query.md)
