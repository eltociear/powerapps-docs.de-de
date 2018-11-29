---
title: setVisible (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 485d9843-5907-49e4-971b-0e86f3bd1eb8
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setvisible-client-api-reference"></a>setVisible (Client-API-Referenz)



[!INCLUDE[./includes/setVisible-description.md](./includes/setVisible-description.md)] 

## <a name="syntax"></a>Syntax

`tabObj.setVisible(bool);`

## <a name="parameter"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|bool|Boolean|Ja|Geben Sie **true** an, um die Registerkarte anzuzeigen; **false**, um die Registerkarte auszublenden.|

## <a name="remarks"></a>Anmerkungen

Eine weitere Methode, eine Registerkarte auszublenden, ist es, alle Abschnitte darin auszublenden. Wenn alle Abschnitte auf einer Registerkarte nicht angezeigt werden, ist die Registerkarte nicht sichtbar.

### <a name="related-topics"></a>Verwandte Themen

[getVisible](getVisible.md)



