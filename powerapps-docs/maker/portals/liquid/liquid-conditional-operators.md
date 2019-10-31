---
title: Verwenden von Liquid-Operatoren für ein Portal | MicrosoftDocs
description: Lesen Sie mehr zu den verfügbaren bedingten Liquid-Operatoren in einem Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
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
