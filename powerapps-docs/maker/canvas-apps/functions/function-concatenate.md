---
title: Funktionen „Concat“ und „Concatenate“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen „Concat“ und „Concatenate“ in PowerApps
services: ''
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 08/28/2017
ms.author: gregli
ms.openlocfilehash: 5f69d51fc1d018a48576cade665ebd19ec1d7c82
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="concat-and-concatenate-functions-in-powerapps"></a>Funktionen „Concat“ und „Concatenate“ in PowerApps
Verketten einzelne Zeichenfolgen von Text und Zeichenfolgen in [Tabellen](../working-with-tables.md)

## <a name="description"></a>Beschreibung
Die **Concat**-Funktion verkettet das Ergebnis einer Formel, das in allen [Datensätzen](../working-with-tables.md#records) einer Tabelle angewendet wird, was zu einer einzelnen Zeichenfolge führt. Verwenden Sie diese Funktion, um die Zeichenfolgen einer Tabelle zusammenzufassen, wie es die **[Sum](function-aggregates.md)**-Funktion bei Zahlen macht.

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

Verwenden Sie die  **[Split](function-split.md)** -Funktion zum Aufteilen einer Zeichenfolge in eine Tabelle von Teilzeichenfolgen.

Die **Concatenate**-Funktion verkettet eine Mischung aus einzelnen Zeichenfolgen und eine einspaltige Tabelle von Zeichenfolgen. Wenn sie mit einzelnen Zeichenfolgen verwendet wird, entspricht diese Funktion der Verwendung des [Operators](operators.md) **&**. Sie können eine Formel verwenden, die die **[ShowColumns](function-table-shaping.md)**-Funktion umfasst, um aus einer Tabelle mit mehreren Spalten eine einspaltige Tabelle zu erstellen.

## <a name="syntax"></a>Syntax
**Concat**( *Tabelle*, *Formel* )

* *Tabelle* (erforderlich):  Die zu verarbeitende Tabelle.
* *Formel* (erforderlich):  Die auf alle Datensätze der Tabelle anzuwendende Formel.

**Concatenate**( *Zeichenfolge1* [, *Zeichenfolge2*, ...] )

* *Zeichenfolge(n)*: Erforderlich.  Mischung aus einzelnen Zeichenfolgen oder eine einspaltige Tabelle von Zeichenfolgen.

## <a name="examples"></a>Beispiele
#### <a name="concat"></a>Concat
1. Fügen Sie ein **[Button](../controls/control-button.md)**-Steuerelement (Schaltfläche) hinzu, und legen Sie seine **[OnSelect](../controls/properties-core.md)**-Eigenschaft auf diese Formel fest:
   
    **Collect(Products, {String:"Violin", Wind:"Trombone", Percussion:"Bongos"}, {String:"Cello", Wind:"Trumpet", Percussion:"Tambourine"})**
2. Drücken Sie F5, klicken Sie auf die Schaltfläche, und drücken Sie anschließend die ESC-TASTE, um zum Designarbeitsbereich zurückzukehren.
3. Fügen Sie ein **[Label](../controls/control-text-box.md)**-Steuerelement (Bezeichnung) hinzu, und legen Sie dessen **[Text](../controls/properties-core.md)**-Eigenschaft auf diese Formel fest:
   
    **Concat(Products, String & " ")**
   
    Die Bezeichnung zeigt **Violin Cello** (Violoncello) an.

#### <a name="concatenate"></a>Concatenate
1. Fügen Sie ein **[Texteingabe](../controls/control-text-input.md)**-Steuerelement hinzu, und benennen Sie es **AuthorName**.
2. Fügen Sie ein **[Label](../controls/control-text-box.md)**-Steuerelement (Bezeichnung) hinzu, und legen Sie dessen **[Text](../controls/properties-core.md)**-Eigenschaft auf diese Formel fest:<br>
   **Concatenate("By ", AuthorName.Text)**
3. Geben Sie Ihren Namen in **AuthorName** (Autorenname) ein.
   
    Die Bezeichnung zeigt **By** gefolgt von Ihrem Namen an.

Wenn Sie über eine Tabelle **Employees** (Mitarbeiter) verfügten, die eine Spalte **FirstName** (Vorname) und eine Spalte **LastName** (Nachname) umfasst, würde diese Formel die Daten in jeder Zeile dieser Spalten verketten.
<br>**Concatenate(Employees.FirstName, " ", Employees.LastName)**

