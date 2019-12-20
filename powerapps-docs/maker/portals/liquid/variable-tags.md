---
title: Variable Tags für ein Portal verwenden | MicrosoftDocs
description: Lesen Sie mehr zu den verfügbaren variablen Tags im Portal
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: cdccf267000247a7363a05f72c3ccdd93abb6fd6
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2866265"
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
