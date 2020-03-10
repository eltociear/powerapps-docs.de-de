---
title: 'Attachments-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen zum Attachment-Steuerelement, einschließlich Eigenschaften und Beispielen
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 03/09/2020
ms.author: chmoncay
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 35e4107934134a229817deb258bacf5e36c9dbb6
ms.sourcegitcommit: a02b20113164acb11955d27ef4ffa421ee0fba9d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "78970979"
---
# <a name="attachments-control-in-power-apps"></a>Anlagen-Steuerelement in powerapps
Ein Steuerelement, mit dem Benutzer Dateien auf Ihr Gerät herunterladen sowie Dateien aus einer SharePoint-Liste oder einer Common Data Service Entität hochladen und löschen können.

## <a name="limitations"></a>Einschränkungen
Für das Steuerelement für Anlagen gelten folgende Einschränkungen:
1. Anlagen werden mit SharePoint-Listen und Common Data Service Entitäten unterstützt.

1. Die Funktionalität zum Hochladen und Löschen funktioniert nur in einem Formular. Das Anlage Steuerelement wird im Bearbeitungsmodus und nicht in einem Formular deaktiviert angezeigt. Um Datei Ergänzungen und-Löschungen zu speichern, muss der App-Benutzer das Formular speichern. Aufgrund dieser Einschränkung ist das Anlagen Steuerelement auf der Registerkarte " **Einfügen** " nicht verfügbar, wird jedoch im Formular angezeigt, wenn das Feld "Anlage Formular" in einem SharePoint-oder Common Data Service Formular aktiviert ist.

1. Dateien können nur dann hochgeladen werden, wenn Sie 10 MB oder weniger groß sind.  

## <a name="description"></a>Beschreibung
Mit einem **Anlagen** -Steuerelement können Sie Dateien aus einer SharePoint-Liste oder einer Common Data Service Entität öffnen, hinzufügen und löschen.

## <a name="key-properties"></a>Haupteigenschaften
**[Items](properties-core.md)** – Die Quelle mit Beschreibungen der Dateien, die heruntergeladen werden können.

**MaxAttachments** – Die maximale Anzahl von Dateien, die vom Steuerelement akzeptiert wird.

**MaxAttachmentSize** – die maximal zulässige Dateigröße für jede neue Anlage in MB.  Zurzeit besteht eine Beschränkung von 10 MB.

**OnAttach** – Legt fest, wie die App reagiert, wenn der Benutzer eine neue Dateianlage hinzufügt.

**OnRemove** – Legt fest, wie die App reagiert, wenn der Benutzer eine vorhandene Anlage löscht.

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf eine Anlage klickt.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[AccessibleLabel](properties-accessibility.md)** : Bezeichnung für Sprachausgaben Sollte den Zweck dieser Anlagen beschreiben.

**AddAttachmentText** – Der Beschriftungstext des Links, mit dem eine neue Anlage hinzugefügt wird.

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[DisplayMode](properties-core.md)** : Legt fest, ob das Steuerelement das Hinzufügen und Löschen von Dateien zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[FocusedBorderColor](properties-color-border.md)** : die Rahmenfarbe eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[FocusedBorderThickness](properties-color-border.md)** : die Rahmendicke eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**MaxAttachmentsText** – Der Text, der den Link „Datei anfügen“ ersetzt, wenn das Steuerelement die maximal zulässige Anzahl von Dateien enthält.

**NoAttachmentsText** – Hinweistext, der für den Benutzer, der angezeigt wird, wenn keine Anlagen vorhanden sind.

**[TabIndex](properties-accessibility.md)** : Navigationsreihenfolge der Tastatur in Bezug auf andere Steuerelemente.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (oder des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (oder des Bildschirms, wenn kein übergeordneter Container vorhanden ist).


## <a name="example"></a>Beispiel
1. Fügen Sie der APP ein Formular hinzu, und legen Sie eine SharePoint-Liste als Datenquelle fest.

2. Wählen Sie in der Strukturansicht auf der linken Seite das **Formular Formular anzeigen** aus. Sie können stattdessen auch das **Formular bearbeiten** verwenden.

3. Wählen Sie auf der Registerkarte Eigenschaften im Bereich Optionen auf der rechten Seite **Datenquelle** , und wählen Sie dann die SharePoint-Liste aus, mit der Sie verbunden sind.

4. Wählen *Sie im Feld Abschnitt Felder* **Bearbeiten** und **Feld hinzufügen**aus. 

5. Wählen Sie das Feld **Anlagen** und dann **Hinzufügen**aus.

    Im Formular wird das der SharePoint-Liste zugeordnete Feld „Anlagen“ angezeigt.

[Erfahren Sie, wie Sie ein Steuerelement hinzufügen und konfigurieren](../add-configure-controls.md)


## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit
### <a name="color-contrast"></a>Farbkontrast
Zwischen folgenden Eigenschaften muss es einen ausreichenden Farbkontrast geben:
* **ItemColor** und **ItemFill**
* **ItemHoverColor** und **ItemHoverFill**
* **ItemPressedColor** und **ItemPressedFill**
* **AddedItemColor** und **AddedItemFill**
* **RemovedItemColor** und **RemovedItemFill**
* **ItemErrorColor** und **ItemErrorFill**
* **AddAttachmentColor** und **Fill**
* **MaxAttachmentsColor** und **Fill**
* **NoAttachmentsColor** und **Fill**

Dies ist ein Zusatz zu den [Standardanforderungen für Farbkontraste](../accessible-apps-color.md).

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe
Die folgenden Eigenschaften müssen vorhanden sein:
* **[AccessibleLabel](properties-accessibility.md)**
* **AddAttachmentsText**
* **MaxAttachmentsText**
* **NoAttachmentsText**

### <a name="keyboard-support"></a>Tastaturunterstützung
* **[TabIndex](properties-accessibility.md)** muss gleich 0 (null) oder größer sein, damit Tastaturbenutzer dorthin navigieren können.
* Fokusindikatoren müssen deutlich sichtbar sein. Mithilfe von **[FocusedBorderColor](properties-color-border.md)** und **[FocusedBorderThickness](properties-color-border.md)** können Sie dies archivieren.
