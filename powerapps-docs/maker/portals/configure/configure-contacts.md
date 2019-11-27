---
title: Konfigurieren eines Kontakts zur Verwendung auf einem Portal | MicrosoftDocs
description: Anleitungen zum Hinzufügen und Konfigurieren eines Kontakts in einem Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 4a8c70304385007c132f2c13ec0ddca4b68e2231
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2760456"
---
# <a name="configure-a-contact-for-use-on-a-portal"></a>Konfigurieren eines Kontakts zur Verwendung auf einem Portal

Nachdem Sie die grundlegenden Informationen für einen Kontakt in ausgefüllt haben (oder einen Benutzer das Anmeldeformular in einem Portal ausfüllen lassen), müssen Sie zur Registerkarte „Webauthentifizierung” des Kontaktformulars im Portal navigieren, um einen Kontakt mithilfe lokaler Authentifizierung zu konfigurieren. Weitere Informationen zu Verbund-Authentifizierungsoptionen finden Sie in [Festlegen der Authentifizierungsidentität für ein Portal](set-authentication-identity.md). Wenn Sie einen Kontakt für Portale unter Verwendung der lokalen Authentifizierung konfigurieren, folgen Sie den folgenden Anweisungen:  

1.  Geben Sie einen **Benutzernamen** ein.
2.  Klicken Sie im Befehlsmenüband auf **Weitere Befehle** &gt; **Kennwort ändern**.

Schließen Sie den Workflow zum Ändern des Kennworts ab, und die gewünschten Felder werden automatisch konfiguriert. Anschließend wird der Kontakt für Ihre Portale konfiguriert.

## <a name="change-password-for-a-contact-from-portal-management-app"></a>Ändern Sie das Kennwort für einen Kontakt der Portalverwaltungs-App

1.  Öffnen Sie die [Portalverwaltungs-App](configure-portal.md).

2.  Gehen Sie zu **Portale** > **Kontakte** und öffnen Sie den Kontakt, für den Sie das Kennwort ändern möchten.
    Als Alternative können Sie auch die Seite **Kontakte** des Bereichs [Freigeben](../manage-existing-portals.md#share) öffnen. 

3.  Wählen Sie auf der Symbolleiste **Aufgabenfluss** oben.

    > [!div class="mx-imgBorder"]
    > ![Aufgabenfluss-Symbol](../media/task-flow.png "Aufgabenfluss-Symbol")

4.  Verwenden Sie diesen Aufgabenfluss **Kennwort für einen Portalkontakt ändern**.

5.  Wählen Sie im Bereich **Passwort für Portalkontakt ändern** einen Kontakt auswählen oder erstellen aus, um das Passwort zu ändern und wählen Sie **Weiter** aus.

    > [!div class="mx-imgBorder"]
    > ![Wählen Sie einen Kontakt aus, um das Kennwort zu ändern](../media/change-password-select-contact.png "Wählen Sie einen Kontakt aus, um das Kennwort zu ändern")

6.  Im Feld **Neues Kennwort** geben Sie ein neues Kennwort ein, und wählen Sie dann **Weiter** aus.

    > [!div class="mx-imgBorder"]
    > ![Geben Sie ein neues Kennwort für den Kontakt ein](../media/change-password-new-password.png "Geben Sie ein neues Kennwort für den Kontakt ein")

    Wenn Sie kein Kennwort eingeben wählen Sie **Weiter**. Sie werden gefragt, ob Sie einen ausgewählten Kontakt entfernen möchten.

    > [!div class="mx-imgBorder"]
    > ![Entfernen Sie das Kennwort für den Kontakt](../media/change-password-remove-password.png "Entfernen Sie das Kennwort für den Kontakt")

7.  Nachdem die Änderungen vorgenommen wurden, wählen Sie **Fertig**.


### <a name="see-also"></a>Siehe auch
[Einladen von Kontakten zu Ihren Portalen](invite-contacts.md)  
[Festlegen der Authentifizierungsidentität für ein Portal](set-authentication-identity.md)  