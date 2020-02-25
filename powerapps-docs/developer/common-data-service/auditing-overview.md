---
title: Überwachungsübersicht (Common Data Service) | Microsoft-Dokumentation
description: Lesen Sie, wie die Überwachungsfähigkeit Common Data Service genutzt werden kann, um Änderungen von Attribut- und Entitätsdaten im Laufe der Zeit für Analyse- und Berichtszwecke aufzuzeichnen.
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
ms.openlocfilehash: 71f39d432e551df456f3d339155d1f3105d6891b
ms.sourcegitcommit: 5bfd0448f1d5ca3d938e3bd928d1dd3d4042afff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/28/2020
ms.locfileid: "2992808"
---
# <a name="auditing-overview"></a>Überwachungsübersicht

Organisationen müssen oft verschiedene Vorschriften beachten, um Verfügbarkeit von Kundeninteraktionsverlauf, Überwachungsprotokollen, Zugriffsberichten und Sicherheitsvorfallnachverfolgung sicherzustellen. Organisationen können Änderungen in Common Data Service-Daten für Sicherheit und Analysezwecke nachverfolgen.  
  
 Common Data Service unterstützt eine Überwachungsfunktion, in der sich Entitäts- und Attributdaten innerhalb der Organisation ändern und über einen bestimmten Zeitraum für Analyse- und Berichterstellungszwecke erfasst werden können. Die Überwachung wird für alle benutzerdefinierten und für die meisten anpassbaren Entitäten und Attribute unterstützt. Die Überwachung wird nicht für Metadatenänderungen, Abrufvorgänge, Exportvorgänge oder während der Authentifizierung unterstützt. Weitere Informationen darüber, wie die Überwachung zu konfigurieren, finden Sie unter [Konfigurieren von Entitäten und Attributen für Überwachung](configure-entities-attributes-auditing.md).  
  
## <a name="supported-for-auditing"></a>Unterstützt für Überwachung  
 Nachfolgend sind die Überwachungsleistung für Common Data Service aufgelistet:  
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
 Nachfolgend wird gezeigt, was für Common Data Service nicht überwacht werden kann:  
  
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
   
 [Konfigurieren von Entitäten und Attributen für die Überwachung](configure-entities-attributes-auditing.md) 
