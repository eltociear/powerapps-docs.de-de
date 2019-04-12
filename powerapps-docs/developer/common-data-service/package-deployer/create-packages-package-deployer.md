---
title: Erstellen von Paketen für den Package Deployer (Common Data Service) | Microsoft Docs
description: 'Erstellen Sie Pakete, die Administratoren im Common Data Service-Instanzen bereitstellen können.'
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
# <a name="create-packages-for-the-package-deployer"></a>Erstellen von Paketen für den Package Deployer

Mit dem Package Deployer können Administratoren Pakete auf Common Data Service-Instanzen bereitstellen. Ein *Paket* kann aus einem oder allen der folgenden Elemente bestehen:  

- Mindestens eine Common Data Service-Lösungsdatei.  
- Flache Dateien oder exportierte Konfigurationsdatendateien aus dem Configuration Migration-Tool. Weitere Informationen zum Tool finden Sie unter  [Verschieben von Konfigurationsdaten über Instanzen und Organisationen hinweg mit dem Konfigurationsmigration-Tool](/dynamics365/customer-engagement/admin/manage-configuration-data).  
- Benutzerdefinierter Code, der ausgeführt werden kann, bevor, während oder nachdem das Paket auf der Common Data Service-Instanz bereitgestellt wird.  
- inhaltsspezifische HTML für das Paket, das bei Start und Ende des Bereitstellungsprozesses angezeigt werden kann. Dies kann nützlich sein, um eine Beschreibung der Lösungen und Dateien bereitzustellen, die im Paket bereitgestellt werden.  

Common Data Service stellt Ihnen eine Visual Studio-Vorlage für die Erstellung dieser Pakete zur Verfügung, die Sie mit dem Package Deployer-Tool verwenden können, um sie in einer Common Data Service-Instanz bereitzustellen.

<a name="Prereq"></a>
 
## <a name="prerequisites"></a>Voraussetzungen  

- Stellen Sie sicher, dass Sie alle Lösungen und Dateien haben, die Sie in Paket einschließen möchten.  
- Microsoft .NET Framework 4.6.2
- Visual Studio 2015 oder Visual Studio 2017
- NuGet Package Manager für [Visual Studio 2015](https://visualstudiogallery.msdn.microsoft.com/5d345edc-2e2d-4a9c-b73b-d53956dc458d)
    - In Visual Studio 2017 werden NuGet und der NuGet-Paket-Manager automatisch installiert, wenn Sie alle .NET-bezogenen Workloads auswählen.
- Microsoft Dynamics CRM SDK-Vorlagen für Visual Studio, die die Paketvorlage enthalten. Sie können es erhalten, indem Sie die [Microsoft Dynamics CRM SDK-Vorlagen](http://go.microsoft.com/fwlink/p/?LinkId=400925) herunterladen und auf die `CRMSDKTemplates.vsix`-Datei doppelklicken, um die Vorlage in Visual Studio zu installieren.  



<a name="HowTo"></a>
   
## <a name="create-a-package"></a>Erstellen Sie ein Paket  

 Führen Sie folgenden fünf Schritte aus, um ein Paket zu erstellen:  

- [Schritt 1: Erstellen Sie ein Projekt mithilfe einer Vorlage](create-packages-package-deployer.md#Step1)  
- [Schritt 2: Fügen Sie Ihre Dateien dem Projekt hinzu](create-packages-package-deployer.md#Step2)  
- [Schritt 3: Aktualisieren der HTML-Dateien](create-packages-package-deployer.md#Step3)  
- [Schritt 4: Geben Sie die Konfigurationswerte für das Paket an](create-packages-package-deployer.md#Step4)  
- [Schritt 5: Definieren Sie benutzerdefinierten Code für das Paket](create-packages-package-deployer.md#Step5)  

<a name="Step1"></a>  
 
#### <a name="step-1-create-a-project-using-the-template"></a>Schritt 1: Erstellen Sie ein Projekt mithilfe einer Vorlage  

1. Starten Sie Visual Studio, und erstellen Sie ein neues Projekt.  
2. Im Dialogfeld **Neues Projekt**: 

   1. Erweitern Sie in der Liste der installierten Vorlagen **Visual C#**, und wählen Sie **Dynamics 365-SDK Vorlagen** aus.  
   2. Stellen Sie sicher, dass **.NET Framework 4.6.2** ausgewählt ist.  
   3. Wählen Sie das **Dynamics 365-Paket** aus.  
   4. Geben Sie den Namen und den Standort des Projekts an, und klicken Sie auf **OK**.  

    ![Neues Projekt zum Erstellen eines benutzerdefinierten Pakets](../media/crm-sdkv6-packagedeployer-01.png)

<a name="Step2"></a>   

#### <a name="step-2-add-your-files-to-the-project"></a>Schritt 2: Fügen Sie Ihre Dateien dem Projekt hinzu  

1.  Fügen Sie im Bereich **Projektmappen-Explorer** die Lösungen und Dateien dem Ordner **PkgFolder** hinzu.  
2.  Setzen Sie für alle Dateien, die Sie unter dem Ordner **PkgFolder**, im Bereich **Eigenschaften**,hinzufügen, den Wert **Kopie zu Ausgabeverzeichnis** auf **Immer kopieren**.  Dadurch wird sichergestellt, dass die Datei, im generierten Paket verfügbar ist.  

<a name="Step3"></a>  
 
#### <a name="step-3-update-the-html-files-english-and-other-languages"></a>Schritt 3: Aktualisieren Sie die HTML-Dateien: Englisch und andere Sprachen  

1.  Im Bereich Projektmappen-Explorer erweitern Sie **PkgFolder** > **Inhalt** > **de-DE**. Sie finden hier zwei Ordner genannt `EndHTML` und `WelcomeHTML`. Diese Ordner enthalten das HTML und die zugeordneten Dateien, mit denen Sie Informationen am Ende und am Anfang des Paketbereitstellungsprozesses anzeigen können. Bearbeiten Sie die Dateien im HTML Ordner dieser Ordner, um Informationen für das Paket hinzuzufügen.  

2.  Sie können in Ihrem Paket auch HTML-Dateien in anderen Sprachen hinzufügen, damit der Inhalt des HTML in der Sprache der Gebietsschemaeinstellungen der Firma des Benutzers angezeigt wird. Um dies zu tun:  

    1.  Erstellen Sie eine Kopie des Ordners **de-DE** unter **PkgFolder** > **Inhalt**.  
    2.  Benennen Sie den kopierten Ordner entsprechend der Sprache. Benennen Sie ihn für die spanische Sprache beispielsweise mit **es-ES**.  
    3.  Ändern Sie den Inhalt der HTML-Dateien, um spanischen Inhalt hinzuzufügen.  

<a name="Step4"></a>   

#### <a name="step-4-specify-the-configuration-values-for-the-package"></a>Schritt 4: Geben Sie die Konfigurationswerte für das Paket an  

1. Definieren Sie die Paketkonfiguration, indem Sie Informationen über das Paket in der Datei **ImportConfig.xml** im **PkgFolder** hinzufügen. Doppelklicken Sie auf die Datei, um sie für die Bearbeitung zu öffnen. Die folgende Liste enthält Informationen zu den Parametern und Knoten in der CONFIG-Datei.  

    `installsampledata`  
    `True` oder `false`. Wenn `true`, werden Beispieldaten auf der Common Data Service-Instanz installiert. Hierbei handelt es sich um dieselben Beispieldaten, die Sie aus dem Bereich **Einstellungen** > **Datenverwaltung** in Common Data Service installieren können.  

    `waitforsampledatatoinstall`  
   **True** oder **False**. Wenn **true** und wenn **installsampledata** ebenfalls auf **true** festgelegt ist, wird darauf gewartet, dass Beispieldaten installiert werden, bevor das Paket bereitgestellt wird.  

   > [!NOTE]
   >  Stellen Sie sicher, dass Sie **installsampledata** auf **true** setzen, wenn Sie `waitforsampledatatoinstall` auf **true** setzen.  

    `agentdesktopzipfile`  
    Dateiname der zu entpacken ZIP-Datei. Wenn Sie einen zip-Dateinamen angeben, wird während des Paketbereitstellungsprozesses ein Bildschirm hinzugefügt, der Sie aufgefordert, einen Speicherort auszuwählen, an dem Sie die Inhalte der Datei entpacken möchten.  

    Dies wird häufig verwendet, um Pakete für Unified Service Desk for Dynamics 365 zu erstellen. Weitere Informationen zu Unified Service Desk finden Sie im [Verwaltungshandbuch für Unified Service Desk 3.0](/dynamics365/customer-engagement/unified-service-desk/administration-guide-unified-service-desk-3).  

    `agentdesktopexename`  
    Name der .exe oder .msi-Datei in der ZIP-Datei oder eine URL, die am Ende des Bereitstellungsprozesses aufgerufen wird.  

    Dies wird häufig verwendet, um Pakete für Unified Service Desk zu erstellen.  

    `crmmigdataimportfile`  
    Dateiname der Standardkonfigurationsdatendatei (ZIP-Datei), exportiert mithilfe des Configuration Migration-Tools.  

   - Sie können eine lokalisierte Version der Konfigurationsdatendatei basierend auf der Gebietsschema-ID (LCID) importieren, die unter Verwendung der neuen Laufzeiteinstellungen angegeben wird, während Package Deployer ausgeführt wird. Verwenden Sie den Knoten `<cmtdatafile>` (später erläutert), um die lokalisierten Versionen der Konfigurationsdatendatei in einem Paket anzugeben, und dann die Methode `OverrideConfigurationDataFileLanguage` (später erläutert), um die Logik für das Importieren der Konfigurationsdatendatei basierend auf der Gebietsschema-ID anzugeben, die mithilfe der Laufzeiteinstellungen angegeben wurde. Sie können nicht mehrere Konfigurationsdatendateien gleichzeitig mithilfe eines Pakets importieren.  

   - Für Common Data Service (lokal): wenn Ihre Konfigurationsdatendatei Benutzerinformation enthält, und sowohl die Quell- als auch die Zielinstanz von Common Data Service in der gleichen Active Directory-Domäne sind, werden Benutzerinformation zur Zielinstanz von Common Data Service importiert. Um Benutzerinformation in eine Common Data Service (lokal)-Instanz auf einer anderen Domäne zu importieren, müssen Sie die Benutzerkartendatei (.xml) in Ihrem Projekt mit einschließen, die unter Verwendung des Konfigurationsmigration-Tools , erzeugt wurde, und sie zusammen mit der Konfigurationsdatendatei unter Verwendung des `usermapfilename`-Attributes im `<cmtdatafile>`-Knoten, der später erklärt wird, angeben. Benutzerinformation können nicht zu Common Data Service-Instanzen importiert werden.  
     `<solutions>` Knoten  
     Enthält ein Array aus `<configsolutionfile>`-Knoten, das die zu importierenden Lösungen beschreibt. Der Reihenfolge der Lösungen unter diesem Knoten gibt die Reihenfolge an, in der die Lösungen auf der Zielinstanz von Common Data Service importiert werden.  

     `<configsolutionfile>` Knoten  
     Verwenden Sie diesen Knoten unter dem `<solutions>` Knoten, um die einzelnen Lösungen und die folgenden Informationen zu spezifizieren, damit jede Lösung importiert werden kann:  

   - `solutionpackagefilename`: Spezifizieren Sie den .zip-Dateinamen Ihrer Lösung. Erforderlich.  

   - `overwriteunmanagedcustomizations`: Spezifizieren Sie, ob alle nicht verwalteten Anpassungen überschrieben werden sollen, wenn Sie eine Lösung importieren, die bereits in der Zielinstanz von Dynamics 365 existiert. Dieses ist optional und wenn Sie nicht dieses Attribut spezifizieren, werden standardmäßig die nicht verwalteten Anpassungen in der vorhandenen Lösung auf dem Ziel Dynamics 365-Instanz aufrechterhalten.  

   - `publishworkflowsandactivateplugins`: Spezifizieren Sie, ob Workflows veröffentlicht und Plug-Ins in der Ziel-Dynamics 365-Instanz nach dem Import der Lösung aktiviert werden sollen. Dieses ist optional und wenn Sie dieses Attribut nicht spezifizieren, werden standardmäßig die Arbeitsflüsse veröffentlicht und Plug-Ins aktiviert, nachdem die Lösung auf der Ziel-Dynamics 365-Instanz importiert ist.  

     Sie können mehrere Lösungsdateinamen in einem Paket hinzufügen, indem Sie genauso viele `<configsolutionfile>` Knoten hinzufügen. Wenn also beispielsweise drei Lösungsdateien importiert werden sollen, fügen Sie sie wie folgt hinzu:  

   ```xml  

   <solutions>  
   <configsolutionfile solutionpackagefilename="SampleSolutionOne_1_0_managed.zip"  
   overwriteunmanagedcustomizations="false"  
   publishworkflowsandactivateplugins="true"/>  
   <configsolutionfile solutionpackagefilename="SampleSolutionTwo_1_0_managed.zip"  
   overwriteunmanagedcustomizations="false"  
   publishworkflowsandactivateplugins="true"/>  
   <configsolutionfile solutionpackagefilename="SampleSolutionThree_1_0_managed.zip" />  
   </solutions>  

   ```  

    `<filestoimportnode>` Knoten  
    Enthält ein Array von `<configimportfile>` und `<zipimportdetails>` Knoten, die verwendet werden, um die einzelnen Dateien und ZIP-Dateien zu beschreiben, die importiert werden.  

    `<configimportfile>` Knoten  
    Verwenden Sie den Knoten unter dem `<configimportfile>`-Knoten, um eine Datei zu beschreiben, die zu Common Data Service importiert wird. Sie können mehrere Dateien in einem Paket hinzufügen, indem Sie genauso viele `<configimportfile>` Knoten hinzufügen.  

   ```xml  

   <filestoimport>  
   <configimportfile filename="File.csv"  
   filetype="CSV"  
   associatedmap="FileMap"  
   importtoentity="FileEntity"  
   datadelimiter=""  
   fielddelimiter="comma"  
   enableduplicatedetection="true"  
   isfirstrowheader="true"  
   isrecordownerateam="false"  
   owneruser=""  
   waitforimporttocomplete="true" />  
   <configimportfile filename="File.zip"  
   filetype="ZIP"  
   associatedmap="FileMapName"  
   importtoentity="FileEntity"  
   datadelimiter=""  
   fielddelimiter="comma"  
   enableduplicatedetection="true"  
   isfirstrowheader="true"  
   isrecordownerateam="false"  
   owneruser=""  
   waitforimporttocomplete="true"/>  

   </filestoimport>  

   ```  

    Dies hat die folgenden Attribute:  

   |Attribut|Beschreibung|
   |--|-|
   |`filename`| Name der Datei, die die importierten Daten enthält. Wenn die Datei eine ZIP-Datei ist, muss ein `<zipimportdetails>` Knoten mit einem     `<zipimportdetail>` Knoten für jede Datei in der in der ZIP-Datei vorhanden sein. |
   |`filetype`|Dies kann csv, xml oder zip sein.          |
   |`associatedmap`|Name der Common Data Service-Importdatenzuordnung, die mit dieser Datei verwendet werden soll. Wenn leer, wird versucht, der vom System bestimmte Importdatenzuordnungsname diese Datei zu verwenden.|
   |`importtoentity`| Dies kann der Name der EXE-Datei in der ZIP-Datei, eine URL oder eine MSI-Datei sein, um einen Link bereitzustellen, der am Ende des Vorgangs aufgerufen wird.|
   |`datadelimiter`| In der Importdatei verwendeter Name des Datentrennzeichens. Gültige Werte sind einfache Anführungszeichen oder doppelte Anführungszeichen.|
   |`fielddelimiter`|In der Importdatei verwendeter Name des Feldtrennzeichens. Gültige Werte sind Komma oder Doppelpunkt oder einfache Anführungszeichen.|
   |`enableduplicatedetection`|Gibt an, ob der Datenimport für Duplikaterkennungsregeln aktiviert wird. Gültige Werte sind **true** oder **false**.|
   |`isfirstrowheader`|Wird verwendet, um zu bezeichnen, dass die erste Zeile der Importdatei die Feldnamen enthält. Gültige Werte sind `true` oder `false`. |
   |`isrecordownerateam`|Gibt an, ob der Besitzer des importierten Datensatzes ein Team sein sollte. Gültige Werte sind `true` oder `false`.|
   |`owneruser`|Gibt die Benutzer-ID an, die die Datensätze besitzen sollte. Der Standardwert ist der aktuell angemeldete Benutzer.  |
   |`waitforimporttocomplete`|Wenn `true`, wartet das System auf den Abschluss des Importvorgangs, bevor fortgesetzt wird. Wenn `false`, werden die Aufträge in Warteschlangen gegeben und es wird fortgesetzt.|

    `<zipimportdetails>` Knoten  
    Dieser Knoten enthält ein Array von `<zipimportdetail>`-Knoten, die die Dateien beschreiben, die in einer ZIP-Datei enthalten sind, die verwendet wird, um zu Dynamics 365 zu importieren.  

    `<zipimportdetail>` Knoten  
    Verwenden Sie den Knoten unter dem `<zipimportdetails>` Knoten, um Informationen zu einer einzelnen Datei in einer ZIP-Datei bereitzustellen, die im `<configimportfile>` Knoten angegeben ist.  

   ```xml  
   <filestoimport>  
   ...  
   ...  
   <zipimportdetails>  
   <zipimportdetail filename="subfile1.csv" filetype="csv" importtoentity="account" />  
   <zipimportdetail filename="subfile2.csv" filetype="csv" importtoentity="contact" />  
   </zipimportdetails>  
   </filestoimport>  

   ```  

    Dies hat die folgenden Attribute:  

   |Attribut|Beschreibung|  
   |---------------|-----------------|  
   |`filename`|Name der Datei, die die importierten Daten enthält.|  
   |`filetype`|Dies kann csv oder xml sein.|  
   |`importtoentity`|Dies kann der Name der EXE-Datei in der ZIP-Datei, eine URL oder eine MSI-Datei sein, um einen Link bereitzustellen, der am Ende des Vorgangs aufgerufen wird.|  

    `<filesmapstoimport>` Knoten  
    Dieser Knoten enthält ein Array von `<configmapimportfile>` Knoten für den Import. Die Reihenfolge der Zuordnungsdateien in diesem Knoten gibt die Reihenfolge an, in der sie importiert werden. Informationen zu Datenzuordnungen, siehe [Datenzuordnungen für Import erstellen](../create-data-maps-for-import.md).  

    `<configimportmapfile>` Knoten  
    Verwenden Sie den Knoten unter dem `<filesmapstoimport>`-Knoten, um Informationen zu einer einzelnen Zuordnungsdatei für den Import in Common Data Service bereitzustellen.  

   ```xml  
   <filesmapstoimport>  
   <configimportmapfile filename="FileMap.xml" />  
   </filesmapstoimport>  
   ```  

    `<cmtdatafiles>` Knoten  
    Dieser Knoten enthält ein Array von `<cmtdatafile>`-Knoten, die die lokalisierten Versionen der Konfigurationsdatendatei enthalten, die importiert werden soll.  

    `<cmtdatafile>` Knoten  
    Verwenden Sie diesen Knoten unter dem `<cmtdatafiles>`-Knoten, um die lokalisierten Konfigurationsdatendateien sowie die Gebietsschema-ID (erforderlich) und die Zuordnungsdatei für Benutzerinformationen (optional) anzugeben. Beispiel:  

   ```xml  
   <cmtdatafiles>  
   <cmtdatafile filename="data_1033.zip" lcid="1033" usermapfilename="UserMap.xml" />  
   <cmtdatafile filename="data_1041.zip" lcid="1041" usermapfilename="" />  
   </cmtdatafiles>  
   ```  

    Sie können Ihre benutzerdefinierte Logik in der `OverrideConfigurationDataFileLanguage`-Methode definieren(später erläutert), um eine lokalisierte Konfigurationsdatendatei zu importieren statt der Standarddatei (angegeben in ), basierend auf dem Wert der Gebietsschema-ID (LCID), der mit den Laufzeiteinstellungen angegeben wird (später erläutert).  

2. Klicken Sie auf **Speichern unter**.  

    Das folgende stellt den Inhalt einer Beispiel `ImportConfig.xml` Datei dar.  

   ```xml  
   <?xml version="1.0" encoding="utf-16"?>  
   <configdatastorage xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
   xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
   installsampledata="true"  
   waitforsampledatatoinstall="true"  
   agentdesktopzipfile=""  
   agentdesktopexename=""  
   crmmigdataimportfile="data_1033.zip">  
   <solutions>  
   <configsolutionfile solutionpackagefilename="SampleSolutionOne_1_0_managed.zip"  
   overwriteunmanagedcustomizations="false"  
   publishworkflowsandactivateplugins="true"/>  
   <configsolutionfile solutionpackagefilename="SampleSolutionTwo_1_0_managed.zip"  
   overwriteunmanagedcustomizations="false"  
   publishworkflowsandactivateplugins="true"/>  
   <configsolutionfile solutionpackagefilename="SampleSolutionThree_1_0_managed.zip" />  
   </solutions>  
   <filestoimport>  
   <configimportfile filename="SampleOption.csv"  
   filetype="CSV"  
   associatedmap="SampleOption"  
   importtoentity="sample_option"  
   datadelimiter=""  
   fielddelimiter="comma"  
   enableduplicatedetection="true"  
   isfirstrowheader="true"  
   isrecordownerateam="false"  
   owneruser=""  
   waitforimporttocomplete="false"/>  
   <configimportfile filename="File.zip"  
   filetype="ZIP"  
   associatedmap="FileMapName"  
   importtoentity="FileEntity"  
   datadelimiter=""  
   fielddelimiter="comma"  
   enableduplicatedetection="true"  
   isfirstrowheader="true"  
   isrecordownerateam="false"  
   owneruser=""  
   waitforimporttocomplete="true"/>  
   <zipimportdetails>  
   <zipimportdetail filename="subfile1.csv"  
   filetype="csv"  
   importtoentity="account" />  
   <zipimportdetail filename="subfile2.csv"  
   filetype="csv"  
   importtoentity="contact" />  
   </zipimportdetails>  
   </filestoimport>  
   <filesmapstoimport>  
   <configimportmapfile filename="SampleOption.xml" />  
   </filesmapstoimport>  
   <cmtdatafiles>  
   <cmtdatafile filename="data_1033.zip"  
   lcid="1033"  
   usermapfilename="UserMap.xml" />  
   <cmtdatafile filename="data_1041.zip"  
   lcid="1041"  
   usermapfilename="" />  
   </cmtdatafiles>  
   </configdatastorage>  

   ```  

<a name="Step5"></a>  
 
#### <a name="step-5-define-custom-code-for-your-package"></a>Schritt 5: Definieren Sie benutzerdefinierten Code für das Paket  

1. Doppelklicken Sie im Projektmappen-Explorer-Bereich auf die Datei **PackageTemplate.cs** im Stammverzeichnis, um sie zu bearbeiten.  

2. In der PackageTemplate.cs-Datei können Sie:  

   1. Geben Sie benutzerdefinierten Code ein, der ausgeführt wird, wenn das Paket in der Definition der Überschreibenmethode von `InitializeCustomExtension` initialisiert wird.  

       Diese Methode kann angewendet werden, um Benutzer die Ablaufparameter beim Ausführen eines Pakets verwenden zu lassen. Als Entwickler können Sie Unterstützung für jeden Ablaufparameter Ihrem Paket hinzufügen, indem Sie die Eigenschaft <xref:Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.IImportExtensions2.RuntimeSettings> verwenden, solange Sie Code haben, zum sie basierend auf den Benutzereingaben zu verarbeiten.  

       Zum Beispiel ermöglicht der folgende Beispielcode einem Ablaufparameter namens `SkipChecks` für das Paket, der zwei mögliche Werte hat: true oder false. Die Beispielcode prüft, ob der Benutzer irgendwelche Ablaufparameter beim Ausführen von Package Deployer angegeben hat (entweder per Befehlszeile oder per PowerShell) und verarbeitet die Informationen dann entsprechend. Wenn kein Ablaufparameter vom Benutzer beim Ausführen des Pakets spezifiziert wird, ist der Wert der Eigenschaft <xref:Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.IImportExtensions2.RuntimeSettings> gleich null.  

      ```csharp  
      public override void InitializeCustomExtension()  
      {  
      // Do nothing.  

      // Validate the state of the runtime settings object.  
      if (RuntimeSettings != null)  
      {  
      PackageLog.Log(string.Format("Runtime Settings populated.  Count = {0}", RuntimeSettings.Count));  
      foreach (var setting in RuntimeSettings)  
      {  
      PackageLog.Log(string.Format("Key={0} | Value={1}", setting.Key, setting.Value.ToString()));  
      }  

      // Check to see if skip checks is present.  
      if ( RuntimeSettings.ContainsKey("SkipChecks") )  
      {  
      bool bSkipChecks = false;  
      if (bool.TryParse((string)RuntimeSettings["SkipChecks"], out bSkipChecks))  
      OverrideDataImportSafetyChecks = bSkipChecks;  
      }  
      }  
      else  
      PackageLog.Log("Runtime Settings not populated");  
      }  
      ```  

       Dadurch kann der Administrator die Eingabeaufforderung oder das [Import-CrmPackage](/powershell/module/microsoft.xrm.tooling.packagedeployment/import-crmpackage)-Cmdlet verwenden, um anzugeben, ob die Sicherheitsprüfungen beim Ausführen des Package Deployer-Tools zum Importieren des Pakets übersprungen werden sollen. Weitere Informationen: [Bereitstellen von Paketen mit Dynamics 365 Package Deployer und Windows PowerShell](/dynamics365/customer-engagement/admin/deploy-packages-using-package-deployer-windows-powershell)  

   2. Geben Sie kundenspezifischen Code ein, der ausgeführt wird, bevor die Lösungen in die Definition der Überschreibungsmethode von `PreSolutionImport` importiert werden, um zu spezifizieren, ob Anpassungen bei der Aktualisierung der spezifizierten Lösung in einer Zielinstanz von Common Data Service beibehalten oder überschrieben werden sollen, und ob Plug-Ins und Arbeitsflüsse automatisch aktiviert werden.  

   3. Verwenden Sie die Außerkraftsetzungsmethodendefinition von `RunSolutionUpgradeMigrationStep`, um Datenumwandlung oder Aktualisierung zwischen zwei Versionen einer Lösung auszuführen. Diese Methode wird nur aufgerufen, sofern die Lösung, die Sie importieren, in der Common Data Service-Zielinstanz bereits vorhanden ist.  

        Diese Funktion erwartet die folgenden Parameter:  

        |    Parameter    |            Beschreibung             |
        |-----------------|------------------------------------|
        | `solutionName`  |        Der Name des Lösungsherausgebers.        |
        |  `oldVersion`   | Versionsnummer der alten Lösung |
        |  `newVersion`   | Versionsnummer der neuen Lösung |
        | `oldSolutionId` |     GUID der alten Lösung.      |
        | `newSolutionId` |     GUID der neuen Lösung.      |


   4. Geben Sie benutzerdefinierten Code ein, der ausgeführt wird, bevor der Lösungsimport abgeschlossen wird, in der Überschreibungsdefinition der Methode `BeforeImportStage`. Die Beispieldaten und einige Textdateien für die Lösungen, die in der Datei `ImportConfig.xml` spezifiziert werden, werden importiert, bevor der Lösungsimport abschließt.  

   5. Überschreiben Sie die gegenwärtig-vorgewählte Sprache für Konfigurationsdatenimport unter Verwendung der Überschreibungsmethodendefinition von `OverrideConfigurationDataFileLanguage`. Wenn die spezifizierte Gebietsschema-ID (LCID) der angegebenen Sprache nicht in der Liste von verfügbaren Sprachen im Paket gefunden wird, wird die Standarddatendatei importiert.  

       Sie spezifizieren die verfügbaren Sprachen für die Konfigurationsdaten im `<cmtdatafiles>` Knoten in der `ImportConfig.xml` Datei. Die Standard-Konfigurationsdaten-Importdatei wird im Attribut `crmmigdataimportfile` in der Datei `ImportConfig.xml` spezifiziert.  

       Überspringen der Datenfehler (<xref:Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.IImportExtensions2.OverrideDataImportSafetyChecks> = wahr) kann hier effektiv sein, wenn Sie sicher sind, dass die Common Data Service-Zielinstanz keine Daten enthält.  

   6. Geben Sie benutzerdefinierten Code ein, der ausgeführt wird, nachdem der Import abgeschlossen wird, in der Überschreibungsdefinition der Methode `AfterPrimaryImport`. Die restlichen Textdateien, die nicht früher importiert wurden, bevor der angestellte Lösungsimport, werden jetzt importiert.  

   7. Ändern Sie den Standardnamen Ihres PkgFolder auf den Paketnamen, den Sie wünschen. Benennen Sie dazu den `PkgFolder`>Ordner im Bereich **Projektmappen-Explorer** um, und bearbeiten Sie dann den Rückgabewert unter der `GetImportPackageDataFolderName` Eigenschaft.  

      ```csharp  
      public override string GetImportPackageDataFolderName  
      {  
      get  
      {  
      // WARNING this value directly correlates to the folder name in the Solution Explorer where the ImportConfig.xml and sub content is located.  
      // Changing this name requires that you also change the correlating name in the Solution Explorer  
      return "PkgFolder";  
      }  
      }  
      ```  

   8. Ändern Sie den Paketnamen, indem Sie den Rückgabewert unter der `GetNameOfImport` Eigenschaft bearbeiten.  

      ```csharp  
      public override string GetNameOfImport(bool plural)  
      {  
      return "Package Short Name";  
      }  
      ```  

       Dies ist der Name des Pakets, der auf der Paketauswahlseite im Dynamics 365 Package Deployer-Assistenten angezeigt wird.  

   9. Ändern Sie die Paketbeschreibung, indem Sie den Rückgabewert unter der `GetImportPackageDescriptionText` Eigenschaft bearbeiten.  

       ```csharp  

       public override string GetImportPackageDescriptionText  
       {  
       get { return "Package Description"; }  
       }  

       ```  

        Dies ist die Paketbeschreibung, die neben dem Paketnamen auf der Paketauswahlseite Package Deployer-Assistenten angezeigt wird.  

   10. Ändern Sie den langen Paketnamen, indem Sie den Rückgabewert unter der `GetLongNameOfImport` Eigenschaft bearbeiten.  

       ```csharp  

       public override string GetLongNameOfImport  
       {  
       get { return "Package Long Name"; }  
       }  

       ```  

        Der lange Paketname wird auf der nächsten Seite angezeigt, nachdem Sie das zu installierende Paket ausgewählt haben.  

3. Darüber hinaus sind die folgenden Funktionen und die Variablen für das Paket verfügbar:  


   |Name|Typ|Beschreibung|
   |--|--|--|
   |<xref:Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.ImportExtension.CreateProgressItem(System.String)> |Funktion|Wird verwendet, um ein neues Statuselement in der Benutzeroberfläche (UI) zu erstellen. |
   |<xref:Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.ImportExtension.RaiseUpdateEvent(System.String,Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.ProgressPanelItemStatus)> |Funktion| Wird verwendet, um den Status zu aktualisieren, der beim Aufruf von <xref:Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.ImportExtension.CreateProgressItem(System.String)> erstellt wird.<br /><br /> <xref:Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.ProgressPanelItemStatus> ist eine Enumeration mit folgenden Werte:<br /><br /> Arbeit = 0<br />Abgeschlossen = 1<br />Fehler = 2<br />Warnung = 3<br />Unbekannt = 4 |
   |<xref:Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.ImportExtension.RaiseFailEvent(System.String,System.Exception)>|Funktion|Wird verwendet, um den Import des aktuellen Status mit einer Ausnahmebedingungsnachricht fehlschlagen zu lassen.|
   |<xref:Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.ImportExtension.IsRoleAssoicatedWithTeam(System.Guid,System.Guid)>|Funktion|Wird verwendet, um zu ermitteln, ob eine Rolle einem bestimmten Team zugeordnet ist.|
   |<xref:Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.ImportExtension.IsWorkflowActive(System.Guid)>|Funktion|Wird verwendet, um zu bestimmen, ob ein angegebener Workflow aktiv ist. |
   |<xref:Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.ImportExtension.PackageLog>| Klassenzeiger|Dies ist ein Zeiger auf die initialisierte Protokollierungs-Schnittstelle für das Paket. Diese Schnittstelle wird von einem Paket verwendet, um Nachrichten und Ausnahmen in der Paketprotokolldatei zu protokollieren.|
   |<xref:Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.ImportExtension.RootControlDispatcher>|Eigenschaft|Dies ist eine Verteilerschnittstelle, die verwendet wird, um dem Steuerelement zu ermöglichen, während der Paketbereitstellung eine eigene Benutzeroberfläche zu rendern. Sie verwenden diese Schnittstelle, um beliebige UI-Elemente oder -Befehle einzubinden. Es ist wichtig, diese Variable vor der Nutzung auf NULL-Werte zu prüfen, da sie auf einen Wert festgelegt sein können, oder nicht.  |
   |<xref:Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.ImportExtension.CrmSvc>|Eigenschaft |Dies ist ein Zeiger auf die <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>-Klasse, die es einem Paket ermöglicht, aus dem Paket heraus Dynamics 365 zu adressieren. Diese Klasse wird verwendet, um SDK-Methoden und weitere Aktionen in den überschriebenen Methoden auszuführen.|
   |<xref:Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.IImportExtensions2.DataImportBypass> |Eigenschaft|Verwenden Sie dies, um zu spezifizieren, ob Dynamics 365 Package Deployer alle Datenimport-Operationen überspringt, wie Import von Common Data Service-Beispieldaten, von Textdateien und von Daten, die vom Konfigurationsmigration-Tool exportiert werden. Geben Sie true oder false an. Der Standardwert ist `false`.|
   | <xref:Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.IImportExtensions2.OverrideDataImportSafetyChecks> |Eigenschaft|Verwenden Sie dieses, um zu spezifizieren, ob Dynamics 365 Package Deployer einige seiner Sicherheitskontrollen überspringt, was hilft, die Importleistung zu verbessern. Geben Sie `true` oder `false` an. Der Standardwert ist `false`.<br /><br /> Sie sollten dieses nur dann auf `true` setzen, wenn die Common Data Service-Zielinstanz keine Daten enthält.|


4. Speichern Sie Ihr Projekt, und bauen Sie es auf (**Aufbauen** > **Lösung aufbauen**), um das Paket zu erstellen. Ihr Paket ist die folgenden Dateien unter dem *\<Project>* \Bin\Debug-Ordner  

   - **\<PackageName> Ordner**: Der Ordnername ist derselbe, den Sie für Ihren Paketordnernamen im Schritt 2.g dieses Abschnitts geändert haben (Schritt 5: Definieren Sie benutzerdefinierten Code für Ihr Paket). Dieser Ordner enthält alle Lösungen, Konfigurationsdateien, Textdateien und Inhalte für Ihr Paket.  

   - **\<PackageName>.dll**: Die Assembly enthält den benutzerdefinierten Code für das Paket. Standardmäßig ist der Name der Assemblys identisch mit Visual Studio-Projektname.  

     Der nächste Schritt ist, Ihr Paket bereitzustellen.  

<a name="UsethePackage"></a> 
  
## <a name="deploy-a-package"></a>Ein Paket bereitstellen  

 Nachdem Sie ein Paket erstellt haben, können Sie es auf der Common Data Service-Instanz bereitstellen, indem Sie entweder das Package Deployer-Tool oder Windows PowerShell verwenden. 

 Das Package Deployer-Tool wird bereitgestellt als Teil des [Microsoft.CrmSdk.XrmTooling.PackageDeployment.WPF](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.PackageDeployment) NuGet-Pakets. Zum Herunterladen des Package Deployer Tools, siehe [Herunterladen von Tools von NuGet](../download-tools-nuget.md).

 Ausführliche Informationen finden Sie unter [Pakete mit Dynamics 365-Package Deployer oder Windows PowerShell bereitstellen](/dynamics365/customer-engagement/admin/deploy-packages-using-package-deployer-windows-powershell).  

<a name="BestPractices"></a>   

## <a name="best-practices-for-creating-and-deploying-packages"></a>Bewährte Methoden zum Erstellen und Bereitstellen von Paketen  

Beim Erstellen von Paketen, müssen Entwickler sicherstellen, dass die Paketassemblys signiert sind.  

Beim Bereitstellen der Pakete müssen Common Data Service-Administratoren Folgendes durchführen:  

- Auf einer signierten Paketassembly bestehen, damit Sie eine Assembly bis zu ihrer Quelle zurück nachverfolgen können.  
- das Paket auf einer Vor-Produktionsinstanz testen, (vorzugsweise als Spiegelbild der Produktionsinstanz), bevor sie in einer Produktionsinstanz ausgeführt wird.  
- Eine Sicherungskopie der Produktionsinstanz erstellen, bevor das Paket bereitgestellt wird.  



