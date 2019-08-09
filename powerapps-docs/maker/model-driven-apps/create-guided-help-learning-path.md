---
title: Erstellen eines eigenen interaktiven Begleiters (Lernpfad) (Dynamics 365 for Customer Engagement-Apps) | MicrosoftDocs
description: ''
keywords: null
ms.date: 04/30/2019
ms.service: dynamics-365
ms.topic: article
applies_to:
  - Dynamics 365 for Customer Engagement (online)
ms.assetid: 8ee3c432-5f76-4086-b9cc-6cd467ae056b
author: Mattp123
ms.author: matp
manager: kvivek
topic-status: Drafting
search.audienceType:
  - customizer
search.app:
  - D365CE
---

# <a name="create-guided-help-learning-path-for-your-app"></a>Erstellen eines interaktiven Begleiters (Lernpfads) für Ihre App

Verwenden Sie den Lernpfad, um Ihren Benutzern eine benutzerdefinierte In-App-Hilfeumgebung bereitzustellen, die für Ihre Umgebung und die spezifische Nutzung und den Workflow in der Organisation angepasst wird. Der Lernpfad erleichtert das Lernen und die Akzeptanz von Apps und organisatorischen Prozessen und stellt sicher, dass Daten einheitlich interpretiert und eingegeben und Fehler und Supportanfragen von Benutzern reduziert werden. [Sehen Sie sich ein kurzes Video (1:50) zum Lernpfad an](https://community.dynamics.com/crm/b/crmvideos/archive/2016/05/09/introducing-learning-path-for-dynamics-crm).  

<a name="CustomHelp"></a>   

## <a name="how-is-learning-path-different-from-customizable-help"></a>Wie unterscheidet sich der Lernpfad von der anpassbaren Hilfe?  
 Mit der anpassbaren Hilfe ist es möglich, die standardmäßige [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)]-Apps-Hilfe zu überschreiben und Benutzer in der Organisation an eine andere URL für die Hilfe zu verweisen. Alternativ können Sie auch die Hilfe für eine Entität stark anpassen, damit Sie den Workflow besser beschreiben können. 

 Sie können im Lernpfad anpassbare Hilfe hinzufügen, die Benutzer in der App sehen, wenn sie eine Seite öffnen, eine Aktion ausführen oder die Hilfe-Schaltfläche (?) auswählen.   

 Weitere Informationen zu anpassbaren Hilfen finden Sie unter [Anpassen der Hilfeumgebung](https://technet.microsoft.com/library/dn832079.aspx).  

<a name="Avail"></a>   
## <a name="prerequisites"></a>Voraussetzungen  

 Zum Erstellen von Lernpfadinhalt müssen Sie:  

- PowerApps oder [!INCLUDE[pn_crm_online_shortest](../../includes/pn-crm-online-shortest.md)] verwenden.  

- Sich für Lernpfad angemeldet haben. Diese Einstellung ist standardmäßig aktiviert, kann aber deaktiviert worden sein.  

   Um sicherzustellen, dass der Lernpfad aktiviert ist: Wechseln Sie auf der Navigationsleiste zu **Einstellungen** ![Symbol „Einstellungen“](media/optionsbutton.png "Symbol „Einstellungen“") > **Für Lernpfad anmelden**.  

   Weitere Informationen: [Ein/Aus-Schalter für den Lernpfad (interaktiver Begleiter)](/dynamics365/customer-engagement/admin/on-off-switch-for-learning-path-guided-help)  

- Eine Systemadministratorrolle oder Systemanpasserrolle oder eine andere Rolle haben, die das Erstellungsrecht für den Lernpfad gibt.  

- Lernpfaderstellung aktivieren. Dadurch wird die Lernpfad-Autorensicherheitsgruppe von [!INCLUDE[pn_Office_365](../../includes/pn-office-365.md)] erstellt.  

- Sie müssen Mitglied der Lernpfad-Autorensicherheitsgruppe von [!INCLUDE[pn_Office_365](../../includes/pn-office-365.md)] sein.  

  Sie können Lernpfadinhalt für Internet-App-Module und Einheitliche Oberfläche-App-Module erstellen. Umfasst auch [!include[](../../includes/pn-dyn-365-tablets.md)].  

<a name="TurnOnLP"></a>   
## <a name="turn-on-learning-path-for-your-organization"></a>Lernpfad für Ihre Organisation aktivieren  
 Lernpfad ist eine Zusatzeinrichtung, die für Ihre Organisation aktiviert oder deaktiviert werden kann. Sie können in [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)] enthaltene Lernpfadinhalte anzeigen, Ihre eigenen Lernpfadinhalte für Benutzer erstellen oder beides tun.  

1. Melden Sie sich mit einem Administratorkonto bei [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) oder [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)] an.  

2. Gehen Sie zu **Einstellungen** und wählen Sie dann **Verwaltung** unter **System** aus. Weitere Informationen: [Einstellungen](/powerapps/maker/model-driven-apps/advanced-navigation#settings)

3. Wählen Sie auf der **Verwaltungsseite** den Eintrag **Systemeinstellungen**.  

4. Klicken Sie auf der Registerkarte **Allgemein** unter **URL für benutzerdefinierte Hilfe festlegen auf** **Ja**, für **Lernpfad aktivieren** und **Lernpfad-Erstellung aktivieren**.  

    Sie können den Lernpfad oder die benutzerdefinierte Hilfe aktivieren, aber nicht beide gleichzeitig. Bestätigen Sie, dass **Benutzerdefinierte Hilfe für anpassbare Entitäten verwenden** und **Parameter an URL anfügen** auf **Nein** festgelegt wurden.  

     ![Systemeinstellungen-Dialogfeld mit Optionen für die Auswahl der Aktivierung der Lernpfaderstellung](media/lp-system-settings.png "Systemeinstellungen-Dialogfeld mit Optionen für die Auswahl der Aktivierung der Lernpfaderstellung")  

5. Wählen Sie **OK** aus.  

<a name="ReqsAuth"></a>   
## <a name="add-a-user-to-the-office-365-learning-path-authors-security-group"></a>Einen Benutzer zur Office 365-Lernpfad-Autorensicherheitsgruppe hinzufügen  
 Wenn Sie nicht Mitglied der Lernpfad-Autorensicherheitsgruppe von [!INCLUDE[pn_Office_365](../../includes/pn-office-365.md)] sind, wird die folgende Fehlermeldung zurückgegeben, wenn Sie die Lernpfad-Inhalts-Bibliothek öffnen.  

 ![Fehlermeldung, die darauf hinweist, dass Sie kein Mitglied der Lernpfad-Sicherheitsgruppe sind](media/lp-o365-security-group.png "Fehlermeldung, die darauf hinweist, dass Sie kein Mitglied der Lernpfad-Sicherheitsgruppe sind")  

#### <a name="add-a-user"></a>Hinzufügen eines Benutzers  

1. Wechseln Sie zum Verwaltungsportal Ihres [!INCLUDE[pn_Office_365](../../includes/pn-office-365.md)] Mandanten, indem Sie die Schaltfläche **Zu anderen Anwendungen navigieren** in der linken oberen Ecke der Seite wählen, wenn Sie bei [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)]angemeldet sind, und wählen Sie dann **Administrator**.  

    Möglicherweise müssen Sie erneut Ihr Kennwort eingeben.  

2. Wählen Sie im **Administratorcenter** **Gruppen** aus.  

3. Wählen Sie auf der Seite **Gruppen** die Sicherheitsgruppe aus für die **Lernpfad-Autoren**  

4. Wählen Sie in der Zeile **Mitglieder** **Bearbeiten** und fügen Sie einer Gruppe Benutzer hinzu.  

5. Wählen Sie **+ Mitglieder hinzufügen** und definieren oder suchen Sie anschließend die Benutzer, die Sie die Gruppe hinzufügen möchten.  

6. Wählen Sie **Speichern und schließen**, wenn Sie fertig sind.  

> [!NOTE]
>  Eine weitere Methode, die Gruppe einem Benutzerkonto zuzuweisen ist es, aus **Benutzer** > **Aktive Benutzer** den Benutzer auszuwählen, den Sie hinzufügen möchten, und wählen Sie dann **Bearbeiten** neben **Gruppenmitgliedschaft**, um die Gruppe auszuwählen, um den Benutzer hinzuzufügen.  

<a name="MultipleOrgs"></a>   
## <a name="how-does-learning-path-work-with-multiple-organizations"></a>Wie funktioniert Lernpfad mit mehreren Organisationen?  
 Wenn Sie Lernpfadinhalt veröffentlichen, können Sie Veröffentlichungs-Umgebungen verwenden, um zu steuern, in welchen Organisationen, die dem Mandant zugeordnet ist, der Inhalt veröffentlicht wird. Um unterschiedliche Inhalte in verschiedenen Organisationen zu veröffentlichen, erstellen Sie mehrere Veröffentlichungsumgebungen und fügen jeder Organisation mindestens einer hinzu.  

<a name="SecurityRoles"></a>   
## <a name="learning-path-and-dynamics-365-for-customer-engagement-apps-security-roles"></a>Lernpfad- und Dynamics 365 for Customer Engagement-Apps-Sicherheitsrollen  
 [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)] verwendet Sicherheitsrollen, um zu bestimmen, welcher Lernpfadinhalt angezeigt wird, wenn Benutzer die Hilfe-Taste wählen, zu einer Seite navigieren oder eine definierte Aktionen in [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)] ausführen.  

 Die Rollen, die im Lernpfad verwendet werden, sind die selben Rollen, die in Ihrer [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)]-Organisation für Sicherheit und Datenzugriff verwendet werden, aber Sie können für Lernpfadinhalte für eine oder alle [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)]-Sicherheitsrollen erstellen.  In der Regel sollen die Sicherheitsrollen im Lernpfad-Designer vorhanden sein, um mit Ihren [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)]-Instanzen übereinzustimmen. Sie können die Ansicht in der Benutzeroberfläche im Designer vereinfachen, indem Sie einige [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)] Sicherheitsrollen im Designer ausblenden. Wenn Sie sich später entscheiden, dass Sie eine Sicherheitsrolle verwenden möchten, die Sie vom Lernpfad gelöscht haben, können Sie die gewünschten Rollen zwischen dem Lernpfad und [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)] synchronisieren.  

 Wenn Ihre Organisation mehrere Unternehmenseinheiten hat, können Sie Sicherheitsrollen für übergeordnete/untergeordnete Beziehungen haben. Nur die Sicherheitsrollen der Stammunternehmenseinheit werden synchronisiert.  

 Weitere Informationen über Sicherheitsrollen: [Sicherheitsrollen und Rechte](/dynamics365/customer-engagement/admin/security-roles-privileges).  

<a name="Precedence"></a>   
### <a name="learning-path-role-precedence"></a>Lernpfadrolle Rangfolge  
 Wenn einem Benutzer in Ihrer Organisation mehr als einer Sicherheitsrolle zugewiesen ist, wird die Rangfolge verwendet, um zu bestimmen, welche Sicherheitsrollen verwendet wird, um Lernpfadinhalt anzuzeigen. Wenn Lernpfadinhalt einer Sicherheitsrolle zugeordnet ist, sieht jeder Benutzer, der dieser Rolle zugeordnet ist, den Lernpfadinhalt, selbst wenn ihnen eine Sicherheitsrolle mit höherer Rangfolge zugewiesen wird, die nicht dem Lernpfadinhalt zugeordnet ist.  

 Jede Rolle, die in den Lernpfad integriert wird, hat einen numerischen Wert. Die erste Rolle in der Liste mit dem höchsten Vorrang und nachfolgende Rollen haben gegenüber niedrigeren Vorrang. Wenn einem Benutzer einer Rolle zugewiesen ist, mit der Lernpfadinhalt angezeigt wird, sieht der Benutzer diese Inhalte, wenn dem Benutzer die Rolle mit niedrigerer Rangfolge zugewiesen wird, die nicht den Inhalten zugeordnet ist. Angenommen einem Benutzer wird eine Rolle mit Rangfolge 1 und eine Rolle mit Rangfolge 20 zugewiesen, so sieht der Benutzer Lernpfadinhalte, die nur für die Rolle mit Rangfolge 1 definiert sind.  

 Wenn Sie unterschiedliche Inhalt für verschiedene Rollen auf derselben [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)] Seite oder -Bildschirm erstellen, sehen Benutzer Inhalte, die Rollen mit höherer Rangfolge zugeordnet sind..  

<a name="ManageRoles"></a>   
### <a name="manage-security-roles-and-precedence"></a>Verwalten von Rangfolge und Sicherheitsrollen  
 Sie können steuern, welche Sicherheitsrollen im Lernpfad-Designer verfügbar sind, und die Reihenfolge der Rollen für das Ermitteln von Rangfolge festlegen, wenn der Lernpfad ausgeführt wird. Wenn ein Benutzer zwei Rollen hat und es verschiedene Inhalt gibt, der für einen gegebenen Kontext für jede dieser Rollen veröffentlicht wird, wird der Benutzer den Inhalt für die Rolle sehen, die in der Liste höher aufgeführt wird.  

<a name="ConfigureRoles"></a>   
#### <a name="configure-security-roles"></a>Sicherheitsrollen konfigurieren  

1. Melden Sie sich bei [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)] mit einem Konto an, das Lernpfad-Erstellungsberechtigungen hat.  

2. Öffnen Sie die **Inhaltsbibliothek**.  

3. Wählen Sie **Konfiguration** oben im Bildschirm aus.  

4. Sie können die Sicherheitsrollen mit Ihren [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)]-Sicherheitsrollen synchronisieren, wählen Sie **Synchronisierungsrollen**.  

5. Um die Rangfolge für die Rollen festzulegen, die vom Lernpfad verwendet werden, nutzen Sie den Nach-Oben- oder Nach-Unten-Pfeil, um eine Rolle in der Liste nach oben oder nach unten zu verschieben.  

    Rangfolge wird durch den Auftrag der Rollen bestimmt, die auf dieser Seite angegeben ist.  

6. Um eine Rolle zu löschen, die mit dem Lernpfad verwendet wird, wählen Sie die Schaltfläche **Löschen** neben der Rolle.  

   > [!NOTE]
   >  Dies löscht die Rolle nicht von [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)]. Es wird die Rolle im Lernpfad-Designer gelöscht, um zu definieren, wie der Inhalt den Benutzern angezeigt wird. Sie können eine ausgeblendete Rolle immer wiederherstellen, indem Sie **Rollen synchronisieren** wählen.  

7. Wenn Sie die Änderungen abgeschlossen haben, wählen Sie **Speichern**.  

8. Wählen Sie **Zurück**, um zur Inhaltsbibliothek zurückzukehren.  

<a name="MobileApp"></a>   
## <a name="create-learning-path-controls-for-includepn_dyn_365_tabletsincludespn-dyn-365-tabletsmd"></a>Erstellen von Lernpfadsteuerelementen für [!INCLUDE[pn_dyn_365_tablets](../../includes/pn-dyn-365-tablets.md)]  
 Sie können Lernpfadsteuerelemente für [!INCLUDE[pn_dyn_365_tablets](../../includes/pn-dyn-365-tablets.md)] genauso erstellen, wie Sie Steuerelemente für den Webclient erstellen. Dazu müssen Sie den App-Simulator in einem mobilen Webbrowser nutzen, damit Sie Zugriff zur mobilen Benutzeroberfläche zum Anheften der Lernpfadkontrollen haben. Dieser Simulator soll nur zu diesem Zweck verwendet werden.  


### <a name="display-the-mobile-app-interface-simulator-in-a-web-browser"></a>Anzeigen des mobilen App-Schnittstellensimulator in einem Webbrowser  

1. Melden Sie sich bei [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)] an.  

2. Kopieren Sie den Servernamen für Ihre [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)]-Organisation aus der URL, die in Ihrem Browser angezeigt wird, zum Beispiel *<https://contososales.crm.dynamics.com/>*.  

    Stellen Sie sicher, dass den Schrägstrich (/) nach .com enthalten ist.  

3. Ermitteln Sie den eindeutigen Namen für die Organisation (auch Instanz genannt), für die Sie Lernpfadsteuerelemente erstellen möchten. Um den eindeutigen Namen der Organisation zu erhalten, wählen Sie in der Siteübersicht **Einstellungen** > **Anpassungen** und dann auf der Seite **Anpassung** **Entwicklerressourcen**. Kopieren Sie den Wert für das Feld **Eindeutiger Name**, das im Abschnitt **Instanz-Verweis** angezeigt wird.  

   ![Dynamics Organisations-Name, der im Informationsbereich für den Benutzer angezeigt wird](media/lp-org-name.png "Dynamics Organisations-Name, der im Informationsbereich für den Benutzer angezeigt wird")  

4. Fügen Sie Folgendes dem ersten Teil der URL für Ihre Organisation hinzu und ersetzen Sie \<org name> durch den eindeutigen Namen für Ihre Organisation, wie im vorherigen Schritt bestimmt:  

    nga/main.htm?org=*\<org name>*  

    Ihre URL sollte jetzt etwa wie folgt aussehen: https://contososales.crm.dynamics.com/nga/main.htm?org=orgb557e46a  

5. Fügen Sie auf die URL aus dem vorherigen Schritt hinzu und ersetzen Sie \<server name> durch den Servernamen aus dem ersten Schritt aus diesem Vorgang:  

    &server=*\<server name>*  

    Ihre URL sollte jetzt etwa wie folgt aussehen: https://contososales.crm.dynamics.com/nga/main.htm?org=orgb557e46a&server=https://contososales.crm.dynamics.com/.  

6. Öffnen Sie eine neue Registerkarte oder ein Browserfenster und kopieren Sie die vollständige URL, die Sie erstellt haben, in die neue Registerkarte oder das Browserfenster und drücken Sie dann die EINGABETASTE.  

    Wenn Sie sich zum ersten Mal mit der mobilen App-Schnittstelle verbinden, wird ein Begrüßungsbildschirm angezeigt, während das System Metadaten- und Downloadanpassungen verarbeitet. Nach Abschluss wird Ihr Arbeitsbereich angezeigt.  

   > [!NOTE]
   >  Wenn Sie sich mit der mobilen App-Version der Benutzeroberfläche verbinden, werden die Anmeldeinformationen der Anmeldung für Weboberfläche verwendet, um Sie zu authentifizieren. Sie müssen die Weboberfläche geöffnet werden, um den Zugriff, verweigerte abzurufen Fehler zu vermeiden, wenn die mobile App-Schnittstelle öffnen.  

7. Schließen Sie den Arbeitsbereichskalender, um die Homepage für die mobile App-Schnittstelle in Ihrem Browser anzuzeigen. Sie können dann die Inhaltsbibliothek öffnen, um Lernpfadsteuerelemente zu erstellen und zu aktualisieren. Weitere Informationen: [Inhaltsbibliothek](#ContentLibrary).  


<a name="ContentLibrary"></a>   
## <a name="content-library"></a>Inhaltsbibliothek  
 Die Inhaltsbibliothek zeigt alle Inhalte an, die erstellt und für Ihre Organisation verfügbar sind, zusätzlich zu den Befehlen zum Erstellen, Verwalten und Interagieren mit Steuerelementen. Um Lernpfad-Steuerelemente zu erstellen oder zu bearbeiten sollten Sie sich zunächst mit der Clientschnittstelle für Steuerelemente verbinden, für die Sie Steuerelemente erstellen möchten, und dann die Inhaltsbibliothek öffnen.  

**Um die Inhaltsbibliothek mit der Standardwebclientschnittstelle zu öffnen, wählen Sie eine der folgenden Optionen:**  

-   Wählen Sie auf der Randleiste die Schaltfläche **Inhaltsbibliothek**.  

     ![Symbol für die Inhaltsbibliothek in der Lernfpad-Randleiste](media/lp-sidebar-cl-icon.png "Symbol für die Inhaltsbibliothek in der Lernfpad-Randleiste")  

-   Wählen Sie die Kachel **Schulung** der Siteübersicht und dann **Inhaltsbibliothek**.  

     ![Inhaltsbibliotheksymbol auf Dynamics 365 for Customer Engagement-Sitemap](media/lp-sitemap-content-library.png "Inhaltsbibliotheksymbol auf Dynamics 365 for Customer Engagement-Apps-Sitemap")  

**Wenn Sie die Inhaltsbibliothek im mobilen App-Schnittstellensimulator öffnen:**  

1.  Wählen Sie die Auslassungspunkteschaltfläche (...) innerhalb eines Kreises in der rechten unterer Ecke des Bildschirms.  

    ![Auslassungspunkteschaltfläche für die Anzeige von Lernpfadsymbolen](media/lp-cl-ellipses.png "Auslassungspunkteschaltfläche für die Anzeige von Lernpfadsymbolen")  

2.  Wählen Sie **Lernpfad-Inhaltsbibliothek** aus.  

    ![Auf der Benutzeroberfläche der mobilen App angezeigte Lernpfadschaltflächen](media/lp-mobile-lp-button.png "Auf der Benutzeroberfläche der mobilen App angezeigte Lernpfadschaltflächen")  



> [!NOTE]
>  Wenn Sie nicht alle Spalten in der Inhaltsbibliothek sehen, ist unter Umständen das Ansichtszoom des Browsers auf höher als 100% festgelegt. Um alle Spalten zu sehen, muss das Zoom auf 100% oder tiefer festgelegt sein.  

 Die zufriedene Bibliothek enthält die Spalten, die in der folgenden Tabelle ist beschrieben werden:  

|Spalte|Beschreibung|  
|------------|-----------------|  
|**Name**|Der Name, den Sie benutzten, wenn Sie die Aufgabenhilfe oder die Randleiste erstellt haben. Ein rotes Sperrsymbol neben den Namen gibt an, dass der Inhalt gerade ausgecheckt wird. Sie können den Mauszeiger über das Symbol bewegen, um anzuzeigen, für welchen Benutzer der Inhalt ausgecheckt ist.<br /><br /> ![Ein rotes Sperrsymbol zeigt an, dass der Inhalt ausgecheckt ist.](media/lp-cl-checked-out.png "Ein rotes Sperrsymbol zeigt an, dass der Inhalt ausgecheckt ist.")<br /><br /> Ein rotes Sternchen neben dem Namen zeigt an, dass neu eingecheckter Inhalt vorhanden ist.<br /><br /> ![Ein roter Stern kennzeichnet neu eingecheckten Inhalt](media/lp-cl-new-check-in.png "Ein roter Stern kennzeichnet neu eingecheckten Inhalt")|  
|**Titel**|Der Titel, den Sie angegeben haben, als Sie Inhalt der Aufgabenhilfe oder Randleiste hinzugefügt haben. Titel für Randleisten und angeleitete Aufgaben werden angezeigt, wenn diese als Links hinzugefügt werden oder wenn sie für Suchergebnisse zurückgegeben werden.|  
|**Typ**|Ein Symbol, das den Typ des Inhalts angibt: Randleiste oder Aufgabenhilfe|  
|**Formularfaktor**|Symbole, die für den Formfaktor stehen, der für diesen Inhalt bei der Erstellung ausgewählt wurden, entweder **Desktop** oder **Tablet**.<br /><br /> Die Spalte **Formularfaktor** wird nicht angezeigt, wenn Sie die die Inhaltsbibliothek mit dem mobilen App-Schnittstellensimulator oder den interaktiven Servicehub verwenden.|  
|**Tags**|Zeigt alle Tags an, die in diesen Inhalten angewendet werden. Sie können Tags mit dem Dialogfeld **Erweiterte Optionen** hinzufügen. Mithilfe von Tags können Sie Inhalte filtern, die in der Bibliothek angezeigt werden.|  
|**App-Version**|Die Version der Anwendung, auf der das Steuerelement erzielt wurde.|  
|**Autor**|Name der Person, die das Steuerelement erstellt hat.|  
|**Sprachen**|Ein numerischer Wert, der die Anzahl von Sprachen darstellt, in die das Steuerelement lokalisiert werden soll.<br /><br /> Dieses Col.|  
|**Status**|Zeigt **Veröffentlicht**, wenn der Inhalt gerade veröffentlicht wird; andernfalls wird der Status **Entwurf** angezeigt.|  
|**Aktiviert**|Zeigt an, ob der Inhalt aktiviert oder deaktiviert ist.  Nur aktivierter Inhalt wird für die Benutzer angezeigt.|  
|**Zuletzt veröffentlicht**|Das aktuelle Datum, an dem der Inhalt veröffentlicht wurde.|  

<a name="ContentTypes"></a>   
## <a name="learning-path-content-types-guided-tasks-and-sidebars"></a>Lernpfadinhaltstypen: Aufgabenhilfen und Randleisten  
 Sie können zwei Arten von Inhalt im Lernpfad erstellen: Aufgabenhilfen und Randleisten.  

<a name="GT"></a>   
### <a name="guided-tasks"></a>Aufgabenhilfen  
 Eine Aufgabenhilfe ist normalerweise eine Serie von Schritten, wobei es auch ein einzelner Schritt sein kann. Ein Benutzer kann eine Aufgabenhilfe starten, indem er einen Link auf einer Randleiste wählt, indem er zu einer Seite navigiert oder indem er einen Link auf einer Seite wählt, für die Sie Inhalt erstellt haben. In jedem Schritt wählt der Benutzer die Schaltfläche **Weiter** oder beendet eine definierte Aktion, um zum nächsten Schritt zu gehen oder die Aufgabenhilfe zu schließen.  

 Aufgabenhilfen sind nützlich, um Benutzer durch allgemeine oder neue Aufgaben zu führen. Sie können auch verwendet werden, um sicherzustellen, dass Aufgaben einheitlich in Ihrer Organisation ausgeführt werden oder Daten mit einer bestimmten Methode eingegeben werden, damit sie die Prozesse oder Workflows in der Organisation unterstützen. Aufgabenhilfen können, Links, Videos und andere Informationen enthalten, um Benutzer dabei zu unterstützen, mehr zum Bereich der Benutzeroberfläche, auf die der Schritt verweist, zu erfahren oder sich damit vertraut zu machen.  

<a name="Sidebar"></a>   
### <a name="sidebars"></a>Randleisten  
 Eine Randleiste wird angezeigt, wenn ein Benutzer die Hilfe-Taste wählt, zu einer Seite navigiert oder einen Link oder eine Schaltfläche auf einer Seite wählt, für die Sie Inhalt erstellt haben. Sie können Hauptrandleisten zusammenstellen, die angezeigt werden, wenn der Benutzer eine Seite oder ein Fenster öffnet oder das Hauptsymbol auf einer Randleiste wählt.  

 ![Startsymbol auf einer Randleiste](media/sidebar-home.png "Startsymbol auf einer Randleiste")  

 Sie können auch Fehlerrandleisten definieren, die angezeigt werden, wenn es ein Problem beim Anzeigen der beabsichtigte Randleiste gibt. Randleisten können, Links, Videos und andere Informationen enthalten, die Sie dem Benutzern zur Verfügung stellen können, damit er mehr über die Seite oder das angezeigte Formular oder die Aktionen, die auf der Seite oder mit dem Formular möglich sind, erfährt oder sich damit vertraut machen kann.  

<a name="CreateGT"></a>   
## <a name="create-a-guided-task"></a>Eine neue Aufgabenhilfe erstellen  

 Es gibt zwei Schritte zum Erstellen einer Aufgabenhilfe:  

1.  Definieren Sie, wie die Aufgabe aufgerufen werden, und weisen Sie die Rollen zu, für die der Inhalt gilt.  

2.  Verwenden Sie den Fluss-Editor, um Schritte hinzuzufügen, die Benutzer sehen, während Sie die Aufgabenhilfen durchlaufen.  

### <a name="define-the-triggers-and-roles"></a>Definiert Auslöser und Rollen  

1. Öffnen Sie die Seite, für die Sie eine Aufgabenhilfe erstellen möchten.  

2. Öffnen Sie die Inhaltsbibliothek. Weitere Informationen finden Sie in der [Inhaltsbibliothek](#ContentLibrary).  

3. In der Inhaltsbibliothek wählen Sie **Aufgabenhilfe**.  

    ![Link zur Erstellung einer neuen Aufgabenhilfe in der Lernpfad-Inhaltsbibliothek](media/lp-content-library-gt.png "Link zur Erstellung einer neuen Aufgabenhilfe in der Lernpfad-Inhaltsbibliothek")  

4. Geben Sie einen Namen ein und wählen Sie die anderen für die Einstellungen für die Aufgabenhilfe. Verwenden Sie diese Tabelle als Referenz.  


   |              Einstellung               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |    **Diese Aufgabenhilfe deaktivieren**    |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          Aktivieren Sie dieses Kontrollkästchen, um die Aufgabenhilfe zu deaktivieren. Wenn deaktiviert, wird sie nicht für die Benutzer angezeigt.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
   | **Dies zu einer Fehleraufgabenhilfe machen** |                                                                                                                                                                                                                                                                                                                                                                                                                       Aktivieren Sie dieses Kontrollkästchen, wenn Sie diese Aufgabenhilfe nur anzeigen möchten, wenn ein Fehler mit anderen Aufgabenhilfen besteht, wie ein Fehlen von Rechten oder andere Probleme, die verhindern, dass andere Aufgabenhilfen, die dieser Seite zugeordnet sind, angezeigt werden.                                                                                                                                                                                                                                                                                                                                                                                                                       |
   |              **Name**              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        Der Name für die Aufgabenhilfe, die in der Inhaltsbibliothek angezeigt wird.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
   |             **Client**             |                                                                                                                                                                               Der Clientwert wird automatisch für die Plattform festgelegt, in der Sie den Inhalt erstellten. **Warnung:** Wenn Sie ein vorhandenes Steuerelement bearbeiten, wenn sie mit einer anderen als Benutzeroberfläche als jener verbunden sind, auf der das Steuerelement erstellt wurde, wird die Clienteinstellung zum aktuellen Clienttyp aktualisiert. Dadurch bricht das Steuerelemen und funktioniert nicht auf dem Client-, für den es ursprünglich erstellt wurde. <br /><br /> Wenn Sie Steuerelemente für die Webschnittstelle erstellen, wird der **Webclient** angezeigt.<br /><br /> Wenn Sie mit dem mobilen App-Schnittstellensimulator verbunden sind, wird **Mobile Apps** angezeigt.<br /><br /> Wenn Sie mit dem interaktiven Servicehub verbunden sind, wird **Interaktiver Servicehub** angezeigt.                                                                                                                                                                               |
   |          **Formfaktor**           |                                                                                                                                                                       Der angezeigte Formfaktor hängt davon ab, auf welcher Benutzeroberfläche Sie Inhalt erstellen. Wenn Sie die Webclientschnittstelle verwenden, werden **Desktop** und **Tablet** angezeigt. Falls für den Webclient ausgewählt wird, bezieht sich **Tablet** auf den Browser auf dem Tabletgerät und nicht auf die mobile App.<br /><br /> Wenn Sie Steuerelemente für die mobile App-Shnittstelle erstellen, wird **Tablet** angezeigt. Hier finden die Geräte, auf den die [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)] mobile App ausgeführt wird, aber nur auf Tablets unterstützt wird.<br /><br /> Wenn Sie den interaktiven Servicehub nicht verwenden, wird **Desktop** angezeigt. **Wichtig:** Lernpfad wird in [!INCLUDE[pn_crm_shortest](../../includes/pn-dyn-365-phones.md)] nicht unterstützt.                                                                                                                                                                        |
   |     **Aufgabenhilfe wird geöffnet, wenn**     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                              Wählen Sie aus, ob die Aufgabenhilfe angezeigt werden soll, wenn die **Seite lädt** oder wenn ein Benutzer einen **Link anklickt** auf einer Randleiste.                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
   |        **Lebenszyklusphase**         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        Dieses Einstellung dient nur zur internen Verwendung.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
   |   **Dynamics 365 for Customer Engagement-Apps-Sicherheitsrolle**   |                                                                                                                                                                                                                                                                                                                                                                                                  Wählen Sie die Sicherheitsrolle aus, für die Sie die Aufgabehilfe anzeigen möchten. Sie können beliebig viele Rollen auswählen. Wenn einem Benutzer mehrere Rollen zugewiesen werden, erscheinen die Aufgabenhilfen nur für die Rolle in der obersten Rangfolge, wie weiter oben in diesem Thema beschrieben.                                                                                                                                                                                                                                                                                                                                                                                                   |
   |             **Status**             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                Zeigt den Status der Aufgabenhilfe an. Der Status ist **Entwurf** bis Sie ihn veröffentlichen.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
   |        **Erweiterte Optionen**        | Diese Option ist verfügbar, nachdem Sie die Aufgabenhilfe gespeichert haben. Die folgenden Einstellungen sind unter **Erweiterte Optionen** verfügbar:<ul><li>**Diese Fehleraufgabenhilfe machen**: Wählen Sie dieses Kontrollkästchen, wenn Sie diese Aufgabenhilfe nur anzeigen möchten, wenn ein Fehler mit anderen Aufgabenhilfen besteht.</li><li>**Unterstützte Sprachen**: Wählen Sie die Sprache für diese Aufgabehilfe und für den Import und Export.</li><li>**Autor**: Ändern des Autors, der für diese Aufgabenhilfe definiert wurde.</li><li>**Tags**: Hinzufügen oder Entfernen der Tags für diese Aufgabenhilfe. Tags verwenden, um Inhalt in der Inhaltsbibliothek zu finden oder um den Inhalt zu kategorisieren.</li></ul><br />Sie können auch die folgenden Einstellungen unter **Informationen veröffentlichen** festlegen:<ul><li>**App-Version**: Festlegen der [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)]-Version, die dem Inhalt zugeordnet wurde.</li><li>**Version**: Die Version des Inhalts festlegen, den Sie erstellen.</li><li>**Erstellen der Gruppe**: Legen Sie die Erstellungs-Gruppe für den Inhalt fest, den Sie erstellen.</li><li>**Veröffentlichungs-Gruppen**: Wählen Sie die Veröffentlichungsgruppe(n) zum Inhalt aus.</li></ul> |


5. Wenn Sie fertig sind, wählen Sie **Speichern**, um den Fluss-Editor zu nutzen.  

### <a name="add-steps-with-the-flow-editor"></a>Fügen Sie Schritte mit dem Fluss-Editor hinzu  

1. Fügen Sie dort einen Titel hinzu, wo der *Titel der Aufgabenhilfe* angezeigt wird. Dies ist der Titel, den Benutzer sehen.  

2. Wählen Sie aus, ob feste ID-Steuerelemente angezeigt werden sollen. Registrierte Steuerelemente werden in Grün und nicht registrierte Steuerelemente werden in Blau angezeigt, wenn Sie die Kachel ziehen, um sie in der Benutzeroberfläche anzuheften. Wenn Sie einen Schritt an ein Steuerelement ohne feste ID anheften, wird es möglicherweise durch ein zukünftiges Update von [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)]beeinträchtigt werden. Updates betreffen keine festen ID-Steuerelemente.  

3. Wählen Sie **Neuen Schritt hinzufügen** und wählen Sie den Schritttyp aus, den Sie für die ersten Schritte der Aufgabenhilfe verwenden möchten.  

   |Schaltfächentyp|Beschreibung|  
   |-----------------|-----------------|  
   |**Schritt mit Schaltfläche "Weiter"**|Dieser Schritt umfasst eine Schaltfläche "Weiter", die der Benutzer anklickt, um zum nächsten Schritt im Fluss zu wechseln. Wenn dies die letzte Blase im Verlauf, wird die Schaltfläche "Weiter " nicht angezeigt. Ziehen Sie die Kachel, um den Schritt dort anzuheften, wo er in der App erscheinen soll.|  
   |**Schritt mit Benutzeraktion**|Dieser Schritt umfasst keine Schaltfläche "Weiter". Der Benutzer wird aufgefordert, das Benutzeroberflächenelement zu wählen, an dem der Schritt angeheftet ist. Wenn eine Seitenumleitung oder eine Benutzeroberflächenstatusänderung infolge dieser Auswahl erfolgt, stellen Sie sicher, dass Sie den nächsten Schritt am geänderten Benutzeroberflächenstatus anheften. Ziehen Sie die Kachel, um den Schritt dort anzuheften, wo er in der App erscheinen soll.<br /><br /> Heften Sie diesen Schritt-Typ an ein auswählbares Steuerelement in der Benutzeroberfläche, wie eine Schaltfläche oder einen Hyperlink.|  
   |**Benutzeraktion mit Schaltfläche "Weiter"**|Dieser Schritt umfasst eine Schaltfläche "Weiter". Das Auswählen der Schaltfläche "Weiter " hat die selbe Wirkung, wie wenn Sie das Benutzeroberflächenelement auswählen, an dem der Schritt angeheftet wurde. Wenn eine Seitenumleitung oder eine Benutzeroberflächenstatusänderung infolge dieser Auswahl erfolgt, stellen Sie sicher, dass Sie den nächsten Schritt am geänderten Benutzeroberflächenstatus anheften. Ziehen Sie die Kachel, um den Schritt dort anzuheften, wo er in der App erscheinen soll.|  
   |**Lernschritt**|Dieser Schritt ist eine anpassbare Schaltfläche für die Endaktion. Dieser Schritt kann sich nur am Ende eines Aufgabenhilfeflusses befinden. Sie können ihn verwenden, um ihn mit einer Lernpfad-Randleiste zu verknüpfen. Ziehen Sie die Kachel, um den Schritt dort anzuheften, wo er in der App erscheinen soll.|  

   > [!NOTE]
   >  Wenn Sie die Aufgabenhilfen bereits geplant haben und wissen, welche Schritte Sie hinzufügen möchten, können Sie jetzt alle hinzufügen. Jeder Schritt, den Sie hinzugefügt haben, erscheint im Fluss-Editor im Auftrag, den Sie hinzufügten. Sie können Schritte neu anordnen, nachdem Sie diese hinzugefügt haben, indem Sie diese in der Liste nach oben oder unten ziehen.  

4. Wählen Sie die Art des Schritts aus, den Sie hinzufügen möchten, und ziehen Sie dann die Kachel zur Benutzeroberfläche, um sie an das Steuerelemente anzuheften. Es werden möglicherweise einige Versuche notwendig sein, den Schritt am gewünschten Ort zu platzieren.  

   > [!NOTE]
   >  Sie können den Schritt bis zu 15 Sekunden halten. Wenn Sie ihn nicht innerhalb von 15 Sekunden anheften, bleibt die Kachel ungelöst und der Mauszeiger ist wieder normal.  

   ![Aufgabenhilfe-Fluss-Editor](media/lp-gt-flow-editor.png "Aufgabenhilfe-Fluss-Editor")  

5. Wenn Sie den Schritt am gewünschten Ort positioniert haben, lassen Sie die Maustaste los, um ihn am Steuerelement anzuheften. Die Schritt erscheint am gewünschten Ort. Um den Schritt zu verschieben, können Sie die Schaltfläche **Mich ziehen** im Bereich neben dem Schritt verwenden.  

   !["Mich ziehen"-Symbol in einer Aufgabenhilfeblase](media/lp-gt-bubble-drag-me.png "\"Mich ziehen\"-Symbol in einer Aufgabenhilfeblase")  

6. Fügen Sie dem Schritt mithilfe der daneben angezeigten Steuerelementen Inhalte hinzu. Die folgenden Einstellungen stehen zur Verfügung:  

   - **Inhaltstyp**: Dem Schritt Text oder ein Video hinzufügen. Wählen Sie **Bearbeiten**, um weitere Einstellungen zu sehen. Sie können die Schriftgröße, die Farbe und den Schriftgrad für Text ändern und eine Miniaturansicht für Videos hinzufügen.  

   - **Platzierung**: Definieren Sie den Speicherort des Schritts auf dem Steuerelement, an dem er angeheftet ist. Auswahl enthält: Automatische Position (standardmäßig aktiviert), oben links, oben rechts, unten links, links oben, links unten, rechts oben und rechts unten.  

   - **Kopieren**: Dies erstellt eine Kopie des Schritts mit identischem Inhalt, der am selben Ort angeheftet wird und fügt einen Aufgabenhilfefluss direkt hinter dem Originalschritt ein.  

7. Wählen Sie **Speichern**, wenn Sie den Schritt positioniert und Inhalte hinzugefügt haben. Schließen Sie dann entweder den Schritt mithilfe der Schaltfläche in der rechten oberen Ecke des Schritts oder wählen Sie den Pfeil in der linken oberen Ecke des Bildschirms aus, um zum Fluss-Editor zurückzukehren.  

   > [!NOTE]
   >  Sie können den Schritt später jederzeit bearbeiten, sodass Sie sich keine Sorgen machen müssen, dass Sie vor dem Schließen nicht alles integriert haben.  

8. Um den nächsten Schritt in der Aufgabenhilfe hinzuzufügen oder zu bearbeiten, wählen Sie den Pfeil nach rechts ![Pfeilsymbol zur Rückkehr zum Fluss-Editor](media/lp-chevron.png "Pfeilsymbol zur Rückkehr zum Fluss-Editor") in der linken oberen Ecke der Seite, um den Fluss-Editor anzuzeigen.  

9. Fügen Sie weitere Schritte hinzu, die Sie in der Aufgabenhilfe einschließen möchten und stellen Sie sicher, dass Sie jeden Schritt speichern, wenn Sie den Inhalt hinzugefügt haben.  

    > [!NOTE]
    >  Wenn Sie einen Schritt neu anordnen oder ihn mithilfe der Schaltfläche **Kopieren** auf der Symbolleiste kopieren, gehen alle nicht gespeicherten Änderungen in diesem Schritt verloren. Vergessen Sie nicht, die Änderungen oft zu speichern.  

10. Wenn Sie alle Schritte der Aufgabenhilfe hinzugefügt haben, wählen Sie **Speichern**.  

11. Wählen Sie **Vorschau**, um die Aufgabehilfe zu testen und zu sehen, wie Sie für die Benutzer angezeigt wird.  

    > [!NOTE]
    >  Um Ihre Aufgabenhilfe zu veröffentlichen, müssen Sie sie zuerst in der Vorschau anzeigen. Wenn Sie einen Schritt schließen oder den Pfeil auf der linken oberen Ecke des Bildschirms während des Seitenansichtsmodus verwenden, finden Sie die Schaltflächen **Einchecken** und **Veröffentlichen** im Lernpfad-Designer.  

12. Wenn Sie mit den Änderungen zufrieden sind, veröffentlichen Sie diese in der Aufgabenhilfe oder später in der Inhaltsbibliothek.  

<a name="CreateSidebar"></a>   
## <a name="create-a-sidebar"></a>Eine Randleiste erstellen  

 Es gibt zwei Schritte zum Erstellen einer Randleiste:  

1.  Legen Sie die Randleisteneigenschaften fest und weisen Sie die Rollen zu, die angewendet werden sollen.  

2.  Fügen Sie Inhalt der Randleiste hinzu (Text, Bilder, Links und Schaltflächen).  

### <a name="set-the-sidebar-properties-and-roles"></a>Festlegen der Randleisteneigenschaften und -rollen  

1. Öffnen Sie die Seite, für die Sie eine Randleiste erstellen möchten.  

2. Öffnen Sie die Inhaltsbibliothek. Weitere Informationen finden Sie in der [Inhaltsbibliothek](#ContentLibrary).  

3. In der Inhaltsbibliothek wählen Sie **Randleiste**.  

   ![Link zur Erstellung einer neuen Randleiste in der Lernpfad-Inhaltsbibliothek](media/lp-content-library-sb.png "Link zur Erstellung einer neuen Randleiste in der Lernpfad-Inhaltsbibliothek")  

4. Geben Sie einen Namen ein und wählen Sie die anderen Einstellungen für die Randleiste. Verwenden Sie diese Tabelle als Referenz.  


   |             Einstellung             |                                                                                                                                                                                                                                                                                                                                                        Beschreibung                                                                                                                                                                                                                                                                                                                                                        |
   |---------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |           **Deaktivieren**           |                                                                                                                                                                                                                                                                                                                                       Aktivieren Sie dieses Kontrollkästchen, um die Randleiste zu deaktivieren.                                                                                                                                                                                                                                                                                                                                       |
   | **Dies zu einer Fehlerrandleiste machen**  |                                                                                                                                                                                                                                         Aktivieren Sie dieses Kontrollkästchen, wenn Sie diese Randleiste nur anzeigen möchten, wenn ein Fehler mit einer anderen Randleiste besteht, wie ein Fehlen von Rechten oder andere Probleme, die verhindern, dass andere Randleisten, die dieser Seite zugeordnet sind, angezeigt werden.                                                                                                                                                                                                                                          |
   |   **Als Startrandleiste festlegen**    |                                                                                                                                                                                                                                                                         Die Hauptrandleiste wird angezeigt, wenn ein Benutzer die Ausgangsschaltfläche auswählt oder wenn es keine Randleiste auf der Seite gibt und der Benutzer "Hilfe" auswählt. Jede Seite kann nur eine Hauptrandleiste haben.                                                                                                                                                                                                                                                                         |
   |            **Name**             |                                                                                                                                                                                                                                                                                                                                    Der Name, der in Inhaltsbibliothek angezeigt wird.                                                                                                                                                                                                                                                                                                                                     |
   |           **Client**            | Der Clientwert wird automatisch für die Plattform festgelegt, in der Sie den Inhalt erstellten. **Warnung:** Wenn Sie ein vorhandenes Steuerelement bearbeiten, wenn sie mit einer anderen als Benutzeroberfläche als jener verbunden sind, auf der das Steuerelement erstellt wurde, wird die Clienteinstellung zum aktuellen Clienttyp aktualisiert. Dadurch bricht das Steuerelemen und funktioniert nicht auf dem Client-, für den es ursprünglich erstellt wurde. <br /><br /> Wenn Sie Steuerelemente für die Webschnittstelle erstellen, wird der **Webclient** angezeigt.<br /><br /> Wenn Sie mit dem mobilen App-Schnittstellensimulator verbunden sind, wird **Mobile Apps** angezeigt.<br /><br /> Wenn Sie mit dem interaktiven Servicehub verbunden sind, wird **Interaktiver Servicehub** angezeigt. |
   |         **Formfaktor**         |                                                  Der angezeigte Formfaktor hängt davon ab, auf welcher Benutzeroberfläche Sie Inhalt erstellen. Wenn Sie die Webclientschnittstelle verwenden, werden **Desktop** und **Tablet** angezeigt. Falls für den Webclient ausgewählt wird, bezieht sich **Tablet** auf den Browser auf dem Tabletgerät und nicht auf die mobile App.<br /><br /> Wenn Sie Steuerelemente für die mobile App-Shnittstelle erstellen, wird **Tablet** angezeigt. Hier finden die Geräte, auf den die [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)] mobile App ausgeführt wird, aber nur auf Tablets unterstützt wird.<br /><br /> Wenn Sie den interaktiven Servicehub nicht verwenden, wird **Desktop** angezeigt.                                                  |
   |     **Randleiste wird geöffnet, wenn**      |                                                                                                                                                                                                                                                                                               Wählen Sie aus, ob die Randleiste angezeigt werden soll, wenn die Seite geladen wird, oder wenn ein Benutzer einen Link oder eine Schaltfläche auf der Seite auswählt.                                                                                                                                                                                                                                                                                               |
   |       **Lebenszyklusphase**       |                                                                                                                                                                                                                                                                                                                                              Dies ist nur zur internen Verwendung.                                                                                                                                                                                                                                                                                                                                               |
   | **Dynamics 365 for Customer Engagement-Apps-Sicherheitsrolle** |                                                                                                                                                                                                                  Wählen Sie die Rolle oder Rollen aus, für die Sie die Randleiste für Benutzer anzeigen möchten. Sie können beliebig viele Rollen auswählen. Wenn einem Benutzer mehrere Rollen zugewiesen werden, erscheint die Randleiste nur für die Rolle in der obersten Rangfolge, wie weiter oben in diesem Thema beschrieben.                                                                                                                                                                                                                   |
   |          **Vorlage**           |                                                                                                                                                                                                                                                                                       Wählen Sie die Vorlage aus, die Sie für die neue Randleiste verwenden möchten, entweder **Eine Spalte** oder **Zwei Spalten**. Die Standardvorlage ist eine einspaltige Randleiste.                                                                                                                                                                                                                                                                                        |
   |           **Status**            |                                                                                                                                                                                                                                                                                                              Zeigt den Status der Randleiste an. Der Status ist **Entwurf** bis Sie die Randleiste veröffentlichen.                                                                                                                                                                                                                                                                                                              |
   |      **Erweiterte Optionen**       |                                                                         Diese Option ist nicht verfügbar, bis Sie die Randleiste speichern. Die folgenden Einstellungen sind unter **Erweiterte Optionen** verfügbar:<ul><li>**Randleistenkopfzeile deaktivieren**</li><li>**Randleistentitel deaktivieren**</li><li>**Randleistenfußzeile deaktivieren**</li><li>**Autor**: Ändern des Autors, der für diese Randleiste definiert wurde.</li><li>**Tags**: Hinzufügen oder Entfernen der Tags für diese Randleiste. Tags verwenden, um Inhalt in der Inhaltsbibliothek leichter zu finden oder um den Inhalt zu kategorisieren.</li><li>**Unterstützte Sprachen**: Wählen Sie die Sprache für diese Randleiste und für den Import und Export.</li></ul>                                                                         |


5. Wenn Sie fertig sind, wählen Sie **Speichern**, um Ihrer Randleiste im Designer Inhalt hinzuzufügen.  

<a name="SidebarContent"></a>   

### <a name="add-content-to-your-sidebar"></a>Fügen Sie Inhalt der Randleiste hinzu  

1.  Nachdem Sie Ihren Randleistennamen und die Eigenschaften in der Inhaltsbibliothek gespeichert haben, öffnet sich der Designer.  

2.  Geben Sie einen Titel für die Randleiste ein.  

3.  Fügen Sie Inhalte hinzu, die Sie für Ihre Benutzer anzeigen möchten, wenn die Randleiste angezeigt wird.  

4.  Wählen Sie **Abschnitt hinzufügen**, um einen neuen Abschnitt hinzuzufügen.  

5.  Um einen Abschnitt aus der Vorlage zu entfernen, wählen Sie den gewünschten Abschnitt, den Sie löschen möchten, und dann die Schaltfläche **Löschen**.  

6.  Wenn Sie mit der Bearbeitung des Inhalts in der Randleiste fertig sind, wählen Sie **Speichern**, um Ihre Änderungen zu speichern, und schließen Sie dann die Randleiste, indem Sie die Schaltfläche **Schließen** in der oberen rechten Ecke auswählen, um zur Inhaltsbibliothek zurückzukehren.  

7.  Wählen Sie **Verwalten** oben auf der Seite und dann **Einchecken**, um Ihre Änderungen zu speichern und sie Benutzern, die Inhalt erstellen, bereitzustellen.  

### <a name="add-links-to-your-sidebar"></a>Fügen Sie Links der Randleiste hinzu  
 Wenn Sie eine Randleiste erstellen, stehen mehrere Möglichkeiten für das Hinzufügen von Links bereit. Sie können eine Verbindung mit einer anderen Lernpfad-Aufgabenhilde oder Randleiste, zu einer anderen Seite in [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)] oder einer Webseite erstellen. Sie können sogar nach Hilfe- und Schulungsthemen suchen, um eine Verknüpfung zu erstellen, während Sie eine Randleiste erstellen. Nachdem Sie die Randleisteneigenschaften und -Rollen festgelegt haben und bereit sind, Inhalt hinzuzufügen, folgen Sie diesen Schritten, um Links einem Abschnitt der Randleiste hinzuzufügen, die Sie erstellte haben.  

1. Im Abschnitt, in dem Sie Links hinzufügen möchten, wählen Sie das Symbol **Liste von Links**.  

   ![Liste der Link-Symbole, die auf einer Lernpfad-Randleiste ausgewählt sind](media/lp-sidebar-links.png "Liste der Link-Symbole, die auf einer Lernpfad-Randleiste ausgewählt sind")  

2. Fügen Sie einen Abschnittstitel hinzu und wählen Sie dann **+ Link hinzufügen**.  

   ![Markiertes Kästchen "Link hinzufügen" in einem Abschnitt einer Lernpfad-Randleiste](media/lp-sidebar-addlink.png "Markiertes Kästchen \"Link hinzufügen\" in einem Abschnitt einer Lernpfad-Randleiste")  

3. Wählen Sie den Link-Typ aus, den Sie hinzufügen möchten und wählen Sie **Weiter**. Sie können aus den folgenden Optionen auswählen:  

   - **Aufgabenhilfe** Erstellt eine Verbindung mit einer vorhandenen angeleiteten Aufgabe des Lernpfads her. Dies kann nützlich sein, um Informationen über eine Aufgabe in der Randleiste bereitzustellen, um diese dann mit einer Aufgabenhilfe zu verbinden, die einen Benutzer durch die Aufgabe in der [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)] - Benutzeroberfläche führt.  

   - **Randleiste**: Erstellet eine Verbindung mit einer vorhandenen Lernpfad-Randleiste. Sie können einen Link zu einer Randleiste verwenden um  

   - **Seite in App**  

   - **Webseite**  

<a name="Videos"></a>   
## <a name="use-videos-in-your-learning-path-controls"></a>Videos in den Lernpfadkontrollen zu verwenden  
 Nur Videos, die auf YouTube gehostet werden, werden in Lernpfadsteuerelementen unterstützt. Wenn Sie Videos in den Lernpfad-Steuerelementen verwenden möchten, müssen Sie ein YouTube-Konto und einen Kanal zum Hochladen der Videos haben. Sie können keine Videos mit einem Kanal verknüpfen der auf "Privat" festgelegt ist, aber Sie können Videos verknüpfen, wenn Ihr Kanal auf "Öffentlich" oder "Nicht aufgeführt" festgelegt ist. Sie können den Kanal auch so festlegen, dass verschiedene Benutzer den Videoinhalt für Ihr Unternehmen verwalten können.  

 Wenn Sie Ihren Steuerelementen Videos hinzufügen, können Sie das Video innerhalb des Steuerelements einbetten. Wenn die Benutzer die Videos in einer neuen Registerkarte oder in einem Browserfenster angezeigt erhalten sollen, können Sie einen Textabschnitt der Randleiste hinzufügen und dann den Link zu Ihrem Video im Textabschnitt hinzufügen.  

 Wenn Sie Videos einbetten, die innerhalb der Randleiste oder einer Aufgabenhilfe angezeigt werden, können Sie den Link verwenden, den Sie von YouTube erhalten. Der Lernpfad aktualisiert automatisch den Link, um das Video und die Größe einzubetten, damit sie in die Randleiste oder Aufgabenhilfekachel zu passen. Ein Benutzer kann **Vollbildschirm** auswählen, um das Video im Ganzseitenmodus anzuzeigen. Wenn ein Benutzer die Wiedergabe unterbricht oder die Wiedergabe beendet ist, kann YouTube automatisch Links zu anderen Videos anzeigen, die den Benutzer interessieren könnten. Sie können dies verhindern, indem Sie den Link im Steuerelement ändern und **? rel=0** am Ende hinzufügen.  

 Beispielsweise nachdem Sie ein Video erstellt und in Ihren Kanal hochgeladen haben, kopieren Sie die Video-URL, die YouTube angibt, nämlich **https://youtu.be/4TrYMB4pjyw**. Um dieses Video in ein Steuerelement einzubetten, geben Sie die URL in das Feld **Video-URL eingeben** für das Steuerelement ein.  

 Wenn Sie das Steuerelement speichern, ändert Lernpfad die URL in **https://www.youtube.com/embed/4TrYMB4pjyw**. Um die Anzeige von Links zu anderen Videos auszuschalten, wenn die Wiedergabe unterbrochen oder beendet ist, bearbeiten Sie die URL, um **? rel=0** am Ende anzufügen, damit Ihre URL in etwa wie folgt aussieht: **https://www.youtube.com/embed/4TrYMB4pjyw?rel=0**.  

Weitere Informationen zum Verwenden von YouTube: [YouTube-Hilfecenter](https://go.microsoft.com/fwlink/?linkid=847120)  

<a name="PublishLP"></a>   
## <a name="publish-learning-path-content"></a>Lernpfad-Inhalts veröffentlichen  
 Benutzer sehen nur Lernpfad-Inhalte, die Sie erstellen, nachdem sie diese veröffentlicht haben. Nur überprüfter Inhalt kann veröffentlicht werden.  

1.  Öffnen Sie die Inhaltsbibliothek.  

2.  Wählen Sie das Kontrollkästchen neben der Aufgabenhilfe und der Randleiste, die Sie veröffentlichen möchten. Stellen Sie sicher, dass das Steuerelement, das Sie veröffentlichen möchten, überprüft ist.  

3.  Wählen Sie **Veröffentlichen** oben an der Seite und dann **Veröffentlichen**.  

4.  Klicken Sie auf der Seite **Steuerelement veröffentlichen** auf die Veröffentlichungsumgebungen, die Sie veröffentlichen möchten, und wählen Sie dann **Veröffentlichen**.  

<a name="PublishingGroup"></a>   
### <a name="about-publishing-groups"></a>Informationen zur Veröffentlichung von Gruppen  
 Lernpfad-Inhalt wird in einer Veröffentlichungsgruppe veröffentlicht. Wenn Sie den Lernpfad für Ihre Organisation aktivieren, wird eine Veröffentlichungsgruppe mit demselben Namen wie der Organisationsname erstellt. Sie können zusätzliche Veröffentlichungsgruppen nach Bedarf erstellen. Sie können mehrere Organisationen zu einer Veröffentlichungsgruppe hinzufügen, und eine Organisation kann zu verschiedenen Veröffentlichungsgruppen gehören, sodass Sie Inhalt anpassen und ihn in den verschiedenen Organisationen einfach veröffentlichen können.  

<a name="CreatePG"></a>   
### <a name="create-a-publishing-group"></a>Erstellen einer Veröffentlichungsgruppe  

1.  Öffnen Sie die Inhaltsbibliothek.  

2.  Wählen Sie **Konfiguration** oben im Bildschirm aus.  

3.  Wählen Sie **Konfiguration veröffentlichen**.  

4.  Wählen Sie auf der Seite **Konfiguration veröffentlichen** **Neue PG**.  

5.  Geben Sie einen Namen und eine Beschreibung (optional) ein.  

6.  Wählen Sie die Organisationen aus, die in der Veröffentlichungsgruppe enthalten sein sollen. Sie werden nur die Organisationen sehen, für die Sie die Berechtigungen verfügen.  

7.  Wählen Sie **Speichern** aus und dann **OK**.  

<a name="ExportandImport"></a>   
## <a name="export-and-import-learning-path-content"></a>Export- und Import von Lernpfadinhalten  
 Sie können Inhalte exportieren, die Sie erstellen, um sie dem Autor einer anderen Organisation freizugeben oder um Sicherungskopien zu erstellen. Die Exportfunktion erstellt eine komprimierten ZIP-Datei, die .json-Dateien enthält, die für den Inhalt im Lernpfad verwendet werden. Es gibt einen Ordner in der ZIP-Datei für jede ausgewählte Lernpfad-Randleiste oder Aufgabenhilfe.  

<a name="ExportProc"></a>   
### <a name="export-your-learning-path-content"></a>Lernpfadinhalt exportieren  

1.  In der Inhaltsbibliothek wählen Sie das Kontrollkästchen neben dem Inhalt aus, die Sie exportieren möchten.  

     Sie können Inhalt exportieren, ohne ihn in zu überprüfen.  

2.  Wählen Sie **Verwalten** oben an der Seite und dann **Exportieren**.  

3.  Wählen Sie die Option, die Sie zum Speichern der generierten ZIP-Datei verwenden möchten, und wählen Sie dann einen Namen und einen Speicherort aus.  

    > [!NOTE]
    >  Der Standarddateiname für ZIP-Datei ist identisch, sobald Sie exportieren möchten. Deshalb sollten Sie einen eindeutigen Namen verwenden, um zu verhindern, dass zuvor exportierte Dateien überschrieben werden.  

### <a name="import-your-learning-path-content"></a>Lernpfadinhalt importieren  

1.  In der Inhaltsbibliothek wählen Sie **Verwalten** und dann **Importieren**.  

2.  Wählen Sie **Durchsuchen**, um die zuvor exportierte Datei auszuwählen, die Sie importieren möchten, und ziehen Sie die Datei in das Feld **Steuerelemente hierhin ziehen** im Dialogfeld.  

    > [!CAUTION]
    >  Wenn Sie ein Steuerelement importieren, überschreibt und ersetzt es alle Versionen des gleichen Steuerelements, die bereits in der Bibliothek vorhanden sind. Auch wenn das Steuerelement neuer ist.  

3.  Stellen Sie sicher, dass der Dateiname die Datei ist, die Sie importieren möchten, und wählen Sie dann **Importieren**.  

4.  Wählen Sie im Bestätigungsdialogfeld **OK**.  

<a name="Localize"></a>   
## <a name="localize-learning-path-controls"></a>Lernpfadsteuerelemente lokalisieren  
 Sie können den Inhalt in den Steuerelemente im Lernpfad lokalisieren, um sie den Benutzern in ihrer ausgewählten Sprache für [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)] anzuzeigen. Zur Lokalisierung der Steuerelemente können Sie sie einfach nach Zeichenfolgen suchen, die den Benutzern angezeigt werden, und dann importieren die das Steuerelement der lokalisierten Inhalte enthält. Sie können das Steuerelement in dieselbe Organisation importieren oder in eine andere Organisation. Sie können dasselbe Steuerelement in mehrere Sprachen lokalisieren und die einzelnen Sprachen in spezifische Organisationen importieren, die Benutzer mit der ausgewählten Sprache unterstützen. Der Lokalisierungssupport im Lernpfad folgen dem OASIS XML Localisation Interchange File Format TC-Standard (XLIFF) 2.0. Es gibt kostenlose Tools und Lernprogramme für das Arbeiten mit diesem Format. Weitere Informationen: [XLIFF-Version 2.0](http://docs.oasis-open.org/xliff/xliff-core/v2.0/os/xliff-core-v2.0-os.html).  

 Weitere Informationen zur Benutzerspracheinstellungen in [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)]: [Persönliche Optionen hinzufügen](/dynamics365/customer-engagement/basics/set-personal-options).  

1.  Wählen Sie das Steuerelement aus, die Sie in der Inhaltsbibliothek lokalisieren möchten.  

2.  Wählen Sie **Lokalisieren** und dann **Exportieren** aus.  

    ![Export-Schaltfläche im Lernpfad-Lokalisierungsmenü](media/lp-localize-export.png "Export-Schaltfläche im Lernpfad-Lokalisierungsmenü")  

3.  Wählen Sie die Option, die Sie zum Speichern der generierten ZIP-Datei verwenden möchten, und wählen Sie dann einen Namen und einen Speicherort aus.  

    > [!NOTE]
    >  Der Standarddateiname für ZIP-Datei ist identisch, sobald Sie exportieren möchten. Deshalb sollten Sie einen eindeutigen Namen verwenden, um zu verhindern, dass zuvor exportierte Dateien überschrieben werden.  

4.  Nachdem Sie Inhalte lokalisiert haben, wählen Sie in der Inhaltsbibliothek **Lokalisieren** und dann **Importieren**.  

5.  Wählen Sie **Durchsuchen**, um die zuvor exportierte Datei auszuwählen, die Sie importieren möchten, und ziehen Sie die Datei in das Feld **Steuerelemente hierhin ziehen** im Dialogfeld.  

    > [!CAUTION]
    >  Wenn Sie ein Steuerelement importieren, überschreibt und ersetzt es alle Versionen des gleichen Steuerelements, die bereits in der Bibliothek vorhanden sind. Auch wenn das Steuerelement neuer ist.  

6.  Stellen Sie sicher, dass der Dateiname die Datei ist, die Sie importieren möchten, und wählen Sie dann **Importieren**.  

7.  Wählen Sie im Bestätigungsdialogfeld **OK**.  

8.  Veröffentlichen Sie das lokalisierte Steuerelement für die gewünschten Veröffentlichungsumgebungen. Der lokalisierte Inhalt wird automatisch für Benutzer angezeigt, die dieselbe Sprache für die Benutzeroberfläche ausgewählt haben.  



## <a name="includepn_crm_shortestincludespn-crm-shortestmd-apps-data-center-mapping-to-includepn-azure-shortestincludespn-azure-shortestmd-regions"></a>[!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)]-Apps-Rechenzentrumszuordnung zu [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)]-Regionen
Die folgende Tabelle enthält die [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)]-Apps-Rechenzentrumsregionen und die entsprechenden [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)]-Regionen, in denen der Lernpfad verfügbar ist.


| [!INCLUDE[pn_crm_shortest](../../includes/pn-crm-shortest.md)]-Rechenzentrum | [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)]-Region |
|------------------------------------------------------------------------|------------------------------------------------------------------------|
|                          Asien-Pazifik (APAC)                           |                               Ostasien                                |
|                              Kanada (CAN)                              |                             Kanada, Mitte                             |
|       Europa, Naher Osten, Afrika und Großbritannien (EMEA, GBR)       |                              Westeuropa                               |
|                              Indien (IND)                               |                             Indien, Mitte                              |
|                              Japan (JPN)                               |                               Japan, Osten                               |
|                          Nordamerika (NAM)                           |                                USA (Osten)                                 |
|                             Ozeanien (OZE)                              |                             Australien, Osten                             |
|                          Südamerika (SAM)                           |                              Brasilien, Süden                              |

## <a name="privacy-notice"></a>Datenschutzbestimmungen  
[!INCLUDE[cc_privacy_learning_path_authoring](../../includes/cc-privacy-learning-path-authoring.md)]

### <a name="see-also"></a>Siehe auch  
 [Ein/Aus-Schalter für den Lernpfad (interaktiver Begleiter)](/dynamics365/customer-engagement/admin/on-off-switch-for-learning-path-guided-help)
