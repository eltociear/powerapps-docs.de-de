---
title: Erstellen von Lösungen, die mehrere Sprachen unterstützen (Common Data Service) | Microsoft-Dokumentation
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
ms.openlocfilehash: 2eef717e694013295adba3946b2f3f7bc3e888c7
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753010"
---
# <a name="create-solutions-that-support-multiple-languages"></a>Erstellen von Lösungen, die mehrere Sprachen unterstützen

Common Data Service unterstützt mehrere Sprachen. Wenn Sie die Lösung für Organisationen installieren möchten, die verschiedene Ausgangssprachen enthalten oder die mehrere Sprachen bereitstellen, berücksichtigen Sie diese Option, wenn Sie Ihre Lösung planen. Die folgende Tabelle enthält Taktiken für die Verwendung mit Lösungskomponenten, um sie in einer Lösung einzuschließen, die mehrere Sprachen unterstützt.  
  
|Taktik|Lösungskomponententyp|  
|------------|-----------------------------|  
|[Zeichenfolge (RESX) Webressourcen](#BKMK_Localizable_Web_Resources)|Webressourcen|  
|[Eingebettete Beschriftungen](#BKMK_EmbeddedLabels)|Anwendungsnavigation (SiteMap) <br />Menübänder|  
|[Importieren und Exportieren von Übersetzungen](#BKMK_ExportAndImportTranslations)|Attribute<br />Diagramme<br />Dashboards<br />Entity<br />Entitätsbeziehungen<br />Formulare<br />Nachrichten<br />Optionssätze<br />Ansichten|  
|[Lokalisierung in den Ausgangssprachenzeichenfolgen](#BKMK_LocalizationInBaseLanguageStrings)|Vertragsvorlagen<br /> Verbindungsrollen<br />Prozesse (Workflow)<br />Sicherheitsrollen<br />Feldsicherheitsprofile|  
|[Lokalisierung nicht erforderlich](#BKMK_LocalizationNotRequired)|SDK-Nachrichtenverarbeitungsschritte<br />Serviceendpunkte|  
|[Separate Komponente für jede Sprache](#BKMK_SeparateComponentForEachLanguage)|Artikelvorlagen<br />E-Mail-Vorlagen<br />Seriendruckvorlagen<br />Berichte<br />Dialoge|  
|[Verwenden von XML-Webressourcen als Sprachenressourcen](#BKMK_UseXMLWebResourcesAsLanguageResources)|Plug-In-Assemblys|  
  
 Die folgenden Abschnitte stellen weitere Details für jede Taktik bereit.  

 <a name="BKMK_Localizable_Web_Resources"></a>

 ## <a name="string-resx-web-resources"></a>Zeichenfolge (RESX) Webressourcen
 Wenn Zeichenfolge (RESX)-Webressourcen mit Common Data Service hinzugefügt werden, verfügen Entwickler über eine Option, robustere Webressourcen zu erstellen, die mehrere Sprachen unterstützen. Weitere Information [Webressourcen der Zeichenfolge (RESX)](/dynamics365/customer-engagement/developer/resx-web-resources)

 Für frühere Versionen siehe [Entwickleroption](https://msdn.microsoft.com/library/hh670609(v=crm.8).aspx#BKMK_DeveloperOption)
  
<a name="BKMK_EmbeddedLabels"></a>   

## <a name="embedded-labels"></a>Eingebettete Beschriftungen  
 Jede der Lösungskomponenten, die diese Taktik verwenden, erfordert, dass jeder lokalisierte Text in der Lösungskomponente enthalten ist.  
  
### <a name="ribbons"></a>Menübänder  
 Wenn ein Language Pack installiert ist, zeigt das Menüband automatisch lokalisierten Text für den gesamten Standardtext im Menüband an. Systembeschriftungen werden in einem `ResourceId`-Attribut definiert, das nur für den internen Gebrauch ist. Wenn Sie einen eigenen Text hinzufügen, sollten Sie das `<LocLabels>`-Element verwenden, um lokalisierten Text für Sprachen bereitzustellen, die Sie unterstützen. Weitere Informationen: [Verwenden von lokalisierten Bezeichnungen in Menübändern](/dynamics365/customer-engagement/developer/customize-dev/use-localized-labels-ribbons)  
  
### <a name="sitemap"></a>SiteMap  
 Wenn ein Language Pack installiert ist, zeigt der Standardtext in der Anwendungsnavigationsleiste automatisch lokalisierten Text an. Wenn Sie den Standardtext überschreiben oder einen eigenen Text bereitstellen möchten, verwenden Sie das `<Titles>`-Element. Das `Titles`-Element sollte ein `<Title>`-Element mit lokalisiertem Text für alle Sprachen enthalten, die Ihre Lösung unterstützt. Wenn ein `Title`-Element für die bevorzugte Sprache des Benutzers nicht verfügbar ist, wird der Titel, der der Organisationsausgangssprache entspricht, angezeigt.  
  
 Das `<SubArea>`-Element ermöglicht das Übergeben der Spracheinstellung des Benutzers mithilfe des `userlcid`-Parameters, sodass Inhalt, der das Ziel des `SubArea.Url`-Attributs ist, die Spracheinstellung des Benutzers berücksichtigen und entsprechend anpassen kann. Weitere Informationen: [Übergeben von Parametern an eineURL mithilfe von SiteMap](/dynamics365/customer-engagement/developer/customize-dev/pass-parameters-url-using-sitemap)  
  
<a name="BKMK_ExportAndImportTranslations"></a>   

## <a name="export-and-import-translations"></a>Importieren und Exportieren von Übersetzungen  
 Lokalisierbare Beschriftungen für die Lösungskomponenten in der folgenden Tabelle können für die Lokalisierung exportiert werden.  
  
||||  
|-|-|-|  
|Entitäten|Attribute|Beziehungen|  
|Globaler Optionssatz|Entitätsmeldungen|Entitätsformulare|  
|Entitätsansichten (SavedQuery)|Diagramme|Dashboards|  
  
### <a name="translating-labels-and-display-strings"></a>Übersetzen von Beschriftungen und Anzeigezeichenfolgen  
 Sie können Anpassungen nur in der Anwendung ausführen, indem Sie die Ausgangssprache verwenden. Wenn Sie für diese Anpassungen lokalisierte Bezeichnungen und Anzeigezeichenfolgen zur Verfügung stellen möchten, müssen Sie den Text der Bezeichnungen exportieren, damit sie für andere Sprachen lokalisiert werden können, die für die Organisation aktiviert sind. Verwenden Sie die folgenden Schritte:  
  
1. Stellen Sie sicher, dass die Organisation, an der Sie arbeiten, alle MUI-Pakete installiert und Sprachen für die Sprachen bereitgestellt hat, für die Sie Übersetzungen bereitstellen möchten.  
  
2. Erstellen Sie die Lösung und ändern Sie die Komponenten.  
  
3. Wenn Sie das Entwickeln der Lösung abgeschlossen haben, verwenden Sie die Funktion "Übersetzungen exportieren". Dadurch wird ein Office Excel-Spreadsheet (CrmTranslations.xml) erstellt, das alle zu übersetzenden Bezeichnungen enthält.  
  
4. In der Tabelle können Sie die entsprechenden Übersetzungen bereitstellen.  
  
5. Importieren Sie Übersetzungen zurück in dieselbe Common Data Service-Organisation mithilfe der Funktionen "Übersetzungen importieren" und veröffentlichen Sie die Änderungen.  
  
6. Beim nächsten Exportieren der Lösung sind alle Übersetzungen enthalten, die Sie bereitgestellt haben.  
  
   Wenn eine Lösung importiert wird, werden Beschriftungen für die Sprachen, die nicht verfügbar sind im Zielsystem, verworfen, und eine Warnung wird protokolliert.  
  
   Wenn Bezeichnungen für die Ausgangssprache des Zielsystems nicht im Lösungspaket bereitgestellt werden, werden die Bezeichnungen der Ausgangssprache der Quelle verwendet. Beispielsweise wenn Sie eine Lösung importieren, die Bezeichnungen für Englisch und Französisch mit Englisch die Ausgangsprache enthält, aber das Zielsystem Japanisch und Französisch mit Japanisch als Ausgangssprache aufweist, werden anstelle der japanischen Beschriftungen englische verwendet. Die Ausgangssprachenbeschriftungen können nicht **Null** oder leer sein.  
  
#### <a name="exporting-translations"></a>Exportieren von Übersetzungen  
 Bevor Sie Übersetzungen exportieren, müssen die Sprachpakete installieren und alle Sprachen bereitstellen, die Sie lokalisieren möchten. Sie können Übersetzungen in die Webanwendung exportieren oder die <xref:Microsoft.Crm.Sdk.Messages.ExportTranslationRequest>-Nachricht verwenden. Weitere Informationen finden Sie unter [Exportieren von benutzerdefiniertem Entitäts- und Feldtext zur Übersetzung](/dynamics365/customer-engagement/customize/export-customized-entity-field-text-translation).  
  
#### <a name="translating-text"></a>Übersetzen von Text  
 Wenn Sie die CrmTranslations.xml-Datei in Office Excel öffnen, sehen Sie die drei Arbeitsblätter, die in der folgenden Tabelle aufgeführt sind.  
  
|Arbeitsblatt|Beschreibung|  
|---------------|-----------------|  
|Informationen|Zeigt Organisations- und Lösungsinformationen an, aus denen die Bezeichnungen und Zeichenfolgen exportiert wurden.|  
|Anzeigezeichenfolgen|Zeigt Zeichenfolgen an, die den Text aller Nachrichten darstellen, die einer Metadatenkomponente zugeordnet sind. Diese Tabelle enthält Fehlermeldungen und Zeichenfolgen, die für Systemmenübandelemente verwendet werden.|  
|Lokalisierte Beschriftungen|Zeigt alle Texte für alle Metadatenkomponentenbeschriftungen an.|  
  
 Sie können diese Datei an einen Sprachexperten, an eine Übersetzungsagentur oder an ein Lokalisierungsunternehmen senden. Sie müssen lokalisierte Zeichenfolgen für die leeren Zellen bereitstellen.  
  
> [!NOTE]
>  Bei benutzerdefinierten Entitäten gibt es mehrere mögliche Bezeichnungen, die gemeinsam mit Systementitäten, beispielsweise **Erstellt am** oder **Erstellt von**, verwendet werden. Da Sie die Sprachen bereits installiert und bereitgestellt haben, wenn Sie für die Standardlösung Sprachen exportieren, können Sie in der Lage sein, einige Beschriftungen in Ihren benutzerdefinierten Entitäten mit lokalisiertem Text für identische Etiketten abzugleichen, die von anderen Entitäten verwendet werden. Dadurch können die Lokalisierungskosten verringert und die Konsistenz verbessert werden.  
  
 Nachdem der Text in den Tabellen lokalisiert wurde, fügen Sie die Dateien CrmTranslations.xml und [Content_Types].xml Dateien einer einzelnen komprimierten .zip-Datei hinzu. Diese Datei können Sie dann importieren.  
  
 Wenn Sie lieber mit den exportierten Dateien programmgesteuert als XML Dokument arbeiten möchten, finden Sie unter [Office 2003 XML-Referenzschemas](https://www.microsoft.com/downloads/details.aspx?FamilyID=fe118952-3547-420a-a412-00a2662442d9) Informationen zu den Schemas, die diese Dateien verwenden.  
  
#### <a name="importing-translated-text"></a>Importieren von übersetztem Text  
  
> [!IMPORTANT]
>  Sie können nur übersetzten Text in dieselbe Organisation importieren, aus der er exportiert wurde.  
  
 Wenn Sie den angepassten Text für Entitäten oder Attribute exportiert und anschließend übersetzt haben, können Sie die übersetzten Textzeichenfolgen mit der <xref:Microsoft.Crm.Sdk.Messages.ImportTranslationRequest>-Nachricht in die Webanwendung importieren. Die Datei, die Sie importieren, muss eine komprimierte Datei sein, in der die CrmTranslations.xml und die [Content_Types].xml im Stammverzeichnis enthalten ist. Weitere Informationen finden Sie unter [Importieren von übersetztem Entitäts- und Feldtext](/dynamics365/customer-engagement/customize/import-translated-entity-field-text).  
  
 Nach dem Importieren der fertig gestellten Übersetzungen wird benutzerdefinierter Text für Benutzer angezeigt, die in den Sprachen arbeiten, in die der Text übersetzt wurde.  
  
> [!NOTE]
> In Common Data Service kann übersetzter Text mit mehr als 500 Zeichen nicht importiert werden. Wenn Elemente in Ihrer Übersetzung eine Länge von 500 Zeichen überschreiten, tritt beim Importvorgang ein Fehler auf. Überprüfen Sie bei Auftreten eines Importfehlers die Zeile in der Datei, durch die der Fehler verursacht wurde, verringern Sie die Zeichenanzahl, und führen Sie einen erneuten Importvorgang aus.  
  
 Da die Anpassung nur in der Ausgangssprache unterstützt wird, können Sie Common Data Service so verwenden, dass die Ausgangssprache auf Ihre Spracheinstellung festgelegt ist. Wenn Sie überprüfen möchten, ob der übersetzte Text angezeigt wird, muss die Spracheinstellung für die Benutzeroberfläche von Common Data Service geändert werden. Zum Ausführen weiterer Anpassungen muss die Spracheinstellung dann wieder auf die Ausgangssprache festgelegt werden.  
  
<a name="BKMK_LocalizationInBaseLanguageStrings"></a>   

## <a name="localization-in-base-language-strings"></a>Lokalisierung in den Ausgangssprachenzeichenfolgen  
 Einige Lösungskomponenten unterstützen nicht mehrere Sprachen. Diese Komponenten enthalten Namen oder Texte, die nur in einer bestimmten Sprache eine Bedeutung haben. Wenn Sie eine Lösung für eine bestimmte Sprache erstellen, definieren Sie diese Lösungskomponenten für die beabsichtigte Organisationsausgangssprache.  
  
 Falls Sie mehrere Sprachen unterstützen müssen, ist eine Taktik, Lokalisierung in die Ausgangssprachenzeichenfolgen einzuschließen. Wenn Sie z. B. eine Verbindungsrolle namens "Freund" haben und Sie Englisch, Spanisch und Deutsch unterstützen müssen, können Sie möglicherweise den Text "Freund (Amigo/Friend)" als Name der Verbindungsrolle verwenden. Angesichts der Probleme der Textlänge bestehen Einschränkungen hinsichtlich der Anzahl der Sprachen, die mit dieser Taktik unterstützt werden können.  
  
 Einige Lösungskomponenten in dieser Gruppe werden nur Administratoren angezeigt. Da die Anpassung des Systems nur in der Organisationsausgangssprache ausgeführt werden kann, ist es nicht erforderlich, mehrere Sprachversionen bereitzustellen. Die Komponenten **Sicherheitsrollen** und **Feldsicherheitsprofil** gehören dieser Gruppe an.  
  
 **Vertragsvorlagen** stellen eine Beschreibung eines Typs von Servicevertrag bereit. Diese erfordern Text für die Felder **Name** und **Abkürzung**. Sie sollten Abkürzungen und Namen verwenden, die für alle Benutzer der Organisation eindeutig und geeignet sind.  
  
 **Verbindungsrollen** basieren auf einer Person, die für eine Verbindungsrolle beschreibende Kategorien und Namen auswählt. Da diese möglicherweise verhältnismäßig kurz sind, wird empfohlen, dass Sie in den Ausgangssprachenzeichenfolgen Lokalisierung einschließen.  
  
 **Prozesse (Workflows)** die für Ereignisse initiiert werden, können gut funktionieren, wenn sie keine Datensätze mit Text aktualisieren müssen, der lokalisiert werden soll. Es ist möglich, eine Workflowassembly zu verwenden, damit Logik, die ggf. für lokalisierten Text gilt, die gleiche Strategie wie Plug-In-Assemblys verwenden kann.([Verwenden von XML Webressourcen als Sprachressourcen](#BKMK_UseXMLWebResourcesAsLanguageResources)).  
  
 **Bedarfsgesteuerte Workflows** erfordern einen Namen, damit Benutzer sie auswählen können. Zusätzlich zum Einschließen der Lokalisierung innerhalb des Namens des bedarfsgesteuerten Workflows ist eine andere Taktik, mehrere Workflows mit lokalisierten Namen zu erstellen, die alle den gleichen untergeordneten Prozess aufrufen. Allerdings sehen alle Benutzer die vollständige Liste der bedarfsgesteuerten Workflows, nicht nur die in der bevorzugten Sprache der Benutzeroberfläche.  
  
<a name="BKMK_LocalizationNotRequired"></a>   
## <a name="localization-not-required"></a>Lokalisierung nicht erforderlich  
 **SDK-Nachrichtenverarbeitungsschritt**- und **Dienstendpunkt**-Lösungskomponenten zeigen dem Benutzer keinen lokalisierbaren Text an. Wenn es wichtig ist, dass diese Komponenten Namen und Beschreibungen haben, die der Ausgangssprache der Organisation entsprechen, können Sie eine verwaltete Lösung mit Namen und Beschreibungen in dieser Sprache erstellen und exportieren.  
  
<a name="BKMK_SeparateComponentForEachLanguage"></a>   
## <a name="separate-component-for-each-language"></a>Separate Komponente für jede Sprache  
 Die folgenden Lösungskomponenten enthalten unter Umständen viel lokalisierbaren Text:  
  
- Artikelvorlagen  
  
- E-Mail-Vorlagen  
  
- Seriendruckvorlagen  
  
- Berichte  
  
- Dialoge  
  
  Für diesen Typen von Lösungskomponenten ist die empfohlene Taktik, separate Komponenten für jede Sprache zu erstellen. Das bedeutet, dass Sie üblicherweise eine verwalteten Basislösung erstellen, die die Kernlösungskomponenten enthält, und anschließend eine separate verwaltete Lösung erstellen, die Lösungskomponenten für die Sprachen enthält. Nachdem Kunden die Gebietsschemalösung installiert haben, können sie die verwalteten Lösungen für die Sprachen installieren, die sie für die Organisation bereitgestellt haben.  
  
  Anders als **Prozesse (Workflows)** können Sie **Dialoge** erstellen, die die Spracheinstellungen des aktuellen Benutzers wiedergeben und die Dialoge nur Benutzern dieser Sprache anzeigen.  
  
#### <a name="create-a-localized-dialog-box"></a>Erstellen eines lokalisierten Dialogfelds  
  
1. Installieren Sie das entsprechende Sprachpaket und stellen Sie die Sprache bereit.  
  
    Weitere Informationen finden Sie unter [Sprachpaket-Installationsanweisungen](https://technet.microsoft.com/library/hh699674.aspx).  
  
2. Ändern Sie Ihre persönlichen Optionen, um die **Sprache der Benutzeroberfläche** für die Sprache für den Dialog anzugeben.  
  
3. Navigieren Sie zu **Einstellungen**, und wählen Sie in der Gruppe **Prozesscenter** die Option **Prozesse** aus.  
  
4. Klicken Sie auf **Neu** und erstellen Sie das Dialogfeld in der angegebenen Sprache.  
  
5. Nachdem Sie das Dialogfeld erstellt haben, ändern Sie Ihre persönlichen Optionen, um die Organisationsausgangssprache anzugeben.  
  
6. Bei Verwendung der Organisationsausgangssprache können Sie zum Bereich **Lösungen** unter **Einstellungen** navigieren und das lokalisierte Dialogfeld als Teil einer Lösung hinzufügen.  
  
   Das Dialogfeld, das in der anderen Sprache erstellt wurde, wird nur Benutzern angezeigt, die Common Data Service mithilfe dieser Sprache anzeigen.  
  
<a name="BKMK_UseXMLWebResourcesAsLanguageResources"></a>   

## <a name="use-xml-web-resources-as-language-resources"></a>Verwenden von XML-Webressourcen als Sprachenressourcen  
 Plug-In-Assemblylösungskomponenten können Nachrichten an einen Endbenutzer senden, indem sie <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> auslösen und Datensätze erstellen und aktualisieren. Im Gegensatz zu Silverlight-Webressourcen können Plug-Ins keine Ressourcendateien verwenden.  
  
 Falls ein Plug-In lokalisierten Text erfordert, können Sie eine XML-Webressource verwenden, um die lokalisierten Zeichenfolgen zu speichern, damit das Plug-In bei Bedarf darauf zugreifen kann. Die Struktur der XML-Datei können Sie auswählen, aber Sie sollten der Struktur folgen, die von ASP.NET Ressourcendateien (.resx) verwendet wird, um separate XML-Webressourcen für die einzelnen Sprachen zu erstellen. Folgendes ist z. B. eine XML-Webressource namens **localizedString.en_US**, die dem Muster folgt, das verwendet wird von resx-Dateien.  
  
```xml  
<root>  
 <data name="ErrorMessage">  
  <value>There was an error completing this action. Please try again.</value>  
 </data>  
 <data name="Welcome">  
  <value>Welcome</value>  
 </data>  
</root>  
```  
  
 Der folgende Code zeigt, wie eine lokalisierte Nachricht zurück an ein Plug-In gegeben werden kann, um dem Benutzer eine Nachricht anzuzeigen. Es eignet sich für die Vorüberprüfungsphase eines `Delete`-Ereignisses für die `Account`-Entität:  
  
```csharp  
protected void ExecutePreValidateAccountDelete(LocalPluginContext localContext)  
  {  
   if (localContext == null)  
   {  
    throw new ArgumentNullException("localContext");  
   }  
   int OrgLanguage = RetrieveOrganizationBaseLanguageCode(localContext.OrganizationService);  
   int UserLanguage = RetrieveUserUILanguageCode(localContext.OrganizationService,  
 localContext.PluginExecutionContext.InitiatingUserId);  
   String fallBackResourceFile = "";  
   switch (OrgLanguage)  
   {  
    case 1033:  
     fallBackResourceFile = "new_localizedStrings.en_US";  
     break;  
    case 1041:  
     fallBackResourceFile = "new_localizedStrings.ja_JP";  
     break;  
    case 1031:  
     fallBackResourceFile = "new_localizedStrings.de_DE";  
     break;  
    case 1036:  
     fallBackResourceFile = "new_localizedStrings.fr_FR";  
     break;  
    case 1034:  
     fallBackResourceFile = "new_localizedStrings.es_ES";  
     break;  
    case 1049:  
     fallBackResourceFile = "new_localizedStrings.ru_RU";  
     break;  
    default:  
     fallBackResourceFile = "new_localizedStrings.en_US";  
     break;  
   }  
   String ResourceFile = "";  
   switch (UserLanguage)  
   {  
    case 1033:  
     ResourceFile = "new_localizedStrings.en_US";  
     break;  
    case 1041:  
     ResourceFile = "new_localizedStrings.ja_JP";  
     break;  
    case 1031:  
     ResourceFile = "new_localizedStrings.de_DE";  
     break;  
    case 1036:  
     ResourceFile = "new_localizedStrings.fr_FR";  
     break;  
    case 1034:  
     ResourceFile = "new_localizedStrings.es_ES";  
     break;  
    case 1049:  
     ResourceFile = "new_localizedStrings.ru_RU";  
     break;  
    default:  
     ResourceFile = fallBackResourceFile;  
     break;  
   }  
   XmlDocument messages = RetrieveXmlWebResourceByName(localContext, ResourceFile);  
   String message = RetrieveLocalizedStringFromWebResource(localContext, messages, "ErrorMessage");  
   throw new InvalidPluginExecutionException(message);  
  }  
  protected static int RetrieveOrganizationBaseLanguageCode(IOrganizationService service)  
  {  
   QueryExpression organizationEntityQuery = new QueryExpression("organization");  
   organizationEntityQuery.ColumnSet.AddColumn("languagecode");  
   EntityCollection organizationEntities = service.RetrieveMultiple(organizationEntityQuery);  
   return (int)organizationEntities[0].Attributes["languagecode"];  
  }  
  protected static int RetrieveUserUILanguageCode(IOrganizationService service, Guid userId)  
  {  
   QueryExpression userSettingsQuery = new QueryExpression("usersettings");  
   userSettingsQuery.ColumnSet.AddColumns("uilanguageid", "systemuserid");  
   userSettingsQuery.Criteria.AddCondition("systemuserid", ConditionOperator.Equal, userId);  
   EntityCollection userSettings = service.RetrieveMultiple(userSettingsQuery);  
   if (userSettings.Entities.Count > 0)  
   {  
    return (int)userSettings.Entities[0]["uilanguageid"];  
   }  
   return 0;  
  }  
  protected static XmlDocument RetrieveXmlWebResourceByName(LocalPluginContext context, string webresourceSchemaName)  
  {  
   context.TracingService.Trace("Begin:RetrieveXmlWebResourceByName, webresourceSchemaName={0}", webresourceSchemaName);  
   QueryExpression webresourceQuery = new QueryExpression("webresource");  
   webresourceQuery.ColumnSet.AddColumn("content");  
   webresourceQuery.Criteria.AddCondition("name", ConditionOperator.Equal, webresourceSchemaName);  
   EntityCollection webresources = context.OrganizationService.RetrieveMultiple(webresourceQuery);  
   context.TracingService.Trace("Webresources Returned from server. Count={0}", webresources.Entities.Count);  
   if (webresources.Entities.Count > 0)  
   {  
    byte[] bytes = Convert.FromBase64String((string)webresources.Entities[0]["content"]);  
    // The bytes would contain the ByteOrderMask. Encoding.UTF8.GetString() does not remove the BOM.  
    // Stream Reader auto detects the BOM and removes it on the text  
    XmlDocument document = new XmlDocument();  
    document.XmlResolver = null;  
    using (MemoryStream ms = new MemoryStream(bytes))  
    {  
     using (StreamReader sr = new StreamReader(ms))  
     {  
      document.Load(sr);  
     }  
    }  
    context.TracingService.Trace("End:RetrieveXmlWebResourceByName , webresourceSchemaName={0}", webresourceSchemaName);  
    return document;  
   }  
   else  
   {  
    context.TracingService.Trace("{0} Webresource missing. Reinstall the solution", webresourceSchemaName);  
    throw new InvalidPluginExecutionException(String.Format("Unable to locate the web resource {0}.", webresourceSchemaName));  
    return null;  
 // This line never reached  
   }  
  }  
  protected static string RetrieveLocalizedStringFromWebResource(LocalPluginContext context, XmlDocument resource, string resourceId)  
  {  
   XmlNode valueNode = resource.SelectSingleNode(string.Format(CultureInfo.InvariantCulture, "./root/data[@name='{0}']/value", resourceId));  
   if (valueNode != null)  
   {  
    return valueNode.InnerText;  
   }  
   else  
   {  
    context.TracingService.Trace("No Node Found for {0} ", resourceId);  
    throw new InvalidPluginExecutionException(String.Format("ResourceID {0} was not found.", resourceId));  
   }  
  }  
```  
  
### <a name="see-also"></a>Siehe auch  
 [Packen und Verteilen von Erweiterungen mithilfe von Dynamics 365-Lösungen](/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions)   
 [Einführung zu Lösungen](introduction-solutions.md)   
 [Planen einer Lösungsentwicklung](/dynamics365/customer-engagement/developer/plan-solution-development)   
 [Abhängigkeitsnachverfolgung für Lösungskomponenten](dependency-tracking-solution-components.md)   
 [Erstellen, Exportieren oder Importieren einer nicht verwalteten Lösung](create-export-import-unmanaged-solution.md)   
 [Eine verwaltete Lösung erstellen, installieren und aktualisieren](create-install-update-managed-solution.md)   
 [Deinstallieren oder Löschen einer Lösung](uninstall-delete-solution.md)   
 [Lösungsentitäten](/dynamics365/customer-engagement/developer/solution-entities)   
 [Produkteigenschaftswerte lokalisieren](/dynamics365/customer-engagement/developer/localize-product-property-values)
