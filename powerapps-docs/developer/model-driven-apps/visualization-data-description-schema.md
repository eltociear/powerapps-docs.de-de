---
title: Visualisierungsdaten-Beschreibungsschema (modellgesteuerte Apps) | Microsoft Docs
description: Im Folgenden finden Sie das Schema für die Datenbeschreibung-XML-Zeichenfolge für Diagramme in der Visualisierung. Dieses kann verwendet werden, um den Inhalt der Datenbeschreibung-XML-Zeichenfolge zu validieren, während ein Diagramm erstellt wird.
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
ms.openlocfilehash: 48bc0b00dbb5a2a75cb8bf5f87ca912db83e48f7
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753394"
---
# <a name="visualization-data-description-schema"></a>Visualisierungsdaten-Beschreibungsschema

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/visualization-data-description-schema -->

Im Folgenden finden Sie das Schema für die Datenbeschreibung-XML-Zeichenfolge für Diagramme in der Visualisierung. Dieses kann verwendet werden, um den Inhalt der Datenbeschreibung-XML-Zeichenfolge zu validieren, während ein Diagramm erstellt wird. Weitere Informationen finden Sie unter [Diagramme: Zugrunde liegende Daten und Diagrammpräsentation](understand-charts-underlying-data-chart-representation.md). [!INCLUDE[schema_download](../../includes/schema-download.md)] und sehen Sie die Datei `VisualizationDataDescription.xsd` im Ordner.  
  
## <a name="schema"></a>Schema  
  
```xml  
<?xml version='1.0' encoding='utf-8'?>  
<xs:schema attributeFormDefault='unqualified'  
           elementFormDefault='qualified'  
           xmlns:xs='https://www.w3.org/2001/XMLSchema'>  
 <xs:element name='datadefinition'>  
  <xs:complexType>  
   <xs:sequence>  
    <xs:element name='fetchcollection'>  
     <xs:complexType>  
      <xs:sequence>  
       <xs:element maxOccurs='unbounded'  
                   name='fetch'>  
        <xs:annotation>  
         <!--FetchXML goes here-->  
        </xs:annotation>  
       </xs:element>  
      </xs:sequence>  
     </xs:complexType>  
    </xs:element>  
    <xs:element name='categorycollection'>  
     <xs:complexType>  
      <xs:sequence>  
       <xs:element name='category'  
                   type='CategoryType'  
                   minOccurs='1'  
                   maxOccurs='unbounded' />  
      </xs:sequence>  
     </xs:complexType>  
    </xs:element>  
   </xs:sequence>  
  </xs:complexType>  
 </xs:element>  
 <xs:complexType name ='CategoryType'>  
  <xs:sequence>  
   <xs:element minOccurs='1'  
               maxOccurs='unbounded'  
               name='measurecollection'>  
    <xs:complexType>  
     <xs:sequence>  
      <xs:element minOccurs='1'  
                  maxOccurs='unbounded'  
                  name='measure'>  
       <xs:complexType>  
        <xs:attribute name='alias'  
                      type='xs:string'  
                      use='required' />  
       </xs:complexType>  
      </xs:element>  
     </xs:sequence>  
    </xs:complexType>  
   </xs:element>  
  </xs:sequence>  
  <xs:attribute name='alias'  
                type='xs:string'  
                use='optional' />  
 </xs:complexType>  
</xs:schema>  
```  
### <a name="see-also"></a>Siehe auch  
 [Anpassen von Visualisierungen und Dashboards](customize-visualizations-dashboards.md)   
 [Diagramme verstehen: Zugrunde liegende Daten und Diagrammdarstellung](understand-charts-underlying-data-chart-representation.md)   
 [Beispieldiagramme](sample-charts.md)   
 [Verwenden von FetchXML zum Erstellen einerAbfrage](../common-data-service/use-fetchxml-construct-query.md)