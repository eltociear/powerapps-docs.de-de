---
title: Skript-Webressourcenentwicklung mithilfe von Fiddler AutoResponder (modellgestützte Apps) | Microsoft Docs
description: Erfahren Sie, wie AutoResponder in Fiddler für lokales Debuggen von JavaScript-Webressourcen eingerichtet und verwendet wird.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5c2a4a12834cbaabbe9d44639b73025f2380c4dd
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2754559"
---
# <a name="script-web-resource-development-using-fiddler-autoresponder"></a>Skript-Webressourcenentwicklung unter Verwendung von Fiddler-AutoResponder

Während Sie JavaScript-Webressourcen entwickeln und debuggen, können Sie AutoResponder in [Telerik Fiddler](https://www.telerik.com/fiddler) verwenden, um den Inhalt einer Webressource mit Inhalt aus einer lokalen Datei ersetzen, anstatt diesen jedes Mal in Ihre modellgestützte App-Instanz hochzuladen und zu veröffentlichen. Verwenden Sie folgende Schritte unten, um AutoResponder in Fiddler einzurichten.

## <a name="install-and-configure-fiddler"></a>Fiddler installieren und konfigurieren

1. [Herunterladen](https://www.telerik.com/download/fiddler) und Installieren von Fiddler.
1. Öffnen Sie Fiddler, und von der Menüleiste aus wechseln Sie zu **Extras**, und wählen Sie dann **Optionen** aus.
2. Wählen Sie die Registerkarte **HTTPS** im Dialogfeld aus, und aktivieren Sie die Kontrollkästchen **HTTPS-VERBINDUNGEN erfassen** und **HTTPS-Datenverkehr entschlüsseln**, sodass der HTTPS-Datenverkehr erfasst und anschließend entschlüsselt wird.<br />
 ![Aktivieren Sie die markierten Kontrollkästchen in der Registerkarte HTTP](media/fiddler-https-options.png "SAktivieren Sie die markierten Kontrollkästchen in der Registerkarte HTTP)</br>
3. Klicken Sie auf **OK**, um das Dialogfeld zu schließen.

> [!NOTE]
> Wenn Sie zum ersten Mal diese Einstellung aktivieren, wird Fiddler Sie dazu auffordern, ein Zertifikat zu installieren. Installieren Sie das Zertifikat, und starten Sie Fiddler erneut, damit die neuen Einstellungen wirksam werden.<br />
> Wenn Sie Fiddler in der Vergangenheit ausgeführt haben und einen `NET::ERR_CERT_AUTHORITY_INVALID`-Fehler auf der Registerkarte **HTTPS** erhalten, klicken Sie auf die Schaltfläche **Aktionen**, und wählen Sie **Alle Zertifikate zurücksetzen** aus. Dadurch wird auch eine Anzahl von Aufforderungen zur Installation der neuen Zertifikate angezeigt.

## <a name="configure-autoresponder"></a>AutoResponder konfigurieren

1. Öffnen Sie die Seite in Ihrer Dynamics 365-Instanz, die Sie debuggen möchten.
2. Starten Sie die Fiddler-Ablaufverfolgungserfassung, indem Sie auf die Schaltfläche **Erfassung** in der unteren linken Ecke klicken.
   ![Klicken Sie auf die Schaltfläche „Erfassung”, um mit der Erfassung des HTTPS-Datenverkehrs zu beginnen](media/fiddler-start-capturing.png "CKlicken Sie auf die Schaltfläche „Erfassung”, um mit der Erfassung des HTTPS-Datenverkehrs zu beginnen)</br>

   > [!NOTE]
   > Wenn Sie HTTPS-Datenverkehr nur von einem bestimmten Host erfassen möchten, wählen Sie auf der Registerkarte **Filter** im Bereich **Hosts** im Dropdownmenü **-Kein Hostfilter-** die Option **Nur die folgenden Hosts anzeigen** aus dem Menü an, und geben Sie die Liste von Domänen ein, von denen aus Sie den Datenverkehr sehen möchten, getrennt durch Semikolon. Weitere Informationen: [Filterreferenz](https://docs.telerik.com/fiddler/KnowledgeBase/Filters).
   > ![Datenverkehr, der in der Fiddler-Benutzeroberfläche angezeigt wird, filtern](media/fiddler-filter-traffic.png "FDatenverkehr, der in der Fiddler-Benutzeroberfläche angezeigt wird, filtern)

3. Führen Sie jeglichen notwendigen Vorgang aus, um das Skript zu laden, das Sie testen. Sie können die Erfassung beenden, indem Sie erneut auf dieselbe Schaltfläche **Erfassung** klicken.
4. Wählen Sie die Ablaufverfolgungsprotokollsitzungen im linken Bereich aus, und suchen Sie die Datei, für die Sie den AutoResponder einrichten möchten.<br /> Wenn der Code, den Sie debuggen möchte, sich beispielsweise in einer JavaScript-Webressource mit Namen `new_testscript.js` befindet, verwenden Sie die Schaltfläche **Suchen**, um das Dialogfeld **Sitzungen suchen** zu öffnen, und suchen Sie nach dem Namen der Webressource. <br />![Eine Sitzung in Fiddler finden](media/fiddler-find-sessions.PNG)<br />Sie sehen die Zeilen, die mit Ihren Suchkriterien übereinstimmen, hervorgehoben im linken Bereich.
5. Wählen Sie diese Zeile aus. Wählen Sie im rechten Bereich die Registerkarte **AutoResponder** aus. <br /> ![Die Registerkarte AutoResponder auswählen](media/fiddler-auto-responder.png)
6. Aktivieren Sie in der Registerkarte **AutoResponder** die Kontrollkästchen **Regeln aktivieren** und **Passthrough nicht abgeglichener Anforderungen**.<br />
   ![Die beiden hervorgehobenen Kontrollkästchen aktivieren](media/fiddler-select-checkbox.png "SDie beiden hervorgehobenen Kontrollkästchen aktivieren)<br />
7. Stellen Sie sicher, dass Sie immer noch die Sitzung ausgewählt haben, die mit Ihrer Zieldatei verknüpft ist, und klicken Sie dann auf die Schaltfläche **Regel hinzufügen** im Abschnitt **AutoResponder**. Dadurch wird ein neuer Eintrag in der Regeltabelle hinzugefügt.<br />
   ![Neue Regel hinzufügen](media/fiddler-add-rule.png "ANeue Regel hinzufügen)
8. Wenn die Regel ausgewählt ist, wird beim **Regeleditor** unten die oberste Zeile mit der Sitzungs-URL aufgefüllt, die mit Ihrer Datei verknüpft ist und mit einer vorangestellten Zeichenfolge wie `EXACT:` versehen ist.<br />
   Sie können dann die abzugleichende Zeichenfolge bearbeiten, um sie zu vereinfachen. Mit Webressourcen wird die URL generierte Werte in der URL oder in einer Abfragezeichenfolge enthalten, um sicherzustellen, dass die aktuellste veröffentlichte Version in der Antwort enthalten ist. Sie werden wahrscheinlich feststellen, dass der Wert `EXACT` etwa folgendermaßen aussehen wird:<br />
    ```
    EXACT:https://<org URL>/%7B636556138760000160%7D/WebResources/new_testscript.js?    ver=-1229805553
    ```<br />
    You can simplify this to remove the generated values and use this instead:<br />
    ```
    /WebResources/new_testscript.js
    ```<br />
   The bottom row is left blank. Type the path to your local file on your disk on this bottom row and <strong>Save</strong>.<br />
   ![Add path to your local file in Rule editor](media/fiddler-save-rule.png "Add path to your local file in Rule editor")<br />

 

 
By following the above steps, Fiddler is configured to listen to the requests and responds with the local file instead of passing the request over the network.

## Update and test your code

1. Apply changes to your local file.
2. Start Fiddler trace capture again and go back to your browser and hard reload the page with empty cache.
3. In the browser developer tools you can see that the file that is now received will be the local one.
4. Continue repeating this process while updating your code until you get the results you require.


## See Also

[Web resources](web-resources.md)<br />
[Client scripting using JavaScript](client-scripting.md)
