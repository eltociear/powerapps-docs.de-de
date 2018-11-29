---
title: Menübandbefehle definieren (modellgesteuerte Apps) | Microsoft Docs
description: 'Ein Menübandbefehl erstellt eine wiederverwendbare Definition, auf die von Menübandkontrollelementen verwiesen werden kann.'
keywords: ''
ms.date: 10/31/2018
ms.service:
  - powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: 60933770-8c7c-499c-12b4-8b64f6eedb35
author: JimDaly
ms.author: jdaly
manager: shilpas
ms.reviewer: null
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="define-ribbon-commands"></a>Menübandbefehle definieren

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/customize-dev/define-ribbon-commands -->

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
 [Definieren von Menüband-Aktivierungsregeln](define-ribbon-enable-rules.md)
