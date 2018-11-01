---
title: Verwaltete Eigenschaften in modellgesteuerten Apps für Ansichten mit PowerApps | MicrosoftDocs
description: 'Erfahren Sie, wie verwaltete Eigenschaften für eine Ansicht festgelegt werden'
ms.custom: ''
ms.date: 06/12/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: a9014576-8fb2-4f28-b8bb-5d2d49d76e12
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="model-driven-app-managed-properties-for-views"></a>Verwaltete Eigenschaften in modellgesteuerten Apps für Ansichten

<a name="BKMK_ManagedProperties"></a>   
 
 Wenn Sie eine benutzerdefinierte öffentliche Ansicht in PowerApps erstellen, die Sie in eine verwaltete Lösung einbeziehen möchten, die Sie verteilen werden, haben Sie die Option, für jeden Benutzer, der Ihre Lösung installiert, die Möglichkeit einzuschränken, die Ansicht anzupassen.  
  
 Standardmäßig ist bei den meisten Ansichten die verwaltete Eigenschaft **Anpassbar** auf "Wahr" gesetzt, damit Benutzer sie anpassen können. Außer wenn Sie einen sehr triftigen Grund haben, dies zu ändern, wird empfohlen, dass Sie Benutzern erlauben, Ansichten in Ihrer App anzupassen.  
  
## <a name="set-managed-properties-for-a-view"></a>Verwaltete Eigenschaften für eine Ansicht einrichten  
  
1.  Öffnen Sie den [Lösungs-Explorer](advanced-navigation.md#solution-explorer), erweitern Sie **Entitäten**, wählen Sie die gewünschte Entität und dann **Ansichten** aus.  
  
2.  Wählen Sie eine angepasste öffentliche Ansicht aus.  
  
3.  Wählen Sie auf der Symbolleiste auf **Weitere Aktionen** > **Verwaltete Eigenschaften**.  

    > [!div class="mx-imgBorder"] 
    > ![Menü Verwaltete Eigenschaften)](media/managed-properties.png)
  
4.  Legen Sie die Optionen **Anpassbar** oder **Kann gelöscht werden** auf **True** oder auf **False** fest.  

    > [!div class="mx-imgBorder"] 
    > ![Verwaltete Eigenschaften festlegen](media/set-managed-properties.png)
  
> [!NOTE]
> Die Einstellung wird erst wirksam, wenn Sie eine Lösung exportieren, die die Ansicht als verwaltete Lösung enthält und sie sie in einer anderen Umgebung installieren.  

## <a name="next-steps"></a>Nächste Schritte
[Ansichten verstehen](create-edit-views.md)
