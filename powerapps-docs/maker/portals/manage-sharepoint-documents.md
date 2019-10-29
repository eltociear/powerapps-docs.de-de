---
title: Verwalten von SharePoint-Dokumenten in einem Portal | MicrosoftDocs
description: Anweisungen zum Verwalten von SharePoint-Dokumenten in einem Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: ab51a2b1a309921e32949a806adb4a7bf3273ccf
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72974688"
---
# <a name="manage-sharepoint-documents"></a>Verwalten von SharePoint-Dokumenten

Common Data Service unterstützt die Integration in [!INCLUDE[pn-microsoft-sharepoint-online](../../includes/pn-microsoft-sharepoint-online.md)], mit der Sie die Dokument Verwaltungsfunktionen von [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] von Common Data Service aus verwenden können. Powerapps-Portale unterstützen jetzt das Hochladen und Anzeigen von Dokumenten in und aus [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] direkt in einem Entitäts Formular oder Webformular in einem Portal. Dadurch können Portalbenutzer Dokumente in einem Portal anzeigen, herunterladen, hinzufügen und löschen. Benutzer des Portals können auch Unterordner erstellen, um Ihre Dokumente zu organisieren.

> [!NOTE]
> - Die Dokument Verwaltung funktioniert nur mit [!INCLUDE[pn-microsoft-sharepoint-online](../../includes/pn-microsoft-sharepoint-online.md)].
> - Die Dokument Verwaltung wird bei der serverbasierten Integration unterstützt.

Zum Arbeiten mit den Dokument Verwaltungsfunktionen von [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] in Common Data Service müssen Sie folgende Schritte ausführen:

1.  [Aktivieren der Funktionalität der Dokument Verwaltung in Modell gesteuerten apps in Dynamics 365](#step-1-enable-document-management-functionality-in-model-driven-apps-in-dynamics-365)

2.  [Einrichten der SharePoint-Integration über das powerapps-Portal Admin Center](#step-2-set-up-sharepoint-integration-from-powerapps-portals-admin-center)

3.  [Aktivieren der Dokument Verwaltung für Entitäten](#step-3-enable-document-management-for-entities)

4.  [Konfigurieren des entsprechenden Formulars in powerapps-Dokumenten](#step-4-configure-the-appropriate-form-to-display-documents)

5.  [Erstellen Sie eine entsprechende Entitäts Berechtigung, und weisen Sie Sie der entsprechenden webrolle zu](#step-5-create-appropriate-entity-permission-and-assign-it-to-the-appropriate-web-role)

## <a name="step-1-enable-document-management-functionality-in-model-driven-apps-in-dynamics-365"></a>Schritt 1: Aktivieren der Funktionalität der Dokument Verwaltung in Modell gesteuerten apps in Dynamics 365

Sie müssen die Funktionalität der Dokument Verwaltung in Modell gesteuerten apps in Dynamics 365 mithilfe der serverbasierten [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] Integration aktivieren. Bei der serverbasierten [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] Integration können Modell gesteuerte apps in Dynamics 365 und [!INCLUDE[pn-microsoft-sharepoint-online](../../includes/pn-microsoft-sharepoint-online.md)] eine Server-zu-Server-Verbindung ausführen. Der Standard [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] Site-Datensatz wird vom Portal verwendet. Informationen zum Aktivieren der Dokument Verwaltungs Funktionalität in Modell gesteuerten apps in Dynamics 365 finden Sie [unter Einrichten von Modell gesteuerten apps in Dynamics 365 für die Verwendung von SharePoint Online](https://docs.microsoft.com/en-us/power-platform/admin/set-up-dynamics-365-online-to-use-sharepoint-online).

## <a name="step-2-set-up-sharepoint-integration-from-powerapps-portals-admin-center"></a>Schritt 2: Einrichten der SharePoint-Integration über das powerapps-Portal Admin Center

Um die Dokument Verwaltungsfunktionen von [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]verwenden zu können, müssen Sie [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] Integration über das powerapps-Portal Admin Center aktivieren.

> [!NOTE]
> Sie müssen ein globaler Administrator sein, um diese Aktion ausführen zu können.

1. Öffnen Sie das [powerapps-Portal Admin Center](admin/admin-overview.md).

2.  Wechseln Sie zu **Einrichten [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] Integration** , >  **[!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] Integration aktivieren**.

    > [!div class=mx-imgBorder]
    > ![Aktivieren der SharePoint-Integration](media/enable-sharepoint-integration.png "Aktivieren der SharePoint-Integration")

3.  Wählen Sie im Bestätigungsfenster die Option **aktivieren** aus. Dadurch wird die Kommunikation des Portals mit [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]ermöglicht. Während die [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] Integration aktiviert ist, wird das Portal neu gestartet und ist für einige Minuten nicht verfügbar. Wenn [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] Integration aktiviert ist, wird eine Meldung angezeigt.

Wenn [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] Integration aktiviert ist, wird die folgende Aktion verfügbar:

- **Deaktivieren Sie [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] Integration**: mit können Sie die [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] Integration in Ihr Portal deaktivieren. Während die [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] Integration deaktiviert wird, wird das Portal neu gestartet und ist für einige Minuten nicht verfügbar. Wenn [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] Integration deaktiviert ist, wird eine Meldung angezeigt.

    > [!div class=mx-imgBorder]
    > ![Deaktivieren der SharePoint-Integration](media/disable-sharepoint-integration.png "Deaktivieren der SharePoint-Integration")

Durch das Aktivieren oder Deaktivieren der [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] Integration wird die [!INCLUDE[pn-azure-active-directory](../../includes/pn-azure-active-directory.md)]-Anwendung ([!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] AD) für das Portal aktualisiert, und die erforderlichen [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] Berechtigungen werden hinzugefügt bzw. entfernt. Sie werden auch umgeleitet, um Ihre Zustimmung zu den Änderungen in der [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] AD-Anwendung bereitzustellen. 

> [!div class=mx-imgBorder]
> ![Deaktivieren der SharePoint-Integration](media/sharepoint-integration-consent.png "Deaktivieren der SharePoint-Integration")

Wenn Sie Ihre Zustimmung nicht angeben:

- Das Aktivieren oder Deaktivieren der [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] Integration ist nicht fertiggestellt, und es wird eine Fehlermeldung angezeigt.

- Die Standard-[!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] AD-Anmeldung im Portal funktioniert nicht. 


## <a name="step-3-enable-document-management-for-entities"></a>Schritt 3: Aktivieren der Dokument Verwaltung für Entitäten
Sie müssen die Dokument Verwaltung für Entitäten aktivieren, um Dokumente zu speichern, die auf Entitäts Datensätze in [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] Informationen zum Aktivieren der Dokument Verwaltung für Entitäten finden Sie unter [Aktivieren der SharePoint-Dokument Verwaltung für bestimmte Entitäten](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/admin/enable-sharepoint-document-management-specific-entities).

## <a name="step-4-configure-the-appropriate-form-to-display-documents"></a>Schritt 4: Konfigurieren des entsprechenden Formulars zum Anzeigen von Dokumenten

### <a name="powerapps-customization"></a>Powerapps-Anpassung

Identifizieren Sie das Formular, in dem Sie die Dokument Verwaltungsfunktionen verwenden möchten. Sie müssen das Formular mit dem Modell gesteuerten App-Formular-Editor bearbeiten und diesem ein unter Raster hinzufügen. Das subraster fügt dem Formular einen Abschnitt hinzu, mit dem Sie Dokumente innerhalb eines Portals bearbeiten können. Sie müssen die folgenden Eigenschaften im subraster festlegen, damit dieses Feature funktioniert:

- Wählen Sie unter **Datenquelle**die Option **Dokument Speicherorte** aus der Liste **Entität** aus.

- Wählen Sie unter **Datenquelle**die Option **aktive Dokument Speicherorte** aus der **Standard Ansichts** Liste aus.

Sie können den Namen und die Bezeichnung gemäß Ihrer Anforderung angeben. Speichern und veröffentlichen Sie das Formular, sobald das unter Raster hinzugefügt und konfiguriert wurde.

> [!NOTE]
> Die Dokument Verwaltung muss für die Entität aktiviert werden, für die Sie das Formular bearbeiten. Weitere Informationen: [Aktivieren der Dokument Verwaltung für Entitäten](#step-3-enable-document-management-for-entities)

### <a name="powerapps-portals-configuration"></a>Konfiguration der powerapps-Portale

Abgesehen von der Standardkonfiguration, die für das Entitäts Formular oder Web Form erforderlich ist, müssen Sie die folgenden Eigenschaften festlegen, um die Dokument Verwaltung zu aktivieren:

- **Entitäts Name** und **Formular Name**: Geben Sie die Namen der Entität und des Formulars ein, die Sie im vorherigen Schritt angepasst haben.

- Aktivieren Sie das Kontrollkästchen **Entitäts Berechtigung aktivieren** im Formular, damit ein Benutzer die Dokumente lesen kann.

- Legen Sie den **Modus** auf **Bearbeiten** fest, um das Hochladen von Dokumenten zuzulassen.

> [!NOTE]
> Zum Hochladen von Dokumenten muss der übergeordnete Entitäts Daten Satz vorhanden sein. Wenn Sie den Modus auf Einfügen festlegen, funktioniert das Hochladen des Dokuments nicht, da der übergeordnete Entitäts Daten Satz erst erstellt wird, wenn das Formular übermittelt wird.

## <a name="step-5-create-appropriate-entity-permission-and-assign-it-to-the-appropriate-web-role"></a>Schritt 5: Erstellen Sie die entsprechende Entitäts Berechtigung, und weisen Sie Sie der entsprechenden webrolle zu.

Zum Einrichten des erforderlichen Zugriffs zum Anzeigen und Hochladen von Dokumenten sind zwei Entitäts Berechtigungs Einträge erforderlich.

- Berechtigungen für die Entität der Entität oder des Webformulars: 
    - Erstellen Sie einen **Entitäts Berechtigungs** Daten Satz, der den **Entitäts Namen** als Entität des zuvor konfigurierten Entitäts Formulars oder Webformulars angibt. 
    - Wählen Sie eine **Bereich** -und Bereichs Beziehung aus, die für das gewünschte Verhalten des Formulars geeignet ist. 
    - Aktivieren **Sie** die Berechtigungen Lesen und **an Berechtigungen anfügen** , um Lesezugriff auf Dokumente zuzulassen, und aktivieren Sie optional **Schreib** Berechtigungen, um das Hochladen von Dokumenten zuzulassen. Ignorieren Sie den Abschnitt Berechtigungen für untergeordnete **Entitäten** vorerst, da er mit dem nächsten Schritt aufgefüllt wird.
- Berechtigungen für den **Dokument Speicherort** mit übergeordnetem **Bereich** , der auf den vorherigen Berechtigungsdaten Satz verweist: 
    - Erstellen Sie einen **Entitäts Berechtigungs** Daten Satz, und geben Sie den **Entitäts Namen** als **Dokument Speicherort** Entität mit dem **Bereich** **Parent** 
    - Wählen Sie die übergeordnete Entitäts Berechtigung für den im vorherigen Schritt erstellten Entitäts Berechtigungsdaten Satz aus. 
    - Berechtigungen 
        - Die Mindestberechtigungen zum Zulassen von Lesezugriff auf Dokumente **lauten lesen**, erstellen und **Anfügen**. 
        - Einschließen von **Schreib** Berechtigungen für den Zugriff auf den Dokument Upload. 
        - Schließen Sie **Delete** ein, um das Löschen eines Dokuments zuzulassen.

> [!NOTE]
> Eine entsprechende untergeordnete Entitäts Berechtigung für die Entität " **Dokument Speicherort** " muss für jede Instanz des übergeordneten Entitäts Berechtigungsdaten Satzes erstellt werden, der in der Entität der Entität oder des Webformulars vorhanden ist, in der Dokumente angezeigt werden müssen.

## <a name="configure-file-upload-size"></a>Dateiuploadgröße konfigurieren

Standardmäßig ist die Dateigröße auf 10 MB festgelegt. Allerdings können Sie die Dateigröße auf maximal 50 MB konfigurieren, indem Sie die Standort Einstellung `SharePoint/MaxUploadSize`verwenden.

## <a name="sample-configuration-to-enable-document-management-on-the-case-entity-form"></a>Beispielkonfiguration zum Aktivieren der Dokument Verwaltung für das Formular "Case-Entität"

Das folgende Beispiel veranschaulicht die Konfiguration mithilfe der Case-Entität, die die Dynamics 365-Kundendienst Anwendung als erforderliche Komponente benötigt. Obwohl in diesem Beispiel die Case-Entität verwendet wird, handelt es sich lediglich um eine Abbildung der oben genannten Schritte, und Sie können mit jeder anderen benutzerdefinierten Entität oder einer beliebigen Common Data Service Entität, die die Verwaltung von Dokumenten in SharePoint unterstützt 

1.  Befolgen Sie die Anweisungen in [Schritt 1](#step-1-enable-document-management-functionality-in-model-driven-apps-in-dynamics-365) , um sicherzustellen, dass die serverbasierte Konfiguration für Modell gesteuerte apps in Dynamics 365 und [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] Integration beendet ist.

2.  Befolgen Sie die Anweisungen in [Schritt 2](#step-2-set-up-sharepoint-integration-from-powerapps-portals-admin-center) , um sicherzustellen, dass das Portal über Berechtigungen zum Integrieren in [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]verfügt. 

3.  Befolgen Sie die Anweisungen in [Schritt 3](#step-3-enable-document-management-for-entities) , um sicherzustellen, dass die Dokument Verwaltung für die Fall Entität aktiviert ist.

4.  Befolgen Sie die Anweisungen in [Schritt 4](#step-4-configure-the-appropriate-form-to-display-documents) mit den folgenden Konfigurationen:

    - Modell gesteuerte apps in Dynamics 365-Anpassung

        a. Wechseln Sie zu **Einstellungen** > **Anpassung** > **passen Sie das System**an. 

        b. Wechseln Sie in der **Standardlösung**zu der **Case** -Entität > **Forms**. 
    
        c. Öffnen Sie den **Web –-Bearbeitungs Fall** im Formular-Editor.

         > [!div class=mx-imgBorder]
         > ![Webbearbeitungs Fall]Formular(media/web-edit-case-form.png "Web-Bearbeitungs Fall Formular")
    
        d. Wählen Sie das Feld **erstellt für** im Formular aus, und wählen Sie auf der Registerkarte **Einfügen** die Option **unter Raster**aus.

         > [!div class=mx-imgBorder]
         > ![Hinzufügen eines untergeordneten Rasters zum Web-Edit-Fall-Formular](media/add-sub-grid.png "Hinzufügen eines untergeordneten Rasters zum Web-Bearbeitungs Fall Formular")
    
        e. Legen Sie im Dialogfeld **Eigenschaften festlegen** die folgenden Eigenschaften fest, und wählen Sie **OK**aus:

         - **Name** (Dies kann ein beliebiger Name sein): casedocuments 
    
         - **Bezeichnung** (Dies kann ein beliebiger Bezeichnungs Name sein): Fall Dokumente 
      
         - **Entität**: Dokument Speicherorte 
    
         - **Standardansicht**: aktive Dokument Speicherorte

         > [!div class=mx-imgBorder]
         > Subgrid- ![Eigenschaften]((media/sub-grid-properties.png "Subgrid") -Eigenschaften)

        c. Wählen Sie im Formular-Editor die Option **Speichern** aus, und wählen Sie dann **veröffentlichen**aus.

    - Konfiguration der powerapps-Portale

        a. Wechseln Sie zu **Portale** > **Entitäts Formularen**.
    
        b. Suchen und öffnen Sie das Formular **Customer Service-Edit Case-** Entität.
    
        c. Überprüfen Sie, ob die folgenden Eigenschaften festgelegt sind:
    
         - **Entitäts Name**: Fall (Incident)
    
         - **Formular Name**: Web – Bearbeitungs Fall
    
         - **Modus**: Bearbeiten
    
         - **Entitäts Berechtigung**: aktiviert
    
         > [!div class=mx-imgBorder]
         > ![Kundendienst-Bearbeitungs Fall Formular](media/customer-service-edit-case-form.png "Kundendienst-Bearbeitungs Fall Formular")
    
        d. Wenn Sie Änderungen am Formular vorgenommen haben, wählen Sie **Speichern**aus.

5. Befolgen Sie [Schritt 5](#step-5-create-appropriate-entity-permission-and-assign-it-to-the-appropriate-web-role
) , um sicherzustellen, dass den Benutzern Entitäts Berechtigungen gewährt werden.

   1. Wechseln Sie zum **Webrollen** -Datensatz, der dem Benutzer zugeordnet ist. In diesem Beispiel gehen wir davon aus, dass der Benutzer über eine Administrator-webrolle verfügt.

   2. Stellen Sie sicher, dass ein Entitäts Berechtigungsdaten Satz mit dem Namen der **Kundendienst Fälle vorhanden ist, bei denen Contact der Kunde ist** 

      > [!NOTE]
      > Stellen Sie sicher, dass für Ihre webrolle diese Berechtigungen hinzugefügt wurde. Wenn Ihr Benutzer bereits Administrator ist, muss die oben genannte Entitäts Berechtigung nicht explizit zugewiesen werden.

   3. Erstellen Sie eine neue Entitäts Berechtigung, geben Sie die folgenden Details ein, und wählen Sie **Speichern**aus:

    - **Name** (Dies kann ein beliebiger Name sein): Kundendienst bezogene Dokumente

    - **Entitäts Name**: Dokument Speicherort
        
    - **Bereich**: übergeordnetes Element
        
    - Berechtigung für die über **geordnete Entität**: Kundendienst Fälle, in denen Contact der Kunde ist
        
    - Über **geordnete Beziehung**: incident_SharePointDocumentLocations
        
    - **Berechtigungen**: lesen, erstellen, anfügen, schreiben, löschen

      > [!div class=mx-imgBorder]
      > Customer Service-Entitäts ![Berechtigung](media/customer-service-entity-permission.png "Customer Service-Entitäts Berechtigung")
  
   4. Melden Sie sich beim Portal an, um sicherzustellen, dass die Dokument Verwaltung für die Fall Entität aktiviert ist

      a. Wechseln Sie zur Seite **Support** .

      > [!div class=mx-imgBorder]
      > ![Portal Support]Seite(media/portal-support-page.png "Portal Supportseite")

      b. Klicken Sie in der Liste auf einen vorhandenen Fall Daten Satz. Wechseln Sie auf der Seite zum Abschnitt **Fall Dokumente** , und sehen Sie sich die hinzugefügte Dokument Liste an.

      > [!div class=mx-imgBorder]
      > (media/case-document.png "Fall Dokument") für ![Fall Dokument]

