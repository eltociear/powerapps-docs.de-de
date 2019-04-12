---
title: 'Skalierbares Anpassungsdesign: Datenbanktransaktionen (Common Data Service) | Microsoft Docs'
description: Das zweite in einer Reihe von Themen. Dieses Thema konzentriert sich auf die Auswirkungen von Datenbanktransaktionen auf das skalierbare Anpassungsdesign.
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

# <a name="scalable-customization-design-database-transactions"></a>Skalierbares Anpassungsdesign: Datenbanktransaktionen

> [!NOTE]
> Dies ist der zweite in einer Reihe von Themen über skalierbares Anpassungsdesign. Um am Anfang zu beginnen, siehe [Skalierbares Anpassungsdesign im Common Data Service](overview.md).

Eines der grundlegendsten Konzepte hinter vielen der hier anstehenden Herausforderungen ist das der Datenbanktransaktion. Im Common Data Service steht die Datenbank im Mittelpunkt fast aller Anfragen an das System und die Datenkonsistenz wird in erster Linie durchgesetzt.

- Keine Common Data Service-Datenoperationen, weder interne noch Teil von Codeanpassungen, funktionieren vollständig isoliert.
- Alle Datenoperationen von Common Data Service interagieren mit den gleichen Datenbankressourcen, entweder auf Daten- oder Infrastrukturebene wie Prozessor-, Speicher- oder I/O-Nutzung.
- Um sich vor widersprüchlichen Änderungen zu schützen, sperrt jeder Request die Ressourcen, die angesehen oder geändert werden sollen.
- Diese Sperren werden innerhalb einer Transaktion übernommen und erst freigegeben, wenn die Transaktion bestätigt oder abgebrochen wird.

## <a name="transaction-and-locking-awareness"></a>Transaktion und Berücksichtigung des Sperrverhaltens

Ein häufiger Grund dafür, dass in diesem Bereich Probleme auftreten können, ist die mangelnde Sensibilität dafür, wie sich Anpassungen auf Transaktionen auswirken können.

Obwohl die Details, wie dies geschieht, über den Rahmen dieses Themas hinausgehen, ist das einfachste zu betrachtende Element, dass als Common Data Service mit Daten in seiner Datenbank interagiert. SQL Server bestimmt die entsprechenden Sperren, die von Transaktionen für diese Daten verwendet werden sollen, wie z. B.:
- Beim Abrufen eines bestimmten Datensatzes setzt SQL Server eine Lesesperre auf diesen Datensatz.
- Beim Abrufen eines Bereichs von Datensätzen kann in einigen Szenarien eine Lesesperre für diesen Bereich von Datensätzen oder die gesamte Tabelle verhängt werden.
- Beim Erstellen eines Datensatzes erzeugt es eine Schreibsperre für diesen Datensatz.
- Beim Aktualisieren eines Datensatzes wird eine Schreibsperre gegen den Datensatz verhängt.
- Wenn eine Sperre gegen eine Tabelle oder einen Datensatz verhängt wird, wird sie auch gegen entsprechende Indexsätze verhängt.

Es ist jedoch möglich, den Umfang und die Dauer dieser Sperren zu beeinflussen. Es ist auch möglich, dem SQL Server mitzuteilen, dass für bestimmte Szenarien keine Sperre erforderlich ist.

Betrachten wir das Sperren von SQL Server-Datenbanken und die Auswirkungen einzelner Anfragen, die versuchen, auf dieselben Daten zuzugreifen. Im folgenden Beispiel hat das Anlegen eines Kontos eine Reihe von Prozessen eingerichtet, einige mit Plug-Ins, die sofort nach dem Anlegen des Datensatzes ausgelöst werden, andere in einem zugehörigen asynchronen Workflow, der beim Anlegen gestartet wird.
 
Das Beispiel zeigt die Konsequenzen, wenn ein Kontoaktualisierungsprozess eine komplexe Nachbearbeitung hat, während andere Aktivitäten ebenfalls mit demselben Kontendatensatz interagieren. Wenn ein asynchroner Workflow verarbeitet wird, während die Kontoaktualisierungstransaktion noch läuft, kann dieser Workflow blockiert werden, um eine Aktualisierungssperre zu erhalten, um den gleichen Kontent zu ändern, der noch gesperrt ist.

![Sperren und Transaktionsbeispiel](media/locking-and-transactions-example.png)

Es ist zu beachten, dass Transaktionen nur während der Laufzeit einer bestimmten Anfrage an die Plattform durchgeführt werden. Sperren werden nicht auf der Ebene einer Benutzersitzung oder während der Anzeige von Informationen auf der Benutzeroberfläche gehalten. Sobald die Plattform die Anforderung abgeschlossen hat, gibt sie die Datenbankverbindung, die zugehörige Transaktion und die von ihr getroffenen Sperren frei. 


## <a name="blocking"></a>Blockierung

Während die Art der Blockierung im vorherigen Beispiel an sich unangenehm sein kann, kann dies auch zu schwerwiegenderen Folgen führen, wenn man bedenkt, dass Common Data Service eine Plattform ist, die Hunderte von gleichzeitigen Aktionen verarbeiten kann. Während das Halten einer Sperre für einen einzelnen Kontoeintrag relativ begrenzte Auswirkungen haben kann, was passiert, wenn eine Ressource stärker beansprucht wird?

Wenn jedes Konto beispielsweise eine eindeutige Referenznummer erhält, kann dies dazu führen, dass eine einzige Ressource, die die verwendeten Referenznummern verfolgt, bei jedem Kontoerstellungsprozess gesperrt wird. Wie im [Beispiel der automatischen Nummerierung](auto-numbering-example.md) beschrieben, müssen überlappende Anfragen, wenn viele Konten parallel generiert werden, alle auf diese Ressource zugreifen und sie blockieren, bis sie ihre Aktion abgeschlossen haben. Je länger jeder Kontoerstellungsprozess dauert und je mehr gleichzeitige Anfragen es gibt, desto mehr wird blockiert.

Während die erste Anforderung, die automatische Ressourcensperre zu greifen, leicht abgeschlossen werden kann, muss die zweite Anforderung warten, bis die erste abgeschlossen ist, bevor sie überprüfen kann, was die nächste eindeutige Referenznummer ist. Die dritte Anforderung muss warten, bis die erste und zweite Anforderung abgeschlossen ist. Je mehr Anfragen es gibt, desto länger dauert die Sperrung. Wenn es genügend Anfragen gibt und jede Anfrage lange genug dauert, kann dies die späteren Anfragen so weit bringen, dass sie zeitlich begrenzt sind, auch wenn sie einzeln korrekt abgeschlossen werden können.

![Blockierbeispiel](media/blocking.png)

## <a name="lock-release"></a>Sperrfreigabe

Es gibt zwei Hauptgründe, warum eine Sperre nicht freigegeben wird, sondern bis zum Abschluss der Transaktion gehalten wird:

- Der Datenbankserver hält die Sperre aus Konsistenzgründen fest, falls die Transaktion später eine weitere Anforderung zur Aktualisierung des Datenelements stellt.
- Der Datenbankserver muss auch berücksichtigen, dass ein später ausgegebener Fehler- oder Abbruchbefehl dazu führen kann, dass er die gesamte Transaktion zurücksetzt, so dass er die Sperren für die gesamte Lebensdauer der Transaktion halten muss, um die Konsistenz zu gewährleisten.

Es ist wichtig zu wissen, dass, obwohl Ihr Prozess möglicherweise alle Interaktionen mit einem bestimmten Datenelement abgeschlossen hat, die Sperre so lange gehalten wird, bis die gesamte Transaktion abgeschlossen und bestätigt ist. Je länger die Transaktion verlängert wird, desto länger wird die Sperre gehalten und verhindert, dass andere Threads mit diesen Daten interagieren. Wie später gezeigt wird, beinhaltet dies auch verwandte Anpassungen, die innerhalb derselben Transaktion funktionieren und die die Lebensdauer von Transaktionen wie z. B. synchronen Workflows erheblich verlängern können.

Im folgenden Beispiel wird die Schreibsperre für eine benutzerdefinierte Entität im Pre-Create Plug-in für ein Konto gesperrt, bis die gesamte mit der Erstellung des Kontos verbundene Logik abgeschlossen ist.

![Sperrfreigabe](media/lock-release.png)

## <a name="intermittent-errors-timing"></a>Intermittierende Fehler: Timing

Intermittierendes Verhalten ist ein offensichtliches Symptom für das Blockieren von gleichzeitigen Aktivitäten. Wenn die Wiederholung genau der gleichen Aktion später erfolgreich ist, wenn sie früher fehlgeschlagen ist, besteht eine sehr hohe Wahrscheinlichkeit, dass der Fehler oder die Verlangsamung durch etwas anderes verursacht wurde, das gleichzeitig auftritt.

Das ist wichtig zu erkennen, wenn man beim Debuggen eines Problems oft die beleidigende Funktionalität auf das absolute Minimum reduziert. Wenn das Problem jedoch nur sporadisch auftritt, müssen Sie sich möglicherweise ansehen, wo die fehlgeschlagene Aktion im Widerspruch zu einer anderen Aktivität im System steht, und Sie müssen sich mögliche Streitpunkte ansehen. Sie können Konflikte vermeiden, indem Sie einen einzelnen Prozess optimieren; je kürzer die Bearbeitungszeit, desto unwahrscheinlicher ist es, dass die Aktivität mit anderen Prozessen in Konflikt gerät. 

## <a name="transaction-control"></a>Transaktionssteuerung

Während in den meisten Fällen die Art und Weise, wie Transaktionen verwendet werden, einfach der Plattform überlassen werden kann, um sie zu verwalten, gibt es Szenarien, in denen die erforderliche Logik komplex genug ist, dass Verständnis und Einfluss auf Transaktionen erforderlich sind, um die gewünschten Ergebnisse zu erzielen. Common Data Service bietet eine Reihe von verschiedenen Anpassungsansätzen, die sich unterschiedlich auf die Art und Weise auswirken, wie Transaktionen verwendet werden.

Wenn Sie verstehen, wie jede Art von Anpassung an den Plattformtransaktionen beteiligt ist, können Sie komplexe Szenarien in Common Data Service effektiv modellieren und deren Verhalten vorhersagen.

Wie bereits erwähnt, wird eine Transaktion nur während der Laufzeit einer Anfrage an die Plattform durchgeführt, sie ist nichts, was nach Abschluss des Plattformschritts gepflegt wird. Dadurch wird vermieden, dass Transaktionen von einem externen Kunden über einen längeren Zeitraum gehalten werden und andere Plattformaktivitäten blockiert werden.

Die Aufgabe der Plattform besteht darin, die Konsistenz in der gesamten Plattformtransaktionspipeline aufrechtzuerhalten und gegebenenfalls Anpassungen zu ermöglichen, die an derselben Transaktion teilnehmen.

## <a name="how-model-driven-apps-use-transactions"></a>Wie modellgetriebene Apps Transaktionen verwenden

Bevor Sie verstehen, wie Anpassungen mit der Plattform interagieren, ist es sinnvoll zu verstehen, wie modellgetriebene Anwendungen Anfragen an die Plattform verwenden und wie sie die Transaktionsverwendung beeinflussen.

|Vorgang|Beschreibung|
|--|--|
|Forms (Retrieve)|&bull; Setzt eine Lesesperre für den angezeigten Datensatz.<br />&bull; Geringe Auswirkungen auf andere Anwendungen.|
|Erstellen|&bull; Führt eine Erstellungsanforderung über die Plattform aus.<br />&bull; Geringe Auswirkungen auf andere Aktivitäten, da ein neuer Rekord nichts anderes blockiert.<br />&bull; Kann Sperranfragen an die gesamte Tabelle blockieren, bis sie abgeschlossen ist.<br />&bull; Kann oft verwandte Aktionen in der Anpassung auslösen, die Auswirkungen haben können.|
|Update|&bull; Führt einen Aktualisierungsauftrag über die Plattform aus.<br />&bull; Es ist wahrscheinlicher, dass es Konflikte gibt. Eine Aktualisierungssperre blockiert alle anderen Aktualisierungen oder das Lesen dieses Datensatzes. Blockiert auch alles, was eine breite Lesesperre auf dieser Tabelle nimmt.<br />&bull; Löst oft andere Aktivitäten aus.|
|View (RetrieveMultiple)|&bull; Könnte viele andere Aktivitäten blockieren.<br />&bull; Übergibt aber bewusst `nolock` Hinweise auf Abfragen.<br />&bull; Sperrt also typischerweise keine anderen Aktivitäten.<br />&bull; Obwohl eine schlechte Abfrageoptimierung die Auslastung der DB-Ressourcen beeinflussen kann und möglicherweise zu Timeouts führt.|

## <a name="event-pipeline-platform-step"></a>Event Pipeline: Plattformschritt

Wenn eine Ereignis-Pipeline initiiert wird, wird eine SQL-Transaktion erstellt, die den Plattformschritt beinhaltet. Auf diese Weise wird sichergestellt, dass alle von der Plattform ausgeführten Datenbankaktivitäten konsequent umgesetzt werden. Die Transaktion wird zu Beginn der Event-Pipeline angelegt und nach Abschluss der Verarbeitung entweder committed oder abgebrochen, je nachdem, ob sie erfolgreich war. 

![Event Pipeline Plattform Schritt](media/event-pipeline-platform-step.png)

## <a name="customization-requests"></a>Anpassungsanforderungen

Es ist auch möglich, an der plattforminitiierten Transaktion im Rahmen von Anpassungen teilzunehmen. Jede Art von Anpassung nimmt auf unterschiedliche Weise an Transaktionen teil. In den folgenden Abschnitten werden die einzelnen Abschnitte nacheinander beschrieben. 
    
- [Synchronisation von Plugins (vor oder nach der Operation: im Transaktionskontext)](#sync-plug-ins-pre-or-post-operation-in-transaction-context)
- [Synchronisation von Plugins (vor und nach der Operation: im Transaktionskontext)](#sync-plug-ins-pre-and-post-operation-in-transaction-context)
- [Plugins synchronisieren (**PreValidation**: außerhalb des Transaktionskontextes)](#sync-plug-ins-prevalidation-outside-transaction-context)
- [Plugins synchronisieren (**PreValidation**: im Transaktionskontextes)](#sync-plug-ins-prevalidation-in-transaction-context)
- [Async-Plug-ins](#async-plug-ins)
- [Zusammenfassung der Verwendung von Plug-in-Transaktionen](#plug-in-transaction-use-summary)
- [Synchrone Workflows](#synchronous-workflows)
- [Asynchrone Workflows](#asynchronous-workflows)
- [Benutzerdefinierte Workflow-Aktivität](#custom-workflow-activity)
- [Benutzerdefinierte Aktionen](#custom-actions)
- [Webservice-Anfragen](#web-service-requests)

### <a name="sync-plug-ins-pre-or-post-operation-in-transaction-context"></a>Synchronisation von Plugins (vor oder nach der Operation: im Transaktionskontext)

Wenn Plugins für ein Ereignis registriert sind, können sie gegen eine **PreOperation**- oder **PostOperation**-Phase registriert werden, die sich innerhalb der Transaktion befindet. Alle Nachrichtenanforderungen des Plugins werden innerhalb der Transaktion ausgeführt. Dies bedeutet, dass die Lebensdauer der Transaktion und die Dauer der Sperren verlängert werden.

![Synchronisation von Plugins (vor oder nach der Operation: im Transaktionskontext)](media/sync-plug-ins-pre-or-post-operation-in-transaction-context.png)

### <a name="sync-plug-ins-pre-and-post-operation-in-transaction-context"></a>Synchronisation von Plugins (vor und nach der Operation: im Transaktionskontext)

Plug-Ins können sowohl für die Phasen **PreOperation** als auch **PostOperation** registriert werden. In diesem Fall kann die Transaktion noch länger dauern, da sie vom Start des **PreOperation**-Plugins bis zum Abschluss des **PostOperation**-Plugins reicht.

![Synchronisation von Plugins (vor und nach der Operation: im Transaktionskontext)](media/sync-plug-ins-pre-and-post-operation-in-transaction-context.png)

### <a name="sync-plug-ins-prevalidation-outside-transaction-context"></a>Plugins synchronisieren (**PreValidation**: außerhalb des Transaktionskontextes)

Ein Plug-in kann auch außerhalb der Plattformtransaktion registriert werden, indem es in der **PreValidierungs**phase registriert wird.

> [!NOTE]
> Es erstellt KEINE eigene Transaktion. Dadurch wird jede Nachrichtenanforderung innerhalb des Plugins unabhängig voneinander in der Datenbank bearbeitet.

![Plugins synchronisieren (**PreValidation**: außerhalb des Transaktionskontextes)](media/sync-plug-ins-pre-validation-outside-transaction-context.png)

Dieses Szenario gilt nur, wenn die **PreValidation** als erste Stufe eines Pipeline-Ereignisses aufgerufen wird. Obwohl das Plug-in in der **PreValidation**-Phase registriert ist, ist es möglich, dass es an einer Transaktion teilnimmt, wie im nächsten Abschnitt beschrieben. Es kann nicht davon ausgegangen werden, dass ein **PreValidation**-Plugin nicht an einer Transaktion teilnimmt, obwohl es möglich ist, aus dem Ausführungskontext heraus zu überprüfen, ob dies der Fall ist.

### <a name="sync-plug-ins-prevalidation-in-transaction-context"></a>Plugins synchronisieren (**PreValidation**: im Transaktionskontext)

Das zugehörige Szenario tritt auf, wenn ein **PreValidation**-Plugin registriert ist, aber das zugehörige Pipeline-Ereignis durch eine Nachrichtenanforderung innerhalb einer bestehenden Transaktion ausgelöst wird. 

Wie das folgende Diagramm zeigt, kann die Erstellung eines Kontos dazu führen, dass ein **PreValidation**-Plugin zunächst außerhalb einer Transaktion ausgeführt wird, wenn die erste Erstellung durchgeführt wird. Wenn als Teil des Post-Plugins eine Nachrichtenanforderung zum Erstellen eines zugehörigen untergeordneten Kontos gestellt wird, weil diese zweite Ereignis-Pipeline aus der übergeordneten Pipeline heraus initiiert wird, nimmt sie an derselben Transaktion teil. 

In diesem Fall stellt das **PreValidation**-Plugin fest, dass eine Transaktion bereits existiert, und nimmt somit an dieser Transaktion teil, obwohl sie auf der Stufe **PreValidation** registriert ist. 

![Plugins synchronisieren (**PreValidation**: im Transaktionskontext)](media/sync-plug-ins-pre-validation-in-transaction-context.png)

Wie bereits erwähnt, kann das Plug-in den Ausführungskontext für die Eigenschaft <xref:Microsoft.Xrm.Sdk.IExecutionContext.IsInTransaction> überprüfen, was anzeigt, ob dieses Plug-in innerhalb einer Transaktion ausgeführt wird oder nicht.

### <a name="async-plug-ins"></a>Async-Plug-ins

Ein Plug-in kann auch für asynchrones Arbeiten registriert werden. In diesem Fall agiert das Plug-in auch außerhalb der Plattformtransaktion.

> [!NOTE]
> Das Plug-in erstellt keine eigene Transaktion; jede Nachrichtenanforderung innerhalb des Plug-ins wird unabhängig voneinander bearbeitet.

![foo](media/async-plug-ins.png)


### <a name="plug-in-transaction-use-summary"></a>Zusammenfassung der Verwendung von Plug-in-Transaktionen

Zusammenfassen:

- Synchrone Plugins nehmen in der Regel an Transaktionen teil.
- Async-Plugins nehmen nie an einer Plattformtransaktion teil; jede Anforderung wird unabhängig ausgeführt.
- **PreValidation**-Plugins erstellen keine Transaktion, sondern nehmen teil, wenn bereits eine existiert.

|Ereignis|Name der Phase|Transaktion ist noch nicht vorhanden|Transaktion existiert bereits|
|--|--|--|--|
|Vor-Ereignis|**PreValidation**|Es wird keine Transaktion angelegt. Nimmt nicht an der Transaktion teil; jede Anfrage verwendet eine unabhängige Transaktion für die Datenbank|Teilnahme an einer bestehenden Transaktion|
|Vor-Ereignis|**PreOperation**|Teilnahme an einer bestehenden Transaktion|Teilnahme an einer bestehenden Transaktion|
|Post-Event|**PostOperation**|Teilnahme an einer bestehenden Transaktion|Teilnahme an einer bestehenden Transaktion|
|Asynchron|Nicht zutreffend|Es wird keine Transaktion angelegt. Nimmt nicht an der Transaktion teil; jede Anfrage verwendet eine unabhängige Transaktion für die Datenbank|Nicht zutreffend|

### <a name="synchronous-workflows"></a>Synchrone Workflows

Aus transaktionsbezogener Sicht fungieren synchrone Workflows als Pre/Post Operation Plug-Ins. Sie agieren daher innerhalb der Plattform-Pipeline-Transaktion und können sich auf die Länge der gesamten Transaktion gleichermaßen auswirken.

![Synchrone Workflows](media/synchronous-workflows.png)

### <a name="asynchronous-workflows"></a>Asynchrone Workflows

Asynchrone Workflows werden außerhalb der Plattformtransaktion ausgelöst.

> [!NOTE]
> Der Workflow erstellt auch KEINE eigene Transaktion und daher wird jede Nachrichtenanforderung innerhalb des Workflows unabhängig voneinander bearbeitet.

Das folgende Diagramm zeigt den asynchronen Workflow außerhalb der Plattformtransaktion und jeden Schritt, der eine eigene unabhängige Transaktion initiiert.

![Asynchrone Workflows](media/asynchronous-workflows.png)

### <a name="custom-workflow-activity"></a>Benutzerdefinierte Workflow-Aktivität

Benutzerdefinierte Workflow-Aktivitäten agieren innerhalb des übergeordneten Workflow-Kontextes.

- Synchronisations-Workflow: Aktionen innerhalb der Transaktion
- Asynchroner Workflow: Aktionen außerhalb der Transaktion

Das folgende Diagramm zeigt benutzerdefinierte Aktivitäten, die zuerst innerhalb eines synchronen Workflows und dann innerhalb eines asynchronen Workflows ausgeführt werden.

![Benutzerdefinierte Workflow-Aktivität](media/custom-workflow-activity.png)

### <a name="custom-actions"></a>Benutzerdefinierte Aktionen

Benutzerdefinierte Aktionen können eigene Transaktionen erstellen. Dies ist ein wesentliches Merkmal. Eine benutzerdefinierte Aktion kann eine separate Transaktion außerhalb des Plattformschritts erstellen, je nachdem, ob sie für Rollback aktivieren konfiguriert ist.

- Rollback-Set aktivieren
    - Wenn die benutzerdefinierte Aktion durch eine Nachrichtenanforderung eines Plug-Ins aufgerufen wird, das in der Transaktion ausgeführt wird, und Rollback aktivieren eingestellt ist, wirkt sie innerhalb der bestehenden Transaktion.
    - Die benutzerdefinierte Aktion erstellt ansonsten eine neue Transaktion und wird innerhalb dieser ausgeführt.
- Rollback aktivieren nicht gesetzt
    - Die benutzerdefinierte Aktion wird nicht innerhalb einer Transaktion ausgeführt.

![benutzerdefinierte Aktionen](media/custom-actions.png)

### <a name="web-service-requests"></a>Webservice-Anfragen

Wenn Anforderungen extern über Webservices gestellt werden, wird eine Pipeline erstellt und die Transaktionsabwicklung innerhalb der Pipeline erfolgt wie zuvor beschrieben, aber eine Transaktion wird nach der Rückgabe der Antwort nicht mehr gepflegt. Da die Zeit bis zur nächsten Anfrage unbekannt ist, erlaubt die Plattform kein Sperren von Ressourcen, die andere Aktivitäten blockieren würden.

Wenn innerhalb eines Plugins mehrere Anforderungen mit demselben Ausführungskontext gestellt werden, ist es der gemeinsame Ausführungskontext, der die Transaktionsreferenz aufrechterhält und in synchronen Plugins sicherstellt, dass jede Anforderung innerhalb derselben Transaktion ausgeführt wird. Die Möglichkeit, einen Ausführungskontext über Anforderungen hinweg zu pflegen, ist außerhalb von Plug-Ins nicht verfügbar und daher kann eine Transaktion nicht über getrennte, extern erstellte Anforderungen hinweg gepflegt werden.

Es gibt zwei spezielle Messages, bei denen mehrere Aktionen als Teil einer einzigen Webservice-Anfrage an die Common Data Service-Plattform übergeben werden können.

|Meldung|Beschreibung|
|--|--|
|`ExecuteMultiple`|Dies ermöglicht es, mehrere unabhängige Aktionen innerhalb derselben Webservice-Anfrage zu übergeben. Jede dieser Anfragen wird unabhängig innerhalb der Plattform ausgeführt, so dass es keinen Transaktionskontext zwischen den Anfragen gibt.|
|`ExecuteTransaction`|Dadurch können mehrere Aktionen innerhalb derselben Datenbanktransaktion verarbeitet werden, ähnlich wie bei mehreren Nachrichtenanforderungen, die innerhalb eines synchronen Plugins erfolgen.<br /> <br />Diese Fähigkeit hätte auch Auswirkungen ähnlich wie mehrere Nachrichtenanforderungen, d.h. wenn jede Aktion lange Zeit in Anspruch nimmt (z.B. durch teure Abfragen oder das Auslösen einer langen Kette von zugehörigen synchronen Plugins oder Workflows), könnte dies dazu führen, dass Probleme auf der breiteren Plattform blockiert werden.|

#### <a name="web-api-odata-requests-in-plug-ins"></a>Web API (OData) Anfragen in Plugins

Verwenden Sie keine Web-API-(OData)-Anforderungen innerhalb eines Plug-Ins an dieselbe Organisation wie das Plug-In. Verwenden Sie immer die <xref:Microsoft.Xrm.Sdk.IOrganizationService>-Methoden. Dadurch kann der Transaktionskontext übergeben werden, so dass der Vorgang an der Pipelinetransaktion teilnehmen kann.

## <a name="next-steps"></a>Nächste Schritte

Zusätzlich zu den Datenbanktransaktionen ist es wichtig, die Auswirkungen mehrerer gleichzeitiger Datenoperationen auf das System zu verstehen. Mehr Informationen: [Skalierbares Anpassungsdesign: Concurrency-Probleme](concurrency-issues.md)


