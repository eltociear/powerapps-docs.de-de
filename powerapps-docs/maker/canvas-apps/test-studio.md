---
title: Test Studio zum Testen von Canvas-Apps | Microsoft-Dokumentation
description: Informationen zu Test Studio einschließlich einer Übersicht, Terminologie, bewährter Methoden und Einschränkungen
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/18/2019
ms.author: aheaney
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: dc5ad83a127c812c2a97750ce0fbd05abee50bc7
ms.sourcegitcommit: 6b2961308c41867756ecdd55f55eccbebf70f7f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "76541173"
---
# <a name="test-studio-experimental"></a>Test Studio (experimentell) 

Erstellen Sie mithilfe von Test Studio End-to-End-Tests für die Benutzeroberfläche Ihrer Canvas-App. Wahren Sie die Qualität Ihrer App, indem Sie stets prüfen, ob sie wie erwartet funktioniert, wenn neue Änderungen und Updates bereitgestellt werden. 

## <a name="overview"></a>Übersicht

Tests sind ein wichtiger Bestandteil moderner Lebenszyklen der Softwareentwicklung. Sie können dabei helfen, die Qualität der Apps zu gewährleisten, die den Kunden bereitgestellt werden. Sie tragen dazu bei, dass bereits in einer frühen Phase des Releaseprozesses Probleme oder Fehler gefunden werden können, und bieten die Möglichkeit, diese zu beheben, damit die App an Zuverlässigkeit gewinnt, bevor die Änderungen veröffentlicht werden. Je nach Größe und Nutzung der App können manuelle Tests von Änderungen ausreichend sein. Wenn die App jedoch komplexer und vermehrt genutzt wird, sollten Sie sich ggf. eine Teststrategie als Alternative für manuelle Tests überlegen. Wenn die App eine wesentliche Bedeutung für Ihr Unternehmen hat, kann schon der kleinste Fehler große Auswirkungen haben.

Wenn vermehrt Änderungen an der App vorgenommen werden, sind unter Umständen auch die Testzyklen länger. Mit der Zeit dauern die Regressionstests dann möglicherweise sogar länger als die Entwicklung neuer Features. In Zeiten schnelllebiger Entwicklung können ausführliche Tests jedes einzelnen Features einer App die Veröffentlichung von Softwareupdates verzögern. Die Testautomatisierung stellt eine Möglichkeit dar, in Testzyklen und bei Regressionstests Zeit zu sparen. Mithilfe der Testautomatisierung können Sie Ihre App mit wenig Aufwand in kurzer Zeit testen und schwerwiegende Probleme vor dem Release erkennen.

Die Low-Code-Lösung Test Studio von Power Apps bietet die Möglichkeit, Tests für Canvas-Apps zu schreiben, zu organisieren und zu automatisieren. Sie können mithilfe von Power Apps-Ausdrücken in Test Studio Tests schreiben oder Aufzeichnungen verwenden, um App-Interaktionen zu speichern und die Ausdrücke anschließend zu generieren. Sie können in Test Studio geschriebene Tests wiedergeben, um die App-Funktionen zu überprüfen. Außerdem können Sie die Tests in einem Webbrowser ausführen und die automatisierten Tests in Ihren Prozess zum Bereitstellen von Apps integrieren.

![Test Studio](./media/test-studio/test-studio.png)

> [!NOTE]
> Dieses Feature ist noch experimentell, und Sie sollten es noch nicht zum Schreiben von Tests für Apps verwenden, die nicht für die Produktion vorgesehen sind. Weitere Informationen finden Sie unter [Experimentelle Features und Previewfunktionen](working-with-experimental-preview.md).

## <a name="test-studio-terminology"></a>Terminologie zu Test Studio

Im folgenden Abschnitt werden die wichtigsten Begriffe zu Test Studio erläutert:

### <a name="test-cases"></a>Testfälle

Testfälle bestehen aus einer Reihe von Anweisungen oder Aktionen, die als Testschritte bezeichnet werden. Testfälle werden ausgeführt, um zu überprüfen, ob Ihre App oder bestimmte Features in Ihrer App erwartungsgemäß funktionieren. Angenommen, Sie möchten beispielsweise in einer App für Ausgaben sicherstellen, dass nur Ausgaben übermittelt werden können, denen auch tatsächlichen Kosten zugeordnet werden. Mit einem Testfall kann gewährleistet werden, dass diese Bedingung oder Anforderung immer erfüllt ist.

In Test Studio werden die Testschritte mithilfe der Power Apps-Ausdruckssprache geschrieben. Testausdrücke können sowohl aus den Funktionen, die beim Erstellen der App verfügbar sind, als auch aus zusätzlichen Ausdrücken bestehen, um die automatisierten Tests zu unterstützen.

### <a name="test-suites"></a>Testsammlungen

Testsammlungen werden verwendet, um Testfälle zusammen zu sortieren oder zu gruppieren. Wenn immer mehr Testfälle zu einer App hinzukommen, bietet es sich möglicherweise an, diese in bestimmte Features oder Funktionen zu sortieren. Zum Beispiel können Sie eine Testsammlung mit Testfällen zum Überprüfen der übermittelten Ausgabenberichte erstellen und eine weitere Testsammlung verwenden, deren Fokus auf den Genehmigungen von Ausgaben liegt.

In Testsammlungen enthaltene Testfälle werden sequenziell ausgeführt. Der App-Status wird für alle Testfälle in einer Sammlung beibehalten. Wenn z. B. ein Testfall in Bildschirm 5 Ihrer App abgeschlossen wird, beginnt der nächste Testfall in Ihrer Testsammlung ab Bildschirm 5. Dadurch haben Sie die Möglichkeit, komplexe Testszenarios in mehrere Testfälle innerhalb einer einzelnen Sammlung zu unterteilen, und der Status wird für alle Testfälle übernommen. Wenn Ihr zweiter Testfall auf dem Startbildschirm der App beginnen soll, können Sie im ersten Schritt für Ihren Testfall zum Startbildschirm navigieren. Beachten Sie dabei, dass die App nicht zu Beginn jedes Testfalls in einer Testsammlung neu geladen wird, wenn Sie die Testausführung planen.

### <a name="test-assertions"></a>Testassertionen

Für jeden Testfall sollte es ein zu erwartendes Ergebnis geben. Sie können Testassertionen schreiben, um das erwartete Ergebnis eines Tests mit dem tatsächlichen Testergebnis abzugleichen. Eine Assertion ist ein Ausdruck, der die Ergebnisse TRUE oder FALSE für den jeweiligen Test zurückgibt. Wenn der Ausdruck FALSE zurückgibt, schlägt dieser Testfall fehl.

Im obigen Beispiel der Ausgaben-App können Sie eine Assertion schreiben, um zu überprüfen, ob ein Ausgabenbericht mit einer Position erstellt wird, der keine Kosten zugeordnet sind.

## <a name="best-practices"></a>Bewährte Methoden

Beachten Sie beim Testen der Canvas-App mithilfe von Test Studio die folgenden bewährten Methoden, um die Qualität Ihrer App zu optimieren:

1. **Bestimmen Sie, welche Testfälle automatisiert werden sollen.**

    Es ist schwierig, alle Tests zu automatisieren, und es wird nicht empfohlen, sich voll und ganz auf die Testautomatisierung zu verlassen. Neben automatisierten Tests sollten auch manuelle Tests durchgeführt werden. Tests, die am besten für die Automatisierung geeignet sind:

    - wiederkehrende Tests
    - Tests von Funktionen, die essenziell für das Geschäft sind
    - Features, die beständig sind und an denen keine wesentlichen Änderungen vorgenommen werden
    - Features, für die mehrere Datasets erforderlich sind
    - manuelle Tests, die viel Zeit und Mühe kosten

2. **Arbeiten Sie mit möglichst kleinen Testfällen.**

    Zwar können Sie mit nur einem Testfall alle Funktionen Ihrer App testen, aber es wird nicht empfohlen, monolithische Testfälle zu schreiben. Erstellen Sie besser mehrere einzelne Testfälle. Sie könnten beispielsweise für jedes Feature oder jede Funktion Ihrer App einen eigenen Testfall verwenden. Ein Assertionsfehler in einem größeren Testfall kann dazu führen, dass andere Funktionen nicht getestet werden. Durch die Verwendung mehrerer Testfälle in einer Testsammlung werden andere Funktionen unabhängig davon getestet, ob ein vorheriger Testfall fehlgeschlagen ist. Bei dieser Strategie können Testfehler auch besser isoliert werden.

3. **Beschränken Sie Ausdrücke auf eine einzelne Testaktion.**

    Eine Testaktion kann mehre Ausdrücke enthalten. Größere Testausdrücke für mehrere Aktionen für einen einzelnen Schritt können Sie daran hindern, mögliche Testfehler zu debuggen und zu isolieren. Unterteilen Sie Testschritte mit mehreren Aktionen besser in mehrere Schritte mit einzelnen Aktionen, um Probleme schneller ermitteln zu können.  

4. **Für jeden Testfall sollte es ein zu erwartendes Ergebnis geben.**

    Für jeden Testfall sollte es mindestens ein zu erwartendes Ergebnis geben. Sie sollten Testassertionen verwenden, um die zu erwartenden Ergebnisse Ihres Tests mit den tatsächlichen Ergebnissen abzugleichen. Pro Testfall können mehrere Assertionen geschrieben werden.

5. **Verwenden Sie Testsammlungen.**

    Gruppieren oder kategorisieren Sie aus Wartungsgründen einzelne Testfälle zusammen, und stellen Sie Beschreibungen des Zwecks und des zu erwartenden Ergebnisses für Ihren Test zur Verfügung.

## <a name="known-limitations"></a>Bekannte Einschränkungen

Es wird derzeit daran gearbeitet, Vollzugriff in Power Apps Test Studio zu integrieren. Aktuell sind die folgenden Funktionen nicht verfügbar:

- Komponenten
- Codekomponenten, die in Power Apps Component Framework geschrieben wurden
- verschachtelte Kataloge
- Mediensteuerelemente
- Das experimentelle Feature zur Fehlerverwaltung auf Formelebene muss für die App aktiviert werden.
- Unterstützung für Steuerelemente, die nicht in den Funktionen [Select](./functions/function-select.md) und [SetProperty](./functions/function-setproperty.md) aufgeführt sind.
- Spalten für die Personentypen
