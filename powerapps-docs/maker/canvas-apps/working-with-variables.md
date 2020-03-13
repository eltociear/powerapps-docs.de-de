---
title: Grundlegendes zu Variablen in Canvas-Apps | Microsoft-Dokumentation
description: Referenzinformationen zum Arbeiten mit Zustands- und Kontextvariablen und Sammlungen in Canvas-Apps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/07/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d7fb0e386309f207809204d4f9f582aa3aedfe7e
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79212743"
---
# <a name="understand-canvas-app-variables-in-power-apps"></a>Grundlegendes zu Canvas-App-Variablen in powerapps

Wenn Sie eine anderes Programmiertool verwenden, wie z.B. Visual Basic oder JavaScript, fragen Sie sich möglicherweise: **Wo sind die Variablen?** Power Apps ist ein wenig anders und erfordert einen anderen Ansatz. Statt auf eine Variable zurückzugreifen, wenn Sie eine Canvas-App erstellen, sollten Sie sich die Frage stellen: **Wie würde ich in Excel verfahren?**

In anderen Tools haben Sie möglicherweise eine explizite Berechnung ausgeführt und das Ergebnis in einer Variablen gespeichert. In Power apps und Excel werden Formeln jedoch sowohl automatisch neu berechnet, wenn die Eingabedaten geändert werden. Daher müssen Sie in der Regel keine Variablen erstellen und aktualisieren. Wenn Sie diesen Ansatz wann immer möglich verwenden, können Sie Ihre App leichter erstellen, verstehen und warten.

In einigen Fällen müssen Sie Variablen in powerapps verwenden, die das Modell von Excel erweitern, indem Sie [Verhaltens Formeln](working-with-formulas-in-depth.md)hinzufügen. Diese Formeln werden z.B. ausgeführt, wenn ein Benutzer eine Schaltfläche auswählt. Innerhalb einer Verhaltensformel ist es oft hilfreich, eine Variable festzulegen, die in anderen Formeln verwendet werden soll.

Vermeiden Sie im allgemeinen das Verwenden von Variablen. Manchmal hat jedoch nur eine Variable die Auswirkungen, die Sie benötigen. Variablen werden implizit erstellt und eingegeben, wenn Sie in Funktionen angezeigt werden, die ihre Werte festlegen. 

## <a name="translate-excel-into-power-apps"></a>Übersetzen von Excel in powerapps

### <a name="excel"></a>Excel

Betrachten Sie die Funktionsweise von Excel. Eine Zelle kann einen Wert, z.B. eine Zahl oder eine Zeichenfolge, oder eine Formel enthalten, die auf den Werten der anderen Zellen basiert. Nachdem der Benutzer einen anderen Wert in eine Zelle eingibt, berechnet Excel automatisch alle Formeln, die von dem neuen Wert abhängig sind. Zum Aktivieren dieses Verhaltens müssen Sie nichts programmieren.

Im folgenden Beispiel wird Zelle **a3** auf die Formel **a1 + a2**festgelegt. Wenn **a1** oder **a2** geändert wird, wird **a3** automatisch neu berechnet, um die Änderung widerzuspiegeln. Dieses Verhalten erfordert keine Codierung außerhalb der Formel selbst.

![Animation der Neuberechnung der Summe von zwei Zahlen in Excel](media/working-with-variables/excel-recalc.gif)

Excel verfügt nicht über Variablen. Der Wert einer Zelle, die eine Formel enthält, ändert sich abhängig von seiner Eingabe; es gibt allerdings keine Möglichkeit, das Ergebnis einer Formel in einer Zelle oder an einer anderen Stelle zu speichern. Wenn Sie den Wert einer Zelle ändern, ändert sich möglicherweise das gesamte Arbeitsblatt, und alle zuvor berechneten Werte gehen verloren. Ein Excel-Benutzer kann Zellen kopieren und einfügen, aber dies unterliegt der manuellen Eingabe des Benutzers und ist mit Formeln nicht möglich.

### <a name="power-apps"></a>Power Apps

Apps, die Sie in powerapps erstellen, Verhalten sich ähnlich wie Excel. Statt Zellen zu aktualisieren, können Sie Steuerelemente überall auf dem Bildschirm hinzufügen und sie für den Einsatz in Formeln benennen.

Beispielsweise können Sie das Excel-Verhalten in einer APP replizieren, indem Sie ein **[Label](controls/control-text-box.md)** -Steuerelement mit dem Namen **Label1**und zwei **[Text Eingabe](controls/control-text-input.md)** -Steuerelemente mit den Namen **TextInput1** und **TextInput2**hinzufügen. Wenn Sie dann die **[Text](controls/properties-core.md)** -Eigenschaft von **Label1** auf **TextInput1 + TextInput2**festlegen, wird immer die Summe aller Zahlen in **TextInput1** und **TextInput2** automatisch angezeigt.

![Berechnen der Summe von zwei Zahlen in Power apps](media/working-with-variables/recalc1.png)

Beachten Sie, dass das **Label1** -Steuerelement ausgewählt ist und seine Text Formel in der **[Bearbeitungs](controls/properties-core.md)** Leiste oben auf dem Bildschirm anzeigt. Hier finden Sie die Formel **TextInput1 + TextInput2**. Diese Formel erstellt eine Abhängigkeit zwischen diesen Steuerelementen, genauso wie Abhängigkeiten zwischen den Zellen in einer Excel-Arbeitsmappe erstellt werden.  Ändern Sie den Wert von **TextInput1**:

![Animation der Berechnung der Summe von zwei Zahlen in Power apps](media/working-with-variables/recalc2.gif)

Die Formel für **Label1** wurde automatisch neu berechnet und zeigt den neuen Wert.

In powerapps können Sie Formeln verwenden, um nicht nur den primär Wert eines Steuer Elements zu bestimmen, sondern auch Eigenschaften wie z. b. die Formatierung. Im nächsten Beispiel zeigt eine Formel für die **[Color](controls/properties-color-border.md)** -Eigenschaft der Bezeichnung automatisch negative Werte rot an. Die **[If](functions/function-if.md)** -Funktion ist Ihnen wahrscheinlich aus Excel vertraut:

`If( Value(Label1.Text) < 0, Red, Black )`

![Animation der bedingten Formatierung](media/working-with-variables/recalc-color.gif)

Sie können verschiedene Formeln für eine Vielfalt an Szenarios verwenden:

* Indem Sie das GPS Ihres Geräts verwenden, kann ein Kartensteuerelement mit einer Formel, die **Location.Latitude** und **Location.Longitude** verwendet, Ihre aktuelle Standort anzeigen.  Während Sie sich bewegen, verfolgt die Karte automatisch Ihren Standort.
* Andere Benutzer können [Datenquellen](working-with-data-sources.md) aktualisieren.  Andere Mitglieder Ihres Teams können z.B. die Elemente in einer SharePoint-Liste aktualisieren.  Wenn Sie eine Datenquelle aktualisieren, werden alle abhängigen Formeln automatisch neu berechnet, um die aktualisierten Daten widerzuspiegeln. Wenn Sie das Beispiel fortführen, können Sie beispielsweise die **[Items](controls/properties-core.md)** -Eigenschaft eines Katalogs auf die Formel **Filter (SharePointList)** festlegen, sodass automatisch die neu gefilterte Menge von [Datensätze](working-with-tables.md#records) angezeigt wird.

### <a name="benefits"></a>Vorteile

Das Erstellen von Apps mithilfe von Formeln hat viele Vorteile:

* Wenn Sie Excel kennen, kennen Sie powerapps. Das Modell und die Formelsprache sind identisch.
* Wenn Sie schon mal andere Programmiertools verwendet haben, können Sie sich vorstellen, wie viel Code erforderlich wäre, um diese Beispiele zu realisieren.  In Visual Basic müssten Sie einen Ereignishandler für das Änderungsereignis für jedes Texteingabe-Steuerelement erstellen.  Der Code, der jede dieser Berechnung ausführen soll, ist redundant und könnte möglicherweise nicht mehr synchron abgerufen werden, oder Sie müssten eine gängige Unterroutine schreiben.  In Power apps haben Sie all dies mit einer einzigen, einzeiligen Formel erreicht.
* Um zu verstehen, woher der Text von **Label1**stammt, wissen Sie genau, wo Sie suchen können: die Formel in der **[Text](controls/properties-core.md)** -Eigenschaft.  Es gibt keine andere Möglichkeit, den Text dieses Steuerelements zu beeinflussen.  In einem herkömmlichen Programmiertool könnte jeder Ereignishandler und jede Unterroutine überall im Programm den Wert des Bezeichners ändern.  Dadurch kann es schwieriger sein, einzugrenzen, wann und wo eine Variable geändert wurde.
* Wenn der Benutzer ein Schieberegler-Steuerelement ändert und es sich dann noch mal anders überlegt, kann er den Schieberegler wieder auf den ursprünglichen Wert zurücksetzen.  Und es ist, als ob nichts geändert worden wäre: Die Anwendung zeigt die gleichen Steuerelementwerte wie vorher an.  Das Experimentieren und Fragen nach „Was wäre wenn“ hat keine Folgen, genauso wenig wie in Excel.  

Im Allgemeinen sind Sie bessergestellt, wenn Sie durch das Verwenden einer Formel einen Effekt erzielen können. Lassen Sie die Formel-Engine in Power Apps für Sie arbeiten.  

## <a name="know-when-to-use-variables"></a>Wann es sinnvoll ist, Variablen zu verwenden

Passen Sie Ihren einfachen Addierer an, sodass er sich wie eine traditionelle Rechenmaschine mit einer laufenden Summe verhält. Wenn Sie eine **Add**-Schaltfläche (Hinzufügen) auswählen, fügen Sie eine Zahl zur laufenden Summe hinzu. Wenn Sie eine **Clear**-Schaltfläche (Löschen) auswählen, setzen Sie die laufende Summe auf 0 (null) zurück.

| Anzeige | Beschreibung |
|----|----|
| <style>IMG {max-width: None}</style> ![App mit einem Text Eingabe-Steuerelement, einer Bezeichnung und zwei Schaltflächen](media/working-with-variables/button-changes-state-1.png) | Wenn die APP gestartet wird, wird die laufende Summe auf 0 (null).<br><br>Der rote Punkt stellt den Finger des Benutzers im Texteingabefeld dar, in dem der Benutzer **77**eingibt. |
| ![Das Text Eingabe-Steuerelement enthält 77, und die Schaltfläche hinzufügen wird gedrückt.](media/working-with-variables/button-changes-state-2.png) | Der Benutzer wählt die Schaltfläche **Hinzufügen** aus. |
| ![Der Gesamtwert ist 77, und ein weiterer 77 wird hinzugefügt.](media/working-with-variables/button-changes-state-3.png) | 77 wird der laufenden Summe hinzugefügt.<br><br>Der Benutzer wählt erneut die Schaltfläche **Hinzufügen** aus. |
| ![Die Summe beträgt 154, bevor Sie gelöscht wird.](media/working-with-variables/button-changes-state-4.png) | 77 wird wieder zur laufenden Summe hinzugefügt. Dies ergibt 154.<br><br>Der Benutzer wählt die Schaltfläche **Löschen** aus. |
| ![Die Summe ist gelöscht.](media/working-with-variables/button-changes-state-5.png) | Die laufende Summe wird auf 0 zurückgesetzt. |

Ihre Rechenmaschine verwendet etwas, das es in Excel so nicht gibt: eine Schaltfläche. Sie können in dieser App die laufende Summe nicht mit Formeln allein berechnen, da ihr Wert von einer Reihe von Aktionen des Benutzers abhängt. Stattdessen muss die laufende Summe aufgezeichnet und manuell aktualisiert werden. Die meisten Programmiertools speichern diese Informationen in einer *Variablen*.

Manchmal benötigen Sie für Ihre App eine Variable, um das zu erreichen, was Sie möchten.  Doch dieser Ansatz hat auch Nachteile:

* Sie müssen die laufende Summe manuell aktualisieren. Die automatische Berechnung erfüllt nicht Ihre Ansprüche.
* Die laufende Summe kann nicht mehr basierend auf den Werten anderer Steuerelemente berechnet werden. Dies hängt davon ab, wie oft der Benutzer die Schaltfläche **Add** (Hinzufügen) ausgewählt hat und welcher Wert sich jeweils in dem Texteingabe-Steuerelement befunden hat. Hat der Benutzer 77 eingegeben und **Hinzufügen** zweimal ausgewählt, oder hat er jeweils 24 und 130 für jede der Hinzufügungen angegeben? Nachdem die Summe 154 beträgt, können Sie den Unterschied nicht mehr feststellen.
* Änderungen der Gesamtsumme können aus verschiedenen Pfaden stammen. In diesem Beispiel kann sowohl die **Add**- als auch die **Clear**-Schaltflächen die Gesamtsumme aktualisieren. Wenn die App sich nicht wie erwartet verhält, ist welche Schaltfläche für das Problem verantwortlich?

## <a name="use-a-global-variable"></a>Globale Variable verwenden

Sie benötigen eine Variable, die die laufende Summe enthält, um unseren hinzufügenden Computer zu erstellen. Die einfachsten Variablen, mit denen Sie in Power apps arbeiten können, sind *globale Variablen*.  

Funktionsweise von globalen Variablen:

* Sie legen den Wert der globalen Variablen mit der **[Set](functions/function-set.md)** -Funktion fest.  Durch **Set( MyVar, 1 )** wird die globale Variable **MyVar** auf den Wert **1** festgelegt.
* Sie verwenden die globale Variable, indem Sie mit der **Set**-Funktion auf den verwendeten Namen verweisen.  In diesem Fall gibt **MyVar** den Wert **1** zurück.
* Globale Variablen können beliebige Werte enthalten, z.B. Zeichenfolgen, Zahlen, Datensätze und [Tabellen](working-with-tables.md).

Erstellen Sie Ihre Rechenmaschine mithilfe einer globalen Variablen neu:

1. Fügen Sie ein Texteingabe-Steuerelement mit dem Namen **TextInput1** hinzu, und zwei Schaltflächen mit dem Namen **Button1** und **Button2**.

2. Legen Sie die **[Text](controls/properties-core.md)** -Eigenschaft von **Button1** auf **"Add"** fest, und legen Sie die **Text**-Eigenschaft von **Button2** auf **"Clear"** fest.

3. Legen Sie dieOnSelect **[-Eigenschaft einer ](controls/properties-core.md)Add**-Schaltfläche auf folgende Formel fest, um die laufende Summe zu aktualisieren, wenn ein Benutzer die Schaltfläche auswählt:

    **Set (runningTotal, runningTotal + TextInput1)**

    Durch das bloße vorhanden sein dieser Formel wird **runningTotal** als globale Variable festgelegt, die eine Zahl aufgrund des **+** Operators enthält. Sie können auf " **runningTotal** " in der APP verweisen. Jedes Mal, wenn der Benutzer diese APP öffnet, hat **runningTotal** den Anfangswert *blank*.

    Wenn ein Benutzer zum ersten Mal die Schaltfläche **Hinzufügen** und **[set](functions/function-set.md)** Runs auswählt, wird **runningTotal** auf den Wert **runningTotal + TextInput1**festgelegt.

    ![Die onselect-Eigenschaft der Schaltfläche hinzufügen ist auf Set Function festgelegt.](media/working-with-variables/global-variable-1.png)

4. Legen Sie dieOnSelect-Eigenschaft der **Clear[-Schaltfläche auf folgende Formel fest, um die laufende Summe auf ](controls/properties-core.md)0** festzulegen:

    **Set( RunningTotal, 0 )**

    ![Die onselect-Eigenschaft der Clear-Schaltfläche ist auf Set-Funktion festgelegt.](media/working-with-variables/global-variable-2.png)

5. Fügen Sie ein **[Label](controls/control-text-box.md)** -Steuerelement (Bezeichnung) hinzu, und legen Sie dessen **[Text](controls/properties-core.md)** -Eigenschaft auf **RunningTotal** fest.

    Diese Formel wird automatisch neu berechnet und zeigt dem Benutzer den Wert von **RunningTotal** an, während sie sich auf Grundlage der vom Benutzer ausgewählten Schaltflächen ändert.

    ![Die Text-Eigenschaft der Bezeichnung wird auf den Namen der Variablen festgelegt.](media/working-with-variables/global-variable-3.png)

6. Sehen sie sich eine Vorschau der App an, und Sie sehen die Rechenmaschine, wie sie oben beschrieben wurde. Geben Sie eine Zahl im Textfeld ein, und drücken Sie mehrmals die Schaltfläche **Add**. Kehren Sie anschließend zur Erstellung zurück, indem Sie die ESC-TASTE drücken.

    ![Das Text Eingabe-Steuerelement enthält einen Wert, und die Bezeichnung enthält die laufende Summe.](media/working-with-variables/global-variable-4.png)

7. Um den Wert der globalen Variablen anzuzeigen, wählen Sie das Menü **Datei** aus, und wählen Sie im linken Bereich **Variablen** aus.

    ![Variablen Option im Menü "Datei"](media/working-with-variables/global-variable-file-1.png)

8. Um alle Stellen anzuzeigen, an denen die Variable definiert und verwendet wird, wählen Sie Sie aus.

    ![Liste des Speicher Orts, an dem Variable verwendet wird](media/working-with-variables/global-variable-file-2.png)

## <a name="types-of-variables"></a>Typen von Variablen

Powerapps verfügt über drei Arten von Variablen:

| Variablentyp | Gültigkeitsbereich | Beschreibung | Funktionen, die einrichten |
| --- | --- | --- | --- |
| Globale Variablen |App |Sind am einfachsten zu verwenden. Enthalten eine Zahl, eine Textzeichenfolge, einen booleschen Wert, einen Datensatz, eine Tabelle usw., auf die an einer beliebigen Stelle in der App verwiesen werden kann. |[**Set**](functions/function-set.md) |
| Kontextvariablen |Bildschirm |Ideal für die Übergabe von Werten an einen Bildschirm (ähnelt der Übergabe eines Parameters an eine Prozedur in anderen Sprachen). Kann nur von einem Bildschirm aus referenziert werden. |[**UpdateContext**](functions/function-updatecontext.md)<br>[**Navigate**](functions/function-navigate.md) |
| Auflistungen |App |Enthält eine Tabelle, auf die von überall in der APP verwiesen werden kann. Ermöglichen es, dass der Inhalt der Tabelle geändert wird, und wird nicht in seiner Gesamtheit festgelegt. Können für die spätere Verwendung auf dem lokalen Gerät gespeichert werden. |[**Collect**](functions/function-clear-collect-clearcollect.md)<br>[**ClearCollect**](functions/function-clear-collect-clearcollect.md) |

## <a name="create-and-remove-variables"></a>Erstellen und Entfernen von Variablen

Alle Variablen werden implizit erstellt, wenn Sie in einer **Set**-, **updatecontext**-, **Navigate**-, **Collect**-oder **clearcollect** -Funktion angezeigt werden. Um eine Variable und ihren Typ zu deklarieren, müssen Sie Sie nur in einer dieser Funktionen an einer beliebigen Stelle in Ihrer APP einschließen. Keine dieser Funktionen erstellt Variablen. Sie füllen nur Variablen mit Werten aus. Sie deklarieren Variablen nie explizit wie in einem anderen Programmier Tool, und die gesamte Typisierung ist von der Verwendung implizit.

Beispielsweise können Sie ein Schaltflächen-Steuerelement mit einer **onselect** -Formel haben, die auf **Set (X, 1) festgelegt**ist. Mit dieser Formel wird **X** als Variable mit dem Typ "Number" festgelegt. Sie können **X** in Formeln als Zahl verwenden, und diese Variable hat den Wert *leer* , nachdem Sie die APP geöffnet haben, aber bevor Sie die Schaltfläche auswählen. Wenn Sie die Schaltfläche auswählen **, übergeben Sie** den Wert **1**.

Wenn Sie eine weitere Schaltfläche hinzugefügt und deren **onselect** -Eigenschaft auf **Set (X, "Hello")** festgelegt haben, tritt ein Fehler auf, weil der Typ (Text Zeichenfolge) nicht mit dem Typ in der vorherigen **Menge** (Zahl) identisch ist. Alle impliziten Definitionen der Variablen müssen dem Typ zustimmen. Auch hier ist alles passiert, weil Sie **X** in Formeln erwähnt haben, nicht, weil diese Formeln tatsächlich ausgeführt wurden.

Entfernen Sie eine Variable, indem Sie alle **Set**-, **updatecontext**-, **Navigate**-, **Collect**-oder **clearcollect** -Funktionen entfernen, mit denen die Variable implizit festgelegt wird. Ohne diese Funktionen ist die Variable nicht vorhanden. Außerdem müssen Sie alle Verweise auf die Variable entfernen, da Sie zu einem Fehler führen.

## <a name="variable-lifetime-and-initial-value"></a>Variablen Lebensdauer und Anfangswert

Alle Variablen werden im Arbeitsspeicher gespeichert, während die app ausgeführt wird. Nachdem die app geschlossen wurde, gehen die Werte, die in den Variablen gespeichert wurden, verloren.

Sie können den Inhalt einer Variablen in einer Datenquelle speichern, indem Sie die **Patch** -Funktion oder die **Collect** -Funktion verwenden. Mithilfe der [**SaveData**](functions/function-savedata-loaddata.md) -Funktion können Sie auch Werte in Sammlungen auf dem lokalen Gerät speichern.

Wenn der Benutzer die APP öffnet, haben alle Variablen den Anfangswert *blank*.

## <a name="reading-variables"></a>Lesen von Variablen

Sie verwenden den Variablennamen, um den Wert zu lesen. Beispielsweise können Sie eine Variable mit der folgenden Formel definieren:

`Set( Radius, 12 )`

Anschließend können Sie einfach **RADIUS** überall verwenden, wo Sie eine Zahl verwenden können, und es wird durch **12**ersetzt:

`Pi() * Power( Radius, 2 )`

Wenn Sie eine Kontext Variable mit dem gleichen Namen wie eine globale Variable oder eine Auflistung versehen, hat die Kontext Variable Vorrang. Sie können jedoch immer noch auf die globale Variable oder Auflistung verweisen, wenn Sie den [disambiguations-Operator](functions/operators.md#disambiguation-operator) **[@Radius]** verwenden.

## <a name="use-a-context-variable"></a>Verwenden einer Kontext Variablen

Im Folgenden wird erläutert, wie die Rechenmaschine mit einer Kontextvariablen und nicht mit einer globalen Variablen erstellt wird.

Funktionsweise von Kontextvariablen:

* Mithilfe der **[updatecontext](functions/function-updatecontext.md)** -Funktion oder der **[Navigate](functions/function-navigate.md)** -Funktion erstellen und legen Sie Kontext Variablen implizit fest. Wenn die APP gestartet wird, ist der Anfangswert aller Kontext Variablen *leer*.
* Sie aktualisieren Kontext Variablen mit Datensätzen. In anderen Programmiertools verwenden Sie häufig „=“ für Zuweisungen, wie z.B. in „x = 1“. Verwenden Sie stattdessen für Kontextvariablen **{ x: 1 }** . Wenn Sie eine Kontext Variable verwenden, verwenden Sie Ihren Namen direkt ohne die Datensatz-Syntax.
* Sie können auch eine Kontext Variable festlegen, wenn Sie mit der **[Navigate](functions/function-navigate.md)** -Funktion einen Bildschirm anzeigen. Wenn Sie sich einen Bildschirm als eine Art von Prozedur oder Unterroutine vorstellen, ähnelt diese Vorgehensweise der Parameter Übergabe in anderen Programmier Tools.
* Mit Ausnahme von **[Navigate](functions/function-navigate.md)** sind Kontextvariablen auf den Kontext eines einzelnen Bildschirms beschränkt, wo sie ihren Namen erhalten. Außerhalb dieses Kontexts können Sie sie weder verwenden noch festlegen.
* Kontextvariablen können jeden Wert enthalten, z.B. Zeichenfolgen, Zahlen, Datensätze und [Tabellen](working-with-tables.md).

Erstellen Sie Ihren hinzufügenden Computer mithilfe einer Kontextvariablen neu:

1. Fügen Sie ein Texteingabe-Steuerelement mit dem Namen **TextInput1** hinzu, und zwei Schaltflächen mit dem Namen **Button1** und **Button2**.

2. Legen Sie die **[Text](controls/properties-core.md)** -Eigenschaft von **Button1** auf **"Add"** fest, und legen Sie die **Text**-Eigenschaft von **Button2** auf **"Clear"** fest.

3. Legen Sie dieOnSelect **[-Eigenschaft einer ](controls/properties-core.md)Add**-Schaltfläche auf folgende Formel fest, um die laufende Summe zu aktualisieren, wenn ein Benutzer die Schaltfläche auswählt:

    **Updatecontext ({runningTotal: runningTotal + TextInput1})**

    Durch das bloße vorhanden sein dieser Formel wird **runningTotal** als Kontext Variable festgelegt, die eine Zahl aufgrund des **+** Operators enthält. Auf diesem Bildschirm können Sie auf **runningTotal** verweisen. Jedes Mal, wenn der Benutzer diese APP öffnet, hat **runningTotal** den Anfangswert *blank*.

    Wenn der Benutzer die Schaltfläche **Hinzufügen** und **[updatecontext](functions/function-updatecontext.md)** zum ersten Mal auswählt, wird **runningTotal** auf den Wert **runningTotal + TextInput1**festgelegt.

    ![Onselect-Eigenschaft der Schaltfläche "hinzufügen"](media/working-with-variables/context-variable-1.png)

4. Legen Sie dieOnSelect-Eigenschaft der **Clear[-Schaltfläche auf folgende Formel fest, um die laufende Summe auf ](controls/properties-core.md)0** festzulegen:

    **UpdateContext( { RunningTotal: 0 } )**

    Hier wird **[UpdateContext](functions/function-updatecontext.md)** erneut mit der Formel **UpdateContext( { RunningTotal: 0 } )** verwendet.

    ![Onselect-Eigenschaft der Schaltfläche "Löschen"](media/working-with-variables/context-variable-2.png)

5. Fügen Sie ein **[Label](controls/control-text-box.md)** -Steuerelement (Bezeichnung) hinzu, und legen Sie dessen **[Text](controls/properties-core.md)** -Eigenschaft auf **RunningTotal** fest.

    Diese Formel wird automatisch neu berechnet und zeigt dem Benutzer den Wert von **RunningTotal** an, während sie sich auf Grundlage der vom Benutzer ausgewählten Schaltflächen ändert.

    ![Text-Eigenschaft der Bezeichnung](media/working-with-variables/context-variable-3.png)

6. Sehen sie sich eine Vorschau der App an, und Sie sehen die Rechenmaschine, wie sie oben beschrieben wurde. Geben Sie eine Zahl im Textfeld ein, und drücken Sie mehrmals die Schaltfläche **Add**. Kehren Sie anschließend zur Erstellung zurück, indem Sie die ESC-TASTE drücken.

    ![Text Eingabe-Steuerelement zeigt einen Wert an, und die Bezeichnung zeigt die laufende Summe an](media/working-with-variables/context-variable-4.png)

7. Sie können den Wert einer Kontextvariablen beim Wechsel zu einem Bildschirm festlegen. Dies ist hilfreich, wenn Sie den „Kontext“ bzw. die „Parameter“ von einem Bildschirm an einen anderen übergeben möchten. Um diese Technik zu veranschaulichen, fügen Sie einen Bildschirm ein, fügen Sie eine Schaltfläche ein, und legen **Sie die onselect** -Eigenschaft auf diese Formel fest

    **Navigate( Screen1, None, { RunningTotal: -1000 } )**

    ![Onselect-Eigenschaft einer Schaltfläche](media/working-with-variables/context-variable-5.png)

    Halten Sie die Alt-Taste gedrückt, während Sie diese Schaltfläche auswählen, um **Screen1** anzuzeigen, und legen Sie die Kontext Variable **runningTotal** auf-1000 fest.

    ![Screen1 ist offen](media/working-with-variables/context-variable-6.png)

8. Um den Wert der Kontext Variablen anzuzeigen, wählen Sie das Menü **Datei** aus, und wählen Sie dann im linken Bereich **Variablen** aus.

    ![Variablen (Option) im Menü "Datei"](media/working-with-variables/context-variable-file-1.png)

9. Um anzuzeigen, wo die Kontext Variable definiert und verwendet wird, wählen Sie Sie aus.

    ![Die Liste, in der eine Variable verwendet wird.](media/working-with-variables/context-variable-file-2.png)

## <a name="use-a-collection"></a>Sammlung verwenden

Veranschaulichen wir abschließend das Erstellen der Rechenmaschine mithilfe einer Sammlung.  Da eine Sammlung eine Tabelle enthält, die leicht geändert werden kann, legen wir fest, dass diese Rechenmaschine bei Eingabe der einzelnen Werte einen „Papierstreifen“ des Werts aufbewahrt.

Funktionsweise von Sammlungen:

* Erstellen Sie Sammlungen mithilfe der **[ClearCollect](functions/function-clear-collect-clearcollect.md)** -Funktion, oder legen Sie diese fest.  Sie können stattdessen die **[Collect](functions/function-clear-collect-clearcollect.md)** -Funktion verwenden; jedoch erfordert diese eine andere Variable statt die alte lediglich zu ersetzen.  
* Eine Sammlung ist eine Art von Datenquelle und somit eine Tabelle. Verwenden Sie die **[First](functions/function-first-last.md)** -Funktion, um auf einen einzelnen Wert in einer Sammlung zuzugreifen, und extrahieren Sie ein Feld aus dem resultierenden Datensatz. Wenn Sie einen einzelnen Wert mit **[ClearCollect](functions/function-clear-collect-clearcollect.md)** verwendet haben, ist dies das **Value**-Feld, wie in diesem Beispiel:<br>
**First (** *VariableName* **). Wert**

Erstellen Sie Ihre Rechenmaschine mithilfe einer Sammlung neu:

1. Fügen Sie ein **[Texteingabe](controls/control-text-input.md)** -Steuerelement mit dem Namen **TextInput1** hinzu, und zwei Schaltflächen mit dem Namen **Button1** und **Button2**.

2. Legen Sie die **[Text](controls/properties-core.md)** -Eigenschaft von **Button1** auf **"Add"** fest, und legen Sie die **Text**-Eigenschaft von **Button2** auf **"Clear"** fest.

3. Legen Sie dieOnSelect **[-Eigenschaft einer ](controls/properties-core.md)Add**-Schaltfläche auf folgende Formel fest, um die laufende Summe zu aktualisieren, wenn ein Benutzer die Schaltfläche auswählt:

    **Collect( PaperTape, TextInput1.Text )**

    Das bloße vorhanden sein dieser Formel richtet **Taschen Bänder** als Sammlung ein, die eine einspaltige Tabelle mit Text Zeichenfolgen enthält. Sie können auf **Taschen Bänder** an beliebiger Stelle in dieser APP verweisen. Wenn ein Benutzer diese APP öffnet, ist das **Taschen Band** eine leere Tabelle.

    Wenn diese Formel ausgeführt wird, wird der neue Wert am Ende der Collection hinzugefügt. Da wir einen einzelnen Wert hinzufügen, wird er von **Collect** automatisch in eine einspaltige Tabelle eingefügt, und der Name der Spalte ist **Wert**, den Sie später verwenden werden.

    ![Onselect-Eigenschaft der Schaltfläche "hinzufügen"](media/working-with-variables/papertape-1.png)

4. Um das Papierband zu löschen, wenn der Benutzer die Schaltfläche **Löschen** auswählt, legen **[Sie dessen onselect](controls/properties-core.md)** -Eigenschaft auf diese Formel fest:

    **Clear( PaperTape )**

    ![Onselect-Eigenschaft der Schaltfläche "Löschen"](media/working-with-variables/papertape-2.png)

5. Fügen Sie eine Bezeichnung hinzu, um die laufende Summe anzuzeigen, und legen Sie ihre **[Text](controls/properties-core.md)** -Eigenschaft auf folgende Formel fest:

    **Sum( PaperTape, Value )**

    ![Text-Eigenschaft der Bezeichnung](media/working-with-variables/papertape-3.png)

6. Um die Rechenmaschine auszuführen, drücken Sie F5, um die Vorschau zu öffnen, geben Sie im Texteingabe-Steuerelement Zahlen ein, und wählen Sie Schaltflächen aus.

    ![Das Text Eingabe-Steuerelement zeigt einen Wert an, und die Bezeichnung zeigt die laufende Summe an](media/working-with-variables/papertape-run-1.png)

7. Drücken Sie die ESC-TASTE, um zum Standardarbeitsbereich zurückzukehren.

8. Fügen Sie zum Anzeigen des Papierstreifens ein **Datentabellen**-Steuerelement hinzu, und legen Sie dessen **[Items](controls/properties-core.md)** -Eigenschaft auf diese Formel fest:

    **PaperTape**

    Wählen Sie im rechten Bereich die Spalte **Wert** aus, um Sie anzuzeigen.

    ![Datentabelle, in der die der Auflistung hinzugefügten Werte angezeigt werden](media/working-with-variables/papertape-4.png)

9. Wählen Sie im **Dateimenü** **Collections** (Sammlungen) aus, um die Werte in Ihrer Sammlung anzuzeigen.

    ![Vorschau der Sammlung "Taschen Band"](media/working-with-variables/papertape-file.png)

10. Fügen Sie zum Speichern und Abrufen der Auflistung zwei zusätzliche Schaltflächen-Steuerelemente hinzu, und legen Sie deren **Text** -Eigenschaften auf **Laden** und **Speichern**fest. Legen **Sie die onselect** -Eigenschaft der Schaltfläche " **Laden** " auf diese Formel fest:

     **Clear( PaperTape ); LoadData( PaperTape, "StoredPaperTape", true )**

     Sie müssen zuerst die Auflistung löschen, da **LoadData** die gespeicherten Werte an das Ende der Auflistung anfügt.

     ![Onselect-Eigenschaft der Schaltfläche "Laden"](media/working-with-variables/papertape-5.png)

11. Legen **Sie die onselect** -Eigenschaft der Schaltfläche **Speichern** auf diese Formel fest:

     **SaveData( PaperTape, "StoredPaperTape" )**

     ![Onselect *-Eigenschaft der Schaltfläche "Speichern"](media/working-with-variables/papertape-6.png)

12. Drücken Sie erneut F5, um die Vorschau aufzurufen, geben Sie Zahlen im Textsteuerelement ein, und wählen Sie Schaltflächen aus. Wählen Sie die Schaltfläche **Save** aus. Schließen Sie die APP, **und laden Sie** Sie neu

> [!NOTE]
> Die Funktion " **SaveData** " und " **LoadData** " in Power Apps Mobile, aber nicht in powerapps Studio oder im Web Player für Power apps.