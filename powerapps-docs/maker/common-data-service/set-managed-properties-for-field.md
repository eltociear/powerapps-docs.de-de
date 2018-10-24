---
title: Festlegen von verwalteten Eigenschaften für Felder in PowerApps | Microsoft-Dokumentation
description: Informationen zum Festlegen von verwalteten Eigenschaften für ein Feld
ms.custom: ''
ms.date: 06/19/2018
ms.reviewer: ''
ms.service: crm-online
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
ms.openlocfilehash: be3b04bbc324520904c765506e32d6027927e214
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39689114"
---
# <a name="set-managed-properties-for-fields"></a>Festlegen von verwalteten Eigenschaften für Felder

<a name="BKMK_SettingManagedProperties"></a>   

 Verwaltete Eigenschaften gelten nur, wenn Sie einer verwalteten Projektmappe Felder hinzufügen und die Projektmappe in eine andere Umgebung importieren. Diese Einstellungen ermöglichen einem Projektmappenersteller, die Anpassungsmöglichkeiten der Benutzer, die die verwaltete Projektmappe installieren, zu steuern, wenn sie dieses Feld anpassen. Um verwaltete Eigenschaften für ein Feld festzulegen, wählen Sie in der Menüleiste **Verwaltete Eigenschaften** aus.  
  
 Die Option **Kann angepasst werden** steuert alle anderen Optionen. Wenn diese Option `False` ist, gilt keine der anderen Einstellungen. Wenn sie `True` ist, können Sie die anderen Anpassungsoptionen festlegen.  
  
 Wenn das Feld angepasst werden kann, legen Sie die folgenden Optionen auf `True` oder `False` fest.  
  
- **Anzeigename kann geändert werden**  
  
- **Kann Erforderlichkeitsstufe ändern**  
  
- **Ändern zusätzlicher Eigenschaften möglich**  
  
 Diese Optionen sind selbsterklärend. Wenn Sie alle einzelnen Optionen auf `False` setzen, können Sie auch **Kann angepasst werden** auf `False` setzen.  

 ## <a name="next-steps"></a>Nächste Schritte

 [Erstellen und Bearbeiten von Feldern](create-edit-fields.md)