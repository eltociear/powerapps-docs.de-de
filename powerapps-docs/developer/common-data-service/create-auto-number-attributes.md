---
title: Erstellen von automatischen Nummerierungsattributen (Common Data Service) | Microsoft Docs
description: 'Erfahren Sie über das Erstellen des automatischen Nummerierungsattributs in derselben Weise, wie Sie ein Zeichenfolgenattribut mithilfe der StringAttributeMetadata-Klasse erstellen, außer Verwendung der neuen AutoNumberFormat-Eigenschaft. Verwenden Sie die AutoNumberFormat-Eigenschaft, um ein Muster zu definieren, das Sequenznummern und zufällige Zeichenfolgen beim Zusammenstellen der Platzhalter enthält und die Länge und den Typ der generierten Werte bestimmt.'
keywords: Automatische Nummerierungsattribute
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
# <a name="create-auto-number-attributes"></a>Automatische Nummerierungsattribute erstellen

Mit Common Data Service können Sie ein automatisches Nummerierungsattribut für eine beliebige Entität hinzufügen. Im Moment können Sie das Attribut auch programmgesteuert hinzufügen. Es gibt keine Benutzerschnittstelle, um dieses Typ des Attributs hinzuzufügen. Dieses Thema erläutert, wie Sie ein automatisches Nummerierungsattribut programmgesteuert erstellen und einen Startwert für sequenzielle Elemente festlegen können. Außerdem wird im Thema gezeigt, wie die Sequenznummer für den nächsten Datensatz festgelegt wird, wenn Sie später den Startwert jederzeit zurücksetzen müssen.
> [!NOTE]
>Die Einstellung des Startwerts ist optional. Es ist nicht erforderlich, den Startwert anzurufen, wenn Sie den Startwert nicht erneut festlegen müssen.


Sie können ein automatisches Nummerierungsattribut in derselben Weise, wie Sie ein Zeichenfolgenattribut mithilfe der **StringAttributeMetadata**-Klasse erstellen, außer Verwendung der neuen **AutoNumberFormat**-Eigenschaft. Verwenden Sie die **AutoNumberFormat**-Eigenschaft, um ein Muster zu definieren, das Sequenznummern und zufällige Zeichenfolgen beim Zusammenstellen der Platzhalter enthält und die Länge und den Typ der generierten Werte bestimmt. Die zufälligen Zeichenfolgen helfen Ihnen, Duplikate oder Konflikte zu vermeiden, insbesondere, wenn die Offline-Clients versuchen, die automatische Nummerierung zu erstellen.

Beim Erstellen eines automatischen Nummerierungsattributs muss die Werte der **StringAttributeMetadata.FormatName**-Eigenschaft oder der **StringAttributeMetadata.Format**-Eigenschaft Text sein. Da diese die Standardwerte sind, legen Sie in der Regel diese Eigenschaft nicht fest. Sie können ein automatisches Nummerierungsattribut nicht erstellen, das jedes andere Format besonderer Art wie E-Mail, Phone, Textbereich, URL oder jedes andere der [vorhandenen Formate](https://msdn.microsoft.com/library/microsoft.xrm.sdk.metadata.stringformatname.aspx) verwendet.

Das sequenzielle Segment wird durch SQL generiert, und daher ist die Eindeutigkeit durch SQL garantiert.

> [!NOTE]
>Sie können ein vorhandenes Formattextattribut in ein automatisches Nummerierungsformat umwandeln.

Wenn Sie das automatische Nummerierungsformatattribut als ein Feld einem Formular hinzufügen, verhaltet sich das automatische Nummerierungsformat als schreibgeschützt im Formular, und Endbenutzer können nicht das Feld bearbeiten. Der Wert wird erst dann festgelegt, nachdem Sie die Entität gespeichert haben. Sie können ein beliebiges automatisches Nummerierungsattribut als den Wert jedes anderen Felds in Ansichten, Rastern usw. finden.

### <a name="examples"></a>Beispiele
Die folgenden Beispiele zeigen, wie ein neues automatisches Nummerierungsattribut namens **new\_SerialNumber** für eine benutzerdefinierte Entität namens **new\_Widget** zu erstellen, damit es einen Wert hat, der wie folgt aussieht: **WID-00001-AB7LSFG-20170913070240**.
Verwenden des Organisationsdientes mit SDK-Assemblys-**CreateAttributeRequest**- und **StringAttributeMetadata**-Klassen:

```csharp
CreateAttributeRequest widgetSerialNumberAttributeRequest = new CreateAttributeRequest
            {
                EntityName = "newWidget",
                Attribute = new StringAttributeMetadata
                {
                    //Define the format of the attribute
                    AutoNumberFormat = "WID-{SEQNUM:5}-{RANDSTRING:6}-{DATETIMEUTC:yyyyMMddhhmmss}",
                    LogicalName = "new_serialnumber",
                    SchemaName = "new_SerialNumber",
                    RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
                    MaxLength = 100, // The MaxLength defined for the string attribute must be greater than the length of the AutoNumberFormat value, that is, it should be able to fit in the generated value.
                    DisplayName = new Label("Serial Number", 1033),
                    Description = new Label("Serial Number of the widget.", 1033)
                }
            };
            _serviceProxy.Execute(widgetSerialNumberAttributeRequest);
```

## <a name="use-web-api"></a>Verwendung der Web-API

Sie können die Entitätsdefinitionen mit der Web-API erstellen und aktualisieren.

Weitere Informationen: [Erstellen und Aktualisieren von Entitätsdefinitionen mit der Web-API > Attribute erstellen](https://msdn.microsoft.com/library/mt593078.aspx#Anchor_3).

#### <a name="request"></a>Anforderung
```http
POST [Organization URI]/api/data/v9.0/EntityDefinitions(LogicalName='new_widget')/Attributes HTTP/1.1
Accept: application/json
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0

{
 "AttributeType": "String",
 "AttributeTypeName": {
  "Value": "StringType"
 },
 "Description": {
  "@odata.type": "Microsoft.Dynamics.CRM.Label",
  "LocalizedLabels": [
   {
    "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",
    "Label": "Serial Number of the widget.",
    "LanguageCode": 1033
   }
  ]
 },
 "DisplayName": {
  "@odata.type": "Microsoft.Dynamics.CRM.Label",
  "LocalizedLabels": [
   {
    "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",
    "Label": "Serial Number",
    "LanguageCode": 1033
   }
  ]
 },
 "RequiredLevel": {
  "Value": "None",
  "CanBeChanged": true,
  "ManagedPropertyLogicalName": "canmodifyrequirementlevelsettings"
 },
 "SchemaName": "new_SerialNumber",
 "AutoNumberFormat": "WID-{SEQNUM:5}-{RANDSTRING:6}-{DATETIMEUTC:yyyyMMddhhmmss}",
 "@odata.type": "Microsoft.Dynamics.CRM.StringAttributeMetadata",
 "FormatName": {
  "Value": "Text"
 },
 "MaxLength": 100
}
```

#### <a name="response"></a>Antwort

```http
HTTP/1.1 204 No Content
OData-Version: 4.0
OData-EntityId: [Organization URI]/api/data/v9.0/EntityDefinitions(402fa40f-287c-e511-80d2-00155d2a68d2)/Attributes(f01bef16-287c-e511-80d2-00155d2a68d2)
```

## <a name="autonumberformat-options"></a>AutoNumberFormat-Optionen

Diese Beispiele zeigen, wie Sie die **AutoNumberFormat**-Eigenschaft konfigurieren können, um verschiedene Ergebnisse zu erhalten:

|**AutoNumberFormat-Wert**|**Beispielswert**|
|:----------|:----------|
|`CAR-{SEQNUM:3}-{RANDSTRING:6}`|`CAR-123-AB7LSF`|
|`CNR-{RANDSTRING:4}-{SEQNUM:4}`|`CNR-WXYZ-1000`|
|`{SEQNUM:6}-#-{RANDSTRING:3}`  |`123456-#-R3V`|
|`KA-{SEQNUM:4}`                |`KA-0001`|
|`{SEQNUM:10}`                  |`1234567890`|
|`QUO-{SEQNUM:3}#{RANDSTRING:3}#{RANDSTRING:5}`|      `QUO-123#ABC#PQ2ST`|
|`QUO-{SEQNUM:7}{RANDSTRING:5}` |`QUO-0001000P9G3R`|
|`CAS-{SEQNUM:6}-{RANDSTRING:6}-{DATETIMEUTC:yyyyMMddhhmmss}`|`CAS-002000-S1P0H0-20170913091544`|
|`CAS-{SEQNUM:6}-{DATETIMEUTC:yyyyMMddhh}-{RANDSTRING:6}`|`CAS-002002-2017091309-HTZOUR`|
|`CAS-{SEQNUM:6}-{DATETIMEUTC:yyyyMM}-{RANDSTRING:6}-{DATETIMEUTC:hhmmss}`|`CAS-002000-201709-Z8M2Z6-110901`|

Die zufälligen Zeichenfolgenplatzhalter sind optional. Sie können mehr als einen zufälligen Zeichenfolgenplatzhalter einschließen. Verwenden Sie jeden der Formatwerte für Datum-Zeit-Platzhalter von [Standardzeichenfolgen für Datums- und Uhrzeitformat](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings).

### <a name="string-length"></a>Zeichenfolgenlänge

Die Tabelle stellt den Zeichenfolgenlängenwert für die zufälligen und sequenziellen Platzhalter dar.

<table>
  <tr>
    <th>Platzhalter</th>
    <th>Zeichenfolgenlänge</th>
    <th>Ausgangsszenario</th>
  </tr>
  <tr>
    <td><code>{RANDSTRING:MIN_LENGTH}</code></td>
    <td>Der Wert von <b>MIN_LENGTH</b> liegt zwischen 1 und 6.</td>
     <td>Wenn Sie die Entität speichern, wird das automatische Nummerierungsattribut die zufällige Zeichenfolge mit der bestimmten Länge generieren, wenn der Wert zwischen 1 und 6 liegt. Wenn Sie den <b>MIN_LENGTH</b>-Wert von 7 oder höher verwenden, werden Sie einen Fehler des falschen Arguments sehen.</td>
  </tr>
  <tr>
    <td><code>{SEQNUM:MIN_LENGTH}</code></td>
    <td>Der Minimalwert Wert der <b>MIN_LENGTH</b> ist 1. Die Nummer wächst, um über die minimale Länge hinaus zu inkrementieren.</td>
    <td>Wenn Sie die Entität speichern, funktioniert das automatische Nummerierungsattribut perfekt und wird weiter bei höheren Werten von <b>MIN_LENGTH</b> perfekt funktionieren.</td></table>

Für sequenzielle Wertplatzhalter ist die **MIN_LENGTH** eine minimale Länge. Wenn Sie den Wert auf 2 setzen, wird der Anfangswert 01 sein und der Wert der 100. Entität wird 100 sein. Die Nummer wird weiter über die minimale Länge hinaus inkrementieren. Der Wert in Einstellung der Länge für Seqenzwerte muss eine konsequente Länge für den automatisch generierten Wert bei der Hinzufügung zusätzlicher 0s zum ursprünglichen Wert herstellen. Er wird den absoluten Wert nicht einschränken. Zufallwertplatzhalter werden immer der gleichen Länge sein.

Da die sequenziellen Werte höher als minimale Länge, die dafür eingeräumt ist, werden können, sollen Sie die **StringAttributeMetadata.MaxLength**-Eigenschaft nicht anpassen, damit die Länge Ihrem formatierten Wert entspricht. Dabei gibt es einen geringen Wert, und er könnte zu einem Fehler in der Zukunft führen, wenn der Wert den **MaxLength**-Wert überschreitet. Stellen Sie sicher, dass Sie genug Raum für einen realistischen Bereich von seqenziellen Werten gelassen haben.

> [!NOTE]
> Es gibt keine Überprüfung der Platzhalterwerte, wenn Sie das Attribut erstellen. Dieser Fehler wird nur dann angezeigt, wenn Sie versuchen, eine Entitätsinstanz zu speichern, die einen falsch konfigurierten **AutoNumberFormat**-Wert verwendet.
> Beispielweise, wenn Sie die Länge der zufälligen Zeichenfolge mehr als 6 festlegen, wird die erste Person, die eine neue Entitätsinstanz erstellt, einen Fehler mit dem **falschen Argument** haben, wenn Sie zuvor versucht hat, die Entität zu speichern, die das neue automatische Nummerierungsattribut enthält.

## <a name="update-auto-number-attributes"></a>Automatische Nummerierungsattribute aktualisieren

Wenn Sie ein automatisches Nummerierungsattribut für eine fehlerhafte Konfiguration erstellen, oder wenn Sie ein vorhandenes automatisches Nummerierungsattribut ändern möchten, können Sie den Wert des **AutoNumberFormat**-Attributs aktualisieren.

Der folgende Codeausschnitt hilft Ihnen das automatische Nummerierungsattribut abzurufen, zu ändern und zu aktualisieren.

Zur Bearbeitung eines vorhandenen automatischen Nummerierungsattributs müssen Sie das Attribut mithilfe der **RetrieveAttributeRequest**-Klasse abrufen.

```csharp
// Create the retrieve request
RetrieveAttributeRequest attributeRequest = new RetrieveAttributeRequest
            {
                EntityLogicalName = entityName.ToLower(),
                LogicalName = "new_serialnumber",
                RetrieveAsIfPublished = true
            };
// Retrieve attribute response
RetrieveAttributeResponse attributeResponse = (RetrieveAttributeResponse)_serviceProxy.Execute(attributeRequest);
```

Nachdem Sie das automatische Nummerierungsattribut abgerufen haben, müssen Sie das Attribut ändern und aktualisieren.

```csharp            
//Modify the retrieved auto-number attribute
AttributeMetadata retrievedAttributeMetadata = attributeResponse.AttributeMetadata;
retrievedAttributeMetadata.AutoNumberFormat = "CAR-{RANDSTRING:5}{SEQNUM:6}"; //Modify the existing attribute by writing the format as per your requirement 

// Update the auto-number attribute            
UpdateAttributeRequest updateRequest = new UpdateAttributeRequest
                        {
                            Attribute = retrievedAttributeMetadata,
                            EntityName = "newWidget",
                        };
// Execute the request
_serviceProxy.Execute(updateRequest);
```

## <a name="set-a-seed-value"></a>Einen Startwert festlegen

Standardmäßig beginnen alle automatisch nummerierten sequenziellen Werte ab 1000 und nutzen 0 als Präfix abhängig von der Länge. Deswegen ist die Länge des Werts immer gleich. Wenn Sie den Anfangswert ändern möchten, müssen Sie den ursprünglichen Startwert mithilfe der nachstehenden API ändern, um die nächste Nummer festzulegen, die für das sequenzielle Segment verwendet werden wird.

Zum Beispiel, wenn die Länge der sequenziellen Nummer 5 ist, möchten Sie ab einem Anfangswert von 10.000 anstelle des Standardwerts von 00001 beginnen. Wenn Sie einen anderen Startwert auswählen möchten, müssen Sie, nachdem Sie das automatische Nummerierungsattribut erstellt haben, die **SetAutoNumberSeed**-Nachricht verwenden. Verwenden Sie die **SetAutoNumberSeedRequest**-Klasse, wenn Sie die SDK-Assemblys und **SetAutoNumberSeed**-Aktion mithilfe der Web-API verwenden.

Die **AutoNumberSeed**-Nachricht hat die folgenden Parameter:


|**Name**|**Typ**|**Beschreibung**|
|:----------|:----------|:----------|
|EntityName|Zeichenfolge|Der logische Name der Entität, der das Attribut enthält, für das Sie den Startwert festlegen möchten.|
|AttributeName|Zeichenfolge|Der logische Name des Attributs, für das Sie den Startwert festlegen möchten.|
|Value|int|Nächster Wert der automatischen Nummer fürs Attribut.|

> [!NOTE]
> Festlegen des Startwerts ändert nur den **aktuellen Zahlenwert** für das angegebene Attribut in der aktuellen Umgebung. Es gibt keinen allgemeinen **Startwert** für das Attribut an. Der Startwert ist nicht in einer Lösung enthalten, wenn er in einer anderen Umgebung installiert ist. Um die Startzahl nach dem Import einer Lösung festzulegen, verwenden Sie **SetAutoNumberSeed**-Nachricht in der Zielumgebung.

### <a name="examples"></a>Beispiele
Die folgenden Beispiele legen den Startwert bis 10.000 für ein automatisches Nummerierungsattribut namens **new\_SerialNumber** für eine benutzerdefinierte Entität namens **new\_Widget** fest.

Verwenden des Organisationsdienstes mit der **SetAutoNumberSeedRequest**-Klasse der SDK-Assemblys:
```csharp
//Define the seed 
SetAutoNumberSeedRequest req = new SetAutoNumberSeedRequest();
req.EntityName = "newWidget";
req.AttributeName = "newSerialnumber";
req.Value = 10000;
_serviceProxy.Execute(req);
```
Verwenden der **SetAutoNumberSeed**-Aktion der Web-API.

Weitere Informationen: [Verwenden der Web-API-Aktionen > Ungebundene Aktionen](https://msdn.microsoft.com/library/mt607600.aspx#bkmk_unboundActions)

#### <a name="request"></a>Anforderung

```http
POST [Organization URI]/api/data/v9.0/SetAutoNumberSeed HTTP/1.1
Accept: application/json
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0

{
 "EntityName": "new_Widget",
 "AttributeName": "new_Serialnumber",
 "Value": 10000
} 
```

#### <a name="response"></a>Antwort

```json
HTTP/1.1 204 No Content
OData-Version: 4.0
```
## <a name="community-tools"></a>Community-Tools

### <a name="auto-number-manager"></a>Automatische Nummerierungmanager erstellen

**[Automatischer Nummerierungsmanager](https://www.xrmtoolbox.com/plugins/Rappen.XrmToolBox.AutoNumManager/)** für XrmToolBox ist ein Community-basiertes Tool für Common Data Service, das eine Benutzeroberfläche zum Einstellen, Aktualisieren und Entfernen des automatischen Nummerierungsformats für neue oder bestehende Attribute bereitstellt.
Weitere Informationen finden Sie im [Entwicklertools](developer-tools.md) Thema für Community entwickelte Tools und [anm.xrmtoolbox.com](http://anm.xrmtoolbox.com) weitere Informationen zum automatischen Zahlen-Manager.

> [!NOTE]
> Die Communitytools sind kein Produkt von Common Data Service. Es wird kein Support für die Communitytools angeboten. Wenn Sie Fragen zu dem Tool haben, setzen Sie sich bitte mit dem Herausgeber in Verbindung. Weitere Informationen: [XrmToolBox](https://www.xrmtoolbox.com). 


### <a name="see-also"></a>Siehe auch
[Metadaten und Datenmodelle in Dynamics 365](/dynamics365/customer-engagement/developer/metadata-data-models)  
[Anpassen von Entitätsmetadaten](customize-entity-metadata.md) 