---
title: getValue (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 4d025f92-db16-440c-9f82-e40d71e09862
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getvalue-client-api-reference"></a>getValue (Client-API-Referenz)



Ruft den neuesten Wert in einem Steuerelement ab, wenn Benutzer Zeichen in ein bestimmtes Text- oder Zahlenfeld eingeben. Diese Methode hilft Ihnen dabei, interaktive Erfahrungen aufzubauen, indem Daten überprüft und Benutzer gewarnt werden, wenn sie Zeichen in ein Steuerelement eingeben.

Die getValue Methode ist anders als die Attribut [getValue](../attributes/getvalue.md) Methode aufgrund der Steuermethode holt die Werte aus dem Steuerelement wieder, wenn der Anwender im Steuerelement gegensätzlich zum Attribut getValue Methode, dass der Wert wieder geholt wird nachdem der Anwender das Feld speichert. 

## <a name="syntax"></a>Syntax

`formContext.getControl(arg).getValue();`

## <a name="return-value"></a>Rückgabewert

**Typ:**: Zeichenfolge

**Beschreibung**: Der aktuelle Datenwert für ein Steuerelement.

