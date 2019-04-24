---
title: Funktion „Char“ | Microsoft-Dokumentation
description: Referenzinformationen zur Funktion „Char“ in PowerApps, einschließlich Syntax und Beispielen
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 03/01/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1b598cc863ec01bcb2a66a9510cb48ec5203e679
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61559661"
---
# <a name="char-function-in-powerapps"></a>Funktion „Char“ in PowerApps

Übersetzt einen Zeichencode in eine Zeichenfolge

## <a name="description"></a>Beschreibung

Die **Char** Funktion übersetzt eine Zahl in eine Zeichenfolge durch das entsprechende ASCII-Zeichen.

## <a name="syntax"></a>Syntax

**Char**( *ZeichenCode* )

- *ZeichenCode*: erforderlich. Zu übersetzender ASCII-Zeichencode

## <a name="examples"></a>Beispiele

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Char( 65 )** |Gibt das Zeichen zurück, das ASCII-Code 65 entspricht |"A" |
| **Char( 105 )** |Gibt das Zeichen zurück, das ASCII-Code 105 entspricht |"i" |
| **Char( 35 )** |Gibt das Zeichen zurück, das ASCII-Code 35 entspricht |"#" |

### <a name="display-a-character-map"></a>Zeigt eine zeichenzuordnung

1. Auf einem leeren Bildschirm in eine Tablet-app hinzufügen eine [ **Katalog** ](../controls/control-gallery.md) steuern Sie mit einer **leere horizontale** Layout, und legen Sie diese Eigenschaften:

    - **Elemente**: `[0,1,2,3,4,5,6,7]`
    - **Width**: 800
    - **Höhe**: 500
    - **TemplateSize**: 100
    - **TemplatePadding**: 0

1. Fügen Sie diesen Katalog, eine **Katalog** steuern Sie mit einer **leere vertikale** Layout, und legen Sie diese Eigenschaften:

    - **Elemente**: `ForAll( [0,2,3,4,5,6,7,8,9,10,11,12,13,14,15], Value + ThisItem.Value * 16 )`
    - **Width**: 100
    - **Höhe**: 500
    - **TemplateSize**: 30
    - **TemplatePadding**: 0

    Der Wert des der **Elemente** Eigenschaft multipliziert, 16 x die Nummer der Spalte, die von der Spalte Wert der bereitgestellten der **Elemente** Eigenschaft aus dem ersten Katalog (0 bis 7 in `ThisItem.Value`). Die Formel fügt dann das Ergebnis auf eine der Nummern der Zeilen aus dem Katalog der zweiten (0 bis 15 im Datensatz zu begrenzen, die die [ **ForAll** ](function-forall.md) -Funktion).

1. Der zweite (vertikal) Katalog, fügen Sie eine **Bezeichnung** steuern, und legen Sie diese Eigenschaften:

    - **Text**: `ThisItem.Value`
    - **Width**: 50

1. Der zweite (vertikal) Katalog, fügen Sie einen anderen **Bezeichnung** steuern, und legen Sie diese Eigenschaften:

    - **Text**: `Char( ThisItem.Value )`
    - **Width**: 50
    - **X**: 50

Sie haben ein Diagramm mit den ersten 128 ASCII-Zeichen erstellt. Zeichen, die angezeigt werden, wie ein kleines Quadrat nicht gedruckt werden kann.

![Zuerst 128 ASCII-Zeichen](media/function-char/chart-lower.png)

Um die erweiterten ASCII-Zeichen anzuzeigen, legen die **Elemente** -Eigenschaft des zweiten Katalogs auf diese Formel, die jeder Zeichenwert 128 hinzufügt:

`ForAll( [0,2,3,4,5,6,7,8,9,10,11,12,13,14,15], Value + ThisItem.Value * 16 + 128)`

![Erweiterte ASCII-Zeichen](media/function-char/chart-higher.png)

Um die Zeichen in einer anderen Schriftart anzuzeigen, legen die **Schriftart** -Eigenschaft der zweiten Bezeichnung auf einen Wert wie z. B. **"Tanzen Script"**.

![Tanzen Skript](media/function-char/chart-higher-dancing-script.png)
