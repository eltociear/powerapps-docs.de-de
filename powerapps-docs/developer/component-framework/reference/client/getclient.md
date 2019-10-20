---
title: getclient | Microsoft-Dokumentation
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
ms.assetid: 4b7c18f8-cd00-4f39-8f88-ed9306d6a055
ms.openlocfilehash: 503d24d97061548132f912351a58fbce68082d18
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345748"
---
# <a name="getclient"></a>getClient

[!INCLUDE [getclient-description](includes/getclient-description.md)]

## <a name="syntax"></a>Syntax

`context.client.getClient()`

## <a name="available-for"></a>Verfügbar für 

Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau) 



## <a name="return-value"></a>Rückgabewert

Typ: `String`

Gibt einen Wert zurück, der angibt, in welchem Client das Skript ausgeführt wird.

|||
|-----|-----|
|Kamera| Webanwendung oder vereinheitlichte Schnittstelle|
|Outlook| Outlook|
|Funk| Mobile App|



### <a name="related-topics"></a>Verwandte Themen

[Client](../client.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../../overview.md)