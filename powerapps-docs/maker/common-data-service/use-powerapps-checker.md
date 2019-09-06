---
title: 'Verwenden Sie Lösungsprüfer, um Ihre Apps in PowerApps zu prüfen  | Microsoft Docs'
description: 'Verwenden Sie den Lösungsprüfer, um Ihre Lösung zu überprüfen.'
author: Mattp123
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: article
ms.date: 07/09/2019
ms.author: matp
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="use-solution-checker-to-validate-your-model-driven-apps-in-powerapps"></a>Verwenden Sie Lösungsprüfer, um Ihre modellgesteuerten Apps in PowerApps zu prüfen

Um komplexe geschäftliche Anforderungen zu liefern, können Modell-angetriebene App-Hersteller mit fortschrittlichen Lösungen arbeiten, die Common Data Service-Plattform anpassen und erweitern. Mit der erweiterten Implementierungen kommt ein erhöhtes Risiko, wo, Leistung und Stabilität Zuverlässigkeitsprobleme eingegeben werden, und sich auf die Benutzererfahrung negativ auswirken können. Identifizieren und verstehen, wie diese Probleme zeitaufwendig und kompliziert sein können. Mit der Lösungsprüferfunktion können Sie eine umfangreiche Prüfung der statischen Analyse auf Ihren Lösungen für einen Satz von Regeln der bewährten Methode ausführen und diese problematischen Muster schnell ermitteln. Nach der Überprüfung erhalten Sie einen Bericht, der Probleme aufzeigt, die bestimmt werden, welche Komponenten und Code betroffen sind und die Dokumentation verknüpft, die beschreibt, wie ein Problem zu beheben ist.

Der Lösungsprüfer analysiert die Lösungskomponente: 
- Common Data Service-Plug-Ins
- Common Data Service benutzerdefinierte Workflowaktivitäten 
- Common Data Service-Webressourcen (HTML) und JavaScript
- Common Data Service-Konfigurationen, wie SDK-Nachrichtenschritte 

Lösungsprüfer abeiten mit nicht verwalteten Lösungen, die von einer Umgebung exportiert werden. 

> [!NOTE]
> - In diesem Artikel wird erläutert, wie der Lösungsprüfer über das PowerApps-Herstellerportal ausgeführt wird. Ein PowerShell-Modul ist ebenfalls verfügbar, das Sie verwenden können, um direkt mit dem Service zu interagieren. Das Microsoft.PowerApps.Checker.PowerShell-Modul kann für die Analyse verwalteter und nicht verwalteter Lösungen für unterstützte Versionen von lokalen und Online-Umgebungen verwendet werden, oder der Service kann automatisiert und in Ihre Build- und Release-Pipelines integrieren. Weitere Informationen: [Microsoft.PowerApps.Checker.PowerShell-Übersicht]( /powershell/powerapps/overview?view=pa-ps-latest#get-started-using-the-microsoftpowerappscheckerpowershell-module) 
> - Der Lösungsprüfer funktioniert nicht für Lösungen, die JavaScript mit ECMAScript 6 (2015 ) oder höhere Versionen enthalten. Wenn JavaScript mit einer dieser Versionen erkannt wird, wird ein JS001 Syntax-Problem für die Webressource berichtet.

## <a name="enable-the-solution-checker"></a>Aktivieren des Lösungsprüfer
Der Solution Checker ist standardmäßig in jeder Common Data Service-Umgebung aktiviert. Ein Menüpunkt **Solution Checker** ist verfügbar, wenn Sie eine nicht verwaltete Lösung im Bereich **Lösungen** von PowerApps auswählen. Wenn die Option **Ausführen** im Menü **Solution Checker** nicht verfügbar ist, können Sie sie aktivieren, indem Sie die PowerApps-Checker-Lösung installieren. Zur Installation führen Sie die folgenden Schritte aus:   

1. Melden Sie sich bei [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an und wählen Sie die Common Data Service-Umgebung aus, in der Sie den Lösungsprüfer aktivieren möchten. 
2. Wählen Sie im linken Navigationsbereich die Option **Lösungen** aus.
3. Klicken Sie auf der Symbolleiste die Option **Lösungsprüfer** und anschließend **Installieren** aus – das öffnet die Microsoft AppSource-Seite. Sie müssen Popup-Fenster ermöglichen, wenn der Browser die Seite am Öffnen hindert. 

   > [!div class="mx-imgBorder"]
   > ![Installieren des Lösungsprüfers](media/solution-checker-install.png "Installieren des Lösungsprüfers")

4. Wählen Sie **Kostenlose Testversion** auf der AppSource-Seite. 

5. Wenn Sie zustimmen, nehmen Sie die Bedingungen und wählen Sie die Organisationen aus, um die PowerApps-Prüferlösung zu installieren. 
6. Wenn die Installation abgeschlossen ist, aktualisieren Sie die Liste **Lösung** auf der PowerApps-Seite, um sicherzustellen, dass der Solution Checker verfügbar ist.  
7. Wenn Sie eine Lösung prüfen [Führen Sie den aus Lösungsprüfer aus](#run-the-solution-checker).


<!-- ### Components created with the PowerApps checker
When you install the PowerApps checker these solution specific components are created. 
- Entities: The entities that are created are required to store the results of solution analysis and the status of analysis jobs in your environment.
   - Analysis Component
   - Analysis Job
   - Analysis Result
- System job: A system job is created so admins can remove solution analysis data from the environment. The job contains a configuration value, currently set to remove the solution analysis data after 60 days, which an administrator can override. 
- Security Roles: Two security roles, **Export Customizations**, and **Solution Checker** are created. These roles are required to export the solution for analysis, and storing the analysis results to the entities in your environment.
- User principle: The **PowerApps Advisor** user is created that allows the checker to authenticate with your Common Data Service environment and assign the two security roles, Export Customizations and Solution Checker. The PowerApps Advisor is an application user and does not consume a license.  -->

## <a name="run-the-solution-checker"></a>Ausführen es Lösungsprüfer
Nachdem Sie den PowerApps-Prüfer in Ihrer Umgebung installieren haben, steht ein Menüelement **Lösungsprüfer** zur Verfügung, wenn Sie eine nicht verwaltete Lösung PowerApps **Lösungen** im Bereich aktivieren. 

1. Melden Sie sich bei [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an. 
2. Wählen Sie im Navigationsbereich **Lösungen** aus. 
3. Neben der nicht verwalteten Lösung, die Sie auch zum Analysieren möchten, wählen Sie **...** aus, zeigen Sie auf **Lösungsprüfer** und dann auf **Ausführen**. 

   > [!div class="mx-imgBorder"]
   > ![Ausführen des Lösungsprüferbefehls](media/solution-checker-run.png "Ausführen des Lösungsprüferbefehls")

4.  Der Statusbereich im oberen Recht Bereich der Seite **Lösung** zeigt **Lösungenprüfer wird ausgeführt**. 

    > [!div class="mx-imgBorder"]
    > ![Lösungsprüferstatus](media/solution-checker-status.png "Lösungsprüferstatus")
   
    Beachten Sie Folgendes:
    - Der Lösungsprüfer kann einige Minuten dauern, um die Analyse zu starten. 
    
    - Während dieser Zeit wird **Ausführen…** angezeigt Status in der Spalte **Lösungsprüfung** der Liste **Lösung**. 
    
    - Sie erhalten eine E-Mail-Benachrichtigung und eine Benachrichtigung im Bereich **Benachrichtigungen** des PowerApps-Standorts, wenn die automatische Suche ausgeführt wird.  

5.  [Zum Anzeigen des Berichts](#review-the-solution-checker-report) Wenn eine Prüfung abgeschlossen ist.

## <a name="cancel-a-check"></a>Prüfvorgang abbrechen

Wenn Sie E-Mails senden, um Lösungen in Ihrer Umgebung übermitteln zu können, kann die Prüfung über den Statusbereich im oberen rechten Bereich der **Lösungen** storniert werden. 

Wenn Sie eine Prüfung abbrechen, läuft die Lösungsprüfung nicht weiter und der  Lösungsprüfungsstatus kehrt zum vorherigen Zustand zurück. 

## <a name="solution-checker-states"></a>Lösungsprüfer-Status
Wenn Sie den Lösungsprüfer in Ihrer Umgebung installieren, steht die **Lösungsprüfung** in der **Lösungen** zur Verfügung. In dieser Spalte werden die Lösungsanalysestatus für eine Lösung angezeigt. 

|Status  |Beschreibung  |
|---------|---------|
|Ist nicht ausgeführt worden    | Die Lösung wurde nicht analysiert.        |
|Wird ausgeführt...     | Die Lösung wird analysiert.       |
|Konnte nicht abgeschlossen werden     |  Lösungsanalyse wurde angefordert, aber die Analyse wurde nicht erfolgreich abgeschlossen.       |
|Ergebnisse erhalten *Datum und Uhrzeit*   | Lösungsanalyse abgeschlossen und Ergebnisse können heruntergeladen werden.      |
|Konnte nicht abgeschlossen werden. Ergebnisse erhalten *Datum und Uhrzeit*     | Die aktuelle Analyseanforderung in nicht erfolgreich abgeschlossen. Die letzten erfolgreichen Ergebnisse können heruntergeladen werden.         |
|Geprüft von Microsoft     | Dies ist eine Microsoft-verwaltete Lösung. Lösungsanalyse ist für diese Lösungen nicht erlaubt.         |
|Geprüft von Publisher     | Dies ist eine verwalteten Lösung von Drittanbieter. Für die Erstellung der Lösungsanalyse nicht verfügbar.        |


## <a name="review-the-solution-checker-report"></a>Wiederholen Sie den Lösungsprüferbericht
Wenn eine Lösungsprüfung abgeschlossen ist, können Sie den Analysebericht im Portal anzeigen oder den Bericht über Ihren Webbrowser herunterladen. Im Portal haben Sie die Möglichkeit, die Ergebnisse nach **Ausgabe**, **Standort** oder nach **Schweregrad** zu filtern und zu gruppieren und detaillierte Informationen zu den in Ihrer Lösung gefundenen Problemen anzuzeigen. 

1. Wählen Sie im Navigationsbereich **Lösungen** aus.
2. Wählen Sie neben der nicht verwalteten Lösung, für die Sie den Bericht über den Solution Checker anzeigen möchten, **...**, zeigen Sie auf **Solution Checker**, und wählen Sie dann **Ergebnisse anzeigen**.  
3. Wählen Sie ein Problem aus, um die Details und Anleitungen zur Lösung anzuzeigen.

    > [!div class="mx-imgBorder"] 
    > ![](media/solution-checker-viewresults.png "Solution Checker-Ergebnisse")

Die Ergebnisse der Lösungsprüfung stehen auch zum Download bereit. Der Download-Bericht ist im Format [!INCLUDE [pn-excel-short](../../includes/pn-excel-short.md)] und enthält mehrere Visualisierungen und Spalten, die Ihnen helfen, die Auswirkungen, den Typ und die Position jedes in Ihrer Lösung erkannten Problems zu identifizieren. Ein Link zu detaillierten Anweisungen, wie das Problem auch bereitgestellt wird. 

1. Wählen Sie im Navigationsbereich **Lösungen** aus.
2. Wählen Sie neben der nicht verwalteten Lösung, für die Sie den Bericht über den Solution Checker herunterladen möchten, **...**, zeigen Sie auf **Solution Checker**, und wählen Sie dann **Ergebnisse herunterladen**.  
3. Die Lösungsprüferzip-Datei wird heruntergeladen in den Ordner, der über dem Webbrowser angegeben ist.

Hier finden Sie eine Zusammenfassung einer Spalte im Bericht.

|Berichtsfeld |Beschreibung  |Sie betrifft nur Komponente.   |
|---------|---------|---------|
|Problem     |   Der Titel des Problems ist in der Lösung identifiziert.      | Alle        |
|Kateg.     | Kategorisiert das Problem wie **Leistung**, **Verwendung** oder **Unterstützung**.      |  Alle     |
|Schweregrad     | Stellt die möglichen Auswirkungen des Problems identifizierten dar. Verfügbare Auswirkungstypen sind **Hoch**, **Mittel**, **Niedrig** und **Informatorisch**.         |  Alle       |
|Anleitung     |  Verknüpfen Sie Artikel, die das Problem aufführen, beeinflussen und Aktionen empfehlen.       |  Alle       |
|Komponente     |  Die Lösungskomponente, in der das Problem identifiziert wird.        |   Alle      |
|Location     |  Der Standort und/oder die Quelldatei der Komponente, in der das Problem ist, wie z.B. die Assembly  oder der JavaScript-Dateiname.        |  Alle       |
|Linie #     |  Der Zeilennummernverweis des Problems in der betroffenen Webressourcenkomponente.       |  Webressourcen       |
|Modul     | Modulname,der das Problem identifiziert, das in der angegeben Assembly erkannt wurde.     |   Plug-in oder benutzerdefinierte Workflowaktivität      |
|Typ     | Typ des Problems in der identifizierten Assembly.        | Plug-in oder benutzerdefinierte Workflowaktivität        |
|Mitglied     |  Typ des Problems in der identifizierten Assembly.      | Plug-in oder benutzerdefinierte Workflowaktivität        |
|Anweisung     | Die Codeanweisung oder die Konfiguration, die das Problem auslöst.        |  Alle       |
|Kommentare     | Details zum Problem, die Auflösungsstufen auf hohem Niveau verfügen.         |  Alle       |


## <a name="best-practice-rules-used-by-solution-checker"></a>Bewährte Methoden, die vom Lösungsprüfer verwendet werden

|Lösungskomponente  |Regelname  |Regelbeschreibung  |
|---------|---------|---------|
|Plug-in oder Workflowaktivität   | [il-specify-column](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-specify-column&client=PAChecker&source=featuredocs)  | Vermeiden Sie es, alle Spalten über Dynamics 365 for Customer Engagement Abfrage APIs zu wählen.     |
|Plug-in oder Workflowaktivität   | [meta-remove-dup-reg](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-dup-reg&client=PAChecker&source=featuredocs)     | Vermeiden Sie doppeltes Dynamics 365 for Customer Engagement Plug-In Registrierungen.     |
|Plug-in oder Workflowaktivität   | [il-turn-off-keepalive](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-turn-off-keepalive&client=PAChecker&source=featuredocs)   | Legen Sie KeepAlive auf false, wenn Sie mit externen Hosts in einem Dynamics 365 for Customer Engagement Plug-in interagieren.     |
|Plug-in oder Workflowaktivität   | [il-avoid-unpub-metadata](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-unpub-metadata&client=PAChecker&source=featuredocs)   | Vermeiden Sie es, unveröffentlichtes Dynamics 365 for Customer Engagement Metadaten  abzurufen.     |
|Plug-in oder Workflowaktivität   | [il-avoid-batch-plugin](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-batch-plugin&client=PAChecker&source=featuredocs)   | Vermeiden Sie die Verwendung von Batch-Requesttypen in Dynamics 365 Customer Engagement-Plugins und -Workflow-Aktivitäten.    |
|Plug-in oder Workflowaktivität   | [meta-avoid-reg-no-attribute](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-reg-no-attribute&client=PAChecker&source=featuredocs)  | Schließen Sie Filterungsattribute mit Dynamics 365 for Customer Engagement Plug-In-Registrierungen ein.    |
|Plug-in oder Workflowaktivität   | [meta-avoid-reg-retrieve](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-reg-retrieve&client=PAChecker&source=featuredocs)  | Verwenden Sie Dynamics 365 for Customer Engagement Plug-ins mit Vorsicht, die für Retrieve und RetrieveMultiple Nachrichten angemeldet sind.    |
|Plug-in oder Workflowaktivität   | [meta-remove-inactive](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-inactive&client=PAChecker&source=featuredocs)    | Entfernen Sie inaktive Konfigurationen in Dynamics 365 for Customer Engagement.    |
|Plug-in oder Workflowaktivität   | [il-meta-avoid-crm2011-depr-message](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-crm2011-depr-message&client=PAChecker&source=featuredocs)  | Verwenden Sie keine veralteten Microsoft Dynamics CRM 2011-Messages.     |
|Plug-in oder Workflowaktivität   | [meta-avoid-crm4-event](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-crm4-event&client=PAChecker&source=featuredocs) | Verwenden Sie keine Microsoft Dynamics CRM 4.0-Plug-In-Registrierungs-Phase.    |
|Plug-in oder Workflowaktivität   | [il-avoid-specialized-update-ops](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-specialized-update-ops&client=PAChecker&source=featuredocs)  | Verwenden Sie keine speziellen Aktualisierungsvorgangsanforderungen in Dynamics 365 for Customer Engagement.    | 
| Plug-in oder Workflowaktivität |  [il-use-autonumber-feature](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-use-autonumber-feature&client=PAChecker)  |Verwenden Sie die automatische Zahlenfunktion statt einer benutzerdefinierten automatischen Nummerierungslösung. | 
| Plug-in oder Workflowaktivität  | [il-avoid-parallel-plugin](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-parallel-plugin&client=PAChecker)  | Die Verwendung von parallelen Mustern sollte innerhalb von Plug-Ins vermieden werden.  |
| Plug-in oder Workflowaktivität  | [il-avoid-lock-plugin](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-lock-plugin&client=PAChecker)  | Vermeiden Sie die Sperre statischer Mitglieder in Plug-Ins.  |
| Plug-in oder Workflowaktivität  | [meta-avoid-retrievemultiple-annotation](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-retrievemultiple-annotation&client=PAChecker)  | Vermeiden Sie die Registrierung eines Plug-Ins bei RetrieveMultiple der Anmerkung.  |
|Webressourcen  | [web-use-async](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-async&client=PAChecker&source=featuredocs)  |  Interagieren mit HTTP- und HTTPS-Ressourcen asynchron.   |
|Webressourcen  | [meta-remove-invalid-form-handler](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-invalid-form-handler&client=PAChecker&source=featuredocs)  | Korrigieren Sie oder entfernen Sie ungültiges Dynamics 365 for Customer Engagement Formular-Ereignisanmeldungen.   |
|Webressourcen  | [meta-remove-orphaned-form-element](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-orphaned-form-element&client=PAChecker&source=featuredocs)  | Korrigieren Sie oder entfernen Sie ungültiges Dynamics 365 for Customer Engagement Formular-Ereignisanmeldungen.   |
|Webressourcen  | [web-avoid-modals](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-modals&client=PAChecker&source=featuredocs)  | Vermeiden Sie die Nutzung von modalen Dialogfelder.   |
|Webressourcen  | [web-avoid-crm2011-service-odata](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-crm2011-service-odata&client=PAChecker&source=featuredocs)   | Zielen Sie nicht auf den Microsoft Dynamics CRM 2011 ODatas 2.0-Endpunkt ab.     |
|Webressourcen  | [web-avoid-crm2011-service-soap](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-crm2011-service-soap&client=PAChecker&source=featuredocs)  | Zielen Sie nicht auf die Microsoft Dynamics CRM 2011 SOAP-Services ab.   |
|Webressourcen  | [web-avoid-browser-specific-api](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-browser-specific-api&client=PAChecker&source=featuredocs) | Verwenden Sie keine Internet Explorer-Vorgänger APIs Internet oder -Browser-Plug-Ins.   |
|Webressourcen  | [web-avoid-2011-api](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-2011-api&client=PAChecker&source=featuredocs)  | Verwenden Sie kein veraltetes Microsoft Dynamics CRM 2011-Objektmodell.  |
|Webressourcen  | [web-use-relative-uri](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-relative-uri&client=PAChecker&source=featuredocs)   | Verwenden Sie keine absoluten Common Data Service-Endpunkt-URLs.    |
|Webressourcen  | [web-use-client-context](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-client-context&client=PAChecker&source=featuredocs)  | Nutzen Sie Client-Kontexte.   |
|Webressourcen  | [web-use-dialog-api-param](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-dialog-api-param&client=PAChecker&source=featuredocs)   | Nutzen Sie Dialog-API-Parameter.   |
|Webressourcen  | [web-use-org-setting](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-org-setting&client=PAChecker&source=featuredocs)   | Nutzen Sie Organisationseinstellungen.   |
|Webressourcen  | [web-use-grid-api](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-grid-api&client=PAChecker&source=featuredocs)   | Verwenden Sie Gitter-APIs.    |
|Webressourcen  | [web-avoid-isActivityType](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-isActivityType&client=PAChecker&source=featuredocs)   | Ersetzen Sie Xrm.Utility.isActivityType-Methode mit neuen Xrm.Utility.getEntityMetadata und verwenden Sie nicht die Menübandregeln.    |
|Webressourcen  | [meta-avoid-silverlight](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-silverlight&client=PAChecker&source=featuredocs)   | Die Nutzung der Webressource Silverlight (XAP) ist veraltet.   |
| Webressourcen  | [web-remove-debug-script](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-remove-debug-script&client=PAChecker)  | Verwenden SIe keine Debugskripts in Nicht-Entwicklungsumgebungen.  | 
| Webressourcen  | [web-use-strict-mode](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-strict-mode&client=PAChecker)  | Verwenden Sie den strengem Modus, wenn möglich.  | 
| Webressourcen  | [web-use-strict-equality-operators](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-strict-equality-operators&client=PAChecker)  | Verwenden Sie strenge Gleichheitsoperatoren.  | 
| Webressourcen  | [web-avoid-eval](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-eval&client=PAChecker)  | Verwenden Sie nicht die Funktion „eval” oder deren funktionale Entsprechungen.  | 


### <a name="see-also"></a>Siehe auch
[Bewährte Methoden sowie Anweisungen zum Common Data Service](../../developer/common-data-service/best-practices/index.md)<br />
[Best Practices und Anleitungen für modellgetriebene Anwendungen](../../developer/model-driven-apps/best-practices/index.md)<br />
[Häufige Probleme und Lösungen für Solution Checker](common-issues-resolutions-solution-checker.md)<br />
