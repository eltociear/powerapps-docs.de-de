---
title: Verwenden der Einzel-Mandanten-Server-zu-Server-Authentifizierung (Common Data Service) | MicrosoftDocs
description: 'Beschreibt den Zugriff auf D365-Daten aus einer Anwendung oder einem Dienst heraus, ohne explizite Benutzerauthentifizierung.'
ms.custom: ''
ms.date: 2/21/2019
ms.reviewer: pehecke
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
# <a name="use-single-tenant-server-to-server-authentication"></a>Verwenden der Einzel-Mandanten-Server-zu-Server-Authentifizierung

Die Einzel-Mandanten-Server-zu-Server-Authentifizierung wird normalerweise bei Unternehmensorganisationen verwendet, die mehrere Common Data Service-Umgebungen haben und die Active Directory Federation Services (AD FS) für die Authentifizierung verwenden. Allerdings kann es auch von Umgebungen angewendet werden, wenn die Anwendung nicht an andere Umgebungen verteilt wird.  
  
 Eine Firma kann eine Webanwendung oder einen Service erstellen, um alle Common Data Service-Umgebungen zu verbinden, die mit einem einzelnen Azure Active Directory(AD)-Mandanten verknüpft sind.
  
## <a name="differences-from-multi-tenant-scenario"></a>Unterschiede von mehrinstanzenfähigen Szenarien  
 Eine Webanwendung oder einen Service für eine Einzelmandanten-Server-zu-Server-Authentifizierung zu erstellen ist gleich wie jene, die für eine mehrinstanzenfähige Organisation verwendet wird, aber es gibt einige wichtige Unterschiede.  
  
-   Da sich alle Organisationen im gleichen Mandanten befinden, muss ein Mandantenadministrator keine Zustimmung für jede Organisation gewähren. Die Anwendung ist einfach einmal auf dem Mandanten registriert.
  
-   Wenn Sie es bevorzugen, haben die Möglichkeit, anstelle von Schlüsseln Zertifikate zu verwenden. 

Im [Siehe auch](#bkmk_seealso)-Abschnitt am Ende dieses Artikels finden Sie Links zu Informationen zum Aktualisieren einer Einzelinstanzanwendung zur Mehrinstanzenfähigkeit.  

<a name="bkmk_Requirements"></a>
## <a name="requirements"></a>Anforderungen  

 Wenn Sie eine einzelinstanzenfähige Anwendung erstellen und testen, die eine Server-zu-Server (S2S) Authentifizierung verwendet, müssen die folgenden Aktionen ausgeführt werden:  
  
- Ein Azure AD-Mandant, der verwendet wird, wenn die bereitgestellte Beispielanwendung registriert wird.
- Ein Common Data Service-Abonnement, das mit dem Azure AD-Mandanten verknüpft ist.
- Administratorrechte im Azure AD-Mandanten und der D365-Organisation.

<a name="bkmk_registration"></a>
## <a name="azure-application-registration"></a>Azure-Anwendungsregistrierung
Gehen Sie zum Erstellen einer Anwendungsregistrierung in Azure AD folgendermaßen vor.

1. Navigieren Sie zu https://admin.microsoft.com, und melden Sie sich an, oder wählen Sie auf der Webseite Ihrer D365-Organisation das Anwendungsstartprogramm in der oberen linker Ecke aus.
2. Wählen Sie **Administrator** > **Admin Center** > **Azure Active Directory** aus.
3. Wählen Sie im linken Bereich **Azure Active Directory** > **App-Registrierungen (Vorschau)** aus.
4. Wählen Sie **+ Neue Registrierung** aus.
5. Geben Sie im Formular **Eine Anwendung registrieren** einen Namen für Ihre App ein, wählen Sie **Nur Firmen in diesem organisatorischen Verzeichnis** aus, und wählen Sie **Registrieren** aus. Ein Umleitungs-URI wird für diese exemplarische Vorgehensweise und den zur Verfügung gestellten Beispielcode nicht benötigt.<br /> ![Registrieren eines Anmeldeformulars](media/S2S-app-registration-started.PNG)
6. Wählen Sie auf der Seite **Übersicht** die Option **API-Berechtigungen** aus. <br >![App-Registrierungsberechtigungen](media/S2S-app-registration-completed.PNG)
7. Wählen Sie **+ Eine Berechtigung hinzufügen** aus
8. Wählen Sie in der Registerkarte **Microsoft-APIs** die Option **Dynamics CRM** aus.
9. Wählen Sie im Formular **API-Berechtigung anfordern** die Option **Delegierte Berechtigungen** aus, prüfen Sie die **user_impersonation** und wählen Sie **Berechtigungen hinzufügen** aus. <br />![Festlegen von API-Berechtigungen](media/S2S-api-permission-started.PNG)
10. Wählen Sie auf der Seite **API-Berechtigungen** unter **Zustimmung erteilen** die Option **Administratorzustimmung für "Org-Name" erteilen** aus, und wenn Sie dazu aufgefordert werden, wählen Sie **Ja** aus. <br />![Erteilen von API-Berechtigungen](media/S2S-api-permission-completed.PNG)
11. Wählen Sie im Navigationsbereich **Übersicht** aus, zeichnen Sie die Werte für **Anzeigename**, **Anwendungs-ID** und **Verzeichnis-ID** der App-Registrierung auf. Sie stellen diese später im Codebeispiel bereit.
12. Wählen Sie im Navigationsbereich auf **Zertifikate und geheime Schlüssel**
13. Wählen Sie unter **Geheime Clientschlüssel** die Option **+ Neuer geheimer Clientschlüssel** aus, um einen geheimen Schlüssel zu erstellen
14. Geben Sie im Formular eine Beschreibung ein und wählen Sie **Hinzufügen** aus. Zeichnen Sie die geheime Zeichenfolge auf. Es ist nicht möglich, den geheimen Schlüssel erneut anzuzeigen, nachdem Sie den aktuellen Bildschirm verlassen haben.

<a name="bkmk_appuser"></a>
## <a name="application-user-creation"></a>Erstellung eines Anwendungsbenutzers
Um einen nicht lizenzierten "Anwendungsbenutzer" in Ihrer Dynamics 365-Organisation zu erstellen, führen Sie diese Schritte aus. Dieser Anwendungsbenutzer erhält Zugriff auf Organisationsdaten im Namen des Endbenutzers, der Ihre Anwendung verwendet.

1. Navigieren Sie zum Azure Active Directory-Administratorcenter.
2. Wählen Sie im linken Navigationsbereich **Benutzer** aus
3. Wählen Sie **+ Neuer Benutzer** aus
4. Geben Sie im Formular **Benutzer** einen Namen und einen Benutzernamen für den neuen Benutzer ein, und wählen Sie **Erstellen** aus. Stellen Sie sicher, dass der Benutzername die URL der Organisationsdomäne Ihres D365-Mandanten enthält, (d. h. someuser@myorg.onmicrosoft.com). Sie können Azure AD jetzt verlassen.
5. Navigieren Sie zu Ihrer D365-Organisation
6. Gehen Sie zu **Einstellungen** > **Sicherheit** > **Benutzer**
7. Wählen Sie im Ansichtsfilter **Anwendungsbenutzer** aus
8. Wählen Sie **+ Neu** aus.
9. Geben Sie im Formular **Neuer Benutzer** die erforderlichen Informationen ein. Diese Werte müssen den Werten für den neuen Benutzer entsprechen, den Sie im Azure-Mandanten erstellt haben. <br />![Neuer App-Benutzer](media/S2S-new-appuser.PNG)
10. Wenn alles richtig verläuft, werden die Felder **URI der Anwendungs-ID** und **Azure AD-Objekt-ID** automatisch mit ihren richtigen Werten befüllt, wenn Sie **SPEICHERN** auswählen.
11. Bevor Sie das Benutzerformular beenden, wählen Sie **ROLLEN VERWALTEN** aus und weisen diesem Anwendungsbenutzer eine Sicherheitsrolle zu, damit der Anwendungsbenutzer auf die gewünschten Organisationsdaten zugreifen kann.

> [!IMPORTANT]
> Wenn Sie eine praxisorientierte Anwendung mithilfe S2S entwickeln, sollten Sie eine benutzerdefinierte Sicherheitsrolle verwenden, die in einer Lösung gespeichert und zusammen mit Ihrer Anwendung verteilt werden kann.

<a name="bkmk_coding"></a>
## <a name="application-coding-and-execution"></a>Anwendungscodierung und -ausführung

Folgen Sie diesen Schritten, um die Beispielanwendung herunterzuladen, zu erstellen und auszuführen. In diesem Beispiel wird WebAPI aufgerufen, um eine Liste der ersten 3 Firmen (nach Name) in der Organisation zurückzugeben.

1. Laden Sie das Visual Studio 2017 SingleTenantS2S-[Beispiel](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/webapi/C%23/SingleTenantS2S) herunter.
2. Aktualisieren Sie die App.config-Datei mit der App-Registrierung und den Serverschlüsselwerten.
3. Erstellen Sie die Anwendung und führen Sie sie aus.

### <a name="expected-results"></a>Erwartete Ergebnisse
Eine OData-Antwort, die die Namen die ersten 3 Firmen in Ihrer D365-Organisation aufführt.

### <a name="example-console-output"></a>Beispielskonsolenausgabe
Unten veranschaulicht ein Beispiel die Konsolenausgabe, die von einer D365-Organisation abgerufen wird, die nur zwei Firmen mit den Namen "Testfirma 1" und "Testfirma 2" hat.

```json
{
"@odata.context":"https://crmue2.api.crm.dynamics.com/api/data/v9.1/$metadata#accounts(name)",
"@Microsoft.Dynamics.CRM.totalrecordcount":-1,
"@Microsoft.Dynamics.CRM.totalrecordcountlimitexceeded":false,

"value":[
{"@odata.etag":"W/\"4648334\"","name":"Test Account 1","accountid":"28630624-cac9-e811-a964-000d3a3ac063"},
{"@odata.etag":"W/\"4648337\"","name":"Test Account 2","accountid":"543fd72a-cac9-e811-a964-000d3a3ac063"}]
}
```

<a name="bkmk_seealso"></a>

### <a name="see-also"></a>Siehe auch

[Verwenden Sie mehrinstanzenfähige Server-zu-Server-Authentifizierung](use-multi-tenant-server-server-authentication.md)   
[Erstellen von Webanwendungen mit Server-to-Server-Authentifizierung (S2S)](build-web-applications-server-server-s2s-authentication.md)  
[Anleitung: Einen beliebigen Azure Active Directory-Benutzer mit dem mehrinstanzenfähigen Anwendungsmuster anmelden](https://docs.microsoft.com/azure/active-directory/develop/howto-convert-app-to-be-multi-tenant)
