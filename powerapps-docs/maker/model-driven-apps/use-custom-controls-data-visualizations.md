---
title: Verwenden Sie benutzerdefinierte Steuerelemente für modellgesteuerte App-Datenvisualisierungen in PowerApps | MicrosoftDocs
description: 'Erfahren Sie, wie Sie benutzerdefinierte Steuerelemente für Felder verwenden'
ms.custom: ''
ms.date: 06/07/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: 0d6064cd-4d38-4fc2-a564-735cb453a4b2
caps.latest.revision: 8
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-custom-controls-for-model-driven-app-data-visualizations"></a>Verwenden Sie benutzerdefinierte Steuerelemente für modellgesteuerte App-Datenvisualisierungen

In diesem Thema wird erläutert, wie Sie ein benutzerdefiniertes Steuerelement für ein Feld konfigurieren. 

Mit benutzerdefinierten Steuerelementen können Sie Komponenten der Benutzeroberfläche von Anwendungen, wie z. B. ein Feld oder eine Ansicht, die traditionell Text enthalten, in Visualisierungen umwandeln. Benutzerdefinierte Steuerelemente können für Felder, Formulare, Dashboards, Ansichten und Gitter konfiguriert werden. Beispielsweise kann ein Schiebereglersteuerelement auf einem Zahlenfeld konfiguriert werden.

   > [!div class="mx-imgBorder"] 
   > ![Benutzerdefiniertes Schiebereglersteuerelement](media/slider-control.PNG "Schiebereglersteuerelement für ein Feld")

Oder das bearbeitbare Rastersteuerelement kann auf eine Ansicht konfiguriert werden. 

   > [!div class="mx-imgBorder"] 
   > ![Steuerelement für bearbeitbares Rasterelemente](media/editable-grid-example.png)

Sie können ein benutzerdefiniertes Steuerelement so festlegen, dass es in einem Webbrowser-Client angezeigt wird, während ein anderes benutzerdefiniertes Steuerelement in Ihren Dynamics 365 phone- und Dynamics 365 tablet mobile-Apps angezeigt wird. So können Sie beispielsweise ein benutzerdefiniertes Steuerelement zur Eingabe von Zahlen für ein Feld in Webbrowser-Clients verwenden und ein benutzerdefiniertes Schiebereglersteuerelement für die Smartphone-App. Nachdem die Anpassung veröffentlicht wurde, können Benutzer vollständig mit dem Steuerelement interagieren, um den Wert zu ändern, beispielsweise durch Verschieben des Steuerelements bei Verwendung des linearen, benutzerdefinierten Schiebereglersteuerelements. Änderungen werden automatisch gespeichert, wenn das Formular geschlossen wird, genau wie bei Änderungen an einem herkömmlichen Feld auf dem Formular.  
  
## <a name="use-a-custom-control-to-add-visualizations-to-a-field"></a>Verwenden eines benutzerdefinierten Steuerelements, um einem Feld Visualisierungen hinzuzufügen  
 Durch die Schritte dieses Vorgangs werden die standardmäßige Label- und Textfeld-Felder im Feld **Budgetbetrag** in das Schiebereglersteuerelement der Verkaufschancenentität geändert. Sie können auf ähnliche Weise ein vorhandenes Feld mit einem benutzerdefinierten Steuerelement ersetzen oder ein benutzerdefiniertes Steuerelement für ein benutzerdefiniertes Feld konfigurieren.  
  
1.  Melden Sie sich bei [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.  

     

2.  Erweitern Sie **Daten** und wählen **Entitäten**, wählen Sie die Entität aus und wählen Sie die Registerkarte **Formulare**.  
  
2.  Öffnen Sie ein Formular, z.B. das Formular **Haupt** für die Verkaufschancenentität. 
  
3.  Doppelklicken Sie im Formular-Editor auf das Feld, dem Sie ein benutzerdefiniertes Steuerelement hinzufügen möchten, oder fügen Sie ein neues Feld , beispielsweise das Feld **Budgetbetrag** auf dem Hauptformular Verkaufschance hinzu. Sie können ein benutzerdefiniertes Feld erstellen. 
  
4.  Klicken Sie auf der Seite **Feldeigenschaften** auf die Registerkarte **Steuerelemente**, und klicken Sie dann auf **Steuerelement hinzufügen**.  
  
5.  Wählen Sie auf der Seite "Steuerelement hinzufügen" das gewünschte Steuerelement aus, beispielsweise das hier gezeigte **Linearer Schieberegler** und klicken Sie dann auf **Hinzufügen**.  

   > [!div class="mx-imgBorder"] 
   > ![Lineares Schiebereglersteuerelement hinzufügen](media/add-slider.PNG "Lineares Schiebereglersteuerelement hinzufügen")  
  
6.  Wählen Sie den Client aus, auf dem das Steuerelement angezeigt werden soll.  
  
    - **Web**. Um das benutzerdefinierte Steuerelement in jedem Webbrowser zur Verfügung zu stellen, wählen Sie die Option **Web** neben dem Steuerelement aus. Beachten Sie, dass die Option **Web** das Rendern des Steuerelements in Webbrowsern auf PCs, Macs und mobilen Geräten einschließt.  
  
    - **Telefon**. Um das benutzerdefinierte Steuerelement auf allen Smartphones bereitzustellen, auf denen Dynamics 365 for phones ausgeführt wird, wählen Sie die Option **Telefon** neben dem Steuerelement aus.  
  
    - **Tablet**. Um das benutzerdefinierte Steuerelement auf allen Tablets bereitzustellen, auf denen Dynamics 365 for tablets ausgeführt wird, wählen Sie die Option **Tablet** neben dem Steuerelement aus.  
  
   > [!div class="mx-imgBorder"] 
   > ![Auswählen der Clients-Apps zum Ansehen des benutzerdefinierten Steuerelements](media/choose-client.png "Auswählen der Clients-Apps zum Ansehen des benutzerdefinierten Steuerelements")  
  
7.  Klicken Sie auf ![Symbol für das Bearbeiten der Eigenschaft des benutzerdefinierten Steuerelements](media/ccf-pencil-icon.png "Symbol für das Bearbeiten der Eigenschaft des benutzerdefinierten Steuerelements")-Bleistiftsymbol neben **Min.**, **Max.** und **Schritt**, legen Sie die unten beschriebene Eigenschaftenoption fest, und klicken Sie auf **OK**.  
  
   > [!div class="mx-imgBorder"] 
   > ![Eigenschaften des benutzerdefinierten Steuerelements hinzufügen](media/ccf-add-properties.png "Eigenschaften des benutzerdefinierten Steuerelements hinzufügen")
  
   - **Min.**. Legen Sie den minimalen gültigen Wert fest. Sie können einen statischen Wert binden, den Sie eingeben oder den Wert an ein vorhandenes Feld binden. In diesem Beispiel ist **An statischen Wert binden** **Währung** und der minimale Wert, der eingegeben werden kann, ist *Null*.  
  
       - **An statischen Wert binden**. Wählen Sie den Datentyp, beispielsweise eine ganze Zahl (Whole.None), eine Währung, ein Gleitkomma oder eine Dezimalzahl. Geben Sie dann eine Zahl ein, die den minimalen gültigen Wert für das Feld darstellt.  
  
       - **Wert an ein Feld binden**. Wählen Sie ein Feld aus der Liste aus, das als minimaler gültiger Wert verwendet wird.  
  
   - **Max.**. Legen Sie maximalen gültigen Wert für das Feld fest. Ähnlich wie beim Min.-Wert können Sie einen statischen Wert binden, den Sie eingeben, oder den Wert an ein vorhandenes Feld binden, wie zuvor beschrieben. In diesem Beispiel ist **An statischen Wert binden** **Währung** und der maximale Wert, der eingegeben werden kann, ist **1 Milliarde**.  
  
   - **Schritt**. Stellt die Einheit für das Erhöhen oder Verringern dar, wenn vom aktuellen Wert abgezogen oder zu diesem hinzugefügt wird. Beispielsweise können Sie für den Budgetbetrag 100 Dollar Erhöhung\Verringerung auswählen.  
  
   - **Standardsteuerelement ausblenden**. Durch Auswählen dieser Option wird das Steuerelement ausgeblendet, sodass weder das Steuerelement noch die Daten in Clients angezeigt werden, die das benutzerdefinierte Steuerelement nicht unterstützen. Beachten Sie, dass der klassische Dynamics 365-Webclient die meisten benutzerdefinierten Steuerelemente nicht unterstützt. Standardmäßig ist diese Option nicht ausgewählt, und der klassische Dynamics 365-Webclient zeigt das standardmäßige, in der Regel textbasierte, Steuerelement an.  
  
       > [!NOTE]
       >  Das Standardsteuerelement wird mit **(Standard)** gefolgt vom Steuerelementnamen identifiziert.  
       >   
       > > [!div class="mx-imgBorder"] 
       > > ![Standardsteuerelement](media/default-control.png "Standardsteuerelement")  
  
8.  Klicken Sie auf **OK**, um die Seite **Feldeigenschaften** zu schließen.  
  
9. Zum Aktivieren der Anpassung klicken Sie auf dem Entitätsformular auf **Speichern** und dann auf **Veröffentlichen**.  
  
10. Klicken Sie auf **Speichern und schließen**, um den Formular-Editor zu schließen.  
  
### <a name="see-the-custom-control-in-action"></a>Das benutzerdefinierte Steuerelement in Aktion  
 Öffnen Sie einen Datensatz, der das Feld mit dem benutzerdefinierten Steuerelement enthält, beispielsweise das Verkaufschancenformular aus dem vorherigen Beispiel, und sehen Sie sich an, wie sich das Feld geändert hat.  
  
   > [!div class="mx-imgBorder"] 
   > ![Schiebereglersteuerelement auf dem Formular gerendert](media/slider-control.PNG "Schiebereglersteuerelement auf dem Formular gerendert")  
  
 Das Feld ist nun als Schiebereglersteuerelement und nicht als Textfeld gerendert. 

## <a name="use-the-editable-grid-control-on-a-view-or-sub-grid"></a>Verwenden Sie das editierbare Rastersteuerelement auf einer Ansicht oder einem Unterraster.

Mit bearbeitbaren Rastern können Benutzer umfangreiche Inlinebearbeitung direkt von Ansichten und Unterrastern aus vornehmen, ungeachtet dessen, ob sie eine Web-App, ein Tablet oder Smartphone verwenden. Weitere Informationen: [Raster (Listen) mithilfe des benutzerdefinierten Steuerelements „Bearbeitbares Raster” bearbeitbar machen](make-grids-lists-editable-custom-control.md) 
  
## <a name="next-steps"></a>Nächste Schritte  
[Erstellen und Bearbeiten von Feldern](../common-data-service/create-edit-fields.md)
