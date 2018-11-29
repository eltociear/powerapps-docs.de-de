---
title: 'Exemplarische Vorgehensweise: Registrieren einer App bei Azure Active Directory (Common Data Service für Apps) | Microsoft Docs'
description: 'In dieser exemplarischen Vorgehensweise wird beschrieben, wie Sie eine Anwendung bei Azure Active Directory registrieren, sodass diese eine Verbindung mit der "Common Data Service für Apps"-Umgebung herstellen kann, sich per OAuth Authentifizieren und auf Webdienste zugreifen kann.'
keywords: ''
ms.date: 10/31/2018
ms.service:
  - powerapps
ms.custom:
  - ''
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
---

# <a name="walkthrough-register-an-app-with-azure-active-directory"></a>Exemplarische Vorgehensweise: Registrieren einer App bei Azure Active Directory

In dieser exemplarischen Vorgehensweise wird beschrieben, wie Sie eine Anwendung bei Azure Active Directory registrieren, wodurch ein Benutzer mit einem PowerApps-Benutzerkonto eine Verbindung mit seiner "Common Data Service (CDS) für Apps"-Umgebung von externen Client-Anwendungen aus mithilfe einer OAuth-Authentifizierung herstellen kann.

> [!IMPORTANT]
> PowerApps bietet Ihnen auch die Möglichkeit der Server-to-Server (S2S)-Authentifizierung, um eine Verbindung zur "CDS für Apps"-Umgebung von externen Anwendungen und Diensten über das spezielle Anwendungsbenutzerkonto herzustellen. Die S2S-Authentifizierung ist die gängige Methode, mit der auf Microsoft AppSource registrierte Anwendungen auf die Daten ihrer Abonnenten zugreifen. Weitere Informationen: Weitere Informationen finden Sie unter: [Webanwendungen mit der Server-zu-Server-(S2S)-Authentifizierung erstellen.](build-web-applications-server-server-s2s-authentication.md).


App-Registrierung in Azure Active Directory erfolgt normalerweise per ISVs, die externe Client-Anwendungen entwickeln möchten, um Daten in CDS für Apps zu lesen und zu schreiben. Das Registrieren einer App in Azure Active Directory stellt Ihnen Werte für **Anwendungs-ID** und **Umleitungs-URI** bereit, die ISVs im Authentifizierungscode ihrer Client-Anwendung verwenden können. Wenn Endbenutzer die Anwendung des ISV zum *ersten Mal* verwenden, um eine Verbindung zu Ihrer "CDS für Apps"-Umgebung herzustellen, indem sie ihre "CDS für Apps"-Anmeldeinformationen angeben, wird dem Endbenutzer ein Zustimmungsformular angezeigt. Nach Zustimmung zur Verwendung ihres „CDS für Apps”-Kontos mit der Anwendung des ISV, können Endbenutzer von einer externen Anwendung aus eine Verbindung zur "CDS für Apps"-Umgebung herstellen. Das Zustimmungsformular wird nach dem ersten Benutzer, der bereits der Verwendung der App des ISV zugestimmt hat, nicht erneut anderen Benutzern angezeigt. Die Apps, die in Azure Active Directory registriert sind, sind für mehrere Mandanten ausgelegt. Das bedeutet, dass andere "CDS für Apps"-Benutzer von anderen Mandanten eine Verbindung zu ihrer Umgebung mithilfe der App des ISV herstellen können. 

App-Registrierung kann auch von einem Anwendungsentwickler oder einem einzelnen Benutzer durchgeführt werden, der eine Client-Anwendung erstellt, um eine Verbindung zu CDS für Apps herzustellen und dort Daten zu lesen/zu scheiben. Verwenden Sie die Werte **Anwendungs-ID** und **Umleitungs-URI** aus Ihrer registrierten App im Authentifizierungscode Ihrer Client-Anwendung, um eine Verbindung mit der "CDS für Apps"-Umgebung von Ihrer Client-Anwendung aus herzustellen und die erforderlichen Vorgänge auszuführen. Beachten Sie, dass wenn die App im selben Mandanten wie Ihre "CDS für Apps"-Umgebung registriert wird, Ihnen kein Zustimmungsformular angezeigt wird, wenn Sie eine Verbindung von Ihrer Client-Anwendung mit Ihrer "CDS für Apps"-Umgebung herstellen.

## <a name="prerequisites"></a>Voraussetzungen  
-   Der Benutzer, der die Anwendung registriert, muss ein Benutzerkonto mit einer Systemadministrator-Sicherheitsrolle und die globale Administratorrolle für das Office 365-Abonnement haben.  
  
-   Ein Azure-Abonnement für die Anwendungsregistrierung. Eine Probefirma funktioniert auch.  
  
    

## <a name="create-an-application-registration"></a>Erstellen einer Anwendungsregistrierung 
  
1.  [Melden Sie sich an](http://manage.windowsazure.com) im Azure-Verwaltungsportal mithilfe eines Kontos mit Administratorberechtigungen. Sie müssen ein Konto im gleichen Office 365-Abonnement (Mandant) verwenden, in dem Sie auch die App registrieren möchten.<br><br> Sie können auch auf das Azure-Verwaltungsportal über das Office 365 [Admin Center](https://portal.office.com/adminportal) zugreifen, indem Sie das Element **Admin Center** im linken Navigationsbereich erweitern und **Azure AD** auswählen.  
  
    > [!NOTE]
    > Falls Sie keinen Azure-Mandanten (Konto) haben oder darüber zwar verfügen, aber Ihr Office 365-Abonnement mit Dynamics 365 (online) nicht in Ihrem Azure-Abonnement verfügbar ist, folgen Sie den Anweisungen im Thema [Einrichten des Azure Active Directory-Zugriffs für die Entwickler-Website](https://docs.microsoft.com/en-us/office/developer-program/office-365-developer-program), um die beiden Konten zuzuordnen.<br><br> Wenn Sie kein Konto haben, können Sie sich für eines anmelden, indem Sie eine Kreditkarte verwenden. Allerdings ist das Konto kostenlos für die Anwendungsregistrierung, und Ihre Kreditkarte wird nicht belastet, wenn Sie nur den Vorgehensweisen folgen, die in diesem Thema genannt werden, um mindestens eine App zu registrieren. Weitere Informationen: [Active Directory-Preisberechnungsdetails](http://azure.microsoft.com/pricing/details/active-directory/)  
  
1. Folgen Sie im Azure-Verwaltungsportal den Schritten, wie sie im Abschnitt [Hinzufügen einer Anwendung](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-integrating-applications#adding-an-application) im Azure Active Directory-Entwicklerhandbuch beschrieben werden, um eine App zu erstellen. 
  
1. Beim Erstellen einer App in Azure Active Directory wird eine eindeutige **Anwendungs-ID** (zuvor bezeichnet als **Client-ID**) für Ihre Anwendung generiert, und die neu registrierte App wird auf der Seite für registrierte Apps angezeigt. Klicken Sie auf die App, um die App-Informationsseite zu öffnen.

1. Auf der App-Informationsseite zeigen Sie auf den Wert **Anwendungs-ID** (zuvor als **Client-ID** bezeichnet), und wählen Sie das Symbol **Zum Kopieren klicken** aus, um den Wert zu kopieren, da Sie diesen im Authentifizierungscode Ihrer Anwendung oder in der Datei app.config, sofern erforderlich, angeben müssen.

    ![Anwendungs-ID kopieren](media/Azure-copy-app-id.png "Anwendungs-ID kopieren")
  
1. Wählen Sie **Einstellungen** auf der App-Informationsseite aus, und verwenden Sie die Option **Umleitungs-URIs** auf der Seite **Einstellungen**, um den Umleitungs-URI-Wert für Ihre App zu kopieren. Sie können nach Bedarf auch weitere URIs ändern und hinzufügen. Für eine App des Anwendungstyps **Web-App / API** wird Ihnen die Option **Antwort-URLs** statt der Option **Umleitungs-URIs** angezeigt.

## <a name="apply-permissions"></a>Berechtigungen anwenden

1. Auf der Seite **Einstellungen** wählen Sie **Erforderliche Berechtigungen** > **Hinzufügen** aus, um Berechtigungen für die registrierte App hinzuzufügen.

    ![App-Berechtigung hinzufügen](media/Azure-add-app-permission.png "App-Berechtigung hinzufügen")
  
1. Auf der Seite **API-Zugriff hinzufügen**:
    - Wählen Sie **API auswählen** > **Dynamics CRM Online** aus, und klicken Sie dann auf **Auswählen**.

      ![App-Berechtigung hinzufügen](media/Azure-add-api-access.png "App-Berechtigung hinzufügen")  
   
    - Wählen Sie **Berechtigungen auswählen** > **Auf CRM Online als Organisationsbenutzer zugreifen** aus, und klicken Sie dann auf **Auswählen**.
  
      ![Delegierte Berechtigung hinzufügen](media/azure-add-permission.PNG "Delegierte Berechtigung hinzufügen")  

    - Wählen Sie **Fertig** aus, um die delegierte Berechtigung der registrierten App hinzuzufügen.

Dadurch wird die Registrierung Ihrer Anwendung in Azure Active Directory abgeschlossen.

## <a name="additional-configuration-options"></a>Zusätzliche Konfigurationsoptionen

Falls Ihre Anwendung eine Single-Page-Anwendung (SPA) sein wird, die von CORS abhängig ist, müssen Sie die App-Registrierung so konfigurieren, dass sie den impliziten Flow unterstützt. Mehr Informationen: [Exemplarische Vorgehensweise: Registrierung und Konfiguration einer SPA-Anwendung mit adal.js](walkthrough-registering-configuring-simplespa-application-adal-js.md)

Wenn Ihre Anwendung Server-zu-Server-Verbindungen unterstützt, finden Sie Informationen unter [Server-zu-Server-Authentifizierung mit mehreren Mandanten verwenden](use-multi-tenant-server-server-authentication.md)

  
### <a name="see-also"></a>Siehe auch  
 [Anwendungsregistrierung in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)    
 [Authentifizieren von Benutzern mit Dynamics 365-Webdiensten](authentication.md)