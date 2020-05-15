---
title: Zusammenarbeiten mithilfe von SharePoint | Microsoft-Dokumentation
description: Hier erfahren Sie, wie die Zusammenarbeit mithilfe von SharePoint in einer modellgesteuerten App funktioniert
documentationcenter: ''
author: mduelae
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 03/02/2020
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3491468724662edcac932cf37345730defd6a006
ms.sourcegitcommit: 5b6e6b41a3fc4d7f1aea46ec66c086b784efacac
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/03/2020
ms.locfileid: "3303206"
---
# <a name="collaborate-using-sharepoint"></a>Zusammenarbeit mithilfe von SharePoint 

Mit Common Data Service können Sie Ihre Dokumente in SharePoint speichern und aus der App verwalten. Die Dokumente, die Sie in der Ihrer erstellen, werden auf SharePoint gespeichert und automatisch mit Ihren Desktop- und Mobilgeräten synchronisiert.

Bevor Sie SharePoint zum Ablegen von Dokumenten verwenden können, muss es von Ihrem Systemadministrator aktiviert werden. Weitere Informationen:

-   [Suchen Sie nach Ihrem Administrator oder Supportmitarbeiter](find-admin.md).  

-   [Ihre Dokumente mit SharePoint verwalten](https://docs.microsoft.com/power-platform/admin/manage-documents-using-sharepoint)  

## <a name="where-do-you-access-the-documents-from"></a>Von wo aus können Sie auf die Dokumente zugreifen?

1. Für Datensatztypen, die die Dokumentenverwaltung unterstützen, öffnen Sie den Datensatz, wählen die Registerkarte **Verknüpft** und dann **Dokumente**.

   > [!div class="mx-imgBorder"]
   > ![Öffnen der Registerkarte „Dokumente“ in einem Datensatz](media/onedrive_nav.png "Öffnen der Registerkarte „Dokumente“ in einem Datensatz")

2. Klicken Sie auf **Dokumentspeicherort**  >  **Documents on Default Site 1** (Dokumente auf der Standardwebsite 1). Wenn SharePoint aktiviert ist, ist der Speicherort standardmäßig auf **Dokumente auf der Standardwebsite 1** festgelegt.

   > [!div class="mx-imgBorder"]
   > ![Standardspeicherort](media/sharepoint_defualtsite.png "Standardspeicherort")


## <a name="create-a-new-document-and-save-it-to-sharepoint"></a>Erstellen eines neuen Dokuments und Speichern in SharePoint

1. Öffnen Sie einen Datensatz, und navigieren Sie zur Ansicht **Zugeordnetes Raster des Dokuments**. Öffnen Sie z. B. einen Kontaktdatensatz.

2. Klicken Sie beim geöffneten Datensatz auf die Registerkarte **Verknüpft** und dann auf **Dokumente**.
 
    > [!div class="mx-imgBorder"]
    > ![Öffnen der Registerkarte „Dokumente“ in einem Datensatz](media/onedrive_nav.png "Öffnen der Registerkarte „Dokumente“ in einem Datensatz")

2. Klicken Sie auf **Dokumentspeicherort**, und ändern Sie den Speicherort in **Documents on Default Site 1** (Dokumente auf der Standardwebsite 1).

3. Klicken Sie auf **Neu**, und wählen Sie dann einen Dokumenttyp aus, z. B. Word, Excel oder PowerPoint.

    > [!div class="mx-imgBorder"]
    > ![Ein neues Dokument erstellen](media/onedrive_new_doc.png "Ein neues Dokument erstellen")

4. Geben Sie einen Dokumentnamen ein, und wählen Sie dann **Speichern**.  

## <a name="create-a-new-folder-in-the-default-sharepoint-site-location"></a>Erstellen eines neuen Ordners am Standardspeicherort der SharePoint Website

1. Öffnen Sie einen Datensatz, und navigieren Sie zur Ansicht **Zugeordnetes Raster des Dokuments**. Öffnen Sie z. B. einen Kontaktdatensatz.

2. Klicken Sie beim geöffneten Datensatz auf die Registerkarte **Verknüpft** und dann auf **Dokumente**.
 
    > [!div class="mx-imgBorder"]
    > ![Öffnen der Registerkarte „Dokumente“ in einem Datensatz](media/onedrive_nav.png "Öffnen der Registerkarte „Dokumente“ in einem Datensatz")

2. Klicken Sie auf **Dokumentspeicherort**, und ändern Sie den Speicherort in **Documents on Default Site 1** (Dokumente auf der Standardwebsite 1).

3. Klicken Sie auf **Neu** und dann auf **Ordner**.

    > [!div class="mx-imgBorder"]
    > ![Neuen Ordner erstellen](media/Sharepoint_new_folder.png "Neuen Ordner erstellen")
    
 4. Geben Sie einen Ordnernamen ein, und klicken Sie auf **Speichern**.  
 
 
 ## <a name="upload-an-existing-document-to-sharepoint-from-your-app"></a>Ein bestehendes Dokument aus Ihrer App auf SharePoint hochladen

1. Navigieren Sie zu dem Datensatz, für den Sie das Dokument erstellen möchten, klicken Sie auf die Registerkarte **Verknüpft** und dann auf **Dokumente**.
 
2. Wählen Sie **Hochladen.**

   > [!div class="mx-imgBorder"]
   > ![Hochladen von Dokumenten](media/upload_doc.png "Hochladen von Dokumenten")

3. Wählen Sie die Datei aus, die Sie hochladen möchten. Sie können immer nur eine Datei nach der anderen auswählen.

   Das Dokument wird am Dokumentspeicherort erstellt, an dem Sie sich gerade befinden.

   > [!Note]
   > Sie können eine Datei mit bis zu 50 MB hochladen. Wenn Ihre Internetverbindung langsam ist, tritt unter Umständen ein Fehler beim Hochladen von großen Dateien aus.

4. Wenn Dateien mit demselben Namen in SharePoint vorhanden sind, wählen Sie aus, ob Sie die Dateien überschreiben möchten.

5. Wählen Sie **OK** aus.

## <a name="manage-sharepoint-locations"></a>Verwalten von SharePoint Standorten

Sie können in Ihrer App neue oder bestehende SharePoint Positionen anlegen oder bearbeiten in Common Data Service.

### <a name="edit-a-location"></a>Bearbeiten eines Speicherorts

1. Öffnen Sie einen Datensatz, klicken Sie auf die Registerkarte **Verknüpft** und dann auf **Dokumente**.

2. Klicken Sie auf **Speicherort bearbeiten**, und wählen Sie dann einen Speicherort für die SharePoint Website aus.

   Das Dialogfeld **Speicherort bearbeiten** wird angezeigt.

   > [!div class="mx-imgBorder"]
   > ![Speicherort bearbeiten](media/edit_location.png "Speicherort bearbeiten")

3. Der Anzeigename, der übergeordnete Standort und der Ordnername werden automatisch aufgefüllt. Geben Sie Informationen zum neuen Standort ein, und wählen Sie dann **Speichern** aus.

### <a name="add-a-new-location"></a>Hinzufügen eines neuen Speicherorts

1. Öffnen Sie einen Datensatz, klicken Sie auf die Registerkarte **Verknüpft** und dann auf **Dokumente**.

2. Klicken Sie auf **Speicherort hinzufügen**. 

   Das Dialogfeld **Speicherort hinzufügen** wird angezeigt.

   > [!div class="mx-imgBorder"]
   > ![Speicherort hinzufügen](media/add_location.png "Speicherort hinzufügen")

3. Der Anzeigename, der übergeordnete Standort und der Ordnername werden automatisch aufgefüllt. Ändern Sie die Informationen nach Bedarf, und wählen Sie dann **Speichern** aus.

## <a name="files-tab-faq"></a>Häufig gestellte Fragen zur Registerkarte „Dateien“

*Warum wurde der Speicherort für den Zugriff auf Dokumente verschoben?* 
- Der Befehl wurde verschoben, damit Dokumente leichter, mit weniger Klicks, gefunden werden können.

*Wurde die Registerkarte „Dokumente“ entfernt?*
- Nein, sie wurde nicht entfernt. Benutzer können weiterhin wie gewohnt auf mit dem Datensatz verknüpfte Dokumente zugreifen, indem sie auf das Menü **Verknüpft** und dann auf den Link **Dokumente** klicken.

*Werden mit der Änderung Unterordner in SharePoint immer noch automatisch erstellt werden?*
- Ja. Das Verhalten ist ähnlich dem des Links **Dokumente** unter dem Menü **Verknüpft**. Wenn ein Benutzer zum ersten Mal auf die Registerkarte **Dateien** klickt, wird der entsprechende SharePoint Unterordner vom System erstellt. 

*Gibt es eine Möglichkeit, die Registerkarte „Dateien“ zu anderen Entitäten hinzuzufügen oder zu entfernen?*
- Ja. Hinzufügen oder Entfernen der **Dateien** befolgen Sie auf der Registerkarte die Schritte in diesem Artikel: [Ergänzen Sie die SharePoint Registerkarte Dokumente zum Hauptformular für eine Entität](../maker/model-driven-apps/add-documents-tab-entity-main-form.md)  
