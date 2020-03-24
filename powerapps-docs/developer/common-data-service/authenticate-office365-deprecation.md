---
title: Verwendung der Office365-Authentifizierung mit dem Sicherheitsprotokoll WS-Trust (Common Data Service) | Microsoft Docs
description: Beschreibt die Verwerfung des WS-Trust-Sicherheitsprotokolls und die in Anwendungen erforderlichen Änderungen des Authentifizierungscodes.
ms.custom: ''
ms.date: 02/05/2020
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: phecke
ms.author: pehecke
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 734d64fe24e7fbaec56109987fc8f0bb9163f5c8
ms.sourcegitcommit: 4f2e9e8f9bd3204ca9eee9e2a46f797c957c55ec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/06/2020
ms.locfileid: "3029794"
---
# <a name="use-of-office365-authentication-with-the-ws-trust-security-protocol"></a>Verwendung der Office365-Authentifizierung mit dem WS-Trust-Sicherheitsprotokoll

Die Verwendung des WS-Trust-Authentifizierungs-Sicherheitsprotokolls bei der Verbindung mit Common Data Service wird nicht mehr empfohlen und wurde veraltet; siehe [Ankündigung](/power-platform/important-changes-coming#deprecation-of-office365-authentication-type-and-organizationserviceproxy-class-for-connecting-to-common-data-service). 

Diese Änderung wirkt sich auf benutzerdefinierte Client-Anwendungen aus, die die „Office365“-Authentifizierung und die Klassen [Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy](/dotnet/api/microsoft.xrm.sdk.client.organizationserviceproxy) oder [Microsoft.Xrm.Tooling.Connector.CrmServiceClient](/dotnet/api/microsoft.xrm.tooling.connector.crmserviceclient) verwenden. Wenn Ihre Anwendungen diese Art von Authentifizierungsprotokoll und API verwenden, lesen Sie weiter unten, um mehr über die empfohlenen Änderungen an der Authentifizierung zu erfahren, die am Code Ihrer Anwendung vorgenommen werden sollten.

## <a name="how-do-i-know-if-my-code-or-application-is-using-ws-trust"></a>Woher weiß ich, ob mein Code oder meine Anwendung WS-Trust verwendet?

Erstens und am wichtigsten ist, dass diese Änderung **nur** Auswirkungen auf Client-Anwendungen hat, die eine Verbindung zu Common Data Service herstellen. Sie hat keine Auswirkungen auf benutzerdefinierte Plug-Ins, Workflow-Aktivitäten oder lokale/IFD-Dienstverbindungen.

- Wenn Ihr Code für die Authentifizierung mit Common Data Service oder einer Anwendung Benutzerkonto- und Passwort-Anmeldeinformationen verwendet, verwenden Sie wahrscheinlich das Sicherheitsprotokoll WS-Trust. Einige Beispiele werden unten gezeigt, wobei diese Liste nicht vollständig ist.

  - Bei Verwendung der Klasse [CrmServiceClient](/dotnet/api/microsoft.xrm.tooling.connector.crmserviceclient) mit einer Verbindungszeichenfolge:

    `connectionString="AuthType=Office365; Username=jsmith\@contoso.onmicrosoft.com;Password=passcode;Url=https://contoso.crm.dynamics.com"`

  - Bei Verwendung von [OrganizationServiceProxy](/dotnet/api/microsoft.xrm.sdk.client.organizationserviceproxy) Klassenkonstruktoren:


```csharp
using (OrganizationServiceProxy organizationServiceProxy =
    new OrganizationServiceProxy(serviceManagement, clientCredentials)
{ ... }
```

- Wenn Sie die Klasse `OrganizationServiceProxy` überhaupt in Ihrem Code verwenden, verwenden Sie WS-Trust.

- Wenn Sie [CrmServiceClient](/dotnet/api/microsoft.xrm.tooling.connector.crmserviceclient) verwenden, verwenden Sie `OrganizationServiceProxy` in Ihrem Code verwenden Sie WS-Trust.

## <a name="what-should-i-do-to-fix-my-application-code-if-affected"></a>Was sollte ich tun, um meinen Anwendungscode zu reparieren, falls er betroffen ist?

Es gibt sehr einfache Möglichkeiten, den Code Ihrer Anwendung so zu ändern, dass die empfohlene Verbindungsschnittstelle für die Authentifizierung mit Common Data Service verwendet wird.

- Wenn Ihr Code eine [Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy](/dotnet/api/microsoft.xrm.sdk.client.organizationserviceproxy) Instanz verwendet:

  Wenn Sie die `OrganizationServiceProxy` Instanz an verschiedene Methoden weitergeben oder die Instanz von einer Funktion zurückgeben, ersetzen Sie alle Vorkommen vom Typ `OrganizationServiceProxy` durch die Schnittstelle [IOrganizationService](/dotnet/api/microsoft.xrm.sdk.iorganizationservice?view=dynamics-general-ce-9). Diese Schnittstelle stellt alle Kernmethoden zur Verfügung, die zur Kommunikation mit Common Data Service verwendet werden.

  Wenn Sie den Konstruktor aufrufen, wird empfohlen, das Paket NuGet [Microsoft.CrmSdk.XrmTooling.CoreAssembly](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.CoreAssembly/) zu Ihrem Projekt hinzuzufügen und alle Verwendungen von `OrganizationServiceProxy` Klassenkonstruktoren durch [CrmServiceClient](/dotnet/api/microsoft.xrm.tooling.connector.crmserviceclient) Klassenkonstruktoren zu ersetzen. Sie müssen hier jedoch der Einfachheit halber Ihr Codierungsmuster ändern, da `CrmServiceClient` neben komplexen Konstruktoren und der Möglichkeit, externe Authentifizierungs-Handler bereitzustellen, auch Verbindungszeichenketten unterstützt. `CrmServiceClient` implementiert `IOrganizationService`, daher wird Ihr neuer Authentifizierungscode auf den Rest Ihres Anwendungscodes portierbar sein. Beispiele für die Verwendung von `CrmServiceClient` finden Sie im [PowerApps-Beispiele](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23)-Repository.

- Wenn Ihr Code [CrmServiceClient](/dotnet/api/microsoft.xrm.tooling.connector.crmserviceclient) mit der Authentifizierungsart „Office365“ verwendet:

    Ein Beispiel dafür ist eine Verbindungszeichenfolge, die wie folgt aussieht:

    `connectionString = "AuthType=Office365;Username=jsmith@contoso.onmicrosoft.com;Password=passcode;Url=https://contoso.crm.dynamics.com"`

    In ähnlicher Weise könnten Sie auch einen Konstruktor `CrmServiceClient` verwenden und `AuthType.Office365` übergeben.

    Sie haben zwei Möglichkeiten, damit umzugehen.<p/>

    - Wechseln Sie zur Verwendung einer OAuth-basierten Verbindungszeichenfolge. Eine solche Verbindungszeichenfolge sieht wie folgt aus:

        `connectionString = "AuthType=OAuth;Username=jsmith@contoso.onmicrosoft.com;
    Password=passcode;Url=https://contosotest.crm.dynamics.com;AppId=51f81489-12ee-4a9e-aaae-a2591f45987d;
    RedirectUri=app://58145B91-0C36-4500-8554-080854F2AC97;LoginPrompt=Auto"`

        Dies ist der schnellste Weg, den Code zu aktualisieren. Beachten Sie, dass LoginPrompt auf „nie“ gesetzt werden kann, um die Art und Weise zu simulieren, wie das Office 365-Verhalten funktioniert.

        Die oben angegebenen AppId und RedirectUri sind Beispiele für funktionierende Anwendungsregistrierungswerte. Diese Werte funktionieren überall dort, wo unsere Online-Dienste eingesetzt werden. Sie werden hier jedoch als Beispiele bereitgestellt, und Sie werden ermutigt, Ihre eigene Anwendungsregistrierung in Azure Active Directory (AAD) für Anwendungen zu erstellen, die in Ihrem Mandanten laufen.<p/>

    - Wenn wir sie ankündigen, aktualisieren Sie auf das neueste Paket [Microsoft.CrmSdk.XrmTooling.CoreAssembly](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.CoreAssembly/) NuGet, das die automatische Umleitung unterstützt. Diese Bibliothek leitet eine Authentifizierungsart von Office365 nach OAuth um und verwendet automatisch die Beispiel-URI AppId und Redirect. Diese Funktionalität ist für die Version 9.2.x des Microsoft.CrmSdk.XrmTooling.CoreAssembly-Pakets geplant.

- Wenn Sie auf den [CrmServiceClient](/dotnet/api/microsoft.xrm.tooling.connector.crmserviceclient) zugreifen.`OrganizationServiceProxy` Eigenschaft:

     Entfernen Sie jegliche Verwendung dieser Eigenschaft in Ihrem Code. `CrmServiceClient` implementiert `IOrganizationService` und stellt alles dar, was für den Service-Proxy der Organisation einstellbar ist.

> [!IMPORTANT]
> Was die Möglichkeit betrifft, sich nicht mit Benutzer-ID/Passwort anzumelden, selbst wenn OAuth verwendet wird: Wenn Ihr Mandant und Benutzer in Azure Active Directory für die Zugangsberechtigung und/oder Multi-Faktor-Authentifizierung konfiguriert ist, können Sie Benutzer-ID/Passwort-Ströme überhaupt nicht in einer nicht-interaktiven Form verwenden. Für diese Situationen müssen Sie einen Service-Hauptbenutzer verwenden, um sich mit Common Data Service zu authentifizieren.<p/>
Dazu müssen Sie zunächst den Anwendungsbenutzer (Service Principal) mit Azure Active Directory registrieren. Wie Sie dies tun können, erfahren Sie [hier](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal). Während der Registrierung der Anwendung müssen Sie diesen Benutzer in Common Data Service anlegen und Berechtigungen erteilen. Diese Berechtigungen können entweder direkt oder indirekt erteilt werden, indem der Benutzer der Anwendung einem Team hinzugefügt wird, das die Berechtigungen in Common Data Service erhalten hat. Weitere Informationen darüber, wie Sie einen Benutzer der Anwendung für die Authentifizierung mit Common Data Service einrichten können, finden Sie [hier](/powerapps/developer/common-data-service/use-single-tenant-server-server-authentication).

## <a name="need-help"></a>Benötigen Sie Hilfe?

Wir werden die Power Apps ALM- und ProDev-Community-[Foren](https://powerusers.microsoft.com/t5/Power-Apps-Component-Framework/bd-p/pa_component_framework) überwachen. Bitte schauen Sie dort nach, um Hilfe bei der Lösung verschiedener Probleme zu erhalten oder eine Frage zu stellen.
