---
ms.openlocfilehash: 509ad3f5b1b94378b2c6fd7661510b7aef0e3a23
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61574926"
---
Nach dem Aktivieren der Lernpfaderstellung für eine [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]-Organisation werden Lernpfadinhalte (veröffentlichte oder als Entwurf gespeichert), die von Benutzern (mit den entsprechenden Sicherheitsrechten) erstellt wurden, in [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] gespeichert. Darüber hinaus ermöglicht das Aktivieren dieser Funktion [!INCLUDE[pn_azure_cloud_services](pn-azure-cloud-services.md)] das Erfassen der folgenden Daten im Zusammenhang mit einer [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]-Organisation:  
  
-   Liste der Organisationen im Mandanten  
  
-   [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]-Client und zutreffende Browser-/Betriebssystemkonfiguration der Endbenutzer  
  
-   Nutzungsdaten der Endbenutzer – z.B. mit Lernpfaden verbrachte Zeit oder aufgezeichnete Mausklicks  
  
-   Aggregierte Endbenutzerdaten: Standort, Sicherheitsrolle, Benutzersprache  
  
-   Aggregierte Endbenutzerdaten: Standort, Sicherheitsrolle, Benutzersprache  
  
-   Wörtliches Feedback von Endbenutzern  
  
 Administratoren können die Lernpfaderstellung aktivieren (und anschließend deaktivieren). Dazu dient eine Einstellung auf der Registerkarte **Allgemein** des Dialogfelds **Systemeinstellungen**.  
  
 Die im Rahmen der Lernpfaderstellung verfügbaren [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Komponenten und -Dienste werden in den folgenden Abschnitten ausführlich dargestellt.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Cloud Services](https://azure.microsoft.com/en-us/services/cloud-services/)  
  
 **Webdienst**  
  
 Der Webdienst stellt die Steuerelemente bereit, die auf dem Client durch die Lernpfadruntime gerendert werden. Zudem unterstützt der Webdienst die Designer-API, die von der Lernpfaderstellung verwendet wird. Die Steuerelemente werden vom Dienst in der [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)]-Instanz gespeichert.  
  
 **Compiler (Workerrolle)**  
  
 Die Compilerrolle verwaltet die Veröffentlichung eines Steuerelements in einer Veröffentlichungsgruppe. Der Compiler speichert Nachrichten über den Veröffentlichungsauftrag mithilfe der Warteschlange. Die Ergebnisse werden in der [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)]-Instanz gespeichert.  
  
 [Azure SQL-Datenbank](https://azure.microsoft.com/en-us/services/sql-database/)  
  
 Der Lernpfad verwendet [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] zum Speichern der folgenden Elemente:  
  
-   Steuerelemente, die mithilfe des Lernpfads erstellt werden.  
  
-   Mit der Konfiguration zusammenhängende Lernpfaderstellung.  
  
 [Azure Active Directory](https://azure.microsoft.com/en-us/services/active-directory/)  
  
 Der Lernpfad verwendet [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] zum Authentifizieren des Webdiensts.  
  
 [Azure Traffic Manager](https://azure.microsoft.com/en-us/services/traffic-manager/)  
  
 Der Lernpfad verwendet [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Traffic Manager zum Lastenausgleich beim Webdienst bezüglich Verfügbarkeit und Leistung.  
  
 [Azure Storage Queue](https://azure.microsoft.com/en-us/services/storage/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage Queue wird zum Koordinieren der Kommunikation zwischen den Webdienst- und Compilerrollen verwendet.  
  
 [Azure Blob Storage](https://azure.microsoft.com/en-us/services/storage/)  
  
 Der Lernpfad verwendet [!INCLUDE[pn_azure_blob_storage](pn-azure-blob-storage.md)] zum Speichern des statischen Inhalts (clientseitigen [!INCLUDE[pn_JavaScript](pn-javascript.md)]-Code, Bilder, CSS-Inhalt).  
  
 [Azure Content Delivery Network (CDN)](https://azure.microsoft.com/en-us/services/cdn/)  
  
 CDN wird zum Zwischenspeichern der clientseitigen statischen Inhalte ([!INCLUDE[pn_JavaScript](pn-javascript.md)], Bilder und CSS-Dateien) verwendet, damit diese über das globale Netzwerk CDN bereitgestellt werden können.