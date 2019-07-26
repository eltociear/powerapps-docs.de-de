---
ms.openlocfilehash: ac90bfc27e03047cf422c44c83f550608d67b57e
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2019
ms.locfileid: "67212847"
---
Durch die Aktivierung der Portalfunktionen für [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] können [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]-Daten, wie z.B. Kundenname, Produktname, Anfragenummer oder beliebige benutzerdefinierte Entitätsdaten, über ein [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]-Portal für externen Zugriff verfügbar gemacht werden. Alle über dieses Portal zur Verfügung gestellten Daten werden im Speicher von Microsoft [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Web-Apps zur Zwischenspeicherung sowie als Dateien auf einer lokalen Festplatte gespeichert, um die Funktionen für die Portalsuche zu aktivieren.

Ein Mandantenadministrator aktiviert [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]-Portale, indem er sie durch das [!INCLUDE[pn_dyn_365_admin_center](../includes/pn-dyn-365-admin-center.md)] konfiguriert, das außerdem ein Paket (mit Lösungen und Daten) in der gewählten [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]-Instanz installiert. Ein Mandantenadministrator oder ein [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]-Benutzer, der als Portaladministrator eingerichtet ist, kann anschließend festlegen, welche Daten über das Portal verfügbar gemacht werden. Um die Portalfunktionen später wieder zu deaktivieren, kann ein Mandantenadministrator das Abonnement für das Portal-Add-On in [!INCLUDE[pn_Office_365](pn-office-365.md)] stornieren.

Wichtige [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Komponenten und ‑Dienste in Verbindung mit den Portalfunktionen sind:
- [Azure-Web-Apps](https://azure.microsoft.com/services/app-service/web/): [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]Web-Apps werden zum Hosten des Portals [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]in verwendet.
- [Azure-Traffic Manager](https://azure.microsoft.com/services/traffic-manager/): [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]Traffic Manager wird verwendet, um die Hochverfügbarkeit des Diensts sicherzustellen, indem der Benutzer an die Web-Apps weiterleitet, die aktiv sind und ausgeführt werden. 
- [Azure Service Bus](https://azure.microsoft.com/services/service-bus/): [!INCLUDE[pn_azure_service_bus](pn-azure-service-bus.md)](Themen/Abonnements) wird für die Cache Validierung der Portale verwendet. [!INCLUDE[pn_azure_service_bus](pn-azure-service-bus.md)] speichert vorübergehend Meldungen, die bei Änderungen eines Datensatzes in Verbindung mit dem Portal in [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] ausgelöst und anschließend zur Cacheinvalidierung an Web-Apps übergeben werden. 
- [Azure Key Vault](https://azure.microsoft.com/services/key-vault/): Alle Dienste speichern Konfigurationsdaten in [!INCLUDE[pn_azure_key_vault](pn_azure_key_vault.md)].
- [Azure Storage](https://azure.microsoft.com/services/storage/): Daten im Zusammenhang mit der Organisation, dem Mandanten und dem Portal [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] werden im Speicher gespeichert.
- [Azure Active Directory](https://azure.microsoft.com/services/active-directory/): Alle Webdienste, die [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] für die Authentifizierung verwendet werden.
