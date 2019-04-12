---
title: Mehrfachauswahl-Listenattribute (Common Data Service) | Microsoft Docs
description: 'Infos zu Mehrfachauswahllistenattributen, die das Speichern von mehreren Options-Auswahlen in einem einzelnen Attribut erlauben.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: MicroSri
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="multi-select-picklist-attributes"></a>Mehrfachauswahl-Listenattribute

Systemanpasser können Sie einen Attributtyp definieren, der die Auswahl mehrerer Optionen ermöglicht. Diese <xref:Microsoft.Xrm.Sdk.Metadata.MultiSelectPicklistAttributeMetadata>-Klasse definiert einen Attributtyp, der von der Klasse <xref:Microsoft.Xrm.Sdk.Metadata.EnumAttributeMetadata> erbt. Wie für die <xref:Microsoft.Xrm.Sdk.Metadata.PicklistAttributeMetadata>-Klasse, umfasst dieses Attribut eine <xref:Microsoft.Xrm.Sdk.Metadata.OptionSetMetadata><xref:Microsoft.Xrm.Sdk.Metadata.OptionSetMetadata.Options>-Eigenschaft, die die gültigen Optionen für das Attribut enthält. Der Unterschied besteht darin, dass die Werte, die Sie erhalten oder einstellen, ein <xref:Microsoft.Xrm.Sdk.OptionSetValueCollection>-Typ sind, der ein Array von ganzen Zahlen enthält, die für die ausgewählten Optionen stehen. Formatierte Werte für dieses Attribut sind eine durch Semikolon getrennte Zeichenfolge, welche die Bezeichnungen der ausgewählten Optionen enthält.

Mit dem Internet-API wird das Attribut definiert mithilfe von <xref href="Microsoft.Dynamics.CRM.MultiSelectPicklistAttributeMetadata?text=MultiSelectPicklistAttributeMetadata EntityType" />.

Wie für Auswahllistenattribute, gibt es technisch keine Obergrenze für die Anzahl von Optionen, die definiert werden können. Benutzerfreundlichkeitsüberlegungen müssen als einschränkende Faktor angewendet werden. Es können jedoch nur jeweils 150 Optionen für ein einzelnes Attribut ausgewählt werden. Außerdem kann ein Standardwert nicht festgelegt werden.

## <a name="setting-multi-select-picklist-values"></a>Festlegen von Mehrfach-Auswahllistenwerten

Mit dem Internet-API können Sie die Werte durch Übergeben einer Zeichenfolge durch Trennzeichen getrennter Zahlenwerte festlegen, wie im folgenden Beispiel angezeigt:
### <a name="request"></a>Anforderung
```http
POST [organization uri]/api/data/v9.0/contacts HTTP/1.1
Accept: application/json
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0

{
    "@odata.type": "Microsoft.Dynamics.CRM.contact",
    "firstname": "Wayne",
    "lastname": "Yarborough",
    "sample_outdooractivities": "1, 9"
}
```
### <a name="response"></a>Antwort
```http
HTTP/1.1 204 No Content
OData-Version: 4.0
OData-EntityId: [organization uri]/api/data/v9.0/contacts(0c67748a-b78d-e711-811c-000d3a75bdf1)
```

Mit dem Organisationsdienste mithilfe der entsprechenden Assemblys können Sie mit <xref:Microsoft.Xrm.Sdk.OptionSetValueCollection> Werte für dieses Attribut festlegen,wie im folgenden C#-Beispiel gezeigt:
```csharp
OptionSetValueCollection activities = new OptionSetValueCollection();
activities.Add(new OptionSetValue(1)); //Swimming
activities.Add(new OptionSetValue(9)); //Camping

Contact contact = new Contact();
contact["firstname"] = "Wayne";
contact["lastname"] = "Yarborough";
contact["sample_outdooractivities"] = activities;

_serviceProxy.Create(contact);
```

## <a name="query-data-from-multi-select-picklists"></a>Abfragen von Daten aus Mehrfach-Auswahllisten

Zwei neue Bedingungsoperatoren können hinzugefügt wurde, um das Abfragen von Werten zu unterstützen Optionssätze auszuwählen: `ContainValues` und `DoesNotContainValues` oder die FetchXml `contain-values` und -`not-contain-values`-Operatoren. Mit dem Internet API gibt es die äquivalenten `ContainValues` und `DoesNotContainValues`-Abfragenfunktionen.

Andere vorhandene Bedingungsoperatoren, die mit diesem Typ von Attribut verwendet werden, sind nachfolgend aufgeführt: `Equal`, `NotEqual`, `NotNull`, `Null`, `In` und `NotIn`. 

> [!NOTE]
> Die `ContainValues` und `DoesNotContainValues`-Operatoren hängen von der Anwendung der Volltextindizierung auf die Datenbanktabellen ab, die mehrere Werte speichern. Es gibt eine Latenz, wenn neue Datensätze erstellt werden und der Volltextindex wirksam wird. Sie müssen einige Sekunden warten, wenn neue Datensätze optimiert sind, bevor Filter mithilfe dieser Operatoren die Werte auswerten können.

Die folgenden Beispiele zeigen die Verwendung von `ContainValues` und `not-contain-values` Verwenden `FetchXML` für folgenden Datnsatz auf ein Auswählensauswahllistenattribut , das `sample_outdooractivities` auf der Entität " `contact` heißt.

### <a name="multi-select-picklist-sampleoutdooractivities-options"></a>Mehrfachauswahl-Listen `sample_outdooractivities`-Optionen:

|Value|Bezeichnung|
|-----|-----|
|1|Schwimmen|
|2|Wandern|
|3|Bergsteigen|
|4|Fischen|
|5|Jagen|
|6|Wird ausgeführt...|
|7|Bootfahren|
|8|Skifahren|
|9|Camping|

### <a name="contact-entity-values"></a>Kontaktentitätswerte

|`fullname`| `sample_outdooractivities` |
|--------|-------------------|
|Wayne Yarborough|1,9|
|Monte Orton|2|
|Randal Maple|4|
|Hiram Mundy|2,3,8,9|
|Barbara Weber|1,4,7|
|Georgette Sullivan|4,5,9|
|Verna Kennedy|2,4,9|
|Marvin Bracken|1,2,8,9|

### <a name="example-code-using-web-api"></a>Beispielcode mithilfe von Web-API
Im folgenden Beispiel wird die Verwendung `ContainsValues`-Abfragenfunktion gezeigt, um alle Kontakte anzuzeigen, den Wandern gefällt. Beachten Sie, wie der Text der Optionen als Anmerkungen aufgrund aufgrund der übernommenen Einstellung `odata.include-annotations="OData.Community.Display.V1.FormattedValue"` zurückgegeben wird.

#### <a name="request"></a>Anforderung
```http
GET [organization uri]/api/data/v9.0/contacts?$select=fullname,sample_outdooractivities&$filter=Microsoft.Dynamics.CRM.ContainValues(PropertyName='sample_outdooractivities',PropertyValues=%5B'2'%5D) HTTP/1.1
Accept: application/json
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0
Prefer: odata.include-annotations="OData.Community.Display.V1.FormattedValue"
```
#### <a name="response"></a>Antwort
```http
HTTP/1.1 200 OK
Content-Type: application/json; odata.metadata=minimal
OData-Version: 4.0
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"
Content-Length: 1092

{
    "@odata.context": "[organization uri]/api/data/v9.0/$metadata#contacts(fullname,sample_outdooractivities)",
    "value": [{
        "@odata.etag": "W/\"529811\"",
        "fullname": "Monte Orton",
        "sample_outdooractivities@OData.Community.Display.V1.FormattedValue": "Hiking",
        "sample_outdooractivities": "2",
        "contactid": "cdbcc48e-0b8d-e711-811c-000d3a75bdf1"
    }, {
        "@odata.etag": "W/\"529823\"",
        "fullname": "Hiram Mundy",
        "sample_outdooractivities@OData.Community.Display.V1.FormattedValue": "Hiking; Mountain Climbing; Skiing; Camping",
        "sample_outdooractivities": "2,3,8,9",
        "contactid": "d7bcc48e-0b8d-e711-811c-000d3a75bdf1"
    }, {
        "@odata.etag": "W/\"529838\"",
        "fullname": "Verna Kennedy",
        "sample_outdooractivities@OData.Community.Display.V1.FormattedValue": "Hiking; Fishing; Camping",
        "sample_outdooractivities": "2,4,9",
        "contactid": "e6bcc48e-0b8d-e711-811c-000d3a75bdf1"
    }, {
        "@odata.etag": "W/\"529843\"",
        "fullname": "Marvin Bracken",
        "sample_outdooractivities@OData.Community.Display.V1.FormattedValue": "Swimming; Hiking; Skiing; Camping",
        "sample_outdooractivities": "1,2,8,9",
        "contactid": "ebbcc48e-0b8d-e711-811c-000d3a75bdf1"
    }]
}
```
Im folgenden Beispiel wird die Verwendung des `not-contain-values`-Operators in der folgenden `FetchXml`-Abfrage mit Internet-API angezeigt.

```xml
<fetch distinct='false' no-lock='false' mapping='logical'>
    <entity name='contact'>
        <attribute name='fullname' />
        <attribute name='sample_outdooractivities' />
            <filter type='and'>
                <condition attribute='sample_outdooractivities' operator='not-contain-values'>
                    <value>2</value>
                </condition>
            </filter>
    </entity>
</fetch>
```

#### <a name="request"></a>Anforderung
```http
GET [organization uri]/api/data/v9.0/contacts?fetchXml=%253Cfetch%2520distinct%253D'false'%2520no-lock%253D'false'%2520mapping%253D'logical'%253E%253Centity%2520name%253D'contact'%253E%253Cattribute%2520name%253D'fullname'%2520%252F%253E%253Cattribute%2520name%253D'sample_outdooractivities'%2520%252F%253E%253Cfilter%2520type%253D'and'%253E%253Ccondition%2520attribute%253D'sample_outdooractivities'%2520operator%253D'not-contain-values'%253E%253Cvalue%253E2%253C%252Fvalue%253E%253C%252Fcondition%253E%253C%252Ffilter%253E%253C%252Fentity%253E%253C%252Ffetch%253E HTTP/1.1
Accept: application/json
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0
Prefer: odata.include-annotations="OData.Community.Display.V1.FormattedValue"
```
#### <a name="response"></a>Antwort
```http
HTTP/1.1 200 OK
Content-Type: application/json; odata.metadata=minimal
OData-Version: 4.0
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"

{
    "@odata.context": "[organization uri]/api/data/v9.0/$metadata#contacts(fullname,sample_outdooractivities,contactid)",
    "value": [{
        "@odata.etag": "W/\"529806\"",
        "fullname": "Wayne Yarborough",
        "sample_outdooractivities@OData.Community.Display.V1.FormattedValue": "Swimming; Camping",
        "sample_outdooractivities": "1,9",
        "contactid": "c8bcc48e-0b8d-e711-811c-000d3a75bdf1"
    }, {
        "@odata.etag": "W/\"529816\"",
        "fullname": "Randal Maple",
        "sample_outdooractivities@OData.Community.Display.V1.FormattedValue": "Fishing",
        "sample_outdooractivities": "4",
        "contactid": "d2bcc48e-0b8d-e711-811c-000d3a75bdf1"
    }, {
        "@odata.etag": "W/\"529828\"",
        "fullname": "Barbara Weber",
        "sample_outdooractivities@OData.Community.Display.V1.FormattedValue": "Swimming; Fishing; Boating",
        "sample_outdooractivities": "1,4,7",
        "contactid": "dcbcc48e-0b8d-e711-811c-000d3a75bdf1"
    }, {
        "@odata.etag": "W/\"529833\"",
        "fullname": "Georgette Sullivan",
        "sample_outdooractivities@OData.Community.Display.V1.FormattedValue": "Fishing; Hunting; Camping",
        "sample_outdooractivities": "4,5,9",
        "contactid": "e1bcc48e-0b8d-e711-811c-000d3a75bdf1"
    }]
}
```

### <a name="example-code-using-queryexpression-and-fetchexpression"></a>Beispielcode mithilfe QueryExpression und FetchExpression

Im folgenden C#-Beispiel wird die Verwendung von `ContainsValues`-Operator mit `QueryExpression` und `not-contain-values` mit `FetchExpression` mit `RetrieveMultiple` und dem Organisationsdienst.

```csharp
//Retrieve contacts who like hiking
//Using Query Expression
int[] hikingValue = new int[] { 2 };
ConditionExpression condition = new ConditionExpression("sample_outdooractivities", ConditionOperator.ContainValues, hikingValue);

FilterExpression filter = new FilterExpression();
filter.AddCondition(condition);

QueryExpression likesHikingQuery = new QueryExpression(Contact.EntityLogicalName);
likesHikingQuery.ColumnSet.AddColumns("fullname", "sample_outdooractivities");
likesHikingQuery.Criteria.AddFilter(filter);

EntityCollection hikers = _serviceProxy.RetrieveMultiple(likesHikingQuery);

Console.WriteLine("\nContacts who like Hiking");
Console.WriteLine("=========================");
foreach (Contact contact in hikers.Entities)
{
    string values = (contact["sample_outdooractivities"] == null) ? "null" : contact.FormattedValues["sample_outdooractivities"];
    Console.WriteLine("{0} {1}", contact.FullName, values);
}

    /*OUTPUT:
    Contacts who like Hiking
    =========================
    Monte Orton Hiking
    Hiram Mundy Hiking; Mountain Climbing; Skiing; Camping
    Verna Kennedy Hiking; Fishing; Camping
    Marvin Bracken Swimming; Hiking; Skiing; Camping
    */

//Retrieving contacts who do not like hiking:
//Using Fetch Expression
string fetchXml = @"<fetch distinct='false' no-lock='false' mapping='logical'>
                     <entity name='contact'>
                      <attribute name='fullname' />
                      <attribute name='sample_outdooractivities' />
                       <filter type='and'>
                        <condition attribute='sample_outdooractivities' operator='not-contain-values'>
                         <value>2</value>
                        </condition>
                       </filter>
                      </entity>
                     </fetch>";
FetchExpression doesNotLikeHiking = new FetchExpression(fetchXml);

EntityCollection nonHikers = _serviceProxy.RetrieveMultiple(doesNotLikeHiking);

Console.WriteLine("\nContacts who do not like Hiking");
Console.WriteLine("===============================");
foreach (Contact contact in nonHikers.Entities)
{
    string values = (contact["sample_outdooractivities"] == null) ? "null" : contact.FormattedValues["sample_outdooractivities"];
    Console.WriteLine("{0} {1}", contact.FullName, values);
}

    /* OUTPUT
    Contacts who do not like Hiking
    ===============================
    Wayne Yarborough Swimming; Camping
    Randal Maple Fishing
    Barbara Weber Swimming; Fishing; Boating
    Georgette Sullivan Fishing; Hunting; Camping 
    */
```


## <a name="create-a-multi-select-picklist-with-code"></a>Erstellen einer Mehrfach-Auswählensauswahlliste mit Code

Die einfachste Möglichkeit, eine Mehrfachauswahlliste zu erstellen ist, den Attributeditor in den Anpassungstools zu verwenden. Weitere Informationen: [Erstellen und Bearbeiten von Feldern](/dynamics365/customer-engagement/customize/create-edit-fields)

Aber, wenn Sie dieses Abhängigkeitstyps Erstellung des Attributs automatisieren möchten, können Sie C#-Code beispielsweise folgende mit dem Organisationsservice verwenden, der eine Mehrfachauswahlliste erstellt, um der `contact` Entität Optionen von Aktivitäten im Freien zu erlauben. Weitere Informationen [Attribute erstellen](/dynamics365/customer-engagement/developer/org-service/work-attribute-metadata.md#create-attributes)

```csharp
    private const int _languageCode = 1033; //English

    MultiSelectPicklistAttributeMetadata outDoorActivitiesAttribute = new MultiSelectPicklistAttributeMetadata()
    {
    SchemaName = "sample_OutdoorActivities",
    LogicalName = "sample_outdooractivities",
    DisplayName = new Label("Outdoor activities", _languageCode),
    RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
    Description = new Label("Outdoor activities that the contact likes.", _languageCode),
    OptionSet = new OptionSetMetadata()
        {
            IsGlobal = false,
            OptionSetType = OptionSetType.Picklist,
            Options = {
                new OptionMetadata(new Label("Swimming",_languageCode),1),
                new OptionMetadata(new Label("Hiking",_languageCode),2),
                new OptionMetadata(new Label("Mountain Climbing",_languageCode),3),
                new OptionMetadata(new Label("Fishing",_languageCode),4),
                new OptionMetadata(new Label("Hunting",_languageCode),5),
                new OptionMetadata(new Label("Running",_languageCode),6),
                new OptionMetadata(new Label("Boating",_languageCode),7),
                new OptionMetadata(new Label("Skiing",_languageCode),8),
                new OptionMetadata(new Label("Camping",_languageCode),9)}
        }
    };

    CreateAttributeRequest createAttributeRequest = new CreateAttributeRequest
    {
        EntityName = Contact.EntityLogicalName,
        Attribute = outDoorActivitiesAttribute
    };
```

### <a name="see-also"></a>Siehe auch
[Einführung in die Entitätsattribute](/dynamics365/customer-engagement/developer/introduction-entity-attributes)<br />
[Erstellen einer Entität mithilfe des Web-API](webapi/create-entity-web-api.md)<br />
[Datenabfrage mit Web-API](webapi/query-data-web-api.md)<br />
[Verwenden von Attributmetadaten](/dynamics365/customer-engagement/developer/org-service/work-attribute-metadata)<br />
[Beipiel: Verwenden von Attributmetadaten](/dynamics365/customer-engagement/developer/org-service/sample-work-attribute-metadata)<br />
[Programmierung mit später und früher Bindung mithilfe des Organisationsservices](org-service/early-bound-programming.md)
