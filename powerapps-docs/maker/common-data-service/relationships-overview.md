---
title: Entitätsübersicht in PowerApps | MicrosoftDocs
description: Entitäten mit dem PowerApps-Portal erstellen und bearbeiten
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
ms.assetid: null
caps.latest.revision: 0
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="entity-relationships-overview"></a>Übersicht über Entitätsbeziehungen

Entitätsbeziehungen definieren die Möglichkeiten, auf welche Weise Entitätsdatensätze Datensätzen anderer Entitäten oder der gleichen Entität zugeordnet werden können. Es gibt zwei Typen von Entitätsbeziehungen.
- **1: n-Beziehungen** Bei Eins-zu-viele-Entitätsbeziehung können viele verweisende (zugehörige) Entitätsdatensätze einem einzigen referenzierten (primären) Entitätsdatensatz zugeordnet werden. Der referenzierte Entitätsdatensatz wird manchmal als "übergeordneter Datensatz" bezeichnet, und Datensätze der verweisenden Entität als "untergeordnete Datensätze".  Eine n: 1-Beziehung ist nur die untergeordnete Perspektive einer 1: n-Beziehung.
- **n:n-Beziehungen** In einer Viele-zu-viele-Entitätsbeziehung können viele Entitätsdatensätze vielen anderen Entitätsdatensätzen zugeordnet werden. Mit einer n:n-Beziehung verknüpfte Datensätze gelten als gleichwertig, und die Beziehung ist reziprok. 

## <a name="see-also"></a>Siehe auch
[Erstellen einer Beziehung zwischen Entitäten](data-platform-entity-lookup.md) <br/>
[Erstellen von n:n-Entitätsbeziehungen in Common Data Service for Apps mithilfe des PowerApps-Portals](create-edit-nn-relationships-portal.md)
