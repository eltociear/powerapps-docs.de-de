---
title: Konfigurieren eines Umleitungs Schritts Typs für ein Portal | MicrosoftDocs
description: Anweisungen zum Hinzufügen und Konfigurieren eines Umleitungs Schritts für ein Portal.
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
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553507"
---
# <a name="add-a-redirect-step-type"></a>Umleitungs Schritttyp hinzufügen

Der Umleitungs Schritt ermöglicht eine Umleitung der Browsersitzung des Benutzers zu einer anderen Seite im Portal oder zu einer externen URL. Dies ist nützlich, um Flow nahtlos zu leiten.

| Name                                                            | Beschreibung                                                                                                                                                                                  |
|-----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Externe URL                                                    | Erfordert bei erfolgreicher Umleitung eine Umleitung. Geben Sie eine URL für eine externe Ressource im Web an.                                                                                                       |
| oder Webseite                                                     | Erfordert bei erfolgreicher Umleitung eine Umleitung. Wählen Sie eine Webseite auf der aktuellen Website aus.                                                                                                             |
| Vorhandene Abfrage Zeichenfolge anfügen                                    | Erfordert bei erfolgreicher Umleitung eine Umleitung. Wenn diese Option aktiviert ist, werden die vorhandenen Abfrage Zeichen folgen Parameter der Ziel-URL vor der Umleitung hinzugefügt.                                                 |
| Datensatz-ID an Abfrage Zeichenfolge anfügen                                | Erfordert bei erfolgreicher Umleitung eine Umleitung. Wenn diese Option aktiviert ist, wird die ID des erstellten Datensatzes an die Abfrage Zeichenfolge der URL angehängt, an die umgeleitet wird.                                               |
| Name der Abfrage Zeichenfolge für Datensatz-ID                           | Erfordert bei erfolgreicher Umleitung eine Umleitung. Der Name des ID-Parameters in der Abfrage Zeichenfolge der URL, an die umgeleitet wird.                                                                        |
| Benutzerdefinierte Abfrage Zeichenfolge anfügen                                      | Erfordert bei erfolgreicher Umleitung eine Umleitung. Eine benutzerdefinierte Zeichenfolge, die an die vorhandene Abfrage Zeichenfolge der Umleitungs-URL angefügt werden kann.                                                                  |
| Attribut Wert an Abfrage Zeichenfolge anfügen-Parameter Name         | Erfordert bei erfolgreicher Umleitung eine Umleitung. Ein Name, der an den Parameter übergeben wird, der mit dem Attribut Wert der Ziel Entität korreliert, der an die Abfrage Zeichenfolge der Umleitungs-URL angefügt wird. |
| Attribut Wert an Abfrage Zeichenfolge anfügen-logischer Name des Attributs | Erfordert bei erfolgreicher Umleitung eine Umleitung. Ein logischer Name eines Attributs in der Ziel Entität, um den Wert zu erhalten, der an die Abfrage Zeichenfolge der Umleitungs-URL angehängt werden soll.                            |

### <a name="see-also"></a>Siehe auch

[Konfigurieren eines Portals](configure-portal.md)  
[Definieren von Entitäts Formularen](entity-forms.md)  
[Webformular Schritte für Portale](web-form-steps.md)  
[Auslastungs Formular/Lade Registerkarten-Schritttyp](load-form-step.md)  
[Bedingter Schritttyp](add-conditional-step.md)  
[Hinzufügen benutzerdefinierter JavaScript](add-custom-javascript.md)  

