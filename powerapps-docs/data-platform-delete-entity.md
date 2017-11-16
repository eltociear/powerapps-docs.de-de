---
title: "Löschen einer benutzerdefinierten Entität und Löschen von Daten | Microsoft-Dokumentation"
description: "Löschen Sie eine benutzerdefinierte Entität, und löschen Sie alle Daten."
services: powerapps
documentationcenter: na
author: kfend
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/06/2016
ms.author: kfend
ms.openlocfilehash: 2c0dbc172ee7354bc94670f9bb6993d33fca8f2c
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="delete-a-custom-entity"></a>Eine benutzerdefinierte Entität löschen
Sie können benutzerdefinierte Entitäten, jedoch keine Standardentitäten löschen.

1. Erweitern Sie auf [powerapps.com](https://web.powerapps.com) den Bereich **Common Data Service**, und klicken oder tippen Sie im linken Navigationsbereich auf **Entities** (Entitäten). Sie können in der Liste der Entitäten filtern, indem Sie mindestens ein Zeichen in der Suchleiste über der Liste eingeben.
2. Klicken oder tippen Sie in der Liste der Entitäten auf die Entität, die Sie löschen möchten, und klicken oder tippen Sie anschließend in der rechten oberen Ecke auf die Schaltfläche Mülleimer.
3. Klicken oder tippen Sie in dem erscheinenden Dialogfeld auf **Löschen**, um die Entität zu löschen.

## <a name="notes"></a>Hinweise
* Wenn Sie eine Entität löschen, löschen Sie sowohl ihre Definition als auch alle in der Entität enthaltenen Daten.
* Eine App funktioniert möglicherweise nicht mehr, wenn Sie eine Entität löschen, die in dieser App verwendet wird.
* Wenn Entität A [Nachschlagefelder](data-platform-entity-lookup.md) für Entität B enthält, müssen Sie möglicherweise zunächst Entität B löschen, bevor Sie Entität A löschen können.

