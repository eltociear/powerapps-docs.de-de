---
title: Einschränkungen von powerapps-Komponenten Framework | MicrosoftDocs
description: Einschränkungen bei Verwendung des powerapps-Komponenten Frameworks
author: nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: index-page
ms.assetid: 18e88d702-3349-4022-a7d8-a9adf52cd34f
ms.author: nabuthuk
ms.openlocfilehash: aabcf4518e71648797c795a006c2d842f3e5ff01
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346737"
---
# <a name="limitations"></a>Einschränken 

Mit der Veröffentlichung von powerapps Component Framework können Sie nun eigene Code Komponenten erstellen, um die Benutzeroberfläche in Modell gesteuerten apps und Canvas-apps zu verbessern. Obwohl Sie eigene Komponenten erstellen können, gibt es einige Einschränkungen, die Entwicklern das Implementieren einiger Features in den Code Komponenten einschränken. Im folgenden finden Sie einige der Einschränkungen:

1. Nur der *Feldtyp* von Komponenten wird in der experimentellen Vorschau für Canvas-apps und nicht in den *DataSet* -typkomponenten unterstützt. 
2. Common Data Service abhängige APIs, einschließlich WebAPI, sowie einige andere APIs, sind für diese experimentelle Vorschau nicht verfügbar. Eine individuelle API-Verfügbarkeit für diese experimentelle Vorschauversion finden Sie unter [powerapps Component Framework-API-Referenz](reference/index.md).
3. Code Komponenten sollten den gesamten Code einschließlich externer Bibliotheksinhalte in das primäre Code Bündel bündeln. Ein Beispiel dafür, wie die powerapps-Befehlszeilenschnittstelle beim bündeln externer Bibliotheksinhalte in ein Komponenten spezifisches Bündel helfen kann, finden Sie unter Beispiel für eine [Angular Flip-Komponente](sample-controls/angular-flip-control.md) .

   > [!NOTE]
   > Die Unterstützung für freigegebene Bibliotheken über Komponenten hinweg, die Bibliotheks Knoten im Komponenten Manifest verwenden, wird noch nicht unterstützt. Wir überprüfen dies und werden diese Funktion in einer zukünftigen Version hinzufügen.
4. Das Definieren mehrerer Komponenten in einer einzelnen Manifest-Datei wird noch nicht unterstützt.
5. Das Aufrufen von Prozessen und Aktionen wird noch nicht unterstützt. Dialogfelder können nur mithilfe der [Navigations](reference/navigation.md) Methode aufgerufen werden.
6. Das Aufrufen einer Komponente aus einer anderen Code Komponente wird noch nicht unterstützt.
7. Derzeit wird die Schriftart Ressource (. tff) noch nicht unterstützt.

## <a name="related-topics"></a>Verwandte Themen

[API-Referenz für das powerapps-Komponenten Framework](reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](overview.md)
