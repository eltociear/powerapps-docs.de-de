---
title: HTTP-Abfragen erstellen und Fehler behandeln (Common Data Service)| Microsoft Docs
description: Lesen Sie über die HTTP-Methoden und Header, die einen Teil der HTTP-Anforderungen, die mit der Web-API interagieren, formieren, und wie Fehler, die in Antwort zurückgegeben werden, zu erkennen und zu beheben.
ms.custom: ''
ms.date: 11/05/2018
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 64a39182-25de-4d31-951c-852025a75811
caps.latest.revision: 13
author: JimDaly
ms.author: jdaly
ms.reviewer: susikka
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 405e27d3461f78a2452de1c8b19d99d4d827d879
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "3109024"
---
# <a name="compose-http-requests-and-handle-errors"></a>HTTP-Anforderungen verfassen und Fehler beheben

Sie interagieren mit der Web-API, indem Sie HTTP-Anforderungen erstellen und senden. Sie müssen wissen, wie die entsprechenden HTTP-Kopfzeilen festgelegt werden, und auf mögliche Fehler in der Antwort reagieren.  

<a name="bkmk_url_versions"></a>

## <a name="web-api-url-and-versions"></a>Web-API-URL und Versionen

Um auf die Web-API zuzugreifen, müssen Sie eine URL mithilfe von Teilen der folgenden Tabelle verfassen.

|Komponente|Beschreibung|
|--|--|
|Protokoll| `https://`|
|Umgebungsname|Der eindeutige Name, der für Ihre Umgebung gilt. Wenn Ihr Firmennamen *Contoso* ist, kann er `contoso` sein.|
|Region|Ihre Umgebung ist in der Regel in einem Rechenzentrum in Ihrer Nähe verfügbar.<br />Nordamerika: `crm`<br />Südamerika: `crm2`<br />Kanada: `crm3`<br />Europa, Naher Osten und Afrika (EMEA): `crm4`<br />Asien-Pazifik (APAC): `crm5`<br />Ozeanien: `crm6`<br />Japan: `crm7`<br />Indien: `crm8`<br />Nordamerika 2: `crm9`<br />Vereinigtes Königreich: `crm11`<br />Frankreich: `crm12`<br />Die Werte werden im Laufe der Zeit hinzugefügt, wenn neue Rechenzentrumregionen geöffnet werden.|
|Basis-URL|`dynamics.com.`|
|Web-API-Pfad|Der Pfad zur Web-API ist `/api/data/`.|
|Version|   Die Version wird auf folgende Weise ausgedrückt: `v[Major_version].[Minor_version][PatchVersion]/`. Die gültige Version für diese Freigabe ist `v9.0`.|
|Ressource|Der Name der Entität, Funktion oder Aktionen, die Sie verwenden möchten.|


Die URL, die Sie verwenden, wird mit diesen Teilen zusammengesetzt: Protokoll + Umgebungsname + Region + Basis-URL + Web-API-Pfad + Version + Ressource.

<a name="version_compatiblity"></a>

###   <a name="version-compatibility"></a>Versionskompatibilität

Diese Version führt Funktionen ein, die bei älteren Versionen nicht verfügbar sind. Nachfolgende Nebenversionen bieten ggf. weitere Funktionen, die nicht auf die früheren Nebenversionen zurückübertragen werden. Ihr Code, der für v9.0 geschrieben ist, wird weiterhin in zukünftigen Versionen funktionieren, wenn Sie in der verwendeten URL auf v9.0 verweisen.

Sobald neue Funktionen eingeführt sind, können sie mit früheren Versionen kollidieren. Dies ist erforderlich, um den Dienst besser zu machen. Meistens bleiben Funktionen identisch zwischen Versionen, aber Sie sollten darauf nicht zählen, dass sie so bleiben würden.

> [!NOTE]
> Im Gegensatz zur v8.x-Untersatzversionen werden die neuen Funktionen oder andere Änderungen,, die in zukünftigen Versionen hinzugefügt werden, für frühere Versionen nicht anwendbar.
> Sie müssen auf die Version des Dienstes, den Sie verwenden, aufpassen und Ihren Code danach prüfen, ob Sie die verwendete Version nicht geändert haben.

<a name="bkmk_methods"></a>

## <a name="http-methods"></a>HTTP-Methoden

 HTTP-Anforderungen können zahlreiche verschiedene Methoden anwenden. Wenn Sie die Internet-API verwenden, werden Sie nur die in der folgenden Tabelle aufgeführten Methoden anwenden.  
  
|Methode|Verwendung|  
|------------|-----------|  
|GET|Wird verwendet, wenn Daten inkl. aufrufender Funktionen abgerufen werden. Der erwartete Statuscode für einen erfolgreiches Abrufen ist 200 OK.|  
|POST|Wird verwendet wenn Entitäten erstellt oder Aktionen aufgerufen werden.|  
|PATCH|Wird verwendet, wenn Entitäten aktualisiert werden oder Upsert Vorgänge ausgeführt werden.|  
|DELETE|Wir verwendet, wenn Entitäten oder Einzelpersoneneigenschaften gelöscht werden.|  
|PUT|Verwendung in bestimmten Fällen zur Aktualisierung einzelner Eigenschaften von Entitäten. Diese Methode wird nicht empfohlen, wenn die meisten Entitäten aktualisiert werden. Verwenden Sie diese Option, wenn Sie Entitäten vorbildliche aktualisieren.|  
  
<a name="bkmk_headers"></a>

## <a name="http-headers"></a>HTTP-Kopfzeilen

Obwohl das OData-Protokoll sowohl das JSON- als auch ATOM-Format zulässt, unzerstützt die Web-API nur JSON. Deshalb können folgende Kopfzeilen angewandt werden.  
  
Jede Anfrage sollte den Accept-Kopfzeilenwert von `application/json` beinhalten, auch wenn keine Antwort erwartet wird. Jeder Fehler, der in der Antwort zurückgegeben worden ist, wird als JSON zurückgegeben. Auch wenn Ihr Code verwendet werden kann, wenn die Kopfzeile nicht enthalten ist, sollten Sie sie im Rahmen der bewährten Methoden einschließen.  
  
Die aktuelle OData-Version ist 4.0, aber zukünftige Versionen werden die Möglichkeit bieten neue Funktionen zu verwenden. Um sicherzustellen dass es keine Verwechselung der OData-Version für den Code gibt, sollten Sie immer eine die aktuellen OData-Version sowie die neustmögliche Version für den Code angeben. Verwenden Sie OData-Version- und OData-MaxVersion-Kopfzeilen, um einen Wert auf 4.0 zu setzen.  
 
Abfragen angezeigt, die unter Umständen Sammlung-bewertete erweitern Navigationseigenschaften zwischengespeicherten Daten für diese Eigenschaften zurückgibt, die keine neuen Änderungen angezeigt. Fügen Sie `If-None-Match: null`-Kopfzeile im Anforderungstext, um Browserzwischenspeicher der Web-API-Anforderung zu überschreiben. Weitere Informationen finden Sie unter [Hypertext Transfer Protocol (HTTP/1.1): Bedingte Anforderungen 3.2 : If-None-Match](https://tools.ietf.org/html/rfc7232#section-3.2).
 
Alle HTTP-Kopfzeilen sollten folgende mindestens folgende Kopfzeilen enthalten.  
  
```
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0
If-None-Match: null
```  
  
Jede Anfrage, die JSON-Daten im Anforderungstext enthält, muss eine Content-Type-Kopfzeile mit einem Wert von `application/json` beinhalten.  
  
```  
Content-Type: application/json  
```  
  
Sie können zusätzliche Kopfzeilen verwenden, um bestimmte Möglichkeiten zu aktivieren.  
  
-   Um Daten für Erstellen- (POST) oder Aktualisieren (PATCH)-Vorgänge für Entitäten zurückzugeben, nutzen Sie die `return=representation`-Einstellung. Wenn diese Einstellung auf eine POST-Anfrage angewendet wurde, hat eine erfolgreiche Antwort den Status 201 (erstellt). Eine PATCH-Anfrage hat eine erfolgreiche Antwort den Status 200 (OK). Ohne diese angewendete Einstellung haben beide Vorgänge Status 204 (Kein Inhalt), um anzuzeigen, dass standardmäßig keine Daten im Textteil der Antwort zurückgegeben werden.  
  
-   Um formatierte Werte mit einer Abfrage zurückzugeben, schließen die odata.include-annotations-Einstellung, gesetzt auf Microsoft.Dynamics.CRM.formattedvalue mithilfe der [Prefer](https://tools.ietf.org/html/rfc7240)-Kopfzeile festgelegt wurde, ein. Weitere Informationen:[Formatierte Werte einschließen](query-data-web-api.md#bkmk_includeFormattedValues)  
  
-   Sie können die Prefer-Kopfzeile mit der odata.maxpagesize-Option auch dazu verwenden, anzugeben, wie viele Seiten Sie zurückgeben möchten. Weitere Informationen:[Anzahl der auf einer Seite zurückzugebenden Entitäten angeben](query-data-web-api.md#bkmk_specifyNumber)  
  
-   Um den Kontaxt eines andern Benutzers zu nutzen wenn der Aufrufer die entsprechenden Berechtigungen hat, fügen Sie die MSCRMCallerID-Kopfzeile mit dem systemuserid-Wert des Benutzers hinzu. Weitere Informationen:[Annehmen eines anderen Benutzerkontos mit Web API](impersonate-another-user-web-api.md).  
  
-   Um die optimistische Parallelität anzuwenden, können Sie die [If-Match](https://tools.ietf.org/html/rfc7232#section-3.1)-Kopfzeile mit einem Etag-Wert anwenden. Weitere Informationen:[Wenden Sie optimistische Parallelität an](perform-conditional-operations-using-web-api.md#bkmk_Applyoptimisticconcurrency).  
  
-   Um zu prüfen, ob ein Upsert-Vorgang tatsächlich eine Entität erstellen oder aktualisiert, können Sie die Kopfzeilen If-Match- und [If-None-Match](https://tools.ietf.org/html/rfc7232#section-3.2)-Kopfzeilen verwenden. Weitere Informationen:[Upsert einer Entität](update-delete-entities-using-web-api.md#bkmk_upsert).  
  
-   Wenn Sie Batchbetriebe ausführen, müssen Sie in der Anforderung verschiedene Kopfzeilen anwenden sowie für jeden Teil, in dem der Text gesendet wird. Weitere Informationen:[Ausführen von Batchvorgängen mit der Web-API](execute-batch-operations-using-web-api.md).  
  
<a name="bkmk_statusCodes"></a>

## <a name="identify-status-codes"></a>Ermitteln von Statuscodes

 Egal, ob eine HTTP-Anforderung erfolgreich ist oder fehlschlägt, die Antwort umfasst einen Statuscode. Die Statuscodes, die durch Common Data Service Web API zurückgegeben werden umfassen Folgendes.  
  
|Code|Beschreibung|Typ|  
|----------|-----------------|----------|  
|200 OK|Dies annehmen, wenn durch den Vorgang Daten im Antworttext zurückgegeben werden.|Erfolgreich|  
|201 Erstellt|Erwarten Sie dies, wenn Ihr Entitäts-POST-Vorgang erfolgreich ist und Sie die `return=representation`-Einstellung in der Anfrage angegeben haben.|Erfolgreich|  
|204 Kein Inhalt|Dies annehmen, wenn der Vorgang erfolgreich durchgeführt wird, jedoch keine Daten im Antworttext zurückgegeben werden.|Erfolgreich|  
|304 Nicht geändert|Dies beim Testen, ob eine Entität seit dem letzten Abruf geändert wurde, annehmen. Weitere Informationen:[Bedingte Abrufe](perform-conditional-operations-using-web-api.md#bkmk_DetectIfChanged).|Umleitung|  
|403 Verboten|Folgendes für die folgenden Fehlertypen annehmen:<br /><br /> -   AccessDenied<br />-   AttributePermissionReadIsMissing<br />-   AttributePermissionUpdateIsMissingDuringUpdate<br />-   AttributePrivilegeCreateIsMissing<br />-   CannotActOnBehalfOfAnotherUser<br />-   CannotAddOrActonBehalfAnotherUserPrivilege<br />-   CrmSecurityError<br />-   InvalidAccessRights<br />-   PrincipalPrivilegeDenied<br />-   PrivilegeCreateIsDisabledForOrganization<br />-   PrivilegeDenied<br />-   unManagedinvalidprincipal<br />-   unManagedinvalidprivilegeedepth|Client-Fehler|  
|401 Nicht autorisiert|Folgendes für die folgenden Fehlertypen annehmen:<br /><br /> -   BadAuthTicket<br />-   ExpiredAuthTicket<br />-   InsufficientAuthTicket<br />-   InvalidAuthTicket<br />-   InvalidUserAuth<br />-   MissingCrmAuthenticationToken<br />-   MissingCrmAuthenticationTokenOrganizationName<br />-   RequestIsNotAuthenticated<br />-   TamperedAuthTicket<br />-   UnauthorizedAccess<br />-   UnManagedInvalidSecurityPrincipal|Client-Fehler|  
|413 Nutzlast zu groß|Dies annehmen, wenn die Anforderung zu lang ist.|Client-Fehler|  
|400 BadRequest|Dies annehmen, wenn ein Argument ungültig ist.|Client-Fehler|  
|404 Seite nicht gefunden|Dies annehmen, wenn die Ressource nicht vorhanden ist.|Client-Fehler|  
|405 Methode nicht erlaubt|Dieser Fehler tritt für falsche Methoden und Ressourcenkombinationen auf. Beispielsweise können Sie weder DELETE noch PATCH bei einer Sammlung von Entitäten verwenden.<br /><br /> Folgendes für die folgenden Fehlertypen annehmen:<br /><br /> -   CannotDeleteDueToAssociation<br />-   InvalidOperation<br />-   NotSupported|Client-Fehler|  
|412 Vorbedingung gescheitert|Folgendes für die folgenden Fehlertypen annehmen:<br /><br /> -   ConcurrencyVersionMismatch<br />-   DuplicateRecord|Client-Fehler|
|429 zu viele Anforderungen|Erwarten Sie dies, wenn API-Begrenzungen überschritten werden. Für weitere Informationen gehen Sie zu: [API-Grenzwerte für den Serviceschutz](../api-limits.md)|Client-Fehler|  
|501 Nicht implementiert|Rechnen Sie damit, wenn ein angeforderter Vorgang nicht implementiert wird.|Serverfehler|  
|503 Service nicht verfügbar|Dies annehmen, wenn der Web-API-Service nicht verfügbar ist.|Serverfehler|  
  
<a name="bkmk_parseErrors"></a>

## <a name="parse-errors-from-the-response"></a>Analysefehler von der Antwort

 Details zu Fehlern sind als JSON in der Antwort enthalten. Fehler werden in diesem Format angezeigt.  
  
```json  
{  
 "error":{  
  "code": "<This code is not related to the http status code and is frequently empty>",  
  "message": "<A message describing the error>",  
  "innererror": {  
   "message": "<A message describing the error, this is frequently the same as the outer message>",  
   "type": "Microsoft.Crm.CrmHttpException",  
   "stacktrace": "<Details from the server about where the error occurred>"  
  }  
 }  
}  
```  
  
### <a name="see-also"></a>Siehe auch  

[Vorgänge mithilfe der Web-API ausführen](perform-operations-web-api.md)<br />
[Datenabfrage mit Web-API](query-data-web-api.md)<br />
[Erstellen einer Entität mithilfe des Web-API](create-entity-web-api.md)<br />
[Abrufen einer Entität mithilfe des Web-API](retrieve-entity-using-web-api.md)<br />
[Entitäten aktualisieren und löschen mithilfe der Web API](update-delete-entities-using-web-api.md)<br />
[Entitäten zuordnen und Zuordnungen aufheben mithilfe der Web API](associate-disassociate-entities-using-web-api.md)<br />
[Nutzen von Web-API-Funktionen](use-web-api-functions.md)<br />
[Nutzen von Web-API-Aktionen](use-web-api-actions.md)<br />
[Ausführen von Batchbetrieben mithilfe der Web-API](execute-batch-operations-using-web-api.md)<br />
[Annehmen eines anderen Benutzerkontos mit Web API](impersonate-another-user-web-api.md)<br />
[Bedingte Vorgänge mithilfe der Web-API ausführen](perform-conditional-operations-using-web-api.md)
