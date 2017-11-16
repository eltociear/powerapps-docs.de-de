---
title: "Funktion „Shuffle“ | Microsoft-Dokumentation"
description: "Referenzinformationen einschließlich Syntax und Beispielen für die Funktion „Shuffle“ in PowerApps"
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
ms.openlocfilehash: 672caee3b683bb0222b15a65cdad4edce78c4fe4
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="shuffle-function-in-powerapps"></a>Funktion „Shuffle“ in PowerApps
Sortiert die [Datensätze](../working-with-tables.md#records) einer [Tabelle](../working-with-tables.md) nach dem Zufallsprinzip neu

## <a name="description"></a>Beschreibung
Die **Shuffle**-Funktion sortiert die Datensätze einer Tabelle neu.

**Shuffle** gibt eine Tabelle zurück, die über die gleichen [Spalten](../working-with-tables.md#columns) und die gleiche Anzahl von Zeilen als das Argument verfügt.

## <a name="syntax"></a>Syntax
**Shuffle**( *Tabelle* )

* *Table*: erforderlich.  Die nach dem Zufallsprinzip zu sortierende Tabelle.

## <a name="example"></a>Beispiel
Wenn Sie Informationen zu Spielkarten in einer [Sammlung](../working-with-data-sources.md#collections) mit dem Namen **Deck** gespeichert hätten, würde diese Formel eine Kopie dieser Sammlung zurückgeben, die nach dem Zufallsprinzip sortiert wurde.

**Shuffle(Deck)**

