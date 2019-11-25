---
title: Schnellstart für die Umstellung Ihrer bestehenden Web-Client-Anwendung auf die einheitliche Oberfläche | MicrosoftDocs
description: Hier erfahren Sie mehr zum Übergang der Vorgänger-Webclient-Anwendung zur einheitlichen Oberfläche
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
ms.assetid: 14c4c18c-927c-4ea2-ba66-0531285a99a7
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: eed1efac81b882d076e0e809c93ddec63f6a75f7
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2759730"
---
# <a name="quick-start-for-transitioning-your-legacy-web-client-application-to-unified-interface"></a>Schnellstart für die Umstellung Ihrer bestehenden Web-Client-Anwendung auf die einheitliche Oberfläche

Die einheitliche Oberfläche verwendet auch dynamische Webdesignprinzipien, um bei jeder Bildschirmgröße oder -ausrichtung sowie auf jedem Gerät die bestmögliche Ansicht und Interaktion zu bieten. In diesem Schnellstartthema wird erklärt, wie Sie Ihre alte Webclient-Anwendung auf die einheitliche Oberfläche umstellen können, indem Sie eine neue Nicht-Produktionsumgebung verwenden. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3JwWU]

Um eine bestehende produktionsfreie Umgebung für die Umstellung Ihrer Web Client-Anwendung zu verwenden, siehe [Schneller Start für die Verwendung einer bestehenden Umgebung zur Validierung Ihrer bestehenden Web Client-Anwendung mit der einheitlicheb Oberfläche](transition-web-app-existing.md). 
## <a name="prerequisites"></a>Voraussetzungen
- Eine alte Web-Client-Anwendung. 
- Obwohl nicht erforderlich, wird empfohlen, eine Nicht-Produktionsumgebung zu verwenden, um die Anwendung zu testen und sicherzustellen, dass die aktuellen Bereitstellungs- oder Entwicklungszyklen nicht beeinflusst werden. Mehr Informationen: [Verwalten Sie Sandbox-Instanzen](/dynamics365/admin/manage-sandbox-instances).

## <a name="prepare-the-environment"></a>Vorbereiten der Umgebung
Wählen Sie zuerst eine Nicht-Produktionsumgebung aus und aktivieren Sie den Modus **Nur Einheitliche Oberfläche verwenden**, sodass die einheitliche Oberfläche für alle modellgesteuerten Apps in der Umgebung verwendet wird. Dazu gehören auch alle Dynamics 365-Anwendungsmodule, die ursprünglich für den Legacy-Webclient konfiguriert wurden.

1. Melden Sie sich bei [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an, wählen Sie **Umgebung**, und wählen Sie dann eine Sandbox-Umgebung aus. 

2. Wählen Sie **Einstellungen** > **Verhalten** aus, und aktivieren Sie dann **Nur Einheitliche Oberfläche verwenden**.

   > [!div class="mx-imgBorder"] 
   > ![Einstellung für „Nur Einheitliche Oberfläche verwenden“](media/use-unified-interface-only-pac.png)

Sie können dies auch im Einstellungsbereich einstellen. Gehen Sie zu **Einstellungen** > **Verwaltung** > **Systemeinstellungen** und dann auf die Registerkarte **Allgemein**, und legen Sie **Nur die Einheitliche Oberfläche aktivieren** auf **Ja** fest.

> [!div class="mx-imgBorder"] 
> ![Nur die neue Einheitliche Oberfläche verwenden](media/use-unified-interface-only.png "Nur die neue Einheitliche Oberfläche verwenden")


> [!NOTE]
> Wenn Sie die Umgebung wieder in den vorherigen Status setzen möchten, können Sie die Einstellung für die einheitliche Oberfläche umschalten, um zur ursprünglichen Oberfläche zurückzukehren. Weitere Informationen: [Nur Einheitliche Oberfläche aktivieren](/dynamics365/customer-engagement/admin/enable-unified-interface-only).

## <a name="run-and-validate-your-application-in-the-unified-interface"></a>Ausführen und Überprüfen der Anwendung in der einheitlichen Oberfläche
Führen Sie Anwendungen aus, die ursprünglich Webclient-Anwendungen waren. Beachten Sie, dass, nachdem Sie die Option **Nur Einheitliche Oberfläche verwenden** aktiviert haben, alle verfügbaren Apps in der Umgebung die einheitliche Oberfläche verwenden, auch wenn die Anwendung ursprünglich für den Webclient konfiguriert wurde.

Um Ihre Anwendung auszuführen, melden Sie sich bei [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an, wählen Sie **Apps**, und wählen Sie dann die Anwendung aus, die Sie ausführen möchten. Alternativ können Sie auch direkt zur Seite **Meine Apps** gehen, z.B. *https://contoso.crm.dynamics.com/apps/*.

### <a name="validate-your-app-processes-and-customizations"></a>Überprüfen der App, Prozesse und Anpassungen 
Es ist empfehlenswert, alle Anwendungsfälle zu testen. Sie können mit den wichtigsten Anwendungsfällen starten oder sie in logische Entwurfsmuster gruppieren. Da die einheitliche Oberfläche auf einem reagierenden Entwurf basiert, wird empfohlen, Tests mit unterschiedlichen Geräten auszuführen, die verschiedene Bildschirmauflösungen haben. Während Sie die Anwendung testen, können Sie überprüfen, ob Ihre Anpassungen mit der einheitlichen Benutzeroberfläche kompatibel sind und ob es Funktionen gibt, die ein Redesign erfordern oder fehlende Funktionen aufweisen. Erstellen Sie einen Plan für die Überprüfung dieser Elemente und veröffentlichen Sie Ihre Fragen und Ihr Feedback in unserem Community-Forum. 

> [!IMPORTANT]
> Die aktuelle Version von Common Data Service und modellgetriebenen Apps in Dynamics 365 enthält noch einige veraltete Funktionen. Sie sollten Ihre Anwendung auf veraltete Funktionen überprüfen und bei Bedarf durch neue Funktionen ersetzen. Mehr Informationen: [Wichtige Änderungen (veraltet) kommen ](/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming)

### <a name="dynamics-365-apps"></a>Dynamics 365 Anwendungen
Wenn Sie die Apps Dynamics 365 Field Service oder Dynamics 365 Project Service Automation verwenden und die einheitliche Benutzeroberfläche testen möchten, müssen Sie eine neue Sandbox-Umgebung einrichten und eine Kopie Ihrer Produktionsumgebung erstellen, um auf die neueste Field Service Version und Project Service Automation Version zu aktualisieren, bevor Sie diese Anwendungen in der einheitlichen Benutzeroberfläche überprüfen können. Gehen Sie dazu wie folgt vor:

1. Erstellen Sie eine neue Sandboxumgebung im [Power Platform Admin Center](https://admin.powerplatform.microsoft.com/environments) oder [Dynamics 365-Administrationscenter](https://port.crm.dynamics.com/). Siehe [Hinzufügen einer Instanz zum Abonnement](/dynamics365/customer-engagement/admin/add-instance-subscription)

2. Kopieren Sie Ihre Produktionsumgebung mit Dynamics 365 Field Service- oder Dynamics 365 Project Service Automation-Apps in die neue Sandboxumgebung. Öffnen Sie hierzu im Power Platform Admin Center die Produktionsumgebung, und wählen Sie dann **Kopieren** aus.

    > [!div class="mx-imgBorder"] 
    > ![Umgebung kopieren](media/ppac-copy-environment.png "Umgebung kopieren")

3. Wählen Sie auf der Seite **Umgebung kopieren** zunächst die Option **Alles**, dann die neue Sandboxumgebung in der Liste **Zu überschreibende Umgebung auswählen**, und dann **Kopieren** aus. 

    > [!div class="mx-imgBorder"] 
    > ![Umgebung überschreiben](media/ppac-copy-overwrite.png "Umgebung überschreiben")

4. Das Dialogfeld **Umgebung überschreiben** wird angezeigt. Stellen Sie sicher, dass Sie die richtige Umgebung und die richtigen Optionen ausgewählt haben, und wählen Sie dann **Bestätigen** aus. 

5. Wenn die Kopie erfolgreich ist, wird eine Bestätigungsmitteilung angezeigt. 

6. Auf der Menüleiste wählen Sie **Lösungen verwalten** aus, um den Bereich **Lösungen** zu öffnen. 

    > [!div class="mx-imgBorder"] 
    > ![Lösungen verwalten](media/ppac-manage-solutions.png "Lösungen verwalten")

    > [!IMPORTANT]
    > Wenn **Verwaltungsmodus** aktiviert ist, müssen Sie diesen deaktivieren, damit der Bereich **Lösungen** angezeigt wird. Mehr Informationen: [Verwaltungsmodus](/power-platform/admin/sandbox-environments#administration-mode)

7. Suchen Sie die Lösung Field Service oder Project Service Automation und wählen Sie sie aus. Die Option zum **Upgrade** sollte verfügbar sein. Wählen Sie diese aus, um die Lösung zu aktualisieren. 

    > [!div class="mx-imgBorder"] 
    > ![Lösung aktualisieren](media/ppac-upgrade-solution.png "Lösung aktualisieren")
    
> [!NOTE]
> Die neuesten Versionen von Field Service und Project Service Automation für die einheitliche Oberfläche sind standardmäßig für neu erstellte Instanzen verfügbar. Wenn Sie eine vorhandene Umgebung mit früheren installierten Versionen aktualisieren möchten, müssen Sie die Aktualisierung anfordern, indem Sie den [Microsoft-Kundensupport](https://go.microsoft.com/fwlink/?LinkId=853505) kontaktieren. 

Weitere Informationen: [Dynamics 365 for Field Service – neueste Versionen](/dynamics365/customer-engagement/field-service/version-history#latest-versions) und [Dynamics 365 for Project Service Automation Upgrade-Homepage](/dynamics365/customer-engagement/project-service/upgrade-psa-home-page)

## <a name="next-steps"></a>Nächste Schritte
Basierend auf Ihren Erkenntnissen kann Ihr Implementierungsteam oder Ihr Partner den Aufwand für die Umstellung Ihrer Anwendung auf die einheitliche Benutzeroberfläche abschätzen und mögliche Verbesserungen der Benutzerfreundlichkeit identifizieren. Mit mehreren neuen Features und Funktionen, die in der einheitlichen Oberfläche zur Verfügung stehen, kann der Wert für die Anwendungsbenutzer erhöht werden. 

Der Übergang zur einheitlichen Benutzeroberfläche ist eine großartige Gelegenheit für Sie, eine moderne Benutzeroberfläche zu erstellen und Ihre bestehenden Prozesse zu überprüfen, um sicherzustellen, dass sie noch gültig sind oder verbessert werden müssen. Dies ist auch ein guter Zeitpunkt, um zu prüfen, ob Ihre Anwendung Ihren Geschäftsanforderungen entspricht und ob die bestehende Anwendung auf mehrere Anwendungen für verschiedene Teams und Rollen verteilt werden kann.
Mehr Informationen: [Entwerfen Sie modellbasierte Anwendungen mit dem App Designer](design-custom-business-apps-using-app-designer.md).  

### <a name="see-also"></a>Siehe auch
<!-- Unified Interface transition community (link tbd) <br />  -->
[Einheitliche Benutzeroberfläche - Playbook](unified-interface-playbook.md) <br />
[Annäherung an eine Benutzererfahrung und Übergang zur einheitlichen Benutzeroberfläche](approaching-unified-interface.md) <br />
[Über „Einheitliche Oberfläche”](/dynamics365/customer-engagement/admin/about-unified-interface) <br />
[Was sind modellgetriebene Apps in PowerApps?](model-driven-app-overview.md) <br />
[Aktualisieren Ihrer Apps auf die einheitliche Oberfläche](/dynamics365/customer-engagement/admin/update-apps-to-unified-interface) <br />
[Informationen zum Konfigurieren von Dashboards für interaktive Funktionen](configure-interactive-experience-dashboards.md) <br />
[Verwenden Sie benutzerdefinierte Steuerelemente für modellgesteuerte App-Datenvisualisierungen](use-custom-controls-data-visualizations.md) <br />
[PowerApps component framework Übersicht](/powerapps/developer/component-framework/overview) <br />
[Einheitliche Benutzeroberfläche für alle](/power-platform-release-plan/2019wave2/microsoft-powerapps/unified-interface-app-everybody)

