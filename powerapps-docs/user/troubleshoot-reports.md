---
title: Problembehandlung bei Daten, die nicht in einem Bericht angezeigt werden | Microsoft-Dokumentation
description: Problembehandlung bei Daten, die nicht in einem Bericht angezeigt werden
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
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2019
ms.locfileid: "67420764"
---
# <a name="troubleshoot-problems-with-data-not-displaying-in-a-report"></a>Problembehandlung bei Daten, die nicht in einem Bericht angezeigt werden

Es gibt mehrere mögliche Gründe, warum Daten, die Sie in einem Bericht erwarten, nicht angezeigt werden:  
  
- **Unzureichende Sicherheits Berechtigungen**. Wenn Sie nicht über die Berechtigung verfügen, Common Data Service einen Datensatz anzuzeigen, wird er nicht im Bericht angezeigt.  
  
- **Es werden keine Daten eingegeben.** Die Person, die Daten eingibt, darf Felder leer lassen.  
  
- **Die Daten stimmen nicht mit den Kriterien für den Bericht überein.** Viele Berichte enthalten einen Standardfilter, in dem nur aktive Datensätze angezeigt werden, oder Sie haben möglicherweise Kriterien ausgewählt, die über keinen übereinstimmenden Datensatz verfügen. Versuchen Sie, den Berichts Filter zu ändern. Weitere Informationen finden Sie unter [Edit the default Filter of a Report](edit-report-filter.md) .  
  
- **Möglicherweise wird eine zwischengespeicherte Kopie des Berichts angezeigt.** Standardmäßig werden Daten in Common Data Service Berichten jedes Mal aus der Datenbank abgerufen, wenn Sie einen Bericht ausführen. Der Systemadministrator hat jedoch möglicherweise einen Bericht so geändert, dass er aus dem Cache ausgeführt wird. Wenn die von Ihnen kürzlich eingegebenen Daten nicht im Bericht enthalten sind, ist möglicherweise eine ältere Version des Berichts aus dem Cache vorhanden. Um den Bericht zu aktualisieren, klicken Sie auf der Berichts Symbolleiste auf die Schaltfläche **Aktualisieren** .  
  
- **Sie verfügen möglicherweise nicht über die Berechtigung zum Lesen von Datensätzen in einem unter Bericht.** Wenn Sie nicht über die Berechtigung zum Lesen von Daten Satz Typen verfügen, die in einem unter Bericht enthalten sind, wird eine Fehlermeldung angezeigt, die besagt, dass der unter Bericht nicht angezeigt werden konnte.  
  
- **Die Microsoft Internet Explorer-Datenschutzeinstellungen können erforderliche Cookies blockieren.** Wenn für Diagramm Berichte anstelle des Diagramms der rote Buchstabe X angezeigt wird, können die Datenschutzeinstellungen ein Cookie blockieren, das für das Diagramm Steuerelement erforderlich ist. Um dieses Problem zu beheben, aktivieren Sie in Ihrem Browser Cookies für den Server, auf dem Reporting Services ausgeführt wird.  
  

### <a name="see-also"></a>Siehe auch
[Arbeiten mit Berichten](work-with-reports.md) 

[Erstellen eines Berichts mithilfe des Berichts-Assistenten](create-report-with-wizard.md)

[Vorhandenen Bericht hinzufügen](add-existing-report.md)

[Berichts Filter bearbeiten](edit-report-filter.md)

