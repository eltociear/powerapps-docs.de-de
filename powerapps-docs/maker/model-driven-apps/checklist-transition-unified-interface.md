---
title: 'Prüfliste: Schnittstellenübergang Einheitliche Startseite | Microsoft-Dokumentation'
description: Prüfliste, um sicherzustellen, dass Sie für einen Übergang zur Einheitlichen Oberfläche vorbereitet sind.
ms.custom: ''
ms.date: 11/04/2019
ms.reviewer: kvivek
ms.service: powerapps
ms.topic: article
author: Mattp123
ms.author: haybass
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 03b3db348ff88b7fd2c5e89e2b94a7d16a1fee17
ms.sourcegitcommit: bcaffcb3135251ea3c2e828f8b59926d19520bec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2761814"
---
# <a name="checklist-unified-interface-transition"></a>Prüfliste: Übergang Einheitliche Oberfläche

Folgen Sie den Schritten in diesem Artikel, um sicherzustellen, dass Sie für einen Übergang zur Einheitlichen Oberfläche vorbereitet sind. Die Bereitschaft zum Übergang zur Einheitlichen Oberfläche ist davon abhängig, ob Sie grundlegende Kompatibilität anstreben oder neu entwerfen, um in größtmöglichem Umfang neuen Funktionen abzurufen. Weitere ausführliche Informationen finden Sie unter [Einheitliches Schnittstellentextbuch](https://docs.microsoft.com/powerapps/maker/model-driven-apps/unified-interface-playbook) und [Benutzererfahrung-Whitepaper](https://docs.microsoft.com/powerapps/maker/model-driven-apps/approaching-unified-interface).

Die Anweisungen gelten für die folgenden modellgesteuerten Apps in Dynamics 365:

- Dynamics 365 Sales

- Dynamics 365 Customer Service

- Dynamics 365 Field Service

- Dynamics 365 Project Service Automation

## <a name="run-the-powerapps-solution-checker-on-your-solutions"></a>Führen Sie die PowerApps Lösungsprüfung für Ihre Lösungen aus.

Mit der [PowerApps Lösungsprüfung](https://docs.microsoft.com/powerapps/maker/common-data-service/use-powerapps-checker) können Sie eine umfangreiche Prüfung der statischen Analyse auf Ihren Lösungen für einen Satz von Regeln der bewährten Methode ausführen, um problematische Muster schnell zu ermitteln. Nach der Überprüfung erhalten Sie einen Bericht, der Probleme aufzeigt, die bestimmt werden, welche Komponenten und Code betroffen sind und die Dokumentation verknüpft, die beschreibt, wie ein Problem zu beheben ist.

Der Lösungsprüfer analysiert die Lösungskomponente:

-   Common Data Service-Plug-Ins

-   Common Data Service benutzerdefinierte Workflowaktivitäten

-   Common Data Service-Webressourcen (HTML) und JavaScript

-   Common Data Service-Konfigurationen, wie SDK-Nachrichtenschritte

**Zu berücksichtigende Punkte** 

-   Die möglichen Probleme, die von der Lösungsprüfung erkannt werden, gelten unter Umständen nicht ausschließlich für die Einheitliche Oberfläche. Bedenken Sie, was sich auf den Übergang auswirkt, wenn Sie die Ergebnisse überprüfen.

-   Wie in den automatisierten Codeüberprüfung können einige Probleme Fehlalarme sein und bedeuten nicht, dass Ihre Anwendung nicht auf der Einheitlichen Oberfläche ausgeführt wird.

-   Logik, die serverseitig ausgeführt wird, zum Beispiel Plug-Ins, benutzerdefinierte Workflowaktivitäten und die Konfiguration von SDK-Nachrichtenschritten, sollten die Benutzeroberfläche, und damit den Übergang zur Einheitlichen Oberfläche, nicht beeinflussen.

-   Selbst wenn alle Probleme nicht direkt mit der Einheitlichen Oberfläche verbunden sind, empfehlen wir jedoch, ausreichend Zeit für die Überprüfung aufzuwenden, um die Gesamtintegrität Ihrer Anwendung zu verbessern.

## <a name="check-third-party-solutions-compatibility-with-unified-interface"></a>Überprüfen Sie die Kompatibilität mit der Einheitlichen Oberfläche von Lösungen von Drittanbietern


Vor dem Übergang zur Einheitlichen Oberfläche ist es wichtig sicherzustellen, dass jede entsprechende Lösung von Drittanbietern, die Sie in der Anwendung verwenden, in der Einheitlichen Oberfläche funktioniert.

-   Wenn Sie Add-Ins unabhängiger Softwareanbieter (ISV) durch [AppSource](https://appsource.microsoft.com)installiert haben, überprüfen Sie, ob Upgrades im [Power Platform Admin Center](https://admin.powerplatform.microsoft.com) verfügbar sind, indem Sie **Umgebungen** > [Name der Umgebung] > **Lösungen verwalten** auswählen.

-   Wenn Sie Lösungen von Drittanbietern verwenden, die außerhalb von AppSource bereitgestellt wurden, setzen Sie sich mit dem Anbieter (Partner oder ISV) in Verbindung, um eine neue Version zu erhalten, die die Apps auf die Einheitliche Oberfläche aktualisiert.

> [!NOTE]
> Wenn keine Pläne für Ihre Lösungen von Drittanbietern zur Aktualisierung einer Version existieren, die mit der Einheitlichen Oberfläche kompatibel ist, ist es wichtig, einen Pfad zu bestimmen, entweder diese Funktionen durch systemeigene Plattformfunktionen oder Ausweichlösungen zu ersetzen, die kompatibel sind.

## <a name="identify-replacements-for-deprecated-client-api-code-and-features"></a>Identifizieren Sie Ersetzungen für veraltete Client-API-Codes und Funktionen

Aufgrund der Ergebnisse der **PowerApps Lösungsprüfung** und der Informationen, die in [Wichtige kommende Änderungen (Veralterungen)](https://docs.microsoft.com/power-platform/important-changes-coming) über veraltete Client-APIs und -Funktionen enthalten sein, sollten Sie ein gutes Verständnis der Anpassungen und Funktionen haben, die entweder in Ihrem Projekt Einheitliche Oberfläche behoben oder ersetzt werden müssen.

Im Folgenden finden Sie einige der häufigsten Bereiche, die Aufmerksamkeit erfordern:

-   **Client API**: Empfohlene Ersetzungsmethoden sind [hier](https://docs.microsoft.com/power-platform/important-changes-coming#some-client-apis-are-deprecated) dokumentiert.

-   **Prozessdialoge**: Empfohlene Ersetzungen für Dialoge sind [hier](https://docs.microsoft.com/flow/replace-dialogs) dokumentiert.

-   **Aufgabenflüsse**: Erwägen Sie, [Geschäftsprozessflüsse](https://docs.microsoft.com/power-platform-release-plan/2019wave2/microsoft-flow/business-process-immersive-experiences) anstelle von Aufgabenflüsse zu verwenden.

-   **Serviceplanung**: Erwägen Sie, [Universal Resource Scheduling](https://docs.microsoft.com/dynamics365/common-scheduler/schedule-anything-with-universal-resource-scheduling) zum Ersetzen von Vorgängerserviceplanung zu verwenden.

> [!NOTE]
> Erwägen Sie ebenso das Ersetzen von Dynamics 365 for Outlook (COM-Add-In) mit der Leichtgewichtler [Dynamics 365 App for Outlook](https://docs.microsoft.com/dynamics365/outlook-app/overview).

## <a name="test-your-application-in-unified-interface"></a>Testen Sie Ihre Anwendung in der Einheitlichen Oberfläche

Eine der einfachsten Möglichkeiten, Ihre Anwendung in der Einheitlichen Oberfläche zu testen, ist die Option [**Nur Einheitliche Oberfläche aktivieren**](https://docs.microsoft.com/power-platform/admin/enable-unified-interface-only) auf einer Kopie Ihrer Produktionsumgebung zu aktivieren. Nachdem die Einheitliche Oberfläche aktiviert ist, sollte es möglich sein, auf Ihre Anwendung mithilfe der App **Dynamics 365 – Benutzerdefiniert** zuzugreifen und die Anwendungsfälle zu testen, die für Ihren Kontext relevant sind.

### <a name="test-your-business-and-technical-scenarios"></a>Testen Sie Ihre Geschäfts- und technischen Szenarien

Konzentrieren Sie sich auf das, was möglicherweise betroffen sein kann:

-   **Geschäftsprozesse** wie Geschäftsprozessflüsse, Geschäftsregeln

-   **Anpassungen** wie Formulare, Ansichten, Befehlsleistenschaltflächen, Webressourcen und Diagramme

> [!TIP]
> Fordern Sie die Benutzererfahrung gleichzeitig mit der Durchführung dieser frühen Tests heraus: leuchtet alles ein und erhöht es den Wert? Was sollte entfernt, verbessert, hinzugefügt werden? Sind beispielsweise die aktuellen Listen der Ansichten relevant? Oder werden meine Benutzer gezwungen, ihre eigenen Ansichten zu erstellen?

### <a name="identify-gaps"></a>Ermitteln Sie Lücken

-   Potentielle Regressionen, die noch nicht durch die Lösungsprüfung und Lösungen durch Drittanbieter-Updates entdeckt wurden.

-   Benutzerproblemfälle, die zu Optimierungen (z. B. neues Formularrendering durch die Reorganisierung von Abschnitten und Registerkarten ) oder bestimmte Schulung führen könnten.

-   Alle sonstigen Abhängigkeiten vom Vorgängerwebclienten, wie der Verwendung des veralteten Outlook COM-Add-Ins anstelle des Leichtgewichtlers Dynamics 365 App for Outlook.

## <a name="define-your-app-strategy-and-settings"></a>Definieren Sie Ihre App-Strategie und -Einstellungen

Statt die **Dynamics 365 – Benutzerdefiniert**-App zu verwenden, die nicht für die Einheitliche Oberfläche optimiert ist, sondern im Kompatibilitätsmodus ausgeführt werden, empfehlen wir, dass Sie von Erstanbieter-Apps profitieren, die von Microsoft hergestellt werden oder Ihre eigenen Apps erstellen.

Die Dynamics 365 Apps von Erstanbietern, die bereits für Einheitliche Oberfläche optimiert wurden, sind die folgenden:

-   Dynamics 365-Vertriebshub

-   Dynamics 365-Kundenservicehub

-   Dynamics 365 Marketing

-   Dynamics 365 Field Service (Version 8.x und höher)

-   Dynamics 365 Project Service Automation (Version 3.x und höher)

### <a name="what-are-model-driven-apps"></a>Was sind modellgesteuerte Apps?

**Modellgesteuerte Apps** stellen eine Art von App dar, die Sie mithilfe von PowerApps erstellen. Das hilft Ihnen, Ihren Benutzern individuelle Erfahrungen je nach deren Rolle in der Organisation zur Verfügung stellen. Beispielsweise kann ein Vertriebsmitarbeiter eine völlig andere Erfahrung als ein Kundenservicemitarbeiter durch verschiedene modellgesteuerte Apps haben, obwohl sie Daten aus der gleichen Umgebung verwenden. Mehrere modellgesteuerte Apps können in einer Common Data Service-Umgebung erstellt werden. Weitere Informationen: [Was sind modellgesteuerte Apps?](https://docs.microsoft.com/powerapps/maker/model-driven-apps/model-driven-app-overview)

Die Dynamics 365 Apps von Erstanbietern, die zuvor aufgeführt wurden, sind Beispiele für modellgesteuerte Apps.

### <a name="how-to-define-your-app-strategy"></a>So definieren Sie Ihre App-Strategie

Stellen Sie sich folgende Fragen:

1.  Können Sie Ihre Benutzer in mehrere Gruppen mit spezifischen Geschäftsprozessen aufteilen?

2.  Haben diese Gruppen unterschiedliche Anforderungen bezüglich was sie sehen und tun sollen?

3.  Ist es schwierig für Sie, verschiedene Benutzererfahrungen zu haben ohne Apps verwenden?

Wenn Sie mit "Ja" auf diese Fragen geantwortet haben, erwägen Sie die Verwendung mehrerer Apps.

Das ist die Gelegenheit, die Erfahrung im Kontext der Geschäftsprozesse für jede Gruppe oder Rolle zu überdenken.

### <a name="out-of-the-box-apps-for-example-sales-hub-or-customized-apps"></a>Standard-Apps (beispielsweise Vertriebshub) oder benutzerdefinierte Apps?

-   Das hängt davon ab, wie individuell die Erfahrung Ihrer Meinung nach sein sollte.

-   Wenn Sie nur wenige Anpassungen haben oder von Apps-Updates von Erstanbietern profitieren möchten, sollten Sie systemeigenen Apps in Erwägung ziehen.

-   Wenn Sie eine größere Kontrolle über Erfahrungen sowie Updates von Standard-Apps und Anpassungen haben möchten, erstellen Sie Ihre eigene App.

### <a name="once-you-have-defined-your-app-strategy-what-should-be-the-next-steps"></a>Nachdem Sie Ihre App-Strategie definiert haben, was sollten dann die nächsten Schritte sein?

1.  Passen Sie Ihre Ziel-Apps an und integrieren Sie nur, was Benutzer benötigen. Weniger ist mehr. Reduzieren Sie die Überfrachtung, um Benutzern effizienteres Arbeiten zu ermöglichen.

2.  Trennen Sie Sicherheitsrollen von nicht verwendeten Apps.

## <a name="review-your-apps-settings-and-user-experience-fundamentals"></a>Überprüfen Sie Ihre App-Einstellungen und Grundlagen der Benutzererfahrung

### <a name="app-settings"></a>App-Einstellungen

-   Schließen Sie alle erforderlichen Entitäten in Ihrer App ein, selbst wenn sie nicht in der Siteübersicht enthalten sind.  
    
-   Verleihen Sie das Recht zum **Lesen** für **modellgesteuerte App** auf der Registerkarte **Anpassung** im Dialogfeld **Sicherheitsrolle**.

-   Aktivieren Sie den Modus **Nur Einheitliche Oberfläche**, wenn Ihre Benutzer den Vorgängerwebclienten nicht verwenden müssen. Sie können trotzdem auf Verwaltungsfunktionen zugreifen, indem Sie **Einstellungen** > **Erweiterte Einstellungen** auswählen.

-   Erstellen Sie eine einfachere App-URL. Zum Beispiel: https://\*.crm.dynamics.com/apps/MyApp*

-   Versuchen Sie, die Anzahl von Apps auf die ein Benutzer zugreifen kann, zu begrenzen.  
    
    > [!TIP]
    > Wenn **Nur Einheitliche Oberfläche verwenden** auf **Ja** festgelegt ist und wenn Benutzer nur Zugriff auf eine App haben, werden sie automatisch zu der App geleitet, wenn sie auf die Stamm-URL (https://\*.crm.dynamics.com) zugreifen*

### <a name="optimize-navigation-sitemap"></a>Optimieren Sie die Navigation (Siteübersicht)

-   Definieren Sie einen Haupt-**Bereich** mit den am meisten verwendeten **Unterbereichen** (Dashboard, Entitäten, usw.) in **Gruppen** organisiert

-   Erstellen Sie einen oder mehrere zusätzliche Bereiche für weniger verwendeten Funktionen (Konfiguration, Einstellungen, usw.). Es geht darum, Ihren Benutzern zu helfen, sich nur auf das zu konzentrieren, was wichtig zur Ausführung ihrer Arbeit ist.

### <a name="update-icons"></a>Symbole aktualisieren

-   Der Übergang zur Einheitlichen Oberfläche ist eine gute Gelegenheit, Symbole zu aktualisieren.

-   Wir empfehlen das **SVG**-Format, da es gut rendert unabhängig von der Bildschirmauflösung.

    > [!TIP]
    > Beispiel eines SVG-Symbolformats:  
    > Breite und Höhe: 16px; Abstand: 0px; Hintergrund: transparent; Symbolfarbe: \#FF000000  
    Um Probleme beim rendern zu vermeiden, öffnen Sie die SVG-Datei mit einem Editor (beispielsweise Notepad) und entfernen Sie Füllung= "\#000000"

## <a name="enrich-your-app-with-unified-interface-exclusive-features"></a>Reichern Sie Ihre App mit exklusiven Funktionen der Einheitlichen Oberfläche an

-   Erstellen Sie eine **Willkommensseite**, die Benutzer beim Zugreifen auf alle Ihre Apps sehen. Dies ist eine gute Gelegenheit, Benutzer bei Ihren ersten Schritte anzuleiten.

-   Verwenden Sie vorhandene **Benutzerdefinierte Steuerelemente**, um die Benutzerfreundlichkeit der meisten Feldtypen, insbesondere bei Mobil, zu verbessern. Ersetzen Sie beispielsweise eine Feldbewertung von 0 bis 5 durch Sterne, ersetzen Sie eine Ansicht von Terminen durch eine Kalenderansicht, ersetzen Sie eine Unterrasteransicht durch Kartenformulare.

-   Nutzen Sie **Bereich-Verweise** auf Formularen, um mehrere Ansichten, Schnellansichten, und Suchfunktionen von Wissensdatenbanken an einem einzigen Ort zu bündeln.

-   Nutzen Sie das [PowerApps Component Framework](https://docs.microsoft.com/powerapps/developer/component-framework/overview), um noch mehr benutzerdefinierte Steuerelemente hinzuzufügen. Sie können einige von der Community oder von Partnern und ISV beziehen.

-   Betten Sie [Canvas-Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/getting-started) in Ihre Formulare ein, um die Anwendung einfach zu erweitern. No-Code- oder Low-Code-Erweiterung Ihrer App ohne die Notwendigkeit, benutzerdefinierte HTML-/JS-Webressourcen zu entwickeln.

-   Betten Sie **Power BI** Berichte und Kacheln in Formulare ein: konsolidieren Sie Daten für mehrere Systeme in einer einzelnen Ansicht.

-   Erwägen Sie die Nutzung von **Interaktive Dashboards**, um einen One-Stop-Arbeitsbereich zu konfigurieren, der globales Filtern über Dashboardkomponenten hinweg ermöglicht.

-   Konfigurieren Sie **Benutzerdefinierte Hilfebereiche und Aufgabenhilfen**, damit Benutzer schnell Hilfe und Unterstützung erhalten.

## <a name="conduct-user-acceptance-testing"></a>Führen Sie eine Prüfung der Benutzerakzeptanz durch

Es ist sehr wichtig, dass Ihre Anwendungen, Geschäftsszenarien und technischen Szenarien von den geschäftlichen Benutzern in der Einheitlichen Oberfläche unter Bedingungen, die Ihrer Produktionsumgebung ähneln, getestet werden. Diese Benutzer können als Geschäftsmeister auftreten, um die Skalierung von Wissen über das Unternehmen hinweg zu unterstützen.

Tests können helfen, die übrigen zu adressierenden Elemente zu identifizieren, bevor alle Ihre Benutzer den Übergang zur Einheitlichen Oberfläche unternehmen.

## <a name="update-user-training-materials"></a>Benutzertrainingsmaterial aktualisieren

Überprüfen Sie Ihre vorhandenen und geplanten Schulungsmaterialien, um zu gewährleisten, dass sie die neuesten Screenshots enthalten und alle Änderungen wiedergeben, die Sie am Benutzerfluss vorgenommen haben.

## <a name="check-your-transition-date"></a>Überprüfen Sie Ihr Übergangsdatum.

Am 1. Oktober 2020 [ist der Vorgängerwebclient nicht mehr verfügbar](https://docs.microsoft.com/power-platform/important-changes-coming#legacy-web-client-is-deprecated).
Stellen Sie sicher, dass Sie mit reichlich Vorlaufzeit migrieren, um sicherzustellen, dass ausreichend Zeit zur Behandlung aller Probleme zur Verfügung steht.
