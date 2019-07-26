---
ms.openlocfilehash: 3fb3961dc88033a44c60c4b6f09124c7c38a11bf
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2019
ms.locfileid: "67212787"
---
Wenn Sie bei der Veröffentlichung einer Umfrage von Dynamics 365 aus die „Stimme des Kunden für Dynamics 365“ aktivieren, wird die Umfragedefinition an Azure gesendet und in Azure Storage gespeichert. Wenn ein Befragter ein Umfrageergebnis übermittelt (durch Öffnen des per E-Mail an ihn gesendeten Umfrageeinladungslinks), werden die Umfrageantworten temporär in Azure Service Bus gespeichert und dann in Dynamics 365 abgerufen sowie gespeichert. Sobald die Antworten in Dynamics 365 gespeichert sind, werden sie aus Azure gelöscht.  
  
 Beachten Sie, dass Dynamics 365-Daten wie Kundenname, Produktname, Fallnummer usw. in eine Umfrage einbezogen werden können (in Umfrageelementen wie Fragen, Antworten, usw.), wenn eine Umfrage für einen Befragten bereitgestellt wird. Beim Generieren eines Umfrageeinladungslinks würden diese Dynamics 365-Daten aus Dynamics 365 gesendet und im Austausch gegen einen Bezeichner, der in diesem Umfrageeinladungslink verwendet wird, in einer Azure SQL-Datenbankinstanz gespeichert. Mit diesem Bezeichner werden die Dynamics 365-Daten nach dem Öffnen der Umfrage über den Umfrageeinladungslink in der Umfrage angezeigt. Die Bezeichner innerhalb des Umfragelinks, der einem Befragten per E-Mail gesendet wird, werden in dem E-Mail-System des Befragten gespeichert.  
  
 Ein Administrator kann das Feature „Stimme des Kunden für Dynamics 365“ aktivieren, indem er es als Lösung in der Dynamics 365-Organisation installiert. Außerdem kann ein Administrator das Feature später deaktivieren, indem er die Lösung in der Dynamics 365-Organisation deinstalliert.  
  
 Die im Rahmen der Funktionalität von „Stimme des Kunden für Dynamics 365“ verfügbaren Azure-Komponenten und -Dienste werden in den folgenden Abschnitten ausführlich dargestellt.  
  
 Hinweis: Weitere Informationen zu zusätzlichen Azure-Dienst angeboten finden Sie im Microsoft Azure Trust Center ([https://azure.microsoft.com/support/trust-center/](https://azure.microsoft.com/support/trust-center/)).  
  
 **Cloud Services** ([https://azure.microsoft.com/services/cloud-services/](https://azure.microsoft.com/services/cloud-services/))  
  
 **Designer Service (Webrolle)**  
  
 Dadurch werden mehrere Webdienste für die Kommunikation zwischen einer Dynamics 365-Organisation und den mehrinstanzenfähigen Azure-Komponenten für „Stimme des Kunden für Dynamics 365“ bereitgestellt.  Beispielsweise werden Umfragen in Azure Blob Storage veröffentlicht und gespeichert.  Umfrageantworten werden aus einer Azure Service Bus-Warteschlange abgerufen und zurückgegeben, damit sie in der Dynamics 365-Organisation beibehalten werden.  Alle Anforderungen werden mithilfe von Azure Active Directory authentifiziert.  
  
 **Survey Runtime (Webrolle)**  
  
 Diese Webanwendung stellt die Umfragen für die Befragten bereit.  Übermittelte Umfrageantworten werden vorübergehend in einer Azure Service Bus-Warteschlange gespeichert, bevor sie von einem asynchronen Dynamics 365-Dienst abgerufen und verarbeitet werden.  
  
 **Response Processor (Workerrolle)**  
  
 Diese Workerrolle ist verantwortlich für die Verarbeitung der Rohdaten der abgeschlossenen Umfragen in gültige Umfrageantworten, die in Dynamics 365 erstellt werden können.  
  
 **Pushprozessor (workerrolle)**   Diese workerrolle ist für die Verarbeitung gültiger Umfrage Antworten und das Aktualisieren als Dynamics 365-Entitäts Datensätze verantwortlich. 
 
 **Azure Key Vault** ([https://azure.microsoft.com/services/key-vault/](https://azure.microsoft.com/services/key-vault/))  
  
 Alle Cloud Services speichern Konfigurationsdaten in Azure Key Vault.  Organisations- und Mandantendaten werden in SQL Azure gespeichert.  
  
 **Azure SQL-Datenbank** ([https://azure.microsoft.com/services/sql-database/](https://azure.microsoft.com/services/sql-database/))  
  
 „Stimme des Kunden für Dynamics 365“ verwendet SQL Azure zum Speichern von:  
  
-   Weitergeleitete Daten  
  
-   Umfragemetadaten  
  
-   Organisationsdaten (Mandantendaten)  
  
 **Azure Blob Storage** ([https://azure.microsoft.com/services/storage/](https://azure.microsoft.com/services/storage/))  
  
 Umfragedefinitionen und teilweise abgeschlossene (gespeicherte) Antworten werden in Azure Blob Storage gespeichert.  
  
 **Azure Content Delivery Network (CDN)** ([https://azure.microsoft.com/services/cdn/](https://azure.microsoft.com/services/cdn/))  
  
 Die „Stimme des Kunden für Dynamics 365“-Lösung stellt mit dem Azure Content Delivery Network der Umfrageruntime statische Inhalte wie Bilder (einschließlich hochgeladener Bilder wie z. B. Kundenlogos), JavaScript und CSS bereit.  
  
 **Azure Active Directory** ([https://azure.microsoft.com/services/active-directory/](https://azure.microsoft.com/services/active-directory/))  
  
 Die „Stimme des Kunden für Dynamics 365“-Lösung verwendet Azure Active Directory Service, um Webdienste zu authentifizieren.  
  
 **Azure Service Bus** ([https://azure.microsoft.com/services/service-bus/](https://azure.microsoft.com/services/service-bus/))  
  
 Nachrichten, die erstellt werden, wenn eine Umfrage angezeigt/übermittelt wird, werden temporär in einer Azure Service Bus-Warteschlange der Organisation (des Mandanten) gespeichert, bis die Azure-Workerrolle die Umfrageantworten in die Dynamics 365-Instanz einer Organisation pusht und sie dauerhaft als Dynamics 365-Entitätsdatensätze speichert.
