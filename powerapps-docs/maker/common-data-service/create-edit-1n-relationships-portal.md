---
title: 'Erstellen oder Bearbeiten von 1: N- (eine-zu-vielen) oder N:1-Entitätsbeziehungen (viele-zu einer) im PowerApps-Portal | MicrosoftDocs'
description: 'Erstellen oder Bearbeiten von 1: N- oder n: n:-Entitätsbeziehungen mithilfe des PowerApps-Portals'
ms.custom: ''
ms.date: 06/11/2018
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
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 70f48af48b2a9221029735de484b555bc03a66c4
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2756518"
---
# <a name="create-and-edit-one-to-many-or-many-to-one-entity-relationships-using-powerapps-portal"></a>Erstellen oder Bearbeiten von 1: N- (eine-zu-vielen) oder N:1-Entitätsbeziehungen (viele-zu einer) im PowerApps-Portal

Das [PowerApps-Portal](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) stellt eine einfache Möglichkeit zur Verfügung, 1:N- (eine-zu-viele) oder N:1-Entitätsbeziehungen (viele-zu-einer) für Common Data Service zu erstellen und zu bearbeiten.

PowerApps-Portal aktiviert das  Konfigurieren der allgemeinen Optionen, jedoch bestimmte Optionen können nur mithilfe des Lösungs-Explorers festgelegt werden. Weitere Informationen: 
- [Erstellen oder Bearbeiten von 1: N (eine-zu-vielen) oder N:1 (viele-zu einer)-Entitätsbeziehungen](create-edit-1n-relationships.md)
- [Erstellen oder Bearbeiten von 1: N (eine-zu-vielen) oder N:1 (viele-zu-einer) Entitätsbeziehungen mithilfe des Lösungs-Explorers](create-edit-1n-relationships-solution-explorer.md)

## <a name="view-entity-relationships"></a>Zeigen Sie Entitätsbeziehungen an

1. Wählen Sie im [PowerApps-Portal](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) entweder den Entwurfsmodus **Modellgesteuert** oder **Canvas** aus.
2. Wählen Sie **Daten**  >  **Entitäten** und wählen Sie die Entität aus, die die Beziehung enthält, die Sie anzeigen möchten.
3. Wenn die Registerkarte **Beziehungen** ausgewählt ist, können Sie die folgenden Ansichten auswählen: 

 |Ansicht|Beschreibung|
 |--|--|
 |**Alle**| Zeigt alle Beziehungen für die Entität an|
 |**Benutzerdefiniert**|Zeigt nur benutzerdefinierte Beziehungen der Entität an|
 |**Standard**|Zeigt nur Standard-Beziehungen der Entität an|
<!-- TODO: What is the actual difference between All and Default? -->

![Konten-Entitätsbeziehungen](media/view-account-relationships-portal.png)

## <a name="create-relationships"></a>Beziehung erstellen

Während dem [Anzeigen von Entitätsbeziehungen](#view-entity-relationships) wählen Sie in der Befehlsleiste **Beziehung hinzufügen** und entweder **viele-zu-einer** oder **einer-zu-vielen** aus.

![Wählen Sie auf den Typ der Beziehung](media/add-relationship-menu-portal.png)

> [!NOTE]
> Informationen über **viel-zu-einer** Beziehungen finden Sie unter [Erstellen von N:N (vielen-zu-vielen) Beziehungen ](create-edit-nn-relationships.md)

<!-- This may change going forward, but this is the way it is now. #2534972 -->
> [!Important]
> Dieses Portal verwendet eine andere Terminologie als der Lösungs-Explorer. Der Lösungsexplorer **Primäre Entität** ist die **Aktuelle Entität** im Portal.

Je nach Optionen sehen Sie:

<!-- These are the correct screenshots from the UI as of 6/11/18 -->
|Typ|Bereich|
|--|--|
|**Viele-zu-eine**|![Einer-zu-vielen-Beziehungsbereich](media/many-to-one-relationship-panel.png)|
|**Einer-zu-vielen**|![Einer-zu-vielen-Beziehungsbereich](media/one-to-many-relationship-panel.png)|

Wählen Sie für **Verknüpfte Entität** die Beziehung aus, die Sie zwischen den zwei Entitäten erstellen möchten. 

> [!NOTE]
> Mit einer Option wird ein Suchfeld in der *aktuellen* Entität erstellt.

Sobald Sie die Entität ausgewählt ist, können Sie die Beziehung bearbeiten. In diesem Beispiel können mehrere Kontaktentitätsdatensätze einer Firma zugeordnet werden.

<!-- These are the correct screenshots from the UI as of 6/11/18 -->
![1:n-Beziehungskonto und -Kontakt](media/One-to-many-account-contact.png)

Sie können die bereitgestellten Standardwerte bearbeiten vor dem Speichern. Wählen Sie **Weitere Optionen** aus, um die Felder **Beziehungsname** und **Suchfeld-Description** anzuzeigen.

|Feld|Beschreibung|
|--|--|
|**Anzeigename für das Suchfeld**|Diese Entität wird der Zieltyp für das Suchfeld, das für die verknüpfte Entität erstellt wird.<br />Dies kann später bearbeitet werden.|
|**Name des Suchfelds**|Der Name für das Suchfeld, das für die verknüpfte Entität erstellt wird.|
|**Beziehungsname**|Der Name für die Beziehung, die erstellt wird.|
|**Suchfeldbeschreibung**|Geben Sie eine Beschreibung für das Suchfeld ein. In Modell-angetriebenen Apps erscheint dies als Tipp, wenn Personen mit der Maus über das Feld fahren. <br />Dies kann später bearbeitet werden.|

Sie können die Entitäten weiter bearbeiten. Wählen Sie **Entität speichern** aus, um eine Beziehung zu erstellen, die Sie konfiguriert haben.

## <a name="edit-relationships"></a>Beziehungen bearbeiten

Während dem [Anzeigen von Entitätsbeziehungen](#view-entity-relationships) wählen Sie die Beziehung aus, die Sie bearbeiten möchten.

> [!NOTE]
> Jede Beziehung kann in der primären Entität oder der verknüpfte Entität als Beziehung **N:1** oder **1: N-Beziehungen** angezeigt werden. Sie müssen zwar in jedem Ort bearbeitet werden kann, es kann aber dieselbe Beziehung sein.
>
> Der Herausgeber einer verwalteten Lösung kann Anpassungen von Beziehungen verhindern, die Teil der Lösung sind.

Die einzelnen Felder, die Sie bearbeiten können, sind **Suchfeldanzeigename** und **Suchfeldbeschreibung**. Diese können ebenfalls unter Eigenschaften des Suchfelds in der verknüpften Entität bearbeitet werden. Weitere Informationen: [Bearbeiten eines Feldes](create-edit-field-portal.md#edit-a-field)

## <a name="delete-relationships"></a>Beziehungen löschen

Während dem [Anzeigen von Entitätsbeziehungen](#view-entity-relationships) wählen Sie die Beziehung aus, die Sie löschen möchten.

![Entitätsbeziehung löschen](media/delete-entity-relationship-portal.png)

Sie können den Befehl **Beziehung löschen** in der Befehlsleiste oder im Zeilenkontextmenü verwenden, wenn Sie die Elipses (**...**) auswählen.

Das Löschen der Beziehung löscht das Suchfeld der verknüpften Entität.

> [!NOTE]
> Sie können die Beziehung nicht löschen, die Abhängigkeiten enthält. Wenn Sie das Suchfeld in einem Formular für die verknüpfte Entität hinzugefügt haben, müssen Sie das Feld aus dem Formular entfernen, bevor Sie die Beziehung löschen.

### <a name="see-also"></a>Siehe auch

[Erstellen und Bearbeiten von Beziehungen zwischen Entitäten](create-edit-entity-relationships.md)<br />
[Erstellen oder Bearbeiten von 1: N (eine-zu-vielen) oder N:1 (viele-zu einer)-Entitätsbeziehungen](create-edit-1n-relationships.md)<br />
[Erstellen oder Bearbeiten von 1: N (1: n- oder n: n) Entitätsbeziehungen 1 mithilfe des Lösungs-Explorers](create-edit-1n-relationships-solution-explorer.md)<br />
[Bearbeiten eines Felds](create-edit-field-portal.md#edit-a-field)
