---
title: Häufige Probleme und Lösungen für powerapps | Microsoft-Dokumentation
description: Eine Liste häufiger Probleme und Lösungen für PowerApps.
author: KumarVivek
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 08/21/2019
ms.author: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c8f05c74141301d0c41238daa20625874eec98aa
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678785"
---
# <a name="common-issues-and-resolutions-for-powerapps"></a>Häufige Probleme und Lösungen für PowerApps

In diesem Artikel werden einige häufige Probleme aufgelistet, die bei der Verwendung von powerapps auftreten können. Nach Möglichkeit werden Problemumgehungen bereitgestellt.

1. **Anmelde Problem auf bestimmten mobilen Android-Geräten bei Verwendung des Authentifikators** (21. August 2019)

    In bestimmten Geräten und Szenarien können bei der Verwendung von Authenticator Anmeldefehler auftreten. Dies ist darauf zurückzuführen, dass OEM diese Funktionalität einschränkt. Weitere Informationen zum Fehler und zu möglichen entschärfungen finden Sie [hier](https://github.com/AzureAD/azure-activedirectory-library-for-android/wiki/ADALError:-BROKER_AUTHENTICATOR_NOT_RESPONDING).    

1. **Kamera Problem auf mobilen Android-Geräten** (Jan. 1, 2019)

    Wenn das Kamera Steuerelement nicht mehr auf einem Android-Gerät funktioniert, veröffentlichen Sie die APP erneut, und öffnen Sie Sie auf dem Gerät erneut. Das Kamera Steuerelement wurde als Reaktion auf eine Änderung im Android-Betriebssystem aktualisiert, und Ihre APP profitiert von der Aktualisierung, wenn Sie Sie erneut veröffentlichen.

1. **Scrollen in flexiblen Galerien** (Nov. 27, 2018)

    Wenn beim Scrollen mit dem Finger eine Einschränkung angezeigt wird, heben Sie die Übertragung auf, und starten Sie den Bildlauf erneut.

1. Das **Zeichnen mit Maus-oder Finger Eingaben ist in Power Apps für Windows nicht reibungslos** (Sep. 24, 2018).

    Das Pen-Steuerelement verfügt nur über partielle Unterstützung für das Zeichnen mithilfe von Maus-oder Finger Eingaben in der Windows-App Striche können zeitweilig sein. Verwenden Sie für Smooth Drawing einen Stift, oder führen Sie die app in einem Browser aus.

1. **Mehrere mediensteuer Elemente in Power Apps Mobile** (Aug. 2, 2018)

    Powerapps Mobile kann auf verschiedenen Arten von Geräten ausgeführt werden, und einige von Ihnen weisen Einschränkungen auf, die für diese Plattform spezifisch sind:

    - Mit Ausnahme von iPhone-Geräten können Sie Videos auf allen Plattformen in mehreren **Video**-Steuerelementen gleichzeitig abspielen.
    - Mit Ausnahme des Webplayers können Sie auf allen Plattformen Audio mit mehreren **Microphone**-Steuerelementen gleichzeitig aufzeichnen.

1. **Erneutes Veröffentlichen von Apps** (2. August 2018)

    Wenn Sie Ihre APP in mehreren Monaten nicht aktualisiert haben, veröffentlichen Sie Sie erneut, um Sie mit der neuesten Version von powerapps zu synchronisieren, die Leistungsverbesserungen und andere Korrekturen umfasst.

1. <a name="out-of-memory"></a>**Browser hat nicht genügend Arbeitsspeicher** (23. Juli 2018)

    Wenn bei der Verwendung von powerapps nicht genügend Arbeitsspeicher verfügbar ist, sollten Sie eine 64-Bit-Version von Chrome, Microsoft Edge oder Internet Explorer herunterladen.

1. **Starten einer Website aus einer eingebetteten App** (10. Mai 2018)

    Internet Explorer und Microsoft Edge blockieren möglicherweise den Aufruf einer URL oder Website, die sich im geschützten Modus oder in einer niedrigeren Sicherheitszone als die Website befindet, in der die App geladen wurde. Um dieses Problem zu lösen, [ändern Sie die Sicherheits- und Datenschutzeinstellungen](https://support.microsoft.com/help/17479/windows-internet-explorer-11-change-security-privacy-settings) für Ihren Browser.

1. **Kombinationsfeld-Steuerelemente in Katalogen** (3. Mai 2018)

    Wenn Sie ein Steuerelement des Typs **Kombinationsfeld** innerhalb eines Katalogs verwenden, werden die ausgewählten Optionen nicht beibehalten, sobald der Benutzer durch den Katalog scrollt. Dies ist kein Problem, wenn Sie ein Steuerelement des Typs **Kombinationsfeld** in einem Katalog verwenden, der Scrollen nicht unterstützt. Eine Problemumgehung ist derzeit nicht verfügbar.

1. **Verwenden eines benutzerdefinierten Bilds als App-Symbol** (11. April 2018)

    In powerapps Studio für Windows, Version 3,18043, können Sie kein benutzerdefiniertes Image hochladen, das als App-Symbol verwendet werden soll. Um dieses Problem zu umgehen, verwenden Sie [powerapps Studio für Web](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) , um ein benutzerdefiniertes Image hochzuladen. Alternativ dazu können Sie auch eines der Symbole verwenden, das in Power apps Studio für Windows enthalten ist, und die Hintergrundfarbe anpassen.

1. **Kopieren und Einfügen von Anzeigen über mehrere Apps hinweg** (4. April 2018)

    Das Kopieren und Einfügen von Anzeigen über mehrere Apps wird derzeit nicht unterstützt. Wenn Sie dieses Problem umgehen möchten, fügen Sie eine neue Anzeige zu Ihrer Ziel-App hinzu, kopieren Sie die Steuerelemente aus der Anzeige in die Quell-App, und fügen Sie sie in die Anzeige Ihrer Ziel-App ein.

1. **Ändern des Layouts von SharePoint-Formularen** (7. März 2018)

    Wenn Sie in bestimmten Sprachen ein Formular in einer SharePoint-Liste anpassen und versuchen, das Layout vom Hochformat (Standard) in das Querformat zu ändern, werden in der App möglicherweise mehrere Fehler angezeigt (gelbe Dreiecke in Steuerelementen). Um diese Fehler zu beheben und das Layout mit Querformat zu erhalten, klicken Sie auf **Rückgängig**.

1. **Data Table-Steuerelement**

    Wenn Sie ein **Data Table**-Steuerelement kopieren und einfügen, für das die **Items**-Eigenschaft auf eine Formel mit einer **Filter**-Funktion festgelegt wurde, enthalten die Feldnamen in der Formel für die **Items**-Eigenschaft im neuen **Data Table**-Steuerelement das Suffix **_1**. Hierdurch werden die Feldnamen ungültig, und es werden keine Daten in der Datentabelle angezeigt. Um dieses Problem zu umgehen, überprüfen Sie vor dem Kopieren des Steuerelements, dass die **Filter**-Funktion nicht auf ein Feld in der Datenquelle verweist, dessen Name dem Namen einer Spalte im **Data Table**-Steuerelement entspricht. Wenn es der Fall ist, benennen Sie die Spalte im **Data Table**-Steuerelement um. Alternativ können Sie das Suffix **_1** aus den ungültigen Feldnamen entfernen, damit sie den Namen in der Entität entsprechen.

1. **Kamera Steuerelemente in powerapps Studio für Windows**

    Powerapps Studio für Windows stürzt möglicherweise ab, wenn Sie ein Kamera Steuerelement hinzufügen oder eine APP öffnen, die ein Kamera Steuerelement verwendet. Um dieses Problem zu vermeiden, verwenden Sie [powerapps Studio für Web](create-app-browser.md) , wenn Sie ein Kamera Steuerelement hinzufügen oder verwenden.

1. **Version 2.0.700 auf Android-Geräten**

    Wenn Sie Release 2.0.700 auf einem Android-Gerät installieren und dann keine apps öffnen können (oder eine APP nicht mehr reagiert), deinstallieren Sie Power apps, starten Sie das Gerät neu, und installieren Sie dann powerapps neu.

1. **„Leerer“ Katalog beim Öffnen einer App**

    Wenn Sie automatisch eine App auf der Grundlage von Daten erstellen, die App speichern und anschließend wieder öffnen, werden im durchsuchbaren Katalog möglicherweise nicht sofort Daten angezeigt. Geben Sie zum Beheben dieses Problems mindestens ein Zeichen im Suchfeld ein, und löschen Sie dann den eingegebenen Text. Im Katalog werden nun ordnungsgemäß die Daten angezeigt.

1. **Aktualisieren von powerapps auf Windows 8.1**

    Wenn Sie powerapps auf einem Computer installieren, auf dem Windows 8 oder Windows 8.1 ausgeführt wird, lassen Sie die Windows Store-App geöffnet und aktiv, verwenden Sie den Charm "Einstellungen", um nach Updates zu suchen, und installieren Sie Sie.

1. **Benutzerdefinierte Connectors und der Common Data Service**

    Wenn eine mit Power apps Build 2.0.540 oder früher erstellte App auf einer Datenbank im Common Data Service und mindestens einem benutzerdefinierten Connector in einer anderen Umgebung basiert, müssen Sie den Connector in der gleichen Umgebung wie die Datenbank bereitstellen und die APP so aktualisieren, dass Sie verwendet wird. e neuer Connector. Andernfalls teilt ein Dialogfeld Benutzern mit, dass die API nicht gefunden wurde. Weitere Informationen finden Sie in der [Übersicht zu Umgebungen](../../administrator/environments-overview.md).

1. **Ausführen einer App unter Windows 8.1**

    Wenn Sie [dieses Update für Windows 8.1](https://technet.microsoft.com/library/security/ms16-118)installieren, können Sie keine apps ausführen, die Sie in powerapps Studio auf diesem Betriebssystem öffnen. Sie können jedoch weiterhin apps ausführen, die Sie in [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) oder mithilfe von powerapps Mobile öffnen.

1. **Spaltennamen mit Leerzeichen**

    Wenn Sie eine SharePoint-Liste oder Excel-Tabelle verwenden, in der ein Spaltenname ein Leerzeichen enthält, wird diese von powerapps durch **"\_x0020\_"** ersetzt. Beispielsweise wird **"Spalten Name"** in SharePoint oder Excel in powerapps als **"Column_x0020_Name"** angezeigt, wenn Sie im Datenlayout angezeigt oder in einer Formel verwendet werden.

1. **Ändern eines Flows in einer freigegebenen Anwendung**

    Wenn Sie einer App einen Flow hinzufügen, sie freigeben und dann einen Dienst hinzufügen oder eine Verbindung im Flow ändern, müssen Sie den Flow aus der freigegebenen App entfernen, den Flow erneut hinzufügen und die App erneut freigeben. Andernfalls empfangen Benutzer, die den Flow auslösen, einen Authentifizierungsfehler.

1. **Verwenden einer lokalisierten Version**.

    Wenn Sie Version 2.0.531 unter Windows 8.1 ausführen, können Sie in einem **Texteingabe**-Steuerelement keine Eingaben vornehmen, wenn das Gerät auf eine Sprache eingestellt ist, für die ein IME-Fenster erforderlich ist.

1. **Kamerasteuerelement eines Windows Phones**

    Eine Anwendung, die ein Kamerasteuerelement enthält, stürzt möglicherweise ab, wenn Sie die App auf einem Windows Phone öffnen, das Build 10.0.10586.107 ausführt. Führen Sie zur Vermeidung dieses Problems ein Upgrade auf den aktuellen Build aus (etwa, indem Sie den [Aktualisierungsratgeber](https://www.microsoft.com/store/p/upgrade-advisor/9nblggh0f5g4) ausführen).

1. **Öffnen einer App aus einer Vorlage**

    Wenn Sie das Release 2.0.500 oder ein früheres ausführen, wird eine Fehlermeldung angezeigt, wenn Sie versuchen, eine App aus einer Vorlage zu erstellen. Sie müssen ein Upgrade durchführen, um diese Funktion verwenden zu können.

    Wenn Sie das Release 2.0.510 oder ein späteres ausführen, wird möglicherweise eine Warnung angezeigt, wenn Sie versuchen, eine App aus einer Vorlage zu erstellen. Sie können die Meldung jedoch schließen und die App erstellen.

1. **Scannen eines Barcodes**

    Informationen zu Beschränkungen und bewährten Methoden beim Verwenden eines **Barcode**-Steuerelements finden Sie unter [Scan a barcode (Scannen eines Barcodes)](scan-barcode.md).

1. **Erstellen und Bearbeiten von Apps in einem Browser**

    Sie können in Power apps Studio für Windows viele, aber nicht alle gleichen Dinge tun wie in Power apps Studio für Windows. Weitere Informationen finden Sie unter [Create or edit apps in a browser (Erstellen oder Bearbeiten von Apps in einem Browser)](create-app-browser.md).

1. **Ändern eines Titelfelds in einer Entität**

    Wenn Sie das Titelfeld für eine Entität ändern, auf die andere Entitäten über mindestens ein Nachschlagefeld verweisen, tritt ein Fehler auf, wenn Sie versuchen, die Änderung zu speichern. Um dieses Problem zu umgehen, entfernen Sie alle Nachschlagefelder für die Entität, bei der Sie das Titelfeld ändern möchten, nehmen Sie die Änderung vor, und erstellen Sie die Nachschlagefelder erneut. Weitere Informationen zu Nachschlagefeldern finden Sie unter [Erstellen einer Beziehung zwischen Entitäten](../common-data-service/data-platform-entity-lookup.md).

1. **Apps, die eine Verbindung mit lokalem SharePoint herstellen**

    Wenn Sie eine App freigeben, die auf Verbindungen beruht, die nicht automatisch freigegeben werden (z.B. eine lokale SharePoint-Website), wird Benutzern, die die App in einem Browser öffnen, ein Dialogfeld ohne Text angezeigt, wenn Sie auf **Anmelden** klicken oder tippen. Klicken oder tippen Sie auf das „Schließen“-Symbol (X) in der rechten oberen Ecke, um das Dialogfeld zu schließen. Das Dialogfeld wird nicht angezeigt, wenn Sie die app in powerapps Studio oder powerapps Mobile öffnen. Weitere Informationen zu freigegebenen Verbindungen finden Sie unter [Share app resources (Freigeben von App-Ressourcen)](share-app-resources.md).

1. **Wenn Power apps eine APP aus Daten generiert, wird das für das Sortieren und suchen verwendete Feld nicht automatisch konfiguriert**.

   Um dieses Feld zu konfigurieren, bearbeiten Sie die **[Elemente](controls/properties-core.md)** -Formel für den Katalog, wie in den Abschnitten zum Filtern und Sortieren unter [Add a gallery (Hinzufügen eines Katalogs)](add-gallery.md) beschrieben.

1. **Bei Apps, die aus Daten erstellt werden, kann nur auf die ersten 500 Datensätze einer Datenquelle zugegriffen werden**.

     Im allgemeinen arbeitet Power apps mit jeder Größendaten Quelle, indem Vorgänge an die Datenquelle delegiert werden. Bei Vorgängen, die nicht delegiert werden können, gibt Power Apps bei der Erstellung eine Warnung aus und funktioniert nur für die ersten 500-Datensätze der Datenquelle.  Weitere Informationen zur Delegierung finden Sie im Artikel zur [Filterfunktion](functions/function-filter-lookup.md).

1. **Excel-Daten müssen als Tabelle formatiert sein**.

     Weitere Informationen zu Einschränkungen bei der Verwendung von Excel als Datenquelle finden Sie unter [Cloudspeicherverbindungen](connections/cloud-storage-blob-connections.md#known-limitations).

1. **Benutzerdefinierte SharePoint-Listen werden unterstützt, Bibliotheken jedoch nicht, bestimmte Typen von Listenspalten oder Spalten, die mehrere Werte oder Auswahlen unterstützen**.

     Weitere Informationen finden Sie unter [SharePoint Online](connections/connection-sharepoint-online.md#known-issues).

1. Die **gemeinsamen Erstellung wird nicht unterstützt. Einen Autor gleichzeitig, bitte**.

     Wenn mehr als eine Person zur gleichen Zeit die gleiche App bearbeitet, kann eine App beschädigt oder die Änderungen von Anderen überschrieben werden. Schließen Sie die App, bevor sie von einer anderen Person bearbeitet wird.

1. **Manchmal kann es einen Moment dauern, bis eine neu freigegebene App verwendet werden kann**.

     In einigen Fällen ist eine neu freigegebene App nicht sofort verfügbar. Warten Sie einige Minuten, und sie sollte verfügbar sein.

1. **Im [Formularsteuerelement](controls/control-form-detail.md), können Sie Daten nicht mithilfe einer benutzerdefinierten Karte ändern**.

     Der bestehenden benutzerdefinierten Karte fehlt die **[Update](controls/control-card.md)** -Eigenschaft, die für das Zurückschreiben von Änderungen benötigt wird. Dieses Problem können Sie folgendermaßen umgehen:

    * Wählen Sie das Formularsteuerelement aus, und fügen Sie eine Karte mithilfe des rechten Bereichs basierend auf dem Feld ein, das mit der Karte angezeigt werden soll.  
    * Entsperren Sie die Karte, wie unter [Understand data cards (Grundlegendes zu Datenkarten)](working-with-cards.md#unlock-a-card) beschrieben.
    * Entfernen Sie Steuerelemente, oder ordnen Sie diese passend neu an, so wie Sie es mit der benutzerdefinierten Karte machen würden.

1. **Eine App, die auf Android 5.0, Nexus 6 mit den WebView-Versionen 48 oder 49 ausgeführt wird, kann abstürzen**.

     Benutzer können dieses Problem beheben, indem Sie auf eine niedrigere Version von WebView (3x) oder auf Android 6.0 aktualisieren.

1. **Die Kameraverwendung kann vorübergehend deaktiviert sein, wenn der Speicherplatz gering ist**.

     Wenn der Speicherplatz Ihres mobilen Geräts gering ist, wird die Kamera vorübergehend deaktiviert, um zu verhindern, dass das Gerät abstürzt.

1. **Der Office 365-Video-Connector wird nicht unterstützt**.

1. **Der Kartenkatalog wird nicht mehr unterstützt**.

     Vorhandene Apps, die diese Funktion verwenden, werden vorerst weiter ausgeführt, Sie können jedoch keinen Kartenkatalog hinzufügen. Ersetzen Sie Kartenkataloge mit den neuen Steuerelementen **[Edit form](controls/control-form-detail.md)** (Formular bearbeiten) und **[Display form](controls/control-form-detail.md)** (Formular anzeigen).
