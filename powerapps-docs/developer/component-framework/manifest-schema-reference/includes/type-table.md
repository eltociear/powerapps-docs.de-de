---
title: Typ-Table | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
ms.assetid: 41ea27ac-65b6-45a4-ae03-5f8d02dfc67b
---

|Value|Beschreibung|
|--|--|
|`Currency`|Geldbeträge zwischen -922.337.203.685.477 und 922.337.203.685.477 können in diesem Feld verwendet werden. Sie können eine Präzisionsebene angeben, die Präzision auf einer bestimmten Währung basieren oder eine von der Organisation genutzte einzelne Standardpräzision verwenden.|
|`DateAndTime.DateAndTime`|Zeigt Datum und Uhrzeit an.|
|`DateAndTime.DateOnly`|Zeigt nur das Datum an.|
|`Decimal`|Es können bis zu 10 Dezimalstellen für Werte zwischen -100.000.000.000 und -100.000.000.000 in diesem Feld verwendet werden. Sie können die Präzisionsebene und die Maximal- und Minimalwerte angeben.|
|`Enum`|Aufzählungsdatentyp|
|`FP`|Es können bis zu 5 Dezimalstellen für Werte zwischen -100.000.000.000 und -100.000.000.000 in diesem Feld verwendet werden. Sie können die Präzisionsebene und die Maximal- und Minimalwerte angeben. |
|`Multiple`|Bis zu 1.048.576 Textzeichen können in diesem Feld enthalten sein. Sie können die maximale Länge als weniger festlegen. Wenn Sie das Feld einem Formular hinzufügen, können Sie den Umfang des Felds angeben.|
|`OptionSet`|Dieses Feld stellt einen Satz von Optionen zur Verfügung. Jede Option hat einen Zahlenwert und eine Beschriftung. Bei Hinzufügung zu einem Formular enthält dieses Feld ein Steuerelement für Benutzer zur Auswahl von nur einer Option. |
|`SingleLine.Email`|Der Text bietet einen mailto-Link zum Öffnen der E-Mail-Anwendung des Benutzers.|
|`SingleLine.Phone`|In der Webanwendung sind Felder klick-aktiviert, um Aufrufe mit Skype oder Lync zu initiieren, wenn ein Client dafür auf Ihrem Computer installiert ist. Die Wahl des Telefonieanbieters befindet sich am Ende der Registerkarte "Allgemein" der Systemeinstellungen. Für Dynamics 365 for tablets ist Skype der einzige verfügbare Telefonieanbieter.|
|`SingleLine.Text`|Diese Option zeigt einfach Text an.|
|`SingleLine.TextArea`|Diese Formatoption kann verwendet werden, um mehrere Textzeilen anzuzeigen. Aber bei einem Limit von 4000 Zeichen ist das Mehrzeilentextfeld besser geeignet, wenn große Textmengen erwartet werden.|
|`SingleLine.Ticker`|Für die meisten Sprachen fungiert der Text als Link, um die MSN Money-Website zu öffnen, um Details zum Aktienkurs anzuzeigen, der durch das Tickersymbol dargestellt wird. Für bestimmte ostasiatische Sprachen wird das Fenster Bing-Suchergebnisse abnstelle des Tickersymbol geöffnet.|
|`SingleLine.URL`|Der Text bietet einen Hyperlink, um die angegebene Seite zu öffnen. Jedem Text, der nicht mit einem gültigen Protokoll beginnt, wird" http://" vorangestellt. Nur HTTP-, HTTPS-, FTP-, FTPS-, ONENOTE- und TEL-Protokolle sin in diesem Feld erlaubt.|
|`TwoOptions`|Dieses Feld stellt zwei Optionen zur Verfügung. Jede Option hat den Zahlenwert 0 oder 1, entsprechend dem Wert "true" oder "false". Darüber hinaus verfügt jede Option über eine Beschriftung, sodass die Werte "true" und "false" als "Ja"/"Nein", "Heiß"/"Kalt", "EIN"/"AUS" oder in beliebiger anderer Weise angezeigt werden können.|
|`Whole.None`|Diese Option zeigt einfach eine Zahl an.|
