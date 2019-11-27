---
title: Führen Sie Aktionen aus einer eingebetteten Canvas-App auf dem modellgesteuerten Hostformular aus | MicrosoftDocs
ms.custom: ''
ms.date: 06/25/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.assetid: 00e62904-2ce9-4730-a113-02b1fedbf22e
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
ms.openlocfilehash: 0f6ec9122582f338ac23143149c6f59ea63e456f
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2706105"
---
# <a name="perform-predefined-actions-on-the-host-model-driven-form-from-within-an-embedded-canvas-app"></a>Führen Sie vordefinierte Aktionen aus einer eingebetteten Canvas-App auf dem modellgesteuerten Hostformular aus
Eingebettete Canvas-Apps bieten die Möglichkeit, vordefinierte Aktionen im modellgesteuerten Hostformular auszuführen. Diese Aktionen ermöglichen es Herstellern, das modellgesteuerte Hostformular zu navigieren, zu aktualisieren und zu speichern. Mithilfe dieser Aktionen kann eine eingebettete Canvas-App als ein weiterer wesentlicher Bestandteil des modellgesteuerten Formulars und und der modellgesteuerten App agieren.  

Das **ModelDrivenFormIntegration**-Objekt enthält nun die folgenden neuen Methoden, damit Hersteller Aktionen auf dem modellgesteuerten Hostformular ausführen können.  
  
### <a name="navigatetomainformentityname-mainformname-recordid"></a>NavigateToMainForm (entityName, mainFormName, recordId)
Navigiert das modellgesteuerte Hostformular zu einem Hauptformular und zeigt den angegebenen Datensatz an.  
* **entityName** - Ein erforderlicher Zeichenfolgenparameter, der die übergeordnete Entität des Hauptformulars angibt.  
* **formName** - Ein erforderlicher Zeichenfolgenparameter, der den Namen des Hauptformulars angibt, zu dem navigiert wird.  
* **recordId** - Ein erforderlicher Zeichenfolgenparameter, der die ID des Datensatzes angibt, die im Hauptformular angezeigt wird.  
 
Das Anrufen der NavigateToMainForm-Methode kann die folgende Fehlermeldungen anzeigen.
  
| Fehlermeldung | Leitfaden für Fehlerbehebung |
|:--------------|:-------------------------|
|**Entität nicht gefunden: *[EntityName]*** | Sehen Sie sich den Wert des Parameters *entityName* an und stellen Sie sicher, dass es ein gültiger Entitätsname ist und der Benutzer Zugriff daraf hat. |
|**Formular nicht gefunden: *[FormName]*** | Sehen Sie sich den Wert des Parameters *mainFormName* an und stellen Sie sicher, dass es ein gültiger Hauptformularname ist und der Benutzer Zugriff daraf hat. |
|**Beim Laden des Datensatzes ist ein Problem aufgetreten.** | Sehen Sie sich den Wert des Parameters *recordId* an und stellen Sie sicher, dass es eine gültige Datensatz-ID ist und der Benutzer Zugriff daraf hat. |
  
  
### <a name="navigatetoviewentityname-viewname"></a>NavigateToView (entityName, viewName)
Navigiert das modellgesteuerte Hostformular zu einer Ansicht.  
* **entityName** - Ein erforderlicher Zeichenfolgenparameter, der die übergeordnete Entität der Ansicht angibt.  
* **viewName** - Ein erforderlicher Zeichenfolgenparameter, der den Namen des Hauptformulars angibt, zu dem navigiert wird.  
 
Das Anrufen der NavigateToView-Methode kann die folgende Fehlermeldungen anzeigen.
  
| Fehlermeldung | Leitfaden für Fehlerbehebung |
|:--------------|:-------------------------|
|**Entität nicht gefunden: *[EntityName]*** | Sehen Sie sich den Wert des Parameters *entityName* an und stellen Sie sicher, dass es ein gültiger Entitätsname ist und der Benutzer Zugriff daraf hat. |
|**Ansicht nicht gefunden: *[ViewName]*** | Sehen Sie sich den Wert des Parameters *viewName* an und stellen Sie sicher, dass es ein gültiger Ansichtsname ist und der Benutzer Zugriff daraf hat. |
  
  
### <a name="openquickcreateformentityname"></a>OpenQuickCreateForm (entityName)  
Öffnet die Standard-Schnellerfassungsformular für eine Entität.  
* **entityName** - Ein erforderlicher Zeichenfolgenparameter, der die übergeordnete Entität des Schnellerfassungsformulars angibt.  
 
Das Anrufen der OpenQuickCreateForm-Methode kann die folgende Fehlermeldungen anzeigen.
  
| Fehlermeldung | Leitfaden für Fehlerbehebung |
|:--------------|:-------------------------|
|**Entität nicht gefunden: *[EntityName]*** | Sehen Sie sich den Wert des Parameters *entityName* an und stellen Sie sicher, dass es ein gültiger Entitätsname ist und der Benutzer Zugriff daraf hat. |
  
  
### <a name="refreshformshowprompt"></a>RefreshForm (showPrompt)  
Aktualisiert die Daten im modellgesteuerten Hostformular.  
* **showPrompt** – Ein erforderliches boolescher Parameter, der angibt, ob dem Benutzer eine Bestätigungseingabeaufforderung angezeigt wird, bevor nicht gespeicherten Daten im modellgesteuerten Hostformular gespeichert werden. Die Werte sollen "true" oder "false" lauten.
 
Das Anrufen der RefreshForm-Methode kann die folgende Fehlermeldungen anzeigen.
  
| Fehlermeldung | Leitfaden für Fehlerbehebung |
|:--------------|:-------------------------|
|**Verwenden Sie "true" oder "false" als Parameterwert.** | Sehen Sie sich den Wert des Parameters *showPrompt* an und stellen Sie sicher, dass er entweder "true" oder "false" lautet. |
  
  
### <a name="saveform"></a>SaveForm()  
Speichert die Daten im modellgesteuerten Hostformular.  


> [!NOTE]
> Wenn Sie IntelliSense für die Methoden zum Ausführen vordefinierter Aktionen nicht in eingebetteten Canvas-Apps finden, die erstellt wurden, bevor die Funktion zur Verfügung gestellt wurde, schließen Sie die App und öffnen Sie sie erneut. 

## <a name="see-also"></a>Siehe auch
[Einbetten einer Canvas-App in einem modellgesteuerten Formular](embed-canvas-app-in-form.md) <br />
[Hinzufügen einer eingebetteten Canvas-App in einem modellgesteuerten Formular](embedded-canvas-app-add-classic-designer.md) <br />
[Bearbeiten einer Canvas-App, die in einem modellgesteuerten Formular eingebettet ist](embedded-canvas-app-edit-classic-designer.md) <br />
[Anpassen der Bildschirmgröße und Ausrichtung einer Canvas-App, die in einem modellgesteuerten Formular eingebettet ist](embedded-canvas-app-customize-screen.md) <br />
[Eigenschaften und Aktionen des ModelDrivenFormIntegration-Steuerelements](embedded-canvas-app-properties-actions.md) <br />
[Teilen einer eingebetteten Canvas-App](share-embedded-canvas-app.md) <br />
[Richtlinien zum Arbeiten mit eingebetteten Canvas-Apps](embedded-canvas-app-guidelines.md) <br />
[Migrieren von eingebetteten Canvas-Apps in modellgesteuerten Formularen, die mithilfe der öffentlichen Vorschauversion als die neueste Version erstellt wurden](embedded-canvas-app-migrate-from-preview.md) <br />
