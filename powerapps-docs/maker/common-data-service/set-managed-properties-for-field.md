---
title: Verwaltete Eigenschaften für Felder in PowerApps festlegen | MicrosoftDocs
description: Erfahren Sie, wie verwaltete Eigenschaften für ein Feld festgelegt werden
ms.custom: ''
ms.date: 06/19/2018
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
ms.assetid: 4ddcfcf3-5604-4b93-a5ee-589d4fb97fa4
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 44f56e4c3430d52c8b921ece893c893c8258c858
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2702013"
---
# <a name="set-managed-properties-for-fields"></a>Verwaltete Eigenschaften für Felder einrichten

<a name="BKMK_SettingManagedProperties"></a>   

 Verwaltete Eigenschaften gelten nur, wenn Sie in einer verwalteten Lösung Felder hinzufügen und die Lösung in eine andere Umgebung importieren. Diese Einstellungen ermöglichen einem Lösungsentwickler, die Anpassungsmöglichkeiten zu steuern, die Benutzer, die die verwaltete Lösung installieren, haben sollen, wenn sie dieses Feld anpassen. Wählen Sie zur Festlegung verwalteter Eigenschaften für ein Feld auf der Menüleiste **Verwaltete Eigenschaften** aus.  
  
 Die Option **Kann angepasst werden** steuert alle anderen Optionen. Wenn diese Option `False` ist, gelten keine der anderen Einstellungen. Wenn sie `True` ist, können Sie die anderen Anpassungsoptionen angeben.  
  
 Wenn das Entität Feld werden kann, können Sie die folgenden Optionen auf `True` oder `False` einstellen.  
  
- **Anzeigename kann geändert werden**  
  
- **Kann Erforderlichkeitsstufe ändern**  
  
- **Kann zusätzliche Eigenschaften ändern**  
  
 Diese Optionen sind selbsterklärend. Wenn Sie alle Optionen auf `False` setzen, können Sie auch einfach `False` auf **Kann angepasst werden** setzen.  

 ## <a name="next-steps"></a>Nächste Schritte

 [Erstellen und Bearbeiten von Feldern](create-edit-fields.md)
