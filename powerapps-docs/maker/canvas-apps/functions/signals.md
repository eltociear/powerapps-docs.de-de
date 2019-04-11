---
title: Die Signale „Acceleration“, „App“, „Compass“, „Connection“ und „Location“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Signale „Acceleration“, „App“, „Compass“, „Connection“ und „Location“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d13f4a0669ae9f0d7ef9a5f4ef7115e006256bd9
ms.sourcegitcommit: d1d39d6b72516d62514af4ff90f04c35fbdd8638
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59480237"
---
# <a name="acceleration-app-compass-connection-and-location-signals-in-powerapps"></a>Die Signale „Acceleration“, „App“, „Compass“, „Connection“ und „Location“
Gibt Informationen zur App-Umgebung zurück, z.B. den Standort des Benutzers und welcher Bildschirm angezeigt wird  

## <a name="description-and-syntax"></a>Beschreibung und Syntax
Alle Signale geben einen [Datensatz](../working-with-tables.md#records) von Informationen zurück. Sie können diese Informationen als Datensatz verwenden und speichern oder einzelne Eigenschaften mithilfe des **.**- [Operators](operators.md) extrahieren.

> [!NOTE]
> Die **Acceleration** und **Compass** Funktionen geben genaue Werte in einen nativen Spieler wie z. B. unter iOS oder Android zurück, aber diese Funktionen geben einen Nullwert zurück beim Erstellen oder eine app im Browser zu ändern.

### <a name="acceleration"></a>Acceleration
Das Signal **Acceleration** gibt die Beschleunigung des Geräts dreidimensional im Verhältnis zum Bildschirm des Geräts zurück. Die Beschleunigung wird in *g*-Einheiten von 9.81 m/Sekunde<sup>2</sup> oder 32.2 ft/Sekunde<sup>2</sup> gemessen (die Erdbeschleunigung wird aufgrund der Schwerkraft an Objekte auf der Erdoberfläche übertragen).

| Eigenschaft | Beschreibung |
| --- | --- |
| **Acceleration.X** |Rechts und links.  Rechts ist eine positive Zahl. |
| **Acceleration.Y** |Vorwärts und zurück.  Vorwärts ist eine positive Zahl. |
| **Acceleration.Z** |Hoch und herunter.  Hoch ist eine positive Zahl. |

### <a name="app"></a>App
Das Signal **App** gibt Informationen über die ausgeführte App zurück.

| Eigenschaft | Beschreibung |
| --- | --- |
| **App.ActiveScreen** | Der angezeigte Bildschirm. Gibt ein Bildschirmobjekt zurück, das Sie zum Verweisen auf Bildschirmeigenschaften oder Vergleichen mit einem anderen Bildschirm verwenden können, um zu bestimmen, welcher Bildschirm angezeigt wird. Verwenden Sie zum Ändern des angezeigten Bildschirms der **[wieder](function-navigate.md)** oder **[Navigate](function-navigate.md)** Funktion. |
| **App.Width** | Gibt die Breite des Fensters, in dem die app ausgeführt wird. Sie können diese Eigenschaft in einer Formel verwenden, beim Festlegen der **Breite** Eigenschaft des Bildschirms, um einen reaktionsfähigen app zu erstellen.  |
| **App.Height** | Gibt die Höhe des Fensters, in dem die app ausgeführt wird. Sie können diese Eigenschaft in einer Formel verwenden, beim Festlegen der **Höhe** Eigenschaft des Bildschirms, um einen reaktionsfähigen app zu erstellen. |
| **App.DesignWidth** | Gibt die Breite der app in PowerApps Studio zurück. Sie können diese Eigenschaft in einer Formel verwenden, beim Festlegen der **Breite** Eigenschaft des Bildschirms, um eine minimale Breite in einer reaktionsfähigen app sicherzustellen.  |
| **App.DesignHeight** | Gibt die Höhe der app in PowerApps Studio zurück. Sie können diese Eigenschaft in einer Formel verwenden, beim Festlegen der **Höhe** Eigenschaft des Bildschirms, um eine minimale Höhe in einem reaktionsfähigen app sicherzustellen.  |

Die **App** -Objekt verfügt außerdem über eine [verhaltensformel](../working-with-formulas-in-depth.md) , die Sie festlegen können.

| Eigenschaft  | Beschreibung |
| --- | --- |
| **OnStart** | Das Verhalten einer app, wenn der Benutzer gestartet wird. Diese Eigenschaft wird am häufigsten zum Abrufen und Zwischenspeichern von Daten in Sammlungen mit der **[sammeln](function-clear-collect-clearcollect.md)** Funktion richten Sie Variablen mit der **[festgelegt](function-set.md)** funktionieren, und navigieren Sie zu einer ersten Bildschirm mit der **[Navigate](function-navigate.md)** Funktion. Diese Formel wird ausgewertet, bevor der erste Bildschirm angezeigt wird. Kein Bildschirm geladen wird, damit Sie Kontextvariablen mit festlegen, können die **["updatecontext"](function-updatecontext.md)** Funktion. Sie können aber auch Kontextvariablen mit übergeben die **Navigate** Funktion. |

Die **App** Objekt am Anfang der hierarchischen Liste der Steuerelemente im linken Navigationsbereich angezeigt wird, und Sie können dieses Objekt wie ein Steuerelement auf einem Bildschirm auswählen. Nachdem Sie das Objekt ausgewählt haben, können Sie anzeigen und bearbeiten eine seiner Eigenschaften, wenn Sie diese Eigenschaft in der Dropdown-Liste auf der linken Seite der Bearbeitungsleiste auswählen.  

Nach dem Ändern der **OnStart** -Eigenschaft, können Sie testen, indem Sie mit dem Mauszeiger auf die **App** Objekt in den Links im Navigationsbereich, Sie auf die Auslassungspunkte (...), der angezeigt wird, und wählen dann **ausführen OnStart**. Im Gegensatz zu, wenn die app zum ersten Mal geladen wird werden vorhandene Auflistungen und Variablen bereits festgelegt. Verwenden der **[ClearCollect](function-clear-collect-clearcollect.md)** -Funktion anstelle von der **sammeln** Funktion für den Einstieg leere Sammlungen.

 ![App-Kontextmenü mit OnStart ausführen](media/appobject-runonstart.png)

### <a name="compass"></a>Compass
Das Signal **Compass** gibt die Kompassausrichtung des oberen Bildschirmrands zurück. Die Ausrichtung basiert auf dem elektromagnetischen Norden.

| Eigenschaft | Beschreibung |
| --- | --- |
| **Compass.Heading** |Ausrichtung in Grad.  Gibt eine Zahl von 0 bis 360 zurück, 0 ist Norden. |

### <a name="connection"></a>Verbindung
Das Signal **Connection** gibt die Informationen über die Netzwerkverbindung zurück. Bei einer getakteten Verbindung empfiehlt es sich, die über das Netzwerk gesendeten oder empfangenen Daten zu beschränken.

| Eigenschaft | Beschreibung |
| --- | --- |
| **Connection.Connected** |Gibt einen booleschen Wert **TRUE** oder **FALSE** zurück, der angibt, ob das Gerät mit einem Netzwerk verbunden ist |
| **Connection.Metered** |Gibt einen booleschen Wert **TRUE** oder **FALSE** zurück, der angibt, ob die Verbindung getaktet ist |

### <a name="location"></a>Ort
Das Signal **Location** gibt den Standort des Geräts anhand des Globalen Positionsbestimmungssystems (GPS) und anderer Geräteinformationen zurück, z.B. der Kommunikation von Funktürmen und der IP-Adresse.

Wenn ein Benutzer zum ersten Mal auf die Positionsinformationen zugreift, kann das Gerät diesen Benutzer dazu auffordern, Zugriff auf diese Informationen zu erteilen.

Wenn sich der Standort ändert, werden Abhängigkeiten vom Standort kontinuierlich neu berechnet, was die Batterieleistung beeinträchtigt. Um Akkulaufzeit zu erhöhen, können Sie die Standortupdates mithilfe der Funktionen **[Enable](function-enable-disable.md)** und **[Disable](function-enable-disable.md)** an- und ausschalten. Das Signal „Location“ wird automatisch deaktiviert, wenn der angezeigte Bildschirm nicht von Standortinformationen abhängig ist.

| Eigenschaft | Beschreibung |
| --- | --- |
| **Location.Altitude** |Gibt eine Zahl zurück, die die Höhe über dem Meeresspiegel in Metern angibt |
| **Location.Latitude** |Gibt eine Zahl zwischen -90 und 90 zurück, die den Breitengrad vom Äquator aus in Grad angibt. Eine positive Zahl gibt einen Standort nördlich vom Äquator an. |
| **Location.Longitude** |Gibt eine Zahl zwischen 0 und 180 zurück, die den Längengrad westwärts von Greenwich, England in Grad angibt. |

## <a name="examples"></a>Beispiele
In einem Feld Baseball löst ein Pitcher aus des pitchers ein Smartphone, einem Catcher auf der Home Plate an. Das Telefon fliegt flach über dem Boden, der obere Bildschirmrand zeigt auf den Catcher, und der Pitcher fügt kein Drehmoment hinzu. In diesem Moment hat das Telefon getakteten Mobilfunknetzdienst, jedoch kein WLAN. Die **PlayBall**-Bildschirm wird angezeigt.   

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Location.Latitude** |Gibt den Breitengrad der aktuellen Position zurück. Das Feld befindet sich an den Koordinaten 47.591 N, 122.333 w. |47.591<br><br>Der Breitengrad wird fortlaufend geändert, während sich der Ball vom Pitcher zum Catcher bewegt. |
| **Location.Longitude** |Gibt den Längengrad der aktuellen Position zurück |122.333<br><br>Der Längengrad wird fortlaufend geändert, während sich der Ball vom Pitcher zum Catcher bewegt. |
| **Location** |Gibt den Längen- und Breitengrad des aktuellen Standorts in einem Datensatz zurück |{&nbsp;Breitengrad:&nbsp;47.591, Längengrad:&nbsp;122.333&nbsp;} |
| **Compass.Heading** |Gibt die Kompassausrichtung des oberen Bildschirmrands zurück Dieses Feld liegt die Home Platte aus des pitchers ungefähr Südwesten. |230.25 |
| **Acceleration.X** |Gibt die Beschleunigung des Geräts von linkem zu rechtem Rand an. Der Pitcher wirft das Gerät in Bezug auf den oberen Bildschirmrand geradeaus, sodass das Gerät nicht von Seite zu Seite beschleunigt. |0 |
| **Acceleration.Y** |Gibt die Beschleunigung des Geräts zwischen Vorder- und Rückseite an. Der Pitcher beschleunigt das Gerät anfänglich durch den Wurf erheblich, von 0 auf 90 Meilen pro Stunde (132 Fuß pro Sekunde) innerhalb einer halben Sekunde. Einmal in der Luft beschleunigt das Telefon, wenn die Luftreibung außen vor gelassen wird, nicht weiter. Das Gerät wird verlangsamt, wenn der Catcher es fängt, und wird angehalten. |8.2, während der Pitcher das Geräts wirft<br><br>0, während sich das Gerät in der Luft befindet<br><br>-8.2, während der Catcher das Gerät fängt |
| **Acceleration.Z** |Gibt die Beschleunigung des Geräts vom oberen zum unteren Rand an. Das Telefon unterliegt in der Luft den Auswirkungen der Schwerkraft. |0, bevor der Pitcher das Geräts wirft<br><br>1, während sich das Gerät in der Luft befindet<br><br>0, nachdem der Catcher das Gerät gefangen hat |
| **Acceleration** |Gibt die Beschleunigung als Datensatz zurück |{ X: 0, Y: 264, Z: {0} als der Pitcher das Gerät löst. |
| **Connection.Connected** |Gibt einen booleschen Wert zurück, der angibt, ob das Gerät mit einem Netzwerk verbunden ist |**"True"** |
| **Connection.Metered** |Gibt einen booleschen Wert zurück, der angibt, ob die Verbindung getaktet ist |**"True"** |
| **App.ActiveScreen = PlayBall** |Gibt einen booleschen Wert zurück, der angibt, ob **PlayBall** angezeigt wird. |**"True"** |
| **App.ActiveScreen.Fill** |Gibt die Hintergrundfarbe des angezeigten Bildschirms zurück |**Color.Green** |

