---
title: Verwenden von flüssigen bedingten Operatoren für ein Portal | MicrosoftDocs
description: Informieren Sie sich über die verfügbaren flüssigen bedingten Operatoren in einem Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: def132ebc0f8ef93121b10b221479a2452a1d4fb
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975010"
---
# <a name="available-liquid-conditional-operators"></a>Verfügbare bedingte Liquid-Operatoren

Bei Verwendung in Bedingungs Anweisungen (**Wenn**,**sofern nicht**), werden einige Liquid-Werte als true behandelt, und einige werden als false behandelt.

In Liquid werden NULL und der boolesche Wert false als false behandelt; alles andere wird als true behandelt. Leere Zeichen folgen, leere Arrays usw. werden als true behandelt. Beispiele:

```
{% assign empty_string =  %}
{% if empty_string %}
<p>This will render.</p>
{% endif %}
```
Wenn erforderlich, können Sie auf leere Zeichen folgen und Arrays mit dem Wert Empty testen.

```
{% unless page.title == empty %}
<h1>{{ page.title }}</h1>
{% endunless %}
```
Sie können auch die Größe von [Liquid-Typen](liquid-types.md), [Liquid-Typen](liquid-types.md)oder [Liquid-Typen](liquid-types.md) mithilfe der Eigenschaft besondere Größe testen.

```
{% if page.children.size > 0 %}
<ul>
{% for child in page.children %}
<li>{{ child.title }}</li>
{% endfor %}
</ul>
{% endif %}
```

## <a name="summary"></a>FAS

|                           | True | Alarm |
|---------------------------|------|-------|
| True                      | ×    |       |
| Alarm                     |      | ×     |
| Normal                      |      | ×     |
| Zeichenfolge                    | ×    |       |
| Leere Zeichenfolge              | ×    |       |
| 0                         | ×    |       |
| 1, 3,14                   | ×    |       |
| Array oder Wörterbuch       | ×    |       |
| leeres Array oder Wörterbuch | ×    |       |
| Objekt                    | ×    |       |

### <a name="see-also"></a>Siehe auch

[Speichern von Quell Inhalten mithilfe von Webvorlagen](store-content-web-templates.md)  
[Grundlegendes zu Liquid](liquid-operators.md)  
[Liquid-Typen](liquid-types.md)  
[Liquid-Objekte](liquid-objects.md)  
[Liquid-Tags](liquid-tags.md)  
[Liquid-Filter](liquid-filters.md)  
