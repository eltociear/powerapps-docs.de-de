---
title: Erstellen und Bearbeiten von Entitäten mithilfe des Lösungsexplorer  | MicrosoftDocs
description: Erfahren Sie, wie Sie eine Entität mithilfe des Lösungsexplorers erstellen
ms.custom: ''
ms.date: 05/30/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 7774090950b179e349c6c576439ebd4ad47da67b
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "2883746"
---
# <a name="create-and-edit-entities-using-solution-explorer"></a>Erstellen und Bearbeiten von Entitäten mithilfe des Lösungsexplorer

Sie können Entität mithilfe des Power Apps-Portals für die meisten allgemeinen Situationen einfach erstellen, jedoch nicht alle Funktionen werden dort implementiert. Falls Sie die Bedingungen erfüllen müssen, die in [Entitäten erstellen und bearbeiten Common Data Service](create-edit-entities.md) beschrieben sind, können Sie sie ausführen, indem Sie mithilfe des Lösungs-Explorers Entitäten erstellen oder bearbeiten.

## <a name="open-solution-explorer"></a>Öffnen Sie den Lösungs-Explorer

Ein Teil des Namens jeder benutzerdefinierten Entität, die Sie erstellen, ist das Anpassungspräfix. Dieser Satz basiert auf dem Lösungsherausgeber für die Lösung, in der Sie arbeiten. Wenn Ihnen das Anpassungspräfix wichtig ist, achten Sie darauf, dass Sie in einer nicht verwalteten Lösung oder der Standardlösung arbeiten, in der das Anpassungspräfix Ihren Wünschen für diese Entität entspricht. Weitere Informationen [Lösungsherausgeberpräfix ändern](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-entities"></a>Entitäten anzeigen

Im Lösungs-Explorer-Knoten **Komponenten** wählen Sie den Knoten **Entitäten** aus.

![Entitäten anzeigen im Lösungs-Explorer](media/view-entities-solution-explorer.png)

## <a name="create-an-entity"></a>Erstellen einer Entität

Beim [Entitäten anzeigen](#view-entities) auf der Menüleiste, wählen Sie **Neue Entität** zum Öffnen.

![Neues Entitätsformular im Lösungsexplorer](media/new-entity-form-solution-explorer.png)

Das neue Entitätsformular umfasst zwei Registerkarten. Die Registerkarte **Allgemein** ist für Entitätsoptionen. Die Registerkarte **Hauptfeld** ist für Optionen über das spezielle Textfeld, die jede einzelne Entität hat, die den angezeigten Text definiert, wenn ein Link zum Öffnen der Entität im Suchfeld vorhanden ist.

Weitere Informationen zu jedem Abschnitt finden Sie wie folgt:
- [Hauptfeld konfigurieren](#configure-the-primary-field).
- [Pflichtfelder konfigurieren](#configure-required-fields)

> [!NOTE]
> Sie können aus der Entität eine benutzerdefinierte Aktivität machen. Diese Wahlmöglichkeit ändert einige der Standardoptionswerte. Weitere Informationen: [Benutzerdefinierte Aktivitätsentität erstellen](#create-custom-activity-entity)

Wenn Sie die erforderlichen Optionen für die Entität festgelegt haben, klicken Sie auf !["Speichern"-Befehl](media/save-entity-icon-solution-explorer.png) Erstellen Sie die benutzerdefinierte Entität.

### <a name="configure-the-primary-field"></a>Hauptfeld konfigurieren.

Auf der Registerkarte **Hauptfeld** können Sie die Standardwerte für das primäre Feld jedoch akzeptieren, aber Sie haben die folgenden Optionen:

|Feld   |Beschreibung  |
|---------|---------|
|**Anzeigename**|Geben Sie die lokalisierbare Beschriftung ein, die für das Feld in Formularen und Listen angezeigt wird. Der Standardwert ist **Name**.|
|**Name**|Legen Sie einen Namen fest, der im System für dieses Feld verwendet wurde. Der Standardwert ist `<customization prefix>_name`.|
|**Maximale Länge**|Geben Sie die maximale Länge für diesen Feldwert ein. Der Standard ist 100.|

> [!NOTE]
> Diese Optionen treffen nicht zu, wenn die Entität eine Aktivitätsentität ist. Weitere Informationen: [Benutzerdefinierte Aktivitätsentität erstellen](#create-custom-activity-entity)

### <a name="configure-required-fields"></a>Pflichtfelder konfigurieren

In der Registerkarte **Allgemein** sind einige Optionen erforderlich, damit Sie die Entität speichern können.

|Feld   |Beschreibung  |
|---------|---------|
|**Anzeigename**|Dies ist der Name im Singular für die Entität, die in der App angezeigt wird.<br />Dieses Limit kann später geändert werden.|
|**Pluralname**|Dies ist der Name im Plural für die Entität, die in der App angezeigt wird.<br />Dieses Limit kann später geändert werden.|
|**Name**|Dieses Feld wird basierend auf dem von Ihnen eingegebenen Anzeigenamen vorab ausgefüllt. Es enthält das Anpassungspräfix des Lösungsherausgebers.|
|**Besitz**|Sie können eine benutzer-/team-eigene oder eine organisationseigene Entität wählen. Weitere Informationen finden Sie unter [Entitätsbesitz](types-of-entities.md#entity-ownership).|

## <a name="edit-an-entity"></a>Bearbeiten einer Entität

Unter [Betrachtungsentitäten](#view-entities), wählen Sie die Entität aus, oder fahren mit dem Bearbeiten einer neuen Entität fort, die Sie gerade gespeichert haben.

> [!NOTE]
> Standard-Informationsstrukturen oder benutzerdefinierte Entitäten, die Teil einer verwalteten Lösung sind, haben möglicherweise Einschränkungen auf Änderungen, die Sie haben können. Wenn die Option nicht verfügbar sind oder deaktiviert wird, dürfen Sie keine Änderungen vornehmen.

#### <a name="set-once-options"></a>Optionen einmal festlegen

Folgende Optionen können einmal festgelegt werden und können nicht geändert werden nachdem sie  festgelegt wurden. Legen Sie diese Optionen nur fest, wenn Sie sie benötigen.

<!-- 
Same data is presented in edit-entities.md
Both should point to this include
 -->
[!INCLUDE [cc_entity-set-once-options-table](../../includes/cc_entity-set-once-options-table.md)]

#### <a name="options-that-you-can-change"></a>Optionen, die Sie ändern können

Die folgenden Eigenschaften können jederzeit geändert werden.

<!-- 
Same data is presented in edit-entities.md
Both should point to this include
 -->
[!INCLUDE [cc_entity-changeable-options-table](../../includes/cc_entity-changeable-options-table.md)]

Die folgenden Typen von Änderungen können vorgenommen werden:
- [Erstellen und Bearbeiten von Feldern für Common Data Service](create-edit-fields.md)
- [Erstellen und Bearbeiten von Beziehungen zwischen Entitäten](create-edit-entity-relationships.md)
- [Formulare erstellen und gestalten](../model-driven-apps/create-design-forms.md)
- [Einen neuen Geschäftsprozessfluss erstellen, um Prozesse zu standardisieren](/flow/create-business-process-flow)

## <a name="delete-an-entity"></a>Löschen einer Entität

Als Benutzer mit der Sicherheitsrolle "Systemadministrator" können Sie benutzerdefinierte Entitäten löschen, die nicht Teil einer verwalteten Lösung sind.  
  
> [!IMPORTANT]
>  Wenn Sie eine benutzerdefinierte Entität löschen, werden die Datenbanktabellen, die Daten für diese Entität speichern, gelöscht, und alle enthaltenen Daten gehen verloren. Alle zugeordneten Datensätze mit einer hierarchischen Beziehung zu der benutzerdefinierten Entität werden ebenfalls gelöscht. Weitere Informationen über hierarchische Beziehungen finden Sie unter [Erstellen und Bearbeiten von Entitätsbeziehungen](create-edit-entity-relationships.md).  
  
> [!NOTE]
> Die einzige Möglichkeit, Daten aus einer Entität wiederherzustellen, die entfernt wurde, besteht darin, die Datenbank von einem Zeitpunkt wiederherzustellen, bevor die Entität gelöscht wurde. Weitere Informationen finden Sie unter [Sicherung und Wiederherstellung von Instanzen.](/dynamics365/customer-engagement/admin/backup-restore-instances)

Bei [Betrachtungsentitäten](#view-entities), klicken Sie auf den Befehl ![Löschenl](media/delete.gif) auf der Symbolleiste.

Beim Anzeigen einer Entitätsverwendung nutzen Sie den Löschbefehl auf der Menüleiste.

![Befehl löschen](media/delete-custom-entity-solution-explorer.png)

> [!WARNING]
> Eine Entität löschen, die Daten enthalten, löscht alle Daten. Diese Daten können nur durch die Sicherung der Datenbank abgerufen werden.

> [!NOTE]
> Falls Entitätsabhängigkeiten vorhanden sind, wird eine Fehlermeldung **Die Komponente kann nicht gelöscht werden.** mit einem **Detail** Link gesendet, die Sie verwenden können, um herauszufinden,  weshalb die Entität nicht gelöscht werden kann. In den meisten Fällen ist dies bei einer Abhängigkeit, die entfernt werden soll. 
>
> Möglicherweise sind mehrere Abhängigkeit, die das Löschen einer Entität blockieren. Diese Fehlermeldung zeigt möglicherweise nur die ersten an. Eine andere Methode ermittelt Abhängigkeiten zu entdecken, finden Sie unter [Ermitteln Sie Entitätsabhängigkeiten](#identify-entity-dependencies)



### <a name="identify-entity-dependencies"></a>Entitätsabhängigkeiten gefunden

Sie können Abhängigkeiten identifizieren, die verhindern, dass eine Entität gelöscht wird, bevor Sie versuchen, diese zu löschen. 

1. Klicken Sie im Lösungs-Explorer mit der ausgewählten Entität, klicken Sie auf **Abhängigkeiten anzeigen** in der Befehlsleiste.

![Abhängigkeitsbefehl anzeigen](media/entity-show-dependencies.png)

2. Im Dialog, der geöffnet wird, gehen Sie zu der Liste rechts, um **Abhängigkeitstyp** anzuzeigen.

![Veröffentlichter Abhängigkeitstyp](media/published-entity-dependency.png)

**Veröffentlicht** Abhängigkeiten sperren das Löschen einer Entität. **Intern** Abhängigkeiten sollten vom System aufgelöst werden.  

3. Entfernen Sie diese veröffentlichten Abhängigkeiten und Sie sollten in der Lage sein, die Entität zu löschen.

 > [!NOTE]
 > Eine sehr häugige Abhängigkeit ist, dass ein anderes Entitätsformular über ein Suchfeld für die Entität verfügt, die Sie löschen. Dieses Suchfeld aus dem Formular wird die Abhängigkeit auflösen.

## <a name="create-custom-activity-entity"></a>Erstellen einer benutzerdefinierten Aktivitätsentität

Um die Entität als Aktivitätsentität zu erstellen, können Sie dieselben Schritte ausführen, die in diesem Thema beschriebenen sind, außer **Als Aktivitätsentität definieren**.

![Als Aktivitätsentität definieren](media/create-activity-entity-solution-explorer.png)

Die Aktivitätsentität ist eine spezielle Art von Entität, die Aktionen nachverfolgt, für die ein Eintrag in einem Kalender vorgenommen werden kann. Mehr Informationen: [Aktivitäten-Entitäten](types-of-entities.md#activity-entities).

Wenn Sie diese Option festlegen, sind einige Entitätseigenschaften nicht kompatibel. Die Aktivitätsentität muss sich an die standardmäßigen Verhalten anpassen, die alle Entitäten verwenden.

Das primäre Feld **Name** und **Anzeigename** wird auf **Betreff** festgelegt und Sie können dies nicht ändern.

Folgende Optionen sind standardmäßig festgelegt und können nicht mehr geändert werden:

 - **Feedback**
 - **Notizen (enthält Anlagen)**
 - **Verbindungen**
 - **Warteschlangen**
 - **Offlinefunktionen für Dynamics 365 for Outlook**

Folgende Optionen können nicht festgelegt werden:

- **Bereiche, in denen diese Entität angezeigt wird**
- **Aktivitäten**
- **E-Mail wird gesendet**
- **Seriendruck**
- **Einzelne Datensatzüberwachung**
- **Mehrere Datensatzüberwachung**

## <a name="create-a-virtual-entity"></a>Eine virtuelle Entität erstellen

Einige Optionen werden nur verwendet, falls eine virtuelle Entität erstellt wird.

|Option   |Beschreibung  |
|---------|---------|
|**Virtuelle Entität**|Gibt an, ob die Entität eine virtuelle Entität ist.|
|**Datenquelle**|Die Datenquelle für die Entität.|

Mehr Informationen: [Erstellen und Bearbeiten von virtuellen Entitäten, die Daten aus einer externen Datenquelle enthalten](create-edit-virtual-entities.md)

### <a name="see-also"></a>Siehe auch
[Entitäten erstellen und bearbeiten in Common Data Service](create-edit-entities.md)<br />
[Tutorial: Erstellen Sie eine benutzerdefinierte Entität, die Komponenten in Power Apps enthält](/powerapps/maker/common-data-service/create-custom-entity)<br />
[Erstellen einer Lösung](create-solution.md)
