---
title: Funktion „User“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Funktion „User“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 69da2bbdadc40421e9962de73d531b6c19554eeb
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71983473"
---
# <a name="user-function-in-powerapps"></a>Funktion „User“ in PowerApps
Gibt Informationen über den aktuellen Benutzer zurück.

## <a name="description"></a>Beschreibung
Die Funktion **User** gibt einen [Datensatz](../working-with-tables.md#records) mit Informationen über den aktuellen Benutzer zurück:

| Eigenschaft | Beschreibung |
| --- | --- |
| **User().Email** |E-Mail-Adresse des aktuellen Benutzers. |
| **User().FullName** |Vollständiger Name des aktuellen Benutzers, einschließlich Vor-und Nachnamen. |
| **User().Image** |Bild des aktuellen Benutzers. Dies ist eine Bild-URL der Form "blob:*Bezeichner*". Legen Sie die Eigenschaft **[Image](../controls/properties-visual.md)** des **[Image](../controls/control-image.md)** -Steuerelements auf diesen Wert fest, um das Bild in der App anzuzeigen. |

> [!NOTE]
> Die zurückgegebenen Informationen beziehen sich auf den aktuellen PowerApps-Benutzer.  Sie stimmen mit den Kontoinformationen überein, die in den PowerApps-Playern und in Studio angezeigt werden, die außerhalb von Apps mit Verfassern verfügbar sind.  Möglicherweise stimmen sie nicht mit den Informationen des aktuellen Benutzers in Office 365 oder anderen Diensten überein.

## <a name="syntax"></a>Syntax
**User**()

## <a name="examples"></a>Beispiele
Der aktuelle PowerApps-Benutzer weist die folgenden Informationen auf:

* Vollständiger Name: **"John Doe"**
* E-Mail-Adresse: **"john.doe@contoso.com"**
* Bild: ![](media/function-user/john-doe-picture.png) 

|       Formel       |                                                                    Beschreibung                                                                    |                                                 Ergebnis                                                  |
|---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
|     **User()**      |                                             Datensatz mit allen Informationen für den aktuellen PowerApps-Benutzer.                                             |    { FullName:&nbsp;"John Doe", Email:&nbsp;"john.doe@contoso.com", Image:&nbsp;"blob:1234...5678" }    |
|  **User().Email**   |                                                 Die E-Mail-Adresse des aktuellen PowerApps-Benutzers.                                                  |                                         "john.doe@contoso.com"                                          |
| **User().FullName** |                                                   Der vollständige Name des aktuellen PowerApps-Benutzers.                                                    |                                               "John Doe"                                                |
|  **User().Image**   | Die Bild-URL für den aktuellen PowerApps-Benutzer.  Legen Sie die Eigenschaft **Image** des **Image**-Steuerelements auf diesen Wert fest, um das Bild in der App anzuzeigen. | "blob:1234...5678"<br><br>Für **ImageControl.Image**:<br>![](media/function-user/john-doe-picture.png) |

