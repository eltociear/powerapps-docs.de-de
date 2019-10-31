---
title: Anpassen von Dynamics 365 Power BI Inhaltspaketen | MicrosoftDocs
description: 'Erfahren Sie, wie Sie die verfügbaren Power BI-Inhaltspakete für die Verwendung mit Dynamics 365-Daten ändern können.'
keywords: PBI
ms.date: 09/30/2017
ms.service: crm-online
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 for Customer Engagement (online)
ms.assetid: 424d7f29-de44-4ce0-94f1-be8777ad6485
author: Mattp123
ms.author: matp
manager: amyla
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
caps.latest.revision: 16
topic-status: Drafting
tags: null
search.audienceType:
  - customizer
search.app:
  - D365CE
---

# <a name="customize-dynamics-365-apps-power-bi-content-packs"></a>Anpassen von Dynamics 365 Apps Power BI Inhaltspaketen

Power BI ist umfassende Sammlung an Diensten und Tools, die Sie verwenden, um Ihre Geschäftsdaten darzustellen.  Es sind Content-Pakete verfügbar, die es einfach machen, die Daten der Dynamics 365 Sales-, Service- und Marketing-Apps mit Power BI auf Basis eines Standard-Datenmodells zu visualisieren und zu analysieren. Die Inhaltspakete bestehen aus einer Reihe von Entitäten und Feldern, die für die meisten Sales-, Service- und Marketing-Berichtsszenarien nützlich sind.  
  
 Dynamics 365-Apps werden oft um benutzerdefinierte Felder erweitert. Diese benutzerdefinierten Felder werden nicht automatisch im Power BI-Model angezeigt. In diesem Thema werden die verschiedenen Möglichkeiten, zur Bearbeitung oder zum Erweitern der Berichte, die in einem Content Pack enthalten sind, um benutzerdefinierte Felder in Power BI hinzufügen, beschrieben.  
    
<a name="PBI_edit_first"></a>   
## <a name="do-this-before-you-customize-a-content-pack-for-power-bi-reports"></a>Führen Sie dies aus, bevor Sie ein Inhaltspaket für Power BI-Berichte anpassen.  
 
Bevor Sie ein Content Pack anpassen, lesen Sie die hier aufgeführten Informationen und führen jede Aufgabe nach Bedarf aus.  
  
### <a name="meet-the-requirements"></a>Erfüllen der Anforderungen  
  
- [Power BI-Serviceregistrierung](http://powerbi.com/).  
  
- [Power BI Desktop](https://powerbi.microsoft.com/desktop)-Anwendung zu Bearbeitung von Power BI-Berichten  
  
- PBIX-Datei für das Content Pack, das Sie anpassen möchten.  
  
  -   [Laden Sie den Dynamics CRM Online Sales Manager PBIX herunter](http://download.microsoft.com/download/9/2/B/92BCBDCE-CE01-4BC9-A306-2A92653B683E/Sales%20Manager.pbix)  
  
  -   [Laden Sie den Dynamics CRM Online Service Manager PBIX herunter](http://download.microsoft.com/download/9/2/B/92BCBDCE-CE01-4BC9-A306-2A92653B683E/Customer%20Service%20Manager.pbix)  
  
  -   [Laden Sie den Microsoft Dynamics 365 Prozessanalysator PBIX herunter](http://download.microsoft.com/download/9/2/B/92BCBDCE-CE01-4BC9-A306-2A92653B683E/Process%20Analyzer%20-1.34b.pbix)  
  
  Dynamics 365 Content Packs werden derzeit nur in der US-amerikanischen Sprache unterstützt.  
  
### <a name="prepare-a-content-pack-for-customization"></a>Vorbereiten der Anpassung eines Content Packs  
  
> [!IMPORTANT]
>  Um den OData-Feed mit Ihrer Instanz zu verbinden, müssen Sie die hier beschriebenen Schritte ausführen, bevor Sie das Content Pack anpassen.  
> 
> Derzeit ist der Dienst Power BI nicht mit dem OData-Endpunkt von Dynamics 365 Version 9.0 kompatibel. Wenn Sie versuchen, den OData-Endpunkt mit dem Power BI-Service zu verwenden, wird die Fehlermeldung "Das Metadatendokument des Feeds scheint ungültig zu sein" angezeigt. Um diese Inkompatibilität zu umgehen, verwenden Sie den Dynamics 365 Version 8.2 OData-Endpunkt. Weitere Informationen zu den verschiedenen Endpunktversionen finden Sie unter [HTTP-Anfragen erstellen und Fehler behandeln](../../developer/common-data-service/webapi/compose-http-requests-handle-errors.md).
  
1. Starten Sie Power BI Desktop.  
  
    Wählen Sie **Datei** > **Öffnen**, öffnen Sie ein Inhaltspaket, z.B. Sales Manager.bpix, und wählen Sie dann **Öffnen**.  
  
    Einige Seiten der Berichte in Content Packs werden in Power BI Desktopgeladen und angezeigt.  
  
2. Wählen Sie in der Multifunktionsleiste Power BI Desktop **Abfragen bearbeiten**.  
  
3. Wählen Sie im linken Navigationsbereich des Fensters Abfragen bearbeiten unter **Abfragen** die Abfrage **CRMServiceUrl** aus, und wählen Sie dann in der Multifunktionsleiste **Erweiterter Editor**. Ersetzen Sie in der Quelldefinition **base.crm.dynamics.com** durch die URL Ihrer Apps-Instanz. Falls der Organisationsname beispielsweise *Contoso* ist, sieht die URL wie folgt aus:  
  
    Source = "https://*contoso*.crm.dynamics.com/api/data/v8.0/"  
  
4. Wählen Sie **Beenden**, und wählen Sie dann **Schließen und Anwenden** im Query Editor.  
  
5. Wenn das Dialogfeld Zugriff auf einen OData-Feed erscheint, wählen Sie **Organisationskonto** und dann **Anmeldung**.  
  
   ![Zugriff auf einen OData-Feed-Dialog](media/pbi-odata-signin.PNG "Zugriff auf einen OData-Feed-Dialog")  
  
6. Wenn die Anmeldeseite angezeigt wird, geben Sie Ihre Anmeldeinformationen ein, um sich bei Ihrer Instanz zu authentifizieren.  
  
7. Wählen Sie im Dialogfeld Zugriff auf einen Odata-Feed die Option **Verbindung herstellen**.  
  
    Die Content Pack-Abfragen werden aktualisiert. Dies kann einige Minuten in Anspruch nehmen.  
  
<a name="PBI_edit_report"></a>   
## <a name="customize-adynamics-365-content-pack"></a>Anpassen des Dynamics 365 Inhaltspakets  
 [Ändern des Datumsformats, das in einem Bericht angezeigt wird](#PBI_edit_date)  
  
 [Hinzufügen eines benutzerdefinierten Felds zu einem Bericht für eine beliebige Entität, außer für die Firmenentität](#PBI_edit_field)  
  
 [Hinzufügen eines benutzerdefinierten Felds zu einem Bericht für die Firmenentität](#PBI_field_Account)  
  
 [Einem Bericht ein Optionssatzfeld hinzufügen](#PBI_optionset_field)  
  
 [Erhöhen Sie die Anzahl der abgefragten Zeilen](#BPI_increaserows)  
  
<a name="PBI_edit_date"></a>   
### <a name="convert-a-datetime-field-to-a-date-field-for-reporting"></a>Datum/Zeit-Feld in ein Datumsfeld für die Berichterstellung konvertieren  
 In Dynamics 365-Anwendungen werden einige Daten in einem Datum/Uhrzeit/Zeitzonenformat gespeichert, das möglicherweise nicht das bevorzugte Format für die Aggregation von Daten in einem Bericht ist. Sie können die Daten konvertieren, die in Berichten für ein Entitätsfeld angezeigt werden. Beispielsweise kann das Feld "Verkaufschance erstellt am" in ein Datum konvertiert werden, über das die erstellten Verkaufschancen pro Tag anzeigt werden können.  
  
1. Wählen Sie unter Power BI Desktop **Abfragen bearbeiten**.  
  
2. Wählen Sie im linken Navigationsbereich des Abfrage-Editors unter **Abfragen** die Abfrage aus, die das Datumsfeld hat, das Sie ändern möchten, wie z.B. das **Geschätztes Abschlussdatum** in der Entität-Abfrage **Opportunity**.  
  
3. Klicken Sie mit der rechten Maustaste auf die Spaltenüberschrift, z.B. *Voraussichtliches Abschlussdatum*, zeigen Sie auf **Typ ändern** und wählen dann einen anderen Datumstyp, beispielsweise **Datum**, aus.  
  
   ![Datentyp ändern in Power BI Desktop](media/pbi-changeformat.PNG "Datentyp ändern in Power BI Desktop")  
  
4. Wählen Sie **Schließen & Anwenden**, um den Abfrageeditor zu schließen.  
  
5. Wählen Sie auf der Hauptseite Power BI **Änderungen übernehmen**, um die zugehörigen Berichte zu aktualisieren.  
  
<a name="PBI_edit_field"></a>   
### <a name="add-a-custom-field-to-a-report"></a>Hinzufügen eines benutzerdefinierten Felds zu einem Formular  
 Die folgende Vorgehensweise beschreibt, wie Sie ein benutzerdefiniertes Feld, das ein Datum, eine Zeichenkette oder eine Nummer ist, zu einem Bericht für alle verfügbaren Entitäten mit Ausnahme der Kontenentität hinzufügen.  
  
> [!NOTE]
>  Weitere Informationen zum Hinzufügen eines Felds zur Firmenentität finden Sie unter [Hinzufügen eines benutzerdefinierten Felds zu einem Bericht für die Firmenentität](#PBI_field_Account). Um ein Feld vom Typ „Optionssatz“ hinzuzufügen, lesen Sie unter [Einem Bericht ein Optionssatzfeld hinzufügen](#PBI_optionset_field).  
  
1. Wählen Sie unter Power BI Desktop **Abfragen bearbeiten**.  
  
2. Wählen Sie im linken Navigationsbereich des Abfrage-Editors unter **Abfragen** die Abfrage aus, die das benutzerdefinierte Feld enthält, das Sie für Berichte zur Verfügung stellen möchten, wie beispielsweise die Entitätsabfrage **Chance**.  
  
3. Wählen Sie im rechten Bereich unter **ANGEWENDETE SCHRITTE** die Einstellungsschaltfläche ![Einstellungsschaltfläche](media/mp-ua-r16-settings.png "Einstellungsschaltfläche") neben **Andere Spalten entfernt**.  
  
4. Die Liste **Spalten auswählen** zeigt alle Felder für die Entität, einschließlich benutzerdefinierter Felder. Wählen Sie das gewünschte benutzerdefinierte Feld aus und wählen Sie dann **OK**.  
  
    Die Entitätsabfrage wird aktualisiert und der Entitätstabelle wird eine Spalte für das benutzerdefinierte Feld hinzugefügt, das Sie ausgewählt haben.  
  
5. Wählen Sie im rechten Bereich unter **ANGEWENDETE SCHRITTE** **Lang - Umbenannte Spalten** und wählen Sie dann **Erweiterter Editor**, um die Zuordnung für das Feld zur Entitätsabfrage hinzuzufügen. Wenn der benutzerdefinierte Feldname für die Opportunity-Entität beispielsweise *int_forecast* und der Anzeigename *Forecast* lautet, sollte der Eintrag so aussehen.  
  
   ```  
   {"int_forecast","Forecast"}  
   ```  
  
   ![Eine Zuordnung für ein benutzerdefiniertes Feld in einem Bericht hinzufügen](media/pbi-addfieldmapping.png "Eine Zuordnung für ein benutzerdefiniertes Feld in einem Bericht hinzufügen")  
  
6. Nachdem Sie die Feldzuordnung hinzugefügt haben, stellen Sie sicher, dass es keine Syntaxfehler gibt, die am Ende des erweiterten Editor angezeigt werden. Stellen Sie auch sicher sicher, dass der Feldname genauso angezeigt wird, wie in der Spaltenüberschrift, einschließlich der richtigen Groß-/Kleinschreibung. Wenn keine Syntax- oder Tabellenfehler erkannt werden, wählen Sie **Beendet**.  
  
7. Klicken Sie im Abfrageeditor auf **Schließen und Übernehmen**.  
  
    Das benutzerdefinierte Feld ist jetzt im rechten Bereich unter **Felder** für die Entität verfügbar und kann neuen oder vorhandenen Berichten hinzugefügt werden.  
  
<a name="PBI_field_Account"></a>   
## <a name="add-a-custom-field-to-a-report-for-the-account-entity"></a>Hinzufügen eines benutzerdefinierten Felds zu einem Bericht für die Firmenentität  
 Da die Firmenabfrage Fetch XML verwendet, um die Abfrage zu filtern, unterscheiden sich die Schritte zum Hinzufügen eines Felds von anderen Entitätsabfragen, die OData verwenden. Weitere Informationen zum Hinzufügen eines benutzerdefinierten Felds zu Entitäten, die mit OData abgefragt werden, finden Sie unter [Hinzufügen eines benutzerdefinierten Felds zu einem Bericht](#PBI_edit_field).  
  
1. Kopieren Sie die kodierte Fetch XML-Abfrage für die Kontoentität. Gehen Sie dazu wie folgt vor:  
  
   1.  Wählen Sie unter Power BI Desktop **Abfragen bearbeiten**.  
  
   2.  Wählen Sie im linken Navigationsbereich des Abfrageeditors unter **Abfragen** die Entitätsabfrage **Konto** aus, und wählen Sie dann in der Multifunktionsleiste **Erweiterter Editor**.  
  
   3.  Kopieren Sie den gesamten codierten Fetch XML-Code angefangen mit der ersten Zeile beginnend mit %3Cfetch bis fetch%3E.  
  
   4.  Der codierte Fetch XML-Code, den Sie kopieren, sollte in etwa wie folgt aussehen:  
  
        %3Cfetch%20version%3D%221.0%22%20output-format%3D%22xml-platform%22%20mapping%3D%22logical%22%20distinct%3D%22true%22%3E%3Centity%20name%3D%22account%22%3E%3Cattribute%20name%3D%22territorycode%22%20%2F%3E%3Cattribute%20name%3D%22customersizecode%22%20%2F%3E%3Cattribute%20name%3D%22owningbusinessunit%22%20%2F%3E%3Cattribute%20name%3D%22ownerid%22%20%2F%3E%3Cattribute%20name%3D%22originatingleadid%22%20%2F%3E%3Cattribute%20name%3D%22revenue%22%20%2F%3E%3Cattribute%20name%3D%22sic%22%20%2F%3E%3Cattribute%20name%3D%22marketcap%22%20%2F%3E%20%3Cattribute%20name%3D%22parentaccountid%22%20%2F%3E%3Cattribute%20name%3D%22owninguser%22%20%2F%3E%3Cattribute%20name%3D%22accountcategorycode%22%20%2F%3E%3Cattribute%20name%3D%22marketcap_base%22%20%2F%3E%3Cattribute%20name%3D%22customertypecode%22%20%2F%3E%3Cattribute%20name%3D%22address1_postalcode%22%20%2F%3E%3Cattribute%20name%3D%22numberofemployees%22%20%2F%3E%3Cattribute%20name%3D%22accountratingcode%22%20%2F%3E%3Cattribute%20name%3D%22address1_longitude%22%20%2F%3E%3Cattribute%20name%3D%22revenue_base%22%20%2F%3E%3Cattribute%20name%3D%22createdon%22%20%2F%3E%3Cattribute%20name%3D%22name%22%20%2F%3E%3Cattribute%20name%3D%22address1_stateorprovince%22%20%2F%3E%3Cattribute%20name%3D%22territoryid%22%20%2F%3E%3Cattribute%20name%3D%22accountclassificationcode%22%20%2F%3E%3Cattribute%20name%3D%22businesstypecode%22%20%2F%3E%3Cattribute%20name%3D%22address1_country%22%20%2F%3E%3Cattribute%20name%3D%22accountid%22%20%2F%3E%3Cattribute%20name%3D%22address1_latitude%22%20%2F%3E%3Cattribute%20name%3D%22modifiedon%22%20%2F%3E%3Cattribute%20name%3D%22industrycode%22%20%2F%3E%3Clink-entity%20name%3D%22opportunity%22%20from%3D%22parentaccountid%22%20to%3D%22accountid%22%20alias%3D%22ab%22%3E%3Cfilter%20type%3D%22and%22%3E%3Ccondition%20attribute%3D%22opportunityid%22%20operator%3D%22not-null%22%20%2F%3E%3Ccondition%20attribute%3D%22modifiedon%22%20operator%3D%22last-x-days%22%20value%3D%22365%22%20%2F%3E%3C%2Ffilter%3E%3C%2Flink-entity%3E%3C%2Fentity%3E%3C%2Ffetch%3E  
  
2. Decodieren Sie den codierten Fetch XML-Code. Es muss ein gültiger codierter FetchXML-Code sein und sollte fertig kodiert in etwa so aussehen:  
  
    \<fetch version="1.0" output-format="xml-platform" mapping="logical" distinct="true"> \<entity name="account"> \<attribute name="territorycode" /> \<attribute name="customersizecode" /> \<attribute name="owningbusinessunit" /> \<attribute name="ownerid" /> \<attribute name="originatingleadid" /> \<attribute name="revenue" /> \<attribute name="sic" /> \<attribute name="marketcap" />  \<attribute name="parentaccountid" /> \<attribute name="owninguser" /> \<attribute name="accountcategorycode" /> \<attribute name="marketcap_base" /> \<attribute name="customertypecode" /> \<attribute name="address1_postalcode" /> \<attribute name="numberofemployees" /> \<attribute name="accountratingcode" /> \<attribute name="address1_longitude" /> \<attribute name="revenue_base" /> \<attribute name="createdon" /> \<attribute name="name" /> \<attribute name="address1_stateorprovince" /> \<attribute name="territoryid" /> \<attribute name="accountclassificationcode" /> \<attribute name="businesstypecode" /> \<attribute name="address1_country" /> \<attribute name="accountid" /> \<attribute name="address1_latitude" /> \<attribute name="modifiedon" /> \<attribute name="industrycode" /> \<link-entity name="opportunity" from="parentaccountid" to="accountid" alias="ab"> \<filter type="and"> \<condition attribute="opportunityid" operator="not-null" /> \<condition attribute="modifiedon" operator="last-x-days" value="365" /> \</filter> \</link-entity> \</entity> \</fetch>  
  
   > [!TIP]
   >  Viele URL Encoder- und -Decodertools sind im Netz frei verfügbar.  
  
3. Fügen Sie Ihre benutzerdefinierte Entität als Attributknoten zwischen den \<entity>-Knoten im FetchXML-Code hinzu. Um beispielsweise ein benutzerdefiniertes Feld mit dem Namen *customclassificationcode* hinzufügen, fügen Sie den Knoten nach einem anderen Attributknoten, wie z.B. **industrycode** ein.  
  
   ```  
  
   <attribute name="industrycode" />  
   <attribute name=" customclassificationcode "/>  
   <link-entity name="opportunity" from="parentaccountid" to="accountid" alias="ab">  
   ```  
  
4. URL-codieren Sie den aktualisierten Fetch XML-Code. Der Fetch XML-Code, der das neue benutzerdefinierte Attribut enthält, muss codiert sein, um die vorhandene OData-Feedabfrage zu ersetzen, die im Content Pack enthalten ist. Kopieren Sie dazu den aktualisierten Fetch XML-Code in die Zwischenablage und fügen Sie ihn in einen URL-Encoder ein.  
  
5. Fügen Sie die codierte Fetch XML-URL in den OData-Feed ein. Fügen Sie dazu die kodierte URL zwischen den Anführungszeichen nach dem Text **Query=[fetchXml=** ein und ersetzen Sie die vorhandene kodierte FetchXML, und wählen Sie dann **Beendet**.  
  
    Der unten gezeigte Screenshot gibt an, wo sich das am weitesten links stehende Anführungszeichen befindet.  
  
   ![Einfügen einer codierten URL in den OData-Feed](media/pbi-acct-encoded-url.PNG "Einfügen einer codierten URL in den OData-Feed")  
  
6. Wählen Sie im rechten Bereich unter **ANGEWENDETE SCHRITTE** die Einstellungsschaltfläche ![Einstellungsschaltfläche](media/mp-ua-r16-settings.png "Einstellungsschaltfläche") neben **Andere Spalten entfernt**.  
  
7. Die "Auswählen"-Spaltenliste zeigt alle Felder der Entität an, einschließlich der benutzerdefinierten Felder, aufführt. Wählen Sie das benutzerdefinierte Feld, wie z.B. *Klassifizierungscode*, das Sie zuvor der XML-Abfrage Fetch hinzugefügt haben, und wählen Sie dann **OK**.  
  
   > [!NOTE]
   >  Der Feldname, den Sie in der Spalten-Auswahl gewählt haben und der Feldname, den Sie der Fetch XML-Abfrage hinzufügen, müssen übereinstimmen.  
  
    Die Entitätsabfrage wird aktualisiert und der Entitätstabelle wird eine Spalte für das benutzerdefinierte Feld hinzugefügt, das Sie ausgewählt haben.  
  
8. Wählen Sie **Schließen & Anwenden** im Abfrageeditor.  
  
    Das benutzerdefinierte Feld ist jetzt im rechten Bereich unter **Felder** für die Entität verfügbar und kann neuen oder vorhandenen Berichten hinzugefügt werden.  
  
<a name="PBI_optionset_field"></a>   
## <a name="add-a-custom-option-set-field-to-a-report"></a>Ein benutzerdefinierte Feld "Optionssatz" einem Bericht hinzufügen  
 Optionssatzfelder ermöglichen die Auswahl aus mehreren Werten. Beispiele für vordefinierten Optionssatzfelder sind das "Bewertung"- und "Vertriebsphase"-Feld für eine Verkaufschance. Stellen Sie sich vor, Sie haben ein benutzerdefiniertes Optionsfeld auf dem Formular der Hauptchance, das die folgenden Werte und Bezeichnungen enthält.  
  
 ![Beispiel für einen benutzerdefinierten Optionssatz](media/pbi-custom-option-set-example.PNG "Beispiel für einen benutzerdefinierten Optionssatz")  
  
 Um das benutzerdefinierte Feld "Optionssatz" einem Bericht hinzufügen, gehen Sie folgendermaßen vor.  
  
1. Fügen Sie die Spalte "Benutzerdefiniertes Feld" hinzu.  
  
   -   Wählen Sie im linken Navigationsbereich des Abfrageeditors unter **Abfragen** die Entität aus, für die die zugehörige benutzerdefinierte Option eingestellt ist, wie z.B. die Entität *Chance*.  
  
   -   Wählen Sie im rechten Bereich unter **ANGEWENDETE SCHRITTE** die Einstellungsschaltfläche ![Einstellungsschaltfläche](media/mp-ua-r16-settings.png "Einstellungsschaltfläche") neben **Andere Spalten entfernt**.  
  
   -   Die "Auswählen"-Spaltenliste zeigt alle Felder der Entität an, einschließlich der benutzerdefinierten Felder, aufführt. Wählen Sie das benutzerdefinierte Feld, z.B. *new_customoptionset*, und wählen Sie dann **OK**.  
  
   -   Wählen Sie **Speichern**, und wählen Sie dann bei Aufforderung **Anwenden**.  
  
        Die Spalte für das benutzerdefinierte Feld wird in der Entitätstabelle angezeigt.  
  
2. Erstellen Sie die Optionssatzabfrage.  
  
   1.  Wählen Sie unter Power BI Desktop **Abfragen bearbeiten**.  
  
   2.  Wählen Sie im linken Navigationsbereich des Abfrageeditors unter **Abfragen** die Abfrage unter der Gruppe **Tabellen erstellen** aus, die das Feld Optionssatz hat, das dem Optionssatz am ähnlichsten ist, den Sie einem Bericht hinzufügen möchten. In diesem Beispiel hat die **SalesStageOptionSet**-Abfrage vier Optionen und ist daher eine gute Wahl.  
  
   3.  Wählen Sie **Erweiterter Editor**.  
  
        Die Optionssatzabfrage wird angezeigt.  
  
   ![Eine Optionssatzabfrage erstellen](media/pbi-makeoptionsetquery.png "Eine Optionssatzabfrage erstellen")  
  
   4.  Kopieren Sie die gesamte Abfrage in die Zwischenablage. Sie können sie in einen Text-Editor ,z.B. Notepad, einfügen, um sie für Referenzzwecke zu speichern.  
  
   5.  Klicken Sie im Abfrageeditor mit der rechten Maustaste auf die Gruppe **Tabellen erstellen**, wählen Sie **Neue Abfrage**, und wählen Sie dann **Abfrage löschen**.  
  
   6.  Geben Sie im rechten Bereich unter **Name** einen Namen ein, z.B. *CustomOptionSet*, und drücken Sie dann die Eingabetaste.  
  
   7.  Wählen Sie **Erweiterter Editor**.  
  
   8.  Fügen Sie im erweiterten Editor die Abfrage ein, die Sie zuvor kopiert haben.  
  
   9. Ersetzen Sie den vorhandenen Werten und die Optionen mit Ihren benutzerdefinierten Werten und Optionen. In diesem Beispiel ändern Sie dieses.  
  
       ```  
       let  
           Source = #table({"Value","Option"},{{0,"Qualify"},{1,"Develop"},{2,"Propose"},{3,"Close"}})  
       in  
           Source  
  
       ```  
  
        In das.  
  
       ```  
       let  
           Source = #table({"Value","Option"},{{0,"A"},{1,"B"},{2,"C"},{3,"D"},{4,"E"}})  
       in  
           Source  
  
       ```  
  
   10. Stellen Sie sicher, dass keine Syntaxfehler vorliegen, und wählen Sie dann **Beendet**, um den erweiterten Editor zu schließen. Die Tabelle mit Werten und von Optionen wird im Abfrage-Editor angezeigt.  
  
   ![Neue Optionssatzabfrage](media/pbi-optionsetquerycreated.png "Neue Optionssatzabfrage")  
  
   11. Wählen Sie **Speichern**, und wählen Sie dann bei Aufforderung **Anwenden**.  
  
3. Hinzufügen einer Zusammenführungsabfrage für die Entitäts- und benutzerdefinierten Optionssatztabellen.  
  
   1.  Wählen Sie im linken Bereich des Abfrageeditors unter **Entitäten** die Entität aus, die das benutzerdefinierte Optionsset enthält. In diesem Beispiel ist die Entitätsabfrage **Verkaufschance** ausgewählt.  
  
   2.  Wählen Sie in der Multifunktionsleiste **Abfragen zusammenführen** und, wenn Sie aufgefordert werden, einen Schritt einzufügen, **Einfügen**.  
  
   3.  Wählen Sie im Dialogfeld Zusammenführen die Spaltenüberschrift für das benutzerdefinierte Optionsset, z. B. *new_optionset*. Wählen Sie in der Dropdownliste die entsprechende Optionssatzabfrage aus, die Sie zuvor erstellt haben.  Wenn die Tabelle der Optionssätze erscheint, wählen Sie die Spaltenüberschrift **Wert**, um sie auszuwählen.  
  
   ![Tabellenauswahlen zusammenführen](media/pbi-merge-tables.png "Tabellenauswahlen zusammenführen")  
  
   4.  Lassen Sie die Art der Verbindung als **Linke Außenseite (alle von der ersten, übereinstimmend von der zweiten)**, und wählen Sie dann **OK**.  
  
       > [!TIP]
       >  Benennen Sie die Zusammenführungsabfrage um. Klicken Sie unter **ANGEWENDETE SCHRITTE** mit der rechten Maustaste auf die von Ihnen erstellte Zusammenführungsabfrage, wählen Sie **Umbenennen** und geben Sie einen beschreibenden Namen ein, z.B. *CustomOptionSet zusammenführen*.  
  
4. Definieren Sie die Spalte so, dass nur die Bezeichnungen angezeigt werden.  
  
   1.  Wählen Sie im linken Bereich des Abfrageeditors unter Entitäten die Entität aus, die das benutzerdefinierte Optionsset enthält. In diesem Beispiel ist die Entitätsabfrage **Verkaufschance** ausgewählt.  
  
   2.  Wählen Sie im rechten Bereich unter **ANGEWENDETE SCHRITTE** eine der erweiterten Abfragen aus, um die zusammengeführten Spalten anzuzeigen, wie z.B. **Erweiterte SalesStage**.  
  
   3.  Suchen und Auswählen der Spaltenüberschrift für die neue Spalte, die im Rahmen des früheren Abfrageschrittes Zusammenführen erstellt wurde.  
  
   4.  Wählen Sie auf der Registerkarte **Transformation** **Erweitern**.  
  
   5.  Löschen Sie im Dialog "Neue Spalte erweitern" die Spalte, die den Werten entspricht (da nur die Bezeichnungen in der Spalte angezeigt werden sollen). **Fertig** auswählen  
  
   ![Auswählen der Spalte, die die Beschriftung darstellt](media/pbi-expand-column.png "Auswählen der Spalte, die die Beschriftung darstellt")  
  
   6.  Wählen Sie **Speichern**, und wählen Sie dann bei Aufforderung **Anwenden**.  
  
5. Ändern Sie den Spaltennamen für die Berichtserstellung.  
  
   1.  Wählen Sie im linken Bereich des Abfrageeditors unter **Entitäten** die Entität aus, die das benutzerdefinierte Optionsset enthält. In diesem Beispiel ist die Entitätsabfrage **Verkaufschance** ausgewählt.  
  
   2.  Wählen Sie **Erweiterter Editor**.  
  
   3.  Fügen Sie eine umbenannte Spaltenposition hinzu, stellen Sie sicher, dass keine Syntaxfehler vorliegen, und wählen Sie dann **Beendet**. In diesem Beispiel lautet der benutzerdefinierte Optionssatzspaltenname, der zuvor erstellt wurde, **NewColumn** und wurde umbenannt in *Benutzerdefinierter Optionssatz*.  
  
   ![Umbenennen einer Spalte für die anzeige in Berichten](media/pbi-rename-column.png "Umbenennen einer Spalte für die anzeige in Berichten")  
  
   4.  Wählen Sie **Speichern**, und wählen Sie dann bei Aufforderung **Anwenden**.  
  
6. Wählen Sie **Schließen & Anwenden**, um den Abfrageeditor zu schließen.  
  
    Der benutzerdefinierte Optionssatz kann nun verwendet werden, um Power BI-Berichte zu erstellen.  
  
<a name="BPI_increaserows"></a>   
## <a name="increase-the-number-of-rows-queried"></a>Erhöhen Sie die Anzahl der abgefragten Zeilen  
 Standardmäßig dürfen alle Power BI-Entitätsabfragen in den Content Packs 100.000 Zeilen nicht überschreiten. Um die Zeilenanzahl zu erhöhen, die abgefragt werden kann, führen Sie die folgenden Schritte aus.  
  
> [!IMPORTANT]
>  Das Überschreiten der Zeilenanzahlgrenze kann die Zeit, die zur Aktualisierung eines Berichts benötigt wird, beträchtlich erhöhen. Außerdem hat der Power BI- Dienst eine 30-Minuten-Grenze für das Ausführen von Abfragen. Sie sollten daher vorsichtig mit dem Erhöhen der Zeilenanzahlgrenze sein.  
  
1. Wählen Sie unter Power BI Desktop **Abfragen bearbeiten**.  
  
2. Wählen Sie im linken Navigationsbereich des Abfrage-Editors unter **Abfragen** die Entitätsabfrage aus, für die Sie die Zeilenzahlgrenze erhöhen möchten, wie z.B. die Entität **Lead**.  
  
3. Wählen Sie im rechten Fensterbereich unter **ANGEWENDETE SCHRITTE** **Kept First Rows**.  
  
4. Erhöhen Sie die gefilterte Zeilenanzahl. Um beispielsweise auf 150.000 erhöhen, ändern Sie Table.FirstN(#"Filtered Rows",100001), auf Table.FirstN(#"Filtered Rows",150000)  
  
5. Wählen Sie im rechten Fensterbereich unter **ANGEWENDETE SCHRITTE** **Check Row Count**.  
  
6. Suchen Sie den **>100,000**-Bereich dieses Schritts.  
  
   ![Zeilenzählerwert erhöhen](media/pbi-increaserowcount.png "Zeilenzählerwert erhöhen")  
  
7. Erhöhen Sie den Wert auf eine größere Anzahl, zum Beispiel *150.000*.  
  
8. Wählen Sie **Schließen & Anwenden** im Abfrageeditor.  
  
<a name="BPI_publish"></a>   
## <a name="publish-your-report-to-the-power-bi-service"></a>Veröffentlichen Ihres Bericht im Power BI-Service  
 Veröffentlichen Sie Ihren Bericht organisationsintern und greifen Sie mit fast allen Geräten von überall darauf zu.  
  
1. Wählen Sie auf der Power BI Desktop-Hauptseite **Start** das Registerkarten-Ribbon **Veröffentlichen**.  
  
2. Wenn Sie aufgefordert werden, sich beim Dienst Power BI anzumelden, wählen Sie **Anmelden**.  
  
3. Wenn mehrere Ziele verfügbar sind, wählen Sie das gewünschte aus und wählen Sie dann **Veröffentlichen**.  
  
### <a name="see-also"></a>Siehe auch  
 [Verwenden Sie Power BI mit Dynamics 365 Customer Engagement (on-premises) ](use-power-bi.md).
