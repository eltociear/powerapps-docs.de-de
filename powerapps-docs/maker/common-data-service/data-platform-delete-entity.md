---
title: Löschen einer benutzerdefinierten Entität | Microsoft-Dokumentation
description: Schrittanleitungen zum Löschen einer benutzerdefinierten Entität und sämtlicher Daten in PowerApps
author: clwesene
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: clwesene
ms.openlocfilehash: 6ef9dc3a1c82fdee9927ffd533ed41386345eaf7
ms.sourcegitcommit: b3b6118790d6b7b4285dbcb5736e55f6e450125c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2018
---
# <a name="delete-a-custom-entity"></a>Eine benutzerdefinierte Entität löschen
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

