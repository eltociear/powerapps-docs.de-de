---
title: Hinzufügen der Azure Storage-Webressource zu einem Formular | Microsoft-Dokumentation
description: Schritte zum Hinzufügen einer Azure Storage-Webressource zu einem Formular, um das Hochladen von Anhängen zu Azure Storage zu aktivieren.
author: sbmjais
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 01/07/2020
ms.author: shjais
ms.reviewer: tapanm
ms.openlocfilehash: b98bce4b3b9d2fae1015250c509df30ec69c7797
ms.sourcegitcommit: df15c909ba27c9ed83197305a4ee1f01e46a826b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2020
ms.locfileid: "2936193"
---
# <a name="add-the-azure-storage-web-resource-to-a-form"></a>Hinzufügen der Azure Storage-Webressource zu einem Formular

Anlagen, die zu Azure Storage und nicht direkt zu Common Data Service hochgeladen wurden, können über Notizen in Common Data Service verwaltet werden.

Damit Anlagen aus einem bestimmten Formular nach Azure Storage hochgeladen werden können, müssen Sie eine Webressource zu diesem Formular hinzufügen und [Azure Storage für Ihre Organisation konfigurieren](enable-azure-storage.md).

> [!Note]
> In diesem Beispiel wird das Formular zum Lead-Formular für die Lead-Entität hinzugefügt. Wir empfehlen Ihnen, beim Bearbeiten vorhandener Formulare vorsichtig vorzugehen.

Wenn eine Datei (beispielsweise attachments.zip) über das Portal nach Azure Storage hochgeladen wird, wird dies durch eine Notiz zu einer Entität und einen Platzhalter für die Anlage dargestellt.

![Anlage zu einem Formular](media/notes-attachment-lead-form.png "Platzhalter für die Anlage in einem Formular")

Beachten Sie, dass die Anlagendatei jetzt attachment.zip.txt heißt. Standardmäßig verfügt Common Data Service nicht über die Konzeption einer Azure-Datei, deshalb wird diese TXT-Platzhalterdatei stattdessen in Common Data Service gespeichert. Der Azure Storage-Kontext für die Platzhalterdatei zeigt Details zur Datei an.
```
{
 Name: attachment.zip,
 Type: application/x-zip-compressed,
 Size: 24890882,
 "Url": "https://accountname.blob.core.windows.net/storage/81a9a9491c36e51182760026833bcf82/attachment.zip"
}
```

Um die in Azure gespeicherte Datei anzeigen und mit dieser interagieren zu können, müssen Sie die Webressource adx.annotations.html zum Formular hinzufügen. Stellen Sie als Voraussetzung sicher, dass Ihre Benutzer Lesezugriff auf adx_setting haben. Andernfalls wird die Webressource nicht richtig dargestellt.

1. Wählen Sie im Formular-Editor für das relevante Formular **Webressource** auf der Registerkarte **Einfügen** aus.

2. Wählen Sie im Feld **Webressource** die Option **adx_annotations/adx.annotations.html** aus.

3. Geben Sie einen Namen und eine Bezeichnung für die Ressource an.

4. Geben Sie im Feld **Benutzerdefinierte Parameter (Daten)** den Text **azureEnabled=true** ein. <br>Auf diese Weise können Sie auch die Webressource verwenden, ohne Azure-Unterstützung zu aktivieren. In diesem Fall funktioniert sie fast genau so wie das Standardsteuerelement.</br>

5. Wählen Sie auf der Registerkarte **Formatierung** die von Ihnen bevorzugten Formatierungsregeln aus. Es wird empfohlen, das Kontrollkästchen **Rahmen anzeigen** zu deaktivieren.

6. Wählen Sie **OK** aus, um die Ressource zu speichern.

7. Optional können Sie das vorhandene Notizensteuerelement entfernen oder auf eine Registerkarte bzw. in einen Abschnitt verschieben, für die/den festgelegt ist, dass sie/er standardmäßig nicht angezeigt werden soll.

8. Speichern Sie das Formular, und veröffentlichen Sie anschließend die Änderungen.

   ![Webressource hinzufügen](media/add-web-resource.png "Webressource hinzufügen")

Das neue Steuerelement wird jetzt auf der Seite gerendert, wodurch Sie die Möglichkeit haben, Ihre Anlagen in Azure Storage zu verwalten.

![Azure Dateianlage in einem Formular](media/azure-file-attachment-lead-form.png "Azure Dateianlage in einem Formular")

Das Büroklammersymbol wurde durch ein Wolkensymbol ersetzt, um zu kennzeichnen, dass diese Datei in Azure Storage gespeichert wird. Sie können Anlagen weiterhin in Common Data Service speichern. Diese Dateien werden mit dem Büroklammersymbol gekennzeichnet.

> [!Note]
> Sie müssen auch die ursprungsübergreifende Ressourcenfreigabe (Cross-Origin Resource Sharing, CORS) in Ihrem Azure-Speicherkonto hinzufügen, andernfalls wird das reguläre Anlagensymbol anstelle des Wolkensymbols angezeigt.
> - **Zulässige Ursprünge**: Geben Sie Ihre Domäne an. Zum Beispiel: `https://contoso.crm.dynamics.com`.
> - **Zulässige Verben**: GET, PUT, DELETE, HEAD, POST
> - **Zulässige Überschriften**: Geben Sie die erforderlichen Überschriften an, die möglicherweise die Ursprungsdomäne auf der CORS-Anforderung angibt. Beispielsweise x-ms-meta-data\*, x-ms-meta-target\*. Für dieses Szenario müssen Sie * angeben, da die Webressource sonst nicht richtig dargestellt wird.
> - **Verfügbar gemachte Überschriften**: Geben Sie die Antwortheader an, die möglicherweise in der Antwort zur CORS-Anforderung gesendet und vom Browser für den angeforderten Aussteller verfügbar gemacht werden. Beispielsweise x-ms-meta-\*.
> - **Höchstalter (Sekunden)**: Geben Sie die größtmöglichenMenge Zeit an, nach der ein Browser die Preflight-OPTIONEN-Anforderungen in den Zwischenspeicher verschiebt. Zum Beispiel 200.
> 
> [!include[More information](../../includes/proc-more-information.md)] [CORS-Unterstützung für die Azure Storage Services](https://docs.microsoft.com/rest/api/storageservices/cross-origin-resource-sharing--cors--support-for-the-azure-storage-services).

Wenn es sich bei der angehängten Datei um ein Bild handelt, zeigt das Steuerelement das Bild als Miniaturansicht an, gleich, ob es in Common Data Service oder in Azure Storage gespeichert ist.

> [!Note]
> Die Miniaturansichtsfunktion ist auf Bilder mit einer Größe von weniger als 1 MB beschränkt.

![Nachrichten-Miniaturansicht](media/notes-thumbnail.png "Nachrichten-Miniaturansicht")

## <a name="cors-protocol-support"></a>CORS-Protokollunterstützung

Das Protokoll zur [ursprungsübergreifenden Ressourcenfreigabe (Cross-Origin Resource Sharing, CORS)](https://www.w3.org/TR/cors/) besteht aus einem Satz an Headern, der angibt, ob eine Antwort für eine andere Domäne freigegeben werden kann.
Die folgenden Websiteeinstellungen werden verwendet, um CORS zu konfigurieren:

|                 Name                  |                                                                            Beschreibung                                                                            |
|---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| HTTP/Access-Control-Allow-Credentials | Der einzige gültige Wert für diesen Header ist "true" (Groß-/Kleinschreibung wird beachtet). Wenn keine Anmeldeinformationen erforderlich sind, können Sie diesen Header vollständig weglassen (anstatt den Wert auf "false" zu setzen). |
|   HTTP/Access-Control-Allow-Headers   |                                                   Eine durch Kommas getrennte Liste der unterstützten HTTP-Anforderungsheader.                                                   |
|   HTTP/Access-Control-Allow-Methods   |                                      Eine durch Kommas getrennte Liste der zulässigen HTTP-Anforderungsmethoden wie ABRUFEN, POSTEN, OPTIONEN.                                       |
|   HTTP/Access-Control-Allow-Origin    |                   Damit alle Ressourcen auf Ihre Ressourcen zugreifen können, können Sie \* angeben. Geben Sie andernfalls die URI an, die auf die Ressourcen zugreifen kann.                   |
|  HTTP/Access-Control-Expose-Headers   |                Eine durch Kommas getrennte Liste mit anderen HTTP-Headernamen als den einfachen Antwortheadern, die die Ressource verwenden kann und die eingeblendet werden kann.                 |
|      HTTP/Access-Control-Max-Age      |                                                       Die maximale Anzahl an Sekunden, die die Ergebnisse zwischengespeichert werden können.                                                        |
|                                       |                                                                                                                                                                   |

