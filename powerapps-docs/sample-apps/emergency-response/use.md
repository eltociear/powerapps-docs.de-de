---
title: Die mobile App für Notfallmaßnahmen im Krankenhaus verwenden | Microsoft Docs
description: Durchlaufen verschiedener Apps und Komponenten für die Benutzer der Hospital Emergency Response-Beispiel-App-Vorlage
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
ms.locfileid: "3265014"
---
# <a name="use-the-hospital-emergency-response-mobile-app"></a>Die mobile App für Notfallmaßnahmen im Krankenhaus verwenden

Das Krankenhauspersonal ist gefordert, eine Zunahme der Patientenzahlen zu bewältigen und gleichzeitig die Lieferkette im Notfall zu verwalten. Mithilfe der Hospital Emergency Response-Mobile App können Mitarbeiter an vorderster Front schnell Daten für Beatmungsgeräte, Personal, ausstehende Entlassungen und Patienten im Zusammenhang mit COVID-19 anzeigen und hinzufügen.

## <a name="prerequisites"></a>Voraussetzungen

Um mit der mobilen App zu beginnen, müssen Sie Power Apps Mobile auf Ihr Gerät über den App Store des Geräts herunterladen.

- **Herunterladen** der [**Power Apps Mobile**](https://powerapps.microsoft.com/downloads)
    - Verwenden Sie den [**App-Store**](https://aka.ms/powerappsios) für **Apple**-Geräte mit iOS wie iPhone und iPad.
    - Verwenden Sie [**Google Play**](https://aka.ms/powerappsandroid) für **Android**-Geräte.
- Stellen Sie sicher, dass Ihre Organisation die Hospital Emergency Response-App bereitgestellt und konfiguriert hat, wie erläutert in [Bereitstellen und Konfigurieren der App](deploy-configure.md).

Nachdem Sie die Power Apps Mobile installiert haben, öffnen Sie die App von Ihrem Gerät aus und melden Sie sich mit Ihrem Azure Active Directory-Konto des Unternehmens an. Sie können alle Apps anzeigen, die Ihnen von Ihrer Organisation freigegeben wurden, sobald Sie sich angemeldet haben. Weitere Informationen finden Sie unter [Power Apps-Anmeldung für Mobilgeräte](https://docs.microsoft.com/powerapps/user/run-app-client#open-power-apps-and-sign-in).

## <a name="demo-use-the-hospital-emergency-response-mobile-app"></a>Demo: Die mobile App für Notfallmaßnahmen im Krankenhaus verwenden

Sehen Sie sich an, wie Sie die Hospital Emergency Response-App verwenden.

<br/>

> [!VIDEO https://www.youtube.com/embed/H1u6SYt3UsQ]

## <a name="hospital-emergency-response-mobile-app"></a>Mobile App für Notfallmaßnahmen im Krankenhaus

![Hospital Emergency Response-App](media/use/app-launcher.png)

Die Hospital Emergency Response-Mobile App ist modular aufgebaut und enthält je nach Rolle unterschiedliche Apps. Öffnen Sie die Hospital Emergency Response-Mobile App über die Power Apps Mobile, wählen Sie Ihr **Krankenhaussystem**, **Region, Einrichtung** und dann **Weiter** aus, um loszulegen.

> [!NOTE]
> Wenn Sie die Hospital Emergency Response-Mobile App oder eine ihrer Komponenten das *erste Mal* starten, werden Sie um Ihre Zustimmung für den Zugriff der App auf Ihr *Office 365-Benutzer*-Profil und Ihren *Standort* gebeten. Sie müssen die Option **Zulassen** auswählen, bevor Sie die ausgewählte App verwenden können. Weitere Informationen finden Sie unter [Zustimmung geben](https://docs.microsoft.com/powerapps/user/run-app-client#give-consent).

## <a name="app-components"></a>App-Komponenten

![Komponenten der Hospital Emergency Response-Mobile App](media/use/app-components.png)

Die Hospital Emergency Response-Beispiellösungs-App besteht aus mehreren Apps für eine verbesserte Benutzererfahrung. Abhängig von Ihrer Rolle sehen Sie möglicherweise eine oder mehrere Komponenten in der **Hospital Emergency Response-App**.

- **Bettenkapazität**
    <br> Sammeln Sie Bettinformationen wie lizenzierte Betten, Intensivbetten und andere Daten zur Bettenkapazität.

- **COVID-19-Statistiken**
    <br> Sammeln Sie den Status darüber, wie viele Patienten auf COVID-19 untersucht werden und wie viele positiv getestet wurden.

- **Arbeitsgerät**
    <br> Verfolgen Sie Geräteinformationen wie Beatmungsgeräte, NIPPV und PAPR.

- **Personal**
    <br> Sammeln Sie die Anzahl der Patienten und RN-Statusinformationen, z. B. „Partner“, „Zugewiesen“, „Angefordert“ und „Nicht zugewiesen“.

- **Bedarf**
    <br> Verfolgen Sie wichtigen Bedarf, um das Inventar effektiver zu verfolgen, zu verwalten und zu prognostizieren. 

- **Personalbedarf**
    <br> Sammeln Sie Personalanfragen nach Abteilung, Rolle und Dringlichkeit.

- **Entlassungsplanung**
    <br> Sammeln Sie Status und Projektionen zu Patientenentlassungen.

> [!NOTE]
> Standardmäßig können Sie Informationen in den folgenden Apps auf der Ebene *Standort* verfolgen: **COVID-19-Statistiken**, **Ausrüstung**, und **Personal**. In den restlichen Apps können Sie Informationen standardmäßig unter *Einrichtung* verfolgen. Ihr Administrator kann bei Bedarf die Standardverfolgungsebene ändern. Weitere Informationen: [Verwalten der Nachverfolgungsebene für mobile Apps](configure-data-reporting.md#manage-tracking-level-for-mobile-apps)

## <a name="bed-capacity"></a>Bettenkapazität

![Bettenkapazität](media/use/bed-capacity.png)

Senden Sie bettbezogene Informationen wie lizenzierte Betten, Betten auf der Intensivstation (AIIR/Nicht-AIIR), Betten für Akutversorgung (AIIR/Nicht-AIIR) und ob die ausgewählte Einrichtung mit voller Lizenzbettkapazität besetzt ist.

Wählen **Zurück** von oben links, wenn Sie zurück zur **Hospital Emergency Response-App** gehen möchten, ohne Änderungen zu senden. Die Schaltfläche **Senden** sendet die von Ihnen eingegebenen Werte.

Nachdem Sie die Daten übermittelt haben, haben Sie die Möglichkeit, zur App **Bettkapazität** zurückzukehren, um einen weiteren Datensatz mit der Schaltfläche **Andere nachverfolgen** zu erstellen. Wählen Sie **Home** aus, um zur **Hospital Emergency Response-App** zurückzugehen.

### <a name="fields-and-description"></a>Felder und Beschreibung

| **Optionsname**                                               | **Beschreibung**                                                                       |
|---------------------------------------------------------------|---------------------------------------------------------------------------------------|
| Wie viele lizenzierte Betten werden derzeit in dieser Einrichtung verwendet? | Anzahl der lizenzierten Betten, die derzeit in dieser Einrichtung verwendet werden.                            |
| Anzahl derzeit verwendeter Intensivbetten (Luftübertragungsisolationsräume)               | Anzahl derzeit verwendeter Intensivbetten (Luftübertragungsisolationsräume).                                      |
| Anzahl derzeit verwendeter Intensivbetten (Nicht-Luftübertragungsisolationsräume)           | Anzahl derzeit verwendeter Intensivbetten (Nicht-Luftübertragungsisolationsräume).                                  |
| Anzahl derzeit verwendeter Akutversorgungsbetten (Luftübertragungsisolationsräume)        | Anzahl derzeit verwendeter Akutversorgungsbetten (Luftübertragungsisolationsräume).                               |
| Anzahl derzeit verwendeter Akutversorgungsbetten (Nicht-Luftübertragungsisolationsräume)    | Anzahl derzeit verwendeter Akutversorgungsbetten (Nicht-Luftübertragungsisolationsräume).                           |
| Ist Ihre Einrichtung mit einer voll lizenzierten Bettenkapazität besetzt?    | Ja/Nein: Wenn die Antwort Nein lautet, können Sie alle zutreffenden Gründe auswählen: <br> - Personal <br> - Platz <br> - PSA <br> - Arbeitsgerät <br> - Geringes Patientenvolumen |
| Können Sie einen plötzlichen Anstieg über lizenzierte Betten hinaus bewältigen?              | Ja/Nein: Wenn die Antwort Nein lautet, können Sie alle zutreffenden Gründe auswählen: <br> - Personal <br> - Platz <br> - PSA <br> - Arbeitsgerät <br> - Geringes Patientenvolumen  |
| Anzahl derzeit verwendeter Betten für plötzlichen Anstieg                         | Anzahl derzeit verwendeter Betten für plötzlichen Anstieg.                                                |

## <a name="covid-19-stats"></a>COVID-19-Statistiken

![COVID-19-Statistiken](media/use/covid19-stats.png)

Senden Sie COVID-19-spezifische Details mit der App **COVID-19-Statistiken**. Sie können die ortsspezifischen Patientendetails wie PUIs, positive, intubierte und entlassene Patienten aktualisieren.

Wählen **Zurück** von oben links, wenn Sie zurück zur **Hospital Emergency Response-App** gehen möchten, ohne Änderungen zu senden. Die Schaltfläche **Senden** sendet die von Ihnen eingegebenen Werte.

Nachdem Sie die Daten übermittelt haben, haben Sie die Möglichkeit, zur App **COVID-19-Statistiken** zurückzugehen, um einen weiteren Datensatz mit der Schaltfläche **Weiteren nachverfolgen** zu erstellen. Wählen Sie **Home** aus, um zur **Hospital Emergency Response-App** zurückzugehen.

### <a name="fields-and-description"></a>Felder und Beschreibung

| **Feldname**  | **Beschreibung**                                                                                    |
|-----------------|----------------------------------------------------------------------------------------------------|
| Standort        | Name und Typ des Raums, der Station oder eines anderen speziellen Standortes innerhalb der ausgewählten Einrichtung.  |
| PUIs            | Anzahl der untersuchten Patienten.                                                            |
| Positiv        | Anzahl der mit COVID-19 positiven Patienten.                                                         |
| Intubiert        | Anzahl intubierter Patienten.                                                         |
| Entlassen        | Anzahl der entlassenen Patienten mit COVID-19.                                                         |

## <a name="equipment"></a>Arbeitsgerät

![Arbeitsgerät](media/use/equipment.png)

Senden Sie ortsspezifische Gerätedetails mit der App **Ausrüstung**. Sie können die Anzahl der verwendeten Geräte wie Beatmungsgeräte, NIPPV und PAPR aktualisieren.

Wählen **Zurück** von oben links, wenn Sie zurück zur **Hospital Emergency Response-App** gehen möchten, ohne Änderungen zu senden. Die Schaltfläche **Senden** sendet die von Ihnen eingegebenen Werte.

Nachdem Sie die Daten übermittelt haben, haben Sie die Möglichkeit, zur App **Ausrüstung** zurückzukehren, um einen weiteren Datensatz mit der Schaltfläche **Andere nachverfolgen** zu erstellen. Wählen Sie **Home** aus, um zur **Hospital Emergency Response-App** zurückzugehen.

### <a name="fields-and-description"></a>Felder und Beschreibung

| **Feldname**  | **Beschreibung**                                                                                    |
|-----------------|----------------------------------------------------------------------------------------------------|
| Standort        | Name und Typ des Raums, der Station oder eines anderen speziellen Standortes innerhalb der ausgewählten Einrichtung.  |
| Beatmungsgeräte            | Anzahl der derzeit verwendeten Beatmungsgeräte.                                                            |
| NIPPV (Nichtinvasive Überdrückbeatmung)        | Anzahl der verwendeten nichtinvasiven Überdruckventilatoren.                                                         |
| PAPR-Gürtel        | Anzahl der verwendeten Atemschutzgurte mit Luftreinigung.                                                         |
| PAPR-Ladegeräte        | Anzahl der verwendeten Atemschutzladegeräte mit Luftreinigung.                                                         |
| PAPR-Hauben        | Anzahl der verwendeten Atemschutzhauben mit Luftreinigung.                                                         |

## <a name="staff"></a>Personal

![Personal](media/use/staff.png)

Senden Sie ein standortspezifisches Inventar für registrierte Krankenschwestern, Patienten und Arbeitsgeräte. Sie müssen nicht für jedes Feld auf dem Bildschirm Werte eingeben. Geben Sie eine Nummer für das Feld ein, das Sie in der Lösungsdatenbank speichern müssen.

Wenn Sie beispielsweise die Anzahl der angeforderten examinierten Krankenschwestern als 3 hinzufügen müssen, geben Sie 3 in das Feld **Examinierte Krankenschwestern im Dienst – Angefordert** ein und wählen Sie **Absenden**. Wenn Sie auch **Examinierte Krankenschwestern im Dienst – Zugewiesen** als 6 aktualisieren müssen, geben Sie 3 in das Feld **Examinierte Krankenschwestern im Dienst – Angefordert** ein, dann geben Sie 6 in **Examinierte Krankenschwestern im Dienst – Zugewiesen** ein und wählen Sie dann **Absenden** aus.

Wählen **Zurück** von oben links, wenn Sie zurück zur **Hospital Emergency Response-App** gehen möchten, ohne Änderungen zu senden. Die Schaltfläche **Senden** sendet die von Ihnen eingegebenen Werte.

Nachdem Sie die Daten übermittelt haben, haben Sie die Möglichkeit, zur App **Personal** zurückzukehren, um einen weiteren Datensatz mit der Schaltfläche **Andere nachverfolgen** zu erstellen. Wählen Sie **Home** aus, um zur **Hospital Emergency Response-App** zurückzugehen.

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
| **Nachverfolgung auf Einrichtungsebene** |                                                                                                   |
| % des derzeit abwesenden wichtigen Personals in dieser Einrichtung                  | Das Personal für die Grundversorgung fehlt derzeit im prozentualen Format der Gesamtsumme für **gesamte Einrichtung**.                    |

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

### <a name="app-feedback"></a>App-Feedback

Sie können Ihr Feedback mit der Option **App-Feedback** aus einer beliebigen mobilen Komponente der Notfalleinsatz-App teilen. Um Ihr Feedback zu teilen, wählen Sie Ihr Profil oben links aus und wählen Sie dann die Schaltfläche **Feedback senden** aus:

![Feedback geben](media/use/give-feedback.png)

Wenn Sie **App-Feedback** auswählen, haben Sie die Möglichkeit, ein Lob, eine Idee oder ein Problem mit der App zu teilen.

### <a name="switch-facility"></a>Einrichtung wechseln

![Einrichtung wechseln](media/use/switch-facility.png)

Wechseln Sie die Einrichtung jederzeit, indem Sie den Namen der Einrichtung oben rechts auf dem Bildschirm auswählen. Nachdem Sie den Standortnamen ausgewählt haben, gelangen Sie zum Bildschirm der **Hospital Emergency Response-App**, auf dem Sie ein anderes Krankenhaus, eine andere Region oder eine andere Einrichtung auswählen können.

## <a name="issues-and-feedback"></a>Probleme und Feedback

- Um ein Problem mit der Hospital Emergency Response-Beispiel-App zu melden, navigieren Sie zu <https://aka.ms/emergency-response-issues>.

- Feedback zur Hospital Emergency Response-Beispiel-App finden Sie unter <https://aka.ms/emergency-response-feedback>.


