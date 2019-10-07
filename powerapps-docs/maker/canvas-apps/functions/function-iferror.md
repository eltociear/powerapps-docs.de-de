---
title: IfError-Funktion | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die IfError-Funktion in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/21/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 992ff4ccfae533908acac96efaa117a726198334
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71984715"
---
# <a name="iferror-function-in-powerapps"></a>IfError-Funktion in PowerApps

Erkennt Fehler und stellt einen Alternativwert bereit oder führt eine Aktion aus.

## <a name="description"></a>Beschreibung

> [!NOTE]
> Diese Funktion ist Teil eines experimentellen Features, das möglicherweise in Zukunft überarbeitet wird. Das Verhalten, das in diesem Thema beschrieben wird, ist nur verfügbar, wenn das Feature zur *Fehler Verwaltung auf Formel Ebene* aktiviert ist. Diese Einstellung auf App-Ebene ist standardmäßig deaktiviert. Um diese Funktion zu aktivieren, öffnen Sie die Registerkarte *Datei* , wählen Sie im Menü auf der linken Seite *App-Einstellungen* aus, und wählen Sie dann *experimentelle Features*aus. Wir sind sehr an Ihrem Feedback interessiert und würden uns freuen, wenn Sie uns in den [PowerApps-Communityforen](https://powerusers.microsoft.com/t5/Expressions-and-Formulas/bd-p/How-To) Ihre Meinung mitteilen würden.

Die **IFERROR** -Funktion testet mindestens einen Wert, bis ein Fehler Ergebnis gefunden wird. Wenn die Funktion einen Fehler findet, gibt die Funktion einen entsprechenden Wert zurück. Andernfalls gibt die Funktion einen Standardwert zurück. In beiden Fällen gibt die Funktion möglicherweise eine anzuzeigende Zeichenfolge, eine auszuwertende Formel oder eine andere Form des Ergebnisses zurück. Die **IFERROR** -Funktion ähnelt der **if** -Funktion: **IFERROR** testet auf Fehler, während auf **true** **überprüft wird.**

Verwenden Sie **IFERROR** , um Fehler Werte durch gültige Werte zu ersetzen. Verwenden Sie diese Funktion z. b., wenn Benutzereingaben eine Division durch 0 (null) verursachen könnten. Erstellen Sie eine Formel, um das Ergebnis durch einen 0 oder einen anderen Wert zu ersetzen, der für Ihre APP geeignet ist, damit downstreamberechnungen fortgesetzt werden können. Die Formel kann so einfach sein wie in diesem Beispiel:

```powerapps-dot
IfError( 1/x, 0 )
```

Wenn der Wert von **x** nicht 0 (null) ist, gibt die Formel **1/x**zurück. Andernfalls erzeugt **1/x** einen Fehler, und die Formel gibt stattdessen 0 zurück.

Verwenden Sie **IFERROR** in [Verhaltens Formeln](../working-with-formulas-in-depth.md) , um eine Aktion auszuführen und auf einen Fehler zu überprüfen, bevor Sie weitere Aktionen ausführen, wie in diesem Muster:

```powerapps-dot
IfError(
    Patch( DS1, ... ), Notify( "problem in the first action" ),
    Patch( DS2, ... ), Notify( "problem in the second action" )
)
```

Wenn beim ersten Patch ein Problem auftritt, wird die erste **Benachrichtigung** ausgeführt, es erfolgt keine weitere Verarbeitung, und der zweite Patch wird nicht ausgeführt. Wenn der erste Patch erfolgreich ist, wird der zweite Patch ausgeführt, und wenn ein Problem auftritt, wird der zweite **Benachrichtigungs** Vorgang ausgeführt.

Wenn die Formel keine Fehler findet und Sie das optionale *defaultResult* -Argument angegeben haben, gibt die Formel den Wert zurück, den Sie für dieses Argument angegeben haben. Wenn die Formel keine Fehler findet und Sie dieses Argument nicht angegeben haben, gibt die Formel das zuletzt ausgewertete *Wert* Argument zurück.

## <a name="syntax"></a>Syntax

**IFERROR**( *value1*, *Fallback1* [, *value2*, *Fallback2*,... [, *DefaultResult* ]] )

* *Value (s)* : erforderlich. Ein oder mehrere Formeln, die auf einen Fehlerwert geprüft werden.
* *Ausweichformel(n)* : erforderlich. Die auszuwertenden Formeln und zurück zugebende Werte, wenn übereinstimmende *Wert* Argumente einen Fehler zurückgegeben haben.
* *DefaultResult*: Optional.  Die Formeln, die ausgewertet werden sollen, wenn die Formel keine Fehler findet.

## <a name="examples"></a>Beispiele

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **IfError( 1, 2 )** |Das erste Argument ist kein Fehler. Die Funktion hat keine weiteren Fehler, die überprüft werden können, und gibt keinen Standard Rückgabewert zurück. Die-Funktion gibt das zuletzt ausgewertete *Wert* Argument zurück.   | 1 |
| **IfError( 1/0, 2 )** | Das erste Argument gibt einen Fehlerwert zurück (aufgrund der Division durch null). Die-Funktion wertet das zweite Argument aus und gibt es als Ergebnis zurück. | 2 |
| **IfError( 1/0, Notify( "There was an internal problem", NotificationType.Error ) )** | Das erste Argument gibt einen Fehlerwert zurück (aufgrund der Division durch null). Die-Funktion wertet das zweite Argument aus und zeigt dem Benutzer eine Meldung an. Der Rückgabewert von **IfError** ist der Rückgabewert von **Notify** und wird in denselben Typ wie das erste Argument für **IfError** (eine Zahl) umgewandelt. | 1 |
| **IFERROR (1, 2, 3, 4, 5)** | Beim ersten Argument handelt es sich nicht um einen Fehler, daher wertet die Funktion das entsprechende Fallback des Arguments nicht aus. Das dritte Argument ist entweder kein Fehler, daher wertet die Funktion das entsprechende Fallback des Arguments nicht aus. Das fünfte Argument hat kein entsprechendes Fall Back und ist das Standard Ergebnis. Die Funktion gibt das Ergebnis zurück, da die Formel keine Fehler enthält. | 5 |

### <a name="step-by-step"></a>Schritt für Schritt

1. Fügen Sie ein **[Texteingabe](../controls/control-text-input.md)** -Steuerelement hinzu, und nennen Sie es **TextEingabe1**, wenn es nicht standardmäßig so benannt ist.

2. Fügen Sie ein **[Label](../controls/control-text-box.md)** -Steuerelement hinzu, und nennen Sie es **Label1**, wenn es nicht standardmäßig so benannt ist.

3. Legen Sie für die **Text**-Eigenschaft von **Label1** die folgende Formel fest:

    **IfError( Value( TextEingabe1.Text ), -1 )**

4. Geben Sie in **TextEingabe1** die Zeichenfolge **1234** ein.  

    Für Label1 wird der Wert **1234** angezeigt, da es sich um eine gültige Eingabe für die Value-Funktion handelt.

5. Geben Sie in **TextEingabe1** die Zeichenfolge **ToInfinity** ein.

    Für Label1 wird der Wert **-1** angezeigt, da es sich nicht um eine gültige Eingabe für die Value-Funktion handelt.  Wenn die Value-Funktion nicht von IfError umschlossen wäre, würde für das Label kein Wert angezeigt werden, da der Fehlerwert als *leerer Wert* interpretiert würde. 

