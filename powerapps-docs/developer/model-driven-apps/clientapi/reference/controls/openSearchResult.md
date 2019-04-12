---
title: openSearchResult (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 1f9169ce-cba3-4bb6-af20-f86140139cfe
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="opensearchresult-client-api-reference"></a>openSearchResult (Client-API-Referenz)



Öffnet ein Suchergebnis im Suchsteuerelement, indem die Ergebniszahl angegeben wird. 

## <a name="control-types-supported"></a>Unterstützter Steuerelementtypen

Suchsteuerelement für die Wissensdatenbank

## <a name="syntax"></a>Syntax

```
var kbSearchControl = formContext.getControl("<name>");
var openResultStatus = kbSearchControl.openSearchResult(resultNumber, mode);
```

## <a name="parameter"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|resultNumber|Zahl|Ja|Zahlenwert, der die zu öffnende Ergebniszahl spezifiziert. Ergebniszahl beginnt bei 1.|
|Modus|String|No|Geben Sie "Inline" oder "Popout" an. Wenn Sie keinen Wert für das Argument angeben, wird die Standardoption ("Inline") verwendet.<br/><br/>Im Modus "Inline" wird das Ergebnis entweder im Lesebereich des Steuerelements oder einer Registerkarte für den Bereich "Verweise" im Falle eines Bereichs "Verweise" geöffnet. Im Modus "Popout" wird das Ergebnis in einem Popup-Fenster geöffnet.|

## <a name="return-value"></a>Rückgabewert

**Typ**: Boolesch.

**Description**: Status des Öffnens des spezifizierten Suchergebnisses. Gibt 1 zurück, wenn erfolgreich; 0 wenn erfolglos. Die Methode gibt -1 zurück, wenn der spezifizierte resultNumber-Wert nicht anwesend ist oder wenn der spezifizierte Modus-Wert ungültig ist.