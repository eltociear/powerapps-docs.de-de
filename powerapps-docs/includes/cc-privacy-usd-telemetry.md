Die Funktion zur Mithilfe zur Verbesserung [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] sendet [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] Nutzungsinformationen wie Betriebssystem, Browserdetails, [!INCLUDE[pn_unified_service_desk](../includes/pn-unified-service-desk.md)] anwendungsspezifische Informationen und [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] Version des Computers, auf dem der Client installiert ist. [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] sendet die Informationen an [!INCLUDE[cc_Microsoft](cc-microsoft.md)] über eine sichere Verbindung an Organisationsinformationen und speichert sie im [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Tabellenspeicher.
  
> [!NOTE]
>  Organization Insights bietet Systemadministratoren einer [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)]-Organisation einen schnellen Überblick über die Nutzung einer Organisation. Systemadministratoren können neben den aktivsten Benutzern die Zahl der initiierten SDK-Anfragen und der SDK-Benutzeransichten anzeigen.
  
 Die von den Funktionen für die Mithilfe zur Verbesserung von Unified Service Desk abgedeckten [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Komponenten und -Dienste werden unten aufgelistet.  
  
> [!NOTE]
>  Weitere Informationen über zusätzliche [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Serviceangebote finden Sie im [Microsoft Azure Trust Center](https://azure.microsoft.com/support/trust-center/).  
  
 [Cloud Services](https://azure.microsoft.com/services/cloud-services/) OrgInsights-Daten-REST API (Webrolle)  
  
 Diese Webrolle akzeptiert Anfragen von Diagrammen zur Anzeige von Daten in Organisationsinformationen. Die API liest aggregierte Daten aus [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Tabellen und gibt diese zurück.  
  
 [Azure Blob Storage](https://azure.microsoft.com/services/storage/blobs/)  
  
 Die Telemetrie-Rohdaten einer [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)]-Organisation werden vom (auf jedem Skalierungsgruppencomputer ausführbarem) Monitoring Agent gesammelt und im strukturierten Format (binären Format) im [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-BLOB-Speicher hochgeladen.  
  
 [Azure-Tabellenspeicher](https://azure.microsoft.com/services/storage/tables/)  
  
 Telemetrie-Rohdaten in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage werden im Azure-Tabellenspeicher, der vom Cloud Service gelesen wird, aggregiert und gespeichert.  
  
 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
 Organisationsinformationen nutzen den [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)]-Service zur Authentifizierung von Webdiensten.  
  
 [Azure Service Bus](https://azure.microsoft.com/services/service-bus/)  
  
 Der Monitoring Agent erstellt Nachrichten beim Hochladen von Daten in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage und stellt diese in die Warteschlange. Diese Nachrichten werden von der CMA-Pipe zur Aggregation der hochgeladenen Daten entgegengenommen.