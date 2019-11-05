---
title: Konfigurieren der Portal Authentifizierung | MicrosoftDocs
description: Erfahren Sie, wie Sie die Authentifizierung für ein Portal konfigurieren.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b285ce6e3a93efb72ed867149ce0740f7ee96579
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542759"
---
# <a name="configure-portal-authentication"></a>Konfigurieren der Authentifizierung für ein Portal

In einer Portal Anwendung wird ein authentifizierter Portalbenutzer entweder einem Kontakt oder einem Systembenutzer zugeordnet. Die Standard Portal Konfiguration ist Kontakt basiert. Zum Anmelden muss für einen Kontakt die entsprechenden Webauthentifizierungs Informationen konfiguriert sein. Portal Benutzer müssen Webrollen zugewiesen werden, um Berechtigungen über nicht authentifizierte Benutzer zu erhalten. Um Berechtigungen für eine webrolle zu konfigurieren, konfigurieren Sie den Webseiten Zugriff und die Zugriffs Steuerungs Regeln für die Website.

Die neueste Portal Authentifizierung ermöglicht es Portal Benutzern, sich mit Ihrer Wahl eines lokalen Kontos oder eines externen Kontos, das auf [ASP.net Identity](https://www.asp.net/identity)basiert, anzumelden.   

- **Lokale Authentifizierung**: bei der allgemeinen Formular basierten Authentifizierung werden die Kontaktdaten Sätze einer Common Data Service Umgebung für die Authentifizierung verwendet. Um benutzerdefinierte Authentifizierungsfunktionen zu erstellen, können Entwickler benutzerdefinierte Anmelde Seiten und Tools mit der ASP.net Identity-API erstellen.
- **Externe Authentifizierung**: die externe Authentifizierung wird von der ASP.net Identity-API bereitgestellt. In diesem Fall werden Konto Anmelde Informationen und Kenn Wort Verwaltung von einem Drittanbieter-Identitäts Anbieter verarbeitet. Dies schließt OpenID-basierte Anbieter ein, z. b. Yahoo! und Google-und OAuth 2,0-basierte Anbieter wie Twitter, Facebook und [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]. Benutzer melden sich beim Portal an, indem Sie eine externe Identität für die Registrierung beim Portal auswählen. Nach der Registrierung hat eine externe Identität Zugriff auf dieselben Features wie ein lokales Konto. 

Sowohl für die lokale als auch für die externe Kontoregistrierung können Einladungs Codes für die Registrierung und der e-Mail-Bestätigungs Workflow verwendet werden. Außerdem können Portaladministratoren eine beliebige Kombination von Authentifizierungs Optionen über Portal Site Einstellungen aktivieren oder deaktivieren.

> [!NOTE]
> Benutzer des Portals müssen über eine eindeutige e-Mail-Adresse verfügen. Wenn mindestens zwei Kontaktdaten Sätze (einschließlich der deaktivierten Kontaktdaten Sätze) dieselbe e-Mail-Adresse aufweisen, können sich die Kontakte nicht im Portal authentifizieren.

## <a name="account-sign-up-registration"></a>Kontoregistrierung (Registrierung)

Portal Administratoren haben mehrere Möglichkeiten, das Registrierungs Verhalten von Konten zu steuern. Open Registration ist die am wenigsten restriktive Registrierungs Konfiguration, bei der das Portal ermöglicht, dass ein Benutzerkonto durch einfaches Bereitstellen einer Benutzeridentität registriert wird. Alternative Konfigurationen erfordern möglicherweise, dass Benutzer einen Einladungscode oder eine gültige e-Mail-Adresse angeben, um sich beim Portal zu registrieren. Unabhängig von der Registrierungs Konfiguration sind sowohl lokale als auch externe Konten gleichmäßig Teil des Registrierungs Workflows. Das heißt, die Benutzer haben die Möglichkeit, die Art des Kontos auszuwählen, das Sie registrieren möchten.

## <a name="open-registration"></a>Registrierung öffnen

Während der Registrierung hat der Benutzer die Möglichkeit, ein lokales Konto (Benutzername und Kennwort) zu erstellen oder eine externe Identität aus einer Liste von Identitäts Anbietern auszuwählen. Wenn eine externe Identität ausgewählt ist, muss sich der Benutzer über den ausgewählten Identitäts Anbieter anmelden, um nachzuweisen, dass er das externe Konto besitzt. In beiden Fällen wird der Benutzer sofort registriert und über das Portal authentifiziert. Bei der Registrierung wird in der Common Data Service Umgebung ein neuer Kontaktdaten Satz erstellt.

Wenn die Open-Registrierung aktiviert ist, müssen Benutzer keinen Einladungscode bereitstellen, um den Registrierungsvorgang abzuschließen.

### <a name="see-also"></a>Siehe auch

[Festlegen der Authentifizierungs Identität für ein Portal](set-authentication-identity.md)  
