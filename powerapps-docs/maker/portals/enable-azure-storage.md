---
title: Aktivieren von Azure Storage für Portale | Microsoft-Dokumentation
description: Anweisungen zum Aktivieren von Azure-Speicherung für Portale, um die größere Speicherungsfunktion von Azure zu nutzen.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 02/12/2020
ms.author: tapanm
ms.reviewer: tapanm
ms.openlocfilehash: ceb25954357efeafec6b33338ff4b617af82ebda
ms.sourcegitcommit: 6cffa70358fd2e388d64a01f906c8c196fbbdefb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/17/2020
ms.locfileid: "3069757"
---
# <a name="enable-azure-storage"></a>Aktivieren von Azure Storage

Die Azure Storage-Integration für Portale ermöglicht Ihnen, die erweiterte Funktion für die Dateispeicherung von Azure zu nutzen, indem Sie dieselbe Oberfläche verwenden und indem dieselbe Benutzerumgebung bereitgestellt wird wie bei Standard-Dateianlagen. Diese Funktion wird für Webdateien, Entitätsformulare und Webformulare unterstützt.

Sie müssen ein Speicherkonto mit dem **Ressourcenmanager** als Bereitstellungsmodell erstellen. [!include[More information](../../includes/proc-more-information.md)] [Erstellen eines Azure-Speicherkontos](https://docs.microsoft.com/azure/storage/storage-create-storage-account#create-a-storage-account).

Wenn das Speicherkonto ausgeführt wird, sind bestimmte globale Einstellungen für Portale erforderlich, die der Anwendung mitteilen, wie Ihr Speicherkonto lokalisiert werden kann. Navigieren Sie in der App Portalverwaltung zu **Einstellungen** > **Neu** und fügen Sie eine neue Einstellung mit dem Namen **FileStorage/CloudStorageAccount** hinzu.

Die Integration der Azure-Speicherung funktioniert nur mit **Notizen**, die in den Entitätsformular-Metadaten konfiguriert sind. Azure Blob als Speicher wird nicht verwendet, wenn Sie **Portal-Kommentare** verwenden, die mit **Timeline** eingerichtet werden können. Obwohl die Portalkommentare auch die Möglichkeit bieten, Dateien als Anhang hochzuladen, werden diese Dateien nur in Common Data Service gespeichert.
 
> [!NOTE]
> Die maximale Dateigröße für den Upload beträgt 125 MB.

Um den Wert für FileStorage/CloudStorageAccount zu suchen, müssen Sie eine Verbindungszeichenfolge von Ihrem [!include[Azure portal](../../includes/pn-azure-portal.md)] abrufen.

1. Melden Sie sich bei Ihrem [!include[Azure portal](../../includes/pn-azure-portal.md)] an.

2. Navigieren Sie zu Ihrem Speicherkonto.

3. Wählen Sie **Zugriffsschlüssel** aus.

    ![Suchen Sie den Wert für die Verbindungszeichenfolge Ihres Azure Portals](media/key-azure-storage.png "Suchen Sie den Wert für die Verbindungszeichenfolge Ihres Azure Portals")

4. Suchen Sie im angezeigten Bereich das Feld mit der Bezeichnung **Verbindungszeichenfolge**. Wählen Sie das Symbol **Kopieren** neben dem Feld, für das Sie den Wert kopieren müssen, und fügen Sie diesen Wert dann in Ihre neue Einstellung ein:

    ![Primärer Verbindungszeichenfolgenwert](media/primary-connection-string-azure-storage.png "Primärer Verbindungszeichenfolgenwert")

    ![Portaleinstellung für Cloudspeicherkonto](media/portal-site-setting-cloud-storage-account.png "Portaleinstellung für Ihr Cloudspeicherkonto")

## <a name="specify-the-storage-container"></a>Angeben des Speichercontainer

Wenn Sie noch keinen Azure Blob-Container in Ihrem Speicherkonto haben, müssen Sie einen über Ihr [!include[Azure portal](../../includes/pn-azure-portal.md)] hinzufügen.

Navigieren Sie in der [App Portalverwaltung](configure/configure-portal.md) zu **Einstellungen** > **Neu** und fügen Sie eine neue Einstellung mit dem Namen **FileStorage/CloudStorageContainerName** hinzu. Verwenden Sie dabei den Namen Ihres Containers als Wert.

![Portaleinstellung für Cloudspeichercontainer](media/portal-site-setting-cloud-storage-container.png "Portaleinstellung für Ihren Cloudspeichercontainer")

## <a name="add-cors-rule"></a>CORS-Regel hinzufügen

Sie müssen auch die ursprungsübergreifende Ressourcenfreigabe (Cross-Origin Resource Sharing, CORS) in Ihrem Azure-Speicherkonto hinzufügen, andernfalls wird das reguläre Anlagensymbol anstelle des Wolkensymbols angezeigt:

- **Zulässige Ursprünge**: Geben Sie Ihre Domäne an. Zum Beispiel: `https://contoso.crm.dynamics.com`.
- **Zulässige Verben**: GET, PUT, DELETE, HEAD, POST
- **Zulässige Überschriften**: Geben Sie die erforderlichen Überschriften an, die möglicherweise die Ursprungsdomäne auf der CORS-Anforderung angibt. Beispielsweise x-ms-meta-data\*, x-ms-meta-target\*. 
- **Verfügbar gemachte Überschriften**: Geben Sie die Antwortheader an, die möglicherweise in der Antwort zur CORS-Anforderung gesendet und vom Browser für den angeforderten Aussteller verfügbar gemacht werden. Beispielsweise x-ms-meta-\*.
- **Höchstalter (Sekunden)**: Geben Sie die größtmöglichenMenge Zeit an, nach der ein Browser die Preflight-OPTIONEN-Anforderungen in den Zwischenspeicher verschiebt. Zum Beispiel 200.
 
[!include[More information:](../../includes/proc-more-information.md)] [CORS-Unterstützung für die Azure Storage Services](https://docs.microsoft.com/rest/api/storageservices/cross-origin-resource-sharing--cors--support-for-the-azure-storage-services)

## <a name="add-site-settings"></a>Website-Einstellungen hinzufügen

Fügen Sie den folgenden Website-Einstellungen von **Portale** > **Website-Einstellungen** hinzu. [!include[More information:](../../includes/proc-more-information.md)] [Verwalten Sie Portalwebsite-Einstellungen](configure/configure-site-settings.md#manage-portal-site-settings).

|Name|Value|
|-----|-----|
|WebFiles/CloudStorageAccount|Stellen Sie dieselbe Verbindungszeichenfolge bereit, die für die Einstellung FileStorage/CloudStorageAccount bereitgestellt wird.|
|WebFiles/StorageLocation|AzureBlobStorage|
|||

Sie können jetzt im Portal eine untergeordneten Datei erstellen und einen voll qualifizierten Namen (zusammen mit Container) in der Azure Blob-Adress-URL nennen. Mit diesen Einstellungen ist Ihr Portal bereit, mit dem Hoch- und Herunterladen von Dateien auf und von Azure Storage zu beginnen. Sie können diese Funktionalität jedoch erst vollständig nutzen, wenn Sie [eine Webressource hinzufügen, um das Hochladen von Anlagen zu Azure Storage zu aktivieren](add-web-resource.md), und [Entitätsformulare](configure-notes.md#notes-configuration-for-entity-forms) oder [Webformulare](configure-notes.md#notes-configuration-for-web-forms) so konfigurieren, dass sie diese verwenden.

### <a name="see-also"></a>Siehe auch

[Webressource hinzufügen](add-web-resource.md)

[Hinweise konfigurieren](configure-notes.md)
