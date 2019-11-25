---
title: Anpassen von Etiketten, um mehrere Sprachen zu unterstützen (Common Data Service) | Microsoft-Dokumentation
description: Infos zum Anpassen von Etiketten, um mehrere Sprachen zu unterstützen.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 759dcce9d209a904a1c8f0705414eccb88216e26
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2752998"
---
# <a name="customize-labels-to-support-multiple-languages"></a>Anpassen von Etiketten, um mehrere Sprachen zu unterstützen

Wenn Sie Anpassungen in Common Data Service erstellen, können Sie mehrere Sprachen unterstützen, indem Sie Etiketten verwenden.  

<a name="BKMK_UsingLabels"></a>   

## <a name="using-labels"></a>Verwenden von Etiketten  

|Microsoft.Xrm.Sdk.dll|Web-API|
|----------------|----------------|
|<xref:Microsoft.Xrm.Sdk.Label> Klasse|<xref href="Microsoft.Dynamics.CRM.Label?text=Label ComplexType" />|
|<xref:Microsoft.Xrm.Sdk.LocalizedLabel> Klasse|<xref href="Microsoft.Dynamics.CRM.LocalizedLabel?text=LocalizedLabel ComplexType" />|

 Etiketten sind lokalisierte Zeichenfolgen, die Benutzern in den Client-Anwendungen angezeigt werden. Sie werden implementiert durch Verwendung der `Label` (<xref href="Microsoft.Dynamics.CRM.Label?text=Label ComplexType" /> oder <xref:Microsoft.Xrm.Sdk.Label>-Klasse), die Sprachpakete unterstützt. Zeichenfolgen, die den Benutzern angezeigt werden, wie etwa Anzeigenamen von Entitäten oder Optionen in einem Optionssatz, können in mehreren Sprachen gespeichert werden. Benutzer können die Sprache auswählen, in der Formulare und Ansichten in Common Data Service angezeigt werden.  

 Die folgende Tabelle enthält alle Metadaten, die die `Label` verwenden.  

|Metadateneigenschaft|Beschreibung|  
|-----------------------|-----------------|  
|AttributeMetadata.Description|Beschreibung für ein Attribut.|  
|AttributeMetadata.DisplayName|Anzeigename für ein Attribut.|  
|EntityMetadata.Description|Beschreibung für eine Entität.|  
|EntityMetadata.DisplayCollectionName|Plural-Anzeigename für eine Entität.|  
|EntityMetadata.DisplayName|Anzeigename für eine Entität.|  
|AssociatedMenuConfiguration.Label|Etikett für eine Entität in einer Entitätsbeziehung.|  
|OptionMetadata.Label|Etikett für eine Option in einer Auswahlliste, einen Status oder ein Statusattribut.|  

 Die `Label` kann eine Zeichenfolge für jede installierte Sprache speichern. Dieses Array ist die `LocalizedLabels`-Eigenschaft. Es muss immer ein Etikett für die Basissprache gespeichert sein. Die Etiketten für die anderen Sprachen können **null** sein. Wenn der Benutzer die Benutzeroberfläche in einer Sprache anzeigen möchte und ein Etikett keine Zeichenfpölge für diese Sprache hat, wird das Etikett für die Basissprache verwendet.  

 Sie können die `UserLocalizedLabel`-Eigenschaft verwenden, um das Etikett für die von dem Benutzer ausgewählte Sprache abzurufen.  

<a name="BKMK_MessagesToWorkWithLabels"></a>   

## <a name="messages-to-use-with-labels"></a>Mit Etiketten zu verwendende Meldungen  
 In der folgenden Tabelle werden die Meldungen aufgeführt, mit denen Sie mit lokalisierten Etiketten arbeiten können, um mehrere Sprachen zu unterstützen. Beim Importieren von Übersetzungen können Sie einen Bericht auf der Grundlage des Importjobs wie beim Importieren einer Lösung generieren. Weitere Informationen finden Sie unter [Installieren oder Aktualisieren einer Lösung](work-solutions.md#BKMK_InstallUpgradeSolution).  


|                                                                                          Meldung                                                                                          |                                                    Web-API-Vorgang                                                     |                                SDK-Assembly                                |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------|
|                                               ExportTranslation</br>Exportiert alle Übersetzungen für eine bestimmte Lösung in eine komprimierte Datei.                                                |                  <xref href="Microsoft.Dynamics.CRM.ExportTranslation?text=ExportTranslation Action" />                  |         <xref:Microsoft.Crm.Sdk.Messages.ExportTranslationRequest>         |
|                                                          ImportTranslation</br>Importiert alle Übersetzungen aus einer komprimierten Datei.                                                           |                  <xref href="Microsoft.Dynamics.CRM.ImportTranslation?text=ImportTranslation Action" />                  |         <xref:Microsoft.Crm.Sdk.Messages.ImportTranslationRequest>         |
| RetrieveFormattedImportJobResults</br>Ruft die Ergebnisse eines ImportJob als XML-Dokument ab, das dafür entwickelt ist, mit Office Excel geöffnet zu werden. | <xref href="Microsoft.Dynamics.CRM.RetrieveFormattedImportJobResults?text=RetrieveFormattedImportJobResults Function" /> | <xref:Microsoft.Crm.Sdk.Messages.RetrieveFormattedImportJobResultsRequest> |
|                                                     RetrieveLocLabels</br>Ruft die lokalisierten Beschriftungen für das angegebene Attribut ab.                                                     |                 <xref href="Microsoft.Dynamics.CRM.RetrieveLocLabels?text=RetrieveLocLabels Function" />                 |         <xref:Microsoft.Crm.Sdk.Messages.RetrieveLocLabelsRequest>         |
|                                                          SetLocLabels</br>Legt die lokalisierten Beschriftungen für das angegebene Attribut ab.                                                          |                       <xref href="Microsoft.Dynamics.CRM.SetLocLabels?text=SetLocLabels Action" />                       |           <xref:Microsoft.Crm.Sdk.Messages.SetLocLabelsRequest>            |

<a name="BKMK_CustomizingLabelsInBaseLanguage."></a>
   
## <a name="customize-labels-in-the-base-language"></a>Anpassen von Etiketten in der Basissprache  
 Die Anpassungstools bieten Methoden zur Bearbeitung der Anzeigenamen von Entitäten, und Sie können diese Eigenschaften programmgesteuert anpassen. Sie können auch Entitätsmeldungen anpassen. Es wird aber nicht jede Meldung angezeigt. Eine weitere Methode, Text in der Anwendung zu suchen und anzupassen besteht darin, die Übersetzungen zu exportieren, die Werte für die Basissprache zu bearbeiten und die Übersetzungen wieder zu importieren. Obwohl dies nicht der eigentliche Verwendungszweck dieser Funktion ist, ist dies eine unterstützte Methode zur Identifizierung und Anpassung von in der Anwendung verwendetem Text. Weitere Informationen zu Meldungen für die [Nachrichten für eine Entität ändern](/dynamics365/customer-engagement/developer/modify-messages-entity).  

<a name="BKMK_TranslatingCustomizedEntityAndAttributeText"></a>   

## <a name="translate-customized-entity-and-attribute-text"></a>Übersetzen des angepassten Entitäts- und Attributtexts  
 Da Sie Anpassungen in der Anwendung nur unter Verwendung der Basissprache vornehmen können, gilt: Wenn Sie für diese Anpassungen lokalisierte Bezeichnungen und Anzeigezeichenfolgen zur Verfügung stellen möchten, müssen Sie den Text der Bezeichnungen exportieren, damit sie für andere Sprachen lokalisiert werden können, die für die Organisation aktiviert sind.  

### <a name="export-customized-text-for-translation"></a>Exportieren von angepasstem Text zur Übersetzung  
 Sie können Übersetzungen in die Webanwendung exportieren oder die `ExportTranslation`-Message (<xref href="Microsoft.Dynamics.CRM.ExportTranslation?text=ExportTranslation Action" /> oder <xref:Microsoft.Crm.Sdk.Messages.ExportTranslationRequest>-Klasse) verwenden.  

 Der exportierte Text wird als komprimierte Datei gespeichert, die ein CrmTranslations.xml enthält, das Sie mit Office Excel öffnen können. Sie können diese Datei an einen Sprachexperten, an eine Übersetzungsagentur oder an ein Lokalisierungsunternehmen senden.  

 Weitere Informationen finden Sie in den [Office 2003-XML-Referenzschemata](https://www.microsoft.com/downloads/details.aspx?FamilyID=fe118952-3547-420a-a412-00a2662442d9).  

### <a name="import-translated-text"></a>Importieren von übersetztem Text  
 Wenn Sie den angepassten Text für Entitäten oder Attribute exportiert und anschließend übersetzt haben, können Sie die übersetzten Textzeichenfolgen mit der `ImportTranslation`-Nachricht (<xref href="Microsoft.Dynamics.CRM.ImportTranslation?text=ImportTranslation Action" /> oder <xref:Microsoft.Crm.Sdk.Messages.ImportTranslationRequest>-Klasse) in die Webanwendung importieren. Die Datei, die Sie importieren, muss eine komprimierte Datei sein, in der die CrmTranslations.xml und die [Content_Types].xml Datei im Stammverzeichnis enthalten ist, genauso wie sie exportiert wurden.  

 Nach dem Importieren der fertig gestellten Übersetzungen wird benutzerdefinierter Text für Benutzer angezeigt, die in den Sprachen arbeiten, in die der Text übersetzt wurde.  

> [!NOTE]
> In Common Data Service kann übersetzter Text mit mehr als 500 Zeichen nicht importiert werden. Wenn Elemente in Ihrer Übersetzung eine Länge von 500 Zeichen überschreiten, tritt beim Importvorgang ein Fehler auf. Überprüfen Sie bei Auftreten eines Importfehlers die Zeile in der Datei, durch die der Fehler verursacht wurde, verringern Sie die Zeichenanzahl, und führen Sie einen erneuten Importvorgang aus.  

 Da die Anpassung nur in der Ausgangssprache unterstützt wird, können Sie Common Data Service so verwenden, dass die Ausgangssprache auf Ihre Spracheinstellung festgelegt ist. Wenn Sie überprüfen möchten, ob der übersetzte Text angezeigt wird, muss die Spracheinstellung für die Benutzeroberfläche von Common Data Service geändert werden. Zum Ausführen weiterer Anpassungen muss die Spracheinstellung dann wieder auf die Ausgangssprache festgelegt werden.  

<a name="BKMK_ManagingLanguages"></a>   

## <a name="manage-languages-for-your-organization"></a>Verwalten von Sprachen für Ihre Organisation  
 Mit Common Data Service wird es Ihnen ermöglicht, mehrere Sprachpakete auf einem Server zu speichern und Benutzern die Auswahl von Sprachpaketen zu ermöglichen. Informationen zum Installieren der Language Packs finden Sie in unter [Aktivieren von Sprachen](/dynamics365/customer-engagement/admin/enable-languages). Dieser Abschnitt enthält Informationen zu den Meldungen, mit denen die für Ihre Organisation installierten Sprachpakete verwaltet werden.  

 Die folgende Tabelle enthält die Meldungen, die Sie für die Arbeit mit Sprachpaketen verwenden. Verwenden Sie diese Meldungen mit der <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*>-Methode. Methode.  

|Meldung|Web-API-Vorgang|SDK-Assembly|  
|-------------|-----------------|----------------|  
|DeprovisionLanguage</br>Enthält die Daten, die nötig sind, um die Bereitstellung einer Sprache aufzuheben.|<xref href="Microsoft.Dynamics.CRM.DeprovisionLanguage?text=DeprovisionLanguage Action" />|<xref:Microsoft.Crm.Sdk.Messages.DeprovisionLanguageRequest>|  
|ProvisionLanguage</br>Enthält die Daten, die nötig sind, um eine Sprache bereitzustellen.|<xref href="Microsoft.Dynamics.CRM.ProvisionLanguage?text=ProvisionLanguage Action" />|<xref:Microsoft.Crm.Sdk.Messages.ProvisionLanguageRequest>|  
|RetrieveAvailableLanguages</br>Ruft die Liste der verfügbaren Sprachen ab.|<xref href="Microsoft.Dynamics.CRM.RetrieveAvailableLanguages?text=RetrieveAvailableLanguages Function" />|<xref:Microsoft.Crm.Sdk.Messages.RetrieveAvailableLanguagesRequest>|  
|RetrieveDeprovisionedLanguages</br>Ruft die Liste der auf dem Server installierten Sprachpakete ab, die deaktiviert wurden.|<xref href="Microsoft.Dynamics.CRM.RetrieveDeprovisionedLanguages?text=RetrieveDeprovisionedLanguages Function" />|<xref:Microsoft.Crm.Sdk.Messages.RetrieveDeprovisionedLanguagesRequest>|  
|RetrieveInstalledLanguagePacks</br>Enthält die Daten, die benötigt werden, um die Liste der auf dem Server installierten Sprachpakete abzurufen.|<xref href="Microsoft.Dynamics.CRM.RetrieveInstalledLanguagePacks?text=RetrieveInstalledLanguagePacks Function" />|<xref:Microsoft.Crm.Sdk.Messages.RetrieveInstalledLanguagePacksRequest>|  
|RetrieveInstalledLanguagePackVersion</br>Enthält die Daten, die benötigt werden, um die Version eines installierten Sprachpakets abzurufen.|<xref href="Microsoft.Dynamics.CRM.RetrieveInstalledLanguagePacks?text=RetrieveLicenseInfo Function" />|<xref:Microsoft.Crm.Sdk.Messages.RetrieveInstalledLanguagePackVersionRequest>|  
|RetrieveProvisionedLanguages</br>Ruft die Liste der auf dem Server installierten Sprachpakete ab, die aktiviert sind.|<xref href="Microsoft.Dynamics.CRM.RetrieveProvisionedLanguages?text=RetrieveProvisionedLanguages Function" />|<xref:Microsoft.Crm.Sdk.Messages.RetrieveProvisionedLanguagesRequest>|  
|RetrieveProvisionedLanguagePackVersion</br>Ruft die Version der auf dem Server installierten Sprachpakete ab.|<xref href="Microsoft.Dynamics.CRM.RetrieveProvisionedLanguagePackVersion?text=RetrieveProvisionedLanguagePackVersion Function" />|<xref:Microsoft.Crm.Sdk.Messages.RetrieveProvisionedLanguagePackVersionRequest>|  

### <a name="see-also"></a>Siehe auch  
 [Erweitern Sie das Metadatenmodell für Dynamics 365](/dynamics365/customer-engagement/developer/org-service/use-organization-service-metadata)   
 [Anpassen von Dynamics 365](/dynamics365/customer-engagement/developer/customize-dev/customize-applications)   
 [Ändern der Meldungen für eine Entität](/dynamics365/customer-engagement/developer/modify-messages-entity)     
 <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata>   
 <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>    
 <xref:Microsoft.Xrm.Sdk.Metadata.OptionMetadata> 
