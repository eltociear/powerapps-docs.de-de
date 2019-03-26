---
title: So erstellen und bearbeiten Sie Felder für Common Data Service for Apps | MicrosoftDocs
ms.custom: ''
ms.date: 02/08/2019
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
ms.assetid: d88677fa-2caf-47b0-aec6-10a25a7ec9c3
caps.latest.revision: 55
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="how-to-create-and-edit-fields"></a>So erstellen und bearbeiten Sie Felder

In Common Data Service for Apps definieren die Felder die einzelnen Datenelemente, die verwendet werden, um Daten in einer Entität zu speichern. Felder werden von Entwicklern auch als *Attribute* bezeichnet. 
  
Bevor Sie ein benutzerdefiniertes Feld erstellen, prüfen Sie, ob die Verwendung eines vorhandenen Feldes Ihre Anforderungen erfüllen könnte. Weitere Informationen [Neue Metadaten oder bestehende Metadaten erstellen](create-edit-metadata.md#create-new-metadata-or-use-existing-metadata)

Sie können zwei Designer verwenden, um Felder zu erstellen oder zu bearbeiten:

|Designer| Beschreibung|
|--|--|
|[PowerApps-Portal](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|Gibt eine einfache konzentrierte Erfahrung, aber einige besondere Einstellungen sind nicht verfügbar.<br />Weitere Informationen: [Erstellen und Bearbeiten von Feldern für Common Data Service for Apps mit dem PowerApps-Portal](create-edit-field-portal.md)|
|Projektmappen-Explorer|Nicht so einfach, aber gibt mehr Flexibilität für weniger allgemeine Anforderungen.<br />Weitere Informationen: [Erstellen und Bearbeiten von Feldern für Common Data Service for Apps mit PowerApps-Lösungsexplorer](create-edit-field-solution-explorer.md) |

> [!NOTE]
> Sie können Felder in Ihrer Umgebung auch wie folgt erstellen:
> - In modellgesteuerten Apps wählen Sie **Neues Feld** im Formular-Editor aus.
> - Importieren Sie eine Lösung, die die Definition der Felder enthält.
> - Verwenden Sie Power-Abfrage, um neue Entitäten zu erstellen und diese mit Daten auszufüllen.<br />Weitere Informationen:  [Daten einer Entität in Common Data Service für Apps mithilfe der Power-Abfrage hinzufügen](/powerapps/maker/common-data-service/data-platform-cds-newentity-pq).
> - Ein Entwickler kann [Metadatendienste](/powerapps/developer/common-data-service/use-web-services#metadata-services) verwenden, um ein Programm zum Schreiben, um Felder zu erstellen und zu aktualisieren.

Die Informationen in diesem Thema helfen Ihnen auswählen, welche Designer Sie verwenden können. 

Sie sollten das PowerApps-Portal verwenden, um Felder Common Data Service for Apps zu erstellen und zu bearbeiten, außer Sie müssen eine der folgenden Anforderungen erfüllen:

- Erstellen eines Suchfeld für Kunden. 
   - Weitere Informationen: [Unterschiedliche Suchmethoden](types-of-fields.md#different-types-of-lookups)
- Erstellen eines Felds in einer Lösung, die keine CDS-Standardlösung ist. 
   - Weitere Informationen finden Sie in [Überblick zu Lösungen](solutions-overview.md).
- Festlegen von Statusgrundübergängen. 
   - Weitere Informationen: [Festlegen von Statusgrundübergängen für benutzerdefinierte Entitäten](define-status-reason-transitions.md)
- Mehrere Felder gleichzeitig bearbeiten.
- Aktivieren der Überwachung. 
   - Mehr Informationen: [Überblick über die Auditierung](../../developer/common-data-service/auditing-overview.md)
- Sicherheit auf Feldebene aktivieren. 
   - Mehr Informationen: [Entitäten für die Feldsicherheit](../../developer/common-data-service/field-security-entities.md)
- Auswählen, ob das Feld in interaktiven Funktionen im globalen Filter angezeigt wird. 
   - Mehr Informationen: [Konfigurieren Sie modellgetriebene interaktive Dashboards für Anwendungen.](../model-driven-apps/configure-interactive-experience-dashboards.md)
- Auswählen, ob das Feld in Dashboards für interaktive Funktionen sortierbar ist. 
   - Mehr Informationen: [Konfigurieren Sie modellgetriebene interaktive Dashboards für Anwendungen.](../model-driven-apps/configure-interactive-experience-dashboards.md)
- Festlegen einer Anforderungsstufe "Eingabe empfohlen" für das Feld 
   - Weitere Informationen: [Erstellen von Geschäftsregeln und Empfehlungen zur Anwendung eines Modell-getriebenen App-Formulars](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md)
- Verwaltete Eigenschaften für ein Feld einrichten 
   - Weitere Informationen: [Verwaltete Eigenschaften für Felder festlegen](set-managed-properties-for-field.md)

> [!NOTE]
> Sie können ein Suchfeld im PowerApps-Portal oder im Projektmappen-Explorer erstellen, indem Sie eine 1: n-Beziehung für die Entität erstellen. Nur der Projektmappen-Explorer bietet die Option, um diese Beziehung beim Erstellen eines Felds zu erstellen.

## <a name="community-tools"></a>Community-Tools

**[Attribut-Manager](https://www.xrmtoolbox.com/plugins/DLaB.Xrm.AttributeManager/)** ist ein Tool, das die XrmToolbox-Community für CDS for Apps entwickelt hat. Weitere Informationen finden Sie im Thema [Entwicklertools](https://docs.microsoft.com/dynamics365/customer-engagement/developer/developer-tools) für von der Community entwickelte Tools.

> [!NOTE]
> Die Communitytools sind kein Produkt von Microsoft und es wird kein Support für die Communitytools angeboten. Wenn Sie Fragen zu dem Tool haben, setzen Sie sich bitte mit dem Herausgeber in Verbindung. Weitere Informationen: [XrmToolBox](https://www.xrmtoolbox.com).

### <a name="see-also"></a>Siehe auch  
[Erstellen und Bearbeiten von Feldern für Common Data Service für Apps mit PowerApps-Portals](create-edit-field-portal.md)<br />
[Erstellen und Bearbeiten von Feldern für Common Data Service für Apps mit PowerApps Lösungs-Explorer](create-edit-field-solution-explorer.md)<br />
[Feldtypen und Felddatentypen](types-of-fields.md)<br />
[Dokumentation für Entwickler: Arbeiten mit Attributmetadaten](/dynamics365/customer-engagement/developer/org-service/work-attribute-metadata)
 
