---
title: 'Exemplarische Vorgehensweise: Registrierung und Konfiguration von SimpleSPA-Anwendung mit adal.js (Common Data Service) | Microsoft Docs'
description: Diese Vorgehensweise beschreibt den Prozess des Registrierens und Konfigurierens der grundlegenden Single-Page-Anwendung (SPA) für den Zugriff auf Daten in Dynamics 365 Customer Engagement mithilfe von adal.js und Cross-origin Resource Sharing (CORS).
keywords: ''
ms.date: 02/12/2019
ms.service:
  - powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: a327d2ff-e252-61cf-1190-6a974130ef19
author: paulliew
ms.author: jdaly
manager: ryjones
ms.reviewer: null
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="walkthrough-registering-and-configuring-a-spa-application-with-adaljs"></a>Exemplarische Vorgehensweise: SPA-Anwendung mit adal.js registrieren und konfigurieren

Diese exemplarische Vorgehensweise beschreibt den Prozess des Registrierens und Konfigurierens der grundlegendsten Single-Page-Anwendung (SPA) für den Zugriff auf Daten in Common Data Service mithilfe von adal.js und Cross-origin Resource Sharing (CORS). Weitere Informationen: [Verwenden von OAuth mit Cross-Origin Resource Sharing, um eine Single Page-Anwendung mit Dynamics 365 (online) zu verbinden](oauth-cross-origin-resource-sharing-connect-single-page-application.md)
  
## <a name="prerequisites"></a>Voraussetzungen  
  
- PowerApps von Common Data Service  
  
- Sie müssen über ein Dynamics 365 (online)-Systembenutzerkonto mit einer Administratorrolle für Office 365 verfügen.  
  
- Ein Azure-Abonnement zur Registrierung Ihrer Anwendung. Eine Probefirma funktioniert auch.  
  
- Visual Studio 2017  
  
<a name="bkmk_goal"></a>

## <a name="goal-of-this-walkthrough"></a>Ziel dieser exemplarischen Vorgehensweise

Wenn Sie diese exemplarische Vorgehensweise abschließen, können Sie eine einfache SPA-Anwendung in Visual Studio ausführen, über die sich der Benutzer authentifizieren und Daten aus Common Data Service abrufen kann. Diese Anwendung besteht aus einer exemplarischen HTML-Seite.  

Wenn Sie die Anwendung debuggen, gibt es zunächst nur eine Schaltfläche **Anmelden**.  

Klicken Sie auf **Anmelden**. Sie werden zu Anmeldeseite umgeleitet und geben Ihre Anmeldedaten ein.  

Nachdem Sie Ihre Anmeldeinformationen eingegeben haben, werden sie wieder zur HTML-Seite umgeleitet. Dort finden Sie die Schaltflächen **Anmelden**, **Abmelden** und **Firmen abrufen**. Sie sehen außerdem eine Begrüßung mit Informationen zu Ihrem Benutzerkonto.  

Klicken Sie auf die Schaltfläche **Firmen abrufen**, um 10 Firmendatensätze aus Ihrer Common Data Service-Organisation abzurufen. Die Schaltfläche **Firmen abrufen** ist wie im folgenden Screenshot dargestellt deaktiviert:  
  
![Die SimpleSPA-Seite](media/simple-spa.png "Die SimpleSPA-Seite")  

> [!NOTE]
>  Das erstmalige Laden von Daten aus Common Data Service kann langsam sein während die Authentifizierung stattfindet. Nachfolgende Vorgänge sind jedoch deutlich schneller.  

Schließlich können Sie auf die Schaltfläche **Abmelden** klicken, um sich abzumelden.  

> [!NOTE]
>  Diese SPA-Anwendung ist nicht als Muster zum Entwickeln von SPA-Anwendungen vorgesehen. Sie dient nur zu Beschreibung des Vorgangs der Registrierung und Konfiguration der Anwendung.  

<a name="bkmk_createwebapp"></a>

## <a name="create-a-web-application-project"></a>Erstellen eines Webanwendungsprojekts  
  
1.  Erstellen Sie mit Visual Studio 2017 ein neues **ASP.NET-Webanwendung**-Projekt und nutzen Sie die Vorlage **Leer**. Sie können das Projekt beliebig benennen.  
  
    Möglicherweise können Sie auch frühere Versionen von Visual Studio verwenden. Für diese Schritte wird jedoch Visual Studio 2017 verwendet.  
  
2.  Fügen Sie dem Projekt eine neue HTML-Seite namens `SimpleSPA.html` hinzu und fügen Sie den folgenden Code ein:  
  
    ```html  
    <!DOCTYPE html>  
    <html>  
    <head>  
     <title>Simple SPA</title>  
     <meta charset="utf-8" />  
     <script src="https://secure.aadcdn.microsoftonline-p.com/lib/1.0.17/js/adal.min.js"></script>  
     <script type="text/javascript">  
      "use strict";  
  
      //Set these variables to match your environment  
      var organizationURI = "https://[organization name].crm.dynamics.com"; //The URL of your Common Data Service organization  
      var tenant = "[xxx.onmicrosoft.com]"; //The name of the Azure AD organization you use  
      var clientId = "[client id]"; //The ClientId you got when you registered the application  
      var pageUrl = "http://localhost:[PORT #]/SimpleSPA.html"; //The URL of this page in your development environment when debugging.  
  
      var user, authContext, message, errorMessage, loginButton, logoutButton, getAccountsButton, accountsTable, accountsTableBody;  
  
      //Configuration data for AuthenticationContext  
      var endpoints = {  
       orgUri: organizationURI  
      };  
  
      window.config = {  
       tenant: tenant,  
       clientId: clientId,  
       postLogoutRedirectUri: pageUrl,  
       endpoints: endpoints,  
       cacheLocation: 'localStorage', 
      };  
  
      document.onreadystatechange = function () {  
       if (document.readyState == "complete") {  
  
        //Set DOM elements referenced by scripts  
        message = document.getElementById("message");  
        errorMessage = document.getElementById("errorMessage");  
        loginButton = document.getElementById("login");  
        logoutButton = document.getElementById("logout");  
        getAccountsButton = document.getElementById("getAccounts");  
        accountsTable = document.getElementById("accountsTable");  
        accountsTableBody = document.getElementById("accountsTableBody");  
  
        //Event handlers on DOM elements  
        loginButton.addEventListener("click", login);  
        logoutButton.addEventListener("click", logout);  
        getAccountsButton.addEventListener("click", getAccounts);  
  
        //call authentication function  
        authenticate();  
  
        if (user) {  
         loginButton.style.display = "none";  
         logoutButton.style.display = "block";  
         getAccountsButton.style.display = "block";  
  
         var helloMessage = document.createElement("p");  
         helloMessage.textContent = "Hello " + user.profile.name;  
         message.appendChild(helloMessage)  
  
        }  
        else {  
         loginButton.style.display = "block";  
         logoutButton.style.display = "none";  
         getAccountsButton.style.display = "none";  
        }  
  
       }  
      }  
  
      // Function that manages authentication  
      function authenticate() {  
       //OAuth context  
       authContext = new AuthenticationContext(config);  
  
       // Check For & Handle Redirect From AAD After Login  
       var isCallback = authContext.isCallback(window.location.hash);  
       if (isCallback) {  
        authContext.handleWindowCallback();  
       }  
       var loginError = authContext.getLoginError();  
  
       if (isCallback && !loginError) {  
        window.location = authContext._getItem(authContext.CONSTANTS.STORAGE.LOGIN_REQUEST);  
       }  
       else {  
        errorMessage.textContent = loginError;  
       }  
       user = authContext.getCachedUser();  
  
      }  
  
      //function that logs in the user  
      function login() {  
       authContext.login();  
      }  
      //function that logs out the user  
      function logout() {  
       authContext.logOut();  
       accountsTable.style.display = "none";  
       accountsTableBody.innerHTML = "";  
      }  
  
    //function that initiates retrieval of accounts  
      function getAccounts() {  
  
       getAccountsButton.disabled = true;  
       var retrievingAccountsMessage = document.createElement("p");  
       retrievingAccountsMessage.textContent = "Retrieving 10 accounts from " + organizationURI + "/api/data/v9.1/accounts";  
       message.appendChild(retrievingAccountsMessage)  
  
       // Function to perform operation is passed as a parameter to the aquireToken method  
       authContext.acquireToken(organizationURI, retrieveAccounts)  
  
      }  
  
    //Function that actually retrieves the accounts  
      function retrieveAccounts(error, token) {  
       // Handle ADAL Errors.  
       if (error || !token) {  
        errorMessage.textContent = 'ADAL error occurred: ' + error;  
        return;  
       }  
  
       var req = new XMLHttpRequest()  
       req.open("GET", encodeURI(organizationURI + "/api/data/v9.1/accounts?$select=name,address1_city&$top=10"), true);  
       //Set Bearer token  
       req.setRequestHeader("Authorization", "Bearer " + token);  
       req.setRequestHeader("Accept", "application/json");  
       req.setRequestHeader("Content-Type", "application/json; charset=utf-8");  
       req.setRequestHeader("OData-MaxVersion", "4.0");  
       req.setRequestHeader("OData-Version", "4.0");  
       req.onreadystatechange = function () {  
        if (this.readyState == 4 /* complete */) {  
         req.onreadystatechange = null;  
         if (this.status == 200) {  
          var accounts = JSON.parse(this.response).value;  
          renderAccounts(accounts);  
         }  
         else {  
          var error = JSON.parse(this.response).error;  
          console.log(error.message);  
          errorMessage.textContent = error.message;  
         }  
        }  
       };  
       req.send();  
      }  
      //Function that writes account data to the accountsTable  
      function renderAccounts(accounts) {  
       accounts.forEach(function (account) {  
        var name = account.name;  
        var city = account.address1_city;  
        var nameCell = document.createElement("td");  
        nameCell.textContent = name;  
        var cityCell = document.createElement("td");  
        cityCell.textContent = city;  
        var row = document.createElement("tr");  
        row.appendChild(nameCell);  
        row.appendChild(cityCell);  
        accountsTableBody.appendChild(row);  
       });  
       accountsTable.style.display = "block";  
      }  
  
     </script>  
     <style>  
      body {  
       font-family: 'Segoe UI';  
      }  
  
      table {  
       border-collapse: collapse;  
      }  
  
      td, th {  
       border: 1px solid black;  
      }  
  
      #errorMessage {  
       color: red;  
      }  
  
      #message {  
       color: green;  
      }  
     </style>  
    </head>  
    <body>  
     <button id="login">Login</button>  
     <button id="logout" style="display:none;">Logout</button>  
     <button id="getAccounts" style="display:none;">Get Accounts</button>  
     <div id="errorMessage"></div>  
     <div id="message"></div>  
     <table id="accountsTable" style="display:none;">  
      <thead><tr><th>Name</th><th>City</th></tr></thead>  
      <tbody id="accountsTableBody"></tbody>  
     </table>  
    </body>  
    </html>  
  
    ```  
  
3.  Klicken Sie mit der rechten Maustaste auf die SimpleSPA.html-Datei und wählen Sie **Als Startseite festlegen**, um diese Seite als Startseite für das Projekt festzulegen.  
  
4.  In die Eigenschaften des Projekts wählen Sie **Web** und unter **Server** die Option **Projekt-URL**. Sie sollte ungefähr so aussehen: `http://localhost:62111/`. Beachten Sie die Portnummer, die generiert wird. Sie benötigen diese im nächsten Schritt.  
  
5.  Innerhalb der Seite SimpleSPA.html finden Sie die folgenden Konfigurationsvariablen und legen Sie sie nach Bedarf fest. Sie können `clientId` festlegen, nachdem Sie den folgenden folgenden Teil dieser exemplarischen Verfahren gelesen haben.  
  
    ```javascript  
    //Set these variables to match your environment  
    var organizationURI = "https://[organization name].crm.dynamics.com"; //The URL to connect to PowerApps Common Data Service  
    var tenant = "[xxx.onmicrosoft.com]"; //The name of the Azure AD organization you use  
    var clientId = "[client id]"; //The ClientId you got when you registered the application  
    var pageUrl = "http://localhost:[PORT #]/SimpleSPA.html"; //The URL of this page in your development environment when debugging.  
  
    ```  
  
## <a name="register-the-application"></a>Registrieren der Anwendung  
  
1.  [Melden Sie sich an](https://portal.azure.com) im Azure-Verwaltungsportal mithilfe eines Kontos mit Administratorberechtigungen. Sie müssen ein Konto im gleichen Office 365-Abonnement (Mandant) verwenden, in dem Sie auch die App registrieren möchten. Sie können auch über das Microsoft 365 Administratoren-Center auf das Azure-Porta zugreifen, indem Sie das Element **ADMIN** im linken Navigationsbereich erweitern und **Azure AD** auswählen.  
  
     Wenn Sie keinen Azure-Mandaten (Firma) haben oder wenn Sie einen haben, aber Ihr Office 365-Abonnement mit Common Data Service in Ihrem Azure-Abonnement nicht verfügbar ist, befolgen Sie die Anweisungen im Abschnitt [Azure Active Directory-Zugang für Ihre Entwicklerseite einrichten](https://docs.microsoft.com/office/developer-program/office-365-developer-program), um die beiden Konten zu verbinden.  
  
     Wenn Sie kein Konto haben, können Sie sich für eines anmelden, indem Sie eine Kreditkarte verwenden. Allerdings ist das Konto kostenlos für die Anwendungsregistrierung, und Ihre Kreditkarte wird nicht belastet, wenn Sie nur den Vorgehensweisen folgen, die in diesem Thema genannt werden, um mindestens eine App zu registrieren. Mehr Informationen: [Active Directory Preisgestaltung Details](http://azure.microsoft.com/pricing/details/active-directory/).  
  
2.  Klicken Sie auf **Azure Active Directory** in der linken Spalte der Seite. Möglicherweise müssen Sie in der linken Spalte scrollen, um das **Azure Active Directory**-Symbol und die Bezeichnung zu sehen.  
  
3.  Wählen Sie nun im sich öffnenden Fenster **Enterprise Applications** aus.

![Unternehmensanwendungen auswählen](media/register-spa-app-registration.PNG)

4.  Wählen Sie **Neue Anwendung** (oben auf der Seite) und dann unter **Eigene Anwendung hinzufügen** die Option **Anwendung, die Sie gerade entwickeln**.  

![Wählen Sie die Anwendung, die Sie entwickeln möchten.](media/register-spa-app-you-developing.PNG)
  
5.  Klicken Sie nun auf **Ok, bringen Sie mich zu App Registrierungen, um meine neue Anwendung zu registrieren**.

![Wählen Sie Ok, bringen Sie mich zu den App-Registrierungen.](media/register-spa-take-me-app-reg.PNG)

6.  Klicken Sie nun auf **Registrierung neuer Anwendungen** (oben auf der Seite).  

![Wählen Sie die Registrierung einer neuen Anwendung](media/register-spa-new-reg.PNG)
  
7.  Geben Sie die folgenden Informationen ein:  
  
  - **Name**<br />Der Name der Anwendung.

  - **Web-Anwendungstyp**<br />Wählen Sie **Web App/API**.

  - **Anmelde-URL**<br />Dies ist die URL, zu der Benutzer nach der Anmeldung umgeleitet werden. Für Debugzwecke in Visual Studio sollte sie `http://localhost:####/SimpleSPA.html` sein, wobei #### die Portnummer darstellt, die Sie in Schritt 4 der Vorgehensweise [Erstellen eines Webanwendungsprojektes](#bkmk_createwebapp) erhalten haben.  

![Details eingeben](media/register-spa-enter-details.PNG)
    
8. Klicken Sie dann am Ende der Seite auf **Erstellen**.

9.  Kopieren Sie auf der Registerkarte der neu registrierten Anwendung die **Anwendungs-ID**.  
  
    Legen Sie die `clientId`-Variablen auf der Seite SimpleSPA.html auf diesen Wert fest. Siehe Schritt 5 der Vorgehensweise. **Erstellen eines Webanwendungsprojekt**.  

10. Klicken Sie nun auf **Einstellungen** und wählen Sie dann **Erforderliche Berechtigungen**.

![Erforderliche Berechtigungen auswählen](media/register-spa-settings-permissions.PNG)

11. Klicken Sie auf **Hinzufügen** und wählen Sie dann **Eine API auswählen**. Wählen Sie nun **Dynamics CRM Online** und klicken Sie am Ende der Seite auf **Auswählen**.

![Wählen Sie Dynamics CRM Online unter Auswahl einer API.](media/register-spa-permission-dyncrm.PNG)

12. Wählen Sie nun auf der Registerkarte **Ausgewählte Berechtigungen** alle **delegierten Berechtigungen** aus und klicken Sie am Ende der Seite auf **Auswählen**.

![Alle delegierten Berechtigungen auswählen](media/register-spa-del-permissions.PNG)

13. Wählen Sie dann **Fertig**. Sie sehen eine Zeile für **Dynamics CRM Online** hinzugefügt.

![Neue Zeile für Dynamics CRM Online wurde hinzugefügt.](media/register-spa-row-dyncrm.PNG)

14. Schließen Sie nun die Registerkarte **Einstellungen**. Wählen Sie auf der Registerkarte der registrierten App die Option **Manifest**.

15. Klicken Sie auf **Bearbeiten** und suchen Sie die Linie: `"oauth2AllowImplicitFlow": false,` und ändern Sie `false` in `true` und klicken Sie dann auf **Speichern**, um die Datei zu speichern.

![Setzt oauth2AllowImplicitFlow in der Manifestdatei auf true.](media/register-spa-edit-manifest.PNG)

16. Für eine erfolgreiche Ausführung Ihrer Anwendung müssen Sie außerdem die Zustimmung des Administrators erteilen. Melden Sie sich dazu als Mandantenadministrator in Ihrem Azure Management Portal an und wählen Sie **Azure Active Directory**. Klicken Sie dann auf **Enterprise Applications** und wählen Sie aus der Liste der angezeigten Anwendungen die Anwendung aus, die Sie gerade erstellt haben.

![Erteilen Sie dem Administrator die Zustimmung zu Ihrer Anwendung.](media/simple-spa-admin-consent.PNG)

17. Wählen Sie nun wie oben gezeigt **Berechtigungen** aus und klicken Sie auf **Zustimmung des Administrators gewähren**`<your AAD Org name>`.

![Klicken Sie auf die Schaltfläche Einwilligung des Administrators gewähren.](media/simple-spa-admin-consent-button.PNG)

18. Sobald Sie auf diese Schaltfläche klicken, öffnet sich ein Anmeldefenster und fragt Sie, ob Sie Ihrer Anwendung die erforderlichen Berechtigungen erteilen möchten. Klicken Sie zum Fortfahren auf **Akzeptieren**.

![Klicken Sie auf Akzeptieren, um die angeforderten Berechtigungen zu erteilen.](media/simple-spa-admin-consent-click-accept.PNG)

19. Sobald dies erledigt ist, fahren Sie mit dem Debuggen der Anwendung fort.

## <a name="debugging-the-application"></a>Debuggen der Anwendung  
  
1.  Stellen Sie den Browser so ein, dass er Microsoft Edge oder Google Chrome verwendet.  
  
    > [!NOTE]
    > Internet Explorer funktioniert in diesem Fall nicht für das Debuggen.  
  
2.  Drücken Sie F5, um das Debuggen zu starten. Sie sollten das in [Ziel dieser exemplarischen Vorgehensweise](walkthrough-registering-configuring-simplespa-application-adal-js.md#bkmk_goal) beschriebene Verhalten erwarten.  
  
Wenn Sie nicht die erwarteten Ergebnisse erhalten, überprüfen Sie die Werte, die Sie bei der Registrierung der Anwendung und der Konfiguration des `SimpleSPA.html`-Codes eingestellt haben.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Client-Anwendungen](connect-cds.md)<br />
 [Tutorial: Registrieren Sie eine App bei Azure Active Directory](walkthrough-register-app-azure-active-directory.md) <br />
 [Erstellen von Webanwendungen mit Hilfe der Server zu Server(S2S)-Authentifizierung](build-web-applications-server-server-s2s-authentication.md)<br />
 [Verwenden von OAuth mit Cross-Origin Resource Sharing zum Verbinden einer Single Page-Anwendung mit Common Data Service](oauth-cross-origin-resource-sharing-connect-single-page-application.md)