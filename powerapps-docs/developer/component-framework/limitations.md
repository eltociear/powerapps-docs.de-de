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
ms.openlocfilehash: 61567ce7d1dff080c1e953751796973105f66885
ms.sourcegitcommit: 59f0b3adc56279b5673cbf04b4a55bd7678e1ea7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2020
ms.locfileid: "3091237"
---
# <a name="limitations"></a>Einschränkungen 

Mit der Veröffentlichung des Power Apps component framework können Sie nun Ihre eigenen Codekomponenten erstellen, um die Benutzerfreundlichkeit von modellgetriebenen Anwendungen und Canvas-Anwendungen zu verbessern. Auch wenn Sie Ihre eigenen Komponenten erstellen können, gibt es einige Einschränkungen, die Entwickler einschränken, die einige Funktionen in den Codekomponenten implementieren. Es folgen einige der Einschränkungen:

1. Common Data Service abhängige APIs, einschließlich WebAPI zusammen mit wenigen anderen APIs, sind für diese experimentelle Vorschau nicht verfügbar. Für die individuelle API-Verfügbarkeit für diese experimentelle Vorschau-Version siehe [Power Apps component framework-API-Referenz](reference/index.md).
2. Codekomponenten sollten den gesamten Code einschließlich externer Bibliotheksinhalte in das primäre Codebundle bündeln. Um ein Beispiel dafür zu sehen, wie die Befehlszeilenschnittstelle Power Apps bei der Bündelung Ihrer externen Bibliotheksinhalte zu einem komponentenspezifischen Bundle helfen kann, siehe Beispiel [Angular Flip Komponente](sample-controls/angular-flip-control.md).

   > [!NOTE]
   > Die Unterstützung von gemeinsamen Bibliotheken über Komponenten hinweg, die Bibliotheksknoten im Komponentenmanifest verwenden, wird noch nicht unterstützt. Es prüfen dies und werden diese Funktion in einer zukünftigen Versionen hinzufügen.

## <a name="related-topics"></a>Verwandte Themen

[Power Apps component framework-API-Referenz](reference/index.md)<br/>
[Power Apps component framework Übersicht](overview.md)
