---
title: Konfigurieren eines bedingten Schritttyps für ein Portal | MicrosoftDocs
description: Anweisungen, einen bedingten Schritttyp für ein Portal hinzuzufügen und zu konfigurieren.
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
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2760457"
---
# <a name="add-a-conditional-step-type"></a>Hinzufügen eines bedingten Schritttyps

Ein Webformularschritt kann ein Bedingungstyp sein, der angibt, dass der Schritt einen Ausdruck auswerten soll. Wenn der Ausdruck als "true" ausgewertet wird, wird der nächste Schritt angezeigt. Wird der Ausdruck als "false" auswertet und "Nächster Schritt, wenn die Bedingung fehlschlägt" angegeben worden ist, wird diser Schritt angezeigt. Die aktuelle Entität ist das Ziel, das verwendet wird, um den Ausdruck auszuwerten. Als Datensatzquelle wird die Datensatzquelle des vorherigen Schrittes als Standard übernommen.

## <a name="attributes"></a>Attribute

| Name                         | Beschreibung                                                                                                                                                                                                                          |
|------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Bedingung                    | Der Bedingte Ausdruck, der ausgewertet wird                                                                                                                                                                                           |
| Nächster Schritt, wenn die Bedingung fehlschlägt | "Bedingter Schritttyp" besitzt, im Gegensatz zu allen anderen, zwei "Nächster Schritt"-Suchen. Die standardmäßige "Nächster Schritt"-Suche wird berücksichtigt, wenn die Bedingung "true" auswertet. Diese Eigenschaft legt den nächsten Schritt fest, falls die Bedingung "false" auswertet. |

Die verfügbaren Operanden sind wie folgt:

| Operand(en)    | Typ                   |
|---------------|------------------------|
| =, ==         | Gleich                 |
| !=            | Ungleich             |
| &gt;          | Größer als           |
| &lt;          | Kleiner als              |
| &gt;=         | Größer Als oder Gleich |
| &lt;=         | Kleiner oder Gleich    |
| &             | Und                    |
| \|             | Oder                     |
| !             | Nicht                    |
| =\*, ==\*, -= | Wie                   |
| !=\*          | Nicht Wie               |

## <a name="format"></a>Format

Das Format der Ausdrucks ist wie folgt:

\[logischer Name des Entitätsattributs\] \[Operator\] \[Wert\]

Beispiel:

new\_categorycode = 750101

Eine Bedingung kann mehrere Ausdrücke haben. Sie können Klammern verwenden, um geschachtelte Ausdrücke zu gruppieren, beispielsweise:

new\_categorycode = 750101 und gendercode = 2

-   new\_categorycode = 750101 und (gendercode = 2 | gendercode = 3)

-   new\_name = Jane Doe

-   new\_twooptionfield = true

-   new\_twooptionfield = false

### <a name="see-also"></a>Siehe auch

[Ein Portal konfigurieren](configure-portal.md)  
[Entitätsformulare definieren](entity-forms.md)  
[Webformularschritte für Portale](web-form-steps.md)  
[Schritttyp zum Laden von Formularen/Registerkarten](load-form-step.md)  
[Umleitungsschritttyp](add-redirect-step.md)  
[Benutzerdefiniertes JavaScript hinzufügen](add-custom-javascript.md)  

