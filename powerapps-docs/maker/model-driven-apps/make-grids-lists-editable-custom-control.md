---
title: Aktivieren der Bearbeitung von Rastern (Listen) in modellgesteuerten Apps mit dem benutzerdefinierten Steuerelement „Bearbeitbares Raster“ mit PowerApps | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie das benutzerdefinierte Steuerelement „Bearbeitbares Raster“ verwenden.
ms.custom: ''
ms.date: 06/27/2018
ms.reviewer: ''
ms.service: crm-online
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
ms.openlocfilehash: 704280dbed2177ba9a5467e2897980f78c31b050
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39688624"
---
# <a name="make-model-driven-app-grids-lists-editable-using-the-editable-grid-custom-control"></a>Aktivieren der Bearbeitung von Rastern (Listen) in modellgesteuerten Apps mit dem benutzerdefinierten Steuerelement „Bearbeitbares Raster“

In früheren Versionen von Dynamics CRM konnten Benutzer Daten nicht direkt in Raster (manchmal auch „Listen“ genannt) oder Unterraster von Formularen eingeben. Sie mussten einen Datensatz im Raster auswählen, um ein Formular zu öffnen, die Daten zu bearbeiten und dann zu speichern. Das heißt, es waren mehrere Schritte erforderlich. Mit bearbeitbaren Rastern können Benutzer die umfangreiche Inlinebearbeitung direkt aus Rastern und Unterrastern ausführen, unabhängig davon, ob sie eine Web-App, ein Tablet oder ein Smartphone verwenden.  
  
 ![Beispiele für bearbeitbare Raster](media/editable-grid-examples.png "Beispiele für bearbeitbare Raster")  
  
 Wenn bearbeitbare Raster über das benutzerdefinierte Steuerelement „Bearbeitbares Raster“ aktiviert werden, können Benutzer die meisten Feldarten bearbeiten, einschließlich Felder für die einfache Suche und Optionssätze.  

**Bearbeitbare Raster unterstützen:**
  
-   Inlinebearbeitung von Datensätzen auf Entitäts- oder Unterrasterebene (einschließlich benutzerdefinierter Entitäten)  
  
-   Systemsichten und persönliche Ansichten  
  
-   Web- und mobile Clients  
  
-   Navigation mit einer Tastatur oder Maus  
  
-   Gruppieren und Sortieren nach beliebigen Spalten in der aktuellen Ansicht  
  
-   Filterung  
  
-   Verschieben und Ändern der Größe von Spalten  
  
-   Paginierung  
  
-   Speichern von Änderungen in einer Sitzung für eine andere für Gruppierung, Sortierung, Filterung, Paginierung, Verschieben und Ändern der Größe von Spalten  
  
-   Konfigurieren der Suche  
  
-   Berechnete Felder und Rollupfelder  
  
-   Geschäftsregeln („Fehlermeldung anzeigen“, „Feldwert festlegen“, „Eingabe als erforderlich festlegen“, „Standardwert festlegen“, „Feld sperren oder entsperren“)  
  
-   JavaScript-Ereignisse  
  
-   Aktivieren/Deaktivieren von Zellen basierend auf der Sicherheitsrolle  
  
-   Suchfunktionen, Diagramme und Zugriff auf die Aktionsleiste wie bei schreibgeschützten Rastern  
  
## <a name="make-main-grids-editable"></a>Aktivieren der Bearbeitung von Hauptrastern  
  
1.  Öffnen Sie den [Projektmappen-Explorer](advanced-navigation.md#solution-explorer).  
  
2.  Öffnen Sie in der Liste **Entitäten** die entsprechende Entität, wählen Sie die Registerkarte **Steuerelemente** und dann **Steuerelement hinzufügen** aus.  
  
     ![Benutzerdefiniertes Steuerelement zum Hinzufügen eines bearbeitbaren Rasters](media/add-editable-grids-custom-control.png "Benutzerdefiniertes Steuerelement zum Hinzufügen eines bearbeitbaren Rasters")  
  
3.  Wählen Sie im Dialogfeld **Steuerelement hinzufügen** **Bearbeitbares Raster** und dann **Hinzufügen** aus.  
  
4.  Wählen Sie in der hinzugefügten Zeile **Bearbeitbares Raster** die Formularfaktoren aus, auf die Sie das Raster anwenden möchten. Dadurch wird „Bearbeitbares Raster“ zum Standardsteuerelement für die ausgewählten Formularfaktoren.  
  
     ![Zeile „Bearbeitbares Raster“ mit Formularfaktorauswahl](media/editable-grid-row-wit-factor-selection.png "Zeile „Bearbeitbares Raster“ mit Formularfaktorauswahl")    

   > [!NOTE]
   >  Zur Laufzeit können Benutzer zwischen bearbeitbaren Rastern und schreibgeschützten Rastern wechseln.  
      
5.  Um eine Suche hinzuzufügen, wählen Sie in der Optionsgruppe **Bearbeitbares Raster** **Suche hinzufügen** aus, und nehmen Sie dann im Dialogfeld **Suche hinzufügen: Eigenschaft konfigurieren** die folgenden Einstellungen vor:  
  
    1.  Wählen Sie in der Liste **Verfügbare Ansichten** die Ansicht aus, der Sie die Suche hinzufügen möchten (z.B. **Meine aktiven Firmen**).  
  
    2.  Wählen Sie in der Liste **Verfügbare Spalten** die hinzuzufügende Suchspalte (z.B. **Primärer Kontakt**) aus.  
  
    3.  Wählen Sie in der Liste **Standardansicht** die Datenquelle für das Suchfeld aus.  
  
    4.  Wenn Sie die angezeigten Datensätze einschränken möchten, aktivieren Sie das Kontrollkästchen **Nur Datensätze anzeigen, für die Folgendes zutrifft**, wählen Sie Ihre Kriterien aus der Liste und dann **OK** aus.  
  
         ![„Suche hinzufügen“ im Steuerelement „Bearbeitbares Raster“](media/add-lookup-in-editable-grid-control.png "„Suche hinzufügen“ im Steuerelement „Bearbeitbares Raster“")  
     
6.  Wenn Sie ein geschachteltes Raster haben, wählen Sie die Schaltfläche mit dem Stift für **Geschachtelte Rasteransicht** und dann die Entität sowie die Ansicht für das geschachtelte Raster aus. Wählen Sie für **Übergeordnete ID des geschachtelten Rasters** die Beziehung für die Entitäten aus. Das Feld „ParentAccountID“ verbindet beispielsweise die Entitäten **Konto** und **Kontakt**.  
  
    > [!NOTE]
    >  Geschachtelte Raster sind nur für Smartphones und Tablets verfügbar – nicht für das Web.  
  
7.  Wenn Sie einem Benutzer nicht erlauben möchten, Daten in der Ansicht nach Spalten zu gruppieren (z.B. um Platz zu sparen), wählen Sie in der Zeile **Gruppieren nach Spalte** die Schaltfläche mit dem Stift und im Dialogfeld **Gruppieren nach Spalte: Eigenschaft konfigurieren** **Deaktiviert** und dann **OK** aus.  
  
    > [!TIP]
    >  Dies ist vor allem für Unterraster in Formularen nützlich.  
  
8.  Wenn Sie JavaScript-Ereignisse hinzufügen möchten, wählen Sie die Registerkarte **Ereignisse** und dann die entsprechenden Entitäten, Felder und Ereignisse aus. Weitere Informationen finden Sie unter [Dokumentation für Entwickler: Verwenden von bearbeitbaren Rastern](/dynamics365/customer-engagement/developer/customize-dev/use-editable-grids-dynamics-365.md).  
  
     ![Ereignisse im Steuerelement „Bearbeitbares Raster“ hinzufügen](media/add-events-in-editable-grid-control.png "Ereignisse im Steuerelement „Bearbeitbares Raster“ hinzufügen")  
  
9. Wählen Sie zum Speichern Ihrer Arbeit in der Aktionsleiste **Speichern** aus.  
  
10. Wenn Sie Ihrem Team Änderungen zur Verfügung stellen möchten, wählen Sie in der Aktionsleiste **Veröffentlichen** aus.  
  
11. Um Ihre Änderungen zu testen, gehen Sie zu der Ansicht, die Sie in Schritt 5 angegeben haben, und nehmen Sie einige Änderungen an der Inlinebearbeitung vor.  
  
## <a name="make-a-sub-grid-on-a-form-editable"></a>Aktivieren der Bearbeitung eines Unterrasters in einem Formular

> [!NOTE] 
> - Um Änderung an einem bearbeitbaren Raster in einem Unterraster zu speichern, muss der Benutzer einen expliziten Speichervorgang ausführen, bevor er das Formular verlässt.
> - Wenn Sie ältere Formulare (Versionen vor Dynamics CRM 2016) verwenden und ein bearbeitbares Raster auf einem Unterraster aktivieren, wird das bearbeitbare Unterraster nicht gerendert. Systemadministratoren können bei Bedarf ältere Formulare in den Systemeinstellungen deaktivieren.
  
1.  Öffnen Sie den [Projektmappen-Explorer](advanced-navigation.md#solution-explorer).  
  
2.  Öffnen Sie das Formular, das das Unterraster enthält.  
  
3.  Wählen Sie das entsprechende Steuerelement und dann im Menüband **Eigenschaften ändern** aus.  
  
4.  Wählen Sie im Dialogfeld **Eigenschaften festlegen** **Steuerelemente** und **Steuerelement hinzufügen** aus, und führen Sie dann die oben aufgeführten Schritte aus.  
  
## <a name="supported-standard-entities"></a>Unterstützte Standardentitäten  
  
||||  
|-|-|-|  
|**Web/Tablet/Smartphone**|**Nur Tablet/Smartphone**|**Nur Web**|  
|Konto<br /><br /> Appointment<br /><br /> Bookable Resource<br /><br /> Bookable Resource Booking<br /><br /> Bookable Resource Booking Header<br /><br /> Bookable Resource Category<br /><br /> Bookable Resource Category Assn<br /><br /> Bookable Resource Characteristic<br /><br /> Bookable Resource Group<br /><br /> Booking Status<br /><br /> Case<br /><br /> Kategorie<br /><br /> Characteristic<br /><br /> Competitor<br /><br /> Kontakt<br /><br /> E-Mail-Adresse<br /><br /> Entitlement<br /><br /> Feedback<br /><br /> Invoice<br /><br /> Wissensartikel<br /><br /> Wissensartikelansichten<br /><br /> Wissensdatenbank-Datensatz<br /><br /> Lead<br /><br /> Opportunity<br /><br /> Order<br /><br /> Telefonanruf<br /><br /> Price List<br /><br /> Product<br /><br /> Warteschlange<br /><br /> Quote<br /><br /> Rating Model<br /><br /> Rating Value<br /><br /> SLA-KPI-Instanz<br /><br /> Social Media-Aktivität<br /><br /> Social Media-Profil<br /><br /> Synchronisierungsfehler<br /><br /> Task<br /><br /> Team<br /><br /> User|Aktivität<br /><br /> Anlage<br /><br /> Element der Kanalzugriffsprofil-Regel<br /><br /> Mitbewerberadresse<br /><br /> Verbindung<br /><br /> Verbindungsrolle<br /><br /> E-Mail-Signatur<br /><br /> E-Mail-Vorlage<br /><br /> Abgelaufener Prozess<br /><br /> Rechnung (Produkt)<br /><br /> Wissensartikelvorfall<br /><br /> Lead für Vertriebsprozess Verkaufschance<br /><br /> Prozess<br /><br /> Mailbox<br /><br /> Neuer Prozess<br /><br /> Note<br /><br /> Verkaufschance (Produkt)<br /><br /> Vertriebsprozess Verkaufschance<br /><br /> Auftrag (Produkt)<br /><br /> Organisation<br /><br /> Telefon-zu-Anfrage-Prozess<br /><br /> Price List Item<br /><br /> Queue Item<br /><br /> Angebot (Produkt)<br /><br /> SharePoint-Dokument<br /><br /> Übersetzungsprozess|Kampagne<br /><br /> Kampagnenaktivität<br /><br /> Kampagnenreaktion<br /><br /> Kanalzugriffsprofil<br /><br /> Kanalzugriffsprofil-Regel<br /><br /> Vertrag<br /><br /> Berechtigungsvorlage<br /><br /> Externe Partei<br /><br /> Fax<br /><br /> Letter<br /><br /> Marketingliste<br /><br /> Position<br /><br /> Schnellkampagne<br /><br /> Terminserie<br /><br /> Vertriebsdokumentation<br /><br /> SLA|  
 
##  <a name="data-types-that-arent-editable-in-an-editable-grid"></a>Nicht bearbeitbare Datentypen in einem bearbeitbaren Raster
Die folgenden Datentypen können in bearbeitbaren Rastern nicht bearbeitet werden: Suchfelder für Kunden und Parteilisten; zusammengesetzte (Adress-)Felder; Felder für Status/Zustand; Suchfelder für Entitäten (z.B. beinhaltet die Entität „Konto“ eine Kontaktsuche, wobei das Feld „Kontakt“ bearbeitbar ist, das Feld „EmailAdress(Contact)“ jedoch nicht).  
 
## <a name="next-steps"></a>Nächste Schritte  
 [Verwenden von Tastenkombinationen in bearbeitbaren Rastern](https://docs.microsoft.com/dynamics365/customer-engagement/basics/keyboard-shortcuts#editable-grids-views)

