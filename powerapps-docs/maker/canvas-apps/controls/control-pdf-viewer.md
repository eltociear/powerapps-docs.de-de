---
title: 'PDF-Viewer-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, zum PDF-Viewer-Steuerelement
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/10/2020
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a8136fc1ce04ed696aeb68af7139d1b538dd879e
ms.sourcegitcommit: af653cd30f5879fea97a594d458d355fe18f4834
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2020
ms.locfileid: "81223332"
---
# <a name="pdf-viewer-control-experimental-in-power-apps"></a>PDF-Viewer-Steuerelement (experimentell) in powerapps
Ein experimentelles Steuerelement, das den Inhalt einer PDF-Datei anzeigt.

## <a name="description"></a>Beschreibung
Zeigen Sie Text, Grafiken und anderen Inhalt in einer PDF-Datei an, indem Sie diese Art von Steuerelement hinzufügen und seine **Document**-Eigenschaft auf die URL der Datei festlegen, die Sie anzeigen möchten. Verwenden Sie dabei doppelte Anführungszeichen.

## <a name="limitations"></a>Einschränkungen
1. Die Sicherheitsarchitektur von powerapps erfordert, dass der PDF-Viewer nur HTTPS-Links, nicht aber http unterstützt.  

2. Die **Document** -Eigenschaft muss direkt mit der PDF-Datei verknüpft werden. Server Umleitungen oder HTML-Ansichten des Dokuments werden nicht unterstützt.

3. Der Server, der das Dokument hostet, darf keine Authentifizierung erfordern.

4. Möglicherweise sind Sie nicht in der Lage, ein PDF-Dokument in Ihrer APP anzuzeigen, wenn sich das Dokument auf einem Server befindet, der restriktive cors-Einstellungen (Cross-Origin Resource Sharing) aufweist. Um dieses Problem zu beheben, muss der Server, der PDF-Dokumente hostet, Ursprungs übergreifende Anforderungen von powerapps.com zulassen.

App-Benutzer können diese Einschränkungen umgehen, indem Sie PDF-Dokumente in einem externen Browser öffnen, wie Sie dazu aufgefordert werden, wenn das Steuerelement ein Dokument nicht öffnen kann. Diese Option ist auch im Systemmenü für alle externen Dokumente verfügbar.

## <a name="key-properties"></a>Haupteigenschaften
**Document**: gibt die, in doppelten Anführungszeichen gesetzte, URL der PDF-Datei an.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**ActualZoom**: gibt den tatsächlichen Vergrößerungsfaktor des Steuerelements an. Dieser kann sich von dem Faktor unterscheiden, der mit der **Zoom**-Eigenschaft angefordert wurde.

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**CurrentFindText**: gibt den aktuellen Suchbegriff an, der verwendet wird.

**CurrentPage**: gibt die Anzahl der Seiten in einer PDF-Datei an, die tatsächlich angezeigt wird.

**[DisplayMode](properties-core.md)** : Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[DisabledBorderColor](properties-color-border.md)** : Die Farbe des Steuerelementrahmens, wenn die **[DisplayMode](properties-core.md)** -Eigenschaft des Steuerelements auf **Disabled** (Deaktiviert) festgelegt ist.

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**FindNext**: sucht nach der nächsten Instanz von **FindText** im Dokument.

**FindPrevious**: sucht nach der vorherigen Instanz von **FindText** im Dokument.

**FindText**: gibt den Suchbegriff an, der im Dokument gesucht.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[HoverBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über das Steuerelement hält.

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**OnStateChange**: gibt an, wie eine App reagiert, wenn sich der Zustand des Steuerelements ändert.

**[PaddingBottom](properties-size-location.md)** : Der Abstand zwischen dem Text eines Steuerelements und dem unteren Rand des Steuerelements.

**[PaddingLeft](properties-size-location.md)** : Der Abstand zwischen dem Text eines Steuerelements und dem linken Rand des Steuerelements.

**[PaddingRight](properties-size-location.md)** : Der Abstand zwischen dem Text eines Steuerelements und dem rechten Rand des Steuerelements.

**[PaddingTop](properties-size-location.md)** – Der Abstand zwischen dem Text in einem Steuerelement und dem oberen Rand des Steuerelements.

**Page**: gibt die Nummer der Seite an, die Sie anzeigen möchten.

**PageCount**: gibt die Anzahl der Seiten in einem Dokument an.

**[PressedBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**ShowControls** – Gibt an, ob ein Audio- oder Videoplayer, z.B. eine Schaltfläche für Wiedergabe und ein Lautstärkeregler, und ein Stift-Steuerelement angezeigt wird, z.B. Symbole zum Zeichnen oder Löschen.

**[Tooltip](properties-core.md)** – Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**Zoom**– Der Prozentsatz, mit dem ein Bild einer Kamera oder die Ansicht einer Datei in einem PDF-Viewer vergrößert wird.

## <a name="example"></a>Beispiel

Fügen Sie ein Steuerelement des Typs **PDF-Viewer** hinzu, und legen Sie seine **Document**-Eigenschaft (in doppelten Anführungszeichen) auf die URL einer PDF-Datei fest, wie im folgenden Beispiel gezeigt:

  **„https://blog.mozilla.org/security/files/2015/05/HTTPS-FAQ.pdf“**

Das Steuerelement zeigt die PDF-Datei.

Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen und konfigurieren](../add-configure-controls.md)?

## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit

Es werden nicht alle Barrierefreiheitsfeatures von PDF-Dokumenten unterstützt, da sich der **PDF-Viewer** noch in der Experimentierphase befindet. Daher sollte **ShowControls** auf **TRUE** festgelegt sein, damit Benutzer das Dokument in einer externen Anwendung öffnen können.

Erfahren Sie, wie Sie mithilfe der [WCAG 2.0](https://www.w3.org/TR/WCAG-TECHS/pdf.html)- und [PDF/UA](https://www.pdfa.org/pdfua-the-iso-standard-for-universal-accessibility/)-Standards PDF-Dokumente erstellen können, auf die zugegriffen werden kann.

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe
* Fügen Sie ggf. mithilfe einer **[Bezeichnung](control-text-box.md)** einen Titel hinzu, wenn dem PDF-Dokument noch keiner zugeteilt ist. Der Titel kann direkt vor dem **PDF-Viewer** platziert werden.
