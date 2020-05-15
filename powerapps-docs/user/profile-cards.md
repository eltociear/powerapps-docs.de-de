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
ms.locfileid: "3302608"
---
# <a name="view-the-profile-card-for-a-contact-or-user"></a>Anzeigen der Profilkarte für einen Kontakt oder Benutzer

Verwenden Sie die Profilkarte, um schnell Informationen zu einem Kontakt oder Benutzer zu erhalten. Wenn Sie ein Kontakt- oder Benutzerfeld in modellgesteuerten Apps in Dynamics 365 (wie z. B. Dynamics 365 Sales und Dynamics 365 Customer Service) auswählen, finden Sie entsprechende Informationen auf der zugehörigen Profilkarte. Weitere Informationen zu Profilkarten finden Sie unter [Profilkarten in Office 365](https://support.office.com/article/Profile-cards-in-Office-365-e80f931f-5fc4-4a59-ba6e-c1e35a85b501).

> [!NOTE]
>  - Eine Profilkarte ist für die Entitäten **Kontakt** und **Benutzer** verfügbar. Weitere Informationen finden Sie unter [Aktivieren der Anzeige von Profilkarten](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-profile-card).
>  - Die Profilkarte in Common Data Service wird nicht angezeigt, wenn die Multi-Faktor-Authentifizierung für den Office Delve-Dienst in Azure Active Directory aktiviert ist.

## <a name="view-a-contacts-profile"></a>Anzeigen des Profils eines Kontakts

1.  Gehen Sie zu **Aktivitäten**.
2.  Wählen Sie eine vorhandene Aktivität aus, oder erstellen Sie eine neue.
3.  Zeigen Sie mit der Maus auf das Feld **Anrufen**, wenn es einen Kontaktdatensatz hat. 

Sie können die Details des Kontakts inline angezeigt. Diese sind das Kontaktbild, der Name, die Position und die Firma.

4. Wählen Sie zum Anzeigen ausführlicherer Informationen **Mehr anzeigen**, um das Profil des Kontakts zu erweitern.
 
    > [!div class="mx-imgBorder"] 
    > ![Erweitern der Details zur Kontaktprofilkarte](media/profile1.png "Erweitern der Details zur Kontaktprofilkarte")
   
 ## <a name="view-a-users-profile"></a>Anzeigen eines Benutzerprofils
 
1.  Wechseln Sie zu **Konten**.
2.  Wählen Sie einen Kontodatensatz aus.
3.  Zeigen Sie auf das Feld „Besitzer“, wenn es einen Benutzerdatensatz enthält. Sie können die Details des Benutzers inline anzeigen.
4.  Wenn Sie weitere Details anzeigen möchten wie E-Mails und für den Benutzer freigegebene Dateien, wählen Sie **Mehr anzeigen**, um das Profil des Kontakts zu erweitern.
 
    > [!div class="mx-imgBorder"] 
    > ![Erweitern der Details zur Benutzerprofilkarte](media/profile2.png "Erweitern der Details zur Benutzerprofilkarte")


 ## <a name="faqs"></a>Häufig gestellte Fragen
 
### <a name="where-can-i-see-profile-cards-in-dynamics-365"></a>Wo sehe ich Profilkarten in Dynamics 365?
Profilkarten werden in Kontakt- und Benutzerdatensätzen angezeigt. Sie können sie nur anzeigen, wenn sie sich in einer Suche befinden.

### <a name="where-is-information-shown-in-the-profile-card-coming-from"></a>Woher stammen die Informationen in der Profilkarte?
Die auf der Kontaktprofilkarte angezeigten Informationen werden von Common Data Service (und nicht von Microsoft Exchange) abgerufen. Dies bedeutet, dass die Kontaktdetails aus Dynamics 365 kommen.

Die auf der Benutzerprofilkarte angezeigten Informationen werden von Office 365 (Azure Active Directory) abgerufen. Weitere Informationen finden Sie unter [Profilkarten in Office 365 (Admin-Bereich)](https://support.office.com/article/Profile-cards-in-Office-365-e80f931f-5fc4-4a59-ba6e-c1e35a85b501).

### <a name="how-can-i-customize-the-fields-shown-on-the-profile-card"></a>Wie kann ich die Felder anpassen, die auf der Profilkarte angezeigt werden?
Derzeit kann die Liste der Felder, die in der Profilkarte angezeigt werden, nicht angepasst werden.

### <a name="why-is-the-start-chat-option-on-the-profile-card-disabled-greyed-out"></a>Warum ist die Option **Chat beginnen** auf der Profilkarte deaktiviert (abgeblendet)?
Die Optionen **Chat beginnen** und **E-Mail senden** auf der Profilkarte öffnen die standardmäßgen Sofortnachrichten- und E-Mail-Apps. Die Option **Chat starten** ist aktiviert, wenn die Person, die Sie zu kontaktieren versuchen, sich in derselben Azure Active Directory-Umgebung befindet wie Sie oder ein Verbundkontakt ist.


  
