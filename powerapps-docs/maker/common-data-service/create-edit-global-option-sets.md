---
title: Erstellen und Bearbeiten globaler Optionssätze (Auswahllisten) – Übersicht für Common Data Service for Apps | MicrosoftDocs
ms.custom: ''
ms.date: 05/26/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
ms.assetid: f06b8941-8dca-4601-b965-341cfb6fc3b2
caps.latest.revision: 11
ms.author: matp
manager: brycho
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-and-edit-global-option-sets-overview"></a>Erstellen und Bearbeiten globaler Optionssätze – Übersicht 

Ein Optionssatz (Auswahlliste) ist ein Feldtyp, der einer Entität hinzugefügt werden kann. Er definiert einen Satz von Optionen. Wenn ein Optionssatz in einem Formular angezeigt wird, verwendet er ein Dropdownlistensteuerelement. Wenn er in der **Erweiterten Suche** angezeigt wird, verwendet er ein *Auswahllistensteuerelement*. Manchmal werden Optionssätze von den Entwicklern als Auswahllisten bezeichnet.  
  
Sie können einen Optionssatz definieren, um einen Satz von Optionen, die in sich selbst (lokal) definiert sind, oder er kann einen anderswo definierten Optionssatz verwenden (global), der von anderen Optionssatzfeldern verwendet werden kann. 

Globale Optionssätze sind hilfreich, wenn Sie einen Standardsatz von Kategorien haben, die für mehrere Felder gelten. Zwei verschiedene Optionssätze mit denselben Werten zu führen ist schwierig, und wenn sie nicht synchronisiert werden, können Fehler auftreten, besonders wenn Sie Entitätsfelder in einer 1:n-Entitätsbeziehung zuordnen. Weitere Informationen: [Zuordnen von Entitätsfeldern](map-entity-fields.md).

> [!NOTE]
> Wenn Sie jeden Optionssatz als globalen Optionssatz in der Liste der globalen Optionssätze definieren, wächst diese Liste und könnte zum Verwalten schwierig werden. Wenn Sie wissen, dass der Datensatz von Optionen nur an einer Stelle verwendet wird, verwenden Sie einen lokalen Optionssatz.

Sie können zwei Designer verwenden, um globale Optionssätze zu erstellen oder zu bearbeiten:

|Designer| Beschreibung|
|--|--|
|[PowerApps-Portal](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|Gibt eine einfache konzentrierte Erfahrung, aber einige besondere Einstellungen sind nicht verfügbar.<br />Weitere Informationen: [Ein Optionssatz erstellen](custom-picklists.md) |
|Projektmappen-Explorer|Nicht so einfach, aber gibt mehr Flexibilität für weniger allgemeine Anforderungen. <br />Weitere Informationen: [Erstellen und Bearbeiten von globalen Optionssätzen für Common Data Service for Apps mit Projekt-Explorer](create-edit-global-option-sets-solution-explorer.md) |

> [!NOTE]
> Sie können globale Optionssätze in Ihrer Umgebung auch wie folgt erstellen:
> - Importieren Sie eine Lösung, die die Definition der globalen Optionssätze enthält.
> - Ein Entwickler kann ein Programm schreiben, um sie zu erstellen. <br />Weitere Informationen: [Entwicklerdokumentation: Globale Optionssätze anpassen](/dynamics365/customer-engagement/developer/org-service/customize-global-option-sets).

Die Informationen in diesem Thema helfen Ihnen auswählen, welche Designer Sie verwenden können. 

Sie können das [PowerApps-Portal](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) verwenden, um mit globalen Optionssätzen zu arbeiten, es sei denn, Sie müssen eine der folgenden Anforderungen erfüllen:

- Optionen Farben zuweisen
- Die Reihenfolge von Optionen ändern
- Erstellen eines globalen Optionssatzes in einer Lösung, die keine CDS-Standardlösung ist
- Verwaltete Eigenschaften festlegen
- Festlegen der Eigenschaften, die für virtuelle Entitäten verwendet werden
- Abhängigkeiten anzeigen

## <a name="see-also"></a>Siehe auch

[Einen Optionssatz erstellen](custom-picklists.md)<br />
[Erstellen und Bearbeiten von globalen Optionssätzen für Common Data Service for Apps mit Projekt-Explorer](create-edit-global-option-sets-solution-explorer.md)<br />
[Entwicklerdokumentation: Globale Optionssätze anpassen](/dynamics365/customer-engagement/developer/org-service/customize-global-option-sets).
  

 
