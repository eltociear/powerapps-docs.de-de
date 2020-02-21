---
title: Anzeigen der Profilkarte für einen Kontakt oder Benutzer | Microsoft-Dokumentation
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/03/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 276c7d3cbf95947306fab768da8af3c4c66b33e0
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543371"
---
# <a name="view-the-profile-card-for-a-contact-or-user"></a>Anzeigen der Profilkarte für einen Kontakt oder Benutzer

Verwenden Sie die Profilkarte, um schnell Informationen zu einem Kontakt oder Benutzer zu erhalten. Wenn Sie ein Kontakt- oder Benutzerfeld in modellgesteuerten Apps in Dynamics 365 (wie z. B. Dynamics 365 Sales und Dynamics 365 Customer Service) auswählen, finden Sie entsprechende Informationen auf der zugehörigen Profilkarte. Weitere Informationen zu Profilkarten finden Sie unter [Profilkarten in Office 365](https://support.office.com/article/Profile-cards-in-Office-365-e80f931f-5fc4-4a59-ba6e-c1e35a85b501).

> [!NOTE]
>  - Eine Profilkarte ist für die Entitäten **Kontakt** und **Benutzer** verfügbar. Weitere Informationen finden Sie unter [Aktivieren der Anzeige von Profilkarten](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-profile-card).
>  - Die Profilkarte in Common Data Service wird nicht angezeigt, wenn die mehrstufige Authentifizierung für den Office Delve-Dienst in Azure Active Directory aktiviert ist.

## <a name="view-a-contacts-profile"></a>Anzeigen des Profils eines Kontakts

1.  Wechseln Sie zu **Aktivitäten**.
2.  Wählen Sie eine vorhandene Aktivität aus, oder erstellen Sie eine neue.
3.  Zeigen Sie mit dem Mauszeiger auf das Feld **Anrufen**, wenn ein Kontaktdatensatz vorhanden ist. 

So können Sie inline die Details des Kontakts anzeigen, wie u. a. Bild, Name, Titel und Konto des Kontakts.

4. Wenn Sie weitere Details anzeigen möchten, wählen Sie **Mehr anzeigen** aus, um das Profil des Kontakts zu erweitern.
 
    > [!div class="mx-imgBorder"] 
    > ![Erweitern der Details zur Kontaktprofilkarte](media/profile1.png "Erweitern der Details zur Kontaktprofilkarte")
   
 ## <a name="view-a-users-profile"></a>Anzeigen eines Benutzerprofils
 
1.  Wechseln Sie zu **Konten**.
2.  Wählen Sie einen Kontodatensatz aus.
3.  Zeigen Sie auf das Feld „Besitzer“, wenn es einen Benutzerdatensatz enthält. Sie können die Details des Benutzers inline anzeigen.
4.  Wenn Sie weitere Details wie E-Mails und für den Benutzer freigegebene Dateien anzeigen möchten, wählen Sie **Mehr anzeigen** aus, um das Profil des Kontakts zu erweitern.
 
    > [!div class="mx-imgBorder"] 
    > ![Erweitern der Details zur Benutzerprofilkarte](media/profile2.png "Erweitern der Details zur Benutzerprofilkarte")


 ## <a name="faqs"></a>Häufig gestellte Fragen
 
### <a name="where-can-i-see-profile-cards-in-dynamics-365"></a>Wo sehe ich Profilkarten in Dynamics 365?
Profilkarten werden in Kontakt- und Benutzerdatensätzen angezeigt. Sie können sie nur anzeigen, wenn sie sich in einer Suche befinden.

### <a name="where-is-information-shown-in-the-profile-card-coming-from"></a>Woher stammen die Informationen, die in der Profilkarte angezeigt werden?
Die Informationen, die auf der Kontaktprofilkarte angezeigt werden, werden von Common Data Service abgerufen (und nicht von Microsoft Exchange). Das heißt, dass die Kontaktinformationen von Dynamics 365 stammen.

Die Informationen, die auf der Benutzerprofilkarte angezeigt werden, werden aus Office 365 (Azure Active Directory) abgerufen. Weitere Informationen finden Sie unter [Profilkarten in Office 365 (Abschnitt für Administratoren)](https://support.office.com/article/Profile-cards-in-Office-365-e80f931f-5fc4-4a59-ba6e-c1e35a85b501).

### <a name="how-can-i-customize-the-fields-shown-on-the-profile-card"></a>Wie kann ich die Felder anpassen, die auf der Profilkarte angezeigt werden?
Die Liste der Felder, die auf der Profilkarte angezeigt werden, kann derzeit nicht bearbeitet werden.

### <a name="why-is-the-start-chat-option-on-the-profile-card-disabled-greyed-out"></a>Warum ist die Option **Chat starten** auf der Profilkarte deaktiviert (abgeblendet)?
Die Optionen **Chat starten** und **E-Mail senden** auf der Profilkarte öffnen Ihre Standard-Apps für Chatnachrichten und E-Mails. Die Option **Chat starten** ist aktiviert, wenn sich die Person, die Sie kontaktieren möchten, in derselben Azure Active Directory-Umgebung befindet wie Sie oder ein Verbundkontakt.


  
