---
title: Funktionen „DateValue“, „TimeValue“ und „DateTimeValue“ | Microsoft-Dokumentation
description: Referenzinformationen, Syntax und Beispiele für die Funktionen "DateValue", "TimeValue" und "dateTimeValue" in powerapps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/08/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2fc1a91b4468926ee98351f79d7ce2e84133aa46
ms.sourcegitcommit: 7d3caf698d367a56af9e16c43af8005adb9f87cd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987243"
ms.PowerAppsDecimalTransform: true
---
# <a name="datevalue-timevalue-and-datetimevalue-functions-in-power-apps"></a>Funktionen "DateValue", "TimeValue" und "dateTimeValue" in powerapps

Konvertiert ein Datum, eine Uhrzeit oder beides in einer *Zeichenfolge* in einen *Datums-/Uhrzeitwert* .

## <a name="description"></a>Beschreibung

- Die **DateValue** -Funktion konvertiert eine *Datums Zeichenfolge* (z. b. "10/01/2014") in einen *Datums-/Uhrzeitwert* .

- Die **TimeValue** -Funktion konvertiert eine *Zeit Zeichenfolge* (z. b. "12:15 pm") in einen *Datums-/Uhrzeitwert* .

- Die **dateTimeValue** -Funktion konvertiert eine *Datums-und Uhrzeit Zeichenfolge* (z. b. "January 10, 2013 12:13 am") in einen *Datums-/Uhrzeitwert* .

Die **DateValue** -Funktion ignoriert alle Zeit Informationen in der Datums Zeichenfolge, und die **TimeValue** -Funktion ignoriert alle Datumsinformationen in der Zeit Zeichenfolge.

> [!NOTE]
> Die Funktionen DateValue, TimeValue und dateTimeValue verwenden standardmäßig die Sprache aus den Einstellungen des aktuellen Benutzers. Sie können es überschreiben, um sicherzustellen, dass Zeichen folgen ordnungsgemäß interpretiert werden. Beispielsweise wird "10/1/1920" als *1<sup>.</sup> Oktober* in "*en*" und als 10. *Januar in<sup>th</sup>*  "*fr*" interpretiert.

Datumsangaben müssen eines der folgenden Formate aufweisen:

- Mm/dd/yyyy oder mm-dd-yyyy
- Dd/mm/yyyy oder dd-mm-yyyy
- Yyyy/mm/dd oder yyyy-mm-dd
- Mm/dd/yy oder mm-dd-yy
- Dd/mm/yy oder dd-mm-yy
- TT Mon JJJJ
- Monat TT, JJJJ

Zum Konvertieren aus numerischen Date-, month-und Year-Komponenten lesen Sie [Date](function-date-time.md). <br>
Zum Konvertieren von numerischen Stunden-, Minuten-und zweiten Komponenten lesen Sie die [Zeit](function-date-time.md).

Weitere Informationen finden Sie unter:

- [Arbeiten mit Datum und Uhrzeit](../show-text-dates-times.md).
- [Datums-/Uhrzeit-und Datentypen](data-types.md#date-time-and-datetime).

## <a name="syntax"></a>Syntax

**DateValue**( *String* [; *Language* ])<br>
**DateTimeValue**( *String* [; *Language* ])<br>
**TimeValue**( *String* [; *Language* ])

* *Zeichenfolge*: erforderlich. Eine Textzeichenfolge, die einen Datum-, Uhrzeit- oder einen Datum/Uhrzeit-Wert enthält.
* *Sprache*: optional. Eine sprach Zeichenfolge, z. b., wird von den ersten zwei Zeichen aus der [Language](function-language.md) -Funktion zurückgegeben.  Wenn keine Angabe erfolgt, wird die Sprache der Einstellungen des aktuellen Benutzers verwendet.  

## <a name="examples"></a>Beispiele

### <a name="datevalue"></a>DateValue

Wenn Sie **10/11/2014** in ein Texteingabe-Steuerelement mit dem Namen **StartDate**eingeben, und legen Sie dann die [Text](../controls/properties-core.md) -Eigenschaft einer Bezeichnung auf die folgenden Formeln fest:

- Konvertiert ein Datum aus einer Zeichenfolge in das Gebiets Schema des Benutzers und zeigt das Ergebnis als langes Datum an.

    ```powerapps-comma
    Text( DateValue( Startdate.Text ); DateTimeFormat.LongDate )
    ```

    Auf dem Gebiets Schema " **en** " wird die Bezeichnung **Samstag, 11. Oktober 2014**angezeigt.
  
    > [!NOTE]
    > Sie können mehrere Optionen mit der **DateTimeFormat** -Enum verwenden. Zum Anzeigen einer Liste von Optionen geben Sie den Parameter ein, gefolgt von einem Punkt oder Punkt ( **.** ) in der Bearbeitungs Leiste oder in der Funktionsreferenz für den [ **Text** ](function-text.md).

- Konvertieren Sie das Datum aus einer Zeichenfolge im französischen Gebiets Schema, und zeigen Sie das Ergebnis als langes Datum an. In diesem Beispiel werden die Monate und der Tag des Monats anders als Englisch interpretiert.

    ```powerapps-comma
    Text( DateValue( Startdate.Text; "fr" ); DateTimeFormat.LongDate )
    ```
  
    Auf dem Gebiets Schema " **en** " wird die Bezeichnung **Montag, 10. November 2014**angezeigt.

Wenn Sie stattdessen den **20. Oktober 2014 eingegeben haben** :

- Konvertieren Sie ein Datum aus einer Zeichenfolge in das Gebiets Schema des Benutzers, und berechnen Sie die Differenz zwischen zwei Tagen (in Tagen).

    ```powerapps-comma
    DateDiff( DateValue( Startdate.Text ); Today() )
    ```
  
    Auf dem Gebiets Schema " **en** " wird die Bezeichnung **9**angezeigt, die die Anzahl der Tage zwischen dem 11. und dem 20. Oktober angibt. Die [DateDiff](function-dateadd-datediff.md) -Funktion kann auch den Unterschied in Monaten, Quartalen oder Jahren anzeigen.

### <a name="datetimevalue"></a>DateTimeValue

Wenn Sie **10/11/2014 1:50:24.765 pm** in ein Texteingabe-Steuerelement mit dem Namen **Start**eingegeben haben, legen Sie die [Text](../controls/properties-core.md) -Eigenschaft einer Bezeichnung auf die folgende Formel fest:

- Konvertiert eine Datums-und Uhrzeit Zeichenfolge im aktuellen Gebiets Schema.
 
    ```powerapps-comma
    Text( DateTimeValue( Start.Text ); DateTimeFormat.LongDateTime )
    ```    
    
    Auf dem Gebiets Schema " **en** " wird die Bezeichnung **Samstag, 11. Oktober 2014 1:50:24 Uhr**angezeigt.
  
  > [!NOTE]
  > Sie können mehrere Optionen mit der **DateTimeFormat** -Enum verwenden. Zum Anzeigen einer Liste von Optionen geben Sie den Parameter ein, gefolgt von einem Punkt oder Punkt ( **.** ) in der Bearbeitungs Leiste oder in der Funktionsreferenz für den [ **Text** ](function-text.md).

- Konvertieren Sie eine Datums-und Uhrzeit Zeichenfolge in das französische Gebiets Schema. Monat und Tag des Monats werden unterschiedlich interpretiert.

    ```powerapps-comma
    Text( DateTimeValue( Start.Text; "fr"); DateTimeFormat.LongDateTime )
    ```
  
    Auf dem Gebiets Schema " **en** " ist die Bezeichnung **Montag, 10. November 2014 1:50:24 Uhr**.

- Konvertieren Sie eine Datums-und Uhrzeit Zeichenfolge in das Gebiets Schema des Benutzers, und zeigen Sie das Ergebnis mit einer Sekundenbruchteile an.

    ```powerapps-comma
    Text( DateTimeValue( Start.Text ); "dddd, mmmm dd, yyyy hh:mm:ss.fff AM/PM" )
    ```
  
    Auf dem Gebiets Schema " **en** " wird die Bezeichnung **Samstag, 11. Oktober, 2014 01:50:24.765 Uhr**angezeigt.
  
    Als Alternative können Sie **hh: mm: SS. f** oder **hh: mm: SS. FF** angeben, um die Uhrzeit auf die nächst<sup>gelegene 10.</sup> <sup>oder 100. Sekunde einer Sekunde</sup> zu runden.

### <a name="timevalue"></a>TimeValue

Benennen Sie ein Texteingabe-Steuerelement **finishedat**, und legen Sie die [Text](../controls/properties-core.md) -Eigenschaft einer Bezeichnung auf diese Formel fest:

```powerapps-comma
If( TimeValue( FinishedAt.Text ) < TimeValue( "5:00:00.000 PM" ); 
    "You made it!"; 
    "Too late!"
)
```

- Wenn Sie im **finishedat** -Steuerelement **4:59:59.999 PM** eingeben, zeigt die Bezeichnung "*Sie haben Sie!* "
- Wenn Sie im **finishedat** -Steuerelement **5:00:00.000 pm** eingeben, zeigt die Bezeichnung "*zu spät!* " an.
