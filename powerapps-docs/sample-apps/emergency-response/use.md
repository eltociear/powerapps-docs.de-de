---
title: Verwenden der Hospital Emergency Response-App | Microsoft-Dokumentation
description: Durchlaufen verschiedener Apps und Komponenten für die Benutzer der Hospital Emergency Response-Beispiel-App-Vorlage
author: pankajarora-msft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/05/2020
ms.author: tapanm
ms.reviewer: pankar
searchScope:
- PowerApps
ms.openlocfilehash: fcb4d780d5b9a1f888f66270a5a4f65a2d83dba6
ms.sourcegitcommit: 604b6ea4be80c9dc9c2e21e24a497b69f683f2f2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "3229161"
---
# <a name="use-the-hospital-emergency-response-app"></a>Verwenden der Hospital Emergency Response-App

Das Krankenhauspersonal ist gefordert, eine Zunahme der Patientenzahlen zu bewältigen und gleichzeitig die Lieferkette im Notfall zu verwalten. Mithilfe der Hospital Emergency Response-Mobile App können Mitarbeiter an vorderster Front schnell Daten für Beatmungsgeräte, Personal, ausstehende Entlassungen und Patienten im Zusammenhang mit COVID-19 anzeigen und hinzufügen.

## <a name="prerequisites"></a>Voraussetzungen

Um mit der App zu beginnen, müssen Sie die Power Apps Mobile auf Ihrem Gerät über den App-Store des Geräts herunterladen.

- **Herunterladen** der [**Power Apps Mobile**](https://powerapps.microsoft.com/downloads)
    - Verwenden Sie den [**App-Store**](https://aka.ms/powerappsios) für **Apple**-Geräte mit iOS wie iPhone und iPad.
    - Verwenden Sie [**Google Play**](https://aka.ms/powerappsandroid) für **Android**-Geräte.
- Stellen Sie sicher, dass Ihre Organisation die Hospital Emergency Response-App bereitgestellt und konfiguriert hat, wie erläutert in [Bereitstellen und Konfigurieren der App](deploy-configure.md).

Nachdem Sie die Power Apps Mobile installiert haben, öffnen Sie die App von Ihrem Gerät aus und melden Sie sich mit Ihrem Azure Active Directory-Konto des Unternehmens an. Sie können alle Apps anzeigen, die Ihnen von Ihrer Organisation freigegeben wurden, sobald Sie sich angemeldet haben. Weitere Informationen finden Sie unter [Power Apps-Anmeldung für Mobilgeräte](https://docs.microsoft.com/powerapps/user/run-app-client#open-power-apps-and-sign-in).

## <a name="demo-use-the-hospital-emergency-response-app"></a>Demo: Verwenden der Hospital Emergency Response-App

Sehen Sie sich an, wie Sie die Hospital Emergency Response-App verwenden.

<br/>

> [!VIDEO https://www.youtube.com/embed/H1u6SYt3UsQ]

## <a name="hospital-emergency-response-app"></a>Hospital Emergency Response-App

![Hospital Emergency Response-App](media/use/app-launcher.png)

Die Hospital Emergency Response-Mobile App ist modular aufgebaut und enthält je nach Rolle unterschiedliche Apps. Öffnen Sie die Hospital Emergency Response-Mobile App über die Power Apps Mobile, wählen Sie Ihr **Krankenhaussystem**, **Region, Einrichtung** und dann **Weiter** aus, um loszulegen.

> [!NOTE]
> Wenn Sie die Hospital Emergency Response-Mobile App oder eine ihrer Komponenten das *erste Mal* starten, werden Sie um Ihre Zustimmung für den Zugriff der App auf Ihr *Office 365-Benutzer*-Profil und Ihren *Standort* gebeten. Sie müssen die Option **Zulassen** auswählen, bevor Sie die ausgewählte App verwenden können. Weitere Informationen finden Sie unter [Zustimmung geben](https://docs.microsoft.com/powerapps/user/run-app-client#give-consent).

## <a name="app-components"></a>App-Komponenten

![Komponenten der Hospital Emergency Response-Mobile App](media/use/app-components.png)

Die Hospital Emergency Response-Beispiellösungs-App besteht aus mehreren Apps für eine verbesserte Benutzererfahrung. Abhängig von Ihrer Rolle sehen Sie möglicherweise eine oder mehrere Komponenten in der **Hospital Emergency Response-App**.

- **Personal + Arbeitsgeräte**
    <br> Sammeln Sie den Status der RNs und der kritischen Ausrüstung nach Standort in dieser Einrichtung.

- **Bedarf**
    <br> Verfolgen Sie wichtigen Bedarf, um das Inventar effektiver zu verfolgen, zu verwalten und zu prognostizieren. 

- **Personalbedarf**
    <br> Sammeln Sie Personalanfragen nach Abteilung, Rolle und Dringlichkeit.

- **COVID-19-Statistiken**
    <br> Sammeln Sie den Status darüber, wie viele Patienten auf COVID-19 untersucht werden und wie viele positiv getestet wurden.

- **Entlassungsplanung**
    <br> Sammeln Sie Status und Projektionen zu Patientenentlassungen.

## <a name="staff--equipment"></a>Personal + Arbeitsgeräte

![Personal + Arbeitsgeräte](media/use/staff-equipment.png)

Senden Sie ein standortspezifisches Inventar für registrierte Krankenschwestern, Patienten und Arbeitsgeräte. Die Gebietsliste enthält alle Standorte, die für die in der **Hospital Emergency Response-App** ausgewählten Einrichtung spezifisch ist. Wählen Sie aus den verfügbaren Optionen den Standort aus, um andere Felder zu aktualisieren.

Geben Sie nach Auswahl eines Gebiets die erforderlichen Werte für die Felder ein, um die Datensätze in der Lösungsdatenbank zu speichern. Sie müssen nicht für jedes Feld auf dem Bildschirm Werte eingeben. Geben Sie eine Nummer für das Feld ein, das Sie in der Lösungsdatenbank speichern müssen.

Wenn Sie beispielsweise die Anzahl der als 3 angeforderten registrierten Krankenschwestern hinzufügen müssen, geben Sie 3 in das Feld **Registrierte Krankenschwestern im Dienst – Angefordert** ein und wählen Sie **Senden** aus. Wenn Sie auch verwendete Beatmungsgeräte als 6 aktualisieren müssen, geben Sie 3 in das Feld **Registrierte Krankenschwestern im Dienst – Angefordert** und dann 6 in **Beatmungsgeräte** unter **Arbeitsgeräte im Einsatz** ein. Wählen Sie anschließend **Senden** aus.

Wählen **Zurück** von oben links, wenn Sie zurück zur **Hospital Emergency Response-App** gehen möchten, ohne Änderungen zu senden. Die Schaltfläche **Senden** sendet die von Ihnen eingegebenen Werte.

Nachdem Sie die Daten übermittelt haben, haben Sie die Möglichkeit, zur App **Personal + Ausrüstung** zurückzugehen, um einen weiteren Datensatz mit der Schaltfläche **Weiteren nachverfolgen** zu erstellen. Wählen Sie **Home** aus, um zur **Hospital Emergency Response-App** zurückzugehen.

### <a name="fields-and-description"></a>Felder und Beschreibung

| **Optionsname**               | **Beschreibung**                                                                                   |
|-------------------------------|---------------------------------------------------------------------------------------------------|
| Standort                      | Name und Typ des Raums, der Station oder eines anderen speziellen Standortes innerhalb der ausgewählten Einrichtung. |
| Anzahl der Patienten            | Aktuelle Gesamtzahl der Patienten am ausgewählten Standort.                                        |
| **Registrierte Krankenschwestern im Dienst** |                                                                                                   |
| *Partner*                    | Anzahl der am ausgewählten Standort anwesenden registrierten Krankenschwesterpartner.                             |
| *Angefordert*                   | Anzahl der für den ausgewählten Standort angeforderten registrierten Krankenschwestern.                                  |
| *Zugewiesen*                    | Anzahl der registrierten Krankenschwestern, die dem ausgewählten Standort zugewiesen sind.                                    |
| *Nicht zugewiesen*                  | Anzahl der registrierten Krankenschwestern, die am ausgewählten Standort keiner Aufgabe zugewiesen sind.                    |
| **Arbeitsgeräte im Einsatz**          |                                                                                                   |
| *Beatmungsgeräte*                 | Anzahl der am ausgewählten Standort verwendeten Beatmungsgeräte.                                            |
| *PAPR-Hauben*                  | Anzahl der am ausgewählten Standort verwendeten motorbetriebenen Luftreinigungs-Atemschutzhauben.                 |
| *PAPR-Gürtel*                  | Anzahl der am ausgewählten Standort verwendeten motorbetriebenen Luftreinigungs-Atemschutzgürtel.                 |
| *PAPR-Ladegeräte*               | Anzahl der am ausgewählten Standort verwendeten motorbetriebenen Luftreinigungs-Atemschutzladegeräte.              |


## <a name="supplies"></a>Bedarf

![Bedarf](media/use/supplies.png)

Zeigen Sie das Bedarfsinventar mit der App **Bedarf** an. Über diese App können Sie die Mengen der Bedarfskomponenten im gesamten Einrichtungsinventar und die tägliche Verbrauchsrate aktualisieren.

> [!NOTE]
> Geben Sie Werte in beide Felder **Auf Lager** und **Verwendet in letzten 24 Stunden** ein, bevor Sie **Senden** auswählen.

Wählen **Zurück** von oben links, wenn Sie zurück zur **Hospital Emergency Response-App** gehen möchten, ohne Änderungen zu senden. Die Schaltfläche **Senden** sendet die von Ihnen eingegebenen Werte. Wählen Sie nach dem Senden **Home** aus, um zur **Hospital Emergency Response-App** zurückzugehen.

### <a name="fields-and-description"></a>Felder und Beschreibung

Die Artikelliste der Bedarfs-App kann je nach den Anforderungen Ihres Unternehmens unterschiedlich sein. Beschreibungen der Bedarfsnamen finden Sie in den Ressourcen Ihrer Organisation.

IT-Administratoren können die Artikelliste der Bedarfs-App mithilfe der modellgesteuerten App für Power Apps hinzufügen oder aktualisieren. Weitere Informationen finden Sie unter [Konfigurationsanleitung](deploy-configure.md).

> [!NOTE]
> Die Artikelwerte des Bedarfsinventars müssen im Zahlenformat vorliegen.

## <a name="staffing-needs"></a>Personalbedarf

![Personalbedarf](media/use/staffing-needs.png)

Sammelt Arbeitspoolanforderungen für die ausgewählte Einrichtung. Stellen Sie sicher, dass die als *erforderlich* (*) gekennzeichneten Felder ausgefüllt sind, bevor Sie die Arbeitspoolanforderung für eine Einrichtung senden können.

Wählen **Zurück** von oben links, wenn Sie zurück zur **Hospital Emergency Response-App** gehen möchten, ohne Änderungen zu senden. Die Schaltfläche **Senden** sendet die von Ihnen eingegebenen Werte. Wählen Sie nach dem Senden **Home** aus, um zur **Hospital Emergency Response-App** zurückzugehen.

### <a name="fields-and-description"></a>Felder und Beschreibung

| **Feldname**           | **Beschreibung**                                                                            |
|--------------------------|--------------------------------------------------------------------------------------------|
| Abteilung               | Name der Abteilung, die die Arbeitsanforderung anfordert. In diesem Feld ist ein Eintrag *erforderlich*.             |
| Abteilungsstandort      | Standort der Abteilung.                                                                |
| Anforderungstyp             | Art der Arbeitsanforderung wie klinisch und nicht klinisch. In diesem Feld ist ein Eintrag *erforderlich*. |
| Rolle benötigt              | Rolle der angeforderten Arbeit wie Sitter oder eine registrierte Krankenschwester.                          |
| Jetzt oder nächste Schicht benötigt | Wählen Sie eine Schicht für die angeforderte Arbeit, die aktuelle Schicht oder eine bevorstehende Schicht aus.                |
| Wie viele                 | Wie viele Ressourcen benötigt werden, im Zahlenformat.                |
| Details                  | Beschreiben Sie zusätzliche Details oder Kommentare für die Arbeitspoolanforderung.                        |

## <a name="covid-19-stats"></a>COVID-19-Statistiken

![COVID-19-Statistiken](media/use/covid19-stats.png)

Senden Sie COVID-19-spezifische Details mit der App **COVID-19-Statistiken**. Sie können die ortsspezifische Anzahl der untersuchten Patienten und der positiv getesteten Patienten aktualisieren.

Sie können auch einen weiteren Standort mit der Schaltfläche **+ Weiteren Standort hinzufügen** hinzufügen, um Statistiken für mehr als einen Standort zu senden.

Wählen **Zurück** von oben links, wenn Sie zurück zur **Hospital Emergency Response-App** gehen möchten, ohne Änderungen zu senden. Die Schaltfläche **Senden** sendet die von Ihnen eingegebenen Werte.

Nachdem Sie die Daten übermittelt haben, haben Sie die Möglichkeit, zur App **COVID-19-Statistiken** zurückzugehen, um einen weiteren Datensatz mit der Schaltfläche **Weiteren nachverfolgen** zu erstellen. Wählen Sie **Home** aus, um zur **Hospital Emergency Response-App** zurückzugehen.

### <a name="fields-and-description"></a>Felder und Beschreibung

| **Feldname**  | **Beschreibung**                                                                                    |
|-----------------|----------------------------------------------------------------------------------------------------|
| Standort        | Name und Typ des Raums, der Station oder eines anderen speziellen Standortes innerhalb der ausgewählten Einrichtung.  |
| PUIs            | Anzahl der untersuchten Patienten.                                                            |
| Positiv        | Anzahl der mit COVID-19 positiven Patienten.                                                         |

## <a name="discharge-planning"></a>Entlassungsplanung

![Entlassung](media/use/discharge.png)

Übermitteln Sie die Entlassungsinformationen und den Patientenstatus insgesamt mithilfe der App **Entlassungsplanung**. Sie können die Entlassungsdetails für die letzten 24 Stunden, die aktuellen Entlassungsbarrieren und die Aufteilung der Barrieren aktualisieren.

Wählen **Zurück** von oben links, wenn Sie zurück zur **Hospital Emergency Response-App** gehen möchten, ohne Änderungen zu senden. Die Schaltfläche **Senden** sendet die von Ihnen eingegebenen Werte. Wählen Sie nach dem Senden **Home** aus, um zur **Hospital Emergency Response-App** zurückzugehen.

### <a name="fields-and-description"></a>Felder und Beschreibung

| **Feldname**            | **Beschreibung**                                                    |
|---------------------------|--------------------------------------------------------------------|
| Autorisierung             | Anzahl der Patienten im Autorisierungsverfahren.                   |
| Langlebige medizinische Arbeitsgeräte | Anzahl der Patienten, die die langlebigen medizinischen Arbeitsgeräte verwenden.            |
| Vormundschaft              | Anzahl der Patienten unter Vormundschaft.                             |
| Heim- und Pflegedienste | Anzahl der Patienten, die Heim- und Pflegedienste nutzen.               |
| Unterbringung                 | Anzahl der benötigten Unterbringungen.                                       |
| Qualifizierte Pflegeeinrichtungen  | Anzahl qualifizierter Pflegeeinrichtungen.                              |
| **Entlassungen**            |                                                                    |
| Letzte 24 Stunden                 | Anzahl der Patienten, deren Entlassung in den letzten 24 Stunden erwartet wird.  |
| Voraussichtlich nächste 24 Stunden          | Anzahl der Patienten, die in den letzten 24 Stunden entlassen wurden.                    |

## <a name="other-options"></a>Weitere Möglichkeiten

In diesem Abschnitt werden weitere Aktionen erläutert, die Sie mit den Komponenten der Hospital Emergency Response-Mobile App ausführen können.

### <a name="end-shift---sign-out"></a>Schicht beenden – abmelden

Sie können sich über das Profilsymbol oben links auf dem Bildschirm von der App abmelden.  

![Abmelden](media/use/sign-out.png)

Wählen Sie die Schaltfläche **Schicht beenden** aus, um Ihre Sitzung zu beenden und sich abzumelden.

> [!NOTE]
> *Schicht beenden* ist möglicherweise nicht verfügbar, wenn Ihr IT-Administrator die Gerätefreigabe deaktiviert hat.

### <a name="provide-feedback"></a>Feedback geben

Sie können Ihr Feedback mit der Option **Feedback geben** aus einer beliebigen Komponente der Hospital Emergency Response-Mobile App teilen. Um Ihr Feedback zu teilen, wählen Sie Ihr Profil oben links und dann die Schaltfläche **Feedback geben** aus:

![Feedback geben](media/use/give-feedback.png)

Wenn Sie **Feedback geben** auswählen, haben Sie die Möglichkeit, ein Lob, eine Idee oder ein Problem mit der App zu teilen.

### <a name="switch-facility"></a>Einrichtung wechseln

![Einrichtung wechseln](media/use/switch-facility.png)

Wechseln Sie die Einrichtung jederzeit, indem Sie den Namen der Einrichtung oben rechts auf dem Bildschirm auswählen. Nachdem Sie den Standortnamen ausgewählt haben, gelangen Sie zum Bildschirm der **Hospital Emergency Response-App**, auf dem Sie ein anderes Krankenhaus, eine andere Region oder eine andere Einrichtung auswählen können.

## <a name="issues-and-feedback"></a>Probleme und Feedback

- Um ein Problem mit der Hospital Emergency Response-Beispiel-App zu melden, navigieren Sie zu <https://aka.ms/emergency-response-issues>.

- Feedback zur Hospital Emergency Response-Beispiel-App finden Sie unter <https://aka.ms/emergency-response-feedback>.


