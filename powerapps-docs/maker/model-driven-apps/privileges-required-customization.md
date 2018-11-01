---
title: Benötigte Berechtigungen für modellgesteuerte App-Anpassungen | MicrosoftDocs
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
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="privileges-required-for-model-driven-app-customization"></a>Benötigte Berechtigungen für modellgesteuerte App-Anpassungen

App Benutzer können das System personalisieren und sogar einige ihrer Anpassungen für andere Benutzer freigeben, aber nur Benutzer mit entsprechenden Berechtigungen können Änderungen für alle -Benutzer anwenden.  
  
> [!NOTE]
>  In diesem Abschnitt wird davon ausgegangen, dass Sie die Arbeit mit Sicherheitsrollen kennen. Weitere Informationen zum Verwenden von Sicherheitsrollen finden Sie unter [Erstellen von Benutzern und Zuweisen von Sicherheitsrollen](https://docs.microsoft.com/dynamics365/customer-engagement/admin/create-users-assign-online-security-roles).  
  
<a name="BKMK_SysAdminAndSysCustomizer"></a>   
## <a name="system-administrator-and-system-customizer-security-roles"></a>Sicherheitsrollen: Systemadministrator und Systemanpasser  
 Fast jeder, der  anpasst, verfügt über die Sicherheitsrolle "Systemadministrator" oder "Systemanpasser", die ihm über das Konto zugeordnet wurde. Diese Berechtigungen ermöglichen Ihnen, Ihre App-Bereitstellung anzupassen.  
  
|Systemadministrator|Systemanpasser|  
|--------------------------|-----------------------|  
|Hat volle Rechte zum Anpassen des Systems|Hat volle Rechte zum Anpassen des Systems|  
|Kann alle Daten im System anzeigen|Kann nur Datensätze für Systementitäten anzeigen, die sie erstellen|  
  
 Die Unterschied zwischen den Sicherheitsrollen "Systemadministrator" und "Systemanpasser" besteht darin, dass ein Systemadministrator über Leseberechtigungen für die meisten Datensätze im System verfügt und alles anzeigen kann. Weisen Sie die Systemanpasserrolle einem Benutzer zu, der Anpassungsaufgaben durchführen muss, die Daten in den Systementitäten jedoch nicht sehen soll. Tests sind jedoch ein wichtiger Bestandteil des Anpassens des Systems. Wenn Systemanpasser keine Daten anzeigen können, müssen Sie Datensätze erstellen, um ihre Anpassungen zu testen. Standardmäßig haben Systemanpasser vollständigen Zugriff auf die benutzerdefinierten Entitäten. Falls Sie dieselben Einschränkungen wünschen, die für Systementitäten vorhanden sind, müssen Sie die Systemanpasser-Sicherheitsrolle so anpassen, dass die Zugriffsebene **Benutzer** und nicht **Organisation** für benutzerdefinierte Entitäten ist.  
  
<a name="BKMK_DelegatingCustomizationTasks"></a>   
## <a name="delegate-customization-tasks"></a>Delegieren von Anpassungsaufgaben  
 Möglicherweise sollten Sie einige Aufgaben an vertrauenswürdige Benutzer delegieren, damit diese die benötigten Anpassungen vornehmen können. Beachten Sie, dass Benutzer mehrere Sicherheitsrollen in ihrem Benutzerkonto haben können, und dass die Rechte und Zugriffsrechte, die durch die Sicherheitsrollen erteilt werden, auf der *am wenigsten einschränkenden* Berechtigungsstufe basieren.  
  
 Das bedeutet, dass Sie die Systemanpasser-Sicherheitsrolle jemanden zuweisen können, der bereits eine andere Sicherheitsrolle hat, beispielsweise einem Vertriebsmanager. Damit können sie neben anderen Berechtigungen auch das System anpassen. Sie müssen die bereits vorhandene Sicherheitsrolle nicht bearbeiten, und Sie können die Sicherheitsrolle "Systemanpasser" jederzeit aus dem Konto des Benutzers entfernen.  
  
<a name="BKMK_UsingTwoUserAccounts"></a>   
## <a name="test-customizations-without-customization-privileges"></a>Testen von Anpassungen ohne Anpassungsberechtigungen  
 Sie sollten alle Anpassungen, die Sie vornehmen, mit einem Benutzerkonto testen, dass keine Anpassungsrechte besitzt. Dadurch können Sie sicherstellen, dass Benutzer ohne die Sicherheitsrolle "Systemadministrator" oder "Systemanpasser" ihre Anpassungen verwenden können. Um dies in effektiver Weise zu tun, müssen Sie auf zwei Benutzerkonten zugreifen können: Eines mit der Sicherheitsrolle Systemadministrator und eines mit den Sicherheitsrollen der Benutzer, die die Anpassungen verwenden sollen.  
  
> [!IMPORTANT]
>  Versuchen Sie nicht, Ihre Systemadministratorsicherheitsrolle zu entfernen, wenn Sie nur ein Benutzerkonto haben. Das System warnt Sie, wenn Sie dies versuchen, wenn Sie jedoch fortfahren, kann es sein, das Sie nicht mehr zurückgehen können. Die meisten Sicherheitsrollen ermöglichen nicht die Bearbeitung der Sicherheitsrollen eines Benutzers.  
  
## <a name="next-steps"></a>Nächste Schritte  
[Grundlegendes zu Komponenten modellgestützter Apps](model-driven-app-components.md)

