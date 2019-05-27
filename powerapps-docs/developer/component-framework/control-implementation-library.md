---
title: Komponentenimplementierungsbibliothek | Microsoft Docs
description: Erstellen Sie benutzerdefinierte Komponenten mit JavaScript oder TypeScript
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d100dc3-bd82-4b45-964c-d90eaebc0735
---

[!INCLUDE[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Die Komponentenbibliothek zu implementieren ist eine der wichtigen Schritte, wenn Sie benutzerdefinierte Komponenten mithilfe des PowerApps-Komponentenframeworks entwickeln. Entwickler können die Komponentenbibliothek mithilfe von TypeScript implementieren. Jede benutzerdefinierte Komponente muss über eine Bibliothek verfügen, die die Definition einer Funktion umfasst, die ein Objekt zurückgibt, das die Methoden implementiert, die in der benutzerdefinierten Komponentenschnittstelle beschrieben werden. 

> [!IMPORTANT]
> - PowerApps-Komponentenframework ist eine Vorschaufunktion.
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)] 
> - [!INCLUDE[cc_preview_features_no_MS_support](../../includes/cc-preview-features-no-ms-support.md)]

Das Objekt implementiert die folgenden Methoden:

- [init](reference/control/init.md) (erforderlich)
- [updateView](reference/control/updateview.md) (erforderlich)
- [getOutputs](reference/control/getoutputs.md) (optional)
- [destroy](reference/control/destroy.md) (erforderlich)

Diese Methode steuert den Lebenszyklus der benutzerdefinierten Komponente.
