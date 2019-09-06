---
title: DateFormattingInfo | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4e7d43fb-b6b7-4f1d-89e3-0b8157c9d2d9
---

# <a name="dateformattinginfo"></a>DateFormattingInfo

[!INCLUDE[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

[!INCLUDE [context-description](includes/dateformattinginfo-description.md)]

## <a name="properties"></a>Eigenschaften

## <a name="abbreviateddaynames"></a>abbreviatedDayNames

{ "So", "Mo", "Di", "Mi", "Do", "Fr", "Sa" }

**Typ**: `string`

## <a name="abbreviatedmonthgenitivenames"></a>abbreviatedMonthGenitiveNames

{ "Jan", "Feb", "Mär", "Apr", "Mai", "Jun", "Jul", "Aug", "Sep", "Okt", "Nov", "Dez", "" }

**Typ**: `string[]`

## <a name="abbreviatedmonthnames"></a>abbreviatedMonthNames

{ "Jan", "Feb", "Mär", "Apr", "Mai", "Jun", "Jul", "Aug", "Sep", "Okt", "Nov", "Dez", "" }

**Typ**: `string[]`

## <a name="amdesignator"></a>amDesignator

"AM"

**Typ**: `string`

## <a name="calendar"></a>Kalender

**Typ**: `object`

Das `calendar`-Objekt hat die folgenden Eigenschaften:

|Name|Typ|Beschreibung|
|--|--|--|
|`algorithmType`|`number`|1|
|`calendarType`|`number`|1|
|`maxSupportedDateTime`|`Date`|"/Date(253402300799999)/"|
|`minSupportedDateTime`|`Date`|"/Date(-62135568000000)/"|
|`twoDigitYearMax`|`number`|2029|

## <a name="calendarweekrule"></a>calendarWeekRule

0

**Typ**: `number`

## <a name="dateseparator"></a>dateSeparator

"/"

**Typ**: `string`

## <a name="daynames"></a>dayNames

{ "Sonntag", "Montag", "Dienstag", "Mittwoch", "Donnerstag", "Freitag", "Samstag" }

**Typ**: `string[]`

## <a name="firstdayofweek"></a>firstDayOfWeek

**Typ**: `number`

Die `firstDayOfWeek`-Eigenschaft kann auf einen der folgenden Werte festgelegt werden:

|Value|Bedeutung|
|--|--|
|0|Sonntag|
|1|Montag|
|2|Dienstag|
|3|Mittwoch|
|4|Donnerstag|
|5|Freitag|
|6|Samstag|

## <a name="fulldatetimepattern"></a>fullDateTimePattern

"tttt, MMMM t, jjjj s:mm:ss tt"

**Typ**: `string`

## <a name="longdatepattern"></a>longDatePattern

tttt, MMMM d, jjjj"

**Typ**: `string`

## <a name="longtimepattern"></a>longTimePattern

"hh:mm:ss:tt"

**Typ**: `string`

## <a name="monthdaypattern"></a>monthDayPattern

"MMMM tt"

**Typ**: `string`

## <a name="monthgenitivenames"></a>monthGenitiveNames

{ "Januar", "Februar", "März", ... "Dezember", "" }

**Typ**: `string[]`

## <a name="monthnames"></a>monthNames

{ "Januar", "Februar", "März", ... "Dezember", "" }

**Typ**: `string[]`

## <a name="pmdesignator"></a>pmDesignator

"PM"

**Typ**: `string`

## <a name="shortdatepattern"></a>shortDatePattern

"M/t/jjjj"

**Typ**: `string`

## <a name="shorttimepattern"></a>shortTimePattern

"h:mm tt"

**Typ**: `string`

## <a name="shortestdaynames"></a>shortestDayNames

{ "So", "Mo", "Di", "Mi", "Do", "Fr", "Sa" }

**Typ**: `string[]`

## <a name="sortabledatetimepattern"></a>sortableDateTimePattern

jjjj'-'MM'-'tt'T'HH':'mm':'ss"

**Typ**: `string`

## <a name="timeseparator"></a>timeSeparator

":"

**Typ**: `string`

## <a name="universalsortabledatetimepattern"></a>universalSortableDateTimePattern

"jjjj'-'MM'-'tt HH':'mm':'ss'Z'"

**Typ**: `string`

## <a name="yearmonthpattern"></a>yearMonthPattern

"MMMM jjjj"

**Typ**: `string`


### <a name="related-topics"></a>Verwandte Themen

[PowerApps-Komponentenframework-API-Referenz](../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../overview.md)