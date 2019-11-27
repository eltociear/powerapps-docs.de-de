---
title: Eigenschaften und Aktionen des ModelDrivenFormIntegration-Steuerelements | MicrosoftDocs
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
ms.openlocfilehash: 20a28b159158579b35fb9e8a1b650f718c5ef83b
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2703949"
---
# <a name="modeldrivenformintegration-control-properties-and-actions"></a>Eigenschaften und Aktionen des ModelDrivenFormIntegration-Steuerelements
Canvas-Apps, die in modellgesteuerten Formularen eingebettet sind, enthalten ein spezielles Steuerelement namens **ModelDrivenFormIntegration**. Dieses Steuerelement ist dafür verantwortlich, Kontextdaten aus dem Hostmodell-basierten Formular in die eingebettete Canvas-App zu bringen.  

In diesem Thema werden die Eigenschaften und Aktionen erläutert, die im ModelDrivenFormIntegration-Steuerelement verfügbar sind.

| Eigenschaft oder Aktion | Beschreibung |
|:--------------|:-------------------------|
|**Datenquelle** | Sollte auf die Datenquelle festgelegt werden, die mit der übergeordneten Entität des modellgesteuerten Hostformulars verknüpft ist. <br />Wird automatisch festgelegt, wenn [eine neue Canvas-App eingebettet wird](embedded-canvas-app-add-classic-designer.md). |
|**Element** | Die schreibgeschützte Eigenschaft, die es der eingebetteten Canvas-App ermöglicht, über das modellgesteuerte Hostformular auf den Datensatz zuzugreifen. <br />Wenn Sie beispielsweise den Wert eines Felds mit dem Namen AccountNumber und den Anzeigenamen Firmennummer abrufen möchten, können Sie ModelDrivenFormIntegration.Item.accountnumber oder ModelDrivenFormIntegration.Item.'Account Number' verwenden. |
|**OnDataRefresh** | Die Formel in dieser Eigenschaft wird ausgewertet, wenn das modellgesteuerte Hostformular Daten speichert. <br />Verwenden Sie sie, um die Datenquelle zu aktualisieren, die mit der übergeordneten Entität des modellgesteuerten Formulars verknüpft ist, und um andere Aktionen auszuführen wie das Festlegen oder Aktualisieren von Variablen. <br /> Wenn Sie dies beispielsweise auf die Formel unten festlegen, wird die Datenquelle der Firma aktualisiert und eine Variable namens CurrentAccountNumber auf den Wert des Firmennummernfelds des aktuellen Datensatzes festgelegt. <br /> Refresh(Accounts); Set(CurrentAccountNumber, ModelDrivenFormIntegration.Item.'Account Number') |
|**RefreshForm** | Aktualisiert die Daten im modellgesteuerten Hostformular. <br />Siehe [Durchführen vordefinierter Aktionen im Hostformular](embedded-canvas-app-actions.md#refreshformshowprompt) for details. |
|**SaveForm** | Speichert die Daten im modellgesteuerten Hostformular. <br />Siehe [Durchführen vordefinierter Aktionen im Hostformular](embedded-canvas-app-actions.md#saveform) for details.  |
|**NavigateToMainForm** | Navigiert das modellgesteuerte Hostformular zu einem Hauptformular und zeigt den angegebenen Datensatz an. <br />Siehe [Durchführen vordefinierter Aktionen im Hostformular](embedded-canvas-app-actions.md#navigatetomainformentityname-mainformname-recordid) for details. |
|**NavigateToView** | Navigiert das modellgesteuerte Hostformular zu einer Ansicht. <br />Siehe [Durchführen vordefinierter Aktionen im Hostformular](embedded-canvas-app-actions.md#navigatetoviewentityname-viewname) for details.  |
|**OpenQuickCreateForm** | Öffnet die Standard-Schnellerfassungsformular für eine Entität.  <br />Siehe [Durchführen vordefinierter Aktionen im Hostformular](embedded-canvas-app-actions.md#openquickcreateformentityname) for details.  |
|**Daten** | Eine schreibgeschützte Eigenschaft, die vom Framework verwendet wird, um bestimmte Schlüsseldaten vom modellgesteuerten Hostformular an die eingebettete Canvas-App zu senden.  <br /> Verwenden Sie diese Eigenschaft nicht. Verwenden Sie dieses Element, um über das modellgesteuerte Hostformular auf den Datensatz zuzugreifen.  |

## <a name="see-also"></a>Siehe auch
[Einbetten einer Canvas-App in einem modellgesteuerten Formular](embed-canvas-app-in-form.md) <br />
[Hinzufügen einer eingebetteten Canvas-App in einem modellgesteuerten Formular](embedded-canvas-app-add-classic-designer.md) <br />
[Bearbeiten einer Canvas-App, die in einem modellgesteuerten Formular eingebettet ist](embedded-canvas-app-edit-classic-designer.md) <br />
[Anpassen der Bildschirmgröße und Ausrichtung einer Canvas-App, die in einem modellgesteuerten Formular eingebettet ist](embedded-canvas-app-customize-screen.md) <br />
[Führen Sie vordefinierte Aktionen aus einer eingebetteten Canvas-App auf dem Hostformular aus](embedded-canvas-app-actions.md) <br />
[Teilen einer eingebetteten Canvas-App](share-embedded-canvas-app.md) <br />
[Richtlinien zum Arbeiten mit eingebetteten Canvas-Apps](embedded-canvas-app-guidelines.md) <br />
[Migrieren von eingebetteten Canvas-Apps in modellgesteuerten Formularen, die mithilfe der öffentlichen Vorschauversion als die neueste Version erstellt wurden](embedded-canvas-app-migrate-from-preview.md) <br />
