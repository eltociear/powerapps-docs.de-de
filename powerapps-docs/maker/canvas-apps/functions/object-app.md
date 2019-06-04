---
title: App-Objekt | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen, für das App-Objekt in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/29/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 232accd1050fb84816e86ea95069b8c8778f6586
ms.sourcegitcommit: 562c7ed5fbb116be1cbb0f45e3f6e75e3e4cf011
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2019
ms.locfileid: "66451608"
ms.PowerAppsDecimalTransform: true
---
# <a name="app-object-in-powerapps"></a>App-Objekt, in PowerApps

Enthält Informationen über die aktuell ausgeführte app und die Kontrolle über das Verhalten der app.

## <a name="description"></a>Beschreibung

Wie Sie ein Steuerelement, das **App** -Objekt bietet Eigenschaften, die identifizieren, welcher Bildschirm angezeigt wird, die der Benutzer aufgefordert, Änderungen zu speichern, damit sie nicht verloren gehen. Jede app hat eine **App** Objekt.

Sie können Formeln für einige Eigenschaften der Schreiben der **App** Objekt. Am oberen Rand der **Strukturansicht** wählen Sie im Bereich der **App** Objekt wie alle anderen steuern oder würden Bildschirm. Zeigen Sie an und bearbeiten Sie eine der Eigenschaften des Objekts durch Auswahl aus der Dropdown-Liste auf der linken Seite der Bearbeitungsleiste.

> [!div class="mx-imgBorder"]
> ![Das App-Objekt in der Strukturansicht anzuzeigen](media/object-app/appobject.png)

## <a name="activescreen-property"></a>ActiveScreen-Eigenschaft

Die **ActiveScreen** identifiziert den Bildschirm, der angezeigt wird.

Diese Eigenschaft gibt ein Bildschirmobjekt, die Sie verwenden können, verweisen auf Bildschirmeigenschaften oder vergleichen mit einem anderen Bildschirm, um zu bestimmen, welcher Bildschirm angezeigt wird. Sie können auch den Ausdruck **App.ActiveScreen.Name** um den Namen des Bildschirms abzurufen, die angezeigt wird.

Verwenden der **[wieder](function-navigate.md)** oder **[Navigate](function-navigate.md)** Funktion, um den Bildschirm zu ändern, die angezeigt wird.

## <a name="onstart-property"></a>OnStart-Eigenschaft

Die **OnStart** Eigenschaft ausgeführt wird, wenn der Benutzer die app startet. App-Entwickler verwenden diese Eigenschaft normalerweise zum Ausführen dieser Aufgaben:

- Abrufen und Zwischenspeichern von Daten in Sammlungen mithilfe der **[sammeln](function-clear-collect-clearcollect.md)** Funktion.
- Einrichten der globalen Variablen mithilfe der **[festgelegt](function-set.md)** Funktion.
- Navigieren Sie zu einer ersten Bildschirm mit der **[Navigate](function-navigate.md)** Funktion.

Diese Formel wird ausgewertet, bevor der erste Bildschirm angezeigt wird. Kein Bildschirm geladen wird, damit Sie Kontextvariablen mit festlegen, können die **["updatecontext"](function-updatecontext.md)** Funktion. Sie können aber auch Kontextvariablen mit übergeben die **Navigate** Funktion.

Nach dem Ändern der **OnStart** -Eigenschaft, testen, indem Sie mit dem Mauszeiger auf die **App** -Objekt in der **Strukturansicht** Bereich, Sie auf die Auslassungspunkte (...), der angezeigt wird, und wählen dann **Ausführen OnStart**. Im Gegensatz zu, wenn die app zum ersten Mal geladen wird werden vorhandene Auflistungen und Variablen bereits festgelegt. Für den Einstieg leere Sammlungen, verwenden Sie die **[ClearCollect](function-clear-collect-clearcollect.md)** -Funktion anstelle von der **sammeln** Funktion.

> [!div class="mx-imgBorder"]
> ![App-Menü für arbeitselementverknüpfung in OnStart ausführen](media/object-app/appobject-runonstart.png)

## <a name="confirmexit-properties"></a>ConfirmExit-Eigenschaften

Niemand möchte, dass nicht gespeicherte Änderungen verloren gehen. Verwenden der **ConfirmExit** und **ConfirmExitMessage** Eigenschaften, die den Benutzer zu warnen, bevor sie Ihre app zu schließen.

> [!NOTE]
> **ConfirmExit** funktioniert nicht in apps, die in, z. B. eingebettet sind Power BI und SharePoint.

> [!NOTE]
> Derzeit können diese Eigenschaften nur der erste Bildschirm Steuerelemente verweisen, wenn die **verzögerte Laden** Vorschaufeature aktiviert ist (es wird standardmäßig für neue apps ist). Wenn Verweise vorgenommen werden, wird PowerApps Studio keinen Fehler angezeigt, aber nicht die resultierende veröffentlichte app in PowerApps Mobile oder in einem Browser geöffnet. Wir arbeiten aktiv daran, diese Einschränkung aufzuheben. In der Zwischenzeit können Sie deaktivieren **verzögerte Laden** in **Datei** > **Anwendungseinstellungen** > **Erweiterte Einstellungen**(unter **Vorschaufeatures**).

### <a name="confirmexit"></a>ConfirmExit

**ConfirmExit** ist eine boolesche Eigenschaft, wenn *"true"* , geöffnet wird, wird ein Bestätigungsdialogfeld die app geschlossen wird. Diese Eigenschaft ist standardmäßig *"false"* , und kein Dialogfeld angezeigt wird.

Verwenden Sie diese Eigenschaft, um ein Bestätigungsdialogfeld angezeigt wird, wenn der Benutzer Änderungen vorgenommen hat, aber nicht werden gespeichert. Verwenden Sie eine Formel, die Variablen überprüfen und steuern die Eigenschaften kann (z. B. die **Unsaved** Eigenschaft der [ **Bearbeitungsformular** ](../controls/control-form-detail.md) Steuerelement).

Das Dialogfeld zur Bestätigung wird angezeigt, in einer Situation, in denen Daten wie in diesen Beispielen verloren gehen könnten:

- Ausführen der [ **beenden** ](function-exit.md) Funktion.
- Wenn die app in einem Browser ausgeführt wird:
  - Schließen den Browser oder die Registerkarte "Browser" in der die app ausgeführt wird.
  - Wählen im Browser auf die Schaltfläche "zurück".
- Wenn die app in PowerApps Mobile (iOS oder Android) ausgeführt wird:
  - Ausführen der [ **starten** ](function-param.md) Funktion.<br>Die **starten** Funktion nicht das Dialogfeld in einem Browser auslösen, da eine andere Registerkarte öffnet, damit Daten nicht verloren geht.
  - Wischen, um in eine andere app in PowerApps Mobile zu wechseln.
  - Auswählen der Schaltfläche "zurück", auf einem Android-Gerät.

Die genaue Darstellung der im Dialogfeld zum bestätigen kann übergreifend für Geräte und PowerApps-Versionen variieren.

Das Dialogfeld zur Bestätigung wird in PowerApps Studio angezeigt.

### <a name="confirmexitmessage"></a>ConfirmExitMessage

Standardmäßig zeigt das Dialogfeld zur Bestätigung eine generische Meldung, z. B. **"Möglicherweise Ihre ungespeicherten Änderungen."** in der Sprache des Benutzers.

Verwendung **ConfirmExitMessage** , geben Sie eine benutzerdefinierte Meldung in das Dialogfeld zur Bestätigung. Wenn diese Eigenschaft *leere*, der Standardwert verwendet wird. Benutzerdefinierte Meldungen werden abgeschnitten, sofern nötig, um in das Dialogfeld zur Bestätigung passen, wird, der die Nachricht in ein paar Zeilen höchstens.

In einem Browser möglicherweise das Dialogfeld zur Bestätigung über dem Browser mit eine generische Meldung angezeigt.

### <a name="example"></a>Beispiel

1. Erstellen Sie eine app, die zwei Formularsteuerelemente, enthält **AccountForm** und **ContactForm**.

1. Legen Sie die **App** des Objekts **ConfirmExit** Eigenschaft auf den folgenden Ausdruck:

    ```powerapps-comma
    AccountForm.Unsaved Or ContactForm.Unsaved
    ```

    Dieses Dialogfeld wird angezeigt, wenn der Benutzer Daten in einer der Formen geändert und anschließend wird versucht, die app zu schließen, ohne die Änderungen zu speichern.

    > [!div class="mx-imgBorder"]
    > ![Generische Bestätigungsdialogfeld](media/object-app/confirm-native.png)

1. Legen Sie die **App** des Objekts **ConfirmExitMessage** -Eigenschaft auf diese Formel:

    ```powerapps-comma
    If( AccountsForm.Unsaved;
        "Accounts form has unsaved changes.";
        "Contacts form has unsaved changes."
    )
    ```

    Dieses Dialogfeld wird angezeigt, wenn der Benutzer Daten in das Formular ändert und anschließend wird versucht, die app zu schließen, ohne die Änderungen zu speichern.

    > [!div class="mx-imgBorder"]
    > ![Dialogfeld zum Bestätigen der Formular-spezifische](media/object-app/confirm-native-custom.png)
