---
title: Einrichten einer Postman-Umgebung (Common Data Service für Apps)| MicrosoftDocs
description: Erfahren Sie, wie Sie eine Postman-Umgebung einrichten und konfigurieren, die mit Common Data Service Umgebungen verbunden ist.
ms.custom: ''
ms.date: 04/09/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 955BA444-A53D-4843-9429-833B1636E2B4
caps.latest.revision: 7
author: susikka
ms.author: susikka
manager: shujoshi
search.audienceType:
- developer
search.app:
- D365CE
ms.openlocfilehash: da8d3ac44d9993aee813347b327442789e7fb8a7
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2859923"
---
# <a name="set-up-a-postman-environment"></a>Einrichten einer Postman-Umgebung

Sie können Postman verwenden, um sich mit Ihrer Common Data Service-Instanz zu verbinden und Web-API-Anfragen zu erstellen, zu senden und Antworten anzuzeigen. Die Verwaltung der Authentifizierung ist ein Teil, den viele Nutzer schwierig finden. Dieses Thema beschreibt, wie Sie eine Postman-Umgebung so konfigurieren, dass sie für Ihre Common Data Service-Umgebungen funktioniert.

Sie können eine Postman-Umgebung verwenden, um einen Satz von Variablen zu speichern, die Sie für die Verbindung verwenden werden. Auf diese Werte kann innerhalb von Postman mit dieser Syntax zugegriffen werden: `{{name}}`. Weitere Informationen zu Postman-Variablen finden Sie unter [Postman-Dokumentation > Variablen](https://www.getpostman.com/docs/v6/postman/environments_and_globals/variables).

## <a name="prerequisites"></a>Voraussetzungen

* Haben Sie eine Power Apps Common Data Service Umgebung, mit der Sie sich verbinden können. 
* Downloaden und installieren Sie die [Postman Desktop Anwendung](https://www.getpostman.com/apps).

<a name="bkmk_connectcds"></a> 

## <a name="connect-with-your-common-data-service-environment"></a>Verbinden Sie sich mit Ihrer Common Data Service-Umgebung.

Diese Umgebung verwendet eine Client-ID für eine Anwendung, die für alle Common Data Service-Umgebungen registriert ist. 
 
Sie können die Werte `clientid` und `callback` aus diesen Anweisungen verwenden.  Wenn Sie jedoch eine eigene Anwendung erstellen, sollten Sie eine eigene Azure Active Directory (Azure AD) Anwendung registrieren.
 
Um Ihre eigene Azure AD-Anwendung zu registrieren, lesen Sie die unter [Walkthrough: Registrieren Sie eine Common Data Service App mit Azure Active Directory](../walkthrough-register-app-azure-active-directory.md).

Verwenden Sie diese Schritte, um eine Postman-Umgebung zu erstellen, mit der Sie sich mit Ihrer Common Data Service-Instanz verbinden können:

1. Starten Sie die Postman-Desktop-Anwendung.
1. Klicken Sie auf das Symbol **Umgebungsoptionen** in der rechten oberen Ecke. 
1. In der sich öffnenden Dialogbox **Umgebungen verwalten** klicken Sie auf **Hinzufügen**, um eine neue Umgebung hinzuzufügen.
  
  ![Klicken Sie auf die Schaltfläche „Hinzufügen“, um eine neue Postman-Umgebung hinzuzufügen](media/postman-manage-env.png "Klicken Sie auf die Schaltfläche „Hinzufügen“, um eine neue Postman-Umgebung hinzuzufügen")<br>
  
1. Geben Sie in dem Dialogfeld, das geöffnet wird, einen Namen für die Umgebung ein. Fügen Sie dann den folgenden Schlüssel/Wert-Paare im Editierbereich hinzu.<br>

    | Variablenname | Value |
    |----|---|
    |`url`|`https://<add your environment name, like ‘myorg.crm’>.dynamics.com`|
    |`clientid`|`51f81489-12ee-4a9e-aaae-a2591f45987d`|
    |`version`|`9.0`|
    |`webapiurl`|`{{url}}/api/data/v{{version}}/`|
    |`callback`|`https://callbackurl`|
    |`authurl`|`https://login.microsoftonline.com/common/oauth2/authorize?resource={{url}}`|

    ![Erstellen Sie eine neue Postman-Umgebung für die Verbindung mit der Online-Instanz](media/postman-add-online-env.png "Erstellen Sie eine neue Postman-Umgebung für die Verbindung mit der Online-Instanz")<br>
1. Ersetzen Sie den Wert des Platzhalters für die Instanz-URL durch die URL Ihrer Common Data Service-Instanz und wählen Sie **Hinzufügen**, um die Umgebung zu speichern.

1. Schließen Sie den Dialog **Umgebungen verwalten**.  

### <a name="generate-an-access-token-to-use-with-your-environment"></a>Generieren eines Zugriffstokens für Ihre Umgebung

Um eine Verbindung über **OAuth 2.0** herzustellen, benötigen Sie ein Zugriffstoken. Führen Sie die folgenden Schritte aus, um ein neues Zugriffstoken zu erhalten.

1. Stellen Sie sicher, dass die neue Umgebung, die Sie angelegt haben, ausgewählt ist.
1. Wählen Sie die Registerkarte **Autorisierung**.
1. Setzen Sie den **Typ** auf **OAuth 2.0**.
1. Überprüfen Sie, ob Sie die von Ihnen erstellte Umgebung ausgewählt haben.
1. Klicken Sie auf **Neues Zugriffstoken abrufen**.

    ![Setzen Sie die Registerkarte "Autorisierung" auf OAuth 2.0.](media/postman-set-type.png)<br>
1. Stellen Sie im Dialog die folgenden Werte ein. Wählen Sie `Implicit` aus dem Dropdown-Menü **Gewähren-Typ**. Sie können den **Tokennamen** auf einen beliebigen Wert setzen und andere Schlüssel auf den Standardwerten belassen.<br>

    ![Neues Zugriffstoken abrufen](media/postman-access-token.png "Neues Zugriffstoken abrufen")<br>

    > [!NOTE]
    > Wenn Sie Umgebungen in Postman für mehrere Common Data Service-Instanzen mit unterschiedlichen Benutzerdaten konfigurieren, müssen Sie möglicherweise die von Postman zwischengespeicherten Cookies löschen. Klicken Sie auf den Link **Cookies**, der sich unter dem Button **Senden** befindet und entfernen Sie die gespeicherten Cookies aus dem Dialog **Cookies verwalten**.<br>![Cookies löschen](media/postman-cookies.png "Cookies löschen")<br>
    > Einige dieser Cookies sind sehr langlebig. Sie können einige davon in Gruppen löschen, andere müssen jedoch einzeln gelöscht werden.   Möglicherweise müssen Sie dies zweimal tun, um sicherzustellen, dass keine Cookies verbleiben.

1. Wählen Sie **Token anfordern** aus. Dabei erscheint eine Azure Active Directory Anmeldeseite. Geben Sie Ihren Benutzernamen und Ihr Kennwort ein.
1. Nachdem das Token generiert wurde, scrollen Sie nach unten und klicken Sie auf **Token verwenden**. Dadurch wird der Dialog **Zugriffstokens verwalten** geschlossen. 
1. Nachdem Sie ein Token hinzugefügt haben, können Sie auswählen, welches Token für Anforderungen angewendet werden soll. Klicken Sie auf die Dropdown-Liste **Verfügbare Token** und wählen Sie das soeben erstellte Token aus. Der Autorisierungs-Header wird der Web-API-Anforderung hinzugefügt.

Siehe [Test Ihrer Verbindung](#test-your-connection) für Schritte zur Überprüfung Ihrer Verbindung.

## <a name="test-your-connection"></a>Testen Ihrer Verbindung

Erstellen Sie eine neue Web-API-Anfrage, um die Verbindung mit Ihrer Common Data Service-Instanz zu testen. Verwenden des <xref href="Microsoft.Dynamics.CRM.WhoAmI?text=WhoAmI function" />Formular-Assistenten:
1. Wählen Sie `GET` als HTTP-Methode und fügen Sie `{{webapiurl}}WhoAmI` im Editierbereich hinzu.
  ![WhoAmI-Funktionsanforderung](media/postman-whoami-request.png "WWhoAmI-Funktionsanforderung)
2. Klicken Sie auf **Senden**, um diese Anfrage zu senden.
3. Wenn Ihre Anfrage erfolgreich ist, sollten Sie die Daten der <xref href="Microsoft.Dynamics.CRM.WhoAmIResponse?text=WhoAmIResponse ComplexType" /> sehen, die von <xref href="Microsoft.Dynamics.CRM.WhoAmI?text=WhoAmI Function" /> zurückgegeben wird.

## <a name="see-also"></a>Siehe auch

[Verwenden von Postman, um Operationen durchzuführen](use-postman-perform-operations.md)<br>
[Walkthrough: Registrieren Sie eine Common Data Service App bei Azure Active Directory](../walkthrough-register-app-azure-active-directory.md)
