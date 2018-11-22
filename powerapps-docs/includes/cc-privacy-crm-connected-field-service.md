Wenn Sie [!INCLUDE[pn_connected_field_service_msdyn365](pn-connected-field-service-msdyn365.md)] installieren und Ihre [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Abonnementinformationen angeben, werden die erforderlichen [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Ressourcen (im Folgenden aufgeführt) bereitgestellt, und Ihre [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)]-Instanz sendet Daten (z. B. Befehle und Registrierungen) an [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Auf diese Weise werden IoT-fähige Szenarios möglich, in denen Geräte registriert werden und dann Befehle an diese gesendet und von ihnen empfangen werden. Administratoren können Connected Field Service deinstallieren, um die entsprechenden Funktionen zu entfernen, und dann zum [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Portal navigieren, um zugehörige [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Dienste zu verwalten, die nicht mehr benötigt werden.  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Komponenten und -Dienste, die im Rahmen von Connected Field Service verfügbar sind, werden in den folgenden Abschnitten ausführlich dargestellt.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Service Bus-Warteschlange](https://azure.microsoft.com/documentation/articles/service-bus-dotnet-get-started-with-queues/)  
  
 Stellt eine Warteschlange für eingehende und ausgehende Nachrichten (Befehle) bereit, die zwischen [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] und [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] ausgetauscht werden. Wenn eine IoT-Warnung an [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] oder ein Befehl von [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] an IoT Hub gesendet wird, wird dieses Element hier in eine Warteschlange gestellt.  
  
 [Logik-Apps](https://azure.microsoft.com/services/logic-apps/)  
  
 Stellt einen Orchestrierungsdienst dar, der einen [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]-Connector und einen Warteschlangen-Connector verwendet. [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]-Connectors werden zum Erstellen von spezifischen [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]-Entitäten verwendet, und Warteschlangenconnectors werden zum Abfragen der Warteschlange verwendet.  
  
 [Stream Analytics](https://azure.microsoft.com/services/stream-analytics/)  
  
 Bietet ein vollständig verwaltetes Echtzeit-Ereignisverarbeitungsmodul, das dabei hilft, aus Daten tiefe Einblicke zu gewinnen. Mit Stream Analytics ist es einfach, Analyseberechnungen in Echtzeit für Datenstreams aus Geräten, Sensoren, Websites, sozialen Medien, Anwendungen, Infrastruktursystemen und mehr einzurichten. Der Dienst funktioniert als Trichter zum Senden ausgewählter IoT-Warnungen an [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)].  
  
 [IoT Hub](https://azure.microsoft.com/services/iot-hub/)  
  
 Connected Field Services nutzt IoT Hub zum Verwalten des Status registrierter Geräte und Objekte. Darüber hinaus sendet IoT Hub Befehle und Benachrichtigungen an verbundene Geräte – und verfolgt den Nachrichtenempfang durch Bestätigungsbelege nach. Gerätenachrichten werden auf permanente Weise gesendet, um Geräte zu berücksichtigen, die mit Unterbrechungen verbunden sind.  
  
 **Simulator**  
  
 Dies ist eine Test-Web-App zum Emulieren des Geräts, das Befehle an IoT Hub sendet oder von dort empfängt.  
  
 [Azure SQL-Datenbank](https://azure.microsoft.com/services/sql-database/)  
  
 Connected Field Service verwendet SQL [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], um Gerätetaktnachrichten für die spätere Verwendung durch Power BI zu speichern, sodass der Status der Geräte in [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] angezeigt wird.  
  
 [Azure Blob Storage](https://azure.microsoft.com/services/storage/)  
  
 Von Stream Analytics verwendete Abfragen werden in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage gespeichert.