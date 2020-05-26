---
title: FAQs | MicrosoftDocs
description: Häufig gestellte Fragen zum Komponenten-Framework
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: index-page
ms.assetid: 9f940264-d7d5-4930-8052-1bd582445d37
ms.author: grhurl
author: ghurlman
ms.reviewer: nkrb
ms.openlocfilehash: 12b8f136c717ad61f958df5869034f204c03cea5
ms.sourcegitcommit: 943672dad0041d3bab25b44cd8c4d25e88f39b93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/25/2020
ms.locfileid: "3289278"
---
# <a name="faqs"></a>Häufig gestellte Fragen

[!INCLUDE[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

### <a name="component-changes-are-not-reflected-after-the-updated-solution-import"></a>Änderungen an den Komponenten werden nach dem Import der aktualisierten Lösung nicht berücksichtigt?

Aktualisieren Sie die Komponentenversion (Minor oder Patch) in der Komponentenmanifestdatei (z.B. 1.0.0 auf 1.0.1). Jede Aktualisierung in der Komponente benötigt einen Komponentenversions-Stoß, um auf dem Common Data Service-Server widergespiegelt zu werden.

> [!NOTE]
> - Eine neue Lösung muss jedes Mal erstellt werden, wenn Sie einen größeren Versions-Stoß haben möchten. Das Erhöhen der Hauptversionsnummer (z.B. 1.0 auf 2.0) wird nicht als Upgrade unterstützt.
> - Es werden nur drei Versionsabschnitte unterstützt (d.h. MAJOR.MINOR.PATCH). Diese Abschnitte der Versionsnummer sollten zwischen 0 und 65536 liegen.

### <a name="what-are-the-things-to-be-considered-from-a-performance-perspective"></a>Was sind die Dinge, die aus Sicht der Leistung zu beachten sind?

1. Wenn Sie auf große Datenmengen zugreifen möchten, implementieren Sie [Filterung](reference/filtering.md) und [Paging](reference/paging.md) Methoden, um die Menge der zu ladenden Daten zu begrenzen.
2. Stellen Sie Ihre Netzwerkaufrufe zusammen und machen Sie alle Netzwerkaufrufe asynchron. Entwerfen Sie die Komponente so, dass alle erforderlichen Informationen mit einem einzigen Aufruf bereitgestellt werden. 
3. Gestalten Sie die Komponente so, dass der Benutzer eine Aktion (z. B. das Klicken auf eine Schaltfläche) durchführen muss, um das Laden bestimmter Daten des Elements zu initiieren, anstatt den Aufruf für jedes Datenelement durchzuführen.
4. Stellen Sie sicher, dass Sie die Ressourcen mit der Funktion [destroy](reference/control/destroy.md) bereinigen. Offene Netzwerkaufrufe, Verbindungen und Ereignisbehandler müssen bereinigt werden, um die Leistung zu erhöhen.

### <a name="where-can-i-find-some-good-examples-of-code-components"></a>Wo finde ich einige gute Beispiele für Code-Komponenten?

Viele gute Beispiele aus der Community sind auf den [Power Apps Community-Foren](https://powerusers.microsoft.com/t5/Power-Apps-Component-Framework/Community-content-sample-components-blogs-etc-Link-to-this-page/td-p/280710) verfügbar.

### <a name="how-to-use-rich-data-types-in-code-components-such-as-collections"></a>Wie kann man reichhaltige Datentypen in Code-Komponenten wie z.B. Sammlungen verwenden?

Derzeit wird diese Funktion nicht unterstützt. Es gibt jedoch eine [JSON-Funktion](https://docs.microsoft.com/powerapps/maker/canvas-apps/functions/function-json) in Canvas-Apps, die es App-Machern erlaubt, ihre Daten zu stringentieren.

1. Übergeben Sie die Sammlung an die JSON-Funktion.
2. Übergeben Sie die String-Repräsentation der Sammlungsdaten, die von der JSON-Funktion zurückgegeben wird, an eine der String-Eigenschaften der Komponente.
3. Verwenden Sie [JSON.parse](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse) im Komponentencode, um ihn wieder in ein JavaScript-Objekt zu konvertieren.

### <a name="how-can-i-define-multiple-components-in-a-single-manifest-file"></a>Wie kann ich mehrere Komponenten in einer einzigen Manifestdatei definieren?

Die Definition mehrerer Komponenten in einer einzigen Manifestdatei wird nicht unterstützt. 

### <a name="how-can-i-define-behavior-properties"></a>Wie kann ich Verhaltenseigenschaften definieren?

Dies wird zur Zeit nicht unterstützt. Zurzeit können Sie Dialogfelder nur über die Methode [Navigation](reference/navigation.md) in modellgesteuerten Anwendungen aufrufen.

### <a name="how-can-i-call-other-components-from-within-another-component"></a>Wie kann ich andere Komponenten aus einer anderen Komponente heraus aufrufen?

Dies wird vom Framework nicht nativ unterstützt. Sie können eine von vielen Bibliotheken von Drittanbietern verwenden, um diese Funktionalität in Ihren Komponenten zu aktivieren.

### <a name="can-i-bundle-font-resources"></a>Kann ich Font-Ressourcen bündeln?

Derzeit werden Schriftartenressourcen (Dateien mit der Dateierweiterung .ttf) vom Framework nicht unterstützt.

### <a name="can-i-use-img-resource-property-in-canvas-apps"></a>Kann ich die img-Ressourceneigenschaft in Canvas Apps verwenden?

Derzeit werden [img](manifest-schema-reference/img.md) Ressourcen in Canvas-Apps nicht unterstützt.

## <a name="related-topics"></a>Verwandte Themen

[Power Apps component framework-API-Referenz](reference/index.md)<br/>
[Power Apps component framework Übersicht](overview.md)
