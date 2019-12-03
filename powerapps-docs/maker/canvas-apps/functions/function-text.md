---
title: Funktion „Text“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktion "Text" in powerapps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/14/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9ebc28c72d1d25c4a6e85e25a14c8addaf457318
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74729975"
---
# <a name="text-function-in-power-apps"></a>Funktion "Text" in powerapps
Konvertiert einen beliebigen Wert und formatiert eine Zahl oder einen Datums-/Uhrzeitwert in eine Text Zeichenfolge.

## <a name="description"></a>Beschreibung
Die Funktion **Text** formatiert eine Zahl oder einen Datums-/Uhrzeit-Wert auf der Grundlage eines dieser Argumenttypen:

* Eines vordefinierten Datums-/Uhrzeitformats, das Sie mithilfe der **DateTimeFormat**-Enumeration angeben. Für Datums-und Uhrzeitwerte wird dieser Ansatz bevorzugt, da er sich automatisch an die Sprache und Region der einzelnen Benutzer anpasst.
* Ein benutzerdefiniertes Format, das eine Zeichenfolge mit Platzhaltern umfasst, die z. b. festlegen, ob Zahlen ein Dezimaltrennzeichen und Datumsangaben den vollständigen Namen des Monats, den Monat als Abkürzung oder den Monat als Zahl anzeigen. Powerapps unterstützt eine Teilmenge der Platzhalter, die Microsoft Excel verwendet. In dieser Zeichenfolge gibt der sprach Platzhalter die Sprache an, in der die anderen Platzhalter interpretiert werden sollen. Wenn das benutzerdefinierte Format z. b. einen Punkt enthält, gibt der Platzhalter für den sprach Format an, ob der Punkt ein Dezimaltrennzeichen (ja-JP) oder ein Tausender Trennzeichen (es-es) ist.

Weitere Informationen finden Sie unter [Arbeiten mit Datums- und Uhrzeitangaben](../show-text-dates-times.md).

Die **Text** -Funktion kann auch jeden Datentyp in eine Text Darstellung mit einem Standardformat konvertieren. Verwenden Sie diese Eigenschaft, um nicht-Text-Werte an textbasierte Funktionen wie z. b. [**len**](function-len.md), [**right**](function-left-mid-right.md)und [**IsMatch**](function-ismatch.md)zu übergeben.

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
| **.** (*Punkt*) |Zeigt das Dezimaltrennzeichen in einer Zahl an. Hängt von der Sprache des benutzerdefinierten Formats ab. Weitere Informationen finden Sie unter [globale apps](#global-apps) . |
| **.** (*Komma*) |Zeigt das Gruppierungstrennzeichen in einer Zahl an, häufig für Tausender verwendet. **Text** trennt Gruppen durch Punkte ab, wenn ein Format einen Punkt enthält, der von Zahlenzeichen ( **#** ) oder Nullen eingeschlossen ist. Hängt von der Sprache des benutzerdefinierten Formats ab. Weitere Informationen finden Sie unter [globale apps](#global-apps) . |

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
|  **m**   |   Zeigt die Minute als Zahl ohne führende Null an.<br><br>Dieser Platzhalter muss direkt nach dem **h** -oder **HH** -Code oder direkt vor dem **SS** -Code angezeigt werden. Andernfalls gibt **Text** den Monat anstelle von Minuten zurück.  |    
| **mm**   | Zeigt die Minute als Zahl mit führender Null an, wenn das angebracht ist.<br><br>Dieser Platzhalter muss direkt nach dem **h** -oder **HH** -Platzhalter oder direkt vor dem **SS** -Platzhalter angezeigt werden. Andernfalls gibt **Text** den Monat anstelle von Minuten zurück. |                                                                                                                   
| **s**   |  Zeigt die Sekunde als Zahl ohne führende Null an.  |
| **ss**  | Zeigt die Sekunde als Zahl mit führender Null an, wenn das angebracht ist.                                                                        |
|                                                                                                    **f**                                                                                                     |                                                                                         Zeigt die Sekundenbruchteile an.                                                                                          |
|                                                                                    **Am/pm**, **a/p**                                                                                    |               Zeigt die Stunde basierend auf dem 12-Stunden-Format an. **Text** gibt "am" oder "a" für Uhrzeiten von Mitternacht bis Mittag und "PM" oder "p" für Uhrzeiten von Mittag bis Mitternacht zurück.                |

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

* **Die Sprache des benutzerdefinierten Formats:** Wie soll ein benutzerdefiniertes Format für Ersteller interpretiert werden? Die Trennzeichen ( **.** und **,** ) haben in verschiedenen Sprachen verschiedene Bedeutungen. Wenn Sie ein benutzerdefiniertes Format angeben, können Sie einen sprach Platzhalter einschließen oder den Standardwert verwenden, der die Sprache angibt, in der das Gerät festgelegt ist. Noch einfacher können Sie eines der [vordefinierten Datums-/Uhrzeitformate](#predefined-datetime-formats)verwenden, die sprach agnostisch sind.
* **Die Sprache des Ergebnisses:** In welcher Sprache soll das Ergebnis der Funktion angezeigt werden? Namen von Monaten und Wochentagen müssen sich in der entsprechenden Sprache für den Benutzer der APP befinden, den Sie durch Hinzufügen eines dritten optionalen Arguments zur **Text** Funktion angeben können. 

Für beide müssen Sie die Sprache mithilfe eines [sprach Tags](function-language.md#language-tags)angeben. Wenn Sie die Liste der unterstützten Sprachen anzeigen möchten, geben Sie **Text (1234, "",)** in die Bearbeitungs Leiste oder die Registerkarte " **erweitert** " im rechten Bereich ein, und Scrollen Sie dann durch die Liste der Gebiets Schemas, die für das dritte Argument vorgeschlagen werden.

### <a name="language-placeholder"></a>Sprach Platzhalter
Um die Sprache des benutzerdefinierten Formats anzugeben, verwenden Sie:

| Platzhalter | Beschreibung |
| --- | --- |
| **[$-*LanguageTag*]** |*Sprachkennzeichen* ist ein Sprachkennzeichen, wie es von der Funktion **Language** zurückgegeben wird. Es kann nur die Sprache angeben (z. b. **[$-en]** für Englisch), oder es kann auch die Region angeben (z. b. **[$-en-GB]** , um Großbritannien weiter anzugeben). |

Der Sprachplatzhalter kann an beliebiger Stelle im benutzerdefinierten Format auftreten, darf jedoch nur einmal angegeben werden.

Wenn Sie ein benutzerdefiniertes Format ohne sprach Platzhalter angeben und das Format aus globaler Sicht nicht eindeutig ist, wird das Sprachtag für die aktuelle Sprache automatisch eingefügt.  

**[$-en-US]** wird angenommen, wenn dieser Platzhalter nicht vorhanden ist, wenn Ihre APP ausgeführt wird. 

> [!NOTE]
> In einer zukünftigen Version kann sich die Syntax dieses Platzhalters ändern, um Verwechslungen mit einem ähnlichen, aber unterschiedlichen Platzhalter zu vermeiden, der von Excel unterstützt wird.

### <a name="result-language-tag"></a>Sprachkennzeichen für das Ergebnis
Das Ergebnis von **Text** umfasst übersetzte Zeichen folgen für Monate, Wochentage und am/pm-Bezeichnungen sowie die entsprechenden Gruppen-und Dezimaltrennzeichen.

Standardmäßig verwendet **Text** die Sprache des Benutzers, der die Anwendung ausführt. Die Funktion **Language** gibt das Sprachkennzeichen für den aktuellen Benutzer zurück. Sie können diesen Standardwert überschreiben, indem Sie ein Sprachtag für das dritte Argument für **Text**angeben.

## <a name="syntax"></a>Syntax
**Text**(" *numordatetime*", " *datetimeformaterum* " [, *resultlanguagetag* ])

* *Numordatetime* : erforderlich. Die zu formatierende Zahl bzw. der zu formatierende Datums-/Uhrzeitwert.
* *DateTimeFormat*: erforderlich.  Ein Mitglied der **DateTimeFormat**-Enumeration.
* *ResultLanguageTag*: optional. Das Sprachkennzeichen, das für den Ergebnistext verwendet werden soll. Standardmäßig wird die Sprache des aktuellen Benutzers verwendet.

**Text**( *databordatetime*, *CustomFormat* [, *resultlanguagetag* ])

* *Zahl*: erforderlich. Die zu formatierende Zahl bzw. der zu formatierende Datums-/Uhrzeitwert.
* *CustomFormat*: erforderlich. Mindestens ein in doppelte Anführungszeichen gesetzter Platzhalter.
* *ResultLanguageTag*: optional. Das Sprachkennzeichen, das für den Ergebnistext verwendet werden soll. Standardmäßig wird die Sprache des aktuellen Benutzers verwendet.

**Text**( *anyvalue* )

* *Anyvalue* : erforderlich. Der Wert, der in eine Textdarstellung konvertiert werden soll. Ein Standardformat wird verwendet.

## <a name="examples"></a>Beispiele
Sofern nicht anders angegeben, befindet sich der Benutzer, der diese Formeln durchführt, in der USA und hat Englisch als Sprache ausgewählt.  Die Funktion **Language** gibt „en-US“ zurück.

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
| **Text (1448318857 * 1000, "MMM". DD, JJJJ (hh: mm: SS am/pm))** | Zeigt einen UNIX-Datums-/Uhrzeitwert in einem von menschenlesbaren Format an, wenn Sie den Quellwert mit 1.000 multiplizieren. | "Nov. 23, 2015 (02:47:37 Uhr)" |

### <a name="global-apps"></a>Globale Anwendungen

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Text (1234567.89, "[$-fr-FR] # # # #, # # &euro;", "fr-FR")** | Zeigt ein Leerzeichen als Gruppierungs Trennzeichen, das Komma als Dezimaltrennzeichen und **&euro;** als Währungssymbol an. |"1&nbsp;234&nbsp;567, 89 &euro;" |
| **Text (1234567, 89; "[$-fr-FR] # # # #, # # &euro;")** | Wenn die Quelldaten dem französischen Französisch entsprechen und ein Komma als Dezimaltrennzeichen verwendet wird, müssen Sie das Gebiets Schema in Französisch ändern und die Argumente mit einem Semikolon anstelle eines Kommas trennen, um das gleiche Ergebnis wie oben zu erhalten. |"1&nbsp;234&nbsp;567, 89 &euro;" |
| **Text( Date(2016,1,31), "dddd mmmm d" )** |Gibt den Wochentag, Monat und Tag des Monats in der Sprache des aktuellen Benutzers zurück. Da keiner der Platzhalter sprachabhängig ist, gibt es keine Notwendigkeit für ein Textformat-Sprachkennzeichen. |"Samstag&nbsp;Januar&nbsp;31" |
| **Text( Date(2016,1,31), "dddd mmmm d", "es-ES" )** |Gibt den Wochentag, Monat und Tag des Monats in der Sprache „es-ES“ zurück. |"Domingo&nbsp;enero&nbsp;31" |

### <a name="converting-values-to-text"></a>Werte werden in Text umgerechnet

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Text (&nbsp;1234567,89&nbsp;)** | Konvertiert eine Zahl in eine Zeichenfolge. Es gibt keine Tausender Trennzeichen oder Kontrolle über die Anzahl der Ziffern vor oder nach dem Dezimaltrennzeichen. Wenn Sie mehr Kontrolle haben, stellen Sie zahlen Platzhalter als zweites Argument bereit. | "1234567,89" |
| **Text (&nbsp;dateTimeValue (&nbsp;"01/04/2003"&nbsp;)&nbsp;)** | Konvertiert einen Datums-/Uhrzeitwert in eine Text Zeichenfolge. Um die Konvertierung zu steuern, stellen Sie entweder einen Member der DateTimeFormat-Enumeration oder eine benutzerdefinierte Format Zeichenfolge bereit. | "1/4/2003 12:00 Uhr" |
| **Text (&nbsp;true&nbsp;)** | Konvertiert einen booleschen Wert in eine Zeichenfolge. | Fall |
| **Text (&nbsp;GUID ()&nbsp;)** | Konvertiert einen generierten GUID-Wert in eine Zeichenfolge.  | "f8b10550-0f12-4f08-9aa3-bb10958bc3ff" |
| **Left (&nbsp;Text (&nbsp;GUID ()&nbsp;),&nbsp;4&nbsp;)** | Gibt die ersten vier Zeichen einer generierten GUID zurück. | "2d9c" | 
