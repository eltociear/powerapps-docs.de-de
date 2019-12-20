---
title: Anzeige benutzerdefinierter Symbole neben Werten in Listenansichten mit Power Apps | MicrosoftDocs
description: Erfahren Sie, wie benutzerdefinierte Symbolgrafiken in einer Ansicht angezeigt werden
ms.custom: ''
ms.date: 11/20/2019
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
ms.assetid: af866aed-2586-4b6f-bb1c-3519baae3645
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5a8eec0d7079b748b5b70c623c794b403b399ea2
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2861069"
---
# <a name="display-custom-icons-alongside-values-in-list-views"></a>Benutzerdefinierte Symbole zusammen mit Werten in Listenansichten anzeigen

<a name="GridIcons"></a>   

 Power Apps-Umgebungsadministratoren und Customizer können einer Ansicht Grafiken hinzufügen und die Logik festlegen, mit der eine Grafik basierend auf dem Spaltenwert per JavaScript ausgewählt wird. Mit dieser Funktion können Sie Listenansichten anpassen, die Symbole neben Text- oder Zahlenwerten anzeigen. 

In diesem Beispiel werden benutzerdefinierte Symbole in einer Ansicht für die Verkaufschancen-Entität angezeigt, die für bestimmte Apps verfügbar ist, z. B. Dynamics 365 Sales. Sie können benutzerdefinierte Symbole in Ansichten mit anderen Standardentitäten wie dem Konto oder der Kontaktentität sowie benutzerdefinierten Entitäten anzeigen. 

> [!div class="mx-imgBorder"] 
> ![](media/icon-in-opportunity-view.png "All Opportunities view with Rating column displaying icons and text value")
  
Benutzerdefinierte Symbole in Listenansichten können in der einheitlichen Oberfläche, im alten Webclient, der mobilen App und App for Outlook angezeigt werden. 
  
## <a name="add-custom-graphics-and-javascript-as-web-resources"></a>Hinzufügen von benutzerdefinierten Grafiken und JavaScript als Webressourcen  
  
1.  Erstellen Sie neue Grafikdateien für Ihre Anpassungen. Es wird empfohlen, eine Symbolgröße von 16x16 Pixeln zu nutzen (größeren Bilder werden herunterskaliert).  
  
2.  Schreiben Sie einen oder mehrere JavaScript-Funktionen, die definieren, welche Symbole für welche Werte angezeigt werden (Sie benötigen in der Regel eine Funktion für jede Spalte, die Sie anpassen möchten). Jede Funktion muss ein Zeilendatenobjekt und einen Sprachcode (LCID) als Eingabe akzeptieren einen Array mit einem Bildnamen und Tooltiptext zurückgeben. Im Abschnitt [Beispiel-JavaScript-Funktion](#SampleJavascript) weiter unten in diesem Artikel finden Sie eine Beispielfunktion.  
  
3.  Melden Sie sich in Ihrer Umgebung als Administrator an, und öffnen Sie den [Lösungs-Explorer](../model-driven-apps/advanced-navigation.md#solution-explorer).  
  
4.  Die Fenster **Standardlösung** wird geöffnet. Navigieren Sie zu **Komponenten** > **Webressourcen**.  
  
5.  Jetzt können Sie Ihre benutzerdefinierten Grafiken einzeln als Webressourcen hochladen. Wählen Sie in der Symbolleiste die Schaltfläche **Neu**, um eine neue Webressource zu erstellen. Ein weiteres Popupfenster wird geöffnet, das Ihnen dabei hilft, die Ressource zu erstellen. Führen Sie die folgenden Schritte aus:  
  
    1.  Geben Sie der neuen Ressource einen aussagekräftigen **Namen**. Dies ist der Name, den Sie zum Verweis auf jede Grafik im JavaScript-Code verwenden.  
  
    2.  Legen Sie den **Typ** auf das Grafikformat fest, das Sie verwendet haben, um die Grafikdatei (PNG, JPEG oder GIF) zu speichern.  
  
    3.  Wählen Sie **Datei auswählen** aus, um ein Dateibrowserfenster zu öffnen. Verwenden Sie es, um die Grafikdatei zu suchen und auszuwählen.  
  
    4.  Fügen Sie **Anzeigename** und/oder **Beschreibung** bei Bedarf hinzu.  
  
    5.  Wählen Sie **Speichern** aus, und schließen Sie dann das Fenster **Webressource**.  
  
6.  Wiederholen Sie diese Schritte für jede Grafikdatei, die Sie besitzen.  
  
7.  Fügen Sie nun JavaScript als Webressource hinzu. Wählen Sie in der Symbolleiste **Neu** aus, um eine neue Webressource zu erstellen. Ein weiteres Popupfenster wird geöffnet, das Ihnen dabei hilft, die Ressource zu erstellen. Führen Sie die folgenden Schritte aus:  
  
    1.  Geben Sie der neuen Ressource einen aussagekräftigen **Namen**.  
  
    2.  Legen Sie **Typ** auf **Skript (JScript)** fest.  
  
    3.  Wählen Sie **Text-Editor** (neben der **Typ**-Einstellung), um ein Texteditorfenster zu öffnen. Fügen Sie Ihren Javascriptcode hier ein und wählen Sie **OK** aus, um ihn zu speichern.  
  
    4.  Fügen Sie **Anzeigename** und/oder **Beschreibung** bei Bedarf hinzu.  
  
    5.  Wählen Sie **Speichern** aus, und schließen Sie dann das Fenster **Webressource**.  
  
8.  Mit dem offenen **Standardlösung**-Popupfenster erweitern Sie die Struktur **Komponenten** > **Entitäten** und suchen die Entität, die Sie anpassen möchten.  
  
9. Erweitern Sie die Entität und wählen Sie das **Ansichten**-Symbol aus.  
  
10. Sie sehen jetzt eine Liste der Ansichten für die ausgewählte Entität. Wählen Sie eine Ansicht in der Liste aus. Öffnen Sie dann die Dropdownliste **Weitere Aktionen** auf der Symbolleiste, und wählen Sie **Bearbeiten** aus.  
  
11. Ein Popupfenster wird geöffnet. Es enthält Steuerelemente für die Bearbeitung der ausgewählten Ansicht. Er zeigt jede Spalte an, die Teil der Ansicht ist. Wählen Sie die Zielspalte und wählen Sie dann **Eigenschaften ändern** im Feld **Allgemeine Aufgaben** aus. Das Dialogfeld **Spalteneigenschaften ändern** wird geöffnet. Nehmen Sie die folgenden Einstellungen vor:  
  
    - **Webressource**: Geben Sie den Namen der Webressource an, die Sie für Ihre Javascript-Funktionen erstellt haben (wählen Sie **Durchsuchen** aus, um aus einer Liste zu wählen).  
  
    - **Funktionsname**: Geben Sie den Namen der Funktionalität ein, die Sie für die Änderung der ausgewählten Spalte und Ansicht geschrieben haben.  
  
12. Wählen Sie **OK** aus, um den Dialog **Spalteneigenschaften ändern** zu schließen.  
  
13. Wählen Sie **Speichern und schließen** aus, um Ihre Ansicht zu speichern.  
  
14. Wiederholen Sie diese Schritte für jede betreffende Entität, Ansicht und Spalte.  
  
15. Wenn Sie bereit sind, wählen Sie **Alle Anpassungen veröffentlichen** aus, um die Änderungen zu veröffentlichen. Schließen Sie dann das Fenster **Standardlösung**.  
  
<a name="SampleJavascript"></a>   

### <a name="sample-javascript-function"></a>Beispiel-JavaScript-Funktion  
 Die JavaScript-Funktion zum Anzeigen benutzerdefinierter Symbole und Tooltips erwartet die folgenden beiden Argumente: das gesamte Zeilenobjekt angegeben in layoutxml und des aufrufender Benutzers Gebietsschema-ID (LCID). Der LCID-Parameter ermöglicht Ihnen, Tooltiptext für das Symbol in mehreren Sprachen zu definieren. Weitere Informationen zu den von der Umgebung unterstützten Sprachen finden Sie unter [Sprachen aktivieren](/dynamics365/customer-engagement/admin/enable-languages) und [Sprachpakete installieren oder aktualisieren](/dynamics365/customer-engagement/on-premises/install-or-upgrade-language-packs). Eine Liste mit Werten von lokalen Gebietsschema-ID (LCID)-Werten, die Sie in Ihrem Code verwenden können, finden Sie unter [Von Microsoft zugewiesene lokale IDs](https://go.microsoft.com/fwlink/?linkid=829588).

  
 Sie werden wahrscheinlich benutzerdefinierte Symbole für einen Optionssatztyp von Attributen hinzufügen, bei dem die vordefinierten Optionen begrenzt sind. Stellen Sie sicher, dass Sie den ganzzahligen Wert der Optionen anstelle der Beschriftung verwenden, um zu Lokalisierungsprobleme zu verhindern.  
  
 Der folgende Beispielcode zeigt Symbole und Tooltips auf Basis von drei Werten an (1: Hot, 2: Warm, 3: Cold) im Attribut opportunityratingcode (Bewertung) an. Der Beispielcode zeigt auch, wie ein lokalisiertes Tooltip angezeigt wird. Damit dieses Beispiel funktioniert, müssen Sie drei Bildwebressourcen von 16x16 Bildern mit den folgenden Namen erstellen: new_Hot, new_Warm und new_Cold.  

> [!IMPORTANT]
> Dieses Beispiel benötigt die Verkaufschancen-Entität, die mit der Dynamics 365 Sales App verfügbar ist.
  
```javascript
function displayIconTooltip(rowData, userLCID) {      
    var str = JSON.parse(rowData);  
    var coldata = str.opportunityratingcode_Value;  
    var imgName = "";  
    var tooltip = "";  
    switch (parseInt(coldata,10)) { 
        case 1:  
            imgName = "new_Hot";  
            switch (userLCID) {  
                case 1036:  
                    tooltip = "French: Opportunity is Hot";  
                    break;  
                default:  
                    tooltip = "Opportunity is Hot";  
                    break;  
            }  
            break;  
        case 2:  
            imgName = "new_Warm";  
            switch (userLCID) {  
                case 1036:  
                    tooltip = "French: Opportunity is Warm";  
                    break;  
                default:  
                    tooltip = "Opportunity is Warm";  
                    break;  
            }  
            break;  
        case 3:  
            imgName = "new_Cold";  
            switch (userLCID) {  
                case 1036:  
                    tooltip = "French: Opportunity is Cold";  
                    break;  
                default:  
                    tooltip = "Opportunity is Cold";  
                    break;  
            }  
            break;  
        default:  
            imgName = "";  
            tooltip = "";  
            break;  
    }  
    var resultarray = [imgName, tooltip];  
    return resultarray;  
}  
```  
  
 <!-- This results in displaying icons with tooltips in the **Rating** column that depend on the value in each row. The result could look like this:  
  
 ![Custom column graphics example](../customize/media/custom-column-graphics-example.png "Custom column graphics example")  --> 

## <a name="custom-icon-view-display-behavior"></a>Anzeigeverhalten der benutzerdefinierten Symbolansicht
### <a name="primary-fields"></a>Hauptfelder 
In der Rasterlistenansicht ersetzen benutzerdefinierte Symbole, die auf das primäre Entitätsfeld angewendet werden, das vom System generierte Standardsymbol. 

> [!div class="mx-imgBorder"] 
> ![](media/mobile-primary-field-custom-icon-display.png "Primary field replaces default icon in the custom icon view")

### <a name="other-fields"></a>Andere Felder 
In der Rasterlistenansicht werden benutzerdefinierte Symbole, die auf ein Feld angewendet werden, das nicht das primäre Entitätsfeld ist, zusätzlich zum vom System generierten Standardsymbol als sekundäres Symbol angezeigt. 

> [!div class="mx-imgBorder"] 
> ![](media/card-form-not-primary-field.png "Not an entity primary field custom icon view")

### <a name="card-forms"></a>Kartenformulare
Benutzerdefinierte Symbole ersetzen das vom System generierte Standardsymbol, wenn die Ansicht für die Verwendung von Kartenformular konfiguriert ist. 

> [!div class="mx-imgBorder"] 
> ![](media/card-view-icon-display.png "Card view custom icon view")

 
 ### <a name="see-also"></a>Siehe auch
[Grundlegendes zu Ansichten modellgestützter Apps](../model-driven-apps/create-edit-views.md)
