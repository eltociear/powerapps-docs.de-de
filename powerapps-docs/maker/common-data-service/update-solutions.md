---
title: Aktualisieren einer Lösung | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine Lösung in Power Apps aktualisieren oder upgraden können
ms.custom: ''
ms.date: 03/18/2020
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
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0bebbc9eeead8fb4f02c4bf958c33b79c0d9cc1c
ms.sourcegitcommit: 48414442a10210d49911c3eda8b49f68db85f684
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2020
ms.locfileid: "3151172"
---
# <a name="upgrade-or-update-a-solution"></a>Upgraden oder Aktualisieren einer Lösung  
Es gibt Zeiten, in denen Sie eine vorhandene verwaltete Lösung aktualisieren müssen. Führen Sie die folgenden Schritte aus, um die Lösung zu aktualisieren: 

1.  Öffnen Sie die nicht verwaltete Lösung in Ihrer Entwicklungsumgebung, erstellen Sie neue Komponenten oder fügen Sie Komponenten hinzu und entfernen Sie bestehende Komponenten. 
2.  Erhöhen Sie die Versionsnummer, wenn Sie die Lösung als verwaltete Lösung exportieren. Weitere Informationen: [Verstehen der Versionsnummern für Updates](#understanding-version-numbers-for-updates) 

    > [!div class="mx-imgBorder"] 
    > ![Aktualisieren der Lösungsversion](media/update-solution-version.png)
3. [Übernehmen des Upgrades oder Updates in der Zielumgebung](#apply-the-upgrade-or-update-in-the-target-environment)

## <a name="apply-the-upgrade-or-update-in-the-target-environment"></a>Übernehmen des Upgrades oder Updates in der Zielumgebung
Das Verfahren zum Importieren der aktualisierten Lösung ähnelt dem Installieren einer neuen verwalteten Lösung, außer dass Sie verschiedene Optionen erhalten. Wenn Sie eine Lösung aktualisieren, die Sie von jemand anderem erhalten haben, sollten Sie den Lösungsherausgeber danach fragen, welche Optionen Sie auswählen sollten.  

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an, wählen Sie die gewünschte Zielumgebung und dann **Lösungen** in der linken Navigation aus.  

2. Wählen Sie in der Befehlsleiste **Importieren**.  

3. Wählen Sie auf der Seite **Lösungspaket auswählen** die Option **Durchsuchen** aus, um die komprimierte Datei (.zip oder .cab) zu finden, die die zu aktualisierende Lösung enthält.  

4. Wählen Sie **Weiter**.  

5. Sie können Informationen zur Lösung anzeigen, bevor Sie **Weiter** wählen. Auf dieser Seite wird ein gelber Balken angezeigt, der **Dieses Lösungspaket enthält ein Update für eine bereits installierte Lösung** anzeigt.  

6. Wählen Sie aus den folgenden Optionen für Lösungsaktionen aus:  
   - **Upgrade (empfohlen)** Diese Option wird die Lösung in die neuste Version und Rollup für alle vorherigen Patches in einem Schritt aktualisieren.  Alle Komponenten, die der vorherigen Lösungsversion zugeordnet sind, die nicht in der neueren Lösungsversion sind, werden nicht gelöscht. Dies ist die empfohlene Option, da sie sicherstellt, dass Ihr resultierender Konfigurationszustand mit der importierenden Lösung konsistent ist, einschließlich der Entfernung von Komponenten, die nicht mehr Teil der Lösung sind.
        
   - **Für Upgrade planen** Diese Option aktualisiert Ihre Lösung auf die höhere Version, verschiebt jedoch die Löschung der vorherigen Version und aller damit verbundenen Patches, bis Sie später ein Lösungs-Upgrade durchführen.  Diese Option sollte nur gewählt werden, wenn Sie sowohl die alte als auch die neue Lösung gleichzeitig im System installiert haben möchten, damit Sie vor dem Abschluss des Lösungs-Upgrades eine Datenmigration durchführen können. Dadurch werden die alte Lösung und alle Komponenten, die nicht in der neuen Lösung enthalten sind, gelöscht.
        
   - **Update (nicht empfohlen)** Diese Option ersetzt die Lösung von dieser Version.  Komponenten, die nicht in der neueren Lösung enthalten sind, werden nicht gelöscht und verbleiben im System.  Diese Option wird nicht empfohlen, da die Zielumgebung in der Konfiguration der Quellumgebung weicht und Probleme auftreten können, die schwierig sind hervorzurufen und zu diagnostizieren.
        
7. Wählen Sie aus den folgenden Anpassungsoptionen:

   - **Anpassungen warten (empfohlen)**  

        Mit der Auswahl dieser Option werden alle unverwalteten Anpassungen gewartet, die auf Komponenten ausgeführt wurden. Allerdings werden nicht alle Updates in dieser Lösung angewendet.  

   - **Anpassungen überschreiben (nicht empfehlenswert)**  

        Diese Option überschreibt oder entfernt nicht verwaltete Anpassungen, die zuvor für Komponenten in dieser Lösung vorgenommen wurden. Diese Option hat keine Komponenten, die das Zusammenführungsverhalten unterstützen (Formulare,Siteübersicht, Menüband, App-Module).  Komponenten, die andere verwaltete Lösungen auf der vorhandenen Lösung haben, die Sie ersetzen, bleiben auch weiterhin im Vordergrund und sind von dieser Option nicht betroffen.  

8. Entscheiden Sie, ob Sie die folgende Option für Aktionen nach dem Import aktivieren möchten:
   - **Sämtliche in der Lösung enthaltene Verarbeitungsschritte für SDK-Mitteilungen aktivieren**  
        Durch Auswahl dieser Option werden Plug-Ins und Workflows aktiviert, die in der Lösung enthalten sind.
        
9. Wählen Sie **Weiter**.  

10. Möglicherweise müssen Sie einige Momente beim Lösungsimport warten. Wenn dies erfolgreich ist, können Sie die Ergebnisse anzeigen und **Schließen** wählen.  

   Wenn Sie Änderungen importiert haben, die veröffentlicht werden müssen, müssen Sie die Anpassungen veröffentlichen, bevor sie verfügbar sind. 

**Abschließen von Lösungs-Upgrades** Wenn Sie die ausgewählte Phase für Upgrades wählen oder das System ein Problem hat, das Upgrade zu beenden, sehen Sie, dass die erste Lösung immer noch in Ihrem System installiert ist, zusammen mit einer neuen Lösung, die den gleichen Namen hat wie die Lösung, der Sie das \_Upgrade hinzugefügt haben.  Um das Upgrade abzuschließen, wählen Sie die Basislösung in der Lösungsliste aus und wählen Sie **Lösungs-Upgrade anwenden**.  Dadurch werden alle vorherigen Patches deinstalliert und die ursprüngliche Lösung erhält die \_Upgrade-Lösung, die dann den gleichen Namen hat wie die vorherige Lösung.  Alle Komponenten, die in der ursprünglichen Lösung und Lösungspatches enthalten waren und in der \_Upgrade-Lösung nicht vorhanden sind, werden als Teil des Prozesses gelöscht.

## <a name="understanding-version-numbers-for-updates"></a>Verstehen der Versionsnummern für Updates
Eine Lösungsversion hat das folgende Format: major.minor.build.revision. Ein Update muss eine höhere Haupt-, Neben-, Build- oder Revisionsnummer als die übergeordnete Lösung haben. Beispielsweise könnte für eine Basislösungsversion 3.1.5.7 ein kleines Update eine Version 3.1.5.8 oder ein etwas bedeutenderes Update die Version 3.1.7.0 sein. Ein wesentlich bedeutenderes Update könnte die Version 3.2.0.0 sein.


### <a name="see-also"></a>Siehe auch
[Hinzufügen von Lösungskomponenten](create-solution.md#add-solution-components) <br />
[Exportieren von Lösungen](export-solutions.md) <br />
[Lösung importieren](import-update-export-solutions.md)