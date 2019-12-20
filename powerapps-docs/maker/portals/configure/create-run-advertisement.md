---
title: Erstellen und Ausführen von Werbung in einem Portal | MicrosoftDocs
description: Anleitungen zum Erstellen von bild- oder textbasierten Anzeigen und deren Ausführen in mehreren Platzierungen in der Website.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/22/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 34305495dd284f3af99e1d77c1616839aede1cc7
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "2875768"
---
# <a name="create-and-run-advertisements-on-a-portal"></a>Erstellen und Ausführen von Werbung auf einem Portal

Erstellen Sie bild- oder textbasierte Anzeigen und führen Sie diese in mehreren Platzierungen in der Website aus. Randomisieren Sie Anzeigen oder wählen Sie spezielle Anzeigen für bestimmte Platzierungen aus. Sie können Veröffentlichung- und Ablaufdaten für zeitempfindlichen, geplante Inhalte auswählen. Anzeigen können zu jedem beliebigem Ziel verlinkt werden und im aktiven oder einem neuen Fenster geöffnet werden. Anzeigen werden im Portal über zwei Entitäten angezeigt: Die Anzeigenplatzierungsentität und die zugehörigen Anzeigenentität. Anzeigen können in verschiedenen Varianten angezeigt werden: mit vordefinierten Liquid-Vorlagen aus der -Portal-Anwendung über Liquid-Vorlagen/Beispielsweisewebsitevorlagen oder innerhalb der gewünschten MVC-Aktionen oder ASPX-Seite.

## <a name="create-a-new-advertisement"></a>Erstellen einer neuen Anzeige

Anzeigen stellen bestimmte Werbung oder Bilder dar, die für eine bestimmte Zeit auf dem Portal zu sehen sind. Die Anzeigenentität wird an dem durch die Anzeigenplatzierung angegeben Ort angezeigt. Die Anzeige muss einer Anzeigenplatzierung zugeordnet werden, um auf dem Portal angezeigt zu werden. In dieser Demonstration werden die OOB-Beispiel-Anzeigeplatzierungen Platzhalter und Sidebar Unten im Unternehmensportal angezeigt, um die grundlegende Funktionalität zu zeigen und diese kennenzulernen. Alle Starterwebsites können anstelle des Unternehmens-Portals verwendet werden. Beachten Sie jedoch die für diese Demonstration verwendeten Liquid-Vorlagen den Namen der Randleisten-Schaltfläche-Anzeigenplatzierung aufrufen.

1. Öffnen Sie die [Portalverwaltungs-App](configure-portal.md).

2. Öffnen Sie **Portale** > **Anzeigen**

3. Öffnen Sie die **Platzhalter**-Anzeige, die der **Unternehmens-Portal**-Website zugeordnet ist (kann mit der Starterwebsite ihrer Wahl durchgeführt werden, indem Sie auf **+Neu** klicken und eine identische Anzeige unterhalb der Website erstellen). 

4. Klicken Sie auf das Symbol **Speichern** in der rechten unteren Ecke (oder **Speichern und schließen** in der oberen linken Ecke, wenn Sie eine neue Anzeige erstellt haben)

Innerhalb des Anzeigen-Formulars, müssen Sie **Name** angeben, um die Anzeige zu beschreiben, die **Website** auf der die Anzeige angezeigt wird und **Veröffentlichungstatus**. Optional können Sie eine Webvorlage und eine Version/ein Ablaufdatum angegeben. Sie müssen bestimmte Daten angeben, damit die Anzeige angezeigt wird. Verwenden Sie die Anzeigenentitätsattributtabelle weiter unten in diesem Leitfaden, um die Angaben zur Anzeige zu erstellen.


## <a name="create-a-new-advertisement-placements"></a>Erstellen einer neuen Anzeigenplatzierung

1. Öffnen Sie die [Portalverwaltungs-App](configure-portal.md).

2. Öffnen Sie **Portale** > **Anzeigenplatzierungen**.

3. Klicken Sie auf das Webvorlagen-Feld, um eine Webvorlage auszuwählen. Zu Demonstrationszwecken wurde die Webvorlage Zufällige Anzeige ausgewählt.

4. Auf der rechten Ecke des Anzeigenrasters klicken Sie auf **+**, um die im vorherigen Schritt erstellte Anzeige auszuwählen.

5. Klicken Sie in der unteren rechten Ecke auf das Symbol **Speichern**

Wenn Sie eine neue Anzeigenplatzierung erstellen, müssen Sie einen **Namen** angeben, um die Anzeigenplatzierung und die **Website** zu beschreiben, auf der nach Bedarf die Anzeigenplatzierung angezeigt wird. Die Webvorlagen, die die Verwendung Anzeigen als OOB-Funktion aktivieren werden in der Suche für des Webvorlagenfelds im Formular angezeigt. Diese Vorlagen werden als Basis für benutzerdefinierte Vorlagen verwendet.

> [!div class=mx-imgBorder]
> ![Suchdatensatz ansehen](../media/see-lookup-record.png "Suchdatensatz ansehen")  

> [!div class=mx-imgBorder]
> ![Einstellungen unten in der Seitenleiste](../media/set-sidebar-bottom.png "Einstellungen unten in der Seitenleiste")  

> [!div class=mx-imgBorder]
> ![Anzeigenunternehmensportal](../media/ad-company-portal.png "Anzeigenunternehmensportal")  

> [!NOTE] 
> Die oben erstellte Anzeige wird nicht auf der Startseite des Starterportals angezeigt.

## <a name="using-liquid-templates-to-place-advertisements"></a>Verwenden von Liquid-Vorlagen, um Werbung zu platzieren

Inhalts-Manager können mit Liquid jedem bearbeitbaren Bereich eine Anzeige hinzufügen, wie in [Hinzufügen von dynamischen Inhalten und Erstellen benutzerdefinierter Vorlagen](../liquid/liquid-overview.md) und besonders in [Anzeigen](../liquid/liquid-objects.md#ads) beschrieben.

Diese Vorlage rendert eine Anzeige nach Namen oder eine zufällige Anzeige aus einer Anzeigenplatzierung. Der unten angegebene Code rendert aktuell nicht mehrere Anzeigen in einer Platzierung (d. h. rotierende Anzeigen). Zum Anzeigen mehrerer Anzeigen in der Platzierung müssten Sie eine Liquid Ads-API erstellen. Weitere Informationen über integrierte Webvorlagen finden Sie unter [Quellinhalt mithilfe von Webvorlagen speichern](../liquid/store-content-web-templates.md)

```
{% include 'ad' ad_name:'Name' %}
{% include 'ad' ad_placement_name:'Placement Name' %}
1. {% include 'Random Ad' placement:ads.placements[Sidebar Bottom] %}
```
ODER 

```
1. {% include 'Ad Template' ad:ads{Retail Ad - Go Greene] %}
```


## <a name="attributes"></a>Attribute

Die Anzeigenentität hat die folgenden Attribute:


|        Name        |                                                                                                                                                                                                                                             Beschreibung                                                                                                                                                                                                                                              |
|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|        Name        |                                                                                                                                                                                                                                    Ein beschreibender Name für die Anzeige                                                                                                                                                                                                                                     |
|      Website       |                                                                                                                                                                                                                                  Die zugeordnete Website. Erforderlich.                                                                                                                                                                                                                                   |
|    Webvorlage    |                                                                                                                                                Die zugeordnete [Webvorlage](../liquid/store-content-web-templates.md), die standardmäßig verwendet wird, um die Anzeige zu rendern. Dieses Feld ist optional; wenn es leer ist, wird die Anzeige mit einer Standardvorlage gerendert.                                                                                                                                                |
|    Veröffentlichungsdatum    |                                                                                      Steuert das Datum und die Uhrzeit, ab der die Umfrage auf dem Portal sichtbar ist. Wenn die Anzeige-Platzierung in mehreren Anzeigen rotiert, wird eine unveröffentlichte Anzeige nicht angezeigt. Wenn keine freigegebenen Anzeige einer Anzeige-Platzierung zugeordnet sind, wird nichts angezeigt. Dies ist nützlich zur Steuerung der Veröffentlichungzeit von Inhalten.                                                                                      |
|  Ablaufdatum   |                                                                                                                                                                                                             Steuert das Datum/die Uhrzeit, vor der die Anzeige auf dem Portal sichtbar ist.                                                                                                                                                                                                             |
|  Veröffentlichungsstatus  |                                                                                                                                                                                                                                    Der aktuelle Veröffentlichungsstatus.                                                                                                                                                                                                                                     |
|    Umleitungs-URL    |                                                                                                                                                                                Wenn die Anzeige geklickt wird, wird der Benutzer zu dieser URL weitergeleitet. **Dieses Feld ist optional.** Wenn kein Wert festgelegt ist, ist die Anzeige nicht klickbar.                                                                                                                                                                                 |
| In neuem Fenster öffnen |                                                                                                                                                                                                             Boolescher Wert Wenn Sie den Wert "true" festlegen, wir ein neues Browserfenster geöffnet, wenn geklickt wird.                                                                                                                                                                                                             |
|       Position        |  Eine einzelne Textzeile für die Anzeige, die im Verwaltungsportal angezeigt werden kann. Ob sie angezeigt wird hängt von einer Eigenschaft im AdPlacement-Steuerelement ab. Dies ist vor Allem für textbasierte Anzeigen oder einfache einzeilige Links nützlich, die Sie auf dem Portal mithilfe von Anzeigen-Platzierungen platzieren möchten. Wenn der Titel angezeigt wird, wird er standardmäßig als Link gerendert, der zur Umleitungs-URL verweist. Dieses Verhalten kann über eine benutzerdefinierte [Webvorlage](../liquid/store-content-web-templates.md) geändert werden.   |
|        Kopieren        |                                                                      Ein mehrzeiliger Text oder andere Webinhalte, die in der Anzeigenplatzierung angezeigt werden. Dies ermöglicht die Platzierung wie bei Code-Stücken. Aber es empfiehlt sich, diese Verwendung zu vermeiden und sie als Element für Inhalte zu verwenden. Am besten werden sie zum Rotieren von Bildern oder Textinhalten verwendet.                                                                      |
|     Bild-URL      | Die URL des Bilds, das in der Anzeige angezeigt wird. Optional; Verwenden Sie das Feld, wenn Sie die Anzeige als statische Ressource eine Webdatei rendern möchten. Das Bild ist klickbar und verlinkt auf die Umleitungs-URL. Wenn eine Anzeige eine Notiz mit einer Bilddateianlage hat, wird die Anzeige als Bild gerendert. Dies ist vielleicht die bequemste Möglichkeit, um Bilder für Anzeigen einzurichten und das Bild direkt mit der Anzeige zu verbinden. In diesem Fall ist das URL-Bild-Feld nicht erforderlich. |
|    Bildbreite     |                                                                                                                                                                                    Breite des Bilds. Dieses Feld ist nicht erforderlich, wird jedoch empfohlen, um sicherzustellen, dass die gerenderte Anzeige gültiges und zugreifbares HTML ist                                                                                                                                                                                     |
|    Bildhöhe    |                                                                                                                                                                                    Hohe des Bilds. Dieses Feld ist nicht erforderlich, wird jedoch empfohlen, um sicherzustellen, dass die gerenderte Anzeige gültiges und zugreifbares HTML ist                                                                                                                                                                                    |
|   Alternativer Bildtext   |                                                                                                                                                                                  Alt-Text für das Bild. Dieses Feld ist nicht erforderlich, wird jedoch empfohlen, um sicherzustellen, dass die gerenderte Anzeige gültiges und zugreifbares HTML ist.                                                                                                                                                                                  |

### <a name="see-also"></a>Siehe auch

[Ein Portal konfigurieren](configure-portal.md)  
[Über Entitätslisten](entity-lists.md)  
[Erstellen und Ausführen von Werbung in einem Portal](create-run-advertisement.md)  
[Einholung von Feedback mit Umfragen im Portal](gather-feedback-poll.md)  
[Webseite oder Blogbeitrag im Portal bewerten bzw. darüber abstimmen](rate-webpage.md)  
[Umleiten zu einer neuen URL auf einem Portal](add-redirect-url.md)  

