---
title: Hinzufügen der Registerkarte „Dokumente” zum Hauptformular für eine Entität | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die Registerkarte „Dokumente” zum Hauptformular für eine Entität hinzufügen.
s.custom: ''
ms.date: 09/05/2019
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: Mattp123
ms.assetid: ''
caps.latest.revision: ''
ms.author: matp
manager: kvivek
search.audienceType:
- customizer
search.app:
- D365CE
ms.openlocfilehash: f245d4c2a9272d10f7aefa2b2847adba5ce0f6e5
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2860805"
---
# <a name="add-the-sharepoint-documents-tab-to-the-main-form-for-an-entity"></a>Hinzufügen der Registerkarte „SharePoint-Dokumente” zum Hauptformular für eine Entität
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Wenn Sie eine Registerkarte zu einem Hauptformular für eine Entität zum Anzeigen von SharePoint-Dokumenten hinzufügen, können Benutzer die Integrationsfeatures von SharePoint finden und verwenden, die in einer modellgesteuerten App verfügbar sind. 

![Registerkarte für Dokumentdateien](media/document-files-tab.png)

> [!IMPORTANT]
> Sie müssen die Dokumentenverwaltung aktivieren, um dieses Feature nutzen zu können. Weitere Informationen: [Ihre Dokumente mit SharePoint verwalten](/dynamics365/customer-engagement/admin/manage-documents-using-sharepoint)

## <a name="add-the-documents-tab-in-the-formxml"></a>Hinzufügen der Registerkarte „Dokumente” im FormXML 
1.  Erstellen Sie eine neue Lösung. Melden Sie sich bei Power Apps an, wechseln Sie zu **Lösungen**, wählen Sie die Option **Neue Lösung**, und geben Sie dann die erforderlichen und optionalen Informationen ein. Weitere Informationen: [Erstellen einer Lösung](../common-data-service/create-solution.md)
2. Fügen Sie die Entität zu der Lösung hinzu, in der Sie die Registerkarte „Dokumente” auf dem Hauptformular hinzufügen möchten. Alle standardmäßigen und benutzerdefinierten Entitäten werden unterstützt. Weitere Informationen: [Hinzufügen einer vorhandenen Komponente zu einer Lösung](/powerapps/maker/common-data-service/use-solution-explorer#add-an-existing-component-to-a-solution)
3. Schließen Sie das Formular für die Entität in der Lösung ein, z. B. das Hauptformular für die Konto-Entität. Wählen Sie neben der Entität die Option **...** und dann **Bearbeiten** aus. Wählen Sie die Registerkarte **Formulare** aus. Wenn das gewünschte Formular fehlt, fügen sie es hinzu.   

4. Fügen Sie eine einspaltige Registerkarte zum Hauptformular hinzu. Wählen Sie dazu im Formulardesigner einen Bereich im Formularcanvas aus, wählen Sie **Komponente hinzufügen** und dann **Registerkarte mit 1 Spalte** aus.  
   ![Eine einspaltige Registerkarte einfügen](media/insert-one-column-tab.png)

5. Wählen Sie im Formulardesigner **Neue Registerkarte** im Formularcanvas aus, wählen Sie **Feld hinzufügen**, und fügen Sie dann ein Feld wie z. B. *Address 1: Ort* im linken Bereich hinzu. Sie können einen beliebigen Text oder ein beliebiges numerisches Feld für die Registerkarte verwenden. ![Hinzufügen eines Felds zur Registerkarte](media/add-field-to-tab.png)
6. Benennen Sie die Registerkartenbeschriftung um. Wählen Sie dazu die Option **Neue Registerkarte** aus, und ersetzen Sie im rechten Eigenschaftenbereich **Neue Registerkarte** durch etwas Aussagekräftigeres wie z. B. *Dateien*.
7. Wählen Sie **Speichern** und **Veröffentlichen** aus, und schließen Sie dann den Formulardesigner. 
8. Wählen Sie auf der Startseite von Power Apps Maker die Option **Lösungen**, und wählen Sie die Lösung aus. Wählen Sie dann **Exportieren**, um die Lösung als nicht verwaltete Lösung zu exportieren. Weitere Informationen: [Exportieren von Lösungen](../common-data-service/import-update-export-solutions.md#export-solutions) 
9. Extrahieren Sie die Lösung, und öffnen Sie die Datei "customization.xml" mit einem XML- oder Texteditor. 
10. Suchen Sie in der Datei "customization.xml" nach **label description="Dateien"** (oder wie auch immer Sie die Registerkartenbeschriftung im vorherigen Schritt benannt haben).
11. Führen Sie einen Bildlauf zum Element control id="*Feldname*" durch, z. B. **control id="Adresse1_Ort"**, und ersetzen Sie das gesamte Element durch das [XML-Beispiel](#xml-sample-for-adding-the-documents-tab-to-a-form) in diesem Thema. 

    > [!div class="mx-imgBorder"] 
    > ![](media/form-xml.png "XML sample insertion point")

12. Nehmen Sie diese Änderungen am XML-Beispiel vor. 
    
     a. Suchen Sie das Element **RelationshipName**, und ersetzen Sie es durch den Schemanamen, der als *entityLogicalName*_SharePointDocument angezeigt wird. Zum Beispiel lautet für die Konten-Entität der Schemaname für die Beziehung "Account_SharePointDocument". Dies ist der Schemaname für das XML-Beispiel in diesem Thema. Um den Namen für eine andere Entität zu finden, wechseln Sie zu **Einstellungen** > **Anpassungen** > **System anpassen** > **Entitäten**. Wählen Sie die Entität aus, und wählen Sie dann **1:n-Beziehungen**. Suchen Sie **Verknüpfte Entität** vom Typ **SharePointDocument**. 

      ![Kontobeziehung SharePoint-Dokument](media/account-sharepointdocument.png)

     b. Erstellen Sie einen Globally Unique Identifier (GUID), und ersetzen Sie den vorhandenen GUID **uniqueid** im **Steuerelement**, das Sie im vorherigen Schritt eingefügt haben, unter Beibehaltung der geschweiften Klammern {}.  
       ![Eindeutige ID des Steuerelements](media/control-unique-id.png) c. Speichern Sie die Änderungen an der Datei "customizations.xml". 
13. Öffnen Sie die Datei "solution.xml", und erhöhen Sie den Elementwert **Version**. Zum Beispiel von *1.1.0.0* in *1.2.0.0*. 
14. Verpacken Sie alle Lösungsdateien in einem komprimierten (gezippten) Ordner, und importieren Sie diesen in Ihre Umgebung. Wenn Sie eine Fehlermeldung erhalten, dass Sie die vorherige Lösung löschen müssen, tun Sie dies. Weitere Informationen: [Eine Lösung importieren und aktualisieren](../common-data-service/import-update-export-solutions.md) 

## <a name="xml-sample-for-adding-the-documents-tab-to-a-form"></a>XML-Beispiel zum Hinzufügen der Registerkarte "Dokumente" zu einem Formular
```xml
  <control id="DocumentSubGrid" classid="{E7A81278-8635-4d9e-8D4D-59480B391C5B}" indicationOfSubgrid="true" uniqueid="{9cd66b5c-8b7a-6433-c5a5-46a7245dd534}"> 
    <parameters> 
      <ViewId>{0016F9F3-41CC-4276-9D11-04308D15858D}</ViewId> 
      <IsUserView>false</IsUserView>         
      <RelationshipName>Account_SharepointDocument</RelationshipName>
      <TargetEntityType>sharepointdocument</TargetEntityType> 
      <AutoExpand>Fixed</AutoExpand> 
      <EnableQuickFind>false</EnableQuickFind> 
      <EnableViewPicker>true</EnableViewPicker> 
      <ViewIds /> 
      <EnableJumpBar>false</EnableJumpBar> 
      <ChartGridMode>Grid</ChartGridMode> 
      <VisualizationId /> 
      <IsUserChart>false</IsUserChart> 
      <EnableChartPicker>false</EnableChartPicker> 
      <RecordsPerPage>10</RecordsPerPage> 
      <HeaderColorCode>#F3F3F3</HeaderColorCode> 
    </parameters> 
  </control> 
```

### <a name="see-also"></a>Siehe auch
[Ihre Dokumente mit SharePoint verwalten](/dynamics365/customer-engagement/admin/manage-documents-using-sharepoint)