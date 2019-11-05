---
title: Konfigurieren eines Kontakts für die Verwendung in einem Portal | MicrosoftDocs
description: Anweisungen zum Hinzufügen und Konfigurieren eines Kontakts, der in einem Portal verwendet werden soll.
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
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553185"
---
# <a name="configure-a-contact-for-use-on-a-portal"></a>Konfigurieren eines Kontakts für die Verwendung in einem Portal

Nachdem Sie die grundlegenden Informationen für einen Kontakt ausgefüllt haben (oder wenn ein Benutzer das Registrierungsformular in einem Portal ausgefüllt hat), wechseln Sie im Kontaktformular des Portals zur Registerkarte "Webauthentifizierung", um einen Kontakt mithilfe der lokalen Authentifizierung zu konfigurieren. Weitere Informationen zu den Optionen für die Verbund Authentifizierung finden Sie unter [Festlegen der Authentifizierungs Identität für ein Portal](set-authentication-identity.md). Befolgen Sie die folgenden Anweisungen, um einen Kontakt für Portale mithilfe der lokalen Authentifizierung zu konfigurieren:  

1.  Geben Sie einen **Benutzernamen**ein.
2.  Navigieren Sie im Befehls Menüband zu **Weitere Befehle** &gt; **Kennwort ändern**.

Vervollständigen Sie den Workflow zum Ändern des Kennworts, und die erforderlichen Felder werden automatisch konfiguriert. Wenn Sie diesen Vorgang abgeschlossen haben, wird Ihr Kontakt für ihre Portale konfiguriert.

## <a name="change-password-for-a-contact-from-portal-management-app"></a>Kennwort für einen Kontakt aus der Portal Verwaltungs-App ändern

1.  Öffnen Sie die [Portal Verwaltungs-App](configure-portal.md).

2.  Wechseln Sie zu **Portale** > **Kontakte**, und öffnen Sie den Kontakt, für den Sie das Kennwort ändern möchten.
    Alternativ dazu können Sie auch die Seite **Kontakte** über den Bereich [Freigabe](../manage-existing-portals.md#share) öffnen. 

3.  Wählen Sie auf der Symbolleiste oben den **Task Ablauf** aus.

    > [!div class="mx-imgBorder"]
    > ![Task Fluss (Symbol)](../media/task-flow.png "Task Fluss (Symbol)")

4.  Wählen Sie den Task Ablauf **Kennwort für den Portal Kontakt ändern aus** .

5.  Wählen Sie im Bereich **Kennwort für Portal Kontakt ändern aus** , oder erstellen Sie einen Kontakt, um das Kennwort zu ändern, und klicken Sie dann auf **weiter**.

    > [!div class="mx-imgBorder"]
    > ![Wählen Sie einen Kontakt, um das Kennwort zu ändern.](../media/change-password-select-contact.png "Wählen Sie einen Kontakt, um das Kennwort zu ändern.")

6.  Geben Sie im Feld **Neues Kennwort** ein neues Kennwort ein, und klicken Sie dann auf **weiter**.

    > [!div class="mx-imgBorder"]
    > ![Neues Kennwort für den Kontakt eingeben](../media/change-password-new-password.png "Neues Kennwort für den Kontakt eingeben")

    Wenn Sie kein Kennwort eingeben und **weiter**auswählen, werden Sie gefragt, ob Sie das Kennwort für den ausgewählten Kontakt entfernen möchten.

    > [!div class="mx-imgBorder"]
    > ![Kennwort für den Kontakt entfernen](../media/change-password-remove-password.png "Kennwort für den Kontakt entfernen")

7.  Nachdem Sie die Änderungen vorgenommen haben, wählen Sie **abgeschlossen**aus.


### <a name="see-also"></a>Siehe auch
[Kontakte zu Ihren Portalen einladen](invite-contacts.md)  
[Festlegen der Authentifizierungs Identität für ein Portal](set-authentication-identity.md)  