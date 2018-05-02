---
title: DSR-Leitfaden zu von Kunden erstellten Daten in PowerApps | Microsoft -Dokumentation
description: DSR-Leitfaden zu von Kunden erstellten Daten in PowerApps
services: powerapps
suite: powerapps
documentationcenter: na
author: jamesol-msft
manager: kfile
editor: ''
tags: ''
ms-topic: article
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/17/2018
ms.author: jamesol
ms.openlocfilehash: 823c14d0677ef96c48a26e2488bac1c91bbea225
ms.sourcegitcommit: e3a2819c14ad67cc4ca6640b9064550d0f553d8f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
---
# <a name="responding-to-data-subject-rights-dsr-requests-for-powerapps-customer-data"></a>Reagieren auf DSR-Anforderungen (Data Subject Rights) zu PowerApps-Kundendaten

## <a name="introduction-to-dsr-requests"></a>Einführung in DSR-Anforderungen
Im Rahmen unserer Verpflichtung, unsere Kunden im Umgang mit der DSGVO (Datenschutz-Grundverordnung) stets zu begleiten, wurden diese Informationen entwickelt, um Sie bestmöglich vorzubereiten und zu unterstützen. Diese Dokumentation beschreibt nicht nur unsere Bemühungen um eine bestmögliche Vorbereitung auf die Datenschutz-Grundverordnung, sondern soll auch Beispiele liefern, was Sie bereits heute unternehmen können, um den Bestimmungen der DSGVO mithilfe von PowerApps, Microsoft Flow und Common Data Service für Apps nachzukommen.

Die Datenschutz-Grundverordnung der EU erteilt Personen (in der Verordnung als betroffene Personen bezeichnet) das Recht, vom Arbeitgeber oder einer anderen Einrichtung oder Organisation (auch als Verantwortliche bezeichnet) erhobene personenbezogene Daten zu verwalten. Personenbezogene Daten sind in der DSGVO sehr umfassend definiert als alle Informationen, die sich auf eine identifizierte oder identifizierbare natürliche Person beziehen. Die DSGVO gewährt betroffenen Personen bestimmte Rechte bezüglich ihrer personenbezogenen Daten, darunter das Recht auf Erhalt einer Kopie der personenbezogenen Daten, das Recht auf Berichtigung, das Recht auf Einschränkung der Verarbeitung, das Recht auf Löschung sowie das Recht auf Erhalt der Daten in einem maschinenlesbaren Format, um sie an einen anderen Verantwortlichen übermitteln zu können. Eine betroffene Person kann bei einem Verantwortlichen mit einem formellen Antrag die Einschränkung der Verarbeitung von personenbezogenen Daten verlangen. Dieser Antrag wird auch DSR-Anforderung (Data Subject Rights, Rechte betroffener Personen) genannt.

In diesem Leitfaden wird erklärt, wie Sie als Verantwortlicher im Zuge von DSR-Anforderungen Produkte, Dienste und Verwaltungstools von Microsoft nutzen können, um personenbezogene Daten zu finden und zu verarbeiten. Dies gilt insbesondere für die Suche nach, den Zugriff auf sowie das Ergreifen von Maßnahmen bezüglich personenbezogener Daten, die sich in Microsoft Cloud befinden. Die folgende Auflistung gibt einen Überblick über die in diesem Leitfaden beschriebenen Prozesse:

1. **Ermitteln**: Verwenden Sie Such- und Ermittlungstools, um schneller Kundendaten zu finden, die Gegenstand einer DSR-Anforderung sein könnten. Sobald Sie möglicherweise relevante Dokumente ermittelt haben, können Sie eine oder mehrere der in den folgenden Schritten beschriebenen Aktionen ausführen, um auf eine DSR-Anforderung zu reagieren. Oder Sie entscheiden, dass die Anforderung nicht den Richtlinien Ihrer Organisation bezüglich DSR-Anforderungen entspricht.

1. **Zugreifen**: Rufen Sie personenbezogene Daten aus Microsoft Cloud ab, und fertigen Sie gegebenenfalls eine Kopie an, die Sie der betroffenen Person zur Verfügung stellen können.

1. **Berichtigen**: Nehmen Sie an den personenbezogenen Daten gegebenenfalls Änderungen oder andere geforderte Aktionen vor.

1. **Einschränken**: Schränken Sie die Verarbeitung von personenbezogenen Daten ein, indem Sie entweder die Lizenzen für verschiedene Onlinedienste entfernen oder die gewünschten Dienste, wenn möglich, deaktivieren. Sie können Daten auch aus Microsoft Cloud entfernen und sie lokal oder an einem anderem Speicherort beibehalten.

5. **Löschen**: Löschen Sie personenbezogene Daten dauerhaft aus Microsoft Cloud.

6. **Exportieren**: Stellen Sie der betroffenen Person eine elektronische Kopie ihrer personenbezogenen Daten (in einem maschinenlesbaren Format) zur Verfügung.

Jeder Abschnitt dieses Leitfadens beschreibt jeweils die technischen Vorgänge, die Ihre Organisation als Verantwortlicher durchführen kann, um auf eine DSR-Anforderung bezüglich personenbezogener Daten in Microsoft Cloud zu reagieren.

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
PowerApps-Benachrichtigungen | In PowerApps werden Benutzern verschiedene Arten von Benachrichtigungen gesendet, z.B. wenn eine App für sie freigegeben wurde oder ein Exportvorgang für Common Data Service für Apps abgeschlossen ist.
Gateway | Gateways sind lokale Datengateways, die ein Benutzer zur schnellen und sicheren Übertragung von Daten zwischen PowerApps und einer nicht in der Cloud befindlichen Datenquelle installieren kann. [Weitere Informationen](https://go.microsoft.com/fwlink/?linkid=872247)
Gatewayberechtigungen | Gateways können innerhalb einer Organisation für andere Benutzer freigegeben werden. [Weitere Informationen](https://go.microsoft.com/fwlink/?linkid=872249)
Modellgesteuerte Apps und Berechtigungen für modellgesteuerte Apps  | Das Design einer modellgesteuerten App ist ein auf Komponenten bezogener Ansatz zum Entwickeln von Apps. Modellgesteuerte Apps und die Zugriffsberechtigungen für ihre Benutzer werden als Daten in der Common Data Service-Datenbank für Apps gespeichert.  [Weitere Informationen](https://go.microsoft.com/fwlink/?linkid=872248)

In PowerApps haben Sie die folgenden Möglichkeiten, um nach personenbezogenen Daten über einen bestimmten Benutzer zu suchen:

- **Websitezugriff**: [PowerApps-Website](https://web.powerapps.com), [PowerApps Admin Center](https://admin.powerapps.com/) und [Office 365 Service Trust Portal](https://servicetrust.microsoft.com/)
- **PowerShell-Zugriff**: PowerApps-Cmdlets (für [App-Ersteller](https://go.microsoft.com/fwlink/?linkid=871448) und [Administratoren](https://go.microsoft.com/fwlink/?linkid=871804)) sowie [Cmdlets für lokale Gateways](https://go.microsoft.com/fwlink/?linkid=872238)

Eine ausführliche Anleitung zur Verwendung dieser Möglichkeiten bei der Suche nach personenbezogenen Daten über einen bestimmten Benutzer für jede dieser Ressourcentypen finden Sie unter [Export Customer Data in PowerApps (Exportieren von Kundendaten in PowerApps)]( https://go.microsoft.com/fwlink/?linkid=871888).

Nachdem Sie die Daten gefunden haben, können Sie die jeweilige Aktion ausführen, die von der betroffenen Person gefordert wurde.

### <a name="step-2-find-personal-data-for-the-user-in-microsoft-flow"></a>Schritt 2: Suchen von personenbezogenen Daten über einen Benutzer in Microsoft Flow
In PowerApps-Lizenzen sind immer Microsoft Flow-Funktionen enthalten. Microsoft Flow ist nicht nur in PowerApps-Lizenzen enthalten, sondern auch als eigenständiger Dienst.
Informationen zur Ermittlung von personenbezogenen Daten, die in Microsoft Flow gespeichert wurden, finden Sie unter „Executing DSRs against Microsoft Flow Customer Data (Ausführen von DSR-Anforderungen zu Microsoft Flow-Kundendaten)“.

> [!IMPORTANT]
> Es wird empfohlen, dass Administratoren diesen Schritt für PowerApps-Benutzer ausführen.

### <a name="step-3-find-personal-data-for-the-user-in-instances-of-common-data-service-cds-for-apps"></a>Schritt 3: Suchen von personenbezogenen Daten über einen Benutzer in CDS-Instanzen für Apps (Common Data Service)
Über bestimmte PowerApps-Lizenzen, einschließlich des PowerApps-Communityplans, können Benutzer innerhalb Ihrer Organisation CDS-Instanzen für Apps erstellen sowie Apps auf CDS für Apps erstellen und entwickeln. Der PowerApps-Communityplan ist eine kostenlose Lizenz, mit der Benutzer CDS für Apps in einer individuellen Umgebung testen können. Informationen zu den Funktionen der einzelnen PowerApps-Lizenzen finden Sie auf der [Seite mit den PowerApps-Preisen](https://powerapps.microsoft.com/pricing/).

Informationen zur Ermittlung von personenbezogenen Daten, die mit CDS für Apps gespeichert wurden, finden Sie unter „Executing DSRs against Common Data Service Customer Data (Ausführen von DSR-Anforderungen zu CDS-Kundendaten)“.

> [!IMPORTANT]
> Es wird empfohlen, dass Administratoren diesen Schritt für PowerApps-Benutzer ausführen.

## <a name="rectify"></a>Berichtigen
Bei der Anfrage einer betroffenen Personen bezüglich einer Berichtigung der von Ihrer Organisation gespeicherten personenbezogenen Daten müssen Sie entscheiden, ob die Anforderung umgesetzt werden soll oder nicht. Das Berichtigen von Daten kann Aktionen wie die Bearbeitung, Zensur oder Entfernung von personenbezogenen Daten aus einem Dokument oder einem anderen Element beinhalten.

PowerApps weist bei der Identitätsbestimmung Abhängigkeiten von Azure Active Directory auf. Identitäten enthalten personenbezogene Daten und können als solche in Azure Active Directory bearbeitet werden. Unternehmenskunden können DSR-Berichtigungsanforderungen verwalten, einschließlich eingeschränkter Bearbeitungsfeatures je nach Art des angegebenen Microsoft-Diensts.  Als verarbeitende Instanz für die Daten bietet Microsoft keine Möglichkeit, vom System generierte Protokolle zu korrigieren, da diese auf Fakten basierende Aktivitäten und einen historischen Datensatz von Ereignissen innerhalb der Microsoft-Dienste darstellen. Weitere Informationen finden Sie in der Dokumentation zu DSR-Anforderungen in Azure im Rahmen der Datenschutz-Grundverordnung im [Office 365 Service Trust Portal](https://servicetrust.microsoft.com/ViewPage/GDPRDSR).

## <a name="restrict"></a>Einschränken
Betroffene Personen können das Einschränken der Verarbeitung ihrer personenbezogenen Daten fordern.  Wir stellen hierfür bereits vorhandene Anwendungsprogrammierschnittstellen (APIs) sowie Benutzeroberflächen bereit.  Mit diesen Möglichkeiten kann der Mandantenadministrator des Unternehmens solche DSR-Anforderungen mithilfe einer Kombination aus Datenexport und Datenlöschung verwalten. Ein Kunde kann Folgendes fordern:

- Exportieren einer elektronischen Kopie der personenbezogenen Daten des Benutzers einschließlich:

    - Konto/Konten
    - vom System generierter Protokolle
    - zugeordneter Protokolle
- Löschen des Kontos und der zugehörigen Daten, die sich innerhalb der Microsoft-Systeme befinden.

## <a name="export"></a>Exportieren
Das „Recht auf Datenübertragbarkeit“ erlaubt einer betroffenen Person die Anforderung einer Kopie ihrer personenbezogenen Daten in einem elektronischen Format (d.h. in einem „strukturierten, gängigen, maschinenlesbaren und kompatiblen Format“), in dem die Daten einem anderen Verantwortlichen übermittelt werden können.

Weitere Informationen finden Sie unter [Executing Export Data Subject Rights (DSR) Requests against PowerApps Customer Data (Ausführen von DSR-Anforderungen zum Export von PowerApps-Kundendaten)](https://go.microsoft.com/fwlink/?linkid=871888).

## <a name="delete"></a>Löschen
Das „Recht auf Löschung“ von personenbezogenen Daten aus den Kundendaten einer Organisation ist ein Kernpunkt der Schutzbestimmungen der DSGVO. Das Entfernen personenbezogener Daten bezieht sich auch auf vom System generierte Protokolle, jedoch nicht auf Informationen aus Überwachungsprotokollen.

Mit PowerApps können Benutzer Branchenanwendungen erstellen, die ein wichtiger Bestandteil des täglichen Betriebs Ihrer Organisation sind. Wenn ein Benutzer Ihre Organisation verlässt, müssen Sie manuell überprüfen und bestimmen, ob bestimmte, vom Benutzer erstellte Daten und Ressourcen gelöscht werden sollen. Andere Kundendaten werden automatisch gelöscht, sobald das Konto des Benutzers aus Azure Active Directory gelöscht wird.

Weitere Informationen finden Sie unter [Executing Delete Data Subject Rights (DSR) Requests against PowerApps Customer Data (Ausführen von DSR-Anforderungen zum Löschen von PowerApps-Kundendaten)](https://go.microsoft.com/fwlink/?linkid=871883).
