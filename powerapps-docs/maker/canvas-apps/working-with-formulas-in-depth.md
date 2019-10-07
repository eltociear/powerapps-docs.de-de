---
title: Verstehen von Verhaltensformeln in einer Canvas-App | Microsoft-Dokumentation
description: Referenzinformationen zum Arbeiten mit Verhaltensformeln, die den Status von Canvas-Apps in PowerApps ändern
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/10/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 546c19dd0bc767758fcf854e383be0f075717525
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71988000"
---
# <a name="understand-behavior-formulas-for-canvas-apps-in-powerapps"></a>Grundlegendes zu Verhaltensformeln für Canvas-Apps in PowerApps

Die meisten Formeln berechnen einen Wert.  Wie in einer Excel-Tabelle erfolgt die Neuberechnung automatisch, sobald sich Werte ändern.  Wenn ein Wert kleiner als 0 (null) ist, soll das **[Label](controls/control-text-box.md)** -Steuerelement z.B. möglicherweise in Rot, andernfalls in Schwarz angezeigt werden. Dazu können Sie die **[Color](controls/properties-color-border.md)** -Eigenschaft des Steuerelements auf diese Formel festlegen:

**If( Value(TextBox1.Text) >= 0, Color.Black, Color.Red )**

Was bedeutet es in diesem Kontext, wenn der Benutzer ein **[Schaltflächen](controls/control-button.md)** -Steuerelement auswählt?  Da kein Wert geändert wurde, muss nichts neu berechnet werden. Excel bietet kein Äquivalent zu einem **[Schaltfläche](controls/control-button.md)** -Steuerelement.  

Durch Auswahl eines **[Schaltflächen](controls/control-button.md)** -Steuerelements initiiert der Benutzer eine Abfolge von Aktionen oder Verhaltensweisen, die den Status der App ändern werden:

* Ändern Sie den angezeigten Bildschirm: **[Back](functions/function-navigate.md)** -und **[Navigate](functions/function-navigate.md)** -Funktionen.
* Steuern eines [Signals](functions/signals.md): **[Aktivieren](functions/function-enable-disable.md)** und **[Deaktivieren](functions/function-enable-disable.md)** von Funktionen.
* Aktualisieren, aktualisieren oder Entfernen von Elementen in einer [Datenquelle](working-with-data-sources.md): **[Aktualisieren](functions/function-refresh.md)** , **[Aktualisieren](functions/function-update-updateif.md)** , **[updateif](functions/function-update-updateif.md)** , **[Patch](functions/function-patch.md)** , **[Remove](functions/function-remove-removeif.md)** und **[removeif](functions/function-remove-removeif.md)** -Funktionen.
* Aktualisieren einer [Kontext Variablen](working-with-variables.md#use-a-context-variable):  **[Updatecontext](functions/function-updatecontext.md)** -Funktion.
* Erstellen, aktualisieren oder Entfernen von Elementen in einer [Sammlung](working-with-data-sources.md#collections):  **[Collect](functions/function-clear-collect-clearcollect.md)** -, **[Clear](functions/function-clear-collect-clearcollect.md)** -und **[clearcollect](functions/function-clear-collect-clearcollect.md)** -Funktionen.

Da diese Funktionen den Status der App ändern, können sie nicht automatisch neu berechnet werden. Verwenden Sie sie in den Formeln für die **[OnSelect](controls/properties-core.md)** -, **[OnVisible](controls/control-screen.md)** -, **[OnHidden](controls/control-screen.md)** - und anderen **On...** -Eigenschaften, die Verhaltensformeln genannt werden.

### <a name="more-than-one-action"></a>Mehr als eine Aktion
Verwenden Sie Semikolons, um eine Liste von auszuführenden Aktionen zu erstellen. Wenn Sie z.B. eine Kontextvariable aktualisieren und dann zum vorherigen Bildschirm zurückkehren, verwenden Sie diese Formel:

* **updatecontext ({x: 1}); Zurück ()**

Aktionen werden in der Reihenfolge ausgeführt, in der sie in der Formel angezeigt werden.  Die nächste Funktion wird erst gestartet, wenn die aktuelle Funktion abgeschlossen wurde. Wenn ein Fehler auftritt, werden nachfolgende Funktionen möglicherweise nicht gestartet.

