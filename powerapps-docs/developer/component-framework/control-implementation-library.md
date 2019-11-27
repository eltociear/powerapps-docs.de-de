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
ms.openlocfilehash: 31b7d2b30a1ef83ca4400011d50854713cb260f6
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748486"
---
# <a name="component-implementation-library"></a>Komponentenimplementierungsbibliothek

Die Komponentenbibliothek zu implementieren ist einer der wichtigen Schritte, wenn Sie Code-Komponenten mithilfe des PowerApps Component Framework entwickeln. Entwickler können die Komponentenbibliothek mithilfe von TypeScript implementieren. Jede Code-Komponente muss über eine Bibliothek verfügen, die die Definition einer Funktion umfasst, die ein Objekt zurückgibt, das die Methoden implementiert, die in der Code-Komponentenschnittstelle beschrieben werden. 

Das Objekt implementiert die folgenden Methoden:

- [init](reference/control/init.md) (erforderlich)
- [updateView](reference/control/updateview.md) (erforderlich)
- [getOutputs](reference/control/getoutputs.md) (optional)
- [destroy](reference/control/destroy.md) (erforderlich)

Diese Methode steuert den Lebenszyklus der Codekomponente.

