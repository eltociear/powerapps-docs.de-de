---
title: 'Vorschau: Senden von E-Mails mithilfe der erweiterten E-Mail-Funktion in modellgesteuerten Apps | Microsoft-Dokumentation'
description: Hier erfahren Sie, wie Sie die erweiterte E-Mail-Funktion verwenden, um eine E-Mail zu erstellen, ohne Ihren aktuellen Arbeitskontext zu verlassen.
ms.date: 04/09/2020
ms.service:
- dynamics-365-sales
ms.topic: article
author: shubhadaj
ms.author: shujoshi
manager: annbe
ms.openlocfilehash: bc4b7023e56ae75b34f797089a812ab4ea1f8d84
ms.sourcegitcommit: 2484ebce6563cfd1c849e1e2f66dd2d29fdb7b64
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/10/2020
ms.locfileid: "3303620"
---
# <a name="send-email-using-the-enhanced-email-experience"></a>Senden von E-Mails mithilfe der erweiterten E-Mail-Funktion

Mithilfe der erweiterten E-Mail-Funktion in modellgesteuerten Apps können Sie eine E-Mail erstellen, ohne den Datensatz zu verlassen, an dem Sie gerade arbeiten. Die erweiterte E-Mail-Funktion ermöglicht Folgendes:

- Navigieren Sie zu verschiedenen Seiten, ohne den E-Mail-Inhalt zu verlieren.
- Minimieren Sie das E-Mail-Fenster, um zu den Datensätzen zurückzukehren, an denen Sie gerade gearbeitet haben.
- Erweitern Sie das Popupfenster des E-Mail-Editors, um mehr E-Mail-Optionen anzuzeigen.
- Öffnen Sie gleichzeitig drei Popupfenster zur E-Mail-Verfassung.
- Suchen Sie eine vordefinierte Vorlage einer E-Mail. die Sie gerade verfassen, und übernehmen Sie sie.
- Fügen Sie Anlagen an eine E-Mail an.


> [!IMPORTANT]
> - Systemadministratoren müssen die erweiterte E-Mail-Umgebung aktivieren, bevor Sie sie verwenden können.
> - [!INCLUDE[cc_preview_features_definition](../includes/cc-preview-features-definition.md)]  
> - [!INCLUDE[cc_preview_features_expect_changes](../includes/cc-preview-features-expect-changes.md)]
> - [!INCLUDE[cc-preview-features-no-ms-support](../includes/cc-preview-features-no-ms-support.md)]

Gehen Sie wie folgt vor, um eine E-Mail mithilfe der erweiterten Funktion zu erstellen:

1. Im Abschnitt **Zeitskala** der Datensätze wie Firma oder Kontakts wählen Sie **+** und dann unter **Aktivitäten** die Option **E-Mail** aus.

   Ein neues E-Mail-Popupfenster öffnet sich. 

   > [!div class="mx-imgBorder"]
   > ![Verbessertes E-Mail-Pop-Up-Fenster](media/enhanced-email-pop-up.png "Verbessertes E-Mail-Pop-Up-Fenster")

   Die Felder **Von** und **An** werden automatisch anhand des Benutzers und der Firma sowie des Kontakts des ursprünglichen Datensatzes aufgefüllt.

2. Schreiben Sie Ihre E-Mail von Grund auf oder wählen Sie **Vorlage einfügen** zum Suchen und Anwenden einer Vorlage. Weitere Informationen zum Einfügen einer E-Mail-Vorlage finden Sie unter [Einfügen einer E-Mail-Vorlage](insert-email-template.md).

3. Wählen Sie **Datei anhängen** aus, wenn Sie Anhänge anfügen möchten.

4. Wählen Sie **Signatur einfügen** aus, um nach Ihrer Signatur zu suchen und sie hinzuzufügen.

5. Wählen Sie **Senden** aus, wenn Sie fertig sind. 

> [!IMPORTANT]
> - Die erweiterte E-Mail-Funktion steht nur für E-Mail-Aktivitäten zur Verfügung, die im Abschnitt **Zeitachse** einer modellgesteuerten App erstellt werden. 
> - Das Popupfenster der erweiterten E-Mail-Funktion wird nur geöffnet, wenn die Höhe und Breite Ihrer Bildschirmgröße mindestens 400 x 650 Pixel beträgt. Wenn sie geringer ist, werden Sie automatisch zum Standardformular der erweiterten E-Mail-Umgebung geführt. 

### <a name="see-also"></a>Siehe auch

[Erweiterte E-Mail einrichten](https://docs.microsoft.com/power-platform/admin/system-settings-dialog-box-email-tab)<br>
[E-Mail-Vorlage einfügen](insert-email-template.md)
