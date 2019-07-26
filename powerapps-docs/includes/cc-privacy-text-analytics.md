---
ms.openlocfilehash: 80997689e9d4ebca8eb4809cc3e94dab549482b5
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2019
ms.locfileid: "67224729"
---
Durch Aktivierung des Textanalysefeatures aktivieren Sie abhängige Features in [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)], die die [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Cognitive Services-Textanalyse-API für erweiterte Einblicke nutzen. Diese abhängigen Features sind:  
  
-   Wissensdatenbankvorschläge  
  
-   Anfragethemenanalyse  
  
-   Vorschläge für ähnliche Anfragen  
  
 Ein Administrator kann das Textanalysefeature unter **Einstellungen** > **Verwaltung** > **Systemeinstellungen** >  Registerkarte **Vorschau** in der [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)]-Organisation aktivieren.  
  
 Wenn Sie auf Textanalysen basierende Wissensdatenbankvorschläge in [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] einrichten, werden durch Aktivieren des Textanalysefeatures die Anfrage und die Daten von deren verknüpften Entitäten an die [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Textanalyse-API gesendet, um Schlüsselwörter/Ausdrücke zu extrahieren. Mit der [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Textanalyse-API werden keine Daten gespeichert. Nur konfigurierte Felder in der Wissensartikelkonfiguration werden an die [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Textanalyse-API gesendet, um die Begriffe zu extrahieren. Der Administrator oder Anpasser hat die Option zum Deaktivieren der Wissensartikelkonfiguration, um [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Textanalyse-API-Aufrufe zu beenden. Zudem kann der Anpasser auf Textanalysen basierende Vorschläge unterbinden, indem er in der Konfiguration des Entitätsformulars für Anfragen wieder auf feldbasierte Vorschläge umstellt.  
  
 Wenn Sie die Anfragethemenanalyse in [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] einrichten, werden durch Aktivieren des Textanalysefeatures die Anfrage und die Daten von deren verknüpften Entitäten an die [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Textanalyse-API gesendet, um Themen zu bestimmen. Mit der [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Textanalyse-API werden keine Daten gespeichert. Nur konfigurierte Felder in der Themenmodellkonfiguration werden an die [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Textanalyse-API gesendet, um die Themen zu extrahieren. Der Administrator oder Anpasser hat die Option zum Deaktivieren des Themenmodells, um [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Textanalyse-API-Aufrufe zu beenden.  
  
 Wenn Sie Vorschläge für ähnliche Anfragen in [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] einrichten und die Option für die erweiterte Textanalyse in der Ähnlichkeitsregel aktiviert ist, werden durch Aktivieren des Textanalysefeatures die Anfrage und die Daten von deren verknüpften Entitäten an die [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Textanalyse-API gesendet, um Schlüsselwörter und Ausdrücke zu extrahieren. Nur in der Ähnlichkeitsregel konfigurierte Textfelder werden an die [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Textanalyse-API gesendet. Mit der [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Textanalyse-API werden keine Daten gespeichert. Der Administrator oder Anpasser hat die Option zum Deaktivieren der Ähnlichkeitsregel, um [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Textanalyse-API-Aufrufe zu beenden.  
  
 Die im Rahmen der auf Textanalysen basierenden Features verfügbaren [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Komponenten und -Dienste werden in den folgenden Abschnitten ausführlich dargestellt.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Azure-API-App](https://azure.microsoft.com/services/app-service/api/)  
  
 Die [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-API-App löst die Webaufträge aus, die Daten aus der [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]-Organisation lesen und Daten für Themenanalysen an die Textanalyse-API senden. Die [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-API-App verwendet einen Webauftrag für die eigentliche Datenverarbeitung im Hintergrund zum Schreiben der Datenausgabe in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage. Die Daten werden vorübergehend in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage gespeichert. Nach der Themenbestimmung werden die Daten schließlich aus [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage gelöscht.  
  
 [Azure Scheduler](https://azure.microsoft.com/services/storage/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Scheduler wird verwendet, um einen Webauftrag nach einem Zeitplan auszulösen, um die Themenanalyse durchzuführen. Nur der Zeitplan für die Erstellung eines Themenmodells wird für den Scheduler freigegeben.  
  
 [Azure-Tabelle](https://azure.microsoft.com/services/storage/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Tabelle wird für den Austausch der Modellversion und des Organisationskontexts zwischen der [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-API-App und dem Webauftrag verwendet.  
  
 [Azure Blob Storage](https://azure.microsoft.com/services/storage/)  
  
 Webaufträge speichern Daten vorübergehend in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage und löschen sie, sobald die Logik-App-Pipeline die Ausführung abgeschlossen hat.  
  
 [Azure-Textanalyse-API](https://www.microsoft.com/cognitive-services/en-us/text-analytics-api)  
  
 Die [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Textanalyse-API erhält jedes Mal Daten auf Grundlage der Felder, die in aktiven Feldern für die Suche in Wissensdatenbankartikeln oder der Themenmodellkonfiguration oder der Ähnlichkeitsregelkonfiguration konfiguriert sind. Beispielsweise werden die Entitätsfelder für Anfragen, z.B. Titel und Beschreibung, sowie das Beschreibungsfeld in zugehörigen Hinweisen und Aktivitäten in der Konfiguration des Felds für die Suche in Wissensdatenbankartikeln konfiguriert.  
  
 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]-Relevanzsuche  
  
 Sie können die Relevanzsuche verwenden, wenn sie von einem Administrator aktiviert wurde, um ähnliche Datensätze für Anfragen zu finden. Mit den Feldern für Textübereinstimmungen und genaue Übereinstimmungen, die in der Ähnlichkeitsregel verwendet werden, wird die Relevanzsuche-API aufgerufen. Details der Datenverarbeitung finden Sie in den technischen Inhalten für die [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]-Relevanzsuche.