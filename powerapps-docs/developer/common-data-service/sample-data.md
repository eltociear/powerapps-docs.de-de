---
title: Hinzufügen und Entfernen von Beispieldaten (Common Data Service) | Microsoft-Dokumentation
description: Installieren oder Deinstallieren von Beispieldaten mithilfe der Web-API oder des Organisationsservice
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5d92cc56311242e19f94f7234ca2c9abf6a3af0e
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748652"
---
# <a name="add-and-remove-sample-data"></a>Hinzufügen und Entfernen von Beispieldaten

Sie können Beispieldaten für eine Organisation mithilfe der Messages `InstallSampleData` und `UninstallSampleData` programmgesteuert installieren und deinstallieren: 

|Web-API-Aktion |Organisationsservice-Klasse|
|--|--|
|<xref href="Microsoft.Dynamics.CRM.InstallSampleData?text=InstallSampleData Action" /> |<xref:Microsoft.Crm.Sdk.Messages.InstallSampleDataRequest>|
|<xref href="Microsoft.Dynamics.CRM.UninstallSampleData?text=UninstallSampleData Action" />|<xref:Microsoft.Crm.Sdk.Messages.UninstallSampleDataRequest>|

## <a name="using-the-web-api"></a>Verwenden der Web-API

Installieren Sie Beispieldaten mithilfe der <xref href="Microsoft.Dynamics.CRM.InstallSampleData?text=InstallSampleData Action" />.

### <a name="request"></a>Anforderung

```http
POST [Organization URI]/api/data/v9.0/InstallSampleData HTTP/1.1
Accept: application/json
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0
```
### <a name="response"></a>Antwort

```http
HTTP/1.1 204 No Content
OData-Version: 4.0
```

Deinstallieren Sie Beispieldaten mithilfe der <xref href="Microsoft.Dynamics.CRM.UninstallSampleData?text=UninstallSampleData Action" />.

### <a name="request"></a>Anforderung

```http
POST [Organization URI]/api/data/v9.0/UninstallSampleData HTTP/1.1
Accept: application/json
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0
```
### <a name="response"></a>Antwort

```http
HTTP/1.1 204 No Content
OData-Version: 4.0
```

## <a name="using-the-organization-service"></a>Verwenden des Organisationsservice

Installieren von Beispieldaten mithilfe der <xref:Microsoft.Crm.Sdk.Messages.InstallSampleDataRequest>

```csharp
var request = new InstallSampleDataRequest();
service.Execute(request);
```

Deinstallieren von Beispieldaten mithilfe der <xref:Microsoft.Crm.Sdk.Messages.UninstallSampleDataRequest>

```csharp
var request = new UninstallSampleDataRequest();
service.Execute(request);
```

> [!NOTE]
> Weder die Klasse <xref:Microsoft.Crm.Sdk.Messages.InstallSampleDataResponse> noch die Klasse <xref:Microsoft.Crm.Sdk.Messages.UninstallSampleDataResponse>, die von diesen Vorgänge zurückgegeben wurden, enthalten zu untersuchenden Eigenschaften.

### <a name="see-also"></a>Siehe auch

[Importieren von Daten](import-data.md)