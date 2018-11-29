---
title: getGlobalContext.organizationSettings (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: badf4f82-cb47-4864-aa43-bb777d04de4d
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getglobalcontextorganizationsettings-client-api-reference"></a>getGlobalContext.organizationSettings (Client-API-Referenz)



Gibt Informationen zu aktuellen Organisationseinstellungen zurück. 

`var organizationSettings = Xrm.Utility.getGlobalContext().organizationSettings`

Das Objekt **organizationSettings** bietet die folgenden Eigenschaften.

## <a name="attributes"></a>Attribute

Gibt Attribute und ihre Werte als `key:value`-Paare zurück, die für die Organisationsentität verfügbar sind. Attribute als Mehrwerte sind verfügbar, wenn Sie als Attributabhängigkeiten in der Webressourceabhängigkeitsliste angegeben werden. Der `key` ist der logische Name des Attributs.

### <a name="syntax"></a>Syntax

`organizationSettings.attributes`

### <a name="return-value"></a>Rückgabewert

**Typ:**: Objekt.

**Beschreibung**: Ein Objekt mit Attributen und den dazugehörigen Werten.

## <a name="basecurrencyid"></a>baseCurrencyId 

Gibt die ID der Basiswährung für die aktuelle Organisation wieder.

### <a name="syntax"></a>Syntax

`organizationSettings.baseCurrencyId`

### <a name="return-value"></a>Rückgabewert

**Typ:**: Zeichenfolge

**Description**: ID der Basiswährung.

## <a name="defaultcountrycode"></a>defaultCountryCode 

Gibt den Standard-Land-/Region-Code für Telefonnummern für die aktuelle Organisation wieder.

### <a name="syntax"></a>Syntax

`organizationSettings.defaultCountryCode`

### <a name="return-value"></a>Rückgabewert

**Typ:**: Zeichenfolge

**Beschreibung**: Standard-Landes-/Regionskennzahl für Telefonnummern.

## <a name="isautosaveenabled"></a>isAutoSaveEnabled 

Gibt an, ob die automatische Speicheroption für die aktuelle Organisation aktiviert ist.

### <a name="syntax"></a>Syntax

`organizationSettings.isAutoSaveEnabled`

### <a name="return-value"></a>Rückgabewert

**Typ**: Boolesch.

**Beschreibung**: **true**, wenn aktiviert; sonst **false**.

## <a name="languageid"></a>languageId 

Gibt die bevorzugte Sprache-ID für die aktuelle Organisation wieder.

### <a name="syntax"></a>Syntax

`organizationSettings.languageId`

### <a name="return-value"></a>Rückgabewert

**Typ:**: Anzahl

**Beschreibung**: Bevorzugte Sprache ID Beispiel:

`1033`

## <a name="organizationid"></a>organizationId 

Gibt die ID der aktuellen Organisation zurück.

### <a name="syntax"></a>Syntax

`organizationSettings.organizationId`

### <a name="return-value"></a>Rückgabewert

**Typ:**: Zeichenfolge

**Beschreibung**: ID der aktuellen Organisation.

## <a name="uniquename"></a>uniqueName 

Gibt den eindeutige Name der zu aktuellen Organisation zurück.

### <a name="syntax"></a>Syntax

`organizationSettings.uniqueName`

### <a name="return-value"></a>Rückgabewert

**Typ:**: Zeichenfolge

**Beschreibung**: Eindeutiger Name der zu aktuellen Organisation.

## <a name="useskypeprotocol"></a>useSkypeProtocol 

Gibt an, ob das Skype-Protokoll für die aktuelle Organisation verwendet wird.

### <a name="syntax"></a>Syntax

`organizationSettings.useSkypeProtocol`

### <a name="return-value"></a>Rückgabewert

**Typ**: Boolesch.

**Beschreibung**: **true**, wenn Skype-Protokoll verwendet wird; Andernfalls **false**.


## <a name="related-topics"></a>Verwandte Themen

[Kundenkontext](client.md)

[Benutzereinstellungen](userSettings.md)

[Xrm.Utility.getGlobalContext](../getGlobalContext.md)