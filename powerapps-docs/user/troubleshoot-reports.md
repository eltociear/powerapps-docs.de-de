---
title: Behandeln von Problemen im Zusammenhang mit nicht angezeigten Berichtsdaten | Microsoft-Dokumentation
description: Behandeln von Problemen im Zusammenhang mit nicht angezeigten Berichtsdaten
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 06/27/2019
ms.author: mkaur
ms.custom: ''
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1156aa8fb5fbc3ae51c21b8aa41606df6dbc2e86
ms.sourcegitcommit: e9671e018c1ee4b640528915350a367758991b6a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2019
ms.locfileid: "67420764"
---
# <a name="troubleshoot-problems-with-data-not-displaying-in-a-report"></a>Behandeln von Problemen im Zusammenhang mit nicht angezeigten Berichtsdaten

Das Problem, dass erwartete Daten in einem Bericht nicht angezeigt werden, kann verschiedene Ursachen haben:  
  
- **Unzureichende Sicherheitsberechtigungen:** Wenn Sie in Common Data Service nicht zum Anzeigen eines Datensatzes berechtigt sind, wird er im Bericht nicht angezeigt.  
  
- **Daten nicht eingegeben:** Die Person, die die Daten eingegeben hat, hat möglicherweise nicht alle Felder ausgefüllt.  
  
- **Daten entsprechen nicht den Kriterien für den Bericht:** Viele Berichte enthalten einen Standardfilter, der dafür sorgt, dass nur aktive Datensätze angezeigt werden. Möglicherweise haben Sie aber auch Kriterien ausgewählt, für die keine passenden Datensätze vorhanden sind. Ändern Sie den Berichtsfilter. Weitere Informationen finden Sie unter [Bearbeiten des Standardfilters eines Berichts](edit-report-filter.md).  
  
- **Betrachtung einer zwischengespeicherten Kopie des Berichts:** Standardmäßig werden Daten in Common Data Service-Berichten bei jeder Berichtsausführung aus der Datenbank gepullt. Es kann jedoch sein, dass Ihr Systemadministrator einen Bericht so geändert hat, dass er aus dem Cache ausgeführt wird. Sollten kürzlich eingegebene Daten nicht in dem Bericht enthalten sein, wird unter Umständen eine ältere Berichtsversion aus dem Cache verwendet. Wählen Sie zum Aktualisieren des Berichts auf der Berichtssymbolleiste die Schaltfläche **Aktualisieren** aus.  
  
- **Keine Berechtigung zum Lesen von Datensätzen in einem Unterbericht:** Wenn Sie nicht zum Lesen von Datensatztypen aus einem Unterbericht berechtigt sind, erhalten Sie eine Fehlermeldung mit dem Hinweis, dass der Unterbericht nicht angezeigt werden konnte.  
  
- **Blockierung erforderlicher Cookies durch die Datenschutzeinstellungen von Microsoft Internet Explorer:** Falls bei Diagrammberichten anstelle des Diagramms ein rotes X angezeigt wird, wird durch Ihre Datenschutzeinstellungen möglicherweise ein für das Diagrammsteuerelement erforderliches Cookie blockiert. Aktivieren Sie zur Behebung dieses Problems in Ihrem Browser Cookies für den Server, auf dem Reporting Services ausgeführt wird.  
  

### <a name="see-also"></a>Siehe auch
[Arbeiten mit Berichten](work-with-reports.md) 

[Erstellen eines Berichts mithilfe des Berichts-Assistenten](create-report-with-wizard.md)

[Hinzufügen eines vorhandenen Berichts](add-existing-report.md)

[Bearbeiten des Standardfilters eines Berichts](edit-report-filter.md)

