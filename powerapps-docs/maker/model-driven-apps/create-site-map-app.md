---
title: Erstellen einer modellgesteuerte App-Site-Map in Power Apps | MicrosoftDocs
description: Erfahren Sie, wie Sie eine Siteübersicht für Ihre App erstellen
keywords: ''
ms.date: 05/29/2018
ms.service: powerapps
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
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 2dcfea33867b6a5113ed6fd36e20d529608ed0ab
ms.sourcegitcommit: 59f0b3adc56279b5673cbf04b4a55bd7678e1ea7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2020
ms.locfileid: "3091355"
---
# <a name="create-a-model-driven-app-site-map-using-the-site-map-designer"></a>Erstellen einer modellgesteuerten App-Sitemap mit dem Sitemap-Designer

In diesem Lernprogramm werden Sie mehrere Siteübersichtsaufgaben wie das Erstellen einer neuen Siteübersicht und Hinzufügen eines Bereichs, einer Gruppe und eines Unterbereichs ausführen.

Siteübersichten definieren der Navigation für die App. Erstellen Sie eine Siteübersicht für die App, indem Sie den Kachel-basierten Siteübersichtsdesigner verwenden. Verwenden Sie den Designer, um Komponenten auf den Entwurfscanvas zu ziehen, Ihre Arbeit in der Vorschau anzuzeigen und sofort die Siteübersicht zu veröffentlichen. Systemanpasser oder jeder Benutzer mit entsprechenden Berechtigungen können für die Siteübersichten für Apps schnell erstellen.  
  
Mit dem Siteübersichtsdesigner können Sie auch Bereichs-, Unterbereichs- oder Gruppentitel in den Sprachen definieren, die von der Umgebung unterstützt werden.  
  
Eine Standardsiteübersicht ist verfügbar. Sie können diese Siteübersicht bearbeiten, oder neue Siteübersichten für neue Apps mit dem Siteübersichtsdesigner konfigurieren. Der Siteübersichtsdesigner ist mit dem Anwendungsdesigner integriert.  

## <a name="prerequisites"></a>Voraussetzungen
Stellen Sie sicher, dass Sie über die Sicherheitsrolle „Systemadministrator“ oder „Systemanpasser“ bzw. entsprechende Berechtigungen verfügen.  Jeder Benutzer mit den folgenden Berechtigungen kann Apps erstellen:  
-   Erstellen-, Lesen-, Schreiben-Rechte für die App-Entität  
-   Lese- und Schreibrechte in der Entität "Anpassungen"  
-   Leseberechtigungen in der Lösungsentität

Sie können diese Rechte auf der Registerkarte **Anpassung** einer Sicherheitsrolle anzeigen oder festlegen.
  
## <a name="create-a-site-map-for-an-app"></a>Erstellen einer App-Siteübersicht  
  
1. Wählen Sie auf der App Designer-Canvas im Bereich **Siteübersicht** **Siteübersichtdesigner öffnen** ![Schaltfläche Siteübersichtsdesigner öffnen](media/dynamics365-open-designer.PNG "Schaltfläche "Siteübersichts-Designer öffnen"").  
  
     Der Siteübersichtsdesigner wird geöffnet. Der Canvas wird mit einem Bereich, einer Gruppe und einem Unterbereich gefüllt. Wählen Sie die Bereichs-, Unterbereichs- oder die Gruppenkachel, um die Eigenschaften zu ändern.  
  
    > [!NOTE]
    >  Wenn Sie **Öffnen des Sitemap-Designers** ![Öffnen des Sitemap-Designers Schaltfläche](media/dynamics365-open-designer.PNG "Schaltfläche "Siteübersichts-Designer öffnen"") auf der App Designer Canvas auswählen, wird automatisch eine neue Sitemap erstellt (wenn es keine existierende Sitemap gibt), und die neue Sitemap erhält den gleichen Namen wie der App-Name und den gleichen eindeutigen Namen wie der eindeutige Name der App. 

   ![Siteübersicht auswählen](media/app-designer-sitemap-location.png "Siteübersicht auswählen") 
  
2.  [Hinzufügen eines Bereichs zur Siteübersicht](create-site-map-app.md#bkmk_AddArea).  
  
3.  [Hinzufügen einer Gruppe zur Siteübersicht](create-site-map-app.md#bkmk_AddGroup).  
  
4.  [Hinzufügen eines Unterbereiches zu einer Gruppe in der Siteübersicht](create-site-map-app.md#bkmk_AddSubarea).  
  
5.  Wählen Sie **Speichern** aus.  
  
    > [!NOTE]
    >  Die neue Siteübersicht ist der App zugeordnet, wenn Sie wieder zum App-Designer wechseln und **Speichern** wählen. Wenn eine SiteMap konfiguriert ist, wird auf der Siteübersichtskachel **Konfiguriert** angezeigt. Andernfalls erscheint **Nicht konfiguriert** auf der Kachel.  Wenn Sie den Siteübersichtsdesigner aus dem App-Designer öffnen und eine neue Siteübersicht konfigurieren, den Browser aber schließen, bevor Sie die Siteübersicht der App zuordnen, wird die Siteübersicht automatisch der App zugeordnet, wenn Sie den App-Designer das nächste Mal öffnen, entsprechend des eindeutigen Namens der App.  
  
6.  Wählen Sie **Veröffentlichen** aus.  
  
## <a name="edit-the-default-site-map"></a>Bearbeiten der Standardsiteübersicht 

 Ihre Umgebung verfügt über eine Standardsiteübersicht.  
  
1. Öffnen Sie den Projektmappen-Explorer.  
  
2. Wählen Sie im Lösungsfenster unter **Komponenten** **Clienterweiterungen** aus.  

3. Auf der Komponentensymbolleiste wählen Sie **Vorhandenes Element hinzufügen** > **Siteübersicht** aus.

4. In der Liste der Lösungskomponenten wählen Sie die Siteübersicht mit dem Namen **Siteübersicht** und dann **OK** aus.
  
5.  Doppelklicken Sie, um die hinzugefügte Siteübersicht auszuwählen, die den Anzeigenamen **Site Map** und den Status **Verwaltet** hat. Sie können alternativ die Siteübersicht auswählen und dann in der Aktionsleiste **Bearbeiten** wählen.  
  
     Die Siteübersicht wird im Siteübersichtsdesigner geöffnet.  
  
6.  [Hinzufügen eines Bereichs zur Siteübersicht](create-site-map-app.md#bkmk_AddArea).  
  
7.  [Hinzufügen einer Gruppe zur Siteübersicht](create-site-map-app.md#bkmk_AddGroup).  
  
8.  [Hinzufügen eines Unterbereiches zu einer Gruppe in der Siteübersicht](create-site-map-app.md#bkmk_AddSubarea).  
  
9. Wählen Sie **Speichern** aus.  
  
10. Wählen Sie **Veröffentlichen** aus.  
  
<a name="bkmk_AddArea"></a>   
## <a name="add-an-area-to-the-site-map"></a>Hinzufügen eines Bereichs zur Siteübersicht  
  
1.  Wählen Sie **Hinzufügen** ![Hinzufügen-Schaltfläche auf dem Designer](media/dynamics365-designer-addbutton.PNG "Schaltfläche im Designer hinzufügen") auf der Designer Canvas Sitemap-Designers, und wählen Sie dann **Bereich**.  
  
     oder  
  
     Ziehen Sie auf der Registerkarte **Komponenten** die Kachel **Bereich** auf das leere Feld auf dem Canvas. Sie sehen das leere Feld, wenn Sie die Kachel an den richtigen Ort in der Canvas verschieben.  
  
2.  Wählen Sie den Bereich, den Sie gerade hinzugefügt haben. Sie sehen die Registerkarte **Eigenschaften**, die im Bereich rechts neben dem Canvas hervorgehoben wird.  
  
3.  Fügen Sie die Bereichseigenschaften hinzu oder bearbeiten Sie sie.  
  
     Führen Sie unter **Allgemein** die folgenden Schritte aus:  
  
    - **Titel**: Geben Sie einen Titel für den Bereich in der Ausgangssprache der Organisation ein.  
  
    - **Symbol**: Es wird ein standardmäßiges Anwendungssymbol ausgewählt. Wählen Sie ein anderes Symbol für den Bereich aus der Liste aus der Webressourcen aus, die in der Lösung verfügbar ist.  
  
    - **ID**: Eine eindeutige ID wird automatisch generiert, aber Sie können eine andere eingeben, wenn Sie möchten. Es wird empfohlen, das Sie die bereitgestellte ID verwenden. Wenn die eingegebene ID nicht eindeutig ist, erhalten die Benutzer möglicherweise einen Fehler bei der Verwendung der App, oder wenn Sie eine Lösung importieren, die diese Sitemap enthält.  
  
    - **Gruppen anzeigen**: Aktivieren Sie das Kontrollkästchen, um Gruppen aus Unterbereichen im Navigationsbereich anzuzeigen.  
  
     Führen Sie unter **Erweitert** die folgenden Schritte aus:  
  
    - **Weitere Titel**: Wenn Ihre Organisation mehrere Sprachen verwendet, wählen Sie eine Sprache (Gebietsschema) für den Titel aus, geben Sie den Titel ein und wählen dann **Hinzufügen** ![Schaltfläche Hinzufügen im Siteübersichtsdesigner](media/add-icon-sitemap-designer.png "Schaltfläche im Siteübersichtsdesigner hinzufügen"). Sie können für beliebig viele Sprachen Titel für Ihre Organisation erstellen, bearbeiten oder löschen. Sie können jedoch nur einen Titel pro Sprache nutzen.  
  
    - **Weitere Beschreibung**: Wenn Ihre Organisation mehrere Sprachen verwendet, wählen Sie eine Sprache für die Beschreibung aus, geben Sie die Beschreibung ein und wählen dann **Hinzufügen** ![Schaltfläche Hinzufügen im Siteübersichtsdesigner](media/add-icon-sitemap-designer.png "Schaltfläche im Siteübersichtsdesigner hinzufügen"). Sie können für beliebig viele Sprachen Beschreibungen für Ihre Organisation erstellen, bearbeiten oder löschen. Sie können jedoch nur eine Beschreibung pro Sprache nutzen.  
  
    - **URL**: Geben Sie die URL ein, um den Dynamics 365 for Outlook-Ordner zu erstellen, der den Bereich darstellt.  
  
<a name="bkmk_AddGroup"></a>   
## <a name="add-a-group-to-the-site-map"></a>Hinzufügen einer Gruppe zur Siteübersicht  
  
1.  Wählen Sie den Bereich im Siteübersicht-Designer-Canvas, zu dem Sie die Gruppe hinzufügen möchten.  
2.  Wählen Sie **Hinzufügen** ![Schaltfläche Hinzufügen im Designer](media/dynamics365-designer-addbutton.PNG "Schaltfläche im Designer hinzufügen"), und dann **Gruppe**.  
  
     oder  
  
     Ziehen Sie auf der Registerkarte **Komponenten** die Kachel **Gruppe** auf ein leeres Feld unter dem **Bereich** auf der Canvas. Sie sehen das leere Feld, wenn Sie die Kachel an den richtigen Ort in der Canvas verschieben.  
  
3.  Wählen Sie die Gruppe, die Sie gerade hinzugefügt haben.  
  
4.  Fügen Sie auf der **Eigenschaften**-Registerkarte Gruppeneigenschaften hinzu oder bearbeiten Sie sie.  
  
     Führen Sie unter **Allgemein** die folgenden Schritte aus:  
  
    - **Titel**: Geben Sie einen Titel für die Gruppe in der Ausgangssprache der Organisation ein.  
  
    - **ID**: Eine eindeutige ID wird automatisch generiert. Geben Sie eine andere ein falls erforderlich. Es wird empfohlen, dass Sie die automatische ID verwenden. Wenn die eingegebene ID nicht eindeutig ist, tritt möglicherweise ein Fehler auf, wenn Sie eine Lösung importieren, die diese Sitemap enthält.  
  
     Führen Sie unter **Erweitert** die folgenden Schritte aus:  
  
    - **Weitere Titel**: Wenn Ihre Organisation mehrere Sprachen verwendet, wählen Sie eine Sprache (Gebietsschema) für den Titel aus, geben den Titel für die Gruppe ein und wählen dann **Hinzufügen** ![Schaltfläche Hinzufügen im Siteübersichtsdesigner](media/add-icon-sitemap-designer.png "Schaltfläche im Siteübersichtsdesigner hinzufügen"). Sie können für beliebig viele Sprachen Titel für Ihre Organisation erstellen, bearbeiten oder löschen. Sie können jedoch nur einen Titel pro Sprache nutzen.  
  
    - **Weitere Beschreibung**: Wenn Ihre Organisation mehrere Sprachen verwendet, wählen Sie eine Sprache für die Beschreibung aus, geben Sie die Beschreibung für die Gruppe ein und wählen dann **Hinzufügen** ![Schaltfläche Hinzufügen im Siteübersichtsdesigner](media/add-icon-sitemap-designer.png "Schaltfläche im Siteübersichtsdesigner hinzufügen"). Sie können für beliebig viele Sprachen Beschreibungen für Ihre Organisation erstellen, bearbeiten oder löschen. Sie können jedoch nur eine Beschreibung pro Sprache nutzen.  
  
    - **URL**: Geben Sie die URL ein, um den Dynamics 365 for Outlook-Ordner zu rendern, der die Gruppe darstellt.  
  
    - **Als Profil festlegen**: Aktivieren Sie dieses Kontrollkästchen, um anzugeben, ob diese Gruppe ein benutzerselektiertes Profil für den Arbeitsbereich darstellt. Die Gruppe, die als benutzerselektiertes Profil festgelegt ist, wird als Optionen in Ihren persönlichen Optionen angezeigt. Dies gilt nur für Gruppen im Bereich **Arbeitsbereich**.  
  
<a name="bkmk_AddSubarea"></a>   
## <a name="add-a-subarea-to-a-group-in-the-site-map"></a>Hinzufügen eines Unterbereiches zu einer Gruppe in der Siteübersicht  
  
1.  Wählen Sie **Hinzufügen** ![Hinzufügen-Schaltfläche auf dem Designer](media/dynamics365-designer-addbutton.PNG "Schaltfläche im Designer hinzufügen") auf der Designer Canvas Sitemap-Designers, und wählen Sie dann **Unterbereich**.  
  
     oder  
  
     Ziehen Sie auf der Registerkarte **Komponenten** die Kachel **Unterbereich** auf ein leeres Feld unter dem Abschnitt **Gruppe** auf der Canvas. Sie sehen das leere Feld, wenn Sie die Kachel an den richtigen Ort in der Canvas verschieben.  
  
2.  Wählen Sie den Unterbereich, den Sie gerade hinzugefügt haben.  
  
3.  Fügen Sie auf der **Eigenschaften**-Registerkarte Unterbereichseigenschaften hinzu oder bearbeiten Sie sie.  
  
     Führen Sie unter **Allgemein** die folgenden Schritte aus:  
  
    - **Typ**: Wählen Sie aus, ob der Unterbereich, den Sie hinzufügen, ein Dashboard, eine Entität, eine Webressourcen oder eine URL ist.  
  
    - **Entität**: Wählen Sie die Entität aus, für die Unterbereich bestimmt ist. Dieses Feld wird deaktiviert, wenn der Unterbereichstyp in der Dropdownliste **Typ** nicht **Entität** ist.  
  
    - **URL**: Geben Sie eine URL für die Hauptseite der Anwendung an, die angezeigt wird, wenn dieser Unterbereich ausgewählt wird. Dieses Feld wird deaktiviert, wenn Sie **Entität** in der Dropdownliste **Typ** auswählen.  
  
    - **Standarddashboard**: Wählen Sie das Standarddashboard für diesen Unterbereich aus. Dieses Feld wird deaktiviert, wenn Sie kein **Dashboard** in der Dropdownliste **Typ** auswählen.  
  
    - **Titel**: Geben Sie einen Titel für den Unterbereich in der Ausgangssprache der Organisation ein.  
  
    - **Symbol**: Es wird ein standardmäßiges Anwendungssymbol ausgewählt. Wählen Sie ein anderes Symbol für den Unterbereich aus der Liste aus der Webressourcen aus, die in der Lösung verfügbar ist.  
  
    - **ID**. Eine eindeutige ID wird automatisch generiert. Geben Sie eine andere eindeutige ID ein, falls erforderlich.  
  
    - **Parameterübergabe** Aktivieren Sie dieses Kontrollkästchen, um Informationen zur Organisation und zum Sprachkontext zur URL hinzuzufügen. Dieses Kontrollkästchen ist nur aktiviert, wenn der Unterbereichstyp eine Webressource oder ein URL-basierter Unterbereich ist.  
  
     Führen Sie unter **Erweitert** die folgenden Schritte aus:  
 
    - **Rechte**: Definiert, ob ein Unterbereich anhand der Rechte angezeigt wird, die in allen Sicherheitsrollen verfügbar sind, die dem Benutzer zugewiesen werden. Wählen Sie den Namen der Entität aus, deren Rechte Sie überprüfen möchten, und wählen Sie anschließend die Kontrollkästchen aus, um Rechte zuzuweisen. 
  
    - **Weitere Titel**: Wenn Ihre Organisation mehrere Sprachen verwendet, wählen Sie eine Sprache für den Titel, geben den Titel für den Unterbereich ein und wählen **Hinzufügen**. Sie können für beliebig viele Sprachen Titel für Ihre Organisation erstellen, bearbeiten oder löschen. Sie können jedoch nur einen Titel pro Sprache nutzen.  
  
    - **Weitere Beschreibungen**: Wenn Ihre Organisation mehrere Sprachen verwendet, wählen Sie eine Sprache für die Beschreibung, geben die Beschreibung für den Unterbereich ein und wählen **Hinzufügen**. Sie können für beliebig viele Sprachen Beschreibungen für Ihre Organisation erstellen, bearbeiten oder löschen. Sie können jedoch nur eine Beschreibung pro Sprache nutzen.  
  
    - **SKUs**: Wählen Sie die Versionen von Dynamics 365 aus, die diesen Teilbereich anzeigen.  
  
    - **Client**: Wählen Sie den Typ des Clients aus, für den dieser Unterbereich angezeigt wird.  
  
    - **Outlook-Verknüpfung**: Wählen Sie das in Dynamics 365 for Outlook anzuzeigende Symbol aus.  
  
    - **Offlineverfügbarkeit**: Aktivieren Sie das Kontrollkästchen, um diesen Unterbereich für Benutzer zur Verfügung zu stellen, wenn diese in Dynamics 365 for Outlook offline sind.  
  
## <a name="organize-areas-groups-and-subareas"></a>Organisieren von Bereichen, Gruppen und Unterbereichen  
 Sie können die Bereiche, Gruppen und Unterbereiche durch Ziehen an neue Positionen organisieren. Ein Containerfeld wird dort angezeigt, wo Sie die Kachel ablegen können. Diese Aktionen können Sie ausführen:  
  
-   Verschieben Sie einen Unterbereich auf eine neue Position in derselben Gruppe oder in einer Gruppe unter demselben Bereich.  
  
-   Verschieben Sie einen Unterbereich auf eine neue Position in derselben unter einem anderen Bereich.  
  
-   Verschieben einer Gruppe auf eine neue Position im selben Bereich.  
  
-   Verschieben einer Gruppe auf eine neue Position in einem anderen Bereich.  
  
-   Verschieben Sie einen Bereich auf eine neue Position.  
  
## <a name="clone-a-component-in-a-site-map"></a>Klonen einer Komponente in einer Siteübersicht  
 Um eine Kopie einer vorhandenen Komponente zu erstellen, wählen Sie die Komponente und dann auf der Aktionssymbolleiste **Klonen**.  Alle Details der geklonten Komponente sind mit denen der Basiskomponente identisch (bis auf ID und Titel). Die ID wird zufällig generiert. 
  
 Wenn Sie einen Bereich klonen, wird der geklonte Bereich rechts neben der gerade ausgewählten Bereich hinzugefügt. Wenn Sie eine Gruppe klonen, wird die geklonte Gruppe rechts neben der gerade ausgewählten Gruppe hinzugefügt. Wenn Sie einen Unterbereich klonen, wird der geklonte Unterbereich rechts neben der gerade ausgewählten Unterbereich hinzugefügt.  
  
## <a name="delete-an-area-group-or-subarea-from-a-site-map"></a>Löschen eines Bereichs, einer Gruppe oder eines Unterbereich aus einer Siteübersicht  
 Um eine Siteübersichtskomponente zu löschen, wählen Sie die Komponentenkachel und dann auf der Aktionsleiste **Löschen**. Wenn Sie einen Bereich löschen, werden alle Gruppen und Unterbereiche im Bereich ebenfalls gelöscht. Auch wenn Sie eine Gruppe löschen, werden die Gruppe und die Unterbereiche gelöscht.  
  
## <a name="clients-supported"></a>Unterstützte Clients  
 In der folgenden Tabelle wird veranschaulicht, welche Clients für die verschiedenen Siteübersichten unterstützt werden.  
 
|Siteübersichten|Unterstützte Clients|  
|---------------|-----------------------|  
|Neue Apps| Einheitliche Oberfläche |  
|Siteübersicht für benutzerdefinierte Dynamics 365-Apps | Legacy Web-Applikation und Dynamics 365 for Outlook. |  
|Modelgesteuerte Anwendungen (Sales, Vertriebs-Hub, Customer Service, Kundenservice-Hub, Field Service, Project Service Automation)| Legacy Web-App und die einheitliche Benutzeroberfläche|  
 
  
### <a name="next-steps"></a>Nächste Schritte  
 [Erstellen oder Bearbeiten einer App](create-edit-app.md)   
 [App-Komponenten hinzufügen oder bearbeiten](add-edit-app-components.md)
