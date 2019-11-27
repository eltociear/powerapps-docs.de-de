Durch Installation und Aktivierung der [!INCLUDE[pn_gamification](pn-gamification.md)]-Lösung werden Informationen aus dem Benutzerkonto (wie Vorname, Nachname und E-Mail-Adresse) in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] gespeichert, um eine Autorisierung beim [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)]-Service zu ermöglichen. Dieser Service wird in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] gehostet. Dies gilt für alle Benutzer, die im [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)]-Service von einem Administrator aktiviert wurden. Die [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)]-Lösung sendet von einem Administrator konfigurierte Daten zu Key Performance Indicators (KPIs) an den [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Service. Die Daten werden dann im strukturierten [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Speicher sowie im Blobspeicher gespeichert.  Avatar, benutzerdefinierte Auszeichnungen und Unternehmenslogo der einzelnen Benutzer werden zwar in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] gespeichert, aber nicht an [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] zurückgegeben.  
  
Beachten Sie, dass Administratoren und autorisierte Benutzer Daten aus [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] wie Telefonanrufe, Verkaufschancen und gebuchte Umsätze heranziehen können, um KPIs für Spiele zu konfigurieren. Der [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)]-Service tätigt keine Aufrufe an [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] und reagiert nur auf Daten, wie beispielsweise Spiele, in denen KPIs verwendet werden, die an [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] zurückgehen.  
  
Administratoren können den [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)]-TV-Stream auch Veröffentlichen. Spielmanager, die [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)]-TV-Streams einrichten und öffentliches Streaming zulassen, lassen damit auch zu, dass jeder Benutzer, der den Stream-Link hat, den TV-Stream im Internet verfolgen kann.  
  
Administratoren können die [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)]-Funktion auch wieder entfernen, indem sie die Lösung in der [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)]-Organisation deinstallieren.  
  
Die zu [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] gehörigen Komponenten und Services von [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] werden in den folgenden Abschnitten ausführlich vorgestellt.  
  
[!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
[Cloud Services](https://azure.microsoft.com/services/cloud-services/)  
  
 **Designerservice (Webrolle)**  
  
Stellt mehrere Webdienste zur Kommunikation zwischen einer [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)]-Organisation und den mehrinstanzenfähigen [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Komponenten bereit. Beispielsweise werden Gamification-Details in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] SQL-Speicher gespeichert.  Spielberechnungen nutzen die [!INCLUDE[pn_azure_service_bus](pn-azure-service-bus.md)]-Warteschlange, werden zur Bewertung zurückgegeben und im Service angezeigt.  Von Kunden und Benutzern hochgeladener Bilder werden in [!INCLUDE[pn_azure_blob_storage](pn-azure-blob-storage.md)]gespeichert. Alle Anfragen werden anhand von [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] authentifiziert.  
  
[Azure Key Vault](https://azure.microsoft.com/services/key-vault/)  
  
Alle Services speichern Konfigurationsdaten in [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)].  
  
[Azure SQL-Datenbank](https://azure.microsoft.com/services/sql-database/)  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] nutzt SQL [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], um Folgendes zu speichern:  
  
- KPI-Daten  
  
- Spielberechnungen  
  
- Daten der Organisation (des Mandanten)  
  
[Azure-Blobspeicher](https://azure.microsoft.com/services/storage/)  
  
Avatare, Unternehmenslogos und andere vom Kunden hochgeladene Bilder werden in [!INCLUDE[pn_azure_blob_storage](pn-azure-blob-storage.md)] gespeichert.  
  
[Azure Content Delivery Network (CDN)](https://azure.microsoft.com/services/cdn/)  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] nutzt [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Content Delivery Network, um statische Inhalte zur Laufzeit, darunter Bilder (einschließlich hochgeladener Bilder wie Kundenlogos) sowie [!INCLUDE[pn_JavaScript](pn-javascript.md)] und CSS bereitzustellen.  
  
[Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] nutzt [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)], um Benutzer zu authentifizieren und die Berechtigung zur Plattformnutzung zu ermitteln.