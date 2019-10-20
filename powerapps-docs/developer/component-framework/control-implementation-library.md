---
title: Komponenten Implementierungs Bibliothek | Microsoft-Dokumentation
description: Erstellen von Code Komponenten mithilfe von JavaScript oder typescript
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
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72347243"
---
# <a name="component-implementation-library"></a>Komponenten Implementierungs Bibliothek

Das Implementieren der Komponentenbibliothek ist einer der wichtigsten Schritte beim Entwickeln von Code Komponenten mithilfe des powerapps-Komponenten-Frameworks. Entwickler können die Komponentenbibliothek mithilfe von typescript implementieren. Jede Code Komponente muss über eine Bibliothek verfügen, die die Definition einer Funktion enthält, die ein Objekt zurückgibt, das die in der Code Component-Schnittstelle beschriebenen Methoden implementiert. 

Das-Objekt implementiert die folgenden Methoden:

- [Init](reference/control/init.md) (erforderlich)
- [UpdateView](reference/control/updateview.md) (erforderlich)
- [getoutputs](reference/control/getoutputs.md) (optional)
- [zerstören](reference/control/destroy.md) (erforderlich)

Diese Methoden steuern den Lebenszyklus der Code Komponente.

