---
title: Hinzufügen von Code Komponenten zu einem Feld oder einer Entität | Microsoft-Dokumentation
description: Prozess zum Importieren von Code Komponenten
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
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72347036"
---
# <a name="add-code-components-to-a-field-or-entity-in-model-driven-apps"></a>Hinzufügen von Code Komponenten zu einem Feld oder einer Entität in Modell gesteuerten apps

Mit Code Komponenten können Sie Felder transformieren, die normalerweise Text in Visualisierungen enthalten. Analog dazu können Sie mithilfe von Code Komponenten Datasets, wie z. b. eine Sicht, in einem visuellen Rendering anstelle einer Liste von Datensätzen anzeigen. Code Komponenten können als Visualisierungen in Formularen, Dashboards, Ansichten und Homepage-Rastern angezeigt werden. 


   > [!div class="mx-imgBorder"] 
   > (../../maker/model-driven-apps/media/slider-control.PNG "Schieberegler") -Steuerelement für ![benutzerdefiniertes Schieberegler]

## <a name="add-a-code-component-to-a-field"></a>Hinzufügen einer Code Komponente zu einem Feld

Wenn Sie die Schritte in diesem Verfahren ausführen, ändern Sie das Feld Standard Bezeichnung und Textfeld des Felds **Budget Betrag** in die Code Komponente für den Schieberegler für die Entität "Chance". Sie können ähnliche Schritte verwenden, um ein vorhandenes Feld durch eine Code Komponente zu ersetzen oder eine Code Komponente für ein benutzerdefiniertes Feld zu konfigurieren.

1. Öffnen Sie den Projektmappen-Explorer.

2. Erweitern Sie **Entitäten**, erweitern Sie die gewünschte Entität, z. b. die Verkaufs **Chancen** Entität, wählen Sie **Formulare**aus, und öffnen Sie dann ein Formular wie das **Haupt** Formular.

3. Doppelklicken Sie im Formular-Editor auf das Feld, in dem Sie eine Code Komponente hinzufügen möchten, z. b. das Feld **Budget Betrag** im Hauptformular der Verkaufschance. Alternativ können Sie ein benutzerdefiniertes Feld erstellen.

4. Wählen Sie auf der Seite **Feldeigenschaften** die Registerkarte Steuer **Elemente** aus, und klicken Sie dann auf **Steuerelement hinzufügen**.

5. Wählen Sie auf der Seite Steuerelement hinzufügen die gewünschte Komponente aus, z. b. die **lineare Schieberegler** -Komponente, und klicken Sie dann auf **Hinzufügen**.

   > [!div class="mx-imgBorder"] 
   > ![Lineare Schieberegler-Steuer]Element hinzufügen(../../maker/model-driven-apps/media/add-slider.PNG "lineares Schieberegler")

6. Wählen Sie den Client aus, auf dem die Komponente angezeigt werden soll.

   - **Web**. Um die Code Komponente über einen beliebigen Webbrowser verfügbar zu machen, wählen Sie die Option Web neben der Komponente aus. Beachten Sie, dass das Festlegen der Weboption das Rendern der Komponente in Webbrowsern auf PCs, Macs und mobilen Geräten einschließt.

   - **Telefon**. Wählen Sie die Option Telefon neben der Komponente aus, um die Code Komponente auf Smartphones mit Dynamics 365 für Smartphones verfügbar zu machen.

   - **Tablet**. Um die Code Komponente auf Tablet-Geräten mit Dynamics 365 für Tablets verfügbar zu machen, wählen Sie die Option Tablet neben der Komponente aus.

   > [!div class="mx-imgBorder"] 
   > ![Wählen Sie die Client-Apps aus, um das benutzerdefinierte Steuerelement anzuzeigen](../../maker/model-driven-apps/media/choose-client.png "") 

7. Wählen Sie das Stift Symbol neben **Min**, **Max**und **Schritt**aus, legen Sie die Option Eigenschaft fest, und wählen Sie dann **OK**aus.  
   
   > [!div class="mx-imgBorder"] 
   > ![Benutzerdefinierte Steuerelement Eigenschaften]hinzufügen(../../maker/model-driven-apps/media/ccf-add-properties.png "benutzerdefinierte Steuerelement Eigenschaften")

   - **Min**. Legen Sie den minimal zulässigen Wert fest. Sie können einen statischen Wert, den Sie eingeben, binden oder den Wert an ein vorhandenes Feld binden. In diesem Beispiel ist die **Bindung an den statischen Wert** **Currency** , und der Minimalwert, der eingegeben werden kann, ist *0 (null*).  
  
       - **Binden an einen statischen Wert**. Wählen Sie den Datentyp aus, z. b. eine ganze Zahl (ganz. None), Currency, Floating Point (FP) oder Decimal. Geben Sie als nächstes eine Zahl ein, die den minimal zulässigen Wert für das Feld darstellt.  
  
       - **Binden an Werte in einem Feld**. Wählen Sie ein Feld aus der Liste aus, das als minimal akzeptierter Wert verwendet werden soll.  
  
   - **Maximal**. Legen Sie den maximal zulässigen Wert für das Feld fest. Ähnlich wie der minimale Wert können Sie einen statischen Wert, den Sie eingeben, binden oder den Wert an ein vorhandenes Feld binden, wie zuvor beschrieben. In diesem Beispiel ist die **Bindung an den statischen Wert** **Currency** , und der maximale Wert, der eingegeben werden kann, ist **1 Milliarde**.  
  
   - **Schritt**. Dies stellt die Einheit dar, die beim Hinzufügen oder subtrahieren vom aktuellen Wert Inkrement oder Dekrement erhöht werden soll. Beispielsweise können Sie für den Budgetbetrag 100 Dollar increments\dekrementsauswählen.  
  
   - **Standard Steuerelement ausblenden**. Wenn Sie diese Option auswählen, wird die Komponente ausgeblendet, sodass weder die Komponente noch die Daten auf einem der Clients angezeigt werden, die die Code Komponente nicht unterstützen.   
  
8. Wählen Sie **OK**aus, um die Feldeigenschaften Seite zu schließen.  
  
9. Wählen Sie zum Aktivieren der Anpassung im Formular Entität die Option **Speichern**aus, und wählen Sie dann **veröffentlichen**aus.  
  
10. Wählen Sie **Speichern und schließen** aus, um den Formular-Editor zu schließen.  
  
## <a name="add-code-component-to-an-entity"></a>Hinzufügen einer Code Komponente zu einer Entität

Führen Sie die folgenden Schritte aus, um einem Raster oder einer Sicht eine Code Komponente wie eine Daten Satz Komponente oder eine einfache Tabellenkomponente hinzuzufügen:

  - Navigieren Sie zu **Einstellungen > Anpassungen** , und klicken Sie auf **System anpassen**.
  - Klicken Sie auf den Pfeil neben **Entitäten** Registerkarte a Wählen Sie die Entität aus, die Sie der Code Komponente hinzufügen möchten. 
  - Klicken Sie auf die Registerkarte Steuer **Elemente** , und klicken Sie auf **Steuerelement hinzufügen**.
  - Wählen Sie auf der Seite Steuerelement hinzufügen die gewünschte Komponente aus, z. b. einfache Tabellenkomponente, und wählen Sie dann **Hinzufügen**aus.
  - Wählen Sie den Client aus, auf dem die Komponente angezeigt werden soll.


## <a name="see-the-code-component-in-action"></a>Anzeigen der Code Komponente in Aktion  

 Öffnen Sie einen Datensatz, der das Feld mit der Code Komponente enthält, z. b. das Verkaufschancen Formular aus dem vorherigen Beispiel, und zeigen Sie an, wie das Feld geändert wird. Das Feld wird nun als Schieberegler-Komponente anstelle des Textfelds gerendert.  

> [!div class="mx-imgBorder"] 
> Das ![Schieberegler-Steuer]Element wurde auf dem(../../maker/model-driven-apps/media/slider-control.PNG "Formular gerendert") .  

### <a name="see-also"></a>Siehe auch

[Implementieren von Komponenten in typescript](implementing-controls-using-typescript.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](overview.md)