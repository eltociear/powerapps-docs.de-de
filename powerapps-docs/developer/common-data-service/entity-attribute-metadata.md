---
title: Attributmetadaten| Microsoft Docs
description: Sie erhalten Informationen über die Attributmetadatenverwendung in Common Data Service.
services: ''
suite: powerapps
documentationcenter: na
author: mayadumesh
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/31/2018
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

<!-- This topic was not migrated it was written for PowerApps 
Was Mike Carter
Overlap with https://docs.microsoft.com/dynamics365/customer-engagement/developer/introduction-entity-attributes

-->
# <a name="attribute-metadata"></a>Attribut-Metadaten

Entitäten enthalten eine Sammlung von Attributen, die für die Daten stehen, die in jedem Datensatz eingeschlossen sein können. Entwickler müssen die verschiedenen Arten von Attributen kennen und wie damit gearbeitet wird. 

Weitere Informationen: [Einführung in Entitätsattributen](/dynamics365/customer-engagement/developer/introduction-entity-attributes)

## <a name="attribute-names"></a>Attributname.

Wie Entitäten hat jedes Attribut einen eindeutig definierten Namen, wenn es erstellt wird, Dieser Name ist auf verschiedene Weise dargestellt:


|Name |Beschreibung  |
|---------|---------|
|`SchemaName`|In der Regel eine Pascal-umkleidete Version des logischen Namen. z. B. `AccountNumber`|
|`LogicalName`|Alle kleingeschriebene Namen. z. B. `accountnumber`|

Wenn Sie ein benutzerdefiniertes Attribut erstellen, wird der Name, den Sie auswählen, mit dem Anpassungspräfixwert des Lösungsherausgebers verwendet, der mit der Lösung zugeordnet wird, als das Attribut in erstellt wurde.

Sie können die Namen eines Attributes nicht ändern, nachdem es erstellt wurde.

Jedes Attribut weist auch zwei Eigenschaften auf, die lokalisierte Werte anzeigen. Dies sind die Werte, die verwendet werden, um sich auf die Attribute in einer App zu beziehen.

|Name |Beschreibung  |
|---------|---------|
|`DisplayName`|Normalerweise gleich wie der Schemaname, können aber Leerzeichen enthalten. z. B. **Firmennummer**|
|`Description`|Ein kurzer folgenden Satz, der das Attribut beschreibt oder eine Anweisung für Benutzer enthält. z.B.*Um eine Firma in Systemansichten schnell suchen und erkennen zu können, geben Sie eine ID-Nummer oder einen ID-Code für die Firma in der Systemansicht ein.*<br />In Modell-angetriebenen Apps werden diese Informationen angezeigt, wenn Benutzer über das Feld für dieses Attribut in einem Formular angezeigt werden.|


Dies sind die Lokalisierungswerte, die verwendet werden, um sich auf die Attribute in einer App zu beziehen. Diese Werte können jederzeit geändert werden. Um die lokalisierten Werte hinzuzufügen oder zu bearbeiten gehen Sie zu [Common Data Service-Anpassungs-Handbuch:  Angepassten Entitäts- und Feldtext in andere Sprachen übersetzen](/dynamics365/customer-engagement/customize/export-customized-entity-field-text-translation).

## <a name="attribute-types"></a>Attributtypen

Die `AttributeTypeName`-Eigenschaft beschreibt den Typ eines Attributes. Diese Eigenschaft enthält einen Wert vom Typ, `AttributeTypeDisplayName` der eine Beschriftung für jedes der unterschiedlichen Arten von Attributen bietet, die es gibt. 

> [!NOTE]
> Lassen Sie sich nicht von der `AttributeType`-Eigenschaft verwirren. Die Werte in dieser älteren Eigenschaft sind mehrheitlich mit dem `AttributeTypeName` abgestimmt,  außer dass es `ImageType`-Attribute als `Virtual` zeigt. Sie sollten sich auf die Eigenschaft `AttributeTypeName` anstelle der Eigenschaft `AttributeType` beziehen.

In der folgende Tabelle:

- Diese sind Typen für Vergleich nach Kategorie gruppiert.
- Für jeden `AttributeTypeDisplayName`-Wert ist die entsprechende .NET-Assembly[AttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.attributemetadata) abgeleitete Klasse enthalten, wo verfügbar. Es ist keine 1:1 Beziehung zwischen diesen Datensatztypen und der `AttributeTypeDisplayName` Beschriftung.
- Diese Attributtypen, die als benutzerdefinierte Attribute erstellt werden können, umfassen die entsprechenden Beschriftung, die auf der Benutzeroberfläche angezeigt wird.


|Kateg.|AttributeTypeDisplayName/<br />AttributeMetadata Typ|Kan erstellen/<br />Beschriftung|Beschreibung  |
|---------|---------|---------|---------|
|Kategorisierung|`BooleanType`<br />[BooleanAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.booleanattributemetadata)|Ja<br />**Zwei Optionen**|Enthält den ausgewählten Optionswert von zwei Optionen, die normalerweise einen wahren oder falschen Wert angeben.<br />Weitere Informationen:[Optionssatz](#option-sets)|
|Kategorisierung|`EntityNameType`<br />[EntityNameAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.entitynameattributemetadata)|Nein|Enthält einen Optionswerts, der einer Entität im System entspricht. Nur zur internen Verwendung.|
|Kategorisierung|`MultiSelectPicklistType`<br />[MultiSelectPicklistAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.multiselectpicklistattributemetadata)|Ja<br />**MultiSelect-Optionssatz**|Enthält mehrere ausgewählte Optionswerte, in der mehrere Optionen ausgewählt werden können.<br />Weitere Informationen: <br />[Optionssätze](#option-sets)<br />[Mehrfachauswahl-Listenattribute](/dynamics365/customer-engagement/developer/multi-select-picklist)|
|Kategorisierung|`PicklistType`<br />[PicklistAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.picklistattributemetadata)|Ja<br />**Optionssatz**|Enthält den ausgewählten Optionswert, in dem mehrere Optionen ausgewählt werden können.<br />Weitere Informationen:[Optionssatz](#option-sets)|
|Kategorisierung|`StateType`<br />[StateAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.stateattributemetadata)|Nein|Enthält den Optionswerts, der den Status eines Entitätsdatensatzes beschreibt.<br />Weitere Informationen:[Optionssatz](#option-sets)|
|Kategorisierung|`StatusType`<br />[StatusAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.statusattributemetadata)|Nein|Enthält den Optionswerts, der den Grund für den Status eines Entitätsdatensatzes beschreibt.<br />Weitere Informationen:[Optionssatz](#option-sets)|
|Abholung|`CalendarRulesType`|Nein|Enthält eine Sammlung von `CalendarRules` Entitätsdatensätzen<br />Es gibt keine aktuellen Attribute, die diesen Typ verwenden. Wenn Sie einen Proxy erstellen, erstellt das Codegenerierungstool die folgenden zwei simulierten Attribute, die nicht in den Metadaten vorhanden sind. Diese Attribute repräsentieren tatsächlich eine Ansicht der Kalenderregeldatensätze, die in einer 1: n-Beziehung dem Entitätsdatensatz zugeordnet sind.|
|Abholung|`PartyListType`|Nein|Enthält eine Sammlung von `ActivityParty` Entitätsdatensätzen<br />Mehr Informationen: [ActivityParty-Entität](reference/entities/activityparty.md).|
|Datum und Uhrzeit|`DateTimeType`<br />[DateTimeAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.datetimeattributemetadata)|Ja<br />**Datum und Uhrzeit**|Enthält einen Datums- und einen Zeitwert.<br />Alle Daten- und Zeitattribute unterstützen Werte ab dem 1/1/1753 12:00 Uhr.|
|Bild|`ImageType`<br />[ImageAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.imageattributemetadata)|Ja<br />**Bild**|Enthält Daten, um das Abrufen von Bilddaten nach einem Entitätsdatensatz zu unterstützen.<br />Weitere Informationen: [Entitätsbilder](entity-metadata.md#entity-images)|
|Verwaltete Eigenschaft|`ManagedPropertyType`<br />[ManagedPropertyAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.managedpropertyattributemetadata)|Nein|Enthält Daten, die beschreiben, dass die Lösungskomponente, die im Entitätsdatensatz gespeichert ist, angepasst werden kann, wenn sie in eine verwaltete Lösung eingebunden wird.<br />Weitere Informationen: [Verwaltete Eigenschaften](introduction-solutions.md#managed-properties)|
|Menge|`BigIntType`<br />[BigIntAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.bigintattributemetadata)|Nein|Enthält einen `BigInt`-Wert. Nur zur internen Verwendung.|
|Menge|`DecimalType`<br />[DecimalAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.decimalattributemetadata)|Ja<br />**Dezimalzahl**|Enthält einen `Decimal`-Wert. Die `Precision`-Eigenschaftensätze der Berechtigungsebene der Genauigkeit.|
|Menge|`DoubleType`<br />[DoubleAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.doubleattributemetadata)|Ja<br />**Gleitkommazahl**|Enthält einen `Double`-Wert. Die `Precision`-Eigenschaftensätze der Berechtigungsebene der Genauigkeit.|
|Menge|`IntegerType`<br />[IntegerAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.integerattributemetadata)|Ja<br />**Ganze Zahl**|Enthält einen `Int`-Wert.|
|<a name='money_type'></a>Menge|`MoneyType`<br />[MoneyAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.moneyattributemetadata)|Ja<br />**Währung**|Enthält einen `Decimal`-Wert. Die `PrecisionSource`-Eigenschaft bestimmt, wo die Ebene der Genauigkeit festgelegt ist.<br />0: Die `Precision`-Eigenschaft<br />1: Das `Organization.PricingDecimalPrecision` Attribut<br />2: Das `TransactionCurrency.CurrencyPrecision`-Attribut im Entitätsdatensatz|
|Referenz|`CustomerType`<br />[LookupAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.lookupattributemetadata)|Ja<br />**Kunde**|Enthält einen Verweis entweder über eine Firma oder einen Kontaktentitätsdatensatz.|
|Referenz|`LookupType`<br />[LookupAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.lookupattributemetadata)|Ja<br />**Suche**|Entfernen Sie eine Referenz auf einem Entitätsdatensatz. Die logischen Namen der gültigen Datensätze werden in der Regel in der Eigenschaft `Targets` des Attributs gespeichert.|
|Referenz|`OwnerType`<br />[LookupAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.lookupattributemetadata)|Nein|Enthält einen Verweis entweder zu einem Benutzer- oder einem Team-Entitätsdatensatz.|
|String|`MemoType`<br />[MemoAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.memoattributemetadata)|Ja<br />**Mehrere Textzeilen**|Enthält einen Zeichenwert der in einem mehrzeiligen Textfeld angezeigt werden soll.|
|String|`StringType`<br />[StringAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.stringattributemetadata)|Ja<br />**Einzelne Textzeile**|Enthält einen Zeichenwert der in einem einzeiligen Textfeld angezeigt werden soll.|
|Eindeutiger Bezeichner|`UniqueidentifierType`<br />[UniqueIdentifierAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.uniqueidentifierattributemetadata)|Nein|Enthält einen Wert des GUID- Bezeichners.|
|Virtuell|`VirtualType`|Nein|Diese Attribute können nicht im Code verwenden und können im Wesentlichen ignoriert werden.|


## <a name="supported-operations-and-form-usage-for-attributes"></a>Unterstützte Vorgänge und Formularverwendung für Attribute

Jedes Attribut enthält boolesche Eigenschaften, die die Arten von Vorgängen beschreiben, an denen sie teilnehmen können und wie sie in einem Formular vorhanden sein können.

|Eigenschaft|Beschreibung|
|--|--|
|`IsRequiredForForm`|Ob das Attribut in einem Formular als Feld hinzugefügt werden muss.|
|`IsValidForCreate`|Ob der Atributtwert in einen Erstellungsvorgang festgelegt werden kann.|
|`IsValidForForm`|Ob das Attribut in einem Formular als Feld hinzugefügt werden muss.|
|`IsValidForRead`|Ob der Attributwert abgerufen werden kann.|
|`IsValidForUpdate`|Ob der Atributtwert in einen Aktualisierungssvorgang festgelegt werden kann.|

Wenn Sie versuchen, einen Wert in einem Erstellungs- oder Aktualisierungsvorgang für ein Attribut festzulegen, das für diesen Vorgang gültig ist, wird der Wert ignoriert.
Wenn Sie versuchen, ein Attribut abzurufen, das zum Lesen ungültig ist, wird ein NULL-Wert zurückgegeben.


## <a name="attribute-requirement-level"></a>Attribut-Anforderungsebene

Die `RequiredLevel`-Eigenschaft ist eine boolesche verwaltete Eigenschaft, die beschreibt, wenn ein Attributwert erforderlich ist.

Diese Eigenschaft kann einen der folgenden Werte sein:

|Name|Value|UI-Beschriftung|Beschreibung|
|--|--|--|--|
|`None`|0|**Optional**|Die Anforderungen werden angegeben.|
|`SystemRequired`|1|**Systemabhängig**|Das Attribut ist erforderlich, um einen Wert zu haben.|
|`ApplicationRequired`|2|**Eingabe erforderlich**|Das Attribut ist vom Geschäft erforderlich, um einen Wert zu haben.|
|`Recommended`|3|**Eingabe empfohlen**|Es wird empfohlen, dass das Attribut ein Wert ist.|

Common Data Service erzwingt nur die `SystemRequired`-Option für Attribute, die vom System erstellt werden. Benutzerdefinierte Attribute können nicht angegeben werden, um die Option `SystemRequired` zu nutzen. 

Modell-angetriebene Apps erzwingen die `ApplicationRequired` Option und verwenden eine Präsentation für die `Recommended` Option. Ersteller benutzerdefinierter Clients können diese Informationen brauchen, um ähnliche Überprüfungs- oder Präsentationsoptionen anzufordern.

Da es sich um eine verwaltete Eigenschaft handelt, wie z.B. Herausgeber einer verwalteten Lösung können Sie entscheiden, ob der Verbraucher der Lösung diese Einstellungen der Attribute in Ihrer Lösung ändern kann.

Weitere Informationen: [Verwaltete Eigenschaften](introduction-solutions.md#managed-properties)


## <a name="rollup-and-calculated-attributes"></a>Rollup und berechnete Attribute

Berechnete und Rollup-Attribute befreien den Benutzer von manuellen Berechnungen und lassen ihn sich auf die Arbeit konzentrieren. Systemadministratoren können jetzt ein Feld definieren, das den Wert vieler allgemeiner Berechnungen enthält, ohne mit einem Entwickler arbeiten zu müssen. Entwickler können die Plattformfunktionen auch dazu nutzen, diese Berechnungen anzustellen, anstatt dies im eigenen Code zu tun.

Weitere Informationen: 
- [Common Data Service-Anpassungshandbuch: Definieren der Rollupfelder, die Werte zusammenfassen](/dynamics365/customer-engagement/customize/define-rollup-fields)
- [Common Data Service-Anpassungshandbuch: Berechnete und Rollupattribute](/dynamics365/customer-engagement/customize/define-calculated-fields)
- [Berechnete und Rollupattribute](/dynamics365/customer-engagement/developer/calculated-rollup-attributes)

## <a name="attribute-format"></a>Attributformat

Die Formatwerte für Attributkontrollen, wie sie in Modell-angetriebenen Apps angezeigt wird. Entwickler benutzerdefinierter Apps verwenden diese Informationen, um ähnliche Erfahrungen zu erstellen.

### <a name="integer-formats"></a>Ganzzahlige Formate

Verwenden Sie die `Format`-Eigenschaft mit Ganzzahlattributen, um andere Benutzerfreundlichkeiten für den Typ anzuzeigen.

|Option|Beschreibung|
|--|--|
|`None`|Zeigt ein Textfeld, um einen Zahlenwert zu bearbeiten|
|`Duration`|Zeigt eine Dropdownliste an, die Zeitintervallen enthält. Ein Benutzer kann einen Wert in der Liste auswählen oder einen ganzzahligen Wert eingeben, der die Anzahl von Minuten darstellt.|
|`TimeZone`|Zeigt eine Dropdownliste an, die eine Liste von Zeitzonen enthält.|
|`Language`|Zeigt eine Dropdownliste an, die eine Liste von Sprachen enthält, die für die Organisation aktiviert sind. Wenn keine anderen Sprachen aktiviert sind, ist die einzige Option die Ausgangssprache. Der gespeicherte Wert ist der LCID-Wert für die Sprache.|

### <a name="string-formats"></a>Zeichenkettenformate

Verwenden Sie die `FormatName` Eigenschaft mit Zeichenattributen, um Werte von [StringFormatName-Klasse](/dotnet/api/microsoft.xrm.sdk.metadata.stringformatname) festzulegen, um zu steuern, wie das Zeichenfolgenattribut formatiert wird.

|Name|Beschreibung|
|--|--|
|`Email`|Das Formfeld wird den Textwert als E-Mail-Adresse überprüfen und im Feld einen mailto-Link erstellen.|
|`PhoneNumber`|Das Formularfeld enthält einen Link, um einen Telefonanruf mithilfe von Skype zu initiieren.|
|`PhoneticGuide`|Nur zur internen Verwendung|
|`Text`|Das Formular zeigt ein Textfeld an.|
|`TextArea`|Das Formular zeigt ein Textbereichsfeld an.|
|`TickerSymbol`|Das Formular zeigt einen Link an, der sich öffnet, um ein Angebot für das Aktientickersymbol anzuzeigen.|
|`URL`|Das Formular zeigt einen Link an, um die URL zu öffnen.|
|`VersionNumber`|Nur zur internen Verwendung.|

### <a name="date-and-time-formats"></a>Datum- und Zeitformate

Die `DateTimeBehavior`-Eigenschaft, um das Verhalten für Datum und Zeitattributte zu steuern.
Es gibt drei Optionen:

|Option|Kurze Beschreibung|
|--|--|
|`UserLocal`|Speichert den Datums- und Uhrzeitwert als UTC-Wert im System.|
|`DateOnly`|Speichert den tatsächlichen Datumswert mit dem Zeitwert als 00:00 Uhr (00:0000) im System.|
|`TimeZoneIndependent`|Speichert die tatsächlichen Datums- und Uhrzeitwerte im System unabhängig von der Benutzerzeitzone.|

Verwenden der `Format`-Eigenschaften, um zu steuern, wie beispielsweise Wert in einer Modell-angetriebenen App unabhängig von `DateTimeBehavior` angezeigt werden.

|Option|Beschreibung|
|--|--|
|DateAndTime|Datum und Uhrzeit vollständig anzeigen|
|DateOnly|Nur das Datum anzeigen.|

Weitere Informationen: [Verhalten und Format des Datums- und Uhrzeitattributs](/dynamics365/customer-engagement/developer/behavior-format-date-time-attribute)

## <a name="auto-number-attributes"></a>Automatische Nummerierungsattribute

Sie können ein automatisches Nummerierungsattribut für eine beliebige Entität hinzufügen. Im Moment können Sie das Attribut auch programmgesteuert hinzufügen. Es gibt keine Benutzerschnittstelle, um dieses Typ des Attributs hinzuzufügen.
Weitere Informationen [Automatisch nummerierte Attribute erstellen](/dynamics365/customer-engagement/developer/create-auto-number-attributes)

## <a name="option-sets"></a>Optionssätze

Diese Attribute, die eine Gruppe von Optionen anzeigen, können sich auf einen Satz von Optionen  beziehen, die durch das Attribut definiert sind oder sie können sich auf einen separaten Satz von Optionen beziehen, die von mehreren für ein Attribut freigegeben werden können. Dies gilt besonders dann, wenn Werte in einem Attribut auch für andere Attribute gelten. Durch das Verweisen auf einen allgemeinen Satz von Optionen können die Optionen an einem zentralen Ort verwaltet werden. Diese Optionssätze, die freigegeben werden können, sind *globale* . Optionssätze. Die im Attribut definierten sind *lokale* Optionssätze.

### <a name="retrieve-options-data"></a>Optionen Daten abrufen
Der Organisationsservice stellt Anforderungsklassen zur Verfügung, die Sie verwenden können, um die Optionen abzurufen, die durch ein Attribut verwendet werden.

#### <a name="use-the-organization-service-to-retrieve-options"></a>Nutzen Sie den Organistionsservicce, um Optionen abzurufen

Jedes der Attribute mit Optionen von [EnumAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.enumattributemetadata) geerbt und umfasst eine [Optionssatz-Eigenschaft](/dotnet/api/microsoft.xrm.sdk.metadata.enumattributemetadata.optionset). Diese Eigenschaft enthält, [OptionSetMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.optionsetmetadata) welche Optionen in der [Optionseigenschaft](/dotnet/api/microsoft.xrm.sdk.metadata.optionsetmetadata.options) enthalten. 

Mit dem Organisationsservice können Sie die folgenden Nachrichten verwenden, um Informationen zu  Optionsets abzurufen:

|Anforderungsklasse|Beschreibung|
|--|--|
|[RetrieveAllOptionSetsRequest](/dotnet/api/microsoft.xrm.sdk.messages.retrievealloptionsetsrequest) |Ruft Daten für alle *globalen* Optionssets ab|
|[RetrieveAttributeRequest](/dotnet/api/microsoft.xrm.sdk.messages.retrieveattributerequest) |Ruft Daten über ein Attribut mit allen *lokalen* Optionensets ab|
|[RetrieveMetadataChangesRequest](/dotnet/api/microsoft.xrm.sdk.messages.retrievemetadatachangesrequest) |Ruft Metadaten auf Basis einer Abfrage ab, die *lokalw* Optionsets umfassen kann<br />Weitere Informationen: [Abrufen und Erkennen von Änderungen bei Metadaten](/dynamics365/customer-engagement/developer/retrieve-detect-changes-metadata)|
|[RetrieveOptionSetRequest](/dotnet/api/microsoft.xrm.sdk.messages.retrieveoptionsetrequest) |Ruft Daten für alle *globalen* Optionssets ab.|

Weitere Informationen: 
- [Beispiel: Speichern von Attributauswahllisten-Metadaten in einer Datei](/dynamics365/customer-engagement/developer/org-service/sample-dump-attribute-picklist-metadata-file)
- [Common Data Service-Entwicklerdokumentation: Globale Optionssätze anpassen](/dynamics365/customer-engagement/developer/org-service/customize-global-option-sets)

#### <a name="use-the-web-api-to-retrieve-options"></a>Nutzen Sie den Web API, um Optionen abzurufen

Der Web API stellt einen beruhigenden Stil zum Abfragen von Optionswerten bereit. Sie können diese lokalen bzw. globalen Optionen abrufen, indem Sie die Attribute innerhalb einer Entität abrufen. Im folgenden Beispiel gibt [OptionSetMetadata](/dynamics365/customer-engagement/web-api/optionsetmetadata) für die Optionen zurück, einschließlich [Konto](reference/entities/account.md).[AccountCategoryCode property](reference/entities/account.md#BKMK_AccountCategoryCode).

`GET <organization url>/api/data/v9.0/EntityDefinitions(LogicalName='account')/Attributes(LogicalName='accountcategorycode')/Microsoft.Dynamics.CRM.PicklistAttributeMetadata?$select=LogicalName&$expand=OptionSet`

Mit der Web API können Sie auch [RetrieveMetadataChanges-Funktion](/dynamics365/customer-engagement/web-api/retrievemetadatachanges) abrufen.

Weitere Informationen: [Abfrage von Metadaten mithilfe der Web API> Abfrage von EntityMetadaten-Attributen](/dynamics365/customer-engagement/developer/webapi/query-metadata-web-api#querying-entitymetadata-attributes)



## <a name="attribute-mapping"></a>Attribut-Zuordnung

Beim Erstellen eines neuen Entitätsdatensatz im Rahmen eines vorhandenen Entitätsdatensatzes können Sie bestimmte Werte des vorhandenen Datensatz über Standardwerte für den als neuen Entitätsdatensatz automatisch übertragen. Dadurch wird die Dateneingabe für Personen geführt , die Modell-angetriebene Apps verwenden. Anwendungsbenutzer sehen die zugeordneten Werte und können sie bearbeiten vor dem Speichern der Entität.

Für die Entwickler, die benutzerdefinierte Clients erstellen, kann das gleiche Verhalten erreicht werden, indem die `InitializeFrom`Meldung (Organisations-Service [InitializeFromRequest-Klasse](/dotnet/api/microsoft.crm.sdk.messages.initializefromrequest) oder Internet API [InitializeFrom-Funktion](/dynamics365/customer-engagement/web-api/initializefrom)) verwendet wird, um die Entitätsdaten mit konfigurierten festgelegten Standardwerten abzurufen.

Weitere Informationen 
- [Common Data Service-Anpassungshandbuch: Zuordnen von Entitätsfeldern](/dynamics365/customer-engagement/customize/map-entity-fields#BKMK_mappingEntityFields)
- [Common Data Service-Entwicklerhandbuch: Anpassen von Entitäten und Attributzuordnungen](/dynamics365/customer-engagement/developer/customize-entity-attribute-mappings)

### <a name="see-also"></a>Siehe auch

[Common Data Service-Entitäten](entities.md)
