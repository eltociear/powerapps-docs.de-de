---
title: Funktion „Refresh“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Funktion „Refresh“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/21/2015
ms.author: gregli
ms.openlocfilehash: aad4f24c692053cf450104e22bf039fc8dbe32d0
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/13/2018
ms.locfileid: "39015330"
---
# <a name="refresh-function-in-powerapps"></a>Funktion „Refresh“ in PowerApps
Aktualisiert die [Datensätze](../working-with-tables.md#records) einer [Datenquelle](../working-with-data-sources.md)

## <a name="description"></a>Beschreibung
Die **Refresh**-Funktion ruft eine neue Kopie einer Datenquelle ab.  Sie können die Änderungen anzeigen, die andere Benutzer vorgenommen haben.

**Refresh** weist keinen Rückgabewert auf; Sie können diese Funktion nur innerhalb einer [Verhaltensformel](../working-with-formulas-in-depth.md) verwenden.

## <a name="syntax"></a>Syntax
**Refresh**( *Datenquelle* )

* *Datenquelle*: Erforderlich. Die Datenquelle, die Sie aktualisieren möchten.

## <a name="example"></a>Beispiel
In diesem Beispiel aktualisieren Sie die Datenquelle namens **IceCream** (Eiscreme), die mit den Daten in dieser Tabelle beginnt:

![](media/function-refresh/icecream.png)

Ein Benutzer auf einem anderen Gerät ändert die **Quantity** (Menge) des Datensatzes **Strawberry** (Erdbeere) auf **400**.  Diese Änderung wird erst angezeigt, wenn diese Formel ausgeführt wird:

**Refresh( IceCream )**

Nachdem diese Formel ausgeführt wurde, zeigen Kataloge, die mit der **IceCream**-Datenquelle verbunden sind, den aktualisierten Wert für **Strawberry** an:

![](media/function-refresh/icecream-after.png)

