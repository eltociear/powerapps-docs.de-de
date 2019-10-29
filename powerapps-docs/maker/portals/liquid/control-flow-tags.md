---
title: Verwenden von Ablauf Steuerungs Tags für ein Portal | MicrosoftDocs
description: Erfahren Sie mehr über Ablauf Steuerungs Tags, die im Portal verfügbar sind.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 77fcc7db0adf68cd6decbcc95e11d8e803761535
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975102"
---
# <a name="control-flow-tags"></a>Ablaufsteuerungstags

Ablauf Steuerungs Tags bestimmen, welcher Codeblock ausgeführt werden soll und welcher Inhalt basierend auf den angegebenen Bedingungen gerendert werden soll. Bedingungen werden mithilfe der verfügbaren [Liquid-Operatoren](liquid-operators.md)oder nur basierend auf [der Wahrheit oder der Falschheit eines bestimmten Werts](liquid-conditional-operators.md)erstellt.  

## <a name="if"></a>Sei

Führt einen Codeblock aus, wenn eine bestimmte Bedingung erfüllt ist.

```
{% if user.fullname == 'Dave Bowman' %}

Hello, Dave.

{% endif %}
```

## <a name="unless"></a>anderes

Wie bei, mit der Ausnahme, dass ein Codeblock ausgeführt wird, wenn eine bestimmte Bedingung**nicht** erfüllt wird.

```
{% unless page.title == 'Home' %}

This is not the Home page.

{% endunless %}
```

## <a name="elsifelse"></a>elsif/Else

Fügt einer if-oder-Block-Sperre weitere Bedingungen hinzu.

```
{% if user.fullname == 'Dave Bowman' %}

Hello, Dave.

{% elsif user.fullname == 'John Smith' %}

Hello, Mr. Smith.

{% else %}

Hello, stranger.

{% endif %}
```

## <a name="casewhen"></a>Groß-/Kleinschreibung

Eine Switch-Anweisung, mit der eine Variable mit unterschiedlichen Werten verglichen und für jeden Wert ein anderer Codeblock ausgeführt wird.

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

[Iterations Tags](iteration-tags.md)<br>
[Variablen Tags](variable-tags.md)<br>
[Vorlagen Tags](template-tags.md)<br>
[Powerapps Common Data Service-Entitäts Tags](portals-entity-tags.md)
