---
title: Häufig gestellte Fragen | Microsoft Docs
description: Häufig gestellte Fragen in PowerApps Portalen.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 10/02/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="powerapps-portals-faq"></a>PowerApps Portale FAQs

Damit Sie eine schnelle Übersicht erhalten, haben wir eine Liste mit häufig gestellten Fragen sowie kurze Antworten zusammengestellt, damit Sie schnell Ihre Informationen erhalten können.

## <a name="im-getting-an-error-that-only-one-portal-can-be-created"></a>Ich erhalte einen Fehler, dass nur ein Portal erstellt werden kann.

Derzeit können Sie in einer Umgebung pro Sprache nur ein Portal pro Typ erstellen. Wenn Sie versuchen, mehr als ein Portal anzulegen, erhalten Sie eine Fehlermeldung wie folgt:

> [!div class=mx-imgBorder]
> ![Fehler: Maximale Portalzahl erstellt](media/portal-max-error.png "Fehler: Maximale Portalzahl erstellt")

Um weitere Portale zu erstellen, müssen Sie eine neue Umgebung über den Link **Neue Umgebung erstellen** in der Fehlermeldung erstellen. Weitere Informationen zum Anlegen eines Portale finden Sie unter [Ein Portal anlegen](create-portal.md).

## <a name="im-getting-an-error-that-i-cant-delete-my-portal"></a>Ich erhalte einen Fehler, dass ich mein Portal nicht löschen kann.

Wenn Sie nicht über ausreichende Berechtigungen zum Löschen eines Portale verfügen, wird ein Fehler wie folgt angezeigt:

> [!div class=mx-imgBorder]
> ![Portalfehler löschen](media/portal-delete-error.png "Portalfehler löschen")

Informationen zum Löschen eines Portale und der erforderlichen Berechtigungen finden Sie unter [Löschen eines Portale](manage-existing-portals.md#delete).

## <a name="im-getting-an-error-that-i-cant-create-a-portal"></a>Ich erhalte einen Fehler, dass ich kein Portal erstellen kann.

Wenn Sie nicht über ausreichende Berechtigungen verfügen, um ein Portal in einer Umgebung zu erstellen, wird ein Fehler wie folgt angezeigt:

> [!div class=mx-imgBorder]
> ![Portalfehler erzeugen](media/portal-create-error.png "Portalfehler erzeugen")

Informationen zum Erstellen eines Portale und zu den erforderlichen Berechtigungen finden Sie unter [Erstellen eines Portale](create-portal.md).

## <a name="im-getting-the-message-your-data-isnt-quite-ready"></a>Ich verstehe die Nachricht: "Deine Daten sind nicht ganz fertig".

Manchmal kann die Erstellung der Datenbank einige Zeit in Anspruch nehmen und der richtige Status spiegelt sich möglicherweise nicht auf der Startseite wider. In diesem Fall erhalten Sie die folgende Meldung:

> [!div class=mx-imgBorder]
> ![Daten nicht bereit ](media/data-not-ready.png "Daten nicht bereit ")

Wenn Sie weiterhin die Eingabeaufforderung für die Erstellung der Datenbank erhalten oder Ihre Daten nicht ganz fertig sind, können Sie versuchen, die Startseite PowerApps zu aktualisieren, bevor Sie die Kachel Portal aus leerer (Vorschau) auswählen.

## <a name="im-getting-an-error-that-i-dont-have-required-permissions-to-create-azure-active-directory-applications"></a>Ich erhalte einen Fehler, dass ich keine erforderlichen Berechtigungen habe, um Azure Active Directory-Anwendungen zu erstellen.

Wenn Sie ein Portal anlegen, wird das Portal als neue Anwendung in der dem Mandant zugeordneten Azure Active Directory registriert. Wenn Sie nicht über ausreichende Berechtigungen verfügen, um einen Antrag bei Ihrem Azure Active Directory-Mandanten zu registrieren, erhalten Sie wie folgt einen Fehler:

> [!div class=mx-imgBorder]
> ![Azure Active Directory Fehler](media/azure-ad-error.png "Azure Active Directory Fehler")

Um Anwendungen in Azure Active Directory zu erstellen und zu registrieren, müssen Sie sich an Ihren Mandantenadministrator wenden, um die Einstellung **App-Registrierungen** für Ihren Mandanten einzuschalten. Weitere Informationen finden Sie unter [Benötigte Berechtigungen](https://docs.microsoft.com/en-us/azure/active-directory/develop/howto-create-service-principal-portal#required-permissions).

## <a name="im-getting-an-error-that-portal-creation-is-blocked-in-this-tenant-by-global-administrator"></a>Ich erhalte einen Fehler, dass die Portalerstellung in diesem Mandanten durch den globalen Administrator blockiert wird.

Wenn die Portalerstellung in einem Mandanten von Ihrem globalen Administrator blockiert wird, erhalten Sie einen Fehler wie folgt:

> [!div class=mx-imgBorder]
> ![Fehler – Portalerstellung blockiert](media/portal-create-blocked-error.png "Fehler – Portalerstellung blockiert")

Sie müssen Ihren globalen Administrator kontaktieren, um die Erstellung von Portalen auch für Nicht-Administratoren zu ermöglichen.

Wenn Sie ein globaler Administrator sind, müssen Sie die Einstellung `disablePortalsCreationByNonAdminUsers` auf Mandantenebene über PowerShell deaktivieren. Führen Sie den folgenden Befehl in einem PowerShell-Fenster aus (führen Sie PowerShell als Administrator aus).

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $false }
```

Mehr Informationen: [Deaktivieren der Portalerstellung in einem Mandanten](create-portal.md#disable-portal-creation-in-a-tenant)
