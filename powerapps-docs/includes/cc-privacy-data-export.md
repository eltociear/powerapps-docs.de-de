Wenn Sie den Datenexportservice verwenden und ein Datenexportprofil über [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] aktivieren, werden die Daten der Entitäten, die dem Profil hinzugefügt wurden, an [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] gesendet. Die Erstsynchronisierung umschließt alle Daten, die den Entitäten zugeordnet sind, die zum Exportprofil hinzugefügt wurden. Danach werden bei einer Synchronisierung nur neue Änderungen berücksichtigt, die fortlaufend zum Datenexportservice gesendet werden. An den Datenexportservice gesendete Daten werden vorübergehend in [!INCLUDE[pn_azure_service_bus](pn_azure_service_bus.md)] und [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] gespeichert, in [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)] verarbeitet und zuletzt in der Zieldatenbank synchronisiert (eingefügt, aktualisiert oder gelöscht), die in Ihrem [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Abonnement angegeben ist. Nachdem die Daten synchronisiert wurden, werden sie aus den Speichern [!INCLUDE[pn_azure_service_bus](pn_azure_service_bus.md)] und [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] gelöscht. Falls während der Datensynchronisierung ein Fehler auftritt, werden minimale Daten entsprechend Entitätstyp, Datensatz-ID und Synchronisierungszeitstempel im [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Speicher gespeichert, um so das Herunterladen einer Liste mit den nicht aktualisierten Datensätzen zu ermöglichen.  
  
 Ein Administrator kann das Datenexportprofil jederzeit deaktivieren, um die Datensynchronisierung anzuhalten. Darüber hinaus kann ein Administrator das Exportprofil löschen, um alle fehlerhaften Datensatzprotokolle zu entfernen, und kann die Datenexportservicelösung deinstallieren, damit der Datenexportservice nicht mehr verwendet wird.  
  
 Die sichere Datensynchronisierung findet fortlaufend zwischen [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] und dem Datenexportservice statt. Die Daten werden verschlüsselt, während sie fortlaufend zwischen [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] und dem Datenexportservice ausgetauscht werden.  
  
 Azure-Komponenten und ‑Dienste in Verbindung mit dem Data Export Service werden in den folgenden Abschnitten ausführlich beschrieben.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc_privacy_note_azure_trust_center.md)]  
  
 [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)  
  
 Stellt die API bereit und berechnet virtuelle [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Computer zur Verarbeitung von Benachrichtigungen zur Datensatzsynchronisierung von [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] und zur anschließenden Verarbeitung zum Einfügen, Aktualisieren oder Löschen von Datensatzdaten in der Zieldatenbank. Mikrodienste, die auf virtuellen Computern bereitgestellt werden, die von der [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)]-Laufzeit verwaltet werden, bearbeiten alle Berechnungsdienste in Bezug auf Datensynchronisierung.  
  
 [Azure Service Bus](https://azure.microsoft.com/services/service-bus/)  
  
 Liefert den Nachrichtenbus, in den [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] die Benachrichtigungsmeldungen zur Synchronisierung einfügt, die von den Berechnungsknoten in [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)] verarbeitet werden. In jeder Nachricht werden Informationen wie die Organisations-ID und der Datensatz für die Datensynchronisierung gespeichert. Daten in Azure Service Bus werden im Ruhezustand nicht verschlüsselt, sind aber nur über den Datenexportdienst zugänglich.  
  
 [Azure Blob Storage](https://azure.microsoft.com/services/storage/)  
  
 Daten werden temporär in [!INCLUDE[pn_azure_blob_storage](pn_azure_blob_storage.md)] gespeichert, falls die Daten der Datensatzsynchronisierungsbenachrichtigung zu groß sind, um sie in einer Meldung speichern, oder bei der Verarbeitung der Synchronisierungsbenachrichtigung eine vorübergehende Störung auftritt. Diese Blobs werden mithilfe der neuesten Funktion im [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage SDK verschlüsselt, die die symmetrische und asymmetrische Verschlüsselung und die Integration in [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)] unterstützt.  
  
 [Azure SQL](https://azure.microsoft.com/services/sql-database/)  
  
 Die [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] speichert Datenexportprofilkonfiguration und Datensynchronisierungsmetrik.