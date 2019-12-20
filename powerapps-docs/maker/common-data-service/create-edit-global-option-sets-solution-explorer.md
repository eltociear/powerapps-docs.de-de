---
title: Erstellen und Bearbeiten von globalen Optionssätzen für Common Data Service mithilfe des Projektmappen-Explorers | MicrosoftDocs
ms.custom: ''
ms.date: 05/26/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.author: matp
manager: kvivek
author: Mattp123
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 060d749fe3f8c7f3d2e0870b99a836571c29bd86
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2865913"
---
# <a name="create-and-edit-global-option-sets-for-common-data-service-using-solution-explorer"></a>Erstellen und Bearbeiten von globalen Optionssätzen für Common Data Service mithilfe des Projektmappen-Explorers

Der Projektmappen-Explorer bietet eine Möglichkeit, um globale Optionssätze für Common Data Service zu erstellen und zu bearbeiten.

Das [Power Apps-Portal](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) ermöglicht das Konfigurieren der allgemeinen Optionen, jedoch können bestimmte Optionen nur mithilfe des Projektmappen-Explorers festgelegt werden. <br />Weitere Informationen: 
- [Erstellen und Bearbeiten globaler Optionssätze für Common Data Service](create-edit-global-option-sets.md)
- [Einen Optionssatz erstellen](custom-picklists.md)

## <a name="open-solution-explorer"></a>Öffnen Sie den Lösungs-Explorer

Ein Teil des Namens jedes globalen Optionssatzes, die Sie erstellen, ist das Anpassungspräfix. Dieser Satz basiert auf dem Lösungsherausgeber für die Lösung, in der Sie arbeiten. Wenn Ihnen das Anpassungspräfix wichtig ist, achten Sie darauf, dass Sie in einer nicht verwalteten Lösung oder der Standardlösung arbeiten, in der das Anpassungspräfix Ihren Wünschen für diesen globalen Optionssatz entspricht. Weitere Informationen [Lösungsherausgeberpräfix ändern](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-global-option-sets"></a>Globale Optionssätze anzeigen

Öffnen Sie im Projektmappen-Explorer unter **Komponenten** die Option **Optionssatz**.

![Globale Optionssätze anzeigen](media/view-global-option-sets-solution-explorer.png)

> [!NOTE]
> Einige globale Systemoptionssätze sind nicht anpassbar. Diese Optionen können sich bei neuen Versionen oder Updates ändern, daher wird empfohlen, sie nicht zu verwenden, sofern Sie nicht sicher sind, dass die Anforderungen der Art entsprechen, in der Common Data Service die Werte verwendet.

## <a name="create-a-global-option-set"></a>Erstellen eines globalen Optionssatzes

> [!NOTE]
> Sie müssen keinen globalen Optionssatz erstellen, bevor Sie ihn in einem benutzerdefinierten Feld verwenden. Beim Erstellen eines neuen Optionssatzfelds haben Sie die Möglichkeit, einen neuen globalen Optionssatz zu erstellen oder einen vorhandenen zu verwenden. Siehe [Optionssatzfeldoptionen](create-edit-field-solution-explorer.md#option-set-field-options)

Beim Anzeigen von globalen Optionssätzen klicken Sie auf **Neu**, um ein Formular zu öffnen, um den globalen Optionssatz zu definieren.

![Globalen Optionssatz erstellen](media/create-global-option-set-solution-explorer.png)

Geben Sie einen **Anzeigenamen** ein, der für Benutzer mit der Sicherheitsrolle "Systemadministrator" der der Rolle "Systemanpasser" angezeigt wird, die diesen globalen Optionssatz auswählen, wenn neue Felder definiert werden, die ihn verwenden. Dieser Name ist nicht für Benutzer sichtbar, die Ihre Apps verwenden.

Ein Feldwert **Name** wird basierend auf den **Anzeigenamen** für Sie generiert, den Sie eingeben. Er enthält den Anpassungspräfix für den Lösungsherausgeber im Kontext der Lösung, die Sie verwenden. Sie können den erstellten Anteil des Feldwerts von **Name** ändern, bevor Sie speichern.

Geben Sie eine **Beschreibung** für den globalen Optionssatz ein. 

> [!TIP]
> Verwenden Sie die **Beschreibung**, um den Zweck dieses globalen Optionssatzes zu erläutern. Dieser Wert wird Benutzern der Anwendung nicht angezeigt. Er ist für andere Benutzer mit der Sicherheitsrolle "Systemadministrator" oder "Systemanpasser" gedacht, die wissen möchten, weshalb dieser bestimmte globale Optionssatz erstellt wurde.

### <a name="configure-options"></a>Konfigurieren von Optionen

[!INCLUDE [cc_configure-option-set-options-solution-explorer](../../includes/cc_configure-option-set-options-solution-explorer.md)]

## <a name="edit-a-global-option-set"></a>Bearbeiten eines globalen Optionssatzes

Beim Anzeigen von globalen Optionssätzen wählen Sie den Optionssatz aus, den Sie bearbeiten möchten, um den Bereich zu öffnen, um ihn zu bearbeiten.

Außer dem Ändern des Feldwerts **Name** oder der Nummer **Wert**, die einer Option zugewiesen ist, können Sie beliebige Änderungen vornehmen, die Sie vornehmen können, wenn Sie den globalen Optionssatz erstellen.

[!INCLUDE [cc_remove-option-warning](../../includes/cc_remove-option-warning.md)]

## <a name="delete-a-global-option-set"></a>Löschen eines globalen Optionssatzes

Um einen globalen Optionssatz zu löschen, wenn Sie die Liste anzeigen, wählen Sie die ![Befehl löschen](media/delete.gif) Befehl in der Befehlsleiste.

> [!IMPORTANT]
> Wenn der globale Optionssatz für ein Feld verwendet wurde, können Sie es nicht löschen, bis das Feld gelöscht wurde.
  
### <a name="see-also"></a>Siehe auch
 
[Erstellen und Bearbeiten globaler Optionssätze für Common Data Service](create-edit-global-option-sets.md)<br />
[Einen Optionssatz erstellen](custom-picklists.md)<br />
[Erstellen und Bearbeiten von Feldern](create-edit-fields.md)<br />
[Entwicklerdokumentation: Globale Optionssätze anpassen](/dynamics365/customer-engagement/developer/org-service/customize-global-option-sets).
