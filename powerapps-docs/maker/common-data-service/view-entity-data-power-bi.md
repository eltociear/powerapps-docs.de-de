---
title: Entitätsdaten in Power BI Desktop (Vorschau) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie in Power BI Desktop auf Entitätsdaten zugreifen und diese anzeigen können
ms.custom: ''
ms.date: 05/01/2020
ms.reviewer: matp
ms.service: powerapps
author: Mattp123
ms.assetid: ''
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 446381f491fac0cb5d60c3945f5404983f1ed364
ms.sourcegitcommit: 0ede8e3bc795e151aa94ffcbce15cff7a949c57a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "3335404"
---
# <a name="view-entity-data-in-power-bi-desktop-preview"></a>Entitätsdaten in Power BI Desktop (Vorschau) anzeigen

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Sie können Power BI Desktop verwenden, um Entitäten in Common Data Service anzuzeigen. Die Entitätsdatensatzdaten, auf die Sie von Ihrer Umgebung aus zugreifen können, sind schreibgeschützt. Der Datenzugriff erfolgt über das Common Data Service-Sicherheitsmodell, das auch für den Zugriff auf Entitätsdatensatzdaten mithilfe einer Power Apps-App verwendet wird.

> [!IMPORTANT]
> - Dies ist eine Vorschaufunktion und nicht in allen Regionen verfügbar.
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)]

1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com/) an und wählen Sie dann die passende Umgebung aus der oberen rechten Ecke aus.

2.  Erweitern Sie im linken Navigationsbereich **Daten**, wählen Sie **Entitäten**und dann **In Power BI analysieren** in der Befehlsleiste.

    Die pbids-Datei für Ihre Umgebung wird in den Standarddownload-Ordner Ihres Browsers heruntergeladen.
    
    > [!NOTE]
    > Wenn Sie die Option **In Power BI analysieren** nicht in Ihrer Power Apps-Umgebung haben, haben Sie noch keinen Zugriff auf die SQL-Verbindungsfunktion.

3.  Öffnen Sie die .pbids-Datei, um in Power BI Desktop darauf zuzugreifen. Sie verfügen nicht über Power BI Desktop? [Jetzt installieren](https://powerbi.microsoft.com/downloads/).

4.  Die pbids-Datei wird in Power BI Desktop geladen. Wählen Sie im Dialogfeld **SQL Server-Datenbank** die Option **Microsoft-Konto** und **Anmelden** aus, und geben Sie dann im angezeigten Browserfenster Ihre Anmeldeinformationen ein.

    > [!div class="mx-imgBorder"] 
    > ![](media/power-bi-environment-signin.png)

5.  Wählen Sie im Dialogfeld **SQL Server-Datenbank** in Power BI Desktop **Verbinden** aus.

    Die Umgebung erscheint in der Power BI Desktop-Fenster **Navigator**. Erweitern Sie es, um die zur Analyse verfügbaren Entitätstabellen anzuzeigen. Wählen Sie eine Entität aus, um ihre Daten anzuzeigen.

    > [!div class="mx-imgBorder"] 
    > ![](media/entity-record-data-displayed.png)

> [!NOTE]
> SQL-Optionen wie T-SQL-Abfragen werden nicht unterstützt.

Weitere Informationen zu Power BI Desktop finden Sie unter [Erste Schritte mit Power BI Desktop](/power-bi/desktop-getting-started).

### <a name="see-also"></a>Siehe auch
[SQL zur Abfrage von Daten verwenden](../../developer/common-data-service/cds-sql-query.md)
