---
title: Erstellen oder bearbeiten von modellgesteuerten Hauptformularen in Power Apps | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie ein Hauptformular erstellen oder bearbeiten können.
ms.custom: ''
ms.date: 05/23/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: <needs new guid>
caps.latest.revision: 18
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 2c60e3b149ae634364a0e0bca8fb2349c96c1aab
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "2875308"
---
# <a name="create-or-edit-a-model-driven-app-main-form-for-an-entity"></a>Erstellen oder Bearbeiten eines modellgesteuerten App-Hauptformulars für eine Entität 

In diesem Thema wird gezeigt, wie Sie ein Hauptformular für eine Entität erstellen oder bearbeiten.

Wenn Sie ein neues Formular für eine Entität erstellen, weist es den Formulartyp Haupt auf. Wenn das Formular geöffnet wird, ist es identisch mit dem Formular namens Informationen. Sie können Felder, Abschnitte, Registerkarten, Navigation sowie dem Formular zugeordnete Eigenschaften hinzufügen oder bearbeiten und das Formular dann speichern.

Jedes Hauptformular besteht aus mindestens einer Registerkarte. Jede Registerkarte kann einen oder mehrere Abschnitte enthalten. Jeder Abschnitt enthält ein Feld oder mehrere Felder oder IFRAMES. Wenn Sie als Grundlage für das neue Formular kein vorhandenes Formular verwenden möchten, können Sie ein Formular klonen. 

Stellen Sie sicher, dass Sie über die Sicherheitsrolle „Systemadministrator“ oder „Systemanpasser“ bzw. entsprechende Berechtigungen verfügen, um diese Aufgabe auszuführen.

## <a name="how-to-create-or-edit-a-main-form"></a>So erstellen oder bearbeiten Sie ein Hauptformular
  
1.   Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.


> [!IMPORTANT]
> "Wenn der **Modell-angetrieben** Entwurfsmodus nicht verfügbar ist, müssen Sie ggf eine [Umgebung erstellen](https://docs.microsoft.com/powerapps/administrator/create-environment).   
  
2.  Erweitern Sie **Daten** und wählen **Entitäten**, wählen Sie die Entität aus und wählen Sie die Registerkarte **Formulare**. 

3. Um ein neues Hauptformular zu erstellen, wählen Sie auf der Symbolleiste die Option **Formular hinzufügen** > **Hauptformular** aus.  
    \-ODER- Zur Bearbeitung eines Hauptformulars wählen Sie ein beliebiges Formular des **Typs** **Haupt** aus.
  
3.  Ändern Sie den Formularentwurf auf eine der folgenden Arten, falls erforderlich:
    -   Hinzufügen einer Registerkarte zu einem Formular
    -   Hinzufügen eines Abschnitts zu einem Formular
    -   Hinzufügen eines Felds zu einem Formular
    -   Hinzufügen oder Bearbeiten eines Formular-IFRAMEs
    -   Hinzufügen oder Bearbeiten eines Unterrasters in einem Formular
    -   Hinzufügen oder Bearbeiten einer Formularwebressource
    -   Hinzufügen oder Bearbeiten der Formularnavigation für verknüpfte Entitäten
    -   Bearbeiten von Formularkopfzeilen und -fußzeilen
    -   Entfernen einer Registerkarte, eines Abschnitts, eines Felds oder eines IFRAMEs
    -   Aktivieren oder Deaktivieren des Formular-Assistenten
    
4.  Bearbeiten Sie die Eigenschaften für Teile des Formulars je nach Bedarf:
    -   Bearbeiten von Formulareigenschaften
    -   Bearbeiten von Formularfeldeigenschaften
    -   Bearbeiten von Registerkarteneigenschaften
    -   Bearbeiten von Abschnitteigenschaften

5.  Fügen Sie Ereignisskripts hinzu, falls erforderlich. 

6.  Legen Sie fest, mit welchen Sicherheitsrollen das Formular angezeigt werden kann. Weitere Informationen: [Zuweisen von Sicherheitsrollen zu einem Formular](https://docs.microsoft.com/dynamics365/customer-engagement/admin/assign-security-roles-form)

7.  Prüfen Sie in einer Vorschau die Darstellung des Hauptformulars und die Funktionsweise der Ereignisse:
    - Wählen Sie auf der Registerkarte **Startseite** die Option **Vorschau** aus, und wählen Sie dann **Formular erstellen**, **Formular aktualisieren** oder **Schreibgeschütztes Formular** aus.
    - Wählen Sie zum Schließen des Formulars „Vorschau” im Menü **Datei** die Option **Schließen** aus.

8.  Wenn Sie die Bearbeitung des Formulars abgeschlossen haben, wählen Sie **Speichern unter** aus, geben Sie einen Namen für das Formular ein, und wählen Sie dann **OK** aus.

9.  Sind die Anpassungen vollständig, können sie veröffentlicht werden:
    -   Wenn Sie Anpassungen für ausschließlich die Komponente veröffentlichen möchten, die Sie gerade bearbeiten, wählen Sie unter **Komponenten** die Entität aus, an der Sie gearbeitet haben, und wählen Sie dann **Veröffentlichen** aus.
    -   Um Anpassungen für alle nicht veröffentlichten Komponenten gleichzeitig zu veröffentlichen, wählen Sie unter **Komponenten** die Option **Entitäten** und dann auf der Befehlsleiste die Option **Alle Anpassungen veröffentlichen** aus.
    
 
### <a name="next-steps"></a>Nächste Schritte  
[Übersicht zur Formular-Editor-Benutzeroberfläche](form-editor-user-interface-legacy.md)
 
