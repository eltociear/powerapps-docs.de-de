---
title: Funktion „Defaults“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Funktion „Defaults“ in PowerApps
services: ''
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 11/01/2015
ms.author: gregli
ms.openlocfilehash: 0caa1c2cc4d9d1308255869fdb33149c8bb38139
ms.sourcegitcommit: 79b8842fb0f766a0476dae9a537a342c8d81d3b3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2018
ms.locfileid: "37897062"
---
# <a name="defaults-function-in-powerapps"></a>Funktion „Defaults“ in PowerApps
Gibt die Standardwerte für eine [Datenquelle](../working-with-data-sources.md) zurück.  

## <a name="description"></a>Beschreibung
Verwenden Sie die **Defaults**-Funktion, um ein Dateneingabeformular schon voraufzufüllen, sodass es einfacher zu füllen ist.

Diese Funktion gibt einen [Datensatz](../working-with-tables.md#records) zurück, der die Standardwerte für die Datenquelle enthält.  Wenn eine [Spalte](../working-with-tables.md#columns) innerhalb der Datenquelle nicht über einen Standardwert verfügt, ist diese Eigenschaft nicht vorhanden.

Datenquellen stellen unterschiedlich viele Standardinformationen zur Verfügung, manchmal sogar gar keine.  Beim Arbeiten mit einer [Sammlung](../working-with-data-sources.md#collections) oder einer anderen Datenquelle, die keine Standardwerte unterstützt, gibt die **Defaults**-Funktion einen [leeren](function-isblank-isempty.md) Datensatz zurück (empty).

Sie können die **Defaults**-Funktion mit der **[Patch](function-patch.md)**-Funktion kombinieren, um [einen Datensatz zu erstellen](../working-with-data-sources.md).

## <a name="syntax"></a>Syntax
**Defaults**( *DataSource* )

* *Datenquelle*: Erforderlich. Die Datenquelle, für die Sie Standardwerte haben möchten

## <a name="examples"></a>Beispiele

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Defaults(&nbsp;Scores&nbsp;)** |Gibt die Standardwerte für die **Scores**-Datenquelle zurück. |**{ Score: 0 }** |

