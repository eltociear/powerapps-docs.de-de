---
title: Löschen einer benutzerdefinierten Entität | Microsoft Docs
description: Schrittweise Anweisungen zum Löschen einer benutzerdefinierten Entität und aller Daten in PowerApps
author: lancedMicrosoft
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8b4b9fb7942a7977bf6795ca21985b93c5469d26
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2754913"
---
# <a name="delete-a-custom-entity"></a>Löschen einer benutzerdefinierten Entität
Sie können benutzerdefinierte Entitäten aber keine Standardentitäten löschen.

1. Auf [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), erweitern Sie den Abschnitt **Daten** und klicken oder tippen Sie im linken Navigationsbereich **Entitäten**.

    ![Entitätsdetails](./media/data-platform-cds-create-entity/entitylist.png "Entitätsliste")

2. In der Liste der Entitäten klicken oder tippen Sie auf die zu löschende Entität, und klicken oder tippen Sie auf die Option **Entität löschen** in der Befehlsleiste.

3. Im Dialog, der angezeigt wird, klicken oder tippen Sie auf **Löschen**, um die Entität zu löschen.

>[!NOTE]
>Wenn Sie eine Entität löschen, löschen Sie die Entitätsdefinition und alle Daten, die die Entität enthält. Entitäten und die Daten darin können nicht wiederhergestellt werden, wenn sie gelöscht werden.

>[!NOTE]
>Sie beschädigen möglicherweise eine App oder einen Flow, wenn Sie eine Entität löschen, die in dieser App verwendet wird.

>[!NOTE]
>Wenn Entität A [Suchfelder](data-platform-entity-lookup.md) für Entität B enthält, müssen Sie möglicherweise Entität B löschen, damit Sie Entität A löschen können.

