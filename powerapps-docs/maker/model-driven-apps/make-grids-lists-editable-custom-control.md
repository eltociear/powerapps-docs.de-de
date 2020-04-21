---
title: Modellgesteuerte App-Raster (Listen) bearbeitbar machen mit Hilfe des benutzerdefinierten Steuerelements für bearbeitbares Raster mit Power Apps | Microsoft-Dokumentation
description: Erfahren Sie, wie das benutzerdefinierte Steuerelement „Bearbeitbares Raster” verwendet wird
ms.custom: ''
ms.date: 04/09/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: cefbc0c2-769b-4230-ab5a-b28a84630a42
caps.latest.revision: 8
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: edb149b72716eb22e97ffce2d54a14be3bf84de5
ms.sourcegitcommit: af653cd30f5879fea97a594d458d355fe18f4834
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2020
ms.locfileid: "3258513"
---
# <a name="make-model-driven-app-grids-lists-editable-using-the-editable-grid-custom-control"></a>Modellgetriebene App-Raster (Listen) editierbar machen mit Benutzerdefiniertes Steuerelement für bearbeitbares Raster

In früheren Versionen von Dynamics CRM konnten Benutzer Daten nicht direkt in Rastern (manchmal Listen genannt) oder in den Unterrastern auf Formularen eingeben. Sie mussten den Datensatz im Raster auswählen, um ein Formular zu öffnen, die Daten zu bearbeiten und dann zu speichern, was Schritte erforderte. Mit bearbeitbaren Rastern können Benutzer umfangreiche Inlinebearbeitung direkt von Rastern und Unterrastern aus vornehmen, ungeachtet dessen, ob sie eine Web-App, ein Tablet oder Smartphone verwenden.  
  
 ![Bearbeitbare Raster - Beispiele](media/editable-grid-examples.png "Bearbeitbare Raster - Beispiele")  
  
 Wenn bearbeitbare Raster über das benutzerdefinierte Steuerelement für bearbeitbare Raster aktiviert werden, können Benutzer die meisten Feldtypen, einschließlich grundlegender Suchfelder und Optionssätze bearbeiten.  

**Bearbeitbare Raster unterstützen:**
  
-   Inline-Bearbeitung von Datensätzen auf der Ebene von Entitäten oder Unterrastern (einschließlich benutzerdefinierte Entitäten)  
  
-   Systemansichten und persönliche Ansichten  
  
-   Internet- und Mobilclienten  
  
-   Navigation mit Tastatur oder Maus  
  
-   Gruppieren und Sortieren (Sie können clientseitige Datensätze nach einer beliebigen Spalte in der aktuellen Ansicht gruppieren)  
  
-   Filtern  
  
-   Spalten verschieben und ihre Größe ändern  
  
-   Paginierung  
  
-   Änderungen aus einer Sitzung zu einer anderen speichern, zum Gruppieren, Sortieren, Filtern, Paginieren und Verschieben und Ändern der Größe von Spalten  
  
-   Suchkonfiguration  
  
-   Berechnete Felder und Rollup-Felder  
  
-   Geschäftsregeln (Fehlermeldung anzeigen, Feldwert festlegen, Geschäft festlegen erforderlich, Standardwert festlegen, Feld sperren oder Sperrung aufheben)  
  
-   JavaScript-Ereignisse  
  
-   Aktivieren oder Deaktivieren von Zellen auf Basis der Sicherheitsrolle  
  
-   Benutzer können weiterhin Suche und Diagramme verwenden und auf die Aktionsleiste zugreifen, wie bei schreibgeschützten Rastern  
  
## <a name="make-main-grids-editable"></a>Hauptraster bearbeitbar machen  
  
1.  Öffnen Sie den [Lösungs-Explorer](advanced-navigation.md#solution-explorer).  
  
2.  Öffnen Sie in der Liste **Entitäten** die entsprechende Entität, wählen Sie die Registerkarte **Steuerelemente** aus, und wählen Sie dann **Steuerelement hinzufügen** aus.  
  
     ![Benutzerdefiniertes Steuerelement für bearbeitbares Raster hinzufügen](media/add-editable-grids-custom-control.png "Benutzerdefiniertes Steuerelement für bearbeitbares Raster hinzufügen")  
  
3.  Wählen Sie im Dialogfeld **Steuerelement hinzufügen** die Option **Bearbeitbares Raster** aus, und wählen Sie dann **Hinzufügen** aus.  
  
4.  Wählen Sie in der Zeile **Bearbeitbares Raster**, die hinzugefügt wird, den/die Formfaktor(en) aus, auf den/die das Raster angewendet werden soll. Dadurch wird das bearbeitbare Rastersteuerelement zum Standardsteuerelement für den/die ausgewählten Formfaktor(en).  
  
     ![Bearbeitbare Rasterzeile mit Formfaktor-Auswahl](media/editable-grid-row-wit-factor-selection.png "Bearbeitbare Rasterzeile mit Formfaktor-Auswahl")    

   > [!NOTE]
   >  Zur Ausführungszeit können Benutzer zwischen schreibgeschützten Rastern und bearbeitbaren Rastern umschalten.  
      
5.  Um eine Suche hinzuzufügen, wählen Sie in der Optionsgruppe **Bearbeitbares Raster** die Option **Suche hinzufügen** aus, und dann im Dialogfeld **Eigenschaft „Suche hinzufügen” konfigurieren**:  
  
    1.  Wählen Sie in der Liste **Verfügbare Ansichten** die Ansicht aus, die der Suche hinzugefügt werden soll (z. B. **Meine aktiven Konten**).  
  
    2.  Wählen Sie in der Liste **Verfügbare Spalten** die Suchenspalte, die hinzugefügt werden soll (z. B. **Primärer Kontakt**).  
  
    3.  Wählen Sie in der Liste **Standardansicht** die Datenquelle für das Suchfeld aus.  
  
    4.  Wenn Sie die angezeigten Datensätze beschränken möchten, aktivieren Sie das Kontrollkästchen **Nur Datensätze anzeigen, für die Folgendes zutrifft:** aus, und wählen Sie dann die Kriterien in der Liste aus, und wählen Sie **OK** aus.  
  
         ![Suche im Steuerelement Bearbeitbares Unterraster hinzufügen](media/add-lookup-in-editable-grid-control.png "Suche im Steuerelement Bearbeitbares Unterraster hinzufügen")  
     
6.  Wenn Sie ein geschachteltes Raster haben, wählen Sie die Stiftschaltfläche für **Geschachtelte Rasteransicht** aus, und wählen dann die Entität und die Ansicht für das geschachtelte Raster aus. Wählen Sie unter **ID des übergeordneten geschachtelten Rasters** die Beziehung für die Entitäten aus. Beispielsweise verbindet das ParentAccountID-Feld **Firma** und **Kontakt** die Entitäten.  
  
    > [!NOTE]
    >  Geschachtelte Raster sind nur für Telefone und Tablets, nicht für das Internet verfügbar.  
  
7.  Wenn Sie dem Benutzer die Benutzung der Gruppendaten durch eine beliebige Spalte in der Ansicht nicht gestatten möchten (weil Sie etwa Platz sparen möchten), wählen Sie in der Zeile **Nach Spalte gruppieren** die Stiftschaltfläche aus, und wählen Sie dann im Dialogfeld, **Eigenschaft „Nach Spalte gruppieren” konfigurieren** die Option **Deaktiviert** aus, und wählen Sie dann **OK** aus.  
  
    > [!TIP]
    >  Dies ist vor allem für Unterraster auf Formularen hilfreich.  
  
8.  Wenn Sie JavaScript-Ereignisse hinzufügen möchten, wählen Sie die Registerkarte **Ereignisse** und wählen Sie dann die entsprechenden Entitäten, Felder und Ereignisse aus. Weitere Informationen: [Dokumentation für Entwickler: Bearbeitbare Raster verwenden](/dynamics365/customer-engagement/developer/customize-dev/use-editable-grids-dynamics-365.md)  
  
     ![Fügen Sie Ereignisse in bearbeitbaren Unterrastersteuerelement hinzu](media/add-events-in-editable-grid-control.png "Fügen Sie Ereignisse in bearbeitbaren Unterrastersteuerelement hinzu")  
  
9. Um Ihre Arbeit zu speichern, wählen Sie **Speichern** auf der Aktionsleiste aus.  
  
10. Wenn Sie bereit sind, Änderungen für Ihr Team zur Verfügung zu stellen, wählen Sie **Veröffentlichen** auf der Aktionsleiste aus.  
  
11. Um die Änderungen zu testen, gehen Sie zu der Ansicht, die Sie in Schritt 5 angegeben haben, und nehmen dann Inline-Bearbeitungsänderungen vor.  
  
## <a name="make-a-sub-grid-on-a-form-editable"></a>Ein Unterraster in einem Formular bearbeitbar machen

> [!NOTE] 
> - Um die Änderung an einem bearbeitbaren Raster innerhalb eines Unterrasters zu speichern, muss der Benutzer explizit speichern, bevor er aus dem Formular heraus navigiert.
> - Wenn Sie Vorgängerformulare verwenden (Versionen vor Dynamics CRM 2016) und ein bearbeitbares Raster für ein Unterraster aktivieren, wird das bearbeitbare Unterraster nicht gerendert. Systemadministratoren können Vorgängerformulare in den Systemeinstellungen nach Bedarf deaktivieren.
  
1.  Öffnen Sie den [Lösungs-Explorer](advanced-navigation.md#solution-explorer).  
  
2.  Öffnen Sie das Formular, das das Unterraster enthält.  
  
3.  Wählen Sie das entsprechende Steuerelement aus, und wählen Sie im Menüband dann **Eigenschaften ändern** aus.  
  
4.  Im Dialogfeld **Eigenschaften festlegen** wählen Sie **Steuerelemente** aus, wählen Sie dann **Steuerelement hinzufügen** aus, und folgen Sie anschließend den gleichen Schritten, die oben aufgelistet wurden.  
  
## <a name="supported-standard-entities"></a>Unterstützte Standardentitäten  
  
||||  
|-|-|-|  
|**Internet/TabletTelefon**|**Nur Tablet/Telefon**|**Nur Internet**|  
|Firma<br /><br /> Termin<br /><br /> Buchbare Ressource<br /><br /> Buchbare Ressourcenbuchung<br /><br /> Kopfzeile für buchbare Ressourcenbuchungen<br /><br /> Buchbare Ressourcenkategorie<br /><br /> Zuordnung der buchbaren Ressourcenkategorie<br /><br /> Merkmal der buchbaren Ressource<br /><br /> Buchbare Ressourcengruppe<br /><br /> Buchungsstatus<br /><br /> Anfrage<br /><br /> Kateg.<br /><br /> Merkmal<br /><br /> Mitbewerber<br /><br /> Kontakt<br /><br /> E-Mail<br /><br /> Berechtigung<br /><br /> Feedback<br /><br /> Rechnung<br /><br /> Wissensartikel<br /><br /> Wissensartikelansichten<br /><br /> Wissensdatenbankdatensatz<br /><br /> Lead<br /><br /> Verkaufschance<br /><br /> Auftrag<br /><br /> Telefonanruf<br /><br /> Preisliste<br /><br /> Produkt<br /><br /> Warteschlange<br /><br /> Angebot<br /><br /> Bewertungsmodell<br /><br /> Bewertungswert<br /><br /> SLA-KPI-Instanz<br /><br /> Social Media-Aktivität<br /><br /> Social Media-Profil<br /><br /> Synchronisierungsfehler<br /><br /> Aufgabe<br /><br /> Teams<br /><br /> Benutzer|Aktivität<br /><br /> Anlage<br /><br /> Element der Kanalzugriffsprofilregel<br /><br /> Mitbewerberadresse<br /><br /> Verbindung<br /><br /> Verbindungsrolle<br /><br /> E-Mail-Signatur<br /><br /> E-Mail-Vorlage<br /><br /> Abgelaufener Prozess<br /><br /> Rechnung (Produkt)<br /><br /> Vorfall mit Wissensartikel<br /><br /> Lead für Vertriebs-Verkaufschance<br /><br /> Prozess<br /><br /> Postfach<br /><br /> Neuer Prozess<br /><br /> Hinweise<br /><br /> Verkaufschance (Produkt)<br /><br /> Vertriebsprozess Verkaufschance<br /><br /> Auftrag (Produkt)<br /><br /> Organisation<br /><br /> Telefon-zu-Anfrage-Prozess<br /><br /> Preislistenelement<br /><br /> Warteschlangenelement<br /><br /> Angebot (Produkt)<br /><br /> SharePoint-Dokument<br /><br /> Übersetzungsprozess|Kampagne<br /><br /> Kampagnenaktivität<br /><br /> Kampagnenreaktion<br /><br /> Kanalzugriffsprofil<br /><br /> Kanalzugriffsprofilregel<br /><br /> Vertrag<br /><br /> Anspruchsvorlage<br /><br /> Externe Partei<br /><br /> Fax<br /><br /> Brief<br /><br /> Marketingliste<br /><br /> Position<br /><br /> Schnellkampagne<br /><br /> Terminserie<br /><br /> Vertriebsdokumentation<br /><br /> SLA|  
 
##  <a name="data-types-that-arent-editable-in-an-editable-grid"></a>Datentypen, die in einem bearbeitbaren Raster nicht bearbeitbar sind
Die folgenden Datentypen sind nicht in bearbeitbaren Rastern bearbeitbar: Kunden und Partylist-Suchfelder; Zusammengesetzte (Adress-) Felder, Status/Statusfelder; mit der Suchentität verknüpfte Felder (beispielsweise umfasst die Firmenentität eine Kontaktsuche, in der das Kontaktfeld bearbeitbar ist, jedoch ist das Feld EmailAdress (Kontakt) nicht bearbeitbar). 

## <a name="group-by-views-work-on-client-side-only"></a>Das Gruppieren nach Ansichten funktioniert nur auf der Clientseite
Das Gruppierungsverhalten funktioniert nur auf der Clientseite und erstreckt sich nicht über Seiten. „Gruppieren nach“ ist eine Nur-Client-Funktion und funktioniert nur auf einer Datenseite. Bei „Gruppieren nach“ werden nicht alle Optionen angezeigt, die auf Ihrem vollständigen Dataset auf dem Server basieren. „Gruppieren nach“ zeigt die Gruppierung nur auf der aktuellen Seite an. Sie können die Gruppierung deaktivieren, indem Sie die Eigenschaft in der benutzerdefinierten Steuerelementkonfiguration verwenden. Weitere Informationen: [Hauptgitter bearbeitbar machen](#make-main-grids-editable)

 
## <a name="next-steps"></a>Nächste Schritte  
 [Verwenden von Tastenkombinationen in bearbeitbaren Rastern](https://docs.microsoft.com/dynamics365/customer-engagement/basics/keyboard-shortcuts#editable-grids-views)

