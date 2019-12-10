---
title: Integrieren von powerapps, Power automatisiert und Power BI mit SharePoint Online (Einführung) | Microsoft-Dokumentation
description: 'In dieser Reihe von Tutorials erfahren Sie, wie Sie eine einfache Canvas-App für das Projektmanagement auf der Grundlage von SharePoint-Listen und drei Schlüsseltechnologien erstellen, die in SharePoint Online integriert sind: powerapps, Power automatisiert und Power BI.'
author: NickWaggoner
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/05/2019
ms.author: niwaggon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 45f33285b288dc273caeff1e85591210cc3deb8c
ms.sourcegitcommit: d194d2fa009ca7bfcbe95e5f31473832a130e0a6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "74959539"
---
# <a name="integrate-power-apps-power-automate-and-power-bi-with-sharepoint-online"></a>Integrieren von powerapps, Energie automatisierter und Power BI mit SharePoint Online
Sie verfügen über SharePoint Online und möchten Ihre Geschäftsprozesse besser automatisieren und optimieren? Haben Sie mit Power apps, Energie Automatisierung oder Power BI gearbeitet, sind aber nicht sicher, wie Sie diese mit SharePoint Online verwenden können? Dann sind Sie hier richtig. In dieser Reihe von Tutorials erfahren Sie, wie Sie eine einfache Canvas-App für das Projektmanagement auf der Grundlage von SharePoint-Listen und drei Schlüsseltechnologien erstellen, die in SharePoint Online integriert sind: powerapps, Power automatisiert und Power BI. Diese Technologien wirken zusammen und erleichtern das *Messen* Ihrer Geschäftsprozesse, das *Reagieren* auf die Ergebnisse und das *Automatisieren* Ihrer Workflows. Wenn Sie diese Reihe abgeschlossen haben, liegt Ihnen ein cooles Szenario wie die folgenden vor:

![Diagramm des abgeschlossenen-Szenarios](./media/sharepoint-scenario-intro/composite-with-background.png)

## <a name="business-scenario"></a>Geschäftsszenario
In dieser Reihe von Tutorials verfügt das Unternehmen Contoso über eine SharePoint Online-Website, auf welcher der Lebenszyklus von Projekten von der Anforderung über die Genehmigung und Entwicklung bis hin zur Endabnahme verwaltet wird. Ein *Projektanforderer*, beispielsweise ein Abteilungsleiter, fordert ein IT-Projekt an, indem er einer SharePoint-Liste einen Eintrag hinzufügt. Durch einen *Projektgenehmiger*, beispielsweise einen IT-Manager, wird das Projekt geprüft und anschließend genehmigt bzw. abgelehnt. Wenn das Projekt genehmigt wurde, wird es einem *Projektmanager* zugewiesen, und über die gleiche App wird einer zweiten Liste ein weiterer Eintrag hinzugefügt. Ein *Wirtschaftsanalytiker* prüft laufende und abgeschlossene Projekte anhand eines Power BI-Berichts, der in SharePoint eingebettet ist.  Mit der Energie Automatisierung werden Genehmigungs-e-Mails gesendet und auf Power BI Warnungen reagiert.

## <a name="getting-started-quickly"></a>Schnelleinstieg
Das in dieser Reihe von Tutorials vorgestellte Szenario scheint unkompliziert, wenn es einer umfassenden App für Projektmanagement und -analyse gegenübergestellt wird, dennoch dauert es jedoch eine gewisse Zeit, alle Aufgaben auszuführen. Wenn Sie nur eine kurze Einführung in die Verwendung von powerapps, Power automatisiert und Power BI mit SharePoint wünschen, lesen Sie die folgenden Artikel:

* **Powerapps**: [Erstellen einer App aus SharePoint mithilfe von powerapps](app-from-sharepoint.md#create-an-app-from-within-sharepoint-online) und [Erstellen einer App zum Verwalten von Daten in einer SharePoint-Liste](app-from-sharepoint.md)
* **Energie Automatisierung**: [warten auf die Genehmigung in der Energie Automatisierung](https://docs.microsoft.com/flow/wait-for-approvals)
* **Power BI:** [Einbetten mit einem Berichts-Webpart in SharePoint Online](https://docs.microsoft.com/power-bi/service-embed-report-spo)

Wenn Sie diese Artikel durchgelesen haben, kehren Sie hoffentlich zu diesem kompletten Szenario zurück.

Selbst innerhalb dieses Szenarios können Sie sich auf die Aufgaben konzentrieren, die für Sie von größter Relevanz sind und die Aufgaben ausführen, wenn Sie ausreichend Zeit dafür haben. Nachdem Sie SharePoint-Listen in Aufgabe 1 eingerichtet haben, können Sie die Aufgaben 2 bis 5 in beliebiger Reihenfolge durcharbeiten. Die Aufgaben 6 bis 8 sind der Reihe nach auszuführen. Schließlich haben wir zwei vollständige Apps und einen Power BI Desktop-Bericht als Teil des [Downloadpakets](https://aka.ms/o4ia0f) für dieses Szenario eingebunden. Sie können diese eingehend untersuchen und sich einen exemplarischen Überblick verschaffen, selbst wenn Sie nicht alle Schritte in den einzelnen Aufgaben durcharbeiten.

## <a name="prerequisites"></a>Voraussetzungen
Zum Durcharbeiten dieses Szenarios benötigen Sie die folgenden Abonnements und Desktoptools. Das Office 365 Business Premium-Abonnement umfasst powerapps und Power-Automatisierung.

| **Abonnement oder Tool** | **Link** |
| --- | --- |
| Office 365 Business Premium-Abonnement |[Abonnement für die Testversion](https://signup.microsoft.com/Signup?OfferId=467eab54-127b-42d3-b046-3844b860bebf&dl=O365_BUSINESS_PREMIUM&ali=1) |
| Power BI Pro-Abonnement |[Abonnement für die Testversion](https://powerbi.microsoft.com/get-started/) (klicken Sie auf **KOSTENLOS TESTEN**) |
| Power BI Desktop |[Kostenloser Download](https://powerbi.microsoft.com/get-started/) (klicken Sie auf **KOSTENLOS HERUNTERLADEN**) |

Im Idealfall sind Sie im Wesentlichen mit den einzelnen Technologien vertraut. Sie können das Szenario jedoch auch durcharbeiten, wenn Sie mit einer dieser Technologien keine Erfahrung haben. Die folgenden Ressourcen erleichtern Ihnen den schnellen Einstieg:

* [Erste Schritte mit SharePoint](https://support.office.com/article/Get-started-with-SharePoint-909ec2f0-05c8-4e92-8ad3-3f8b0b6cf261)
* [Geführtes lernen zu Power apps](../../guided-learning/index.md)
* [Geführtes lernen für die Energie Automatisierung](https://docs.microsoft.com/flow/guided-learning/)
* [Geführtes Lernen zu Power BI](https://docs.microsoft.com/power-bi/guided-learning/)

## <a name="next-steps"></a>Nächste Schritte
Der nächste Schritt in dieser Reihe von Tutorials besteht im [Einrichten der SharePoint Online-Listen](sharepoint-scenario-setup.md), die in der gesamten Reihe verwendet werden.

