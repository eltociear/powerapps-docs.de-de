---
ms.openlocfilehash: dff813dcdf6d025ba47e29699e2047f79cf85600
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2019
ms.locfileid: "67225484"
---
Durch Aktivieren der Relevanzsuche werden Daten in beteiligten Entitäten und Attributen in Ihrer [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)]-Instanz mit einem [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Search-Index synchronisiert und gespeichert.  
  
 Die Relevanzsuche ist standardmäßig nicht aktiviert. Der Systemadministrator muss die Funktionalität in einer [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)]-Instanz aktivieren. Nach der Aktivierung der Relevanzsuche haben Systemadministratoren und -anpasser vollständige Kontrolle über die Daten, die mit dem [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Search-Index synchronisiert werden.  
  
 Systemanpasser können mit dem Dialogfeld **Relevanzsuche konfigurieren** in **Anpassungstools** bestimmte Entitäten für die Suche aktivieren und dann Ansichten der Schnellsuche für aktivierte Entitäten konfigurieren, um die durchsuchbaren Attribute auszuwählen. Datenänderungen werden über eine sichere Verbindung kontinuierlich zwischen [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] und [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Search synchronisiert.  Konfigurationsdaten werden verschlüsselt, und die erforderlichen Geheimnisse werden in [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)] gespeichert.  
  
 Die im Rahmen der Relevanzsuche verfügbaren Azure-Komponenten und -Dienste werden in den folgenden Abschnitten ausführlich dargestellt.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc_privacy_note_azure_trust_center.md)]  
  
 [Azure Search-Dienste](https://azure.microsoft.com/services/search/)  
  
 Ein [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Search-Index wird verwendet, um qualitativ hochwertige Suchergebnisse mit schnellen Antwortzeiten bereitzustellen.  [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Search erweitert [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] um leistungsstarke und anspruchsvolle Suchfunktionen der nächsten Generation.  Dies ist ein dedizierter Suchdienst außerhalb von [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)], der von [!INCLUDE[pn_Windows_Azure](pn-windows-azure.md)] bereitgestellt wird. Alle neuen [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Search-Indizes werden im Ruhezustand verschlüsselt.  Wenn Sie sich vor dem 24. Januar 2018 angemeldet haben, müssen Sie Ihre Daten neu indizieren, indem Sie sich von der Relevanzsuche abmelden, eine Stunde warten und sich wieder anmelden.  
  
 [Azure SQL-Datenbank](https://azure.microsoft.com/services/sql-database/)  
  
 Die Relevanzsuche verwendet die [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)], um Folgendes zu speichern:  
  
-   Konfigurationsdaten, die im Zusammenhang mit der Organisation und dem zugehörigen Index stehen  
  
-   Metadaten, die im Zusammenhang mit dem Suchdienst und den Indizes stehen  
  
-   Zeiger auf Systemmetadaten und Daten beim Synchronisieren von Änderungen  
  
-   Autorisierungsdaten zum Aktivieren erweiterter Sicherheit auf Zeilenebene  
  
[Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/)  
  
Die Komponente [!INCLUDE[pn_azure_event_hubs](pn-azure-event-hubs.md)] wird für den Nachrichtenaustausch zwischen [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] und [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] verwendet. Zudem werden damit Arbeitselemente beibehalten, die durch den Synchronisierungsprozess verwaltet werden. Jede Nachricht speichert Informationen, z.B. die Organisations-ID und den Entitätsnamen, die verwendet werden, um die Daten zu synchronisieren.  
  
[Azure Service Fabric-Cluster](https://azure.microsoft.com/services/service-fabric/)  
  
Die Verarbeitung und Indizierung von Daten erfolgt in Microservices, die auf virtuellen Computern bereitgestellt werden, die über die Service Fabric-Runtime verwaltet werden. Die Such-APIs und der Datensynchronisierungsvorgang werden auch im Service Fabric-Cluster gehostet.  
  
Service Fabric wurde aus jahrelanger Erfahrung bei Microsoft entwickelt, die Unternehmens wichtige Clouddienste bereitstellt, und ist jetzt seit mehr als fünf Jahren in der Produktion. Es handelt sich um das Technologiefundament, auf dem wir unsere [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Kerninfrastruktur sowie u.a. die folgenden Dienste ausführen: [!INCLUDE[pn_skype_for_business](pn-skype-for-business.md)], [!INCLUDE[pn_intune](pn-intune.md)], [!INCLUDE[pn_azure_event_hubs](pn-azure-event-hubs.md)], [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Data Factory, [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] DocumentDB, [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] und [!INCLUDE[pn_cortana](pn-cortana.md)]. Diese Infrastruktur lässt sich auf über 500 Millionen Auswertungen pro Sekunde skalieren.  
  
[Azure Virtual Machine Scale Sets](https://azure.microsoft.com/services/virtual-machine-scale-sets/)  
  
[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Virtual Machine Scale Sets sind elastisch und wurden zur Unterstützung von Workloads mit extremer horizontaler Skalierung konzipiert. Die [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)]-Cluster werden in VM-Skalierungsgruppen ausgeführt. Die Microservices für die Verarbeitung und Indizierung von Daten werden in den Skalierungsgruppen gehostet und von der Service Fabric-Runtime verwaltet.  
  
[Azure Key Vault](https://azure.microsoft.com/services/key-vault/)  
  
[!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)] dient zur sicheren Verwaltung von Zertifikaten, Schlüsseln und anderen Geheimnissen, die im Suchprozess verwendet werden.  
  
[Azure Storage (Blob Storage)](https://azure.microsoft.com/services/storage/blobs/?b=16.38)  
  
Änderungen an Kundendaten werden bis zu 2 Tage in [!INCLUDE[pn_azure_blob_storage](pn_azure_blob_storage.md)] gespeichert.  Diese Blobs werden mit den neuesten Features im [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage SDK verschlüsselt, das Unterstützung für symmetrische und asymmetrische Verschlüsselung und Integration in [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)] bietet. Mit [!INCLUDE[pn_crm_8_2_0_online_subsequent](pn-crm-8-2-0-online-subsequent.md)] werden die Dokumente aus den Notizen und Anlagen in E-Mail-Nachrichten und Terminen auch mit dem Blobspeicher synchronisiert.  
  
[Azure Active Directory-Dienst](https://azure.microsoft.com/services/active-directory/)  
  
[!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] wird für die Authentifizierung zwischen den [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)]- und [!INCLUDE[pn_Windows_Azure](pn-windows-azure.md)]-Diensten verwendet.  
  
[Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/)  
  
Mit dem [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Load Balancer wird eingehender Datenverkehr auf fehlerfreie Dienstinstanzen in Clouddiensten oder virtuellen Computern, die in einer Lastenausgleichsgruppe definiert sind, verteilt. Die Relevanzsuche führt darüber einen Lastenausgleich für die Endpunkte in einer Bereitstellung durch.  
  
[Virtuelle Azure-Netzwerke](https://azure.microsoft.com/documentation/articles/virtual-networks-overview/)  
  
Die virtuellen Computer im Service Fabric-Cluster werden in einem oder mehreren Subnetzen ausgeführt, die durch ein virtuelles [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Netzwerk verbunden sind. Die Sicherheitsrichtlinien, DNS-Einstellungen, Routingtabellen und IP-Adressen werden in diesem virtuellen Netzwerk vollständig kontrolliert. Netzwerksicherheitsgruppen werden genutzt, um Sicherheitsregeln auf dieses virtuelle Netzwerk anzuwenden. Diese Regeln erlauben oder verweigern Netzwerkdatenverkehr für die virtuellen Computer im virtuellen Netzwerk.