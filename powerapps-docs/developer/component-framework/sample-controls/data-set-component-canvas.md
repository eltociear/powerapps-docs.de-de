---
title: DataSet Rasterkomponente für Canvas-Anwendungen | Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 02/18/2020
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 356561d0-a36b-4b93-8b76-3e1abf9414e9
ms.openlocfilehash: 44cad6fe7eafb457db7b2d5d3204612a42944a02
ms.sourcegitcommit: 5b6e6b41a3fc4d7f1aea46ec66c086b784efacac
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/03/2020
ms.locfileid: "3095484"
---
# <a name="implementing-data-set-component-for-canvas-apps"></a>Implementierung einer Datensatzkomponente für Canvas-Anwendungen

Dieses Beispiel zeigt, wie man eine Datensatzkomponente für Canvas-Anwendungen erstellt. Die Datensatzkomponente zeigt auch, wie man die Datensatz-API-Methoden verwendet, um Spaltenmetadaten zu erhalten, Daten aufzuzeichnen, durch Daten zu blättern und die Navigation zu handhaben. 

 Sie können die Beispielkomponente von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/component-framework/TS_PropertySetTableControl) herunterladen.

> [!div class="mx-imgBorder"]
> ![Datensatzrastersteuerelement](../media/data-set-grid-control-canvas.png)

## <a name="available-for"></a>Verfügbar für 

Modellgesteuerte Anwendungen und Canvas-Anwendungen (öffentliche Vorschau).

> [!NOTE]
> Einige der Dataset-API-Methoden werden in Canvas-Anwendungen immer noch nicht unterstützt. Siehe, [individuelle API-Dokumentation](../reference/index.md) für Details zur Verfügbarkeit.
> Siehe [Datensatzkomponente für modellgesteuerte Anwendungen](data-set-grid-control.md), um mehr darüber zu erfahren, wie Datensatzkomponenten in modellgesteuerten Anwendungen implementiert werden.

## <a name="manifest"></a>Manifest 

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<manifest>
  <control namespace="PcfSample" constructor="TestDataSetCtrl" version="0.0.6" display-name-key="TestDataSetCtrl" description-key="TestDataSetCtrl description" control-type="standard" api-version="1.2.1">
    <data-set name="simpleTableGrid" display-name-key="Dataset_Display_Key">
      <property-set name="samplePropertySet" display-name-key="Property_Display_Key" description-key="Property_Desc_Key" of-type="SingleLine.Text" usage="bound" required="true"/>
      <property-set name="samplePropertySet2" display-name-key="Property_Display_Key2" description-key="Property_Desc_Key2" of-type="SingleLine.Text" usage="bound" required="true"/>
    </data-set>
    <resources>
      <code path="bundle.js" order="1"/>
      <css path="css/TestDataSetCtrl.css" order="1"/>
      <resx path="strings/TestDataSetCtrl.1033.resx" version="1.0.0"/>
    </resources>
    <built-by name="pac" version="1.1.6"/>
  </control>
</manifest>
```

## <a name="code"></a>Code 

```TypeScript
import {IInputs, IOutputs} from "./generated/ManifestTypes";
import DataSetInterfaces = ComponentFramework.PropertyHelper.DataSetApi;
type DataSet = ComponentFramework.PropertyTypes.DataSet;
// Define const here
const RowRecordId:string = "rowRecId";
// Style name of disabled buttons
const Button_Disabled_style =  "loadNextPageButton_Disabled_Style";
export class TSPropertySetTableControl implements ComponentFramework.StandardControl<IInputs, IOutputs> {
    private contextObj: ComponentFramework.Context<IInputs>;
    
    // Div element created as part of this control's main container
    private mainContainer: HTMLDivElement;
    // Table element created as part of this control's table
    private dataTable: HTMLTableElement;
    // Button element created as part of this control
    private loadNextPageButton: HTMLButtonElement;
    // Button element created as part of this control
    private loadPrevPageButton: HTMLButtonElement;
    private getValueResultLabel: HTMLLabelElement;
    private selectedRecord: DataSetInterfaces.EntityRecord;
    private selectedRecords: {[id: string]: boolean} = {};
    /**
     * Empty constructor.
     */
    constructor()
    {
    }
    /**
     * Used to initialize the control instance. Controls can kick off remote server calls and other initialization actions here.
     * Data-set values are not initialized here, use updateView.
     * @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to property names defined in the manifest, as well as utility functions.
     * @param notifyOutputChanged A callback method to alert the framework that the control has new outputs ready to be retrieved asynchronously.
     * @param state A piece of data that persists in one session for a single user. Can be set at any point in a controls life cycle by calling 'setControlState' in the Mode interface.
     * @param container If a control is marked control-type='standard', it will receive an empty div element within which it can render its content.
     */
    public init(context: ComponentFramework.Context<IInputs>, notifyOutputChanged: () => void, state: ComponentFramework.Dictionary, container:HTMLDivElement)
    {
        // Need to track container resize so that control could get the available width.
        // In Model-driven app, the available height won't be provided even this is true
        // In Canvas-app, the available height will be provided in context.mode.allocatedHeight
        context.mode.trackContainerResize(true);
        // Create main table container div.
        this.mainContainer = document.createElement("div");
        this.mainContainer.classList.add("SimpleTable_MainContainer_Style");
        this.mainContainer.id = "SimpleTableMainContainer";
        // Create data table container div.
        this.dataTable = document.createElement("table");
        this.dataTable.classList.add("SimpleTable_Table_Style");
        this.loadPrevPageButton = document.createElement("button");
        this.loadPrevPageButton.setAttribute("type", "button");
        this.loadPrevPageButton.innerText = context.resources.getString("TSPropertySetTableControl_LoadPrev_ButtonLabel");
        this.loadPrevPageButton.classList.add(Button_Disabled_style);
        this.loadPrevPageButton.classList.add("Button_Style");
        this.loadPrevPageButton.addEventListener("click", this.onLoadPrevButtonClick.bind(this));
        this.loadNextPageButton = document.createElement("button");
        this.loadNextPageButton.setAttribute("type", "button");
        this.loadNextPageButton.innerText = context.resources.getString("TSPropertySetTableControl_LoadNext_ButtonLabel");
        this.loadNextPageButton.classList.add(Button_Disabled_style);
        this.loadNextPageButton.classList.add("Button_Style");
        this.loadNextPageButton.addEventListener("click", this.onLoadNextButtonClick.bind(this));
        // Create main table container div. 
        this.mainContainer = document.createElement("div");
        // Adding the main table and loadNextPage button created to the container DIV.
        this.mainContainer.appendChild(this.createGetValueDiv());
        this.mainContainer.appendChild(this.loadPrevPageButton);
        this.mainContainer.appendChild(this.loadNextPageButton);
        this.mainContainer.appendChild(this.dataTable);
        this.mainContainer.classList.add("main-container");
        container.appendChild(this.mainContainer);
    }
/**
 * Called when any value in the property bag has changed. This includes field values, data-sets, global values such as container height and width, offline status, control metadata values such as label, visible, etc.
 * @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to names defined in the manifest, as well as utility functions
 */
public updateView(context: ComponentFramework.Context<IInputs>): void {
    this.contextObj = context;
    this.toggleLoadMoreButtonWhenNeeded(context.parameters.sampleDataSet);
    this.toggleLoadPreviousButtonWhenNeeded(context.parameters.sampleDataSet);
    
    if (!context.parameters.sampleDataSet.loading) {
        // Get sorted columns on View
        let columnsOnView = this.getSortedColumnsOnView(context);
        if (!columnsOnView || columnsOnView.length === 0) {
            return;
        }
        //calculate the width for each column
        let columnWidthDistribution = this.getColumnWidthDistribution(context, columnsOnView);
        //When new data is received, it needs to first remove the table element, allowing it to properly render a table with updated data
        //This only needs to be done on elements having child elements which is tied to data received from canvas/model ..
        while (this.dataTable.firstChild) {
            this.dataTable.removeChild(this.dataTable.firstChild);
        }
        this.dataTable.appendChild(this.createTableHeader(columnsOnView, columnWidthDistribution));
        this.dataTable.appendChild(this.createTableBody(columnsOnView, columnWidthDistribution, context.parameters.sampleDataSet));
        this.dataTable.parentElement!.style.height = (context.mode.allocatedHeight - 50) + "px";
    }
}
/**
 * It is called by the framework prior to a control receiving new data.
 * @returns an object based on nomenclature defined in manifest, expecting object[s] for property marked as â€œboundâ€ or â€œoutputâ€
 */
public getOutputs(): IOutputs {
    return {};
}
/**
     * Called when the control is to be removed from the DOM tree. Controls should use this call for cleanup.
 * i.e. cancelling any pending remote calls, removing listeners, etc.
 */
public destroy(): void {
}
private createGetValueDiv(): HTMLDivElement {
    const getValueDiv = document.createElement("div");
    const inputBox = document.createElement("input");
    const getValueButton = document.createElement("button");
    const resultText = document.createElement("label");
    const _this = this; 
    inputBox.id = "getValueInputBox";
    inputBox.placeholder = "select a row and enter the alias name";
    inputBox.classList.add("GetValueInput_Style");
    getValueButton.innerText = "GetValue";      
    getValueButton.onclick = () => {
        if (_this.selectedRecord) {
            resultText.innerText = _this.selectedRecord.getFormattedValue(inputBox.value);
        }
    }
    resultText.innerText = "Select a row first";
    resultText.classList.add("GetValueResult_Style");
    this.getValueResultLabel = resultText;
    getValueDiv.appendChild(inputBox);
    getValueDiv.appendChild(getValueButton);
    getValueDiv.appendChild(resultText);
    return getValueDiv;
}
/**
 * Get sorted columns on view, columns are sorted by DataSetInterfaces.Column.order
 * Property-set columns will always have order = -1.
 * In Model-driven app, the columns are ordered in the same way as columns defined in views.
 * In Canvas-app, the columns are ordered by the sequence fields added to control
 * Note that property set columns will have order = 0 in test harness, this is a bug.
 * @param context
 * @return sorted columns object on View
 */
private getSortedColumnsOnView(context: ComponentFramework.Context<IInputs>): DataSetInterfaces.Column[] {
    if (!context.parameters.sampleDataSet.columns) {
        return [];
    }
    let columns = context.parameters.sampleDataSet.columns;
    return columns;
}
/**
 * Get column width distribution using visualSizeFactor. 
 * In model-driven app, visualSizeFactor can be configured from view's settiong.
 * In Canvas app, currently there is no way to configure this value. In all data sources, all columns will have the same visualSizeFactor value.
 * Control does not have to render the control using these values, controls are free to display any columns with any width, or making column width adjustable.
 * However, these kind of configurations will be lost when leaving the page
 * @param context context object of this cycle
 * @param columnsOnView columns array on the configured view
 * @returns column width distribution
 */
private getColumnWidthDistribution(context: ComponentFramework.Context<IInputs>, columnsOnView: DataSetInterfaces.Column[]): string[] {
    let widthDistribution: string[] = [];
    // Considering need to remove border & padding length
    let totalWidth: number = context.mode.allocatedWidth;
    let widthSum = 0;
    columnsOnView.forEach(function (columnItem) {
        widthSum += columnItem.visualSizeFactor;
    });
    let remainWidth: number = totalWidth;
    columnsOnView.forEach(function (item, index) {
        let widthPerCell = "";
        if (index !== columnsOnView.length - 1) {
            let cellWidth = Math.round((item.visualSizeFactor / widthSum) * totalWidth);
            remainWidth = remainWidth - cellWidth;
            widthPerCell = cellWidth + "px";
        }
        else {
            widthPerCell = remainWidth + "px";
        }
        widthDistribution.push(widthPerCell);
    });
    return widthDistribution;
}
private createTableHeader(columnsOnView: DataSetInterfaces.Column[], widthDistribution: string[]): HTMLTableSectionElement {
    let tableHeader: HTMLTableSectionElement = document.createElement("thead");
    let tableHeaderRow: HTMLTableRowElement = document.createElement("tr");
    tableHeaderRow.classList.add("SimpleTable_TableRow_Style");
    columnsOnView.forEach(function (columnItem, index) {
        let tableHeaderCell = document.createElement("th");
        let innerDiv = document.createElement("div");
        innerDiv.classList.add("SimpleTable_TableCellInnerDiv_Style");
        innerDiv.style.maxWidth = widthDistribution[index];
        let columnDisplayName: string;
        if (columnItem.order < 0) {
            tableHeaderCell.classList.add("SimpleTable_TableHeader_PropertySet_Style");
            columnDisplayName = columnItem.displayName + "(propertySet)";
        } else {
            tableHeaderCell.classList.add("SimpleTable_TableHeader_Style");
            columnDisplayName = columnItem.displayName;
        }
        innerDiv.innerText = columnDisplayName;
        tableHeaderCell.appendChild(innerDiv);
        tableHeaderRow.appendChild(tableHeaderCell);
    });
    tableHeader.appendChild(tableHeaderRow);
    return tableHeader;
}
private createTableBody(columnsOnView: DataSetInterfaces.Column[], widthDistribution: string[], gridParam: DataSet): HTMLTableSectionElement {
    let tableBody: HTMLTableSectionElement = document.createElement("tbody");
    if (gridParam.sortedRecordIds.length > 0) {
        for (let currentRecordId of gridParam.sortedRecordIds) {
            let tableRecordRow: HTMLTableRowElement = document.createElement("tr");
            tableRecordRow.classList.add("SimpleTable_TableRow_Style");
            tableRecordRow.addEventListener("click", this.onRowClick.bind(this));
            // Set the recordId on the row dom, this is the simplest way to help us track which record has been clicked.
            tableRecordRow.setAttribute(RowRecordId, gridParam.records[currentRecordId].getRecordId());
            columnsOnView.forEach(function (columnItem, index) {
                let tableRecordCell = document.createElement("td");
                tableRecordCell.classList.add("SimpleTable_TableCell_Style");
                let innerDiv = document.createElement("div");
                innerDiv.classList.add("SimpleTable_TableCellInnerDiv_Style");
                innerDiv.style.width = widthDistribution[index];
                // Currently there is a bug in canvas preventing retrieving value using alias for property set columns.
                // In this sample, we use the column's actual attribute name to retrieve the formatted value to work around the issue
                // columnItem.alias should be used after bug is addressed
                innerDiv.innerText = gridParam.records[currentRecordId].getFormattedValue(columnItem.name);
                tableRecordCell.appendChild(innerDiv);
                tableRecordRow.appendChild(tableRecordCell);
            });
            tableBody.appendChild(tableRecordRow);
        }
    }
    else {
        let tableRecordRow: HTMLTableRowElement = document.createElement("tr");
        let tableRecordCell: HTMLTableCellElement = document.createElement("td");
        tableRecordCell.classList.add("No_Record_Style");
        tableRecordCell.colSpan = columnsOnView.length;
        tableRecordCell.innerText = this.contextObj.resources.getString("TSPropertySetTableControl_No_Record_Found");
        tableRecordRow.appendChild(tableRecordCell)
        tableBody.appendChild(tableRecordRow);
    }
    return tableBody;
}
/**
 * Row Click Event handler for the associated row when being clicked
 * @param event
 */
private onRowClick(event: Event): void {
    let rowElement = (event.currentTarget as HTMLTableRowElement);
    let rowRecordId = rowElement.getAttribute(RowRecordId);
    if (rowRecordId) {
        const record = this.contextObj.parameters.sampleDataSet.records[rowRecordId];
        this.selectedRecord = record;
        this.getValueResultLabel.innerText = "";
        this.selectedRecords[rowRecordId] = !this.selectedRecords[rowRecordId];
        const selectedRecordsArray = [];
        for (const recordId in this.selectedRecords) {
            if (this.selectedRecords[recordId]) {
                selectedRecordsArray.push(recordId);
            }
        }
        this.contextObj.parameters.sampleDataSet.setSelectedRecordIds(selectedRecordsArray);
        this.contextObj.parameters.sampleDataSet.openDatasetItem(record.getNamedReference());
    }
}
/**
 * Toggle 'LoadMore' button when needed
 */
private toggleLoadMoreButtonWhenNeeded(gridParam: DataSet): void {
    if (gridParam.paging.hasNextPage) {
        this.loadNextPageButton.disabled = false;
    } else if (!gridParam.paging.hasNextPage) {
        this.loadNextPageButton.disabled = true;
    }
}
/**
 * Toggle 'LoadMore' button when needed
 */
private toggleLoadPreviousButtonWhenNeeded(gridParam: DataSet): void {
    if (gridParam.paging.hasPreviousPage) {
        this.loadPrevPageButton.disabled = false;
    } else if (!gridParam.paging.hasPreviousPage) {
        this.loadPrevPageButton.disabled = true;
    }
}
/**
 * 'LoadMore' Button Event handler when load more button clicks
 * @param event
 */
private onLoadNextButtonClick(event: Event): void {
    this.contextObj.parameters.sampleDataSet.paging.loadNextPage();
    this.toggleLoadMoreButtonWhenNeeded(this.contextObj.parameters.sampleDataSet);
    this.toggleLoadPreviousButtonWhenNeeded(this.contextObj.parameters.sampleDataSet);
}
/**
 * 'LoadPrevious' Button Event handler when load more button clicks
 * @param event
 */
private onLoadPrevButtonClick(event: Event): void {
    this.contextObj.parameters.sampleDataSet.paging.loadPreviousPage();
    this.toggleLoadPreviousButtonWhenNeeded(this.contextObj.parameters.sampleDataSet);
    this.toggleLoadMoreButtonWhenNeeded(this.contextObj.parameters.sampleDataSet);
}
```

## <a name="resources"></a>Ressourcen

```css
 .PcfSample\.TestDataSetCtrl table.SimpleTable_Table_Style{
    border-spacing:0;
    text-align:left;
    width:100%;
    margin:0 auto;
    overflow: auto;
    height: 94%;
    display: block;
}
.PcfSample\.TestDataSetCtrl div.SimpleTable_TableCellInnerDiv_Style{
    word-wrap:break-word;
    overflow: hidden;
    text-overflow: ellipsis;
    line-height:1.5rem;
    max-height:1.5rem;
}
.PcfSample\.TestDataSetCtrl th.SimpleTable_TableHeader_Style{
    height:3rem;
    font-family:"Segoe UI Regular","Segoe UI", Arial, Sans-Serif;
    font-size:1rem;
    line-height:1.384;
    background-color:rgb(0, 0, 0);
    color: #fff;
    text-align:left;
    padding:0.5rem;
    border-left:.1rem solid rgba(255,255,255,.1);
    vertical-align: middle;
    width: 100vw;
}
.PcfSample\.TestDataSetCtrl tr.SimpleTable_TableRow_Style{
    height:3.5rem;
    background-color:#fff;
    color:#333
}
.PcfSample\.TestDataSetCtrl tr.SimpleTable_TableRow_Style:hover{
    cursor:pointer;
    border: solid thin rgb(59, 121, 183);
    background:rgba(160,160,160,.15);
}
.PcfSample\.TestDataSetCtrl td.SimpleTable_TableCell_Style {
    font-size:1rem;
    line-height:1.467;
    padding:0 .5rem;
    vertical-align: middle;
    width: 100vw;
    font-weight: bold;
    font-family: "Segoe UI Light";
    color: rgb(59, 121, 183);
}
.PcfSample\.TestDataSetCtrl td.No_Record_Style {
    text-align: center;
    padding: 20px;
}
.PcfSample\.TestDataSetCtrl table.SimpleIncrement_Button_Style {
    text-decoration: none;
    display: inline-block;
    font-size: 14px;
    margin: 4px 6px;
    cursor: pointer;
    color: white;
    border-radius: 10px;
    background-color: black;
    border: none;
    padding: 5px;
    text-align: center;
}
.PcfSample\.TestDataSetCtrl input.SimpleIncrement_Input_Error_Style{
    color: red;
}
.PcfSample\.TestDataSetCtrl button.LoadPageButton_Disabled_Style{
    background-color:#e5e5e5;
}
.PcfSample\.TestDataSetCtrl button.LoadPageButton_Style{
    background-color:#0099ff;
    font-size:1.3rem;
    font-weight:bold;
    text-align:center;
    width:100px;
    border:none;
    padding: 5px;
    margin: 5px;
}
```

```XML
<xsd:schema id="root" xmlns="" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">
    <xsd:import namespace="http://www.w3.org/XML/1998/namespace" />
    <xsd:element name="root" msdata:IsDataSet="true">
      <xsd:complexType>
        <xsd:choice maxOccurs="unbounded">
          <xsd:element name="metadata">
            <xsd:complexType>
              <xsd:sequence>
                <xsd:element name="value" type="xsd:string" minOccurs="0" />
              </xsd:sequence>
              <xsd:attribute name="name" use="required" type="xsd:string" />
              <xsd:attribute name="type" type="xsd:string" />
              <xsd:attribute name="mimetype" type="xsd:string" />
              <xsd:attribute ref="xml:space" />
            </xsd:complexType>
          </xsd:element>
          <xsd:element name="assembly">
            <xsd:complexType>
              <xsd:attribute name="alias" type="xsd:string" />
              <xsd:attribute name="name" type="xsd:string" />
            </xsd:complexType>
          </xsd:element>
          <xsd:element name="data">
            <xsd:complexType>
              <xsd:sequence>
                <xsd:element name="value" type="xsd:string" minOccurs="0" msdata:Ordinal="1" />
                <xsd:element name="comment" type="xsd:string" minOccurs="0" msdata:Ordinal="2" />
              </xsd:sequence>
              <xsd:attribute name="name" type="xsd:string" use="required" msdata:Ordinal="1" />
              <xsd:attribute name="type" type="xsd:string" msdata:Ordinal="3" />
              <xsd:attribute name="mimetype" type="xsd:string" msdata:Ordinal="4" />
              <xsd:attribute ref="xml:space" />
            </xsd:complexType>
          </xsd:element>
          <xsd:element name="resheader">
            <xsd:complexType>
              <xsd:sequence>
                <xsd:element name="value" type="xsd:string" minOccurs="0" msdata:Ordinal="1" />
              </xsd:sequence>
              <xsd:attribute name="name" type="xsd:string" use="required" />
            </xsd:complexType>
          </xsd:element>
        </xsd:choice>
      </xsd:complexType>
    </xsd:element>
  </xsd:schema>
  <resheader name="resmimetype">
    <value>text/microsoft-resx</value>
  </resheader>
  <resheader name="version">
    <value>2.0</value>
  </resheader>
  <resheader name="reader">
    <value>System.Resources.ResXResourceReader, System.Windows.Forms, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089</value>
  </resheader>
  <resheader name="writer">
    <value>System.Resources.ResXResourceWriter, System.Windows.Forms, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089</value>
  </resheader>
  <data name="PCF_TSTableGrid_LoadMore_ButtonLabel" xml:space="preserve">
    <value>Next</value>
    <comment>Label for TSTableGrid's Load More Paging Button</comment>
  </data>
  <data name="PCF_TSTableGrid_LoadPrevious_ButtonLabel" xml:space="preserve">
    <value>Previous</value>
    <comment>Label for TSTableGrid's Load More Paging Button</comment>
  </data>
  <data name="PCF_TSTableGrid_No_Record_Found" xml:space="preserve">
    <value>No records found.</value>
    <comment>No records found if no records</comment>
  </data>
  <data name="Dataset_Display_Key" xml:space="preserve">
    <value>Dataset</value>
    <comment>Dataset</comment>
  </data>
  <data name="Property_Display_Key" xml:space="preserve">
    <value>Sample Property Set</value>
    <comment>Sample Property Set</comment>
  </data>
  <data name="Property_Desc_Key" xml:space="preserve">
    <value>This is a sample property set allows to retrieve a data field using alias.</value>
    <comment>Sample Property Set</comment>
  </data>
    <data name="Property_Display_Key2" xml:space="preserve">
    <value>Sample Property Set 2</value>
    <comment>Sample Property Set 22</comment>
  </data>
  <data name="Property_Desc_Key2" xml:space="preserve">
    <value>This is a sample property set 2 allows to retrieve a data field using alias.</value>
    <comment>Sample Property Set 2</comment>
  </data>
</root>
```

In diesem Beispiel werden die Spalteninformationen mit der `context.parameters.[dataset_property_name].columns` extrahiert. Es ist ein Array-Typ. Die Zugriffsmöglichkeiten sind für Canvas- und modellgesteuerte Anwendungen gleich.

### <a name="record-binding"></a>Datensatz-Bindung

- Die sortierte Datensatz-Ids-Information kann mit `context.parameters.[dataset_property_name].sortedRecordIds` extrahiert werden.
- Mit `context.parameters.[dataset_property_name].records` erhalten Sie alle Datensatzinformationen.
- Holen Sie jedes Datensatzobjekt mit `context.parameters.[dataset_property_name].records[record_Id]`
- Der formatierte Wert konnte mit der `getFormattedValue`-Methode abgerufen werden.

### <a name="load-more-pages-of-data"></a>Weitere Seiten mit Daten laden

Die `context.parameters.[dataset_property_name].paging`-Methode bietet eine Paging-Funktionalität. Die `Load Next`-Schaltfläche wird angezeigt, wenn sie Daten für die nächste Seite hat. Benutzer können mit der `Load Prev`-Schaltfläche zu den vorherigen Seiten zurückkehren. 

### <a name="propertysets"></a>PropertySets

In dieser Beispielkomponente sind in ihrem Manifest zwei Eigenschaftssätze definiert, `samplePropertySet` und `samplePropertySet2`. Benutzer können zwei leere Spalten sehen, bevor sie der Komponente Spaltenfelder hinzufügen. Dies sind die Spalten der Eigenschaftsgruppe, die verwendet werden können, um auf die in der entsprechenden Eigenschaft definierten Spalten mit Hilfe des Ausdrucks input zuzugreifen. Bei einer Eigenschaftengruppe ist die entsprechende Spaltenreihenfolge 0.

> [!div class="mx-imgBorder"]
> ![Konfiguration des Eigenschaftssatzes](../media/property-set-configuration.png)

> [!div class="mx-imgBorder"]
> ![Ansichtsfelder für Eigenschaften einstellen](../media/property-set-view-fields.png)

### <a name="sizing"></a>Dimensionierung

Dieses Beispiel demonstriert auch, wie die Komponente der Container-Anpassung lauscht. Die `trackContainerResize`-Methode sollte innerhalb der `init`-Methode aufgerufen werden, sodass die `mode.allocatedWidth` und die `mode.allocatedHeight` jedes Mal bereitgestellt werden, wenn die `updateView` aufgerufen wird. Wenn diese Methode anfänglich nicht aufgerufen wird, werden die Werte `allocatedWidth` und `allocatedHeight` nicht bereitgestellt. Wenn die `allocatedHeight` gleich -1 ist, bedeutet das, dass es keine Höhenbegrenzung gibt. Die Komponente soll ihre Höhe anhand der bereitgestellte Breite anpassen.

## <a name="dataset-api-methods-that-arent-supported-in-canvas-apps-public-preview"></a>Dataset-API-Methoden, die in Canvas-Anwendungen nicht unterstützt werden (öffentliche Vorschau)

**Filter und Sortierstatus**

In dieser Vorschau für Canvas-Anwendungen wird nur ein begrenzter Satz von Methoden [filtering](../reference/filtering.md) und [sortStatus](../reference/sortstatus.md) unterstützt. Filter und Sortierung können auf den Datensatz auf Spalten vom Primärtyp angewendet werden, mit Ausnahme der GUID. Filter und Sortierung können auf die gleiche Weise wie in modellgesteuerten Anwendungen angewendet werden. Um den Datensatz mit Filter- und Sortierinformationen abzurufen, rufen Sie die Methoden in `context.parameters.[dataset_property_name].filtering` und `context.parameters.[dataset_property_name].sorting` auf und rufen dann die `context.parameters.[dataset_property_name].refresh()` auf.

**Ansicht**

In modellgesteuerten Anwendungen werden Ansichten für die Datensatzkomponenten benötigt, um die Informationen der Spalte zu erhalten. In Canvas-Anwendungen werden Ansichten als Filter verwendet. Es liegt am Hersteller der Anwendung, zu entscheiden, welche Spalten für jede Komponente hinzugefügt werden sollen. Eine Ansicht kann ausgewählt werden, nachdem eine Quelle für die Datensatzkomponente ausgewählt wurde. Dies ist nur anwendbar, wenn Sie Common Data Service als Quelle wählen. Wenn Sie eine Ansicht auswählen, wird der Filter der Ansicht auf die Quelle angewendet. Der Ansichtsname und die Ansichts-ID können mit den Methoden `context.parameters.[dataset_property_name].getTitle()` und `context.parameters.[dataset_property_name].getViewId()` abgerufen werden.

### <a name="related-topics"></a>Verwandte Themen

[Beispielkomponenten herunterladen](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[Beispielkomponenten verwenden](../use-sample-components.md)<br/>
[Power Apps component framework-API-Referenz](../reference/index.md)<br/>
[Manifestschemareferenz des Power Apps component framework](../manifest-schema-reference/index.md)
