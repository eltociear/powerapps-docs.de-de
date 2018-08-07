---
title: Funktion „HashTags“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Funktion „HashTags“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: c2b4cff0cc9d579cd76dad97a3ab1b160f4089ea
ms.sourcegitcommit: 0f6d7bb9e524202c065b9a7ef92a7f54bdc4bc7c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2018
ms.locfileid: "39022054"
---
# <a name="hashtags-function-in-powerapps"></a>Funktion „HashTags“ in PowerApps
Extrahiert die Hashtags (#strings) aus einer Textzeichenfolge.

## <a name="description"></a>Beschreibung
Die **HashTags**-Funktion durchsucht eine Zeichenfolge nach Hashtags. Hashtags beginnen mit einem Hashtag (#), das von eine beliebige Kombination aus Folgendem gefolgt wird:

* Groß-und Kleinbuchstaben
* Zahlen
* Unterstriche
* Währungszeichen (z.B. $)

**HashTags** gibt eine einspaltige [Tabelle](../working-with-tables.md) zurück, die die Hashtags in der Zeichenfolge enthält.  Wenn die Zeichenfolge keine Hashtags enthält, gibt die Funktion eine Tabelle mit einer Spalte zurück, die [empty](function-isblank-isempty.md) ist.

## <a name="syntax"></a>Syntax
**HashTags**( *String* )

* *Zeichenfolge*: erforderlich.  Die Zeichenfolge zum Suchen der Hashtags

## <a name="examples"></a>Beispiele
### <a name="step-by-step"></a>Schritt für Schritt
1. Fügen Sie ein **[Texteingabe](../controls/control-text-input.md)**-Steuerelement hinzu, benennen Sie dieses **Tweet**, und geben Sie folgenden Satz ein:
   
    **Diese #App ist #TOLL und kann #123zählen oder #123ABC, aber Sie kann nicht #1-23 oder #$\*(#@“)**
2. Fügen Sie einen vertikalen benutzerdefinierten Katalog hinzu, und legen seine **[Items](../controls/properties-core.md)**-Eigenschaft auf folgende Funktion fest:
   
    **HashTags(Tweet.Text)**
3. Fügen Sie der Katalogvorlage ein **[Label](../controls/control-text-box.md)**-Steuerelement (Bezeichnung) hinzu.
   
    Der Katalog zeigt diese Hashtags:
   
   * **\#App**
   * **\#TOLL**
   * **\#123ZÄHLEN**
   * **\#123ABC**
   * **\#1**

