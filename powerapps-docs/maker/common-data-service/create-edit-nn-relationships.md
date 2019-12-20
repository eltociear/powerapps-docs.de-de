---
title: Überblick über die Erstellung von m:n-Entitätsbeziehungen in Common Data Service | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie N:N-Beziehungen erstellen
ms.custom: ''
ms.date: 05/29/2018
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
ms.assetid: 248cecfd-c9e8-430b-b4b0-860669866084
caps.latest.revision: 33
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 907a1147630cc779e6c1af7be2486548f1907c5a
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2865731"
---
# <a name="create-many-to-many-entity-relationships-overview"></a>Überblick über die Erstellung von n:m-Entitätsbeziehungen

1:n-Entitätsbeziehungen richten eine Hierarchie zwischen Datensätzen ein. Mit viele-zu-viele-Beziehungen (N:N) gibt es keine explizite Hierarchie. Es müssen keine Suchfelder oder Verhaltensweisen konfiguriert werden. Mit n:n-Beziehungen erstellte Datensätze gelten als gleichwertig, und die Beziehung ist reziprok.  
  
Mit n:n-Beziehungen speichert eine Beziehungs (oder Überschneidungs)-Entität die Daten, die die Entitäten zuweist. Diese Entität weist eine n:n-Beziehung zu beiden verknüpften Entitäten auf und speichert nur die für die Definition der Beziehung benötigten Werte. Sie können einer Beziehungsentität keine benutzerdefinierten Felder hinzufügen und sie wird nie in der Benutzeroberfläche angezeigt. 
  
Das Erstellen einer n:n-Beziehung erfordert das Auswählen der zwei Entitäten, die an der Beziehung beteiligt sein sollen. Bei modellgesteuerten Apps können Sie entscheiden, wie die entsprechenden Listen in der Navigation für die Entität verfügbar sein sollen. Diese sind dieselben Optionen, die für die primäre Entität in 1:n-Beziehungen verwendet werden. Weitere Informationen: [Navigationsbereichselement für die primäre Entität](create-edit-1n-relationships-solution-explorer.md#navigation-pane-item-for-primary-entity)
  
Nicht alle Entitäten können mit N:N-Beziehungen verwendet werden. Wenn die Entität nicht im Designer ausgewählt werden kann, können Sie eine neue n:n-Beziehung mit dieser Entität erstellen. Weitere Informationen: [Entwicklerdokumentation: Entitätsbeziehungseignung](https://docs.microsoft.com/dynamics365/customer-engagement/developer/entity-relationship-eligibility)

Es gibt zwei Ansicht, die Sie verwenden können, um 1:n (eine-zu-vielen) oder N:1 (viele-zu-einer) Beziehungen:

|Designer| Beschreibung|
|--|--|
|[Power Apps-Portal](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|Gibt eine einfache konzentrierte Erfahrung, aber einige besondere Einstellungen sind nicht verfügbar.<br />Weitere Informationen: [m:n-Entitätsbeziehungen in Common Data Service mit Hilfe des Power Apps-Portals erstellen](create-edit-nn-relationships-portal.md)|
|Projektmappen-Explorer|Nicht so einfach, aber gibt mehr Flexibilität für weniger allgemeine Anforderungen.<br />Weitere Informationen: [Erstellen von m:n-Entitätsbeziehungen in Common Data Service mithilfe des Projektmappen-Explorers](create-edit-nn-relationships-solution-explorer.md) |

> [!NOTE]
> Sie können eine neue n: n-Entitätsbeziehung folgendermaßen auch in Ihrer Umgebung erstellen mithilfe des folgenden:
> - Importieren Sie eine Lösung, die die Definition der Beziehung enthält. Weitere Informationen dazu finden Sie [Lösungen importieren, aktualisieren und exportieren](import-update-export-solutions.md)
> - Ein Entwickler kann [Metadatendienste](../../developer/common-data-service/metadata-services.md) verwenden, um ein Programm zum Schreiben, um Entitätsbeziehungen zu erstellen und zu aktualisieren. Weitere Informationen: [Entwicklerdokumentation: Entitätsbeziehungseignungsmetadaten anpassen](https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-entity-relationship-metadata)

Die Informationen in diesem Thema helfen Ihnen auswählen, welche Designer Sie verwenden können. 

Sie sollten das Power Apps-Portal verwenden, um Viele-zu-viele (m:n)-Entitätsbeziehungen zu erstellen und zu bearbeiten, es sei den, Sie müssen eine der folgenden Anforderungen erfüllen:

- Konfigurieren Sie Navigationsbereichsoptionen für modellgesteuerte Apps.
- Verbergen Sie die Beziehung in der erweiterten Suche in modellgesteuerten Apps.

## <a name="see-also"></a>Siehe auch

[Erstellen und Bearbeiten von Beziehungen zwischen Entitäten](create-edit-entity-relationships.md)<br />
[n:m-Entitätsbeziehungen in Common Data Service mit Hilfe des Power Apps-Portals erstellen](create-edit-nn-relationships-portal.md)<br />
[Erstellen von n:n-Entitätsbeziehungen in Common Data Service mithilfe des Projektmappen-Explorers](create-edit-nn-relationships-solution-explorer.md)<br />
[Entwicklerdokumentation: Entitätsbeziehungseignungsmetadaten anpassen](https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-entity-relationship-metadata)<br />
[Entwicklerdokumentation: Entitätsbeziehungseignung](https://docs.microsoft.com/dynamics365/customer-engagement/developer/entity-relationship-eligibility)
