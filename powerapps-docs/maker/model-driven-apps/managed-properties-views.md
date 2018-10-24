---
title: Verwaltete Eigenschaften für Ansichten einer modellgesteuerten App bei PowerApps | Microsoft-Dokumentation
description: Informationen zum Festlegen von verwalteten Eigenschaften für eine Ansicht
ms.custom: ''
ms.date: 06/12/2018
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
ms.assetid: a9014576-8fb2-4f28-b8bb-5d2d49d76e12
caps.latest.revision: 25
ms.author: matp
manager: kvivek
ms.openlocfilehash: 9f33212ae81de0418dfc3695d5ae3c8e5acf36da
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39685282"
---
# <a name="model-driven-app-managed-properties-for-views"></a>Verwaltete Eigenschaften für Ansichten einer modellgesteuerten App

<a name="BKMK_ManagedProperties"></a>   
 
 Wenn Sie eine benutzerdefinierte öffentliche Ansicht in PowerApps erstellen, die Sie in eine verwaltete Lösung einbinden möchten, die Sie wiederum verteilen möchten, können Sie für Benutzer, die Ihre Lösung installieren, die Möglichkeiten zur Anpassung der Ansicht begrenzen.  
  
 Standardmäßig ist bei den meisten Ansichten die verwaltete Eigenschaft **Anpassbar** auf TRUE festgelegt, sodass die Ansichten von Benutzern angepasst werden können. Wenn Sie keinen speziellen Grund haben, diese Einstellung zu ändern, empfehlen wir Ihnen, den Benutzern die Anpassung der Ansichten in Ihrer App zu erlauben.  
  
## <a name="set-managed-properties-for-a-view"></a>Festlegen von verwalteten Eigenschaften für eine Ansicht  
  
1.  Öffnen Sie [Projektmappen-Explorer](advanced-navigation.md#solution-explorer), erweitern Sie **Entitäten**, wählen Sie die gewünschte Entität aus, und wählen Sie dann **Ansichten** aus.  
  
2.  Wählen Sie eine benutzerdefinierte öffentliche Ansicht aus.  
  
3.  Wählen Sie in der Menüleiste **Weitere Aktionen** > **Verwaltete Eigenschaften** aus.  

    ![Menü „Verwaltete Eigenschaften“](media/managed-properties.png)
  
4.  Legen Sie die Optionen **Anpassbar** oder **Can Be Deleted** (Kann gelöscht werden) auf **TRUE** oder **FALSE** fest.  

    ![Festlegen von verwalteten Eigenschaften](media/set-managed-properties.png)
  
> [!NOTE]
> Die Einstellung wird erst wirksam, nachdem Sie eine Lösung, die die Ansicht als verwaltete Lösung enthält, exportiert und in einer anderen Umgebung installiert haben.  

## <a name="next-steps"></a>Nächste Schritte
[Grundlegendes zu Ansichten](create-edit-views.md)
