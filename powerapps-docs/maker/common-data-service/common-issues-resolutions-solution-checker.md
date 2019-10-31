---
title: Häufige Probleme und Lösungen für Solution Checker | Microsoft Docs
description: ' Eine Liste der häufigsten Probleme und Lösungen im Solution Checker'
keywords: ''
ms.date: 02/11/2019
ms.service: powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: caa4e3f2-9700-49b8-87ed-8a68e8878b02
author: jowells1
ms.author: jowells
manager: austinj
ms.reviewer: null
robots: 'noindex,nofollow'
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="common-issues-and-resolutions-for-solution-checker"></a>Häufige Probleme und Lösungen für Solution Checker

Dieser Artikel listet einige häufige Probleme auf, die bei der Verwendung des Solution Checker auftreten können. Gegebenenfalls werden Workarounds angeboten.

## <a name="youre-unable-to-use-solution-checker-to-run-analysis-or-download-results"></a>Es ist nicht möglich, die Lösungsprüfung zu verwenden, um die Analyse auszuführen oder Ergebnisse herunterzuladen

Kurz nach dem Senden einer Lösungsprüfungsanforderung zum Ausführen einer Analyse oder Download von Ergebnissen wird der Vorgang nicht abgeschlossen und eine Fehlermeldung angezeigt, z. B.:

> *„Wir konnten die Überprüfung der Lösung **[Name der Lösung]** nicht ausführen. Versuchen sie es noch einmal.“*

Wenn möglich, versucht die Lösungsprüfung, eine bestimmte Fehlermeldung mit einem Link zu den Details zu der möglichen Ursache und Lösungsschritten zurückzugeben. Wählen Sie für Details **'Weitere Informationen'** aus.

![Fehlermeldungsleiste](media/solution-checker-missing-roles-error.png)

Fehler, die während der Hintergrundverarbeitung der Analyse auftreten, schlagen mit dem Status **Konnte nicht abgeschlossen werden** fehl und geben eine Fehlermeldung im PowerApps-Portal zurück. Dazu wird eine E-Mail-Benachrichtigung an den Anforderer gesendet. 

![Fehlerstatus](media/solution-checker-exception-status.png)

Durch Auswählen der Portalbenachrichtigung erfolgt eine Verknüpfung zu dieser Seite mit allgemeinen Problemen zur weiteren Problembehandlung. Wenn eine der genannten allgemeinen Probleme das Problem nicht löst, wird auch eine Referenznummer zurückgegeben. Stellen Sie diese Referenznummer dem Microsoft Support zur weiteren Überprüfung bereit.

![Fehlerbenachrichtigung](media/solution-checker-failure-notification.png)

## <a name="solution-checker-fails-due-to-unsupported-version-of-powerapps-checker"></a>Die Lösungsprüfung funktioniert nicht, da die PowerApps-Prüfungsversion nicht unterstützt wird

Die Lösungsprüfung ist eine Funktion der PowerApps-Prüfungs-App.  Wenn Sie eine PowerApps-Prüfungs-App-Version vor **1.0.0.47** installiert haben, wird die Ausführung der Lösungsprüfung möglicherweise nicht erfolgreich abgeschlossen. Sie sollten Ihre PowerApps-Prüfungsversion vom [!INCLUDE [pn-dyn-365-admin-center](../../includes/pn-dyn-365-admin-center.md)] aktualisieren. 

Wenn Sie jedoch eine PowerApps-Prüfungsversion vor **1.0.0.45** installiert haben, empfehlen wir Ihnen, die Lösung zu löschen und erneut zu installieren. Aufgrund der letzten Schemaänderungen kann ein Upgrade der PowerApps-Prüfung von Versionen vor **1.0.0.45** fehlschlagen.

Wenn Sie die bisherigen Ergebnisse von Solution Checker beibehalten möchten, exportieren Sie die Ergebnisse eines früheren Laufs oder exportieren Sie alle Daten von Solution Checker mit [Datenexport nach Excel](../../user/export-data-excel.md), um die Daten aus den folgenden Entitäten zu exportieren:

- Analysekomponente
- Analyseauftrag
- Analyseergebnis
- Analyseergebnisdetail

### <a name="how-to-uninstall-powerapps-checker"></a>So wird die PowerApps-Prüfung deinstalliert

So deinstallieren Sie die PowerApps-Prüfungslösung:

1. Öffnen Sie als Systemadministrator oder als Systemanpasser das PowerApps-Portal, indem Sie zu https://web.powerapps.com/environments navigieren.
2. Wählen Sie **Lösungen** aus.
3. Wählen Sie **PowerApps-Prüfung** und dann in der Symbolleiste der Lösungen **Löschen**.

### <a name="how-to-install-powerapps-checker"></a>So wird die PowerApps-Prüfung installiert

So installieren Sie die PowerApps-Prüfung wieder in Ihrer Common Data Service-Umgebung:

1. Öffnen Sie als Systemadministrator oder Systemanpasser Ihr PowerApps-Portal, indem Sie zu https://web.powerapps.com/environments navigieren.
2. Wählen Sie **Lösungen** aus.
3. Wählen Sie in der Symbolleiste den **Solution Checker** aus und wählen Sie dann **Install**.

## <a name="solution-checker-cant-access-organizations-in-administration-mode"></a>Die Lösungsprüfung kann nicht auf Organisationen im Verwaltungsmodus zugreifen

Organisationen, die in den [Verwaltungsmodus](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/admin/manage-sandbox-instances#administration-mode) gesetzt wurden, schränken den Zugriff absichtlich auf Benutzer mit der Systemadministrator- und Systemanpasser-Rollen ein. Da der PowerApps-Prüfungsanwendungsidentität keine dieser Rollen standardmäßig zugewiesen ist, kann sie nicht auf Organisationen zugreifen, die in diesem Modus ausgeführt werden.

Um die Lösungsprüfung in dieser Organisation zu verwenden, muss der Verwaltungsmodus deaktiviert werden.

### <a name="how-to-disable-administration-mode"></a>So deaktivieren Sie den Verwaltungsmodus

So deaktivieren Sie den Administrationsmodus für eine Organisationsinstanz:

1. Öffnen Sie in der Dynamics 365-Instanzauswahl: https://port.crm.dynamics.com/G/Instances/InstancePicker.aspx.
2. Wählen Sie die Organisationinstanz aus, bei der Probleme mit der Lösungsprüfung auftreten.
3. Wählen Sie **ADMIN**.<br/>
![Instance Admin](media/solution-checker-instance-admin.png)

4. Deaktivieren Sie **Verwaltungsmodus aktivieren**, und wählen Sie dann **Speichern** aus.<br/>
![Admin-Modus deaktivieren](media/solution-checker-instance-disable-admin-mode.png)

5. Führen Sie den Solution Checker erneut aus.

## <a name="solution-checker-fails-due-to-missing-security-roles"></a>Die Lösungsprüfung schlägt aufgrund der fehlenden Sicherheitsrollen fehl

Der Anwendungsbenutzer für die Lösungsprüfung erfordert zwei zugewiesene Sicherheitsrollen, um die erforderlichen Rechte zum Kommunizieren mit der Common Data Service-Organisation zur Verfügung zu stellen. Wenn dem Benutzer **PowerApps-Prüfung** eine dieser Rollen nicht zugewiesen ist, schlagen Versuche, die Analyse auszuführen, Ergebnisse herunterzuladen und das Beenden auszuführen, fehl. Dies tritt am häufigsten auf, wenn Kunden eine Automatisierung eingerichtet haben, die Sicherheitsrollen von unerwarteten Benutzern entfernt. Die folgenden Sicherheitsrollen enthalten minimale erforderliche Berechtigungen:

- Anpassungen exportieren
- Lösungsprüfung

### <a name="how-to-assign-missing-security-roles"></a>So weisen Sie fehlende Sicherheitsrollen zu

So weisen Sie fehlende Sicherheitsrollen zu PowerApps-Prüfungsbenutzern zu:

1. Öffnen Sie die Common Data Service-Organisation und navigieren Sie zu **Einstellungen** > **Sicherheit** > **Benutzer**.
2. Wählen Sie den **PowerApps-Prüfung**-Benutzer aus der Liste der Benutzer aus.
3. Wählen Sie auf der Befehlsleiste auf **ROLLEN VERWALTEN** aus.
4. Aktivieren Sie die Kontrollkästchen für die Rollen **'Anpassungen exportieren'** und **'Lösungsprüfung'**, und wählen Sie dann **OK** aus.<br/>
![Erforderliche Sicherheitsrollen](media/solution-checker-required-roles.png)

5. Führen Sie den Solution Checker erneut aus.

## <a name="solution-checker-fails-due-to-restricted-access-mode"></a>Die Lösungsprüfung schlägt aufgrund des eingeschränkten Zugriffsmodus fehl

Der Anwendungsbenutzer für die Lösungsprüfung erfordert den Zugriffsmodus **'Nicht interaktiv'** oder **'Lesen-Schreiben'**, um mit der Common Data Service-Organisation zu kommunizieren. Wenn der Zugriffsmodus in einen anderen Wert, z. B. **'Verwaltung'** geändert wurde, schlagen Versuche, die Analyse auszuführen, Ergebnisse herunterzuladen und das Beenden auszuführen, fehl.

Um dieses Problem zu beheben, müssen Sie den Anwendungsbenutzer **PowerApps-Prüfung** mit dem Zugriffsmodus 'Nicht interaktiv' aktualisieren.

### <a name="how-to-update-user-access-mode"></a>So aktualisieren Sie den Zugriffsmodus eines Benutzers

So aktualisieren Sie den Zugriffsmodus für den PowerApps-Prüfungsbenutzer:

1. Öffnen Sie die Common Data Service-Organisation und navigieren Sie zu **Einstellungen** > **Sicherheit** > **Benutzer**.
2. Wählen Sie den **PowerApps-Prüfung**-Benutzer aus der Liste der Benutzer aus, und doppelklicken Sie, um das Benutzerformular zu öffnen.
3. Scrollen Sie zum Abschnitt **'Verwaltung'** > **'Informationen zur Clientzugriffslizenz (CAL)'** des Formulars.
4. Wählen Sie **'Nicht interaktiv'** im Dropdown-Steuerelement **Zugriffsmodus** aus.<br/>
![Zugriffsmodus](media/solution-checker-access-mode.png)

5. Speichern und schließen Sie das Benutzerformular.
6. Führen Sie den Solution Checker erneut aus.

## <a name="solution-checker-fails-due-to-disabled-first-party-application-in-aad"></a>Die Lösungsprüfung schlägt wegen der deaktivierten Erstanbieteranwendung in AAD fehl

Die Erstanbieter-Unternehmensanwendungsidentität, die von der Lösungsprüfung (PowerApps-Advisor) verwendet wird, sollte in Azure Active Directory (AAD) nicht deaktiviert werden. Wird sie deaktiviert, ist keine Authentifizierung der Identität möglich, wenn Bearertoken für Common Data Service und andere erforderliche Ressourcenanbieter im Auftrag des anfordernden Benutzers anfordert werden. 

Führen Sie die unten genannten Schritte aus, um zu überprüfen, ob die Anwendungsidentität in AAD deaktiviert wurde, und aktivieren Sie die Anwendung, falls erforderlich.

### <a name="how-to-verify-andor-modify-application-enabled-status"></a>So überprüfen und/der ändern Sie den Anwendungs-Aktiviert-Status

So überprüfen und/der ändern Sie den Aktiviert-Status der PowerApps-Advisor-Unternehmensanwendungsidentität

1. Greifen Sie auf den Mandanten im [Azure Active Directory (AAD)-Portal](https://aad.portal.azure.com/) zu.
2. Navigieren Sie zu **Unternehmensanwendungen**.
3. Wählen Sie **Alle Anwendungen** aus, und suchen Sie nach **PowerApps-Advisor**.<br/>
![Suchen der PowerApps-Advisor-App](media/solution-checker-search-advisor-app.png)

4. Wählen Sie **PowerApps-Advisor** aus, um die App-Details anzuzeigen.
5. Wählen Sie **Eigenschaften** aus.
6. Überprüfen Sie den Status für **Aktiviert für die Benutzeranmeldung**. Wenn **'Nein'**, wurde die Anwendung deaktiviert.<br/>
![Deaktivierte Unternehmens-App](media/solution-checker-disabled-app.png)

7. Wählen Sie das Steuerelement aus, um den Wert in **'Ja'** zu wechseln. Dadurch wird die Anwendung aktiviert.<br/>
![Aktivieren der PowerApps-Advisor-App](media/solution-checker-enable-app.png)

8. Wählen Sie **Speichern** aus. Die Anwendung ist jetzt aktiviert. Möglicherweise müssen Sie einige Minuten warten, bis die Änderungen übernommen wurden.
9. Führen Sie den Solution Checker erneut aus.

> [!IMPORTANT]
> Sie benötigen Administratorrechte in Azure Active Directory (AAD), um Unternehmensanwendungen zu bearbeiten.

## <a name="solution-checker-fails-to-export-solutions-with-draft-business-process-flow-components"></a>Die Lösungsprüfung kann keine Lösungen mit Geschäftsprozessfluss-Entwurfskomponenten exportieren

Wenn eine Lösung eine Geschäftsprozessflusskomponente im Entwurfsstatus enthält, der zuvor nie aktiviert wurde, kann die Lösungsprüfung die Lösung für die Analyse nicht exportieren. Dieser Fehler findet sich nicht nur in der Lösungsprüfung und ist auf den Geschäftsprozessfluss zurückzuführen, der eine Abhängigkeit zu einer unterstützenden (benutzerdefinierten) Entitätskomponente besitzt, die nicht erstellt wird, bis der Geschäftsprozessfluss zum ersten Mal aktiviert ist. Dieses Problem kann auch auftreten, wenn ein Geschäftsprozessfluss im Projektmappen-Explorer aktiviert ist.

Referenz [Wissensdatenbankartikel #4337537: Ungültiger Export – Geschäftsprozessentität fehlt](https://support.microsoft.com/en-hk/help/4337537/invalid-export-business-process-entity-missing) für Einzelheiten zum Fehler und Schritte zur Lösung.

## <a name="solution-checker-fails-to-export-patched-solutions"></a>Die Lösungsprüfung kann keine gepatchten Lösungen exportieren

Wenn eine Lösung mit einem [Patch](https://docs.microsoft.com/powerapps/developer/common-data-service/create-patches-simplify-solution-updates) installiert wurde, kann der Solution Checker die Lösung nicht zur Analyse exportieren. Wenn eine Lösung mit einem Patch versehen wurde, wird die ursprüngliche Lösung gesperrt und kann nicht geändert oder exportiert werden, solange es abhängige Patches in dem Unternehmen gibt, die die Lösung als übergeordnete Lösung identifizieren.

Um dieses Problem zu lösen, klonen Sie die Lösung so, dass für alle mit der Lösung verbundenen Patches ein Rollup in die neu erstellte Lösung ausgeführt wird. Dadurch wird die Lösung entsperrt und die Lösung kann aus dem System exportiert werden.  Weitere Informationen finden Sie unter [Klonen einer Lösung](use-segmented-solutions-patches-simplify-updates.md#clone-a-solution).

## <a name="solution-checker-will-not-analyze-empty-solutions"></a>Die Lösungsprüfung analysiert keine leeren Lösungen

Wenn die Lösungsprüfung eine Lösung exportiert, die keine zu analysierenden Komponenten enthält, beendet sie die weitere Verarbeitung und wertet die Ausführung als Fehler. Stellen Sie sicher, dass die ausgewählte Lösung, die für eine Lösungsprüfungsanalyse übertragen wird, mindestens eine Komponente enthält.

## <a name="solution-checker-fails-to-export-large-solutions"></a>Die Lösungsprüfung kann keine großen Lösungen exportieren

Das primäre Szenario für einen Fehler beim Exportieren einer großen Lösung aus der Common Data Service-Umgebung umfasst eine Timeout-Ausnahme bei der Exportanforderung. Dies tritt auf, wenn die Anforderung 20 Minuten übersteigt. Große Lösungen, wie die Standardlösung, können innerhalb dieser Zeit nicht exportiert werden, und die Prüfung wird nicht erfolgreich abgeschlossen. Wenn bei der Lösungsprüfung ein Timeout beim Export auftritt, wird es diesen dreimal wiederholen, bevor es den Auftrag nicht bearbeitet, sodass es über eine Stunde dauern kann, bis Sie eine Fehlermeldung erhalten.

Die Problemumgehung besteht darin, kleinere Lösungen mit weniger zu analysierenden Komponenten zu erstellen. Wenn die Dateigröße der Lösung auf viele Plug-In-Assembly-Komponenten zurückzuführen ist, finden Sie unter [Optimierung der Entwicklung kundenspezifischer Assemblys](../../developer/common-data-service/best-practices/business-logic/optimize-assembly-development.md) weitere Informationen. 

> [!IMPORTANT]
> Um Fehlalarme zu minimieren, stellen Sie sicher, dass Sie abhängige Anpassungen vornehmen. Wenn Sie eine Lösung anlegen und diese Komponenten hinzufügen, fügen Sie Folgendes hinzu:
> - Wenn Sie Plugins hinzufügen, fügen Sie die Schritte der SDK-Nachrichtenverarbeitung für das Plug-in hinzu.
> - Wenn Sie Entitätsformulare hinzufügen, fügen Sie die JavaScript-Webressourcen hinzu, die an die Formularereignisse angehängt sind.  
> - Wenn Sie JavaScript-Webressourcen hinzufügen, schließen Sie alle abhängigen JavaScript-Webressourcen ein.
> - Wenn Sie HTML-Webressourcen hinzufügen, schließen Sie alle abhängigen Skripte ein, die in der HTML-Webressource definiert sind.
> - Wenn Sie benutzerdefinierte Workflows hinzufügen, fügen Sie die Assembly hinzu, die innerhalb des Workflows verwendet wird.

## <a name="line-number-references-for-issues-in-html-resources-with-embedded-javascript-are-not-correct"></a>Zeilennummernverweise bei Problemen in HTML-Ressourcen mit eingebettetem JavaScript sind nicht korrekt. 

Wenn HTML-Webressourcen innerhalb des Solution Checker verarbeitet werden, wird die HTML-Webressource getrennt von JavaScript innerhalb der HTML-Webressource verarbeitet. Aus diesem Grund ist die Zeilennummer der Verletzung, die unter `<script>` der HTML-Webressource gefunden wurde, nicht korrekt.

## <a name="web-unsupported-syntax-issue-for-web-resources"></a>Web-ununterstützte Syntaxprobleme bei Web-Ressourcen

ECMAScript 6 (2015) oder neuere Versionen werden derzeit für die Lösungsprüfung nicht unterstützt. Wenn die Lösungsprüfung JavaScript mit ECMAScript 6 oder höher analysiert, wird ein webgestütztes Syntaxproblem für die Webressource gemeldet.  

## <a name="multiple-violations-reported-for-plug-ins-and-workflow-activities-based-on-call-scope"></a>Mehrere Verletzungen für Plug-Ins und Workflowaktivitäten anhand des Anrufumfangs gemeldet

Für Plug-In- und Workflowaktivitätsregeln, bei denen das Problem nur im aufrufenden Kontext relevant ist, beginnt das Solution Checker-Tool die Analyse bei der IPlugin-Schnittstellenimplementierung und durchläuft ein Anrufdiagramm, um Probleme im Umfang der Implementierung zu erkennen.  In einigen Fällen gehen viele Anrufpfade ggf. am gleichen Standort ein, wo das Problem erkannt wird.  Da das Problem für den Anrufumfang relevant ist, meldet das Tool möglicherweise auf Grundlage dieses Umfangs, statt auf unterschiedlichen Standorten, um ein besseres Bild der Auswirkungen zu bieten. Daher verweisen verschiedene Probleme möglicherweise einen Standort, der behoben werden soll.

## <a name="see-also"></a>Siehe auch
[Bewährte Methoden sowie Anweisungen zum Common Data Service](../../developer/common-data-service/best-practices/index.md)<br/>
[Best Practices und Anleitungen für modellgetriebene Anwendungen](../../developer/model-driven-apps/best-practices/index.md)<br/>
