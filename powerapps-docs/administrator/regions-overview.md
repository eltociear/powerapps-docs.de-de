---
title: Übersicht über die Regionen | Microsoft-Dokumentation
description: 'Regionen in PowerApps: wo Apps bereitgestellt werden, verfügbare Regionen, für bestimmte Regionen spezifische Funktionen'
services: ''
suite: powerapps
documentationcenter: na
author: skjerland
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/21/2018
ms.author: manasma
ms.openlocfilehash: ab5443ae628a80d52d5bbcb1fa46ceed05391794
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="regions-overview-in-powerapps"></a>Übersicht der Regionen in PowerApps
## <a name="how-do-i-find-out-where-my-app-is-deployed"></a>Wie finde ich heraus, wo meine App bereitgestellt ist?
Ihre App ist in der Region bereitgestellt, in der die Umgebung gehostet ist. Wenn Ihre Umgebung z.B. in der Region Europa erstellt wird, wird Ihre App in europäischen Rechenzentren bereitgestellt.

Wenn Sie Administrator sind, können Sie die Region für die einzelnen Umgebungen im PowerApps Admin Center bestimmen.

* Wechseln Sie zum [Admin Center](https://admin.powerapps.com), und melden Sie sich mit Ihrem Geschäftskonto an.
  
    Im Admin Center sind alle vorhandenen Umgebungen auf der Registerkarte **Umgebungen** aufgelistet. Diese Liste zeigt die **Region**, in der Ihre App bereitgestellt ist:
  
   ![Registerkarte „Umgebungen“](./media/regions-overview/environment-list.png)

## <a name="what-regions-are-available"></a>Welche Regionen sind verfügbar?
* USA
* Kanada
* Europa
* Asien
* Australien
* Indien
* Japan
* Vereinigtes Königreich

## <a name="what-features-are-specific-to-a-given-region"></a>Welche Funktionen sind spezifisch für eine bestimmte Region?
Umgebungen können in verschiedenen Regionen erstellt werden und sind dann an den betreffenden geografischen Ort gebunden. Wenn Sie eine App in einer Umgebung erstellen, wird diese App in Rechenzentren in der betreffenden geografischen Region bereitgestellt. Dies gilt auch für alle Elemente, die Sie in der betreffenden Umgebung erstellen, einschließlich Datenbanken im Common Data Service, Apps, Verbindungen, Gateways und benutzerdefinierte Connectors.

Wenn sich Ihre Benutzer in Europa befinden, sollten Sie zum Erzielen optimaler Leistung die Umgebung in der Region Europa erstellen und verwenden. Wenn Ihre Benutzer in den Vereinigten Staaten sind, erstellen und verwenden Sie die Umgebung in den USA.

> [!NOTE]
> Derzeit können Sie Datenbanken nur in einer Produktions- oder Testumgebung erstellen, die sich in der Region Ihres Azure AD- oder Office 365-Mandanten befinden. Es wird daran gearbeitet, dass in Zukunft auch Datenbanken in Umgebungen erstellt werden können, die sich nicht in der Region Ihres Mandanten befinden. Außerdem können Sie derzeit (mit PowerApps Community-Plan) noch keine Datenbanken in der Standardumgebung und keine individuelle Umgebung erstellen.

> [!NOTE]
> Lokale Datengateways sind in der Region „Indien“ und in benutzerdefinierten Umgebungen nicht verfügbar. Gateways müssen in der Standardumgebung erstellt werden.


