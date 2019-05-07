---
title: Concurrent-Funktion | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Funktion „Concurrent“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/26/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ce8128f3a5eddf3a67fe2082844bf996c25adc05
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61551431"
ms.PowerAppsDecimalTransform: true
---
# <a name="concurrent-function-in-powerapps"></a>Concurrent-Funktion in PowerApps
Wertet mehrere Formeln gleichzeitig aus.

## <a name="description"></a>Beschreibung
Die **Concurrent**-Funktion wertet mehrere Formeln gleichzeitig aus. In der Regel ausgewertet mehrere Formeln durch Verkettung werden zusammen mit den [ **;** ](operators.md) -Operator, der jeweils nacheinander in der Reihenfolge ausgewertet wird. Wenn die App gleichzeitig Vorgänge ausführt, warten Benutzer nicht mehr so lange auf das gleiche Ergebnis.

Verwenden Sie **Concurrent** in der Eigenschaft [**OnStart**](../controls/control-screen.md) Ihrer App, um die Leistung zu verbessern, wenn die App Daten lädt. Wenn Datenaufrufe bis zum Abschluss der vorherigen Aufrufe nicht gestartet wurden, muss die App auf die Summe aller Anforderungszeiten warten. Wenn die Datenaufrufe zur selben Zeit beginnen, muss die App nur auf die längste Anforderungszeit warten. Webbrowser verbessern oft die Leistung durch Ausführen gleichzeitiger Datenvorgänge.

Sie können die Reihenfolge, in der Formeln in der **Concurrent**-Funktion beginnen, nicht vorhersagen oder die Evaluierung beenden. Formeln innerhalb der **Concurrent**-Funktion sollten keine Abhängigkeiten von anderen Formeln innerhalb der gleichen **Concurrent**-Funktion enthalten. PowerApps gibt einen Fehler aus, sollte dies doch passieren. Sie können problemlos Abhängigkeiten von Formeln von innerhalb der **Concurrent**-Funktion außerhalb der Funktion verwenden, da diese abgeschlossen werden, bevor die **Concurrent**-Funktion startet. Formeln nach der **gleichzeitige** Funktion kann Abhängigkeiten von Formeln in sicher annehmen: sie müssen alle abgeschlossen ist, bevor die **gleichzeitige** Funktion abgeschlossen ist, und fährt mit der nächsten Formel in einer Kette (Wenn Sie Verwenden Sie die **;** Operator). Achten Sie auf subtile Reihenfolgenabhängigkeiten, wenn Sie Funktionen oder Dienstmethoden aufrufen, die Nebeneffekte haben.

Sie können Formeln, die zusammen mit Verketten der **;** Operator in einem Argument für **gleichzeitige**. Beispielsweise wertet **Concurrent( Set( a; 1 );; Set( b; a+1 ); Set( x; 2 );; Set( y; x+2 ) )** **Set( a; 1 );; Set( b; a+1 )** gleichzeitig mit **Set( x; 2 );; Set( y; x+2 )** aus. In diesem Fall sehen die Abhängigkeiten in den Formeln gut aus: **a** wird vor **b** festgelegt und **x** vor **y**.

Je nach Gerät oder Browser, auf bzw. in dem die App ausgeführt wird, können nur eine Handvoll Formeln tatsächlich gleichzeitig ausgewertet werden. **Concurrent** verwendet die verfügbaren Funktionen und wird nicht beendet, bevor nicht alle Formeln ausgewertet wurden.

Wenn Sie die **Fehlerverwaltung auf Formelebene** (in den erweiterten Einstellungen) aktivieren, wird der erste Fehler, der in der Argumentreihenfolge erkannt wird, von **Concurrent** zurückgegeben. Andernfalls wird *blank* zurückgegeben. Wenn alle Formeln erfolgreich sind, wird *TRUE* zurückgegeben. Wenn eine Formel fehlschlägt, wird der Rest dieser Formel angehalten, die anderen Formeln werden aber ganz normal ausgewertet.

Verwenden Sie **Concurrent** nur in [Verhaltensformeln](../working-with-formulas-in-depth.md).

## <a name="syntax"></a>Syntax
**Concurrent**( *Formel1*; *Formel2* [; ...] )

* *Formel(n)*: Erforderlich Formeln, die gleichzeitig ausgewertet werden sollen. Sie müssen mindestens zwei Formeln angeben.

## <a name="examples"></a>Beispiele

#### <a name="loading-data-faster"></a>Schnelleres Laden von Daten

1. Erstellen Sie eine app, und fügen Sie vier Datenquellen aus Common Data Service, SQL Server oder SharePoint hinzu. 

    In diesem Beispiel werden vier Tabellen aus der [Adventure Works-Beispieldatenbank unter SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal) verwendet. Nachdem die Datenbank erstellt wurde, stellen Sie eine Verbindung von PowerApps damit her, und verwenden Sie dazu den vollqualifizierten Servernamen (z.B. „srvname.database.windows.net“):

    ![Verbinden mit der Adventure Works-Datenbank in Azure](media/function-concurrent/connect-database.png)

2. Fügen Sie ein **[Schaltflächen](../controls/control-button.md)**-Steuerelement hinzu, und legen Sie seine **OnSelect**-Eigenschaft auf folgende Formel fest:

    ```powerapps-comma
    ClearCollect( Product; '[SalesLT].[Product]' );;
    ClearCollect( Customer; '[SalesLT].[Customer]' );;
    ClearCollect( SalesOrderDetail; '[SalesLT].[SalesOrderDetail]' );; 
    ClearCollect( SalesOrderHeader; '[SalesLT].[SalesOrderHeader]' )
    ```

3. Aktivieren Sie in [Microsoft Edge](https://docs.microsoft.com/microsoft-edge/devtools-guide/network) oder [Google Chrome](https://developers.google.com/web/tools/chrome-devtools/network-performance/) die Entwicklertools, um den Netzwerkdatenverkehr zu überwachen, während Ihre App ausgeführt wird.

1. Optional: Aktivieren Sie die Einschränkung, um die Auswirkungen dieses Vergleichs auszuweiten.

4. Halten Sie die Alt-Taste gedrückt, klicken Sie auf die Schaltfläche, und beobachten Sie den Netzwerkdatenverkehr.

    Die Tools zeigen vier Anforderungen an, die der Reihe nach ausgeführt werden, ähnlich wie in diesem Beispiel.  Die tatsächlichen Zeiten wurden entfernt, da sie stark variieren.  Das Diagramm zeigt, dass jeder Aufruf nach dem letzten Aufruf, der abgeschlossen wurde, beginnt:

    ![Zeitdiagramm von vier Netzwerkanforderungen, die jeweils nach der Beendigung der vorherigen beginnen und die gesamte Zeitspanne abdecken](media/function-concurrent/chained-network.png)

5. Speichern, schließen und öffnen Sie die App erneut.

    PowerApps speichert Daten zwischen, deshalb führt das Klicken auf die Schaltfläche nicht unbedingt zu vier neuen Anforderungen. Jedes Mal, wenn Sie die Leistung testen möchten, müssen Sie die App schließen und erneut öffnen. Wenn die Einschränkung aktiviert ist, sollten Sie diese deaktivieren, bis Sie für einen weiteren Test bereit sind.

1. Fügen Sie ein zweites **[Schaltflächen](../controls/control-button.md)**-Steuerelement hinzu, und legen Sie seine **OnSelect**-Eigenschaft auf folgende Formel fest:

    ```powerapps-comma
    Concurrent( 
        ClearCollect( Product; '[SalesLT].[Product]' ); 
        ClearCollect( Customer; '[SalesLT].[Customer]' );
        ClearCollect( SalesOrderDetail; '[SalesLT].[SalesOrderDetail]' );
        ClearCollect( SalesOrderHeader; '[SalesLT].[SalesOrderHeader]' )
    )
    ```

    Beachten Sie, dass Sie die gleichen **ClearCollect**-Aufrufe der ersten Schaltfläche hinzugefügt haben, diese jedoch dieses Mal in einer **Concurrent**-Funktion umschlossen und mit Kommas getrennt sind.

2. Löschen Sie den Netzwerkmonitor im Browser.

1. Wenn Sie zuvor die Einschränkung verwendet haben, aktivieren Sie sie erneut.

3. Halten Sie die ALT-TASTE gedrückt, klicken Sie auf die zweite Schaltfläche, und beobachten Sie den Netzwerkdatenverkehr.

    Die Tools zeigen vier Anforderungen an, die gleichzeitig ausgeführt werden, ähnlich wie in diesem Beispiel.  Die tatsächlichen Zeiten wurden wieder entfernt, da sie stark variieren.  Das Diagramm zeigt, dass alle Aufrufe etwa zur selben Zeit beginnen und nicht darauf warten, dass der vorherige Aufruf beendet wird:

    ![Zeitdiagramm mit vier Netzwerkanforderungen, die alle zusammen beginnen und etwa die Hälfte der Zeitspanne umfassen](media/function-concurrent/concurrent-network.png)

    Diese Diagramme basieren auf der gleichen Skalierung. Durch Verwendung von **Concurrent** haben Sie die Gesamtzeit halbiert, die diese Vorgänge für den Abschluss benötigen. 

5. Speichern, schließen und öffnen Sie die App erneut.

#### <a name="race-condition"></a>Racebedingung

1. Fügen Sie dem [Microsoft Translator](../connections/connection-microsoft-translator.md)-Dienst eine Verbindung zu Ihrer App hinzu.

2. Fügen Sie ein [**Texteingabe**](../controls/control-text-input.md)-Steuerelement hinzu, und benennen Sie es in **TextInput1** um, wenn es nicht bereits so heißt.

3. Fügen Sie ein **Schaltflächen**-Steuerelement hinzu, und legen Sie seine **OnSelect**-Eigenschaft auf folgende Formel fest:

    ```powerapps-comma
    Set( StartTime; Value( Now() ) );;
    Concurrent(
        Set( FRTrans; MicrosoftTranslator.Translate( TextInput1.Text; "fr" ) );; 
            Set( FRTransTime; Value( Now() ) );
        Set( DETrans; MicrosoftTranslator.Translate( TextInput1.Text; "de" ) );; 
            Set( DETransTime; Value( Now() ) )
    );;
    Collect( Results;
        { 
            Input: TextInput1.Text;
            French: FRTrans; FrenchTime: FRTransTime - StartTime; 
            German: DETrans; GermanTime: DETransTime - StartTime; 
            FrenchFaster: FRTransTime < DETransTime
        }
    )
    ```

4. Fügen Sie ein Steuerelements des Typs [**Datentabelle**](../controls/control-data-table.md) hinzu, und legen Sie seine **Items**-Eigenschaft auf **Results** (Ergebnisse) fest.

1. Auf der **Eigenschaften** im rechten Bereich auf der Registerkarte **Felder bearbeiten** zum Öffnen der **Felder** Bereich.

1. Aktivieren Sie in der Feldliste das Kontrollkästchen für jedes Feld, sodass alle in der Datentabelle angezeigt werden.

1. Optional: Ziehen Sie das Feld **Input** (Eingabe) an den Anfang der Liste und das Feld **FrenchFaster** an das Ende der Liste.

    ![Liste der Felder in der Ergebnisauflistung](media/function-concurrent/field-list.png) 

6. Geben bzw. fügen Sie im Steuerelement **Texteingabe** einen zu übersetzen Ausdruck ein.

7. Klicken Sie mehrmals auf die Schaltfläche, während Sie die ALT-TASTE gedrückt halten, um die Tabelle zu füllen.

    Die Zeiten werden in Millisekunden angezeigt.
  
    ![Datentabelle, die die Ergebnisse der Übersetzung für „Hello World“ in Französisch und Deutsch anzeigt Es kommt vor, dass die Französischübersetzung schneller als die Deutschübersetzung ist, manchmal ist es aber genau umgekehrt.](media/function-concurrent/race-condition.png) 

    In einigen Fällen ist die Französischübersetzung schneller als die Deutschübersetzung, manchmal ist es aber genau umgekehrt. Beide beginnen zur selben Zeit, jedoch wird aus unterschiedlichen Gründen (wie Netzwerklatenz und serverseitiger Verarbeitung) eine Übersetzung noch vor der anderen zurückgegeben.

    Es tritt eine [Racebedingung](https://en.wikipedia.org/wiki/Race_condition) auf, wenn die App davon abhängig ist, dass eine Übersetzung zuerst beendet wird. Glücklicherweise kennzeichnet PowerApps die meisten Zeitabhängigkeiten, die erkannt wurden.
