---
title: Verwenden der Standardlösung zum Anpassen mit Power Apps | Microsoft-Dokumentation
description: Erfahren, wie Standardlösungen angepasst werden
ms.custom: ''
ms.date: 02/20/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: f993c4ed-1fc3-4e47-bef1-d38695ddb11a
caps.latest.revision: 57
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1525cdb41cb7e809a54b6389472e5be842a87697
ms.sourcegitcommit: d98dd90a7dda11f434a13a7f8976459856d6142b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/29/2020
ms.locfileid: "3093617"
---
# <a name="use-a-solution-to-customize"></a>Eine Lösung zum Anpassen verwenden
Wir empfehlen Ihnen, eine nicht verwaltete Lösung zu erstellen, um Ihre Anpassungen zu verwalten. Mit einer benutzerdefinierten Lösung können Sie ganz einfach nur die von Ihnen angepassten Lösungskomponenten finden, Ihren Präfix-Lösungsherausgeber konsistent anwenden und Ihre Lösung zur Verteilung in andere Umgebungen exportieren.  

Wenn Sie keine benutzerdefinierte Lösung verwenden, arbeiten Sie mit einer Standardlösung in der nicht verwalteten Ebene. Es gibt jeweils zwei Standardlösungen in jeder Common Data Service Umgebung:  
- Common Data Service Standardlösung. Dies ist eine Basislösung, die den Herstellern als Standardlösung für Ihre Anpassungen in einer Umgebung zur Verfügung steht. Dies Common Data Service Standardlösung ist nützlich, wenn Sie bewerten oder lernen möchten Power Apps.  
- Standardlösung. Dies ist eine besondere Lösung, die alle Komponenten im System enthält. Die Standardlösung ist nützlich, um alle Komponenten und Konfigurationen in Ihrem System zu ermitteln.  

## <a name="why-you-shouldnt-use-the-default-solutions-to-manage-customizations"></a>Warum Sie eine Standardlösung nicht zum Verwalten von Anpassungen verwenden sollten
Es gibt verschiedene Gründe, warum Sie in der Standardlösung keine Apps erstellen und Anpassungen vornehmen sollten:  
- Die Standardlösung enthält alle Komponenten und Anpassungen aus allen Lösungen in der Umgebung. 
- Standardmäßig können alle aktivierten Benutzer in einer Umgebung Apps erstellen und Komponenten in der Common Data Services Standardlösung anpassen. 
- Es ist schwierig, die Anpassungen, die Sie in der Umgebung vorgenommen haben, mit der Standardlösung zu finden oder zu identifizieren. 
- Wenn Sie eine der Standardlösungen verwenden, wird beim Erstellen von Komponenten auch der ihr zugewiesene Standardherausgeber verwendet. Dies kann dazu führen, dass auf einige Komponenten das falsche Herausgeber-Präfix angewendet wird. 
- Die Standardlösung kann nicht exportiert werden. Daher können Sie die Standardlösung nicht an eine andere Umgebung verteilen. 

<!-- Notice that if you have installed or imported other applications or solutions, additional solutions may be available in the solutions list. 

By default,  when you build or customize a model-driven app, you work with the solution called Common Data Services Default Solution. You can open the Common Data Services Default Solution to view and edit the components that are contained in it. To do this, follow these steps.
 
1.  On the left navigation pane select **Solutions**.

2.  In the list of solutions, select **Common Data Services Default Solution**.
  
> [!TIP]
>  If you plan to distribute the applications your make, consider changing the publisher customization prefix. More information: [Solution publisher prefix](change-solution-publisher-prefix.md).  -->
  
<a name="BKMK_PrivacyNotice"></a>   

## <a name="privacy-notices"></a>Datenschutzhinweise  
 [!INCLUDE[cc_privacy_crm_gcc_solution_import](../../includes/cc-privacy-crm-gcc-solution-import.md)]  
  
 [!INCLUDE[cc_privacy_crm_customizations](../../includes/cc-privacy-crm-customizations.md)]  
  
### <a name="see-also"></a>Siehe auch  
[Erstellen einer Lösung](create-solution.md) <br />
[Grundlegendes zu Komponenten modellgestützter Apps](../model-driven-apps/model-driven-app-components.md)


