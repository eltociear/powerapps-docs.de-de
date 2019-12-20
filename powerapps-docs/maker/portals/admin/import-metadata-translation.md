---
title: Importieren der Metadatenübersetzung | Microsoft-Dokumentation
description: Anleitungen zum Importieren der Metadatenübersetzung.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/21/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 6e1f577e5097aead282b6da9338acfd5d1f36364
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2862618"
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