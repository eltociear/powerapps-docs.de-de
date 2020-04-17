---
title: Automatisieren von Tests mit der Azure-Pipeline mit klassischem Editor | Microsoft-Dokumentation
description: Hier wird beschrieben, wie Test Auflistungen und Fälle mit dem klassischen Editor aus der Azure-Pipeline automatisiert werden.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/16/2020
ms.author: aheaney
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ecfeeb1f62032008d7ada618afb56e6da8589f40
ms.sourcegitcommit: 223c3d19ec4fbe43fcc7a16b76423c00f8602ecd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81490888"
---
# <a name="automate-tests-with-azure-pipeline-using-classic-editor"></a>Automatisieren von Tests mit der Azure-Pipeline mit klassischem Editor

In diesem Artikel erfahren Sie, wie Sie Ihre Canvas-App-Tests, die in Test Studio erstellt wurden, mit dem [Azure Pipelines klassischen Editor](https://docs.microsoft.com/azure/devops/pipelines/get-started/pipelines-get-started?view=azure-devops#define-pipelines-using-the-classic-interface) in [Azure DevOps Services](https://docs.microsoft.com/azure/devops/user-guide/what-is-azure-devops?view=azure-devops)einrichten und ausführen.

Sie können ein öffentliches Projekt auf GitHub- [Microsoft/powerappstestautomation](https://github.com/microsoft/PowerAppsTestAutomation) für Folgendes verwenden:

- Automatisieren Sie den Betrieb der Anmeldung bei Ihrer Anwendung.
- Öffnen Sie einen Browser auf dem Build-Agent, und führen Sie eine Reihe von Testfällen und Suites aus.
- Anzeigen des Status der Testausführung in der Azure devops-Pipeline.

## <a name="prerequisites"></a>Erforderliche Komponenten

Bevor Sie beginnen, müssen Sie die folgenden Schritte ausführen:

- [Verzweigen](#step-1---fork-the-powerappstestautomation-project) Sie das [Microsoft/powerappstestautomation-](https://github.com/microsoft/PowerAppsTestAutomation) Projekt auf GitHub.

    > [!NOTE]
    > Öffentliche Forks können nicht als privat fest gegeben werden. Wenn Sie ein privates Repository erstellen möchten, [Duplizieren Sie das Repository](https://help.github.com/github/creating-cloning-and-archiving-repositories/duplicating-a-repository).

- Erstellen Sie eine neue [*Test-URLs. JSON-Datei*](#step-2---create-test-url-json-file) im Repository mit den App-Test-URLs, die Sie aus der Pipeline ausführen möchten.

### <a name="step-1---fork-the-powerappstestautomation-project"></a>Schritt 1: Verzweigen des Projekts "powerappstestautomation"

Eine [Verzweigung](https://help.github.com/github/getting-started-with-github/fork-a-repo) ist eine Kopie eines Repository. Durch das forken eines Repository können Sie Änderungen vornehmen, ohne das ursprüngliche Projekt zu beeinflussen.

1. Melden Sie sich bei [GitHub](https://github.com/)an.

1. Wechseln Sie zum [Microsoft/powerappstestautomation-](https://github.com/microsoft/PowerAppsTestAutomation) Repository. Sie können stattdessen auch nach **Microsoft/powerappstestautomation** suchen und dann das Repository auswählen:

    ![GitHub durchsuchen](media/test-studio-classic-pipeline-editor/search-github.png)

1. **Verzweigung**auswählen:

    ![Verzweigung](media/test-studio-classic-pipeline-editor/fork.png)

1. Wählen Sie die gewünschte Verzweigung aus:

    ![Fork-Konto](media/test-studio-classic-pipeline-editor/fork-account.png)

Ihr verzweigtes Repository ist nun verfügbar.

### <a name="step-2---create-test-url-json-file"></a>Schritt 2: Erstellen der Datei "Test-URL. JSON"

Die Datei "Test URL. JSON" enthält die Test Sammlung und die Testfall-URLs zum Überprüfen Ihrer APP. Die APP-Test Auflistung und die Testfall-URLs können abgerufen werden, indem Sie in Teststudio den [Link "Play Play](working-with-test-studio.md#playing-tests-in-a-browser) " auswählen.

Sie finden eine Beispieldatei ```Samples/TestAutomationURLs.json``` in dem Repository, das Sie zuvor erstellt haben.

1. Erstellen Sie eine neue ```TestURLs.json``` Datei in Ihrem Repository, oder verwenden Sie einen anderen Dateinamen. <br> Der Dateiname und der Speicherort werden später im Dokument in den Pipeline Variablen zugeordnet.

1. Kopieren Sie das Format aus der ```Samples/TestAutomationURLs.json``` Datei.

1. Aktualisieren Sie den Test-URLs-Abschnitt mit den Tests, die Sie in Ihrer APP überprüfen möchten.

1. Commit für die Änderungen in Ihrem Repository ausführen:

    ![JSON-Update](media/test-studio-classic-pipeline-editor/json-update.png)

## <a name="create-a-pipeline"></a>Erstellen einer Pipeline

1. Melden Sie sich bei ihrer Azure devops-Instanz an.

1. Wählen Sie ein vorhandenes Projekt aus, oder erstellen Sie ein neues Projekt.

1. Wählen Sie im Menü auf der linken Seite **Pipelines** aus.

1. Wählen Sie **Pipeline erstellen**aus:

    ![Pipeline erstellen](media/test-studio-classic-pipeline-editor/create-pipeline.png)

1. Wählen Sie **klassischen Editor verwenden**aus:

    ![Klassischer Editor](media/test-studio-classic-pipeline-editor/use-classic-editor.png)

1. Wählen Sie GitHub als Quelle aus.

1. Autorisieren Sie ggf. Ihre GitHub-Verbindung mithilfe von OAuth, oder verwenden Sie ein persönliches Zugriffs Token:

    ![Pipeline-GitHub](media/test-studio-classic-pipeline-editor/pipeline-github.png)

1. Bearbeiten Sie bei Bedarf den Namen der Verbindung.

1. Wählen Sie auf der rechten Seite der **Repository** -Eingabe die Option **...** (Auslassungs Zeichen) aus.

1. Geben Sie den Namen des Projekts auf GitHub ein, und **Wählen** Sie es aus:

    ![Repository auswählen](media/test-studio-classic-pipeline-editor/select-repo.png)

1. Klicken Sie auf **Weiter**.

1. Wählen Sie auf dem Bildschirm Vorlage auswählen die Option **leerer Auftrag**aus:

    ![Leerer Auftrag](media/test-studio-classic-pipeline-editor/empty-job.png)

1. **Speichern** Sie Ihre Pipeline.

## <a name="add-tasks-to-the-pipeline"></a>Hinzufügen von Aufgaben zur Pipeline

Nun fügen Sie neue Auftrags Aufgaben hinzu und konfigurieren die Tasks zum Ausführen der Tests aus der Pipeline in dieser Reihenfolge:

1. [Konfigurieren Sie die Bildschirmauflösung mithilfe von PowerShell.](#step-1---configure-screen-resolution-using-powershell)

1. [Stellen Sie die nuget-Pakete für die powerappstestautomation-Lösung wieder her.](#step-2---restore-nuget-packages)

1. [Erstellen Sie die powerappstestautomation-Lösung.](#step-3---build-the-powerappstestautomation-solution)

1. [Fügen Sie Visual Studio-Tests für Google Chrome hinzu.](#step-4---add-visual-studio-tests-for-google-chrome)

1. [Fügen Sie Visual Studio-Tests für Mozilla Firefox hinzu.](#step-5---add-visual-studio-tests-for-mozilla-firefox)

### <a name="step-1---configure-screen-resolution-using-powershell"></a>Schritt 1: Konfigurieren der Bildschirmauflösung mithilfe von PowerShell

1. Wählen Sie **+** neben dem *Agentauftrag 1*aus.

1. Suchen Sie nach **PowerShell**.

1. Wählen Sie **Hinzufügen** aus, um dem Auftrag eine PowerShell-Aufgabe hinzuzufügen:

    ![PowerShell](media/test-studio-classic-pipeline-editor/powershell.png)

1. Wählen Sie den Task aus. <br>
    Sie können den anzeigen Amen auch aktualisieren, um *die Bildschirmauflösung des Agents auf 1920 x 1080 oder ähnlich festzulegen* .

1. Wählen Sie **Inline** als Skripttyp aus, und geben Sie im Skript Fenster den folgenden Code ein:

    ```powershell
    # Set agent screen resolution to 1920x1080 to avoid sizing issues with Portal  
    Set-DisplayResolution -Width 1920 -Height 1080 -Force
    # Wait 10 seconds  
    Start-Sleep -s 10
    # Verify Screen Resolution is set to 1920x1080  
    Get-DisplayResolution
    ```

    ![Skript](media/test-studio-classic-pipeline-editor/script.png)

### <a name="step-2---restore-nuget-packages"></a>Schritt 2: Wiederherstellen von nuget-Paketen

1. Wählen Sie **+** neben dem Agentauftrag 1 aus.

1. Suchen Sie nach **nuget**.

1. Wählen Sie hinzufügen aus, um dem Auftrag eine nuget-Aufgabe hinzuzufügen.

1. Wählen Sie den Task aus.
    <br> Sie können den anzeigen Amen auch aktualisieren, um **nuget-Pakete oder ähnliches wiederherzustellen** .

1. Wählen Sie **...** (Ellipsen) im Konfigurationsfeld **Pfad zu Projekt Mappe, Packages. config oder Project. JSON** .

1. Wählen Sie die Projektmappendatei "powerappstestautomation. sln" aus.

1. Wählen Sie **OK**aus:

    ![Nuget-Paket](media/test-studio-classic-pipeline-editor/nuget.png)

### <a name="step-3---build-the-powerappstestautomation-solution"></a>Schritt 3: Erstellen der powerappstestautomation-Lösung

1. Wählen Sie **+** neben dem Agentauftrag 1 aus.

1. Suchen Sie nach **Visual Studio-Build**.

1. Wählen Sie **Hinzufügen** aus, um dem Auftrag eine Visual Studio-Buildaufgabe hinzuzufügen.

1. Wählen Sie den Task aus.
    <br> Sie können den anzeigen Amen auch so aktualisieren, dass **powerapps-Test Automatisierungslösungen** oder ähnliches erstellt werden.

1. Wählen Sie **...** (Ellipsen) im projektmappenkonfigurations **-** Feld.

1. Wählen Sie die Projektmappendatei "powerappstestautomation. sln" aus.

1. Wählen Sie **OK**.

### <a name="step-4---add-visual-studio-tests-for-google-chrome"></a>Schritt 4: Hinzufügen von Visual Studio-Tests für Google Chrome

1. Wählen Sie **+** neben dem Agentauftrag 1 aus.

1. Suchen Sie nach **Visual Studio-Test**.

1. Wählen Sie hinzufügen aus, um dem Auftrag eine Visual Studio-Test Aufgabe hinzuzufügen.

1. Wählen Sie den Task aus.
    <br> Sie können den anzeigen Amen auch aktualisieren, um *powerapps-Test Automatisierungs Tests über \$(browsertypechrome)* oder ähnliches auszuführen.

1. Entfernen Sie die Standardeinträge im Textfeld Test Dateien, und fügen Sie Folgendes hinzu:

    ```**\Microsoft.PowerApps.TestAutomation.Tests\bin\\Debug\Microsoft.PowerApps.TestAutomation.Tests.dll```

1. Geben Sie im **Feld Test Filter Kriterien**```TestCategory=PowerAppsTestAutomation``` ein.

1. Wählen Sie **Test Mischung enthält UI-Tests**.

    ![Chrome](media/test-studio-classic-pipeline-editor/chrome.png)

1. Wählen Sie **...** (Ellipsen) im **Einstellungsdatei** Feld.

1. Erweitern Sie **Microsoft. powerapps. Testautomation. Tests**, wählen Sie die Datei **patestautomation. RunSettings** aus, und wählen Sie dann **OK**aus:

    ![Test Lauf Einstellungen](media/test-studio-classic-pipeline-editor/runsettings.png)

1. Kopieren Sie Folgendes in das Feld **Test Lauf Parameter überschreiben** .

    ```
    -OnlineUsername $(OnlineUsername) -OnlinePassword $(OnlinePassword) -BrowserType $(BrowserTypeChrome) -OnlineUrl $(OnlineUrl) -UsePrivateMode $(UsePrivateMode) -TestAutomationURLFilePath $(TestAutomationURLFilePath) -DriversPath $(ChromeWebDriver)
    ```

    > [!NOTE]
    > An dieser Stelle werden die Variablen in der Pipeline konfiguriert, die oben in Form von \$(VariableName) dargestellt werden.

1. Geben Sie **powerapps Test Automation Tests via \$(browsertypechrome)** oder ähnlich im Feld Test Lauf Titel ein.

    ![Testlauf](media/test-studio-classic-pipeline-editor/test-run.png)

### <a name="step-5---add-visual-studio-tests-for-mozilla-firefox"></a>Schritt 5: Hinzufügen von Visual Studio-Tests für Mozilla Firefox

1. Klicken Sie mit der rechten Maustaste auf den Task **Visual Studio-Tests für Chrome hinzufügen** , und wählen Sie **Aufgabe (n) Klonen**.

1. Wählen Sie den Task aus, und aktualisieren Sie die folgenden Bereiche.

    1. **Title**: powerapps-Test Automatisierungs Tests über \$(browsertypefirefox)-Kopiervorgang ausführen

    1.  **Test Lauf Parameter überschreiben**

        ```
        -OnlineUsername $(OnlineUsername) -OnlinePassword $(OnlinePassword) -BrowserType $(BrowserTypeFirefox) -OnlineUrl $(OnlineUrl) -UsePrivateMode $(UsePrivateMode) -TestAutomationURLFilePath $(TestAutomationURLFilePath) -DriversPath $(GeckoWebDriver)
        ```

    1.  **Test Lauf Titel**: Ausführen von Test Automatisierungs Tests für powerapps über \$(browsertypefirefox)

## <a name="configure-pipeline-variables"></a>Konfigurieren von Pipeline Variablen

Nun konfigurieren Sie die Pipeline Variablen, die in den [zuvor](#add-tasks-to-the-pipeline)hinzugefügten Aufgaben definiert sind.

1. Wählen Sie die Registerkarte **Variablen** aus.

2. Wählen Sie **Hinzufügen** , und wiederholen Sie diesen Schritt, um die folgenden Variablen zu konfigurieren

| Variablenname             | Variablen Wert                                                                                                                 |
|---------------------------|--------------------------------------------------------------------------------------------------------------------------------|
| Browsertypechrome         | Chrome                                                                                                                         |
| Browsertypefirefox        | Firefox                                                                                                                        |
| Onlineurl                 | <https://make.powerapps.com>                                                                                                   |
| Testautomationurlfilepath | ```$(Build.SourcesDirectory)\<test URL file>.json``` <br>**Hinweis:** Dies ist die [*Datei "Test URLs. JSON*](#step-2---create-test-url-json-file) ", die Sie zuvor erstellt haben.                      |
| Useprivatemode            | true                                                                                                                           |
| Onlineusername            | Geben Sie die Azure Active Directory e-Mail-Adresse des Benutzer Kontexts ein, der sich bei der Anwendung anmelden soll. Tests werden im Kontext dieses Benutzerkontos ausgeführt.\> |

1. Wählen Sie hinzufügen aus, und geben Sie **Online** Password in den Variablennamen ein.

1. Aktivieren Sie das Sperr Abbild, um diese Variable als geheimen Schlüssel zu markieren.

    ![Variablen](media/test-studio-classic-pipeline-editor/variables.png)

1. **Speichern** Sie die Pipeline Konfigurationen.

## <a name="run-and-analyze-tests"></a>Ausführen und Analysieren von Tests

Um zu überprüfen, ob die Tests erfolgreich ausgeführt werden, wählen Sie **Warteschlange** und dann **Ausführen**aus. Der Auftrag wird gestartet.

![Auftrag ausführen](media/test-studio-classic-pipeline-editor/run-job.png)

Wenn der Auftrag ausgeführt wird, wählen Sie den Auftrag aus, um einen detaillierten Status für jede ausgeführte Aufgabe anzuzeigen:

![Auftragsdetails](media/test-studio-classic-pipeline-editor/job-details.png)

Wenn der Auftrag abgeschlossen ist, können Sie die allgemeine Auftrags Zusammenfassung sowie alle Fehler oder Warnungen anzeigen. Durch Auswählen der Registerkarte Test können Sie bestimmte Details zu den Testfällen anzeigen, die Sie ausgeführt haben.

Im folgenden Beispiel wird angegeben, dass mindestens einer unserer Testfälle fehlgeschlagen ist, während die Tests mit dem Chrome-Browser ausgeführt werden:

![Chrome-Fehler](media/test-studio-classic-pipeline-editor/chrome-failed.png)

Wählen Sie **runtestautomation** -Test aus, um die Details zu den fehlgeschlagenen Testfällen anzuzeigen. Auf der *Registerkarte Anlagen*können Sie die Zusammenfassung der Testausführung und die fehlerhaften Testfälle in der Test Sammlung anzeigen:

![Registerkarte Anlagen](media/test-studio-classic-pipeline-editor/attachments-tab.png)

> [!NOTE]
> Wenn Sie eine Test Sammlung ausführen, wird eine Zusammenfassung der bestandenen Testfälle angezeigt. Wenn Sie einen Testfall ausführen, werden bestimmte Details zum Fehler mit Ablauf Verfolgungs Informationen angezeigt, sofern verfügbar.

## <a name="known-limitations"></a>Bekannte Einschränkungen

- Multi-Factor Authentication wird nicht unterstützt.

- Internet Explorer 11 und Microsoft Edge sind keine unterstützten Browser.

- Bei der Test Zusammenfassung wird ein einzelnes Testergebnis pro Browser gemeldet. Das Testergebnis enthält einen oder mehrere Testfälle oder Test Auflistungs Ergebnisse.   

- Jeder andere Authentifizierungsprozess als Azure Active Directory Anmeldevorgang erfordert eine Anpassung des Anmeldevorgangs in der **powerappstestautomation** -Lösung.

### <a name="see-also"></a>Siehe auch

- [Test Studio: Übersicht](test-studio.md)
- [Arbeiten mit Test Studio](working-with-test-studio.md)