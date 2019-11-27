Durch die Aktivierung der Relevanzsuche werden Daten der beteiligten Entitäten und Attribute in Ihrer [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)]-Instanz in einem [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Suchindex synchronisiert und gespeichert.  
  
 Die Relevanzsuche ist standardmäßig deaktiviert. Der Systemadministrator muss die Funktion in einer [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)]-Instanz aktivieren. Nach Aktivierung der Relevanzsuche haben die Systemadministratoren und Systemanpasser die volle Kontrolle über die im [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Suchindex synchronisierten Daten.  
  
 Über das Dialogfeld **Relevanzsuche konfigurieren** in den **Anpassungstools** können Systemanpasser spezifische Entitäten für die Suche auswählen und dann die zugehörigen Ansichten für die Schnellsuche konfigurieren, um die durchsuchbaren Attribute auszuwählen. Datenänderungen werden über eine sichere Verbindung zwischen [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] und [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Search kontinuierlich synchronisiert.  Die Konfigurationsdaten sind verschlüsselt und erforderliche geheime Daten werden in [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)] gespeichert.  
  
 Azure-Komponenten und ‑Dienste, die im Rahmen der Relevanzsuche verfügbar sind, werden in den folgenden Abschnitten ausführlich dargestellt.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc_privacy_note_azure_trust_center.md)]  
  
 [Azure Search-Dienste](https://azure.microsoft.com/services/search/)  
  
 Der [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Suchindex ermöglicht hochwertige Suchergebnisse bei kurzen Reaktionszeiten.  [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Search bietet leistungsstarke und anspruchsvolle Suchfunktionen der nächsten Generation für [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)].  Dabei handelt es sich um einen dedizierten Suchdienst außerhalb von [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)], der von [!INCLUDE[pn_Windows_Azure](pn-windows-azure.md)] bereitgestellt wird. Alle neuen [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Suchindizes werden im Ruhezustand verschlüsselt.  Wenn Sie sich vor dem 24. Januar 2018 angemeldet haben, müssen Sie die Daten neu indizieren, indem Sie die Relevanzsuche abwählen, eine Stunde warten und sie wieder auswählen.  
  
 [Azure SQL-Datenbank](https://azure.microsoft.com/services/sql-database/)  
  
 Die Relevanzsuche nutzt die [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] zum Speichern von:  
  
-   Organisations‑ und entsprechende indexbezogene Konfigurationsdaten  
  
-   Suchdienst‑ und ‑indexbasierte Metadaten  
  
-   Systemmetadaten‑ und ‑datenaktivitäten bei der Synchronisierung von Änderungen  
  
-   Autorisierungsdaten zur Aktivierung von verbesserter Sicherheit auf Zeilenebene  
  
[Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/)  
  
Die [!INCLUDE[pn_azure_event_hubs](pn-azure-event-hubs.md)]-Komponente wird für den Nachrichtenaustausch zwischen [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] und [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] und zur Wartung von Arbeitsaufgaben verwendet, die bei der Synchronisierung verwaltet werden. In jeder Nachricht werden Informationen wie die Organisations-ID und der Entitätsname für die Datensynchronisierung gespeichert.  
  
[Azure Service Fabric Cluster](https://azure.microsoft.com/services/service-fabric/)  
  
Die Verarbeitung und Indizierung erfolgt mithilfe von Mikrodiensten, die auf virtuellen Computern bereitgestellt werden, die von der Service Fabric-Laufzeit verwaltet werden. Die Such-APIs und der Datensynchronisierungsprozess werden ebenfalls im Service Fabric-Cluster gehostet.  
  
Service Fabric ist das Ergebnis jahrelanger Erfahrungen von Microsoft mit der Bereitstellung unternehmenswichtiger Clouddienste und hat sich seit mittlerweile fünf Jahren in der Produktion bewährt. Es handelt sich um das Technologiefundament, auf dem wir unsere [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Kerninfrastruktur ausführen, durch die Dienste, wie u. a. [!INCLUDE[pn_skype_for_business](pn-skype-for-business.md)], [!INCLUDE[pn_intune](pn-intune.md)], [!INCLUDE[pn_azure_event_hubs](pn-azure-event-hubs.md)], [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Data Factory, [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] DocumentDB, [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] und [!INCLUDE[pn_cortana](pn-cortana.md)], funktionieren – diese können auf die Verarbeitung von über 500 Mio. Auswertungen pro Sekunde skaliert werden.  
  
[Azure-VM-Skalierungsgruppen](https://azure.microsoft.com/services/virtual-machine-scale-sets/)  
  
[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-VM-Skalierungsgruppen sind flexibel und zur Unterstützung horizontal hochskalierter Workloads konzipiert. Der [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)]-Cluster wird auf Skalierungsgruppen für virtuelle Computer ausgeführt. Die Mikrodienste für die Verarbeitung und Indizierung von Daten werden auf den Skalierungsgruppen gehostet und von der Service Fabric-Laufzeit verwaltet.  
  
[Azure Key Vault](https://azure.microsoft.com/services/key-vault/)  
  
[!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)] wird für die sichere Verwaltung von Zertifikaten, Schlüsseln und anderen geheimen Daten verwendet, die im Suchprozess zum Einsatz kommen.  
  
[Azure-Speicher (BLOB-Speicher)](https://azure.microsoft.com/services/storage/blobs/?b=16.38)  
  
Kundendatenänderungen werden für maximal zwei Tage im [!INCLUDE[pn_azure_blob_storage](pn_azure_blob_storage.md)] gespeichert.  Diese Blobs werden mithilfe der neuesten Funktion im [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Storage-SDK verschlüsselt, mit der die symmetrische und asymmetrische Verschlüsselung sowie die Integration in [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)] unterstützt werden. Mit [!INCLUDE[pn_crm_8_2_0_online_subsequent](pn-crm-8-2-0-online-subsequent.md)] werden die Dokumente, die in den Hinweisen und Anlagen von E-Mail-Nachrichten und Terminen gefunden werden, auch im Blob-Speicher synchronisiert.  
  
[Azure Active Directory Service](https://azure.microsoft.com/services/active-directory/)  
  
[!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] dient zur Authentifizierung zwischen den [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)]- und [!INCLUDE[pn_Windows_Azure](pn-windows-azure.md)]-Diensten.  
  
[Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/)  
  
Der [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Load Balancer dient dazu, eingehenden Datenverkehr unter fehlerfreien Serviceinstanzen in den Clouddiensten oder virtuellen Computern zu verteilen, die in einem Lastenausgleichssatz definiert sind. Die Relevanzsuche verwendet ihn zum Lastenausgleich bei den Endpunkten einer Bereitstellung.  
  
[Azure Virtual Networks](https://azure.microsoft.com/documentation/articles/virtual-networks-overview/)  
  
Die virtuellen Computer auf dem Service Fabric-Cluster, die in einem oder mehreren Subnetzen ausgeführt werden, sind durch das [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Virtual Network verbunden. Die Sicherheitsrichtlinien, DNS-Einstellungen, Routentabellen und IP-Adressen werden vollständig in diesem virtuellen Netzwerk gesteuert. Netzwerksicherheitsgruppen werden genutzt, um Sicherheitsregeln auf das virtuelle Netzwerk anzuwenden. Diese Regeln ermöglichen oder verweigern Datenverkehr mit den virtuellen Computern im virtuellen Netzwerk.