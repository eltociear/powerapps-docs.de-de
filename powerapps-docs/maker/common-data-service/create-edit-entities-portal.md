---
title: Entitäten mit dem Power Apps-Portal erstellen und bearbeiten | Microsoft-Dokumentation
description: Entitäten mit dem Power Apps-Portal erstellen und bearbeiten
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
ms.assetid: fa04f99d-a5f9-48cb-8bfb-f0f50718ccee
caps.latest.revision: 41
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 199399fe75103df2d8fde902d54a803ec56fc395
ms.sourcegitcommit: 2b34de88c977c149e4c632b23d8e816901c15949
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/12/2020
ms.locfileid: "3040565"
---
# <a name="create-and-edit-entities-using-power-apps-portal"></a>Entitäten mit dem Power Apps-Portal erstellen und bearbeiten

Das [Power Apps-Portal](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) stellt eine einfache Möglichkeit zur Verfügung, Entitätsfelder mit dem Common Data Service zu erstellen und zu bearbeiten.

PowerApps-Portal aktiviert das  Konfigurieren der allgemeinen Optionen, jedoch bestimmte Optionen können nur mithilfe des Lösungs-Explorers festgelegt werden. Weitere Informationen: 
- [Entitäten erstellen und bearbeiten in Common Data Service](create-edit-entities.md)
- [Erstellen und Bearbeiten von Entitäten mithilfe des Lösungsexplorer](create-edit-entities-solution-explorer.md)

## <a name="view-entities"></a>Entitäten anzeigen

1. Wählen Sie auf dem [Power Apps Portal](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) **Daten** > **Entitäten**.

![Entitäten anzeigen](media/view-entities-portal.png)

Sie können die Entitäten filtern, die Sie mit der folgenden Ansichten in einer Liste sehen: 

![Entitätsansichten](media/entity-views-portal.png)

 |Ansicht|Beschreibung|
 |--|--|
 |**Alle**| Zeigt alle Entitäten an|
 |**Verwaltet**| Zeigt nur verwaltete und Standard-Entitäten an|
 |**Benutzerdefiniert**|Zeigt nur benutzerdefinierte Entitäten an|
 |**Standard**|Zeigt nur die Standard-Entitäten |

Sie können auch **Gruppe** auswählen, um Entitäten nach **Tags** zu gruppieren, die dazu angewendet werden.

## <a name="create-an-entity"></a>Erstellen einer Entität

Beim [Entitäten anzeigen](#view-entities) auf der Menüleiste, wählen Sie **Neue Entität**. Dadurch wird der neue Entitätsbereich geöffnet.

![Neuer Entitätsbereich](media/new-entity-panel.png)

Geben Sie Daten in die folgenden Felder ein:

|Feld|Beschreibung|
|--|--|
|**Anzeigename**|Dies ist der Name im Singular für die Entität, die in der App angezeigt wird. Dieses Limit kann später geändert werden.|
|**Plural-Anzeigename**|Dies ist der Name im Plural für die Entität, die in der App angezeigt wird. Dieses Limit kann später geändert werden.|
|**Name**|Dieses Feld wird basierend auf dem von Ihnen eingegebenen **Anzeigenamen** vorab ausgefüllt. Es enthält das Anpassungspräfix des Common Data Service-Lösungsherausgebers. Eine spätere Änderung ist nach dem Speichern der Entität nicht möglich.|
|**Primärname**|Dies ist das einzige an dieser Stelle sichtbare Feld.| Bearbeiten Sie es, wenn Sie den **Anzeigename**oder **Name** des Feldes ändern möchten.
|**Anzeigename**|Dies ist der wichtigste benutzerfreundliche Textbezeichner für Ihren Datensatz (normalerweise ein Name oder eine Nummer). Der Wert dieses Feldes wird den Benutzern angezeigt, wenn sie aus einer Liste von Datensätzen auswählen müssen.
|**Name**|Dieses Feld wird basierend auf dem von Ihnen eingegebenen **Anzeigenamen** vorab ausgefüllt. Es enthält das Anpassungspräfix des Common Data Service-Lösungsherausgebers. Eine spätere Änderung ist nach dem Speichern der Entität nicht möglich.|

Wählen Sie **Anhänge** aktivieren, um Notizen und Dateien an Datensätze für diese Entität anzuhängen.

Wählen Sie **Weitere Einstellungen**. Diese Einstellungen sind für eine Entität optional.

|Feld|Beschreibung|
|--|--|
|**Beschreibung**|Geben Sie eine aussagekräftige Beschreibung des Entitätszwecks ein.|
|**Entitätstyp und Eigentümer**|Schalten Sie den Entitätstyp auf Aktivitätsentität um, um Entitäten anzulegen, die Aufgaben verwalten können. Der Typ **Eigentümer** definiert, wer Operationen auf einem Datensatz durchführen kann.|
|**Zusammenarbeit**|Aktivieren Sie Funktionen, die den Benutzern die Zusammenarbeit an dieser Entität erleichtern.|
|**Einstellungen erstellen und aktualisieren**|Sie können die schnelle Erstellung von Formularen aktivieren, um Ihrer Anwendung eine optimierte Dateneingabe zu ermöglichen. Mit der Dublettenerkennung können Sie Richtlinien für die Dublettenerkennung festlegen und Regeln für die Dublettenerkennung erstellen. Die Änderungsverfolgung bietet eine Möglichkeit, die Daten performant zu synchronisieren.|
|**Dynamics 365 for Outlook**|Konfigurieren Sie, wie diese Entität in Outlook angezeigt wird.|

Wählen Sie **Erstellen** um fortzufahren. Dadurch wird das Fenster **Neue Entität** geschlossen und die Liste der Felder angezeigt.

Das Feld **Primärname** der Entität wird in der Liste der Felder angezeigt. Aktivieren Sie das Kontrollkästchen **Primärer Name**, um ihn zu bearbeiten, wenn Sie **Anzeigename** oder **Name** im Feld ändern möchten. Die Werte sind standardmäßig und unten angezeigt:

![Name für Primärbereich](media/primary-name-panel.png)

## <a name="edit-an-entity"></a>Entität bearbeiten

Während dem [Anzeigen von Feldern](#view-entities) klicken Sie auf das Feld, das Sie bearbeiten möchten.

Wählen Sie **Einstellungen** aus dem Menü, wenn Sie den **Anzeigename**, **Pluraler Anzeigename** oder **Beschreibung** für die Entität bearbeiten möchten.

![Entitätseinstellungen](media/entity-settings-portal.png)

Für andere Elemente wählen Sie aus den Registerkarten.

### <a name="fields"></a>Felder

Siehe [Felder anlegen und bearbeiten](create-edit-fields.md)

### <a name="relationships"></a>Beziehungen

Vgl. [Erstellen und Bearbeiten von Beziehungen zwischen Entitäten](create-edit-entity-relationships.md)

### <a name="business-rules"></a>Geschäftsregeln

Vgl.[Erstellen von Geschäftsregeln und Empfehlungen zur Anwendung einer Logik in einem Formular](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md)

### <a name="views"></a>Ansichten

Vgl [Erstellen oder Bearbeiten einer öffentlichen Ansicht](../model-driven-apps/create-edit-views.md)

### <a name="forms"></a>Formulare

Vgl. [Formulare erstellen und gestalten](../model-driven-apps/create-design-forms.md)

### <a name="dashboards"></a>Dashboards

Vgl.[Dashboards erstellen oder bearbeiten](../model-driven-apps/create-edit-dashboards.md)

### <a name="charts"></a>Diagramme

Vgl. [Systemdiagramm löschen](../model-driven-apps/create-edit-system-chart.md)

### <a name="keys"></a>Schlüssel

Vgl. [Definieren von Alternativschlüsseln für den Verweis auf Datensätze](define-alternate-keys-reference-records.md)

### <a name="data"></a>Daten

Zeigen Sie die Daten in der Entität an.
Verwenden Sie das Menü **Ansicht auswählen**, um die verfügbaren Ansichten für die Entität auszuwählen oder alle Felder anzuzeigen.

![Ansicht auswählen](media/entity-data-select-view.png)

Mithilfe der Befehle **Nächste Seite** und **Vorherige Seite** unten im Formular, mehr Daten anzuzeigen.

## <a name="delete-an-entity"></a>Löschen einer Entität

Als Benutzer mit der Sicherheitsrolle "Systemadministrator" können Sie benutzerdefinierte Entitäten löschen, die nicht Teil einer verwalteten Lösung sind.  
  
> [!IMPORTANT]
>  Wenn Sie eine benutzerdefinierte Entität löschen, werden die Datenbanktabellen, die Daten für diese Entität speichern, gelöscht, und alle enthaltenen Daten gehen verloren. Alle zugeordneten Datensätze mit einer hierarchischen Beziehung zu der benutzerdefinierten Entität werden ebenfalls gelöscht. Weitere Informationen über hierarchische Beziehungen finden Sie unter [Erstellen und Bearbeiten von Entitätsbeziehungen](create-edit-entity-relationships.md).  
  
> [!NOTE]
> Die einzige Möglichkeit, Daten aus einer Entität wiederherzustellen, die entfernt wurde, besteht darin, die Datenbank von einem Zeitpunkt wiederherzustellen, bevor die Entität gelöscht wurde. Weitere Informationen finden Sie unter [Sicherung und Wiederherstellung von Instanzen.](/dynamics365/customer-engagement/admin/backup-restore-instances)

Wenn Sie [Entitäten](#view-entities) ansehen, wählen Sie die Entität aus und wählen Sie **Entität löschen** aus dem Menü.

![Löschen einer Entität mithilfe des Power Apps-Portals](media/delete-entity-powerapps-portal.png)

Wenn die Entität Abhängigkeiten hat, die das Löschen verhindern, wird eine Fehlermeldung angezeigt. Um Abhängigkeiten zu identifizieren und zu entfernen, müssen Sie den Lösungs-Explorer verwenden. Weitere Informationen [Ermitteln Sie Entitätsabhängigkeiten](create-edit-entities-solution-explorer.md#identify-entity-dependencies)

### <a name="see-also"></a>Siehe auch

[Entitäten erstellen und bearbeiten in Common Data Service](create-edit-entities.md)<br />
[Erstellen und Bearbeiten von Entitäten mithilfe des Lösungsexplorer](create-edit-entities-solution-explorer.md)


