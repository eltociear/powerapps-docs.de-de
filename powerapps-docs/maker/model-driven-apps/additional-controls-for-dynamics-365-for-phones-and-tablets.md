---
title: Zusätzliche Steuerelemente für Dynamics 365 für Smartphones und Tablets | Microsoft-Dokumentation
description: Eine Liste der für die Verwendung mit Dynamics 365 für Smartphones und Tablets verfügbaren Steuerelemente
ms.custom: ''
ms.date: 06/18/2018
ms.reviewer: ''
ms.service: crm-online
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
ms.openlocfilehash: d6293f1fc0913a7e2f66e3830702458e3249f0f0
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39683090"
---
# <a name="additional-controls-for-dynamics-365-for-phones-and-tablets"></a>Zusätzliche Steuerelemente für Dynamics 365 für Smartphones und Tablets 

 Sie können einen umfangreichen Satz von zusätzlichen Steuerelementen verwenden, um eine für die Toucheingabe optimierte Benutzeroberfläche für Dynamics 365 für Smartphones und Tablets zu erstellen. Dazu gehören Schieberegler, Schalter, Multimediaplayer, Eingabemasken, Kalender und andere Steuerelemente.  

 
> [!NOTE]
>  Sie können diese zusätzlichen Steuerelemente nur mit mobilen Apps verwenden. In der Web-App werden sie nicht unterstützt.  
  
 So verwenden Sie diese Steuerelemente im Formular-Editor:  
  
1.  Doppelklicken Sie auf das Feld oder die Liste, wo Sie das Steuerelement hinzufügen möchten.  
  
2.  Klicken Sie auf die Registerkarte **Steuerelemente**.  
  
3.  Klicken Sie auf **Steuerelement hinzufügen**.  
  
4.  Wählen Sie das gewünschte Steuerelement aus, und klicken Sie dann auf **Hinzufügen**.  
  
    > [!NOTE]
    >  Je nach Feld- oder Listentyp sind verschiedene Steuerelemente verfügbar. Schieberegler-Steuerelemente sind z.B. vielleicht nur für numerische oder Geldfelder verfügbar und das Kalendersteuerelement nur für Listen.  
  
5.  Wählen Sie die Geräte aus, auf denen das Steuerelement angezeigt werden soll (Smartphone, Tablet oder beides). Steuerelemente sind für Smartphone-Kopfzeilenfelder nicht verfügbar.  
  
6.  Konfigurieren Sie die Werte für jede Eigenschaft.  
  
7.  Klicken Sie auf **OK**, wenn Sie das Steuerelement konfiguriert haben.  
  
 Es folgen Beschreibungen für jedes Steuerelement, das Sie in Formularen für Dynamics 365 für Smartphones und Tablets verwenden können.  
  
## <a name="calendar-control"></a>Kalendersteuerelement  
 Konfigurieren Sie mit diesem Steuerelement Formulare, damit sie in Dynamics 365 für Smartphones und Tablets als Kalenderansicht angezeigt werden. Sie können mit diesem Steuerelement auch Dashboards, Listen oder Entitätsraster für Smartphones und Tablets ersetzen.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Startdatum|Definieren Sie Startdatum und -uhrzeit des Elements, das in der Kalenderansicht visualisiert werden soll. Die verfügbaren Werte sind beliebige Spalten in dieser Ansicht des Datumstyps.|  
|Enddatum|Definieren Sie Enddatum und -uhrzeit des Elements, das in der Kalenderansicht visualisiert werden soll. Die verfügbaren Werte sind beliebige Spalten in dieser Ansicht des Datumstyps.|  
|Dauer|Die Dauer in Minuten. Wenn Sie einen Wert für „Enddatum“ angeben, wird „Dauer“ ignoriert.|  
|Beschreibung|Dies ist die gewünschte Beschriftung für Kalenderelemente.|  
  
 Die angezeigte Mindestdauer im Kalender beträgt 30 Minuten. Elemente mit einer Dauer von weniger als 30 Minuten werden dennoch mit 30 Minuten angezeigt.  
  
 Das Kalendersteuerelement unterstützt alle Datumsvarianten („Lokaler Benutzer“, „Nur Datum“ und „Zeitzonenunabhängig“).  
  
## <a name="timeline-control"></a>Zeitachsensteuerelement  
 Stellen Sie eine Zeitachse mit aktuellen, relevanten neuen Artikeln und Twitter-Tweets für ein Konto bereit.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|CC_Timeline_Title|Eigenschaft, die dem Titel jedes Zeitachsenelements zugeordnet werden soll.|  
|CC_Timeline_Title_Desc|Beschreibung des Titels.|  
|CC_Timeline_Label1|Feld, das unter dem Titel des Zeitachsenelements angezeigt werden soll.|  
|CC_Timeline_Label1_Desc|Beschreibung für Beschriftung 1.|  
|CC_Timeline_Label2|Feld, das nach Label 1 angezeigt werden soll.|  
|CC_Timeline_Label2_Desc|Beschreibung für Beschriftung 2.|  
|CC_Timeline_Label3|Feld, das nach Beschriftung 2 angezeigt werden soll.|  
|CC_Timeline_Label3_Desc|Beschreibung für Beschriftung 3.|  
|CC_Timeline_Label4|Feld, das nach Beschriftung 3 angezeigt werden soll.|  
|CC_Timeline_Label4_Desc|Beschreibung für Beschriftung 4.|  
|CC_Timeline_Label5|Feld, das nach Beschriftung 4 angezeigt werden soll.|  
|CC_Timeline_Label5_Desc|Beschreibung für Beschriftung 5.|  
|CC_Timeline_Timestamp|Feld zum Sortieren der Zeitachse in umgekehrter chronologischer Reihenfolge.|  
|CC_Timeline_Timestamp_Desc|Beschreibung des Zeitstempels.|  
|CC_Timeline_Group|Feld, das zum Gruppieren der Zeitachse zugeordnet wird.|  
|CC_Timeline_Group_Desc|Beschreibung für Gruppenfeld.|  
|CC_Timeline_GroupOrder|Position der Gruppe, zu der das Element gehört, relativ zu anderen Gruppen (die Werte 1, 2, 3 usw. werden den anzuzeigenden Gruppen zugewiesen). Die Gruppen werden in aufsteigender Folge gemäß der zugewiesenen Gruppenwerte angezeigt.|  
|CC_Timeline_GroupOrder_Desc|Beschreibung für Gruppenreihenfolge-Feld.|  
|CC_Timeline_URL|URL-Feld, das zum Anzeigen der URL jedes Zeitachsenelements zugeordnet wird.|  
|CC_Timeline_URL_Desc|Beschreibung für URL-Feld.|  
|CC_Timeline_ThumbnailURL|Zuzuweisendes Feld für Miniaturansicht des Bilds/Symbols, das für jedes Element angezeigt wird.|  
|CC_Timeline_ThumnailURL_Desc|Beschreibung des `ThumbnailURL`-Felds.|  
|CC_Timeline_Filter|Zuzuweisendes Feld für Zeitachsenfilter.|  
|CC_Timeline_Filter_Desc|Beschreibung für Filter.|  
|CC_Timeline_Footer|Webressource, die als Fußzeile der Zeitachse angezeigt werden soll.|  
|CC_Timeline_Footer_Desc|Beschreibung für Fußzeilenfeld.|  
  
## <a name="linear-slider"></a>Linearer Schieberegler  
 Mit dem linearen Schieberegler-Steuerelement können die Benutzer Zahlenwerte über einen Schieberegler eingeben. Darüber hinaus ist die manuelle Eingabe der Menge möglich. Der Schieberegler ermöglicht nur die Eingabe und Anzeige ganzer Zahlen. Verwenden Sie dieses Steuerelement für alle numerischen Felder oder Geldfelder.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Max.|Festlegen des maximalen Anzeigewerts für den Schieberegler.|  
|Min|Festlegen des minimalen Anzeigewerts für den Schieberegler.|  
|Wert|Der Anzeigewert des Schiebereglers.|  
|Schritt|Legen Sie den Betrag fest, der zum aktuellen Wert addiert oder davon subtrahiert werden soll, wenn Daten mithilfe dieses Steuerelements eingegeben werden.|  
  
## <a name="option-sets"></a>Optionssätze  
 Das Optionssatz-Steuerelement stellt einen Satz von Optionen bereit, aus denen Benutzer beim Eingeben von Daten wählen können. Verwenden Sie dieses Steuerelement für Optionssätze mit nur zwei oder drei Optionen.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Feld|Zeigt das Feld an, dem das Steuerelement zugeordnet ist.|  
  
## <a name="flip-switch"></a>Kippschalter  
 Der Kippschalter entspricht einem Ein-/Ausschalter, der eine Auswahl zwischen zwei Werten ermöglicht.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Feld|Zeigt das Feld an, dem das Steuerelement zugeordnet ist.|  
  
## <a name="star-rating"></a>Bewertungssterne  
 Verwenden Sie die Bewertungssterne als visuelle Darstellung der Bewertung. Sie können maximal fünf Sterne festlegen. Sie können dieses Steuerelement nur für ganze Zahlen verwenden, denn es kann keine Dezimalwerte akzeptieren.  
  
> [!NOTE]
>  Wählen Sie für dieses Steuerelement unbedingt die Option **Im Web ausblenden** aus.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Max.|Wählen Sie die maximale Anzahl von Sternen für das Steuerelement in der Dropdownliste aus.|  
  
## <a name="radial-knob"></a>Radial-Knopf  
 Mit dem Radial-Knopf können Benutzer Daten durch Bewegen des Knopfs eingeben, der auf dem Bildschirm als Kreis angezeigt wird. Der Radial-Knopf ermöglicht nur die Eingabe und Anzeige ganzer Zahlen. Verwenden Sie dieses Steuerelement für alle numerischen Felder oder Geldfelder. Sie können den Wert durch Toucheingabe ändern oder mit der Zehnertastatur den Fokus auf die Zahl legen und sie bearbeiten.  
  
> [!NOTE]
>  Dieses Steuerelement wird auf Android 4.2- und 4.3-Geräten nicht unterstützt. Es beeinträchtigt die Scrollfunktion in diesen Versionen.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Max.|Legen Sie den maximalen Anzeigewert für das Messgerät fest.|  
|Min|Legen Sie den minimalen Anzeigewert für das Messgerät fest.|  
|Wert|Rufen Sie den Anzeigewert für das Messgerät ab, bzw. legen Sie ihn fest.|  
|Schritt|Legen Sie den Betrag fest, der zum aktuellen Wert addiert oder davon subtrahiert werden soll, wenn Daten mithilfe dieses Steuerelements eingegeben werden.|  
  
## <a name="website-preview"></a>Websitevorschau  
 Ordnen Sie mit dem Websitevorschau-Steuerelement ein URL-Feld zu, und zeigen Sie eine Vorschau der Website an.  
  
> [!IMPORTANT]
>  Durch Aktivieren dieses Steuerelements erlauben Sie Ihren Benutzern die Freigabe bestimmter identifizierbarer Geräteinformationen für ein externes System. Aus externen Systemen in eine PowerApps-App oder in Dynamics 365 Customer Engagement importierte Daten unterliegen unseren Datenschutzbestimmungen gemäß der [Datenschutzerklärung von Microsoft](http://go.microsoft.com/fwlink/p/?LinkId=521839).  
>   
>  [Datenschutzhinweise](use-the-form-editor-legacy.md#BKMK_PrivacyNotices)  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Feld|Zeigt das Feld an, dem das Steuerelement zugeordnet ist.|  
  
## <a name="bullet-graph"></a>Bullet Chart  
 Das Bullet Chart-Steuerelement zeigt eine einzelne wichtige Kennzahl mit einer vergleichbaren Kennzahl und qualitativen Bereichen an, um unmittelbar zu signalisieren. ob die Kennzahl gut oder schlecht ist oder einen anderen Status hat. Verwenden Sie dieses Steuerelement für alle numerischen Felder oder Geldfelder in Dashboards. Beispielsweise können Sie den Wert dem tatsächlichen Umsatz zuordnen und das Ziel dem geschätzten Umsatz, um den tatsächlichen und den geschätzten Umsatz grafisch darzustellen.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Max.|Legen Sie den maximalen Anzeigewert für das Diagramm fest.|  
|Min|Legen Sie den minimalen Anzeigewert für das Diagramm fest.|  
|In Ordnung|Legen Sie einen Wert fest, der für die Kennzahl als gut angesehen wird (optional).|  
|Schlecht|Legen Sie einen Wert fest, der für die Kennzahl als schlecht angesehen wird (optional).|  
|Wert|Zeigt das Feld an, dem das Steuerelement zugeordnet ist.|  
|Ziel|Ordnen Sie dies dem Feld zu, mit dem Sie den Wert vergleichen möchten. Wenn **Wert** z.B. dem **tatsächlichen Umsatz** zugeordnet ist, können Sie **Ziel** dem **Geschätzten Umsatz** zuordnen oder einen statischen Wert angeben.|  
  
## <a name="pen-control"></a>Stiftsteuerelement  
 Verwenden Sie das Stiftsteuerelement, um geschriebene Eingaben wie z.B. Unterschriften zu erfassen.  
  
> [!NOTE]
>  Die empfohlene minimale **Maximallänge** für das Feld, dem dieses Steuerelement zugeordnet ist, beträgt 15.000.  
>   
>  Wählen Sie für dieses Steuerelement unbedingt die Option **Im Web ausblenden** aus.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|PenMode|Geben Sie **PenMode!Zeichnen**, **PenMode!Löschen** oder **PenMode!Auswählen** an, um zu bestimmen, was geschieht, wenn ein Benutzer ein Zeigegerät in ein Stiftsteuerelement zieht.|  
  
## <a name="auto-complete"></a>Automatische Vervollständigung  
 Das Steuerelement zur automatischen Vervollständigung filtert eine Elementliste während der Eingabe und ermöglicht Ihnen die Auswahl eines Werts aus der Dropdownliste. Mit diesem Steuerelement können Sie Benutzern z.B. die Auswahl aus einer Dropdownliste mit Staaten oder Ländern/Regionen erlauben. Dieses Steuerelement wird einem Feld des Typs **Einzelne Textzeile** zugeordnet.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Feld|Zeigt das Feld an, dem das Steuerelement zugeordnet ist.|  
|Quelle|Legen Sie die Quelle für die Daten (Gruppierte Optionen, Optionssatz oder Ansicht) fest.|  
|Optionssatz|Wählen Sie den Optionssatz für dieses Feld aus.|  
|Anzeigen|Wählen Sie die Entität und Ansicht für dieses Feld aus.|  
|Feld|Wählen Sie das Feld der primären Entität der Ansicht aus, die als Datenquelle verwendet wird.|  
  
## <a name="multimedia"></a>Multimedia  
 Sie können Videos einbetten, um eine bessere Benutzerzufriedenheit bei Verkaufs- und Außendienstmitarbeitern zu erreichen. Verwenden Sie dieses Steuerelement, um ein URL-Feld zuzuordnen, das den Audio- oder Videolink zur Wiedergabe im Steuerelement enthält.  
  
> [!NOTE]
>  Dieses Steuerelement wird von Android-Versionen ab 4.4 unterstützt.  
>   
>  YouTube-Videos werden derzeit auf Windows 8- und Windows 8.1-Tablets und -Smartphones nicht unterstützt. Unter Windows 10 werden nur HTTPS-Videos (einschließlich YouTube) unterstützt.  
  
 Zu den unterstützten Medientypen zählen:  
  
-   Streaming von MP4-Dateien  
  
-   YouTube-Videos  
  
-   Azure-Medien  
  
-   Azure-Datenströme  
  
 [Hinweis zum Datenschutz](use-the-form-editor-legacy.md#BKMK_PrivacyNotices)  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Medien|Geben Sie die URL des in diesem Steuerelement wiederzugebenden Mediums ein.|  
  
## <a name="number-input"></a>Zahleneingabe  
 Ermöglichen Sie mit dem Steuerelement zur Zahleneingabe Benutzern eine schnelle Dateneingabe. Benutzer müssen nur auf die Plus- und Minusschaltfläche tippen, um einen numerischen Wert in den von Ihnen festgelegten Schritten zu ändern. Verwenden Sie dieses Steuerelement für alle numerischen Felder oder Geldfelder. Benutzer können eine Zahl auch direkt in das Feld eingeben. Dieses Feld wird nur im Bearbeitungsmodus unterstützt.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Schritt|Legen Sie den Betrag fest, der zum aktuellen Wert addiert oder davon subtrahiert werden soll, wenn Daten mithilfe dieses Steuerelements eingegeben werden.|  
|Feld|Zeigt das Feld an, dem das Steuerelement zugeordnet ist.|  
  
## <a name="input-mask"></a>Eingabeformat  
 Über das Eingabeformat-Steuerelement legen Sie die Formatierung für Felder wie „Telefonnummer“ oder „Kreditkarte“ fest, um die Eingabe ungültiger Daten zu verhindern. Wenn Sie beispielsweise wünschen, dass Benutzer eine USA-Telefonnummer im Format „+1-222-555-1011“ eingeben, verwenden Sie das Eingabeformat „+1-000-000-0000“.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Maske|Geben Sie die Maske für die Validierung von Daten während der Eingabe durch den Benutzer ein. Sie können eine Kombination der folgenden Zeichen für die Maske verwenden:<br /><br /> 0 – Ziffer<br /><br /> 9 – Ziffer oder Leerzeichen<br /><br /> # – Ziffer, Vorzeichen oder Leerzeichen<br /><br /> L – Buchstabe<br /><br /> I – Buchstabe oder Leerzeichen<br /><br /> A – alphanumerisches Zeichen<br /><br /> A – alphanumerisches Zeichen oder Leerzeichen<br /><br /> < – folgende Zeichen werden in Kleinbuchstaben konvertiert<br /><br /> > – folgende Zeichen werden in Großbuchstaben konvertiert<br /><br /> &#124; – deaktiviert die Konvertierung der Groß-/Kleinschreibung<br /><br /> \ – Escapezeichen vor einem Zeichen, um es in ein Literal umzuwandeln<br /><br /> Alle anderen – Literale|  
|Feld|Zeigt das Feld an, dem das Steuerelement zugeordnet ist.|  
  
## <a name="linear-gauge"></a>Linearmessgerät  
 Mit dem Linearmessgerät können Ihre Benutzer numerische Werte durch Ziehen eines Schiebereglers statt genauer Zahleneingabe eingeben. Der Schieberegler ermöglicht nur die Eingabe und Anzeige ganzer Zahlen. Verwenden Sie dieses Steuerelement für alle numerischen Felder oder Geldfelder.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Max.|Legen Sie den maximalen Anzeigewert für das Messgerät fest.|  
|Min|Legen Sie den minimalen Anzeigewert für das Messgerät fest.|  
|Wert|Rufen Sie den Anzeigewert für das Messgerät ab, bzw. legen Sie ihn fest.|  
|Schritt|Legen Sie den Betrag fest, der zum aktuellen Wert addiert oder davon subtrahiert werden soll, wenn Daten mithilfe dieses Steuerelements eingegeben werden.|  
  
## <a name="arc-knob"></a>Bogen-Knopf  
 Mit dem Bogen-Knopf können Benutzer Daten durch Bewegen des Knopfs eingeben, der auf dem Bildschirm als Bogen angezeigt wird. Der Bogen-Knopf ermöglicht nur die Eingabe und Anzeige ganzer Zahlen. Verwenden Sie dieses Steuerelement für alle numerischen Felder oder Geldfelder. Sie können den Wert durch Toucheingabe ändern oder mit der Zehnertastatur den Fokus auf die Zahl legen und sie bearbeiten.  
  
> [!NOTE]
> Dieses Steuerelement wird auf Android 4.2- und 4.3-Geräten nicht unterstützt. Es beeinträchtigt die Scrollfunktion in diesen Versionen.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Max.|Legen Sie den maximalen Anzeigewert für das Messgerät fest.|  
|Min|Legen Sie den minimalen Anzeigewert für das Messgerät fest.|  
|Wert|Rufen Sie den Anzeigewert für das Messgerät ab, bzw. legen Sie ihn fest.|  
|Schritt|Legen Sie den Betrag fest, der zum aktuellen Wert addiert oder davon subtrahiert werden soll, wenn Daten mithilfe dieses Steuerelements eingegeben werden.|  
  
## <a name="next-steps"></a>Nächste Schritte
[Tutorial: Verwenden von benutzerdefinierten Steuerelementen für Datenvisualisierungen](use-custom-controls-data-visualizations.md)