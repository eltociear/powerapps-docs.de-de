---
title: Konfigurieren eines bedingten Schritt Typs für ein Portal | MicrosoftDocs
description: Anweisungen zum Hinzufügen und Konfigurieren eines bedingten Schritt Typs für ein Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: ec3e568b239bf66c0d4554e244d5afef2d5ef673
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553668"
---
# <a name="add-a-conditional-step-type"></a>Fügen Sie einen bedingten Schritttyp hinzu.

Ein Webformular Schritt kann ein "Condition"-Typ sein, der angibt, dass der Schritt einen Ausdruck auswerten soll. Wenn der Ausdruck zu true ausgewertet wird, wird der nächste Schritt angezeigt. Wenn der Ausdruck zu false ausgewertet wird und der "Next Step if Condition"-Wert angegeben wurde, wird dieser Schritt angezeigt. Die aktuelle Entität ist das Ziel, mit dem der Ausdruck ausgewertet wird. Die Daten Satz Quelle ist standardmäßig die Daten Satz Quelle des vorherigen Schritts.

## <a name="attributes"></a>Attribute

| Name                         | Beschreibung                                                                                                                                                                                                                          |
|------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Anlage                    | Der bedingte Ausdruck, der ausgewertet werden soll.                                                                                                                                                                                           |
| Nächster Schritt, wenn die Bedingung fehlschlägt | Der bedingte Schritttyp weist im Gegensatz zu allen anderen zwei Lookups für den nächsten Schritt auf. Der Standardwert für die nächste Schritt Suche wird berücksichtigt, wenn die Bedingung als true ausgewertet wird. Diese Eigenschaft legt den nächsten Schritt fest, wenn die Bedingung als false ausgewertet wird. |

Die folgenden Operanden sind verfügbar:

| Operand (s)    | Typ                   |
|---------------|------------------------|
| =, ==         | Aufbauen                 |
| !=            | Ungleich             |
| &gt;          | Größer als           |
| &lt;          | Kleiner als              |
| &gt;=         | Größer als oder ist |
| &lt;=         | Kleiner als oder ist    |
| &             | And                    |
| \|             | Or                     |
| !             | Not                    |
| =\*, = =\*,-= | mögen                   |
| ! =\*          | Nicht wie               |

## <a name="format"></a>Format

Das Format des Ausdrucks lautet wie folgt:

\[logischer Name des Entitäts Attributs\] \[Operanden\] \[Wert\]

Beispiel:

neuer\_categorycode = 750101

Eine Bedingung kann über mehrere Ausdrücke verfügen. Sie können geschachtelte Ausdrücke mithilfe von Klammern gruppieren, z. b.:

New\_categorycode = 750101 & gendercode = 2

-   New\_categorycode = 750101 & (gendercode = 2 | gendercode = 3)

-   New\_Name = Jane Doe

-   neuer\_twooptionfield = true

-   neuer\_twooptionfield = false

### <a name="see-also"></a>Siehe auch

[Konfigurieren eines Portals](configure-portal.md)  
[Definieren von Entitäts Formularen](entity-forms.md)  
[Webformular Schritte für Portale](web-form-steps.md)  
[Auslastungs Formular/Lade Registerkarten-Schritttyp](load-form-step.md)  
[Umleitungs Schritttyp](add-redirect-step.md)  
[Hinzufügen benutzerdefinierter JavaScript](add-custom-javascript.md)  

