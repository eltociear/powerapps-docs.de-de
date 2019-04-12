---
title: Überwachungsübersicht (Common Data Service) | MicrosoftDocs
description: 'Lesen Sie, wie die Überwachungsfähigkeit von Common Data Service genutzt werden kann, um Änderungen von Attribut- und Entitätsdaten im Laufe der Zeit für Analyse- und Berichtszwecke aufzuzeichnen.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: paulliew
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="auditing-overview"></a>Überwachungsübersicht

Organisationen müssen oft verschiedene Vorschriften beachten, um Verfügbarkeit von Kundeninteraktionsverlauf, Überwachungsprotokollen, Zugriffsberichten und Sicherheitsvorfallnachverfolgung sicherzustellen. Organisationen können Änderungen in Common Data Service-Daten für Sicherheit und Analysezwecke nachverfolgen.  
  
 Common Data Service unterstützt eine Überwachungsfunktion, in der sich Entitäts- und Attributdaten innerhalb der Organisation ändern und über einen bestimmten Zeitraum für Analyse- und Berichterstellungszwecke erfasst werden können. Die Überwachung wird für alle benutzerdefinierten und für die meisten anpassbaren Entitäten und Attribute unterstützt. Die Überwachung wird nicht für Metadatenänderungen, Abrufvorgänge, Exportvorgänge oder während der Authentifizierung unterstützt. Weitere Informationen darüber, wie die Überwachung zu konfigurieren, finden Sie unter [Konfigurieren von Entitäten und Attributen für Überwachung](configure-entities-attributes-auditing.md).  
  
## <a name="supported-for-auditing"></a>Unterstützt für Überwachung  
 Nachfolgend sind die Überwachungsfunktionen für Common Data Service aufgelistet:  
<!-- TODO: Jim, I don't think this is online only. Please correct the tokens here. -->
  
* Überwachung anpassbarer Entitäten
* Überwachung benutzerdefinierter Entitäten
* Konfigurieren Sie die Entitäten zur Überwachung
* Konfigurieren Sie die Attribute zur Überwachung
* Recht-basierte Überwachungsprotokollanzeige
* Recht-basierte Überwachungszusammenfassungsanzeige
* Überwachungsprotokolllöschung für eine partitionierte SQL-Datenbank  
* Überwachungsprotokolllöschung für eine nicht-partitionierte SQL-Datenbank 
* Überwachung von datensatzbasierten Erstellungs-, Aktualisierungs- und Löschvorgängen
* Überwachung von Beziehungen (1:n, N:N) 
* Überwachung von Überwachungsereignissen
* Überwachung von Benutzerzugriff
* Einhaltung von regulatorischen Vorgaben
* Überwachungs-APIs für Entwickler
  
## <a name="not-supported-for-auditing"></a>Nicht unterstützt für Überwachung  
 Nachfolgend wird aufgeführt, was für Common Data Service nicht geprüft werden kann:  
  
* Überwachung von Lesevorgängen
* Überwachung von Metadatenänderungen 
  
## <a name="key-concepts"></a>Wichtige Konzepte  
 In der folgenden Aufzählung werden Schlüsselüberwachungskonzepte identifiziert:  
  
-   Sie können die Überwachung auf der Organisations-, Entitäts- und Attributebene aktivieren oder deaktivieren. Wenn die Überwachung auf der Organisationsebene nicht aktiviert ist, wird die Überwachung von Entitäten und Attributen nicht ausgeführt, auch dann nicht, wenn diese aktiviert ist. Standardmäßig wird die Überwachung für alle überprüfbaren Entitätsattribute aktiviert, jedoch auf der Entitäts- und Organisationsebene deaktiviert.  
  
-   Die Möglichkeit, den Überwachungsverlauf abzurufen und anzuzeigen, ist auf Benutzer begrenzt, die bestimmte Sicherheitsrechte haben: Überwachungsverlauf anzeigen und Anzeigen einer Überwachungszusammenfassung. Außerdem gibt es partitionsspezifische Rechte: Anzeigen der Überwachungspartitionen und Überwachungspartitionen löschen. Lesen Sie die spezifische Nachrichtenanforderungsdokumentation für Informationen zu den erforderlichen Rechten für jede Nachricht.  
  
-   Überwachte Datenänderungen werden in Datensätzen der **Überwachungs**-Entität gespeichert.  
  
## <a name="data-that-can-be-audited"></a>Überwachbare Daten  
 In der folgenden Auflistung werden die Daten und Vorgänge identifiziert, die überwacht werden können:  
  
-   Datensatzbasierte Erstellungs-, Aktualisierungs- und Löschvorgänge  
  
-   Änderungen an den freigegebenen Rechten an einem Datensatz.  
  
-   N:N-Zuordnung oder Aufheben der Zuordnung von Datensätzen.  
  
-   Änderungen an Sicherheitsrollen.  
  
-   Überwachungsänderungen auf Entitäts-, Attribut- und Organisationsebene. Beispielsweise Aktivierung der Überwachung für eine Entität.  
  
-   Löschung von Überwachungsprotokollen.  
  
-   Wann (Datum/Zeit) ein Benutzerzugriff auf Common Data Service-Daten erfolgt, wie lange und über welchen Client.  
  
 Das Aktivieren oder Deaktivieren der Sicherheit auf Feldebene durch Festlegen des <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.IsSecured>-Attributs kann nicht überwacht werden.  
  
### <a name="see-also"></a>Siehe auch
 [Datenverwaltung in Dynamics 365](/dynamics365/customer-engagement/developer/manage-data)   
 [Überwachung von Entitätsdatenänderungen](/dynamics365/customer-engagement/developer/audit-entity-data-changes)   
 [Konfigurieren von Entitäten und Attributen für die Überwachung](configure-entities-attributes-auditing.md)       
 [Blog: Wiederherstellen gelöschter CRM-Daten und Neuerstellung mit der CRM-API](http://blogs.msdn.com/b/crm/archive/2011/05/23/recover-your-deleted-crm-data-and-recreate-them-using-crm-api.aspx)