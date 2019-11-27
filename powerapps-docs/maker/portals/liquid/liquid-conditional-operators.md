---
title: Verwenden von bedingten Liquid-Operatoren für ein Portal | MicrosoftDocs
description: Lesen Sie mehr zu den verfügbaren bedingten Liquid-Operatoren in einem Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: def132ebc0f8ef93121b10b221479a2452a1d4fb
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2708261"
---
# <a name="available-liquid-conditional-operators"></a>Verfügbare bedingte Liquid-Operatoren

Wenn sie in den Bedingungsanweisungen (**if**, **unless**) verwendet werden, werden einige Liquid-Werte als "true" und andere als "false" angesehen.

In Liquid werden Null und der boolesche Wert als „false“ behandelt, alles andere als „true“. Leere Zeichenfolgen, leere Arrays usw. werden als "true" behandelt. Zum Beispiel,

```
{% assign empty_string =  %}
{% if empty_string %}
<p>This will render.</p>
{% endif %}
```
Sie können leere Zeichenfolgen und Arrays mithilfe des speziellen Wertes "empty" testen, falls erforderlich.

```
{% unless page.title == empty %}
<h1>{{ page.title }}</h1>
{% endunless %}
```
Sie können auch die Größe von [Liquid-Typen](liquid-types.md), [Liquid-Typen](liquid-types.md) oder [Liquid-Typen](liquid-types.md) mit der speziellen Größeneigenschaft testen.

```
{% if page.children.size > 0 %}
<ul>
{% for child in page.children %}
<li>{{ child.title }}</li>
{% endfor %}
</ul>
{% endif %}
```

## <a name="summary"></a>Inhaltsübersicht

|                           | Wahr | Falsch |
|---------------------------|------|-------|
| Wahr                      | ×    |       |
| Falsch                     |      | ×     |
| Null                      |      | ×     |
| Zeichenfolge                    | ×    |       |
| Leere Zeichenfolge              | ×    |       |
| 0                         | ×    |       |
| 1, 3,14                   | ×    |       |
| Array oder Wörterbuch       | ×    |       |
| Leeres Array oder Wörterbuch | ×    |       |
| Objekt                    | ×    |       |

### <a name="see-also"></a>Siehe auch

[Speichern von Inhalten mit Webvorlagen](store-content-web-templates.md)  
[Lernen Sie Liquid-Operatoren kennen](liquid-operators.md)  
[Liquid-Typen](liquid-types.md)  
[Liquid-Objekte](liquid-objects.md)  
[Liquid-Tags](liquid-tags.md)  
[Liquid-Filter](liquid-filters.md)  
