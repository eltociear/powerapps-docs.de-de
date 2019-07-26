---
ms.openlocfilehash: 787ff9592604f9a9bce1929e4d429a39da5ec48a
ms.sourcegitcommit: 982cab99d84663656a8f73d48c6fae03e7517321
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/28/2019
ms.locfileid: "67456821"
---
Wenn Sie die Offlinefunktion der mobilen Dynamics 365-App aktivieren, werden die Onlinedaten von Dynamics 365 basierend auf den für die Offlineverfügbarkeit aktivierten Entitäten über die Azure-Cloud in die Azure SQL -Datenbank heruntergeladen. Wenn ein Benutzer eine Verbindung mit Azure Cloud Services über eine mobile App mit der Offlinefunktion herstellt, werden Daten aus der Azure SQL-Datenbank in eine lokale Datenbank auf dem mobilen Gerät heruntergeladen. Die Datenübertragung zwischen der Azure SQL-Datenbank in der Azure-Cloud und der mobilen Dynamics 365-App mit Offlinefunktion erfolgt über eine sichere SSL-Verbindung. Schließlich werden die Kundendaten in der Azure SQL-Datenbank und auf dem mobilen Gerät gespeichert.  
  
 Ein Administrator legt mithilfe von Sicherheitsrollen und der Profilanpassung für die mobile Microsoft Dynamics 365-App fest, ob die Benutzer einer Organisation die Offlinefunktion der mobilen Microsoft Dynamics 365-App verwenden dürfen. Dynamics 365-Administratoren können konfigurieren, welche Entitäten über die Offlinesynchronisierung heruntergeladen werden, indem sie im Dialogfeld „Einstellung – Mobile Offline“ die Einstellung „Synchronisierungsfilter“ verwenden.  
  
 Beachten Sie, dass die Daten, die auf dem Gerät des Benutzers gespeichert werden, vom Kunden kontrolliert werden, nicht von Microsoft. Der Administrator hat die volle Kontrolle über die Daten, die auf der Ebene der Benutzersicherheitsrolle oder der Entität extrahiert werden können. Nachdem die Daten extrahiert wurden, werden sie nicht mehr durch die Sicherheitsbegrenzung von Dynamics 365 Online geschützt.  
  
 Die Azure-Komponenten und -Dienste in Verbindung mit der mobilen Offlinefunktionalität werden unten aufgelistet.  
  
 **Hinweis**: Weitere Informationen über zusätzliche Azure-Dienstangebote finden Sie im [Microsoft Azure Trust Center](https://azure.microsoft.com/support/trust-center/).  
  
 **Cloud Services (Webrolle)**  
  
 Die mobile Offlinefunktion nutzt zwei Clouddienste, einen für die Bereitstellung und den anderen für die Datensynchronisierung.  
  
 Der Bereitstellungsdienst hat eine einzige Webrolle, die Nachrichten aus der Service Bus-Warteschlange zu verschiedenen Dynamics 365-Ereignissen liest, z.B. zur Bereitstellung oder Aufhebung der Bereitstellung. Dann werden diese Nachrichten verarbeitet, indem Organisationsdatenbanken erstellt oder gelöscht und wiederkehrende Arbeitselemente (Nachrichten) an die Service Bus-Warteschlange für die Datensynchronisierung übermittelt werden. Dabei werden Konfigurationsdaten entweder aus der CSCFG-Datei oder der Software-API von Dynamics 365 gelesen/geschrieben.  
  
 Der Datensynchronisierungsdienst hat zwei Webrollen. Eine synchronisiert das Schema und die Daten der Stagingdatenbank mit den Metadaten und Daten einer Dynamics 365-Organisation. Die zweite Webrolle ist für die Ausführung des Synchronisierungsservers und die Verarbeitung der Synchronisierungsanforderungen des Clients zuständig. Die erste Webrolle verarbeitet Nachrichten aus der Datensynchronisierung der Server Bus-Warteschlange für unterschiedliche Organisationen und ruft dann die geänderten Metadaten und Daten aus Dynamics 365 ab, bevor diese in der Stagingdatenbank gespeichert werden. Sie ist zudem für die Konfiguration des Synchronisierungsservers für Organisationen, die dem System hinzugefügt werden bzw. dieses verlassen, und deren Clientmodelle zuständig. Die andere Webrolle führt den Synchronisierungsserver (nicht verwalteter Code) aus, um Administrator- und Synchronisierungsendpunkte zu hosten. Der Administratorendpunkt wird von der ersten Webrolle verwendet, um Konfigurationsdaten zu senden. Der Synchronisierungsendpunkt wird von externen Clients (mobile Dynamics 365-Anwendung) für die Datensynchronisierung verwendet. Wie der Bereitstellungsdienst auch lesen/schreiben diese beiden Rollen Konfigurationsdaten aus der CSCFG-Datei oder aus der Dynamics 365-Software-API.  
  
 **Warteschlange**  
  
 Die Offlinefunktion der mobilen App verwendet Azure-Warteschlangen für den Nachrichtenaustausch zwischen Dynamics 365 und Azure. Damit werden Arbeitselemente verwaltet, die die Clouddienste verarbeiten. In jeder Nachricht werden Informationen wie die Organisations-ID, der Entitätsname für die Datensynchronisierung und die Verbindungszeichenfolge für den OData-Endpunkt der Organisation gespeichert.  
  
 **SQL-Datenbank**  
  
 Die mobile Offlinefunktion verwendet den SQL-Speicher zum Speichern der folgenden Daten:  
  
-   Replizierte Daten von Dynamics 365-Organisationen und zum Bedienen von Clientsynchronisierungsanforderungen  
  
-   Konfigurationsdaten wie Organisationsdatenbank-Verbindungszeichenfolgen  
  
 **Speicher**  
  
 Die mobile Offlinefunktion verwendet Azure Blob Storage zum Speichern der vom Clouddienst generierten Protokolle und Ablaufverfolgungen.  
  
 **Azure Active Directory**  
  
 Die mobile Offlinefunktion verwendet Azure Active Directory zur Authentifizierung bei anderen Diensten wie Dynamics 365, Software-API oder Azure-Verwaltungs-APIs.  
  
 **Azure DNS**  
  
 Die mobile Offlinefunktion verwendet Azure DNS, um Clientanforderungen basierend auf dem Namen der Organisation zu den richtigen Clouddienst-Endpunkten umzuleiten.  
  
 **Azure Virtual Network**  
  
 Ein virtuelles Azure-Netzwerk (VNET) ist eine Darstellung Ihres eigenen Netzwerks in der Cloud. Das Dynamics 365-Produktteam kann Ihre Azure-Netzwerkeinstellungen steuern und DHCP-Adressblöcke, DNS-Einstellungen, Sicherheitsrichtlinien und Routing definieren.  
  
 **Azure Load Balancer**  
  
 Azure Load Balancer bietet Hochverfügbarkeit und Netzwerkleistung für Ihre Anwendungen. Es handelt sich um einen Layer-4-Lastenausgleich (TCP, UDP), der eingehenden Datenverkehr auf fehlerfreie Dienstinstanzen in Clouddiensten oder auf virtuellen Computern verteilt, die in einem Lastenausgleichssatz definiert sind. Die Funktion dient zum Lastenausgleich bei den Endpunkten einer Bereitstellung.