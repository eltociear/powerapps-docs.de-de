---
title: Aktualisieren eines Portale | MicrosoftDocs
description: Erfahren Sie, wie Sie ein Portal aktualisieren.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/18/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 7f8837179ccf9edb7376db88ee421e4cb424909f
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "2978543"
---
# <a name="upgrade-a-portal"></a>Aktualisieren eines Portals

Dieser Abschnitt hilft Ihnen, den Freigabeprozess von Dynamics 365 Portale zu verstehen, um sich auf jede neue Version richtig vorzubereiten und die Auswirkungen auf Ihre Kunden zu reduzieren. Es wird auch über verschiedene Komponenten gesprochen, die Teil des Portals sind.

Ein Portal besteht aus den folgenden Komponenten:

|Komponente|Beschreibung|Aktualisierungsvorgang|
|---------|-----------|--------------|
|Portallösungen|Lösungen, die in einer Common Data Service-Umgebung installiert sind und die Metadaten-Entitäten für jedes Portal enthalten.|Von Kunden selbst über die Dynamics 365-Verwaltungskonsolenseite aktualisiert.|
|Portalwebsitehost|Portalwebsitehost ist der Portalcode, der die eigentliche Website formt.|Der Portalwebsitehost wird automatisch für alle Portale aktualisiert.<br>**Hinweis**: Eine neue Version des Portalwebsitehosts ist in allen unterstützten Versionen der Portallösungen abwärtskompatibel. Wenn jedoch eine Lösungsversion nicht mehr unterstützt wird, ist sie nicht dafür zertifiziert, mit der neuen Version des Portalwebsitehosts ausgeführt zu werden.|
|||

## <a name="impact-of-new-releases-on-a-portal-solution"></a>Auswirkungen neuer Veröffentlichungen auf einer Portallösung

Als Teil einer Portalversion werden Portalwebsitehosts automatisch auf die neuesten Versionen aktualisiert, wenn Portallösungen von Kunden aktualisiert werden. Es ist wichtig, die Auswirkungen der einzelnen Komponentenupdates auf das Liveportal zu verstehen, sodass Sie entsprechend planen können.

### <a name="portal-website-host-update"></a>Portalwebsitehost-Update

Wenn Sie eine Produktionsversion von Portal verwenden (Sie können sie im Power Apps Portale Administrationscenter sehen), wird es keine Ausfallzeiten in Ihrem Live-Portal geben, wenn Ihr Portal aktualisiert wird. Wenn Sie allerdings eine Testversion des Portals ausführen, gibt es 6-10 Minuten Ausfallzeit, und Sie können nicht auf Ihr Portal zugreifen.

### <a name="portal-solution-update"></a>Portallösungs-Update

Während der Installation oder Aktualisierung einer Lösung in Ihrer Instanz können Sie eine gewisse Instabilität in Ihrer Instanz feststellen. Die Aktualisierung der Portallösung aktualisiert die in Ihrer Instanz verfügbaren Lösungen und wirkt sich auf Ihre Instanz aus, was wiederum Auswirkungen auf Ihr Portal hat. Daher ist es immer ratsam, in Ihrer Instanz während der Nachtzeiten Lösungs-Updates durchzuführen.

## <a name="get-notified-about-new-releases"></a>Lassen Sie über neue Veröffentlichungen benachrichtigten

Jeder Kunde wird über das Office 365-Nachrichtencenter (im Microsoft 365 Administrationscenter) über die neue Portalversion benachrichtigt. Stellen Sie sicher, dass Sie entweder Zugriff auf das Nachrichtencenter Office 365 haben (Globaler Administrator und Service-Administrator haben Zugriff) oder mit Ihrem globalen Administrator oder Service-Administrator besprochen haben, um Sie über jedes neue Portal-Release zu informieren.

Benachrichtigungen werden etwa alle 2-5 Werktage vor der Version gesendet. Benachrichtigungen werden nur an die Kunden gesendet, deren Portale aktualisiert werden sollen. Jede Benachrichtigung enthält Details zum Typ des Updates und zu Datum/Uhrzeit, zu der es bereitgestellt wird sowie ein Link zu den Anmerkungen zur Version.

## <a name="enable-a-portal-for-new-release"></a>Aktivieren eines Portals für eine neue Version

Sie können ein Entwicklungs- oder Testportal aktivieren, um das Upgrade vor anderen Kunden zu erhalten, damit Sie alle Kernszenarien in Ihrem Testportal testen können, bevor ein Upgrade Ihres Liveportals bereitgestellt wird. Frühe Upgrades werden mindestens eine Woche vor der globalen Einführung jeder Version bereitgestellt. Außerdem werden Benachrichtigungen für frühe Upgrades wie in [Lassen Sie sich über neue Versionen benachrichtigen](#get-notified-about-new-releases) beschrieben gesendet.

So aktivieren Sie ein Portal für frühes Upgrade:

1.  Öffnen Sie das [Admin Center für Power Apps-Portale](admin-overview.md).

2.  Wählen Sie auf der Registerkarte **Portalaktionen** die Option **Portal für frühes Upgrade aktivieren** aus.

    > [!div class="mx-imgBorder"]
    > ![Ein Portal für frühes Upgrade aktivieren](../media/upgrade-portal.png "Ein Portal für ein frühzeitiges Upgrade aktivieren")

> [!NOTE]
> Sie können ein Portal jederzeit für frühes Upgrade aktivieren oder deaktivieren. Allerdings wird von allen Portalen, die für frühes Upgrade markiert sind, zwei Tage vor einer Veröffentlichung eine Momentaufnahme aufgenommen, und bei Portalen, die danach für frühen Zugriff markiert werden, ist ein frühes Upgrade nicht garantiert.

Falls ein Problem beim frühen Upgrade auftritt, können Sie dies über den Microsoft-Support melden.


