---
title: getSubmitMode (Client API-Referenz) | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: a3231438-3821-4dce-b118-d63e6ce85e01
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getsubmitmode-client-api-reference"></a>getSubmitMode (Client-API-Referenz)



Gibt eine Zeichenfolge zurück, die angibt, wann Daten vom Attribut gesendet werden, wenn der Datensatz gespeichert wird. 

## <a name="attribute-types-supported"></a>Unterstützte Attributtypen

Alle

## <a name="syntax"></a>Syntax

`formContext.getAttribute(arg).getSubmitMode()`

## <a name="return-value"></a>Rückgabewert

**Typ:**: Zeichenfolge. 

**Beschreibung**: Gibt einen der folgenden Werte zurück:
- immer
- Niemals
- dirty

### <a name="related-topic"></a>Verwandtes Thema
[setSubmitMode (Client-API-Referenz)](setSubmitMode.md)

