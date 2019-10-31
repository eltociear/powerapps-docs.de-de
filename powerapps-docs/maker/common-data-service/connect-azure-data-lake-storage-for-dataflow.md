---
title: Verbinden von Azure Data Lake Storage Gen2 für Dataflow-Speicher | MicrosoftDocs
description: Informationen zum Verbinden von Azure Data Lake Storage Gen2 für Dataflow-Speicher
ms.custom: ''
ms.date: 09/05/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: null
caps.latest.revision: null
ms.author: matp
manager: kvivek
tags: null
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="connect-azure-data-lake-storage-gen2-for-dataflow-storage"></a>Verbinden von Azure Data Lake Storage Gen2 für Dataflow-Speicher

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Sie können Dataflows konfigurieren, um ihre Daten im Azure Data Lake Storage Gen2-Konto Ihrer Organisation zu speichern. In diesem Artikel werden die wesentlichen Schritte für diesen Vorgang beschrieben und er enthält Anweisungen und bewährte Methoden. 

Es gibt einige Vorteile beim Konfigurieren von Dataflows zum Speichern der zugehörigen Definitionen und Datendateien in Ihrem Data Lake, u. a. folgende:
- Azure Data Lake Storage Gen2 bietet einen enorm skalierbaren Speicherraum für Daten.
- Dataflow-Daten und -definitionsdateien können durch Entwickler Ihrer IT-Abteilung genutzt werden, um Azure-Daten und KI-Dienste (Künstliche Intelligenz) wie in den GitHub-Beispielen der Azure-Datendienste veranschaulicht zu nutzen.
- Damit können Entwickler in Ihrer Organisation mithilfe von Entwicklerressourcen für Dataflows und Azure Dataflow-Daten in interne Anwendungen und branchenspezifische Lösungen integrieren.

## <a name="requirements"></a>Anforderungen
Sie benötigen Folgendes, um Azure Data Lake Storage Gen2 für Dataflows zu verwenden:
- Eine PowerApps-Umgebung. Sie können mit jedem PowerApps-Plan Dataflows mit Azure Data Lake Storage Gen2 als Ziel erstellen. Sie müssen in Umgebungen als Entwickler autorisiert werden. 
- Ein Azure-Abonnement. Sie benötigen ein Azure-Abonnement, um Azure Data Lake Storage Gen2 zu verwenden.
- Eine Ressourcengruppe. Sie können eine bereits vorhandene Ressourcengruppe nutzen oder eine neue erstellen.
- Ein Azure Storage-Konto. Bei dem Speicherkonto muss die Funktion "Data Lake Storage Gen2" aktiviert sein.

> [!TIP]
> Wenn Sie kein Azure-Abonnement haben, [erstellen Sie ein kostenloses Testkonto](https://azure.microsoft.com/free/), bevor Sie starten.

## <a name="prepare-your-azure-data-lake-storage-gen2-for-power-platform-dataflows"></a>Bereiten Sie Azure Data Lake Storage Gen2 für Power Platform-Dataflows vor
Bevor Sie Power BI mit einem Azure Data Lake Storage Gen2-Konto konfigurieren, müssen Sie ein Speicherkonto erstellen und konfigurieren. Hier sind die Anforderungen für Power Platform-Dataflows:
1.  Das Speicherkonto muss im selben Azure Active Directory-Mandanten wie Ihr PowerApps-Mandant erstellt werden.
2.  Es wird empfohlen, das Speicherkonto in derselben Region wie die PowerApps-Umgebung zu erstellen, in der es verwendet werden soll. Um zu bestimmen, wo Ihre PowerApps-Umgebung ist, wenden Sie sich an den Umgebungsadministrator.
3.  Bei dem Speicherkonto muss die Funktion für den hierarchischen Namespace aktiviert sein.
4.  Dir muss eine Besitzerrolle im Speicherkonto zugewiesen werden.

In den folgenden Abschnitten werden Sie durch die erforderlichen Schritte für die Konfiguration Ihres Azure Data Lake Storage Gen2-Kontos geführt.

## <a name="create-the-storage-account"></a>Erstellen des Speicherkontos
Folgen Sie den Schritten unter [Erstellen eines Azure Data Lake Storage Gen2-Speicherkontos](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-quickstart-create-account).
1.  Stellen Sie sicher, dass Sie denselben Speicherort wie für Ihren Power BI-Mandanten auswählen und Ihren Speicher als SpeicherV2 (universell v2) festlegen.
2.  Stellen Sie sicher, dass Sie die Funktion für den hierarchischen Namespace aktivieren. 
3.  Wir empfehlen, die Replikationseinstellung auf "Georedundanter Speicher (RA-GRS) mit Leseberechtigung" festzulegen.



<!--from editor: I haven't heard of Athena before. Is it the Amazon service, https://aws.amazon.com/athena/? If so, it probably should be identified as Amazon at first mention. -->


## <a name="create-a-cross-origin-resource-sharing-cors-rule-for-the-athena-service"></a>Erstellen einer "Ursprungsübergreifende Ressourcenfreigabe (CORS)"-Regel für den Athena-Service

> [!NOTE]
> Power Platform-Dataflows nutzen den Athena-Service, um einen Data Lake mit einer PowerApps-Umgebung zu verbinden. In diesem Abschnitt werden Sie aufgefordert, dem Athena-Service eine Rolle für das Speicherkonto zuzuweisen, sodass er für die Dataflow-Verwendung konfiguriert werden kann.

Anschließend müssen Sie dem Athena-Service über den Webbrowser und das PowerApps-Portal Zugriff auf das Speicherkonto gewähren. Webbrowser implementieren eine Sicherheitsbeschränkung, auch bekannt als [Same-Origin-Richtlinie](http://www.w3.org/Security/wiki/Same_Origin_Policy), die verhindert, dass eine Webseite APIs in einer anderen Domäne aufruft; CORS bietet eine sichere Möglichkeit, es einer Domäne zu erlauben (die Ursprungsdomäne), APIs in einer anderen Domäne aufzurufen. Weitere Informationen über CORS findest du unter [CORS-Spezifikation](http://www.w3.org/TR/cors/).

Folgen Sie den Schritten im Speicherkonto, das Sie gerade auf der Einstellungsseite im Azure-Portal erstellt haben. Wählen Sie im CORS-Menüelement den Abschnitt "Blob-Dienst" aus und geben Sie diese Details ein. 

|Einstellungen  |Value  |
|---------|---------|
|Zulässige Ursprünge   | https://athena-ui-prod.trafficmanager.net     |
|Zulässige Methoden   |  DELETE, GET, HEAD, MERGE, POST, OPTIONS, PUT, PATCH   |
|Zulässige Kopfzeilen   | *    |
|Öffentlich verfügbare Kopfzeilen   | *    |
|Maximales Alter |   *  |


Auf dem folgenden Bild wird die CORS-Regel gezeigt, die für den Athena-Service konfiguriert ist.

![CORS-Regel](media/dataflows-cores-rule.png)

## <a name="connect-your-azure-data-lake-storage-gen2-to-powerapps"></a>Verbinden von Azure Data Lake Storage Gen2 mit PowerApps
Sobald Sie Ihr Azure Data Lake Storage Gen2-Konto im Azure-Portal eingerichtet haben, können Sie es mit einem bestimmten Dataflow oder einer PowerApps-Umgebung verbinden. Durch die Verbindung eines Lakes mit einer Umgebung können andere Entwickler und Administratoren in der Umgebung Dataflows erstellen, bei denen ihre Daten auch im Lake Ihrer Organisation gespeichert werden. 

Führen Sie diese Schritte aus, um Ihr Azure Data Lake Storage Gen2-Konto mit dem Dataflow zu verbinden:
1.  Melden Sie sich in [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an und überprüfen Sie, in welcher Umgebung Sie sich befinden. Der Umgebungs-Schnellzugriff befindet sich auf der rechten Seite der Kopfzeile. 
2. Wählen Sie im linken Navigationsbereich den Abwärtspfeil neben **Daten** aus.

   ![Registerkarte für PowerApps-Entwicklerportaldaten](media/powerapps-portal-data.png)

3. Wählen Sie in der daraufhin angezeigten Liste die Option **Dataflows** und dann in der Befehlsleiste die Option **Neuer Dataflow** aus.

   ![Erstellen eines neuen Dataflows](media/new-dataflow.png) 

4. Wählen Sie die gewünschten analytischen Entitäten aus. Diese Entitäten geben an, welchen Daten Sie im Azure Data Lake Store Gen2-Konto Ihrer Organisation speichern möchten. 

   ![Auswählen analytischer Entitäten](media/select-analytical-entities.png)

## <a name="select-the-storage-account-to-use-for-dataflow-storage"></a>Auswählen des Speicherkontos zur Nutzung für den Dataflow-Speicher
Wenn ein Speicherkonto noch nicht mit der Umgebung verknüpft wurde, erscheint ein Dialogfeld **Link zum Data Lake**. Sie müssen sich anmelden und den Data Lake suchen, den Sie im vorherigen Schritt erstellt haben. In diesem Beispiel wird kein Data Lake mit der Umgebung verknüpft. Daher erscheint eine Aufforderung, in der Sie gebeten werden, einen hinzuzufügen. 



<!--from editor: Should "storage account" be in bold because it's something the user has to select? --"

1. Select storage account.

    The **Select Storage Account** screen appears.
    
    ![Select storage account](media/select-storage-account.png)
    
2. Select the **Subscription ID** of the storage account.
3. Select the **Resource group name** in which the storage account was created.
4. Enter the **Storage account name**.
5. Select **Save**.

Once these steps are successfully completed, your Azure Data Lake Storage Gen2 account is connected to Power Platform Dataflows and you can continue to create a dataflow.

## Considerations and limitations
There are a few considerations and limitations to keep in mind when working with your dataflow storage:
- Linking an Azure Data Lake Store Gen2 account for dataflow storage is not supported in the default environment.
- Once a dataflow storage location is configured for a dataflow, it can't be changed.
- By default, any member of the environment can access dataflow data using the Power Platform Dataflows Connector. However, only the owners of a dataflow can access its files directly in Azure Data Lake Storage Gen2. To authorize additional people to access the dataflows data directly in the lake, you must authorize them to the dataflow’s CDM folder in the data lake or the data lake itself.
- When a dataflow is deleted, its CDM folder in the lake will also be deleted. 

> [!IMPORTANT]
> You shouldn't change files created by dataflows in your organization’s lake or add files to a dataflow’s CDM folder. Changing files might damage dataflows or alter their behavior and is not supported. Power Platform Dataflows only grants read access to files it creates in the lake. If you authorize other people or services to the filesystem used by Power Platform Dataflows, only grant them read access to files or folders in that filesystem.

## Frequently asked questions
*What if I had previously created dataflows in my organization’s Azure Data Lake Storage Gen2 and would like to change their storage location?*

   You can't change the storage location of a dataflow after it was created.

*When can I change the dataflow storage location of an environment?*

   Changing the environment's dataflow storage location is not currently supported. 

## Next steps
This article provided guidance about how to connect an Azure Data Lake Storage Gen2 account for dataflow storage. 

For more information about dataflows, the Common Data Model, and Azure Data Lake Storage Gen2, see these articles:
- [Self-service data prep with dataflows](https://go.microsoft.com/fwlink/?linkid=2099972)
- [Creating and using dataflows in PowerApps](https://go.microsoft.com/fwlink/?linkid=2100076)
- [Connect Azure Data Lake Storage Gen2 for dataflow storage](https://go.microsoft.com/fwlink/?linkid=2099973)
- [Add data to an entity in Common Data Service](https://go.microsoft.com/fwlink/?linkid=2100075)

For more information about Azure storage, see this article:
- [Azure Storage security guide](https://docs.microsoft.com/azure/storage/common/storage-security-guide)

For more information about the Common Data Model, see these articles:
- [Common Data Model - overview](https://docs.microsoft.com/powerapps/common-data-model/overview) 
- [Common Data Model folders](https://go.microsoft.com/fwlink/?linkid=2045304)
- [CDM model file definition](https://go.microsoft.com/fwlink/?linkid=2045521)

You can ask questions in the [PowerApps Community](https://go.microsoft.com/fwlink/?linkid=2099971).
