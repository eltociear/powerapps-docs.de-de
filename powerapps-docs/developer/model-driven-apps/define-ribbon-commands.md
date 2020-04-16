---
title: Menübandbefehle definieren (modellgesteuerte Apps) | Microsoft Docs
description: Ein Menübandbefehl erstellt eine wiederverwendbare Definition, auf die von Menübandkontrollelementen verwiesen werden kann.
keywords: ''
ms.date: 03/27/2020
ms.service: powerapps
ms.topic: article
ms.assetid: 60933770-8c7c-499c-12b4-8b64f6eedb35
author: Nkrb
ms.author: nabuthuk
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3ea2f5cfdffb19589719780e7da1afaf3c510243
ms.sourcegitcommit: ebb4bb7ea7184e31dc95f0c301ebef75fae5fb14
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2020
ms.locfileid: "3218555"
---
# <a name="define-ribbon-commands"></a>Menübandbefehle definieren

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/define-ribbon-commands -->

Ein *Menübandbefehl* erstellt eine wiederverwendbare Definition, auf die von Menübandkontrollelementen verwiesen werden kann.  
  
## <a name="ribbon-command-elements"></a>Menübandbefehlselemente  
 Das `<CommandDefinition>` Element definiert einen Befehl im Menüband. Das `Id` Attribut definiert einen eindeutigen Bezeichner für den Befehl, auf die von Menübandkontrollelementen verwiesen werden kann, indem die `Command` Parameter verwendet werden.  
  
 Eine Menübandbefehl definiert drei Punkte:  
  
- **Regeln aktivieren**: Gibt an, ob ein bestimmtes Menübandsteuerelement aktiviert ist.  
  
- **Anzeigen-Regeln**: Gibt an, ob ein bestimmtes Menübandelement angezeigt wird.  
  
- **Aktionen**: Gibt an, welcher Code ausgeführt wird, wenn ein Menübandsteuerelement verwendet wird.  
  
> [!IMPORTANT]
>  Alle Befehlsdefinitionen werden auf den Computer eines Benutzers heruntergeladen, damit sie bei Laufzeit ausgewertet werden können. Das bedeutet, dass ein Benutzer, der keine Berechtigung hat, ein bestimmtes Steuerelement im Menüband zu sehen, den Browserbefehl **Quelle anzeigen** verwenden, den Code überarbeiten und bestimmen kann, ob ein Steuerelement besteht, das nicht angezeigt wird.  
  
### <a name="see-also"></a>Siehe auch  
 [Passen Sie Befehle und das Menüband an](customize-commands-ribbon.md)   
 [Verwenden von lokalisierten Bezeichnungen in Menübändern](use-localized-labels-ribbons.md)   
 [Definieren von Menüband-Aktivierungsregeln](define-ribbon-enable-rules.md) [Beheben von Menübandproblemen](https://support.microsoft.com/help/4552163)
