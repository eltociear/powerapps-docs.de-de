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
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34167559"
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

