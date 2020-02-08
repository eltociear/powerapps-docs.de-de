---
title: Anzeigen und Erstellen von e-Mails in Modell gesteuerten apps | MicrosoftDocs
description: Anzeigen und Erstellen von e-Mails bei Verwendung einer Modell gesteuerten app.
ms.date: 02/03/2020
ms.service:
- dynamics-365
ms.topic: article
author: lalexms
ms.author: lalexms
manager: shujoshi
ms.openlocfilehash: 7a0dee04334f52518c1746b6650f75ebfb67634d
ms.sourcegitcommit: 68a31e3fa4d1635ccf4cd8bd9da5fba1bfecefa4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/06/2020
ms.locfileid: "77051911"
---
# <a name="preview-view-and-create-email-through-the-activities-grid"></a>Vorschau: anzeigen und Erstellen von e-Mails über das Raster "Aktivitäten"

Das anzeigen und Erstellen von e-Mails über das Raster "Aktivitäten" ist eine Funktion für den frühen Zugriff. Sie können sich früh entscheiden, diese Features in Ihrer Umgebung zu aktivieren. Auf diese Weise können Sie diese Features testen und Sie dann in ihren Umgebungen übernehmen. Informationen dazu, wie Sie diese Features aktivieren, finden [Sie unter Opt in 2020 Release Wave 1 Updates](https://docs.microsoft.com/power-platform/admin/opt-in-early-access-updates).

Mit den Modell gesteuerten Dynamics 365-Apps können Sie per e-Mail mit Kunden interagieren. Die e-Mail-Funktionalität ermöglicht Ihnen Folgendes:

- Sie können e-Mails anzeigen und darauf reagieren. 

- Nutzen Sie die allgemeinen Funktionen für e-Mail-Symbolleisten und Rich Texteditor 

- Verwenden Sie die Drag & Drop-Funktion oder die Kopier-und Einfügefunktion, um Bilder inline anzuzeigen und einzufügen. 

- Erstellen Sie eine e-Mail in einem Popup Fenster.  

- Vorschau Vorlagen vor deren Anwendung. 



## <a name="view-your-email"></a>E-Mail anzeigen

So zeigen Sie Ihre e-Mail an:

1. Wählen Sie in der Sitemap der Modell gesteuerten APP **Aktivitäten**aus. 

2. Wählen Sie die Dropdown-Option **alle Aktivitäten** aus, und wählen Sie dann **meine empfangenen e-Mails**aus.

    ![e-Mail anzeigen](media/view-email.png "Empfangene e-Mails anzeigen")

3. Wählen Sie die e-Mail aus, die Sie anzeigen möchten, um Sie zu öffnen. Die e-Mail wird geöffnet, und Sie können dann an den Absender und die Empfänger Antworten oder Sie weiterleiten.

## <a name="create-email"></a>E-Mail erstellen

In den folgenden Schritten wird beschrieben, wie Sie eine e-Mail erstellen.

1. Wählen Sie in der Sitemap der Modell gesteuerten APP **Aktivitäten**aus.

2. Wählen Sie in der Befehlsleiste **e-Mail**aus. Ein neues e-Mail-Fenster wird geöffnet.

    ![e-Mail erstellen](media/create-email.png "Neue e-Mail-Adresse erstellen")

    Das Feld **from** wird automatisch basierend auf dem aktuell angemeldeten Benutzer ausgefüllt.

3. Schreiben Sie Ihre e-Mail direkt in den Composer, oder wählen Sie **Vorlage einfügen** aus, um nach einer Vorlage zu suchen und diese anzuwenden. Weitere Informationen zum Einfügen einer e-Mail-Vorlage finden Sie unter [Einfügen einer e-Mail-Vorlage](insert-email-template.md).

4. Wählen Sie zum Verfassen Ihrer e-Mail in einem voll Bildfenster das Erweiterungs Symbol aus.

    ![e-Mail-erweitern-Fenster](media/email-expand-window.png "Fenster "e-Mail" erweitern")

    Das Meldungs Feld enthält einen Rich-Text-Editor, mit dem Sie umfangreiche und gut formatierte Inhalte für die e-Mails mit Betonung erstellen können. Der-Editor bietet allgemeine Textverarbeitungsfunktionen wie die folgenden: 

    - Kopier Formatierung
    - Schriftart und Größe
    - Fett, kursiv und unterstrichen
    - Hintergrundfarbe für Text und Textfarbe
    - Aufzählige und nummerierte Liste
    - Einzug verkleinern und vergrößern
    - Anführungszeichen
    - Text Ausrichtung (ausrichten Links, zentriert und rechts)
    - Verknüpfung und Verknüpfung aufheben
    - Text durchgestrichen
    - Bild
    - Text Richtung von rechts nach links und von links nach rechts
    - Rückgängig und wiederholen
    - Format entfernen
    - Table

    ![e-Mail-Symbolleiste](media/email-toolbar.png "Verwenden der Rich-Text-Editor-Funktionen")

5. Wenn Sie fertig sind, wählen Sie **senden**aus.


### <a name="see-also"></a>Siehe auch

[Erweiterte e-Mail einrichten](https://docs.microsoft.com/power-platform/admin/system-settings-dialog-box-email-tab)<br>
[E-Mail-Vorlage einfügen](insert-email-template.md)
