---
ms.openlocfilehash: e9b0446c2fb09cad33f5a3ae4bb69103f7d07d70
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2019
ms.locfileid: "67212649"
---
Wenn Sie beim Datenexportdienst ein Datenexportprofil über [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] aktivieren, werden die Daten der Entitäten, die dem Profil hinzugefügt werden, an [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] gesendet. Die erste Synchronisierung umfasst alle Daten, die mit den dem Exportprofil hinzugefügten Entitäten verknüpft sind, aber danach umfasst die Synchronisierung nur neue Änderungen, die kontinuierlich an den Datenexportdienst gesendet werden. An den Datenexportdienst gesendete Daten werden vorübergehend in [!INCLUDE[pn_azure_service_bus](pn_azure_service_bus.md)]- und [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage gespeichert, in [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)] verarbeitet und schließlich mit der im [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Abonnement angegebenen Zieldatenbank synchronisiert (eingefügt, aktualisiert oder gelöscht). Nachdem die Daten synchronisiert wurden, werden sie aus [!INCLUDE[pn_azure_service_bus](pn_azure_service_bus.md)]- und [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage gelöscht. Bei einem Fehler während der Datensynchronisierung werden wenige Daten, die dem Entitätstyp, der Datensatz-ID und dem Synchronisierungszeitstempel entsprechen, in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage gespeichert, um das Herunterladen einer Liste von Datensätzen, die nicht aktualisiert wurden, zu ermöglichen.  
  
 Ein Administrator kann das Datenexportprofil jederzeit deaktivieren, um die Datensynchronisierung zu beenden. Darüber hinaus kann ein Administrator das Exportprofil löschen, um Protokolle fehlerhafter Datensätze zu entfernen. Zudem kann er die Datenexportdienst-Lösung deinstallieren, um die Nutzung des Datenexportdiensts zu beenden.  
  
 Die Datensynchronisierung erfolgt auf sichere Weise kontinuierlich zwischen [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] und dem Datenexportdienst. Daten werden verschlüsselt, während sie kontinuierlich zwischen [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] und dem Datenexportdienst ausgetauscht werden.  
  
 Die im Rahmen des Datenexportdiensts verfügbaren Azure-Komponenten und -Dienste werden in den folgenden Abschnitten ausführlich dargestellt.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc_privacy_note_azure_trust_center.md)]  
  
 [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)  
  
 Bietet die API und die [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Compute-VMs zum Verarbeiten der von [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] empfangenen Benachrichtigungen über Datensatzsynchronisierungen. Anschließend werden Datensatzdaten in die Zieldatenbank eingefügt, darin aktualisiert oder gelöscht. Microservices, die auf virtuellen Computern bereitgestellt werden, die von der [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)]-Runtime verwaltet werden, verarbeiten alle Computedienste im Zusammenhang mit der Datensynchronisierung.  
  
 [Azure Service Bus](https://azure.microsoft.com/services/service-bus/)  
  
 Bietet den Nachrichtenbus, in den [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] die Nachrichten der Synchronisierungsbenachrichtigungen einfügt, die von Computeknoten in [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)] verarbeitet werden. Jede Nachricht speichert Informationen, z.B. die Organisations-ID und den Datensatz, für die Daten synchronisiert werden sollen. Daten in Azure Service Bus sind im Ruhezustand nicht verschlüsselt, aber nur der Datenexportdienst kann darauf zugreifen.  
  
 [Azure Blob Storage](https://azure.microsoft.com/services/storage/)  
  
 Daten werden in [!INCLUDE[pn_azure_blob_storage](pn_azure_blob_storage.md)] temporär gespeichert, falls die Daten der Benachrichtigung über die Datensatzsynchronisierung zum Speichern in einer Nachricht zu umfangreich sind oder ein vorübergehender Fehler beim Verarbeiten der Synchronisierungsbenachrichtigung auftritt. Diese Blobs werden mit den neuesten Features im [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage SDK verschlüsselt, das Unterstützung für symmetrische und asymmetrische Verschlüsselung und Integration in [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)] bietet.  
  
 [Azure SQL](https://azure.microsoft.com/services/sql-database/)  
  
 [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] speichert die Konfiguration von Datenexportprofilen und Metriken für die Datensynchronisierung.