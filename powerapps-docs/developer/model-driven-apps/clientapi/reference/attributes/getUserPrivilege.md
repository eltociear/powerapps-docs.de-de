---
title: getUserPrivilege (Client-API-Referenz) | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 0a3f0349-af9a-418a-b99d-5085999884eb
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getuserprivilege-client-api-reference"></a>getUserPrivilege (Client-API-Referenz) | MicrosoftDocs



Gibt ein Objekt mit drei Booleschen Eigenschaften zurück, entsprechend den Berechtigungen, die angeben, ob der Benutzer Datenwerte für ein Attribut erstellen, lesen oder aktualisieren kann. Diese Funktion ist für Szenarien vorgesehen, in denen die Sicherheit auf Feldebene die Berechtigungen eines Benutzers für ein bestimmtes Attribut ändert. 

## <a name="attribute-types-supported"></a>Unterstützte Attributtypen

Alle

## <a name="syntax"></a>Syntax

`formContext.getAttribute(arg).getUserPrivilege()`

## <a name="return-value"></a>Rückgabewert

**Typ**: Objekt. 

**Beschreibung**: Das Objekt besitzt drei Boolesche Eigenschaften:
- canRead
- canUpdate
- canCreate

