---
title: Funktion „Text“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Funktion „Text“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/14/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 452b5f11ede81c0e19a84026803ea60d7fd3f934
ms.sourcegitcommit: 26704369b17d2358a77cd4841bd70bbcca3384f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2019
ms.locfileid: "65521090"
---
# <a name="text-function-in-powerapps"></a>Funktion „Text“ in PowerApps
Konvertiert einen beliebigen Wert ein, und formatiert einen Zahl oder Datum/Uhrzeit-Wert in eine Zeichenfolge des Texts.

## <a name="description"></a>Beschreibung
Die Funktion **Text** formatiert eine Zahl oder einen Datums-/Uhrzeit-Wert auf der Grundlage eines dieser Argumenttypen:

* Eines vordefinierten Datums-/Uhrzeitformats, das Sie mithilfe der **DateTimeFormat**-Enumeration angeben. Für die Datums- und Uhrzeitwerte ist dieser Ansatz bevorzugt, wie es auf Sprache und Region des Benutzers automatisch angepasst wird.
* Ein benutzerdefiniertes Format, das eine Zeichenfolge mit Platzhaltern, die z. B. definieren umfasst, ob Zahlen zeigen an, ein Dezimaltrennzeichen und Datumsangaben den vollständigen Namen des Monats, den Monat als Abkürzung oder den Monat als Zahl zeigt. PowerApps unterstützt eine Teilmenge der von Microsoft Excel unterstützten Platzhalter. Der sprachplatzhalter in dieser Zeichenfolge gibt an, dass die Sprache, in dem die anderen Platzhalter interpretiert werden sollen. Wenn das benutzerdefinierte Format einen Punkt enthält, z. B. der Platzhalter für die Sprache-Format angibt, ob der Zeitraum ein Dezimaltrennzeichen (ja-JP) oder ein Tausendertrennzeichen Trennzeichen (es-ES).

Weitere Informationen finden Sie unter [Arbeiten mit Datums- und Uhrzeitangaben](../show-text-dates-times.md).

Die **Text** -Funktion kann auch einen beliebigen Datentyp aufweisen, eine Textdarstellung mit einem standardmäßigen Format konvertieren. Hiermit können Sie nicht-Text-Werte an textbasierten Funktionen übergeben werden z. B. [ **Len**](function-len.md), [ **rechts**](function-left-mid-right.md), und [  **"IsMatch"**](function-ismatch.md).

### <a name="predefined-datetime-formats"></a> Vordefinierte Datums-/Uhrzeitformate

| Vordefiniertes Format | Beschreibung |
| --- | --- |
| **DateTimeFormat.LongDate** |Vollständiges Jahr, Monat, Tag des Monats und Wochentag. Monatsnamen und Wochentage sind nicht abgekürzt. |
| **DateTimeFormat.LongDateTime** |Vollständiges Jahr, Monat, Tag des Monats und Wochentag plus Stunde (12-Stunden-Format), Minuten, Sekunden und AM/PM-Angabe. Monatsnamen und Wochentage sind nicht abgekürzt. |
| **DateTimeFormat.LongDateTime24** |Vollständiges Jahr, Monat, Tag des Monats und Wochentag plus Stunde (24-Stunden-Format), Minuten und Sekunden. Monatsnamen und Wochentage sind nicht abgekürzt. |
| **DateTimeFormat.LongTime** |Stunde (12-Stunden-Format), Minuten, Sekunden und AM/PM-Angabe. Identisch mit ShortTime. |
| **DateTimeFormat.LongTime24** |Stunde (24-Stunden-Format), Minuten, Sekunden. Identisch mit ShortTime24. |
| **DateTimeFormat.ShortDate** |Vierstellige Jahresangabe mit zweistellig angegebenem Monat und Tag im Monat. |
| **DateTimeFormat.ShortDateTime** |Vierstellige Jahresangabe mit zweistellig angegebenem Monat und Tag im Monat plus Stunde (12-Stunden-Format), Minuten, Sekunden und AM/PM-Angabe. |
| **DateTimeFormat.ShortDateTime24** |Vierstellige Jahresangabe mit zweistellig angegebenem Monat und Tag im Monat plus Stunde (24-Stunden-Format), Minuten und Sekunden. |
| **DateTimeFormat.ShortTime** |Stunde (12-Stunden-Format), Minuten, Sekunden und AM/PM-Angabe.  Identisch mit LongTime. |
| **DateTimeFormat.ShortTime24** |Stunde (24-Stunden-Format), Minuten und Sekunden.  Identisch mit LongTime24. |
| **DateTimeFormat.UTC** |Der Datums-/Uhrzeitwert wird basierend auf der Zeitzone des Benutzers in UTC konvertiert und gemäß dem ISO 8601-Standard formatiert. |

### <a name="number-placeholders"></a>Zahlplatzhalter

| Platzhalter | Beschreibung |
| --- | --- |
| **0** (*null*) |Zeigt nicht signifikante Nullen an, wenn eine Zahl weniger Stellen aufweist, als Nullen im Format festgelegt sind. Verwenden Sie beispielsweise das Format **#,00**, wenn Sie **8,9** im Format **8,90** anzeigen möchten. |
| **#** |Folgt den gleichen Regeln wie **0** (null). **Text** gibt jedoch keine zusätzlichen Nullen zurück, wenn die Zahl weniger Stellen auf beiden Seiten des Dezimaltrennzeichens aufweist, als #-Symbole im Format vorhanden sind. Beispielsweise wird **8,9** angezeigt, wenn das benutzerdefinierte Format **#,##** und die zu formatierende Zahl **8,9** ist. |
| **.** (*Punkt*) |Zeigt das Dezimaltrennzeichen in einer Zahl an. Hängt von der Sprache des benutzerdefinierten Formats; finden Sie unter [globalen apps](#global-apps) Weitere Details. |
| **.** (*Komma*) |Zeigt das Gruppierungstrennzeichen in einer Zahl an, häufig für Tausender verwendet. **Text** trennt Gruppen durch Punkte ab, wenn ein Format einen Punkt enthält, der von Zahlenzeichen (**#**) oder Nullen eingeschlossen ist. Hängt von der Sprache des benutzerdefinierten Formats; finden Sie unter [globalen apps](#global-apps) Weitere Details. |

Wenn eine Zahl mehr Stellen rechts vom Dezimaltrennzeichen aufweist, als Platzhalter im Format vorhanden sind, wird die Zahl zu der im Format definierten Anzahl Dezimalstellen gerundet. Wenn links vom Dezimaltrennzeichen mehr Stellen als Platzhalter vorhanden sind, werden die zusätzlichen Stellen angezeigt. Wenn das Format nur Zahlenzeichen (#) links vom Dezimaltrennzeichen aufweist, beginnen Zahlen kleiner als 1 mit dem Dezimaltrennzeichen (z. B. **,47**).

### <a name="date-and-time-placeholders"></a>Platzhalter für Datum und Uhrzeit

|   Platzhalter    |   Beschreibung                                                  |
|------------------|----------------------------------------------------------------|
|  **m**   |   Zeigt den Monat als Zahl ohne führende Null an.               |
|  **mm**  |   Zeigt den Monat als Zahl mit führender Null an, wenn das angebracht ist. |
|  **mmm** |   Zeigt den Monat als Abkürzung an (**Jan** bis **Dez**).          |
|                                                                                                   **mmmm**                                                                                                   |                                                                          Zeigt den Monat als vollständigen Namen an (**Januar** bis **Dezember**).                                                                           |
|                                                                                                    **d**                                                                                                     |                                                                                Zeigt den Tag als Zahl ohne führende Null an.                                                                                 |
|                                                                                                    **dd**                                                                                                    |                                                                         Zeigt den Tag als Zahl mit führender Null an, wenn das angebracht ist.                                                                          |
|                                                                                                   **ddd**                                                                                                    |                                                                              Zeigt den Tag als Abkürzung an (**So** bis **Sa**).                                                                              |
|                                                                                                   **dddd**                                                                                                   |                                                                            Zeigt den Tag als vollständigen Namen an (**Sonntag** bis **Samstag**).                                                                            |
|                                                                                                    **yy**                                                                                                    |                                                                                      Zeigt das Jahr als zweistellige Zahl an.                                                                                       |
|                                                                                                   **yyyy**                                                                                                   |                                                                                      Zeigt das Jahr als vierstellige Zahl an.                                                                                      |
|                                                                                                    **h**                                                                                                     |                                                                                Zeigt die Stunde als Zahl ohne führende Null an.                                                                                |
|   **hh** | Zeigt die Stunde als Zahl mit führender Null an, wenn das angebracht ist. Wenn das Format **AM** oder **PM** enthält, wird die Stunde basierend auf der 12-Stunden-Uhr angezeigt. Andernfalls wird die Stunde auf der 24-Stunden-Uhr basierend angezeigt. | 
|  **m**   |   Zeigt die Minute als Zahl ohne führende Null an.<br><br>Dieser Platzhalter muss unmittelbar die **h** oder **Hh** Code oder unmittelbar vor der **ss** code hingegen **Text** zurückgibt der Monat anstelle von Minuten.  |    
| **mm**   | Zeigt die Minute als Zahl mit führender Null an, wenn das angebracht ist.<br><br>Dieser Platzhalter muss unmittelbar die **h** oder **Hh** Platzhalter oder unmittelbar vor der **ss** Platzhalter. Andernfalls **Text** gibt den Monat anstelle von Minuten zurück. |                                                                                                                   
| **s**   |  Zeigt die Sekunde als Zahl ohne führende Null an.  |
| **ss**  | Zeigt die Sekunde als Zahl mit führender Null an, wenn das angebracht ist.                                                                        |
|                                                                                                    **f**                                                                                                     |                                                                                         Zeigt die Sekundenbruchteile an.                                                                                          |
|                                                                                    **AM/PM**, **eine / p**                                                                                    |               Zeigt die Stunde basierend auf dem 12-Stunden-Format an. **Text** gibt "AM" oder "a" für ein Timeout von Mitternacht bis Mittag und "PM" oder "p" für ein Timeout ab Mittag bis Mitternacht                |

### <a name="literal-placeholders"></a>Literalplatzhalter
Sie können jedes dieser Zeichen in Ihre Formatzeichenfolge aufnehmen.  Sie werden im Ergebnis von **Text** wie eingegeben angezeigt. Zusätzliche Zeichen sind für kommende Platzhalter reserviert, daher sollten Sie diese nicht verwenden.

| Zeichen | Beschreibung |
| --- | --- |
| Beliebiges Währungssymbol |Dollarzeichen, Centzeichen, Eurozeichen usw. |
| **+** |Pluszeichen |
| **(** |Öffnende Klammer |
| **:** |Doppelpunkt |
| **^** |Zirkumflexakzent (Caretzeichen) |
| **'** |Apostroph |
| **{** |Öffnende geschweifte Klammer |
| **<** |Kleiner-als-Zeichen |
| **=** |Gleichheitszeichen |
| **-** |Minuszeichen |
| **/** |Schrägstrich |
| **)** |Schließende Klammer |
| **&** |Kaufmännisches Und-Zeichen |
| **~** |Tilde |
| **}** |Schließende geschweifte Klammer |
| **>** |Größer-als-Zeichen |
| &nbsp; |Leerzeichen |

## <a name="global-apps"></a>Globale Anwendungen
Die Funktion **Text** ist global kompatibel. Sie „weiß“ für eine Vielzahl von Sprachen, wie Datumswerte, Uhrzeiten, Währungen und Zahlen ordnungsgemäß geschrieben werden. Für ihren Job benötigt sie zwei Informationen :

* **Die Sprache des benutzerdefinierten Formats:** Für Entwickler sollte wie ein benutzerdefiniertes Format werden interpretiert? Die Trennzeichen (**.** und **,**) haben in verschiedenen Sprachen verschiedene Bedeutungen. Wenn Sie ein benutzerdefiniertes Format angeben, können Sie sprachplatzhalter enthalten oder nutzen den Standardwert, der Sprache spiegelt wider, auf die Ihr Gerät festgelegt ist. Noch einfacher, können Sie eine der der [vordefinierte Datums-/Uhrzeitformate](#predefined-datetime-formats), die unabhängig von der Sprache sind.
* **Die Sprache des Ergebnisses:** Für Benutzer sollte in welcher Sprache das Ergebnis der Funktion angezeigt werden? Namen von Monaten und Wochentagen müssen in der entsprechenden Sprache für den Benutzer der app, die Sie angeben können, durch das Hinzufügen einer dritten, optionalen Argument, werden die **Text** Funktion. 

Für beide Sie die Sprache angeben, indem eine [Sprach-Tag](function-language.md#language-tags). Um die Liste der unterstützten Sprachen anzuzeigen, geben **Text (1234, "",)** in der Bearbeitungsleiste oder die **erweitert** Registerkarte den rechten Bereich, und scrollen Sie durch die Liste der Gebietsschemas, die für das dritte Argument vorgeschlagen.

### <a name="language-placeholder"></a>Sprachplatzhalter
Um die Sprache des benutzerdefinierten Formats anzugeben, verwenden Sie:

| Platzhalter | Beschreibung |
| --- | --- |
| **[$-*LanguageTag*]** |*Sprachkennzeichen* ist ein Sprachkennzeichen, wie es von der Funktion **Language** zurückgegeben wird. Er kann nur in die Sprache angeben (z. B. **[$-de]** für Englisch), oder sie können auch die Region angeben (z. B. **[$-En-GB]** zu Sprachangabe). |

Der Sprachplatzhalter kann an beliebiger Stelle im benutzerdefinierten Format auftreten, darf jedoch nur einmal angegeben werden.

Wenn Sie ein benutzerdefiniertes Format ohne sprachplatzhalter angeben und das Format von globalen Standpunkt aus mehrdeutig ist, wird automatisch das Sprachkennzeichen für Ihre aktuelle Sprache eingefügt.  

**[$-En-US]**  wird angenommen, wenn dieser Platzhalter nicht vorhanden ist, wenn Ihre app ausgeführt wird. 

> [!NOTE]
> In einer zukünftigen Version wird möglicherweise die Syntax dieser Platzhalter ändern, um Verwechslungen mit einem ähnlich, aber doch verschiedenen Platzhalter zu vermeiden, die Excel unterstützt.

### <a name="result-language-tag"></a>Sprachkennzeichen für das Ergebnis
Das Ergebnis des **Text** übersetzte Zeichenfolgen für die Monate, Wochentagen, und AM/PM-Angaben sowie die entsprechende Gruppe und Dezimaltrennzeichen enthält.

Standardmäßig verwendet **Text** die Sprache des Benutzers, der die Anwendung ausführt. Die Funktion **Language** gibt das Sprachkennzeichen für den aktuellen Benutzer zurück. Sie können diesen Standardwert überschreiben, indem Sie ein Sprachkennzeichen für das dritte Argument angeben **Text**.

## <a name="syntax"></a>Syntax
**Text**( *NumberOrDateTime*, *DateTimeFormatEnum* [, *ResultLanguageTag* ] )

* *NumberOrDateTime* : erforderlich. Die zu formatierende Zahl bzw. der zu formatierende Datums-/Uhrzeitwert.
* *DateTimeFormat*: erforderlich.  Ein Mitglied der **DateTimeFormat**-Enumeration.
* *ResultLanguageTag*: optional. Das Sprachkennzeichen, das für den Ergebnistext verwendet werden soll. Standardmäßig wird die Sprache des aktuellen Benutzers verwendet.

**Text**( *NumberOrDateTime*, *CustomFormat* [, *ResultLanguageTag* ] )

* *Number*: erforderlich. Die zu formatierende Zahl bzw. der zu formatierende Datums-/Uhrzeitwert.
* *CustomFormat*: erforderlich. Mindestens ein in doppelte Anführungszeichen gesetzter Platzhalter.
* *ResultLanguageTag*: optional. Das Sprachkennzeichen, das für den Ergebnistext verwendet werden soll. Standardmäßig wird die Sprache des aktuellen Benutzers verwendet.

**Text**( *AnyValue* )

* *AnyValue* : erforderlich. Wert, der in einem Textdarstellung zu konvertieren. Es wird ein Standardformat verwendet.

## <a name="examples"></a>Beispiele
Sofern nicht anders angegeben, wird der Benutzer diese Formeln ausführt befindet sich in den USA und hat Englisch als Sprache ausgewählt.  Die Funktion **Language** gibt „en-US“ zurück.

### <a name="number"></a>Number

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Text (&nbsp;1234.59,&nbsp;"###, #"&nbsp;)** |Formatiert die Zahl mit einer Dezimalstelle. |"1234,6" |
| **Text (&nbsp;8,9&nbsp;"#,000"&nbsp;)** |Füllt die Nachkommastellen der Zahl mit nachfolgenden Nullen auf, falls erforderlich. |"8,900" |
| **Text (&nbsp;0,631,&nbsp;"0,#"&nbsp;)** |Füllt den ganzzahligen Teil der Zahl mit führenden Nullen auf, falls erforderlich. |"0,6" |
| **Text(&nbsp;12;&nbsp;"#,0#"&nbsp;)**<br>**Text(&nbsp;1234,568;&nbsp;"#,0#"&nbsp;)** |Füllt die Nachkommastellen der Zahl mit Nullen für eine Dezimalstelle auf und schließt eine zweite Dezimalstelle ein, wenn sie angegeben wird. |"12,0"<br>"1234,57" |
| **Text(&nbsp;12000;&nbsp;"$ #.###"&nbsp;)**<br>**Text(&nbsp;1200000;&nbsp;"$&nbsp;#.###"&nbsp;)** |Fügt nach jeweils drei Stellen ein Tausendertrennzeichen ein und schließt ein Währungssymbol mit ein. |"$&nbsp;12.000"<br>"$&nbsp;1.200.000" |

### <a name="datetime"></a>Datum/Uhrzeit
* Um **2:37:47 PM** am **Montag, 23. November 2015**
* Pacific-Zeitzone der USA (UTC-8)

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Text( Now(); DateTimeFormat.LongDate )** |Formatiert als lange Datumszeichenfolge in der Sprache und dem Gebietsschema des aktuellen Benutzers. |"Montag, 23 November 2015" |
| **Text( Now(); DateTimeFormat.LongDateTime )** |Formatiert als lange Datums- und Uhrzeitzeichenfolge in der Sprache und dem Gebietsschema des aktuellen Benutzers und legt eine 12-Stunden-Uhr zugrunde. |"Montag, 23. November 2015 2:37:47 PM" |
| **Text( Now(); DateTimeFormat.LongTime24 )** |Formatiert als lange Uhrzeitzeichenfolge und legt eine 24-Stunden-Uhr zugrunde. |"14:37:47" |
| **Text( Now(); DateTimeFormat.ShortDate )** |Formatiert als kurze Datumszeichenfolge in der Sprache und dem Gebietsschema des aktuellen Benutzers. |"23.11.2015" |
| **Text( Now(); "d-mmm-yy" )** |Formate mit Platzhalterzeichen: <ul><li>**d** für eine einstellige oder zweistellige Angabe des Tags im Monat<li>**-** als literales Zeichen, das in das Ergebnis kopiert wird<li>**mmm** für eine aus drei Buchstaben bestehende Abkürzung des Monats<li>**-** als weiteres literales Zeichen, das in das Ergebnis kopiert wird<li>**yy** für eine zweistellige Kurzform für das Jahr</ul> |"23. Nov. 15" |
| **Text (1448318857000, "mmm. Dd, Yyyy (hh: mm: ss AM/PM) ")** | Zeigt einen Unix-Datum / Uhrzeit-Wert in von Menschen lesbaren Format an, wenn Sie den Wert des mit 1000 multiplizieren. | "November 23 2015 (02:47:37 PM)" |

### <a name="global-apps"></a>Globale Anwendungen

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Text (1234567,89; "[$-fr-FR] # ###, ## &euro;", "fr-FR")** | Zeigt Leerzeichen als Gruppierungszeichen, das Komma als Dezimaltrennzeichen, und **&euro;** als Währungssymbol. |"1&nbsp;234&nbsp;567,89 &euro;" |
| **Text(1234567,89; "[$-fr-FR]# ###,## &euro;")** | Wenn die Quelldaten das französische benutzerdefinierte des durch ein Komma als Dezimaltrennzeichen folgt, müssen Sie das Gebietsschema auf Französisch ändern und trennen die Argumente durch ein Semikolon statt ein Komma, um das gleiche Ergebnis wie oben beschrieben zu erhalten. |"1&nbsp;234&nbsp;567,89 &euro;" |
| **Text( Date(2016,1,31), "dddd mmmm d" )** |Gibt den Wochentag, Monat und Tag des Monats in der Sprache des aktuellen Benutzers zurück. Da keiner der Platzhalter sprachabhängig ist, gibt es keine Notwendigkeit für ein Textformat-Sprachkennzeichen. |"Samstag&nbsp;Januar&nbsp;31" |
| **Text( Date(2016,1,31), "dddd mmmm d", "es-ES" )** |Gibt den Wochentag, Monat und Tag des Monats in der Sprache „es-ES“ zurück. |"Domingo&nbsp;Enero&nbsp;31" |

### <a name="converting-values-to-text"></a>Konvertieren von Werten in text

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Text(&nbsp;1234567.89&nbsp;)** | Konvertiert eine Zahl in eine Zeichenfolge an. Es gibt keine Tausende Trennzeichen oder die Kontrolle über die Anzahl der Ziffern vor oder nach dem Dezimaltrennzeichen; Geben Sie zur präziseren Steuerung können zahlplatzhalter als zweites Argument ein. | "1234567.89" |
| **Text(&nbsp;DateTimeValue(&nbsp;"01/04/2003"&nbsp;)&nbsp;)** | Konvertiert einen Datum/Uhrzeit-Wert in eine Zeichenfolge des Texts an. Um die Konvertierung gesteuert werden, geben Sie entweder ein Mitglied der DateTimeFormat-Enumeration oder eine benutzerdefinierte Formatzeichenfolge ein. | "1/4/2003 12:00 UHR" |
| **Text (&nbsp;"true"&nbsp;)** | Konvertiert einen booleschen Wert in eine Zeichenfolge an. | "true" |
| **Text(&nbsp;GUID()&nbsp;)** | Konvertiert einen generierten GUID-Wert in eine Zeichenfolge an.  | "f8b10550-0f12-4f08-9aa3-bb10958bc3ff" |
| **Left (&nbsp;Text (&nbsp;GUID()&nbsp;),&nbsp;4&nbsp;)** | Gibt die ersten vier Zeichen eine generierte GUID zurück. | "2d9c" | 
