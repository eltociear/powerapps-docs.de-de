---
title: Verwenden der mobilen Notfallreaktions-App für Krankenhäuser | Microsoft-Dokumentation
description: Exemplarische Vorgehensweise beim Einsatz verschiedener Apps und Komponenten für die Benutzer der Vorlage der Beispiel-App zur Notfallreaktion für Krankenhäuser
author: pankajarora-msft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/15/2020
ms.author: pankar
ms.reviewer: tapanm
searchScope:
- PowerApps
ms.openlocfilehash: 3e77410c59eebc0008bf15a5aef3ed477669af0f
ms.sourcegitcommit: 263a12aefa72a3d73e07b2660bf1e89eba532a16
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81441511"
---
# <a name="use-the-hospital-emergency-response-mobile-app"></a>Verwenden der mobilen Notfallreaktions-App für Krankenhäuser

Krankenhauspersonal steht vor der Herausforderung, einer steigenden Anzahl von Patienten gerecht zu werden und gleichzeitig die Logistikkette in Notfallsituationen im Griff zu behalten. Mithilfe der mobilen Notfallreaktions-App für Krankenhäuser können Mitarbeiter an vorderster Front schnell Daten zu Beatmungsgeräten, Personal, anstehenden Entlassungen und Patienten mit COVID-19-Befund anzeigen und hinzufügen.

## <a name="prerequisites"></a>Voraussetzungen

Um die Arbeit mit der mobilen App aufzunehmen, müssen Sie Power Apps Mobile über den App Store des Geräts auf Ihr Gerät herunterladen.

- **Laden Sie**  die [**mobilen Power Apps** ](https://powerapps.microsoft.com/downloads) herunter
    - Verwenden Sie für **Apple**-Geräte mit iOS wie iPhone und iPad den [**App Store**](https://aka.ms/powerappsios).
    - Verwenden Sie für **Android**-Geräte [**Google Play**](https://aka.ms/powerappsandroid).
- Vergewissern Sie sich, dass Ihre Organisation die Notfallreaktions-App für Krankenhäuser, wie unter [Bereitstellen und Konfigurieren der App](deploy-configure.md) erläutert, bereitgestellt und konfiguriert hat.

Nachdem Sie die mobilen Power Apps installiert haben, öffnen Sie die App auf Ihrem Gerät. Melden Sie sich mit dem Azure Active Directory-Konto Ihres Unternehmens an. Sie können, sobald Sie sich angemeldet haben, alle Apps anzeigen, die von Ihrer Organisation für Sie freigegeben wurden. Weitere Informationen finden Sie unter [Anmelden bei Power Apps auf einem mobilen Gerät](https://docs.microsoft.com/powerapps/user/run-app-client#open-power-apps-and-sign-in).

## <a name="demo-use-the-hospital-emergency-response-mobile-app"></a>Demo: Verwenden der mobilen Notfallreaktions-App für Krankenhäuser

Sehen Sie sich an, wie die Notfallreaktions-App für Krankenhäuser verwendet wird.

<br/>

> [!VIDEO https://www.youtube.com/embed/H1u6SYt3UsQ]

## <a name="hospital-emergency-response-mobile-app"></a>Mobile Notfallreaktions-App für Krankenhäuser

![Notfallreaktions-App für Krankenhäuser](media/use/app-launcher.png)

Die mobile Notfallreaktions-App für Krankenhäuser hat eine modulare Struktur mit verschiedenen der jeweiligen Rolle entsprechenden Apps. Öffnen Sie in den mobilen Power Apps die mobile Notfallreaktions-App für Krankenhäuser. Wählen Sie Ihre Einstellungen für **Hospital system** (Krankenhaussystem), **Region, Facility** (Einrichtung) und dann **Next** (Weiter) aus, um die ersten Schritte zu unternehmen.

> [!NOTE]
> Wenn Sie die mobile Notfallreaktions-App für Krankenhäuser oder eine ihrer Komponenten zum *ersten Mal* starten, werden Sie um Ihre Zustimmung gebeten, dass die App Ihr Profil *Office 365-Benutzer* und Ihren *Standort* auslesen darf. Sie müssen **Zulassen** wählen, damit Sie die ausgewählte App verwenden können. Weitere Informationen finden Sie unter [Erteilen von Zustimmung](https://docs.microsoft.com/powerapps/user/run-app-client#give-consent).

## <a name="app-components"></a>App-Komponenten

![Komponenten der mobilen Notfallreaktions-App für Krankenhäuser](media/use/app-components.png)

Die Beispiellösungs-App für die Notfallreaktion für Krankenhäuser besteht für eine bessere Benutzererfahrung aus mehreren Apps. Je nach Ihrer Rolle sehen Sie in der **Notfallreaktions-App für Krankenhäuser** möglicherweise eine oder mehrere Komponenten.

- **Bed capacity**
     (Bettenkapazität)<br> Erfassen Sie Informationen zur Bettenkapazität, z. B. zur Anzahl von belegbaren Betten, Intensivbetten und anderen Betten.

- **COVID-19 stats**
     (Statistik zu COVID-19)<br> Erfassen Sie den Stand, wie viele Patienten auf COVID-19 untersucht und wie viele positiv getestet wurden.

- **Equipment**
     (Geräte)<br> Verfolgen Sie Informationen zur Geräten nach, z. B. die Anzahl von Beatmungsgeräten, Geräten für nicht-invasive Überdruckbeatmung und akkubetriebenen gebläseunterstützten Atemschutzgeräten.

- **Staff**
     (Personal)<br> Erfassen Sie die Anzahl von Patienten und Informationen zum Status der Pflegekräfte, z. B. Partner, beantragte, zugewiesene und nicht zugewiesene Pflegekräfte.

- **Supplies**
     (Verbrauchsmaterialien)<br> Behalten Sie wichtige Verbrauchsmaterialien im Blick, um den Bestand effektiver zu verfolgen, zu verwalten und zu prognostizieren. 

- **Staffing**
     (Personalbedarf)<br> Erfassen Sie Beantragungen von Personal nach Abteilung, Rolle und Dringlichkeit.

- **Discharge planning**
     (Entlassungsplanung)<br> Erfassen Sie den Status von und Prognosen zu Patientenentlassungen.

> [!NOTE]
> Standardmäßig können Sie Informationen in den folgenden Apps auf Ebene des *Standorts* nachverfolgen: **COVID-19 stats** (Statistik zu COVID-19), **Equipment** (Geräte) und **Staff** (Personal). In den anderen Apps können Sie Informationen auf Ebene der *Einrichtung* nachverfolgen. Ihr Administrator kann die standardmäßige Nachverfolgungsebene ggf. ändern. Weitere Informationen: [Verwalten der Nachverfolgungsebene für mobile Apps](configure-data-reporting.md#manage-tracking-level-for-mobile-apps)

## <a name="bed-capacity"></a>Bed capacity (Bettenkapazität)

![Bed capacity (Bettenkapazität)](media/use/bed-capacity.png)

Übermitteln Sie Informationen zu Betten, z. B. Anzahl von belegbaren Betten, Intensivbetten (Isolationszimmer mit Unterdruck zum Schutz vor aerogener Übertragung), Akutbetten (Isolationszimmer mit Unterdruck zum Schutz vor aerogener Übertragung) und Informationen dazu, ob die ausgewählte Einrichtung über genügend Personal für eine vollständige Belegung verfügt.

Wählen Sie links oben **Back** (Zurück) aus, wenn Sie zur **Notfallreaktions-App für Krankenhäuser** zurückkehren möchten, ohne eine Änderung zu übermitteln. Über die Schaltfläche **Submit** (Senden) werden die von Ihnen eingegebenen Werte übermittelt.

Nachdem Sie die Daten übermittelt haben, haben Sie die Möglichkeit, zur App **Bed capacity** (Bettenkapazität) zurückzukehren, um über die Schaltfläche **Track another** (Weiteren nachverfolgen) einen weiteren Datensatz zu erstellen. Wählen Sie **Home** (Start) aus, um zur **Notfallreaktions-App für Krankenhäuser** zurückzukehren.

### <a name="fields-and-description"></a>Felder und Beschreibung

| **Optionsname**                                               | **Beschreibung**                                                                       |
|---------------------------------------------------------------|---------------------------------------------------------------------------------------|
| How many licensed beds are currently in use in this facility? (Wie viele belegbaren Betten sind in dieser Einrichtung derzeit belegt?) | Die Anzahl der belegbaren Betten in dieser Einrichtung, die derzeit belegt sind.                            |
| Number of ICU Beds (AIIR Room) currently in use (Anzahl von derzeit belegten Intensivbetten (Isolationszimmer mit Unterdruck zum Schutz vor aerogener Übertragung))               | Die Anzahl der derzeit belegten Intensivbetten (Isolationszimmer mit Unterdruck zum Schutz vor aerogener Übertragung).                                      |
| Number of ICU Beds (non-AIIR Room) currently in use (Anzahl von derzeit belegten Intensivbetten (Isolationszimmer mit Unterdruck zum Schutz vor aerogener Übertragung))           | Die Anzahl der derzeit belegten Intensivbetten (Isolationszimmer mit Unterdruck zum Schutz vor aerogener Übertragung).                                  |
| Number of Acute Care Beds (AIIR Room) currently in use (Anzahl von derzeit belegten Akutbetten (Isolationszimmer mit Unterdruck zum Schutz vor aerogener Übertragung))        | Die Anzahl der derzeit belegten Akutbetten (Isolationszimmer mit Unterdruck zum Schutz vor aerogener Übertragung).                               |
| Number of Acute Care Beds (non-AIIR Room) currently in use (Anzahl von derzeit belegten Akutbetten (Isolationszimmer mit Unterdruck zum Schutz vor aerogener Übertragung))    | Die Anzahl der derzeit belegten Akutbetten (Isolationszimmer mit Unterdruck zum Schutz vor aerogener Übertragung).                           |
| Is your facility staffed to its full license bed capacity? (Sind in Ihrer Einrichtung genügend Mitarbeiter für die vollständige Kapazität der belegbaren Betten vorhanden?)    | Ja/Nein. Falls die Antwort „Nein“ lautet, können Sie alle zutreffenden Gründe auswählen: <br> – Staff (Personal) <br> – Space (Verfügbarer Platz) <br> – PPE (Persönliche Schutzausrüstung, PSA) <br> – Equipment (Geräte) <br> – Low Patient Volume (Geringe Patientenzahl) |
| Are you able to surge beyond your licensed beds? (Können Sie Ihre Kapazität über die genehmigte Anzahl von Betten hinaus aufstocken?)              | Ja/Nein. Falls die Antwort „Nein“ lautet, können Sie alle zutreffenden Gründe auswählen: <br> – Staff (Personal) <br> – Space (Verfügbarer Platz) <br> – PPE (Persönliche Schutzausrüstung, PSA) <br> – Equipment (Geräte) <br> – Low Patient Volume (Geringe Patientenzahl)  |
| Number of surge beds currently in use (Anzahl von derzeit belegten Notbetten)                         | Die Anzahl der derzeit belegten Notbetten.                                                |

## <a name="covid-19-stats"></a>COVID-19 stats (Statistik zu COVID-19)

![COVID-19 Stats (Statistik zu COVID-19)](media/use/covid19-stats.png)

Übermitteln Sie mit der App  **COVID-19 stats** COVID-19-spezifische Details. Sie können die standortspezifischen Details zu Patienten wie beispielsweise die Anzahl von Verdachtsfällen sowie von positiv getesteten, intubierten und entlassenen Patienten aktualisieren.

Wählen Sie links oben **Back** (Zurück) aus, wenn Sie zur **Notfallreaktions-App für Krankenhäuser** zurückkehren möchten, ohne eine Änderung zu übermitteln. Über die Schaltfläche **Submit** (Senden) werden die von Ihnen eingegebenen Werte übermittelt.

Nachdem Sie die Daten übermittelt haben, haben Sie die Möglichkeit, zur App **COVID-19 stats** (COVID-19-Statistik) zurückzukehren, um über die Schaltfläche **Track another** (Weiteren nachverfolgen) einen weiteren Datensatz zu erstellen. Wählen Sie **Home** (Start) aus, um zur **Notfallreaktions-App für Krankenhäuser** zurückzukehren.

### <a name="fields-and-description"></a>Felder und Beschreibung

| **Feldname**  | **Beschreibung**                                                                                    |
|-----------------|----------------------------------------------------------------------------------------------------|
| Standort        | Name und Typ des Raums, der Station oder eines anderen speziellen Bereichs innerhalb der ausgewählten Einrichtung.  |
| PUIs (Untersuchte Patienten)            | Anzahl der untersuchten Patienten.                                                            |
| Positive        | Anzahl der Patienten mit positivem Befund auf COVID-19.                                                         |
| Intubiert        | Die Anzahl der Patienten, die intubiert sind.                                                         |
| Entlassen        | Die Anzahl der COVID-19-Patienten, die bereits entlassen wurden.                                                         |

## <a name="equipment"></a>Geräte

![Geräte](media/use/equipment.png)

Übermitteln Sie über die App  **Equipment** (Geräte) Informationen zu Geräten und Ausrüstung an Ihrem Standort. Sie können die Anzahl der verwendeten Geräte (z. B. Beatmungsgeräte, Geräte für nicht-invasive Überdruckbeatmung und akkubetriebene gebläseunterstützte Atemschutzgeräte) aktualisieren.

Wählen Sie links oben **Back** (Zurück) aus, wenn Sie zur **Notfallreaktions-App für Krankenhäuser** zurückkehren möchten, ohne eine Änderung zu übermitteln. Über die Schaltfläche **Submit** (Senden) werden die von Ihnen eingegebenen Werte übermittelt.

Nach Übermittlung der Daten haben Sie die Möglichkeit, zur App **Staff + equipment** (Personal und Geräte) zurückzukehren, um über die Schaltfläche **Track another** (Weiteren nachverfolgen) einen weiteren Datensatz zu erstellen. Wählen Sie **Home** (Start) aus, um zur **Notfallreaktions-App für Krankenhäuser** zurückzukehren.

### <a name="fields-and-description"></a>Felder und Beschreibung

| **Feldname**  | **Beschreibung**                                                                                    |
|-----------------|----------------------------------------------------------------------------------------------------|
| Standort        | Name und Typ des Raums, der Station oder eines anderen speziellen Bereichs innerhalb der ausgewählten Einrichtung.  |
| Ventilators (Beatmungsgeräte)            | Die Anzahl der derzeit genutzten Beatmungsgeräte.                                                            |
| NIPPV (Geräte für nicht-invasive Überdruckbeatmung)        | Die Anzahl der derzeit genutzten Geräte für nicht-invasive Überdruckbeatmung.                                                         |
| PAPR belts (Gurte für akkubetriebene gebläseunterstützte Atemschutzgeräte)        | Die Anzahl der derzeit genutzten Gurte für akkubetriebene gebläseunterstützte Atemschutzhauben.                                                         |
| PAPR chargers (Ladegeräte für akkubetriebene gebläseunterstützte Atemschutzgeräte)        | Die Anzahl der derzeit genutzten Ladegeräte für akkubetriebene gebläseunterstützte Atemschutzhauben.                                                         |
| PAPR hoods (Hauben für akkubetriebene gebläseunterstützte Atemschutzgeräte)        | Die Anzahl der derzeit genutzten Hauben für akkubetriebene gebläseunterstützte Atemschutzhauben.                                                         |

## <a name="staff"></a>Personal

![Personal](media/use/staff.png)

Übermitteln Sie den standortspezifischen Stand bei Pflegepersonal, Patienten und Geräten. Sie müssen nicht in jedes Feld auf dem Bildschirm Werte eingeben. Geben Sie einen Wert in das Feld ein, der in der Lösungsdatenbank gespeichert werden soll.

Wenn Sie z. B. drei examinierte Krankenschwestern oder -pfleger als beantragt eintragen möchten, geben Sie in das Feld **Registered nurses on duty - Requested** (Examiniertes Pflegepersonal im Dienst – beantragt) die Zahl 3 ein, und wählen Sie dann **Submit** (Senden) aus. Wenn Sie außerdem die Anzahl unter **Registered nurses on duty - Assigned** (Examiniertes Pflegepersonal im Dienst – zugewiesen) auf 6 aktualisieren möchten, geben Sie die Zahl 3 im Feld **Registered nurses on duty - Requested** (Examiniertes Pflegepersonal im Dienst – beantragt) und dann die Zahl 6 im Feld **Registered nurses on duty - Assigned** (Examiniertes Pflegepersonal im Dienst – zugewiesen) ein. Wählen Sie dann **Submit** (Senden) aus.

Wählen Sie links oben **Back** (Zurück) aus, wenn Sie zur **Notfallreaktions-App für Krankenhäuser** zurückkehren möchten, ohne eine Änderung zu übermitteln. Über die Schaltfläche **Submit** (Senden) werden die von Ihnen eingegebenen Werte übermittelt.

Nach Übermittlung der Daten haben Sie die Möglichkeit, zur App **Staff** (Personal) zurückzukehren, um über die Schaltfläche **Track another** (Weiteren nachverfolgen) einen weiteren Datensatz zu erstellen. Wählen Sie **Home** (Start) aus, um zur **Notfallreaktions-App für Krankenhäuser** zurückzukehren.

### <a name="fields-and-description"></a>Felder und Beschreibung

| **Optionsname**               | **Beschreibung**                                                                                   |
|-------------------------------|---------------------------------------------------------------------------------------------------|
| Standort                      | Name und Typ des Raums, der Station oder eines anderen speziellen Bereichs innerhalb der ausgewählten Einrichtung. |
| Number of patients (Anzahl der Patienten)            | Aktuelle Gesamtanzahl der Patienten am ausgewählten Standort.                                        |
| **Registered nurses on duty** (Pflegepersonal im Dienst) |                                                                                                   |
| *Partner*                    | Anzahl der Partner des Pflegepersonals am ausgewählten Standort.                             |
| *Requested* (Beantragt)                   | Umfang des am ausgewählten Standort beantragten Pflegepersonals.                                  |
| *Assigned* (Zugewiesen)                    | Anzahl des dem ausgewählten Standort zugewiesenen Pflegepersonals.                                    |
| *Unassigned* (Nicht zugewiesen)                  | Umfang des Pflegepersonals, dem am ausgewählten Standort keine Aufgaben zugewiesen ist.                    |
| **Nachverfolgung auf Ebene der Einrichtung** |                                                                                                   |
| % of essential care personnel currently absent in this facility (Prozentsatz des in dieser Einrichtung derzeit nicht anwesenden essenziellen Pflegepersonals)                  | In dieser Einrichtung nicht anwesendes essenzielles Pflegepersonal als Prozentsatz des Personals in der **gesamten Einrichtung**.                    |

## <a name="supplies"></a>Supplies (Verbrauchsmaterialien)

![Supplies (Verbrauchsmaterialien)](media/use/supplies.png)

In der App **Supplies** (Verbrauchsmaterialien) können Sie den Bestand an Verbrauchsmaterialien einsehen. In dieser App können Sie die Mengen der einzelnen Verbrauchsmaterialien im gesamten Bestand der Einrichtung und den täglichen Verbrauch aktualisieren.

> [!NOTE]
> Geben Sie in beide Felder, **In stock** (Auf Lager) und **Used past 24 hr** (Verbrauch in den letzten 24 Stunden), Werte ein, bevor Sie **Submit** (Senden) auswählen.

Wählen Sie links oben **Back** (Zurück) aus, wenn Sie zur **Notfallreaktions-App für Krankenhäuser** zurückkehren möchten, ohne eine Änderung zu übermitteln. Über die Schaltfläche **Submit** (Senden) werden die von Ihnen eingegebenen Werte übermittelt. Wählen Sie **Home** (Start) aus, um nach dem Übermitteln zur **Notfallreaktions-App für Krankenhäuser** zurückzukehren.

### <a name="fields-and-description"></a>Felder und Beschreibung

Die Liste der Verbrauchsmaterialien kann je nach Anforderungen Ihrer Organisation variieren. Die Namen von Verbrauchsmaterialien finden Sie in den Dokumentationsressourcen Ihrer Organisation.

IT-Administratoren können mithilfe der modellgesteuerten App für Power Apps die Liste der Artikel in der App „Supplies“ ergänzen oder aktualisieren. Weitere Informationen finden Sie in der [Konfigurationsanleitung](deploy-configure.md).

> [!NOTE]
> Die Werte der Artikel im Verbrauchsmaterialbestand müssen im Zahlenformat vorliegen.

## <a name="staffing-needs"></a>Staffing needs (Personalbedarf)

![Staffing needs (Personalbedarf)](media/use/staffing-needs.png)

Erfasst Beantragungen von Pflegepersonal in der gewählten Einrichtung. Bevor Sie die Beantragung von Pflegepersonal für eine Einrichtung übermitteln können, müssen Sie die als *Pflichtfeld* (*) gekennzeichneten Felder unbedingt ausfüllen.

Wählen Sie links oben **Back** (Zurück) aus, wenn Sie zur **Notfallreaktions-App für Krankenhäuser** zurückkehren möchten, ohne eine Änderung zu übermitteln. Über die Schaltfläche **Submit** (Senden) werden die von Ihnen eingegebenen Werte übermittelt. Wählen Sie **Home** (Start) aus, um nach dem Übermitteln zur **Notfallreaktions-App für Krankenhäuser** zurückzukehren.

### <a name="fields-and-description"></a>Felder und Beschreibung

| **Feldname**           | **Beschreibung**                                                                            |
|--------------------------|--------------------------------------------------------------------------------------------|
| Abteilung               | Der Name der Abteilung, das Pflegepersonal beantragt. Dies ist ein *Pflichtfeld*.             |
| Department location (Standort der Abteilung)      | Der Standort der Abteilung.                                                                |
| Anforderungstyp             | Typ des beantragten Personals, z. B. klinisch und nicht klinisch. Dies ist ein *Pflichtfeld*. |
| Role needed (Erforderliche Rolle)              | Rolle des angeforderten Personals, z. B. Pfleger oder examinierte Krankenschwester.                          |
| Needed now or next shift (Jetzt oder in der nächsten Schicht benötigt) | Wählen Sie eine Schicht für das beantragte Personal aus: aktuelle Schicht oder eine kommende Schicht.                |
| How many (Anzahl)                 | Die Anzahl der benötigten Mitarbeiter im numerischen Format.                |
| Details                  | Geben Sie zusätzliche Details oder Kommentare für die Beantragung von Personal an.                        |



## <a name="discharge-planning"></a>Discharge planning (Entlassungsplanung)

![Discharge (Entlassen)](media/use/discharge.png)

Mithilfe der App  **Discharge planning** (Entlassungsplanung) können Sie Informationen zu Entlassungen und den Patientenstatus samt Gesamtanzahl übermitteln. Sie können die Entlassungsdetails der letzten 24 Stunden, die aktuellen Entlassungssperren und die Aufhebung der Sperren aktualisieren.

Wählen Sie links oben **Back** (Zurück) aus, wenn Sie zur **Notfallreaktions-App für Krankenhäuser** zurückkehren möchten, ohne eine Änderung zu übermitteln. Über die Schaltfläche **Submit** (Senden) werden die von Ihnen eingegebenen Werte übermittelt. Wählen Sie **Home** (Start) aus, um nach dem Übermitteln zur **Notfallreaktions-App für Krankenhäuser** zurückzukehren.

### <a name="fields-and-description"></a>Felder und Beschreibung

| **Feldname**            | **Beschreibung**                                                    |
|---------------------------|--------------------------------------------------------------------|
| Autorisierung             | Anzahl der Patienten im Autorisierungsprozess.                   |
| Durable medical equipment (Langlebige medizinische Geräte) | Anzahl der Patienten, die langlebige medizinische Geräte nutzen.            |
| Guardianship (Vormundschaft)              | Anzahl der Patienten unter Vormundschaft.                             |
| Home + Community Services (Ambulante Pflegedienste) | Anzahl der Patienten, die ambulante Pflegedienste nutzen.               |
| Platzierung                 | Anzahl der benötigten Unterbringungen.                                       |
| Skilled Nursing Facility (Pflegeheim)  | Anzahl der Pflegeheime.                              |
| **Discharges** (Entlassungen)            |                                                                    |
| Past 24 h (Letzte 24 Stunden)                 | Anzahl der Patienten, die voraussichtlich in den letzten 24 Stunden entlassen wurden.  |
| Likely next 24 h (Wahrscheinlich in den nächsten 24 Stunden)          | Anzahl der Patienten, die in den nächsten 24 Stunden entlassen werden.                    |

## <a name="other-options"></a>Weitere Optionen

In diesem Abschnitt werden weitere Aktionen erläutert, die mit den Komponenten der mobilen Notfallreaktions-App für Krankenhäuser möglich sind.

### <a name="end-shift---sign-out"></a>Abmelden bei Schichtende

Sie können sich über das Profilsymbol links oben auf dem Bildschirm von der App abmelden.  

![Abmeldung](media/use/sign-out.png)

Wählen Sie die Schaltfläche **End shift** (Schicht beenden) aus, um die Sitzung zu beenden und sich anzumelden.

> [!NOTE]
> *End shift* (Schicht beenden) ist möglicherweise nicht möglich, wenn Ihr IT-Administrator die Gerätefreigabe deaktiviert hat.

### <a name="app-feedback"></a>App-Feedback

Sie können in jeder Komponente der mobilen Notfallreaktions-App über die Option **App feedback** Ihr Feedback abgeben. Um Ihr Feedback zu übermitteln, wählen Sie links oben Ihr Profil und dann die Schaltfläche **Submit feedback** (Feedback senden) aus:

![Feedback geben](media/use/give-feedback.png)

Wenn Sie **App-Feedback** auswählen, haben Sie die Möglichkeit, Lob, Anregungen oder ein Problem mit der App zu melden.

### <a name="switch-facility"></a>Ändern der Einrichtung

![Ändern der Einrichtung](media/use/switch-facility.png)

Sie können jederzeit die Einrichtung ändern, indem Sie rechts oben auf dem Bildschirm den Namen der Einrichtung auswählen. Nach Wahl des Standortnamens gelangen Sie zum Bildschirm der **Notfallreaktions-App für Krankenhäuser**, auf dem Sie ein anderes Krankenhaus, eine andere Region oder eine andere Einrichtung auswählen können.

## <a name="issues-and-feedback"></a>Issues und Feedback

- Wenn Sie ein Issue mit der Beispiel-App für die Notfallreaktion für Krankenhäuser melden möchten, besuchen Sie <https://aka.ms/emergency-response-issues>.

- Wenn Sie Feedback zur Beispiel-App für die Notfallreaktion für Krankenhäuser geben möchten, besuchen Sie <https://aka.ms/emergency-response-feedback>.


