---
title: 'Exemplarische Vorgehensweise: Registrierung und Konfiguration von SimpleSPA-Anwendung mit adal.js (Common Data Service für Apps) | Microsoft Docs'
description: Diese Vorgehensweise beschreibt den Prozess des Registrierens und Konfigurierens der grundlegenden Single-Page-Anwendung (SPA) für den Zugriff auf Daten in Dynamics 365 Customer Engagement mithilfe von adal.js und Cross-origin Resource Sharing (CORS).
keywords: ''
ms.date: 10/31/2018
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

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/walkthrough-registering-configuring-simplespa-application-adal-js -->

Diese exemplarische Vorgehensweise beschreibt den Prozess des Registrierens und Konfigurierens der grundlegendsten Single-Page-Anwendung (SPA) für den Zugriff auf Daten in Dynamics 365 Common Data Service für Apps mithilfe von adal.js und Cross-origin Resource Sharing (CORS). Weitere Informationen: [Verwenden von OAuth mit Cross-Origin Resource Sharing, um eine Single Page-Anwendung mit Dynamics 365 (online) zu verbinden](oauth-cross-origin-resource-sharing-connect-single-page-application.md)
  
## <a name="prerequisites"></a>Voraussetzungen  
  
- Dynamics 365  
  
-   Sie müssen über ein Dynamics 365 (online)-Systembenutzerkonto mit einer Administratorrolle für Office 365 verfügen.  
  
-   Ein Azure-Abonnement für die Anwendungsregistrierung. Eine Probefirma funktioniert auch.  
  
- Visual Studio 2015  
  
<a name="bkmk_goal"></a>

## <a name="goal-of-this-walkthrough"></a>Ziel dieser exemplarischen Vorgehensweise

Wenn Sie diese exemplarische Vorgehensweise abschließen, können Sie eine einfache SPA-Anwendung in Visual Studio ausführen, über die sich der Benutzer authentifizieren und Daten aus Dynamics 365 (online) abrufen kann. Diese Anwendung besteht aus einer einzelnen HTML-Seite.  

Wenn Sie die Anwendung debuggen, gibt es zunächst nur eine Schaltfläche **Anmelden**.  

Klicken Sie auf **Anmelden**. Sie werden zu Anmeldeseite umgeleitet und geben Ihre Anmeldedaten ein.  

Nachdem Sie Ihre Anmeldeinformationen eingegeben haben, werden sie wieder zur HTML-Seite umgeleitet. Dort finden Sie die Schaltflächen **Anmelden**, **Abmelden** und **Firmen abrufen**. Sie sehen außerdem eine Begrüßung mit Informationen zu Ihrem Benutzerkonto.  

Klicken Sie auf die Schaltfläche **Firmen abrufen**, um 10 Firmendatensätze Ihrer Dynamics 365-Organisation abzurufen. Die Schaltfläche **Firmen abrufen** ist wie im folgenden Screenshot dargestellt deaktiviert:  
  
![Die SimpleSPA-Seite](media/simple-spa.png "Die SimpleSPA-Seite")  

> [!NOTE]
>  Das erstmalige Laden von Daten aus Dynamics 365 kann langsam sein während die Vorgänge zur Unterstützung der Authentifizierung stattfinden. Nachfolgende Vorgänge sind jedoch deutlich schneller.  

Klicken Sie zuletzt auf die Schaltfläche **Abmelden**, um sich abzumelden.  

> [!NOTE]
>  Diese SPA-Anwendung ist nicht als Muster zum Entwickeln von SPA-Anwendungen vorgesehen. Sie dient nur zu Beschreibung des Vorgangs der Registrierung und Konfiguration der Anwendung.  
  
### <a name="create-a-web-application-project"></a>Erstellen eines Webanwendungsprojekts  
  
1.  Erstellen Sie mit Visual Studio 2015 ein neues **ASP.NET-Webanwendung**-Projekt und nutzen Sie die Vorlage **Leer**. Sie können das Projekt beliebig benennen.  
  
    Möglicherweise können Sie auch frühere Versionen von Visual Studio verwenden. Für diese Schritte wird jedoch Visual Studio 2015 verwendet.  
  
2.  Fügen Sie eine neue HTML-Seite namens SimpleSPA.html zum Projekt hinzu und fügen Sie den folgenden Code ein:  
  
    ```html  
    <!DOCTYPE html>  
    <html>  
    <head>  
     <title>Simple SPA</title>  
     <meta charset="utf-8" />  
     <script src="https://secure.aadcdn.microsoftonline-p.com/lib/1.0.0/js/adal.min.js"></script>  
     <script type="text/javascript">  
      "use strict";  
  
      //Set these variables to match your environment  
      var organizationURI = "https:// [organization name].crm.dynamics.com"; //The URL to connect to CRM (online)  
      var tenant = "[xxx.onmicrosoft.com]"; //The name of the Azure AD organization you use  
      var clientId = "[client id]"; //The ClientId you got when you registered the application  
      var pageUrl = "http://localhost: [PORT #]/SimpleSPA.html"; //The URL of this page in your development environment when debugging.  
  
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
       cacheLocation: 'localStorage', // enable this for IE, as sessionStorage does not work for localhost.  
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
       retrievingAccountsMessage.textContent = "Retrieving 10 accounts from " + organizationURI + "/api/data/v8.0/accounts";  
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
       req.open("GET", encodeURI(organizationURI + "/api/data/v8.0/accounts?$select=name,address1_city&$top=10"), true);  
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
  
3.  Legen Sie diese Seite als Startseite für das Projekt fest  
  
4.  In die Eigenschaften des Projekts wählen Sie **Web** und unter **Server** die Option **Projekt-URL**. Sie sollte ungefähr so aussehen: `http://localhost:46575/`. Beachten Sie die Portnummer, die generiert wird. Sie benötigen diese im nächsten Schritt.  
  
5.  Innerhalb der Seite SimpleSPA.html finden Sie die folgenden Konfigurationsvariablen und legen Sie sie nach Bedarf fest. Sie können `clientId` festlegen, nachdem Sie den folgenden folgenden Teil dieser exemplarischen Verfahren gelesen haben.  
  
    ```javascript  
    //Set these variables to match your environment  
    var organizationURI = "https://[organization name].crm.dynamics.com"; //The URL to connect to CRM (online)  
    var tenant = "[xxx.onmicrosoft.com]"; //The name of the Azure AD organization you use  
    var clientId = "[client id]"; //The ClientId you got when you registered the application  
    var pageUrl = "http://localhost:[PORT #]/SimpleSPA.html"; //The URL of this page in your development environment when debugging.  
  
    ```  
  
### <a name="register-the-application"></a>Registrieren der Anwendung  
  
1.  [Melden Sie sich an](http://manage.windowsazure.com) im Azure-Verwaltungsportal mithilfe eines Kontos mit Administratorberechtigungen. Sie müssen ein Konto im gleichen Office 365-Abonnement (Mandant) verwenden, in dem Sie auch die App registrieren möchten. Sie können auch auf das Azure-Portal über das Office 365 Administratoren-Center zugreifen, indem Sie das Element **ADMIN** im linken Navigationsbereich erweitern und **Azure AD** auswählen.  
  
     Falls Sie keinen Azure-Mandanten (Konto) haben oder darüber zwar verfügen, aber Ihr Office 365-Abonnement mit Dynamics 365 (online) nicht in Ihrem Azure-Abonnement verfügbar ist, folgen Sie den Anweisungen im Thema [Einrichten des Azure Active Directory-Zugriffs für die Entwickler-Website](https://docs.microsoft.com/en-us/office/developer-program/office-365-developer-program), um die beiden Konten zuzuordnen.  
  
     Wenn Sie kein Konto haben, können Sie sich für eines anmelden, indem Sie eine Kreditkarte verwenden. Allerdings ist das Konto kostenlos für die Anwendungsregistrierung, und Ihre Kreditkarte wird nicht belastet, wenn Sie nur den Vorgehensweisen folgen, die in diesem Thema genannt werden, um mindestens eine App zu registrieren. Weitere Informationen: [Active Directory-Preisberechnungsdetails](http://azure.microsoft.com/pricing/details/active-directory/)  
  
2.  Klicken Sie auf **Active Directory** in der linken Spalte der Seite. Möglicherweise müssen Sie in der linken Spalte einen Bildlauf durchführen, um das Symbol und die Beschriftung von **Active Directory** zu sehen.  
  
3.  Klicken Sie auf das gewünschte Mandantenverzeichnis in der Verzeichnisliste.  
  
    ![Liste verfügbarer Active Directory-Einträge](media/azure-active-directory.PNG "Liste verfügbarer Active Directory-Einträge")  
  
    Wenn Ihr Azure-Mandantenverzeichnis in der Verzeichnisliste nicht angezeigt wird, klicken Sie auf **Hinzufügen**, und wählen Sie dann im Dialogfeld **Vorhandenes Verzeichnis verwenden** aus. Folgen Sie den bereitgestellten Eingabeaufforderungen und Anweisungen, und kehren Sie dann zu Schritt 1 zurück.  
  
4.  Wenn das Zielverzeichnis ausgewählt ist, klicken Sie auf **Anwendungen** (am oberen Seitenrand), und klicken Sie dann auf **Hinzufügen**.  
  
5.  Klicken Sie im Dialogfeld **Wie möchten Sie vorgehen?** auf **Hinzufügen einer Anwendung, die meine Organisation entwickelt**.  
  
6.  Wenn Sie zur dazu aufgefordert werden, geben Sie einen Namen für die Anwendung ein (z. B. "SimpleSPA"), wählen Sie den Typ aus: **Webanwendung und/oder Web-API**, und wählen Sie dann zum Fortfahren den rechten Pfeil. Klicken Sie auf das Fragezeichen **?**, um weitere Informationen über die entsprechenden Werte für jedes Eingabefeld zu erhalten.  
  
7.  Geben Sie die folgenden Informationen ein:  
  
    **Anmelde-URL**  
    Dies ist die URL, zu der Benutzer nach der Anmeldung umgeleitet werden. Für Debugzwecke in Visual Studio sollte sie `http://localhost:####/SimpleSPA.html` sein, wobei #### die Portnummer darstellt, die Sie in Schritt 4 der Vorgehensweise **Erstellen eines Webanwendungsprojektes** erhalten haben.  
  
    **APP ID URI**  
    Hierbei muss es sich um einen eindeutigen Bezeichner für die Anwendung handeln. Verwenden Sie `https://XXXX.onmicrosoft.com/SimpleSPA`, wobei XXXX der Active Directory-Mandant ist.  
  
8.  Mit der Registerkarte die neu registrierten App ausgewählt klicken Sie auf **Konfigurieren**, suchen Sie **Client-ID** und kopieren Sie die ID.  
  
    Legen Sie die `clientId`-Variablen auf der Seite SimpleSPA.html auf diesen Wert fest. Siehe Schritt 5 der Vorgehensweise. **Erstellen eines Webanwendungsprojekt**.  
  
9. Führen Sie einen Bildlauf nach unten durch und klicken Sie auf **Anwendung hinzufügen**. Wählen Sie im Dialogfeld **Dynamics 365 Online** aus und Schließen Sie das Dialogfeld.  
  
10. Die "Berechtigungen für andere Anwendungen" finden Sie eine Zeile für **Dynamics 365 Online** und **Delegierte Berechtigungen: 0**. Wählen Sie diese und fügen Sie **Zugriff auf Dynamics 365 (online) als Organisationsbenutzer** hinzu.  
  
11. Speichern der Anwendungsregistrierung  
  
12. Wählen Sie unten **Manifest verwalten** und **Manifest herunterladen** aus.  
  
13. Öffnen Sie die JSON-Datei, die Sie heruntergeladen und suchen Sie die Zeile `"oauth2AllowImplicitFlow": false,` und ändern Sie `false` zu `true` und speichern Sie die Datei.  
  
14. Wechseln Sie wieder zu **Manifest verwalten**. Wählen Sie **Upload-Manifest** aus und laden Sie die JSON-Datei hoch, die Sie gerade gespeichert haben.  
  
### <a name="debugging-the-application"></a>Debuggen der Anwendung  
  
1.  Legen Sie als Browser die Verwendung von Microsoft Edge, Google Chrome oder Mozilla Firefox fest.  
  
    > [!NOTE]
    > Internet Explorer funktioniert in diesem Fall nicht für das Debuggen.  
  
2.  Drücken Sie F5, um das Debuggen zu starten. Sie sollten das in [Ziel dieser exemplarischen Vorgehensweise](walkthrough-registering-configuring-simplespa-application-adal-js.md#bkmk_goal) beschriebene Verhalten erwarten.  
  
     Wenn Sie nicht die erwarteten Ergebnisse erhalten, prüfen Sie die Werte, die Sie bei der Registrierung der Anwendung und der Konfiguration des SimpleSPA.html-Codes festgelegt haben.  
  
### <a name="see-also"></a>Siehe auch  
 [Verwenden von OAuth mit Cross-Origin Resource Sharing, um eine Single Page-Anwendung mit Dynamics 365 (online) zu verbinden](oauth-cross-origin-resource-sharing-connect-single-page-application.md)