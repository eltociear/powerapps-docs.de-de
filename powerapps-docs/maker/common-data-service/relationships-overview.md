---
title: Entitätenübersicht in PowerApps | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie über das PowerApps-Portal Entitäten erstellen und bearbeiten können.
ms.custom: ''
ms.date: 07/25/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: ''
caps.latest.revision: 0
ms.author: matp
manager: kvivek
ms.openlocfilehash: 1c45941a7b00e9393aab429d2573b2e48964a4de
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39687905"
---
# <a name="entity-relationships-overview"></a>Übersicht über Entitätsbeziehungen

Entitätsbeziehungen definieren die Art und Weise, wie Entitätsdatensätze den Datensätzen von anderen Entitäten oder derselben Entität zugeordnet werden können. Es gibt zwei Arten von Entitätsbeziehungen.
- **1:n-Beziehungen**. In einer 1:n-Entitätsbeziehung können viele verweisende (verwandte) Entitätsdatensätze einem einzelnen verwiesenen (primären) Entitätsdatensatz zugeordnet werden. Der Datensatz der verwiesenen Entität wird manchmal als „übergeordnetes Element“ und die Datensätze der verweisenden Entität werden als „untergeordnete Elemente“ bezeichnet.  Eine n:1-Beziehung besteht demnach lediglich aus Sicht des untergeordneten Elements einer 1:n-Beziehung.
- **m:n-Beziehungen**. In einer m:n-Entitätsbeziehung können viele Entitätsdatensätze vielen anderen Entitätsdatensätzen zugeordnet werden. Datensätze, die mit einer m:n-Beziehung verknüpft sind, können als Peers betrachtet werden, und die Beziehung ist wechselseitig. 

## <a name="see-also"></a>Siehe auch
[Erstellen einer Beziehung zwischen Entitäten](data-platform-entity-lookup.md) <br/>
[Create Many-to-many entity relationships in Common Data Service for Apps using PowerApps portal](create-edit-nn-relationships-portal.md) (Erstellen von m:n-Entitätsbeziehungen in Common Data Service for Apps über das PowerApps-Portal)