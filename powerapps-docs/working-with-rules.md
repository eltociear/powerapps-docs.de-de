---
title: Erstellen einer Regel | Microsoft-Dokumentation
description: Eine schrittweise Anleitung zum Entwerfen von App-Logik durch Erstellen von Regeln
services: 
suite: PowerApps
documentationcenter: na
author: karthik-1
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 09/14/2017
ms.author: karthikb
ms.openlocfilehash: c6b7141c20591c1fdbb5278b1fe4d75bfb6a4ebb
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="create-a-rule-in-powerapps"></a>Erstellen einer Regel in PowerApps
Erstellen Sie Regeln, damit eine App automatisch auf Grundlage der von Ihnen angegebenen Kriterien geändert wird. Beispielsweise können Listenelemente je nach ihrem Status in Rot, Gelb oder Grün angezeigt werden, oder eine Genehmigungsschaltfläche kann nur für bestimmte Benutzer (z.B. Manager) angezeigt werden.

Sie können vielen verschiedenen Steuerelementen Regeln hinzufügen. In diesem Thema fügen Sie eine Regel hinzu, um die Textfarbe eines **Label**-Steuerelements (Bezeichnung) zu ändern, wenn der Wert eines **Slider**-Steuerelements (Schieberegler) größer als 70 ist.

## <a name="add-a-rule"></a>Regel hinzufügen
1. Wählen Sie ein Steuerelement aus (oder fügen Sie ein Steuerelement hinzu, und lassen sie es ausgewählt).
   
    In diesem Thema [fügen Sie ein Label- und ein Slider-Steuerelement hinzu](add-configure-controls.md), legen die **Text**-Eigenschaft des Label-Steuerelements auf **Slider1.Value** fest, und wählen dann das Slider-Steuerelement aus.
2. Klicken oder tippen Sie im rechten Bereich auf **Regeln**, und klicken oder tippen Sie dann auf **Neue Regel**.
   
    ![Neue Regel erstellen](./media/working-with-rules/new-rule.png)
   
    Wenn Sie ein Steuerelement auswählen, für das bereits eine oder mehrere Regeln definiert wurden, können Sie diese bearbeiten, indem Sie darauf klicken oder tippen.  

## <a name="add-a-condition"></a>Bedingung hinzufügen
Eine Bedingung ist ein Ausdruck, der als „true“ oder „false“ ausgewertet wird, z.B. die Bedingung, dass ein Wert größer als 70 ist. Sie können den Ausdruck anhand einer Vorlage oder vollständig neu schreiben, und Sie können den Ausdruck gemäß der Anleitung auf der Benutzeroberfläche (IntelliSense) anpassen.

1. Klicken oder tippen Sie auf **Bedingung hinzufügen**, und klicken Sie dann auf eine Vorlage oder auf **Benutzerdefinierte Bedingung**.
   
    In diesem Thema klicken oder tippen Sie auf **Größer als**.
   
    ![Bedingung hinzufügen](./media/working-with-rules/rule-conditions.png)
2. Definieren Sie am Ende des Ausdrucks, wann die Regel angewendet wird.
   
    In diesem Thema verwenden Sie den folgenden Ausdruck:  <br>**Value(Slider1.Value) > 70**
   
    **Hinweis:** Zum Zeitpunkt der Erstellung dieses Dokuments gilt, dass Sie die Eigenschaft des im Vergleich verwendeten Steuerelements angeben müssen. In zukünftigen Versionen leitet PowerApps möglicherweise allgemeine Eigenschaften des Steuerelements (z.B. **Text** oder **Value**) ab.

## <a name="add-an-action"></a>Aktion hinzufügen
Aktionen definieren, was geschieht, wenn die Regel angewendet wird. In PowerApps können Aktionen automatisch basierend auf den Änderungen erstellt werden, die Sie an Steuerelementen vornehmen.

1. Klicken oder tippen Sie auf **Aktionen definieren**.
   
    ![Aktionen definieren](./media/working-with-rules/rule-define-actions.png)
2. Klicken oder tippen Sie im Bestätigungsdialogfeld auf **Los geht's**, damit PowerApps Ihre nächste(n) Änderung(en) als eine oder mehrere Aktionen aufzeichnet.
3. Konfigurieren Sie ein oder mehrere Steuerelemente entsprechend Ihren Erwartungen für den Fall, dass die Bedingung zutrifft.
   
    In diesem Thema ändern Sie die Farbe der Bezeichnung.
   
    ![Eigenschaften erfassen](./media/working-with-rules/rule-capture-properties.png)
4. (Optional) Überprüfen Sie die Änderungen, indem Sie auf **Aktionen anzeigen** tippen oder klicken.
   
    ![Aktionen überprüfen](./media/working-with-rules/rule-review-actions.png)
5. Wenn Sie alle Aktionen hinzugefügt haben, klicken oder tippen Sie auf **Fertig**.
6. Überprüfen Sie die Bedingung und Aktionen für die Regel, und klicken oder tippen Sie dann auf **Fertig**, um sie zu speichern.
   
    ![Regel überprüfen](./media/working-with-rules/rule-review.png)

## <a name="test-the-rule"></a>Testen der Regel
1. Drücken Sie F5 (oder klicken Sie rechts oben auf die Wiedergabeschaltfläche), um die App im Vorschaumodus anzuzeigen.
   
    ![Vorschau öffnen](./media/working-with-rules/open-preview.png)
2. Sorgen Sie dafür, dass die von Ihnen angegebene Bedingung zutrifft, und vergewissern Sie sich dann, dass die Aktionen wie erwartet ausgeführt werden.
   
    In diesem Thema schieben Sie den Schieberegler auf einen Wert, der größer als 70 ist. Vergewissern Sie sich dann, dass sich die Farbe des Bezeichnungstexts ändert.

## <a name="known-limitations"></a>Bekannte Einschränkungen
Zum Zeitpunkt der Erstellung dieses Dokuments:

* Regeln können nicht umbenannt werden.
* Sie können die **ThisItem**-Eigenschaft eines Formulars oder Katalogs nicht als Teil einer Bedingung angeben.

