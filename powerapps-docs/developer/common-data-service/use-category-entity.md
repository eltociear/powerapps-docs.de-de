---
title: Verwenden der Kategorieentität (Common Data Service) | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Kategorisierung von Entitätsdatensätzen mithilfe der Kategorieentität.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: b506c926fd2ac43d7fd15782e0f32d3402ed8989
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155198"
---
# <a name="use-the-category-entity"></a>Verwenden der Kategorieentität

Kategorisieren von Entitätsdatensätzen in Common Data Service hilft Ihnen die Datensätze zu kennzeichnen, damit Sie sie leicht suchen können. Verwenden Sie die `Category`-Entität, um eine Baumstruktur der Kategorien in Common Data Service zu erstellen und zu verwalten, und weisen dann Entitätsdatensätze einer oder mehreren Kategorien zu.  
  
 Eine Kategorie kann mehrere untergeordnete Kategorien haben, aber eine untergeordnete Kategorie kann nur eine übergeordnete Kategorie haben. Das Löschen eines übergeordneten `Category`-Datensatzes löscht automatisch alle seine untergeordneten Datensätze und Entitätszuordnungen. Sie definieren eine übergeordnete Kategorie für eine Kategorie unter Verwendung des `Category.ParentCategoryId`-Attributes.  
  
 Verwenden Sie das `Category.SequenceNumber`-Attribut, um den Anzeigereihenfolge für Kategorien in der Hierarchie programmgesteuert zu definieren.  Wenn Sie eine neue Kategorie unter Verwendung des Webclients hinzufügen, wird sie automatisch nach der letzten Kategorie in der Hierarchie hinzugefügt. Sie können auch das `Category.CategoryNumber`-Attribut verwenden, um programmgesteuert eine Zahl für Kategorie festzulegen oder zu aktualisieren, damit Sie leicht eine Gruppe von Kategorien zu unterscheiden. Die Kategoriezahl kann programmatisch auf jeden Wert eingestellt werden, wird aber automatisch eingestellt, wenn Sie eine Kategorie unter Verwendung des Webclient basierend auf dem Präfix für die automatische Nummerierung erstellen, das vom Administrator für Kategorien im Webclient angegeben wird (Registerkarte **Einstellungen** > **Administration** > **Automatische Nummerierung** > **Kategorien**).  
  
 Sie können `Category`-Datensätze dem Systems und benutzerdefinierte Entitätsdatensätze zuweisen, indem Sie Beziehungen und Verbindungen verwenden. Ein Kategoriedatensatz kann verschiedenen Entitätsdatensätzen zugeordnet werden. Zum Beispiel können Sie einen `Category`-Datensatz `Account`, `Contact` und `Incident` zuweisen.   

