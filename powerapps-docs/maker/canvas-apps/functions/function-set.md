---
title: Funktion „Set“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Set-Funktion in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/29/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 3292d03a55fe6296b8efdf2377efde5f2b4ad36e
ms.sourcegitcommit: 676cfa415f67e2e8fcfcf30fab83fc118a6f3210
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2019
ms.locfileid: "57800489"
---
# <a name="set-function-in-powerapps"></a>Set-Funktion in PowerApps
Legt den Wert einer globalen Variablen fest.

## <a name="overview"></a>Übersicht
Verwenden Sie die **Set**-Funktion zum Festlegen des Werts einer globalen Variablen, die vorübergehend eine Information enthält, z.B. wie oft ein Benutzer auf eine Schaltfläche geklickt hat oder das Ergebnis eines Datenvorgangs.  

Globale Variablen sind in Ihrer App auf allen Bildschirmen verfügbar. Sie stellen den einfachsten Typ von Variablen dar und erfüllen die Anforderungen in den meisten Situationen. Es gibt auch Kontextvariablen, deren Gültigkeitsbereich auf einen einzigen Bildschirm beschränkt ist, sowie Sammlungen, die Änderungen von Tabellen auf Zeilenebene ermöglichen. Weitere Informationen zu diesen anderen Optionen finden Sie in [Grundlegendes zu Variablen](../working-with-variables.md).

PowerApps basiert auf Formeln, die automatisch neu berechnet werden, während der Benutzer mit einer App interagiert. Alle Formeln, die für eine Variable abhängig sind, werden automatisch aktualisiert, wenn sich diese ändern. Aber die Variable wird nicht automatisch aktualisiert, wenn der Wert der Formel in der **festgelegt** Änderungen funktionieren. Dies erfordert die app-Ersteller so aktualisieren Sie manuell die Variable, die fehleranfällig und für andere Benutzer zu schwieriger sein kann. Bevor Sie eine Variable verwenden, lesen Sie [Grundlegendes zu Variablen](../working-with-variables.md).

## <a name="description"></a>Beschreibung
Globale Variablen werden mithilfe der **Set**-Funktion implizit erstellt. Es ist keine explizite Deklaration erforderlich. Wenn Sie alle Entfernen der **festgelegt** Funktionen für eine globale Variable, die globale Variable wird nicht mehr vorhanden. Um eine Variable zu löschen, legen Sie seinen Wert auf das Ergebnis der [ **leere** Funktion](function-isblank-isempty.md).

Sehen Sie Ihre Variablen Werte, Definitionen und verwendet, mit der Ansicht "Variablen" unter der **Datei** in PowerApps Studio im Menü.

Wie in den Beispielen weiter unten in diesem Thema gezeigt, können globale Variablen verschiedene Arten von Informationen enthalten, u.a. folgende:

* einen einzelnen Wert
* einen Datensatz
* eine Tabelle
* einen Objektverweis
* jedes Ergebnis einer Formel

Eine globale Variable verfügt über ihren Wert, bis die App geschlossen wird.  Sobald die App geschlossen wird, geht der Wert der globalen Variablen verloren; er muss neu erstellt werden, wenn die App wieder geladen wird.

Globale Variablen können nicht denselben Namen wie eine vorhandene Sammlung oder ein vorhandenes Steuerelement aufweisen.  Sie kann jedoch denselben Namen wie eine Kontextvariable besitzen.  Verwenden Sie den [Operator zur Mehrdeutigkeitsvermeidung](operators.md#disambiguation-operator), um zu zwischen beiden zu unterscheiden.

**Set** weist keinen Rückgabewert auf; Sie können die Funktion nur innerhalb einer [Verhaltensformel](../working-with-formulas-in-depth.md) verwenden.

## <a name="syntax"></a>Syntax
**Set**( *VariableName*, *Value* )

* *VariableName*: Erforderlich.  Der Name der zu erstellenden oder zu aktualisierenden globalen Variablen.
* *Value*: Erforderlich.  Der der Kontextvariablen zuzuweisende Wert

## <a name="examples"></a>Beispiele

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Set(&nbsp;Counter,&nbsp;1&nbsp;)** |Erstellt oder ändert die globale Variable **Counter** und legt deren Wert auf **1** fest. |**Counter** hat den Wert **1**. Mit dem Namen **Counter** können Sie in einer Formel in einem beliebigen Bildschirm auf diese Variable verweisen. |
| **Set(&nbsp;Counter,&nbsp;2&nbsp;)** |Legt den Wert für die globale Variable **Counter** aus dem vorherigen Beispiel auf **2** fest. |**Counter** hat den Wert **2**. |
| **Set(&nbsp;Counter,&nbsp;Counter + 1&nbsp;)** |Erhöht den Wert für die globale Variable **Counter** aus dem vorherigen Beispiel auf **3**. |**Counter** hat den Wert **3**. |
| **Set(&nbsp;Name,&nbsp;"Lily" )** |Erstellt oder ändert die globale Variable **Name** und legt deren Wert auf **Lily** fest. |**Name** weist den Wert **Lily** auf. |
| **Set(&nbsp;Person,&nbsp;{&nbsp;Name:&nbsp;"Milton", Address:&nbsp;"1&nbsp;Main&nbsp;St"&nbsp;} )** |Erstellt oder ändert die globale Variable **Person** und legt deren Wert auf einen Datensatz fest. Der Datensatz enthält zwei Spalten mit den Namen **Name** und **Address**. Der Wert der **Name**-Spalte ist **Milton**, und der Wert der **Address**-Spalte ist **1 Main St**. |**Person** hat den Wert des Datensatzes **{&nbsp;Name:&nbsp;"Milton", Address:&nbsp;"1&nbsp;Main&nbsp;St"&nbsp;}**.<br><br>Verweisen Sie mit dem Namen **Person** auf den kompletten Datensatz, oder verweisen Sie auf eine einzelne Spalte dieses Datensatzes mit **Person.Name** oder **Person.Address**. |
| **Set(&nbsp;Person, Patch(&nbsp;Person,&nbsp;{Address:&nbsp;"2&nbsp;Main&nbsp;St"&nbsp;}&nbsp;)&nbsp;)** |Arbeitet mit der **[Patch](function-patch.md)**-Funktion zusammen, um die globale Variable **Person** durch Festlegen des Werts der Spalte **Address** auf **2 Main St** zu aktualisieren. |**Person** hat nun den Wert des Datensatzes **{&nbsp;Name:&nbsp;"Milton", Address:&nbsp;"2&nbsp;Main&nbsp;St"&nbsp;}**. |

