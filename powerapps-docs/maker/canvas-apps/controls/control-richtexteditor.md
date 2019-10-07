---
title: Referenz zum Rich-Text-Editor-Steuerelement | Microsoft-Dokumentation
description: Informationen über das Rich-Text-Editor-Textsteuerelement, einschließlich Eigenschaften und Beispielen
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/24/2018
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c6b94f636ebf6d373c3fc2117b589116b5a4a2fd
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71986363"
---
# <a name="rich-text-editor-control-in-powerapps"></a>Rich-Text-Editor-Steuerelement in powerapps
Ermöglicht Endbenutzern das Formatieren von Text in einem WYSIWYG-Bearbeitungsbereich.  Die Ausgabe erfolgt im HTML-Format.

## <a name="description"></a>Beschreibung
Das **Rich-Text-Editor**-Steuerelement stellt für den App-Benutzer einen WYSIWYG-Bearbeitungsbereich zum Formatieren von Text bereit.  Die Eingaben und Ausgaben des Steuerelements erfolgen im HTML-Format.

Sie können (z.B. aus einem Webbrowser oder aus Word) kopierten Rich-Text in das Steuerelement einfügen.  

Das Steuerelement soll zum Formatieren von Text verwendet werden. Es wird nicht garantiert, dass die Integrität der HTML-Eingabe erhalten bleibt.  Sämtliche Skript-, Stil- und Objektmarkierungen sowie andere Markierungen, die Probleme hervorrufen könnten, werden vom Editor entfernt.  D.h., wenn Rich-Text außerhalb von PowerApps erstellt wurde, sieht er möglicherweise nicht so aus wie in dem Produkt, in dem er erstellt wurde.

Derzeit werden die folgenden Features unterstützt:
- Fett, kursiv, unterstrichen
- Textfarbe, Hervorhebungsfarbe
- Textgröße
- Nummerierte Listen, Aufzählungen
- Hyperlinks
- Formatierung löschen

Wenn Sie das Steuerelement innerhalb eines Formulars verwenden möchten, klicken Sie auf die Karte „Mehrzeiligen Text bearbeiten“, und passen Sie dieses an, indem Sie das RTE-Steuerelement einfügen.

## <a name="key-properties"></a>Haupteigenschaften
**[Standard:](properties-core.md)** Eingabeeigenschaft für den ersten Textwert, der im Editor angezeigt wird.

**HtmlText:** Ausgabeeigenschaft für den entstandenen Rich-Text im HTML-Format.


## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[AccessibleLabel](properties-accessibility.md)** : Bezeichnung für Sprachausgaben Sollte den Zweck dieser Anlagen beschreiben.

**[DisplayMode](properties-core.md)** : Legt fest, ob das Steuerelement das Hinzufügen und Löschen von Dateien zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[TabIndex](properties-accessibility.md)** : Navigationsreihenfolge der Tastatur in Bezug auf andere Steuerelemente.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (oder des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (oder des Bildschirms, wenn kein übergeordneter Container vorhanden ist).


## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit
### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe
* **[AccessibleLabel](properties-accessibility.md)** muss vorhanden sein.

### <a name="keyboard-support"></a>Tastaturunterstützung
* **[TabIndex](properties-accessibility.md)** muss gleich 0 (null) oder größer sein, damit Tastaturbenutzer dorthin navigieren können.

> [!TIP]
> Verwenden Sie **alt + 0** , während der Editor fokussiert ist, um mehr über andere Tastenkombinationen zu erfahren.