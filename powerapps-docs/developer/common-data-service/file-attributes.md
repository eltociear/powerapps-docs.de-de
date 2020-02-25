---
title: Dateiattribute (Common Data Service) | Microsoft-Dokumentation
description: Infos zu Dateiattributen, die Dateidaten in der Anwendung speichern, sowie zum Unterstützen von Attributen, Abrufen von Daten und Hochladen von Dateidaten.
ms.custom: ''
ms.date: 10/04/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: phecke
ms.author: pehecke
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 73858109ed8e43c5693061a2141e8e30e68f8623
ms.sourcegitcommit: b250e63e881d9bd10c0b3dea36c7f12e8a9c6ac2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2020
ms.locfileid: "2987921"
---
# <a name="file-attributes"></a>Dateiattribute

Ein Dateiattribut wird zum Speichern von Dateidaten bis zu einer angegebenen maximalen Größe verwendet. Eine benutzerdefinierte oder anpassbare Entität kann null oder mehr Dateiattribute sowie eine Sammlung der Notizen (Anmerkungen) mit null bis einer Anlage in den jeweiligen Notizen haben. Der <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.SchemaName> des Dateiattributs ist `EntityFile`.

Web-API (REST) | .NET-API (SOAP)
------- | -------
FileAttributeMetadata | <xref:Microsoft.Xrm.Sdk.Metadata.FileAttributeMetadata>

Informationen zu den nicht zulässigen Dateitypen finden Sie auf der [Registerkarte „Systemeinstellungen“ > „Allgemein“](/power-platform/admin/system-settings-dialog-box-general-tab) unter der Einstellung **Gesperrte Dateierweiterungen für Anlagen festlegen**.

> [!IMPORTANT]
> Einige Einschränkungen gelten, wenn die Datei und die erweiterten Bild-Datentypen von Common Data Service verwendet werden. Wenn Customer Managed Keys (CMK) für den Mandanten aktiviert sind, sind Datei-, Bild- und IoT-Datentypen nicht für Organisationen des Mandanten verfügbar. Lösungen, die ausgeschlossene Datentypen enthalten, werden nicht installiert. Kunden müssen sich bei CMK abmelden, um diese Daten verwenden zu können.

<!--File data is not passed to plug-ins for performance reasons. You must retrieve the file data in plug-in code using an explicit retrieve call. -->
  
<a name="BKMK_SupportingAttributes"></a>   
## <a name="supporting-attributes"></a>Unterstützen von Attributen  
Wenn ein Dateiattribut einer Entität hinzugefügt wird, werden zur Unterstützung einige zusätzliche Attribute erstellt.
  
### <a name="maxsizeinkb-attribute"></a>MaxSizeInKB-Attribut

 Dieser Wert stellt die maximale Größe (in KB) der Dateidaten dar, die das Attribut enthalten kann. Legen Sie diesen Wert auf die kleinste verwendbare Datengröße fest, die für Ihre bestimmte Anwendung geeignet ist. Siehe die <xref:Microsoft.Xrm.Sdk.Metadata.FileAttributeMetadata.MaxSizeInKB>-Eigenschaft für die zulässige Dateigröße und den Standardwert.
  
<a name="BKMK_RetrievingFiles"></a>

## <a name="retrieve-file-data"></a>Dateidaten abrufen
Um Dateiattributdaten abzurufen, nutzen Sie die folgenden APIs.

Web-API (REST) | .NET-API (SOAP)
------- | -------
 keine  | <xref:Microsoft.Crm.Sdk.Messages.InitializeFileBlocksDownloadRequest>,<br/><xref:Microsoft.Crm.Sdk.Messages.InitializeAttachmentBlocksDownloadRequest>,<br/><xref:Microsoft.Crm.Sdk.Messages.InitializeAnnotationBlocksDownloadRequest>
GET /api/data/v9.1/\<entity-type(id)\>/\<file-attribute-name\>/$value   | <xref:Microsoft.Crm.Sdk.Messages.DownloadBlockRequest>

Dateidatenübertragungen von den Webdienstendpunkten sind auf maximal 16 MB Daten in einem einmaligen Dienstaufruf begrenzt. Dateidaten, die größer sind, müssen in 4 MB- oder kleinere Datenblöcke (-abschnitte) unterteilt werden, wobei jeder Block in einem separaten API-Aufruf empfangen wird, bis alle Dateidaten empfangen wurden. Es liegt in Ihrer Zuständigkeit, die heruntergeladenen Datenblöcke zu verknüpfen, um die Datendatei zu vervollständigen, indem Sie die Datenblöcke in der gleichen Reihenfolge kombinieren, wie sie empfangen wurden.

Nachrichten wie <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest> und <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest> können nicht zum Herunterladen der Dateiattributdaten verwendet werden.

### <a name="example-rest-download-with-chunking"></a>Beispiel: REST-Download mit Segmentierung

**Anforderung**
```http
GET [Organization URI]/api/data/v9.1/accounts(id)/myfileattribute/$value
Headers:
Range: 0-1023/8192
```

**Antwort**
```http
206 Partial Content

Body:
byte[]

Response Headers:
Content-Disposition: attachment; filename="sample.txt"
x-ms-file-name: "sample.txt"
x-ms-file-size: 8192
Location: api/data/v9.1/accounts(id)/myfileattribute?FileContinuationToken
```

Die Segmentierung hängt ab von dem Vorhandensein des `Range`-Headers in der Anforderung. Das Bereichs-Headerwertformat ist: startByte-endByte/total bytes. Die vollständige Datei wird (bis zu 16 MB) in einer Anforderung heruntergeladen, wenn kein `Range`-Header enthalten ist. Für die Segmentierung enthält der `Location`-Antwortheader den abfragefähigen Parameter `FileContinuationToken`. Verwenden Sie den angegebenen Speicherort-Headerwert in der folgenden GET-Anforderung, um den folgenden Block von Daten in der Reihenfolge abzurufen.

### <a name="example-net-c-code-for-download-with-chunking"></a>Beispiel: .NET C#-Code für den Download mit Segmentierung

```csharp
static async Task ChunkedDownloadAsync(
            Uri urlPrefix,
            string customEntitySetName,
            string entityId,
            string entityFileOrAttributeAttributeLogicalName,
            string fileRootPath,
            string downloadFileName,
            string token)
        {
            var url = new Uri(urlPrefix, $"{customEntitySetName}({entityId})/{entityFileOrAttributeAttributeLogicalName}/$value?size=full");
            var increment = 4194304;
            var from = 0;
            var fileSize = 0;
            byte[] downloaded = null;
            do
            {
                using (var request = new HttpRequestMessage(HttpMethod.Get, url))
                {
                    request.Headers.Range = new System.Net.Http.Headers.RangeHeaderValue(from, from + increment - 1);
                    request.Headers.Authorization = new System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", token);
                    using (var response = await Client.SendAsync(request))
                    {
                        if (downloaded == null)
                        {
                            fileSize = int.Parse(response.Headers.GetValues("x-ms-file-size").First());
                            downloaded = new byte[fileSize];
                        }

                        var responseContent = await response.Content.ReadAsByteArrayAsync();
                        responseContent.CopyTo(downloaded, from);
                    }
                }

                from += increment;
            } while (from < fileSize);

            await File.WriteAllBytesAsync(Path.Combine(fileRootPath, downloadFileName), downloaded);
        }
```

<a name="BKMK_UploadingFiles"></a>

## <a name="upload-file-data"></a>Dateidaten hochladen  
Um Dateiattributdaten hochzuladen, nutzen Sie die folgenden APIs.

Web-API (REST) | .NET-API (SOAP)
------- | -------
keine   | <xref:Microsoft.Crm.Sdk.Messages.InitializeFileBlocksUploadRequest>,<br/><xref:Microsoft.Crm.Sdk.Messages.InitializeAttachmentBlocksUploadRequest>,<br/><xref:Microsoft.Crm.Sdk.Messages.InitializeAnnotationBlocksUploadRequest>
PATCH /api/data/v9.1/\<entity-type(id)\>/\<file-attribute-name\>   | <xref:Microsoft.Crm.Sdk.Messages.UploadBlockRequest>
keine   | <xref:Microsoft.Crm.Sdk.Messages.CommitFileBlocksUploadRequest>,<br/><xref:Microsoft.Crm.Sdk.Messages.CommitAttachmentBlocksUploadRequest>,<br/><xref:Microsoft.Crm.Sdk.Messages.CommitAnnotationBlocksUploadRequest>

Wie bereits unter [Dateidaten abrufen](#retrieve-file-data) erwähnt kann das Hochladen einer Datendatei von 16 MB oder weniger in einem einzelnen API-Aufruf erfolgen, während beim Hochladen von mehr als 16 MB Daten erforderlich ist, dass die Dateidaten in Datenblöcke von 4 MB oder weniger unterteilt werden. Nachdem der vollständige Satz von Datenblöcken hochgeladen wurde und eine Commit-Anforderung gesendet wurde, kombiniert der Webdienst die Blöcke automatisch in derselben Reihenfolge, in der die Datenblöcke hochgeladen wurden, zu einer einzigen Datendatei im Azure-Blobspeicher.

Nachrichten wie <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> und <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> können nicht zum Hochladen der Dateiattributdaten verwendet werden.

### <a name="example-rest-upload-with-chunking-first-request"></a>Beispiel: REST-Upload mit Segmentierung (erste Anfrage)

**Anforderung**
```http
PATCH [Organization URI]/api/data/v9.1/accounts(id)/myfileattribute 

Headers: 
x-ms-transfer-mode: chunked 
x-ms-file-name: sample.png
```
**Antwort**
```http
200 OK 

Response Headers: 
x-ms-chunk-size: 4096 
Accept-Ranges: bytes 
Location: api/data/v9.1/accounts(id)/myfileattribute?FileContinuationToken 
```

### <a name="example-rest-upload-with-chunking-next-request"></a>Beispiel: REST-Upload mit Segmentierung (nächste Anfrage)
**Anforderung**
```http
PATCH [Organization URI]/api/data/v9.1/accounts(id)/myfileattribute?FileContinuationToken 

Headers: 
Content-Range: 0-4095/8192 
Content-Type: application/octet-stream
x-ms-file-name: sample.png

Body:
byte[]
```

**Antwort**
```http
206 Partial Content
```

### <a name="example-net-c-code-for-upload-with-chunking"></a>Beispiel: .NET C#-Code für den Upload mit Segmentierung

```csharp
static async Task ChunkedUploadAsync(
            Uri urlPrefix,
            string customEntitySetName,
            string entityId,
            string entityFileOrAttributeAttributeLogicalName,
            string fileRootPath,
            string uploadFileName,
            string accessToken)
        {
            var filePath = Path.Combine(fileRootPath, uploadFileName);
            var fileBytes = await File.ReadAllBytesAsync(filePath);
            var url = new Uri(urlPrefix, $"{customEntitySetName}({entityId})/{entityFileOrAttributeAttributeLogicalName}");

            var chunkSize = 0;
            using (var request = new HttpRequestMessage(HttpMethod.Patch, url))
            {
                request.Headers.Add("x-ms-transfer-mode", "chunked");
                request.Headers.Authorization = new System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", accessToken);
                request.Headers.Add("x-ms-file-name", uploadFileName);
                using (var response = await Client.SendAsync(request))
                {
                    response.EnsureSuccessStatusCode();
                    url = response.Headers.Location;
                    chunkSize = int.Parse(response.Headers.GetValues("x-ms-chunk-size").First());
                }
            }

            for (var offset = 0; offset < fileBytes.Length; offset += chunkSize)
            {
                var count = (offset + chunkSize) > fileBytes.Length ? fileBytes.Length % chunkSize : chunkSize;
                using (var content = new ByteArrayContent(fileBytes, offset, count))
                using (var request = new HttpRequestMessage(HttpMethod.Patch, url))
                {
                    content.Headers.Add("Content-Type", "application/octet-stream");
                    content.Headers.ContentRange = new System.Net.Http.Headers.ContentRangeHeaderValue(offset, offset + (count - 1), fileBytes.Length);
                    request.Headers.Add("x-ms-file-name", uploadFileName);
                    request.Headers.Authorization = new System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", accessToken);
                    request.Content = content;
                    using (var response = await Client.SendAsync(request))
                    {
                        response.EnsureSuccessStatusCode();
                    }
                }
            }
        }
```
 
<a name="BKMK_DeletingFiles"></a>

## <a name="delete-file-data"></a>Dateidaten löschen  
Um die Dateiattributdaten im Speicher zu löschen, verwenden Sie die folgenden APIs.

Web-API (REST) | .NET-API (SOAP)
------- | -------
DELETE /api/data/v9.1/\<entity-type(id)\>/\<attribute-name\> | <xref:Microsoft.Crm.Sdk.Messages.DeleteFileRequest>

### <a name="see-also"></a>Siehe auch
[Bildattribute](image-attributes.md)
