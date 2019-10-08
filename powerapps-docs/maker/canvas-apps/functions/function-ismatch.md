---
title: Funktionen "IsMatch", "Match" und "MatchAll" | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax für die Funktionen "IsMatch", "Match" und "MatchAll" in powerapps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 08/15/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ac6e5196de03a3c2d292696f1216c443f4c5b7e6
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992660"
ms.PowerAppsDecimalTransform: true
---
# <a name="ismatch-match-and-matchall-functions-in-powerapps"></a>Funktionen "IsMatch", "Match" und "MatchAll" in powerapps
Testet auf eine Entsprechung oder extrahiert Teile einer Text Zeichenfolge auf der Grundlage eines Musters.

## <a name="description"></a>Beschreibung
Die **IsMatch**-Funktion prüft, ob eine Textzeichenfolge mit einem Muster übereinstimmt, das normale Zeichen, vordefinierte Muster oder einen [regulären Ausdruck](#regular-expressions) enthält.  Die **Match** -und **MatchAll** -Funktionen geben zurück, was abgeglichen wurde, einschließlich Teil Übereinstimmungen.  

Verwenden Sie **IsMatch**,um zu überprüfen, was ein Benutzer in ein **[Texteingabe](../controls/control-text-input.md)** -Steuerelement eingegeben hat. Beispielsweise können Sie überprüfen, ob der Benutzer eine gültige E-Mail-Adresse eingegeben hat, bevor das Ergebnis in der Datenquelle gespeichert wird. Wenn der Eintrag nicht mit Ihren Kriterien übereinstimmt, fügen Sie andere Steuerelemente hinzu, die den Benutzer zur Korrektur der Eingabe auffordern.

Verwenden Sie **Match** , um die erste Text Zeichenfolge zu extrahieren, die einem Muster und **MatchAll** entspricht, um alle übereinstimmenden Zeichen folgen zu extrahieren. Sie können auch Teil Übereinstimmungen extrahieren, um komplexe Zeichen folgen zu analysieren.   

**Match** gibt einen Datensatz mit Informationen für die erste gefundene Übereinstimmung zurück, und **MatchAll** gibt eine Tabelle mit Datensätzen für jede gefundene Übereinstimmung zurück. Der Datensatz oder die Datensätze enthalten Folgendes:

| Spalte | Typ | Beschreibung |
|----|----|----|
| *benannte Teil&#8209;Übereinstimmung&#8209;oder Teil Übereinstimmungen* | Text | Jede benannte Teil Übereinstimmung weist eine eigene Spalte auf. Erstellen Sie eine benannte Teil Übereinstimmung mit **(? &lt;*Name*&gt;** ... **)** im regulären Ausdruck. Wenn eine benannte Teil Übereinstimmung denselben Namen hat wie eine der vordefinierten Spalten (unten), hat die unter Übereinstimmung Vorrang, und es wird eine Warnung generiert. Um diese Warnung zu vermeiden, benennen Sie die unter Übereinstimmung um. |
| **Vollständiger Treffer** | Text | Alle übereinstimmenden Text Zeichenfolgen. |
| **Startmatch** | Number | Die Anfangsposition der Entsprechung innerhalb der Eingabetext Zeichenfolge. Das erste Zeichen der Zeichenfolge gibt 1 zurück. | 
| **Teil Übereinstimmungen** | Einspaltige Tabelle von Text (Spalten **Wert**) | Die Tabelle mit benannten und unbenannten Teil Übereinstimmungen in der Reihenfolge, in der Sie im regulären Ausdruck angezeigt werden. Im Allgemeinen sind benannte Teil Übereinstimmungen einfacher zu arbeiten und werden empfohlen. Verwenden Sie die Funktion " [**ForAll**](function-forall.md) " oder " [**Last**](function-first-last.md)( [**firstn**](function-first-last.md)( **...** ))", um mit einer einzelnen Teil Übereinstimmung zu arbeiten. Wenn im regulären Ausdruck keine untergeordneten Übereinstimmungen definiert sind, ist diese Tabelle vorhanden, aber leer. |

Diese Funktionen unterstützen [**matchoptions**](#match-options). Standardmäßig: 
- Bei diesen Funktionen wird die Groß-/Kleinschreibung beachtet. Verwenden Sie **ignoreCase** , um Übereinstimmungen ohne Berücksichtigung von Groß-und klein    
- **"IsMatch** " entspricht der gesamten Text Zeichenfolge ( **"matchoption** **vervollständigen** "), während " **Match** " und " **MatchAll** " eine Übereinstimmung an einer beliebigen Stelle in der Text Zeichenfolge findet Verwenden Sie " **Complete**", " **enthält**", " **beginswith**" oder " **EndsWith** " entsprechend Ihrem Szenario.

**IsMatch** gibt *TRUE* zurück, wenn die Zeichenfolge mit dem Muster übereinstimmt, oder *FALSE*, Wenn dies nicht der Fall ist. Die **Match** -Rückgabe ist *leer* , wenn keine Entsprechung gefunden wird, die mit der [**isblank**](function-isblank-isempty.md) -Funktion getestet werden kann. **MatchAll** gibt eine leere Tabelle zurück, wenn keine Übereinstimmung gefunden wird, die mit der [**IsEmpty**](function-isblank-isempty.md) -Funktion getestet werden kann.

Wenn Sie **MatchAll** verwenden, um eine Text Zeichenfolge aufzuteilen, sollten Sie die **[Split](function-split.md)** -Funktion verwenden, die einfacher zu verwenden und schneller ist.

## <a name="patterns"></a>Muster
Der Schlüssel für die Verwendung dieser Funktionen besteht darin, das Abzugleichende Muster zu beschreiben. Sie beschreiben das Muster als Testzeichenfolge als Kombination aus Folgendem:

* Normale Zeichen, z.B. **"Abc"** oder **"123"**
* Vordefinierte Muster, z.B. **Letter** (Buchstabe), **MultipleDigits** (mehrere Ziffern) oder **E-Mail**. (Die **Match**-Enumeration definiert diese Muster.)
* Codes für reguläre Ausdrücke, z. **b. "\d + \s + \d +"** oder **"[a-z] +"** .

Kombinieren Sie diese Elemente mithilfe des [Zeichenfolgenverkettungs-Operators **&** ](operators.md). **"abc" & Digit & "\s+"** ist beispielsweise ein gültiges Muster, das den Zeichen „a“, „b“ und „c“ gefolgt von einer Ziffer zwischen 0 und 9 entspricht, auf die mindestens ein Leerzeichen folgt.

### <a name="ordinary-characters"></a>Normales Zeichen
Das einfachste Muster ist eine Sequenz von normalen Zeichen, die exakt übereinstimmen sollen.

Bei Verwendung mit der **IsMatch** -Funktion stimmt die Zeichenfolge "Hello" z. b. genau mit dem Muster **"Hello"** überein. Nicht mehr und nicht weniger. Die Zeichenfolge „hello!“ entspricht nicht dem Muster aufgrund des Ausrufezeichens am Ende und, da die Groß-/Kleinschreibung für den Buchstaben "h" falsch ist. (Unter ["MatchOptions"](#match-options) finden Sie Informationen zu Modifizierungsmöglichkeiten dieses Verhaltens.)

In der Mustersprache sind bestimmten Zeichen bestimmte Funktionen vorbehalten. Um diese Zeichen zu verwenden, versehen Sie das Zeichen entweder mit einem **\\ (umgekehrter** Schrägstrich), um anzugeben, dass das Zeichen buchstäblich verwendet werden soll, oder verwenden Sie eines der vordefinierten Muster, das weiter unten in diesem Thema beschrieben wird. Diese Tabelle enthält die Sonderzeichen:

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
Vordefinierte Muster stellen eine einfache Möglichkeit dar, entweder einen Zeichensatz oder eine Sequenz von mehreren Zeichen abzugleichen. Verwenden Sie den Operator für die [Zeichen folgen Verkettung **&** ](operators.md) , um Ihre eigenen Text Zeichenfolgen mit Membern der **Match** -Enumeration zu kombinieren:

| Match-Aufzählung | Beschreibung | Regulärer Ausdruck |
| --- | --- | --- |
| **Any** |Ordnet ein beliebiges Zeichen zu |`.` |
| **Comma** |Ordnet ein Komma zu |`;` |
| **Digit** |Ordnet eine einzelne Ziffer („0“ bis „9“) zu |`\d` |
| **Email** |Ordnet eine E-Mail-Adresse zu, die ein at-Zeichen (\@) und einen Domänennamen enthält, der einen Punkt (.) enthält |`.+\@.+\\.[^\\.]{2;}` |
| **Hyphen** |Ordnet einen Bindestrich zu |`\-` |
| **LeftParen** |Ordnet eine linke Klammer „(“ zu |`\(` |
| **Letter** |Ordnet einen Buchstaben zu |`\p{L}` |
| **MultipleDigits** |Entspricht einer oder mehreren Ziffern. |`\d+` |
| **MultipleLetters** |Ordnet mindestens einen Buchstaben zu |`\p{L}+` |
| **MultipleNonSpaces** |Entspricht einem oder mehreren Zeichen, die kein Leerzeichen hinzufügen (nicht Leerzeichen, Tabstopps oder Zeilen Umschriften). |`\S+` |
| **MultipleSpaces** |Entspricht einem oder mehreren Zeichen, die Leerzeichen (Leerzeichen, Tabstopps oder Zeilen Umschriften) hinzufügen. |`\s+` |
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
Das Muster, das diese Funktionen verwenden, ist ein [regulärer Ausdruck](https://en.wikipedia.org/wiki/Regular_expression). Die normalen Zeichen und vordefinierten Muster, die weiter oben in diesem Thema beschrieben werden, helfen bei der Erstellung regulärer Ausdrücke.  

Reguläre Ausdrücke sind sehr leistungsstark; sie stehen in vielen Programmiersprachen zur Verfügung und werden für eine Vielzahl von Aufgaben verwendet. Sie können auch oft wie eine zufällige Sequenz von Satzzeichen aussehen. In diesem Artikel werden nicht alle Aspekte von regulären Ausdrücken beschrieben. es gibt jedoch eine Vielzahl von Informationen, Tutorials und Tools, die im Web zur Verfügung stehen.  

Reguläre Ausdrücke sind in unterschiedlichen Dialekten enthalten, und powerapps verwendet eine Variante des JavaScript-Dialekts. Eine Einführung in die-Syntax finden Sie unter [Syntax für reguläre Ausdrücke](https://msdn.microsoft.com/library/1400241x.aspx) . Benannte Teil Übereinstimmungen (manchmal auch benannte Erfassungs Gruppen genannt) werden unterstützt:

- Benannte Teil Übereinstimmungen: **(? &lt;*Name*&gt;...)**
- Benannte Rückverweise: **\\K @ no__t-2*Name*&gt;**

In der abgleichsaufgabentabelle weiter oben in diesem Thema wird jede **-Enumeration** in derselben Zeile wie der entsprechende reguläre Ausdruck angezeigt.

## <a name="match-options"></a>Übereinstimmungsoptionen
Sie können das Verhalten dieser Funktionen ändern, indem Sie mindestens eine Option angeben, die Sie mit dem Operator für die Zeichen folgen Verkettung ( **&amp;** ) kombinieren können.  

| Matchoptions-Enumeration | Beschreibung | Auswirkung auf einen regulären Ausdruck |
| --- | --- | --- |
| **BeginsWith** |Das Muster muss ab dem Anfang des Texts übereinstimmen. |Fügt ein **^** am Anfang des regulären Ausdrucks ein |
| **Complete** |Standard für **IsMatch**. Das Muster muss mit der gesamten Text Zeichenfolge von Anfang bis Ende abgeglichen werden. |Fügt am Anfang einen **^** und einen **$** am Ende des regulären Ausdrucks ein. |
| **Contains** |Standard für **Match** und **MatchAll**. Das Muster muss irgendwo im Text vorkommen; allerdings muss es nicht zwangsläufig am Anfang oder Ende vorkommen. |Ändert nicht den regulären Ausdruck |
| **EndsWith** |Das Muster muss dem Ende der Text Zeichenfolge entsprechen. |Fügt ein **$** am Ende des regulären Ausdrucks ein. |
| **IgnoreCase** |Behandelt groß-und Kleinbuchstaben als identisch. Standardmäßig wird bei der Übereinstimmung auf Groß- und Kleinschreibung geachtet. |Ändert nicht den regulären Ausdruck Diese Option entspricht dem standardmäßigen "i"-Modifizierer für reguläre Ausdrücke.  |
| **Multiline** |Zeilenübergreifende Übereinstimmung |Ändert nicht den regulären Ausdruck Diese Option entspricht dem Standard-Modifizierer "m" für reguläre Ausdrücke. |

Die Verwendung von **MatchAll** entspricht der Verwendung des Standard-Modifizierers "g" für reguläre Ausdrücke.

## <a name="syntax"></a>Syntax
**IsMatch**( *Text*; *Pattern* [; *Options* ] )

* *Text*: Erforderlich. Die zu prüfende Textzeichenfolge
* *Pattern*: erforderlich. Das zu überprüfende Muster als Text Zeichenfolge. Verketten Sie vordefinierte Muster, **die die** Übereinstimmungs-Enumeration definiert, oder stellen Sie einen regulären Ausdruck bereit. Das *Muster* muss eine Konstante Formel ohne Variablen, Datenquellen oder andere dynamische Verweise sein, die sich bei der Ausführung der App ändern.
* *Options*: optional. Eine Textzeichen folgen Kombination von **matchoptions** -Enumerationswerten. Standardmäßig wird **MatchOptions.Complete** verwendet.

**Match**( *Text*; *Muster* [; *Optionen* ])

* *Text*: Erforderlich. Die zu Übereinstimmungs Text Zeichenfolge.
* *Pattern*: erforderlich. Das Muster, das als Text Zeichenfolge abgeglichen werden soll. Verketten Sie vordefinierte Muster, **die die** Übereinstimmungs-Enumeration definiert, oder stellen Sie einen regulären Ausdruck bereit. Das *Muster* muss eine Konstante Formel ohne Variablen, Datenquellen oder andere dynamische Verweise sein, die sich bei der Ausführung der App ändern.
* *Options*: optional. Eine Textzeichen folgen Kombination von **matchoptions** -Enumerationswerten. Standardmäßig wird **matchoptions. enthält** verwendet.

**MatchAll**( *Text*; *Muster* [; *Optionen* ])

* *Text*: Erforderlich. Die zu Übereinstimmungs Text Zeichenfolge.
* *Pattern*: erforderlich. Das Muster, das als Text Zeichenfolge abgeglichen werden soll. Verketten Sie vordefinierte Muster, **die die** Übereinstimmungs-Enumeration definiert, oder stellen Sie einen regulären Ausdruck bereit. Das *Muster* muss eine Konstante Formel ohne Variablen, Datenquellen oder andere dynamische Verweise sein, die sich bei der Ausführung der App ändern.
* *Options*: optional. Eine Textzeichen folgen Kombination von **matchoptions** -Enumerationswerten. Standardmäßig wird **matchoptions. enthält** verwendet.

## <a name="ismatch-examples"></a>IsMatch-Beispiele
### <a name="ordinary-characters"></a>Normales Zeichen
Stellen Sie sich vor, dass die App ein **Texteingabe**-Steuerelement mit dem Namen **TextInput1** enthält. Der Benutzer gibt Werte in dieses Steuerelement ein, die in einer Datenbank gespeichert werden sollen.   

Der Benutzer gibt **Hello World** in **Texteingabe1** ein.

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| `IsMatch( TextInput1.Text; "Hello world" )` |Testet, ob die Eingabe des Benutzers genau mit der Zeichenfolge "Hello World" übereinstimmt. |**TRUE** |
| `IsMatch( TextInput1.Text; "Good bye" )` |Testet, ob die Eingabe des Benutzers genau mit der Zeichenfolge "Good Bye" übereinstimmt. |**FALSE** |
| `IsMatch( TextInput1.Text; "hello"; Contains )` |Testet, ob die Eingabe des Benutzers das Wort "Hello" (Groß-/Kleinschreibung wird beachtet) enthält. |**FALSE** |
| `IsMatch( TextInput1.Text; "hello"; Contains & IgnoreCase )` |Prüft, ob die Eingabe des Benutzers das Wort „Hello“(Groß-/Kleinschreibung beachten) enthält. |**TRUE** |

### <a name="predefined-patterns"></a>Vordefinierte Muster

|                                                            Formel                                                            |                                                                Beschreibung                                                                |  Ergebnis   |
|-------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-----------|
| `IsMatch( "123-45-7890"; Digit & Digit & Digit & Hyphen & Digit & Digit & Hyphen & Digit & Digit & Digit & Digit )` |                                              Ordnet eine US-Sozialversicherungsnummer zu                                               | **TRUE**  |
|                                           `IsMatch( "joan@contoso.com"; Email )`                                            |                                                         Ordnet eine E-Mail-Adresse zu                                                          | **TRUE**  |
|                              `IsMatch( "123.456"; MultipleDigits & Period & OptionalDigits )`                               |                                   Ordnet eine Folge von Ziffern, einen Punkt (.) und dann 0 (null) oder mehrere Ziffern zu                                   | **TRUE**  |
|                                `IsMatch( "123"; MultipleDigits & Period & OptionalDigits )`                                 | Ordnet eine Folge von Ziffern, einen Punkt (.) und dann 0 (null) oder mehrere Ziffern zu Es wird kein Zeitraum im Text angezeigt, der übereinstimmt, sodass dieses Muster nicht übereinstimmt. | **FALSE** |

### <a name="regular-expressions"></a>Reguläre Ausdrücke

|                                                                              Formel                                                                              |                                                                                                                                  Beschreibung                                                                                                                                   |  Ergebnis   |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|
|                                                                    `IsMatch( "986"; "\d+" )`                                                                   |                                                                                                                    Entspricht einer ganzen Zahl, die größer als NULL ist.                                                                                                                     | **TRUE**  |
|                                                               `IsMatch( "1.02"; "\d+(\.\d\d)?" )`                                                              |                                        Ordnet einen positiven Währungsbetrag zu Wenn die Eingabe ein Dezimaltrennzeichen enthält, muss die Eingabe auch zwei numerische Zeichen nach dem Dezimaltrennzeichen enthalten. 3,00 ist beispielsweise gültig, aber 3,1 nicht.                                         | **TRUE**  |
|                                                            `IsMatch( "-4.95"; "(-)?\d+(\.\d\d)?" )`                                                             |                                                        Ordnet einen positiven oder negativen Währungsbetrag zu. Wenn die Eingabe ein Dezimaltrennzeichen enthält, muss die Eingabe auch zwei numerische Zeichen nach dem Dezimaltrennzeichen enthalten.                                                        | **TRUE**  |
|                                                         `IsMatch( "111-11-1111"; "\d{3}-\d{2}-\d{4}" )`                                                        | Ordnet eine US-Sozialversicherungsnummer zu Überprüft das Format, den Typ und die Länge des angegebenen Eingabefelds. Die Zeichenfolge, die abgeglichen werden soll, muss aus drei numerischen Zeichen gefolgt von einem Bindestrich, zwei numerischen Zeichen gefolgt von einem Bindestrich und dann vier numerischen Zeichen bestehen. | **TRUE**  |
|                                                         `IsMatch( "111-111-111"; "\d{3}-\d{2}-\d{4}" )`                                                         |                                                                                               Wie im vorherigen Beispiel, aber einer der Bindestriche ist in der Eingabe an der falschen Stelle                                                                                               | **FALSE** |
|                                         `IsMatch( "AStrongPasswordNot"; "(?!^[0-9]\*$)(?!^[a-zA-Z]\*$)([a-zA-Z0-9]{8,10})" )`                                        |                                        Validiert ein sicheres Kennwort, das acht, neun oder zehn Zeichen enthalten muss, zusätzlich zu mindestens einer Ziffer und mindestens einem alphabetischen Zeichen. Die Zeichenfolge darf keine Sonderzeichen enthalten.                                        | **FALSE** |
| `IsMatch( "<https://microsoft.com>"; "(ht&#124;f)tp(s?)\:\/\/\[0-9a-zA-Z\]([-.\w]\*[0-9a-zA-Z])\*(:(0-9)\*)\*(\/?)([a-zA-Z0-9\-\.\?\,\'\/\\\+&%\$#_]\*)?" )` |                                                                                                                     Überprüft eine http-, https- oder ftp-URL                                                                                                                      | **TRUE**  |

## <a name="match-and-matchall-examples"></a>Match-und MatchAll-Beispiele

| Formel | Beschreibung | Ergebnis |
|--------|------------|-----------|
| `Match( "Bob Jones <bob.jones@contoso.com>"; "<(?<email>" & Match.Email & ")>"` | Extrahiert nur den e-Mail-Anteil der Kontaktinformationen.  | {<br>e-Mail: &nbsp; "bob.jones@contoso.com",<br>Fullmatch: &nbsp; "&lt; @ no__t-2 >",<br>Teil Übereinstimmungen: &nbsp; [&nbsp; "bob.jones@contoso.com" &nbsp;],<br>Startmatch: 11:<br>}  
| `Match( "Bob Jones <InvalidEmailAddress>"; "<(?<email>" & Match.Email & ")>"` | Extrahiert nur den e-Mail-Anteil der Kontaktinformationen. Es wurde keine juristische Adresse gefunden (es ist kein @-Zeichen vorhanden), sodass die Funktion *leer*ist. | *blank* |  
| `Match( Language(); "(<language>\w{2})(?:-(?<script>\w{4}))?(?:-(?<region>\w{2}))?" )` | Extrahiert die sprach-, Skript-und Regions Teile des sprach Tags, das von der **[Language](function-language.md)** -Funktion zurückgegeben wird. Diese Ergebnisse spiegeln die USA ein. Weitere Beispiele finden Sie in der Dokumentation zur [ **sprach** Funktion](function-language.md) .  Der Operator **(?:** gruppiert Zeichen, ohne eine andere unter Übereinstimmung zu erstellen. | {<br>Sprache: "en",<br>Skript: *leer*, <br>AUM "USA",<br>Fullmatch: "en-US", <br>Teil Übereinstimmungen: ["en", "", "US"], <br>Startmatch: 1<br>} 
| `Match( "PT2H1M39S"; "PT(?:<hours>\d+)H)?(?:(?<minutes>\d+)M)?(?:(?<seconds>\d+)S)?" )` | Extrahiert die Stunden, Minuten und Sekunden aus einem Wert der ISO 8601-Dauer. Die extrahierten Zahlen sind immer noch in einer Text Zeichenfolge. Verwenden Sie die [**value**](function-value.md) -Funktion, um Sie vor mathematischen Operationen in eine Zahl zu konvertieren.  | {<br> Hours "2",<br>Minuten "1",<br>Vorsprung "39",<br>Fullmatch: "PT2H1M39S",<br>Teil Übereinstimmungen: &nbsp; [&nbsp; "2", &nbsp; "1", &nbsp; "39" &nbsp;],<br>Startmatch: 1<br>} |

Sehen wir uns das letzte Beispiel an. Wenn Sie diese Zeichenfolge mithilfe der **[time](function-date-time.md)** -Funktion in einen Datums-/Uhrzeitwert konvertieren möchten, müssen Sie die benannten Teil Übereinstimmungen einzeln übergeben. Zu diesem Zweck können Sie die **[with](function-with.md)** -Funktion **verwenden, die für den zurückgegebenen** Datensatz verwendet wird:

``` powerapps-comma
With( 
    Match( "PT2H1M39S"; "PT(?:(?<hours>\d+)H)?(?:(?<minutes>\d+)M)?(?:(?<seconds>\d+)S)?" ); 
    Time( Value( hours ); Value( minutes ); Value( seconds ) )
)
```

Fügen Sie für diese Beispiele ein [Button](../controls/control-button.md) -Steuerelement hinzu, legen Sie dessen **onselect** -Eigenschaft auf diese Formel fest, und wählen Sie dann die Schaltfläche aus:

``` powerapps-comma
Set( pangram; "The quick brown fox jumps over the lazy dog." )
```
 
| Formel | Beschreibung | Ergebnis |
|---------|-------------|--------|
| `Match( pangram; "THE"; IgnoreCase )` | Sucht alle Übereinstimmungen von "The" in der Text Zeichenfolge, die in der **Pangram** -Variablen enthalten ist. Die Zeichenfolge enthält zwei Übereinstimmungen, aber nur das erste wird zurückgegeben, da Sie **Match** und nicht **MatchAll**verwenden. Die SubMatches-Spalte ist leer, da keine untergeordneten Übereinstimmungen definiert wurden.  | {<br>Fullmatch: "The",<br>Teil Übereinstimmungen: [&nbsp;],<br>Startmatch: 32<br>} |
| `MatchAll( pangram; "the" )` | Sucht alle Übereinstimmungen von "The" in der Text Zeichenfolge, die in der **Pangram** -Variablen enthalten ist. Beim Test wird die Groß-/Kleinschreibung beachtet, daher wird nur die zweite Instanz von "The" gefunden. Die SubMatches-Spalte ist leer, da keine untergeordneten Übereinstimmungen definiert wurden.  | <style> img { max-width: none } </style> ![](media/function-ismatch/pangram-the-one.png) |
| `MatchAll( pangram; "the"; IgnoreCase )` | Sucht alle Übereinstimmungen von "The" in der Text Zeichenfolge, die in der **Pangram** -Variablen enthalten ist. In diesem Fall wird bei dem Test die Groß-/Kleinschreibung nicht beachtet, sodass beide Instanzen des Worts gefunden werden. Die SubMatches-Spalte ist leer, da keine untergeordneten Übereinstimmungen definiert wurden.  | <style> img { max-width: none } </style> ![](media/function-ismatch/pangram-the-two.png) |
| `MatchAll( pangram; "\b\wo\w\b" )` | Findet alle aus drei Buchstaben bestehenden Wörter mit einem "o" in der Mitte. Beachten Sie, dass "Brown" ausgeschlossen ist, weil es sich nicht um ein aus drei Buchstaben bestehender Wort handelt und daher nicht "\b" (Wort Grenze) entspricht.  | <style> img { max-width: none } </style> ![](media/function-ismatch/pangram-fox-dog.png) |
| `Match( pangram; "\b\wo\w\b\s\*(?<between>\w.+\w)\s\*\b\wo\w\b" )` | Entspricht allen Zeichen zwischen "Fox" und "Dog". | {<br>zwischen: &nbsp; "Sprünge @ no__t-1over @ no__t-2The @ no__t-3lazy",<br>Fullmatch: &nbsp; "Fox @ no__t-1jumps @ no__t-2over @ no__t-3the @ no__t-4lazy @ no__t-5dog",<br>Teil Übereinstimmungen: ["springt über den Lazy"],<br>Startmatch: Uhr<br> } |

So zeigen Sie die Ergebnisse von **MatchAll** in einem Katalog an:

1. Fügen Sie auf einem leeren Bildschirm ein leeres **[vertikales](../controls/control-gallery.md)** Katalog Steuerelement ein.

2. Legen Sie die **Items** -Eigenschaft des Katalogs auf **MatchAll (Pangram, "\w +")** oder **MatchAll (Pangram, multipleletters)** fest.

    ![](media/function-ismatch/pangram-gallery1.png)

3. Wählen Sie in der Mitte des Katalog-Steuer Elements auf der Registerkarte Einfügen die Option "Element hinzufügen" aus, um die Vorlage der Galerie auszuwählen. 

5. Fügen Sie der Vorlage des Katalogs ein **[Label](../controls/control-text-box.md)** -Steuerelement hinzu.  

4. Legen Sie die **Text** -Eigenschaft der Bezeichnung auf **thisitem. fullmatch**fest.  
 
    Der Katalog wird mit jedem Wort in unserem Beispiel Text gefüllt.  Ändern Sie die Größe der Galerie Vorlage und das Label-Steuerelement, um alle Wörter auf einem Bildschirm anzuzeigen.

    ![](media/function-ismatch/pangram-gallery2.png)
