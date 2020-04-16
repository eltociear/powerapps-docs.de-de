---
title: Verhalten spezialisierter Update-Vorgänge (Common Data Service) | Microsoft-Dokumentation
description: Beschreibt ein spezielles Verhalten in Plug-Ins und in Workflows für Update-Ereignisse aufgrund veralteter Nachrichten.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 97f9c0a917504400170d00cf7764cfeace2cc8a6
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155286"
---
# <a name="behavior-of-specialized-update-operations"></a>Verhalten spezialisierter Update-Vorgänge

Es gibt mehrere veraltete spezialisierte Nachrichten, die Aktualisierungsvorgänge ausführen. In früheren Versionen wurde es erforderlich, um die Nachrichten zu verwenden, aber jetzt können dieselben Vorgänge mithilfe von <xref:Microsoft.Xrm.Sdk.IOrganizationService> <xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*> ausgeführt werden. oder <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> Klasse  mit<xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*>

[!INCLUDE [cc-legacy-update-messages](includes/cc-legacy-update-messages.md)]

Weitere Informationen: [Veraltete Update-Nachrichten](org-service/entity-operations-update-delete.md#legacy-update-messages) 

Diese Änderung führte ein spezielles Verhalten ein, das für Plug-Ins und Workflows beachtet werden soll. 

## <a name="for-plug-ins"></a>Für Plug-Ins

Wenn Updateanforderungen verarbeitet werden, die beide Besitzerfelder sowie andere Standardfelder für Entitäten im Besitz von Unternehmenseinheiten enthalten, werden Plug-Ins, die für die **Update**-Nachricht in den Phasen **PreOperation** und/oder **PostOperation** registriert sind, einmal für alle Nicht-Besitzerfelder und dann einmal für die Besitzerfelder ausgeführt. Beispiele für Besitzerfelder sind `businessunit` und `manager` (für eine [SystemUser-Entität](reference/entities/systemuser.md)). Beispiele von Unternehmen im Besitz von Entitäten umfassen [SystemUser](reference/entities/systemuser.md), [BusinessUnit](reference/entities/businessunit.md)[Equipment](/dynamics365/customer-engagement/developer/entities/equipment) und [Team](reference/entities/team.md).

Wenn Updateanforderungen verarbeitet werden, die Zustand-/Statusfelder sowie andere Standardfelder enthalten, werden Plug-Ins, die für die **Update**-Nachricht in den Phasen **PreOperation** und/oder **PostOperation** registriert sind, einmal für alle Nicht-Zustand-/Statusfelder und dann einmal für die Zustand-/Statusfelder ausgeführt.

Damit Plug-In-Code die gesamten Datenänderungen des Updates erhält, müssen Sie das Plug-In in der Phase **PreOperation** registrieren und die relevanten Informationen in <xref:Microsoft.Xrm.Sdk.IExecutionContext.SharedVariables> im Plug-In-Kontext speichern, damit spätere Plug-Ins (in der Pipeline) sie nutzen können.

## <a name="for-workflows"></a>Für Workflows

Wenn Updateanforderungen verarbeitet werden, die beide Besitzerfelder sowie andere Standardfelder enthalten, werden Workflows, die für die **Update**-Nachricht registriert sind, einmal für alle Nicht-Besitzerfelder und dann einmal für die Besitzerfelder ausgeführt. Die Workflows, die von Benutzern für die **Assign**-Nachricht registriert werden, werden weiterhin durch Updates von Besitzerfeldern gestartet.

Wenn Updateanforderungen verarbeitet werden, die beide Statusfelder sowie andere Standardfelder enthalten, werden Workflows, die für die **Update**-Nachricht registriert sind, einmal für alle Nicht-Statusfelder und dann einmal für die Statusfelder ausgeführt. Die Workflows, die für den Schritt **Status ändern** registriert werden, werden weiterhin über Updates an Statusfeldern gestartet.

### <a name="see-also"></a>Siehe auch

[Aktualisieren und Löschen von Entitäten mit dem Organisationsservice](org-service/entity-operations-update-delete.md)<br />
[Ereignisframework](event-framework.md)