---
title: 'Anhang: App-Zertifizierungscheckliste (PowerApps) | Microsoft-Dokumentation'
description: Die App-Zertifizierungscheckliste bietet Ihnen Informationen zu den Prüfungen, die Ihre modellgestützten Apps, Canvas-Apps und Flows vor der Veröffentlichung auf AppSource durchlaufen müssen.
ms.custom: ''
ms.date: 03/20/2019
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: omarcdoc
ms.author: omarc
manager: AnnBe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d36fe4c8d62ea8cbc2750d44fbe28901fd7a827a
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156478"
---
# <a name="appendix-app-certification-checklist"></a>Anhang: App-Zertifizierungscheckliste

Die folgende Checkliste bietet eine Liste der Überprüfungen, die von Microsoft während des Zertifizierungsprozesses durchgeführt werden, nachdem Sie Ihre App [eingereicht](next-steps-submit-app-cloud-partner-portal.md) haben. 

<table>
<tbody>
<tr>
<th>Apps</th>
<th>Überprüfungstyp</th>
<th>Zertifizierungscheckliste</th>
</tr>
<tr>
<td rowspan=5><a href="https://docs.microsoft.com/powerapps/maker/model-driven-apps/model-driven-app-overview">Modellgesteuerte Apps</a>, <a href="https://docs.microsoft.com/powerapps/maker/canvas-apps/getting-started">Canvas-Apps</a> und <a href="https://docs.microsoft.com/power-automate/getting-started">Flows</a>, die eine Verbindung mit Common Data Service herstellen<br/></td>
<td>Plausibilitätsprüfung</td>
<td><ul>
<li>Überprüfen des App-Registrierungstyps: Kostenlos, Testversion oder Kontakt.</li>
<li>Überprüfen Sie, dass das eingereichte <a href="https://docs.microsoft.com/powerapps/developer/common-data-service/create-package-app-appsource">Paket</a> alle Artefakte enthält, die erforderlich sind, um auf AppSource zu veröffentlichen.</li>
<li>Laden Sie das End-to-End (E2E)-Funktionsdokument von <a href="https://partner.microsoft.com/dashboard">Partner-Center</a> herunter und überprüfen Sie, ob das Dokument mit Funktionsszenarien und Benutzer/Administrator-Reisen aktualisiert wurde.</li>
</ul>
</td>
</tr>
<tr>
<td>Codeüberprüfung</td>
<td>
<ul>
<li>Die Code-Validierung für Canvas-Anwendungen erfolgt über <a href="https://docs.microsoft.com/powerapps/maker/canvas-apps/accessibility-checker">Accessibility Checker-Tool</a> in Power Apps, um Folgendes zu überprüfen:
<ul>
<li>Statische Formelfehler und Warnungen: Wenn Probleme gefunden werden, wird das Zertifizierungsteam die Rückmeldung zur Behebung freigeben und die App wieder bei AppSource einreichen.</li>
<li>Laufzeitfehler: Können auftreten, wenn die App im Ausführmodus zur Ansicht geöffnet wird. Alle gefundenen Probleme werden per E-Mail gemeldet.</li>
<li>Barrierefreiheitsfehler und Warnungen: Alle Barrierefreiheitsfehler sollten gemäß der Solution Checker-Anleitung gelöst werden.</li>
</ul></li>
<li>Die Code-Validierung für die Lösung Common Data Service wird mit <a href="https://docs.microsoft.com/powerapps/developer/common-data-service/checker/webapi/overview">Power Apps Checker</a> durchgeführt.</li>
<li>Probleme, die vom Power Apps Checker gemeldet werden, werden manuell auf ihre Korrektheit hin überprüft und falsch-positive Probleme werden auf einen geringen Schweregrad reduziert.</li>
<li>Die Qualität der Lösung und der Pakete wird gegen die AppSource-Zertifizierung <a href="https://docs.microsoft.com/powerapps/developer/common-data-service/checker/webapi/retrieve-rulesets">Regelsatz</a> validiert. 
<li>Der erstellte Bericht wird dem Herausgeber per E-Mail zugestellt.</li>
</ul>
</td>
</tr>
<tr>
<td>Bereitstellungsüberprüfung</td>
<td>
<ul>
<li>Die Lösung wird mithilfe vom <a href="https://docs.microsoft.com/powerapps/developer/common-data-service/package-deployer/create-packages-package-deployer">Package Deployer</a> in einem Power Apps Studio installiert. Installierte Canvas-Apps werden nach der Installation manuell in der Lösung und im App-Abschnitt gesucht. Es wird sichergestellt, dass die App im Bearbeitungs- und Ausführungsmodus geöffnet wird. Die Canvas-App wird manuell von Power Apps Studio gelöscht, um die erfolgreiche Deinstallation zu überprüfen.</li>
<li>Überprüfen Sie, ob die Canvas-App erfolgreich eine Verbindung über die vom Hersteller bereitgestellten Konnektoren herstellt. Beispielsweise Common Data Service oder andere Verbindungen.</li>
<li>Überprüfen Sie, ob alle Common Data Service-Komponenten (Entitäten, Webressourcen, Plug-Ins und andere Komponenten) der Lösung zur Verfügung stehen.</li>
<li>Deinstallieren Sie die Lösung manuell und überprüfen Sie, ob alle Komponenten, die der verwalteten Lösung zugeordnet wurden, entfernt werden.</li>
</ul>
</td>
</tr>
<tr>
<td>Funktionsüberprüfung</td>
<td>
<ul>
<li>Überprüfen Sie die Funktionalität der App basierend auf dem funktionalen Dokument, das dem Herausgeber freigegeben wurde. Alle Funktionen, die in der App implementiert wurden, sollten bestehen.</li>
<li>Der Herausgeber sollte das E2E-Funktionsdokument über das <a href="https://partner.microsoft.com/dashboard">Partner-Center</a> einreichen oder kann Videolinks per E-Mail weitergeben.</li>
<li>Wenn für die App eine Lizenzkonfiguration erforderlich ist, wird das Zertifizierungsteam die Instanzdetails freigeben, damit Herausgeber die erforderliche Lizenz aktualisieren können.</li>
</ul></td>
</tr>
<tr>
<td>Sicherheitsüberprüfung</td>
<td>
<ul>
<li>Überprüfen Sie, dass die Canvas-App eine Verbindung mit einer beliebigen externe Datenquelle oder Verbindungen herstellt, die Zugriff benötigen, und überprüfen Sie die richtigen Verbindungsdetails, die im E2E-Dokument freigegeben werden.</li>
<li>Überprüfen Sie, ob die Canvas-App aus Power Apps-Konnektoren eine Verbindung mit beliebigen externen Verbindungen herstellt.</li>
<li>Überprüfen Sie den benutzerdefinierten Code, der im Package Deployer zur Verfügung gestellt wird. Überprüfen Sie den Code, bevor Sie die App für AppSource genehmigen.</li>
<li>Überprüfen Sie den Code manuell, um zu überprüfen, ob der benutzerdefinierte Code beliebige Kundendaten von der Zielumgebung abruft.</li>
</ul>
</td>
</tr>
<tr>
<td rowspan=5><a href="https://docs.microsoft.com/powerapps/maker/canvas-apps/getting-started">Canvas-Apps</a> und <a href="https://docs.microsoft.com/power-automate/getting-started">Flows</a>, die eine Verbindung mit Datenquellen <i>außer</i> Common Data Service herstellen
</td>
<td>Plausibilitätsprüfung</td>
<td><ul>
<li>Überprüfen Sie, ob die Canvas-App eine gültige .msapp-Datei enthält.</li>
<li>Überprüfen Sie, ob der Paketordner alle erforderlichen Komponenten wie Manifest, Jason und andere Bildkomponenten umfasst.</li>
</ul>
</td>
</tr>
<tr>
<td>Codeüberprüfung</td>
<td><ul>
<li>Das Gleiche, was zuvor für modellgesteuerte Apps, Canvas-Apps und Flows erklärt wurde, die eine Verbindung mit Common Data Service herstellen</li></ul>
</td>
</tr>
<tr>
<td>Bereitstellungsüberprüfung</td>
<td>
<ul>
<li>Canvas-Apps werden manuell auf einem Power Apps Studio mit der Import App-Funktion installiert. Installierte Canvas-Apps werden nach der Installation manuell im App-Abschnitt gesucht. Es wird sichergestellt, dass die App im Bearbeitungs- und Ausführungsmodus geöffnet wird. Die Canvas-App wird manuell von Power Apps Studio gelöscht, um die erfolgreiche Deinstallation zu überprüfen.</li>
<li>Überprüfen Sie, ob die Canvas-App erfolgreich eine Verbindung mit den vom Hersteller bereitgestellten Konnektoren herstellt.</li>
</ul>
</td>
</tr>
<tr>
<td>Funktionsüberprüfung</td>
<td>
<ul>
<li>Das Gleiche, was zuvor für modellgesteuerte Apps, Canvas-Apps und Flows erklärt wurde, die eine Verbindung mit Common Data Service herstellen</li></ul></td>
</tr>
<tr>
<td>Sicherheitsüberprüfung</td>
<td>
<ul>
<li>Das Gleiche, was zuvor für modellgesteuerte Apps, Canvas-Apps und Flows erklärt wurde, die eine Verbindung mit Common Data Service herstellen</li></ul>
</td>
</tr>
</tbody>
</table>

Weitere Informationen zu bewährten Methoden für das Erstellen von:
- Canvas-Apps finden Sie unter [Codierstandard und -Anleitung für Canvas-App](https://aka.ms/powerappscanvasguidelines)
- Modellgesteuerte Apps finden Sie unter [Grundlegendes zu Komponenten modellgestützter Apps](https://docs.microsoft.com/powerapps/maker/model-driven-apps/model-driven-app-components)

### <a name="see-also"></a>Siehe auch

[Partner-Center-Dokumentation](https://docs.microsoft.com/partner-center/)




  

