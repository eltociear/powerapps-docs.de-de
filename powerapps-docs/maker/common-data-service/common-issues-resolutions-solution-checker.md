---
title: Häufige Probleme und Lösungen für Lösungsprüfer | Microsoft Docs
description: " Eine Liste der häufigsten Probleme und Lösungen im Lösungsprüfer"
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
ms.reviewer: ''
robots: noindex,nofollow
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 2280ea28178a85429367ea0359660b3b94f5f99b
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3154720"
---
# <a name="common-issues-and-resolutions-for-solution-checker"></a>Häufige Probleme und Lösungen für Lösungsprüfer

Dieser Artikel listet einige häufige Probleme auf, die bei der Verwendung des Lösungsprüfer auftreten können. Gegebenenfalls werden Workarounds angeboten.

## <a name="youre-unable-to-use-solution-checker-to-run-analysis-or-download-results"></a>Es ist nicht möglich, den Lösungsprüfer zu verwenden, um die Analyse auszuführen oder Ergebnisse herunterzuladen

Kurz nach dem Senden einer Lösungsprüfungsanforderung zum Ausführen einer Analyse oder Herunterladen von Ergebnissen wird der Vorgang nicht abgeschlossen und eine Fehlermeldung angezeigt, wie z. B.:

> *„Wir konnten die Überprüfung der Lösung **[Name der Lösung]** nicht ausführen. Versuchen sie es noch einmal.“*

Wenn möglich, versucht der Lösungsprüfer eine bestimmte Fehlermeldung mit einem Link zu den Details zu der möglichen Ursache und Lösungsschritten zurückzugeben. Wählen Sie für Details **'Weitere Informationen'** aus.

![Fehlermeldungsleiste](media/solution-checker-missing-roles-error.png)

Fehler, die während der Hintergrundverarbeitung der Analyse auftreten, schlagen mit dem Status **Konnte nicht abgeschlossen werden** fehl und geben eine Fehlermeldung im Power Apps-Portal zurück. Dazu wird eine E-Mail-Benachrichtigung an den Anforderer gesendet.

![Fehlerstatus](media/solution-checker-exception-status.png)

Durch Auswählen der Portalbenachrichtigung erfolgt eine Verknüpfung zu dieser Seite mit allgemeinen Problemen zur weiteren Problembehandlung. Wenn eine der genannten allgemeinen Probleme das Problem nicht löst, wird auch eine Referenznummer zurückgegeben. Stellen Sie diese Referenznummer dem Microsoft Support zur weiteren Überprüfung bereit.

![Fehlerbenachrichtigung](media/solution-checker-failure-notification.png)

## <a name="solution-checker-fails-due-to-unsupported-version-of-power-apps-checker"></a>Der Lösungsprüfer funktioniert nicht, da die Power Apps-Prüfungsversion nicht unterstützt wird

Der Lösungsprüfer ist eine Funktion, die vom Power Apps-Prüfungs-App aktiviert wird.  Wenn Sie eine Power Apps-Prüfungs-App-Version vor **1.0.0.47** installiert haben, wird die Ausführung der Lösungsprüfung möglicherweise nicht erfolgreich abgeschlossen. Sie sollten Ihre Power Apps-Prüfungsversion vom [!INCLUDE [pn-dyn-365-admin-center](../../includes/pn-dyn-365-admin-center.md)] aktualisieren.

Wenn Sie jedoch eine Power Apps-Prüfungsversion vor **1.0.0.45** installiert haben, empfehlen wir Ihnen, die Lösung zu löschen und erneut zu installieren. Aufgrund der letzten Schemaänderungen kann ein Upgrade der Power Apps-Prüfung von Versionen vor **1.0.0.45** fehlschlagen.

Wenn Sie die bisherigen Ergebnisse vom Lösungsprüfer beibehalten möchten, exportieren Sie die Ergebnisse eines früheren Laufs oder exportieren Sie alle Daten vom Lösungsprüfer mit [Datenexport nach Excel](../../user/export-data-excel.md), um die Daten aus den folgenden Entitäten zu exportieren:

- Analysekomponente
- Analyseauftrag
- Analyseergebnis
- Analyseergebnisdetail

### <a name="how-to-uninstall-power-apps-checker"></a>So wird die Power Apps-Prüfung deinstalliert

So deinstallieren Sie die Power Apps-Prüfungslösung:

1. Öffnen Sie als Systemadministrator oder als Systemanpasser das Power Apps-Portal, indem Sie zu https://make.powerapps.com/environments navigieren.
2. Wählen Sie **Lösungen** aus.
3. Wählen Sie **Power Apps-Prüfung** und dann in der Symbolleiste der Lösungen **Löschen**.

### <a name="how-to-install-power-apps-checker"></a>So wird die Power Apps-Prüfung installiert

So installieren Sie die Power Apps-Prüfung wieder in Ihrer Common Data Service-Umgebung:

1. Öffnen Sie als Systemadministrator oder Systemanpasser Ihr Power Apps-Portal, indem Sie zu https://make.powerapps.com/environments navigieren.
2. Wählen Sie **Lösungen** aus.
3. Wählen Sie in der Symbolleiste den **Solution Checker** aus und wählen Sie dann **Installieren**.

## <a name="solution-checker-cant-access-organizations-in-administration-mode"></a>Die Lösungsprüfung kann nicht auf Organisationen im Verwaltungsmodus zugreifen

Organisationen, die in den [Verwaltungsmodus](https://docs.microsoft.com/dynamics365/customer-engagement/admin/manage-sandbox-instances#administration-mode) gesetzt wurden, schränken den Zugriff absichtlich auf Benutzer mit der Systemadministrator- und Systemanpasser-Rollen ein. Da der Power Apps-Prüfungsanwendungsidentität keine dieser Rollen standardmäßig zugewiesen ist, kann sie nicht auf Organisationen zugreifen, die in diesem Modus ausgeführt werden.

Um den Lösungsprüfer in dieser Organisation zu verwenden, muss der Verwaltungsmodus deaktiviert werden.

### <a name="how-to-disable-administration-mode"></a>So deaktivieren Sie den Verwaltungsmodus

So deaktivieren Sie den Administrationsmodus für eine Organisationsinstanz:

1. Öffnen Sie in der Dynamics 365-Instanzauswahl: https://port.crm.dynamics.com/G/Instances/InstancePicker.aspx.
2. Wählen Sie die Organisationinstanz aus, bei der Probleme mit dem Lösungsprüfer auftreten.
3. Wählen Sie **ADMIN**.

![Instance Admin](media/solution-checker-instance-admin.png)

4. Deaktivieren Sie **Verwaltungsmodus aktivieren**, und wählen Sie dann **Speichern** aus.

![Admin-Modus deaktivieren](media/solution-checker-instance-disable-admin-mode.png)

5. Führen Sie den Lösungsprüfer erneut aus.

## <a name="solution-checker-fails-due-to-missing-security-roles"></a>Der Lösungsprüfer schlägt aufgrund der fehlenden Sicherheitsrollen fehl

Der Anwendungsbenutzer für die Lösungsprüfung erfordert zwei zugewiesene Sicherheitsrollen, um die erforderlichen Rechte zum Kommunizieren mit der Common Data Service-Organisation zur Verfügung zu stellen. Wenn dem Benutzer **Power Apps-Prüfung** eine dieser Rollen nicht zugewiesen ist, schlagen Versuche, die Analyse auszuführen, Ergebnisse herunterzuladen und das Beenden auszuführen, fehl. Dies tritt am häufigsten auf, wenn Kunden eine Automatisierung eingerichtet haben, die Sicherheitsrollen von unerwarteten Benutzern entfernt. Die folgenden Sicherheitsrollen enthalten minimale erforderliche Berechtigungen:

- Anpassungen exportieren
- Lösungsprüfung

### <a name="how-to-assign-missing-security-roles"></a>So weisen Sie fehlende Sicherheitsrollen zu

So weisen Sie fehlende Sicherheitsrollen zu Power Apps-Prüfungsbenutzern zu:

1. Öffnen Sie die Common Data Service-Organisation und navigieren Sie zu **Einstellungen** > **Sicherheit** > **Benutzer**.
2. Wählen Sie den **Power Apps-Prüfung**-Benutzer aus der Liste der Benutzer aus.
3. Wählen Sie auf der Befehlsleiste auf **ROLLEN VERWALTEN** aus.
4. Aktivieren Sie die Kontrollkästchen für die Rollen **'Anpassungen exportieren'** und **'Lösungsprüfung'**, und wählen Sie dann **OK** aus.

![Erforderliche Sicherheitsrollen](media/solution-checker-required-roles.png)

5. Führen Sie den Lösungsprüfer erneut aus.

## <a name="solution-checker-fails-due-to-restricted-access-mode"></a>Die Lösungsprüfung schlägt aufgrund des eingeschränkten Zugriffsmodus fehl

Der Anwendungsbenutzer für den Lösungsprüfer erfordert den Zugriffsmodus **'Nicht interaktiv'** oder **'Lesen-Schreiben'**, um mit der Common Data Service-Organisation zu kommunizieren. Wenn der Zugriffsmodus in einen anderen Wert, z. B. **'Verwaltung'** geändert wurde, schlagen Versuche, die Analyse auszuführen, Ergebnisse herunterzuladen und das Beenden auszuführen, fehl.

Um dieses Problem zu beheben, müssen Sie den Anwendungsbenutzer **Power Apps-Prüfung** mit dem Zugriffsmodus 'Nicht interaktiv' aktualisieren.

### <a name="how-to-update-user-access-mode"></a>So aktualisieren Sie den Zugriffsmodus eines Benutzers

So aktualisieren Sie den Zugriffsmodus für den Power Apps-Prüfungsbenutzer:

1. Öffnen Sie die Common Data Service-Organisation und navigieren Sie zu **Einstellungen** > **Sicherheit** > **Benutzer**.
2. Wählen Sie den **Power Apps-Prüfung**-Benutzer aus der Liste der Benutzer aus, und doppelklicken Sie, um das Benutzerformular zu öffnen.
3. Scrollen Sie zum Abschnitt **'Verwaltung'** > **'Informationen zur Clientzugriffslizenz (CAL)'** des Formulars.
4. Wählen Sie **'Nicht interaktiv'** im Dropdown-Steuerelement **Zugriffsmodus** aus.

![Zugriffsmodus](media/solution-checker-access-mode.png)

5. Speichern und schließen Sie das Benutzerformular.
6. Führen Sie den Lösungsprüfer erneut aus.

## <a name="solution-checker-fails-due-to-disabled-application-user"></a>Die Lösungsprüfung schlägt wegen der deaktivierten Benutzeranwendung fehl

Der Power Apps Anwendungsprüfer-Bentuzer in der Common Data Service Organisation mit den zu analysierenden Lösungen muss aktiviert sein. Wenn der Anwendungsbenutzer deaktiviert wird, schlagen Anforderungen zum Analysieren von Lösungen in derselben Organisation fehl. Wenn diese Fehlermeldung angezeigt wird, überprüfen Sie zunächst, ob der Power Apps Anwendungsbenutzerprüfer in der Tat deaktiviert ist. Befolgen Sie dann die unten aufgeführten Schritte zur Schadensbegrenzung.

![Deaktivierter Benutzerstatus](media/solution-checker-disabled-application-user.png)

### <a name="how-to-enable-the-power-apps-checker-application-user"></a>So aktivieren Sie die Power Apps Anwendungsbenutzerprüfung

1. Wählen Sie im Power Platform Admin Center die Umgebung aus und gehen Sie zu **Einstellungen** > **Benutzer + Berechtigungen**  > **Benutzer**.
2. In der Ansicht **Anwendungsbenutzer** wählen Sie das Häkchen neben dem Power Apps Anwendungsbenutzerprüfer aus.
3. Wählen Sie auf der Aktionssymbolleiste **Aktivieren** aus.

![Benutzer aus Ansicht aktivieren](media/solution-checker-enable-application-user-view.png)

4. Klicken oder tippen Sie in der Meldung **Aktivierung von Benutzer bestätigen** auf **Aktivieren**.
5. Ein alternativer Ansatz besteht darin, das Anwendungsbenutzerformular zu öffnen und den Status **aktiviert** in der Formularfußzeile zu wählen. **Speichern** Sie die Änderung.

![Benutzer aus Formular aktivieren](media/solution-checker-enable-application-user-form.png)

## <a name="common-plugin-conditions-that-cause-solution-checker-to-fail"></a>Allgemeine Plugin-Bedingungen, bei denen die Lösungsprüfung fehlschlägt

Wenn der Lösungsprüfer Analyseanforderungen empfängt und verarbeitet, muss er den Common Data Service Endpunkt aufrufen, um relevante Auftragsdaten abzurufen/zu aktualisieren und die ausgewählten Lösungen zu exportieren. Jede Interaktion des Lösungsprüferservice mit dem Common Data Service könnte möglicherweise einen oder mehrere Plug-In-Schritte auslösen, die für die in der Anforderung übermittelte Nachricht registriert wurden. Diese Plugins können wiederum Bedingungen einführen, die verhindern, dass die Nachricht wie erwartet vom Common Data Service behandelt wird und die Fähigkeit des Lösungsprüfers unterbricht, um den angeforderten Analysejob zu verarbeiten. Ähnliche Situationen können auftreten, wenn Lösungsprüfer-Auftragsergebnisse heruntergeladen oder ein laufender Analyseauftrag abgebrochen werden.

Typischer Common Data Service Vorgang, der vom Lösungsprüfer angefordert wird:

- Abrufen von Lösungs-, Systembenutzer- und Organisationsentitätsdaten
- Erstellen, Aktualisieren und Abrufen von Analysejob-, Analysekomponenten- und Analyseergebnis-Entitätsdaten
- Exportieren von Lösungen

### <a name="plugin-step-registered-to-execute-in-context-of-a-unlicensed-user"></a>Plugin-Schritt registriert, um im Kontext eines nicht lizenzierten Benutzers ausgeführt zu werden

Wenn die Lösungsüberprüfung aufgrund einer Ausnahme "Nicht lizenzierter Benutzer" fehlschlägt, wird dies häufig durch einen ausgelösten Plug-In-Schritt verursacht, der für die Ausführung im Kontext eines bestimmten Systembenutzers konfiguriert ist, der zurzeit nicht lizenziert ist. Stellen Sie sicher, dass alle Plug-In-Schritte, die vom Lösungsprüfer ausgelöst werden könnten, im Kontext eines lizenzierten Benutzers ausgeführt werden.

>[!IMPORTANT]
>Es wird dringend empfohlen, die Plug-In-Schritte so zu konfigurieren, dass sie im Kontext des aufrufenden Benutzers ausgeführt werden, und nicht für bestimmte Benutzer, denen eine Lizenz entzogen wird.

### <a name="plugin-step-performs-operations-that-require-privileges-not-granted-to-power-apps-checker-application-user"></a>Der Plug-In-Schritt führt Vorgänge aus, für die Rchte erforderlich sind, die nicht gewährt wurden für Power Apps Anwendungsbenutzerprüfer

Wenn die Lösungsprüfung fehlschlägt, weil Common Data Service den Zugriff aufgrund fehlender Berechtigungen verweigert, wird dies häufig durch einen ausgelösten Plug-In-Schritt verursacht, der Vorgänge ausführt, für die Berechtigungen erforderlich sind, die dem Benutzer derzeit nicht gewährt werden unter Power Apps Anwendungsbenutzerprüfer Konfigurieren Sie den Plug-In-Schritt so, dass er für den von der Lösungsprüfung aufgerufenen Vorgang nicht ausgeführt wird, oder erteilen Sie dem Power Apps Anwendungsbenutzerprüfer die erforderlichen Rechte zum Ausführen des benutzerdefinierten Plug-In-Schritts besitzt.

### <a name="plugin-step-unexpectedly-interrupts-execution-by-throwing-invalidpluginexecutionexception"></a>Der Plug-In-Schritt unterbricht die Ausführung unerwartet, indem er eine InvalidPluginExecutionException auslöst

Wenn die Lösungsprüfung aufgrund des Fehlers "ISV abgebrochener Code" fehlschlägt, wurde ein Plug-In-Schritt ausgelöst, der die Ausführung explizit durch Auslösen einer InvalidPluginExcecutionException unterbrach. Konfigurieren Sie den Plug-In-Schritt so, dass er für den vom Lösungsprüfer aufgerufenen Vorgang nicht ausgeführt wird, oder passen Sie die Plug-In-Implementierung so an, dass die Ausführung basierend auf den vom Lösungsprüfer angegebenen Bedingungen nicht unterbrochen wird.

## <a name="solution-checker-fails-due-to-disabled-first-party-application-in-aad"></a>Der Lösungsprüfer schlägt wegen der deaktivierten Erstanbieteranwendung in AAD fehl

Die Erstanbieter-Unternehmensanwendungsidentität, die vom Lösungsprüfer (PowerApps-Advisor) verwendet wird, sollte in Azure Active Directory (AAD) nicht deaktiviert werden. Wird sie deaktiviert, ist keine Authentifizierung der Identität möglich, wenn Bearertoken für Common Data Service und andere erforderliche Ressourcenanbieter im Auftrag des anfordernden Benutzers anfordert werden.

Führen Sie die unten genannten Schritte aus, um zu überprüfen, ob die Anwendungsidentität in AAD deaktiviert wurde, und aktivieren Sie die Anwendung, falls erforderlich.

### <a name="how-to-verify-andor-modify-application-enabled-status"></a>So überprüfen und/der ändern Sie den Anwendungs-Aktiviert-Status

So überprüfen und/der ändern Sie den Aktiviert-Status der PowerApps-Advisor-Unternehmensanwendungsidentität

1. Greifen Sie auf den Mandanten im [Azure Active Directory (AAD)-Portal](https://aad.portal.azure.com/) zu.
2. Navigieren Sie zu **Unternehmensanwendungen**.
3. Wählen Sie **Alle Anwendungen** aus, und suchen Sie nach **PowerApps-Advisor**.

![Suchen der PowerApps-Advisor-App](media/solution-checker-search-advisor-app.png)

4. Wählen Sie **PowerApps-Advisor** aus, um die App-Details anzuzeigen.
5. Wählen Sie **Eigenschaften** aus.
6. Überprüfen Sie den Status für **Aktiviert für die Benutzeranmeldung**. Wenn **'Nein'**, wurde die Anwendung deaktiviert.

![Deaktivierte Unternehmens-App](media/solution-checker-disabled-app.png)

7. Wählen Sie das Steuerelement aus, um den Wert in **'Ja'** zu wechseln. Dadurch wird die Anwendung aktiviert.

![Aktivieren der PowerApps-Advisor-App](media/solution-checker-enable-app.png)

8. Wählen Sie **Speichern** aus. Die Anwendung ist jetzt aktiviert. Möglicherweise müssen Sie einige Minuten warten, bis die Änderungen übernommen wurden.
9. Führen Sie den Lösungsprüfer erneut aus.

> [!IMPORTANT]
> Sie benötigen Administratorrechte in Azure Active Directory (AAD), um Unternehmensanwendungen zu bearbeiten.

## <a name="solution-checker-fails-to-export-solutions-with-draft-business-process-flow-components"></a>Der Lösungsprüfer kann keine Lösungen mit Geschäftsprozessfluss-Entwurfskomponenten exportieren

Wenn eine Lösung eine Geschäftsprozessflusskomponente im Entwurfsstatus enthält, der zuvor nie aktiviert wurde, kann die Lösungsprüfung die Lösung für die Analyse nicht exportieren. Dieser Fehler findet sich nicht nur in der Lösungsprüfung und ist auf den Geschäftsprozessfluss zurückzuführen, der eine Abhängigkeit zu einer unterstützenden (benutzerdefinierten) Entitätskomponente besitzt, die nicht erstellt wird, bis der Geschäftsprozessfluss zum ersten Mal aktiviert ist. Dieses Problem kann auch auftreten, wenn ein Geschäftsprozessfluss im Projektmappen-Explorer aktiviert ist.

Referenz [Wissensdatenbankartikel #4337537: Ungültiger Export – Geschäftsprozessentität fehlt](https://support.microsoft.com/en-hk/help/4337537/invalid-export-business-process-entity-missing) für Einzelheiten zum Fehler und Schritte zur Lösung.

## <a name="solution-checker-fails-to-export-patched-solutions"></a>Die Lösungsprüfung kann keine gepatchten Lösungen exportieren

Wenn eine Lösung mit einem [Patch](https://docs.microsoft.com/powerapps/developer/common-data-service/create-patches-simplify-solution-updates) installiert wurde, kann der Solution Checker die Lösung nicht zur Analyse exportieren. Wenn eine Lösung mit einem Patch versehen wurde, wird die ursprüngliche Lösung gesperrt und kann nicht geändert oder exportiert werden, solange es abhängige Patches in dem Unternehmen gibt, die die Lösung als übergeordnete Lösung identifizieren.

Um dieses Problem zu lösen, klonen Sie die Lösung so, dass für alle mit der Lösung verbundenen Patches ein Rollup in die neu erstellte Lösung ausgeführt wird. Dadurch wird die Lösung entsperrt und die Lösung kann aus dem System exportiert werden.  Weitere Informationen finden Sie unter [Klonen einer Lösung](solution-patches.md#clone-a-solution).

## <a name="solution-checker-will-not-analyze-empty-solutions"></a>Der Lösungsprüfer analysiert keine leeren Lösungen

Wenn der Lösungsprüfer eine Lösung exportiert, die keine zu analysierenden Komponenten enthält, beendet er die weitere Verarbeitung und wertet die Ausführung als Fehler. Stellen Sie sicher, dass die ausgewählte Lösung, die für eine Lösungsprüfungsanalyse übertragen wird, mindestens eine Komponente enthält.

## <a name="solution-checker-fails-to-export-large-solutions"></a>Die Lösungsprüfung kann keine großen Lösungen exportieren

Das primäre Szenario für einen Fehler beim Exportieren einer großen Lösung aus der Common Data Service-Umgebung umfasst eine Timeout-Ausnahme bei der Exportanforderung. Dies tritt auf, wenn die Anforderung 20 Minuten übersteigt. Große Lösungen, wie die Standardlösung, können innerhalb diesers Zeitrahmens nicht exportiert werden, und die Prüfung wird nicht erfolgreich abgeschlossen. Wenn beim Lösungsprüfer ein Timeout beim Export auftritt, wird es diesen dreimal wiederholen, bevor es den Auftrag nicht bearbeitet, sodass es über eine Stunde dauern kann, bis Sie eine Fehlermeldung erhalten.

Die Problemumgehung besteht darin, kleinere Lösungen mit weniger zu analysierenden Komponenten zu erstellen. Wenn die Dateigröße der Lösung auf viele Plug-In-Assembly-Komponenten zurückzuführen ist, finden Sie unter [Optimierung der Entwicklung kundenspezifischer Assemblys](../../developer/common-data-service/best-practices/business-logic/optimize-assembly-development.md) weitere Informationen.

> [!IMPORTANT]
> Um Fehlalarme zu minimieren, stellen Sie sicher, dass Sie abhängige Anpassungen vornehmen. Wenn Sie eine Lösung anlegen und diese Komponenten hinzufügen, fügen Sie Folgendes hinzu:
> - Wenn Sie Plugins hinzufügen, fügen Sie die Schritte der SDK-Nachrichtenverarbeitung für das Plug-in hinzu.
> - Wenn Sie Entitätsformulare hinzufügen, fügen Sie die JavaScript-Webressourcen hinzu, die an die Formularereignisse angehängt sind.  
> - Wenn Sie JavaScript-Webressourcen hinzufügen, schließen Sie alle abhängigen JavaScript-Webressourcen ein.
> - Wenn Sie HTML-Webressourcen hinzufügen, schließen Sie alle abhängigen Skripte ein, die in der HTML-Webressource definiert sind.
> - Wenn Sie benutzerdefinierte Workflows hinzufügen, fügen Sie die Assembly hinzu, die innerhalb des Workflows verwendet wird.

## <a name="line-number-references-for-issues-in-html-resources-with-embedded-javascript-are-not-correct"></a>Zeilennummernverweise bei Problemen in HTML-Ressourcen mit eingebettetem JavaScript sind nicht korrekt.

Wenn HTML-Webressourcen innerhalb des Lösungsprüfer verarbeitet werden, wird die HTML-Webressource getrennt von JavaScript innerhalb der HTML-Webressource verarbeitet. Aus diesem Grund ist die Zeilennummer der Verletzung, die unter `<script>` der HTML-Webressource gefunden wurde, nicht korrekt.

## <a name="web-unsupported-syntax-issue-for-web-resources"></a>Web-ununterstützte Syntaxprobleme bei Web-Ressourcen

ECMAScript 6 (2015) oder neuere Versionen werden derzeit für den Lösungsprüfer nicht unterstützt. Wenn der Lösungsprüfer JavaScript mit ECMAScript 6 oder höher analysiert, wird ein webgestütztes Syntaxproblem für die Webressource gemeldet.  

## <a name="multiple-violations-reported-for-plug-ins-and-workflow-activities-based-on-call-scope"></a>Mehrere Verletzungen für Plug-Ins und Workflowaktivitäten anhand des Anrufumfangs gemeldet

Für Plug-In- und Workflowaktivitätsregeln, bei denen das Problem nur im aufrufenden Kontext relevant ist, beginnt das Lösungsprüfer-Tool die Analyse bei der IPlugin-Schnittstellenimplementierung und durchläuft ein Anrufdiagramm, um Probleme im Umfang der Implementierung zu erkennen.  In einigen Fällen gehen viele Anrufpfade ggf. am gleichen Standort ein, wo das Problem erkannt wird.  Da das Problem für den Anrufumfang relevant ist, meldet das Tool möglicherweise auf Grundlage dieses Umfangs, statt auf unterschiedlichen Standorten, um ein besseres Bild der Auswirkungen zu bieten. Daher verweisen verschiedene Probleme möglicherweise einen Standort, der behoben werden soll.

## <a name="see-also"></a>Siehe auch

[Bewährte Methoden sowie Anweisungen zum Common Data Service](../../developer/common-data-service/best-practices/index.md)

[Best Practices und Anleitungen für modellgetriebene Anwendungen](../../developer/model-driven-apps/best-practices/index.md)
