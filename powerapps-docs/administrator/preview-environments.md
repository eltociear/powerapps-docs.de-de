---
title: Vorschauumgebungen | Microsoft-Dokumentation
description: Erhalten Sie mit dem PowerApps-Vorschauprogramm vorab Zugriff auf Funktionen.
author: manasmams
manager: kvivek
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 08/29/2018
ms.author: manasma
search.audienceType:
- admin
search.app:
- D365CE
- PowerApps
- Powerplatform
ms.openlocfilehash: e2c4c735827941b32ce5e019eb8d71e4328e4a7a
ms.sourcegitcommit: b8eee36e680036accb0e7d9fc7a434906af1c4d2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43297945"
---
# <a name="powerapps-preview-program"></a>PowerApps-Vorschauprogramm
PowerApps aktualisiert die Plattform und die zugehörigen Funktionen alle paar Tage oder Wochen. Das PowerApps-Vorschauprogramm ist eine Möglichkeit, bereits vor der Verfügbarkeit in anderen Regionen (in denen die Produktions-Apps für Kunden bereitgestellt werden) Zugriff auf diese Funktionen und Updates zu erhalten. 

Das PowerApps-Vorschauprogramm bietet Ihnen folgende Vorteile:
- **Informieren Sie sich über neue Funktionen, und probieren Sie sie aus**: Viele Funktionen werden zuerst für einige Tage in einer Vorschauversion eingeführt, um Feedback von Kunden zu erhalten. Durch die Teilnahme am Vorschauprogramm können Sie sich schneller über neue Funktionen informieren und Feedback senden. Sie können auch schnell von neuen Funktionen profitieren, sobald diese in Regionen verfügbar werden, in denen Produktions-Apps erstellt werden.
- **Sorgen Sie für Geschäftskontinuität, indem Sie sicherstellen**, dass aktuelle Apps mit den neuen Updates (vNext) von PowerApps weiterhin funktionieren.

## <a name="what-in-powerapps-is-available-for-preview"></a>Welche Funktionen von PowerApps sind für die Vorschau verfügbar?
Um auf die Vorschaufunktionen in PowerApps zuzugreifen, müssen Sie sich in einer Vorschauumgebung befinden. Weitere Informationen zur Vorschauumgebung finden Sie im nächsten Abschnitt.
Derzeit stellen wir die Vorschau für die folgenden Szenarien in PowerApps bereit:
1. **Erstellen von Apps**: Mit der nächsten Version von PowerApps können Sie canvasbasierte Apps erstellen. Diese Apps erstellen Sie in einer Vorschauumgebung. Aktuelle Einschränkungen u.a.: Modellgesteuerte Apps können im Vorschauprogramm nicht erstellt werden. Wir arbeiten daran.
2. **Verwalten von Apps**: Sie können Apps über das [PowerApps-Webportal][2] verwalten und freigeben. Um auf die Vorschaufunktionen zuzugreifen, müssen Sie sich nur in einer Vorschauumgebung befinden – damit gelangen Sie zur Vorschauversion des [PowerApps-Webportals][3].
3. **Wiedergeben von Apps**: Sie müssen die Apps über den Webplayer in einer Vorschauumgebung wiedergeben. Wenn Sie dies tun, werden Sie automatisch an die [Vorschauversion des Webplayers][4] weitergeleitet. Apps werden mit der vNext-Version des PowerApps-Webplayers wiedergegeben. Aktuelle Einschränkungen u.a.: PowerApps Mobile für iOS, Android und Windows ist zurzeit nicht für die Vorschau verfügbar. Die Wiedergabe von Apps, die in der First Release-Umgebung erstellt wurden, funktioniert möglicherweise nicht. Wir arbeiten daran.
4. **Verwalten von PowerApps**: Über die [Vorschauversion von PowerApps Admin Center][1] stehen Administratorfunktionen als Vorschau zur Verfügung.

## <a name="how-to-get-early-access-to-the-upcoming-updates"></a>Wie erhalten ich Vorabzugriff auf die neuen Updates?
Alle Apps und zugehörigen Ressourcen für PowerApps sind in einer Umgebung gespeichert. Vorabzugriff auf alle Vorschaufunktionen ist auch in einer Umgebung möglich, die in einer Region erstellt wurde, in der die vNext-Version (Vorschau) bereitgestellt ist. Zurzeit gibt es nur eine Region, **Vorschau (USA)**, wie in der folgenden Abbildung gezeigt:

![](./media/preview-environment/env3-preview.png)

Wählen Sie **Vorschau (USA)** als Region für die Umgebung aus, und stimmen Sie der Teilnahme am Vorschauprogramm zu, um die Umgebung zu erstellen und Zugriff auf die nächste Version (vNext) von PowerApps zu erhalten.
Alle in dieser Umgebung erstellten Apps und weitere Ressourcen befinden sich in der vNext-Version der Plattform (SaaS).

## <a name="how-to-learn-about-the-latest-updates"></a>Wie erhalte ich Informationen zu den neuesten Updates?
Unter [Neuerungen bei PowerApps][5] erfahren Sie, welche neuen Funktionen für die Vorschau verfügbar sind. Die Funktionen, die in der Vorschau verfügbar sind, sind mit „Vorschau“ gekennzeichnet.

## <a name="key-scenarios-to-test-with-the-preview-program"></a>Wichtige Szenarien zum Testen mit dem Vorschauprogramm
1. **Überprüfen der Produktions-Apps mit den neuen PowerApps-Updates (vNext)**

   Sie möchten sicher überprüfen, ob Ihre Produktions-Apps mit den nächsten Updates in PowerApps funktionieren. Sie können die Apps aus einer Produktionsumgebung in eine First Release-Umgebung [kopieren][6] und wiedergeben, um die Szenarien zu testen. Beachten Sie, dass alle anderen erforderlichen Ressourcen wie CustomAPI, Flow usw. zusammen mit den Apps kopiert werden müssen. Dadurch entsteht einfach eine neue Kopie dieser Apps und erforderlichen Ressourcen. Sie können die neuen Updates nicht nur für die Wiedergabe von Apps testen, sondern auch während der Bearbeitung und Verwaltung der Apps.
   
2. **Testen der neuen in der Vorschau verfügbaren Funktionen**

   Wir werden viele neue Funktionen zunächst in der Region **Vorschau (USA)** starten. Sie können neue Funktionen testen, bevor diese in den verbleibenden Regionen zur Verfügung gestellt werden (dies kann Ihre Produktionsumgebung beeinträchtigen).

## <a name="how-to-provide-feedback-to-the-product-team"></a>Wie stelle ich dem Produktteam Feedback zur Verfügung?
Sie können Feedback im [PowerApps-Forum][8] bereitstellen und/oder sich an den [Support][9] wenden.

## <a name="what-are-the-known-issues-and-limitations"></a>Welche Probleme und Einschränkungen sind bekannt?
1. **PowerApps-Portale und -Clients, die nicht in der Vorschau verfügbar sind** 

   Es gibt bestimmte Funktionen, Dienste und Portale, die in der Vorschau verfügbar sind:
   
   ![](./media/preview-environment/table.png)

2. **Zugriff auf Apps, die über Desktop Studio in Windows in der First Release-Umgebung erstellt wurden**

   Wie bereits erwähnt, ist Desktop Studio in Windows in der Vorschau nicht verfügbar. Daher ist die Erstellung oder Bearbeitung der Apps in der Vorschauumgebung möglicherweise nicht mit Desktop Studio kompatibel, und es wird die folgende Fehlermeldung angezeigt:
   
   ![](./media/preview-environment/error2.jpg)

   In einem solchen Fall empfehlen wir die Verwendung von Web Studio, um die App in der Vorschauumgebung zu erstellen oder zu bearbeiten.

3. **Erstellen einer Datenbank in der Vorschauumgebung nicht möglich**

   Derzeit können Sie in einer Umgebung in der Region „Vorschau (USA)“ mit Common Data Service für Apps keine Datenbank erstellen. Wir arbeiten daran.


<!--Reference links in article-->
[1]: https://preview.admin.powerapps.com
[2]: https://web.powerapps.com
[3]: https://preview.web.powerapps.com
[4]: https://preview.web.powerapps.com/webplayer
[5]: https://docs.microsoft.com/powerapps/maker/canvas-apps/release-notes
[6]: https://docs.microsoft.com/powerapps/administrator/environment-and-tenant-migration
[7]: https://preview.create.powerapps.com
[8]: https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1
[9]: https://powerapps.microsoft.com/support/

