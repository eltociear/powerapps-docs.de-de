---
title: Verwenden von Liquid-Filtern für ein Portal | MicrosoftDocs
description: Lesen Sie mehr zu den verfügbaren Liquid-Filtern in einem Portal.
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
ms.locfileid: "2757266"
---
# <a name="available-liquid-filters"></a>Verfügbare Liquid-Filter

Liquid-Filter dienen zur Änderung der Ausgabe von Zeichenfolgen, Zahlen, Variablen und Objekten. Sie werden vom Wert getrennt, für den sie von einem a | übernommen werden.

`{{ 'hal 9000' | upcase }} <!-- Output: HAL 9000 -->`

Einige Filter akzeptieren Parameter. Filter können auch kombiniert werden und werden von links nach rechts angewendet.

```
{{ 2 | times: 2 | minus: 1 }} <!-- Output: 3 -->

{{ "Hello, " | append: user.firstname }} <!-- Output: Hello, Dave -->
```
Der unten stehende Abschnitt beschreibt verschiedene Filter. 

## <a name="array-filters"></a>Arrayfilter

Arrayfilter werden zur Arbeit mit [Arrays](liquid-types.md#array) verwendet.  

### <a name="batch"></a>batch

Teilt ein Array auf mehrere Arrays mit gegebenen Größe auf.

**Code**

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

**Ausgabe**

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

### <a name="concat"></a>concat

Verkettet zwei Arrays in ein einzelnes Array.

Bei einem Element als Parameter gibt concat ein neues Array zurück, das aus dem ursprünglichen Array besteht, bei dem das angegebene Element das letzte Element ist.

**Code**

```
Group #1: {{ group1 | join: ', ' }}

Group #2: {{ group2 | join: ', ' }}

Group #1 + Group #2: {{ group1 | concat: group2 | join: ', ' }}

Group #1 + Leslie: {{ group1 | concat: 'Leslie' | join: ', ' }}
```

**Ausgabe**

```
Group #1: John, Pete, Hannah

Group #2: Joan, Bill

Group #1 + Group #2: John, Pete, Hannah, Joan, Bill

Group #1 + Leslie: John, Pete, Hannah, Leslie
```

### <a name="except"></a>except

Wählt alle Objekte in einem Array aus, bei denen ein gegebenes Attribut nicht einen bestimmten Wert enthält. (Gegenteil von **where**.)

**Code**

```
{% assign redmond = entityview.records | except: 'address1_city', 'Redmond' %}

{% for item in redmond %}

{{ item.fullname }}

{% endfor %}
```

**Ausgabe**

```
Jack Robinson
```

### <a name="first"></a>erste

Gibt das erste Element eines Arrays zurück.

„erste“ kann auch mit einer speziellen Punktnotation verwendet werden. In diesem Fall muss es innerhalb eines Tags verwendet werden.

**Code**

```
{% assign words = This is a run of text | split:   %}

{{ words | first }}

{% if words.first == This %}

The first word is This.

{% endif %}
```

**Ausgabe**

```
This

The first word is This.
```

### <a name="group_by"></a>group_by

Gruppieren der Elemente in einem Array nach einen bestimmten Attribut.

**Code**

```
{% assign groups = entityview.records | group_by: 'address1_city' %}

{% for group in groups %}

{{ group.key }}:

{% for item in group.items %}

{{ item.fullname }}

{% endfor %}

{% endfor %}
```

**Ausgabe**

```
Redmond:

John Smith

Dave Thomas

Jake Johnson

New York:

Jack Robinson
```

### <a name="join"></a>join

Verbindet die Elemente eines Arrays mit einem als Parameter übergebenen Zeichen. Das Ergebnis ist eine einzelne Zeichenfolge.

**Code**

```
{% assign words = This is a run of text | split:   %}

{{ words | join: ,  }}
```

**Ausgabe**

```
This, is, a, run, of, text
```

### <a name="last"></a>letzte

Gibt das letzte Element eines Arrays zurück.

„letzte“ kann auch mit einer speziellen Punktnotation verwendet werden. In diesem Fall muss es innerhalb eines Tags verwendet werden.

**Code**

```
{% assign words = This is a run of text | split:   -%}

{{ words | last }}

{% if words.last == text -%}

The last word is text.

{% endif -%}
```

**Ausgabe**

```
text

The last word is text.
```

### <a name="order_by"></a>order\_by

Gibt die Elemente eines Arrays sortiert nach einem Attribut zurück.

Optional können Sie als zweiten Parameter „desc“ angeben, um die Elemente in absteigender Reihenfolge zu sortieren.

**Code**

```
{{ entityview.records | order_by: 'fullname' | join: ', ' }}

{{ entityview.records | order_by: 'fullname', 'desc' | join: ', ' }}
```

**Ausgabe**

```
Dave Thomas, Jack Robinson, Jake Johnson, John Smith

John Smith, Jake Johnson, Jack Robinson, Dave Thomas
```

### <a name="random"></a>random

Gibt ein einzelnes zufällig ausgewähltes Element im Array zurück.

**Code**

```
{{ group1 | join: ', ' }}

{{ group1 | random }}
```

**Ausgabe**

```
John, Pete, Hannah

Pete
```

### <a name="select"></a>select

Wählt den Wert eines bestimmten Attributs in einem Array aus und gibt diesen zurück.

**Code**

```
{{ entityview.records | select: 'address1_city' | join: ', ' }}
```

**Ausgabe**

```
Redmond, New York
```

### <a name="shuffle"></a>shuffle

Gibt einen neuen Array zurück, in dem die Elemente in zufälliger Reihenfolge vorhanden sind.

**Code**

```
{{ group1 | join: ', ' }}

{{ group1 | shuffle | join: ', ' }}
```

**Ausgabe**

```
John, Pete, Hannah

Hannah, John, Pete
```

### <a name="size"></a>size

Gibt die Anzahl der Elemente in einem "Array" zurück.

„size“ kann auch mit einer speziellen Punktnotation verwendet werden. In diesem Fall muss es innerhalb eines Tags verwendet werden.

**Code**

```
{% assign words = This is a run of text | split:   -%}

{{ words | size }}

{% if words.size == 6 -%}

The text contains 6 words.

{% endif -%}
```

**Ausgabe**

```
6

The text contains 6 words.
```

### <a name="skip"></a>skip

Überspringt eine bestimmte Anzahl von Elementen in einem "Array" und gibt den Rest zurück.

**Code**

```
{% assign words = This is a run of text | split:   %}

{{ words | skip: 3 | join: ', ' }}
```

**Ausgabe**

```
run, of, text
```

### <a name="take"></a>take

Nimmt eine bestimmte Anzahl der Elemente im Array und gibt diese zurück.

**Code**

```
{% assign words = This is a run of text | split:   %}

{{ words | take: 3 | join: ', ' }}
```
**Ausgabe**

```

This, is, a
```

### <a name="then_by"></a>dann\_bei

Fügt einem bereits über **order\_by** sortierten Array eine weitere Sortierung hinzu.

Optional können Sie als zweiten Parameter „desc“ angeben, um die Elemente in absteigender Reihenfolge zu sortieren.

**Code**

```
{{ entityview.records | order_by: 'address1_city' | then_by: 'fullname' | join: ', ' }}

{{ entityview.records | order_by: 'address1_city' | then_by: 'fullname', 'desc' | join: ', ' }}
```

**Ausgabe**

```
Dave Thomas, Jack Robinson, Jake Johnson, John Smith

John Smith, Jake Johnson, Jack Robinson, Dave Thomas
```

### <a name="where"></a>Dabei gilt Folgendes:

Wählt alle Objekte in einem Array aus, bei denen ein gegebenes Attribut einen bestimmten Wert enthält.

**Code**

```
{% assign redmond = entityview.records | where: 'address1_city', 'Redmond' %}

{% for item in redmond %}

{{ item.fullname }}

{% endfor %}
```

**Ausgabe**

```
John Smith

Dave Thomas

Jake Johnson
```


## <a name="date-filters"></a>Datumsfilter

Datumsfilter können für die Datumsarithmetik verwendet werden, oder um DateTime-Werte in unterschiedliche Formate zu konvertieren.

### <a name="date"></a>Datum

Formatiert einen DateTime-Wert mithilfe einer .NET-Formatzeichenfolge.

[Standardformatzeichenfolgen für Datum und Uhrzeiten](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)  

[Standardformatzeichenfolgen für Datum und Uhrzeiten](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings)  

**Code**

```
{{ now | date: 'g' }}

{{ now | date: 'MMMM dd, yyyy' }}
```

**Ausgabe**

```
5/7/2018 7:20 AM

May 07, 2018
```

### <a name="date_add_days"></a>datum\_hinzufügen\_Tag

Fügt die angegebene Anzahl von ganzen und teilweisen Tagen aus dem DateTime-Wert hinzu. Der Parameter kann positiv oder negativ sein.

**Code**

```
{{ now }}

{{ now | date_add_days: 1 }}

{{ now | date_add_days: -2.5 }}
```

**Ausgabe**

```
5/7/2018 7:20:46 AM

5/8/2018 7:20:46 AM

5/4/2018 7:20:46 PM
```

### <a name="date_add_hours"></a>Daten\_hinzufügen\_Stunden

Fügt die angegebene Anzahl von ganzen und teilweisen Stunden aus dem DateTime-Wert hinzu. Der Parameter kann positiv oder negativ sein.

**Code**

```
{{ now }}

{{ now | date_add_hours: 1 }}

{{ now | date_add_hours: -2.5 }}
```

**Ausgabe**

```
5/7/2018 7:20:46 AM

5/7/2018 8:20:46 AM

5/7/2018 4:50:46 AM
```

### <a name="date_add_minutes"></a>Datum\_hinzufügen\_Minuten

Fügt die angegebene Anzahl von ganzen und teilweisen Minuten aus dem DateTime-Wert hinzu. Der Parameter kann positiv oder negativ sein.

**Code**

```
{{ now }}

{{ now | date_add_minutes: 10 }}

{{ now | date_add_minutes: -2.5 }}
```


**Ausgabe**

```
5/7/2018 7:20:46 AM

5/7/2018 7:30:46 AM

5/7/2018 7:18:16 AM
```

### <a name="date_add_months"></a>date\_add\_months

Fügt die angegebene Anzahl von ganzen und teilweisen Monaten aus dem DateTime-Wert hinzu. Der Parameter kann positiv oder negativ sein.

**Code**

```
{{ now }}

{{ now | date_add_months: 1 }}

{{ now | date_add_months: -2 }}
```

**Ausgabe**

```
5/7/2018 7:20:46 AM

6/7/2018 7:20:46 AM

3/7/2018 7:20:46 AM
```

### <a name="date_add_seconds"></a>date\_add\_seconds

Fügt die angegebene Anzahl von ganzen und teilweisen Sekunden aus dem DateTime-Wert hinzu. Der Parameter kann positiv oder negativ sein.

**Code**

```
{{ now }}

{{ now | date_add_seconds: 10 }}

{{ now | date_add_seconds: -1.25 }}
```

**Ausgabe**

```
5/7/2018 7:20:46 AM

5/7/2018 7:20:56 AM

5/7/2018 7:20:45 AM
```

### <a name="date_add_years"></a>date\_add\_years

Fügt die angegebene Anzahl von ganzen und teilweisen Jahren aus dem DateTime-Wert hinzu. Der Parameter kann positiv oder negativ sein.

**Code**

```
{{ now }}

{{ now | date_add_years: 1 }}

{{ now | date_add_years: -2 }}
```

**Ausgabe**

```
5/7/2018 7:20:46 AM

5/7/2019 7:20:46 AM

5/7/2016 7:20:46 AM
```

### <a name="date_to_iso8601"></a>date\_to\_iso8601

Formatiert einen DateTime-Wert, gemäß dem [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) Standards. Sinnvoll beim Erstellen von [*Atom-Feeds*](https://tools.ietf.org/html/rfc4287) oder einem HTML5 &lt;time&gt;-Element.  

**Code**

```
{{ now | date_to_iso8601 }}
```

**Ausgabe**

```
2018-05-07T07:20:46Z
```

### <a name="date_to_rfc822"></a>date\_to\_rfc822

Formatiert einen DateTime-Wert, gemäß dem [RFC 822](https://www.ietf.org/rfc/rfc0822.txt) Standards. Sinnvoll beim Erstellen von [*RSS-Feeds*](https://cyber.law.harvard.edu/rss/rss.html).  

**Code**

```
{{ now | date_to_rfc822 }}
```

**Ausgabe**

```
Mon, 07 May 2018 07:20:46 Z
```


## <a name="entity-list-filters"></a>Entitäts-Listenfilter

Entitäts-Listenfilter werden verwendet, um mit bestimmten [entitylist](liquid-objects.md#entitylist)-Attributwerten zu arbeiten und Ansichten von Entitätslisten zu erstellen.  

### <a name="current_sort"></a>current\_sort

Gibt bei angegebenen Sortierausdruck die aktuelle Sortierreihenfolge für ein bestimmtes Attribut zurück.

**Code**

```
{{ 'name ASC, createdon DESC' | current_sort: 'createdon' }}
```

**Ausgabe**

```
DESC
```

### <a name="metafilters"></a>metafilters

Analysiert einen [entitylis](liquid-objects.md#entitylist)t filter\_definition-JSON-Wert in Filteroptions-Gruppenobjekte.  

„metafilters“ kann optional mit einer aktuellen Attributfilterabfrage und aktueller [entitylist](liquid-objects.md#entitylist) bereitgestellt werden, wodurch die zurückgegebenen Filterobjekte entweder als ausgewählt oder als nicht ausgewählt gekennzeichnet werden können.

**Code**

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

### <a name="reverse_sort"></a>reverse\_sort

Kehrt eine angegebene Sortierreihenfolge um.

**Code**

```
<!-- Sort direction is not case-sensitive -->

{{ 'ASC' | reverse_sort }}

{{ 'desc' | reverse_sort }}
```

**Ausgabe**

```
DESC

ASC
```


## <a name="math-filters"></a>Mathematische Filter

Mathematische Filter ermöglichen mathematische Vorgänge für[Zahlen](liquid-types.md#number) .  

Mathematische Filter können wie alle Filter verkettet werden und werden von links nach rechts angewendet.

**Code**

```
{{ 10 | times: 2 | minus: 5 | divided_by: 3 }}
```

**Ausgabe**

```
5
```

### <a name="ceil"></a>ceil

Rundet einen Wert auf die nächste Ganzzahl auf.

**Code**

```
{{ 4.6 | ceil }}

{{ 4.3 | ceil }}
```

**Ausgabe**

```
5

5
```

### <a name="divided_by"></a>divided\_by

Dividiert eine Zahl durch eine andere Zahl.

**Code**

```
{{ 10 | divided_by: 2 }}

{{ 10 | divided_by: 3 }}

{{ 10.0 | divided_by: 3 }}
```

**Ausgabe**

```
5

3

3.333333
```

### <a name="floor"></a>floor

Rundet einen Wert auf die nächste Ganzzahl ab.

**Code**

```
{{ 4.6 | floor }}

{{ 4.3 | floor }}
```

**Ausgabe**

```
4

4
```

### <a name="minus"></a>minus

Subtrahiert eine Zahl von einer anderen Zahl.

**Code**

```
<!-- entityview.page = 11 -->

{{ entityview.page | minus: 1 }}

{{ 10 | minus: 1.1 }}

{{ 10.1 | minus: 1 }}
```

**Ausgabe**

```
10

9

9.1
```

### <a name="modulo"></a>modulo

Dividiert eine Zahl durch eine andere Zahl und gibt den Rest zurück.

**Code**

```
{{ 12 | modulo: 5 }}
```

**Ausgabe**

```
2
```

### <a name="plus"></a>plus

Fügt eine Zahl zu einer anderen Zahl hinzu.

**Code**

```
<!-- entityview.page = 11 -->

{{ entityview.page | plus: 1 }}

{{ 10 | plus: 1.1 }}

{{ 10.1 | plus: 1 }}
```

**Ausgabe**

```
12

11

11.1
```

### <a name="round"></a>round

Rundet einen Wert auf die nächste ganze Zahl oder angegebene Anzahl von Dezimalstellen.

**Code**

```
{{ 4.6 | round }}

{{ 4.3 | round }}

{{ 4.5612 | round: 2 }}
```

**Ausgabe**

```
5

4

4.56
```

### <a name="times"></a>times

Multipliziert eine Zahl durch eine andere Zahl.

**Code**

```
{{ 10 | times: 2 }}

{{ 10 | times: 2.2 }}

{{ 10.1 | times: 2 }}
```

**Ausgabe**

```
20

20

20.2
```


## <a name="string-filters"></a>String-Filter

String-Filter bearbeiten [Strings](liquid-types.md#string).  

### <a name="append"></a>anfügen

Fügt eine Zeichenfolge an das Ende einer anderen Zeichenfolge an.

**Code**

```
{{ 'filename' | append: '.js' }}
```

**Ausgabe**

```
filename.js
```

### <a name="capitalize"></a>**capitalize**

schreibt das erste Wort einer Zeichenfolge groß.

**Code**

```
{{ 'capitalize me' | capitalize }}
```

**Ausgabe**

```
Capitalize Me
```

### <a name="downcase"></a>**downcase**

Konvertiert eine Zeichenfolge in Kleinbuchstaben.

**Code**

```
{{ 'MIxed Case TExt' | downcase }}
```

**Ausgabe**

```
mixed case text
```

### <a name="escape"></a>**escape**

HTML-maskiert eine Zeichenfolge.

**Code**

```
{{ '<p>test</p>' | escape }}
```

**Ausgabe**

```
&lt;p&gt;test&lt;/p&gt;
```

### <a name="newline_to_br"></a>**newline\_to\_br**

Fügt einen &lt;br /&gt;-Zeilenumbruch-HTML-Tag an jedem Zeilenumbruch in einer Zeichenfolge ein.

**Code**

```
{% capture text %}

A

B

C

{% endcapture %}

{{ text | newline_to_br }}
```

**Output**

```
A<br />

B<br />

C<br />
```

### <a name="prepend"></a>**prepend**

Stellt eine Zeichenfolge an den Anfang einer anderen Zeichenfolge.

**Code**

```
{{ 'Jane Johnson' | prepend: 'Dr. ' }}
```

**Ausgabe**

```
Dr. Jane Johnson
```

### <a name="remove"></a>**remove**

Entfernt alle Vorkommen einer Teilzeichenfolge aus der Zeichenfolge.

**Code**

```
{{ 'Hello, Dave. How are you, Dave?' | remove: 'Dave' }}
```

**Ausgabe**

```
Hello, . How are you, ?
```

### <a name="remove_first"></a>**remove\_first**

Entfernt alle ersten Vorkommen einer Teilzeichenfolge aus der Zeichenfolge.

**Code**

```
{{ 'Hello, Dave. How are you, Dave?' | remove_first: 'Dave' }}
```

**Ausgabe**

```
Hello, . How are you, Dave?
```

### <a name="replace"></a>**replace**

Entfernt alle Vorkommen einer Zeichenfolge, die eine Teilzeichenfolge enthalten.

**Code**

```
{{ 'Hello, Dave. How are you, Dave?' | replace: 'Dave', 'John' }}
```

**Ausgabe**

```
Hello, John. How are you, John?
```

### <a name="replace_first"></a>**replace\_first**

Ersetzt das erste Vorkommen einer Zeichenfolge, die eine Teilzeichenfolge enthalten.

**Code**

```
{{ 'Hello, Dave. How are you, Dave?' | replace_first: 'Dave', 'John' }}
```

**Ausgabe**

```
Hello, John. How are you, Dave?
```

### <a name="split"></a>**split**

Der split-Filter nimmt eine Teilzeichenfolge als Parameter entgegen. Die Teilzeichenfolge wird wie ein Trennzeichen verwendet werden, um eine Zeichenfolge in einen Array zu unterteilen.

**Code**

```
{% assign words = This is a demo of the split filter | split: ' ' %}

First word: {{ words.first }}

First word: {{ words[0] }}

Second word: {{ words[1] }}

Last word: {{ words.last }}

All words: {{ words | join: ', ' }}
```

**Ausgabe**

```
First word: This

First word: This

Second word: is

Last word: filter

All words: This, is, a, demo, of, the, split, filter
```

### <a name="strip_html"></a>**strip\_html**

Entfernt alle HTML-Tags einer Zeichenfolge.

**Code**

```
<p>Hello</p>
```

**Ausgabe**

```
Hello
```

### <a name="strip_newlines"></a>**strip\_newlines**

Entfernt alle Zeilenumbrüche einer Zeichenfolge.

**Code**

```
{% capture text %}

A

B

C

{% endcapture %}

{{ text | strip_newlines }}
```

**Ausgabe**

```
ABC
```

### <a name="text_to_html"></a>**text\_to\_html**

Formatiert eine Nur-Text-Zeichenfolge als HTML. Jeder Text wird als HTML codiert, Textblöcke, die durch eine Leerzeile getrennt sind, werden in Paragraph &lt;p&gt; -Tags eingebettet, einzelne Zeilenumbrüche werden durch &lt;br&gt; ersetzt und URLs werden in Hyperlinks konvertiert.

**Code**

```
{{ note.notetext | text_to_html }}
```

**Ausgabe**

```
<p>This is the first paragraph of notetext. It contains a URL: <a href="https://example.com/" rel="nofollow">https://example.com</a></p>

<p>This is a second paragraph.</p>
```

### <a name="truncate"></a>**truncate**

Verkürzt eine Zeichenfolge auf eine angegebene Anzahl von Zeichen. Auslassungspunkte (...) werden der Zeichenfolge angefügt und sind in der Zeichenzählung enthalten.

**Code**

```
{{ 'This is a long run of text.' | truncate: 10 }}
```

**Ausgabe**

```
This is...
```

### <a name="truncate_words"></a>**truncate\_words**

Verkürzt eine Zeichenfolge auf eine angegebene Anzahl von Wörtern. Auslassungspunkte (...) werden an die verkürzte Zeichenfolge angefügt.

**Code**

```
{{ 'This is a long run of text.' | truncate_words: 3 }}
```

**Ausgabe**

```
This is a...
```

### <a name="upcase"></a>**upcase**

Konvertiert eine Zeichenfolge in Großbuchstaben.

**Code**

```
{{ 'MIxed Case TExt' | upcase }}
```

**Ausgabe**

```
MIXED CASE TEXT
```

### <a name="url_escape"></a>**url\_escape**

URI-maskiert eine Zeichenfolge zur Einbindung in eine URL.

**Code**

```
{{ 'This & that//' | url_escape }}
```

**Ausgabe**

```
This+%26+that%2F%2F
```

### <a name="xml_escape"></a>**xml\_escape**

XML-maskiert eine Zeichenfolge zur Einbindung in eine XML-Ausgabe.

**Code**

```
{{ '<p>test</p>' | xml_escape }}
```

**Ausgabe**

```
&lt;p&gt;test&lt;/p&gt;
```


## <a name="type-filters"></a>Typfilter

Mit Typfiltern können Sie den Werte von einem Typ in andere Typen konvertieren.

### <a name="boolean"></a>**boolean**

Versucht, einen Zeichenfolgenwert in einen Booleschen Wert zu konvertieren. Wenn der Wert ist bereits ein Boolescher Wert ist, bleibt er unverändert. Falls der Wert nicht in einen booleschen Wert konvertiert werden kann, wird Null zurückgegeben.

Diese Filter nimmt auch "on", "enabled" oder "yes" als True und "off", "disabled" und "no" als False an.

**Code**

```
{{ true | boolean }}

{{ 'false' | boolean }}

{{ 'enabled' | boolean }}

{{ settings['something/enabled'] | boolean | default: false }}
```

**Ausgabe**

```
true

false

true

false
```

### <a name="decimal"></a>**decimal**

Versucht, einen Zeichenfolgenwert in eine Dezimalzahl zu konvertieren. Wenn der Wert ist bereits eine Dezimalzahl ist, bleibt er unverändert. Falls der Wert nicht in eine Dezimalzahl konvertiert werden kann, wird Null zurückgegeben.

**Code**

```
{{ 10.1 | decimal }}

{{ '3.14' | decimal }}

{{ 'text' | decimal | default: 3.14 }}
```

**Ausgabe**

```
10.1

3.14

3.14
```

### <a name="integer"></a>**integer**

Versucht, einen Zeichenfolgenwert in eine Ganzzahl zu konvertieren. Wenn der Wert ist bereits eine Ganzzahl ist, bleibt er unverändert. Falls der Wert nicht in eine Ganzzahl konvertiert werden kann, wird Null zurückgegeben.

**Code**

```
{{ 10 | integer }}

{{ '10' | integer }}

{{ '10.1' | integer }}

{{ 'text' | integer | default: 2 }}
```

**Ausgabe**

```
10

10


2
```

### <a name="string"></a>**string**

Versucht, einen Zeichenfolgenwert in eine Zeichenfolgendarstellung zu konvertieren. Wenn der Wert ist bereits eine Zeichenfolge ist, bleibt er unverändert. Wenn der Wert Null ist, wird Null zurückgegeben.



## <a name="url-filters"></a>URL-Filter

URL-Filter ermöglichen Ihnen, Teile von URLs zu erstellen bzw. zu extrahieren.

### <a name="add_query"></a>**add\_query**

Fügt einer URL einen Abfragezeichenfolgenparameter an. Wenn der Parameter bereits in der URL vorhanden ist, wird der Parameterwert aktualisiert.

Wenn der Filter für eine vollständige absolute URL angewendet wird, ist eine aktualisierte absolute URL das Ergebnis. Wenn er für einen Pfad angewendet wird, ist ein aktualisierter Pfad das Ergebnis.

**Code**

```
{{ 'https://example.com/path?page=1' | add_query: 'foo', 'bar' }}

{{ '/path?page=1' | add_query: 'page', 2 }}
```

**Ausgabe**

```
https://example.com/path?page=1&foo=bar

/path?page=2
```

### <a name="base"></a>**base**

Ruft die Basis-URL einer bestimmten URL ab.

**Code**

```
{{ 'https://example.com/path?foo=bar&page=2' | base }}
```

**Ausgabe**

```
https://example.com
```

### <a name="host"></a>**host**

Ruft den Hostteil einer URL ab.

**Code**

```
{{ 'https://example.com/path?foo=bar&page=2' | host }}
```

**Ausgabe**

```
example.com
```

### <a name="path"></a>**path**

Ruft den Pfadteil einer URL ab.

**Code**

```
{{ 'https://example.com/path?foo=bar&page=2' | path }}

{{ '/path?foo=bar&page=2' | path }}
```

**Ausgabe**

```
/path

/path
```

### <a name="path_and_query"></a>**path\_and\_query**

Ruft den Pfad- und Abfrageteil einer URL ab.

**Code**

```
{{ 'https://example.com/path?foo=bar&page=2' | path_and_query }}

{{ '/path?foo=bar&page=2' | path_and_query }}
```

**Ausgabe**

```
/path?foo=bar&page=2

/path?foo=bar&page=2
```

### <a name="port"></a>**port**

Ruft die Portnummer einer URL ab.

**Code**

```
{{ 'https://example.com/path?foo=bar&page=2' | port }}

{{ 'https://example.com/path?foo=bar&page=2' | port }}

{{ 'https://example.com:9000/path?foo=bar&page=2' | port }}
```

**Ausgabe**

```
80

443

9000
```

### <a name="remove_query"></a>**remove\_query**

Entfernt einen Abfragezeichenfolgenparameter von einer URL. Wenn der Parameter nicht in der URL vorhanden ist, wird die URL unverändert zurückgegeben.

Wenn der Filter für eine vollständige absolute URL angewendet wird, ist eine aktualisierte absolute URL das Ergebnis. Wenn er für einen Pfad angewendet wird, ist ein aktualisierter Pfad das Ergebnis.

**Code**

```
{{ 'https://example.com/path?page=1' | remove_query: 'page' }}

{{ '/path?page=1' | remove_query: 'page' }}
```

**Ausgabe**

```
https://example.com/path

/path
```

### <a name="scheme"></a>**scheme**

Ruft den Schemateil einer URL ab.

**Code**

```
{{ 'https://example.com/path?foo=bar&page=2' | scheme }}

{{ 'https://example.com/path?foo=bar&page=2' | scheme }}
```

**Ausgabe**

```
http

https
```


## <a name="additional-filters"></a>Zusätzliche Filter

Diese Filter bieten nützliche allgemeine Funktionen.

### <a name="default"></a>**default**

Gibt einen Standardwert für alle Variablen ohne zugewiesenen Wert zurück (also Null).

**Code**

```
{{ snippets[Header] | default: 'My Website' }}
```

**Ausgabe**

```
<!-- If a snippet with the name Header returns null -->

My Website
```

### <a name="file_size"></a>**file\_size**

Gilt für einen Zahlenwert, der für eine Reihe von Bytes steht und eine formatierte Dateigröße mit einer Einheit einer entsprechenden Skala zurückgibt.

Optional kann ein Genauigkeitsparameter übergeben werden, um die Anzahl der Dezimalstellen im Resultat zu steuern. Die Standardeinstellung ist 1.

**Code**

```
{{ 10000000 | file_size }}

{{ 2050 | file_size: 0 }}

{{ entity.notes.first.filesize | file_size: 2 }}
```

**Ausgabe**

```
9.5 MB

2 KB

207.14 KB
```

### <a name="has_role"></a>**has\_role**

Angewendet für einen [Benutzer](liquid-objects.md#user) wird True zurückgegeben, wenn der Benutzer zur angegebenen Rolle gehört. Gibt „false“ zurück, wenn nicht.  

**Code**

```
{% assign is_admin = user | has_role: 'Administrators' %}

{% if is_admin %}

User is an administrator.

{% endif %}
```

### <a name="liquid"></a>**liquid**

Bezeichnet einen String als flexiblen Code. Dieser Code hat Zugriff auf den aktuellen flexiblen Ausführungskontext (Variablen., usw.).

> [!Note] 
> Diese Filter sollte mit Vorsicht verwendet werden und sollte nur für Werte angewendet werden, die unter dem exklusiven Steuerelement der Autoren der Portalinhalte oder anderen Nutzern liegen, die Liquid-Codes schreiben können.

**Code**

```
{{ page.adx_copy | liquid }}
```

### <a name="see-also"></a>Siehe auch

[Speichern von Inhalten mit Webvorlagen](store-content-web-templates.md)  
[Grundlegendes zu Liquid-Operatoren](liquid-operators.md) 
[Liquid-Typen](liquid-types.md)  
[Liquid-Objekte](liquid-objects.md)  
[Liquid-Tags](liquid-tags.md)  
[Liquid-Filter](liquid-filters.md)  
