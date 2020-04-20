---
title: Konfigurieren von Masterdaten und Anzeigen von Dashboards in der Notfallreaktions-App für Krankenhäuser | Microsoft-Dokumentation
description: Detaillierte Anweisungen für IT-Administratoren von Krankenhäusern für die Bereitstellung und Konfiguration der Beispielanwendung in ihrer Organisation.
author: pankajarora-msft
manager: annbe
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/15/2020
ms.author: pankar
ms.reviewer: kvivek
searchScope:
- PowerApps
ms.openlocfilehash: 5a622a7d945fa78536c3addb75cfa64d327c7c90
ms.sourcegitcommit: 263a12aefa72a3d73e07b2660bf1e89eba532a16
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81448271"
---
# <a name="configure-master-data-and-view-dashboards"></a>Konfigurieren von Masterdaten und Anzeigen von Dashboards

Dieser Artikel bietet Informationen dazu, wie Sie mithilfe der Administrator-App (modellgesteuerte App) Masterdaten für Ihre Lösung hinzufügen und verwalten und wie Sie wichtige Erkenntnisse und Metriken im Power BI-Dashboard anzeigen.

Diese Aufgaben werden in der Regel von geschäftlichen Administratoren in Ihrer Organisation ausgeführt.

## <a name="configure-and-manage-master-data-for-your-organization"></a>Konfigurieren und Verwalten von Masterdaten für Ihre Organisation

Verwenden Sie die Administrator-App, um Masterdaten für Ihre Organisation zu erstellen und zu verwalten. Diese Daten werden benötigt, damit die Notfallreaktions-App für Krankenhäuser funktionieren kann.

> [!IMPORTANT]
> - Stellen Sie sicher, dass der zuständige IT-Administrator die Lösung in Ihrer Organisation bereitgestellt und geschäftlichen Administratoren die geeigneten Berechtigungen zur Verwendung der Administrator-App erteilt hat. Weitere Informationen: [Bereitstellen der Notfallreaktions-App für Krankenhäuser](deploy-configure.md#deploy-the-hospital-emergency-response-app)
> 
> - Sie können Ihre Daten auch aus den Datendateien importieren, die im Bereitstellungspaket zur Verfügung stehen. Weitere Informationen: [Schritt 4: Laden der Konfigurations- und Stammdaten für Ihre Organisation](deploy-configure.md#step-4-load-configuration-and-master-data-for-your-organization)

Sie müssen Stammdaten in diesen Entitäten in der folgenden Reihenfolge hinzufügen:

1. [Systems (Systeme)](#systems-data)

1. [Regionen](#regions-data)

1. [Facilities (Einrichtungen)](#facilities-data)

1. [Speicherorte](#locations-data)

1. [Departments (Abteilungen)](#departments-data)

Die Stammdaten werden in der Admin-App im linken Navigationsbereich im Bereich **Locations** verwaltet:

> [!div class="mx-imgBorder"]
> ![Bereich „Locations“](media/locations-area.png)

Die Entitäten unter dem Bereich **Hierarchy** (Hierarchie) sind in der Reihenfolge aufgeführt, in der Sie die Daten auffüllen müssen.

> [!NOTE]
> Daten zur Pflegeintensität (Acuity) werden während der Bereitstellung der Lösung importiert. Weitere Informationen: [Schritt 4: Laden der Konfigurations- und Stammdaten für Ihre Organisation](deploy-configure.md#step-4-load-configuration-and-master-data-for-your-organization)

### <a name="systems-data"></a>Daten zu Systemen

Mit der Entität **Systems** können Sie Einträge für Krankenhaussysteme erstellen und verwalten. Dies ermöglicht Ihnen die Verwaltung mehrerer Krankenhaussysteme innerhalb derselben Organisation.

So erstellen Sie einen Datensatz

1. Melden Sie sich über die von Ihrem IT-Administrator bereitgestellte URL bei der Administrator-App (modellgesteuerte App) an.

1. Wählen Sie im linken Bereich **Systems** und dann **New** (Neu) aus:  
    > [!div class="mx-imgBorder"]
    > ![„Systems“->„New“ auswählen](media/select-systems-new.png)

1. Geben Sie auf der Seite **New System** (Neues System) die entsprechenden Werte an:  
   > [!div class="mx-imgBorder"]
   > ![Details zum neuen System eingeben](media/enter-details-new-system.png)

   | **Feld**            | **Beschreibung**                                    |
   |----------------------|----------------------------------------------------|
   | Systemname          | Geben Sie für Ihr Krankenhaus einen Namen ein.                     |
   | Beschreibung          | Geben Sie eine optionale Beschreibung ein.                      |
   | Effective Start Data (Tatsächliches Startdatum) | Geben Sie Startdatum und -uhrzeit für dieses Krankenhaussystem ein. |
   | Effective Start End (Tatsächliches Enddatum)   | Geben Sie Enddatum und -uhrzeit für dieses Krankenhaussystem ein.   |

1. Wählen Sie **Speichern und Schließen** aus. Der neu erstellte Datensatz ist in der Liste **Systems** verfügbar.

Um den Datensatz zu bearbeiten, wählen Sie ihn aus. Aktualisieren Sie die Werte wie gewünscht, und wählen Sie **Speichern und schließen** aus.

### <a name="regions-data"></a>Daten zu Regionen

Die Entität **Regions** ermöglicht Ihnen die Verwaltung der geografischen Regionen in Ihren Krankenhaussystemen.

So erstellen Sie einen Datensatz

1. Melden Sie sich über die von Ihrem IT-Administrator bereitgestellte URL bei der Administrator-App (modellgesteuerte App) an.

1. Wählen Sie im linken Bereich **Regions** und dann **New** aus.

1. Geben Sie auf der Seite **New Region** (Neue Region) die entsprechenden Werte an:  

    > [!div class="mx-imgBorder"]
    > ![Details zu neuer Region eingeben](media/enter-details-new-region.png)

    | **Feld**            | **Beschreibung**                                                                                          |
    |----------------------|----------------------------------------------------------------------------------------------------------|
    | System               | Wählen Sie ein Krankenhaussystem aus. Diese Liste wird auf Grundlage der Daten zu den **Systemen** aufgefüllt, die Sie zuvor erstellt haben. |
    | Name der Region          | Geben Sie den Namen der Region ein. Beispiel: Seattle.                                                              |
    | Beschreibung          | Geben Sie eine optionale Beschreibung ein.                                                                            |
    | Effective Start Data (Tatsächliches Startdatum) | Geben Sie Startdatum und -uhrzeit für diese Region ein.                                                       |
    | Effective Start End (Tatsächliches Enddatum)   | Geben Sie Enddatum und -uhrzeit für diese Region ein.                                                         |

1. Wählen Sie **Speichern und Schließen** aus. Der neu erstellte Datensatz ist in der Liste **Regions** verfügbar.

Um den Datensatz zu bearbeiten, wählen Sie ihn aus. Aktualisieren Sie die Werte wie gewünscht, und wählen Sie **Speichern und schließen** aus.

### <a name="facilities-data"></a>Daten zu Einrichtungen

Mithilfe der Entität **Facilities** können Sie die Krankenhausstandorte innerhalb jeder Region verwalten. Beispielsweise die Einrichtungen **Redmond** und **Bellevue** in der Region **Seattle**.

So erstellen Sie einen Datensatz

1. Melden Sie sich über die von Ihrem IT-Administrator bereitgestellte URL bei der Administrator-App (modellgesteuerte App) an.

1. Wählen Sie im linken Bereich **Facilities** und dann **New** aus.

1. Geben Sie auf der Seite **New Facility** (Neue Einrichtung) die entsprechenden Werte an: 

    > [!div class="mx-imgBorder"] 
    > ![Details zu neuer Einrichtung eingeben](media/enter-details-new-facility.png)

    | **Feld**            | **Beschreibung**                                                                                 |
    |----------------------|-------------------------------------------------------------------------------------------------|
    | Region               | Wählen Sie die Region aus, der diese Einrichtung zugeordnet ist. Diese Liste wird auf Grundlage der Daten zu den **Regionen** aufgefüllt, die Sie zuvor erstellt haben. |
    | Facility Name (Name der Einrichtung)        | Geben Sie den Namen der Einrichtung ein. Beispiel: Bellevue.                                                  |
    | Total Vents (Beatmungsgeräte insgesamt)          | Geben Sie die Gesamtanzahl der in der Einrichtung verfügbaren Beatmungsgeräte ein.                                  |
    | Beschreibung          | Geben Sie eine optionale Beschreibung ein.                                                                   |
    | Effective Start Data (Tatsächliches Startdatum) | Geben Sie Startdatum und -uhrzeit für diese Einrichtung ein.                                                     |
    | Effective Start End (Tatsächliches Enddatum)   | Geben Sie Enddatum und -uhrzeit für diese Einrichtung ein.                                                       |
    |Total Beds (Betten insgesamt)      | Wird automatisch berechnet.|
    |Total Occupied (Belegung gesamt)      | Wird automatisch berechnet.|
    |Facility Address (Anschrift der Einrichtung)      | Geben Sie Straße, Postleitzahl, Ort, Bundesland sowie Längen- und Breitengrad der Einrichtung an.|

    Geben Sie bei Bedarf die Adresse der Einrichtung ein.

1. Wählen Sie **Speichern und Schließen** aus. Der neu erstellte Datensatz ist in der Liste **Facilities** verfügbar.

Um den Datensatz zu bearbeiten, wählen Sie ihn aus. Aktualisieren Sie die Werte wie gewünscht, und wählen Sie **Speichern und schließen** aus.

### <a name="locations-data"></a>Daten zu Standorten

Mithilfe der Entität **Locations** können Sie Standorte innerhalb jeder Krankenhauseinrichtung verwalten.

> [!NOTE]
> Bevor Sie einen Datensatz des Typs **Locations** erstellen, stellen Sie sicher, dass Sie die Pflegestufendaten mithilfe der Datei **00 - Acuities Import.xlsx** importiert haben. Weitere Informationen finden Sie weiter oben in [Schritt 4: Laden der Konfigurations- und Stammdaten für Ihre Organisation](deploy-configure.md#step-4-load-configuration-and-master-data-for-your-organization). Der Grund dafür ist, dass zur Erstellung eines Datensatzes des Typs **Location** Informationen zur Pflegestufe erforderlich sind.

So erstellen Sie einen Datensatz

1. Melden Sie sich über die von Ihrem IT-Administrator bereitgestellte URL bei der Administrator-App (modellgesteuerte App) an.

1. Wählen Sie im linken Bereich **Locations** und dann **New** aus.

1. Geben Sie auf der Seite **New Location** (Neuer Standort) die entsprechenden Werte an:  
 
    > [!div class="mx-imgBorder"]
    > ![Details zu neuem Standort eingeben](media/enter-details-new-location.png)

    | **Feld**            | **Beschreibung**                                                                                      |
    |----------------------|------------------------------------------------------------------------------------------------------|
    | Standortname        | Geben Sie den Namen des Standorts ein.                                                                       |
    | Facility             | Wählen Sie eine Einrichtung aus. Diese Liste wird auf Grundlage der Daten zu den **Einrichtungen** aufgefüllt, die Sie zuvor erstellt haben. |
    | Etage                | Geben Sie die Informationen zur Etage der Einrichtung ein.                                                         |
    | Einheit                 | Geben Sie die Informationen zur Einheit der Einrichtung ein.                                                           |
    | Occupancy Percentage (Belegungsprozentsatz) | Wird basierend auf der letzten Zählung und der Gesamtanzahl von Betten automatisch berechnet.                                         |
    | Acuity (Pflegestufe)      | Wählen Sie den Datensatz zur Pflegestufe aus, der mit diesem Standort verknüpft ist.                                                                                                     |
    | COVID Location (COVID-Standort)      | Wählen Sie aus, ob an diesem Standort COVID-Patienten behandelt werden (**Yes** oder **No**).                                                                                                      |
    | Total Beds (Betten insgesamt)           | Geben Sie die Gesamtanzahl der Betten in der Einrichtung ein.                                                       |
    | Surge Beds (Notbetten)           | Geben Sie die Gesamtanzahl der Notbetten in der Einrichtung ein. Notbetten sind solche, die über die zugelassene Bettenkapazität hinaus belegt werden können, wenn Patienten aufgenommen werden müssen.                                                      |
    | Blocked beds (Belegte Betten)         | Geben Sie die Anzahl der belegten Betten in der Einrichtung ein.                                                     |
    | Last Census (Letzte Volkszählung)          | Wird basierend auf dem zuletzt erstellten Volkszählungs-Datensatz aufgefüllt.                                             |
    | Effective Start Data (Tatsächliches Startdatum) | Geben Sie Startdatum und -uhrzeit für diesen Standort ein.                                                   |
    | Effective Start End (Tatsächliches Enddatum)   | Geben Sie Enddatum und -uhrzeit für diesen Standort ein.                                                     |
    | Location Order (Standortreihenfolge)       | Geben Sie eine Zahl zum Sortieren des Standorts in die Dropdownlisten für den Standort ein.                               |
    | Alternate Site Flag (Flag für alternatives Standort)  | Für die interne Verwendung.                                                                                     |

1. Wählen Sie **Speichern und Schließen** aus. Der neu erstellte Datensatz ist in der Liste **Locations** verfügbar.

Um den Datensatz zu bearbeiten, wählen Sie ihn aus. Aktualisieren Sie die Werte wie gewünscht, und wählen Sie **Speichern und schließen** aus.

Sie können die Daten für einen Standort – z. B. **Census** (Zählung), **COVID Tracking** (Nachverfolgung von COVID-Fällen) oder **Equipment Needs** (benötigte Geräte) – anzeigen, indem Sie einen vorhandenen Standort öffnen und die jeweiligen Registerkarten auswählen. Die zugehörigen Daten werden von den Mitarbeitern an vorderster Front über die [mobile App](use.md) eingegeben.

> [!div class="mx-imgBorder"]
> ![location-related-records](media/location-related-records.png)


### <a name="departments-data"></a>Daten zu Abteilungen

Mithilfe der Entität **Departments** können Sie Abteilungsinformationen für ein Krankenhaus verwalten.

So erstellen Sie einen Datensatz

1. Melden Sie sich über die von Ihrem IT-Administrator bereitgestellte URL bei der Administrator-App (modellgesteuerte App) an.

1. Wählen Sie im linken Bereich **Departments** und dann **New** aus.

1. Geben Sie auf der Seite **New Department** (Neue Abteilung) die entsprechenden Werte an:

    > [!div class="mx-imgBorder"]
    > ![Details zu neuer Abteilung eingeben](media/enter-details-new-department.png)

    | **Feld**            | **Beschreibung**                                    |
    |----------------------|----------------------------------------------------|
    | Department Name      | Geben Sie einen Abteilungsnamen ein.                            |
    | Beschreibung          | Geben Sie eine optionale Beschreibung ein.                      |
    | Effective Start Data (Tatsächliches Startdatum) | Geben Sie Startdatum und -uhrzeit für diese Abteilung ein. |
    | Effective Start End (Tatsächliches Enddatum)   | Geben Sie Enddatum und -uhrzeit für diese Abteilung ein.   |

1. Wählen Sie **Speichern und Schließen** aus. Der neu erstellte Datensatz ist in der Liste **Departments** verfügbar.

Um den Datensatz zu bearbeiten, wählen Sie ihn aus. Aktualisieren Sie die Werte wie gewünscht, und wählen Sie **Speichern und schließen** aus.

## <a name="manage-tracking-level-for-mobile-apps"></a>Verwalten der Nachverfolgungsebene für mobile Apps

Mitarbeiter an vorderster Front können Informationen über die mobilen Apps (Canvas-Apps) anhand von *Standort* oder *Einrichtung* nachverfolgen. Folgende Nachverfolgungsebene gilt standardmäßig für jede mobile App: 

|App  |Standardnachverfolgungsebene  |
|--|--|
|COVID tracking (Nachverfolgung von COVID-Fällen)|Standort|
|Personal|Standort|
|Equipment (Geräte)|Standort|
|Bed capacity (Bettenkapazität)|Facility|
|Supplies (Verbrauchsmaterialien)|Facility|
|Staffing needs (Personalbedarf)|Facility|
|Discharge tracking (Nachverfolgung von entlassenen Patienten)|Facility|

Als Administrator können Sie die Standardnachverfolgungsebene von mobilen Apps ändern.

1. Melden Sie sich über die von Ihrem IT-Administrator bereitgestellte URL bei der Administrator-App (modellgesteuerte App) an.

1. Wählen Sie im linken Navigationsmenü den Bereich **Administration** und dann **Apps** aus. 

    > [!div class="mx-imgBorder"]
    > ![config-admin-app-records](media/admin-apps.png)

1. Wählen Sie eine der Canvas-Apps aus, um den Datensatz zu öffnen.

1. Wählen Sie im App-Datensatz im Feld **Tracking Level** (Nachverfolgungsebene) einen geeigneten Wert aus.

    > [!div class="mx-imgBorder"]
    > ![app-tracking-level](media/app-tracking-level.png)

    - Wenn für eine App der Wert **Location** (Standort) ausgewählt ist, enthalten die Datensätze, die über die mobile App erstellt werden, Informationen zum Standort und zur Einrichtung sowie weitere Daten. Darüber hinaus steht in der mobilen App ein Dropdownmenü für **Location** (Standort) zur Verfügung, sodass die Benutzer einen Standort für die Nachverfolgung von Daten auswählen können.

    - Wenn für eine App die Option **Facility** (Einrichtung) ausgewählt ist, enthalten die über die mobile App erstellten Datensätze nur Informationen zur Einrichtung sowie weitere Daten.

    - Wenn Sie im Wert **Tracking Level** (Nachverfolgungsebene) keinen Wert auswählen, wird auf die mobilen Apps die *standardmäßige* Nachverfolgungsebene angewendet, wie weiter oben erläutert.

1. Wählen Sie rechts unten **Speichern** aus, um Ihre Änderungen zu speichern.

## <a name="view-common-data-service-dashboards"></a>Anzeigen von Common Data Service-Dashboards

Die folgenden Dashboards sind in der modellgesteuerten Notfallreaktions-Admin-App für Krankenhäuser standardmäßig verfügbar:

- **Bed Management** (Bettenmanagement)

   Zeigt die Verfügbarkeit von Betten, die prozentuale Belegung und die Gesamtanzahl der Betten in den verschiedenen Einrichtungen.

- **Equipment and Supply** (Geräte und Verbrauchsmaterial)

  Zeigt in verschiedenen Einrichtungen in Betrieb befindliche kritische Geräte und verfügbare Verbrauchsmaterialen.

- **Staff Management** (Personalverwaltung)

  Zeigt die Anzahl der in verschiedenen Einrichtungen beantragten, zugewiesenen und verfügbaren Mitarbeiter.

- **COVID Patients** (COVID-Patienten)

  Zeigt die Anzahl der Patienten, die in verschiedenen Einrichtungen untersucht wurden und einen positiven Befund auf COVID-19 haben.

- **Discharges** (Entlassungen)

  Zeigt die Anzahl von Patienten, die voraussichtlich entlassen werden, und die tatsächliche Entlassungen.

Zusätzlich zu den standardmäßig verfügbaren Dashboards können Sie auch eigene Dashboards erstellen.

### <a name="manage-dashboards"></a>Dashboards verwalten

So verwalten Sie Dashboards

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an, und navigieren Sie zu Ihrer Admin-App.

2. Wählen Sie im linken Navigationsbereich in der Bereichsauswahl **Dashboards** aus:

    > [!div class="mx-imgBorder"]
    > ![Dashboards auswählen](media/select-dashboards.png)

3. Wählen Sie im linken Navigationsbereich einen Dashboardnamen aus, um die Diagramme anzuzeigen:

    > [!div class="mx-imgBorder"]
    > ![Diagramme anzeigen](media/view-charts.png)

    > [!NOTE]
    > Wenn Sie die Daten unten auf dem Bildschirm filtern, werden die Diagramme oben automatisch mit gefilterten Werten aktualisiert.

4. Wählen Sie die Option **Erweitern** aus, um ein Diagramm im Vollbildmodus anzuzeigen:

    > [!div class="mx-imgBorder"]
    > ![„Erweitern“ auswählen](media/select-expand.png)

### <a name="additional-analysis"></a>Zusätzliche Analyse

- **Drilldown**: Sie können einen Diagrammbereich auswählen, um weitere Attribute (Felder) für eine Entität genauer zu untersuchen:

    > [!div class="mx-imgBorder"]
    > ![Drilldown für Diagrammbereich auswählen](media/select-chart-area-drill-down.png)

- **Aktualisieren:** Sie können die Dashboards aktualisieren und dadurch auf den neuesten Stand bringen. Sie können entweder alle Diagramme auf einem bestimmten Dashboard mit **Alle aktualisieren** oder ein ausgewähltes Diagramm mit **Aktualisieren** aktualisieren:

    > [!div class="mx-imgBorder"]
    > ![Dashboards aktualisieren](media/refresh-dashboards.png)

- **Datensätze anzeigen**: Wählen Sie **Weitere Befehle** ( **...** ) und dann **Datensätze anzeigen** aus, um alle mit einem bestimmten Diagramm verknüpften Datensätze anzuzeigen:

    > [!div class="mx-imgBorder"]
    > ![„Weitere Befehle“ auswählen](media/select-more-commands.png)

    > [!NOTE] 
    > Wenn Sie **Datensätze anzeigen** auswählen, sehen Sie eine zwischen dem Diagramm und den Datensätzen aufgeteilte Ansicht der Entität. Jede Änderung der Filter für Datensätze auf der rechten Seite wird durch automatische Aktualisierungen des Diagramms auf der linken Seite des Bildschirms widergespiegelt.

Weitere Informationen zum Bearbeiten eines bestehenden Dashboards und Aktualisieren der Eigenschaften von Diagrammen finden Sie unter [Bearbeiten eines bestehenden Dashboards](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-dashboards#edit-an-existing-dashboard).

### <a name="create-new-dashboards"></a>Erstellen neuer Dashboards

Sie können auch Ihre eigenen Dashboards erstellen und an Ihre Anforderungen anpassen. Um ein neues Dashboard zu erstellen, wählen Sie **Neu** und danach **Dynamics 365-Dashboard** aus:

> [!div class="mx-imgBorder"]
> ![Neues Dynamics-Dashboard auswählen](media/select-new-dynamics-dashboard.png)

Weitere Informationen zum Erstellen eines neuen Dashboards finden Sie unter [Erstellen eines neuen Dashboards](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-dashboards#create-a-new-dashboard).

## <a name="view-power-bi-dashboard"></a>Anzeigen des Power BI-Dashboards

Zeigen Sie Power BI-Dashboards an, um Erkenntnisse zu gewinnen und Entscheidungen zu treffen.

### <a name="prerequisites"></a>Voraussetzungen

- Power BI Premium-Kapazität- oder Power BI Pro-Lizenzen, die Benutzern zugewiesen sind, die auf den Bericht zugreifen. 

- Ihr IT-Administrator muss den Power BI-Bericht veröffentlicht und Ihnen Berechtigungen für den Zugriff darauf gewährt haben. Weitere Informationen: [Veröffentlichen des Power BI-Dashboards](deploy-configure.md#publish-the-power-bi-dashboard) 

### <a name="view-the-dashboard"></a>Anzeigen des Dashboards

Melden Sie sich bei [Power BI](https://apps.powerbi.com) an, um auf das Power BI-Dashboard zuzugreifen und es anzuzeigen.

> [!div class="mx-imgBorder"]
> ![Anzeigen des Power BI-Dashboards](media/view-powerbi-dashboard.png)

Sie können die Filter auf der rechten Seite verwenden, um Daten nach Standorten, Einrichtungen, Regionen und Krankenhaussystemen in Bezug auf COVID zu filtern.

#### <a name="system-at-a-glance-page"></a>Die Seite „Systems at a glance“ (Systeme auf einen Blick) 

Die Seite **Systems at a glance** (Systeme auf einen Blick) ist die Standardseite bzw. Seite der obersten Ebene, die einen allgemeinen Überblick bietet.  

Auf der Seite wird eine Übersicht der folgenden Punkte gezeigt: 

- **COVID Patient Information** (Informationen zu COVID-Patienten): Zeigt die Gesamtanzahl von COVID-Patienten, die Anzahl von positiv auf COVID-19 getesteten Patienten und die Anzahl von Verdachtsfällen (Patients Under Investigation, PUI) an.

- **Bed Management** (Bettenmanagement): Zeigt die Verfügbarkeit von Betten, die prozentuale Belegung, die Anzahl der Notbetten und die Gesamtanzahl der Betten. Sie können auch das nachstehende Raster verwenden, um die Zahlen nach Akut-Einheiten anzuzeigen.

- **Staffing Information** (Informationen zum Personal): Zeigt die Anzahl der Patienten auf der Intensivstation, die zugewiesenen Pflegekräfte und das Verhältnis von Pflegekraft zu Patienten.  

- **Patient Discharge Information** (Informationen zur Entlassung von Patienten): Zeigt die Gesamtanzahl der Patienten mit Langzeitaufenthalt, die Anzahl der Patienten, die voraussichtlich entlassen werden, und die tatsächlichen Entlassungen.

- **Equipment Information** (Informationen zu Geräten): Zeigt die Gesamtanzahl der Beatmungsgeräte, die Anzahl der verwendeten Beatmungsgeräte und die verfügbaren Beatmungsgeräte. 

- **Supplies Information** (Informationen zu Verbrauchsmaterialien): Zeigt die Anzahl der verfügbaren Verbrauchsmaterialien in Tagen an.

> [!NOTE]
> - Wenn Sie in einem der Übersichtsbereiche einen Titel auswählen, gelangen Sie zur entsprechenden Detailseite für den Bereich. 
> - Sie können auch andere Aktionen auf Berichte anwenden, z. B. Daten filtern und sortieren, den Bericht in das PDF- und PowerPoint-Format exportieren, ein Spotlight hinzufügen usw. Ausführliche Informationen zu Berichtsfeatures in Power BI finden Sie unter [Berichte in Power BI](https://docs.microsoft.com/power-bi/consumer/end-user-reports).
> - Die zuletzt verwendeten oder aktualisierten Spalten in einigen dieser Berichte zeigen das Datum und die Uhrzeit, zu der die Daten zuletzt aktualisiert wurden. Es ist auch einfach, die Aktualität zu erkennen, indem Sie sich die Farbe der Datums- und Uhrzeitangaben in diesen Spalten ansehen:
>    - Schwarz: Die Daten werden vor weniger als 20 Stunden aktualisiert.
>    - Grau: Die Daten wurden vor 20-24 Stunden aktualisiert.
>    - Rot: Die Daten werden vor mehr als 24 Stunden aktualisiert. 
 
#### <a name="system-view-page"></a>Seite „System View“ (Systemansicht)

Auf der Seite **System View** (Systemansicht) werden Diagramme mit den folgenden Informationen für ein Krankenhaussystem angezeigt:
- Verwendete Beatmungsgeräte und verfügbare Beatmungsgeräte
- Verfügbarkeit von Betten und Akutpflegebetten und Belegungsprozentsatz
- Angefordertes Personal insgesamt, Anzahl der Patienten (Zählung), Verhältnis Pflegepersonal zu Patienten
- Vorhandene Verbrauchsmaterialien über einen bestimmten Zeitraum

> [!div class="mx-imgBorder"]
> ![System View](media/report-system-view.png) (Systemansicht)

#### <a name="location-details-page"></a>Seite „Location Details“ (Standortdetails) 

Wählen Sie auf der Seite **System at a glance** (System auf einen Blick) in der rechten oberen Ecke das Symbol **i** aus. Auf der Seite **Location Details** (Standortdetails) werden Daten nach Standort wie Gesamtanzahl der Betten, verfügbaren Betten, Notbetten, COVID-Patienten usw. angezeigt. 

> [!div class="mx-imgBorder"]
> ![Location Details](media/report-location-details.png) (Standortdetails) 

#### <a name="covid-patients-page"></a>Seite „COVID patients“ (COVID-Patienten) 

Diese Seite bietet detaillierte Informationen zu den COVID-Patienten, wie z. B. Patienten an den einzelnen Standorten, Patiententrend im Zeitverlauf mit Höchst- und Tiefstwerten bei der Anzahl der Verdachtsfälle und der Anzahl der positiv getesteten Patienten. Hier können Sie sich ein Bild davon machen, wo sich die Patienten innerhalb des Krankenhauses befinden.

> [!div class="mx-imgBorder"]
> ![COVID Patient Details](media/report-covid-details.png) (Details zu COVID-Patienten)

#### <a name="bed-management-page"></a>Seite „Bed Management“ (Bettenmanagement) 

Diese Seite bietet detaillierte Informationen nach Standort, wie z. B. insgesamt verfügbare Betten, verfügbare Akutbetten und prozentuale Belegung.

> [!div class="mx-imgBorder"]
> ![Bed Management](media/report-bed-details.png) (Bettenmanagement)

#### <a name="staffing-details-page"></a>Seite „Staffing Details“ (Details zum Personal)  

Diese Seite bietet Details zum Personal nach Standort, zur Anzahl der zugeteilten Pflegekräfte, zur Gesamtanzahl der Patienten und zur Anzahl der COVID-Patienten. Außerdem wird das Verhältnis von Pflegepersonal zu Patienten und von Intensivpflegepersonal zu Patienten über einen bestimmten Zeitraum gezeigt.

> [!div class="mx-imgBorder"]
> ![Staff Details](media/report-staff-details.png) (Details zum Personal)

#### <a name="equipment-page"></a>Seite „Equipment“ (Geräte) 

Diese Seite enthält Einzelheiten zu den Geräten nach Standort, die Gesamtanzahl der genutzten Beatmungsgeräte, kombiniert mit der Anzahl der COVID-Patienten, und die Anzahl anderer Gegenstände, wie z. B. Gurte, Ladegeräte und Hauben, die derzeit in Gebrauch sind.

> [!div class="mx-imgBorder"]
> ![Equipment Details](media/report-equipment-details.png) (Details zu Geräten)

#### <a name="discharges-page"></a>Seite „Discharges“ (Entlassungen) 

Diese Seite liefert Einzelheiten zu Langzeitpatienten, Entlassungshindernissen über einen bestimmten Zeitraum und der Varianz in Bezug auf tatsächliche und erwartete Entlassungen.

> [!div class="mx-imgBorder"]
> ![Equipment Details](media/report-discharge-details.png) (Details zu Geräten)

#### <a name="supplies-page"></a>Seite „Supplies“ (Verbrauchsmaterialien) 

Diese Seite bietet Details zu Verbrauchsmaterialien nach Standort. Sie zeigt auch ein Diagramm zu vorhandenen Materialien, aufgeschlüsselt nach Material und Einrichtung, sowie zu vorhandenen Materialien über einen bestimmten Zeitraum an.

> [!div class="mx-imgBorder"]
> ![Equipment Details](media/report-supplies.png) (Details zu Geräten)

## <a name="view-and-manage-app-feedback"></a>Anzeigen und Verwalten von Feedback zur App

Das gesamte Feedback, das von Mitarbeitern an vorderster Front mithilfe von Canvas-Apps auf ihren mobilen Geräten gegeben wird, wird in der Entität **App-Feedback** gespeichert. Administratoren können es im linken Navigationsbereich der Admin-App im Bereich **Administration** einsehen und verwalten.

So wird Feedback zur App angezeigt und verwaltet

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an, und navigieren Sie zu Ihrer Admin-App.

2. Wählen Sie im linken Navigationsbereich in der Bereichsauswahl **Administration** aus:

3. Wählen Sie **App-Feedback** aus, um eine Liste des von Benutzern übermittelten Feedbacks zur App anzuzeigen. Sie können auf einen Datensatz klicken, um Details anzuzeigen und als überprüft zu markieren.  

    > [!div class="mx-imgBorder"]
    > ![„App-Feedback“ auswählen](media/select-app-feedback.png)

## <a name="issues-and-feedback"></a>Issues und Feedback

- Wenn Sie ein Issue mit der Beispiel-App für die Notfallreaktion für Krankenhäuser melden möchten, besuchen Sie <https://aka.ms/emergency-response-issues>.

- Wenn Sie Feedback zur Beispiel-App für die Notfallreaktion für Krankenhäuser geben möchten, besuchen Sie <https://aka.ms/emergency-response-feedback>.

## <a name="next-step"></a>Nächster Schritt

[Verwenden der mobilen Notfallreaktions-App für Krankenhäuser](use.md)
