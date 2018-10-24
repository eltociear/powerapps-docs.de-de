---
title: Löschen von Feldern in PowerApps | Microsoft-Dokumentation
description: Informationen zum Löschen von Feldern
ms.custom: ''
ms.date: 06/20/2018
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
ms.assetid: 578ac950-da16-4ec6-a0a4-25f3aaa3b96e
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: ''
ms.openlocfilehash: 82e560f063f2e46190420b6be5cef4cc55d9ab4f
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39684577"
---
# <a name="delete-fields"></a>Löschen von Feldern

<a name="BKMK_DeletingFields"></a>   
 
 Als Benutzer mit der Sicherheitsrolle „Systemadministrator“ können Sie benutzerdefinierte Felder löschen, die nicht Teil einer verwalteten Lösung sind. Wenn Sie Felder löschen, werden alle in den Feldern gespeicherte Daten gelöscht. Daten aus einem gelöschten Feld können nur durch Wiederherstellen der Datenbank von einem Zeitpunkt vor dem Löschen des Felds wiederhergestellt werden.  
  
 Vor dem Löschen einer benutzerdefinierten Entität müssen alle Abhängigkeiten in anderen Lösungskomponenten entfernt werden. Öffnen Sie hierzu das Feld, und verwenden Sie die Schaltfläche **Abhängigkeiten anzeigen** in der Menüleiste, um alle **abhängigen Komponenten** anzuzeigen. Wenn das Feld beispielsweise in einem Formular oder in einer Ansicht verwendet wird, müssen Sie zunächst Verweise auf das Feld in diesen Lösungskomponenten entfernen.  
  
 Wenn Sie ein Suchfeld löschen, wird die entsprechende 1:n-Entitätsbeziehung automatisch gelöscht.  

 ## <a name="next-steps"></a>Nächste Schritte

 [Löschen von benutzerdefinierten Entitäten](data-platform-delete-entity.md)
