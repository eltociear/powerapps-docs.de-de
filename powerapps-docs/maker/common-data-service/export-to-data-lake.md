---
title: Zu Data Lake exportieren | MicrosoftDocs
description: Erfahren Sie, wie Sie Entitätsdaten in einen Azure Data Lake exportieren in Power Apps
ms.custom: ''
ms.date: 01/28/2020
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
ms.openlocfilehash: 152fc65e69ccb728727f92ed77d6495f6dc5dcab
ms.sourcegitcommit: 303d5aed44f2bbb406cabeb6b9c8474d738d9114
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "3005276"
---
# <a name="export-entity-data-to-azure-data-lake-gen-2"></a>Exportieren Sie Entitätsdaten in Azure Data Lake Gen 2

Der Export nach Data Lake Service ist eine Pipeline, aus der Daten kontinuierlich exportiert werden von Common Data Service zu Azure Data Lake Gen 2. Der Export zum Data Lake-Service wurde für die Big Data-Analyse im Unternehmen entwickelt, indem skalierbare Hochverfügbarkeit mit Funktionen zur Wiederherstellung nach einem Katastrophenfall bereitgestellt wird. Daten werden im Common Data Model Format (CDM) gespeichert, das eine semantische Konsistenz für alle Apps und Bereitstellungen bietet. 

![Zu Data Lake exportieren, Übersicht](media/export-data-lake-overview.png)

Der Export zu Data Lake bietet die folgenden Funktionen: 
- Verknüpfen oder trennen Sie die Common Data Service Umgebung zu einem Data Lake Gen 2 in Ihrem Azure Abonnement. 
- Fortlaufende Replikation von Entitäten in Azure Data Lake Gen 2.
- Erstes Schreiben, gefolgt von inkrementellen Schreibvorgängen für Daten und Metadaten. 
- Repliziert sowohl Standard- als auch benutzerdefinierte Entitäten. 
- Replikate erstellen, aktualisieren und Transaktionen löschen. 
- Kontinuierliche Snapshot-Updates für umfangreiche Analyseszenarien. 
- Erleichtert die Suche nach Metadaten und die Interoperabilität zwischen Datenproduzenten und -konsumenten wie Power BI, Azure Data Factory, Azure Databricks und Azure Machine Learning Service.

## <a name="how-data-and-metadata-are-exported"></a>Wie Daten und Metadaten exportiert werden
Der Export in den Data Lake Service unterstützt das anfängliche und inkrementelle Schreiben von Entitätsdaten und Metadaten. Alle Daten oder Metadatenänderungen in Common Data Service werden ohne weitere Aktion automatisch zum Data Lake übertragen. Dies ist eher eine Push- als eine Pull-Operation. Änderungen werden an das Ziel übertragen, ohne dass Aktualisierungsintervalle eingerichtet werden müssen. 

Es können sowohl Standard- als auch benutzerdefinierte Entitäten exportiert werden. Beachten sie, dass die Änderungsnachverfolgungsfunktion in Common Data Service verwendet wird, um die Daten effizient zu synchronisieren, indem festgestellt wird, welche Daten geändert wurden, nachdem die Daten ursprünglich extrahiert oder zuletzt synchronisiert wurden. 

Alle Erstellungs-, Aktualisierungs- und Löschvorgänge (CrUD) werden aus exportiert Common Data Service zum Data Lake. Wenn ein Benutzer beispielsweise einen Kontoentitätsdatensatz in Common Data Service löscht, wird die Transaktion auf den Ziel Data Lake repliziert.

## <a name="prerequisites"></a>Voraussetzungen
Bevor Sie die Common Data Service Daten zu einem Data Lake exportieren können, müssen Sie ein Azure StorageV2-Speicherkonto (General Purpose v2) erstellen und konfigurieren. 

Folgen Sie den Schritten im [Erstellen Sie ein Azure Storage Konto](/azure/storage/blobs/data-lake-storage-quickstart-create-account) Artikel und beachten Sie diese Anforderungen: 
- Ihnen muss eine Besitzerrolle im Speicherkonto zugewiesen werden. 
- Stellen Sie Ihren Speichertyp ein als **Speicher v2 (Universell v2)**. 
- Bei dem Speicherkonto muss die Funktion für den **Hierarchischen Namespace** aktiviert sein. 
 - Wir empfehlen, die Replikationseinstellung auf Georedundanter Speicher (RA-GRS) mit Leseberechtigung festzulegen. Mehr Informationen: [Georedundanter Speicher mit Lesezugriff](/azure/storage/common/storage-redundancy-grs#read-access-geo-redundant-storage) 
>   ![Speicherkonto Eigenschaften](media/storage-account-properties.png)

> [!NOTE]
> - Das Speicherkonto muss im selben Azure AD-Mandanten wie Ihr PowerApps-Mandant erstellt werden.  
> - Es wird empfohlen, das Speicherkonto in derselben Region wie die PowerApps Umgebung zu erstellen, in der die Funktion verwendet werden soll.  
>  - Zum verlinken der Common Data Service Umgebung für Azure Data Lake Gen 2 müssen Sie ein Common Data Service Administrator sein. 
>  - Nur Entitäten, die die Änderungsnachverfolgung aktiviert haben, können exportiert werden. 


## <a name="select-and-export-common-data-service-entity-data-to-azure-data-lake-gen-2"></a>Wählen und exportieren Sie Common Data Service Entitätsdaten in Azure Data Lake Gen 2
1. Einloggen in [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), erweitern von **Daten** und dann **Entitäten** auswählen. 
2. Wählen Sie in der Befehlsleiste **In Data Lake exportieren** und dann auf der Seite **In Data Lake exportieren** wählen Sie **Neuer Link zum Data Lake**. 
3. Wählen Sie jeder der folgenden Einstellungen und dann **Weiter**: 
   - **Abonnement**. Wählen Sie Ihr Azure Abonnement. 
   - **Ressourcengruppe**. Wählen Sie die Ressourcengruppe aus, die das Speicherkonto Storagev2 (General Purpose v2) enthält.
   - **Speicherkonto**. Wählen Sie die Ressourcengruppe aus, die das Speicherkonto Storagev2 (General Purpose v2) enthält, das für den Export verwendet wird. 
4. Wählen Sie die Entitäten aus, die Sie zum Data Lake exportieren möchten und wählen Sie dann **Speichern** aus. Nur Entitäten, die die Änderungsnachverfolgung aktiviert haben, können exportiert werden. Mehr Informationen: [Änderungsverfolgung für eine Entität aktivieren](/dynamics365/customer-engagement/admin/enable-change-tracking-control-data-synchronization)

   > [!div class="mx-imgBorder"] 
   > ![Die zu exportierende Entitäten auswählen](media/export-data-lake-select-entity.png)

Ihre Common Data Service Umgebung ist mit dem Azure Data Lake Gen 2-Speicherkonto verknüpft. Das Dateisystem im Azure-Speicherkonto wird mit einem Ordner für jede Entität erstellt, die zum Replizieren in den Data Lake ausgewählt wurde. 

## <a name="manage-entity-data-to-the-data-lake"></a>Entitätsdaten zum Data Lake verwalten
Nachdem Sie in Ihrem Abonnement den Datenexport in den Azure-Datensee 2 eingerichtet haben, können Sie den Export von Entitätsdaten in den Data Lake auf zwei Arten verwalten. 

- Im Bereich Power Apps Herstellerportal **zum Data Lake exportieren** wählen Sie **Entitäten verwalten** in der Befehlsleiste, um eine oder mehrere verknüpfte Entitäten hinzuzufügen oder zu entfernen.
- Im Bereich Power Apps Herstellerportal **Entitäten** wählen Sie **…** Klicken Sie neben einer Entität auf den verknüpften Data Lake, in den Sie Entitätsdaten exportieren möchten. 
   ![Wählen Sie eine Entität für den Export aus](media/select-entity-export.png)


Um die Verknüpfung aller verknüpften Entitäten zu lösen, klicken Sie auf Power Apps Herstellerportal **In Data Lake Bereich exportieren**, wählen **Verknüpfung zum Data Lake aufheben**. 

## <a name="view-your-data-in-the-azure-data-lake-gen-2"></a>Zeigen Sie Ihre Daten im Azure Data Lake Gen 2 an
1. Melden Sie sich bei [Azure](https://portal.azure.com) an und wählen Sie das Speicherkonto aus, und wählen Sie dann im linken Navigationsbereich **Speicher-Explorer**. 
2. Erweitern von **Dateisysteme**, wählen Sie dann commondataservice-*environmentName*-org-*ID*. 

Die Datei model.json enthält neben Name und Version eine Liste der Entitäten, die in den Lake exportiert wurden. Die model.json-Datei enthält auch den anfänglichen Synchronisierungsstatus und die abgeschlossene Zeit. 

Es wird ein Ordner für jede Entität angezeigt, die in den Data Lake exportiert wurde. Dieser Ordner enthält Dateien im CSV-Format (Snapshot Command Delimited Format). 
   > [!div class="mx-imgBorder"] 
   > ![Objektdaten im Lake](media/entity-data-in-lake.png) 

### <a name="continuous-snapshot-updates"></a>Kontinuierliche Snapshot-Updates
Common Data Service Daten können sich kontinuierlich durch das Erstellen, Aktualisieren und Löschen von Transaktionen ändern. Snapshots bieten eine schreibgeschützte Snapshot-Kopie von Daten, die in regelmäßigen Abständen, dh stündlich, aktualisiert werden. Dies stellt sicher, dass ein Datenanalyse-Konsument zu jedem Zeitpunkt zuverlässig Daten im Lake konsumieren kann.   

![Kontinuierliche Snapshot Updates](media/snapshot-updates.png)

Wenn beim ersten Export Entitäten hinzugefügt werden, werden die Entitätsdaten in die Datei entity.csv unter den entsprechenden Ordnern im Lake geschrieben. Dies ist das T1-Intervall, in dem eine schreibgeschützte Momentaufnahme-Datei namens *Entität* -T1.csv, z. B. Konto-T1.csv und Kontakte-T1.csv, erstellt wird. Darüber hinaus wird die model.json-Datei aktualisiert, um auf diese Momentaufnahme-Dateien zu verweisen. Durch Öffnen der Datei model.json können Sie die Details der Momentaufnahme anzeigen. 

Hier ist ein Beispiel für eine partitionierte Account.csv-Datei und einen Momentaufnahme-Ordner im See.
![Momentaufnahme der Kontenentität](media/export-data-lake-account-snapshots.png) 

Änderungen in Common Data Service werden unter Verwendung der Trickle-Feed-Engine kontinuierlich in die entsprechenden CSV-Dateien verschoben. Dies ist das T2-Intervall, in dem eine weitere Momentaufnahme erstellt wird. *Entität* -T2.csv, z. B. Accounts-T2.csv und Contacts-T2.csv (vorausgesetzt, es gibt Änderungen für beide Entitäten), und model.json werden auf die neuen Momentaufnahme-Dateien aktualisiert. Jede neue Person, die Momentaufnahme-Daten ab T2 anzeigt, wird zu den neueren Momentaufnahme-Dateien weitergeleitet. Auf diese Weise kann der ursprüngliche Momentaufnahme-Viewer weiterhin mit den älteren Momentaufnahme-T1-Dateien arbeiten, während neuere Viewer die neuesten Updates lesen können. Dies ist nützlich in Szenarien mit länger laufenden nachgeordneten Prozessen. 

Hier ist ein Beispiel für die model.json-Datei, die immer auf die aktuellste mit einem Zeitstempel versehene Konto-Momentaufnahme-Datei verweist. 

![Beispiel Momentaufnahme-Json](media/sample-snapshot-json.png) 

## <a name="transporting-export-to-data-lake-configuration-across-environments"></a>Transportieren des Exports in die Data Lake-Konfiguration in verschiedenen Umgebungen
In Power Apps werden Lösungen genutzt, um Anwendungen und Komponenten von einer Umgebung in eine andere zu transportieren oder eine Reihe von Anpassungen auf bestehende Anwendungen anzuwenden. Importieren Sie die Lösung Export in Data Lake Core in die Umgebung, um den Export in Data Lake-Konfigurationen zu ermöglichen. Dies ermöglicht grundlegende Funktionen für das Application Lifecycle Management (ALM) wie die Verteilung sowie das Sichern und Wiederherstellen des Exports in die Data Lake-Konfiguration. 

### <a name="import-the-export-to-data-lake-core-solution"></a>Importieren Sie die Export to Data Lake Core-Lösung 
1.  Von dem Power Apps Herstellerportal wählen Sie die Umgebung aus, in der Sie den Export in die Data Lake-Konfiguration verteilen möchten.
2.  Wählen Sie im linken Navigationsbereich **Lösungen** aus und wählen Sie **Öffnen AppSource**, Suchen Sie nach der Lösung mit dem Namen **In Data Lake Core exportieren** und importieren Sie dann die Lösung.

### <a name="add-an-export-to-data-lake-configuration-to-a-solution"></a>Hinzufügen eines Exports zur Data Lake Konfiguration zu einer Lösung

> [!IMPORTANT]
> Bevor Sie einen Export zur Data Lake Konfiguration hinzufügen können, müssen Sie die zuvor beschriebene Export to Data Lake Core-Lösung installieren. 

1.  Von dem Power Apps Herstellerportal wählen Sie die Umgebung aus, in der Sie den Export in die Data Lake-Konfiguration verteilen möchten, und klicken Sie dann im linken Navigationsbereich auf **Lösungen**. 
2.  Wählen Sie **Neue Lösung** und geben Sie einen Namen ein, wählen Sie einen Herausgeber aus und geben Sie dann eine Versionsnummer an.  
3.  Öffnen Sie die im vorherigen Schritt erstellte Lösung und wählen Sie **Vorhandenes hinzufügen** > **Andere** > **Export nach Data Lake Config**. 
4.  Wählen Sie die verknüpften Data Lake Konfigurationen aus, die Sie möchten, und wählen Sie dann **hinzufügen** aus. 
5.  In dem **Lösungen** Bereich, wählen Sie die Lösung, wählen Sie in der Befehlsleiste **Export**. 
6.  In dem **Bevor Sie exportieren** Bereich auswählen **Veröffentlichen**, um alle Änderungen vor dem Export zu veröffentlichen, und wählen Sie dann **Nächster**. 

### <a name="import-the-solution-that-contains-the-export-to-data-lake-configuration"></a>Importieren Sie die Lösung, die den Export in die Data Lake-Konfiguration enthält
In der Umgebung, in die Sie Ihre Lösung importieren möchten, klicken Sie im Bereich Power Apps Herstellerportal **Lösungen** und importieren Sie die Lösung. 

#### <a name="verify-the-export-to-data-lake-configuration"></a>Prüfen Sie den Export zur Data Lake Konfiguration
Von dem Power Apps Herstellerportal in der Umgebung, in der Sie den Export in die Data Lake-Konfiguration importiert haben, prüfen Sie, dass Sie Ihre verknüpften Data Lake sowie die Entitäten sehen können, die Sie aus Ihrer anderen Umgebung transportiert haben.
> [!div class="mx-imgBorder"] 
> ![Importierter Export in Data Lake-Entitäten](media/imported-export-entities.png) 

### <a name="see-also"></a>Siehe auch
[Blog: Exportieren von CDS-Daten nach Azure Data Lake](https://powerapps.microsoft.com/blog/exporting-cds-data-to-azure-data-lake-preview/)