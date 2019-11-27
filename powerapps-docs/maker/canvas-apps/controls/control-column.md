---
title: 'Spalten-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Dieses Thema enthält Informationen zum Spalten-Steuerelement in Microsoft PowerApps.
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/05/2017
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 21bc7e025515397fa853e5de7f2df574a3768935
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2019
ms.locfileid: "73650643"
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


## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit
### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe
* **DisplayName** muss vorhanden sein.
