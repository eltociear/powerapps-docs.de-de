---
title: Implementieren von benutzerdefinierten Steuerelementen mithilfe von TypeScript | MicrosoftDocs
description: So implementieren Sie ein benutzerdefiniertes Steuerelement mithilfe von TypeScript
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.author: nabuthuk
---

# <a name="implement-controls-using-typescript"></a>Implementieren von Steuerelementen mit TypeScript

Dieses Lernprogramm führt Sie durch die Erstellung eines neuen benutzerdefinierten Steuerelements in TypeScript. Das Beispielsteuerelement ist ein lineares Eingabesteuerelement. Das lineare Eingabesteuerelement ermöglicht es Benutzern, numerische Werte mithilfe eines visuellen Schiebereglers einzugeben, anstatt Werte direkt über die Tastatur einzugeben.


## <a name="implementing-manifest"></a>Implementieren des Manifests

Ein benutzerdefinierte Steuerelement wird anhand der Informationen in der Manifestdatei `Manifest.xml` definiert. Für das lineare Eingabesteuerelement wird eine Eigenschaft definiert, um den numerischen Wert der Schiebereglereingabe zu speichern.

1. Öffnen Sie die `Manifest.xml`-Datei im Code-Editor (Visual Studio Code). Die `Manifest.xml`-Datei definiert eine anfängliche Steuerelementeigenschaft namens `sampleProperty`.

    ```XML
    <property name="sampleProperty" display-name-key="Property_Display_Key" description-key="Property_Desc_Key" of-type="SingleLine.Text" usage="bound" required="true" /> 
    ```

2. Nennen Sie `sampleProperty` um und ändern Sie den Eigenschaftstyp

    ```XML
    <property name="sliderValue" display-name-key=" sliderValue _Display_Key" description-key=" sliderValue_Desc_Key" of-type-group="numbers" usage="bound" required="true" /> 
    ```

3. Das of-type-group-Attribut verweist eine Gruppe zulässiger Nummern. Fügen Sie das folgende Typ-Gruppe-Element als nebengeordnetes Element dem <property>-Element im Manifest hinzu. Die Typ-Gruppe gibt den Steuerelementwert an und kann ganze, Währungs-, Gleitkomma- und Dezimalwerte enthalten.

    ```XML
    <type-group name="numbers"> 
      <type>Whole.None</type> 
      <type>Currency</type> 
      <type>FP</type> 
      <type>Decimal</type> 
     </type-group> 
    ```


4. Speichern Sie die Änderungen in der `ControlManifest.Input.xml`-Datei.
5. Erstellen Sie das Steuerelementprojekt mit dem Befehl `npm run build`.
6. Das Build generiert eine aktualisierte Typescript-Typdeklinationsdatei unter `TSLinearInputControl/generated folder`.  Die `ManifestTypes.d.ts`-Datei definiert die Eigenschaften, auf die das Steuerelement der Zugriff hat, um Quellcode mit Typescript zu erstellen.

## <a name="implementing-control-logic"></a>Implementieren von Steuerelementlogik

Die Quelle für das benutzerdefinierte Steuerelement wird in der Datei `index.ts` implementiert. Die `index.ts`-Datei schließt das Gerüst für Schnittstellenmethoden ein, die für das PowerApps-Komponentenframework erforderlich sind. 

1. Öffnen Sie die `index.ts`-Datei im Codeeditor Ihrer Wahl.
2. Aktualisieren Sie die `TSLinearInputControl`-Klasse folgendermaßen

```TypeScript
export class TSLinearInputControl implements ComponentFramework.StandardControl<IInputs, IOutputs> {
// Value of the field is stored and used inside the control 
private _value: number;
// PowerApps component framework framework delegate which will be assigned to this object which would be called whenever any update happens. 
private _notifyOutputChanged: () => void;
// label element created as part of this control
private labelElement: HTMLLabelElement;
// input element that is used to create the range slider
private inputElement: HTMLInputElement;
// Reference to the control container HTMLDivElement
// This element contains all elements of our custom control example
private _container: HTMLDivElement;
// Reference to ComponentFramework Context object
 private _context: ComponentFramework.Context<IInputs>;
// Event Handler 'refreshData' reference
 private _refreshData: EventListenerOrEventListenerObject;
    
constructor() {
    }
    
public init(context: ComponentFramework.Context<IInputs>, notifyOutputChanged: () => void, state: ComponentFramework.Dictionary, container:HTMLDivElement)
  {
     this._context = context;
     this._container = document.createElement("div");
     this._notifyOutputChanged = notifyOutputChanged;
     this._refreshData = this.refreshData.bind(this);
     // creating HTML elements for the input type range and binding it to the function which refreshes the control data
     this.inputElement = document.createElement("input");
     this.inputElement.setAttribute("type","range");
     this.inputElement.addEventListener("input",this._refreshData);
     //setting the max and min values for the control.
     this.inputElement.setAttribute("min","1");
     this.inputElement.setAttribute("max","1000");
     this.inputElement.setAttribute("class","linearslider");
     this.inputElement.setAttribute("id","linearrangeinput");
     // creating a HTML label element that shows the value that is set on the linear range control
     this.labelElement = document.createElement("label");
     this.labelElement.setAttribute("class", "TS_LinearRangeLabel");
     this.labelElement.setAttribute("id","lrclabel");
     // retrieving the latest value from the control and setting it to the HTMl elements.
     this._value = context.parameters.sliderValue.raw;
     this.inputElement.setAttribute("value",context.parameters.sliderValue.formatted ? context.parameters.sliderValue.formatted : "0");
     this.labelElement.innerHTML = context.parameters.sliderValue.formatted ? context.parameters.sliderValue.formatted : "0";
     // appending the HTML elements to the control's HTML container element.
     this._container.appendChild(this.inputElement);
     this._container.appendChild(this.labelElement);
     container.appendChild(this._container);
        }
    
/**
* Updates the values to the internal value variable we are storing and also updates the html label that displays the value
* @param context : The "Input Properties" containing the parameters, control metadata and interface functions
*/

public refreshData(evt: Event) : void
  {
      this._value = (this.inputElement.value as any)as number;
      this.labelElement.innerHTML = this.inputElement.value;
      this._notifyOutputChanged();
    }
        
public updateView(context: ComponentFramework.Context<IInputs>): void
 {
      // storing the latest context from the control.
    this._value = context.parameters.sliderValue.raw;
    this._context = context;
    this.inputElement.setAttribute("value",context.parameters.sliderValue.formatted ? context.parameters.sliderValue.formatted : "");
    this.labelElement.innerHTML = context.parameters.sliderValue.formatted ? context.parameters.sliderValue.formatted : "";
        }
    
public getOutputs(): IOutputs
  {
     return {
            sliderValue : this._value
            };
        }
        
public destroy()
   {
     this.inputElement.removeEventListener("input", this._refreshData);
        }
    }
```

3. Erstellen Sie das Projekt mit dem Befehl `npm run build` neu. 
 
4. Das Steuerelement wird in den `/out/controls/TSLinearInputControl`-Ordner kompiliert. Die Build-Artefakte umfassen:

   - bundle.js – Gebündelter Steuerelementquellcode 
   - ControlManifest.xml – Tatsächliche Steuerelementmanifestdatei, die zur Common Data Service-Organisation hochgeladen wird.

## <a name="adding-style-to-the-custom-control"></a>Hinzufügen von Stil zum benutzerdefinierten Steuerelement

Die `init`-Methode des linearen Ausgabesteuerelements erstellt ein Eingabeelement und legt das Klassenattribut auf `linearslider` fest. Der Stil für die `linearslider`-Klasse wird in einer separaten `css`-Datei definiert. Zusätzliche Steuerelementressourcen wie `css` - Dateien können in das benutzerdefinierte Steuerelement eingeschlossen werden, um weitere Anpassungen zu unterstützen.

1. Bearbeiten Sie die `ControlManifest.Input.xml`-Datei, um eine zusätzliche `css`-Ressource im <resources>-Element einzuschließen.
 
    ```XML
      <resources> 
      <code path="index.ts" order="1"/> 
      <css path="css/TS_LinearInputControl.css" order="1"/> 
    </resources> 
     ```

2. Erstellen Sie einen neuen `css`-Unterordner im `TSLinearInputControl`-Ordner. 
3. Erstellen Sie eine neue `TS_LinearInputControl.css`-Datei im `css`-Unterordner. 
4. Fügen Sie der `TS_LinearInputControl.css`-Datei den folgenden Stilinhalt hinzu

   ```CSS
    .SampleNamespace\.TSLinearInputControl input[type=range].linearslider {    
    margin: 1px 0;    
    background:transparent; 
   -webkit-appearance:none; 
    width:100%;padding:0; 
    height:24px; 
   -webkit-tap-highlight-color:transparent 
    } 
    .SampleNamespace\.TSLinearInputControl input[type=range].linearslider:focus { 
     outline: none; 
     } 
    .SampleNamespace\.TSLinearInputControl input[type=range].linearslider::-webkit-slider-runnable-track {    
     background: #666; 
     height:2px; 
     cursor:pointer 
     }    
     .SampleNamespace\.TSLinearInputControl input[type=range].linearslider::-webkit-slider-thumb {    
     background: #666;    
     border:0 solid #f00; 
     height:24px; 
     width:10px; 
     border-radius:48px; 
     cursor:pointer; 
     opacity:1; 
    -webkit-appearance:none; 
     margin-top:-12px 
     }     
    .SampleNamespace\.TSLinearInputControl input[type=range].linearslider::-moz-range-track {    
     background: #666;    
     height:2px; 
     cursor:pointer   
     }    
     .SampleNamespace\.TSLinearInputControl input[type=range].linearslider::-moz-range-thumb {    
     background: #666;    
     border:0 solid #f00; 
     height:24px; 
     width:10px; 
     border-radius:48px; 
    cursor:pointer; 
    opacity:1; 
   -webkit-appearance:none; 
   margin-top:-12px 
   }    
   .SampleNamespace\.TSLinearInputControl input[type=range].linearslider::-ms-track {    
    background: #666;    
    height:2px; 
    cursor:pointer   
     }     
    .SampleNamespace\.TSLinearInputControl input[type=range].linearslider::-ms-thumb {    
    background: #666;    
    border:0 solid #f00; 
    height:24px; 
    width:10px; 
    border-radius:48px; 
   cursor:pointer; 
   opacity:1; 
   -webkit-appearance:none; 
    } 
   ```

5. Speichern von `TS_LinearInputControl.css` 
6. Erstellen Sie das Projekt mit dem Befehl `npm run build ` neu.
7. Inspizieren Sie die Build-Ausgabe unter `./out/controls/TSLinearInputControl` und beachten Sie, dass die `TS_LinearInputControl.css`-Datei jetzt in den kompilierten Build-Artefakten enthalten ist. 


### <a name="see-also"></a>Siehe auch

[Aktualisieren vorhandener PowerApps-Komponentenframework-Steuerelemente](updating-existing-controls.md)
