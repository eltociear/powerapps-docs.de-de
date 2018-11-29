---
title: openUrl (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 29cb3685-21aa-42fc-8e84-0074dcc69197
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="openurl-client-api-reference"></a>openUrl (Client-API-Referenz)



[!INCLUDE[./includes/openUrl-description.md](./includes/openUrl-description.md)]

## <a name="syntax"></a>Syntax

`Xrm.Navigation.openUrl(url,openUrlOptions)`

## <a name="parameters"></a>Parameter

|Name |Typ |Erforderlich |Beschreibung |
|---|---|---|---|
|URL|String|Ja|Zu öffnende URL.|
|openUrlOptions|Objekt|No|Optionen zum Öffnen der URL. das Objekt enthält die folgenden Attribute:<br/>- **Höhe**: (Optional) Zahl. Höhe des Fensters zum Anzeigen der resultierenden Seite in Pixeln.<br/>- **Breite**: (Optional) Zahl. Breite des Fensters zum Anzeigen der resultierenden Seite in Pixeln.|

## <a name="remarks"></a>Anmerkungen

Diese Möglichkeit ist besonders nützlich für mobile Clients, um eine URL in einem Browser außerhalb des Shim zu öffnen.

 ### <a name="related-topics"></a>Verwandte Themen

[Xrm.Navigation](../xrm-navigation.md)

