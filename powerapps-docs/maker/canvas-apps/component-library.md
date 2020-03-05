---
title: Erstellen einer Komponentenbibliothek für Canvas-apps | Microsoft-Dokumentation
description: Bibliothek von wiederverwendbaren Komponenten für Canvas-apps
author: yifwang
ms.service: powerapps
ms.topic: article
ms.date: 02/20/2020
ms.author: yifwang
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ae1b1b7bc7657d513921ddc2513696af9a808299
ms.sourcegitcommit: efb05dbd29c4e4fb31ade1fae340260aeba2e02b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78293130"
---
# <a name="component-library"></a>Komponentenbibliothek

> [!IMPORTANT]
> Dieses Feature befindet sich noch in der öffentlichen Vorschau Phase. Weitere Informationen finden Sie unter [Experimentelle Features und Previewfunktionen](working-with-experimental.md).

Im [Übersichts](create-component.md) Artikel zum Erstellen von Komponenten werden Komponenten in der Canvas-App eingeführt. Wenn Sie Komponenten innerhalb einer APP erstellen, können Sie auch eine Bibliothek von Komponenten erstellen, die wieder verwendet werden können. Durch das Erstellen einer Komponentenbibliothek können APP-Ersteller eine oder mehrere Komponenten auf einfache Weise mit anderen Herstellern teilen und aktualisieren.

Komponenten Bibliotheken sind Container von Komponenten Definitionen, die Folgendes erleichtern:

- Entdecken und Durchsuchen von-Komponenten.
- Veröffentlichen Sie Updates in mehreren Umgebungen.
- Benachrichtigen von App-Herstellern über verfügbare Komponenten Updates. 

> [!NOTE]
> Komponenten Bibliotheken sind die empfohlene Methode, um Komponenten für apps zu verwenden. Wenn Sie die Komponentenbibliothek verwenden, verwaltet eine APP Abhängigkeiten von den verwendeten Komponenten. Der APP-Ersteller wird benachrichtigt, wenn die Updates für abhängige Komponenten verfügbar werden. Daher sollten stattdessen alle neuen wiederverwendbaren Komponenten in den Komponenten Bibliotheken erstellt werden. Eine frühere Power apps-Funktion, die das [Importieren von Komponenten aus einer Canvas-app in eine andere](create-component.md?#import-and-export-components) gestattet hat, wird als veraltet markiert.

## <a name="difference-between-an-app-and-a-component-library"></a>Unterschied zwischen einer APP und einer Komponentenbibliothek

Eine Komponentenbibliothek bietet ein zentralisiertes und verwaltetes Repository von Komponenten für die Wiederverwendbarkeit. 

Beim **Einfügen** im linken Navigationsbereich wird standardmäßig die Registerkarte Komponenten angezeigt, wenn Sie eine Komponentenbibliothek erstellen. Wenn Sie eine APP erstellen, werden in dieser Ansicht anstelle von Komponenten Bildschirme angezeigt. 

Die Bildschirme in einer Komponentenbibliothek sind nur zu Testzwecken verfügbar. Er bietet Bibliotheks Erstellern eine Möglichkeit, die erstellten Komponenten auf dem eigentlichen Bildschirm schnell zu testen und das Aktualisierungs Verhalten zu überprüfen, da die Komponenten im Lauf der Zeit verbessert werden. Um die Komponenten aus der Komponentenbibliothek zu verwenden, müssen Sie eine APP erstellen, die die Komponentenbibliothek verwendet.

Sie können Komponenten Bibliotheks Komponenten mithilfe der Bildschirme in der Bibliothek mit der Wiedergabe Option anzeigen. Wenn Sie die Registerkarte Komponente auswählen, ist die Wiedergabe Option deaktiviert. Die Komponentenbibliothek wird bei Verwendung von powerapps Mobile nicht angezeigt.

> [!NOTE]
> Die in diesem Artikel erörterte Komponentenbibliothek unterscheidet sich vom Komponenten Framework von powerapps, das Entwicklern und Entwicklern das Erstellen von Code Komponenten für Modell gesteuerte und Canvas-Apps ermöglicht. Weitere Informationen finden Sie unter [Übersicht über das Komponenten Framework von powerapps](https://docs.microsoft.com/powerapps/developer/component-framework/overview).

## <a name="working-with-component-library"></a>Arbeiten mit der Komponentenbibliothek

Sie können eine neue Komponentenbibliothek erstellen oder eine vorhandene Komponentenbibliothek von derselben Schnittstelle bearbeiten. Navigieren Sie zu [make.powerapps.com](https://make.powerapps.com), wählen Sie **apps**aus, und wählen Sie dann **Komponenten Bibliotheken**aus:

![Komponentenbibliothek erstellen oder bearbeiten](./media/component-library/create-edit-component-library.png)

## <a name="create-an-example-component-library"></a>Erstellen einer Beispiel-Komponentenbibliothek

Die Schritte zum Erstellen von Komponenten in einer Komponentenbibliothek sind identisch mit dem Erstellen von Komponenten innerhalb einer App. Sie erstellen eine Komponentenbibliothek. Und dann die Schritte zum Erstellen von Komponenten aus dem [Übersichts Beispiel für Komponenten](create-component.md#create-an-example-component)wieder verwenden. Anschließend verwenden Sie die Komponentenbibliothek, um die wiederverwendbaren Komponenten in einer neuen App bereitzustellen.

1. Melden Sie sich bei [make.powerapps.com](https://make.powerapps.com)an.

1. Klicken Sie im linken Navigationsbereich auf **apps** , wählen Sie **Komponenten Bibliotheken**aus, und klicken Sie dann auf **neue Komponentenbibliothek**.

1. Benennen Sie die Komponentenbibliothek als *Menü Komponenten*. Sie können auch einen anderen Namen Ihrer Wahl angeben.

1. Führen Sie die Schritte zum Erstellen von Komponenten aus dem [Übersichts Beispiel für Komponenten](create-component.md#create-an-example-component)aus. Sie müssen Power apps Studio nicht öffnen oder eine neue leere app erstellen, da Sie bereits eine neue Komponentenbibliothek erstellt haben. Beginnen Sie mit Schritt 2. 

    Nachdem Sie die Schritte zum Erstellen von Komponenten ausgeführt haben, befolgen Sie die nächsten Schritte zum [Hinzufügen von Komponenten zu einem Bildschirm](create-component.md#add-component-to-a-screen) mit den Schritten zum [Erstellen der Ausgabe Eigenschaft](create-component.md#create-and-use-output-property). 

1. Nachdem Sie die Komponenten Erstellung und-Tests abgeschlossen haben, speichern Sie die Komponentenbibliothek, indem Sie auf das Menü **Datei** und dann auf **Speichern**klicken. 

    Sie haben auch die Möglichkeit, eine **Versions Notiz**zu speichern. Der Versions Hinweis ist nützlich, um Versionen einer Komponentenbibliothek abzurufen. Und bei der Aktualisierung der in Apps verwendeten Komponenten aus dieser Komponentenbibliothek.

    ![Versions Hinweis beim Speichern der Komponentenbibliothek](./media/component-library/save-component-libray-version-note.png)

    > [!TIP]
    > Der Versions Hinweis ist hilfreich beim Überprüfen der Versionen einer Komponentenbibliothek und der APP-Ersteller, die ihre Komponentenbibliothek zum Überprüfen von Änderungen und zum Aktualisieren von Apps verwenden, die diese Komponenten nach Bedarf nutzen. Weitere Informationen finden Sie unter [Aktualisieren einer Komponentenbibliothek](component-library.md?#update-a-component-library) .   

1. Die gespeicherte Komponentenbibliothek kann veröffentlicht werden. Nur veröffentlichte Komponenten Bibliotheks Updates sind für apps verfügbar, die eine Komponentenbibliothek nutzen. Wählen Sie **veröffentlichen** aus, um die Version der Komponentenbibliothek zu veröffentlichen:

    ![Version der Komponentenbibliothek veröffentlichen](./media/component-library/publish-component-library.png)

## <a name="import-from-a-component-library"></a>Importieren aus einer Komponentenbibliothek

Nachdem Sie eine Komponentenbibliothek erstellt und veröffentlicht haben, können Apps die Komponenten aus dieser Komponentenbibliothek nutzen, indem Sie die Bibliothek importieren. Sie können auch [eine Komponentenbibliothek freigeben](component-library.md#component-library-permissions).

Bearbeiten Sie eine vorhandene APP, oder erstellen Sie eine neue APP, um Sie aus einer Komponentenbibliothek zu importieren. Nachdem die app in Canvas App Studio geöffnet wurde, wählen Sie im linken Navigationsbereich **Einfügen** oder den **+** aus. Klicken Sie dann auf **Get More Components** , um die in der aktuellen Umgebung verfügbaren Komponenten Bibliotheken aufzulisten:

![Weitere Komponenten](./media/component-library/get-more-components.png)

Auf der rechten Seite des Bildschirms wird die Liste der Komponenten Bibliotheken angezeigt, die in der aktuellen Umgebung verfügbar sind. Wählen Sie eine einzelne Komponente aus einer Komponentenbibliothek aus. Oder verwenden **Sie alle auswählen** , um alle Komponenten gleichzeitig aus der Bibliothek zu importieren:

![Importieren von Komponenten](./media/component-library/components.png)

> [!NOTE]
> Wenn der Ersteller die im Abschnitt importieren aufgeführte Komponentenbibliothek nicht sieht, stellen Sie sicher, dass die Komponentenbibliothek für den Ersteller freigegeben ist Weitere Informationen finden Sie unter [Komponenten Bibliotheks Berechtigungen](component-library.md#component-library-permissions). 

Beachten Sie, dass Sie mehr als eine Komponente und über verschiedene Komponenten Bibliotheken hinweg auswählen und importieren können. 

Komponenten, die in der app verfügbar sind, werden unter **benutzerdefinierte** Kategorie in der Liste der Komponenten im **Einfügebereich** aufgelistet. Die Komponenten, die in importierten Komponenten Bibliotheken verfügbar sind, sind unter **Bibliotheks Komponenten** Kategorie aufgeführt:

![Komponenten in die APP einfügen](./media/component-library/insert-components.png)

## <a name="update-a-component-library"></a>Aktualisieren einer Komponentenbibliothek

Sie können vorhandene Komponenten Bibliotheken ändern und alle Änderungen mit zusätzlichen Versions Anmerkungen speichern. Die aktualisierte Komponenten Bibliotheksversion muss jedoch für die Verwendung in vorhandenen apps veröffentlicht werden, die die-Komponentenbibliothek verwenden. In den obigen Schritten der [Komponentenbibliothek](component-library.md#create-an-example-component-library) wird erläutert, wie eine Komponentenbibliothek nach dem Speichern veröffentlicht wird.

Ersteller anderer apps werden benachrichtigt, wenn aktualisierte Komponenten verfügbar sind. Die Benachrichtigung wird angezeigt, wenn die Entwickler die apps in Canvas App Studio bearbeiten. Und können die Komponenten aktualisieren:

![Update verfügbar](./media/component-library/update-available.png)

Wählen Sie **überprüfen**aus, und die Option zum Aktualisieren der Komponente wird angezeigt:

![Komponente aktualisieren](./media/component-library/update-components.png)

Beachten Sie den Versions Hinweis, den Sie bei der Veröffentlichung der Komponenten Bibliotheksversion hinzugefügt haben, hier. 

Wählen Sie **Aktualisieren** aus, um die Komponenten zu aktualisieren.

## <a name="component-library-permissions"></a>Komponenten Bibliotheks Berechtigungen

Das Freigeben einer Komponentenbibliothek funktioniert genauso wie eine Canvas-app. Wenn Sie eine Komponentenbibliothek freigeben, können andere Benutzer die Komponentenbibliothek wieder verwenden. Nach der Freigabe können andere Benutzer die Komponentenbibliothek bearbeiten und Komponenten aus dieser freigegebenen Komponentenbibliothek zum Erstellen und Bearbeiten von apps importieren. Wenn der Benutzer als Mitbesitzer freigegeben ist, kann er die Komponentenbibliothek verwenden, bearbeiten, freigeben, aber nicht löschen oder ändern.

## <a name="known-limitations"></a>Bekannte Einschränkungen

- [Bekannte Einschränkungen](create-component.md#known-limitations) , die für-Komponenten gelten, gelten auch für die Komponentenbibliothek.
- Es ist nicht möglich, Komponenten mithilfe der Komponentenbibliothek aus der lokal gespeicherten Komponenten Bibliotheksdatei zu importieren. Wenn Sie versuchen, eine lokal gespeicherte Komponentenbibliothek mithilfe der **Datei** zu importieren ->  -> **diesem Computer** **Speichern** und die Komponenten Bibliotheksdatei als app herunterladen, wird die folgende Fehlermeldung angezeigt: 

    ![Komponenten Bibliotheksdatei importieren](./media/component-library/import-component-library-file.png)

- Sie [können einer Projekt Mappe keine vorhandenen](add-app-solution.md)Komponenten Bibliotheken hinzufügen. Sie können jedoch neue Komponenten Bibliotheken für Projektmappen erstellen, indem Sie den Flow Komponentenbibliothek hinzufügen verwenden.

- Wenn Sie eine Komponente aus einer Komponentenbibliothek importieren, können Sie Sie nicht innerhalb der Verb raubenden App bearbeiten. Wenn Sie **Komponente bearbeiten**auswählen, wird eine Option angezeigt, mit der Sie eine Kopie der Komponente in der aktuellen app erstellen können, um Änderungen vorzunehmen: 

    ![Bibliotheks Komponente bearbeiten](./media/component-library/edit-library-component.png)

    Wenn Sie **Kopie erstellen**auswählen, wird die Komponente in die lokale App kopiert. Die lokale Kopie der Komponente wird im **Einfügebereich** unter der Kategorie **Benutzer** definiert angezeigt. Diese lokale Kopie der Komponente empfängt keine Updates, wenn eine neue Version der Ursprungs Komponentenbibliothek zu einem späteren Zeitpunkt veröffentlicht wird.
    
- Wenn eine Komponente einer App aus der Komponentenbibliothek hinzugefügt wird und das Design der APP aktualisiert wird, wird die Komponente zu einer lokalen app-Komponente und ist nicht mehr der Master Komponente in der Komponentenbibliothek zugeordnet.

## <a name="next-steps"></a>Nächste Schritte

Erlernen von [Verhaltens Formeln](component-behavior.md) für Canvas-apps

### <a name="see-also"></a>Siehe auch

Lesen Sie die [Übersicht über](create-component.md) Canvas-App-Komponenten und arbeiten mit Komponenten in einer App.
