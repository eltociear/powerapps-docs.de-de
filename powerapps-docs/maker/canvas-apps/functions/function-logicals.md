---
title: Funktionen „And“, „Or“ und „Not“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen „And“, „Or“ und „Not“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a2b04e6a752ade561ec1b95658bcacda759b1a1c
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992555"
ms.PowerAppsDecimalTransform: true
---
# <a name="and-or-and-not-functions-in-powerapps"></a>Die Funktionen „And“, „Or“ und „Not“ in PowerApps

Boolesche Logikfunktionen, die oft dazu verwendet werden, die Ergebnisse von Vergleichen und Tests zu bearbeiten

## <a name="description"></a>Beschreibung

Die **And**-Funktion gibt **TRUE** zurück, wenn alle ihre Argumente **TRUE** sind.

Die **Or**-Funktion gibt **TRUE** zurück, wenn eines der Argumente **TRUE** ist.

Die **Not**-Funktion gibt **TRUE** zurück, wenn ihr Argument **FALSE** ist; sie gibt **FALSE** zurück, wenn ihr Argument **TRUE** ist.

Diese Funktionen funktionieren genauso wie in Excel. Sie können auch [Operatoren](operators.md) verwenden, um dieselben Vorgänge auszuführen, indem Sie entweder Visual Basic oder JavaScript-Syntax verwenden:

| Funktions Notation | Visual Basic Operator Notation | JavaScript-Operator Notation |
| -------------|------------|--------|
| **Und (x, y)** | **x und y** | **x & & y** |
| **Oder (x, y)** | **x oder y** | **x &#124; &#124; y** |
| **Nicht (x)** | **Nicht x** | **! Stuben** |

Diese Funktionen arbeiten mit logischen Werten. Sie können Ihnen nicht direkt eine Zahl oder eine Zeichenfolge übergeben. Stattdessen müssen Sie einen Vergleich oder einen Test durchführen. Diese logische Formel **x > 1** wertet z. b. den booleschen Wert **true** aus, wenn **x** größer als **1**ist. Wenn " **x** " kleiner als **1**ist, wird die Formel als " **false**" ausgewertet.

## <a name="syntax"></a>Syntax

**And**( *LogicalFormula1*; *LogicalFormula2* [; *LogicalFormula3*; ... ] )<br>
**Or**( *LogicalFormula1*; *LogicalFormula2* [; *LogicalFormula3*; ... ] )<br>
**Not**( *LogicalFormula* )

- *LogicalFormula(s)* : erforderlich.  Logische Formeln, die bewertet und verarbeitet werden sollen

## <a name="examples"></a>Beispiele

In den Beispielen in diesem Abschnitt werden diese globalen Variablen verwendet:

- **a** = *false*
- **b** = *true*
- **x** = 10
- **j** = 100
- **s** = "Hallo Welt"

Wenn Sie diese globalen Variablen in einer APP erstellen möchten, fügen Sie ein [**Button**](../controls/control-button.md) -Steuerelement ein, und legen **Sie dessen onselect** -Eigenschaft auf diese Formel fest:

```powerapps-comma
Set( a; false );; Set( b; true );; Set( x; 10 );; Set( y; 100 );; Set( s; "Hello World" )
```

Wählen Sie die Schaltfläche aus (indem Sie darauf klicken, während Sie die Alt-Taste gedrückt halten), und legen Sie dann die **Text** -Eigenschaft eines [**Label**](../controls/control-text-box.md) -Steuer Elements auf eine Formel in der ersten Spalte der nächsten Tabelle fest.

| Formel | Beschreibung | Ergebnis |
|---------|-------------|--------|
| **Und (a, b)** | Testet die Werte von **a** und **b**.  Eines der Argumente ist " *false*", sodass die Funktion " *false*" zurückgibt. | *FALSE* |
| **a und b** | Identisch mit dem vorherigen Beispiel mit Visual Basic Notation. | *FALSE* |
| **a & & b** | Identisch mit dem vorherigen Beispiel mithilfe der JavaScript-Notation. | *FALSE* |
| **Oder (a, b)** | Testet die Werte von **a** und **b**. Eines der Argumente ist " *true*", sodass die Funktion " *true*" zurückgibt. | *TRUE* |
| **a oder b** | Identisch mit dem vorherigen Beispiel mit Visual Basic Notation. | *TRUE* |
| **a &#124; &#124; b** | Identisch mit dem vorherigen Beispiel mithilfe der JavaScript-Notation. | *TRUE* |
| **Nicht (a)** | Testet den **Wert von.** Das-Argument ist *false*, sodass die-Funktion das Gegenteil-Ergebnis zurückgibt. | *TRUE* |
| **Keine** | Identisch mit dem vorherigen Beispiel mit Visual Basic Notation. | *TRUE* |
| **! ein** | Identisch mit dem vorherigen Beispiel mithilfe der JavaScript-Notation. | *TRUE* |
| **Len (&nbsp;s&nbsp;)&nbsp;<&nbsp;20 und&nbsp;nicht&nbsp;isblank (&nbsp;s&nbsp;)** | Testet, ob die Länge von **s** kleiner als 20 ist und ob es sich nicht um einen **leeren** Wert handelt. Die Länge ist kleiner als 20, und der Wert ist nicht leer. Daher ist das Ergebnis " *true*". | *TRUE* |
| **Or (&nbsp;len (&nbsp;s&nbsp;)&nbsp;<&nbsp;10, x&nbsp;<&nbsp;100, y&nbsp;<&nbsp;100&nbsp;)** | Testet, ob die Länge von **s** kleiner als 10 ist, ob **x** kleiner als 100 ist und ob **y** kleiner als 100 ist. Das erste und dritte Argument sind false, das zweite Argument ist jedoch true. Daher gibt die Funktion *true*zurück. | *TRUE* |
| **Nicht isblank (&nbsp;s&nbsp;)** | Testet, ob s *leer*ist, und gibt *false*zurück. Gibt **nicht** das Gegenteil dieses Ergebnisses zurück, was *true*ist. | *TRUE* |