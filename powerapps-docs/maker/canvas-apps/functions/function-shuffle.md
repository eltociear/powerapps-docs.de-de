---
title: Funktion „Shuffle“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Funktion „Shuffle“ in PowerApps
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: 6d981c410b22dd9db52cdf077a00e6eaae83be75
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="shuffle-function-in-powerapps"></a>Funktion „Shuffle“ in PowerApps
Sortiert die [Datensätze](../working-with-tables.md#records) einer [Tabelle](../working-with-tables.md) nach dem Zufallsprinzip neu

## <a name="description"></a>Beschreibung
Die **Shuffle**-Funktion sortiert die Datensätze einer Tabelle neu.

**Shuffle** gibt eine Tabelle zurück, die über die gleichen [Spalten](../working-with-tables.md#columns) und die gleiche Anzahl von Zeilen als das Argument verfügt.

## <a name="syntax"></a>Syntax
**Shuffle**( *Tabelle* )

* *Tabelle* (erforderlich):  Die nach dem Zufallsprinzip zu sortierende Tabelle.

## <a name="example"></a>Beispiel
Wenn Sie Informationen zu Spielkarten in einer [Sammlung](../working-with-data-sources.md#collections) mit dem Namen **Deck** gespeichert hätten, würde diese Formel eine Kopie dieser Sammlung zurückgeben, die nach dem Zufallsprinzip sortiert wurde.

**Shuffle(Deck)**

