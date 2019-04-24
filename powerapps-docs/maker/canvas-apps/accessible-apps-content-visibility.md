---
title: Anzeigen oder Ausblenden von Inhalt von hilfstechnologien in Canvas-apps | Microsoft-Dokumentation
description: Techniken nur für sehbehinderte Benutzer oder nur für Benutzer der Sprachausgabe für Canvas-apps nur Inhalt anzeigen
author: tahoon-ms
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.date: 10/22/2018
ms.author: tahoon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c680767bc6a56f0596eba03dd555c1c9a0205346
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61550086"
---
# <a name="show-or-hide-content-from-assistive-technologies-for-canvas-apps"></a>Anzeigen oder Ausblenden von Inhalt von hilfstechnologien für Canvas-apps

Klicken Sie in den meisten Fällen alle Benutzer sollten in der Lage, alle Inhalte zugreifen, aber möchten Sie möglicherweise gelegentlich Inhalt nur für sehbehinderte Benutzer oder nur für Benutzer der Sprachausgabe angezeigt. Beispielsweise sollten Sie nur Sprachausgabe-Benutzer auf eine Beschreibung der liniendiagrammtrends zugreifen, die für sehbehinderte Benutzer offensichtlich sind. Sie sollten auch die Symbolgröße Benutzer der Sprachausgabe ausgeblendet werden soll, wenn eine angrenzende Bezeichnung beschrieben. Eine weitere Beschreibung, die auf das Symbol wäre unnötig ausführlich.

## <a name="hide-content-from-all-users"></a>Ausblenden von Inhalt von allen Benutzern

* Legen Sie **[Visible](controls/properties-core.md)** auf "false".

## <a name="hide-content-from-sighted-users-and-show-it-to-screen-reader-users"></a>Ausblenden von Inhalten für sehbehinderte Benutzer aus, und zeigen Sie sie für Benutzer der Sprachausgabe

Verwenden Sie eine der folgenden Methoden:

* Legen Sie **[Größe](controls/properties-text.md)** auf 0.
* Legen Sie **[Breite](controls/properties-size-location.md)** und **[Höhe](controls/properties-size-location.md)** auf 1.
* Legen Sie  **[X](controls/properties-size-location.md)**,  **[Y](controls/properties-size-location.md)**, oder beide Eigenschaften so, dass das Steuerelement außerhalb des Bildschirms.
* Legen Sie **[Farbe](controls/properties-color-border.md)** zugehörigen Eigenschaften transparent.
* Position ein Rechtecks **[Form](controls/control-shapes-icons.md)** über den Inhalt, und klicken Sie auf Gruppe **[füllen](controls/properties-color-border.md)** auf die gleiche Farbe wie die Hintergrundfarbe des Bildschirms.

> [!NOTE]
> Benutzer können weiterhin eine Tastatur verwenden, eine interaktive Steuerung, wie z. B. den Zugriff auf eine  **[Schaltfläche](controls/control-button.md)**, auch wenn Sie es ausblenden, indem Sie eine der Methoden in der vorherigen Liste. Legen Sie **[TabIndex](controls/properties-accessibility.md)** , 1, wenn Sie, um zu verhindern, dass Benutzer Zugriff auf das Steuerelement durch Drücken der Tab-Taste möchten.

## <a name="hide-content-from-screen-reader-users-and-show-it-to-sighted-users"></a>Ausblenden von Inhalten für Benutzer der Sprachausgabe und für sehbehinderte Benutzer anzeigen

* Für  **[Image](controls/control-image.md)**,  **[Symbol](controls/control-shapes-icons.md)**, und **[Form](controls/control-shapes-icons.md)** Steuerelemente festlegen **[AccessibleLabel](controls/properties-accessibility.md)** auf eine leere Zeichenfolge "".

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie mehr über [Eigenschaften von Bedienungshilfen](controls/properties-accessibility.md) von Steuerelementen in Canvas-apps.
