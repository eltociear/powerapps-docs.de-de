---
title: Importieren der Metadatenübersetzung | Microsoft-Dokumentation
description: Anleitungen zum Importieren der Metadatenübersetzung.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/21/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: a648efdea5538dbedc431f0c3299b23948d39eb2
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "2978015"
---
# <a name="import-metadata-translation"></a>Importieren der Metadatenübersetzung

Wenn Sie ein Portal bereitstellen, werden die mit dem Portal verknüpften Lösungen für die Organisation installiert. Während der Installation der Lösungen werden die Lösungsmetadatenübersetzungen (beispielsweise Feldname, Formularname, Ansichtname usw.) nur für die Sprachen installiert, die zurzeit für die Organisation aktiviert sind. Wenn Sie in der Zukunft eine weitere Sprache aktivieren, werden die Metadaten für die neu aktivierte Sprache nicht automatisch installiert. Um die Metadatenübersetzung für die neu aktivierte Sprache abzurufen, müssen Sie die Metadatenübersetzung aus dem Power Apps-Portaladministratorcenter importieren.

## <a name="to-import-metadata-translation"></a>So importieren Sie die Metadatenübersetzung

1.  Öffnen Sie das [Admin Center für Power Apps-Portale](admin-overview.md).

2.  Wechseln Sie zu **Portalaktionen** > **Aktuelle Metadatenübersetzungen abrufen**. Anschließend wird ein Bestätigungsfenster angezeigt, in dem Sie gefragt werden, ob die Portallösungen aktualisiert werden sollen.

3.  Wählen Sie **Aktualisieren**. Die Portallösungen werden mit der aktuellen Metadatenübersetzung aktualisiert.

> [!Note]
> - Wenn die neueste Version des Portalpakets verfügbar ist, wird es nicht aktualisiert. Die Portallösungen werden in derselben Version aktualisiert. Um Ihre Portallösungen auf der Grundlage der neuesten verfügbaren Pakete zu aktualisieren, müssen Sie auf das Solution Admin Center zugreifen.
> - Wenn ein Benutzer Daten in Common Data Service geändert hat, werden die vorhandenen Daten während des Updates nicht überschrieben.
> - Wenn die Portallösungen installiert werden, kann das Lösungsupdate nicht ausgelöst werden.