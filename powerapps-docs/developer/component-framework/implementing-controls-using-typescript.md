---
title: Implementieren von benutzerdefinierten Komponenten mit TypeScript | MicrosoftDocs
description: So implementieren Sie eine benutzerdefinierte Komponente mit TypeScript
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.topic: index-page
ms.assetid: 18e88d702-3349-4022-a7d8-a9adf52cd34f
ms.author: nabuthuk
author: Nkrb
---

# <a name="implement-components-using-typescript"></a>Implementieren von Komponenten mithilfe von TypeScript

[!INCLUDE[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Dieses Lernprogramm führt Sie durch die Erstellung einer neuen benutzerdefinierten Komponente in TypeScript. Die Beispielkomponente ist eine lineare Ausgabekomponente. Die lineare Ausgabekomponente ermöglicht es Benutzern, numerische Werte mit einem visuellen Schiebregler anstelle der direkten Tastatureingabe einzugeben. 

## <a name="creating-a-new-component-project"></a>Erstellen eines neuen Komponentenprojekts

Wenn Sie ein neues Projekt erstellen möchten, führen Sie folgende Schritte aus:

1. Öffnen Sie eine Entwicklereingabeaufforderung für das VS 2017-Fenster.
2. Erstellen Sie einen neuen Ordner für das Projekt mit dem Befehl `mkdir LinearComponent`.
3. `cd` in das neue Verzeichnis und führen Sie den Befehl `cd LinearComponent` aus 
4. Erstellen Sie das Komponentenprojekt mit dem Befehl `pac pcf init --namespace SampleNamespace --name TSLinearInputControl --template field` 
5. Installieren Sie die Erstellungstools für das Projekt mit dem Befehl `npm install` 
6. Öffnen Sie Ihr Projekt in einer Entwicklerumgebung Ihrer Wahl und beginnen Sie mit der Implementierung Ihrer benutzerdefinierten Komponente.

## <a name="implementing-manifest"></a>Implementieren des Manifests

Eine benutzerdefinierte Komponente wird von den Informationen in der `ControlManifest.Input.xml`-Manifestdatei definiert. In dieser exemplarischen Vorgehensweise wird die Datei im Unterordner `<Your component Name>` erstellt. Für die lineare Eingabekomponente wird eine Eigenschaft definiert, um den numerischen Wert der Schiebreglereingabe zu speichern.

1. Öffnen Sie die `ControlManifest.Input.xml`-Datei im Codeeditor (Visual Studio Code). Die Datei `ControlManifest.Input.xml` definiert eine anfängliche Komponenteneigenschaft namens `sampleProperty`.

    ```XML
    <property name="sampleProperty" display-name-key="Property_Display_Key" description-key="Property_Desc_Key" of-type="SingleLine.Text" usage="bound" required="true" /> 
    ```

2. Nennen Sie `sampleProperty` um und ändern Sie den Eigenschaftstyp

    ```XML
    <property name="sliderValue" display-name-key="sliderValue_Display_Key" description-key="sliderValue_Desc_Key" of-type-group="numbers" usage="bound" required="true" /> 
    ```

3. Das of-type-group-Attribut verweist eine Gruppe zulässiger Nummern. Fügen Sie das folgende Typ-Gruppe-Element als nebengeordnetes Element dem Eigenschaftenelement im Manifest hinzu. Die Typ-Gruppe gibt den Komponentenwert an und kann Ganz-, Währungs-, Gleitkomma oder Dezimalwerte enthalten.

    ```XML
    <type-group name="numbers"> 
      <type>Whole.None</type> 
      <type>Currency</type> 
      <type>FP</type> 
      <type>Decimal</type> 
     </type-group> 
    ```

4. Speichern Sie die Änderungen in der `ControlManifest.Input.xml`-Datei.
5. Jetzt können Sie einen neuen Ordner innerhalb des `TSLinearInputControl`-Ordners erstellen und ihn mit **css** benennen.
6. Erstellen Sie eine CSS-Datei, um [der benutzerdefinierten Komponente ein Format hinzuzufügen](#adding-style-to-the-custom-component)
7. Erstellen Sie das Komponentenprojekt mit dem Befehl `npm run build`.
8. Das Build generiert eine aktualisierte Typescript-Typdeklinationsdatei unter `TSLinearInputControl/generated folder`.

## <a name="implementing-component-logic"></a>Implementieren von Komponentenlogik

Die Quelle für die benutzerdefinierte Komponente wird in der `index.ts`-Datei implementiert. Die `index.ts`-Datei schließt das Gerüst für Schnittstellenmethoden ein, die für das PowerApps-Komponentenframework erforderlich sind. 

1. Öffnen Sie die `index.ts`-Datei im Codeeditor Ihrer Wahl.
2. Aktualisieren Sie die `TSLinearInputControl`-Klasse folgendermaßen

```TypeScript
import { IInputs, IOutputs } from "./generated/ManifestTypes";
export class TSLinearInputControl implements ComponentFramework.StandardControl<IInputs, IOutputs> {
  // Value of the field is stored and used inside the control 
  private _value: number;
  // PCF framework delegate which will be assigned to this object which would be called whenever any update happens. 
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

  public init(context: ComponentFramework.Context<IInputs>, notifyOutputChanged: () => void, state: ComponentFramework.Dictionary, container: HTMLDivElement) {
    this._context = context;
    this._container = document.createElement("div");
    this._notifyOutputChanged = notifyOutputChanged;
    this._refreshData = this.refreshData.bind(this);
    // creating HTML elements for the input type range and binding it to the function which refreshes the control data
    this.inputElement = document.createElement("input");
    this.inputElement.setAttribute("type", "range");
    this.inputElement.addEventListener("input", this._refreshData);
    //setting the max and min values for the control.
    this.inputElement.setAttribute("min", "1");
    this.inputElement.setAttribute("max", "1000");
    this.inputElement.setAttribute("class", "linearslider");
    this.inputElement.setAttribute("id", "linearrangeinput");
    // creating a HTML label element that shows the value that is set on the linear range control
    this.labelElement = document.createElement("label");
    this.labelElement.setAttribute("class", "TS_LinearRangeLabel");
    this.labelElement.setAttribute("id", "lrclabel");
    // retrieving the latest value from the control and setting it to the HTMl elements.
    this._value = context.parameters.sliderValue.raw;
    this.inputElement.setAttribute("value", context.parameters.sliderValue.formatted ? context.parameters.sliderValue.formatted : "0");
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

  public refreshData(evt: Event): void {
    this._value = (this.inputElement.value as any) as number;
    this.labelElement.innerHTML = this.inputElement.value;
    this._notifyOutputChanged();
  }

  public updateView(context: ComponentFramework.Context<IInputs>): void {
    // storing the latest context from the control.
    this._value = context.parameters.sliderValue.raw;
    this._context = context;
    this.inputElement.setAttribute("value",context.parameters.sliderValue.formatted ? context.parameters.sliderValue.formatted : "");
    this.labelElement.innerHTML = context.parameters.sliderValue.formatted ? context.parameters.sliderValue.formatted : "";
  }

  public getOutputs(): IOutputs {
    return {
      sliderValue: this._value
    };
  }

  public destroy() {
    this.inputElement.removeEventListener("input", this._refreshData);
  }
}
```

3. Erstellen Sie das Projekt mit dem Befehl `npm run build` neu. 
 
4. Die Komponente wird in den Ordner `out/controls/TSLinearInputControl` kompiliert. Die Build-Artefakte umfassen:

   - bundle.js – Gebündelter Komponentenquellcode 
   - ControlManifest.xml – Tatsächliche Komponentenmanifestdatei, die in die Common Data Service-Organisation hochgeladen wird.

## <a name="adding-style-to-the-custom-component"></a>Hinzufügen von Stil zur benutzerdefinierten Komponente

Die `init`-Methode der linearen Eingabekomponente erstellt ein Eingabeelement und legt das Klassenattribut auf `linearslider` fest. Der Stil für die `linearslider`-Klasse wird in einer separaten `CSS`-Datei definiert. Zusätzliche Komponentenressourcen wie `CSS`-Dateien können in die benutzerdefinierte Komponente eingeschlossen werden, um weitere Anpassungen zu unterstützen.

1. Erstellen Sie einen neuen `css`-Unterordner im `TSLinearInputControl`-Ordner. 
2. Erstellen Sie eine neue `TS_LinearInputControl.css`-Datei im `css`-Unterordner. 
3. Fügen Sie der `TS_LinearInputControl.css`-Datei den folgenden Stilinhalt hinzu

    ```CSS
    .SampleNamespace\.TSLinearInputControl input[type=range].linearslider {
      margin: 1px 0;
      background: transparent;
      -webkit-appearance: none;
      width: 100%;
      padding: 0;
      height: 24px;
      -webkit-tap-highlight-color: transparent
    }

    .SampleNamespace\.TSLinearInputControl input[type=range].linearslider:focus {
      outline: none;
    }

    .SampleNamespace\.TSLinearInputControl input[type=range].linearslider::-webkit-slider-runnable-track {
      background: #666;
      height: 2px;
      cursor: pointer
    }

    .SampleNamespace\.TSLinearInputControl input[type=range].linearslider::-webkit-slider-thumb {
      background: #666;
      border: 0 solid #f00;
      height: 24px;
      width: 10px;
      border-radius: 48px;
      cursor: pointer;
      opacity: 1;
      -webkit-appearance: none;
      margin-top: -12px
    }

    .SampleNamespace\.TSLinearInputControl input[type=range].linearslider::-moz-range-track {
      background: #666;
      height: 2px;
      cursor: pointer
    }

    .SampleNamespace\.TSLinearInputControl input[type=range].linearslider::-moz-range-thumb {
      background: #666;
      border: 0 solid #f00;
      height: 24px;
      width: 10px;
      border-radius: 48px;
      cursor: pointer;
      opacity: 1;
      -webkit-appearance: none;
      margin-top: -12px
    }

    .SampleNamespace\.TSLinearInputControl input[type=range].linearslider::-ms-track {
      background: #666;
      height: 2px;
      cursor: pointer
    }

    .SampleNamespace\.TSLinearInputControl input[type=range].linearslider::-ms-thumb {
      background: #666;
      border: 0 solid #f00;
      height: 24px;
      width: 10px;
      border-radius: 48px;
      cursor: pointer;
      opacity: 1;
      -webkit-appearance: none;
    }
    ```

5. Speichern Sie die Datei `TS_LinearInputControl.css`.
6. Bearbeiten Sie die `ControlManifest.Input.xml`-Datei, um die `CSS`-Ressourcendatei im Ressourcenelement einzuschließen.
 
    ```XML
    <resources> 
      <code path="index.ts" order="1"/> 
      <css path="css/TS_LinearInputControl.css" order="1"/> 
    </resources> 
     ```
7. Erstellen Sie das Projekt mit dem Befehl  neu. 
   ```CLI
   npm run build
   ```
8. Inspizieren Sie die Build-Ausgabe unter **./out/controls/TSLinearInputControl** und beachten Sie, dass die **TS_LinearInputControl.css**-Datei jetzt in den kompilierten Build-Artefakten enthalten ist. 

## <a name="debugging-your-custom-component"></a>Debuggen der benutzerdefinierten Komponente

Sobald Sie Ihre benutzerdefinierte Komponentenlogik implementiert haben, führen Sie den folgenden Befehl aus, um den Debugging-Prozess zu starten. Weitere Informationen: [Debugging von benutzerdefinierten Komponenten](debugging-custom-controls.md)

```CLI
npm start
```

## <a name="packaging-your-custom-components"></a>Verpackung der benutzerdefinierten Komponenten

Führen Sie die folgenden Schritte aus um eine [Lösungs](https://docs.microsoft.com/dynamics365/customer-engagement/customize/solutions-overview)-Datei zu erstellen und zu importieren.

1. Erstellen Sie einen neuen Ordner **Lösungen** innerhalb des Ordners **LinearComponent** und navigieren Sie in den Ordner. 
2. Erstellen Sie mithilfe des Befehls ein neues Lösungsprojekt im **LinearComponent**-Ordner. 
 
    ```CLI
     pac solution init --publisher-name developer --publisher-prefix dev 
    ```

   > [!NOTE]
   > Die Werte für [publisher-name](https://docs.microsoft.com/powerapps/developer/common-data-service/reference/entities/publisher) und [publisher-prefix](https://docs.microsoft.com/powerapps/maker/common-data-service/change-solution-publisher-prefix) müssen in Ihrer Umgebung eindeutig sein.
 
3. Sobald das neue Lösungsprojekt erstellt ist, müssen Sie den Speicherort verweisen, an dem sich die erstellte Komponente befindet. Sie können den Verweis mit dem Befehl  hinzufügen.

    ```CLI
     pac solution add-reference --path c:\users\LinearComponent
    ```

4. Um eine ZIP-Datei aus Ihrem Lösungsprojekt zu erstellen, müssen Sie `cd` im Lösungsprojektverzeichnis hinzufügen und das Projekt erstellen mithilfe des Befehls 

    ```CLI
     msbuild /t:restore
    ```

5. Führen Sie erneut den folgenden Befehl msbuild aus
    ```CLI
     msbuild
    ```

    > [!NOTE]
    > Stellen Sie sicher, dass die **NuGet-Ziele und Build-Aufgaben** überprüft werden. So aktivieren Sie es
    > - Öffnen Sie das **Visual Studio-Installationsprogramm**
    > - Für VS 2017 klicken Sie auf **Ändern**.
    > - Klicken Sie auf **Einzelne Komponenten**
    > - Überprüfen Sie unter **Code-Tools** die Option **NuGet-Ziele und Build-Aufgaben**

6. Die erstelle Lösungs-Zip-Datei befindet sich in `Solution\\bin\debug\`.
7. Sie sollten mit dem Webportal einen manuellen [Import der Lösung](https://docs.microsoft.com/dynamics365/customer-engagement/customize/import-update-export-solutions) durchführen, sobald die Zip-Datei bereit ist.

## <a name="adding-custom-components-to-a-field-or-an-entity"></a>Hinzufügen von benutzerdefinierten Komponenten zu einem Feld oder einer Entität

Um eine benutzerdefinierte Komponente wie eine Datensatz-Komponente oder eine einfache Tabellenkomponente zu einem Raster oder einer Ansicht hinzuzufügen, führen Sie die im Thema [Hinzufügen von Komponenten zu Feldern und Entitäten](add-custom-controls-to-a-field-or-entity.md) erwähnten Schritte aus.

### <a name="see-also"></a>Siehe auch

[Beispielkomponenten herunterladen](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[Aktualisieren vorhandener PowerApps-Komponentenframework-Steuerelemente](updating-existing-controls.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](overview.md)
