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
ms.openlocfilehash: b58e99e4775ed5c18d3498864c6e652e814ddf19
ms.sourcegitcommit: c76ec82db5d261be1fb7fdeeec3e119cdfada57f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="attachments-control-in-powerapps"></a>Attachments-Steuerelement in PowerApps
Ein Steuerelement, mit dem Benutzer Dateien auf Ihr Gerät herunterladen sowie Dateien in einer SharePoint-Liste hochladen und löschen können.

## <a name="limitations"></a>Beschränkungen
Für das Steuerelement für Anlagen gelten die folgenden temporären Einschränkungen:
1. Das Hochladen von Anlagen funktioniert nur mit SharePoint-Listen als Datenquellen.  Die Unterstützung für andere Datenquellen wird beginnend mit CDS schrittweise eingeführt.

1. Die Funktionen zum Hochladen und Löschen funktionieren nur in Formularen.  Das Steuerelement für Anlagen wird im Bearbeitungsmodus deaktiviert angezeigt, wenn es sich nicht in einem Formular befindet.   Beachten Sie, dass der Endbenutzer das Formular speichern muss, um hinzugefügte und gelöschte Dateien im Back-End zu speichern.

1. Sie können nur Dateien bis maximal 10 MB hochladen.  

## <a name="description"></a>Beschreibung
Mit dem **Attachments**-Steuerelement können Sie in einer Datenquelle gespeicherte Dateien öffnen sowie Dateien aus einer SharePoint-Liste hinzufügen und löschen.

## <a name="key-properties"></a>Haupteigenschaften
**[Items](properties-core.md)** – Die Quelle mit Beschreibungen der Dateien, die heruntergeladen werden können.

**MaxAttachments** – Die maximale Anzahl von Dateien, die vom Steuerelement akzeptiert wird.

**MaxAttachmentSize** – die maximal zulässige Dateigröße für jede neue Anlage in MB.  Zurzeit besteht eine Beschränkung von 10 MB.

**OnAttach** – Legt fest, wie die App reagiert, wenn der Benutzer eine neue Dateianlage hinzufügt.

**OnRemove** – Legt fest, wie die App reagiert, wenn der Benutzer eine vorhandene Anlage löscht.

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf eine Anlage klickt.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**AccessibleLabel** – Bezeichnung, die von einer Sprachausgabe gelesen wird.

**AddAttachmentText** – Der Beschriftungstext des Links, mit dem eine neue Anlage hinzugefügt wird.

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement das Hinzufügen und Löschen von Dateien zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**MaxAttachmentsText** – Der Text, der den Link „Datei anfügen“ ersetzt, wenn das Steuerelement die maximal zulässige Anzahl von Dateien enthält.

**NoAttachmentsText** – Hinweistext, der für den Benutzer, der angezeigt wird, wenn keine Anlagen vorhanden sind.

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
