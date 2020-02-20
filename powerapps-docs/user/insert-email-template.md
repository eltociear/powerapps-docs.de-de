---
title: Einfügen einer E-Mail-Vorlage beim Verfassen einer E-Mail in modellgesteuerten Apps | Microsoft-Dokumentation
description: Einfügen einer vorformatierten E-Mail-Nachricht beim Verfassen einer E-Mail
ms.date: 02/03/2020
ms.service:
- dynamics-365-sales
ms.topic: article
author: sbmjais
ms.author: shjais
manager: shujoshi
ms.openlocfilehash: abbef00f3b93809dadf617c4180b52a1372e625a
ms.sourcegitcommit: 68a31e3fa4d1635ccf4cd8bd9da5fba1bfecefa4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/06/2020
ms.locfileid: "77051842"
---
# <a name="preview-insert-an-email-template"></a>Vorschauversion: Hinzufügen einer E-Mail-Vorlage

Das Einfügen einer E-Mail-Vorlage ist ein Early-Access-Feature. Sie können diese Features frühzeitig in Ihrer Umgebung aktivieren. So können Sie diese testen und dann in Ihre Umgebungen einführen. Weitere Informationen zur Aktivierung dieser Features finden Sie unter [Aktivieren von Early-Access-Updates](https://docs.microsoft.com/power-platform/admin/opt-in-early-access-updates).

Zum schnellen Erstellen und Senden von E-Mails können Sie eine E-Mail-Vorlage bzw. eine vorformatierte E-Mail-Nachricht verwenden. Sie können die Vorlage einfügen, während Sie eine E-Mail verfassen. Wählen Sie hierzu auf der Befehlsleiste **Vorlage einfügen** aus. Die Liste der verfügbaren Vorlagen wird im Fenster **E-Mail-Vorlagen** angezeigt. Im Abschnitt **Zuletzt verwendet** werden die vier von Ihnen zuletzt verwendeten Vorlagen angezeigt. Im Abschnitt **Alle Vorlagen** wird eine Liste aller standardmäßig verfügbaren E-Mail-Vorlagen (globale und entitätsspezifische) in alphabetischer Reihenfolge angezeigt. Globale Vorlagen werden als Typ „Benutzer“ angezeigt. Wenn Sie eine benutzerdefinierte E-Mail-Vorlage erstellt haben, ist sie hier ebenfalls verfügbar. Weitere Informationen zum Erstellen einer benutzerdefinierten E-Mail-Vorlage finden Sie unter [Vorlagen für E-Mails erstellen](https://docs.microsoft.com/power-platform/admin/create-templates-email).

Sie können Vorlagen einer bestimmten Sprache anzeigen, indem Sie eine Sprache aus der Liste **Sprache** auswählen. Sie können entweder nach einer Vorlage suchen oder die Liste durchsuchen und eine Vorlage auswählen. Wenn Sie eine E-Mail-Vorlage auswählen, wird auf der rechten Seite des Fensters eine Vorschau angezeigt. In der Vorschau werden Ihnen die Inhalte angezeigt, sodass Sie die Vorlage auswählen können, die Ihren Anforderungen am besten entspricht. Nachdem Sie eine E-Mail-Vorlage eingefügt haben, können Sie den Inhalt nach Bedarf ändern und dann die E-Mail senden.

> [!NOTE]
> Die Suche unterstützt keine regulären Ausdrücke und funktioniert nur mit dem Namen der Vorlage.

**So fügen Sie eine E-Mail-Vorlage ein**

1.  Wählen Sie im E-Mail-Editor auf der Befehlsleiste **Vorlage einfügen** aus.

     > [!div class="mx-imgBorder"]
     > ![Schaltfläche „Vorlage einfügen“](media/insert-email-template-button.png "Schaltfläche „Vorlage einfügen“") 

    Das Fenster **E-Mail-Vorlagen** wird geöffnet.

2.  Wählen Sie eine Sprache aus der Liste **Sprache** aus, um Vorlagen eines anderen Gebietsschemas anzuzeigen. Die Vorlagen werden entsprechend der gewählten Sprache geladen.    

3.  Suchen Sie nach der gewünschten Vorlage. Wählen Sie die Vorlage aus, und klicken Sie in der Vorschau auf den Inhalt der Vorlage.

4.  Optional können Sie den Pfeil nach unten neben dem Vorlagennamen auswählen, um eine Beschreibung des Inhalts anzuzeigen.

5.  Wählen Sie **Vorlage anwenden** aus, um den Inhalt in die E-Mail einzufügen.

     > [!div class="mx-imgBorder"]
     > ![Fenster „E-Mail-Vorlagen“](media/email-templates-window.png "Fenster „E-Mail-Vorlagen“")

Wenn Sie eine E-Mail-Vorlage auf einem Gerät mit einer geringeren Bildschirmgröße einfügen, sehen Sie nur eine Option, mit der Sie eine Vorlage suchen und auswählen können.

> [!div class="mx-imgBorder"]
> ![Vorlage suchen](media/search-template.png "Vorlage suchen") 

### <a name="see-also"></a>Siehe auch

[Einrichten von erweiterten E-Mail-Funktionen](https://docs.microsoft.com/power-platform/admin/system-settings-dialog-box-email-tab)<br>
[Verfassen und Senden von E-Mails mithilfe erweiterter E-Mail-Funktionen](enhanced-email.md)
