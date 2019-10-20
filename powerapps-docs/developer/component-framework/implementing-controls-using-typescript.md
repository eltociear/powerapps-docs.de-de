---
title: Implementieren von Code Komponenten mithilfe von typescript | MicrosoftDocs
description: Implementieren von Code Komponenten mithilfe von typescript
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: index-page
ms.assetid: 18e88d702-3349-4022-a7d8-a9adf52cd34f
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: cd57cce824c4071de12e7dc96407018dde57c2d7
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346829"
---
# <a name="implement-components-using-typescript"></a>Implementieren von Komponenten mithilfe von typescript

Dieses Tutorial führt Sie durch den Prozess der Erstellung einer neuen Code Komponente in typescript. Die Beispiel Komponente ist eine lineare Eingabe Komponente, die es Benutzern ermöglicht, numerische Werte mithilfe eines visuellen Schiebereglers einzugeben, statt die Werte in das Feld einzugeben. 

## <a name="creating-a-new-component-project"></a>Erstellen eines neuen Komponenten Projekts

So erstellen Sie ein neues Projekt:

1. Öffnen Sie eine **Developer-Eingabeaufforderung für das Fenster vs 2017** .
1. Erstellen Sie einen neuen Ordner für das Projekt, indem Sie den folgenden Befehl verwenden: 
    ```CLI
    mkdir LinearComponent
    ```

1. Wechseln Sie mit dem Befehl `cd LinearComponent` in das neue Verzeichnis. 
   
1. Führen Sie den folgenden Befehl aus, um ein neues Komponenten Projekt zu erstellen, das Basisparameter übergibt.

   ```CLI
    pac pcf init --namespace SampleNamespace --name TSLinearInputComponent --template field
    ``` 

1. Installieren Sie die projektbuildtools mithilfe des Befehls `npm install`. 
2. Öffnen Sie Ihren Projektordner `C:\Users\<your name>\Documents\<My_PCF_Component>` in einer Entwicklerumgebung Ihrer Wahl, und beginnen Sie mit der Entwicklung von Code Komponenten. Die schnellste Möglichkeit zum Einstieg besteht darin, dass Sie `code .` über die Eingabeaufforderung ausführen, sobald Sie sich im `C:\Users\<your name>\Documents\<My_PCF_Component>` Verzeichnis befinden. Dieser Befehl öffnet das Komponenten Projekt in Visual Studio Code.

## <a name="implementing-manifest"></a>Implementieren des Manifests

Manifest ist eine XML-Datei, die die Metadaten der Code Komponente enthält. Außerdem wird das Verhalten der Code Komponente definiert. In diesem Lernprogramm wird diese Manifest-Datei unter dem `<Your component Name>` Unterordner erstellt. Wenn Sie die `ControlManifest.Input.xml` Datei in Visual Studio Code öffnen, werden Sie feststellen, dass die Manifest-Datei mit einigen Eigenschaften vordefiniert ist. Nehmen Sie Änderungen an der vordefinierten Manifest-Datei vor, wie hier gezeigt:

1. Der [Steuer](manifest-schema-reference/control.md) Knoten definiert den Namespace, die Version und den anzeigen amen der Code Komponente. Definieren Sie nun jede Eigenschaft des [Steuer](manifest-schema-reference/control.md) Element Knotens, wie hier gezeigt:

   - **Namespace**: der Namespace der Code Komponente. 
   - **Konstruktor**: Konstruktor der Code Komponente.
   - **Version**: Version der Komponente. Wenn Sie die Komponente aktualisieren, müssen Sie die Version aktualisieren, um die Änderungen in der Laufzeit anzuzeigen.
   - **Display-Name-Key**: Name der Code Komponente, die auf der Benutzeroberfläche angezeigt wird.
   - **Description-Name-Key**: Beschreibung der Code Komponente, die auf der Benutzeroberfläche angezeigt wird.
   - **Control-Type**: der Code Komponententyp. Es werden nur *Standardtyp* von Code Komponenten unterstützt.

     ```XML
      <?xml version="1.0" encoding="utf-8" ?>
      <manifest>
      <control namespace="SampleNameSpace" constructor="TSLinearInputComponent" version="1.0.0" display-name-key="Linear Input Component" description-key="Allows you to enter the numeric values using the visual slider." control-type="standard">
     ```

2. Der [Eigenschafts](manifest-schema-reference/property.md) Knoten definiert die Eigenschaften der Code Komponente wie das Definieren des Datentyps des Felds. Der Eigenschafts Knoten wird als untergeordnetes Element unter dem Steuerelement angegeben. Definieren Sie den [Eigenschafts](manifest-schema-reference/property.md) Knoten, wie hier gezeigt:

   - **Name**: Name der Eigenschaft.
   - **Display-Name-Key**: Anzeige Name der Eigenschaft, die auf der Benutzeroberfläche angezeigt wird.
   - **Description-Name-Key**: Beschreibung der Eigenschaft, die auf der Benutzeroberfläche angezeigt wird. 
   - **von-Type-Group**: der [von-Type-Group](manifest-schema-reference/type-group.md) wird verwendet, wenn Sie mehr als zwei Datentyp Felder verwenden möchten. Fügen Sie dem `property`-Element im Manifest das [vom-Type-Group-](manifest-schema-reference/type-group.md) Element als gleich geordnetes Element hinzu. Der-`of-type-group` gibt den Komponenten Wert an und kann ganze, Währungs-, Gleit Komma-oder Dezimalwerte enthalten.
   - **Verwendung**: verfügt über zwei Eigenschaften: *gebunden* und *Eingabe*. Gebundene Eigenschaften werden nur an den Wert des Felds gebunden. Eingabe Eigenschaften werden entweder an ein Feld gebunden oder geben einen statischen Wert an.
   - **erforderlich**: definiert, ob die-Eigenschaft erforderlich ist.

     ```XML
      <property name="sliderValue" display-name-key="sliderValue_Display_Key" description-key="sliderValue_Desc_Key" of-type-group="numbers" usage="bound" required="true" />
      ```
3. Der Knoten [Ressourcen](manifest-schema-reference/resources.md) definiert die Visualisierung der Code Komponente. Sie enthält alle Ressourcen, die die Code Komponente bilden. Der [Code](manifest-schema-reference/code.md) wird als untergeordnetes Element unter dem Resources-Element angegeben. Definieren Sie die [Ressourcen](manifest-schema-reference/resources.md) wie hier gezeigt:

   - **Code**: bezieht sich auf den Pfad, in dem sich alle Ressourcen Dateien befinden.
 
      ```XML
      <resources>
        <code path="index.ts" order="1" />
        <css path="css/TS_LinearInputComponent.css" order="1" />
        </resources>
        ```
      Die Manifest-Gesamt Datei sollte in etwa wie folgt aussehen: 

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
5. Erstellen Sie nun einen neuen Ordner im Ordner "`TSLinearInputComponent`", und nennen Sie ihn " **CSS**".
6. Erstellen Sie eine CSS-Datei, um [der Code Komponente formatieren hinzuzufügen](#adding-style-to-the-code-component).
7. Erstellen Sie das Komponenten Projekt mithilfe des Befehls `npm run build`.
8. Der Build generiert eine aktualisierte typescript-typdeklarations Datei im Ordner "`TSLinearInputComponent/generated`".

## <a name="implementing-component-logic"></a>Implementieren von Komponenten Logik

Der nächste Schritt nach der Implementierung der Manifest-Datei besteht darin, die Komponenten Logik mithilfe von typescript zu implementieren. Die Komponenten Logik sollte in der `index.ts`-Datei implementiert werden. Wenn Sie die `index.ts` Datei im Visual Studio Code öffnen, werden Sie feststellen, dass die vier wichtigen Klassen vordefiniert sind. Nun implementieren wir die Logik für die Code Komponente. 

1. Öffnen Sie die Datei `index.ts` im Code-Editor Ihrer Wahl.
2. Aktualisieren Sie die `TSLinearInputComponent`-Klasse mit folgendem Code:

```TypeScript
import { IInputs, IOutputs } from "./generated/ManifestTypes";
export class TSLinearInputComponent
  implements ComponentFramework.StandardControl<IInputs, IOutputs> {
  // Value of the field is stored and used inside the component
  private _value: number;
  // PowerApps component framework delegate which will be assigned to this object which would be called whenever any update happens.
  private _notifyOutputChanged: () => void;
  // label element created as part of this component
  private labelElement: HTMLLabelElement;
  // input element that is used to create the range slider
  private inputElement: HTMLInputElement;
  // reference to the component container HTMLDivElement
  // This element contains all elements of our code component example
  private _container: HTMLDivElement;
  // reference to PowerApps component framework Context object
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
    this.inputElement.setAttribute(
      "value",
      context.parameters.sliderValue.formatted
        ? context.parameters.sliderValue.formatted
        : "0"
    );
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
    this.inputElement.setAttribute(
      "value",
      context.parameters.sliderValue.formatted
        ? context.parameters.sliderValue.formatted
        : ""
    );
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
 
4. Die Komponente wird in den `out/controls/TSLinearInputComponent` Ordner kompiliert. Die buildartefakte umfassen:

   - Bundle. js – Komponentenquellcode für gebündelte Komponente. 
   - Controlmanifest. XML – tatsächliche Komponenten Manifest-Datei, die in die Common Data Service Organisation hochgeladen wird.

## <a name="adding-style-to-the-code-component"></a>Hinzufügen von Stil zur Code Komponente

Entwickler und App-Ersteller können Ihre Formatierung definieren, um Ihre Code Komponenten visuell mithilfe von CSS darzustellen. CSS ermöglicht Entwicklern das Beschreiben der Darstellung von Code Komponenten, einschließlich Stil, Farben, Layouts und Schriftarten. Die [Init](reference/control/init.md) -Methode der linearen Eingabe Komponente erstellt ein input-Element und legt das Class-Attribut auf `linearslider` fest. Der Stil für die `linearslider`-Klasse wird in einer separaten `CSS` Datei definiert. Zusätzliche Komponenten Ressourcen wie `CSS` Dateien können in der Code Komponente enthalten sein, um weitere Anpassungen zu unterstützen.

1. Erstellen Sie einen neuen `css` Unterordner unter dem Ordner `TSLinearInputComponent`. 
2. Erstellen Sie eine neue `TS_LinearInputComponent.css` Datei im Unterordner `css`. 
3. Fügen Sie den folgenden Stil Inhalt der `TS_LinearInputComponent.css` Datei hinzu:

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

5. Speichern Sie die `TS_LinearInputComponent.css` Datei.
6. Bearbeiten Sie die Datei `ControlManifest.Input.xml`, um die `CSS` Ressourcen Datei in das Resources-Element einzuschließen.
 
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
8. Überprüfen Sie die Buildausgabe unter **./out/Controls/TSLinearInputComponent** , und beobachten Sie, dass die Datei **TS_LinearInputComponent. CSS** nun in den kompilierten buildartefakte enthalten ist. 

## <a name="debugging-your-code-component"></a>Debuggen der Code Komponente

Nachdem Sie die Code Komponenten Logik implementiert haben, führen Sie den folgenden Befehl aus, um den Debugprozess zu starten. Weitere Informationen: [Debuggen von Code Komponenten](debugging-custom-controls.md)

```CLI
npm start
```

## <a name="packaging-your-code-components"></a>Verpacken der Code Komponenten

Führen Sie zum Erstellen und [Importieren einer](https://docs.microsoft.com/dynamics365/customer-engagement/customize/solutions-overview) Projektmappendatei die folgenden Schritte aus:

1. Erstellen Sie im Ordner **linearcomponent** eine **neue Ordner Projekt** Mappe, und navigieren Sie zum Ordner. 
2. Erstellen Sie mit dem folgenden Befehl ein neues Projektmappenprojekt im Ordner **linearcomponent** :
 
    ```CLI
     pac solution init --publisher-name developer --publisher-prefix dev 
    ```

   > [!NOTE]
   > Die Werte für " [Publisher-Name](https://docs.microsoft.com/powerapps/developer/common-data-service/reference/entities/publisher) " und " [Publisher-Prefix](https://docs.microsoft.com/powerapps/maker/common-data-service/change-solution-publisher-prefix) " müssen für Ihre Umgebung eindeutig sein.
 
3. Nachdem das neue Projektmappenprojekt erstellt wurde, müssen Sie auf den Speicherort verweisen, an dem sich die erstellte Komponente befindet. Sie können den Verweis mit dem folgenden Befehl hinzufügen:

    ```CLI
     pac solution add-reference --path c:\users\LinearComponent
    ```

4. Um eine ZIP-Datei aus dem Projektmappenprojekt zu generieren, müssen Sie in das projektmappenprojektverzeichnis `cd` und das Projekt mithilfe des folgenden Befehls erstellen: 

    ```CLI
     msbuild /t:restore
    ```

5. Führen Sie den folgenden Befehl MSBuild aus:
    ```CLI
     msbuild
    ```

    > [!NOTE]
    > Stellen Sie sicher, dass **nuget-Ziele & Buildaufgaben** aktiviert ist. So aktivieren Sie Sie:
    > - Öffnen Sie **Visual Studio-Installer**.
    > - Wählen Sie für Visual Studio 2017 die Option **ändern**aus.
    > - Wählen Sie **einzelne Komponenten**aus.
    > - Aktivieren Sie unter **Code Tools**die Option **nuget-Ziele & Buildaufgaben**.

6. Die generierte ZIP-Datei der Projekt Mappe befindet sich im Ordner "`Solution\bin\debug`".
7. [Importieren Sie die Lösung manuell in Common Data Service](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/customize/import-update-upgrade-solution) mithilfe des Webportals, sobald die ZIP-Datei bereit ist, oder sehen Sie sich die Abschnitte [Authentifizieren bei Ihrer Organisation](import-custom-controls.md#authenticating-to-your-organization) und [Bereitstellung](import-custom-controls.md#deploying-code-components) an, um Sie mithilfe von CLI-Befehlen von powerapps

## <a name="adding-code-components-in-model-driven-apps"></a>Hinzufügen von Code Komponenten in Modell gesteuerten apps

Um eine Code Komponente wie eine lineare Eingabe Komponente hinzuzufügen, führen Sie die im Thema [Hinzufügen von Komponenten zu Feldern und Entitäten](add-custom-controls-to-a-field-or-entity.md)beschriebenen Schritte aus.

## <a name="adding-code-components-to-a-canvas-app"></a>Hinzufügen von Code Komponenten zu einer Canvas-App

Um die Code Komponenten einer Canvas-App hinzuzufügen, führen Sie die Schritte im Thema [Hinzufügen von Code Komponenten zu einer Canvas-App](component-framework-for-canvas-apps.md#add-components-to-a-canvas-app)aus.

### <a name="see-also"></a>Siehe auch

[Beispiel Komponenten herunterladen](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[Aktualisieren vorhandener Komponenten Framework-Komponenten von powerapps](updating-existing-controls.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](overview.md)
