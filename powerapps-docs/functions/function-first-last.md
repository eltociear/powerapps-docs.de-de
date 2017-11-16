---
title: "Funktionen „First“, „FirstN“, „Last“ und „LastN“ | Microsoft-Dokumentation"
description: "Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen „First“, „FirstN“, „Last“ und „LastN“ in PowerApps"
services: 
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: 0a056aa20532ffe6e2e8ae502e67b5b27d134839
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="first-firstn-last-and-lastn-functions-in-powerapps"></a>Die Funktion „First“, „FirstN“, „Last“ und „LastN“ in PowerApps
Gibt den ersten oder letzten Satz von [Datensätze](../working-with-tables.md#records) einer Tabelle zurück.

## <a name="description"></a>Beschreibung
Die **First**-Funktion gibt den ersten Datensatz einer [Tabelle](../working-with-tables.md) zurück.

Die **FirstN**-Funktion gibt die erste Gruppe von Datensätzen einer Tabelle zurück; das zweite Argument gibt die Anzahl der zurückzugebenden Datensätze an.

Die **Last**-Funktion gibt den letzten Datensatz einer Tabelle zurück.

Die **LastN**-Funktion gibt die letzte Gruppe von Datensätzen einer Tabelle zurück; das zweite Argument gibt die Anzahl der zurückzugebenden Datensätze an.

**First** und **Last**  geben einen einzelnen Datensatz zurück.  **FirstN** und **LastN** geben eine Tabelle zurück, selbst wenn Sie nur einen einzelnen Datensatz angeben.

[!INCLUDE [delegation-no](../../includes/delegation-no.md)]

## <a name="syntax"></a>Syntax
**First**( *Table* )<br>**Last**( *Table* )

* *Tabelle*: erforderlich. Die zu verarbeitende Tabelle.

**FirstN**( *Table* [, *NumberOfRecords* ] )<br>**LastN**( *Table* [, *NumberOfRecords* ] )

* *Table*: erforderlich. Die zu verarbeitende Tabelle.
* *ZahlDerDatensätze*: optional.  Die Anzahl der zurückzugebenden Datensätze. Wenn Sie dieses Argument nicht angeben, gibt die Funktion einen Datensatz zurück.

## <a name="examples"></a>Beispiele
Diese Formel gibt den ersten Datensatz aus einer Tabelle mit dem Namen **Employees** (Mitarbeiter) zurück:<br>
**First(Employees)**

Diese Formel gibt die letzten 15 Datensätze aus einer Tabelle mit dem Namen **Employees** zurück:<br>
**LastN(Employees, 15)**

