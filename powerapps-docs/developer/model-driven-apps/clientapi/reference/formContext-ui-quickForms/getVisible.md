---
title: getVisible (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 72c7ec48-1d27-499c-b56c-b7a449a347b8
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getvisible-client-api-reference"></a>getVisible (Client-API-Referenz)



[!INCLUDE[./includes/getVisible-description.md](./includes/getVisible-description.md)]

>[!NOTE]
>Wenn der enthaltende **Abschnitt** oder **Registerkarte** für dieses Steuerelement nicht angezeigt wird, kann diese Methode weiterhin **true** zurückgegeben. So stellen Sie sicher, dass das Steuerelement tatsächlich angezeigt wird; Sie müssen auch die Sichtbarkeit der enthaltenden Elemente überprüfen.

## <a name="syntax"></a>Syntax

`quickViewControl.getVisible();`

## <a name="return-value"></a>Rückgabewert

**Typ:**: Boolesch.

**Beschreibung**: „True“, wenn das Steuerelement sichtbar ist, andernfalls „false“.

### <a name="related-topics"></a>Verwandte Themen

[setVisible](setVisible.md)

[formContext.ui.quickForms](../formContext-ui-quickForms.md)



