---
title: Erstellen Sie Ihre erste Komponente mit Power Apps Component Framework | MicrosoftDocs
description: So implementieren Sie Code-Komponenten mit TypeScript
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: index-page
ms.assetid: 18e88d702-3349-4022-a7d8-a9adf52cd34f
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: e2a9ceb90ec91e7c13c50b966b3a2808d988cf31
ms.sourcegitcommit: cb533c30252240dc298594e74e3189d7290a4bd7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/04/2020
ms.locfileid: "3017368"
---
# <a name="create-your-first-component"></a>Erstellen Sie Ihre erste Codekomponente 

 In diesem Tutorial wird gezeigt, wie eine lineare Schieberegler-Codekomponente erstellt wird, die es Benutzern ermöglicht, die numerischen Werte mithilfe eines visuellen Schiebereglers zu ändern, anstatt die Werte in das Feld einzugeben. 

Die folgenden Schritte sind erforderlich, um eine lineare Schieberegler-Codekomponente zu erstellen:

- [Erstellen eines neuen Komponentenprojekts](#creating-a-new-component-project)
- [Implementieren des Manifests](#implementing-manifest)
- [Implementieren von Komponentenlogik mit Hilfe von TypeScript](#implementing-component-logic)
- [Hinzufügen von Stilen zu Codekomponenten](#adding-style-to-the-code-component)
- [Verpacken von Codekomponenten](#packaging-your-code-components)
- [Hinzufügen einer Komponente zu einer modellgesteuerten App](#adding-code-components-in-model-driven-apps)
- [Hinzufügen einer Komponente zu einer Canvas-App](#adding-code-components-to-a-canvas-app)

## <a name="creating-a-new-component-project"></a>Erstellen eines neuen Komponentenprojekts

Um ein neues Projekt zu erstellen:

1. Öffnen Sie eine **Entwickler Eingabeaufforderung für VS 2017** Fenster.
1. Erstellen Sie einen neuen Ordner für das Projekt mit dem folgenden Befehl: 
    ```CLI
    mkdir LinearComponent
    ```

1. Wechseln Sie zum Komponentenordner mit dem Befehl `cd LinearComponent`. 
   
1. Führen Sie den Befehl aus, um ein neues Komponentenprojekt zu erstellen, indem Sie Basisparameter übergeben.

   ```CLI
    pac pcf init --namespace SampleNamespace --name TSLinearInputComponent --template field
    ``` 

1. Installieren Sie die Projekt-Build-Tools mit dem Befehl `npm install`. 
1. Öffnen Sie Ihren Projektordner `C:\Users\<your name>\Documents\<My_code_Component>` in einer Entwicklerumgebung Ihrer Wahl und beginnen Sie mit der Entwicklung Ihrer Codekomponente. Am schnellsten starten Sie mit Hilfe der Ausführung von `code .` über die Eingabeaufforderung, sobald Sie sich im Verzeichnis `C:\Users\<your name>\Documents\<My_code_Component>` befinden. Durch diesen Befehl wird das Komponentenprojekt in Visual Studio Code geöffnet.

## <a name="implementing-manifest"></a>Implementieren des Manifests

Manifest ist eine XML-Datei, die die Metadaten der Codekomponente enthält. Es definiert auch das Verhalten der Codekomponente. In diesem Tutorial wird diese Manifestdatei unter dem Unterordner `<Your component Name>` erstellt. Wenn Sie die Datei `ControlManifest.Input.xml` im Visual Studio-Code öffnen, sehen Sie, dass die Manifestdatei mit einigen Eigenschaften vordefiniert ist. Weitere Informationen: [Manifest](manifest-schema-reference/manifest.md).

Nehmen Sie Änderungen an der vordefinierten Manifestdatei vor, wie hier gezeigt:

1. Der [control](manifest-schema-reference/control.md)-Knoten definiert Namespace, Version und Anzeigename der Codekomponente. Jetzt definieren Sie die jeweiligen Eigenschaften des [control](manifest-schema-reference/control.md)-Knotens, wie hier gezeigt:

   - **namespace**: Namespace der Codekomponente. 
   - **Konstruktor**: Konstruktor der Codekomponente.
   - **Version**: Version der Komponente. Wenn Sie die Komponente aktualisieren, müssen Sie die Version aktualisieren, um die neuesten Änderungen in der Laufzeit anzuzeigen.
   - **display-name-key**: Name der Codekomponente, die in der Benutzeroberfläche angezeigt wird.
   - **description-name-key**: Beschreibung der Codekomponente, die in der Benutzeroberfläche angezeigt wird.
   - **control-type**: Der Codekomponententyp. Nur *Standard*-Typen von Codekomponenten werden unterstützt.

     ```XML
      <?xml version="1.0" encoding="utf-8" ?>
      <manifest>
      <control namespace="SampleNameSpace" constructor="TSLinearInputComponent" version="1.0.0" display-name-key="Linear Input Component" description-key="Allows you to enter the numeric values using the visual slider." control-type="standard">
     ```

2. Der Knoten [Property](manifest-schema-reference/property.md) definiert die Eigenschaften der Codekomponente wie die Definition des Datentyps des Feldes. Der Eigenschaftenknoten wird als untergeordnetes Element unter dem `control`-Element angezeigt. Definieren Sie den [property](manifest-schema-reference/property.md)-Knoten wie hier gezeigt:

   - **name**: Name der Eigenschaft.
   - **display-name-key**: Anzeigename der Eigenschaft, die in der Benutzeroberfläche angezeigt wird.
   - **description-name-key**: Beschreibung der Eigenschaft, die in der Benutzeroberfläche angezeigt wird. 
   - **of-type-group**: Die [of-type-group](manifest-schema-reference/type-group.md) wird verwendet, wenn Sie mehr als zwei Datentypfelder haben möchten. Füge das Element [of-type-group](manifest-schema-reference/type-group.md) als Geschwister zum Element `property` im Manifest hinzu. Die `of-type-group` gibt den Komponentenwert an und kann Ganz-, Währungs-, Fließkomma- oder Dezimalwerte enthalten.
   - **Nutzung**: Verfügt über zwei Eigenschaften, *bound* und *input*. Bound-Eigenschaften sind lediglich an den Wert des Felds gebunden. Input-Eigenschaften sind entweder an ein Feld gebunden oder erlauben einen statischen Wert.
   - **erforderlich**: Definiert, ob die Eigenschaft erforderlich ist.

     ```XML
      <property name="sliderValue" display-name-key="sliderValue_Display_Key" description-key="sliderValue_Desc_Key" of-type-group="numbers" usage="bound" required="true" />
      ```

3. Der Knoten [ressources](manifest-schema-reference/resources.md) definiert die Visualisierung der Codekomponente. Sie enthält alle Ressourcen, die die Visualisierung und Formatierung der Codekomponente erstellen. Der [Code](manifest-schema-reference/code.md) ist als untergeordnetes Element unter dem Ressourcenelement angegeben. Definieren Sie die [Ressourcen](manifest-schema-reference/resources.md) wie hier gezeigt:

   - **Code**: Verweist auf den Pfad, in dem sich alle Ressourcendateien befinden.
 
      ```XML
      <resources>
        <code path="index.ts" order="1" />
        <css path="css/TS_LinearInputComponent.css" order="1" />
        </resources>
        ```
      Die gesamte Manifestdatei sollte in etwa so aussehen: 

     ```XML
      <?xml version="1.0" encoding="utf-8" ?>
      <manifest>
      <control namespace="SampleNamespace" constructor="TSLinearInputComponent" version="1.0.0" display-name-key="Linear Input Component" description-key="Allows you to enter the numeric values using the visual slider." control-type="standard">
        <type-group name="numbers">
          <type>Whole.None</type>
          <type>Currency</type>
          <type>FP</type>
          <type>Decimal</type>
         </type-group>
        <property name="sliderValue" display-name-key="sliderValue_Display_Key" description-key="sliderValue_Desc_Key" of-type-group="numbers" usage="bound" required="true" />
       <resources>
         <code path="index.ts" order="1" />
         <css path="css/TS_LinearInputComponent.css" order="1" />
       </resources>
      </control>
     </manifest>
     ```

4. Speichern Sie die Änderungen in der `ControlManifest.Input.xml`-Datei.
5. Jetzt können Sie einen neuen Ordner innerhalb des `TSLinearInputComponent`-Ordners erstellen und ihn mit **css** benennen.
6. Erstellen Sie eine CSS-Datei zu [Hinzufügen eines Stylings zur Codekomponente](#adding-style-to-the-code-component).
7. Erstellen Sie das Komponentenprojekt mit dem Befehl `npm run build`.
8. Das Build generiert eine aktualisierte TypeScript-Typdeklinationsdatei unter dem Ordner `TSLinearInputComponent/generated`.

## <a name="implementing-component-logic"></a>Implementieren von Komponentenlogik

Der nächste Schritt nach der Implementierung der Manifestdatei ist die Implementierung der Komponentenlogik mit TypeScript. Die Komponentenlogik sollte innerhalb der Datei `index.ts` implementiert werden. Wenn Sie die Datei `index.ts` im Code Visual Studio öffnen, sehen Sie, dass die vier wesentlichen Klassen vordefiniert sind. Nun, lassen Sie uns die Logik für die Codekomponente implementieren. 

1. Öffnen Sie die `index.ts`-Datei im Codeeditor Ihrer Wahl.
2. Aktualisieren Sie die Klasse `TSLinearInputComponent` mit dem folgenden Code:

```TypeScript
import { IInputs, IOutputs } from "./generated/ManifestTypes";
export class TSLinearInputComponent
  implements ComponentFramework.StandardControl<IInputs, IOutputs> {
  // Value of the field is stored and used inside the component
  private _value: number;
  // Power Apps component framework delegate which will be assigned to this object which would be called whenever any update happens.
  private _notifyOutputChanged: () => void;
  // label element created as part of this component
  private labelElement: HTMLLabelElement;
  // input element that is used to create the range slider
  private inputElement: HTMLInputElement;
  // reference to the component container HTMLDivElement
  // This element contains all elements of our code component example
  private _container: HTMLDivElement;
  // reference to Power Apps component framework Context object
  private _context: ComponentFramework.Context<IInputs>;
  // Event Handler 'refreshData' reference
  private _refreshData: EventListenerOrEventListenerObject;

  constructor() {}

  public init(
    context: ComponentFramework.Context<IInputs>,
    notifyOutputChanged: () => void,
    state: ComponentFramework.Dictionary,
    container: HTMLDivElement
  ) {
    this._context = context;
    this._container = document.createElement("div");
    this._notifyOutputChanged = notifyOutputChanged;
    this._refreshData = this.refreshData.bind(this);
    // creating HTML elements for the input type range and binding it to the function which refreshes the component data
    this.inputElement = document.createElement("input");
    this.inputElement.setAttribute("type", "range");
    this.inputElement.addEventListener("input", this._refreshData);
    //setting the max and min values for the component.
    this.inputElement.setAttribute("min", "1");
    this.inputElement.setAttribute("max", "1000");
    this.inputElement.setAttribute("class", "linearslider");
    this.inputElement.setAttribute("id", "linearrangeinput");
    // creating a HTML label element that shows the value that is set on the linear range component
    this.labelElement = document.createElement("label");
    this.labelElement.setAttribute("class", "TS_LinearRangeLabel");
    this.labelElement.setAttribute("id", "lrclabel");
    // retrieving the latest value from the component and setting it to the HTML elements.
    this._value = context.parameters.sliderValue.raw
      ? context.parameters.sliderValue.raw
      : 0;
    this.inputElement.value =
      context.parameters.sliderValue.formatted
        ? context.parameters.sliderValue.formatted
        : "0";
    
    this.labelElement.innerHTML = context.parameters.sliderValue.formatted
      ? context.parameters.sliderValue.formatted
      : "0";
    // appending the HTML elements to the component's HTML container element.
    this._container.appendChild(this.inputElement);
    this._container.appendChild(this.labelElement);
    container.appendChild(this._container);
  }

  /**
   * Updates the values to the internal value variable we are storing and also updates the html label that displays the value
   * @param context : The "Input Properties" containing the parameters, component metadata and interface functions
   */

  public refreshData(evt: Event): void {
    this._value = (this.inputElement.value as any) as number;
    this.labelElement.innerHTML = this.inputElement.value;
    this._notifyOutputChanged();
  }

  public updateView(context: ComponentFramework.Context<IInputs>): void {
    // storing the latest context from the control.
    this._value = context.parameters.sliderValue.raw
      ? context.parameters.sliderValue.raw
      : 0;
    this._context = context;
    this.inputElement.value =
     
      context.parameters.sliderValue.formatted
        ? context.parameters.sliderValue.formatted
        : "";
    
    this.labelElement.innerHTML = context.parameters.sliderValue.formatted
      ? context.parameters.sliderValue.formatted
      : "";
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
 
4. Die Komponente wird in den Ordner `out/controls/TSLinearInputComponent` kompiliert. Die Build-Artefakte umfassen:

   - bundle.js – Gebündelter Komponentenquellcode. 
   - ControlManifest.xml – Tatsächliche Komponentenmanifestdatei, die in die Common Data Service-Organisation hochgeladen wird.

## <a name="adding-style-to-the-code-component"></a>Hinzufügen eines Styles zur Codekomponente

Entwickler und App-Ersteller können mit CSS ihr Styling zur visuellen Darstellung ihrer Codekomponenten definieren. CSS ermöglicht es den Entwicklern, die Präsentation von Codekomponenten zu beschreiben, einschließlich Stil, Farben, Layouts und Schriften. Die Methode [init](reference/control/init.md) der linearen Eingangskomponente erzeugt ein Eingangselement und setzt das Klassenattribut auf `linearslider`. Der Stil für die `linearslider`-Klasse wird in einer separaten `CSS`-Datei definiert. Zusätzliche Komponentenressourcen wie `CSS`-Dateien können in die Codekomponente aufgenommen werden, um weitere Anpassungen zu unterstützen.

1. Erstellen Sie einen neuen `css`-Unterordner im `TSLinearInputComponent`-Ordner. 
2. Erstellen Sie eine neue `TS_LinearInputComponent.css`-Datei im `css`-Unterordner. 
3. Fügen Sie der `TS_LinearInputComponent.css`-Datei den folgenden Stilinhalt hinzu:

    ```CSS
    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider {
      margin: 1px 0;
      background: transparent;
      -webkit-appearance: none;
      width: 100%;
      padding: 0;
      height: 24px;
      -webkit-tap-highlight-color: transparent
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider:focus {
      outline: none;
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-webkit-slider-runnable-track {
      background: #666;
      height: 2px;
      cursor: pointer
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-webkit-slider-thumb {
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

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-moz-range-track {
      background: #666;
      height: 2px;
      cursor: pointer
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-moz-range-thumb {
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

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-ms-track {
      background: #666;
      height: 2px;
      cursor: pointer
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-ms-thumb {
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

5. Speichern Sie die Datei `TS_LinearInputComponent.css`.
6. Bearbeiten Sie die `ControlManifest.Input.xml`-Datei, um die `CSS`-Ressourcendatei im Ressourcenelement einzuschließen.
 
    ```XML
    <resources> 
      <code path="index.ts" order="1"/> 
      <css path="css/TS_LinearInputComponent.css" order="1"/> 
    </resources> 
     ```
7. Erstellen Sie das Projekt mit dem folgenden Befehl neu: 
   ```CLI
   npm run build
   ```
8. Überprüfen Sie die Buildausgabe unter **./out/controls/TSLinearInputComponent** und beachten Sie, dass die Datei **TS_LinearInputComponent.css** nun mit den kompilierten Build-Artefakten enthalten ist. 

## <a name="debugging-your-code-component"></a>Debuggen Ihrer Codekomponente

Sobald Sie die Codekomponentenlogik implementiert haben, führen Sie den folgenden Befehl aus, um den Prozess des Debuggens zu starten. Weitere Informationen: [Debugging von Codekomponenten](debugging-custom-controls.md)

```CLI
npm start
```

## <a name="packaging-your-code-components"></a>Verpackung Ihrer Code-Komponenten

Führen Sie diese Schritte aus, um eine [Lösung](https://docs.microsoft.com/powerapps/maker/common-data-service/solutions-overview)-Datei zu erstellen und zu importieren:

1. Erstellen Sie einen neuen Ordner **Lösungen** innerhalb des Ordners **LinearComponent** und navigieren Sie in den Ordner. 
2. Erstellen Sie mit Hilfe des folgenden Befehls ein neues Lösungsprojekt im **LinearComponent**-Ordner:
 
    ```CLI
     pac solution init --publisher-name developer --publisher-prefix dev 
    ```

   > [!NOTE]
   > Die Werte für [publisher-name](https://docs.microsoft.com/powerapps/developer/common-data-service/reference/entities/publisher) und [publisher-prefix](https://docs.microsoft.com/powerapps/maker/common-data-service/change-solution-publisher-prefix) müssen in Ihrer Umgebung eindeutig sein.
 
3. Sobald das neue Lösungsprojekt erstellt ist, müssen Sie den Speicherort verweisen, an dem sich die erstellte Komponente befindet. Sie können den Verweis mit dem folgenden Befehl hinzufügen:

    ```CLI
     pac solution add-reference --path c:\users\LinearComponent
    ```

4. Um eine ZIP-Datei aus Ihrem Lösungsprojekt zu erstellen, müssen Sie `cd` im Lösungsprojektverzeichnis hinzufügen und das Projekt mit Hilfe des folgenden Befehls erstellen: 

    ```CLI
     msbuild /t:restore
    ```

5. Führen Sie erneut den folgenden Befehl msbuild aus:
    ```CLI
     msbuild
    ```

    > [!NOTE]
    > Stellen Sie sicher, dass die **NuGet-Ziele und Build-Aufgaben** überprüft werden. Um es zu aktivieren:
    > - Öffnen Sie das **Visual Studio-Installationsprogramm**.
    > - Wählen Sie für Visual Studio 2017 **Ändern** aus.
    > - Klicken Sie auf **Einzelne Komponenten**.
    > - Überprüfen Sie unter **Code-Tools** die Option **NuGet-Ziele und Build-Aufgaben**.

6. Die erstelle Lösungs-ZIP-Datei befindet sich im Ordner `Solution\bin\debug`.
7. Manuell [importieren Sie die Lösung in Common Data Service](https://docs.microsoft.com/powerapps/maker/common-data-service/import-update-export-solutions) mithilfe des Webportals, sobald die ZIP-Datei bereit ist, oder automatisch mithilfe der [Power Apps Build Tools](https://marketplace.visualstudio.com/items?itemName=microsoft-IsvExpTools.PowerApps-BuildTools).

## <a name="adding-code-components-in-model-driven-apps"></a>Hinzufügen von Codekomponenten in modellgetriebenen Anwendungen

Um eine Codekomponente wie eine lineare Eingangskomponente hinzuzufügen, führen Sie die im Thema [Komponenten zu Feldern und Entitäten hinzufügen](add-custom-controls-to-a-field-or-entity.md) genannten Schritte aus.

## <a name="adding-code-components-to-a-canvas-app"></a>Hinzufügen von Codekomponenten zu einer Canvas-App

Um die Codekomponenten zu einer Canvas-App hinzuzufügen, befolgen Sie die Schritte in dem Thema [Hinzufügen von Codekomponenten zu einer Canvas-App](component-framework-for-canvas-apps.md#add-components-to-a-canvas-app).

### <a name="see-also"></a>Siehe auch

[Beispielkomponenten herunterladen](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[Aktualisieren vorhandener Power Apps component framework-Komponenten](updating-existing-controls.md)<br/>
[Power Apps Build Tools](https://docs.microsoft.com/powerapps/developer/common-data-service/build-tools-overview)<br/>
[Power Apps component framework-API-Referenz](reference/index.md)<br/>
[Power Apps component framework Übersicht](overview.md)
