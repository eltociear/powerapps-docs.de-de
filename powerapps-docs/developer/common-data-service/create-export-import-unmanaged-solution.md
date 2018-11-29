---
title: 'Erstellen, importieren oder exportieren einer nicht verwalteten Lösung (Common Data Service for Apps) | Microsoft Docs'
description: 'Eine nicht verwaltete Lösung ist nützlich als Möglichkeit, einen Satz nicht verwalteter Anpassungen zu einem Satz zu gruppieren, der zwischen Organisationen transportiert werden kann.'
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
# <a name="create-export-or-import-an-unmanaged-solution"></a>Erstellen, Exportieren oder Importieren einer nicht verwalteten Lösung

Darüber hinaus, dass es eine Voraussetzung zum Erstellen einer verwalteten Lösung ist, ist eine nicht verwaltete Lösung nützlich als Möglichkeit, einen Satz nicht verwalteter Anpassungen zu einem Satz zu gruppieren, der zwischen Organisationen transportiert werden kann.  

 Weitere Informationen: [Verwendung von Lösungen für die Anpassungen](/dynamics365/customer-engagement/developer/customize/use-solutions-for-your-customizations).  

<a name="BKMK_CreateUnmanagedSolution"></a> 

## <a name="create-an-unmanaged-solution"></a>Erstellen einer nicht verwalteten Lösung  
 Jede Lösung erfordert einen Herausgeber. Wenn Sie die Lösung nicht verteilen möchten, können Sie den Standardherausgeber verwenden, der bereits für die Organisation erstellt wurde. Siehe [Einen Lösungsherausgeber erstellen](create-export-import-unmanaged-solution.md#BKMK_CreateSolutionPublisher) für Informationen zum Erstellen eines Lösungsherausgebers.  

 In der folgenden Tabelle sind die Felder und Beschreibungen aufgelistet, die in einer Lösung enthalten sind.  


|      Feldbezeichnung       |                                                                                                                                                              Beschreibung                                                                                                                                                               |
|------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    **Anzeigename**    |                                                                                                                                                       Der Name der Lösung.                                                                                                                                                       |
|        **Name**        |                                     Common Data Service for Apps generiert einen eindeutigen Namen basierend auf dem **Anzeigename**. Sie können den eindeutigen Namen bearbeiten. Der eindeutige Name darf nur alphanumerische Zeichen oder das Unterstrichzeichen enthalten.                                     |
|     **Herausgeber**      |                                                                                                                                Verwenden Sie die **Herausgeber**-Suche, um die Lösung dem Herausgeber zuzuordnen.                                                                                                                                |
|      **Version**       |                                                                                                                     Geben Sie eine Version im folgenden Format an: Hauptversion.Nebenversion.Build.Revision, zum Beispiel 1.0.0.0.                                                                                                                     |
| **Konfigurationsseite** | Wenn Sie in die Lösung eine HTML-Webressource einschließen, können Sie diese Suche verwenden, um sie als festgelegte Konfigurationsseite hinzuzufügen.<br /><br /> Weitere Informationen: [Verwenden Sie die Lösungskonfigurationsseite](create-export-import-unmanaged-solution.md#BKMK_UseSolutionConfigurationPage) |
|    **Beschreibung**     |                                                                                                                                  Verwenden Sie das Feld, um alle relevanten Details über die Lösung einzufügen.                                                                                                                                   |

 Nach dem Erstellen einer nicht verwalteten Lösung können Sie Lösungskomponenten hinzufügen, indem Sie sie im Kontext dieser Lösung erstellen oder indem Sie vorhandene Komponenten von anderen Lösungen hinzufügen. Weitere Informationen zum programmgesteuerten Erstellen einer Lösungsherausgebers finden Sie unter [So erstellen Sie eine Lösung](work-solutions.md#BKMK_CreateASolution)  

<a name="BKMK_CreateSolutionPublisher"></a>   

### <a name="create-a-solution-publisher"></a>Erstellen eines Lösungsherausgebers  
 Wenn Sie verwaltete Lösungen verteilen möchten, sollten Sie einen `Publisher` erstellen. In der folgenden Tabelle sind die Felder und Beschreibungen aufgelistet, die in einem `Publisher` enthalten sind.  


|          Etikett          |                                                                                                                                                                                                       Beschreibung                                                                                                                                                                                                        |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    **Anzeigename**     |                                                                                                                                                                       Der im **Herausgeber**-Suchfeld in der Lösung angezeigt werden soll.                                                                                                                                                                        |
|        **Name**         |                               CDS for Apps generiert einen eindeutigen Namen basierend auf dem **Anzeigename**. Der eindeutige Name kann nur alphanumerische Zeichen und das Unterstrichzeichen enthalten. **Hinweis:**  Sie verwenden den `Unique Name`, um einen `Publisher` eindeutig zu identifizieren. Verwaltete Lösungen, die den gleichen Herausgeber haben, können sich gegenseitig aktualisieren.                               |
|     **Beschreibung**     |                                                                                                                                                                           Verwenden Sie das Feld, um alle relevanten Details über die Lösung einzufügen.                                                                                                                                                                            |
|       **Präfix**        |                   Mithilfe des Anpassungspräfixes können Sie identifizieren, welcher Herausgeber eine Lösungskomponente hinzugefügt hat. Zum Beispiel wird das Präfix dem logischen Namen aller Entitäten oder Attribute hinzugefügt, die im Kontext einer diesem Herausgeber zugeordneten Lösung erstellt werden. Das Präfix muss zwischen zwei und acht Zeichen enthalten und kann nur alphanumerische Zeichen enthalten. Es kann nicht mit ‘mscrm’ anfangen.                   |
| **Optionswertpräfix** | Mithilfe dieses Werts können Sie Optionen trennen, die Sie Optionssätzen hinzufügen, um das Zusammenführen von Optionen zu unterstützen. Der Wert wird auf der Basis des **Präfix**-Textes automatisch generiert, damit er eindeutiger werden kann. Der Wert muss zwischen 10.000 und 99.999 sein.<br /><br /> Weitere Informationen: [Optionssatz-Optionen zusammenführen](/dynamics365/customer-engagement/developer/understand-managed-solutions-merged#BKMK_MergingOptionSetOptions) |
|   **Kontaktdetails**   |                                                                                                                                                           Verwenden Sie diese Felder, um Informationen hinzuzufügen, mithilfe derer Personen, die die Lösung installieren, Sie kontaktieren können.                                                                                                                                                           |

 Siehe [Einen Lösungsherausgeber erstellen](work-solutions.md#BKMK_CreatePublisher) für Informationen zum programmgesteuerten Erstellen eines Lösungsherausgebers.  

<a name="BKMK_UseSolutionConfigurationPage"></a>   
### <a name="use-the-solution-configuration-page"></a>Verwenden der Lösungskonfigurationsseite  
 Die Lösungskonfigurationsseite enthält eine Canvas, die Sie verwenden können, um Informationen anzuzeigen oder um Kunden zu ermöglichen, Aktionen im Rahmen der Lösung auszuführen. Legen Sie die Konfigurationsseite fest, indem Sie das Suchfeld **Konfigurationsseite** verwenden, um eine Webseiten-(HTML)-Webressource auszuwählen, die in der Lösung enthalten ist. Dadurch wird ein neuer **Konfiguration**sknoten im Lösungsfenster unter dem **Information**sknoten und über dem **Komponenten**knoten angezeigt. Der **Konfigurations**knoten zeigt die von Ihnen festgelegte Webressource an.  

 Sie können die Lösungskonfigurationsseite verwenden, um Steuerelemente anzuzeigen, die Ihre Lösung konfigurieren. Sie können möglicherweise einige Entitäten in Ihrer Lösung bereitstellen, die das Verhalten der Lösung steuern. Indem Sie die Web-API für Datenzugriff verwenden, können Sie auf Ihrer Webressourcenseite benutzerdefinierte Steuerelemente bereitstellen, um die Daten in diesen Entitäten zu aktualisieren.  

<a name="BKMK_UnmanagedSolution"></a>   
## <a name="export-an-unmanaged-solution"></a>Exportieren einer nicht verwalteten Lösung  
 In den folgenden Fällen möchten Sie möglicherweise eine nicht verwaltete Lösung exportieren:  

- Sie müssen bestimmten XML-Inhalt in der Datei customizations.xml bearbeiten, beispielsweise möchten Sie möglicherweise die SiteMap bearbeiten oder benutzerdefinierte Menübänder erstellen.  

- Sie möchten die nicht verwaltete Lösung aus einer Organisation in eine andere transportieren.  

- Sie möchten eine Sicherung Ihres aktuellen Satzes von Anpassungen erstellen.  

  Durch das Exportieren einer nicht verwalteten Lösung wird eine komprimierte (gezippte) Datei erstellt, die dann in eine andere Organisation oder dieselbe Organisation importiert werden kann.  

  Nur veröffentlichte Anpassungen werden einbezogen, wenn Sie eine Lösung exportieren. Deshalb müssen Sie darauf achten, alle Änderungen zu veröffentlichen, bevor Sie eine Lösung exportieren.  

  Wenn Sie eine Lösung mithilfe der Webanwendung exportieren und wenn die Lösung dann irgendwelche fehlenden, erforderlichen Komponenten enthält, sehen Sie den Schritt **Fehlende erforderliche Komponenten**. Sie können diese Warnung nur dann ignorieren, wenn Sie diese Lösung als nicht verwaltete Lösung in die ursprüngliche Organisation zurückimportieren wollen. Befolgen Sie andernfalls die Anweisungen im Dialogfeld, um den Export abzubrechen und die erforderlichen Komponenten hinzuzufügen.  

  Verwenden Sie die Nachricht <xref:Microsoft.Crm.Sdk.Messages.ExportSolutionRequest>, um eine Lösung programmgesteuert zu exportieren. Weitere Informationen: [Exportieren oder Packen einer Lösung](work-solutions.md#BKMK_ExportPackageSolution)  

  Wenn Sie eine Lösung mithilfe der Webanwendung exportieren, können Sie im Schritt **Systemeinstellungen exportieren (Erweitert)** auswählen, welche Systemeinstellungen in die Lösung einbezogen werden sollen. Diese Optionen sind für Entwicklern verfügbar, und zwar mithilfe von <xref:Microsoft.Crm.Sdk.Messages.ExportSolutionRequest> über die in der Anforderung verfügbaren Member. In den Anmerkungen zur Anforderung finden Sie Details darüber, welche Einstellungen enthalten sind.  

  Sie können eine Zielversion auswählen, wenn Sie eine Lösung exportieren. Sie können eine Lösung exportieren, die mit früheren Versionen kompatibel ist. Weitere Informationen: [Exportieren einer Lösung für eine bestimmte Dynamics 365-Version](export-solution-specific-version.md).  

<a name="BKMK_ImportUnmanagedSolution"></a>   
## <a name="import-an-unmanaged-solution"></a>Importieren einer nicht verwalteten Lösung  
 In den folgenden Fällen sollten Sie eine nicht verwaltete Lösung importieren:  

- Sie möchten einen Satz von Anpassungen von einer Organisation zu einer anderen transportieren, und Sie möchten es zulassen, dass die Lösungskomponenten geändert werden können.  

- Sie möchten einen älteren Satz von Lösungskomponentendefinitionen wiederherstellen oder zu diesem zurückkehren.  

  Das Importieren einer nicht verwaltete Lösung ist ein additiver Prozess. Beim Importieren einer älteren Version einer verwalteten Lösung, werden Lösungskomponenten nicht entfernt, die in einer späteren Version enthalten sind. Allerdings wird die Definition von allen Lösungskomponenteneigenschaften mit der Definition überschrieben, die in der letzten nicht verwaltete Lösung enthalten ist, die Sie importieren.  

> [!IMPORTANT]
>  Änderungen, die durch das Importieren einer nicht verwalteten Lösung angewendet wurden, können nicht deinstalliert werden. Sie sollten daher keine nicht verwaltete Lösung installieren, wenn Sie die Änderungen zurücksetzen möchten.  

 Dieser Vorgang wird programmgesteuert mithilfe der Nachricht  <xref:Microsoft.Crm.Sdk.Messages.ImportSolutionRequest> ausgeführt. Sie können Code schreiben, um diese Nachricht asynchron auszuführen. Weitere Informationen: [Nachrichten im Hintergrund (asynchron) ausführen](/dynamics365/customer-engagement/developer/org-service/use-messages-request-response-classes-execute-method#bkmk_executeasync). Sie können den Status des Importvorgangs verfolgen oder einen Bericht des Erfolgs des Imports generieren, indem Sie die Entität`ImportJob` verwenden. Weitere Informationen: [Installieren oder Aktualisieren einer Lösung](work-solutions.md#BKMK_InstallUpgradeSolution).  

> [!IMPORTANT]
>  Das Installieren einer Lösung oder Veröffentlichen von Anpassungen kann den normalen Systembetrieb stören. Es ist empfehlenswert, den Import von Lösungsimporte einzuplanen, wenn er für die Benutzer am wenigsten Unterbrechungen mit sich bringt.  

<a name="BKMK_MaxSizeOfSolution"></a>   
### <a name="maximum-size-of-solution-to-import"></a>Maximal zulässige Größe der zu importierenden Lösung  
 Für CDS for Apps beträgt die maximale Größe für eine Lösung 29,296 MB.  

 Für lokale Organisationen ist die standardmäßige maximale Größe für eine Lösung 6 MB, diese kann jedoch nach Bedarf erhöht werden.  

 Ändern Sie die maximal zulässige Größe, indem Sie das Element [\<httpRuntime>](https://msdn.microsoft.com/library/e1f13641\(v=vs.100\).aspx) in der Datei web.config für die Anwendung bearbeiten. Bearbeiten Sie die Attribute `executionTimeout` und `maxRequestLength`, um die erforderliche Größe zuzulassen. Nach Abschluss der Installation der Lösung, können sie dafür die von Ihnen gewünschte Größe festlegen.  

### <a name="see-also"></a>Siehe auch  
 [Planen einer Lösungsentwicklung](/dynamics365/customer-engagement/developer/plan-solution-development)   
 [Packen und Verteilen von Erweiterungen mithilfe von Dynamics 365-Lösungen](/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions)   
 [Anpassungslösungsdateischema](/dynamics365/customer-engagement/developer/customize-dev/customization-solutions-file-schema)   
 [Eine verwaltete Lösung erstellen, installieren und aktualisieren](create-install-update-managed-solution.md)   
 [Deinstallieren oder Löschen einer Lösung](uninstall-delete-solution.md)