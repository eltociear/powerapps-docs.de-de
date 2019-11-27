---
title: 'Kombinationsfeld-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen über das Kombinationsfeld-Steuerelement, einschließlich Eigenschaften und Beispielen
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 09/13/2017
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8c4316c8f4aac11903aaad8cb624ff881173b403
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2019
ms.locfileid: "73650626"
---
# <a name="combo-box-control-in-powerapps"></a>Kombinationsfeld-Steuerelement in PowerApps
Ein Steuerelement, das es Benutzern ermöglicht, unter Optionen eine Auswahl zu treffen.  Unterstützt die Suche und Mehrfachauswahl.

## <a name="description"></a>Beschreibung
Mit einem **Kombinationsfeld**-Steuerelement können Sie Elemente suchen, die Sie auswählen.  Die Suche erfolgt serverseitig mit der SearchField-Eigenschaft. Deshalb verursachen sehr große Datenquellen keine Leistungseinbuße.  

Der Einfach- oder Mehrfachauswahlmodus wird mit der SelectMultiple-Eigenschaft konfiguriert.

Wenn Sie auszuwählende Elemente suchen, können Sie für jedes Element festlegen, dass ein einzelner Datenwert, zwei Werte oder ein Bild und zwei Werte (Person) angezeigt werden. Hierzu ändern Sie die Einstellung „Layout“ im Bereich „Daten“.

## <a name="people-picker"></a>Personenauswahl
Wenn Sie ein **Kombinationsfeld** als Personenauswahl verwenden möchten, wählen Sie im Datenbereich in den Layouteinstellungen die Vorlage **Person** aus, und konfigurieren Sie die folgenden Dateneigenschaften, die für die Person angezeigt werden sollen.

## <a name="key-properties"></a>Haupteigenschaften
**[Items](properties-core.md)** – Die Quelle der Daten, aus der Elemente ausgewählt werden können.

**Defaultselecteditems** – die ersten ausgewählten Elemente, bevor der Benutzer mit dem Steuerelement interagiert.

**SelectedItems** – Die Liste der aufgrund der Benutzerinteraktion ausgewählten Elemente.

**SelectMultiple** – Legt fest, ob der Benutzer ein einzelnes Element oder mehrere Elemente auswählen kann.

**IsSearchable** – Legt fest, ob der Benutzer vor der Auswahl nach Elementen suchen kann.

**SearchFields**: Die Datenfelder der Datenquelle, die durchsucht werden, wenn Benutzer Text eingeben.  Um mehrere Felder zu durchsuchen, legen Sie Folgendes fest: ComboBox1.SearchFields = ["MyFirstColumn", "MySecondColumn"]

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[AccessibleLabel](properties-accessibility.md)** : Bezeichnung für Sprachausgaben

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**DisplayFields** – Die Liste der Felder, die für jedes von der Suche zurückgegebene Element angezeigt werden.  Diese Eigenschaft lässt sich am einfachsten im Bereich „Daten“ der Optionsregisterkarte „Eigenschaften“ konfigurieren.

**[DisplayMode](properties-core.md)** : Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[FocusedBorderColor](properties-color-border.md)** : die Rahmenfarbe eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[FocusedBorderThickness](properties-color-border.md)** : die Rahmendicke eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**InputTextPlaceholder** – Ein Hinweistext, der für Endbenutzer angezeigt wird, wenn kein Element ausgewählt ist.

**OnChange** – Legt fest, wie die App reagiert, wenn der Benutzer eine Auswahl ändert.

**OnNavigate** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Element klickt.

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**[TabIndex](properties-accessibility.md)** : Navigationsreihenfolge der Tastatur in Bezug auf andere Steuerelemente.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="example"></a>Beispiel
1. Öffnen Sie auf der Registerkarte **Einfügen** das Menü Steuer **Elemente** , und wählen Sie dann Kombinations **Feld**aus.  

1. Öffnen Sie auf der Registerkarte **Eigenschaften** im rechten Bereich die Liste **Datenquelle auswählen** (neben **Elemente**), und fügen Sie dann eine Datenquelle hinzu, oder wählen Sie Sie aus.

1. Wählen Sie auf der gleichen Registerkarte **Bearbeiten** (neben **Felder**) aus.

1. Öffnen Sie im Bereich **Daten** die **primäre Textliste** , und wählen Sie dann die Spalte aus, die Sie im Kombinations **Feld** -Steuerelement anzeigen möchten.

1. Wählen Sie bei gedrückter Alt-Taste den Pfeil nach unten aus, um das Kombinations **Feld** -Steuerelement zu öffnen.

    Das-Steuerelement zeigt die Daten aus der Spalte an, die Sie in der von Ihnen angegebenen Datenquelle angegeben haben.
    
1. optionale Um den ersten Datensatz standardmäßig anzuzeigen, legen Sie die **defaultselecteditems** -Eigenschaft auf diesen Ausdruck fest, und ersetzen Sie dabei *DataSource* durch den Namen Ihrer Datenquelle:

    `First(DataSource)`

## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit
### <a name="color-contrast"></a>Farbkontrast
Zwischen den folgenden Eigenschaften muss es einen ausreichenden Farbkontrast geben:
* **ChevronFill** und **ChevronBackground**
* **ChevronHoverFill** und **ChevronHoverBackground**
* **SelectionColor** und **SelectionFill**
* **SelectionFill** und **[Fill](properties-color-border.md)**
* **SelectionTagColor** und **SelectionTagFill**

Dies ist ein Zusatz zu den [Standardanforderungen für Farbkontraste](../accessible-apps-color.md).

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe
* **[AccessibleLabel](properties-accessibility.md)** muss vorhanden sein.

    > [!NOTE]
  > Auf Touchscreens können Benutzer, die die Sprachausgabe benutzen, der Reihe nach durch die Inhalte des Kombinationsfelds navigieren. Das Kombinationsfeld fungiert als Schaltfläche, die Inhalte anzeigt bzw. ausblendet, wenn diese aktiviert bzw. deaktiviert werden.

### <a name="keyboard-support"></a>Tastaturunterstützung
* **[TabIndex](properties-accessibility.md)** muss gleich 0 (null) oder größer sein, damit Tastaturbenutzer dorthin navigieren können.
* Fokusindikatoren müssen deutlich sichtbar sein. Mithilfe von **[FocusedBorderColor](properties-color-border.md)** und **[FocusedBorderThickness](properties-color-border.md)** können Sie dies archivieren.

    > [!NOTE]
  > Über die TAB-TASTE können Sie zum Kombinationsfeld navigieren oder dieses schließen. Über die Pfeiltasten können Sie durch die Inhalte des Kombinationsfelds navigieren. Über die ESC-Taste können Sie die Dropdownliste ggf. schließen.
