---
title: Arbeiten mit Test Studio zum Testen von Canvas-Apps | Microsoft-Dokumentation
description: In diesem Artikel wird die Verwendung von Test Studio anhand eines Testbeispiels einer Canvas-App erläutert.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/05/2020
ms.author: aheaney
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9e3192d6eda9730250e35b7ce6cd488b89037d43
ms.sourcegitcommit: 223c3d19ec4fbe43fcc7a16b76423c00f8602ecd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81489040"
ms.PowerAppsDecimalTransform: true
---
# <a name="working-with-test-studio-experimental"></a>Arbeiten mit Test Studio (experimentell)

In diesem Schnellstart erstellen Sie Tests für eine Canvas-App namens Kudos. Sie können sich außerdem Testkonzepte näher ansehen und sie anwenden, um Tests für Ihre eigene Canvas-App zu schreiben. Die Beispiel-App Kudos ist Teil mehrerer Apps für die Mitarbeiterbindung, die im Rahmen des [Employee Experience Starter Kit](https://powerapps.microsoft.com/en-us/blog/powerapps-employee-experience-starter-kit) zum Download bereit stehen.

> [!NOTE]
> Dieses Feature ist noch experimentell, und Sie sollten es noch nicht verwenden, um Tests für Produktions-Apps zu schreiben. Weitere Informationen finden Sie unter [Experimentelle Features und Previewfunktionen](working-with-experimental-preview.md).

## <a name="open-test-studio"></a>Öffnen von Test Studio

Dieses Feature müssen Sie nicht wie bei anderen experimentellen Features in Ihrer App aktivieren. Test Studio steht standardmäßig für alle Canvas-Apps zur Verfügung.

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.

2. Erstellen Sie eine [neue App](get-started-test-drive.md), oder [bearbeiten Sie eine vorhanden App](edit-app.md).

3. Speichern Sie Ihre App in Power Apps, um Test Studio zu öffnen. 
    
    > [!NOTE]
    > Apps müssen gespeichert werden, bevor Sie Tests dafür schreiben können.

4. Klicken Sie im linken Navigationsbereich auf die Option **Erweiterte Tools**.

5. Klicken Sie auf **Test öffnen**, um Test Studio für diese Anwendung zu öffnen. Dadurch wird Test Studio in einer neuen Browserregisterkarte geöffnet.

    ![Öffnen von Test Studio](./media/working-with-test-studio/open-tests.png)

> [!NOTE]
> Tests werden im App-Paket veröffentlicht und gespeichert. Beim Exportieren und Importieren eines Canvas-App-Pakets in eine andere Umgebung sind auch alle Test Definitionen enthalten, wie z. b. Test Auflistungen und erstellte Testfälle. 

## <a name="create-a-test-suite"></a>Erstellen einer Testsammlung

Standardmäßig werden für Sie eine Testsammlung und ein Testfall in Test Studio erstellt. Einzelne Testfälle können mithilfe von Testsammlungen sortiert werden. Eine App kann eine oder auch mehrere Testsammlungen enthalten. Entweder verwenden Sie die Standardtestsammlung und den Standardtestfall, um sofort mit dem Schreiben von Tests zu beginnen, oder Sie erstellen eine neue Testsammlung.

1. Klicken Sie auf **Neue Sammlung**.
2. Füllen Sie die Felder für **Name und Beschreibung der Testsammlung** aus, indem Sie auf die entsprechenden Felder auf dem Hauptraster klicken.

    ![Neue Testsammlung](./media/working-with-test-studio/new-test-suite.png)

## <a name="create-a-test-case"></a>Testfall erstellen

Je nachdem, ob Sie Ihre Tests einzeln anordnen oder miteinander gruppieren möchten, können Sie auch mehrere Testfälle in einer Testsammlung erstellen. Mit jedem Testfall kann ein bestimmtes Feature oder ein bestimmter Teilbereich von Funktionen Ihrer App getestet werden.

1. Wählen Sie eine Testsammlung aus.
2. Klicken Sie im oberen Menü auf **Neuer Fall**, um einen neuen Testfall zu erstellen.
3. Füllen Sie die Felder für **Name und Beschreibung des Testfalls** aus, indem Sie auf die entsprechenden Felder auf dem Hauptraster klicken.

 ![Neuer Testfall](./media/working-with-test-studio/new-test-case.png)

## <a name="record-a-test-case"></a>Aufzeichnen eines Testfalls

Ein Testfall besteht aus Testschritten, die Aktionen enthalten. Diese Aktionen werden mithilfe von Power Apps-Ausdrücken geschrieben, die eine Aufgabe ausführen. Sie können das Aufzeichnungstool verwenden, um die Testschritte automatisch generieren zu lassen, während Sie mit der App interagieren. Nach der Aufzeichnung können Sie den Testfall aktualisieren, neue Schritte hinzufügen, Schritte löschen und Testassertionen schreiben, um das Ergebnis Ihres Tests zu überprüfen.

> [!NOTE]
> Nur veröffentlichte Apps können im Aufzeichnungsmodus wiedergeben werden. Veröffentlichen Sie alle vor Kurzem an der App vorgenommenen Änderungen, bevor Sie mit der Aufzeichnung eines Testfalls beginnen. Wenn Sie eine Aufzeichnung beginnen, ohne aktuelle Änderungen veröffentlicht zu haben, wird im Aufzeichnungsmodus die zuletzt veröffentlichte Version der App wiedergeben.

1. Klicken Sie in der oberen Menüleiste auf **Aufzeichnen**. Dadurch wird die veröffentlichte App im Aufzeichnungsmodus in einer neuen Browserregisterkarte geöffnet.

    > [!IMPORTANT]
    > Aufzeichnungen innerhalb eines bestehenden Testfalls überschreiben alle bereits vorhandenen Testschritte.

    ![Aufzeichnen von Tests](./media/working-with-test-studio/record-tests.png)

2. Interagieren Sie mit Ihrer App. Ihre Aktionen werden dann im linken Bereich **aufgezeichnet**.

3. Klicken Sie auf **Fertig**, wenn Sie die Interaktionen abgeschlossen haben. Optional können Sie auch auf **Abbrechen** klicken, um zu Test Studio zurückzukehren, ohne dass Ihre Interaktionen aufgezeichnet werden. 

    ![Speichern von Aufzeichnungen](./media/working-with-test-studio/save-recording.png)

4. Sehen Sie sich die Testschritte und die Ausdrücke an, die in Test Studio automatisch für Sie generiert wurden.
5. Bearbeiten Sie gegebenenfalls den Beschreibungstext für Schritte im Hauptraster. Sie können auch die Testschrittaktionen aktualisieren, indem Sie auf die Formel im Hauptraster klicken.

    ![Aktualisieren eines Testfalls](./media/working-with-test-studio/update-test-case.png)

### <a name="add-test-steps-and-test-assertions"></a>Hinzufügen von Testschritten und Testassertionen

Jeder Testfall sollte zum zu erwarteten Ergebnis führen. Im Kudos-Beispiel ist eines der erwarteten Ergebnisse für das Senden eines Lobs das Erstellen eines neuen Datensatzes in der Common Data Service-Datenbank. Sie aktualisieren nun den Testfall und fügen zusätzliche Testschritte hinzu, um zu überprüfen, ob erfolgreich ein Datensatz erstellt wurde.

Sie müssen die folgenden Schritte ausführen, um zu überprüfen, ob ein Datensatz erfolgreich erstellt wurde:

- Initialisieren Sie zu Beginn des Testfalls eine Variable für die Anzahl der Datensätze für das Senden eines Lobs in der Datenbank.
- Initialisieren Sie am Ende des Testfalls eine Variable für die Anzahl der Datensätze für das Senden eines Lobs in der Datenbank.
- Schreiben Sie einen Assertionsausdruck für den Test, um zu überprüfen, ob die Anzahl um 1 inkrementiert wurde. Wenn die Anzahl nicht um 1 inkrementiert wurde, schlagen sowohl die Testassertion als auch Ihr Testfall fehl.

So fügen Sie in der Kudos-App Testschritte und Testassertionen hinzu:

1. Wählen Sie Schritt 1 oder einen Schritt aus, über dem Sie einen neuen Schritt einfügen möchten. 

2. Klicken Sie oben im Menü auf **Insert a step above** (Über diesem Schritt einen Schritt einfügen) oder auf die Option in der ausgewählten Zeile. Dadurch wird ein leerer Schritt erstellt.

    ![Schritt einfügen](./media/working-with-test-studio/insert-step-above.png)

    > [!NOTE]
    > Wenn Sie auf die Option **Insert a step above** (Über diesem Schritt einen Schritt einfügen) klicken, wird oberhalb des aktuellen Schritts ein neuer, leerer Schritt eingefügt. Alternativ können Sie auch die Aktionen **Assert**, **SetProperty**, **Select** oder **Trace** verwenden. Dadurch wird jeweils ein Schritt mit entsprechender Aktionsformel hinzugefügt, die Sie bearbeiten können.

3. Aktualisieren Sie die Beschreibung des Schritts. Beispiel: "count Kudo in Database".

4. Geben Sie in die Aktionseingabe einen Ausdruck oder eine Formel ein, um die Datensätze in der Datenbank vor der Ausführung des Tests zählen zu lassen.

    Sie können jeden beliebigen unterstützten Ausdruck verwenden. Sie können auch beliebige Datenquellen, Sammlungen, Variablen oder Flowausführungen abfragen, die in Ihrer App enthalten sind, und neue globale Variablen oder Sammlungen erstellen, die in Ihren Tests verwendet werden.

    ```Set(kudosBeforeTest; CountRows(Filter(Kudos; Receiver.Email = "someone@example.com")))```

5. Wählen Sie Schritt 2 oder einen Schritt aus, über dem Sie einen neuen Schritt einfügen möchten.

6. Klicken Sie oben im Menü auf **Insert a step above** (Über diesem Schritt einen Schritt einfügen) oder auf die Option in der ausgewählten Zeile. Dadurch wird ein leerer Schritt erstellt.

7. Geben Sie in die Aktionseingabe einen [Trace](./functions/function-trace.md)-Ausdruck oder eine entsprechende Formel ein, und schreiben Sie den Wert *kudosBeforeTest* in den Datensatz der Testergebnisse.

    ```Trace("kudosBeforeTest : " & kudosBeforeTest);;```

    ![Lobanzahl vor dem Test](./media/working-with-test-studio/kudos-before-test.png)

8. Scrollen Sie im Testfall nach unten, und fügen Sie dort einen neuen Schritt ein, um die Datensätze in der Datenbank nach Abschluss des Tests zählen zu lassen.

    ```Set(kudosAfterTest; CountRows(Filter(Kudos; Receiver.Email = "someone@example.com")))```

9. Fügen Sie einen abschließenden Schritt hinzu, um zu überprüfen, ob die Anzahl der Datensätze in der Datenbank um 1 inkrementiert wurde, und geben Sie die folgende Assertionsaktion ein, damit dies überprüft wird:

    ```Assert(kudosAfterTest = kudosBeforeTest + 1; "Kudos count incorrect. Expected : " & kudosBeforeTest + 1  & " Actual :" & kudosAfterTest)```

    ![Lobanzahl nach der Testassertion](./media/working-with-test-studio/kudos-after-test-assert.png)

10. Speichern Sie den Testfall in Test Studio im Menü oben rechts. 

## <a name="play-back-your-test"></a>Wiedergeben Ihres Tests

Sie können Ihren aufgezeichneten Test wiedergeben, um die App-Funktionalität zu überprüfen. Entweder geben Sie alle Tests einer einzelnen Testsammlung oder einen einzelnen Testfall wieder. 

Bevor Sie eine Aufzeichnung mit aktuellen Änderungen wiedergeben können, müssen Sie die App veröffentlichen:

![Wiedergeben ohne Veröffentlichung](./media/working-with-test-studio/publish-test-studio-changes.png)

> [!IMPORTANT]
> Wenn Sie die Veröffentlichung überspringen, werden in der Wiedergabe Ihrer Aufzeichnung aktuelle Teständerungen nicht berücksichtigt. In diesem Fall wird der zuletzt veröffentlichte Testfall oder die zuletzt veröffentlichte Testsammlung für die App wiedergegeben.

1. Klicken Sie auf **Veröffentlichen**. Dadurch wird Ihr Test automatisch gespeichert und veröffentlicht.

    ![Veröffentlichen von Änderungen](./media/working-with-test-studio/publish-button.png)

2. Wählen Sie entweder eine Testsammlung oder einen einzelnen Testfall aus.

3. Klicken Sie auf **Wiedergabe**. Die veröffentlichte App wird im **Wiedergabemodus** geöffnet, und Sie können sich ansehen, wie Ihre Testschritte automatisch wiedergegeben werden. Wenn ein Testschritt erfolgreich ausgeführt wurde, wird dies durch ein grünes Häkchen angezeigt. Wenn ein Schritt fehlschlägt, erhält der Schritt eine rote Fehlerhervorhebung, und die entsprechende Fehlermeldung wird angezeigt.

    ![Wiedergabemodus](./media/working-with-test-studio/play-mode.png)

4. Klicken Sie auf „Fertig“, um zu Test Studio zurückzukehren.

### <a name="failed-assertion"></a>Assertionsfehler

In diesem Abschnitt ändern Sie die Testassertion, um zu sehen, was im Fall eines fehlgeschlagenen Tests geschieht:

1. Bearbeiten Sie den Assertionsschritt, indem Sie auf das Ausdrucksfeld klicken.

2. Ändern Sie in der Testaktion ```+ 1``` in ```+ 2```. Das bedeutet, dass der Test erwartet, dass zwei Datensätze erstellt werden. Das ist jedoch falsch. Wenn der Test erfolgreich ist, sollte in der Datenbank lediglich ein Datensatz erstellt werden.

    ```Assert(kudosAfterTest = kudosBeforeTest + 2; "Kudos count incorrect. Expected : " & kudosBeforeTest + 2  & " Actual :" & kudosAfterTest)```

    ![Geänderte Assert-Anweisung zum Überprüfen der Anzahlinkrementierung](./media/working-with-test-studio/assert-count-update.png)

3. Klicken Sie auf **Veröffentlichen**.

4. Wählen Sie **Abspielen** aus.

5. Sehen Sie sich an, wie der Test wiedergeben wird. Der letzte Schritt schlägt nun fehl, und es wird ein Fehler sowie die Nachricht angezeigt, die Sie im Assertionsschritt angegeben haben.  

    ![Wiedergabefehler](./media/working-with-test-studio/playback-error.png)

### <a name="playing-tests-in-a-browser"></a>Wiedergeben von Tests in einem Browser

Sie können einen Link kopieren, um einen Test in einem separaten Browser außerhalb von Test Studio wiederzugeben. So können Sie Ihre Tests in kontinuierliche Build- und Releasepipelines wie **Azure DevOps** integrieren.

Der Wiedergabelink für einen ausgewählten Test wird beibehalten. Er ändert sich nicht pro Testsammlung oder Testfall. Sie können Ihre Tests aktualisieren, ohne Build- und Releaseprozesse ändern zu müssen.

So geben Sie Tests in einem Browser wieder:

1. Wählen Sie im rechten Bereich eine Testsammlung oder einen Testfall aus.

2. Klicken Sie auf **Wiedergabelink kopieren**.

    ![Wiedergabelink kopieren](./media/working-with-test-studio/copy-play-link.png)

3. Sie werden aufgefordert, Ihre Tests zu veröffentlichen, wenn es noch nicht veröffentlichte Änderungen gibt.

    ![Veröffentlichen vor dem Kopieren des Links](./media/working-with-test-studio/publish-before-copy-link.png)

4. Sie können auswählen, dass der Veröffentlichungsprozess übersprungen und der Wiedergabelink kopiert wird. Wenn Sie das Veröffentlichen überspringen, werden aktuelle Änderungen am Test jedoch nicht wiedergegeben.

    ![Wiedergabelink kopieren](./media/working-with-test-studio/copy-play-link-ack.png)

5. Öffnen Sie einen Browser, und fügen Sie die URL in die Adressleiste ein, damit der Test wiedergegeben wird.

6. Sehen Sie sich an, wie der Test wiedergeben wird.

## <a name="processing-test-results"></a>Verarbeiten von Testergebnissen

Der Testbereich, der bei der Wiedergabe von Tests in Test Studio angezeigt wird, wird nicht angezeigt, wenn Sie einen Browser verwenden. Deshalb können Sie nicht bestimmen, welcher konkrete Testschritt gerade ausgeführt wird oder ob ein Test erfolgreich war bzw. fehlschlägt.

Es gibt im Testobjekt jedoch zwei Eigenschaften namens **OnTestCaseComplete** und **OnTestSuiteComplete** mithilfe derer Sie die Testergebnisse außerhalb von Test Studio bestimmen können. Mit diesen Objekten können Sie die Ergebnisse Ihrer Tests verarbeiten. Wenn Sie Tests in eine kontinuierliche Build- und Releasepipeline wie **Azure DevOps** integrieren, können Sie mit diesen Eigenschaften bestimmen, ob Sie eine App-Bereitstellung fortsetzen sollten.

Der für diese Eigenschaften eingegebene Ausdruck wird ausgelöst, wenn ein jeweiliger Testfall oder eine Testsammlung abgeschlossen ist. Sie können diese Eigenschaften auch anpassen, sodass die Ergebnisse Ihrer Tests verarbeitet und z. B. an die folgenden Datenquellen oder Dienste gesendet werden:

- SQL Server sichern.
- Common Data Service
- Power Automate
- E-Mail über Office 365

Diese Einstellungen gelten für alle Testsammlungen oder Testfälle in Ihrer App. Nach Abschluss einer Testsammlung oder aller Testfälle können Sie sich die Testergebnisse und gegebenenfalls in den Tests aufgetretene Ablaufverfolgungsmeldungen in den Datensätzen **TestCaseResult** und **TestSuiteResult** ansehen.

Im Datensatz **TestCaseResult** sind die folgenden Eigenschaften enthalten:

- *TestCaseName:* Name des Testfalls
- *TestCaseId:* ID des Testfalls
- *TestSuiteName:* Name der Testsammlung, zu der der Fall gehört
- *TestSuiteId:* ID der Testsammlung, zu der der Fall gehört
- *StartTime:* Startzeit der Ausführung des Tests
- *EndTime:* Endzeit der Ausführung des Tests
- *Traces:* Ergebnisse aller Testassertionen und gegebenenfalls aufgetretene Meldungen der Nachverfolgungsfunktion
- *Success:* Gibt an, ob der Testfall erfolgreich abgeschlossen wurde
- *TestFailureMessage:* Fehlermeldung, wenn der Testfall fehlschlägt

Im Datensatz **TestSuiteResult** sind die folgenden Eigenschaften enthalten: 

- *TestSuiteName:* Name der Testsammlung
- *TestSuiteId:* ID der Testsammlung
- *StartTime:* Startzeit der Ausführung der Testsammlung
- *EndTime:* Endzeit der Ausführung der Testsammlung
- *TestsPassed:* Anzahl der Testfälle, die innerhalb einer Sammlung erfolgreich abgeschlossen wurden
- *TestsFailed:* Anzahl der Testfälle, die innerhalb einer Sammlung fehlgeschlagen sind

In diesem Schnellstart erstellen Sie zwei benutzerdefinierte Entitäten in der Common Data Service-Datenbank, um die Testergebnisse zu speichern, indem die Eigenschaften **OnTestCaseComplete** und **OnTestSuiteComplete** angepasst werden:

1. Klicken Sie im linken Bereich auf **Testen** oder in der Sammlungskopfzeile auf **Anzeigen**.

    ![Testen oder Anzeigen der festgelegten Eigenschaft](./media/working-with-test-studio/test-or-view-to-set-property.png)

2. Klicken Sie auf die Aktion **OnTestCaseComplete**.

3. Geben Sie einen Ausdruck ein, um die Ergebnisse Ihres Tests zu verarbeiten. Im folgenden Beispiel werden die Ergebnisse aller Testfälle in der benutzerdefinierten AppTestResults-Entität in Common Data Service gespeichert. Die Testergebnisse können optional auch in SQL, SharePoint oder einer beliebigen anderen Datenquelle gespeichert werden. Möglicherweise müssen Sie das Feld für die Ablaufverfolgung in Ihrer Datenquelle entsprechend festlegen oder vergrößern.

    > [!NOTE]
    > Für die folgenden Beispiele ist eine [Common Data Service-Verbindung](https://docs.microsoft.com/connectors/commondataservice/) erforderlich. Mit Common Data Service können Sie eine [einfache App](data-platform-create-app.md) oder [eine App von Grund auf erstellen](data-platform-create-app-scratch.md). Sehen Sie sich außerdem die Referenz zur [Patchfunktion](./functions/function-patch.md) an, um weitere Informationen für das Bearbeiten der Datensätze einer Datenquelle zu erhalten, die in den folgenden Beispielen verwendet werden.

    ```
    //Save to Common Data Service
    Patch(AppTestResults
    , Defaults(AppTestResults)
    , {
             TestPass: TestCaseResult.TestCaseName & ":" & Text(Now())
             ,TestSuiteId: TestCaseResult.TestSuiteId
             ,TestSuiteName: TestCaseResult.TestSuiteName
             ,TestCaseId: TestCaseResult.TestCaseId
             ,TestCaseName: TestCaseResult.TestCaseName
             ,StartTime: TestCaseResult.StartTime
             ,EndTime: TestCaseResult.EndTime
             ,TestSuccess: TestCaseResult.Success
             ,TestTraces: JSON(TestCaseResult.Traces)
             ,TestFailureMessage: TestCaseResult.TestFailureMessage
    }
    );
    ```
    ![Beispielbild für „OnTestCaseComplete“](./media/working-with-test-studio/ontestcasecomplete-example.png)

4. Klicken Sie auf die Aktion **OnTestSuiteComplete**.

5. Geben Sie einen Ausdruck ein, um die Ergebnisse Ihres Tests zu verarbeiten. Im folgenden Beispiel speichern Sie alle Ergebnisse der Testsammlung in der benutzerdefinierten AppTestSuiteResults-Entität in Common Data Service. 

    ```
    //Save to Common Data Service
    Patch(AppTestSuiteResults
        , Defaults(AppTestSuiteResults)
        , {
             TestSuiteId: TestSuiteResult.TestSuiteId
             ,TestSuiteName: TestSuiteResult.TestSuiteName
             ,StartTime: TestSuiteResult.StartTime
             ,EndTime: TestSuiteResult.EndTime
             ,TestPassCount: TestSuiteResult.TestsPassed
             ,TestFailCount: TestSuiteResult.TestsFailed
        }
    );
    ```

    ![Beispielbild für „OnTestSuiteComplete“](./media/working-with-test-studio/ontestsuitecomplete-example.png)

Weitere Beispiele für Ausdrücke, die Sie in diesen Eigenschaften verwenden könnten, sind die Folgenden:

- Senden der Ergebnisse an einen Flow in Power Automate:

    ```MyTestResultsFlow.Run(JSON(TestCaseResult))```

- Senden der Ergebnisse per E-Mail:

    ```Office365.SendMailV2("someone@example.com"; "Test case results"; JSON(TestCaseResult; JSONFormat.IndentFour))```

- Erhalten einer App-Benachrichtigung mit dem Testergebnis:

  Sie könnten beispielsweise bei der Wiedergabe des Tests in einem Browser außerhalb von Test Studio eine Benachrichtigung erhalten, sobald der Test abgeschlossen ist.

    ```
    Notify(TestCaseResult.TestCaseName & " : "
            & If( TestCaseResult.Success
                , " Passed"
                , TestCaseResult.TestFailureMessage)
            ,If(  TestCaseResult.Success
                , NotificationType.Success
                , NotificationType.Error)
    )
    ```

## <a name="test-functions"></a>Testfunktionen

Zusätzlich zu den in Power Apps verfügbaren [Funktionen](formula-reference.md) werden die folgenden Funktionen häufig verwendet, um Tests zu erstellen.

- [Auswählen](./functions/function-select.md)
- [SetProperty](./functions/function-setproperty.md)
- [Machung](./functions/function-assert.md)
- [Ablauf Verfolgungs](./functions/function-trace.md)

## <a name="next-steps"></a>Nächste Schritte

- [Automatisieren von Tests mit dem klassischen Azure devops-Pipeline-Editor](test-studio-classic-pipeline-editor.md)