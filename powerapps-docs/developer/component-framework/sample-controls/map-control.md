---
title: " Map-Komponente | Microsoft-Dokumentation"
description: Implementieren einer Karten Komponente mithilfe von Angular js
ms.custom: ''
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: article
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: f4b8702ef39688bdfc5f3ce9a51bf5c8c6e0ff20
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72341332"
---
# <a name="implementing-map-component"></a>Implementieren der Karten Komponente

Diese Beispiel Komponente ändert die Benutzeroberflächen Interaktion mit Adressfeldern im Formular. Zusammen mit den Textwerten der Adresse bietet diese Komponente die Möglichkeit, eine bestimmte Adresse auf einer Karte visuell zu identifizieren, ohne zu einer anderen Registerkarte oder einem anderen Bildschirm zu navigieren. 

> [!div class="mx-imgBorder"]
> ![Komponenten]Zuordnungs(../media/map-control.png "Komponente") zuordnen

## <a name="available-for"></a>Verfügbar für 

Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau) 

## <a name="manifest"></a>Kundiger

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
  // reference to ComponentFramework Context object
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

In der Manifest-Datei haben wir die Eigenschaft vom Typ `Single line of Text` definiert. Wir verwenden diese, um Sie an das Adressfeld im Formular zu binden.  

> [!NOTE]
> Sie können jede der Karten-APIs verwenden, die auf dem Markt verfügbar sind. In diesem Beispiel zeigen wir, wie Sie dies mit der Google Map-API durchführen. Für den Zugriff auf die Google Map-API müssen Sie einen API-Schlüssel für die Komponente erstellen. Befolgen Sie die Anweisungen (https://developers.google.com/maps/documentation/embed/get-api-key, um eines zu generieren).

Erstellen Sie einen Variablennamen `MAPS_API_KEY`, auf den im Kontext der-Komponente zugegriffen werden kann.
Mit der Google Map-API können Sie nur die Zuordnungen innerhalb eines `IFRAME` Rendering. Daher müssen Sie ein `IFRAME` Element erstellen, das die Zuordnung mit der von uns generierten URL Rendering. Standardmäßig wird die Zuordnung als ausgeblendet festgelegt und nur angezeigt, wenn der Adress Wert im Formular vorhanden ist.

`buildMapUrl` und `renderMap` (Sie können Sie sogar in einem zusammenführen) nimmt die Adress Zeichenfolge an und bettet Sie in die Karten-URL ein, indem Sie die Adress Zeichenfolge codiert und dann das src-Element des IFRAME-Elements auf die URL festlegt. Außerdem wird die **notifyoutputchanged** -Methode aufgerufen, um sicherzustellen, dass die Komponente benachrichtigt wird, dass sich das Rendering geändert hat. 
 
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

Stellen Sie sicher, dass Sie die `renderMap`-Funktion innerhalb der [UpdateView](../reference/control/updateview.md) -Funktion aufrufen, um sicherzustellen, dass das Steuerelement bei jedem Aktualisieren der Ansicht aktualisiert wird 

### <a name="related-topics"></a>Verwandte Themen

[Beispiel Komponenten herunterladen](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../reference/index.md)<br/>
[Schema Referenz für das powerapps-Komponenten Framework](../manifest-schema-reference/index.md)