---
title: Web-API CDSWebApiService-Klasse (C#) (Common Data Service) | Microsoft Docs
description: Dieses Beispielprojekt für die .NET Framework-Klassenbibliothek zeigt eine Assembly zur Definition eines Service-Clients bei Verwendung der Common Data Service Web-API und C#.
ms.custom: ''
ms.date: 04/20/2020
ms.service: powerapps
applies_to:
- Dynamics 365 (online)
author: JimDaly
ms.author: pehecke
ms.reviewer: pehecke
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5b0b8335352d80585a9f36494bc5b8f7a06b8b2b
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "3276703"
---
# <a name="web-api-cdswebapiservice-class-sample-c"></a>Web-API CDSWebApiService-Klassenbeispiel (C#)


Dies ist ein .NET Framework-Klassenbibliotheksprojekt, das bei Verwendung der CDS-Web-API eine Assembly zur Definition eines Dienstes erstellt.

Diese Assembly zeigt, wie das geht:

- Erstellen Sie Ihren Code '[DRY](/dotnet/architecture/modern-web-apps-azure/architectural-principles#dont-repeat-yourself-dry)-mäßiger, indem Sie gängige Operationen mit Http-Methoden umbrechen.
- Verwalten Sie eine <xref:System.Net.Http.HttpClient> auf thread-sichere Weise.
- Verwalten der Service Protection Limit API [429 Zu viele Anfragen](https://developer.mozilla.org/docs/Web/HTTP/Status/429) Fehler, mit denen eine Client-Anwendung rechnen muss.
    - Für weitere Informationen gehen Sie zu: [API-Grenzwerte für den Serviceschutz](../../api-limits.md)

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt, wie eine CDSWebAPIService-Instanz instanziiert und ein Kontaktdatensatz erstellt wird.

In diesem Beispiel wird erwartet, dass die Verbindungszeichenfolge in der Datei App.config wie unten gezeigt eingestellt ist.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0"
                      sku=".NETFramework,Version=v4.7.2" />
  </startup>
  <connectionStrings>
    <add name="Connect"
         connectionString="Url=https://yourorg.api.crm.dynamics.com;
         Authority=null;
         ClientId=51f81489-12ee-4a9e-aaae-a2591f45987d;
         RedirectUrl=app://58145B91-0C36-4500-8554-080854F2AC97;
         UserPrincipalName=you@yourorg.onmicrosoft.com;
         Password=y0urp455w0rd;
         CallerObjectId=null;
         Version=9.1;
         MaxRetries=3;
         TimeoutInSeconds=180;
         "/>
  </connectionStrings>
</configuration>
```
Der Code greift auf die Verbindungszeichenfolge zu, um den CDSWebApiService zu instanziieren.

```csharp
//Get configuration data from App.config connectionStrings
static readonly string connectionString = ConfigurationManager.ConnectionStrings["Connect"].ConnectionString;
static readonly ServiceConfig config = new ServiceConfig(connectionString);

    using (CDSWebApiService svc = new CDSWebApiService(config))
    {
        //Create a contact
        var contact1 = new JObject
            {
                { "firstname", "Rafel" },
                { "lastname", "Shillo" }
            };
        Uri contact1Uri = svc.PostCreate("contacts", contact1);
    }
```

## <a name="properties"></a>Eigenschaften

Diese Klasse legt nur die Eigenschaft **BaseAddress** offen. Dies ist die konfigurierte <xref:System.Net.Http.HttpClient.BaseAddress>, die von der <xref:System.Net.Http.HttpClient> verwendet wird. Es kann nützlich sein, bei Bedarf vollständige URIs zu erstellen, da in den meisten Fällen relative URIs erwartet werden.

## <a name="methods"></a>Methoden

Diese Klasse stellt die folgenden öffentlichen Methoden zur Verfügung:

## <a name="postcreate"></a>PostCreate

Erstellt eine Entität synchron und gibt den URI zurück.

### <a name="parameters"></a>Parameter

|Name  |Typ  |Beschreibung  |
|---------|---------|---------|
|entitySetName|<xref:System.String>|Der Name des Entitätssatzes für den Typ der zu erstellenden Entitäten. |
|Textkörper|[JObject](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_Linq_JObject.htm)|Enthält die Daten für die zu erstellende Entität|

### <a name="return-value"></a>Rückgabewert

Die <xref:System.Uri> der erstellten Entitäten

### <a name="remarks"></a>Anmerkungen

Diese Methode wird angeboten, weil die Erstellung von Entitäten ein üblicher Vorgang ist und der URI im `OData-EntityId` Header zurückgegeben wird. Mit dieser speziellen Methode ist weniger Code erforderlich als mit der Methode [Post](#post), die nur ein [JObject](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_Linq_JObject.htm) zurückgibt.

Weitere Informationen: [Erstellen Sie einen Entitäten-Datensatz mit der Web-API](../create-entity-web-api.md).

## <a name="postcreateasync"></a>PostCreateAsync

Die asynchrone Version von [PostCreate](#postcreate).

## <a name="post"></a>Nachricht

Sendet synchron eine `POST`-Anfrage und gibt die Antwort als [JObject](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_Linq_JObject.htm) zurück.

### <a name="parameters"></a>Parameter

|Name  |Typ  |Beschreibung  |
|---------|---------|---------|
|path|<xref:System.String>|Der relative Pfad zum Senden der Anfrage. Häufig der Name einer Aktion oder der Name eines Entitäten-Sets.|
|Textkörper|[JObject](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_Linq_JObject.htm)|Der Payload für `POST`|
|Header|`Dictionary<string, List<string>>`|(Optional) Alle Header, die zur Anwendung spezieller Verhaltensweisen erforderlich sind|

### <a name="return-value"></a>Rückgabewert

Ein [JObject](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_Linq_JObject.htm), das die Antwort enthält.

### <a name="remarks"></a>Anmerkungen

Diese Methode kann für jede Operation mit der `POST` http-Methode verwendet werden, umfasst jedoch nur den Antwortinhalt. Verwenden Sie [PostCreate](#postcreate), um Entitäten zu erstellen und nur die URI der erstellten Entität zurückzugeben.

Weitere Informationen:

- [Erstellen mit den zurückgegebenen Daten](../create-entity-web-api.md#create-with-data-returned)
- [Nutzen von Web-API-Aktionen](../use-web-api-actions.md)


## <a name="postasync"></a>PostAsync

Die asynchrone Version von [Post](#post).

## <a name="patch"></a>Patch

Sendet eine `PATCH`-Anforderung synchron.

### <a name="parameters"></a>Parameter

|Name  |Typ  |Beschreibung  |
|---------|---------|---------|
|URI|<xref:System.Uri>|Der relative Pfad zum Senden der Anfrage. Häufig der Uri für eine bestimmte Entität|
|Textkörper|[JObject](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_Linq_JObject.htm)|Der zu sendende Payload|
|Header|`Dictionary<string, List<string>>`|(Optional) Alle Header, die zur Anwendung spezieller Verhaltensweisen erforderlich sind|

### <a name="remarks"></a>Anmerkungen

Patch wird häufig zur Aktualisierung oder Aktualisierung von Datensätzen verwendet.

Weitere Informationen:

- [Grundlegende Aktualisierung](../update-delete-entities-using-web-api.md#basic-update)
- [Upsert einer Entität](../update-delete-entities-using-web-api.md#upsert-an-entity)

## <a name="patchasync"></a>PatchAsync

Die asynchrone Version von [Patch](#patch).

## <a name="get"></a>Abrufen

Sendet eine `GET`-Anfrage synchron und gibt Daten zurück

### <a name="parameters"></a>Parameter

|Name  |Typ  |Beschreibung  |
|---------|---------|---------|
|path|<xref:System.String>|Der relative Pfad der zurückzugebenden Ressource |
|Header|`Dictionary<string, List<string>>`|(Optional) Alle Header, die zur Anwendung spezieller Verhaltensweisen erforderlich sind|

### <a name="return-value"></a>Rückgabewert

Ein [JToken](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_Linq_JToken.htm), das die angeforderten Daten repräsentiert.

### <a name="remarks"></a>Anmerkungen

Weitere Informationen:

- [Datenabfrage mit Web-API](../query-data-web-api.md)
- [Abrufen eines Entitätsdatensatzes mit der Web-API](../retrieve-entity-using-web-api.md)
- [Nutzen von Web-API-Funktionen](../use-web-api-functions.md)


## <a name="getasync"></a>GetAsync

Die asynchrone Version von [Get](#get).

## <a name="delete"></a>Löschen

Sendet eine `DELETE`-Anforderung synchron.

### <a name="parameters"></a>Parameter

|Name  |Typ  |Beschreibung  |
|---------|---------|---------|
|URI|<xref:System.Uri>|Der relative Pfad der zu löschenden Ressource |
|Header|`Dictionary<string, List<string>>`|(Optional) Alle Header, die zur Anwendung spezieller Verhaltensweisen erforderlich sind|

### <a name="remarks"></a>Anmerkungen

Weitere Informationen:

- [Grundlegende Löschung](../update-delete-entities-using-web-api.md#basic-delete)
- [Entfernen Sie eine Referenz auf eine Entität](../associate-disassociate-entities-using-web-api.md#remove-a-reference-to-an-entity)
- [Löschen Sie einen einzelnen Eigenschaftswert](../update-delete-entities-using-web-api.md#delete-a-single-property-value)

## <a name="deleteasync"></a>DeleteAsync

Die asynchrone Version von [Delete](#delete).

## <a name="put"></a>Einlagern

Sendet eine `PUT`-Anforderung synchron.

### <a name="parameters"></a>Parameter

|Name  |Typ  |Beschreibung  |
|---------|---------|---------|
|URI|<xref:System.Uri>|Der relative Pfad zu der zu aktualisierenden Ressource.|
|eigenschaft|<xref:System.String>|Der Name der zu aktualisierenden Eigenschaft|
|Wert|<xref:System.String>|Der einzustellende Wert|

### <a name="remarks"></a>Anmerkungen

Put wird verwendet, um bestimmte Entitätseigenschaften zu aktualisieren.

**Anmerkung**: Die Http `PUT` Methode wird auch zur Aktualisierung der Metadaten verwendet. Diese Methode kann nicht für diesen Zweck verwendet werden. Es ist speziell für Geschäftsdaten gedacht.

Weitere Informationen: 

- [Aktualisieren Sie einen einzelnen Eigenschaftswert](../update-delete-entities-using-web-api.md#update-a-single-property-value)
- [Ändern Sie die Referenz in einer einzelwertigen Navigationseigenschaft](../associate-disassociate-entities-using-web-api.md#change-the-reference-in-a-single-valued-navigation-property)


## <a name="putasync"></a>PutAsync

Die asynchrone Version von [Post](#put).

## <a name="private-sendasync-method"></a>Private SendAsync-Methode

Alle der oben genannten Methoden leiten ihre Anfragen über die private `SendAsync`-Methode weiter. An dieser Stelle tritt die gemeinsame Logik auf niedriger Ebene auf.

Diese Methode enthält die Logik, um alle Fehler der Service Protection API 429 zu verwalten und sie für eine im Dienst konfigurierbare Anzahl von Malen erneut zu versuchen.

Zu diesem Zweck wird eine Kopie der Anforderung statt der eigentlichen Anforderung gesendet, da die Anforderung entsorgt wird und nicht erneut gesendet werden kann, wenn ein Fehler zurückgegeben wird.

Die Kopie der Anfrage ist aufgrund der in der Datei Extensions.cs definierten benutzerdefinierten Methode <xref:System.Net.Http.HttpRequestMessage> `Clone` verfügbar.

## <a name="oauthmessagehandler"></a>OAuthMessageHandler

Wenn die interne <xref:System.Net.Http.HttpClient> im CDSWebApiService-Konstruktor initialisiert wird, wird eine Instanz dieser Klasse als <xref:System.Net.Http.HttpMessageHandler> festgelegt. Diese Klasse arbeitet mit den ADAL-Bibliotheken zusammen, um sicherzustellen, dass die `accessToken` jedes Mal aktualisiert wird, wenn eine Anfrage gesendet wird. Wenn die `accessToken` abläuft, wird sie von den ADAL-Bibliotheksmethoden automatisch aktualisiert.

Weitere Informationen: [Beispiel zur Demonstration eines DelegatingHandlers](../../authenticate-oauth.md#example-demonstrating-a-delegatinghandler)

## <a name="serviceconfig"></a>ServiceConfig

Die CDSWebApiService-Klasse sollte mit einer Verbindungszeichenfolge über die ServiceConfig-Klasse initialisiert werden.

Der ServiceConfig-Konstruktor akzeptiert eine Verbindungszeichenfolge, normalerweise aus der App.config-Konfiguration, und die dort definierten Daten werden in eine ServiceConfig-Instanz geparst, die der CDSWebApiService-Konstruktor benötigt.

### <a name="properties"></a>Eigenschaften

Im Folgenden sind die Eigenschaften der ServiceConfig-Klasse aufgeführt.

|Name|Typ|Beschreibung|
|---------|---------|---------|
|Autoritative Stelle|<xref:System.String>|Die Autorisierung, mit der der Benutzer autorisiert wird. Voreinstellung ist https://login.microsoftonline.com/common|
|CallerObjectId|<xref:System.Guid>|Die Azure AD ObjectId für den Benutzer, um sich als andere Benutzer auszugeben.|
|-Client-ID|<xref:System.String>|Die mit Azure AD registrierte ID der Anwendung|
|MaxRetries|<xref:System.Byte>|Die maximale Anzahl von Versuchen, eine durch Dienstschutzgrenzen blockierte Anforderung erneut zu versuchen. Die Standardeinstellung ist 3.|
|Kennwort|<xref:System.Security.SecureString>|Das Passwort für den Benutzerprinzipal|
|RedirectUrl|<xref:System.String>|Die Redirect Url der mit Azure AD registrierten Anwendung|
|TimeoutInSeconds|`ushort`|Die Zeitspanne, in der versucht wird, einen Antrag abzuschließen, bevor er storniert wird. Der Standardwert ist 120 (2 Minuten)|
|URL|<xref:System.String>|Die Url zur CDS-Umgebung, d.h "https://yourorg.api.crm.dynamics.com"|
|UserPrincipalName|<xref:System.String>|Der Hauptname des Benutzers. d.h. you@yourorg.onmicrosoft.com|
|Version|<xref:System.String>|Die zu verwendende Version der Web-API. Die Voreinstellung ist '9.1'|

### <a name="example-connection-string"></a>Beispiel für eine Verbindungszeichenfolge

Jedes der Beispiele, die CDSWebApiService verwenden, enthält einen Verweis auf eine gemeinsame App.config und Code zum Lesen eines Verbindungszeichenkettenwertes namens `Connect`. Es folgt ein Beispiel für diese App.config:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0"
                      sku=".NETFramework,Version=v4.7.2" />
  </startup>
  <connectionStrings>
    <add name="Connect"
         connectionString="Url=https://yourorg.api.crm.dynamics.com;
         Authority=null;
         ClientId=51f81489-12ee-4a9e-aaae-a2591f45987d;
         RedirectUrl=app://58145B91-0C36-4500-8554-080854F2AC97;
         UserPrincipalName=you@yourorg.onmicrosoft.com;
         Password=y0urp455w0rd;
         CallerObjectId=null;
         Version=9.1;
         MaxRetries=3;
         TimeoutInSeconds=180;
         "/>
  </connectionStrings>
</configuration>
```

Die Werte **ClientId** und **RedirectUrl** sind für Beispielanwendungen. Sie können diese zum Ausführen der Beispiele verwenden, aber Sie sollten Ihre eigenen Anwendungen registrieren und die entsprechenden Werte für diese Eigenschaften eingeben. 

Weitere Informationen: [Exemplarische Vorgehensweise: Registrieren einer App mit Azure Active Directory](../../walkthrough-register-app-azure-active-directory.md)

## <a name="serviceexception"></a>ServiceException

Diese Klasse erweitert einfach die <xref:System.Exception> und stellt zusätzliche Eigenschaften aus einer Fehlerantwort zur Verfügung.

### <a name="properties"></a>Eigenschaften

|Name  |Typ  |Beschreibung  |
|---------|---------|---------|
|Nachricht|<xref:System.String>|Die von der Plattform zurückgegebene Meldung|
|ErrorCode|<xref:System.Int32>|Der von der Plattform zurückgegebene Fehlercode|
|StatusCode|<xref:System.Int32>|Im <xref:System.Net.Http.HttpResponseMessage>.<xref:System.Net.Http.HttpResponseMessage.StatusCode>|
|ReasonPhrase|<xref:System.String>|Im <xref:System.Net.Http.HttpResponseMessage>.<xref:System.Net.Http.HttpResponseMessage.ReasonPhrase>|

## <a name="samples-using-this-class"></a>Beispiele, die diese Klasse verwenden

Die folgenden Beispiele verwenden diese Klasse:

- [Web-API CDSWebApiService Beispiel für grundlegende Operationen (C#)](cdswebapiservice-basic-operations.md)
- [Web-API CDSWebApiService-Beispiel für parallele Operationen (C#)](cdswebapiservice-parallel-operations.md)
- [Web-API CDSWebApiService Async Parallel Operations Beispiel (C#)](cdswebapiservice-async-parallel-operations.md)