---
title: Zusammenarbeiten mithilfe von SharePoint | Microsoft-Dokumentation
description: Hier erfahren Sie, wie die Zusammenarbeit mithilfe von SharePoint in einer modellgesteuerten App funktioniert.
documentationcenter: ''
author: Mattp123
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 11/20/2019
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 428291712f91e90cea515723a93e1871ec94de2e
ms.sourcegitcommit: 8f32eed48adf4b24b9ca607bbf6db3d19749c46f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74418279"
---
# <a name="collaborate-using-sharepoint"></a>Zusammenarbeiten mithilfe von SharePoint 

Verwalten Sie gängige Dokumenttypen wie Word, Excel und PowerPoint, und erstellen Sie Ordner, um diese Dokumente zu speichern und zu sortieren. Diese Ordner werden über eine modellgesteuerte App nahtlos in SharePoint gespeichert. 

> [!NOTE]
> Für dieses Feature ist es erforderlich, dass der Systemadministrator die SharePoint-Dokumentverwaltung aktiviert hat. Weitere Informationen: [Verwalten von Dokumenten mit SharePoint](/power-platform/admin/manage-documents-using-sharepoint)

Für Konto- und Kontaktdaten wird automatisch ein Standardordner in SharePoint erstellt, wenn Sie zum ersten Mal auf die Registerkarte **Dateien** wechseln. Weitere Standarddatensätze oder benutzerdefinierte Entitätsdatensätze finden Sie auf der Registerkarte **Verknüpft** > **Dokumente**. Der Name des Dokumentspeicherorts weist folgendes Format auf: <Datensatzname>_<Datensatz-ID>.

Standardmäßig ist der Speicherort auf „Dokumente“ an „Standardstandort 1“ festgelegt.

## <a name="add-a-document"></a>Hinzufügen eines Dokuments
1.  Öffnen Sie ein Konto oder einen Kontaktdatensatz, und öffnen Sie die Registerkarte **Dateien**. Bei anderen Standardentitäten oder benutzerdefinierten Entitäten, die für die Dokumentverwaltung aktiviert sind, öffnen Sie die Registerkarte **Verknüpft** und klicken dann auf **Dokumente**.
2.  Sie können zwischen folgenden Optionen wählen: 
    - Klicken Sie auf **Neu**, um ein neues Dokument zu erstellen. Wählen Sie dann den Dokumenttyp (z. B. Word, Excel oder OneNote) aus, und geben Sie einen Namen ein. Wählen Sie **Speichern**. Das leere Dokument wird in einer neuen Registerkarte geöffnet. 
    - Sie können ein vorhandenes Dokument hinzufügen, indem Sie auf **Hochladen** > **Datei auswählen** klicken und dann zur gewünschten Datei navigieren. Klicken Sie anschließend auf **Öffnen**. Wählen Sie **OK** aus. 

Die Dokumentdatei wird in der Ansicht **Zugeordnetes Raster des Dokuments** angezeigt. 

> [!div class="mx-imgBorder"] 
> ![](media/add-doc-sharepoint.png "Add document to SharePoint")

Das Dokument wird ebenfalls im Ordner des SharePoint-Standorts abgelegt. 

> [!div class="mx-imgBorder"] 
> ![](media/doc-on-sharepoint.png "Document on SharePoint")

## <a name="manage-sharepoint-locations"></a>Verwalten von SharePoint-Speicherorten
Sie können über eine modellgesteuerte App neue SharePoint-Speicherorte erstellen oder vorhandene bearbeiten.

1. Klicken Sie in der Liste **Dateien** auf der Befehlsleiste auf **Speicherort öffnen**, und wählen Sie dann den Speicherort aus.
2. Sie können den Speicherort bearbeiten, indem Sie auf der Befehlsleiste auf **Speicherort bearbeiten**<location name> klicken.
Daraufhin wird das Dialogfeld **Speicherort bearbeiten** angezeigt.
3. Der Anzeigename, der übergeordnete Standort und der Ordnername werden automatisch aufgefüllt. Geben Sie die Informationen zum neuen Speicherort ein, und klicken Sie dann auf **Speichern**.
4. Klicken Sie auf der Befehlsleiste auf **Speicherort hinzufügen**, um einen Speicherort hinzuzufügen.
5. Daraufhin wird das Dialogfeld **Speicherort hinzufügen** angezeigt.

    > [!div class="mx-imgBorder"] 
    > ![](media/add-location-dialog-box.png "Add location dialog box")
6. Der Anzeigename, der übergeordnete Standort und der Ordnername werden automatisch aufgefüllt. Passen Sie die Angaben bei Bedarf an, und klicken Sie dann auf **Speichern**.

## <a name="actions-on-documents"></a>Aktionen in Dokumenten
Wenn Sie ein oder mehrere Dokumente aus der Liste „Dokumente“ auswählen, können Sie die folgenden allgemeinen SharePoint-Aktionen in diesen ausführen:
- Bearbeiten
- Löschen
- Einchecken
- Auschecken
- Auschecken verwerfen
- Eigenschaften bearbeiten

## <a name="files-tab-faq"></a>Häufig gestellte Fragen zur Registerkarte „Dateien“
*Warum wurde der Speicherort für den Zugriff auf Dokumente verschoben?* 
- Der Befehl wurde verschoben, damit Dokumente mit weniger Klicks gesucht und gefunden werden können.

*Wurde die Registerkarte „Dokumente“ entfernt?*
- Nein, sie wurde nicht entfernt. Benutzer können weiterhin wie gewohnt auf die dem Datensatz zugeordneten Dokumente zugreifen, indem sie auf „Verknüpft > Dokumente“ klicken.

*Werden trotz der Änderung noch automatisch Unterordner in SharePoint erstellt?*
- Ja. Das Verhalten ähnelt dem Link **Dokumente** im Menü **Verknüpft**. Wenn ein Benutzer zum ersten Mal auf die Registerkarte **Dateien** klickt, wird der entsprechende SharePoint-Unterordner vom System erstellt. 

*Gibt es eine Möglichkeit, die Registerkarte „Dateien“ zu anderen Entitäten hinzuzufügen oder zu entfernen?*
- Ja. Befolgen Sie die Schritt in diesem Artikel, um die Registerkarte „Dateien“ hinzuzufügen oder zu entfernen: [Hinzufügen der Registerkarte „SharePoint-Dokumente” zum Hauptformular für eine Entität](../maker/model-driven-apps/add-documents-tab-entity-main-form.md)  

*Wohin kann ich Feedback zu dieser Änderung senden?*
- Sie können Ihr Feedback an das Dynamics 365 Sales Office and Teams Integration-Team (d365_ot_crew@microsoft.com) senden.

### <a name="see-also"></a>Siehe auch
[SharePoint-, OneNote- und OneDrive-Integration mit Common Data Service](../maker/common-data-service/sharepoint-onedrive-onenote-intro.md)