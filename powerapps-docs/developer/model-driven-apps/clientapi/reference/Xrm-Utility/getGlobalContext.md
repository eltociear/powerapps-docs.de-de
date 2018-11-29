---
title: getGlobalContext (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: d87e0614-f365-4ed1-992a-741575bb2b7e
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getglobalcontext-client-api-reference"></a>getGlobalContext (Client-API-Referenz)



[!INCLUDE[./includes/getGlobalContext-description.md](./includes/getGlobalContext-description.md)]
 Die Methode ermöglicht Zugriff auf den globalen Kontext, ohne den Formularkontext durchzulaufen. Sie enthält eine Entsprechung aller Methoden, die dem Objekt **Xrm.Page.context** (jetzt veraltet) zum Abrufen von Informationen zu einem bestimmten Client, Organisation oder Benutzer zur Verfügung stehen.

> [!IMPORTANT]
> Um die Auszeichnung Kontextinformationen in einer eigenständigen HTML-Webressource zu ermöglichen, sollten Sie einen Verweis auf **ClientGlobalContext.js.aspx** Webressource hinzufügen und nutzen dann die **GetGlobalContext** Funktion. Weitere Informationen: [GetGlobalContext Funktion und ClientGlobalContext.js.aspx](../GetGlobalContext-ClientGlobalContext.js.aspx.md) 

## <a name="properties-of-global-context-getglobalcontext"></a>Eigenschaften des globalen Kontexts (getGlobalContext)

Verwenden Sie die folgenden Eigenschaften des globalen Kontext, um Informationen zu Client-, Organisations- oder Benutzereinstellungen zurückzugeben:

|Eigenschaft |Beschreibung | 
|---|---|
|[client](getGlobalContext/client.md) | Gibt Informationen zum Client zurück.|
|[organizationSettings](getGlobalContext/organizationSettings.md) | Gibt Informationen zu aktuellen Organisationseinstellungen zurück.|
|[userSettings](getGlobalContext/userSettings.md) | Gibt Informationen zu aktuellen Benutzereinstellungen zurück.|


## <a name="methods-of-global-context-getglobalcontext"></a>Methoden des globalen Kontexts (getGlobalContext)

|Methode |Beschreibung |
|---|---|
|[GetAdvancedConfigSetting](getGlobalContext/getAdvancedConfigSetting.md) |Gibt Informationen zu erweiterten Konfigurationseinstellungen für die Organisation zurück.|
|[getClientUrl](getGlobalContext/getClientUrl.md) |Gibt die Basis-URL zurück, die verwendet wurde, um auf die Anwendung zuzugreifen.|
|[getCurrentAppName](getGlobalContext/getCurrentAppName.md) |Gibt den Namen der aktuellen Geschäfts-API in modellgetriebenen Apps zurück.|
|[getCurrentAppProperties](getGlobalContext/getCurrentAppProperties.md) |Gibt der Eigenschaft der aktuellen Geschäfts-API in modellgetriebenen Apps zurück.|
|[getCurrentAppUrl](getGlobalContext/getCurrentAppUrl.md) |Gibt die URL der aktuellen Geschäfts-API in modellgetriebenen Apps zurück.|
|[getVersion](getGlobalContext/getVersion.md) |Gibt die Versionennummer der modellgestützten App-Instanz zurück.|
|[isOnPremises](getGlobalContext/isOnPremises.md) |Gibt ein angebenden booleschen Wert zurück, wenn die modellgesteuerte Instanz lokal oder online gehostet wird.|
|[prependOrgName](getGlobalContext/prependOrgName.md) |Setzt den aktuellen eindeutigen Namen der Organisation vor eine Zeichenfolge, normalerweise ein URL-Pfad.|




 



