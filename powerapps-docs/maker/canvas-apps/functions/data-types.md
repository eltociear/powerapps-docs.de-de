---
title: Datentypen | Microsoft-Dokumentation
description: Datentypen in Canvas-apps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/07/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 87af59cfc755ea7ad33f3891ae4f27589318eddc
ms.sourcegitcommit: ee1960fe32136a621e653d6ff2f13d87017830a2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2020
ms.locfileid: "77145442"
ms.PowerAppsDecimalTransform: true
---
# <a name="data-types-in-canvas-apps"></a>Datentypen in Canvas-apps

Informationen fließen durch eine app in kleinen, diskreten Werten, ähnlich wie die Zellen einer Tabelle. Beispielsweise würden Daten in einem **Geburts** Feld und einem **Anniversary** -Feld als **Datums** Wert durchlaufen, der das Jahr, den Monat und den Tag einschließt. Die APP weiß, wie diese Werte formatiert werden, die Eingabe auf die für die einzelnen geeigneten Elemente beschränken und die Werte für eine Datenbank freigeben. Geburtstage unterscheiden sich von Jubiläen bis hin zu Personen, aber das System verarbeitet sie genau auf die gleiche Weise. In diesem Fall ist **Date** ein Beispiel für einen- [Datentyp](https://en.wikipedia.org/wiki/Data_type).

Dieser Artikel enthält Details zu den Datentypen, die von Canvas-Apps unterstützt werden. Wenn eine APP eine Verbindung mit einer externen Datenquelle herstellt, wird jeder Datentyp in dieser Quelle einem Datentyp für Canvas-apps zugeordnet.

| Datentyp | Beschreibung | Beispiele |
|-----------|-------------|---------|
| **Booleschen** | Ein *true* -oder *false* -Wert.  Kann direkt in **if**-, **Filter** -und anderen Funktionen ohne einen-Vergleich verwendet werden.  | *TRUE* |
| **Farbe** | Eine Farb Angabe, einschließlich eines Alphakanals. | **Color.Red**<br>**ColorValue ("#102030")**<br>**RGBA (255, 128, 0, 0,5)** |
| **Währung** | Ein Währungswert, der in einer Gleit Komma Zahl gespeichert wird. Währungswerte entsprechen den Zahlenwerten mit Währungs Formatierungsoptionen.  | **123**<br>**4,56** |
| **Date** | Ein Datum ohne Uhrzeit in der Zeitzone des App-Benutzers. | **Datum (2019, 5, 16)** |
| **DateTime** | Ein Datum mit einer Uhrzeit in der Zeitzone des App-Benutzers. | **DateTimeValue ("Mai 16, 2019 1:23:09 Uhr")** |
| **GUID** | Ein [Global eindeutiger Bezeichner](https://en.wikipedia.org/wiki/Universally_unique_identifier). | **GUID ()**<br>**GUID ("123e4567-e89b-12d3-A456-426655440000")** |
| **Hyperlinks** | Eine Text Zeichenfolge, die einen Link enthält. | **„https://powerapps.microsoft.com“** |
| **Bild** | Eine URI-Text Zeichenfolge [(Universal Resource Identifier)](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier) für ein Bild im JPEG-, PNG-, SVG-, GIF-oder anderen gängigen Webbild Format. | **MyImage** als App-Ressource hinzugefügt<br>**„https://northwindtraders.com/logo.jpg“**<br>**"appres://blobmanager/7b12ffa2..."** |
| **Medien** | Eine URI-Text Zeichenfolge für eine Video-oder Audioaufzeichnung. | **MyVideo** als App-Ressource hinzugefügt<br>**„https://northwindtraders.com/intro.mp4“**<br>**"appres://blobmanager/3ba411c..."** |
| **Einigen** | Eine Gleit Komma Zahl. | **123**<br>**-4,567**<br>**8.903e121** |
| **Options Satz** | Eine Auswahl aus einer Reihe von Optionen, die durch eine Zahl unterstützt werden. Dieser Datentyp kombiniert eine lokalisierbare Text Bezeichnung mit einem numerischen Wert. Die Bezeichnung wird in der App angezeigt, und der numerische Wert wird gespeichert und für Vergleiche verwendet. | **Thisitem. OrderStatus** |
| **Datensatz** | Ein Datensatz von Datenwerten. Dieser Verbund Datentyp enthält Instanzen anderer Datentypen, die in diesem Thema aufgeführt sind. Weitere Informationen finden Sie [unter Arbeiten mit Tabellen](../working-with-tables.md). | **{Company: "Northwind Traders";<br>Personal: 35; <br>Non Profit: false}** |
| **Daten Satz Verweis** | Ein Verweis auf einen Datensatz in einer Entität. Solche Verweise werden häufig bei polymorphen Such Vorgängen verwendet. Weitere Informationen finden Sie [unter Arbeiten mit verweisen](../working-with-references.md).| **Zuerst (Konten). Eigentor** |
| **Tabelle** | Eine Tabelle mit Datensätzen.  Alle Datensätze müssen die gleichen Namen für Ihre Felder mit denselben Datentypen aufweisen, und ausgelassene Felder werden als *leer*behandelt. Dieser Verbund Datentyp enthält Instanzen anderer Datentypen, die in diesem Thema aufgeführt sind. Weitere Informationen finden Sie [unter Arbeiten mit Tabellen](../working-with-tables.md). | **Table ({FirstName: "Sidney";<br>LastName: "Higa"}; <br>{FirstName: "Nancy";<br>LastName: "Anderson"})**
| **Text** | Eine Unicode-Text Zeichenfolge. | **"Hello, World"** |
| **Zeit** | Eine Uhrzeit ohne Datum in der Zeitzone des App-Benutzers. | **Zeit (11, 23, 45)** |
| **Zwei Optionen** | Eine Auswahl aus einer Reihe von zwei Optionen, die von einem booleschen Wert unterstützt werden. Dieser Datentyp kombiniert eine lokalisierbare Text Bezeichnung mit einem booleschen Wert. Die Bezeichnung wird in der App angezeigt, und der boolesche Wert wird gespeichert und für Vergleiche verwendet. | **Thisitem. steuerlich** |

Viele dieser Datentypen sind ähnlich und haben dieselbe zugrunde liegende Darstellung, z. b. ein **Hyperlink** -Feld, das als **Text**behandelt wird.  Die zusätzlichen Datentypen bieten eine bessere Standard Erfahrung in Formularen und anderen Steuerelementen.

## <a name="blank"></a>Leer

Alle Datentypen können den Wert *blank* aufweisen (d. h. kein Wert). Der Begriff "Null" wird häufig in Datenbanken für dieses Konzept verwendet.  

Verwenden Sie die **leere** Funktion mit der **set** -oder **Patch** -Funktion, um eine Variable oder ein Feld auf " *blank*" festzulegen. Beispielsweise entfernt **Set (x, Blank ())** alle Werte in der globalen Variablen **x**.  

Testen Sie den Wert mit der [**isblank**](function-isblank-isempty.md) -Funktion auf einen *leeren* Wert. Ersetzen Sie mögliche *leere* Werte durch nicht*leere* Werte mithilfe der [**COALESCE**](function-isblank-isempty.md) -Funktion.

Da alle Datentypen *leer*unterstützen, verfügen die **booleschen** und **zwei Options** Datentypen über drei mögliche Werte.

## <a name="text-hyperlink-image-and-media"></a>Text, Hyperlink, Bild und Medien

Alle vier dieser Datentypen basieren auf einer [Unicode](https://en.wikipedia.org/wiki/Unicode) -Text Zeichenfolge.

### <a name="embedded-text"></a>Eingebetteter Text

Eingebettete Text Zeichenfolgen in einer Formel sind in doppelte Anführungszeichen eingeschlossen.  Verwenden Sie zwei doppelte Anführungszeichen, um ein einzelnes doppeltes Anführungszeichen in der Text Zeichenfolge darzustellen.  Verwenden Sie beispielsweise die folgende Formel in der **onselect** -Eigenschaft eines [**Button**](../controls/control-button.md) -Steuer Elements:

```powerapps-comma
Notify( "Jane said ""Hello, World!""" )
```

führt zu einem Banner, wenn die Schaltfläche gedrückt wird, wobei die erste und die letzte doppelte Anführungszeichen ausgelassen werden (da Sie die Text Zeichenfolge begrenzen) und die wiederholten doppelten Anführungszeichen um **Hello, World!** werden durch ein einzelnes doppeltes Anführungszeichen ersetzt:

![Popup Benachrichtigung mit der Meldung Andrea sagte "Hello, World"](media/data-types/literal-string.png)

Einfache Anführungszeichen werden nicht für [Bezeichnernamen](operators.md#identifier-names) verwendet, die Sonderzeichen enthalten und in einer Text Zeichenfolge keine Bedeutung haben.  

### <a name="image-and-media-resources"></a>Bild-und Medienressourcen

Über das Menü **Datei** können Sie Bild-, Video-und Audiodateien als App-Ressourcen hinzufügen. Der Name der importierten Datei wird zum Ressourcennamen in der app. In dieser Grafik wurde das Northwind Traders-Logo mit dem Namen **nwindlogo**zu einer app hinzugefügt:

![](media/data-types/nwind-resource.png)

Wenn Sie diese Ressource in einer App verwenden möchten, geben Sie Sie in der **Image** -Eigenschaft eines [**Image**](../controls/control-image.md) -Steuer Elements an:

![](media/data-types/nwind-image.png)

### <a name="uris-for-images-and-other-media"></a>URIs für Bilder und andere Medien

Wenn Sie die **Text** -Eigenschaft eines [**Label**](../controls/control-text-box.md) -Steuer Elements auf **nwindlogo**festgelegt haben, können Sie sich näher mit dem letzten Beispiel befassen. Die Bezeichnung zeigt eine Text Zeichenfolge an:

![](media/data-types/nwind-text.png)

Canvas-Apps verweisen auf jedes Bild oder jede andere Mediendatei, ob Sie in der Cloud oder als App-Ressource durch eine URI-Text Zeichenfolge hinzugefügt wird.

Beispielsweise akzeptiert die **Image** -Eigenschaft eines Image-Steuer Elements nicht nur App-Ressourcen, sondern auch Links zu Bildern im Web, z. b. "https://northwindtraders.com/logo.jpg". Die-Eigenschaft akzeptiert auch Inline Bilder, die das [Daten-URI-Schema](https://en.wikipedia.org/wiki/Data_URI_scheme)verwenden, wie in diesem Beispiel:

```powerapps-comma
"data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAkAAAAFAQMAAACtnVQoAAAABlBMVEUAAAB0J3UMNU6VAAAAAXRSTlMAQObYZgAAABRJREFUCNdjUGJgCGVg6GgAkkA2AA8/AffqCEBsAAAAAElFTkSuQmCC"
```

Dieser URI zeigt eine hochskalierte Version von zwei lila Diamanten an:

![](media/data-types/double-diamonds.png)

Sie können das neueste Bild, das in einem [**Kamera**](../controls/control-camera.md) Steuerelement aufgezeichnet wurde, anzeigen, wenn Sie die **Image** -Eigenschaft eines Bild-Steuer Elements auf die **Photo** -Eigenschaft des Kamera-Steuer Elements festlegen. Die app enthält das Bild im Speicher, und die **Photo** -Eigenschaft des Kamera Steuer Elements gibt einen URI-Verweis auf das Bild zurück. Sie können z. b. ein Bild sehen, und die **Photo** -Eigenschaft der Kamera kann **"appres://blobmanager/7b12ffa2ea4547e5b3812cb1c7b0a2a0/1"** zurückgeben.

Sie verwenden einen URI, um auf ein Bild oder eine andere Mediendatei zu verweisen, die in einer Datenbank gespeichert ist. Auf diese Weise Ruft die APP die tatsächlichen Daten erst ab, wenn Sie tatsächlich benötigt wird. Beispielsweise könnte eine Anlage in einer Common Data Service Entität **"appres://DataSources/Contacts/Table/..."** zurückgeben, wie im Kamera Beispiel, Sie können dieses Bild anzeigen, indem Sie die **Image** -Eigenschaft eines Image-Steuer Elements auf diesen Verweis festlegen, der die Binärdaten abruft.

Wenn Sie einen Medien Datentyp, z. b. ein Bild, in einer Datenbank speichern, sendet die APP das eigentliche Image oder die tatsächlichen Mediendaten, nicht den URI-Verweis.

### <a name="size-limits"></a>Größen Limits

Als Text Zeichenfolgen und URIs haben diese Datentypen keinen voreingestellten Grenzwert für Ihre Länge.

Die Binärdaten, auf die diese Datentypen verweisen, haben auch keine Voreinstellung für die Größe. Beispielsweise kann ein Bild, das über das Kamera Steuerelement aufgezeichnet wird, das nun als **"appres://..."** bezeichnet wird, so groß und hoch aufgelöst sein, wie es die Kamera des Geräts erreichen kann. Die Auflösung, die Framerate und andere Attribute von Mediendateien sind nicht durch den-Datentyp eingeschränkt, aber bestimmte Steuerelemente für die Wiedergabe und Erfassung von Medien können über eigene Einschränkungen verfügen.

Allerdings unterliegen alle Datengrößen der Menge an verfügbarem Arbeitsspeicher in der app. Browser, die auf einem Desktop Computer ausgeführt werden, unterstützen in der Regel mehr als 100 Megabyte an Daten. Die Menge des verfügbaren Arbeitsspeichers auf einem Gerät, z. b. ein Telefon, kann jedoch weitaus niedriger sein, in der Regel im Bereich von 30-70 Megabyte. Testen Sie gängige Szenarien auf allen Geräten, auf denen die app ausgeführt werden soll, um zu bestimmen, ob Ihre APP innerhalb dieser Grenzwerte ausgeführt wird.

Es wird empfohlen, Daten im Arbeitsspeicher nur so lange wie nötig aufzunehmen. Hochladen von Bildern in eine Datenbank, sobald Sie dies möglich sind. Laden Sie Images nur herunter, wenn Sie vom Benutzer der APP angefordert werden.

## <a name="number-and-currency"></a>Anzahl und Währung

Die Datentypen " **Number** " und " **Currency** " verwenden den [IEEE 754-Gleit Komma Wert mit doppelter Genauigkeit](https://en.wikipedia.org/wiki/IEEE_754). Dieser Standard bietet einen sehr großen Bereich von Zahlen, der von – 1,79769 x 10<sup>308</sup> bis 1,79769 x 10<sup>308</sup>verwendet werden kann. Der kleinste Wert, der dargestellt werden kann, ist 5 x 10<sup>– 324</sup>.

Canvas-Apps können ganze Zahlen (oder ganze Zahlen) genau zwischen – 9.007.199.254.740.991 (– (2<sup>53</sup> – 1)) und 9.007.199.254.740.991 (2<sup>53</sup> – 1), einschließlich, darstellen. Dieser Bereich ist größer als 32 die ganzzahligen Datentypen (oder 4 Byte), die von Datenbanken häufig verwendet werden. Canvas-Apps können jedoch keine ganzzahligen Datentypen mit einer Größe von 64 Bit (oder 8 Byte) darstellen. Möglicherweise möchten Sie die Zahl in einem Textfeld speichern oder eine berechnete Spalte verwenden, um eine Kopie der Zahl in einem Textfeld zu erstellen, damit Sie in der Canvas-APP einem **Text** Datentyp zugeordnet wird. Auf diese Weise können Sie diese Werte halten, anzeigen und eingeben sowie vergleichen, um zu bestimmen, ob Sie gleich sind. in diesem Formular können Sie jedoch keine numerischen Berechnungen ausführen.

Gleit Komma Arithmetik ist ungefähre Werte, daher kann es manchmal zu unerwarteten Ergebnissen mit vielen dokumentierten Beispielen führen. Sie erwarten möglicherweise, dass die Formel **55/100 * 100** genau 55 und **(55/100 * 100)-55** zurückgibt, um genau 0 (null) zurückzugeben. Die zweite Formel gibt jedoch 7,1054 x 10<sup>– 15</sup>zurück, die sehr klein, aber nicht 0 (null) ist. Dieser kleine Unterschied verursacht in der Regel kein Problem, und die APP rundet Sie auf, wenn das Ergebnis angezeigt wird. Kleine Unterschiede können jedoch in nachfolgenden Berechnungen zusammengesetzt werden und scheinen die falsche Antwort zu erhalten.

Datenbanksysteme speichern häufig Währungen und führen Berechnungen mithilfe der Dezimalzahl aus, die einen kleineren Bereich bietet, aber eine bessere Kontrolle über die Genauigkeit bietet. Standardmäßig ordnen Canvas-apps Währungen in und aus Gleit Komma Werten zu. Daher kann sich das Ergebnis von Berechnungen unterscheiden, die in einem nativen Decimal-Datentyp durchgeführt werden. Wenn diese Art von Abweichung Probleme verursacht, können Sie mit diesen Werten als **Text**arbeiten, so wie Sie es auch mit großen Ganzzahlen tun können, die weiter oben in diesem Abschnitt beschrieben wurden.

## <a name="date-time-and-datetime"></a>Datum, Uhrzeit und DateTime

### <a name="time-zones"></a>Zeitzonen

Datums-/Uhrzeitwerte fallen in die folgenden Kategorien:

- **Lokaler Benutzer**: diese Werte werden in [UTC (koordinierte Weltzeit)](https://en.wikipedia.org/wiki/Coordinated_Universal_Time)gespeichert, aber die Zeitzone der App-Benutzer wirkt sich darauf aus, wie diese Werte von der App angezeigt werden und wie der App-Benutzer Sie angibt. Ein Beispiel: der gleiche Zeitpunkt wird für einen Benutzer in Kanada anders als für einen Benutzer in Japan angezeigt.
- **Zeit Zonen unabhängig**: die APP zeigt diese Werte auf dieselbe Weise an, und der App-Benutzer gibt Sie unabhängig von der Zeitzone auf dieselbe Weise an. Der gleiche Zeitpunkt wird für einen Benutzer in Kanada genauso wie für einen Benutzer in Japan angezeigt. App-Autoren, die nicht erwarten, dass Ihre apps in anderen Zeitzonen ausgeführt werden, verwenden diese Werte, da Sie einfacher sind.

Diese Tabelle enthält einige Beispiele:

| Datums-/Uhrzeittyp | In der Datenbank gespeicherter Wert | Angezeigter Wert und 7 Stunden, Westen von UTC | Angezeigter Wert und 4 Stunden Ost UTC |
|--------------------------|------------------------------|------------------------------|
| **Lokaler Benutzer** | Sonntag,&nbsp;&nbsp;19,&nbsp;2019<br>4:00 Uhr | Samstag,&nbsp;&nbsp;18. Mai,&nbsp;2019<br>9:00 PM | Sonntag,&nbsp;&nbsp;19,&nbsp;2019<br>8:00 Uhr |
| **Zeit Zonen unabhängig** | Sonntag,&nbsp;&nbsp;19,&nbsp;2019<br>4:00 Uhr | Sonntag,&nbsp;&nbsp;19,&nbsp;2019<br>4:00 Uhr | Sonntag,&nbsp;&nbsp;19,&nbsp;2019<br>4:00 Uhr | 

Für **lokale** Datums-/Uhrzeitangaben von Benutzern verwenden Canvas-Apps die Zeitzone des Browsers oder Geräts, aber Modell gesteuerte Apps verwenden die Einstellung des Benutzers in Common Data Service. Diese Einstellungen entsprechen in der Regel, aber die Ergebnisse unterscheiden sich, wenn sich diese Einstellungen unterscheiden

Verwenden Sie die Funktionen " [**DateAdd**](function-dateadd-datediff.md) " und " [**TimeZoneInformation**](function-dateadd-datediff.md) ", um die lokale Zeit in UTC und wieder zurück zu konvertieren.  Weitere Informationen zu diesen Funktionen finden Sie in den Beispielen am Ende der Dokumentation.

### <a name="numeric-equivalents"></a>Numerische Entsprechungen

Canvas-apps behalten und berechnen alle Datums-/Uhrzeitwerte, unabhängig davon, ob **Benutzer lokal** oder Zeitzone in UTC **unabhängig** sind. Die APP übersetzt die Werte auf der Grundlage der Zeitzone des App-Benutzers, wenn diese angezeigt werden und der App-Benutzer Sie angibt.

Wenn eine Canvas-APP einen **Zeit Zonen unabhängigen** Wert aus einer Datenquelle liest oder einen solchen Wert in eine Datenquelle schreibt, passt die APP den Wert automatisch an, um die Zeitzone des Benutzers der APP auszugleichen. Die APP behandelt den Wert dann als UTC-Wert, der mit allen anderen Datums-/Uhrzeitwerten in der APP konsistent ist. Aufgrund dieser Kompensierung wird der ursprüngliche **Zeit Zonen unabhängige** Wert angezeigt, wenn die APP den UTC-Wert für die Zeitzone der App-Benutzer anpasst.

Sie können dieses Verhalten genauer beobachten, indem Sie die [**value**](function-value.md) -Funktion verwenden, um auf den zugrunde liegenden numerischen Wert für einen Datums-/Uhrzeitwert zuzugreifen. Diese Funktion gibt den Datums-/Uhrzeitwert als die Anzahl der Millisekunden seit dem 1. Januar 1970 00:00:00.000 UTC zurück.

Da jeder Datums-/Uhrzeitwert in UTC gespeichert wird, gibt der Formel **Wert (Date (1970, 1, 1))** in den meisten Teilen der Welt keine NULL zurück, da die **Date** -Funktion ein Datum in UTC zurückgibt. Beispielsweise würde die Formel 28,8 Millionen in einer Zeitzone zurückgeben, die von UTC um acht Stunden abweicht. Diese Zahl gibt die Anzahl der Millisekunden in 8 Stunden wieder.

Zurückkehren zum obigen Beispiel:

| Datums-/Uhrzeittyp | In der Datenbank gespeicherter Wert | Angezeigter Wert und 7 Stunden, Westen von UTC | Rückgabe **Wert** Funktion |
|--------------------------|------------------------------|------------------------------|
| **Lokaler Benutzer** | Sonntag,&nbsp;&nbsp;19,&nbsp;2019<br>4:00 Uhr | Samstag,&nbsp;&nbsp;18. Mai,&nbsp;2019<br>9:00 PM | 1\.558.238.400.000<br> (Sonntag,&nbsp;&nbsp;19,&nbsp;2019<br>4:00 Uhr UTC) |
| **Zeit Zonen unabhängig** | Sonntag,&nbsp;&nbsp;19,&nbsp;2019<br>4:00 Uhr | Sonntag,&nbsp;&nbsp;19,&nbsp;2019<br>4:00 Uhr |1\.558.263.600.000<br> (Sonntag,&nbsp;&nbsp;19,&nbsp;2019<br>11:00 Uhr UTC) |

### <a name="converting-unix-times"></a>Wechseln von UNIX-Zeiten

UNIX-Zeiten entsprechen der Anzahl der Sekunden seit dem 1. Januar 1970 00:00:00 UTC. Da Canvas-apps Millisekunden anstelle von Sekunden verwenden, können Sie zwischen den beiden konvertieren, indem Sie die Multiplikation oder Division durch 1.000 durchführen.

Die UNIX-Zeit zeigt z. b. den 9. September 2001 und 01:46:40 UTC als 1 Milliarde an. Um den Datums-/Uhrzeitwert in einer Canvas-App anzuzeigen, Multiplizieren Sie diese Zahl mit 1.000, um Sie in Millisekunden zu konvertieren, und verwenden Sie Sie dann in einer [**Text**](function-text.md) Funktion. Der Formel **Text (1 Milliarde * 1000, DateTimeFormat. UTC)** gibt die Zeichenfolge **2001-09-09t01:46:40.000 z**zurück.

Diese Funktion gibt jedoch **Samstag, dem 8. September, 2001 18:46:40** zurück, wenn Sie das Format **DateTimeFormat. LongDateTime24** in einer Zeitzone verwenden, die-7 Stunden von UTC abweicht (7 Stunden West UTC). Das Ergebnis zeigt den **DateTime** -Wert ordnungsgemäß basierend auf der lokalen Zeitzone.

Um in eine Unix-Zeit zu konvertieren, teilen Sie das Ergebnis von **Wert** durch 1.000:
<br>**ROUNDDOWN (Wert (Unixtime)/1000, 0)**

Wenn Sie die UNIX-Zeit in einem **Datums** Wert zur weiteren Berechnung oder Anzeige innerhalb von powerapps benötigen, verwenden Sie die folgende Formel:
<br>**DateAdd (Datum (1970, 1, 1), Unixtime, Sekunden)**

### <a name="sql-server"></a>SQL Server

SQL Server verfügt über [ **DateTime**-, **datetime2**-und andere Datums-/Uhrzeit-Datentypen](https://docs.microsoft.com/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql?view=sql-server-2017) , die keinen Zeit Zonen Offset enthalten und nicht angeben, in welcher Zeitzone Sie sich befinden. Canvas-apps gehen davon aus, dass diese Werte in UTC gespeichert und als **Benutzer lokal**behandelt werden. Wenn die Werte Zeit Zonen unabhängig sein sollen, korrigieren Sie die UTC-Übersetzungen mithilfe der [**TimezoneOffset**](function-dateadd-datediff.md#converting-to-utc) -Funktion.

Canvas-Apps verwenden die enthaltenen Zeitzoneninformationen in **DateTimeOffset** -Feldern, wenn ein Wert in die interne UTC-Darstellung der APP umgerechnet wird. Die apps verwenden immer UTC als Zeitzone (null Zeit Zonen Offset), wenn Sie Daten schreiben.

Canvas-apps lesen und schreiben Werte des [**time**](https://docs.microsoft.com/sql/t-sql/data-types/time-transact-sql) -Datentyps in SQL Server als Text Zeichenfolgen im [ISO 8601-Duration-Format](https://en.wikipedia.org/wiki/ISO_8601#Durations). Beispielsweise müssen Sie dieses Zeichen folgen Format analysieren und die [**time**](function-date-time.md) -Funktion verwenden, um die Text Zeichenfolge **"PT2H1M39S"** **in einen Uhrzeitwert** zu konvertieren:

```powerapps-comma
With( 
    Match( "PT2H1M39S"; "PT(?:(?<hours>\d+)H)?(?:(?<minutes>\d+)M)?(?:(?<seconds>\d+)S)?" );
    Time( Value( hours ); Value( minutes ); Value( seconds ) )
)
// Result: 2:01 AM (as shown in a label control; use the Text function to see the seconds)

```

### <a name="mixing-date-and-time-information"></a>Kombinieren von Datums-und Uhrzeit Informationen

**Date**, **time**und **DateTime** haben unterschiedliche Namen, aber alle enthalten dieselben Informationen zu Datums-und Uhrzeitangaben. 

Ein **Datums** Wert kann Zeit Informationen enthalten, d. h. in der Regel Mitternacht. Ein **Uhrzeitwert** kann Datumsinformationen enthalten, die in der Regel am 1. Januar 1970 liegen. Common Data Service speichert auch Zeit Informationen mit einem reinen **Datums** Feld, zeigt jedoch standardmäßig nur die Datumsinformationen an. Ebenso unterscheiden Canvas-apps manchmal zwischen diesen Datentypen, um Standardformate und-Steuerelemente zu bestimmen.

Die direkte Addition und Subtraktion von Datums-und Uhrzeitwerten ist nicht empfehlenswert, da Zeit Zonen und andere Konvertierungen zu verwirrenden Ergebnissen führen können. Verwenden Sie die **value** -Funktion, um Datums-/Uhrzeitwerte zuerst in Millisekunden zu konvertieren und die Zeitzone des App-Benutzers zu berücksichtigen, oder verwenden Sie die Funktionen [**DateAdd**](function-dateadd-datediff.md) und [**DateDiff**](function-dateadd-datediff.md) , um einen dieser Werte hinzuzufügen oder zu subtrahieren.

## <a name="option-sets-and-two-options"></a>Optionssätze und zwei Optionen

Optionssätze und Datentypen mit zwei Optionen bieten eine Auswahl von zwei oder mehr Optionen für einen App-Benutzer. Beispielsweise kann ein Options Satz für den **Bestell Status** die Optionen " **neu**", " **ausgeliefert**", " **abgerechnet**" und " **geschlossen**" enthalten. Der Datentyp Two-Option bietet nur zwei Optionen.

Beide Datentypen zeigen ihre Bezeichnungen in einem Text Zeichenfolgen-Kontext an. Beispielsweise wird in einem Label-Steuerelement eine der Order-Status-Optionen angezeigt, wenn die **Text** -Eigenschaft des Steuer Elements auf eine Formel festgelegt ist, die auf diesen Options Satz verweist. Options Bezeichnungen können für App-Benutzer an unterschiedlichen Standorten lokalisiert werden.

Wenn ein App-Benutzer eine Option auswählt und diese Änderung speichert, überträgt die APP die Daten an die Datenbank, in der die Daten in einer von der Sprache unabhängigen Darstellung gespeichert werden. Eine Option in einem Options Satz wird als Zahl übertragen und gespeichert, und eine Option in einem Datentyp mit zwei Optionen wird als boolescher Wert übertragen und gespeichert.

Die Bezeichnungen dienen nur zu Anzeige Zwecken. Sie können keine direkten Vergleiche mit den Bezeichnungen durchführen, da Sie für eine Sprache spezifisch sind. Stattdessen hat jeder Options Satz eine Enumeration, die mit der zugrunde liegenden Zahl oder dem booleschen Wert arbeitet. Beispielsweise können Sie diese Formel nicht verwenden:

`If( ThisItem.OrderStatus = "Active"; ...`

Aber Sie können diese Formel verwenden:

`If( ThisItem.OrderStatus = OrderStatus.Active; ...`

Bei globalen Options Sätzen (bei denen die Entitäten gemeinsam genutzt werden) entspricht der Name der Options Satz-Enumeration dem Namen der globalen Options Menge. Für lokale Optionssätze (die auf eine Entität bezogen sind) kann der Name den Namen der Entität enthalten. Dieses Verhalten vermeidet Konflikte, wenn mehrere Entitäten über Optionssätze verfügen, die denselben Namen aufweisen. Beispielsweise kann für die Entität " **Accounts** " eine Option " **OrderStatus** " festgelegt werden, und der Name kann " **OrderStatus (Accounts)** " lauten. Dieser Name enthält ein oder mehrere Leerzeichen und Klammern, sodass Sie ihn in einfache Anführungszeichen einschließen müssen, wenn Sie ihn in einer Formel referenzieren.

Außerdem können sich zwei Optionswerte auch als boolesche Werte Verhalten. Beispielsweise kann für einen zwei-Options-Wert mit dem Namen " **taxstatus** " die Bezeichnung "Tax **" und "** **Non-** Tax" lauten, die " *true* " bzw. " *false* " Um dies zu veranschaulichen, können Sie die folgende Formel verwenden:

`If( ThisItem.Taxable = TaxStatus.Taxable; ...`

Sie können auch diese äquivalente Formel verwenden:

`If( ThisItem.Taxable; ...`