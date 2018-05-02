---
title: 'PDF-Viewer-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, zum PDF-Viewer-Steuerelement
documentationcenter: na
author: fikaradz
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 10/25/2016
ms.author: fikaradz
ms.openlocfilehash: e52f89f685aeb9c06678b973e926c0fd89bdf47f
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="pdf-viewer-control-experimental-in-powerapps"></a>PDF-Viewer-Steuerelement in PowerApps (experimentell)
Ein experimentelles Steuerelement, das den Inhalt einer PDF-Datei anzeigt.

## <a name="description"></a>Beschreibung
Zeigen Sie Text, Grafiken und anderen Inhalt in einer PDF-Datei an, indem Sie diese Art von Steuerelement hinzufügen und seine **Document**-Eigenschaft auf die URL der Datei festlegen, die Sie anzeigen möchten. Verwenden Sie dabei doppelte Anführungszeichen.

## <a name="limitations"></a>Beschränkungen
Beachten Sie, dass der PDF-Viewer aufgrund der Sicherheitsarchitektur PowerApps nur HTTPS-Links und nicht HTTP unterstützt.  
Wenn sich das PDF-Dokument auf einem Server mit restriktiven CORS-Einstellungen befindet, können es möglicherweise nicht in Ihrer App angezeigt werden.  Um dieses Problem zu beheben, muss der Server, der PDF-Dokumente hostet, Cross-Origin-Anfragen (CORS) von powerapps.com zulassen.

Wenn das Dokument in PowerApps nicht geöffnet werden kann, wird dem Endanwender die Option zum Öffnen des Dokuments in einem externen Browser angezeigt.  Diese Option ist auch im Systemmenü für alle externen Dokumente verfügbar.

## <a name="key-properties"></a>Haupteigenschaften
**Document**: gibt die, in doppelten Anführungszeichen gesetzte, URL der PDF-Datei an.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**ActualZoom**: gibt den tatsächlichen Vergrößerungsfaktor des Steuerelements an. Dieser kann sich von dem Faktor unterscheiden, der mit der **Zoom**-Eigenschaft angefordert wurde.

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**CurrentFindText**: gibt den aktuellen Suchbegriff an, der verwendet wird.

**CurrentPage**: gibt die Anzahl der Seiten in einer PDF-Datei an, die tatsächlich angezeigt wird.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[DisabledBorderColor](properties-color-border.md)**: Die Farbe des Steuerelementrahmens, wenn die **[DisplayMode](properties-core.md)**-Eigenschaft des Steuerelements auf **Disabled** (Deaktiviert) festgelegt ist.

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**FindNext**: sucht nach der nächsten Instanz von **FindText** im Dokument.

**FindPrevious**: sucht nach der vorherigen Instanz von **FindText** im Dokument.

**FindText**: gibt den Suchbegriff an, der im Dokument gesucht.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[HoverBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über das Steuerelement hält.

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**OnStateChange**: gibt an, wie eine App reagiert, wenn sich der Zustand des Steuerelements ändert.

**[PaddingBottom](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem unteren Rand des Steuerelements.

**[PaddingLeft](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem linken Rand des Steuerelements.

**[PaddingRight](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem rechten Rand des Steuerelements.

**[PaddingTop](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem oberen Rand des Steuerelements.

**Page**: gibt die Nummer der Seite an, die Sie anzeigen möchten.

**PageCount**: gibt die Anzahl der Seiten in einem Dokument an.

**[PressedBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**ShowControls**: Gibt beispielsweise an, ob für einen Audio- oder Videoplayer eine Schaltfläche für die Wiedergabe und ein Lautstärkeregler und für ein Stift-Steuerelement Symbole zum Zeichnen oder Löschen angezeigt werden.

**[Tooltip](properties-core.md)**: Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**Zoom**: Der Prozentsatz, mit dem ein Bild einer Kamera vergrößert wird (oder die Ansicht einer Datei in einem PDF-Viewer).

## <a name="example"></a>Beispiel
* Fügen Sie ein Steuerelement des Typs **PDF-Viewer** hinzu, und legen Sie seine **Document**-Eigenschaft (in doppelten Anführungszeichen) auf die URL einer PDF-Datei fest, wie im folgenden Beispiel gezeigt:<br>
  **„http://www.who.int/gho/publications/world_health_statistics/EN_WHS2015_TOC.pdf?ua=1“**

    Das Steuerelement zeigt die PDF-Datei.

    Möchten Sie wissen, wie Sie ein [Steuerelement hinzufügen und konfigurieren](../add-configure-controls.md)?


## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit
Es werden nicht alle Barrierefreiheitsfeatures von PDF-Dokumenten unterstützt, da sich der **PDF-Viewer** noch in der Experimentierphase befindet. Daher sollte **ShowControls** auf **TRUE** festgelegt sein, damit Benutzer das Dokument in einer externen Anwendung öffnen können.

Erfahren Sie, wie Sie mithilfe der [WCAG 2.0](https://www.w3.org/TR/WCAG-TECHS/pdf.html)- und [PDF/UA](https://www.pdfa.org/pdfua-the-iso-standard-for-universal-accessibility/)-Standards PDF-Dokumente erstellen können, auf die zugegriffen werden kann.

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe
* Fügen Sie ggf. mithilfe einer **[Bezeichnung](control-text-box.md)** einen Titel hinzu, wenn dem PDF-Dokument noch keiner zugeteilt ist. Der Titel kann direkt vor dem **PDF-Viewer** platziert werden.
