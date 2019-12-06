---
title: Arbeiten mit SharePoint | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mit SharePoint in einer Modell gesteuerten App zusammenarbeiten.
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
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74418279"
---
# <a name="collaborate-using-sharepoint"></a>Zusammenarbeiten mithilfe von SharePoint 

Verwalten allgemeiner Dokumenttypen wie Word, Excel und PowerPoint und Erstellen von Ordnern zum Speichern und Verwalten von Dokumenten, die nahtlos in SharePoint in einer Modell gesteuerten APP gespeichert werden. 

> [!NOTE]
> Für dieses Feature ist es erforderlich, dass der Systemadministrator die SharePoint-Dokument Verwaltung aktiviert hat. Weitere Informationen finden [Sie unter Verwalten von Dokumenten mithilfe von SharePoint](/power-platform/admin/manage-documents-using-sharepoint) .

Bei Konto-und Kontaktdaten Sätzen wird automatisch ein Standardordner für den Dokument Speicherort auf SharePoint erstellt, wenn Sie zum ersten Mal zur Registerkarte **Dateien** wechseln. Wechseln Sie für andere Standard-oder benutzerdefinierte Entitäts Datensätze zur Registerkarte **Verwandte** > **Dokumente** . Der Name des Dokument Speicher Orts weist das folgende Format auf: < record_name > _ < record_id >.

Standardmäßig ist der Speicherort auf Dokumente auf der Standard Website 1 festgelegt.

## <a name="add-a-document"></a>Hinzufügen eines Dokuments
1.  Öffnen Sie ein Konto oder einen Kontaktdaten Satz, und wählen Sie die Registerkarte **Dateien** . Bei anderen Standard Entitäten oder benutzerdefinierten Entitäten, die für die Dokument Verwaltung aktiviert sind, wählen Sie die Registerkarte **verwandt** und dann **Dokumente**aus.
2.  Wählen Sie eine der folgenden Optionen aus. 
    - Um ein neues Dokument zu erstellen, wählen Sie **neu**aus, wählen Sie den gewünschten Dokumenttyp aus, z. b. Word, Excel oder OneNote, und geben Sie dann einen Namen ein. Wählen Sie **Speichern**. Das leere Dokument wird auf einer neuen Registerkarte geöffnet. 
    - Wählen Sie zum Hinzufügen eines vorhandenen Dokuments **hochladen**aus, wählen Sie **Datei auswählen**aus, navigieren Sie zu, wählen Sie die gewünschte Datei aus, und wählen Sie dann **Öffnen**aus. Wählen Sie **OK** aus. 

Die Dokument Datei wird in der mit dem **Dokument verknüpften Raster** Ansicht angezeigt. 

> [!div class="mx-imgBorder"] 
> ![](media/add-doc-sharepoint.png "Add document to SharePoint")

Das Dokument wird auch am Speicherort des SharePoint-Website Ordners angezeigt. 

> [!div class="mx-imgBorder"] 
> ![](media/doc-on-sharepoint.png "Document on SharePoint")

## <a name="manage-sharepoint-locations"></a>Verwalten von SharePoint-Speicherorten
Sie können in einer Modell gesteuerten App neue SharePoint-Speicherorte erstellen oder vorhandene SharePoint-Speicherorte bearbeiten.

1. Wählen Sie in der Liste **Dateien** auf der Befehlsleiste die Option **Speicherort öffnen**aus, und wählen Sie dann den Speicherort aus.
2. Um den Speicherort zu bearbeiten, wählen Sie auf der Befehlsleiste **Speicherort <location name>bearbeiten** aus.
Das Dialogfeld **Speicherort bearbeiten** wird angezeigt.
3. Anzeige Name, übergeordneter Standort und Ordnername werden automatisch aufgefüllt. Geben Sie Details zum neuen Speicherort ein, und klicken Sie dann auf **Speichern**.
4. Um einen Speicherort hinzuzufügen, wählen Sie auf der Befehlsleiste **Speicherort hinzufügen**aus.
5. Das Dialogfeld **Speicherort hinzufügen** wird angezeigt.

    > [!div class="mx-imgBorder"] 
    > ![](media/add-location-dialog-box.png "Add location dialog box")
6. Anzeige Name, übergeordneter Standort und Ordnername werden automatisch aufgefüllt. Ändern Sie die Details bei Bedarf, und wählen Sie dann **Speichern**aus.

## <a name="actions-on-documents"></a>Aktionen für Dokumente
Wenn Sie ein oder mehrere Dokumente in der Liste Dokumente auswählen, können Sie die folgenden anderen allgemeinen SharePoint-Aktionen in den Dokumenten ausführen:
- Bearbeiten
- Löschen
- Einchecken
- Sehen Sie sich
- Auschecken verwerfen
- Eigenschaften bearbeiten

## <a name="files-tab-faq"></a>FAQ zu Dateien
*Warum wurde der Speicherort für den Zugriff auf Dokumente verschoben?* 
- Wir haben den Befehl verschoben, um die Suche von Dokumenten mit weniger Klicks zu vereinfachen.

*Ist die Registerkarte "Dokumente" entfernt?*
- Nein, das ist nicht abgelaufen. Benutzer können weiterhin auf die Dokumente, die dem fraglichen Datensatz zugeordnet sind, auf die alte Weise zugreifen, indem Sie einfach auf das entsprechende Menü und dann auf den Link Dokumente klicken.

*Mit der Änderung werden Unterordner in SharePoint weiterhin automatisch erstellt?*
- Ja. Das Verhalten ähnelt dem Link " **Dokumente** " im **entsprechenden** Menü. Wenn ein Benutzer die Registerkarte **Dateien** zum ersten Mal auswählt, wird der entsprechende SharePoint-Unterordner vom System erstellt. 

*Gibt es eine Möglichkeit, die Registerkarte "Dateien" anderen Entitäten hinzuzufügen oder zu entfernen?*
- Ja. Um die Registerkarte "Datei" hinzuzufügen oder zu entfernen, führen Sie die Schritte in diesem Artikel aus. [Hinzufügen der Registerkarte "SharePoint-Dokumente" zum Hauptformular für eine Entität](../maker/model-driven-apps/add-documents-tab-entity-main-form.md)  

*Wo kann ich mein Feedback zu dieser Änderung senden?*
- Sie können Ihr Feedback an das Dynamics 365 Sales Office-und Teams-Integrationsteam an dieser e-Mail-Adresse senden: d365_ot_crew@microsoft.com

### <a name="see-also"></a>Siehe auch
[Integration von SharePoint, OneNote und onedrive in Common Data Service](../maker/common-data-service/sharepoint-onedrive-onenote-intro.md)