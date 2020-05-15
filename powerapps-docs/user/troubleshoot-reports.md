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
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "3302401"
---
# <a name="troubleshoot-problems-with-data-not-displaying-in-a-report"></a>Behandeln von Problemen im Zusammenhang mit nicht angezeigten Berichtsdaten

Es gibt verschiedene Gründe, warum Daten möglicherweise nicht wie erwartet in einem Bericht angezeigt werden:  
  
- **Unzureichende Sicherheitsberechtigungen**. Wenn Sie in Common Data Service nicht die Berechtigung zum Anzeigen eines Datensatzes besitzen, ist er nicht im Bericht enthalten.  
  
- **Daten wurden nicht engegeben.** Der Benutzer, der die Daten eingegeben hat, hat möglicherweise nicht alle Felder ausgefüllt.  
  
- **Die Daten entsprechen nicht den Kriterien des Berichts** Viele Berichte enthalten einen Standardfilter, der dafür sorgt, dass nur aktive Datensätze angezeigt werden. Möglicherweise haben Sie aber auch Kriterien ausgewählt, für die keine passenden Datensätze vorhanden sind. Ändern Sie den Berichtsfilter. Weitere Informationen finden Sie unter [Bearbeiten des Standardfilters eines Berichts](edit-report-filter.md).  
  
- **Möglicherweise zeigen Sie eine Kopie des Berichts aus dem Cache an.** Die Daten in Common Data Service-Berichten werden standardmäßig bei jedem Ausführen des Berichts aus der Datenbank abgerufen. Möglicherweise hat jedoch der Systemadministrator festgelegt, dass ein Bericht aus dem Cache ausgeführt wird. Wenn kürzlich eingegebene Daten nicht im Bericht eingeschlossen sind, wird möglicherweise eine ältere Version des Berichts aus dem Cache angezeigt. Wählen Sie zum Aktualisieren des Berichts auf der Berichtssymbolleiste die Schaltfläche **Aktualisieren** aus.  
  
- **Sie besitzen möglicherweise nicht die Berechtigung zum Lesen von Datensätzen in einem Unterbericht.** Wenn Sie nicht zum Lesen der Datensatztypen in einem Unterbericht berechtigt sind, wird eine Fehlermeldung angezeigt, dass der Unterbericht nicht angezeigt werden konnte.  
  
- **Ihre Microsoft Internet Explorer Datenschutzeinstellungen können erforderliche Cookies blockieren.** Wenn anstelle eines Diagrammberichts ein rotes X angezeigt wird, blockieren Ihre Datenschutzeinstellungen möglicherweise ein Cookie, das für die Steuerung des Diagramms benötigt wird. Zum Beheben dieses Problems müssen Sie in Ihrem Browser für den Server, auf dem Reporting Services ausgeführt wird, Cookies aktivieren.  
  

### <a name="see-also"></a>Siehe auch
[Arbeiten mit Berichten](work-with-reports.md) 

[Erstellen eines Berichts mithilfe des Berichts-Assistenten](create-report-with-wizard.md)

[Hinzufügen eines vorhandenen Berichts](add-existing-report.md)

[Bearbeiten des Standardfilters eines Berichts](edit-report-filter.md)

