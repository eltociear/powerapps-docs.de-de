---
title: Hinzufügen einer Azure Storage-Webressource zu einem Formular | MicrosoftDocs
description: Schritte zum Hinzufügen von Azure Storage-Webressourcen zu einem Formular zum Aktivieren des Hochladens von Anlagen in Azure Storage
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: ed1053c758f97234ad94a09832683ff00ef17744
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72977563"
---
# <a name="add-the-azure-storage-web-resource-to-a-form"></a>Hinzufügen einer Azure Storage-Webressource zu einem Formular

Anlagen, die auf Azure Storage anstatt direkt in Common Data Service hochgeladen werden, können mithilfe von Notizen in Common Data Service verwaltet werden.

Damit Anlagen von einem bestimmten Formular in Azure Storage hochgeladen werden können, müssen Sie dem Formular eine Webressource hinzufügen und [Azure Storage für Ihre Organisation konfigurieren](enable-azure-storage.md).

> [!Note]
> In diesem Beispiel wird das Formular dem Lead Formular für die Lead-Entität hinzugefügt. Beim Bearbeiten vorhandener Formulare wird die Verwendung von Vorsicht empfohlen.

Wenn eine Datei (z. b. Anhänge. zip) über das Portal in Azure Storage hochgeladen wird, wird Sie durch einen Hinweis auf eine Entität und einen Platzhalter für die Anlage dargestellt.

![Anlage auf einem Formular](media/notes-attachment-lead-form.png "Platzhalter für die Anlage auf einem Formular")

Beachten Sie, dass die Anlagen Datei jetzt "Attachment. zip. txt" heißt. Standardmäßig ist Common Data Service kein Konzept für eine Azure-Datei, sodass diese Datei "plachalter. txt" stattdessen in Common Data Service gespeichert wird. Der Azure Storage Kontext der Platzhalter Datei zeigt Details zur Datei an.
```
{
 Name: attachment.zip,
 Type: application/x-zip-compressed,
 Size: 24890882,
 "Url": "https://accountname.blob.core.windows.net/storage/81a9a9491c36e51182760026833bcf82/attachment.zip"
}
```

Um die in Azure gespeicherte Datei anzuzeigen und mit ihr zu interagieren, müssen Sie die Webressource "adx. Annotations. html" dem Formular hinzufügen. Stellen Sie als Voraussetzung sicher, dass Ihre Benutzer über Lesezugriff auf adx_setting verfügen. Andernfalls wird die Webressource nicht ordnungsgemäß Rendering.

1. Wählen Sie im Formular-Editor für das relevante Formular auf der Registerkarte **Einfügen** die Option **Webressource** aus.

2. Wählen Sie im Feld Webressource die Option **adx_annotations/adx. Annotations. html**aus.

3. Geben Sie einen Namen und eine Bezeichnung für die Ressource ein.

4. Geben Sie im Feld **benutzerdefinierter Parameter (Daten)** **azureaktiviertes = true**ein. <br>Sie können auch die Webressource verwenden, ohne den Azure-Support auf diese Weise zu aktivieren. in diesem Fall funktioniert Sie fast vollständig genauso wie das Standard Steuerelement.</br>

5. Wählen Sie auf der Registerkarte **Formatierung** die gewünschten Formatierungs Regeln aus. Es wird empfohlen, das Kontrollkästchen **Anzeige** Rahmen zu deaktivieren.

6. Wählen Sie **OK** aus, um die Ressource zu speichern.

7. Optional können Sie das vorhandene Notes-Steuerelement entfernen oder es in eine Registerkarte oder einen Abschnitt verschieben, die als standardmäßig nicht sichtbar markiert ist.

8. Speichern Sie das Formular, und veröffentlichen Sie dann die Änderungen.

   ![Webressource]hinzufügen(media/add-web-resource.png "Webressource hinzufügen")

Das neue Steuerelement wird nun auf der Seite gerendert, sodass Sie Ihre Anlagen in Azure Storage verwalten können.

![Azure-Datei Anlage in einem Formular](media/azure-file-attachment-lead-form.png "Azure-Datei Anlage in einem Formular")

Das Papierclip Symbol wurde durch ein cloudsymbol ersetzt, um anzugeben, dass diese Datei in Azure Storage gespeichert wird. Sie können Anlagen weiterhin in Common Data Service speichern. Diese Dateien werden mit dem Papierclips-Symbol gekennzeichnet.

> [!Note]
> Sie müssen eine cors-Regel (Cross-Origin Resource Sharing, Cross-Origin Resource Sharing) für Ihr Azure Storage Konto wie folgt hinzufügen. andernfalls wird das Symbol für die reguläre Anlage anstelle des cloudsymbols angezeigt.
> - **Zulässige Ursprünge**: Geben Sie Ihre Domäne an. Beispielsweise contoso.CRM.Dynamics.com.
> - **Zulässige Verben**: Get, Put, DELETE, Head, Post
> - **Zulässige Header**: Geben Sie die Anforderungs Header an, die die Ursprungs Domäne für die cors-Anforderung angeben kann. Beispiel: x-ms-Meta-Data\*, x-ms-Meta-Target\*. In diesem Szenario müssen Sie * angeben. andernfalls wird die Webressource nicht ordnungsgemäß dargestellt.
> - Verfügbar gemachte **Header**: Geben Sie die Antwortheader an, die in der Antwort auf die cors-Anforderung gesendet und vom Browser für den Anforderungs Aussteller verfügbar gemacht werden können. Beispiel: x-ms-Meta-\*.
> - **Maximales Alter (Sekunden)** : Geben Sie die maximale Zeit an, die ein Browser die Preflight Options-Anforderung Zwischenspeichern soll. Beispiel: 200.
> 
> [!include[More information](../../includes/proc-more-information.md)] [cors-Unterstützung für die Azure Storage Services](https://docs.microsoft.com/rest/api/storageservices/cross-origin-resource-sharing--cors--support-for-the-azure-storage-services).

Wenn die angefügte Datei ein Bild ist, zeigt das Steuerelement das Bild als Miniaturansicht an, unabhängig davon, ob es in Common Data Service oder Azure Storage gespeichert ist.

> [!Note]
> Die Miniaturansicht ist auf Bilder mit einer Größe von weniger als 1 MB beschränkt.

![Hinweise](media/notes-thumbnail.png "zur Miniaturansicht") für Miniaturansichten

## <a name="cors-protocol-support"></a>Cors-Protokoll Unterstützung

Das [cors-Protokoll (Cross-Origin Resource Sharing)](http://www.w3.org/TR/cors/) besteht aus einem Satz von Headern, der angibt, ob eine Antwort mit einer anderen Domäne gemeinsam genutzt werden kann.
Zum Konfigurieren von cors werden die folgenden Site Einstellungen verwendet:

|                 Name                  |                                                                            Beschreibung                                                                            |
|---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| HTTP/Access-Control-Allow-Anmelde Informationen | Der einzige gültige Wert für diesen Header ist true (Groß-/Kleinschreibung wird beachtet). Wenn Sie keine Anmelde Informationen benötigen, lassen Sie diesen Header vollständig aus (anstatt den Wert auf "false" festzulegen). |
|   HTTP/Access-Control-Allow-Headers   |                                                   Eine durch Trennzeichen getrennte Liste der unterstützten HTTP-Anforderungs Header.                                                   |
|   HTTP/Access-Control-Allow-Methods   |                                      Eine durch Trennzeichen getrennte Liste der zulässigen HTTP-Anforderungs Methoden wie Get, Post, Options.                                       |
|   HTTP/Access-Control-Allow-Origin    |                   Um allen Ressourcen den Zugriff auf Ihre Ressourcen zu ermöglichen, können Sie \*angeben. Geben Sie andernfalls den URI an, der auf die Ressourcen zugreifen kann.                   |
|  HTTP/Access-Control-Expose-Headers   |                Eine durch Trennzeichen getrennte Liste von HTTP-Headern, die keine einfachen Antwortheader sind, die von der Ressource verwendet werden können und die verfügbar gemacht werden können.                 |
|      HTTP/Access-Control-max-age      |                                                       Maximale Anzahl von Sekunden, die die Ergebnisse zwischengespeichert werden können.                                                        |
|                                       |                                                                                                                                                                   |

