---
title: Verwenden der Common Data Service Web API (Common Data Service)| Microsoft Docs
description: Die Common Data Service Web-API implementiert OData v4 und bietet eine Entwicklungserfahrung, die in einer Vielzahl von Programmiersprachen, Plattformen und Geräten verwendet werden kann.
ms.custom: ''
ms.date: 03/31/2020
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 15c4039e-a3ca-4116-ba1d-3ac88cba3ae1
caps.latest.revision: 15
author: JimDaly
ms.author: susikka
ms.reviewer: pehecke
manager: shujoshi
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: bc52a5058b6246534761d5191d9fed49672ba5b1
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "3275806"
---
# <a name="use-the-common-data-service-web-api"></a>Verwenden der Common Data Service-Web-API

Die Web API ist einer von zwei Webservices, mit denen Sie mit Daten und Metadaten in Common Data Service arbeiten können. Der andere ist der [Organisationsservice](../org-service/overview.md).

Die Common Data Service Web API bietet eine Entwicklungserfahrung, die für eine Vielzahl von Programmiersprachen, Plattformen und Geräten genutzt werden kann. Die Web-API implementiert OData (Open Data Protocol), Version 4.0, ein OASIS-Standard zum Erstellen und Nutzen von RESTful APIs über umfassende Datenquellen. Weitere Informationen zu diesem Protokoll finden Sie unter [https://www.odata.org/](https://www.odata.org/). Details zu diesem Standard finden Sie unter [https://www.oasis-open.org/standards#odatav4.0](https://www.oasis-open.org/standards#odatav4.0). 


Da die Web-API auf offenen Standards aufbaut, stellen wir keine Assemblies für eine bestimmte Entwicklererfahrung zur Verfügung. Sie können HTTP-Anforderungen für bestimmte Vorgänge erstellen oder Bibliotheken von Drittanbietern verwenden, um Klassen für beliebige Sprachen oder Plattformen zu erstellen. Eine Liste der Bibliotheken, die OData-Version 4.0 unterstützen, finden Sie unter [https://www.odata.org/libraries/](https://www.odata.org/libraries/).  

## <a name="web-api-and-the-organization-service"></a>Web-API und Organisationsservice

Es ist wichtig zu wissen, dass der Organisationsservice die Plattform definiert. Die Web-API stellt eine RESTful-Programmierungserfahrung bereit. Letztendlich durchlaufen aber alle Datenoperationen den zugrunde liegenden Organisationsservice. Der Organisationsservice definiert die unterstützten Vorgänge als Nachrichten. Jede Nachricht hat einen Namen. Die Namen sind an die Ereignisse gebunden, die im Ereignisframework verwendet werden, um zu bestimmen, welche registrierten Erweiterungen initiiert werden sollten. Weitere Informationen: [Ereignisframework](../event-framework.md)

Mit der Web API können Sie die gleichen Operationen wie mit dem Organisationsservice auszuführen, haben aber eine Umgebung im RESTful-Stil. OData v4 stellt benannte Operationen über *Funktionen* oder *Aktionen* bereit. Die meisten im Organisationsservice verfügbaren Nachrichten werden als entsprechende benannte Funktion oder Aktion verfügbar gemacht. Diese Nachrichten, die CRUD-Vorgängen entsprechen, sind nicht in der Web-API verfügbar, da sie als RESTful-Service Implementierungen mit GET, POST, PATCH und DELETE HTTP-Methoden haben. Innerhalb der Plattform werden die Nachrichten *Abrufen*, *Erstellen*, *Aktualisieren* und *Löschen* aber so wie sie sind aufgerufen, wenn die entsprechenden Vorgänge mit den .NET Framework-Assemblys ausgeführt werden.

## <a name="getting-started"></a>Erste Schritte

Nachdem Sie nun einen Überblick über die Web-API gelesen haben, fahren Sie mit dem Thema [Mit Common Data Service Web-API beginnen](get-started-dynamics-365-web-api-csharp.md) fort, um zu erfahren, wie Sie Ihr erstes C#-Programm in Visual Studio schreiben, das die Web-API verwendet.

Wenn Sie ein JavaScript-Entwickler sind und die Web-API in modellbasierten Apps verwenden möchten, navigieren Sie zu [Clientseitiges JavaScript unter Verwendung der Web-API in modellbasierten Apps](get-started-web-api-client-side-javascript.md).
  
### <a name="related-sections"></a>Verwandte Abschnitte

[Verwenden von Daten mit Code](../work-with-data-cds.md)<br />
[OData - the best way to REST](https://www.odata.org/)<br />
[OData Version 4.0 Part 1: Protocol Plus Errata 02](https://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html)<br />
[OData Version 4.0 Part 2: URL Conventions Plus Errata 02](https://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part2-url-conventions.html)<br />
[OData Version 4.0 Part 3: Common Schema Definition Language (CSDL) Plus Errata 02](https://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part3-csdl.html)
