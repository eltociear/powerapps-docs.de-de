---
title: 'Skalierbares Anpassungsdesign: Beispiel für automatische Nummerierung (Common Data Service for Apps) | Microsoft Docs'
description: 'Dieses Beispiel veranschaulicht, wie Transaktionen und Probleme mit der Parallelität in einer Codeanpassung berücksichtigt werden müssen.'
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
# <a name="scalable-customization-design-auto-numbering-example"></a>Skalierbares Anpassungsdesign: Beispiel für automatische Nummerierung

> [!NOTE]
> Dieses Beispiel unterstützt eine Reihe von Themen über skalierbares Anpassungsdesign. Um am Anfang zu beginnen, siehe [Skalierbares Anpassungsdesign im Common Data Service für Apps](overview.md).

Ein Szenario, das das häufige Missverständnis veranschaulicht, wie Transaktionen innerhalb von CDS for Apps behandelt werden, ist die Implementierung eines automatischen Nummerierungssystems.

In diesem Szenario ist die Anforderung typischerweise zu:

- Generieren Sie eine eindeutige Nummer nach einem bestimmten Muster.
- Ermöglichen Sie es vielen gleichzeitigen Anfragen, den zugehörigen Typ von Datensätzen zu erstellen, z. B. Konten, die eine eindeutige Referenz benötigen.
- Ermöglicht die fortlaufende Nummerierung der eindeutigen Nummern.
- Stellen Sie sicher, dass die Nummerngenerierung konsistent, aber skalierbar ist und unter Last nicht ausfällt. Sie muss auch sicherstellen, dass keine doppelten Nummern erzeugt werden können.
- Generieren Sie die Nummer beim Anlegen des entsprechenden Datensatzes.

Der typische Ansatz besteht aus folgenden Variationen:

- Speichern Sie die zuletzt verwendete Nummer in einem Auto-Nummer-Indexdatenspeicher, z. B. eine benutzerdefinierte Entität mit einer Zeile pro Datentyp.
- Rufen Sie die zuletzt verwendete Zahl ab und erhöhen Sie diese Zahl.
- Notieren Sie die neue Nummer gegen den neu erzeugten Datensatz.
- Speichern Sie die neue Nummer wieder als die zuletzt verwendete Nummer im automatischen Nummernverzeichnisspeicher.

Die folgenden Abschnitte beschreiben verschiedene Ansätze, die innerhalb von CDS für Apps angewendet werden können, und heben die Auswirkungen hervor, indem sie sowohl die Bedeutung als auch den Nutzen des Verständnisses der Art und Weise, wie Transaktionen verwendet werden, verdeutlichen. 

## <a name="approach-1-out-of-a-transaction"></a>Ansatz 1: Aus einer Transaktion heraus

Der einfachste Ansatz besteht darin, zu erkennen, dass jede Nutzung einer häufig benötigten Ressource das Potenzial für eine Blockade mit sich bringen würde. Da dies einen Einfluss auf die Skalierbarkeit hat, können Sie entscheiden, ob Sie bei der Generierung einer Autonummer eine Plattformtransaktion vermeiden möchten.
Betrachten wir das Szenario für die automatische Generierung von Nummerierungen außerhalb der Pipelinetransaktion in einem Pre-Validierungs-Plugin.

![Ansatz 1: Aus einer Transaktion heraus](media/autonumber-approach-1.png)

Wenn Sie dies isoliert ausführen, funktioniert es einwandfrei. Es schützt jedoch nicht wirklich vor Gleichzeitigkeitsfehlern. Wie das folgende Diagramm zeigt, werden Sie, wenn zwei parallele Anfragen sowohl die neueste Nummer anfordern als auch den Wert erhöhen und aktualisieren, doppelte Zahlen erhalten. Da keine Sperre gegen die abgerufene Nummer gehalten wird, ist es möglich, dass eine Race Condition auftritt und beide Threads den gleichen Wert haben. 

![Race-Bedingung](media/autonumber-approach-1-a.png)

In vielen Fällen, auch wenn mehrere Anfragen auftreten können, könnte dies aufgrund des begrenzten Zeitfensters für Überschneidungen gut funktionieren, aber es verlässt sich eher auf Glück als auf gutes Design, um die Doppelung zu verhindern.

## <a name="approach-2-in-a-plug-in-transaction"></a>Ansatz 2: In einer Plug-In-Transaktion

Wenn Sie die automatische Nummerierung von einem in der Transaktion registrierten Plug-in (txn) vornehmen, funktioniert das sicher ... richtig?

![Ansatz 2: In einer Plug-In-Transaktion](media/autonumber-approach-2.png)

Unter den gleichen Umständen, in denen sich überschneidende Anfragen, die versuchen, gleichzeitig Nummern zu generieren, wäre es möglich, beiden Anfragen eine Lesesperre in der automatischen Nummerierungstabelle zu gewähren. Leider ist dies an dem Punkt, an dem die Anwendung versucht, dies zu einer exklusiven Sperre zu aktualisieren, nicht möglich, da eine andere gemeinsame Lesesperre dies verhindern würde.

![gemeinsame Lesesperre verhindert Zugriff](media/autonumber-approach-2-a.png)

Abhängig davon, wie die Abfragen generiert werden, kann das genaue Verhalten variieren, aber sich auf diese Bedingungen zu verlassen und sich nicht sicher zu sein, wo die Einzigartigkeit wesentlich ist, ist nicht ideal. Selbst wenn dies keinen Fehler verursacht, könnte die gemeinsame Lesefähigkeit es ermöglichen, eine doppelte Nummer zu erzeugen, wenn die Isolationsmodi nicht korrekt sind. Wie das folgende Diagramm zeigt, erhalten beide Datensätze den gleichen Autonummernwert von 8.

![beide Datensätze enden mit dem gleichen Wert für die automatische Nummerierung](media/autonumber-approach-2-b.png)

## <a name="approach-3-pre-lock-in-a-plug-in-transaction"></a>Ansatz 3: Pre-Lock in einer Plug-In-Transaktion

Das Verständnis der Funktionsweise der Transaktionen führt dazu, dass man einen sicheren Weg finden kann, dies zu tun. 

Bei diesem Ansatz wird von Beginn der Transaktion an ein Platzhalter-Update für den automatischen Nummerierungssatz in ein Feld (z. B. UpdateInProgress) durchgeführt, das ausschließlich aus Gründen der Konsistenz verwendet wird. Dies geschieht durch das Schreiben eines Updates, das anzeigt, dass ein Update im Begriff ist, zu starten. Dieser Prozess fordert dann eine exklusive Schreibsperre für diese Zeile in der automatischen Nummerierungstabelle an und blockiert damit andere Prozesse daran, die automatische Nummerierung zu starten. 

Dies ermöglicht es Ihnen dann, die aktualisierte Autonummer sicher zu erhöhen und zurückzuschreiben, ohne dass ein anderer Prozess eingreifen kann. 

![Ansatz 3: Pre-Lock in einer Plug-In-Transaktion](media/autonumber-approach-3.png)

Es hat die Implikation, dass dies nicht nur die Aktualisierungen der automatischen Nummerierung, sondern auch die Anforderungen an die Kontoerstellung serialisiert, da diese beiden Schritte in derselben Plattformtransaktion stattfinden. Wenn die Erstellung von Konten schnelle Aktionen sind, dann kann das ein perfekter Ansatz sein und stellt sicher, dass die Kontoerstellung und die automatische Nummerierung konsistent durchgeführt werden; wenn man scheitert, scheitern sie beide und rollen zurück.
 
In der Tat, wenn die anderen Aktionen innerhalb der Transaktion schnell sind, ist dies der konsistenteste und effizienteste Ansatz zur Implementierung der automatischen Nummerierung in Anpassungen. 

Wenn Sie jedoch auch andere synchrone Plugins oder Workflows einführen, die jeweils längere Zeit in Anspruch nehmen, kann die Serialisierung zu einer echten Skalierbarkeitsherausforderung werden, da der automatische Nummerierungsprozess nicht nur sich selbst blockiert, sondern auch das Warten auf die Fertigstellung der anderen Aktivitäten blockiert. 

![Auto-Nummerierungsprozess blockiert sich nicht nur selbst, sondern blockiert auch das Warten auf den Abschluss der anderen Aktivitäten](media/autonumber-approach-3-a.png)

Normalerweise wird die Generierung der Autonummer in einem Pre-Event Plug-in durchgeführt. Sie nehmen die Nummer in die Eingabeparameter des Erstellungsschrittes auf und vermeiden eine zweite Aktualisierung in der Nachbearbeitung, um die generierte Autonummer gegen das Konto aufzuzeichnen.

Unter Berücksichtigung der Auswirkungen der Skalierbarkeit wäre eine Alternative, wenn es eine andere komplexe Verarbeitung im Kontoerstellungsprozess gibt, die automatische Nummerngenerierung in einen Post-Erstellungsprozess zu verschieben, der dennoch einen konsistenten Aktualisierungsprozess gewährleistet. Der Vorteil wäre, dass es die Zeit innerhalb der Transaktion verkürzt, dass die automatische Nummernaufzeichnungssperre gehalten wird, da die Sperre erst gegen Ende des Prozesses durchgeführt wird. Wenn die automatische Nummerierungstabelle die am stärksten umstrittene Ressource ist und dieser Ansatz für alle Prozesse, die auf sie zugreifen, gewählt wird, reduziert dies die Anzahl der Streitigkeiten insgesamt.

Der Kompromiss wäre hier die Notwendigkeit, eine zusätzliche Aktualisierung des Kontos durchzuführen und gleichzeitig die Gesamtzeit zu verkürzen, die das Warten auf den Datensatz der automatischen Nummerierung blockiert.

![Verschieben der automatischen Nummerngenerierung in einen Post-Erstellungsprozess](media/autonumber-approach-3-b.png)
