---
title: Funktion „Trace“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax zur Funktion „Trace“ in Power Apps Test Studio
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
ms.openlocfilehash: 927b8dae59a4dc6fc55d74c1998b0d434eb8356c
ms.sourcegitcommit: d500f44e77747a3244b6691ad9b3528e131dbfa5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2020
ms.locfileid: "79133586"
---
# <a name="trace-function"></a>Funktion „Trace“ 

Die Funktion „Trace“ stellt in Test Studio einen optionalen Ausdruck dar, der verwendet werden kann, um über das Ereignis **OnTestCaseComplete** zusätzliche Informationen zu Ihren Testergebnissen bereitzustellen. Meldungen zu „Trace“-Ereignissen sowie sämtliche Meldungen zu erfolgreichen und fehlgeschlagenen Assertionen sind in der Tabelle „Traces“ im Datensatz „TestCaseResult“ enthalten. Die Tabelle „Traces“ verfügt über zwei Eigenschaften: „Message“ und „Timestamp“. 

Ablauf Verfolgungs Meldungen können auch in der APP definiert werden. Diese können im powerapps-Monitor Tool zusammen mit anderen APP-Aktivitäten angezeigt werden, um das Debuggen oder identifizieren von Problemen mit Diagnoseinformationen in Echtzeit für Ihre APP zu unterstützen. Wenn Sie für Ihre App das Senden von Telemetriedaten an Azure Application Insights freigegeben haben, kann die Funktion „Trace“ auch verwendet werden, um benutzerdefinierte Ereignis- oder Diagnoseinformationen an Ihre Application Insights-Ressource zu senden. Sie können diese Daten in Application Insights überprüfen, um Probleme zu diagnostizieren oder um Informationen zur Nutzung Ihrer Apps und Features zu erhalten. Die in den Tests verwendeten „Trace“-Informationen werden ebenfalls in Application Insights gespeichert. Die Test Ablauf Verfolgungs Informationen sind im Überwachungs Tool nicht verfügbar, da der Monitor mit der App verbunden ist, wenn er von der Canvas Studio wiedergegeben wird. 

## <a name="syntax"></a>Syntax

*Ablauf Verfolgung (Nachricht, trace_severity custom_record)*

- *Message* – Erforderlich. Dies sind die nachzuverfolgenden Informationen. In Tests erstellt dieses Element einen Eintrag in der Tabelle „Traces“ im Datensatz „TestCaseResult“. 
- *Trace_severity* : optional. Dies entspricht dem Schweregrad des in Application Insights aufgezeichneten Trace-Elements. Optionen sind "traceseverity. Information", "traceseverity. Warning" oder "traceseverity. Error". 
- *custom_record:* optional. Dies ist ein Datensatz mit benutzerdefinierten Daten, die in Application Insights gespeichert werden. 
  

### <a name="see-also"></a>Siehe auch

[Test Studio: Übersicht](../test-studio.md) <br>
[Arbeiten mit Test Studio](../working-with-test-studio.md)
