---
title: SetFocus-Funktion | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax, für die Funktion "SetFocus" in powerapps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 08/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: fce0148e77432aa136a6279eb7fb69c0ca3b0846
ms.sourcegitcommit: de77b6d5f77e84961fff9a399622ba8eeb48d4c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70037094"
ms.PowerAppsDecimalTransform: true
---
# <a name="setfocus-function-in-powerapps"></a>SetFocus-Funktion in powerapps
Verschiebt den Eingabefokus auf ein bestimmtes Steuerelement. 

## <a name="description"></a>Beschreibung
Die **SetFocus** -Funktion gibt einem Steuerelement den Eingabefokus.  Die Tastatureingaben des Benutzers werden dann von diesem Steuerelement empfangen, sodass Sie Sie in ein Texteingabe-Steuerelement eingeben oder die *Eingabe* Taste verwenden können, um eine Schaltfläche auszuwählen.  Der Benutzer kann auch die *Tab* -Taste, die Fingereingabe, die Maus oder eine andere Geste verwenden, um den Eingabefokus selbst zu verschieben. Das Verhalten der *Tab* -Taste wird durch die [ **TabIndex** -Eigenschaft](../controls/properties-accessibility.md)gesteuert.

Verwenden Sie die **SetFocus** -Funktion, um den Fokus festzulegen, wenn (jedes mit einem Beispiel unten):
- ein neu bereit gelegtes oder aktiviertes Eingabe Steuerelement, das den Benutzer dazu führt, was als nächstes Eintritt und für schnellere Dateneingaben.
- ein Formular wird überprüft, um den Fokus zu haben und das angreifende Eingabe Steuerelement für die schnelle Auflösung anzuzeigen.
- ein Bildschirm wird angezeigt, um das erste Eingabe Steuerelement mit der **onvisible** -Eigenschaft des [**Bildschirms**](../controls/control-screen.md)zu fokussieren.

Das Steuerelement mit Fokus kann sich basierend auf den Eigenschaften [**focusedbordercolor**](../controls/properties-color-border.md) und [**focusedborderdicke**](../controls/properties-color-border.md) visuell unterscheiden.

## <a name="limitatoins"></a>Limits

**SetFocus** kann nur mit verwendet werden:
- [**Button**](../controls/control-button.md) -Steuerelement
- [**Symbol**](../controls/control-shapes-icons.md) Steuerelement
- [**Image**](../controls/control-image.md) -Steuerelement
- [**Label**](../controls/control-text-box.md)-Steuerelement (Bezeichnung)
- [**TextInput**](../controls/control-text-input.md) -Steuerelement

Der Fokus kann nicht auf Steuerelemente festgelegt werden, die sich [**in einem Katalog**](../controls/control-gallery.md) -Steuerelement, [**Bearbeitungs Formular**](../controls/control-form-detail.md) Steuer [Element oder Komponente](../create-component.md)befinden.  **SetFocus** kann mit einem-Steuerelement in einem scrollbale-Bildschirm verwendet werden.

Sie können den Fokus nur auf Steuerelemente auf dem gleichen Bildschirm festlegen wie die Formel, die den **SetFocus** -Befehl enthält.

Der Versuch, den Fokus auf ein Steuerelement festzulegen, dessen [**Display Mode**](../controls/properties-core.md) -Eigenschaft auf " **deaktiviert** " festgelegt ist, hat keine Auswirkungen.  Der Fokus bleibt unverändert.

Unter Apple IOS wird die weiche Tastatur nur automatisch angezeigt, wenn **SetFocus** durch eine direkte Benutzeraktion initiiert wurde.  Wenn Sie z. b. über die **onselect** -Eigenschaft einer Schaltfläche aufrufen, wird die weiche Tastatur angezeigt, während der Aufruf über die **onvisible** eines Bildschirms nicht erfolgt. 

Sie können **SetFocus** nur in [Verhaltens Formeln](../working-with-formulas-in-depth.md)verwenden.

## <a name="syntax"></a>Syntax
**SetFocus** ( *Steuer* Element)

* *Steuerelement* – Erforderlich.  Das Steuerelement, das dem Eingabefokus zugewiesen werden soll.

## <a name="examples"></a>Beispiele

### <a name="focus-on-a-newly-exposed-or-enabled-input-control"></a>Fokus auf ein neu bereit gelegtes oder aktiviertes Eingabe Steuerelement

Viele Einkaufswagen ermöglichen es dem Kunden, die Lieferadresse als Abrechnungsadresse zu verwenden, wodurch die Notwendigkeit verringert wird, die gleichen Informationen zweimal einzugeben.  Wenn eine andere Abrechnungsadresse gewünscht wird, werden die Eingabefelder für die Abrechnungs Adress Text-Eingabe aktiviert, und es ist hilfreich, den Kunden diese neu aktivierten Steuerelemente zur schnelleren Dateneingabe zu leiten.  

![Animation, bei der die Verwendung einer benutzerdefinierten Abrechnungsadresse verwendet wird, wobei der Fokus in das Eingabe Steuerelement des Abrechnungs namens verschoben wird, wobei die automatische Synchronisierung mit den Versand Adressierung deaktiviert wird](media/function-setfocus/shipping-billing.gif)

Hier sind viele Formeln vorhanden, aber die, die den Fokus verschiebt, ist die **onuncheck** -Eigenschaft des Kontroll **Kästchen** -Steuer Elements:

```powerappa-dot
SetFocus( BillingName ) 
```

Die *Tab* -Taste kann auch verwendet werden, um den Fokus schnell von einem Feld in ein anderes zu verschieben.  Zur besseren Veranschaulichung wurde die *Tab* -Taste in der Animation nicht verwendet.

So erstellen Sie dieses Beispiel
1. Erstellen Sie eine neue APP.
1. Fügen Sie [ **Label** ](../controls/control-text-box.md) -Steuerelemente mit dem Text "Shipping Address", "Name:", "Address:", "Rechnungsadresse", "Name:" und "Address:" hinzu, und positionieren Sie Sie wie in der Animation gezeigt.
1. Fügen Sie ein Steuerelement [ **Text Eingabe** ](../controls/control-text-input.md) hinzu, und benennen Sie es **shippingname**um.
1. Fügen Sie ein Steuerelement [ **Text Eingabe** ](../controls/control-text-input.md) hinzu, und benennen Sie es **shippingaddress**um.
1. Fügen Sie ein [Kontroll **Kästchen** -Steuer](../controls/control-check-box.md) Element hinzu, und benennen Sie **syncadressen**um.
1. Legen Sie die **Text** -Eigenschaft dieses Steuer Elements auf `"Use Shipping address as Billing address"`die Formel fest.
1. Fügen Sie ein Steuerelement [ **Text Eingabe** ](../controls/control-text-input.md) hinzu, und benennen Sie es **billingname**um.
1. Legen Sie die **Standard** Eigenschaft für dieses Steuerelement auf `ShippingName`die Formel fest.
1. Legen Sie die **Display Mode** -Eigenschaft dieses Steuer Elements auf die `If( SyncAddresses.Value; DisplayMode.View; DisplayMode.Edit )`Formel fest.  Dadurch wird dieses Steuerelement basierend auf dem Zustand des Kontrollkästchen-Steuer Elements automatisch aktiviert oder deaktiviert.
1. Fügen Sie ein Steuerelement [ **Text Eingabe** ](../controls/control-text-input.md) hinzu, und benennen Sie es **billingaddress**um.
1. Legen Sie die **Standard** Eigenschaft für dieses Steuerelement auf `ShippingAddress`die Formel fest.
1. Legen Sie die **Display Mode** -Eigenschaft dieses Steuer Elements auf die `If( SyncAddresses.Value; DisplayMode.View; DisplayMode.Edit )`Formel fest.  Dadurch wird dieses Steuerelement basierend auf dem Zustand des Kontrollkästchen-Steuer Elements automatisch aktiviert oder deaktiviert.
1. Legen Sie die **Standard** Eigenschaft des Kontrollkästchens auf `true`die Formel fest.  Dadurch wird standardmäßig die Abrechnungsadresse verwendet, um den gleichen Wert wie die Lieferadresse zu verwenden.
1. Legen Sie die **OnCheck** -Eigenschaft des Kontrollkästchens `Reset( BillingName );; Reset( BillingAddress )`auf die Formel fest.  Wenn sich der Benutzer für die Synchronisierung von Versand-und abrechnungsadressen entscheidet, werden alle Benutzereingaben in den Abrechnungs Adressfeldern gelöscht, sodass die **Standard** Eigenschaften der einzelnen Werte aus den entsprechenden Versand Adressfeldern abgerufen werden können.
1. Legen Sie die Eigenschaft **onuncheck** des Kontrollkästchens auf `SetFocus( BillingName )`die Formel fest.  Wenn sich der Benutzer für eine andere Abrechnungsadresse entscheidet, wird der Fokus auf das erste Steuerelement in der Abrechnungsadresse verschoben.  Die Steuerelemente wurden bereits aufgrund ihrer **DisplayMode** -Eigenschaften aktiviert.

### <a name="focus-on-validation-issues"></a>Schwerpunkt auf Validierungs Problemen

> [!NOTE]
> Obwohl es sich bei diesem Beispiel um ein **Bearbeitungs Formular** -Steuerelement handelt, wird " **SetFocus** " noch nicht von diesem Steuerelement unterstützt.  Stattdessen verwendet dieses Beispiel einen Bild lauffähigen Bildschirm zum Hosten der Eingabe Steuerelemente.

Wenn Sie ein Formular validieren, kann es hilfreich sein, eine Meldung nicht nur anzuzeigen, wenn ein Problem vorliegt, sondern auch den Benutzer in das Feld zu bringen, das eine Beschädigung verursacht.  Dies kann besonders hilfreich sein, wenn das betreffende Feld vom Bildschirm entfernt und nicht sichtbar ist.

![Eine Animation, bei der ein Dateneingabe Formular überprüft und nicht nur eine Meldung angezeigt wird, sondern auch der Eingabefokus auf das angreifende Eingabe Steuerelement festgelegt wird, auch wenn der Bildschirm vom Bildschirm entfernt wird.](media/function-setfocus/scrollable-screen.gif)

In dieser Animation wird die Schaltfläche Überprüfung wiederholt gedrückt, bis alle Felder ordnungsgemäß ausgefüllt wurden.  Beachten Sie, dass der Mauszeiger nicht vom oberen Bildschirmrand nach unten verschoben wird.   Stattdessen hat die **SetFocus** -Funktion den Eingabefokus auf das Steuerelement verschoben, das mit dieser Formel Aufmerksamkeit erfordert:

```powerapps-comma
If( IsBlank( Name ); 
        Notify( "Name requires a value"; Error );; SetFocus( Name );
    IsBlank( Street1 ); 
        Notify( "Street Address 1 requires a value"; Error );; SetFocus( Street1 );
    IsBlank( Street2 ); 
        Notify( "Street Address 2 requires a value"; Error );; SetFocus( Street2 );
    IsBlank( City ); 
        Notify( "City requires a value"; Error );; SetFocus( City );
    IsBlank( County ); 
        Notify( "County requires a value"; Error );; SetFocus( County );
    IsBlank( StateProvince ); 
        Notify( "State or Province requires a value"; Error );; SetFocus( StateProvince );
    IsBlank( PostalCode ); 
        Notify( "Postal Code requires a value"; Error );; SetFocus( PostalCode );
    IsBlank( Phone ); 
        Notify( "Contact Phone requires a value"; Error );; SetFocus( Phone );
    Notify( "Form is Complete"; Success )
)
```

So erstellen Sie dieses Beispiel
1. Erstellen Sie eine neue, leere Phone-app.
1. Wählen Sie im Menü **Einfügen** die Option **neuer Bildschirm**aus, und wählen Sie dann **scrollfähig**aus.
1. Fügen Sie im mittleren Bereich des Bildschirms **Text Eingabe** -Steuerelemente hinzu, und nennen Sie Sie **Name**, **Street1**, **Street2**, **City**, **County**, **StateProvince**, **PostalCode**und **Phone**. Fügen Sie oberhalb jeder **Bezeichnung** Steuerelemente hinzu, um die Felder zu identifizieren.  Möglicherweise müssen Sie die Größe des Abschnitts ändern, wenn er nicht lang genug ist, um alle Steuerelemente zu erfüllen.
1. Fügen Sie am oberen Rand des Bildschirms oberhalb des Bild lauffähigen Abschnitts ein Häkchensymbol- [ Steuer](../controls/control-shapes-icons.md) Element hinzu.  
1. Legen **Sie die onselect** -Eigenschaft des Symbol-Steuer Elements `If( IsBlank( ...` auf die oben angegebene Formel fest.

### <a name="focus-when-displaying-a-screen"></a>Fokus beim Anzeigen eines Bildschirms

> [!NOTE]
> Obwohl es sich bei diesem Beispiel um ein **Bearbeitungs Formular** -Steuerelement handelt, wird "unversöhnutnatley **SetFocus** " noch nicht von diesem Steuerelement unterstützt.  Stattdessen verwendet dieses Beispiel einen Bild lauffähigen Bildschirm zum Hosten der Eingabe Steuerelemente.

Ähnlich wie beim verfügbar machen eines Eingabe Steuer Elements ist es hilfreich, das erste Eingabe Steuerelement auf einen schnelleren Dateneintrag zu fokussieren, wenn ein Dateneingabe-Bildschirm angezeigt wird.

![Eine Animation, die einen parallelen Vergleich der Verwendung von SetFocus und deren Verwendung beim Anzeigen eines Dateneingabe Bildschirm anzeigt.](media/function-setfocus/visible-setfocus.gif)

In dieser Animation verwendet der Bildschirm Dateneingabe auf der linken Seite nicht **SetFocus**.  Bei der Anzeige hat kein Eingabe Steuerelement den Fokus, sodass der Benutzer mit der Tab-Taste, dem Fingerabdruck, der Maus oder einem anderen Mittelpunkt das **namens** Feld fokussieren kann, bevor ein Wert eingegeben werden kann.

Auf der rechten Seite haben wir genau dieselbe APP, bei der die **onvisible** -Eigenschaft des Dateneingabe Bildschirm auf diese Formel festgelegt ist:

```powerapps-comma
SetFocus( Name )
```

Dadurch wird der Fokus automatisch auf das Feld **Name** festgelegt.  Der Benutzer kann sofort mit der Eingabe und der Tabstopps zwischen den Feldern beginnen, ohne dass eine vorherige Aktion erforderlich ist.

So erstellen Sie dieses Beispiel
1. Erstellen Sie die oben genannte App "Fokus auf Validierungs Probleme".
1. Legen Sie auf diesem Bildschirm die **onvisible** -Eigenschaft auf `SetFocus( Name )`die Formel fest.
1. Fügen Sie einen zweiten Bildschirm hinzu.
1. Hinzufügen eines [ **Schalt** ](../controls/control-button.md)Flächen-Steuer Elements
1. Legen **Sie die onselect** -Eigenschaft dieses Steuer Elements auf `Navigate( Screen1 )`die Formel fest.
1. Vorschau der APP auf diesem Bildschirm anzeigen.  Klicken Sie auf die Schaltfläche.  Die **onvisible** -Formel wird ausgewertet, und das **Name** -Feld wird automatisch im Fokus.
