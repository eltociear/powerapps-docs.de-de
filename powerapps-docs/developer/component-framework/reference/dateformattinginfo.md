---
title: DateFormattingInfo | Microsoft-Dokumentation
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4e7d43fb-b6b7-4f1d-89e3-0b8157c9d2d9
ms.openlocfilehash: fb6dc5c67cc0ea031ab4e264d282458163ee46a0
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72344828"
---
# <a name="dateformattinginfo"></a>DateFormattingInfo

[!INCLUDE [context-description](includes/dateformattinginfo-description.md)]

## <a name="available-for"></a>Verfügbar für 

Modellgesteuerte Apps

## <a name="properties"></a>Eigenschaften

### <a name="abbreviateddaynames"></a>abbreviatedDayNames

{"Sun", "Mon", "di", "Wed", "Do", "Fri", "Sat"}

**Typ**: `string`

### <a name="abbreviatedmonthgenitivenames"></a>abbreviatedMonthGenitiveNames

{"Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec", ""}

**Typ**: `string[]`

### <a name="abbreviatedmonthnames"></a>abbreviatedMonthNames

{"Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec", ""}

**Typ**: `string[]`

### <a name="amdesignator"></a>amDesignator

Uhr

**Typ**: `string`

### <a name="calendar"></a>Kalender

**Typ**: `object`

Das `calendar`-Objekt enthält die folgenden Eigenschaften:

|Name|Typ|Beschreibung|
|--|--|--|
|`algorithmType`|`number`|1|
|`calendarType`|`number`|1|
|`maxSupportedDateTime`|`Date`|"/Date(253402300799999)/"|
|`minSupportedDateTime`|`Date`|"/Date(-62135568000000)/"|
|`twoDigitYearMax`|`number`|2029|

### <a name="calendarweekrule"></a>CalendarWeekRule

**Typ**: `number`

### <a name="dateseparator"></a>dateseparser

"/"

**Typ**: `string`

### <a name="daynames"></a>DayNames

{"Sunday", "Montag", "Dienstag", "Mittwoch", "Donnerstag", "Freitag", "Samstag"}

**Typ**: `string[]`

### <a name="firstdayofweek"></a>FirstDayOfWeek

**Typ**: `number`

Die `firstDayOfWeek`-Eigenschaft kann auf einen der folgenden Werte festgelegt werden:

|Value|D.h.|
|--|--|
|0|Sunday|
|1|Pfingst|
|2|Mitteilte|
|3|Mittwochs|
|4|Mitteilte|
|5|Am|
|6|Saturday|

### <a name="fulldatetimepattern"></a>fullDateTimePattern

"dddd, MMMM d, JJJJ h:mm: ss tt"

**Typ**: `string`

### <a name="longdatepattern"></a>longDatePattern

dddd, MMMM d, yyyy "

**Typ**: `string`

### <a name="longtimepattern"></a>longTimePattern

"hh: mm: ss tt"

**Typ**: `string`

### <a name="monthdaypattern"></a>monthDayPattern

"MMMM dd"

**Typ**: `string`

### <a name="monthgenitivenames"></a>MonthGenitiveNames

{"January", "February", "March",...  "Dezember", ""}

**Typ**: `string[]`

### <a name="monthnames"></a>MonthNames

{"January", "February", "March",...  "Dezember", ""}

**Typ**: `string[]`

### <a name="pmdesignator"></a>pmDesignator

14:

**Typ**: `string`

### <a name="shortdatepattern"></a>shortDatePattern

"M/d/yyyy"

**Typ**: `string`

### <a name="shorttimepattern"></a>shortTimePattern

"h:mm tt"

**Typ**: `string`

### <a name="shortestdaynames"></a>ShortestDayNames

{"Su", "Mo", "tu", "We", "th", "fr", "SA"}

**Typ**: `string[]`

### <a name="sortabledatetimepattern"></a>sortableDateTimePattern

yyyy'-' mm'-' dd ' HH ': ' mm ': ' ss '

**Typ**: `string`

### <a name="timeseparator"></a>timeseparser

":"

**Typ**: `string`

### <a name="universalsortabledatetimepattern"></a>universalSortableDateTimePattern

"yyyy'-' mm'-' dd HH ': ' mm ': ' ss' Z '"

**Typ**: `string`

### <a name="yearmonthpattern"></a>yearMonthPattern

"MMMM yyyy"

**Typ**: `string`


### <a name="related-topics"></a>Verwandte Themen

[API-Referenz für das powerapps-Komponenten Framework](../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../overview.md)