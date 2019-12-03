---
title: Funktion „Char“ | Microsoft-Dokumentation
description: Referenzinformationen für die Char-Funktion in powerapps, einschließlich Syntax und Beispielen
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/01/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 641b22945dc6398e0f1ab57b03813eb7db02c79f
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678417"
---
# <a name="char-function-in-powerapps"></a>Funktion „Char“ in PowerApps

Übersetzt einen Zeichencode in eine Zeichenfolge

## <a name="description"></a>Beschreibung

Die **char** -Funktion übersetzt eine Zahl in eine Zeichenfolge mit dem entsprechenden ASCII-Zeichen.

## <a name="syntax"></a>Syntax

**Char**( *ZeichenCode* )

- *ZeichenCode*: erforderlich. Zu übersetzender ASCII-Zeichencode

## <a name="examples"></a>Beispiele

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Char( 65 )** |Gibt das Zeichen zurück, das ASCII-Code 65 entspricht |Ein |
| **Char( 105 )** |Gibt das Zeichen zurück, das ASCII-Code 105 entspricht |Ich |
| **Char( 35 )** |Gibt das Zeichen zurück, das ASCII-Code 35 entspricht |"#" |

### <a name="display-a-character-map"></a>Zeichen Zuordnung anzeigen

1. Fügen Sie [**auf einem leeren**](../controls/control-gallery.md) Bildschirm in einer Tablet-App ein Katalog-Steuerelement mit einem **leeren horizontalen** Layout hinzu, und legen Sie dann die folgenden Eigenschaften fest:

    - **Elemente**: `[0,1,2,3,4,5,6,7]`
    - **Breite**: 800
    - **Höhe**: 500
    - **Templatesize**: 100
    - **Templatepadditions**: 0

1. Fügen Sie in diesem Katalog ein Katalog **-Steuerelement mit einem** **leeren vertikalen** Layout hinzu, und legen Sie dann die folgenden Eigenschaften fest:

    - **Elemente**: `ForAll( [0,2,3,4,5,6,7,8,9,10,11,12,13,14,15], Value + ThisItem.Value * 16 )`
    - **Breite**: 100
    - **Höhe**: 500
    - **Templatesize**: 30
    - **Templatepadditions**: 0

    Der Wert der **Items** -Eigenschaft multipliziert 16 mit der Spaltennummer, die von der Value-Spalte der **Items** -Eigenschaft aus der ersten Galerie (0-7 in `ThisItem.Value`) bereitgestellt wird. Die Formel fügt dann das Ergebnis einer der Zeilennummern aus dem zweiten Katalog hinzu (0-15 im Daten Satz Bereich, den die [**ForAll**](function-forall.md) -Funktion bereitstellt).

1. Fügen Sie in der zweiten (vertikalen) Galerie ein **Label** -Steuerelement hinzu, und legen Sie die folgenden Eigenschaften fest:

    - **Text**: `ThisItem.Value`
    - **Breite**: 50

1. Fügen Sie in der zweiten (vertikalen) Galerie ein weiteres **Label** -Steuerelement hinzu, und legen Sie die folgenden Eigenschaften fest:

    - **Text**: `Char( ThisItem.Value )`
    - **Breite**: 50
    - **X**: 50

Sie haben ein Diagramm mit den ersten 128 ASCII-Zeichen erstellt. Zeichen, die als kleines Quadrat angezeigt werden, können nicht gedruckt werden.

![Erste 128 ASCII-Zeichen](media/function-char/chart-lower.png)

Um die erweiterten ASCII-Zeichen anzuzeigen, legen Sie die **Items** -Eigenschaft des zweiten Katalogs auf diese Formel fest. Dadurch wird jedem Zeichen Wert 128 Hinzugefügt:

`ForAll( [0,2,3,4,5,6,7,8,9,10,11,12,13,14,15], Value + ThisItem.Value * 16 + 128)`

![Erweiterte ASCII-Zeichen](media/function-char/chart-higher.png)

Wenn Sie die Zeichen in einer anderen Schriftart anzeigen möchten, legen Sie die Eigenschaft **Schriftart** der zweiten Bezeichnung auf einen Wert wie z. b. **"tanzendes Skript"** fest.

![Tanz Skript](media/function-char/chart-higher-dancing-script.png)
