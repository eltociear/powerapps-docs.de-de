---
title: Bekannte Probleme in PowerApps-Portalen | Microsoft-Dokumentation
description: Erfahren Sie mehr über die bekannten Probleme in PowerApps-Portalen
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 743db54c0f26323be841dd177c993fb30b310d5f
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2757354"
---
# <a name="known-issues"></a>Bekannte Probleme


## <a name="general-issues"></a>Allgemeine Fragen

- Das **Änderungsdatum** für die App könnte falsch sein, da es sich um vorab bereitgestellte Apps handelt und früher hätte bereitgestellt werden können.

- Wenn Sie eine Umgebung zusammen mit dem Starterportal erstellen, wird der Besitzer des Portals nicht richtig angezeigt. Es wird als System angezeigt.

- Wenn Sie die URL eines kürzlich gelöschten Portale wiederverwenden, um ein neues Portal zu erstellen, hat dies eine gewisse Verzögerung bei der Einrichtung der Laufzeit. Dies liegt daran, dass die Bereinigung früherer Ressourcen noch im Gange wäre und zwischen 30 Minuten und 1 Stunde dauern kann, bis das neue Portal auf Azure eingerichtet ist. Dieses Portal ist während dieser Zeit auch nicht verfügbar zum Bearbeiten und zeigt möglicherweise Fehler an, wenn es im Studio für die Bearbeitung gestartet wird.

- Wenn Sie eine Umgebung in PowerApps wechseln, werden die Portale innerhalb einer Umgebung möglicherweise nicht sofort in der Liste **Apps** oder **Letzte Apps** angezeigt. Dies geschieht insbesondere in Umgebungen, die in einer anderen Region als ihr Mandantentstehen. Der Workaround besteht darin, die Browseraktualisierung zu verwenden oder einige Zeit zu warten, bis das Portal in der App-Liste erscheint.

- Wenn Sie den Portaleinstellungsbereich auf der PowerApps-Homepage geöffnet lassen, während Sie das Portal vom PowerApps-Portaladministratorcenter zurücksetzen, wird Benutzern die Fehlermeldung „Leider ist ein Fehler aufgetreten“ im Portaleinstellungsbereich angezeigt, da das Portal nicht verfügbar ist.

- In bestimmten Fällen, wenn Sie ein Portal erstellen, werden die Stile nicht ordnungsgemäß auf das Portal angewendet, und die Website wird beim Öffnen über **Website durchsuchen** ohne die Stile angezeigt. Dies passiert selten und Stile können wiederhergestellt werden, indem das Portal über das PowerApps-Portaladministratorcenter neu gestartet wird.

## <a name="powerapps-portals-studio-issues"></a>Probleme mit PowerApps-Portalstudio

- Wenn ein Portal über eine Seitenhierarchie mit über drei Ebenen verfügt, werden die Seiten ab der vierten Ebene nicht im PowerApps-Portalstudio angezeigt.

- Der ausgewählte Textschriftgrad wird nur angezeigt, wenn speziell für diesen Text ein Schriftgrad definiert wurde. Wenn er Teil der Standard-HTML-Tags wie H1, H2, H3 usw. ist, zeigt PowerApps-Portalstudio den Schriftgrad nicht an.

- Die Webseite mit der Vorlage **Seite mit Seitennavigation** zeigt nur den Link der Seiten an, die bei der Erstellung der Webseite vorhanden waren. Sie können die Links auf der linken Seite der Seite aktualisieren, indem Sie die Seitenvorlage in eine andere Vorlage ändern und dann zurück zu **Seite mit Seitennavigation**.

- Wenn Sie eine Webseite löschen, spiegelt das Canvas bis zur nächsten Aktualisierung des Canvas nicht das aktualisierte Menü wider.

- Die Farbauswahl und die dazugehörigen Zeichenketten werden nur auf Englisch unterstützt.

- Einige Template-Seiten auf dem Self-Service-Portal sind nicht in der Lage, das richtige Breadcrumb darzustellen.

- Einige PowerApps-Portalvorlagen, besonders an modellgesteuerte Apps in Dynamics 365 gebundene, haben keine Standardmenüelemente gemäß ihrer Seitenhierarchie. Der Grund ist, dass in allen oder einigen Webseiten keine Seitenreihenfolge verfügbar ist. Alle Portale ohne die Anzeigereihenfolge von Webseiten haben dieses Problem.

- Eine Fehlermeldung wird angezeigt, wenn der Seiteninhalt (Seitenkopie) das Limit von 65536 Zeichen und die Seitenübersicht das Standardlimit von 2000 Zeichen überschreitet.

- Das Navigationsmenü wird nur auf dem Canvas mit einer Auflösung der Mindestbreite von 1600px angezeigt.

- Ein Bild, das auf einer Seite hochgeladen wird, wird das untergeordnete Element der Seite. Wenn Sie die Seite löschen und das Bild auf einer anderen Seite verwenden, wird das Bild nicht im PowerApps-Portalstudio und auf der Website gerendert.

- Das Formularrendering wird im PowerApps-Portalstudio derzeit nicht unterstützt. Wenn Sie ein Formular hinzufügen, müssen Sie **Website durchsuchen** auswählen, um die Website zu öffnen und das Formular zu überprüfen.

- In einem Text oder Abschnitthintergrund, wenn Sie die Farbe in **Keine Farbe** ändern, entfernt PowerApps-Portalstudio nicht die zugehörigen Attribute wie Hintergrundfarbe oder Schriftfarbe, stattdessen werden die Werte auf Null gesetzt.

- Im folgenden Szenarien stoppt PowerApps-Portalstudio das Laden und zeigt den Fehler „Fehler bei der Verbindung“ an:
    - Wenn die Homepage für ein Portal gelöscht oder deaktiviert wird.
    - Wenn eine Seitenvorlage, die mit der Homepage oder einer beliebigen Seite verknüpft ist, deaktiviert oder gelöscht wird.

- PowerApps-Portalstudio kann Quellcode dieser Inhaltsausschnitte, denen keine Sprache in Common Data Service zugewiesen wurde, nicht laden.

- In einigen Fällen werden die Änderungen für Kopf- und Fußzeile, entweder in der WYSIWYG-Umgebung von PowerApps-Portalstudio oder über den Code-Editor, nicht sofort angezeigt.

- Wenn eine Webseite der Suchvorlage in PowerApps-Portalstudio zugewiesen wurde, zeigt sie eine einfache Seite mit Ladeprogramm an. Damit dies für Sie funktioniert, müssen Sie eine entsprechende Websitemarkierung für diese Seite erstellen.

- Die Standardstudiovorlage wird beim Erstellen einer neuen Seite auch als Option in der Seitenvorlage angezeigt, wenn sie in PowerApps-Portalstudio verwendet wird. Diese Vorlage wird außerdem nur in englischer Sprache eingefügt und dies unterstützt nicht die Lokalisierung anhand der Common Data Service-Standard- oder Portalsprache.

- Eine Liste, die als Kalendersteuerelement oder Übersicht gerendert wird, kann nicht über PowerApps-Portalstudio konfiguriert werden.

- Das Feld der Teil-URL in den Seiteneigenschaften akzeptiert keine Sonderzeichen und unterbricht das Rendering in der Canvas für einige Zeit. 

- Das Hochladen von CSS kann in Szenarien, in denen der CSS-Dateiname Sonderzeichen oder Leerzeichen im Dateinamen enthält, fehlschlagen.

- Unveröffentlichte Webseiten werden in den Canvas von PowerApps-Portalstudio nicht gerendert.

- Bei der Verwendung von PowerApps-Portalstudio, wenn die Portalausgangssprache anders ist als die Sprache des Browsers, werden in die neuen Webseiten, die mit Hilfe der Standardstudiovorlage erstellt wurden, Dummy-Inhalte in der Sprache des Browsers anstelle der Portalsprache eingefügt.

- Nur CSS, das auf der Stammseite übernommen wird, wird im **Design**-Bereich angezeigt. Wenn Sie jedoch versuchen, eine CSS-Datei mit dem gleichen Namen wie eine andere CSS-Datei, die im Portal verfügbar ist, hochzuladen, werden Sie von PowerApps-Portalstudio aufgefordert, diese Datei zu ersetzen.

- PowerApps-Portalstudio wird derzeit nicht für Safari im Mac-Betriebssystem unterstützt und hat die folgenden Probleme:
    - Die Auswahl der Komponente ist nicht korrekt und das Zeigen auf eine Komponente gibt eine falsche Zielangabe wieder.
    - Zwei oder drei Spaltenabschnitte rendern nicht ordnungsgemäß in PowerApps-Portalstudio, funktionieren jedoch einwandfrei auf der Website.

