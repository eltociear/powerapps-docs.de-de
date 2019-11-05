---
title: Informationen zum Lebenszyklus von powerapps-Portalen | MicrosoftDocs
description: Informationen über den Lebenszyklus von powerapps-Portalen und deren Umstellung von Testversion in die Produktion.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 5476bb0306b5d9e0767f451fba36a567a70c4c54
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542947"
---
# <a name="about-portal-lifecycle"></a>Informationen zum Lebenszyklus des Portals

Ein Portal wird immer als Testversion erstellt. Ein testportal, das nach 30 Tagen abläuft, ist nützlich, um seine Funktionen kostenlos auszuprobieren. Nach dem Ablauf wird ein Portal angehalten und heruntergefahren. Sieben Tage nach dem anhalten wird das testportal gelöscht. Bei jeder Änderung der Lebenszyklusphase des Portals, z. b. zum Anhalten, anhalten, löschen und Konvertieren von Testversionen in die Produktion, erhalten Sie Benachrichtigungen als Toast und per e-Mail.

Als Administrator können Sie eine Testversion oder ein angehaltene Portal in ein Produktions Portal konvertieren. Stellen Sie beim Umstellen eines Test Portals in die Produktion sicher, dass die Umgebung auch eine Produktionsumgebung ist. Sie können ein testportal in einer Testumgebung nicht in eine Produktionsumgebung konvertieren. Wenn Sie die Umgebung löschen, in der ein testportal erstellt wurde, wird das Portal ebenfalls gelöscht.

Das erste Portal kann in einer Umgebung in einem Mandanten erstellt werden. Wenn Sie mehr als ein Portal erstellen müssen, benötigen Sie im Mandanten 1 GB nicht genutzten Speicherplatz.

## <a name="stages-in-portal-lifecycle"></a>Phasen im Portal Lebenszyklus

### <a name="trial-portal"></a>Testportal

Ein Portal wird immer als testportal erstellt. Wenn Sie über die erforderlichen Lizenzen verfügen, können Sie Sie über das powerapps-Portal Admin Center in die Produktion konvertieren. Informationen zum Konvertieren eines Test Portals in die Produktion finden Sie unter [Konvertieren eines Test Portals in eine Produktions](#convert-a-trial-portal-to-production)Umgebung.

Zum Konvertieren eines Test Portals in die Produktion muss die Umgebung über erforderliche Add-ons für externe Benutzer oder eine Lizenz für interne Benutzer verfügen. Weitere Informationen zur Lizenzierung finden Sie unter Häufig gestellte Fragen zu [powerapps und Microsoft Flow Lizenzierung](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq) und [powerapps-Portale-Lizenzierung](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#can-you-share-more-details-regarding-the-new-powerapps-portals-licensing).

### <a name="suspended-portal"></a>Angehaltene Portal

Weitere Informationen zum Ablauf des Test Portals finden Sie im Admin Center für die powerapps-Portale. Test Portale laufen nach 30 Tagen ab. Wenn Sie Ihr Portal innerhalb des Testzeitraums nicht in die Produktion konvertieren, wird das Portal heruntergefahren und in den Status "angehalten" versetzt. Sie können nach dem Ablauf nicht mehr auf Ihr Portal zugreifen.

Allerdings kann das angehaltene Portal innerhalb von sieben Tagen nach der Unterbrechung immer noch in die Produktion konvertiert werden. 

### <a name="deleted-portal"></a>Gelöschtes Portal

Wenn Sie Ihr Portal innerhalb des Zeitraums von sieben Tagen nicht in die Produktion konvertieren, wird das Portal gelöscht. Die Portal Daten werden nicht aus der Umgebung gelöscht, aber der Speicherplatz, der vom Portal in einer Umgebung verwendet wird, wird freigegeben, und Sie können ein neues Portal erstellen.

## <a name="convert-a-trial-portal-to-production"></a>Konvertieren eines Test Portals in eine Produktionsumgebung

Sie können ein testportal in die Produktion konvertieren, indem Sie die Benachrichtigungen im Admin Center der powerapps-Portale anzeigen.

> [!NOTE]
> Sie müssen einer der folgenden Rollen zugewiesen sein, um ein testportal in eine Produktionsumgebung zu konvertieren:
> - Globaler Administrator
> - System Administrator

Wenn Sie das [powerapps-Portal Admin Center](admin-overview.md) öffnen und zur Registerkarte " [Portal Details](portal-details.md) " navigieren, wird die Benachrichtigung über den Ablauf der Testversion unter dem Feld " **Typ** " angezeigt.

> [!div class=mx-imgBorder]
> ![Test Benachrichtigung auf der Registerkarte "Portal Details"](../media/admin-center-convert-notif.png "Test Benachrichtigung auf der Registerkarte "Portal Details"")

Auf anderen Seiten im Admin Center wird die Benachrichtigung oben auf der Seite angezeigt.

> [!div class=mx-imgBorder]
> ![Test Benachrichtigung auf anderen Registerkarten](../media/admin-center-convert-notif-all.png "Test Benachrichtigung auf anderen Registerkarten")

So konvertieren Sie Ihr testportal in die Produktion:

1.  Wählen Sie in der Benachrichtigung **konvertieren**aus.

2.  Wählen Sie **bestätigen**aus.

    > [!div class=mx-imgBorder]
    > ![Bestätigung der Testversion in der Produktion](../media/trial-to-prod-confirm.png "Bestätigung der Testversion in der Produktion")
