---
title: Iterationskennzeichen für ein Portal verwenden | MicrosoftDocs
description: Lesen Sie mehr zu den verschiedenen verfügbaren Vorlage-Tags in einem Portal
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 3240b06c54b24778a8327d403a36902a3b3e0da4
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "2980743"
---
# <a name="iteration-tags"></a>Iterationstags

Iterationstags werden zur wiederholten Ausführung/Rederung eines Codeblocks genutzt.

## <a name="for"></a>für  (möglicherweise in englischer Sprache)

Führt ein Codeblock wiederholt aus. Wir häufig genutzt, um Elemente in einem Array oder Dictionary durchzulaufen.

Innerhalb des Tagblocks ist die [forloop](liquid-objects.md#forloop) verfügbar.  

**Code**

```
{% for child_page in page.children %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**Ausgabe**

```
<a href=/parent/child1/>Child 1</a>

<a href=/parent/child2/>Child 2</a>

<a href=/parent/child3/>Child 3</a>
```

### <a name="parameters"></a>Parameter

Diese Parameter von „for” können allein oder in Kombination verwendet werden.

**limit**

Beendet die Schleife nach der Anzahl der Elemente.

**Code**

```
{% for child_page in page.children limit:2 %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**Ausgabe**

```
<a href=/parent/child1/>Child 1</a>

<a href=/parent/child2/>Child 2</a>
```

**offset**

Startet die Schleife am gegebenen Index.

**Code**

```
{% for child_page in page.children offset:1 %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**Ausgabe**

```
<a href=/parent/child2/>Child 2</a>

<a href=/parent/child3/>Child 3</a>
```

**range**

Definiert einen Nummernbereich für die Schleife.

**Code**

```
{% assign n = 4 %}

{% for i in (2..n) %}

{{ i }}

{% endfor %}

{% for i in (10..14) %}

{{ i }}

{% endfor }}
```

**Ausgabe**

```
2 3 4

10 11 12 14
```

**reversed**

Läuft Schleife in umgekehrter Reihenfolge durch.

**Code**

```
{% for child_page in page.children reversed %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**Ausgabe**

```
<a href=/parent/child3/>Child 3</a>

<a href=/parent/child2/>Child 2</a>

<a href=/parent/child1/>Child 1</a>
```

## <a name="cycle"></a>cycle

Läuft eine Gruppe von Zeichenfolgen durch und gibt sie in der Reihenfolge aus, in der Sie als Parameter übergeben werden. Bei jedem Aufruf von cycle wird die nächste Zeichenfolge zurückgeben.

**Code**

```
{% for item in items %}

<div class={% cycle 'red', 'green', 'blue' %}> {{ item }} </div>

{% end %}
```

**Ausgabe**

```
<div class=red> Item one </div>

<div class=green> Item two </div>

<div class=blue> Item three </div>

<div class=red> Item four </div>

<div class=green> Item five</div>
```

## <a name="tablerow"></a>tablerow

Generiert eine HTML-Tabelle. Muss in öffnende &lt;table&gt;- und schließende &lt;/table&gt;-HTML-Tags eingebunden werden.

Innerhalb des tablerow-Tagblocks ist [tablerowloop](liquid-objects.md#tablerowloop) verfügbar.  

**Code**

```
<table>

{% tablerow child_page in page.children %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

**Ausgabe**

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

### <a name="parameters"></a>Parameter

Diese Parameter von „tablerow” können allein oder in Kombination verwendet werden.

**Ausgabe**

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

**Code**

```
<table>

{% tablerow child_page in page.children cols:2 %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

Legt fest, wie viele Zeilen die Tabelle haben soll.

**cols**

**limit**

Beendet die Schleife nach der Anzahl der Elemente.

**Code**

```
<table>

{% tablerow child_page in page.children limit:2 %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

**Ausgabe**

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

Startet die Schleife am gegebenen Index.

**Code**

```
<table>

{% tablerow child_page in page.children offset:2 %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

**Ausgabe**

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

**range**

Definiert einen Nummernbereich für die Schleife.

**Code**

```
<table>

{% tablerow i in (1..3) %}

{{ i }}

{% endtablerow %}

</table>
```

### <a name="see-also"></a>Siehe auch

[Control flow tags](control-flow-tags.md)
[Variable tags](variable-tags.md)
[Template tags](template-tags.md)
[Power Apps common data service Entität Tags](portals-entity-tags.md)
