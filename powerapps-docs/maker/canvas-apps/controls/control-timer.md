---
title: 'Timer-Steuerelement: Referenz | Microsoft-Dokumentation'
description: "Informationen, einschließlich Eigenschaften und Beispiele, über das Timer-Steuerelement"
services: 
suite: powerapps
documentationcenter: na
author: fikaradz
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/25/2016
ms.author: fikaradz
ms.openlocfilehash: 008c992ad3452c1844064335a51593c222fb1ac1
ms.sourcegitcommit: 68eee592c351688e5d0bd458f33a70be507fa53f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2018
---
# <a name="timer-control-in-powerapps"></a>Timer-Steuerelement in PowerApps
Ein Steuerelement, das bestimmen kann, wie Ihre App reagiert, wenn eine gewisse Zeit verstrichen ist.

## <a name="description"></a>Beschreibung
Timer können, z.B. bestimmen, wie lange ein Steuerelement angezeigt wird, oder andere Eigenschaften eines Steuerelements ändern, nachdem eine bestimmte Zeit verstrichen ist.

Beachten Sie, dass Sie die App im Vorschaumodus ausführen müssen, damit der Timer im Designer ausgeführt wird.  Dadurch können Benutzer den Timer ohne zeitliche Einschränkung im Designer konfigurieren.

## <a name="key-properties"></a>Haupteigenschaften
**Duration**: Gibt an, wie lange ein Timer ausgeführt wird (in Millisekunden).  Es gibt keinen Höchstwert.

**OnTimerEnd**: Wie eine App beim Beenden der Ausführung eines Timers reagiert.

**Repeat**: Ob ein Timer beim Beenden der Ausführung automatisch neu gestartet wird.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[Align](properties-text.md)** – Die Position von Text in Relation zur horizontalen Mitte des Steuerelements.

**AutoPause**: Ob ein Audio- oder Videoclip automatisch angehalten wird, wenn der Benutzer zu einem anderen Bildschirm navigiert.

**AutoStart** – Gibt an, ob ein Steuerelement Audio oder Video automatisch einen Clip wiedergibt, wenn der Benutzer zu dem Bildschirm navigiert, der das Steuerelement enthält.

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[Color](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[DisabledBorderColor](properties-color-border.md)**: Die Farbe des Steuerelementrahmens, wenn die **[DisplayMode](properties-core.md)**-Eigenschaft des Steuerelements auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisabledColor](properties-color-border.md)**: Die Farbe des Texts in einem Steuerelement, wenn seine **[DisplayMode](properties-core.md)**-Eigenschaft auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisabledFill](properties-color-border.md)**: Die Hintergrundfarbe eines Steuerelements, wenn dessen **[DisplayMode](properties-core.md)**-Eigenschaft auf **Disabled** (Deaktiviert) festgelegt ist.

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[Font](properties-text.md)** – Der Name der Schriftfamilie des angezeigten Texts.

**[FontWeight](properties-text.md)** – Die Schriftbreite des Texts in einem Steuerelement: **Bold** (Fett), **Semibold** (Halbfett), **Normal** oder **Lighter** (Heller).

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[HoverBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über das Steuerelement hält.

**[HoverColor](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement, wenn der Benutzer den Mauszeiger über ihm hält.

**[HoverFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über ihm hält.

**[Italic](properties-text.md)** – Legt fest, ob der Text in einem Steuerelement kursiv formatiert ist.

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**OnTimerStart**: Wie eine App reagiert, wenn ein Timer mit der Ausführung beginnt.

**[PressedBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[PressedColor](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[PressedFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[Reset](properties-core.md)** – Legt fest, ob ein Steuerelement auf seinen Standardwert zurückgesetzt wird.

**[Size](properties-text.md)** – Der Schriftgrad des Texts, der in einem Steuerelement angezeigt wird.

**Start**: Ob ein Audio- oder Videoclip gespielt wird.

**[Strikethrough](properties-text.md)** – Legt fest, ob der in einem Steuerelement angezeigte Text durchgestrichen ist.

**[Text](properties-core.md)** – Text, der in einem Steuerelement angezeigt wird oder von einem Benutzer in ein Steuerelement eingegeben wird.

**[Tooltip](properties-core.md)**: Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

**[Underline](properties-text.md)** – Legt fest, ob der in einem Steuerelement angezeigte Text unterstrichen ist.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="related-functions"></a>Verwandte Funktionen
[**Refresh**( *DataSource* )](../functions/function-refresh.md)

## <a name="examples"></a>Beispiele
### <a name="show-a-countdown"></a>Anzeigen eines Countdowns
1. Fügen Sie einen Timer hinzu, und nennen Sie ihn **Countdown**.

    Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen, benennen und konfigurieren](../add-configure-controls.md)?
2. Legen Sie die Eigenschaft **Duration** für den Timer auf **10000** und seine Eigenschaften **Repeat** und **Autostart** auf **TRUE** fest.
3. (optional) Erhöhen Sie die Lesbarkeit des Timers durch Festlegen seiner Eigenschaft **[Height](properties-size-location.md)** auf **160**, seiner Eigenschaft **[Width](properties-size-location.md)** auf **600**, und seiner Eigenschaft **[Size](properties-text.md)** auf **60**.
4. Fügen Sie eine Bezeichnung hinzu, und legen Sie deren Eigenschaft **[Text](properties-core.md)** auf diese Funktion fest:
   <br>**"Anzahl verbleibender Sekunden: " & RoundUp(10-Countdown.Value/1000, 0)**

    Benötigen Sie weitere Informationen zur **[If](../functions/function-round.md)**-Funktion oder [anderen Funktionen](../formula-reference.md)?

    Die Bezeichnung zeigt die bis zum Neustart des Timers verbleibenden Sekunden an.
5. (optional) Legen Sie die Eigenschaft **[Visible](properties-core.md)** für den Timer auf **FALSE** fest.

### <a name="animate-a-control"></a>Animieren eines Steuerelements
1. Fügen Sie einen Timer hinzu, und nennen Sie ihn **FadeIn**.

    Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen, benennen und konfigurieren](../add-configure-controls.md)?
2. Legen Sie die Eigenschaft **Duration** für den Timer auf **5000** und seine Eigenschaften **Repeat** und **Autostart** auf **TRUE** fest.
3. (optional) Erhöhen Sie die Lesbarkeit des Timers durch Festlegen seiner Eigenschaft **[Height](properties-size-location.md)** auf **160**, seiner Eigenschaft **[Width](properties-size-location.md)** auf **600**, und seiner Eigenschaft **[Size](properties-text.md)** auf **60**.
4. Fügen Sie eine Bezeichnung hinzu, und legen Sie deren Eigenschaft **[Text](properties-core.md)** auf **Welcome!** fest und legen Sie dessen Eigenschaft **[Color](properties-color-border.md)** auf diese Formel fest:
   <br>**ColorFade(Color.BlueViolet, FadeIn.Value/5000)**

    Benötigen Sie weitere Informationen zur **[ColorFade](../functions/function-colors.md)**-Funktion oder [anderen Funktionen](../formula-reference.md)?

    Der Text in der Bezeichnung wird weiß, kehrt zur vollständigen Intensität zurück und wiederholt den Prozess.
5. (optional) Legen Sie die Eigenschaft **[Visible](properties-core.md)** für den Timer auf **FALSE** fest.
