---
title: Felder löschen in Power Apps | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Felder löschen
ms.custom: ''
ms.date: 06/20/2018
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
ms.assetid: 578ac950-da16-4ec6-a0a4-25f3aaa3b96e
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 224c07600a13b0adf9cedd7592be7f1c2befec90
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2864053"
---
# <a name="delete-fields"></a>Felder löschen

<a name="BKMK_DeletingFields"></a>   
 
 Als Benutzer mit der Sicherheitsrolle "Systemadministrator" können Sie benutzerdefinierte Felder löschen, die nicht Teil einer verwalteten Lösung sind. Wenn Sie Felder löschen, werden alle Daten in den Feldern gelöscht. Die einzige Möglichkeit, Daten aus einem Feld wiederherzustellen, das entfernt wurde, besteht darin, die Datenbank von einem Zeitpunkt wiederherzustellen, bevor das Feld gelöscht wurde.  
  
 Vor dem Löschen einer benutzerdefinierten Entität müssen Sie alle Abhängigkeiten in anderen Lösungskomponenten entfernen. Öffnen Sie das Feld, und verwenden Sie die Schaltfläche **Abhängigkeiten anzeigen** auf der Menüleiste, um eventuelle **Abhängige Komponenten** anzuzeigen. Wenn das Feld beispielsweise in einem Formular oder in einer Ansicht verwendet wird, müssen Sie zunächst Verweise auf das Feld in diesen Lösungskomponenten entfernen.  
  
 Wenn Sie ein Suchfeld löschen, wird die 1: N-Entitätsbeziehung für dieses automatisch gelöscht.  

 ## <a name="next-steps"></a>Nächste Schritte

 [Löschen einer benutzerdefinierten Entität](data-platform-delete-entity.md)
