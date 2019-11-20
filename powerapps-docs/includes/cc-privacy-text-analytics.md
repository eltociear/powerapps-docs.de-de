Durch Aktivierung der Textanalyse-Funktion aktivieren Sie auch abhängige Funktonen in [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)], die die [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Cognitive Services Textanalyse-API verwenden, um erweiterte Erkenntnisse zu bieten. Dabei handelt es sich um die folgenden abhängigen Funktionen:  
  
-   Wissensvorschläge  
  
-   Anfragethemenanalyse  
  
-   Vorschläge für ähnliche Anfragen  
  
 Ein Administrator kann die Textanalyse-Funktion unter **Einstellungen** > **Verwaltung** > **Systemeinstellungen** > **Registerkarte Vorschau** in der [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)]-Organisation aktivieren.  
  
 Wenn Sie die Textanalyse-Funktion aktivieren und einen textanalysebasierten Wissensvorschlag in [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] erstellen, werden die Anfrage und die zugehörigen Daten der Entitäten zum Extrahieren von Schlüsselworten/Phrasen an die [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Textanalyse-API übertragen. Mit der [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Textanalyse-API werden keine Daten gespeichert. Nur konfigurierte Felder in der Wissensartikel-Konfiguration werden zum Extrahieren von Bedingungen an die [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Textanalyse-API gesendet. Administrator oder Systemanpasser können die Wissensartikel-Konfiguration deaktivieren, damit API-Aufrufe an die [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Textanalyse-API verhindert werden. Darüber hinaus kann der Systemanpasser die Verwendung textanalysebasierter Vorschläge deaktivieren, indem er in der Anfrageentitätsformular-Konfiguration zurück zu feldbasierten Vorschlägen wechselt.  
  
 Wenn Sie die Textanalyse-Funktion aktivieren und eine Anfragethemenanalyse in [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] erstellen, werden die Anfrage und die zugehörigen Daten der Entitäten zur Themenbestimmung an die [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Textanalyse-API übertragen. Mit der [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Textanalyse-API werden keine Daten gespeichert. Nur konfigurierte Felder in der Themenmodell-Konfiguration werden zur Extrahierung von Themen an die [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Textanalyse-API gesendet. Administrator oder Systemanpasser können das Themenmodell deaktivieren, damit API-Aufrufe an die [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Textanalyse-API verhindert werden.  
  
 Wenn Sie die Textanalyse-Funktion aktivieren, die Option „erweiterte Textanalyse” in der Ähnlichkeitsregel aktiviert haben und Vorschläge für ähnliche Anfragen in [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] erstellen, werden die Anfrage und die zugehörigen Daten der Entitäten zum Extrahieren von Schlüsselworten/Wortgruppen an die [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Textanalyse-API übertragen. Nur in der Ähnlichkeitsregel konfigurierte Textfelder werden an die [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Textanalyse-API gesendet. Mit der [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Textanalyse-API werden keine Daten gespeichert. Administrator oder Systemanpasser können die Ähnlichkeitsregel deaktivieren, damit API-Aufrufe an die [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Textanalyse-API verhindert werden.  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Komponenten und ‑Dienste in Verbindung mit textanalysebasierten Funktionen werden in den folgenden Abschnitten ausführlich dargestellt.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Azure API-App](https://azure.microsoft.com/services/app-service/api/)  
  
 Die [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] API-App löst die Webaufträge aus, die Daten aus der [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]-Organisation lesen und Daten zur Themenanalyse an die Textanalyse-API senden. Die [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] API-App verwendet einen Webauftrag, um die tatsächliche Datenverarbeitung im Hintergrund auszuführen und die Datenausgabe in den [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-BLOB-Speicher zu schreiben. Die Daten werden vorübergehend im [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-BLOB-Speicher gespeichert. Nachdem die Themenbestimmungen abgeschlossen ist, werden die Daten aus dem [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Speicher gelöscht.  
  
 [Azure Planer](https://azure.microsoft.com/services/storage/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Der Planer wird zum Auslösen eines Webauftrags nach einem Zeitplan verwendet, um eine Themenanalyse auszuführen. Nur der Erstellungszeitplan für das Themenmodell wird für den Planer freigegeben.  
  
 [Azure-Tabelle](https://azure.microsoft.com/services/storage/)  
  
 Die [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Tabelle wird für die Übermittlung von Modellversion und Organisationskontext zwischen der [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] API-App und einem Webauftrag verwendet.  
  
 [Azure Blob-Speicher](https://azure.microsoft.com/services/storage/)  
  
 Webaufträge speichern Daten vorübergehend im [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob-Speicher und löschen sie, nachdem die Logik-App-Pipeline das Ausführen abgeschlossen hat.  
  
 [Azure Textanalyse-API](https://www.microsoft.com/cognitive-services/text-analytics-api)  
  
 An das [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Textanalyse-API werden Daten auf Basis von Feldern gesendet, die in aktiven Wissensdatenbanksuche-Feldern oder der Themenmodell- oder der Ähnlichkeitsregel-Konfiguration konfiguriert werden. Beispielsweise werden Anfrageentitätsfelder (z. B. Titel und Beschreibung) und das Beschreibungsfeld in verknüpften Notizen und Aktivitäten in der Feldkonfiguration für die Suche in Wissensdatenbankartikeln konfiguriert.  
  
 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] Relevanzsuche  
  
 Wenn die Relevanzsuche von einem Administrator aktiviert wurde, können Sie damit ähnliche Datensätze von Anfragen suchen. Die in der Ähnlichkeitsregel verwendeten Felder für Textübereinstimmungen und exakte Übereinstimmungen werden zum Aufrufen der Relevanzsuche-API verwendet. Informationen zur Datenverarbeitung finden Sie in den technischen Angaben für die [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] Relevanzsuche.