---
title: Anzeigen von Details zum aktuellen Benutzer in einer Canvas-App | Microsoft-Dokumentation
description: In powerapps den Namen und die e-Mail-Adresse des angemeldeten Benutzers in einer Canvas-App anzeigen
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/16/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f77ec80cfaf579c836277f0e29d3b84b325a0462
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74674607"
---
# <a name="show-information-about-a-power-apps-user-in-a-canvas-app"></a>Anzeigen von Informationen zu einem powerapps-Benutzer in einer Canvas-App

Zeigen Sie in powerapps den vollständigen Namen, die e-Mail-Adresse und das Bild an, das dem Benutzer zugeordnet ist, der sich bei einer Canvas-App angemeldet hat. Sie können diese Informationen verwenden, um beispielsweise ein Formular automatisch auszufüllen.

Beispielsweise können Sie dieses Feature folgendermaßen einsetzen:

* Erstellen Sie für die Benutzer ein „Anmeldeformular“ zur Teilnahme an Trainings und Events, zum Einchecken bei einem Kioskcomputer usw.
* Zeigen Sie den vollständigen Namen in einer Personalverwaltungs-App an.
* Fügen Sie automatisch eine E-Mail-Adresse ein, wenn Sie sich an Ihren Helpdesk wenden.

Grundsätzlich können Sie diese Funktion immer dann einsetzen, wenn Benutzer davon profitieren, dass Formulare oder Bezeichnungen automatisch ausgefüllt werden.

[!INCLUDE [app-customization-requirements](../../includes/app-customization-requirements.md)]

## <a name="show-user-details"></a>Anzeigen von Benutzerdetails

1. Klicken oder tippen Sie auf der Registerkarte **Einfügen** auf **Medien** und anschließend auf **Bild**.
   
   ![][2]
2. Legen Sie die Eigenschaft **[Image](controls/properties-visual.md)** auf die folgende Formel fest:
   <br>**User().Image**
   
    ![][3]
3. Klicken oder tippen Sie auf der Registerkarte **Einfügen** auf **Text** und anschließend auf **Bezeichnung**:  
   
    ![][4]
4. Legen Sie die **[Text](controls/properties-core.md)** -Eigenschaft auf diese Formel fest:
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
