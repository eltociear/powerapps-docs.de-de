---
title: Hinzufügen von Codekomponenten zu einem Feld oder einer Entität | Microsoft-Dokumentation
description: Prozess zum Importieren von Codekomponenten
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: 63ecdde21328219b70af04b9b65edbb3073f3025
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748487"
---
# <a name="add-code-components-to-a-field-or-entity-in-model-driven-apps"></a>Hinzufügen von Codekomponenten zu einem Feld oder einer Entität in modellgesteuerten Apps

Mit Codekomponenten können Sie Felder transformieren, die üblicherweise Text in Visualisierungen enthalten. Sie können mit Codekomponenten auch Datasets, z. B. eine Ansicht, transformieren, um es in einem visuelleren Rendering als einer Datensatzliste darzustellen. Codekomponenten können in Formularen, Dashboards, Ansichten und Homepagerastern als Visualisierungen erscheinen. 


   > [!div class="mx-imgBorder"] 
   > ![Benutzerdefiniertes Schieberegler-Steuerelement](../../maker/model-driven-apps/media/slider-control.PNG "Schieberegler-Steuerelement für ein Feld")

## <a name="add-a-code-component-to-a-field"></a>Hinzufügen einer Codekomponente zu einem Feld

Durch Ausführen der Schritte in diesem Verfahren werden die Standardbezeichnung und das Textfeld im Feld **Budgetbetrag** in die Schieberegler-Codekomponente in der Entität „Geschäftschance” geändert. Sie können ähnliche Schritte verwenden, um ein vorhandenes Feld durch eine Codekomponente zu ersetzen oder eine Codekomponente für ein benutzerdefiniertes Feld zu konfigurieren.

1. Öffnen Sie den Projektmappen-Explorer.

2. Erweitern Sie **Entitäten**, erweitern Sie die Entität, wie die Entität **Verkaufschance**, wählen Sie **Formulare**, und öffnen dann ein Formular wie das Formular **Hauptformular**.

3. Klicken Sie zweimal im Formulareditor in das Feld, in dem Sie eine Codekomponente hinzufügen möchten, z. B. in das Feld **Budgetbetrag** im Geschäftschance-Hauptformular. Sie können ein benutzerdefiniertes Feld erstellen.

4. Klicken Sie auf der Seite **Feldeigenschaften** auf die Registerkarte **Steuerelemente**, und klicken Sie dann auf **Steuerelement hinzufügen**.

5. Wählen Sie auf der Seite „Steuerelement hinzufügen” die Komponente aus, die Sie möchten, z. B. die **Linearer Schiebregler**-Komponente, und wählen Sie dann **Hinzufügen** aus.

   > [!div class="mx-imgBorder"] 
   > ![Lineares Schieberegler-Steuerelement hinzufügen](../../maker/model-driven-apps/media/add-slider.PNG "Lineares Schieberegler-Steuerelement hinzufügen")

6. Wählen Sie den Client aus, auf dem die Komponente erscheinen soll.

   - **Web**. Damit die Codekomponente von jedem Webbrowser verfügbar ist, wählen Sie die Web-Option neben der Komponente aus. Beachten Sie, dass das Festlegen der Web-Option das Rendern der Komponente in Webbrowsern auf PCs, Macs und Mobilgeräten umfasst.

   - **Telefon**. Damit die Codekomponente auf Telefonen verfügbar wird, auf denen Dynamics 365 für Telefone ausgeführt wird, wählen Sie die Option "Telefon" neben der Komponente aus.

   - **Tablet**. Damit die Codekomponente auf Tablet-Geräten verfügbar wird, auf denen Dynamics 365 für Tablets ausgeführt wird, wählen Sie die Option "Tablet" neben der Komponente aus.

   > [!div class="mx-imgBorder"] 
   > ![Wählen Sie die Client-Apps, um das benutzerdefinierte Steuerelement anzuzeigen](../../maker/model-driven-apps/media/choose-client.png "Wählen Sie die Client-Apps aus, um das benutzerdefinierte Steuerelement anzuzeigen") 

7. Wählen Sie das Bleistiftsymbol neben **Min**, **Max** und **Schritt** aus, legen Sie die Eigenschaftsoption fest und wählen Sie dann **OK** aus.  
   
   > [!div class="mx-imgBorder"] 
   > ![Hinzufügen von benutzerdefinierten Steuerelementeigenschaften](../../maker/model-driven-apps/media/ccf-add-properties.png "Hinzufügen von benutzerdefinierten Steuerelementeigenschaften")

   - **Min.**. Legen Sie den minimalen gültigen Wert fest. Sie können einen statischen Wert binden, den Sie eingeben oder den Wert an ein vorhandenes Feld binden. In diesem Beispiel ist **An statischen Wert binden** **Währung** und der minimale Wert, der eingegeben werden kann, ist *Null*.  
  
       - **An statischen Wert binden**. Wählen Sie den Datentyp, beispielsweise eine ganze Zahl (Whole.None), eine Währung, ein Gleitkomma oder eine Dezimalzahl. Geben Sie dann eine Zahl ein, die den minimalen gültigen Wert für das Feld darstellt.  
  
       - **Wert an ein Feld binden**. Wählen Sie ein Feld aus der Liste aus, das als minimaler gültiger Wert verwendet wird.  
  
   - **Max.**. Legen Sie maximalen gültigen Wert für das Feld fest. Ähnlich wie beim Min.-Wert können Sie einen statischen Wert binden, den Sie eingeben, oder den Wert an ein vorhandenes Feld binden, wie zuvor beschrieben. In diesem Beispiel ist **An statischen Wert binden** **Währung** und der maximale Wert, der eingegeben werden kann, ist **1 Milliarde**.  
  
   - **Schritt**. Stellt die Einheit für das Erhöhen oder Verringern dar, wenn vom aktuellen Wert abgezogen oder zu diesem hinzugefügt wird. Beispielsweise können Sie für den Budgetbetrag 100 Dollar Erhöhung\Verringerung auswählen.  
  
   - **Standardsteuerelement ausblenden**. Durch die Auswahl der Option wird die Komponente ausgeblendet. Also werden weder die Komponente noch die Daten in einem der Clients angezeigt, die diese Codekomponente nicht unterstützen.   
  
8. Klicken Sie auf **OK**, um die Seite "Feldeigenschaften" zu schließen.  
  
9. Zum Aktivieren der Anpassung klicken Sie auf dem Entitätsformular auf **Speichern** und dann auf **Veröffentlichen**.  
  
10. Klicken Sie auf **Speichern und schließen**, um den Formular-Editor zu schließen.  
  
## <a name="add-code-component-to-an-entity"></a>Hinzufügen der Codekomponente zu einer Entität

Um eine Codekomponente wie die Datensatz-Komponente oder eine einfache Tabellenkomponente einem Raster oder einer Ansicht hinzuzufügen, führen Sie die folgenden Schritte aus:

  - Navigieren Sie zu **Einstellungen > Anpassungen** und klicken Sie auf **System anpassen**.
  - Klicken Sie auf den Pfeil neben der Registerkarte **Entitäten**, und wählen Sie die Entität aus, der Sie die Codekomponente hinzufügen möchten. 
  - Klicken Sie auf die Registerkarte **Steuerelemente** und auf **Steuerelement hinzufügen**.
  - Auf der Seite "Steuerelement hinzufügen" wählen Sie die Komponente aus, die Sie möchten, z. B. die Komponente "Einfache Tabelle", und wählen dann **Hinzufügen** aus.
  - Wählen Sie den Client aus, auf dem die Komponente erscheinen soll.


## <a name="see-the-code-component-in-action"></a>Die Codekomponente in Aktion  

 Öffnen Sie einen Datensatz, der das Feld mit der Codekomponente enthält, z. B. das Geschäftschance-Feld aus dem vorherigen Beispiel, und schauen Sie, wie das Feld sich geändert hat. Das Feld wird jetzt als Schiebreglerkomponente statt als Textfeld gerendert.  

> [!div class="mx-imgBorder"] 
> ![Schieberegler-Steuerelement auf Formular angezeigt](../../maker/model-driven-apps/media/slider-control.PNG "Schieberegler-Steuerelement auf Formular angezeigt")  

### <a name="see-also"></a>Siehe auch

[Implementieren von Komponenten in TypeScript](implementing-controls-using-typescript.md)<br/>
[PowerApps component framework API-Referenz](reference/index.md)<br/>
[Übersicht über das PowerApps component framework](overview.md)