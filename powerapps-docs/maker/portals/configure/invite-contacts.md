---
title: Kontakte in Ihr Portal einladen | MicrosoftDocs
description: Anweisungen zum Erstellen und Konfigurieren von Einladungen in einem Portal.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 03/16/2020
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: f6e6989e1005f12fd3e9d3a02222a8cd95226cca
ms.sourcegitcommit: cf492063eca27fdf73459ff2f9134f2ca04ee766
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "3136219"
---
# <a name="invite-contacts-to-your-portals"></a>Laden Sie Kontakte für Ihre Portale ein

Mit der Portaleinladungsfunktion haben Sie die Möglichkeit, Kontakte durch automatische E-Mails zu Ihrem Portal einzuladen, die in Common Data Service erstellt wurden. Eingeladene Personen erhalten eine E-Mail, vollständig anpassbar durch Sie, mit einem Link zum Portal und einem Einladungscode. Dieser Code kann verwendet werden, um bestimmten Zugriff zu erhalten, der von Ihnen konfiguriert ist. Mit diesem Feature haben Sie folgende Möglichkeiten:

- Senden von Einzel- oder Gruppen-Einladungen
-   Angeben eines Ablaufdatums (falls gewünscht)
-   Angeben eines Benutzer- oder Portalkontakts als Einladender (falls gewünscht)
-   Automatisches Zuweisen eingeladener Kontakte zu einer Firma bei Einlösung der Einladung
-   Automatisches Ausführen eines Workflows bei Einlösung der Einladung
-   Automatisches Zuweisen eingeladener Kontakte zu einer Webrolle bei Einlösung der Einladung

Die Einladungseinlösung kann mithilfe unserer vielen Authentifizierungsoptionen erreicht werden. Die Dokumentation zur Portalauthentifizierung finden Sie unter [Authentifizierungsidentität für ein Portal festlegen](set-authentication-identity.md), wo Sie das Modell entsprechend Ihrer Portalversion und -konfiguration auswählen können. Der Benutzer übernimmt die Einstellungen, die vom Administrator bei Einlösung bereitgestellt werden. Eine Einladungseinlösungs-Aktivität wird für die Einladung und den Kontakt erstellt.

Einladungen werden über den **Einladung senden**-Workflow gesendet. Standardmäßig erstellt der Workflow eine E-Mail mit einer allgemeinen Nachricht und sendet diese an die primäre E-Mail-Adresse des eingeladenen Kontakts. Die E-Mail-Adressen in den Feldern CC und BCC werden ignoriert, um eine sichere Kommunikation zu gewährleisten. Der **Einladung senden**-Workflow enthält eine E-Mail-Vorlage, die bearbeitet werden muss, um eine bestimmte Nachricht für das Portal und den korrekten Link zur **Einladungseinlösungsseite** des Portals einzuschließen.

Um die **Einladung senden** Workflowe-E-Mail-Vorlage zu bearbeiten, suchen und deaktivieren Sie sie. Nach dem Deaktivieren können Sie die E-Mail-Vorlage bearbeiten, um die gewünschte Nachricht zu senden und einen Link zur **Einladungseinlösungsseite** des Portals bereitzustellen.

> [!NOTE]
> Diese Einladung wird nur an die primäre E-Mail (emailaddress1) des Kontakts gesendet. Die Einladung wird nicht an die sekundäre (emailaddress2) oder alternative E-Mail-Adresse (emailaddress3) des Kontaktdatensatzes gesendet.

## <a name="create-invitations-from-portal-management-app"></a>Erstellen von Einladungen in der Portalverwaltungs-App

1.  Öffnen Sie die [Portalverwaltungs-App](configure-portal.md).

2.  Gehen Sie zu **Portale** > **Kontakte**.
    Als Alternative können Sie auch die Seite **Kontakte** des Bereichs [Freigeben](../manage-existing-portals.md#share) öffnen. 

3.  Wählen Sie einen Kontakt aus oder öffnen den einzuladenden Kontaktdatensatz.

4.  Wählen Sie in der Befehlsleiste **Aus Einladung erstellen** aus.

5.  Auf der Seite **Einladung** können Sie die Werte in die Felder eingeben. Weitere Informationen [Einladungs-Attribute](#invitation-attributes)

6.  Wählen Sie **Speichern** aus.

7.  Wählen Sie in der Befehlsleiste **Fluss** > **Einladung senden** aus.

    > [!div class="mx-imgBorder"]
    > ![„Einladung senden“-Workflow](../media/send-invitation-portal-app.png "„Einladung senden“-Workflow")

8.  Wählen Sie im Bestätigungsfenster **OK** aus. Die Einladung wird an ausgewählte Kontakte gesendet.

    > [!div class="mx-imgBorder"]
    > ![Bestätigung, um Einladung zu senden](../media/confirm-invitation-portal-app.png "Bestätigung, um Einladung zu senden")

### <a name="send-multiple-invitations"></a>Mehrere Einladungen senden

Sie können die Einladungen für Kontakte erstellen und diesen anschließend sofort senden.

1.  Erstellen Sie Einladungen für die erforderlichen Kontakte und gehen Sie dann zu **Portale** > **Einladungen**.

2.  Wählen Sie die erstellten Einladungen aus.

3.  Wählen Sie in der Befehlsleiste **Fluss** > **Einladung senden** aus.

    > [!div class="mx-imgBorder"]
    > ![„Einladung senden“-Workflow](../media/send-invitation-portal-app.png "„Einladung senden“-Workflow")

4.  Wählen Sie im Bestätigungsfenster **OK** aus. Die Einladungen werden an ausgewählte Kontakte gesendet.

    > [!div class="mx-imgBorder"]
    > ![Bestätigung, um mehrere Einladungen zu senden](../media/confirm-multiple-invites-portal-app.png "Bestätigung, um mehrere Einladungen zu senden")

## <a name="invitation-attributes"></a>Einladungsattribute

In der folgenden Tabelle werden die Attribute der Seite **Einladung** erklärt:


|  Name    |    Beschreibung    |
|-------|------------|
|                 Name                  |                                                                                                      Ein beschreibender Name zur Erkennung der Einladung.                                                                                                      |
|                 Typ                  |                                             **Einzeln** oder **Gruppe**. "Einzeln" erlaubt nur einen einzuladenden Kontakt und nur eine Einlösung. "Gruppe" erlaubt mehrere einzuladende Kontakte und mehrere Einlösungen.                                              |
|             Besitzer/Absender              | Der Benutzer, der Sender der E-Mail ist, wenn die Einladung gesendet wird. Dies kann im **Einladung senden**-Workflow überschrieben werden, wenn die erstellte E-Mail bereits jemanden im "Von"-Feld enthält. |
|            Einladungscode            |                                                                 Ein eindeutiger Code für die Einladung, den nur der Eingeladene kennt. Dieser wird automatisch generiert, wenn Sie eine neue Einladung erstellen.                                                                  |
|              Ablaufdatum              |                                                                                     Das Datum, das anzeigt, wann die Einlösung der Einladung ungültig ist. (Optional).                                                                                     |
|                Einladende Person                |                                                                                               Kann verwendet werden, wenn ein Kontakt der Absender der Einladung ist. (Optional).                                                                                                |
|          Eingeladene(r) Kontakt(e)           |                                                                                                             Die zu einem Portal einzuladenden Kontakte.                                                                                                              |
|           Zuweisen an Firma           |                                                                        Ein Firmendatensatz, der als übergeordneter Kunde des einlösenden Kontakts zugeordnet werden soll, wenn die Einladung eingelöst wird. (Optional).                                                                        |
| Workflow für einlösenden Kontakt ausführen |                                                         Ein Workflowprozess, der ausgeführt werden soll, wenn die Einladung eingelöst wird. Dem Workflow wird der einlösende Kontakt als primäre Entität übergeben. (Optional).                                                          |
|          Zu Webrollen zuweisen          |                                                                               Ein Satz von Webrollen, die dem einlösenden Kontakt zugeordnet werden sollen, wenn die Einladung eingelöst wird. (Optional).                                                                                |
|          Eingelöst – Kontakt(e)          |                                                                                                   Die Kontakte, die die Einladung erfolgreich eingelöst haben.                                                                                                   |
|      Maximal zulässige Einlösungen      |                                                                                   Die Anzahl der möglichen Einlösungen der Einladung. Verfügbar nur für Gruppentypeinladungen.                                                                                   |
|                                       |                                                                                                                                                                                                                                                                    |

### <a name="see-also"></a>Siehe auch

[Konfigurieren eines Kontakts zur Verwendung auf einem Portal](configure-contacts.md)  
[Festlegen der Authentifizierungsidentität für ein Portal](set-authentication-identity.md)  
