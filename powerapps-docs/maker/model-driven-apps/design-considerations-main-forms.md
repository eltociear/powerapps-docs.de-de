---
title: Überlegungen zum Entwurf von modellgesteuerten App-Hauptformularen mit PowerApps | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Hauptformulare entwerfen.
ms.custom: ''
ms.date: 06/27/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: a83872f4-9e36-413b-8561-41a1e5ffe5dd
caps.latest.revision: 17
ms.author: matp
manager: kvivek
ms.openlocfilehash: 68915af214b86511f7fba4bbb05ee59f598340b0
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39689770"
---
# <a name="design-considerations-for-model-driven-app-main-forms"></a>Überlegungen zum Entwurf von modellgesteuerten App-Hauptformularen

Hauptformulare sind die primäre Benutzeroberfläche, auf der Benutzer ihre Daten anzeigen und damit interagieren. Hauptformulare bieten eine sehr umfangreiche Palette an Optionen und sind für modellgesteuerte Apps verfügbar, mit Ausnahme von Dynamics 365 für Smartphones.  
  
 Eins der wichtigsten Ziele beim Entwurf von Hauptformularen ist, dass Sie ein solches Formular nur einmal erstellen und dann überall bereitstellen. Dasselbe Hauptformular, das Sie für eine modellgesteuerte App oder die Dynamics 365-Webanwendung für die Kundenbindung entwerfen, wird auch in Dynamics 365 für Outlook und Dynamics 365 für Tablets verwendet. Der Vorteil bei dieser Vorgehensweise ist, dass Sie Änderungen nicht in mehrere Formulare einarbeiten müssen. Es gibt jedoch eine Reihe wichtiger Faktoren, die beim Entwerfen dieser Formulare berücksichtigt werden müssen.  
  
<a name="BKMK_CustomFormsForGroups"></a>   

## <a name="custom-forms-for-different-groups"></a>Benutzerdefinierte Formulare für verschiedene Gruppen  
 Da Sie mehrere Hauptformulare erstellen und jedem Formular unterschiedliche Sicherheitsrollen zuweisen können, können Sie jeder der verschiedenen Gruppen in Ihrer Organisation ein Formular zur Verfügung stellen, das für die jeweilige Nutzung der Anwendung optimiert ist. Sie können sogar für jede Gruppe verschiedene Optionen bereitstellen, sodass die Gruppen aus mehreren Formularen auswählen können. Weitere Informationen: [Steuern des Zugriffs auf Formulare](control-access-forms.md).  
  
 Sie können davon ausgehen, dass Vorgesetzte und Entscheidungsträger Formulare wünschen, die so optimiert sind, dass sie einen schnellen Überblick über wichtige Datenpunkte bieten. Sie möchten eher Diagramme als Listen sehen und werden wahrscheinlich nicht viele Daten eingeben.  
  
 Personen, die direkt mit Kunden interagieren, benötigen Formulare, die direkt auf die am häufigsten ausgeführten Aufgaben zugeschnitten sind. Diese Personen wünschen Formulare, die eine möglichst effiziente Dateneingabe ermöglichen.  
  
 Sie müssen herausfinden, was die verschiedenen Gruppen in Ihrer Organisation wünschen und benötigen. Das ist häufig ein Prozess, der in mehreren Schritten abläuft und bei dem Sie Informationen sammeln, verschiedene Dinge ausprobieren und dann wirklich nutzbare Formulare erstellen. Denken Sie immer daran, dass Ihnen eine Reihe verschiedener Tools zur Verfügung steht und dass nicht alle Vorgänge in einem Formular stattfinden müssen. Verwenden Sie Geschäftsregeln, Workflowprozesse, Dialogfelder und Geschäftsprozessflows zusammen mit Ihren Formularen, um eine Lösung bereitzustellen, die für Ihre Organisation funktioniert.  
  
 Sie müssen den Zeitaufwand in Ihre Überlegungen einbeziehen, der für die Verwaltung von Formularen anfällt. Das Erstellen und Bearbeiten von Formularen ist relativ einfach, aber je mehr Formulare Sie erstellen, desto mehr Formulare müssen Sie auch verwalten.  
  
<a name="BKMK_PresentationDifferences"></a>   
## <a name="presentation-differences"></a>Unterschiede in der Darstellung  
 Obwohl Sie nicht für jede Darstellung mehrere Formulare verwalten müssen, müssen Sie überlegen, wie Unterschiede in der Darstellung im Hauptformular einbezogen werden können. [Darstellungen von Hauptformularen](main-form-presentations.md) beschreibt die unterschiedlichen Arten, in denen ein Hauptformular dargestellt werden kann. Primär müssen folgende Aspekte berücksichtigt werden:  
  
- Dynamics 365 für Tablets unterstützt nicht das Hinzufügen von Bild-, HTML- oder Silverlight-Webressourcen zu Formularen.  
  
-   Das Layout von Dynamics 365 für Tablets-Formularen wird basierend auf dem Hauptformular automatisch generiert. Es gibt keinen speziellen Formular-Editor für Dynamics 365 für Tablets-Formulare. Sie müssen überprüfen, ob die Formulardarstellung für beide Clients gut funktioniert.  
  
-   Nicht unterstützte Skripts, die mit DOM-Elementen in der Webanwendung interagieren, funktionieren in den Dynamics 365 für Tablets-Formularen nicht, da nicht die gleichen DOM-Elemente verfügbar sind.  
  
- Formulare für den Lesebereich in Dynamics 365 für Outlook lassen kein Skripting zu. Die Sichtbarkeit von Formularelementen richtet sich nach den Standardeinstellungen und kann zur Laufzeit nicht mithilfe von Skripts geändert werden.  
  
<a name="BKMK_FormPerformance"></a>   
## <a name="form-performance"></a>Formularleistung  
 Formulare, die langsam geladen werden oder nicht schnell reagieren, wirken sich mit Sicherheit auf die Produktivität und die Akzeptanz der App durch die Benutzer aus. Unter [Optimieren der Formularleistung](optimize-form-performance.md) finden Sie eine Reihe von Empfehlungen, die Sie beim Entwerfen von Formularen berücksichtigen sollten, damit Anpassungen sich nicht negativ auf die Formularleistung auswirken.  
  
### <a name="next-steps"></a>Nächste Schritte 
 [Erstellen und Entwerfen von Formularen](create-design-forms.md)    
 [Erstellen und Bearbeiten von Schnellerfassungsformularen](create-edit-quick-create-forms.md)   

 
