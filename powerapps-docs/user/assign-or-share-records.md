---
title: Zuweisen oder Freigeben von Datensätzen | Microsoft-Dokumentation
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 1/20/2020
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 81a6513f98351f656fdac3fd0ccc24a10061ca85
ms.sourcegitcommit: d0f02fdaa125feaea884932e1ef31b8fea1bd10c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/30/2020
ms.locfileid: "76886503"
---
# <a name="assign-or-share-records"></a>Zuweisen oder Freigeben von Datensätzen

Wenn Sie möchten, dass eine andere Person in Ihrer Organisation einen Kundendatensatz bearbeitet, können Sie dieser Person den Datensatz zuweisen. Sie können einen Datensatz auch einem Team oder sich selbst zuweisen.  

Verwenden Sie die Option **Freigeben**, wenn Sie im Besitz des Datensatzes bleiben möchten, jedoch auch eine andere Person daran arbeiten soll. 

1. Wählen Sie im linken Navigationsbereich einen Datensatztyp aus, z. B. **Kontakte**.

2. Wählen Sie aus der Liste der Datensätze den Datensatz aus, den Sie neu zuweisen möchten.  
  
3. Wählen Sie in der Befehlsleiste **Zuweisen** aus.

   > [!div class="mx-imgBorder"]
   > ![Neuzuweisen eines Datensatzes](media/assign1.png "Neuzuweisen eines Datensatzes")

   > [!NOTE]
   > Wenn Sie im Besitz des Datensatzes bleiben möchten, eine andere Person jedoch auch daran arbeiten soll, wählen Sie **Freigeben** aus. Verwenden Sie dann die QuickInfos, um sich durch die Option **Freigeben** führen zu lassen. 
   
4. Wählen Sie im Dialogfeld „Zuweisen“ im Bereich **Zuweisen zu** die Option **Mir** oder **Benutzer oder Team** aus.

   > [!div class="mx-imgBorder"]
   > ![Neuzuweisen eines Datensatzes zu meiner Person oder zu einem Team](media/assign2.png "Neuzuweisen eines Datensatzes zu meiner Person oder zu einem Team")
  
   Wenn Sie **Benutzer oder Team** auswählen, geben Sie im Feld **Nach Datensätzen suchen** den Namen des Benutzers bzw. Teams ein. Wenn Sie einen neuen Datensatz erstellen müssen, wählen Sie **+ Neu** aus.
  
5. Wenn Sie fertig sind, wählen Sie **Zuweisen** aus.

## <a name="use-advanced-find-to-reassign-records"></a>Verwenden der erweiterten Suche zum erneuten Zuweisen von Datensätzen

Verwenden Sie die erweiterte Suche, um nach Datensätzen zu suchen und diese dann einem anderen Benutzer zuzuweisen. Weitere Informationen zur erweiterten Suche finden Sie unter [Erstellen, Bearbeiten oder Speichern einer erweiterten Suche](advanced-find.md).


1. Wählen Sie in der Befehlsleiste **Erweiterte Suche** aus.

   > [!div class="mx-imgBorder"]
   > ![Erweiterte Suche](media/assign3.png "Erweiterte Suche")
   
2. Wählen Sie aus der Liste der Datensätze die Datensätze aus, die Sie neu zuweisen möchten, und wählen Sie dann die Option „Zuweisen“ aus.

   > [!div class="mx-imgBorder"]
   > ![Neuzuweisen eines Datensatzes mithilfe der erweiterten Suche](media/assign4.png "Neuzuweisen eines Datensatzes mithilfe der erweiterten Suche")
   
 
 ## <a name="reassign-all-records-for-admins"></a>Neuzuweisen aller Datensätze (für Administratoren)
 
 Ein Administrator kann einem Benutzer den gesamten Datensatz über den Administratorbereich „Einstellung“ neu zuweisen.
 
 1. Wechseln Sie zu **Einstellungen** > **Sicherheit**.
 2. Wählen Sie **Benutzer** und anschließend einen Benutzernamen aus, um das Profil des Benutzers zu öffnen.
 3. Wählen Sie auf der Befehlsleiste **Datensätze neu zuweisen** aus.
 
   > [!div class="mx-imgBorder"]
   > ![Neuzuweisen aller Datensätze](media/assign5.png "Neuzuweisen aller Datensätze")
   
 4. Legen Sie im Dialogfeld **Datensätze neu zuweisen** fest, wie Sie alle Datensätze neu zuweisen möchten, und wählen Sie dann **OK** aus.
 
  > [!NOTE]
   > Mit der Option **Datensätze neu zuweisen** werden alle Datensätze unabhängig von ihrem Status neu zugewiesen. Inaktive und aktive Datensätze werden dem anderen Benutzer oder Team zugewiesen. Wenn der Datensatz einem anderen Benutzer oder Team zugewiesen wird, werden auch alle aktivierten Prozesse, einschließlich Geschäftsregeln und Workflows, deaktiviert. Der neue Besitzer muss die zu verwendeten Prozesse aktivieren.
 
   > [!div class="mx-imgBorder"]
   > ![Alle Datensätze einem Benutzer oder Team neu zuweisen](media/assign6.png "Neuzuweisen aller Datensätze zu einem Benutzer oder Team")
 

