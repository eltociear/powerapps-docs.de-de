---
title: Optimieren Sie die Formularleistung modellgesteuerter Apps in Power Apps | Microsoft-Dokumentation
description: Erfahren Sie, wie Formularentwürfe vermieden werden, die bewirken, das ein Formular langsam geladen wird
ms.custom: ''
ms.date: 06/27/2018
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
ms.assetid: 59cfa5e6-638a-437f-a462-fddfd26fb07d
caps.latest.revision: 8
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5df20edea9440d407c75b114d24dcb3c0f39306a
ms.sourcegitcommit: 5e6d71967902c463f34a9254f988b9c10e431eb4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "2890645"
---
# <a name="optimize-model-driven-app-form-performance"></a>Optimieren Sie die Leistung modellgesteuerter App-Formulare

Formulare, die langsam geladen werden, können die Produktivität beeinträchtigen und dazu führen, dass Benutzer nicht damit arbeiten wollen. Befolgen Sie diese Empfehlungen, um die Ladegeschwindigkeit Ihrer Formulare zu maximieren. Viele dieser Empfehlungen beziehen sich darauf, wie ein Entwickler Formularskripte für Ihre Organisation implementiert. Besprechen Sie diese Empfehlungen mit Entwicklern, die Formularskripte für Ihre Formulare erstellen.  
  
<a name="BKMK_FormDesign"></a>   
## <a name="form-design"></a>Formulardesign  
 Denken Sie an die Interaktion des Benutzers mit dem Formular und der Datenmenge, die damit angezeigt werden muss.  
  
 **Verwenden Sie nur eine minimale Anzahl von Feldern**  
 Je mehr Felder ein Formular enthält, umso mehr Daten müssen für die Anzeige jedes Datensatzes über das Internet oder Intranet übertragen werden.
 
 **Entwurf für Leistung**  
 Platzieren Sie beim Entwerfen von Formularen und Seiten das Wichtigste ganz oben, um den Zugriff für Ihre Benutzer zu vereinfachen. Verschieben Sie selten verwendete Komponenten auf andere Registerkarten in einem Formular, verwenden Sie rollenbasierte Formulare, anstatt Komponenten anzuzeigen und auszublenden, und stellen Sie sicher, dass verschiedene Workflows über dedizierte Dashboards und Ansichten verfügen. Verwenden Sie Abschnitte, um Ihre Steuerelemente zu organisieren. Dadurch werden Ihre Formulare nicht langsamer.
 
<a name="BKMK_FormScripts"></a>   
## <a name="form-scripts"></a>Formularskripts  
 Wenn Sie Anpassungen mithilfe von Formularskripts anwenden, achten Sie darauf, dass der Entwickler diese Strategien kennt, um die Leistung verbessern zu können.  
  
 **Vermeiden Sie nicht benötigte JavaScript-Webressourcebibliotheken**  
 Je mehr Skripts Sie dem Formular hinzufügen, um so länger dauert ihr Download. Normalerweise werden Skripts in Ihrem Browser zwischengespeichert, wenn sie zum ersten Mal geladen werden, die Leistung beim ersten Anzeigen eines Formulars macht oft erheblichen Eindruck.  
  
 **Vermeiden Sie es, alle Skripts im Onload-Ereignis zu laden**  
 Wenn Sie Code haben, der nur `OnChange`-Ereignisse für Felder oder das `OnSave`-Ereignis unterstützt, stellen Sie sicher, die Skriptbibliothek mit dem Ereignishandler für diese Ereignisse anstelle des `OnLoad`-Ereignisses festzulegen. Dadurch kann das Laden dieser Bibliotheken verschoben werden, was die Leistung beim Laden des Formulars erhöht.  
  
 **Verwenden Sie eingeklappte Registerkarten, um das Laden von Webressourcen zu verschieben**  
 Wenn Webressourcen oder IFRAMES in Abschnitten einer eingeklappten Registerkarte enthalten sind, werden sie nicht geladen. Sie werden geladen, wenn die Registerkarte erweitert wird. Wenn sich der Status der Registerkarte ändert, tritt das `TabStateChange`-Ereignis ein. Jeder Code, der erforderlich ist, um Webressourcen oder IFRAMEs in eingeklappten Registerkarten zu unterstützen, kann Ereignishandler für das **TabStateChange**-Ereignis verwenden und Code reduzieren, der andernfalls im `OnLoad`-Ereignis ausgeführt werden müsste.  
  
 **Richten Sie Standard-Sichtbarkeitsoptionen ein**  
 Vermeiden Sie die Verwendung von Formularskripts im `OnLoad`-Ereignis, die Formularelemente ausblenden. Richten Sie stattdessen die standardmäßigen Sichtbarkeitsoptionen für Formularelementen, die ausgeblendet werden könnten, so ein, dass sie beim Laden des Formulars nicht standardmäßig sichtbar sind. Verwenden Sie dann Skripts im `OnLoad`-Ereignis, um die gewünschten Formularelemente anzuzeigen.  
  
<a name="BKMK_CommandBar"></a>   
## <a name="command-bar-or-ribbon"></a>Menüband oder Befehlsleiste  
 Beachten Sie diese Empfehlungen, wenn Sie die Befehlsleiste oder das Menüband bearbeiten  
  
 **Verwenden Sie nur eine minimale Anzahl von Steuerelementen**  
 Prüfen Sie innerhalb der Befehlsleiste oder des Menübands für das Formular, welche Steuerelemente erforderlich sind, und blenden Sie die aus, die nicht benötigt werden. Jedes angezeigte Steuerelement führt dazu, dass mehr Ressourcen in den Browser heruntergeladen werden müssen.  
  
## <a name="next-steps"></a>Nächste Schritte  
 [Erstellen und Gestalten von Formularen](create-design-forms.md)    
    
 
