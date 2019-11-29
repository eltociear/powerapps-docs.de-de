---
title: 'Microsoft Stream Video-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispielen, über das Microsoft Stream Video-Steuerelement
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 11/26/2019
ms.author: fikaradz
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: bfefad0a3e1500e926251d68f12ea9c398e9cd9a
ms.sourcegitcommit: abeedb952afc5e09ae4c158611e4813b63cb49b3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643782"
---
# <a name="microsoft-stream-video-control-in-powerapps"></a>Microsoft Stream Video-Steuerelement in powerapps
Ein Video Player für Microsoft Stream Videos und Kanäle.

## <a name="description"></a>Beschreibung
Das-Steuerelement ermöglicht App-Benutzern das Abspielen von Videos und Durchsuchen von Kanälen aus dem Microsoft Stream-Dienst.

## <a name="key-properties"></a>Haupteigenschaften
**Streamurl** – die URL des Microsoft Stream Videos oder Kanals, das im Steuerelement angezeigt werden soll.

**ShowControls** – gibt an, ob die Videowiedergabe-Steuerelemente für den Endbenutzer angezeigt werden.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[AccessibleLabel](properties-accessibility.md)** : Bezeichnung für Sprachausgaben Sollte dem Titel des Videos oder der Audiodatei entsprechen.

**AutoStart**: Gibt an, ob ein Audio- oder Video-Steuerelement automatisch einen Clip wiedergibt, wenn der Benutzer zu dem Bildschirm navigiert, der das Steuerelement enthält.

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[DisplayMode](properties-core.md)** : Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[FocusedBorderColor](properties-color-border.md)** : die Rahmenfarbe eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[FocusedBorderThickness](properties-color-border.md)** : die Rahmendicke eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**StartTime** – Der Zeitpunkt nach dem Start eines Audio- oder Videoclips, zu dem die Wiedergabe des Clips beginnt.

**[TabIndex](properties-accessibility.md)** : Navigationsreihenfolge der Tastatur in Bezug auf andere Steuerelemente.

**[QuickInfo](properties-core.md)** : Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="example"></a>Beispiel

### <a name="play-an-audio-or-video-file-from-microsoft-stream"></a>Wiedergabe einer Audiodatei oder Videodatei aus Microsoft Stream

1. Wählen Sie im Menü **Datei** die Option **Einfügen** und dann das Dropdown Menü **Medien** öffnen aus. 
2. Wählen Sie in der Liste der mediensteuer Elemente **Microsoft Stream** aus:

    ![Microsoft Stream](./media/control-stream-video/stream-icon.png "Microsoft Stream")

3. Fügen Sie den Video Link in der **Stream-URL** -Eigenschaft auf der linken Seite ein:

    ![Streamurl-Eigenschaft anpassen](./media/control-stream-video/stream-url.png "Streamurl-Eigenschaft anpassen")

4. Drücken Sie F5, und wählen Sie die Wiedergabe Schaltfläche des hinzugefügten Steuer Elements aus.

    > [!NOTE]
   > Zum Abspielen des Videos **Microsoft Stream** eine Authentifizierung erforderlich. Stellen Sie sicher, dass der App-Benutzer die erforderliche Berechtigung hat.
5. Drücken Sie ESC, um den Vorschaumodus zu beenden.

## <a name="browser-considerations"></a>Überlegungen zum Browser

### <a name="ios"></a>erhältlich
Der IOS-Player von Power Apps unterstützt keine direkte Wiedergabe von Videos, die in der APP eingebettet sind.  Um das Video anzusehen, klicken Sie auf das streamsymbol, um den Video Player im Vollbildmodus zu starten.

### <a name="safari"></a>SK

Um Microsoft Stream Videos in einer APP im Safari-Browser anzuzeigen, müssen Sie die Option deaktivieren, um die [standortübergreifende Nachverfolgung zu verhindern](https://support.apple.com/guide/safari/sfri40732/mac).

## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit
### <a name="audio-and-video-alternatives"></a>Alternativen zu Audio- und Videodateien
* **ShowControls** muss auf TRUE festgelegt sein, sodass Benutzer Multimediadateien in ihrem eigenen Tempo hören oder ansehen können. Damit können Benutzer auch Untertitel und den Vollbildmodus in Videoplayern aktivieren bzw. deaktivieren.
* Untertitel müssen für alle Videos bereitgestellt werden.
 * Sie können auch ein Audio- oder Videotranskript mithilfe einer der folgenden Methoden bereitstellen:
  1. Platzieren Sie den Text in einer **[Bezeichnung](control-text-box.md)** , und positionieren Sie ihn neben dem Multimedia-Player. Erstellen Sie optional eine **[Schaltfläche](control-button.md)** , um die Textanzeige umzuschalten.
  2. Platzieren Sie den Text in einem anderen Bildschirm. Erstellen Sie eine **[Schaltfläche](control-button.md)** , die auf diesen Bildschirm weiterleitet, und positionieren Sie die Schaltfläche neben dem Multimedia-Player.
  3. Wenn die Beschreibung kurz ist, kann sie in **[AccessibleLabel](properties-accessibility.md)** eingegeben werden.

### <a name="color-contrast"></a>Farbkontrast
Zwischen den folgenden Eigenschaften muss es einen ausreichenden Farbkontrast geben:
* **[FocusedBorderColor](properties-color-border.md)** und die äußere Farbe
* **[Fill](properties-color-border.md)** (Füllfarbe) und dem Multimedia-Player-Steuerelement (falls zutreffend)

Stellen Sie Untertitel und/oder Transkripte bereit, wenn der Videoinhalt Probleme mit dem Farbkontrast aufweist.

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe
* **[AccessibleLabel](properties-accessibility.md)** muss vorhanden sein.

### <a name="keyboard-support"></a>Tastaturunterstützung
* **[TabIndex](properties-accessibility.md)** muss gleich 0 (null) oder größer sein, damit Tastaturbenutzer dorthin navigieren können.
* Fokusindikatoren müssen deutlich sichtbar sein. Mithilfe von **[FocusedBorderColor](properties-color-border.md)** und **[FocusedBorderThickness](properties-color-border.md)** können Sie dies archivieren.
* **AutoStart** sollte FALSE sein, da es für Tastaturbenutzer schwierig sein kann, die Wiedergabe schnell zu beenden.