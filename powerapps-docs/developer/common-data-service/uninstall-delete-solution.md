---
title: Eine Lösung deinstallieren oder löschen (Common Data Service) | Microsoft-Dokumentation
description: Dieses Dokument enthält Beschreibungen zum Deinstallieren und Löschen für verwaltete und nicht verwaltete Lösung in Dynamics 365.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 37dd257acaa114ebd6c608b2bed3947d74f15921
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155226"
---
# <a name="uninstall-or-delete-a-solution"></a>Deinstallieren oder Löschen einer Lösung

Sie löschen verwaltete und nicht verwaltete Lösungen auf die gleiche Weise, aber die resultierenden Aktionen sind sehr verscheiden. Durch das Löschen einer verwalteten Lösung wird die verwaltete Lösung deinstalliert.  
  
<a name="BKMK_DeleteSolution"></a>   
## <a name="delete-a-solution"></a>Löschen einer Lösung  
 Abhängig vom Typ der Lösung, die Sie löschen möchten, wird eine der folgenden **Löschen bestätigen**-Meldungen angezeigt:  
  
 **Verwaltete Lösung**  
 "Sie löschen eine verwaltete Lösung. Die Lösung und alle ihre Komponenten werden gelöscht. Diese Aktion kann nicht rückgängig gemacht werden. Es kann einige Minuten dauern, bis diese Lösung deinstalliert wird. Sie können die Deinstallation nicht abbrechen, nachdem sie gestartet wurde. Möchten Sie den Vorgang fortsetzen?"  
  
 **Nicht verwaltete Lösungen**  
 "Sie löschen eine nicht-verwaltete Lösung. Die Lösung wird gelöscht, jedoch werden Komponenten, die in dieser Lösung enthalten sind, nicht gelöscht. Diese Aktion kann nicht rückgängig gemacht werden. Möchten Sie den Vorgang fortsetzen?"  
  
 Zum programmgesteuerten Löschen einer Lösung verwenden Sie die <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Delete*> Methode. Weitere Informationen: [Löschen einer Lösung](work-solutions.md#BKMK_DeleteSolution)  
  
<a name="BKMK_UinstallAManagedSolution"></a>   
### <a name="uninstall-a-managed-solution"></a>Deinstallieren einer verwalteten Lösung  
 Durch das Löschen einer verwalteten Lösung wird die Lösung deinstalliert. Alle Lösungskomponenten, die darin definiert sind, werden gelöscht.  
  
> [!IMPORTANT]
>  Wenn Sie eine verwaltete Lösung deinstallieren, gehen die folgenden Daten verloren: in benutzerdefinierten Entitäten gespeicherte Daten, die Teil der Lösung sind sowie die Daten, die in benutzerdefinierten Attributen in Systementitäten gespeichert werden, die Teil der Lösung sind.  
  
<a name="BKMK_DeleteUnmanagedSolution"></a>   
### <a name="delete-an-unmanaged-solution"></a>Löschen einer nicht verwalteten Lösung  
 Eine nicht verwaltete Lösung ist eine Gruppe von Lösungskomponenten. Durch Löschen der Lösung wird ein einzelner Lösungsdatensatz in der Datenbank gelöscht. Lösungskomponenten werden durch das Löschen der Lösung nicht betroffen, sie bleiben im System.  
  
<a name="BKMK_AccessSolutionsGridWithUrl"></a>   
## <a name="access-the-solutions-list-with-a-url"></a>Zugreifen auf die Lösungsliste mit einer URL  
 Wenn Sie direkt zur Lösungsliste navigieren möchten, können Sie die folgende URL verwenden:  
  
```http
<organization root url>/tools/Solution/home_solution.aspx?etn=solution  
```  
  
### <a name="see-also"></a>Siehe auch  
 [Packen und Bereitstellen von Erweiterungen](/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions)   
 [Löschen einer Lösung](work-solutions.md#BKMK_DeleteSolution)   
 [Einführung zu Lösungen](introduction-solutions.md)   
 [Planen für Lösungsentwicklung](/dynamics365/customer-engagement/developer/plan-solution-development)   
 [Lösungskomponenten und Abhängigkeitsnachverfolgung](dependency-tracking-solution-components.md)   
 [Erstellen einer verwalteten Lösung](create-install-update-managed-solution.md#BKMK_CreateManagedSolution)   
 [Exportieren einer nicht verwalteten Lösung](create-export-import-unmanaged-solution.md#BKMK_UnmanagedSolution)   
 [Importieren einer nicht verwalteten Lösung](create-export-import-unmanaged-solution.md#BKMK_ImportUnmanagedSolution)   
 [Erstellen einer verwalteten Lösung](create-install-update-managed-solution.md#BKMK_CreateManagedSolution)   
 [Erstellen von Lösungen, die mehrere Sprachen unterstützen](create-solutions-support-multiple-languages.md)   
 [Installieren der verwalteten Lösung](create-install-update-managed-solution.md#BKMK_InstallManagedSolution)
