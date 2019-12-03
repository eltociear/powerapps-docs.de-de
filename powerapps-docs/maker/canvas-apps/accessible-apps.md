---
title: Erstellen barrierefreier Canvas-Apps | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie barrierefreie Canvas-Apps für Menschen mit Behinderungen erstellen.
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/03/2018
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 56e5ec7f303706ded114655e5c6d473408e9ddd7
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74680027"
---
# <a name="create-accessible-canvas-apps-in-powerapps"></a>Erstellen barrierefreier Canvas-Apps in PowerApps
Eine barrierefreie Canvas-App kann von Benutzern mit Sehschwäche, Gehörschädigung und anderen Beeinträchtigungen erfolgreich verwendet werden.  Die nachfolgenden Richtlinien sind nicht nur für viele Behörden und Organisationen verpflichtend, sie erhöhen zudem die Verwendbarkeit für alle Benutzer, unabhängig von ihren Fähigkeiten.

Verwenden Sie die **[Barrierefreiheitsprüfung](accessibility-checker.md)** , um mögliche Probleme Ihrer App bei der Barrierefreiheit zu überprüfen. 

## <a name="layout-and-color"></a>Layout und Farben
Ein allgemeingültiger und unkomplizierter Entwurf sorgt für eine einfachere Bedienbarkeit der Apps für alle Benutzer.  Wenn Sie Apps stark anpassen, beachten Sie die folgenden Vorschläge.  Powerapps-Designs sind standardmäßig zugänglich.
- Stellen Sie sicher, dass alle Elemente gut zu sehen sind und Texte eine angemessene Größe besitzen.  Alle Inhalte müssen mit bloßem Auge leicht und deutlich lesbar sein.
- Vermeiden Sie die Verwendung der Sichtbarkeitseigenschaft von Elementen, um ein Element ins Sichtfeld zu rücken.  Wenn Sie ein Element je nach Bedingung anzeigen möchten, erstellen Sie den Inhalt in einem neuen Bildschirm, den Sie öffnen und schließen können.
- Stellen Sie sicher, dass Eingabeelemente auf dem Bildschirm bezeichnet werden. Die Eigenschaft **[AccessibilityLabel](controls/properties-accessibility.md)** definiert, was in der Sprachausgabe vorgelesen wird.
- Stellen Sie beim Anpassen von Farben sicher, dass der Kontrast zwischen Text und Hintergrund ein Verhältnis von 4,5:1 oder höher aufweist.  Softwaretools für die Unterstützung dieses Vorgangs sind sofort verfügbar.
- Stellen Sie sicher, dass das Layout einem logischen Ablauf folgt, wenn es von oben nach unten und von links nach rechts gelesen wird.


## <a name="keyboard-support"></a>Tastaturunterstützung
Stellen Sie beim Testen der Barrierefreiheit Ihrer App sicher, dass die App auch über die Tastatur und in den Bedienungshilfemodi von iOS und Android verwendet werden kann und dass die Navigation mit aktivierter Sprachausgabe erfolgreich durchführbar ist.

Stellen Sie bei der Tastaturnavigation (mit und ohne Sprachausgabe) sicher, dass bei Verwendung der TAB-TASTE zum Durchlaufen der Eingabefelder eine logische Abfolge eingehalten wird, indem Sie die Eigenschaft **[TabIndex](controls/properties-accessibility.md)** der einzelnen Steuerelemente festlegen:
- Label-, Image-, Symbol-und Shape-Steuerelemente: Wenn Sie interaktive Elemente darstellen (d.h. Schaltflächen), legen Sie TabIndex auf 0 fest. Wenn es sich um dekorative Elemente oder Text handelt, legen Sie TabIndex auf-1 fest.
- Vermeiden Sie das Festlegen von TabIndex auf einen höheren Wert als null.

## <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe
Die folgenden Software Kombinationen sind die unterstützten Empfehlungen für die Nutzung von powerapps mit einer Bildschirm Sprachausgabe:

- **Windows**: Microsoft Edge/Sprachausgabe
- **macOS**: Safari/VoiceOver
- **Android**: powerapps-App/Talkback
- **IOS**: powerapps-App/VoiceOver

Um für die Sprachausgabe ein zufriedenstellendes Ergebnis sicherzustellen, wird Folgendes empfohlen:

- Vergewissern Sie sich, dass für alle Eingabesteuerelemente die Eigenschaft **[AccessibilityLabel](controls/properties-accessibility.md)** festgelegt wurde.
- Legen Sie in **[AccessibilityLabel](controls/properties-accessibility.md)** für Bilder eine entsprechende Beschreibung fest.
  - Wenn ein Bild nicht als Schaltfläche oder Link verwendet wird (ein Symbol also nur zur Dekoration dient) und von der Sprachausgabe nicht vorgelesen werden soll, stellen Sie sicher, dass **[AccessibilityLabel](controls/properties-accessibility.md)** leer oder nicht festgelegt ist.
  - Wenn ein Bild oder ein Symbol als Schaltfläche verwendet wird, legen Sie **[TabIndex](controls/properties-accessibility.md)** auf 0 und **[AccessibilityLabel](controls/properties-accessibility.md)** auf die Linkbeschreibung fest.


## <a name="multimedia"></a>Multimedia
Stellen Sie sicher, dass alle Videos mit Untertiteln versehen und Abschriften aller Audioaufnahmen für den Benutzer verfügbar sind.  Das **Video** Steuerelement unterstützt Untertitel im webvtt-Format über die **closedcaptionsurl** -Eigenschaft.

Beachten Sie, dass der **Timer** bei aktivierter Sprachausgabe nicht den Schaltflächentext, sondern die verstrichene Zeit angibt.  Die Ankündigungen können auch dann nicht deaktiviert werden, wenn der Timer durch niedrige Deckkraft ausgeblendet wurde.

## <a name="working-with-signatures"></a>Arbeiten mit Signaturen
Wenn Sie über ein Signaturfeld verfügen, das das Steuerelement „PenInput“ verwendet, müssen Sie eine alternative Methode der Signatureingabe aktivieren.  Empfohlen wird die Anzeige eines TextInput-Steuerelements, in dem ein Benutzer seinen Namen eingeben kann.  Stellen Sie sicher, die Signaturanweisungen in der Eigenschaft **[AccessibilityLabel](controls/properties-accessibility.md)** angegeben sind und dass sich das Steuerelement in der Nähe der Stifteingabe (rechts daneben oder direkt darunter) befindet.



Ähnlich:
- [Accessibility properties (Eigenschaften der Barrierefreiheit)](controls/properties-accessibility.md)
- [Verwenden der Barrierefreiheitsprüfung](accessibility-checker.md)
- [Barrierefreie Farben in PowerApps](accessible-apps-color.md)
