---
title: JSON-Funktion | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax, für die JSON-Funktion in powerapps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/02/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0780280298041aede5b24a9a819aa2743584f8c8
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730730"
ms.PowerAppsDecimalTransform: true
---
# <a name="json-function-in-power-apps"></a>JSON-Funktion in powerapps

Generiert eine JSON-Text Zeichenfolge für eine Tabelle, einen Datensatz oder einen Wert.

## <a name="description"></a>Beschreibung

Die **JSON** -Funktion gibt die JavaScript Object Notation (JSON)-Darstellung einer Datenstruktur als Text zurück, damit Sie für die Speicherung oder Übertragung über ein Netzwerk geeignet ist. [ECMA-404](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-404.pdf) und [IETF RFC 8259](https://tools.ietf.org/html/rfc8259) beschreiben das Format, das häufig von JavaScript und anderen Programmiersprachen verwendet wird.

Canvas-apps unterstützen die [Datentypen](data-types.md) , die in dieser Tabelle aufgeführt sind, mit Details zur Textdarstellung:

| Datentyp | Beschreibung | Ergebnis Beispiel |
|-----------|-------------|---------|
| **Booleschen** | *true* oder *false*. | `true` |
| **Farbe** | Eine Zeichenfolge, die die 8-stellige hexadezimale Darstellung der Farbe enthält. Diese Darstellung hat das Format #*RRGGBBAA*, wobei *RR* die rote Komponente, *GG* ist grün, *BB* ist blau und *AA* der Alphakanal. Für den Alphakanal ist **00** vollständig transparent, und **FF** ist vollständig transparent. Sie können die Zeichenfolge an die [**ColorValue**](function-colors.md) -Funktion übergeben.  | `"#102030ff"` |
| **Währung** | Eine Zahl, die das entsprechende Dezimaltrennzeichen für die Sprache des Benutzers verwendet. Bei Bedarf wird die wissenschaftliche Schreibweise verwendet. | `1,345` |
| **Datum** | Eine Zeichenfolge, die das Datum im Format ISO 8601 **yyyy-mm-dd** enthält. | `"2019-03-31"` |
| **DateTime** | Eine Zeichenfolge, die ein Datum/eine Uhrzeit für ISO 8601 enthält. Datums-/Uhrzeitwerte werden in UTC angegeben, wie das Ende "Z" anzeigt.  | `"2019-03-31T22:32:06.822Z"`  |
| **GUID** | Eine Zeichenfolge, die den GUID-Wert enthält. Buchstaben sind Kleinbuchstaben. | `"751b58ac-380e-4a04-a925-9f375995cc40"`
| **Bild, Medien** | Wenn **includebinarydata** angegeben ist, werden Mediendateien in einer Zeichenfolge codiert. Webverweise, die das http: oder https: URL-Schema verwenden, werden nicht geändert. Verweise auf Binärdaten im Arbeitsspeicher werden mit dem Format ["Data:*MimeType*; Base64,..."](https://en.wikipedia.org/wiki/Data_URI_scheme) codiert. In-Memory-Daten enthalten Bilder, die Benutzer mithilfe des [**Kamera**](../controls/control-camera.md) -Steuer Elements und anderer Verweise mit den Schemas appres: und BLOB: URL erfassen.| `"data:image/jpeg;base64,/9j/4AA..."` |
| **Einigen** | Eine Zahl, die das entsprechende Dezimaltrennzeichen für die Sprache des Benutzers verwendet. Bei Bedarf wird die wissenschaftliche Schreibweise verwendet. | `1,345` |
| **Option&nbsp;festgelegt** | Numerischer Wert des Options Satzes, nicht der Bezeichnung, die für die Anzeige verwendet wird. Der numerische Wert wird verwendet, da er sprachunabhängig ist.  | `1001` |
| **Zeit** | Eine Zeichenfolge, die ein ISO 8601 *hh: mm: SS. fff* -Format enthält.  | `"23:12:49.000"` |
| **Aufnahme** | Durch Trennzeichen getrennte Liste, zwischen **{** und **}** , von Feldern und deren Werten. Diese Notation ähnelt der für Datensätze in Canvas-apps, aber der Name ist immer zwischen doppelten Anführungszeichen. Dieses Format unterstützt keine Datensätze, die auf n:1-Beziehungen basieren.  | `{ "First Name": "Fred"; "Age": 21 }` |
| **Glaub** | Durch Trennzeichen getrennte Liste zwischen **[** und **]** von Datensätzen. Dieses Format unterstützt keine Tabellen, die auf 1: n-Beziehungen basieren.  | `[ { "First Name": "Fred"; "Age": 21 }; { "First Name": "Jean"; "Age": 20 } ]` |
| **Zwei&nbsp;Option** | Der boolesche Wert der beiden Option *true* oder *false*, nicht die Bezeichnung, die für die Anzeige verwendet wird. Der boolesche Wert wird verwendet, da er sprachunabhängig ist. | `false` |
| **Hyperlink, Text** | Zeichenfolge zwischen doppelten Anführungszeichen. Die Funktion schützt eingebettete doppelte Anführungszeichen mit einem umgekehrten Schrägstrich, ersetzt neue Zeilen durch "\n" und führt andere standardmäßige JavaScript-Ersetzungen durch. | `"This is a string."` |

Geben Sie das optionale *Format* Argument an, um zu steuern, wie lesbar das Ergebnis ist und wie nicht unterstützte und binäre Datentypen behandelt werden. Standardmäßig ist die Ausgabe so kompakt wie möglich ohne unnötige Leerzeichen oder Zeilenumbrüche, und nicht unterstützte Datentypen und binäre Daten sind nicht zulässig. Sie können mehrere Formate kombinieren, wenn Sie den **&** -Operator angeben.

| Jsonformat-Enumeration | Beschreibung |
|-----------------|-------------|
| **Theit** | Standard.  Die Ausgabe ist so kompakt wie möglich ohne hinzugefügte Leerzeichen oder Zeilenumbrüche. |
| **Einzug** | Um die Lesbarkeit zu verbessern, enthält die Ausgabe einen Zeilen Wechsel für jede Spalte und Schachtelungs Ebene und verwendet vier Leerzeichen für jede Einzugs Ebene. |
| **Includebinarydata** | Das Ergebnis enthält Bild-, Video-und Audioclip-Spalten. Dieses Format kann die Größe des Ergebnisses drastisch erhöhen und die Leistung Ihrer APP beeinträchtigen. |
| **Ignorebinarydata** | Das Ergebnis enthält keine Bild-, Video-oder Audioclip-Spalten. Wenn Sie weder **includebinarydata** noch **ignorebinarydata**angeben, erzeugt die Funktion einen Fehler, wenn Binärdaten gefunden werden. |
| **Ignoreunsupportedtypes** | Nicht unterstützte Datentypen sind zulässig, das Ergebnis enthält Sie jedoch nicht. Standardmäßig wird von nicht unterstützten Datentypen ein Fehler erzeugt. |

Verwenden Sie die Funktionen [ **showcolumns** und **dropcolumns** ](function-table-shaping.md) , um zu steuern, welche Daten das Ergebnis enthält, und um nicht unterstützte Datentypen zu entfernen.

Da **JSON** sowohl Arbeitsspeicher als auch Rechen intensiv sein kann, können Sie diese Funktion nur in [Verhaltens Funktionen](../working-with-formulas-in-depth.md)verwenden. Sie können das Ergebnis aus **JSON** in einer [Variablen](../working-with-variables.md)erfassen, die Sie dann im Datenfluss verwenden können.

Wenn eine Spalte sowohl einen anzeigen Amen als auch einen logischen Namen aufweist, enthält das Ergebnis den logischen Namen. Anzeigen Amen spiegeln die Sprache des App-Benutzers wider und sind daher für die Datenübertragung an einen gemeinsamen Dienst ungeeignet.

## <a name="syntax"></a>Syntax

**JSON**( *datastructure* [; *Format* ])

* *Datastructure* – erforderlich. Die Datenstruktur, die in JSON konvertiert werden soll.  Tabellen, Datensätze und primitive Werte werden beliebig unterstützt.
* *Format* : optional.  Der **jsonformat** -Enumerationswert. Der Standardwert ist **Compact**. Dadurch werden keine Zeilenumbrüche oder Leerzeichen hinzugefügt, und binäre Daten und nicht unterstützte Spalten werden blockiert.

## <a name="examples"></a>Beispiele

### <a name="hierarchical-data"></a>Hierarchische Daten

1. Fügen Sie ein [**Button**](../controls/control-button.md) -Steuerelement ein, und legen **Sie dessen onselect** -Eigenschaft auf diese Formel fest.

    ```powerapps-comma
    ClearCollect( CityPopulations;
        { City: "London";    Country: "United Kingdom"; Population: 8615000 };
        { City: "Berlin";    Country: "Germany";        Population: 3562000 };
        { City: "Madrid";    Country: "Spain";          Population: 3165000 };
        { City: "Hamburg";   Country: "Germany";        Population: 1760000 };
        { City: "Barcelona"; Country: "Spain";          Population: 1602000 };
        { City: "Munich";    Country: "Germany";        Population: 1494000 }
    );;
    ClearCollect( CitiesByCountry; GroupBy( CityPopulations; "Country"; "Cities" ) )
    ```

1. Wählen Sie die Schaltfläche, während Sie die Alt-Taste gedrückt halten.

    Die Sammlung " **citiesbycountry** " wird mit dieser Datenstruktur erstellt, die Sie anzeigen können, indem Sie im Menü " **Datei** " die Option **Sammlungen** auswählen und dann den Namen der Sammlung auswählen.

    > [!div class="mx-imgBorder"]
    > ![der citiesbycountry-Sammlung](media/function-json/cities-grouped.png)

    Sie können diese Auflistung auch anzeigen, indem Sie **Datei** > **App-Einstellungen** > **Erweiterte Einstellungen** auswählen > **Ergebnis Ansicht der Formel Leiste aktivieren**, den Namen der Sammlung in der Bearbeitungs Leiste auswählen und dann den Pfeil nach unten neben dem Namen der Sammlung in der Bearbeitungs Leiste auswählen.

    > [!div class="mx-imgBorder"]
    > ![Sammlung in der Ergebnis Ansicht der Formel Leiste](media/function-json/cities-grouped-resultview.png)

1. Fügen Sie eine weitere Schaltfläche ein, und legen **Sie die onselect** -Eigenschaft auf diese Formel fest

    ```powerapps-comma
    Set( CitiesByCountryJSON; JSON( CitiesByCountry ) )
    ```

    Diese Formel legt die globale Variable " **citiesbycountryjson** " auf die JSON-Darstellung für " **citiesbycountry**" fest.

1. Wählen Sie die Schaltfläche, während Sie die Alt-Taste gedrückt halten.

1. Fügen Sie ein [**Label**](../controls/control-text-box.md) -Steuerelement ein, und legen Sie dessen Eigenschaft **Text** auf diese Variable fest.

    ```powerapps-comma
    CitiesByCountryJSON
    ```

    Die Bezeichnung zeigt dieses Ergebnis an, und zwar in einer einzelnen Zeile ohne Leerzeichen, die für die Übertragung über ein Netzwerk geeignet ist:

    ```json
    [{"Cities":[{"City":"London","Population":8615000}],"Country":"United Kingdom"},{"Cities":[{"City":"Berlin","Population":3562000},{"City":"Hamburg","Population":1760000},{"City":"Munich","Population":1494000}],"Country":"Germany"},{"Cities":[{"City":"Madrid","Population":3165000},{"City":"Barcelona","Population":1602000}],"Country":"Spain"}]
    ```

1. Ändern Sie die Formel der zweiten Schaltfläche, um die Ausgabe lesbarer zu machen.

    ```powerapps-comma
    Set( CitiesByCountryJSON; JSON(CitiesByCountry; JSONFormat.IndentFour ))
    ```

1. Wählen Sie die zweite Schaltfläche, während Sie die Alt-Taste gedrückt halten.

    Die Bezeichnung zeigt das besser lesbare Ergebnis.

    ```json
    [
        {
            "Cities": [
                {
                    "City": "London",
                    "Population": 8615000
                }
            ],
            "Country": "United Kingdom"
        },
        {
            "Cities": [
                {
                    "City": "Berlin",
                    "Population": 3562000
                },
                {
                    "City": "Hamburg",
                    "Population": 1760000
                },
                {
                    "City": "Munich",
                    "Population": 1494000
                }
            ],
            "Country": "Germany"
        },
        {
            "Cities": [
                {
                    "City": "Madrid",
                    "Population": 3165000
                },
                {
                    "City": "Barcelona",
                    "Population": 1602000
                }
            ],
            "Country": "Spain"
        }
    ]
    ```

### <a name="images-and-media-in-base64"></a>Bilder und Medien in Base64

1. Fügen Sie ein [**Bild**](../controls/control-image.md) Steuerelement hinzu.

    Dieses Steuerelement bringt **sampleImage** damit ein.

1. Fügen Sie ein [**Button**](../controls/control-button.md) -Steuerelement hinzu, und legen Sie dessen **onselect** -Eigenschaft auf diese Formel fest.

    ```powerapps-comma
    Set( ImageJSON; JSON( SampleImage; JSONFormat.IncludeBinaryData ) )
    ```

1. Wählen Sie die Schaltfläche, während Sie die Alt-Taste gedrückt halten.

1. Fügen Sie eine Bezeichnung hinzu, und legen Sie deren **Text** -Eigenschaft auf diese Variable fest.

    ```powerapps-comma
    ImageJSON
    ```

1. Ändern Sie die Größe des Steuer Elements, und reduzieren Sie den Schrift Grad nach Bedarf, um den größten Teil des Ergebnisses anzuzeigen.

    Die Bezeichnung zeigt die Text Zeichenfolge, die die **JSON** -Funktion aufgezeichnet hat.

    ```json
    "data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0idXRmLTgiPz4NCjxzdmcgdmVyc2lvbj0iMS4xIg0KCSB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHhtbG5zOnhsaW5rPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5L3hsaW5rIiB4bWxuczphPSJodHRwOi8vbnMuYWRvYmUuY29tL0Fkb2JlU1ZHVmlld2VyRXh0ZW5zaW9ucy8zLjAvIg0KCSB4PSIwcHgiIHk9IjBweCIgd2lkdGg9IjI3MHB4IiBoZWlnaHQ9IjI3MHB4IiBlbmFibGUtYmFja2dyb3VuZD0ibmV3IDAgMCAyNzAgMjcwIiB4bWw6c3BhY2U9InByZXNlcnZlIj4NCgk8ZyBjbGFzcz0ic3QwIj4NCgkJPHJlY3QgeT0iMC43IiBmaWxsPSIjRTlFOUU5IiB3aWR0aD0iMjY5IiBoZWlnaHQ9IjI2OS4zIi8+DQoJCTxwb2x5Z29uIGZpbGw9IiNDQkNCQ0EiIHBvaW50cz0iMjc3LjksMTg3LjEgMjQ1LDE0My40IDE4OC42LDIwMi44IDc1LDgwLjUgLTQuMSwxNjUuMyAtNC4xLDI3MiAyNzcuOSwyNzIiLz4NCgkJPGVsbGlwc2UgZmlsbD0iI0NCQ0JDQSIgY3g9IjIwMi40IiBjeT0iODQuMSIgcng9IjI0LjQiIHJ5PSIyNC4zIi8+DQoJPC9nPg0KPC9zdmc+"
    ```
