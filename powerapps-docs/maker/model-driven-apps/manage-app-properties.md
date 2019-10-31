---
title: Verwaltung modellgetriebener App-Eigenschaften im PowerApps App Designer | MicrosoftDocs
description: 'Erfahren Sie, wie Sie die Eigenschaften für Ihre App verwalten'
keywords: ''
ms.date: 02/05/2019
ms.service: powerapps
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: e773e60f-0211-4c4b-a1af-663be4997629
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
caps.latest.revision: 14
topic-status: Drafting
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="manage-model-driven-app-properties-in-the-app-designer"></a>Verwalten von modellgesteuerten App-Eigenschaften im App-Designer

App-Eigenschaften definieren wichtige Details der App, wie den Titel oder die URL. Sie können App-Eigenschaften definieren, wenn Sie eine App erstellen. Wenn Sie die App-Eigenschaften später ändern möchten, führen Sie dies im App-Designer durch.  
  
1.  Im App-Designer auf der rechten Seite wählen Sie auf die Registerkarte **Eigenschaften** aus.  

    > [!div class="mx-imgBorder"] 
    > ![Bereich "App-Designer-Eigenschaften"](media/app-designer-properties-tab.png "Bereich \"App-Designer-Eigenschaften\"")  
  
2.  Ändern Sie die Informationen so, wie dies erforderlich ist:  

    |Eigenschaft|Beschreibung|  
    |--------------|-----------------|
    |**Name**|Geben Sie einen eindeutigen Namen für die App ein.|  
    |**Beschreibung**|Geben Sie eine kurze Beschreibung für die App ein.|  
    |**Symbol**|Standardmäßig ist das Kontrollkästchen **Standard-App verwenden** aktiviert. Wenn Sie eine andere Webressource als ein Symbol für die App auswählen, deaktivieren Sie das Kontrollkästchen, und wählen Sie anschließend ein Symbol aus der Dropdownliste. Dieses Symbol wird auf der Vorschaukachel der App angezeigt.|
    |**Eindeutiger Name**| Sie können den eindeutigen Namen nicht ändern. Mithilfe des eindeutigen Namens können Sie Tabellen abfragen, um Daten aus der Datenbank abzurufen.|
    |**App URL Suffix<sup>1</sup>**| Die URL, die Sie beim Erstellen der App gewählt haben, wird hier standardmäßig angezeigt. Sie können die App-URL im Dialogfeld **App verwalten** ändern. Beachten Sie, dass Sie das App-URL-Suffix zu diesem Zeitpunkt nicht über eine Lösung exportieren bzw. importieren können.|
    |**Wählen Sie eine Startseite für die App aus**|Diese Option gestattet Ihnen, eine der Webressourcen auszuwählen, die in Ihrer Umgebung zur Verfügung stehen. Die Willkommensseiten, die Sie erstellen, können hilfreiche Informationen für Benutzern enthalten (z.B. Links zu Videos, Upgradeanweisungen oder Informationen zu ersten Schritten). Weitere Informationen dazu, wie Sie eine Webressource erstellen, wie beispielsweise eine HTML-Datei, die Sie als Begrüßungsdatei verwenden können, finden Sie unter [Erstellen und Bearbeiten von Webressourcen zum Erweitern der Webanwendung](create-edit-web-resources.md).|
    |**Mobile Offline aktivieren**|Diese Option ermöglicht es der App, auf Mobilgeräten in Profilen offline verfügbar zu sein, die über die **Mobile Offline-Profile**-Dropdownliste ausgewählt werden.|

    <sup>1</sup> Die **Client** und **App Suffix URL** Eigenschaften sind nicht mehr verfügbar, wenn Sie eine App neu erstellen.
3.  Speichern Sie die App.  
  
## <a name="next-steps"></a>Nächste Schritte  
 [Erstellen oder Bearbeiten einer App](create-edit-app.md)
