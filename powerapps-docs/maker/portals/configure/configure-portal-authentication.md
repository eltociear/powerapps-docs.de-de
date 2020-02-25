---
title: Konfigurieren der Portalauthentifizierung | MicrosoftDocs
description: Lernen Sie, wie Sie Authentifizierung für ein Portal konfigurieren.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: acae3e962ed23e9cdff9cf74c1b6c5b7706c23be
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "2979159"
---
# <a name="configure-portal-authentication"></a>Konfigurieren der Portalauthentifizierung

In einer Portalanwendung wird ein authentifizierten Portalbenutzer entweder einem Kontakt oder einem Systembenutzer zugeordnet. Die standardmäßige Portalkonfiguration ist Kontakt-basiert. Zum Anmelden muss der Kontakt eine entsprechende konfigurierte Authentifizierungsinformationen haben. Portalbenutzer muss einer Internetrolle zugewiesen werden, damit Sie Berechtigungen erhalten, die über jene der nicht authentifizierten Benutzer hinausgehen. Um Berechtigungen für eine Internetrolle zu konfigurieren, müssen Sie den Webseitenzugriff und die Webseitenzugriffssteuerungsregeln konfigurieren.

Die aktuelle Portalauthentifizierungsfunktion ermöglicht Portalbenutzern, sich mit einem lokalen Kontakt-Mitgliedschaftsanbieter-Konto oder einem externen Konto ihrer Wahl auf Grundlage der [ASP.NET-Identität](https://www.asp.net/identity) anzumelden.   

- **Lokale Authentifizierung**: Lokale Authentifizierung ist die allgemeine formularbasierte Authentifizierung, die Kontaktdatensätze einer Common Data Service-Umgebung für die Authentifizierung verwendet. Wenn Sie benutzerdefinierte Authentifizierungsumgebungen erstellen möchten, können API-Entwickler die ASP.NET-Identität verwenden, um benutzerdefinierte Anmeldeseiten und -Tools zu erstellen.
- **Externe Authentifizierung**: Externe Authentifizierung wird von der ASP.NET-Identität-API bereitgestellt. In diesem Fall werden Kontoanmeldeinformationen und Kennwortverwaltung von einem Drittanbieter-Identitätsanbieter behandelt. Hierzu zählen OpenID-basierte Anbieter wie Yahoo! sowie Google- und OAuth 2.0-basierte Anbieter, wie Twitter, Facebook und [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]. Benutzer melden sich beim Portal an, indem sie eine externe Identität für die Portalregistrierung auswählen. Nach der Registrierung hat eine externe Identität Zugriff auf dieselben Features wie ein lokales Konto. 

Bei der Registrierung eines lokalen wie auch eines externen Kontos können Einladungscodes und E-Mail-Bestätigungsworkflow für die Anmeldung verwendet werden. Außerdem können Portaladministratoren Authentifizierungsoptionskombinationen über Portalwebsiteeinstellungen aktivieren oder deaktivieren.

> [!NOTE]
> Portalbenutzer müssen eine eindeutige E-Mail-Adresse haben. Wenn zwei oder mehrere Kontaktdatensätze (einschließlich deaktivierte Kontaktdatensätze) die gleiche E-Mail-Adresse haben, werden Kontakte nicht in der Lage sein, sich auf dem Portal zu authentifizieren.

## <a name="account-sign-up-registration"></a>Kontoanmeldung (Registrierung)

Portaladministratoren haben mehrere Möglichkeiten zum Steuern des Kontoanmeldeverhaltens. Die offene Registrierung ist die am wenigsten einschränkende Anmelde-Konfiguration, bei der das Portal einem Benutzerkonto ermöglicht, registriert zu werden, indem einfach eine Benutzeridentität bereitgestellt wird. Alternative Konfigurationen erfordern möglicherweise, dass Benutzer einen Einladungscode oder eine gültige E-Mail-Adresse zum Registrieren beim Portal zur Verfügung stellen. Unabhängig von der Registrierungskonfiguration tragen lokale wie externe Konten gleichermaßen zum Registrierungsworkflow bei. Das bedeutet, dass Benutzer die Option haben, auswählen, mit welcher Art Konto sie sich registrieren möchten.

## <a name="open-registration"></a>Offene Registrierung

Beim Anmelden kann der Benutzer ein lokales Konto erstellen (mit Benutzernamen und Kennwort) oder eine externe Identität aus einer Liste mit Identitätsanbietern auswählen. Wenn eine externe Identität ausgewählt wird, muss sich der Benutzer über den ausgewählten Identitätsanbieter anmelden, um nachzuweisen, dass ihm das externe Konto gehört. In jedem Fall wird der Benutzer sofort beim Portal registriert und authentifiziert. Ein neuer Kontaktdatensatz wird in der Common Data Service-Umgebung erstellt.

Wenn die offene Registrierung aktiviert ist, müssen Benutzer keinen Einladungscode bereitstellen, um den Anmeldeprozess abzuschließen.

### <a name="see-also"></a>Siehe auch

[Festlegen der Authentifizierungsidentität für ein Portal](set-authentication-identity.md)  
