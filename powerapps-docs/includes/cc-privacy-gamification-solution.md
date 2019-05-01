---
ms.openlocfilehash: 747ea34b784b852261debe91f587d64ee3277804
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61574942"
---
Durch die Installation und Aktivierung der [!INCLUDE[pn_gamification](pn-gamification.md)]-Lösung werden die Konto-IDs des aktivierenden Benutzers (wie Vorname, Nachname und E-Mail-Adresse) in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] gespeichert, um eine Autorisierung mit dem [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)]-Dienst zu ermöglichen, der in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] gehostet wird. Dies gilt für alle Benutzer, die im [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)]-Dienst von ihrem Administrator aktiviert werden. Die [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)]-Lösung sendet von einem Administrator konfigurierte Daten zu Key Performance Indicators (KPIs) an den [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Service. Die Daten werden dann im strukturierten [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Speicher sowie im Blobspeicher gespeichert.  Avatar, benutzerdefinierte Auszeichnungen und Unternehmenslogo der einzelnen Benutzer werden zwar in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] gespeichert, aber nicht an [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] zurückgegeben.  
  
Beachten Sie, dass Administratoren und autorisierte Benutzer Daten aus [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] wie Telefonanrufe, Verkaufschancen und gebuchte Umsätze heranziehen können, um KPIs für Spiele zu konfigurieren. Der [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)]-Dienst tätigt keine Aufrufe an [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] und reagiert nur auf Daten, wie beispielsweise Spiele, in denen KPIs verwendet werden, die an [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] zurückgehen.  
  
Administratoren können den [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)]-TV-Stream auch veröffentlichen. Spielmanager, die [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)]-TV-Streams einrichten und öffentliches Streaming zulassen, lassen damit auch zu, dass jeder Benutzer, der den Stream-Link hat, den TV-Stream im Internet verfolgen kann.  
  
Administratoren können die [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)]-Funktion auch wieder entfernen, indem sie die Lösung in der [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)]-Organisation deinstallieren.  
  
Die zu [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] gehörigen Komponenten und Services von [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] werden in den folgenden Abschnitten ausführlich vorgestellt.  
  
[!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
[Cloud-Dienste](https://azure.microsoft.com/services/cloud-services/)  
  
 **Designerdienst (Webrolle)**  
  
Stellt mehrere Webdienste zur Kommunikation zwischen einer [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)]-Organisation und den mehrmandantenfähigen [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Komponenten bereit. Beispielsweise werden Gamification-Details in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] SQL-Speicher gespeichert.  Spielberechnungen nutzen die [!INCLUDE[pn_azure_service_bus](pn-azure-service-bus.md)]-Warteschlange, werden zur Bewertung zurückgegeben und im Dienst angezeigt.  Von Kunden und Benutzern hochgeladener Bilder werden in [!INCLUDE[pn_azure_blob_storage](pn-azure-blob-storage.md)] gespeichert. Alle Anfragen werden anhand von [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] authentifiziert.  
  
[Azure Key Vault](https://azure.microsoft.com/services/key-vault/)  
  
Alle Dienste speichern Konfigurationsdaten in [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)].  
  
[Azure SQL-Datenbank](https://azure.microsoft.com/services/sql-database/)  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] verwendet SQL [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], um Folgendes zu speichern:  
  
- KPI-Daten  
  
- Spielberechnungen  
  
- Organisationsdaten (Mandantendaten)  
  
[Azure Blob Storage](https://azure.microsoft.com/services/storage/)  
  
Avatare, Unternehmenslogos und andere vom Kunden hochgeladene Bilder werden in [!INCLUDE[pn_azure_blob_storage](pn-azure-blob-storage.md)] gespeichert.  
  
[Azure Content Delivery Network (CDN)](https://azure.microsoft.com/services/cdn/)  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] nutzt [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Content Delivery Network, um statische Inhalte zur Laufzeit, darunter Bilder (einschließlich hochgeladener Bilder wie Kundenlogos), [!INCLUDE[pn_JavaScript](pn-javascript.md)] sowie CSS, bereitzustellen.  
  
[Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] nutzt [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)], um Benutzer zu authentifizieren und die Eignung zur Plattformnutzung zu ermitteln.