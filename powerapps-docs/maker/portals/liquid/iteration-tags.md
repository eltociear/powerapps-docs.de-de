---
title: Verwenden von Iterations Tags für ein Portal | MicrosoftDocs
description: Weitere Informationen zu Iterations Tags, die im Portal verfügbar sind
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 600ddb0ac6e016acf057e592ac638b4e07ddf8ba
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976505"
---
# <a name="iteration-tags"></a>Iterationstags

Iterations Tags werden verwendet, um einen Codeblock wiederholt auszuführen oder zu rendern.

## <a name="for"></a>damit

Führt einen Codeblock wiederholt aus. Es wird am häufigsten verwendet, um die Elemente in einem Array oder Wörterbuch zu durchlaufen.

Im for-tagblock ist das [Schleife-Objekt](liquid-objects.md#forloop) verfügbar.  

**Ordnung**

```
{% for child_page in page.children %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**Ausgeben**

```
<a href=/parent/child1/>Child 1</a>

<a href=/parent/child2/>Child 2</a>

<a href=/parent/child3/>Child 3</a>
```

### <a name="parameters"></a>Metern

Diese Parameter von for können allein oder in Kombination verwendet werden.

**ans**

Beendet die Schleife nach einer angegebenen Anzahl von Elementen.

**Ordnung**

```
{% for child_page in page.children limit:2 %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**Ausgeben**

```
<a href=/parent/child1/>Child 1</a>

<a href=/parent/child2/>Child 2</a>
```

**kompensieren**

Startet die Schleife am angegebenen Index.

**Ordnung**

```
{% for child_page in page.children offset:1 %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**Ausgeben**

```
<a href=/parent/child2/>Child 2</a>

<a href=/parent/child3/>Child 3</a>
```

**Bereich**

Definiert einen Bereich von Zahlen, der durchlaufen werden soll.

**Ordnung**

```
{% assign n = 4 %}

{% for i in (2..n) %}

{{ i }}

{% endfor %}

{% for i in (10..14) %}

{{ i }}

{% endfor }}
```

**Ausgeben**

```
2 3 4

10 11 12 14
```

**gestellt**

Iteriert die Schleife in umgekehrter Reihenfolge, beginnend mit dem letzten Element.

**Ordnung**

```
{% for child_page in page.children reversed %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**Ausgeben**

```
<a href=/parent/child3/>Child 3</a>

<a href=/parent/child2/>Child 2</a>

<a href=/parent/child1/>Child 1</a>
```

## <a name="cycle"></a>Zyklus

Durchläuft eine Gruppe von Zeichen folgen und gibt diese in der Reihenfolge aus, in der Sie als Parameter übermittelt wurden. Jeder Zeit Kreis wird aufgerufen, die nächste als Parameter übergebene Zeichenfolge wird ausgegeben.

**Ordnung**

```
{% for item in items %}

<div class={% cycle 'red', 'green', 'blue' %}> {{ item }} </div>

{% end %}
```

**Ausgeben**

```
<div class=red> Item one </div>

<div class=green> Item two </div>

<div class=blue> Item three </div>

<div class=red> Item four </div>

<div class=green> Item five</div>
```

## <a name="tablerow"></a>TableRow

Generiert eine HTML-Tabelle. Muss in eine öffnende &lt;Tabelle umschlossen werden&gt; und schließt &lt;/Table&gt; HTML-Tags.

Innerhalb des TableRow-tagblocks ist [tablerowloop](liquid-objects.md#tablerowloop) verfügbar.  

**Ordnung**

```
<table>

{% tablerow child_page in page.children %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

**Ausgeben**

```
<table>

<tr class=row1>

<td class=col1>

Child Page 1

</td>

<td class=col2>

Child Page 2

</td>

<td class=col3>

Child Page 3

</td>

<td class=col4>

Child Page 4

</td>

</tr>

</table>
```

### <a name="parameters"></a>Metern

Diese Parameter von tablerowcan können allein oder in Kombination verwendet werden.

**Ausgeben**

```
<table>

<tr class=row1>

<td class=col1>

Child Page 1

</td>

<td class=col2>

Child Page 2

</td>

</tr>

<tr class=row2>

<td class=col3>

Child Page 3

</td>

<td class=col4>

Child Page 4

</td>

</tr>

</table>
```

**Ordnung**

```
<table>

{% tablerow child_page in page.children cols:2 %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

Bestimmt, wie viele Zeilen die generierte Tabelle enthalten sollte.

**cols**

**ans**

Beendet die Schleife nach einer angegebenen Anzahl von Elementen.

**Ordnung**

```
<table>

{% tablerow child_page in page.children limit:2 %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

**Ausgeben**

```
<table>

<tr class=row1>

<td class=col1>

Child Page 1

</td>

<td class=col2>

Child Page 2

</td>

</tr>

</table>

offset
```

Startet die Schleife am angegebenen Index.

**Ordnung**

```
<table>

{% tablerow child_page in page.children offset:2 %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

**Ausgeben**

```
<table>

<tr class=row1>

<td class=col1>

Child Page 3

</td>

<td class=col2>

Child Page 4

</td>

</tr>

</table>
```

**Bereich**

Definiert einen Bereich von Zahlen, der durchlaufen werden soll.

**Ordnung**

```
<table>

{% tablerow i in (1..3) %}

{{ i }}

{% endtablerow %}

</table>
```

### <a name="see-also"></a>Siehe auch

[Ablauf Steuerungs Tags](control-flow-tags.md)
[Variablen Tags](variable-tags.md)
[Vorlagen Tags](template-tags.md)
[powerapps Common Data Service-Entitäts Tags](portals-entity-tags.md)
