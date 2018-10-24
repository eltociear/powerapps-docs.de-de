---
title: Löschen einer modellgesteuerten App | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine modellgesteuerte App aus Ihrer PowerApps-Umgebung löschen.
keywords: ''
ms.date: 05/31/2018
ms.service: crm-online
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
ms.openlocfilehash: 9512c0b1c13f408b92c0c18f08946ea9afa1e62b
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39687978"
---
# <a name="delete-a-model-driven-app"></a>Löschen einer modellgesteuerten App

Löschen oder entfernen Sie Apps, die in Ihrer Umgebung veraltet sind.

1. Melden Sie sich bei [PowerApps](https://web.powerapps.com/) an.
2. Öffnen Sie [Projektmappen-Explorer](advanced-navigation.md#solution-explorer). 
3. Wählen Sie im Projektmappenfenster unter **Komponenten** die Option **Apps** aus.
4. Wählen Sie die zu löschende App aus, und wählen Sie dann in der Befehlsleiste **Löschen** aus.

    ![Löschen einer App](media/app-module-solution-window.png "Löschen einer App")

5. Wählen Sie in der angezeigten Bestätigungsmeldung die Option **Löschen** aus.

   Die App wird aus Ihrer Umgebung gelöscht.
  
Wenn die Komponente Abhängigkeiten (z.B. Beziehungen) aufweist, müssen Sie die Abhängigkeiten entfernen, bevor Sie die App löschen können. Um die Abhängigkeiten einer App anzuzeigen, wählen Sie erst die App und dann in der Befehlsleiste **Abhängigkeiten anzeigen** aus.

> [!NOTE]
> Wenn Sie die App löschen, wird empfohlen, die zugehörige Siteübersicht ebenfalls zu löschen. Wenn Sie die zugehörige Siteübersicht nicht löschen, zeigt der Designer für die Siteübersicht einen Fehler an, sobald Sie zum ersten Mal versuchen, eine andere App mit dem gleichen Namen zu erstellen. Sie können den Fehler jedoch ignorieren, und er wird beim Versuch, die App erneut zu erstellen, nicht mehr angezeigt.


