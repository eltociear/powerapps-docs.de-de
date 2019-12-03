---
title: Funktion „Reset“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktion "Reset" in powerapps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 07/06/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 20109be5e9c77af75409973a32fe46c353d57282
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730312"
---
# <a name="reset-function-in-power-apps"></a>Funktion "Reset" in powerapps
Setzt ein Eingabesteuerelement auf seinen Standardwert zurück, wobei alle Benutzeränderungen verworfen werden.  

## <a name="description"></a>Beschreibung
Durch die Funktion **Reset** wird ein Steuerelement auf seinen **Default**-Eigenschaftswert zurückgesetzt.  Alle Benutzeränderungen werden verworfen.

Steuerelemente, die sich innerhalb eines [**Katalog**](../controls/control-gallery.md)-Steuerelements oder [**Bearbeitungsformular**](../controls/control-form-detail.md)-Steuerelements befinden, können außerhalb dieser Steuerelemente nicht zurückgesetzt werden.  Sie können Steuerelemente aus Formeln für Steuerelemente innerhalb desselben Katalogs oder Formulars zurücksetzen.  Sie können auch alle Steuerelemente innerhalb eines Formulars mit der Funktion [**ResetForm**](function-form.md) zurücksetzen. 

Die Verwendung der Funktion **Reset** stellt eine Alternative zum Umschalten der **Reset**-Eigenschaft von Eingabesteuerelementen dar und ist generell zu bevorzugen.  Die **Reset**-Eigenschaft ist eine bessere Wahl, wenn viele Steuerelemente gemeinsam aus mehreren Formeln zurückgesetzt werden müssen.  Das Umschalten der **Reset**-Eigenschaft kann aus einem [**Schaltflächen**](../controls/control-button.md)-Steuerelement mit der Formel **Reset = Button.Pressed** oder aus einer Variablen mit **Reset = MyVar** sowie durch Umschalten von **MyVar** mit der Formel **Button.OnSelect = Set( MyVar, true ); Set( MyVar, false )** erfolgen.    

Eingabesteuerelemente werden ebenfalls zurückgesetzt, wenn ihre **Default**-Eigenschaft geändert wird.

**Reset** weist keinen Rückgabewert auf; Sie können diese Funktion nur innerhalb einer [Verhaltensformel](../working-with-formulas-in-depth.md) verwenden.

## <a name="syntax"></a>Syntax
**Reset**( *Steuerelement* )

* *Steuerelement* – Erforderlich. Das zurückzusetzende Steuerelement.

## <a name="example"></a>Beispiel
1. Fügen Sie ein **Texteingabe**-Steuerelement in einem Bildschirm ein.  In der Standardeinstellung lautet sein Name **TextInput1**, und die zugehörige **Default**-Eigenschaft wird auf **„Texteingabe“** festgelegt.
2. Geben Sie im Textfeld einen neuen Wert ein.  
3. Fügen Sie ein **Schaltflächen**-Steuerelement im Bildschirm ein.
4. Legen Sie die **OnSelect**-Eigenschaft der Schaltfläche auf **Reset( TextInput1 )** fest.
5. Wählen Sie die Schaltfläche aus.  Dies kann sogar während des Erstellens durch Auswahl am Ende des Steuerelements erfolgen.
6. Der Inhalt des Textfelds wird als Wert der **Default**-Eigenschaft zurückgegeben.

