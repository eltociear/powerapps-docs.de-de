---
ms.openlocfilehash: 943aa1eb128341b960270d21a53cec47003bcec4
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61577502"
---
Die Funktion zur Mithilfe für die Verbesserung von [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] sendet [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)]-Nutzungsinformationen wie Betriebssystem, Browserdetails, anwendungsspezifische Informationen zu [!INCLUDE[pn_unified_service_desk](../includes/pn-unified-service-desk.md)] und die [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)]-Version des Computers, auf dem der Client installiert ist. [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] sendet die Informationen an [!INCLUDE[cc_Microsoft](cc-microsoft.md)] über eine sichere Verbindung mit Organisationsinformationen und speichert sie in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Table Storage.
  
> [!NOTE]
>  Das Feature „Organisationsinformationen“ bietet Systemadministratoren einer [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)]-Organisation einen schnellen Überblick über die Nutzung einer Organisation. Systemadministratoren können neben den aktivsten Benutzern die Zahl der initiierten SDK-Anforderungen und der SDK-Benutzeransichten anzeigen.
  
 Die von der Funktion zur Mithilfe für die Verbesserung von Unified Service Desk abgedeckten [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Komponenten und -Dienste sind unten aufgelistet.  
  
> [!NOTE]
>  Weitere Informationen über zusätzliche [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Dienstangebote finden Sie im [Microsoft Azure Trust Center](https://azure.microsoft.com/en-us/support/trust-center/).  
  
 [Cloud Services](https://azure.microsoft.com/en-us/services/cloud-services/) – OrgInsights-Data-REST-API (Webrolle)  
  
 Diese Webrolle akzeptiert Anforderungen von Diagrammen zur Anzeige von Daten im Organisationsinformationen-Feature. Die API liest aggregierte Daten aus [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Tabellen und gibt diese zurück.  
  
 [Azure Blob Storage](https://azure.microsoft.com/en-us/services/storage/blobs/)  
  
 Die Telemetrierohdaten einer [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)]-Organisation werden vom (auf jedem Skalierungsgruppencomputer ausführbaren) Monitoring Agent gesammelt und im strukturierten Format (binären Format) in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage hochgeladen.  
  
 [Azure Table Storage](https://azure.microsoft.com/en-us/services/storage/tables/)  
  
 Telemetrierohdaten in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage werden in der Azure Table Storage-Instanz, die vom Cloud Service gelesen wird, aggregiert und gespeichert.  
  
 [Azure Active Directory](https://azure.microsoft.com/en-us/services/active-directory/)  
  
 Das Organisationsinformationen-Feature nutzt den [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)]-Dienst zur Authentifizierung von Webdiensten.  
  
 [Azure Service Bus](https://azure.microsoft.com/en-us/services/service-bus/)  
  
 Der Monitoring Agent erstellt Nachrichten beim Hochladen von Daten in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage und stellt diese in die Warteschlange. Diese Nachrichten werden von der CMA-Pipe zur Aggregation der hochgeladenen Daten entgegengenommen.