---
title: Funktionen „Collect“, „Clear“ und „ClearCollect“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispiele, für die Collect-, Clear- und ClearCollect-Funktionen in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 09/14/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 02a69fd7844de8965607cd828c6b3e17437ce34f
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678394"
---
# <a name="collect-clear-and-clearcollect-functions-in-powerapps"></a>Collect-, Clear- und ClearCollect-Funktionen in PowerApps

Erstellt und löscht [Sammlungen](../working-with-data-sources.md#collections) und fügt [Datensätze](../working-with-tables.md#records) zu einer beliebigen [Datenquelle](../working-with-data-sources.md) hinzu.

## <a name="description"></a>Beschreibung

### <a name="collect"></a>Collect

Die **Collect**-Funktion fügt Datensätze zu einer Datenquelle hinzu. Die hinzuzufügenden Elemente können sein:

- Ein einzelner Wert: Der Wert befindet sich im **[Wert](function-value.md)** -Feld eines neuen Datensatzes.  Alle anderen Eigenschaften bleiben [leer](function-isblank-isempty.md).
- Ein Datensatz: Jede benannte Eigenschaft wird in der entsprechenden Eigenschaft des neuen Datensatzes eingefügt.  Alle anderen Eigenschaften bleiben leer.
- Ein [Tabelle](../working-with-tables.md): Jeder Datensatz der Tabelle wird als ein separater Datensatz der Datenquelle hinzugefügt, wie oben beschrieben. Die Tabelle wird nicht als geschachtelte Tabelle zu einen Datensatz hinzugefügt. Umschließen Sie zu diesem Zweck zuerst die Tabelle in einem Datensatz.

Bei Verwendung mit einer Sammlung werden bei Bedarf zusätzliche [Spalten](../working-with-tables.md#columns) erstellt. Die Spalten für andere Datenquellen werden von der Datenquelle vordefiniert, und neue Spalten können nicht hinzugefügt werden.  

Wenn die Datenquelle nicht bereits vorhanden ist, wird eine Sammlung erstellt.

Sammlungen werden manchmal verwendet, um globale Variablen zu halten oder eine temporäre Kopie einer Datenquelle zu erstellen. Powerapps basieren auf Formeln, die automatisch neu berechnet werden, wenn der Benutzer mit einer APP interagiert. Sammlungen haben diesen Vorteil nicht und ihre Verwendung kann das Erstellen und Verstehen Ihrer App erschweren. Lesen Sie vor dem Verwenden einer Sammlung auf diese Weise [Working with Variables (Mit Variablen arbeiten)](../working-with-variables.md).

Sie können auch die **[Patch](function-patch.md)** -Funktion für die Erstellung von Datensätzen in einer Datenquelle verwenden.

**Collect** gibt die geänderte Datenquelle als Tabelle zurück.  **Collect** kann nur in einer [behavior formula (Verhaltensformel)](../working-with-formulas-in-depth.md) verwendet werden.

### <a name="clear"></a>Clear

Die **Clear**-Funktion löscht alle Datensätze einer Sammlung.  Die Spalten der Sammlung bleiben erhalten.

Beachten Sie, dass **Clear** nur bei Sammlungen und nicht bei anderen Datenquellen angewendet wird.  Für diesen Zweck können Sie **[RemoveIf](function-remove-removeif.md)( *DataSource*, TRUE)** verwenden.  Seien Sie vorsichtig, da dies alle Datensätze aus dem Speicher der Datenquelle entfernt und Auswirkungen auf andere Benutzer haben kann.

Sie können die **[Remove](function-remove-removeif.md)** -Funktion verwenden, um Datensätze gezielt zu entfernen.

**Clear** hat keinen Rückgabewert.  Es kann nur in einer Verhaltensformel verwendet werden.

### <a name="clearcollect"></a>ClearCollect

Die **ClearCollect**-Funktion löscht alle Datensätze aus einer Sammlung und fügt anschließend ein anderes Set von Datensätzen zur selben Sammlung hinzu.  Mit einer einzelnen Funktion bietet **ClearCollect** die Kombination von **Clear** und anschließend **Collect**.

**ClearCollect** gibt die geänderte Sammlung als Tabelle zurück.  **ClearCollect** kann nur in einer Verhaltensformel verwendet werden.

## <a name="syntax"></a>Syntax

**Collect**( *Datenquelle*, *Element*, ... )

* *DataSource*: erforderlich. Die Datenquelle, in die Sie Daten hinzufügen möchten.  Wenn nicht bereits vorhanden, wird eine neue Sammlung erstellt.
* *Element(e)* : Erforderlich.  Eine oder mehrere Datensätze oder Tabellen, die der Datenquelle hinzugefügt werden sollen.  

**Clear**( *Auflistung* )

* *Auflistung*: Erforderlich. Die Sammlung, die Sie löschen möchten.

**ClearCollect**( *Auflistung*, *Element*, ... )

* *Auflistung*: Erforderlich. Die Sammlung, die Sie löschen und zu der Sie dann Daten hinzufügen möchten.
* *Element(e)* : Erforderlich.  Eine oder mehrere Datensätze oder Tabellen, die der Datenquelle hinzugefügt werden sollen.  

## <a name="examples"></a>Beispiele

### <a name="clearing-and-adding-records-to-a-data-source"></a>Löschen und Hinzufügen von Datensätzen zu einer Datenquelle

In diesen Beispielen löschen und fügen Sie Daten zu einer Sammlung mit dem Namen **IceCream** hinzu. Die Datenquelle beginnt mit dem folgenden Inhalt:

![Beispiel Datenquelle](media/function-clear-collect-clearcollect/icecream.png)

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **ClearCollect( IceCream, {&nbsp;Flavor:&nbsp;"Strawberry",&nbsp;Quantity:&nbsp;300&nbsp;} )** |Löscht alle Daten aus der Sammlung **IceCream**, und fügt anschließend einen Datensatz hinzu, der eine Menge von Erdbeereis enthält. |<style>IMG {max-width: None}</style> ![Tabelle mit einem Datensatz](media/function-clear-collect-clearcollect/icecream-clearcollect.png)<br><br>Die **icecream** -Auflistung wurde ebenfalls geändert. |
| **Collect( IceCream, {&nbsp;Flavor:&nbsp;"Pistachio",&nbsp;Quantity:&nbsp;40&nbsp;}, {&nbsp;Flavor:&nbsp;"Orange",&nbsp;Quantity:&nbsp;200&nbsp;}  )** |Fügt der **icecream** -Auflistung zwei Datensätze hinzu, die eine Menge von Pistazie und orangefarbener Eiscreme enthalten. |![Tabelle mit zwei Datensätzen](media/function-clear-collect-clearcollect/icecream-collect.png)<br><br>Die **icecream** -Auflistung wurde ebenfalls geändert. |
| **Clear( IceCream )** |Entfernt alle Datensätze aus der Sammlung **IceCream**. |![leere Tabelle](media/function-clear-collect-clearcollect/icecream-clear.png)<br><br>Die **icecream** -Auflistung wurde ebenfalls geändert. |

Schritt-für-Schritt-Beispiele zum Erstellen einer Sammlung finden Sie unter [Erstellen und Aktualisieren einer Sammlung](../create-update-collection.md).

### <a name="records-and-tables"></a>Datensätze und Tabellen

In diesen Beispielen wird untersucht, wie Datensatz-und Tabellen Argumente **erfasst** und **clearcollect** behandelt werden.

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Clearcollect (icecream, {&nbsp;Flavor:&nbsp;"Chocolate",&nbsp;Menge:&nbsp;100&nbsp;}, {&nbsp;Flavor:&nbsp;"Vanille",&nbsp;Menge:&nbsp;200&nbsp;})** | Löschen Sie alle Daten, und fügen Sie dann der **icecream** -Auflistung zwei Datensätze hinzu, die eine Menge von Schoko-und Vanille-Eis enthalten.  Die hinzu zufügenden Datensätze werden als einzelne Argumente der Funktion bereitgestellt.| ![der Sammlung hinzugefügte Schoko-und Vanille Datensätze](media/function-clear-collect-clearcollect/icecream.png) <br><br>Die **icecream** -Auflistung wurde ebenfalls geändert. |
| **Clearcollect (icecream, Tabelle ({&nbsp;Flavor:&nbsp;"Chocolate",&nbsp;Menge:&nbsp;100&nbsp;}, {&nbsp;Flavor:&nbsp;"Vanille",&nbsp;Menge:&nbsp;200&nbsp;}))** | Identisch mit dem vorherigen Beispiel, mit dem Unterschied, dass die Datensätze in einer Tabelle kombiniert und durch ein einzelnes Argument übermittelt werden. Der Inhalt der Tabelle wird nach Datensatz extrahiert, bevor Sie der **icecream** -Auflistung hinzugefügt wird. | ![der Sammlung hinzugefügte Schoko-und Vanille Datensätze](media/function-clear-collect-clearcollect/icecream.png)<br><br>Die **icecream** -Auflistung wurde ebenfalls geändert. |
| **Clearcollect (icecream,<br>{&nbsp;myfavoriten: Table ({&nbsp;Flavor:&nbsp;"Chocolate",&nbsp;Menge:&nbsp;100&nbsp;}, {&nbsp;Flavor:&nbsp;"Vanille",&nbsp;Menge:&nbsp;200&nbsp;})})** | Identisch mit dem vorherigen Beispiel, mit der Ausnahme, dass die Tabelle in einem Datensatz umschließt ist.  Die Datensätze der Tabelle werden nicht extrahiert, und stattdessen wird die gesamte Tabelle als untergeordnete Tabelle des Datensatzes hinzugefügt. | ![der Sammlung hinzugefügte Schoko-und Vanille Datensätze](media/function-clear-collect-clearcollect/icecream-myfavorites.png)<br><br>Die **icecream** -Auflistung wurde ebenfalls geändert. |

