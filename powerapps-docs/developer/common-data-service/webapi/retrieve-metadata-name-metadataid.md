---
title: Abrufen von Metadaten über den Namen oder die MetadataId (Common Data Service) | Microsoft-Dokumentation
description: Common Data Service verwendet eine durch Metadaten gesteuerte Architektur, um die Flexibilität bereitzustellen, benutzerdefinierte Entitäten und zusätzliche Systementitätsattribute zu erstellen.
ms.custom: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 80bcdd8e-7c4f-4fd5-8708-00345f5d0408
caps.latest.revision: 8
author: JimDaly
ms.author: jdaly
ms.reviewer: susikka
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: f56f825b426843b5e3c1ad9747ac060d84100ae0
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748349"
---
# <a name="retrieve-metadata-by-name-or-metadataid"></a>Abrufen von Metadaten über den Namen oder die MetadataId

Ihre Anwendungen können durch Abrufen von Metadaten an Konfigurationsänderungen anpassen. Wenn Sie eine der Schlüsseleigenschaften eines Metadatenelements kennen, können Sie Metadatendefinitionen mit der Web-API abrufen.  

<a name="bkmk_byName"></a>

## <a name="retrieve-metadata-items-by-name"></a>Abrufen von Metadatenelemente per Name
  
Alle abrufbaren Metadatenelemente haben einen `MetadataId`-Primärschlüssel, der verwendet werden kann, um einzelne Elemente abzurufen. Für die Metadatentypen, die einen definierten Alternativschlüssel haben, können Sie ihn per Name abrufen.  
  
Elemente per Name abzurufen ist im Allgemeinen einfacher, da Sie wahrscheinlich bereits einen Verweis auf den Metadatenelementnamen in Ihrem Code haben. Die folgende Tabelle enthält die Alternativschlüsseleigenschaften für das Abrufen von Metadatenelementen per Name  
  
|Metadatenelement|Alternativschlüssel|Beispiel|  
|-------------------|-------------------|-------------|  
|Entität|LogicalName|`GET /api/data/v9.0/EntityDefinitions(LogicalName='account')`|  
|Attribut|LogicalName|`GET /api/data/v9.0/EntityDefinitions(LogicalName='account')/Attributes(LogicalName='emailaddress1')`|  
|Beziehung|SchemaName|`GET /api/data/v9.0/RelationshipDefinitions(SchemaName='Account_Tasks')`|  
|Globaler Opstionssatz|Name|`GET /api/data/v9.0/GlobalOptionSetDefinitions(Name='metric_goaltype')`|  
  
<a name="bkmk_exampleByName"></a>

### <a name="example-retrieve-metadata-items-by-name"></a>Beispiel: Abrufen von Metadatenelemente per Name

Ein allgemeines Element von Metadaten das häufig abgerufen wird, sind die Optionen, die für ein bestimmtes Attribut konfiguriert werden. Im folgenden Beispiel wird gezeigt, wie die `OptionSet`- und `GlobalOptionSet`-Eigenschaften von <xref href="Microsoft.Dynamics.CRM.PicklistAttributeMetadata?text=PicklistAttributeMetadata EntityType" /> abgerufen werden.  
  
> [!NOTE]
>  Beim Erweitern der `OptionSet`- und `GlobalOptionSet`-Einzelwert-Navigationseigenschaften von <xref href="Microsoft.Dynamics.CRM.PicklistAttributeMetadata?text=PicklistAttributeMetadata EntityType" /> können Sie die Optionsdefinition abrufen ob ein Attribut konfiguriert ist, um globale Optionsets oder das "lokale" Optionset der Entität zu verwenden. Wenn es sich um ein "lokales" Optionset handelt, entspricht die `GlobalOptionSet`-Eigenschaft dem Wert Null.  
>   
>  Wenn das Attribut ein globales Optionset verwendete, würde die `GlobalOptionSet`-Eigenschaft die definierten Optionen enthalten und die `OptionSet`-Eigenschaft wäre Null.  
  
 **Anforderung**  

```http  
GET [Organization URI]/api/data/v9.0/EntityDefinitions(LogicalName='account')/Attributes(LogicalName='accountcategorycode')/Microsoft.Dynamics.CRM.PicklistAttributeMetadata?$select=LogicalName&$expand=OptionSet($select=Options),GlobalOptionSet($select=Options) HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
```  
  
 **Antwort**  

```http   
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
  
{  
    "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#EntityDefinitions('account')/Attributes/Microsoft.Dynamics.CRM.PicklistAttributeMetadata(LogicalName,OptionSet,GlobalOptionSet,OptionSet(Options),GlobalOptionSet(Options))/$entity",  
    "LogicalName": "accountcategorycode",  
    "MetadataId": "118771ca-6fb9-4f60-8fd4-99b6124b63ad",  
    "OptionSet@odata.context": "[Organization URI]/api/data/v9.0/$metadata#EntityDefinitions('account')/Attributes(118771ca-6fb9-4f60-8fd4-99b6124b63ad)/Microsoft.Dynamics.CRM.PicklistAttributeMetadata/OptionSet(Options)/$entity",  
    "OptionSet": {  
        "Options": [{  
            "Value": 1,  
            "Label": {  
                "LocalizedLabels": [{  
                    "Label": "Preferred Customer",  
                    "LanguageCode": 1033,  
                    "IsManaged": true,  
                    "MetadataId": "0bd8a218-2341-db11-898a-0007e9e17ebd",  
                    "HasChanged": null  
                }],  
                "UserLocalizedLabel": {  
                    "Label": "Preferred Customer",  
                    "LanguageCode": 1033,  
                    "IsManaged": true,  
                    "MetadataId": "0bd8a218-2341-db11-898a-0007e9e17ebd",  
                    "HasChanged": null  
                }  
            },  
            "Description": {  
                "LocalizedLabels": [  
  
                ],  
                "UserLocalizedLabel": null  
            },  
            "Color": null,  
            "IsManaged": true,  
            "MetadataId": null,  
            "HasChanged": null  
        }, {  
            "Value": 2,  
            "Label": {  
                "LocalizedLabels": [{  
                    "Label": "Standard",  
                    "LanguageCode": 1033,  
                    "IsManaged": true,  
                    "MetadataId": "0dd8a218-2341-db11-898a-0007e9e17ebd",  
                    "HasChanged": null  
                }],  
                "UserLocalizedLabel": {  
                    "Label": "Standard",  
                    "LanguageCode": 1033,  
                    "IsManaged": true,  
                    "MetadataId": "0dd8a218-2341-db11-898a-0007e9e17ebd",  
                    "HasChanged": null  
                }  
            },  
            "Description": {  
                "LocalizedLabels": [  
  
                ],  
                "UserLocalizedLabel": null  
            },  
            "Color": null,  
            "IsManaged": true,  
            "MetadataId": null,  
            "HasChanged": null  
        }],  
        "MetadataId": "b994cdd8-5ce9-4ab9-bdd3-8888ebdb0407"  
    },  
    "GlobalOptionSet": null  
}  
```  
  
<a name="bkmk_byMetadataId"></a>
   
## <a name="retrieve-metadata-items-by-metadataid"></a>Abrufen von Metadatenelemente über MetadataId

Da der `MetadataId` der Primärschlüssel für Metadatenelemente ist, folgt das Abrufen einzelner Elemente demselben Muster, das verwendet wird, um Unternehmensdatenentitäten abzurufen.  
  
|Metadatenelement|Beispiel|  
|-------------------|-------------|  
|Entität|`GET /api/data/v9.0/EntityDefinitions(<Entity MetadataId>)`|  
|Attribut|`GET /api/data/v9.0/EntityDefinitions(<Entity MetadataId>)/Attributes(<Attribute MetadataId>)`|  
|Beziehung|`GET /api/data/v9.0/RelationshipDefinitions(<Relationship MetadataId>)`|  
|Globaler Opstionssatz|`GET /api/data/v9.0/GlobalOptionSetDefinitions(<OptionSet MetadataId>)`|  
  
### <a name="example-retrieve-metadata-items-by-metadataid"></a>Beispiel: Abrufen von Metadatenelemente per MetadataId  

Um das gleiche Ergebnis wie in [Beispiel: Abrufen von Metadatenelemente per Name](#bkmk_exampleByName) zu erhalten, müssen Sie eine Serie von Abfrageoperationen durchführen, um die `MetadataId` durch Filtern nach der Entität `LogicalName` zu erhalten und dann nach Attribut `LogicalName` filtern.  
  
 **Anforderung**

```http  
GET [Organization URI]/api/data/v9.0/EntityDefinitions?$filter=LogicalName%20eq%20'account'&$select=MetadataId HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
```  
  
 **Antwort**

```http  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
  
{  
  "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#EntityDefinitions(MetadataId)","value":[  
    {  
      "MetadataId":"70816501-edb9-4740-a16c-6a5efbc05d84"  
    }  
  ]  
}  
```  
  
 **Anforderung**

```http  
GET [Organization URI]/api/data/v9.0/EntityDefinitions(70816501-edb9-4740-a16c-6a5efbc05d84)/Attributes?$filter=LogicalName%20eq%20'accountcategorycode'&$select=MetadataId HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
```  
  
 **Antwort**

```http  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
  
{  
    "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#EntityDefinitions(70816501-edb9-4740-a16c-6a5efbc05d84)/Attributes(MetadataId)","value":[  
    {  
        "@odata.type": "#Microsoft.Dynamics.CRM.PicklistAttributeMetadata",  
        "MetadataId": "118771ca-6fb9-4f60-8fd4-99b6124b63ad"  
    }  
    ]  
}  
```  
  
 **Anforderung**

```http  
GET [Organization URI]/api/data/v9.0/EntityDefinitions(70816501-edb9-4740-a16c-6a5efbc05d84)/Attributes(118771ca-6fb9-4f60-8fd4-99b6124b63ad)/Microsoft.Dynamics.CRM.PicklistAttributeMetadata?$select=LogicalName&$expand=OptionSet($select=Options),GlobalOptionSet($select=Options) HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
```  
  
 **Antwort**

```http
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
  
{  
    "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#EntityDefinitions(70816501-edb9-4740-a16c-6a5efbc05d84)/Attributes/Microsoft.Dynamics.CRM.PicklistAttributeMetadata(LogicalName,OptionSet,GlobalOptionSet,OptionSet(Options),GlobalOptionSet(Options))/$entity",  
    "LogicalName": "accountcategorycode",  
    "MetadataId": "118771ca-6fb9-4f60-8fd4-99b6124b63ad",  
    "OptionSet@odata.context": "[Organization URI]/api/data/v9.0/$metadata#EntityDefinitions(70816501-edb9-4740-a16c-6a5efbc05d84)/Attributes(118771ca-6fb9-4f60-8fd4-99b6124b63ad)/Microsoft.Dynamics.CRM.PicklistAttributeMetadata/OptionSet(Options)/$entity",  
    "OptionSet": {  
        "Options": [{  
            "Value": 1,  
            "Label": {  
                "LocalizedLabels": [{  
                    "Label": "Preferred Customer",  
                    "LanguageCode": 1033,  
                    "IsManaged": true,  
                    "MetadataId": "0bd8a218-2341-db11-898a-0007e9e17ebd",  
                    "HasChanged": null  
                }],  
                "UserLocalizedLabel": {  
                    "Label": "Preferred Customer",  
                    "LanguageCode": 1033,  
                    "IsManaged": true,  
                    "MetadataId": "0bd8a218-2341-db11-898a-0007e9e17ebd",  
                    "HasChanged": null  
                }  
            },  
            "Description": {  
                "LocalizedLabels": [  
  
                ],  
                "UserLocalizedLabel": null  
            },  
            "Color": null,  
            "IsManaged": true,  
            "MetadataId": null,  
            "HasChanged": null  
        }, {  
            "Value": 2,  
            "Label": {  
                "LocalizedLabels": [{  
                    "Label": "Standard",  
                    "LanguageCode": 1033,  
                    "IsManaged": true,  
                    "MetadataId": "0dd8a218-2341-db11-898a-0007e9e17ebd",  
                    "HasChanged": null  
                }],  
                "UserLocalizedLabel": {  
                    "Label": "Standard",  
                    "LanguageCode": 1033,  
                    "IsManaged": true,  
                    "MetadataId": "0dd8a218-2341-db11-898a-0007e9e17ebd",  
                    "HasChanged": null  
                }  
            },  
            "Description": {  
                "LocalizedLabels": [  
  
                ],  
                "UserLocalizedLabel": null  
            },  
            "Color": null,  
            "IsManaged": true,  
            "MetadataId": null,  
            "HasChanged": null  
        }],  
        "MetadataId": "b994cdd8-5ce9-4ab9-bdd3-8888ebdb0407"  
    },  
    "GlobalOptionSet": null  
}  
```  
  
### <a name="see-also"></a>Siehe auch

[Verwenden der Web-API mit Common Data Service-Metadaten](use-web-api-metadata.md)<br />
[Metadaten mit Web-API abfragen](query-metadata-web-api.md)<br />
[Erstellen und Aktualisieren von Entitätsdefinitionen mit der Web-API](create-update-entity-definitions-using-web-api.md)<br /> 
[Erstellen und Aktualisieren von Entitätsbeziehungen mit der Web-API](create-update-entity-relationships-using-web-api.md)
