---
title: Anzeigen von Aktivitäten in einer Portalzeitskala | MicrosoftDocs
description: Anweisungen zum Anzeigen aller Aktivitäten in einer Portal-Zeitskala.
author: tapanm-msft
manager: kumarvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 12/12/2019
ms.author: dileeps
ms.reviewer: tapanm
ms.openlocfilehash: 0536890f5665d6b3f6a3cd94aaf6612d06b97293
ms.sourcegitcommit: 212bd841595db0d6f41002f7ff9a1c8eb33a0724
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2019
ms.locfileid: "2914336"
---
# <a name="view-activities-in-a-portal-timeline"></a>Anzeigen von Aktivitäten in einer Portalzeitskala

Während Sie an einem Fall arbeiten oder mit einem Kunden interagieren, können Sie eine Aktivität wie einen Termin, eine E-Mail oder einen Telefonanruf erstellen. Wenn Sie im Support-Portal zur Zeitskala navigieren, finden Sie die Aktivität möglicherweise nicht, da standardmäßig nicht alle Aktivitäten im Portalzeitplan angezeigt werden. 

Anzeigen aller Aktivitäten in einer Portalzeitskala: 

1. Stellen Sie die **CustomerSupport/DisplayAllUserActivitiesOnTimeline** Site-Einstellung auf true.  
    
    > [!NOTE]
    > Wenn **DisplayAllUserActivitiesOnTimeline** Website-Einstellung ist nicht vorhanden, können Sie eine neue Einstellung mit diesem Namen erstellen.

2. Wenn nicht vorhanden, fügen Sie den Aktivitätstyp hinzu, der in den Ansichtsfilter aufgenommen werden soll:  
    1. Gehen Sie zu [**Einstellungen**](https://docs.microsoft.com/power-platform/admin/admin-settings#app-settings) > **Anpassungen** > **System anpassen**.
    2. Wählen Sie **Aktivität** Entität und erweitern Sie die **Ansicht**.
    3. Die **Portalzeitleistenansicht** bearbeiten.
    4. Aktualisieren Sie die **Filterkriterien bearbeiten** und fügen Sie den gewünschten Aktivitätstyp hinzu, wie beispielsweise **Termin, E-Mail oder Telefonanruf**.
    5. **Speichern** und **veröffentlichen** Sie die Anpassungen. 

    > [!IMPORTANT]
    > Das Vorbereiten von Anpassungen nimmt möglicherweise einige Zeit in Anspruch. Wenn Sie eine Mitteilung sehen, dass die Browserseite nicht mehr reagiert, warten Sie darauf, dass diese wieder reagiert und schießen Sie sie nicht.

3. Da dies eine Änderung der Portal-Metadaten ist, [Leeren Sie den serverseitigen Cache](../admin/clear-server-side-cache.md), um sicherzustellen, dass die aktualisierten Daten auf dem Portal angezeigt werden.
