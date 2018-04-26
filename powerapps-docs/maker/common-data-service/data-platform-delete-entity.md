---
title: Schnellstart für das Löschen einer benutzerdefinierten Entität und das Löschen von Daten | Microsoft-Dokumentation
description: Schnellstart für das Löschen einer benutzerdefinierte Entität und das Löschen aller Daten
documentationcenter: na
author: clwesene
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: cds
ms.date: 3/21/2018
ms.author: clwesene
ms.openlocfilehash: 971016233578c4eadf397d662a0ea74187548635
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="quickstart-delete-a-custom-entity"></a>Schnellstart: Löschen einer benutzerdefinierten Entität
Sie können benutzerdefinierte Entitäten, jedoch keine Standardentitäten löschen.

1. Erweitern Sie unter [powerapps.com](https://web.powerapps.com) den Bereich **Daten**, und klicken oder tippen Sie im linken Navigationsbereich auf **Entitäten**.

    ![Entitätsdetails](./media/data-platform-cds-create-entity/entitylist.png "Entitätsliste")

2. Klicken oder tippen Sie in der Liste der Entitäten auf die Entität, die Sie löschen möchten, und klicken oder tippen Sie anschließend auf die Option **Entität löschen** in der Befehlsleiste.
3. Klicken oder tippen Sie in dem erscheinenden Dialogfeld auf **Löschen**, um die Entität zu löschen.

>[!NOTE]
>Wenn Sie eine Entität löschen, löschen Sie sowohl ihre Definition als auch alle in der Entität enthaltenen Daten. Entitäten und die enthaltenen Daten können nach dem Löschen nicht wiederhergestellt werden.

>[!NOTE]
>Eine App oder ein Flow funktioniert möglicherweise nicht mehr, wenn Sie eine Entität löschen, die in dieser App verwendet wird.

>[!NOTE]
>Wenn Entität A [Nachschlagefelder](data-platform-entity-lookup.md) für Entität B enthält, müssen Sie möglicherweise zunächst Entität B löschen, bevor Sie Entität A löschen können.

