---
title: Öffnen von Dialogfeldern, Formularen, Ansichten und Berichten mit einer URLs (modellgestützte Apps) | Microsoft Docs
description: Erfahren Sie mehr zu URL-adressierbaren Elementen, mit denen Sie Links in Formulare, Ansichten, Dialogfelder und Berichten in anderen Anwendungen einfügen können.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c2176e4915970f214a8c74fa8c4f1ac61fd81f53
ms.sourcegitcommit: 6c73e316f866af6a34619f95a5ac64ad1664b48a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "3326444"
---
# <a name="open-forms-views-dialogs-and-reports-with-a-url"></a>Öffnen von Formularen, Ansichten, Dialogen und Berichten mit einer URL

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/open-forms-views-dialogs-reports-url -->

Mit URL-adressierbaren Elementen können Sie Links zu Formularen, Ansichten, Dialogfeldern und Berichten in andere Anwendungen einfügen. Auf diese Art und Weise können Sie andere Anwendungen, Berichte oder Websites einfach erweitern, sodass die Benutzer Informationen anzeigen und Aktionen ausführen können, ohne die Anwendungen zu wechseln.  

> [!NOTE]
> - Über URL adressierbare Formulare, Ansichten, Dialoge und Berichte können die Sicherheit nicht umgehen. Nur lizenzierte Benutzer können, basierend auf ihren Sicherheitsrollen, auf die angezeigten Datensätze und Daten zugreifen.  
>   -   Verwenden Sie `Xrm.Navigation.`[openForm](clientapi/reference/Xrm-Navigation/openForm.md), wenn Sie Entitätsformulare programmgesteuert in der Anwendung öffnen, indem Sie Webressourcen verwenden. Verwenden Sie nicht `window.open`.  
>   -   Verwenden Sie außerhalb der Anwendung, wo Seiten keinen Zugriff auf die Funktion `Xrm.Navigation.`[openForm](clientapi/reference/Xrm-Navigation/openForm.md) haben, `window.open` oder einen Link, um einen bestimmten Datensatz oder ein bestimmtes Formular für eine Entität zu öffnen.  

<a name="BKMK_URLAddressableFormsAndViews"></a>

## <a name="url-addressable-forms-and-views"></a>Über URL adressierbare Formulare und Ansichten

 Alle Entitätsformulare und -ansichten werden in der main.aspx-Seite angezeigt. Abfragezeichenfolgen-Parameter, die an dieses Seitensteuerelement übergeben wurden, werden angezeigt. Beispiel:  

<!-- To open a new account entity record form for on-premises [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)]:  
 ```  
https://mycrm/myOrg/main.aspx?etn=account&pagetype=entityrecord  
 ```  -->

 So öffnen Sie ein Entitätsdatensatzformular des Kontos für die ID {91330924-802A-4B0D-A900-34FD9D790829}:  
 ```  
https://myorg.crm.dynamics.com/main.aspx?etn=account&pagetype=entityrecord&id=%7B91330924-802A-4B0D-A900-34FD9D790829%7D  
 ```  

 So öffnen Sie die Ansicht **Geschlossene Verkaufschancen**:  
 ```  
https://myorg.crm.dynamics.com/main.aspx?etn=opportunity&pagetype=entitylist&viewid=%7b00000000-0000-0000-00AA-000010003006%7d&viewtype=1039  
 ```  

 So öffnen Sie die Ansicht **Aktive Kontakte** ohne Navigations- oder Befehlsleiste  
 ```  
https://myorg.crm.dynamics.com/main.aspx?etn=contact&pagetype=entitylist&viewid={00000000-0000-0000-00AA-000010001004}&viewtype=1039&navbar=off&cmdbar=false  
 ```  

> [!NOTE]
>  Das Öffnen von Entitätsformularen in einem Dialogfenster mithilfe von [showModalDialog](https://msdn.microsoft.com/library/ie/ms536759.aspx) oder [showModelessDialog](https://msdn.microsoft.com/library/ie/ms536761.aspx) wird nicht unterstützt.  
>   
>  Beim Anzeigen eines Entitätsformulars mit einem IFrame, der eingebettet in einem anderen Entitätsformular ist, wird nicht unterstützt.  

 Sie können in der Regel die [getClientUrl](clientapi/reference/Xrm-Utility/getGlobalContext/getClientUrl.md)-Methode verwenden, um die URL des Organisationsstamms für modellgestützte Apps abzurufen.  

<a name="BKMK_QueryStringParametersForMainForm"></a>   
### <a name="query-string-parameters-for-the-mainaspx-page"></a>Abfragezeichenfolgen-Parameter für die main.aspx-Seite  

> [!TIP]
>  Um den ID-Wert für einen Datensatz zu erhalten, verwenden Sie die Schaltfläche **Link senden** in der Befehlsleiste. Im Folgenden finden Sie ein Beispiel dafür, was in der E-Mail-Anwendung geöffnet wird:  
>   
>  `<https://mycrm/myOrg/main.aspx?etc=4&id=%7b899D4FCF-F4D3-E011-9D26-00155DBA3819%7d&pagetype=entityrecord>`.  
>   
>  Der ID-Parameter, der an die URL übergeben wird, ist der codierte ID-Wert für den Datensatz. In diesem Beispiel lautet der ID-Wert `{899D4FCF-F4D3-E011-9D26-00155DBA3819}`. Die codierte Version der GUID ersetzt die öffnenden und schließenden Klammern “{” und “}” durch “%7B” bzw. “%7D”.  

 Die folgenden Abfragezeichenfolgen-Parameter werden mit der main.aspx-Seite verwendet, um Entitätsformulare oder -ansichten zu öffnen:  


|  Parameter   |                                                                                                                                                                                                                                                                                                                                            Beschreibung                                                                                                                                                                                                                                                                                                                                            |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   **etn**    |                                                                                                                                                                                                                                    Der logische Name der Entität. **Wichtig:** Verwenden Sie nicht den **etc** (Entitätstypcode)-Parameter, der einen ganzzahligen Code für die Entität enthält. Dieser ganzzahlige Code für benutzerdefinierte Entitäten kann sich in den verschiedenen Organisationen unterscheiden.                                                                                                                                                                                                                                     |
| **extraqs**  |     Optional für Formulare. Dieser Parameter enthält codierte Parameter innerhalb dieses Parameters.<br /><br /> Verwenden Sie diesen Parameter, um Werte an ein Formular zu übergeben. Weitere Informationen finden Sie unter [Legen Feldwerte unter Verwendung der Parameter festgelegt, die an ein Formular übergeben wurden](set-field-values-using-parameters-passed-form.md).<br /><br /> Wenn eine Entität über mehr als ein Formular verfügt, können Sie diesen Parameter verwenden, um anzugeben, welches Formular geöffnet werden soll, indem Sie den codierten Parameter `formid` mit einem Wert übergeben, der dem ID-Wert des Formulars entspricht. Wenn Sie beispielsweise ein Formular mit der ID ‘6009c1fe-ae99-4a41-a59f-a6f1cf8b9daföffnen möchten, geben Sie diesen Wert `extraqs`im Parameter `formid%3D6009c1fe-ae99-4a41-a59f-a6f1cf8b9daf%0D%0A` an: .     |
| **pagetype** |                                                                                                                                                                                                                                                        Der Typ der Seite. Es gibt zwei mögliche Werte:<br /><br /> - **entityrecord**<br />     Zeigt ein Entitätsdatensatzformular an.<br />- **entitylist**<br />     Zeigt eine Entitätsansicht an.                                                                                                                                                                                                                                                         |
|    **id**    |                                                                                                                                                                      Optional für Formulare. Verwenden Sie diese Option, wenn Sie einen bestimmten Datensatz öffnen möchten. Übergeben Sie den codierten GUID-Bezeichner für die Entität. Die codierte Version der GUID ersetzt die öffnenden und schließenden Klammern “{“ und “}” durch “%7B” bzw. “%7D” für Beispiel `{91330924-802A-4B0D-A900-34FD9D790829}` ist `%7B91330924-802A-4B0D-A900-34FD9D790829%7D`.                                                                                                                                                                      |
|  **viewid**  |                                                                                                                                                                                                        Erforderlich für Ansichten. Dies ist die ID des `savedquery`- oder `userquery`-Datensatzes, der die Ansicht definiert. Die einfachste Möglichkeit, die URL für eine Ansicht zu erhalten, ist sie zu kopieren. Weitere Informationen finden Sie unter [Kopieren der URL für eine Ansicht](open-forms-views-dialogs-reports-url.md#BKMK_CopyViewURL).                                                                                                                                                                                                         |
| **viewtype** |                                                                                                                                                                                                        Definiert den Typ der Ansicht. Verfügbare mögliche Werte:<br /><br /> - **1039**<br />     Verwenden Sie diesen Wert für eine Systemansicht. Die `viewid` stellt die ID eines `savedquery`-Datensatzes dar.<br />- **4230**<br />     Verwenden Sie diesen Wert für eine persönliche Ansicht. Die `viewid` stellt die ID eines `userquery`-Datensatzes dar.                                                                                                                                                                                                         |
|   `navbar`   | Steuert, ob die Navigationsleiste angezeigt wird und ob Anwendungsnavigation über die in der Siteübersicht definierten Bereiche und Unterbereiche verfügbar ist.<br /><br /> -   `on`<br />     Die Navigationsleiste wird angezeigt. Dies ist das Standardverhalten, wenn der Parameter `navbar` nicht verwendet wird.<br />-   `off`<br />     Die Navigationsleiste wird nicht angezeigt. Benutzer können andere Benutzeroberflächenelemente oder die Schaltflächen Zurück und Weiter für die Navigation verwenden.<br />-   `entity`<br />     In einem Entitätsformular sind nur die Navigationsoptionen für verknüpfte Entitäten verfügbar. Nach der Navigation zu einer verknüpften Entität wird die Schaltfläche Zurück in der Navigationsleiste angezeigt, mit der Sie zum ursprünglichen Datensatz zurückkehren können. |
|   `cmdbar`   |                                                                                                                Steuert, ob die Befehlsleiste angezeigt wird. **Hinweis:**  Diese Funktion unterstützt die Anforderungen für die Unified Service Desk-Anwendung. Die Verwendung, um eine Entität in einem IFrame anzuzeigen, das eingebettet in einem anderen Entitätsformular ist, wird nicht unterstützt. <br /><br /> -   `true`<br />     Die Befehlsleiste wird angezeigt. Dies ist die Standardeinstellung.<br />-   `false`<br />     Die Befehlsleiste wird ausgeblendet.                                                                                                                |

<a name="BKMK_CopyViewURL"></a>   

### <a name="copy-the-url-for-a-view"></a>Kopieren der URL für eine Ansicht  
 Bei vielen Ansichten in modellbasierten Apps kann ein Benutzer die URL für eine bestimmte Ansicht kopieren oder eine E-Mail mit der URL für eine bestimmte Ansicht senden, die in der Nachricht eingebettet ist. Diese Funktion vereinfacht die Kommunikation zwischen Benutzern und ermöglicht es Ihnen, auf eine URL für eine Ansicht zuzugreifen, die Benutzer in einer anderen Anwendung, z. B. in einer SharePoint-Website, einschließen können.  

> [!NOTE]
>  Verwenden Sie diese URL nicht, um die Ansicht in der Anwendungsnavigation mithilfe der Siteübersicht einzuschließen. Informationen hierzu finden Sie unter [Anzeigen einer Ansicht in der Anwendungsnavigation mithilfe der Siteübersicht](open-forms-views-dialogs-reports-url.md#BKMK_DisplayViewInApplicationUsingSiteMap).  

 Die Seite, die durch die URL angezeigt wird, umfasst die vollständige Ansicht. Hierzu zählen das Menüband, jedoch nicht die Anwendungsnavigation.  

##### <a name="get-the-url-for-a-view"></a>Abrufen der URL für eine Ansicht  

1. Öffnen Sie die Ansicht, die Sie verwenden möchten.  

2. Klicken Sie in der Befehlsleiste auf **Aktionen** und klicken Sie dann auf **Link per E-Mail senden**.  

3. Fügen Sie den Link in Notepad ein, und bearbeiten Sie ihn, um nur den URL-Teil des gewünschten Textes zu extrahieren.  

> [!NOTE]
> - Ansichten, die den Benutzerkontext als Parameter verwenden, beispielsweise **Meine Konten**, können nicht kopiert werden.  
>   - Die GUID, die Systemansichten für Systementitäten darstellt, ist bei jeder Installation gleich. Die GUID für benutzerdefinierte Entitäten und benutzerdefinierte Ansichten ist für jede Installation von  eindeutig.  

<a name="BKMK_DisplayViewInApplicationUsingSiteMap"></a>  

### <a name="display-a-view-in-the-application-navigation-using-the-site-map"></a>Anzeigen einer Ansicht in der Anwendungsnavigation mithilfe der Siteübersicht  

Wenn Sie die Anwendungsnavigation mithilfe der Siteübersicht anpassen, verwenden Sie nicht die Ansicht-URL, die Sie aus der Anwendung mithilfe der Schritte in [Kopieren der URL für eine Ansicht](open-forms-views-dialogs-reports-url.md#BKMK_CopyViewURL) kopiert haben, um die URL festzulegen.
Mit dieser URL wird eine Seite angezeigt, die das Menüband enthält und zu unerwünschten Ergebnissen führt, wenn sie in einem `<SubArea>`-URL-Attribut verwendet wird.  

Wenn Sie eine Liste von Entitätsdatensätzen innerhalb der Anwendung für einen Unterbereich anzeigen möchten, legen Sie den Entitätsattributwert fest. Dadurch wird die standardmäßige Ansicht für diese Entität mit dem richtigen Titel und Symbol angezeigt.  

Wenn Sie jedoch ein SubArea-Element wünschen, das eine bestimmte Standard-Anfangsansicht verwendet, verwenden Sie folgendes URL-Muster.  

```xml  
Url=“/_root/homepage.aspx?etn=<entity logical name >&amp;viewid=%7b<GUID value of view id>%7d”  
```  

 Wenn Sie diese URL verwenden, müssen Sie außerdem entsprechende Werte für `<Titles>` und `<Descriptions>` sowie ein Symbol für die Entität angeben.  

> [!NOTE]
> Wenn Sie die Ansicht mithilfe der `/_root/homepage.aspx`-Seite angeben, wird die Ansichtsauswahl weiterhin angezeigt. Wenn der Benutzer die Ansicht ändert, merkt sich die modellgestützte App die aktuellste Auswahl des Benutzers, und die Standard-Anfangsansicht wird angezeigt, nachdem der Benutzer den Browser geschlossen und erneut geöffnet hat.  

<a name="BKMK_OpenADialogProcess"></a>   

## <a name="opening-a-dialog-process-by-using-a-url"></a>Öffnen eines Dialogprozess durch Verwendung einer URL

Eine gebräuchliche Anpassung besteht darin, einem Benutzer die Möglichkeit zu geben, einen bestimmten Dialogprozess im Kontext eines bestimmten Datensatzes zu öffnen. Beispielsweise können Sie eine benutzerdefinierte Schaltfläche zum Menüband für eine bestimmte Entität mithilfe des ID-Werts für den aktuellen Datensatz als Eingabeparameter für den Dialogprozess hinzufügen.  

Zum Öffnen eines Dialogs ist Folgendes erforderlich:  

-   Der eindeutige Bezeichner für den Dialog.  

-   Der logische Name für die Entität, für die der Dialog erstellt wird.  

-   Der eindeutige Bezeichner für den Datensatztyp, für den der Dialog ausgeführt werden soll.  

> [!TIP]
>  Um den eindeutigen Bezeichner für den Dialog abzurufen, navigieren Sie zu **Einstellungen**, und wählen Sie in der Standardlösung **Prozesse** aus. Wählen Sie einen Prozess aus, und wählen Sie anschließend in den Optionen unter **Aktionen** in der Befehlsleiste **Link kopieren** aus. Dadurch wird ein Link zum Bearbeiten des Dialogfelds in die Zwischenablage kopiert, beispielsweise *[Organisations-URL]*`/sfa/workflow/edit.aspx?id=%7b6A6E93C9-1FE6-4C07-91A9-E0E2A7C70976%7d`.  

 Das folgende Beispiel zeigt die URL und Abfragezeichenfolgen-Parameter zum Öffnen eines Dialogs:  

```
[organization url]/cs/dialog/rundialog.aspx?DialogId=[dialog unique identifier]&EntityName=[entity logical name]&ObjectId=[unique identifier for the record]  
```  

 Wenn Sie beispielsweise den Dialog mit ID = {6A6E93C9-1FE6-4C07-91A9-E0E2A7C70976} mit der Firmendatensatz-ID öffnen = {40C9ADFD-90A8-DF11-840E-00155DBA380F}, verwenden Sie die URL im folgenden Beispiel.  

```
[organization url]/cs/dialog/rundialog.aspx?DialogId=%7b6A6E93C9-1FE6-4C07-91A9-E0E2A7C70976%7d&EntityName=account&ObjectId=%7b40C9ADFD-90A8-DF11-840E-00155DBA380F%7d  
```  

> [!TIP]
>  Wenn ein Dialogprozess über einen Link geöffnet wird, funktioniert bei anderen Webbrowsern als Internet Explorer die Schaltfläche **Fertig stellen** unter Umständen nicht. Die Daten werden gespeichert, aber der Benutzer muss im Fenster auf die Schaltfläche **Schließen** klicken, um es zu schließen. Dies liegt daran, dass andere Browser keine `window.close`-Methode bereitstellen, wenn das Fenster nicht mithilfe von JavaScript von einem anderen Fenster geöffnet wird. Verwenden Sie nach Möglichkeit JavaScript und die `window.open`-Methode, um Dialogprozesse zu öffnen, statt nur Links zur Verfügung zu stellen.  

 Sie können eine JavaScript-Funktion erstellen, um den Dialog wie im folgenden Beispiel gezeigt zu öffnen:  

```javascript  
function openDialogProcess(dialogId, entityName, objectId)  
{  
 var url = Xrm.Page.context.getClientUrl() +  
  "/cs/dialog/rundialog.aspx?DialogId=" +  
  dialogId + "&EntityName=" +  
  entityName + "&ObjectId=" +  
  objectId;  
 window.open(url);  
}  
```  

<a name="BKMK_OpenReportWithURL"></a>   
## <a name="opening-a-report-by-using-a-url"></a>Öffnen eines Berichts durch Verwendung einer URL  
 Sie können einen Bericht öffnen, indem Sie die entsprechenden Parameterwerte an die folgende URL übergeben: `[organization url]/crmreports/viewer/viewer.aspx`.  

 Diese URL akzeptiert die folgenden Parameter:  

 **action**  
 Zwei mögliche Werte für diesen Parameter lauten `run` oder `filter`. Wenn `run` verwendet wird, wird der Bericht mit den Standardfiltern angezeigt. Wenn `filter` verwendet wird, zeigt der Bericht einen Filter an, den der Benutzer bearbeiten kann, bevor er auf die Schaltfläche **Bericht ausführen** klickt, um den Bericht anzuzeigen.  

 **helpID**  
 Dieser Parameter ist optional. Bei Berichten, die in modellbasierten Apps enthalten sind, erlaubt der Wert in diesem Parameter, dass die Schaltfläche **Hilfe** den entsprechenden Inhalt über diesen Bericht anzeigt, wenn **Hilfe auf dieser Seite** gewählt wird. Der Wert sollte dem `FileName`-Attributwert des Berichts entsprechen.  

 **id**  
 Dieser Parameter ist der `ReportId`-Attributwert des Berichts.  

 Die folgenden Beispiele zeigen URLs, die zum Öffnen von Berichten in modellbasierten Apps verwendet werden können.  

 Öffnen Sie den Bericht **Vernachlässigte Anfragen** mithilfe des Standardfilters:  
 ```  
 [organization url]/crmreports/viewer/viewer.aspx?action=run&helpID=Neglected%20Cases.rdl&id=%7b8c9f3e6f-7839-e211-831e-00155db7d98f%7d  
 ```  

 Öffnen Sie den Bericht **Topauswahl - Wissensdatenbankartikel**, und fordern Sie den Benutzer auf, Filterwerte festzulegen:  
 ```  
 [organization url]/crmreports/viewer/viewer.aspx?action=filter&helpID=Top%20Knowledge%20Base%20Articles.rdl&id=%7bd84ec390-7839-e211-831e-00155db7d98f%7d  
 ```  

 Die folgende Funktion zeigt, wie Werte in der URL ordnungsgemäß codiert werden:  

```javascript  
function getReportURL(action,fileName,id) {  
 var orgUrl = GetGlobalContext().getClientUrl();  
 var reportUrl = orgUrl +   
  "/crmreports/viewer/viewer.aspx?action=" +  
  encodeURIComponent(action) +  
  "&helpID=" +  
  encodeURIComponent(fileName) +  
  "&id=%7b" +  
  encodeURIComponent(id) +  
  "%7d";  
 return reportUrl;  
}  
```  

### <a name="see-also"></a>Siehe auch   

 [Festlegen von Feldwerten mithilfe von Parametern, die an ein Formular übergeben werden](set-field-values-using-parameters-passed-form.md)<br/>
 [Xrm:Navigation.openUrl](https://docs.microsoft.com/powerapps/developer/model-driven-apps/clientapi/reference/xrm-navigation/openurl)<br/>
 [Ein Formular konfigurieren, um benutzerdefinierte Abfragezeichenfolgenparameter zu akzeptieren.](configure-form-accept-custom-querystring-parameters.md)    
 [Anpassen des Menübands](customize-commands-ribbon.md)<br/>
 [Clientskripting mit JavaScript](client-scripting.md)<br/>
 [Webressourcen](web-resources.md)<br/> 
 [Erweitern des Clients](/dynamics365/customer-engagement/developer/extend-client)<br/> 
 [Anwendungsnavigation mithilfe von SiteMap ändern](/dynamics365/customer-engagement/developer/customize-dev/change-application-navigation-using-sitemap)<br/> 
 [Starten eines Dialogfelds mit einer URL](/dynamics365/customer-engagement/developer/actions-dialogs#StartDialog)
