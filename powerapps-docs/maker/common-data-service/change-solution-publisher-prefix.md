---
title: Lösungsherausgeber Übersicht | MicrosoftDocs
ms.custom: ''
ms.date: 02/03/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
author: Mattp123
ms.assetid: ece684h8-ad40-4bfa-975a-3e5bafb854aa
caps.latest.revision: 55
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: b54afabbed9e7dfcc53fe887f600593e77a02a7f
ms.sourcegitcommit: cb533c30252240dc298594e74e3189d7290a4bd7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/04/2020
ms.locfileid: "3017568"
---
# <a name="solution-publisher-overview"></a>Lösungsherausgeber Übersicht

Jede App, die Sie erstellen, ist Teil einer Lösung. Jede Lösung hat einen Herausgeber. Sie geben den Herausgeber an, wenn Sie eine Lösung erstellen. 

> [!div class="mx-imgBorder"] 
> <img src="media/solution-publisher-select.png" alt="Select solution publisher" height="731" width="416">

Die Lösungsherausgeber gibt an, wer die App entwickelt hat. Das Präfix gibt schnell an, wie man versteht, welche Lösung dem Element hinzugefügt wurde. Aus diesen Gründen sollten Sie ein Lösungsherausgeber erstellen und ein aussagekräftiges Präfix angeben. Dies ist besonders wichtig, wenn Metadatenelemente aus importierten Lösungen angezeigt werden. Beispielsweise wird die Lösung verwendet, die die Fundraiser-Beispiel-App enthält und *Beispiel* als Verleger-Präfix verwendet. 

> [!div class="mx-imgBorder"] 
> ![Fundraiser-Lösungsherausgeberpräfix](media/fundraiser-sample-app-prefix.png)

> [!NOTE]
> Wenn Sie ein Lösungsherausgeberpräfix ändern, sollten Sie diese Schritte ausführen, bevor Sie neue Metadatenelemente erstellen. Sie können die Namen von Metadaten-Elementen ändern. 

## <a name="common-data-services-default-solution"></a>Common Data Service Standardlösung
Die Standardlösung in Power Apps ist die Common Data Service Standardlösung, die mit dem Common Data Service Standardverleger assoziiert ist. Das Standardverlegerpräfix wird zufällig für diesen Herausgeber zugewiesen, und lautet beispielsweise *cr8a3*. Das bedeutet, dass der Name jedes neuen Artikels der Metadaten in der Standardlösung, die für die Organisation erstellt wurden, diese Endung im Namen hat, um die Elemente eindeutig zu identifizieren. Wenn Sie eine neue Entität mit Namen *Animal* erstellen, wäre der eindeutige Name, der von Common Data Service verwendet wird *cr8a3_animal*. Dasselbe gilt für alle neuen Felder (Attribute), Beziehungen oder optionset Optionen. Wenn Sie die Standardlösung anpassen, sollten Sie das Publisher-Präfix ändern. 

## <a name="create-a-solution-publisher"></a>Erstellen eines Lösungsherausgebers
1.  Wählen Sie im Power Apps Portal **Einstellungen** (Zahnrad) und wählen Sie **Erweiterte Einstellungen**. 
2.  Wählen Sie **Einstellungen** > **Anpassungen** > **Veeöffentlicher**. 
3.  In der Befehlsleiste **Publisher-Hauptansicht** wählen Sie **Neu**. 
4.  Geben Sie die erforderlichen Informationen ein: 
   - **Anzeigename**: Geben Sie den Anzeigename für den Herausgeber ein. 
   - **Name** Geben Sie den eindeutigen Anzeigename für den Herausgeber ein. 
   - **Präfix**. Geben Sie das gewünschte Herausgeber-Präfix ein. 
   -    **Optionswertpräfix**. Dieses Feld generiert eine Nummer basierend auf dem Verleger-Präfix. Diese Nummer wird verwendet, wenn Sie Optionen zu Optionssätzen hinzufügen, und zeigt an, welche Lösung zum Hinzufügen der Option verwendet wurde. 
   - **Kontaktdetails**. Optional können Sie Kontakt- und Adressinformationen hinzufügen.
5. Klicken Sie auf **Speichern und schließen**.

## <a name="change-a-solution-publisher"></a>Ändern eines Lösungsherausgebers
Sie können einen Lösungsherausgeber für eine nicht verwaltete Lösung ändern, indem Sie die folgenden Schritte ausführen:
1.  In dem Power Apps Portal wählen Sie **Lösungen**, und wählen **…** neben der gewünschten Lösung wählen Sie **Einstellungen**. 
2.  In dem **Lösungseinstellungen** Bereich wählen Sie **Herausgeber bearbeiten**. 
3.  Bearbeiten Sie die Felder**Anzeigename** und **Präfix** und geben die gewünschten Werte ein. Das Feld **Option Wertpräfix** generiert eine Nummer basierend auf dem Verleger-Präfix. Diese Nummer wird verwendet, wenn Sie Optionen zu Optionssätzen hinzufügen, und zeigt an, welche Lösung zum Hinzufügen der Option verwendet wurde. 
4.  Zusätzlich zum Präfix können Sie auch den Lösungsherausgeber-Anzeigename, Kontaktinformationen und Adresse im Abschnitt **Kontaktdetails** ändern. 
5.  Klicken Sie auf **Speichern und schließen**.

### <a name="see-also"></a>Siehe auch
[Erstellen einer Lösung](create-solution.md)