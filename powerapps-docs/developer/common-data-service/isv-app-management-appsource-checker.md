---
title: Einführung in den AppSource-Checker | Microsoft Docs
description: Lernen Sie, wie man AppSource Checker verwendet
services: ''
suite: powerapps
documentationcenter: na
author: nkrb
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.reviewer: pehecke
ms.workload: na
ms.date: 04/07/2020
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5a0cd90c78b0654ded91d13761b228f4a6f4ba34
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "3275770"
---
# <a name="appsource-checker"></a>AppSource Checker

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Sie können den AppSource Checker verwenden, um zu überprüfen, ob Ihre App die Zertifizierungskriterien erfüllt, bevor Sie sie an [AppSource](https://appsource.microsoft.com/) senden. Der Checker lässt Sie wissen, ob Ihre Lösungsdatei Fehler enthält, die korrigiert werden müssen, und überprüft, ob die Zertifizierungskriterien für AppSource erfüllt sind. 

In ISV Studio können Sie entweder ein vollständiges [Paket](/powerapps/developer/common-data-service/package-deployer/create-packages-package-deployer) oder die Lösung(en) hochladen. Sie werden benachrichtigt, ob irgendwelche Probleme behoben werden müssen.

**Zur Ausführung von AppSource Checker**

1. Wählen Sie in ISV Studio im linken Bereich **AppSource Checker** und wählen Sie dann **Anwendung validieren**.

    > [!div class="mx-imgBorder"]
    > ![AppSource Checker](media/appsource-checker.png "AppSource Checker")

2. Wählen Sie **Suchen**, um eine Lösungsdatei von Ihrem lokalen Rechner hochzuladen, und wählen Sie dann **Prüfung ausführen**.
   
   > [!div class="mx-imgBorder"]
   > ![Prüfbefehl ausführen](media/appsource-browse-solution-files.png "Befehl Scheck ausführen")
 
   > [!NOTE]
   > Wenn Sie zuvor eine Lösung zur Validierung hochgeladen haben, sehen Sie anstelle des obigen Screenshots eine Historie der Einreichungen.

3. Nachdem die Validierungsprüfung abgeschlossen ist, wird eine Zusammenfassung der Ergebnisse mit der Anzahl der gefundenen Probleme (falls vorhanden) angezeigt. Doppelklicken Sie auf die Lösungsdatei, um die Probleme im Detail zu sehen.

   > [!div class="mx-imgBorder"]
   > ![Zusammenfassung der Ergebnisse von AppSource Checker](media/appsource-results-page.png "Zusammenfassung der Ergebnisse von AppSource Checker")

4. Wenn die Einreichung keine Fehler aufweist, sehen Sie die folgende Meldung:
 
   > [!div class="mx-imgBorder"]
   > ![AppSource Checker-Erfolgsmeldung](media/appsource-no-error-page.png "AppSource Checker Erfolgsmeldung")
   
Jetzt können Sie den Validierungsbericht für Ihre Apps herunterladen und ihn Ihrer AppSource-Einreichung beifügen. 

### <a name="see-also"></a>Siehe auch

[Homepage](isv-app-management-homepage.md)<br/>
[App-Seite](isv-app-management-apppage.md)<br/>
[Mandantenseite](isv-app-management-tenantpage.md)<br/>
[Zertifizierung von Konnektoren](isv-app-management-certification.md)

