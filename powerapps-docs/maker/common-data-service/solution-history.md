---
title: Anzeigen des Verlaufs einer Lösung | MicrosoftDocs
description: Erfahren Sie, wie Sie den Verlauf einer Lösung anzeigen
keywords: ''
ms.date: 04/20/2020
ms.service: powerapps
ms.custom: ''
ms.topic: article
ms.assetid: ''
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: ''
topic-status: Drafting
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 75880ec6d29dbb8e9fa9e5f1c2ef4f9721a479ce
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "3276008"
---
# <a name="view-the-history-of-a-solution"></a>Anzeigen des Verlaufs einer Lösung
Sie können Informationen zu Lösungsvorgängen im Bereich **Lösungen** von Power Apps. Ein Vorgang kann ein Lösungsimport, -export oder eine -deinstallation sein. Im Lösungsverlauf werden Informationen wie die Lösungsversion, der Lösungsherausgeber, die Art des Vorgangs, die Start- und Endzeit des Vorgangs sowie der Vorgangsstatus angezeigt.

## <a name="view-solution-history"></a>Anzeige des Lösungsverlaufs
1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.
2.  Klicken Sie im linken Navigationsbereich die Option **Lösungen**, wählen die gewünschte Lösung aus und klicken Sie dann auf der Befehlsleiste die Option **Verlauf anzeigen**. 

    Der Verlauf wird angezeigt. 

    > [!div class="mx-imgBorder"] 
    > ![](media/solution-history.png "Solution history")

Wählen Sie einen Lösungsvorgang aus, um die **Informationsseite** anzuzeigen. Jeder Lösungsverlaufsdatensatz ist schreibgeschützt und enthält den folgenden Bereich **Details**:
-   **Name** Der eindeutige Name der Lösung. 
-   **Startzeit**. Die Zeit, zu der der Vorgang gestartet wurde.
-   **Endzeit**: Die Zeit, zu der der Vorgang geendet ist.
-   **Version**. Die Version der Lösung.
-   **Herausgeber**. Der Name des Herausgebers, der dem Vorgang zugeordnet ist. 
-   **Vorgang**. Der Vorgang, wie Import, Export oder Löschen. 
-   **Teilvorgang**: Bezeichnet die Art des Vorgangs, wie ein neuer Lösungsimport oder ein Update einer vorhandenen Lösung.
-   **Ergebnis**. Das Ergebnis des Vorgangs, zum Beispiel Erfolgreich oder Fehler.

 > [!div class="mx-imgBorder"] 
 > ![](media/solution-history-details.png "Solution history details")

### <a name="view-solution-operation-error-details"></a>Lösungsvorgangs-Fehlerdetails anzeigen 
Unter dem Bereich **Details** befindet sich der Bereich **Weitere Details**, der zusätzliche Informationen zur Lösung enthält sowie darüber, wenn ein Lösungsvorgang einen Fehler aufweist. Die Informationen enthalten: 
- Den **Fehlercode** des Fehlers, der von dem Vorgang zurückgegeben wird. 
- Die **Ausnahmenachricht**, die bei der Diagnose der zugrunde liegenden Ursache für den Betriebsfehler hilfreich sein kann. Einige Fehler, einschließlich Lösungsabhängigkeitsfehler, umfassen unter Umständen auch Links zu Lösungsebenen, um Ihnen die Fehlerdiagnose zu erleichtern. 
- Die **Aktivitäts-ID** kann hilfreich sein, wenn Sie sich an den Microsoft-Kundensupport wenden müssen.

### <a name="see-also"></a>Siehe auch
[Anzeigen von Lösungsebenen](solution-layers.md)  <br />
[Überblick über Lösungen](solutions-overview.md) 


