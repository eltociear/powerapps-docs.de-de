---
title: Funktion „Refresh“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Funktion „Refresh“ in PowerApps
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 10/21/2015
ms.author: gregli
ms.openlocfilehash: 9ec2711c4a38f26fec2d44681b2606b4a8ecba29
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "31825370"
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

