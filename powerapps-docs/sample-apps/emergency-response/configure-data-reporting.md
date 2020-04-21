---
title: Masterdaten konfigurieren und Dashboards in der Hospital Emergency Response App anzeigen | Microsoft Docs
description: Bietet detaillierte Anweisungen für IT-Administratoren in Krankenhäusern, um die Beispiel-App für ihre Organisation bereitzustellen und zu konfigurieren.
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
ms.locfileid: "3265403"
---
# <a name="configure-master-data-and-view-dashboards"></a>Masterdaten konfigurieren und Dashboards anzeigen

Dieser Artikel enthält Informationen dazu, wie Sie mit der Admin-App (modellgesteuerte App) Masterdaten für Ihre Lösung hinzufügen und verwalten und das Power BI-Dashboard zum Anzeigen der wichtigsten Erkenntnisse und Metriken verwenden können.

Diese Aufgaben werden normalerweise von Geschäftsadministratoren in Ihrer Organisation ausgeführt.

## <a name="configure-and-manage-master-data-for-your-organization"></a>Stammdaten für Ihre Organisation konfigurieren und verwalten

Verwenden Sie die Administrator-App, um Stammdaten für Ihre Organisation zu erstellen und zu verwalten. Diese Daten sind erforderlich, damit die Hospital Emergency Response-App funktioniert.

> [!IMPORTANT]
> - Stellen Sie sicher, dass Ihr IT-Administrator die Lösung in Ihrem Unternehmen bereitgestellt und Geschäftsadministratoren die entsprechenden Berechtigungen zur Verwendung der Administrator-App erteilt hat. Mehr Informationen: [Die App für Notfallmaßnahmen im Krankenhaus bereitstellen](deploy-configure.md#deploy-the-hospital-emergency-response-app)
> 
> - Sie können Ihre Daten auch aus den im Bereitstellungspaket verfügbaren Datendateien importieren. Weitere Informationen: [Schritt 4: Laden der Konfigurations- und Stammdaten für Ihre Organisation](deploy-configure.md#step-4-load-configuration-and-master-data-for-your-organization)

Sie müssen Stammdaten zu diesen Entitäten in der folgenden Reihenfolge hinzufügen:

1. [Systeme](#systems-data)

1. [Regionen](#regions-data)

1. [Einrichtungen](#facilities-data)

1. [Standorte](#locations-data)

1. [Abteilungen](#departments-data)

Die Stammdaten werden vom Bereich **Standorte** in der linken Navigation in der Administrator-App verwaltet:

> [!div class="mx-imgBorder"]
> ![Standortbereich](media/locations-area.png)

Die Entitäten im Bereich **Hierarchie** werden in der Reihenfolge aufgelistet, in der Sie Daten auffüllen sollten.

> [!NOTE]
> Pflegekategoriendaten werden während der Bereitstellung der Lösung importiert. Weitere Informationen: [Schritt 4: Laden der Konfigurations- und Stammdaten für Ihre Organisation](deploy-configure.md#step-4-load-configuration-and-master-data-for-your-organization)

### <a name="systems-data"></a>Systemdaten

Mit der Entität **Systeme** können Sie Einträge für Krankenhaussysteme erstellen und verwalten. Auf diese Weise können Sie mehrere Krankenhaussysteme innerhalb derselben Organisation verwalten.

So erstellen Sie einen Datensatz:

1. Melden Sie sich bei der Administrator-App (modellgesteuerte App) unter der von Ihrem IT-Administrator angegebenen URL an.

1. Wählen Sie im linken Bereich **Systeme** und dann **Neu** aus:  
    > [!div class="mx-imgBorder"]
    > ![Neue Systeme auswählen](media/select-systems-new.png)

1. Geben Sie auf der Seite **Neues System** die entsprechenden Werte an:  
   > [!div class="mx-imgBorder"]
   > ![Details für neues System eingeben](media/enter-details-new-system.png)

   | **Feld**            | **Beschreibung**                                    |
   |----------------------|----------------------------------------------------|
   | Systemname          | Geben Sie einen Namen für das Krankenhaus ein.                     |
   | Beschreibung          | Geben Sie eine optionale Beschreibung ein.                      |
   | Effektives Startdatum | Geben Sie Startdatum und -uhrzeit für dieses Krankenhaussystem ein. |
   | Effektives Enddatum   | Geben Sie Enddatum und -uhrzeit für dieses Krankenhaussystem ein.   |

1. Klicken Sie auf **Speichern und Schließen**. Der neu erstellte Datensatz ist in der Liste **Systeme** verfügbar.

Um den Datensatz zu bearbeiten, wählen Sie den Datensatz aus, aktualisieren Sie die Werte nach Bedarf und wählen Sie **Speichern und Schließen** aus.

### <a name="regions-data"></a>Regionendaten

Mit der Entität **Regionen** können Sie die geografischen Regionen für Ihre Krankenhaussysteme verwalten.

So erstellen Sie einen Datensatz:

1. Melden Sie sich bei der Administrator-App (modellgesteuerte App) unter der von Ihrem IT-Administrator angegebenen URL an.

1. Wählen Sie im linken Bereich **Regionen** und dann **Neu** aus.

1. Geben Sie auf der Seite **Neue Region** die entsprechenden Werte an:  

    > [!div class="mx-imgBorder"]
    > ![Details für neue Region eingeben](media/enter-details-new-region.png)

    | **Feld**            | **Beschreibung**                                                                                          |
    |----------------------|----------------------------------------------------------------------------------------------------------|
    | System               | Wählen Sie ein Krankenhaussystem aus. Diese Liste wird basierend auf den **System**daten, die Sie zuvor erstellt haben, ausgefüllt. |
    | Regionenname          | Geben Sie den Regionennamen ein. Zum Beispiel Berlin.                                                              |
    | Beschreibung          | Geben Sie eine optionale Beschreibung ein.                                                                            |
    | Effektives Startdatum | Geben Sie Startdatum und -uhrzeit für diese Region ein.                                                       |
    | Effektives Enddatum   | Geben Sie Enddatum und -uhrzeit für diese Region ein.                                                         |

1. Klicken Sie auf **Speichern und Schließen**. Der neu erstellte Datensatz ist in der Liste **Regionen** verfügbar.

Um den Datensatz zu bearbeiten, wählen Sie den Datensatz aus, aktualisieren Sie die Werte nach Bedarf und wählen Sie **Speichern und Schließen** aus.

### <a name="facilities-data"></a>Einrichtungsdaten

Mit der Entität **Einrichtungen** können Sie die Krankenhausstandorte in jeder Region verwalten. Zum Beispiel die Einrichtungen **Potsdam** und **Oranienburg** innerhalb der Region **Berlin**.

So erstellen Sie einen Datensatz:

1. Melden Sie sich bei der Administrator-App (modellgesteuerte App) unter der von Ihrem IT-Administrator angegebenen URL an.

1. Wählen Sie im linken Bereich die Option **Einrichtungen** und dann **Neu** aus.

1. Geben Sie auf der Seite **Neue Einrichtung** die entsprechenden Werte an: 

    > [!div class="mx-imgBorder"] 
    > ![Details für neue Einrichtung eingeben](media/enter-details-new-facility.png)

    | **Feld**            | **Beschreibung**                                                                                 |
    |----------------------|-------------------------------------------------------------------------------------------------|
    | Region               | Wählen Sie eine Region aus, der diese Einrichtung zugeordnet ist. Diese Liste wird basierend auf den **Regionen**daten, die Sie zuvor erstellt haben, ausgefüllt. |
    | Einrichtungsname        | Geben Sie den Einrichtungsnamen ein. Zum Beispiel Oranienburg.                                                  |
    | Beatmungsgeräte insgesamt          | Geben Sie die Gesamtzahl der in der Einrichtung verfügbaren Beatmungsgeräte ein.                                  |
    | Beschreibung          | Geben Sie eine optionale Beschreibung ein.                                                                   |
    | Effektives Startdatum | Geben Sie Startdatum und -uhrzeit für diese Einrichtung ein.                                                     |
    | Effektives Enddatum   | Geben Sie Enddatum und -uhrzeit für diese Einrichtung ein.                                                       |
    |Betten insgesamt      | Automatisch berechnet.|
    |Besetzt gesamt      | Automatisch berechnet.|
    |Einrichtungsadresse      | Geben Sie Straße, Stadt, Landkreis, Bundesland, Postleitzahl, Breitengrad und Längengrad für die Einrichtung ein.|

    Geben Sie bei Bedarf die Adresse der Einrichtung ein.

1. Klicken Sie auf **Speichern und Schließen**. Der neu erstellte Datensatz ist in der Liste **Einrichtungen** verfügbar.

Um den Datensatz zu bearbeiten, wählen Sie den Datensatz aus, aktualisieren Sie die Werte nach Bedarf und wählen Sie **Speichern und Schließen** aus.

### <a name="locations-data"></a>Standortdaten

Mit der Entität **Standorte** können Sie bestimmte Standorte in jeder Krankenhauseinrichtung verwalten.

> [!NOTE]
> Stellen Sie vor dem Erstellen eines **Standorte**-Datensatzes sicher, dass Sie die Pflegekategoriedaten mit der Datei **00 – Acuities Import.xlsx** wie weiter oben erläutert in [Schritt 4: Laden der Konfigurations- und Stammdaten für Ihre Organisation](deploy-configure.md#step-4-load-configuration-and-master-data-for-your-organization) importiert haben. Dies liegt daran, dass Pflegekategoriedaten zur Erstellung eines **Standort**-Datensatzes erforderlich sind.

So erstellen Sie einen Datensatz:

1. Melden Sie sich bei der Administrator-App (modellgesteuerte App) unter der von Ihrem IT-Administrator angegebenen URL an.

1. Wählen Sie im linken Bereich die Option **Standorte** und dann **Neu** aus.

1. Geben Sie auf der Seite **Neuen Standort** die entsprechenden Werte an:  
 
    > [!div class="mx-imgBorder"]
    > ![Details für neuen Standort eingeben](media/enter-details-new-location.png)

    | **Feld**            | **Beschreibung**                                                                                      |
    |----------------------|------------------------------------------------------------------------------------------------------|
    | Standortname        | Geben Sie den Namen des Standortes ein.                                                                       |
    | Einrichtung             | Wählen Sie eine Einrichtung aus. Diese Liste wird basierend auf den **Einrichtungs**daten, die Sie zuvor erstellt haben, ausgefüllt. |
    | Etage                | Geben Sie die Etagedaten für die Einrichtung ein.                                                         |
    | Einheit                 | Geben Sie die Einheitsdaten für die Einrichtung ein.                                                           |
    | Belegungsprozentsatz | Automatisch berechnet basierend auf der letzten Volkszählung und den Gesamtbettenwerten.                                         |
    | Pflegekategorie      | Wählen Sie den Pflegekategoriedatensatz aus, der diesem Standort zugewiesen ist.                                                                                                     |
    | COVID-Standort      | Wählen Sie aus, ob dieser Standort zur Behandlung von COVID-Patienten genutzt wird (**Ja** oder **Nein**).                                                                                                      |
    | Betten insgesamt           | Geben Sie die Gesamtzahl der Betten in der Einrichtung ein.                                                       |
    | Schwallbetten           | Geben Sie die Anzahl der Schwallbetten in der Einrichtung ein. Schwallbetten sind solche, die über die lizenzierte Bettenkapazität hinaus besetzt werden können, wenn Patienten aufgenommen werden müssen.                                                      |
    | Blockierte Betten         | Geben Sie die Anzahl blockierter Betten in der Einrichtung ein.                                                     |
    | Letzte Zählung          | Ausgefüllt basierend auf dem zuletzt erstellten Zählungsdatensatz.                                             |
    | Effektives Startdatum | Geben Sie Startdatum und -uhrzeit für diesen Standort ein.                                                   |
    | Effektives Enddatum   | Geben Sie Enddatum und -uhrzeit für diesen Standort ein.                                                     |
    | Standortreihenfolge       | Geben Sie eine Zahl ein, die den Standort in den Dropdown-Standortlisten sortiert.                               |
    | Alternatives Site-Kennzeichen  | Nur zur internen Verwendung.                                                                                     |

1. Klicken Sie auf **Speichern und Schließen**. Der neu erstellte Datensatz ist in der Liste **Standorte** verfügbar.

Um den Datensatz zu bearbeiten, wählen Sie den Datensatz aus, aktualisieren Sie die Werte nach Bedarf und wählen Sie **Speichern und Schließen** aus.

Sie können die zugehörigen Daten für einen Standort anzeigen, z. B. **Erhebung**, **COVID-Verfolgung**, **Gerätebedarf**, indem Sie einen vorhandenen Standortdatensatz öffnen und die entsprechenden Registerkarten auswählen. Die zugehörigen Daten werden vom Frontline-Personal über [Mobile Apps](use.md) eingegeben.

> [!div class="mx-imgBorder"]
> ![Mit Standort verknüpfte Datensätze](media/location-related-records.png)


### <a name="departments-data"></a>Abteilungsdaten

Mit der Entität **Abteilungen** können Sie Abteilungsdaten für ein Krankenhaus verwalten.

So erstellen Sie einen Datensatz:

1. Melden Sie sich bei der Administrator-App (modellgesteuerte App) unter der von Ihrem IT-Administrator angegebenen URL an.

1. Wählen Sie im linken Bereich die Option **Abteilungen** und dann **Neu** aus.

1. Geben Sie auf der Seite **Neue Abteilung** die entsprechenden Werte an:

    > [!div class="mx-imgBorder"]
    > ![Details für neue Abteilung eingeben](media/enter-details-new-department.png)

    | **Feld**            | **Beschreibung**                                    |
    |----------------------|----------------------------------------------------|
    | Abteilungsname      | Geben Sie einen Abteilungsnamen ein.                            |
    | Beschreibung          | Geben Sie eine optionale Beschreibung ein.                      |
    | Effektives Startdatum | Geben Sie Startdatum und -uhrzeit für diese Abteilung ein. |
    | Effektives Enddatum   | Geben Sie Enddatum und -uhrzeit für diese Abteilung ein.   |

1. Klicken Sie auf **Speichern und Schließen**. Der neu erstellte Datensatz ist in der Liste **Abteilungen** verfügbar.

Um den Datensatz zu bearbeiten, wählen Sie den Datensatz aus, aktualisieren Sie die Werte nach Bedarf und wählen Sie **Speichern und Schließen** aus.

## <a name="manage-tracking-level-for-mobile-apps"></a>Verwalten der Nachverfolgungsebene für mobile Apps

Mitarbeiter an vorderster Front können Informationen mithilfe der mobilen Apps (Canvas-Apps) nach *Standort* oder *Einrichtung* nachverfolgen. Hier ist die Standard-Nachverfolgungsebene für jede mobile App: 

|App  |Standard-Nachverfolgungsebene  |
|--|--|
|COVID-Nachverfolgung|Speicherort|
|Personal|Speicherort|
|Arbeitsgerät|Speicherort|
|Bettenkapazität|Raum|
|Bedarf|Raum|
|Personalbedarf|Raum|
|Entlassungsverfolgung|Raum|

Als Administrator können Sie die Standard-Nachverfolgungsebene für mobile Apps ändern.

1. Melden Sie sich bei der Administrator-App (modellgesteuerte App) unter der von Ihrem IT-Administrator angegebenen URL an.

1. Wählen Sie in der linke Navigation den Bereich **Verwaltung** und dann **Apps** aus. 

    > [!div class="mx-imgBorder"]
    > ![config-admin-app-records](media/admin-apps.png)

1. Wählen Sie eine der Canvas-Apps aus, um den Datensatz zu öffnen.

1. Wählen Sie im App-Datensatz einen geeigneten Wert im Feld **Nachverfolgungsebene** aus.

    > [!div class="mx-imgBorder"]
    > ![app-tracking-level](media/app-tracking-level.png)

    - Wenn **Standort** für eine App ausgewählt ist, enthalten mit der mobilen App erstellte Datensätze neben anderen Daten auch Standort- und Einrichtungsinformationen. In der mobilen App steht zusätzlich ein Dropdown-Menü **Standort** zur Verfügung, in dem Benutzer einen Ort zum Verfolgen der Daten auswählen können.

    - Wenn **Einrichtung** für eine App ausgewählt ist, enthalten mit der mobilen App erstellte Datensätze neben anderen Daten nur die Einrichtungsinformationen.

    - Wenn Sie keinen Wert für das Feld **Nachverfolgungsebene** auswählen, wird die zuvor erläuterte Nachverfolgungsebene *Standard* auf die mobilen Apps angewendet.

1. Wählen Sie **Speichern** in der unteren rechten Ecke aus, um Ihre Änderungen zu speichern.

## <a name="view-common-data-service-dashboards"></a>Common Data Service-Dashboards anzeigen

Die folgenden Dashboards sind standardmäßig in der (modellgesteuerten) Hospital Emergency Response-Administrator-App verfügbar:

- **Bettenverwaltung**

   Zeigt die Verfügbarkeit von Betten, den Belegungsprozentsatz und die Gesamtzahl der Betten in verschiedenen Einrichtungen an.

- **Arbeitsgeräte und Bedarf**

  Zeigt kritische Arbeitsgeräte in Gebrauch und verfügbaren Bedarf in verschiedenen Einrichtungen an.

- **Personalverwaltung**

  Zeigt die Anzahl der angeforderten, zugewiesenen und verfügbaren Mitarbeiter in verschiedenen Einrichtungen an.

- **COVID-Patienten**

  Zeigt die Anzahl der untersuchten und mit COVID-19 positiv getesteten Patienten in verschiedenen Einrichtungen an.

- **Entlassungen**

  Zeigt die Anzahl der Patienten, deren Entlassung erwartet wird, und tatsächlich entlassener Patienten an.

Sie können zusätzlich zu den standardmäßig verfügbaren Dashboards auch eigene Dashboards erstellen.

### <a name="manage-dashboards"></a>Verwalten von Dashboards

So verwalten Sie Dashboards:

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an und navigieren Sie zu Ihrer Administrator-App.

2. Wählen Sie im linken Navigationsbereich die Option **Dashboards** aus der Bereichsauswahl aus:

    > [!div class="mx-imgBorder"]
    > ![Dashboards auswählen](media/select-dashboards.png)

3. Wählen Sie in der linken Navigation einen Dashboard-Namen aus, um die Diagramme anzuzeigen:

    > [!div class="mx-imgBorder"]
    > ![Diagramme anzeigen](media/view-charts.png)

    > [!NOTE]
    > Sie können Daten am unteren Bildschirmrand filtern und die Diagramme oben werden automatisch mit gefilterten Werten aktualisiert.

4. Wählen Sie die Option **Erweitern** aus, um ein Diagramm im Vollbildmodus anzuzeigen:

    > [!div class="mx-imgBorder"]
    > ![Auswahl erweitern](media/select-expand.png)

### <a name="additional-analysis"></a>Zusätzliche Analyse

- **Drilldown ausführen**: Sie können den Diagrammbereich auswählen, um einen weiteren Drilldown mit zusätzlichen Attributen (Feldern) für eine Entität auszuführen:

    > [!div class="mx-imgBorder"]
    > ![Diagrammbereich auswählen und Drilldown ausführen](media/select-chart-area-drill-down.png)

- **Aktualisieren**: Sie können die Dashboards aktualisieren, um aktualisierte Daten wiederzugeben. Sie können entweder alle Diagramme in einem bestimmten Dashboard mit der Option **Alle aktualisieren** oder ein ausgewähltes Diagramm mit der Option **Aktualisieren** aktualisieren:

    > [!div class="mx-imgBorder"]
    > ![Dashboards aktualisieren](media/refresh-dashboards.png)

- **Datensätze anzeigen**: Wählen Sie **Weitere Befehle** (**…**) und dann **Datensätze anzeigen** aus, um alle Datensätze, die einem bestimmten Diagramm zugeordnet sind, anzuzeigen:

    > [!div class="mx-imgBorder"]
    > ![Weitere Befehle auswählen](media/select-more-commands.png)

    > [!NOTE] 
    > Wenn Sie die Option **Datensätze anzeigen** auswählen, sehen Sie die Ansicht der Entität, die zwischen Diagramm und Datensätzen aufgeteilt ist. Jede Änderung an Filtern für Datensätze auf der rechten Seite wird durch automatische Aktualisierungen des Diagramms auf der linken Seite des Bildschirms angezeigt.

Weitere Informationen zum Bearbeiten eines vorhandenen Dashboards und zum Aktualisieren der Eigenschaften von Diagrammen finden Sie unter [Bearbeiten eines vorhandenen Dashboards](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-dashboards#edit-an-existing-dashboard).

### <a name="create-new-dashboards"></a>Erstellen neuer Dashboards

Sie können auch Ihre eigenen Dashboards erstellen und an Ihre Bedürfnisse anpassen. Wählen Sie zum Erstellen eines neuen Dashboards die Option **Neu** und dann **Dynamics 365-Dashboard** aus:

> [!div class="mx-imgBorder"]
> ![Neues Dynamics-Dashboard auswählen](media/select-new-dynamics-dashboard.png)

Weitere Informationen zum Erstellen eines neuen Dashboards finden Sie unter [Erstellen eines neuen Dashboards](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-dashboards#create-a-new-dashboard).

## <a name="view-power-bi-dashboard"></a>Power BI-Dashboard anzeigen

Zeigen Sie die Power BI-Dashboards für Einblicke und Entscheidungsfindung an.

### <a name="prerequisites"></a>Voraussetzungen

- Power BI-Premium-Kapazität oder Power BI-Pro-Lizenzen für Benutzer, die auf den Bericht zugreifen. 

- Ihr IT-Administrator muss den Power BI-Bericht veröffentlicht haben und Ihnen die Berechtigung zum Zugriff erteilt haben. Weitere Information: [Power BI-Dashboard veröffentlichen](deploy-configure.md#publish-the-power-bi-dashboard) 

### <a name="view-the-dashboard"></a>Dashboard anzeigen

Melden Sie sich bei [Power BI](https://apps.powerbi.com) an, um das Power BI-Dashboard anzuzeigen und darauf zuzugreifen.

> [!div class="mx-imgBorder"]
> ![Power BI-Dashboard anzeigen](media/view-powerbi-dashboard.png)

Mit den Filtern auf der rechten Seite können Sie Daten nach COVID-Standorten, Einrichtungen, Regionen und Krankenhaussystemen filtern.

#### <a name="system-at-a-glance-page"></a>Systemüberblickseite 

Die **Systemüberblickseite** ist die Standardseite oder die Seite der obersten Ebene, die eine Gesamtansicht bietet.  

Auf der Seite wird eine zusammengefasste Ansicht der folgenden Elemente angezeigt: 

- **COVID-Patienteninformationen**: Zeigt die Gesamtzahl der COVID-Patienten, die Anzahl der mit COVID-19 als positiv befundenen Patienten und die Anzahl der untersuchten Patienten (PUI) an.

- **Bettenverwaltung**: Zeigt die Verfügbarkeit von Betten, den Belegungsprozentsatz, die Anzahl der Schwallbetten und die Gesamtzahl der Betten an. Sie können auch das unten stehende Raster verwenden, um die Zahlen nach akuten Einheiten anzuzeigen.

- **Personalinformationen**: Zeigt die Anzahl der Patienten auf der Intensivstation, die zugewiesenen Krankenschwestern und das Verhältnis von Krankenschwestern zu Patienten an.  

- **Informationen zur Patientenentlassung**: Zeigt die Gesamtanzahl der Patienten mit längerem Aufenthalt, die Anzahl der Patienten, deren Entlassung erwartet wird, und die tatsächliche Entlassung an.

- **Geräteinformationen**: Zeigt die Gesamtzahl der Beatmungsgeräte, die Anzahl der verwendeten Beatmungsgeräte und die verfügbaren Beatmungsgeräte an. 

- **Versorgungsinformationen**: Zeigt die Anzahl der verfügbaren Vorräte pro Tag an.

> [!NOTE]
> - Durch Auswahl des Titels in einem der zusammengefassten Bereiche gelangen Sie zur entsprechenden Detailseite für den Bereich. 
> - Sie können auch andere Aktionen für Berichte ausführen, z. B. Daten filtern und sortieren, den Bericht in PDF und PowerPoint exportieren, einen Spotlight hinzufügen usw. Ausführliche Informationen zu Berichtsfunktionen in Power BI finden Sie unter [Berichte in Power BI](https://docs.microsoft.com/power-bi/consumer/end-user-reports).
> - Die letzten oder zuletzt aktualisierten Spalten in einigen dieser Berichte zeigen Datum und Uhrzeit der letzten Aktualisierung der Daten an. Es ist auch einfach, die Aktualität zu identifizieren, indem Sie die Farbe der Datums- und Uhrzeitwerte in diesen Spalten ansehen:
>    - Schwarz: Daten wurden vor weniger als 20 Stunden aktualisiert
>    - Grau: Daten wurden vor 20 bis 24 Stunden aktualisiert
>    - Rot: Daten wurden vor mehr als 24 Stunden aktualisiert 
 
#### <a name="system-view-page"></a>Systemansichtsseite

Auf der **Systemansichtsseite** werden Diagramme mit den folgenden Daten für ein Krankenhaussystem angezeigt:
- Beatmungsgeräte in Gebrauch und Beatmungsgeräte verfügbar
- Verfügbarkeit von Betten und Akutbetten und Belegungsprozentsatz
- Gesamtzahl der angeforderten Mitarbeiter, Anzahl der Patienten (Erhebung) und Verhältnis von Krankenschwester zu Patient
- Verfügbare Vorräte über einen bestimmten Zeitraum

> [!div class="mx-imgBorder"]
> ![Systemansicht](media/report-system-view.png)

#### <a name="location-details-page"></a>Standortdetailseite 

Wählen Sie auf der Seite **System auf einen Blick** in der obenren rechten Ecke **i** aus. Auf der Seite **Standortdetails** werden Daten nach Standort angezeigt, z. B. Gesamtzahl der Betten, verfügbare Betten, Schwallbetten, COVID-Patienten usw. 

> [!div class="mx-imgBorder"]
> ![Standortdetails](media/report-location-details.png) 

#### <a name="covid-patients-page"></a>Seite „COVID-Patienten“ 

Die Seite enthält Drilldown-Informationen zu den COVID-Patienten, z. B. Patienten an jedem Standort, Patiententrend im Zeitverlauf, die Spitzen und Täler der Anzahl der untersuchten Patienten (PUI) und der Anzahl der positiv gefundenen Patienten, und gibt einen Überblick darüber, wo Die Patienten sich im Krankenhaus befinden.

> [!div class="mx-imgBorder"]
> ![COVID-Patientendetails](media/report-covid-details.png)

#### <a name="bed-management-page"></a>Bettenverwaltungsseite 

Die Seite enthält Drilldown-Informationen nach Standort, z. B. insgesamt verfügbare Betten, verfügbare Akutbetten und Belegungsprozentsatz.

> [!div class="mx-imgBorder"]
> ![Bettenverwaltung](media/report-bed-details.png)

#### <a name="staffing-details-page"></a>Personalbesetzungsseite  

Die Seite enthält Details zum Personal nach Standort, Anzahl der zugewiesenen Krankenschwestern, Gesamtzahl der Patienten und Anzahl der COVID-Patienten. Es zeigt auch das Verhältnis von Krankenschwester zu Patient und das Verhältnis von Krankenschwester zu Patient auf der Intensivstation über einen bestimmten Zeitraum an.

> [!div class="mx-imgBorder"]
> ![Personaldetails](media/report-staff-details.png)

#### <a name="equipment-page"></a>Arbeitsgeräteseite 

Auf dieser Seite finden Sie Details zu den Geräten nach Standort, zur Gesamtzahl der verwendeten Beatmungsgeräte, überlagert mit der Anzahl der COVID-Patienten und zu anderen Geräten wie Gürteln, Ladegeräten und Hauben, die verwendet werden.

> [!div class="mx-imgBorder"]
> ![Arbeitsgerätedetails](media/report-equipment-details.png)

#### <a name="discharges-page"></a>Entlassungsseite 

Die Seite enthält Details zu Langzeitpatienten, Entlassungsbarrieren über einen bestimmten Zeitraum und Abweichungen in Bezug auf tatsächliche und erwartete Entlassungen.

> [!div class="mx-imgBorder"]
> ![Arbeitsgerätedetails](media/report-discharge-details.png)

#### <a name="supplies-page"></a>Vorräteseite 

Die Seite enthält Details zu den Vorräten nach Standort. Sie enthält auch eine Tabelle mit den verfügbaren Tagen nach Vorrat und Einrichtung sowie dem verfügbaren Angebot über einen bestimmten Zeitraum.

> [!div class="mx-imgBorder"]
> ![Arbeitsgerätedetails](media/report-supplies.png)

## <a name="view-and-manage-app-feedback"></a>Anzeigen und Verwalten von App-Feedback

Alle Rückmeldungen von Mitarbeitern an vorderster Front, die Canvas-Apps auf ihren Mobilgeräten verwenden, werden in der Entität **App-Feedback** gespeichert. Administratoren können dies mithilfe des Bereichs **Verwaltung** im linken Navigationsbereich in der Administrator-App anzeigen und verwalten.

So erfolgt das Anzeigen und Verwalten von App-Feedback:

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an und navigieren Sie zu Ihrer Administrator-App.

2. Wählen Sie im linken Navigationsbereich die Option **Administration** aus der Bereichsauswahl aus.

3. Wählen Sie **App-Feedback** aus, um eine Liste der von Benutzern eingereichten App-Rückmeldungen anzuzeigen. Sie können auf einen Datensatz klicken, um Details anzuzeigen und als überprüft oder nicht überprüft zu markieren.  

    > [!div class="mx-imgBorder"]
    > ![App-Feedback auswählen](media/select-app-feedback.png)

## <a name="issues-and-feedback"></a>Probleme und Feedback

- Um ein Problem mit der Hospital Emergency Response-Beispiel-App zu melden, navigieren Sie zu <https://aka.ms/emergency-response-issues>.

- Feedback zur Hospital Emergency Response-Beispiel-App finden Sie unter <https://aka.ms/emergency-response-feedback>.

## <a name="next-step"></a>Nächster Schritt

[Die mobile App für Notfallmaßnahmen im Krankenhaus verwenden](use.md)
