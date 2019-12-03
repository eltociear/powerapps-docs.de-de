---
title: Funktion „Shuffle“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktion "shuffle" in powerapps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c67e8095a7c0ed3246bce0401bbe787becd7cea0
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730156"
---
# <a name="shuffle-function-in-power-apps"></a>Funktion "shuffle" in powerapps
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

