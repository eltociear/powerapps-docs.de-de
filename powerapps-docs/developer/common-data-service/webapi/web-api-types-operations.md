---
title: Web-API-Typen und -vorgänge (Common Data Service) | Microsoft Docs
description: 'Dieses Thema beschreibt, was für Sie verfügbar ist, um die Web-API vis-a-vis zu verwenden. Es informiert über wichtige Themen und darüber, wie Sie benötigte Informationen in der Dokumentation finden, die aus Service- und Metadaten-Dokumenten erstellt wurde und aus der Dokumentation zu Systementitätstypen, Funktionen und Aktionen'
ms.custom: ''
ms.date: 02/05/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: d80cfb87-d4f1-4c75-bcc8-4f54d1351e26
caps.latest.revision: 27
author: brandonsimons
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="web-api-types-and-operations"></a>Internet API-Typen und -Vorgänge

Um Web API zu verwenden, müssen Sie Informationen zu dem suchen, was für Sie zur Nutzung verfügbar ist. Der Dienst beschreibt sich über Service- und Metadatendokumente, auf die Sie zugreifen können. Dieses Thema enthält wichtige Konzepte und beschreibt, wie Sie die von Ihnen benötigten Informationen mithilfe von Dokumentationen finden, die aus Service- und Metadatendokumenten sowie der Dokumentation der Systementitätstypen, Funktionen und Aktionen erstellt werden.  
  
<a name="bkmk_terminology"></a>
  
## <a name="terminology"></a>Terminologie 

Der Web API wird mithilfe des ODatas v4 Standards implementiert, der bstimmte Begriffe verwendet, mit denen Sie vertraut sein müssen. *Entity Data Model (EDM)* ist das abstrakte Datenmodell, das verwendet wird, um die Daten zu beschreiben, die von einem OData-Service verfügbar gemacht werden. Die folgende Tabelle enthält eine ausgewählte Terminologieliste definiert in [OData Version 4.0 Teil 1: Protokoll Plus Errata 02](http://docs.oasis-open.org/odata/odata/v4.0/errata02/os/complete/part1-protocol/odata-v4.0-errata02-os-part1-protocol-complete.html), die Sie kennen sollten.  
  
|Begriff|Definition|  
|----------|----------------|  
|*Entitätstypen*|Benannte strukturierte Typen mit einen Schlüssel. Sie definieren die benannten Eigenschaften und Beziehungen einer Entität. Entitätstypen können durch einzelne Vererbung von anderen Entitätstypen abgeleitet werden.|  
|*Entitäten*|Instanzen von Entitätstypen (z. B. Firma, Verkaufschance).|  
|*Entitätssätze*|Benannte Sammlungen von Entitäten (z. B. sind Firmen ein Entitätssatz, der Firmenentitäten enthält). Ein Entitätsschlüssel, der die Entität in einem Entitätssatz eindeutig bezeichnet|  
|*Komplexe Typen*|Schlüssellose benannte strukturierte Typen, die einen Satz von Eigenschaften enthalten. Komplexe Typen werden als Eigenschaftswerte in Modelentitäten oder als Parameter oder Rückgabewerte für Vorgänge verwendet.|  
|*Enumerationstypen* oder *Enumerationstypen*|Primitive Typen, dessen Werte nach Konstanten mit zugrunde liegenden ganzzahligen Werten benannt sind.|  
|*Funktionen*|Vorgänge, die keine Nebenwirkungen aufweisen und weitere Zusammensetzung unterstützen können, beispielsweise zusätzliche Filtervorgänge, Funktionen oder eine Aktion.|  
|*Aktionen*|Vorgänge, die Nebenwirkungen, wie Datenänderung zulassen und nicht weiter zusammengesetzt werden können, um ein nicht deterministisches Verhalten zu vermeiden.|  
  
<a name="bkmk_servicedocs"></a>
  
## <a name="service-documents"></a>Servicedokumente

Es gibt zwei Servicedokumente, auf die Sie verweisen können, um mehr über den Web API zu erfahren.  
  
<a name="bkmk_serviceDocument"></a>

### <a name="service-document"></a>Servicedokument

Die folgende, Abfrage, die in das Adressfeld des Browsers eingegeben wird, gibt das *Service-Dokumenht* zurück, eine vollständige Liste aller Entitätssätze, die für Ihre Organisation verfügbar sind. Beachten Sie, dass *[Organisations-URI]* die URL für Ihre Organisation darstellt.  
  
```  
  
[Organization URI]/api/data/v9.0  
  
```  
  
 Die Entitätssätze werden in Form eines JSON-Arrays zurückgegeben. Jedes Element im Array besteht aus drei aufgelisteten Eigenschaften aufgelistet in diesr Tabelle.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|`name`|Dies ist der Name des Entitätssatzes. Diese Daten sind von der Eigenschaft <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" /> `EntitySetName` für die Entität.|  
|`kind`|Für die WEB API weden nur Entitätssätze aufgelistet.|  
|`url`|Dieser Wert ist identisch mit der Name-Eigenschaft und zeigt den Teil des Ressourcenpfads zum Abrufen von Daten für die Entität.|  
  
 Diese Information kann mithilfe der `GET` Anfrage abgerufen werden und kann hilfreich sein, um eine Liste aller verfügbaren Entitätssätze, die den Service nutzen, abzurufen.  
  
<a name="bkmk_csdl"></a>

### <a name="csdl-metadata-document"></a>CSDL-$Metadatendokument
 
Eine `GET`- Anfrage für die folgende URL gibt ein eher großes (mehr als 3.5 MB) Common Schema Definition Language (CSDL)-Dokument oder ein *Metadatendokument* zurück, das die Daten und den Ablauf des Service darstellt.  
  
```http  
GET [Organization URI]/api/data/v9.0/$metadata  
```  
  
Dieses Dokument kann als Datenquelle verwendet werde, um Klassen zu erstellen, die stark typisierte Objekte für den Service bereitstellen. Aber, wenn Sie keine generierten Klassen verwenden, sollten Sie die Dokumentation, die aus diesen Informationen generiert wurden, überprüfen. Die [Web-API-Referenz](/dynamics365/customer-engagement/web-api/about) nutzt Informationen primär aus diesem Dokument, das von einem System stammt, auf dem allgemeine zusätzliche Lösungen installiert sind.  
  
Sie erfahren mehr über dieses Dokument unter [OData-Version 4.0 Teil 3: Common Schema Definition Language (CSDL) Plus Errata 02](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part3-csdl.html).  
  
> [!TIP]
>  Ehe Sie den Rest des Themas lesen, laden Sie `$metadata` für Ihre Organisation herunter, und sehen Sie sich an, wie die beschriebene Typen, Funktionen und Aktionen in `$metadata` und der unterstützenden Dokumentation enthalten sind.  
>   
>  Sie können das Dokument mithilfe des Browsers anzeigen oder herunterladen, indem Sie zur URL navigieren.  

<a name="bkmk_metannot"></a>

### <a name="metadata-annotations"></a>Metadatenanmerkungen

Das Metadatendokument enthält mehrere Typen von `Annotation`-Elementen, die zusätzliche Informationen zu Metadatenelementen und Funktionen des Service bereitstellen.  Ab v9.x sind diese Anmerkungen nicht im Standardmetadatendokument enthalten, sofern nicht explizit angefordert. Diese Anmerkungen erhöhen die Größe des Metadatendokuments und sind nicht immer erforderlich.  
  
 Zum Einschließen von Anmerkungen sind beim Anfordern des Metadatendokuments zwei Optionen verfügbar:  
  
-   Fügen Sie den `?annotations=true`-Abfragezeichenfolgenparameter an die URL an.  
  
-   Fügen Sie den `Prefer: odata.include-annotations="*"`-Header zur Anforderung hinzu.  
  
Jedes `Annotation`-Element enthält ein `Term`-Attribut, das den Anmerkungstyp beschreibt. Die Definitionen aller möglichen Anmerkungen, die von OData v4-Clients verwendet werden, sind in [OData-Vokabular-Version 4.0](http://docs.oasis-open.org/odata/odata-vocabularies/v4.0/csprd01/odata-vocabularies-v4.0-csprd01.html) enthalten. Die folgende Tabelle enthält einige Beispiele, die von der Web-API verwendet werden.  
  
|Begriff|Beschreibung|  
|----------|-----------------|  
|`Org.OData.Core.V1.Description`|Eine Beschreibung eines entitytype (Entitätstyps) oder einer Eigenschaft.|  
|`Org.OData.Core.V1.Permissions`|Eine Liste von den Berechtigungen, die für eine Eigenschaft verfügbar ist, wenn Berechtigungen eingeschränkt sind.  Normalerweise wird dies für Eigenschaften mit nur einem einzelnen untergeordneten `<EnumMember>Org.OData.Core.V1.PermissionType/Read</EnumMember>`-Element angezeigt, um darauf hinzuweisen, dass die Eigenschaft schreibgeschützt ist.|  
|`Org.OData.Core.V1.Computed`|Ob die Eigenschaft berechnet wird. Diese sind in der Regel auch schreibgeschützt.|  
|`OData.Community.Keys.V1.AlternateKeys`|Enthält eine Sammlung von Elementen, die alle Alternativschlüssel beschreiben, die für eine Entität definiert wurden. Weitere Informationen: [Alternativschlüssel](#bkmk_alternateKeys)|  
|`Org.OData.Capabilities.V1.IndexableByKey`|Ob ein entityset Schlüsselwerte nach OData-URL-Konventionen unterstützt.|  
|`Org.OData.Capabilities.V1.SkipSupported`|Ob ein entityset `$skip` unterstützt.|  
|`Org.OData.Capabilities.V1.SearchRestrictions`|Welche Arten von Einschränkungen auf `$search`-Ausdrücke in einem entityset angewendet werden.|  
|`Org.OData.Capabilities.V1.CountRestrictions`|Welche Arten von Einschränkungen auf `/$count`-Pfadsuffix und $count=true Systemabfrageoption gelten.|  
|`Org.OData.Capabilities.V1.NavigationRestrictions`|Welche Arten von Einschränkungen bei Navigationseigenschaften gemäß OData-URL-Konventionen gelten.|  
|`Org.OData.Capabilities.V1.ChangeTracking`|Die Änderungsnachverfolgungsfunktionen dieses Service oder Entitätssatzes.|  
|`Org.OData.Capabilities.V1.ConformanceLevel`|Die Übereinstimmungsebene, die durch diesen Service erreicht wird.|  
|`Org.OData.Capabilities.V1.FilterFunctions`|Eine Liste von Funktionen und Operatoren, die in `$filter` unterstützt werden.|  
|`Org.OData.Core.V1.DereferenceableIDs`|Ob Entität-IDs URLs sind, die die identifizierte Entität lokalisieren.|  
|`Org.OData.Core.V1.ConventionalIDs`|Ob die Entität-IDs den OData-URL-Konventionen folgen.|  
|`Org.OData.Capabilities.V1.AsynchronousRequestsSupported`|Ob der Service die synchrone Anforderungspräferenz unterstützt.|  
|`Org.OData.Capabilities.V1.BatchContinueOnErrorSupported`|Ob der Service das Fortfahren nach Fehlerpräferenz unterstützt.  Diese Einstellung unterstützt `$batch`-Anforderungen.|  
|`Org.OData.Capabilities.V1.CrossJoinSupported`|Ob Cross-Joins für die Entitätssätze in diesem Container unterstützt werden.|  
|`Org.OData.Capabilities.V1.SupportedFormats`|Die Medientypen unterstützter Formate, einschließlich Formatparameter.|  
  
<a name="bkmk_entityTypes"></a>

## <a name="entity-types"></a>Entitätstypen

<xref:Microsoft.Dynamics.CRM.EntityTypeIndex> führt alle Systementitätstypen auf, die durch die Web API verfügbar sind, die Geschäftsdaten speichert. Ein Entitätstyp ist ein benannter strukturierter Typ von einen Schlüssel. Sie definieren die benannten Eigenschaften und Beziehungen einer Entität. Entitätstypen können durch einzelne Vererbung von anderen Entitätstypen abgeleitet werden. <xref:Microsoft.Dynamics.CRM.MetadataEntityTypeIndex> fürht die Entitätstypen auf, die verwendet werden, um die Systemmetadaten zu verwalten. Beides sind Entuitätstypen, aber die Art, wie Sie mit ihnen arbeiten, ist unterschiedlich. Lesen Sie [Verwenden von Web-API mit "Common Data Service für Apps"-Metadaten](use-web-api-metadata.md), um Informationen zum Verwenden von Modellentitäten zu erhalten. Jeder Entitätstyp ist in einem `EntityType`-Element in den `$metadata` enthalten. Im Folgenden finden Sie die Definition des <xref href="Microsoft.Dynamics.CRM.account?text=account EntityType" /> vom `$metadata` mit entfernten Eigenschaften und Navigationseigenschaften.  
  
```xml  
<EntityType Name="account" BaseType="mscrm.crmbaseentity">  
  <Key>  
    <PropertyRef Name="accountid" />  
  </Key>  
  <!--Properties and navigation properties removed for brevity-->  
  <Annotation Term="Org.OData.Core.V1.Description" String="Business that represents a customer or potential customer. The company that is billed in business transactions." />  
</EntityType>  
```  
  
Jede `EntityType`-Referenzseite in der SDK-Dokumentation verwendet Informationen aus den `$metadata`, um die folgenden Informationen anzuzeigen, falls verfügbar.  
  
|Informationen|Beschreibung|  
|-----------------|-----------------|  
|**Beschreibung**|Eine Beschreibung der Entität.<br /><br /> Die <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" /> `Description`-Eigenschaftsinformation ist im `EntityType`-Element enthalten. Dafür wird das `Annotation`-Element mit dem `Term`-Attributwert von Org.OData.Core.V1.Description verwendet.|  
|**Sammlungs-URL**|Die URL, mit der Sie auf jeden Typ in de Sammlung zugreifen können.<br /><br /> Die <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" /> `EntitySetName`-Eigenschaftsinformation ist über das `$metadata` `EntityContainer`-Element enthalten. Das `Name`-Attribut jedes `EntitySet`-Elements steuert, wie auf die Daten über die URL zugeriffen wird.|  
|**Basistyp**|Hierbei handelt es sich um den Entitätstyp, von dem der Entitätstyp abstimmt.<br /><br /> Das `BaseType`-Attribut vom `EntityType`-Element enthält den Namen des Entitätstyps. Diesem Namen wird der Alias für den Microsoft.Dynamics.CRM namespace: mscrm vorangestellt. Weitere Informationen: [Typvererbung](web-api-types-operations.md#bkmk_typeInheritance)|  
|**Anzeigename**|Diese Informationen sind nicht in den `$metadata` enthalten. Sie werden von der <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" /> `DisplayName`-Eigenschaft abgerufen.|  
|**Primärschlüssel**|Der Eigenschaftswert, die den eindeutigen Bezeichner enthält, der auf eine Instanz einer Entität verweist.<br /><br /> Der <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" /> `PrimaryIdAttribute` Eigenschaftswert ist im `EntityType` `Key`-Element eingeschlossen. Jede Entität kann nur einen Primärschlüssel haben.<br /><br /> Alternativschlüssel sind hier nicht aufgeführt. Weitere Informationen: [Alternativschlüssel](web-api-types-operations.md#bkmk_alternateKeys)|  
|**Primäres Attribut**|Viele Entitäten verlangen, dass ein primärer Attributwert festgelegt wird, deshalb wird dieser hier eingeschlossen.<br /><br /> Diese Informationen sind nicht in den `$metadata` enthalten. Sie werden von der Metadateneigenschaft <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" /> `PrimaryNameAttribute` abgerufen.|  
|**Eigenschaften**|Siehe [Eigenschaften](web-api-types-operations.md#bkmk_properties).|  
|**Einzelwertige Navigationseigenschaften**|Siehe [Einzelwertige Navigationseigenschaften](web-api-types-operations.md#bkmk_singleValuedNavigationProperties).|  
|**Gemeinsam bewertete Navigationseigenschaften**|Siehe [Gemeinsam bewertete Navigationseigenschaften](web-api-types-operations.md#bkmk_collectionvaluedNavProperties).|  
|**An den Entitätstyp gebundene Vorgänge**|Wenn ein Vorgang an einen bestimmten Entitätstyp gebunden ist, ist er der Einfachheit halber aufgelistet.|  
|**Vorgänge, die den Entitätstyp verwenden**|Diese Liste enthält alle Vorgänge, die möglicherweise den Entitätstyp verwenden. Dieser wird berechnet, indem Verweise auf alle Vorgänge abgerufen werden, die sich auf den aktuellen Typ im Parameter beziehen oder als Rückgabewert gelten.|  
|**Entitätstypen, die vom Entitätstyp erben**|Diese Liste beinhaltet sämtliche Entitätstypen, die direkt vom ausgewählten Entitätstyp erben. Siehe [Typvererbung](web-api-types-operations.md#bkmk_typeInheritance) für weitere Informationen.|  
  
<a name="bkmk_changeentitysetname"></a>
 
### <a name="change-the-name-of-an-entity-set"></a>Ändern des Namens eines Entitätssets
 
Standardmäßig entspricht der Entitätssetname dem <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" /> `LogicalCollectionName` (<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>`LogicalCollectionName`) Eigenschaftswert. Wenn Sie eine benutzerdefinierte Entität haben, die Sie mit einem anderen Entitätsnamen ansprechen möchten, können Sie den <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" /> `EntitySetName` (<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.`EntitySetName`) Eigenschaftswert aktualisieren, um einen anderen Entitätsnamen zu verwenden.  
  
<a name="bkmk_alternateKeys"></a>

### <a name="alternate-keys"></a>Alternativschlüssel

Obwohl Common Data Service das Erstellen von Alternativschlüsseln zulässt, kann nur der Primärschlüssel in den Standardentitäten gefunden werden.  
  
 Keine dieser Systementitäten hat definierte Alternativschlüssel. Wenn Sie Alternativschlüssel für eine Entität definieren, werden diese im `$metadata` `EntityType`-Element als eine `Annotation` wie die folgende eingeschlossen:  
  
```  
<Annotation Term="OData.Community.Keys.V1.AlternateKeys">  
  <Collection>  
    <Record Type="OData.Community.Keys.V1.AlternateKey">  
      <PropertyValue Property="Key">  
        <Collection>  
          <Record Type="OData.Community.Keys.V1.PropertyRef">  
            <PropertyValue Property="Alias" String="key name" />  
            <PropertyValue Property="Name" PropertyPath="key name" />  
          </Record>  
        </Collection>  
      </PropertyValue>  
    </Record>  
  </Collection>  
</Annotation>  
```  
  
Informationen zu Alternativschlüsseln können auch aus den Metadaten mithilfe der <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" /> `Keys` sammlungswertigen Navigationseigenschaft mittels Web-API oder der <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.`Keys` Eigenschaften mittels Organisationsdienst abgerufen werden.  
  
<a name="bkmk_typeInheritance"></a>
 
### <a name="type-inheritance"></a>Typvererbung

Vererbung ist das Freigeben von allgemeinen Eigenschaften und die Kategorisieren von Entitätstypen in Gruppen. Alle Entitätstypen im Web API erben von den zwei folgenden Entitätstypen. Alle Geschäftsentitätstypen erben unter <xref href="Microsoft.Dynamics.CRM.crmbaseentity?text=crmbaseentity EntityType" /> und alle Modellentitäten erben von <xref href="Microsoft.Dynamics.CRM.crmmodelbaseentity?text=crmmodelbaseentity EntityType" />  
  
|Basisentität|Beschreibung|  
|-----------------|-----------------|  
|<xref href="Microsoft.Dynamics.CRM.crmbaseentity?text=crmbaseentity EntityType" />|Alle Geschäftsentitäten erben aus dieser Entität. Sie hat keine Eigenschaften. Sie dient nur als abstrakte Basisentität.|  
|<xref href="Microsoft.Dynamics.CRM.activitypointer?text=activitypointer EntityType" />|Alle aktiven Entitäten erben aus dieser Entität. Definieren Sie die allgemein Eigenschafts- und die Navigationseigenschaften für Aktivitätsentitäten.|  
|<xref href="Microsoft.Dynamics.CRM.principal?text=principal EntityType" />|<xref href="Microsoft.Dynamics.CRM.systemuser?text=systemuser EntityType" /> und <xref href="Microsoft.Dynamics.CRM.team?text=team EntityType" /> erben eine gemeinsame ownerid-Eigenschaft von dieser Entität.|  
|<xref href="Microsoft.Dynamics.CRM.crmmodelbaseentity?text=crmmodelbaseentity EntityType" />|Nur <xref href="Microsoft.Dynamics.CRM.MetadataBase?text=MetadataBase EntityType" /> erbt direkt aus dieser Entität. Sie hat keine Eigenschaften. Sie dient nur als abstrakte Basisentität.|  
|<xref href="Microsoft.Dynamics.CRM.MetadataBase?text=MetadataBase EntityType" />)|Alle Metadatenentitäten erben von dieser Entität. Sie stellt `MetadataId`- und `HasChanged`-Eigenschaften für alle Metadatenentitäten zur Verfügung.|  
|<xref href="Microsoft.Dynamics.CRM.AttributeMetadata?text=AttributeMetadata EntityType" />|Alle Modellentitäten, die unterschiedliche Attributtypen darstellen, erben aus dieser Entität.|  
|<xref href="Microsoft.Dynamics.CRM.EnumAttributeMetadata?text=EnumAttributeMetadata EntityType" />|Die Modellentitäten, die Attribute anzeigen, die einen Satz von Optionen aus dieser Entität erben.|  
|<xref href="Microsoft.Dynamics.CRM.OptionSetMetadataBase?text=OptionSetMetadataBase EntityType" />|Dieser Modellentitättyp bietet einen allgemeinen Satz von Eigenschaften, die von den <xref href="Microsoft.Dynamics.CRM.BooleanOptionSetMetadata?text=BooleanOptionSetMetadata EntityType" /> und <xref href="Microsoft.Dynamics.CRM.OptionSetMetadata?text=OptionSetMetadata EntityType" /> Modellentitättypen verwendet werden, die davon erben.|  
|<xref href="Microsoft.Dynamics.CRM.RelationshipMetadataBase?text=RelationshipMetadataBase EntityType" />|Dieser Entitätstyp bietet einen allgemeinen Satz von Eigenschaften, die von den <xref href="Microsoft.Dynamics.CRM.ManyToManyRelationshipMetadata?text=ManyToManyRelationshipMetadata EntityType" /> und <xref href="Microsoft.Dynamics.CRM.OneToManyRelationshipMetadata?text=OneToManyRelationshipMetadata EntityType" /> Modellentitättypen verwendet werden, die davon erben.|  
  
<a name="bkmk_properties"></a>
 
## <a name="properties"></a>Eigenschaften

Jeder Entitätstpy kann Eigenschaften haben, die den Attributen entsprechen. Im <xref:Microsoft.Dynamics.CRM.EntityTypeIndex> und <xref:Microsoft.Dynamics.CRM.MetadataEntityTypeIndex> Inhalt werden Eigenschaften, die von einem Basisentitätstyp vererbt werden, in der Liste der deklarierten Eigenschaften für jeden Entitätstyp kombiniert. Die Vererbung wird in der Beschreibung für jede ausgerufen Eigenschaft definiert.  
  
In den `$metadata` `EntityType`-Elementen ist jede Eigenschaft im `Property`-Element mit einem `Name`-Attributwert enthalten, der den Eigenschaften entspricht, die Sie im Code festlegen werden. Der `Type` Attributwert definiert den Datentyp der Eoigenschaft. Eigenschaften für Geschäftsentitätstypen verwenden im Allgemeinen primitive OData-Typen.  
  
Nachfolgend finden Sie ein Beispiel der <xref href="Microsoft.Dynamics.CRM.account?text=account EntityType" /> `name`-Eigenschaft, die in den `$metadata` definiert ist.  
  
```  
<Property Name="name" Type="Edm.String" Unicode="false">  
  <Annotation Term="Org.OData.Core.V1.Description" String="Type the company or business name." />  
</Property>  
```  
  
Die Beschreibung der Eigenschaft ist in einem `Annotation`-Element mit der `Term`-Attributeigenschaft von Org.OData.Core.V1.Description enthalten. Diese Beschreibung stammt vom Eigenschaftswert <xref href="Microsoft.Dynamics.CRM.AttributeMetadata?text=AttributeMetadata EntityType" /> `Description`. Nicht alle aufgelisteten Eigenschaften haben eine Beschreibung.  
  
Jede Eigenschaft kann berechnet werden. Das bedeutet, dass der Wert möglicherweise vom System festgelegt ist. Dies ist im `Annotation`-Element mit dem `Term`-Attributwert von Org.OData.Core.V1.Computed angegeben.  
  
Jede Eigenschaft kann auch Beschränkungen haben, ob sie aktualisiert wird. Dies ist im `Annotation`-Element mit einem `Term`-Attributwert von Org.OData.Core.V1.Permissions definiert. Der einzige Optionssatz dafür ist Org.OData.Core.V1.PermissionType/Read, der angibt, dass die Eigenschaft schreibgeschützt ist.  
  
<a name="bkmk_primitives"></a>

### <a name="primitive-types"></a>Primitive Typen
 
OData unterstützt eine Vielzahl von Datentypen, aber Common Data Service verwendet nicht alle davon. Die folgende Tabelle beschreibt, wie Common Data Service-Organisationsservicetypen primitiven OData-Typen zugeordnet werden.  
  
|Organisationsservicetype|Web API Typ|Beschreibung|  
|-------------------------------|------------------|-----------------|  
|BigInt|Edm.Int64|64-Bit-Ganzzahl|  
|Boolean|Boolesch|Binärdbewertete Logik|  
|CalendarRules|Einzelwertige Navigationseigenschaften|Bestimmte einzelwertige Navigationseigenschaften zu <xref href="Microsoft.Dynamics.CRM.calendarrule?text=calendarrule EntityType" />.|  
|Kunde|Einzelwertige Navigationseigenschaften|Der Kunde einer Entität mit dem Typ der Eigenschaft kann eine einzelwertige Navigationseigenschaft sein, die entweder mithilfe der entsprechenden einzelwertigen Navigationseigenschaften auf einen Firma- oder Kontakt-Entitätstyp gesetzt ist. Wenn eine der einzelwertigen entsprechenden Sammlungseigenschaften festgelegt ist, wird die andere gelöscht.|  
|DateTime|Edm.DateTimeOffset|Datum und Uhrzeit in einem Zeitzonenoffset, keine Schaltsekunden <br />Es gibt keinen DateTime-Typen in OData.|  
|Dezimal|Edm.Decimal|Numerische Werte mit fester Genauigkeit und Skala|  
|Double|Edm.Double|IEEE 754 binary64 Gleitkommazahl (15-17 Dezimalstellen)|  
|EntityName|Edm.String|Reihenfolge von UTF-8-Zeichen|  
|Bild|Edm.Binary|Binärdaten|  
|Integer|Edm.Int32|32-Bit-Ganzzahl|  
|Suche|einzelwertige Navigationseigenschaften|Ein Verweis auf eine bestimmte Entität|  
|ManagedProperty|Nicht verfügbar|Nur zur internen Verwendung|  
|Memo|Edm.String|Reihenfolge von UTF-8-Zeichen|  
|Zahlung|Edm.Decimal|Numerische Werte mit fester Genauigkeit und Skala|  
|Eigentümer|einzelwertige Navigationseigenschaften|Ein Verweis auf <xref href="Microsoft.Dynamics.CRM.principal?text=principal EntityType" />. Systemuser- und Team-Entitättypen erben ihre ownerid-Eigenschaft vom prinzipalen Entitätstyp.|  
|Bei Auswahllistenattributen ist keine Texteingabe möglich.|Edm.Int32|32-Bit-Ganzzahl|  
|Status|Edm.Int32|32-Bit-Ganzzahl|  
|Status|Edm.Int32|32-Bit-Ganzzahl|  
|String|Edm.String|Reihenfolge von UTF-8-Zeichen|  
|Uniqueidentifier|Edm.Guid|eindeutiger Bezeichner des 16-Bytes (128-Bit)|  

<!-- TODO:
|PartyList|Collection-valued navigation property to the `activityparty` entity type.|The activitypartyparticipationtypemask property contains a value to represent the role of the participant. See [Activity Party Types](../activityparty-entity.md#ActivityPartyTypes) for more information.|   -->

<a name="bkmk_lookupProperties"></a>
 
### <a name="lookup-properties"></a>Such-Eigenschaften

Für die meisten einzelwertigen Navigationseigenschaften finden Sie eine berechnete, schreibgeschützte Eigenschaft, die die folgende Namenskonvention verwendet: `_<name>_value` wo `<name>` dem Namen der einzelwertigen Navigationseigenschaft entspricht. Ausnahmen zu diesem Muster bildet ein Suchattribut einer Entität, das mehrere Typen von Entitätsverweisen annehmen kann. Ein allgemeines Beispiel dafür ist das `incident` `customerid` Entitätsattribut, das als Referenz gesetzt werden kann und entweder eine `contact` oder `account` Entität ist. Unter <xref href="Microsoft.Dynamics.CRM.incident?text=incident EntityType" /> [Einzelwertige Navigationseigenschaften](/dynamics365/customer-engagement/web-api/incident?view=dynamics-ce-odata-9#Single-valued_navigation_properties) finden Sie `customerid_account` und `customerid_contact` als separate einzelwertige Navigationseigenschaften, um den Kunden widerzuspiegeln, der der Verkaufschance zugeordnet ist. Wenn diese einzelwertige Navigationseigenschaften festgelegt ist, wird die andere auf Null gesetzt, weil sie an das `customerid`-Attribut gebunden sind. Unter den [<xref href="Microsoft.Dynamics.CRM.incident?text=incident EntityType" /> [Eigenschaften](/dynamics365/customer-engagement/web-api/incident?view=dynamics-ce-odata-9#Properties) finden Sie eine `_customerid_value`-Sucheneigenschaft, die denselben Wert enthält, der für die einzelwertigen Navigationseigenschaften festgelegt ist, die einen Wert enthalten.  
  
Im Allgemeinen sollten Sie keine Sucheigenschaften verwenden und stattdessen die entsprechenden einzelwertigen Navigationseigenschaften verwenden. Diese Eigenschaften sind eingeschlossen, weil sie möglicherweise für bestimmte Integrationsszenarien hilfreich sein können. Diese Eigenschaften sind schreibgeschützt und berechnet, weil sie einfach die Änderungen wiedergeben, die mithilfe der entsprechenden einzelwertigen Navigationseigenschaft angewendet werden.  
  
Wenn Sie Sucheneigenschaften in einer Abfrage mit einschließen, können Sie verlangen, dass Anmerkungen, die zusätzliche Informationen zu den Daten enthalten, eingeschlossen werden und für diese zugrunde liegenden Attribute, die nicht von einer einzelwertige Navigationseigenschaft vertreten werden, angezeigt werden. Weitere Informationen:[Abrufen von Daten zu Sucheigenschaften](query-data-web-api.md#bkmk_lookupProperty)  
  
<a name="bkmk_navprops"></a>

## <a name="navigation-properties"></a>Navigationseigenschaften

In OData erlauben Navigationseigenschaften, dass Sie auf Daten zugreifen können, die sich auf die aktuelle Entität beziehen. Wenn Sie eine Entität abrufen, können Sie festlegen, das Navigationseigenschaften zu erweitern, um die zugehörigen Daten einzuschliessen. Es gibt zwei Arten von Navigationseigenschaften: einzelwertige und sammlungswertige.  
  
<a name="bkmk_singleValuedNavigationProperties"></a>
 
### <a name="single-valued-navigation-properties"></a>Einzelwertige Navigationseigenschaften

Diese Einzelwertigen Navigationseigenschaften entsprechen Suchattributen, die viel-zu-ein-Beziehungen unterstützen und eine Referenz auf eine andere Entität einstellen dürfen. Im `$metadata` `EntityType`-Element sind diese als `NavigationProperty`-Element mit einem `Type`-Attribut auf einen einzelnen Typ festgelegt. Nachfolgend finden Sie ein Beispiel der einzelwertigen <xref href="Microsoft.Dynamics.CRM.account?text=account EntityType" /> `createdby`-Navigationseigenschaft in den `$metadata`:  
  
```xml  
<NavigationProperty Name="createdby" Type="mscrm.systemuser" Nullable="false" Partner="lk_accountbase_createdby">  
 <ReferentialConstraint Property="_createdby_value" ReferencedProperty="systemuserid" />  
</NavigationProperty>  
```  
  
Jede Navigationseigenschaft, die eine einzewertige Navigationseigenschaft darstellt, hat eine entsprechende sammlungswertige Navigationseigenschaft, die vom `Partner` Attributswert angegeben ist. Jede einzelwertige Navigationseigenschaft ist auch ein `ReferentialConstraint`-Element mit `Property` Attributwert, der die berechnete, schreibgeschützte Sucheneigenschaft darstellt, die verwendet werden kann, um entsprechende GUID-Wert der verknüpften Entität abzurufen. Weitere Informationen: [Such-Eigenschaften](web-api-types-operations.md#bkmk_lookupProperties)  
  
<a name="bkmk_collectionvaluedNavProperties"></a>

### <a name="collection-valued-navigation-properties"></a>Gemeinsam bewertete Navigationseigenschaften

Diese Eigenschaften entsprechen ein-zu-vielen oder viel-zu-vielen Verhältnissen. Im `$metadata` `EntityType`-Element werden diese als `NavigationProperty`-Element mit einem `Type`-Attributsatz definiert, der auf die Sammlung eines Typs festgelegt ist. Im Folgenden wird die <xref href="Microsoft.Dynamics.CRM.account?text=account EntityType" /> `Account_Tasks` sammlungswertige Navigationseigenschaft dargestellt, die eine ein-zu-vielen Beziehung darstellt.  
  
```xml  
<NavigationProperty Name="Account_Tasks" Type="Collection(mscrm.task)" Partner="regardingobjectid_account_task" />  
```  
  
Wenn die sammlungswertige Navigationseigenschaft eine n: n-Beziehung darstellt, sind der Name der Navigationseigenschaft und der Name des Partners identisch. Im Folgenden wird die <xref href="Microsoft.Dynamics.CRM.account?text=account EntityType" /> `accountleads_association` sammlungswertige Navigationseigenschaft dargestellt, die eine n:n-Beziehung darstellt.  
  
```xml  
<NavigationProperty Name="accountleads_association" Type="Collection(mscrm.lead)" Partner="accountleads_association" />  
```  
  
Der Unterschied zwischen 1:n- und n:n-Beziehungen ist wichtig, wenn Web API verwendet wird. Die Art, wie Sie Entitäten zuordnen, ist immmer gleich, unabhängig vom Typ der Beziehung. Die n: n-Beziehungen verwenden weiterhin überschneidende Entitäten im Hintergrund, nur einige spezielle Systgementitäten sind im <xref:Microsoft.Dynamics.CRM.EntityTypeIndex> enthalten. Beispielsweise ist <xref href="Microsoft.Dynamics.CRM.campaignactivityitem?text=campaignactivityitem EntityType" /> technisch eine überschneidende Entität, aber ist eingeschlossen, weil sie mehr Eigenschaften hat als eine gewöhnliche überschneidende Entität.  
  
Ein normale überschneidene Entität hat nur die folgenden vier grundlegenden Eigenschaften, um n: n-Beziehung zu verwalten. Wenn Sie eine angepasste n: n-Beziehung zwischen Entitäten erstellen, wird eine normale überschneidende Entität erstellt, um die Beziehung zu unterstützen. Da Sie Navigationseigenschaften verwenden sollen, um Vorgänge auszuführen, die n: n-Beziehungen einbeziehen, sind normale überschneidende Entitäten nicht vollständig dokumentiert können aber weiterhin mithilfe vom Web API zur verfügung stehen. Auf diese überschneidenden Entitätstypen kann über einen festgelegten Entitätsnamen zugegriffen werden, der folgende Namenskonvention verwendet: *\<intersect entity logical name>*+’collection’. Beispielsweise können Sie Informationen vom überschneidenden contactleads-Entitätstyp mit `[Organization URI]/api/data/v9.0/contactleadscollection` abrufen. Sie sollten diese normalen überschneidenden Entitäten nur verwenden, wenn Sie Änderungen nachverfolgen möchten.  
  
<a name="bkmk_actions"></a>

## <a name="actions"></a>Aktionen

*Aktionen* sind Vorgänge, die Nebenwirkungen, wie Datenänderung zulassen und nicht weiter zusammengesetzt werden können, um ein nicht deterministisches Verhalten zu vermeiden.  
  
 Das <xref:Microsoft.Dynamics.CRM.ActionIndex> Thema enthält jede der verfügbaren Systemmaßnahmen. Weitere Informationen finden Sie unter [Verwenden von Web-API-Aktionen](use-web-api-actions.md).  
  
<a name="bkmk_functions"></a>
 
## <a name="functions"></a>Funktionen

*Funktionen* sind Vorgänge, die keine Nebenwirkungen aufweisen und weitere Zusammensetzung unterstützen können, beispielsweise zusätzliche Filtervorgänge, Funktionen oder eine Aktion.  
  
 Es gibt zwei Arten von Funktionen im Web API:  
  
-   Das <xref:Microsoft.Dynamics.CRM.FunctionIndex> Thema enthält jede der verfügbaren Systemfunktionen.  
  
-   Das <xref:Microsoft.Dynamics.CRM.QueryFunctionIndex> Thema führt Funktionen auf, die als Kriterien in einer Abfrage verwendet werden.  
  
 Weitere Informationen: [Verwenden von Web-API-Funktionen](use-web-api-functions.md)  
  
<a name="bkmk_complexTypes"></a>
 
## <a name="complex-types"></a>Komplexe Typen

*Komplexe Typen* sind schlüssellose benannte strukturierte Typen, die einen Satz von Eigenschaften enthalten. Komplexe Typen werden als Eigenschaftswerte in Modelentitäten oder als Parameter oder Rückgabewerte für Vorgänge verwendet.  
  
<xref:Microsoft.Dynamics.CRM.ComplexTypeIndex> enthält alle systemkomplexen Typen. *Komplexe Typen* sind schlüssellose benannte strukturierte Typen, die einen Satz von Eigenschaften enthalten. Sie werden allgemein als Eigenschaftswerte in Modelentitäten oder als Parameter oder Rückgabewerte für Vorgänge verwendet. Nachfolgend finden Sie den <xref href="Microsoft.Dynamics.CRM.WhoAmIResponse?text=WhoAmIResponse ComplexType" /> der $metadata.  
  
```xml  
<ComplexType Name="WhoAmIResponse">  
  <Property Name="BusinessUnitId" Type="Edm.Guid" Nullable="false" />  
  <Property Name="UserId" Type="Edm.Guid" Nullable="false" />  
  <Property Name="OrganizationId" Type="Edm.Guid" Nullable="false" />  
</ComplexType>  
```  
  
<a name="bkmk_EnumTypes"></a>
 
## <a name="enumeration-types"></a>Enumerationstypen
 
*Enumerationstypen* oder *EnumTypen* weden primitive Typen genannt, deren Werte Konstanten mit zugrunde liegenden ganzzahligen Werten benannt sind.  
  
<xref:Microsoft.Dynamics.CRM.EnumTypeIndex> enthält alle Enumerationstypen. *Enumerationstypen* nennt man primitive Typen, deren Werte Konstanten mit zugrunde liegenden ganzzahligen Werten lauten. Nachfolgend finden Sie den <xref href="Microsoft.Dynamics.CRM.AccessRights?text=AccessRights EnumType" /> der $metadata.  
  
```  
<EnumType Name="AccessRights">  
  <Member Name="None" Value="0" />  
  <Member Name="ReadAccess" Value="1" />  
  <Member Name="WriteAccess" Value="2" />  
  <Member Name="AppendAccess" Value="4" />  
  <Member Name="AppendToAccess" Value="16" />  
  <Member Name="CreateAccess" Value="32" />  
  <Member Name="DeleteAccess" Value="65536" />  
  <Member Name="ShareAccess" Value="262144" />  
  <Member Name="AssignAccess" Value="524288" />  
</EnumType>  
```  
  
### <a name="see-also"></a>Siehe auch  

[Common Data Service-Web-API verwenden](overview.md)<br />
[Authentifizierung beim Common Data Service mit der Web-API](authenticate-web-api.md)<br />
[Vorgänge mithilfe der Web-API ausführen](perform-operations-web-api.md)
