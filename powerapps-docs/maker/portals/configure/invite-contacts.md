---
title: Einladen von Kontakten zum Portal | MicrosoftDocs
description: Anweisungen zum Erstellen und Konfigurieren von Einladungen in einem Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 631f17d9764fbfc209fd193ddabe4882f8ad8042
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73552219"
---
# <a name="invite-contacts-to-your-portals"></a>Kontakte zu Ihren Portalen einladen

Verwenden Sie die Einladungs Funktion von Portalen, um Kontakte zu Ihrem Portal über automatisierte, in ihrer Common Data Service erstellte e-Mails einzuladen. Die Personen, die Sie einladen, erhalten eine e-Mail, die von Ihnen vollständig anpassbar ist, mit einem Link zu Ihrem Portal und einem Einladungscode. Dieser Code kann verwendet werden, um speziellen, von Ihnen konfigurierten Zugriff zu erhalten. Mit dieser Funktion haben Sie folgende Möglichkeiten:

- Einladungen zu einer einzelnen oder einer Gruppe senden
-   Angeben eines Ablaufdatums, falls gewünscht
-   Geben Sie bei Bedarf einen Benutzer-oder Portal Kontakt als einladenden Benutzer an.
-   Beim Einlösen der Einladung den eingeladenen Kontakt (e) automatisch einem Konto zuweisen
-   Workflow beim Einlösen der Einladung automatisch ausführen
-   Der eingeladenen Kontakt (e) automatisch einer webrolle beim Einlösen zuweisen

Die Einlösung der Einladung kann mit einer unserer vielen Authentifizierungs Optionen durchgeführt werden. Eine Dokumentation zur Portal Authentifizierung finden Sie unter [Festlegen der Authentifizierungs Identität für ein Portal](set-authentication-identity.md) und auswählen des Modells, das für Ihre Portal Version und-Konfiguration gilt. Der Benutzer übernimmt beim Einlösen alle vom Administrator bereitgestellten Einstellungen. Für die Einladung und den Kontakt wird eine einlösungs Aktivität zum einladen erstellt.

Einladungen werden über den Workflow zum **Senden einer Einladung** gesendet. Standardmäßig erstellt der Workflow eine e-Mail mit einer generischen Nachricht und sendet Sie an die primäre e-Mail-Adresse des eingeladenen Kontakts. Der Workflow zum **Senden einer Einladung** enthält eine e-Mail-Vorlage, die bearbeitet werden muss, damit Sie eine bestimmte Nachricht für das Portal und den korrekten Hyperlink zur Seite für die Einladung zum **einlösen**Ihres Portals enthält.

Zum Bearbeiten der e-Mail-Vorlage zum **Senden eines Einladungs** Workflows suchen Sie diese, und deaktivieren Sie Sie. Nachdem Sie deaktiviert wurde, bearbeiten Sie die e-Mail-Vorlage, um die gewünschte Nachricht zu senden, und geben Sie einen Link zur **Seite Einlösen der Einladung** Ihres Portals ein.

> [!NOTE]
> Die Einladung wird nur an die primäre e-Mail-Adresse (EmailAddress1) des Kontakts gesendet. Die Einladung wird nicht an die sekundäre e-Mail (EmailAddress2) oder an eine Alternative e-Mail-Adresse (EmailAddress3) des Kontaktdaten Satzes gesendet.

## <a name="create-invitations-from-portal-management-app"></a>Einladungen aus der Portal Verwaltungs-app erstellen

1.  Öffnen Sie die [Portal Verwaltungs-App](configure-portal.md).

2.  Wechseln Sie zu **Portale** > **Kontakte**.
    Alternativ dazu können Sie auch die Seite **Kontakte** über den Bereich [Freigabe](../manage-existing-portals.md#share) öffnen. 

3.  Wählen Sie einen Kontakt aus, oder öffnen Sie den Kontaktdaten Satz, der eingeladen wird.

4.  Wählen Sie in der Befehlsleiste die Option **Einladung erstellen**aus.

5.  Geben Sie auf der Seite **Einladung** entsprechende Werte in die Felder ein. Weitere Informationen: [Einladungs Attribute](#invitation-attributes)

6.  Wählen Sie **Speichern**.

7.  Wählen Sie in der Befehlsleiste **Flow** > **Einladung senden**aus.

    > [!div class="mx-imgBorder"]
    > ![Einladungs Workflow senden](../media/send-invitation-portal-app.png "Einladungs Workflow senden")

8.  Wählen Sie im Bestätigungsfenster die Option **OK**aus. Die Einladung wird an den ausgewählten Kontakt gesendet.

    > [!div class="mx-imgBorder"]
    > ![Bestätigung für das Senden einer Einladung](../media/confirm-invitation-portal-app.png "Bestätigung für das Senden einer Einladung")

### <a name="send-multiple-invitations"></a>Senden mehrerer Einladungen

Sie können Einladungen für Ihre Kontakte erstellen und dann alle Einladungen gleichzeitig senden.

1.  Erstellen Sie Einladungen für die erforderlichen Kontakte, und wechseln Sie dann zu **Portale** > **Einladungen**.

2.  Wählen Sie die erstellten Einladungen aus.

3.  Wählen Sie in der Befehlsleiste **Flow** > **Einladung senden**aus.

    > [!div class="mx-imgBorder"]
    > ![Einladungs Workflow senden](../media/send-invitation-portal-app.png "Einladungs Workflow senden")

4.  Wählen Sie im Bestätigungsfenster die Option **OK**aus. Die Einladungen werden an die ausgewählten Kontakte gesendet.

    > [!div class="mx-imgBorder"]
    > ![Bestätigung zum Senden mehrerer Einladungen](../media/confirm-multiple-invites-portal-app.png "Bestätigung zum Senden mehrerer Einladungen")

## <a name="invitation-attributes"></a>Einladungs Attribute

In der folgenden Tabelle werden die Attribute der **Einladungs** Seite erläutert:


|  Name    |    Beschreibung    |
|-------|------------|
|                 Name                  |                                                                                                      Ein beschreibender Name, um die Einladung zu erkennen.                                                                                                      |
|                 Typ                  |                                             **Ein** -oder- **Gruppe**. Single ermöglicht nur die Einladung eines Kontakts und nur eine Einlösung. Die Gruppe ermöglicht das einladen mehrerer Kontakte und mehrere einlöseungen.                                              |
|             Besitzer/Absender              | Der Benutzer, der der Absender der e-Mail ist, wenn die Einladung gesendet wird. Dies kann im **Sende Einladungs** Workflow überschrieben werden, wenn die erstellte e-Mail bereits eine Person im Feld from enthält. |
|            Einladungs Code            |                                                                 Ein eindeutiger Code für die Einladung, den nur der einladende Empfänger kennt. Diese wird automatisch generiert, wenn eine neue Einladung erstellt wird.                                                                  |
|              Ablaufdatum              |                                                                                     Das Datum, das angibt, wann die Einladung für die Einlösung ungültig wird. Optional.                                                                                     |
|                Einladender                |                                                                                               Kann verwendet werden, wenn ein Kontakt der Absender der Einladung ist. Optional.                                                                                                |
|          Eingeladene Kontakt (e)           |                                                                                                             Der Kontakt (e), der in ein Portal geladen werden soll.                                                                                                              |
|           Zu Konto zuweisen           |                                                                        Ein Kontodaten Satz, der als der übergeordnete Kunde des einlösen Kontakts verknüpft werden soll, wenn die Einladung eingelöst wird. Optional.                                                                        |
| Workflow beim Einlösen des Kontakts ausführen |                                                         Ein Workflow Prozess, der ausgeführt werden soll, wenn die Einladung eingelöst wird. Dem Workflow wird der einlösende Kontakt als primäre Entität übermittelt. Optional.                                                          |
|          Webrollen zuweisen          |                                                                               Ein Satz von Webrollen, die dem Einlösen von Kontakten beim Einlösen der Einladung zugeordnet werden sollen. Optional.                                                                                |
|          Eingelöste Kontakt (e)          |                                                                                                   Der Kontakt (e), der die Einladung erfolgreich eingelöst hat.                                                                                                   |
|      Maximal zulässige einlösen      |                                                                                   Gibt an, wie oft die Einladung eingelöst werden kann. Nur für Gruppentyp Einladungen verfügbar.                                                                                   |
|                                       |                                                                                                                                                                                                                                                                    |

### <a name="see-also"></a>Siehe auch

[Konfigurieren eines Kontakts für die Verwendung in einem Portal](configure-contacts.md)  
[Festlegen der Authentifizierungs Identität für ein Portal](set-authentication-identity.md)  
