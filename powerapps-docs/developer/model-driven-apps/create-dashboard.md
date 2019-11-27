---
title: Erstellen eines Dashboards (modellgesteuerte Anwendungen) | Microsoft Docs
description: Sie können ein Dashboard im Besitz der Organisation erstellen, indem Sie die Common Data Service-Webdienste (SDK) verwenden oder das Entitätsformular in Common Data Service anpassen, indem Sie die customizations.xml-Datei bearbeiten.
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
ms.assetid: da41f997-1f61-7ea8-db83-5d670d708d67
author: JimDaly
ms.author: jdaly
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8dfbf28255f3e36d6b5fcb28a52bf02f738b9860
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748472"
---
# <a name="create-a-dashboard"></a>Erstellen eines Dashboards

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/create-dashboard -->

Sie können ein Dashboard im Besitz der Organisation erstellen, indem Sie das Common Data Service verwenden oder das Entitätsformular in Common Data Service anpassen, indem Sie die customizations.xml-Datei bearbeiten.  
  
> [!NOTE]
>  Einige Dashboards, die unter Verwendung von SDK oder durch Anpassung des Entitätsformulars erstellt wurden, werden vom Dashboard-Designer in der Webanwendung nicht unterstützt. Weitere Informationen finden Sie unter [Einschränkungen: Dashboards mithilfe des SDK oder durch Formularanpassung erstellen](#Limitations) unten in diesem Thema.  
  
 Bevor Sie ein Dashboard erstellen, sollten Sie Folgendes erwägen:  
  
- **Typ des Dashboards**: Wenn die Dashboards in der gesamten Organisation verfügbar sein sollen und Sie die Zugriffsebenen nicht genauer verwalten möchten, sollten Sie ein Dashboard im Besitz einer Organisation erstellen. Wenn Sie sich jedoch über die Zugriffsrechte und die Sicherheit Ihres dashboards Gedanken machen, sollten Sie überlegen, ein Dashboard im Besitz eines Benutzers zu erstellen, bei der Sie eine größere Kontrolle darüber haben, wer darauf zugreifen kann.  
  
     Um die Dashboards im Besitz der Organisation zu erstellen, müssen Sie die Rolle "Systemanpasser" oder "Systemadministrator" besitzen.  
  
- **Dashboardlayout**: Beim Erstellen von Dashboards müssen Sie die FormXML-Datei verwenden, um die Dashboardkomponenten das Layout zu definieren. Informationen zum Arbeiten mit FormXML, um ein Dashboard zu definieren, finden Sie unter [Dashboardkomponenten und FormXML-Elemente](understand-dashboards-dashboard-components-formxml.md#DashboardComponentsandFormXML). Einige Beispiel-FormXML-Dateien unterschiedlicher Typen von Dashboards finden Sie unter [Beispiel-Dashboards](sample-dashboards.md).  
  
<a name="UsingSDK"></a>   
## <a name="create-a-dashboard-by-using-the-sdk"></a>Erstellen eines Dashboards mithilfe von SDK  
 Um ein Dashboard zu erstellen, erstellen Sie eine Instanz von `SystemForm` für ein Dashboard im Besitz der Organisation, oder `UserForm` für ein Dashboard im Besitz des Benutzers. Im folgenden Beispiel wird gezeigt, wie ein Dashboard im Besitz der Organisation erstellt wird.  
  
 ```csharp
 //This is the language code for U.S. English. If you are running this code
//in a different locale, you will need to modify this value.
int languageCode = 1033;

//We set up our dashboard and specify the FormXml. Refer to the
//FormXml schema in the Microsoft Dynamics CRM SDK for more information.
SystemForm dashboard = new SystemForm
{
    Name = "Sample Dashboard",
    Description = "Sample organization-owned dashboard.",
    FormXml = String.Format(@"<form>
            <tabs>
                <tab name='Test Dashboard' verticallayout='true'>
                    <labels>
                        <label description='Sample Dashboard' languagecode='{0}' />
                    </labels>
                    <columns>
                        <column width='100%'>
                            <sections>
                                <section name='Information Section'
                                    showlabel='false' showbar='false'
                                    columns='111'>
                                    <labels>
                                        <label description='Information Section'
                                            languagecode='{0}' />
                                    </labels>
                                    <rows>
                                        <row>
                                            <cell colspan='1' rowspan='10' 
                                                showlabel='false'>
                                                <labels>
                                                    <label description='Top Opportunitiess - 1'
                                                    languagecode='{0}' />
                                                </labels>
                                                <control id='TopOpportunities'
                                                    classid='{{E7A81278-8635-4d9e-8D4D-59480B391C5B}}'>
                                                    <parameters>
                                                        <ViewId>{1}</ViewId>
                                                        <IsUserView>false</IsUserView>
                                                        <RelationshipName />
                                                        <TargetEntityType>opportunity</TargetEntityType>
                                                        <AutoExpand>Fixed</AutoExpand>
                                                        <EnableQuickFind>false</EnableQuickFind>
                                                        <EnableViewPicker>false</EnableViewPicker>
                                                        <EnableJumpBar>false</EnableJumpBar>
                                                        <ChartGridMode>Chart</ChartGridMode>
                                                        <VisualizationId>{2}</VisualizationId>
                                                        <EnableChartPicker>false</EnableChartPicker>
                                                        <RecordsPerPage>10</RecordsPerPage>
                                                    </parameters>
                                                </control>
                                            </cell>
                                            <cell colspan='1' rowspan='10' 
                                                showlabel='false'>
                                                <labels>
                                                    <label description='Top Opportunities - 2'
                                                    languagecode='{0}' />
                                                </labels>
                                                <control id='TopOpportunities2'
                                                    classid='{{E7A81278-8635-4d9e-8D4D-59480B391C5B}}'>
                                                    <parameters>
                                                        <ViewId>{1}</ViewId>
                                                        <IsUserView>false</IsUserView>
                                                        <RelationshipName />
                                                        <TargetEntityType>opportunity</TargetEntityType>
                                                        <AutoExpand>Fixed</AutoExpand>
                                                        <EnableQuickFind>false</EnableQuickFind>
                                                        <EnableViewPicker>false</EnableViewPicker>
                                                        <EnableJumpBar>false</EnableJumpBar>
                                                        <ChartGridMode>Grid</ChartGridMode>
                                                        <VisualizationId>{2}</VisualizationId>
                                                        <EnableChartPicker>false</EnableChartPicker>
                                                        <RecordsPerPage>10</RecordsPerPage>
                                                    </parameters>
                                                </control>
                                            </cell>
                                        </row>
                                        <row />
                                        <row />
                                        <row />
                                        <row />
                                        <row />
                                        <row />
                                        <row />
                                        <row />
                                        <row />
                                    </rows>
                                </section>
                            </sections>
                        </column>
                    </columns>
                </tab>
            </tabs>
        </form>",
    languageCode,
    defaultOpportunityQuery.SavedQueryId.Value.ToString("B"),
    visualization.SavedQueryVisualizationId.Value.ToString("B")),
    IsDefault = false
};
_dashboardId = _serviceProxy.Create(dashboard);
 ``` 
  
 Ein vollständiges Beispiel finden Sie unter [Beispiel: Erstellen, Abrufen, Aktualisieren und Löschen eines Dialogs](/dynamics365/customer-engagement/developer/customize-dev/sample-create-retrieve-update-delete-dashboard). Ein Beispiel des Erstellens eines benutzereigenenn Dashboards und dessen Zuordnung an einen anderen Benutzer finden Sie unter [Beispiel: Zuordnung eines benutzereigenenn Dashboards an einen anderen Benutzer](/dynamics365/customer-engagement/developer/customize-dev/sample-assign-user-owned-dashboard-another-user).  <!-- TODO relevant powerapps repo topic must be linked> 
  
<a name="UsingFormCustomization"></a>   
## <a name="create-an-organization-owned-dashboard-by-customizing-the-entity-form"></a>Erstellen eines Dashboards im Besitz eines Benutzers durch Anpassen des Entitätsformulars  
 Die customizations.xml-Datei, die mit einer nicht verwalteten Lösung exportiert wird, enthält Definitionen für Entitätsformulare und Dashboards. Sie können die customizations.xml-Datei ändern oder hinzufügen, um ein Dashboard hinzuzufügen oder zu aktualisieren.  
  
#### <a name="create-a-dashboard-by-customizing-an-entity-form"></a>Erstellen eines Dashboards durch Anpassen eines Entitätsformulars  
  
1. Melden Sie sich bei Common Data Service an.  
  
2. Exportieren Sie eine Lösung. Informationen dazu finden Sie unter [Exportierung, Vorbereitung zum Bearbeiten und Importierung des Menübands](export-prepare-edit-import-ribbon.md).  
  
3. Suchen Sie die Datei customizations.xml im Ordner "Exportierte Lösungen", und öffnen Sie sie zum Bearbeiten.  
  
4. Navigieren Sie zum Ende des Dashboardbereichs in der customizations.xml-Datei, indem Sie nach dem folgenden Tag suchen: `</Dashboards>`.  
  
5. Vor dem `</Dashboards>`-tag fügen Sie Folgendes hinzu, um ein neues Dashboard zu definieren:  
  
   ```xml  
   <Dashboard>  
      <LocalizedNames>  
         <LocalizedName description="Dashboard_Name" languagecode="1033" />  
      </LocalizedNames>     
      <IsCustomizable>1</IsCustomizable>  
      <IsDefault>0</IsDefault>  
      <FormXml>  
         <forms type="dashboard">  
   *** Dashboard definition goes here. *** // See “Sample Dashboards” topic for the FormXML content to be used here.  
         </forms>  
      </FormXml>  
   </Dashboard>  
   ```  
  
6. Speichern der customizations.xml-Datei.  
  
7. Importieren Sie die ZIP-Datei als eine Lösung in Common Data Service. Weitere Informationen: [Exportieren, Vorbereiten der Bearbeitung und Importieren des Menübands](export-prepare-edit-import-ribbon.md).  
  
<a name="Limitations"></a>   

## <a name="limitations-creating-dashboards-by-using-the-sdk-or-through-form-customization"></a>Einschränkungen: Erstelen von Dashboards mithilfe des SDK oder durch Formularanpassung  

 Bestimmte Dashboards, die unter Verwendung von Common Data Service oder durch Formularanpassung erstellt wurden, werden vom Dashboard-Designer in der Webanwendung nicht unterstützt. Vermeiden Sie Folgendes beim Erstellen oder Ändern eines Dashboards mithilfe des SDK oder durch Formularanpassung.  
  
### <a name="general"></a>Allgemein  
  
- **Problem**: Sie können ein Dashboard erstellen, das eine Registerkarte enthält, ohne dass ein Abschnitt in der FormXML-Datei definiert wird.  
  
  **Abschluss**: Achten Sie darauf, dass Sie ein Dashboard erstellen, bei dem mindestens ein Abschnitt für jede der Registerkarte in der FormXML-Datei definiert ist.  
  
- **Problem**: Sie können ein Dashboard erstellen, das nicht die gleiche Anzahl von `<row>`-Elementen für einen Abschnitt enthält, wie in der `rowspan`-Eigenschaft eines `<cell>`-Elements des Abschnitt in der FormXML-Datei angegeben. Idealerweise müssen der`rowspan`-Eigenschaftswert eines `<cell>`-Elements und die Anzahl der `<row>`-Elemente in einem Abschnitt identisch sein.  
  
  **Lösung**: Achten Sie darauf, dass Sie ein Dashboard erstellen, das die gleiche Anzahl von `<row>`-Elementen für einen Abschnitt enthält, wie in der `rowspan`-Eigenschaft eines `<cell>`-Elements in dem Abschnitt angegeben ist.  
  
### <a name="grids"></a>Raster  
 **Problem**: Sie können ein Dashboard erstellen, das Raster enthält, bei denen der `<AutoExpand>`-Parameterwert für das Raster auf `Auto` gesetzt ist.  
  
 **Lösung**: Achten Sie darauf, dass Sie den `<AutoExpand>`-Parameterwert als `Fixed` für die Raster in der FormXML-Datei beim Erstellen eines Dashboards angeben.  
  
### <a name="iframes"></a>IFRAMEs  
 **Problem**: Sie können ein Dashboard erstellen, das einen IFRAME enthält. Dies ist der Fall, wenn Sie keinen Wert für den `<Url>`-Parameter für das IFRAME-Steuerelement in der FormXML-Datei angeben.  
  
 **Lösung**: Achten Sie darauf, dass Sie einen wert für den `<Url>`-Parameter angeben, während Sie einen IFRAME in der FormXML-datei erstellen.  
  
### <a name="see-also"></a>Siehe auch  
 [Dashboards](analyze-data-with-dashboards.md)   
 [Nutzung der FormXML-Datei für Dashboards](understand-dashboards-dashboard-components-formxml.md)   
 [Aktionen für Dashboards](actions-dashboards.md)   
 [Beispiel-Dashboards](sample-dashboards.md)   
 [Beispiel: Ein Dashboard erstellen, abrufen, aktualisieren und löschen (EAAL)](/dynamics365/customer-engagement/developer/customize-dev/sample-create-retrieve-update-delete-dashboard)   <!-- TODO relevant powerapps repo topic must be linked-->
 [Anpassen von Entitätsformularen](customize-entity-forms.md)
