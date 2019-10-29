---
title: Verwenden von Liquid-Typen für ein Portal | MicrosoftDocs
description: Erfahren Sie mehr über die verfügbaren Liquid-Typen in einem Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: dd6da4788f6563c2026f57914c8156caedfadad3
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72974941"
---
# <a name="available-liquid-types"></a>Verfügbare Liquid-Typen

Liquid-Objekte können einen von sieben Grundtypen zurückgeben: **String**, **Number**, **Boolean**, **Array**, **Dictionary**, **DateTime**oder **null**. Flüssige Variablen können mithilfe der **assign** -oder **Capture** -Tags initialisiert werden.

## <a name="string"></a>Zeichenfolge

Eine Zeichenfolge wird deklariert, indem Text in einfache oder doppelte Anführungszeichen eingeschlossen wird.

```
{% assign string_a = Hello World! %}

{% assign string_b = 'Single quotes work too.' %}
```

Die Anzahl von Zeichen in einer Zeichenfolge mit der Size-Eigenschaft erhalten.

```
{{ string_a.size }} <!-- Output: 12 -->
```

## <a name="number"></a>Number

Zahlen können ganze Zahlen oder Gleit Komma Zahlen sein.

```
{% assign pi = 3.14 %}

{% if page.title.size > 100 %}

This page has a long title.

{% endif %}
```

## <a name="boolean"></a>Boolescher Wert

Ein boolescher Wert ist entweder true oder false.

```
{% assign x = true %}

{% assign y = false %}

{% if x %}

This will be rendered, because x is true.

{% endif %}
```

## <a name="array"></a>Array

Ein Array enthält eine Liste der Werte eines beliebigen Typs. Sie können auf ein angegebenes Element mit (null basierter) Index zugreifen, indem Sie \[ \]verwenden, diese mithilfe des **für-Tags**durchlaufen und die Anzahl der Elemente im Array mithilfe der Size-Eigenschaft abrufen.

```
{% for view in entitylist.views %}

{{ view.name }}

{% endfor %}

{{ entitylist.views[0] }}

{% if entitylist.views.size > 0 %}

This entity list has {{ entitylist.views.size }} views.

{% endif %}
```

## <a name="dictionary"></a>Buch

Wörterbücher enthalten eine Auflistung von Werten, auf die über einen Zeichen folgen Schlüssel zugegriffen werden kann. Sie können mit \[ \]auf ein bestimmtes Element über einen Zeichen folgen Schlüssel zugreifen, ihn mit dem **for-Tag**durchlaufen und die Anzahl der Elemente im Wörterbuch mithilfe der Size-Eigenschaft abrufen.

```
{{ request.params[ID] }}

{% if request.params.size > 0 %}

The request parameters collection contains some items.

{% endif %}
```

## <a name="datetime"></a>DateTime

Ein DateTime-Objekt stellt ein bestimmtes Datum und eine bestimmte Uhrzeit dar.

```
{{ page.modifiedon | date: 'f' }}
```

## <a name="null"></a>Normal

NULL stellt einen leeren oder nicht vorhandenen Wert dar. Alle Ausgaben, die versuchen, einen NULL-Wert zurückzugeben, werden nichts gereinigen. In Bedingungen wird er als falsch behandelt.

```
{% if request.params[ID] %}

This will render if the ID request parameter is NOT null.

{% endif %}
```

### <a name="see-also"></a>Siehe auch

[Speichern von Quell Inhalten mithilfe von Webvorlagen](store-content-web-templates.md)  
[Grundlegendes zu Liquid](liquid-operators.md)  
[Conditional](liquid-conditional-operators.md)  
[Liquid-Objekte](liquid-objects.md)  
[Liquid-Tags](liquid-tags.md)  
[Liquid-Filter](liquid-filters.md)  