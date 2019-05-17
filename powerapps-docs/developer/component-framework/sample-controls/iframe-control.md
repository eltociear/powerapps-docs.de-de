---
title: ' IFRAME-Komponente | Microsoft Docs'
description: Implementieren einer IFRAME-Komponente
ms.custom: ''
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.topic: article
ms.author: nabuthuk
---
# <a name="implementing-a-iframe-component"></a>Implementieren einer IFRAME-Komponente

[!INCLUDE[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

In diesem Beispiel wird beschrieben, wie Sie eine benutzerdefinierte Komponente an unterschiedliche Felder im Formular gebunden wird wie der Wert dieser Felder als Eingabeeigenschaften der Komponente verwendet werden.  

> [!div class="mx-imgBorder"]
> ![IFRAME-Komponente](../media/iframe-control.png "IFRAME-Komponente")

> [!IMPORTANT]
> - PowerApps-Komponentenframework ist eine Vorschaufunktion.
> - [!INCLUDE[cc_preview_features_definition](../../../includes/cc-preview-features-definition.md)] 
> - [!INCLUDE[cc_preview_features_no_MS_support](../../../includes/cc-preview-features-no-ms-support.md)]

## <a name="manifest"></a>Manifest

```xml
<?xml version="1.0" encoding="utf-8" ?>
<manifest>
    <control namespace="SampleNamespace" constructor="TSIFrameControl" version="1.0.0" display-name-key="TS_IFrameControl_Display_Key" description-key="TS_IFrameControl_Desc_Key" control-type="standard">
        <property name="stringProperty" display-name-key="stringProperty_Display_Key" description-key="stringProperty_Desc_Key" of-type="SingleLine.Text" usage="bound" required="true" />
        <property name="latitudeValue" display-name-key="Bing_Maps_Latitude_Value" description-key="latitude" of-type="FP" usage="bound" required="true" />
        <property name="longitudeValue" display-name-key="Bing_Maps_Longitude_Value" description-key="longitude" of-type="FP" usage="bound" required="true" />
        <resources>
            <code path="index.ts" order="1" />
            <css path="css/TS_IFrameControl.css" order="2" />
        </resources>
    </control>
</manifest>
```

## <a name="code"></a>Code

```TypeScript

import {IInputs, IOutputs} from "./generated/ManifestTypes";
export class TSIFrameControl implements ComponentFramework.StandardControl<IInputs, IOutputs> 
{
// Reference to Bing Map IFrame HTMLElement
private _bingMapIFrame: HTMLElement;
// Reference to the control container HTMLDivElement
// This element contains all elements of our custom control example
private _container: HTMLDivElement;
// Flag if control view has been rendered
private _controlViewRendered: Boolean;
/**
 * Used to initialize the control instance. Controls can kick off remote server calls and other initialization actions here.
 * Data-set values are not initialized here, use updateView.
 * @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to property names defined in the manifest, as well as utility functions.
 * @param notifyOutputChanged A callback method to alert the framework that the control has new outputs ready to be retrieved asynchronously.
 * @param state A piece of data that persists in one session for a single user. Can be set at any point in a controls life cycle by calling 'setControlState' in the Mode interface.
 * @param container If control is marked control-type='standard', it receives an empty div element within which it can render its content.
 */
public init(context: ComponentFramework.Context<IInputs>, notifyOutputChanged: () => void, state: ComponentFramework.Dictionary, container:HTMLDivElement)
{
    this._container = container;
    this._controlViewRendered = false;
}
/**
 * Called when any value in the property bag has changed. This includes field values, data-sets, global values such as container height and width, offline status, control metadata values such as label, visible, etc.
 * @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to names defined in the manifest, as well as utility functions
 */
public updateView(context: ComponentFramework.Context<IInputs>)
{
    if (!this._controlViewRendered)
    {
        this._controlViewRendered = true;
        this.renderBingMapIFrame();
    }
    let latitude: number = context.parameters.latitudeValue.raw;
    let longitude: number = context.parameters.longitudeValue.raw;
    this.updateBingMapURL(latitude, longitude);
}
/** 
 * Render IFrame HTML Element that hosts the Bing Map and appends the IFrame to the control container 
 */
private renderBingMapIFrame(): void
{
    this._bingMapIFrame = this.createIFrameElement();
    this._container.appendChild(this._bingMapIFrame);
}
/**
 * Updates the URL of the Bing Map IFrame to display the updated lat/long coordinates
 * @param latitude : latitude of center point of Bing map
 * @param longitude : longitude of center point of Bing map
 */
private updateBingMapURL(latitude:number, longitude:number): void
{
    // Bing Map API:
    // https://msdn.microsoft.com/en-us/library/dn217138.aspx
    // Provide bing map query string parameters to format and style map view
    let bingMapUrlPrefix = "https://www.bing.com/maps/embed?h=400&w=300&cp=";
    let bingMapUrlPostfix = "&lvl=12&typ=d&sty=o&src=SHELL&FORM=MBEDV8";
    // Build the entire URL with the user provided latitude and longitude
    let iFrameSrc:string = bingMapUrlPrefix + latitude + "~"+ longitude + bingMapUrlPostfix;
    // Update the IFrame to point to the updated URL
    this._bingMapIFrame.setAttribute("src", iFrameSrc);
}
/** 
 * Helper method to create an IFrame HTML Element
 */
private createIFrameElement(): HTMLElement
{
    let iFrameElement:HTMLElement = document.createElement("iframe")
    iFrameElement.setAttribute("class", "TS_SampleControl_IFrame");
    return iFrameElement
}
/** 
 * It is called by the framework prior to a control receiving new data. 
 * @returns an object based on nomenclature defined in manifest, expecting object[s] for property marked as “bound” or “output”
 */
public getOutputs(): IOutputs
{
    // no-op: method not leveraged by this example custom control
    return {};
}
/** 
 * Called when the control is to be removed from the DOM tree. Controls should use this call for cleanup.
 * i.e. canceling any pending remote calls, removing listeners, etc.
 */
public destroy()
{
    // no-op: method not leveraged by this example custom control
}
}
```

## <a name="resources"></a>Ressourcen

```css
.SampleNamespace\.TSIFrameControl .TS_SampleControl_IFrame
{
    width: 300px;
    height: 400px;
}
```

> [!NOTE]
> Das PowerApps Komponentenframework unterstützt noch keine zusammengesetzten Felder, Sie können diese Komponente daher nicht an die Adressfelder für Längen- und Breitengrad binden. Sie müssen die benutzerdefinierte Komponente an ein anderes Gleitkommafeld binden.

In dieser Beispielkomponente wird `IFRAME` gerendert, das `Bing Maps URL` anzeigt. Die Komponente ist an zwei Gleitkommafelder im Formular gebunden, die als Parameter an die Komponente übergeben und in `IFRAME URL` eingebracht werden, um Bing Map mit dem Längengrad und Breitendrad der bereitgestellten Eingabe zu aktualisieren.  

Aktualisieren Sie die `Manifest`-Datei, um Bindung an zwei zusätzliche Felder im Formular einzuschließen.  
Diese Änderung informiert das PowerApps Komponentenframework, dass diese gebundenen Felder während der Initialisierung und wenn einer der der Werte initialisiert wird, an die Komponente übergeben werden müssen.
  
```xml

<property name="latitudeValue" display-name-key="Bing_Maps_Latitude_Value" description-key="latitude" of-type="FP" usage="bound" required="true" />  
<property name="longitudeValue" display-name-key="Bing_Maps_Longitude_Value" description-key="longitude" of-type="FP" usage="bound" required="true" />  
```

Möglicherweise gelten zusätzliche gebundene Eigenschaften oder nicht. Dadurch wird bei der Komponentenkonfiguration erzwungen, wenn die Komponente an das Formular gebunden wird. Dies kann konfiguriert werden, indem das Attribut `required` des Eigenschaftenknotens im Komponentenmanifest festgelegt wird. Legen Sie den Wert auf "falsch" fest, wenn Sie die Komponenteneigenschaft nicht an ein Feld gebunden werden soll. 
 
`ControlFramework.d.ts` muss aktualisiert werden, um der `IInputs`-Schnittstelle zwei Felder hinzuzufügen. Dies ist das Format, das vom PowerApps Komponentenframework an die Feldwerte übergeben wird. Das Hinzufügen dieser Werte zur `IInputs`-Schnittstelle ermöglicht es Ihrer TypeScript-Datei, die Werte zu verweisen und erfolgreich zu kompilieren.  

```TypeScript
    export interface IInputs 
    { latitudeValue: ControlFramework.PropertyTypes.NumberProperty;  
        longitudeValue: ControlFramework.PropertyTypes.NumberProperty;  
    }  
 ```

Das ursprüngliche Rendering generiert ein `IFRAME`-Element und hängt es dem Steuerelement-Container an. Dieses `IFRAME` wird häufig verwendet, um **Bing Map** anzuzeigen. Die URL von `IFRAME` wird auf eine `Bing Map URL` festgelegt,und enthält die gebundenen Felder (latitudeValue und longitudeValue) in der URL, um die Karte am angegebenen Standort zu zentrieren. 

Die [updateView](../reference/control/updateview.md)-Methode wird aufgerufen, wenn eine dieser Felder im Formular aktualisiert wird. Diese Methode aktualisiert die URL des **Bing Map**-IFRAMEs, um die neuen Breiten- und Längengradwerte zu verwenden, die der Komponente übergeben werden. Wenn Sie diese Komponente zur Laufzeit anzeigen möchten, binden Sie die Komponente, wie jede andere angepasste Komponente, an ein Feld im Formular.

### <a name="related-topics"></a>Verwandte Themen

[Beispielkomponenten herunterladen](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[Schema-Referenz des PowerApps Komponenten-Frameworks](../manifest-schema-reference/index.md)<br />
[PowerApps-Komponentenframework-API-Referenz](../index.md)<br />
[Übersicht über das PowerApps-Komponentenframework](../overview.md)
