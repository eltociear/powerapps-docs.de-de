Wenn Sie die Produktempfehlungen-Funktion aktivieren und ein Empfehlungsmodell über [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] erstellen, werden die historischen Transaktionsdaten auf Grundlage der konfigurierten Warenkorbdatenentitäten ihr ihrer Filter an [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] gesendet, in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] verarbeitet, vorübergehend im [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Speicher gespeichert und zuletzt an die Azure Recommendations API gesendet, um das Machine Learning-Modell zu erstellen. Nachdem das Modell mit der Azure Recommendations API erstellt wurde, werden die Daten aus dem [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Speicher gelöscht. Beachten Sie, dass nur IDs (Firmen-ID, Produkt-ID, Transaktions-ID) zu [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] gesendet werden, um das Empfehlungsmodell zu erstellen.

Ein Administrator kann die Produktempfehlungen-Funktion unter **Einstellungen** &gt; **Verwaltung** &gt; **Systemeinstellungen** &gt; Registerkarte **Vorschau** in der [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)]-Organisation aktivieren. Daten werden nur zur Azure Recommendations API gesendet, wenn ein Empfehlungsmodell erstellt wird. Der Systemadministrator kann das bestehende Modell löschen, um Daten zu löschen, die für die Azure Recommendations API freigegeben wurden. Darüber hinaus kann der Systemadministrator die Verbindung zur Azure Recommendations API löschen, damit in Zukunft keine Empfehlungsmodelle erstellt werden können.

Die im Rahmen der Produktempfehlungen-Funktion verfügbaren [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Komponenten und ‑Services sind in den folgenden Abschnitten ausführlich dargestellt.

[!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]

[Azure Logik-Apps](https://azure.microsoft.com/services/app-service/logic/)

Liefert die orchestrierte Datenpipeline zur Synchronisierung von Produktkatalog und Transaktionsdaten mit der Recommendations API zur Erstellung der Empfehlungsmodellversion. Diese Pipeline wird als mehrinstanzenfähiger Service mit mehreren API-Apps zur Kommunikation zwischen einer Dynamics 365-Organisation und der Recommendations API ausgeführt. Logic Apps werden von [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] mit minimalem Kontext ausgelöst, z. B. Modellversion-ID und [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]-Organisations-URL. 

[Azure API-Apps](https://azure.microsoft.com/services/app-service/api/)

Dies sind die Webanwendungen, die Webaufträge starten, die Daten der [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]-Organisation lesen und Daten zu Recommendations API senden, um das Empfehlungsmodell zu erstellen. Es gibt drei API-Apps und entsprechende Webaufträge – einen zum Lesen von Produktdaten, einen zum Lesen von Transaktionsdaten und einen zum Erstellen eines Empfehlungsmodells. API-Apps verwenden einen Webauftrag, um die tatsächliche Datenverarbeitung im Hintergrund auszuführen und die Datenausgabe in den [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-BLOB-Speicher zu schreiben. Die Daten werden vorübergehend im [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-BLOB-Speicher gespeichert. Nachdem das Modell erstellt wurde, werden die Daten aus dem [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Speicher gelöscht.

[Azure-Tabelle](https://azure.microsoft.com/services/storage/tables/)

Die [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Tabelle wird für die Übermittlung von Modellversion und Organisationskontext zwischen der API-App und einem Webauftrag verwendet.

[Azure Blob-Speicher](https://azure.microsoft.com/services/storage/) 

Daten werden von Webaufträgen vorübergehend im [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-BLOB-Speicher gespeichert und gelöscht, nachdem die Logic App-Pipeline das Ausführen abgeschlossen hat.

[Azure Recommendations API](https://www.microsoft.com/cognitive-services/en-us/recommendations-api) Die Azure Recommendations API wird mit minimalen Daten der Produkt-IDs, Transaktions-IDs und Firmen-IDs gesendet, um das Empfehlungsmodell zu erstellen. Daten werden mit dem Recommendations API-Service gespeichert, bis eine entsprechende Modellversion existiert.
