---
title: JSON-Funktion | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die JSON-Funktion in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/02/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 74e10a5b073e16ba9f35139441c94e9911446a0f
ms.sourcegitcommit: 2084789802fc5134dbeb888e759cced46019a017
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2019
ms.locfileid: "66736397"
---
# <a name="json-function-in-powerapps"></a>JSON-Funktion in PowerApps

Generiert eine JSON-Text-Zeichenfolge für eine Tabelle, einen Datensatz oder einen Wert an.

## <a name="description"></a>Beschreibung

Die **JSON** Funktion gibt die JavaScript Object Notation (JSON)-Darstellung einer Datenstruktur als Text, damit es zum Speichern oder übertragen über ein Netzwerk geeignet ist. [ECMA-404](http://www.ecma-international.org/publications/files/ECMA-ST/ECMA-404.pdf) und [IETF RFC 8259](https://tools.ietf.org/html/rfc8259) beschreiben Sie das Format, das häufig von JavaScript und anderen Programmiersprachen verwendet wird.

Canvas-apps unterstützen die [Datentypen](data-types.md) , die diese Tabelle enthält, mit den Details für ihre Textdarstellung:

| Datentyp | Beschreibung | Ergebnis-Beispiel |
|-----------|-------------|---------|
| **Boolean** | *"true"* oder *"false"* . | `true` |
| **Farbe** | Eine Zeichenfolge, die die 8-stellige hexadezimale Darstellung für die Farbe enthält. Diese Darstellung hat das Format #*Rrggbbaa*, wobei *rr* ist die Rotkomponente, *Gg* ist Grün, *bb* ist Blau und *aa* ist der alpha-Kanal. Für den Alphakanal **00** ist vollständig transparent, und **ff** vollständig deckend ist. Sie können die Zeichenfolge, die übergeben die [ **ColorValue** ](function-colors.md) Funktion.  | `"#102030ff"` |
| **Währung** | Zahl, die die entsprechenden Dezimaltrennzeichen für die Sprache des Benutzers verwendet. Wissenschaftliche Schreibweise wird verwendet, wenn erforderlich. | `1.345` |
| **Datum** | Zeichenfolge, das Datum im ISO 8601 enthält **jjjj-mm-tt** Format. | `"2019-03-31"` |
| **DateTime** | Zeichenfolge, die von einem ISO 8601-Datum/Uhrzeit enthält. Datum/Uhrzeit-Werte sind in UTC, als der Ende "Z" steht.  | `"2019-03-31T22:32:06.822Z"`  |
| **GUID** | Eine Zeichenfolge, die den GUID-Wert enthält. Buchstaben sind Kleinbuchstaben. | `"751b58ac-380e-4a04-a925-9f375995cc40"`
| **Abbildung Medien** | Wenn **IncludeBinaryData** angegeben ist, wird von Mediendateien in einer Zeichenfolge codiert werden. Web-Verweise, die die Verwendung des http: oder Https: URL-Schema werden nicht geändert werden. Verweise auf binäre Daten im Arbeitsspeicher mit codiert sind die ["Daten:*Mimetype*; base64,..."](https://en.wikipedia.org/wiki/Data_URI_scheme) Format. In-Memory-Daten enthält Images, die Benutzer mithilfe der Erfassen der [ **Kamera** ](../controls/control-camera.md) -Steuerelement und alle anderen Verweise mit der Appres: und -Blob: URL-Schemas.| `"data:image/jpeg;base64,/9j/4AA..."` |
| **Anzahl** | Zahl, die die entsprechenden Dezimaltrennzeichen für die Sprache des Benutzers verwendet. Wissenschaftliche Schreibweise wird verwendet, wenn erforderlich. | `1.345` |
| **Option&nbsp;set** | Numerischer Wert der Option festgelegt, nicht die Bezeichnung, die für die Anzeige verwendet wird. Der numerische Wert wird verwendet, da es sich um sprachunabhängig ist.  | `1001` |
| **Zeit** | Zeichenfolge mit einer ISO-8601 *ss.fff* Format.  | `"23:12:49.000"` |
| **Record** | Durch Trennzeichen getrennte Liste, zwischen **{** und **}** , Felder und ihre Werte. Diese Notation ähnelt, die für Datensätze in der Canvas-apps, aber der Name ist immer in doppelte Anführungszeichen ein. Dieses Format unterstützt keine Datensätze, die für die n: 1 Beziehungen basieren.  | `{ "First Name": "Fred", "Age": 21 }` |
| **Tabelle** | Durch Trennzeichen getrennte Liste, zwischen **[** und **]** , der Datensätze. Dieses Format unterstützt keine Tabellen, die für die 1: n Beziehungen basieren.  | `[ { "First Name": "Fred", "Age": 21 }, { "First Name": "Jean", "Age": 20 } ]` |
| **Two&nbsp;option** | Boolescher Wert, der zwei-Option *"true"* oder *"false"* , nicht die Bezeichnung, die für die Anzeige verwendet wird. Der boolesche Wert wird verwendet, da es sich um sprachunabhängig ist. | `false` |
| **Hyperlink, Text** | Eine Zeichenfolge in doppelte Anführungszeichen ein. Die Funktion eingebettete doppelte Anführungszeichen mit einem umgekehrten Schrägstrich mit Escapezeichen zu versehen, ersetzt der neue Zeilen mit "\n" und andere standard-JavaScript-Ersetzungen macht. | `"This is a string."` |

Geben Sie den optionalen *Format* Argument, um zu steuern, wie lesbare Ergebnis und wie nicht unterstützt und binären Datentypen behandelt werden. In der Standardeinstellung die Ausgabe ist so kompakt wie möglich, ohne unnötige Leerzeichen oder Zeilenumbrüche, und nicht unterstützten Datentypen und binäre Daten sind nicht zulässig. Sie können mehrere Formate kombinieren, bei der Angabe der **&** Operator.

| JSONFormat-Enumeration | Beschreibung |
|-----------------|-------------|
| **Komprimieren** | Standard.  Die Ausgabe ist so kompakt wie möglich ohne zusätzliche Leerzeichen oder Zeilenumbrüche. |
| **IndentFour** | Um die Lesbarkeit zu verbessern, wird die Ausgabe enthält eine neue Zeile für jede Spalte und die Schachtelungsebene und vier Leerzeichen verwendet, für die einzelnen Einzugsebenen. |
| **IncludeBinaryData** | Das Ergebnis enthält das Bild, video und Audio Clips Spalten. Dieses Format kann erheblich vergrößern Sie das Ergebnis des und beeinträchtigt die Leistung Ihrer app. |
| **IgnoreBinaryData** | Das Ergebnis enthält keine Bild, video oder Audio Clips Spalten. Wenn Sie keines von beiden angeben **IncludeBinaryData** noch **IgnoreBinaryData**, die Funktion erzeugt einen Fehler aus, wenn es sich um binäre Daten trifft. |
| **IgnoreUnsupportedTypes** | Nicht unterstützte Datentypen sind zulässig, aber das Ergebnis nicht enthalten sind. Standardmäßig werden von nicht unterstützten Datentypen einen Fehler erzeugen. |

Verwenden der [ **ShowColumns** und **DropColumns** ](function-table-shaping.md) Funktionen steuern, welche Daten das Ergebnis enthält und nicht unterstützten Datentypen zu löschen.

Da **JSON** kann Arbeitsspeicher- und Compute-intensiv ist, können Sie diese Funktion nur in [-Verhalten funktioniert](../working-with-formulas-in-depth.md). Sie können das Ergebnis von erfassen **JSON** in einer [Variable](../working-with-variables.md), die Sie dann im Datenfluss verwenden können.

Wenn eine Spalte einen Anzeigenamen ein, und einen logischen Namen aufweist, enthält das Ergebnis den logischen Name. Anzeigenamen entsprechend die Sprache der app-Benutzer und können daher für die Übertragung von Daten in einen gemeinsamen Dienst nicht geeignet.

## <a name="syntax"></a>Syntax

**JSON**( *DataStructure* [, *Format* ])

* *DataStructure* : erforderlich. Die Datenstruktur in JSON konvertieren.  Tabellen, Datensätze und primitive Werte werden unterstützt und beliebig geschachtelt an.
* *Format* : Optional.  **JSONFormat** Enum-Wert. Der Standardwert ist **Compact**, die keine Zeilenumbrüche oder Leerzeichen hinzufügen und blockiert die Binärdaten und nicht unterstützte Spalten.

## <a name="examples"></a>Beispiele

### <a name="hierarchical-data"></a>Hierarchische Daten

1. Fügen Sie eine [ **Schaltfläche** ](../controls/control-button.md) steuern, und legen dessen **OnSelect** -Eigenschaft auf diese Formel.

    ```powerapps-dot
    ClearCollect( CityPopulations,
        { City: "London",    Country: "United Kingdom", Population: 8615000 },
        { City: "Berlin",    Country: "Germany",        Population: 3562000 },
        { City: "Madrid",    Country: "Spain",          Population: 3165000 },
        { City: "Hamburg",   Country: "Germany",        Population: 1760000 },
        { City: "Barcelona", Country: "Spain",          Population: 1602000 },
        { City: "Munich",    Country: "Germany",        Population: 1494000 }
    );
    ClearCollect( CitiesByCountry, GroupBy( CityPopulations, "Country", "Cities" ) )
    ```

1. Wählen Sie die Schaltfläche, während Sie die Alt-Taste gedrückt halten.

    Die **CitiesByCountry** Sammlung wird erstellt, mit dieser Datenstruktur, das Sie durch Auswahl anzeigen können **Sammlungen** auf die **Datei** Menü auswählen und dann auf den Namen des der Auflistung.

    > [!div class="mx-imgBorder"]
    > ![CitiesByCountry-Auflistung](media/function-json/cities-grouped.png)

    Sie können diese Sammlung auch anzeigen, dazu **Datei** > **Anwendungseinstellungen** > **Erweiterte Einstellungen**  >   **Aktivieren Sie die Bearbeitungsleiste Ergebnisansicht**, wählen Sie in der Bearbeitungsleiste den Namen der Sammlung, und wählen Sie dann auf den Pfeil nach unten neben dem Namen der Sammlung unter der Bearbeitungsleiste angezeigt.

    > [!div class="mx-imgBorder"]
    > ![Die Auflistung in der Bearbeitungsleiste-Ergebnisansicht](media/function-json/cities-grouped-resultview.png)

1. Einfügen einer weiteren Schaltfläche, und legen Sie dessen **OnSelect** -Eigenschaft auf diese Formel:

    ```powerapps-dot
    Set( CitiesByCountryJSON, JSON( CitiesByCountry ) )
    ```

    Diese Formel wird die globale Variable **CitiesByCountryJSON** die JSON-Darstellung für **CitiesByCountry**.

1. Wählen Sie die Schaltfläche, während Sie die Alt-Taste gedrückt halten.

1. Fügen Sie eine [ **Bezeichnung** ](../controls/control-text-box.md) steuern, und legen dessen **Text** Eigenschaft, um diese Variable.

    ```powerapps-dot
    CitiesByCountryJSON
    ```

    Die Bezeichnung zeigt dieses Ergebnis, alle in einer einzelnen Zeile ohne Leerzeichen, für die Übertragung über ein Netzwerk geeignet ist:

    ```json
    [{"Cities":[{"City":"London","Population":8615000}],"Country":"United Kingdom"},{"Cities":[{"City":"Berlin","Population":3562000},{"City":"Hamburg","Population":1760000},{"City":"Munich","Population":1494000}],"Country":"Germany"},{"Cities":[{"City":"Madrid","Population":3165000},{"City":"Barcelona","Population":1602000}],"Country":"Spain"}]
    ```

1. Ändern Sie die zweite Schaltfläche Formel ein, um die Ausgabe besser lesbar zu machen.

    ```powerapps-dot
    Set( CitiesByCountryJSON, JSON(CitiesByCountry, JSONFormat.IndentFour ))
    ```

1. Wählen Sie die zweite Schaltfläche, während Sie die Alt-Taste gedrückt halten.

    Die Bezeichnung zeigt das Ergebnis besser lesbarere.

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

### <a name="images-and-media-in-base64"></a>Bildern und Medien in base64

1. Hinzufügen einer [ **Image** ](../controls/control-image.md) Steuerelement.

    Dieses Steuerelement wird **SampleImage** mit.

1. Hinzufügen einer [ **Schaltfläche** ](../controls/control-button.md) steuern, und legen dessen **OnSelect** -Eigenschaft auf diese Formel.

    ```powerapps-dot
    Set( ImageJSON, JSON( SampleImage, JSONFormat.IncludeBinaryData ) )
    ```

1. Wählen Sie die Schaltfläche, während Sie die Alt-Taste gedrückt halten.

1. Fügen Sie eine Bezeichnung hinzu, und legen dessen **Text** Eigenschaft, um diese Variable.

    ```powerapps-dot
    ImageJSON
    ```

1. Die Größe des Steuerelements, und reduzieren Sie den Schriftgrad aus, nach Bedarf, um die meisten der das Ergebnis anzuzeigen.

    Die Bezeichnung zeigt der Zeichenfolge, die die **JSON** Funktion erfasst.

    ```json
    "data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0idXRmLTgiPz4NCjxzdmcgdmVyc2lvbj0iMS4xIg0KCSB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHhtbG5zOnhsaW5rPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5L3hsaW5rIiB4bWxuczphPSJodHRwOi8vbnMuYWRvYmUuY29tL0Fkb2JlU1ZHVmlld2VyRXh0ZW5zaW9ucy8zLjAvIg0KCSB4PSIwcHgiIHk9IjBweCIgd2lkdGg9IjI3MHB4IiBoZWlnaHQ9IjI3MHB4IiBlbmFibGUtYmFja2dyb3VuZD0ibmV3IDAgMCAyNzAgMjcwIiB4bWw6c3BhY2U9InByZXNlcnZlIj4NCgk8ZyBjbGFzcz0ic3QwIj4NCgkJPHJlY3QgeT0iMC43IiBmaWxsPSIjRTlFOUU5IiB3aWR0aD0iMjY5IiBoZWlnaHQ9IjI2OS4zIi8+DQoJCTxwb2x5Z29uIGZpbGw9IiNDQkNCQ0EiIHBvaW50cz0iMjc3LjksMTg3LjEgMjQ1LDE0My40IDE4OC42LDIwMi44IDc1LDgwLjUgLTQuMSwxNjUuMyAtNC4xLDI3MiAyNzcuOSwyNzIiLz4NCgkJPGVsbGlwc2UgZmlsbD0iI0NCQ0JDQSIgY3g9IjIwMi40IiBjeT0iODQuMSIgcng9IjI0LjQiIHJ5PSIyNC4zIi8+DQoJPC9nPg0KPC9zdmc+"
    ```
