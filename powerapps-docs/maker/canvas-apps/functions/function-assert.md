---
title: Funktion „Assert“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax zur Funktion „Assert“ in Power Apps Test Studio
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/19/2018
ms.author: aheneay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e4319c3685db46f4277109e385a640e744402edc
ms.sourcegitcommit: 6b2961308c41867756ecdd55f55eccbebf70f7f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "76541288"
---
# <a name="assert-function-in-power-apps-test-studio"></a>Funktion „Assert“ in Power Apps Test Studio

Eine Assertion ist eine Bedingung oder ein Ausdruck, der die Ergebnisse TRUE oder FALSE für einen Test zurückgibt. Wenn der Ausdruck FALSE zurückgibt, schlägt der Testfall fehl. Assertionen werden verwendet, um das erwartete Ergebnis eines Tests oder Testschritts mit dem tatsächlichen Ergebnis abzugleichen und um einen Fehler für den Test auszulösen, wenn für die Bedingung FALSE zurückgegeben wird. Assertionen können verwendet werden, um den Zustand der Steuerelemente wie Bezeichnungswerte, Listenfeldauswahl und andere Steuerelementeigenschaften in Ihrer App zu überprüfen.  

Assertionsmeldungen für sowohl erfolgreiche als auch fehlgeschlagene Assertionen sind auch in einer „Traces“-Tabelle im Datensatz „TestCaseResult“ enthalten. 

## <a name="syntax"></a>Syntax

*Assert(Ausdruck, Meldung)*

- *Ausdruck:* erforderlich. Dies ist ein Ausdruck, der als TRUE oder FALSE ausgewertet wird.
- *Meldung:* nicht erforderlich. Dies ist eine Meldung, die den Assertionsfehler beschreibt. 


## <a name="examples"></a>Beispiele

```Assert(lblResult.Text = "Success", "lblResult value Expected : Success , Actual : " & lblResult.Text)```<br>
```Assert(ListBox1.Selected.Value = "Success", "ListBox1 selection Expected : Success,  Actual : " & ListBox1.Selected.Value)```<br>
```Assert(kudosAfterTest = kudosBeforeTest + 1, "Kudos count. Expected : " & kudosBeforeTest + 1  & " Actual :" & kudosAfterTest)```

### <a name="see-also"></a>Siehe auch

[Test Studio: Übersicht](../test-studio.md) <br>
[Arbeiten mit Test Studio](../working-with-test-studio.md)
