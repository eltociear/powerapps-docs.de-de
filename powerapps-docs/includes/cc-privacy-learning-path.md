---
ms.openlocfilehash: 719e72ff70580386b9b0a9bca3dcdc591574d026
ms.sourcegitcommit: 982cab99d84663656a8f73d48c6fae03e7517321
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/28/2019
ms.locfileid: "67456989"
---
Das Aktivieren der Lernpfadfunktion (für statisches HTML) ermöglicht das Speichern von Bildern und Skripts im [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Content Delivery Network (CDN). Dazu werden alle angezeigten dynamischen Inhalte in der [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Redis Cache-Instanz gespeichert, die als vorgeschalteter Speicher für die [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] SQL-Datenbank-Instanz verwendet wird.  
  
 Die Lernpfadfunktion kann von einem Administrator in einer [!INCLUDE[pn_crm_online_shortest](pn-crm-online-shortest.md)]-Instanz über die Einstellung für den interaktiven Begleiter in der [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)]-Organisation aktiviert oder deaktiviert werden.  
  
 Die im Rahmen der Lernpfadfunktionalität verfügbaren [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Komponenten und -Dienste werden in den folgenden Abschnitten ausführlich dargestellt.  
  
> [!NOTE]
>  Weitere Informationen über zusätzliche Azure-Dienstangebote finden Sie im [Microsoft Azure Trust Center](https://azure.microsoft.com/support/trust-center/).  
  
 [Cloud Services](https://azure.microsoft.com/services/cloud-services/)  
  
 **Lernpfadruntime (Webrolle)**  
  
 Dies ist die Webanwendung, die den Benutzern den Inhalt zur Verfügung stellt.  
  
 **Lernpfaddienst (Workerrolle)**  
  
 Die Workerrolle ist für die Verarbeitung der Daten aus [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] SQL-Datenbank und deren Zwischenspeicherung in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Redis Cache verantwortlich.  
  
 [Azure SQL-Datenbank](https://azure.microsoft.com/services/sql-database/)  
  
 Der Lernpfad verwendet SQL-Datenbank, um Folgendes zu speichern:  
  
-   Inhalt  
  
-   Inhaltsmetadaten  
  
-   Systemmetadaten  
  
 [Azure Blob Storage](https://azure.microsoft.com/services/storage/)  
  
 Der HTML-Code, Bilder, [!INCLUDE[pn_JavaScript](pn-javascript.md)] und CSS werden in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage gespeichert.  
  
 [Azure Content Delivery Network (CDN)](https://azure.microsoft.com/services/cdn/)  
  
 Der Lernpfad nutzt [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Content Delivery Network, um statische Inhalte für die Umfragelaufzeit bereitzustellen, z.B. HTML, Bilder, [!INCLUDE[pn_JavaScript](pn-javascript.md)] und CSS.  
  
 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
 Der Lernpfad nutzt den [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)]-Dienst zur speziellen Webdienstauthentifizierung für den Designer. Der Designer steht Kunden und Partnern zurzeit noch nicht zur Verfügung. Daher erfolgt die Authentifizierung ausschließlich in der [!INCLUDE[cc_Microsoft](cc-microsoft.md)]-Domäne.  
  
 [Azure Redis Cache](https://azure.microsoft.com/services/cache/)  
  
 Der Lernpfad nutzt [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Redis Cache zur Zwischenspeicherung dynamischer Inhalte für Benutzer.  
  
 [Azure Traffic Manager](https://azure.microsoft.com/services/traffic-manager/)  
  
 Der Lernpfad nutzt Traffic Manager zur verbesserten Verfügbarkeit wichtiger Anwendungen durch Überwachen Ihrer [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Websites oder externer Websites und Dienste. Benutzer werden bei Ausfällen automatisch an neue Standorte weitergeleitet.  
  
 [Azure Resource Manager](https://azure.microsoft.com/features/resource-manager/)  
  
 Der Lernpfad ermöglicht mit [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Resource Manager die Bereitstellung von CDN, Redis Cache, SQL-Datenbank und Clouddiensten als Ressourcengruppen, sodass diese mit einheitlichem Status und wiederholt bereitgestellt werden können.