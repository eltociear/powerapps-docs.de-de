---
title: Umleiten zu einer neuen URL in einem Portal | MicrosoftDocs
description: Anweisungen zum Erstellen einer Umleitungs-URL, um einen Benutzer an eine andere Seite eines Standorts umzuleiten.
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
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553415"
---
# <a name="add-a-redirect-url-to-a-new-url-on-a-portal"></a>Hinzufügen einer Umleitungs-URL zu einer neuen URL in einem Portal

Kunden möchten häufig über eine einfache URL verfügen, die zu einer Seite weitergeleitet wird, oder Sie möchten zulassen, dass eine ältere URL für die Website verwendet wird, und automatisch zu einer neuen URL auf der Website umgeleitet werden. Mit Seiten Umleitungen kann ein Inhalts Autor eine URL angeben, die bei Bedarf permanent oder temporär an eine bestimmte Webseite oder Webdatei umgeleitet wird. Diese Umleitungs-URLs werden getrennt vom Seiten Inhalt verwaltet, sodass Sie nicht direkt in die Webhierarchie passen.

## <a name="create-a-redirect"></a>Umleitung erstellen

1. Öffnen Sie die [Portal Verwaltungs-App](configure-portal.md).

2. Wechseln Sie zu den **Portalen** > **Website** > **Umleitungen**.

3. Wählen Sie **neu**aus.

4. Geben Sie die Umleitungs Informationen wie unten beschrieben ein.

| Name        | Beschreibung                                                                                                                                  |
|-------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| Name        | Der Anzeige Name der Umleitung. (Kann etwas sein. Leicht zu erkennen.)                                                              |
| Website     | Die Website, der die Umleitung zugeordnet ist. (Die Website, von der der Benutzer umgeleitet wird.)                                                         |
| Eingehende URL | Die partielle URL, die umgeleitet werden soll. (Die Seite, von der der Benutzer umgeleitet wird.)                                                            |
| Status Code | Eines der folgenden: **302 (temporäre Umleitung)** : gibt einen temporären Umleitungs Status zurück. Dies ist die Standardeinstellung.                                               -   **301 (permanente Umleitung)** : gibt einen permanenten Umleitungs Status zurück, der angibt, dass die Ressource permanent verschoben wurde.                          |
| Urne         | Eine externe ZielURL, zu der umgeleitet werden soll. (Verwenden Sie diesen Wert, wenn der Benutzer zu einem Link umgeleitet wird, der sich außerhalb der oben angegebenen Website befindet.)                            |
| Webseite    | Eine interne Zielwebseite, zu der umgeleitet werden soll. (Verwenden Sie diesen Wert, wenn der Benutzer zu einer Seite weitergeleitet wird, die für die oben angegebene Website intern ist.) |
| Standort Markierung | Ein interner Ziel Standort Marker, an den umgeleitet werden soll.                                                                                           |

4. Nachdem Sie die erforderlichen Felder eingegeben und einen Wert für mindestens eine der Felder URL, Web Page oder Site Marker angegeben haben, wählen Sie **Speichern**aus.

    ![Umleiten einer Kundenumfrage](../media/redirect-customer-survey.png "Umleiten einer Kundenumfrage")  

## <a name="use-the-redirect"></a>Umleitung verwenden

Wenn die eingehende URL angefordert wird, wird der Browser an die URL der Zielwebseite für den entsprechenden Umleitungs Eintrag umgeleitet.

Beispiel: für einen eingehenden URL-Wert von CS-Survey, bei dem eine Zielwebseite auf die Seite Kunden Support Umfrage festgelegt ist, wird die folgende Anforderung angezeigt:

https://customerportal.contoso.com/cs-survey

führt dazu, dass der Browser die folgende URL anfordert:

https://customerportal.contoso.com/surveys/customer-service-survey/

