---
title: Ein Portal mit einer Common Data Service-Umgebung verbinden | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie ein Portal mit einer Common Data Service-Umgebung verbinden und wie Sie den Authentifizierungsschlüssel erneuern.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 82245371095e523ba9221fc43ce21564e0445103
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2862654"
---
# <a name="connect-to-a-common-data-service-environment-using-a-portal"></a>Ein Portal mit einer Common Data Service-Umgebung verbinden

Ein Portal stellt eine Verbindung mit einer Common Data Service-Umgebung mit Hilfe einer Azure Active Directory-Anwendung her. Die Anwendung wird im gleichen Mandanten erstellt, in dem das Portal bereitgestellt wird. Die Anwendung wird bei der Common Data Service-Umgebung während des Portalbereitstellungsprozesses registriert.

![Ein Portal mit der Common Data Service-Umgebung verbinden](../media/connect-with-dynamics.png "Ein Portal mit der Common Data Service-Umgebung verbinden")

Jedem Portal ist eine separate Azure Active Directory-Anwendung zugeordnet, ungeachtet dessen, ob es mit derselben Common Data Service-Umgebung verbunden ist. Der standardmäßige Azure Active Directory-Authentifizierungsanbieter, der für ein Portal erstellt ist, verwendet dieselbe Azure Active Directory-Anwendung, um das Portal zu authentifizieren. Die Autorisierung wird durch Webrollen erzwungen, die dem Benutzer zugewiesen werden, der auf das Portal zugreift.

Sie können die zugeordneten Portalanwendung in Azure Active Directory sehen. Der Name dieser Anwendung wird Microsoft CRM-Portale sein, und die Portal-ID befindet sich im Feld **App-ID-URI** in der Azure Active Directory-Anwendung. Die Person, die das Portal bereitstellt, besitzt diese Anwendung. Sie dürfen diese Anwendung nicht löschen oder ändern. Anderenfalls zerstören Sie möglicherweise die Portalfunktionen. Sie müssen der Anwendungsbesitzer sein, um ein Portal aus dem Admin-Center für Power Apps-Portale zu verwalten.

## <a name="authentication-key"></a>Authentifizierungsschlüssel

Damit ein Portal eine Verbindung mit Common Data Service unter Verwendung einer Azure Active Directory-Anwendung herstellt, benötigt es einen Authentifizierungsschlüssel, der mit der Azure Active Directory-Anwendung verbunden ist. Dieser Schlüssel wird generiert, wenn Sie ein Portal bereitstellen und der öffentliche Teil dieses Schlüssels automatisch zur Azure Active Directory-Anwendung hochgeladen wird.

> [!IMPORTANT]
> Der Authentifizierungsschlüssel läuft in zwei Jahren ab. Er muss alle zwei Jahre erneuert werden, um sicherzustellen, dass Ihr Portal weiterhin eine Verbindung mit Ihrer Common Data Service-Umgebung herstellt. Wenn Sie den Schlüssel nicht aktualisieren, funktioniert das Portal nicht mehr.  

### <a name="authentication-key-details"></a>Schlüsseldetails zur Authentifizierung

Die Details eines Authentifizierungsschlüssels werden im Admin-Center und Portal für Power Apps-Portale angezeigt.

**Admin-Center für Power Apps-Portale**

1. Öffnen Sie das [Admin Center für Power Apps-Portale](admin-overview.md).

2. Wählen Sie **Portalauthentifizierungsschlüssel verwalten** aus. Der Authentifizierungsschlüssel wird zusammen mit seinem Ablaufdatum und Fingerabdruck angezeigt.

   > [!div class=mx-imgBorder]
   > ![Authentifizierungsschlüsseldetails im Power Apps-Portal-Administratorcenter](../media/manage-auth-key.png "Authentifizierungsschlüsseldetails im Power Apps-Portal-Administratorcenter")

**Portal**

1. Melden Sie sich beim Portal als Administrator an.

2. Navigieren Sie zur URL <portal_path>/_services/about. Das Authentifizierungsschlüssel-Ablaufdatum wird angezeigt. 

   > [!div class=mx-imgBorder]
   > ![Portalserviceseite](../media/portal-services-page.png "Portalserviceseite")

> [!NOTE]
> Um Authentifizierungsschlüsselinformationen anzuzeigen, müssen Sie sich beim Portal in derselben Browsersitzung anmelden, und Sie müssen über die gesamte Websitezugriffsberechtigung verfügen.

### <a name="authentication-key-expiration-notification"></a>Benachrichtigung über den Ablauf des Authentifizierungsschlüssels

Bevor der Authentifizierungsschlüssel abläuft, werden Sie per E-Mails, Admin-Center der Power Apps-Portale und Portal benachrichtigt.

**Email**

E-Mail wird an Personen gesendet, die sich für die E-Mail-Benachrichtigung für die Organisation angemeldet haben, die mit ihrem Portal verbunden ist. Weitere Informationen über die Anmeldung für die E-Mail-Benachrichtigung: [Verwalten von E-Mail-Benachrichtigungen an Administratoren](https://docs.microsoft.com/dynamics365/customer-engagement/admin/manage-email-notifications)

E-Mail-Benachrichtigungen werden in den nachfolgenden Intervallen gesendet: 
- 90 Tage 
- 60 Tage 
- 30 Tage 
- 15 Tage 
- 7 Tage 
- 6 Tage 
- 5 Tage 
- 4 Tage 
- 3 Tage 
- 2 Tage 
- 1 Tag 
- 12 Stunden 
- 6 Stunden 
- 3 Stunden

Außerdem werden Sie benachrichtigt, nachdem der Schlüssel abgelaufen ist, und zwar jeden Tag bis 1 Woche nach Schlüsselablauf.

> [!NOTE]
> - Intervalle werden in UTC ab dem Schlüsselablaufdatum berechnet.
> - Die E-Mail kann nicht zu genau den oben aufgelisteten Intervallen garantiert werden. Eine E-Mail-Benachrichtigung kann sich verzögern oder verpasst werden. Stellen Sie sicher, dass Sie auch online das Schlüsselablaufdatum überprüfen.

**Admin-Center für Power Apps-Portale**

Eine Nachricht über das Schlüsselablaufdatum wird oben auf der Seite angezeigt.

> [!div class=mx-imgBorder]
> ![Authentifizierungsschlüsselbenachrichtigung im Power Apps-Portal-Administratorcenter](../media/portal-admin-center-auth-notif.png "Authentifizierungsschlüsselbenachrichtigung im Power Apps-Portal-Administratorcenter")

**Portal**

Wenn Sie zur URL <portal_path>/_services/about navigieren, wird eine Benachrichtigung über das Schlüsselablaufdatum unten auf der Seite angezeigt.

> [!NOTE]
> Sie müssen sich bei Ihrem Portal in derselben Browsersitzung anmelden, und Ihnen muss die gesamte Websitezugriffsberechtigung zugewiesen sein.

> [!div class=mx-imgBorder]
> ![Authentifizierungsschlüsselbenachrichtigung im Portal](../media/portal-service-page-auth-notif.png "Authentifizierungsschlüsselbenachrichtigung im Portal")

## <a name="renew-portal-authentication-key"></a>Portalauthentifizierungsschlüssel erneuern

Sie müssen den Schlüssel alle zwei Jahre erneuern, um sicherzustellen, dass Ihr Portal eine Verbindung mit Ihrer Common Data Service-Umgebung herstellen kann.

> [!NOTE]
> Um den Schlüssel zu erneuern, müssen Sie über Berechtigungen zur Verwaltung Ihres Portale verfügen.

1. Öffnen Sie das [Admin Center für Power Apps-Portale](admin-overview.md).

2. Wählen Sie **Portalauthentifizierungsschlüssel verwalten** aus. Der Authentifizierungsschlüssel wird zusammen mit seinem Ablaufdatum und Fingerabdruck angezeigt.

    > [!div class=mx-imgBorder]
    > ![Portalauthentifizierungsschlüssel verwalten](../media/manage-portal-auth-key.png "Portalauthentifizierungsschlüssel verwalten")

3. Wählen Sie **Schlüssel aktualisieren** aus.

4. Wählen Sie **Aktualisieren** in der Meldung aus. Der Updateprozess startet, und eine Meldung wird angezeigt.

> [!NOTE]
> - Während dieser Prozess im Hintergrund ausgeführt wird, startet das Portal einmal erneut.
> - Wenn Sie einen Schlüssel aktualisieren, wird er für zwei Jahre aktualisiert.
> - Dieser Prozess wird fünf bis sieben Minuten dauern.

### <a name="troubleshooting"></a>Problembehandlung

Wenn das Schlüsselupdate fehlschlägt, wird eine Fehlermeldung zusammen mit der folgenden Aktion angezeigt:

- **Authentifizierungsschlüsselupdate erneut versuchen**. Diese Aktion ermöglicht es Ihnen, den Portalauthentifizierungsschlüssel-Updateprozess erneut zu starten. Wenn das Update mehrmals fehlschlägt, wenden Sie sich an den Microsoft-Support.

    > [!div class=mx-imgBorder]
    > ![Portalauthentifizierungsschlüssel-Update wiederholen](../media/retry-auth-key-update.png "Portalauthentifizierungsschlüssel-Update wiederholen")