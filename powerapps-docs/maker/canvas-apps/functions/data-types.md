---
title: -Datentypen | Microsoft-Dokumentation
description: Datentypen in Canvas-apps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/19/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e96bf33b5ca5446c309eeb8a35ff0dd1c7fc5847
ms.sourcegitcommit: 6b75019dccc5296a313f9ff0eb397003f13ce737
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2019
ms.locfileid: "65941622"
---
# <a name="data-types-in-canvas-apps"></a>Datentypen in Canvas-apps

Informationen, Durchlaufen einer app in kleinen, diskrete Werte sehr ähnlich wie die Zellen einer Kalkulationstabelle aufweisen. Z. B. Daten in eine **Geburtstag** Feld und einem **Anniversary** Feld würden beide passieren als eine **Datum** -Wert, der das Jahr, Monat und den Tag enthält. Die app weiß, wie diese Werte zu formatieren, schränken Sie die Eingabe mit den jeweils geeigneten und weisen Werte mit einer Datenbank. Geburtstage unterscheiden sich von Geburtstage an Personen, aber das System behandelt diese auf genau die gleiche Weise. In diesem Fall **Datum** ist ein Beispiel für eine [Datentyp](https://en.wikipedia.org/wiki/Data_type).

Dieser Artikel enthält Details für die Datentypen, die canvas-Unterstützung für apps. Wenn eine app mit einer externen Datenquelle verbunden ist, wird jeder Datentyp in dieser Quelle in einen Datentyp für Canvas-apps zugeordnet.

| Datentyp | Beschreibung | Beispiele |
|-----------|-------------|---------|
| **Boolean** | Ein *"true"* oder *"false"* Wert.  Kann verwendet werden, direkt in **Wenn**, **Filter** und andere Funktionen ohne einen Vergleich.  | *TRUE* |
| **Hyperlink** | Eine Textzeichenfolge, die einen Link enthält. | **„http://powerapps.microsoft.com“** |
| **Währung** | Ein Währungswert, der in einer Gleitkommazahl gespeichert sind. Currency-Werte sind identisch mit der Number-Werte mit Currency-Formatierungsoptionen.  | **123**<br>**4.56** |
| **Bild** | Ein [Universal Resource Identifier (URI)](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier) Textzeichenfolge, die ein Bild im JPEG, PNG, SVG, GIF und andere allgemeine WebImage formatiert. | **MyImage** als app-Ressource hinzugefügt<br>**„https://northwindtraders.com/logo.jpg“**<br>**"appres://blobmanager/7b12ffa2..."** |
| **Farbe** | Eine Farbe-Spezifikation, einschließlich der alpha-Kanal. | **Color.Red**<br>**ColorValue( "#102030" )**<br>**RGBA( 255, 128, 0, 0.5 )** |
| **Datum** | Ein Datum ohne Zeit, in der Zeitzone des Benutzers von der app. | **Datum (2019, 5, 16)** |
| **DateTime** | Ein Datum mit Zeit, in der Zeitzone des Benutzers von der app. | **DateTimeValue( "May 16, 2019 1:23:09 PM" )** |
| **GUID** | Ein [Globally Unique Identifier](https://en.wikipedia.org/wiki/Universally_unique_identifier). | **GUID()**<br>**GUID( "123e4567-e89b-12d3-a456-426655440000" )** |
| **Medien** | Eine URI-Text-Zeichenfolge, ein video oder audio-Aufzeichnung. | **MyVideo** als app-Ressource hinzugefügt<br>**„https://northwindtraders.com/intro.mp4“**<br>**"appres://blobmanager/3ba411c..."** |
| **Anzahl** | Eine Gleitkommazahl. | **123**<br>**-4.567**<br>**8.903e121** |
| **Optionssatz** | Eine Auswahl aus einer Reihe von Optionen, die durch eine Reihe gesichert. Dieser Datentyp kombiniert eine Bezeichnung lokalisierbaren Text mit einem numerischen Wert an. Die Bezeichnung wird in der app angezeigt, und der numerische Wert gespeichert und für Vergleiche verwendet. | **ThisItem.OrderStatus** |
| **Record** | Ein Datensatz von Datenwerten. Dieser zusammengesetzten Datentyp enthält Instanzen anderer Datentypen, die in diesem Thema aufgeführt sind. Weitere Informationen finden Sie unter: [Arbeiten mit Tabellen](../working-with-tables.md). | **{Unternehmen: "Nordwind"<br>Mitarbeiter: 35, <br>gemeinnützige Organisationen: false}** |
| **Datensatz-Referenz** | Ein Verweis auf einen Datensatz in einer Entität. Solche Verweise werden häufig mit polymorphen Suchvorgänge verwendet. Weitere Informationen finden Sie unter: [Arbeiten mit Verweise](../working-with-references.md).| **First(Accounts).Owner** |
| **Tabelle** | Eine Tabelle mit Datensätzen.  Alle Datensätze müssen die gleichen Namen für die Felder mit den gleichen Datentypen und Weggelassene Felder werden als behandelt *leere*. Dieser zusammengesetzten Datentyp enthält Instanzen anderer Datentypen, die in diesem Thema aufgeführt sind. Weitere Informationen finden Sie unter: [Arbeiten mit Tabellen](../working-with-tables.md). | **Tabelle ({FirstName: "Sidney",<br>"LastName": "Higa"}, <br>{FirstName: "Nancy"<br>"LastName": "Anderson" } )**
| **Text** | Eine Unicode-Text-Zeichenfolge. | **"Hello, World"** |
| **Zeit** | Eine Uhrzeit ohne ein Datum in der Zeitzone des Benutzers von der app. | **Zeit ("11", "23", "45")** |
| **Zwei-option** | Eine Auswahl aus einem Satz von zwei Optionen, die durch einen booleschen Wert gesichert werden soll. Dieser Datentyp kombiniert eine Bezeichnung lokalisierbaren Text mit einem booleschen Wert. Die Bezeichnung wird in der app angezeigt, und der boolesche Wert gespeichert und für Vergleiche verwendet. | **ThisItem.Taxable** |

Viele dieser Datentypen sind vergleichbar und besitzen die gleiche zugrunde liegende Darstellung, wie z. B. eine **Hyperlink** Feld als behandelt **Text**.  Die zusätzliche Datentypen bieten bessere Standardeinstellung in Formularen und andere Steuerelemente auftritt.

## <a name="blank"></a>Blank

Alle Datentypen haben einen Wert von *leere* (das heißt, kein Wert). Der Begriff "Null" wird häufig in Datenbanken für dieses Konzept verwendet.  

Verwenden der **leere** -Funktion mit der **festgelegt** oder **Patch** Funktion, um eine Variable festlegen oder das Feld *leere*. Z. B. **Set (X, Blank())** Werte in der globalen Variablen entfernt **x**.  

Test für eine *leere* Wert mithilfe der [ **"isblank"** ](function-isblank-isempty.md) Funktion. Ersetzen Sie dies möglich *leer* Werte mit nicht -*leer* Werte mithilfe der [ **Coalesce** ](function-isblank-isempty.md) Funktion.

Da alle Datentypen unterstützt *leere*, **booleschen** und **zwei Option** Datentypen effektiv haben drei mögliche Werte.

## <a name="text-hyperlink-image-and-media"></a>Text, links, Images und Medien

Alle vier dieser Datentypen basieren auf einer [Unicode](https://en.wikipedia.org/wiki/Unicode) Textzeichenfolge.

### <a name="size-limits"></a>Größenbeschränkungen

Diese Datentypen werden nicht beschränkt auf ihre Länge aufweisen. Die zugrunde liegende JavaScript-Implementierung in Ihrem Browser oder auf Ihrem Gerät kann maximal verursachen, aber es ist in der Regel deutlich mehr als 100 MB. Allerdings kann die Menge des verfügbaren Arbeitsspeichers auf dem Gerät durch einen anderen Grenzwert verursachen, die wahrscheinlich niedriger ist als 100 MB. Um zu bestimmen, ob Ihre app innerhalb dieser Grenzwerte ausgeführt wird, testen Sie allgemeine Szenarien auf allen Geräten, die auf denen sie ausgeführt werden soll.

### <a name="image-and-media-resources"></a>Image und Medienressourcen

Durch die **Datei** Menü, Video- und Audiodateien Bilddateien können app-Ressourcen hinzugefügt. Der Name der importierten Datei wird der Ressourcenname in der app. In dieser Abbildung, die das Logo für Northwind Traders, mit dem Namen **Nwindlogo**, eine app hinzugefügt wurde:

![](media/data-types/nwind-resource.png)

Um diese Ressource in einer app zu verwenden, geben sie in der **Image** Eigenschaft eine [ **Image** ](../controls/control-image.md) Steuerelement:

![](media/data-types/nwind-image.png)

### <a name="uris-for-images-and-other-media"></a>URIs für Bilder und andere Medien

Sie können tiefer ein wenig in diesem letzten Beispiel durch Festlegen der **Text** Eigenschaft eine [ **Bezeichnung** ](../controls/control-text-box.md) die Steuerung an **Nwindlogo**. Die Bezeichnung zeigt eine Textzeichenfolge an:

![](media/data-types/nwind-text.png)

Canvas-apps verweisen auf die jedes Image oder eine andere Mediadatei, in der Cloud oder als app-Ressource hinzugefügt werden, indem eine URI-Text-Zeichenfolge.

Z. B. die **Image** Eigenschaft eines Bildsteuerelements akzeptiert nicht nur app-Ressourcen, sondern auch Links zu Bildern im Web, wie z. B. "https://northwindtraders.com/logo.jpg". Die Eigenschaft akzeptiert auch Inlinebilder, mit denen die [Daten-URI-Schema](https://en.wikipedia.org/wiki/Data_URI_scheme), wie in diesem Beispiel:

```powerapps-dot
"data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAkAAAAFAQMAAACtnVQoAAAABlBMVEUAAAB0J3UMNU6VAAAAAXRSTlMAQObYZgAAABRJREFUCNdjUGJgCGVg6GgAkkA2AA8/AffqCEBsAAAAAElFTkSuQmCC"
```

Dieser URI wird eine erweiterten Version zwei Lila Diamanten angezeigt:

![](media/data-types/double-diamonds.png)

Können Sie anzeigen, das neueste Image erfasst werden, eine [ **Kamera** ](../controls/control-camera.md) steuern, wenn Sie festlegen, die **Image** Eigenschaft eines Bildsteuerelements zu der **Foto** die Eigenschaft von der Kamera-Steuerelement. Die app enthält das Bild im Arbeitsspeicher, und die **Foto** Eigenschaft von der Kamera-Steuerelement gibt einen URI-Verweis auf das Bild zurück. Sie können z. B. dauern, ein Bild und der Kamera **Foto** Eigenschaft zurückgeben könnte **"appres://blobmanager/7b12ffa2ea4547e5b3812cb1c7b0a2a0/1"**.

Sie verwenden einen URI zum Verweisen auf ein Bild oder eine andere Media-Datei, die in einer Datenbank gespeichert. Auf diese Weise die app nicht die eigentlichen Daten abzurufen, bis sie tatsächlich benötigt wird. Beispielsweise kann ein Anhang in einer Common Data Service-Entität zurückgeben **"Appres://datasources/Contacts/table/..."** Sie können dieses Image durch Festlegen von anzeigen, wie im Beispiel Kamera der **Image** Eigenschaft eines Bildsteuerelements auf diesen Verweis, der die binären Daten abgerufen.

Wenn Sie einen Media-Datentyp, z. B. ein Bild, mit einer Datenbank speichern, sendet die app an das tatsächliche Bild oder die Media-Daten, nicht den URI-Verweis.

## <a name="number-and-currency"></a>Zahl und Währung

**Anzahl** und **Währung** -Datentypen verwenden die [IEEE 754-Gleitkommazahl mit doppelter Genauigkeit mit der Norm](https://en.wikipedia.org/wiki/IEEE_754). Dieser Standard bietet einen sehr großen Bereich von Zahlen, in dem Sie arbeiten, von –1.79769 x 10<sup>308</sup> 1.79769 x 10<sup>308</sup>. Der kleinste Wert, der dargestellt werden kann, ist 5 x 10<sup>–324</sup>.

Canvas-apps können nicht genau darstellen ganze Zahlen (oder ganze Zahlen) zwischen –9,007,199,254,740,991 (– (2<sup>53</sup> – 1)) und 9,007,199,254,740,991 (2<sup>53</sup> – 1) (inklusiv) enthalten. Dieser Bereich ist größer als die 32-Bit-(oder 4-Byte-) ein Integer-Datentypen, die Datenbanken häufig verwenden. Allerdings können nicht Canvas-apps auf 64-Bit-(oder 8-Byte) ein Integer-Datentypen darstellen. Sie möchten die Zahl in einem Textfeld speichern oder verwenden eine berechnete Spalte, um eine Kopie der Zahl in einem Textfeld zu erstellen, damit er in zugeordnet ist eine **Text** -Datentyp in der Canvas-app. Auf diese Weise können Sie halten, anzuzeigen, und geben Sie diese Werte als auch verglichen, um zu ermitteln, ob sie gleich sind; Sie allerdings können keine numerische Berechnungen werden in dieser Form ausführen.

Gleitkommaarithmetik sind Näherungswerte. damit unerwartete Ergebnisse mit der viele dokumentierten Beispiele manchmal zuweisen können. Sie erwarten wahrscheinlich die Formel **55 / 100 * 100** genau 55 zurückgegeben und **(55 / 100 * 100): 55** genau 0 (null) zurückgegeben. Die zweite Formel dagegen die 7.1054 x 10<sup>– 15</sup>, dies ist sehr klein, aber nicht gleich NULL ist. Diesen kleinen Unterschied nicht normalerweise dazu führen, dass ein Problem, und die app wird es sofort, wenn das Ergebnis angezeigt. Jedoch können geringfügige Unterschiede, die Verbundauthentifizierung in nachfolgenden Berechnungen und angezeigt werden, um die falsche Antwort zu geben.

Datenbanksysteme häufig Währungen gespeichert und Berechnungen mithilfe von decimal Mathematik, die einen kleineren Bereich jedoch mehr Kontrolle über die Genauigkeit bietet. In der Standardeinstellung canvas-apps-Zuordnung Währungen in Gleitkommazahlen-Punktwerte; aus diesem Grund kann das Ergebnis von Berechnungen unterscheiden, die in einem systemeigenen decimal-Datentyp durchgeführt werden. Wenn diese Art von Diskrepanzen Probleme verursachen, sollten Sie für die Arbeit mit diesen Werten als **Text**genau, wie Sie mit großen ganzen Zahlen, die weiter oben in diesem Abschnitt beschrieben.

## <a name="date-time-and-datetime"></a>Date, Time und DateTime

### <a name="time-zones"></a>Zeitzonen

Datum/Uhrzeit-Werte fallen in den folgenden Kategorien:

- **Benutzer lokale**: Diese Werte werden gespeichert, [UTC (Coordinated Universal Time)](https://en.wikipedia.org/wiki/Coordinated_Universal_Time), aber die Zeitzone des Benutzers, der die app wirkt sich auf die app diese Werte veranschaulicht, wie und wie diese von der app-Benutzer angibt. Beispielsweise wird angezeigt, der gleiche Zeitpunkt anders zu einem Benutzer in Kanada als mit einem Benutzer in Japan.
- **Unabhängig von Zeitzone**: Die app zeigt die Werte die gleiche Weise aus, und der app-Benutzer gibt sie die gleiche Weise, unabhängig von Zeitzone. Der gleiche Zeitpunkt wird die gleiche Weise zu einem Benutzer in Kanada angezeigt, wie mit einem Benutzer in Japan. App-Autoren, die ihre apps zur Ausführung in verschiedenen Zeitzonen erwarten, dass keine verwenden diese Werte auf, weil sie insgesamt einfacher sind.

Diese Tabelle zeigt einige Beispiele:

| Datum/Uhrzeit-Typ | In der Datenbank gespeicherten Wert | Wert angezeigt, und 7 Stunden westlicher Richtung gemessen wird UTC eingegeben | Wert angezeigt, und 4 Stunden östlich UTC eingegeben | 
|--------------------------|------------------------------|------------------------------|
| **Lokaler Benutzer** | Sonntag,&nbsp;möglicherweise&nbsp;19&nbsp;2019<br>4:00 UHR | Samstag,&nbsp;möglicherweise&nbsp;18,&nbsp;2019<br>21:00 UHR | Sonntag,&nbsp;möglicherweise&nbsp;19&nbsp;2019<br>8:00 UHR |
| **Unabhängig von Zeitzone** | Sonntag,&nbsp;möglicherweise&nbsp;19&nbsp;2019<br>4:00 UHR | Sonntag,&nbsp;möglicherweise&nbsp;19&nbsp;2019<br>4:00 UHR | Sonntag,&nbsp;möglicherweise&nbsp;19&nbsp;2019<br>4:00 UHR | 

Für **Benutzer lokale** Datumsangaben und Uhrzeiten, Canvas-apps die Zeitzone des Browsers oder des Geräts verwenden, sondern modellgesteuerte apps des Benutzers festlegen in Common Data Service. Diese Einstellungen in der Regel übereinstimmen, aber die Ergebnisse variieren, wenn diese Einstellungen unterschiedlich sein.

### <a name="numeric-equivalents"></a>Numerischen Entsprechungen

Canvas-apps enthalten, und berechnen Sie alle Datum/Uhrzeit-Werte, gibt an, ob **Benutzer lokale** oder **unabhängig von Zeitzone** in UTC angegeben. Die app übersetzt, die Werte entsprechend der Zeitzone der app-Benutzer, wenn sie angezeigt, und bei der Angabe durch den app-Benutzer.

Wenn eine Canvas-app liest eine **unabhängig von Zeitzone** Wert aus einer Datenquelle oder Schreibvorgänge, die solche Werte mit einer Datenquelle, die app automatisch angepasst den Wert wird, der für die Zeitzone des Benutzers von der app zu kompensieren. Die app wird den Wert als UTC-Wert, und alle anderen Datum/Uhrzeit-Werte in der app konsistent behandelt. Aufgrund dieser Kompensierung der ursprünglichen **unabhängig von Zeitzone** Wert angezeigt wird, wenn die app den UTC-Wert für die Zeitzone des Benutzers, der die app passt.

Sie können dieses Verhalten besser verfolgen, mit der [ **Wert** ](function-value.md) Funktion Zugriff auf den zugrunde liegenden numerischen Wert für Datum/Uhrzeit-Wert. Diese Funktion gibt den Datum/Uhrzeit-Wert als die Anzahl der Millisekunden seit dem 1. Januar 1970 00:00:00.000 UTC.

Da alle Datums-/Uhrzeitwert in UTC, zu der Formel gespeichert wird **Wert (Datum (1970, 1, 1))** NULL in den meisten Teilen der Welt nicht zurückgegeben werden, da die **Datum** Funktion gibt ein Datum in UTC zurück. Beispielsweise würde die Formel zurück 28,800,000 in einer anderen Zeitzone, die Offsets von UTC von acht Stunden. Diese Zahl gibt die Anzahl der Millisekunden in acht Stunden.

Zurück zu unserem Beispiel von oben:

| Datum/Uhrzeit-Typ | In der Datenbank gespeicherten Wert | Wert angezeigt, und 7 Stunden westlicher Richtung gemessen wird UTC eingegeben | **Wert** -Funktion zurückgegeben wird |
|--------------------------|------------------------------|------------------------------|
| **Lokaler Benutzer** | Sonntag,&nbsp;möglicherweise&nbsp;19&nbsp;2019<br>4:00 UHR | Samstag,&nbsp;möglicherweise&nbsp;18,&nbsp;2019<br>21:00 UHR | 1,558,238,400,000<br> (Sonntag,&nbsp;möglicherweise&nbsp;19&nbsp;2019<br>4:00 UHR UTC) |
| **Unabhängig von Zeitzone** | Sonntag,&nbsp;möglicherweise&nbsp;19&nbsp;2019<br>4:00 UHR | Sonntag,&nbsp;möglicherweise&nbsp;19&nbsp;2019<br>4:00 UHR |1,558,263,600,000<br> (Sonntag,&nbsp;möglicherweise&nbsp;19&nbsp;2019<br>11:00 UHR UTC) |

### <a name="converting-unix-times"></a>Konvertieren von Uhrzeiten von Unix

UNIX-Zeiten geben die Anzahl der Sekunden seit dem 1. Januar 1970 um 00:00:00 UTC. Da das Canvas-apps Millisekunden statt Sekunden verwenden möchten, können Sie zwischen den beiden durch Multiplikation oder Division durch 1000 konvertieren.

Unix-Zeit zeigt z. B. 9. September 2001, 01:46:40 UTC, als 1.000.000.000. Zum Anzeigen, die Datum/Uhrzeit-Wert in einer Canvas-app, Multiplizieren Sie diese Zahl mit 1000 in Millisekunden zu konvertieren und dann verwenden, in einem [ **Text** ](function-text.md) Funktion. Die Formel **Text (1000000000 * 1000, DateTimeFormat.UTC)** gibt die Zeichenfolge **2001-09-09T01:46:40.000Z**.

Diese Funktion jedoch zurückgibt **Samstag, 8. September 2001 18:46:40** bei Verwendung der **DateTimeFormat.LongDateTime24** Format in einer anderen Zeitzone, der-7 Stunden von der koordinierten Weltzeit (7 Stunden westlicher Richtung gemessen wird UTC) versetzt ist. Dieses Ergebnis zeigt die **"DateTime"** Wert anhand der lokalen Zeitzone richtig.

### <a name="sql-server"></a>SQL Server

SQL Server verfügt über [ **"DateTime"**, **Datetime2**, und andere Datum/Uhrzeit-Datentypen](https://docs.microsoft.com/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql?view=sql-server-2017) , die nicht mit einen Zeitzonenoffset einschließen und nicht der Zeitzone angeben wie. Canvas-apps wird vorausgesetzt, diese Werte werden in UTC gespeichert und behandelt sie als **Benutzer lokale**. Wenn die Werte Zeitzone unabhängig sein sollen, für die UTC-Übersetzungen korrigieren, mithilfe der [ **"timeZoneOffset"** ](function-dateadd-datediff.md#converting-to-utc) Funktion.

Canvas-apps verwenden Sie die enthaltene Zeitzonen-Informationen in **Datetimeoffset** Felder beim Konvertieren eines Werts mit Ihrer Darstellung in der app interne UTC. Verwenden Sie die apps immer UTC Zeitzone (null Offset der Zeitzone) Wenn sie Daten schreiben.

Canvas-apps lesen und Schreiben von Werten der der [ **Zeit** ](https://docs.microsoft.com/en-us/sql/t-sql/data-types/time-transact-sql) -Datentyp in der SQL Server als Textzeichenfolgen in die [Zeitformat ISO 8601](https://en.wikipedia.org/wiki/ISO_8601#Durations). Beispielsweise müssen Sie dieses Zeichenfolgenformat zu analysieren und verwenden Sie die [ **Zeit** ](function-date-time.md) Funktion, die Textzeichenfolge zu konvertieren **"PT2H1M39S"** auf eine **Zeit** Wert:

```powerapps-dot
First(
    ForAll(
        MatchAll( "PT2H1M39S", "PT(?:(?<hours>\d+)H)?(?:(?<minutes>\d+)M)?(?:(?<seconds>\d+)S)?" ),
        Time( Value( hours ), Value( minutes ), Value( seconds ) )
    )
).Value
```

### <a name="mixing-date-and-time-information"></a>Das Kombinieren von Datums-und Uhrzeitinformationen

**Datum**, **Zeit**, und **"DateTime"** unterschiedliche Namen besitzen, aber sie enthalten die gleiche Informationen zu Datums- und Uhrzeitangaben. 

Ein **Datum** Wert kann enthalten Informationen, die in der Regel ist Mitternacht. Ein **Zeit** Wert kann Datumsinformationen, in der Regel ausführen am 1. Januar 1970. Common Data Service speichert auch Informationen mit einer **nur Date** Feld wird jedoch nur die Datumsinformationen in der Standardeinstellung. Auf ähnliche Weise zu Canvas-apps manchmal zwischen dieser Datentypen, die Standardformate zu ermitteln und Steuerelementen unterscheiden.

Addieren und Subtrahieren von Datums-und Uhrzeitwerte direkt wird nicht empfohlen, da die Zeitzone und andere Konvertierungen verwirrende Ergebnissen führen können. Verwenden Sie entweder die **Wert** -Funktion zum Konvertieren von Datums-/Uhrzeitwerten in Millisekunden zuerst und der app-Benutzer-Zeitzone berücksichtigt, oder Verwenden der [ **DateAdd** ](function-dateadd-datediff.md) und [ **DateDiff** ](function-dateadd-datediff.md) Funktionen hinzufügen oder Entfernen von einem der folgenden Werte.

## <a name="option-sets-and-two-options"></a>Optionssätze und zwei Optionen

Optionssätze und Datentypen der beiden-Option stellen eine zwei oder mehr Optionen für app-Benutzer auswählen. Z. B. eine **Bestellstatus** Optionssatz kann die Auswahlmöglichkeiten **neu**, **Shipped**, **fakturiert**, und **geschlossen** . Der Datentyp der beiden-Option bietet nur zwei Auswahlmöglichkeiten gibt.

Beide dieser Datentypen zeigen ihre Bezeichnungen in einer Text-Zeichenfolge. "Zeigt", wenn Sie ein Label-Steuerelement eine der Bestellstatus Optionen, z. B. wenn des Steuerelements **Text** -Eigenschaftensatz auf eine Formel, die auf diese Option festgelegt. Option Bezeichnungen können für app-Benutzer an verschiedenen Speicherorten lokalisiert werden.

Wenn app-Benutzer eine Option auswählt, und die Änderung speichert, überträgt die app die Daten in der Datenbank, die diese Daten in einer Darstellung, die unabhängig von Sprache ist, speichert. Eine Option in einen Optionssatz übertragen und als Zahl gespeichert, und eine Option in einem zwei-Option Datentyp übertragen und gespeichert, die als boolescher Wert.

Die Bezeichnungen werden nur zu Anzeigezwecken. Direkte Vergleiche mit den Bezeichnungen können nicht ausgeführt werden, da sie für eine Sprache spezifisch sind. Stattdessen enthält jede Optionssatz eine Enumeration, die mit der zugrunde liegende Anzahl oder ein boolescher Wert. Beispielsweise können Sie keine diese Formel:

`If( ThisItem.OrderStatus = "Active", ...`

Sie können jedoch diese Formel:

`If( ThisItem.OrderStatus = OrderStatus.Active, ...`

Für globale Optionssätze (freigeben, welche Entitäten), den Namen der Optionssatz Enumeration entspricht der Name des Satzes globale Option. Für lokale Optionssätze (die eine Entität zugeordnet sind), der Name kann den Namen der Entität enthalten. Dadurch werden Konflikte vermieden, wenn mehrere Entitäten Optionssätze verfügen, die den gleichen Namen haben. Z. B. die **Konten** Entität eine **"orderstatus"** -Option festgelegt werden soll, und der Name möglicherweise **"orderstatus" (Konten)**. Dieser Name enthält ein oder mehrere Leerzeichen und Klammern, damit Sie ihn in einfache Anführungszeichen umgeben müssen, wenn Sie in einer Formel darauf verweisen.

Darüber hinaus können Werte von zwei-Option auch als boolesche Werte sich Verhalten. Z. B. einen zwei-Option-Wert, der mit dem Namen **TaxStatus** möglicherweise die Bezeichnungen **steuerbaren** und **Non-steuerbare**, entsprechen die *"true"* und *"false"* bzw. Um zu veranschaulichen, können Sie diese Formel:

`If( ThisItem.Taxable = TaxStatus.Taxable, ...`

Sie können auch die folgenden gleichwertigen Formel verwenden:

`If( ThisItem.Taxable, ...`