---
title: " Iframe-Komponente | Microsoft-Dokumentation"
description: Implementieren der iframe-Komponente
ms.custom: ''
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: article
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: d10b03c478f238df02ee7e1309c0e39e758ce4c9
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340458"
---
# <a name="implementing-a-iframe-component"></a>Implementieren einer IFRAME-Komponente

In diesem Beispiel wird beschrieben, wie eine Code Komponente an verschiedene Felder im Formular gebunden und der Wert dieser Felder als Eingabe Eigenschaften für die Komponente verwendet wird.  

> [!div class="mx-imgBorder"]
> Iframe- ![Komponente]((../media/iframe-control.png "iframe") -Komponente)

## <a name="available-for"></a>Verfügbar für 

Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau) 

## <a name="manifest"></a>Kundiger

```XML
<?xml version="1.0" encoding="utf-8"?>
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
import { IInputs, IOutputs } from "./generated/ManifestTypes";
export class TSIFrameControl
  implements ComponentFramework.StandardControl<IInputs, IOutputs> {
  // reference to Bing Map IFrame HTMLElement
  private _bingMapIFrame: HTMLElement;
  // reference to the control container HTMLDivElement
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
  public init(
    context: ComponentFramework.Context<IInputs>,
    notifyOutputChanged: () => void,
    state: ComponentFramework.Dictionary,
    container: HTMLDivElement
  ) {
    this._container = container;
    this._controlViewRendered = false;
  }
  /**
   * Called when any value in the property bag has changed. This includes field values, data-sets, global values such as container height and width, offline status, control metadata values such as label, visible, etc.
   * @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to names defined in the manifest, as well as utility functions
   */
  public updateView(context: ComponentFramework.Context<IInputs>) {
    if (!this._controlViewRendered) {
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
  private renderBingMapIFrame(): void {
    this._bingMapIFrame = this.createIFrameElement();
    this._container.appendChild(this._bingMapIFrame);
  }
  /**
   * Updates the URL of the Bing Map IFrame to display the updated lat/long coordinates
   * @param latitude : latitude of center point of Bing map
   * @param longitude : longitude of center point of Bing map
   */
  private updateBingMapURL(latitude: number, longitude: number): void {
    // Bing Map API:
    // https://msdn.microsoft.com/library/dn217138.aspx
    // Provide bing map query string parameters to format and style map view
    let bingMapUrlPrefix = "https://www.bing.com/maps/embed?h=400&w=300&cp=";
    let bingMapUrlPostfix = "&lvl=12&typ=d&sty=o&src=SHELL&FORM=MBEDV8";
    // Build the entire URL with the user provided latitude and longitude
    let iFrameSrc: string =
      bingMapUrlPrefix + latitude + "~" + longitude + bingMapUrlPostfix;
    // Update the IFrame to point to the updated URL
    this._bingMapIFrame.setAttribute("src", iFrameSrc);
  }
  /**
   * Helper method to create an IFrame HTML Element
   */
  private createIFrameElement(): HTMLElement {
    let iFrameElement: HTMLElement = document.createElement("iframe");
    iFrameElement.setAttribute("class", "TS_SampleControl_IFrame");
    return iFrameElement;
  }
  /**
   * It is called by the framework prior to a control receiving new data.
   * @returns an object based on nomenclature defined in manifest, expecting object[s] for property marked as “bound” or “output”
   */
  public getOutputs(): IOutputs {
    // no-op: method not leveraged by this example custom control
    return {};
  }
  /**
   * Called when the control is to be removed from the DOM tree. Controls should use this call for cleanup.
   * i.e. canceling any pending remote calls, removing listeners, etc.
   */
  public destroy() {
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
> Das powerapps-Komponenten Framework unterstützt noch keine Verbund Felder, sodass Sie diese Komponente nicht an die Standardwerte für breiten-und Längengrade binden können. Sie müssen die Code Komponente an ein anderes Gleit Komma Feld binden.

Diese Beispiel Komponente rendert eine `IFRAME` die `Bing Maps URL` anzeigt. Die Komponente ist an zwei Gleit Komma Felder in dem Formular gebunden, die als Parameter an die Komponente weitergegeben und in den `IFRAME URL` eingefügt werden, um die Übersicht über die Längen-und Längengrade der bereitgestellten Eingaben zu aktualisieren.  

Aktualisieren Sie die `Manifest` Datei so, dass Sie die Bindung an zwei zusätzliche Felder im Formular einschließt.  
Diese Änderung informiert das powerapps-Komponenten Framework, dass diese gebundenen Felder während der Initialisierung an die Komponente und immer dann, wenn einer der Werte aktualisiert wird, an die Komponente übermittelt werden müssen.
  
```xml

<property name="latitudeValue" display-name-key="Bing_Maps_Latitude_Value" description-key="latitude" of-type="FP" usage="bound" required="true" />  
<property name="longitudeValue" display-name-key="Bing_Maps_Longitude_Value" description-key="longitude" of-type="FP" usage="bound" required="true" />  
```

Möglicherweise sind zusätzliche gebundene Eigenschaften erforderlich. Dies wird während der Komponenten Konfiguration erzwungen, wenn die Komponente an das Formular gebunden wird. Dies kann konfiguriert werden, indem das `required`-Attribut des Eigenschafts Knotens im Komponenten Manifest festgelegt wird. Legen Sie den Wert auf false fest, wenn Sie nicht möchten, dass die Komponenten Eigenschaft an ein Feld gebunden ist. 
 
`ControlFramework.d.ts` müssen aktualisiert werden, um `IInputs`-Schnittstelle zwei Felder hinzuzufügen. Dies ist das Format, das das powerapps-Komponenten Framework die Feldwerte übergibt. Wenn Sie diese Werte der `IInputs`-Schnittstelle hinzufügen, kann die typescript-Datei auf die Werte verweisen und erfolgreich kompiliert werden.  

```TypeScript
    export interface IInputs 
    { latitudeValue: ControlFramework.PropertyTypes.NumberProperty;  
        longitudeValue: ControlFramework.PropertyTypes.NumberProperty;  
    }  
 ```

Das anfängliche Rendering generiert ein `IFRAME`-Element und fügt es an den Steuerelement Container an. Diese `IFRAME` wird verwendet, um die Bildschirm- **Karte**anzuzeigen. Die URL des `IFRAME` ist auf einen `Bing Map URL` festgelegt und schließt die gebundenen Felder ("latitudevalue" und "-Wert") in die URL ein, um die Karte an der angegebenen Position zu zentrieren. 

Die [UpdateView](../reference/control/updateview.md) -Methode wird immer dann aufgerufen, wenn eines dieser Felder im Formular aktualisiert wird. Diese Methode aktualisiert die URL des **Karten** -Iframes von dumaps so, dass die neuen breiten-und Längengrad Werte an die Komponente übermittelt werden. Um diese Komponente zur Laufzeit anzuzeigen, binden Sie die Komponente wie jede andere Code Komponente an ein Feld im Formular.

### <a name="related-topics"></a>Verwandte Themen

[Beispiel Komponenten herunterladen](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[Schema Referenz für das powerapps-Komponenten Framework](../manifest-schema-reference/index.md)<br />
[API-Referenz für das powerapps-Komponenten Framework](../reference/index.md)<br />
[Übersicht über das powerapps-Komponenten Framework](../overview.md)
