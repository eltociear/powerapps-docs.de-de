---
title: Alternativschlüssel mithilfe von PowerApps-Portalen festlegen | MicrosoftDocs
description: 'Erfahren Sie, wie Sie Alternativschlüssel mithilfe von PowerApps-Portalen festlegen'
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
# <a name="define-alternate-keys-using-powerapps-portal"></a>Alternativschlüssel mithilfe von PowerApps-Portalen festlegen

Das [PowerApps-Portal](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) stellt eine einfache Möglichkeit zur Verfügung, Entitätsalternativschlüssel vom Common Data Service for Apps anzuzeigen und zu erstellen.

PowerApps-Portal aktiviert das  Konfigurieren der allgemeinen Optionen, jedoch bestimmte Optionen können nur mithilfe des Lösungs-Explorers festgelegt werden. <br />Weitere Informationen: 
- [Definieren von Alternativschlüsseln für den Verweis auf Datensätze](define-alternate-keys-reference-records.md)
- [Alternativschlüssel mithilfe des Projektmappen-Explorers festlegen](define-alternate-keys-solution-explorer.md)

## <a name="view-alternate-keys"></a>Alternativschlüssel anzeigen

1. In [PowerApps-Portal](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) Wählen Sie **Modell-angetrieben** oder **Canvas** Entwurfsmodus aus.
2. Wählen Sie **Daten** > **Entitäten** und die Entität aus, die Sie anzeigen möchten.
3. Wählen Sie **Schlüssel** aus, um eine Liste der Alternativschlüssel anzuzeigen, die definiert werden.

    ![Alternativschlüssel anzeigen](media/view-alternate-keys-portal.png)

## <a name="create-an-alternate-key"></a>Erstellen eines Alternativschlüssels

1. Während dem [Anzeigen von Alternativschlüsseln](#view-alternate-keys) wählen Sie **Schlüssel hinzufügen** aus.
2. Verwenden Sie den Bereich, um einen **Anzeigenamen** festzulegen und die Felder auszuwählen, um den Alternativschlüssel zu erstellen.

    Das Feld **Name** wird basierend auf dem Wert im Anzeigenamen befüllt.

    ![Beispielhafte Alternativschlüsseldefinition](media/alternate-key-account-number-sic-code.png)

1. Wählen Sie **Fertig** aus, um den Bereich zu schließen.
2. Klicken Sie auf **Entität speichern**, um den Alternativschlüssel zu erstellen.

> [!NOTE]
> Der Alternativschlüssel ist nicht sofort verfügbar. Ein Systemauftrag wird initiiert, wenn Sie die Entität speichern, um Datenbankindizes zu erstellen und den Alternativschlüssel zu unterstützen.

## <a name="delete-an-alternate-key"></a>Einen Alternativschlüssel löschen

Beim [Anzeigen von Alternativschlüsseln](#view-alternate-keys) wählen Sie den Schlüssel, den Sie löschen möchten, und wählen Sie **Schlüssel löschen** in der Befehlsleiste aus.

### <a name="see-also"></a>Siehe auch

[Definieren von Alternativschlüsseln für den Verweis auf Datensätze](define-alternate-keys-reference-records.md)<br />
[Alternativschlüssel mithilfe des Projektmappen-Explorers festlegen](define-alternate-keys-solution-explorer.md)<br />
[Entwicklerdokumentation: Definieren eines Alternativschlüssels für eine Entität](/dynamics365/customer-engagement/developer/define-alternate-keys-entity)
