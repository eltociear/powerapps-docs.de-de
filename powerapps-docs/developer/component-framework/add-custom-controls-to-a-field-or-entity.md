---
title: Hinzufügen von benutzerdefinierten Komponenten zu einem Feld oder einer Entität | Microsoft Docs
description: Prozess zum Importieren von benutzerdefinierten Komponenten
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
---

# <a name="add-custom-components-to-a-field-or-entity"></a>Hinzufügen von benutzerdefinierten Komponenten zu einem Feld oder einer Entität

Mit benutzerdefinierten Komponenten können Sie Felder transformieren, die üblicherweise Text in Visualisierungen enthalten. Sie können mit benutzerdefinierte Komponenten auch Datasets, z. B. eine Ansicht, transformieren, um es in einem visuelleren Rendering als einer Datensatzliste darzustellen. Benutzerdefinierte Komponenten können in Formularen, Dashboards, Ansichten und Homepagerastern als Visualisierungen erscheinen. 

## <a name="add-a-custom-component-to-a-field"></a>Hinzufügen einer benutzerdefinierten Komponente zu einem Feld

Das Ausführen der Schritte in dieser Prozedur ändert die Standardbezeichnung und das Textfeld im **Budgetbetrag**-Feld auf die benutzerdefinierte Schiebreglerkomponente in der Entität "Geschäftschance". Sie können ähnliche Schritte verwenden, um ein vorhandenes Feld durch ein benutzerdefiniertes Feld zu ersetzen oder eine benutzerdefinierte Komponente für ein benutzerdefiniertes Feld zu konfigurieren.

1. Öffnen Sie den Projektmappen-Explorer.

2. Erweitern Sie **Entitäten**, erweitern Sie die Entität, wie die Entität **Verkaufschance**, wählen Sie **Formulare**, und öffnen dann ein Formular wie das Formular **Hauptformular**.

3. Klicken Sie zweimal im Formulareditor in das Feld, in dem Sie eine benutzerdefinierte Komponente hinzufügen möchten, z. B. das Feld **Budgetbetrag** im Geschäftschance-Hauptformular. Sie können ein benutzerdefiniertes Feld erstellen.

4. Klicken Sie auf der Seite **Feldeigenschaften** auf die Registerkarte **Steuerelemente**, und klicken Sie dann auf **Steuerelement hinzufügen**.

5. Wählen Sie auf der Seite "Steuerelement hinzufügen" die Komponente aus, die Sie möchten, z. B. die **Linearer Schiebregler**-Komponente, und wählen Sie dann **Hinzufügen** aus.

6. Wählen Sie den Client aus, auf dem die Komponente erscheinen soll.

   - **Web**. Damit die benutzerdefinierte Komponente von jedem Webbrowser verfügbar ist, wählen Sie die Web-Option neben der Komponente aus. Beachten Sie, dass das Festlegen der Web-Option das Rendern der Komponente in Webbrowsern auf PCs, Macs und Mobilgeräten umfasst.

   - **Telefon**. Damit die benutzerdefinierte Komponente auf Telefonen verfügbar wird, auf denen Dynamics 365 for phones ausgeführt wird, wählen Sie die Option "Telefon" neben der Komponente aus.

   - **Tablet**. Damit die benutzerdefinierte Komponente auf Tablet-Geräten verfügbar wird, auf denen Dynamics 365 for tablets ausgeführt wird, wählen Sie die Option "Tablet" neben der Komponente aus.
7. Wählen Sie das Bleistiftsymbol neben **Min**, **Max** und **Schritt** aus, legen Sie die Eigenschaftsoption fest und wählen Sie dann **OK** aus.  
  
   - **Min.**. Legen Sie den minimalen gültigen Wert fest. Sie können einen statischen Wert binden, den Sie eingeben oder den Wert an ein vorhandenes Feld binden. In diesem Beispiel ist **An statischen Wert binden** **Währung** und der minimale Wert, der eingegeben werden kann, ist *Null*.  
  
       - **An statischen Wert binden**. Wählen Sie den Datentyp, beispielsweise eine ganze Zahl (Whole.None), eine Währung, ein Gleitkomma oder eine Dezimalzahl. Geben Sie dann eine Zahl ein, die den minimalen gültigen Wert für das Feld darstellt.  
  
       - **Wert an ein Feld binden**. Wählen Sie ein Feld aus der Liste aus, das als minimaler gültiger Wert verwendet wird.  
  
   - **Max.**. Legen Sie maximalen gültigen Wert für das Feld fest. Ähnlich wie beim Min.-Wert können Sie einen statischen Wert binden, den Sie eingeben, oder den Wert an ein vorhandenes Feld binden, wie zuvor beschrieben. In diesem Beispiel ist **An statischen Wert binden** **Währung** und der maximale Wert, der eingegeben werden kann, ist **1 Milliarde**.  
  
   - **Schritt**. Stellt die Einheit für das Erhöhen oder Verringern dar, wenn vom aktuellen Wert abgezogen oder zu diesem hinzugefügt wird. Beispielsweise können Sie für den Budgetbetrag 100 Dollar Erhöhung\Verringerung auswählen.  
  
   - **Standardsteuerelement ausblenden**. Durch die Auswahl der Option wird die Komponente ausgeblendet. Also werden weder die Komponente noch die Daten in einem der Clients angezeigt, die diese benutzerdefinierte Komponente nicht unterstützen.   
  
8. Klicken Sie auf **OK**, um die Seite "Feldeigenschaften" zu schließen.  
  
9. Zum Aktivieren der Anpassung klicken Sie auf dem Entitätsformular auf **Speichern** und dann auf **Veröffentlichen**.  
  
10. Klicken Sie auf **Speichern und schließen**, um den Formular-Editor zu schließen.  
  
## <a name="add-custom-component-to-an-entity"></a>Fügen Sie die Komponente einer Entität hinzu

Um eine benutzerdefinierte Komponente wie die Daten-Satz-Komponente oder eine einfache Tabellenkomponente einem Raster oder einer Ansicht hinzuzufügen, führen Sie die folgenden Schritte aus:

  - Navigieren Sie zu **Einstellungen > Anpassungen** und klicken Sie auf **System anpassen**.
  - Klicken Sie auf den Pfeil neben der Registerkarte **Entitäten** und wählen Sie die Entität aus, die Sie der benutzerdefinierten Komponente hinzufügen möchten. 
  - Klicken Sie auf die Registerkarte **Steuerelemente** und auf **Steuerelement hinzufügen**.
  - Auf der Seite "Steuerelement hinzufügen" wählen Sie die Komponente aus, die Sie möchten, z. B. die Komponente "Einfache Tabelle", und wählen dann **Hinzufügen** aus.
  - Wählen Sie den Client aus, auf dem die Komponente erscheinen soll.


## <a name="see-the-custom-component-in-action"></a>Das benutzerdefinierte Komponente in Aktion  

 Öffnen Sie einen Datensatz, der das Feld mit der benutzerdefinierten Komponente enthält, z. B. das Geschäftschance-Feld aus dem vorherigen Beispiel, und zeigen Sie an, wie das Feld sich geändert hat. Das Feld wird jetzt als Schiebreglerkomponente statt als Textfeld gerendert.  

### <a name="see-also"></a>Siehe auch

[Implementieren von Komponenten in TypeScript](implementing-controls-using-typescript.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](overview.md)