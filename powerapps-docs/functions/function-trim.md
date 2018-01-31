---
title: "Funktionen „Trim“ und „TrimEnds“ | Microsoft-Dokumentation"
description: "Referenzinformationen einschließlich Syntax und Beispiele für die Trim- und TrimEnds-Funktionen in PowerApps"
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
ms.date: 09/09/2016
ms.author: gregli
ms.openlocfilehash: b40f44f8bdcb319191221d0f2cee39e15d5b3b49
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2018
---
# <a name="trim-and-trimends-functions-in-powerapps"></a>Trim- und TrimEnds-Funktionen in PowerApps
Entfernt zusätzliche Leerzeichen aus einer Textzeichenfolge.

## <a name="description"></a>Beschreibung
Die **Trim**-Funktion entfernt alle Leerzeichen aus einer Textzeichenfolge mit Ausnahme einzelner Leerzeichen zwischen Wörtern.  

Die **TrimEnds**-Funktion entfernt alle Leerzeichen am Anfang und Ende einer Textzeichenfolge, aber Leerzeichen zwischen Wörtern bleiben intakt.

Wenn Sie eine einzelne Textzeichenfolge angeben, ist der Rückgabewert für eine Funktion die Zeichenfolge, bei der jedes zusätzliche Leerzeichen entfernt wurde. Wenn Sie eine einspaltige [Tabelle](../working-with-tables.md) angeben, die Zeichenfolgen enthält, ist der Rückgabewert eine einspaltige Tabelle mit zugeschnittenen Zeichenfolgen. Mehrspaltige Tabellen können in einspaltige Tabellen umgeformt werden, wie unter [Arbeiten mit Tabellen](../working-with-tables.md) beschrieben.

Durch das Entfernen der Leerzeichen zwischen Wörtern ist **Trim** konsistent mit der Funktion mit dem gleichen Namen in Microsoft Excel. Allerdings ist **TrimEnds** konsistent mit der Programmierung von Tools, die Leerzeichen nur am Anfang und Ende einer Zeichenfolge entfernt.

## <a name="syntax"></a>Syntax
**Trim**( *Zeichenfolge* )<br>**TrimEnds**( *Zeichenfolge* )

* *Zeichenfolge*: erforderlich. Die Textzeichenfolge, bei der Leerzeichen entfernt werden sollen.

**Trim**( *EinspaltigeTabelle* )<br>**TrimEnds**( *EinspaltigeTabelle* )

* *EinspaltigeTabelle*: erforderlich. Eine einspaltige Tabelle mit Zeichenfolgen, in der Leerzeichen entfernt werden sollen.

## <a name="example"></a>Beispiel
| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Trim(&nbsp;"&nbsp;&nbsp;&nbsp;Hello&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;World&nbsp;&nbsp;&nbsp;"&nbsp;)** |Entfernt alle Leerzeichen am Anfang und Ende einer Zeichenfolge und zusätzliche Leerzeichen innerhalb der Zeichenfolge. |„Hello World“ |
| **TrimEnds(&nbsp;"&nbsp;&nbsp;&nbsp;Hello&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;World&nbsp;&nbsp;&nbsp;"&nbsp;)** |Entfernt alle Leerzeichen am Anfang und Ende einer Zeichenfolge. |„Hello&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;World“ |

Die folgenden Beispiele verwenden eine einspaltige-Sammlung mit dem Namen **Spaces**, die diese Zeichenfolgen enthält:

![](media/function-trim/input-strings.png)

Legen Sie die Eigenschaft **OnSelect** eines Steuerelements **[Schaltfläche](../controls/control-button.md)** auf diese Formel fest, öffnen Sie den Vorschaumodus, und klicken oder tippen Sie anschließend auf die Schaltfläche, um eine Sammlung zu erstellen:
<br>**ClearCollect( Spaces, [ "&nbsp;&nbsp;&nbsp;Jane&nbsp;&nbsp;&nbsp;Doe&nbsp;&nbsp;&nbsp;", "&nbsp;&nbsp;&nbsp;&nbsp;Jack&nbsp;&nbsp;&nbsp;and&nbsp;&nbsp;&nbsp;Jill", "Already&nbsp;trimmed", "&nbsp;&nbsp;&nbsp;Venus,&nbsp;&nbsp;&nbsp;Earth,&nbsp;&nbsp;&nbsp;Mars&nbsp;&nbsp;", "Oil&nbsp;and&nbsp;Water&nbsp;&nbsp;&nbsp;" ] )**

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Trim(&nbsp;Spaces&nbsp;)** |Entfernt alle Leerzeichen am Anfang und Ende jeder Zeichenfolge und zusätzliche Leerzeichen innerhalb der Zeichenfolgen in der Sammlung **Spaces**. |<style> img { max-width: none } </style> ![](media/function-trim/output-trim.png) |
| **TrimEnds(&nbsp;Spaces&nbsp;)** |Entfernt alle Leerzeichen am Anfang und Ende einer Zeichenfolge in der Sammlung **Spaces**. |<style> img { max-width: none } </style> ![](media/function-trim/output-trimends.png) |

> [!NOTE]
> Zusätzliche Leerzeichen werden nicht angezeigt, wenn Sie eine Sammlung anzeigen, indem Sie im Menü **File** auf **Sammlungen** klicken oder tippen. Verwenden Sie die **[Len](function-len.md)**-Funktion, um die Länge der Zeichenfolge zu überprüfen.

