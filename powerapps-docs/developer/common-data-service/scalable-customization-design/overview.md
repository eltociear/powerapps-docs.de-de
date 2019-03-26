---
title: 'Skalierbares Anpassungsdesign: Übersicht (Common Data Service for Apps) | Microsoft Docs'
description: 'Das erste in einer Reihe von Themen. In diesem Thema werden Symptome vorgestellt, die auftreten können, wenn Code-Anpassungen nicht optimiert werden, und die Einschränkungen, die Code-Anpassungen innerhalb derer durchführen müssen, um sie zu vermeiden. '
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
# <a name="scalable-customization-design-in-common-data-service-for-apps"></a>Skalierbares Anpassungsdesign in Common Data Service for Apps

> [!NOTE]
> Dies ist der erste in einer Reihe von Themen über skalierbares Anpassungsdesign. Obwohl dieser Inhalt in einzelne Themenbereiche unterteilt wurde, bietet er einen ganzheitlichen Überblick über Konzepte, Probleme und Strategien rund um das Design skalierbarer Anpassungen. Jedes Thema baut auf den Konzepten der vorangegangenen Themen auf.
> Sie können diese [Themen als einzelnes PDF-Dokument herunterladen](/powerapps/opbuildpdf/developer/common-data-service/scalable-customization-design/TOC.pdf?branch=live), wenn Sie sie offline lesen möchten.

Common Data Service for Apps (CDS for Apps) wurde entwickelt, um sich und seine Benutzer vor lang laufenden Aktivitäten zu schützen, die sowohl die Antwortzeiten für den anfragenden Benutzer als auch die Stabilität und Reaktionsfähigkeit des Systems für andere Benutzer beeinflussen könnten.

Eine Herausforderung für einige Anwender bei der Implementierung von CDS for Apps-Lösungen sind Fehler, die von der Plattform oder der zugrunde liegenden Microsoft SQL Server-Datenbank verursacht werden, wenn diese Schutzmaßnahmen wirksam werden. Dies wird oft als die Plattform interpretiert, die nicht in der Lage ist, Anfragen an das System zu skalieren oder falsch zu terminieren oder zu drosseln.

Dieser Inhalt basiert auf Erfahrungen, die die wahren Ursachen der meisten dieser Arten von Herausforderungen untersuchen und angehen. Diese Themen beschreiben, wie sich die Plattform vor den Auswirkungen dieser Anforderungen an das System schützt und erklären, warum dieses Verhalten meist das Ergebnis von benutzerdefinierten Implementierungen ist, die die Auswirkungen auf die Blockierung und Transaktionsnutzung innerhalb der Plattform nicht verstehen.

Dieser Inhalt beschreibt auch, wie die Optimierung einer benutzerdefinierten Implementierung zur Vermeidung solcher Verhaltensweisen nicht nur Plattformfehler vermeidet, sondern auch eine bessere Leistung und damit eine bessere Benutzerfreundlichkeit ermöglicht. Es bietet gute Designpraktiken und identifiziert häufige Fehler, die es zu vermeiden gilt.

## <a name="the-challenge"></a>Die Herausforderung

Die Untersuchung und Bewältigung der Herausforderungen in diesem Bereich beginnt in der Regel dann, wenn bestimmte Arten von Fehlern und Symptomen im System auftreten. Diese werden oft als Probleme auf der Plattform wahrgenommen, und der notwendige Abhilfeschritt besteht darin, die Plattformbeschränkungen zu lockern, die typischerweise dazu führen, dass eine langsam laufende Anforderung zu einem gemeldeten Fehler wird.

In Wirklichkeit könnten die Fehler zwar kurzfristig vermieden werden, indem einige der Plattformbeschränkungen gelockert werden, aber diese Beschränkungen gibt es aus guten Gründen und sollen verhindern, dass eine zu lange laufende Aktion andere Benutzer oder die Systemleistung beeinträchtigt. Während die Einschränkungen gelockert werden konnten, um die Fehler zu vermeiden, würden die Benutzer immer noch langsame Reaktionszeiten erleben, was sich auch auf die Erfahrung anderer Benutzer mit dem System auswirken würde.

Daher ist es vorzuziehen, die Ursachen dafür zu untersuchen, warum diese Einschränkungen ausgelöst werden und Fehler verursachen, und dann die Codeanpassungen zu optimieren, um sie zu vermeiden. Dies wird ein konsistenteres und reaktionsschnelleres System für die Benutzer ermöglichen. 

### <a name="common-symptoms"></a>Häufige Symptome

Diese Art von Problemen weist typischerweise eine Kombination von häufigen Symptomen auf, wie in der folgenden Tabelle dargestellt.

|Symptom|Beschreibung|
|--|--|
|**Langsame Abfragen**|Benutzer sehen langsame Antwortzeiten für das System in bestimmten Bereichen, z. B. bestimmte Formulare und Abfragen.|
|**Generische SQL-Fehler**|Bestimmte Aktionen reagieren mit einem Plattformfehler, der einen Generic SQL Error meldet. <br />Dies übersetzt sich oft auf einer Plattformebene in einen SQL-Timeout.|
|**Deadlocks**|Plattformfehler, die melden, dass ein Deadlock aufgetreten ist, was dazu geführt hat, dass die Aktion beendet und zurückgesetzt wurde.|
|**Begrenzter Durchsatz**|Gerade in Batch-Load-Szenarien zeigt sich dies oft darin, dass ein wirklich langsamer Durchsatz erreicht wird, viel langsamer als es möglich sein sollte.|
|**Intermittierende Fehler / langsame Leistung**|Ein wichtiger Indikator für dieses Verhalten ist, dass die gleiche Aktion sehr schnell oder unglaublich langsam sein kann, und ein erneuter Versuch funktioniert viel schneller oder vermeidet einen Fehler.|

In Wirklichkeit kann und wird eine Kombination dieser Symptome oft zusammen gemeldet, wenn diese Herausforderungen auftreten. Es ist nicht immer der Fall, dass diese Symptome ein Indikator für Probleme mit dem Design sind. Andere Probleme, wie z.B. Einschränkungen der Festplatten-I/O in der Datenbank oder ein Produktfehler, können ähnliche Symptome verursachen. Aber die häufigste Ursache für diese Art von Symptomen, und damit eine, auf die es sich zu prüfen lohnt, bezieht sich direkt auf das Design der benutzerdefinierten Implementierung und wie sie sich auf das System auswirkt. 

> *Warum sollten wir uns Sorgen machen? Kümmert sich CDS for Apps nicht einfach darum ...?*

Es tut, was es kann... Aber es verwendet Sperren und Transaktionen, um das System bei Bedarf vor Konflikten zu schützen.

Wir bieten Ihnen auch die Möglichkeit, Entscheidungen über Ihr spezielles Szenario zu treffen und zu entscheiden, wo es wichtig ist, den Zugriff auf Daten zu kontrollieren. Aber diese Entscheidungen können falsch getroffen werden, und es ist möglich, unbeabsichtigte Konsequenzen in benutzerdefinierten Code einzubringen. Diese Probleme haben typischerweise Auswirkungen auf die Benutzerfreundlichkeit durch langsamere Reaktionszeiten, so dass das Verständnis der Auswirkungen bestimmter Aktionen zu konsistenteren und besseren Ergebnissen für die Benutzer führen kann.

## <a name="understanding-causes"></a>Ursachen verstehen

Häufige Symptome haben Ursachen, die dazu führen, dass bestimmte Anforderungen langsam laufen und dann Plattformbeschränkungen auslösen. Das folgende Diagramm zeigt typische Symptome mit einigen der häufigsten Ursachen dieser Symptome.

![Ursachen verstehen](media/understanding-causes.png)

Die zugrunde liegenden Auswirkungen von lang laufenden Transaktionen, Datenbankblockaden und komplexen Abfragen können sich alle überschneiden und ihre Auswirkungen verstärken, um diese Symptome zu verursachen. Beispielsweise kann eine Reihe von lang laufenden Abfragen, die völlig unabhängig voneinander sind, zu langsamen Benutzerreaktionszeiten führen, aber erst wenn sie Zugriff auf die gleichen Ressourcen benötigen, werden die Reaktionszeiten so langsam, dass sie zu Fehlern werden. 

## <a name="design-for-platform-constraints"></a>Design für Plattformbeschränkungen

Die CDS for Apps-Plattform hat eine Reihe von bewussten Einschränkungen, die sie auferlegt, um zu verhindern, dass eine einzelne Aktion zu schädliche Auswirkungen auf den Rest des Systems und damit auf die Benutzer hat. Während dieses Verhalten frustrierend sein kann, da es das Abschließen spezifischer Anfragen blockieren kann und oft zu Fragen darüber führt, ob die Beschränkungen aufgehoben werden können, ist dies selten ein guter Ansatz, wenn man die breiteren Auswirkungen betrachtet.

Wenn die Plattform bestimmungsgemäß genutzt und eine Implementierung optimiert wird, ist es sehr selten, dass es ein Szenario gibt, in dem diese Einschränkungen auftreten würden. Das Ausführen der Einschränkung ist fast immer ein Hinweis auf Verhaltensweisen, die Ressourcen im System übermäßig binden. Dies bedeutet, dass andere Anfragen entweder vom gleichen Benutzer oder von anderen Benutzern nicht bearbeitet werden können. Während es also möglich ist, die Einschränkung der zu blockierenden Anforderung zu lockern, bedeutet das eigentlich, dass die Ressourcen, die sie verbraucht, noch länger gebunden sind und größere Auswirkungen auf andere Benutzer haben.

Im Mittelpunkt dieser Einschränkungen steht die Idee, dass die CDS for Apps-Plattform so konzipiert ist, dass sie eine transaktionale Mehrbenutzeranwendung unterstützt, bei der eine schnelle Reaktion auf die Benutzernachfrage im Vordergrund steht. Es ist nicht als Plattform für Langzeit- oder Stapelverarbeitung gedacht. Es ist möglich, eine Reihe von kurzen Anfragen an CDS for Apps zu senden, aber CDS for Apps ist nicht für die Stapelverarbeitung ausgelegt. Ebenso ist CDS for Apps bei Aktivitäten mit großer iterativer Verarbeitung nicht für diese iterative Verarbeitung ausgelegt.

In diesen Szenarien kann ein separater Dienst verwendet werden, um den lang laufenden Prozess zu hosten und kürzere transaktionale Anfragen an CDS for Apps selbst zu leiten. Beispielsweise ist es viel besser, Flow zu verwenden oder Microsoft SQL Server Integration Services (SSIS) anderweitig zu hosten und dann einzelne Erstellungs- oder Aktualisierungsanforderungen an CDS for Apps zu leiten, als mit einem Plug-in Tausende von Datensätzen, die in CDS for Apps erstellt werden, durchzugehen.

Es lohnt sich, die vorhandenen Plattformbeschränkungen zu kennen und zu verstehen, damit Sie sie in Ihrem Anwendungsdesign berücksichtigen können. Auch wenn Sie auf diese Fehler stoßen, können Sie verstehen, warum sie passieren und was Sie ändern können, um sie zu vermeiden.

|Einschränkung|Beschreibung|
|--|--|
|**Plug-in-Zeitüberschreitungen**|&bull; Plug-In-Timeout nach 2 Minuten <br />&bull; Führen Sie keine lang laufenden Operationen in Plug-Ins durch. Schützt die Plattform und den Sandbox-Service und letztendlich den Benutzer vor einer schlechten Benutzererfahrung|
|**SQL-Zeitüberschreitungen**|&bull; Anfragen an SQL Server Timeout bei 30 Sekunden<br />&bull; Schützt vor lang laufenden Anfragen<br />&bull; Bietet Schutz innerhalb eines bestimmten Unternehmens und seiner privaten Datenbank<br />&bull; Bietet auch Schutz auf der Ebene des Datenbankservers vor übermäßiger Nutzung gemeinsamer Ressourcen wie Prozessoren/Speicher|
|**Workflow-Begrenzungen**|&bull; arbeitet nach einer Richtlinie für eine faire Nutzung.<br />&bull; Keine spezifischen harten Grenzen, sondern Ressourcenausgleich zwischen Unternehmen<br />&bull; Bei geringer Nachfrage kann ein Unternehmen die verfügbare Kapazität voll ausschöpfen. Bei hoher Nachfrage werden Ressourcen und Durchsatz geteilt.|
|**Maximale gleichzeitige Verbindungen**|&bull; Es gibt eine Plattformvoreinstellung für eine maximale Verbindungspoolgrenze von 100 Verbindungen aus dem Webserver-Verbindungspool im IIS zur Datenbank. CDS for Apps ändert diesen Wert nicht<br />&bull; Wenn Sie darauf treffen, ist es ein Hinweis auf einen Fehler im System; schauen Sie sich an, warum so viele Verbindungen blockieren.<br />&bull; Bei mehreren Webservern mit jeweils 100 gleichzeitigen Verbindungen zur Datenbank mit typischen &lt; 10ms schlägt dies einen Durchsatz von &gt; 10k Datenbankanforderungen für jeden Webserver vor. Dies sollte nicht erforderlich sein und würde andere Herausforderungen schon lange vorher treffen.|
|**ExecuteMultiple**|&bull; Die Nachricht `ExecuteMultiple` wurde entwickelt, um die Sammlung von Vorgängen zu unterstützen, die an CDS for Apps von einer externen Quelle gesendet werden.<br />&bull; Die Verarbeitung großer Gruppen dieser Anfragen kann wichtige Ressourcen im CDS für Apps auf Kosten von mehr antwortkritischen Anfragen von Benutzern binden, daher ist dies auf 2 gleichzeitige `ExecuteMultiple`-Anfragen pro Unternehmen beschränkt.|

## <a name="next-steps"></a>Nächste Schritte

Um zu verstehen, wie die Plattformbeschränkungen angewendet werden, ist es notwendig, Datenbanktransaktionen zu verstehen. Mehr Informationen: [Skalierbares Anpassungsdesign: Datenbanktransaktionen](database-transactions.md)


