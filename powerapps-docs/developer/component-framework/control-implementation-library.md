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
ms.openlocfilehash: febda5c1c52b482db449b370d114c771cb2984eb
ms.sourcegitcommit: 310dd3dc68ffebe6a416450836ac0ba988b84fb4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "3162171"
---
# <a name="component-implementation-library"></a>Komponentenimplementierungsbibliothek

Die Implementierung der Komponentenbibliothek ist einer der wichtigen Schritte, wenn Sie Codekomponenten mithilfe von Power Apps component framework entwickeln. Entwickler können die Komponentenbibliothek mithilfe von TypeScript implementieren.

Jede Code-Komponente muss über eine Bibliothek verfügen, die die Definition einer Funktion umfasst, die ein Objekt zurückgibt, das die Methoden implementiert, die in der Code-Komponentenschnittstelle beschrieben werden. 

Das Objekt implementiert die folgenden Methoden:

- [init](reference/control/init.md) (erforderlich)
- [updateView](reference/control/updateview.md) (erforderlich)
- [getOutputs](reference/control/getoutputs.md) (optional)
- [destroy](reference/control/destroy.md) (erforderlich)

Diese Methode steuert den Lebenszyklus der Codekomponente.

