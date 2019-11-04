---
title: Anzeigen der Profil Karte für einen Kontakt oder Benutzer | MicrosoftDocs
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
ms.openlocfilehash: 67441e506ba2715a9994f6b81cd08426e37e0fc8
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2019
ms.locfileid: "71950908"
---
# <a name="view-the-profile-card-for-a-contact-or-user"></a>Anzeigen der Profil Karte für einen Kontakt oder Benutzer

Verwenden Sie die Profil Karte, um schnell Informationen zu einem Kontakt oder Benutzer zu erhalten. Wenn Sie ein Kontakt-oder Benutzer Feld in Modell gesteuerten apps in Dynamics 365 (z. b. Dynamics 365 Sales und Dynamics 365 Customer Service) auswählen, finden Sie entsprechende Informationen auf der zugehörigen Profil Karte. Weitere Informationen zu Profil Karten finden Sie unter [Profil Karten in Office 365](https://support.office.com/en-us/article/Profile-cards-in-Office-365-e80f931f-5fc4-4a59-ba6e-c1e35a85b501).

> [!NOTE]
>  - Die Profil Karte ist für die **Kontakt** -und **Benutzer** Entität verfügbar. Weitere Informationen finden Sie unter [Aktivieren der Profil Karte (für Administratoren)](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/admin/enable-profile-card).
>  - Die Profil Karte in Common Data Service wird nicht angezeigt, wenn die Multi-Factor Authentication für den Office-Delta Dienst in Azure Active Directory aktiviert ist.

## <a name="view-a-contacts-profile"></a>Anzeigen des Profils eines Kontakts

1.  Wechseln Sie zu **Aktivitäten**.
2.  Wählen Sie eine vorhandene Aktivität aus, oder erstellen Sie eine neue.
3.  Zeigen Sie mit dem Mauszeiger auf das Feld "" **,** wenn es einen Kontaktdaten Satz hat 

Sie können die Details des Kontakts Inline anzeigen, einschließlich des Kontakt Bilds, des Namens, des Titels und des Kontos.

4. Um weitere Details anzuzeigen, wählen Sie **mehr anzeigen** aus, um das Profil des Kontakts zu erweitern.
 
    > [!div class="mx-imgBorder"] 
    > ![Details zur Kontakt Profil Karte erweitern](media/profile1.png "Details zur Kontakt Profil Karte erweitern")
   
 ## <a name="view-a-users-profile"></a>Anzeigen des Profils eines Benutzers
 
1.  Wechseln Sie zu **Konten**.
2.  Wählen Sie einen Kontodaten Satz aus.
3.  Zeigen Sie auf das Feld "Besitzer", wenn es einen Benutzerdaten Satz enthält. Sie können die Details des Benutzers Inline anzeigen.
4.  Um weitere Details wie e-Mails und freigegebene Dateien für den Benutzer anzuzeigen, wählen Sie **mehr anzeigen** aus, um das Profil des Kontakts zu erweitern.
 
    > [!div class="mx-imgBorder"] 
    > ![Benutzerprofil-Karten Detail erweitern](media/profile2.png "Benutzerprofil-Kartendetails erweitern")


 ## <a name="faqs"></a>Obigen
 
### <a name="where-can-i-see-profile-cards-in-dynamics-365"></a>Wo kann ich Profil Karten in Dynamics 365 sehen?
Profil Karten sind in Kontakt-und Benutzerdaten Sätzen zu sehen. Sie können Sie nur anzeigen, wenn Sie sich in einer Suche befinden.

### <a name="where-is-information-shown-in-the-profile-card-coming-from"></a>Wo werden die Informationen angezeigt, die in der Profil Karte angezeigt werden?
Die Informationen, die auf der Karte Kontakt Profil angezeigt werden, werden von Common Data Service abgerufen (und nicht von Microsoft Exchange). Dies bedeutet, dass die Kontaktinformationen von Dynamics 365 stammen.

Die Informationen, die auf der Benutzerprofil Karte angezeigt werden, werden aus Office 365 (Azure Active Directory) abgerufen. Weitere Informationen finden Sie unter [Profil Karten in Office 365 (Administrator Abschnitt)](https://support.office.com/en-us/article/Profile-cards-in-Office-365-e80f931f-5fc4-4a59-ba6e-c1e35a85b501).

### <a name="how-can-i-customize-the-fields-shown-on-the-profile-card"></a>Wie kann ich die Felder anpassen, die auf der Profil Karte angezeigt werden?
Die Liste der Felder, die auf der Profil Karte angezeigt werden, ist zurzeit nicht für die Anpassung geöffnet.

### <a name="why-is-the-start-chat-option-on-the-profile-card-disabled-greyed-out"></a>Warum ist die Option zum **Starten von Chats** auf der Profil Karte deaktiviert (abgeblendet)?
Mit den Optionen **Chat starten** und **e-Mail senden** auf der Profil Karte werden Ihre standardmäßigen Sofortnachrichten-und e-Mail-apps geöffnet. Die Option **Chat starten** ist aktiviert, wenn die Person, die Sie versuchen, sich in derselben Azure Active Directory Umgebung zu kontaktieren, wie Sie oder ein Verbund Kontakt ist.


  
