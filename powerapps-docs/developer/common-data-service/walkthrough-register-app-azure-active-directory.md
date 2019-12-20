---
title: 'Exemplarische Vorgehensweise: Registrieren einer App bei Azure Active Directory (Common Data Service) | Microsoft Docs'
description: In dieser exemplarischen Vorgehensweise wird beschrieben, wie eine Desktop-Client- oder Smartphone-Anwendung in Azure Active Directory registriert wird, damit sie eine Verbindung mit der Common Data Service-Umgebung herstellen, sich per OAuth authentifizieren und auf Webdienste zugreifen kann.
keywords: ''
ms.date: 04/01/2019
ms.service: powerapps
ms.topic: article
ms.assetid: 86c4a8a8-7401-6d75-7979-3b04b506eb0c
author: paulliew
ms.author: jdaly
manager: ryjones
ms.reviewer: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: b2cf649ad1bcba55e32192a8f72f3a7c7aabf10f
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2859931"
---
# <a name="walkthrough-register-an-app-with-azure-active-directory"></a>Exemplarische Vorgehensweise: Registrieren einer App mit Azure Active Directory

In dieser exemplarischen Vorgehensweise wird beschrieben, wie Sie eine Anwendung mit Azure Active Directory registrieren, wodurch ein Benutzer mit einem Power Apps-Benutzerkonto eine Verbindung mit seiner Common Data Service-Umgebung von externen Client-Anwendungen aus mit Hilfe einer OAuth-Authentifizierung herstellen kann.

> [!IMPORTANT]
> Power Apps bietet Ihnen auch die Möglichkeit der Server-to-Server (S2S)-Authentifizierung, um eine Verbindung zur Common Data Service-Umgebung von externen Anwendungen und Diensten über das spezielle Anwendungsbenutzerkonto herzustellen. Die S2S-Authentifizierung ist der normale Weg, über den bei Microsoft AppSource registrierte Apps auf die Daten der Abonnenten zugreifen. Weitere Informationen finden Sie unter: [Webanwendungen mit der Server-zu-Server-(S2S)-Authentifizierung erstellen.](build-web-applications-server-server-s2s-authentication.md).

App-Registrierung in Azure Active Directory erfolgt normalerweise per ISVs, die externe Client-Anwendungen entwickeln möchten, um Daten in Common Data Service zu lesen und zu schreiben. Das Registrieren einer App in Azure Active Directory stellt Ihnen Werte für **Anwendungs-ID** und **Umleitungs-URI** bereit, die ISVs im Authentifizierungscode ihrer Client-Anwendung verwenden können. Wenn Endbenutzer die Anwendung des ISV *zum ersten Mal* verwenden, um eine Verbindung zu Ihrer Common Data Service-Umgebung herzustellen, indem sie ihre Common Data Service-Anmeldeinformationen angeben, wird dem Endbenutzer ein Zustimmungsformular angezeigt. Nach Zustimmung zur Verwendung ihres Common Data Service-Kontos mit der Anwendung des ISV, können Endbenutzer von einer externen Anwendung aus eine Verbindung zur Common Data Service-Umgebung herstellen. Das Zustimmungsformular wird nach dem ersten Benutzer, der bereits der Verwendung der App des ISV zugestimmt hat, nicht erneut anderen Benutzern angezeigt. Die Apps, die in Azure Active Directory registriert sind, sind für mehrere Mandanten ausgelegt. Das bedeutet, dass andere Common Data Service-Benutzer von anderen Mandanten eine Verbindung mit ihrer Umgebung mithilfe der App des ISV herstellen können. 

Die App-Registrierung kann auch von einem Anwendungsentwickler oder einem einzelnen Benutzer durchgeführt werden, der eine Client-Anwendung erstellt, um eine Verbindung zu Common Data Service herzustellen und dort Daten zu lesen/zu scheiben. Verwenden Sie die Werte **Anwendungs-ID** und **Umleitungs-URI** aus Ihrer registrierten App im Authentifizierungscode Ihrer Client-Anwendung, um eine Verbindung mit der Common Data Service-Umgebung von Ihrer Client-Anwendung aus herzustellen und die erforderlichen Vorgänge auszuführen. Beachten Sie, dass wenn die App im selben Mandanten wie Ihre Common Data Service-Umgebung registriert wird, Ihnen kein Zustimmungsformular angezeigt wird, wenn Sie eine Verbindung von Ihrer Client-Anwendung mit Ihrer Common Data Service-Umgebung herstellen.

## <a name="prerequisites"></a>Voraussetzungen  

-   Der Benutzer, der die Anwendung registriert, muss ein Benutzerkonto mit einer Systemadministrator-Sicherheitsrolle und die globale Administratorrolle für das Office 365-Abonnement haben.  
  
-   Ein Azure-Abonnement für die Anwendungsregistrierung. Eine Probefirma funktioniert auch.  
  
## <a name="create-an-application-registration"></a>Erstellen einer Anwendungsregistrierung 
  
1. Melden Sie sich beim [Azure-Portal](https://go.microsoft.com/fwlink/?linkid=2083908) mit einem Konto mit Administratorrechten an. Sie müssen ein Konto im gleichen Office 365-Abonnement (Mandant) verwenden, in dem Sie auch die App registrieren möchten. Sie können das Azure-Portal auch über die Schaltfläche Office 365 [Admin Center](https://admin.microsoft.com/adminportal) aufrufen, indem Sie das Element **Admin Center** im linken Navigationsbereich erweitern und **Azure Active Directory** auswählen.  
  
   > [!NOTE]
   > Wenn Sie keinen Azure-Mandaten (Konto) haben oder wenn Sie einen haben, aber Ihr Office365-Abonnement mit Common Data Service in Ihrem Azure-Abonnement nicht verfügbar ist, folgen Sie den Anweisungen im Thema [Einrichten des Azure Active Directory-Zugriffs für Ihre Entwicklerseite](https://msdn.microsoft.com/office/office365/HowTo/setup-development-environment), um die beiden Konten zu verbinden.<br><br> Wenn Sie kein Konto haben, können Sie sich für eines anmelden, indem Sie eine Kreditkarte verwenden. Allerdings ist das Konto kostenlos für die Anwendungsregistrierung, und Ihre Kreditkarte wird nicht belastet, wenn Sie nur den Vorgehensweisen folgen, die in diesem Thema genannt werden, um mindestens eine App zu registrieren. Weitere Informationen: [Active Directory-Preisberechnungsdetails](https://azure.microsoft.com/pricing/details/active-directory/)  
  
2. Wählen Sie im Azure-Portal im linken Bereich **Azure Active Directory** und wählen Sie **App-Registrierungen** und klicken Sie auf **Neue Registrierung**.
    
    ![Azure-App-Registrierung](media/azure-app-registrations-page.png "Azure-App-Registrierung")  

3. Geben Sie unter **Registrieren einer Anmeldeseite** die Registrierungsinformationen Ihrer Anmeldung ein:
   - Geben Sie im Abschnitt **Name** einen aussagekräftigen Anwendungsnamen ein, der den Benutzern angezeigt wird.
   - Wählen Sie **Konten in einem beliebigen Organisationsverzeichnis** unter **Unterstützte Kontoarten**.
   - Legen Sie die **Redirect URI** fest.
   - Klicken Sie auf **Registrieren**, um die Anwendung zu erstellen.

      ![Seite „Neue App-Registrierung“](media/new-app-registration-page.png "Seite „Neue App-Registrierung“")

5. Bewegen Sie auf der Seite App-**Übersicht** den Mauszeiger über den Wert **Anwendungs-ID (Client)** und wählen Sie das Symbol **In die Zwischenablage kopieren**, um den Wert zu kopieren, da Sie dies gegebenenfalls im Authentifizierungscode Ihrer Anwendung oder in der app.config-Datei angeben müssen.

    ![Anwendungs-ID kopieren](media/app-registration-overview-page.png "Anwendungs-ID kopieren")
  
5. Wählen Sie die Registerkarte **Manifest**, setzen Sie im Manifest Editor die Eigenschaft **allowPublicClient** auf **true** und klicken Sie auf **Speichern**.
   
    ![App-Registrierungsmanifest](media/app-registration-manifest-page.png "App-Registrierungsmanifest")

6. Wählen Sie die Registerkarte **API-Berechtigungen**, klicken Sie auf **Eine Berechtigung hinzufügen**. 

    ![App-Berechtigung hinzufügen](media/azure-api-permissions-page.png "App-Berechtigung hinzufügen")

7. Wählen Sie **Dynamics CRM** unter der Registerkarte **Microsoft APIs**.
    
    ![API auswählen](media/app-registration-select-api-page.png "API auswählen")    

8. Klicken Sie auf **Delegierte Berechtigungen** und überprüfen Sie die Optionen und klicken Sie auf **Berechtigungen hinzufügen**. 
    
    ![Berechtigungen delegieren](media/app-registration-delegate-permissions-page.png "Berechtigung delegieren")

Dadurch wird die Registrierung Ihrer Anwendung in Azure Active Directory abgeschlossen.

## <a name="additional-configuration-options"></a>Zusätzliche Konfigurationsoptionen

Falls Ihre Anwendung eine Single-Page-Anwendung (SPA) sein wird, die von CORS abhängig ist, müssen Sie die App-Registrierung so konfigurieren, dass sie den impliziten Flow unterstützt. Mehr Informationen: [Exemplarische Vorgehensweise: Registrierung und Konfiguration einer SPA-Anwendung mit adal.js](walkthrough-registering-configuring-simplespa-application-adal-js.md)

Wenn Ihre Anwendung Server-zu-Server-Verbindungen unterstützt, finden Sie Informationen unter [Server-zu-Server-Authentifizierung mit mehreren Mandanten verwenden](use-multi-tenant-server-server-authentication.md)
  
### <a name="see-also"></a>Siehe auch  
 [Anwendungsregistrierung in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)    
 [Authentifizieren von Benutzern durch Common Data Service-Webdienste](authentication.md)
