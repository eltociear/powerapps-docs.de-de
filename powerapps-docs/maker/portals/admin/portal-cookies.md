---
title: Cookies in Power Apps-Portalen | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Cookies, die Power Apps-Portale verwenden.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 03/10/2020
ms.author: nenandw
ms.reviewer: tapanm
ms.openlocfilehash: 13730a4faa284890136cc04d2f56ff50c46d42e2
ms.sourcegitcommit: cf492063eca27fdf73459ff2f9134f2ca04ee766
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "3136651"
---
# <a name="cookies-in-power-apps-portals"></a>Cookies in Power Apps-Portalen

Ein Cookie ist eine kleine Datei, die vom Browser von der Website an das Gerät des Besuchers gesendet wird. Eine einzelne Websitzung kann mehrere Cookies verwenden.

Power Apps-Portale verwenden Cookies auch, um Informationen für verschiedene Zwecke zu speichern. Der folgende Abschnitt enthält und beschreibt die Cookies, die Power Apps-Portale verwenden:

## <a name="names-and-descriptions-of-cookies-used-by-portals"></a>Namen und Beschreibungen von Cookies, die von Portalen verwendet werden

#### <a name="arraffinity"></a>ARRAffinity

Wird automatisch von Azure-Websites hinzugefügt und stellt sicher, dass Anforderungen zwischen verschiedenen Websites lastenausgeglichen sind. Speichert keine Benutzerinformationen.

####  <a name="aspnet-session-id"></a>ASP.Net Session Id

Wird verwendet, um die Sitzung eines angemeldeten Benutzers aufrechtzuerhalten, um eine wiederholte Anmeldung zu vermeiden. Das Cookie ist nicht dauerhaft und wird nach Abschluss der Sitzung gelöscht.

#### <a name="dynamics-365-portal-analytics"></a>Dynamics 365 Portal Analytics

Kritisches Service-Cookie zur anonymen Analyse der Servicenutzung und zu statistischen Zwecken aggregiert.

#### <a name="contextlanguagecode"></a>ContextLanguageCode

Speichert die Standardsprache des Benutzers, der auf das Portal zugreift, innerhalb einer Sitzung und über Webseiten hinweg. Das Cookie wird nach Abschluss der Sitzung gelöscht.

#### <a name="aspnetapplicationcookie"></a>.AspNet.ApplicationCookie

Wird verwendet, um Benutzersitzungen zu identifizieren. Eine Benutzersitzung beginnt, wenn ein Benutzer das Portal zum ersten Mal durchsucht. Und endet, wenn die Sitzung geschlossen wird. [Einstellungen der Authentifizierungssite](https://docs.microsoft.com/powerapps/maker/portals/configure/set-authentication-identity) kann verwendet werden, um die Ablaufdauer der Sitzung zu ändern.

#### <a name="__requestverificationtoken"></a>__RequestVerificationToken 

Wird vom [antiforgery](https://docs.microsoft.com/dotnet/api/system.web.helpers.antiforgeryconfig.cookiename)-System verwendet.

#### <a name="adxpreviewunpublishedentities"></a>adxPreviewUnpublishedEntities

Enthält den **EIN/AUS**-Vorschaumodus, der im klassischen CMS-System für Portaladministratoren verwendet wird.

#### <a name="adx-notification"></a>adx-notification

Wird in Entitätsformularaktionen zum Speichern von Warnmeldungen verwendet, die bei der Umleitung angezeigt werden sollen.

#### <a name="timezonecode"></a>timezoneCode

Enthält den Feldwert *Zeitzonencode* der Entität *CRM-Zeitzonendefinition* für die aktuelle Zeitzone.

#### <a name="timezoneoffset"></a>timezoneoffset

Enthält die [Zeitzonendifferenz](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Date/getTimezoneOffset) zwischen UTC und lokaler Browserzeit.

#### <a name="isdstsupport"></a>isDSTSupport

Gibt an, ob ein bestimmtes Datum und eine bestimmte Uhrzeit in den Bereich der Sommerzeit fallen.

#### <a name="isdstobserved"></a>iisDSTObserved

Speichert einen Wert, der angibt, ob der aktuelle Moment in der Sommerzeit liegt.

### <a name="see-also"></a>Siehe auch

[Cookie-Authentifizierungswebsiteeinstellungen](https://docs.microsoft.com/powerapps/maker/portals/configure/set-authentication-identity#cookie-authentication-site-settings)

