---
title: Die Signale „Acceleration“, „App“, „Compass“, „Connection“ und „Location“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Sensoren "Beschleunigung", "App", "Compass", "Connection" und "Location" in Power apps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/29/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9cd0470d6911452b38040531ec17060b3bc69fa0
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74729582"
---
# <a name="acceleration-app-compass-connection-and-location-signals-in-power-apps"></a>Signale für Beschleunigung, APP, Kompass, Verbindung und Standort in Power apps

Gibt Informationen zur App-Umgebung zurück, z.B. den Standort des Benutzers und welcher Bildschirm angezeigt wird

## <a name="description-and-syntax"></a>Beschreibung und Syntax

Signale sind Werte, die jederzeit geändert werden können, unabhängig davon, wie der Benutzer mit der APP interagieren kann. Formeln, die auf Signalen basieren, werden automatisch neu berechnet, wenn sich diese Werte ändern.

Signale geben in der Regel einen [Datensatz](../working-with-tables.md#records) von Informationen zurück. Sie können diese Informationen als Datensatz verwenden und speichern oder einzelne Eigenschaften mithilfe des **.** - [Operators](operators.md) extrahieren.

> [!NOTE]
> Die Funktionen **Acceleration** und **Compass** geben genaue Werte in einem systemeigenen Player wie z. b. unter IOS oder Android zurück, aber diese Funktionen geben beim Erstellen oder Ändern einer APP im Browser NULL-Werte zurück.

### <a name="acceleration"></a>Acceleration

Das Signal **Acceleration** gibt die Beschleunigung des Geräts dreidimensional im Verhältnis zum Bildschirm des Geräts zurück. Die Beschleunigung wird in *g*-Einheiten von 9.81 m/Sekunde<sup>2</sup> oder 32.2 ft/Sekunde<sup>2</sup> gemessen (die Erdbeschleunigung wird aufgrund der Schwerkraft an Objekte auf der Erdoberfläche übertragen).

| Eigenschaft | Beschreibung |
| --- | --- |
| **Acceleration.X** |Rechts und links.  Rechts ist eine positive Zahl. |
| **Acceleration.Y** |Vorwärts und zurück.  Vorwärts ist eine positive Zahl. |
| **Acceleration.Z** |Hoch und herunter.  Hoch ist eine positive Zahl. |

### <a name="app"></a>App

Neben anderen Eigenschaften enthält das **App** -Objekt ein Signal, das angibt, welcher Bildschirm angezeigt wird.

| Eigenschaft | Beschreibung |
| --- | --- |
| **App.ActiveScreen** |Bildschirm, der angezeigt wird. Gibt ein Bildschirm Objekt zurück, mit dem Sie auf Eigenschaften des Bildschirms verweisen oder mit einem anderen Bildschirm vergleichen können, um zu bestimmen, welcher Bildschirm angezeigt wird. Mit der **[Back](function-navigate.md)** -oder **[Navigate](function-navigate.md)** -Funktion können Sie den Bildschirm ändern, der angezeigt wird. |

Weitere Informationen finden Sie unter Dokumentation zu [ **App** -Objekten](object-app.md) .

### <a name="compass"></a>Compass
Das Signal **Compass** gibt die Kompassausrichtung des oberen Bildschirmrands zurück. Die Ausrichtung basiert auf dem elektromagnetischen Norden.

| Eigenschaft | Beschreibung |
| --- | --- |
| **Compass.Heading** |Ausrichtung in Grad.  Gibt eine Zahl von 0 bis 360 zurück, 0 ist Norden. |

### <a name="connection"></a>Connection
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
In einem Baseball-Feld löst ein Pitcher ein Telefon aus dem Muter des Pitcher an einen Fänger an der Hausplatte aus. Das Telefon fliegt flach über dem Boden, der obere Bildschirmrand zeigt auf den Catcher, und der Pitcher fügt kein Drehmoment hinzu. In diesem Moment hat das Telefon getakteten Mobilfunknetzdienst, jedoch kein WLAN. Die **PlayBall**-Bildschirm wird angezeigt.   

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Location.Latitude** |Gibt den Breitengrad der aktuellen Position zurück. Das Feld befindet sich in den Kartenkoordinaten 47,591 N, 122,333 W. |47.591<br><br>Der Breitengrad wird fortlaufend geändert, während sich der Ball vom Pitcher zum Catcher bewegt. |
| **Location.Longitude** |Gibt den Längengrad der aktuellen Position zurück |122.333<br><br>Der Längengrad wird fortlaufend geändert, während sich der Ball vom Pitcher zum Catcher bewegt. |
| **Location** |Gibt den Längen- und Breitengrad des aktuellen Standorts in einem Datensatz zurück |{&nbsp;Breitengrad:&nbsp;47.591, Längengrad:&nbsp;122.333&nbsp;} |
| **Compass.Heading** |Gibt die Kompassausrichtung des oberen Bildschirmrands zurück In diesem Feld befindet sich die Hausplatte ungefähr Südwest von der Spitze des Pitcher. |230.25 |
| **Acceleration.X** |Gibt die Beschleunigung des Geräts von linkem zu rechtem Rand an. Der Pitcher wirft das Gerät in Bezug auf den oberen Bildschirmrand geradeaus, sodass das Gerät nicht von Seite zu Seite beschleunigt. |0 |
| **Acceleration.Y** |Gibt die Beschleunigung des Geräts zwischen Vorder- und Rückseite an. Der Pitcher beschleunigt das Gerät anfänglich durch den Wurf erheblich, von 0 auf 90 Meilen pro Stunde (132 Fuß pro Sekunde) innerhalb einer halben Sekunde. Einmal in der Luft beschleunigt das Telefon, wenn die Luftreibung außen vor gelassen wird, nicht weiter. Das Gerät wird verlangsamt, wenn der Catcher es fängt, und wird angehalten. |8.2, während der Pitcher das Geräts wirft<br><br>0, während sich das Gerät in der Luft befindet<br><br>-8.2, während der Catcher das Gerät fängt |
| **Acceleration.Z** |Gibt die Beschleunigung des Geräts vom oberen zum unteren Rand an. Das Telefon unterliegt in der Luft den Auswirkungen der Schwerkraft. |0, bevor der Pitcher das Geräts wirft<br><br>1, während sich das Gerät in der Luft befindet<br><br>0, nachdem der Catcher das Gerät gefangen hat |
| **Acceleration** |Gibt die Beschleunigung als Datensatz zurück |{ X: 0, Y: 264, Z: 0 }, während der Pitcher das Telefon wirft |
| **Connection.Connected** |Gibt einen booleschen Wert zurück, der angibt, ob das Gerät mit einem Netzwerk verbunden ist |**TRUE** |
| **Connection.Metered** |Gibt einen booleschen Wert zurück, der angibt, ob die Verbindung getaktet ist |**TRUE** |
| **App.ActiveScreen = PlayBall** |Gibt einen booleschen Wert zurück, der angibt, ob **PlayBall** angezeigt wird. |**TRUE** |
| **App.ActiveScreen.Fill** |Gibt die Hintergrundfarbe des angezeigten Bildschirms zurück |**Color.Green** |

