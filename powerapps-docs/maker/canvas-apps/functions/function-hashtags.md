---
title: Funktion „HashTags“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktion "hashtags" in powerapps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a88371e9c151ed097d2c86bcb64121c68a6d62d0
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730789"
---
# <a name="hashtags-function-in-power-apps"></a>Funktion "hashtags" in powerapps
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
1. Fügen Sie ein **[Texteingabe](../controls/control-text-input.md)** -Steuerelement hinzu, benennen Sie dieses **Tweet**, und geben Sie folgenden Satz ein:
   
    **Diese #App ist #TOLL und kann #123zählen oder #123ABC, aber Sie kann nicht #1-23 oder #$\*(#\@“)**
2. Fügen Sie einen vertikalen benutzerdefinierten Katalog hinzu, und legen seine **[Items](../controls/properties-core.md)** -Eigenschaft auf folgende Funktion fest:
   
    **HashTags(Tweet.Text)**
3. Fügen Sie der Katalogvorlage ein **[Label](../controls/control-text-box.md)** -Steuerelement (Bezeichnung) hinzu.
   
    Der Katalog zeigt diese Hashtags:
   
   * **\#App**
   * **\#TOLL**
   * **\#123ZÄHLEN**
   * **\#123ABC**
   * **\#1**

