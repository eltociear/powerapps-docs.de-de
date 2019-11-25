---
title: Konfigurieren der Schritte eines Webformulars für ein Portal | MicrosoftDocs
description: Anweisungen, einen Internet-Formularschritt für ein Internet-Formular auf einem Portal zu erstellen.
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
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2760439"
---
# <a name="define-web-form-steps-for-portals"></a>Definieren von Webformularschritten für Portale

Der Webformularschritt stellt Flowlogik der Benutzererfahrung des Formulars wie Schritte und Bedingungsverzweigung bereit. Er stellt auch Details zum Rendering eines Formulars und zusätzliche Verhalten bereit.

> [!NOTE]
> Webformulare enthalten den Verlauf der Schritte, die ein Besucher in einem Objekt auf einer Formularsitzungsentität getätigt hat. Wenn ein Webformularschritt abgeändert wurde, könnte der vorgängig erstellte Datenverlauf veraltet sein. Immer wenn Schritte geändert, wird empfohlen, alle Webformularsitzungseinträge zu löschen, um Unstimmigkeiten zischen Schrittsequenzen in Verlauf und aktuellen Sequenzen zu vermeiden.

Jedes Webformular, das im Portal angezeigt wird, besitzt einen oder mehrere Schritte. Diese Schritt haben einige gemeinsame Eigenschaften, wie unten erläutert. Jeder Schritt enthält einen Zeiger (eine Suche) zum nächsten Schritt mit der Ausnahme der letzten Schritte. Letzte Schritte haben keinen nächsten Schritt und stellen deshalb den letzten Schritt in einem Webformular dar (aufgrund der Bedingungsverzweigung kann es mehrere letzte Schritte geben)

![Schritte zum Erstellen eines Webformulars](../media/web-form-creation-steps.png "Schritte zum Erstellen eines Webformulars")  

| Name     | Beschreibung                                    |
|----------|------------------------------------------------|
| Name     | Ein Titel, der als Referenz verwendet wird.                    |
| Webformular | Das Webformular, das dem aktuellen Schritt zugeordnet ist. |
|Typ|Eine der folgenden Komponenten:<br>[Formular laden/Registerkarten-Schritttyp laden](load-form-step.md): zeigt Eigenschaften von Formularen an. <ul><li>[Formular laden/Registerkarten-Schritttyp laden](load-form-step.md): zeigt Eigenschaften von Registerkarte an.</li><li>[Bedingter Schritttyp](add-conditional-step.md): zeigt Eigenschaften für spezifische Ausdrücke an, die für Bedingungsverzweigungen evaluiert werden. </li><li>[Schritttyp umleiten](add-redirect-step.md): zeigt die Einstellungen an, die zum Konfigurieren einer Websiteumleitung erforderlich sind.</li></ul><br>Weitere Details zu den Einstellungen für diese Webformularschrittart finden Sie in den entsprechenden Abschnitten unten.<br>**Hinweis**: Der erste Schritt kann nicht vom Typ „Bedingung” sein.|
| Nächster Schritt                  | Der Schritt, der dem aktuellen Schritt folgt. Ist für ein einzelnes Einzelschrittformular leer.                                                                                                            |
| Logischer Name der Zielentität | Der logische Name der Entität, die dem Formular zugeordnet ist.                                                                                                                                               |
| „Zur vorherigen Option wechseln“ zulässig    | Gibt an, ob der Benutzer die Option hat, in einem Mehrfachschrittformular zum vorherigen Schritt zu navigieren Der Standardwert ist korrekt. Deaktivieren, um zu verhindern, dass der Benutzer zum vorherigen Schritt zurückkehren kann. |
||

### <a name="see-also"></a>Siehe auch

[Ein Portal konfigurieren](configure-portal.md)  
[Entität definieren](entity-forms.md)  
[Schritttyp zum Laden von Formularen/Registerkarten](load-form-step.md)  
[Umleitungsschritttyp](add-redirect-step.md)  
[Bedingter Schritttyp](add-conditional-step.md)  
[Benutzerdefiniertes JavaScript hinzufügen](add-custom-javascript.md)  

