---
title: Informationen zum Power Apps-Portallebenszyklus | Microsoft-Dokumentation
description: Informationen zum Power Apps-Portallebenszyklus und Konvertieren von einer Testversion in eine Produktionsumgebung.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 12/26/2019
ms.author: shjais
ms.reviewer: tapanm
ms.openlocfilehash: 26e02d2b8c8a8d47ed41727e13150875bfa307a4
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934512"
---
# <a name="about-portal-lifecycle"></a>Info über den Portallebenszyklus

Ein Portal wird immer als Testversion erstellt. Ein Testportal, das nach 30 Tagen abläuft, ist für den kostenlosen Test der Funktionen hilfreich. Nach Ablauf wird ein Portal abgeschaltet und heruntergefahren. Sieben Tage nach Abschaltung wird das Testportal gelöscht. Bei jeder Änderung einer Portallebenszyklusphase, wie bevorstehende Abschaltung, abgeschaltet, gelöscht und konvertiert von der Testversion in die Produktionsumgebung, erhalten Sie Benachrichtigungen als Toast und per E-Mail.

Als Administrator können Sie ein Test- oder abgeschaltetes Portal in ein Produktionsportal konvertieren. Beim Konvertieren eines Testportals in die Produktionsumgebung müssen Sie sicherstellen, dass die Umgebung auch eine Produktionsumgebung ist. Sie können ein Testportal nicht in einer Testumgebung in eine Produktionsumgebung konvertieren. Wenn Sie die Umgebung löschen, in der ein Testportal erstellt wurde, wird das Portal ebenfalls gelöscht.

Das erste Portal kann in einer Umgebung in einem Mandanten kostenlos erstellt werden. Wenn Sie mehr als ein Portal erstellen müssen, brauchen Sie 1 GB ungenutzten Speicherplatz im Mandanten.

## <a name="stages-in-portal-lifecycle"></a>Phasen im Portallebenszyklus

### <a name="trial-portal"></a>Testportal

Ein Portal wird immer als Testportal erstellt. Sie können es im Power Apps-Portal-Administratorcenter in eine Produktionsumgebung konvertieren, wenn Sie die erforderlichen Lizenzen besitzen. Informationen zum Konvertieren eines Testportals in die Produktionsumgebung finden Sie unter [Konvertieren eines Testportals in die Produktionsumgebung](#convert-a-trial-portal-to-production).

Um ein Testportal in die Produktionsumgebung zu konvertieren, braucht die Umgebung die erforderlichen Add-Ons für externe Benutzer oder eine Lizenz für interne Benutzer. Weitere Informationen zu Lizenzen finden Sie unter [FAQs zur Power Apps- und Power Automate-Lizenzierung](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq) und [Power Apps- Portal-Lizenzierung](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#can-you-share-more-details-regarding-the-new-power-apps-portals-licensing).

### <a name="suspended-portal"></a>Abgeschaltetes Portal

Es werden weiterhin Benachrichtigungen im Power Apps-Portal-Administratorcenter zum Ablauf des Testportals angezeigt. Testportale laufen nach 30 Tagen ab. Wenn Sie Ihr Portal innerhalb des Testzeitraums nicht in die Produktionsumgebung konvertieren, wird das Portal heruntergefahren und auf den Status „Abgeschaltet“ gesetzt. Es ist nicht möglich, auf das Portal nach dem Ablauf zuzugreifen.

Das abgeschaltete Portal kann aber noch innerhalb von sieben Tagen nach Abschaltung in die Produktionsumgebung konvertiert werden. 

### <a name="deleted-portal"></a>Gelöschtes Portal

Wenn Sie Ihr Portal nicht innerhalb von sieben Tagen nach Abschaltung in die Produktionsumgebung konvertieren, wird das Portal gelöscht. Die Portaldaten werden nicht aus der Umgebung gelöscht, aber der Speicherplatz, der vom Portal in einer Umgebung verwendet wurde, wird freigegeben, und Sie können ein neues Portal erstellen.

## <a name="convert-a-trial-portal-to-production"></a>Ein Testportal in die Produktionsumgebung konvertieren

Sie können ein Testportal über die Benachrichtigungen, die im Power Apps-Portal-Administratorcenter angezeigt werden, in eine Produktionsumgebung konvertieren.

> [!NOTE]
> Ihnen muss eine der folgenden Rollen zugewiesen sein, um ein Testportal in die Produktionsumgebung zu konvertieren:
> - Globaler Administrator
> - Systemadministrator

Wenn Sie das [Power Apps-Portal-Administratorcenter](admin-overview.md) öffnen und zur Registerkarte [Portaldetails](portal-details.md) navigieren, wird die Benachrichtigung über den Testablauf unterhalb des **Typ**-Felds angezeigt.

> [!div class=mx-imgBorder]
> ![Testbenachrichtigung auf der Portaldetail-Registerkarte](../media/admin-center-convert-notif.png "Testbenachrichtigung auf der Portaldetail-Registerkarte")

Auf anderen Seiten im Administratorcenter wird die Benachrichtigung oben auf der Seite angezeigt.

> [!div class=mx-imgBorder]
> ![Testbenachrichtigung auf anderen Registerkarten](../media/admin-center-convert-notif-all.png "Testbenachrichtigung auf anderen Registerkarten")

So konvertieren Sie ein Testportal in die Produktionsumgebung:

1.  Wählen Sie in der Benachrichtigung **Konvertieren** aus.

2.  Wählen Sie **Bestätigen** aus.

    > [!div class=mx-imgBorder]
    > ![Bestätigung für die Konvertierung der Testversion in die Produktionsumgebung](../media/trial-to-prod-confirm.png "Bestätigung für die Konvertierung der Testversion in die Produktionsumgebung")

## <a name="considerations-for-add-on-portals"></a>Überlegungen zu Add-On-Portalen

Die folgenden Bedingungen gelten für Portale [Bereitstellung mit dem Portal-Add-On-Plan](../provision-portal-add-on.md), die früher gekauft wurden:

### <a name="trial-add-on-portal"></a>Test-Add-on-Portal

Das Test-Add-On-Portal läuft nach 30 Tagen ab. Das abgelaufene Portal ist für 7 Tage gesperrt. Das Portal wird nach Ablauf der Sperrfrist gelöscht. Das Test-Add-On-Portal kann während des konfigurierten oder angehaltenen Zeitraums weiterhin auf die Produktion umgestellt werden.

### <a name="production-add-on-portal"></a>Produktion-Add-On-Portal

Das Produktions-Add-On-Portal läuft am Ende des erworbenen Lizenzzeitraums ab. Die Sperrfrist für ein Produktions-Add-On-Portal kann je nach erworbenem Lizenzplan variieren. Das Portal wird nach Ablauf der Sperrfrist gelöscht. Sie können die Lizenz eines Produktions-Add-On-Portals verlängern, während sich das Portal im konfigurierten oder angehaltenen Zustand befindet. Wenn das Portal angehalten wird, kann es nach Verlängerung des Lizenzzeitraums in den konfigurierten Status konvertiert werden.

> [!IMPORTANT]
> Das Aussetzen oder Löschen eines Portals kann zu Funktionsverlust führen. Stellen Sie eine zeitnahe Verlängerung des Lizenzzeitraums für das Add-On-Portal sicher, um ein Aussetzen oder Löschen zu vermeiden.

### <a name="reset-add-on-portal"></a>Add-on-Portal zurücksetzen

Folgen Sie den Schritten, um das Portal [zurücksetzen](reset-portal.md), das mit einem zuvor gekauften älteren Portal-Add-On-Plan bereitgestellt wird.

## <a name="see-also"></a>Siehe auch

[Power Apps Portale FAQs](../faq.md)
