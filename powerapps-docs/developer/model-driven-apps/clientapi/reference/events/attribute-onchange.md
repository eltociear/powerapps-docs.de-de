---
title: Attribut OnChange-Ereignis in modellgesteuerten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 89123cde-7c66-4c7d-94e4-e287285019f8
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="attribute-onchange-event-client-api-reference"></a>OnChange-Attributereignis (Client-API-Referenz)



Das `OnChange`-Ereignis tritt in den folgenden Fällen auf:
- Daten in einem Formularfeld sind geändert und der Fokus ist verloren. Es gibt eine Ausnahme zu diesem Verhalten, die für Zwei-Option Felder (boolesche Felder) gelten, die so formatiert sind, dass Optionsfelder oder Kontrollkästchen verwendet werden. In einem solchen Fall tritt das Ereignis sofort auf.
- Datenänderungen auf dem Server werden abgerufen, um ein Feld zu aktualiseren, wenn das Formular aktualisiert wird, z. B. nachdem ein Datensatz gespeichert wird.
- Die attribute.[fireOnchange](../attributes/fireOnChange.md)-Methode wird verwendet.

Alle Felder unterstützen das `OnChange`-Ereignis. Daten im Feld werden vor und nach dem `OnChange`-Ereignis überprüft.

Das `OnChange`-Ereignis tritt nicht auf, wenn das Feld programmgesteuert mithilfe der attribute.[setValue](../attributes/setValue.md)-Methode geändert wird. Wenn Sie Ereignishandler für das Ereignis `OnChange` nach dem Einstellen des Werts ausführen möchten, müssen Sie die `formContext.data.entity attribute.`[fireOnchange](../attributes/fireOnChange.md)-Methode in Ihrem Code verwenden. 

> [!NOTE]
> Obwohl das **Status**-Feld das `OnChange`-Ereignis unterstützt, ist das Feld schreibgeschützt, sodass das Ereignis nicht nach Benutzerinteraktion auftreten kann. Ein anderes Skript kann dazu führen, dass dieses Ereignis eintritt, indem die [fireOnchange](../attributes/fireOnChange.md)-Methode im Feld verwendet wird.

## <a name="methods-supported-for-this-event"></a>Unterstütze Möglichkeiten für das Ereignis
Es gibt drei Möglichkeiten, die Sie verwenden können, um mithilfe des `OnChange`-Ereignisses für ein Attribut zu arbeiten:
- [addOnChange](../attributes/addOnChange.md)
- [fireOnChange](../attributes/fireOnChange.md)
- [removeOnChange](../attributes/removeOnChange.md)

### <a name="related-topics"></a>Verwandte Themen
[Attribute (Client-API-Referenz)](../attributes.md)
 



