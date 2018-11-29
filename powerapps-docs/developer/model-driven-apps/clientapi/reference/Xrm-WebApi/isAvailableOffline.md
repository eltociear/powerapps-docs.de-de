---
title: isAvailabelOfffline (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: ea9eacc0-2e31-49f4-a329-dcdf430a5a7e
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="isavailableoffline-client-api-reference"></a>isAvailableOffline (Client-API-Referenz)



[!INCLUDE[./includes/isAvailableOffline-description.md](./includes/isAvailableOffline-description.md)] 

## <a name="syntax"></a>Syntax

`Xrm.WebApi.offline.isAvailableOffline(entityLogicalName);`

## <a name="parameters"></a>Parameter

<table style="width:100%">
<tr>
<th>Name</th>
<th>Typ</th>
<th>Erforderlich</th>
<th>Beschreibung</th>
</tr>
<tr>
<td>entityLogicalName</td>
<td>String</td>
<td>Ja</td>
<td>Logischer Name der Entität. Zum Beispiel: "Konto".</td>
</tr>

</table>

## <a name="return-value"></a>Rückgabewert

**Typ:**: Boolesch.

**Beschreibung**: Wert true festlegen, wenn die Entität im Benutzerprofil vorhanden ist und für die Verwendung im Offlinemodus verfügbar ist; andernfalls false.

[Xrm.WebApi.offline](offline.md)

[Xrm.WebApi](../xrm-webapi.md)




