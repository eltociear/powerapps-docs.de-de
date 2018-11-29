---
title: getGlobalContext.userSettings (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 44296667-f1cd-49be-a300-7259bc3b41e0
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getglobalcontextusersettings-client-api-reference"></a>getGlobalContext.userSettings (Client-API-Referenz)



Gibt Informationen zu aktuellen Benutzereinstellungen zurück.

`var userSettings = Xrm.Utility.getGlobalContext().userSettings`

Das Objekt **userSettings** bietet die folgenden Eigenschaften und eine Methode.

## <a name="dateformattinginfo"></a>dateFormattingInfo 

Gibt die Datumsformatierungsinformationen für den aktuellen Benutzer zurück.

### <a name="syntax"></a>Syntax

`userSettings.dateFormattingInfo`

### <a name="return-value"></a>Rückgabewert

**Typ:**: Objekt.

**Beschreibung**: Ein Objekt mit Informationen zur Datumsformatierung wie **FirstDayOfWeek**, **LongDatePattern**, **MonthDayPattern**, **TimeSeparator** usw.

## <a name="defaultdashboardid"></a>defaultDashboardId 

Gibt die ID des Standard-Dashboards für den aktuellen Benutzer wieder.

### <a name="syntax"></a>Syntax

`userSettings.defaultDashboardId`

### <a name="return-value"></a>Rückgabewert

**Typ:**: Zeichenfolge

**Beschreibung**: ID des Standard-Dashboards. 

## <a name="isguidedhelpenabled"></a>isGuidedHelpEnabled 

Gibt an, ob die anpassbare Hilfe für den aktuellen Benutzer aktiviert ist.

### <a name="syntax"></a>Syntax

`userSettings.isGuidedHelpEnabled`

### <a name="return-value"></a>Rückgabewert

**Typ**: Boolesch

**Beschreibung**: true, wenn aktiviert; sonst false. 

## <a name="ishighcontrastenabled"></a>isHighContrastEnabled 

Gibt an, ob der hohe Kontrast für den aktuellen Benutzer aktiviert ist.

### <a name="syntax"></a>Syntax

`userSettings.isHighContrastEnabled`

### <a name="return-value"></a>Rückgabewert

**Typ**: Boolesch

**Beschreibung**: true, wenn aktiviert; sonst false.

## <a name="isrtl"></a>isRTL 

Gibt an, ob die Sprache für den aktuellen Benutzer eine Rechts-nach-links-Sprache (RTL) ist.

### <a name="syntax"></a>Syntax

`userSettings.isRTL`

### <a name="return-value"></a>Rückgabewert

**Typ**: Boolesch

**Beschreibung**: „true“, wenn es eine RTL ist, andernfalls „false“.

## <a name="languageid"></a>languageId 

Gibt die Sprachen-ID des aktuellen Benutzer wieder.

### <a name="syntax"></a>Syntax

`userSettings.languageId`

### <a name="return-value"></a>Rückgabewert

**Typ:**: Anzahl

**Beschreibung**: Sprachen-ID

## <a name="securityroleprivileges"></a>securityRolePrivileges 

Gibt ein Zeichenfolgenarray zurück, das die GUID-Werte für jede des Sicherheitsrollenrechts darstellt, die dem Benutzer oder jedem Team zugeordnet sind, dem der Benutzer angehört.

### <a name="syntax"></a>Syntax

`userSettings.securityRolePrivileges`

### <a name="return-value"></a>Rückgabewert

**Typ**: Array

**Beschreibung**: GUID-Werte jedes der Sicherheitsrollenrechte.

## <a name="securityroles"></a>securityRoles 

Gibt ein Zeichenfolgenarray zurück, das die GUID-Werte für jede der Sicherheitsrollen darstellt, die dem Benutzer oder jedem Team zugeordnet sind, dem der Benutzer angehört.

### <a name="syntax"></a>Syntax

`userSettings.securityRoles`

### <a name="return-value"></a>Rückgabewert

**Typ**: Array

**Beschreibung**: GUID-Werte jeder der Sicherheitsrollen. Beispiel:

`["0d3dd20a-17a6-e711-a94e-000d3a1a7a9b", "ff42d20a-17a6-e711-a94e-000d3a1a7a9b"]`

## <a name="transactioncurrencyid"></a>transactionCurrencyId 

Gibt die Transaktionswährungs-ID des aktuellen Benutzers wieder.

### <a name="syntax"></a>Syntax

`userSettings.transactionCurrencyId`

### <a name="return-value"></a>Rückgabewert

**Typ:**: Zeichenfolge

**Beschreibung**: Transaktionswährungs-ID.

## <a name="userid"></a>userId 

Gibt die GUID des **SystemUser.Id**-Werts für den aktuellen Benutzer zurück.

### <a name="syntax"></a>Syntax

`userSettings.userId`

### <a name="return-value"></a>Rückgabewert

**Typ:**: Zeichenfolge

**Beschreibung**: Die ID des Benutzers. Beispiel:

`"{75B5BA27-FD41-4D45-8E3A-C8446C95F0CC}"`

## <a name="username"></a>userName 

Gibt den Namen des aktuellen Benutzers zurück.

### <a name="syntax"></a>Syntax

`userSettings.userName`

### <a name="return-value"></a>Rückgabewert

**Typ:**: Zeichenfolge

**Beschreibung**: Name des aktuellen Benutzers.

## <a name="gettimezoneoffsetminutes-method"></a>getTimeZoneOffsetMinutes-Methode

Gibt die Differenz in Minuten zwischen der Ortszeit und der Coordinated Universal Time (UTC) zurück.

### <a name="syntax"></a>Syntax

`userSettings.getTimeZoneOffsetMinutes()`

### <a name="return-value"></a>Rückgabewert

**Typ**: Zahl

**Beschreibung**: Zeitzonenoffset in Minuten.

## <a name="related-topics"></a>Verwandte Themen

[Kundenkontext](client.md)

[Organisationseinstellungen](organizationSettings.md)

[Xrm.Utility.getGlobalContext](../getGlobalContext.md)

