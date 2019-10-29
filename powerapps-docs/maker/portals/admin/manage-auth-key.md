---
title: Verbinden eines Portals mit einer Common Data Service Umgebung | MicrosoftDocs
description: Erfahren Sie, wie Sie ein Portal mit einer Common Data Service Umgebung verbinden und den Authentifizierungsschlüssel erneuern.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 31632f4de1834855c696baa1b4b651ed777c8abd
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72977494"
---
# <a name="connect-to-a-common-data-service-environment-using-a-portal"></a>Herstellen einer Verbindung mit einer Common Data Service Umgebung mithilfe eines Portals

Ein Portal stellt mithilfe einer Azure Active Directory Anwendung eine Verbindung mit einer Common Data Service Umgebung her. Die Anwendung wird im gleichen Mandanten erstellt, in dem das Portal bereitgestellt wird. Die Anwendung wird während des Bereitstellungs Prozesses des Portals bei der Common Data Service Umgebung registriert.

![Verbinden eines Portals mit Common Data Service Umgebung]verbinden(../media/connect-with-dynamics.png "eines Portals mit Common Data Service Umgebung")

Jedem Portal ist eine separate Azure Active Directory Anwendung zugeordnet, egal, ob es mit derselben Common Data Service Umgebung verbunden ist oder nicht. Der Standard Azure Active Directory Authentifizierungs Anbieters, der für ein Portal erstellt wurde, verwendet dieselbe Azure Active Directory Anwendung, um das Portal zu authentifizieren. Die Autorisierung wird von Webrollen erzwungen, die dem Benutzer zugewiesen sind, der auf das Portal

Die zugehörige Portal Anwendung wird in Azure Active Directory angezeigt. Der Name dieser Anwendung ist Microsoft CRM-Portale, und die Portal-ID befindet sich im Feld **App-ID-URI** in der Azure Active Directory-Anwendung. Die Person, die das Portal bereitstellt, besitzt diese Anwendung. Sie sollten diese Anwendung nicht löschen oder ändern, oder Sie können die Funktionalität des Portals unterbrechen. Sie müssen der Besitzer der Anwendung sein, um ein Portal über das powerapps-Portal Admin Center verwalten zu können.

## <a name="authentication-key"></a>Authentifizierungsschlüssel

Damit ein Portal mithilfe einer Azure Active Directory Anwendung eine Verbindung mit Common Data Service herstellen kann, ist ein Authentifizierungsschlüssel erforderlich, der mit der Azure Active Directory Anwendung verbunden ist. Dieser Schlüssel wird generiert, wenn Sie ein Portal bereitstellen und der öffentliche Teil dieses Schlüssels automatisch in die Azure Active Directory Anwendung hochgeladen wird.

> [!IMPORTANT]
> Der Authentifizierungsschlüssel läuft in zwei Jahren ab. Er muss alle zwei Jahre erneuert werden, um sicherzustellen, dass das Portal weiterhin eine Verbindung mit der Common Data Service Umgebung herstellt. Wenn Sie den Schlüssel nicht aktualisieren, wird das Portal nicht mehr funktionieren.  

### <a name="authentication-key-details"></a>Details zum Authentifizierungsschlüssel

Die Details eines Authentifizierungs Schlüssels werden im Admin Center und Portal des powerapps-Portals angezeigt.

**Powerapps-Portale Admin Center**

1. Öffnen Sie das [powerapps-Portal Admin Center](admin-overview.md).

2. Wählen Sie **Portal Authentifizierungsschlüssel verwalten**aus. Der Authentifizierungsschlüssel wird zusammen mit dem Ablaufdatum und dem Fingerabdruck angezeigt.

   > [!div class=mx-imgBorder]
   > ![Details zum Authentifizierungsschlüssel in den powerapps-Portalen admin]Center(../media/manage-auth-key.png "Authentifizierungsschlüssel Details im powerapps-Portal Admin Center")

**Portal**

1. Melden Sie sich beim Portal als Administrator an.

2. Navigieren Sie zur URL < portal_path >/_services/about. Das Ablaufdatum für den Authentifizierungsschlüssel wird angezeigt. 

   > [!div class=mx-imgBorder]
   > Portal ![Dienst]Seite(../media/portal-services-page.png "Portal Dienst Seite")

> [!NOTE]
> Um Informationen zum Authentifizierungsschlüssel anzuzeigen, müssen Sie sich in derselben Browsersitzung beim Portal anmelden, und Sie müssen über alle Zugriffsberechtigungen für die Website verfügen.

### <a name="authentication-key-expiration-notification"></a>Ablauf Benachrichtigung für Authentifizierungsschlüssel

Bevor der Authentifizierungsschlüssel abläuft, werden Sie per e-Mail, powerapps-Portale Admin Center und Portal benachrichtigt.

**Email**

E-Mail wird an Personen gesendet, die sich für die e-Mail-Benachrichtigung für die Organisation registriert haben, die mit dem Portal verbunden ist. Weitere Informationen zum Registrieren für eine e-Mail-Benachrichtigung: [Verwalten von e-Mail-Benachrichtigungen an Administratoren](https://docs.microsoft.com/dynamics365/customer-engagement/admin/manage-email-notifications)

E-Mail-Benachrichtigungen werden in den folgenden Intervallen gesendet: 
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

Sie werden auch benachrichtigt, wenn der Schlüssel jeden Tag bis zu einer Woche nach dem Ablauf des Schlüssels abläuft.

> [!NOTE]
> - Intervalle werden in UTC vom Ablaufdatum des Schlüssels aus berechnet.
> - Es ist nicht garantiert, dass die e-Mail-Adresse genau den in den oben aufgeführten Intervallen entspricht E-Mail-Benachrichtigungen können verzögert oder übersehen werden. Stellen Sie sicher, dass Sie auch online auf das Ablaufdatum des Schlüssels achten.

**Powerapps-Portale Admin Center**

Oben auf der Seite wird eine Meldung zum Ablauf des Schlüssels angezeigt.

> [!div class=mx-imgBorder]
> ![Benachrichtigung über Authentifizierungsschlüssel in powerapps-Portale Admin Center](../media/portal-admin-center-auth-notif.png "Authentifizierungsschlüssel Benachrichtigung im powerapps-Portal Admin Center")

**Portal**

Wenn Sie zur URL < portal_path >/_services/about navigieren, wird unten auf der Seite eine Benachrichtigung über den Ablauf des Schlüssels angezeigt.

> [!NOTE]
> Sie müssen sich in der gleichen Browsersitzung bei Ihrem Portal anmelden, und Sie müssen alle Zugriffsberechtigungen für die Website erhalten.

> [!div class=mx-imgBorder]
> Benachrichtigung über ![Authentifizierungsschlüssel bei der Benachrichtigung über den Portal](../media/portal-service-page-auth-notif.png "Authentifizierungsschlüssel im Portal")

## <a name="renew-portal-authentication-key"></a>Erneuern des Authentifizierungsschlüssels für ein Portal

Sie müssen den Schlüssel alle zwei Jahre erneuern, um sicherzustellen, dass das Portal eine Verbindung mit Common Data Service Umgebung herstellen kann.

> [!NOTE]
> Zum Erneuern des Schlüssels müssen Sie über Berechtigungen zum Verwalten des Portals verfügen.

1. Öffnen Sie das [powerapps-Portal Admin Center](admin-overview.md).

2. Wählen Sie **Portal Authentifizierungsschlüssel verwalten**aus. Der Authentifizierungsschlüssel wird zusammen mit dem Ablaufdatum und dem Fingerabdruck angezeigt.

    > [!div class=mx-imgBorder]
    > ![Verwalten des Portal Authentifizierungs Schlüssels](../media/manage-portal-auth-key.png "Verwalten des Portal Authentifizierungs Schlüssels")

3. Wählen Sie **Schlüssel aktualisieren**aus.

4. Wählen Sie in der Meldung die Option **Aktualisieren** aus. Der Aktualisierungs Vorgang wird gestartet, und es wird eine Meldung angezeigt.

> [!NOTE]
> - Während dieser Prozess im Hintergrund ausgeführt wird, wird das Portal einmal neu gestartet.
> - Wenn Sie einen Schlüssel aktualisieren, wird er zwei Jahre lang aktualisiert.
> - Dieser Vorgang dauert fünf bis sieben Minuten.

### <a name="troubleshooting"></a>Problembehandlung

Wenn die Schlüssel Aktualisierung fehlschlägt, wird eine Fehlermeldung zusammen mit der folgenden Aktion angezeigt:

- **Wiederholen Sie die Aktualisierung des Authentifizierungs Schlüssels**. Mit dieser Aktion können Sie den Aktualisierungs Vorgang für den Portal Authentifizierungsschlüssel neu starten. Wenn die Aktualisierung mehrmals fehlschlägt, wenden Sie sich an den Microsoft Support.

    > [!div class=mx-imgBorder]
    > Authentifizierungsschlüssel für erneuten Authentifizierungs ![Schlüssel aktualisieren]Wiederholungs(../media/retry-auth-key-update.png "Portal Authentifizierungsschlüssel aktualisieren")