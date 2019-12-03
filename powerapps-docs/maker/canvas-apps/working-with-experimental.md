---
redirect_url: working-with-experimental-preview
title: Grundlegendes zu experimentellen, Vorschau-und experimentellen Features | Microsoft-Dokumentation
description: Testen Sie neue Features, und übernehmen Sie diese nach und nach.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/08/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 618192bcaafa5fef8ce2577dc5f07548d49f005e
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74732303"
---
# <a name="understand-experimental-preview-and-deprecated-features-in-power-apps"></a>Verstehen von experimentellen, Vorschau und veralteten Features in Power apps

Mit jeder Version nehmen wir Änderungen vor und fügen Features hinzu, damit Power apps das beste Tool ist, das Ihren Anforderungen entspricht. Wir verbessern das Produkt kontinuierlich.  

Abwärtskompatibilität ist ein sehr wichtiger Aspekt für uns. Es kann jedoch vorkommen, dass durch eine Änderung oder eine Verbesserung unbeabsichtigte Nebeneffekte auftreten und Ihre App nicht mehr wie bisher funktioniert.

Größere Features durchlaufen mehrere Phasen, um Verbesserungen und Auswirkungen auf vorhandene Apps gegeneinander abwägen zu können. In diesem Artikel wird dieser Prozess beschrieben. Außerdem erfahren Sie, wie Sie mit in der Entwicklungsphase befindlichen Features umgehen können.

## <a name="feature-roll-out-stages"></a>Einführungsphasen von Features

Features durchlaufen drei verschiedene Phasen, bevor sie offizieller Bestandteil des Produkts werden:

1. **Experimentell:** Das Feature befindet sich noch in der Bearbeitung. Verlassen Sie sich nicht auf dieses Feature. Es kann sein, dass es sich noch deutlich verändert.
1. **Vorschau:** Das Feature ist fast fertig und funktioniert stabil. Sie können mit der Migration vorhandener Apps beginnen.
1. **Ausgeliefert:** Das Feature ist fertig. Das Feature ist für alle Apps aktiviert, und Sie können es nicht deaktivieren.

In jeder Phase erhöht sich die Anzahl der Personen, die das Feature verwenden, und unterstützt wir dabei, zu überprüfen, ob das Feature für Sie erforderlich ist, und dass keine unbeabsichtigten Nebeneffekte eingeführt werden.

**Für diesen Prozess ist Ihr Feedback wesentlich.**  Senden Sie Ihr Feedback im [Community-Forum für Power apps](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1).

Wie lange befindet sich ein Feature in einer der oben genannten Phasen? Das kann sich von Feature zu Feature unterscheiden. Dabei werden sehr viele Faktoren berücksichtigt, z.B. die Anzahl der Apps, die das Feature verwenden, die Anzahl der gemeldeten Probleme und die Dringlichkeit des Features. Features können sich Wochen aber auch Monate in einer Phase befinden.  Wir können auch einige Phasen überspringen, wenn wir nicht glauben, dass es hilfreich wäre.

Anhand dieser Tabelle können Sie entscheiden, wann es für Sie am sinnvollsten ist, mit der Verwendung von Features zu beginnen: 

| Phase | Wann sollte ich Sie verwenden? | Ist es zuverlässig?  Ist es standardmäßig für neue Apps aktiviert? | 
|----|----|----|
| **Experimentell** | Wenn Sie ein Early Adopter sind, ein Feature nützlich für Sie sein könnte, oder Sie beim Testen des Features helfen möchten | Nein. Experimentelle Features können sich noch deutlich verändern oder im Laufe der Zeit wieder vollständig verschwinden. Aus diesem Grund ist die Funktion standardmäßig nicht aktiviert, und Sie müssen die Verwendung explizit aktivieren. |  
| **Vorschau** | Neue Apps enthalten diese Funktion automatisch, aber Sie können trotzdem ausgeschaltet werden.  Sie können das Feature in vorhandenen Apps aktivieren und testen, da es irgendwann auch für vorhandene Apps aktiviert wird.  |Ja.  Dieses Feature soll ein permanenter Bestandteil des Produkts werden. Sie sollten es deaktivieren, wenn ein Problem auftritt.  Melden Sie uns diese Probleme, denn genau aus diesem Grund befindet sich das Feature noch in der Vorschauphase.  | 
| **Vorschau (abschließende&nbsp;Validierung)** | Für einige Features, die weitreichende Auswirkungen haben würden, können wir den zusätzlichen Schritt über die **Vorschau** Version hinaus machen, indem wir den Funktions Wechsel für vorhandene apps auf einmal erzwingen, wenn Sie in Studio geöffnet werden.  Wenn ein Problem auftritt, kann die Funktion weiterhin ausgeschaltet werden, und Ihr Feedback ist wichtig, bevor wir den nächsten Schritt ausführen. | Ja. Diese Funktion kann mit Sicherheit verwendet werden, es ist jedoch sehr nahe, dauerhaft zu werden. Sie sollten es deaktivieren, wenn ein Problem auftritt.  Melden Sie alle auftretenden Probleme. |
| **Ausgeliefert** für&nbsp;neue&nbsp;apps | Diese Funktion ist für alle neuen apps aktiviert und kann nicht deaktiviert werden.  Für vorhandene apps, bei denen die Funktion ausgeschaltet ist, wird die Funktion weiterhin als Vorschau Feature angezeigt, bis Sie eingeschaltet ist.  Wenn diese Option aktiviert ist und der Switch nicht mehr verfügbar ist, können Sie [die APP auf eine vorherige Version](restore-an-app.md) zurücksetzen, um zu einem Zustand zurückzukehren, bevor die Funktion aktiviert wurde. | Ja. |
| **Ausgeliefert** für&nbsp;alle&nbsp;-apps | Alle apps verfügen über diese Funktion und können nicht deaktiviert werden. | Ja. | 

## <a name="documentation"></a>Dokumentation

Wo werden Informationen zu diesen Features veröffentlicht?  Vorschaufeatures werden als abgeschlossene Features angesehen, und Sie können dort mehr über diese Features erfahren, wo Sie auch Informationen zu jedem anderen Feature erhalten: 
- [Powerapps-Dokumentation](https://docs.microsoft.com/powerapps/maker/canvas-apps/getting-started). Hier erhalten Sie grundlegende Informationen zum neuen Feature: zu den Vorteilen, den ersten Schritte und zu Referenzinformationen.
- [Powerapps-Communityforum](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1).  Sie lernen das neue Feature gemeinsam mit anderen Benutzern kennen. Hier können Sie sich austauschen und voneinander lernen.
- [Blog zu Power apps](https://powerapps.microsoft.com/blog/)  Die meiste Zeit, allerdings nicht immer, wir mit einem neuen Feature auch ein dazugehöriger Blogbeitrag veröffentlicht.

Das ist bei experimentellen Features anders.  Sie befinden sich noch in Bearbeitung und werden nicht als fertig angesehen. Die kurze Beschreibung im Bereich **App-Einstellungen** (siehe unten) kann die einzige Stelle sein, an der Sie Informationen zu diesen Features erhalten. Experimentelle Features werden normalerweise nicht in der Dokumentation behandelt. Das Communityforum ist in diesem Fall Ihre beste Informationsquelle.  In einigen Fällen wird das Feature in einem frühen Blogbeitrag beschrieben.  Wenn Sie nicht ausreichend Informationen finden können, stellen Sie im Forum eine Frage, oder warten Sie, bis das Feature in die Vorschauphase übergeht.

## <a name="controlling-which-features-are-enabled"></a>Aktivieren und Deaktivieren von Features

Experimentelle Features und Vorschaufeatures werden in den **erweiterten Einstellungen** der App aufgeführt.  Klicken Sie in der App auf das Menü **Datei**, wählen Sie **App-Einstellungen** und dann **Erweiterte Einstellungen**. Scrollen Sie nach unten zu den Bereichen **Preview Features** (Vorschaufeatures) und **Experimental Features** (Experimentelle Features):

![](media/working-with-experimental/advanced-settings.png)

Jedes Feature hat einen Umschalter.  Wenn **Off** (Aus) angezeigt wird, ist das Feature deaktiviert.  Standardmäßig stehen alle Umschalter auf „Off“. So können Sie Ihre App am sichersten ausführen.

In einigen Fällen kann es nötig sein, die App zu schließen und neu zu starten, nachdem Sie Änderungen vorgenommen haben.  Sollte dieser Schritt erforderlich sein, wird dies in der Featurebeschreibung angegeben.

Im oberen Bereich der **erweiterten Einstellungen** finden Sie Einstellungen für vollständig ausgelieferte Features, die sich nicht mehr in der experimentellen oder Vorschauphase befinden und die zuverlässig funktionieren. 

Diese Einstellungen unterscheiden sich je nach App. Wenn Sie einen Umschalter betätigen, wirkt sich das deshalb nur auf die App aus, die Sie gerade geöffnet haben. Wenn Sie eine App erstellen, werden die Umschalter auf die Standardeinstellungen für diese App zurückgesetzt.

## <a name="feature-deprecation"></a>Funktions Veraltung

Manchmal muss ein Feature abgekoppelt werden.  Dies tritt häufig auf, wenn eine neue, bessere Methode zum Ausführen einer Aufgabe vorhanden ist.  Außerdem werden unbeliebte Features ebenfalls gelöscht, da für alle Features ein zusätzlicher Aufwand erforderlich ist, um mit Produktänderungen zu umgehen.

Funktions Veraltung durchläuft ebenfalls Phasen.  Features sind eindeutig, und nicht jede Phase wird von allen Funktionen verwendet.

| Phase | Wann sollte ich Sie verwenden? | Ist es zuverlässig?  Ist es standardmäßig für neue Apps aktiviert? | 
|----|----|----|
| **Veraltet** | Vorhandene Apps können diese Funktion für einen begrenzten Zeitraum weiterhin verwenden. Sie können das Feature für neue apps weiterhin aktivieren.  Es ist an der Zeit, Alternativen zu evaluieren.  | Ja, Sie können das Feature weiterhin vertrauenswürdiger nutzen. Es wird jedoch bald nicht mehr angezeigt. Aus diesem Grund müssen Sie explizit die Verwendung der Funktion in neuen apps abonnieren, was nicht empfohlen wird.  |
| **Veraltet (abschließende&nbsp;Warnung)** | Für einige Features, die weitreichende Auswirkungen haben, kann es erforderlich sein, den zusätzlichen Schritt zu **überschreiten, der für** vorhandene apps beim nächsten Öffnen des Features deaktiviert wird, wenn Sie in Studio geöffnet werden.  Wenn ein Problem vorliegt, kann die Funktion weiterhin aktiviert werden, und Ihr Feedback ist wichtig, bevor wir den nächsten Schritt durchführen.|  Nein.  Das Feature wird im Begriff, dauerhaft entfernt zu werden. Sie müssen sich explizit für die Verwendung der Funktion entscheiden, was nicht empfohlen wird. |
| Für&nbsp;neue&nbsp;-apps **entfernt** | Diese Funktion ist für alle neuen apps ausgeschaltet und kann nicht aktiviert werden.  Für vorhandene apps, bei denen die Funktion aktiviert ist, wird die Funktion weiterhin als veralteter Funktions Anzeige angezeigt, bis Sie ausgeschaltet ist.  Wenn Sie ausgeschaltet sind und der Funktions Wechsel nicht mehr verfügbar ist, können Sie [die APP auf eine frühere Version](restore-an-app.md) zurücksetzen, um zu einem Zustand zurückzukehren, bevor die Funktion deaktiviert wurde. | Nein.  Das Feature wird im Begriff, dauerhaft entfernt zu werden. Die Funktion ist für neue apps nicht mehr verfügbar. |
| Zum&nbsp;aller&nbsp;-apps **entfernt** | Die Funktion ist für alle apps nicht verfügbar. | Nein. |  

