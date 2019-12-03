---
title: App-Objekt | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für das App-Objekt in powerapps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/29/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c2e34a9f466fcb64bcf14ef6a504d5b18b0a596d
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74676742"
ms.PowerAppsDecimalTransform: true
---
# <a name="app-object-in-powerapps"></a>App-Objekt in powerapps

Stellt Informationen über die derzeit laufende App bereit und steuert das Verhalten der app.

## <a name="description"></a>Beschreibung

Wie ein-Steuerelement stellt das **App** -Objekteigenschaften bereit, mit denen der Bildschirm angezeigt wird, der den Benutzer auffordert, Änderungen zu speichern, damit Sie nicht verloren gehen. Jede APP verfügt über ein **App** -Objekt.

Sie können Formeln für einige Eigenschaften des **App** -Objekts schreiben. Wählen Sie oben im Struktur **Ansichts** Bereich das **App** -Objekt wie jedes andere Steuerelement oder Bildschirm aus. Sie können eine der Eigenschaften des Objekts anzeigen und bearbeiten, indem Sie Sie in der Dropdown Liste links neben der Bearbeitungs Leiste auswählen.

> [!div class="mx-imgBorder"]
> ![Sie das App-Objekt im Struktur Ansichts Bereich](media/object-app/appobject.png)

## <a name="activescreen-property"></a>Activescreen (Eigenschaft)

Die **activescreen** -Eigenschaft identifiziert den Bildschirm, der angezeigt wird.

Diese Eigenschaft gibt ein Bildschirm Objekt zurück, das Sie verwenden können, um auf Eigenschaften des Bildschirms zu verweisen oder mit einem anderen Bildschirm zu vergleichen, um zu bestimmen, welcher Bildschirm angezeigt wird Sie können auch den Ausdruck **app.ActiveScreen.Name** verwenden, um den Namen des Bildschirms abzurufen, der angezeigt wird.

Verwenden Sie die Funktion **[Back](function-navigate.md)** oder **[Navigate](function-navigate.md)** , um den Bildschirm zu ändern, der angezeigt wird.

## <a name="onstart-property"></a>OnStart-Eigenschaft

Die **OnStart** -Eigenschaft wird ausgeführt, wenn der Benutzer die APP startet. App-Ersteller verwenden diese Eigenschaft häufig, um die folgenden Aufgaben auszuführen:

- Abrufen und Zwischenspeichern von Daten in Sammlungen mithilfe der **[Collect](function-clear-collect-clearcollect.md)** -Funktion.
- Richten Sie globale Variablen mit der **[Set](function-set.md)** -Funktion ein.
- Navigieren Sie mit der **[Navigate](function-navigate.md)** -Funktion zu einem ersten Bildschirm.

Diese Formel wird ausgewertet, bevor der erste Bildschirm angezeigt wird. Es wurde kein Bildschirm geladen, sodass Sie keine Kontext Variablen mit der Funktion **[updatecontext](function-updatecontext.md)** festlegen können. Sie können jedoch Kontext Variablen mit der **Navigate** -Funktion übergeben.

Nachdem Sie die **OnStart** -Eigenschaft geändert haben, testen Sie Sie, indem Sie im Struktur **Ansichts** Bereich auf das **App** -Objekt zeigen, **und wählen Sie**dann die Schaltfläche mit den Auslassungs Punkten (...) aus, die angezeigt wird. Wenn die APP zum ersten Mal geladen wird, werden bereits vorhandene Sammlungen und Variablen festgelegt. Verwenden Sie die **[clearcollect](function-clear-collect-clearcollect.md)** -Funktion anstelle der **Collect** -Funktion, um mit leeren Auflistungen zu beginnen.

> [!div class="mx-imgBorder"]
> ![App-Element-Kontextmenü für "OnStart" ausführen](media/object-app/appobject-runonstart.png)

## <a name="confirmexit-properties"></a>Confirmexit-Eigenschaften

Niemand möchte nicht gespeicherte Änderungen verlieren. Verwenden Sie die Eigenschaften **confirmexit** und **confirmexitmessage** , um den Benutzer vor dem Schließen Ihrer APP zu warnen.

> [!NOTE]
> **Confirmexit** funktioniert nicht in apps, die in eingebettet sind, z. b. Power BI und SharePoint.

> [!NOTE]
> Diese Eigenschaften können derzeit nur auf Steuerelemente auf dem ersten Bildschirm verweisen, wenn die Vorschau Funktion für **Verzögertes Laden** aktiviert ist (Dies ist standardmäßig für neue apps der Fall). Wenn Verweise erstellt werden, zeigt Power apps Studio keinen Fehler an, aber die resultierende veröffentlichte APP wird nicht in powerapps Mobile oder einem Browser geöffnet. Wir arbeiten aktiv daran, diese Einschränkung aufzuheben. In der Zwischenzeit können Sie das **verzögerte Laden** in **Datei** > **App-Einstellungen** > **erweiterten Einstellungen** (unter **Vorschau Features**) deaktivieren.

### <a name="confirmexit"></a>Confirmexit

**Confirmexit** ist eine boolesche Eigenschaft, die bei *true*ein Bestätigungs Dialogfeld öffnet, bevor die app geschlossen wird. Standardmäßig ist diese Eigenschaft *false*, und es wird kein Dialogfeld angezeigt.

Verwenden Sie diese Eigenschaft, um ein Bestätigungs Dialogfeld anzuzeigen, wenn der Benutzer Änderungen vorgenommen, aber nicht gespeichert hat. Verwenden Sie eine Formel, die Variablen und Steuerelement Eigenschaften überprüfen kann (z. b. die **nicht gespeicherte** Eigenschaft des [**Bearbeitungs Formular**](../controls/control-form-detail.md) -Steuer Elements).

Das Bestätigungs Dialogfeld wird in jeder Situation angezeigt, in der Daten verloren gehen können, wie in den folgenden Beispielen:

- Ausführen der [**Exit**](function-exit.md) -Funktion.
- Wenn die app in einem Browser ausgeführt wird:
  - Schließen des Browsers oder der Browser Registerkarte, in der die app ausgeführt wird.
  - Die Schaltfläche "zurück" des Browsers wird ausgewählt.
- Wenn die app in powerapps Mobile (IOS oder Android) ausgeführt wird:
  - Die [**Launch**](function-param.md) -Funktion wird ausgeführt.<br>Die **Launch** -Funktion löst das Dialogfeld in einem Browser nicht aus, da eine andere Registerkarte geöffnet wird, sodass keine Daten verloren gehen.
  - Wischen Sie, um zu einer anderen app in Power Apps Mobile zu wechseln.
  - Auswählen der Schaltfläche "zurück" auf einem Android-Gerät.

Das genaue Erscheinungsbild des Bestätigungs Dialogfelds kann von Geräten und Versionen von powerapps abweichen.

Das Bestätigungs Dialogfeld wird in powerapps Studio nicht angezeigt.

### <a name="confirmexitmessage"></a>Confirmexitmessage

Standardmäßig zeigt das Bestätigungs Dialogfeld eine generische Meldung an, z **. b. "möglicherweise sind nicht gespeicherte Änderungen vorhanden".** in der Sprache des Benutzers.

Verwenden Sie **confirmexitmessage** , um im Bestätigungs Dialogfeld eine benutzerdefinierte Meldung bereitzustellen. Wenn diese Eigenschaft *leer*ist, wird der Standardwert verwendet. Benutzerdefinierte Nachrichten werden nach Bedarf gekürzt, damit Sie in das Bestätigungs Dialogfeld passen. behalten Sie die Nachricht also höchstens ein paar Zeilen.

In einem Browser wird das Bestätigungs Dialogfeld möglicherweise mit einer generischen Meldung aus dem Browser angezeigt.

### <a name="example"></a>Beispiel

1. Erstellen Sie eine APP, die zwei Formular Steuerelemente enthält: **accountform** und **contactform**.

1. Legen Sie die **confirmexit** -Eigenschaft des **App** -Objekts auf diesen Ausdruck fest:

    ```powerapps-comma
    AccountForm.Unsaved Or ContactForm.Unsaved
    ```

    Dieses Dialogfeld wird angezeigt, wenn der Benutzerdaten in einem der beiden Formulare ändert und dann versucht, die APP zu schließen, ohne diese Änderungen zu speichern.

    > [!div class="mx-imgBorder"]
    > ![generischen Bestätigungs Dialogfeld](media/object-app/confirm-native.png)

1. Legen Sie die **confirmexitmessage** -Eigenschaft des **App** -Objekts auf diese Formel fest:

    ```powerapps-comma
    If( AccountsForm.Unsaved;
        "Accounts form has unsaved changes.";
        "Contacts form has unsaved changes."
    )
    ```

    Dieses Dialogfeld wird angezeigt, wenn der Benutzer die Daten im Kontoformular ändert und dann versucht, die APP zu schließen, ohne diese Änderungen zu speichern.

    > [!div class="mx-imgBorder"]
    > ![Formular spezifisches Bestätigungs Dialogfeld](media/object-app/confirm-native-custom.png)
