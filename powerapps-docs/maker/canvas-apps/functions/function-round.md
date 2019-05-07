---
title: Funktionen „Round“, „RoundDown“ und „RoundUp“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich der Syntax, der Funktionen „Round“, „RoundDown“ und „RoundUp“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8d96b9362047113bda332ab7e7e36c8d5cea0666
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61520511"
ms.PowerAppsDecimalTransform: true
---
# <a name="round-rounddown-and-roundup-functions-in-powerapps"></a>Die Funktionen „Round“, „RoundDown“ und „RoundUp“ in PowerApps
Rundet eine Zahl

## <a name="description"></a>Beschreibung
Die **Round**-, **RoundDown**- und **RoundUp**-Funktionen runden eine Zahl auf die angegebene Anzahl von Dezimalstellen:

* **Round** rundet auf, wenn die nächste Ziffer 5 oder höher ist. Andernfalls rundet dieser Funktion ab.
* **RoundDown** rundet immer auf die nächstniedrigere Zahl ab.
* **RoundUp** rundet immer auf die nächsthöhere Zahl auf.

Wenn Sie eine einzelne Zahl übergeben haben, ist der Rückgabewert die abgerundete Version dieser Zahl.  Wenn Sie eine einspaltige [Tabelle](../working-with-tables.md) übergeben, die Zahlen enthält, wird eine einspaltige Tabelle mit abgerundeten Zahlen zurückgegeben. Mehrspaltige Tabellen können in einspaltige Tabellen umgeformt werden, wie unter [Arbeiten mit Tabellen](../working-with-tables.md) beschrieben.

## <a name="syntax"></a>Syntax
**Round**( *Number*; *DecimalPlaces* )<br>**RoundDown**( *Number*; *DecimalPlaces* )<br>**RoundUp**( *Number*; *DecimalPlaces* )

* *Zahl*: erforderlich. Die zu rundende Zahl.
* *Dezimalstellen*: erforderlich.  Die Anzahl der Stellen rechts vom Dezimaltrennzeichen, auf die gerundet werden soll.  Verwenden Sie 0, um auf eine ganze Zahl zu runden.  

