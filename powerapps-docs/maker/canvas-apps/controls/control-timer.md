---
title: 'Timer-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, über das Timer-Steuerelement
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/25/2016
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5d20e2324f2efb4f866ed4fc183f289733c10a41
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61560465"
---
# <a name="timer-control-in-powerapps"></a>Timer-Steuerelement in PowerApps
Ein Steuerelement, das bestimmen kann, wie Ihre App reagiert, wenn eine gewisse Zeit verstrichen ist.

## <a name="description"></a>Beschreibung
Timer können, z.B. bestimmen, wie lange ein Steuerelement angezeigt wird, oder andere Eigenschaften eines Steuerelements ändern, nachdem eine bestimmte Zeit verstrichen ist.

> [!NOTE]
> Führen in PowerApps Studio Zeitgeber nur im Vorschaumodus.


## <a name="key-properties"></a>Haupteigenschaften
**Duration**: Gibt an, wie lange ein Timer ausgeführt wird (in Millisekunden).  Es gibt keinen Höchstwert.

**OnTimerEnd**: Wie eine App beim Beenden der Ausführung eines Timers reagiert.

**Repeat**: Ob ein Timer beim Beenden der Ausführung automatisch neu gestartet wird.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[Align](properties-text.md)** – Die Position von Text in Relation zur horizontalen Mitte des Steuerelements.

**AutoPause**: Gibt an, ob das Timersteuerelement automatisch angehalten wird, wenn der Benutzer zu einem anderen Bildschirm navigiert.

**AutoStart**: Gibt an, ob das Timersteuerelement automatisch wiedergegeben wird, wenn der Benutzer zu dem Bildschirm navigiert, der das Steuerelement enthält.

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[Color](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[DisabledBorderColor](properties-color-border.md)**: Die Farbe des Steuerelementrahmens, wenn die **[DisplayMode](properties-core.md)**-Eigenschaft des Steuerelements auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisabledColor](properties-color-border.md)**: Die Farbe des Texts in einem Steuerelement, wenn seine **[DisplayMode](properties-core.md)**-Eigenschaft auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisabledFill](properties-color-border.md)**: Die Hintergrundfarbe eines Steuerelements, wenn dessen **[DisplayMode](properties-core.md)**-Eigenschaft auf **Disabled** (Deaktiviert) festgelegt ist.

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[FocusedBorderColor](properties-color-border.md)**: die Rahmenfarbe eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[FocusedBorderThickness](properties-color-border.md)**: die Rahmendicke eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[Font](properties-text.md)** – Der Name der Schriftfamilie des angezeigten Texts.

**[FontWeight](properties-text.md)**  – die Schriftbreite des Texts in einem Steuerelement: **Fett**, **Semibold**, **Normal**, oder **heller**.

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

**Start**: Gibt an, ob der Timer gestartet wird.

**[Strikethrough](properties-text.md)** – Legt fest, ob der in einem Steuerelement angezeigte Text durchgestrichen ist.

**[TabIndex](properties-accessibility.md)**: Navigationsreihenfolge der Tastatur in Bezug auf andere Steuerelemente.

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

### <a name="animate-a-control"></a>Animieren eines Steuerelements
1. Fügen Sie einen Timer hinzu, und nennen Sie ihn **FadeIn**.

    Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen, benennen und konfigurieren](../add-configure-controls.md)?
2. Legen Sie für diese Eigenschaften des Timers Folgendes fest: **Dauer** = **5000**, **Wiederholen** = **TRUE** und **[Text](properties-core.md)** = **Toggle animation** (Umschalter-Animation).
3. (optional) Erhöhen Sie die Lesbarkeit des Timers durch Festlegen seiner Eigenschaft **[Height](properties-size-location.md)** auf **160**, seiner Eigenschaft **[Width](properties-size-location.md)** auf **600**, und seiner Eigenschaft **[Size](properties-text.md)** auf **60**.
4. Fügen Sie eine Bezeichnung hinzu, und legen Sie deren Eigenschaft **[Text](properties-core.md)** auf **Welcome!** fest und legen Sie dessen Eigenschaft **[Color](properties-color-border.md)** auf diese Formel fest:
   <br>**ColorFade(Color.BlueViolet, FadeIn.Value/5000)**

    Benötigen Sie weitere Informationen zur **[ColorFade](../functions/function-colors.md)**-Funktion oder [anderen Funktionen](../formula-reference.md)?

5. Klicken Sie auf die Timer-Schaltfläche, um die Animation zu starten oder zu beenden. Der Text in der Bezeichnung wird weiß, kehrt zur vollständigen Intensität zurück und wiederholt den Prozess.

## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit
Dieselben Richtlinien wie für die **[Schaltfläche](control-button.md)** Steuerelement gelten für die **Timer** steuern, wenn der Benutzer mit ihr interagieren können.

### <a name="background-timers"></a>Hintergrund-Timer
Hintergrund-Zeitgeber automatisch ausgeführt und sind ausgeblendet. Verwenden sie eine untergeordnete Rolle, wobei die verstrichene Zeit von geringem Interesse an den Benutzer. Sie können z. B. einmal pro Minute Daten zu aktualisieren oder eine Meldung nur für einen bestimmten Zeitraum anzeigen.

Hintergrund-Timer müssen ihre **[Visible](properties-core.md)** Eigenschaft auf False festgelegt, damit sie von allen Benutzern ausgeblendet sind.

### <a name="timing-considerations"></a>Timing-Überlegungen
Wenn eine **Timer** führt automatisch, überlegen Sie, ob es sich bei Benutzer haben ausreichend Zeit zum Lesen und reagieren bleibt. Tastatur und Bildschirm-Reader-Benutzern möglicherweise mehr Zeit, um auf ein zeitlich festgelegtes Ereignis zu reagieren.

Eine der folgenden Vorgehensweisen ist ausreichend:
* Ermöglicht Benutzern die zeitlich begrenzte Ereignis abzubrechen.
* Ermöglicht Benutzern das Zeitlimit anzupassen, bevor sie beginnt.
* Warnen Sie 20 Sekunden vor Ablauf des Zeitlimits und bieten Sie eine einfache Möglichkeit, um den Grenzwert zu erweitern.

Einige Szenarios sind von diesen Anforderungen ausgenommen. Weitere Informationen finden Sie in der englischsprachigen [WCAG 2.0-Richtlinie für Zeitlimits](https://www.w3.org/TR/WCAG20/#time-limits).

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe
* Wenn Sie Änderungen auf dem aktuellen Bildschirm von ein Timer ausgelöst wird, verwenden Sie eine [dynamischen Bereichs](../accessible-apps-live-regions.md) Sprachausgabe Benutzern mitteilen, was sich geändert.

    > [!NOTE]
    > Wenn der Zeitgeber sichtbar ist und ausgeführt wird, wird die verstrichene Zeit alle fünf Sekunden die Sprachausgabe.

* Verwenden Sie nicht die **[Text](properties-core.md)** Eigenschaft eines Steuerelements für zeitkritische und wichtige Informationen. Wird nicht die Sprachausgabe Änderungen  **[Text](properties-core.md)**.
* Für interaktive Timer:
    * Die **[Text](properties-core.md)**-Eigenschaft muss vorhanden sein.
    * Erwägen Sie eine **[Bezeichnung](control-text-box.md)** -Steuerelement an die verstrichene Zeit. Mithilfe des **[Text](properties-core.md)** Eigenschaft, um den Benutzer anweisen, starten oder Beenden des Zeitgebers.
