---
title: Verwenden der Server-zu-Server-Authentifizierung mit mehreren Mandanten (Common Data Service) | MicrosoftDocs
description: 'Beschreibt, wie Sie einen Anwendungsbenutzer für Server-zu-Server-Authentifizierung mit Common Data Service konfigurieren.'
ms.custom: ''
ms.date: 2/28/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: paulliew
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-multi-tenant-server-to-server-authentication"></a>Verwenden Sie mehrinstanzenfähige Server-zu-Server-Authentifizierung

Dies ist das gebräuchlichste Szenario und jenes, das verwendet wird für Apps, die mithilfe von Microsoft AppSourceverteilt werden, aber Sie können Mehrinstanzen auch verwenden, ohne die Anwendung in Microsoft AppSource aufzuführen.  
  
Jede Common Data Service-Organisation ist einem Azure Active Directory-Mandanten zugeordnet. Ihre Webanwendung oder der Dienst ist mit einem eigenen Azure AD-Mandanten registriert.  
  
In diesem Szenario kann jeder Common Data Service Mandant Ihre mögliche mehrinstanzenfähige Anwendung sein, nachdem die Übereinstimmung vorhanden ist, auf die Daten zuzugreifen.  
  
<a name="bkmk_Requirements"></a>   

## <a name="requirements"></a>Anforderungen  

 Wenn Sie eine mehrinstanzenfähige Anwendung erstellen und testen, die eine Server-zu-Server (S2S) Authentifizierung verwendet, müssen die folgenden Aktionen ausgeführt werden:  
  
- Sie benötigen einen Azure AD-Mandanten, um Ihre Anwendung oder Ihren Service zu veröffentlichen.  
  
- 2 Common Data Service Abonnements  
  
  -   Einer muss dem Azure AD-Mandanten zugewiesen sein, denn Sie verwenden, um Ihre Anwendung oder Ihren Service zu veröffentlichen.  
  
  -   Der andere kann ein Testabonnement sein, das verwendet wird, um zu testen, wie Abonnenten auf Ihre Anwendung zugreifen.  
  
<a name="bkmk_DevelopAndTest"></a>  
 
## <a name="overview-develop-and-test-your-application"></a>Übersicht: Entwickeln und testen Sie Ihre Anwendung  

 Die Anwendung, die Sie erstellen, muss mit dem Azure AD-Mandanten angemeldet sein, den Sie verwenden, wenn Sie die Anwendung veröffentlichen.  
  
 Auf einer allgemeinen Ebene besteht der Prozess aus:  
  
1. Erstellen einer mehrinstanzenfähigen Webanwendung mit Ihrem Azure AD-Mandanten  
  
2. Erstellen Sie einen Anwendungsnutzer, der einer registrierten Anwendung in Ihrem  Common Data Service Mandant zugeordnet ist  
  
3. Erstellen Sie eine benutzerdefinierte Sicherheitsrolle und weisen Sie sie den Anwendungsbenutzern im Common Data Service Mandant zu.  
  
4. Testen Sie die Anwendung mithilfe des Mandanten Common Data Service  
  
5. Testen Sie die Anwendung mithilfe eines separaten Common Data Service Mandanten  
  
<a name="bkmk_CreateAMultitenantWebApp"></a>
   
## <a name="create-a-multi-tenant-web-application-registered-with-your-azure-ad-tenant"></a>Erstellen einer mehrinstanzenfähigen Webanwendung mit Ihrem Azure AD-Mandanten 
 
 Sie erstellen eine mehrinstanzenfähige Web-Anwendung oder einen Service, der Azure AD als Authentifizierungsanbieter verwendet.  
  
 Wie Sie dabei vorgehen, ist nicht Teil des Fokus in diesem Thema. Es gibt verschiedene Möglichkeiten, um die zu unterstützen und treffen Sie eine Wahl, die Ihren Anforderungen oder Einstellungen entspricht. Weitere Links zu mehr Informationen und Beispielen finden Sie hier:  
  
- [Erstellen einer mehrinstanzenfähigen SaaS-Webanwendung mit Azure AD &amp; OpenID Connect](https://azure.microsoft.com/documentation/samples/active-directory-dotnet-webapp-multitenant-openidconnect/)  
  
- [Erstellen einer mehrinstanzenfähigen SaaS Webanwendung die eine Web API mithilfe von Azure AD abruft](https://azure.microsoft.com/documentation/samples/active-directory-webapp-webapi-multitenant-openidconnect-aspnetcore/)  
  
  Azure AD erfordert die folgenden Werte, um Ihre Anwendung zu registrieren:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**Anwendungs-ID der URI**|Der Bezeichner für die Anwendung. Dieser Wert wird während der Authentifizierung an Azure AD gesendet, um anzugeben, für welche Anwendung der Anrufer einen Token möchte. Darüber hinaus ist dieser Wert im Token enthalten, sodass die Anwendung weiß, dass dies das beabsichtigte Ziel war.|  
|**Auf URL antworten und URI umleiten**|Bei einer Anfrage der Web API oder einer Webanwendung, ist die antwortende URL der Standort, an den Azure AD die Authentifizierungsantwort sendet, einschließlich eines Tokens, wenn die Authentifizierung erfolgreich war.|  
|**Client-ID**|Die ID für eine Anwendung, die über Azure AD generiert wird, wenn die Anwendung registriert ist. Wenn Sie einen Autorisierungscode oder einen Token anfordern, werden die Client-ID und der Schlüssel in der Azure AD bei der Authentifizierung gesendet.|  
|**Key**|Der Schlüssel, der zusammen mit einer Client-ID beim Authentifizieren von Azure AD gesendet wird, um eine Web-API anzurufen|  
  
 Wenn die Anwendung registriert ist, ist eine **Azure Active Directory-Objekt-ID** ein eindeutiger Bezeichner für die registrierte Anwendung.  
  
 Wenn Sie eine neue ASP.NETMVC Anwendung mit  Visual Studio erstellen, haben Sie die Optionen, um anzugeben, dass die Anwendung mehrinstanzenfähige Funktionen unterstützt. Die Vorlage für eine MVC-Anwendung bietet die Möglichkeit anzugeben, welche Art Authentifizierung erfolgt. Sie haben die Möglichkeit, die Authentifizierungsmethode zu wählen, indem Sie die Eigenschaften des Projektumfangs konfigurieren, wenn Sie es erstellen. Das folgende Diagramm zeigt die verfügbaren Optionen an:  
  
 ![Dialogfeld für die ASP.NET-MVC-Änderungsauthentifizierung](media/mvc-change-authentication-dialog.png "Dialogfeld für die ASP.NET-MVC-Änderungsauthentifizierung")  
  
 Wenn Sie ein Projekt für diese Optionen konfigurieren, wird es so konfiguriert, dass OWIN Middleware für eine Grundanwendung verwendet wird, die dieses Szenario unterstützt. Mit einigen grundlegenden Änderungen arbeiten sie mit Common Data Service. 
  
 Im Erstellungs- und Anmeldeprozess Ihrer Anwendung für die Entwicklung werden Sie wahrscheinlich `http://localhost` als **Anmelde-URL** und **Antworte-URL** Wert verwenden, damit Sie Ihre Anwendung lokal testen und von Fehlern befreien können, bevor Sie sie veröffentlichen. Sie müssen die Werte ändern, bevor Sie die App veröffentlichen.  
  
 Wenn Sie die App registrieren, müssen Sie einen Schlüssel erstellen, der auch als `ClientSecret` bekannt ist. Diese Schlüssel können für  1oder 2 Jahre konfiguriert werden. Als Host der Anwendung müssen Sie diesen Wert wie ein Kennwort behandeln und es liegt in Ihrer Verantwortung, die Schlüssel vor Ablauf zu erneuern. Sie möchten Key Vault verwenden. Weitere Informationen: [https://azure.microsoft.com/services/key-vault/](https://azure.microsoft.com/services/key-vault/)  
  
<a name="bkmk_GrantApplicationRights"></a>
   
## <a name="grant-your-application-rights-to-access-common-data-service-data"></a>Gewähren Sie Ihrer Anwendung die Rechte, auf Common Data Service Daten zuzugreifen
  
 Das ist der Grund, wieso Ihre Common Data Service-Instanz dem Azure AD-Mandanten zugeordnet werden muss. Wenn der Azure AD-Mandant keinem Common Data Service-Mandanten zugeordnet ist, können Sie folgende Schritte nicht ausführen.  
  
1. Wählen Sie [https://portal.azure.com](https://portal.azure.com) und anschließend **Azure Active Directory** aus.  
  
2. Klicken Sie auf **App-Registrierungen** und suchen Sie nach der Anwendung, die Sie in Visual Studio verwenden.  
  
3. Sie müssen Ihrer Anwendung Rechte geben, um auf die Common Data Service-Daten zuzugreifen. Im Bereich **API Zugriff** klicken Sie auf **Erforderliche Berechtigungen**. Sie sollten sehen, dass es bereits die Berechtigungen für **Windows Azure Active Directory** hat.  
  
4. Klicken Sie auf **Hinzufügen**, und wählen Sie **Eine API auswählen** aus. Wählen Sie in der Liste **Dynamics 365**aus, klicken Sie auf die Schaltfläche**Auswählen**.  
  
5. In **Berechtigungen wählen** wählen Sie **Zugriff auf Dynamics 365 als Organisationsbenutzer** aus. Klicken Sie dann auf die Schaltfläche **Auswählen**.  
  
6. Klicken Sie auf **Fertig**, um diese Berechtigungen hinzufügen. Wenn Sie fertig sind, sollten Sie die übernommenen Berechtigungen finden.  
  
   ![Erteilen von Dynamics 365-Berechtigungen für eine Anwendung](media/grant-crm-permissions-to-application.png "Erteilen von Dynamics 365-Berechtigungen für eine Anwendung")  
  
<a name="bkmk_CreateAppUser"></a>
   
## <a name="create-an-application-user--associated-with-the-registered-application--in-common-data-service"></a>Erstellen Sie einen Anwendungsnutzer mit der registrierten Anwendung in Common Data Service  
 Falls Ihre Anwendung auf die Common Data Service Daten  von einem Abonnent Ihrer Anwendung zugreift, erfordert dies einen Anwendungsbenutzer im Abonnent Common Data Service der Organisation. Wie jeder Common Data Service Benutzer muss diesem Anwendungsbenutzer mindestens eine Sicherheitsrolle zugeordnet werden, die Daten, die definiert, auf die der Benutzer auf zugreifen kann.  
  
 Die [SystemUser-Entität](reference/entities/systemuser.md) besitzt drei neue Attribute, um diese Daten zu speichern.  
  
|Schemaname|Name anzeigen|Typ|Beschreibung|  
|-----------------|------------------|----------|-----------------|  
|[ApplicationId](reference/entities/systemuser.md#BKMK_ApplicationId)|**Anwendungs-ID**|UniqueidentifierType|Der Bezeichner für die Anwendung. Dies wird für die Daten in einer anderen Anwendung verwendet.|  
|[ApplicationIdUri](reference/entities/systemuser.md#BKMK_ApplicationIdUri)|**URI der Anwendungs-ID**|StringType|Die URI die als eindeutigen logischen Bezeichner für die externe App verwendet wird.. Dies kann verwendet werden, um die Anwendung zu überprüfen|  
|[AzureActiveDirectoryObjectId](reference/entities/systemuser.md#BKMK_AzureActiveDirectoryObjectId)|**Objekt-ID von Azure AD**|UniqueidentifierType|Dies ist die Objekt-ID des Anwendungsverzeichnisses.|  
  
 Dieser `systemuser``AzureActiveDirectoryObjectId`-Eigenschaftswert muss ein Verweis in der Azure Active Directory-Objekt-ID der registrierten Anwendung werden. Dieser Verweis wird im Common Data Service festgelegt, wenn der Anwendungsbenutzer basierend auf dem `ApplicationId` erstellt wird.  
  
> [!NOTE]
>  Falls Sie Ihre Anwendung erstmalig mit Ihrem eigenen Common Data Service-Mandanten entwickeln und dem Azure AD-Mandant zugeordnet ist, können Sie den Anwendungsbenutzer einfach erstellen, da die registrierte Anwendung Teil des Azure AD-Mandanten ist.  
> 
>  Um jedoch den Anwendungsbenutzer in einer anderen Organisation für das Testen zu erstellen oder wenn ein Abonnent die Anwendung verwenden wird, müssen sie zuerst Zugriff auf Ihre Anwendung erhalten, und deshalb sind die Schritte in diesem Prozess unterschiedlich. Siehe [Testen Sie die Anwendung mithilfe eines separaten Dynamics 365-Mandanten](#bkmk_TestUsingSeparateTenant) für weitere Informationen.  
  
<a name="bkmk_CreateSecurityRole"></a>  
 
### <a name="create-a-security-role-for-the-application-user"></a>Erstellen einer Sicherheitsrolle für den Anwendungsbenutzer  

 Im nächsten Schritt können Sie einen Common Data Service Anwendungsbenutzer erstellen. Die Rechte und die Berechtigungen für diesen Benutzer werden durch eine benutzerdefinierte Sicherheitsrolle definiert. Bevor Sie den Anwendungsbenutzer erstellen, müssen Sie eine benutzerdefinierte Sicherheitsrolle erstellen, sodass Sie den Benutzer zuordnen können. Weitere Information finden Sie unter [Erstellen oder Bearbeiten einer Sicherheitsrolle](https://technet.microsoft.com/library/dn531130.aspx)  
  
> [!NOTE]
>  Der Anwendungsbenutzer darf nicht einer der standardmäßigen Common Data Service-Sicherheitsrollen zugeordnet werden. Sie müssen eine benutzerdefinierte Sicherheitsrolle zur Zuordnung mit dem Anwendungsbenutzer erstellen.  
  
<a name="bkmk_ManuallyCreateUser"></a>   

### <a name="manually-create-a-common-data-service-application-user"></a>Erstellen Sie einen Common Data Service Anwendungsbenutzer  

 Die Vorgehensweise, um diesen Benutzer zu erstellen, unterscheidet sich vom Erstellen eines lizenzierten Benutzers. Verwenden Sie die folgenden Schritte:  
  
1. Gehen Sie zu **Einstellungen** > **Sicherheit** > **Benutzer**  
  
2. Klicken Sie in der Dropdownliste der Ansichten auf **Anwendungsbenutzer**.  
  
3. Klicken Sie auf **Neu**. Überprüfen Sie dann, ob Sie das Formular **Anwendungsbenutzer** verwenden.  
  
    Wenn Sie die Felder **Anwendungs-ID**, **URI der Anwendungs-ID** und **Objekt-ID von Azure AD** im Formular nicht sehen, müssen Sie aus der Liste **Anwendungsbenutzer** auswählen:  
  
   ![Auswählen eines Anwendungsbenutzersformulars](media/select-application-user-form.PNG "Auswählen eines Anwendungsbenutzersformulars")  
  
4. Hinzufügen der entsprechenden Werte zu den Feldern:  
  
   |Feld|Value|  
   |-----------|-----------|  
   |**Anwendungs-ID**|Der Anwendungs-ID-Wert für die Anwendung, die bei Azure AD registriert ist.|  
   |**Vollständiger Name**|Der Name Ihrer Anwendung.|  
   |**Primäre E-Mail-Adresse**|Die E-Mail-Adresse, die Ihr  Abonnent verwenden soll, um Sie zu kontaktieren.|  
  
    Die Felder **Benutzername**, **URI der Anwendungs-ID** und **Objekt-ID von Azure AD** sind gesperrt und können keine Werte für diese Felder festlegen.  
  
    Wenn Sie diesen Benutzer erstellen, werden die Werte für diese Felder aus Azure AD basierend auf dem Wert der **Anwendungs-ID** abgerufen, wenn Sie den Benutzer speichern.  
  
5. Ordnen Sie den Anwendungsbenutzer der angepassten Sicherheitsrolle zu, die Sie in [Erstellen einer Sicherheitsrolle für den Anwendungsbenutzer](#bkmk_CreateSecurityRole) erstellt haben. Weitere Informationen: [Erstellen von Benutzern in Dynamics 365 (online) und Zuweisen von Sicherheitsrollen](/dynamics365/customer-engagement/admin/create-users-assign-online-security-roles)  
  
<a name="bkmk_TestUsingYourTenant"></a>  
 
## <a name="test-your-application-using-your-common-data-service-tenant"></a>Testen Sie die Anwendung mithilfe des Mandanten Common Data Service 
 
 Da die Anwendung bei Ihrem Azure AD-Mandanten angemeldet wurde und der Anwendungsbenutzer in Ihrer Entwicklungsorganisation bereits konfiguriert ist, können Sie Ihre Anwendung mit Ihrem eigenen Common Data Service-Mandanten weiterentwickeln. Aber dies ist kein gültiger Test für eine mehrinstanzenfähige Mandaten-Funktion. Sie müssen Ihre Anwendung mithilfe eines separaten Common Data Service Mandanten testen.  
  
<a name="bkmk_TestUsingSeparateTenant"></a>   

## <a name="test-your-application-using-a-separate-common-data-service-tenant"></a>Testen Sie die Anwendung mithilfe eines separaten Common Data Service Mandanten  

 Bevor Sie die Verwendung mit einem separaten Common Data Service-Mandanten testen, sollte ein Administrator für den Azure AD-Mandanten die Zustimmung für die Anwendung gewähren. Der Administrator gewährt die Zustimmung, indem Sie die Anwendung mithilfe eines Browsers navigieren. Bei der ersten Anmeldung bei der Anwendung, sehen sie einen Dialog wie dieser:  
  
 ![Erteilen der Zustimmung für den Zugriff auf Dynamics 365-Daten](media/grant-consent-to-access-crm-data.PNG "Erteilen der Zustimmung für den Zugriff auf Dynamics 365-Daten")  
  
 Wenn sie die Zustimmung gewähren, wird Ihre registrierte Anwendung der Azure AD Enterprise-Anwendungsliste hinzugefügt und sie wird für Benutzer des Azure AD-Mandanten bereitgestellt.  
  
 Erst nachdem ein Administrator die Zustimmung gewährt hat, können Sie die Anwendungsbenutzer im Abonnent Common Data Service-Mandanten erstellen. Sie können den Anwendungsbenutzer manuell erstellen mit den Schritten, die unter [Manuelles Erstellen eines Dynamics 365-Anwendungsbenutzers](#bkmk_ManuallyCreateUser) beschrieben werden.  
  
 Für die anfänglichen Tests möchten Sie diese Schritte allenfalls manuell ausführen. Wenn Sie bereit sind, Ihre Anwendung oder den Service dem Abonnent bereitzustellen, möchten Sie eine effizientere Vorgehensweise. Dies wird im nächsten Abschnitt behandeltet.  
  
<a name="bkmk_PrepareMethodToDeployAppUser"></a>
   
## <a name="prepare-a-method-to-deploy-the-application-user"></a>Bereiten Sie eine Möglichkeit vor, um den Anwendungsbenutzer bereitzustellen  

 Nachdem der Abonnent die Zustimmung zu Ihrer Anwendung oder zu Ihrem Service gewährt hat, brauchen Sie einen einfachen, verlässlichen Weg, um diesen Anwendungsbenutzer und andere erforderlichen Komponenten dem Common Data Service hinzuzufügen.  
  
 Sie müssen eine benutzerdefinierte Sicherheitsrolle einschließen, die definiert, welche Rechte der Anwendung erforderlich sind und überprüft dann, ob der Anwendungsbenutzer dieser benutzerdefinierten Sicherheitsrolle zugeordnet ist. Da eine benutzerdefinierte Sicherheitsrolle einer Lösung hinzugefügt werden kann, sollten Sie möglicherweise eine verwaltete Lösung vorbereiten, die Definition der benutzerdefinierten Sicherheitsrolle und andere Lösungskomponente Ihre Anwendung enthält.  
  
 Informationen zum Erstellen benutzerdefinierter Sicherheitsrollen finden Sie unter  
  
- [Erstellen oder Bearbeiten einer Sicherheitsrolle](/dynamics365/customer-engagement/admin/create-edit-security-role)  
- [Kopieren einer Sicherheitsrolle](/dynamics365/customer-engagement/admin/copy-security-role)  
- [Hinzufügen von Lösungskomponenten](/dynamics365/customer-engagement/customize/create-solution.md#add-solution-components)
  
  Informationen zum Erstellen einer Common Data Service-Lösung, finden Sie in den folgenden Themen:
  
- [Verwendung von Lösungen für die Anpassungen](../../maker/common-data-service/use-solutions-for-your-customizations.md)  
- [Packen und Verteilen von Erweiterungen mithilfe von Lösungen](/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions)  
  
  Allerdings kann der Anwendungsbenutzer nicht einer Lösung hinzugefügt werden. Sie müssen daher eine Möglichkeit bereitstellen, die Anwendungsbenutzer erstellen und diese den benutzerdefinierten Sicherheitsrollen zuordnen.  
  
  Es gibt mehrere Möglichkeiten, mit denen Sie das erreichen können, einschließlich dem Schreiben Ihres eigenen Programm mit dem Webservice und den Abonnenten das Programm ausführen lassen.  
  
  Der Dynamics 365 Package Deployer bietet eine Anwendung, die verwendet werden kann, um ein Paket vorzubereiten, um die Übertragung von Lösungen und Daten in eine andere Common Data Service-Organisation zu automatisieren. Weitere Informationen: [Erstellen von Paketen für den Dynamics 365 Package Deployer](/dynamics365/customer-engagement/developer/create-packages-package-deployer)  
  
### <a name="see-also"></a>Siehe auch  
 [Verwenden Sie Einzel-Mandanten-Server-zu-Server-Authentifizierung](use-single-tenant-server-server-authentication.md)   
 [Erstellen von Webanwendungen mit Server-to-Server-Authentifizierung (S2S)](build-web-applications-server-server-s2s-authentication.md)   
 [Verbinden mit Dynamics 365](/dynamics365/customer-engagement/developer/connect-customer-engagement)
