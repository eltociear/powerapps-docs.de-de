---
title: Bildattribute (Common Data Service) | Microsoft-Dokumentation
description: Infos zu Bildattributen, die Bilddaten speichern, sowie zum Unterstützen von Attributen, Abrufen von Bilddaten und Hochladen von Bilddaten.
ms.custom: ''
ms.date: 02/11/2020
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 79cacd85ae1478ed43ee21e499fdfd4b1e606c14
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156182"
---
# <a name="image-attributes"></a>Bildattribute

Bestimmte Systementitäten und alle benutzerdefinierten Entitäten unterstützen Bilder. Entitäten, die Bilder unterstützen, können eine Miniaturansicht und ein primäres Bild in voller Größe enthalten. Die Miniaturansicht kann in der Webanwendung angezeigt werden, wenn die Formulardaten der Entität anzeigt werden. Es können mehrere Bildattribute in einer Entitätsinstanz vorhanden sein, jedoch nur ein primäres Bild. Sie können jedoch das primäre Bild von einem Bild in ein anderes ändern, indem Sie [IsPrimaryImage](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.metadata.imageattributemetadata.isprimaryimage?view=dynamics-general-ce-9#Microsoft_Xrm_Sdk_Metadata_ImageAttributeMetadata_IsPrimaryImage) für dieses Attribut auf `true` festlegen. Jedes Bildattribut in voller Größe kann maximal 30 MB groß sein. Der <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.SchemaName> des Entitätsbildattributs ist `EntityImage`. Weitere Informationen: [Entitätsbilder](/dynamics365/customer-engagement/developer/introduction-entities#entity-images).

Vorschaubilder und Bild-Metadaten werden in Common Data Service gespeichert, die die zum Abrufen des vollständigen Bildes erforderlichen Informationen enthalten. Die Vollbilder werden im Dateispeicher auf dem Azure Blob gespeichert, um den Datenspeicherverbrauch zu reduzieren.

Web-API (REST) | .NET-API (SOAP) 
------- | -------
[ImageAttributeMetadata](/dynamics365/customer-engagement/web-api/imageattributemetadata) | <xref:Microsoft.Xrm.Sdk.Metadata.ImageAttributeMetadata>
IsPrimaryImage, MaxHeight, MaxWidth | [IsPrimaryImage](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.metadata.imageattributemetadata.isprimaryimage?view=dynamics-general-ce-9#Microsoft_Xrm_Sdk_Metadata_ImageAttributeMetadata_IsPrimaryImage), [MaxHeight](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.metadata.imageattributemetadata.maxheight?view=dynamics-general-ce-9), [MaxWidth](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.metadata.imageattributemetadata.maxwidth?view=dynamics-general-ce-9)

Zusätzlich zu den Bildattributen unterstützen benutzerdefinierte Entitäten null oder mehr Dateiattribute, die beliebige Dateidaten enthalten können. Diese Dateiattribute können deutlich mehr Daten enthalten als Bildattribute. Weitere Informationen finden Sie unter [Dateiattribute](file-attributes.md).

<a name="BKMK_SupportingAttributes"></a>   
## <a name="supporting-attributes"></a>Unterstützen von Attributen  
 Wenn ein Bildattribut einer Entität hinzugefügt wird, werden zur Unterstützung einige zusätzliche Attribute erstellt.  
  
### <a name="entityimage_timestamp-attribute"></a>EntityImage_Timestamp-Attribut  
 Name des Attributtyps: `BigIntType`  
  
 Der Wert zeigt an, wenn das Bild zuletzt aktualisiert wurde, und wird verwendet, um sicherzustellen, dass die aktuelle Version des Bilds heruntergeladen und auf dem Client zwischengespeichert wird.  
  
### <a name="entityimage_url-attribute"></a>EntityImage_URL-Attribut  
 Name des Attributtyps: `StringType`  
  
 Eine absolute URL, um das Entitätsbild in einem Client anzuzeigen.  
  
 Die URL setzt sich wie folgt zusammen:  
  
```http  
{0}/image/download.aspx?entity={1}&attribute={2}&id={3}&timestamp={4}
```  
  
- 0 : Die URL der Organisation  
  
- 1 : Der logische Entitätsname  
  
- 2 : Der logische Attributname  
  
- 3 : Der EntityImageId-Wert  
  
- 4 : Der EntityImage_Timestamp-Wert  
  
  Beispiel:   
  `https://myorg.crm.dynamics.com/image/download.aspx?attribute=entityimage&entity=contact&id={ECB6D3DF-4A04-E311-AFE0-00155D9C3020}&timestamp=635120312218444444`  
  
### <a name="entityimageid"></a>EntityImageId  
 Name des Attributtyps: `UniqueIdentifierType`  
  
 Der eindeutige Bezeichner des Bilds  

### <a name="maxsizeinkb-attribute"></a>MaxSizeInKB-Attribut

 Dieser Wert stellt die maximale Größe (in KB) der Bilddaten dar, die das Attribut enthalten kann. Legen Sie diesen Wert auf die kleinste verwendbare Datengröße fest, die für Ihre bestimmte Anwendung geeignet ist. Siehe die <xref:Microsoft.Xrm.Sdk.Metadata.ImageAttributeMetadata.MaxSizeInKB>-Eigenschaft für die zulässige Dateigröße und den Standardwert.

### <a name="canstorefullimage-attribute"></a>CanStoreFullImage-Attribut

 Dieser Wert gibt an, ob ein Bildattribut ein ganzes Bild speichern kann. Siehe die <xref:Microsoft.Xrm.Sdk.Metadata.ImageAttributeMetadata.CanStoreFullImage>-Eigenschaft.

<a name="BKMK_RetrievingImages"></a>   
## <a name="retrieve-image-data"></a>Abrufen von Bilddaten  

Um Miniaturansichtsattributdaten herunterzuladen, nutzen Sie die folgenden APIs.

Web-API (REST) | .NET-API (SOAP)
------- | -------
GET /api/data/v9.1/\<entity-type(id)\>/\<image-attribute-name\>/$value   | <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest> oder <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest>

 > [!NOTE]
> Wenn Sie <xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*> oder <xref:Microsoft.Xrm.Sdk.IOrganizationService.Retrieve*> verwenden, ist `EntityImage` nicht enthalten, wenn die <xref:Microsoft.Xrm.Sdk.Query.ColumnSet>.`AllColumns`- Eigenschaft auf `true` festgelegt ist. Aufgrund von möglichen Größe der Daten in diesem Attribut müssen Sie es explizit anfordern, wenn es zurückgegeben werden soll.

Bilddatenübertragungen von den Webdienstendpunkten sind auf maximal 16 MB Daten in einem einmaligen Dienstaufruf begrenzt. Bilddaten, die größer sind, müssen in 4 MB- oder kleinere Datenblöcke (-abschnitte) unterteilt werden, wobei jeder Block in einem separaten API-Aufruf empfangen wird, bis alle Bilddaten empfangen wurden. Es liegt in Ihrer Zuständigkeit, die heruntergeladenen Datenblöcke zu verknüpfen, um die Bilddatei zu vervollständigen, indem Sie die Datenblöcke in der gleichen Reihenfolge kombinieren, wie sie empfangen wurden.

 Weitere Informationen zur Unterteilung in Abschnitte: [Dateiattribute](file-attributes.md).

Um die Vollbildattributdaten herunterzuladen, nutzen Sie die folgenden APIs.

Web-API (REST) | .NET-API (SOAP)
------- | -------
 keine  | <xref:Microsoft.Crm.Sdk.Messages.InitializeFileBlocksDownloadRequest>
GET /api/data/v9.1/\<entity-type(id)\>/\<image-attribute-name\>/$value?size=full   | <xref:Microsoft.Crm.Sdk.Messages.DownloadBlockRequest>

Beachten Sie, dass in diesem Fall der Bildattributdownload die Dateiattribut-Nachrichtenanforderungen verwendet. 

### <a name="example-rest-thumbnail-download"></a>Beispiel: Download der REST-Miniaturansicht

**Anforderung**
```http
GET [Organization URI]/api/data/v9.1/accounts(b9ccec62-f266-e911-8196-000d3a6de638)/myentityimage/$value

Headers:
Content-Type: application/octet-stream
```

**Antwort**
```http
204 No Content

Body:
byte[]
```

### <a name="example-rest-full-image-download-16mb"></a>Beispiel: Download des REST-Bilds in voller Größe (<=16 MB)

**Anforderung**
```http
GET [Organization URI]/api/data/v9.1/accounts(C0864F1C-0B71-E911-8196-000D3A6D09B3)/myentityimage/$value?size=full

Headers:
Content-Type: application/octet-stream
```
**Antwort**
```http
204 No Content

Body:
byte[]

Response Headers:
x-ms-file-name: "sample.png"
x-ms-file-size: 12345
```

Im oben aufgeführten Beispiel gibt der Abfragezeichenfolgenparameter `size=full` an, das Bild in voller Größe herunterzuladen. Dateiname und -größe werden in den Antwortheadern angegeben.

### <a name="example-rest-full-image-download-16mb"></a>Beispiel: Download des REST-Bilds in voller Größe (>16 MB)

**Anforderung**
```http
GET [Organization URI]/api/data/v9.1/accounts(C0864F1C-0B71-E911-8196-000D3A6D09B3)/myentityimage/$value?size=full

Header:
Range: bytes=0-1023/8192
```
**Antwort**
```http
206 Partial Content

Body:
byte[]

Response Headers:
x-ms-file-name: "sample.png"
x-ms-file-size: 8192
Location: api/data/v9.1/accounts(id)/myentityimage?FileContinuationToken
```
Im oben aufgeführten Beispiel gibt der **Bereich**-Header den ersten segmentierten Download mit 1024 Byte für ein Bild an, das insgesamt 8192 Byte groß ist.
  
<a name="BKMK_UploadingImages"></a>   
## <a name="upload-image-data"></a>Hochladen von Bilddaten  
 Um Bilder zu aktualisieren, legen Sie den Wert des Bildattributs auf ein Byte-Array fest, das die Inhalte der Bilddatei enthält. Miniaturansichten werden zugeschnitten und vom Webdienst auf eine Größe von 144x144 Pixelquadrat geändert, um die Größe der Daten zu verringern, bevor sie gespeichert werden. Die Größenreduzierung unterliegt folgenden Regeln:
  
- Bilder, bei denen mindestens eine Seite größer ist als 144 Pixel, werden zentriert auf 144x144 zugeschnitten.  
  
- Bilder, bei denen beide Seiten kleiner sind als 144 Pixel, werden quadratisch auf ihre kleinste Seite zugeschnitten.  
  
  Die folgende Tabelle enthält zwei Beispiele.  
  
|Vorher|After|  
|------------|-----------|  
|![Bild vor Größenänderung](media/crm-itpro-cust-imagebeforeresize.png "Bild vor Größenänderung")<br /><br /> 300x428|![Bild nach dem Ändern der Größe](media/crm-itpro-cust-imageafterresize.jpg "Bild nach dem Ändern der Größe")<br /><br /> 144x144|  
|![Zweites Beispiel für die Änderung der Bildgröße](media/crm-itpro-cust-imagebeforeresizeexample2.png "Zweites Beispiel für die Änderung der Bildgröße")<br /><br /> 91x130|![Zweites Beispiel für die Änderung der Größe](media/crm-itpro-cust-imageafterresizeexample2.jpg "Zweites Beispiel für die Änderung der Größe")<br /><br /> 91x91|

Um Bilddaten hochzuladen, die kleiner oder gleich 16 MB groß sind, verwenden Sie die folgenden APIs.

Web-API (REST) | .NET-API (SOAP)
------- | -------
PUT oder PATCH /api/data/v9.1/\<entity-type(id)\>/\<image-attribute-name\>   | <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> oder <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest>

Bilddatenübertragungen von den Webdienstendpunkten sind auf maximal 16 MB Daten in einem einmaligen Dienstaufruf begrenzt. Bilddaten, die größer sind, müssen in 4 MB- oder kleinere Datenblöcke (-abschnitte) unterteilt werden, wobei jeder Block in einem separaten API-Aufruf hochgeladen wird, bis alle Bilddaten empfangen wurden. Es liegt in Ihrer Zuständigkeit, die Bilddaten in Blöcke mit einer Größe von maximal 4 MB zu unterteilen und sie in den richtigen Reihenfolge hochzuladen.

 Weitere Informationen zur Unterteilung in Abschnitte: [Dateiattribute](file-attributes.md).

Um Bilddaten hochzuladen, die größer als 16 MB sind, verwenden Sie die folgenden APIs.

Web-API (REST) | .NET-API (SOAP)
------- | -------
keine   | <xref:Microsoft.Crm.Sdk.Messages.InitializeFileBlocksUploadRequest>
PATCH /api/data/v9.1/\<entity-type(id)\>/\<image-attribute-name\>   | <xref:Microsoft.Crm.Sdk.Messages.UploadBlockRequest>
keine   | <xref:Microsoft.Crm.Sdk.Messages.CommitFileBlocksUploadRequest>

Sie können auch die Initialize/Upload/Commit-Blocknachrichtenanfragen für ein Bildattribut <=16 MB Größe (anstelle von Create/Update-Nachrichtenanfragen) verwenden, wenn Sie die Bilddaten segmentieren.

### <a name="example-rest-full-image-upload-16mb"></a>Beispiel: Upload des REST-Bilds in voller Größe (<=16 MB)

**Anforderung**
```http
PUT [Organization URI]/api/data/v9.1/accounts(C0864F1C-0B71-E911-8196-000D3A6D09B3)/myentityimage

Header:
Content-Type: application/octet-stream
x-ms-file-name: sample.png

Body:
byte[]
```
Wenn der Upload abgeschlossen ist, wird eine Miniaturansicht automatisch vom Webdienst erstellt. 

### <a name="example-rest-upload-with-chunking-first-request"></a>Beispiel: REST-Upload mit Segmentierung (erste Anfrage)

**Anforderung**
```http
PATCH [Organization URI]/api/data/v9.1/accounts(id)/myentityimage

Headers:
x-ms-transfer-mode: chunked
x-ms-file-name: sample.png
```

**Antwort**
```http
Response:
200 OK

Response Headers:
x-ms-chunk-size: 4096
Accept-Ranges: bytes 
Location: api/data/v9.1/accounts(id)/myentityimage?FileContinuationToken
```
Im oben aufgeführten Beispiel gibt der `x-ms-transfer-mode: chunked`-Header einen segmentierten Upload an.
 
### <a name="example-rest-upload-with-chunking-next-request"></a>Beispiel: REST-Upload mit Segmentierung (nächste Anfrage)

**Anforderung**
```http
PATCH [Organization URI]/api/data/v9.1/accounts(id)/myentityimage?FileContinuationToken

Headers:
Content-Range: bytes 0-4095/8192
Content-Type: application/octet-stream
x-ms-file-name: sample.png

Body:
byte[]
```

**Antwort**
```http
204 No Content
```
In der oben genannten Anfrage wird der nächste Block von Daten hochgeladen. Wenn alle Bilddaten vom Webdienst empfangen wurden, wird eine Miniaturansicht automatisch vom Webdienst erstellt.

### <a name="see-also"></a>Siehe auch  
[Dateiattribute](file-attributes.md)  
[Einführung in Entitäten in Dynamics 365](/dynamics365/customer-engagement/developer/introduction-entities)   
[Einführung in die Entitätsattribute in Dynamics 365](/dynamics365/customer-engagement/developer/introduction-entity-attributes)   
[Beispiel: Festlegen und Abrufen von Entitätsbildern](/dynamics365/customerengagement/on-premises/developer/sample-set-retrieve-entity-images)
