---
title: Analysieren von App-Telemetriedaten mit Application Insights | Microsoft-Dokumentation
description: Analysieren von App-Telemetriedaten mit Application Insights
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/25/2020
ms.author: aheaney
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: cf7e65d395e8ad28e434cc957502a5bce52a3e6e
ms.sourcegitcommit: 77e00640a59a7db9d67d3ac52f74d264cbe3a494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2020
ms.locfileid: "80328914"
---
# <a name="analyze-app-telemetry-using-application-insights"></a>Analysieren der APP-Telemetrie mit Application Insights

Sie können Ihre APP mit [Application Insights](https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview)verbinden, einer Funktion von [Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview). Application Insights bietet leistungsstarke Analysetools, mit denen Sie Probleme diagnostizieren und nachvollziehen können, welche Benutzer Ihre APP tatsächlich verwenden. 

Mit Ihrer APP, die mit Application Insights verbunden ist, können Sie Informationen sammeln, die Ihnen helfen, bessere Geschäftsentscheidungen zu treffen und die Qualität Ihrer apps zu verbessern.

In dieser Schnellstartanleitung Instrumentieren Sie eine Canvas-App namens Kudos. Dies hilft Ihnen dabei, telemetriekonzepte zu erforschen und auf Ihre eigenen Canvas-apps anzuwenden. Die Kudos-Beispiel-APP ist Teil einer Suite von Employee Engagement-apps, die vom [Employee Samples Starter Kit](https://powerapps.microsoft.com/blog/powerapps-employee-experience-starter-kit)heruntergeladen werden können.

## <a name="prerequisites"></a>Erforderliche Komponenten

- Sie müssen Zugriff auf [Azure-Portal](https://portal.azure.com)haben.
- Sie müssen über die Berechtigungen zum [Erstellen von Azure-Ressourcen](https://docs.microsoft.com/azure/role-based-access-control/quickstart-assign-role-user-portal)verfügen.

### <a name="optional"></a>Optional

- Herunterladen und Installieren der Kudos-App aus dem [Starter Kit der Employee](https://powerapps.microsoft.com/blog/powerapps-employee-experience-starter-kit)-Funktion. Sie können stattdessen auch eine vorhandene App verwenden.

## <a name="create-an-application-insights-resource"></a>Erstellen einer Application Insights Ressource

Bevor Sie Telemetriedaten für eine APP senden können, müssen Sie eine Azure-Anwendung Insights-Ressource erstellen, um die Ereignisse zu speichern.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com/)an.

1. Suchen Sie nach Application Insights:

    ![Azure Application Insights](./media/application-insights/azureappinsights.png)

1. Erstellen Sie eine Application Insights Ressource:

    ![Hinzufügen einer Azure-Anwendung Insights-Ressource](./media/application-insights/azureappinsights-add.png)

1. Geben Sie die entsprechenden Werte ein, und wählen Sie **überprüfen + erstellen**. Weitere Informationen finden Sie unter [Erstellen einer Application Insights Ressource](https://docs.microsoft.com/azure/azure-monitor/app/create-new-resource). 

    ![Erstellen einer Ressource](./media/application-insights/createresource.png)

1. Nachdem die Application Insights Instanz erstellt wurde, wird die instanzübersicht angezeigt. Kopieren Sie den **Instrumentierungs Schlüssel**. Sie benötigen diesen Schlüssel, um Ihre APP zu konfigurieren.

    ![Instrumentierungs Schlüssel kopieren](./media/application-insights/instrumentation-key.png)

## <a name="connect-your-app-to-application-insights"></a>Verbinden Ihrer APP mit Application Insights

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.

1. Wählen Sie im linken Navigationsbereich **apps** aus. Wählen Sie in der Liste der apps die **Kudos** -App aus, und klicken Sie dann auf **Bearbeiten**:

    ![Bearbeiten der Kudos-App](./media/application-insights/edit-kudos-app.png)

    > [!NOTE]
    > Stattdessen können Sie auch eine neue APP [Erstellen](open-and-run-a-sample-app.md) oder eine beliebige vorhandene APP [Bearbeiten](edit-app.md) .

1. Wählen Sie in der linken Navigationsstruktur das **App** -Objekt aus, und fügen Sie den **Instrumentierungs Schlüssel**ein:

    ![Instrumentierungs Schlüssel hinzufügen](./media/application-insights/add-instrumentation-key.png)

1. **Speichern** Sie & **veröffentlichen** Sie Ihre APP.

1. **Spielen** Sie die veröffentlichte APP, und Durchsuchen Sie verschiedene Bildschirme. 

Beim Durchsuchen verschiedener Bildschirme werden Ereignisse automatisch in Application Insights protokolliert, einschließlich der Verwendungs Details wie z. b.:

- Der Zugriff auf die APP über.
- Dabei handelt es sich um die verwendeten Geräte.
- Die verwendeten Browsertypen.

> [!IMPORTANT]
> Sie müssen die veröffentlichte App wiedergeben, um Ereignisse an Application Insights zu senden. Ereignisse werden nicht an Application Insights gesendet, wenn Sie in Power apps Studio eine Vorschau der App anzeigen.

## <a name="view-events-in-application-insights"></a>Anzeigen von Ereignissen in Application Insights

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com/) an, und öffnen Sie die Application Insights Ressource, die Sie [zuvor](#create-an-application-insights-resource)erstellt haben.

1. Scrollen Sie im linken Navigationsbereich nach unten, und wählen Sie im Abschnitt **Verwendung** den Abschnitt **Benutzer** aus. 

    > [!NOTE]
    > Die Ansicht " **Benutzer** " zeigt Nutzungs Details der APP an, z. b.:
    > - Anzahl der Benutzer, die die App angezeigt haben.
    > - Anzahl der Sitzungen durch die Benutzer für die app.
    > - Anzahl von Ereignissen, die für die APP protokolliert wurden.
    > - Betriebssysteme und Browser Versions Details der Benutzer.
    > - Region und Standort der Benutzer.
    > 
    > Weitere Informationen finden Sie [unter Benutzer, Sitzungen und Ereignis Analyse in Application Insights](https://docs.microsoft.com/azure/azure-monitor/app/usage-segmentation).

1. Wählen Sie eine der Benutzersitzungen aus, um Details zu bestimmten Details anzuzeigen. Informationen wie die Sitzungs Länge und die besuchten Bildschirme können angezeigt werden:

    ![Verwendungs Details für Benutzer](./media/application-insights/appinsights-users.gif)

1. Wählen Sie im linken Navigationsbereich im Abschnitt **Verwendung** die Ansicht **Ereignisse** aus. Eine Zusammenfassung aller Bildschirme, die in allen APP-Sitzungen angezeigt werden, wird angezeigt:

    ![Ereignis Details für die APP](./media/application-insights/appInsights-events.gif)

> [!TIP]
> Einige zusätzliche Application Insights Features, die Sie verwenden können, sind:  
> - [**Trichter**](https://docs.microsoft.com/azure/azure-monitor/app/usage-funnels)
> - [**Kohorten**](https://docs.microsoft.com/azure/azure-monitor/app/usage-cohorts)
> - [**Auswirkungs Analyse**](https://docs.microsoft.com/azure/azure-monitor/app/usage-impact)
> - [**Beibehaltungs Analyse**](https://docs.microsoft.com/azure/azure-monitor/app/usage-retention)
> - [**Verwendungs Abläufe**](https://docs.microsoft.com/azure/azure-monitor/app/usage-flows)

## <a name="create-custom-trace-events"></a>Erstellen benutzerdefinierter Ablauf Verfolgungs Ereignisse

Sie können benutzerdefinierte Ablauf Verfolgungen direkt in Application Insights schreiben und mit der Analyse von Informationen beginnen, die für Ihr Szenario spezifisch sind. Die Ablauf [Verfolgungs](https://docs.microsoft.com/powerapps/maker/canvas-apps/functions/function-trace) Funktion ermöglicht es Ihnen, Folgendes zu erfassen:

- Differenzierte Verwendungs Informationen für Steuerelemente auf den Bildschirmen.
- Welche spezifischen Benutzer auf Ihre App zugreifen.
- Gibt an, welche Fehler auftreten.

Die Ablauf Verfolgung kann auch helfen, Probleme zu diagnostizieren, da Sie eine Spur von Informationen senden können, wenn Ihre Benutzer Ihre APP durchsuchen und verschiedene Aktionen ausführen.

Es gibt drei Schweregrade für Ablauf Verfolgungs Meldungen, wenn Sie benutzerdefinierte Ablauf Verfolgungs Informationen an Application Insights von Ihrer APP senden:

- **Informationen**
- **Davor**
- **Zeit**

Abhängig von Ihrem Szenario können Sie auswählen, ob eine Ablauf Verfolgungs Meldung mit dem entsprechenden Schweregrad gesendet werden soll. Sie können die Daten Abfragen und auf der Grundlage des Nachrichten schwere Grads bestimmte Aktionen durchführen.

> [!NOTE]
> Wenn Sie Personaldaten protokollieren, müssen Sie alle Daten Konformitäts Verpflichtungen in Erwägung gezogen werden, wie z. b. dsgvo, die Sie möglicherweise auch implementieren müssen.

Nun aktualisieren Sie Ihre APP und erstellen eine neue Komponente, um Feedback auf den einzelnen Bildschirmen der APP zu sammeln. Sie schreiben die Ereignisse in Application Insights.

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.

1. Wählen Sie im linken Navigationsbereich **apps** aus. Wählen Sie in der Liste der apps die **Kudos** -App aus, und klicken Sie dann auf **Bearbeiten**.

    > [!NOTE]
    > Stattdessen können Sie auch eine neue APP [Erstellen](open-and-run-a-sample-app.md) oder eine beliebige vorhandene APP [Bearbeiten](edit-app.md) .

1. Wählen Sie in der Struktur **Ansicht**die Option **Komponenten** aus:

    ![Komponenten](./media/application-insights/new-component.png)

1. Wählen Sie **neue Komponente**aus, und ändern Sie die Breite auf 200 und die Höhe auf 75:

    ![Höhe und Breite](./media/application-insights/resize-component.png)

1. Wählen Sie im Menü **Einfügen** aus, und wählen Sie dann **Symbole** aus, um *Emoji-frown-* und *Emoji-Lächeln-* Symbole hinzuzufügen:

    ![Hinzufügen von Symbolen](./media/application-insights/add-icons.png)

1. Wählen Sie **neue benutzerdefinierte Eigenschaft** , um eine benutzerdefinierte Eigenschaft zu erstellen:

    ![Benutzerdefinierte Eigenschaft erstellen](./media/application-insights/create-custom-property.png)

1. Geben Sie den Eigenschaften *Namen* und *anzeigen Amen* ein, z. b. *feedbacksceen*.

1. Geben Sie die Eigenschaften *Beschreibung*ein.

1. Wählen Sie **Eigenschaftentyp** als **Eingabe** und **Datentyp** als **Bildschirm**aus:

    ![Benutzerdefinierte Eigenschaft](./media/application-insights/custom-input-property.png)

    > [!NOTE]
    > Die Eingabe Eigenschaft ermöglicht es Ihnen, den Bildschirmnamen und seine Komponente zu erfassen, damit Sie diese Informationen in Application Insights protokollieren können.

1. Wählen Sie in der Struktur **Ansicht**die Komponente aus, und wählen Sie dann die **weiteren Aktionen** (**...**) und dann **Umbenennen** aus, um die Komponente mit einem aussagekräftigen Namen wie *feedbackcomponent*umzubenennen.

    ![Komponente und Nachteile umbenennen](./media/application-insights/rename-component-icons.png)

1. Wählen Sie Symbole aus, wählen Sie **Weitere Aktionen** (**...**) aus, und wählen Sie dann **Umbenennen** aus, um die Symbole mit aussagekräftigen Namen wie *frownicon* und *smileicon*umzubenennen.

1. Wählen Sie das *frownicon*aus, wählen Sie die **onselect** -Eigenschaft aus, und geben Sie dann den folgenden Ausdruck in die Bearbeitungs Leiste ein:

    ```
    Trace(
       "App Feedback",
       TraceSeverity.Information,
           {
             UserName: User().FullName,
             UserEmail: User().Email,
             Screen: FeedbackComponent.FeedbackScreen.Name,
             FeedbackValue: "-1"
           }
         );
    Notify("Thanks for you feedback!");
    ```

    ![Symbol Formel für Stirnrunzeln](./media/application-insights/frownicon-formula.png)

    > [!NOTE]
    > Der Formel Ausdruck sendet *username*, *useremail*, *Screen* und das *Feedback* (mit dem Wert *-1*) an Application Insights.

1. Wählen Sie das *smileicon*aus, wählen Sie die **onselect** -Eigenschaft aus, und geben Sie dann den folgenden Ausdruck in die Bearbeitungs Leiste ein:
    
    ```
    Trace(
       "App Feedback",
       TraceSeverity.Information,
           {
             UserName: User().FullName,
             UserEmail: User().Email,
             Screen: FeedbackComponent.FeedbackScreen.Name,
             FeebackValue: "1"
           }
         );
    Notify("Thanks for you feedback!");
    ```

1. Fügen Sie die Komponente einem der Bildschirme in Ihrer APP hinzu:

    ![Feedback Komponente hinzufügen](./media/application-insights/add-feedback-component.png)

1. Wählen Sie **Speichern** aus, und klicken Sie dann auf **veröffentlichen** , um & Veröffentlichen Ihrer APP zu speichern

1. Spielen Sie die veröffentlichte APP, und senden Sie ein Lächeln und ein runzeln-Feedback von ihren Bildschirmen.

    > [!IMPORTANT]
    > Sie müssen die veröffentlichte App wiedergeben, um Ereignisse an Application Insights zu senden. Ereignisse werden nicht an Application Insights gesendet, wenn Sie in Power apps Studio eine Vorschau der App anzeigen.

    ![Veröffentlichte App abspielen](./media/application-insights/play-published-app.png)

## <a name="analyze-data-in-application-insights"></a>Analysieren von Daten in Application Insights

Nun können Sie mit der Analyse der Daten beginnen, die Sie mithilfe der Funktion "Ablauf [Verfolgung](#create-custom-trace-events) " aus der Anwendung in App Insights gesendet haben.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com/) an, und öffnen Sie die Application Insights Ressource, die Sie [zuvor](#create-an-application-insights-resource)erstellt haben:

    ![Application Insights auswählen](./media/application-insights/select-app-insights.png)

1. Wählen Sie im linken Navigationsbereich unter **Überwachung** die Option **Protokolle** aus:

    ![Protokolle auswählen](./media/application-insights/select-logs.png)

1. Geben Sie die folgende Abfrage ein, und wählen Sie **Ausführen**. Das von Ihrer APP empfangene Feedback wird zurückgegeben:

    ```powerappsfl
    traces
    | where message == "App Feedback"
    | order by timestamp
    ```

    ![App-Feedback anzeigen](./media/application-insights/view-app-feedback.png)

1. Wählen Sie eine Zeile in den Ergebnissen aus, und erweitern Sie das Feld *benutzerdefinierte Dimensionen* . 

    Die Werte für " **Screen**", " **username**", " **useremail**" und " **feedbackvalue** " für das **onselect** -Ereignis des Symbols "Lächeln" oder "Stirnrunzeln" in der Komponente wurden aufgezeichnet. <br>
    Es werden auch einige zusätzliche Werte für jedes Ereignis aufgezeichnet, das an Application Insights gesendet wurde. beispielsweise " **AppID**", " **appname** " und " **appsessionid**".

    ![Erweitern von benutzerdefinierten Dimensionen](./media/application-insights/expand-custom-dimensions.png)

1. Mit der folgenden Beispiel Abfrage können Sie die Eigenschaften der benutzerdefinierten JSON-Dimensionen erweitern und die Spalten in der Ergebnis Ansicht projizieren.

    ```powerappsfl
    traces
        | extend customdims = parse_json(customDimensions)
        | where message == "App Feedback"
        | project timestamp
            , message
            , AppName = customdims.['ms-appName']
            , AppId = customdims.['ms-appId']
            , FeedbackFrom = customdims.UserEmail
            , Screen = customdims.Screen
            , FeedbackValue = customdims.FeedbackValue
        | order by timestamp desc
    ```

    ![Erweitern der customdimensions-Abfrage](./media/application-insights/custom-dimensions-extend-query.png)

    > [!TIP]
    > *Protokoll Abfragen* sind sehr leistungsstark. Sie können Sie verwenden, um mehrere Tabellen zu verknüpfen, große Datenmengen zusammenzufassen und komplexe Vorgänge auszuführen. Weitere Informationen finden Sie unter [Protokoll Abfragen](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview).

## <a name="export-data-to-power-bi"></a>Exportieren von Daten nach Power BI

Sie können Ihre Application Insights Daten und Abfrageergebnisse in Power BI für Analyse-und Daten Präsentationen exportieren.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com/) an, und öffnen Sie die Application Insights Ressource, die Sie [zuvor](#create-an-application-insights-resource)erstellt haben:

1. Wählen Sie im linken Navigationsbereich unter **Überwachung** die Option **Protokolle** aus:

1. Wählen Sie im Log Analytics-Abfragefenster das Dropdown Menü **exportieren** aus.

1. Wählen Sie **in Power BI Option (M-Abfrage) exportieren** aus. Dadurch wird eine Power BI Abfrage Datei auf Ihren Computer heruntergeladen:

    ![Exportieren Power BI Abfrage](./media/application-insights/export-powerbi-query.png)

1. Öffnen Sie die heruntergeladene Datei in einem Text-Editor, und kopieren Sie die Abfrage in die Zwischenablage.

1. Öffnen Sie Power BI.

1. Wählen Sie im Menüband **Start** das Dropdown Menü **Daten** herunter schreiben aus, und wählen Sie dann **leere Abfrage**aus:

    ![Leere Abfrage Power BI](./media/application-insights/powerbi-blank-query.png)

1. Wählen Sie im Abfragefenster **Erweiterter Editor**aus. Fügen Sie die Abfrage aus Schritt 5 in das Fenster ein, wählen Sie **abgeschlossen**aus, und wählen Sie dann **Schließen & anwenden**aus:

    ![Abfrage Power BI vorab](./media/application-insights/powerbi-advance-query.png)

1. Sie können auch Diagramme und Visualisierungen in Power BI erstellen, um das in Ihrer APP empfangene Feedback darzustellen. Und treffen datenbasierte Entscheidungen und Aktionen.

    ![Diagramme und Visualisierungen](./media/application-insights/powerbi-feedback.png)

## <a name="default-trace-event-context-and-dimensions"></a>Standard-Ablauf Verfolgungs Ereignis-Kontext und-Dimensionen

Ein Satz von Standard Dimensionen wird auch der *customdimensions* -Eigenschaft jedes Ablauf Verfolgungs Ereignisses hinzugefügt. Diese Dimensionen können verwendet werden, um die Anwendungs-und Anwendungs Sitzungen zu identifizieren, in denen die Ereignisse aufgetreten sind. Wenn Sie zusätzliche benutzerdefinierte Daten mithilfe der Ablauf Verfolgungs Funktion protokollieren, werden Sie auch in den benutzerdefinierten Dimensionen angezeigt.

| Dimensions Name  | Stellt Datenelemente                                            |
|-----------------|-------------------------------------------------------|
| MS-AppID        | Die Anwendungs-ID der APP, die das Ereignis gesendet hat.     |
| MS-appname      | Der Anwendungsname der APP, die das Ereignis gesendet hat.   |
| MS-appsessionid | Die Anwendungs Sitzungs-ID.                           |

