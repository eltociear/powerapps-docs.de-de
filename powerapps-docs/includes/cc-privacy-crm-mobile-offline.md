Wenn Sie Dynamics 365 Mobile Offline aktivieren, werden die Onlinedaten von Dynamics 365, je nach den für die Offlineverwendung aktivierten Entitäten, unter Verwendung der Azure Cloud in die SQL Azure-Datenbank heruntergeladen. Wenn ein Benutzer eine Verbindung mit Azure Cloud Services aus einer mobilen App mit Offlinefunktion herstellt, werden Daten aus der SQL Azure-Datenbank in eine lokale Datenbank auf dem mobilen Gerät heruntergeladen. Die Datenübertragung zwischen der SQL Azure-Datenbank in der Azure Cloud und der mobilen Dynamics 365-App mit Offlinefunktion erfolgt über eine sichere SSL-Verbindung. Letztendlich werden die Kundendaten in der SQL Azure-Datenbank und auf dem mobilen Gerät gespeichert.  
  
 Ein Administrator legt mithilfe von Sicherheitsrollen und der Dynamics 365 Mobile-Profilanpassung fest, ob Benutzer einer Organisation mit der Microsoft Dynamics 365 Mobile Offline-Anwendung offline gehen dürfen. Dynamics 365-Administratoren können konfigurieren, welche Entitäten per Offlinesynchronisierung heruntergeladen werden, indem sie im Dialogfeld "Einstellung – Mobile Offline" die Einstellung "Synchronisierungsfilter" verwenden.  
  
 Beachten Sie, dass die Daten, die im Gerät des Benutzers gespeichert werden, vom Kunden kontrolliert werden, nicht von Microsoft. Der Administrator hat die volle Kontrolle über die Daten, die auf der Ebene der Benutzersicherheitsrolle oder der Entität extrahiert werden können. Nachdem die Daten extrahiert wurden, sind sie jedoch nicht mehr durch die Sicherheitsbegrenzung von Dynamics 365 Online geschützt.  
  
 Die Azure-Komponenten und -Services in Verbindung mit Mobile Offline-Funktionen werden unten aufgelistet.  
  
 **Hinweis:** Weitere Informationen über zusätzliche Azure-Serviceangebote finden Sie im [Microsoft Azure Trust Center](https://azure.microsoft.com/en-us/support/trust-center/).  
  
 **Cloud Services (Webrolle)**  
  
 Mobile Offline nutzt zwei Clouddienste, einen für die Bereitstellung und den anderen für die Datensynchronisierung.  
  
 Der Bereitstellungsservice hat eine einzige Webrolle, die Nachrichten von der Service Bus (SB)-Warteschlange zu verschiedenen Ereignissen von Dynamics 365 liest, z. B. zur Bereitstellung oder Stilllegung. Dann werden diese Nachrichten verarbeitet, indem Organisationsdatenbanken erstellt oder gelöscht und wiederkehrende Arbeitselemente (Nachrichten) an die SB-Warteschlange für die Datensynchronisierung übermittelt werden. Dabei werden Konfigurationsdaten entweder aus der CSCFG-Datei oder der Software-API von Dynamics 365 gelesen oder geschrieben.  
  
 Der Datensynchronisierungsservice besitzt zwei Webrollen. Eine synchronisiert mithilfe der Metadaten und Daten einer Dynamics 365-Organisation das Schema und die Daten der Stagingdatenbank. Die zweite Webrolle ist für die Ausführung des Synchronisierungsservers und die Verarbeitung der Synchronisierungsanforderungen des Clients zuständig. Die erste Webrolle verarbeitet Nachrichten von der SB-Warteschlange der Datensynchronisierung für unterschiedliche Organisationen und ruft dann die geänderten Metadaten und Daten aus Dynamics 365 ab, bevor diese in der Stagingdatenbank gespeichert werden. Sie ist zudem für die Konfiguration des Synchronisierungsservers für Organisationen, die dem System hinzugefügt werden bzw. dieses verlassen, und deren Clientmodelle zuständig. Die andere Webrolle führt den Synchronisierungsserver (nicht verwalteter Code) aus, um Administrator- und Synchronisierungsendpunkte zu hosten. Der Administratorendpunkt wird von der ersten Webrolle verwendet, um Konfigurationsdaten zu senden. Der Synchronisierungsendpunkt wird von externen Clients (Dynamics 365 Mobile-Anwendung) für die Datensynchronisierung verwendet. Wie bei der Dienstbereitstellung lesen/schreiben diese beiden Rollen Konfigurationsdaten enweder aus der CSCFG-Datei oder aus der Dynamics 365 SW API.  
  
 **Warteschlange**  
  
 In Mobile Offline dienen Azure-Warteschlangen zum Nachrichtenaustausch zwischen Dynamics 365 und Azure. Damit werden Arbeitsobjekte gepflegt, die von den Cloudservices verarbeitet werden. In jeder Nachricht werden Informationen wie die Organisations-ID, der Entitätsname für die Datensynchronisierung und die Verbindungszeichenfolge für den OData-Endpunkt der Organisation gespeichert.  
  
 **SQL-Datenbank**  
  
 Mobile Offline verwendet den Azure SQL-Speicher zum Speichern der folgenden Daten:  
  
-   Replizierte Daten von Dynamics 365-Organisationen und zur Bedienung von Clientsynchronisierungsanforderungen.  
  
-   Konfigurationsdaten wie Organisationsdatenbank-Verbindungszeichenfolgen.  
  
 **Speicher**  
  
 Mobile Offline verwendet Azure-BLOB-Speicher zum Speichern von Protokollen und Ablaufverfolgungen, die vom Cloud Service generiert werden.  
  
 **Active Directory Service**  
  
 Mobile Offline verwendet den Azure Active Directory Service zur Authentifizierung bei anderen Diensten wie Dynamics 365, Software-APIs bzw. Azure-Verwaltungs-APIs.  
  
 **Azure DNS**  
  
 Mobile Offline verwendet Azure DNS, um Clientanforderungen basierend auf dem Namen der Organisation zu den richtigen Cloud Service-Endpunkten umzuleiten.  
  
 **Azure Virtual Network**  
  
 Ein Azure Virtual Network (VNet) ist eine Darstellung Ihres eigenen Netzwerks in der Cloud. Das Produktteam von Dynamics 365 kann Ihre Azure-Netzwerkeinstellungen steuern und DHCP-Adressblöcke, DNS-Einstellungen, Sicherheitsrichtlinien und die Weiterleitung festlegen.  
  
 **Azure Load Balancer**  
  
 Der Azure Load Balancer bietet hohe Verfügbarkeit und Netzwerkleistung für Ihre Anwendungen. Es handelt sich um einen Layer-4-Lastenausgleich (TCP, UDP), der eingehenden Datenverkehr unter fehlerfreien Serviceinstanzen in den Clouddiensten oder virtuellen Computern verteilt, die in einem Lastenausgleichssatz definiert sind. Die Funktion dient zum Lastenausgleich bei den Endpunkten einer Bereitstellung.