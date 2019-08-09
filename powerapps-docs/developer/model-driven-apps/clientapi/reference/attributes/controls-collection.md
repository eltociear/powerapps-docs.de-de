---
title: Steuerelementsammlung (Client-API-Referenz) | MicrosoftDocs
description: 'Erfahren Sie darüber, wie auf die mit Attributen verbundenen Steuerelemente zuzugreifen.'
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: d5f3c0c5-b267-42a8-82e8-8c4a1cda3752
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="controls-collection-client-api-reference"></a>Steuerelementsammlung (Client-API-Referenz) | MicrosoftDocs



Verwenden Sie die Steuerelementsammlung, um auf die mit Attributen verbundenen Steuerelemente zuzugreifen. 

Da jedes Attribut mehr als einmal auf der Seite angezeigt werden kann, bietet die Steuerelement-Sammlung Zugriff auf alle Steuerelemente, die dieses Attribut darstellen. Wenn das Attribut nur durch ein Feld auf der Seite dargestellt wird, ist die Länger der Collection 1. Wenn Sie die control getName-Methode verwenden, ist der Name des ersten Steuerelements derselbe wie der Name des Attributs. Die zweite Instanz eines Steuerelements für dieses Attribut ist **\<attributeName>1**. Das Muster **\<attributeName>+N** wird für jedes zusätzliche Steuerelement fortgesetzt, das dem Formular für ein bestimmtes Attribut hinzugefügt wird.

Wenn ein Formular ein Geschäftsprozessfluss-Steuerelement in der Kopfzeile anzeigt, werden zusätzliche Steuerelemente für jedes Attribut hinzugefügt, das im Geschäftsprozessfluss angezeigt wird. Diese Steuerelemente enthalten einen eindeutigen Namen wie zum Beispiel: **header\_process\_\<attribute name>**.

Wenn Aktionen für Steuerelemente ausgeführt werden, die an einem Attribut gebunden sind, sollten Sie immer bedenken, dass das Steuerelement möglicherweise mehrmals auf der Seite enthalten ist, und Sie sollten generell die gleichen Aktionen für jedes Steuerelement für das Attribut ausführen. Diesen Vorgang können Sie ausführen, indem Sie eine Schleife durch die gesamte Attributsteuerelementsammlung und die Aktionen für jedes Steuerelement ausführen.

### <a name="related-topics"></a>Verwandte Themen

[Attribute (Client-API-Referenz)](../attributes.md)


