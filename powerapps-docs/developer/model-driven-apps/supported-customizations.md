---
title: Erste Schritte mit modellgesteuerter App-Anpassung durch Code | Microsoft Docs
description: 'Sie können modellgesteuerte Apps anpassen, indem Sie Tools verwenden, die im Power Apps-Portal verfügbar sind oder in der Dokumentation beschrieben werden. '
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: shilpas
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0ac5d6ec9527334b8e9ef82fcff9e37744967c16
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2865583"
---
# <a name="get-started-with-model-driven-apps-customization-using-code"></a>Erste Schritte mit modellgesteuerter App-Anpassung durch Code

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/supported-extensions
Split to just include MDA issues
 -->

Sie können modellgesteuerte Apps anpassen, indem Sie Tools verwenden, die im Power Apps-Portal verfügbar sind oder in der Dokumentation beschrieben werden. Diese Anpassungen werden unterstützt und können aktualisiert werden.

Anpassungen, die mit anderen Methoden als den hier beschriebenen Methoden vorgenommen werden, sind nicht unterstützt und können während Updates und Upgrades auf modellgesteuerte Apps Probleme verursachen. Weitere Informationen finden Sie unter [Nicht unterstützte Anpassungen](#unsupported-customizations) weiter unten in diesem Thema.

Die Themen, die technischen Artikeln veröffentlicht wurden auf Microsoft-Websites wie dieser, werden unterstützt, sind jedoch möglicherweise nicht erweiterungsfähig.


## <a name="customizations-using-power-apps-portal"></a>Anpassungen über das Portal Power Apps vornehmen

Es gibt eine Reihe von Tools, die in modellgesteuerten Apps enthalten sind und die Sie für die Anpassung verwenden können. Die Anpassungen, die mithilfe von modellgesteuerten Apps Tools und Webanwendungen vorgenommen werden, werden vollständig unterstützt und sind vollständig aktualisierbar.

Die folgenden Anpassungsmethoden können verwendet werden, um vollständig unterstützte Anpassungen zu erstellen:

- Anpassung im Portal Power Apps oder im Solution Explorer. Weitere Informationen finden Sie unter [Übersicht über das Erstellen von modellgesteuerten Apps](../../maker/model-driven-apps/model-driven-app-overview.md)

- Einstellungen in der Webanwendung. Weitere Informationen finden Sie unter [modellgesteuerte Apps verwalten](/dynamics365/customer-engagement/admin/admin-guide)

- Reporting Services. Weitere Informationen finden Sie unter [Berichte und Analysen-Handbuch für modellgestützte Apps](/dynamics365/customer-engagement/analytics/reporting-analytics-with-dynamics-365).

> [!NOTE]
> Die Verhaltensweisen von modellgestützten Apps hängen von den Anpassungen ab, die für den zugeordneten Common Data Service übernommen werden. Weitere Informationen: [Unterstützte Anpassungen für Common Data Service](../common-data-service/supported-customizations.md)
> *Vollständig unterstützt* bedeutet, dass der Developer Support Unterstützung für Anpassungen bereitstellen kann und dass der Anwendungssupport Kunden bei der Ausführung solcher Änderungen helfen kann.


## <a name="customizations-applied-using-code"></a>Mit Code angewendete Anpassungen

Die Dokumentation auf dieser Website für Entwickler, die technischen Artikel und der Beispielcode, der auf dieser Website veröffentlicht wird und die Informationen, die vom Common Data Service Developer Support Team veröffentlicht wurden, sind in dem Bereich der Anpassungen enthalten, die mit Hilfe von Code angewendet werden. Die bestimmten Aktionen und Ebenen der Supportfähigkeit und Aktualisierbarkeit werden weiter unten in diesem Thema beschrieben.

### <a name="client-side-javascript"></a>Clientseitiges JavaScript

Sie können JavaScript in modellgestützten Apps drei Bereichen verwenden:

- **Formularskriptereignishandler**: Sie können Formularereignishandler so konfigurieren, dass sie Funktionen aufrufen, die in JavaScript-Webressourcen definiert sind.

- **Befehle auf der Befehlsleiste (Menüband)**: Sie können die Elemente oder `<CustomRule>` oder `<JavaScriptFunction>` verwenden, um Aktionen zu definieren, die Features aufrufen, die in JavaScript-Webressourcen definiert sind.

- **Webressourcen und IFRAMEs**: Sie können JavaScript-Webressourcen innerhalb von HTML-Webressourcen verwenden. IFRAMES, die so konfiguriert sind, dass sie siteübergreifendes Skripting erlauben, oder Skripts in HTML-Webressourcen, die in einem Formular enthalten sind, interagieren ggf. mit den dokumentierten `Xrm.Utility` oder `Xrm.Page`-Methoden innerhalb des Formulars über den übergeordneten Verweis.

Alle Interaktion mit den Anwendungsseiten dürfen nur über die Methoden mit den Methoden durchgeführt werden, die in der [Client-API-Referenz für modellgestützte Apps](clientapi/reference.md) dokumentiert sind. Direkter Zugriff auf das Dokumentobjektmodell (DOM) von modellgestützte Apps-Seite wird nicht unterstützt. Die Verwendung von jQuery in Formularskripten und Befehlen wird nicht empfohlen. Weitere Informationen: [Clientskripting in modellgestützten Apps mit JavaScript](client-scripting.md).

Sie können die modellgestützten App-Formulare , Ansichten, Dialogfelder und Berichte mithilfe der Identifizierungsmöglichkeiten öffnen, die in [Öffnen von Formularen, Ansichten, Dialogen und Berichten mit einer URL](open-forms-views-dialogs-reports-url.md) dokumentiert sind.

### <a name="ribbon-customization"></a>Menübandanpassung

Die Verwendung von `RibbonDiffXml` zum Hinzufügen, Entfernen oder Ausblenden von Menübandelementen wird unterstützt. Die Wiederverwendung von Menübandbefehlen, die von modellgestützten Apps definiert werden, wird unterstützt, allerdings behalten wir uns das Recht vor, die verfügbaren Befehle zu ändern oder zu entfernen. Die Wiederverwendung von JavaScript-Funktionen, die in den Menübandbefehlen definiert werden, wird nicht unterstützt.

## <a name="unsupported-customizations"></a>Nicht unterstützte Anpassungen

Änderungen an modellgestützten Apps, die ohne die Verwendung der in dieser Dokumentation beschriebenen Methoden oder Power Apps-Portal-Tools vorgenommen werden, werden nicht unterstützt und werden während Updates oder Upgrades von modellgestützten Apps nicht beibehalten. Alles, was nicht in dieser Dokumentation und den unterstützenden Dokumenten dokumentiert wird, wird nicht unterstützt. Außerdem könnten nicht unterstützte Änderungen Probleme verursachen, wenn Sie durch das Hinzufügen von Hotfixes oder Service Packs aktualisieren oder modellgestützte Apps aktualisieren.

Im Folgenden finden Sie eine Liste nicht unterstützter Aktionstypen, nach denen häufig gefragt wird: 

- Die erneute Verwendung von JavaScript-Code für modellgestützte Apps. Dieser Code könnte bei einem Upgrade geändert oder überschrieben werden.
- Bearbeiten einer Lösungsdatei zum Bearbeiten von Lösungskomponenten, abgesehen von Menübändern, Formularen, SiteMap oder gespeicherten Abfragen wird nicht unterstützt. Weitere Informationen finden Sie unter [Wann die Anpassungsdatei bearbeitet wird](when-edit-customization-file.md).
    - Das Definieren neuer Lösungskomponenten durch das Bearbeiten der Lösungsdatei wird nicht unterstützt. 
    - Das Bearbeiten der Webressourcendateien, die mit einer Lösung exportiert werden, wird nicht unterstützt. 
    - Abgesehen von den Schritten, die in [Bearbeiten einer verwalteten Lösung](../common-data-service/maintain-managed-solutions.md) dokumentiert werden, wird das Bearbeiten von Inhalten einer verwalteten Lösung nicht unterstützt.

- Anzeigen eines Entitätsformulars mit einem IFrame, der eingebettet in einem anderen Entitätsformular ist, wird nicht unterstützt.

### <a name="see-also"></a>Siehe auch

[Unterstützte Anpassungen für Common Data Service](../common-data-service/supported-customizations.md)<br/>
[Anwenden von Geschäftslogik mit Client-Skripting in modellgestützten Anwendungen mit JavaScript](client-scripting.md)<br/>
[Passen Sie Befehle und das Menüband an](customize-commands-ribbon.md)<br/>
[Webressourcen in modellgestützten Apps](web-resources.md)
