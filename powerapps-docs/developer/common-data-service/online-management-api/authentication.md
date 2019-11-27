---
title: Authentifizieren zur Verwendung der Online-Verwaltungs-API für Common Data Service | Microsoft-Dokumentation
description: Enthält Informationen zum Authentifizieren bei der Online-Verwaltungs-API, um umgebungsbezogene Vorgänge auszuführen.
ms.date: 11/27/2017
ms.service: crm-online
ms.topic: conceptual
ms.assetid: c292c148-01f0-41f6-a2fe-7ed05a01a733
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
- developer
search.app:
- D365CE
ms.openlocfilehash: 7243f2fccc8356ecac5eedba2b740bc39df1913a
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2752938"
---
# <a name="authenticate-to-use-the-online-management-api"></a>Authentifizieren Sie sich, um die Online Management API zu verwenden

Online Management API unterstützt OAuths 2.0-Protokoll für die Authentifizierung. Verwenden Sie [Azure Active Directory (AAD)](https://docs.microsoft.com/azure/active-directory/active-directory-whatis) für die Authentifitzieung, indem Sie ein gültiges OAuth 2.0-Zugriffstoken erhalten, und übergeben Sie es mithilfe des **Authorisierung**-Headers in Ihren Anforderungen an Online Management API.

Die empfohlene Authentifizierungs-API für die Verwendung mit der [Azure Active Directory Authentifizierungs-Bibliothek (ADAL)](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries), die für eine Vielzahl von Plattformen und Programmiersprachen verfügbar ist. 

## <a name="how-to-authenticate"></a>Wie authentifizieren Sie sich?

Hier folgen die wichtigsten Schritte zum Authetifizieren beim Online Management API-Service. 

1. Registrieren Sie eine App mit Azure Active Directory, um die Werte *clientId* und *redirectUrl* für die App zu erhalten. Weitere Informationen hierzu finden Sie im Abschnitt "App-Registrierung für OAuth-Authentifizierung" in [Exemplarische Vorgehensweise: Registrieren einer App mit Azure Active Directory](/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory).

1. Geben Sie die Werte an, die von Schritt# 1 in der Authentifizierung stammen [Hilfecode](sample-authentication-helper.md):

    ```csharp
    // TODO: Substitute your app registration values here.
    // These values are obtained on registering your application with the 
    // Azure Active Directory.
    private static string _clientId = "<GUID>";    //e.g. "e5cf0024-a66a-4f16-85ce-99ba97a24bb2"
    private static string _redirectUrl = "<Url>";  //e.g. "app://s7cf7712-b773-4f16-92b3-34cs97a25cc7"
    ```

1. Erkunden Sie Authentifizierungsinformationen für Online Management API auf Basis der Service-URL. Für die Nordamerika-Region lautet die Service-URL: **https://admin.services.crm.dynamics.com**. Die regionspezifische URL finden Sie unter [Service URL](get-started-online-management-api.md#service-url)<br /> Verwenden Sie Azure Active Directory Forderungsformat, um die Authentifizierunginformationen auf Basis der Service-URL der API zu ermitteln.<br />Wir bestimmen außerdem die Ressource für die Online Management API (abweichend von der Service-URL), die im nächsten Schritt verwendet wird, um Zugriffstoken abzurufen.

    ```csharp
    public static async Task<string> DiscoverAuthority(string _serviceUrl)
    {
        try
        {
            AuthenticationParameters ap = await AuthenticationParameters.CreateFromResourceUrlAsync(
                    new Uri(_serviceUrl + "/api/aad/challenge"));
            _resource = ap.Resource;
            return ap.Authority;
        }
        catch (HttpRequestException e)
        {
            throw new Exception("An HTTP request exception occurred during authority discovery.", e);
        }
        catch (Exception e)
        {
            throw e;
        }
    }
    ```
1. Verwenden Sie die Ressource, die Sie im vorherigen Schritt ermittelt haben, zusammen mit der Client-ID und der Umleitungs-URL Ihrer Client-App, um ein Zugriffstoken abzurufen. Beachten Sie, dass die Ressource verwenden müssen, und nicht die Service URL, um Zugriffstoken zzu erhalten oder zu aktualisieren.

    ```csharp
    public AuthenticationResult AcquireToken()
    {
        return _authContext.AcquireToken(_resource, _clientId, new Uri(_redirectUrl),
                PromptBehavior.Always);
    }        
    ```

1. Sobald Sie das Zugriffstoken haben, müssen Sie die Kopfzeile **Authorisierung** der Nachrichtenanforderung auf den Zugriffstokenwert festlegen, und den Tokentyp als **Träger**. Legen Sie außerdem den Header **Sprache-akzeptieren** auf die bevorzugte Sprache für die Antwort fest. Bei der `SendAsync`-Möglichkeit der Authentifizierung werden diese Header-Werte für alle Nachrichtenanforderungen festgelegt:

    ```csharp
    protected override Task<HttpResponseMessage> SendAsync(
                HttpRequestMessage request, System.Threading.CancellationToken cancellationToken)
    {
        // It is a best practice to refresh the access token before every message request is sent. Doing so
        // avoids having to check the expiration date/time of the token. This operation is quick.
        request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", _auth.AcquireToken().AccessToken);
        
        // Set the "Accept-Language" header
        request.Headers.Add("Accept-Language", "en-US");

        return base.SendAsync(request, cancellationToken);
    }
    ```

Sie können alle dazu festlegen, Nachrichten anhand der Online Management API auszuführen. Einen Beispielcode, der zeigt, wie alle Common Data Service-Umgebungen in Ihrem Office 365-Mandanten abgerufen werden, finden Sie unter [Schnellstart-Beispiel: Umgebungen in Ihrem Mandanten abrufen](sample-quick-start.md).


### <a name="related-topics"></a>Verwandte Themen  

[Beispiel: Authentifizierungshilfe für die Online Management API](sample-authentication-helper.md)

[Erste Schritte mitOnline Management API](get-started-online-management-api.md)

[Online Management API-Referenz](/rest/api/admin.services.crm.dynamics.com)
