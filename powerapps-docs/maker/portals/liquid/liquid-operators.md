---
title: Verwenden von Liquid-Operatoren für ein Portal | MicrosoftDocs
description: Lesen Sie mehr zu den verfügbaren Liquid-Operatoren in einem Portal.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 77561ee8ad31a7c2ab21162edbb08779627d1e65
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "2981183"
---
# <a name="understand-liquid-operators"></a>Lernen Sie Liquid-Operatoren kennen

Liquid hat Zugriff auf alle allgemeinen logischen und Vergleichsoperatoren. Diese können in Tags verwendet werden, z. B. **falls** und **sofern**.

## <a name="basic-operators"></a>Grundlegende Operatoren

| ==    | Gleich                          |
|-------|---------------------------------|
| !=    | ungleich                  |
| &gt;  | Größer als                    |
| &lt;  | Kleiner als                       |
| &gt;= | Größer als oder gleich        |
| &lt;= | Kleiner als oder gleich           |
| oder    | Bedingung A **oder** Bedingung B  |
| und   | Bedingung A **und** Bedingung B |

## <a name="contains"></a>enthält

contains testet die Darstellung einer Teilzeichenfolge innerhalb einer Zeichenfolge.

```
{% if page.title contains 'Product' %}

The title of this page contains the word Product.

{% endif %}
```

contains testet zudem die Darstellung einer Zeichenfolge in einem Zeichenfolgenarray.

## <a name="startswith"></a>startswith

startswith testet, ob eine Zeichenfolge mit einer bestimmten Teilzeichenfolge beginnt.

```
{% if page.title startswith 'Profile' %}

This is a profile page.

{% endif %}
```

## <a name="endswith"></a>endswith

endswith testet, ob eine Zeichenfolge mit einer bestimmten Teilzeichenfolge endet.

```
{% if page.title endswith 'Forum' %}

This is a forum page.

{% endif %}
```

### <a name="see-also"></a>Siehe auch

[Speichern von Inhalten mit Webvorlagen](store-content-web-templates.md)  
[Liquid-Typen](liquid-types.md)  
[Bedingt](liquid-conditional-operators.md)  
[Liquid-Objekte](liquid-objects.md)  
[Liquid-Tags](liquid-tags.md)  
[Liquid-Filter](liquid-filters.md) 