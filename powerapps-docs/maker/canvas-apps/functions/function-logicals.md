---
title: Funktionen „And“, „Or“ und „Not“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen „And“, „Or“ und „Not“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 4eb020d854549b6dc8878f07ae26390523a1bc03
ms.sourcegitcommit: aa9f78c304fe46922aecfe3b3fadb6bda72dfb23
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66215974"
---
# <a name="and-or-and-not-functions-in-powerapps"></a>Die Funktionen „And“, „Or“ und „Not“ in PowerApps

Boolesche Logikfunktionen, die oft dazu verwendet werden, die Ergebnisse von Vergleichen und Tests zu bearbeiten

## <a name="description"></a>Beschreibung

Die **And**-Funktion gibt **TRUE** zurück, wenn alle ihre Argumente **TRUE** sind.

Die **Or**-Funktion gibt **TRUE** zurück, wenn eines der Argumente **TRUE** ist.

Die **Not**-Funktion gibt **TRUE** zurück, wenn ihr Argument **FALSE** ist; sie gibt **FALSE** zurück, wenn ihr Argument **TRUE** ist.

Diese Funktionen funktionieren genauso wie in Excel. Sie können auch [Operatoren](operators.md) zum Ausführen dieser gleiche Vorgänge, die mit Visual Basic oder JavaScript-Syntax:

| Funktion-notation | Visual Basic-Operator-notation | JavaScript-Operator-notation |
| -------------|------------|--------|
| **And( x, y )** | **X und y** | **x && y** |
| **Or( x, y )** | **X oder y** | **x &#124;&#124; y** |
| **Not( x )** | **Nicht-x** | **! x** |

Diese Funktionen arbeiten mit logischen Werten. Sie können keine sie eine Zahl oder eine Zeichenfolge direkt übergeben; Stattdessen müssen Sie einen Vergleich oder einen Test. Beispielsweise diese logische Formel **x > 1** den booleschen Wert ergibt **"true"** Wenn **x** ist größer als **1**. Wenn **x** ist kleiner als **1**, ergibt die Formel **"false"** .

## <a name="syntax"></a>Syntax

**And**( *LogicalFormula1*, *LogicalFormula2* [, *LogicalFormula3*, ... ] )<br>
**Or**( *LogicalFormula1*, *LogicalFormula2* [, *LogicalFormula3*, ... ] )<br>
**Not**( *LogicalFormula* )

- *LogicalFormula(s)* : erforderlich.  Logische Formeln, die bewertet und verarbeitet werden sollen

## <a name="examples"></a>Beispiele

In die Beispielen in diesem Abschnitt verwenden Sie diese globale Variablen:

- **eine** =  *"false"*
- **b** = *true*
- **x** = 10
- **y** = 100
- **s** = "Hello World"

Um diese globalen Variablen in einer app zu erstellen, fügen Sie eine [ **Schaltfläche** ](../controls/control-button.md) steuern, und legen dessen **OnSelect** -Eigenschaft auf diese Formel:

```powerapps-dot
Set( a, false ); Set( b, true ); Set( x, 10 ); Set( y, 100 ); Set( s, "Hello World" )
```

Wählen Sie die Schaltfläche (indem Sie darauf klicken und Sie halten Sie die Alt-Taste gedrückt), und legen Sie dann die **Text** Eigenschaft eine [ **Bezeichnung** ](../controls/control-text-box.md) Steuerelement auf eine Formel in der ersten Spalte der folgenden Tabelle.

| Formel | Beschreibung | Ergebnis |
|---------|-------------|--------|
| **And( a, b )** | Überprüft die Werte der **eine** und **b**.  Eines der Argumente ist *"false"* , sodass die Funktion gibt *"false"* . | *FALSE* |
| **ein And b** | Identisch mit dem vorherigen Beispiel mithilfe der Visual Basic-Notation. | *FALSE* |
| **a && b** | Identisch mit dem vorherigen Beispiel mithilfe der JavaScript-Notation. | *FALSE* |
| **Or( a, b )** | Überprüft die Werte der **eine** und **b**. Eines der Argumente ist *"true"* , sodass die Funktion gibt *"true"* . | *TRUE* |
| **a Or b** | Identisch mit dem vorherigen Beispiel mithilfe der Visual Basic-Notation. | *TRUE* |
| **a &#124;&#124; b** | Identisch mit dem vorherigen Beispiel mithilfe der JavaScript-Notation. | *TRUE* |
| **Keine (a)** | Testet, ob der Wert des **eine**. Das Argument ist *"false"* , sodass die Funktion den entgegengesetzte Ergebnis zurückgibt. | *TRUE* |
| **Kein** | Identisch mit dem vorherigen Beispiel mithilfe der Visual Basic-Notation. | *TRUE* |
| **! ein** | Identisch mit dem vorherigen Beispiel mithilfe der JavaScript-Notation. | *TRUE* |
| **Len (&nbsp;s&nbsp;)&nbsp;<&nbsp;20 und&nbsp;nicht&nbsp;IsBlank (&nbsp;s&nbsp;)** | Tests, ob die Länge des **s** kleiner als 20 und gibt an, ob dies nicht der Fall ein **leere** Wert. Die Länge ist kleiner als 20, und der Wert ist nicht leer. Das Ergebnis aus diesem Grund ist *"true"* . | *TRUE* |
| **Oder (&nbsp;Len (&nbsp;s&nbsp;)&nbsp;<&nbsp;, 10-fache&nbsp;<&nbsp;100, y&nbsp;<&nbsp;100&nbsp;)** | Tests, ob die Länge des **s** ist kleiner als 10 gibt an, ob **x** weniger als 100 ist, und gibt an, ob **y** ist kleiner als 100. Das erste und dritte Argument "false" werden, aber der zweite Parameter ist "true". Aus diesem Grund gibt die Funktion zurück *"true"* . | *TRUE* |
| **Nicht IsBlank (&nbsp;s&nbsp;)** | Tests, ob **s** ist *leere*, gibt *"false"* . **Nicht** gibt zurück, das Gegenteil dieses Ergebnisses, handelt es sich *"true"* . | *TRUE* |