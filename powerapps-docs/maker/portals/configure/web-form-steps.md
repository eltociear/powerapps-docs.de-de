---
title: Konfigurieren von Webformular Schritten für ein Portal | MicrosoftDocs
description: Anweisungen zum Erstellen eines Webformular Schritts für ein Webformular in einem Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: c81cddb771c98ccecf2be206ab45a8271ff3559d
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73551230"
---
# <a name="define-web-form-steps-for-portals"></a>Definieren von Webformular Schritten für Portale

Der Web Form-Schritt bietet die Fluss Logik der Benutzer Darstellung des Formulars, wie z. b. Schritte und bedingte Verzweigungen. Außerdem wurden Details zum Rendern eines Formulars und zusätzliches Verhalten bereitgestellt.

> [!NOTE]
> Web Forms speichert den Verlauf der Schritte, die ein Benutzer in einem Objekt in einer Web Form-Sitzungs Entität besucht hat. Wenn die Schritte eines Webformulars geändert wurden, waren zuvor erstellte Verlaufs Daten möglicherweise veraltet. Wenn die Schritte geändert werden, wird empfohlen, alle Webformular-Sitzungsdaten Sätze zu löschen, um die Fehler Übereinstimmung zwischen der Sequenz von Schritten, die im Verlauf protokolliert wurden, und der aktuellen Sequenz auszuschließen.

Jedes Webformular, das im Portal angezeigt wird, verfügt über einen oder mehrere Schritte. Diese Schritte haben einige allgemeine Eigenschaften, die unten beschrieben werden. Jeder Schritt enthält einen Zeiger (eine Suche) bis zum nächsten Schritt, mit Ausnahme von Terminal Schritten. Terminal Schritte haben nicht das nächste Mal und somit den letzten Schritt des Webformulars (aufgrund der bedingten Verzweigung kann es mehrere Terminal Schritte geben)

![Schritte zum Erstellen eines Webformulars](../media/web-form-creation-steps.png "Schritte zum Erstellen eines Webformulars")  

| Name     | Beschreibung                                    |
|----------|------------------------------------------------|
| Name     | Ein Titel, der als Verweis verwendet wird.                    |
| Webformular | Das Webformular, das dem aktuellen Schritt zugeordnet ist. |
|Typ|Eins der folgenden Elemente:<br>[Auslastungs Formular/Lade Registerkarte (Schritttyp](load-form-step.md)): zeigt Eigenschaften von Formularen an. <ul><li>[Auslastungs Formular/Lade Registerkarte (Schritt](load-form-step.md)): zeigt Eigenschaften von Registerkarten an.</li><li>[Bedingter Schritttyp](add-conditional-step.md): zeigt Eigenschaften zum Angeben von Ausdrücken an, die für die bedingte Verzweigung ausgewertet werden sollen. </li><li>[Umleitungs Schritttyp](add-redirect-step.md): zeigt die Einstellungen an, die zum Konfigurieren einer Website Umleitung geeignet sind.</li></ul><br>Weitere Informationen zu den Einstellungen für diese Web Form-Schritt Typen finden Sie in den entsprechenden Abschnitten weiter unten.<br>**Hinweis**: der erste Schritt kann nicht den Typ "Condition" aufweisen.|
| Nächster Schritt                  | Der Schritt, der dem aktuellen Schritt folgt. Diese Angabe ist für Einzelschritt-Einzel Formulare leer.                                                                                                            |
| Logischer Name der Ziel Entität | Der logische Name der Entität, die dem Formular zugeordnet ist.                                                                                                                                               |
| Vorheriges verschieben    | Gibt an, ob dem Benutzer eine Option zur Navigation zum vorherigen Schritt in einem Webformular mit mehreren Schritten zugewiesen wird. Der Standardwert ist true. Deaktivieren Sie diese Option, um zu verhindern, dass der Benutzer mit dem vorherigen Schritt fortfahren kann. |
||

### <a name="see-also"></a>Siehe auch

[Konfigurieren eines Portals](configure-portal.md)  
[Entität definieren](entity-forms.md)  
[Auslastungs Formular/Lade Registerkarten-Schritttyp](load-form-step.md)  
[Umleitungs Schritttyp](add-redirect-step.md)  
[Bedingter Schritttyp](add-conditional-step.md)  
[Hinzufügen benutzerdefinierter JavaScript](add-custom-javascript.md)  

