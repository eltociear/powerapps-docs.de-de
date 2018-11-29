---
title: 'Grundlegendes zu Dashboards: Dashboardkomponenten und FormXML (modellgestützte Apps) | Microsoft Docs'
description: 'Dashboards sind eine der unterschiedlichen Arten von Formularen in modellgestützten Apps. Sie können das Attribut SystemForm.Typ oder UserForm.Type verwenden, um zu ermitteln, ob das Formular ein Dashboard ist.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="understand-dashboards-dashboard-components-and-formxml"></a>Grundlegendes zu Dashboards: Dashboardkomponenten und FormXML

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/customize-dev/understand-dashboards-dashboard-components-formxml -->

Dashboards sind eine der unterschiedlichen Arten von Formularen in modellgestützten Apps. Sie können das Attribut `SystemForm.Type` oder `UserForm.Type` verwenden, um zu ermitteln, ob das Formular ein Dashboard ist. Ein Formular vom Typ Dashboard besitzt den Eigenschaftswert "0 ".  

 Die Definition des Formularinhalts und der Präsentation wird im FormXML gespeichert. Weitere Informationen: [Formular-XML-Schema](form-xml-schema.md)  

 Für Beispiel-FormXML-Zeichenfolgen für unterschiedliche Arten von Dashboards siehe [Beispiel-Dashboards](sample-dashboards.md).  

<a name="DashboardComponents"></a>   
## <a name="dashboard-components"></a>Dashboardkomponenten  
 Ein Dashboard kann Diagramme, Raster, IFRAMEs oder Webressourcen enthalten. Standardmäßig kann ein einzelnes Dashboard bis zu sechs dieser Komponenten enthalten.  

<!-- In the [!INCLUDE[pn_dynamics_crm](../../includes/pn-dynamics-crm.md)] on-premises version, you can change the number of components to be displayed on a dashboard using [!INCLUDE[pn_PowerShell](../../includes/pn-powershell.md)]. More information: [Set the Number of Dashboard Controls](understand-dashboards-dashboard-components-formxml.md#set_controls_limit)-->

<!--[!INCLUDE[cc_sdk_onpremises_note](../../includes/cc-sdk-onpremises-note.md)]-->

### <a name="charts"></a>Diagramme  
 Ein organisationseigenes Dashboard kann nur organisationseigene Diagramme enthalten. Allerdings kann ein Dashboard im Besitz eines Benutzers Diagramme im Besitz des Benutzers sowie im Besitz der Organisation enthalten. Weitere Informationen [Diagramme (Visualisierungen) für modellgestützte Apps](view-data-with-visualizations-charts.md)  

### <a name="grids"></a>Raster  
 Raster rufen Daten aus Abfragen (Ansichten) in modellgestützten Apps ab. Ein Dashboard im Besitz der Organisation kann nur die Raster enthalten, die Daten aus gespeicherten Abfragen abrufen. Ein Dashboard im Besitz eines Benutzers kann jedoch Raster enthalten, die Daten aus Benutzerabfragen und gespeicherten Abfragen abrufen. Weitere Informationen: [SavedQuery-Entität](../common-data-service/reference/entities/savedquery.md) 

### <a name="iframes"></a>IFRAMEs  
 Wenn Sie einem Dashboard im Besitz der Organisation IFRAMEs hinzufügen, können Sie angeben, ob frameübergreifendes Skripting beschränkt oder erlaubt werden soll. Dazu müssen Sie die Parameter `<Security>` im IFRAME-Steuerelement im FormXML verwenden. Für Dashboards im Besitz des Benutzers ist jedoch frameübergreifendes Skripting für iFrames begrenzt und kann nicht geändert werden. Wenn Sie versuchen, ein Dashboard im Besitz eines Benutzers zu erstellen, das einen IFRAME mit aktiviertem frameübergreifendem Skripting enthält, wird eine Fehlermeldung angezeigt.  

### <a name="web-resources"></a>Webressourcen  
 Nur formularfähige Webressourcen können einem Dashboard hinzugefügt werden. Obwohl diese Einschränkung angewendet wird, wenn Sie eine Webressource mit dem Dashboard-Designer in der Webanwendung hinzufügen, wird eine derartige Einschränkung nicht angewendet, wenn eine Webressource zu einem Dashboard mithilfe des SDK hinzugefügt wird. Weitere Informationen: [Webressourcen für modellgestützte Apps](web-resources.md)

<a name="DashboardComponentsandFormXML"></a>   
## <a name="dashboard-components-and-formxml-elements"></a>Dashboardkomponenten und FormXML-Elemente  
 Die Dashboardkomponenten werden in modellgestützten Apps anhand der im FormXML angegebenen Werte angezeigt. Das folgende Bild zeigt ein Beispiel eines Dashboards. Jedes Dashboard kann mehrere Registerkarten enthalten. Registerkarten sind ein vertikaler Stapel, der den Textkörper des Dashboards teilt, und können erweitert oder reduziert werden. Eine Registerkarte kann mehrere Abschnitte enthalten. Abschnitte ermöglichen das Gruppieren und Anordnen von Dashboardkomponenten. 

 <!-- TODO: image not found ![Dashboard components layout](../media/crm-v5s-dashboards-components.png "Dashboard components layout")   -->

<a name="SupportedFormXMLElements"></a>   
## <a name="formxml-elements-supported-for-dashboards"></a>Für Dashboards unterstützte FormXML-Elemente  
 Obwohl Dashboards ein Formulartyp sind, werden nicht alle FormXML-Elemente und -Attribute von Dashboards unterstützt. Die folgende Tabelle enthält Informationen zu den Elementen, untergeordneten Elementen und Attributen von FormXML, die von Dashboards unterstützt werden.

 Für Beispiel-FormXML für unterschiedliche Arten von Dashboards siehe [Beispiel-Dashboards](sample-dashboards.md).  


|    Element     |                                                                                                                                                                                                                          Untergeordnete Elemente                                                                                                                                                                                                                          |                                          Elementattribute                                          |
|----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------|
|    `<form>`    |                                                                                                                                                                                                                             `<tabs>`                                                                                                                                                                                                                             |                                                  -                                                   |
|    `<tabs>`    |                                                                                                                                                                                                                             `<tab>`                                                                                                                                                                                                                              |                                                  -                                                   |
|    `<tab>`     |                                                                                                                                                                                                               -   `<labels>`<br />-   `<columns>`                                                                                                                                                                                                                | -   ID<br />-   Name<br />-   Erweitert<br />-   verticallayout<br />-   showlabel<br />-   locklevel |
|   `<labels>`   |                                                                                                                                                                                                                            `<label>`                                                                                                                                                                                                                             |                                                  -                                                   |
|   `<label>`    |                                                                                                                                                                                                                                -                                                                                                                                                                                                                                 |                                -   Beschreibung<br />-   languagecode                                 |
|  `<columns>`   |                                                                                                                                                                                                                            `<column>`                                                                                                                                                                                                                            |                                                  -                                                   |
|   `<column>`   |                                                                                                                                                                                                                           `<sections>`                                                                                                                                                                                                                           |                                                width                                                 |
|  `<sections>`  |                                                                                                                                                                                                                           `<section>`                                                                                                                                                                                                                            |                                               addedby                                                |
|  `<section>`   |                                                                                                                                                                                                                 -   `<labels>`<br />-   `<rows>`                                                                                                                                                                                                                 |              -   ID<br />-   Name<br />-   showlabel<br />-   showbar<br />-   columns               |
|    `<rows>`    |                                                                                                                                                                                                                             `<row>`                                                                                                                                                                                                                              |                                               addedby                                                |
|    `<row>`     |                                                                                                                                                                                                                             `<cell>`                                                                                                                                                                                                                             |                                               addedby                                                |
|    `<cell>`    |                                                                                                                                                                                                               -   `<labels>`<br />-   `<control>`                                                                                                                                                                                                                |      -   auto<br />-   addedby<br />-   ID<br />-   showlabel<br />-   rowspan<br />-   colspan      |
|  `<control>`   |                                                                                                                                                                                                                          `<parameters>`                                                                                                                                                                                                                          |                                       -   ID<br />-   classid                                        |
| `<parameters>` | -   `<Url>`<br />-  `<PassParameters>`<br />-   `<Security>`<br />-   `<Scrolling>`<br />-   `<Border>`<br />-   `<ViewIds>`<br />-   `<ViewId>`<br />-   `<IsUserView>`<br />-   `<IsUserChart>`<br />-   `<TargetEntityType>`<br />-   `<AutoExpand>`<br />-   `<RecordsPerPage>`<br />-   `<EnableQuickFind>`<br />-   `<EnableJumpBar>`<br />-   `<EnableChartPicker>`<br />-   `<EnableViewPicker>`<br />-   `<ChartGridMode>`<br />-   `<VisualizationId>` |                                                  -                                                   |

<a name="set_controls_limit"></a>   
## <a name="set-the-number-of-dashboard-controls"></a>Festlegen der Anzahl von Dashboard-Steuerelementen  
 Sie können Windows PowerShell verwenden, um die Anzahl der Dashboard-Steuerelemente anzupassen, wie hier beschrieben. Der maximale Wert ist 20.  

#### <a name="to-retrieve-and-set-the-dashboard-limit"></a>Abrufen und Festlegen der Dashboardgrenze  

1. Öffnen Sie ein Windows PowerShell-Befehlsfenster.  

2. Fügen Sie das Windows PowerShell-Snap-In für modellgestützte Apps hinzu:  

   ```powershell  
   Add-PSSnapin Microsoft.Crm.PowerShell  
   ```  

3. Rufen Sie die aktuelle Einstellung ab:  

   ```powershell  
   $setting = Get-CrmSetting -SettingType DashboardSettings  
   ```  

4. Ändern Sie die aktuelle Einstellung:  

   ```powershell  
   $setting.MaximumControlsLimit = 5  
   ```  

   ```powershell  
   Set-CrmSetting -Setting $setting  
   ```  

### <a name="see-also"></a>Siehe auch  
 [Dashboards](analyze-data-with-dashboards.md)   
 [Aktionen für Dashboards](actions-dashboards.md)   
 [Erstellen eines Dashboards](create-dashboard.md)   
