Nach dem Aktivieren der Lernpfaderstellung für eine [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]-Organisation werden Lernpfadinhalte (veröffentlichte oder als Entwurf gespeichert), die von Benutzern (mit den entsprechenden Berechtigungen) erstellt wurden, in [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] gespeichert. Darüber hinaus ermöglicht das Aktivieren dieses Features [!INCLUDE[pn_azure_cloud_services](pn-azure-cloud-services.md)] das Erfassen von Daten im Zusammenhang mit einer [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]-Organisation:  
  
-   Liste der Organisationen im Mandanten  
  
-   [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]-Client und zutreffende Browser-/Betriebssystemkonfiguration der Endbenutzer  
  
-   Nutzungsdaten der Endbenutzer – z. B. mit Lernpfaden verbrachte Zeit oder aufgezeichnete Mausklicks  
  
-   Aggregierte Endbenutzerdaten – Standort, Sicherheitsrolle, Benutzersprache  
  
-   Aggregierte Endbenutzerdaten – Standort, Sicherheitsrolle, Benutzersprache  
  
-   Wörtliches Feedback von Endbenutzern  
  
 Administratoren können die Lernpfaderstellung aktivieren (und anschließend deaktivieren). Dazu dient eine Einstellung auf der Registerkarte **Allgemein** des Dialogfelds **Systemeinstellungen**.  
  
 Die im Rahmen der Lernpfaderstellungs-Funktionalität verfügbaren [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Komponenten und -Dienste werden in den folgenden Abschnitten ausführlich dargestellt.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Cloud Services](https://azure.microsoft.com/services/cloud-services/)  
  
 **Webdienst**  
  
 Webdienst stellt die Steuerelemente bereit, die auf dem Client durch die Lernpfadruntime gerendert werden. Webdienst unterstützt auch die Designer-API, die von der Lernpfaderstellung verwendet wird. Die Steuerelemente werden vom Dienst bei [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] gespeichert.  
  
 **Compiler (Workerrolle)**  
  
 Compilerrolle verwaltet die Veröffentlichung eines Steuerelements in einer Veröffentlichungsgruppe. Compiler speichert Nachrichten über den Veröffentlichungsauftrag mithilfe der Warteschlange. Die Ergebnisse werden in [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] gespeichert.  
  
 [Azure SQL-Datenbank](https://azure.microsoft.com/services/sql-database/)  
  
 Der Lernpfad verwendet [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] zum Speichern der folgenden Elemente:  
  
-   Steuerelemente, die mithilfe des Lernpfads erstellt werden.  
  
-   Mit der Konfiguration zusammenhängende Lernpfaderstellung.  
  
 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
 Lernpfad verwendet [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] zum Authentifizieren des Webdiensts.  
  
 [Azure Traffic Manager](https://azure.microsoft.com/services/traffic-manager/)  
  
 Lernpfad verwendet [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Traffic Manager zum Lastenausgleich beim Webdienst bezüglich Verfügbarkeit und Leistung.  
  
 [Azure Storage-Warteschlange](https://azure.microsoft.com/services/storage/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage-Warteschlange wird zum Koordinieren der Kommunikation zwischen den Webdienst- und Compilerrollen verwendet.  
  
 [Azure Blob Storage](https://azure.microsoft.com/services/storage/)  
  
 Lernpfad verwendet [!INCLUDE[pn_azure_blob_storage](pn-azure-blob-storage.md)] zum Speichern der statischen Inhalte (clientseitiges [!INCLUDE[pn_JavaScript](pn-javascript.md)], Bilder, CSS-Inhalte).  
  
 [Azure Content Delivery Network (CDN)](https://azure.microsoft.com/services/cdn/)  
  
 CDN wird zum Zwischenspeichern der clientseitigen statischen Inhalte ([!INCLUDE[pn_JavaScript](pn-javascript.md)], Bilder und CSS-Dateien) verwendet, damit diese über das globale Netzwerk CDN bereitgestellt werden können.