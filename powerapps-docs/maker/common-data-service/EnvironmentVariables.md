---
title: 'Vorschau: Umgebungsvariablen in Lösungen verwenden | Microsoft-Dokumentation'
description: Verwenden Sie Umgebungsvariablen, um Anwendungskonfigurationsdaten in Lösungen zu migrieren.
Keywords: Umgebungsvariablen, Variablen, Modellgestützte App, Konfigurationsdaten
author: caburk
ms.author: caburk
manager: kvivek
ms.date: 10/22/2019
ms.service: powerapps
ms.topic: article
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: f0c3189fceebb785a022d04c58ff6cf71fd388bc
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2758278"
---
# <a name="preview-environment-variables-overview"></a>Vorschau: Umgebungsvariablenübersicht 

[!INCLUDE[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Apps und Flows benötigen häufig verschiedene Konfigurationseinstellungen zwischen Umgebungen. Umgebungsvariablen als konfigurierbare Eingabeparameter erlauben die separate Verwaltung von Daten, im Vergleich zu fest codierten Werten in Ihrer Anpassung oder der Verwendung zusätzlicher Tools. Da es Lösungskomponenten sind, ist die Leistung viel besser als beim Import von Konfigurationsdaten als Datensatzdaten.

Vorteile der Verwendung von Umgebungsvariablen:
- Keine manuelle Bearbeitung von konfigurierbaren Werten in einer Produktionsumgebung erforderlich.
- Konfigurieren eines oder mehrerer Variablen an einem Ort und Verweis wie bei einem Parameter für mehrere Lösungskomponenten.
- Werte ohne eine Codeänderung aktualisieren.
- Präzise Sicherheitsebene verwaltet von [Common Data Service](https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-intro).
- Unbegrenzte Anzahl von Variablen (maximal Lösungsgröße ist 29 MB).
- Service der Definitionen und Werte separat oder zusammen.
- Unterstützung durch [SolutionPackager](/powerapps/developer/common-data-service/compress-extract-solution-file-solutionpackager) und [DevOps](/powerapps/developer/common-data-service/build-tools-overview)-Tools ermöglicht die fortlaufende Integration und fortlaufende Lieferung (CI/CD).
- Unterstützung für die Lokalisierung.
- Kann verwendet werden, um Funktionsflags und andere Anwendungseinstellungen zu steuern.

> [!IMPORTANT]
> - Dies ist eine Vorschaufunktion.
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)] 

## <a name="how-they-work"></a>Wie funktionieren sie?
Umgebungsvariablen können durch die moderne Lösungsschnittstelle oder [mit Code](https://docs.microsoft.com/powerapps/developer/common-data-service/work-with-data-cds) erstellt und verwaltet werden. Eine separate JSON-Datei wird innerhalb Ihres Lösungspakets für die Werte erstellt, die auch im Quellsteuerelement verwaltet und in einer Buildpipeline geändert werden können. Export nach und Import aus Excel wird unterstützt. Nachdem Sie Umgebungsvariablen erstellt haben, können Sie diese als Eingaben in die Plug-Ins, Flows und andere Komponenten verwenden.

## <a name="default-value"></a>Standardwert
Dieses Feld ist Bestandteil der Umgebungsvariablen-Definitionsentität und ist nicht erforderlich. Festlegen eines Standardwerts für die Produktionsumgebung oder wenn die Werte nicht für verschiedene Umgebungen geändert werden müssen.

## <a name="value"></a>Wert
Auch als der aktuelle oder der Überschreibwert bekannt, ist dieses Feld optional und Teil der Umgebungsvariablenwertentität. Legen Sie den Wert fest, wenn Sie den Standardwert in Ihrer aktuellen Umgebung überschreiben möchten. Entfernen Sie den Wert aus Ihrer Lösung, wenn Sie ihn nicht in der folgenden Umgebung verwenden möchten. Die Werte sind auch in eine separate JSON-Datei in der Lösungs.zip-Datei getrennt, die exportiert wird. 

>[!NOTE]
> Ein Wert kann nicht ohne eine Definition bestehen. Die Schnittstelle lässt nur die Erstellung von einem Wert pro Definition zu. 

Die Trennung des Standardwerts und des aktuellen Werts ermöglicht Ihnen den Service der Definition und des Standardwerts unabhängig vom aktuellen Wert. Es ermöglicht uns außerdem die Erweiterung der Funktion zu einem späteren Zeitpunkt, um mehrere Werten zu unterstützen, die mit einem bestimmten Laufzeitkontext bewertet werden.

## <a name="notifications"></a>Benachrichtigungen
Eine Benachrichtigung wird angezeigt, wenn die Umgebungsvariablen keine Werte aufweisen. Dies ist eine Erinnerung, die Werte festzulegen, damit die Komponenten, die von Variablen abhängig sind, nicht versagen. Außerdem können Geschäftspartner Variablen ohne Werte versenden, und der Kunde wird aufgefordert, Werte einzugeben.

>[!NOTE]
> Wir empfehlen, dass Partner ihre eigenen Schnittstellen erstellen und von den Kunden die Bereitstellung der Werte fordern. Benachrichtigungen helfen Fehler zu vermeiden, falls dieser Schritte übersprungen wird. 

## <a name="security"></a>Sicherheit
Sowohl die environmentvariabledefinition und environmentvariablevalue Entitäten sind [Benutzer- oder Teambesitz](https://docs.microsoft.com/powerapps/maker/common-data-service/types-of-entities). Wenn Sie eine Anwendung erstellen, die Umgebungsvariablen verwendet, müssen Sie sicherstellen, dass Sie Benutzern die entsprechende Berechtigungsebenen zuweisen. Weitere Informationen: [Sicherheit in Common Data Service](https://docs.microsoft.com/power-platform/admin/wp-security). 

## <a name="current-limitations"></a>Aktuelle Einschränkungen
- Zwischenspeichern. Plug-Ins müssen eine Abfrage ausführen, um die Werte zu erhalten. 
- Canvas-Apps und -flows können Umgebungsvariablen genauso wie Entitätsdatensatzdaten verbrauchen. Wir planen künftig die Erstellung weiterer Aktionen in Canvas-App- und Flowdesigner. Dies vereinfacht die Erstellung und sorgt für einen besseren Einblick in die Umgebungsvariablen, die durch eine bestimmte App oder einen Flow verwendet werden.
- Azure Key Vault-Integration für geheime Verwaltung. Derzeit sollten Umgebungsvariablen nicht verwendet werden, um sichere Daten wie Kennwörter und Schlüssel zu speichern.
- Datentypen werden nur in der modernen Lösungsschnittstelle validiert, aber aktuell nicht auf dem Server bei der Vorschau. 
- Abhängigkeiten werden für bestimmte Komponententypen nicht erzwungen.
- Wenn Excel verwendet wird, um Umgebungsvariablen zu importieren, müssen Sie sicherstellen, die Herausgeberpräfix zum SchemaName voranzustellen.

### <a name="see-also"></a>Siehe auch
[Verwenden von Plug-Ins zur Erweiterung von Geschäftsprozessen](https://docs.microsoft.com/powerapps/developer/common-data-service/plug-ins) </BR>
[Web API Beispiele](https://docs.microsoft.com/powerapps/developer/common-data-service/webapi/web-api-samples) </BR>
[Canvas-App ganz neu erstellen mit Common Data Service.](https://docs.microsoft.com/powerapps/maker/canvas-apps/data-platform-create-app-scratch) </BR>
[Einen Flow erstellen mit Common Data Service](https://docs.microsoft.com/flow/connection-cds)
