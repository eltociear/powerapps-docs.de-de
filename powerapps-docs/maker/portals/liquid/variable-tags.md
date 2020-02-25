---
title: Variable Tags für ein Portal verwenden | MicrosoftDocs
description: Lesen Sie mehr zu den verfügbaren variablen Tags im Portal
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: f9a56a9bccc8445dc7540f6ade402d5988ec1ffc
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "2978807"
---
# <a name="variable-tags"></a>Variable Tags

Variable Tags werden verwendet, um neue Liquid-Variablen zu erstellen.

## <a name="assign"></a>Zuweisen

Erstellt einer neuen Variable. Zuweisungen können auch [Filter](liquid-filters.md) verwenden, um den Wert ändern.  

**Code**

```
{% assign is_valid = true %}

{% if is_valid %}

It is valid.

{% endif %}

{% assign name = dave bowman' | upcase %}

{{ name }}
```

**Ausgabe**

```
It is valid.

DAVE BOWMAN
```

## <a name="capture"></a>capture

Erfasst den Inhalt innerhalb seines Blocks und weist ihn einer Variable zu. Dieser Inhalt kann dann später mithilfe von Ausgabetags gerendert werden.

**Code**

```
{% capture hello %}Hello, {{ user.fullname }}.{% endcapture %}

{{ hello }}

{{ hello }}
```

**Ausgabe**

```
Hello, DAVE BOWMAN.

Hello, DAVE BOWMAN.
```

### <a name="see-also"></a>Siehe auch

[Ablaufsteuerungstags](control-flow-tags.md)<br>
[Iterationstags](iteration-tags.md)<br>
[Vorlagentags](template-tags.md)<br>
[Power Apps Common Data Service-Entitäts-Tags](portals-entity-tags.md)
