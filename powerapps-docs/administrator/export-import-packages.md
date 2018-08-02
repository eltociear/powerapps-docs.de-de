---
title: Exportieren und Importieren von Ressourcen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Ressourcen in PowerApps exportieren und importieren.
author: nimakms
manager: kvivek
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 07/28/2017
ms.author: nimak
ms.openlocfilehash: db5861b9f598045436ad0bf796f04ed1df4b8903
ms.sourcegitcommit: 2e7b621066cdc3e7be329d5213ecfee0b4223641
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/30/2018
ms.locfileid: "39349752"
---
# <a name="export-and-import-resources"></a>Ressourcen exportieren und importieren
Wenn Sie mehrere Umgebungen erstellt haben, um die Entwicklung Ihrer Datenbank und Apps zu unterstützen , müssen Sie Änderungen von einer Umgebung in die andere Umgebung verschieben. Sie können **Ressourcen exportieren** und **Ressourcen importieren** verwenden, um Ressourcen zwischen Umgebungen zu verschieben.

## <a name="why-use-multiple-environments"></a>Gründe für die Verwendung von mehreren Umgebungen
Jede Umgebung enthält Ressourcen wie Entitäten, Flows und Apps, die Sie während des Entwicklungsprozesses erstellen oder ändern. 

In der Regel erfolgt die Entwicklung in derselben Umgebung, die die Endbenutzer des Unternehmens verwenden. Diese Umgebung wird als Standardumgebung bezeichnet. Es ist relativ einfach, Ressourcenänderungen in derselben Umgebung zu verwalten. Überprüfen Sie die Änderungen, um sicherzustellen, dass alle wichtigen Geschäftsprozesse und Anwendungen funktionsfähig sind, und stellen Sie dann die App bereit.

Manchmal erfolgen Entwicklung und Tests in unterschiedlichen Umgebungen. Dann werden Änderungen in die Standardumgebung verschoben, sobald sie für die Verwendung durch die Endbenutzer zur Verfügung stehen. Es gibt mehrere Gründe, warum Sie separate Umgebungen verwenden sollten: Sie haben beispielsweise eine eigenständige Umgebung verwendet, als Sie das System anfänglich ausgewertet haben. Außerdem sollten Sie das Risiko minimieren, das entsteht, wenn Sie Änderungen an der Standardumgebung durchführen. Separate Umgebungen ermöglichen eine Isolation, da Sie die Änderungen in einer Umgebung vornehmen, die nicht die Standardumgebung ist. Je nachdem, wie viele Risiken damit verbunden sind, können Sie eine zusätzliche Stagingumgebung erstellen. In diesem Fall verfügen Sie über eine Entwicklungsumgebung, einer Stagingumgebung und eine Standardumgebung.

## <a name="moving-resource-changes"></a>Verschieben von Änderungen an Ressourcen
Sie verschieben Ressourcen über separate Export- und Importprozesse mithilfe einer Paketdatei (ZIP). Die Paketdatei wird exportiert, in den lokalen Speicher gespeichert, an den Administrator der Zielumgebung gesendet und anschließend in die Zielumgebung importiert. Auf den Importvorgang folgt häufig ein Überprüfungstest, um sicherzustellen, dass keine wichtigen Geschäftsprozesse beeinträchtigt werden.

Die Funktion zum Importieren und Exportieren von Ressourcen ist im Abschnitt **Umgebungen** des Administrationscenters verfügbar. Sowohl das Exportieren als auch das Importieren erfolgen in einer ausgewählten Umgebung.

### <a name="export-resources"></a>Exportieren von Ressourcen
Das Exportpaket enthält alle Änderungen der **Entitäten und Auswahllisten**. Wir arbeiten daran, den Export von weiteren Ressourcentypen wie Apps, Flows, Connectors, Rollen usw. zu ermöglichen. Mithilfe dieser Option können Sie Inhalte von einer Umgebung in eine andere Umgebung verschieben.

1. Klicken Sie im [Admin Center](https://admin.powerapps.com) im linken Navigationsbereich auf **Environments** (Umgebungen).
2. Wählen Sie die Quellumgebung aus.
3. Klicken Sie in der oberen rechten Ecke auf **Ressourcen exportieren**.
4. Wählen Sie die Ressourcen aus, mit denen Sie beginnen möchten:
   1. Wählen Sie die Registerkarte für den auszuwählenden Ressourcentyp aus, z.B. **Entitäten**.
   2. Wählen Sie alle Ressourcen dieses Typs aus, indem Sie auf das Kontrollkästchen in der Kopfzeile klicken, oder wählen Sie Ressourcen einzeln aus.
   3. Klicken Sie auf **Weiter**.
5. Schließen Sie ggf. zugehörige Ressourcen ein:
   1. Wenn zugehörige Ressourcen erkannt werden, wird eine vorausgewählte Liste angezeigt.
   2. Schließen Sie alle zugehörigen Ressourcen aus, indem Sie auf das Kontrollkästchen in der Kopfzeile klicken, oder heben Sie die Auswahl von einzelnen Ressourcen auf.
   3. Klicken Sie auf **Weiter**.
6. Fügen Sie einen **Namen** für das exportierte Paket hinzu.
7. Sie können optional Setupaktionen anpassen, die beim Import von Ressourcen ausgeführt werden sollen:
   1. Klicken Sie für jede Ressource auf **Importeinrichtung**, um ein entsprechendes Dialogfeld zu öffnen.
   2. Wählen Sie die Setupaktion aus, die standardmäßig beim Importieren dieses Pakets ausgeführt werden soll.
   3. Klicken Sie auf **Speichern**.
8. Klicken Sie auf **Exportieren**.
9. Speichern Sie die Paketdatei bei Abschluss des Exportvorgangs im lokalen Speicher.

Sie können auch auf der Ressourcenauswahlseite auf **Alle Ressourcen auswählen** klicken, um sämtliche Ressourcen aller unterstützten Typen in das endgültige Paket einzuschließen und direkt zur abschließenden Exportseite zu wechseln.

### <a name="import-resources"></a>Importieren von Ressourcen
Wählen Sie zunächst eine Paketdatei aus, die aus der Quellumgebung exportiert wurde. Der Importvorgang überprüft, analysiert und versucht, das Paket zu importieren.

1. Klicken Sie im [Admin Center](https://admin.powerapps.com) im Navigationsbereich auf **Umgebungen**.
2. Wählen Sie die Zielumgebung.
3. Klicken Sie in der oberen rechten Ecke auf **Ressourcen importieren**.
4. Klicken Sie auf **Hochladen**, und navigieren Sie zu einer Paketdatei im lokalen Speicher.
5. Klicken Sie auf **Weiter**, um zur abschließenden Importseite zu wechseln.
6. Beheben Sie Validierungsmeldungen und Warnungen zum Import:
   1. Suchen Sie nach Warnungen oder Fehlern; diese werden mit einem Symbol links vom **Namen** einer Ressource angezeigt.
   2. Klicken Sie auf das Feld **Importeinrichtung** oder auf das Symbol unter **Aktion**, um weitere Informationen zu erhalten.
   3. Wählen Sie eine geeignete Importeinrichtungsaktion aus.
   4. Das importierte Paket wird automatisch erneut überprüft.
7. Wenn keine Fehler vorliegen, fahren Sie mit **Importieren** fort.

Wenn das Paket nur teilweise angewendet wurde, erhalten Sie eine Fehlermeldung, die angibt, was importiert wurde und was nicht.

## <a name="resource-types"></a>Ressourcentypen
Der Entwicklungsprozesses kann Änderungen an vielen unterschiedlichen Arten von Ressourcen umfassen. Wenn Sie beispielsweise eine App aktualisieren, können Sie mehrere Entitäten oder Verbindungen hinzufügen, entfernen oder aktualisieren. Einige, wenn auch nicht alle Änderungen an Ressourcentypen können in andere Umgebungen verschoben werden. In den folgenden Abschnitten wird beschrieben, welche Ressourcentypen sich verschieben lassen.

### <a name="entities-picklists"></a>Entitäten, Auswahllisten
Sie können Entitäten und Auswahllisten wie folgt exportieren und importieren:

* **Standardentitäten**: Es werden nur Anpassungen zwischen Umgebungen verschoben. (Die Out-of-Box-Felder von Standard-Entitäten lassen sich allerdings nicht ändern.)
* **Benutzerdefinierte Entitäten** –Benutzerdefinierte Entitäten können zwischen Umgebungen verschoben werden.
* **Benutzerdefinierte Auswahllisten**: Benutzerdefinierte Auswahllisten können zwischen Umgebungen verschoben werden.

## <a name="data"></a>Daten
Datenbankdaten als Teil des Exports und Imports von Ressourcen können nicht verschoben werden. Um Daten zu verschieben, können Sie Microsoft Excel verwenden. 

