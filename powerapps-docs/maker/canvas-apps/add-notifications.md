---
title: Senden einer Pushbenachrichtigung | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie native Pushbenachrichtigungen an eine App in PowerApps senden.
author: kavishi
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 08/08/2017
ms.author: kaagar
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d3f526b8795c8771d3f0e43c2951d207f7f1bfb0
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678900"
---
# <a name="send-a-push-notification-in-powerapps"></a>Senden einer Pushbenachrichtigung in PowerApps
Pushbenachrichtigungen werden bei mobilen Apps für Kunden- und Business-Szenarien in erster Linie verwendet, um mit den App-Benutzern zu kommunizieren und ihnen zu helfen, wichtige Aufgaben zu priorisieren. In powerapps können Sie mithilfe des Benachrichtigungs-Connector für Power apps Benachrichtigungen senden. Sie können native Pushbenachrichtigungen an jede APP senden, die Sie in powerapps erstellen. In Zukunft sollen weitere Benachrichtigungstypen hinzukommen.

![Beispiel für eine Pushbenachrichtigung](./media/add-notifications/pic1-notification-screenshot.png)

Fügen Sie in den folgenden Situationen Pushbenachrichtigungen in Apps hinzu:

* Ihre Benutzer müssen Informationen sofort erhalten.
* Die Benutzer müssen wichtige Aufgaben mit der App in einem vordefinierten Kontext ausführen.
* Sie möchten regelmäßig mit den Benutzern interagieren oder die Benutzer sollen die App in einem bestimmten Kontext öffnen.

> [!NOTE]
> Um Pushbenachrichtigungen zu erhalten, muss jeder Benutzer die APP einmal in powerapps Mobile geöffnet oder die APP aus appsource in [Dynamics 365](https://home.dynamics.com/)abgerufen haben.

## <a name="before-you-start"></a>Bevor Sie beginnen
Fügen Sie in einer APP, für die Sie über die Berechtigung **Mitwirkender** verfügen, eine Power apps-Benachrichtigungs Verbindung hinzu Wenn Sie noch keine App haben, können Sie schnell eine [App aus einer Vorlage erstellen](get-started-test-drive.md). So verfügen Sie standardmäßig über die erforderliche Berechtigung. In dem genannten Tutorial und hier wird eine App auf Grundlage der Vorlage für das Fallmanagement verwendet.

## <a name="send-a-notification-from-a-flow"></a>Senden einer Pushbenachrichtigung aus einem Flow
> [!NOTE]
> Wenn Sie eine Pushbenachrichtigung in einem Flow auslösen, können Sie die Benachrichtigung derzeit jeweils nur an einen Benutzer oder eine Sicherheitsgruppe senden.

1. Erstellen Sie in der [Energie Automatisierung](https://flow.microsoft.com)einen-Auslösers, der angibt, wann die Pushbenachrichtigung gesendet wird.

    Angenommen, Sie möchten eine Benachrichtigung senden, wenn ein Datensatz zur **Case**-Entität im Common Data Service hinzugefügt wird.

    ![Screenshot: Erstellen eines Flows mit einem Common Data Service-Trigger](./media/add-notifications/pic4-step1-flowupdated.png)
2. Erstellen Sie mithilfe des Benachrichtigungs-Connector für **Power apps** eine Aktion für den Flow, und geben Sie die **App-ID** der APP ein, an die Benachrichtigungen gesendet werden sollen.

    Sie können die Verbindung auch für Ihr Szenario umbenennen.

    ![Screenshot: Erstellen einer Verbindung mit den powerapps, die diese Pushbenachrichtigungen erhalten](./media/add-notifications/pic5-step2-create-connection.jpg)
3. (Optional) Übergeben Sie Parameter an die App, wenn sie geöffnet wird (nachdem der Benutzer auf die Pushbenachrichtigung getippt hat).

    In diesem Beispiel werden die Felder **Case ID** (Fall-ID) und **Initial Owner** (Erster Besitzer) für den ausgewählten Kontakt übergeben.

    ![Screenshot: Übergeben von optionalen Parametern an die Pushbenachrichtigung](./media/add-notifications/pic6-step3-configure-notif.jpg)

## <a name="send-a-notification-from-an-app"></a>Senden einer Benachrichtigung aus einer App
Sie können eine Pushbenachrichtigung aus einer App an eine andere App oder an die gleiche App senden.

1. Öffnen Sie die App, an die Pushbenachrichtigungen gesendet werden sollen, in [PowerApps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).
2. Kopieren Sie auf der Registerkarte **Details** die **App-ID** dieser App.

    ![App-ID abrufen](./media/add-notifications/grab-id.png)
3. Erstellen Sie auf der Registerkarte **Verbindungen** eine Verbindung mit dem powerapps-Benachrichtigungs-Connector, und fügen Sie die APP-ID aus dem vorherigen Schritt ein.

    ![Erstellen der Verbindung](./media/add-notifications/create-connection.png)
4. Fügen Sie die Verbindung der Trigger-App hinzu.

    In unserem Beispiel verwenden wir die gleiche App wie die Trigger-App. Der Benutzer, der den Fall erneut zuweist, löst auch eine Pushbenachrichtigung an den neuen Besitzer des Falls aus.

    ![Hinzufügen einer Verbindung](./media/add-notifications/add-connection.png)
5. Rufen Sie in der Pushbenachrichtiungsverbindung die **SendPushNotification**-Methode auf.

    In unserem Beispiel wird diese Benachrichtigung mit der **OnSuccess**-Eigenschaft in einem Formular ausgelöst.

    ![Powerapps-Formel](./media/add-notifications/powerapps-function.png)

## <a name="load-a-specific-page-and-context-when-a-user-taps-the-notification"></a>Laden einer bestimmten Seite und eines bestimmten Kontexts, wenn ein Benutzer auf die Benachrichtigung tippt
### <a name="pass-parameters"></a>Übergeben von Parametern
Die Pushbenachrichtigung kann bestimmte Parameter an die App übergeben. Verwenden Sie z.B. zum Lesen des **CaseID**-Werts *Param("CaseID")* . Um diesen Parameter schnell zu ermitteln, fügen Sie der App ein **Label**-Steuerelement hinzu. Legen Sie die **Text**-Eigenschaft dieses Steuerelements auf **Param("CaseID")** fest. Wenn der Benutzer die App über die Liste **Alle Apps** öffnet, ist der Wert leer. Wenn der Benutzer die App von einem anderen Speicherort auf dem Gerät öffnet, wird der Wert mit dem **CaseID**-Wert aufgefüllt.

### <a name="set-the-start-page"></a>Festlegen der Startseite
Sie können festlegen, dass beim Öffnen der App z.B. die Seite **Case details** (Falldetails) geöffnet wird:

1. Fügen Sie ein **Timer**-Steuerelement hinzu, und legen Sie seine **OnTimerEnd**-Eigenschaft auf diese Formel fest:
   <br>**Navigate(EditCase, ScreenTransition.None)**
2. (Optional) Blenden Sie das **Timer**-Steuerelement aus, indem Sie die **Visible**-Eigenschaft auf **false** festlegen.
3. Legen Sie die **OnVisible**-Eigenschaft des Bildschirms auf **Timer.Start()** fest.

> [!TIP]
> Sie sollten für die Benachrichtigung eine spezielle erste Seite erstellen:
> 
> 1. Erstellen Sie eine leere Seite, die Ihre App nicht bereits öffnet, fügen Sie ein **Texteingabe**-Steuerelement hinzu, und legen Sie den **timer.Duration**-Wert fest.
> 2. Wenn Sie die App erstellen, legen Sie den Timer auf einen Wert ungleich 0 (null) fest. Wenn Sie die App veröffentlichen möchten, legen Sie den Wert auf **0** fest, um den Timer sofort auszulösen.

## <a name="syntax"></a>Syntax

| Name | Beschreibung |
| --- | --- |
| SendPushNotification |Sendet eine Pushbenachrichtigung an die App, die in den Verbindungseinstellungen für die Benachrichtigung angegeben wurde. |

### <a name="parameters"></a>Metern

| Name | Typ | Beschreibung |
| --- | --- | --- |
| recipients |Zeichenfolgenarray, erforderlich |Liste mit: <ul> <li>E-Mail-Adressen für Benutzer oder Sicherheitsgruppen</li> <li>Objekt-IDs für Benutzer oder Sicherheitsgruppen in Azure Active Directory</li></ul> |
| message |Zeichenfolge, erforderlich |Nachrichtentext für die Pushbenachrichtigung |
| openApp |Boolesch, optional |Gibt an, ob die App geöffnet wird, wenn der Benutzer auf die Pushbenachrichtigung tippt |
| params |Parameter, optional |Schlüsselwertparameter, die mit der Benachrichtigung übergeben werden Diese können in der App weiterverarbeitet werden, um eine bestimmte Seite zu öffnen und einen bestimmten Zustand zu laden. |

### <a name="sample-formulas"></a>Beispielformeln
Senden einer einfachen Benachrichtigung

```powerapps-dot
PowerAppsNotification.SendPushNotification(
    {
        recipients: ["f60ccf6f-7579-4f92-967c-2920473c966b", "72f988bf-86f1-41af-91ab-2d7cd011db47"],
        message: "A new case was assigned to you."
    }
)
```

Senden einer Benachrichtigung, die eine App öffnet und bestimmte Parameter übergibt

```powerapps-dot
PowerAppsNotification.SendPushNotification(
    {
        recipients: ["email1@contoso.com", "email2@contoso.com"],
        message: "message in the notif toast",
        params: Table({key:"notificationKey", value:"The value for notificationKey"}),
        openApp: true
    }
)
```

## <a name="known-limitations"></a>Bekannte Einschränkungen
* Zurzeit werden Benachrichtigungen nicht in Power Apps Mobile für Windows Phone angezeigt.
* Derzeit werden keine Pushbenachrichtigungen für Benutzer bereitgestellt, die Apps nur in einem Webbrowser ausführen.
* Benachrichtigungen zeigt anstelle eines bestimmten app-Symbols das generische Symbol "powerapps" an.
* Wenn Sie die Energie Automatisierung verwenden, können Sie eine Pushbenachrichtigung an jeweils nur einen Empfänger senden.

Referenzinformationen finden Sie unter [Power apps-Benachrichtigungs Referenz](https://docs.microsoft.com/connectors/powerappsnotification/).

