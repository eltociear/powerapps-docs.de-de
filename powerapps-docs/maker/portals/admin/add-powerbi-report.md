---
title: Hinzufügen eines Power BI-Berichts oder -Dashboards zu einer Webseite im Portal | Microsoft-Dokumentation
description: Anleitung zum Hinzufügen eines Power BI-Berichts oder -Dashboards zu einer Webseite im Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 07/18/2019
ms.author: shjais
ms.reviewer: null
---


# <a name="add-a-power-bi-report-or-dashboard-to-a-web-page-in-portal"></a>Hinzufügen eines Power BI-Berichts oder -Dashboards zu einer Webseite im Portal

[!include[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

Sie können einen Power BI-Bericht oder -Dashboard zu einer Webseite im Portal hinzufügen, indem Sie den [powerbi](../liquid/portals-entity-tags.md#powerbi)-Liquid-Tag verwenden. Sie können den Tag im Feld **Kopieren** auf einer Webseite oder im Feld **Quelle** auf einem Webvorlagen hinzufügen. Wenn Sie einen Power BI-Bericht oder -Dashboard hinzufügen, das im neuen Arbeitsbereich in Power BI erstellt wird, müssen Sie den Authentifizierungstyp als powerbiembedded im powerbi-Liquid-Tag angeben.

Beispiel: 

```
{% powerbi path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

> [!NOTE]
> Wenn Sie AAD als den Authentifizierungstyp im powerbi-Liquid-Tag angegeben haben, müssen Sie ihn für die erforderlichen Benutzer freigeben, bevor Sie den sicheren Power BI-Bericht oder -Dashboard einer Webseite im Portal hinzufügen. Weitere Informationen: [Freigeben von Power BI-Arbeitsbereich](https://docs.microsoft.com/en-us/power-bi/service-how-to-collaborate-distribute-dashboards-reports#collaborate-with-coworkers-in-an-app-workspace) und [Freigeben von Power BI-Dashboard und Bericht](https://docs.microsoft.com/en-us/power-bi/service-share-dashboards).

## <a name="get-the-path-of-a-dashboard-or-report"></a>Den Pfad eines Dashboards oder Berichts abrufen

1.  Melden Sie sich bei [Power BI](https://powerbi.microsoft.com/) an.

2.  Öffnen Sie das Dashboard oder den Bericht, die Sie in das Portal einbetten möchten.

3.  Kopieren Sie die URL in der Adressleiste.

    > [!div class=mx-imgBorder]
    > ![Den Pfad eines Power BI-Dashboards abrufen](../media/powerbi-dashboard-url.png "Den Pfad eines Power BI-Dashboards abrufen")

## <a name="get-the-id-of-a-dashboard-tile"></a>Abrufen der ID einer Dashboard-Kachel

1.  Melden Sie sich bei [Power BI](https://powerbi.microsoft.com/) an.

2.  Öffnen Sie das Dashboard, von dem aus Sie eine Kachel in Ihr Portal einbetten möchten.

3.  Zeigen Sie auf die Kachel, wählen Sie **Weitere Möglichkeiten**, und wählen Sie dann **Im Fokusmodus öffnen** aus.

    > [!div class=mx-imgBorder]
    > ![Öffnen einer Power BI-Dashboardkachel im Fokusmodus](../media/powerbi-dashboard-tile-focus.png "Öffnen einer Power BI-Dashboardkachel im Fokusmodus")

4.  Kopieren Sie die Kachel ID von der URL in der Adressleiste. Die Kachel-ID ist der Wert nach /tiles/.

    > [!div class=mx-imgBorder]
    > ![Power BI-Dashboardkachel-ID](../media/powerbi-dashboard-tile-id.png "Power BI-Dashboardkachel-ID")


### <a name="see-also"></a>Siehe auch

[Liquid-Tag powerbi](../liquid/portals-entity-tags.md#powerbi)<br> 
[Einrichten der Power BI-Integration](set-up-power-bi-integration.md)
