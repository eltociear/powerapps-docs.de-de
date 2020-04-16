---
title: 'Lernprogramm: Erstellen von Workflow-Erweiterungen (Common Data Service) | Microsoft Docs'
description: In diesem Lernprogramm wird der Prozess gezeigt, um den Workflowdesigner zu erweitern, um benutzerdefinierte Aktivitäten und Logik unter Verwendung einer Workflow-Assembly hinzufügen
ms.custom: ''
ms.date: 07/16/2019
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: fc3f08ac3422a50c3e1580d923aa941bba253c23
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3154906"
---
# <a name="tutorial-create-workflow-extension"></a>Lernprogramm: Erstellen einer Workflow-Erweiterung

In diesem Lernprogramm wird der Prozess gezeigt, um den Workflowdesigner zu erweitern, um benutzerdefinierte Aktivitäten und Logik unter Verwendung einer Workflow-Assembly hinzufügen, gelegentlich als Workflowaktivität bezeichnet. Die Erweiterungen, die Sie auf diese Weise erstellen, können innerhalb eines Workflows, eine benutzerdefinierten Aktion oder eines Dialogs verwendet werden.

In diesem Lernprogramm wird ein sehr einfaches Beispiel verwendet, den Fokus auf die Anforderungen und den Prozess zu konzentrieren, um:

- Erstellen eines Visual Studio Klassenbibliotheksprojektes
- Eine CodeActivity-Klasse hinzufügen
- Ein- und Ausgabeparameter definieren
- Fügen Sie Ihre Geschäftslogik hinzu
- Die Assembly signieren und erstellen
- Registrieren Ihrer Assembly
- Testen Sie Ihre Assembly
- Hinzufügen der Assembly zu einer Lösung

## <a name="prerequisites"></a>Voraussetzungen

- Eine Common Data Service-Instanz und Administratorrechte
- Verstehen, wie Workflows konfiguriert werden. Weitere Informationen: [Klassische Common Data Service-Workflows](/flow/workflow-processes)
- Eine modellgesteuerte App, die es Ihnen ermöglicht, Firmen zu bearbeiten.

## <a name="goal"></a>Ziel

Im folgenden Beispiel wird eine einfache benutzerdefinierte Workflowaktivität erstellt, die in einem Workflow, in einem Dialogfeld oder in einem Aktionsprozess verwendet werden kann. Weitere Informationen: [Workflowphasen und Schritte konfigurieren](/flow/configure-workflow-steps)

Diese benutzerdefinierte Workflowaktivität vergleicht die folgenden Anforderungen:

1. Akzeptieren eines dezimalen Eingabeparameters
1. Ausgeben eines Werts gleich dem Eingabeparameter plus 10.

In einem Workflow für die **Firma**-Entität kann er auf folgende Weise verwendet werden, um den Wert **Kreditlimit** mit zwei Schritte zu erhöhen:

![Ziel des Lernprogramms](media/tutorial-create-workflow-activity-goal.png)

Schritt 1 verwendet die benutzerdefinierte Workflowaktivität **Beispiel: Erhöhung um 10**, um den Wert **Firmen-Kreditlimit** zu akzeptieren und um 10 zu erhöhen.
Schritt 2 verwendet die Aktion **Datensatz aktualisieren**, um den Wert **Firmen-Kreditlimit** mit dem erhöhten Wert zu aktualisieren.

### <a name="step-1-get-incremented-account-credit-limit"></a>Schritt 1:Erhöhten Firmen-Kreditlimit abrufen

Wenn der erste Schritt hinzugefügt wurde, ist die benutzerdefinierte Workflowaktivität in einer **Probe**-Gruppe verfügbar und trägt dem Namen **Erhöhen um 10**.

![Der Schritt "Erhöhen um 10"](media/tutorial-create-workflow-activity-increment-by-10-step.png)

Beim der Konfigurierung des ersten Schritts durch Klicken auf die Schaltfläche **Eigenschaften festlegen**, ist die Eigenschaft **Dezimalzahleingabe** erforderlich und akzeptiert nur einen Dezimalwert, wie das Attribut **Kreditlimit** der Entität **Firma**.

![Festlegen der Dezimaleingabe](media/tutorial-create-workflow-activity-step1.png)

### <a name="step-2-set-new-account-credit-limit"></a>Schritt 2: Festlegen eines neuen Firmen-Kreditlimits

Im zweiten Schritt weist die Aktion **Datensatz aktualisieren** die Ausgabe des Schritts **Erhöhtes Firmen-Kreditlimit abrufen** zu, um den Limitwert **Firmen-Kredit** mit dem erhöhten Wert zu aktualisieren.

![Aktualisieren Sie des Kreditlimits](media/tutorial-create-workflow-activity-step2.png)

## <a name="create-a-visual-studio-class-library-project"></a>Erstellen eines Visual Studio Klassenbibliotheksprojektes

Dies Projekt erstellt eine einfache Workflow-Assembly, die einen Dezimalwert um 10 erhöht.

1. Starten Sie Visual Studio.
1. Klicken Sie im Menü **Datei** auf **Neu** und dann auf **Projekt**.
1. Suchen Sie nach *Klassenbibliothek* und wählen Sie **Klassenbibliothek (.NET Framework)**.

    ![Suche nach Klassenbibliothek (.NET Framework)](media/create-new-class-library-project.png)

1. Klicken Sie auf **Weiter**.
1. Geben Sie einen Namen und einen Ort für die Lösung an.

    ![Konfigurieren Sie Ihren neuen Projektdialog in Visual Studio 2019.](media/configure-your-new-project.png)

    > [!NOTE]
    > Wählen Sie einen Projektnamen, der für Ihr Projekt sinnvoll ist. In diesem Beispiel verwenden wir `SampleWorkflowActivity`.

1. Klicken Sie auf **Erstellen**.
1. Klicken Sie im **Lösungs-Explorer** mit der rechten Maustaste auf das Projekt und wählen Sie **Eigenschaften**. Überprüfen Sie auf der Registerkarte **Anwendung**, ob **.NET Framework 4.6.2** als Zielframework eingestellt ist.

    ![Projekteigenschaften festlegen](media/tutorial-create-workflow-activity-workflow-project.png)

1. Klicken Sie im **Lösungs-Explorer** mit der rechten Maustaste auf das Projekt und wählen Sie **Verwalten von NuGet Paketen ...** .

    ![NuGet-Package verwalten](media/tutorial-create-workflow-activity-manage-nuget-packages.png)

1. Suchen Sie nach dem [Microsoft.CrmSdk.Workflow](https://www.nuget.org/packages/Microsoft.CrmSdk.Workflow/)-NuGet-Paket und installieren Sie es.

    ![Microsoft.CrmSdk.Workflow Workflow Workflow NuGet-Paket installieren](media/select-install-microsoft.crmsdk.workflow-nuget-package.png)

    > [!NOTE]
    > Stellen Sie sicher, dass das Paket, das Sie installieren im Besitz von [crmsdk](https://www.nuget.org/profiles/crmsdk) ist. Dieses Paket enthält `Microsoft.Xrm.Workflow.dll`, einer Abhängigkeit des [Microsoft.CrmSdk.CoreAssemblies](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreAssemblies/)-Pakets, sodass die erforderliche `Microsoft.Xrm.Sdk.dll`-Assembly auch enthalten ist. 

1. Sie müssen auf **Ich akzeptiere** im Dialog **Lizenz annehmen** klicken.

    ![Lizenzvertrag akzeptieren](media/tutorial-create-workflow-activity-license-acceptance.png)

## <a name="rename-the-class-file"></a>Umbenennen der Klassendatei

1. Klicken Sie im **Lösungs-Explorer** mit der rechten Maustaste auf die Standard Class1.cs-Datei und wählen Sie **Umbenennen**.

    ![Umbenennen der Class1.cs-Datei](media/rename-class1-file.png)

    > [!NOTE]
    > Wählen Sie einen Klassennamen aus, der für die Aktivität sinnvoll ist. In diesem Beispiel nennen wir die Klasse `IncrementByTen`.

1. Wählen Sie **Ja** im Dialogfenster, das Sie fragt, ob Sie die Klasse ebenfalls umbenennen möchten.

    ![Wählen Sie Ja, um die Klasse ebenfalls umzubenennen.](media/rename-file-dialog.png)

1. Öffnen Sie die Datei "IncrementByTen.cs", und fügen Sie die folgenden Verwendungsanweisungen hinzu:

    ```csharp
    using System.Activities;
    using Microsoft.Xrm.Sdk;
    using Microsoft.Xrm.Sdk.Workflow;
    ```

1. Legen Sie fest, dass die Klasse von der [CodeActivity](/dotnet/api/system.activities.codeactivity)-Klasse erbt und weisen Sie ihr einen öffentlichen Zugriffs-Modifizierer wie nachfolgend gezeigt zu:

    ```csharp
    public class IncrementByTen: CodeActivity
        {

        }
    ```

1. Fügen Sie die **Ausführen**-Methode aus der `CodeActivity`-Klasse mit Visual Studio-Schnellaktionen oder manuell hinzu:

    ![Codeaktivitätsschnittstelle implementieren](media/tutorial-create-workflow-activity-implement-codeactivity-interface.png)

1. Diese Klasse sieht nun wie folgt aus:

    ```csharp
    public class IncrementByTen : CodeActivity
    {
        protected override void Execute(CodeActivityContext context)
        {
            throw new NotImplementedException();
        }
    }
    ```

## <a name="define-input-and-output-parameters"></a>Ein- und Ausgabeparameter definieren

1. Fügen Sie einen Satz von Ein- und Ausgabeparameter hinzu, wobei der Wert des Ausgabeparameters der Wert des Eingabeparameters ist, der um 10 erhöht wurde.

    ```csharp
    public class IncrementByTen : CodeActivity
    {
        [RequiredArgument]
        [Input("Decimal input")]
        public InArgument<decimal> DecInput { get; set; }

        [Output("Decimal output")]
        public OutArgument<decimal> DecOutput { get; set; }

        protected override void Execute(CodeActivityContext context)
        {
            
        }
    }
    ```

    > [!NOTE]
    > Beachten Sie, wie [.NET-Attribute](/dotnet/standard/attributes) verwendet werden, um Metadaten zu den Parametern in der Assembly bereitzustellen. Weitere Informationen: [Parameter hinzufügen](workflow-extensions.md#add-parameters)

## <a name="add-your-business-logic"></a>Fügen Sie Ihre Geschäftslogik hinzu

Fügen Sie innerhalb der Ausführungsmethode Logik hinzu, um die Logik anwenden, um den Eingabewert um 10 zu erhöhen.

```csharp
    protected override void Execute(CodeActivityContext context)
    {
      decimal input = DecInput.Get(context);
      DecOutput.Set(context, input + 10);
    }
```

## <a name="sign-and-build-the-assembly"></a>Die Assembly signieren und erstellen

1. Die benutzerdefinierten Workflowaktivitäts- (und Plug-In)-Assemblys müssen signiert sein. Wählen Sie in den Projekteigenschaften unter der Registerkarte **Signieren** **Assemby signieren**. Wählen Sie unter **Starker Name für Schlüsseldatei wählen** Sie die Option **&lt;Neu...&gt;**.
    Sie müssen im Rahmen dieses Lernprogramms kein Kennwort festlegen. In diesem Beispiel haben wir eine neue Schlüsseldatei namens `SampleWorkflowActivity.snk` erstellt

    ![Assembly signieren](media/tutorial-create-workflow-activity-sign-assembly.png)

1. Erstellen Sie die Lösung im Debugmodus und überprüfen Sie, dass sich die `SampleWorkflowActivity.dll`-Assembly im Ordner `/bin/Debug` befindet.

> [!NOTE]
> Bei der Entwicklung einer Assembly ist es in Ordnung, die **Debug** Build-Konfiguration zu verwenden. Wenn Sie Ihre Assembly auf einem Produktionsserver oder in einer Lösung bereitstellen, sollten Sie die Build-Konfiguration **Release** verwenden.

## <a name="register-your-assembly"></a>Registrieren Ihrer Assembly

Benutzerdefinierte Workflowaktivitätsassemblys werden mithilfe des Plug-In-Registrierungs-Tools registriert. Dieses Tool stellt eine grafische Benutzeroberfläche bereit und unterstützt das Registrieren Assemblys, die Plug-Ins oder benutzerdefinierte Workflowaktivitäten enthalten. Das Plug-In-Registrierungstool finden Sie unter: [Tools von NuGet herunterladen](../download-tools-nuget.md)

[!INCLUDE [cc-connect-plugin-registration-tool](../includes/cc-connect-plugin-registration-tool.md)]

### <a name="register-your-assembly"></a>Registrieren Ihrer Assembly

1. Wählen Sie **Registrieren** > **Neue Assembly registrieren** aus.

    ![Assemblybefehl registrieren](media/tutorial-create-workflow-activity-register-assembly.png)

1. Klicken Sie im Dialogfeld **Neue Assembly registrieren** auf die Schaltfläche mit den Auslassungspunkten (**...**) und navigieren Sie zu `SampleWorkflowActivity.dll` im Ordner `/bin/Debug`.

    ![Assembly-Dialog registrieren](media/tutorial-create-workflow-activity-register-assembly-dialog.png)

    > [!NOTE]
    > Hinweis: Bei Common Data Service werden die gültigen Optionen für die Schritte 3 und 4 ausgewählt und ungültige Optionen deaktiviert.

1. Wählen Sie **Ausgewählte Plug-ins registrieren** aus. Es sollte ein Bestätigungsdialogfeld angezeigt werden.

    ![Plug-In-Dialog registriert](media/tutorial-create-workflow-activity-register-plug-in-dialog.png)

1. Klicken Sie auf **OK**, um das Dialogfeld **Neue Assembly registrieren** zu schließen.

### <a name="configure-activity-names"></a>Konfigurieren von Aktivitätsnamen

1. Suchen Sie in der Liste **Registrierte Plug-Ins und benutzerdefinierter Workflowaktivitäten** nach **(Assembly) SampleWorkflowActivity** und erweitern Sie diese, um **(Workflowaktivität) SampleWorkflow.Activity.IncrementByTen - Isolatable** anzuzeigen.
1. Wählen Sie **(Workflowaktivität) SampleWorkflow.Activity.IncrementByTen - Isolatable** aus, und bearbeiten Sie im Bereich **Eigenschaften** die **Bearbeitbaren Eigenschaften** mit den Werten in der folgenden Tabelle:

    |Bearbeitbares Feld|Ursprünglicher Wert|Neuer Wert|Beschreibung|
    |--|--|--|--|
    |Beschreibung||Gibt den Wert des Eingabeparameters plus 10 zurück.|Wird in der Benutzeroberfläche des Prozessdesigners nicht angezeigt, kann aber bei der Erstellung der Dokumentation von Daten aus der PluginType-Entität hilfreich sein, in der diese Informationen gespeichert werden.|
    |FriendlyName|ein GUID-Wert|IncrementByTen|Anzeigename des Benutzers für das Plug-In.|
    |Name|SampleWorkflowActivity.IncrementByTen|Erhöhen um 10|Der Name des dargestellten Menüs.|
    |WorkflowActivityGroupName|SampleWorkflowActivity (1.0.0.0)|Probe|Der Name des Untermenüs, das dem Hauptmenü im Common Data Service Prozess hinzugefügt wurde.|

    > [!NOTE]
    > Wenn **Name** und **WorkflowActivityGroupName** auf null festgelegt sind, wird die benutzerdefinierte Aktivität nicht im Prozessdesigner angezeigt.

1. Klicken Sie auf **Speichern** (Symbol), um die Änderungen zu speichern.

    ![Speichern der Workflowaktivitätseigenschaften](media/tutorial-create-workflow-activity-set-workflow-activity-properties.png)

## <a name="test-your-assembly"></a>Testen Sie Ihre Assembly

Sie können Ihre neue Workflowaktivität testen, indem Sie einen Prozess erstellen, der sie verwendet. Führen Sie diese Schritte aus, um den Workflowprozess zu erstellen, der im obigen Abschnitt [Ziel](#goal) beschrieben wird:

1. [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) öffnen
1. Wählen Sie **Lösungen** aus.
1. Öffnen Sie die Lösung **CDS Default Publisher**.
1. Erweitern Sie im Menü die Option **...** und wählen Sie **Wechsel zu klassisch**.
    
    ![Wechseln Sie zur klassischen Benutzeroberfläche](media/switch-to-classic-solution-ui.png)

1. Wählen Sie **Prozesse** in der Liste **Komponenten** aus.
1. Wählen Sie **Neu** aus, und geben Sie im Dialogfeld **Prozess erstellen** Folgendes ein:

    |Feld|Value|
    |--|--|
    |Prozessname|Test von SampleWorkflowActivity.IncrementByTen|
    |Kateg.|Workflow|
    |Entität|Firma|
    |Diesen Workflow im Hintergrund ausführen (empfohlen)|Auswahl aufgehoben|

    > [!NOTE]
    > Die Auswahl der Option **Diesen Workflow im Hintergrund ausführen** wurde aufgehoben, um einen Echtzeit-Workflow (synchron) zu erstellen. Dies erleichtert das Testen.

    ![Erstellen eines Prozesses](media/tutorial-create-workflow-activity-test-activity-process.png)

1. Klicken Sie auf **OK**.
1. Übernehmen Sie die folgenden Änderungen:

    |Feld|Value|
    |--|--|
    |Bereich|Organisation|
    |Starten wenn: Datensatzfelder geändert werden|ausgewählt und `name`-Feld im Dialogfeld angegeben.|

    ![Konfiguration eines Testworkflows](media/tutorial-create-workflow-activity-configuration-test-workflow.png)

    > [!NOTE]
    > Das Festlegen von **Bereich** auf **Organisation** erzeugt einen Workflow, der von jedem in der Organisation angewendet werden kann.

1. Fügen Sie den folgenden **Schritt** hinzu:

    ![Fügen Sie den Schritt "SampleWorkflowActivity.IncrementByTen" hinzu](media/tutorial-create-workflow-activity-use-sample-step.png)

1. Legen Sie den Schritt **Beschreibung** auf **Erhöhten Firmen-Kreditlimit abrufen** fest, und klicken Sie auf **Eigenschaften festlegen**.
1. Legen Sie den Wert der Eigenschaft **Dezimaleingabe** auf mit dem Standardwert 0 das Kreditlimit der Firma fest.

    ![Die Dezimaleingabe-Eigenschaft festlegen](media/tutorial-create-workflow-activity-configure-first-step.png)

1. Klicken Sie auf **Speichern und schließen**.
1. Fügen Sie einen **Datensatz erstellen**-Schritt hinzu:

    ![Hinzufügen eines "Datensatz aktualisieren" Schritts](media/tutorial-create-workflow-activity-add-update-record-step.png)

1. Klicken Sie auf **Eigenschaften festlegen**, und legen Sie den Wert **Kreditlimit** auf den Wert des Schritts **Erhöhtes Firmen-Kreditlimit** fest.

    ![Den Wert des Kreditlimits festlegen](media/tutorial-create-workflow-activity-set-credit-limit.png)

    Die Workflowschritte sollten ungefähr wie folgt aussehen:

    ![Das vollständige Workflow](media/tutorial-create-workflow-activity-completed-workflow.png)

1. Klicken Sie auf **Speichern und schließen**.
1. Aktivieren Sie das Workflows, indem Sie im Menü auf **Aktivieren** klicken...

    ![Workflowbefehl aktivieren](media/tutorial-create-workflow-activity-activate-command.png)

1. Und klicken Sie im Dialogfeld **Bestätigung der Prozessaktivierung** auf **Aktivieren**.

    ![Dialog "Bestätigung der Prozessaktivierung"](media/tutorial-create-workflow-activity-process-activate-confirmation-dialog.png)

1. Navigieren Sie zu einer modellgesteuerten App und zeigen Sie eine Liste der Firmen an.
1. Auswahl einer Firma.
1. Bearbeiten Sie den Feldwert **Firmenname**.
1. Speichern Sie den Firmendatensatz.
1. Stellen Sie sicher, dass die Firma, die Sie bearbeitetet haben den Wert **Kreditlimit** um 10 erhöht hat.

    ![Firmen-Kreditlimiterhöhung bestätigen](media/tutorial-create-workflow-verify-credit-limit.png)

## <a name="add-your-assembly-to-a-solution"></a>Hinzufügen der Assembly zu einer Lösung

Um eine benutzerdefinierte Workflowaktivität in einer Lösung zu verteilen, müssen Sie die registrierte Assembly, die sie enthält, einer nicht verwalteten Lösung hinzufügen.

1. Öffnen Sie die nicht verwaltete Lösung, der Sie die Assembly hinzufügen möchten, mit [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)
1. Wählen Sie **Bestehendes hinzufügen** > **Weitere** > **Plugin-Assembly**.

    ![Vorhandenes Plugin-Assembly hinzufügen](media/add-existing-plugin-assembly.png)

1. Suchen Sie nach dem Plugin-Assembly mit dem Namen - in diesem Fall 'SampleWorkflowActivity'.
1. Wählen Sie das Plugin-Assembly aus und wählen Sie **Hinzufügen**.

### <a name="see-also"></a>Siehe auch

[Workflowerweiterungen](workflow-extensions.md)<br />
[Beispiel: Eine benutzerdefinierte Workflowaktivität erstellen](sample-create-custom-workflow-activity.md)<br />
[Beispiel: Aktualisieren des nächsten Geburtstags mithilfe einer benutzerdefinierten Workflowaktivität](sample-update-next-birthday-using-custom-workflow-activity.md)<br />
[Beispiel: Berechnen Sie mit einer benutzerdefinierten Workflowaktivität einen Kreditscore](sample-calculate-credit-score-custom-workflow-activity.md)