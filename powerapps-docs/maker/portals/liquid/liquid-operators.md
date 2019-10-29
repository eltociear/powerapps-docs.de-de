---
title: Verwenden von Liquid-Operatoren für ein Portal | MicrosoftDocs
description: Erfahren Sie mehr über die verfügbaren Liquid-Operatoren in einem Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 4a27a5364a4ae12fecc3a72dbb52115e415dcdb8
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976528"
---
# <a name="understand-liquid-operators"></a>Grundlegendes zu Liquid-Operatoren

Liquid hat Zugriff auf alle gängigen logischen und Vergleichs Operatoren. Diese können in Tags verwendet werden, wie **z. b**. **if** und.

## <a name="basic-operators"></a>Grundlegende Operatoren

| ==    | Aufbauen                          |
|-------|---------------------------------|
| !=    | Ist nicht gleich                  |
| &gt;  | Größer als                    |
| &lt;  | Kleiner als                       |
| &gt;= | Größer als oder gleich        |
| &lt;= | Kleiner als oder gleich           |
| oder    | Bedingung a **oder** Bedingung B  |
| immer   | Bedingung a **und** Bedingung B |

## <a name="contains"></a>Inhalt

enthält Tests für das vorhanden sein einer Teil Zeichenfolge innerhalb einer Zeichenfolge.

```
{% if page.title contains 'Product' %}

The title of this page contains the word Product.

{% endif %}
```

enthält auch das vorhanden sein einer Zeichenfolge in einem Zeichen folgen Array.

## <a name="startswith"></a>StartsWith

StartWith testet, ob eine Zeichenfolge mit einer angegebenen Teil Zeichenfolge beginnt.

```
{% if page.title startswith 'Profile' %}

This is a profile page.

{% endif %}
```

## <a name="endswith"></a>EndsWith

EndsWith testet, ob eine Zeichenfolge mit einer angegebenen Teil Zeichenfolge endet.

```
{% if page.title endswith 'Forum' %}

This is a forum page.

{% endif %}
```

### <a name="see-also"></a>Siehe auch

[Speichern von Quell Inhalten mithilfe von Webvorlagen](store-content-web-templates.md)  
[Liquid-Typen](liquid-types.md)  
[Conditional](liquid-conditional-operators.md)  
[Liquid-Objekte](liquid-objects.md)  
[Liquid-Tags](liquid-tags.md)  
[Liquid-Filter](liquid-filters.md) 