---
title: Funktion „Table“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, zur Funktion „Table“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta anneta
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ec8f14e06852bac7e09527e49bfc363723c9ea1c
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61543462"
---
# <a name="table-function-in-powerapps"></a>Funktion „Table“ in PowerApps
Erstellt eine temporäre [Tabelle](../working-with-tables.md)

## <a name="description"></a>Beschreibung
Die **Table**-Funktion erstellt eine Tabelle aus einer Argumentliste von [Datensätzen](../working-with-tables.md#records).

Der [Spalten](../working-with-tables.md#columns) der Tabelle werden die Vereinigung aller Eigenschaften aus den Argumentdatensätzen. Jeder Spalte, für die im Datensatz kein Wert enthalten ist, wird ein *leerer* Wert hinzugefügt.

Tabellen stellen in PowerApps einen Wert dar, genau wie Zeichenfolgen oder Zahlen. Sie können eine Tabelle als Argument für eine Funktion angeben, und Funktionen können eine Tabelle als Ergebnis zurückgeben. Die **Table**-Funktion erstellt keine dauerhaften Tabellen. Stattdessen wird eine temporäre Tabelle aus deren Argumenten zurückgegeben.  Sie können diese temporäre Tabelle als Argument für eine andere Funktion angeben, in einem Katalog darstellen oder in eine andere Tabelle einbetten.  Weitere Details erfahren Sie unter [Arbeiten mit Tabellen](../working-with-tables.md).

Sie können auch eine einspaltige Tabelle mit der Syntax **[Wert1, Wert2,...]**  erstellen.

## <a name="syntax"></a>Syntax
**Table**( *Datensatz1* [, *Datensatz2*, ... ] )

* *Datensatz(-sätze)*: erforderlich. Die der Tabelle hinzuzufügenden Datensätze

## <a name="examples"></a>Beispiele
* Legen Sie die **[Items](../controls/properties-core.md)**-Eigenschaft eines Listenfelds auf diese Formel fest:
  <br>**Table({Color:"red"}, {Color:"green"}, {Color:"blue"})**
  
    Das Listenfeld zeigt jede Farbe als Option an.
* Fügen Sie einen Textkatalog hinzu, und legen Sie dessen **[Items](../controls/properties-core.md)**-Eigenschaft auf diese Funktion fest:<br>
  **Table({Item:"Violin123", Location:"France", Owner:"Fabrikam"}, {Item:"Violin456", Location:"Chile"})**
  
    Der Katalog zeigt zwei Datensätze, die beide den Namen und den Speicherort eines Elements enthalten. Nur ein Datensatz enthält den Namen des Besitzers.

