---
title: Bewährte Lösungsmethoden in Power Apps | Microsoft-Dokumentation
description: Erfahren Sie mehr über bewährte Methoden für die Arbeit mit Lösungen
ms.custom: ''
ms.date: 10/08/2019
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
ms.assetid: ''
caps.latest.revision: 55
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 810fd536da5236f5ac7490505e82e78179ab61da
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2865289"
---
# <a name="best-practices-when-working-with-solutions"></a>Bewährte Methoden für die Arbeit mit Lösungen 
Dieses Thema beschreibt bewährte Methoden für die Arbeit mit Lösungen. 


## <a name="use-a-single-managed-solution-to-manage-a-model-driven-app"></a>Verwenden von nur einer verwalteten Lösung, um eine modellgesteuerte App zu verwalten 
Um die App zu aktualisieren, die in die verwaltete Lösung eingebunden wurde, nutzen Sie Update- oder Patch-Lösungen. Installieren Sie keine anderen verwalteten Lösungen in einer Umgebung mit der gleichen modellgesteuerten App. Weitere Informationen: [Update-Lösungen](import-update-export-solutions.md#update-solutions) und [Verwenden segmentierter Lösungen und Patches, um ausgewählte Entitätsanlagen zu exportieren](use-segmented-solutions-patches-simplify-updates.md) 


## <a name="use-security-roles-to-manage-app-access"></a>Den Zugriff auf die Apps mit Sicherheitsrollen verwalten
Bei modellgesteuerten Apps sollten Sicherheitsrollen zum Steuern des Benutzerzugriffs zugewiesen werden. Weitere Informationen: [Fügen Sie Sicherheitsrollen der App hinzu](../model-driven-apps/share-model-driven-app.md#add-security-roles-to-the-app) 

## <a name="delete-the-managed-solution-to-delete-a-model-driven-app"></a>Löschen der verwalteten Lösung, um eine modellgesteuerte App zu löschen 
Um eine modellgesteuerte App zu löschen, die in der Standardlösung als Bestandteil einer verwalteten Lösung installiert wurde, löschen Sie die verwaltete Lösung. 

Löschen Sie nicht direkt eine App oder App-Siteübersicht aus der Standardumgebung, die als Teil einer verwalteten Lösung installiert wurde. Dies kann Fehler bei Lösungsupgrades oder Lösungsupdates für die Lösung, die verwendet wird, und die App zu installieren, verursachen. Ein Beispiel für das direkte Löschen einer modellgesteuerten App wäre das Öffnen der Standardlösung im Lösungs-Explorer und Wechseln zu **Modellgesteuerte Apps**, Auswählen der App und dann **Löschen**.

### <a name="see-also"></a>Siehe auch
[Überblick über Lösungen](solutions-overview.md)