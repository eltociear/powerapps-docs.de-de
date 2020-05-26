---
title: Zu Data Lake exportieren | MicrosoftDocs
description: Erfahren Sie, wie Sie Entitätsdaten in einen Azure Data Lake exportieren in Power Apps
ms.custom: ''
ms.date: 04/27/2020
ms.reviewer: Mattp123
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- powerapps
author: sabinn-msft
ms.assetid: ''
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 52ab32a0ddf27a2a6be3566305655399918b01e4
ms.sourcegitcommit: 51fa748cde4ea81e918dae1b39f9dca1d6e4e546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2020
ms.locfileid: "3292065"
---
# <a name="export-entity-data-to-azure-data-lake-storage-gen2"></a>Entitätsdaten nach Azure Data Lake Storage Gen2 exportieren

Der Export to Data Lake-Dienst ist eine Pipeline zum kontinuierlichen Export von Daten von Common Data Service bis Azure Data Lake Storage Gen2. Der Export to Data Lake-Dienst wurde für die Analyse großer Unternehmensdaten entwickelt, indem er eine skalierbare Hochverfügbarkeit mit Disaster Recovery-Funktionen bietet. Die Daten werden im Common Data Model-Format gespeichert, das für semantische Konsistenz über Anwendungen und Implementierungen hinweg sorgt. 

![Zu Data Lake exportieren, Übersicht](media/export-data-lake-overview.png "Export to Data Lake Übersicht")

Export to Data Lake bietet diese Funktionen: 

- Verknüpfen oder Entkoppeln der Common Data Service-Umgebung mit Data Lake Storage Gen2 in Ihrem Azure-Abonnement. 
- Kontinuierliche Replikation von Entitäten zu Data Lake Storage Gen2.
- Anfängliches Schreiben, gefolgt von inkrementellen Schreibvorgängen für Daten und Metadaten. 
- Replikation sowohl von Standard- als auch von benutzerdefinierten Entitäten. 
- Replikation von Erstellungs-, Aktualisierungs- und Löschvorgängen (CrUD). 
- Kontinuierliche Snapshot-Updates für umfangreiche Analyseszenarien. 
- Erleichterte Metadatenerkennung und Interoperabilität zwischen Datenproduzenten und -konsumenten wie Power BI, Azure Data Factory, Azure Databricks und Azure Machine Learning.

## <a name="how-data-and-metadata-are-exported"></a>Wie Daten und Metadaten exportiert werden

Der Export to Data Lake-Dienst unterstützt anfängliches und inkrementelles Schreiben für Entitätsdaten und Metadaten. Alle Daten oder Metadatenänderungen in Common Data Service werden ohne weitere Aktion automatisch zum Data Lake übertragen. Es handelt sich hierbei eher um eine Push-Operation als um eine Pull-Operation. Änderungen werden an das Ziel übertragen, ohne dass Sie Aktualisierungsintervalle einrichten müssen. 

Es können sowohl Standard- als auch benutzerdefinierte Entitäten exportiert werden. Beachten sie, dass die Änderungsnachverfolgungsfunktion in Common Data Service verwendet wird, um die Daten effizient zu synchronisieren, indem festgestellt wird, welche Daten geändert wurden, nachdem die Daten ursprünglich extrahiert oder zuletzt synchronisiert wurden. 

Alle Erstellungs-, Aktualisierungs- und Löschvorgänge werden von Common Data Service in den Data Lake exportiert. Wenn ein Benutzer beispielsweise einen Kontoentitätsdatensatz in Common Data Service löscht, wird die Transaktion in den Ziel-Data Lake repliziert.

## <a name="prerequisites"></a>Voraussetzungen

Bevor Sie Daten aus Common Data Service in einen Data Lake exportieren können, müssen Sie ein Azure Storage v2 (general-purpose v2)-Speicherkonto erstellen und konfigurieren. 

Befolgen Sie die Schritte im Artikel  [Azure Storage-Konto erstellen](/azure/storage/blobs/data-lake-storage-quickstart-create-account) und beachten Sie diese Anforderungen: 

- Ihnen muss eine Besitzerrolle im Speicherkonto zugewiesen werden. 
- Stellen Sie Ihren Speichertyp ein als **Speicher v2 (Universell v2)**. 
- Bei dem Speicherkonto muss die Funktion für den **Hierarchischen Namespace** aktiviert sein. 

 Wir empfehlen, die Replikationseinstellung auf Georedundanter Speicher (RA-GRS) mit Leseberechtigung festzulegen. Mehr Informationen: [Georedundanter Speicher mit Lesezugriff](/azure/storage/common/storage-redundancy-grs#read-access-geo-redundant-storage)

>   ![Speicherkonto Eigenschaften](media/storage-account-properties.png "Speicherkonto Eigenschaften")

> [!NOTE]
> - Das Speicherkonto muss im gleichen Azure Active Directory (Azure AD) Mandanten wie Ihr Power Apps Mandanten angelegt werden.  
> - Das Speicherkonto muss in der gleichen Region wie die Power Apps-Umgebung, in der Sie die Funktion verwenden werden, erstellt werden.  
> - Um die Common Data Service-Umgebung mit der Azure Data Lake Storage-Gen2-Umgebung zu verknüpfen, müssen Sie ein Common Data Service-Administrator sein. 
> - Nur Entitäten, die die Änderungsnachverfolgung aktiviert haben, können exportiert werden. 

## <a name="select-and-export-common-data-service-entity-data-to-azure-data-lake-storage-gen2"></a>Wählen und exportieren Sie die Daten der Common Data Service Entität in Azure Data Lake Storage Gen2

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an, erweitern Sie **Daten**, und wählen Sie dann **Entitäten**. 
2. Wählen Sie in der Befehlsleiste **In Data Lake exportieren** und dann auf der Seite **In Data Lake exportieren** wählen Sie **Neuer Link zum Data Lake**. 
3. Wählen Sie jeder der folgenden Einstellungen und dann **Weiter**: 
   - **Abonnement**. Wählen Sie Ihr Azure Abonnement. 
   - **Ressourcengruppe**. Wählen Sie die Ressourcengruppe, die das Speicherkonto Storage v2 (general-purpose v2) enthält.
   - **Speicherkonto**. Wählen Sie das Speicherkonto Storage v2 (general-purpose v2), das für den Export verwendet werden soll. 

    > [!NOTE]
    > Wenn Sie die Common Data Service-Umgebung mit einem Data Lake verknüpfen, gewähren Sie dem Export to Data Lake-Service Zugriff auf Ihr Speicherkonto. Stellen Sie sicher, dass Sie den [Voraussetzungen](#prerequisites) zum Erstellen und Konfigurieren des Azure Data Lake Storage-Kontos gefolgt sind und Ihnen selbst eine Besitzerrolle im Speicherkonto zuweisen. Zusätzlich gewähren Sie dem Power Platform-Dataflows-Service Zugriff auf Ihr Speicherkonto. Weitere Informationen: [Self-Service Datenaufbereitung mit Dataflows](self-service-data-prep-with-dataflows.md).  

4. Wählen Sie die Entitäten aus, die Sie zum Data Lake exportieren möchten und wählen Sie dann **Speichern** aus. Nur Entitäten, die die Änderungsnachverfolgung aktiviert haben, können exportiert werden. Mehr Informationen: [Änderungsverfolgung für eine Entität aktivieren](/dynamics365/customer-engagement/admin/enable-change-tracking-control-data-synchronization)

   > [!div class="mx-imgBorder"] 
   > ![Die zu exportierende Entitäten auswählen](media/export-data-lake-select-entity.png "Die zu exportierende Entitäten auswählen")

Ihre Common Data Service-Umgebung ist mit dem Azure Data Lake Storage-Gen2-Konto verknüpft. Das Dateisystem im Azure-Speicherkonto wird mit einem Ordner für jede für die Replikation im Data Lake ausgewählte Entität erstellt. 

> [!NOTE]
> Die vom Dienst Export to data lake exportierten Daten werden im Ruhezustand in Azure Data Lake Storage Gen2 verschlüsselt. Zusätzlich werden transiente Daten im Blobspeicher auch im Ruhezustand verschlüsselt. Die Verschlüsselung in Azure Data Lake Storage Gen2 hilft Ihnen beim Schutz Ihrer Daten, bei der Implementierung von Sicherheitsrichtlinien des Unternehmens und bei der Erfüllung gesetzlicher Vorschriften. Weitere Informationen: [Azure Datenverschlüsselung im Ruhezustand]( /azure/security/fundamentals/encryption-atrest)

## <a name="manage-entity-data-to-the-data-lake"></a>Entitätsdaten zum Data Lake verwalten

Nachdem Sie den Datenexport zu Azure Data Lake Storage Gen2 in Ihrem Abonnement eingerichtet haben, können Sie den Export von Entitätsdaten in den Data Lake auf eine von zwei Arten verwalten: 

- Im Bereich Power Apps Herstellerportal **zum Data Lake exportieren** wählen Sie **Entitäten verwalten** in der Befehlsleiste, um eine oder mehrere verknüpfte Entitäten hinzuzufügen oder zu entfernen.
- Im Bereich Power Apps Herstellerportal **Entitäten** wählen Sie **…** Klicken Sie neben einer Entität auf den verknüpften Data Lake, in den Sie Entitätsdaten exportieren möchten. 

   ![Wählen Sie eine Entität für den Export aus](media/select-entity-export.png "Wählen Sie eine Entität für den Export aus")

Um die Verknüpfung aller verknüpften Entitäten aufzuheben, wählen Sie auf dem Power Apps Erstellerportal **Export zu Data Lake** Bereich, wählen Sie **Data Lake** verknüpfen.

## <a name="view-your-data-in-azure-data-lake-storage-gen2"></a>Anzeigen Ihrer Daten in Azure Data Lake Storage Gen2

1. Melden Sie sich bei [Azure](https://portal.azure.com) an, wählen Sie das Speicherkonto aus und wählen Sie dann im linken Navigationsbereich **Speicherexplorer**. 
2. Erweitern von **Dateisysteme**, wählen Sie dann commondataservice-*environmentName*-org-*ID*. 

Die Datei model.json bietet zusammen mit ihrem Namen und ihrer Version eine Liste der Entitäten, die in den Data Lake exportiert wurden. Die Datei model.json enthält auch den anfänglichen Synchronisationsstatus und die Zeit der Fertigstellung der Synchronisierung. 

Für jede in den Data Lake exportierte Entität wird ein Ordner mit durch Kommata getrennten Snapshot-Dateien (CSV-Format) angezeigt.
   > [!div class="mx-imgBorder"] 
   > ![Entitätsdaten im Data Lake](media/entity-data-in-lake.png "Entitätsdaten im Data Lake") 

### <a name="continuous-snapshot-updates"></a>Kontinuierliche Snapshot-Updates

Common Data Service Daten können sich kontinuierlich durch das Erstellen, Aktualisieren und Löschen von Transaktionen ändern. Snapshots stellen eine schreibgeschützte Kopie der Daten dar, die in regelmäßigen Abständen, in diesem Fall stündlich, aktualisiert wird. Dies stellt sicher, dass ein Datenanalyse-Konsument zu jedem Zeitpunkt zuverlässig Daten im Lake konsumieren kann.

![Kontinuierliche Snapshot-Updates](media/snapshot-updates.png "Kontinuierliche Snapshot-Updates")

Wenn Entitäten als Teil des anfänglichen Exports hinzugefügt werden, werden die Entitätsdaten in die entity.csv-Dateien unter den entsprechenden Ordnern im Data Lake geschrieben. Dies ist das T1-Intervall, in dem eine schreibgeschützte Snapshot-Datei mit dem Namen *Entität*-T1.csv&mdash;z.B. Account-T1.csv oder Contacts-T1.csv&mdash;erstellt wird. Darüber hinaus wird die model.json-Datei aktualisiert, um auf diese Momentaufnahme-Dateien zu verweisen. Wenn Sie model.json öffnen, können Sie die Details des Snapshots anzeigen. 

Hier ist ein Beispiel für eine in Account.csv partitionierte Datei und einen Snapshot-Ordner im Data Lake.

![Momentaufnahme der Kontenentität](media/export-data-lake-account-snapshots.png "Momentaufnahme der Kontenentität") 

Änderungen in Common Data Service werden kontinuierlich mit Hilfe der Trickle-Feed-Engine in die entsprechenden CSV-Dateien übertragen. Dies ist das T2-Intervall, in dem eine weitere Momentaufnahme erstellt wird. *Entity*-T2.csv &mdash; zum Beispiel, Accounts-T2.csv oder Contacts-T2.csv (vorausgesetzt, es gibt Änderungen für die Entität) &mdash; und model.json werden auf die neuen Snapshot-Dateien aktualisiert. Jede neue Person, die die Snapshot-Daten ab T2 anzeigt, wird zu den neueren Snapshot-Dateien geleitet. Auf diese Weise kann der ursprüngliche Snapshot-Viewer weiterhin an den älteren Snapshot-T1-Dateien arbeiten, während neuere Viewer die neuesten Aktualisierungen lesen können. Dies ist in Szenarien mit länger laufenden Downstream-Prozessen nützlich. 

Hier ist ein Beispiel für die Datei model.json, die immer auf die letzte zeitgestempelte Konto-Snapshot-Datei verweist. 

![Beispiel-Snapshot modell.json-Datei](media/sample-snapshot-json.png "Beispiel für eine Snapshot model.json-Datei") 

## <a name="transporting-an-export-to-data-lake-configuration-across-environments"></a>Transportieren einer Export to Data Lake-Konfiguration über mehrere Umgebungen hinweg

In Power Apps werden Lösungen verwendet, um Anwendungen und Komponenten von einer Umgebung in eine andere zu transportieren oder um einen Satz von Anpassungen auf bestehende Anwendungen anzuwenden. Um die Export to Data Lake-Konfigurationen lösungsorientiert zu gestalten, importieren Sie die Export to Data Lake Core-Lösung in die Umgebung. Dies ermöglicht grundlegende ALM-Fähigkeiten (Application Lifecycle Management) wie Verteilung sowie Sicherung und Wiederherstellung der Export to Data Lake-Konfiguration. 

### <a name="import-the-export-to-data-lake-core-solution"></a>Importieren Sie die Export to Data Lake Core-Lösung

1.  Wählen Sie im Power Apps-Erstellerportal die Umgebung aus, in der Sie die Export to Data Lake-Konfiguration verteilen möchten.
2.  Wählen Sie im linken Navigationsbereich **Lösungen**, wählen Sie **AppSource öffnen**, suchen Sie nach der Lösung mit dem Namen **Export to Data Lake Core** und importieren Sie dann die Lösung.

### <a name="add-an-export-to-data-lake-configuration-to-a-solution"></a>Einer Lösung eine Export to Data Lake-Konfiguration hinzufügen

> [!IMPORTANT]
> Bevor Sie eine Export to Data Lake-Konfiguration hinzufügen können, müssen Sie die zuvor beschriebene Export to Data Lake Core-Lösung installieren. 

1.  Wählen Sie im Power Apps Erstellerportal die Umgebung aus, in der Sie die Export to Data Lake-Konfiguration verteilen möchten, und wählen Sie dann im linken Navigationsbereich **Lösungen**. 
2.  Wählen Sie **Neue Lösung** und geben Sie einen Namen ein, wählen Sie einen Herausgeber aus und geben Sie dann eine Versionsnummer an.  
3.  Öffnen Sie die im vorherigen Schritt erstellte Lösung und wählen Sie **Vorhandenes hinzufügen** > **Andere** > **Export nach Data Lake Config**. 
4.  Wählen Sie die verknüpften Data Lake Konfigurationen aus, die Sie möchten, und wählen Sie dann **hinzufügen** aus. 
5.  Wählen Sie im Bereich **Lösungen** die Lösung aus und wählen Sie dann in der Befehlsleiste **Export**. 
6.  In dem **Bevor Sie exportieren** Bereich auswählen **Veröffentlichen**, um alle Änderungen vor dem Export zu veröffentlichen, und wählen Sie dann **Nächster**. 

### <a name="import-the-solution-that-contains-the-export-to-data-lake-configuration"></a>Importieren Sie die Lösung, die die Konfiguration Export to Data Lake enthält

In der Umgebung, in der Sie Ihre Lösung importieren möchten, importieren Sie im Bereich Power Apps Erstellerportal **Lösungen** die Lösung. 

#### <a name="verify-the-export-to-data-lake-configuration"></a>Überprüfen Sie die Konfiguration Export to Data Lake

Vergewissern Sie sich im Herstellerportal Power Apps in der Umgebung, in der Sie die Konfiguration Export to Data Lake importiert haben, dass Sie Ihren verknüpften Data Lake zusätzlich zu den Entitäten sehen können, die Sie aus Ihrer anderen Umgebung transportiert haben.

> [!div class="mx-imgBorder"] 
> ![Importierte Export to Data Lake-Entitäten](media/imported-export-entities.png "Importierter Export in Data Lake-Entitäten") 

### <a name="see-also"></a>Siehe auch

[Blog: Exportieren von CDS-Daten nach Azure Data Lake](https://powerapps.microsoft.com/blog/exporting-cds-data-to-azure-data-lake-preview/)
