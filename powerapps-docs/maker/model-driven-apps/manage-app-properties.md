---
title: Verwalten der Eigenschaften einer modellgesteuerten App im PowerApps-App-Designer | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die Eigenschaften für Ihre App verwalten.
keywords: ''
ms.date: 06/27/2018
ms.service: crm-online
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: e773e60f-0211-4c4b-a1af-663be4997629
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 14
topic-status: Drafting
ms.openlocfilehash: 62129690a0f5969b6f0f749e110eca001f2c0c8b
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39685209"
---
# <a name="manage-model-driven-app-properties-in-the-app-designer"></a>Verwalten der Eigenschaften von einer modellgesteuerten App im App-Designer

App-Eigenschaften definieren wichtige Details für die App, wie den Titel oder die URL. Sie definieren die App-Eigenschaften bei der Erstellung der App. Wenn Sie diese Eigenschaften später ändern möchten, ist dies über den App-Designer möglich.  
  
1.  Wählen Sie im App-Designer auf der rechten Seite die Rechten **Eigenschaften**.  
  
    ![Eigenschaftenbereich im App-Designer](media/app-designer-properties-tab.png "Eigenschaftenbereich im App-Designer")  
  
2.  Ändern Sie die Informationen, falls erforderlich:  

    |Eigenschaft|Beschreibung|  
    |--------------|-----------------|
    |**Name**|Geben Sie einen eindeutigen und aussagekräftigen Namen für die App ein.|  
    |**Beschreibung**|Geben Sie eine kurze Beschreibung für die App ein.|  
    |**Symbol**|Standardmäßig ist das Kontrollkästchen **Standard-App verwenden** aktiviert. Um eine andere Webressource als Symbol für die App auszuwählen, deaktivieren Sie das Kontrollkästchen und wählen Sie dann ein Symbol aus der Dropdownliste. Dieses Symbol wird auf der Vorschaukachel der App angezeigt.|
    |**Eindeutiger Name**| Sie können den eindeutigen Namen nicht ändern. Mit dem eindeutigen Namen können Sie Tabellen abfragen, um Daten von der Datenbank zu erhalten.| 
    |**Client**|Definiert den Typ des Clients, für den die App verwendet wird.<br/>-  **Web:** Dies ist der klassische Dynamics 365 Customer Engagement-Webbrowserclient.<br/>-  **Einheitliche Oberfläche:** Dies ist der neue Webbrowserclient, der eine ähnliche Oberfläche für PC und mobile Geräte bietet.|
    |**API-URL-Suffix**| Hier wird standardmäßig die URL angezeigt, die Sie bei der Erstellung der App gewählt haben. Sie können die App-URL im Dialogfeld **App verwalten** ändern. Beachten Sie, dass Sie das App-URL-Suffix derzeit nicht über eine Projektmappe exportieren oder importieren können.|
    |**Begrüßungsseite für die App auswählen**|Mit dieser Option können Sie aus den in Ihrer Umgebung verfügbaren Webressourcen auswählen. Die von Ihnen erstellten Begrüßungsseiten können nützliche Informationen für Benutzer enthalten, wie z.B. Links zu Videos, Upgradeanweisungen oder Informationen zu den ersten Schritten. Weitere Informationen zum Erstellen einer Webressource, wie z.B. einer HTML-Datei, die Sie als Begrüßungsseite verwenden können, finden Sie unter [Webressourcen erstellen und bearbeiten, um die Webanwendung zu erweitern](create-edit-web-resources.md).|
    |**Mobiles Offline ermöglichen**|Diese Option ermöglicht es, dass die App offline auf Mobiltelefonen für die Profile verfügbar ist, die über die Dropdownliste **Mobile Offlineprofile** ausgewählt wurden.|
  
3.  Speichern Sie die App.  
  
## <a name="next-steps"></a>Nächste Schritte  
 [Erstellen oder Bearbeiten einer App](create-edit-app.md)
