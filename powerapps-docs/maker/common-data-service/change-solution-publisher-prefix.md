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
ms.openlocfilehash: 516f4a35cf7d31c45df011b7685ade1526246582
ms.sourcegitcommit: c6906775005aec98973b1f5c3dbe5924aff6d26e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "3341273"
---
# <a name="solution-publisher-overview"></a>Lösungsherausgeber Übersicht

Jede App, die Sie erstellen, ist Teil einer Lösung. Jede Lösung hat einen Herausgeber. Sie geben den Herausgeber an, wenn Sie eine Lösung erstellen. 

Der Herausgeber der Lösung gibt an, wer die App entwickelt hat. Aus diesem Grund sollten Sie einen aussagekräftigen Lösungsherausgeber anlegen. Sie können den Lösungsherausgeber für eine Lösung anzeigen, indem Sie **Einstellungen** aus dem Bereich **Lösungen** in Power Apps wählen.

Weitere Informationen über den Lösungsherausgeber finden Sie unter [Lösungsherausgeber](/power-platform/alm/solution-concepts-alm#solution-publisher).

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