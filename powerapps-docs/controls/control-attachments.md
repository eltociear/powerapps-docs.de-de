---
title: 'Attachments-Steuerelement: Referenz | Microsoft-Dokumentation'
description: "Informationen zum Attachment-Steuerelement, einschließlich Eigenschaften und Beispielen"
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
ms.date: 09/29/2017
ms.author: fikaradz
ms.openlocfilehash: 2fd5db380eead5403d4cc7d927da5a24aa24abc9
ms.sourcegitcommit: 33099e6197c0139679cd08c42e9e2a5717904c92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2018
---
# <a name="attachments-control-in-powerapps"></a>Attachments-Steuerelement in PowerApps
Ein Steuerelement, das Benutzern das Herunterladen von Dateien auf ihr Gerät ermöglicht.  Uploadfunktionalität ist in Kürze verfügbar.

## <a name="description"></a>Beschreibung
Mit einem **Attachments**-Steuerelement können Sie Dateien öffnen, die in einer Datenquelle gespeichert sind.

## <a name="key-properties"></a>Haupteigenschaften
**[Items](properties-core.md)** – Die Quelle mit Beschreibungen der Dateien, die heruntergeladen werden können.

**MaxAttachments** – Die maximale Anzahl von Dateien, die vom Steuerelement akzeptiert wird.

**OnAttach** – Legt fest, wie die App reagiert, wenn der Benutzer eine neue Dateianlage hinzufügt.

**OnRemove** – Legt fest, wie die App reagiert, wenn der Benutzer eine vorhandene Anlage löscht.

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf eine Anlage klickt.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**AddAttachmentText** – Der Beschriftungstext der Schaltfläche, mit der eine neue Anlage hinzugefügt wird.

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**NoAttachmentsText** – Hinweistext, der für den Benutzer angezeigt wird, wenn keine Anlagen zum Anzeigen vorhanden sind.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (oder des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (oder des Bildschirms, wenn kein übergeordneter Container vorhanden ist).


## <a name="example"></a>Beispiel
1. Erstellen Sie eine App aus Daten, wobei eine SharePoint-Liste als Datenquelle verwendet wird.  Alternativ können Sie der App ein Formular hinzufügen und eine SharePoint-Liste als Datenquelle festlegen.

2. Wählen Sie in der Strukturansicht auf der linken Seite das **Form**-Steuerelement aus.

3. Klicken Sie im Optionsbereich auf der rechten Seite auf der Registerkarte „Eigenschaften“ auf **Daten**.

4. Aktivieren Sie unter **Felder**, das Feld **Anlagen**.

    Im Formular wird das der SharePoint-Liste zugeordnete Feld „Anlagen“ angezeigt.

Möchten Sie wissen, wie Sie ein [Steuerelement hinzufügen und konfigurieren](../add-configure-controls.md)?
