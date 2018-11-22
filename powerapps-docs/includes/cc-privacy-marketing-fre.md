Wenn Sie [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] aktivieren, bestätigen Sie, dass Daten von [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] an bestimmte [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]-Dienste übertragen werden dürfen, damit bestimmte Marketingprozesse durchgeführt werden können. Diese Dienste werden insgesamt als „[!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)]-Dienste” bezeichnet.

Für Kundenkontaktverläufe muss [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] Kundenkontaktverläufe, E-Mails, Eingabeformulare und Marketingseiten an diese [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)]-Dienste übermitteln, die auf [!INCLUDE[pn_azure_service_fabric](../includes/pn_azure_service_fabric.md)] ausgeführt werden. Marketingseiten werden desweiteren an die eigene Portalinstanz eines Kunden für [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] gesendet.

Um gesendete E-Mails zu personalisieren, muss [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] den Datenfluss zu und von [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] aktivieren. Nachfolgend finden Sie weitere Informationen über den [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]-Dienst. Der Datenfluss nach [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] umfasst die Synchronisierung von Kontakten und Konten mit [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]. [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)]-Dienste verwenden diese Daten, um E-Mail-Inhalt zu personalisieren. Welche Daten eingeschlossen werden, hängt ausschließlich von der E-Mail-Definition ab.

Zum Neuberechnen von Leadbewertungsmodellen und Marketingsegmenten muss [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] Leadbewertungsmodell-Definitionen und Segmentdefinitionen an [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] übermitteln und Profile und Interaktionen in [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] innerhalb dieser Berechnungen benutzen.

Um Einblicke in die E-Mail- und Internetinteraktionen zu geben, die von [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)]-Diensten erfasst werden, fließen die gesammelten Daten von [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)]-Diensten sowohl nach [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] als auch nach [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)].

Wenn außerdem die [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]-Ereignisverwaltungsintegration aktiviert ist, synchronisiert [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] Ereignisse mit [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] (direkt über die Verbindung für [!INCLUDE[pn-crm-online-shortest](../includes/pn-crm-online-shortest.md)]) sowie Ereignisregistrierungen und Eincheckvorgänge (über [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)]-Dienste als Interaktionen).

An folgendem Datenfluss ist [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] beteiligt:
- Entitätsdaten von [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] nach [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] mithilfe der regulären Eingangsverbindung von [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)], um Inhalt für die E-Mail-Personalisierung, Leadbewertung und Segmentierung bereitzustellen (hauptsächlich Kontakte und Firmen, letztlich auch Leads und Veranstaltungen)
- Entitätsdaten von [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] über [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)]-Dienste nach [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)], um Bezeichner für Interaktionen und Informationen bereitzustellen (Kundenkontaktverlauf, Marketing-E-Mails, Marketingseiten)
- Interaktionen von [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)]-Diensten mit [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] (E-Mail-Nachverfolgung, Websitenachverfolgung, Kundenkontaktverlauf, Status)
- Interaktionen von [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] über [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)]-Dienste mit [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] (Veranstaltungsregistrierungen und Eincheckvorgänge)
- [!INCLUDE[pn-insights](../includes/pn-insights.md)] (Interaktionen und KPIs) von [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] über [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)]-Dienste mit [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] (hauptsächlich Kundenkontaktverlauf und E-Mail-Sendestatus sowie Leadbewertungsergebnisse)
- [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]-Apps (Segmentierung und Widgets) von [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] direkt in dedizierte und in Sandkastenumgebungen platzierte UI-Elemente in Formularen von [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]

### <a name="marketing-services"></a>Marketingdienste

[!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] verwendet die folgenden [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]-Dienste:

- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Store
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Analytics
- [!INCLUDE[pn-azure-key-vault](../includes/pn-azure-key-vault.md)]
- [!INCLUDE[pn_azure_service_fabric](../includes/pn_azure_service_fabric.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] DocumentDB
- [!INCLUDE[pn-microsoft-azure-active-directory](../includes/pn-microsoft-azure-active-directory.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Storage

> [!NOTE]
> Weitere Informationen zu zusätzlichen [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]-Dienstangeboten, erhalten Sie im [!INCLUDE[cc_privacy_note_azure_trust_center](../includes/cc_privacy_note_azure_trust_center.md)] (<https://azure.microsoft.com/support/trust-center/>).

### [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]

Durch Nutzung von [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] aktivieren Sie die Übertragung von Kundendaten in [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] zur weiteren Verarbeitung. Für Ihre Nutzung von [!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] für [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] ist möglicherweise die Einhaltung bestimmter Datenschutzgesetze erforderlich. Bitte leiten Sie alle Fragen an den zuständigen Mitarbeiter in Ihrer Organisation weiter.

Gegenwärtig befindet sich [!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] in der öffentlichen Vorschau. Es bietet nicht den selben Umfang an Datenschutz- und Sicherheitszusagen wie [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] oder [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] Customer Engagement. [!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] basiert nativ auf [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]-Diensten, und für jeden relevanten [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]-Dienst gelten die jeweiligen Konformitäts- und Sicherheitsstandards. Weitere Informationen finden Sie im [!INCLUDE[cc-microsoft](../includes/cc-microsoft.md)] Trust Center: [https://azure.microsoft.com/support/trust-center/](https://azure.microsoft.com/support/trust-center/)

[!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] verwendet folgende [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]-Dienste:

- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Store
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Analytics
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] HDInsight (Spark, Phoenix, HBase)
- [!INCLUDE[pn-ms-azure-sql-database](../includes/pn-ms-azure-sql-database.md)]
- [!INCLUDE[pn-azure-key-vault](../includes/pn-azure-key-vault.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] – geschützter Geheimspeicher
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]-Ereignishub
- [!INCLUDE[pn-azure-stream-analytics](../includes/pn-azure-stream-analytics.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Redis Cache
- [!INCLUDE[pn_azure_service_fabric](../includes/pn_azure_service_fabric.md)]
- [!INCLUDE[pn-microsoft-azure-active-directory](../includes/pn-microsoft-azure-active-directory.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]-Überwachung
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]-Metriken
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]-Websites
- [!INCLUDE[pn_azure_service_bus](../includes/pn_azure_service_bus.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Storage
