---
title: Bekannte Probleme in powerapps-Portalen | Microsoft-Dokumentation
description: Weitere Informationen zu bekannten Problemen in den powerapps-Portalen
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
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542505"
---
# <a name="known-issues"></a>Bekannte Probleme


## <a name="general-issues"></a>Allgemeine Probleme

- Das **geänderte Datum** für die APP ist möglicherweise falsch, da es sich um vorab bereitgestellte apps handelt, die zuvor bereitgestellt werden können.

- Wenn Sie eine Umgebung zusammen mit dem Starter Portal erstellen, wird der Besitzer des Portals nicht ordnungsgemäß angezeigt. Es wird als System angezeigt.

- Wenn Sie die URL eines kürzlich gelöschten Portals wieder verwenden, um ein neues Portal zu erstellen, tritt für die Laufzeit eine gewisse Verzögerung auf. Dies liegt daran, dass das Löschen vorheriger Ressourcen noch in Bearbeitung ist und zwischen 30 Minuten und einer Stunde dauern kann, bis das neue Portal in Azure eingerichtet wird. Das Portal steht während dieser Zeit auch nicht zur Bearbeitung zur Verfügung und zeigt möglicherweise Fehler an, wenn Sie in Studio zum Bearbeiten gestartet werden.

- Wenn Sie eine Umgebung in powerapps wechseln, werden die Portale in einer Umgebung möglicherweise nicht sofort in **apps** oder in der Liste der **zuletzt geöffneten apps** angezeigt. Dies geschieht insbesondere in Umgebungen, die in einer anderen Region als Ihrem Mandanten erstellt werden. Die Problem Umgehung besteht darin, die Browser Aktualisierung zu verwenden oder einige Zeit zu warten, bis das Portal in der Liste der apps angezeigt wird.

- Wenn Sie den Bereich "Portal Einstellungen" auf der powerapps-Startseite beim Zurücksetzen des Portals über das powerapps-Portal Admin Center geöffnet lassen, wird dem Benutzer im Bereich "Portal Einstellungen" die Fehlermeldung "ein Fehler ist aufgetreten" angezeigt, da das Portal nicht verfügbar ist.

- In bestimmten Fällen werden die Stile beim Erstellen eines Portals nicht ordnungsgemäß auf das Portal angewendet, und die Website wird ohne die Stile angezeigt, wenn Sie über die **Website zum Durchsuchen**geöffnet wird. Dies geschieht nur selten, und Stile können wieder hergestellt werden, indem Sie das Portal über das powerapps-Portal Admin Center neu starten.

## <a name="powerapps-portals-studio-issues"></a>Powerapps-Portale Studio-Probleme

- Wenn ein Portal über eine Seiten Hierarchie mit mehr als drei Ebenen verfügt, werden die Seiten der vierten Ebene ab nicht in powerapps Portale Studio angezeigt.

- Der ausgewählte Textschrift Grad wird nur angezeigt, wenn ein genauer Schrift Grad für diesen Text definiert ist. Wenn es Teil der Standard-HTML-Tags wie z. b. p, H1, H2, H3 usw. ist, zeigt powerapps-Portale Studio den Schrift Grad nicht an.

- Webseite mit der **Seite mit der Seite "Navigations** Vorlage" zeigt nur den Link der Seiten an, die während der Erstellung der Webseite vorhanden waren. Sie können die Links auf der Seite auf der linken Seite aktualisieren, indem Sie die Seitenvorlage in eine andere Vorlage und dann zurück zur **Seite mit seitiger Navigation**ändern.

- Wenn Sie eine Webseite löschen, spiegelt Canvas das aktualisierte Menü erst nach der nächsten Aktualisierung der Canvas wider.

- Die Farbauswahl und die zugehörigen Zeichen folgen werden nur in englischer Sprache unterstützt.

- Einige Vorlagen Seiten im Personal Self-Service-Portal können die korrekte Breadcrumb nicht Rendering.

- Einige powerapps-Portale-Vorlagen, die insbesondere an Modell gesteuerte apps in Dynamics 365 gebunden sind, haben keine Standardmenü Elemente gemäß Ihrer Hierarchie von Seiten. Der Grund dafür ist, dass in allen Webseiten keine Seiten Reihenfolge zur Verfügung steht. In jedem Portal ohne die Anzeigereihenfolge von Webseiten tritt dieses Problem auf.

- Eine Fehlermeldung wird angezeigt, wenn der Seiten Inhalt (Seiten Kopie) das Limit von 65536 Zeichen überschreitet und die Seiten Zusammenfassung das Standard Limit von 2000 Zeichen überschreitet.

- Das Navigationsmenü ist nur auf dem Zeichenbereich mit einer Auflösung der minimalen Breite von 1600px sichtbar.

- Ein Bild, das auf einer Seite hochgeladen wird, wird das untergeordnete Element der Seite. Wenn Sie die Seite löschen und das Bild auf einer anderen Seite verwenden, wird das Image in den powerapps-Portalen Studio und Website nicht mehr angezeigt.

- Das Rendern von Formularen wird in powerapps Portals Studio derzeit nicht unterstützt. Wenn Sie ein Formular hinzufügen, müssen Sie **Website durchsuchen** auswählen, um die Website zu öffnen und das Formular zu überprüfen.

- Wenn Sie in einem Text-oder einem Abschnitts Hintergrund die Farbe in **keine Farbe**ändern, werden die zugehörigen Attribute, wie z. b. Hintergrundfarbe oder Schriftfarbe, von powerapps Portale Studio nicht entfernt, sondern die Werte sind NULL.

- In den folgenden Szenarios wird powerapps-Portale Studio nicht mehr geladen, und es wird die Fehlermeldung "Es gibt eine Trennung" angezeigt:
    - , Wenn die Startseite für ein Portal gelöscht oder deaktiviert ist.
    - Wenn eine Seitenvorlage, die sich auf die Startseite oder eine beliebige Seite bezieht, deaktiviert oder gelöscht wird.

- Powerapps-Portale Studio kann keinen Quellcode für diese Inhalts Ausschnitte laden, denen in Common Data Service keine Sprache zugewiesen ist.

- In einigen Fällen werden die Änderungen für Kopf-und Fußzeilen, entweder über die WYSIWYG-Darstellung von powerapps Portale Studio oder über den Code-Editor, nicht sofort reflektiert.

- Wenn eine Webseite der Suchvorlage in powerapps Portals Studio zugewiesen ist, wird eine einfache Seite mit dem Lade Modul angezeigt. Damit dies funktioniert, müssen Sie einen geeigneten Standort Marker für diese Seite erstellen.

- Die standardmäßige Studio-Vorlage wird auch als Option in der Seitenvorlage angezeigt, wenn eine neue Seite erstellt wird, sobald Sie in powerapps Portale Studio verwendet wird. Außerdem wird diese Vorlage nur in englischer Sprache eingefügt und unterstützt keine Lokalisierung basierend auf Standard Common Data Service oder der Portal Sprache.

- Eine Liste, die als Kalender Steuerelement oder Karte gerendert wird, kann nicht über powerapps-Portale Studio konfiguriert werden

- Das Feld für die partielle URL in den Seiteneigenschaften akzeptiert keine Sonderzeichen und unterbricht das Rendering für einige Zeit in der Canvas. 

- Das Hochladen von CSS schlägt möglicherweise fehl, wenn der CSS-Dateiname Sonderzeichen oder Leerzeichen im Dateinamen enthält.

- Nicht veröffentlichte Webseiten werden nicht in der Canvas von powerapps Portale Studio angezeigt.

- Wenn Sie powerapps-Portale Studio verwenden und sich Ihre Portal-Basis Sprache von der Sprache des Browsers unterscheidet, werden die neuen Webseiten, die mithilfe der standardmäßigen Studio-Vorlage erstellt wurden, in der Sprache des Browsers anstelle der Portal Sprache eingefügt.

- Im Designbereich wird **nur das auf** der Stamm Seite angewendete CSS angezeigt. Wenn Sie versuchen, eine CSS-Datei mit demselben Namen wie eine andere im Portal Verfügbare CSS-Datei hochzuladen, werden Sie von powerapps Portale Studio aufgefordert, diese Datei zu ersetzen.

- Powerapps-Portale Studio wird derzeit auf Safari unter dem Macintosh-Betriebssystem nicht unterstützt. es gibt folgende Probleme:
    - Die Auswahl der Komponente ist nicht korrekt, und der Mauszeiger auf eine Komponente bietet einen falschen Ziel Hinweis.
    - Zwei oder drei Spalten Abschnitte werden in powerapps Portale Studio nicht ordnungsgemäß dargestellt, funktionieren aber problemlos auf der Website.

