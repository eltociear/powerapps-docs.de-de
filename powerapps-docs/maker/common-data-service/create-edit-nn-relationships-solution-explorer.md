---
title: 'Erstellen von n:n-Entitätsbeziehungen in Common Data Service mithilfe des Lösungs-Explorers | MicrosoftDocs'
description: 'Erfahren Sie, wie Sie N:N-Beziehungen erstellen'
ms.custom: ''
ms.date: 05/29/2018
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
---

# <a name="create-nn-many-to-many-entity-relationships-in-common-data-service-using-solution-explorer"></a>Erstellen von n:n-Entitätsbeziehungen in Common Data Service mithilfe des Lösungs-Explorers

Lösungs-Explorer bietet eine Möglichkeit, um n:n (viele-zu-viele)-Beziehungen für Common Data Service zu erstellen und zu bearbeiten.

[PowerApps-Portal](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) aktiviert das  Konfigurieren der allgemeinen Optionen, jedoch bestimmte Optionen können mithilfe des Lösungs-Explorers nur festgelegt werden. Weitere Informationen:
- [N:N (n:n)-Beziehungen erstellen](create-edit-nn-relationships.md)
- [Erstellen von n:n-Entitätsbeziehungen in Common Data Service mithilfe des PowerApps-Portals](create-edit-nn-relationships-portal.md)

  
## <a name="open-solution-explorer"></a>Öffnen Sie den Lösungs-Explorer

Ein Teil des Namens jeder benutzerdefinierten Entität, die Sie erstellen, ist das Anpassungspräfix. Dieser Satz basiert auf dem Lösungsherausgeber für die Lösung, in der Sie arbeiten. Wenn Ihnen das Anpassungspräfix wichtig ist, achten Sie darauf, dass Sie in einer nicht verwalteten Lösung oder der Standardlösung arbeiten, in der das Anpassungspräfix Ihren Wünschen für diese Entität entspricht. Weitere Informationen [Lösungsherausgeberpräfix ändern](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-entity-relationships"></a>Zeigen Sie Entitätsbeziehungen an

Im Lösungexplorer erweitern Sie **Entitäten** und wählen eine Entität. Innerhalb der Entität wählen Sie **N:N-Beziehungen** aus.

![N:M-Entitätsbeziehungen anzeigen](media/view-nn-entity-relationships-solution-explorer.png)

## <a name="create-relationships"></a>Beziehung erstellen

Während dem [Anzeigen von Entitätsbeziehungen](#view-entity-relationships) wählen Sie in der Befehlsleiste **n:n-Beziehung** aus.

> [!NOTE]
> Wenn der Befehl nicht verfügbar ist, kann die Entität keine benutzerdefinierte Beziehung erstellen.

![Neues n:n-Beziehungsformular](media/new-nn-entity-relationship-form-solution-explorer.png)

Wählen Sie in der Gruppe **Andere Entität** das Feld **Entitätsname** aus, wählen Sie die Entität aus, mit der Sie eine Beziehung erstellen möchten. Damit werden de Felder **Name** und **Beziehungsentitätsname** in der Gruppe **Beziehungsdefinition** gefüllt.

Sie können ![Entitätsbeziehungsschaltfläche speichern](media/save-entity-icon-solution-explorer.png) klicken, um die Entität zu speichern und die Bearbeitung fortsetzen. Weitere Informationen: [Beziehungsinformationen bearbeiten](#edit-relationships)

> [!NOTE]
> Wenn die Werte für **Name** oder **Entitätsname der Beziehung** bereits im System vorhanden sind, erhalten Sie beim Speichern eine Fehlermeldung. Bearbeiten Sie die Werte, damit sie eindeutig sind und versuchen Sie es erneut.

## <a name="edit-relationships"></a>Beziehungen bearbeiten

Während dem [Anzeigen von Entitätsbeziehungen](#view-entity-relationships) wählen Sie die Entität aus, die Sie bearbeiten möchten. 

> [!NOTE]
> Der Herausgeber einer verwalteten Lösung kann Anpassungen von Beziehungen verhindern, die Teil der Lösung sind.

Die folgenden Entitätsbeziehungseigenschaften können bearbeitet werden, wenn die Beziehung erstellt wurde.

> [!IMPORTANT]
> Nachdem Sie diese Eigenschaften bearbeitet haben, müssen Sie Anpassungen veröffentlichen, bevor sie in modellgesteuerten Apps wirksam werden.

### <a name="edit-display-options"></a>Anzeigeoptionen bearbeiten

Für **Aktuelle Entität** und **Andere Entität** können Sie die Anzeigenoptionsfelder bearbeiten, die steuern, wie verknüpfte Entitäten bei modellgesteuerten Apps angezeigt werden.

|Feld|Beschreibung|
|--|--|
|**Anzeigeoption**|Wie die Liste der verknüpften Entität angezeigt werden soll. Weitere Informationen: [Anzeigeoptionen](#display-options)|
|**Benutzerdefiniertes Etikett**|Geben Sie den lokalisierbaren Text ein, der anstelle des Pluralnamens verwendenden wird, wenn Sie **Benutzerdefinierte Beschriftung verwenden** als **Anzeigeoption** haben.|
|**Anzeigebereich**|Wählen Sie eine der verfügbaren Gruppierungen aus, um diese Liste anzuzeigen. Die verfügbaren Optionen sind: **Details** (für die Gruppe *Allgemein* ), **Marketing**, **Vertrieb** und **Service**. |
|**Anzeigereihenfolge**|Steuert, wo das Navigationselement in dem ausgewählten Anzeigebereich eingesetzt wird. Der Bereich der zulässigen Zahlen beginnt bei 10.000. Navigationsbereichselemente mit einem niedrigeren Wert werden über anderen Beziehungen mit einem höheren Wert angezeigt.|

<!-- TODO: Not sure whether Display Area or Display Order are still used anymore. Might only be used in the Outlook client?-->

#### <a name="display-options"></a>Anzeigeoption

Dies sind die verfügbaren Anzeigenoptionen:

|Option|Beschreibung|
|--|--|
|**Nicht anzeigen**|Zeigen Sie die verknüpften Entitäten für diese Beziehung an.|
|**Benutzerdefinierte Beschriftung verwenden**|Wenn diese Option ausgewählt ist, wird das Feld **Benutzerdefinierte Beschriftung** aktiviert, damit Sie den lokalisierbaren Text anstelle des Pluralnamens angeben können.|
|**Pluralnamen verwenden**|Hiermit wird der für die verknüpfte Entität definierte Pluralname verwendet.|

### <a name="searchable"></a>Durchsuchbar

Sie können die Beziehung von **Erweiterte Suche** in modellgesteuerten Apps ausblenden, indem Sie das Feld **Durchsuchbar** auf **Nein** festlegen.

## <a name="delete-relationships"></a>Beziehungen löschen

Während [Betrachtungsentitätsbeziehungen](#view-entity-relationships) wählen Sie die Entitätsbeziehung, die Sie löschen möchten und klicken den Befehl ![Löschen](media/delete.gif).

Durch das Löschen der Beziehung wird auch die Beziehungsentität gelöscht. Alle Daten, die Entitäten mit der Beziehung verbinden, gehen verloren.

### <a name="see-also"></a>Siehe auch

[N:N (n:n)-Beziehungen erstellen](create-edit-nn-relationships.md)<br />
[Erstellen von n:n-Entitätsbeziehungen in Common Data Service mithilfe des PowerApps-Portals](create-edit-nn-relationships-portal.md)<br />
[Erstellen oder Bearbeiten von 1: N (eine-zu-vielen) oder N:1 (viele-zu einer)-Entitätsbeziehungen](create-edit-1n-relationships.md)
