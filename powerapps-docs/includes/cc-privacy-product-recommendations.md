---
ms.openlocfilehash: 1cdcb40245aae9a23ecb6d3392e412f8a60b95ba
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2019
ms.locfileid: "67212309"
---
Beim Erstellen eines Empfehlungsmodells von [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] aus werden durch Aktivieren des Features Produktempfehlungen die historischen Transaktionsdaten basierend auf konfigurierten Warenkorbdaten-Entitäten und ihrer Filter an [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] gesendet, in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] verarbeitet, vorübergehend in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Speicher gespeichert und schließlich zum Erstellen des Machine Learning-Modells an die Azure-Empfehlungs-API gesendet. Nach dem Erstellen des Modells mit der Azure-Empfehlungs-API werden die Daten aus dem [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Speicher gelöscht. Beachten Sie, dass nur IDs (Konto-ID, Produkt-ID, Transaktions-ID) an [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] gesendet werden, um das Empfehlungsmodell zu erstellen.

Ein Administrator kann das Feature Produktempfehlungen unter **Einstellungen**&gt;**Verwaltung**&gt;**Systemeinstellungen**&gt; Registerkarte **Vorschau** in der [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)]-Organisation aktivieren. Daten werden nur dann an die Azure-Empfehlungs-API gesendet werden, wenn ein Empfehlungsmodell erstellt wird. Der Systemadministrator hat die Option zum Löschen des vorhandenen Modells, um für die Empfehlungs-API von Azure freigegebene Daten zu löschen. Darüber hinaus kann der Systemadministrator die Verbindung mit der Azure-Empfehlungs-API löschen, um das zukünftige Erstellen von Empfehlungsmodellen zu unterbinden.

[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Komponenten und -Dienste, die mit den Produktempfehlungen in Zusammenhang stehen, werden in den folgenden Abschnitten ausführlich dargestellt.

[!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]

[Azure Logic Apps](https://azure.microsoft.com/services/app-service/logic/)

Hiermit wird die orchestrierte Datenpipeline zum Synchronisieren von Produktkatalog und -transaktionsdaten mit der Empfehlungs-API zum Erstellen der Empfehlungsmodellversion bereitgestellt. Diese Pipeline wird als mehrinstanzenfähiger Dienst mit mehreren API-Apps für die Kommunikation zwischen einer Dynamics 365-Organisation und der Empfehlungs-API ausgeführt. Logik-Apps werden von [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] mit minimalem Kontext ausgelöst, z.B. der Modellversions-ID und der [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]-Organisations-URL. 

[Azure-API-Apps](https://azure.microsoft.com/services/app-service/api/)

Hierbei handelt es sich um die Webanwendungen, die die Webaufträge auslösen, die Daten aus der [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]-Organisation und lesen und Daten an die Empfehlungs-API senden, um das Empfehlungsmodell zu erstellen. Es gibt 3 API-Apps und entsprechende Webaufträge – einen für das Lesen von Produktdaten, einen für das Lesen von Transaktionsdaten und einen zum Erstellen eines Empfehlungsmodells. API-Apps verwenden einen Webauftrag für die eigentliche Datenverarbeitung im Hintergrund zum Schreiben der Datenausgabe in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage. Die Daten werden vorübergehend in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage gespeichert. Sobald das Modell erstellt ist, werden die Daten schließlich aus [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage gelöscht.

[Azure-Tabelle](https://azure.microsoft.com/services/storage/tables/)

[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Tabelle wird für den Austausch der Modellversion und des Organisationskontexts zwischen der API-App und einem Webauftrag verwendet.

[Azure Blob Storage](https://azure.microsoft.com/services/storage/) 

Webaufträge speichern Daten vorübergehend in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage und löschen sie, sobald die Logik-App-Pipeline die Ausführung abgeschlossen hat.

[Azure-Empfehlungs-API](https://www.microsoft.com/cognitive-services/en-us/recommendations-api) Die Azure-Empfehlungs-API wird mindestens mit Produkt-IDs, Transaktions-IDs und Konto-IDs gesendet, um das Empfehlungsmodell zu erstellen. Daten werden mit dem Empfehlungs-API-Dienst gespeichert, bis eine entsprechende Version des Modells vorhanden ist.
