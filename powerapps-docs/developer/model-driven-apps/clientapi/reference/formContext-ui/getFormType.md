---
title: getFormType (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 6c57db71-a76d-404c-852e-9c36a1c549ee
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getformtype-client-api-reference"></a>getFormType (Client-API-Referenz)



[!INCLUDE[./includes/getFormType-description.md](./includes/getFormType-description.md)]

## <a name="syntax"></a>Syntax

`formContext.ui.getFormType();`

## <a name="return-value"></a>Rückgabewert

**Typ:**: Anzahl

**Beschreibung**: Formulartyp. Gibt einen der folgenden Werte zurück 

|Value |Formulartyp |
|---|---|
|0|Nicht definiert|
|1|Erstellen|
|2|Update|
|3|Schreibgeschützt|
|4|Deaktiviert|
|6|Massenbearbeitung|

>[!NOTE]
>Schnellerfassungsformulare geben „1” zurück.


### <a name="related-topics"></a>Verwandte Themen

[formContext.ui](../formContext-ui.md)

[formContext](../../clientapi-form-context.md)

