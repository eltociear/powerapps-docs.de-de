---
ms.openlocfilehash: f331670a2fd6b051c91a7fe2bfa607c54c9ab41a
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2019
ms.locfileid: "67225252"
---
Durch Aktivieren von [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] stimmen Sie dem Datenfluss von [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] zu bestimmten [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]-Diensten zu, um einige der Marketingprozesse auszuführen. Diese Dienste werden zusammen als „[!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)]-Dienste“ bezeichnet.

Für Kundenkontaktverläufe muss [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] Kundenkontaktverlauf, E-Mail-Adresse, Registrierungsformular und Marketingseitendefinitionen an diese [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)]-Dienste senden, die auf [!INCLUDE[pn_azure_service_fabric](../includes/pn_azure_service_fabric.md)] ausgeführt werden. Marketingseiten werden außerdem an die eigene Portalfunktioneninstanz des Kunden für [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] gesendet.

Um gesendete E-Mails zu personalisieren, muss [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] den Datenfluss zu und von [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] aktivieren. Unten finden Sie weitere Informationen zum [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]-Dienst. Der Datenfluss zu [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] schließt die Synchronisierung von Kontakten und Konten mit [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] ein. [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)]-Dienste verwenden diese Daten zum Personalisieren von E-Mail-Inhalt. Welche Daten enthalten sind, hängt ausschließlich von der E-Mail-Definition ab.

Um Modelle zur Bewertung potenzieller Kunden und Marketingsegmente neu zu berechnen, muss [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] Definitionen von Modellen zur Bewertung potenzieller Kunden und Segmentdefinitionen an [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] senden und Profile und Interaktionen in [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] in diesen Berechnungen nutzen.

Um Einblicke in die von [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)]-Diensten erfassten E-Mails und Internetinteraktionen bereitzustellen, fließen die gesammelten Daten von [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)]-Diensten sowohl zu [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] als auch [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)].

Wenn darüber hinaus [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]-Ereignisverwaltungsintegration aktiviert ist, synchronisiert [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] Ereignisse mit [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] (direkt über den Connector für [!INCLUDE[pn-crm-online-shortest](../includes/pn-crm-online-shortest.md)]) sowie Ereignisregistrierungen und Eincheckvorgängen (über [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)]-Dienste, als Interaktionen).

Der [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] einbeziehende Datenfluss verläuft wie folgt:
- Entitätsdaten von [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] zu [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] mit dem regulären Eingangsconnector von [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)], um Inhalte für E-Mail-Personalisierung, Bewertung potenzieller Kunden und Segmentierung (hauptsächlich Kontakte und Konten, schließlich auch potenzielle Kunden und Ereignisse) bereitzustellen
- Entitätsdaten von [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] über [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)]-Dienste zu [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)], um Bezeichner für Interaktionen und Einblicke (Kundenkontaktverlauf, Marketing-E-Mails, Marketingseiten) bereitzustellen
- Interaktionen von [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)]-Diensten zu [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] (E-Mail-Nachverfolgung, Überwachung der Website, Kundenkontaktverlauf)
- Interaktionen von [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] über [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)]-Dienste zu [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] (Ereignisregistrierungen und Eincheckvorgänge)
- [!INCLUDE[pn-insights](../includes/pn-insights.md)] (Interaktionen und KPIs) von [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] über [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)]-Dienste zu [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] (hauptsächlich Fortschritt des Kundenkontaktverlaufs und Sendens von E-Mail sowie Ergebnisse der Bewertung potenzieller Kunden)
- [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]-Apps (Segmentierung und Widgets) von [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] direkt in dedizierte und Sandbox-Benutzeroberflächenelemente in Formularen von [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]

### <a name="marketing-services"></a>Marketingdienste

[!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] verwendet diese [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Dienste:

- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Store
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Analytics
- [!INCLUDE[pn-azure-key-vault](../includes/pn-azure-key-vault.md)]
- [!INCLUDE[pn_azure_service_fabric](../includes/pn_azure_service_fabric.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] DocumentDB
- [!INCLUDE[pn-microsoft-azure-active-directory](../includes/pn-microsoft-azure-active-directory.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Storage

> [!NOTE]
> Weitere Informationen über zusätzliche [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]-Dienstangebote finden Sie im [!INCLUDE[cc_privacy_note_azure_trust_center](../includes/cc_privacy_note_azure_trust_center.md)] (<https://azure.microsoft.com/support/trust-center/>).

### [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]

Mithilfe von [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] aktivieren Sie die Übertragung von Kundendaten in [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] zur weiteren Verarbeitung. Die Verwendung von [!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] für [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] erfordert möglicherweise die Compliance mit bestimmten Datenschutzgesetzen. Bitte richten Sie Fragen an den zuständigen Mitarbeiter in Ihrer Organisation.

Derzeit ist [!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] als Public Preview verfügbar und bietet nicht das gleiche Maß an Datenschutz und Sicherheitsverpflichtungen wie [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] oder [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] Customer Engagement. [!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] baut nativ auf [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]-Diensten auf, und die jeweiligen Compliance- und Sicherheitsstandards gelten für jeden anwendbaren [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]-Dienst. Weitere Informationen finden Sie im [!INCLUDE[cc-microsoft](../includes/cc-microsoft.md)] Trust Center: [https://azure.microsoft.com/support/trust-center/](https://azure.microsoft.com/support/trust-center/)

[!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] verwendet diese [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]-Dienste:

- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Store
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Analytics
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] HDInsight (Spark, Phoenix, HBase)
- [!INCLUDE[pn-ms-azure-sql-database](../includes/pn-ms-azure-sql-database.md)]
- [!INCLUDE[pn-azure-key-vault](../includes/pn-azure-key-vault.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Secret Store
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Event Hub
- [!INCLUDE[pn-azure-stream-analytics](../includes/pn-azure-stream-analytics.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Redis Cache
- [!INCLUDE[pn_azure_service_fabric](../includes/pn_azure_service_fabric.md)]
- [!INCLUDE[pn-microsoft-azure-active-directory](../includes/pn-microsoft-azure-active-directory.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Monitoring
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Metrics
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Websites
- [!INCLUDE[pn_azure_service_bus](../includes/pn_azure_service_bus.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Storage
