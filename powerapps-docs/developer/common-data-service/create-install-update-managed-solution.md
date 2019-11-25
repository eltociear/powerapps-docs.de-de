---
title: Erstellen, Installieren und Aktualisieren einer verwalteten Lösung (Common Data Service) | Microsoft-Dokumentation
description: <Description>
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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
ms.openlocfilehash: 9c9fe500fc2f3a7991b09c346b4fd931f8802160
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748426"
---
# <a name="create-install-and-update-a-managed-solution"></a>Eine verwaltete Lösung erstellen, installieren und aktualisieren

Erstellen Sie eine verwaltete Lösung, indem Sie eine nicht verwaltete Lösung als verwaltete Lösung exportieren. Organisationen, die die verwaltete Lösung verwenden, werden sie installieren und alle Updates dafür, die Sie erstellen.  
  
 Weitere Informationen: [Verwendung von Lösungen für die Anpassungen](/dynamics365/customer-engagement/customize/use-solutions-for-your-customizations).  
  
<a name="BKMK_CreateManagedSolution"></a>   

## <a name="create-a-managed-solution"></a>Erstellen einer verwalteten Lösung  
 Vor dem Erstellen einer verwalteten Lösung müssen Sie zuerst eine nicht verwalte Lösung erstellen. Weitere Informationen zum Erstellen einer nicht verwalteten Lösung finden Sie unter [So erstellen Sie eine nicht verwaltete Lösung](create-export-import-unmanaged-solution.md#BKMK_CreateUnmanagedSolution)  
  
 Erstellen Sie eine verwaltete Lösung, indem Sie die Option **Verwaltet** im Dialogfeld **Pakettyp** auswählen, wenn Sie die Lösung exportieren.  
  
 Eine verwaltete Lösung enthält nur alle anpassbaren Lösungskomponenten, die angepasst wurden. Dies verhindert nicht nur, dass unbeabsichtigt Lösungskomponenten auf dem System, wo die Lösung installiert ist, gelöscht werden, sondern es sorgt auch dafür, dass die Größe der nicht verwalteten Lösungen geringer bleibt.  
  
 Vor dem letzten Schritt zum Erstellen einer verwalteten Lösung, müssen Sie entscheiden, ob es Anpassungsmöglichkeiten gibt, die Sie Benutzern nicht freigeben möchten, die Ihre verwaltete Lösung installieren. Jede Lösungskomponente enthält eine Reihe von verwalteten Eigenschaften, die steuern, welche der Anpassungsmöglichkeiten Sie zulassen möchten. Die Standardeinstellungen erlauben alle Anpassungsmöglichkeiten. Weitere Informationen: [Verwaltete Eigenschaften verwenden](use-managed-properties.md)  
  
 Sie können eine programmgesteuerte verwaltete Lösung erstellen, indem Sie die <xref:Microsoft.Crm.Sdk.Messages.ExportSolutionRequest> Nachricht verwenden. Weitere Informationen: [Exportieren oder Packen einer Lösung](work-solutions.md#BKMK_ExportPackageSolution)  
  
> [!IMPORTANT]
>  Wenn Sie eine verwaltete Lösung erstellen, können Sie sie nicht wieder in die Organisation importieren, die Sie für die Erstellung verwendet haben.  
  
<a name="BKMK_InstallManagedSolution"></a>   

## <a name="install-a-managed-solution"></a>Installieren der verwalteten Lösung  
 Sie können eine verwaltete Lösung gleich installieren wie wenn Sie eine nicht verwaltete Lösung importieren. Der Unterschied besteht darin, wie die Lösung gepackt wurde.  
  
> [!IMPORTANT]
>  Das Installieren einer Lösung oder Veröffentlichen von Anpassungen kann den normalen Systembetrieb stören. Es ist empfehlenswert, den Import von Lösungsimporte einzuplanen, wenn er für die Benutzer am wenigsten Unterbrechungen mit sich bringt.  
  
 Wenn die Lösung nicht erfolgreich importiert wurde, können Sie im Dialogfeld auf **Download-Protokoll** klicken, um einen Bericht aufzurufen, der Formationen zum Fehler enthält und der verhinderte, dass die verwaltete Lösung erfolgreiche importiert werden konnte. Diese Datei ist ein XML-Dokument und so konfiguriert, dass es mithilfe von Office Excel geöffnet werden kann.  
  
 Sie können eine programmgesteuerte verwaltete Lösung importieren oder aktualisieren, indem Sie die <xref:Microsoft.Crm.Sdk.Messages.ImportSolutionRequest> Nachricht verwenden. Wenn Sie diese Meldung verwenden, können Sie ein Verweis auf einen Entitätsdatensatz `ImportJob` anfordern, der Details über den Erfolg des Imports enthält. Weitere Informationen: [Installieren oder Aktualisieren einer Lösung](work-solutions.md#BKMK_InstallUpgradeSolution).  
  
 <xref:Microsoft.Crm.Sdk.Messages.ImportSolutionRequest> kann mithilfe von <xref:Microsoft.Xrm.Sdk.Messages.ExecuteAsyncRequest> aufgerufen werden. Weitere Informationen: [Nachrichten im Hintergrund (asynchron) ausführen](/dynamics365/customer-engagement/developer/org-service/use-messages-request-response-classes-execute-method#bkmk_executeasync)  
  
 Es gibt Größenbeschränkungen für Lösungen, die Sie installieren können. Weitere Informationen: [Maximal zulässige Größe der zu importierenden Lösung](create-export-import-unmanaged-solution.md#BKMK_MaxSizeOfSolution)  
  
<a name="BKMK_UpdateManagedSolution"></a>   

### <a name="update-a-managed-solution"></a>Eine verwaltete Lösung aktualisieren  
 Wenn Sie eine verwaltete Lösung installieren, die in der Organisation vorhanden ist, bietet das Importlösungsdialogfeld folgende Möglichkeiten:  
  
 **Anpassungen warten (empfohlen)**  
 Mit der Auswahl dieser Option werden alle unverwalteten Anpassungen gewartet, die auf Komponenten ausgeführt wurden. Allerdings werden nicht alle Updates in dieser Lösung angewendet.  
  
 **Anpassungen überschreiben**  
 Diese Option überschreibt nicht verwaltete Anpassungen, die zuvor für Komponenten in dieser Lösung vorgenommen wurden. Alle in dieser Lösung enthaltenen Aktualisierungen werden wirksam.  
  
> [!NOTE]
>  Sie sollten Personen, die Ihre verwaltete Lösung installieren, bitten, die Option **Anpassungen überschreiben** zu verwenden, wenn sie Probleme suchen, die einen Anpassungskonflikt mit dem Verhalten Ihrer Lösung verursachen. Sie sollten immer Ihre nicht verwalteten Lösungen zuerst exportieren, damit sie erneut gesendet werden können, wenn dies erforderlich ist.  
  
### <a name="see-also"></a>Siehe auch  
 [Packen und Verteilen von Erweiterungen mithilfe von Dynamics 365-Lösungen](/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions)   
 [Einführung zu Lösungen](introduction-solutions.md)   
 [Planen für Lösungsentwicklung](/dynamics365/customer-engagement/developer/plan-solution-development)   
 [Lösungskomponenten und Abhängigkeitsnachverfolgung](dependency-tracking-solution-components.md)   
 [Erstellen, Exportieren oder Importieren einer nicht verwalteten Lösung](create-export-import-unmanaged-solution.md)   
 [Deinstallieren oder Löschen einer Lösung](uninstall-delete-solution.md)   
 [Anpassungslösungsdateischema](/dynamics365/customer-engagement/developer/customize-dev/customization-solutions-file-schema)