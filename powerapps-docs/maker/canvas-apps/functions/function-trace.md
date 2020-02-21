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
ms.openlocfilehash: 23bfbb3b97764a427d5422e4ad207d4af7cc1589
ms.sourcegitcommit: 3b68c4e29be4e8f68c0bfb88abdd1bbdf0187c57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2020
ms.locfileid: "77530786"
---
# <a name="trace-function"></a>Funktion „Trace“ 

Die Funktion „Trace“ stellt in Test Studio einen optionalen Ausdruck dar, der verwendet werden kann, um über das Ereignis **OnTestCaseComplete** zusätzliche Informationen zu Ihren Testergebnissen bereitzustellen. Meldungen zu „Trace“-Ereignissen sowie sämtliche Meldungen zu erfolgreichen und fehlgeschlagenen Assertionen sind in der Tabelle „Traces“ im Datensatz „TestCaseResult“ enthalten. Die Tabelle „Traces“ verfügt über zwei Eigenschaften: „Message“ und „Timestamp“. 

Ablauf Verfolgungs Meldungen können auch in der APP definiert werden. Diese können im powerapps-Monitor Tool zusammen mit anderen APP-Aktivitäten angezeigt werden, um das Debuggen oder identifizieren von Problemen mit Diagnoseinformationen in Echtzeit für Ihre APP zu unterstützen. Wenn Sie für Ihre App das Senden von Telemetriedaten an Azure Application Insights freigegeben haben, kann die Funktion „Trace“ auch verwendet werden, um benutzerdefinierte Ereignis- oder Diagnoseinformationen an Ihre Application Insights-Ressource zu senden. Sie können diese Daten in Application Insights überprüfen, um Probleme zu diagnostizieren oder um Informationen zur Nutzung Ihrer Apps und Features zu erhalten. Die in den Tests verwendeten „Trace“-Informationen werden ebenfalls in Application Insights gespeichert. Die Test Ablauf Verfolgungs Informationen sind im Überwachungs Tool nicht verfügbar, da der Monitor mit der App verbunden ist, wenn er von der Canvas Studio wiedergegeben wird. 

## <a name="syntax"></a>Syntax

*Trace(Meldung, Schweregrad, custom_record)*

- *Message* – Erforderlich. Dies sind die nachzuverfolgenden Informationen. In Tests erstellt dieses Element einen Eintrag in der Tabelle „Traces“ im Datensatz „TestCaseResult“. 
- *Schweregrad:* optional. Dies entspricht dem Schweregrad des in Application Insights aufgezeichneten Trace-Elements. Es gibt die folgenden Optionen: „Information“, „Warnung“ oder „Fehler“. 
- *custom_record:* optional. Dies ist ein Datensatz mit benutzerdefinierten Daten, die in Application Insights gespeichert werden. 
  

### <a name="see-also"></a>Siehe auch

[Test Studio: Übersicht](../test-studio.md) <br>
[Arbeiten mit Test Studio](../working-with-test-studio.md)
