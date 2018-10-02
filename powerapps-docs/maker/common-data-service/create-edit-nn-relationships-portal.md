---
title: 'Erstellen von n:n-Entitätsbeziehungen in Common Data Service for Apps mithilfe des PowerApps-Portals | MicrosoftDocs'
description: 'Erfahren Sie, wie Sie N:N-Beziehungen erstellen'
ms.custom: ''
ms.date: 06/11/2018
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
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="create-many-to-many-entity-relationships-in-common-data-service-for-apps-using-powerapps-portal"></a>Erstellen von n:n-Entitätsbeziehungen in Common Data Service for Apps mithilfe des PowerApps-Portals

DAs [PowerApps-Portal](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) stellt eine einfache Möglichkeit zur Verfügung, viele-zu-viele-Entitätsbeziehungen für Common Data Service für Apps zu erstellen und zu bearbeiten.

PowerApps-Portal aktiviert das  Konfigurieren der allgemeinen Optionen, jedoch bestimmte Optionen können nur mithilfe des Lösungs-Explorers festgelegt werden. Weitere Informationen: 
- [N:N (viele-zu-viele)-Beziehungen erstellen](create-edit-nn-relationships.md)
- [Erstellen von n:n-Entitätsbeziehungen in Common Data Service for Apps mithilfe des Projektmappen-Explorers](create-edit-nn-relationships-solution-explorer.md)

## <a name="view-many-to-many-entity-relationships"></a>Viele-zu-viele-Entitätsbeziehungen anzeigen

1. In [PowerApps-Portal](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) Wählen Sie **Modell-angetrieben** oder **Canvas** Entwurfsmodus aus.
2. Wählen Sie **Daten**  >  **Entitäten** und wählen Sie die Entität aus, die die Beziehung enthält, die Sie anzeigen möchten.
3. Wenn die Registerkarte **Beziehungen** ausgewählt ist, können Sie die folgenden Ansichten auswählen: 

 |Ansicht|Beschreibung|
 |--|--|
 |**Alle**| Zeigt alle Beziehungen für die Entität an|
 |**Benutzerdefiniert**|Zeigt nur benutzerdefinierte Beziehungen der Entität an|
 |**Standard**|Zeigt nur Standard-Beziehungen der Entität an|
<!-- TODO: What is the actual difference between All and Default? -->

![Konten-Entitätsbeziehungen](media/view-account-relationships-portal.png)

n:n-Beziehungen sind haben den **Beziehungstyp** **Viele-zu-viele**.

> [!NOTE]
> Die Entität, die Sie anzeigen, verfügt möglicherweise über keine **viele-zu-viele**-Beziehungen.

## <a name="create-relationships"></a>Beziehung erstellen

Während dem [Anzeigen von Entitätsbeziehungen](#view-many-to-many-entity-relationships) wählen Sie in der Befehlsleiste **Beziehung hinzufügen** und **Viele-zu-viele**aus.

![Wählen Sie auf den Typ der Beziehung](media/add-relationship-menu-portal.png)

Wählen Sie im **Viele-zu-viele**-Bereich die Entität aus, die der aktuellen Entität zugewiesen werden soll.

![n:n-Bereich mit ausgewählter Firmenentität](media/many-to-many-panel-1.png)

Wählen Sie **Weitere Optionen** aus, um die Felder **Beziehungsname** und **Beziehungsentitätsname** anzuzeigen.

![n:n-Bereich mit ausgewählten weiteren Optionen](media/many-to-many-panel-2.png)

Die Werte für diese Felder werden für Sie anhand der ausgewählten Entität erstellt.

> [!NOTE]
> Wenn Sie mehrere **n:n**-Beziehung mit denselben zwei Entitäten erstellen, müssen Sie die erstellten Felder **Beziehungsname** und **Beziehungsentitätsname** bearbeiten, sodass sie eindeutig sind.

Wählen Sie **OK** aus, um den Bereich **n:n** zu schließen. Die Beziehung wird erstellt, wenn die Sie die Änderungen an der Entität speichern. 

Sobald sie gespeichert sind, kann mit [PowerApps-Portal](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) nichts mehr geändert werden. Zum Bearbeiten der Eigenschaften der Beziehung für modellgesteuerte Apps verwenden Sie den [Projektmappen-Explorer](create-edit-nn-relationships-solution-explorer.md).

## <a name="delete-relationships"></a>Beziehungen löschen

Während dem [Anzeigen von Entitätsbeziehungen](#view-many-to-many-entity-relationships) wählen Sie die Beziehung aus, die Sie löschen möchten.

![Entitätsbeziehung löschen](media/delete-entity-relationship-portal.png)

Sie können den Befehl **Beziehung löschen** in der Befehlsleiste oder im Zeilenkontextmenü verwenden, wenn Sie die Elipses (**...**) auswählen.

Durch das Löschen der n:n-Beziehung wird auch die Beziehungsentität gelöscht. Alle Daten, die Entitäten mit der Beziehung verbinden, gehen verloren.

### <a name="see-also"></a>Siehe auch

[N:N (viele-zu-viele)-Beziehungen erstellen](create-edit-nn-relationships.md)<br />
[Erstellen von n:n-Entitätsbeziehungen in Common Data Service for Apps mithilfe des Projektmappen-Explorers](create-edit-nn-relationships-solution-explorer.md)
