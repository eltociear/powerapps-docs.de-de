---
title: Funktion „Distinct“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispiele, für die Distinct-Funktion in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: 8b482972b7e209c8cca98aae44389c133d5d4dcf
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/13/2018
ms.locfileid: "39020329"
---
# <a name="distinct-function-in-powerapps"></a>Distinct-Funktion in PowerApps
Fasst [Datensätze](../working-with-tables.md#records) aus einer [Tabelle](../working-with-tables.md) zusammen, wobei Duplikate entfernt werden.

## <a name="description"></a>Beschreibung
Die **Distinct**-Funktion wertet eine Formel für jeden Datensatz einer Tabelle aus. **Distinct** gibt eine Tabelle mit einer Spalte mit den Ergebnissen zurück, wobei doppelte Werte entfernt wurden.  

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

## <a name="syntax"></a>Syntax
**Distinct**( *Table*, *Formula* )

* *Tabelle* (erforderlich):  Die Tabelle, die übergreifend ausgewertet werden soll.
* *Formel* (erforderlich):  Die für jeden Datensatz auszuwertende Formel.

## <a name="example"></a>Beispiel
Wenn Sie eine Tabelle **Mitarbeiter** mit einer Spalte **Abteilung** haben, würde diese Funktion jeden individuellen Abteilungsnamen in dieser Spalte auflisten, unabhängig davon, wie oft jeder Name in der Spalte angezeigt wird:

**Distinct(Employees, Department)**

