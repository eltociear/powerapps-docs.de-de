---
title: Löschen einer modellgesteuerten App | MicrosoftDocs
description: 'Erfahren Sie, wie Sie eine modellbasierte App aus Ihrer PowerApps-Umgebung löschen oder entfernen können.'
keywords: ''
ms.date: 05/31/2018
ms.service: crm-online
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: e82e7f64-37ad-41e5-acd7-16309881c6a2
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
caps.latest.revision: 9
topic-status: Drafting
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="delete-a-model-driven-app"></a>Löschen einer modellgesteuerten App

Löschen oder entfernen Sie Apps, die in Ihrer Umgebung nicht mehr erforderlich sind.

1. Melden Sie sich bei [PowerApps](https://web.powerapps.com/) an.
2. Öffnen Sie den [Lösungs-Explorer](advanced-navigation.md#solution-explorer). 
3. Wählen Sie im Lösungsfenster unter **Komponenten** auf **Apps**.
4. Wählen Sie dazu die App aus, die Sie löschen möchten, und wählen Sie auf der Befehlsleiste auf **Löschen** aus.

    ![Löschen einer App](media/app-module-solution-window.png "Löschen einer App")

5. Klicken Sie in der Bestätigungsmeldung, die angezeigt wird, auf **Löschen**.

   Die App wird aus der Umgebung gelöscht.
  
Wenn für die Komponente über Abhängigkeiten verfügt (z. B. Beziehungen), müssen Sie zunächst die Abhängigkeiten entfernen, bevor Sie die App löschen können. Um die Abhängigkeiten einer App anzuzeigen, wählen Sie die App und **Abhängigkeiten anzeigen** in der Befehlsleiste aus.

> [!NOTE]
> Wenn Sie die App löschen, ist es empfehlenswert, die zugeordnete Siteübersicht zu löschen. Wenn Sie die zugehörige Siteübersicht nicht löschen, wird vom Siteübersichtsdesigner eine Fehlermeldung angezeigt, wenn Sie zum ersten Mal versuchen, eine weitere App zu erstellen. Sie können den Fehler allerdings ignorieren. Dann wird der Fehler nicht angezeigt, wenn Sie erneut versuchen, die App zu erstellen.


