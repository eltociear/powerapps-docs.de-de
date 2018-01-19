---
title: "Funktionen „Round“, „RoundDown“ und „RoundUp“ | Microsoft-Dokumentation"
description: "Referenzinformationen, einschließlich der Syntax, der Funktionen „Round“, „RoundDown“ und „RoundUp“ in PowerApps"
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
ms.openlocfilehash: cfb0e8351b1e51a07962e08b2894d02203b274c7
ms.sourcegitcommit: 33099e6197c0139679cd08c42e9e2a5717904c92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2018
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
**Round**( *Number*, *DecimalPlaces* )<br>**RoundDown**( *Number*, *DecimalPlaces* )<br>**RoundUp**( *Number*, *DecimalPlaces* )

* *Zahl*: erforderlich. Die zu rundende Zahl.
* *Dezimalstellen*: erforderlich.  Die Anzahl der Stellen rechts vom Dezimaltrennzeichen, auf die gerundet werden soll.  Verwenden Sie 0, um auf eine ganze Zahl zu runden.  

