---
title: Funktion „User“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax für die Benutzerfunktion in Power apps
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
ms.openlocfilehash: 75b7b4e1f4c66745bdbddebb30c0e4ca45dfeb2b
ms.sourcegitcommit: 56c8c7cc64695ccb00e0d021c9f98cf70b69b4a2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78845351"
---
# <a name="user-function-in-power-apps"></a>Benutzerfunktion in Power apps
Gibt Informationen über den aktuellen Benutzer zurück.

## <a name="description"></a>Beschreibung
Die Funktion **User** gibt einen [Datensatz](../working-with-tables.md#records) mit Informationen über den aktuellen Benutzer zurück:

| Eigenschaft | Beschreibung |
| --- | --- |
| **User().Email** |E-Mail-Adresse des aktuellen Benutzers. |
| **User().FullName** |Vollständiger Name des aktuellen Benutzers, einschließlich Vor-und Nachnamen. |
| **User().Image** |Bild des aktuellen Benutzers. Dies ist eine Bild-URL der Form "blob:*Bezeichner*". Legen Sie die Eigenschaft **[Image](../controls/properties-visual.md)** des **[Image](../controls/control-image.md)** -Steuerelements auf diesen Wert fest, um das Bild in der App anzuzeigen. |

> [!NOTE]
> Die zurückgegebenen Informationen sind für den aktuellen powerapps-Benutzer.  Sie entspricht den "Konto"-Informationen, die in den powerapps-Playern und in Studio angezeigt werden, die außerhalb der erstellten apps gefunden werden können.  Möglicherweise stimmen sie nicht mit den Informationen des aktuellen Benutzers in Office 365 oder anderen Diensten überein.

> [!NOTE]
> Wenn Sie Ihre Anwendung vor dem 2020 mit einer Benutzerfunktion veröffentlicht haben, werden Sie möglicherweise feststellen, dass Sie nicht mehr Fotos abruft. Die Probleme wurden in der Version vom Ende März 2020 behoben.  Wenn Sie die aktualisierte Implementierung nutzen möchten, öffnen Sie einfach Ihre Anwendung erneut, speichern Sie Sie, und veröffentlichen Sie Sie erneut.  

## <a name="syntax"></a>Syntax
**User**()

## <a name="examples"></a>Beispiele
Der aktuelle powerapps-Benutzer verfügt über die folgenden Informationen:

* Vollständiger Name: **"John Doe"**
* E-Mail-Adresse: **"john.doe@contoso.com"**
* Bild: ![](media/function-user/john-doe-picture.png) 

|       Formel       |                                                                    Beschreibung                                                                    |                                                 Ergebnis                                                  |
|---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
|     **User()**      |                                             Zeichnet alle Informationen für den aktuellen powerapps-Benutzer auf.                                             |    { FullName:&nbsp;"John Doe", Email:&nbsp;"john.doe@contoso.com", Image:&nbsp;"blob:1234...5678" }    |
|  **User().Email**   |                                                 Die e-Mail-Adresse des aktuellen powerapps-Benutzers.                                                  |                                         "john.doe@contoso.com"                                          |
| **User().FullName** |                                                   Der vollständige Name des aktuellen powerapps-Benutzers.                                                    |                                               "John Doe"                                                |
|  **User().Image**   | Die Bild-URL für den aktuellen powerapps-Benutzer.  Legen Sie die Eigenschaft **Image** des **Image**-Steuerelements auf diesen Wert fest, um das Bild in der App anzuzeigen. | "blob:1234...5678"<br><br>Für **ImageControl.Image**:<br>![](media/function-user/john-doe-picture.png) |

