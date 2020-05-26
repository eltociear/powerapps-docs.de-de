---
title: Verwenden lokalisierter Bezeichnungen mit Menübändern (modellgestützte Apps) | Microsoft Docs
description: Erfahren Sie mehr über die Verwendung von lokalisierten Beschriftungen in Menübändern.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c4eb7d7bf269541aef706a6e47ae25d7511a1590
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "3275906"
---
# <a name="use-localized-labels-with-ribbons"></a>Verwenden lokalisierten Bezeichnungen in Menübändern

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/use-localized-labels-ribbons -->

Obwohl in Menübandelementen, die Text anzeigen, direkt Text eingegeben werden kann, ist die Verwendung lokalisierter Menübänder für die Definition von Text, der im Menüband angezeigt wird, die bewährte Methode. Das ermöglicht mehrsprachige Funktionen und verbesserte Verwaltung von freigegebenem Text.  
  
## <a name="using-localized-labels"></a>Verwenden von lokalisierten Beschriftungen  

 Das `<RibbonDiffXml>`-Element enthält das `<LocLabels>`-Element. Wie in dem folgenden Beispiel gezeigt können Sie hier angeben, welcher Text in den Menübandbeschriftungen und Tooltips mithilfe des Elements `<Titles>` angezeigt werden soll.  
  
```xml  
<LocLabels>  
 <LocLabel Id="MyISV.account.SendToOtherSystem.LabelText">  
  <Titles>  
   <Title languagecode="1033"  
          description="Send to Other System" />  
  </Titles>  
 </LocLabel>  
 <LocLabel Id="MyISV.account.SendToOtherSystem.ToolTip">  
  <Titles>  
   <Title languagecode="1033"  
          description="Sends this Record to another system" />  
  </Titles>  
 </LocLabel>  
</LocLabels>  
```  
  
 Bei der Definition eines Menübandelements mit angezeigtem Text wird im folgenden Beispiel gezeigt, wie auf die lokalisierte Beschriftung mithilfe der `$LocLabels:`-Direktive verwiesen werden kann.  
  
```xml  
ToolTipTitle="$LocLabels:MyISV.account.SendToOtherSystem.LabelText"  
ToolTipDescription="$LocLabels:MyISV.account.SendToOtherSystem.ToolTip"  
```  
  
## <a name="force-a-line-break-in-a-ribbon-control-label"></a>Erzwingen eines Zeilenumbruchs in einem Steuerelement für die Menübandbeschriftung  

 Wenn Sie ein sehr langes Steuerelement für die Menübeschriftung haben, wird der Text umgebrochen, um in den verfügbaren Platz zu passen. Sie können angeben, wo ein Zeilenumbruch eingefügt werden soll, indem Sie die folgenden Zeichen verwenden: `&#x200b;&#x200b;`.  
  
 Wenn der Beschriftungstexts sehr lang ist und kein Platz für einen Zeilenumbruch bleibt, wird die Breite des Steuerelements erweitert, damit die gesamte Beschriftung angezeigt wird.  
  
### <a name="see-also"></a>Siehe auch  
 [Befehle und das Menüband anpassen](customize-commands-ribbon.md)   
 [Exportieren, Vorbereitung der Bearbeitung und Importieren des Menübands](export-prepare-edit-import-ribbon.md)   
 [Verwenden von lokalisierten Bezeichnungen in Menübändern](use-localized-labels-ribbons.md)   
 [Menübandbefehle definieren](define-ribbon-commands.md)
