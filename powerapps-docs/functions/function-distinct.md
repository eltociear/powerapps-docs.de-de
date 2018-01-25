---
title: "Funktion „Distinct“ | Microsoft-Dokumentation"
description: "Referenzinformationen, einschließlich Syntax und Beispiele, für die Distinct-Funktion in PowerApps"
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
ms.openlocfilehash: b4e2a7c44696a57d01db5ac39da65ad782f0edac
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2018
---
# <a name="distinct-function-in-powerapps"></a>Distinct-Funktion in PowerApps
Fasst [Datensätze](../working-with-tables.md#records) aus einer [Tabelle](../working-with-tables.md) zusammen, wobei Duplikate entfernt werden.

## <a name="description"></a>Beschreibung
Die **Distinct**-Funktion wertet eine Formel für jeden Datensatz einer Tabelle aus. **Distinct** gibt eine Tabelle mit einer Spalte mit den Ergebnissen zurück, wobei doppelte Werte entfernt wurden.  

[!INCLUDE [record-scope](../includes/record-scope.md)]

## <a name="syntax"></a>Syntax
**Distinct**( *Table*, *Formula* )

* *Table*: erforderlich.  Die Tabelle, die übergreifend ausgewertet werden soll.
* *Formel*: Erforderlich.  Die für jeden Datensatz auszuwertende Formel.

## <a name="example"></a>Beispiel
Wenn Sie eine Tabelle **Mitarbeiter** mit einer Spalte **Abteilung** haben, würde diese Funktion jeden individuellen Abteilungsnamen in dieser Spalte auflisten, unabhängig davon, wie oft jeder Name in der Spalte angezeigt wird:

**Distinct(Employees, Department)**

