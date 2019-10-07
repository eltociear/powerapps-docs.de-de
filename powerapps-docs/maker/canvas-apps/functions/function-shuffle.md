---
title: Funktion „Shuffle“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Funktion „Shuffle“ in PowerApps
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
ms.openlocfilehash: 181ef038a90c9bfc7e3fe72af9514a34afce9776
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71983927"
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

