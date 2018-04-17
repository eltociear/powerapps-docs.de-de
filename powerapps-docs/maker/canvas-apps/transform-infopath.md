---
title: Transformieren Ihrer InfoPath-Formulare zu PowerApps | Microsoft-Dokumentation
description: Erste Schritte beim Transformieren Ihrer InfoPath-Formulare in PowerApps mit weiteren Informationen über gängige InfoPath-Szenarien und die Erstellung dieser Elemente in PowerApps
services: powerapps
documentationcenter: na
author: dewcatpaint1
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/05/2018
ms.author: cathed
ms.openlocfilehash: 4e81566ec427b4faa064b1ba5891fa2526497b34
ms.sourcegitcommit: eac8ad7b54a0b0eba6444a38a952dbfd17bc64b5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2018
---
# <a name="transform-your-infopath-forms-to-powerapps"></a>InfoPath-Formulare in PowerApps-Formulare transformieren

Erstellen Sie gerne nützliche Formulare in InfoPath und möchten lernen, wie Sie diese auf einer robusteren Plattform bereitstellen?

## <a name="key-advantages-of-powerapps-over-infopath"></a>Hauptvorteile von PowerApps im Vergleich zu InfoPath

Wie die meisten InfoPath-Poweruser haben Sie sicher schon seit einiger Zeit Ihre hervorragenden Fähigkeiten genutzt, um beeindruckende Formulare zu erstellen. Sie sind zwar mit den von Ihnen erstellten Formularen sehr zufrieden, wissen aber auch, dass diese ihre Grenzen haben: Sie sind &quot;nicht mehr zeitgemäß&quot;, bieten eine nicht gerade ideale Benutzeroberfläche für mobile Geräte und lassen sich nicht mit anderen Diensten verbinden, ohne Code zu schreiben. Zudem ist ihre Zukunftsfähigkeit ungewiss.

Das PowerApps-Team hat von diesen und vielen anderen Herausforderungen gehört. Und sie haben hart daran gearbeitet, Ihnen in PowerApps eine bessere Benutzererfahrung zu bieten. Das Team möchte Ihnen die Möglichkeit bieten, beim Erstellen von Apps alle Ihre geschäftsbezogenen und technologischen Fähigkeiten nutzen zu können. Mit PowerApps können Sie schnell die richtigen Geschäftslösungen erstellen und implementieren, ohne Code schreiben zu müssen.

**PowerApps für eine leistungsstarke Zukunft**  
PowerApps ist eine Software-as-a-Service-Plattform (SaaS), mit der Sie schnell und ohne zusätzlichen Aufwand hochfunktionale Apps erstellen können, die Sie im Web, in SharePoint, in Dynamics 365, in Teams, in Power BI oder auf einem mobilen Gerät einsetzen können. Und weil sie so einfach bereitzustellen sind (Sie müssen lediglich die URL zu Ihrer veröffentlichten App weitergeben), sind sie ebenso einfach zu aktualisieren.

**Teilen Ihrer Apps**  
Haben Sie schon einmal versucht, eine App zu erstellen und sie dann im Google oder Apple App Store zu veröffentlichen? Es ist kompliziert. Eine zusätzliche Herausforderung besteht darin, wenn Sie eine zweite App bereitstellen oder aktualisieren möchten, denn dann müssen die Benutzer noch viele weitere Schritte unternehmen. Nicht bei PowerApps. Die Benutzer installieren die Microsoft PowerApps-App aus ihrem App Store, melden sich dann mit dem Benutzernamen und Kennwort ihres Microsoft-Kontos an und verfügen schon über alle hochfunktionalen Apps, die Sie mit ihnen geteilt haben. Wenn Sie in Zukunft diese Apps aktualisieren oder neue Apps für sie freigeben, werden die Apps auf ihrem Gerät angezeigt. Somit sind mobile Apps ohne den Aufwand für die Geräteverwaltung ein großer Gewinn für Sie und Ihr Unternehmen.

**Apropos mobile Geräte**  
Mit PowerApps können Sie die Leistungsfähigkeit von mobilen Geräten des Benutzers für sich nutzen. Über Ihre App haben Sie Zugriff auf die Beschleunigung, die Kamera, den Kompass, die Verbindungsinformationen und die Positionssignale. Bei der Erstellung von Apps eröffnet ihnen dies eine ganze Welt von Möglichkeiten. Und letztlich wird auch die Touchfunktionalität in PowerApps ganz automatisch eingebunden, d.h. Sie müssen bei der App-Erstellung nichts zusätzlich programmieren.

**Vorkonfigurierte Features**  
Bei InfoPath war es üblich, mit Daten aus einer Datenquelle zu arbeiten. Wenn Sie jedoch irgendwo anders Aktualisierungen vornehmen wollten (z.B. an einer SharePoint-Liste in einer anderen Websitesammlung) oder eine Verbindung zu externen Diensten herstellen wollten, wurde es kompliziert, und der zugrunde liegende Code bescherte Ihnen schlaflose Nächte. Mit PowerApps ist dies anders. Die Lösung ist so konzipiert, dass Sie mit mehreren Datenquellen und Dienstverbindungen in einer App arbeiten können. Derzeit gibt es [mehr als 150 Connectors](https://docs.microsoft.com/powerapps/connections-list#all-connectors), die eine Kombination aus lokalen und Clouddaten, Microsoft Office 365 und Azure-Dienste wie Flow und Dynamics 365 sowie eine Vielzahl von Drittanbieterdiensten wie Dropbox, Google, Salesforce und Slack unterstützen. Jetzt können Sie Lösungen entwickeln, die sich an Benutzeranforderungen anpassen lassen und nicht von dem Speicherort der ursprünglichen Daten abhängen.

## <a name="powerapps-and-sharepoint-even-better-together"></a>PowerApps und SharePoint: gemeinsam noch besser

PowerApps ist ein großartiges Tool, um Ihr SharePoint-Erlebnis auf zwei Arten zu verbessern. Sie haben die Möglichkeit, entweder die Formulare für eine SharePoint-Liste anzupassen oder eine eigenständige App für die Arbeit mit SharePoint-Daten zu erstellen.

Das **Anpassen eines SharePoint-Formulars** ist äußerst nützlich, wenn Benutzer die Liste bei ihrer täglichen Arbeit verwenden. Dabei können Sie anpassen, wie Elemente in der SharePoint-Liste von Benutzern hinzugefügt, angezeigt oder bearbeitet werden. Wenn Sie auf **Formulare anpassen** klicken, wird eine einzige Anzeige &quot;Formular-App&quot; erstellt, die die Modi (Neu/Bearbeiten/Ansicht) kontextabhängig ändert. Diese Apps werden von SharePoint verwaltet; ihre Berechtigungen sind die gleichen wie die Listenberechtigungen zum Bearbeiten bzw. Anzeigen.

Die **Erstellung einer PowerApps-Zeichenbereich-App aus SharePoint** ermöglicht es Ihnen, die App selbst auf einem mobilen Gerät auszuführen. Sie kann auch in einer SharePoint-Seite eingebettet werden. Wenn Sie darauf klicken, wird eine App mit drei Anzeigen erstellt (Listenansicht, Neu/Bearbeitungsformular, Formularansicht).  Das Berechtigungs-/Freigabemodell für diese Apps ist nicht an SharePoint gebunden, sondern wird von PowerApps verwaltet.

Nachdem Sie nun den Unterschied zwischen den beiden Optionen kennen, gibt Ihnen der folgende Abschnitt einen Überblick über deren Verwendung.

## <a name="sharepoint-forms"></a>SharePoint-Formulare

Das PowerApps-Team und das SharePoint-Team haben gemeinsam eine neue Anpassungsmethode erstellt, die Sie mit SharePoint verwenden können.  Wie die meisten InfoPath-Entwickler haben Sie sicherlich gelernt, wie Sie InfoPath einsetzen, um mit SharePoint zu interagieren. An und für sich ist SharePoint ein großartiges Tool, allerdings sind die Standardformulare ein wenig umständlich und erlauben keine Anpassung oder Geschäftslogik ohne InfoPath. Zumindest war es bisher so.

Mit PowerApps können Sie nun Ihre Listenformulare als native Funktionalität anpassen. Und wenn Sie dies tun, erhalten Sie den vollen Leistungsumfang von PowerApps. Im folgenden Screenshot sehen Sie ein Beispiel für ein PowerApps-Formular mit eingebettetem Power BI-Bericht.  Die gesamte Lösung wurde in weniger als 15 Minuten erstellt.

![SharePoint-Integration](./media/transform-infopath/sharepoint-integration.png)

Ein weiteres wichtiges Feature von PowerApps ist die Möglichkeit, eine Verbindung zu einer anderen SharePoint-Websitesammlung oder einer anderen Umgebung aus dem gleichen Formular herzustellen. Möchten Sie beispielsweise ein Formular erstellen, das Daten aus Ihrer SharePoint Online-Umgebung und lokalen SharePoint-Umgebung gleichzeitig anzeigt und aktualisiert? Kein Problem. Installieren Sie das [lokale Datengateway](https://docs.microsoft.com/powerapps/gateway-management), und innerhalb weniger Minuten können Sie PowerApps, Power BI, Microsoft Flow und Azure Logic Apps mit Ihren lokalen Daten verbinden. Die Firewallregeln müssen hierzu nicht geändert werden. Eine weitere Funktionsebene kann durch die Verbindung dieser App mit Microsoft Flow genutzt werden.

## <a name="a-standalone-sharepoint-app"></a>Eine eigenständige SharePoint-App

Wenn Sie nicht nur das Listenformular aktualisieren, sondern eine vollständige, eigenständige App basierend auf Ihren SharePoint-Daten erstellen möchten, verwenden Sie diese Methode. Dies ist auch der beste Weg für den Einstieg. So können Sie den PowerApps-Zeichenbereich kennenlernen und zukünftige Apps aus einer Vielzahl von Datenquellen erstellen.

Um zu beginnen, wechseln Sie zur SharePoint-Liste, mit der Sie interagieren möchten und gehen wie folgt vor:

1. Klicken Sie in der Menüleiste auf „PowerApps“.
2. Wählen Sie „App erstellen“.
3. Geben Sie einen Namen an.
4. Klicken Sie auf „Erstellen“.

PowerApps erstellt daraufhin eine Standard-App, die Sie anpassen können.

Fangen Sie einfach an. Verwenden Sie für Ihre erste App eine einfache benutzerdefinierte Liste, die nur ein paar Felder verschiedener Typen enthält. So können Sie eine solide Grundlage erstellen und behalten den Überblick. Machen Sie sich keine Gedanken, Sie sind im Handumdrehen ein Profi und bereit, komplexe Apps in Angriff zu nehmen.  Hilfreiche Informationen beim Durchlaufen Ihrer ersten App finden Sie in dieser [Dokumentation](https://docs.microsoft.com/powerapps/generate-app-from-sharepoint-list-interface) oder in diesem [Communityvideo](https://youtu.be/BnYe_7fpZRM). Die folgenden Beispiele zeigen allgemeine InfoPath-Aufgaben und wie Sie sie in PowerApps erledigen. Jede davon baut auf einer einfachen SharePoint-Listen-App auf.

# <a name="how-do-you-do-that-with-powerapps"></a>Wie machen Sie das mit PowerApps?

Nun, da Sie die grundlegenden Konzepte kennen, können Sie die nächsten Schritte gehen. Ihre erste App haben Sie in der Tasche. Der folgende Abschnitt hilft Ihnen dabei, einige der gängigen InfoPath-Konzepte in PowerApps anzuwenden.

**Ausblenden, Anzeige oder Sperren eines Felds basierend auf einem Wert**  
Eine der gebräuchlichsten Methoden, um ein erfolgreiches Formular zu erstellen, ist die Verwendung einer stabilen Geschäftslogik und die Möglichkeit, diese Logik durchzusetzen. Eine Option besteht darin, den Zustand eines Felds basierend auf einem Wert oder einer Aktion zu ändern. Mit PowerApps können Sie Ihr Steuerelement auswählen und den Anzeigemodus auf „Bearbeiten“ oder „Ansicht“ setzen, um festzulegen, ob ein Benutzer das Feld ändern kann. Eine zweite Methode ist die Verwendung einer einfachen If-Formel, um eine Bedingung hierfür festzulegen. Wählen Sie zunächst die Bezeichnung aus, die Sie bearbeiten möchten. Klicken Sie dann auf das Schlosssymbol, um die Karte zu entsperren, sodass Sie den Wert ändern können.

![Aus- bzw. Einblenden gesperrter Datenkarten](./media/transform-infopath/hide-show-lock.png)

Scrollen Sie nun auf der Karte rechts nach unten, und bearbeiten Sie die Eigenschaft „DefaultMode“.

![If-Else-Anweisungsausdrücke](./media/transform-infopath/if-else-statement.png)

In diesem Beispiel verwenden Sie eine If-Anweisung. If(ThisItem.Color = &quot;Blue&quot;, DisplayMode.View, DisplayMode.Edit) Diese Anweisung besagt Folgendes: Wenn der aktuelle Wert im Feld für die Farbe „blau“ ist, dann ist das Feld „Tier“ schreibgeschützt, anderenfalls kann das Feld bearbeitet werden.

Wenn Sie die Karte überhaupt nicht anzeigen möchten, können Sie eine ähnliche Funktion in das Feld „Sichtbar“ direkt über „DisplayMode“ einfügen.

Eine andere Spielerei hier wäre das Ausblenden einer Genehmigungsschaltfläche, die nur angezeigt wird, wenn die E-Mail-Adresse des Benutzers mit der E-Mail-Adresse des Genehmigers übereinstimmt. Hinweis: „User().Email“ ist die Art des Zugriffs auf die E-Mail-Adresse des aktuellen Benutzers. So könnten Sie zum Festlegen der Sichtbarkeit der Schaltfläche Folgendes eingeben: If(YourDataCard.Text = User().Email, true, false). Dabei ist „YourDataCard“ die Karte, auf der Sie die E-Mail-Adresse des Genehmigers speichern.

**Bedingte Formatierung**  
In ähnlicher Weise wie oben, wo Sie das Feld ausgeblendet haben, können Sie den Benutzern auch visuelles Feedback geben. Möglicherweise möchten Sie Text in Rot markieren, wenn der eingegebene Wert außerhalb des zulässigen Bereichs liegt, oder den Text und die Farbe der Uploadschaltflächen ändern, um ihn nach dem Upload einer Datei zu löschen. Dies lässt sich alles mithilfe von Funktionen erreichen, zum Beispiel mit einer If-Funktion in Eigenschaftsfeldern wie „Farbe“ oder „Sichtbar“.

Sie könnten auch durch die Verbindung der If-Funktion mit der [IsMatch](https://docs.microsoft.com/powerapps/functions/function-ismatch)-Funktion die Textfarbe des E-Mail-Felds in Rot ändern, wenn der Benutzer keine korrekt formatierte E-Mail-Adresse in das Eingabefeld eingegeben hat. Hierzu würden Sie den Farbwert von „TextInput1“ auf „If(IsMatch(TextInput1.Text, Email), Black, Red)“ setzen, wobei „TextInput1“ das Feld ist, in das der Benutzer eine E-Mail-Adresse eingibt. „IsMatch“ bietet eine Vielzahl von vordefinierten Mustern (wie E-Mail-Adressen) und die Möglichkeit, eigene Muster zu erstellen. Weitere Informationen zur bedingten Formatierung finden Sie in diesem [Communityvideo](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/PowerApps-Conditional-Formatting-and-Popups/m-p/84962).

**Implementieren der rollenbasierten Sicherheit**  
Die erste Funktion, die Sie ins Auge fassen sollten, lautet [DataSourceInfo](https://docs.microsoft.com/powerapps/functions/function-datasourceinfo). Welche Informationen Sie von der Datenquelle erhalten, hängt von der Datenquelle ab, aber oft können Sie mit „DataSourceInfo(YourDataSource, DataSourceInfo.EditPermission)“ prüfen, ob der Benutzer Zugriff auf die Daten hat. Ersetzen Sie „YourDataSource“ durch den Namen Ihrer Datenquelle. Damit können Sie ein Formular oder eine Schaltfläche nur dann einblenden, wenn der Benutzer Schreibzugriff hat. Die vollständige Liste der Informationen, die Sie mit der Funktion abfragen können, finden Sie in der Dokumentation zu „DataSourceInfo“.

Wenn Sie stattdessen Active Directory-Gruppen verwenden möchten, um den Zugriff auf Schaltflächen oder Formulare in Ihrer App zu verwalten, sind weitere Schritte erforderlich. Nutzen Sie hierzu die Flexibilität von PowerApps, und erstellen Sie Ihren eigenen Connector über die Graph-API von Microsoft. Lassen Sie sich von dieser Aufgabe nicht abschrecken, sondern nutzen Sie diese [Dokumentation](https://powerapps.microsoft.com/blog/implementing-role-based-permission/), die Sie sicher durch die einzelnen Schritte dieses Prozesses führt.

**Senden einer E-Mail aus Ihrer App**  
Es gibt viele Möglichkeiten, eine E-Mail aus PowerApps zu versenden. Der einfachste Weg ist die Verwendung des Office 365 Outlook-Connectors. Mit diesem Connector können Sie eine E-Mail von Ihrer Adresse aus Ihrer App heraus versenden. Sie können auch E-Mail-Nachrichten und andere Aufgaben erhalten, die mit Ihrem Postfach interagieren. Informationen zum Senden einer E-Mail finden Sie in dieser [Dokumentation](https://docs.microsoft.com/powerapps/connections/connection-office365-outlook) bzw. in diesem [Communityvideo](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/Send-an-email-from-PowerApps/m-p/74349).

Wenn Sie eine komplexere E-Mail versenden müssen, z.B. indem Sie eine Genehmigungskette für einen SharePoint-Genehmigungsworkflow erstellen, dann ist die Erstellung eines Microsoft Flow-Elements, mit dem Sie Ihre App verbinden, die Lösung. Sobald Ihre App mit Microsoft Flow verbunden ist, können Sie die umfassende Leistung einer Workflowengine nutzen, die – wie PowerApps – über eine sehr gute Verbindung zu externen Daten und Diensten verfügt. Weitere Informationen zur Verbindung von PowerApps und Microsoft Flow finden Sie in dieser [Dokumentation](https://docs.microsoft.com/powerapps/using-logic-flows).

Und wenn Sie die gesuchte E-Mail-Option noch nicht gefunden haben, können Sie auch die PowerApps-Connectors für Benchmark Email, Gmail, MailChimp, Outlook.com, SendGrid oder SMTP nutzen. Das ist das Schöne an PowerApps: Konnektivität.

**Workflows**  
Es ist schwer, über Geschäftsanwendungen und Geschäftslogik zu sprechen, ohne eine Workflowengine zu erwähnen. Die gute Nachricht ist, dass das PowerApps-Team das Rad nicht neu erfunden hat, um Ihnen noch eine Workflowengine zur Verfügung zu stellen. Stattdessen wird Ihnen ein stabiler Connector zum Microsoft Flow-Dienst geboten. Jetzt können Sie Prozesse und Aufgaben für mehr als [200 verschiedene Dienste](https://flow.microsoft.com/connectors/) automatisieren, indem Sie deren einfach zu bedienende Workflowengine nutzen. Weitere Informationen zur Verbindung von PowerApps und Microsoft Flow finden Sie in dieser [Dokumentation](https://docs.microsoft.com/powerapps/using-logic-flows).

**Variablen mit PowerApps**  
Beim Erstellen von Lösungen wird selbstverständlich davon ausgegangen, dass Variablen einbezogen werden müssen. Obwohl PowerApps drei Arten von Variablen anbietet, möchten Sie diese jedoch nur dann verwenden, wenn es erforderlich ist. Anstatt darüber nachzudenken, Daten abzurufen, sie in einer Variablen zu speichern und auf die Variable zu verweisen, müssen Sie nur noch direkt auf diese Daten verweisen. Ein guter Vergleich ist Excel. In Excel ist das Ergebnis keine Variable, sondern die Summe anderer Felder. Wenn Sie diesen Wert also an anderer Stelle auf dem Blatt verwenden möchten, geben Sie das Feld an, in dem Sie die Summe berechnet haben. In der [Dokumentation](https://docs.microsoft.com/powerapps/working-with-variables) finden Sie hierzu eine gute Erklärung. Seien Sie offen für einen anderen Denkprozess.

Wenn Sie noch Variablen benötigen (was in vielen Fällen vorkommt), erfahren Sie nun, welche unterschiedlichen Möglichkeiten Sie haben. Denken Sie daran, dass Sie mit PowerApps keine Variablen definieren müssen. Verwenden Sie einfach eine der Funktionen, um einen Namen und einen zu speichernden Wert festzulegen, und Ihre Variable wird erstellt. Sie können die von Ihnen erstellten Variablen anzeigen, indem Sie in der Menüleiste auf „Ansicht“ klicken und „Variablen“ auswählen. Variablen befinden sich im Arbeitsspeicher, und ihre Werte gehen beim Schließen der App verloren. Es gibt die folgenden drei Arten von Variablen:

- Globale Variablen sind das, woran Sie zuerst denken. Hier können Sie mit der [Set](https://docs.microsoft.com/powerapps/functions/function-set)-Funktion einen Wert für die Variable angeben, der dann über Ihre App zur Verfügung steht. Die Funktion kann z.B. wie folgt verwendet werden: Set(YourVariable, YourValue). Dann können Sie in Ihrer App namentlich auf „YourVariable“ verweisen.
- Kontextvariablen sind Variablen, die nur in der Anzeige verfügbar sind, in der sie definiert sind. Beim Verlassen der Anzeige werden sie zurückgesetzt. Sie werden oft verwendet, um Informationen zu speichern, die von einer vorherigen Anzeige übergeben wurden, oder, um zu verfolgen, ob das Formular z.B. abgeschickt wurde. Die übliche Verwendung von [UpdatedContext](https://docs.microsoft.com/powerapps/functions/function-updatecontext) ist „UpdateContext( { Submitted: "true" } )“. Dies würde die „Submitted“-Variable auf „true“ setzen. Sie können diesen Teil der Schaltfläche „Senden“ auf der Seite verwenden, um zu verfolgen, dass die Informationen übermittelt wurden, und alle Felder in schreibgeschützte Felder umwandeln. Hinweis: Sie verwenden „:“. Sammlungen werden zum Speichern von Tabellen mit Informationen verwendet, die individuell aktualisiert werden können. Sehen Sie sich [Sammeln](https://docs.microsoft.com/powerapps/functions/function-clear-collect-clearcollect) an, um zu beginnen. Ein Verwendungsbeispiel könnte das Erstellen eines Einkaufswagens sein, für den der Benutzer verschiedene SharePoint-Elemente markiert, die er versenden möchte. Die Umsetzung dieses Konzepts wird in diesem [Communityvideo](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/Learn-about-PowerApps-Collections/m-p/89180) veranschaulicht.

**Überlappende Dropdownmenüs**  
Überlappende Dropdownmenüs sind sehr nützlich. Sie ermöglichen es Ihnen, die Auswahl in einem Dropdownmenü basierend auf dem im vorherigen Dropdownmenü ausgewählten Wert zu filtern. In PowerApps werden diese oft durch zwei Datenquellen in Ihrer App erzeugt. Die erste Datenquelle sind die Daten, mit denen Sie arbeiten oder die Sie aktualisieren, und die zweite Datenquelle wird zum Speichern der Werte verwendet, um den gewünschten Überlappungseffekt zu erzielen. Nachfolgend ein Beispiel für die zweite Datenquelle mit den Auswahlmöglichkeiten.

![Überlappende Dropdownmenüs](./media/transform-infopath/cascading-dropdowns.png)

Jetzt würden Sie Ihr erstes Dropdown-Steuerelement erstellen, und für die „Items“-Eigenschaft würden Sie die Formel „Distinct(Impacts, Title)“ verwenden, um im Dropdownmenü nur „Cost“ (Kosten), „Program Impact“ (Programmauswirkungen) und „Schedule“ (Zeitplan) anzuzeigen. Dann würden Sie ein zweites Dropdownmenü hinzufügen und die „Items“-Eigenschaft auf „Filter(Impacts,ddSelectType.Selected.Value in SCategory)“ setzen, wobei „ddSelectType“ der Name des ersten Dropdownfelds ist. So einfach erhalten Sie überlappende Dropdownmenüs. Weitere Informationen finden Sie in diesem Beitrag des PowerApps-Teams [SharePoint: Cascading Dropdowns in 4 Easy Steps!](https://powerusers.microsoft.com/t5/PowerApps-Community-Blog/SharePoint-Cascading-Dropdowns-in-4-Easy-Steps/ba-p/16248) (SharePoint: Überlappende Dropdownmenüs in vier einfachen Schritten) oder in diesem [Communityvideo](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/PowerApps-Cascading-Dropdown/m-p/92813). Übrigens können Sie diese Aufgaben genauso einfach ohne SharePoint ausführen.

**Erstellen Sie keine einzelne Super-App**  
Mit PowerApps können Sie eine App aus einer anderen aufrufen. So können Sie anstelle des von Ihnen erstellten InfoPath-Massenformular eine Gruppe von Apps erstellen, die sich gegenseitig aufrufen und sogar Daten weitergeben. Auf diese Weise wird die Entwicklung erheblich vereinfacht.

## <a name="next-steps"></a>Nächste Schritte

Mit den obigen Informationen sind Sie nun bereit für die reale Welt und können damit beginnen, eine PowerApps-App nach der anderen zu erstellen. Während Sie weitere Erfahrungen in der Praxis sammeln, finden Sie unten einige nützliche Links als Hilfestellung. Einer dieser Links führt Sie zur PowerApps-Communityseite. Treten Sie noch heute in die Community ein, denn in der Entwicklergemeinschaft erweitern Sie Ihre Kenntnisse viel schneller als alleine.

[**Referenz zu Formeln für PowerApps**](https://docs.microsoft.com/en-us/powerapps/formula-reference): Immer eine gute Möglichkeit, sich inspirieren zu lassen. Stöbern Sie einfach in einigen der Standardfunktionen.

[**PowerApps-Community**](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1): Sehen Sie sich Beispiele an, schließen Sie sich mit anderen zusammen, stellen Sie Fragen und beantworten Sie sie, und helfen Sie der PowerApps-Community zu wachsen.