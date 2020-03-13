---
title: Verwenden von OneDrive for Business | Microsoft-Dokumentation
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 03/02/2020
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5cfbed161ca920db3ce474371aa435189dc12543
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79240003"
---
# <a name="use-onedrive-for-business"></a>Verwenden von OneDrive for Business 

In diesem Artikel erfahren Sie, wie Sie persönliche Dokumente in Common Data Service-Apps mithilfe von OneDrive for Business erstellen und verwalten. Weitere Informationen:  [Was ist OneDrive for Business?](https://support.office.com/article/What-is-OneDrive-for-Business-187f90af-056f-47c0-9656-cc0ddca7fdc2)


Bevor Sie OneDrive for Business verwenden können, muss OneDrive for Business von Ihrem Systemadministrator aktiviert werden. Weitere Informationen:

-   [Suchen Sie nach Ihrem Administrator oder Supportmitarbeiter](find-admin.md).  

-   [OneDrive for Business (lokal) aktivieren](https://docs.microsoft.com/power-platform/admin/enable-onedrive-for-business)  


## <a name="the-first-time-you-view-your-documents"></a>Das erste Anzeigen Ihrer Dokumente  

1. Öffnen Sie einen Datensatz, und navigieren Sie zur Ansicht **Zugeordnetes Raster des Dokuments**. Öffnen Sie z. B. einen Kontaktdatensatz.

2.  Klicken Sie beim geöffneten Datensatz auf die Registerkarte **Verknüpft** und dann auf **Dokumente**.

     > [!div class="mx-imgBorder"]
     > ![Öffnen der Registerkarte „Dokumente“ in einem Datensatz](media/onedrive_nav.png "Öffnen der Registerkarte „Dokumente“ in einem Datensatz")

3.  Klicken Sie auf **Dokumentspeicherort**  >  **OneDrive**.

     > [!div class="mx-imgBorder"]
     > ![Öffnen der Registerkarte „Dokumente“ und Klicken auf OneDrive](media/onedrive_menu.png "Öffnen der Registerkarte „Dokumente“ und Klicken auf OneDrive")

4. Sobald OneDrive for Business aktiviert wurde, wird das folgende Dialogfeld angezeigt, wenn Sie zur Registerkarte **Dokumente** navigieren, um Dokumente in Common Data Service anzuzeigen und eine Datei in OneDrive hochzuladen, oder wenn Sie versuchen, ein neues Dokument oder einen neuen Ordner zu erstellen.  

    > [!div class="mx-imgBorder"]
    > ![Ändern Ihres OneDrive-Ordners](media/setup_onedrive.png "Ändern Ihres OneDrive-Ordners")  

5. Klicken Sie auf **Ordnerspeicherort ändern**, um einen neuen Speicherort auszuwählen, an dem OneDrive-Dokumente gespeichert werden sollen, oder klicken Sie auf **Fortfahren**, um den Standardspeicherort für Ordner zu akzeptieren.

  
## <a name="view-existing-onedrive-documents"></a>Anzeigen vorhandener OneDrive-Dokumente 
 
1. Öffnen Sie einen Datensatz, und navigieren Sie zur Ansicht **Zugeordnetes Raster des Dokuments**. Öffnen Sie z. B. einen Kontaktdatensatz.

2. Klicken Sie beim geöffneten Datensatz auf die Registerkarte **Verknüpft** und dann auf **Dokumente**.
 
    > [!div class="mx-imgBorder"]
    > ![Öffnen der Registerkarte „Dokumente“ in einem Datensatz](media/onedrive_nav.png "Öffnen der Registerkarte „Dokumente“ in einem Datensatz")
 
3. Klicken Sie auf **Dokumentspeicherort**, um die Dokumentliste zu filtern.

    > [!div class="mx-imgBorder"]
    > ![Öffnen des Dokumentspeicherorts](media/onedrive_doc_location.png "Öffnen des Dokumentspeicherorts")

4.  Wählen Sie anhand der Informationen in der folgenden Tabelle einen Speicherort aus.  

   |    Dokumentspeicherort      |  Beschreibung                                   |
   |---------------------------|------------------------------------------------|
   |      OneDrive             | In OneDrive for Business gespeicherte Dokumente      |
   | Auf der Standardwebsite gespeicherte Dokumente | Auf der Standard-SharePoint-Website gespeicherte Dokumente  |
   | Für mich freigegeben            | Dokumente, die andere Personen für Sie freigegeben haben, und die mit diesem Datensatz verknüpft sind<!--note from editor: Edit okay? I haven't seen an "app record" defined.-->    |
   |  Alle Standorte            |     Alle Dokumentspeicherorte, die mit diesem Datensatz verknüpft sind     |

5. Nachdem Sie einen Speicherort ausgewählt haben, werden die Dokumente angezeigt, die an diesem Speicherort gespeichert sind.

## <a name="create-a-new-document-and-save-it-to-onedrive"></a>Erstellen eines neuen Dokuments und Speichern in OneDrive

1. Öffnen Sie einen Datensatz, und navigieren Sie zur Ansicht **Zugeordnetes Raster des Dokuments**. Öffnen Sie z. B. einen Kontaktdatensatz.

2. Klicken Sie beim geöffneten Datensatz auf die Registerkarte **Verknüpft** und dann auf **Dokumente**.
 
    > [!div class="mx-imgBorder"]
    > ![Öffnen der Registerkarte „Dokumente“ in einem Datensatz](media/onedrive_nav.png "Öffnen der Registerkarte „Dokumente“ in einem Datensatz")

2. Klicken Sie auf **Dokumentspeicherort**, und ändern Sie den Speicherort in **OneDrive**.

3. Klicken Sie auf **Neu**, und wählen Sie dann einen Dokumenttyp aus, z. B. PowerPoint oder Word. 

    > [!div class="mx-imgBorder"]
    > ![Erstellen eines neuen Dokuments](media/onedrive_new_doc.png "Erstellen eines neuen Dokuments")

4. Geben Sie einen Dokumentnamen ein, und klicken Sie dann auf **Speichern**.  


## <a name="things-to-consider"></a>Zu beachtende Aspekte 

Beachten Sie Folgendes hinsichtlich OneDrive for Business in Common Data Service:

- OneDrive-Speicherordner werden in der aktuellen Common Data Service-Sprache des Benutzers erstellt. Wenn die Sprache geändert wird, werden neue Ordner in der neuen Sprache erstellt. Alte Ordner behalten die bisherige Sprache.  

- Zwischen der Freigabe von Dokumenten in OneDrive und ihrer Verfügbarkeit für Benutzer kann es zu einer Verzögerung kommen. 
