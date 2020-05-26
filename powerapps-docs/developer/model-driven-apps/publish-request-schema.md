---
title: Veröffentlichen des Anforderungsschemas (modellgestützte Apps) | Microsoft Docs
description: Folgendes ist die Schemadefinition für die PublishXmlRequest-Nachricht.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: f02e62c57724e172398788ed1283a99d62c47b14
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "3275858"
---
# <a name="publish-request-schema"></a>Veröffentlichen des Anforderungsschemas

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/publish-request-schema -->

Folgendes ist die Schemadefinition für die <xref:Microsoft.Crm.Sdk.Messages.PublishXmlRequest>-Nachricht. Weitere Informationen finden Sie unter [Veröffentlichung von Anpassungen](publish-customizations.md). [!INCLUDE[schema_download](../../includes/schema-download.md)].  
  
## <a name="schema"></a>Schema  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema attributeFormDefault="unqualified"  
           elementFormDefault="qualified"  
           xmlns:xs="https://www.w3.org/2001/XMLSchema">  
 <xs:element name="importexportxml">  
  <xs:complexType>  
   <xs:sequence>  
    <xs:element name="entities"  
                minOccurs="0">  
     <xs:complexType>  
      <xs:sequence minOccurs="0"  
                   maxOccurs="unbounded">  
       <!-- Name of the entity to publish-->  
       <xs:element maxOccurs="unbounded"  
                   name="entity"  
                   type="xs:string" />  
      </xs:sequence>  
     </xs:complexType>  
    </xs:element>  
    <xs:element name="ribbons"  
                minOccurs="0">  
     <xs:complexType>  
      <xs:sequence minOccurs="0"  
                   maxOccurs="unbounded">  
       <!-- Application ribbon. : This value is not used. We publish the application ribbon if there is at least one <ribbon> node present -->  
       <xs:element maxOccurs="unbounded"  
                   name="ribbon"  
                   type="xs:string" />  
      </xs:sequence>  
     </xs:complexType>  
    </xs:element>  
    <xs:element name="dashboards"  
                minOccurs="0">  
     <xs:complexType>  
      <xs:sequence minOccurs="0"  
                   maxOccurs="unbounded">  
       <!-- Guid of the systemform to publish-->  
       <xs:element maxOccurs="unbounded"  
                   name="dashboard"  
                   type="xs:string" />  
      </xs:sequence>  
     </xs:complexType>  
    </xs:element>  
    <xs:element name="optionsets"  
                minOccurs="0">  
     <xs:complexType>  
      <xs:sequence minOccurs="0"  
                   maxOccurs="unbounded">  
       <!-- Name of the optionset to publish-->  
       <xs:element maxOccurs="unbounded"  
                   name="optionset"  
                   type="xs:string" />  
      </xs:sequence>  
     </xs:complexType>  
    </xs:element>  
    <xs:element name="sitemaps"  
                minOccurs="0">  
     <xs:complexType>  
      <xs:sequence minOccurs="0"  
                   maxOccurs="unbounded">  
       <!-- Guid of the sitemap to publish : This value is not used. We publish the sitemap if there is at least one <sitemap> node present-->  
       <xs:element maxOccurs="unbounded"  
                   name="sitemap"  
                   type="xs:string" />  
      </xs:sequence>  
     </xs:complexType>  
    </xs:element>  
    <xs:element name="webresources"  
                minOccurs="0">  
     <xs:complexType>  
      <xs:sequence minOccurs="0"  
                   maxOccurs="unbounded">  
       <!-- Guid of the web resource to publish -->  
       <xs:element maxOccurs="unbounded"  
                   name="webresource"  
                   type="xs:string" />  
      </xs:sequence>  
     </xs:complexType>  
    </xs:element>  
   </xs:sequence>  
  </xs:complexType>  
 </xs:element>  
</xs:schema>  
  
```  
  
### <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.Crm.Sdk.Messages.PublishXmlRequest>   
 [Anpassungen veröffentlichen](publish-customizations.md)   
 [Schemata, die in modellbasierten Apps verwendet werden](/dynamics365/customer-engagement/developer/schemas-used-dynamics-365)
