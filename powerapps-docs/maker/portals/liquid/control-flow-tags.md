---
title: Verwenden von Ablaufsteuerungs-Tags für ein Portal | MicrosoftDocs
description: Lesen Sie mehr zu den Ablaufsteuerungs-Tags im Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="control-flow-tags"></a>Ablaufsteuerungstags

Ablaufsteuerungstags bestimmen, welcher Codeblock ausgeführt werden sollte und welcher Inhalt dargestellt werden sollte auf der Grundlage bestimmter Bedingungen. Bedingungen werden mithilfe des verfügbaren [Flüssige Operatoren](liquid-operators.md) oder ausschließlich basierend auf [dem Fakt der Wahrheit oder Unwahrheit eines Werts](liquid-conditional-operators.md) basiert.  

## <a name="if"></a>if

Führt einen Codeblock aus, wenn eine bestimmte Bedingung erfüllt ist.

```
{% if user.fullname == 'Dave Bowman' %}

Hello, Dave.

{% endif %}
```

## <a name="unless"></a>unless

Wie „if”, nur dass ein Codeblock ausgeführt wird, wenn eine bestimmte Bedingung **nicht** erfüllt ist.

```
{% unless page.title == 'Home' %}

This is not the Home page.

{% endunless %}
```

## <a name="elsifelse"></a>elsif/else

Fügt mehrere Bedingungen zu einem if- oder unless-Block hinzu.

```
{% if user.fullname == 'Dave Bowman' %}

Hello, Dave.

{% elsif user.fullname == 'John Smith' %}

Hello, Mr. Smith.

{% else %}

Hello, stranger.

{% endif %}
```

## <a name="casewhen"></a>case/when

Eine switch-Anweisung, um eine Variable mit verschiedenen Werten zu vergleichen und einen anderen Codeblock für jeden Wert auszuführen.

```
{% case user.fullname %}

{% when 'Dave Bowman' %}

Hello, Dave.

{% when 'John Smith' %}

Hello, Mr. Smith.

{% else %}

Hello, stranger.

{% endcase %}
```

### <a name="see-also"></a>Siehe auch

[Iterationstags](iteration-tags.md)<br>
[Variable Tags](variable-tags.md)<br>
[Vorlagentags](template-tags.md)<br>
[PowerApps Common Data Service-Entitäts-Tags](portals-entity-tags.md)
