---
title: Bild-Attribute (Common Data Service für Apps) | MicrosoftDocs
description: 'Infos zu Bildattributen, die Bilddaten in der Anwendung umfassen, sowie zum Unterstützen von Attributen, das Abrufen von Bilddaten und Hochladen von Bilddaten.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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
---
# <a name="image-attributes"></a>Bildattribute

Entitätsdatensätze, die Bilddaten enthalten, bieten eine einzigartige Umgebung in der Anwendung. Als Entwickler müssen wissen, wie Sie mit Bilddaten arbeiten.  
  
 Nur bestimmte Systementitäten und benutzerdefinierte Entitäten unterstützen Bilder. Informationen dazu, welche Systementitäten Bilder unterstützen, finden Sie unter [Entitätsbilder](/dynamics365/customer-engagement/developer/introduction-entities.md#BKMK_EntityImages).  
  
<a name="BKMK_SupportingAttributes"></a>   
## <a name="supporting-attributes"></a>Unterstützen von Attributen  
 Für Entitäten, die Bildattribute untersützen, ist das <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.SchemaName> des Entitätsbildattributs immer `EntityImage`. Wenn ein Bildattribut einer Entität hinzugefügt wird, werden zur Unterstützung einige zusätzliche Attribute erstellt.  
  
> [!NOTE]
>  Clients, die nicht die aktuellen .NET-Assemblys verwenden, müssen <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy.SdkClientVersion> mit dem Wert „6.0.0.0“ (oder höher) enthalten, um <xref:Microsoft.Xrm.Sdk.Metadata.ImageAttributeMetadata>-Attribute zu erhalten. Weitere Informationen: <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy.SdkClientVersion>.  
  
### <a name="entityimagetimestamp-attribute"></a>EntityImage_Timestamp-Attribut  
 Name des Attributtyps: `BigIntType`  
  
 Der Wert zeigt an, wenn das Bild zuletzt aktualisiert wurde, und wird verwendet, um sicherzustellen, dass die aktuelle Version des Bilds heruntergeladen und auf dem Client zwischengespeichert wird.  
  
### <a name="entityimageurl-attribute"></a>EntityImage_URL-Attribut  
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
  
<a name="BKMK_RetrievingImages"></a>   
## <a name="retrieving-image-data"></a>Abrufen von Bilddaten  
 Wenn Sie  <xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*><xref:Microsoft.Xrm.Sdk.IOrganizationService.Retrieve*> verwenden, ist`EntityImage` nicht in enthalten<xref:Microsoft.Xrm.Sdk.Query.ColumnSet>.`AllColumns` Eigenschaft auf true festgelegt ist. Aufgrund von möglichen Größe der Daten in diesem Attribut müssen Sie es explizit anfordern, wenn es zurückgegeben werden soll.  
  
 Die Binärdaten, die das Bild darstellen, werden nicht mithilfe der veralteten <xref:Microsoft.Crm.Sdk.Messages.ExecuteFetchRequest>-Klasse zurückgegeben. Sie sollten stattdessen <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest> verwenden.  
  
 Mehr Informationen [Beispiel: Festlegen und Abrufen von Entitätsbildern](/dynamics365/customer-engagement/developer/sample-set-retrieve-entity-images)  
  
<a name="BKMK_UploadingImages"></a>   
## <a name="uploading-image-data"></a>Hochladen von Bilddaten  
 Um Bilder zu aktualisieren, legen Sie den Wert von `EntityImage` auf ein `byte[]` fest, das die Inhalte der Datei enthält. Alle Bilder werden in einem 144x144-Pixelquadrat angezeigt. Die Bilder werden zugeschnitten und die Größe wird geändert, um die Größe der Daten zu verringern, bevor sie gespeichert werden.  
  
- Bilder, bei denen mindestens eine Seite größer ist als 144 Pixel, werden zentriert auf 144x144 zugeschnitten.  
  
- Bilder, bei denen beide Seiten kleiner sind als 144 Pixel, werden quadratisch auf ihre kleinste Seite zugeschnitten.  
  
  Die folgende Tabelle enthält zwei Beispiele.  
  
|Vorher|Nach|  
|------------|-----------|  
|![Bild vor Größenanpassung](media/crm-itpro-cust-imagebeforeresize.png "Bild vor Größenanpassung")<br /><br /> 300x428|![Bild nach Größenanpassung](media/crm-itpro-cust-imageafterresize.jpg "Bild nach Größenanpassung")<br /><br /> 144x144|  
|![Zweites Bild-Größenanpassungsbeispiel](media/crm-itpro-cust-imagebeforeresizeexample2.png "Zweites Bild-Größenanpassungsbeispiel")<br /><br /> 91x130|![Zweites Bild-Größenanpassungsbeispiel](media/crm-itpro-cust-imageafterresizeexample2.jpg "Zweites Bild-Größenanpassungsbeispiel")<br /><br /> 91x91|  
  
 Mehr Informationen [Beispiel: Festlegen und Abrufen von Entitätsbildern](/dynamics365/customer-engagement/developer/sample-set-retrieve-entity-images.md)  
  
### <a name="see-also"></a>Siehe auch  
 [Einführung in Entitäten in Dynamics 365](/dynamics365/customer-engagement/developer/introduction-entities)   
 [Einführung in die Entitätsattribute in Dynamics 365](/dynamics365/customer-engagement/developer/introduction-entity-attributes)   
 [Beispiel: Festlegen und Abrufen von Entitätsbildern](/dynamics365/customer-engagement/developer/sample-set-retrieve-entity-images.md)