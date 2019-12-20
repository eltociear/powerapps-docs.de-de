---
title: Anzeigen des Verlaufs einer Lösung | MicrosoftDocs
description: Erfahren Sie, wie Sie den Verlauf einer Lösung anzeigen
keywords: ''
ms.date: 05/19/2019
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
ms.openlocfilehash: 813a31b3b9d56dfb6742dc138ec947829613cf89
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2869938"
---
# <a name="view-the-history-of-a-solution"></a>Anzeigen des Verlaufs einer Lösung
Sie können Informationen zu Lösungsvorgängen im Bereich **Lösungen** einer modellgesteuerten App anzeigen. Ein Vorgang kann ein Lösungsimport, -export oder -löschung sein. Im Lösungsverlauf werden Informationen wie die Lösungsversion, der Lösungsherausgeber, die Art des Vorgangs, die Start- und Endzeit des Vorgangs sowie der Vorgangsstatus angezeigt.

> [!div class="mx-imgBorder"] 
> ![](media/solutions-history-custom-view.png "Solutions history custom view")

## <a name="view-solution-history"></a>Anzeige des Lösungsverlaufs
1. Wählen Sie **Einstellungen** und dann **Lösungsverlauf** aus.

     > [!div class="mx-imgBorder"] 
     > ![](media/solution-history-sitemap.png "Solution History area")

     > [!NOTE]
     > Um zum Bereich **Einstellungen** aus einer Power Apps vereinheitlichten, schnittstellenmodellgesteuerten Anwendung zu gelangen, wählen Sie **Einstellungen** ![Einstellungen](../model-driven-apps/media/powerapps-gear.png) in der App-Symbolleiste und dann **Erweiterte Einstellungen**. 

2. Standardmäßig wird die Ansicht **Benutzerdefinierter Lösungsverlauf** angezeigt. Die folgenden Ansichten sind im Bereich **Lösungsverlauf** verfügbar. 
- **Alle Lösungsverläufe**. Zeigt die Lösungshistorie für das interne System und benutzerdefinierte Lösungen. 
- **Benutzerdefinierter Lösungsverlauf**. Zeigt den Lösungsverlauf nur für benutzerdefinierte Lösungen an. 
- **Interner Lösungsverlauf**. Zeigt die Lösungshistorie nur für interne Systemlösungen. 

Jeder Lösungsverlaufsdatensatz ist schreibgeschützt und enthält die folgenden Eigenschaften: 
- **Startzeit**. Die Zeit, zu der der Vorgang gestartet wurde. 
- **Endzeit**: Die Zeit, zu der der Vorgang geendet ist. 
- **Lösungsversion**. Die Version der Lösung. 
- **Herausgebername**. Der Name des Herausgebers, der dem Vorgang zugeordnet ist. Weitere Informationen [Lösungsherausgeberpräfix ändern](change-solution-publisher-prefix.md)  
- **Vorgang**. Der Vorgang, wie Import, Export oder Löschen. Weitere Informationen dazu finden Sie [Lösungen importieren, aktualisieren und exportieren](import-update-export-solutions.md)
- **Teilvorgang**: Bezeichnet die Art des Vorgangs, wie ein neuer Lösungsimport oder ein Update einer vorhandenen Lösung. 
- **Status**. Der aktuelle Status des Vorgangs, zum Beispiel **Abgeschlossen** oder **Nicht abgeschlossen**. 
- **Ergebnis**. Das Ergebnis des Vorgangs, zum Beispiel **Erfolgreich** oder **Fehler**. 
- **Fehlercode**: Fehlercode, der von dem Vorgang zurückgegeben wird. Ein Fehlercode von 0 bedeutet, dass der Vorgang erfolgreich abgeschlossen wurde. 

### <a name="view-solution-operation-error-details"></a>Lösungsvorgangs-Fehlerdetails anzeigen 
Wenn ein Lösungsvorgang einen Fehler enthält, können Sie ihn auswählen, um eine Seite mit zusätzlichen Fehlerdetails anzuzeigen. 

> [!div class="mx-imgBorder"] 
> ![](media/solution-history-with-failure.png "Solution history with operation error")

Die Detailseite enthält Informationen einschließlich der **Ausnahmenachricht**, die bei der Diagnose der zugrunde liegenden Ursache für den Vorgangsfehler helfen. Einige Fehler, einschließlich Lösungsabhängigkeitsfehler, umfassen unter Umständen auch Links zu **Lösungsebenen**, um Ihnen die Fehlerdiagnose zu erleichtern. Die **Aktivitäts-ID** kann hilfreich sein, wenn Sie sich an den Microsoft-Kundensupport wenden müssen. 

> [!div class="mx-imgBorder"] 
> ![](media/solution-history-error-details.png "Solution operation error details")

### <a name="see-also"></a>Siehe auch
[Anzeigen von Lösungsebenen](solution-layers.md)  <br />
[Überblick über Lösungen](solutions-overview.md) 


