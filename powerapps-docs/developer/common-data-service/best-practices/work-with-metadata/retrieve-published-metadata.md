---
title: Abrufen von veröffentlichten Metadaten | MicrosoftDocs
description: Das Abrufen unveröffentlichter Metadaten führt nicht nur zu einem höheren Aufwand bei der Verarbeitung der Anfrage selbst, sondern kann auch Metadaten zurückgeben, die der Anforderer nicht erwartet.
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 1/15/2019
ms.author: jowells
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5600d4225868dc67096dc3f72ee30b3166ed30d5
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748235"
---
# <a name="retrieve-published-metadata"></a>Abrufen veröffentlichter Metadaten

**Kategorie**: Leistung, Nutzung

**Wirkungspotential**: Hoch

<a name='symptoms'></a>

## <a name="symptoms"></a>Symptome

Das Abrufen nicht veröffentlichter Metadaten kann zu Folgendem führen:

- Langsamere Leistung
- Benutzerverwirrung

<a name='guidance'></a>

## <a name="guidance"></a>Anleitung

Es ist nicht üblich, unveröffentlichte Anpassungen abzurufen, und selten haben Sie die Notwendigkeit, diese Anpassungen abzurufen.

Ein Beispiel dafür, wann Sie unveröffentlichte Anpassungen abrufen müssen, ist, wenn Sie eine Anwendung erstellen möchten, um benutzerdefinierbare Metadaten zu bearbeiten.  Wenn Sie beispielsweise einen benutzerdefinierten Metadaten-Editor erstellen möchten, müssen Sie alle unveröffentlichten Definitionen dieser Elemente abrufen. Wenn ein Entwickler einige Änderungen definiert, sie aber nicht veröffentlicht, muss Ihre Anwendung sie abrufen können, um sicherzustellen, dass der Entwickler die neuesten entwickelten Anpassungen abruft. Andernfalls kann es zum Verlust von unveröffentlichten Anpassungen kommen.

Wenn Sie jedoch keinen Editor erstellen oder keine explizite Notwendigkeit haben, unveröffentlichte Definitionen abzurufen, dann rufen Sie nur die veröffentlichten Definitionen ab. Die folgenden Beispiele zeigen, wie Sie veröffentlichte Anpassungen abrufen können:

### <a name="default-behavior"></a>Standardverhalten

Standardmäßig wird beim Abrufen von Metadaten nur die veröffentlichten Anpassungen angezeigt.

```csharp
public RetrieveAllEntitiesAttributesResponse GetAllEntitiesImplicit(IOrganizationService service)
{
    var request = new RetrieveAllEntitiesRequest();
    request.EntityFilters = EntityFilters.Attributes;

    return service.Execute(request) as RetrieveAllEntitiesAttributesResponse;
}
```

### <a name="explictly-controlling-the-behavior"></a>Genaue Kontrolle des Verhaltens

Explizites Setzen der Eigenschaft `RetrieveAsIfPublished`, um nur veröffentlichte Anpassungen abzurufen.

```csharp
public RetrieveAllEntitiesAttributesResponse GetAllEntitiesExplicit(IOrganizationService service)
{
    var request = new RetrieveAllEntitiesRequest()
    {
        RetrieveAsIfPublished = false
        EntityFilters = EntityFilters.Attributes
    };

    return service.Execute(request) as RetrieveAllEntitiesAttributesResponse;
}
```

<a name='problem'></a>

## <a name="problematic-patterns"></a>Problematische Muster

Die folgenden Operationen ermöglichen das Abrufen nicht veröffentlichter Metadaten über den Parameter `RetrieveAsIfPublished`:

- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAllEntitiesRequest>
- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAllOptionSetsRequest>
- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAttributeRequest>
- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveEntityRequest>
- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveOptionSetRequest>
- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRelationshipRequest>
- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveEntityKeyRequest>

Beispiele für das Abrufen unveröffentlichter Anpassungen sind im Folgenden aufgeführt:

> [!WARNING]
> Diese Szenarien sollten vermieden werden.

```csharp
public RetrieveEntityKeyResponse GetEntityKey(IOrganizationService service, string entityName, string keyName)
{
    var request = new RetrieveEntityKeyRequest()
    {
        EntityLogicalName = entityName,
        LogicalName = keyName,
        RetrieveAsIfPublished = true
    };

    return service.Execute(request) as RetrieveEntityKeyResponse;
}

public RetrieveRelationshipResponse GetRelationship(IOrganizationService service, Guid id)
{
    var request = new RetrieveRelationshipRequest()
    {
        MetadataId = id,
        RetrieveAsIfPublished = true
    };

    return service.Execute(request) as RetrieveRelationshipResponse;
}

public RetrieveEntityAttributesResponse GetEntity(IOrganizationService service, Guid id)
{
    var request = new RetrieveEntityRequest()
    {
        MetadataId = id,
        RetrieveAsIfPublished = true,
        EntityFilters = EntityFilters.Attributes
    };

    return service.Execute(request) as RetrieveEntityAttributesResponse;
}
```

## <a name="web-api-functions"></a>Web-API-Funktionen

Diese Anleitung gilt auch für die folgenden Web-API-Funktionen:

- <xref href="Microsoft.Dynamics.CRM.RetrieveAllEntities?text=RetrieveAllEntities Function" />
- <xref href="Microsoft.Dynamics.CRM.RetrieveEntity?text=RetrieveEntity Function" />

<a name='additional'></a>

## <a name="additional-information"></a>Weitere Informationen

Der Dynamics 365-Dienst ermöglicht den Abruf bestimmter Metadaten, die veröffentlicht oder unveröffentlicht sind. Seit Dynamics CRM 2011 werden veröffentlichte Metadaten standardmäßig aus dem In-Memory-Metadaten-Cache der Anwendung zurückgegeben, es sei denn, der Entwickler weist den Eigenschaftswert `RetrieveAsIfPublished` explizit `true` zu.

Das Abrufen unveröffentlichter Metadaten führt nicht nur zu einem höheren Aufwand bei der Verarbeitung der Anfrage selbst, sondern kann auch Metadaten zurückgeben, die der Anforderer nicht erwartet. Das Abrufen nicht veröffentlichter Metadaten des Optionssets könnte beispielsweise einen Labelwert zurückgeben, der in der Benutzeroberfläche nicht sichtbar ist, was für den Endbenutzer zu Verwirrung führt.

<a name='seealso'></a>

### <a name="see-also"></a>Siehe auch

<xref:Microsoft.Xrm.Sdk.Messages.RetrieveEntityRequest>.<xref href="Microsoft.Xrm.Sdk.Messages.RetrieveEntityRequest.RetrieveAsIfPublished?text=RetrieveAsIfPublished Property" /><br />
[Arbeiten mit Metadaten mithilfe des Organisationsdiensts](../../org-service/work-with-metadata.md)<br />
[Verwenden der Web-API mit Metadaten](../../webapi/use-web-api-metadata.md)<br />
[Veröffentlichen von Anpassungen](/powerapps/developer/model-driven-apps/publish-customizations#retrieving-unpublished-metadata)