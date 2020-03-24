---
title: Alternativschlüssel mithilfe von Power Apps-Portal definieren | Microsoft-Dokumentation
description: Weitere Informationen zum Definieren von Alternativschlüsseln mithilfe von Power Apps-Portal
ms.custom: ''
ms.date: 05/31/2018
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
ms.openlocfilehash: b0528015899ccc624fed1d83566c445f348343c9
ms.sourcegitcommit: 2b34de88c977c149e4c632b23d8e816901c15949
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/12/2020
ms.locfileid: "3040433"
---
# <a name="define-alternate-keys-using-power-apps-portal"></a>Alternativschlüssel mithilfe von Power Apps-Portal definieren

Das [Power Apps-Portal](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) stellt eine einfache Möglichkeit zur Verfügung, Entitätsalternativschlüssel mit dem Common Data Service anzuzeigen und zu erstellen.

PowerApps-Portal aktiviert das  Konfigurieren der allgemeinen Optionen, jedoch bestimmte Optionen können nur mithilfe des Lösungs-Explorers festgelegt werden. <br />Weitere Informationen: 
- [Definieren von Alternativschlüsseln für den Verweis auf Datensätze](define-alternate-keys-reference-records.md)
- [Alternativschlüssel mithilfe des Projektmappen-Explorers festlegen](define-alternate-keys-solution-explorer.md)

## <a name="view-alternate-keys"></a>Alternativschlüssel anzeigen

1. Wählen Sie im [Power Apps Portal](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) **Daten** > **Entitäten** und wählen Sie die Entität, die Sie anzeigen möchten.
2. Wählen Sie **Schlüssel** aus, um eine Liste der Alternativschlüssel anzuzeigen, die definiert werden.

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
