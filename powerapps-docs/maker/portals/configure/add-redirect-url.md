---
title: Umleiten zu einer neuen URL auf einem Portal | MicrosoftDocs
description: Anweisungen zum Erstellen einer Umleitungs-URL, um einen Benutzer an eine andere Seite in einer Seite umzuleiten.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 63cec47042cee4c29e225f33f1678261da3a01ca
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2760438"
---
# <a name="add-a-redirect-url-to-a-new-url-on-a-portal"></a>Hinzufügen einer Umleitungs-URL zu einer neuen URL auf einem Portal

Häufig möchten Kunden eine einfache URL, die auf eine tiefere Seite der Website umleitet, oder sie möchten eine ältere URL mit der Website verwenden und automatisch auf eine neuen URL der Website umleiten. Seitenumleitungen ermöglichen einem Inhaltsersteller die Angabe einer URL, die permanent oder temporär auf eine bestimmte Webseite oder Webdatei umleitet. Diese Umleitungs-URLs werden separat vom Seiteninhalte verwaltet. So müssen Sie nicht in die Webhierarchie passen.

## <a name="create-a-redirect"></a>Erstellen einer Umleitung

1. Öffnen Sie die [Portalverwaltungs-App](configure-portal.md).

2. Gehen Sie zu **Portale** > **Website** > **Umleitungen**.

3. Wählen Sie **Neu** aus.

4. Geben Sie die Umleitungsinformationen wie unten beschrieben ein.

| Name        | Beschreibung                                                                                                                                  |
|-------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| Name        | Der Anzeigename der Umleitung. (Beliebig, Zur einfachen Identifizierung.)                                                              |
| Website     | Die Website, der die Umleitung zugeordnet ist. (Die Website, von der der Benutzer umgeleitet wird.)                                                         |
| Eingehende URL | Die Teil-URL, die umleiten werden soll. (Die Seite, von der der Benutzer umgeleitet wird.)                                                            |
| Statuscode | Einer der folgenden Werte:  **302 (Temporary Redirect)**: gibt einen temporären Umleitungsstatus zurück. Dies ist die Standardeinstellung.                                               -   **301 (Permanente Umleitung)**: gibt einen permanenten Umleitungsstatus zurück, der anzeigt, dass die Ressource endgültig gelöscht wurde.                          |
| URL         | Ein externe Ziel-URL, auf die umgeleitet wird. (Verwenden Sie diese Option, wenn der Benutzer auf einen für die obengenannte Website externen Link umgeleitet wird.)                            |
| Webseite    | Eine interne Ziel-Webseite, an die umgeleitet wird. (Verwenden Sie diese Option, wenn der Benutzer auf eine oben angegebene interne Website umgeleitet wird.) |
| Websitemarkierung | Ein interner Website-Marker, an den umgeleitet wird.                                                                                           |

4. Nachdem Sie die Pflichtfelder ausgefüllt und einen Wert für mindestens eine URL, Webseite oder ein Site-Marker-Feld eingegeben haben, klicken Sie auf **Speichern**.

    ![Leiten Sie eine Kundenumfrage um](../media/redirect-customer-survey.png "Leiten Sie eine Kundenumfrage um")  

## <a name="use-the-redirect"></a>Nutzung der Umleitung

Wenn die eingehende URL angefordert wird, wird der Browser auf die URL der Zielwebseite des passenden Umleitungseintrags umgeleitet.

Wenn beispielsweise eine eingehende URL den Wert cs-survey und die Zielwebseite Customer Support Survey hat, dann wird die folgenden Anforderung:

https://customerportal.contoso.com/cs-survey

im Browser auf die folgende URL umgeleitet:

https://customerportal.contoso.com/surveys/customer-service-survey/

