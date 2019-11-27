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
ms.openlocfilehash: f94dee983d5d2d9cedf417f2843a2c10c46b82c1
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2756990"
---
# <a name="manage-sharepoint-documents"></a>Verwalten von SharePoint-Dokumenten

Common Data Service unterstützt die Integration mit [!INCLUDE[pn-microsoft-sharepoint-online](../../includes/pn-microsoft-sharepoint-online.md)], die es Ihnen ermöglicht, die Dokumentverwaltungsfunktionen von [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] in Common Data Service zu verwenden. PowerApps-Portale unterstützen jetzt das direkte Hoch- und Herunterladen von Dokumenten von und nach [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] mit einem Entitätsformular oder einem Webformular in einem Portal. Dadurch können Portalbenutzer Dokumente aus einem Portal anzeigen, herunterladen, hinzufügen und löschen. Portalbenutzer können auch Unterordner erstellen, um die Dokumente zu organisieren.

> [!NOTE]
> - Die Dokumentenverwaltung funktioniert nur mit [!INCLUDE[pn-microsoft-sharepoint-online](../../includes/pn-microsoft-sharepoint-online.md)].
> - Dokumentenverwaltung wird mit Server-basierter Integration unterstützt.

Um mit den Dokumentenverwaltungsfunktionen von [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] in Common Data Service arbeiten zu können, müssen Sie:

1.  [Aktivieren der Dokumentenverwaltung in modellgesteuerten Apps in Dynamics 365](#step-1-enable-document-management-functionality-in-model-driven-apps-in-dynamics-365)

2.  [Die SharePoint-Integration über das PowerApps-Portaladministratorcenter einrichten](#step-2-set-up-sharepoint-integration-from-powerapps-portals-admin-center)

3.  [Aktivieren der Dokumentenverwaltung für Entitäten](#step-3-enable-document-management-for-entities)

4.  [Das entsprechende Formular in PowerApps-Dokumenten konfigurieren](#step-4-configure-the-appropriate-form-to-display-documents)

5.  [Die entsprechende Entitätsberechtigung erstellen und der entsprechenden Webrolle zuweisen](#step-5-create-appropriate-entity-permission-and-assign-it-to-the-appropriate-web-role)

## <a name="step-1-enable-document-management-functionality-in-model-driven-apps-in-dynamics-365"></a>Schritt 1: Aktivieren der Dokumentenverwaltung in modellgesteuerten Apps in Dynamics 365

Sie müssen die Dokumentenverwaltung in modellgesteuerten Apps in Dynamics 365 mit Hilfe der serverbasierten [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]-Integration aktivieren. Mit der serverbasierten [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]-Integration können modellgesteuerte Apps in Dynamics 365 und [!INCLUDE[pn-microsoft-sharepoint-online](../../includes/pn-microsoft-sharepoint-online.md)] eine Server-zu-Server-Verbindung ausführen. Der Standardwebsitedatensatz [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] wird über das Portal verwendet. Informationen dazu, wie Sie die Dokumentenverwaltungsfunktionen in modellgesteuerten Apps in Dynamics 365 aktivieren können, finden Sie unter [Modellgesteuerte Apps in Dynamics 365 einrichten, um SharePoint Online zu verwenden](https://docs.microsoft.com/power-platform/admin/set-up-dynamics-365-online-to-use-sharepoint-online).

## <a name="step-2-set-up-sharepoint-integration-from-powerapps-portals-admin-center"></a>Schritt 2: Die SharePoint-Integration über das PowerApps-Portal-Administratorcenter einrichten

Um die Dokumentenverwaltungsfunktionen von [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] verwenden zu können, müssen Sie die [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]-Integration über das PowerApps-Portaladministratorcenter aktivieren.

> [!NOTE]
> Diese Aktion kann nur von einem globalen Administrator ausgeführt werden.

1. Öffnen Sie das [Admin Center für PowerApps-Portale](admin/admin-overview.md).

2.  Wechseln Sie zu **Einrichten der [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] Integration** > **Aktivieren der [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] Integration**.

    > [!div class=mx-imgBorder]
    > ![SharePoint-Integration aktivieren](media/enable-sharepoint-integration.png "Aktivieren der SharePoint-Integration")

3.  Klicken Sie im Bestätigungsfenster auf **Aktivieren**. Das ermöglicht dem Portals die Kommunikation mit [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]. Während die [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]-Integration aktiviert ist, startet das Portal neu und ist für einige Minuten nicht verfügbar. Eine Meldung wird angezeigt, wenn die  [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]-Integration aktiviert ist.

Wenn die [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]-Integration aktiviert ist, ist folgende Aktion verfügbar.

- **[!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]-Integration deaktivieren**: Ermöglicht, das Sie die Integration [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]-Integration mit dem Portal deaktivieren. Während die [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]-Integration deaktiviert ist, startet das Portal neu und ist für einige Minuten nicht verfügbar. Eine Meldung wird angezeigt, wenn die [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]-Integration deaktiviert ist.

    > [!div class=mx-imgBorder]
    > ![SharePoint-Integration deaktivieren](media/disable-sharepoint-integration.png "Deaktivieren der SharePoint-Integration")

Das Aktivieren oder Deaktivieren der [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]-Integration aktualisiert die [!INCLUDE[pn-azure-active-directory](../../includes/pn-azure-active-directory.md)] ([!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] AD)-Anwendung für das Portal und fügt oder entzieht die erforderlichen [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]-Berechtigungen. Sie werden zudem umgeleitet, um Ihre Zustimmung zu den Änderungen zu geben, die in der [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)]-Anwendung vorgenommen werden können. 

> [!div class=mx-imgBorder]
> ![SharePoint-Integration deaktivieren](media/sharepoint-integration-consent.png "Deaktivieren der SharePoint-Integration")

Wenn Sie nicht zustimmen:

- Das Aktivieren oder Deaktivieren der [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]-Integration wird nicht abgeschlossen und eine Fehlermeldung wird angezeigt.

- Die Standard-[!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] AD-Anmeldung auf dem Portal funktioniert nicht. 


## <a name="step-3-enable-document-management-for-entities"></a>Schritt 3. Aktivieren der Dokumentenverwaltung für Entitäten
Sie müssen die Dokumentenverwaltung für Entitäten aktivieren, um Dokumente mit Bezug auf Entitätsdatensätze in [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] zu speichern. Informationen dazu, wie Sie die Dokumentenverwaltung für Entitäten aktivieren finden Sie unter [Aktivieren der SharePoint-Dokumentenverwaltung für bestimmte Entitäten.](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-sharepoint-document-management-specific-entities)

## <a name="step-4-configure-the-appropriate-form-to-display-documents"></a>Schritt 4: Das entsprechenden Formular konfigurieren, um Dokumente anzuzeigen

### <a name="powerapps-customization"></a>PowerApps-Anpassung

Ermitteln Sie das Formular, in dem Dokumentenverwaltungsfunktionen verwendet werden sollen. Sie müssen das Formular mit dem Formulareditor in der modellgesteuerten App bearbeiten und ein Unterraster hinzufügen. Das Unterraster fügt einen Abschnitt zum Formular hinzu, sodass Sie mit Dokumenten im Portal arbeiten können. Sie müssen die folgenden Eigenschaften im Unterraster für diese Funktionalität festlegen:

- Wählen Sie unter **Datenquelle** **Dokumentspeicherorte** in der Liste **Entität** aus.

- Wählen Sie unter **Datenquelle** **Aktives Dokument - Orte** in der Liste **Standardansicht** aus.

Sie können Namen und Beschriftung je nach Anforderung angeben. Speichern und veröffentlichen Sie das Formular, sobald das Unterraster hinzugefügt und konfiguriert ist.

> [!NOTE]
> Die Dokumentenverwaltung muss für die Entität aktiviert werden, für die Sie das Formular bearbeiten. Weitere Informationen: [Aktivieren der Dokumentenverwaltung für Entitäten](#step-3-enable-document-management-for-entities)

### <a name="powerapps-portals-configuration"></a>PowerApps-Portalkonfiguration

Abgesehen von der Standardkonfiguration, die für das Entitäts- oder Webformular erforderlich ist, müssen Sie die folgenden Eigenschaften festlegen, um Dokumentenverwaltung zu aktivieren:

- **Entitätsname** und **Formularname**: Geben Sie jeweils die Entitäts- und Formularnamen ein, die Sie im vorherigen Schritt angepasst haben.

- Aktivieren Sie das Kontrollkästchen **Entitätsberechtigungen aktivieren** im Formular, um einen Benutzer zu ermöglichen, die Dokumente zu lesen.

- Legen Sie **Modus** auf **Bearbeiten** fest, um Dokumentenuploads zu erlauben.

> [!NOTE]
> Das Hochladen von Dokumenten erfordert, dass die übergeordnete Datenentität vorhanden ist. Wenn Sie den Modus auf einfügen festlegen, wird das Hochladne des Dokuments nicht möglic sein, weil die übergeordnete Datenentität nicht erstellt wird, bis das Formular übermittelt wird.

## <a name="step-5-create-appropriate-entity-permission-and-assign-it-to-the-appropriate-web-role"></a>Schritt 5: Die entsprechende Entitätsberechtigung erstellen und der entsprechenden Webrolle zuweisen

Zwei Entitätsberechtigungsdatensätze sind erforderlich, um den notwendigen Zugriff zum Anzeigen und Hochladen von Dokumenten einzurichten.

- Berechtigungen für die Entität auf dem Entität- oder Webformular: 
    - Erstellen Sie einen **Entitätsberechtigungs**-Datensatz, der den **Entitätsname** als Entität des Entitäts- oder Webformulars angibt, das zuvor konfiguriert wurde. 
    - Wählen Sie einen **Umfang** und eine Umfangsbeziehung aus, der bzw. die dem gewünschten Verhalten des Formulars entspricht. 
    - Aktivieren Sie **Lesen**- und **Anfügen an**-Rechte, um einen Lesezugriff auf Dokumente zu ermöglichen. Aktivieren Sie optional **Schreib**-rechte, um Dokumentuploads zu erlauben. Ignorieren Sie den Abschnitt **Untergeordnete Entitätsberechtigungen** erstmal, da dieser im nächsten Schritt gefüllt wird.
- Berechtigungen auf **Dokumentspeicherort** mit **Übergeordneter Umfang**, der sich auf den vorherigen Berechtigungsdatensatz bezieht: 
    - Erstellen Sie einen Datensatz **Entitätsberechtigung**, der den **Entitätsnamen** als **Dokumentspeicherort**-Entität mit **Umfang** gesetzt auf **Übergeordnet** angibt. 
    - Wählen Sie die übergeordnete Entitätsberechtigung für den Entitätsberechtigungsdatensatz aus, der im vorherigen Schritt erstellt wurde. 
    - Rechte 
        - Die minimalen Berechtigungen, um einen Lesezugriff auf Dokumente zu gewähren, sind **Lesen**, **Erstellen** und **Anfügen**. 
        - Schließen Sie **Schreiben**-Berechtigungen für den Dokumentuploadzugriff ein. 
        - Schließen Sie **Löschen** ein, um das Löschen eines Dokuments erlauben.

> [!NOTE]
> Eine entsprechende untergeordnete Entitätsberechtigung auf der **Dokumentspeicherort**-Berechtigung muss für jede Instanz des übergeordneten Entitätsberechtigungsdatensatzes erstellt werden, der auf dem Entität des Entitäts- oder Webformulars vorhanden ist, auf dem Dokumente angezeigt werden.

## <a name="configure-file-upload-size"></a>Konfigurieren der Dateigröße für den Upload

Standardmäßig ist die Dateigröße auf 10 MB festgelegt. Sie können jedoch die Dateigröße auf bis zu 50 MB erhöhen, indem Sie die Standortseinstellung `SharePoint/MaxUploadSize` verwenden.

## <a name="sample-configuration-to-enable-document-management-on-the-case-entity-form"></a>Beispielkonfiguration, um die Dokumentenverwaltung im Anfrageentitätsformular zu aktivieren

Das Beispiel unten veranschaulicht die Konfiguration mit Hilfe der Anfrage-Entität, für die die Dynamics 365 Customer Service-Anwendung als Voraussetzung erforderlich ist. Auch wenn dieses Beispiel die Anfrage-Entität verwendet, ist es lediglich eine Abbildung der Schritte, die oben beschrieben werden, und es kann mit einer anderen benutzerdefinierten Entität oder Common Data Service-Entität, die die Dokumentenverwaltung in SharePoint unterstützt, verwendet werden. 

1.  Folgen Sie den Anweisungen in [Schritt 1](#step-1-enable-document-management-functionality-in-model-driven-apps-in-dynamics-365), um sicherzustellen, dass die serverbasierte Konfiguration für die modellgesteuerten Apps in Dynamics 365 und [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]-Integration abgeschlossen ist.

2.  Folgen Sie den Anweisungen in [Schritt 2](#step-2-set-up-sharepoint-integration-from-powerapps-portals-admin-center), um sicherzustellen, dass das Portal die Berechtigungen für die Integration mit [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] hat. 

3.  Folgen Sie den Anweisungen in [Schritt 3](#step-3-enable-document-management-for-entities), um sicherzustellen, dass die Dokumentenverwaltung für die Anfrageentität aktiviert ist.

4.  Befolgen Sie die Anweisungen in [Schritt 4](#step-4-configure-the-appropriate-form-to-display-documents) mit folgenden Konfigurationen:

    - Anpassung der modellgesteuerten Apps in Dynamics 365

        a. Gehen Sie zu **Einstellungen** > **Anpassung** > **System anpassen**. 

        b. In **Standardlösung** wechseln Sie zu **Anfrage**-Entität >**Formulare**. 
    
        c. Öffnen Sie **Web – Bearbeitungsanfrage** im Formular-Editor.

         > [!div class=mx-imgBorder]
         > ![Web – Bearbeitungsanfrageformular](media/web-edit-case-form.png "Web – Bearbeitungsanfrageformular")
    
        d. Wählen Sie das Feld **Erstellungszeitpunkt** im Formular und auf der Registerkarte **Einfügen** die Option **Unterraster** aus.

         > [!div class=mx-imgBorder]
         > ![Hinzufügen eines Unterrasters zum Web – Bearbeitungsanfrageformular](media/add-sub-grid.png "Hinzufügen eines Unterrasters zum Web – Bearbeitungsanfrageformular")
    
        e. Im Dialogfeld **Eigenschaften festlegen** legen Sie die folgenden Eigenschaften fest und wählen **OK** aus:

         - **Name** (beliebiger Name möglich): CaseDocuments 
    
         - **Beschriftung** (beliebige Beschriftung möglich): Anfragedokumente 
      
         - **Entität**: Dokumentspeicherorte 
    
         - **Standardansicht**: Aktives Dokument - Orte

         > [!div class=mx-imgBorder]
         > ![Unterrastereigenschaften](media/sub-grid-properties.png "Unterrastereigenschaften")

        f. Wählen Sie im Formular-Editor **Speichern** und **Veröffentlichen** aus.

    - PowerApps-Portalkonfiguration

        a. Gehen Sie zu **Portale** > **Entitätsformulare**.
    
        b. Suchen und öffnen Sie das **Kundenservice – Anfrage bearbeiten**-Entitätsformular.
    
        c. Prüfen Sie und stellen Sie sicher, dass die folgenden Eigenschaften festgelegt sind:
    
         - **Entitätsname**: Anfrage (Vorfall)
    
         - **Formularname**: Web – Bearbeitungsanfrage
    
         - **Modus**: Bearbeiten
    
         - **Entitätsberechtigung**: Aktiviert
    
         > [!div class=mx-imgBorder]
         > ![Customer Service – Bearbeitungsanfrageformular](media/customer-service-edit-case-form.png "Customer Service – Bearbeitungsanfrageformular")
    
        d. Falls Änderungen am Formular vorgenommen wurden, wählen Sie **Speichern** aus.

5. Führen Sie [Schritt 5](#step-5-create-appropriate-entity-permission-and-assign-it-to-the-appropriate-web-role
) aus, um sicherzustellen, dass Entitätsberechtigungen Benutzern erteilt wurden.

   1. Navigieren Sie zum **Webrolle**-Datensatz, der dem Benutzer zugeordnet ist. In diesem Beispiel gehen wir davon aus, das der Benutzer eine Administratorwebrolle hat.

   2. Stellen Sie sicher, dass ein Entitätsberechtigungsdatensatz mit dem Namen **Kundenservice – Anfragen, bei denen der Kontakt ein Kunde ist** vorhanden ist. 

      > [!NOTE]
      > Stellen Sie sicher, dass Ihrer Webrolle die Entitätsberechtigung hinzugefügt wurde. Wenn die Benutzer bereits ein Administrator ist, muss die oben angegebene Entitätsberechtigung nicht explizit zugewiesen werden.

   3. Erstellen Sie eine neue Entitätsberechtigung, geben Sie die folgenden Details ein, und wählen Sie **Speichern** aus:

    - **Name** (Jeder beliebige): Kundenservice – verwandte Dokumente

    - **Entitätsname**: Dokumentspeicherort
        
    - **Umfang**: Übergeordnet
        
    - **Übergeordnete Entitätsberechtigung**: Kundenservice – Anfragen, bei denen das Konto des Kontakts ein Kundenkonto ist
        
    - **Übergeordnete Beziehung**: incident_SharePointDocumentLocations
        
    - **Rechte**: Lesen, Erstellen, Anfügen, Schreiben, Löschen

      > [!div class=mx-imgBorder]
      > ![Customer Service – Entitätsberechtigung](media/customer-service-entity-permission.png "Customer Service – Entitätsberechtigung")
  
   4. Melden Sie im Portal an, um sicherzustellen, dass die Dokumentenverwaltung für die Anfrageentität aktiviert ist.

      a. Wechseln Sie zur Seite **Support**.

      > [!div class=mx-imgBorder]
      > ![Portalsupportseite](media/portal-support-page.png "Portalsupportseite")

      b. Klicken Sie auf einen vorhandenen Anfragedatensatz in der Liste. Wechseln Sie in den Bereich **Anfragedokumente** auf der Seite und sehen Sie die hinzugefügte Dokumentliste.

      > [!div class=mx-imgBorder]
      > ![Anfragedokument](media/case-document.png "Anfragedokument")

