---
title: Funktion „Set“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Set-Funktion in powerapps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/29/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6c0e4cfc1a180e183f29392181cd7699b6cb9242
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730210"
---
# <a name="set-function-in-power-apps"></a>Set-Funktion in powerapps
Legt den Wert einer globalen Variablen fest.

## <a name="overview"></a>Übersicht
Verwenden Sie die **Set**-Funktion zum Festlegen des Werts einer globalen Variablen, die vorübergehend eine Information enthält, z.B. wie oft ein Benutzer auf eine Schaltfläche geklickt hat oder das Ergebnis eines Datenvorgangs.  

Globale Variablen sind in Ihrer App auf allen Bildschirmen verfügbar. Sie stellen den einfachsten Typ von Variablen dar und erfüllen die Anforderungen in den meisten Situationen. Es gibt auch Kontextvariablen, deren Gültigkeitsbereich auf einen einzigen Bildschirm beschränkt ist, sowie Sammlungen, die Änderungen von Tabellen auf Zeilenebene ermöglichen. Weitere Informationen zu diesen anderen Optionen finden Sie Untergrund Legendes zu [Variablen](../working-with-variables.md).

Powerapps basieren auf Formeln, die automatisch neu berechnet werden, wenn der Benutzer mit einer APP interagiert. Alle Formeln, die von einer Variablen abhängen, werden automatisch aktualisiert, wenn Sie sich ändert. Die Variable wird jedoch nicht automatisch aktualisiert, wenn sich der Wert der Formel ändert, die in der **Set** -Funktion verwendet wird. Dies erfordert, dass der APP-Hersteller die Variable manuell aktualisiert, was für andere fehleranfällig und für andere schwer zu verstehen ist. Bevor Sie eine Variable verwenden, lesen Sie Untergrund Legendes zu [Variablen](../working-with-variables.md).

## <a name="description"></a>Beschreibung
Globale Variablen werden mithilfe der **Set**-Funktion implizit erstellt. Eine explizite Deklaration ist nicht erforderlich. Wenn Sie alle **Set** -Funktionen für eine globale Variable entfernen, wird diese globale Variable nicht mehr vorhanden sein. Um eine Variable zu löschen, legen Sie Ihren Wert auf das Ergebnis der [ **leeren** Funktion](function-isblank-isempty.md)fest.

Sie können die Werte, Definitionen und Verwendungsmöglichkeiten der Variablen mit der Ansicht Variablen im Menü **Datei** in Power apps Studio sehen.

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
| **Set(&nbsp;Person,&nbsp;{&nbsp;Name:&nbsp;"Milton", Address:&nbsp;"1&nbsp;Main&nbsp;St"&nbsp;} )** |Erstellt oder ändert die globale Variable **Person** und legt deren Wert auf einen Datensatz fest. Der Datensatz enthält zwei Spalten mit den Namen **Name** und **Address**. Der Wert der **Name**-Spalte ist **Milton**, und der Wert der **Address**-Spalte ist **1 Main St**. |**Person** hat den Wert des Datensatzes **{&nbsp;Name:&nbsp;"Milton", Address:&nbsp;"1&nbsp;Main&nbsp;St"&nbsp;}** .<br><br>Verweisen Sie mit dem Namen **Person** auf den kompletten Datensatz, oder verweisen Sie auf eine einzelne Spalte dieses Datensatzes mit **Person.Name** oder **Person.Address**. |
| **Set(&nbsp;Person, Patch(&nbsp;Person,&nbsp;{Address:&nbsp;"2&nbsp;Main&nbsp;St"&nbsp;}&nbsp;)&nbsp;)** |Arbeitet mit der **[Patch](function-patch.md)** -Funktion zusammen, um die globale Variable **Person** durch Festlegen des Werts der Spalte **Address** auf **2 Main St** zu aktualisieren. |**Person** hat nun den Wert des Datensatzes **{&nbsp;Name:&nbsp;"Milton", Address:&nbsp;"2&nbsp;Main&nbsp;St"&nbsp;}** . |

