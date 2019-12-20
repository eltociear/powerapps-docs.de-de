---
title: Zusätzliche Steuerelemente für Dynamics 365 für Smartphones und Tablets | MicrosoftDocs
description: Eine Liste der Steuerelemente die für die Verwendung mit Dynamics 365 für Smartphones und Tablets verfügbar ist
ms.custom: ''
ms.date: 06/18/2018
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
ms.assetid: 7920ef78-2540-48ad-ba25-9ce9cb995ed1
caps.latest.revision: 63
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d2883f0912f9708acf8c24b5ec32996cb96ad3c6
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2863594"
---
# <a name="additional-controls-for-dynamics-365-for-phones-and-tablets"></a>Zusätzliche Steuerelemente für Dynamics 365 für Smartphones und Tablets 

 Sie können einen reichhaltigen Satz an zusätzlichen Steuerelementen verwenden, um eine touch-freundliche Erfahrung auf Dynamics 365 für Smartphones und Tablets zu erstellen. Diese umfassen Schieberegler, Schalter, Multimedia-Player, Eingabemasken, Kalender und andere Steuerelemente.  

 
> [!NOTE]
>  Sie können diese zusätzlichen Steuerelemente nur mit mobilen Apps verwenden. Sie werden in der Web-App nicht unterstützt.  
  
 Um diese Steuerelemente im Formular-Editor zu verwenden:  
  
1.  Doppelklicken Sie in dem Feld oder der Liste, denen Sie das Steuerelement hinzufügen möchten.  
  
2.  Klicken Sie auf die Registerkarte **Steuerelemente**.  
  
3.  Klicken Sie auf **Steuerelement hinzufügen**.  
  
4.  Wählen Sie das gewünschte Steuerelement aus, und klicken Sie anschließend auf **Hinzufügen**.  
  
    > [!NOTE]
    >  Je nach Feld- oder Listentyp sind unterschiedliche Steuerlemente verfügbar. Beispielsweise sind Schiebereglerkontrollen möglicherweise nur für numerische oder Geldfelder verfügbar, und das Kalendersteuerelement ist ausschließlich für Listen verfügbar.  
  
5.  Wählen Sie die Geräte aus, auf denen das Steuerelement angezeigt werden soll (Smartphone, Tablet oder beides). Steuerelemente sind für Telefonkopfzeilenfelder nicht verfügbar.  
  
6.  Konfigurieren Sie die Werte für jede Eigenschaft.  
  
7.  Klicken Sie auf **OK**, wenn Sie mit das Konfigurieren des Steuerelements abgeschlossen haben.  
  
 Im Folgenden finden Sie Beschreibungen für die Steuerelemente, die Sie auf Formularen für Dynamics 365 für Telefone und Tablet-Computer verwenden können.  
  
## <a name="calendar-control"></a>Kalender-Steuerelement  
 Verwenden Sie dieses Steuerelement, um Formulare so zu konfigurieren, dass sie als Kalenderansicht in Dynamics 365 für Smartphones und Tablets angezeigt werden. Sie können dieses Steuerelement dazu einsetzen, um Telefone und Tablet-Computer durch Dashboards, Listen oder Entitätsraster zu ersetzen.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Startdatum|Definieren Sie das Startdatum und die Uhrzeit der Elemente, die in der Kalenderansicht grafisch darzustellen sind. Die folgenden Werte sind einige der Spalten in dieser Ansicht vom Typ Datum.|  
|Enddatum|Definieren Sie das Enddatum und die Uhrzeit der Elemente, die in der Kalenderansicht grafisch darzustellen sind. Die folgenden Werte sind einige der Spalten in dieser Ansicht vom Typ Datum.|  
|Dauer|Die Dauer in Minuten. Wenn Sie einen Wert für das Enddatum angeben, wird die Dauer ignoriert.|  
|Beschreibung|Dies ist die Beschriftung, die Sie für Kalenderelemente sehen möchten.|  
  
 Die Mindestdauer, die im Kalender angezeigt wird, beträgt 30 Minuten. Artikel mit einer Länge von weniger als 30 Minuten werden auch weiterhin als 30 Minuten lang angezeigt.  
  
 Das Kalendersteuerelement unterstützt alle Datumsverhalten ( Benutzer-Daten und Zeitzonen-unabhängig).  
  
## <a name="timeline-control"></a>Zeitachsensteuerelement  
 Stellen Sie eine Zeitachse von aktuellen, relevanten Zeitungsartikeln und -Tweets für eine Firma bereit.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|CC_Timeline_Title|Zuzuweisende Eigenschaft für den Titel jedes Zeitachsenelements.|  
|CC_Timeline_Title_Desc|Beschreibung für Titel.|  
|CC_Timeline_Label1|Feld, das unter dem Titel des Zeitleistenelements angezeigt wird.|  
|CC_Timeline_Label1_Desc|Beschreibung für Beschriftung 1.|  
|CC_Timeline_Label2|Feld, das nach Beschriftung 1. angezeigt wird.|  
|CC_Timeline_Label2_Desc|Beschreibung für Beschriftung 2.|  
|CC_Timeline_Label3|Feld, das nach Beschriftung 2. angezeigt wird.|  
|CC_Timeline_Label3_Desc|Beschreibung für Beschriftung 3.|  
|CC_Timeline_Label4|Feld, das nach Beschriftung 3. angezeigt wird.|  
|CC_Timeline_Label4_Desc|Beschreibung für Beschriftung 4.|  
|CC_Timeline_Label5|Feld, das nach Beschriftung 4. angezeigt wird.|  
|CC_Timeline_Label5_Desc|Beschreibung für Beschriftung 5.|  
|CC_Timeline_Timestamp|Feld, das zum Sortieren der Zeitleiste in umgekehrter chronologischer Reihenfolge verwendent wird.|  
|CC_Timeline_Timestamp_Desc|Beschreibung für Zeitstempel.|  
|CC_Timeline_Group|Feld, das zum gruppieren der Zeitachse zugewiesen wird.|  
|CC_Timeline_Group_Desc|Beschreibung für Gruppenfeld.|  
|CC_Timeline_GroupOrder|Reihenfolge der Gruppe, der das Element angehört, im Verhältnis zu anderen Gruppen (weisen Sie Werte 1, 2, 3, und so weiter zu, damit Gruppen angezeigt werden können). Die Gruppe wird mit aufsteigendem Wert der zugewiesenen Gruppenwerte angezeigt.|  
|CC_Timeline_GroupOrder_Desc|Beschreibung für Gruppenbestellungsfeld.|  
|CC_Timeline_URL|Zuzuweisendes URL-Feld zur Anzeigte der URL jedes Zeitachsenelements.|  
|CC_Timeline_URL_Desc|Beschreibung für URL-Feld|  
|CC_Timeline_ThumbnailURL|Zuzuweisendes Feld für Miniaturansichten des Bilds/Symbols, das für jedes Element angezeigt wird-|  
|CC_Timeline_ThumbnailURL_Desc|Beschreibung für das `ThumbnailURL`-Feld.|  
|CC_Timeline_Filter|Zuzuweisendes Feld für jeden Zeitachsenfilter.|  
|CC_Timeline_Filter_Desc|Beschreibung für Filter.|  
|CC_Timeline_Footer|Als Fußzeile der Zeitachse anzuzeigende Webressource.|  
|CC_Timeline_Footer_Desc|Beschreibung für Fußzeilenfeld.|  
  
## <a name="linear-slider"></a>Linearer Schieberegler  
 Mit dem linearen Schiebereglersteuerelement können die Benutzer Zahlenwerte über einen Schieberegler eingeben. Darüber hinaus ist die manuelle Eingabe der Menge möglich. Der Regler ermöglicht nur die Eingabe und Anzeige ganzer Zahlen. Verwenden Sie dieses Steuerelement für alle numerische Felder oder Geldfelder.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Max.|Festlegen des maximalen Anzeigewerts für den Schieberegler.|  
|Min.|Festlegen des minimalen Anzeigewerts des Schiebereglers.|  
|Wert|Der Anzeigewert des Schiebereglers.|  
|Schritt|Legen Sie den Betrag fest, der zum aktuellen Wert addiert oder davon subtrahiert werden soll, wenn Daten mithilfe dieses Steuerelements eingegeben werden.|  
  
## <a name="option-sets"></a>Optionssätze  
 Das Optionssatz-Steuerelement stellt einen Satz von Optionen bereit, aus denen Benutzer beim Eingeben von Daten wählen können. Verwenden Sie dieses Steuerelement für Optionssätze mit zwei oder drei Optionen.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Feld|Zeigt das Feld an, dem das Steuerelement zugeordnet ist.|  
  
## <a name="flip-switch"></a>Kippschalter  
 Der Umschalter ist wie ein Ein/Aus-Schalter, der eine Auswahl zwischen zwei Werten ermöglicht.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Feld|Zeigt das Feld an, dem das Steuerelement zugeordnet ist.|  
  
## <a name="star-rating"></a>Bewertungssterne  
 Verwenden Sie die Sternbewertung, um eine visuelle Darstellung einer Bewertung bereitzustellen. Die maximale Anzahl der Sterne, die Sie festlegen können, ist fünf. Sie können dieses Steuerelement nur für ganze Zahlen verwenden. Dezimalwerte werden nicht akzeptiert.  
  
> [!NOTE]
>  Stellen Sie daher sicher, für dieses Steuerelement die Option **Im Web ausblenden** auszuwählen.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Max.|Wählen Sie die maximale Anzahl von Bewertungssternen für das Steuerelement aus der Dropdownliste aus.|  
  
## <a name="radial-knob"></a>Radial-Knopf  
 Der Radial-Knopf bietet Benutzern Wege zur Dateneingabe durch das Verschieben des Knopfs. Er wird auf dem Bildschirm als Kreis angezeigt. Das Radialknopf-Steuerelement ermöglicht nur die Eingabe und Anzeige ganzer Zahlen. Verwenden Sie dieses Steuerelement für alle numerische Felder oder Geldfelder. Sie können Touch verwenden, um den Wert zu ändern, oder Sie können einfach das Tastenfeld verwenden, um auf die Zahl zu fokussieren und sie zu bearbeiten.  
  
> [!NOTE]
>  Dieses Steuerelement wird auf Android 4.2- und 4.3-Geräten nicht unterstützt. Es wirkt sich auf die Bildlauferfahrung in diesen Versionen aus.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Max.|Festlegen des maximalen Werts für die Anzeige auf dem Messgerät.|  
|Min.|Festlegen des minimalen Werts für die Anzeige auf dem Messgerät.|  
|Wert|Rufen Sie den Wert für die Anzeige auf dem Messgerät ab oder legen Sie ihn fest.|  
|Schritt|Legen Sie den Betrag fest, der zum aktuellen Wert addiert oder davon subtrahiert werden soll, wenn Daten mithilfe dieses Steuerelements eingegeben werden.|  
  
## <a name="website-preview"></a>Websitevorschau  
 Verwenden Sie das Websitevorschausteuerelement, um ein URL-Feld ein zuordnen und eine Vorschau der Website anzuzeigen.  
  
> [!IMPORTANT]
>  Mit der Aktivierung dieses Steuerelements stimmen Sie zu, Ihren Benutzern bestimmte identifizierbare Geräteinformationen mit einem externen System freizugeben. Die Daten, die aus externen Systemen in eine Power Apps-App oder in Dynamics 365-Apps wie z. B. Dynamics 365 Sales oder Dynamics 365 Customer Service importiert werden, unterliegen unseren Datenschutzbestimmungen unter [Microsoft-Datenschutz und Cookies](https://go.microsoft.com/fwlink/p/?LinkId=521839).  
>   
>  [Datenschutzhinweise](use-the-form-editor-legacy.md#BKMK_PrivacyNotices)  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Feld|Zeigt das Feld an, dem das Steuerelement zugeordnet ist.|  
  
## <a name="bullet-graph"></a>Lineardiagramm  
 Das Aufzählungszeichendiagrammsteuerelement zeigt ein einzelnes Schlüsselmaß mit vergleichbaren Maß und qualitative Bereiche, um unmittelbar zu signalisieren ob die Maßnahme gut oder schlecht ist, oder einen anderen Status hat. Verwenden Sie dieses Steuerelement für alle numerische Felder oder Geldfelder in Dashboards. Beispielsweise können Sie den Wert zum tatsächlichen Umsatz zuordnen und das Ziel zum geschätzten Umsatz, um den tatsächlichen und den geschätzten Umsatz grafisch darzustellen.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Max.|Festlegen des maximalen Werts für die Anzeige im Diagramm.|  
|Min.|Festlegen des minimalen Werts für die Anzeige im Diagramm.|  
|Good|Legen Sie einen Wert fest, der als gut für die Maßeinheit eingestuft wird (optional).|  
|Fehlerhaft|Legen Sie einen Wert fest, der als schlecht für die Maßeinheit eingestuft wird (optional).|  
|Wert|Zeigt das Feld an, dem das Steuerelement zugeordnet ist.|  
|Ziel|Ordnen Sie dies dem Feld zu, mit dem Sie den Wert vergleichen möchten. Beispiel: Wenn **Wert** zu **Tatsächl. Umsatz** zugeordnet ist, können Sie **Ziel** zu **Geschätzter Umsatz** zuordnen, oder Sie können einen statischen Wert bereitstellen.|  
  
## <a name="pen-control"></a>Stiftsteuerelement  
 Verwenden Sie das Stiftssteuerelement zur Erfassung von geschriebener Eingaben wie z. B. Unterschriften.  
  
> [!NOTE]
>  Die mindestens empfohlene **Maximale Länge**, die für das Feld festgelegt ist, das diesem Steuerelement zugeordnet ist, ist 15000.  
>   
>  Stellen Sie daher sicher, für dieses Steuerelement die Option **Im Web ausblenden** auszuwählen.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|PenMode|Geben Sie auf **PenMode! Abgehobener Betrag**, **PenMode! Löschen** oder **PenMode!Auswählen** an, um zu bestimmen, was passiert, wenn ein Benutzer ein Stiftzeigegerät im Stiftsteuerelement verwendet.|  
  
## <a name="auto-complete"></a>Automatische Vervollständigung  
 Das Vervollständigen-Steuerelement filtert automatisch eine Artikelübersicht der Eingabe, und lässt Sie den Wert aus der Dropdownliste auswählen Sie können dieses Steuerelement beispielsweise verwenden, damit Benutzer aus einer Dropdownliste Staaten oder Länder/Regionen auswählen können. Dieses Steuerelement ordnet ein Feld des Typs **Einzelne Textzeile** zu.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Feld|Zeigt das Feld an, dem das Steuerelement zugeordnet ist.|  
|Quelle|Legen Sie die Quelle für die Daten fest (Gruppierte Optionen, Optionssatz oder Ansicht).|  
|Optionssatz|Wählen Sie den Optionssatz für dieses Feld aus.|  
|Anzeigen|Wählen Sie die Entität und die Ansicht für dieses Feld aus.|  
|Feld|Wählen Sie das Feld der primären Entität der Ansicht aus, das als Datenquelle verwendet werden soll.|  
  
## <a name="multimedia"></a>Multimedia  
 Sie können Videos einbetten, um eine bessere Kundenerfahrung für Verkäufe zu ermöglichen und Menschen unterwegs zu erreichen. Verwenden Sie dieses Steuerelement, um ein URL-Feld zuzuordnen, das den Audio- oder Video-Link zum Abspielen im Steuerelement enthält.  
  
> [!NOTE]
>  Dieses Steuerelement wird auf Android-Versionen 4.4 und höher unterstützt.  
>   
>  YouTube-Videos werden momentan auf Windows 8 und Windows 8.1-Tablets und -Smartphones nicht unterstützt. Unter Windows 10 werden derzeit nur HTTPS-Videos unterstützt (einschließlich YouTube).  
  
 Unterstützte Medientypen enthalten:  
  
-   MP4-Dateien Streamen  
  
-   YouTube-Videos  
  
-   Azure Media  
  
-   Audiostreams  
  
 [Datenschutzbestimmungen](use-the-form-editor-legacy.md#BKMK_PrivacyNotices)  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Medien|Geben Sie die URL der Mediendatei ein, die dieses Steuerelement wiedergeben soll.|  
  
## <a name="number-input"></a>Zahleneingabe  
 Verwenden Sie das Zahleneingabesteuerelement, um die Benutzer bei der schnellen Dateneingabe zu unterstützen. Die Benutzer müssen nur auf die Plus- und Minusschaltflächen tippen, um nur einen numerischen Wert in den festgelegten Größen zu ändern. Verwenden Sie dieses Steuerelement für alle numerische Felder oder Geldfelder. Benutzer können auch eine Zahl direkt in das Feld eingeben. Dieses Feld wird nur im Bearbeitungsmodus unterstützt.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Schritt|Legen Sie den Betrag fest, der zum aktuellen Wert addiert oder davon subtrahiert werden soll, wenn Daten mithilfe dieses Steuerelements eingegeben werden.|  
|Feld|Zeigt das Feld an, dem das Steuerelement zugeordnet ist.|  
  
## <a name="input-mask"></a>Eingabemaske  
 Über das Steuerelement Eingabemaske legen Sie die Formatierung für Felder wie "Telefonnummer" oder "Kreditkarte" fest, um die Eingabe ungültiger Daten zu verhindern. Wenn Sie z. B. möchten, dass Benutzer eine Telefonnummer in den USA im Format +1-222-555-1011 eingeben, verwenden Sie die Eingabemaske +1-000-000-0000.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Maske|Geben Sie die Maske ein, die für die Überprüfung von Benutzerdaten verwendet wird. Sie können eine Kombination aus folgenden Zeichen für die Maske verwenden:<br /><br /> 0 – Ziffer<br /><br /> 9 – Zahl oder Leerzeichen<br /><br /> # – Zahl, Zeichen oder Leerzeichen<br /><br /> B – Buchstabe<br /><br /> I - Buchstabe oder Leerzeichen<br /><br /> A - Alphanumerisch<br /><br /> A - Alphanumerisch oder Leerzeichen<br /><br /> < – Konvertiert Zeichen, die auf Kleinbuchstaben folgen<br /><br /> > - Konvertiert Zeichen, die auf Großbuchstaben folgen<br /><br /> &#124;– Deaktiviert Anfrageumwandlung<br /><br /> \ - Markiert jedes Zeichen und wandelt es in ein Literal<br /><br /> Alle anderen - Literale|  
|Feld|Zeigt das Feld an, dem das Steuerelement zugeordnet ist.|  
  
## <a name="linear-gauge"></a>Lineares Messgerät  
 Mit dem linearen Messgerät können Ihre Benutzer Zahlenwerte eingeben, indem sie einen Schieberegler nutzen und nicht die genaue Menge eingeben. Der Regler ermöglicht nur die Eingabe und Anzeige ganzer Zahlen. Verwenden Sie dieses Steuerelement für alle numerische Felder oder Geldfelder.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Max.|Festlegen des maximalen Werts für die Anzeige auf dem Messgerät.|  
|Min.|Festlegen des minimalen Werts für die Anzeige auf dem Messgerät.|  
|Wert|Rufen Sie den Wert für die Anzeige auf dem Messgerät ab oder legen Sie ihn fest.|  
|Schritt|Legen Sie den Betrag fest, der zum aktuellen Wert addiert oder davon subtrahiert werden soll, wenn Daten mithilfe dieses Steuerelements eingegeben werden.|  
  
## <a name="arc-knob"></a>Bogen-Knopf  
 Der Bogen-Knopf stellt eine Möglichkeit zur Verfügung, damit Benutzer Daten eingeben, indem sie den Regler verschieben, er wird auf dem Bildschirm als Bogen angezeigt. Der Bogen-Knopf bietet nur Eingabe und Anzeige ganzer Zahlen. Verwenden Sie dieses Steuerelement für alle numerische Felder oder Geldfelder. Sie können Touch verwenden, um den Wert zu ändern, oder Sie können einfach das Tastenfeld verwenden, um auf die Zahl zu fokussieren und sie zu bearbeiten.  
  
> [!NOTE]
> Dieses Steuerelement wird auf Android 4.2- und 4.3-Geräten nicht unterstützt. Es wirkt sich auf die Bildlauferfahrung in diesen Versionen aus.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Max.|Festlegen des maximalen Werts für die Anzeige auf dem Messgerät.|  
|Min.|Festlegen des minimalen Werts für die Anzeige auf dem Messgerät.|  
|Wert|Rufen Sie den Wert für die Anzeige auf dem Messgerät ab oder legen Sie ihn fest.|  
|Schritt|Legen Sie den Betrag fest, der zum aktuellen Wert addiert oder davon subtrahiert werden soll, wenn Daten mithilfe dieses Steuerelements eingegeben werden.|  
  
## <a name="next-steps"></a>Nächste Schritte
[Anleitung: Verwenden benutzerdefinierter Steuerelemente für Datenvisualisierungen](use-custom-controls-data-visualizations.md)
