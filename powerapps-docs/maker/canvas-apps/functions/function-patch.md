---
title: Funktion „Patch“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Patch-Funktion in powerapps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/16/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 62215281afb650ba230d1ade77a80db6eac5dbd7
ms.sourcegitcommit: aca415459448812e82a9db9151b9123c1ad01041
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79486424"
ms.PowerAppsDecimalTransform: true
---
# <a name="patch-function-in-power-apps"></a>Funktion "Patch" in powerapps
Ändert oder erstellt einen oder mehrere [Datensätze](../working-with-tables.md#records) in einer [Datenquelle](../working-with-data-sources.md) oder verbindet Datensätze außerhalb einer Datenquelle.

Verwenden Sie die **Patch** -Funktion, um Datensätze in komplexen Situationen zu ändern. Beispielsweise, wenn Sie Updates ausführen, die keine Benutzerinteraktion erfordern, oder Formulare verwenden, die mehrere Bildschirme umfassen.

Wenn Sie Datensätze in einer Datenquelle leichter für einfache Änderungen aktualisieren möchten, verwenden Sie stattdessen das **Formular bearbeiten** -Steuerelement. Wenn Sie ein **Bearbeitungsformular**-Steuerelement hinzufügen, geben Sie Benutzern ein Formular an die Hand, das sie ausfüllen und dessen Änderungen sie dann in einer Datenquelle speichern können. Weitere Informationen finden Sie unter [Grundlegendes zu Datenformularen](../working-with-forms.md).

## <a name="overview"></a>Übersicht
Verwenden Sie die **Patch**-Funktion, um einen oder mehrere Datensätze für die Datenquelle zu ändern.  Die Werte bestimmter [Felder](../working-with-tables.md#elements-of-a-table) lassen sich ohne Auswirkungen auf andere Eigenschaften ändern. Beispielsweise ändert diese Formel die Telefonnummer für einen Kunden mit dem Namen Contoso:

`Patch( Customers; First( Filter( Customers; Name = "Contoso" ) ); { Phone: "1-212-555-1234" } )`

Verwenden Sie die Funktion **Patch** mit der **[Default](function-defaults.md)** -Funktion, um Einträge zu erstellen. Verwenden Sie dieses Verhalten zum Erstellen eines [kombinierten Bildschirms](../working-with-data-sources.md) für die Erstellung und Bearbeitung von Datensätzen. Beispielsweise erstellt diese Formel einen Datensatz für einen Kunden mit dem Namen Contoso:

`Patch( Customers; Defaults( Customers ); { Name: "Contoso" } )`

Auch wenn Sie nicht mit einer Datenquelle arbeiten, können Sie die **Patch**-Funktion zum Zusammenführen von zwei oder mehr Datensätzen nutzen. Diese Formel führt beispielsweise zwei Datensätze zu einem zusammen, der sowohl die Telefonnummer als auch den Standort von Contoso angibt:

`Patch( { Name: "Contoso"; Phone: "1-212-555-1234" }; { Name: "Contoso"; Location: "Midtown"  } )`

## <a name="description"></a>Beschreibung
### <a name="modify-or-create-a-record-in-a-data-source"></a>Ändern oder Erstellen eines Datensatzes in einer Datenquelle
Um diese Funktion mit einer Datenquelle zu verwenden, geben Sie zunächst die Datenquelle an und anschließend einen Basisdatensatz:

* Um einen Datensatz zu ändern, muss der Basisdatensatz aus einer Datenquelle stammen.  Der Basisdatensatz kann aus der **[Items](../controls/properties-core.md)** -Eigenschaft eines Katalogs stammen, in einer [Kontextvariablen](../working-with-variables.md#use-a-context-variable) platziert worden sein oder anderer Herkunft sein. Sie können den Basisdaten Satz jedoch zurück zur Datenquelle zurückverfolgen.  Dies ist wichtig, da der Datensatz zusätzliche Informationen enthält, anhand derer Sie ihn wiederfinden können, um ihn zu ändern.  
* Zum Erstellen eines Datensatzes verwenden Sie die **[Defaults](function-defaults.md)** -Funktion und erstellen einen Basisdatensatz mit Standardwerten.  

Geben Sie anschließend einen oder mehrere Änderungsdatensätze mit jeweils neuen Eigenschaftswerten an, die die Eigenschaftswerte im Basisdatensatz überschreiben. Änderungsdatensätze werden nacheinander vom Anfang bis zum Ende der Argumenteliste verarbeitet, wobei spätere Eigenschaftswerte frühere Versionen überschreiben.

Der Rückgabewert der **Patch**-Funktion ist der Datensatz, den Sie erstellt oder geändert haben.  Wenn Sie einen Datensatz erstellt haben, kann der Rückgabewert Eigenschaften enthalten, die die Datenquelle automatisch generiert hat. Der Rückgabewert stellt jedoch keinen Wert für Felder einer verknüpften Entität bereit.  

Beispielsweise verwenden Sie `Set(MyAccount; Patch(Accounts; First(Account); 'Account Name': "Example name");;` und dann `MyAccount.'Primary Contact'.'Full Name'`. In diesem Fall können Sie keinen vollständigen Namen erhalten. Verwenden Sie stattdessen zum Zugreifen auf die Felder einer verknüpften Entität eine separate Suche, z. b.:

```powerapps-comma
LookUp(Accounts; Account = MyAccount.Account).'Primary Contact'.'Full Name'
```

Wenn Sie eine Datenquelle aktualisieren, können Probleme auftreten. Verwenden Sie die **[Errors](function-errors.md)** -Funktion,um Schwierigkeiten zu identifizieren und zu untersuchen, wie unter [Working with Data Sources (Arbeiten mit Datenquellen)](../working-with-data-sources.md) beschrieben.

Verwandte Funktionen enthalten die **[Update](function-update-updateif.md)** -Funktion, um einen vollständigen Datensatz zu ersetzen, und die **[Collect](function-clear-collect-clearcollect.md)** -Funktion, um einen Datensatz zu erstellen.  Verwenden Sie die **[updateif](function-update-updateif.md)** -Funktion, um bestimmte Eigenschaften mehrerer Datensätze basierend auf einer Bedingung zu ändern.

### <a name="modify-or-create-a-set-of-records-in-a-data-source"></a>Ändern oder Erstellen einer Gruppe von Datensätzen in einer Datenquelle
**Patch** kann außerdem zum Erstellen oder Ändern mehrerer Datensätze mit einem einzigen Aufruf verwendet werden.

Anstelle der Übergabe eines einzelnen Basisdatensatzes kann eine Tabelle mit Basisdatensätze im zweiten Argument angegeben werden.  Änderungsdatensätze werden ebenfalls in einer Tabelle bereitgestellt, wobei jedem Änderungsdatensatz direkt ein Datenbank-Datensatz entspricht.  Die Anzahl der Datensätze in jeder Änderungstabelle muss mit der Anzahl der Datensätze in der Basistabelle identisch sein.

Wenn Sie die Funktion **Patch** in dieser Weise verwenden, ist der Rückgabewert ebenfalls eine Tabelle, in der jedem Basisdatensatz jeweils direkt ein Änderungsdatensatz entspricht.

### <a name="merge-records-outside-of-a-data-source"></a>Zusammenführen von Datensätzen außerhalb einer Datenquelle
Geben Sie zwei oder mehr Datensätze an, die Sie zusammenführen möchten. Datensätze werden in der Reihenfolge vom Anfang der Argumentliste bis zum Ende verarbeitet, wobei spätere Eigenschaftswerte frühere Werte überschreiben.

**Patch** gibt den zusammengeführten Datensatz zurück. Dessen Argumente oder Datensätze werden in keiner Datenquellen geändert.

## <a name="syntax"></a>Syntax
#### <a name="modify-or-create-a-record-in-a-data-source"></a>Ändern oder Erstellen eines Datensatzes in einer Datenquelle
**Patch**( *DataSource*; *BaseRecord*; *ChangeRecord1* [; *ChangeRecord2*; … ])

* *DataSource*: erforderlich. Die Datenquelle, die den zu ändernden Datensatz enthält oder für die Sie einen Datensatz erstellen möchten.
* *BaseRecord*: erforderlich. Der zu ändernde oder zu erstellende Datensatz.  Wenn der Datensatz aus einer Datenquelle stammt, wird der Datensatz gefunden und geändert. Wenn das Ergebnis der **[Defaults](function-defaults.md)** -Funktion verwendet wird, wird ein Datensatz erstellt.
* *ChangeRecord(s)* : erforderlich.  Mindestens ein Datensatz, der Eigenschaften enthält, die für jeden Datensatz im *BaseRecord* geändert werden sollen.  Änderungsdatensätze werden nacheinander vom Anfang bis zum Ende der Argumenteliste verarbeitet, wobei spätere Eigenschaftswerte frühere Versionen überschreiben.

#### <a name="modify-or-create-a-set-of-records-in-a-data-source"></a>Ändern oder Erstellen einer Gruppe von Datensätzen in einer Datenquelle
**Patch**( *DataSource*; *baserecordstable*; *ChangeRecordTable1* [; *ChangeRecordTable2*;... ] )

* *DataSource*: erforderlich. Die Datenquelle mit den zu ändernden Datensätzen oder für die Sie Datensätze erstellen möchten.
* *BaseRecordTable*: erforderlich. Eine Tabelle mit zu ändernden oder zu erstellenden Datensätzen.  Wenn der Datensatz aus einer Datenquelle stammt, wird der Datensatz gefunden und geändert. Wenn das Ergebnis der **[Defaults](function-defaults.md)** -Funktion verwendet wird, wird ein Datensatz erstellt.
* *ChangeRecordTable(s)* : erforderlich.  Mindestens eine Tabelle von Datensätzen mit Eigenschaften, die für jeden Datensatz von *BaseRecordTable* geändert werden sollen.  Änderungsdatensätze werden nacheinander vom Anfang bis zum Ende der Argumenteliste verarbeitet, wobei spätere Eigenschaftswerte frühere Versionen überschreiben.

#### <a name="merge-records"></a>Zusammenführen von Datensätzen
**Patch**( *Record1*; *Record2* [; …] )

* *Datensatz(-sätze)* : erforderlich.  Mindestens zwei Datensätze, die Sie zusammenführen möchten. Datensätze werden nacheinander vom Anfang bis zum Ende der Argumenteliste verarbeitet, wobei spätere Eigenschaftswerte frühere Versionen überschreiben.

## <a name="examples"></a>Beispiele
#### <a name="modify-or-create-a-record-in-a-data-source"></a>Ändern oder Erstellen eines Datensatzes (in einer Datenquelle)
In diesen Beispielen ändern oder erstellen Sie einen Datensatz in einer Datenquelle mit dem Namen **icecream**, die die Daten in dieser [Tabelle](../working-with-tables.md) enthält und automatisch die Werte in der [Spalte](../working-with-tables.md#columns) **ID** generiert:

![](media/function-patch/icecream.png)

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Patch(&nbsp;IceCream;<br>First( Filter( IceCream; Flavor = "Chocolate" ) ); {&nbsp;Quantity:&nbsp;400&nbsp;} )** |Ändert einen Datensatz in der **IceCream**-Datenquelle:<ul><li> Die **ID**-Spalte des zu ändernden Datensatzes enthält den Wert **1**. (Der **Chocolate**-Datensatz weist diese ID auf.)</li><li>Der Wert in der **Quantity**-Spalte ändert sich zu **400**. |{&nbsp;ID:&nbsp;1, Flavor:&nbsp;"Chocolate", Quantity:&nbsp;400 }<br><br>Der Eintrag **Chocolate** in der **IceCream**-Datenquelle wurde geändert. |
| **Patch (icecream; Standardwerte (&nbsp;icecream); {&nbsp;Flavor:&nbsp;"Erdbeer"&nbsp;}&nbsp;)** |Erstellt einen Datensatz in der **IceCream**-Datenquelle:<ul><li>Die **ID**-Spalte enthält den Wert **3**, den die Datenquelle automatisch generiert.</li><li>Die Spalte **Quantity** enthält **0**, was dem Standardwert für diese Spalte in der **IceCream**-Datenquelle entspricht,wie von der **[Defaults](function-defaults.md)** -Funktion angegeben.<li>Die Spalte **Flavor** enthält den Wert **Strawberry**.</li> |{ID:&nbsp;3, Flavor:&nbsp;"Erdbeer", Menge:&nbsp;0&nbsp;}<br><br>Der Eintrag **Strawberry** in der **IceCream**-Datenquelle wurde erstellt. |

Nachdem die oben genannten Formeln ausgewertet wurden, endet die Datenquelle mit den folgenden Werten:

![](media/function-patch/icecream-after.png)

#### <a name="merge-records-outside-of-a-data-source"></a>Zusammenführen von Datensätzen (außerhalb einer Datenquelle)

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Patch(&nbsp;{&nbsp;Name:&nbsp;"James";&nbsp;Score:&nbsp;90&nbsp;}; {&nbsp;Name:&nbsp;"Jim";&nbsp;Passed:&nbsp;true&nbsp;} )** |Verbindet zwei Datensätze außerhalb einer Datenquelle:<br><ul><li>Die Werte in der Spalte **Name** jedes Datensatzes stimmen nicht überein. Das Ergebnis enthält den Wert (**Jim**) im Datensatz, der dem Ende der Argumentliste näher ist, anstelle des Werts (**James**) im Datensatz, der näher am Anfang ist.</li><li>Der erste Datensatz enthält eine Spalte (**Score**), die im zweiten Datensatz nicht vorhanden ist. Das Ergebnis enthält diese Spalte mit dem Wert (**90**).</li><li>Der zweite Datensatz enthält eine Spalte (**Passed**), die im ersten Datensatz nicht vorhanden ist. Das Ergebnis enthält diese Spalte mit dem Wert (**TRUE**). |{&nbsp;Name:&nbsp;"Jim", Score:&nbsp;90, Passed:&nbsp;true&nbsp;} |

