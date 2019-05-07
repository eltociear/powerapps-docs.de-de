---
title: IsMatch, Match und MatchAll-Funktionen | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die IsMatch, Match und MatchAll-Funktionen in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 01/15/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7141d3b9a2ba6bf18bffe1756d0d7de048606cad
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61563262"
ms.PowerAppsDecimalTransform: true
---
# <a name="ismatch-match-and-matchall-functions-in-powerapps"></a>IsMatch, Match und MatchAll-Funktionen in PowerApps
Testet, ob eine Übereinstimmung oder extrahiert Teile einer Textzeichenfolge, die basierend auf einem Muster.

## <a name="description"></a>Beschreibung
Die **IsMatch**-Funktion prüft, ob eine Textzeichenfolge mit einem Muster übereinstimmt, das normale Zeichen, vordefinierte Muster oder einen [regulären Ausdruck](#regular-expressions) enthält.  Die **Übereinstimmung** und **MatchAll** Funktionen zurück, was abgeglichen wurde, einschließlich der untergeordneten Übereinstimmungen,.  

Verwenden Sie **IsMatch**,um zu überprüfen, was ein Benutzer in ein **[Texteingabe](../controls/control-text-input.md)**-Steuerelement eingegeben hat. Beispielsweise können Sie überprüfen, ob der Benutzer eine gültige E-Mail-Adresse eingegeben hat, bevor das Ergebnis in der Datenquelle gespeichert wird. Wenn der Eintrag nicht mit Ihren Kriterien übereinstimmt, fügen Sie andere Steuerelemente hinzu, die den Benutzer zur Korrektur der Eingabe auffordern.

Verwendung **entsprechen** die erste Textzeichenfolge zu extrahieren, die mit einem Muster übereinstimmt und **MatchAll** alle Textzeichenfolgen extrahieren, die mit übereinstimmen. Sie können auch untergeordnete Übereinstimmungen, um komplexe Zeichenfolgen zu analysieren extrahieren.   

**Entsprechen** gibt einen Datensatz mit Informationen für die erste Übereinstimmung gefunden, und **MatchAll** gibt eine Tabelle mit Datensätzen für jede gefundene Übereinstimmung zurück. Der Datensatz oder Datensätze enthalten:

| Spalte | Typ | Beschreibung |
|----|----|----|
| *mit dem Namen Sub&#8209;übereinstimmen oder sub&#8209;entspricht* | Text | Jede benannte untergeordnete Übereinstimmung müssen eine eigene Spalte. Erstellen Sie eine benannte untergeordnete Übereinstimmung mithilfe **(?&lt; *Namen*&gt;**... **)** im regulären Ausdruck. Bei eine benannten untergeordneten Übereinstimmung den gleichen Namen wie eine der vordefinierten Spalten (siehe unten), die untergeordnete Übereinstimmung hat Vorrang vor, und eine Warnung generiert. Um diese Warnung zu vermeiden, benennen Sie die untergeordnete Übereinstimmung. |
| **FullMatch** | Text | Alle der Textzeichenfolge, die abgeglichen wurde. |
| **StartMatch** | Number | Die Anfangsposition der Übereinstimmung in der eingegebenen Text-Zeichenfolge. Das erste Zeichen der Zeichenfolge gibt 1 zurück. | 
| **SubMatches** | Einspaltige Tabelle von Text (Spalte **Wert**) | Die Tabelle, benannte und unbenannte untergeordnete Übereinstimmungen in der Reihenfolge, in der sie in den regulären Ausdruck angezeigt werden. Im Allgemeinen benannten untergeordneten Übereinstimmungen sind einfacher zu verwenden und empfohlen. Verwenden der [ **ForAll** ](function-forall.md) Funktion oder [ **letzten**](function-first-last.md)( [ **FirstN**](function-first-last.md)() **...**  )) Funktionen zum Arbeiten mit einer einzelnen untergeordneten Übereinstimmung. Wenn keine untergeordneten Übereinstimmung im regulären Ausdruck definiert sind, werden in dieser Tabelle vorhanden, jedoch leer. |

Diese Funktionen unterstützen [ **"MatchOptions"**](#match-options). Standardmäßig: 
- Diese Funktionen führen eine Übereinstimmung der Groß-/Kleinschreibung beachtet. Verwendung **IgnoreCase** Groß-/Kleinschreibung der Übereinstimmungen ausführen.    
- **"IsMatch"** entspricht die gesamte Zeichenfolge (**abschließen** MatchOption), während **entsprechen** und **MatchAll** Suche nach einer Übereinstimmung an einer beliebigen Stelle in der Textzeichenfolge ( **Enthält** MatchOption). Verwendung **abschließen**, **Contains**, **BeginsWith**, oder **"EndsWith"** je nach Bedarf für Ihr Szenario.

**IsMatch** gibt *TRUE* zurück, wenn die Zeichenfolge mit dem Muster übereinstimmt, oder *FALSE*, Wenn dies nicht der Fall ist. **Entsprechen** gibt *leere* , wenn keine Übereinstimmung gefunden wird, die getestet werden kann, mit der [ **"isblank"** ](function-isblank-isempty.md) Funktion. **MatchAll** eine leere Tabelle zurückgibt, wenn keine Übereinstimmung gefunden wird, die getestet werden kann, mit der [ **"isEmpty"** ](function-isblank-isempty.md) Funktion.

Bei Verwendung von **MatchAll** um eine Zeichenfolge zu teilen, sollten Sie verwenden die **[Split](function-split.md)** -Funktion, die Verwendung einfacher und schneller ist.

## <a name="patterns"></a>Muster
Der Schlüssel für die Verwendung dieser Funktionen ist das Muster, beschreiben. Sie beschreiben das Muster als Testzeichenfolge als Kombination aus Folgendem:

* Normale Zeichen, z.B. **"Abc"** oder **"123"**
* Vordefinierte Muster, z.B. **Letter** (Buchstabe), **MultipleDigits** (mehrere Ziffern) oder **E-Mail**. (Die **Match**-Enumeration definiert diese Muster.)
* Reguläre Ausdrücke-Fehlercodes, wie z. B. **"\d+\s+\d+"** oder **"[a-Z] +"**.

Kombinieren Sie diese Elemente mithilfe der [Operator für zeichenfolgenverkettung **&** ](operators.md). **"abc" & Digit & "\s+"** ist beispielsweise ein gültiges Muster, das den Zeichen „a“, „b“ und „c“ gefolgt von einer Ziffer zwischen 0 und 9 entspricht, auf die mindestens ein Leerzeichen folgt.

### <a name="ordinary-characters"></a>Normales Zeichen
Das einfachste Muster ist eine Sequenz von normalen Zeichen, die exakt übereinstimmen sollen.

Beispielsweise wird bei der Verwendung mit der **"IsMatch"** die Zeichenfolge "Hello"-Funktion mit dem Muster übereinstimmt. **"Hello"** genau. Nicht mehr und nicht weniger. Die Zeichenfolge „hello!“ das Muster kann wegen des Ausrufezeichens am Ende stimmt nicht überein, da die Groß-/Kleinschreibung für den Buchstaben "h" falsch ist. (Unter ["MatchOptions"](#match-options) finden Sie Informationen zu Modifizierungsmöglichkeiten dieses Verhaltens.)

In der Mustersprache sind bestimmten Zeichen bestimmte Funktionen vorbehalten. Um diese Zeichen zu verwenden, entweder das Zeichen mit Präfix einen **\\** (umgekehrter Schrägstrich), um anzugeben, dass das Zeichen wörtlich entnommen werden soll, oder verwenden Sie eine der vordefinierten Muster später in diesem Thema beschrieben. Diese Tabelle enthält die Sonderzeichen:

| Sonderzeichen | Beschreibung |
| --- | --- |
| **.** |Punkt |
| **?** |Fragezeichen |
| **&#42;** |Sternchen |
| **\+** |Plus |
| **( )** |Klammern |
| **[ ]** |eckige Klammern |
| **{ }** |geschweifte Klammern |
| **^** |Caretzeichen |
| **$** |Dollarzeichen |
| **\|** |senkrechter Strich |
| **\\** |umgekehrter Schrägstrich |

Als Übereinstimmung mit der Zeichenfolge „Hello?“ können Sie beispielsweise das Muster **„Hello\\?“** mit einem umgekehrten Schrägstrich vor dem Fragezeichen verwenden.

### <a name="predefined-patterns"></a>Vordefinierte Muster
Vordefinierte Muster bieten eine einfache Möglichkeit, entweder eines Satzes von Zeichen oder eine Sequenz aus mehreren Zeichen übereinstimmen. Verwenden der [Operator für zeichenfolgenverkettung **&** ](operators.md) Ihre eigenen Textzeichenfolgen mit Membern der kombinieren die **Übereinstimmung** Enumeration:

| Match-Enumeration | Beschreibung | Reguläre Ausdrücke |
| --- | --- | --- |
| **Any** |Ordnet ein beliebiges Zeichen zu |`.` |
| **Comma** |Ordnet ein Komma zu |`;` |
| **Digit** |Ordnet eine einzelne Ziffer („0“ bis „9“) zu |`\d` |
| **Email** |Ordnet eine E-Mail-Adresse zu, die ein at-Zeichen (\@) und einen Domänennamen enthält, der einen Punkt (.) enthält |`.+\@.+\\.[^\\.]{2;}` |
| **Hyphen** |Ordnet einen Bindestrich zu |`\-` |
| **LeftParen** |Ordnet eine linke Klammer „(“ zu |`\(` |
| **Letter** |Ordnet einen Buchstaben zu |`\p{L}` |
| **MultipleDigits** |Entspricht einer oder mehreren Ziffern an. |`\d+` |
| **MultipleLetters** |Ordnet mindestens einen Buchstaben zu |`\p{L}+` |
| **MultipleNonSpaces** |Ordnet eine oder mehrere Zeichen, die keine Lücken (keine Leerzeichen, Tabstopp oder Zeilenvorschub) hinzufügen. |`\S+` |
| **MultipleSpaces** |Ordnet eine oder mehrere Zeichen, die Lücken (Leerzeichen, Tabstopp oder Zeilenvorschub) hinzufügen. |`\s+` |
| **NonSpace** |Ordnet ein einzelnes Zeichen zu, das keine Lücken hinzufügt |`\S` |
| **OptionalDigits** |Ordnet 0, 1 oder mehrere Ziffern zu |`\d*` |
| **OptionalLetters** |Ordnet 0, 1 oder mehrere Buchstaben zu |`\p{L}*` |
| **OptionalNonSpaces** |Ordnet 0, 1 oder mehrere Zeichen zu, die keine Lücken hinzufügen |`\S*` |
| **OptionalSpaces** |Ordnet 0, 1 oder mehrere Zeichen zu, die Lücken hinzufügen |`\s*` |
| **Period** |Ordnet einen Punkt (.) zu |`\.` |
| **RightParen** |Ordnet eine rechte Klammer „)“ zu |`\)` |
| **Space** |Ordnet ein Zeichen zu, das Lücken hinzufügt |`\s` |

Das Muster **"A" & MultipleDigits** entspricht dem Buchstaben „A“ gefolgt von einer oder mehreren Ziffern  

### <a name="regular-expressions"></a>Reguläre Ausdrücke
Das Muster, die diese Funktionen verwenden, ist eine [reguläre](https://en.wikipedia.org/wiki/Regular_expression). Erstellen von regulären Ausdrücken die normalen Zeichen und vordefinierte Muster, die weiter oben in diesem Thema Hilfe beschrieben sind.  

Reguläre Ausdrücke sind sehr leistungsstark; sie stehen in vielen Programmiersprachen zur Verfügung und werden für eine Vielzahl von Aufgaben verwendet. Sie können auch häufig eine zufällige Sequenz von Interpunktionszeichen ähneln. In diesem Artikel nicht beschrieben, alle Aspekte von regulären Ausdrücken, aber eine Fülle von Informationen, Tutorials und Tools sind im Web verfügbar.  

Reguläre Ausdrücke gibt es unterschiedliche Dialekte; PowerApps verwendet eine Variante von JavaScript. Finden Sie unter [Syntax von regulären Ausdrücken](http://msdn.microsoft.com/library/1400241x.aspx) eine Einführung in die Syntax. Benannte untergeordnete Übereinstimmungen (manchmal auch als benannte Erfassungsgruppen bezeichnet) werden unterstützt:

- Mit dem Namen untergeordnete Übereinstimmungen: **(?&lt; *Namen* &gt; ...)**
- Benannte Rückverweise:  **\\k&lt;*Name*&gt;**

In der **Übereinstimmung** Enum Tabelle weiter oben in diesem Thema jede Enumeration, die in der gleichen Zeile wie die entsprechende regulären Ausdruck angezeigt wird.

## <a name="match-options"></a>Übereinstimmungsoptionen
Sie können das Verhalten dieser Funktionen ändern, indem Sie eine oder mehrere Optionen, die Sie kombinieren können, mit dem Operator für zeichenfolgenverkettung angeben (**&amp;**).  

| MatchOptions-Enumeration | Beschreibung | Auswirkungen auf einen regulären Ausdruck |
| --- | --- | --- |
| **BeginsWith** |Das Muster muss ab dem Anfang des Texts übereinstimmen. |Fügt ein **^** am Anfang des regulären Ausdrucks ein |
| **Complete** |Standard für **"IsMatch"**. Das Muster muss die gesamte Zeichenfolge des Texts an, von Anfang bis Ende übereinstimmen. |Fügt eine **^** an den Anfang und ein **$** bis zum Ende des regulären Ausdrucks. |
| **Contains** |Standard für **Übereinstimmung** und **MatchAll**. Das Muster muss irgendwo im Text vorkommen; allerdings muss es nicht zwangsläufig am Anfang oder Ende vorkommen. |Ändert nicht den regulären Ausdruck |
| **EndsWith** |Das Muster muss am Ende der Zeichenfolge des Texts übereinstimmen. |Fügt ein **$** am Ende des regulären Ausdrucks ein. |
| **IgnoreCase** |Behandelt, die Groß- und Kleinbuchstaben als identisch. Standardmäßig wird bei der Übereinstimmung auf Groß- und Kleinschreibung geachtet. |Ändert nicht den regulären Ausdruck Diese Option entspricht der standard ist "i"-Modifizierer für reguläre Ausdrücke.  |
| **Multiline** |Zeilenübergreifende Übereinstimmung |Ändert nicht den regulären Ausdruck Diese Option entspricht dem Standard "m"-Modifizierer für reguläre Ausdrücke. |

Mithilfe von **MatchAll** ist äquivalent zur Verwendung des standard ist "g"-Modifizierers für reguläre Ausdrücke.

## <a name="syntax"></a>Syntax
**IsMatch**( *Text*; *Pattern* [; *Options* ] )

* *Text*: Erforderlich. Die zu prüfende Textzeichenfolge
* *Pattern*: erforderlich. Das Muster als Textzeichenfolge testen. Verketten Sie vordefinierte Muster, die die **Übereinstimmung** Enumeration definiert, oder geben Sie einen regulären Ausdruck. *Muster* muss eine Konstante Formel aus, ohne dass alle Variablen, -Datenquellen oder anderen dynamischen verweist auf diese Änderung während die app ausgeführt wird.
* *Options*: optional. Eine Kombination aus Text-Zeichenfolge **"MatchOptions"** Enum-Werte. Standardmäßig wird **MatchOptions.Complete** verwendet.

**Übereinstimmung**( *Text*; *Muster* [; *Optionen* ])

* *Text*: Erforderlich. Die Zeichenfolge entsprechend.
* *Pattern*: erforderlich. Das Muster für den Abgleich einer Textzeichenfolge. Verketten Sie vordefinierte Muster, die die **Übereinstimmung** Enumeration definiert, oder geben Sie einen regulären Ausdruck. *Muster* muss eine Konstante Formel aus, ohne dass alle Variablen, -Datenquellen oder anderen dynamischen verweist auf diese Änderung während die app ausgeführt wird.
* *Options*: optional. Eine Kombination aus Text-Zeichenfolge **"MatchOptions"** Enum-Werte. In der Standardeinstellung **MatchOptions.Contains** verwendet wird.

**MatchAll**( *Text*; *Muster* [; *Optionen* ])

* *Text*: Erforderlich. Die Zeichenfolge entsprechend.
* *Pattern*: erforderlich. Das Muster für den Abgleich einer Textzeichenfolge. Verketten Sie vordefinierte Muster, die die **Übereinstimmung** Enumeration definiert, oder geben Sie einen regulären Ausdruck. *Muster* muss eine Konstante Formel aus, ohne dass alle Variablen, -Datenquellen oder anderen dynamischen verweist auf diese Änderung während die app ausgeführt wird.
* *Options*: optional. Eine Kombination aus Text-Zeichenfolge **"MatchOptions"** Enum-Werte. In der Standardeinstellung **MatchOptions.Contains** verwendet wird.

## <a name="ismatch-examples"></a>IsMatch-Beispiele
### <a name="ordinary-characters"></a>Normales Zeichen
Stellen Sie sich vor, dass die App ein **Texteingabe**-Steuerelement mit dem Namen **TextInput1** enthält. Der Benutzer gibt Werte in dieses Steuerelement ein, die in einer Datenbank gespeichert werden sollen.   

Der Benutzer gibt **Hello World** in **Texteingabe1** ein.

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| `IsMatch( TextInput1.Text; "Hello world" )` |Tests, ob die Benutzereingaben genau übereinstimmt, die Zeichenfolge "Hello World". |**TRUE** |
| `IsMatch( TextInput1.Text; "Good bye" )` |Tests, ob die Benutzereingaben genau übereinstimmt, die Zeichenfolge "Good Bye". |**FALSE** |
| `IsMatch( TextInput1.Text; "hello"; Contains )` |Testet, ob die Eingabe des Benutzers das Wort "Hello" (Groß-/ Kleinschreibung) enthält. |**FALSE** |
| `IsMatch( TextInput1.Text; "hello"; Contains & IgnoreCase )` |Prüft, ob die Eingabe des Benutzers das Wort „Hello“(Groß-/Kleinschreibung beachten) enthält. |**TRUE** |

### <a name="predefined-patterns"></a>Vordefinierte Muster

|                                                            Formel                                                            |                                                                Beschreibung                                                                |  Ergebnis   |
|-------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-----------|
| `IsMatch( "123-45-7890"; Digit & Digit & Digit & Hyphen & Digit & Digit & Hyphen & Digit & Digit & Digit & Digit )` |                                              Ordnet eine US-Sozialversicherungsnummer zu                                               | **TRUE**  |
|                                           `IsMatch( "joan@contoso.com"; Email )`                                            |                                                         Ordnet eine E-Mail-Adresse zu                                                          | **TRUE**  |
|                              `IsMatch( "123.456"; MultipleDigits & Period & OptionalDigits )`                               |                                   Ordnet eine Folge von Ziffern, einen Punkt (.) und dann 0 (null) oder mehrere Ziffern zu                                   | **TRUE**  |
|                                `IsMatch( "123"; MultipleDigits & Period & OptionalDigits )`                                 | Ordnet eine Folge von Ziffern, einen Punkt (.) und dann 0 (null) oder mehrere Ziffern zu Damit dieses Muster nicht übereinstimmt wird nicht in den Text für den Abgleich ein Zeitraum angezeigt. | **FALSE** |

### <a name="regular-expressions"></a>Reguläre Ausdrücke

|                                                                              Formel                                                                              |                                                                                                                                  Beschreibung                                                                                                                                   |  Ergebnis   |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|
|                                                                    `IsMatch( "986"; "\d+" )`                                                                   |                                                                                                                    Entspricht einer ganzen Zahl größer als 0 (null).                                                                                                                     | **TRUE**  |
|                                                               `IsMatch( "1.02"; "\d+(\.\d\d)?" )`                                                              |                                        Ordnet einen positiven Währungsbetrag zu Wenn die Eingabe ein Dezimaltrennzeichen enthält, muss die Eingabe auch zwei numerische Zeichen nach dem Dezimaltrennzeichen enthalten. 3,00 ist beispielsweise gültig, aber 3,1 nicht.                                         | **TRUE**  |
|                                                            `IsMatch( "-4.95"; "(-)?\d+(\.\d\d)?" )`                                                             |                                                        Ordnet einen positiven oder negativen Währungsbetrag zu. Wenn die Eingabe ein Dezimaltrennzeichen enthält, muss die Eingabe auch zwei numerische Zeichen nach dem Dezimaltrennzeichen enthalten.                                                        | **TRUE**  |
|                                                         `IsMatch( "111-11-1111"; "\d{3}-\d{2}-\d{4}" )`                                                        | Ordnet eine US-Sozialversicherungsnummer zu Überprüft das Format, den Typ und die Länge des angegebenen Eingabefelds. Die Zeichenfolge, die übereinstimmen muss aus drei numerischen Zeichen gefolgt von einem Bindestrich und dann zwei numerische Zeichen gefolgt von einem Bindestrich, und klicken Sie dann die vier numerischen Zeichen bestehen. | **TRUE**  |
|                                                         `IsMatch( "111-111-111"; "\d{3}-\d{2}-\d{4}" )`                                                         |                                                                                               Wie im vorherigen Beispiel, aber einer der Bindestriche ist in der Eingabe an der falschen Stelle                                                                                               | **FALSE** |
|                                         `IsMatch( "AStrongPasswordNot"; "(?!^[0-9]\*$)(?!^[a-zA-Z]\*$)([a-zA-Z0-9]{8,10})" )`                                        |                                        Überprüft ein sicheres Kennwort, das 8, 9 oder 10 Zeichen, zusätzlich zu mindestens einer Ziffer und mindestens ein alphabetisches Zeichen enthalten muss. Die Zeichenfolge darf keine Sonderzeichen enthalten.                                        | **FALSE** |
| `IsMatch( "<http://microsoft.com>"; "(ht&#124;f)tp(s?)\:\/\/\[0-9a-zA-Z\]([-.\w]\*[0-9a-zA-Z])\*(:(0-9)\*)\*(\/?)([a-zA-Z0-9\-\.\?\,\'\/\\\+&%\$#_]\*)?" )` |                                                                                                                     Überprüft eine http-, https- oder ftp-URL                                                                                                                      | **TRUE**  |

## <a name="match-and-matchall-examples"></a>Beispiele für die Übereinstimmung und MatchAll

| Formel | Beschreibung | Ergebnis |
|--------|------------|-----------|
| `Match( "Bob Jones <bob.jones@contoso.com>"; "<(?<email>" & Match.Email & ")>"` | Wird nur den Teil-e-Mail die Kontaktinformationen extrahiert.  | {<br>e-Mail-Adresse:&nbsp;"bob.jones@contoso.com",<br>FullMatch:&nbsp;"&lt;bob.jones@contoso.com>",<br>Teilübereinstimmungen:&nbsp;[&nbsp;"bob.jones@contoso.com"&nbsp;],<br>StartMatch: 11<br>}  
| `Match( "Bob Jones <InvalidEmailAddress>"; "<(?<email>" & Match.Email & ")>"` | Wird nur den Teil-e-Mail die Kontaktinformationen extrahiert. Keine rechtlichen Adresse gefunden wird (ist kein @-Zeichen), sodass die Funktion gibt *leere*. | *blank* |  
| `Match( Language(); "(<language>\w{2})(?:-(?<script>\w{4}))?(?:-(?<region>\w{2}))?" )` | Extrahiert die Sprache, Skript und die regionalen Teile der Sprache zu kennzeichnen, die die **[Sprache](function-language.md)** -Funktion zurückgegeben wird. Diese Ergebnisse entsprechen der Vereinigten Staaten; finden Sie unter den [ **Sprache** Funktion Dokumentation](function-language.md) Weitere Beispiele.  Die **(?:** -Operator gruppiert Zeichen, ohne dass eine weitere untergeordnete Übereinstimmung erstellt. | {<br>Sprache: "En",<br>script: *blank*, <br>region: "UNS",<br>FullMatch: "En-US", <br>Teilübereinstimmungen: ["En", "", "USA"], <br>StartMatch: 1<br>} 
| `Match( "PT2H1M39S"; "PT(?:(<hours>\d+)H)?(?:(?<minutes>\d+)M)?(?:(?<seconds>\d+)S)?" )` | Extrahiert die Stunden, Minuten und Sekunden von einer ISO-8601-Zeitwerts an. Die extrahierten Werte sind immer noch in einer Textzeichenfolge; Verwenden Sie die [ **Wert** ](function-value.md) Funktion, die in eine Zahl zu konvertieren, bevor die mathematische Operationen ausgeführt werden.  | {<br> Stunden: "2",<br>Minuten: "1",<br>(Sekunden): "39",<br>FullMatch: "PT2H1M39S",<br>Teilübereinstimmungen:&nbsp;[&nbsp;"2"&nbsp;"1",&nbsp;"39"&nbsp;],<br>StartMatch: 1<br>} |

Lassen Sie uns in diesem letzten Beispiel anzuzeigen. Wenn Sie diese Zeichenfolge in einen Datum/Uhrzeit-Wert mit konvertieren möchten die **[Zeit](function-date-time.md)** -Funktion müssen Sie übergeben das benannte untergeordnete entspricht einzeln. Zu diesem Zweck können Sie die **[ForAll](function-forall.md)** Funktion, die ausgeführt werden, auf dem ersten aufzuzeichnen, die **MatchAll** zurückgibt:

``` powerapps-comma
First( 
    ForAll( 
        MatchAll( "PT2H1M39S"; "PT(?:(?<hours>\d+)H)?(?:(?<minutes>\d+)M)?(?:(?<seconds>\d+)S)?" ); 
        Time( Value( hours ); Value( minutes ); Value( seconds ) )
    )
).Value
```

Für diese Beispiele Hinzufügen einer [Schaltfläche](../controls/control-button.md) steuern, legen Sie dessen **OnSelect** -Eigenschaft auf diese Formel, und wählen Sie dann die Schaltfläche:

``` powerapps-comma
Set( pangram; "The quick brown fox jumps over the lazy dog." )
```
 
| Formel | Beschreibung | Ergebnis |
|---------|-------------|--------|
| `Match( pangram; "THE"; IgnoreCase )` | Suchen aller Übereinstimmungen von "Der" im Text-Zeichenfolge, die **Pangram** Variable enthält. Die Zeichenfolge enthält zwei Übereinstimmungen, aber nur die ersten wird zurückgegeben, da es sich bei Verwendung von **Übereinstimmung** und nicht **MatchAll**. Die Teilübereinstimmungen-Spalte ist leer, da keine untergeordnete Übereinstimmungen definiert wurden.  | {<br>FullMatch: "The",<br>Teilübereinstimmungen: [&nbsp;],<br>StartMatch: 32<br>} |
| `MatchAll( pangram; "the" )` | Suchen aller Übereinstimmungen von "the" in der Textzeichenfolge, die die **Pangram** Variable enthält. Der Test ist nur die zweite Instanz von "the" gefunden, wird Groß-/Kleinschreibung beachtet. Die Teilübereinstimmungen-Spalte ist leer, da keine untergeordnete Übereinstimmungen definiert wurden.  | <style> img { max-width: none } </style> ![](media/function-ismatch/pangram-the-one.png) |
| `MatchAll( pangram; "the"; IgnoreCase )` | Suchen aller Übereinstimmungen von "the" in der Textzeichenfolge, die die **Pangram** Variable enthält. In diesem Fall ist der Test Groß-/Kleinschreibung, damit beide Instanzen des Worts gefunden werden. Die Teilübereinstimmungen-Spalte ist leer, da keine untergeordnete Übereinstimmungen definiert wurden.  | <style> img { max-width: none } </style> ![](media/function-ismatch/pangram-the-two.png) |
| `MatchAll( pangram; "\b\wo\w\b" )` | Sucht alle drei Buchstaben bestehenden Wörter mit einem "o" in der Mitte. Beachten Sie, dass "brown" ausgeschlossen wurde, weil dabei handelt es sich keinen drei Buchstaben bestehendes Wort, daher findet keine Übereinstimmung von "\b" (Word oder Begrenzung).  | <style> img { max-width: none } </style> ![](media/function-ismatch/pangram-fox-dog.png) |
| `Match( pangram; "\b\wo\w\b\s\*(?<between>\w.+\w)\s\*\b\wo\w\b" )` | Ordnet alle Zeichen zwischen "Fuchs" und "Dog". | {<br>zwischen:&nbsp;"springt&nbsp;über&nbsp;der&nbsp;lazy",<br>FullMatch:&nbsp;"Fox&nbsp;springt&nbsp;über&nbsp;der&nbsp;lazy&nbsp;Hund",<br>Teilübereinstimmungen: ["springt über den verzögerten"],<br>StartMatch: 17<br> } |

Um die Ergebnisse der anzuzeigen **MatchAll** in einem Katalog:

1. Fügen Sie in einem leeren Bildschirm ein Leerzeichen vertikal **[Katalog](../controls/control-gallery.md)** Steuerelement.

2. Festlegen des Katalogs **Elemente** Eigenschaft **MatchAll (Pangram, "\w+")** oder **MatchAll (Pangram, MultipleLetters)**.

    ![](media/function-ismatch/pangram-gallery1.png)

3. Wählen Sie "Hinzufügen ein Elements aus der Registerkarte" Einfügen "" in der Mitte des Katalogsteuerelements auf die Vorlage des Katalogs auswählen. 

5. Hinzufügen einer **[Bezeichnung](../controls/control-text-box.md)** Steuerelement Vorlage des Katalogs.  

4. Legen Sie die Bezeichnung des **Text** Eigenschaft **ThisItem.FullMatch**.  
 
    Der Katalog wird mit jedes Worts in unserem Beispieltext gefüllt.  Ändern der Größe Vorlage des Katalogs und das Label-Steuerelement um alle Wörter auf demselben Bildschirm anzeigen.

    ![](media/function-ismatch/pangram-gallery2.png)
