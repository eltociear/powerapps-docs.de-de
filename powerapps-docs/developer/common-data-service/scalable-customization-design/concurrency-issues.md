---
title: 'Skalierbares Anpassungsdesign: Concurrency-Probleme (Common Data Service) | Microsoft Docs'
description: 'Das dritte in einer Reihe von Themen. '
ms.custom: ''
ms.date: 1/15/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: rogergilchrist
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="scalable-customization-design-concurrency-issues"></a>Skalierbares Anpassungsdesign: Concurrency-Probleme

> [!NOTE]
> Dies ist das dritte in einer Reihe von Themen über skalierbares Anpassungsdesign. Um am Anfang zu beginnen, siehe [Skalierbares Anpassungsdesign im Common Data Service](overview.md).
> Das vorherige Thema [Skalierbares Anpassungsdesign: Datenbanktransaktionen](database-transactions.md) beschrieben, wie Datenbanktransaktionen angewendet werden und welche Auswirkungen sie auf verschiedene Arten von Anpassungen haben.

Wenn Sie gleichzeitige Anfragen haben, wird die Wahrscheinlichkeit von Kollisionen an Sperren höher. Je länger die Transaktionen dauern, desto länger werden die Sperren gehalten. Die Wahrscheinlichkeit einer Kollision ist noch größer und die Gesamtwirkung für den Endbenutzer ist größer. 

Sie müssen sich auch der vielfältigen Möglichkeiten bewusst sein, wie Aktivitäten auf die Anwendung angewendet werden können, von denen jede Sperren nimmt, die Konflikte mit anderen Aktionen innerhalb des Systems verursachen können. In diesen Fällen verhindert das Sperren Inkonsistenzen von Daten, wenn überlappende Aktionen auf denselben Daten stattfinden. 

Einige Schlüsselbereiche, für die man das Design in Betracht ziehen und prüfen sollte, ob man Probleme sieht, sind:

![überlappende Anforderungen](media/concurrency-considerations.png)

- **Benutzergesteuerte Aktivität**: Direkt über die Benutzeroberfläche.
- **Async-Aktionen**: Aktivität, die später durch andere Aktionen auftritt. Wann diese Aktivität verarbeitet wird, ist zum Zeitpunkt der Auslösung der auslösenden Aktion nicht bekannt.
- **Batch-Aktivitäten**: Entweder aus dem Common Data Service (z. B. Massenlöschaufträge oder serverseitige Synchronisationsverarbeitung) oder aus externen Quellen (z. B. Integration aus einem anderen System).

## <a name="async-operations-in-parallel"></a>Parallele asynchrone Operationen

Ein häufiger Irrtum ist, dass asynchrone Workflows oder Plug-Ins seriell aus einer Warteschlange verarbeitet werden und es keinen Konflikt zwischen ihnen geben würde. Dies ist nicht korrekt, da Common Data Service mehrere asynchrone Aktivitäten parallel sowohl innerhalb jeder asynchronen Service-Instanz als auch zwischen asynchronen Service-Instanzen, die über verschiedene Server verteilt sind, verarbeitet, um den Durchsatz zu erhöhen. Jeder Async-Dienst ruft tatsächlich Aufträge ab, die in Stapeln von ca. 20 Stück pro Dienst ausgeführt werden sollen, basierend auf Konfiguration und Last.

Wenn Sie mehrere asynchrone Aktivitäten aus demselben Ereignis auf demselben Datensatz initiieren, werden diese wahrscheinlich parallel verarbeitet. Da sie den gleichen Datensatz nutzen, ist ein gemeinsames Muster die Aktualisierung auf den gleichen übergeordneten Datensatz; daher ist die Konfliktgelegenheit hoch. 

Wenn ein auslösendes Ereignis eintritt, wie z. B. die Erstellung eines Kontos, kann die asynchrone Logik in Common Data Service Einträge in der [AsyncOperation (System Job) Entity](../reference/entities/asyncoperation.md) für jeden Prozess oder jede Aktion erstellen, die durchgeführt werden soll. Der Async Service überwacht diese Tabelle, nimmt wartende Anforderungen in Chargen auf und verarbeitet sie dann. Da die Workflows gleichzeitig ausgelöst werden, ist es sehr wahrscheinlich, dass sie in derselben Charge aufgenommen und gleichzeitig verarbeitet werden. 

## <a name="why-its-important-to-understand-transactions"></a>Warum es wichtig ist, Transaktionen zu verstehen

Das [Beispiel der automatischen Nummerierung](auto-numbering-example.md) stellt ein Szenario dar, das veranschaulicht, wie Datenbanktransaktionen und Concurrency-Probleme bei der Entwicklung skalierbarer Anpassungen berücksichtigt werden müssen.

## <a name="serialization-and-timeouts"></a>Serialisierung und Timeouts

Ein hoher Serialisierungsgrad ist typischerweise das, was Blockaden in Timeouts und schlechten Durchsatz verwandelt. Wenn Sie viele gleichzeitige Anfragen haben, sobald sie serialisiert sind und eine lange Zeit in Anspruch nehmen, dauert jede Anfrage wiederum länger, bis Sie Timeouts und damit Fehler machen. 

Der Timeout des Plugins beginnt mit dem Zeitpunkt, zu dem es gestartet wird. Ein SQL-Timeout wird für die Datenbankanfrage berechnet, so dass eine Abfrage, die lange Zeit wartet, eine Zeitüberschreitung verursachen kann.

![Serialisierung und Timeouts](media/serialization-and-timeouts.png)

## <a name="chain-of-actions"></a>Aktionskette

Neben dem Verständnis der spezifischen Abfragen in den direkt ausgelösten Aktivitäten ist es auch notwendig zu überlegen, wo eine Kette von verwandten Ereignissen auftreten kann.
 
Jede Nachrichtenanforderung, die in einem Plug-in oder als Schritt in einem synchronen Workflow gestellt wird, löst nicht nur die direkte Aktion aus, sondern kann auch andere synchrone Plug-Ins und Workflows auslösen. Jede dieser synchronen Aktivitäten findet in derselben Transaktion statt, wodurch sich die Lebensdauer dieser Transaktion verlängert und alle Sperren möglicherweise viel länger gehalten werden, als sie realisiert werden können.

![Aktionskette](media/chain-of-actions.png)

Der Gesamteffekt kann viel größer sein, als ursprünglich realisiert. Dies kann oft unbeabsichtigt geschehen, wenn mehrere Personen die Implementierung aufbauen oder sie sich mit der Zeit weiterentwickelt. 

## <a name="running-into-platform-constraints"></a>Plattformbeschränkungen

Hier kommen die Plattformbeschränkungen ins Spiel. Und in Wirklichkeit ist diese Art von Verhalten genau das, wovor die Einschränkungen bestehen, um das breitere System zu schützen.

Wann immer diese Verzögerung der Verarbeitung eintritt, hat sie unbeabsichtigte Folgen in anderen Bereichen des Systems und für andere Benutzer. Es ist daher wichtig zu verhindern, dass diese Art von Aktivität die Systemleistung beeinträchtigt.

Während der einfachste Weg, die Fehler zu vermeiden, darin besteht, die Plattformbeschränkungen zu lockern, geht es dabei nicht um die grundlegenderen Auswirkungen auf die allgemeine Skalierbarkeit und Leistung des Systems. Dies muss angegangen werden, indem das Verhalten, das die Beschränkungen überhaupt auslöst, behoben und verhindert wird. 

## <a name="impact-on-usage"></a>Auswirkungen auf die Nutzung

Was oft auch Auswirkungen auf die Nutzung hat, ist eine kaskadierende Reihe von Auswirkungen dieses Verhaltens.

![Auswirkungen auf die Nutzung](media/impact-on-usage.png)

Das erste Problem sind Sperren und damit das Sperren im System. Dies führt zu langsamen Benutzerantwortzeiten, die dann als unvorhersehbare und unzuverlässige Benutzerantwortzeiten, oft in einem bestimmten Bereich des Systems, verstärkt werden.

Im Extremfall oder unter höherer als normaler Belastung kann dies dann in jeder Batch-Verarbeitung im Hintergrund mit schlechtem Durchsatz zum Tragen kommen. Schließlich kann es zu Fehlern im System kommen.

Es ist üblich, dass Benutzer bei der Untersuchung von SQL-Timeout-Fehlern auch schlechte und unvorhersehbare Antwortzeiten melden, und die Verbindung zwischen diesen als verwandte Probleme nicht hergestellt wurde. 


## <a name="next-steps"></a>Nächste Schritte

Verstehen Sie die Entwurfsmuster, die Sie anwenden (oder vermeiden) können, um Leistungsprobleme zu minimieren. Mehr Informationen: [Skalierbares Anpassungsdesign: Transaktionsdesign-Muster](transaction-design-patterns.md)