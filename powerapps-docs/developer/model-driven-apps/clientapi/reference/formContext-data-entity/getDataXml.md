---
title: getDataXml (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: powerapps
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
# <a name="getdataxml-client-api-reference"></a>getDataXml (Client-API-Referenz)



[!INCLUDE[./includes/getDataXml-description.md](./includes/getDataXml-description.md)]

## <a name="syntax"></a>Syntax

`formContext.data.entity.getDataXml();`

## <a name="return-value"></a>Rückgabewert

**Typ:**: Zeichenfolge.

**Beschreibung**: In diesem Beispiel wurden die folgenden drei Felder für einen Firmendatensatz aktualisiert: name, accountnumber, telephone2.

```"<account><name>Contoso</name><accountnumber>55555</accountnumber><telephone2>425 555-1234</telephone2></account>"```

## <a name="remarks"></a>Anmerkungen

Diese Methode funktioniert nicht mit Microsoft Dynamics 365 für Tablets.



