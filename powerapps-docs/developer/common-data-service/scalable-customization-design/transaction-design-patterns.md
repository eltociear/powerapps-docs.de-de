---
title: 'Skalierbares Anpassungsdesign: Transaktionsdesign-Muster (Common Data Service) | Microsoft Docs'
description: 'Das vierte in einer Reihe von Themen. '
ms.custom: ''
ms.date: 11/18/2018
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
# <a name="scalable-customization-design-transaction-design-patterns"></a>Skalierbares Anpassungsdesign: Transaktionsdesign-Muster

> [!NOTE]
> Dies ist der vierte in einer Reihe von Themen über skalierbares Anpassungsdesign. Um am Anfang zu beginnen, siehe [Skalierbares Anpassungsdesign im Common Data Service](overview.md).

Dieser Abschnitt beschreibt die zu vermeidenden oder zu minimierenden Entwurfsmuster und deren Auswirkungen. Jedes Entwurfsmuster muss im Zusammenhang mit dem zu lösenden Geschäftsproblem betrachtet werden und kann als Option zur Untersuchung nützlich sein.

## <a name="dont-avoid-locking"></a>Vermeiden Sie nicht die Sperrung

Das Sperren ist eine sehr wichtige Komponente von SQL Server und Common Data Service und ist für einen reibungslosen Betrieb und die Konsistenz des Systems unerlässlich. Aus diesem Grund ist es wichtig, die Auswirkungen auf das Design zu verstehen, insbesondere in Bezug auf die Größe.

## <a name="transaction-usage-nolock-hint"></a>Transaktionsverwendung: Nolock-Hinweis

Eine Funktion der Common Data Service-Plattform, die von Ansichten stark genutzt wird, ist die Möglichkeit, anzugeben, dass eine Abfrage mit einem nolock-Hinweis ausgeführt werden kann, der der Datenbank mitteilt, dass für diese Abfrage keine Sperre erforderlich ist. 

Ansichten verwenden diesen Ansatz, da es keinen direkten Zusammenhang zwischen dem Akt des Startens der Ansicht und nachfolgenden Aktionen gibt. Eine Reihe weiterer Aktivitäten können entweder von diesem Benutzer oder anderen dazwischen ausgeführt werden, und es ist nicht praktisch oder sinnvoll, die gesamte Tabelle der Daten, die die Ansicht anzeigt, zu sperren, bis der Benutzer fortgefahren ist. 

Da eine Abfrage über einen großen Datensatz hinweg bedeutet, dass sie potenziell andere betrifft, die versuchen, mit diesen Daten zu interagieren, kann die Möglichkeit, anzugeben, dass keine Sperre erforderlich ist, einen erheblichen Vorteil für die Skalierbarkeit des Systems haben. 

Wenn Sie eine Abfrage der Plattform über das SDK durchführen, kann es sinnvoll sein, anzugeben, dass nolock verwendet werden kann. Es zeigt an, dass Sie erkennen, dass diese Abfrage keine Lesesperre in der Datenbank setzen muss. Es ist besonders nützlich für folgende Abfragen:

- Es gibt ein breites Spektrum an Daten
- In hohem Maße beanspruchte Ressourcen werden abgefragt
- Serialisierung ist nicht wichtig

Nolock sollte nicht verwendet werden, wenn eine spätere Aktion von keiner Änderung der Ergebnisse abhängt, wie beispielsweise im Beispiel der Sperrung von automatischen Nummerierungen früher. 

Ein Beispielszenario, in dem es nützlich sein kann, ist das Bestimmen, ob eine E-Mail mit einem bestehenden Fall zusammenhängt. Andere Benutzer daran zu hindern, neue Fälle zu erstellen, um sicherzustellen, dass keine Möglichkeit besteht, einen Fall zu generieren, auf den die E-Mail verlinken könnte, wäre keine vorteilhafte Konsistenzprüfung. 

Stattdessen ist es sinnvoller, einen angemessenen Aufwand zu unternehmen, um nach verwandten Fällen zu suchen und die E-Mail an einen bestehenden Fall anzuhängen oder einen neuen zu erstellen, während gleichzeitig andere Fälle generiert werden können. Insbesondere, da es keinen inhärenten Zusammenhang zwischen diesen beiden Aktionen gibt, hätte die E-Mail genauso leicht einige Sekunden früher kommen können und es wäre kein Zusammenhang erkannt worden. 

Ob nolock-Hinweise für ein bestimmtes Szenario gültig sind, würde typischerweise auf einer Beurteilung der Wahrscheinlichkeit und der Auswirkungen von auftretenden Konflikten und der geschäftlichen Auswirkung beruhen, dass die Konsistenz der Aktionen zwischen einem Abruf und nachfolgenden Aktionen nicht gewährleistet ist. Wo keine geschäftlichen Auswirkungen durch die Vermeidung von Verriegelungen auftreten, wäre die Verwendung von Schließungen eine sinnvolle Wahl für die Optimierung. Bei potenziellen geschäftlichen Auswirkungen kann die Konsequenz gegen die Performance- und Skalierbarkeitsvorteile der Vermeidung von Sperrungen abgewogen werden. 

## <a name="consider-order-of-locks"></a>Reihenfolge der Sperren beachten

Ein weiterer Ansatz, der bei der Reduzierung der Auswirkungen von Sperren und insbesondere bei der Vermeidung von Deadlocks nützlich sein kann, ist ein einheitlicher Ansatz für die Reihenfolge der Sperren in einer Implementierung. 

Ein einfaches und häufiges Beispiel ist die Aktualisierung oder Interaktion mit Benutzergruppen. Wenn Sie Anfragen haben, die verwandte Benutzer aktualisieren (z. B. das Hinzufügen von Mitgliedern zu Teams oder das Aktualisieren aller Teilnehmer einer Aktivität), kann die Nichtangabe einer Reihenfolge bedeuten, dass, wenn zwei gleichzeitige Aktivitäten versuchen, dieselben Benutzer zu aktualisieren, Sie das folgende Verhalten zeigen können, was zu einer Deadlock-Situation führt: 

- Transaktion A versucht, Benutzer X und dann Benutzer Y zu aktualisieren
- Transaktion B versucht, Benutzer Y und dann Benutzer X zu aktualisieren

Da beide Anfragen zusammen starten, ist Transaktion A in der Lage, eine Sperre auf Benutzer X zu erhalten und Transaktion B in der Lage, eine Sperre auf Benutzer Y zu erhalten, aber sobald jeder von ihnen versucht, eine Sperre auf den anderen Benutzer zu erhalten, blockieren sie und blockieren dann die Sperre. 

![Problembeispiel: Transaktionssperre](media/order-of-locks-example-1.png)

Durch eine konsistente Anordnung der Ressourcen, auf die Sie zugreifen, können Sie viele Deadlocks vermeiden. Der Bestellmechanismus ist oft unwichtig, solange er konsistent ist und so effizient wie möglich gestaltet werden kann. Beispielsweise kann die Bestellung von Benutzern nach Namen oder sogar nach GUID zumindest eine Konsistenz gewährleisten, die Deadlocks vermeidet.

In einem Szenario, das diesen Ansatz verwendet, würde Transaktion A Benutzer X erhalten, aber Transaktion B würde auch versuchen, Benutzer X und nicht zuerst Benutzer Y zu erhalten. Während das bedeutet, dass Transaktion B sperrt, bis Transaktion A abgeschlossen ist, vermeidet dieses Szenario den Deadlock und wird erfolgreich abgeschlossen.

![Vermeidung von Deadlocks, indem Ressourcen einheitlich angeordnet werden](media/order-of-locks-example-2.png)

In komplexeren und effizienteren Szenarien kann es sein, dass Sie am wenigsten häufig referenzierte Benutzer zuerst und am häufigsten referenzierte Benutzer zuletzt sperren, was zum nächsten Entwurfsmuster führt.

## <a name="hold-contentious-locks-for-shortest-period"></a>Halten Sie konfliktträchtige Sperren für die kürzeste Zeit

Es gibt Szenarien, wie den Ansatz der automatischen Nummerierung, bei denen es keinen Ausweg aus der Tatsache gibt, dass es eine stark beanspruchte Ressource gibt, die gesperrt werden muss. In diesem Fall kann das Blockierungsproblem nicht vollständig vermieden, sondern nur minimiert werden.

Wenn Sie stark beanspruchte Ressourcen haben, ist ein gutes Design, die Interaktion mit dieser Ressource nicht am funktionell logischen Punkt des Prozesses einzubeziehen, sondern die Interaktion mit ihr so nah wie möglich an das Ende der Transaktion zu verschieben. 

Mit diesem Ansatz, obwohl es immer noch eine gewisse Blockierung dieser Ressource geben wird, reduziert er die Zeit, die die Ressource gesperrt ist, und verringert somit die Wahrscheinlichkeit und Zeit, in der andere Anfragen blockiert werden, während sie auf die Ressource warten. 

![Halten Sie konfliktträchtige Sperren für die kürzeste Zeit](media/hold-contentious-locks-for-shortest-period.png)

## <a name="reduce-length-of-transactions"></a>Verkürzung der Länge von Transaktionen

In ähnlicher Weise wird eine Sperre nur dann zu einem Sperrfehler, wenn zwei Prozesse gleichzeitig Zugriff auf die gleiche Ressource benötigen. Je kürzer die Transaktion, die eine Sperre enthält, desto unwahrscheinlicher ist es, dass zwei Prozesse, auch wenn sie auf die gleiche Ressource zugreifen, diese genau zur gleichen Zeit benötigen und eine Kollision verursachen. Je kürzer die Dauer der Transaktionen, desto unwahrscheinlicher wird es, dass die Blockierung zu einem Problem wird.

Im folgenden Beispiel werden die gleichen Sperren verwendet, aber eine andere Verarbeitung innerhalb der Transaktion bedeutet, dass die Gesamtlänge der Transaktion verlängert wird, was zu überlappenden Anfragen für die gleichen Ressourcen führt. Das bedeutet, dass eine Blockierung stattfindet und jede Anforderung insgesamt langsamer ist.

![Problembeispiel: Sperrung wegen zu langer Transaktionslänge](media/reduce-length-of-transactions.png)

Durch die Verkürzung der Gesamtlänge der Transaktion schließt die erste Transaktion ihre Sperren ab und gibt sie frei, bevor die zweite Anforderung überhaupt beginnt, d. h. es gibt keine Sperre und beide Transaktionen werden effizient abgeschlossen. 

Andere Aktivitäten innerhalb einer Anfrage, die die Lebensdauer einer Transaktion verlängern, können die Wahrscheinlichkeit einer Sperrung erhöhen, insbesondere wenn es mehrere sich überschneidende Anfragen gibt, und zu einem deutlich langsameren System führen. 

![Weniger Blockade, da die Dauer der Transaktion verkürzt wird](media/reduce-length-of-transactions-1.png)

Es gibt eine Reihe von Möglichkeiten, die Transaktionslänge zu reduzieren.

## <a name="optimize-requests"></a>Optimieren von Anfragen

Jede Transaktion besteht aus einer Reihe von Datenbankanfragen. Wenn jede Anfrage so effizient wie möglich bearbeitet wird, reduziert dies die Gesamtlänge einer Transaktion und reduziert die Wahrscheinlichkeit von Kollisionen.

Überprüfen Sie jede Abfrage, die Sie stellen, um festzustellen, ob folgendes gegeben ist:

- Ihre Abfrage fragt nur nach dem, was sie benötigt, z.B. Spalten, Datensätze oder Entitätstypen.
  - Dies maximiert die Chance, dass ein Index verwendet werden kann, um die Abfrage effizient zu bedienen
  - Es reduziert die Anzahl der Tabellen und Ressourcen, auf die zugegriffen werden muss, reduziert den Aufwand für andere Ressourcen im Datenbankserver und reduziert die Abfragezeit
  - Es vermeidet mögliche Blockaden von Ressourcen, die Sie nicht benötigen, insbesondere wenn ein Join zu einer anderen Tabelle gewünscht wird, aber vermieden werden könnte oder unnötig ist
- Es gibt einen Index, der die Abfrage unterstützt, Sie fragen auf effiziente Weise ab, und es findet eine Indexsuche statt

  Es ist erwähnenswert, dass die Einführung eines Index nicht verhindert, dass das Erstellen/Aktualisieren von Datensätzen in der zugrunde liegenden Tabelle blockiert wird. Die Einträge in den Indizes werden auch bei der Aktualisierung des Bezugsdatensatzes gesperrt, da der Index selbst Änderungen unterliegt. Die Existenz von Indizes vermeidet dieses Problem nicht vollständig.

Im folgenden Beispiel ist das Abrufen von verwandten Fällen nicht optimiert und erweitert die Gesamttransaktionslänge, wodurch eine Blockierung zwischen den Threads eingeführt wird.

![Abruf von verwandten Fällen nicht optimiert](media/optimize-requests-1.png)

Durch die Optimierung der Abfrage wird der Zeitaufwand für die Ausführung reduziert, und die Wahrscheinlichkeit einer Kollision ist geringer, wodurch die Blockade reduziert wird.

![Abruf von verwandten Fällen optimiert](media/optimize-requests-2.png)

Wenn Sie sicherstellen, dass der Datenbankserver Ihre Anfrage so effizient wie möglich bearbeiten kann, kann die Gesamtzeit Ihrer Transaktionen erheblich verkürzt und das Blockierungspotenzial reduziert werden.

## <a name="reduce-chain-of-events"></a>Verkürzung der Kette von Ereignissen

Wie in früheren Beispielen gezeigt wurde, können die Folgen langer Ketten von Ereignissen einen wesentlichen Einfluss auf die Gesamttransaktionszeit haben und somit das Potenzial zur Sperrung entstehen. Dies gilt insbesondere für das Auslösen von synchronen Plugins und Workflows, die dann andere Aktionen auslösen und wiederum weitere synchrone Plugins und Workflows auslösen.

Die sorgfältige Überprüfung und Gestaltung einer Implementierung, um zu vermeiden, dass lange Ketten von Ereignissen synchron auftreten, kann bei der Reduzierung der Gesamtlänge einer Transaktion von Vorteil sein. Dadurch können eingenommene Sperren schneller freigegeben werden und das Blockierpotential wird reduziert. 

Es reduziert auch die Wahrscheinlichkeit, dass Sekundärsperren zu einem großen Problem werden. Im Beispiel der automatischen Nummerierung bei der Kontoerstellung ist das Hauptproblem zunächst der Zugriff auf die Tabelle der automatischen Nummerierung, aber wenn viele verschiedene Aktionen in einer Sequenz ausgeführt werden, kann auch eine sekundäre Blockade, wie z.B. die Aktualisierung eines zugehörigen Benutzerdatensatzes, auftreten. Sobald mehrere beanspruchte Ressourcen beteiligt sind, wird die Vermeidung von Blockaden noch schwieriger. 

Wenn man bedenkt, ob einige Aktivitäten synchron oder asynchron sein müssen, kann das bedeuten, dass dieselben Aktivitäten erreicht werden, aber weniger anfängliche Auswirkungen haben. Insbesondere bei länger laufenden Aktionen oder solchen, die von stark beanspruchten Ressourcen abhängig sind, kann die Trennung von der Haupttransaktion durch die Ausführung in einer asynchronen Aktion erhebliche Vorteile bringen. Dieser Ansatz wird nicht funktionieren, wenn die Maßnahme mit dem breiteren Plattform-Schritt abgeschlossen oder fehlgeschlagen sein muss, wie z.B. die Aktualisierung eines polizeilichen Kriminalitätsberichts mit dem nächsten Autonummernwert, der sicherstellt, dass ein kontinuierliches, fortlaufendes Nummernschema beibehalten wird. In diesen Szenarien sollten andere Ansätze zur Minimierung der Auswirkungen verfolgt werden. 

Wie das folgende Beispiel zeigt, kann das einfache Verschieben einiger Aktionen in einen asynchronen Prozess, d.h. die Aktionen werden außerhalb der Plattformtransaktion durchgeführt, bedeuten, dass die Länge der Transaktion kürzer ist und das Potenzial für die gleichzeitige Verarbeitung steigt.

![Das Verschieben einiger Aktionen in einen asynchronen Prozess verkürzt die Transaktion](media/reduce-chain-of-events.png)

## <a name="avoid-multiple-updates-to-the-same-record"></a>Vermeiden Sie mehrere Updates für denselben Datensatz

Beim Entwurf mehrerer Schichten funktionaler Aktivität ist es zwar eine gute Praxis, die erforderlichen Aktionen auf logische und leicht nachvollziehbare Aktivitätsabläufe herunterzubrechen, aber in vielen Fällen würde dies zu mehreren, separaten Aktualisierungen desselben Datensatzes führen.
 
Im Fallbehandlungsszenario ist es völlig logisch, zuerst einen Fall mit einem Standardeigentümer zu aktualisieren, der auf dem Kunden basiert, gegen den er erhoben wird, und dann später einen separaten Prozess zu haben, um automatisch Mitteilungen an diesen Kunden zu senden und das letzte Kontaktdatum gegen den Fall zu aktualisieren. 

Die Herausforderung besteht jedoch darin, dass es mehrere Anfragen an Common Data Service gibt, um den gleichen Datensatz zu aktualisieren, was eine Reihe von Auswirkungen hat:

- Jede Anforderung ist ein separates Plattform-Update, das dem Common Data Service-Server eine Gesamtlast zufügt und die Gesamttransaktionslänge verlängert, was die Wahrscheinlichkeit einer Sperrung erhöht.
- Es bedeutet auch, dass der Falldatensatz von der ersten Aktion an gesperrt wird, die an diesem Fall durchgeführt wurde, was bedeutet, dass die Sperre während des gesamten weiteren Verlaufs der Transaktion gehalten wird. Wenn auf den Fall über mehrere parallele Prozesse zugegriffen wird, kann dies zur Sperrung anderer Aktivitäten führen. 

Die Konsolidierung von Aktualisierungen desselben Datensatzes zu einem einzigen Aktualisierungsschritt und später in der Transaktion kann einen erheblichen Vorteil für die allgemeine Skalierbarkeit haben, insbesondere wenn der Datensatz stark umstritten ist oder von mehreren Personen schnell nach der Erstellung aufgerufen wird, z. B. wie bei einem Fall.

Die Entscheidung, ob Aktualisierungen für denselben Datensatz zu einem einzigen Prozess zusammengefasst werden sollen, würde darauf beruhen, die Komplexität der Implementierung gegen das Konfliktpotenzial abzuwägen, das durch separate Aktualisierungen entstehen könnte. Bei Systemen mit hohen Volumina kann dies jedoch für stark umkämpfte Ressourcen von großem Vorteil sein. 

## <a name="only-update-things-you-need-to"></a>Nur Dinge aktualisieren, die Sie benötigen.

Obwohl es wichtig ist, den Nutzen eines Common Data Service-Systems nicht zu verringern, indem Aktivitäten ausgeschlossen werden, die von Vorteil wären, werden oft Anpassungen gefordert, die wenig Geschäftswert schaffen, aber die tatsächliche technische Komplexität erhöhen.
 
Wenn wir jedes Mal, wenn wir eine Aufgabe erstellen, auch den Benutzerdatensatz mit der Anzahl der Aufgaben aktualisieren, die sie derzeit zugewiesen haben, könnte dies zu einer sekundären Sperrebene führen, da der Benutzerdatensatz nun ebenfalls stark beansprucht werden würde. Es würde eine weitere Ressource hinzufügen, die jede Anforderung möglicherweise blockieren und warten muss, obwohl sie nicht unbedingt kritisch für die Aktion ist. In diesem Beispiel sollten Sie sorgfältig prüfen, ob die Speicherung der Anzahl der Aufgaben gegen den Benutzer wichtig ist oder ob die Anzahl bei Bedarf berechnet oder an anderer Stelle gespeichert werden kann, z. B. durch die Verwendung von Hierarchie- und Rollup-Feldfunktionen in Common Data Service. 

![Problembeispiel mit Anzeige unnötiger Updates](media/only-update-things-you-need-to.png)

Wie später gezeigt wird, kann die Aktualisierung der Systembenutzerdatensätze aus Sicht der Skalierbarkeit negative Folgen haben. 

## <a name="multiple-customizations-triggered-on-same-event"></a>Mehrere Anpassungen, die bei gleichem Ereignis ausgelöst werden

Das Auslösen mehrerer Aktionen auf das gleiche Ereignis kann zu einer größeren Kollisionsgefahr führen, da aufgrund der Art der Anforderungen diese Aktionen wahrscheinlich mit denselben verwandten Objekten oder übergeordneten Objekten interagieren.

![Mehrere Anpassungen, die bei gleichem Ereignis ausgelöst werden](media/multiple-triggers-on-same-event.png)

Dies ist ein Muster, das sorgfältig überdacht oder vermieden werden sollte, da es sehr leicht ist, Konflikte zu übersehen, insbesondere wenn verschiedene Personen die verschiedenen Prozesse umsetzen.

## <a name="when-to-use-different-types-of-customization"></a>Wann Sie verschiedene Arten der Anpassung verwenden sollten

Jede Art von Anpassung hat unterschiedliche Auswirkungen auf die Nutzung. Die folgende Tabelle zeigt einige gängige Muster, wann jedes davon berücksichtigt und verwendet werden sollte und wann es nicht geeignet ist.

Häufig muss ein Kompromiss zwischen verschiedenen Verhaltensweisen in Betracht gezogen werden, so dass dies eine Orientierungshilfe für einige der gemeinsamen Merkmale und Szenarien bietet, aber jedes Szenario muss bewertet und der richtige Ansatz basierend auf allen relevanten Faktoren gewählt werden.

|Vor-/Nachlaufphase|Synchron/Asynchron|Art der Anpassung|Verwenden des s|Wann nicht verwenden|
|--|--|--|--|--|
|Vorabprüfung|Synchronisierung|Plug-In|Kurzfristige Validierung von Eingabewerten|Lang laufende Aktionen.<br /><br />Bei der Erstellung verwandter Elemente, die zurückgesetzt werden sollten, wenn spätere Schritte fehlschlagen.|
|Vor Operation|Synchronisierung|Workflow/Plug-in|Kurzfristige Validierung von Eingabewerten.<br /><br />Bei der Erstellung verwandter Elemente, die als Teil des Plattformschrittfehlers zurückgesetzt werden sollten.|Lang laufende Aktionen.<br /><br />Beim Erstellen eines Elements muss die resultierende GUID gegen das Element gespeichert werden, das der Plattformschritt erstellt bzw. aktualisiert.|
|Nach Operation |Synchronisierung|Workflow/Plug-in|Kurz laufende Aktionen, die natürlich dem Plattformschritt folgen und zurückgesetzt werden müssen, wenn spätere Schritte fehlschlagen, z. B. die Erstellung einer Aufgabe für den Eigentümer eines neu erstellten Kontos.<br /><br />Erstellung von zugehörigen Elementen, die die GUID des erstellten Elements benötigen und die im Fehlerfall den Plattformschritt zurücksetzen sollten.|Lang laufende Aktionen.<br /><br />Wo ein Versagen die Fertigstellung der Plattform-Pipeline nicht beeinträchtigen sollte.|
|Nicht in Ereignis-Pipeline|Asynchron|Workflow/Plug-in|Mittelgroße Aktionen, die sich auf die Benutzerfreundlichkeit auswirken würden.<br /><br />Aktionen, die im Fehlerfall ohnehin nicht zurückgenommen werden können.<br /><br />Aktionen, die das Zurücksetzen des Plattformschritts im Falle eines Ausfalls nicht erzwingen sollten.|Sehr lang laufende Aktionen.<br /><br />Diese sollte nicht im Common Data Service verwaltet werden.<br /><br />Sehr kostengünstige Aktionen. Der Aufwand für die Generierung von asynchronem Verhalten für sehr kostengünstige Aktionen kann untragbar sein; wenn möglich, synchronisieren Sie diese und vermeiden Sie den Aufwand der asynchronen Verarbeitung.|
|Nicht zutreffend<br />Verwendet den Kontext, von dem aus er aufgerufen wird.||Benutzerdefinierte Aktionen|Kombinationen von Aktionen, die von einer externen Quelle gestartet wurden, z. B. von einer Web-Ressource.|Wenn immer als Reaktion auf ein Plattformereignis ausgelöst, verwenden Sie in diesen Fällen Plug-in/Workflow.|

## <a name="plug-insworkflows-arent-batch-processing-mechanisms"></a>Plug-Ins/Workflows sind keine Batch-Verarbeitungsmechanismen.

Lang laufende oder Volume-Aktionen sind nicht dazu gedacht, von Plug-Ins oder Workflows ausgeführt zu werden. Common Data Service ist nicht als Berechnungsplattform gedacht und insbesondere nicht als Controller, um große Gruppen von unabhängigen Updates anzusteuern.

Wenn Sie dies tun müssen, entlasten Sie einen separaten Dienst, z. B. eine Azure-Worker-Rolle, und führen Sie ihn aus. 

## <a name="setting-up-security"></a>Einrichten der Sicherheit

Ein sehr häufiger Eskalationsbereich ist die Skalierbarkeit der Sicherheitseinrichtungen. Dies ist eine kostspielige Angelegenheit, sodass, wenn sie in großen Mengen durchgeführt wird, immer wieder Herausforderungen entstehen können, wenn sie nicht verstanden und sorgfältig überlegt werden. 

### <a name="team-setup"></a>Teameinrichtung

- Fügen Sie Benutzer immer in der gleichen Reihenfolge hinzu: vermeiden Sie Deadlocks.
- Nur Benutzer aktualisieren, wenn sie aktualisiert werden müssen: Vermeiden Sie es, die Caches der Benutzer unnötig zu invalidieren.

### <a name="owner-v-access-teams"></a>Eigentümer v. Auf Teams zugreifen

- Wenn sich die Teams der Benutzer regelmäßig ändern, achten Sie darauf, dass die Eigentümer-Teams stark genutzt werden; jedes Mal, wenn sie sich ändern, invalidieren sie den Cache des Benutzers im Webserver.
- Idealerweise Änderungen vornehmen, wenn der Benutzer nicht arbeitet, Auswirkungen reduzieren, z. B. über Nacht.

### <a name="lots-of-team-memberships-bus"></a>Viele Teammitgliedschaften/BUs

- Betrachten Sie sorgfältig Szenarien mit vielen Teams/Einheiten, die die Komplexität der Kalkulation erhöhen

### <a name="cascading-behavior"></a>Kaskadierende Verhaltensweise

- Betrachten Sie die kaskadierende gemeinsame Nutzung, z.B. die Zuweisung

### <a name="careful-updating--of-user-records"></a>Sorgfältige Aktualisierung der Benutzerdatensätze

- Aktualisieren Sie die Systembenutzerdatensätze nicht regelmäßig, es sei denn, es hat sich etwas grundlegendes geändert, da dies dazu führt, dass der Benutzer-Cache neu geladen und die Sicherheitsprivilegien neu berechnet werden müssen, was eine teure Aktivität ist.
- Verwenden Sie den Systembenutzer nicht, um aufzuzeichnen, wie viele offene Aktivitäten der Benutzer hat, z. B.

## <a name="diagram-related-actions"></a>Diagrammbezogene Aktionen

Eine Aktivität, die sowohl als vorbeugende Maßnahme als auch als Werkzeug zur Diagnose von Blockierungsproblemen sehr nützlich ist, ist die Darstellung von Aktionen, die in der Common Data Service-Plattform ausgelöst werden. Dabei hilft es, sowohl absichtliche als auch unbeabsichtigte Abhängigkeiten und Auslöser im System hervorzuheben. Wenn Sie dies für Ihre Lösung nicht tun können, haben Sie möglicherweise kein klares Bild davon, was Ihre Implementierung tatsächlich tut. Die Erstellung eines solchen Diagramms kann unbeabsichtigte Folgen haben und ist in einer Implementierung jederzeit eine gute Praxis. 

Das folgende Beispiel verdeutlicht, wie zunächst zwei Prozesse perfekt zusammenwirken, aber in der laufenden Wartung kann die Hinzufügung eines neuen Schrittes zum Anlegen einer Aufgabe eine unbeabsichtigte Schleife erzeugen. Die Verwendung dieser Dokumentationstechnik kann dies bereits bei der Konstruktion hervorheben und eine Beeinträchtigung des Systems vermeiden.

![Diagrammbezogene Aktionen](media/diagram-related-actions.png)

<!-- NOTE: Excluding content on isolation modes and transaction diagnosis as it is for on-premises only. -->

## <a name="review-system-captured-statistics"></a>Überprüfung der vom System erfassten Statistiken

Es gibt eine Reihe von Möglichkeiten, festzustellen, was passiert, wenn das Problem außerhalb der Datenbankschicht auftritt. Die erste ist die Analyse der Plugin-Performance. Die [PluginTypeStatistic Entity](../reference/entities/plugintypestatistic.md) kann abgefragt werden, um einen Hinweis darauf zu geben, wie oft das Plugin ausgeführt wird, und Statistiken darüber, wie lange es normalerweise dauert.

Wenn bestimmte Fehler auftreten, kann es auch nützlich sein, die Server-Trace-Dateien zu verwenden, um zu verstehen, wo verwandte Probleme auf der Plattform auftreten können. Weitere Informationen: [Verwenden der Ablaufverfolgung](../debug-plug-in.md#use-tracing)

## <a name="summary"></a>Zusammenfassung

Der Inhalt in [Skalierbare Anpassungsgestaltung in Common Data Service](overview.md) und die nachfolgenden Themen [Datenbanktransaktionen](database-transactions.md) und [Parallelitätsprobleme](concurrency-issues.md) haben die folgenden Konzepte mit Beispielen und Strategien beschrieben, die Ihnen helfen werden, zu verstehen, wie Sie skalierbare Anpassungen für Common Data Service entwerfen und implementieren.

Einige wichtige Dinge, die Sie beachten sollten, sind die folgenden: 

### <a name="locks-transactions"></a>Sperren/Transaktionen

- Sperren und Transaktionen sind für ein funktionierendes System unerlässlich
- Bei falscher Anwendung kann es jedoch zu Problemen kommen

### <a name="platform-constraints"></a>Plattformbeschränkungen

- Plattformbeschränkungen zeigen sich oft in Form von Fehlern
- Aber selten ist die Einschränkung die Ursache des Problems
- Sie sind dazu da, die Plattform und andere Aktivitäten vor Beeinträchtigungen zu schützen

### <a name="design-for-transaction-use"></a>Design für die Transaktionsnutzung

- Wenn Implementierungen im Hinblick auf das Transaktionsverhalten entwickelt werden, kann dies zu einer wesentlich höheren Skalierbarkeit und einer verbesserten Benutzerperformance führen.
