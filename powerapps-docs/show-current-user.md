---
title: Anzeigen von Details zum aktuellen Benutzer | Microsoft-Dokumentation
description: "Fügen Sie die User-Funktion ein, um den Namen und die E-Mail-Adresse des angemeldeten Benutzers in PowerApps anzuzeigen."
services: 
suite: powerapps
documentationcenter: 
author: lonu
manager: anneta
editor: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/16/2016
ms.author: lonu
ms.openlocfilehash: c5d4780908ebd20989649df14dec51d70e8eecde
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="show-information-about-a-powerapps-user"></a>Anzeigen von Informationen zu einem PowerApps-Benutzer
Mithilfe der User-Funktion können Sie den vollständigen Namen, die E-Mail-Adresse und das dem angemeldeten Benutzer zugeordnete Bild anzeigen. Sie können diese Informationen verwenden, um ein Formular automatisch auszufüllen.

Beispielsweise können Sie dieses Feature folgendermaßen einsetzen:

* Erstellen Sie für die Benutzer ein „Anmeldeformular“ zur Teilnahme an Trainings und Events, zum Einchecken bei einem Kioskcomputer usw.
* Zeigen Sie den vollständigen Namen in einer Personalverwaltungs-App an.
* Fügen Sie automatisch eine E-Mail-Adresse ein, wenn Sie sich an Ihren Helpdesk wenden.

Grundsätzlich können Sie diese Funktion immer dann einsetzen, wenn Benutzer davon profitieren, dass Formulare oder Bezeichnungen automatisch ausgefüllt werden.

&nbsp;

[!INCLUDE [app-customization-requirements](includes/app-customization-requirements.md)]

## <a name="show-user-details"></a>Anzeigen von Benutzerdetails
1. Klicken oder tippen Sie auf der Registerkarte **Einfügen** auf **Medien** und anschließend auf **Bild**.
   
   ![][2]
2. Legen Sie die Eigenschaft **[Image](controls/properties-visual.md)** auf die folgende Formel fest:
   <br>**User().Image**
   
    ![][3]
3. Klicken oder tippen Sie auf der Registerkarte **Einfügen** auf **Text** und anschließend auf **Bezeichnung**:  
   
    ![][4]
4. Legen Sie die **[Text](controls/properties-core.md)**-Eigenschaft auf diese Formel fest:
   <br>**User().FullName**
   
   ![][6]
   
   Wenn Sie dies tun, wird die Bezeichnung automatisch mit Ihrem vollständigen Namen aufgefüllt. Verschieben Sie die Bezeichnung, sodass sie sich unterhalb des Bildsteuerelements befindet, ähnlich wie hier gezeigt:
   
   ![][5]
5. Fügen Sie eine Bezeichnung hinzu, und legen Sie deren Eigenschaft **[Text](controls/properties-core.md)** auf diese Funktion fest:
   <br>**User().Email**  
   
    ![][8]
   
    Hierdurch wird die Bezeichnung automatisch mit Ihrer E-Mail-Adresse aufgefüllt. Verschieben Sie die Bezeichnung, sodass sie unterhalb der ersten Bezeichnung angezeigt wird, ähnlich wie hier dargestellt:  
   
    ![][7]

[2]: ./media/show-current-user/add-image.png
[3]: ./media/show-current-user/imageproperty.png
[4]: ./media/show-current-user/insertlabel.png
[5]: ./media/show-current-user/label.png
[6]: ./media/show-current-user/textproperty.png
[7]: ./media/show-current-user/secondlabel.png
[8]: ./media/show-current-user/email.png
[9]: ./media/show-current-user/preview.png
