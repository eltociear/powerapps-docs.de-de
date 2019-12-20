---
title: Komponentenimplementierungsbibliothek | Microsoft Docs
description: Erstellen von Code-Komponenten mit JavaScript oder TypeScript
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d100dc3-bd82-4b45-964c-d90eaebc0735
ms.openlocfilehash: 311bb23bac05ffc49be9366d281226fd755c8faa
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2862016"
---
# <a name="component-implementation-library"></a>Komponentenimplementierungsbibliothek

Die Komponentenbibliothek zu implementieren ist einer der wichtigen Schritte, wenn Sie Code-Komponenten mithilfe des Power Apps Component Framework entwickeln. Entwickler können die Komponentenbibliothek mithilfe von TypeScript implementieren. Jede Code-Komponente muss über eine Bibliothek verfügen, die die Definition einer Funktion umfasst, die ein Objekt zurückgibt, das die Methoden implementiert, die in der Code-Komponentenschnittstelle beschrieben werden. 

Das Objekt implementiert die folgenden Methoden:

- [init](reference/control/init.md) (erforderlich)
- [updateView](reference/control/updateview.md) (erforderlich)
- [getOutputs](reference/control/getoutputs.md) (optional)
- [destroy](reference/control/destroy.md) (erforderlich)

Diese Methode steuert den Lebenszyklus der Codekomponente.

