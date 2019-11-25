---
title: Abrufen von verknüpften Entitätsdatensätzen mit einer Abfrage (Common Data Service) | Microsoft-Dokumentation
description: Lesen Sie, wie Sie verknüpfte Entitätsdatensätze abrufen können, indem Sie die Navigationseigenschaften erweitern.
ms.custom: ''
ms.date: 07/15/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 3D8FB9AF-3663-437A-988E-CBAE9579F167
caps.latest.revision: 78
author: susikka
ms.author: susikka
manager: shujoshi
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1119734dd8d61aacdbb3dc553b65c12b4d6c20a9
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748614"
---
# <a name="retrieve-related-entity-records-with-a-query"></a>Abrufen von verknüpften Entitätsdatensätzen mit einer Abfrage

Verwenden Sie die `$expand`-Systemabfrageoption in den Navigationseigenschaften, um zu steuern, welche Daten von den verbundenen Entitäten zurückgegeben werden. Es gibt zwei Typen von Navigationseigenschaften:  
  
- *Einzelwertige* Navigationseigenschaften entsprechen Suchattributen, die viel-zu-ein-Beziehungen unterstützen und eine Referenz auf eine andere Entität einstellen dürfen.  
  
- *Sammlungswertige* Navigationseigenschaften entsprechen ein-zu-vielen oder viel-zu-vielen Verhältnissen.  
  
Wenn Sie nur den Namen der Navigationseigenschaft einschließen, rufen Sie alle Eigenschaften für in Verbindung stehende Datensätze ab. Sie können die Eigenschaften begrenzen, die für in Verbindung stehende Aufzeichnungen unter Verwendung der Systemabfrageoption `$select` in Klammern nach dem Namen der Navigationseigenschaft zurückgegeben werden. Verwenden Sie dieses für einzelwertige und sammlungswertige Navigationseigenschaften.  

> [!NOTE]
>  Um verknüpfte Entitäten für eine Entitätsinstanz abzurufen, siehe [Abrufen verwandter Entitäten für eine Entität durch Erweitern der Navigationseigenschaften](retrieve-entity-using-web-api.md#bkmk_expandRelated).  

<a bkmk="bkmk_retrieverelatedentityexpandsinglenavprop"></a>

## <a name="retrieve-related-entity-records-by-expanding-single-valued-navigation-properties"></a>Abrufen verwandter Entitätsdatensätze durch Erweitern von einfach bewerteten Navigationseigenschaften

Im folgenden Beispiel wird gezeigt, wie der Kontakt für alle Firmendatensätze abgerufen wird. Für die in Verbindung stehenden Kontaktdatensätze rufen wir nur die Kontaktkennung und den vollen Namen ab.  
  
**Anforderung**  

```http 
GET [Organization URI]/api/data/v9.1/accounts?$select=name&$expand=primarycontactid($select=contactid,fullname) HTTP/1.1  
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
   "@odata.context":"[Organization URI]/api/data/v9.1/$metadata#accounts(name,primarycontactid,primarycontactid(contactid,fullname))",
   "value":[  
      {  
         "@odata.etag":"W/\"513475\"",
         "name":"Fourth Coffee (sample)",
         "accountid":"36dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "contactid":"9cdbf27c-8efb-e511-80d2-00155db07c77",
            "fullname":"Yvonne McKay (sample)"
         }
      },
      {  
         "@odata.etag":"W/\"513477\"",
         "name":"Litware, Inc. (sample)",
         "accountid":"38dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "contactid":"9edbf27c-8efb-e511-80d2-00155db07c77",
            "fullname":"Susanna Stubberod (sample)"
         }
      },
      {  
         "@odata.etag":"W/\"513479\"",
         "name":"Adventure Works (sample)",
         "accountid":"3adbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "contactid":"a0dbf27c-8efb-e511-80d2-00155db07c77",
            "fullname":"Nancy Anderson (sample)"
         }
      },
      {  
         "@odata.etag":"W/\"513481\"",
         "name":"Fabrikam, Inc. (sample)",
         "accountid":"3cdbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "contactid":"a2dbf27c-8efb-e511-80d2-00155db07c77",
            "fullname":"Maria Campbell (sample)"
         }
      },
      {  
         "@odata.etag":"W/\"514057\"",
         "name":"Blue Yonder Airlines (sample)",
         "accountid":"3edbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "contactid":"a0dbf27c-8efb-e511-80d2-00155db07c77",
            "fullname":"Nancy Anderson (sample)"
         }
      },
      {  
         "@odata.etag":"W/\"513485\"",
         "name":"City Power & Light (sample)",
         "accountid":"40dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "contactid":"a6dbf27c-8efb-e511-80d2-00155db07c77",
            "fullname":"Scott Konersmann (sample)"
         }
      },
      {  
         "@odata.etag":"W/\"513487\"",
         "name":"Contoso Pharmaceuticals (sample)",
         "accountid":"42dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "contactid":"a8dbf27c-8efb-e511-80d2-00155db07c77",
            "fullname":"Robert Lyon (sample)"
         }
      },
      {  
         "@odata.etag":"W/\"513489\"",
         "name":"Alpine Ski House (sample)",
         "accountid":"44dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "contactid":"aadbf27c-8efb-e511-80d2-00155db07c77",
            "fullname":"Paul Cannon (sample)"
         }
      },
      {  
         "@odata.etag":"W/\"513491\"",
         "name":"A. Datum Corporation (sample)",
         "accountid":"46dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "contactid":"acdbf27c-8efb-e511-80d2-00155db07c77",
            "fullname":"Rene Valdes (sample)"
         }
      },
      {  
         "@odata.etag":"W/\"513493\"",
         "name":"Coho Winery (sample)",
         "accountid":"48dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "contactid":"aedbf27c-8efb-e511-80d2-00155db07c77",
            "fullname":"Jim Glynn (sample)"
         }
      }
   ]
}    
```  

Anstatt, die verbundenen Entitäten für Entitätensätze abzurufen, können Sie auch Verweise (Verbindungen) auf die verbundenen Entitäten zurückgeben, indem Sie die einwertige Navigationseigenschaft mit der Option `$ref` erweitern. Im folgenden Beispiel werden Links zum Kontaktdatensatz für alle Firmen zurückgegeben.  
  
 **Anforderung**

```http  
GET [Organization URI]/api/data/v9.1/accounts?$select=name&$expand=primarycontactid/$ref HTTP/1.1  
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
   "@odata.context":"[Organization URI]/api/data/v9.1/$metadata#accounts(name,primarycontactid)",
   "value":[  
      {  
         "@odata.etag":"W/\"513475\"",
         "name":"Fourth Coffee (sample)",
         "_primarycontactid_value":"9cdbf27c-8efb-e511-80d2-00155db07c77",
         "accountid":"36dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "@odata.id":"[Organization URI]/api/data/v9.1/contacts(9cdbf27c-8efb-e511-80d2-00155db07c77)"
         }
      },
      {  
         "@odata.etag":"W/\"513477\"",
         "name":"Litware, Inc. (sample)",
         "_primarycontactid_value":"9edbf27c-8efb-e511-80d2-00155db07c77",
         "accountid":"38dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "@odata.id":"[Organization URI]/api/data/v9.1/contacts(9edbf27c-8efb-e511-80d2-00155db07c77)"
         }
      },
      {  
         "@odata.etag":"W/\"513479\"",
         "name":"Adventure Works (sample)",
         "_primarycontactid_value":"a0dbf27c-8efb-e511-80d2-00155db07c77",
         "accountid":"3adbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "@odata.id":"[Organization URI]/api/data/v9.1/contacts(a0dbf27c-8efb-e511-80d2-00155db07c77)"
         }
      },
      {  
         "@odata.etag":"W/\"513481\"",
         "name":"Fabrikam, Inc. (sample)",
         "_primarycontactid_value":"a2dbf27c-8efb-e511-80d2-00155db07c77",
         "accountid":"3cdbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "@odata.id":"[Organization URI]/api/data/v9.1/contacts(a2dbf27c-8efb-e511-80d2-00155db07c77)"
         }
      },
      {  
         "@odata.etag":"W/\"514057\"",
         "name":"Blue Yonder Airlines (sample)",
         "_primarycontactid_value":"a0dbf27c-8efb-e511-80d2-00155db07c77",
         "accountid":"3edbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "@odata.id":"[Organization URI]/api/data/v9.1/contacts(a0dbf27c-8efb-e511-80d2-00155db07c77)"
         }
      },
      {  
         "@odata.etag":"W/\"513485\"",
         "name":"City Power & Light (sample)",
         "_primarycontactid_value":"a6dbf27c-8efb-e511-80d2-00155db07c77",
         "accountid":"40dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "@odata.id":"[Organization URI]/api/data/v9.1/contacts(a6dbf27c-8efb-e511-80d2-00155db07c77)"
         }
      },
      {  
         "@odata.etag":"W/\"513487\"",
         "name":"Contoso Pharmaceuticals (sample)",
         "_primarycontactid_value":"a8dbf27c-8efb-e511-80d2-00155db07c77",
         "accountid":"42dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "@odata.id":"[Organization URI]/api/data/v9.1/contacts(a8dbf27c-8efb-e511-80d2-00155db07c77)"
         }
      },
      {  
         "@odata.etag":"W/\"513489\"",
         "name":"Alpine Ski House (sample)",
         "_primarycontactid_value":"aadbf27c-8efb-e511-80d2-00155db07c77",
         "accountid":"44dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "@odata.id":"[Organization URI]/api/data/v9.1/contacts(aadbf27c-8efb-e511-80d2-00155db07c77)"
         }
      },
      {  
         "@odata.etag":"W/\"513491\"",
         "name":"A. Datum Corporation (sample)",
         "_primarycontactid_value":"acdbf27c-8efb-e511-80d2-00155db07c77",
         "accountid":"46dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "@odata.id":"[Organization URI]/api/data/v9.1/contacts(acdbf27c-8efb-e511-80d2-00155db07c77)"
         }
      },
      {  
         "@odata.etag":"W/\"513493\"",
         "name":"Coho Winery (sample)",
         "_primarycontactid_value":"aedbf27c-8efb-e511-80d2-00155db07c77",
         "accountid":"48dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "@odata.id":"[Organization URI]/api/data/v9.1/contacts(aedbf27c-8efb-e511-80d2-00155db07c77)"
         }
      }
   ]
}  
```  

<a bkmk="bkmk_retrieverelatedentityexpandcollectionnavprop"></a>

## <a name="retrieve-related-entities-by-expanding-collection-valued-navigation-properties"></a>Abrufen verwandter Entitäten durch Erweitern von sammlungsbewerteten Navigationseigenschaften

Wenn Sie die sammlungsbewerteten Navigationsparameter erweitern, um verwandte Objekte für Entity-Sets abzurufen, wird eine `@odata.nextLink`-Eigenschaft für die verwandten Objekte zurückgegeben. Sie sollten den Wert der `@odata.nextLink`-Eigenschaft mit einer neuen `GET`-Anforderung nutzen, um die benötigten Daten zurückzugeben.  

Im folgenden Beispiel werden die Aufgaben zurückgegeben, die den Ersten 5 Firmendatensätzen zugewiesen werden.  
  
**Anforderung**

```http 
GET [Organization URI]/api/data/v9.1/accounts?$top=5&$select=name&$expand=Account_Tasks($select%20=%20subject,%20scheduledstart) HTTP/1.1  
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
   "@odata.context":"[Organization URI]/api/data/v9.1/$metadata#accounts(name,Account_Tasks,Account_Tasks(subject,scheduledstart))",
   "value":[  
      {  
         "@odata.etag":"W/\"513475\"",
         "name":"Fourth Coffee (sample)",
         "accountid":"36dbf27c-8efb-e511-80d2-00155db07c77",
         "Account_Tasks":[  

         ],
         "Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.1/accounts(36dbf27c-8efb-e511-80d2-00155db07c77)/Account_Tasks?$select%20=%20subject,%20scheduledstart"
      },
      {  
         "@odata.etag":"W/\"513477\"",
         "name":"Litware, Inc. (sample)",
         "accountid":"38dbf27c-8efb-e511-80d2-00155db07c77",
         "Account_Tasks":[  

         ],
         "Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.1/accounts(38dbf27c-8efb-e511-80d2-00155db07c77)/Account_Tasks?$select%20=%20subject,%20scheduledstart"
      },
      {  
         "@odata.etag":"W/\"514074\"",
         "name":"Adventure Works (sample)",
         "accountid":"3adbf27c-8efb-e511-80d2-00155db07c77",
         "Account_Tasks":[  

         ],
         "Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.1/accounts(3adbf27c-8efb-e511-80d2-00155db07c77)/Account_Tasks?$select%20=%20subject,%20scheduledstart"
      },
      {  
         "@odata.etag":"W/\"513481\"",
         "name":"Fabrikam, Inc. (sample)",
         "accountid":"3cdbf27c-8efb-e511-80d2-00155db07c77",
         "Account_Tasks":[  

         ],
         "Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.1/accounts(3cdbf27c-8efb-e511-80d2-00155db07c77)/Account_Tasks?$select%20=%20subject,%20scheduledstart"
      },
      {  
         "@odata.etag":"W/\"514057\"",
         "name":"Blue Yonder Airlines (sample)",
         "accountid":"3edbf27c-8efb-e511-80d2-00155db07c77",
         "Account_Tasks":[  

         ],
         "Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.1/accounts(3edbf27c-8efb-e511-80d2-00155db07c77)/Account_Tasks?$select%20=%20subject,%20scheduledstart"
          }
       ]
    }
 
```  

<a bkmk="bkmk_retrieverelatedentitysingleandcollectionnavprop"></a>
  
## <a name="retrieve-related-entities-by-expanding-both-single-valued-and-collection-valued-navigation-properties"></a>Abrufen verwandter Einheiten durch Erweitern sowohl von Single-Value- als auch von Collection-Value-Navigationseigenschaften

Das folgende Beispiel zeigt, wie Sie verknüpfte Entitäten für Entity-Sets mit Hilfe von ein- und sammlungsbewerteten Navigationseigenschaften erweitern können. Wie zuvor erklärt, gibt die Erweiterung auf sammlungswertige Navigationseigenschaften, um verbundene Entitäten für Entitätssätze zurückzugeben eine `@odata.nextLink`-Eigenschaft für die verbundenen Entitäten zurück. Sie sollten den Wert der `@odata.nextLink`-Eigenschaft mit einer neuen `GET`-Anforderung nutzen, um die benötigten Daten zurückzugeben.  
  
In diesem Beispiel rufen wir den Kontakt und die Aufgaben ab, die den ersten 3 Firmen zugewiesen werden.  
  
**Anforderung**

```http 
GET [Organization URI]/api/data/v9.1/accounts?$top=3&$select=name&$expand=primarycontactid($select=contactid,fullname),Account_Tasks($select=subject,scheduledstart)  HTTP/1.1  
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
   "@odata.context":"[Organization URI]/api/data/v9.1/$metadata#accounts(name,primarycontactid,Account_Tasks,primarycontactid(contactid,fullname),Account_Tasks(subject,scheduledstart))",
   "value":[  
      {  
         "@odata.etag":"W/\"550614\"",
         "name":"Fourth Coffee (sample)",
         "accountid":"5b9648c3-68f7-e511-80d3-00155db53318",
         "primarycontactid":{  
            "contactid":"c19648c3-68f7-e511-80d3-00155db53318",
            "fullname":"Yvonne McKay (sample)"
         },
         "Account_Tasks":[  

         ],
         "Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.1/accounts(5b9648c3-68f7-e511-80d3-00155db53318)/Account_Tasks?$select=subject,scheduledstart"
      },
      {  
         "@odata.etag":"W/\"550615\"",
         "name":"Litware, Inc. (sample)",
         "accountid":"5d9648c3-68f7-e511-80d3-00155db53318",
         "primarycontactid":{  
            "contactid":"c39648c3-68f7-e511-80d3-00155db53318",
            "fullname":"Susanna Stubberod (sample)"
         },
         "Account_Tasks":[  

         ],
         "Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.1/accounts(5d9648c3-68f7-e511-80d3-00155db53318)/Account_Tasks?$select=subject,scheduledstart"
      },
      {  
         "@odata.etag":"W/\"550616\"",
         "name":"Adventure Works (sample)",
         "accountid":"5f9648c3-68f7-e511-80d3-00155db53318",
         "primarycontactid":{  
            "contactid":"c59648c3-68f7-e511-80d3-00155db53318",
            "fullname":"Nancy Anderson (sample)"
         },
         "Account_Tasks":[  

         ],
         "Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.1/accounts(5f9648c3-68f7-e511-80d3-00155db53318)/Account_Tasks?$select=subject,scheduledstart"
      }
   ]
}
  
```
## <a name="filter-collection-values-based-on-data-in-related-entities"></a>Sammlungswerte anhand von Daten in verknüpften Entitäten filtern

Die Web-API ermöglicht Ihnen, zwei Lambda-Operatoren zu verwenden, nämlich `any` und `all`, um einen booleschen Ausdruck für eine Sammlung auszuwerten. Weitere Informationen: [Lambda-Operatoren verwenden](query-data-web-api.md#bkmk_LambdaOperators).

## <a name="see-also"></a>Siehe auch

[Abfrage von Daten über die Web-API](query-data-web-api.md)<br />
[Vorgänge mithilfe der Web-API ausführen](perform-operations-web-api.md)<br />
[HTTP-Anforderungen verfassen und Fehler beheben](compose-http-requests-handle-errors.md)<br />
[Erstellen einer Entität mithilfe des Web-API](create-entity-web-api.md)<br />
[Abrufen einer Entität mithilfe des Web-API](retrieve-entity-using-web-api.md)<br />
[Entitäten aktualisieren und löschen mithilfe der Web API](update-delete-entities-using-web-api.md)<br />
[Entitäten zuordnen und Zuordnungen aufheben mithilfe der Web API](associate-disassociate-entities-using-web-api.md)
