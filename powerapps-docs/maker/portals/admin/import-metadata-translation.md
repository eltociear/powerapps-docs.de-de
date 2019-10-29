---
title: Metadatenübersetzung importieren | MicrosoftDocs
description: Anweisungen zum Importieren der Metadatenübersetzung.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/21/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: f05a0dfb6424b11e71cf5bf4324d5e3db03a7897
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72977977"
---
# <a name="import-metadata-translation"></a>Metadatenübersetzung importieren

Wenn Sie ein Portal bereitstellen, werden die Portal bezogenen Lösungen in der Organisation installiert. Während der Installation von Projektmappen werden die Übersetzungen der Lösungs Metadaten (z. b. Feldname, Formular Name und Sichtname) nur für die derzeit in der Organisation aktivierten Sprachen installiert. Wenn Sie in Zukunft eine neue Sprache aktivieren, werden die Metadaten für die neu aktivierte Sprache nicht automatisch installiert. Sie müssen die Metadatenübersetzung aus dem powerapps-Portal Admin Center importieren, um die Metadatenübersetzung für die neu aktivierte Sprache zu erhalten.

## <a name="to-import-metadata-translation"></a>So importieren Sie die Metadatenübersetzung

1.  Öffnen Sie das [powerapps-Portal Admin Center](admin-overview.md).

2.  Wechseln Sie zu den **Portal Aktionen** > die **neuesten Metadatenübersetzungen erhalten**. Es wird ein Bestätigungsfenster mit der Frage angezeigt, ob die Portallösungen aktualisiert werden sollen.

3.  Wählen Sie **Aktualisieren**aus. Die Portallösungen werden mit der neuesten Metadatenübersetzung aktualisiert.

> [!Note]
> - Wenn die neueste Version eines Portal Pakets verfügbar ist, wird es nicht aktualisiert. Die Portallösungen werden in derselben Version aktualisiert. Um Ihre Portallösungen basierend auf den neuesten verfügbaren Paketen zu aktualisieren, müssen Sie auf das projektmappenadmin Center zugreifen.
> - Wenn ein Benutzerdaten in Common Data Service geändert hat, werden die vorhandenen Daten während des Updates nicht überschrieben.
> - Wenn die Portallösungen installiert werden, kann das Lösungs Update nicht ausgelöst werden.