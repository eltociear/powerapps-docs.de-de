---
title: Informationen zum Power Apps-Portallebenszyklus | Microsoft-Dokumentation
description: Informationen zum Power Apps-Portallebenszyklus und Konvertieren von einer Testversion in eine Produktionsumgebung.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 60300176f0a39258bbb7030c9e30d9b2e7711990
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "2874648"
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
