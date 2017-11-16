---
title: 'Kombinationsfeld-Steuerelement: Referenz | Microsoft-Dokumentation'
description: "Informationen über das Kombinationsfeld-Steuerelement, einschließlich Eigenschaften und Beispielen"
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
ms.date: 09/13/2017
ms.author: fikaradz
ms.openlocfilehash: 7220771d9798e6bb5481bbc86c430a357aeab7d2
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="combo-box-control-in-powerapps"></a>Kombinationsfeld-Steuerelement in PowerApps
Ein Steuerelement, das es Benutzern ermöglicht, unter Optionen eine Auswahl zu treffen.  Unterstützt die Suche und Mehrfachauswahl.

## <a name="description"></a>Beschreibung
Mit einem **Kombinationsfeld**-Steuerelement können Sie Elemente suchen, die Sie auswählen.  Die Suche erfolgt serverseitig mit der SearchField-Eigenschaft. Deshalb verursachen sehr große Datenquellen keine Leistungseinbuße.  

Der Einfach- oder Mehrfachauswahlmodus wird mit der SelectMultiple-Eigenschaft konfiguriert.

Wenn Sie auszuwählende Elemente suchen, können Sie für jedes Element festlegen, dass ein einzelner Datenwert, zwei Werte oder ein Bild und zwei Werte (Person) angezeigt werden. Hierzu ändern Sie die Einstellung „Layout“ im Bereich „Daten“.

## <a name="key-properties"></a>Haupteigenschaften
**[Items](properties-core.md)** – Die Quelle der Daten, aus der Elemente ausgewählt werden können.

**DefaultItems** – Die ursprünglich ausgewählten Elemente, bevor der Benutzer mit dem Steuerelement interagiert.

**SelectedItems** – Die Liste der aufgrund der Benutzerinteraktion ausgewählten Elemente.

**SelectMultiple** – Legt fest, ob der Benutzer ein einzelnes Element oder mehrere Elemente auswählen kann.

**IsSearchable** – Legt fest, ob der Benutzer vor der Auswahl nach Elementen suchen kann.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[Default](properties-core.md)** – Die ursprüngliche Auswahl, bevor sie vom Benutzer im Einzelauswahlmodus geändert wird.

**DisplayFields** – Die Liste der Felder, die für jedes von der Suche zurückgegebene Element angezeigt werden.  Diese Eigenschaft lässt sich am einfachsten im Bereich „Daten“ der Optionsregisterkarte „Eigenschaften“ konfigurieren.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**InputTextPlaceholder** – Ein Hinweistext, der für Endbenutzer angezeigt wird, wenn kein Element ausgewählt ist.

**OnChange** – Legt fest, wie die App reagiert, wenn der Benutzer eine Auswahl ändert.

**OnNavigate** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Element klickt.

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="example"></a>Beispiel
1. Fügen Sie aus der Registerkarte „Einfügen“ des Menüs „Steuerelemente“ ein **Kombinationsfeld**-Steuerelement hinzu.  
2. Klicken Sie auf der Optionsregisterkarte „Eigenschaften“ auf „Daten“.  
3. Wählen Sie unten die Datenquelle, das Layout und die entsprechenden Eigenschaften aus.
4. Legen Sie auf der Registerkarte „Erweitert“ die **SelectMultiple**-Eigenschaft fest.
   
    In der App wird ein funktionsfähiges **Kombinationsfeld** angezeigt.
   
    Möchten Sie wissen, wie Sie ein [Steuerelement hinzufügen und konfigurieren](../add-configure-controls.md)?

