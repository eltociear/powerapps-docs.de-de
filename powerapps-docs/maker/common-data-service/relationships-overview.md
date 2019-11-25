---
title: Entitätsübersicht in PowerApps | Microsoft-Dokumentation
description: Entitäten mit dem PowerApps-Portal erstellen und bearbeiten
ms.custom: ''
ms.date: 07/25/2018
ms.reviewer: ''
ms.service: powerapps
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
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9fd6f2bf14a8007dd2b4f840a901316a0d3607cd
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2701001"
---
# <a name="entity-relationships-overview"></a>Überblick über Entitätsbeziehungen

Entitätsbeziehungen definieren die Möglichkeiten, auf welche Weise Entitätsdatensätze Datensätzen anderer Entitäten oder der gleichen Entität zugeordnet werden können. Es gibt zwei Typen von Entitätsbeziehungen.
- **1: n-Beziehungen** Bei Eins-zu-viele-Entitätsbeziehung können viele verweisende (zugehörige) Entitätsdatensätze einem einzigen referenzierten (primären) Entitätsdatensatz zugeordnet werden. Der referenzierte Entitätsdatensatz wird manchmal als "übergeordneter Datensatz" bezeichnet, und Datensätze der verweisenden Entität als "untergeordnete Datensätze".  Eine n: 1-Beziehung ist nur die untergeordnete Perspektive einer 1: n-Beziehung.
- **n:n-Beziehungen** In einer Viele-zu-viele-Entitätsbeziehung können viele Entitätsdatensätze vielen anderen Entitätsdatensätzen zugeordnet werden. Mit einer n:n-Beziehung verknüpfte Datensätze gelten als gleichwertig, und die Beziehung ist reziprok. 

## <a name="see-also"></a>Siehe auch
[Erstellen einer Beziehung zwischen Entitäten](data-platform-entity-lookup.md) <br/>
[n:m-Entitätsbeziehungen in Common Data Service mit Hilfe des PowerApps-Portals erstellen](create-edit-nn-relationships-portal.md)
