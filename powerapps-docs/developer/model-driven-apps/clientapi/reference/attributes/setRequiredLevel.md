---
title: setRequiredLevel (Client-API-Referenz) | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 67a96fc4-4d65-4858-90da-f41eeba0365a
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setrequiredlevel-client-api-reference"></a>setRequiredLevel (Client-API-Referenz)



Legt fest, ob Daten für das Attribut erforderlich oder empfohlen sind, bevor der Datensatz gespeichert werden kann.

> [!IMPORTANT]
> Das Verringern der erforderlichen Ebene eines Attributes kann einen Fehler verursachen, wenn die Seite gespeichert wird. Wenn das Attribut vom Server erforderlich ist, tritt ein Fehler auf, wenn kein Wert für das Attribut vorhanden ist. 

## <a name="attribute-types-supported"></a>Unterstützte Attributtypen

Alle

## <a name="syntax"></a>Syntax

`formContext.getAttribute(arg).setRequiredLevel(requirementLevel)`

## <a name="parameters"></a>Parameter

**Typ:**: Zeichenfolge. 

**Beschreibung**: Hierfür muss einer der folgenden Werte festgelegt werden:
- keine
- erforderlich
- Empfohlen

### <a name="related-topic"></a>Verwandtes Thema
[getRequiredLevel (Client-API-Referenz)](getRequiredLevel.md)


