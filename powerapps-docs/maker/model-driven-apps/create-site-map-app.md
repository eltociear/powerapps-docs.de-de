---
title: Erstellen einer modellgesteuerten App-Siteübersicht für eine App in PowerApps | Microsoft-Dokumentation
description: Informationen zum Erstellen einer Siteübersicht für Ihre App
keywords: ''
ms.date: 05/29/2018
ms.service: crm-online
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 2461bd71-6cb4-46b7-8d1f-6a0aa3dca809
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 18
topic-status: Drafting
ms.openlocfilehash: 2c3f1f4f22df6ed8b4824f1942e3fd202362ea9d
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39684449"
---
# <a name="tutorial-create-a-model-driven-app-site-map-for-an-app-using-the-site-map-designer"></a>Tutorial: Erstellen einer modellgesteuerten App-Siteübersicht für eine App mithilfe des Siteübersicht-Designers

In diesem Tutorial führen Sie verschiedene Siteübersichtsaufgaben wie das Erstellen einer neuen Siteübersicht und Hinzufügen eines Bereichs, einer Gruppe und eines Unterbereichs durch.

Siteübersichten definieren die Navigation für Ihre App. Erstellen Sie mühelos eine Siteübersicht für Ihre App mit dem Siteübersichts-Designer auf Kachelbasis. Verwenden Sie den Designer, um Komponenten in den Entwurfszeichenbereich zu ziehen, eine Vorschau Ihrer Arbeit anzuzeigen und die Sitemap sofort zu veröffentlichen. Systemanpasser sowie alle Benutzer mit den erforderlichen Berechtigungen können schnell Siteübersichten für Apps erstellen.  
  
Mit dem Siteübersichts-Designer können Sie auch Bereichs-, Unterbereichs- oder Gruppentitel in den von der Umgebung unterstützten Sprachen definieren.  
  
Eine Standardsiteübersicht ist verfügbar. Sie können diese Siteübersicht bearbeiten oder Siteübersichten für neue Apps mit dem Siteübersichts-Designer konfigurieren. Der Siteübersichts-Designer ist in den App-Designer integriert.  

## <a name="prerequisites"></a>Voraussetzungen
Stellen Sie sicher, dass Sie die Sicherheitsrolle „Systemadministrator“ oder „Systemanpasser“ oder gleichwertige Berechtigungen haben.  Insbesondere kann jeder Benutzer mit den folgenden Berechtigungen auch Apps erstellen:  
-   Berechtigungen zum Erstellen, Lesen und Schreiben für die App-Entität  
-   Lese- und Schreibberechtigungen für die Anpassungenentität  
-   Leseberechtigungen für die Lösungsentität

Sie können diese Berechtigungen auf der Registerkarte **Anpassung** einer Sicherheitsrolle anzeigen oder festlegen.
  
## <a name="create-a-site-map-for-an-app"></a>Erstellen einer Siteübersicht für eine App  
  
1. Wählen Sie im App-Designer-Zeichenbereich im Bereich **Siteübersicht** **Siteübersichts-Designer öffnen** ![Schaltfläche „Siteübersichts-Designer öffnen“](media/dynamics365-open-designer.PNG "Schaltfläche „Siteübersichts-Designer öffnen“") aus.  
  
     Der Siteübersichts-Designer öffnet einen Zeichenbereich, der bereits mit einem Bereich, einer Gruppe und einem Unterbereich gefüllt ist. Wählen Sie die Bereichs-, Gruppen- oder Unterbereichskachel aus, um ihre Eigenschaften zu ändern.  
  
    > [!NOTE]
    >  Bei Auswahl von **Siteübersichts-Designer öffnen** ![Schaltfläche „Siteübersichts-Designer öffnen“](media/dynamics365-open-designer.PNG "Schaltfläche „Siteübersichts-Designer öffnen“") im Zeichenbereich des App-Designers wird automatisch eine neue Siteübersicht erstellt (wenn noch keine Siteübersicht vorhanden ist), und die neue Siteübersicht erhält den gleichen Namen wie die App und ebenso den eindeutigen Namen der App als eindeutigen Namen. 

   ![Wählen Sie „Siteübersicht“ aus](media/app-designer-sitemap-location.png "Wählen Sie „Siteübersicht“ aus") 
  
2.  [Fügen Sie einen Bereich zur Siteübersicht hinzu](create-site-map-app.md#bkmk_AddArea).  
  
3.  [Fügen Sie eine Gruppe zur Siteübersicht hinzu](create-site-map-app.md#bkmk_AddGroup).  
  
4.  [Fügen Sie einen Unterbereich zur Siteübersicht hinzu](create-site-map-app.md#bkmk_AddSubarea).  
  
5.  Wählen Sie **Speichern**.  
  
    > [!NOTE]
    >  Die neue Siteübersicht wird der App zugeordnet ist, wenn Sie zum App-Designer zurückgehen und **Speichern** auswählen. Wenn eine Siteübersicht konfiguriert ist, wird **Konfiguriert** auf der Siteübersichtskachel angezeigt, andernfalls **Nicht konfiguriert**.  Wenn Sie den Siteübersichts-Designer im App-Designer öffnen und eine neue Siteübersicht konfigurieren, aber den Browser schließen, bevor Sie die Siteübersicht der App zuordnen, wird die Siteübersicht basierend auf dem eindeutigen App-Namen automatisch der App zugeordnet, wenn Sie das nächste Mal den Siteübersichts-Designer öffnen.  
  
6.  Klicken Sie auf **Veröffentlichen**.  
  
## <a name="edit-the-default-site-map"></a>Bearbeiten der Standardsiteübersicht 

 In Ihrer Umgebung ist eine Standardsiteübersicht enthalten.  
  
1. Öffnen Sie den Projektmappen-Explorer.  
  
2. Wählen Sie im Projektmappenfenster unter **Komponenten** die Option **Clienterweiterungen** aus.  

3. Wählen Sie auf der Komponentensymbolleiste **Vorhandene hinzufügen** > **Siteübersicht** aus.

4. Wählen Sie in der Liste der Lösungskomponenten die Siteübersicht mit dem Namen **Siteübersicht** aus und dann **OK**.
  
5.  Doppelklicken Sie, um die von Ihnen hinzugefügte Siteübersicht auszuwählen, die den Anzeigenamen **Siteübersicht** hat und sich in einem **Verwalteten** Zustand befindet. Sie können auch die Siteübersicht und dann auf der Symbolleiste **Bearbeiten** auswählen.  
  
     Die Siteübersicht wird im Siteübersichts-Designer geöffnet.  
  
6.  [Fügen Sie einen Bereich zur Siteübersicht hinzu](create-site-map-app.md#bkmk_AddArea).  
  
7.  [Fügen Sie eine Gruppe zur Siteübersicht hinzu](create-site-map-app.md#bkmk_AddGroup).  
  
8.  [Fügen Sie einen Unterbereich zur Siteübersicht hinzu](create-site-map-app.md#bkmk_AddSubarea).  
  
9. Wählen Sie **Speichern**.  
  
10. Klicken Sie auf **Veröffentlichen**.  
  
<a name="bkmk_AddArea"></a>   
## <a name="add-an-area-to-the-site-map"></a>Hinzufügen eines Bereichs zur Siteübersicht  
  
1.  Wählen Sie **Hinzufügen** ![Schaltfläche „Hinzufügen“ im Designer](media/dynamics365-designer-addbutton.PNG "Schaltfläche „Hinzufügen“ im Designer") im Zeichenbereich des Siteübersichts-Designer und dann **Bereich** aus.  
  
     oder  
  
     Ziehen Sie von der Registerkarte **Komponenten** die Kachel **Bereich** auf das leere Feld im Zeichenbereich. Sie sehen das leere Feld, wenn Sie die Kachel auf die richtige Stelle im Zeichenbereich verschieben.  
  
2.  Wählen Sie den Bereich aus, den Sie gerade hinzugefügt haben. Die Registerkarte **Eigenschaften** im Bereich rechts neben dem Zeichenbereich ist hervorgehoben.  
  
3.  Fügen Sie die Bereichseigenschaften hinzu, oder bearbeiten Sie sie.  
  
     Führen Sie unter **Allgemein**Folgendes aus:  
  
    - **Titel**: Geben Sie den Titel für den Bereich in der Basissprache der Organisation ein.  
  
    - **Symbol**: Ein Standardanwendungssymbol ist ausgewählt. Wählen Sie ein anderes Symbol für den Bereich aus der Liste der in der Lösung verfügbaren Webressourcen aus.  
  
    - **ID**: Eine eindeutige ID wird automatisch generiert, aber Sie können einen anderen Wert eingeben, wenn Sie möchten. Sie sollten die angegebene ID verwenden, denn falls die ID, die Sie eingeben, nicht eindeutig ist, könnten Benutzer eine Fehlermeldung erhalten, wenn sie die App verwenden, oder Sie erhalten möglicherweise eine Fehlermeldung, wenn Sie eine Lösung importieren, die diese Siteübersicht enthält.  
  
    - **Anzeigen von Gruppen**: Aktivieren Sie dieses Kontrollkästchen, um Gruppen von Unterbereichen im Navigationsbereich anzuzeigen.  
  
     Führen Sie unter **Erweitert** Folgendes aus:  
  
    - **Weitere Titel**: Wenn Ihre Organisation mehrere Sprachen verwendet, wählen Sie eine Sprache (Gebietsschema) für den Titel aus, geben Sie den Titel ein, und wählen Sie dann **Hinzufügen** ![Schaltfläche „Hinzufügen“ im Siteübersichts-Designer](media/add-icon-sitemap-designer.png "Schaltfläche „Hinzufügen“ im Siteübersichts-Designer") aus. Sie können Titel für so viele Sprachen, wie Ihre Organisation verwendet, erstellen, bearbeiten oder löschen. Allerdings können Sie nur einen Titel pro Sprache haben.  
  
    - **Weitere Beschreibung**: Wenn Ihre Organisation mehrere Sprachen verwendet, wählen Sie eine Sprache für die Beschreibung aus, geben Sie die Beschreibung ein, und wählen Sie dann **Hinzufügen** ![Schaltfläche „Hinzufügen“ im Siteübersichts-Designer](media/add-icon-sitemap-designer.png "Schaltfläche „Hinzufügen“ im Siteübersichts-Designer") aus. Sie können Beschreibungen für so viele Sprachen, wie Ihre Organisation verwendet, erstellen, bearbeiten oder löschen. Allerdings können Sie nur eine Beschreibung pro Sprache haben.  
  
    - **URL**: Geben Sie die URL für den Dynamics 365 für Outlook-Ordner ein, der den Bereich darstellt.  
  
<a name="bkmk_AddGroup"></a>   
## <a name="add-a-group-to-the-site-map"></a>Hinzufügen einer Gruppe zur Siteübersicht  
  
1.  Wählen Sie im Zeichenbereich des Siteübersichts-Designers den Bereich aus, dem Sie die Gruppe hinzufügen möchten.  
2.  Wählen Sie **Hinzufügen** ![Schaltfläche „Hinzufügen“ im Designer](media/dynamics365-designer-addbutton.PNG "Schaltfläche „Hinzufügen“ im Designer") und dann **Gruppe** aus.  
  
     oder  
  
     Ziehen Sie von der Registerkarte **Komponenten** die Kachel **Gruppe** auf ein leeres Feld unter dem **Bereich** im Zeichenbereich. Sie sehen das leere Feld, wenn Sie die Kachel auf die richtige Stelle im Zeichenbereich verschieben.  
  
3.  Wählen Sie die Gruppe aus, die Sie gerade hinzugefügt haben.  
  
4.  Fügen Sie auf der Registerkarte **Eigenschaften** Gruppeneigenschaften hinzu, oder bearbeiten Sie sie:  
  
     Führen Sie unter **Allgemein**Folgendes aus:  
  
    - **Titel**: Geben Sie den Titel für die Gruppe in der Basissprache der Organisation ein.  
  
    - **ID**: Eine eindeutige ID wird automatisch generiert. Geben Sie einen anderen Wert ein, falls erforderlich. Sie sollten die automatische ID verwenden, denn falls die ID, die Sie eingeben, nicht eindeutig ist, könnten Sie eine Fehlermeldung erhalten, wenn Sie eine Lösung importieren, die diese Siteübersicht enthält.  
  
     Führen Sie unter **Erweitert** Folgendes aus:  
  
    - **Weitere Titel**: Wenn Ihre Organisation mehrere Sprachen verwendet, wählen Sie eine Sprache (Gebietsschema) für den Titel aus, geben Sie den Titel für die Gruppe ein, und wählen Sie dann **Hinzufügen** ![Schaltfläche „Hinzufügen“ im Siteübersichts-Designer](media/add-icon-sitemap-designer.png "Schaltfläche „Hinzufügen“ im Siteübersichts-Designer") aus. Sie können Titel für so viele Sprachen, wie Ihre Organisation verwendet, erstellen, bearbeiten oder löschen. Allerdings können Sie nur einen Titel pro Sprache haben.  
  
    - **Weitere Beschreibungen**: Wenn Ihre Organisation mehrere Sprachen verwendet, wählen Sie eine Sprache für die Beschreibung aus, geben Sie die Beschreibung für die Gruppe ein, und wählen Sie dann **Hinzufügen** ![Schaltfläche „Hinzufügen“ im Siteübersichts-Designer](media/add-icon-sitemap-designer.png "Schaltfläche „Hinzufügen“ im Siteübersichts-Designer") aus. Sie können Beschreibungen für so viele Sprachen, wie Ihre Organisation verwendet, erstellen, bearbeiten oder löschen. Allerdings können Sie nur eine Beschreibung pro Sprache haben.  
  
    - **URL**: Geben Sie die URL für den Dynamics 365 für Outlook-Ordner ein, der die Gruppe darstellt.  
  
    - **Als Profil festlegen**: Aktivieren Sie dieses Kontrollkästchen, um anzugeben, ob diese Gruppe ein vom Benutzer auswählbares Profil für den Arbeitsbereich darstellt. Die als vom Benutzer auswählbares Profil festgelegte Gruppe wird als Option in Ihren persönlichen Optionen zur Verfügung gestellt. Dies gilt nur für Gruppen im Bereich **Arbeitsbereich**.  
  
<a name="bkmk_AddSubarea"></a>   
## <a name="add-a-subarea-to-a-group-in-the-site-map"></a>Hinzufügen eines Unterbereichs zu einer Gruppe in der Siteübersicht  
  
1.  Wählen Sie **Hinzufügen** ![Schaltfläche „Hinzufügen“ im Designer](media/dynamics365-designer-addbutton.PNG "Schaltfläche „Hinzufügen“ im Designer") im Zeichenbereich des Siteübersichts-Designer und dann **Unterbereich** aus.  
  
     oder  
  
     Ziehen Sie von der Registerkarte **Komponenten** die Kachel **Unterbereich** auf ein leeres Feld unter dem Abschnitt **Gruppe** im Zeichenbereich. Sie sehen das leere Feld, wenn Sie die Kachel auf die richtige Stelle im Zeichenbereich verschieben.  
  
2.  Wählen Sie den Unterbereich aus, den Sie gerade hinzugefügt haben.  
  
3.  Fügen Sie auf der Registerkarte **Eigenschaften** Unterbereichseigenschaften hinzu, oder bearbeiten Sie sie:  
  
     Führen Sie unter **Allgemein**Folgendes aus:  
  
    - **Typ**: Wählen Sie aus, ob der Unterbereich, den Sie hinzufügen, ein Dashboard, eine Entität, Webressource oder URL ist.  
  
    - **Entität**: Wählen Sie die Entität aus, für die der Unterbereich bestimmt ist. Dieses Feld ist deaktiviert, sofern der Typ des Unterbereichs nicht **Entität** in der Dropdownliste **Typ** ist.  
  
    - **URL**: Geben Sie eine URL für die Hauptseite der Anwendung an, die angezeigt wird, wenn dieser Unterbereich ausgewählt wird. Dieses Feld ist deaktiviert, wenn Sie **Entität** in der Dropdownliste **Typ** ausgewählt haben.  
  
    - **Standarddashboard**: Wählen Sie das Standarddashboard aus, das für diesen Unterbereich angezeigt werden soll. Dieses Feld ist deaktiviert, wenn Sie nicht **Dashboard** in der Dropdownliste **Typ** ausgewählt haben.  
  
    - **Titel**: Geben Sie den Titel für den Unterbereich in der Basissprache der Organisation ein.  
  
    - **Symbol**: Ein Standardanwendungssymbol ist ausgewählt. Wählen Sie ein anderes Symbol für den Unterbereich aus der Liste der in der Lösung verfügbaren Webressourcen aus.  
  
    - **ID**. Eine eindeutige ID wird automatisch generiert. Geben Sie eine andere eindeutige ID ein, falls erforderlich.  
  
    - **Parameterübergabe**. Aktivieren Sie dieses Kontrollkästchen, um Informationen über die Organisation und den Sprachkontext an die URL zu übergeben. Dieses Kontrollkästchen ist nur aktiviert, wenn der Unterbereichstyp eine Webressource oder ein URL-basierter Unterbereich ist.  
  
     Führen Sie unter **Erweitert** Folgendes aus:  
 
    - **Berechtigungen**: Definiert, ob ein Unterbereich basierend auf Berechtigungen, die in dem Benutzer zugewiesenen Sicherheitsrollen verfügbar sind, angezeigt wird. Wählen Sie den Namen der Entität aus, für die Berechtigungen überprüft werden sollen, und aktivieren Sie dann die Kontrollkästchen, um Berechtigungen zuzuweisen. 
  
    - **Weitere Titel**: Wenn Ihre Organisation mehrere Sprachen verwendet, wählen Sie eine Sprache für den Titel aus, geben Sie den Titel für den Unterbereich ein, und wählen Sie dann **Hinzufügen** aus. Sie können Titel für so viele Sprachen, wie Ihre Organisation verwendet, erstellen, bearbeiten oder löschen. Allerdings können Sie nur einen Titel pro Sprache haben.  
  
    - **Weitere Beschreibungen**: Wenn Ihre Organisation mehrere Sprachen verwendet, wählen Sie eine Sprache für die Beschreibung aus, geben Sie die Beschreibung für den Unterbereich ein, und wählen Sie dann **Hinzufügen** aus. Sie können Beschreibungen für so viele Sprachen, wie Ihre Organisation verwendet, erstellen, bearbeiten oder löschen. Allerdings können Sie nur eine Beschreibung pro Sprache haben.  
  
    - **SKUs**: Wählen Sie die Versionen von Dynamics 365 Customer Engagement aus, die diesen Unterbereich anzeigen.  
  
    - **Client**: Wählen Sie den Clienttyp aus, der diesen Unterbereich anzeigt.  
  
    - **Outlook-Verknüpfung**: Wählen Sie das in Dynamics 365 für Outlook anzuzeigende Symbol aus.  
  
    - **Offlineverfügbarkeit**: Aktivieren Sie dieses Kontrollkästchen, um diesen Unterbereich für Benutzer verfügbar zu machen, wenn sie in Dynamics 365 für Outlook offline sind.  
  
## <a name="organize-areas-groups-and-subareas"></a>Organisieren von Bereichen, Gruppen und Unterbereichen  
 Sie können Ihre Bereiche, Gruppen und Unterbereiche durch Ziehen an neue Positionen organisieren. Ein Containerfeld wird angezeigt, wo Sie die Kacheln ablegen können. Hier sind z.B. folgende Aktionen möglich:  
  
-   Verschieben Sie einen Unterbereich an eine neue Position innerhalb der gleichen Gruppe oder in einer anderen Gruppe unter dem gleichen Bereich.  
  
-   Verschieben Sie einen Unterbereich an eine neue Position innerhalb einer Gruppe unter einem anderen Bereich.  
  
-   Verschieben Sie eine Gruppe an eine neue Position innerhalb des gleichen Bereichs.  
  
-   Verschieben Sie eine Gruppe an eine neue Position in einem anderen Bereich.  
  
-   Verschieben Sie einen Bereich an eine neue Position.  
  
## <a name="clone-a-component-in-a-site-map"></a>Klonen einer Komponente in einer Siteübersicht  
 Um eine Kopie einer vorhandenen Komponente zu erstellen, wählen Sie die Komponente aus und dann auf der Symbolleiste **Klonen**.  Alle Details der geklonten Komponente außer ID und Titel entsprechen der Basiskomponente. Die ID wird nach dem Zufallsprinzip generiert. 
  
 Beim Klonen eines Bereichs wird der geklonte Bereich rechts neben dem aktuell ausgewählten Bereich hinzugefügt. Beim Klonen einer Gruppe wird die geklonte Gruppe rechts neben der aktuell ausgewählten Gruppe hinzugefügt. Beim Klonen eines Unterbereichs wird der geklonte Unterbereich unterhalb des aktuell ausgewählten Unterbereichs hinzugefügt.  
  
## <a name="delete-an-area-group-or-subarea-from-a-site-map"></a>Löschen eines Bereichs, einer Gruppe oder eines Unterbereichs aus einer Siteübersicht  
 Um eine Siteübersichtskomponente zu löschen, wählen Sie die Komponentenkachel und dann auf der Symbolleiste **Löschen** aus. Wenn Sie einen Bereich löschen, werden alle Gruppen und Unterbereiche im Bereich auch gelöscht. Wenn Sie eine Gruppe löschen, werden auf ähnliche Weise die Gruppe und Unterbereiche darin gelöscht.  
  
## <a name="clients-supported"></a>Unterstützte Clients  
 In der folgende Tabelle wird erläutert, welche Clients für verschiedene Siteübersichten unterstützt werden.  
 
|Siteübersichten|Unterstützte Clients|  
|---------------|-----------------------|  
|Neue Apps| Einheitliche Oberfläche und Dynamics 365 Customer Engagement-Web-App |  
|Siteübersicht für Dynamics 365 – benutzerdefinierte App | Dynamics 365 Customer Engagement-Web-App und Dynamics 365 für Outlook |  
|Standardgeschäfts-Apps (Sales, Sales Hub, Customer Service, Customer Service Hub, Field Service, Project Service Automation)| Dynamics 365 Customer Engagement-Web-App und Einheitliche Oberfläche|  
 
  
### <a name="next-steps"></a>Nächste Schritte  
 [Erstellen oder Bearbeiten einer App](create-edit-app.md)   
 [Hinzufügen oder Bearbeiten von App-Komponenten](add-edit-app-components.md)
