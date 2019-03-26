---
title: Häufige Probleme und Lösungen für Solution Checker | Microsoft Docs
description: ' Eine Liste der häufigsten Probleme und Lösungen im Solution Checker'
keywords: ''
ms.date: 02/11/2019
ms.service:
  - powerapps
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
# Häufige Probleme und Lösungen für Solution Checker

Dieser Artikel listet einige häufige Probleme auf, die bei der Verwendung des Solution Checker auftreten können. Gegebenenfalls werden Workarounds angeboten.

## Solution Checker läuft nicht, da die PowerApps Checker-Version installiert ist.
Solution Checker ist eine Funktion der PowerApps Checker-Lösung.  Wenn Sie eine PowerApps Checker-Version vor 1.0.0.47 haben, wird der Solution Checker-Lauf nicht erfolgreich abgeschlossen. Sie sollten Ihre PowerApps Checker-Version von der [!INCLUDE [pn-dyn-365-admin-center](../../includes/pn-dyn-365-admin-center.md)] aktualisieren. 

Wenn Sie jedoch eine PowerApps Checker-Version vor 1.0.0.45 installiert haben, empfehlen wir Ihnen, die Lösung zu löschen und erneut zu installieren. Aufgrund der letzten Schemaänderungen kann ein Upgrade von PowerApps Checker von Versionen vor 1.0.0.45 fehlschlagen.

Wenn Sie die bisherigen Ergebnisse von Solution Checker beibehalten möchten, exportieren Sie die Ergebnisse eines früheren Laufs oder exportieren Sie alle Daten von Solution Checker mit [Datenexport nach Excel](../../user/export-data-excel.md), um die Daten aus den folgenden Entitäten zu exportieren:

- Analysekomponente
- Analyseauftrag
- Analyseergebnis
- Analyseergebnisdetail

### PowerApps-Checker löschen

Um die PowerApps Checker-Lösung zu löschen:

1. Öffnen Sie als Systemadministrator oder als Systemadministrator das PowerApps-Portal, indem Sie auf https://web.powerapps.com/environments gehen.
2. Wählen Sie **Lösungen** aus.
3. Wählen Sie **PowerApps Checker** und dann in der Symbolleiste der Lösungen **Löschen**.

### PowerApps Checker hinzufügen

Um PowerApps Checker wieder zu Ihrer CDS for Apps Umgebung hinzuzufügen:

1. Öffnen Sie als Systemadministrator oder als System Customizer Ihr PowerApps-Portal, indem Sie auf https://web.powerapps.com/environments gehen.
2. Wählen Sie **Lösungen** aus.
3. Wählen Sie in der Symbolleiste den **Solution Checker** aus und wählen Sie dann **Install**.

## Läuft bei großen Lösungsausfällen

Solution Checker hat einen 10-minütigen Timeout für den Export einer Lösung aus der Common Data Service (CDS) for Apps Umgebung. Große Lösungen, wie die Standardlösung, können innerhalb dieser Zeit nicht exportiert werden, und die Prüfung wird nicht erfolgreich abgeschlossen. Solution Checker wird es dreimal wiederholen, bevor es den Auftrag nicht bearbeitet, so dass es über 30 Minuten dauern kann, bis Sie eine Fehlermeldung erhalten.

Um dieses Problem zu lösen, überprüfen oder erstellen Sie kleinere Lösungen, die analysiert werden sollen. Um Fehlalarme zu minimieren, stellen Sie sicher, dass Sie abhängige Anpassungen vornehmen. Wenn Sie eine Lösung anlegen und diese Komponenten hinzufügen, fügen Sie Folgendes hinzu:

- Wenn Sie Plugins hinzufügen, fügen Sie die Schritte der SDK-Nachrichtenverarbeitung für das Plug-in hinzu.
- Wenn Sie Entitätsformulare hinzufügen, fügen Sie die JavaScript-Webressourcen hinzu, die an die Formularereignisse angehängt sind.  
- Wenn Sie JavaScript-Webressourcen hinzufügen, schließen Sie alle abhängigen JavaScript-Webressourcen ein.
- Wenn Sie HTML-Webressourcen hinzufügen, schließen Sie alle abhängigen Skripte ein, die in der HTML-Webressource definiert sind.
- Wenn Sie benutzerdefinierte Workflows hinzufügen, fügen Sie die Assembly hinzu, die innerhalb des Workflows verwendet wird.

## Der Solution Checker läuft oder die Ergebnisse des Downloads sind nicht vollständig. 
Kurz nach dem Ausführen des Solution Checker ist der Vorgang nicht abgeschlossen und die folgende Meldung wird angezeigt:<br />
"Wir waren nicht in der Lage, die Überprüfung der *SOLUTIONNAME*-Lösung durchzuführen. Versuchen sie es noch einmal." <br />
![![Wir konnten ](media/solution-checker-werent-able-to-run.png) nicht ausführen](media/solution-checker-werent-able-to-run.png)

Dieses Problem tritt auf, weil sich das Unternehmen im **Administrationsmodus** befindet und der Lösungsprüfer nicht in der Lage ist, die Berechtigungen des Benutzers zur Ausführung der Anforderung zu überprüfen. Um dieses Problem zu beheben, deaktivieren Sie den Administrationsmodus. 

### Deaktivieren des Administrationsmodus für eine Instanz
1. Greifen Sie auf die Instanzpicker von Dynamics 365 for Customer Engagement zu: https://port.crm.dynamics.com/G/Instances/InstancePicker.aspx.
2. Wählen Sie die Instanz aus, bei der Probleme mit dem Solution Checker auftreten.
3. Wählen Sie **ADMIN**.<br />
![![Instance Admin](media/solution-checker-instance-admin.png)](media/solution-checker-instance-admin.png)

4. Löschen **Administrationsmodus aktivieren**. <br />
![![Admin-Modus deaktivieren](media/solution-checker-instance-disable-admin-mode.png)](media/solution-checker-instance-disable-admin-mode.png)

5. Führen Sie den Solution Checker erneut aus.

## Solution Checker verarbeitet keine gepatchten Lösungen.

Wenn eine Lösung mit einem [Patch](https://docs.microsoft.com/powerapps/developer/common-data-service/create-patches-simplify-solution-updates) installiert wurde, kann der Solution Checker die Lösung nicht zur Analyse exportieren. Wenn eine Lösung mit einem Patch versehen wurde, wird die ursprüngliche Lösung gesperrt und kann nicht geändert oder exportiert werden, solange es abhängige Patches in dem Unternehmen gibt, die die Lösung als übergeordnete Lösung identifizieren.

Um dieses Problem zu lösen, klonen Sie die Lösung so, dass alle mit der Lösung verbundenen Patches in die neu erstellte Lösung gerollt werden. Dadurch wird die Lösung entsperrt und die Lösung kann aus dem System exportiert werden. Mehr Informationen: [Klonen einer Lösung](use-segmented-solutions-patches-simplify-updates.md#clone-a-solution)

## Zeilennummernverweise bei Problemen in HTML-Ressourcen mit eingebettetem JavaScript sind nicht korrekt. 

Wenn HTML-Webressourcen innerhalb des Solution Checker verarbeitet werden, wird die HTML-Webressource getrennt von JavaScript innerhalb der HTML-Webressource verarbeitet. Aus diesem Grund ist die Zeilennummer der Verletzung, die unter `<script>` der HTML-Webressource gefunden wurde, nicht korrekt.

## Web-ununterstützte Syntaxprobleme bei Web-Ressourcen

ECMAScript 6 (2015) oder neuere Versionen werden derzeit für Solution Checker nicht unterstützt. Wenn Solution Checker JavaScript mit ECMAScript 6 oder höher analysiert, wird ein webgestütztes Syntaxproblem für die Webressource gemeldet.  

## Siehe auch
[[Best Practices und Leitlinien für den Common Data Service for Apps](../../developer/common-data-service/best-practices/index.md)](../../developer/common-data-service/best-practices/index.md)<br />
[[Best Practices und Anleitungen für modellgetriebene Anwendungen](../../developer/model-driven-apps/best-practices/index.md)](../../developer/model-driven-apps/best-practices/index.md)<br />
