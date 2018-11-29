---
title: addOnChange (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
description: 'Erfahren Sie über das Attribut addOnchange-Methode, um eine Funktion zum Aufruf festzulegen, wenn der Attributwert geändert wird.'
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 9f3b2fed-fde5-46e4-8c59-43aa51aa82df
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="addonchange-client-api-reference"></a>addOnChange (Client-API-Referenz)



Legt Funktion zum Aufruf, wenn das Ereignis **OnChange** geschieht, fest.

## <a name="attribute-types-supported"></a>Unterstützte Attributtypen

Alle

## <a name="syntax"></a>Syntax

`formContext.getAttribute(arg).addOnChange(myFunction)`

## <a name="parameters"></a>Parameter

| Parametername| Typ| Beschreibung  |
| --------|-----------| -----|
|myFunction| Funktionsreferenz| Gibt die Funktion an, die für das **OnChange**-Ereignis ausgeführt werden soll. Der [Ausführungskontext](../../clientapi-execution-context.md) wird automatisch bei der ersten der zu den Funktionen übergeben, die mithilfe des Codes festgelegt wird.|


### <a name="related-topics"></a>Verwandte Themen

[removeOnChange](removeOnChange.md)

[Attribut OnChange-Ereignis](../events/attribute-onchange.md)





