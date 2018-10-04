---
title: Erstellen und Bearbeiten von globalen Optionssätzen für Common Data Service for Apps mit Projekt-Explorer | MicrosoftDocs
ms.custom: ''
ms.date: 05/26/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
ms.author: matp
manager: brycho
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-and-edit-global-option-sets-for-common-data-service-for-apps-using-solution-explorer"></a>Erstellen und Bearbeiten von globalen Optionssätzen für Common Data Service for Apps mit Projekt-Explorer

Der Projektmappen-Explorer bietet eine Möglichkeit zur Erstellung globale Optionssätze für Common Data Service for Apps mithilfe von Common Data Service for Apps.

[PowerApps-Portal](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) aktiviert das  Konfigurieren der allgemeinen Optionen, jedoch bestimmte Optionen können mithilfe des Lösungs-Explorers nur festgelegt werden. <br />Weitere Informationen: 
- [Erstellen und Bearbeiten von globalen Optionssätzen für Common Data Service für Apps](create-edit-global-option-sets.md)
- [Einen Optionssatz erstellen](custom-picklists.md)

## <a name="open-solution-explorer"></a>Öffnen Sie den Lösungs-Explorer

Ein Teil des Namens jedes globalen Optionssatzes, die Sie erstellen, ist das Anpassungspräfix. Dieser Satz basiert auf dem Lösungsherausgeber für die Lösung, in der Sie arbeiten. Wenn Ihnen das Anpassungspräfix wichtig ist, achten Sie darauf, dass Sie in einer nicht verwalteten Lösung oder der Standardlösung arbeiten, in der das Anpassungspräfix Ihren Wünschen für diesen globalen Optionssatz entspricht. Weitere Informationen [Lösungsherausgeberpräfix ändern](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-global-option-sets"></a>Globale Optionssätze anzeigen

Öffnen Sie im Projektmappen-Explorer unter **Komponenten** die Option **Optionssatz**.

![Globale Optionssätze anzeigen](media/view-global-option-sets-solution-explorer.png)

> [!NOTE]
> Einige globale Systemoptionssätze sind nicht anpassbar. Diese Optionen können sich bei neuen Versionen oder Updates ändern, daher wird empfohlen, sie nicht zu verwenden, sofern Sie nicht sicher sind, dass die Anforderungen der Art entsprechen, in der CDS for Apps die Werte verwendet.

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
 
[Erstellen und Bearbeiten von globalen Optionssätzen für Common Data Service für Apps](create-edit-global-option-sets.md)<br />
[Einen Optionssatz erstellen](custom-picklists.md)<br />
[Erstellen und Bearbeiten von Feldern](create-edit-fields.md)<br />
[Entwicklerdokumentation: Globale Optionssätze anpassen](/dynamics365/customer-engagement/developer/org-service/customize-global-option-sets).