---
title: Client API-Xrm-Objekt in modellgesteuerten Apps | MicrosoftDocs
description: Das Thema bietet eine Client-API-Referenz für modellgesteuerteApps.
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: conceptual
applies_to:
- Dynamics 365 (online)
ms.assetid: 15272ad9-25d7-499e-9361-a65f789daf20
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 057c63b0f3c22d653bc0988aeaa908dd455908fc
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748476"
---
# <a name="client-api-xrm-object"></a>Client-API-Xrm-Objekt



Das **Xrm**-Objekt ist weltweit verfügbar, um in Ihrem Code zu verwenden, ohne den Ausführungskontext in der Client-API verwenden zu müssen.

## <a name="xrm-object-model"></a>Xrm-Objektmodell 

Die folgende Abbildung stellt das Xrm-Objektmodell dar:

![Xrm-Objektmodell](../media/ClientAPI-XrmModel.png)

Hier sind die Informationen über die Namespaces im Xrm-Objekt:

|Namespace  |Beschreibung  |
---------|---------------
|[Xrm.Device](reference/xrm-device.md)|Bietet Methoden zur Verwendung der nativen Gerätefunktionen von Mobilgeräten.|
|[Xrm.Encoding](reference/xrm-encoding.md)|Stellt Methoden zur Verfügung, um Zeichenfolgen zu dekodieren.|
|[Xrm.Navigation](reference/xrm-navigation.md)|Bietet Methoden zum Navigieren von Formularen und Elementen in modellgesteuerten Anwendungen.|
|[Xrm.Panel](reference/xrm-panel.md)|Bietet eine Methode zum Anzeigen einer Webseite im Seitenbereich des modellgesteuerten App-Formulars.|
|[Xrm.Utility](reference/xrm-utility.md)|Stellt einen Container für nützliche Methoden bereit.|
|[Xrm.WebApi](reference/xrm-webapi.md)|Stellt Methoden zur Verwendung der Web-API bereit, um Datensätze zu erstellen und zu verwalten sowie Web-API-Aktionen und -Funktionen auszuführen.<br/><br/>[Xrm.WebApi.offline](reference/xrm-webapi/offline.md): Stellt Methoden zur Verfügung, mit denen im *Offline*modus Datensätze in den mobilen Clients modellgestützter Apps erstellt und verwaltet werden können.<br/><br/>[Xrm.WebApi.online](reference/xrm-webapi/online.md): Stellt Methoden zur Verwendung der Web-API, um Datensätze zu schaffen und zu verwalten und die Web-API-Aktionen und -Funktionen bei der Verbindung mit dem Server auszuführen, bereit.|

## <a name="client-api-global-context"></a>Globaler Kontext der Client-API

Sie können die **Xrm.Utility**.[getGlobalContext](reference/xrm-utility/getGlobalContext.md)-Methode verwenden, um Informationen für ein Unternehmen, einen Benutzer oder den Kunden zu bestimmten, wo das Skript ohne Durchgang durch den Formularausführungskontext ausgeführt wird. Das ist eine Änderung von früheren Versionen, wobei Sie den Formularkontext zu verwenden hatten, um den globalen Kontext mithilfe von **Xrm.Page.context** abzurufen.

> [!NOTE]
> **Xrm.Page.context** ist [veraltet](/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming#some-client-apis-are-deprecated) in der aktuellen Version, und Sie müssen die neue Methode **Xrm.Utility.**[getGlobalContext](reference/xrm-utility/getGlobalContext.md) in Ihrem Code verwenden, der sich auf Version 9.0 oder höher bezieht. 

Um die Auszeichnung Kontextinformationen in einer eigenständigen HTML-Webressource zu ermöglichen, sollten Sie einen Verweis auf **ClientGlobalContext.js.aspx** Webressource hinzufügen und nutzen dann die **GetGlobalContext** Funktion. Weitere Informationen: [GetGlobalContext Funktion und ClientGlobalContext.js.aspx](reference/GetGlobalContext-ClientGlobalContext.js.aspx.md)

### <a name="related-topics"></a>Verwandte Themen

[Grundlegendes zum Client API-Objektmodell](understand-clientapi-object-model.md)<br/>
[Veraltete Client-APIs](/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming#some-client-apis-are-deprecated)
