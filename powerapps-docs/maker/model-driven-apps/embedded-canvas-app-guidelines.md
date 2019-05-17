---
title: Richtlinien zum Arbeiten mit eingebetteten Canvas-Apps | MicrosoftDocs
ms.custom: ''
ms.date: 01/07/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
author: Aneesmsft
ms.author: matp
manager: kvivek
tags:
  - PowerApps maker portal impact
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="guidelines-on-working-with-embedded-canvas-apps"></a>Richtlinien zum Arbeiten mit eingebetteten Canvas-Apps
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Dieses Thema enthält Richtlinien für die Arbeit mit eingebetteten Canvas-Apps sowie hilfreiche Tipps zur Fehlerbehebung bei Problemen, die auftreten können.

-   Eingebettete Canvas-Apps werden nur für modellgestützte Apps mit Einheitlicher Oberfläche unterstützt.
-   Sie können nur eine eingebettete Canvas-App pro Formular aktivieren. 
     - Sie können dem Formular mehrere eingebettete Canvas-Apps hinzufügen, können aber nur eine nach der anderen aktivieren.
     - Wenn Sie versuchen, mehr als eine eingebettete Canvas-App in einem modellgestützen Formular zu aktivieren, erhalten Sie die Meldung "Nur eine Canvas-App kann in einem Formular aktiviert werden".
     - Um eine eingebettete Canvas-App zu aktivieren oder zu deaktivieren, siehe [Eingebettete Canvas-App aktivieren](#enable-an-embedded-canvas-app) und [Eingebettete Canvas-App deaktivieren](#disable-an-embedded-canvas-app)
-   Eingebettete Canvas-Apps können nur über das Hostmodell-basierte Formular erstellt, bearbeitet und abgespielt werden.
     - Sie können keine eingebettete Canvas-App direkt außerhalb des Kontextes eines modellgestützten Formulars erstellen.
     - Ebenso wird das Öffnen einer eingebetteten Canvas-App zum Bearbeiten oder Abspielen außerhalb des Kontextes eines modellgestützten Formulars nicht unterstützt.

     > [!NOTE]
     > Obwohl Sie möglicherweise eine eingebettete Canvas-App außerhalb einer modellgestützten App öffnen können, wird dies nicht unterstützt.

-   Beachten Sie Folgendes, wenn Sie ein Sub-Grid-Control verwenden, um eine eingebettete Canvas-App zu einem modellgestützen Formular hinzuzufügen.
     - Die Daten (Felder und Werte), die zur Laufzeit an die eingebettete Canvas-App gesendet werden, werden durch die Ansicht bestimmt, die als **Standardansicht** im Abschnitt **Datenquelle** der Eigenschaften des Unterrastersteuerelements angegeben ist. Verwenden Sie in Ihrer eingebetteten Canvas-App nur Felder, die in der Ansicht enthalten sind, oder fügen Sie sie bei Bedarf der Ansicht hinzu. Alle Felder, die nicht in der Ansicht enthalten sind, zeigen zur Laufzeit leere Werte an. 
     - Die Filterkriterien für eine Ansicht werden zum Zeitpunkt der Erstellung nicht verwendet. Daher werden die Daten, die Sie beim Erstellen von eingebetteten Canvas-Anwendungen sehen, nicht gefiltert, es ist lediglich eine Liste der wichtigsten Datensätze, auf die Sie Zugriff haben. Zur Laufzeit werden die Filterkriterien für die Ansicht erwartungsgemäß angewendet und nur relevante Daten angezeigt.
-   Wenn Sie ein Feldsteuerelement verwenden, um eine eingebettete Canvas-Anwendung zu einem modellgesteuerten Formular hinzuzufügen, verwenden Sie immer ein Pflichtfeld, das garantiert einen Wert hat. Wenn Ihr Feld keinen Wert hat, wird Ihre eingebettete Canvas-App nicht aktualisiert, wenn sich die Daten auf dem Hostmodell-basierten Formular ändern.
-   Das Veröffentlichen eines modellgestützten Formulars veröffentlicht nicht auch die eingebettete Canvas-App.
     - Eingebettete Canvas-Anwendungen müssen unabhängig vom Hostmodell-basierten Formular veröffentlicht werden. Weitere Informationen: [Veröffentlichen einer App](../canvas-apps/save-publish-app.md#publish-an-app).
-   Wenn das Öffnen von PowerApps Studio zum Erstellen oder Bearbeiten einer eingebetteten Canvas-App über die Schaltfläche **Anpassen** in den Eigenschaften der Canvas-App-Steuerung aufgrund eines Popup-Blockers des Webbrowsers blockiert wird, müssen Sie die Website web.powerapps.com aktivieren oder den Popup-Blocker vorübergehend deaktivieren und dann **Anpassen** erneut auswählen.
-   Eingebettete Canvas-Apps werden beim Erstellen eines neuen Datensatzes nicht angezeigt, da sie einen Datensatz-Kontext benötigen, der an sie übergeben werden muss.
-   Das ModelDrivenFormIntegration.Data-Objekt ist schreibgeschützt. 
     - Um Daten zurückzuschreiben, müssen Sie den Common Data Service-Connector verwenden. Weitere Informationen: [Common Data Service](/connectors/commondataservice/)
-   Das ModelDrivenFormIntegration.Data-Objekt ist eine Liste mit Datensätzen. 
     - Sogar der aktuelle Datensatz wird über ModelDrivenFormIntegration.Data als Liste, die einen einzelnen Datensatz enthält, an die eingebettete Canvas-App übergeben.
     - Um den Datensatz direkt zu referenzieren, können Sie die [Funktion First](../canvas-apps/functions/function-first-last.md) verwenden. Beispiel: First(ModelDrivenFormIntegration.Data).Name
-   Eine manuelle Änderung der App-ID in den Canvas-App-Steuerelementeigenschaften ist so weit wie möglich zu vermeiden.
     - Die App-ID der Canvas-App wird automatisch generiert und für Sie ausgefüllt. 
     - Wenn Sie es aus irgendeinem Grund manuell bearbeiten müssen, müssen Sie sicherstellen, dass jede von Ihnen verwendete App-ID einer *eingebetteten* Canvas-App entspricht und nicht nur einer eigenständigen Canvas-App. 
     - Die eingebettete Canvas-App muss ebenfalls mit dem gleichen Datenkontext erstellt werden, den Ihr modellgestütztes Formular senden wird.
     - Nachdem Sie die App-ID aktualisiert haben, wählen Sie **Anpassen**, um sie in PowerApps Studio zu öffnen und die Verbindung zur neuen App herzustellen.
     - Nehmen Sie eine kleine Änderung in der App vor, um sie in einen nicht gespeicherten Status zu versetzten, dann speichern und veröffentlichen Sie die App.
- Wenn Sie ein modellgetriebenes Formular mit einer eingebetteten Canvas-Applikation anzeigen und eine Fehlermeldung mit der Aufschrift "Leider konnte diese Anwendungs-ID nicht gefunden werden" sehen, stellen Sie sicher, dass die eingebettete Canvas-App in der gleichen Lösung wie das modellgestützte Formular ist.
- Wenn Sie ein modellgestütztes Formular mit einer eingebetteten Canvas-App anzeigen und Ihnen wird eine Fehlermeldung angezeigt, die lautet: "Anscheinend haben Sie keinen Zugriff auf diese App. Bitten Sie den Besitzer, sie mit Ihnen zu teilen", stellen Sie sicher, dass der Autor die eingebettete Canvas-App mit Ihnen geteilt hat. Weitere Informationen: [Teilen einer eingebetteten Canvas-App](share-embedded-canvas-app.md).

## <a name="enable-an-embedded-canvas-app"></a>Aktivieren einer eingebetteten Canvas-App
1. Wählen Sie das Feld- oder Unterraster-Steuerelement aus, das so angepasst ist, dass es als eingebettete Canvas-App angezeigt wird.
2. Im Dialogfeld **Feldeigenschaften** (oder **Eigenschaften festlegen** für Unterraster) wählen Sie die Registerkarte **Steuerelemente** aus.
3. Wählen Sie in der Liste der Steuerelemente die Option **Canvas-App** und wählen Sie dann die Option **Web** aus.
4. Wählen Sie **OK** aus.

## <a name="disable-an-embedded-canvas-app"></a>Deaktivieren einer eingebetteten Canvas-App
1. Wählen Sie das Feld- oder Unterraster-Steuerelement aus, das so angepasst ist, dass es als eingebettete Canvas-App angezeigt wird.
2. Im Dialogfeld **Feldeigenschaften** (oder **Eigenschaften festlegen** für Unterraster) wählen Sie die Registerkarte **Steuerelemente** aus.
3. Wählen Sie in der Liste der Steuerelemente das Standardsteuerelement und dann die Option **Web**.
4. Wählen Sie **OK** aus.

## <a name="known-issues-and-limitations-with-embedded-canvas-apps"></a>Bekannte Probleme und Einschränkungen bei eingebetteten Canvas-Anwendungen
- Das benutzerdefinierte Canvas-App-Steuerelement wird nur für die Verwendung mit dem **Web** Clienttyp unterstützt. Derzeit werden **Telefon** und **Tablet** Clienttypen nicht unterstützt. Weitere Informationen: [Verwenden von benutzerdefinierten Steuerelementen für modellgestütze App-Datenvisualisierungen](use-custom-controls-data-visualizations.md)
- Wenn Sie einen neuen Datensatz erstellen, wird eine eingebettete Canvas-App in einem Formular auch nach dem Speichern des Datensatzes nicht angezeigt. 
-    Das ModelDrivenFormIntegration.Data-Objekt arbeitet derzeit nicht mit dem Anzeigenformular und den Formular bearbeiten-Steuerelementen.
- Sie können das **Canvas-App**-Recht in einer Sicherheitsrolle nicht verwenden, um App-Benutzern Zugriff auf eine eingebettete oder eigenständige Canvas-App zu gewähren. Weitere Informationen zum Teilen einer eingebetteten Canvas-App finden Sie unter: [Eine eingebettete Canvas-App teilen](share-embedded-canvas-app.md).
- Wenn Sie die gleichen Daten zurückschreiben, die auch im Hostmodell-basierten Formular angezeigt werden, zeigt das Formular weiterhin alte Daten an, bis es aktualisiert wird. Eine einfache Möglichkeit dazu ist Verwendung der [RefreshForm](embedded-canvas-app-actions.md)-Methode.
- Wenn Sie IntelliSense für die [Methoden zum Ausführen vordefinierter Aktionen](embedded-canvas-app-actions.md) nicht in eingebetteten Canvas-Apps finden, die erstellt wurden, bevor die Funktion zur Verfügung gestellt wurde, schließen Sie die App und öffnen Sie sie erneut. 

## <a name="see-also"></a>Siehe auch
[Einbetten einer Canvas-App in ein modellgesteuertes Formular](embed-canvas-app-in-form.md) <br />
[Den aktuellen Datensatz als Datenkontext an eine eingebettete Canvas-App übergeben](pass-current-embedded-canvas-app.md) <br />
[Eine Liste von aktuellen Datensätzen als Datenkontext an eine eingebettete Canvas-App übergeben](pass-related-embedded-canvas-app.md) <br />
[Führen Sie vordefinierte Aktionen aus einer eingebetteten Canvas-App auf dem Hostformular aus](embedded-canvas-app-actions.md) <br />
[Teilen einer eingebetteten Canvas-App](share-embedded-canvas-app.md)
