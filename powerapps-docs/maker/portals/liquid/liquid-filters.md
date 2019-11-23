---
title: Verwenden von Liquid-Filtern für ein Portal | MicrosoftDocs
description: Erfahren Sie mehr über die verfügbaren Liquid-Filter in einem Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 996b31766641376e9a01cbefc876f3eb2b7aabc7
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543237"
---
# <a name="available-liquid-filters"></a>Verfügbare Liquid-Filter

Liquid-Filter werden verwendet, um die Ausgabe von Zeichen folgen, Zahlen, Variablen und Objekten zu ändern. Sie sind von dem Wert getrennt, auf den Sie angewendet werden.

`{{ 'hal 9000' | upcase }} <!-- Output: HAL 9000 -->`

Einige Filter akzeptieren Parameter. Filter können auch kombiniert werden und werden in der Reihenfolge von links nach rechts angewendet.

```
{{ 2 | times: 2 | minus: 1 }} <!-- Output: 3 -->

{{ "Hello, " | append: user.firstname }} <!-- Output: Hello, Dave -->
```
Im folgenden Abschnitt werden verschiedene Filter beschrieben. 

## <a name="array-filters"></a>Array Filter

Array Filter werden verwendet, um mit [Arrays](liquid-types.md#array)zu arbeiten.  

### <a name="batch"></a>Batches

Dividiert ein Array in mehrere Arrays einer angegebenen Größe.

**Ordnung**

```
{% assign batches = entityview.records | batch: 2 %}

{% for batch in batches %}

<ul>

{% for item in batch %}

<li>{{ item.fullname }}</li>

{% endfor %}

</ul>

{% endfor %}
```

**Ausgeben**

```
<ul>

<li>John Smith</li>

<li>Dave Thomas</li>

</ul>

<ul>

<li>Jake Johnson</li>

<li>Jack Robinson</li>

</ul>
```

### <a name="concat"></a>Concat

Verkettet zwei Arrays zu einem einzelnen neuen Array.

Wenn ein einzelnes Element als Parameter angegeben wird, gibt Concat ein neues Array zurück, das aus dem ursprünglichen Array besteht, wobei das angegebene Element als letztes Element angegeben ist.

**Ordnung**

```
Group #1: {{ group1 | join: ', ' }}

Group #2: {{ group2 | join: ', ' }}

Group #1 + Group #2: {{ group1 | concat: group2 | join: ', ' }}

Group #1 + Leslie: {{ group1 | concat: 'Leslie' | join: ', ' }}
```

**Ausgeben**

```
Group #1: John, Pete, Hannah

Group #2: Joan, Bill

Group #1 + Group #2: John, Pete, Hannah, Joan, Bill

Group #1 + Leslie: John, Pete, Hannah, Leslie
```

### <a name="except"></a>davon

Wählen Sie alle Objekte in einem Array aus, bei denen ein bestimmtes Attribut nicht über einen angegebenen Wert verfügt. (Dies ist die Umkehrung von**Where**.)

**Ordnung**

```
{% assign redmond = entityview.records | except: 'address1_city', 'Redmond' %}

{% for item in redmond %}

{{ item.fullname }}

{% endfor %}
```

**Ausgeben**

```
Jack Robinson
```

### <a name="first"></a>erstes

Gibt das erste Element eines Arrays zurück.

zuerst kann auch mit einer speziellen Punkt Notation verwendet werden, in Fällen, in denen Sie innerhalb eines Tags verwendet werden muss.

**Ordnung**

```
{% assign words = This is a run of text | split:   %}

{{ words | first }}

{% if words.first == This %}

The first word is This.

{% endif %}
```

**Ausgeben**

```
This

The first word is This.
```

### <a name="group_by"></a>group_by

Gruppieren Sie die Elemente in einem Array nach einem angegebenen Attribut.

**Ordnung**

```
{% assign groups = entityview.records | group_by: 'address1_city' %}

{% for group in groups %}

{{ group.key }}:

{% for item in group.items %}

{{ item.fullname }}

{% endfor %}

{% endfor %}
```

**Ausgeben**

```
Redmond:

John Smith

Dave Thomas

Jake Johnson

New York:

Jack Robinson
```

### <a name="join"></a>Join

Fügt die Elemente eines Arrays mit dem Zeichen an, das als-Parameter übergeben wird. Das Ergebnis ist eine einzelne Zeichenfolge.

**Ordnung**

```
{% assign words = This is a run of text | split:   %}

{{ words | join: ,  }}
```

**Ausgeben**

```
This, is, a, run, of, text
```

### <a name="last"></a>letzten

Gibt das letzte Element eines Arrays zurück.

Last kann auch mit einer speziellen Punkt Notation verwendet werden, in Fällen, in denen Sie innerhalb eines Tags verwendet werden muss.

**Ordnung**

```
{% assign words = This is a run of text | split:   -%}

{{ words | last }}

{% if words.last == text -%}

The last word is text.

{% endif -%}
```

**Ausgeben**

```
text

The last word is text.
```

### <a name="order_by"></a>Bestell\_nach

Gibt die Elemente eines Arrays zurück, geordnet nach einem angegebenen Attribut der Elemente des Arrays.

Optional können Sie als zweiten Parameter als zweiten Parameter angeben, um die Elemente in absteigender Reihenfolge und nicht aufsteigend zu sortieren.

**Ordnung**

```
{{ entityview.records | order_by: 'fullname' | join: ', ' }}

{{ entityview.records | order_by: 'fullname', 'desc' | join: ', ' }}
```

**Ausgeben**

```
Dave Thomas, Jack Robinson, Jake Johnson, John Smith

John Smith, Jake Johnson, Jack Robinson, Dave Thomas
```

### <a name="random"></a>erfolgen

Gibt ein einzelnes nach dem Zufallsprinzip ausgewähltes Element aus dem Array zurück.

**Ordnung**

```
{{ group1 | join: ', ' }}

{{ group1 | random }}
```

**Ausgeben**

```
John, Pete, Hannah

Pete
```

### <a name="select"></a>Auswahl

Wählt den Wert eines angegebenen Attributs für jedes Element in einem Array aus und gibt diese Werte als Array zurück.

**Ordnung**

```
{{ entityview.records | select: 'address1_city' | join: ', ' }}
```

**Ausgeben**

```
Redmond, New York
```

### <a name="shuffle"></a>Gedicht

Wird auf ein Array angewendet und gibt ein neues Array mit denselben Elementen in zufällisierter Reihenfolge zurück.

**Ordnung**

```
{{ group1 | join: ', ' }}

{{ group1 | shuffle | join: ', ' }}
```

**Ausgeben**

```
John, Pete, Hannah

Hannah, John, Pete
```

### <a name="size"></a>Größe

Gibt die Anzahl der Elemente in einem Array zurück.

die Größe kann auch mit einer speziellen Punkt Notation verwendet werden, in Fällen, in denen Sie innerhalb eines Tags verwendet werden muss.

**Ordnung**

```
{% assign words = This is a run of text | split:   -%}

{{ words | size }}

{% if words.size == 6 -%}

The text contains 6 words.

{% endif -%}
```

**Ausgeben**

```
6

The text contains 6 words.
```

### <a name="skip"></a>skip

Überspringt eine angegebene Anzahl von Elementen in einem Array und gibt den Rest zurück.

**Ordnung**

```
{% assign words = This is a run of text | split:   %}

{{ words | skip: 3 | join: ', ' }}
```

**Ausgeben**

```
run, of, text
```

### <a name="take"></a>Rechnung

Nimmt eine angegebene Anzahl von Elementen aus dem Array und gibt die Elemente zurück, die entnommen wurden.

**Ordnung**

```
{% assign words = This is a run of text | split:   %}

{{ words | take: 3 | join: ', ' }}
```
**Ausgeben**

```

This, is, a
```

### <a name="then_by"></a>dann\_

Fügt einem Array, das bereits nach der**Reihenfolge\_** geordnet ist, zusätzliche Reihenfolge hinzu.

Optional können Sie als zweiten Parameter als zweiten Parameter angeben, um die Elemente in absteigender Reihenfolge und nicht aufsteigend zu sortieren.

**Ordnung**

```
{{ entityview.records | order_by: 'address1_city' | then_by: 'fullname' | join: ', ' }}

{{ entityview.records | order_by: 'address1_city' | then_by: 'fullname', 'desc' | join: ', ' }}
```

**Ausgeben**

```
Dave Thomas, Jack Robinson, Jake Johnson, John Smith

John Smith, Jake Johnson, Jack Robinson, Dave Thomas
```

### <a name="where"></a>Was

Wählen Sie alle Objekte in einem Array aus, bei denen ein bestimmtes Attribut über einen angegebenen Wert verfügt.

**Ordnung**

```
{% assign redmond = entityview.records | where: 'address1_city', 'Redmond' %}

{% for item in redmond %}

{{ item.fullname }}

{% endfor %}
```

**Ausgeben**

```
John Smith

Dave Thomas

Jake Johnson
```


## <a name="date-filters"></a>Datumsfilter

Datumsfilter können für Datums Arithmetik oder zum Konvertieren von DateTime-Werten in verschiedene Formate verwendet werden.

### <a name="date"></a>Datum

Formatiert einen DateTime-Wert mithilfe einer .NET-Format Zeichenfolge.

[Standard Format Zeichenfolgen für Datum und Uhrzeit](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)  

[Benutzerdefinierte Format Zeichenfolgen für Datum und Uhrzeit](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings)  

**Ordnung**

```
{{ now | date: 'g' }}

{{ now | date: 'MMMM dd, yyyy' }}
```

**Ausgeben**

```
5/7/2018 7:20 AM

May 07, 2018
```

### <a name="date_add_days"></a>Datums\_\_Tage hinzufügen

Fügt dem DateTime-Wert die angegebene Anzahl von ganzen Tagen und Bruchteilen von Tagen hinzu. Der-Parameter kann positiv oder negativ sein.

**Ordnung**

```
{{ now }}

{{ now | date_add_days: 1 }}

{{ now | date_add_days: -2.5 }}
```

**Ausgeben**

```
5/7/2018 7:20:46 AM

5/8/2018 7:20:46 AM

5/4/2018 7:20:46 PM
```

### <a name="date_add_hours"></a>\_Stunden\_hinzufügen

Fügt dem DateTime-Wert die angegebene Anzahl von ganzen Stunden und Bruchteilen von Stunden hinzu. Der-Parameter kann positiv oder negativ sein.

**Ordnung**

```
{{ now }}

{{ now | date_add_hours: 1 }}

{{ now | date_add_hours: -2.5 }}
```

**Ausgeben**

```
5/7/2018 7:20:46 AM

5/7/2018 8:20:46 AM

5/7/2018 4:50:46 AM
```

### <a name="date_add_minutes"></a>\_\_Minuten hinzufügen

Fügt dem DateTime-Wert die angegebene Anzahl von ganzen Minuten und Bruchteilen von Minuten hinzu. Der-Parameter kann positiv oder negativ sein.

**Ordnung**

```
{{ now }}

{{ now | date_add_minutes: 10 }}

{{ now | date_add_minutes: -2.5 }}
```


**Ausgeben**

```
5/7/2018 7:20:46 AM

5/7/2018 7:30:46 AM

5/7/2018 7:18:16 AM
```

### <a name="date_add_months"></a>\_\_Monate hinzufügen

Fügt dem DateTime-Wert die angegebene Anzahl ganzer Monate hinzu. Der-Parameter kann positiv oder negativ sein.

**Ordnung**

```
{{ now }}

{{ now | date_add_months: 1 }}

{{ now | date_add_months: -2 }}
```

**Ausgeben**

```
5/7/2018 7:20:46 AM

6/7/2018 7:20:46 AM

3/7/2018 7:20:46 AM
```

### <a name="date_add_seconds"></a>\_\_Sekunden hinzufügen

Fügt dem DateTime-Wert die angegebene Anzahl von ganzen Sekunden und Bruchteilen von Sekunden hinzu. Der-Parameter kann positiv oder negativ sein.

**Ordnung**

```
{{ now }}

{{ now | date_add_seconds: 10 }}

{{ now | date_add_seconds: -1.25 }}
```

**Ausgeben**

```
5/7/2018 7:20:46 AM

5/7/2018 7:20:56 AM

5/7/2018 7:20:45 AM
```

### <a name="date_add_years"></a>\_Hinzufügen von\_Jahren

Fügt dem DateTime-Wert die angegebene Anzahl ganzer Jahre hinzu. Der-Parameter kann positiv oder negativ sein.

**Ordnung**

```
{{ now }}

{{ now | date_add_years: 1 }}

{{ now | date_add_years: -2 }}
```

**Ausgeben**

```
5/7/2018 7:20:46 AM

5/7/2019 7:20:46 AM

5/7/2016 7:20:46 AM
```

### <a name="date_to_iso8601"></a>Datums\_\_ISO8601

Formatiert einen DateTime-Wert gemäß dem [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) -Standard. Nützlich, wenn [*Atom-Feeds*](https://tools.ietf.org/html/rfc4287)oder das HTML5-&lt;Time&gt;-Element erstellt werden.  

**Ordnung**

```
{{ now | date_to_iso8601 }}
```

**Ausgeben**

```
2018-05-07T07:20:46Z
```

### <a name="date_to_rfc822"></a>Datums\_\_RFC822

Formatiert einen DateTime-Wert gemäß dem [RFC 822](https://www.ietf.org/rfc/rfc0822.txt) -Standard. Nützlich beim Erstellen von [*RSS-Feeds*](https://cyber.law.harvard.edu/rss/rss.html).  

**Ordnung**

```
{{ now | date_to_rfc822 }}
```

**Ausgeben**

```
Mon, 07 May 2018 07:20:46 Z
```


## <a name="entity-list-filters"></a>Filter für Entitäts Listen

Mithilfe von Entitäts Listen Filtern werden bestimmte [entityList](liquid-objects.md#entitylist) -Attributwerte verwendet und Entitäts Listen Sichten erstellt.  

### <a name="current_sort"></a>aktuelle\_Sortierung

Gibt bei Angabe eines Sortier Ausdrucks die aktuelle Sortierreihenfolge für ein bestimmtes Attribut zurück.

**Ordnung**

```
{{ 'name ASC, createdon DESC' | current_sort: 'createdon' }}
```

**Ausgeben**

```
DESC
```

### <a name="metafilters"></a>MetaFilter

Analysiert einen [entityList](liquid-objects.md#entitylist) -Filter\_JSON-Definitions Wert in Filteroption Group-Objekte.  

MetaFilter können optional mit einer aktuellen Attribut Filter Abfrage und der aktuellen [entityList](liquid-objects.md#entitylist)bereitgestellt werden, sodass die zurückgegebenen Filter Objekte entweder als ausgewählt oder nicht ausgewählt gekennzeichnet werden können.

**Ordnung**

```
{% assign filters = entitylist | metafilters: params.mf, entityview %}
{% if filters.size > 0 %}
  <ul id=entitylist-filters>
    {% for filter in filters %}
      <li class=entitylist-filter-option-group>
        {% if filter.selection_mode == 'Single' %}
          {% assign type = 'radio' %}
        {% else %}
          {% assign type = 'checkbox' %}
        {% endif %}
        <h4 class=entitylist-filter-option-group-label
          data-filter-id={{ filter.id | h }}>
          {{ filter.label | h }}
        </h4>
        <ul>
          {% for option in filter.options %}
            <li class=entitylist-filter-option>
              {% if option.type == 'text' %}
                <div class=input-group entitylist-filter-option-text>
                  <span class=input-group-addon>
                    <span class=fa fa-filter aria-hidden=true></span>
                  </span>
                  <input class=form-control
                    type=text
                    name={{ filter.id | h }}
                    value={{ option.text | h }} />
                </div>
              {% else %}
                <div class={{ type | h }}>
                  <label>
                    <input
                      type={{ type | h }}
                      name={{ filter.id | h }}
                      value={{ option.id | h }}
                      {% if option.checked %}
                        checked=checked
                        data-checked=true{% endif %}
                      />
                    {{ option.label | h }}
                  </label>
                </div>
              {% endif %}
            </li>
          {% endfor %}
        </ul>
      </li>
    {% endfor %}
  </ul>
  <button class=btn btn-default data-serialized-query=mf data-target=#entitylist-filters>Apply Filters</button>
{% endif %}
```

### <a name="reverse_sort"></a>\_Sortierung umkehren

Gibt bei einer Sortierrichtung die umgekehrte Sortierreihenfolge zurück.

**Ordnung**

```
<!-- Sort direction is not case-sensitive -->

{{ 'ASC' | reverse_sort }}

{{ 'desc' | reverse_sort }}
```

**Ausgeben**

```
DESC

ASC
```


## <a name="math-filters"></a>Mathematische Filter

Mathematische Filter ermöglichen es Ihnen, mathematische Vorgänge für [Zahlen](liquid-types.md#number)auszuführen.  

Wie bei allen Filtern können mathematische Filter verkettet werden und werden in der Reihenfolge von links nach rechts angewendet.

**Ordnung**

```
{{ 10 | times: 2 | minus: 5 | divided_by: 3 }}
```

**Ausgeben**

```
5
```

### <a name="ceil"></a>ceil

Rundet einen Wert auf die nächste ganze Zahl.

**Ordnung**

```
{{ 4.6 | ceil }}

{{ 4.3 | ceil }}
```

**Ausgeben**

```
5

5
```

### <a name="divided_by"></a>dividiert durch\_

Dividiert eine Zahl durch eine andere Zahl.

**Ordnung**

```
{{ 10 | divided_by: 2 }}

{{ 10 | divided_by: 3 }}

{{ 10.0 | divided_by: 3 }}
```

**Ausgeben**

```
5

3

3.333333
```

### <a name="floor"></a>Steh

Rundet einen Wert auf die nächste ganze Zahl ab.

**Ordnung**

```
{{ 4.6 | floor }}

{{ 4.3 | floor }}
```

**Ausgeben**

```
4

4
```

### <a name="minus"></a>Kurs

Subtrahiert eine Zahl von einer anderen Zahl.

**Ordnung**

```
<!-- entityview.page = 11 -->

{{ entityview.page | minus: 1 }}

{{ 10 | minus: 1.1 }}

{{ 10.1 | minus: 1 }}
```

**Ausgeben**

```
10

9

9.1
```

### <a name="modulo"></a>Modulo

Dividiert eine Zahl durch eine andere Zahl und gibt den Rest zurück.

**Ordnung**

```
{{ 12 | modulo: 5 }}
```

**Ausgeben**

```
2
```

### <a name="plus"></a>Plus

Fügt einer anderen Zahl eine Zahl hinzu.

**Ordnung**

```
<!-- entityview.page = 11 -->

{{ entityview.page | plus: 1 }}

{{ 10 | plus: 1.1 }}

{{ 10.1 | plus: 1 }}
```

**Ausgeben**

```
12

11

11.1
```

### <a name="round"></a>umgekehrt

Rundet einen Wert auf die nächste ganze Zahl oder die angegebene Anzahl von Dezimalstellen.

**Ordnung**

```
{{ 4.6 | round }}

{{ 4.3 | round }}

{{ 4.5612 | round: 2 }}
```

**Ausgeben**

```
5

4

4.56
```

### <a name="times"></a>Vielfaches

Multipliziert eine Zahl mit einer anderen Zahl.

**Ordnung**

```
{{ 10 | times: 2 }}

{{ 10 | times: 2.2 }}

{{ 10.1 | times: 2 }}
```

**Ausgeben**

```
20

20

20.2
```


## <a name="string-filters"></a>Zeichen folgen Filter

Zeichen folgen Filter [Bearbeiten Zeichen](liquid-types.md#string)folgen.  

### <a name="append"></a>Anfügen

Fügt eine Zeichenfolge an das Ende einer anderen Zeichenfolge an.

**Ordnung**

```
{{ 'filename' | append: '.js' }}
```

**Ausgeben**

```
filename.js
```

### <a name="capitalize"></a>**profitieren**

schreibt das erste Wort in eine Zeichenfolge ein.

**Ordnung**

```
{{ 'capitalize me' | capitalize }}
```

**Ausgeben**

```
Capitalize Me
```

### <a name="downcase"></a>**downcase**

Konvertiert eine Zeichenfolge in Kleinbuchstaben.

**Ordnung**

```
{{ 'MIxed Case TExt' | downcase }}
```

**Ausgeben**

```
mixed case text
```

### <a name="escape"></a>**Weg**

HTML: Escapezeichen für eine Zeichenfolge.

**Ordnung**

```
{{ '<p>test</p>' | escape }}
```

**Ausgeben**

```
&lt;p&gt;test&lt;/p&gt;
```

### <a name="newline_to_br"></a>**Zeilen\_zu\_BR**

Fügt bei jedem Zeilenumbruch in einer Zeichenfolge ein &lt;BR/&gt; Zeilenumbruch-HTML-Tag ein.

**Ordnung**

```
{% capture text %}

A

B

C

{% endcapture %}

{{ text | newline_to_br }}
```

**Ausgeben**

```
A<br />

B<br />

C<br />
```

### <a name="prepend"></a>**voranstellen**

Fügt eine Zeichenfolge am Anfang einer anderen Zeichenfolge voran.

**Ordnung**

```
{{ 'Jane Johnson' | prepend: 'Dr. ' }}
```

**Ausgeben**

```
Dr. Jane Johnson
```

### <a name="remove"></a>**aufgeh**

Entfernt alle Vorkommen einer Teil Zeichenfolge aus einer Zeichenfolge.

**Ordnung**

```
{{ 'Hello, Dave. How are you, Dave?' | remove: 'Dave' }}
```

**Ausgeben**

```
Hello, . How are you, ?
```

### <a name="remove_first"></a>**\_zuerst entfernen**

Entfernt das erste Vorkommen einer Teil Zeichenfolge aus einer Zeichenfolge.

**Ordnung**

```
{{ 'Hello, Dave. How are you, Dave?' | remove_first: 'Dave' }}
```

**Ausgeben**

```
Hello, . How are you, Dave?
```

### <a name="replace"></a>**Stelle**

Ersetzt alle Vorkommen einer Zeichenfolge durch eine Teil Zeichenfolge.

**Ordnung**

```
{{ 'Hello, Dave. How are you, Dave?' | replace: 'Dave', 'John' }}
```

**Ausgeben**

```
Hello, John. How are you, John?
```

### <a name="replace_first"></a>**zuerst\_ersetzen**

Ersetzt das erste Vorkommen einer Zeichenfolge durch eine Teil Zeichenfolge.

**Ordnung**

```
{{ 'Hello, Dave. How are you, Dave?' | replace_first: 'Dave', 'John' }}
```

**Ausgeben**

```
Hello, John. How are you, Dave?
```

### <a name="split"></a>**getrennt**

Der Split-Filter nimmt eine Teil Zeichenfolge als Parameter an. Die Teil Zeichenfolge wird als Trennzeichen verwendet, um eine Zeichenfolge in ein Array aufzuteilen.

**Ordnung**

```
{% assign words = This is a demo of the split filter | split: ' ' %}

First word: {{ words.first }}

First word: {{ words[0] }}

Second word: {{ words[1] }}

Last word: {{ words.last }}

All words: {{ words | join: ', ' }}
```

**Ausgeben**

```
First word: This

First word: This

Second word: is

Last word: filter

All words: This, is, a, demo, of, the, split, filter
```

### <a name="strip_html"></a>**\_HTML entfernen**

Entfernt alle HTML-Tags aus einer Zeichenfolge.

**Ordnung**

```
<p>Hello</p>
```

**Ausgeben**

```
Hello
```

### <a name="strip_newlines"></a>**\_Zeilen Streifen entfernen**

Entfernt alle Zeilenumbrüche von einer Zeichenfolge.

**Ordnung**

```
{% capture text %}

A

B

C

{% endcapture %}

{{ text | strip_newlines }}
```

**Ausgeben**

```
ABC
```

### <a name="text_to_html"></a>**\_HTML-\_Text**

Formatiert eine einfache Text Zeichenfolge als einfaches HTML. Der gesamte Text wird HTML-codiert, Textblöcke, die durch eine leere Zeile getrennt sind, werden in Absatz &lt;p&gt; Tags umschließt, einzelne Zeilenumbrüche werden durch &lt;BR-&gt;ersetzt, und URLs werden in Hyperlinks konvertiert.

**Ordnung**

```
{{ note.notetext | text_to_html }}
```

**Ausgeben**

```
<p>This is the first paragraph of notetext. It contains a URL: <a href="https://example.com/" rel="nofollow">https://example.com</a></p>

<p>This is a second paragraph.</p>
```

### <a name="truncate"></a>**TRUNCATE**

Verkürzt eine Zeichenfolge auf eine angegebene Anzahl von Zeichen. Eine Ellipse (...) wird an die Zeichenfolge angefügt und ist in der Zeichen Anzahl enthalten.

**Ordnung**

```
{{ 'This is a long run of text.' | truncate: 10 }}
```

**Ausgeben**

```
This is...
```

### <a name="truncate_words"></a>**\_Wörter Abschneiden**

Verkürzt eine Zeichenfolge auf eine angegebene Anzahl von Wörtern. An die abgeschnittene Zeichenfolge wird eine Ellipse (...) angehängt.

**Ordnung**

```
{{ 'This is a long run of text.' | truncate_words: 3 }}
```

**Ausgeben**

```
This is a...
```

### <a name="upcase"></a>**upcase**

Konvertiert eine Zeichenfolge in einen Großbuchstaben.

**Ordnung**

```
{{ 'MIxed Case TExt' | upcase }}
```

**Ausgeben**

```
MIXED CASE TEXT
```

### <a name="url_escape"></a>**URL\_Escapezeichen**

URI: Escapezeichen für eine Zeichenfolge, um Sie in eine URL einzubeziehen.

**Ordnung**

```
{{ 'This & that//' | url_escape }}
```

**Ausgeben**

```
This+%26+that%2F%2F
```

### <a name="xml_escape"></a>**XML-\_Escape**

XML: Escapezeichen für eine Zeichenfolge, um Sie in die XML-Ausgabe einzubeziehen

**Ordnung**

```
{{ '<p>test</p>' | xml_escape }}
```

**Ausgeben**

```
&lt;p&gt;test&lt;/p&gt;
```


## <a name="type-filters"></a>Typfilter

Mit typfiltern können Sie Werte eines Typs in andere Typen konvertieren.

### <a name="boolean"></a>**booleschen**

Versucht, einen Zeichen folgen Wert in einen booleschen Wert zu konvertieren. Wenn der Wert bereits ein boolescher Wert ist, wird er unverändert zurückgegeben. Wenn der Wert nicht in einen booleschen Wert konvertiert werden kann, wird NULL zurückgegeben.

Dieser Filter akzeptiert auch on, aktiviert oder yes als true, Off, deaktiviert und Nein als false.

**Ordnung**

```
{{ true | boolean }}

{{ 'false' | boolean }}

{{ 'enabled' | boolean }}

{{ settings['something/enabled'] | boolean | default: false }}
```

**Ausgeben**

```
true

false

true

false
```

### <a name="decimal"></a>**mierte**

Versucht, einen Zeichen folgen Wert in eine Dezimalzahl zu konvertieren. Wenn der Wert bereits eine Dezimalzahl ist, wird er unverändert zurückgegeben. Wenn der Wert nicht in eine Dezimalzahl konvertiert werden kann, wird NULL zurückgegeben.

**Ordnung**

```
{{ 10.1 | decimal }}

{{ '3.14' | decimal }}

{{ 'text' | decimal | default: 3.14 }}
```

**Ausgeben**

```
10.1

3.14

3.14
```

### <a name="integer"></a>**Zah**

Versucht, einen Zeichen folgen Wert in eine ganze Zahl zu konvertieren. Wenn der Wert bereits eine ganze Zahl ist, wird er unverändert zurückgegeben. Wenn der Wert nicht in eine ganze Zahl konvertiert werden kann, wird NULL zurückgegeben.

**Ordnung**

```
{{ 10 | integer }}

{{ '10' | integer }}

{{ '10.1' | integer }}

{{ 'text' | integer | default: 2 }}
```

**Ausgeben**

```
10

10


2
```

### <a name="string"></a>**Schnür**

Versucht, einen Wert in seine Zeichen folgen Darstellung zu konvertieren. Wenn der Wert bereits eine Zeichenfolge ist, wird er unverändert zurückgegeben. Wenn der Wert NULL ist, wird NULL zurückgegeben.



## <a name="url-filters"></a>URL-Filter

Mit URL-Filtern können Sie Teile von URLs erstellen oder extrahieren.

### <a name="add_query"></a>**\_Abfrage hinzufügen**

Fügt einen Abfrage Zeichenfolgen-Parameter an eine URL an. Wenn der Parameter bereits in der URL vorhanden ist, wird der Parameterwert aktualisiert.

Wenn dieser Filter auf eine vollständige absolute URL angewendet wird, ist das Ergebnis eine aktualisierte absolute URL. Wenn Sie auf einen Pfad angewendet wird, ist das Ergebnis ein aktualisierter Pfad.

**Ordnung**

```
{{ 'https://example.com/path?page=1' | add_query: 'foo', 'bar' }}

{{ '/path?page=1' | add_query: 'page', 2 }}
```

**Ausgeben**

```
https://example.com/path?page=1&foo=bar

/path?page=2
```

### <a name="base"></a>**sock**

Ruft die Basis-URL einer gegebenen URL ab.

**Ordnung**

```
{{ 'https://example.com/path?foo=bar&page=2' | base }}
```

**Ausgeben**

```
https://example.com
```

### <a name="host"></a>**Host**

Ruft den Hostteil einer URL ab.

**Ordnung**

```
{{ 'https://example.com/path?foo=bar&page=2' | host }}
```

**Ausgeben**

```
example.com
```

### <a name="path"></a>**ADS**

Ruft den Pfadteil einer URL ab.

**Ordnung**

```
{{ 'https://example.com/path?foo=bar&page=2' | path }}

{{ '/path?foo=bar&page=2' | path }}
```

**Ausgeben**

```
/path

/path
```

### <a name="path_and_query"></a>**Pfad\_und\_Abfrage**

Ruft den Pfad und den Abfrage Teil einer URL ab.

**Ordnung**

```
{{ 'https://example.com/path?foo=bar&page=2' | path_and_query }}

{{ '/path?foo=bar&page=2' | path_and_query }}
```

**Ausgeben**

```
/path?foo=bar&page=2

/path?foo=bar&page=2
```

### <a name="port"></a>**Port**

Ruft die Portnummer einer URL ab.

**Ordnung**

```
{{ 'https://example.com/path?foo=bar&page=2' | port }}

{{ 'https://example.com/path?foo=bar&page=2' | port }}

{{ 'https://example.com:9000/path?foo=bar&page=2' | port }}
```

**Ausgeben**

```
80

443

9000
```

### <a name="remove_query"></a>**\_Abfrage entfernen**

Entfernt einen Abfrage Zeichen folgen Parameter aus einer URL. Wenn der-Parameter nicht in der URL vorhanden ist, wird die URL unverändert zurückgegeben.

Wenn dieser Filter auf eine vollständige absolute URL angewendet wird, ist das Ergebnis eine aktualisierte absolute URL. Wenn Sie auf einen Pfad angewendet wird, ist das Ergebnis ein aktualisierter Pfad.

**Ordnung**

```
{{ 'https://example.com/path?page=1' | remove_query: 'page' }}

{{ '/path?page=1' | remove_query: 'page' }}
```

**Ausgeben**

```
https://example.com/path

/path
```

### <a name="scheme"></a>**Schrift**

Ruft den Schema Teil einer URL ab.

**Ordnung**

```
{{ 'https://example.com/path?foo=bar&page=2' | scheme }}

{{ 'https://example.com/path?foo=bar&page=2' | scheme }}
```

**Ausgeben**

```
http

https
```


## <a name="additional-filters"></a>Zusätzliche Filter

Diese Filter bieten nützliche allgemeine Funktionen.

### <a name="default"></a>**vorgegebene**

Gibt einen Standardwert für jede Variable ohne zugewiesenen Wert zurück (d. h. null).

**Ordnung**

```
{{ snippets[Header] | default: 'My Website' }}
```

**Ausgeben**

```
<!-- If a snippet with the name Header returns null -->

My Website
```

### <a name="file_size"></a>**Datei\_Größe**

Wird auf einen Zahlenwert angewendet, der eine Anzahl von Bytes darstellt, gibt eine formatierte Dateigröße mit einer angemessenen Skalierungs Einheit zurück.

Optional kann ein Precision-Parameter übergeben werden, um die Anzahl der Dezimalstellen im Ergebnis zu steuern. Die Standardgenauigkeit beträgt 1.

**Ordnung**

```
{{ 10000000 | file_size }}

{{ 2050 | file_size: 0 }}

{{ entity.notes.first.filesize | file_size: 2 }}
```

**Ausgeben**

```
9.5 MB

2 KB

207.14 KB
```

### <a name="has_role"></a>**hat\_Rolle**

Wird auf einen [Benutzer](liquid-objects.md#user)angewendet und gibt true zurück, wenn der Benutzer zur angegebenen Rolle gehört. Gibt false zurück, wenn nicht.  

**Ordnung**

```
{% assign is_admin = user | has_role: 'Administrators' %}

{% if is_admin %}

User is an administrator.

{% endif %}
```

### <a name="liquid"></a>**flüssi**

Rendert eine Zeichenfolge als Liquid-Code. Dieser Code hat Zugriff auf den aktuellen Liquid-Ausführungs Kontext (Variablen usw.).

> [!Note] 
> Dieser Filter sollte mit Bedacht verwendet werden und sollte in der Regel nur auf Werte angewendet werden, die der ausschließlichen Kontrolle der Autoren von Portal Inhalten oder anderen Benutzern unterliegen, die für das Schreiben von Liquid-Code vertrauenswürdig sind.

**Ordnung**

```
{{ page.adx_copy | liquid }}
```

### <a name="see-also"></a>Siehe auch

[Speichern von Quell Inhalten mithilfe von Webvorlagen](store-content-web-templates.md)  
[Verstehen von Liquid-Operatoren](liquid-operators.md) 
[Liquid-Typen](liquid-types.md)  
[Liquid-Objekte](liquid-objects.md)  
[Liquid-Tags](liquid-tags.md)  
[Liquid-Filter](liquid-filters.md)  
