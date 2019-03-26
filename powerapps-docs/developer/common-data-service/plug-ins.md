---
title: Verwenden von Plug-Ins zur Erweiterung von Geschäftsprozessen (Common Data Service for Apps) | Microsoft Docs
description: 'Ein Plug-In ist eine .NET-Assembly, die Sie zum Common Data Service for Apps hochladen können. Klassen innerhalb der Assemblys können für bestimmte Ereignisse (Schritte) innerhalb des Ereignisframeworks registriert werden. Der Code innerhalb der Klasse bietet Ihnen eine Möglichkeit, auf das Ereignis zu reagieren, sodass Sie das Standardverhalten der Plattform erweitern oder ändern können.'
ms.custom: ''
ms.date: 1/23/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-plug-ins-to-extend-business-processes"></a>Verwenden von Plug-Ins zur Erweiterung von Geschäftsprozessen

Ein Plug-In ist eine .NET-Assembly, die Sie zum Common Data Service for Apps hochladen können. Klassen innerhalb der Assemblys können für bestimmte Ereignisse (Schritte) innerhalb des Ereignisframeworks registriert werden. Der Code innerhalb der Klasse bietet Ihnen eine Möglichkeit, auf das Ereignis zu reagieren, sodass Sie das Standardverhalten der Plattform erweitern oder ändern können.

> [!IMPORTANT]
> Wenn immer möglich, sollten Sie zunächst erwägen, eine von mehreren deklarativen Optionen zur Definition der Geschäftslogik anzuwenden. Weitere Informationen: [Anwenden von Geschäftslogik in CDS for Apps](../../maker/common-data-service/cds-processes.md)<br/><br/>
> Verwenden Sie Plug-Ins, wenn ein deklarativer Prozess nicht Ihre Bedingung erfüllt.

Die Klassen im Assembly, die für einen Schritt registriert werden können, müssen die <xref:Microsoft.Xrm.Sdk.IPlugin>-Benutzeroberfläche bereitstellen. Diese Schnittstelle unterstützt eine einzelne Methode: <xref:Microsoft.Xrm.Sdk.IPlugin.Execute*>. Wenn ein Ereignis auftritt, für das eine Klasse registriert ist, werden kontextbezogene Daten an die Methode `Execute` übergeben. Innerhalb der `Execute`-Methode können Sie Folgendes tun:

- Brechen Sie das Ereignis ab und zeigen Sie eine Fehlermeldung für den Benutzer an
- Nehmen Sie Änderungen an den Daten im Vorgang vor
- Initiieren Sie weitere Aktionen mithilfe des Organisationsservice, um Automatisierung hinzuzufügen

Plug-Ins können so konfiguriert werden, dass sie synchron oder asynchron ausgeführt werden. Ein synchrones Plug-In bewirkt, dass der Vorgang wartet, bis der Code im Plug-In ausgeführt wurde. Dies wirkt sich auf die wahrgenommene Leistung des Systems aus. Die Vorgänge in einem asynchronen Plug-In werden in einer Warteschlange platziert und ausgeführt, nachdem der Vorgang abgeschlossen wurde, sodass der Vorgang mit minimaler Unterbrechung ausgeführt werden kann.

## <a name="when-to-use-plug-ins"></a>Verwenden von Plug-Ins

Personen vergleichen häufig Workflows und Plug-Ins als Auswahlmöglichkeiten für die Anwendung benutzerdefinierter Geschäftslogik. Die Funktionen vonWorkflows und Plug-Ins überschneiden sich signifikant. Plug-Ins können alle Funktionen ausführen, die Workflows ausführen, das Gegenteil trifft aber nicht zu. Dies bedeutet jedoch nicht, dass Sie Plug-Ins für alles verwenden sollten, was mit einem Workflow ausgeführt werden kann. Es stehen weitere Funktionen zum Erfüllen von Anforderungen zur Verfüguing, ohne Plug-Ins zu verwenden. 

- Workflows können benutzerdefinierte Workflowerweiterungen (Workflowaktivitäten) verwenden, mit denen Sie wiederverwendbare Bedingungen und Aktionen mit Code erstellen können, die in mehreren Workflows verwendet werden können. 

- Berechnete Felder und Rollupfelder bieten Funktionen, die bisher nur mit Workflows ausgeführt werden konnten.

- Benutzerdefinierte Aktionen sind ein Prozesstyp, der mit Workflows vergleichbar ist und ermöglichen die Erstellung von wiederverwendbaren Meldungen, die von anderen Workflows oder von Webdienstendpunkten aufgerufen werden können.

- Azure Servicebusintegration und Webhooks können verwendet werden, um Daten in externen Systemen bereitzustellen, in denen Logik mithilfe von vielen verschiedenen Ressourcen angewendet werden kann.

- Microsoft Flow bietet viele Funktionen, die bisher mithilfe von Plug-Ins ausgeführt wurden.

Ihnen stehen viele Optionen zur Verfügung. Sie müssen jede von ihnen auswerten, um die beste Methode zum Erfüllen Ihrer Bedingungen zu verstehen.

### <a name="advantages-of-plug-ins"></a>Vorteile von Plug-Ins

Dies sind die Hauptvorteile von Plug-Ins:

- Plug-Ins erbringen eine gute Leistung. Ein gut geschriebenes Plug-In bietet die leistungsstärkste Möglichkeit, Geschäftslogik anzuwenden.
- Plug-Ins sind leistungsstark. Viele Entwickler würden Ihre Fähigkeiten und Ihr Wissen lieber nutzen, um Logik zu definieren und die Fähigkeiten zu nutzen, um direkt mit dem Organisationsservice oder mit externen Services in Code zu arbeiten. Ein erfahrener Plug-In-Entwickler kann überaus produktiv sein.

### <a name="disadvantages-of-plug-ins"></a>Nachteile von Plug-Ins

- Für das Erstellen und die Pflege von Plug-Ins werden die besonderen Qualifikationen eines Entwicklers benötigt. Entwickler können Kosten verursachen und sind vielen Unternehmen nicht zugänglich, wenn sie sie brauchen. Geschäftsprozesse können sich schnell ändern und durch Bereitstellen von Optionen, die eine Änderung ermöglichen, ohne einen Entwickler zu erfordern, ist es dem System möglich, sich schneller anzupassen.
- Plug-Ins können missbräuchlich verwendet werden. Ein schlecht geschriebenes Plug-In kann erhebliche Auswirkungen auf die Leistung der Umgebung haben. Die große Leistungsfähigkeit von Plug-Ins muss mit gewisser Zurückhaltung und unter Berücksichtigung ihrer Auswirkung auf das System als Ganzes angewendet werden.


## <a name="next-steps"></a>Nächste Schritte

Verwenden Sie das folgende Lernprogramm und die folgenden Vorgehensweisen, um zu lernen, wie Plug-Ins geschrieben werden

### <a name="tutorials"></a>Lernprogramme

Diese Themen leiten Sie bei dem Prozess zum Erstellen einiger einfacher Plug-Ins an.

- [Lernprogramm: Schreiben und Registrieren eines Plugins](tutorial-write-plug-in.md)
- [Lernprogramm: Debuggen eines Plug-Ins](tutorial-debug-plug-in.md)
- [Lernprogramm: Aktualisieren eines Plug-Ins](tutorial-update-plug-in.md)

### <a name="how-to-topics"></a>Vorgehensweisen

Diese Themen enthalten Informationen, die Sie zum Erstellen von Plug-Ins verwenden.

- [Schreiben eines Plug-Ins](write-plug-in.md)
- [Verarbeiten von Ausnahmen](handle-exceptions.md)
- [Registrieren eines Plug-Ins](register-plug-in.md)
- [Debuggen von Plug-Ins](debug-plug-in.md)
- 
Diese Themen enthalten weitere Informationen zum Schreiben oder Debugging ein Plug-In oder Analysieren der Leistung.

- [Die Identität eines Benutzers annehmen](impersonate-a-user.md)
- [Protokollierung und Ablaufverfolgung](logging-tracing.md)
- [Analysieren der Leistung](analyze-performance.md)
- [Zugriff auf externe Web-Ressourcen](access-web-services.md)]
