---
title: Hinzufügen eines Power BI Berichts oder Dashboards zu einer Webseite in einem Portal | MicrosoftDocs
description: Anweisungen zum Hinzufügen eines Power BI Berichts oder Dashboards zu einer Webseite im Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 3735a0ef1a26fdd19b7bfb7f6db717cf9bd07861
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976160"
---
# <a name="add-a-power-bi-report-or-dashboard-to-a-web-page-in-portal"></a>Hinzufügen eines Power BI-Berichts oder -Dashboards zu einer Webseite im Portal

Mithilfe des Liquid-Tags von [powerbi](../liquid/portals-entity-tags.md#powerbi) können Sie einer Webseite im Portal einen Power BI Bericht oder ein Dashboard hinzufügen. Sie können das-Tag im Feld **Kopieren** auf einer Webseite oder im **Quellfeld** einer Webvorlage hinzufügen. Wenn Sie einen Power BI Bericht oder ein Dashboard hinzufügen, der im neuen Arbeitsbereich in Power BI erstellt wurde, müssen Sie den Authentifizierungstyp im powerbi Liquid-Tag als powerbiembedded angeben.

Beispiel: 

```
{% powerbi path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

> [!NOTE]
> Wenn Sie Aad als Authentifizierungstyp im powerbi Liquid-Tag angegeben haben, müssen Sie es für die erforderlichen Benutzer freigeben, bevor Sie den Bericht oder das Dashboard für sichere Power BI einer Webseite im Portal hinzufügen. Weitere Informationen finden Sie unter [Power BI Arbeitsbereich freigeben](https://docs.microsoft.com/power-bi/service-how-to-collaborate-distribute-dashboards-reports#collaborate-with-coworkers-in-an-app-workspace) und [Power BI Dashboard und Bericht freigeben](https://docs.microsoft.com/power-bi/service-share-dashboards).

## <a name="get-the-path-of-a-dashboard-or-report"></a>Den Pfad eines Dashboards oder Berichts erhalten

1.  Melden Sie sich bei [Power BI](https://powerbi.microsoft.com/)an.

2.  Öffnen Sie das Dashboard oder den Bericht, das Sie in Ihr Portal einbetten möchten.

3.  Kopieren Sie die URL aus der Adressleiste.

    > [!div class=mx-imgBorder]
    > Der ![Pfad eines Power BI Dashboards]erhält(../media/powerbi-dashboard-url.png "den Pfad eines Power BI Dashboards") .

## <a name="get-the-id-of-a-dashboard-tile"></a>ID einer dashboardkachel erhalten

1.  Melden Sie sich bei [Power BI](https://powerbi.microsoft.com/)an.

2.  Öffnen Sie das Dashboard, über das Sie eine Kachel in Ihr Portal einbetten möchten.

3.  Zeigen Sie auf die Kachel, wählen Sie **Weitere Optionen**aus, und klicken Sie dann **auf im Fokus Modus öffnen**.

    > [!div class=mx-imgBorder]
    > ![Öffnen Power BI dashboardkachel im Fokus Modus](../media/powerbi-dashboard-tile-focus.png "Power BI dashboardkachel im Fokus Modus öffnen")

4.  Kopieren Sie die Kachel-ID aus der URL in der Adressleiste. Die Kachel-ID ist der Wert nach/Tiles/.

    > [!div class=mx-imgBorder]
    > ![Power BI dashboardkachel-ID](../media/powerbi-dashboard-tile-id.png "Power BI dashboardkachel-ID")


### <a name="see-also"></a>Siehe auch


[powerbi Liquid-Tag](../liquid/portals-entity-tags.md#powerbi)<br> 
[Einrichten Power BI Integration](set-up-power-bi-integration.md)
