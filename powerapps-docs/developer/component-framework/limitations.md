---
title: Einschränkungen des Power Apps component framework | MicrosoftDocs
description: Einschränkungen durch das Power Apps component framework
author: nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: index-page
ms.assetid: 18e88d702-3349-4022-a7d8-a9adf52cd34f
ms.author: nabuthuk
ms.openlocfilehash: 0e594f09712ea88d92bcf08408e4673d9039363a
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2861984"
---
# <a name="limitations"></a>Einschränkungen 

Mit der Veröffentlichung des Power Apps component framework können Sie nun Ihre eigenen Codekomponenten erstellen, um die Benutzerfreundlichkeit von modellgetriebenen Anwendungen und Canvas-Anwendungen zu verbessern. Auch wenn Sie Ihre eigenen Komponenten erstellen können, gibt es einige Einschränkungen, die Entwickler einschränken, die einige Funktionen in den Codekomponenten implementieren. Es folgen einige der Einschränkungen:

1. Nur der Typ *Feld* der Komponenten wird in der experimentellen Vorschau für Canvas-Anwendungen unterstützt und nicht die Typkomponenten *Datensatz*. 
2. Common Data Service abhängige APIs, einschließlich WebAPI zusammen mit wenigen anderen APIs, sind für diese experimentelle Vorschau nicht verfügbar. Für die individuelle API-Verfügbarkeit für diese experimentelle Vorschau-Version siehe [Power Apps component framework-API-Referenz](reference/index.md).
3. Codekomponenten sollten den gesamten Code einschließlich externer Bibliotheksinhalte in das primäre Codebundle bündeln. Um ein Beispiel dafür zu sehen, wie die Befehlszeilenschnittstelle Power Apps bei der Bündelung Ihrer externen Bibliotheksinhalte zu einem komponentenspezifischen Bundle helfen kann, siehe Beispiel [Angular Flip Komponente](sample-controls/angular-flip-control.md).

   > [!NOTE]
   > Die Unterstützung von gemeinsamen Bibliotheken über Komponenten hinweg, die Bibliotheksknoten im Komponentenmanifest verwenden, wird noch nicht unterstützt. Es prüfen dies und werden diese Funktion in einer zukünftigen Versionen hinzufügen.
4. Das Definieren mehrerer Komponenten in einer einzigen Manifestdatei wird noch nicht unterstützt.
5. Das Aufrufen von Prozessen und Aktionen wird noch nicht unterstützt. Dialogfenster können Sie nur über die Methode [Navigation](reference/navigation.md) aufrufen.
6. Der Aufruf einer Komponente aus einer anderen Codekomponente wird noch nicht unterstützt.
7. Derzeit wird die Font-Ressource (.tff) noch nicht unterstützt.

## <a name="related-topics"></a>Verwandte Themen

[Power Apps component framework-API-Referenz](reference/index.md)<br/>
[Power Apps component framework Übersicht](overview.md)
