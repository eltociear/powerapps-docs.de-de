---
title: Alternativschlüssel mithilfe des Projektmappen-Explorers festlegen | MicrosoftDocs
description: 'Erfahren Sie, wie Alternativschlüssel definiert werden, die verwendet werden können, um Datensätze in Common Data Service for Apps mithilfe des Projektmappen-Explorers zu verweisen'
ms.custom: ''
ms.date: 05/31/2018
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
# <a name="define-alternate-keys-using-solution-explorer"></a>Alternativschlüssel mithilfe des Projektmappen-Explorers festlegen

Projektmappen-Explorer bietet eine Möglichkeit, um Alternativschlüssel für Common Data Service for Apps anzuzeigen und zu erstellen.

[PowerApps-Portal](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) aktiviert das  Konfigurieren der allgemeinen Optionen, jedoch bestimmte Optionen können mithilfe des Lösungs-Explorers nur festgelegt werden. <br />Weitere Informationen: 
- [Definieren von Alternativschlüsseln für den Verweis auf Datensätze](define-alternate-keys-reference-records.md)<br />
- [Alternativschlüssel mithilfe von PowerApps-Portalen festlegen](define-alternate-keys-portal.md)

## <a name="open-solution-explorer"></a>Öffnen Sie den Lösungs-Explorer

Ein Teil des Namens jeder Alternativschlüssel, die Sie erstellen, ist das Anpassungspräfix. Dieser Satz basiert auf dem Lösungsherausgeber für die Lösung, in der Sie arbeiten. Wenn Ihnen das Anpassungspräfix wichtig ist, achten Sie darauf, dass Sie in einer nicht verwalteten Lösung oder der Standardlösung arbeiten, in der das Anpassungspräfix Ihren Wünschen für diese Entität entspricht. Weitere Informationen [Lösungsherausgeberpräfix ändern](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-alternate-keys"></a>Alternativschlüssel anzeigen

1. Mit geöffnetem Projektmappen-Explorer erweitern Sie unter **Komponenten** die Option **Entitäten** und wählen Sie die Entität aus, in der Sie der Alternativschlüssel anzeigen möchten.
2. Erweitern Sie die **Schlüssel** und wählen Sie sie aus.

    ![Alternativschlüssel anzeigen](media/view-alternate-keys-solution-explorer.png)

## <a name="create-an-alternate-key"></a>Erstellen eines Alternativschlüssels

1. Beim [Anzeigen von Alternativschlüsseln](#view-alternate-keys), wählen Sie **Neu** aus.
1. Geben Sie im Formular den **Anzeigenamen** ein Das Feld **Name** wird basierend auf dem Wert in **Anzeigename** automatisch befüllt. 
2. Wählen Sie in der Liste **Verfügbare Attribute** jedes Attribut und dann **Hinzufügen >** aus, um das Attribut in der Liste **Ausgewählte Attribute** zu verschieben.
    ![Erstellen eines Alternativschlüssels](media/create-alternate-key-solution-explorer.png)
1. Wählen Sie **OK** aus, zum das Formular zu schließen.

### <a name="optional-view-the-system-job-tracking-creation-of-indexes"></a>(Optional) Zeigen Sie die Indexerstellung bei der Systemauftragsnachverfolgung an
1. Beim [Anzeigen von Alternativschlüsseln](#view-alternate-keys) wird eine Zeile für den erstellten Schlüssel angezeigt, nachdem Sie einen neuen Alternativschlüssel erstellt haben.
2. In der Spalte **Systemauftrag** finden Sie einen Link zum Systemauftrag, der die Erstellung der Indizes überwacht, um den Alternativschlüssel zu unterstützen. 
    
    Der Systemauftrag hat einen Namen, der diesem Muster folgt: `Create index for {0} for entity {1}` wobei `0` der **Anzeigename** des Alternativschlüssels ist und `1` der Namen der Entität.

    Der Link zum Systemauftrag wird nicht angezeigt, nachdem der Systemauftrag erfolgreich abgeschlossen wurde. Weitere Informationen: [Überwachen und verwalten Sie Systemaufträge](/dynamics365/customer-engagement/admin/monitor-manage-system-jobs)


## <a name="delete-an-alternate-key"></a>Einen Alternativschlüssel löschen

Während dem [Anzeigen von Alternativschlüsseln](#view-alternate-keys) wählen Sie ![Löschen](media/delete.gif) aus.

### <a name="see-also"></a>Siehe auch

[Definieren von Alternativschlüsseln für den Verweis auf Datensätze](define-alternate-keys-reference-records.md)<br />
[Alternativschlüssel mithilfe von PowerApps-Portalen festlegen](define-alternate-keys-portal.md)<br />
[Entwicklerdokumentation: Definieren eines Alternativschlüssels für eine Entität](/dynamics365/customer-engagement/developer/define-alternate-keys-entity)
