---
title: Exportieren einer Lösung für eine bestimmte Version  (Common Data Service for Apps) | Microsoft Docs
description: 'Hier erfahren Sie, wie Sie welche Dynamics 365-Version zielen und verwalten, für die Sie eine Lösung exportieren möchten.'
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
---
# <a name="export-a-solution-for-a-specific-version"></a>Exportieren einer Lösung für eine bestimmte Version

> [!NOTE]
>  In diesem Thema werden die Funktionen beschrieben, die für Nebenversionsupdates der Hauptversionen von Common Data Service für Apps verfügbar sind. Diese Funktion ist nicht für die Erstversion von CDS für Apps verfügbar, wird jedoch mit kleinen Versionsupdates verfügbar sein, die zusätzliche Funktionalität bieten.  

 In jeder neuen Version von CDs für Apps sind Funktionen enthalten, die in älteren Versionen fehlen. Lösungen, die neue Funktionen verwenden, können nicht in eine Organisation mit einer früheren Versionsnummer importiert werden. Aus einer Organisation mit einer früheren Version exportiere Lösungen können in Organisationen mit einer spätere Versionen importiert werden.  

 Nachdem Sie ein Upgrade der Organisation durchgeführt haben, die Sie verwenden, um Ihre Lösung zu definieren, können Sie eine Lösung in eine frühere Version exportieren. Wenn Sie eine frühere Zielversion auswählen, werden alle Lösungskomponenten, die von Funktionen abhängen, die seit der Zielversion eingeführt wurden, nicht in der exportierten Lösung enthalten sein.  

> [!NOTE]
>  Sie können keine frühere Version auswählen, wenn Sie die Standardlösung exportieren.  

<a name="BKMK_ExportSolutionForVersion"></a>   

## <a name="target-a-specific-version-when-you-export-a-solution"></a>Auswahl einer Zielversion beim Export einer Lösung  
 Wenn Sie eine Lösung aus CDS für Apps exportieren, haben Sie die Möglichkeit, die Lösung für eine bestimmte Dynamics 365 Version anzupassen. Die Version Dynamics 365 8.2.0.0 der Optionen sind 8.2 (Standard), 8.1 und 8.0. Wenn Sie 8.0 auswählen, werden keine der neuen Funktionen, die in 8.1.0.0 eingeführt wurden, in die exportierte Lösung integriert; alle Organisationen, die frühere Versionen von 8.1.0.0 verwenden, können diese Lösung installieren.  

 Wenn Sie Ihre Lösung exportieren, um sie in eine Vorversion zu importieren, kann der Exportdialog zwei mögliche Nachrichten anzeigen:  

 **Diese Lösung unterstützt die Dynamics 365-Version.**  
 Das bedeutet, dass die Lösungskomponenten in Ihrer Lösung von keiner Funktionalität oder von keinen Lösungskomponenten abhängen, die seit der Version eingeführt wurden.  

 **Die folgenden Komponenten werden entfernt oder als Teil des Exports bearbeitet.**  
 Unterhalb dieser Meldung wird eine Tabelle angezeigt, die alle Lösungskomponentenelemente aufführt, die geändert oder nicht in die exportierte Lösung integriert wurden.  

 Die Informationen, die im Dialog angezeigt werden, sind auch in der exportierten Lösungsdatei zu finden. Wenn Sie eine Lösung in eine bestimmte Zielversion exportieren, spezifiziert der Name der Datei die Ziellösung nach der folgenden Namenskonvention*Solution Name*<em>*Solution_Version_Number*_target_CRM\\</em>*Target Dynamics 365 Versionnummer*.zip.: Eine nicht verwalte Lösung mit dem Namen "Beispiellösung" und der Lösungsversionsnummer "2.0", die in die Zielversion "8.0" exportiert wird, hat z. B. den Namen SampleSolution_2_0_target_CRM_8.0.zip. Wenn Sie die Inhalte der komprimierten Datei extrahieren, finden Sie eine Datei filteredcomponents.xml, die ausführliche Daten zu den ausgeführten Aktionen enthält. Diese Datei können Sie mit Excel öffnen, um einen Bericht darüber anzuzeigen, welche Lösungskomponenten bearbeitet oder entfernt wurden.  

<a name="BKMK_Changes"></a>   

## <a name="what-changes-are-applied-to-a-solution-exported-for-an-earlier-version"></a>Welche Änderungen werden auf eine für eine Vorversion exportierte Lösung angewendet?  
 Seit den Versionen Dynamics 365 6.0.0.0 verfügt jeder Lösungskomponententyp über eine `IntroducedVersion`-Eigenschaft. Dieser Wert erfasst die aktuelle Versionsnummer der Lösung, der die Lösungskomponente bei ihrer Erstellung zugeordnet wurde. Alle Lösungskomponenten, die von Microsoft eingeführt werden, sind Teil einer ausgeblendeten Systemlösung, in der die Versionsnummer der CDS für Apps-Version entspricht.  

<!--
| IntroducedVersion Value |                                                             Solution components introduced                                                             |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
|         5.0.0.0         | Before [!INCLUDE[pn_crm_2013_shortest](../includes/pn-crm-2013-shortest.md)] and [!INCLUDE[pn_crm_online_fall13](../includes/pn-crm-online-fall13.md)] |
|         6.0.0.0         |    [!INCLUDE[pn_crm_2013_shortest](../includes/pn-crm-2013-shortest.md)] and [!INCLUDE[pn_crm_online_fall13](../includes/pn-crm-online-fall13.md)]     |
|         6.1.0.0         |     [!INCLUDE[pn_crm_2013_sp](../includes/pn-crm-2013-sp.md)] and [!INCLUDE[pn_v6_online_ur1_shortest](../includes/pn-v6-online-ur1-shortest.md)]      |
|         7.0.0.0         |                                  [!INCLUDE[pn_crm_2015_and_online_full](../includes/pn-crm-2015-and-online-full.md)]                                   |
|         7.1.0.0         |                                  [!INCLUDE[pn_crm_online_2015_update_1](../includes/pn-crm-online-2015-update-1.md)]                                   |
|         8.0.0.0         |               [!INCLUDE[pn_crm_online_2016_update_shortest](../includes/pn-crm-online-2016-update-shortest.md)] and CRM 2016 on-premises               |
|         8.1.0.0         |          [!INCLUDE[pn_crm_8_1_0_online](../includes/pn-crm-8-1-0-online.md)] and [!INCLUDE[pn_crm_8_1_0_op](../includes/pn-crm-8-1-0-op.md)]           |
|         8.2.0.0         |                                            [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)]                                             |
|         9.0.0.0         |                                          [!INCLUDE[pn_crm_9_0_0_online](../includes/pn-crm-9-0-0-online.md)]                                           |
-->

 Die `IntroducedVersion`-Daten müssen beim Export der Lösung mit der Zielversion übereinstimmen. Dies hat drei mögliche Aktionen zur Folge:  

 **Entfernen**  
 Lösungskomponenten, die nicht in der Zielversion vorhanden sind oder Abhängigkeiten von Komponenten enthalten, die nicht mit der Zielversion funktionieren, werden der Lösung nicht hinzugefügt.  

 **Ändern**  
 Wenn eine Lösungskomponente eine Abhängigkeit von einer anderen Lösungskomponente aufweist, die entfernt wird, wird die Lösungskomponente wenn möglich so geändert, dass die Abhängigkeit entfernt wird. Wenn beispielsweise eine Formulardefinition auf ein Attribut verweist, das in dieser Version nicht vorhanden war, wird das Formular so geändert, dass diese Referenz entfernt wird. Wenn die Lösungskomponente nicht geändert und die Abhängigkeit nicht entfernt kann, wird auch die Lösungskomponente entfernt.  

 **Ersetzen**  
 Wenn eine Lösungskomponente in der Zielversion vorhanden war, jedoch geändert wurde und eine Abhängigkeit von einer zu löschenden Lösungskomponente aufweist, wird diese Lösungskomponente unter Umständen durch die Definition der Lösungskomponente ersetzt, die für die Zielversion definiert wurde.  

<a name="BKMK_TargetVersion"></a>   

## <a name="select-a-target-version-programmatically"></a>Programmgesteuerte Auswahl einer Zielversion  

 Zum programmgesteuerten Export einer Lösung können Sie <xref:Microsoft.Crm.Sdk.Messages.ExportSolutionRequest> verwenden. Nach Dynamics 365 6.0.0.0 weist diese Message eine neue optionale <xref:Microsoft.Crm.Sdk.Messages.ExportSolutionRequest.TargetVersion>`String`-Eigenschaft auf, die Sie auf "8.0.0.0" setzen können, wenn Sie in die Vorversion exportieren möchten.  

### <a name="see-also"></a>Siehe auch  
 [Packen und Verteilen von Erweiterungen mithilfe von Lösungen](/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions)   
 [Erstellen, Exportieren oder Importieren einer nicht verwalteten Lösung](create-export-import-unmanaged-solution.md)   
 [Eine verwaltete Lösung erstellen, installieren und aktualisieren](create-install-update-managed-solution.md)   
 [Pflegen von verwalteten Lösungen](maintain-managed-solutions.md)   
 [Anleitung zur Anpassung: Verwendung von Lösungen für die Anpassungen](http://go.microsoft.com/fwlink/p/?LinkID=322003)
