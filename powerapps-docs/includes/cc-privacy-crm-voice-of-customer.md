Durch Aktivierung der Lösung „Stimme des Kunden für Dynamics 365“ wird bei Veröffentlichung einer Umfrage in Dynamics 365 die Umfragedefinition an Azure gesendet und im Azure-Speicher gespeichert. Reicht ein Befragter eine Umfrage ein (indem er den per E-Mail erhaltenen Link zur Umfrage aufruft), werden seine Antworten vorübergehend im Azure Service Bus gespeichert und dann in Dynamics 365 abgerufen und gespeichert. Danach werden die Daten aus Azure gelöscht.  
  
 Beachten Sie, dass Daten aus Dynamics 365 wie Kundenname, Produktname, Anfragenummer usw. bei Erstellung einer Umfrage für einen Befragten in eine Umfrage aufgenommen werden können (innerhalb von Umfrageelementen wie Fragen und Antworten usw.). Wird ein Einladungslink zu einer Umfrage erstellt, werden diese Daten aus Dynamics 365 gesendet und in der Azure SQL-Datenbank im Austausch gegen einen Bezeichner gespeichert, der im Einladungslink enthalten ist. Wird die Umfrage mit dem entsprechenden Einladungslink geöffnet, werden die Daten aus Dynamics 365 mithilfe dieses Bezeichners in der Umfrage angezeigt. Die Bezeichner innerhalb des per E-Mail an einen Befragten gesendeten Links zur Umfrage werden im E-Mail-System des Befragten gespeichert.  
  
 Administratoren können die Funktion „Stimme des Kunden für Dynamics 365“ aktivieren, indem sie sie als Lösung in der Dynamics 365-Organisation installieren. Sie können die Funktion auch später wieder deaktivieren. Dazu muss die Lösung in der Dynamics 365-Organisation deinstalliert werden.  
  
 Komponenten und Services von Azure, die zur Funktion „Stimme des Kunden für Dynamics 365“ gehören, werden in den folgenden Abschnitten ausführlich vorgestellt.  
  
 Hinweis: Weitere Informationen über zusätzliche Azure-Serviceangebote finden Sie im Microsoft Azure Trust Center ([https://azure.microsoft.com/support/trust-center/](https://azure.microsoft.com/support/trust-center/)).  
  
 **Cloud Services** ([https://azure.microsoft.com/services/cloud-services/](https://azure.microsoft.com/services/cloud-services/))  
  
 **Designerservice (Webrolle)**  
  
 Stellt mehrere Webdienste zur Kommunikation zwischen einer Dynamics 365-Organisation und den mehrinstanzenfähigen Azure-Komponenten der Funktion „Stimme des Kunden für Dynamics 365“ bereit.  Beispielsweise werden Umfragen im Azure-Blobspeicher veröffentlicht und gespeichert.  Umfrageantworten werden aus einer Azure Service Bus-Warteschlange abgerufen und in der Dynamics 365-Organisation persistent zurückgegeben.  Alle Anfragen werden anhand von Azure Active Directory authentifiziert.  
  
 **Befragungslaufzeit (Webrolle)**  
  
 Dies ist die Webanwendung, mit der die Teilnehmer die Umfrage erhalten.  Übermittelte Umfrageantworten werden temporär in einer Azure Service Bus-Warteschlange gespeichert, bevor sie von einem asynchronen Dynamics 365-Service abgerufen und verarbeitet werden.  
  
 **Antwortverarbeiter (Workerrolle)**  
  
 Dieser Worker ist für die Verarbeitung der Rohdaten der abgeschlossenen Umfragen und deren Umwandlung in gültige Umfrageantworten verantwortlich, die in Dynamics 365 erstellt werden können.  
  
 **Push-Verarbeiter (Arbeitsrolle)**   Diese Arbeitsrolle dient zur Verarbeitung der gültigen Umfrageantworten sowie zur Aktualisierung als Dynamics 365-Entitätsdatensätze. 
 
 **Azure Key Vault** ([https://azure.microsoft.com/services/key-vault/](https://azure.microsoft.com/services/key-vault/))  
  
 Alle Cloudservices speichern Konfigurationsdaten in Azure Key Vault.  Organisations- und Mandantendaten werden in SQL Azure gespeichert.  
  
 **Azure SQL-Datenbank** ([https://azure.microsoft.com/services/sql-database/](https://azure.microsoft.com/services/sql-database/))  
  
 Mithilfe von SQL Azure wird in der Funktion „Stimme des Kunden für Dynamics 365“ Folgendes gespeichert:  
  
-   Daten in der Warteschlange  
  
-   Umfrage-Metadaten  
  
-   Daten der Organisation (des Mandanten)  
  
 **Azure-Blobspeicher** ([https://azure.microsoft.com/services/storage/](https://azure.microsoft.com/services/storage/))  
  
 Umfragedefinitionen und teilweise abgeschlossene (gespeicherte) Antworten werden im Azure-Blobspeicher gespeichert.  
  
 **Azure Content Delivery Network (CDN)** ([https://azure.microsoft.com/services/cdn/](https://azure.microsoft.com/services/cdn/))  
  
 Um während der Umfragelaufzeit statische Inhalte, darunter Bilder (einschließlich hochgeladener Bilder wie Kundenlogos), JavaScript und CSS einzubinden, nutzt die Lösung „Stimme des Kunden für Dynamics 365“ Azure Content Delivery Network.  
  
 **Azure Active Directory** ([https://azure.microsoft.com/services/active-directory/](https://azure.microsoft.com/services/active-directory/))  
  
 Zur Authentifizierung von Webdiensten nutzt die Lösung „Stimme des Kunden für Dynamics 365“ Azure Active Directory-Service.  
  
 **Azure Service Bus** ([https://azure.microsoft.com/services/service-bus/](https://azure.microsoft.com/services/service-bus/))  
  
 Nachrichten, die erstellt werden, wenn eine Umfrage angezeigt oder abgesendet wird, werden vorübergehend in einer Azure Service Bus-Warteschlange der Organisation (des Mandanten) gespeichert, bis die Azure-Workerrolle die Umfrageantworten per Push in die Dynamics 365-Instanz einer Organisation überträgt und sie als Dynamics 365-Entitätsdatensätze dauerhaft speichert.
