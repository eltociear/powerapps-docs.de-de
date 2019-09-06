---
title: 'Schritt 5: Speichern Sie das AppSource-Paket in Azure Storage und generieren Sie eine URL mit dem SAS-Schlüssel (Common Data Service) | Microsoft Docs'
description: 'Um die Sicherheit Ihrer Dateien zu wahren, müssen alle App-Entwickler die AppSource-Paketdatei in einem Microsoft Azure-Blobspeicherkonto speichern und einen Schlüssel für die Signatur für den gemeinsamen Zugriff (SAS) verwenden, um die Paketdatei freizugeben. Ihre Paketdatei wird von Ihrem Azure Storage Standort für die Zertifizierung und anschließend für die AppSource-Testversionen abgerufen.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="step-5-store-your-appsource-package-on-azure-storage-and-generate-a-url-with-sas-key"></a>Schritt 5: Speichern Sie das AppSource-Paket in Azure Storage und generieren Sie eine URL mit dem SAS-Schlüssel

Microsoft Azure Storage ist ein von Microsoft verwalteter Cloud Service, der Speicher bereitstellt, der extrem verfügbar, sicher, robust, skalierbar und redundant ist. Weitere Informationen: [Einführung in Microsoft Azure-Speicher](https://docs.microsoft.com/azure/storage/common/storage-introduction).

Um die Sicherheit Ihrer Dateien zu wahren, müssen alle App-Entwickler die AppSource-Paketdatei in einem Microsoft Azure-Blobspeicherkonto speichern und einen Schlüssel für die Signatur für den gemeinsamen Zugriff (SAS) verwenden, um die Paketdatei freizugeben. Ihre Paketdatei wird von Ihrem Azure Storage Standort für die Zertifizierung und anschließend für die AppSource-Testversionen abgerufen.

## <a name="before-you-upload-your-package"></a>Bevor Sie das Paket hochladen

Laden Sie den Microsoft Azure Storage Explorer von [http://storageexplorer.com](http://storageexplorer.com) herunter und installieren Sie ihn.

Mit Azure Storage Explorer können Sie problemlos die Inhalte des Storage-Kontos verwalten.

## <a name="upload-your-package-and-generate-a-url-with-sas-key"></a>Laden Sie das Paket hoch und generieren Sie eine URL mit dem SAS-Schlüssel

Um das Paket in den Azure Blob Storage hochzuladen:

1. Erstellen Sie eine kostenlose Testversion oder Sie zahlen, wenn erforderlich unter [https://azure.microsoft.com](https://azure.microsoft.com).
2. Melden Sie sich unter [https://portal.azure.com](https://portal.azure.com) in Ihrem Azure-Verwaltungsportal an.
3. Erstellen eines neuen Speicherkontos durch Klicken > **Speicher** > **Speicherfirma - Blob, Datei-, Tabelle, Warteschlange**.
    
   ![](media/appsource-storageaccount-pic1.png)

4. Klicken Sie auf der Seite **Speicherkonto erstellen** **Name**, **Ressourcengruppe** und **Standort** für das Speicherkonto an. Behalten Sie die übrigen Felder mit Standardoptionen. Klicken Sie auf **Erstellen**. 

   ![](media/appsource-storageaccount-pic2.png)
 
  
5. Wenn das Speicherkonto erstellt wurde, navigieren Sie auf die neu erstellten Ressourcengruppe, und erstellen Sie einen neuen Blobcontainer erstellen. Unter **Blob-Service** wählen Sie **Container** und dann **+ Container**.

   ![](media/appsource-storageaccount-pic3.png)

6. Geben Sie einen Namen für den Container ein und wählen Sie **öffentliche Zugriffstufe** als **Blob** aus. Klicken Sie auf **OK**.

   ![](media/appsource-storageaccount-pic4.png)

7. Starten Sie Azure Storage Explorer auf dem Computer und stellen Sie eine Verbindung mit Ihrem Azure Speicherkonto her, indem Sie sich mit dem selben Konto anmelden, das Sie beim Erstellen des Azure Speicherkontos verwendeten.

8. Im Azure Storage Explorer wählen Sie den neu erstellten Container, und dann **Hochladen** > **Dateien hochladen** aus, um das App-Quellpaket hochzuladen, das Sie in [Schritt 4: Erstellen eines AppSource-Pakets für Ihre App](create-package-app-appsource.md) erstellt haben. 

   ![](media/appsource-storageaccount-pic5.png)

9. Navigieren Sie zur AppSource-Paketdatei auf dem Computer, und wählen Sie sie zum Hochladen aus.

10. Klicken Sie auf die hochgeladene AppSource-Paketdatei mit einem Rechtsklick und wählen Sie **Signatur für den gemeinsamen Zugriff abrufen** aus.

    ![](media/appsource-storageaccount-pic6.png)

11. Klicken Sie auf die Seite **Signatur für den gemeinsamen Zugriffs**, ändern Sie den Wert **Endzeit**, um die aktive Signatur für einen Monat von der **Startzeit** freizugeben. Klicken Sie auf **Erstellen**.

    ![](media/appsource-storageaccount-pic7.png)

12. Die nächste Seite zeigt die Informationen über die erzeugte Information über die Signatur für den gemeinsamen Zugriff. Kopieren Sie den **URL** Wert und speichern Sie ihn für später. Sie müssen diese URL beim Erstellen eines Angebots im Cloud-Partners-Portal angeben.

    ![](media/appsource-storageaccount-pic8.png)


> [!div class="nextstepaction"]
> [Nächste Schritte: Senden der App im Partner Center](next-steps-submit-app-cloud-partner-portal.md)