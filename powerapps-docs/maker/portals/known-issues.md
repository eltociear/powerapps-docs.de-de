---
title: Bekannte Probleme in PowerApps Portalen | Microsoft Docs
description: Erfahren Sie mehr über die bekannten Probleme in PowerApps-Portalen.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 07/18/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="known-issues"></a>Bekannte Probleme

[!include[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

## <a name="general-issues"></a>Allgemeine Fragen

- Das **Änderungsdatum** für die App könnte falsch sein, da es sich um vorab bereitgestellte Apps handelt und früher hätte bereitgestellt werden können.

- Der Eigentümer des Portale wird nicht korrekt angezeigt. Es wird als System angezeigt.

- Wenn Sie die URL eines kürzlich gelöschten Portale wiederverwenden, um ein neues Portal zu erstellen, hat dies eine gewisse Verzögerung bei der Einrichtung der Laufzeit. Dies liegt daran, dass die Bereinigung früherer Ressourcen noch im Gange wäre und zwischen 30 Minuten und 1 Stunde dauern kann, bis das neue Portal auf Azure eingerichtet ist.

- Wenn Sie eine Umgebung in PowerApps wechseln, werden die Portale innerhalb einer Umgebung möglicherweise nicht sofort in der Liste **Apps** oder **Letzte Apps** angezeigt. Dies geschieht insbesondere in Umgebungen, die in einer anderen Region als ihr Mandantentstehen. Der Workaround besteht darin, die Browseraktualisierung zu verwenden oder einige Zeit zu warten, bis das Portal in der App-Liste erscheint.

- Wenn Sie Ihr Portal erfolgreich aus dem Admin-Center PowerApps Portale zurücksetzen, wird der folgende Fehler angezeigt: "Das Portal, auf das Sie zugreifen möchten, gehört nicht dem Mandant, bei dem Sie gerade angemeldet sind. Bitte melden Sie sich ab und melden Sie sich beim richtigen Mandant an.". Sie können die Startseite PowerApps besuchen und ein neues Portal erstellen. 

## <a name="portal-designer-issues"></a>Probleme mit dem Portal-Designer

-   Wenn Sie Text im Textfeld auswählen, wird die Schriftgröße des ausgewählten Textes nicht in der Symbolleiste für die Formatierung angezeigt.

- Die Auffüllung von Spalten in einem Abschnitt ist nicht identisch mit der Darstellung auf der Website. Der Abstand wird entsprechend dem Inhalt in den Abschnitten angepasst.

- Canvas lädt keine Inhalte in chinesischer Sprache.

- Die Webseite mit der Vorlage **Seite mit Seitennavigation** zeigt nur den Link der Seiten an, die bei der Erstellung der Webseite vorhanden waren. Sie können die Links auf der linken Seite der Seite aktualisieren, indem Sie die Seitenvorlage in eine andere Vorlage ändern und dann zurück zu **Seite mit Seitennavigation**.

- Wenn Sie eine Webseite löschen, spiegelt das Canvas bis zur nächsten Aktualisierung des Canvas nicht das aktualisierte Menü wider.

- Wenn Sie eine untergeordnete Seite aus einer Neuschreibungsseite (nicht unterstützte Seiten im Portal Designer) erstellen, müssen Sie die Vorlage manuell aus dem Eigenschaftsbereich auswählen, um die Seite darzustellen.

- Wenn der Seitenname groß ist und nicht vollständig im Fenster **Seiten** angezeigt wird, wird die Schaltfläche **Auslassungspunkte** (....) nicht angezeigt. Sie müssen mit der rechten Maustaste auf den Seitennamen klicken, um die Seitenoptionen anzuzeigen.

- Wenn Sie ein deaktiviertes Inhaltsausschnitt auf einer Seite hinzugefügt haben, wird dieser im Portal Designer angezeigt. Aber, der deaktivierte Inhaltsausschnitt wird auf der eigentlichen Website ausgeblendet.

- Nur wenige Platzhalter von Komponenten wie Weblinks, Power BI, Diagramm usw. sind nicht editierbar. Aber Sie können den Text trotzdem auf der gleichen Weise bearbeiten. Die Änderungen an Platzhaltern werden nicht gespeichert.

- Informationen und zugehörige Aktionen auf dem Canvas, wie z.B. der Komponentenname, im Portal Designer werden nur in englischer Sprache unterstützt.

- Die Farbauswahl und die dazugehörigen Zeichenketten werden nur auf Englisch unterstützt.

- Einige Template-Seiten auf dem Self-Service-Portal sind nicht in der Lage, das richtige Breadcrumb darzustellen.

- Einige wenige Vorlagen von Dynamics 365 Portale haben keine Menüpunkte gemäß ihrer Seitenhierarchie. Wenn Sie  jedoch neue Seiten erstellen, werden die Menüpunkte entsprechend erstellt.
