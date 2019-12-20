---
title: Anpassen von Entitäten und Attributzuordnungen in Power Apps (Common Data Service) | Microsoft-Dokumentation
description: Informationen zum Zuordnen von Attributen zwischen Entitäten, die eine Entitätsbeziehung in Power Apps haben. Hiermit können Sie Standardwerte für einen Datensatz festlegen, der im Kontext eines anderen Datensatzes erstellt wird.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 123cc7c11659c04d805a5d34abd49b2aa60aca6e
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2861791"
---
# <a name="customize-entity-and-attribute-mappings"></a>Anpassen von Entitäts- und Attributzuordnungen

Sie können Attributen zwischen Entitäten zuordnen, die eine Entitätsbeziehung haben. Hiermit können Sie Standardwerte für einen Datensatz festlegen, der im Kontext eines anderen Datensatzes erstellt wird. Verwenden Sie die Anpassungstools in der Anwendung, um Attribute zuzuordnen, siehe [Entitätsfelder zuordnen](../../maker/common-data-service/map-entity-fields.md).

<a name="bkmk_BehaviorintheApplication"></a>

## <a name="behavior-in-the-application"></a>Verhaltensweise in der Anwendung

 Durch Zuordnungen in Common Data Service wird die Dateneingabe beim Erstellen neuer Datensätze optimiert, die einem anderen Datensatz zugeordnet sind. Wenn eine Entität eine Entitätsbeziehung mit einer anderen Entität aufweist, können Sie verknüpfte Entitätsdatensätze erstellen, indem Sie die **Verknüpfte erstellen**-Registerkarte auf dem Menüband verwenden. Wenn Sie in dieser Weise einen neuen Datensatz erstellen, werden die zugeordneten Daten aus dem Datensatz der primären Entität in das Formular des Datensatzes der neuen zugeordneten Entität kopiert. Durch due Zuordnung von Entitätsattributen steuern Sie, welche Daten kopiert werden, indem Sie der Beziehung zwischen den beiden Entitäten neue Zuordnungen hinzufügen. Wenn ein Datensatz auf andere Weise als über die zugeordnete Ansicht der primären Entität erstellt wird, werden keine Daten zugeordnet.  

 Beispielsweise können Sie eine Zuordnung zwischen den Adressfeldern in Konten und den Adressfeldern in Kontakten einrichten. Mit dieser Zuordnung gilt: Wenn ein Benutzer einen Kontakt hinzufügt, der einem bestimmten Konto zugeordnet ist, werden die Adressfelder für den Kontakt automatisch ausgefüllt.  

 Ein Attribut kann mehreren Zielattributen zugeordnet werden. Beispielsweise können Sie die Adressinformationen eines Kontos sowohl der Rechnungs- als auch der Lieferadresse in einem Auftrag zuordnen.  

 Die Zuordnung geschieht, bevor ein neuer, verwandter Datensatz erstellt wird. Dadurch können die Benutzer vor dem Speichern des Datensatzes Änderungen vornehmen. und spätere Änderungen an den Daten im primären Datensatz werden nicht auf den verknüpften Datensatz angewendet.  

<a name="bkmk_UsingEntityandAttributeMappingData"></a>

## <a name="using-entity-and-attribute-mapping-data"></a>Verwendung von Entitäts- und Attributzuordnungsdaten

### <a name="using-web-api"></a>Verwenden von Web-API

Beim Arbeiten mit der Web-API können Sie <xref href="Microsoft.Dynamics.CRM.InitializeFrom?text=InitializeFrom Function" /> verwenden, um neue Datensätze im Rahmen vorhandener Datensätze zu erstellen, wobei eine Zuordnung zwischen den Entitäten vorhanden ist. 

Die Antwort, die von InitializeFrom-Anforderung empfangen wird, besteht aus zugeordneten Attributen zwischen Quellentität und Zielentität und der GUID des übergeordneten Datensatzes. Die Attributzuordnung zwischen Entitäten, die eine Entitätsbeziehung haben, ist für verschiedene Entitätssätze verschieden und kann angepasst werden, deshalb variieren die Reaktion von der InitializeFrom-Funktionsanforderung für verschiedene Entitäten und Organisationen. Wenn diese Antwort im Text der Erstellungsanforderung an den neuen Datensatz übergeben wird, werden diese Attributwerte im neuen Datensatz repliziert. Die Werte von benutzerdefinierten zugeordneten Attributen werden auch im neuen Datensatz während des Prozesses festgelegt.

> [!NOTE] 
> So bestimmen Sie, ob zwei Entitäten mit der folgenden Web-API-Anforderung zugeordnet werden können:<br/>`GET [Organization URI]/api/data/v9.0/entitymaps?$select=sourceentityname,targetentityname&$orderby=sourceentityname`

Weitere Informationen finden Sie unter [Erstellen eines neuen Entitätsdatensatzes aus einer anderen Entität](webapi/create-entity-web-api.md#create-a-new-entity-record-from-another-entity).

### <a name="using-organization-service"></a>Mit Organisationsservice

 Wenn Sie neue Datensätze im Kontext eines vorhandenen Datensatzes anlegen, wobei eine Zuordnung zwischen den Entitäten vorhanden ist, können Sie die <xref:Microsoft.Crm.Sdk.Messages.InitializeFromRequest>-Meldung verwenden, um einen neuen Datensatz zu definieren, der die Werte enthält, die in der Zuordnung angegeben sind. Anschließend können Sie den <xref:Microsoft.Xrm.Sdk.IOrganizationService> verwenden.
 <xref:Microsoft.Xrm.Sdk.IOrganizationService.Create*>-Methode, um den Datensatz zu speichern. Auf diese Weise werden alle definierten Zuordnungen angewendet.  

 Gültige Entitätszuordnungen werden erstellt, wenn eine Entitätsbeziehung erstellt wird. Verwenden Sie die `entity_map_attribute_maps`-Entitätsbeziehung, um Attributzuordnungen für das von der Entitätszuordnung angegebene Paar von Entitäten abzurufen.  
 Sie können Attributzuordnungsdatensätze erstellen oder aktualisieren. Die folgenden Voraussetzungen müssen für Attributzuordnungen erfüllt sein:  
- Der <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata>-Typ muss übereinstimmen.
- Das Zielfeld darf nicht kürzer sein als das Quellfeld.
- Das Format muss übereinstimmen.
- Das Zielfeld darf nicht in einer anderen Zuordnung verwendet werden.
- Das Quellfeld muss im Entitätsformular sichtbar sein.
- Beim Zielfeld muss es sich um ein Feld handeln, in das der Benutzer Daten eingeben kann.
- Adresskennungswerte können nicht zugeordnet werden.
- PartyList-Attribute, wo <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.AttributeType> ist <xref:Microsoft.Xrm.Sdk.Metadata.AttributeTypeCode>.PartyList kann nicht zugeordnet werden.

<a name="bkmk_Automapping"></a>

## <a name="auto-mapping-attributes-between-entities"></a>Attribute der automatischen Zuordnung zwischen Entitäten

 Sie können Attributzuordnungen zwischen Entitäten für Entitätsbeziehungen bearbeiten, die die Zuordnung unterstützen. 

 Zusätzlich zur manuellen Erstellung der einzelnen Attributzuordnungen können Sie mit der `AutoMapEntity`-Meldung (<xref href="Microsoft.Dynamics.CRM.AutoMapEntity?text=AutoMapEntity Action" /> oder <xref:Microsoft.Crm.Sdk.Messages.AutoMapEntityRequest>-Klasse) einen neuen Satz von Attributzuordnungen erstellen. Diese Meldung führt die Aktion aus, die unter der Menüoption **Zuordng. generieren** im Menü **Weitere Aktionen** auf der Symbolleiste zu finden ist (siehe [Automatisches Generieren von Feldzuordnungen](../../maker/common-data-service/map-entity-fields.md#automatically-generate-field-mappings)). Dieses Meldung ordnet alle Attribute zwischen den beiden verknüpften Entitäten zu, bei denen die Attributnamen und die Typen identisch sind. Diese Meldung wird als Produktivitätserweiterung bereitgestellt, so dass Sie nicht alle Attributzuordnungen manuell hinzufügen müssen. Stattdessen können Sie einen Satz wahrscheinlicher Zuordnungen generieren und die manuelle Arbeit für das Hinzufügen oder Entfernen einzelner Zuordnungen je nach Ihren Anforderungen minimieren. 

> [!NOTE]
> Die automatische Erstellung von Zuordnungen auf diese Weise entfernt alle vorher definierten Attributzuordnungen und kann Zuordnungen beinhalten, die Sie nicht wünschen.  

<a name="BKMK_mapping"></a>

## <a name="retrieve-the-entity-and-attribute-mappings"></a>Abrufen von Entitäts- und Attributzuordnungen

 Eine einfache Möglichkeit, die Zuordnungen zu finden, die erstellt wurden, ist es, die folgende FetchXML-Abfrage zu verwenden. Weitere Informationen dazu, wie diese Abfrage ausgeführt wird, siehe [Verwendung von FetchXML zum Abfragen von Daten](use-fetchxml-construct-query.md).

```xml

<fetch version='1.0' mapping='logical' distinct='false'>
   <entity name='entitymap'>
      <attribute name='sourceentityname'/>
      <attribute name='targetentityname'/>
      <link-entity name='attributemap' alias='attributemap' to='entitymapid' from='entitymapid' link-type='inner'>
         <attribute name='sourceattributename'/>
         <attribute name='targetattributename'/>
      </link-entity>
   </entity>
 </fetch>
```

### <a name="see-also"></a>Siehe auch

 [Entitätsfelder zuordnen](../../maker/common-data-service/map-entity-fields.md)