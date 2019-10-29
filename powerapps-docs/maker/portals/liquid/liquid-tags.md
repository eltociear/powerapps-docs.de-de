---
title: Verwenden von Liquid-Tags für ein Portal | MicrosoftDocs
description: Erfahren Sie mehr über die verfügbaren Liquid-Tags in einem Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b04c6447911d1a884627bd2cbb4ad7b74b9c5ce5
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976551"
---
# <a name="available-liquid-tags"></a>Verfügbare Liquid-Tags

Tags bilden die Programmierlogik, die Vorlagen mitteilt, was zu tun ist. Die Tags werden in {%%} umschließt.

```
{% if user.fullname == 'Dave Bowman' %} Hello, Dave. {% endif %}
```

## <a name="whitespace-control"></a>Leerraum-Steuerelement

Normalerweise rendert Liquid alles außerhalb der Variablen-und Tagblöcke ausführlich, wobei der Leerraum unverändert ist. Gelegentlich ist es nicht ratsam, den zusätzlichen Leerraum zu formatieren, aber Sie möchten die Vorlage trotzdem ordnungsgemäß formatieren, was Leerraum erfordert.

Sie können der Engine mitteilen, dass alle führenden oder nachfolgenden Leerzeichen entfernt werden sollen, indem Sie einen Bindestrich (-) zum Start-oder endblocktag hinzufügen.

**Ordnung**

```
{% for i in (1..5) --%}

{{ i }}

{%-- endfor %}
```

**Ausgeben**

```
12345
```
### <a name="see-also"></a>Siehe auch

[Liquid-Typen](liquid-types.md)  
[Liquid-Objekte](liquid-objects.md)  
[Liquid-Filter](liquid-filters.md) 
