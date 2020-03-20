---
title: Anzeigen und Erstellen von E-Mails in modellgesteuerten Apps | Microsoft-Dokumentation
description: Anzeigen und Erstellen von E-Mails bei Verwendung einer modellgesteuerten App.
ms.date: 02/03/2020
ms.service:
- dynamics-365
ms.topic: article
author: lalexms
ms.author: lalexms
manager: shujoshi
ms.openlocfilehash: 7d4930b03f175133a769226a407436d37f698633
ms.sourcegitcommit: 3066c2800a939fbcaaac4262c802843e2d80b88c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431737"
---
# <a name="preview-view-and-create-email-through-the-activities-grid"></a>Vorschauversion: Anzeigen und Erstellen von E-Mails über das Aktivitätsraster

Das Anzeigen und Erstellen von E-Mails über das Aktivitätsraster ist ein Early-Access-Feature. Sie können diese Features frühzeitig in Ihrer Umgebung aktivieren. So können Sie diese testen und dann in Ihre Umgebungen einführen. Weitere Informationen zur Aktivierung dieser Features finden Sie unter [Aktivieren von Early-Access-Updates](https://docs.microsoft.com/power-platform/admin/opt-in-early-access-updates).

Mit den modellgesteuerten Dynamics 365-Apps können Sie per E-Mail mit Kunden interagieren. Die E-Mail-Funktionalität bietet Ihnen folgende Möglichkeiten:

- Anzeigen und Reagieren auf E-Mails 

- Nutzen der allgemeinen E-Mail-Symbolleistenfunktionen und der Steuerelemente des Rich-Text-Editors 

- Anzeigen und Einfügen von Bildern inline mithilfe von Drag & Drop oder Kopieren und Einfügen. 

- Erstellen von E-Mails in einem Popupfenster  

- Vorschau von Vorlagen vor der Anwendung 



## <a name="view-your-email"></a>Anzeigen Ihrer E-Mail

Zum Anzeigen Ihrer E-Mail:

1. Wählen Sie in der Sitemap der modellgesteuerten App **Aktivitäten** aus. 

2. Wählen Sie die Dropdownliste **Alle Aktivitäten** aus, und wählen Sie dann **Meine eingegangenen E-Mails** aus.

    ![view-email](media/view-email.png "Empfangene E-Mails anzeigen")

3. Wählen Sie die E-Mail aus, die Sie anzeigen möchten, um sie zu öffnen. Die E-Mail wird geöffnet. Anschließend können Sie dem Absender oder den Empfängern antworten oder die E-Mail weiterleiten.

## <a name="create-email"></a>E-Mail erstellen

In den folgenden Schritten wird beschrieben, wie Sie eine E-Mail erstellen.

1. Wählen Sie in der Sitemap der modellgesteuerten App **Aktivitäten** aus.

2. Wählen Sie in der Befehlsleiste **E-Mail** aus. Daraufhin wird ein neues E-Mail-Fenster geöffnet.

    ![create-email](media/create-email.png "Neue E-Mail erstellen")

    Das Feld **Von** wird basierend auf dem aktuell angemeldeten Benutzer automatisch ausgefüllt.

3. Sie können entweder direkt eine E-Mail schreiben oder **Vorlage einfügen** auswählen, um nach einer Vorlage zu suchen und sie anzuwenden. Weitere Informationen zum Einfügen einer E-Mail-Vorlage finden Sie unter [Vorschauversion: Hinzufügen einer E-Mail-Vorlage](insert-email-template.md).

4. Wählen Sie zum Verfassen Ihrer E-Mail in einem Vollbildfenster das Erweiterungssymbol aus.

    ![email-expand-window](media/email-expand-window.png "E-Mail-Fenster erweitern")

    Das Nachrichtenfeld enthält einen Rich-Text-Editor, mit dem Sie umfangreiche und gut formatierte Inhalte für wichtige E-Mails erstellen können. Der Editor bietet allgemeine Textverarbeitungsfunktionen wie zum Beispiel: 

    - Kopieren der Formatierung
    - Schriftart und -größe
    - Fett, kursiv und unterstrichen
    - Hintergrundfarbe für Text und Textfarbe
    - Aufzählungen und nummerierte Listen
    - Verkleinern und Vergrößern des Einzugs
    - Blockzitat
    - Textausrichtung (links, zentriert und rechts)
    - Verknüpfen und Verknüpfungen aufheben
    - Durchgestrichener Text
    - Bild
    - Textrichtung von rechts nach links und von links nach rechts
    - Rückgängig machen und Wiederholen
    - Format entfernen
    - Tabelle

    ![email-toolbar](media/email-toolbar.png "Verwenden der Rich-Text-Editor-Funktionen")

5. Wählen Sie abschließend **Senden** aus.


### <a name="see-also"></a>Siehe auch

[Einrichten von erweiterten E-Mail-Funktionen](https://docs.microsoft.com/power-platform/admin/system-settings-dialog-box-email-tab)<br>
[Hinzufügen einer E-Mail-Vorlage](insert-email-template.md)
