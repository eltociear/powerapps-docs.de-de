---
title: showProgressIndicator (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 36e17a06-e381-4efd-b3a6-62391377b613
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="showprogressindicator-client-api-reference"></a>showProgressIndicator (Client-API-Referenz)



[!INCLUDE[./includes/showProgressIndicator-description.md](./includes/showProgressIndicator-description.md)]

Jeder Anruf zu dieser Methode aktualisiert die angezeigte Meldung im vorhandenen Statusdialogfeld mit der Meldung, die im aktuellen Methodenaufruf angegeben ist.

>[!WARNING]
>Der Statusdialog sperrt die Benutzeroberfläche, bis er mithilfe der [closeProgressIndicator](closeProgressIndicator.md)-Methode geschlossen wird. Deshalb diese Methode mit Vorsicht verwenden.

## <a name="syntax"></a>Syntax

`Xrm.Utility.showProgressIndicator(message)`

## <a name="parameters"></a>Parameter 

|Name |Typ |Erforderlich |Beschreibung |
|---|---|---|---|
|Meldung|String|Ja|Die im Fehler-Dialogfeld anzuzeigende Fortschritt-Nachricht.|



### <a name="related-topics"></a>Verwandte Themen

[closeProgressIndicator](closeProgressIndicator.md)

[Xrm.Utility](../xrm-utility.md)  



