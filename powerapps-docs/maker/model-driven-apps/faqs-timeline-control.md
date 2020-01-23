---
title: FAQs für Zeitskala-Steuerelement (Abschnitt) in Power Apps | Microsoft-Dokumentation
description: FAQs für Zeitskala-Steuerelement (Abschnitt) in Power Apps
ms.date: 12/23/2019
ms.service: powerapps
author: kabala123
ms.assetid: 7F495EE1-1208-49DA-9B02-17855CEB2FDF
ms.author: kabala
manager: shujoshi
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4851f4e5dc173f8861db0ba0b761e01f2537b0e8
ms.sourcegitcommit: 8ba5f6b88dbd71eb3663dfeec5f0b4427c1543c0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/27/2019
ms.locfileid: "2924402"
---
# <a name="faqs-for-timeline-control"></a>FAQs für Zeitskala-Steuerelement

## <a name="why-do-i-receive-the-message-records-could-not-be-loaded-because-of-unexpected-error"></a>Warum erhalte ich die Meldung „Datensätze konnten aufgrund eines unerwarteten Fehlers nicht geladen werden“?

Der Abschnitt **Zeitskala** ruft Daten darüber ab, und zeigt sie in den Formularkarten an. Standardmäßig ruft die Zeitskala Daten für die 10 Standardaktivitätsentitäten ab. Diese sind:

-   E-Mail
-   Aufgabe
-   Vorfalllösung
-   Fax
-   Verkaufschancenabschluss
-   Brief
-   Termin
-   Telefonanruf

Wenn Sie die folgenden Prozeduren als Administrator ausführen, wird Benutzern zur Laufzeit ein Fehler angezeigt:

**Vorgehensweise**
-   Sämtliche zusätzliche benutzerdefinierte Aktivitäten erstellen
-   Benutzerdefinierte Aktivitäten für Handy aktivieren
-   Ein **Kartenformular** für alle benutzerdefinierten Aktivitäten auswählen 

**Fehler:** Datensätze konnten aufgrund eines unerwarteten Fehlers nicht geladen werden.

   > [!div class=mx-imgBorder] 
   > ![Datensätze konnten aufgrund eines unerwarteten Fehlers nicht geladen werden.](media/timeline-error1.png "Datensätze konnten aufgrund eines unerwarteten Fehlers nicht geladen werden.")

Dieser Fehler wird dadurch verursacht, dass die Anzahl der Aktivitätsentitäten für den Datenabruf das maximale Limit von 10 überschritten hat.

   > [!div class=mx-imgBorder] 
   > ![Die Anzahl der Linkentitäten in der Abfrage hat den Höchstwert überschritten](media/timeline-error2.png "[Die Anzahl der Linkentitäten in der Abfrage hat den Höchstwert überschritten")

### <a name="workaround"></a>Problemumgehung

Um das Problem zu umgehen, müssen Sie die Anzahl der Entitäten auf 10 oder weniger reduzieren. Führen Sie dazu die Schritte unten aus.

1.  Melden Sie sich in Ihrer `https://<YourOrgURL>.dynamics.com/apps`-Umgebung an.

2.  Öffnen Sie eine modellgesteuerte App und wählen Sie dann in der Befehlsleiste **Einstellungen** ![Einstellungen](../model-driven-apps/media/powerapps-gear.png) > **Erweiterte Einstellungen** aus.

3.  Gehen Sie zu **Einstellungen** > **Anpassung** > **System anpassen**. Die Seite „Projektmappen-Explorer“ wird in einem neuen Browserfenster geöffnet.

4.  Erweitern Sie **Entitäten** unter **Komponenten** im Standardlösungsbereich.

5.  Wählen Sie eine Entität, und wählen Sie **Formulare** aus. Wählen Sie beispielsweise die Entität **Konto** aus.

6.  Wählen Sie den Datensatz **Konto für interaktive Funktionen** aus, der ein **Haupt**-Formulartyp ist. Das Formular **Konto für Interaktive Funktionen** wird in einem neuen Browserfenster geöffnet.

   > [!div class=mx-imgBorder] 
   > ![Wählen Sie das Entitätsformular mit interaktiven Funktionen im Namen aus](media/account-interactive-experience.png "Wählen Sie das Entitätsformular mit interaktiven Funktionen im Namen aus")

   Für Einheitliche Oberfläche müssen Sie den Formularnamen verwenden, der `<Entity> for Interactive experience` enthält.

7.  Doppelklicken Sie auf das Feld **Unterhaltungsregisterkarten** im Abschnitt **Zeitskala**. Der Dialog **Eigenschaften der Registerkarte „Aktivitäten“** wird angezeigt.

    > [!div class=mx-imgBorder] 
    > ![Machen Sie einen Doppelklick auf das Feld im Social Media-Bereich](media/timeline-conversation-tabs-field.png "Machen Sie einen Doppelklick auf das Feld im Social Media-Bereich")  

8.  Wählen Sie die Option **Ausgewählte anzeigen** für das Feld **Diese Aktivitäten anzeigen** im Container **Filtern nach** aus.

9.  Wählen Sie die Aktivitäten aus, die Sie den Benutzern anzeigen möchten.

10. Wählen Sie **OK** aus und dann **Speichern**.

11. Wählen Sie **Veröffentlichen** aus, um die Anpassungen zu veröffentlichen.


## <a name="why-i-cant-assign-or-delete-an-activity-from-the-timeline"></a>Warum kann ich keine Aktivität aus der Zeitskala zuweisen oder löschen?

Wenn Sie die Regel **HideCustomActions** zum Ausblenden von Schaltflächen in der Menüband-Befehlsleistendefinition verwenden, wie z. B. **Zuweisen** und **Löschen**, dann funktionieren jene Schaltflächen nicht, die sich im Zeitskala-Steuerelement befinden. Die Schaltflächen in der Befehlsleiste entsprechen den Schaltflächen im Zeitskala-Steuerelement. Wenn daher ein Benutzer die Schaltfläche **Zuweisen** oder **Löschen** im Zeitskala-Steuerelement auswählt, wird eine Fehlermeldung angezeigt.

**Sie verfügen über keine Berechtigung zum Ausführen dieser Aktion. Wenden Sie sich an den Systemadministrator.**

Blenden Sie die Schaltflächen in den Befehlsleistendefinitionen ein, um das Problem zu beheben.

## <a name="see-also"></a>Siehe auch

[Zeitskala Steuerelement einrichten](set-up-timeline-control.md)

[Zeitskala-Abschnitt in der Kunderservicehub-App](https://docs.microsoft.com/dynamics365/customer-service/customer-service-hub-user-guide-basics#timeline)

[Einen termin, E-Mail, Telefonanruf, Notiz oder Aufgabenaktivität zur Zeitskala hinzufügen](../../user/add-activities.md)
