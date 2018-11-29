---
title: getGlobalContext.client (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 89123cde-7c66-4c7d-94e4-e287285019f8
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getglobalcontextclient-client-api-reference"></a>getGlobalContext.client (Client-API-Referenz)



Bietet Zugriff auf die Methoden zum Bestimmen, welcher Client verwendet wird, ob der Client mit dem Server verbunden ist, und welcher Gerätetyp verwendet wird.

`var clientContext = Xrm.Utility.getGlobalContext().client`

Die folgenden Methoden sind für den Clientkontext verfügbar.

## <a name="getclient"></a>getClient

Gibt einen Wert zurück, um anzugeben, in welchem Client das Skript ausgeführt wird. 

### <a name="syntax"></a>Syntax

`clientContext.getClient()`

### <a name="return-value"></a>Rückgabewert

**Typ:**: Zeichenfolge

**Bezeichnung**: Die zurückgegebenen Werte sind:

Value |Client | 
|---|---|
|Web |Webanwendung|
|Web |Einheitliche Oberfläche|
|Outlook |Outlook |
|Mobiltelefonnr. |Mobile App |

## <a name="getclientstate"></a>getClientState

Gibt einen Wert zurück, um den Status des Clients anzugeben.

### <a name="syntax"></a>Syntax

`clientContext.getClientState()`

### <a name="return-value"></a>Rückgabewert

**Typ:**: Zeichenfolge

**Bezeichnung**: Die zurückgegebenen Werte sind:

Value |Client | 
|---|---|
|Online |Webanwendung, Outlook, Mobile App, Einheitliche Schnittstelle|
|Offline |Outlook, Mobile App|

## <a name="getformfactor"></a>getFormFactor

Gibt die Informationen zur Art des Geräts, das der Benutzer verwendet, zurück.

### <a name="syntax"></a>Syntax

`clientContext.getFormFactor()`

### <a name="return-value"></a>Rückgabewert

**Typ:**: Anzahl

**Bezeichnung**: Die zurückgegebenen Werte sind:

Value |Formularfaktor | 
|---|---|
|0 |Unbekannt|
|1 |Desktop|
|2 |Tablet |
|3 |Telefonnummer |

## <a name="isoffline"></a>isOffline

Gibt Informationen, ob der Server online oder offline ist, zurück.

### <a name="syntax"></a>Syntax

`clientContext.isOffline()`

### <a name="return-value"></a>Rückgabewert

**Typ**: Boolesch

**Bezeichnung**: **true**, wenn der Server offline ist, andernfalls **false**.

## <a name="related-topics"></a>Verwandte Themen

[Organisationseinstellungen](organizationSettings.md)

[Benutzereinstellungen](userSettings.md)

[Xrm.Utility.getGlobalContext](../getGlobalContext.md)

