---
title: Hinzufügen einer Verbindungsrolle zum Verknüpfen von Datensätzen miteinander | Microsoft-Dokumentation
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 8/01/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4552c874ca6be72d37465abd2492a64979aba865
ms.sourcegitcommit: 5ec4cab1dd934446ec57c320a375e577560ac88a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2019
ms.locfileid: "72239576"
---
# <a name="add-a-connection-role-to-link-records-to-each-other"></a>Hinzufügen einer Verbindungsrolle zum Verknüpfen von Datensätzen miteinander

Verbindungen ermöglichen es Ihnen, Benutzer, Kontakte, Angebote, Verkaufsaufträge und viele andere Entitätsdatensätze einander problemlos zuzuordnen. Den Datensätzen in der Zuordnung können bestimmte Rollen zugewiesen werden, die Ihnen helfen, den Zweck der Beziehung zu definieren.

Es ist eine schnelle Möglichkeit, um mehrere Verbindungen und Rollen für einen bestimmten Datensatz zu erstellen. Ein Kontakt kann z. B. viele Beziehungen zu anderen Kontakten, Konten oder Verträgen aufweisen. In jeder Beziehung kann ein Kontakt eine andere Rolle spielen.

Verbindungsrollen werden direkt einer Verbindung zugeordnet. Um eine Verbindungsrolle zu verwenden, müssen Sie zuerst eine Verbindung mit Ihrem Datensatz hinzufügen.

Bevor Sie Verbindungsrollen hinzufügen können, muss dies von Ihrem Administrator aktiviert werden. Weitere Informationen finden Sie unter [Konfigurieren von Verbindungsrollen](https://docs.microsoft.com/powerapps/maker/common-data-service/configure-connection-roles).

1. Wählen Sie zum Hinzufügen oder Verwalten von Verbindungen den Datensatz, z. B. eine Verkaufschance, aus, den Sie verwalten möchten.  
2. Wählen Sie die Registerkarte **Verknüpft** und anschließend **Verbindung** aus. Dadurch wird das Verbindungsraster mit der Liste der Verbindungen für den Datensatz geöffnet.

    > [!div class="mx-imgBorder"]
    > ![Neue Verbindungsrolle hinzufügen](media/connection1.png "Neue Verbindungsrolle hinzufügen") 

3. Wählen Sie **Verbinden** und anschließend **An anderen** oder **An mich** aus.

    > [!div class="mx-imgBorder"]
    > ![Verbindungstyp auswählen](media/connection2.png "Verbindungstyp auswählen") 
  
4. Geben Sie im Feld **Name** den Namen des Datensatzes für die Verbindung ein, oder suchen Sie ihn.

5. Wählen Sie im Feld **Als diese Rolle** das Suchsymbol aus, und wählen Sie dann **New Connection Role** (Neue Verbindungsrolle) aus. Oder verwenden Sie die Suche, um eine vorhandene Rolle zu suchen, die Sie der Verbindung zuordnen möchten. Wählen Sie anschließend **Speichern** aus.

    > [!div class="mx-imgBorder"]
    > ![Neue Verbindungsrolle auswählen](media/connection3.png "Neue Verbindungsrolle auswählen")  

    > [!NOTE]
    > Wenn Sie vor dem Erstellen einer neuen Verbindungsrolle Informationen eingegeben haben, wird ein Dialogfeld mit einer Warnung angezeigt, in dem Sie gefragt werden, ob Sie den Vorgang abbrechen und weiter an der Verbindung arbeiten oder fortfahren und den Datensatz, den Sie aktuell bearbeiten, verlassen möchten.

6. Um eine neue Verbindungsrolle zu erstellen, geben Sie auf dem Bildschirm **New Connection Role** (Neue Verbindungsrolle) einen Namen ein, und wählen Sie dann eine **Kategorie** aus.

    > [!div class="mx-imgBorder"]
    >  ![Verbindungsrollenkategorie hinzufügen](media/connection4.png "Verbindungsrollenkategorie hinzufügen") 

7. Wählen Sie **Speichern und schließen** aus, wenn der Vorgang abgeschlossen ist.

  
## <a name="manage-connection-roles"></a>Verbindungsrollen verwalten

Wenn Sie eine Verbindungsrolle verwalten möchten, wählen Sie die Verbindungsrolle aus einer Verbindungsentität aus. Dadurch wird der Entitätsdatensatz der Verbindungsrolle geöffnet.  Sie können den Namen bearbeiten, eine Verbindungsrollenkategorie auswählen und eine Beschreibung hinzufügen.


   > [!div class="mx-imgBorder"]
   > ![Verbindungsrolle bearbeiten](media/connection7.png "Verbindungsrolle bearbeiten") 
  
Sie können auch die Verbindungsrollentypen verwalten, die Sie der Verbindungsrolle zuordnen möchten.

1. Öffnen Sie die Verbindungsrolle, und wählen Sie anschließend im Befehl die Option **Manage Record Type** (Datensatztyp verwalten) aus. 

    > [!div class="mx-imgBorder"]
    > ![Verbindungsrolle bearbeiten](media/connection5.png "Verbindungsrolle bearbeiten") 
  

2. Dadurch wird eine Liste der Verbindungsrollentypen geöffnet, die Sie für diese Verbindungsrolle hinzufügen bzw. entfernen können.

    > [!div class="mx-imgBorder"]
    > ![Datensatztyp verwalten](media/connection6.png "Datensatztyp verwalten") 


