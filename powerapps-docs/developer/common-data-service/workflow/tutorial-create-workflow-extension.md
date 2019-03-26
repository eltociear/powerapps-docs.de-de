---
title: 'Lernprogramm: Erstellen von Workflow-Erweiterungen (Common Data Service für Apps) | Microsoft Docs'
description: <Description>
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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
---
# <a name="tutorial-create-workflow-extension"></a>Lernprogramm: Erstellen einer Workflow-Erweiterung

In diesem Lernprogramm wird der Prozess gezeigt, um den Workflowdesigner zu erweitern, um benutzerdefinierte Aktivitäten und Logik unter Verwendung einer Workflow-Assembly hinzufügen, gelegentlich als Workflowaktivität bezeichnet. Die Erweiterungen, die Sie auf diese Weise erstellen, können innerhalb eines Workflows, eine benutzerdefinierten Aktion oder eines Dialogs verwendet werden.

In diesem Lernprogramm wird ein sehr einfaches Beispiel verwendet, den Fokus auf die Anforderungen und den Prozess zu konzentrieren, um:

- Ein Visual Studio-Aktivitätsbibliotheksprojekt zu erstellen
- Eine CodeActivity-Klasse hinzufügen
- Ein- und Ausgabeparameter definieren
- Fügen Sie Ihre Geschäftslogik hinzu
- Die Assembly signieren und erstellen
- Registrieren Ihrer Assembly
- Testen Sie Ihre Assembly
- Hinzufügen der Assembly zu einer Lösung

## <a name="prerequisites"></a>Voraussetzungen

- Sie müssen Windows Workflow Foundation als einzelne Komponente in Visual Studio 2017 integrieren.  Weitere Informationen: [Visual Studio-Anforderungen](workflow-extensions.md#visual-studio-requirements)
- Eine Common Data Service for Apps-Instanz und Administratorrechte
- Verstehen, wie Workflows konfiguriert werden. Weitere Informationen: [Klassische Common Data Service (CDS) für Apps-Workflows](/flow/workflow-processes)
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

## <a name="create-a-visual-studio-activity-library-project"></a>Ein Visual Studio-Aktivitätsbibliotheksprojekt zu erstellen

Dies Projekt erstellt eine einfache Workflow-Assembly, die einen Dezimalwert um 10 erhöht.

1. Visual Studio starten.
1. Klicken Sie im Menü **Datei** auf **Neu** und dann auf **Projekt**.
1. Erweitern Sie im Dialogfeld **Neues Projekt** unter **Andere Sprache** die Option "Visual C#" und wählen Sie **Workflow** und dann **Aktivitätsbibliothek** aus.
1. Geben Sie einen Namen und einen Speicherort für die Lösung ein, und klicken Sie dann auf **OK**.

    > [!NOTE]
    > Wählen Sie einen Lösungsnamen aus, der für das Projekt sinnvoll ist. In diesem Beispiel verwenden wir `SampleWorkflowActivity`.

    ![Workflowaktivitätsprojekt erstellen](media/tutorial-create-workflow-activity-create-workflow-activity-project.png)

1. Navigieren Sie zum Menü **Projekt** und wählen Sie **Eigenschaften** aus. Geben Sie auf der Registerkarte **Anwendung** als Zielframework **.NET Framework 4.6.2** an.

    ![Projekteigenschaften festlegen](media/tutorial-create-workflow-activity-workflow-project.png)

1. Löschen Sie die `Activity1.xaml`-Datei im Projekt.
1. Klicken Sie im Lösungsexplorer mit der rechten Maustaste in das Projekt und wählen Sie **NuGet Pakete verwalten...** aus. .

    ![NuGet-Package verwalten](media/tutorial-create-workflow-activity-manage-nuget-packages.png)

1. Suchen Sie nach dem [Microsoft.CrmSdk.Workflow](https://www.nuget.org/packages/Microsoft.CrmSdk.Workflow/) NuGet-Paket und installieren Sie es.

    > [!NOTE]
    > Stellen Sie sicher, dass das Paket, das Sie installieren im Besitz von [crmsdk](https://www.nuget.org/profiles/crmsdk) ist. Dieses Paket enthält `Microsoft.Xrm.Workflow.dll`, einer Abhängigkeit des [Microsoft.CrmSdk.CoreAssemblies](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreAssemblies/)-Pakets, sodass die erforderliche `Microsoft.Xrm.Sdk.dll`-Assembly auch enthalten ist. 

1. Sie müssen auf **Ich stimme zu** im Dialogfeld "Lizenz-Abnahme" klicken.

    ![Lizenzvertrag akzeptieren](media/tutorial-create-workflow-activity-license-acceptance.png)

## <a name="add-a-codeactivity-class"></a>Eine CodeActivity-Klasse hinzufügen

1. Fügen Sie eine Klassendatei (.cs) zum Projekt hinzu. Klicken Sie im **Lösungsexplorer** mit der rechten Maustaste auf das Projekt, wählen Sie **Hinzufügen** aus, und klicken Sie dann auf **Klasse**. Geben Sie im Dialogfeld **Neues Element hinzufügen** einen Namen für die Klasse ein, und klicken Sie dann auf **Hinzufügen**.

    > [!NOTE]
    > Wählen Sie einen Klassennamen aus, der für die Aktivität sinnvoll ist. In diesem Beispiel nennen wir die Klasse `IncrementByTen`.

    ![Hinzufügen einer Klasse](media/tutorial-create-workflow-activity-add-class.png)

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

1. Signieren Sie die Assembly. Wählen Sie in den Projekteigenschaften unter der Registerkarte **Signierung** die Option **Assembly signieren** aus und geben Sie einen Schlüsseldateinamen an. Die benutzerdefinierten Workflowaktivitäts- (und Plug-In)-Assemblys müssen signiert sein. Sie müssen im Rahmen dieses Lernprogramms kein Kennwort festlegen. In diesem Beispiel haben wir eine neue Schlüsseldatei namens `SampleWorkflowActivity.snk` erstellt

    ![Assembly signieren](media/tutorial-create-workflow-activity-sign-assembly.png)

1. Erstellen Sie die Lösung im Debugmodus und überprüfen Sie, dass sich die `SampleWorkflowActivity.dll`-Assembly im Ordner `/bin/Debug` befindet.

## <a name="register-your-assembly"></a>Registrieren Ihrer Assembly

Benutzerdefinierte Workflowaktivitätsassemblys werden mithilfe des Plug-In-Registrierungs-Tools registriert. Dieses Tool stellt eine grafische Benutzeroberfläche bereit und unterstützt das Registrieren Assemblys, die Plug-Ins oder benutzerdefinierte Workflowaktivitäten enthalten. Informationen zum Abrufen des Plug-in Registrationstools finden Sie unter [Tools von NuGet herunterladen](../download-tools-nuget.md)

[!INCLUDE [cc-connect-plugin-registration-tool](../includes/cc-connect-plugin-registration-tool.md)]

### <a name="register-your-assembly"></a>Registrieren Ihrer Assembly

1. Wählen Sie **Registrieren** > **Neue Assembly registrieren** aus.

    ![Assemblybefehl registrieren](media/tutorial-create-workflow-activity-register-assembly.png)

1. Klicken Sie im Dialogfeld **Neue Assembly registrieren** auf die Schaltfläche mit den Auslassungspunkten (**...**) und navigieren Sie zu `SampleWorkflowActivity.dll` im Ordner `/bin/Debug`.

    ![Assembly-Dialog registrieren](media/tutorial-create-workflow-activity-register-assembly-dialog.png)

    > [!NOTE]
    > Hinweis: Bei CDS for Apps werden die gültigen Optionen für die Schritte 3 und 4 ausgewählt und ungültige Optionen werden deaktiviert.

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
    |WorkflowActivityGroupName|SampleWorkflowActivity (1.0.0.0)|Probe|Der Name des Untermenüs, das dem Hauptmenü im CDS for Apps Prozess hinzugefügt wurde.|

    > [!NOTE]
    > Wenn **Name** und **WorkflowActivityGroupName** auf null festgelegt sind, wird die benutzerdefinierte Aktivität nicht im Prozessdesigner angezeigt.

1. Klicken Sie auf **Speichern** (Symbol), um die Änderungen zu speichern.

    ![Speichern der Workflowaktivitätseigenschaften](media/tutorial-create-workflow-activity-set-workflow-activity-properties.png)

    > [!NOTE]
    > Diese Werte werden in der nicht verwalteten Lösung nicht angezeigt, wenn Sie Ihre Workflowaktivität testen. Wenn Sie allerdings eine verwaltete Lösung exportieren, die diese Workflowaktivität enthält, werden diese Werte im Prozessdesigner angezeigt.

## <a name="test-your-assembly"></a>Testen Sie Ihre Assembly

Sie können Ihre neue Workflowaktivität testen, indem Sie einen Prozess erstellen, der sie verwendet. Führen Sie diese Schritte aus, um den Workflowprozess zu erstellen, der im obigen Abschnitt [Ziel](#goal) beschrieben wird:

1. Öffnen Sie [PowerApps](http://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)
1. Wechseln Sie im Entwurfsmodus von **Canvas** zu **modellgesteuert**.
1. Wählen Sie **Lösungen** aus.
1. Öffnen Sie die **Common Data Service-Standardlösung**.
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
    > Den Umfang auf "Organisation" festzulegen erstellt einen bedarfsgesteuerten Workflow, der von allen Benutzern in der Organisation angewendet werden kann.

1. Fügen Sie den folgenden **Schritt** hinzu:

    ![Fügen Sie den Schritt "SampleWorkflowActivity.IncrementByTen" hinzu](media/tutorial-create-workflow-activity-use-sample-step.png)

    > [!NOTE]
    > Wie bereits erwähnt, werden die benutzerdefinierten Werte, die Sie in [Registrieren der Assembly](#register-your-assembly) festlegen, nicht im Designer angewendet, bis die Workflowaktivität als Teil einer verwalteten Lösung importiert wurde.

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

1. Öffnen Sie die nicht verwaltete Lösung, der Sie die Assembly mit dem Lösungsexplorer hinzufügen möchten.
1. Wählen Sie **Plug-In-Assemblys** in der Liste die Komponenten aus.
1. Klicken Sie in der Befehlsleiste auf **Vorhandene hinzufügen**.

    ![vorhandene hinzufügen auswählen](media/tutorial-create-workflow-activity-add-existing-solution-component.png)

1. Wählen Sie im Dialogfeld **Lösungskomponenten auswählen** die SampleWorkflowActivity aus, die Sie erstellt haben, und klicken Sie auf **OK**.

    ![SampleWorkflowActivity hinzufügen](media/tutorial-create-workflow-activity-add-solution-component.png)

### <a name="see-also"></a>Siehe auch

[Workflowerweiterungen](workflow-extensions.md)<br />
[Beispiel: Eine benutzerdefinierte Workflowaktivität erstellen](sample-create-custom-workflow-activity.md)<br />
[Beispiel: Aktualisieren des nächsten Geburtstags mithilfe einer benutzerdefinierten Workflowaktivität](sample-update-next-birthday-using-custom-workflow-activity.md)<br />
[Beispiel: Berechnen Sie mit einer benutzerdefinierten Workflowaktivität einen Kreditscore](sample-calculate-credit-score-custom-workflow-activity.md)