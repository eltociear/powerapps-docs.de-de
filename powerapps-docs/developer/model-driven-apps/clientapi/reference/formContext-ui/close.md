---
title: close (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 1261a94d-4f5c-446d-8c29-a326e819696b
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="close-client-api-reference"></a>close (Client-API-Referenz)



[!INCLUDE[./includes/close-description.md](./includes/close-description.md)]

## <a name="syntax"></a>Syntax

`formContext.ui.close();`

## <a name="remarks"></a>Anmerkungen

Die HTML-**Window.close**-Methode wird unterdrückt. Um ein Formularfenster zu schließen, müssen Sie diese Methode verwenden. Wenn nicht gespeicherte Änderungen im Formular vorhanden sind, wird der Benutzer gefragt, ob er die Änderungen speichern möchte, bevor das Fenster geschlossen wird.

Bei Microsoft Dynamics 365 für Tabletts imitiert diese Methode das Verhalten der Rückwärtsnavigationsschaltfläche.

### <a name="related-topics"></a>Verwandte Themen

[formContext.ui](../formContext-ui.md)

[formContext](../../clientapi-form-context.md)

