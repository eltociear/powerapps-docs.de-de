---
title: Richtlinien zum Arbeiten mit eingebetteten Canvas-Apps | MicrosoftDocs
ms.custom: ''
ms.date: 08/19/2019
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
- Power Apps maker portal impact
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 20b37d6e4a75560a74fb31779dfd6965247baa7f
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2868401"
---
# <a name="guidelines-on-working-with-embedded-canvas-apps"></a>Richtlinien zum Arbeiten mit eingebetteten Canvas-Apps
Dieses Thema enthält Richtlinien für die Arbeit mit eingebetteten Canvas-Apps sowie hilfreiche Tipps zur Fehlerbehebung bei Problemen, die auftreten können.

-   Eingebettete Canvas-Apps werden nur für modellgestützte Apps mit Einheitlicher Oberfläche unterstützt.
-   Sie können nur eine eingebettete Canvas-App pro Formular aktivieren. 
     - Sie können dem Formular mehrere eingebettete Canvas-Apps hinzufügen, können aber nur eine nach der anderen aktivieren.
     - Wenn Sie versuchen, mehr als eine eingebettete Canvas-App in einem modellgestützen Formular zu aktivieren, erhalten Sie die Meldung "Nur eine Canvas-App kann in einem Formular aktiviert werden".
     - Um eine eingebettete Canvas-App zu aktivieren oder zu deaktivieren, siehe [Eingebettete Canvas-App aktivieren](#enable-an-embedded-canvas-app) und [Eingebettete Canvas-App deaktivieren](#disable-an-embedded-canvas-app)
-   Wenn Sie eine eingebettete Canvas-App zu einem modellgesteuerten Formular hinzuzufügen, verwenden Sie immer ein Pflichtfeld, das garantiert einen Wert hat. Wenn Ihr Feld keinen Wert hat, wird Ihre eingebettete Canvas-App nicht aktualisiert, wenn sich die Daten auf dem Hostmodell-basierten Formular ändern.
-   Das Veröffentlichen eines modellgestützten Formulars veröffentlicht nicht auch die eingebettete Canvas-App.
     - Eingebettete Canvas-Anwendungen müssen unabhängig vom Hostmodell-basierten Formular veröffentlicht werden. Weitere Informationen: [Veröffentlichen einer App](../canvas-apps/save-publish-app.md#publish-an-app).
-   Wenn das Öffnen von Power Apps Studio zum Erstellen oder Bearbeiten einer eingebetteten Canvas-App über die Schaltfläche **Anpassen** in den Eigenschaften der Canvas-App-Steuerungseigenschaften aufgrund eines Popupblockers des Webbrowsers blockiert wird, müssen Sie die Website web.powerapps.com aktivieren oder den Popupblocker vorübergehend deaktivieren und dann **Anpassen** erneut auswählen.
-   Eingebettete Canvas-Apps werden beim Erstellen eines neuen Datensatzes nicht angezeigt, da sie einen Datensatz-Kontext benötigen, der an sie übergeben werden muss.
-   Das ModelDrivenFormIntegration.Item-Objekt ist schreibgeschützt. 
     - Um Daten zurückzuschreiben, müssen Sie den Common Data Service-Connector verwenden. Weitere Informationen: [Common Data Service](/connectors/commondataservice/)
-   Eingebettete Canvas-Apps können nur über das Hostmodell-basierte Formular erstellt werden. 
    - Das Hinzufügen vorhandener Canvas-Apps, die in modellgesteuerten Formularen eingebettet sind, wird derzeit nicht unterstützt.
    - Die Unterstützung für das Einbetten einer vorhandenen Canvas-App in einem modellgesteuerten Formular mithilfe der App-ID wird in einem zukünftigen Update eingeführt.
- Wenn Sie ein modellgetriebenes Formular mit einer eingebetteten Canvas-Applikation anzeigen und eine Fehlermeldung mit der Aufschrift "Leider konnte diese Anwendungs-ID nicht gefunden werden" sehen, stellen Sie sicher, dass die eingebettete Canvas-App in der gleichen Lösung wie das modellgestützte Formular ist.
- Wenn Sie ein modellgestütztes Formular mit einer eingebetteten Canvas-App anzeigen und Ihnen wird eine Fehlermeldung angezeigt, die lautet: "Anscheinend haben Sie keinen Zugriff auf diese App. Bitten Sie den Besitzer, sie mit Ihnen zu teilen", stellen Sie sicher, dass der Autor die eingebettete Canvas-App mit Ihnen geteilt hat. Weitere Informationen: [Teilen einer eingebetteten Canvas-App](share-embedded-canvas-app.md).
- Das Hinzufügen einer Canvas-App zum Subgrid-Control ist nicht mehr möglich.
    - In der Vorschau-Version konnten die Hersteller eine Canvas-App auf einem Sub-Grid-Control hinzufügen. Da die Canvas-Applikation in modellgetriebene Formulare eingebettet ist, die jetzt allgemein verfügbar sind, wird das Hinzufügen einer eingebetteten Canvas-Applikation zu einem modellgetriebenen Formular im Feld optimiert. 
    - Dies erleichtert es den Herstellern, da sie sich nicht im Voraus entscheiden müssen, ob sie den aktuellen (Hauptformular-)Datensatz als Datenkontext oder eine Liste von Datensätzen, die sich auf den aktuellen (Hauptformular-)Datensatz beziehen, übergeben wollen. 
    - Der Ersteller beginnt immer mit einem Feld und kann sowohl auf den aktuellen (Hauptformular-)Datensatz als auch auf eine Liste von Datensätzen zugreifen, die sich auf den aktuellen (Hauptformular-)Datensatz beziehen.
    - Um auf die Liste der Bezugsdatensätze in der Canvas-App zuzugreifen, können Hersteller den Common Data Service-Konnektor und die Funktion [Filter](../canvas-apps/functions/function-filter-lookup.md) mit der Funktion [Verbessern der Erfahrung mit Datenquellen und der in der Canvas-App aktivierten Fähigkeit Common Data Service-Ansichten](https://powerapps.microsoft.com/blog/improved-data-source-selection-and-common-data-service-views/) verwenden.  
    Um beispielsweise auf die Ansicht *Aktive Kontakte* der Entität *Kontakte* zuzugreifen, können Hersteller verwenden: *Filter(Kontakte, 'Kontakte (Ansichten)'.'Aktive Kontakte')*.
    - Bestehende Canvas-Anwendungen, die das Subgrid-Control verwenden, funktionieren weiterhin. Wir empfehlen jedoch, diese Anwendungen zu migrieren, um stattdessen ein Feld zu verwenden. Mehr Informationen: [Migrieren von eingebetteten Canvas-Anwendungen auf modellgesteuerten Formularen, die eine Liste von Datensätzen verwenden, die sich auf den aktuellen (Haupt-)Datensatz](embedded-canvas-app-migrate-from-preview.md#migrating-embedded-canvas-apps-on-model-driven-forms-that-use-a-list-of-records-related-to-the-current-main-form-record) beziehen, für Details.

## <a name="enable-an-embedded-canvas-app"></a>Aktivieren einer eingebetteten Canvas-App
1. Wählen Sie das Feld aus, das so angepasst ist, dass es als eingebettete Canvas-App angezeigt wird.
2. Wählen Sie im Dialogfeld **Feldeigenschaften** die **Steuerelemente**-Registerkarte aus.
3. Wählen Sie in der Liste der Steuerelemente die Option **Canvas-App** und wählen Sie dann die Option **Web** aus.
4. Wählen Sie **OK** aus.

## <a name="disable-an-embedded-canvas-app"></a>Deaktivieren einer eingebetteten Canvas-App
1. Wählen Sie das Feld aus, das so angepasst ist, dass es als eingebettete Canvas-App angezeigt wird.
2. Wählen Sie im Dialogfeld **Feldeigenschaften** die **Steuerelemente**-Registerkarte aus.
3. Wählen Sie in der Liste der Steuerelemente das Standardsteuerelement und dann die Option **Web**.
4. Wählen Sie **OK** aus.

## <a name="known-issues-and-limitations-with-embedded-canvas-apps"></a>Bekannte Probleme und Einschränkungen bei eingebetteten Canvas-Anwendungen
- Das benutzerdefinierte Canvas-App-Steuerelement wird nur für die Verwendung mit dem **Web** Clienttyp unterstützt. Derzeit werden **Telefon** und **Tablet** Clienttypen nicht unterstützt.
- Das ModelDrivenFormIntegration Control liefert keinen Wert für Felder einer verwandten Entität. 
  - Wenn das ModelDrivenFormIntegration Control beispielsweise mit der Entität Accounts verbunden ist, verwenden Sie *ModelDrivenFormIntegration.Item,'Primary Contact','Full Name'* gibt keinen Wert zurück. 
  - Um auf Felder einer verwandten Entität zuzugreifen, können Hersteller einen der hier aufgeführten Ausdrücke verwenden:
    - *LookUp(Accounts, Account = GUID(First(ModelDrivenFormIntegration.Data).ItemId)).'Primary Contact'.'Full Name'*  
      - *ItemId* ist zur Erstellungszeit leer, wird aber zur Laufzeit einen Wert haben.
    - *LookUp(Accounts, Account = ModelDrivenFormIntegration.Item.Account).'Primary Contact'.'Full Name'* (Dieser Ausdruck ist einfacher zu lesen, aber der vorherige Ausdruck wird etwas besser funktionieren.)
- Sie können das **Canvas-App**-Recht in einer Sicherheitsrolle nicht verwenden, um App-Benutzern Zugriff auf eine eingebettete oder eigenständige Canvas-App zu gewähren. Weitere Informationen zum Teilen einer eingebetteten Canvas-App finden Sie unter: [Eine eingebettete Canvas-App teilen](share-embedded-canvas-app.md).
- Wenn Sie die gleichen Daten zurückschreiben, die auch im Hostmodell-basierten Formular angezeigt werden, zeigt das Formular weiterhin alte Daten an, bis es aktualisiert wird. Eine einfache Möglichkeit dazu ist Verwendung der [RefreshForm](embedded-canvas-app-actions.md#refreshformshowprompt)-Methode.

## <a name="see-also"></a>Siehe auch
[Einbetten einer Canvas-App in einem modellgesteuerten Formular](embed-canvas-app-in-form.md) <br />
[Hinzufügen einer eingebetteten Canvas-App in einem modellgesteuerten Formular](embedded-canvas-app-add-classic-designer.md) <br />
[Bearbeiten einer Canvas-App, die in einem modellgesteuerten Formular eingebettet ist](embedded-canvas-app-edit-classic-designer.md) <br />
[Anpassen der Bildschirmgröße und Ausrichtung einer Canvas-App, die in einem modellgesteuerten Formular eingebettet ist](embedded-canvas-app-customize-screen.md) <br />
[Führen Sie vordefinierte Aktionen aus einer eingebetteten Canvas-App auf dem Hostformular aus](embedded-canvas-app-actions.md) <br />
[Eigenschaften und Aktionen des ModelDrivenFormIntegration-Steuerelements](embedded-canvas-app-properties-actions.md) <br />
[Teilen einer eingebetteten Canvas-App](share-embedded-canvas-app.md) <br />
[Migrieren von eingebetteten Canvas-Apps in modellgesteuerten Formularen, die mithilfe der öffentlichen Vorschauversion als die neueste Version erstellt wurden](embedded-canvas-app-migrate-from-preview.md) <br />
