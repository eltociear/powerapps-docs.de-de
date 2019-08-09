---
title: Hinzufügen einer Verbindungs Rolle zum Verknüpfen von Datensätzen untereinander | MicrosoftDocs
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
ms.openlocfilehash: c606a7b809f1684cbe60b5e53e4b291f11b1d164
ms.sourcegitcommit: 4e4f7945c3f24faf9bb8a856a5f3892cbfd113be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2019
ms.locfileid: "68786899"
---
# <a name="add-a-connection-role-to-to-link-records-to-each-other"></a>Hinzufügen einer Verbindungs Rolle zum Verknüpfen von Datensätzen untereinander |

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

Verbindungen ermöglichen es Ihnen, Benutzer, Kontakte, Anführungszeichen, Verkaufsaufträge und viele andere Entitäts Datensätze leicht einander zuzuordnen. Den Datensätzen in der Zuordnung können bestimmte Rollen zugewiesen werden, die Ihnen helfen, den Zweck der Beziehung zu definieren.

Es ist eine schnelle Möglichkeit, mehrere Verbindungen und Rollen für einen bestimmten Datensatz zu erstellen. Ein Kontakt kann z. b. viele Beziehungen zu anderen Kontakten, Konten oder Verträgen aufweisen. In jeder Beziehung kann ein Kontakt eine andere Rolle spielen.

Verbindungs Rollen werden direkt einer Verbindung zugeordnet. Um eine Verbindungs Rolle zu verwenden, müssen Sie zuerst eine Verbindung mit Ihrem Datensatz hinzufügen.

Bevor Sie Verbindungs Rollen hinzufügen können, muss Sie von Ihrem Administrator aktiviert werden. Weitere Informationen finden Sie unter [Konfigurieren von Verbindungs Rollen](https://docs.microsoft.com/en-us/powerapps/maker/common-data-service/configure-connection-roles).

1. Wählen Sie zum Hinzufügen oder Verwalten von Verbindungen den Datensatz aus, den Sie verwalten möchten, wie eine Gelegenheit.  
2. Wählen Sie die Registerkarte **verwandt** und dann **Verbindung**aus. Dadurch wird das Verbindungs Raster mit der Liste der Verbindungen für den Datensatz geöffnet.

    > [!div class="mx-imgBorder"]
    > ![Neue Verbindungs Rolle hinzufügen](media/connection1.png "Neue Verbindungs Rolle hinzufügen") 

3. Wählen Sie **verbinden** aus, und wählen Siedann **eine andere oder eine andere** aus.

    > [!div class="mx-imgBorder"]
    > ![Verbindungstyp auswählen](media/connection2.png "Verbindungstyp auswählen") 
  
4. Geben Sie im Feld **Name** den Namen des Datensatzes für die Verbindung ein, oder suchen Sie ihn.

5. Wählen Sie im Feld **as this Role** das Symbol Suche aus, und wählen Sie dann **neue Verbindungs Rolle**aus. Oder verwenden Sie die Suche, um eine vorhandene Rolle zu suchen, die Sie der Verbindung zuordnen möchten, und wählen Sie dann **Speichern**aus.

    > [!div class="mx-imgBorder"]
    > ![Neue Verbindungs Rolle auswählen](media/connection3.png "Neue Verbindungs Rolle auswählen")  

    > [!NOTE]
    > Wenn Sie vor dem Erstellen einer neuen Verbindungs Rolle Informationen eingegeben haben, wird ein Warn Dialogfeld angezeigt, in dem Sie gefragt werden, ob Sie die Verbindung abbrechen und fortsetzen möchten, oder den aktuellen Datensatz belassen, an dem Sie arbeiten.

6. Um eine neue Verbindungs Rolle zu erstellen, geben Sie auf dem Bildschirm **neue Verbindungs Rolle** einen Namen ein, und wählen Sie dann eine **Verbindungs Rollen Kategorie**aus.

    > [!div class="mx-imgBorder"]
    >  ![Kategorie "Verbindungs Rolle hinzufügen] " (media/connection4.png "Kategorie \"Verbindungs Rolle hinzufügen") " 

7. Wenn Sie den Vorgang abgeschlossen haben, klicken Sie auf **speichern, & schließen**.

  
## <a name="manage-connection-roles"></a>Verwalten von Verbindungs Rollen

Wählen Sie die Verbindungs Rolle aus einer Verbindungs Entität aus, um eine Verbindungs Rolle zu verwalten. Dadurch wird der Entitäts Daten Satz der Verbindungs Rolle geöffnet.  Sie können den Namen bearbeiten, eine Kategorie der Verbindungs Rolle auswählen und eine Beschreibung hinzufügen.


   > [!div class="mx-imgBorder"]
   > ![Verbindungs Rolle bearbeiten](media/connection7.png "Editconnection-Rolle") 
  
Sie können auch die Verbindungs Rollen Typen verwalten, die Sie der Verbindungs Rolle zuordnen möchten.

1. Öffnen Sie die Verbindungs Rolle, und wählen Sie dann im Befehl **Daten Satz Typen verwalten** aus. 

    > [!div class="mx-imgBorder"]
    > ![Verbindungs Rolle bearbeiten](media/connection5.png "Editconnection-Rolle") 
  

2. Dadurch wird eine Liste der Verbindungs Rollen Typen geöffnet, die Sie für diese Verbindungs Rolle hinzufügen bzw. entfernen können.

    > [!div class="mx-imgBorder"]
    > ![Daten Satz Typen verwalten](media/connection6.png "Daten Satz Typen verwalten") 


