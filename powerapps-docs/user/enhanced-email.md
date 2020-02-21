---
title: 'Vorschau: Senden von E-Mails mithilfe der erweiterten E-Mail-Funktion in modellgesteuerten Apps | Microsoft-Dokumentation'
description: Hier erfahren Sie, wie Sie die erweiterte E-Mail-Funktion verwenden, um eine E-Mail zu erstellen, ohne Ihren aktuellen Arbeitskontext zu verlassen.
ms.date: 02/03/2020
ms.service:
- dynamics-365-sales
ms.topic: article
author: shubhadaj
ms.author: shujoshi
manager: annbe
ms.openlocfilehash: 6f3c603284e5f5d53380f5caa932cafac11e2d7a
ms.sourcegitcommit: 68a31e3fa4d1635ccf4cd8bd9da5fba1bfecefa4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/06/2020
ms.locfileid: "77051934"
---
# <a name="preview-send-email-using-the-enhanced-email-experience"></a>Vorschau: Senden von E-Mails mithilfe der erweiterten E-Mail-Funktion

Das Senden von E-Mails mithilfe der erweiterten E-Mail-Funktion ist ein Early-Access-Feature. Diese Features können frühzeitig in Ihrer Umgebung aktiviert werden, um sie zu testen und in Ihren Umgebungen einzuführen. Weitere Informationen zur Aktivierung dieser Features finden Sie unter [Aktivieren von Early-Access-Updates](https://docs.microsoft.com/power-platform/admin/opt-in-early-access-updates).

Mithilfe der erweiterten E-Mail-Funktion in modellgesteuerten Apps können Sie eine E-Mail erstellen, ohne den Datensatz zu verlassen, an dem Sie gerade arbeiten. Die erweiterte E-Mail-Funktion ermöglicht Folgendes:

- Navigieren zu anderen Seiten, ohne dass der E-Mail-Inhalt verloren geht
- Minimieren des E-Mail-Fensters, um zu den Datensätzen zurückzukehren, an denen Sie gearbeitet haben
- Erweitern des Popupfensters des E-Mail-Editors, um weitere E-Mail-Optionen anzuzeigen
- Gleichzeitiges Öffnen von drei Popupfenstern für die E-Mail-Erstellung
- Suchen nach einer vordefinierten Vorlage und Anwenden dieser Vorlage auf eine E-Mail, die Sie gerade erstellen
- Einfügen von Anlagen in eine E-Mail


> [!IMPORTANT]
> - Die erweiterte E-Mail-Funktion muss von einem Systemadministrator aktiviert werden, damit Sie sie verwenden können.
> - [!INCLUDE[cc_preview_features_definition](../includes/cc-preview-features-definition.md)]  
> - [!INCLUDE[cc_preview_features_expect_changes](../includes/cc-preview-features-expect-changes.md)]
> - [!INCLUDE[cc-preview-features-no-ms-support](../includes/cc-preview-features-no-ms-support.md)]

Gehen Sie wie folgt vor, um eine E-Mail mithilfe der erweiterten Funktion zu erstellen:

1. Wählen Sie im Abschnitt **Zeitachse** von Datensätzen (Konto, Kontakt oder Ähnliches) das Pluszeichen ( **+** ) und anschließend unter **Aktivitäten** die Option **E-Mail** aus.

   Daraufhin wird ein neues E-Mail-Popupfenster geöffnet. 

   > [!div class="mx-imgBorder"]
   > ![Popupfenster der erweiterten E-Mail-Funktion](media/enhanced-email-pop-up.png "Popupfenster der erweiterten E-Mail-Funktion")

   Die Felder **Von** und **An** werden automatisch auf der Grundlage des Benutzers sowie des Kontos und Kontakts des ursprünglichen Datensatzes ausgefüllt.

2. Sie können entweder eine E-Mail ohne Vorlage schreiben oder **Vorlage einfügen** auswählen, um nach einer Vorlage zu suchen und sie anzuwenden. Weitere Informationen zum Einfügen einer E-Mail-Vorlage finden Sie unter [Vorschau: Einfügen einer E-Mail-Vorlage](insert-email-template.md).

3. Falls Sie eine Anlage hinzufügen möchten, wählen Sie **Datei anfügen** aus.

4. Wählen Sie **Signatur einfügen** aus, um nach Ihrer Signatur zu suchen und sie hinzuzufügen.

5. Wählen Sie abschließend **Senden** aus. 

> [!IMPORTANT]
> - Die erweiterte E-Mail-Funktion steht nur für E-Mail-Aktivitäten zur Verfügung, die im Abschnitt **Zeitachse** einer modellgesteuerten App erstellt werden. 
> - Das Popupfenster der erweiterten E-Mail-Funktion wird nur geöffnet, wenn die Höhe und Breite Ihrer Bildschirmgröße mindestens 400 x 650 Pixel beträgt. Andernfalls wird anstelle der erweiterten E-Mail-Funktion das Standardformular verwendet. 

### <a name="see-also"></a>Siehe auch

[Systemeinstellungen – E-Mail (Registerkarte)](https://docs.microsoft.com/power-platform/admin/system-settings-dialog-box-email-tab)<br>
[Vorschau: Einfügen einer E-Mail-Vorlage](insert-email-template.md)
