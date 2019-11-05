---
title: Verwenden von Vorlagen Tags für ein Portal | MicrosoftDocs
description: Weitere Informationen zu Vorlagen Tags, die im Portal verfügbar sind
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 4475e9e2ccc474a6eeb3e7a2e959b360b3250aa8
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543289"
---
# <a name="template-tags"></a>Vorlagentags

Vorlagen Tags steuern die Ausgabe einer Vorlage auf verschiedene Weise und ermöglichen die Kombination mehrerer Vorlagen zu einer einzigen Ausgabe.

## <a name="include"></a>darunter

Schließt den Inhalt einer Vorlage in eine andere Vorlage nach Namen ein. In den powerapps-Portalen ist die Quelle dieser anderen Vorlage in der Regel eine [Webvorlage](store-content-web-templates.md). Dies ermöglicht die Wiederverwendung von allgemeinen Vorlagen Fragmenten an mehreren Stellen.  

Wenn eine Vorlage in eine andere Vorlage eingeschlossen wird, hat die enthaltene Vorlage Zugriff auf alle Variablen, die in der übergeordneten Vorlage definiert sind.

`{% include 'My Template' %}`

Es ist auch möglich, eine beliebige Anzahl benannter Parameter an das include-Tag zu übergeben. Diese werden dann in der enthaltenen Vorlage als Variablen definiert.

`{% include 'My Template' a:x, b:y %}`

## <a name="block"></a>Baustein

Wird in Verbindung mit erweitert verwendet, um Vorlagen Vererbung bereitzustellen. Weitere Informationen finden Sie unter Erweiterungen.

## <a name="extends"></a>Erweitern

Wird in Verbindung mit dem Blocktag verwendet und stellt Vorlagen Vererbung bereit. Dies ermöglicht es mehreren Vorlagen, ein frei gegebenes Layout zu verwenden, während bestimmte Bereiche des übergeordneten Layouts außer Kraft gesetzt werden.

In powerapps-Portalen bezieht sich der Name der übergeordneten Vorlage, die für das-Tag bereitgestellt wird, im Allgemeinen auf den Namen einer [Webvorlage](store-content-web-templates.md).  

Wenn erweitert wird, muss es der erste Inhalt in der Vorlage sein, und nur ein oder mehrere Block Tags können befolgt werden.

Wenn ein Block, der in der übergeordneten Vorlage definiert ist, nicht überschrieben wird, wird sein Inhalt in der übergeordneten Vorlage (sofern vorhanden) gerendert.

## <a name="comment"></a>comment

Ermöglicht es Ihnen, nicht gerenderten Code in einer Liquid-Vorlage zu belassen. Jeglicher Inhalt innerhalb des Blocks wird nicht gerendert, und jeder flüssige Code in wird nicht ausgeführt.

**Ordnung**

`Hello{% comment %}, {{ user.fullname }}{% endcomment %}. My name is Charles.`

**Ausgeben**

`Hello. My name is Charles.`

## <a name="raw"></a>Stoffes

Ermöglicht die Ausgabe von Liquid-Code auf einer Seite, ohne dass Sie analysiert und ausgeführt werden muss.

**Ausgeben**

`Hello, {{ user.fullname }}. My name is Charles.`

### <a name="see-also"></a>Siehe auch

[Ablauf Steuerungs Tags](control-flow-tags.md)<br>
[Iterations Tags](iteration-tags.md)<br>
[Variablen Tags](variable-tags.md)<br>
[Powerapps Common Data Service-Entitäts Tags](portals-entity-tags.md)
