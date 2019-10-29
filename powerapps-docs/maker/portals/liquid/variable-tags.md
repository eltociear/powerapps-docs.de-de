---
title: Verwenden von Variablen Tags für ein Portal | MicrosoftDocs
description: Weitere Informationen zu Variablen Tags, die im Portal verfügbar sind
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: fa375909ad3e909e70b3477d4e7ba0f24691fc0c
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72974412"
---
# <a name="variable-tags"></a>Variablentags

Variablen Tags werden zum Erstellen neuer Liquid-Variablen verwendet.

## <a name="assign"></a>einräumen

Erstellt eine neue Variable. Zuweisungen können auch [Filter](liquid-filters.md) verwenden, um den Wert zu ändern.  

**Ordnung**

```
{% assign is_valid = true %}

{% if is_valid %}

It is valid.

{% endif %}

{% assign name = dave bowman' | upcase %}

{{ name }}
```

**Ausgeben**

```
It is valid.

DAVE BOWMAN
```

## <a name="capture"></a>einver

Erfasst den Inhalt innerhalb seines Blocks und weist ihn einer Variablen zu. Dieser Inhalt kann später mithilfe von Ausgabe Tags gerendert werden.

**Ordnung**

```
{% capture hello %}Hello, {{ user.fullname }}.{% endcapture %}

{{ hello }}

{{ hello }}
```

**Ausgeben**

```
Hello, DAVE BOWMAN.

Hello, DAVE BOWMAN.
```

### <a name="see-also"></a>Siehe auch

[Ablauf Steuerungs Tags](control-flow-tags.md)<br>
[Iterations Tags](iteration-tags.md)<br>
[Vorlagen Tags](template-tags.md)<br>
[Powerapps Common Data Service-Entitäts Tags](portals-entity-tags.md)
