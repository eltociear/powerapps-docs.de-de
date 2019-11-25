---
title: Ereignisse in Formularen und in Rastern in Modell-angetriebenen Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 9fb38429-55ef-45ce-a3a3-e649e1be89d0
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ab767999bd518bdae7852f7692d62272b809bcd8
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748477"
---
# <a name="events-in-forms-and-grids-in-model-driven-apps"></a>Ereignisse in Formularen und in Rastern in Modell-angetriebenen Apps



Clientseitiger Code wird durch Ereignisse initiiert. In Modell-angetriebenen Apps verknüpfen Sie eine spezielle Funktionen in einer JavaScript-Bibliothek ([Skriptwebressource](../script-jscript-web-resources.md)), das ausgeführt werden soll, wenn ein Ereignis auftritt. Diese Funktion wird als *Ereignishandler* bezeichnet. Jeder Ereignishandler gibt eine Funktion innerhalb einer einzelnen JavaScript-Bibliothek und alle Parameter an, die an die Funktion übergeben werden können.

Sie können Ereignishandler nur einigen Ereignissen mit der Benutzeroberfläche zuordnen. Für Ereignisse, die nicht verfügbar sind für die Zugeordnund durch UI, bietet Client API Methoden, die verwendet werden können, um Ereignishandler zu solchen Ereignissen anzufügen. 

## <a name="add-or-remove-event-handler-function-to-event-using-ui"></a>Hinzufügen oder Entfernen von Ereignishandlerfunktion zum Ereignis mit der Benutzeroberfläche

Verwenden Sie den Abschnitt **Ereignishandler** des Dialogfelds **Formulareigenschaften**, um Ihr Skript einem Ereignis für Formulare und Felder zuzuordnen.

![Ereignishandlerabschnitt in Formulareigenschaften](../media/Form-EventHandlers.png)

## <a name="add-or-remove-event-handler-function-to-event-using-code"></a>Hinzufügen oder Entfernen von Ereignishandlerfunktion zum Ereignis mit Code

Mithilfe der folgenden Methoden, um den Ereignishandler für Erreignisse hinzuzufügen und zu entfernen, die nicht durch die UI zugeordnet werden können:

|Ereignisse |Ereignishandler|
|-------|-------|
|Attribut [OnChange](reference/events/attribute-onchange.md) | [addOnChange](reference/attributes/addonchange.md) und [removeOnChange](reference/attributes/removeOnchange.md)-Methoden|
|Formular [OnLoad](reference/events/form-onload.md)| formContext.ui und [addOnLoad](reference/formcontext-ui/addonload.md) und [removeOnLoad](reference/formcontext-ui/removeonload.md)-Methoden|
|Formulardaten [OnLoad](reference/events/form-data-onload.md)| formContext.data [addOnLoad](reference/formcontext-data/addonload.md) und [removeOnLoad](reference/formcontext-data/removeonload.md)-Methoden|
|Formular [OnSave](reference/events/form-onsave.md)| [addOnSave](reference/formcontext-data-entity/addonsave.md) und [removeOnSave](reference/formcontext-data-entity/removeonsave.md)-Methoden|
|Nachschlagesteuerung [PreSearch](reference/events/presearch.md)| [addPreSearch](reference/controls/addpresearch.md) und [removePreSearch](reference/controls/removepresearch.md)-Methoden|
|kbsearch Steuerelement [OnResultOpened](reference/events/onresultopened.md)|[addOnResultOpened](reference/controls/addOnResultOpened.md) und [removeOnResultOpened](reference/controls/removeOnResultOpened.md)-Methoden|
|kbsearch Steuerelement [OnSelection](reference/events/onselection.md)|[addOnSelection](reference/controls/addOnSelection.md) und [removeOnSelection](reference/controls/removeOnSelection.md)-Methoden|
|kbsearch Steuerelement [PostSearch](reference/events/postsearch.md)|[addOnPostSearch](reference/controls/addOnPostSearch.md) und [removeOnPostSearch](reference/controls/removeOnPostSearch.md)-Methoden|

>[!IMPORTANT]
>Der Ausführungskontext wird automatisch bei der ersten der zu den Funktionen übergeben, die mithilfe des Codes festgelegt wird. Weitere Informationen: [Client API-Ausführungskontext](clientapi-execution-context.md) 

## <a name="form-event-pipeline"></a>Formularereignispipeline
Sie können bis 50 Ereignsihandler für jedes Ereignis definieren. Jeder Ereignsihandler wird in der Reihenfolge ausgeführt, die im Abschnitt **Ereignishandler** auf der Registerkarte **Ereignisse** des Dialogfelds **Formulareigenschaften** angezeigt wird.

Verwenden Sie die [setSharedVariable](reference/executioncontext/setSharedVariable.md) und [getSharedVariable](reference/executioncontext/getSharedVariable.md)-Methoden, um eine gemeinsam genutzte Variable zwischen Erreignishndlern (Funktionen) zu übergeben. Verwenden Sie die Ausführungskontextmethode [getDepth](reference/executioncontext/getDepth.md), um die Sequenz zu ermitteln, in der ein Ereignishandler relativ zu anderen Handlern ausgeführt wird. 

### <a name="related-topics"></a>Verwandte Themen

[Grundlegendes zum Client API-Objektmodell](understand-clientapi-object-model.md)<br/>
[Client-API-Ausführungskontext](clientapi-execution-context.md)<br/>
[Ereignissse (Client-API-Referenz)](reference/events.md)<br/>

