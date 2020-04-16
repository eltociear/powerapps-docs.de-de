---
title: Verwenden von Liquid-Typen für ein Portal | MicrosoftDocs
description: Lesen Sie mehr zu den verfügbaren Liquid-Typen in einem Portal.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: e84ec3363f492231c218e0bb9f6e8a8d8b45fce6
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "3125043"
---
# <a name="available-liquid-types"></a>Verfügbare Liquid-Typen

Liquid-Objekte können sieben grundlegende Typen zurückgeben: **String**, **Number**, **Boolean**, **Array**, **Dictionary**, **DateTime**, or **Null**. Liquid-Variablen können durch Verwendung der Tags **assign** oder **capture** initialisiert werden.

## <a name="string"></a>Zeichenfolge

Eine Zeichenfolge wird deklariert, indem ein Text in einfache oder doppelte Anführungszeichen eingeschlossen wird.

```
{% assign string_a = Hello World! %}

{% assign string_b = 'Single quotes work too.' %}
```

Rufen Sie die Anzahl der Zeichen in einer Zeichenfolge mit der size-Eigenschaft ab.

```
{{ string_a.size }} <!-- Output: 12 -->
```

## <a name="number"></a>Zahl

Zahlen können ganze Zahlen oder Gleitkommazahlen sein.

```
{% assign pi = 3.14 %}

{% if page.title.size > 100 %}

This page has a long title.

{% endif %}
```

## <a name="boolean"></a>Boolean

Boolesche Werte sind entweder true oder false.

```
{% assign x = true %}

{% assign y = false %}

{% if x %}

This will be rendered, because x is true.

{% endif %}
```

## <a name="array"></a>Array

Arrays führen eine Liste mit Werten eines beliebigen Typs aus. Sie können mit \[ \] auf ein bestimmtes Element im nullbasierten Index zugreifen, den Index über den **for tag** durchlaufen und über die size-Eigenschaft die Anzahl der Elemente im Array abfragen.

```
{% for view in entitylist.views %}

{{ view.name }}

{% endfor %}

{{ entitylist.views[0] }}

{% if entitylist.views.size > 0 %}

This entity list has {{ entitylist.views.size }} views.

{% endif %}
```

## <a name="dictionary"></a>Dictionary

Wörterbücher geben eine Sammlung von Werten an, auf die mit einem Zeichenfolgenschlüssel zugegriffen werden kann. Sie können mit \[ \] auf ein bestimmtes Element im Zeichenfolgenschlüssel zugreifen, den Index über den **for tag** durchlaufen und über die size-Eigenschaft die Anzahl der Elemente im Wörterbuch abfragen.

```
{{ request.params[ID] }}

{% if request.params.size > 0 %}

The request parameters collection contains some items.

{% endif %}
```

## <a name="datetime"></a>DateTime

DateTime-Objekte stellen ein bestimmtes Datum und eine bestimmte Uhrzeit dar.

```
{{ page.modifiedon | date: 'f' }}
```

## <a name="null"></a>Null

Null stellt einen leeren oder nicht vorhandene Wert dar. Alle Ausgaben, die versuchen, einen Nullwert zurückzugeben, rendern nichts. Er wird in Bedingungen als "false" behandelt.

```
{% if request.params[ID] %}

This will render if the ID request parameter is NOT null.

{% endif %}
```

### <a name="see-also"></a>Siehe auch

[Speichern von Inhalten mit Webvorlagen](store-content-web-templates.md)  
[Lernen Sie Liquid-Operatoren kennen](liquid-operators.md)  
[Bedingt](liquid-conditional-operators.md)  
[Liquid-Objekte](liquid-objects.md)  
[Liquid-Tags](liquid-tags.md)  
[Liquid-Filter](liquid-filters.md)  