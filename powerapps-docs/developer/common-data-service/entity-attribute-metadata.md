---
title: Attributmetadaten | Microsoft-Dokumentation
description: Erfahren Sie mehr über Attributmetadaten, die in Common Data Service für Apps verwendet werden.
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: faisalmo
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/12/2018
ms.author: jdaly
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: f6fcf3ba1e8e9773df65ac566a9d5c798f4d13a9
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "42859159"
---
# <a name="attribute-metadata"></a>Attributmetadaten

Entitäten enthalten eine Auflistung der Attribute, die die Daten darstellen, die in jedem Datensatz enthalten sein können. Entwickler müssen die verschiedenen Attributtypen und die Arbeit mit ihnen verstehen. 

Weitere Informationen finden Sie unter [Entwicklerhandbuch zu Dynamics 365 Customer Engagement: Einführung in die Entitätsattribute](/dynamics365/customer-engagement/developer/introduction-entity-attributes).

## <a name="attribute-names"></a>Attributnamen

Wie bei Entitäten wird für jedes Attributen bei der Erstellung ein eindeutiger Name definiert. Dieser Name wird auf verschiedene Weisen dargestellt:


|Name |Beschreibung  |
|---------|---------|
|`SchemaName`|In der Regel ist dies der logische Name in der Pascal-Schreibweise, z.B. `AccountNumber`.|
|`LogicalName`|Der Name in Kleinbuchstaben, z.B. `accountnumber`.|

Wenn Sie ein benutzerdefiniertes Attribut erstellen, wird dem von Ihnen ausgewählten Namen der Anpassungspräfixwert des Lösungsherausgebers vorangestellt, der mit der Lösung verknüpft ist, in der das Attribut erstellt wurde.

Sie können den Attributnamen nicht mehr ändern, nachdem dieses erstellt wurde.

Außerdem verfügt jedes Attribut über zwei Eigenschaften, die lokalisierte Werte anzeigen können. Dies sind die Werte, die verwendet werden, um auf die Attribute in einer App zu verweisen.

|Name |Beschreibung  |
|---------|---------|
|`DisplayName`|In der Regel mit dem Schemanamen identisch, kann aber auch Leerzeichen enthalten, z.B. **Account Number**|
|`Description`|Ein kurzer Satz, der das Attribut beschreibt oder den Benutzer unterstützt, z.B. *Geben Sie eine ID-Nummer oder Code für das Konto ein, um das Konto schnell in den Systemansichten zu finden und zu identifizieren*.<br />In modellgesteuerten Apps werden diese Informationen angezeigt, wenn Benutzer in einem Formular auf das Feld für dieses Attribut zeigen.|


Dies sind lokalisierbare Werte, die verwendet werden, um auf die Attribute in einer App zu verweisen. Diese Werte können jederzeit geändert werden. Informationen zum Hinzufügen oder Ändern von lokalisierten Werten finden Sie unter [Handbuch zur Anpassung von Dynamics 365 Customer Engagement: Übersetzen von benutzerdefiniertem Entitäts- und Feldtext in andere Sprachen](/dynamics365/customer-engagement/customize/export-customized-entity-field-text-translation).

## <a name="attribute-types"></a>Attributtypen

Die `AttributeTypeName`-Eigenschaft beschreibt den Typ eines Attributs. Diese Eigenschaft enthält einen Wert des Typs `AttributeTypeDisplayName`, der eine Bezeichnung für alle vorhandenen unterschiedlichen Attributtypen bereitstellt. 

> [!NOTE]
> Verwechseln Sie sie nicht mit der `AttributeType`-Eigenschaft. Die Werte in dieser älteren Eigenschaft sind auf `AttributeTypeName` ausgerichtet, mit dem Unterschied, dass sie `ImageType`-Attribute als `Virtual` anzeigen. Anstelle der `AttributeType`-Eigenschaft sollten Sie auf die `AttributeTypeName`-Eigenschaft verweisen.

Inhalt der folgenden Tabelle:

- Diese Typen sind zum Vergleich anhand ihrer Kategorie gruppiert.
- Für jeden `AttributeTypeDisplayName`-Wert wird die entsprechende abgeleitete Klasse [AttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.attributemetadata) der .NET Assembly angegeben, sofern diese verfügbar ist. Es gibt keine direkte Beziehung zwischen diesen Typen und der Bezeichnung `AttributeTypeDisplayName`.
- Diese Attributtypen, die als benutzerdefinierte Attribute erstellt werden können, enthalten eine entsprechende Bezeichnung, die in der Benutzeroberfläche angezeigt wird.


|Kategorie|AttributeTypeDisplayName/<br />AttributeMetadata-Typ|Kann Erstellen/<br />Bezeichnung|Beschreibung  |
|---------|---------|---------|---------|
|Kategorisierung|`BooleanType`<br />[BooleanAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.booleanattributemetadata)|Ja<br />**Zwei Optionen**|Enthält den ausgewählten Optionswert von zwei Optionen, die in der Regel einen Wert angeben, der auf TRUE oder FALSE festgelegt ist.<br />Weitere Informationen finden Sie unter [Option Sets (Optionssätze)](#option-sets)|
|Kategorisierung|`EntityNameType`<br />[EntityNameAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.entitynameattributemetadata)|Nein|Enthält einen Optionswert, der einer Entität in dem System entspricht. Nur zur internen Verwendung.|
|Kategorisierung|`MultiSelectPicklistType`<br />[MultiSelectPicklistAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.multiselectpicklistattributemetadata)|Ja<br />**MultiSelect-Optionssatz**|Enthält mehrere ausgewählte Optionswerte, mit denen mehrere Optionen ausgewählt werden können.<br />Weitere Informationen finden Sie unter: <br />[Option Sets (Optionssätze)](#option-sets)<br />[Entwicklerhandbuch zu Dynamics 365 Customer Engagement: Mehrfachauswahl-Listenattribute](/dynamics365/customer-engagement/developer/multi-select-picklist)|
|Kategorisierung|`PicklistType`<br />[PicklistAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.picklistattributemetadata)|Ja<br />**Optionssatz**|Enthält den ausgewählten Optionswert, ab dem eine Option ausgewählt werden kann.<br />Weitere Informationen finden Sie unter [Option Sets (Optionssätze)](#option-sets)|
|Kategorisierung|`StateType`<br />[StateAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.stateattributemetadata)|Nein|Enthält den Optionswert, der den Status eines Entitätsdatensatzes beschreibt.<br />Weitere Informationen finden Sie unter [Option Sets (Optionssätze)](#option-sets)|
|Kategorisierung|`StatusType`<br />[StatusAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.statusattributemetadata)|Nein|Enthält den Optionswert, der die Begründung für den Status eines Entitätsdatensatzes beschreibt.<br />Weitere Informationen finden Sie unter [Option Sets (Optionssätze)](#option-sets)|
|Sammlung|`CalendarRulesType`|Nein|Enthält eine Sammlung von `CalendarRules`-Entitätsdatensätzen.<br />Es gibt keine Attribute, die diesen Typ verwenden. Wenn Sie einen Proxy generieren, erstellt das Tool zur Codegenerierung zwei simulierte Attribute, die nicht in den Metadaten vorhanden sind. Diese Attribute stellen eine Ansicht der CalendarRules-Datensätze dar, die eine 1:n-Beziehung zum Entitätsdatensatz haben.|
|Sammlung|`PartyListType`|Nein|Enthält eine Sammlung von `ActivityParty`-Entitätsdatensätzen.<br />Weitere Informationen finden Sie unter [ActivityParty entity (ActivityParty-Entität)](#activityparty-entity)|
|Datum und Uhrzeit|`DateTimeType`<br />[DateTimeAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.datetimeattributemetadata)|Ja<br />**Datum und Uhrzeit**|Enthält einen Wert für Datum und Uhrzeit.<br />Alle Attribute zu Datum und Uhrzeit unterstützen Werte ab 1.1.1753 00:00 Uhr.|
|Bild|`ImageType`<br />[ImageAttributeMetadata]()|Ja<br />**Bild**|Enthält Daten, um das Abrufen von Bilddaten für einen Entitätsdatensatz zu unterstützen.<br />Weitere Informationen finden Sie unter [Entity Images (Entitätsbilder)](entity-metadata.md#entity-images)|
|Verwaltete Eigenschaft|`ManagedPropertyType`<br />[ManagedPropertyAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.imageattributemetadata)|Nein|Enthält Daten, die beschreiben, ob eine im Entitätsdatensatz gespeicherte Lösungskomponente angepasst werden kann, wenn sie in einer verwalteten Lösung enthalten ist.<br />Weitere Informationen finden Sie unter [Managed Properties (Verwaltete Eigenschaften)](introduction-solutions.md#managed-properties).|
|Menge|`BigIntType`<br />[BigIntAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.bigintattributemetadata)|Nein|Enthält einen `BigInt`-Wert. Nur zur internen Verwendung.|
|Menge|`DecimalType`<br />[DecimalAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.decimalattributemetadata)|Ja<br />**Dezimalzahl**|Enthält einen `Decimal`-Wert. Die Eigenschaft `Precision` legt die Genauigkeit fest.|
|Menge|`DoubleType`<br />[DoubleAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.doubleattributemetadata)|Ja<br />**Gleitkommazahl**|Enthält einen `Double`-Wert. Die Eigenschaft `Precision` legt die Genauigkeit fest.|
|Menge|`IntegerType`<br />[IntegerAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.integerattributemetadata)|Ja<br />**Ganze Zahl**|Enthält einen `Int`-Wert.|
|Menge|`MoneyType`<br />[MoneyAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.moneyattributemetadata)|Ja<br />**Währung**|Enthält einen `Decimal`-Wert. Die Eigenschaft `PrecisionSource` bestimmt das Maß an Genauigkeit.<br />0: Die `Precision`-Eigenschaft<br />1: Das `Organization.PricingDecimalPrecision`-Attribut<br />2: Das `TransactionCurrency.CurrencyPrecision`-Attribut im Entitätsdatensatz|
|Referenz|`CustomerType`<br />[LookupAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.lookupattributemetadata)|Ja<br />**Kunde**|Enthält einen Verweis auf den Entitätsdatensatz eines Kontos oder Kontakts.|
|Referenz|`LookupType`<br />[LookupAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.lookupattributemetadata)|Ja<br />**Nachschlagen**|Enthält einen Verweis auf einen Entitätsdatensatz. Die logischen Namen der gültigen Datensätze werden in der Regel in der `Targets`-Eigenschaft des Attributs gespeichert.|
|Referenz|`OwnerType`<br />[LookupAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.lookupattributemetadata)|Nein|Enthält einen Verweis auf einen Entitätsdatensatz eines Benutzers oder Teams.|
|Zeichenfolge|`MemoType`<br />[MemoAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.memoattributemetadata)|Ja<br />**Mehrere Textzeilen**|Enthält einen Zeichenfolgenwert, der in einem mehrzeiligen Textfeld angezeigt werden soll.|
|Zeichenfolge|`StringType`<br />[StringAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.stringattributemetadata)|Ja<br />**Eine Textzeile**|Enthält einen Zeichenfolgenwert, der in einem einzeiligen Textfeld angezeigt werden soll.|
|Eindeutiger Bezeichner|`UniqueidentifierType`<br />[UniqueIdentifierAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.uniqueidentifierattributemetadata)|Nein|Enthält einen eindeutigen GUID-Bezeichnerwert.|
|Virtuell|`VirtualType`|Nein|Diese Attribute können nicht in Code verwendet werden und können im Allgemeinen ignoriert werden.|


## <a name="supported-operations-and-form-usage-for-attributes"></a>Unterstützte Vorgänge und Formularnutzung für Attribute

Jedes Attribut enthält boolesche Eigenschaften, die die Arten der Vorgänge beschreiben, an denen das Attribut teilnehmen kann, und die es in einem Formular annehmen kann.

|Eigenschaft|Beschreibung|
|--|--|
|`IsRequiredForForm`|Gibt an, ob das Attribut in einem Formular als Feld enthalten sein muss.|
|`IsValidForCreate`|Gibt an, ob der Attributwert in einem Erstellungsvorgang festgelegt werden kann.|
|`IsValidForForm`|Gibt an, ob das Attribut in einem Formular als Feld hinzugefügt werden kann.|
|`IsValidForRead`|Gibt an, ob das Attribut abgerufen werden kann.|
|`IsValidForUpdate`|Gibt an, ob der Attributwert in einem Aktualisierungsvorgang festgelegt werden kann.|

Wenn Sie versuchen, einen Wert in einem Erstellungs- oder Aktualisierungsvorgang für ein Attribut festzulegen, das für diesen Vorgang nicht gültig ist, wird der Wert ignoriert.
Wenn Sie versuchen ein Attribut abzurufen, das nicht zum Lesen gültig ist, wird ein NULL-Wert zurückgegeben.


## <a name="attribute-requirement-level"></a>Attribute für Erforderlichkeitsstufen

Die Eigenschaft `RequiredLevel` ist eine boolesche Eigenschaft, die verwaltet werden kann und beschreibt, ob ein Attributwert erforderlich ist.

Für diese Eigenschaft können die folgenden Werte festgelegt werden:

|Name|Wert|Benutzeroberflächenbezeichnung|Beschreibung|
|--|--|--|--|
|`None`|0|**Optional**|Es werden keine Anforderungen angegeben.|
|`SystemRequired`|1|**Systemabhängig**|Dieses Attribut muss einen Wert aufweisen.|
|`ApplicationRequired`|2|**Eingabe vom Unternehmen als erforderlich markiert**|Vom Unternehmen wird verlangt, dass dieses Attribut einen Wert aufweist.|
|`Recommended`|3|**Eingabe vom Unternehmen empfohlen**|Es wird empfohlen, dass dieses Attribut einen Wert aufweist.|

Common Data Service für Apps erzwingt die Option `SystemRequired` nur bei Attributen, die vom System erstellt wurden. Benutzerdefinierte Attribute können nicht so festgelegt werden, dass Sie die Option `SystemRequired` verwenden. 

Modellgesteuerte Apps erzwingen die Option `ApplicationRequired` und verwenden eine andere Darstellung für die Option `Recommended`. Ersteller von benutzerdefinierten Clients können diese Informationen verwenden, um ähnliche Überprüfungs- oder Darstellungsoptionen zu erfordern.

Da dies eine verwaltete Eigenschaft ist, können Sie als Herausgeber einer verwalteten Lösung entscheiden, ob die Verbraucher Ihrer Lösung diese Einstellungen von Attributen in Ihrer Lösung ändern dürfen.

Weitere Informationen finden Sie unter [Managed Properties (Verwaltete Eigenschaften)](introduction-solutions.md#managed-properties).


## <a name="rollup-and-calculated-attributes"></a>Rollup-Attribute und berechnete Attribute

Berechnete Attribute und Rollup-Attribute nehmen den Benutzern das manuelle Ausführen von Berechnungen ab und ermöglichen ihnen, sich auf ihre Arbeit zu konzentrieren. Systemadministratoren können ein Feld definieren, um den Wert auf vielen allgemeinen Berechnungen einzuschließen, ohne dabei mit einem Entwickler zusammenarbeiten zu müssen. Entwickler können auch die Funktionen der Plattform dafür nutzen, anstatt diese Berechnungen in ihrem eigenen Code auszuführen.

Weitere Informationen finden Sie unter: 
- [Handbuch zur Anpassung von Dynamics 365 Customer Engagement: Definition von Rollupfeldern, die Werte aggregieren](/dynamics365/customer-engagement/customize/define-rollup-fields)
- [Handbuch zur Anpassung von Dynamics 365 Customer Engagement: Definition berechneter Felder für das Automatisieren von manuellen Berechnungen](/dynamics365/customer-engagement/customize/define-calculated-fields)
- [Dynamics 365 Customer Engagement Developer Guide: Calculated and rollup attributes (Entwicklerhandbuch zu Dynamics 365 Customer Engagement: Berechnete Attribute und Rollup-Attribute)](/dynamics365/customer-engagement/developer/calculated-rollup-attributes)

## <a name="attribute-format"></a>Attributformat

Die Formatierungswerte für Attribute steuern, wie diese in modellgesteuerten Apps angezeigt werden. Entwickler von benutzerdefinierten Apps können diese Informationen verwenden, um ähnliche Funktionen zu erstellen.

### <a name="integer-formats"></a>Ganzzahlformate

Verwenden Sie die `Format`-Eigenschaften mit Ganzzahlattributen, um alternative Benutzeroberflächen für diesen Typ anzuzeigen.

|Option|Beschreibung|
|--|--|
|`None`|Zeigt ein Textfeld zum Bearbeiten eines numerischen Werts an|
|`Duration`|Zeigt eine Dropdownliste an, die Zeitintervalle enthält. Ein Benutzer kann einen Wert aus der Liste auswählen oder einen Ganzzahlwert eingeben, der die Anzahl von Minuten darstellt.|
|`TimeZone`|Zeigt eine Dropdownliste an, die eine Liste von Zeitzonen enthält.|
|`Language`|Zeigt eine Dropdownliste an, die eine Liste der Sprachen enthält, die für die Organisation aktiviert wurden. Wenn keine anderen Sprachen aktiviert wurden, ist die Basissprache die einzige Option. Der gespeicherte Wert ist der LCID-Wert für die Sprache.|

### <a name="string-formats"></a>Zeichenfolgenformate

Verwenden Sie die `FormatName`-Eigenschaft mit Zeichenfolgenattributen, um Werte der [StringFormatName-Klasse](/dotnet/api/microsoft.xrm.sdk.metadata.stringformatname) zum Steuern der Formatierung von Zeichenfolgenattributen festzulegen.

|Name|Beschreibung|
|--|--|
|`Email`|Das Formularfeld überprüft, ob der Textwert einer E-Mail-Adresse entspricht, und erstellt einen MailTo-Link im Feld.|
|`PhoneNumber`|Das Formularfeld enthält einen Link zum Initiieren eines Anrufs mit Skype.|
|`PhoneticGuide`|Nur zur internen Verwendung.|
|`Text`|Das Formular zeigt ein Textfeld an.|
|`TextArea`|Das Formular zeigt ein Feld für einen Textbereich an.|
|`TickerSymbol`|Das Formular zeigt einen Link an, über den ein Angebot des Aktientickersymbols geöffnet wird.|
|`URL`|Das Formular zeigt einen Link zum Öffnen der URL an.|
|`VersionNumber`|Nur zur internen Verwendung.|

### <a name="date-and-time-formats"></a>Formate für Datum und Uhrzeit

Die `DateTimeBehavior`-Eigenschaft zum Steuern des Verhaltens von Datums- und Uhrzeitattributen.
Es gibt drei Optionen:

|Option|Kurzbeschreibung|
|--|--|
|`UserLocal`|Speichert Datum und Uhrzeit als UTC-Wert im System.|
|`DateOnly`|Speichert den tatsächlichen Datumswert mit dem Zeitwert 00:00 Uhr (00:00:00) im System.|
|`TimeZoneIndependent`|Speichert die tatsächlichen Werte für Datum und Uhrzeit im System unabhängig von der Zeitzone des Benutzers.|

Verwenden Sie die `Format`-Eigenschaft zum Steuern davon, wie der Wert in einer modellgesteuerten App unabhängig von `DateTimeBehavior` angezeigt wird.

|Option|Beschreibung|
|--|--|
|DateAndTime|Zeigt Datum und Uhrzeit vollständig an.|
|DateOnly|Zeigt nur das Datum an.|

Weitere Informationen finden Sie unter [Entwicklerhandbuch zu Dynamics 365 Customer Engagement: Verhalten und Format des Datums- und Uhrzeitattributs](/dynamics365/customer-engagement/developer/behavior-format-date-time-attribute).

## <a name="auto-number-attributes"></a>Automatische Nummerierungsattribute

Sie können automatische Nummerierungsattribute für alle Entitäten festlegen. Derzeit können Sie das Attribut programmgesteuert hinzufügen. Es gibt keine Benutzeroberfläche zum Hinzufügen dieses Attributtyps.
Weitere Informationen finden Sie unter [Dynamics 365 Customer Engagement Developer Guide: Create auto-number attributes (Entwicklerhandbuch zu Dynamics 365 Customer Engagement: Erstellen von automatischen Nummerierungsattributen)](/dynamics365/customer-engagement/developer/create-auto-number-attributes).

## <a name="option-sets"></a>Optionssätze

Diese Attribute, die einen Satz von Optionen anzeigen, können einen Optionssatz, der von einem Attribut definiert wird, oder einen separaten Optionssatz referenzieren, der von mehreren Attributen gemeinsam genutzt werden kann. Das ist besonders nützlich, wenn Werte in einem Attribut auch für andere Attribute gelten. Durch das Referenzieren eines allgemeinen Optionssatzes können die Optionen an einem Ort verwaltet werden. Die Optionssätze, die freigegeben werden können, sind *globale* Optionssätze. Die Optionssätze, die in Attributen definiert sind, sind *lokale* Optionssätze.

### <a name="retrieve-options-data"></a>Abrufen von Optionsdaten
Der Organisationsdienst bietet Anforderungsklassen, die Sie verwenden können, um die von einem Attribut verwendeten Optionen abzurufen.

#### <a name="use-the-organization-service-to-retrieve-options"></a>Verwenden des Organisationsdiensts zum Abrufen von Optionen

Alle Attribute mit Optionen erben von [EnumAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.enumattributemetadata) und enthalten eine [OptionSet-Eigenschaft](/dotnet/api/microsoft.xrm.sdk.metadata.enumattributemetadata.optionset). Diese Eigenschaft enthält [OptionSetMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.optionsetmetadata)-Elemente, die wiederum die Optionen in der [Optionseigenschaft](/dotnet/api/microsoft.xrm.sdk.metadata.optionsetmetadata.options) enthalten. 

Mit dem Organisationsdienst können Sie die folgenden Nachrichten zum Abrufen von Informationen über Optionssätze verwenden:

|Anforderungsklasse|Beschreibung|
|--|--|
|[RetrieveAllOptionSetsRequest](/dotnet/api/microsoft.xrm.sdk.messages.retrievealloptionsetsrequest) |Ruft Daten über alle *globalen* Optionssätze ab.|
|[RetrieveAttributeRequest](/dotnet/api/microsoft.xrm.sdk.messages.retrieveattributerequest) |Ruft Daten über ein Attribut ab, einschließlich aller *lokalen* Optionssätze.|
|[RetrieveMetadataChangesRequest](/dotnet/api/microsoft.xrm.sdk.messages.retrievemetadatachangesrequest) |Ruft Metadaten basierend auf einer Abfrage ab, die *lokale* Optionssätze enthalten kann.<br />Weitere Informationen finden Sie unter [Abrufen und Erkennen von Änderungen bei Metadaten](/dynamics365/customer-engagement/developer/retrieve-detect-changes-metadata).|
|[RetrieveOptionSetRequest](/dotnet/api/microsoft.xrm.sdk.messages.retrieveoptionsetrequest) |Ruft Daten über einen *globalen* Optionssatz ab.|

Weitere Informationen finden Sie unter: 
- [Beispiel: Speichern von Attributauswahllisten-Metadaten in einer Datei](/dynamics365/customer-engagement/developer/org-service/sample-dump-attribute-picklist-metadata-file)
- [Entwicklerhandbuch zu Dynamics 365 Customer Engagement: Anpassen von globalen Optionssätzen](/dynamics365/customer-engagement/developer/org-service/customize-global-option-sets)

#### <a name="use-the-web-api-to-retrieve-options"></a>Verwenden der Web-API zum Abrufen von Optionen

Die Web-API stellt RESTful-Abfragen für Optionswerte bereit. Sie können lokale und globale Optionen abrufen, indem Sie die Attribute innerhalb einer Entität abrufen. Das folgende Beispiel gibt [OptionSetMetadata](/dynamics365/customer-engagement/web-api/optionsetmetadata) für die Optionen zurück, die in der Eigenschaft [Account](reference/entities/account.md).[AccountCategoryCode-Eigenschaft](reference/entities/account.md#BKMK_AccountCategoryCode) enthalten sind.

`GET <organization url>/api/data/v9.0/EntityDefinitions(LogicalName='account')/Attributes(LogicalName='accountcategorycode')/Microsoft.Dynamics.CRM.PicklistAttributeMetadata?$select=LogicalName&$expand=OptionSet`

Mit der Web-API können Sie auch die Funktion [RetrieveMetadataChanges](/dynamics365/customer-engagement/web-api/retrievemetadatachanges) verwenden.

Weitere Informationen finden Sie unter [Entwicklerhandbuch zu Dynamics 365 Customer Engagement: Abfragen von Metadaten mit der Web-API > Abfragen von EntityMetadata-Attributen](/dynamics365/customer-engagement/developer/webapi/query-metadata-web-api#querying-entitymetadata-attributes)



## <a name="attribute-mapping"></a>Attributzuordnung

Wenn Sie einen Entitätsdatensatz im Kontext eines bereits vorhandenen Entitätsdatensatzes erstellen, können Sie bestimmte Werte automatisch von dem vorhandenen Entitätsdatensatz als Standardwerte für den neuen Entitätsdatensatz übertragen. Dies optimiert die Dateneingabe für Personen, die modellgesteuerte Apps verwenden. Anwendungsbenutzer können die zugeordneten Werte sehen und bearbeiten, bevor sie die Entität speichern.

Für Entwickler, die benutzerdefinierte Clients erstellen, kann das gleiche Verhalten erreicht werden, indem die `InitializeFrom`-Nachricht ([InitializeFromRequest Class](/dotnet/api/microsoft.crm.sdk.messages.initializefromrequest) beim Organisationsdienst oder die Funktion [InitializeFrom](/dynamics365/customer-engagement/web-api/initializefrom) bei der Web-API) verwendet wird, um die Entitätsdaten mit den konfigurierten Standardwerten festzulegen.

Weitere Informationen 
- [Dynamics 365 Customer Engagement Customization Guide: Map entity fields (Handbuch zur Anpassung von Dynamics 365 Customer Engagement: Zuordnen von Entitätsfeldern)](/dynamics365/customer-engagement/customize/map-entity-fields#BKMK_mappingEntityFields)
- [Entwicklerhandbuch zu Dynamics 365 Customer Engagement: Anpassen von Entitäts- und Attributzuordnungen](/dynamics365/customer-engagement/developer/customize-entity-attribute-mappings)

### <a name="see-also"></a>Siehe auch

[Entitäten in Common Data Service für Apps](entities.md)
