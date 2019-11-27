---
title: Häufig gestellte Fragen | Microsoft Docs
description: Häufig gestellte Fragen in PowerApps Portalen.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 810829b58d666b66bd2cac7235d013a4bfdcd806
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2759862"
---
# <a name="powerapps-portals-faq"></a>PowerApps Portale-FAQs

Damit Sie eine schnelle Übersicht erhalten, haben wir eine Liste mit häufig gestellten Fragen sowie kurze Antworten zusammengestellt, damit Sie schnell Ihre Informationen erhalten können.

## <a name="im-getting-an-error-that-only-one-portal-can-be-created"></a>Ich erhalte einen Fehler, dass nur ein Portal erstellt werden kann.

Derzeit können Sie in einer Umgebung pro Sprache nur ein Portal pro Typ erstellen. Wenn Sie versuchen, mehr als ein Portal anzulegen, erhalten Sie eine Fehlermeldung wie folgt:

> [!div class=mx-imgBorder]
> ![Maximal erstellter Portalfehler](media/portal-max-error.png "Maximal erstellter Portalfehler")

Um weitere Portale zu erstellen, müssen Sie eine neue Umgebung über den Link **Neue Umgebung erstellen** in der Fehlermeldung erstellen. Weitere Informationen zum Anlegen eines Portale finden Sie unter [Ein Portal anlegen](create-portal.md).

## <a name="im-getting-an-error-that-i-cant-delete-my-portal"></a>Ich erhalte einen Fehler, dass ich mein Portal nicht löschen kann.

Wenn Sie nicht über ausreichende Berechtigungen zum Löschen eines Portale verfügen, wird ein Fehler wie folgt angezeigt:

> [!div class=mx-imgBorder]
> ![Löschen des Portalfehlers](media/portal-delete-error.png "Löschen des Portalfehlers")

Informationen zum Löschen eines Portale und der erforderlichen Berechtigungen finden Sie unter [Löschen eines Portale](manage-existing-portals.md#delete).

## <a name="im-getting-an-error-that-i-cant-create-a-portal"></a>Ich erhalte einen Fehler, dass ich kein Portal erstellen kann.

Wenn Sie nicht über ausreichende Berechtigungen verfügen, um ein Portal in einer Umgebung zu erstellen, wird ein Fehler wie folgt angezeigt:

> [!div class=mx-imgBorder]
> ![Erstellen des Portalfehlers](media/portal-create-error.png "Erstellen des Portalfehlers")

Informationen zum Erstellen eines Portale und zu den erforderlichen Berechtigungen finden Sie unter [Erstellen eines Portale](create-portal.md).

## <a name="im-getting-the-message-your-data-isnt-quite-ready"></a>Ich verstehe die Nachricht: "Deine Daten sind nicht ganz fertig".

Manchmal kann die Erstellung der Datenbank einige Zeit in Anspruch nehmen und der richtige Status spiegelt sich möglicherweise nicht auf der Startseite wider. In diesem Fall erhalten Sie die folgende Meldung:

> [!div class=mx-imgBorder]
> ![Daten nicht bereit](media/data-not-ready.png "Daten nicht bereit")

Wenn Sie weiterhin die Eingabeaufforderung für die Erstellung der Datenbank erhalten oder Ihre Daten nicht ganz fertig sind, können Sie versuchen, die PowerApps Startseite zu aktualisieren, bevor Sie die Kachel **Portal aus leerer (Vorlage)** auswählen.

## <a name="im-getting-an-error-that-i-dont-have-required-permissions-to-create-azure-active-directory-applications"></a>Ich erhalte einen Fehler, dass ich keine erforderlichen Berechtigungen habe, um Azure Active Directory-Anwendungen zu erstellen.

Wenn Sie ein Portal anlegen, wird das Portal als neue Anwendung in der dem Mandant zugeordneten Azure Active Directory registriert. Wenn Sie nicht über ausreichende Berechtigungen verfügen, um einen Antrag bei Ihrem Azure Active Directory-Mandanten zu registrieren, erhalten Sie wie folgt einen Fehler:

> [!div class=mx-imgBorder]
> ![Azure Active Directory Fehler](media/azure-ad-error.png "Azure Active Directory Fehler")

Um Anwendungen in Azure Active Directory zu erstellen und zu registrieren, müssen Sie sich an Ihren Mandantenadministrator wenden, um die Einstellung **App-Registrierungen** für Ihren Mandanten einzuschalten. Weitere Informationen finden Sie unter [Benötigte Berechtigungen](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal#required-permissions).

## <a name="im-getting-an-error-that-portal-creation-is-blocked-in-this-tenant-by-global-administrator"></a>Ich erhalte einen Fehler, dass die Portalerstellung in diesem Mandanten durch den globalen Administrator blockiert wird.

Wenn die Portalerstellung in einem Mandanten von Ihrem globalen Administrator blockiert wird, erhalten Sie einen Fehler wie folgt:

> [!div class=mx-imgBorder]
> ![Portalerstellung Fehler gesperrt](media/portal-create-blocked-error.png "Portalerstellung Fehler gesperrt")

Sie müssen Ihren globalen Administrator kontaktieren, um die Erstellung von Portalen auch für Nicht-Administratoren zu ermöglichen.

Wenn Sie ein globaler Administrator sind, müssen Sie die Einstellung `disablePortalsCreationByNonAdminUsers` auf Mandantenebene über PowerShell deaktivieren. Führen Sie den folgenden Befehl in einem PowerShell-Fenster aus (führen Sie PowerShell als Administrator aus).

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $false }
```

Mehr Informationen: [Deaktivieren der Portalerstellung in einem Mandanten](create-portal.md#disable-portal-creation-in-a-tenant)

## <a name="im-getting-an-error-that-i-dont-have-appropriate-license-to-access-this-website"></a>Es wird ein Fehler angezeigt, dass ich nicht die entsprechende Lizenz besitze, auf diese Website zuzugreifen.

Für interne Benutzer einer Organisation, die Portale zum Zugriff auf authentifizierten Seiten verwendet, ist es erforderlich, dass Lizenzen der Umgebung zugewiesen werden, mit der ein Portal verbunden ist. Sie können mehr Informationen über Berechtigungen auf Portale für interne Benutzer [hier](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#can-you-clarify-the-use-rights-to-portals-for-internal-users) lesen. Wenn keine Lizenzen einer Umgebung zugeordnet sind, erhalten interne Benutzer einen Fehler wie den folgenden:

> [!div class=mx-imgBorder]
> ![Portalanmeldefehler](media/portal-login-error.png "Portalanmeldefehler")

