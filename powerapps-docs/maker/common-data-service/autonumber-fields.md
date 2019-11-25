---
title: Felder für automatische Nummerierung in Common Data Service | MicrosoftDocs
description: Erfahren Sie, wie Sie Felder mit automatischer Nummerierung erstellen, verwalten und verwenden
keywords: ''
ms.date: 02/26/2019
ms.service: powerapps
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: daemelia
ms.assetid: ''
ms.author: daemelia
manager: kvivek
ms.reviewer: Mattp123
ms.suite: ''
ms.tgt_pltfrm: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5735e425dd0d19dd5e52603433d56cc37e897cd6
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2758387"
---
# <a name="autonumber-fields"></a>Felder mit automatischer Nummerierung

Felder mit automatischer Nummerierung sind Felder, die automatisch alphanumerische Zeichenfolgen erstellen, wenn sie erstellt werden. Ersteller können das Format dieser Felder nach ihren Wünschen anpassen und sich dann darauf verlassen, dass vom System passende Werte erstellt werden, mit denen die Felder bei Laufzeit befüllt werden.

Obwohl Felder mit automatischer Nummerierung formell nur Textfelder mit zusätzlichen erstellten Funktionen sind, vereinfacht [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) dieses Konzept, indem **Automatische Nummerierung** als eindeutiger Datentyp in der **Text**-Kategorie eingeblendet wird. Beachten Sie unbedingt, dass der [klassische Lösungs-Explorer](use-solution-explorer.md#classic-solution-explorer) das Erstellen oder Verwaltung von Felder mit automatischer Nummerierung nicht unterstützt.

Wenn Sie ein Feld mit automatischer Nummerierung erstellen möchten, führen Sie die gleichen Schritte aus, um [ein Feld zu erstellen](create-edit-field-portal.md#create-a-field) und wählen Sie einfach **Automatische Nummerierung** aus dem **Datentyp**-Dropdownlistenfeld aus. 

Sie können die Funktion zur automatischen Nummerierung ggf. auch auf einem vorhandenen Textfeld aktivieren, indem Sie in das Feld öffnen und **Automatische Nummerierung**aus den **Datentyp**-Dropdownlistenfeld auswählen. Dem entsprechend kann die Funktion zur automatischen Nummerierung jederzeit deaktiviert werden, indem Sie das Feld öffnen und eine andere Option in der **Datentyp**-Dropdownlistenfunktion auswählen.

> [!NOTE]
>Werte der automatischen Nummerierung werden von der Datenbank beim Starten des Datensatzes vorab ausgewählt. Wenn ein Datensatz gestartet, dann aber storniert wird, wird die zugewiesene Zahl nicht verwendet. Wenn während dieser Zeit ein weiterer Datensatz mit der folgenden sequenziellen Zahl fertiggestellt wird, können Lücken in der automatischen Nummerierung von Datensätzen auftreten.

## <a name="autonumber-types"></a>Typen der automatischen Nummerierung

Um die Erstellung von Feldern mit automatischer Nummerierung zu vereinfachen, gibt es einige vordefinierte Typen der automatischen Nummerierung, mit denen die häufigsten Szenarien abgedeckt werden. 

### <a name="string-prefixed-number"></a>Zahl mit vorangestellter Zeichenfolge

Das häufigste Format der automatischen Nummerierung ist eine einfache Zahl mit vorangestellter Zeichenfolge. Wenn dieser Typ ausgewählt wird, besteht die automatische Nummer aus einer inkrementierenden Zahl mit einer optionalen Zeichenfolge die konstant vorangestellt wird. Beispielsweise kann eine Zahl mit vorangestellter Zeichenfolge mit dem Präfix *Contoso* Datensätze wie *Contoso-1000*, *Contoso-1001*, *Contoso-1002* usw. generieren.

### <a name="date-prefixed-number"></a>Zahl mit vorangestelltem Datum

Ein anderes übliches Format für automatisches Nummerieren ist eine Zahl mit vorangestelltem Datum. Wenn dieser Typ ausgewählt wird, besteht die automatische Nummer aus einer inkrementierenden Zahl mit einem vorangestellten formatierten Datum. Der Datumsteil des Datensatzes stellt das aktuelle Datum und die Uhrzeit (in UTC-Zeit) dar, zu dem der Datensatz erstellt wurde. Es stehen verschiedene Datumsformate zur Auswahl.
Beispielsweise kann eine Zahl mit vorangestelltem Datum solche Datensätze wie *2019-26-02-1000*, *2019-27-02-1000*, *2019-28-02-1000* usw. erstellen, je nach aktuellem Datum und ausgewähltem Format.

### <a name="custom"></a>Benutzerdefiniert

Für erweiterte Hersteller mit bestimmten Anwendungsfällen bieten wir die Möglichkeit, das gewünschte Format eines für Felds mit automatisierter Nummerierung vollständig anzupassen. Das Format kann aus ein Zeichenfolgenkonstanten,automatisch inkrementiert Zahlen, formatierten Daten oder zufälligen alphanumerischen Sequenzen bestehen.
Ausführliche Informationen dazu, wie benutzerdefinierte Formate definiert werden, finden Sie unter [AutoNumberFormat-Optionen](https://docs.microsoft.com/dynamics365/customer-engagement/developer/create-auto-number-attributes#autonumberformat-options).

## <a name="seed-values"></a>Startwerte

Der Startwert eines Felds für automatisierte Nummerierung ist die Startzahl, die für den Zahlenteil des Formats verwendet wird. Wenn ein Feld für automatisierte Nummerierung beispielsweise Datensätze wie *Contoso-1000*, *Contoso-1001*, *Contoso-1002* usw. erstellen soll, ist der gewünschte Startwert 1000, da Ihre Zahlenreihenfolge mit diesem Wert beginnt. Felder für automatisierte Nummerierung haben einen Standardstartwert von 1000, aber Sie können bei Bedarf einen benutzerdefinierten Startwert festlegen. 


> [!IMPORTANT]
> Festlegen des Startwerts ändert nur den aktuellen Zahlenwert für das angegebene Attribut in der aktuellen Umgebung. Der Startwert ist nicht in einer Lösung enthalten, wenn er in einer anderen Umgebung importiert ist. 

## <a name="create-an-autonumber-field"></a>Erstellen eines Felds mit automatisierter Nummerierung
  
1.  Melden Sie sich beim [PowerAppsPortal](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.
  
2.  Erweitern Sie im linken Bereich **Daten** und wählen Sie **Entitäten** aus.
  
3.  Wählen Sie die Entität aus, zu der Sie ein Feld mit automatisierter Nummerierung hinzufügen möchten, und wählen Sie dann die Registerkarte **Felder** aus.
  
4.  Wählen Sie das Feld **Hinzufügen** in der Symbolleiste aus.  
  
5.  Geben Sie im rechten Bereich einen **Anzeigenamen** ein und wählen Sie **Automatisiert Nummerieren** als **Datentyp** aus.

    > [!div class="mx-imgBorder"] 
    > ![](media/create-autonumber-field.png "Create an autonumber field")
  
6. Legen Sie optionalen Felder nach Bedarf fest. Weitere Informationen: [Erstellen und Bearbeiten von Feldern](create-edit-field-portal.md#create-a-field)

7. Wählen Sie einen Tayp für automatisierte Nummerierung aus oder behalten Sie die Standardoption **Zahl mit vorangestellter Zeichenfolge** bei.

8. Passen Sie ein Startwert an oder behalten Sie den Standardwert **1000** bei.

9. **Fertig** auswählen

## <a name="see-also"></a>Siehe auch
 [Erstellen und Bearbeiten von Feldern für Common Data Service mit dem PowerApps-Portal](create-edit-field-portal.md)
