---
title: Freigeben einer App | Microsoft-Dokumentation
description: Geben Sie Ihre App frei, indem Sie anderen Benutzern die Berechtigung erteilen, die App auszuführen oder zu ändern.
documentationcenter: na
author: AFTOwen
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: canvas
ms.date: 03/18/2018
ms.author: anneta
ms.openlocfilehash: c87f0e644668e9b9804b001560402972fd3d4531
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "32329132"
---
# <a name="share-an-app-in-powerapps"></a>Freigeben einer Apps in PowerApps
Sie können mit PowerApps Apps erstellen, die genau auf die Anforderungen Ihres eigenen Unternehmens abgestimmt sind, aber die eigentliche Stärke von PowerApps liegt darin, dass Sie diese Apps für andere Personen freigeben können. In diesem Thema erfahren Sie, wie Sie Apps für bestimmte Benutzer oder Sicherheitsgruppen oder für Ihre gesamte Organisation freigeben.

## <a name="specify-an-app"></a>Angeben einer App
1. Melden Sie sich bei PowerApps an, und klicken oder tippen Sie dann am linken Bildschirmrand auf **Apps**.

    ![Anzeigen der App-Liste](./media/share-app/file-apps.png)

1. Klicken oder tippen Sie für die App, die Sie freigeben möchten, auf die Auslassungspunkte (...), und klicken oder tippen Sie anschließend auf **Freigeben**.

    ![Geöffneter Bildschirm „Freigeben“](./media/share-app/ellipsis-share.png)

## <a name="share-an-app"></a>Eine App freigeben
1. Geben Sie an, für welche Benutzer- oder Sicherheitsgruppen in Azure Active Directory Sie die App freigeben möchten und ob Sie diesen Personen eine E-Mail-Benachrichtigung senden möchten.

    Sie können die App ebenfalls für Ihre gesamte Organisation freigeben, sodass alle Mitglieder die App ausführen können. Diese können jedoch keine Änderungen vornehmen oder die App freigeben.

    ![Angeben von Benutzern](./media/share-app/share-list.png)

1. Geben Sie die Berechtigungsebenen an, und klicken oder tippen Sie dann auf **Speichern**.

    * **Verwenden**: Benutzer oder Gruppen können die App ausführen, aber nicht freigeben.
    * **Kann bearbeiten:** Benutzer und Gruppen können die App ausführen, anpassen und die benutzerdefinierte Version für andere Benutzer freigeben.

        ![Berechtigungen angeben](./media/share-app/edit-use.png)

Um die Berechtigungen für einen Benutzer oder für Gruppen zu ändern, wiederholen Sie Schritt 1 dieser Prozedur, und geben Sie anschließend eine andere Option in der Liste der Berechtigungen für diesen Benutzer oder diese Gruppe an. Um einen Benutzer oder einer Gruppe alle Berechtigungen zu entziehen, klicken oder tippen Sie auf das Symbol **x** für diesen Benutzer oder diese Gruppe.

### <a name="send-email-notification"></a>Senden einer E-Mail-Benachrichtigung
Wenn Sie eine App freigeben, können Sie auswählen, ob Benutzer oder Sicherheitsgruppen per E-Mail benachrichtigt werden sollen. Wenn Sie diese Option auswählen, wird den Benutzern oder Sicherheitsgruppen eine E-Mail-Benachrichtigung gesendet. Die E-Mail enthält einen Link für den Zugriff auf die App. Gegebenenfalls werden Benutzer dazu aufgefordert, sich für PowerApps zu registrieren.

Die Benachrichtigung enthält einen Link, der von der von Ihnen zugewiesenen Berechtigung abhängt:

- Wenn Sie die App mit der Berechtigung **Verwenden** freigeben, enthält die E-Mail den Link zum Ausführen der App.
- Wenn Sie die App mit der Berechtigung **Kann bearbeiten** freigeben, enthält die E-Mail den Link zum Ausführen oder Bearbeiten der App.

### <a name="how-do-my-users-see-the-app-i-shared"></a>Wie wird meinen Benutzern die freigegebene App angezeigt?
Nachdem Sie eine App für mindestens einen Benutzer oder eine Sicherheitsgruppe freigegeben haben, legt die Freigabeberechtigung fest, wie Benutzern die freigegebene App angezeigt wird.

##### <a name="if-you-shared-an-app-with-can-use-permission"></a>Wenn Sie eine App mit der Berechtigung *Can use* (Verwenden) freigegeben haben
Die Personen, für die Sie die App freigegeben haben, erhalten eine E-Mail-Benachrichtigung, wenn Sie dieses Kontrollkästchen auf dem Bildschirm für die App-Freigabe aktiviert haben. In der E-Mail können die Benutzer auf einen Link klicken oder tippen, um die App in [Dynamics 365](http://home.dynamics.com) auszuführen. In Kürze werden universelle Links unterstützt. Dies bedeutet, dass die App in PowerApps Studio oder PowerApps Mobile geöffnet wird, wenn diese Anwendungen installiert sind.

Benutzer können die App auch in AppSource in [Dynamics 365](http://home.dynamics.com) ermitteln (wenn Sie beispielsweise keine E-Mail gesendet haben). [Erfahren Sie mehr darüber](../../user/app-source.md), wie Benutzer Apps über AppSource abrufen können.

##### <a name="if-you-shared-an-app-with-can-edit-permission"></a>Wenn Sie eine App mit der Berechtigung *Can edit* (Bearbeiten) freigegeben haben
Die Personen, für die Sie die App freigegeben haben, erhalten eine E-Mail-Benachrichtigung, wenn Sie dieses Kontrollkästchen auf dem Bildschirm für die App-Freigabe aktiviert haben. In der E-Mail können sie auf einen Link klicken oder tippen, der die App unter Verwendung von PowerApps Studio direkt für die Bearbeitung öffnet. Es ist auch ein Link zum Ausführen der App in [Dynamics 365](http://home.dynamics.com) vorhanden. In Kürze werden universelle Links unterstützt. Dies bedeutet, dass die App in PowerApps Studio oder PowerApps Mobile geöffnet wird, wenn diese Anwendungen installiert sind.

Benutzer können die App auch unter [powerapps.com](http://web.powerapps.com) suchen (wenn Sie beispielsweise keine E-Mail gesendet haben). Dies ist der Startpunkt für App-Ersteller, um alle Apps zu suchen, die sie erstellt haben oder die mit der Berechtigung **Mitwirkender** für sie freigegeben wurden. Über [Dynamics 365](http://home.dynamics.com) hingegen können Benutzer Apps aus PowerApps oder andere Geschäftsanwendungen schnell ausführen.

## <a name="other-things-to-know"></a>Weitere wichtige Informationen
* Um eine App freizugeben, müssen Sie sie nicht lokal, sondern in der Cloud speichern.
* Bevor Sie eine App freigeben, sollten Sie überlegen, für welche Benutzer und Sicherheitsgruppen Sie die App freigeben möchten und welche Rolle konfiguriert werden soll: **Kann bearbeiten** oder **Verwenden**. Wenn Sie eine App für eine Gruppe, bestehende Mitglieder dieser Gruppe und jeden freigeben, der dieser Gruppe beitritt, verfügen alle über die von Ihnen angegebenen Berechtigungen. Jeder, der die Gruppe verlässt, verliert diese Berechtigungen, es sei denn, diese Personen sind Mitglieder einer anderen Gruppe, die über Zugriff verfügt, oder Sie gewähren ihnen explizit Berechtigungen.
* Jedes Mitglied einer Gruppe besitzt dieselben Berechtigungen für eine App wie die Gruppe allgemein. Sie können allerdings für ein Mitglied oder mehrere Mitglieder dieser Gruppe tiefgreifendere Berechtigungen angeben, um diesen Personen besseren Zugriff zu gewähren. Sie können beispielsweise „Sicherheitsgruppe A“ die Berechtigung **Verwenden** erteilen. Sie können jedoch auch „Benutzer B“, der zu dieser Gruppe gehört, die Berechtigung **Kann bearbeiten** erteilen. Jedes Mitglied der Sicherheitsgruppe kann die App ausführen, aber nur Benutzer B kann diese bearbeiten. Wenn Sie „Sicherheitsgruppe A“ die Berechtigung **Kann bearbeiten** erteilen, aber „Benutzer B“ nur die Berechtigung **Verwenden**, kann der Benutzer die App trotzdem bearbeiten.
* Sie können eine App für Ihre gesamte Organisation freigeben, aber Sie sollten vorher sorgfältig prüfen, ob alle Benutzer Zugriff auf Ihre App benötigen.
* Beachten Sie, dass alle Änderungen, die Sie an einer freigegebenen App vornehmen, beim Speichern der Änderungen sofort an die Personen weitergegeben werden, für die die App freigegeben wurde. Wenn Sie die App verbessern, profitieren alle Benutzer davon. Wenn Sie die Ausführung einer App stören, werden alle Benutzer beeinträchtigt.
* Geben Sie vor der Freigabe einen aussagekräftigen Namen und eine Beschreibung für die App an. So können die Benutzer erkennen, um was für eine App es sich handelt, und sie in einer Liste auswählen. Klicken oder tippen Sie im Menü **Datei** in PowerApps Studio auf **App-Einstellungen**, und geben Sie eine Beschreibung ein.

### <a name="app-sharing-and-the-resources-the-app-uses"></a>App-Freigabe und von der App verwendete Ressourcen
Die meisten Apps stützen sich zumindest auf einen dieser Ressourcentypen:

* eine Verbindung mit einer Datenquelle
* ein lokales Datengateway
* ein benutzerdefinierter Connector
* eine Excel-Arbeitsmappe oder einen anderen Dienst
* einen Flow

Benutzer und Mitwirkende benötigen Berechtigungen für alle Datenverbindungen und Gateways, die von einer App verwendet werden. Einige Berechtigungen werden implizit in der App gewährt, andere müssen explizit zugewiesen werden. Weitere Informationen finden Sie unter [Freigeben von App-Ressourcen](share-app-resources.md).

Wenn Sie eine App freigeben, die eine frühere Version von Common Data Service verwendet, müssen Sie die Laufzeitberechtigung für Common Data Service separat erteilen. Wenn Sie hierzu nicht berechtigt sind, wenden Sie sich an Ihren Umgebungsadministrator. Wenn Sie eine App freigeben, die die aktuelle Version von Common Data Service verwendet, müssen Sie eine benutzerdefinierte Rolle erstellen und dieser Benutzer zuweisen. [Erfahren Sie mehr](../../administrator/database-security.md) über die Sicherheit für Common Data Service.

### <a name="what-isnt-supported"></a>Was wird nicht unterstützt?
* Sie können eine Freigabe für eine Sicherheitsgruppe durchführen, nicht jedoch für eine Verteilergruppe.
* Sie können Apps für Benutzer in Ihrer Organisation freigeben, nicht jedoch für Benutzer in einem anderen Mandanten.
* Sie können eine App erneut freigeben, wenn Sie über die Berechtigung **Kann bearbeiten** (nicht **Verwenden**) für diese App verfügen.
