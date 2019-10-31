---
title: Liquid-Tags für ein Portal verwenden | MicrosoftDocs
description: Lesen Sie mehr zu den verfügbaren Liquid-Tags in einem Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
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
