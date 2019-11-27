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
ms.openlocfilehash: fa375909ad3e909e70b3477d4e7ba0f24691fc0c
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2707733"
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
[PowerApps Common Data Service-Entitäts-Tags](portals-entity-tags.md)
