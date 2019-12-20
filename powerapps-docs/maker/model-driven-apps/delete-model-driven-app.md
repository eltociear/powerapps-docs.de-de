---
title: Löschen einer modellgesteuerten App | MicrosoftDocs
description: Weitere Information, wie Sie eine modellgesteuerte App aus Ihrer Power Apps-Umgebung löschen oder entfernen können.
keywords: ''
ms.date: 10/08/2019
ms.service: powerapps
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: e82e7f64-37ad-41e5-acd7-16309881c6a2
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 9
topic-status: Drafting
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e8f7d58f7c5cf40f6b582bc5be7970211334d271
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "2874826"
---
# <a name="delete-a-model-driven-app"></a>Löschen einer modellgesteuerten App
Löschen oder entfernen Sie Apps, die in Ihrer Umgebung nicht mehr erforderlich sind.

> [!IMPORTANT]
> Wenn die modellgesteuerte App in der Standardlösung als Bestandteil einer verwalteten Lösung installiert wurde, sehen Sie unter [Löschen einer modellgesteuerten App, die als Teil einer verwalteten Lösung installiert war](#delete-a-model-driven-app-that-was-installed-as-part-of-a-managed-solution), nach.

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.
2. Wählen Sie **Apps** in der linken Navigation aus. 
3. Wählen Sie dazu die App aus, die Sie löschen möchten, und wählen Sie auf der Befehlsleiste auf **Löschen** aus.
4. Klicken Sie in der Bestätigungsmeldung, die angezeigt wird, auf **Löschen**.

   Die App wird aus der Umgebung gelöscht.
  
Wenn für die Komponente über Abhängigkeiten verfügt (z. B. Beziehungen), müssen Sie zunächst die Abhängigkeiten entfernen, bevor Sie die App löschen können. Um die Abhängigkeiten einer App anzuzeigen, wählen Sie die App und dann **Abhängigkeiten anzeigen** in der Befehlsleiste aus.

> [!NOTE]
> Wenn Sie die App löschen, ist es empfehlenswert, die zugeordnete Siteübersicht zu löschen. Wenn Sie die zugehörige Siteübersicht nicht löschen, wird vom Siteübersichtsdesigner eine Fehlermeldung angezeigt, wenn Sie zum ersten Mal versuchen, eine weitere App zu erstellen. Sie können den Fehler allerdings ignorieren. Dann wird der Fehler nicht angezeigt, wenn Sie erneut versuchen, die App zu erstellen.

## <a name="delete-a-model-driven-app-that-was-installed-as-part-of-a-managed-solution"></a>Löschen einer modellgesteuerten App, die als Bestandteil einer verwalteten Lösung installiert worden war
Um eine modellgesteuerte App zu löschen, die in der Umgebung als Bestandteil einer verwalteten Lösung installiert wurde, löschen Sie die verwaltete Lösung. 

### <a name="delete-a-managed-solution"></a>Löschen einer verwalteten Lösung 
Alle Komponenten einer verwalteten Lösung werden durch die Löschung der Lösung gelöscht.
1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an. 
2.  Wählen Sie im linken Navigationsbereich **Lösungen** aus.
3.  Wählen Sie in der Liste **Lösungen** die verwaltete Lösung aus, die Sie löschen möchten, und klicken Sie dann auf der Symbolleiste auf **Löschen**. 

