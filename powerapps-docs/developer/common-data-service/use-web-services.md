---
title: Verwenden von Webdiensten für Common Data Service für Apps | Microsoft-Dokumentation
description: Erfahren Sie, wie Entwickler Webdienste für Common Data Service für Apps verwenden können.
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: faisalmo
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 02/26/2018
ms.author: jdaly
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 7e9e14a9d44a3326fb8ac32b11e46b61cc119c27
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "42854436"
---
# <a name="use-common-data-service-for-apps-web-services"></a>Verwenden von Webdiensten für Common Data Service für Apps

Common Data Service für Apps bietet zwei Webdienste, die Sie zum Interagieren mit Daten verwenden können. Sie können den Webdienst auswählen, der Ihren Anforderungen und Ihren Fähigkeiten am besten entspricht. Weitere Informationen finden Sie unter [Dynamics 365 Customer Engagement Developer Guide: Choose your development style for Dynamics 365 Customer Engagement (Entwicklerhandbuch zu Dynamics 365 Customer Engagement: Flexible Möglichkeiten bei der Entwicklung mit Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/choose-development-style)

## <a name="web-api"></a>Web-API
Bei der Web-API handelt es sich um einen OData v4 RESTful-Endpunkt. Verwenden Sie diese API für alle Programmiersprachen, die HTTP-Anforderungen und die Authentifizierung mit OAuth 2.0 unterstützen.

Weitere Informationen finden Sie unter [Dynamics 365 Customer Engagement Developer Guide: Use the Dynamics 365 Customer Engagement Web API (Entwicklerhandbuch zu Dynamics 365 Customer Engagement: Verwenden der Web-API für Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/use-microsoft-dynamics-365-web-api)

## <a name="organization-service"></a>Organisationsdienst

Beim Organisationsdienst handelt es sich um einen wichtigen Bestandteil der Plattform Common Data Service für Apps. Es ist ein Windows Communication Foundation-Dienst (WCF), der derzeit nur einen SOAP-Endpunkt umfasst. .NET-Entwickler können die SDK-Assemblys verwenden, um Datenvorgänge durchzuführen. Im Zusammenhang mit einem Plug-In stellt die Verwendung des Organisationsdiensts über SDK-Assemblys die einzige Möglichkeit dar.
> [!NOTE]
> Entwickler können zwar auch den SOAP-Endpunkt des Organisationsdiensts ohne .NET SDK-Assemblys verwenden, aber die Web-API stellt aufgrund ihrer RESTful-Eigenschaft eine viel bessere Alternative dar.

Weitere Informationen finden Sie unter [Verwenden des Dynamics 365-Organisationsdiensts](/dynamics365/customer-engagement/developer/use-microsoft-dynamics-365-organization-service).

## <a name="about-the-web-services-and-the-platform"></a>Informationen zu den Webdiensten und der Plattform

Es ist wichtig hervorzuheben, dass der Organisationsdienst die Plattform definiert. Aufgrund der Web-API gestaltet sich das Programmieren zwar als RESTful, aber letztendlich müssen alle Datenvorgänge über den zugrundeliegenden Organisationsdienst durchgeführt werden. 

Der Organisationsdienst definiert die unterstützten Vorgänge als Meldungen. Jede Meldung verfügt über einen Namen. Innerhalb der SDK-Assemblys verfügt jede Meldung über einen *&lt;Meldungsnamen&gt;*`Request` und die Klasse *&lt;Meldungsname&gt;*`Response`. Die [IOrganizationService-Schnittstelle](/dotnet/api/microsoft.xrm.sdk.iorganizationservice) in dem `Microsoft.Xrm.Sdk.dll`-Element definiert mehrere Hilfsprogrammmethoden für häufig verwendete CRUD-Vorgänge sowie eine [Execute-Methode](/dotnet/api/microsoft.xrm.sdk.iorganizationservice.execute), die verwendet werden kann, um Meldungen aufzurufen. Alle Meldungen verwenden die zugrunde liegende [OrganizationRequest-Klasse](/dotnet/api/microsoft.xrm.sdk.organizationrequest).

Die Web-API umfasst zwar dieselben Vorgänge wie der Organisationsdienst, sie stellt diese jedoch mithilfe des OData v4-Protokolls im RESTful-Stil dar. OData v4 stellt über *Funktionen* oder *Aktionen* Vorgänge zur Verfügung, die einen Namen haben. Beinahe alle im Organisationsdienst verfügbaren Meldungen werden als passende Funktionen oder Aktionen zur Verfügung gestellt, die einen Namen haben. Die Meldungen, die CRUD-Vorgängen entsprechen, sind in der Web-API nicht verfügbar, da sie einen RESTful-Dienst ausmachen, der über Implementierungen verfügt, die HTTP-Methoden wie GET, POST, PATCH und DELETE verwenden.

Die .NET SDK-Assemblys für den SOAP-Endpunkt des Organisationsdiensts sind dafür konzipiert, um basierend auf der [IOrganizationService-Schnittstelle](/dotnet/api/microsoft.xrm.sdk.iorganizationservice) die zugrunde liegenden Plattformdienste zu modellieren. Es handelt sich dabei jedoch um unterschiedliche Komponenten, die getrennt voneinander behandelt werden sollten. 

Der SOAP-Endpunkt für den Organisationsdienst wurde 2011 eingeführt und gilt jetzt als veraltet. Er wird aber noch so lange funktionieren, bis er entfernt wird. Es wurde außerdem angekündigt, dass die .NET SDK-Assemblys aktualisiert werden sollen, sodass sie auch noch funktionieren, wenn der SOAP-Endpunkt entfernt wird. Das bedeutet, dass noch bevor der SOAP-Endpunkt entfernt wird, SDK-Assemblys zur Verfügung gestellt werden und Entwickler Ihren Code entsprechend der neuen Assemblys irgendwann anpassen müssen.

## <a name="discovery-services"></a>Ermittlungsdienste

Jeder Common Data Service für Apps-Benutzer soll auf mehrere Common Data Service für Apps-Instanzen zugreifen können. Mithilfe von Ermittlungsdiensten können Sie Code schreiben, um Benutzern eine Liste mit Instanzen zur Verfügung zu stellen, mit denen Sie basierend auf ihrem Microsoft-Konto eine Verbindung herstellen können. Jede Instanz umfasst dann eine URL, die Sie verwenden können, um eine Verbindung mit der ausgewählten Instanz herzustellen. 

Sie können entweder über die Web-API oder den Organisationsdienst auf den Ermittlungsdienst zugreifen.

- Weitere Informationen zu der Web-API finden Sie unter: [Dynamics 365 Customer Engagement Developer Guide: Discover the URL for your organization using the Web API (Entwicklerhandbuch zu Dynamics 365 Customer Engagement: Ermitteln der URL für Ihre Organisation mithilfe der Web-API)](/dynamics365/customer-engagement/developer/webapi/discover-url-organization-web-api)
- Weitere Informationen zum Organisationsdienst finden Sie unter: [Dynamics 365 Customer Engagement Developer Guide: Discover the URL for your organization using the Web API (Entwicklerhandbuch zu Dynamics 365 Customer Engagement: Ermitteln der URL für Ihre Organisation mithilfe der Web-API)](/dynamics365/customer-engagement/developer/org-service/discover-url-organization-organization-service)

## <a name="use-custom-actions"></a>Verwenden von benutzerdefinierten Aktionen

Sie können als deklarative Option für Prozesse *benutzerdefinierte Aktionen* erstellen. Benutzerdefinierte Aktionen werden benötigt, um neue Meldungen im Organisationsdienst zu erstellen. Sie können benutzerdefinierte Aktionen verwenden, um mehrere Vorgänge in einen Vorgang zusammenzufassen, der mehrmals verwendet werden kann. So können Sie beispielsweise eine neue Meldung mit dem Namen *new_Escalate* erstellen, die mehrere Standardvorgänge zusammenfasst, die zur Benachrichtigung der richtigen Personen ausgeführt werden, wenn ein wichtiger Kunde schwerwiegende Probleme gemeldet hat.

Für die Definition der benutzerdefinierten Aktion können Sie die Signatur des Vorgangs auswählen, indem Sie Eingabeparameter und Eigenschaften definieren, die in alle zurückgegebenen Ergebnisse eingefügt werden sollen. Anschließend können mithilfe des Designers oder mithilfe von Code über einen deklarativen Prozess benutzerdefinierte Aktionen ausgelöst werden. 

Was einzigartig an benutzerdefinierten Aktionen ist, ist der Umstand, dass die in ihnen enthaltenen Vorgänge auch von Personen verändert werden können, bei denen es sich nicht um Entwickler handelt. Sie können dafür den Designer verwenden, wenn Sie andere Prozesse nicht beeinträchtigen möchten, oder Sie können auf Code zurückgreifen, der die Aktion aufruft.  Dies ist allerdings nur der Fall, solange die Signatur der Aktion nicht verändert wird. Wenn Sie andere Eingabe- oder Ausgabeeigenschaften benötigen, sollten Sie entweder eine neue benutzerdefinierte Aktion erstellen, um zu vermeiden, dass andere Prozesse angehalten werden, oder Code schreiben, der eine bereits vorhandene Aktion verwendet.

Wenn in einer Umgebung eine benutzerdefinierte Aktion definiert wird, können Sie über die Web-API auf eine neue OData v4-Aktion zugreifen. Innerhalb eines Organisationsdiensts kann dann über die [OrganizationRequest-Klasse](/dotnet/api/microsoft.xrm.sdk.organizationrequest) direkt die benutzerdefinierte Aktion oder über die mithilfe des *Tools zur Codegenerierung (CrmSvcUtil.exe)* generierte stark typisierte Klasse ausgelöst werden.

Weitere Informationen finden Sie unter: 
- [Aktionsübersicht](/dynamics365/customer-engagement/customize/actions)
- [Erstellen Ihrer eigenen Aktionen](/dynamics365/customer-engagement/developer/create-own-actions)
- [Nutzen von Web-API-Aktionen](/dynamics365/customer-engagement/developer/webapi/use-web-api-actions#use-a-custom-action)

## <a name="metadata-services"></a>Metadatendienste

Sowohl die Web-API als auch der Organisationsdienst umfassen Funktionen zum Ausführen von CRUD-Vorgängen im Entitätsschema. Sie können zwar diese Vorgänge mithilfe von Code ausführen, aber in der Regel sollten Sie Designer verwenden, um benutzerdefinierte Schemaelemente hinzuzufügen, zu aktualisieren oder zu löschen. Benutzer müssen über Administratorberechtigungen verfügen, um Schemaänderungen anzuwenden. Metadaten können aber von allen Benutzern gelesen werden.

Metadaten werden häufiger verwendet, um Metadaten zu der Umgebung abzurufen, in der Ihre Erweiterung ausgeführt wird. Da jede Umgebung anders sein kann und Schemadaten die meisten Informationen dazu enthalten, wie die Umgebung konfiguriert ist, müssen Sie diese Informationen möglicherweise abrufen, damit Ihre Erweiterungen andere Anpassungen der Umgebung annehmen können.

Im Folgenden finden Sie zwei Beispiele:
- Die Anzahl der in einem optionset-Attribut verfügbaren Optionen kann sich ändern. Nehmen Sie dann keine Hardcodierung der Werte in Ihrer Umgebung vor, sondern ziehen Sie andere Optionen in Betracht. Sie könne eine Abfrage des Systems durchführen, um zu ermitteln, ob mit der aktuellen Umgebung andere Optionen möglich sind.
- Der Anzeigename einer Entität kann verändert werden. Der Standardanzeigename für die Account-Entität lautet *Account* (Konto). Sie könnten diesen Namen in *Company* (Unternehmen) ändern. Wenn Sie einem Benutzer eine Meldung anzeigen wollen und auf den Namen einer Entität verweisen, sollten Sie diese nicht hartcodieren, sondern stattdessen den Wert verwenden, der den Elementen entspricht, die dem Benutzer für gewöhnlich angezeigt werden. Außerdem sollten Sie den Anzeigenamen verwenden, den Sie aus den Entitätsmetadaten abgerufen haben.

Gute Kenntnisse der Metadaten im System helfen beim Verstehen der Funktionsweise der Plattform Common Data Service für Apps. Die Designer, mit denen Sie Metadaten bearbeiten können, können nicht alle Informationen anzeigen, die in den Metadaten gefunden werden. Sie können eine modellgesteuerte App installieren, die als *Metadata Browser* bezeichnet wird und über die Sie alle ausgeblendeten Eigenschaften von Entitäten und Metadaten, die im System gefunden werden, abrufen können. 

Weitere Informationen finden Sie unter [Durchsuchen der Metadaten für die Organisation](/dynamics365/customer-engagement/developer/browse-your-metadata).

Weitere Informationen zum programmatischen Arbeiten mit Metadaten finden Sie unter den folgenden Links:
- [Verwenden der Web-API mit Metadaten](/dynamics365/customer-engagement/developer/webapi/use-web-api-metadata)
- [Verwenden des Organisationsdienstes mit Dynamics 365-Metadaten](/dynamics365/customer-engagement/developer/org-service/use-organization-service-metadata)
 
### <a name="see-also"></a>Siehe auch

[Common Data Service for Apps Developer Overview (Übersicht für Entwickler: Common Data Service für Apps)](overview.md)

