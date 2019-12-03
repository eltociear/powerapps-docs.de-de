---
title: Funktionen „Round“, „RoundDown“ und „RoundUp“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax, für die Funktionen "Round", "ROUNDDOWN" und "Roundup" in powerapps
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
ms.openlocfilehash: 3b319f831291b1d0d21f3ed4699a144beb023611
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730288"
---
# <a name="round-rounddown-and-roundup-functions-in-power-apps"></a>Funktionen "Round", "ROUNDDOWN" und "Roundup" in powerapps
Rundet eine Zahl

## <a name="description"></a>Beschreibung
Die **Round**-, **RoundDown**- und **RoundUp**-Funktionen runden eine Zahl auf die angegebene Anzahl von Dezimalstellen:

* **Round** rundet auf, wenn die nächste Ziffer 5 oder höher ist. Andernfalls rundet dieser Funktion ab.
* **RoundDown** rundet immer auf die nächstniedrigere Zahl ab.
* **RoundUp** rundet immer auf die nächsthöhere Zahl auf.

Wenn Sie eine einzelne Zahl übergeben haben, ist der Rückgabewert die abgerundete Version dieser Zahl.  Wenn Sie eine einspaltige [Tabelle](../working-with-tables.md) übergeben, die Zahlen enthält, wird eine einspaltige Tabelle mit abgerundeten Zahlen zurückgegeben. Mehrspaltige Tabellen können in einspaltige Tabellen umgeformt werden, wie unter [Arbeiten mit Tabellen](../working-with-tables.md) beschrieben.

## <a name="syntax"></a>Syntax
**Round**( *Number*, *DecimalPlaces* )<br>**RoundDown**( *Number*, *DecimalPlaces* )<br>**RoundUp**( *Number*, *DecimalPlaces* )

* *Zahl*: erforderlich. Die zu rundende Zahl.
* *Dezimalstellen*: erforderlich.  Die Anzahl der Stellen rechts vom Dezimaltrennzeichen, auf die gerundet werden soll.  Verwenden Sie 0, um auf eine ganze Zahl zu runden.  

