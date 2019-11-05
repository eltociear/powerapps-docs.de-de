---
title: Aktivieren von Azure Storage für Portale | MicrosoftDocs
description: Anweisungen zum Aktivieren von Azure Storage für Portale, um von der größeren Dateispeicher Funktion von Azure zu profitieren.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 3da40cfdcb88726384218c4b1df370c301f8ac16
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542558"
---
# <a name="enable-azure-storage"></a>Aktivieren von Azure Storage

Mit Azure Storage Integration für Portale können Sie die größere Dateispeicher Funktion von Azure nutzen, indem Sie die gleiche Schnittstelle verwenden und die gleiche Benutzeroberfläche wie bei Standarddatei Anlagen bereitstellen. Diese Funktion wird für Webdateien, Entitäts Formulare und Web Forms unterstützt.

Sie müssen ein Speicherkonto mit **Resource Manager** als Bereitstellungs Modell erstellen. [!include[More information](../../includes/proc-more-information.md)] [Erstellen Sie ein Azure-Speicherkonto](https://docs.microsoft.com/azure/storage/storage-create-storage-account#create-a-storage-account).

Nachdem das Speicherkonto ausgeführt wurde, benötigen Portale bestimmte globale Einstellungen, die der Anwendung mitteilen, wie Sie Ihr Speicherkonto suchen. Wechseln Sie in der Portal Verwaltungs-APP zu **Einstellungen** > **neu**, und fügen Sie eine neue Einstellung mit dem Namen **FileStorage/cloudstorageaccount**hinzu.

> [!NOTE]
> Die maximale Dateiuploadgröße beträgt 125 MB.

Um den Wert für FileStorage/cloudstorageaccount zu suchen, müssen Sie eine Verbindungs Zeichenfolge aus Ihrem [!include[Azure portal](../../includes/pn-azure-portal.md)]erhalten.

1. Melden Sie sich bei Ihrem [!include[Azure portal](../../includes/pn-azure-portal.md)]an.

2. Navigieren Sie zu Ihrem Speicherkonto.

3. Wählen Sie **Zugriffsschlüssel**aus.

    ![Wert für Verbindungs Zeichenfolge aus Ihrem Azure-Portal suchen](media/key-azure-storage.png "Suchen Sie den Wert für die Verbindungs Zeichenfolge aus Ihrem Azure-Portal")

4. Suchen Sie im Ergebnisbereich das Feld mit der Bezeichnung **Verbindungs Zeichenfolge**. Wählen Sie das **Kopier** Symbol neben dem Feld aus, für das Sie den Wert kopieren müssen, und fügen Sie diesen Wert in die neue Einstellung ein:

    ![Wert der primären Verbindungs Zeichenfolge](media/primary-connection-string-azure-storage.png "Wert der primären Verbindungs Zeichenfolge")

    ![Portal Einstellung für das cloudspeicherkonto](media/portal-site-setting-cloud-storage-account.png "Portal Einstellung für Ihr cloudspeicherkonto")

## <a name="specify-the-storage-container"></a>Geben Sie den Speicher Container an.

Wenn Sie nicht bereits über einen Azure-BLOB-Container in Ihrem Speicherkonto verfügen, müssen Sie einen mit Ihrem [!include[Azure portal](../../includes/pn-azure-portal.md)]hinzufügen.

Wechseln Sie in der [Portal Verwaltungs-App](configure/configure-portal.md)zu **Einstellungen** > **neu**, und fügen Sie eine neue Einstellung mit dem Namen **FileStorage/cloudstoragecontainername**hinzu. verwenden Sie dazu den Namen Ihres Containers als Wert.

![Portal Einstellung für den Cloud-Speicher Container](media/portal-site-setting-cloud-storage-container.png "Portal Einstellung für Ihren cloudspeichercontainer")

## <a name="add-cors-rule"></a>Cors-Regel hinzufügen

Sie müssen eine cors-Regel (Cross-Origin Resource Sharing, Cross-Origin Resource Sharing) für Ihr Azure Storage Konto wie folgt hinzufügen. andernfalls wird anstelle des cloudsymbols das Symbol für die reguläre Anlage angezeigt:

- **Zulässige Ursprünge**: Geben Sie Ihre Domäne an. Beispielsweise contoso.CRM.Dynamics.com.
- **Zulässige Verben**: Get, Put, DELETE, Head, Post
- **Zulässige Header**: Geben Sie die Anforderungs Header an, die die Ursprungs Domäne für die cors-Anforderung angeben kann. Beispiel: x-ms-Meta-Data\*, x-ms-Meta-Target\*. 
- Verfügbar gemachte **Header**: Geben Sie die Antwortheader an, die in der Antwort auf die cors-Anforderung gesendet und vom Browser für den Anforderungs Aussteller verfügbar gemacht werden können. Beispiel: x-ms-Meta-\*.
- **Maximales Alter (Sekunden)** : Geben Sie die maximale Zeit an, die ein Browser die Preflight Options-Anforderung Zwischenspeichern soll. Beispiel: 200.
 
[!include[More information:](../../includes/proc-more-information.md)] [cors-Unterstützung für die Azure Storage Services](https://docs.microsoft.com/rest/api/storageservices/cross-origin-resource-sharing--cors--support-for-the-azure-storage-services)

## <a name="add-site-settings"></a>Website Einstellungen hinzufügen

Fügen Sie die folgenden Standorteinstellungen aus **Portalen** > **Site Einstellungen**hinzu. [!include[More information:](../../includes/proc-more-information.md)] Verwaltungs [Portal-Website Einstellungen verwalten](configure/configure-site-settings.md#manage-portal-site-settings).

|Name|Value|
|-----|-----|
|WebFiles/cloudstorageaccount|Geben Sie die gleiche Verbindungs Zeichenfolge wie für die Einstellung FileStorage/cloudstorageaccount an.|
|WebFiles/storageloation|AzureBlobStorage|
|||

Sie können jetzt eine untergeordnete Datei im Portal erstellen und in der Azure-BLOB-Adress-URL den voll qualifizierten Namen (zusammen mit dem Container) erwähnen. Mit diesen Einstellungen kann Ihr Portal mit dem Hochladen und Herunterladen von Dateien in und aus Azure Storage beginnen. Sie können diese Funktion jedoch erst nutzen, wenn Sie [eine Webressource hinzufügen, die das Hochladen von Anlagen in Azure Storage](add-web-resource.md)und das Konfigurieren von [Entitäts Formularen](configure-notes.md#notes-configuration-for-entity-forms) oder [Web Forms](configure-notes.md#notes-configuration-for-web-forms) für die Verwendung ermöglicht.

### <a name="see-also"></a>Siehe auch

[Webressource hinzufügen](add-web-resource.md)

[Notizen konfigurieren](configure-notes.md)
