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
ms.openlocfilehash: c8d16a0c8451abc769990dbd88e6ad7f1e7846a5
ms.sourcegitcommit: c9c1c78dadc92913558dab44af0890e90e2adcd0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/27/2020
ms.locfileid: "3088579"
---
# <a name="solution-publisher-overview"></a>Lösungsherausgeber Übersicht

Jede App, die Sie erstellen, ist Teil einer Lösung. Jede Lösung hat einen Herausgeber. Sie geben den Herausgeber an, wenn Sie eine Lösung erstellen. 

> [!div class="mx-imgBorder"] 
> <img src="media/solution-publisher-select.png" alt="Select solution publisher" height="731" width="416">

Der Herausgeber der Lösung gibt an, wer die App entwickelt hat. Aus diesem Grund sollten Sie einen aussagekräftigen Solution Publisher anlegen. Sie können den Lösungsherausgeber für eine Lösung anzeigen, indem Sie **Einstellungen** aus dem Bereich **Lösungen** in Power Apps wählen.

## <a name="solution-publisher-prefix"></a>Präfix des Lösungsverlegers
Ein Lösungsherausgeber enthält ein Präfix. Das Präfix kann helfen, den für die Komponente zuständigen Herausgeber zu bestimmen. Beispielsweise enthält die hier angezeigte *Contoso-Lösung* ein Lösungsherausgeber-Präfix, das *contoso* lautet. 

> [!div class="mx-imgBorder"] 
> ![Fundraiser-Lösungsherausgeberpräfix](media/publisher-prefix.png)

> [!NOTE]
> Wenn Sie ein Lösungsherausgeberpräfix ändern, sollten Sie diese Schritte ausführen, bevor Sie neue Metadatenelemente erstellen. Sie können die Namen von Metadaten-Elementen ändern. 

## <a name="common-data-services-default-solution"></a>Common Data Services Standardlösung
Die Standardlösung in Power Apps ist die Common Data Services Standardlösung, die mit dem Common Data Service Standard-Publisher verbunden ist. Das Standardverlegerpräfix wird zufällig für diesen Herausgeber zugewiesen, und lautet beispielsweise *cr8a3*. Das bedeutet, dass der Name jedes neuen Artikels der Metadaten in der Standardlösung, die für die Organisation erstellt wurden, diese Endung im Namen hat, um die Elemente eindeutig zu identifizieren. Wenn Sie eine neue Entität mit Namen *Animal* erstellen, wäre der eindeutige Name, der von Common Data Service verwendet wird *cr8a3_animal*. Dasselbe gilt für alle neuen Felder (Attribute), Beziehungen oder optionset Optionen. Wenn Sie die Standardlösung anpassen, sollten Sie das Publisher-Präfix ändern. 

## <a name="create-a-solution-publisher"></a>Erstellen eines Lösungsherausgebers
1.  Wählen Sie im Portal Power Apps die Option **Lösungen**. 
2.  Wählen Sie in der Befehlsleiste **Neue Lösung**, wählen Sie im rechten Fensterbereich die Dropdown-Liste **Herausgeber** und wählen Sie dann **+Herausgeber**. 
    > [!div class="mx-imgBorder"] 
    > <img src="media/create-new-pubisher.png" alt="Create a new publisher" height="738" width="400">
3.  Geben Sie im Formular **Neuer Herausgeber** die erforderlichen und optionalen Informationen ein: 
   - **Anzeigename**: Geben Sie den Anzeigename für den Herausgeber ein. 
   - **Name** Geben Sie den eindeutigen Anzeigename für den Herausgeber ein. 
   - **Präfix**. Geben Sie das gewünschte Herausgeber-Präfix ein. 
   -    **Optionswertpräfix**. Dieses Feld generiert eine Nummer basierend auf dem Verleger-Präfix. Diese Nummer wird verwendet, wenn Sie Optionen zu Optionssätzen hinzufügen, und zeigt an, welche Lösung zum Hinzufügen der Option verwendet wurde. 
   - **Kontaktdetails**. Optional können Sie Kontakt- und Adressinformationen hinzufügen.
4. Klicken Sie auf **Speichern und schließen**.

## <a name="change-a-solution-publisher"></a>Ändern eines Lösungsherausgebers
Sie können einen Lösungsherausgeber für eine nicht verwaltete Lösung ändern, indem Sie die folgenden Schritte ausführen:
1.  In dem Power Apps Portal wählen Sie **Lösungen**, und wählen **…** neben der gewünschten Lösung wählen Sie **Einstellungen**. 
2.  In dem **Lösungseinstellungen** Bereich wählen Sie **Herausgeber bearbeiten**. 
3.  Bearbeiten Sie die Felder**Anzeigename** und **Präfix** und geben die gewünschten Werte ein. Das Feld **Option Wertpräfix** generiert eine Nummer basierend auf dem Verleger-Präfix. Diese Nummer wird verwendet, wenn Sie Optionen zu Optionssätzen hinzufügen, und zeigt an, welche Lösung zum Hinzufügen der Option verwendet wurde. 
4.  Zusätzlich zum Präfix können Sie auch den Lösungsherausgeber-Anzeigename, Kontaktinformationen und Adresse im Abschnitt **Kontaktdetails** ändern. 
5.  Klicken Sie auf **Speichern und schließen**.

### <a name="see-also"></a>Siehe auch
[Erstellen einer Lösung](create-solution.md)