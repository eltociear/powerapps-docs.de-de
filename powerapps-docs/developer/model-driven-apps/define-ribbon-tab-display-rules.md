---
title: Definieren von Menübandregisterkarte-Anzeigeregeln (modellgesteuerte Apps) | Microsoft Docs
description: Infos zum Definieren von Menübandregisterkarten-Anzeigeregeln.
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.custom:
- ''
ms.topic: article
ms.assetid: 916f4e82-01a3-2476-c2a4-ff71caa4195c
author: Nkrb
ms.author: nabuthuk
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4e4b7f1cbfc167d999881e396d53436387c2f184
ms.sourcegitcommit: 5701e7a755fade6c3bac5c4a5774fcc74627e168
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "3115634"
---
# <a name="define-ribbon-tab-display-rules"></a>Definieren von Menüband-Registerkartenanzeigenregeln

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/define-ribbon-tab-display-rules -->

Registerkartenanzeigeregeln legen fest, ob eine bestimmte Registerkarte für ein Menüband angezeigt wird oder nicht.  
  
 Anders als andere Menübandelemente wie Gruppen oder bestimmte Steuerelemente, müssen Sie eine Registerkartenanzeigenregel explizit schaffen, damit eine Registerkarte auf dem Menüband angezeigt werden kann. Standardmäßig wird immer andere Menübandelemente angezeigt, es sei denn, eine Anzeigenregel entfernt sie.  
  
 `<TabDisplayRule>`-Elemente erfordern es, dass das `TabCommand`-Attribut einem `<Tab>` `Command`-Attributwert entspricht.  
  
 In `RibbonDiffXml` können Registerkarten für bestimmte Entitäten oder global definiert werden. Wenn die Registerkarte für eine Entität definiert wird, ist der einzige gültige Regeltyp `<EntityRule>`. Da das Festlegen einer Registerkarte im Kontext einer bestimmten Entität bereits die Registerkarte ausschließlich auf diese Entität beschränkt, sind die einzigen gültigen Attribute `AppliesTo` (`PrimaryEntity` oder `SelectedEntity`) und `Context` (`Form`, `HomePageGrid`, `SubGridStandard`, oder `SubGridAssociated`).  
  
 Wenn Sie eine Registerkartenanzeigenregel global in `RibbonDiffXml` für die Anwendungsmenübänder definieren, können Sie sowohl `EntityRule`-Elemente und `<PageRule>`-Elemente anwenden.  
  
### <a name="see-also"></a>Siehe auch  
 [Passen Sie Befehle und das Menüband an](customize-commands-ribbon.md)   
 [Definieren der Skalierung für Menübandelemente](define-scaling-ribbon-elements.md)   
 [Parameter mit dem Menüband an eine URL übergeben](pass-parameters-url-by-using-ribbon.md)