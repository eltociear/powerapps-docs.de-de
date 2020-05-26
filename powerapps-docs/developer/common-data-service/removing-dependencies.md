---
title: Entfernen von Abhängigkeiten (Common Data Service) | Microsoft Docs
description: Abhängigkeiten können manchmal Operationen blockieren. Dieser Artikel beschreibt, wie Abhängigkeiten entfernt werden können.
ms.custom: ''
ms.date: 04/28/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: ccdietrich
ms.author: cdietric
manager: shmcarth
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3c0227ac41dce2fe28f27d1ac92401fa4d6f476d
ms.sourcegitcommit: 94d66a2e1bc7f45f1a8ae97cc5ec4fce89aefdee
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2020
ms.locfileid: "3325706"
---
# <a name="removing-dependencies"></a>Entfernen von Abhängigkeiten

Abhängigkeiten sind Datensätze, die vom Lösungs-Framework automatisch erstellt werden, um Aktionen zu verhindern, die, wenn sie unkontrolliert ausgeführt werden, Probleme verursachen könnten. Wenn Komponenten geändert und erweitert werden, werden Abhängigkeiten geschaffen, um z.B. anzuzeigen, dass ein Feld für die Funktion eines Formulars erforderlich ist.
Wenn Sie jemals versuchen, eine Aktion auszuführen, die zur Löschung dieses Feldes führt, führt dies dazu, dass das Formular nicht mehr funktioniert.

Abhängigkeiten bestehen, um zu verhindern, dass erforderliche Komponenten gelöscht werden, solange eine oder mehrere abhängige Komponenten noch einen Verweis darauf haben.

> [!NOTE]
> Das Wort *löschen*, wie es im Zusammenhang mit diesem Dokument verwendet wird, ist als vollständige Entfernung der Komponente aus dem System zu verstehen.

In diesem Artikel besprechen wir den Umgang mit diesen Abhängigkeiten und die Strategien, die zur Entfernung nicht mehr benötigter Abhängigkeiten verwendet werden können.

Zunächst muss klargestellt werden, dass Abhängigkeiten nur Operationen verhindern, die das Löschen einer erforderlichen Komponente bewirken würden, und dass die Aktionen, mit denen eine Komponente gelöscht werden kann, je nach ihrem Zustand unterschiedlich sind:

- **Nicht verwaltet**: Komponenten in diesem Zustand werden in der aktiven Lösung durch eine einzige Schicht dargestellt. Jeder **Löschvorgang** an der Komponente führt zur vollständigen Entfernung der Komponente.

 - **Verwalten**: Das Löschen von verwalteten Komponenten hängt von mehreren Faktoren ab: Anzahl der Lösungsschichten, relative Position der Schicht, die deinstalliert wird, und die Herausgeber der Komponenten. Wenn z.B. eine Komponente gelöscht wird, betrachten Sie die folgenden Szenarien und was bei der Deinstallation erwartet wird:

     ![Deinstallieren mit einer einzigen Schicht](media/solution-managed-uninstall-scenario-01.png "Deinstallation mit einer einzigen Ebene")

    - Lösung 1 - Verursacht eine Löschung der Komponente, da sie die einzige Ebene für die Komponente ist.

    ![Deinstallieren mit zwei Ebenen - anderer Herausgeber](media/solution-managed-uninstall-scenario-02.png "Deinstallation mit zwei Ebenen - anderer Herausgeber")

    - Lösung 2 - verursacht keine Löschung von Komponenten. Nur diese Schicht wird entfernt.
    - Lösung 1 - Verursacht eine Komponentenlöschung, da die Aktion in der Basisschicht stattfindet. Tatsächlich kann Lösung 1 in diesem Fall nicht deinstalliert werden, da es eine Lösung von einem anderen Herausgeber gibt, die die Komponente erweitert.

    ![Deinstallieren mit mehreren Ebenen - Anderer Herausgeber](media/solution-managed-uninstall-scenario-03.png "Deinstallation mit mehreren Ebenen - Verschiedene Herausgeber")
    
     - Lösung 3 - Verursacht keine Löschung von Komponenten. Nur diese Schicht wird entfernt.
     - Lösung 2 - verursacht keine Löschung von Komponenten. Nur diese Schicht wird entfernt.
     - Lösung 1 - Verursacht keine Löschung einer Komponente. In diesem Fall gibt es eine andere Lösung vom gleichen Herausgeber (Lösung 3). Die Plattform entfernt die Schicht aus Lösung 1 und ersetzt sie durch die Schicht aus Lösung 3.

    ![Deinstallieren mit zwei Ebenen - Nicht verwaltete Anpassung](media/solution-managed-uninstall-scenario-04.png "Deinstallation mit zwei Ebenen - Nicht verwaltete Anpassung")

      - Aktiv - Führt nicht zur Löschung einer Komponente. Nur diese Schicht wird entfernt. Beachten Sie, dass Sie die aktive Lösung nicht deinstallieren können, aber Sie können Komponenten mit der Funktion **Aktive Anpassung entfernen** entfernen.
      - Lösung 1 - Verursacht eine Löschung der Komponente. Die Aktion findet in der Basisebene statt. Im Gegensatz zu Szenario 2 können Sie Lösung 1 deinstallieren. Die aktive Lösung wird nicht als Erweiterung betrachtet und beide Zeilen werden entfernt.

## <a name="dependency-dialog"></a>Abhängigkeits-Dialog

Im Abhängigkeits-Dialogfeld können Sie die Abhängigkeiten für die ausgewählte Lösung auflisten. Es kann durch aufgerufen werden:

- Klicken Sie auf die Schaltfläche **Abhängigkeiten anzeigen** auf der Seite der Lösung.
- Beim Versuch, eine Lösung zu deinstallieren, stellt die Plattform fest, dass Abhängigkeiten bestehen.

Beispiel:

![Abhängigkeitsdialog mit Abhängigkeiten](media/dependency-dialog-with-dependencies.png "Abhängigkeitsdialog mit Abhängigkeiten")

Das Dialogfeld **Abhängigkeitsdetails** hat 6 Spalten, die im Folgenden beschrieben werden:

- **Anzeigename**: Freundlicher Name der gewünschten Komponente. Jede Komponente kann leicht abweichende Daten anzeigen, um die Identifizierung zu erleichtern. In der Beispielabbildung sehen Sie, dass die Entität nur ihren Namen hat, während das Feld seinen Namen und den Namen der übergeordneten Entität hat.
- **Name/Id**: Interner Name der gewünschten Komponente.
- **Typ**: Der Typ der gewünschten Komponente.
- **Benötigt von**: Freundlicher Name der Komponente, die es erfordert (die abhängige Komponente). Wenn die Komponente über eine Anpassungsseite verfügt, verwandelt sie sich in einen Link, der diese Seite öffnet.
- **Abhängiger Typ**: Typ der abhängigen Komponente.
- **Lösungsschichten**: Link, wo Sie weitere Details über die an der Abhängigkeit beteiligten Komponenten sehen können.

> [!NOTE]
> Die erforderliche Komponente ist diejenige, die Sie löschen möchten. Die abhängige Komponente ist diejenige, die Referenzen auf die erforderliche Komponente hat. Um eine Abhängigkeit zu entfernen, müssen Sie Änderungen vornehmen, die die abhängige Komponente betreffen, nicht die erforderliche Komponente.

## <a name="diagnosing-dependencies"></a>Diagnostizieren von Abhängigkeiten

Betrachten wir das folgende Szenario. Die unten stehende Organisation hat zwei Lösungen: "Lösung - Workflow" und "Lösung - benutzerdefinierte Entitäten".

![Lösungsliste mit zwei Lösungen](media/solution-list-custom-entity-workflow.png "Lösungsliste mit zwei Lösungen")

Der Besitzer der Organisation entschied, dass "Lösung - benutzerdefinierte Entitäten" nicht mehr erforderlich sei, versuchte, diese zu löschen, und wurde mit dem folgenden Dialog konfrontiert:

![Abhängigkeitsdialog mit Abhängigkeiten](media/dependency-dialog-with-dependencies.png "Abhängigkeitsdialog mit Abhängigkeiten")

Ohne ins Detail zu gehen, können wir daraus schließen, dass bei der Deinstallation der Lösung versucht wird, eine Entität namens "Benutzerdefinierte Entität" und die drei Felder "Benutzerdefinierte Entität", "Name" und "Zahlenfeld" zu löschen, in denen alle 4 Komponenten Abhängigkeiten aufweisen.

> [!NOTE]
> Die Lösung kann das Löschen weiterer Komponenten sein, aber da diese keine Abhängigkeiten haben, erscheinen sie nicht in der Liste.

Der nächste Schritt besteht darin, die Lösungsebenen (Link in der Spalte ganz rechts) für jede Abhängigkeit zu prüfen. Das hilft zu definieren, welche Aktion erforderlich ist, um die Abhängigkeit zu entfernen.

Entität (Benutzerdefinierte Entität) und Prozess (Test-Workflow): Entität (Benutzerdefinierte Entität) und Prozess (Test-Workflow):

![Abhängigkeit zwischen Entität (benutzerdefinierte Entität) und Workflow (Meine App)](media/solution-dependency-solution-history-02.png "Abhängigkeit zwischen Entität (Benutzerdefinierte Entität) und Sitemap (Meine App)")

Auf der Grundlage der angezeigten Daten können Sie sehen, dass die abhängige Komponente zu einer Lösung namens Lösungs-Workflow gehört. Um diese Abhängigkeit zu entfernen, können wir beides tun:

- Aktualisieren Sie die Definition des Workflows in SolutionWorkflow, indem Sie alle Verweise auf die Entität oder ihre Unterkomponenten entfernen. Dann **Update** oder **Upgrade** die Lösung.
- Die SolutionWorkflow-Lösung deinstallieren.
- Entfernen Sie den Workflow aus einer neuen Version der SolutionWorkflow-Lösung und führen Sie ein **Upgrade** durch.

Da jede einzelne abhängige Komponente das Entfernen der Lösung stoppen kann, empfehlen wir Ihnen, alle Abhängigkeiten zu überprüfen und alle erforderlichen Änderungen in einem einzigen Vorgang vorzunehmen.

Entität (Benutzerdefinierte Entität) und modellbasierte App (Meine App):

![Abhängigkeit zwischen Entität (benutzerdefinierte Entität) und Sitemap (Meine App)](media/solution-dependency-solution-history-01.png "Abhängigkeit zwischen Entität (Benutzerdefinierte Entität) und Sitemap (Meine App)")

Auf der Grundlage der angezeigten Daten können Sie sehen, dass die abhängige Komponente zu einer Lösung mit dem Namen Aktiv gehört. Dies deutet darauf hin, dass die Abhängigkeit durch den Import einer nicht verwalteten Lösung oder durch eine nicht verwaltete Anpassung erstellt wurde, die über die moderne Benutzeroberfläche oder API ausgeführt wurde.

Um diese Abhängigkeit zu entfernen, können Sie entweder

- Bearbeiten Sie die Definition der modellbasierten App, um jeden Verweis auf die Entität oder ihre Unterkomponenten zu entfernen. Da modellbasierte Apps das Publizieren unterstützen, müssen Sie Ihre Änderungen veröffentlichen.
- Löschen Sie die modellbasierte App.

> [!NOTE]
> Die Deinstallation einer nicht verwalteten Lösung ist keine Option, um diese Abhängigkeit aufzuheben, da nicht verwaltete Lösungen nur Mittel zur Gruppierung von Komponenten sind.

## <a name="actions-to-remove-a-managed-dependency"></a>Aktionen zum Entfernen einer verwalteten Abhängigkeit

Verwaltete Abhängigkeiten sind diejenigen, bei denen die abhängige Komponente mit einer verwalteten Lösung verknüpft ist. Um diese Art der Abhängigkeit zu lösen, müssen Sie sich an die Lösung halten, zu der die Komponente hinzugefügt wurde. Diese Aktion kann je nach dem, was Sie zu tun versuchen, unterschiedlich sein:

- Wenn Sie versuchen, eine Lösung zu deinstallieren, können Sie mit dieser Canvas-Anwendung eine Lösung erstellen und verwalten:

    1. Untersuchen Sie in der Zielorganisation den Link Lösungsebenen, um die oberste Lösung auf der Liste der abhängigen Komponente zu finden.
    1. Bereiten Sie in der Quell-Organisation eine neue Version dieser Lösung vor, wobei: die Lösung die abhängige Komponente nicht enthält oder eine aktualisierte Version der abhängigen Komponente besitzt, die keine Verweise auf die erforderliche Komponente enthält. Ihr Ziel ist es, jeden Verweis auf die erforderlichen Komponenten in der neuen Version der Lösung zu entfernen.
    1. Exportieren Sie die neue Version der Lösung.
    1. In der Zielorganisation: **Aktualisierung** diese Lösung.

Versuchen Sie als nächstes die Deinstallation erneut.

- Wenn Sie versuchen, eine Lösung zu aktualisieren: In diesem Fall müssen Sie bestätigen, dass das Löschen der erforderlichen Komponente eine beabsichtigte Aktion ist (denken Sie daran, dass Abhängigkeiten nur bei Komponenten erzwungen werden, die gelöscht werden).

  Wenn dies nicht beabsichtigt war, ist es richtig, die neue Version der Lösung durch Hinzufügen der Komponente zurück zu reparieren. Dazu müssen Sie dies tun:

    1. Deinstallieren Sie in der Zielorganisation die abgestufte Lösung (die Lösung, die mit _Upgrade endet).
    2. Fügen Sie in der Ausgangsorganisation die erforderliche(n) Komponente(n) wieder zur Lösung hinzu.
    3. Exportieren Sie die neue Version.
    4. Versuchen Sie das Upgrade erneut.

  Wenn die Löschung absichtlich erfolgt, müssen Sie die Abhängigkeit entfernen. Die möglichen Schritte sind die gleichen wie die im vorherigen Aufzählungspunkt beschriebenen.

### <a name="layers-and-dependencies"></a>Ebenen und Abhängigkeiten

Die abhängigen Komponenten können geschichtet werden, so dass Sie unter Umständen mehr als eine Lösung ändern müssen, um eine Abhängigkeit vollständig zu entfernen. Der Abhängigkeitsrahmen berechnet nur die Abhängigkeiten zwischen den obersten Schichten für die erforderlichen und abhängigen Komponenten. Das bedeutet, dass Sie sich von den Lösungen der abhängigen Komponente von oben nach unten vorarbeiten müssen.

Betrachten Sie folgendes Szenario:

![Abhängigkeit zwischen Entität (benutzerdefinierte Entität) und Sitemap (Meine App)](media/solution-dependency-multiple-layers.png "Abhängigkeit zwischen Entität (Benutzerdefinierte Entität) und Sitemap (Meine App)")

Sie versuchen, "Lösung - Benutzerdefinierte Entität" zu deinstallieren, und der Vorgang wird durch Abhängigkeiten blockiert:

![Abhängigkeiten, die die Deinstallation der Lösung blockieren - Benutzerdefinierte Entität](media/solution-dependency-layers-and-dependencies-dependency-dialog-01.png "Abhängigkeiten, die die Deinstallation von 'Lösung - Benutzerdefinierte Entität' blockieren")

Sie beginnen mit der Diagnose der Abhängigkeit, indem Sie auf "Solution Layers" auf dem Attribut (new_numberfield) und dem Workflow (Test Workflow) klicken. Sie sehen den folgenden Bildschirm:

![Abhängigkeit zwischen Attribut (neues_Nummernfeld) und Workflow (Test-Workflow)](media/solution-dependency-layers-and-dependencies-solution-history-01.png "Abhängigkeiten zwischen Attribut (new_numberfield) und Workflow (Test-Workflow)")

Da Abhängigkeiten nur zwischen den obersten Schichten jeder Komponente erstellt werden, besteht der erste Schritt darin, sich mit der Abhängigkeit zwischen dem Attribut (new_numberfield) in SolutionCustomEntity und dem Workflow (Test Workflow) in SolutionWorkflow3 zu befassen.

Um die Abhängigkeit zu entfernen, haben Sie beschlossen, SolutionWorkflow3 zu deinstallieren. Sie haben dies getan, aber wenn Sie versuchen, die Lösung wieder zu deinstallieren, werden Sie durch dasselbe Dialogfeld geführt:

![Abhängigkeiten, die die Deinstallation der Lösung blockieren - Benutzerdefinierte Entität](media/solution-dependency-layers-and-dependencies-dependency-dialog-02.png "Abhängigkeiten, die die Deinstallation von 'Lösung - Benutzerdefinierte Entität' blockieren")

Das Attribut (new_numberfield) wird jedoch nicht mehr aufgeführt, auch wenn es mehr Ebenen hatte.

## <a name="actions-to-remove-an-unmanaged-dependency"></a>Aktionen zur Beseitigung einer nicht verwalteten Abhängigkeit

Um nicht verwaltete Abhängigkeiten zu entfernen, müssen Sie direkt auf die Komponenten einwirken, nicht auf die Lösungen, zu denen sie gehören. Wenn Sie z.B. die Abhängigkeiten zwischen einem Attribut und einem Formular entfernen möchten, müssen Sie es im Formular-Editor bearbeiten und das Attribut aus dem Formular entfernen. Die Abhängigkeit wird entfernt, nachdem Sie **Speichern** und **Veröffentlichen** gewählt haben.

> [!NOTE]
> Sie können auch die abhängige Komponente löschen. Diese Aktion löscht alle Abhängigkeiten zusammen mit der Komponente.

Um die Abhängigkeiten einer Komponente zu sehen, müssen Sie sie auf der Anpassungsseite finden und auf **Abhängigkeiten anzeigen** klicken.

Beispielsweise wird ein Feld angegeben:

![Abhängigkeiten anzeigen](media/solution-dependency-layers-and-dependencies-component-show-dependencies.png "Abhängigkeiten anzeigen")

Das Dialogfeld besteht aus zwei verschiedenen Teilen:

![Komponentenabhängigkeiten](media/solution-dependency-layers-and-dependencies-component-dependency-dialog.png "Komponente anzeigen")

  - Abhängige Komponenten: Liste der Komponenten, die von dem ausgewählten Feld abhängen. Mit anderen Worten, Komponenten, die dieses F=Feld als erforderliche Komponente haben werden.
  - Erforderliche Komponenten: Liste der Komponenten, die für die Funktion dieses Feldes erforderlich sind. Mit anderen Worten: Komponenten, die dieses Feld als abhängige Komponente haben werden.

Die gängigsten Szenarien: (Erforderlich und abhängig)

## <a name="field-and-workflow"></a>Feld und Workflow

Um Abhängigkeiten zwischen Feldern (Attributen) und Workflows (Prozessen) zu entfernen, müssen Sie den Workflow auf der Seite **Anpassungen** finden.

Bei geöffnetem Workflow müssen Sie den Verweis auf die Komponente finden, von der der Workflow nicht mehr abhängen soll. In diesem Beispiel sehen Sie, wie das Feld (Zahlenfeld) in einem Schritt referenziert wird:

![Workflow bearbeiten](media/solution-dependency-component-workflow.png "Workflow bearbeiten")

Löschen (oder ändern) Sie den Schritt und speichern Sie dann den Workflow.

## <a name="field-and-view"></a>Feld und Ansicht

Um Abhängigkeiten zwischen Feldern (Attributen) und Ansichten (gespeicherten Abfragen) zu entfernen, müssen Sie die Ansicht auf der Seite **Anpassungen** finden.

Suchen Sie im Feldeditor den Verweis auf die Komponente, von der der View nicht mehr abhängig sein soll. In diesem Beispiel sehen Sie das Feld (Zahlenfeld), das als Auswahlspalte und Filter verwendet wird.

![Ansicht bearbeiten](media/solution-dependency-component-view.png "Ansicht bearbeiten")

Entfernen Sie beides, speichern Sie und veröffentlichen Sie dann die Ansicht.

## <a name="entity-and-model-driven-apps"></a>Entitäts- und modellbasierte Apps (Meine App)

Um Abhängigkeiten zwischen Entitäten und modellbasierten Apps (App-Modul) zu entfernen, müssen Sie die App in der Liste **Apps** der modernen Benutzerschnittstelle finden.

![Liste der Anwendungen](media/solution-dependency-component-appmodule-01.png "Liste der Apps")

Suchen Sie im Editor den Verweis auf die Komponente, von der die App nicht mehr abhängig sein soll. In diesem Beispiel sehen Sie die Entität (Benutzerdefinierte Entität) in der **Entitätsansicht**.

![Anwendungs-Editor](media/solution-dependency-component-appmodule-02.png "App-Editor")

Sehen Sie sich auch die mit der App verbundene Sitemap an, denn es ist wahrscheinlich, dass Sie dort Verweise finden:

![Site-Map-Editor](media/solution-dependency-component-appmodule-03.png "App Zuordnungseditor")

Entfernen Sie alle Verweise, speichern und veröffentlichen Sie beides (die App und die Sitemap).

> [!NOTE]
> Nach der Bearbeitung können Komponenten zu verwalteten Lösungen hinzugefügt und zu anderen Organisationen transportiert werden, um verwaltete Abhängigkeiten zu entfernen.
  
### <a name="see-also"></a>Siehe auch  
 [Packen und Verteilen von Erweiterungen mithilfe von Dynamics 365-Lösungen](/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions)   
 [Einführung zu Lösungen](introduction-solutions.md)   
 [Planen einer Lösungsentwicklung](/dynamics365/customer-engagement/developer/plan-solution-development)   
 [Erstellen, Exportieren oder Importieren einer nicht verwalteten Lösung](create-export-import-unmanaged-solution.md)   
 [Eine verwaltete Lösung erstellen, installieren und aktualisieren](create-install-update-managed-solution.md)   
 [Eine verwaltete Lösung erstellen, installieren und aktualisieren](create-install-update-managed-solution.md)   
 [Deinstallieren oder Löschen einer Lösung](uninstall-delete-solution.md)   
 [Lösungsentitäten](/dynamics365/customer-engagement/developer/solution-entities)
