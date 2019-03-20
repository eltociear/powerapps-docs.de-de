---
title: Integrieren von PowerApps, Microsoft Flow und Power BI mit SharePoint Online (Einführung) | Microsoft-Dokumentation
description: 'Diese Reihe von Tutorials wird untersucht, wie erstellen Sie eine weitere grundlegende Canvas-app für Projektmanagement, die basierend auf der SharePoint-Listen und drei schlüsseltechnologien, die in SharePoint Online integriert wird: PowerApps, Microsoft Flow und Powerbi.'
author: NickWaggoner
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 12/19/2017
ms.author: niwaggon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 812a73163047914a8f0bcc651c831ee4022fcc28
ms.sourcegitcommit: 90245baddce9d92c3ce85b0537c1ac1cf26bf55a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2019
ms.locfileid: "57799063"
---
# <a name="integrate-powerapps-microsoft-flow-and-power-bi-with-sharepoint-online"></a>Integrieren von PowerApps, Microsoft Flow, und Power BI mit SharePoint Online
Sie verfügen über SharePoint Online und möchten Ihre Geschäftsprozesse besser automatisieren und optimieren? Sie haben mit PowerApps, Microsoft Flow oder Power BI gearbeitet, sind aber nicht sicher, wie Sie diese mit SharePoint Online verwenden können? Dann sind Sie hier richtig. Diese Reihe von Tutorials wird untersucht, wie erstellen Sie eine weitere grundlegende Canvas-app für Projektmanagement, die basierend auf der SharePoint-Listen und drei schlüsseltechnologien, die in SharePoint Online integriert wird: PowerApps, Microsoft Flow und Powerbi. Diese Technologien wirken zusammen und erleichtern das *Messen* Ihrer Geschäftsprozesse, das *Reagieren* auf die Ergebnisse und das *Automatisieren* Ihrer Workflows. Wenn Sie diese Reihe abgeschlossen haben, liegt Ihnen ein cooles Szenario wie die folgenden vor:

![Diagramm des abgeschlossenen-Szenarios](./media/sharepoint-scenario-intro/composite-with-background.png)

## <a name="business-scenario"></a>Geschäftsszenario
In dieser Reihe von Tutorials verfügt das Unternehmen Contoso über eine SharePoint Online-Website, auf welcher der Lebenszyklus von Projekten von der Anforderung über die Genehmigung und Entwicklung bis hin zur Endabnahme verwaltet wird. Ein *Projektanforderer*, beispielsweise ein Abteilungsleiter, fordert ein IT-Projekt an, indem er einer SharePoint-Liste einen Eintrag hinzufügt. Durch einen *Projektgenehmiger*, beispielsweise einen IT-Manager, wird das Projekt geprüft und anschließend genehmigt bzw. abgelehnt. Wenn das Projekt genehmigt wurde, wird es einem *Projektmanager* zugewiesen, und über die gleiche App wird einer zweiten Liste ein weiterer Eintrag hinzugefügt. Ein *Wirtschaftsanalytiker* prüft laufende und abgeschlossene Projekte anhand eines Power BI-Berichts, der in SharePoint eingebettet ist.  Mit Microsoft Flow werden Genehmigungs-E-Mails versendet, und es wird auf Power BI-Warnungen reagiert.

## <a name="getting-started-quickly"></a>Schnelleinstieg
Das in dieser Reihe von Tutorials vorgestellte Szenario scheint unkompliziert, wenn es einer umfassenden App für Projektmanagement und -analyse gegenübergestellt wird, dennoch dauert es jedoch eine gewisse Zeit, alle Aufgaben auszuführen. Wenn Sie lediglich eine rasche Einführung zum Verwenden von PowerApps, Microsoft Flow und Power BI mit SharePoint wünschen, sehen Sie die folgenden Artikel ein:

* **PowerApps**: [Generieren eine app aus SharePoint mit PowerApps](app-from-sharepoint.md#generate-an-app-from-within-sharepoint-online) und [Generieren einer app zum Verwalten von Daten in einer SharePoint-Liste](app-from-sharepoint.md)
* **Microsoft Flow**: [Warten Sie auf Genehmigung in Microsoft Flow](https://docs.microsoft.com/flow/wait-for-approvals)
* **Power BI**: [Betten Sie mit Berichts-Webpart in SharePoint Online ein](https://docs.microsoft.com/power-bi/service-embed-report-spo)

Wenn Sie diese Artikel durchgelesen haben, kehren Sie hoffentlich zu diesem kompletten Szenario zurück.

Selbst innerhalb dieses Szenarios können Sie sich auf die Aufgaben konzentrieren, die für Sie von größter Relevanz sind und die Aufgaben ausführen, wenn Sie ausreichend Zeit dafür haben. Nachdem Sie SharePoint-Listen in Aufgabe 1 eingerichtet haben, können Sie die Aufgaben 2 bis 5 in beliebiger Reihenfolge durcharbeiten. Die Aufgaben 6 bis 8 sind der Reihe nach auszuführen. Schließlich haben wir zwei vollständige Apps und einen Power BI Desktop-Bericht als Teil des [Downloadpakets](https://aka.ms/o4ia0f) für dieses Szenario eingebunden. Sie können diese eingehend untersuchen und sich einen exemplarischen Überblick verschaffen, selbst wenn Sie nicht alle Schritte in den einzelnen Aufgaben durcharbeiten.

## <a name="prerequisites"></a>Voraussetzungen
Zum Durcharbeiten dieses Szenarios benötigen Sie die folgenden Abonnements und Desktoptools. Das Office 365 Business Premium-Abonnement schließt PowerApps und Microsoft Flow ein.

| **Abonnement oder Tool** | **Link** |
| --- | --- |
| Office 365 Business Premium-Abonnement |[Abonnement für die Testversion](https://signup.microsoft.com/Signup?OfferId=467eab54-127b-42d3-b046-3844b860bebf&dl=O365_BUSINESS_PREMIUM&ali=1) |
| Power BI Pro-Abonnement |[Abonnement für die Testversion](https://powerbi.microsoft.com/get-started/) (klicken Sie auf **KOSTENLOS TESTEN**) |
| Power BI Desktop |[Kostenloser Download](https://powerbi.microsoft.com/get-started/) (klicken Sie auf **KOSTENLOS HERUNTERLADEN**) |

Im Idealfall sind Sie im Wesentlichen mit den einzelnen Technologien vertraut. Sie können das Szenario jedoch auch durcharbeiten, wenn Sie mit einer dieser Technologien keine Erfahrung haben. Die folgenden Ressourcen erleichtern Ihnen den schnellen Einstieg:

* [Erste Schritte mit SharePoint](https://support.office.com/article/Get-started-with-SharePoint-909ec2f0-05c8-4e92-8ad3-3f8b0b6cf261)
* [Geführtes Lernen zu PowerApps](../../guided-learning/index.md)
* [Geführtes Lernen zu Microsoft Flow](https://docs.microsoft.com/flow/guided-learning/)
* [Geführtes Lernen zu Power BI](https://docs.microsoft.com/power-bi/guided-learning/)

## <a name="next-steps"></a>Nächste Schritte
Der nächste Schritt in dieser Reihe von Tutorials besteht im [Einrichten der SharePoint Online-Listen](sharepoint-scenario-setup.md), die in der gesamten Reihe verwendet werden.

