---
title: " Lokalisierungs-API-Komponente | Microsoft-Dokumentation"
description: Implementieren der Lokalisierungs-API-Komponente
ms.custom: ''
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: article
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: cb24aa5ee30ecd2d855ff1de30840ac7eb568fcc
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340136"
---
# <a name="implementing-localization-api-component"></a>Implementieren der Lokalisierungs-API-Komponente

Dieses Beispiel zeigt, wie die Lokalisierung für benutzerdefinierte Steuerelemente erfolgt. In diesem Beispiel verwenden wir die [Inkrement-Komponente](increment-control.md) , um den Text, der auf der Inkrement-Schaltfläche angezeigt wird, auf der Grundlage der ausgewählten Sprache des Benutzers zu lokalisieren. 

Das powerapps-Komponenten Framework verwendet das Konzept des Implementierens von Zeichen folgen-Webressourcen (RESX), die zum Verwalten der lokalisierten Zeichen folgen verwendet werden, die auf jeder Weitere Informationen: [Zeichen folgen (RESX) WebResources](https://docs.microsoft.com/dynamics365/customer-engagement/developer/resx-web-resources). 

> [!div class="mx-imgBorder"]
> ![](../media/localization-api-control.png "API-Komponente") der Lokalisierungs-API-Komponente

## <a name="available-for"></a>Verfügbar für 

Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau) 

## <a name="manifest"></a>Kundiger 

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest>
    <control namespace="SampleNamespace" constructor="TSLocalizationAPI" version="1.0.0" display-name-key="TS_LocalizationAPI_Display_Key" description-key="TS_LocalizationAPI_Desc_Key" control-type="standard">
        <type-group name="numbers">
            <type>Whole.None</type>
            <type>Currency</type>
            <type>FP</type>
            <type>Decimal</type>
        </type-group>
        <property name="value" display-name-key="value_Display_Key" description-key="value_Desc_Key" of-type-group="numbers" usage="bound" required="true" />
        <resources>
            <code path="index.ts" order="1" />
            <css path="css/TS_LocalizationAPI.css" order="1" />
            <resx path="strings/TSLocalizationAPI.1033.resx" version="1.0.0" />
            <resx path="strings/TSLocalizationAPI.1035.resx" version="1.0.0" />
            <resx path="strings/TSLocalizationAPI.3082.resx" version="1.0.0" />
        </resources>
    </control>
</manifest>
```

## <a name="code"></a>Code

```TypeScript
import { IInputs, IOutputs } from "./generated/ManifestTypes";
export class TSLocalizationAPI
  implements ComponentFramework.StandardControl<IInputs, IOutputs> {
  // Value of the field is stored and used inside the control
  private _value: number;
  // PowerApps component framework framework delegate which will be assigned to this object which would be called whenever an update happens.
  private _notifyOutputChanged: () => void;
  // label element created as part of this control
  private label: HTMLInputElement;
  // button element created as part of this control
  private button: HTMLButtonElement;
  // reference to the control container HTMLDivElement
  // This element contains all elements of our custom control example
  private _container: HTMLDivElement;
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
    // Creating the label for the control and setting the relevant values.
    this.label = document.createElement("input");
    this.label.setAttribute("type", "label");
    this.label.addEventListener("blur", this.onInputBlur.bind(this));
    //Create a button to increment the value by 1.
    this.button = document.createElement("button");
    // Get the localized string from localized string
    this.button.innerHTML = context.resources.getString(
      "PCF_LocalizationSample_ButtonLabel"
    );
    this.button.classList.add("LocalizationSample_Button_Style");
    this._notifyOutputChanged = notifyOutputChanged;
    //this.button.addEventListener("click", (event) => { this._value = this._value + 1; this._notifyOutputChanged();});
    this.button.addEventListener("click", this.onButtonClick.bind(this));
    // Adding the label and button created to the container DIV.
    this._container = document.createElement("div");
    this._container.appendChild(this.label);
    this._container.appendChild(this.button);
    container.appendChild(this._container);
  }
  /**
   * Button Event handler for the button created as part of this control
   * @param event
   */
  private onButtonClick(event: Event): void {
    this._value = this._value + 1;
    this._notifyOutputChanged();
  }
  /**
   * Input Blur Event handler for the input created as part of this control
   * @param event
   */
  private onInputBlur(event: Event): void {
    let inputNumber = Number(this.label.value);
    this._value = isNaN(inputNumber)
      ? ((this.label.value as any) as number)
      : inputNumber;
    this._notifyOutputChanged();
  }
  /**
   * Called when any value in the property bag has changed. This includes field values, data-sets, global values such as container height and width, offline status, control metadata values such as label, visible, etc.
   * @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to names defined in the manifest, as well as utility functions
   */
  public updateView(context: ComponentFramework.Context<IInputs>): void {
    // This method would re render the control with the updated values after we call NotifyOutputChanged
    //set the value of the field control to the raw value from the configured field
    this._value = context.parameters.value.raw;
    this.label.value = this._value != null ? this._value.toString() : "";
    if (context.parameters.value.error) {
      this.label.classList.add("LocalizationSample_Input_Error_Style");
    } else {
      this.label.classList.remove("LocalizationSample_Input_Error_Style");
    }
  }
  /**
   * It is called by the framework prior to a control receiving new data.
   * @returns an object based on nomenclature defined in manifest, expecting object[s] for property marked as “bound” or “output”
   */
  public getOutputs(): IOutputs {
    // custom code goes here - remove the line below and return the correct output
    let result: IOutputs = {
      value: this._value
    };
    return result;
  }
  /**
   * Called when the control is to be removed from the DOM tree. Controls should use this call for cleanup.
   * i.e. canceling any pending remote calls, removing listeners, etc.
   */
  public destroy(): void {}
}
```

## <a name="resources"></a>Ressourcen

```css
.SampleNamespace\.TSLocalizationAPI button.LocalizationSample_Button_Style {
  text-decoration: none;
  display: inline-block;
  font-size: 14px;
  margin: 4px 6px;
  cursor: pointer;
  color: white;
  border-radius: 0px;
  background-color: rgb(59, 121, 183);
  border: none;
  padding: 5px;
  text-align: center;
}

.SampleNamespace\.TSLocalizationAPI
  button.LocalizationSample_Input_Error_Style {
  color: red;
}
```

```xml
<?xml version="1.0" encoding="utf-8"?>
<root>
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
<data name="PCF_LocalizationSample_ButtonLabel" xml:space="preserve">
<value>Increment</value>
<comment>Label for TSLocalizationAPI's Button</comment>
</data>
<data name="TS_LocalizationAPI_Display_Key" xml:space="preserve">
<value>Sample Localization Control</value>
<comment>Localization Sample Localized Control Name</comment>
</data>
<data name="TS_LocalizationAPI_Desc_Key" xml:space="preserve">
<value>This control showcases usage of localization.</value>
<comment>Localization Sample Localized Control Description</comment>
</data>
<data name="value_Display_Key" xml:space="preserve">
<value>Value</value>
<comment>Localization Sample Control Main Property Localized Name</comment>
</data>
<data name="value_Desc_Key" xml:space="preserve">
<value>Shows the field that the control is mapped to.</value>
<comment>Localization Sample Control Main Property Localized Description</comment>
</data>
</root>
```

```xml
<?xml version="1.0" encoding="utf-8"?>
<root>
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
<data name="PCF_LocalizationSample_ButtonLabel" xml:space="preserve">
<value>lisäys</value>
<comment>Label for TSLocalizationAPI's Button</comment>
</data>
<data name="TS_LocalizationAPI_Display_Key" xml:space="preserve">
<value>Esimerkki lokalisointi valvonnasta</value>
<comment>Localization Sample Localized Control Name</comment>
</data>
<data name="TS_LocalizationAPI_Desc_Key" xml:space="preserve">
<value>Tämä ohjaus objekti esittelee lokalisoinnin käyttöä.</value>
<comment>Localization Sample Localized Control Description</comment>
</data>
<data name="value_Display_Key" xml:space="preserve">
<value>Arvo</value>
<comment>Localization Sample Control Main Property Localized Name</comment>
</data>
<data name="value_Desc_Key" xml:space="preserve">
<value>Näyttää kentän, johon ohjaus objekti on yhdistetty.</value>
<comment>Localization Sample Control Main Property Localized Description</comment>
</data>
</root>
```

```xml
<?xml version="1.0" encoding="utf-8"?>
<root>
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
<data name="PCF_LocalizationSample_ButtonLabel" xml:space="preserve">
<value>Incremento</value>
<comment>Label for TSLocalizationAPI's Button</comment>
</data>
<data name="TS_LocalizationAPI_Display_Key" xml:space="preserve">
<value>Control de localización de muestras</value>
<comment>Localization Sample Localized Control Name</comment>
</data>
<data name="TS_LocalizationAPI_Desc_Key" xml:space="preserve">
<value>Este control muestra el uso de la localización.</value>
<comment>Localization Sample Localized Control Description</comment>
</data>
<data name="value_Display_Key" xml:space="preserve">
<value>Valor</value>
<comment>Localization Sample Control Main Property Localized Name</comment>
</data>
<data name="value_Desc_Key" xml:space="preserve">
<value>Muestra el campo al que se asigna el control.</value>
<comment>Localization Sample Control Main Property Localized Description</comment>
</data>
</root>
```

Zum Lokalisieren eines vorhandenen Projekts müssen Sie lediglich zusätzliche Ressourcen Dateien (RESX) erstellen, jeweils eine für eine bestimmte Sprache, die in den Zeichen folgen-Webressourcen erwähnt wurde, und Sie als Teil der Manifest-Datei des Steuer Elements unter dem Knoten [Ressourcen](../reference/resources.md) einschließen.  

Das powerapps-Komponenten Framework identifiziert die Sprache des Benutzers und gibt die Zeichen folgen aus dieser sprachspezifischen Ressourcen Datei zurück, wenn Sie versuchen, mithilfe `context.resources.getString`-Methode auf die Zeichenfolge zuzugreifen.

In diesem Beispiel werden zwei Sprachen `Spanish` und `Finnish` mit den jeweils definierten Sprachcodes 3082 und 1035. Wir haben eine Kopie des `Increment component` Beispiels erstellt und in `Localization API` umbenannt. Alle entsprechenden Dateien, einschließlich der Dateien in den Unterordnern, werden entsprechend umbenannt.

Im Ordner Strings unter `TS_LocalizationAPI` werden zwei weitere RESX-Dateien mit den Suffixen, die Spanisch und Finnisch entsprechen, als 3082 und 1035 hinzugefügt. Die neuen Dateien, die erstellt werden, sollten ihre Dateinamen als `{filename}.3082.resx` und `{filename}.1035.resx` haben, da das Framework diese Benennungs Konvention zur Identifizierung der Ressourcen Datei, die zum Lesen der Zeichen folgen für den Benutzer ausgewählt werden soll, unterstützt.

Stellen Sie sicher, dass die Schlüssel, die für Zeichen folgen in all diesen Ressourcen Dateien verwendet werden, in allen Sprachen denselben Namen haben. Wenn die Komponente nun auf der Benutzeroberfläche gerendert wird, sehen wir im Code, dass der Wert, der auf der Schaltfläche angezeigt wird, mithilfe `context.resources.getString("PCF_LocalizationSample_ButtonLabel")` abgerufen wird.

Wenn diese Codezeile ausgeführt wird, identifiziert das powerapps-Komponenten Framework automatisch die Sprache des Benutzers und wählt den Wert für die Schaltflächen Bezeichnung mithilfe des Schlüssels aus, der in der entsprechenden Sprachdatei angegeben ist. Im folgenden finden Sie den Text, den Sie für jede der drei Sprachen sehen, die für diese Beispiel Komponente unterstützt werden.
  
|LanguageCode |Angezeigter Wert |
|---|---|
|3082 |Incremento |
|1033 |Inkrement |
|1035 |lisäys | 

### <a name="related-topics"></a>Verwandte Themen

[Beispiel Komponenten herunterladen](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../reference/index.md)<br/>
[Schema Referenz für das powerapps-Komponenten Framework](../manifest-schema-reference/index.md)