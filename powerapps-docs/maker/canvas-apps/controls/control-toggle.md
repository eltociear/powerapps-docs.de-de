---
title: 'Umschalten-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, über das Umschalten-Steuerelement
services: ''
suite: powerapps
documentationcenter: na
author: fikaradz
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/25/2016
ms.author: fikaradz
ms.openlocfilehash: dac1f8ea99746f04d2d3305e279a4bc5faf67903
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="toggle-control-in-powerapps"></a>Umschalten-Steuerelement in PowerApps
Ein Steuerelement, das die Benutzer durch Verschieben des Handles aktivieren oder deaktivieren können.

## <a name="description"></a>Beschreibung
Umschalten wurde für aktuelle GUIs entwickelt, verhält sich jedoch genauso wie ein Kontrollkästchen.

## <a name="key-properties"></a>Haupteigenschaften
**[Default](properties-core.md)** – Der Anfangswert eines Steuerelements, bevor es vom Benutzer geändert wird.

**[Value](properties-core.md)**: Gibt den Wert des Eingabesteuerelements an.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[FocusedBorderThickness](properties-color-border.md)** – Die Rahmenstärke eines Steuerelements, wenn es den Tastaturfokus besitzt.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[DisabledBorderColor](properties-color-border.md)**: Die Farbe des Steuerelementrahmens, wenn die **[DisplayMode](properties-core.md)**-Eigenschaft des Steuerelements auf **Disabled** (Deaktiviert) festgelegt ist.

**FalseFill**: Die Füllfarbe der Umschaltfläche, wenn sie deaktiviert ist.

**FalseHoverFill**: Die Hoverfüllfarbe der Umschaltfläche, wenn sie deaktiviert ist.

**FalseText**: Der Text, der angezeigt wird, wenn die Umschaltfläche deaktiviert ist.

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[HoverBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über das Steuerelement hält.

**[OnChange](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer den Wert eines Steuerelements ändert (z.B. per Schieberegler).

**OnCheck**: Wie eine App reagiert, wenn sich der Wert eines Kontrollkästchens oder von Umschalten auf **TRUE** ändert.

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**OnUncheck**: Wie eine App reagiert, wenn sich der Wert eines Kontrollkästchens oder von Umschalten auf **FALSE** ändert.

**[PressedBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**RailFill**: Die Farbe des Hintergrunds des Rechtecks im Umschalten-Steuerelement, wenn sein Wert **FALSE** ist, oder die Farbe der Linie auf der rechten Seite des Handles in einem Schieberegler-Steuerelement.

**RailHoverFill**: Wenn Sie auf das Umschalten-Steuerelement oder den Schieberegler zeigen: Die Farbe des Hintergrunds des Rechtecks im Umschalten-Steuerelement, wenn sein Wert **false** ist, oder die Farbe der Linie auf der rechten Seite des Handles in einem Schieberegler-Steuerelement.

**[Reset](properties-core.md)** – Legt fest, ob ein Steuerelement auf seinen Standardwert zurückgesetzt wird.

**ShowLabel**: Gibt an, ob neben dem Umschalt-Steuerelement eine Textbezeichnung angezeigt werden soll.

**[TabIndex](properties-accessibility.md)** – Passt die Aktivierreihenfolge von Steuerelementen zur Laufzeit an, wenn sie auf einen Wert ungleich 0 festgelegt wird.

**TextPosition**: Gibt an, ob sich die Bezeichnung links oder rechts neben dem Umschalt-Steuerelement befindet.

**[Tooltip](properties-core.md)**: Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

**TrueFill**: Die Füllfarbe der Umschaltfläche, wenn sie aktiviert ist.

**TrueHoverFill**: Die Hoverfüllfarbe der Umschaltfläche, wenn sie aktiviert ist.

**TrueText**: Der Text, der angezeigt wird, wenn die Umschaltfläche aktiviert ist.

**ValueFill**: Die Farbe des Hintergrunds des Rechtecks im Umschalten-Steuerelement, wenn sein Wert **true** ist, oder die Farbe der Linie auf der linken Seite des Handles in einem Schieberegler-Steuerelement.

**ValueHoverFill**: Wenn Sie mit dem Mauszeiger auf das Umschalten-Steuerelement oder den Schieberegler zeigen: Die Farbe des Hintergrunds des Rechtecks im Umschalten-Steuerelement, wenn sein Wert **TRUE** ist, oder die Farbe der Linie auf der linken Seite des Handles in einem Schieberegler-Steuerelement.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="related-functions"></a>Verwandte Funktionen
[**If**( *Condition*, *Result* )](../functions/function-if.md)

## <a name="example"></a>Beispiel
1. Fügen Sie Umschalten hinzu, und nennen Sie es **MemberDiscount**.

    Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen, benennen und konfigurieren](../add-configure-controls.md)?
2. Fügen Sie eine Bezeichnung hinzu, und legen Sie deren Eigenschaft **[Text](properties-core.md)** auf diese Funktion fest:
   <br>**If(MemberDiscount.Value = true, "Preis: $75", "Preis: $100")**

    Benötigen Sie weitere Informationen zur **[If](../functions/function-if.md)**-Funktion oder [anderen Funktionen](../formula-reference.md)?
3. Drücken Sie F5, und ändern Sie den Wert der **MemberDiscount**.

    Die Bezeichnung zeigt einen anderen Preis, je nachdem, ob **MemberDiscount** aktiviert oder deaktiviert ist.
4. Drücken Sie ESC, um zum Standardarbeitsbereich zurückzukehren.