---
title: Nutzen Regional Government Emergency Response and Monitoring-Portals | Microsoft Docs
description: Erfahren Sie, wie Sie das Portal Regional Government Emergency Response and Monitoring als Mitarbeiter im Gesundheitswesen nutzen können.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 05/04/2020
ms.author: tapanm
ms.reviewer: tapanm
searchScope:
- PowerApps
ms.openlocfilehash: 115cf6a5c1c622374de42230e07e09462cc6de41
ms.sourcegitcommit: c424a17b9c658f4571b5ea26ab6fc8a486051d44
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "3341750"
---
# <a name="use-the-regional-governmentemergency-response-and-monitoring-portal"></a>Nutzen des Regional Government Emergency Response and Monitoring-Portals

Das Krankenhauspersonal ist gefordert, eine Zunahme der Patientenzahlen zu bewältigen und gleichzeitig die Lieferkette im Notfall zu verwalten. Über das Portal Regional Government Emergency Response and Monitoring können Mitarbeiter des Gesundheitswesens Daten zu Beatmungsgeräten, Personal, anstehenden Entlassungen und COVID-19-bezogenen Patienten schnell anzeigen und hinzufügen.

## <a name="portal-at-a-glance"></a>Portal im Überblick

Navigieren Sie zum Power Apps-Portal, um mit Personal, Ausrüstung, Material, Patienten und anderen Bereichen zu arbeiten. Der folgende Abschnitt führt Sie durch die Möglichkeiten, die Sie als Benutzer des Portals im Gesundheitswesen haben, auf das Portal zuzugreifen, es einzureichen oder zu aktualisieren.

![Portal im Überblick ](media/portal-user-at-glance.png)

Sie können die neuesten mobilen Geräte und Webbrowser verwenden, wenn Sie das Portal Regional Government Emergency Response and Monitoring Portal nutzen, mit Ausnahme von Apple iPad.

[!include[cc-getting-started](includes/cc-getting-started.md)]

[!include[cc-manage-user-profile](includes/cc-manage-user-profile.md)]

## <a name="portal-components"></a>Portalkomponenten

Das Portal für Emergency Response and Monitoring der Regional Government besteht aus den folgenden Komponenten:

- **Bettenkapazität**  
  Sammeln Sie Details zu Bettenlizenzen, Kapazität, Schärfe, besetzten Betten und Operationsdaten.

- **Personal**  
  Sammeln Sie den Status der RNs nach Standort in der Einrichtung.

- **Arbeitsgerät**  
  Sammeln Sie Details zu Geräten wie Beatmungsgeräten und NIPPV-Geräten.

- **Bedarf**  
  Sammeln Sie wichtige Verbrauchsmaterialien, um den Bestand besser verfolgen, verwalten und prognostizieren zu können. 

- **COVID-19-Statistiken**  
  Sammeln Sie den Status darüber, wie viele Patienten auf COVID-19 untersucht werden und wie viele positiv getestet wurden.


## <a name="bed-capacity"></a>Bettenkapazität

Wählen Sie **Bettenkapazität**, um Patienteninformationen, Betten und Personalkapazität für den ausgewählten Standort zu aktualisieren:

![Bettenkapazität](media/portal-user-bed-capacity.png)

### <a name="options-and-description"></a>Optionen und Beschreibung

| **Optionsname**                                               | **Beschreibung**                                                                       |
|---------------------------------------------------------------|---------------------------------------------------------------------------------------|
| Anzahl derzeit verwendeter lizenzierter Betten  | Anzahl der lizenzierten Betten, die derzeit in dieser Einrichtung verwendet werden.                            |
| Anzahl derzeit verwendeter IPS-Betten (Luftübertragungsisolationsraum)               | Anzahl der ICU-Betten in Isolationsräumen für luftübertragene Infektionen (AIIR), die derzeit in dieser Einrichtung benutzt werden.                                      |
| Anzahl derzeit verwendeter IPS-Betten (Nicht-Luftübertragungsisolationsraum)           | Anzahl der ICU-Betten (nicht-AIIR), die derzeit in dieser Einrichtung benutzt werden.                                  |
| Anzahl derzeit verwendeter Akutversorgungsbetten (Luftübertragungsisolationsraum)        | Anzahl der Akutpflegebetten (AIIR), die derzeit in dieser Einrichtung benutzt werden.                               |
| Anzahl derzeit verwendeter Akutversorgungsbetten (Nicht-Luftübertragungsisolationsraum)    | Anzahl der Akutbetten (Nicht-AIIR-Betten), die derzeit in dieser Einrichtung benutzt werden.                           |
| Anzahl derzeit verwendeter pädiatrischer IPS-Betten (Luftübertragungsisolationsraum)               | Anzahl der Kinderintensivbetten (AIIR), die derzeit in dieser Einrichtung verwendet werden.                                      |
| Anzahl derzeit verwendeter pädiatrischer IPS-Betten (Nicht-Luftübertragungsisolationsraum)           | Anzahl der Kinderintensivbetten (nicht-AIIR), die derzeit in dieser Einrichtung verwendet werden.                                  |
| Anzahl derzeit verwendeter pädiatrischer Akutversorgungsbetten (Luftübertragungsisolationsraum)        | Anzahl der Kinderakutbetten (AIIR), die derzeit in dieser Einrichtung verwendet werden.                               |
| Anzahl derzeit verwendeter pädiatrischer Akutversorgungsbetten (Nicht-Luftübertragungsisolationsraum)    | Anzahl der Kinderakutbetten (nicht AIIR-Betten), die derzeit in dieser Einrichtung verwendet werden.                           |
| Ist Ihre Einrichtung mit der vollen lizenzierten Bettenkapazität besetzt?    | Ja/Nein. Wenn die Antwort Nein lautet, können Sie einen oder mehrere Gründe aus dem Folgenden auswählen: <br> - Personal <br> - Platz <br> - PSA <br> - Arbeitsgerät <br> - Niedriges Patientenvolumen  |
| Können Sie einen plötzlichen Anstieg über lizenzierte Betten hinaus bewältigen?              | Ja/Nein. Wenn die Antwort Nein lautet, können Sie einen oder mehrere Gründe aus dem Folgenden auswählen: <br> - Personal <br> - Platz <br> - PSA <br> - Arbeitsgerät <br> - Niedriges Patientenvolumen  |
| Anzahl derzeit verwendeter Betten für plötzlichen Anstieg                         | Anzahl der derzeit in dieser Einrichtung genutzten Operationsbetten. 
| Anzahl derzeit verwendeter Unterbringungsmöglichkeiten für Verstorbene                                            | Anzahl der Unterkünfte von Verstorbenen, die derzeit in dieser Einrichtung genutzt werden. <br> **Bemerkung**: Nur sichtbar, wenn die *Gesamtkapazität der Leichenhalle* für die gewählte Einrichtung mindestens 1 beträgt.

### <a name="previous-submissions"></a>Frühere Einsendungen

Wenn Sie **Bettkapazität** oder andere Komponenten wie **Mitarbeiter**, **Ausrüstung**, **Zubehör** oder **COVID-19-Statistiken** öffnen, können Sie das Datum, die Uhrzeit und den Absender der letzten Einreichung sehen.

Wenn Sie ein einzelnes Feld wählen, wie z.B. *Anzahl der lizenzierten Betten, die derzeit benutzt werden* für **Bettkapazität**, können Sie auch den vorherigen Wert sehen, der für das Feld eingegeben wurde:

![Vorheriger Wert](media/previous-submissions.png)

## <a name="staff"></a>Personal

Reichen Sie mit dem Formular **Personal** personalspezifische Details wie Fehlzeiten und Angaben zur registrierten Krankenschwester ein, wie z.B. *im Dienst* und *aktuell benötigt*:

![Angaben zum Personal](media/portal-user-staff-details.png)

### <a name="options-and-description"></a>Optionen und Beschreibung

| **Optionsname**                               | **Beschreibung**                                                                |
|-----------------------------------------------|--------------------------------------------------------------------------------|
| Prozentsatz des fehlenden Personals für Grundversorgung | Abwesenheit des wesentlichen Pflegepersonals in Prozent.                  |
| Anzahl der derzeit diensttuenden RNs                                    | Anzahl der registrierten Krankenschwestern, die derzeit für die ausgewählte Einrichtung im Dienst sind.                 |
| Anzahl der derzeit benötigten examinierten Krankenschwestern                                  | Anzahl der registrierten Krankenschwestern, die derzeit für die ausgewählte Einrichtung benötigt werden. |

## <a name="equipment"></a>Arbeitsgerät

Reichen Sie die Ausrüstungsdetails wie z.B. Beatmungsgeräte und NIPPV-Geräte ein:

![Ausstattungsdetails](media/portal-user-equipment-details.png)

### <a name="options-and-description"></a>Optionen und Beschreibung

| **Optionsname** | **Beschreibung**                 |
|-----------------|---------------------------------|
| Beatmungsgeräte     | Anzahl der derzeit verwendeten Beatmungsgeräte.   |
| NIPPV (Nichtinvasive Überdruckbeatmung)          | Anzahl der eingesetzten NIPPV-Geräte (Nicht-invasive Überdruckbeatmung). |

## <a name="supplies"></a>Bedarf

Reichen Sie den Bestand an Verbrauchsmaterialien ein, die auf Lager sind und in den letzten 24 Stunden verwendet wurden:

![Details zu Verbrauchsmaterial](media/portal-user-supplies-details.png)

### <a name="options-and-description"></a>Optionen und Beschreibung

Die Artikelliste der Bedarfs-App kann je nach den Anforderungen Ihres Unternehmens unterschiedlich sein. Beschreibungen der Bedarfsnamen finden Sie in den Ressourcen Ihrer Organisation.

> [!NOTE]
> Die Artikelwerte des Bedarfsinventars müssen im Zahlenformat vorliegen. Die Versorgungsnummer ist für **Einzelkomponente**. Beispielsweise werden N-95 Masken von jeder einzelnen Maske gezählt, anstatt die Anzahl der Boxen zu zählen, die Masken enthalten.

## <a name="covid-19-stats"></a>COVID-19-Statistiken

Reichen Sie die spezifischen COVID-19-Details mit dem Formular **COVID-19-Statistiken** ein:

![Statistik](media/portal-user-stats.png)

### <a name="options-and-description"></a>Optionen und Beschreibung

| **Optionsname**                                                   | **Beschreibung**                                                    |
|-------------------------------------------------------------------|--------------------------------------------------------------------|
| Anzahl der untersuchten Patienten (PUIs)                     | Anzahl der Patienten, die in dieser Einrichtung untersucht werden.                            |
| Anzahl der Patienten mit bestätigtem COVID-19                        | Anzahl der Patienten mit bestätigtem COVID-19 in dieser Einrichtung.                        |
| Anzahl intubierter Patienten                                      | Anzahl der in dieser Einrichtung intubierten Patienten.                                      |
| Anzahl der Patienten mit COVID-19, die in den letzten 24 Stunden entlassen wurden | Anzahl der Patienten mit COVID-19, die in den vorangegangenen 24 Stunden in dieser Einrichtung entlassen wurden. |

## <a name="general-portal-options"></a>Allgemeine Portal-Optionen

[!include[cc-general-options](includes/cc-general-options.md)]

## <a name="issues-and-feedback"></a>Probleme und Feedback

- Um ein Problem mit der Lösung Regional Government Emergency Response and Monitoring zu melden, besuchen Sie <https://aka.ms/rer-issues>.

- Rückmeldungen über die Lösung Regional Government Emergency Response and Monitoring finden Sie unter <https://aka.ms/rer-feedback>.
