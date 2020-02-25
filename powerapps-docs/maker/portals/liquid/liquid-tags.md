---
title: Verwenden von Liquid-Tags für ein Portal | MicrosoftDocs
description: Lesen Sie mehr zu den verfügbaren Liquid-Tags in einem Portal.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 3f85e4b86b305696f5b155c7e9e3b773f8ba2103
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "2981095"
---
# <a name="available-liquid-tags"></a>Verfügbare Liquid-Tags

Tags bestimmen die Programmierlogik und damit das Verhalten von Vorlagen. Tags sind in {% %} eingebunden.

```
{% if user.fullname == 'Dave Bowman' %} Hello, Dave. {% endif %}
```

## <a name="whitespace-control"></a>Leerstellenensteuerelement

Normalerweise rendert Liquid alles außerhalb von Variablen und Tagblöcken gründlich, mit allen originalen Leerzeichen. Ggf. sind die zusätzlichen Leerstellen nicht gewünscht, jedoch sind für eine saubere Formatierung der Vorlage Leerstellen erforderlich.

Sie können das Modul anweisen, alle führenden oder nachfolgenden Leerstellen zu entfernen, indem Sie einen Bindestrich (-) zum Start- oder Endblocktag hinzufügen.

**Code**

```
{% for i in (1..5) --%}

{{ i }}

{%-- endfor %}
```

**Ausgabe**

```
12345
```
### <a name="see-also"></a>Siehe auch

[Liquid-Typen](liquid-types.md)  
[Liquid-Objekte](liquid-objects.md)  
[Liquid-Filter](liquid-filters.md) 
