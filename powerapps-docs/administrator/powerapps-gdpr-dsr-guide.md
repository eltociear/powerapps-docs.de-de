---
title: Reagieren auf DSR-Anforderungen für PowerApps-Kundendaten | Microsoft-Dokumentation
description: Exemplarische Vorgehensweise zum Reagieren auf DSR-Anforderungen (Data Subject Rights, Rechte betroffener Personen) für PowerApps-Kundendaten
author: jamesol-msft
manager: kvivek
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 05/23/2018
ms.author: jamesol
search.audienceType:
- admin
search.app:
- D365CE
- PowerApps
- Powerplatform
ms.openlocfilehash: fddbb40e7b4b5d94b1df02e32af6316cce0a17d9
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "42862885"
---
# <a name="responding-to-data-subject-rights-dsr-requests-for-powerapps-customer-data"></a>Reagieren auf DSR-Anforderungen (Data Subject Rights, Rechte betroffener Personen) für PowerApps-Kundendaten

## <a name="introduction-to-dsr-requests"></a>Einführung in DSR-Anforderungen
Die Datenschutz-Grundverordnung der EU erteilt Personen (in der Verordnung als *betroffene Personen* bezeichnet) das Recht, vom Arbeitgeber oder einer anderen Einrichtung oder Organisation (auch als *Verantwortliche* bezeichnet) erhobene personenbezogene Daten zu verwalten. Personenbezogene Daten sind in der DSGVO sehr umfassend definiert als alle Informationen, die sich auf eine identifizierte oder identifizierbare natürliche Person beziehen. Die DSGVO erteilt betroffenen Personen folgende Rechte bezüglich ihrer personenbezogenen Daten:

* Recht auf das Erhalten einer Kopie
* Recht auf Berichtigung
* Recht auf Einschränkung der Verarbeitung
* Recht auf Löschung
* Recht auf Datenübertragbarkeit

Eine betroffene Person kann bei einem Verantwortlichen mit einem formellen Antrag die Einschränkung der Verarbeitung von personenbezogenen Daten verlangen. Dieser Antrag wird auch DSR-Anforderung (Data Subject Rights, Rechte betroffener Personen) genannt.

In diesem Artikel wird beschrieben, welche Vorbereitungen Microsoft bezüglich der Datenschutz-Grundverordnung trifft. Darüber hinaus gibt der Artikel einen Überblick über Maßnahmen, die Sie ergreifen können, um den Bestimmungen der DSGVO mithilfe von PowerApps, Microsoft Flow und Common Data Service für Apps nachzukommen. Sie erfahren, wie Sie als Verantwortlicher mit Microsoft-Produkten, -Diensten und -Verwaltungstools im Rahmen einer DSR-Anforderung personenbezogene Daten in der Microsoft-Cloud finden, darauf zugreifen und diese behandeln können.

In diesem Artikel werden die folgenden Aktionen besprochen:

* **Ermitteln**: Verwenden Sie Such- und Ermittlungstools, um schneller Kundendaten zu finden, die Gegenstand einer DSR-Anforderung sein könnten. Sobald Sie potenziell relevante Dokumente ermittelt haben, können Sie eine oder mehrere DSR-Aktionen ausführen, um auf eine Anforderung zu reagieren. Oder Sie entscheiden, dass die Anforderung nicht den Richtlinien Ihrer Organisation bezüglich DSR-Anforderungen entspricht.

* **Zugreifen**: Rufen Sie personenbezogene Daten aus Microsoft Cloud ab, und fertigen Sie gegebenenfalls eine Kopie der Daten an, die Sie der betroffenen Person zur Verfügung stellen können.

* **Berichtigen**: Nehmen Sie Änderungen vor oder implementieren Sie ggf. andere angeforderte Aktionen für die personenbezogenen Daten.

* **Einschränken**: Schränken Sie die Verarbeitung von personenbezogenen Daten ein, indem Sie entweder die Lizenzen für verschiedene Onlinedienste entfernen oder die gewünschten Dienste, wenn möglich, deaktivieren. Sie können Daten auch aus Microsoft Cloud entfernen und sie lokal oder an einem anderem Speicherort beibehalten.

* **Löschen**: Löschen Sie personenbezogene Daten dauerhaft aus der Microsoft-Cloud.

* **Exportieren**: Stellen Sie der betroffenen Person eine elektronische Kopie ihrer personenbezogenen Daten (in einem maschinenlesbaren Format) zur Verfügung.

## <a name="discover"></a>Erkunden
Der erste Schritt bei jeder DSR-Anforderung besteht darin, die angeforderten personenbezogenen Daten zu suchen und zu finden. In diesem Schritt (Suche und Überprüfung der fraglichen Daten) wird auch entschieden, ob eine DSR-Anforderung die Richtlinien Ihrer Organisation zur Umsetzung von DSR-Anforderungen erfüllt. Bei der Überprüfung der fraglichen personenbezogenen Daten wird möglicherweise entschieden, dass die Anforderung nicht den Richtlinien Ihrer Organisation entspricht, da ihre Umsetzung etwa die Rechte und Freiheiten von anderen Personen beeinträchtigt.

### <a name="step-1-find-personal-data-for-the-user-in-powerapps"></a>Schritt 1: Suchen von personenbezogenen Daten über einen Benutzer in PowerApps
Die folgenden Ressourcentypen für PowerApps enthalten personenbezogene Daten über einen bestimmten Benutzer:

Ressourcen mit personenbezogenen Daten |    Zweck
--- | ---
Umgebung |   Eine Umgebung ist ein Bereich zum Speichern, Verwalten und Freigeben der Geschäftsdaten, Apps und Flows Ihres Unternehmens. [Weitere Informationen](https://go.microsoft.com/fwlink/?linkid=872239)
Umgebungsberechtigungen | Benutzern werden Umgebungsrollen mit Hersteller- und Administratorberechtigungen innerhalb einer Umgebung zugewiesen. [Weitere Informationen](https://go.microsoft.com/fwlink/?linkid=872240)
Canvas-App  | Plattformübergreifende Geschäftsanwendung, die aus einem leeren Zeichenbereich erstellt und mit mehr als 200 Datenquellen verbunden werden können. [Weitere Informationen](https://go.microsoft.com/fwlink/?linkid=872241)
Berechtigungen für Canvas-Apps  | Canvas-Apps können innerhalb einer Organisation für andere Benutzer freigegeben werden. [Weitere Informationen](https://go.microsoft.com/fwlink/?linkid=872242)
Verbindung  | Wird von Connectors verwendet und stellt eine Verbindung mit APIs, Systemen, Datenbanken usw. her. [Weitere Informationen](https://go.microsoft.com/fwlink/?linkid=872243)
Verbindungsberechtigungen  | Bestimmte Verbindungstypen können innerhalb einer Organisation für andere Benutzer freigegeben werden. [Weitere Informationen](https://go.microsoft.com/fwlink/?linkid=872244)
Benutzerdefinierter Connector    | Wird von einem Benutzer erstellt, um den Zugriff auf eine Datenquelle zu ermöglichen, der durch keinen der Standard-Connectors in PowerApps bereitgestellt wird. [Weitere Informationen](https://go.microsoft.com/fwlink/?linkid=872245)
Berechtigungen für benutzerdefinierte Connectors    | Benutzerdefinierte Connectors können innerhalb einer Organisation für andere Benutzer freigegeben werden. [Weitere Informationen](https://go.microsoft.com/fwlink/?linkid=872246)
Benutzer- und Benutzeranwendungseinstellungen in PowerApps    | In PowerApps werden mehrere Benutzereinstellungen gespeichert, die für eine Optimierung der PowerApps-Laufzeit und des PowerApps-Portals verwendet werden.
PowerApps-Benachrichtigungen | PowerApps sendet verschiedene Arten von Benachrichtigungen an Benutzer, z.B. wenn eine App für sie freigegeben wurde oder ein CDS für Apps-Export abgeschlossen wurde.
Gateway | Gateways sind lokale Datengateways, die ein Benutzer zur schnellen und sicheren Übertragung von Daten zwischen PowerApps und einer nicht in der Cloud befindlichen Datenquelle installieren kann. [Weitere Informationen](https://go.microsoft.com/fwlink/?linkid=872247)
Gatewayberechtigungen | Gateways können innerhalb einer Organisation für andere Benutzer freigegeben werden. [Weitere Informationen](https://go.microsoft.com/fwlink/?linkid=872249)
Modellgesteuerte Apps und Berechtigungen für modellgesteuerte Apps  | Das Design einer modellgesteuerten App ist ein auf Komponenten bezogener Ansatz zum Entwickeln von Apps. Modellgesteuerte Apps und die Zugriffsberechtigungen für ihre Benutzer werden als Daten in der CDS für Apps-Datenbank gespeichert.  [Weitere Informationen](https://go.microsoft.com/fwlink/?linkid=872248)

In PowerApps haben Sie die folgenden Möglichkeiten, um nach personenbezogenen Daten über einen bestimmten Benutzer zu suchen:

- **Websitezugriff**: [PowerApps-Website](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), [PowerApps Admin Center](https://admin.powerapps.com/) und [Office 365 Service Trust Portal](https://servicetrust.microsoft.com/)
- **PowerShell-Zugriff**: PowerApps-Cmdlets (für [App-Ersteller](https://go.microsoft.com/fwlink/?linkid=871448) und [Administratoren](https://go.microsoft.com/fwlink/?linkid=871804)) sowie [Cmdlets für lokale Gateways](https://go.microsoft.com/fwlink/?linkid=872238)

Eine ausführliche Anleitung zur Verwendung dieser Möglichkeiten bei der Suche nach personenbezogenen Daten über einen bestimmten Benutzer für jede dieser Ressourcentypen finden Sie unter [Reagieren auf Anforderungen eines Exports von DSR-Anforderungen für PowerApps-Kundendaten](powerapps-gdpr-export-dsr.md).

Nachdem Sie die Daten gefunden haben, können Sie die jeweilige Aktion ausführen, die von der betroffenen Person gefordert wurde.

### <a name="step-2-find-personal-data-for-the-user-in-microsoft-flow"></a>Schritt 2: Suchen von personenbezogenen Daten über einen Benutzer in Microsoft Flow
In PowerApps-Lizenzen sind immer Microsoft Flow-Funktionen enthalten. Microsoft Flow ist nicht nur in PowerApps-Lizenzen enthalten, sondern auch als eigenständiger Dienst.

Weitere Informationen über die Ermittlung von personenbezogenen Daten, die vom Microsoft Flow-Dienst gespeichert werden, finden Sie unter [Responding to GDPR Data Subject Requests for Microsoft Flow (Reagieren auf DSGVO-Anforderungen betroffener Personen für Microsoft Flow)](https://go.microsoft.com/fwlink/?linkid=872250).

> [!IMPORTANT]
> Es wird empfohlen, dass Administratoren diesen Schritt für PowerApps-Benutzer ausführen.

### <a name="step-3-find-personal-data-for-the-user-in-instances-of-cds-for-apps"></a>Schritt 3: Suchen von personenbezogenen Daten über einen Benutzer in CDS für Apps-Instanzen
Über bestimmte PowerApps-Lizenzen, einschließlich des PowerApps-Communityplans, können Benutzer innerhalb Ihrer Organisation CDS-Instanzen für Apps erstellen sowie Apps auf CDS für Apps erstellen und entwickeln. Der PowerApps-Communityplan ist eine kostenlose Lizenz, mit der Benutzer CDS für Apps in einer individuellen Umgebung testen können. Informationen zu den Funktionen der einzelnen PowerApps-Lizenzen finden Sie auf der [Seite mit den PowerApps-Preisen](https://powerapps.microsoft.com/pricing/).

Anweisungen zum Ermitteln von personenbezogenen Daten, die von CDS für Apps gespeichert werden, finden Sie unter [Reagieren auf DSR-Anforderungen für Kundendaten in Common Data Service für Apps](common-data-service-gdpr-dsr-guide.md).

> [!IMPORTANT]
> Es wird empfohlen, dass Administratoren diesen Schritt für PowerApps-Benutzer ausführen.

## <a name="rectify"></a>Berichtigen
Bei der Anfrage einer betroffenen Person bezüglich einer Berichtigung der von Ihrer Organisation gespeicherten personenbezogenen Daten müssen Sie entscheiden, ob die Anforderung umgesetzt werden soll oder nicht. Das Berichtigen von Daten kann Aktionen wie die Bearbeitung, Zensur oder Entfernung von personenbezogenen Daten aus einem Dokument oder einem anderen Element beinhalten.

Sie können Azure Active Directory zum Verwalten der Identitäten (personenbezogene Daten) Ihrer Benutzer in PowerApps verwenden. Unternehmenskunden können DSR-Berichtigungsanforderungen verwalten, indem sie die eingeschränkten Bearbeitungsfeatures nutzen, die im jeweiligen Microsoft-Diensts zur Verfügung stehen. Als verarbeitende Instanz für die Daten bietet Microsoft keine Möglichkeit, vom System generierte Protokolle zu berichtigen, da diese auf Fakten basierende Aktivitäten und einen historischen Datensatz von Ereignissen innerhalb der Microsoft-Dienste darstellen. Weitere Einzelheiten finden Sie unter [GDPR: Data Subject Requests (DSRs) (DSGVO: Anforderungen betroffener Personen (Data Subject Requests, DSRs))](https://servicetrust.microsoft.com/ViewPage/GDPRDSR).

## <a name="restrict"></a>Einschränken
Betroffene Personen können das Einschränken der Verarbeitung ihrer personenbezogenen Daten fordern.  Wir stellen hierfür bereits vorhandene Anwendungsprogrammierschnittstellen (APIs) sowie Benutzeroberflächen bereit.  Mit diesen Möglichkeiten kann der Mandantenadministrator des Unternehmens solche DSR-Anforderungen mithilfe einer Kombination aus Datenexport und Datenlöschung verwalten. Ein Kunde kann Folgendes fordern:

* Exportieren einer elektronischen Kopie der personenbezogenen Daten des Benutzers einschließlich:

    - Konto/Konten
    - vom System generierter Protokolle
    - zugeordneter Protokolle

* Löschen des Kontos und der zugehörigen Daten, die sich innerhalb der Microsoft-Systeme befinden.

## <a name="export"></a>Exportieren
Das „Recht auf Datenübertragbarkeit“ ermöglicht einer betroffenen Person die Anforderung einer Kopie ihrer personenbezogenen Daten in elektronischem Format (d.h. in einem „strukturierten, häufig verwendeten, maschinenlesbaren und interoperablen Format“), die an einen anderen Verantwortlichen übertragen werden kann.

Ausführliche Informationen finden Sie unter [Reagieren auf Anforderungen eines Exports von DSR-Anforderungen für PowerApps-Kundendaten](powerapps-gdpr-export-dsr.md).

## <a name="delete"></a>Löschen
Das „Recht auf Löschung“ von personenbezogenen Daten aus den Kundendaten einer Organisation ist ein Kernpunkt der Schutzbestimmungen der DSGVO. Das Entfernen personenbezogener Daten bezieht sich auch auf vom System generierte Protokolle, jedoch nicht auf Informationen aus Überwachungsprotokollen.

Mit PowerApps können Benutzer Branchenanwendungen erstellen, die ein wichtiger Bestandteil des täglichen Betriebs Ihrer Organisation sind. Wenn ein Benutzer Ihre Organisation verlässt, müssen Sie manuell überprüfen und bestimmen, ob bestimmte, vom Benutzer erstellte Daten und Ressourcen gelöscht werden sollen. Andere Kundendaten werden automatisch gelöscht, sobald das Konto des Benutzers aus Azure Active Directory gelöscht wird.

Ausführliche Informationen finden Sie unter [Reagieren auf Anforderungen zum Löschen von DSR-Anforderungen für Kundendaten in PowerApps](powerapps-gdpr-delete-dsr.md).
