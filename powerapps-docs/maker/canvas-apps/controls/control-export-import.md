---
title: 'Export-Steuerelement und Import-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispielen, über das Export-Steuerelement und das Import-Steuerelement
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/09/2020
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5d5144db3147defa43c5e11cb169a6ebc9b02105
ms.sourcegitcommit: a02b20113164acb11955d27ef4ffa421ee0fba9d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "78970970"
ms.PowerAppsDecimalTransform: true
---
# <a name="export-control-and-import-control-in-power-apps"></a>Exportieren von Steuerelement und Import-Steuerelement in powerapps
Steuerelemente zum Exportieren von Daten in eine lokale Datei und zum anschließenden Importieren dieser Daten in eine andere app in powerapps.

## <a name="description"></a>Beschreibung
Wenn Sie mehrere Apps erstellen möchten, die die gleichen Daten verwenden, diese Daten jedoch nicht außerhalb dieser Apps freigeben möchten, können Sie sie mit dem **Export**-Steuerelement und dem **Import**-Steuerelement exportieren bzw. importieren. Wenn Sie Daten exportieren, erstellen Sie eine komprimierte Datei, die Sie auf einen anderen Computer kopieren können, aber Sie können Sie nicht in einem anderen Programm als powerapps lesen.

## <a name="warning"></a>Warnung
Das Aktivieren dieser Funktion in Ihrer App kann Sicherheitslücken und Datenlecks verursachen.  Sie sollten die Benutzer anweisen, nur bekannte und vertrauenswürdige Dateien zu importieren und nur Daten zu exportieren, die nicht vertraulich oder sensibel sind.

## <a name="limitations"></a>Einschränkungen
Die Exportfunktion wird in Webbrowsern nicht unterstützt.

## <a name="key-properties"></a>Haupteigenschaften
**Data** – Der Name einer Sammlung, die Sie in eine lokale Datei exportieren möchten.

* Die **Data**-Eigenschaft ist für **Export**-Steuerelemente, jedoch nicht für **Import**-Steuerelemente verfügbar.

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[Align](properties-text.md)** – Die Position von Text in Relation zur horizontalen Mitte des Steuerelements.

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[Color](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement.

**[DisplayMode](properties-core.md)** : Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[DisabledBorderColor](properties-color-border.md)** : Die Farbe des Steuerelementrahmens, wenn die **[DisplayMode](properties-core.md)** -Eigenschaft des Steuerelements auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisabledColor](properties-color-border.md)** : Die Farbe des Texts in einem Steuerelement, wenn seine **[DisplayMode](properties-core.md)** -Eigenschaft auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisabledFill](properties-color-border.md)** : Die Hintergrundfarbe eines Steuerelements, wenn dessen **[DisplayMode](properties-core.md)** -Eigenschaft auf **Disabled** (Deaktiviert) festgelegt ist.

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[FocusedBorderColor](properties-color-border.md)** : die Rahmenfarbe eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[FocusedBorderThickness](properties-color-border.md)** : die Rahmendicke eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[Font](properties-text.md)** – Der Name der Schriftfamilie des angezeigten Texts.

**[FontWeight](properties-text.md)** – Die Schriftbreite des Texts in einem Steuerelement: **Bold** (Fett), **Semibold** (Halbfett), **Normal** oder **Lighter** (Heller).

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[HoverBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über das Steuerelement hält.

**[HoverColor](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement, wenn der Benutzer den Mauszeiger über ihm hält.

**[HoverFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über ihm hält.

**[Italic](properties-text.md)** – Legt fest, ob der Text in einem Steuerelement kursiv formatiert ist.

**[Padding](properties-size-location.md)** – Der Abstand zwischen dem Text auf einer Import- oder Exportschaltfläche und den Rändern der Schaltfläche.

**[PressedBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[PressedColor](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[PressedFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[RadiusBottomLeft](properties-size-location.md)** – Der Grad der Rundung der linken unteren Ecke eines Steuerelements.

**[RadiusBottomRight](properties-size-location.md)** – Der Grad der Rundung der rechten unteren Ecke eines Steuerelements.

**[RadiusTopLeft](properties-size-location.md)** – Der Grad der Rundung der linken oberen Ecke eines Steuerelements.

**[RadiusTopRight](properties-size-location.md)** – Der Grad der Rundung der rechten oberen Ecke eines Steuerelements.

**[Size](properties-text.md)** – Der Schriftgrad des Texts, der in einem Steuerelement angezeigt wird.

**[Strikethrough](properties-text.md)** – Legt fest, ob der in einem Steuerelement angezeigte Text durchgestrichen ist.

**[TabIndex](properties-accessibility.md)** : Navigationsreihenfolge der Tastatur in Bezug auf andere Steuerelemente.

**[Text](properties-core.md)** – Text, der in einem Steuerelement angezeigt wird oder von einem Benutzer in ein Steuerelement eingegeben wird.

**[Underline](properties-text.md)** – Legt fest, ob der in einem Steuerelement angezeigte Text unterstrichen ist.

**[VerticalAlign](properties-text.md)** – Die Position des Texts in einem Steuerelement in Relation zur vertikalen Mitte des Steuerelements.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="example"></a>Beispiel
1. Fügen Sie ein **[Button](control-button.md)** -Steuerelement (Schaltfläche) hinzu, und legen Sie seine **[OnSelect](properties-core.md)** -Eigenschaft auf diese Formel fest: <br>
   ```
   ClearCollect(Products, {Name:"Europa", Price:"10.99"}, {Name:"Ganymede", Price:"12.49"}, {Name:"Callisto", Price:"11.79"})
   ```
   Weitere Informationen finden Sie unter [hinzufügen, benennen und Konfigurieren eines Steuer](../add-configure-controls.md)Elements, **[clearcollect](../functions/function-clear-collect-clearcollect.md)** und [andere Funktionen](../formula-reference.md).
2. Drücken Sie F5, und wählen Sie **[Button](control-button.md)** -Steuerelement aus. Drücken Sie dann ESC.
3. Fügen Sie ein **Export**-Steuerelement hinzu, und legen Sie seine **Data**-Eigenschaft auf **Products** fest.
4. Drücken Sie F5, und wählen Sie das Steuerelement **exportieren** aus, um die Datei *Data. zip*herunterzuladen.
5. Wählen Sie **Speichern**aus, und drücken Sie dann ESC, um zum Standard Arbeitsbereich zurückzukehren.
6. Fügen Sie in einer neuen oder vorhandenen App ein **Import**-Steuerelement hinzu, benennen Sie es mit **MyData**, und legen Sie seine **[OnSelect](properties-core.md)** -Eigenschaft auf diese Formel fest:<br>
   **Collect(ImportedProducts; MyData.Data)**
7. Drücken Sie F5, und wählen Sie **MyData**aus. Wählen Sie dann die exportierte Datei aus, und wählen Sie dann **Öffnen**aus.
8. Drücken Sie ESC, wählen Sie im Menü **Datei** die Option **Sammlungen** aus, und vergewissern Sie sich, dass die aktuelle APP die Daten enthält, die Sie exportiert haben.


## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit
Es gelten dieselben Richtlinien wie für **[Schaltflächen](control-button.md)** , da **Export** und **Import** nur besondere Schaltflächen sind.
