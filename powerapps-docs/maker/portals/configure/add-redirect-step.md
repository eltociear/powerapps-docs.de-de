---
title: Konfigurieren eines Umleitungsschritt-Typs für ein Portal | MicrosoftDocs
description: Anweisungen, einen Umleitungsschritt für ein Portal hinzuzufügen und zu konfigurieren.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 3cf76cccfd247bdcfb4ee32e99682d2b9e95e139
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2760433"
---
# <a name="add-a-redirect-step-type"></a>Hinzufügen eines Umleitungsschritttyps

Der Umleitungsschritttyp ist eine Umleitung der Browsersitzung des Benutzers zu einer anderen Seite im Portal oder zu einer externen URL. Das ist nützlich für nahtlose Umleitungen.

| Name                                                            | Beschreibung                                                                                                                                                                                  |
|-----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Externe URL                                                    | Erfordert, das "On Success" auf "Redirect" festgelegt ist. Geben Sie eine URL für eine externe Webressource an.                                                                                                       |
| oder Webseite                                                     | Erfordert, das "On Success" auf "Redirect" festgelegt ist. Wählen Sie eine Webseite der aktuellen Webseite aus.                                                                                                             |
| Vorhandene Abfragezeichenfolge anfügen                                    | Erfordert, das "On Success" auf "Redirect" festgelegt ist. Wenn aktiviert werden die vorhandenen Abfragezeichenfolgenparameter zur Ziel-URL vor der Umleitung hinzugefügt.                                                 |
| Datensatz-ID an Abfragezeichenfolge anfügen                                | Erfordert, das "On Success" auf "Redirect" festgelegt ist. Wenn aktiviert, wird die ID des erstellten Datensatzes zur Abfragezeichenfolge der URL an die umgeleitet wird angefügt.                                               |
| Abfragezeichenfolgen-Parametername für Datensatz-ID                           | Erfordert, das "On Success" auf "Redirect" festgelegt ist. Der Name des ID-Parameters in der Abfragezeichenfolge der URL, an die umgeleitet wird.                                                                        |
| Benutzerdefinierte Abfragezeichenfolge anfügen                                      | Erfordert, das "On Success" auf "Redirect" festgelegt ist. Eine benutzerdefinierte Zeichenfolge, die an die Abfragezeichenfolge der Umleitungs-URL angefügt werden kann.                                                                  |
| Attributwert an Abfragezeichenfolge anfügen – Parametername         | Erfordert, das "On Success" auf "Redirect" festgelegt ist. Ein Name für den Parameter, der mit dem Attributwert der Zielentität übereinstimmt, die der Abfragezeichenfolge der Umleitungs-URL angefügt wird. |
| Attributwert an Abfragezeichenfolge anfügen – Logischer Attributname | Erfordert, das "On Success" auf "Redirect" festgelegt ist. Ein logischer Name eines Attributs der Zielentität, um den Wert an die Abfragezeichenfolge der Umleitungs-URL anzufügen.                            |

### <a name="see-also"></a>Siehe auch

[Ein Portal konfigurieren](configure-portal.md)  
[Entitätsformulare definieren](entity-forms.md)  
[Webformularschritte für Portale](web-form-steps.md)  
[Schritttyp zum Laden von Formularen/Registerkarten](load-form-step.md)  
[Bedingter Schritttyp](add-conditional-step.md)  
[Benutzerdefiniertes JavaScript hinzufügen](add-custom-javascript.md)  

