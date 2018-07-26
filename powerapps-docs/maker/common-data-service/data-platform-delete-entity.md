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
ms.openlocfilehash: b17da30916b06b5b76b16cc6bf9758b988549f6f
ms.sourcegitcommit: 0b051bba173353d7ceda3b60921e7e009eb00709
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2018
ms.locfileid: "39218646"
---
# <a name="delete-a-custom-entity"></a>Eine benutzerdefinierte Entität löschen
Sie können benutzerdefinierte Entitäten, jedoch keine Standardentitäten löschen.

1. Erweitern Sie unter [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) den Bereich **Daten**, und klicken oder tippen Sie im linken Navigationsbereich auf **Entitäten**.

    ![Entitätsdetails](./media/data-platform-cds-create-entity/entitylist.png "Entitätsliste")

2. Klicken oder tippen Sie in der Liste der Entitäten auf die Entität, die Sie löschen möchten, und klicken oder tippen Sie anschließend auf die Option **Entität löschen** in der Befehlsleiste.

3. Klicken oder tippen Sie in dem erscheinenden Dialogfeld auf **Löschen**, um die Entität zu löschen.

>[!NOTE]
>Wenn Sie eine Entität löschen, löschen Sie sowohl ihre Definition als auch alle in der Entität enthaltenen Daten. Entitäten und die enthaltenen Daten können nach dem Löschen nicht wiederhergestellt werden.

>[!NOTE]
>Eine App oder ein Flow funktioniert möglicherweise nicht mehr, wenn Sie eine Entität löschen, die in dieser App verwendet wird.

>[!NOTE]
>Wenn Entität A [Nachschlagefelder](data-platform-entity-lookup.md) für Entität B enthält, müssen Sie möglicherweise zunächst Entität B löschen, bevor Sie Entität A löschen können.

