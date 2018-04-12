---
title: Funktion „Revert“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Funktion „Revert“ in PowerApps
services: ''
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/21/2015
ms.author: gregli
ms.openlocfilehash: e61566077ccdf9f3b2913ec0293868c1863c26fa
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="revert-function-in-powerapps"></a>Funktion „Revert“ in PowerApps
Aktualisiert und behebt Fehler für die [Datensätze](../working-with-tables.md#records) einer [Datenquelle](../working-with-data-sources.md)

## <a name="description"></a>Beschreibung
Die **Revert**-Funktion aktualisiert eine gesamte Datenquelle oder einen einzelnen Datensatz in der Datenquelle. Sie können die Änderungen anzeigen, die andere Benutzer vorgenommen haben.

Bei den wiederhergestellten Datensätzen behebt **Revert** auf alle Fehler der [Tabelle](../working-with-tables.md), die von der **[Errors](function-errors.md)**-Funktion zurückgegeben werden.

Wenn die **[Errors](function-errors.md)**-Funktion einen Konflikt nach einem **[Patch](function-patch.md)**- oder einem anderen Datenvorgang meldet, führen Sie die **Revert**-Funktion auf den Datensatz aus, um mit der in Konflikt stehenden Version zu beginnen und die Änderung erneut vorzunehmen.

**Revert** hat keinen Rückgabewert. Sie können diese Funktion nur in einer [Verhaltensformel](../working-with-formulas-in-depth.md) verwenden.

## <a name="syntax"></a>Syntax
**Revert**( *Datenquelle* [, *Datensatz* ] )

* *Datenquelle*: Erforderlich. Die Datenquelle, die Sie wiederherstellen möchten.
* *Datensatz*: Optional.  Der Datensatz, den Sie wiederherstellen möchten.  Wenn Sie keinen Datensatz angeben, wird die gesamte Datenquelle wiederhergestellt.

## <a name="example"></a>Beispiel
In diesem Beispiel stellen Sie die Datenquelle namens **IceCream** (Eiscreme) wieder her, die mit den Daten in dieser Tabelle beginnt:

![](media/function-revert/icecream.png)

Ein Benutzer auf einem anderen Gerät ändert die **Quantity**-Eigenschaft des Datensatzes **Strawberry** (Erdbeere) auf **400**.  Etwa zur gleichen Zeit ändern Sie die gleiche Eigenschaft des gleichen Datensatzes auf **500**, wobei Sie keine Kenntnis von der anderen Änderung haben.

Sie verwenden die **[Patch](function-patch.md)**-Funktion, um den Datensatz zu aktualisieren:<br>
**Patch( IceCream, First( Filter( IceCream, Flavor = "Strawberry" ) ), { Quantity: 500 } )**

Sie überprüfen die **[Errors](function-errors.md)**-Tabelle und finden einen Fehler:

| Datensatz | [Spalte](../working-with-tables.md#columns) | Nachricht | Fehler |
| --- | --- | --- | --- |
| **{ ID: 1, Flavor: "Strawberry", Quantity: 300 }** |*blank* |**"The record you are trying to modify has been modified by another user.  Please revert the record and try again." (Der Datensatz, den Sie versuchen zu ändern, wurde von einem anderen Benutzer geändert. Bitte stellen Sie den Datensatz wieder her, und versuchen Sie es erneut.)** |**ErrorKind.Conflict** |

Basierend auf der Spalte **Error** (Fehler) haben Sie eine Schaltfläche **Reload** (Erneut laden), für die die **[OnSelect](../controls/properties-core.md)**-Eigenschaft auf diese Formel festgelegt wird:<br>
**Revert( IceCream, First( Filter( IceCream, Flavor = "Strawberry" ) ) )**

Nachdem Sie die **Reload**-Schaltfläche ausgewählt haben, ist die **[Errors](function-errors.md)**-Tabelle [leer](function-isblank-isempty.md), und der neue Wert für **Strawberry** wurde geladen:

![](media/function-revert/icecream-after.png)

Sie wenden Ihre Änderung erneut auf die vorherige Änderung an, und Ihre Änderung wird erfolgreich vorgenommen, da der Konflikt gelöst wurde.

![](media/function-revert/icecream-success.png)
