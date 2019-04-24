---
title: Starten eines Flows in einer Canvas-App | Microsoft-Dokumentation
description: Erstellen Sie einen Flow, der mindestens eine Aufgabe ausführt, wenn ein Ereignis in einer Canvas-App auftritt, z.B. wenn ein Benutzer eine Schaltfläche auswählt.
author: stepsic-microsoft-com
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 12/07/2018
ms.author: stepsic
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5439399a22b47fcf4195cf878208e0e0bd4e0764
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61532109"
---
# <a name="start-a-flow-in-a-canvas-app"></a>Starten eines Flows in einer Canvas-App

Mit Microsoft Flow können Sie eine Logik erstellen, die mindestens eine Aufgabe ausführt, wenn ein Ereignis in einer Canvas-App auftritt. Sie können zum Beispiel eine Schaltfläche so konfigurieren, dass bei Auswahl durch den Benutzer ein Element in einer SharePoint-Liste erstellt wird, eine E-Mail oder eine Besprechungsanfrage gesendet wird, eine Datei der Cloud hinzugefügt wird oder all dies ausgeführt wird. Sie können jedes Steuerelement in der App für das Starten des Flows konfigurieren, der auch weiterhin ausgeführt wird, wenn Sie PowerApps schließen.

> [!NOTE]
> Wenn ein Benutzer einen Flow aus einer App ausgeführt wird, muss dieser Benutzer über die Berechtigung für die Aufgaben, die in den Datenfluss angegeben werden. Andernfalls schlägt der Flow fehl.

## <a name="prerequisites"></a>Voraussetzungen

- [Registrieren Sie sich](../signup-for-powerapps.md) bei PowerApps.
- Erfahren Sie, wie Sie ein [Steuerelement konfigurieren](add-configure-controls.md).

## <a name="create-a-flow"></a>Erstellen eines Flows

1. Melden Sie sich bei [PowerApps](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.

1. Wählen Sie in der linken Navigationsleiste auf **Geschäftslogik**, und wählen Sie dann **Flows**.

1. In der oberen linken Ecke des der **Meine Flows** Seite **neu**, und wählen Sie dann **ohne Vorlage neu erstellen**.

    ![Option, um einen Flow ohne Vorlage zu erstellen](./media/using-logic-flows/create-from-blank.png)

1. Wählen Sie im unteren Bereich des daraufhin angezeigten Dialogfeld **Hunderte von Verbindungen und Trigger Durchsuchen**.

1. Geben Sie in das Suchfeld **PowerApps**, und wählen Sie dann die **PowerApps** Symbol.

    ![Erstellen eines Triggers für PowerApps](./media/using-logic-flows/set-trigger.png)
    
1. Wählen Sie auf der nächsten Seite das Symbol "PowerApps" erneut aus, und wählen Sie dann **neuer Schritt**.

1. Klicken Sie im Feld **Connectors und Trigger Durchsuchen**, geben Sie eine Aktion für den Flow ein, wie im folgenden Beispiel:

   1. Typ **SharePoint** in das Feld ein, und wählen Sie dann **Element erstellen** in der Liste unter **Aktionen**.

       ![Option zum Erstellen eines SharePoint-Elements](./media/using-logic-flows/create-sharepoint-item.png)

   1. Geben Sie, wenn Sie dazu aufgefordert werden, die Anmeldeinformationen für die Verbindung mit SharePoint an.

   1. Geben oder fügen Sie in das Feld **Websiteadresse** die URL einer SharePoint Online-Website ein, die eine Liste enthält.

       > [!NOTE]
       > Fügen Sie den Namen der Liste nicht an die URL an.

   1. In der **Listenname** geben die Liste, die Sie verwenden möchten.
   
       ![Geben Sie die Liste](./media/using-logic-flows/list-fields.png)

   1. Wählen Sie das Eingabefeld für ein Feld in der Liste (z. B. **Titel**) Option **Weitere Informationen finden Sie** im Bereich von dynamischem Inhalt, und wählen Sie dann **in PowerApps Fragen**. 

       ![Hinzufügen von „In PowerApps fragen“ zum Feld „Titel“](./media/using-logic-flows/ask-in-powerapps.png)

1. (optional) Geben Sie einen oder mehrere zusätzliche Schritte, wie das Senden von e-Mail zur Genehmigung an eine Adresse, die Sie angeben, oder Erstellen eines zugehörigen Eintrags in einer anderen Datenquelle.

1. In der Nähe der oberen linken Ecke, geben Sie einen Namen für den Flow ein, und wählen Sie dann **speichern** in der Nähe der oberen rechten Ecke.

## <a name="add-a-flow-to-an-app"></a>Hinzufügen eines Flows zu einer App
1. Wählen Sie in der linken Navigationsleiste auf **erstellen**.

1. Zeigen Sie auf die **Canvas-app mit leerer App** Kachel, und wählen Sie dann **diese App**.

1. Fügen Sie ein **[Texteingabe](controls/control-text-input.md)**-Steuerelement hinzu, und nennen Sie es **RecordTitle**.

1. Fügen Sie ein **[Schaltflächen](controls/control-button.md)**-Steuerelement hinzu, und verschieben Sie es unter **RecordTitle**.

1. Wählen Sie bei ausgewähltem **[Schaltflächen](controls/control-button.md)**-Steuerelement **Flows** auf der Registerkarte **Aktion** aus.

    ![Option „Flows“ auf der Registerkarte „Aktion“](./media/using-logic-flows/action-tab.png)

1. Wählen Sie im Bereich, der angezeigt wird, den Flow aus, den Sie im vorherigen Verfahren erstellt haben.

    > [!NOTE]
   > Wenn der von Ihnen erstellte Flow nicht verfügbar ist, vergewissern Sie sich, dass PowerApps auf die Umgebung festgelegt ist, in der Sie den Flow erstellt haben.

    ![Hinzufügen eines Flows aus dem Bereich „Anpassung“](./media/using-logic-flows/add-flow-from-pane.png)

1. Geben oder fügen Sie in der Bearbeitungsleiste **RecordTitle.Text)** am Ende der Formel ein, die automatisch hinzugefügt wurde.

    ![OnSelect-Eigenschaft, die den Flow enthält](./media/using-logic-flows/onselect-with-flow.png)

## <a name="test-the-flow"></a>Testen des Flows
1. Doppelklicken Sie auf die **Texteingabe** zu steuern, und geben oder fügen Sie Text ein.

1. Während Sie die Alt-Taste gedrückt halten, wählen Sie die **[Schaltfläche](controls/control-button.md)** Steuerelement.

    Ein SharePoint-Element wird in der Liste erstellt, die Sie mit dem angegebenen Text, den Sie als Titel angegeben werden. Wenn die Liste bei Ausführung des Flows geöffnet war, müssen Sie ggf. Ihr Browserfenster aktualisieren, um die Änderungen anzuzeigen.
