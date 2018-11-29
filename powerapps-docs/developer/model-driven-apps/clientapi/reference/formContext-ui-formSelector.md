---
title: form Context.ui.FormSelector (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
description: Erfahren Sie mehr über das Verwenden modellgestützten Apps mithilfe von Client-API.
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 32e8d1d0-4093-4588-a517-2930eec34dce
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="formcontextuiformselector-client-api-reference"></a>formContext.ui.FormSelector (Client-API-Referenz)



Die Eigenschaft **formContext.ui.formSelector** können Sie verwenden, um mit Formularelementen zu arbeiten, bei denen Element ein Formular repräsentiert, das für einen Benutzer verfügbar ist, da es einer Sicherheitsrolle zugeordnet ist, der auch der Benutzer zugeordnet ist. Häufig ist nur ein Formular vorhanden. Wenn mehr als ein Formular verfügbar ist, können Methoden für ein Formularelement verwendet werden, um auf das Formular zu ändern, das der Benutzer anzeigt.

Formular-Elemente sind durch folgende Aktionen zur verfügbar:

- **formselector.items** Sammlung: Eine Sammlung von Formularelementen, die für den aktuellen Benutzer verfügbar sind. Nur Formulare, die einer Verknüpfung mit einer der Sicherheitsrollen des Benutzers gemeinsam haben, sind in dieser Sammlung verfügbar. Beispiel:
 
    `formItem = formContext.ui.formSelector.items.get(arg);`

    Siehe [Sammlungen](collections.md) für Informationen zu den Sammlungsmethoden.
 
    >[!NOTE]
    >Diese Sammlung ist nicht für mobile Dynamics 365-Clients (Tablets und Smartphones) verfügbar.

- **formselector.getCurrentItem** Methode: Gibt einen Verweis auf das Formular zurück, das zurzeit angezeigt wird. Wenn nur ein Formular verfügbar ist, gibt diese Methode **null** zurück. Beispiel:
 
    `formItem = formContext.ui.formSelector.getCurrentItem();`       

## <a name="form-item-methods"></a>Formular-Element-Methoden

Nachdem Sie ein Formularelement mithilfe einer der oben beschriebenen Methoden erhalten haben, können Sie die folgenden Möglichkeiten verwenden, um mit dem Formularelement zu arbeiten. 

|Name|Beschreibung|
|--|--|
|[getId](formcontext-ui-formselector/getId.md)|[!INCLUDE[formcontext-ui-formselector/includes/getId-description.md](formcontext-ui-formselector/includes/getId-description.md)]|
|[getLabel](formcontext-ui-formselector/getLabel.md)|[!INCLUDE[formcontext-ui-formselector/includes/getLabel-description.md](formcontext-ui-formselector/includes/getLabel-description.md)]|
|[navigate](formcontext-ui-formselector/navigate.md)|[!INCLUDE[formcontext-ui-formselector/includes/navigate-description.md](formcontext-ui-formselector/includes/navigate-description.md)]|


