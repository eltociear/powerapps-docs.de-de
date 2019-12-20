---
title: Updates in Power Apps-Portalen veröffentlichen | MicrosoftDocs
description: Erfahren Sie mehr über Versionsupdates von Power Apps-Portalen.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/22/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: bbdc9a775c4bfaacc6f99217f6f24ce32db06bca
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "2884471"
---
# <a name="release-updates"></a>Updates veröffentlichen

Diese Thema enthält Ressourcen, in denen Sie Informationen zu den kürzlich veröffentlichten neuen Funktionen und den Funktionen erhalten, die in den nächsten Monaten veröffentlicht werden.

## <a name="power-apps-portals-updates"></a>Power Apps-Portalupdates

Informationen über neue Features, die in den nächsten Monaten freigegeben werden und die Sie für die Planung verwenden können, finden Sie hier:

- [2019 Version Welle 2 Plan](https://docs.microsoft.com/power-platform-release-plan/2019wave2/microsoft-powerapps/planned-features#portal-capabilities-for-power-apps)

## <a name="previous-portal-updates"></a>Frühere Portalupdates

Hier ist eine Liste der Funktionen, die für Dynamics 365-Portale hinzugefügt wurden. Weitere Informationen zu den bisherigen Updates von Dynamics 365 Portale finden Sie unter [Portalfunktionen für Microsoft Dynamics 365 Releases](https://support.microsoft.com/help/3181191).

> [!NOTE]
> Power Apps-Portale waren früher als Dynamics 365-Portale bekannt.

### <a name="dynamics-365-portals-version-914-for-the-model-driven-apps-in-dynamics-365"></a>Dynamics 365 Portale Version 9.1.4 für die modellgetriebenen Anwendungen in Dynamics 365

Dynamics 365 Portale Version 9.1.4 für die modellgetriebenen Anwendungen in Dynamics 365 bringt diese neuen Updates und Funktionen:

- **Wartungsmodus für Portal**: Als Portaladministrator können Sie das Portal jetzt konfigurieren, um Kunden eine korrekte Nachricht anzuzeigen, wenn eine Wartungsaktivität ausgeführt wird, z. B. wenn Lösungspakete aktualisiert werden. Weitere Informationen: [Wartungsmodus für ein Portal](admin/enable-maintenance-mode.md)

- **Power BI Embedded-Service aktivieren**: Als Portalsystemanpasser können Sie Berichte und Dashboards jetzt einbetten, die im neuen Arbeitsbereich von Power BI erstellt werden, indem Sie den Power BI Embedded-Service aktivieren. Die Dashboards und Berichte werden auf Webseiten in einem Portal eingebettet, indem der Liquid-Tag powerbi verwendet wird. Weitere Informationen: [Power BI-Integration einrichten](admin/set-up-power-bi-integration.md#enable-power-bi-embedded-service)

- **Inhaltsmoderation für Ideen aktivieren**: Als Portaladministrator können Sie eine Inhaltsmoderationsrichtlinie jetzt erstellen, um die Ideen zu moderieren, die auf dem Portal gesendet werden.

- **Flow zur implizierten OAuth 2.0-Genehmigung**: Als Portalentwickler können Sie jetzt clientseitige API-Aufrufe an externe APIs vornehmen, indem sie den Flow zur implizierten OAuth 2.0-Genehmigung verwenden. Weitere Informationen: [Flow zur implizierten OAuth 2.0-Genehmigung](oauth-implicit-grant-flow.md)

- **Common Data Service-Starterportal (Vorschau)**: Als Portaladministrator können Sie das Portal jetzt so konfigurieren, dass eine Verbindung zur Common Data Service-Umgebung hergestellt wird, und Benutzern erlauben, mit ihm zu interagieren. Diese Funktion bietet die Möglichkeit, ein Portal mit einer Common Data Service-Umgebung zu verbinden, in der keine modellgesteuerten Apps in Dynamics 365 (Dynamics 365 Sales, Dynamics 365 Service oder Dynamics 365 Marketing) vorinstalliert sind.

### <a name="dynamics-365-portals-version-911-for-the-model-driven-apps-in-dynamics-365"></a>Dynamics 365 Portale Version 9.1.1 für die modellgetriebenen Apps in Dynamics 365

Dynamics 365 Portale Version 9.1.1 für die modellgetriebenen Anwendungen in Dynamics 365 bringt diese neuen Updates und Funktionen mit sich:

- **Portalprüfer**: Sie könnennund den Portalprüfer verwenden, um Probleme mit Ihrem Portal zu identifizieren, indem er sich verschiedene Konfigurationsparameter ansieht und Vorschläge zur Behebung gibt. Weitere Informationen: [Portalprüfung](admin/portal-checker.md)

### <a name="dynamics-365-portals-version-9010-for-the-model-driven-apps-in-dynamics-365"></a>Dynamics 365 Portale Version 9.0.10 für die modellgetriebenen Anwendungen in Dynamics 365

Dynamics 365 Portale Version 9.0.10 für die modellgetriebenen Anwendungen in Dynamics 365 bringt diese neuen Updates und Funktionen:

- **Migrieren der Dynamics 365 Portale Konfiguration**: Sie können jetzt Ihre Dynamics 365 Portale Konfiguration von der Entwicklung in die Testumgebung oder in die Produktionsumgebung migrieren. Die Migration beinhaltet den Export der vorhandenen Konfiguration von der Quell-Dynamics 365-Instanz und den anschließenden Import in die Ziel-Dynamics 365-Instanz. Zum Migrieren der Konfigurationsdaten müssten Sie das Tool für die Konfigurationsmigration und eine portalspezifische Konfigurationsschemadatei verwenden. Mehr Informationen: [Migrieren Sie Dynamics 365 Portale Konfiguration](admin/migrate-portal-configuration.md)

- **Power BI-Visualisierung hinzufügen**: Als Portalsystemanpasser können Sie Power BI-Visualisierungen (Dashboard, Berichte und Kacheln) auf Webseiten in ein Portal einbetten, indem Sie das POWERBI Liquid-Tag verwenden. Weitere Informationen: [Power BI-Integration einrichten](admin/set-up-power-bi-integration.md)

- **Portalzugriff durch IP-Adresse einschränken**: Als Portaladministrator können Sie nun eine Liste von IP-Adressen definieren, die zulässig sind, um auf das Portal zuzugreifen. Wenn eine Anfrage mit dem Portal von einem beliebigen Benutzer erstellt wird, wird ihre IP-Adresse für die Zulassungsliste ausgewertet. Wenn die IP-Adresse nicht in der Liste angezeigt wird, wird das Portal einer Webseite mit einem 403-Statuscode angezeigt. Weitere Informationen: [Einschränken des Portalzugriffs mit IP-Adressen](admin/ip-address-restrict.md)

- **Verwalten Sie SharePoint Dokumente**: Dynamics 365 Portale unterstützt nun das Hochladen und Anzeigen von Dokumenten zu und von SharePoint direkt auf einem Entitätsformular oder Webformular in einem Portal. Dadurch können Portalbenutzer Dokumente aus einem Portal anzeigen, herunterladen, hinzufügen und löschen. Portalbenutzer können auch Ordner erstellen, um die Dokumente zu organisieren. Weitere Informationen: [Verwalten von SharePoint-Dokumenten](manage-sharepoint-documents.md).

- **Neuer Portal Content Editor (Vorschau)**: In dieser Vorschau steht ein neuer und vereinfachter Portal-Editor für Dynamics 365 Portale-Anpasser zur Verfügung, um die Lernkurve bei der Anpassung von Dynamics 365 Portale zu reduzieren und die Produktivität eines Anpassers zu erhöhen.

- **Abstimmung aus Statusgründen aktivieren**: Standardmäßig ist eine Idee aktiviert, die eine Abstimmung nur zulässt, wenn der Statusgrund auf "Neu gesetzt ist". Sie können jetzt die Abstimmung über eine Idee für verschiedene Statusgründe aktivieren. Wenn Sie die Abstimmung für verschiedene Statusgründe aktivieren möchten, müssen Sie die Standorteinstellung "Ideas/EnableVotingForStatusReasons" erstellen und den zugehörigen Wert auf die entsprechenden Statusgrundwerte festlegen. 

### <a name="dynamics-365-portals-version-906-for-the-model-driven-apps-in-dynamics-365"></a>Dynamics 365 Portale Version 9.0.6 für die modellgetriebenen Anwendungen in Dynamics 365

Dynamics 365 Portale Version 9.0.6 für die modellgetriebenen Apps in Dynamics 365 hat die folgenden aktuellen Updates und Features gebracht:

- **Dynamics 365 Portale App**: Die Dynamics 365 Portale App bietet eine neue Erfahrung bei der Konfiguration und Verwaltung Ihrer Online-Plattform zur Kommunikation und Zusammenarbeit mit Kunden. Wenn Sie Dynamics 365 Portale Version 9.0 und höher installieren, wird die Dynamics 365 Portale App, die auf dem Framework der einheitlichen Oberfläche basiert, sofort nach dem Auspacken erstellt.

- .**Ein Portal zurücksetzen**: Sie können nun ein Portal zurücksetzen und planen, zu einer anderen Geolokalisierung oder einem anderen Mandanten zu wechseln und das Portal nicht mehr zu verwenden Wenn Sie ein Portal zurücksetzten, werden die Ressourcen des gehosteten Portals gelöscht und die Portal-URL ist nicht mehr verfügbar. Weitere Informationen: [Ein Portal zurücksetzen](admin/reset-portal.md)

- **Um die URL des Portals zu ändern**: Sie können die URL basierend auf den Portal nach der Bereitstellung ändern. Wenn Sie z. B. contosocommunity.microsoftcrmportals.com als Basis URL ausgewählt haben bei der Bereitstellung des Portals, können Sie später zu zu contosocommunityportal.microsoftcrmportals.com auf Ihre Anforderung hin wechseln. Weitere Informationen: [Basis-URL ändern](admin/change-base-url.md)


### <a name="dynamics-365-portals-version-841-for-the-model-driven-apps-in-dynamics-365"></a>Dynamics 365 Portale Version 8.4.1 für die modellgetriebenen Anwendungen in Dynamics 365

Dynamics 365 Portale Version 8.4.1 für die modellgetriebenen Anwendungen in Dynamics 365 bringt eine Reihe von Bugfixes und Leistungssteigerungen sowie die folgenden Funktionen mit sich:

- **Suche im Anlageninhalt von Knowledge-Artikeln und Webdateien**: Anlageninhalt von Knowledge-Artikeln und Webdateien können jetzt durchsucht werden, um die Wahrscheinlichkeit relevanter Suchergebnisse zu erhöhen. Weitere Informationen: [Suche in Dateianhangsinhalt](configure/search-file-attachment.md)
- **Barrierefreiheit**: Die Standardportale (Community-Portal, Partnerportal, Kundenportal, Self-Service-Portal für Mitarbeiter) sind jetzt verfügbar. Allerdings sollten Systemanpasser sicherstellen, dass das Portal nach sämtlichen Anpassungen oder Änderungen weiterhin barrierefrei bleibt.


### <a name="dynamics-365-portals-version-84-for-the-model-driven-apps-in-dynamics-365"></a>Dynamics 365 Portale Version 8.4 für die modellgetriebenen Apps in Dynamics 365

Dynamics 365 Portale Version 8.4 für die modellgetriebenen Anwendungen in Dynamics 365 bringt eine Reihe von Bugfixes und Leistungssteigerungen sowie die folgenden Funktionen mit sich:

- **Auf Portalfehlerprotokolle zugreifen**: Als Portalentwickler können Sie jetzt auf detaillierte Fehlerprotokolle für alle Probleme in Ihrem Portal zugreifen. Das erleichtert Ihnen das Debuggen der Probleme während Sie das Portal entwickeln. Sobald das Portal live geschaltet ist, können Sie das Portal so konfigurieren, dass alle Anwendungsfehler an ein Azure Blob-Speicherkonto, das Sie besitzen, übermittelt werden. Hierdurch können Sie leichter die Probleme debuggen, die von Ihren Kunden gemeldet werden. Weitere Informationen: [Auf Portalfehlerprotokolle zugreifen](admin/view-portal-error-log.md)
- **Portalauthentifizierungsschlüssel erneuern**: Ein Portal verbindet sich mit der Common Data Service-Umgebung über die Azure Active Directory-App. Dazu ist ein Authentifizierungsschlüssel, der mit einer Azure Active Directory-Anwendung verbunden ist, erforderlich. Dieser Schlüssel wird hinzugefügt, wenn Sie Ihr Portal bereitstellen, und er muss alle zwei Jahre erneuert werden. Diese Version des Portale bietet die Möglichkeit, dass Administratoren über den Flow des Schlüssels informiert werden und diesen Schlüssel aus dem Power Apps Portale Administrationscenter erneuern. Weitere Informationen: [Portalauthentifizierungsschlüssel erneuern](admin/manage-auth-key.md)
- **Datenschutz-Grundverordnung in Portalen implementieren**: Als Portaladministrator können Sie jetzt Ihr Portal so konfigurieren, dass es die Standards der Datenschutz-Grundverordnung erfüllt. Sie können auch bestimmte Geschäftsbedingungen angeben, denen die Portalbenutzer zustimmen müssen, um ein Portal zu benutzen. Sie können auch Überprüfungen einrichten, wie beispielsweise, wenn auf ein Portal durch einen minderjährigen Benutzer zugegriffen wird, dass der Benutzer der elterlichen Zustimmung bedarf, um auf das Portal zuzugreifen. Die Implementierung der DSGVO erlaubt es Ihnen, die Zustimmung der Portalbenutzer bezüglich der Verwendung Ihrer persönlichen Daten einzuholen, minderjährige Benutzer zu identifizieren und eine elterliche Zustimmung für minderjährige Benutzer einzuholen. Weitere Informationen: [Implementieren der DSGVO in Portalen](configure/implement-gdpr.md)

### <a name="dynamics-365-portals-version-83-for-the-model-driven-apps-in-dynamics-365"></a>Dynamics 365 Portale Version 8.3 für die modellgetriebenen Apps in Dynamics 365

Dynamics 365 Portale Version 8.3 für die modellgetriebenen Anwendungen in Dynamics 365 hat viele neue Updates und Funktionen:

- **Möglichkeit, Anlagen mit Wissensartikel einzuschließen**: Mit diesem Feature können Sie in Portalen Notizanlagen zusammen mit dem Wissensartikel anzeigen. Um dieses Feature zu aktivieren, müssen Sie die Standorteinstellung KnowledgeManagement/DisplayNotes erstellen und den Wert auf **true** festlegen. Portalbenutzer können auch nach diesen Anlagen suchen. Weitere Informationen: Anzeigen von Dateianlagen mit Knowledge-Artikeln

  > [!Note]
  > Die Suche nach Anlagen ist nur nach der Beschreibung der Notizen und dem Namen der Dateianlage möglich. Der Inhalt der Anlagendatei ist nicht durchsuchbar.
  
- **Verwaltungs-Assistent zum Hinzufügen von Entitäten zum Portal**: Dieses Feature führt einen neuen Verwaltungs-Assistenten ein, um Daten im Portal auf einfache Weise verfügbar zu machen. Die Entität, die mit dem Assistenten erstellt wird, nimmt die Daten Ihrer Organisation und stellt Ihren Portalkunden eine Teilmenge dieser Daten bereit, basierend auf dem von Ihnen gewählten Sicherheits- und Berechtigungsmodell.

- **Import der Metadatenübersetzung**: Mit diesem Feature können Sie die Metadatenübersetzung einer neu aktivierten Sprachen nach der Installation eines Portals importieren. Weitere Informationen: [Metadatenübersetzung importieren](admin/import-metadata-translation.md)

- **Quellcodeverfügbarkeit für Portale**: Eine einmalige Version von Dynamics 365 Portale Code wird im Microsoft Download Center unter MIT-Lizenz für Entwickler zum Download freigegeben. Diese Funktion ermöglicht die Bereitstellung von Portalen für Dynamics 365 On-premises oder in Online-Umgebungen und ermöglicht es Entwicklern, den Code an ihre spezifischen Geschäftsanforderungen anzupassen.

  > [!NOTE]
  > Der Quellcode wird als Arbeitsbeispiel und bedarfsabhängig bereitgestellt. Für Änderungen des Codes wird keine direkte Unterstützung bereitgestellt.

- **Verbesserung der Konfiguration für einmaliges Anmelden (Single Sign-On, SSO) und Unterstützung für Azure Active Directory B2C (Azure AD B2C)**: Im Fall von Portalen, die verbraucherbasierte Anmeldungen erfordern, unterstützt dieses Feature nun Folgendes:
  - Konfigurieren der Portalauthentifizierung zur Verwendung von SSO. 
  - Unterstützung von Azure AD-B2C zur Kundenauthentifizierung.
  - Verwalten der Portalsicherheit in Azure.

  Weitere Informationen: [Azure AD B2C-Anbietereinstellungen für Portale](configure/azure-ad-b2c.md)

- **Unterstützung zeitzonen&ndash;unabhängiger Datumsformate in Portalformularen**: Dieses Feature fügt Unterstützung für die Verhaltensweisen **Nur Datum** und **Zeitzonenunabhängig** für Datums-/Uhrzeitfelder in Portalen hinzu. Weitere Informationen: [Verhalten und Format des Datums- und Uhrzeitfelds](configure/behavior-format-date-time-field.md)

- **Berechtigung für nichtglobale Administratoren, Portale bereitzustellen**: Sie können nun ein Portal bereitstellen, wenn Sie für die CRM-Organisation, die für das Portal ausgewählt ist, der Rolle Systemadministrator zugewiesen sind. Sie können nun auch ein vorhandenes Portal verwalten, wenn Sie eine der folgenden Rollen besitzen:
  - Dynamics 365 Service Administrator
  - Systemadministrator der CRM-Organisation, die für das Portal ausgewählt ist

- **Speichern eines benutzerdefinierten Domänennamens ein Portal**: Mit diesem Feature können Sie den primären Domänennamen eines Portals im Websitedatensatz speichern. Wenn der Domänenname in der Zukunft geändert wird, wird der jeweils aktuelle primäre Domänenname gespeichert.

- **Nachverfolgungscookie für Portale**: Es wird das persistente Cookie Dynamics365PortalAnalytics platziert, wenn ein Benutzer zu einem Portal navigiert. Dieses Cookie läuft nach 90 Tagen ab. Dieses Cookie speichert keine persönlichen Daten des Benutzers und wird von Microsoft verwendet, um Analysen zum Portalservice zu sammeln. Weitere Informationen finden Sie [hier](https://go.microsoft.com/fwlink/p/?linkid=856855) in den Datenschutzbestimmungen für Microsoft-Onlinedienste.

- **Leistungsverbesserung für Kopf- und Fußzeile in Portalen**: Es wurden zwei neue Websiteeinstellungen, Header/OutputCache/Enabled und Footer/OutputCache/Enabled hinzugefügt, um das Zwischenspeichern von Kopfzeilen-/Fußzeilenausgaben zu ermöglichen, wenn diese Einstellungen auf true festgelegt sind. Für neue Benutzer werden diese Standortseinstellungen standardmäßig auf true festgelegt, sodass das Zwischenspeichern von Kopfzeilen- und Fußzeilenausgaben ermöglicht wird. Für bestehende Benutzer, die auf eine neuere Version von Dynamics 365 Portale aktualisieren, ist das Output-Caching standardmäßig deaktiviert. Das bedeutet, dass die Kopf- und Fußzeilenvorlagen jedes Mal, wenn eine Seite geladen wird, analysiert und gerendert werden. Um das Zwischenspeichern von Ausgaben zu aktivieren, müssen die entsprechenden Webvorlagen aktualisiert und die erforderlichen Websiteeinstellungen erstellt werden. Weitere Informationen: [Ausgabezwischenspeicherung für Kopf- und Fußzeile aktivieren](configure/enable-header-footer-output-caching.md)

### <a name="december-2016-updates"></a>Updates für Dezember 2016

Das Update vom Dezember 2016 hat Dynamics 365 Portale viele neue Funktionen gebracht. Diese Updates ermöglichen bessere Interaktionen zwischen Unternehmen, Partnern und Kunden und sorgen für eine schnellere und einfachere Navigation im Portal. Zu den wichtigsten Updates zählen:

- **Unterstützung mehrerer Sprachen:** Unterstützung von Kunden aus mehreren Regionen über ein einzelnes Portal. Weitere Informationen: [Unterstützung für mehrere Sprachen aktivieren](configure/enable-multiple-language-support.md)
- **Unterstützung ostasiatischer Sprachen:** Multi-Byte-Sprachen wie Chinesisch, Japanisch und Koreanisch werden nun unterstützt.
- **Facettierte Suche:** Neue Filter sorgen dafür, dass Kunden Inhalte schneller finden und ermöglichen eine bessere Steuerung der Sichtbarkeit von Inhalten. Weitere Informationen: [Facettierte Suche](configure/improve-portal-search-faceted-search.md)
- **Produktfilterung:** Portalbenutzer können den Zugriff auf Wissensartikel entsprechend dem Produktbesitz einschränken, um eine Informationsflut zu vermeiden.
- **Inhaltzugriffsebenen:** Eine neue Stufe für den Besitz, verknüpft mit einem Portalkontakt, einem Konto oder einer Webrolle, die für die Steuerung des Zugriffs auf Wissensartikel verwendet werden kann, um die Ausrichtung des richtigen Artikels auf das richtige Publikum zu unterstützen und zu verhindern, dass nichtrelevante Artikel angezeigt werden. Weitere Informationen: [Inhaltszugriffsebenen](https://docs.microsoft.com/dynamics365/portals/manage-knowledge-articles-content-levels)
- **Verbesserte Berichterstellung für Wissensartikel:** Das Portal verfolgt, wo ein Wissensartikel im Portal verwendet wurde.
- **Project Service Automation-Integration:** Bietet Zugriff und Sichtbarkeit für aktive und abgeschlossene Projekte in allen Phasen eines Projektlebenszyklus für Partner und Kunden. Teammitglieder, Prüfer und Kunden können Projektstatus, Angebote, Auftragsforen und buchbare Ressourcen im Portal mit dieser Lösung anzeigen. Weitere Informationen: [Project Service Automation integrieren](https://docs.microsoft.com/dynamics365/portals/integrate-project-service-automation)
- **Field Service-Integration:** Stellen Sie Informationen zu aktiven Vereinbarungen, Anlagen, Arbeitsaufträgen, Rechnungen und Supportfällen für Partner und Kunden über diese Lösung zur Verfügung. Weitere Informationen: [Field Service integrieren](https://docs.microsoft.com/dynamics365/portals/integrate-field-service)
- **Partner-Onboarding:** Finden Sie neue Partner für eine verbesserte Vertriebs- und Serviceerfahrung von Kunden. Mögliche Partner können sich über das Portal als Partner bewerben.

### <a name="privacy-notice"></a>Datenschutzbestimmungen

[!INCLUDE[cc-privacy-crm-portals-data-exposed](../../includes/cc-privacy-crm-portals-data-exposed.md)]

Weitere Informationen zu weiteren [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)]-Serviceangeboten finden Sie unter [[!INCLUDE[cc_privacy_note_azure_trust_center](../../includes/cc_privacy_note_azure_trust_center.md)]](https://azure.microsoft.com/support/trust-center/).  
