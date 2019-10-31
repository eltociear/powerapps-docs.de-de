---
title: ' Kartenkomponente | Microsoft Docs'
description: Implementieren einer Kartenkomponente mit Angular JS
ms.custom: ''
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: article
ms.author: nabuthuk
author: Nkrb
---

# <a name="implementing-map-component"></a>Implementieren einer Kartenkomponente

Diese Beispielkomponente ändert die Benutzerfreundlichkeit beim Interagieren mit Adressfeldern im Formular. In Kombination mit den Textwerten der Adresse stellt diese Komponente die Möglichkeit bereit, eine bestimmte Adresse visuell auf einer Karte zu identifizieren, ohne zu einer anderen Registerkarte oder einen anderen Bildschirm zu navigieren. 

> [!div class="mx-imgBorder"]
> ![Kartenkomponente](../media/map-control.png "Kartenkomponente")

## <a name="available-for"></a>Verfügbar für 

Modellgesteuerte Apps und Canvas-Apps (experimentelle Vorschau) 

## <a name="manifest"></a>Manifest

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest>
    <control namespace="SampleNamespace" constructor="TSMapControl" version="1.0.0" display-name-key="TS_MapControl_Display_Key" description-key="TS_MapControl_Desc_Key" control-type="standard">
        <property name="controlValue" display-name-key="controlValue_Display_Key" description-key="controlValue_Desc_Key" of-type="SingleLine.Text" usage="bound" required="true" />
        <resources>
            <code path="index.ts" order="1" />
            <css path="css/TS_MapControl.css" order="1" />
        </resources>
    </control>
</manifest>
```

## <a name="code"></a>Code 

```TypeScript
import { IInputs, IOutputs } from "./generated/ManifestTypes";
export class TSMapControl
  implements ComponentFramework.StandardControl<IInputs, IOutputs> {
  // HTML IFrame element that will be used to render the map
  private _iFrameElement: HTMLIFrameElement;
  // PowerApps component framework framework delegate which will be assigned to this object which would be called whenever an update happens.
  private _notifyOutputChanged: () => void;
  // Reference to ComponentFramework Context object
  private _context: ComponentFramework.Context<IInputs>;
  // API Key used to activate and embed the maps automatically
  // NOTE: You can follow the documentation at https://developers.google.com/maps/documentation/embed/get-api-key to generate your own API Key
  private MAPS_API_KEY: string = "<Replace your Key here>";
  /**
   * Empty constructor.
   */
  constructor() {}
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
    this._notifyOutputChanged = notifyOutputChanged;
    this._context = context;
    this._iFrameElement = document.createElement("iframe");
    this._iFrameElement.setAttribute("class", "mapHiddenStyle");
    this.renderMap(this.buildMapUrl(context.parameters.controlValue.formatted));
    container.appendChild(this._iFrameElement);
  }
  /**
   * Checks if the url is not null and sets the value to the iFrame source to be loaded inside it and then notifies the ControlFramework that the output has changed
   * @param mapUrl : The url for the map that needs to be loaded inside the iFrame.
   */
  public renderMap(mapUrl: string) {
    if (mapUrl) {
      this._iFrameElement.setAttribute("src", mapUrl);
      this._iFrameElement.setAttribute("class", "mapVisibleStyle");
    } else {
      this._iFrameElement.setAttribute("class", "mapHiddenStyle");
    }
    this._notifyOutputChanged();
  }
  /**
   * Converts the string that is passed to a valid url that can be used to render the map for the location
   * @param addressString : any string that can be used to search for a location in maps
   * @returns the HTML encoded url that can be used to load the map if the addressString is non empty string
   */
  public buildMapUrl(addressString: string | undefined): string {
    if (addressString) {
      let url: string =
        "https://www.google.com/maps/embed/v1/place?key=" +
        this.MAPS_API_KEY +
        "&q=" +
        encodeURIComponent(addressString);
      return url;
    }
    return "";
  }
  /**
   * Called when any value in the property bag has changed. This includes field values, data-sets, global values such as container height and width, offline status, control metadata values such as label, visible, etc.
   * @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to names defined in the manifest, as well as utility functions
   */
  public updateView(context: ComponentFramework.Context<IInputs>) {
    this._context = context;
    this.renderMap(this.buildMapUrl(context.parameters.controlValue.formatted));
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
  public destroy() {}
}
```

## <a name="resources"></a>Ressourcen

```css
.SampleNamespace\.TSMapControl .mapVisibleStyle {
  width: 640px;
  height: 420px;
  visibility: visible;
}
.SampleNamespace\.TSMapControl .mapHiddenStyle {
  visibility: hidden;
}
```

In der Manifestdatei haben wir die Eigenschaft von Typ `Single line of Text` definiert. Anhand dieser Definition binden wir das Adressfeld im Formular.  

> [!NOTE]
> Sie können beliebige Karten-APIs, die im Markt verfügbar sind.Im vorliegenden Beispiel zeigen wir, wie es mit der Map-API Google gemacht wird. Sie müssen einen API-Schlüssel für die Komponente erstellen, um auf Google Map-API zuzugreifen.Folgen Sie den Anweisungen(https://developers.google.com/maps/documentation/embed/get-api-key, um einen zu generieren.

Erstellen Sie den Variablennamen `MAPS_API_KEY`, auf den im Rahmen der Komponente zugegriffen werden kann.
Google Map-API ermöglicht es Ihnen, die Karten in `IFRAME` zu rendern. Demnach müssen Sie ein `IFRAME`-Element erstellen, das die Zuordnung mithilfe der von uns generierten URL rendert. Standardmäßig legen wir fest, dass die Karte ausgeblendet und nur angezeigt wird, wenn die Adresswerte im Formular vorhanden sind.

`buildMapUrl` und `renderMap` (Sie können auch zusammengefügt werden) übernehmen die Adressenzeichenfolge und betten sie auf die Karten-URL, indem die Adresszeichenfolge verschlüsselt und dann das SRC-Element des IFRAME-Elements je auf die URL festgelegt wird. Außerdem rufen Sie die **notifyOutputChanged**-Methoden auf, um die Komponente zu benachrichtigen, dass das Rendering verändert wurde. 
 
```TypeScript
 public renderMap(mapUrl: string) {
    if (mapUrl) {
      this._iFrameElement.setAttribute("src", mapUrl);
      this._iFrameElement.setAttribute("class", "mapVisibleStyle");
    } else {
      this._iFrameElement.setAttribute("class", "mapHiddenStyle");
    }
    this._notifyOutputChanged();
  }
```

Stellen Sie sicher, dass Sie die `renderMap`-Funktion in der [updateView](../reference/control/updateview.md)-Funktion aufrufen, um sicherzustellen, dass das Steuerelement jedes Mal aktualisiert wird, wenn die Ansicht aktualisiert wird. 

### <a name="related-topics"></a>Verwandte Themen

[Beispielkomponenten herunterladen](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[PowerApps component framework-API-Referenz](../reference/index.md)<br/>
[Schema-Referenz des PowerApps component framework](../manifest-schema-reference/index.md)