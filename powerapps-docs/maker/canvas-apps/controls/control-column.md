---
title: 'Spalten-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Dieses Thema enthält Informationen zum Spalten-Steuerelement in Microsoft PowerApps.
services: powerapps
documentationcenter: na
author: jasongre
manager: kfend
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 06/05/2017
ms.author: kfend
ms.openlocfilehash: 0e9c04c4786ff4cee11d7aae75245054e93391fa
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="column-control-in-powerapps"></a>Spalten-Steuerelement in PowerApps
Dient zum Anzeigen eines einzelnes Felds in einem [**Datentabellen**](control-data-table.md)-Steuerelement.

## <a name="description"></a>Beschreibung
Das [**Datentabellen**](control-data-table.md)-Steuerelement zeigt ein Dataset in einem Tabellenformat. Jede Spalte in diesem Tabellenformat wird durch ein **Spalten**-Steuerelement dargestellt. Das **Spalten**-Steuerelement bietet Eigenschaften, mit deren Hilfe der Autor der App das Aussehen und Verhalten der Spalte anpassen kann.

## <a name="capabilities"></a>Funktionen
### <a name="now-available"></a>Jetzt verfügbar
* Ändern der Breite eines **Spalten**-Steuerelements.
* Ändern des Texts eines **Spalten**-Steuerelements.
* Navigieren durch Klicken oder Tippen auf einen Wert im **Spalten**-Steuerelement.

### <a name="not-yet-available"></a>Noch nicht verfügbar
* Anpassen des Formats eines **Spalten**-Steuerelements.

### <a name="known-issues"></a>Bekannte Probleme
* Die **Visible**-Eigenschaft funktioniert noch nicht.

## <a name="properties"></a>Eigenschaften
* **DisplayName**: Der Text, der in der Kopfzeile der Spalte angezeigt wird.
  
  > [!NOTE]
  > Diese Eigenschaft wird in Kürze in **HeaderText** umbenannt.
  > 
  > 
* **IsHyperlink**: Ein Wert, der angibt, ob die Daten in der Spalte unterstrichen werden sollen, um anzugeben, dass es sich um einen Link handelt.
* [**Width**](properties-size-location.md): Der Abstand zwischen dem linken und rechten Rand eines **Spalten**-Steuerelements.

## <a name="examples"></a>Beispiele
### <a name="resize-a-column"></a>Ändern der Größe einer Spalte
1. Erstellen Sie eine leere Tablet-App.
2. Klicken oder tippen Sie auf der Registerkarte **Einfügen** auf **Datentabelle**,und ändern Sie die Größe des **Datentabellen**-Steuerelements so, dass es den gesamten Bildschirm einnimmt.
3. Klicken oder tippen Sie im rechten Bereich auf den Abwärtspfeil neben **Keine Datenquelle ausgewählt**, und klicken oder tippen Sie dann auf **Datenquelle hinzufügen**.
4. Klicken oder tippen Sie in der Liste der Verbindungen auf die Verbindung für Ihre Common Data Service-Datenbank.
5. Klicken oder tippen Sie in der Liste der Entitäten auf **Account** (Kunde) und dann auf **Verbinden**.
   
    Das **Datentabellen**-Steuerelement wird initialisiert und zeigt eine Gruppe von Standardfeldern.
6. Klicken oder tippen Sie auf die Spalte **Vollständiger Name**.
   
    ![Ausgewähltes Spalten-Steuerelement](./media/control-column/pre-resize-column.png)
7. Ziehen Sie den Adorner auf der rechten Seite, um die Größe des Felds zu ändern.
   
    ![Größe des Spalten-Steuerelements geändert](./media/control-column/post-resize-column.png)
