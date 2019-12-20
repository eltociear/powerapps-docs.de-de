---
title: Verwaltete Eigenschaften für Felder in Power Apps festlegen | MicrosoftDocs
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
ms.openlocfilehash: 0b14b5ab55fe6bbaeeb11fb2de548621eb66501a
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2865333"
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
