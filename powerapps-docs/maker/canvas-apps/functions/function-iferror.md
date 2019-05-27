---
title: IfError-Funktion | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die IfError-Funktion in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 03/21/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 63a837eff2944569f5f66223690b11ddcfd399f6
ms.sourcegitcommit: aa9f78c304fe46922aecfe3b3fadb6bda72dfb23
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66215922"
---
# <a name="iferror-function-in-powerapps"></a>IfError-Funktion in PowerApps

Erkennt Fehler und stellt einen Alternativwert bereit oder führt eine Aktion aus.

## <a name="description"></a>Beschreibung

> [!NOTE]
> Diese Funktion ist Teil eines experimentellen Features, das möglicherweise in Zukunft überarbeitet wird. Das Verhalten, das in diesem Thema wird beschrieben, ist nur verfügbar, wenn die *fehlerverwaltung auf Formelebene* Funktion aktiviert ist. Diese Einstellung auf app-Ebene ist standardmäßig deaktiviert. Um dieses Feature zu aktivieren, öffnen Sie die *Datei* Registerkarte *Anwendungseinstellungen* im linken Menü, und wählen Sie dann *experimentelle Features*. Wir sind sehr an Ihrem Feedback interessiert und würden uns freuen, wenn Sie uns in den [PowerApps-Communityforen](https://powerusers.microsoft.com/t5/Expressions-and-Formulas/bd-p/How-To) Ihre Meinung mitteilen würden.

Die **IfError** Funktion testet eine oder mehrere Werte aus, bis er ein Fehlerergebnis findet. Wenn die Funktion einen Fehler findet, gibt die Funktion einen entsprechenden Wert an. Andernfalls gibt die Funktion einen Standardwert zurück. In beiden Fällen kann die Funktion eine Zeichenfolge, die anzeigen, eine auszuwertende Formel oder eine andere Form des Ergebnisses zurück. Die **IfError** Funktion ähnelt der **Wenn** Funktion: **IfError** Tests bei Fehlern während **Wenn** wird getestet, ob **"true"** .

Verwendung **IfError** um Fehlerwerte durch gültige Werte zu ersetzen. Verwenden Sie diese Funktion z. B., wenn Benutzereingaben in einer Division durch Null führen kann. Erstellen Sie eine Formel, um das Ergebnis aus, ersetzen Sie dies durch eine 0 oder einen anderen Wert, der für Ihre app geeignet ist, sodass nachfolgende Berechnungen fortgesetzt werden können. Die Formel kann so einfach wie in diesem Beispiel werden:

```powerapps-dot
IfError( 1/x, 0 )
```

Wenn der Wert des **x** ist nicht 0 (null), die Formel gibt **1 / x**. Andernfalls **1 / x** einen Fehler erzeugt, und die Formel gibt 0 zurück, stattdessen.

Verwendung **IfError** in [verhaltensformeln](../working-with-formulas-in-depth.md) , führen Sie eine Aktion und überprüfen Sie vor dem Ausführen weiterer Aktionen, wie dieses Muster für einen Fehler:

```powerapps-dot
IfError(
    Patch( DS1, ... ), Notify( "problem in the first action" ),
    Patch( DS2, ... ), Notify( "problem in the second action" )
)
```

Wenn der erste Patch, ein Problem, das das erste auftritt **benachrichtigen** ausgeführt wird, ohne weitere Verarbeitung tritt ein, und der zweite Patch nicht ausgeführt werden. Der zweite Patch ausgeführt wird, wenn der erste Patch erfolgreich ist, und, falls er auf ein Problem, das zweite trifft **benachrichtigen** ausgeführt wird.

Wenn die Formel keine Fehler zu finden und Sie, das optionale angegeben haben *Standardergebnis* Argument die Formel gibt den Wert, den Sie für dieses Argument angegeben. Wenn die Formel keine Fehler finden, und dies nicht getan haben Sie dieses Argument angegeben, wird die Formel gibt den letzten *Wert* Argument ausgewertet.

## <a name="syntax"></a>Syntax

**IfError**( *Value1*, *ausweichformel1* [, *Value2*, *ausweichformel2*,... [, *Standardergebnis* ]])

* *Werte* : erforderlich. Ein oder mehrere Formeln, die auf einen Fehlerwert geprüft werden.
* *Ausweichformel(n)* : erforderlich. Die auszuwertenden Formeln und zurückzugebenden Werte, wenn der Abgleich *Wert* Argumente hat einen Fehler zurückgegeben.
* *DefaultResult*: Optional.  Die Formeln zu ermitteln, ob die Formel keine Fehler findet.

## <a name="examples"></a>Beispiele

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **IfError( 1, 2 )** |Das erste Argument ist ein Fehler nicht. Die Funktion weist keine weiteren Fehler überprüfen und kein Standardwert, der Wert zurückgegeben. Die Funktion gibt den letzten *Wert* Argument ausgewertet.   | 1 |
| **IfError( 1/0, 2 )** | Das erste Argument gibt einen Fehlerwert (aufgrund der Division durch null) zurück. Die Funktion ergibt das zweite Argument und gibt ihn als das Ergebnis zurück. | 2 |
| **IfError( 1/0, Notify( "There was an internal problem", NotificationType.Error ) )** | Das erste Argument gibt einen Fehlerwert (aufgrund der Division durch null) zurück. Die Funktion ergibt das zweite Argument und zeigt eine Meldung an den Benutzer. Der Rückgabewert von **IfError** ist der Rückgabewert von **Notify** und wird in denselben Typ wie das erste Argument für **IfError** (eine Zahl) umgewandelt. | 1 |
| **IfError( 1, 2, 3, 4, 5 )** | Das erste Argument ist keinen Fehler aus, damit die Bewertung der Funktion nicht, dass das Argument fallback entsprechende. Das dritte Argument ist ein Fehler, nicht, damit die Bewertung der Funktion nicht, dass das Argument fallback entsprechende. Das fünfte Argument hat keine entsprechende Fallback und wird standardmäßig das Ergebnis. Die Funktion gibt das Ergebnis, da die Formel keine Fehler enthält. | 5 |

### <a name="step-by-step"></a>Schritt für Schritt

1. Fügen Sie ein **[Texteingabe](../controls/control-text-input.md)**-Steuerelement hinzu, und nennen Sie es **TextEingabe1**, wenn es nicht standardmäßig so benannt ist.

2. Fügen Sie ein **[Label](../controls/control-text-box.md)**-Steuerelement hinzu, und nennen Sie es **Label1**, wenn es nicht standardmäßig so benannt ist.

3. Legen Sie für die **Text**-Eigenschaft von **Label1** die folgende Formel fest:

    **IfError( Value( TextEingabe1.Text ), -1 )**

4. Geben Sie in **TextEingabe1** die Zeichenfolge **1234** ein.  

    Für Label1 wird der Wert **1234** angezeigt, da es sich um eine gültige Eingabe für die Value-Funktion handelt.

5. Geben Sie in **TextEingabe1** die Zeichenfolge **ToInfinity** ein.

    Für Label1 wird der Wert **-1** angezeigt, da es sich nicht um eine gültige Eingabe für die Value-Funktion handelt.  Wenn die Value-Funktion nicht von IfError umschlossen wäre, würde für das Label kein Wert angezeigt werden, da der Fehlerwert als *leerer Wert* interpretiert würde. 

