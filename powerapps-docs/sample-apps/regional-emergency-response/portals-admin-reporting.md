---
title: Verwaltung des Regional Government Emergency Response and Monitoring-Portals | Microsoft Docs
description: Erfahren Sie, wie das Portal für Regional Hospital Emergency Response konfiguriert wird.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 05/06/2020
ms.author: tapanm
ms.reviewer: tapanm
searchScope:
- PowerApps
ms.openlocfilehash: 2933ad47995915d60b864188c87bb6c9e6953407
ms.sourcegitcommit: c424a17b9c658f4571b5ea26ab6fc8a486051d44
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "3341882"
---
# <a name="administer-the-regional-governmentemergency-response-and-monitoring-portal"></a>Administration des Regional Government Emergency Response and Monitoring-Portals

Das Krankenhauspersonal ist gefordert, eine Zunahme der Patientenzahlen zu bewältigen und gleichzeitig die Lieferkette im Notfall zu verwalten. Über das Portal für Emergency Response and Monitoring der Regionalregierung können Administratoren schnell Daten zu **Benutzer**, **Systeme**, **Regionen** und **Einrichtungen** einsehen und aktualisieren. Stakeholder können die veröffentlichten Erkenntnisse über Dashboards zum aktuellen Stand des Gesundheitssystems einsehen und Maßnahmen ergreifen.

## <a name="portal-at-a-glance"></a>Portal im Überblick

Navigieren Sie zum Power Apps-Portal, um **Benutzer**, **Systeme**, **Regionen** und **Einrichtungen** hinzuzufügen, zu bearbeiten oder zu löschen. Der folgende Abschnitt führt Sie durch das, worauf Sie als Administrator des Portals zugreifen, einreichen oder aktualisieren können.

![Portal im Überblick](media/portal-at-glance.png)

Sie können die neuesten mobilen Geräte und Webbrowser verwenden, wenn Sie das Portal Regional Government Emergency Response and Monitoring Portal nutzen, mit Ausnahme von Apple iPad.

[!include[cc-getting-started](includes/cc-getting-started.md)]

> [!NOTE] 
> Administratoren müssen **Krankenhaussystem, Region** und **Einrichtung** und **Weiter** wählen, um die Verwaltungs- und Dashboard-Einstellungen anzuzeigen. Wenn Sie das Portal nur für administrative Aktionen wie Benutzerverwaltung oder Dashboard-Überprüfungen verwenden, können Sie einen beliebigen Ort auswählen. Wenn Sie jedoch Benutzerkomponenten wie **Mitarbeiter** oder **Ausrüstung** verwenden möchten, stellen Sie sicher, dass Sie den richtigen Speicherort gewählt haben.

[!include[cc-manage-user-profile](includes/cc-manage-user-profile.md)]

## <a name="administrative-tasks"></a>Administrative Aufgaben

Sie können alle administrativen Optionen anzeigen, die Ihnen nach Auswahl von **Verwaltung** auf dem Startbildschirm zur Verfügung stehen:

![Portalverwaltung](media/portal-admin-screen.png)

### <a name="administrative-tasks-and-description"></a>Administrative Aufgaben und Beschreibung

| **Optionsname** | **Beschreibung**                                                                                               |
|-----------------|---------------------------------------------------------------------------------------------------------------|
| [Benutzeranforderungen](#user-requests) | Anzeigen, Genehmigen oder Ablehnen von Portalbenutzeranfragen.
| [Benutzer](#users)       | Erstellen, bearbeiten oder deaktivieren Sie Portalbenutzer.                                                         |
| [Systeme](#systems)      | Systeme erstellen, bearbeiten oder löschen. |
| [Regionen](#regions)      | Regionen erstellen oder löschen.                              |
| [Facilities](#facilities)    | Einrichtungen erstellen, bearbeiten oder löschen.                        |

### <a name="user-requests"></a>Benutzeranforderungen

Sie können Portal-Benutzeranfragen einsehen, genehmigen und ablehnen, indem Sie die Option Administrationsaufgabe **Benutzeranfragen** wählen.

Wenn Sie **Benutzeranfragen** wählen, können Sie alle vorhandenen Portal-Benutzeranfragen sehen, die zur Überprüfung eingereicht wurden:

![Portal-Benutzeranfragen anzeigen](media/view-portal-user-requests.png)

Sie können die Ansicht ändern und genehmigte oder abgelehnte Anträge anzeigen lassen:

![Ansicht der Portal-Benutzeranfrage ändern](media/portal-user-requests-views.png)

#### <a name="process-pending-requests"></a>Ausstehende Anfragen bearbeiten

Um ausstehende Portalbenutzeranfragen zu bearbeiten, wählen Sie **Details anzeigen** für eine ausstehende Anfrage aus der Ansicht **Ausstehende Portalbenutzeranfragen**:

![Details zur Anfrage anzeigen](media/portal-user-requests-view-details.png)

In der Detailansicht können Sie die Kontaktinformationen und Rollen der Benutzer prüfen und die Anfrage genehmigen oder ablehnen. Die auf dem Formular ausgewählten Rollen sind die angeforderten Rollen. Sie können über das Kontrollkästchen Rollen hinzufügen oder entfernen, bevor Sie die Anfrage genehmigen oder ablehnen:

![Benutzeranfrage genehmigen oder ablehnen](media/approve-reject-user-request.png)

Weitere Informationen über die Rollen finden Sie unter [Benutzerrollen](#user-roles).

Wählen Sie **Zugriffsanfrage genehmigen** zur Genehmigung oder **Zugriffsanfrage ablehnen** zur Ablehnung der Anfrage.

Wenn Sie eine Anfrage ablehnen, müssen Sie einen Grund dafür angeben:

![Grund für die Ablehnung](media/decline-request-reason.png)

#### <a name="request-approval-or-decline-emails"></a>E-Mails zur Genehmigung oder Ablehnung anfordern

Je nachdem, ob Sie eine Benutzeranfrage genehmigen oder ablehnen, erhält der Anforderer eine E-Mail mit dem Ergebnis des Anfrageprozesses. Bei genehmigten Anfragen enthält die E-Mail einen Einladungscode, der vom Benutzer bei der ersten Anmeldung eingelöst werden kann. Bei abgelehnten Anfragen enthält die E-Mail einen Ablehnungsgrund, der bei der Ablehnung der Anfrage eingegeben wurde.

### <a name="review-approved-requests"></a>Genehmigte Anfragen überprüfen

Um genehmigte Portalbenutzeranfragen anzuzeigen, wählen Sie **Details anzeigen** für eine genehmigte Anfrage aus der Ansicht **Genehmigte Portalbenutzeranfragen**:

![Genehmigte Anfrage anzeigen](media/portal-user-requests-view-approved-details.png)

Wählen Sie **Zugriffsanfrage ablehnen**, um eine bestehende genehmigte Anfrage abzulehnen:

![Genehmigte Anfrage ablehnen](media/decline-approved-request.png)

### <a name="review-declined-requests"></a>Überprüfung abgelehnter Anfragen

Um genehmigte Portalbenutzeranfragen anzuzeigen, wählen Sie **Details anzeigen** für eine genehmigte Anfrage aus der Ansicht **Genehmigte Portalbenutzeranfragen**:

![Genehmigte Anfrage anzeigen](media/portal-user-requests-view-declined-details.png)

Sie können auch den obligatorischen **Abgelehnter Grund** für jede Anfrage als Kommentar anzeigen, der bei der früheren Ablehnung der Anfrage abgegeben wurde.

Wählen Sie **Zugriffsanfrage genehmigen**, um eine bestehende abgelehnte Anfrage zu genehmigen:

![Abgelehnte Anfrage genehmigen](media/approve-declined-request.png)

### <a name="users"></a>Benutzer

Gehen Sie zu **Benutzer**, um neue Benutzer anzulegen, die das Portal verwalten, die Dashboards anzeigen oder das Portal als Mitarbeiter im Gesundheitswesen verwenden können:

![Benutzer](media/portal-admin-add-user.png)

Es stehen zwei Ansichten zur Verfügung: **Alle aktiven Benutzer** und **Meine aktiven Benutzer**. Die Ansicht **Alle aktiven Benutzer** zeigt alle aktiven Benutzer für die ausgewählte übergeordnete Organisation. Die Ansicht **Meine aktiven Benutzer** zeigt alle aktiven Benutzer für die ausgewählte übergeordnete Organisation, die vom derzeit angemeldeten Administrator der übergeordneten Organisation erstellt oder genehmigt wurden.

Sie können auch [Benutzerdetails anzeigen](#view-user-details), [Benutzerrolle ändern](#change-role-for-a-user) und [Benutzer deaktivieren](#deactivate-a-user) von **Benutzer**.

#### <a name="search-user-details"></a>Benutzerdetails suchen

Geben Sie Text in das Suchfeld ein, um die gefilterten Ergebnisse für die gesuchten Benutzer anzuzeigen. Die Wildcard-Suche (**\***) ist aktiviert und Sie können nach den folgenden Feldern suchen:

- Vollständiger Name

- Per E-Mail senden

- Mobiltelefonnummer

- Übergeordnete Organisation

Sie können die Platzhaltersuche und Teilbegriffe verwenden, um Ergebnisse, einschließlich Telefonnummern, anzuzeigen.

Wenn Sie z.B. nach einem Benutzer mit **Vollständiger Name** als **Delores Vasquez** suchen möchten, können Sie bei der Suche folgende Beispielzeichenfolgen verwenden:

- Del\*

- \*Del

- Del\*va

Um nach **Mobiltelefon** zu suchen, können Sie ähnlichen Text mit Platzhalter verwenden, wobei Zeichen durch Zahlen ersetzt werden.

#### <a name="create-user"></a>Benutzer erstellen

Um Benutzer zu erstellen, wählen Sie die Schaltfläche **Benutzer erstellen**, wenn Sie sich im Formular **Benutzer** befinden. Und dann geben Sie die neuen Benutzerdetails in das Formular ein:

![Benutzer erstellen](media/portal-admin-create-user.png)

Geben Sie **Vorname**, **Nachname**, **E-Mail** und **Mobiltelefon** ein und wählen Sie dann eine Rolle für den Benutzer aus.

##### <a name="user-roles"></a>Benutzer-Rollen

Die Rolle des Benutzers definiert die Komponenten, die im Portal angezeigt werden:

![Portal mit Rollen](media/portal-with-roles.png)

Die hervorgehobenen Komponenten sind für die Benutzer sichtbar, denen die folgenden Rollen zugewiesen wurden:

1. [Organisationsfachkraft im Gesundheitswesen](#organizational-healthcare-worker)
2. [Berichts-Viewer](#report-viewer)
3. [Administrator der übergeordneten Organisation](#parent-organization-administrator)

Der folgende Abschnitt führt durch jede der Rollen mit Einzelheiten darüber, was das Mitglied der Rolle tun kann:

##### <a name="organizational-healthcare-worker"></a>Organisationsfachkraft im Gesundheitswesen

Ein Healthcare Worker ist ein Mitarbeiter eines Krankenhaussystems, z.B. eine registrierte Krankenschwester. Mitarbeiter des Gesundheitswesens arbeiten in einer oder mehreren Einrichtungen. Das Gesundheitspersonal sammelt Daten in den folgenden Bereichen:

- Bettenkapazität

- Personal

- Arbeitsgerät

- Bedarf

- COVID-19-Statistiken

##### <a name="report-viewer"></a>Berichts-Viewer

Eine Bericht-Viewer-Rolle ist für die Benutzer, die die auf diesem Portal verfügbaren Dashboards anzeigen können. Mitglieder der Rolle Berichtsbetrachter können die folgenden Dashboards anzeigen:

- System im Überblick

- Angaben zum COVID-19-Patienten

- Details zur Bettenkapazität

- Ausstattungsdetails

- Details zu Verbrauchsmaterial

##### <a name="parent-organization-administrator"></a>Administrator der übergeordneten Organisation

Ein Administrator einer übergeordneten Organisation kann Benutzer anlegen, die über dieses Portal auf die Organisationsdetails zugreifen können.

Mitglieder der übergeordneten Organisationsadministrator-Rolle können:

- Erstellen Sie neue Benutzer und fügen Sie sie zu den Rollen **Organisationsmitarbeiter im Gesundheitswesen, Berichtsbetrachter** oder **Verwalter der übergeordneten Organisation** hinzu.

- Ändern Sie die Metadaten für die Organisation mit:

    - Erstellen, bearbeiten oder löschen **System**

    - Erstellen oder löschen Sie **Region**

    - Erstellen, bearbeiten oder löschen Sie **Funktionalität**

> [!TIP]
> Wählen Sie alle 3 Rollen aus, um einem Benutzer den Zugriff auf alle Komponenten zu ermöglichen.

#### <a name="view-user-details"></a>Benutzerdetails anzeigen

Sie können Benutzerdetails anzeigen, indem Sie die Dropdown-Liste für den Benutzer wählen und dann **Details anzeigen** wählen:

![Benutzeroptionen anzeigen](media/portal-user-view-user-options.png)

##### <a name="change-role-for-a-user"></a>Ändern der Rolle für einen Benutzer

Sie können Benutzerrollen zu den Benutzerdetails hinzufügen oder entfernen:

![Benutzerdetails anzeigen](media/portal-user-view-details.png)

#### <a name="deactivate-a-user"></a>Deaktivieren eines Benutzers

Wählen Sie **Deaktivieren** aus der Benutzer-Dropdown-Liste, um ein Benutzerkonto zu deaktivieren:

![Benutzeroptionen anzeigen](media/portal-user-view-user-options.png)

Deaktivierter Benutzer wird nicht mehr in der Liste der Benutzer in der Ansicht **Benutzer** angezeigt.

### <a name="systems"></a>Systeme

Sie können ein **System** hinzufügen, aktualisieren oder löschen, indem Sie das Formular **System** verwenden. Wenn Sie **System** wählen, können Sie alle vorhandenen **Krankenhaussysteme** sehen:

![Systeme](media/portal-add-system.png)

#### <a name="search-existing-systems"></a>Vorhandene Systeme durchsuchen

Geben Sie Text in das Suchfeld ein, um nach Anlage zu suchen und die Liste der Anlagen auf dem Formular zu filtern. Sie können die Platzhaltersuche (**\***) in Kombination mit Textzeichen für **Systemname** und **Beschreibung** Felder verwenden.

#### <a name="view-system-details"></a>Systemdetails anzeigen

Um Details eines Systems anzuzeigen, wählen Sie das Dropdown-Menü für ein System und wählen Sie dann **Details anzeigen**:

![System anzeigen](media/portal-view-system-details.png)

Die Seite Systemdetails zeigt **Übergeordnete Organisation, Systemname**, **Beschreibung** und **Regionen** innerhalb des Systems:

![Einzelheiten zum System](media/portal-system-details.png)

Sie können die Felder **Systemname** und **Beschreibung** in den entsprechenden Textfeldern eines Systems aktualisieren.

##### <a name="add-region"></a>Region hinzufügen

Verwenden Sie die Schaltfläche **Region hinzufügen**, um dem aktuellen System eine Region hinzuzufügen. Wenn Sie **Region hinzufügen** wählen, können Sie Regionsdetails wie **Regionsname** und **Beschreibung** hinzufügen:

![Region hinzufügen](media/portal-admin-add-region.png)

Sie können **System** in der Dropdown-Liste ändern, bevor Sie eine Region hinzufügen. Ziehen Sie es jedoch vor, einem System eine Region hinzuzufügen, indem Sie sich zuerst das System ansehen, dem Sie eine Region hinzufügen möchten. Wenn Sie nämlich **Anmelden** wählen, können Sie, wenn das von Ihnen gewählte System von der geöffneten Detailseite abweicht, die im Regionenabschnitt aufgelistete Region nicht sehen.

#### <a name="create-system"></a>System erstellen

Um ein System zu erstellen, wählen Sie **Erstellen**, geben *Systemname* und *Beschreibung* ein:

![System erstellen](media/portal-admin-create-system.png)

#### <a name="delete-system"></a>System löschen

Um eine Anlage zu löschen, wählen Sie das Dropdown-Menü und wählen Sie dann **Löschen** Option:

![System löschen](media/portal-view-system-details.png)

Wählen Sie **Löschen**, um einen Systemdatensatz zu löschen. Sie werden aufgefordert, die Löschung zu bestätigen, bevor das System gelöscht wird:

![Löschen bestätigen](media/portal-delete-system-confirm.png)

### <a name="regions"></a>Regionen

Sie können ein **Region** hinzufügen oder löschen, indem Sie das Formular **Region hinzufügen** verwenden. Wenn Sie **Region hinzufügen** wählen, können Sie alle vorhandenen **Krankenhaussysteme** sehen:

![Region hinzufügen](media/portal-add-region.png)

#### <a name="search-existing-regions"></a>Suche in bestehenden Regionen

Geben Sie einen Text in das Suchfeld ein, um nach einer Region zu suchen und die Liste der Regionen auf dem Formular zu filtern. Sie können Platzhaltersuche (**\***) in Kombination mit Textzeichen für **Regionsname, System** und **Beschreibung** Felder verwenden.

#### <a name="create-region"></a>Region erstellen

Um eine Region zu erstellen, wählen Sie die Schaltfläche **Erstellen**, wählen Sie ein **System** und geben Sie dann **Regionsname** und **Beschreibung:** ein

![Region erstellen](media/portal-admin-create-region.png)

#### <a name="delete-region"></a>Region löschen

Um eine Region zu löschen, wählen Sie das Dropdown-Menü und wählen Sie dann **Löschen** Option:

![Region löschen](media/portal-admin-delete-region.png)

Sie werden aufgefordert, die Löschung zu bestätigen, bevor die Region gelöscht wird:

![Region löschen bestätigen](media/portal-admin-delete-region-confirm.png)

### <a name="facilities"></a>Facilities

Sie können eine **Einrichtung** hinzufügen oder löschen, indem Sie das Formular **Einrichtungen** verwenden. Wenn Sie **Einrichtungen** wählen, werden alle vorhandenen **Einrichtungen** mit Region, Bezirk und anderen Details angezeigt:

![Löschen bestätigen](media/portal-admin-add-facility.png)

#### <a name="search-existing-facilities"></a>Suche in bestehenden Einrichtungen

Geben Sie einen Text in das Suchfeld ein, um nach System zu suchen und die Liste der Einrichtungen auf dem Formular zu filtern. Sie können die Platzhaltersuche (**\***) in Kombination mit Textzeichen für die Felder **Einrichtungsname**, **Region** und **Landname** verwenden.

#### <a name="create-facility"></a>Einrichtung erstellen

Um eine Einrichtung zu erstellen, wählen Sie die Schaltfläche **Erstellen**:

![Einrichtung erstellen](media/portal-admin-create-facility.png)

##### <a name="options-and-description"></a>Optionen und Beschreibung

| **Optionsname**                                | **Beschreibung**                                                                                                                                                                                            |
|------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name des Raums                                  | Name der Einrichtung.                                                                                                                                                                                      |
| Region                                         | Wählen Sie eine Region aus, der diese Einrichtung zugeordnet ist.                                                                                                                                                          |
| Gesamte Kapazität lizenzierter Betten                   | Gesamte lizenzierte Bettenkapazität, im Zahlenformat.                                                                                                                                                             |
| Gesamte Kapazität der IPS-Betten (Luftübertragungsisolation)            | Anzahl der gesamten Intensivbetten auf der Intensivstation in AIIR (Airborne Infect Isolation Room).                                                                                                                                         |
| Gesamte Kapazität der derzeit verwendeten Akutversorgungsbetten (Luftübertragungsisolationsräume)     | Gesamtkapazität an Akutbetten (AIIR), in Zahlenformat.                                                                                                                                                   |
| Gesamte Kapazität der Beatmungsgeräte                     | Gesamtkapazität des Beatmungsgeräts, im Zahlenformat.                                                                                                                                                               |
| Liste des Verbrauchsmaterials | Wählen Sie [Betriebsmittelliste](#supplies-list-for-a-facility), um Artikel aus den in der Einrichtung verfügbaren Betriebsmitteln auszuwählen. |
| DOH-Nummer                                     | Die Nummer des Gesundheitsministeriums für diese Einrichtung.                                                                                                                                                         |
| Folgt Tropfenprotokoll                       | Wählen Sie **Ja**/**Nein**. Bezieht sich auf die Einrichtung nach Tröpfchenvorsichtsmaßnahmen für Patienten, von denen bekannt ist oder vermutet wird, dass sie mit Krankheitserregern infiziert sind, die durch Atemtröpfchen übertragen werden, wie z.B. in COVID-19-Fällen. |
| Gesamte Kapazität der Betten für plötzlichen Anstieg                      | Gesamtkapazität der Notfallbetten, im Zahlenformat. Operationsbetten sind Betten, die über die lizenzierte Bettenkapazität hinaus besetzt werden können, wenn Patienten aufgenommen werden müssen                                               |
| Gesamte Kapazität der IPS-Betten (Nicht-Luftübertragungsisolation)        | Anzahl der ICU-Betten insgesamt (nicht-AIIR).                                                                                                                                                                       |
| Gesamte Kapazität der derzeit verwendeten Akutversorgungsbetten (Nicht-Luftübertragungsisolation) | Gesamtkapazität an Akutbetten (nicht AIIR-Betten), im Zahlenformat.                                                                                                                                               |
| Gesamtkapazität der Leichenhalle | Gesamtkapazität der Leichenhalle für die Einrichtung. **Anmerkung**: Wenn sie auf mindestens 1 gesetzt wird, bewirkt dies, dass Feld *Anzahl der derzeit benutzten Betten* für das Formular **Bettkapazität** der Einrichtung zur Verfügung steht.
| Einrichtungsadresse                               | Straße, Stadt, Bezirk, Bundesland und Postleitzahl für den Standort der Einrichtung.                                                                                                                                        |

##### <a name="supplies-list-for-a-facility"></a>Verbrauchsmaterialliste für eine Einrichtung

Wenn Sie **Betriebsmittelliste** wählen, können Sie einzelne Betriebsmittel und **Speichern** die Liste auswählen, um die verfügbaren Betriebsmittel für die Einrichtung zuzuordnen:

![Liste des Verbrauchsmaterials für die Einrichtung](media/portal-admin-add-facility-supplies.png)

#### <a name="delete-facility"></a>Einrichtung löschen

Um eine Einrichtung zu löschen, wählen Sie das Dropdown-Menü und dann die Option **Löschen**:

![Einrichtung löschen](media/portal-admin-delete-facility.png)

Sie werden aufgefordert, die Löschung zu bestätigen, bevor die Einrichtung gelöscht wird:

![Einrichtung löschen bestätigen](media/portal-admin-delete-facility-confirm.png)

#### <a name="edit-facility"></a>Einrichtung bearbeiten

Um eine Anlage zu löschen, wählen Sie das Dropdown-Menü und wählen Sie dann die Option **Bearbeiten**:

![Einrichtung bearbeiten](media/portal-admin-delete-facility.png)

Aktualisieren Sie die Felder und wählen Sie **Senden**, um die Änderungen zu speichern.

## <a name="get-insights"></a>Insights abrufen

Wenn Sie Mitglied der Rolle **Berichtsbetrachter** sind, sehen Sie die Option zur Anzeige von **Dashboards**:

![Erkenntnisse gewinnen](media/portal-admin-get-insights.png)

### <a name="dashboards-overview"></a>Übersicht Dashboards

Dashboards stehen für die folgenden Einblicke zur Verfügung:

- [System auf einen Blick](#system-at-a-glance)

- [COVID-19 Patientendaten](#covid-19-patient-details)

- [Angaben zur Bettenkapazität](#bed-capacity-details)

- [Ausstattungsdetails](#equipment-details)

- [Ausrüsterdetails](#equipment-details)

- [Datengesundheits-Scorecard](#data-health-scorecard)

#### <a name="working-with-reports-in-power-bi"></a>Mit Berichten in Power BI arbeiten

Bevor Sie mit der Durchsicht der verfügbaren Dashboards beginnen, machen Sie sich mit den allgemeinen Konzepten und Richtlinien zur Berichtsanzeige vertraut:

- Durch Auswahl des Informationssymbols (i) in einem der zusammengefassten Bereiche gelangen Sie zur entsprechenden Detailseite für den Bereich.

- Sie können auch andere Aktionen mit Berichten durchführen, z.B. Daten filtern und sortieren, den Bericht nach PDF und PowerPoint exportieren, ein Spotlight hinzufügen usw. Ausführliche Informationen über Berichtsfunktionen in Power BI finden Sie unter [Berichte in Power BI](https://docs.microsoft.com/power-bi/consumer/end-user-reports).

- Die letzten oder zuletzt aktualisierten Spalten in einigen dieser Berichte zeigen Datum und Uhrzeit der letzten Aktualisierung der Daten an. Es ist auch einfach, die Aktualität zu identifizieren, indem Sie die Farbe der Datums- und Uhrzeitwerte in diesen Spalten ansehen:

- **Schwarz:** Daten werden vor weniger als 20 Stunden aktualisiert

- **Grau:** Daten werden vor 20 - 24 Stunden aktualisiert

- **Rot:** Daten werden vor mehr als 24 Stunden aktualisiert

### <a name="system-at-a-glance"></a>System im Überblick

Betrachten Sie das gesamte **Krankenhaussystem** zugehörige Statistiken in einer Ansicht mit **System auf einen Blick** Dashboard:

![Informationsleiste](media/portal-admin-powerbi-reports.png)

Das Dashboard zeigt eine Zusammenfassung für Folgendes an:

- **COVID-19 Statistiken**: Sehen Sie sich die COVID-19-Patientenübersicht in Zahlen an, mit Gesamtzahl der Patienten, der untersuchten Patienten, der positiven und der intubierten Patienten.

- **Bettkapazität**: Betrachten Sie die zusammengefassten Daten mit **Verfügbarkeit** und **Belegung** für lizenzierte, ICU-, Akut- und Surge-Kategorien.

- **Bettverfügbarkeit nach Bezirk**: Anzeige der Bettenverfügbarkeit mit der Gesamtzahl der Betten, der Verfügbarkeit von Intensiv-/Akut-/Schwellenbetten und der Gesamtverfügbarkeit aller Betten in allen Bezirken.

- **Vorräte**: Betrachten Sie die Versorgungsinformationen mit tagesaktuellen Informationen für jedes einzeln.

- **Ausrüstung**: Zeigen Sie die Zusammenfassungsnummern für Beatmungsgeräte und Ausrüstung mit Verfügbarkeit, in Betrieb und benötigt an.

### <a name="covid-19-patient-details"></a>Angaben zum COVID-19-Patienten

Anzeigen von COVID-19-bezogenen Patientendetails wie z.B. Zusammenfassung der COVID-PUIs, Positivbefunde, Intubationen. Das Dashboard zeigt unten auch Details auf Länderbasis an.

Sie können die Bezirke auch auf einer Karte anzeigen, und die Bezirke sind zur Trennung farblich gekennzeichnet. Ein Diagramm unten rechts im Dashboard zeigt COVID-19-Positive und PUIs mit Zeitlinien, die die jüngsten und vergangenen Trends erklären:

![Patientendetails](media/portal-admin-powerbi-patients.png)

#### <a name="map"></a>Plan

Fahren Sie mit der Maus über einen Bezirk innerhalb der Karte, um die Bezirks-spezifischen COVID-19 PUIs, Positiv- und Intubationsnummern anzuzeigen:

![Patienten-Karte](media/portal-admin-powerbi-map.png)

Auf ähnliche Weise können Sie mit der Maus über das Zeitliniendiagramm fahren, um datumsbezogene Zahlen in der QuickInfo anzuzeigen, während Sie sich über die Daten bewegen.

### <a name="bed-capacity-details"></a>Details zur Bettenkapazität

Betrachten Sie bettbezogene Erkenntnisse, wie z.B. die Verfügbarkeit von Betten mit lizenzierten, Akut-, AIIR/Non-AAIR-, Chirurgie- und ICU-Nummern. Sie können sich auch die Details in Tabellenform unten mit den Bettdaten pro County und in Prozentangaben anzeigen lassen. Die Karte ist für Bezirke farblich kodiert, wobei die Farbe für niedrigere Zahlen heller ist und bei Dunkelheit mit zunehmender Zahl zunimmt. Das Diagramm unten rechts zeigt Belegungsunterschiede auf der Grundlage von Daten für die Trendanalyse:

![Bettenkapazität](media/portal-admin-powerbi-bed-capacity.png)

#### <a name="map"></a>Plan

Wenn Sie mit der Maus über einen Kartenbereich fahren und auf einen Bezirk zeigen, können Sie die Bezirksbezogenen Informationen anzeigen:

![Karte der Bettenkapazität](media/portal-admin-powerbi-map1.png)

Auf ähnliche Weise können Sie mit der Maus über das Zeitliniendiagramm fahren, um datumsbezogene Zahlen in der QuickInfo anzuzeigen, während Sie sich über die Daten bewegen.

### <a name="equipment-details"></a>Ausstattungsdetails

Mit **Ausstattungsdetails** Dashboard können Sie Details zu den Geräten auf Länderbasis wie Verfügbarkeit und Verbrauch von Beatmungsgeräten anzeigen:

![Ausstattungsdetails](media/portal-admin-powerbi-equipment.png)

Oben links sehen Sie die Gesamtmenge der verfügbaren Geräte und unten links die detaillierte Tabelle. Die Karte zeigt bezirksspezifische Ausrüstungsdaten mit hellerer Farbe für geringere und dunklere Farbe für höhere Anforderungszahlen.

Das Zeitliniendiagramm unten rechts zeigt Einblicke in die Ausrüstung für eine datumsübergreifende Trendanalyse.

#### <a name="map"></a>Plan

Wenn Sie mit der Maus über einen Kartenbereich fahren und auf einen Bezirk zeigen, können Sie die Bezirksbezogenen Informationen anzeigen:

![Ausrüstungszuordnung](media/portal-admin-powerbi-equipment-map.png)

Auf ähnliche Weise können Sie mit der Maus über das Zeitliniendiagramm fahren, um datumsbezogene Zahlen in der QuickInfo anzuzeigen, während Sie sich über die Daten bewegen.

### <a name="supply-details"></a>Verbrauchsmaterialdetails

Mit **Versorgungsdetails** Dashboard können Sie die Versorgungsdetails pro Bezirk anzeigen, z.B. Verfügbarkeit und Verbrauch von Beatmungsgeräten:

![Verbrauchsmaterialdetails](media/portal-admin-powerbi-supply.png)

Auf der linken Seite sehen Sie die Versorgungsdetails auf der Grundlage von **Gesundheitssystem** Karte auf der rechten Seite und die Aufteilung der Versorgung im Diagrammformat auf der unteren Seite.

#### <a name="map"></a>Plan

Wenn Sie mit der Maus über einen Kartenbereich fahren und auf einen Bezirk zeigen, können Sie die Bezirksbezogenen Informationen anzeigen:

![Verbrauchsmaterialzuordnung](media/portal-admin-powerbi-supply-map.png)

Auf ähnliche Weise können Sie mit der Maus über das Zeitliniendiagramm fahren, um datumsbezogene Zahlen in der QuickInfo anzuzeigen, während Sie sich über die Daten bewegen.

### <a name="data-health-scorecard"></a>Daten-Status-Scorecard

Anzeige der Datenhygiene für eine ausgewählte Einrichtung unter Verwendung des **Datengesundheits-Scorecard** Dashboard. Wählen Sie eine Einrichtung aus der Liste der verfügbaren Einrichtungen und wählen Sie dann **Klicken Sie hier, um fortzufahren** um das Dashboard anzuzeigen:

![Wählen Sie eine Einrichtung](media/dashboard-data-health-facility-select.png)

Das Dashboard zeigt die Rangfolge der Datenaktualisierung, die prozentuale Datenaktualisierung und den Tagesstatus über alle Komponenten hinweg. Ein datumsweises Diagramm zeigt die Datenfertigstellung der ausgewählten Einrichtung im Vergleich zum Durchschnitt aller Einrichtungen für einen gegebenen Datensatz. Die Informationen zur Vollständigkeit der Daten in Bezug auf die Einrichtungen sind auch in tabellarischer Form mit einer Auflistung aller Einrichtungen für die letzte Woche verfügbar:

![Daten-Status-Scorecard](media/data-health-scorecard-dashboard.png)

## <a name="general-portal-options"></a>Allgemeine Portal-Optionen

[!include[cc-general-options](includes/cc-general-options.md)]

## <a name="issues-and-feedback"></a>Probleme und Feedback

- Um ein Problem mit der Lösung Regional Government Emergency Response and Monitoring zu melden, besuchen Sie <https://aka.ms/rer-issues>.

- Rückmeldungen über die Lösung Regional Government Emergency Response and Monitoring finden Sie unter <https://aka.ms/rer-feedback>.
