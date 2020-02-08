---
title: Vorschau für e-Mail senden mithilfe der erweiterten e-Mail-Leistung in Modell gesteuerten apps | MicrosoftDocs
description: Verwenden Sie die erweiterte e-Mail-Erfahrung, um eine e-Mail zu verfassen, ohne den Kontext ihrer Arbeit zu belassen.
ms.date: 02/03/2020
ms.service:
- dynamics-365-sales
ms.topic: article
author: shubhadaj
ms.author: shujoshi
manager: annbe
ms.openlocfilehash: 6f3c603284e5f5d53380f5caa932cafac11e2d7a
ms.sourcegitcommit: 68a31e3fa4d1635ccf4cd8bd9da5fba1bfecefa4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/06/2020
ms.locfileid: "77051934"
---
# <a name="preview-send-email-using-the-enhanced-email-experience"></a>Vorschau: Senden von e-Mails mithilfe der erweiterten e-Mail-Funktion

Das Senden von e-Mails mithilfe der erweiterten e-Mail-Funktion ist eine Funktion für den frühen Zugriff. Sie können sich früh entscheiden, diese Features in Ihrer Umgebung zu aktivieren. Auf diese Weise können Sie diese Features testen und Sie dann in ihren Umgebungen übernehmen. Informationen dazu, wie Sie diese Features aktivieren, finden [Sie unter Opt in 2020 Release Wave 1 Updates](https://docs.microsoft.com/power-platform/admin/opt-in-early-access-updates).

Dank der verbesserten e-Mail-Benutzererfahrung in Modell gesteuerten Apps können Sie eine e-Mail verfassen, ohne den Datensatz zu belassen, an dem Sie arbeiten. Mit der verbesserten e-Mail-Leistung können Sie folgende Aktionen ausführen:

- Navigieren zu anderen Seiten, ohne den e-Mail-Inhalt zu verlieren.
- Minimieren Sie das e-Mail-Fenster, um zu den Datensätzen zurückzukehren, an denen Sie arbeiteten
- Erweitern Sie das Popup Fenster e-Mail-Editor, um weitere e-Mail-Optionen anzuzeigen.
- Öffnen Sie gleichzeitig drei Popup Fenster für das Erstellen von e-Mail.
- Suchen Sie eine vordefinierte Vorlage, und wenden Sie Sie auf eine von Ihnen zusammengesetzte e-Mail an.
- Fügt Anlagen in eine e-Mail ein.


> [!IMPORTANT]
> - System Administratoren müssen die erweiterte e-Mail-Leistung aktivieren, bevor Sie Sie verwenden können.
> - [!INCLUDE[cc_preview_features_definition](../includes/cc-preview-features-definition.md)]  
> - [!INCLUDE[cc_preview_features_expect_changes](../includes/cc-preview-features-expect-changes.md)]
> - [!INCLUDE[cc-preview-features-no-ms-support](../includes/cc-preview-features-no-ms-support.md)]

Erstellen Sie eine e-Mail mithilfe des erweiterten Erlebnisses:

1. Wählen Sie im Abschnitt **Zeitachse** von Datensätzen wie Konto oder Kontakt **+** aus, und wählen Sie dann unter **Aktivitäten**die Option **e-Mail**aus.

   Ein neues e-Mail-Popup Fenster wird geöffnet. 

   > [!div class="mx-imgBorder"]
   > ![Popup Fenster für erweiterte e-Mail](media/enhanced-email-pop-up.png "Popup Fenster für erweiterte e-Mail")

   Die Felder **from** und **to** werden automatisch basierend auf dem Benutzer und dem Konto und dem Kontakt zum ursprünglichen Datensatz aufgefüllt.

2. Schreiben Sie Ihre e-Mail von Grund auf, oder wählen Sie **Vorlage einfügen** aus, um nach Vorlagen zu suchen und diese anzuwenden. Weitere Informationen zum Einfügen einer e-Mail-Vorlage finden Sie unter [Einfügen einer e-Mail-Vorlage](insert-email-template.md).

3. Wählen Sie **Datei** anfügen aus, wenn Sie Anlagen hinzufügen möchten.

4. Wählen Sie **Signatur einfügen** aus, um die Signatur zu suchen und hinzuzufügen.

5. Wenn Sie fertig sind, wählen Sie **senden**aus. 

> [!IMPORTANT]
> - Die erweiterte e-Mail-Leistung ist nur für e-Mail-Aktivitäten verfügbar, die im Abschnitt " **Timeline** " einer Modell gesteuerten App erstellt wurden. 
> - Das Popup Fenster Erweiterte e-Mail wird nur geöffnet, wenn die Höhe und Breite der Bildschirmgröße mindestens 400 x 650 Pixel oder größer ist. Wenn Sie niedriger sind, werden Sie anstelle der erweiterten e-Mail-Leistung zum Standardformular weitergeleitet. 

### <a name="see-also"></a>Siehe auch

[Erweiterte e-Mail einrichten](https://docs.microsoft.com/power-platform/admin/system-settings-dialog-box-email-tab)<br>
[E-Mail-Vorlage einfügen](insert-email-template.md)
