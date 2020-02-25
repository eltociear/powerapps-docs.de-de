---
title: Schneller Einstieg in die Nutzung einer bestehenden Umgebung zur Validierung Ihrer bestehenden Web-Client-Anwendung mit der einheitlichen Benutzeroberfläche | MicrosoftDocs
description: Lernen Sie, wie Sie den Übergang vom alten Web-Client zur einheitlichen Schnittstelle planen und durchführen können
ms.custom: ''
ms.date: 09/11/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: ''
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4c0b7f3e477990accf3b92e9e3964fc2751deb19
ms.sourcegitcommit: 303d5aed44f2bbb406cabeb6b9c8474d738d9114
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "3005169"
---
# <a name="quick-start-for-using-an-existing-environment-to-validate-your-legacy-web-client-app-with-the-unified-interface"></a>Schneller Einstieg in die Nutzung einer bestehenden Umgebung zur Validierung Ihrer bestehenden Web Client App mit der einheitlichen Benutzeroberfläche.
Dieses Schnellstartthema zeigt Ihnen, wie Sie eine bestehende Umgebung verwenden können, um eine Anwendung für die einheitliche Benutzeroberfläche basierend auf Ihrer aktuellen Konfiguration oder Standardlösung zu erstellen. Auf diese Weise können Sie die einheitliche Benutzeroberfläche erkunden und testen, während Sie Ihre bestehenden Legacy-Webclient-Anwendungen parallel ausführen. Ein Benutzer kann dann zwischen den Umgebungen für eine Side-by-Side-Ansicht wechseln. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3JzyI]

Ähnliche Anweisungen, die Ihnen zeigen, wie Sie eine neue Sandbox-Umgebung erstellen, um den Test zu isolieren und nur die Einheitliche Benutzeroberfläche-Erfahrung anzuzeigen, finden Sie unter [Schnellstart für die Umstellung Ihrer älteren Dynamics 365 Web-Client-Anwendung auf die einheitliche Benutzeroberfläche](transition-web-app.md).

> [!IMPORTANT]
>  Für Umgebungen mit Dynamics 365 Field Service oder Dynamics 365 Project Service Automation Apps siehe [Dynamics 365 Apps](transition-web-app.md#dynamics-365-apps).

## <a name="prerequisites"></a>Voraussetzungen 
- Eine bestehende veraltete Web-Client-Anwendung von Dynamics 365 Sales oder Service. 
- Obwohl nicht erforderlich, empfehlen wir Ihnen, Ihre Anwendung in einer Nicht-Produktivumgebung zu testen. Mehr Informationen: [Verwalten Sie Sandbox-Instanzen](/dynamics365/customer-engagement/admin/manage-sandbox-instances). 

## <a name="overview"></a>Übersicht 
Dieses Thema richtet sich an Bestandskunden, die derzeit ältere Web-Client-Anwendungen verwenden, die ihren Übergang zur einheitlichen Benutzeroberfläche planen und durchführen müssen. Um eine parallele Umgebung einzurichten, erstellen Sie eine neue Anwendung auf der Grundlage Ihrer Standardlösung, wie sie derzeit vorliegt. Dies kann in Ihrer aktuellen Entwicklungs-Sandbox-Umgebung erfolgen, ohne Ihre bestehende Arbeit zu beeinträchtigen.

Nach Abschluss der Schritte in diesem Artikel können Benutzer mit der entsprechenden Rolle Ihre neue App in der App-Liste sowohl auf der Dynamics 365 Dropdown-Liste als auch auf der Dynamics 365-Startseite (https://home.dynamics.com) sehen.

![App-Liste](media/app-list.png)

Sobald Sie die in diesem Thema beschriebenen Aufgaben in Ihrer Entwicklungsumgebung mit einer Lösung erledigt haben, können Sie die Lösung in Ihre Testumgebung importieren, was einer breiteren Gruppe von Geschäftsanwendern ermöglicht, die Anwendung in einer vertrauten Umgebung zu testen und zu vergleichen. 

Verfolgen Sie Ihre Application Lifecycle Management (ALM) und Entwicklungsbetriebsprozesse. Wir empfehlen, alle innerhalb eines Lösungskontextes beschriebenen Schritte durchzuführen. Sobald Sie die App in der Entwicklungsumgebung getestet und validiert haben, können Sie die App weiter testen, indem Sie sie als Pilotprogramm für mehr Benutzer, z.B. in einer Produktionsumgebung, starten. Die modellbasierte App und Sitemap innerhalb einer Lösung ermöglicht den Export Ihrer App aus der Umgebung, in der Sie diese neue App erstellt haben, nach Ihren bestehenden Prozessen weiter in Ihrer Umgebungspipeline. 

## <a name="process-for-validating-your-legacy-web-client-app-in-an-existing-environment"></a>Verfahren zur Validierung Ihrer bestehenden Web-Client-Anwendung in einer bestehenden Umgebung
 
Der Prozess zur Validierung Ihrer bestehenden Web Client App in einer bestehenden Umgebung umfasst drei Schritte:  

1.  Erstellen Sie eine neue Lösung, die auf der Standardlösung basiert.
2.  Erstellen einer neuen modellbasierten Anwendung 
3.  App-Eigenschaften konfigurieren  

Wenn Sie kürzlich den Modus **Nur einheitliche Benutzeroberfläche verwenden** auf **Ein** in Ihrer Entwicklungsumgebung umgestellt haben, z.B. durch Befolgen des [Schnellstart für die Umstellung Ihrer Dynamics 365 Legacy Web Client Anwendung auf die einheitliche Benutzeroberfläche](transition-web-app.md) Thema, müssen Sie die Einstellung auf **Aus** zurücksetzen, damit Sie die vorhandenen Legacy Web Client Anwendungen ausführen können.

### <a name="create-a-new-solution-thats-based-on-the-default-solution"></a>Erstellen Sie eine neue Lösung, die auf der Standardlösung basiert.
1. Melden Sie sich beim [Power Apps Herstellerportal](https://make.powerapps.com) an.   
2. Wählen Sie aus der Liste der Umgebungen die gewünschte Umgebung aus.  
3. Wählen Sie im linken Navigationsbereich die Option **Lösungen** aus. 
4. Wählen Sie in der Menüleiste **Neue Lösung**. 
5. Geben Sie im Bereich **Neue Lösung** die folgenden Eigenschaften ein: 
   - **Name** Geben Sie einen Namen für die Lösung ein. Zum Beispiel *App für die einheitliche Benutzeroberfläche*. 
   - **Publisher**. Wählen Sie den Publisher aus, den Ihre Organisation verwendet. Beachten Sie unbedingt Ihre Anpassungsregeln für Ihre bestehenden Anpassungen. Dadurch wird sichergestellt, dass die Schemanamen für die modellbasierte Anwendung und deren Sitemap mit Ihren bestehenden Standards übereinstimmen. 
   - **Version**. Dies sollte in Anlehnung an Ihre bestehenden Standards und die Governance für Lösungen festgelegt werden. 
6. Wählen Sie **Erstellen** aus.  
7. Die neue Lösung wird in der Liste der Lösungen angelegt. Wählen Sie diese Option, um die Lösung zu öffnen und zum nächsten Abschnitt zu gelangen. 

### <a name="create-a-new-model-driven-app-in-the-new-solution"></a>Erstellen einer neuen modellbasierten App in der neuen Lösung
In diesem Schritt erstellen Sie eine neue App, die Ihre bestehenden Anpassungen nutzt, damit Sie sie in der einheitlichen Benutzeroberfläche erleben können. Sie erstellen die App innerhalb des Containers der neuen Lösung, die Sie im vorherigen Abschnitt angelegt haben.  

1. Wählen Sie in der Menüleiste **Neu**, zeigen Sie auf **App**, und wählen Sie dann **Modellbasierte App**.
2. Geben Sie auf der Seite **Eine neue App erstellen** die folgenden Eigenschaften ein: 
   - **Name** Geben Sie einen Namen für die Anwendung ein, wie Sie es für richtig halten. Zum Beispiel *Ihr Anwendungsname* + *Neu* oder *Testen der Einheitlichen Oberfläche*. 
   - **Eindeutiger Name**. Dies beginnt mit Ihrem Lösungspräfix und der vereinfachten Version des von Ihnen angegebenen App-Namens. Sie können Änderungen vornehmen oder es so belassen, wie es erscheint.  
   - **Beschreibung**: Fügen Sie eine Beschreibung für die App hinzu, wie z.B. *Für Testzwecke der einheitlichen Benutzeroberfläche unserer Lösung*.  
3. Wählen Sie **Vorhandene Lösung zur Erstellung der App verwenden** aus und wählen Sie dann **Weiter**. 
4. Wählen Sie in der Liste **Lösung auswählen** **Standardlösung**, in der Liste **Sitemap auswählen** **Sitemap auswählen**, und wählen Sie dann **Beendet**.  

   > [!div class="mx-imgBorder"] 
   > ![Auswählen einer vorhandenen Lösung](media/select-existing-solution.png "Auswählen einer vorhandenen Lösung")

5. Der App Designer wird geöffnet und zeigt alle App-Komponenten an, die in der Standardlösung enthalten waren. Wählen Sie **Veröffentlichen** aus.  
6. Nachdem der Veröffentlichungsprozess abgeschlossen ist, wählen Sie **Abspielen**.  

Im Browser öffnet sich ein neues Fenster mit Ihrer neuen modellgesteuerten Anwendung, die alle Entitäten, Sitemap- und Sitemap-Anpassungen enthält, die in Ihrer Standardanwendung Dynamics 365 enthalten sind.  

> [!div class="mx-imgBorder"] 
> ![Neue Einheitliche Oberfläche-App](media/new-unified-interface-app.png "Neue Einheitliche Oberfläche-App")

Beachten Sie, dass, wenn Sie mit dem Bereich Power Apps des Herstellerportals **Lösungen** auf die Registerkarte Browser zurückkehren, Ihre neue modellgetriebene Anwendung und eine ähnlich benannte Sitemap-Client-Erweiterung Teil der von Ihnen erstellten Lösung sind.  

> [!div class="mx-imgBorder"] 
> ![Lösungskomponenten](media/solution-assets.png "Lösungskomponenten")

In diesem Schritt haben Sie eine neue modellbasierte App innerhalb einer Lösung erstellt, die Sie in Ihre Test- oder Evaluierungsumgebungen importieren können. Sie könnten jetzt damit beginnen, die neue App zu erproben, aber vorher werden Sie im nächsten Schritt ein paar Einstellungen für die neue App vornehmen. Auf diese Weise ist es möglich, mit anderen Benutzern zu teilen.

### <a name="configure-app-properties"></a>App-Eigenschaften konfigurieren
Zu den Aufgaben, die zur Konfiguration der modellbasierten App-Eigenschaften erforderlich sind, gehören: 

- Zuweisung von Benutzerrollen an die neue App, um Nichtadministratoren den Zugriff auf die App zu ermöglichen.  
- Anpassen einer benutzerfreundlichen URL, so dass eine Verknüpfung zur neuen App einfach freigegeben, mit einem Lesezeichen versehen oder von Benutzern gespeichert werden kann. 


1. Navigieren Sie zu *UmgebungsURL*/**Apps**. Die URL wird ähnlich wie diese aussehen: https://*Ihre Umgebung*.crm.dynamics.com/apps. Dadurch wird eine Liste aller Apps in Ihrer Umgebung geöffnet. 
2. Suchen Sie die neue modellbasierte App, die Sie erstellt haben.  
3. Wählen Sie auf der App-Kachel die Auslassungspunkte aus und wählen Sie dann **Rollen verwalten**.   

   > [!div class="mx-imgBorder"] 
   > ![Rollen verwalten](media/select-app-ellipsis.png "Rollen verwalten")

4. Der verfügbare Rollenbereich wird im rechten Bereich aufgelistet. Wählen Sie die Rollen nach Bedarf aus, um nicht-administrativen Benutzern Zugriff auf die App zu gewähren. 

    > [!IMPORTANT]
    > Stellen Sie sicher, dass allen Benutzern mindestens eine Sicherheitsrolle zugewiesen wird, die **Lesen**-Zugriff auf das Recht **Modellbasierte App** enthält. Diese Berechtigung finden Sie auf der Registerkarte Anpassung in der Sicherheitsrolle. Benutzer ohne diese Berechtigung erhalten beim Öffnen einer modellbasierten App einen Fehler.  Beachten Sie, dass die Sicherheitsrollen Systemadministrator und Systemanpasser dieses Recht bereits aktiviert haben. 
 
   > [!div class="mx-imgBorder"] 
   > ![Recht „Modellgesteuerte App“](media/model-driven-app-privilege.png "Recht „Modellgesteuerte App“")

5. Optional können Sie im Bereich **Rollen verwalten** das **App URL-Suffix** erweitern, um die benutzerfreundliche URL für die Modell-basierte App anzupassen. Beachten Sie, dass Sie fast alles angeben können. Geben Sie beispielsweise *neu* ein, damit die Vorschau die URL *https://YourEnvironment.crm.dynamics.com/apps/new* anzeigt.   

   > [!div class="mx-imgBorder"] 
   > ![Suffix der App-URL](media/app-url-suffix.png "Suffix der App-URL")

   Dies wird zur freundlichen URL, die verwendet und weitergegeben werden kann, so dass Benutzer direkt in die einheitliche Benutzeroberfläche einsteigen können. Benutzer können diesen Link zu ihrer Bequemlichkeit mit einem Lesezeichen versehen. 

6. Wählen Sie **Speichern** aus. 

Nun können Benutzer mit der entsprechenden Rolle Ihre neue App in der App-Liste sowohl in der Dropdown-Liste der Dynamics 365-App als auch auf der Dynamics 365-Startseite (https://home.dynamics.com) sehen. 
  
   ![App-Liste](media/app-list.png "App-Liste")

Da der Modus **Nur Einheitliche Benutzeroberfläche verwenden** auf **Aus** eingestellt ist, werden Benutzer, die zur Root-URL Ihrer Umgebung navigieren, weiterhin auf der Standardanwendung **Dynamics 365 - Custom** landen. Dies wird erwartet, wenn Sie Ihre bestehenden Legacy-Webclient-Anwendungen beim Testen und Arbeiten an den Anwendungen der einheitlichen Benutzeroberfläche weiterhin unterstützen möchten.  

## <a name="compare-your-new-app-to-the-default-dynamics-365-app"></a>Vergleichen Sie Ihre neue App mit der Standard-App von Dynamics 365.  
Jetzt sind Sie bereit, die App zu starten. Sie können die neue App für die einheitliche Benutzeroberfläche mit der Dynamics 365 - Custom App vergleichen, indem Sie die gleichen Daten, Benutzerrollen, Geschäftsregeln, Workflows, Plugins usw. verwenden, da sie sich in der gleichen Umgebung befinden. Auf diese Weise können Sie Ihrem Unternehmen vermitteln, dass alle wichtigen Grundlagen noch vorhanden sind, und gleichzeitig mit der Erforschung der neuen Erweiterungen der einheitlichen Benutzeroberfläche beginnen.  

> [!TIP]
> Wenn Sie die Apps nebeneinander auf einem Monitor anzeigen möchten, können Sie die Pfeiltasten von Windows und links (oder die Pfeiltaste rechts) zusammen drücken, um Ihre Browserfenster auf dem gleichen Monitor aufzuteilen. 

> [!NOTE]
> Wenn Sie weiterhin Anpassungen in Ihrer Standard-Site-Map vornehmen, wie beispielsweise Änderungen in der Navigation oder tiefere Menüband-Anpassungen für Schaltflächen und Aktionen, müssen Sie den Vorgang wiederholen, indem Sie eine weitere modellbasierte Anwendung erstellen oder die gleichen Anpassungen in der neuen Site-Map für Ihre modellbasierte Anwendung vornehmen.  

## <a name="validate-your-new-app"></a>Validieren Sie Ihre neue App  
Wenn Ihre Anwendung die einheitliche Benutzeroberfläche präsentiert, können Sie mit der Validierung Ihrer Anwendung, Prozesse und Anpassungen beginnen, um festzustellen, wie der Übergang aussehen wird. Wir empfehlen Ihnen, alle Anwendungsfälle zu testen, aber Sie können mit den kritischsten beginnen oder in logische Entwurfsmuster gruppieren. Da die einheitliche Benutzeroberfläche auf einem responsiven Design basiert, empfehlen wir Ihnen, Tests immer mit verschiedenen Geräten mit unterschiedlichen Bildschirmauflösungen durchzuführen. Während Sie die Anwendung testen, können Sie überprüfen, ob Ihre Anpassungen mit der einheitlichen Benutzeroberfläche kompatibel sind und ob es Funktionen gibt, die ein Redesign erfordern oder fehlende Funktionen aufweisen.  

> [!IMPORTANT]
> Die aktuelle Version von Common Data Service und modellgetriebenen Apps in Dynamics 365 enthält noch einige veraltete Funktionen. Sie sollten Ihre Anwendung auf veraltete Funktionen überprüfen und bei Bedarf durch neue Funktionen ersetzen. Mehr Informationen: [Wichtige Änderungen (veraltet) kommen ](/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming)

> [!TIP]
> Das Power Apps Checker-Tool unterstützt Sie bei der Qualitätsprüfung der Komponenten Ihrer Lösung.  Mehr Informationen: [Verwenden Sie den Solution Checker, um Ihre modellgetriebenen Anwendungen in Power Apps](../common-data-service/use-powerapps-checker.md) zu validieren.

## <a name="next-steps"></a>Nächste Schritte
Basierend auf Ihren Erkenntnissen kann Ihr Implementierungsteam oder Ihr Partner den Aufwand für die Umstellung Ihrer Anwendung auf die einheitliche Benutzeroberfläche abschätzen und mögliche Verbesserungen der Benutzerfreundlichkeit identifizieren. Mit einer Vielzahl neuer Funktionen und Fähigkeiten, die in der einheitlichen Benutzeroberfläche verfügbar sind, besteht die Möglichkeit, den Wert für Ihre Anwendungsbenutzer zu erhöhen. 

Der Übergang zur einheitlichen Benutzeroberfläche ist eine großartige Gelegenheit für Sie, eine moderne Benutzeroberfläche zu erstellen und Ihre bestehenden Prozesse zu überprüfen, um sicherzustellen, dass sie noch gültig sind oder verbessert werden müssen. Dies ist auch ein guter Zeitpunkt, um zu prüfen, ob Ihre Anwendung Ihren Geschäftsanforderungen entspricht und ob die bestehende Anwendung auf mehrere Anwendungen für verschiedene Teams und Rollen verteilt werden kann.
Mehr Informationen: [Entwerfen Sie modellbasierte Anwendungen mit dem App Designer](design-custom-business-apps-using-app-designer.md). 

### <a name="see-also"></a>Siehe auch
<!-- Unified Interface transition community (link tbd) <br />  -->
[Einheitliche Benutzeroberfläche - Playbook](unified-interface-playbook.md) <br />
[Annäherung an eine Benutzererfahrung und Übergang zur einheitlichen Benutzeroberfläche](approaching-unified-interface.md) <br />
[Über „Einheitliche Oberfläche”](/dynamics365/customer-engagement/admin/about-unified-interface) <br />
[Was sind modellgetriebene Apps in Power Apps?](model-driven-app-overview.md) <br />
[Aktualisieren Ihrer Apps auf die einheitliche Oberfläche](/dynamics365/customer-engagement/admin/update-apps-to-unified-interface) <br />
[Informationen zum Konfigurieren von Dashboards für interaktive Funktionen](configure-interactive-experience-dashboards.md) <br />
[Verwenden Sie benutzerdefinierte Steuerelemente für modellgesteuerte App-Datenvisualisierungen](use-custom-controls-data-visualizations.md) <br />
[Power Apps component framework Übersicht](/powerapps/developer/component-framework/overview) <br />
[Einheitliche Benutzeroberfläche für alle](/power-platform-release-plan/2019wave2/microsoft-powerapps/unified-interface-app-everybody)
