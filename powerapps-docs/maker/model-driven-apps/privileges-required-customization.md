---
title: Zum Anpassen der modellgesteuerten App erforderliche Berechtigungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/18/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.assetid: 43cf7f3a-7e26-4990-8b5a-c817ac6d51bb
caps.latest.revision: 13
ms.author: matp
manager: kvivek
author: Mattp123
ms.openlocfilehash: dd0c7e05d756145a701bb6bfb137dc07cb8c45fb
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39684057"
---
# <a name="privileges-required-for-model-driven-app-customization"></a>Zum Anpassen der modellgesteuerten App erforderliche Berechtigungen | Microsoft-Dokumentation

App-Benutzer können das System personalisieren und sogar einige ihrer Anpassungen für andere Benutzer freigeben, aber nur Benutzer mit den richtigen Berechtigungen können Änderungen für alle Benutzer anwenden.  
  
> [!NOTE]
>  In diesem Abschnitt wird davon ausgegangen, dass Sie mit Sicherheitsrollen arbeiten können. Weitere Informationen zum Arbeiten mit Sicherheitsrollen finden Sie unter [Erstellen von Benutzern in Dynamics 365 (online) und Zuweisen von Sicherheitsrollen](https://docs.microsoft.com/dynamics365/customer-engagement/admin/create-users-assign-online-security-roles).  
  
<a name="BKMK_SysAdminAndSysCustomizer"></a>   
## <a name="system-administrator-and-system-customizer-security-roles"></a>Sicherheitsrollen Systemadministrator und Systemanpasser  
 Mit dem Konto jedes Benutzers, der Anpassungen vornimmt, müssen die Sicherheitsrollen Systemadministrator bzw. Systemanpasser verknüpft sein. Diese Sicherheitsrollen bieten Ihnen die Berechtigungen, die Sie benötigen, um die App anzupassen.  
  
|Systemadministrator|Systemanpasser|  
|--------------------------|-----------------------|  
|Verfügt über umfassende Berechtigungen zum Anpassen des Systems.|Verfügt über umfassende Berechtigungen zum Anpassen des Systems.|  
|Kann alle Daten im System abrufen.|Kann nur Datensätze zu selbsterstellten Systementitäten abrufen.|  
  
 Der Unterschied zwischen den Sicherheitsrollen Systemadministrator und Systemanpasser ist, dass ein Systemadministrator über Leseberechtigungen für die meisten Datensätze im System verfügt und alles anzeigen kann. Weisen Sie die Rolle Systemanpasser einer Person zu, die Aufgaben zur Anpassung durchführen muss, aber keine Daten in den Systementitäten sehen sollte. Allerdings ist das Testen ein wichtiger Teil der Systemanpassung. Wenn Systemanpasser Daten nicht sehen können, müssen sie Datensätze erstellen, um ihre Anpassungen zu testen. Standardmäßig haben Systemanpasser vollen Zugriff auf benutzerdefinierte Entitäten. Wenn Sie die gleichen Einschränkungen wünschen, die für Systementitäten vorhanden sind, müssen Sie die Sicherheitsrolle des Systemanpassers anpassen, sodass die Zugriffsebene für benutzerdefinierte Entitäten eher **Benutzer** statt **Organisation** ist.  
  
<a name="BKMK_DelegatingCustomizationTasks"></a>   
## <a name="delegate-customization-tasks"></a>Delegieren von Aufgaben zur Anpassung  
 Delegieren Sie einige Aufgaben an vertrauenswürdige Personen, sodass sie erforderliche Änderungen anwenden können. Denken Sie daran, dass mit den Konten aller Benutzer mehrere Sicherheitsrollen verknüpft sein können, und dass von Sicherheitsrollen gewährte Berechtigungen und Zugriffsrechte auf der *am wenigsten restriktiven* Ebene von Berechtigungen basieren.  
  
 Dies bedeutet, dass Sie die Sicherheitsrolle Systemanpasser jeder Person zuweisen können, die bereits eine andere Sicherheitsrolle hat, z.B. einem Vertriebsleiter. So kann die Person zusätzlich zu anderen, bereits vorhandenen Berechtigungen das System anpassen. Sie müssen deren vorhandene Sicherheitsrolle nicht bearbeiten und können die Sicherheitsrolle Systemanpasser vom Benutzerkonto der Person entfernen, wenn Sie möchten.  
  
<a name="BKMK_UsingTwoUserAccounts"></a>   
## <a name="test-customizations-without-customization-privileges"></a>Testen von Anpassungen ohne Anpassungsrechte  
 Sie sollten alle Anpassungen immer mit einem Benutzerkonto testen, das keine Anpassungsberechtigungen besitzt. Auf diese Weise können Sie sicherstellen, dass Personen ohne die Sicherheitsrollen Systemadministrator bzw. Systemanpasser in der Lage sind, Ihre Anpassungen zu verwenden. Um dies effektiv zu tun, benötigen Sie Zugriff auf zwei Benutzerkonten: ein Konto mit der Systemadministrator-Sicherheitsrolle und ein anderes, das über die Sicherheitsrollen verfügt, die die Personen darstellen, die die Anpassungen verwenden werden.  
  
> [!IMPORTANT]
>  Versuchen Sie nicht, Ihre Systemadministrator-Sicherheitsrolle zu entfernen, wenn Sie nur über ein einziges Benutzerkonto verfügen. Das System warnt Sie, wenn Sie dies versuchen, aber wenn Sie den Vorgang fortsetzen, kann es sein, dass der Weg zurück Ihnen versperrt ist. Die meisten Sicherheitsrollen lassen das Bearbeiten von Sicherheitsrollen eines Benutzers nicht zu.  
  
## <a name="next-steps"></a>Nächste Schritte  
 [Erste Schritte mit Anpassungen](getting-started-customization.md)

