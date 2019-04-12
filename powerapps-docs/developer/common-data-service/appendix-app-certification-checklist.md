---
title: 'Anhang: App-Zertifizierungscheckliste (PowerApps) | Microsoft Docs'
description: 'Die App-Zertifizierungscheckliste bietet Ihnen Informationen zu den Prüfungen, die Ihre modellgestützten Apps, Canvas-Apps und Flows vor der Veröffentlichung auf AppSource durchlaufen müssen.'
ms.custom: ''
ms.date: 03/20/2019
ms.reviewer: kvivek
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
<td rowspan=5><a href="https://docs.microsoft.com/powerapps/maker/model-driven-apps/model-driven-app-overview">Modelgestützte Apps</a>, <a href="https://docs.microsoft.com/powerapps/maker/canvas-apps/getting-started">Canvas-Apps</a> und <a href="https://docs.microsoft.com/flow/getting-started">Flows</a>, die eine Verbindung mit Common Data Service herstellen<br/><br/><strong>HINWEIS</strong>: Dynamics 365 for Customer Engagement Apps sind modellgestützte Apps.</td>
<td>Plausibilitätsprüfung</td>
<td><ul>
<li>Überprüfen des App-Registrierungstyps: Kostenlos, Testversion oder Kontakt. Bei einer Registrierung als Kontakt muss der Herausgeber den Testlauf aktivieren.</li>
<li>Überprüfen Sie, dass das eingereichte <a href="https://docs.microsoft.com/powerapps/developer/common-data-service/create-package-app-appsource">Paket</a> alle Artefakte enthält, die erforderlich sind, um auf AppSource zu veröffentlichen.</li>
<li>Laden Sie das funktionelle E2E-Dokument vom Cloud-Partner-Portal herunter und überprüfen Sie, ob das Dokument mit funktionalen Szenarien und einem Benutzer-/Administratorverlauf aktualisiert ist.</li>
</ul>
</td>
</tr>
<tr>
<td>Codeüberprüfung</td>
<td>
<ul>
<li>Codeüberprüfung für Canvas-Apps wird über das <a href="https://docs.microsoft.com/en-us/powerapps/maker/canvas-apps/accessibility-checker">Barrierefreiheitprüfungstool</a> in PowerApps ausgeführt, um Folgendes zu überprüfen:
<ul>
<li>Statische Formelfehler und Warnungen: Wenn Probleme gefunden werden, wird das Zertifizierungsteam die Rückmeldung zur Behebung freigeben und die App wieder bei AppSource einreichen.</li>
<li>Laufzeitfehler: Können auftreten, wenn die App im Ausführmodus zur Ansicht geöffnet wird. Alle gefundenen Probleme werden per E-Mail gemeldet.</li>
<li>Barrierefreiheitsfehler und Warnungen: Alle Barrierefreiheitsfehler sollten gemäß der Solution Checker-Anleitung gelöst werden.</li>
</ul></li>
<li>Codeüberprüfung für die Common Data Service-Lösung wird über das <a href="https://experienceisv.microsoftcrmportals.com/precertification/#/">OnDemand-Codeanalyse (ODCA)</a>-Tool durchgeführt.</li>
<li>Die vom ODCA gemeldet Probleme werden manuell auf für Korrektheit überprüft und falsch positive Ergebnisse werden auf niedrigen Schweregrad verringert.</li>
<li>Der erstellte Bericht wird dem Herausgeber per E-Mail zugestellt.</li>
</ul>
</td>
</tr>
<tr>
<td>Bereitstellungsüberprüfung</td>
<td>
<ul>
<li>Die Lösung wird mithilfe vom <a href="https://docs.microsoft.com/powerapps/developer/common-data-service/package-deployer/create-packages-package-deployer">Package Deployer</a> in einem PowerApps Studio installiert. Installierte Canvas-Apps werden nach der Installation manuell in der Lösung und im App-Abschnitt gesucht. Es wird sichergestellt, dass die App im Bearbeitungs- und Ausführungsmodus geöffnet wird. Die Canvas-App wird manuell von PowerApps Studio gelöscht, um die erfolgreiche Deinstallation zu überprüfen</li>
<li>Überprüfen Sie, ob die Canvas-App erfolgreich eine Verbindung über die vom Hersteller bereitgestellten Konnektoren herstellt. Beispielsweise Common Data Service oder eine beliebige andere Verbindung.</li>
<li>Überprüfen Sie, om alle Common Data Service-Komponenten (Entitäten, Webressourcen, Plug-Ins und andere Komponenten) der Lösung zur Verfügung stehen.</li>
<li>Deinstallieren Sie die Lösung manuell und überprüfen Sie, ob alle Komponenten, die der verwalteten Lösung zugeordnet wurden, entfernt werden.</li>
</ul>
</td>
</tr>
<tr>
<td>Funktionsüberprüfung</td>
<td>
<ul>
<li>Überprüfen Sie die Funktionalität der App basierend auf dem funktionalen Dokument, das dem Herausgeber freigegeben wurde. Alle Funktionen, die in der App implementiert wurden, sollten bestehen.</li>
<li>Der Herausgeber sollte das funktionale E2E-Dokument über das Cloud-Partner-Portal einreichen, oder er kann Videolinks durch E-Mails freigeben.</li>
<li>Wenn für die App eine Lizenzkonfiguration erforderlich ist, wird das Zertifizierungsteam die Instanzdetails freigeben, damit Herausgeber die erforderliche Lizenz aktualisieren können.</li>
</ul></td>
</tr>
<tr>
<td>Sicherheitsüberprüfung</td>
<td>
<ul>
<li>Überprüfen Sie, dass die Canvas-App eine Verbindung mit einer beliebigen externe Datenquelle oder Verbindungen herstellt, die Zugriff benötigen, und überprüfen Sie die richtigen Verbindungsdetails, die im E2E-Dokument freigegeben werden.</li>
<li>Überprüfen Sie, ob die Canvas-App aus PowerApps-Konnektoren eine Verbindung mit beliebigen externen Verbindungen herstellt.</li>
<li>Überprüfen Sie den benutzerdefinierten Code, der im Package Deployer zur Verfügung gestellt wird. Überprüfen Sie den Code, bevor Sie die App für AppSource genehmigen.</li>
<li>Überprüfen Sie den Code manuell, um zu überprüfen, ob der benutzerdefinierte Code beliebige Kundendaten von der Zielumgebung abruft.</li>
</ul>
</td>
</tr>
<tr>
<td rowspan=5><a href="https://docs.microsoft.com/powerapps/maker/canvas-apps/getting-started">Canvas Apps</a> und <a href="https://docs.microsoft.com/flow/getting-started">Flows</a>, die eine Verbindung mit Datenquellen <i>außer</i> Common Data Service herstellen
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
<li>Das Gleiche, was zuvor für modelgestützte Apps, Canvas-Apps und Flows erklärt wurde, die eine Verbindung mit Common Data Service herstellen</li></ul>
</td>
</tr>
<tr>
<td>Bereitstellungsüberprüfung</td>
<td>
<ul>
<li>Canvas-App werden manuell auf einen PowerApps Studio mit der Import App-Funktion installiert. Installierte Canvas-Apps werden nach der Installation manuell im App-Abschnitt gesucht. Es wird sichergestellt, dass die App im Bearbeitungs- und Ausführungsmodus geöffnet wird. Die Canvas-App wird manuell von PowerApps Studio gelöscht, um die erfolgreiche Deinstallation zu überprüfen.</li>
<li>Überprüfen Sie, ob die Canvas-App erfolgreich eine Verbindung mit den vom Hersteller bereitgestellten Konnektoren herstellt.</li>
</ul>
</td>
</tr>
<tr>
<td>Funktionsüberprüfung</td>
<td>
<ul>
<li>Das Gleiche, was zuvor für modelgestützte Apps, Canvas-Apps und Flows erklärt wurde, die eine Verbindung mit Common Data Service herstellen</li></ul></td>
</tr>
<tr>
<td>Sicherheitsüberprüfung</td>
<td>
<ul>
<li>Das Gleiche, was zuvor für modelgestützte Apps, Canvas-Apps und Flows erklärt wurde, die eine Verbindung mit Common Data Service herstellen</li></ul>
</td>
</tr>
</tbody>
</table>

Weitere Informationen zu bewährten Methoden für das Erstellen von:
- Canvas-Apps finden Sie unter [Codierstandard und -Anleitung für Canvas-App](https://aka.ms/powerappscanvasguidelines)
- Modellgesteuerte Apps finden Sie unter [Grundlegendes zu Komponenten modellgestützter Apps](https://docs.microsoft.com/powerapps/maker/model-driven-apps/model-driven-app-components)

  




  

