---
title: Optimieren der Formularleistung einer modellgesteuerten App in PowerApps | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Formularentwürfe vermeiden, die das Laden eines Formulars verlangsamen.
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
ms.assetid: 59cfa5e6-638a-437f-a462-fddfd26fb07d
caps.latest.revision: 8
ms.author: matp
manager: kvivek
ms.openlocfilehash: c9dd764fe565b59e68411dabf453207c4e01a320
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39682585"
---
# <a name="optimize-model-driven-app-form-performance"></a>Optimieren der Formularleistung einer modellgesteuerten App

Formulare, die langsam geladen werden, können die Produktivität und Benutzerakzeptanz beeinträchtigen. Befolgen Sie die folgenden Empfehlungen, um die benötigte Dauer zum Laden von Formularen zu minimieren. Viele dieser Empfehlungen beziehen sich darauf, wie ein Entwickler Formularskripts für Ihre Organisation implementieren kann. Besprechen Sie diese Empfehlungen mit Entwicklern, die Formularskripts für Ihre Formulare erstellen.  
  
<a name="BKMK_FormDesign"></a>   
## <a name="form-design"></a>Formularentwurf  
 Ziehen Sie die Interaktion des Benutzers mit dem Formular und der Menge der Daten in Betracht, die darin angezeigt werden müssen.  
  
 **Anzahl der Felder auf ein Minimum reduzieren**  
 Je mehr Felder Sie in einem Formular verwalten, desto mehr Daten müssen über das Internet oder das Intranet für die Anzeige der Datensätze übertragen werden.  
  
<a name="BKMK_FormScripts"></a>   
## <a name="form-scripts"></a>Formularskripts  
 Stellen Sie bei Anpassungen mithilfe von Formularskripts sicher, dass der Entwickler diese Strategien zur Leistungsverbesserung kennt.  
  
 **Einbeziehung unnötiger JavaScript-Webressourcenbibliotheken vermeiden**  
 Je mehr Skripts Sie dem Formular hinzufügen, desto mehr Zeit benötigen Sie für den Download. In der Regel werden Skripts in Ihrem Browser zwischengespeichert, nachdem diese zum ersten Mal geladen wurden, allerdings ist die Leistung bei der ersten Anzeige des Formulars oftmals ein wesentlicher Faktor für den Eindruck, den Benutzer bekommen.  
  
 **Laden von sämtlichen Skripts im OnLoad-Ereignis vermeiden**  
 Wenn Sie über Code verfügen, der nur `OnChange`-Ereignisse für Felder oder das `OnSave`-Ereignis unterstützt, legen Sie anstelle des `OnLoad`-Ereignisses die Skriptbibliothek mit dem Ereignishandler für diese Ereignisse fest. So kann das Laden dieser Bibliotheken zurückgestellt und die Ladeleistung von Formularen erhöht werden.  
  
 **Laden von Webressourcen mit reduzierten Registerkarten zurückstellen**  
 Wenn Webressourcen oder IFRAMES in die Abschnitte einer reduzierten Registerkarte eingeschlossen werden, werden sie nicht in dieser geladen. Sie werden nur geladen, wenn die Registerkarte erweitert ist. Wenn sich der Registerkartenstatus ändert, tritt das `TabStateChange`-Ereignis auf. Code, der zur Unterstützung von Webressourcen oder IFRAMEs in reduzierten Registerkarten erforderlich ist, kann Ereignishandler für das Ereignis **TabStateChange** enthalten und Code, der sonst im `OnLoad`-Ereignis auftreten muss, kann reduziert werden.  
  
 **Standardoptionen für die Sichtbarkeit festlegen**  
 Verwenden Sie keine Formularskripts im `OnLoad`-Ereignis, das Formularelemente ausblendet. Legen Sie die Standardoptionen für die Sichtbarkeit stattdessen für Formularelemente fest, die eventuell ausgeblendet sind, sodass sie beim Laden des Formulars standardmäßig nicht sichtbar sind. Verwenden Sie dann Skripts im `OnLoad`-Ereignis, damit die gewünschten Formularelemente angezeigt werden.  
  
<a name="BKMK_CommandBar"></a>   
## <a name="command-bar-or-ribbon"></a>Befehlsleiste oder Menüband  
 Beachten Sie diese Empfehlungen, wenn Sie die Befehlsleiste oder das Menüband bearbeiten.  
  
 **Anzahl der Steuerelemente auf ein Minimum reduzieren**  
 Bewerten Sie in der Befehlsleiste oder im Menüband für das Formular, welche Steuerelemente erforderlich sind, und blenden Sie solche aus, die Sie nicht benötigen. Jedes Steuerelement, das angezeigt wird, erhöht die Anzahl der Ressourcen, die im Browser heruntergeladen werden müssen.  
  
## <a name="next-steps"></a>Nächste Schritte  
 [Erstellen und Entwerfen von Formularen](create-design-forms.md)    
    
 
