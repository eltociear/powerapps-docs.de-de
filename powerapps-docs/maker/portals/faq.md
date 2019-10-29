---
title: Häufig gestellte Fragen | Microsoft-Dokumentation
description: Häufig gestellte Fragen in den powerapps-Portalen.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: eb7228f669fe8c36e25a18f4db0c7e4c4964a42d
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976689"
---
# <a name="powerapps-portals-faq"></a>Häufig gestellte Fragen zu PowerApps-Portals

Wir haben eine Liste mit häufig gestellten Fragen kompiliert und kurze Antworten bereitgestellt, damit Sie schnell zu Ihren Informationen gelangen können.

## <a name="im-getting-an-error-that-only-one-portal-can-be-created"></a>Ich erhalte eine Fehlermeldung, dass nur ein Portal erstellt werden kann.

Derzeit können Sie nur ein Portal jedes Typs in einer Umgebung pro Sprache erstellen. Wenn Sie versuchen, mehr als ein Portal zu erstellen, wird eine Fehlermeldung wie folgt angezeigt:

> [!div class=mx-imgBorder]
> ![Maximum des vom Portal erstellten Fehlers](media/portal-max-error.png "Maximum des im Portal erstellten Fehlers")

Um weitere Portale zu erstellen, müssen Sie eine neue Umgebung erstellen, indem Sie den Link **neue Umgebung erstellen** in der Fehlermeldung verwenden. Weitere Informationen zum Erstellen eines Portals finden Sie unter [Erstellen eines Portals](create-portal.md).

## <a name="im-getting-an-error-that-i-cant-delete-my-portal"></a>Ich erhalte eine Fehlermeldung, dass mein Portal nicht gelöscht werden kann.

Wenn Sie nicht über ausreichende Berechtigungen zum Löschen eines Portals verfügen, wird der folgende Fehler angezeigt:

> [!div class=mx-imgBorder]
> ![](media/portal-delete-error.png "Fehler") beim Löschen des Portals zum Löschen des Portals

Informationen zum Löschen eines Portals und der erforderlichen Berechtigungen finden Sie unter [Löschen eines Portals](manage-existing-portals.md#delete).

## <a name="im-getting-an-error-that-i-cant-create-a-portal"></a>Ich erhalte eine Fehlermeldung, dass ich kein Portal erstellen kann.

Wenn Sie nicht über ausreichende Berechtigungen zum Erstellen eines Portals in einer Umgebung verfügen, wird der folgende Fehler angezeigt:

> [!div class=mx-imgBorder]
> Fehler beim Erstellen des ![Portals]beim(media/portal-create-error.png "Erstellen") des Portals.

Informationen zum Erstellen eines Portals und der erforderlichen Berechtigungen finden Sie unter [Erstellen eines Portals](create-portal.md).

## <a name="im-getting-the-message-your-data-isnt-quite-ready"></a>Ich erhalte die folgende Meldung: "Ihre Daten sind nicht Recht bereit".

Manchmal kann die Erstellung der Datenbank eine Weile dauern, und der richtige Status wird auf der Startseite möglicherweise nicht angezeigt. In diesem Fall wird die folgende Meldung angezeigt:

> [!div class=mx-imgBorder]
> ![Nicht bereit bereite]Daten sind(media/data-not-ready.png "nicht bereit") .

Wenn Sie weiterhin die Eingabeaufforderung zum Erstellen einer Datenbank erhalten oder die Eingabeaufforderung für Ihre Daten nicht mehr angezeigt wird, können Sie versuchen, die powerapps-Startseite zu aktualisieren, bevor Sie das **Portal aus der leeren** Kachel

## <a name="im-getting-an-error-that-i-dont-have-required-permissions-to-create-azure-active-directory-applications"></a>Ich erhalte eine Fehlermeldung, dass ich nicht über die erforderlichen Berechtigungen zum Erstellen von Azure Active Directory Anwendungen verfüge.

Wenn Sie ein Portal erstellen, wird das Portal als neue Anwendung in Azure Active Directory registriert, das mit dem Mandanten verknüpft ist. Wenn Sie nicht über ausreichende Berechtigungen verfügen, um eine Anwendung bei Ihrem Azure Active Directory Mandanten zu registrieren, wird wie folgt ein Fehler angezeigt:

> [!div class=mx-imgBorder]
> Fehler(media/azure-ad-error.png "Azure Active Directory Fehler") ![Azure Active Directory]

Um Anwendungen in Azure Active Directory zu erstellen und zu registrieren, müssen Sie sich an ihren Mandanten Administrator wenden, um die **App-Registrierungen** Einstellung für Ihren Mandanten zu aktivieren. Weitere Informationen finden Sie unter [erforderliche Berechtigungen](https://docs.microsoft.com/en-us/azure/active-directory/develop/howto-create-service-principal-portal#required-permissions).

## <a name="im-getting-an-error-that-portal-creation-is-blocked-in-this-tenant-by-global-administrator"></a>Ich erhalte eine Fehlermeldung, dass die Portal Erstellung in diesem Mandanten durch den globalen Administrator blockiert wird.

Wenn die Portal Erstellung in einem Mandanten durch ihren globalen Administrator blockiert wird, wird wie folgt ein Fehler angezeigt:

> [!div class=mx-imgBorder]
> Fehler bei der ![Portal Erstellung für blockierte Fehler](media/portal-create-blocked-error.png "Portal Erstellung")

Sie müssen sich an ihren globalen Administrator wenden, um das Erstellen von Portalen durch nicht Administratoren zu ermöglichen.

Wenn Sie ein globaler Administrator sind, müssen Sie die Einstellung für die `disablePortalsCreationByNonAdminUsers` auf Mandanten Ebene über PowerShell deaktivieren. Führen Sie den folgenden Befehl in einem PowerShell-Fenster aus (führen Sie PowerShell als Administrator aus).

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $false }
```

Weitere Informationen: [Deaktivieren der Portal Erstellung in einem](create-portal.md#disable-portal-creation-in-a-tenant) Mandanten

## <a name="im-getting-an-error-that-i-dont-have-appropriate-license-to-access-this-website"></a>Ich erhalte eine Fehlermeldung, dass ich keine geeignete Lizenz für den Zugriff auf diese Website habe.

Interne Benutzer einer Organisation, die Portale für den Zugriff auf authentifizierte Seiten verwenden, erfordern, dass Lizenzen der Umgebung zugewiesen werden, mit der ein Portal verbunden ist. Weitere Informationen zu den Benutzerrechten für Portale für interne Benutzer finden Sie [hier](https://docs.microsoft.com/en-us/power-platform/admin/powerapps-flow-licensing-faq#can-you-clarify-the-use-rights-to-portals-for-internal-users). Wenn in einer Umgebung keine Lizenzen zugewiesen sind, erhalten interne Benutzer eine Fehlermeldung wie die folgende:

> [!div class=mx-imgBorder]
> (media/portal-login-error.png "Anmeldefehler") im Portal für die ![Portal Anmeldung]

