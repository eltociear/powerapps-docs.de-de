---
title: getPrimaryAttributeValue (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 1a66f93d-a47c-4316-91f1-dcf5d09f9d19
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getprimaryattributevalue-client-api-reference"></a>getPrimaryAttributeValue (Client-API-Referenz)



[!INCLUDE[./includes/getPrimaryAttributeValue-description.md](./includes/getPrimaryAttributeValue-description.md)]

## <a name="syntax"></a>Syntax

`formContext.data.entity.getPrimaryAttributeValue();`

## <a name="return-value"></a>Rückgabewert

**Typ:**: Zeichenfolge.

**Beschreibung**: Der Name der Entität.

## <a name="remarks"></a>Anmerkungen

Jede Entität besitzt ein String-Attribut, das als <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.PrimaryNameAttribute> festgelegt ist. Der Wert für das Attribut wird verwendet, wenn Links zum Datensatz angezeigt werden.



