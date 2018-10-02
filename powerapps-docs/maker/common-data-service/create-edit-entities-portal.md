---
title: Entitäten mit dem PowerApps-Portal erstellen und bearbeiten | MicrosoftDocs
description: Entitäten mit dem PowerApps-Portal erstellen und bearbeiten
ms.custom: ''
ms.date: 05/30/2018
ms.reviewer: ''
ms.service: crm-online
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
---

# <a name="create-and-edit-entities-using-powerapps-portal"></a>Entitäten mit dem PowerApps-Portal erstellen und bearbeiten

Das [PowerApps-Portal](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) stellt eine einfache Möglichkeit zur Verfügung, Felder vom Common Data Service für Apps zu erstellen und zu bearbeiten.

PowerApps-Portal aktiviert das  Konfigurieren der allgemeinen Optionen, jedoch bestimmte Optionen können nur mithilfe des Lösungs-Explorers festgelegt werden. Weitere Informationen: 
- [Erstellen und bearbeiten Sie Entitäten in Common Data Service for Apps | MicrosoftDocs](create-edit-entities.md)
- [Erstellen und Bearbeiten von Entitäten mithilfe des Lösungsexplorer](create-edit-entities-solution-explorer.md)

## <a name="view-entities"></a>Entitäten anzeigen

1. In [PowerApps-Portal](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) Wählen Sie **Modell-angetrieben** oder **Canvas** Entwurfsmodus aus.
2. Wählen Sie **Daten** > **Entitäten** aus.

![Entitäten anzeigen](media/view-entities-portal.png)

Sie können die Entitäten filtern, die Sie mit der folgenden Ansichten in einer Liste sehen: 

![Entitätsansichten](media/entity-views-portal.png)

 |Ansicht|Beschreibung|
 |--|--|
 |**Alle**| Zeigt alle Entitäten an|
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
|**Name**|Dieses Feld wird basierend auf dem von Ihnen eingegebenen **Anzeigenamen** vorab ausgefüllt. Es enthält das Anpassungspräfix des CDS Lösungsherausgebers. Eine spätere Änderung ist nach dem Speichern der Entität nicht möglich.|
|**Beschreibung**|Geben Sie eine aussagekräftige Beschreibung des Zwecks der Entität ein.|

Wählen Sie **Weiter**, um fortzufahren, dadurch wird der Bereich **Neue Entität** beendet und die Liste der Felder angezeigt.

Das Feld **Primärer Name** ist das einzige Feld, das zu einem späteren Zeitpunkt angezeigt wird. Aktivieren Sie das Kontrollkästchen **Primärer Name**, um ihn zu bearbeiten, wenn Sie **Anzeigename** oder **Name** im Feld ändern möchten. Die Werte sind standardmäßig und unten angezeigt:

![Name für Primärbereich](media/primary-name-panel.png)

Wählen Sie **Entität speichern**, um die Entität zu erstellen oder weiter zu bearbeiten.

![Die Entität speichern.](media/save-entity-portal.png)

## <a name="edit-an-entity"></a>Bearbeiten einer Entität

Während dem [Anzeigen von Feldern](#view-entities) klicken Sie auf das Feld, das Sie bearbeiten möchten.

Wählen Sie die Einstellungen im Menü , wenn Sie **Anzeigename**, **Mehrzahl- Anzeigename** oder **Beschreibung** für die Entität verwenden möchten.

![Entitätseinstellungen](media/entity-settings-portal.png)

Für andere Elemente wählen Sie aus den Registerkarten.

### <a name="fields"></a>Felder

Vgl. [Erstellen und Bearbeiten von Feldern](create-edit-fields.md)

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

Unter [Betrachtungsentitäten](#view-entities) wählen Sie die Entität, und wählen **Löschungsentität** aus dem Menü oder dem Kontextmenü.

![Löschen einer Entität mithilfe des PowerApps-Portals](media/delete-entity-powerapps-portal.png)

Wenn die Entität Abhängigkeiten hat, die das Löschen verhindern, wird eine Fehlermeldung angezeigt. Um Abhängigkeiten zu identifizieren und zu entfernen, müssen Sie den Lösungs-Explorer verwenden. Weitere Informationen [Ermitteln Sie Entitätsabhängigkeiten](create-edit-entities-solution-explorer.md#identify-entity-dependencies)

### <a name="see-also"></a>Siehe auch

[Erstellen und bearbeiten Sie Entitäten in Common Data Service for Apps | MicrosoftDocs](create-edit-entities.md)<br />
[Erstellen und Bearbeiten von Entitäten mithilfe des Lösungsexplorer](create-edit-entities-solution-explorer.md)


