---
title: Richten Sie das Zeitskala-Steuerelement (Abschnitt) ein in PowerApps | MicrosoftDocs
description: Erfahren Sie , wie Sie das Zeitskala-Steuerelement (Abschnitt) in PowerApps einrichten
ms.date: 03/10/2020
ms.service: powerapps
author: kabala123
ms.assetid: 7F495EE1-1208-49DA-9B02-17855CEB2FDF
ms.author: kabala
manager: shujoshi
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 272eab58ed332f87a49eae275a98e4a4bdc69cc6
ms.sourcegitcommit: a02b20113164acb11955d27ef4ffa421ee0fba9d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "3114308"
---
# <a name="set-up-timeline-section-control"></a>Zeitskala Abschnitt einrichten (Steuerung)

Die Aktivitäten, die Sie in der Zeitskala verwenden, um die gesamte Kommunikation mit einem Kunden oder Kontakt zu verfolgen, können an Ihre geschäftlichen oder organisatorischen Anforderungen angepasst werden.

  > [!div class="mx-imgBorder"]
  > ![Zeitskala Ansicht der Aktivitäten in PowerApps](../../user/media/TimelineViewOfActivity.png "Zeitskala-Ansicht der Aktivitäten in PowerApps")

  1. Datensätze suchen
  2. Notizen machen
  3. Infos und Aktivitäten hinzufügen
  4. Filter
  5. Weitere Befehle
  6. Aktivitätsstatus
  7. Aktivitäts-Symbol
  8. Datum und Uhrzeit

Weitere Informationen finden Sie unter [Fügen Sie der Zeitskala einen Termin, eine E-Mail, einen Telefonanruf, eine Notiz oder eine Aufgabenaktivität hinzu](../../user/add-activities.md).

Die Anpassung ist in folgende Bereiche unterteilt:

- Modul
- Aktivitätstyp
- Feld

## <a name="customize-modules"></a>Module anpassen

Die Module sind Aktivitäten, Beiträge und Notizen. Als Anpassungsprogramm können Sie auswählen, welche Module Sie den Benutzern gemäß Ihren Geschäftsanforderungen anzeigen möchten.

1.  Melden Sie sich in Ihrer `https://<YourOrgURL>.dynamics.com/apps`-Umgebung an.

2.  Öffnen Sie eine modellgesteuerte App und wählen Sie danach in der Befehlsleiste **Einstellungen** ![Einstellungen](../model-driven-apps/media/powerapps-gear.png "Einstellungen") > **Erweiterte Einstellungen** aus.

3.  Gehen Sie zu **Einstellungen** > **Anpassung** > **System anpassen**. Die Seite „Projektmappen-Explorer“ wird in einem neuen Browserfenster geöffnet. 

4.  Erweitern Sie **Entitäten** unter **Komponenten** im Standardlösungsbereich.

5.  Wählen Sie eine Entität, und wählen Sie **Formulare** aus. Wählen Sie beispielsweise die Entität **Konto** aus.

6.  Wählen Sie den Datensatz **Konto für interaktive Funktionen** aus, der ein **Haupt**-Formulartyp ist. Das Formular **Konto für Interaktive Funktionen** wird in einem neuen Browserfenster geöffnet.

   > [!div class=mx-imgBorder] 
   > ![Wählen Sie das Entitätsformular mit interaktiven Funktionen im Namen aus](media/account-interactive-experience.png "Wählen Sie das Entitätsformular mit interaktiven Funktionen im Namen aus")

   Für Einheitliche Oberfläche müssen Sie den Formularnamen verwenden, der `<Entity> for Interactive experience` enthält. Die Formularnamen für andere Entitäten lauten wie folgt:

   | Entität | Name |
   |--------------------------|----------------------------------|
   | Firma | Firma für interaktive Funktionen |
   | Anfrage | Anfrage für interaktive Funktionen |
   | Kontakt | Kontakt für interaktive Funktionen |

7.  Doppelklicken Sie auf das Feld **Unterhaltungsregisterkarten** im Abschnitt **Zeitskala**. Der Dialog **Eigenschaften der Registerkarte „Aktivitäten“** wird angezeigt.

    > [!div class=mx-imgBorder] 
    > ![Machen Sie einen Doppelklick auf das Feld im Social Media-Bereich](media/timeline-conversation-tabs-field.png "Machen Sie einen Doppelklick auf das Feld im Social Media-Bereich")   

8.  Wählen Sie die Option **Ausgewählte anzeigen** für das Feld **Zeigen Sie diese Module** im Container **Filtern nach** aus.

9.  Wählen Sie die Module aus, die Sie dem Benutzer anzeigen möchten. Wählen Sie nur die Module aus, die von Ihrer Organisation benötigt werden.

10. Geben Sie im Feld Folgendes an **Zusätzliche Optionen** Container.


    | Feld/Optionen | Beschreibung | Wert |
    |------------------------------------------|--------------------------------------------------------------|---------------------------|
    | Standardmodul für die Erstellungsumgebung | Wählen Sie das Modul aus, für das die Standarderstellungserfahrung in der Zeitleiste verwendet werden soll. <br><br> Der Standardwert ist **Hinweise**.  | Hinweise |
    | Bereich „Filter“ anzeigen | Aktivieren Sie das Kontrollkästchen, wenn Sie das Filtersymbol für die Benutzer anzeigen möchten. Wenn Sie das Kontrollkästchen leer lassen, werden keine Filter für die Benutzer angezeigt. |  |
    | Bereich „Filter“ standardmäßig erweitern | Aktivieren Sie standardmäßig das Kontrollkästchen, wenn Sie das Filterfenster im erweiterten Modus anzeigen möchten. <br><br> **Hinweis:** Wenn die Zeitskala in mehr als einer Spalte angezeigt wird, wird der Filterbereich als Spalte neben den Zeitskalaeinträgen angezeigt. Obwohl Sie das Kontrollkästchen in den Zeitskalakonfigurationen **Filterbereich standardmäßig erweitern** deaktiviert haben, wir der Filterbereich Ihren Agents immer angezeigt.|
    | Sort | Wählen Sie die Sortierreihenfolge aus, nach der die Datensätze auf der Zeitachse angezeigt werden. Die Sortierung basiert auf dem Feld, das Sie für Aktivitäten auswählen. Wenn für den Beitrag, die Notizen oder die Aktivität kein Feld vorhanden ist, erfolgt die Sortierung anhand dem Feld **Zuletzt aktualisiert**. <br><br> Die Standardsortierreihenfolge ist **Absteigend**.  <br><br> **Hinweis:** Die Änderung der Sortierreihenfolge ändert nicht die im Zeitleisten-Steuerelement visualisierte Zeiteigenschaft. Zur Anpassung des Zeitleistenformulars siehe [Anpassen des Kartenformulars](#customize-the-card-form).  | Absteigend |
    | Ergebnisanzahl | Die maximale Anzahl von Datensätzen, die auf der Zeitskala angezeigt werden, bevor Sie die Option auswählen **Mehr**. Bei jeder Auswahl der Option **Mehr** zeigt die Zeitskala die konfigurierte Anzahl von Datensätzen. Sie können den Wert 1 bis 50 konfigurieren. <br><br> Der Standardwert ist **10**. | 10 |

    > [!div class=mx-imgBorder] 
    > ![Richten Sie das Zeitskalamodul ein](media/timeline-module.png "richten Sie das Zeitskalamodul ein")

11. Wählen Sie **OK** aus und dann **Speichern**.

12. Wählen Sie **Veröffentlichen** aus, um die Anpassungen zu veröffentlichen.

## <a name="customize-activity"></a>Benutzerdefinierte Aktivität

Als Anpasser können Sie wählen, welche Entitäten Sie den Benutzern gemäß Ihren Geschäftsanforderungen anzeigen möchten. Um eine bessere Leistung zu erzielen, wählen Sie nur die Aktivitäten aus, die spezifisch für das Geschäft sind, und heben Sie die nicht verwendeten Aktivitäten auf.

1.  Melden Sie sich in Ihrer `https://<YourOrgURL>.dynamics.com/apps`-Umgebung an.

2.  Öffnen Sie eine modellgesteuerte App und wählen Sie dann in der Befehlsleiste **Einstellungen** ![Einstellungen](../model-driven-apps/media/powerapps-gear.png "Einstellungen") > **Erweiterte Einstellungen** aus.

3.  Gehen Sie zu **Einstellungen** > **Anpassung** > **System anpassen**. Die Seite „Projektmappen-Explorer“ wird in einem neuen Browserfenster geöffnet.  

4.  Erweitern Sie **Entitäten** unter **Komponenten** im Standardlösungsbereich.

5.  Wählen Sie eine Entität, und wählen Sie **Formulare** aus. Wählen Sie beispielsweise die Entität **Konto** aus.

6.  Wählen Sie den Datensatz **Konto für interaktive Funktionen** aus, der ein **Haupt**-Formulartyp ist. Das Formular **Konto Konto für Interaktive Funktionen** wird in einem neuen Browserfenster geöffnet.

    > [!div class=mx-imgBorder] 
    > ![Wählen Sie das Entitätsformular mit Interaktive Funktionen im Namen aus](media/account-interactive-experience.png "Wählen Sie das Entitätsformular mit interaktiven Funktionen im Namen aus")

    Für Einheitliche Oberfläche müssen Sie den Formularnamen verwenden, der `<Entity> for Interactive experience` enthält. Die Formularnamen für andere Entitäten lauten wie folgt:

    | Entität | Name |
    |--------------------------|----------------------------------|
    | Firma | Firma für interaktive Funktionen |
    | Anfrage | Anfrage für interaktive Funktionen |
    | Kontakt | Kontakt für interaktive Funktionen |

7.  Doppelklicken Sie auf das Feld **Unterhaltungsregisterkarten** im Abschnitt **Zeitskala**. Der Dialog **Eigenschaften der Registerkarte „Aktivitäten“** wird angezeigt.

    > [!div class=mx-imgBorder] 
    > ![Machen Sie einen Doppelklick im Feld Social Media-Bereich](media/timeline-conversation-tabs-field.png "Machen Sie einen Doppelklick auf das Feld im Social Media-Bereich") 

8.  Wählen Sie die Option **Ausgewählte anzeigen** für das Feld **Diese Aktivitäten anzeigen** im Container **Filtern nach** aus.

9.  Wählen Sie die Aktivitäten aus, die Sie den Benutzern anzeigen möchten.

10. Wählen Sie eine Option aus der Liste für die **Zeitachse sortieren nach** Option im Cointainer **Daten** aus. Wählen Sie zum Beispiel die **Zuletzt aktualisiert** Möglichkeit.

11. Geben Sie im Feld Folgendes an **Zusätzliche Optionen** Container.
    
    | Feld/Optionen | Beschreibung |Wert |
    |------------------------------------------|------------------------------------------------------------|-------------------|
    | Aktivitätskopfzeile anzeigen mit |  Mögliche Werte sind **Standardformat** und **Feldbezeichnungen**. <br><br> **Hinweis:** <ul><li> Wenn Sie **Standardformat** auswählen, dann sollten sie immer **Standardfelder** für das Feld **Aktivitäten anzeigen mit** auswählen. <br> ![Standardformat und Standardfelder](media/default-format-default-fields.png "Standardformat und Standardfelder") </li> <li> Wenn Sie auswählen **Feldbezeichnungen**, dann können Sie entweder **Standardfelder** oder **Kartenformular** auswählen für das Feld **Aktivitäten anzeigen mit**. <br> ![Feldbeschriftungen und Standardstartseite](media/field-label-card-form.png "Standardformat und Standardfelder") </li> <li> Wenn Sie auswählen **Standardformat** und **Kartenformular** auswählen für das Feld **Aktivitäten anzeigen mit** dann ignoriert das System den Wert **Kartenformular** und verwendet die **Standardfelder**, um die Aktivitäten anzuzeigen. </li> <ul>| Standardformat |
    | Aktivitäten erstellen mithilfe von | Wählen Sie die Formulare aus, mit denen Sie möchten, dass Benutzer Aktivitäten erstellen. Mögliche Werte sind **Schnellformular erstellen** und **Hauptformular**. | Formular für Schnellerfassung |
    | Aktivitäten anzeigen mit | Wählen Sie aus, wie Aktivitäten angezeigt werden. Mögliche Werte sind **Standardfeld** und **Kartenformular**.  Wenn Sie **Kartenformular** auswählen, dann müssen Sie ein Kartenformular für die Aktivität auswählen.  | |
    | Aktivität auswählen | Wählen Sie eine Aktivität in der Liste aus.  <br><br> **Hinweis:** Dieses Feld wird nur angezeigt, wenn Sie auswählen **Kartenformular** für das Feld **Aktivitäten anzeigen mit**.| E-Mail |
    | Kartenformular auswählen | Wählen Sie ein Kartenformular aus der Liste aus.  <br><br> **Hinweis:** Dieses Feld wird nur angezeigt, wenn Sie auswählen **Kartenformular** für das Feld **Aktivitäten anzeigen mit**. | E-Mail-Kartenformular |

    > [!div class=mx-imgBorder] 
    > ![Passen Sie das Zeitskalamodul an](media/timeline-activity1.png "Passen Sie das Zeitskalamodul an")

12. Wählen Sie **OK** aus und dann **Speichern**.

13. Wählen Sie **Veröffentlichen** aus, um die Anpassungen zu veröffentlichen.

Da das Beispiel in dieser Prozedur, das betrachtet wird **Konto** ist, wollen wir die Aktivität **E-Mail** im Steuerelement **Zeitskala** einer Kontoseite anschauen.

   | Feld | Wert |
   |---------------------------|---------------------------|
   | Aktivitätskopfzeile anzeigen mit | Standardformat |
   | Aktivitäten anzeigen mit | Standardfelder |

   > [!div class=mx-imgBorder] 
   > ![E-Mail-Aktivität in der Zeitskala](media/timeline-email-activity1.png "E-Mail-Aktivität in der Zeitskala")

   Die Standardfelder für eine E-Mail-Aktivität im reduzierten Modus enthalten Folgendes:

   1. E-Mail des \<Besitzers\>
   2. Betreff
   3. Beschreibung
   4. Aktivitätsstatus
   5. Datum und Uhrzeit

Nach dem Ändern des Formulars **E-Mail-Karte** (aus der **E-Mail** Entität) und der Aktualisierung der Optionen im Formular **Konto für Interaktive Funktionen** in der Entität **Konto** können Sie die Änderungen anzeigen.

   | Feld | Wert |
   |---------------------------|---------------------------|
   | Aktivitätskopfzeile anzeigen mit | Feldbezeichnungen |
   | Aktivitäten anzeigen mit | Kartenformular |
   | Aktivität auswählen | E-Mail |
   | Kartenformular auswählen | E-Mail-Kartenformular |

   > [!div class=mx-imgBorder] 
   > ![E-Mail-Aktivität in Zeitskala](media/timeline-email-activity2.png "E-Mail-Aktivität in Zeitskala")

   Die Standardfelder für eine E-Mail-Aktivität im reduzierten Modus enthalten Folgendes:

   1. Besitzer \<Name\>
   2. Priorität
   3. Beschreibung
   4. Aktivitätsstatus

Die Standardzeichenfolge für die Aktivitäten lautet wie folgt:

| Aktivität | Standardfelder | Bild |
|----------------|--------------------------------|------------------------------|
| Termin | `Appointment from <Owner Name>`| ![Termin](media/appointment.png "Termin") |
| E-Mail | `Email from <Owner Name>` | ![Email](media/email.png "E-Mail") |
| Telefonanruf | `Phone Call from <Owner Name>` <br> Wenn der Agent einen Anruf einleitet.| ![Telefonanruf](media/phonecall-owner.png "Telefonanruf") | 
| | `Phone Call from <Contact>` <br> Wenn der Kunde einen Anruf einleitet. | ![Telefonanruf](media/phonecall-contact.png "Telefonanruf") |
| Aufgabe | `Task modified by <Owner Name>` | ![Aufgabe](media/task.png "Aufgabe") |
| Hinweis | `Note modified by <Owner Name>` | ![Hinweis](media/note.png "Hinweis") |
| Beitrag | `Post by <Owner Name>` | ![Beitrag](media/post.png "Beitrag") |

## <a name="customize-field-sections"></a>Feldabschnitte anpassen

Im Abschnitt Zeitskala sehen Benutzer eine Karte für jede Aktivität (basierend auf den aktivierten Aktivitäten). Jede Karte zeigt bestimmte Felder im reduzierten und erweiterten Modus an. Siehe z. B. **E-Mail** Aktivitätskarte im eingeklappten, hover und erweiterten Modus. 

**E-Mail-Karte eingeklappt**: Standardmäßig befinden sich die Aktivitätskarten im eingeklappten Modus.


   > [!div class=mx-imgBorder] 
   > ![Zeitskala-Karte im reduzierten Modus](media/email.png "Zeitskala-Karte im reduzierten Modus")

**E-Mail-Karten Hover-Modus**: Wenn Sie den Mauszeiger bewegen, können Sie einige Befehle sehen, die spezifisch für jede der Aktivitätskartenarten sind.

   > [!div class=mx-imgBorder] 
   > ![Zeitskala-Karte im reduzierten Modus](media/email-hover.png "Zeitskala-Karte im reduzierten Modus")

**Zeitplankarte erweiterter Modus**: Wenn Sie auf der Karte auswählen, wird sie mit wenigen Befehlen erweitert, die für jeden der Aktivitätskartentypen spezifisch sind.

   > [!div class=mx-imgBorder] 
   > ![Erweiterter Modus in der Zeitskala-Karte](media/email-expanded.png "Erweiterter Modus in der Zeitskala-Karte")

Wenn Sie auf der Karte Felder anzeigen möchten, die für Ihr Unternehmen wichtig sind, können Sie die Felder anpassen. Sie können die Felder auch von einem Abschnitt in einen anderen Abschnitt verschieben, zum Beispiel vom Abschnitt **Header** zum Abschnitt **Detail**. Um mehr zu erfahren, gehen Sie zu [Schnellkartenformulare anpassen](#customize-the-card-form).

### <a name="customize-the-card-form"></a>Anpassen des Kartenformulars

Jedes Kartenformular hat die folgenden Abschnitte:

   | Abschnitt Anmerkung | Abschnitt Name | Spalten anzeigen |
   |------------------------------|--------------------------------------|---------------------------------------|
   | A | Farbstreifen | Der ColorStrip-Bereich wird dem Benutzer niemals angezeigt. |
   | B | Kopfzeile | Die Felder in 1 und 2 werden dem Benutzer angezeigt. |
   | C | Details | Die Felder 3, 4 und 5 werden dem Benutzer angezeigt, wobei die Felder 3 und 4 im reduzierten Modus und Feld 5 im erweiterten Modus angezeigt werden. |
   | D | Fußzeile | Abschnitt Fußzeile wird dem Benutzer niemals angezeigt. |

Zum Beispiel siehe **E-Mail-Formular**.

**E-Mail-Konfigurationanzeige**

   > [!div class=mx-imgBorder] 
   > ![E-Mail-Konfigurationkarte](media/customize-field-email.png "E-Mail-Konfigurationkarte")

**Ausgeblendeter E-Mail-Kartenmodus**

Felder **1** und **2** vom **Header** Abschnitt und Felder **3** und **4** von den **Einzelheiten** Abschnitten werden im reduzierten Modus angezeigt. Felder **3** und **4** im reduzierten Modus zeigen keine Inhalte im Rich-Text-Format an.

   > [!div class=mx-imgBorder] 
   > ![Ausgeblendete E-Mail-Karte](media/email-card-collapsed.png "Ausgeblendete E-Mail-Karte")

**E-Mail-Karte Hover-Modus**

Felder **1** und **2** aus dem Abschnitt **Kopfzeile** und Felder **3** und **4** aus dem Abschnitt **Details** werden im Hover-Modus angezeigt.

   > [!div class=mx-imgBorder] 
   > ![Ausgeblendete E-Mail-Karte](media/email-card-hover.png "Ausgeblendete E-Mail-Karte")

**Erweiterter E-Mail-Kartenmouds**

Das Feld **5** aus dem Abschnitt **Details** wird im erweiterten Modus angezeigt. Feld **3** im erweiterten Modus zeigt keine Inhalte im Rich-Text-Format an, wohingegen Feld **4** im erweiterten Modus Inhalte im Rich-Text-Format anzeigt.

   > [!div class=mx-imgBorder] 
   > ![E-Mail Karten im erweiterten Modus](media/email-card-expanded.png "E-Mail Karten im erweiterten Modus")

Um das Kartenformular anzupassen, führen Sie folgende Schritte aus:

1.  Melden Sie sich in Ihrer `https://<YourOrgURL>.dynamics.com/apps`-Umgebung an.

2.  Öffnen Sie eine modellgesteuerte App und wählen Sie dann in der Befehlsleiste **Einstellungen** ![Einstellungen](../model-driven-apps/media/powerapps-gear.png "Einstellungen") > **Erweiterte Einstellungen** aus.

3.  Gehen Sie zu **Einstellungen** > **Anpassung** > **System anpassen**. Die Seite „Projektmappen-Explorer“ wird in einem neuen Browserfenster geöffnet.  

4.  Erweitern Sie **Entitäten** unter **Komponenten** im Standardlösungsbereich.

5.  Wählen Sie eine Entität, und wählen Sie **Formulare** aus. Wählen Sie zum Beispiel die Entität **E-Mail**.

6.  Wählen Sie aus der Liste den Eintrag **E-Mail-Kartenformular**. Das Formular **E-Mail-Karte** wird in einem neuen Browserfenster geöffnet.

7.  Hinzufügen, verschieben oder löschen von Feldern. Mehr Informationen: [Felder hinzufügen, konfigurieren, verschieben oder löschen](add-move-or-delete-fields-on-form.md).

   In diesem Verfahren werden wir **E-Mail-Karte** ändern. 

   > [!div class=mx-imgBorder] 
   > ![E-Mail-Konfigurationkarte](media/customize-field-email1.png "E-Mail-Konfigurationkarte")

   In dem **Header** Abschnitt wird das Feld **Erstellt am** durch **Priorität** ersetzt.

   Ebenso wird im Abschnitt **Einzelheiten** das Feld **Priorität** entfernt und das Feld **Gegenstand** wird nach oben verschoben.

8.  Wählen Sie **OK** aus und dann **Speichern**.

9.  Wählen Sie **Veröffentlichen** aus, um die Anpassungen zu veröffentlichen.

Jetzt können Sie die Änderungen in der **Zeitskala** Steuerung sehen. Im reduzierten Modus können Sie die an der Karte vorgenommenen Änderungen anzeigen.

   > [!div class=mx-imgBorder] 
   > ![E-Mail-Konfigurationkarte](media/email2.png "E-Mail-Konfigurationkarte")

> [!Note]
> Wenn ein Feld keinen Wert hat, bleibt der Feldwert auf der Karte leer. 

## <a name="enable-custom-activity-in-timeline"></a>Aktivieren Sie die benutzerdefinierte Aktivität in der Zeitleiste

Während Sie eine benutzerdefinierte Entität erstellen, möchten Sie diese möglicherweise als Aktivität für Ihre Benutzer in der Zeitleiste anzeigen. Um die benutzerdefinierte Entität als Aktivität anzuzeigen, müssen Sie beim Erstellen einer benutzerdefinierten Entität bestimmte Optionen aktivieren.

> [!Note]
> Stellen Sie sicher, dass die benutzerdefinierte Entität als Aktivität aktiviert ist, bevor Sie die Entität erstellen. Nachdem Sie die benutzerdefinierte Entität erstellt haben, können Sie die Entität nicht mehr als Aktivität aktivieren und für Ihre Benutzer in der **Zeitleiste** Steuerung anzeigen.

Gehen Sie folgendermaßen vor, um eine benutzerdefinierte Aktivität in der Zeitleiste zu aktivieren.

[Schritt 1: Erstellen eines Entitätsformulars](#step-1-create-an-entity)

[Schritt 2: Fügen Sie der modellgetriebenen App eine Entität hinzu](#step-2-add-entity-to-the-model-driven-app)

### <a name="step-1-create-an-entity"></a>Schritt 1: Erstellen eines Entitätsformulars

Sie können eine Entität entweder im [klassischen Modus](#classic-mode) oder [Power Apps](#powerapps) erstellen. 

#### <a name="classic-mode"></a>Klassischer Modus

1.  Melden Sie sich in Ihrer `https://<YourOrgURL>.dynamics.com/apps`-Umgebung an.

2.  Öffnen Sie eine modellgesteuerte App und wählen Sie dann in der Befehlsleiste **Einstellungen** ![Einstellungen](../model-driven-apps/media/powerapps-gear.png) > **Erweiterte Einstellungen** aus.

3.  Gehen Sie zu **Einstellungen** > **Anpassung** > **System anpassen**. Die Seite „Projektmappen-Explorer“ wird in einem neuen Browserfenster geöffnet.  

4.  Wählen Sie **Entitäten** unter **Komponenten** im Standardlösungsbereich.

5.  Wählen Sie **Neu**, um eine neue Entität zu erstellen. Ein neues Browserfenster wird angezeigt.

6. Geben Sie die erforderlichen Felder wie im Thema [Erstellen Sie eine Entität](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/customize/create-entities) beschrieben ein. 

   > [!Note]
   > Das [Erstellen Sie eine Entität](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/customize/create-entities) Thema ist sogar auf die modellgesteuerten Dynamics 365-Apps anwendbar.

7. Wählen Sie die Bereiche aus, der Sie der benutzerdefinierten Entität hinzufügen möchten.

8. Scrollen Sie nach unten zum Abschnitt **Kommunikation & Zusammenarbeit** und wählen Sie die gewünschten Optionen.

9. Scrollen Sie nach unten zum Abschnitt **Datendienste** und wählen Sie das Kontrollkästchen **Schnelle Erstellung zulassen** aus. Mit dieser Option können Sie die Entität in einem Schnellerstellungsformular öffnen.

10. Scrollen Sie bis zu **Entitätsdefinition**, und wählen Sie das Kontrollkästchen **Als Aktivitätseinheit definieren** aus. Diese Option aktiviert die Entität als Aktivität. 

    > [!Note]
    > Nur während der Erstellung der Entität können Sie diese Option aktivieren. Sobald die Entität erstellt wurde, können Sie dieses Kontrollkästchen nicht mehr aktualisieren.

11. Stellen Sie sicher, dass das Kontrollkästchen **In Aktivitätsmenüs anzeigen** auch aktiviert ist.

    > [!Note]
    > Diese Option stellt sicher, dass die Aktivität im Steuermenü **Zeitleiste** aufgeführt ist.

    > [!div class=mx-imgBorder] 
    > ![Aktivität anzeigen](media/display-activity-classicmode.png "Aktivität anzeigen")

12. Wählen Sie **Speichern** aus.

13. Wählen Sie **Veröffentlichen** aus, um die Anpassungen zu veröffentlichen.

#### <a name="powerapps"></a>PowerApps

Folgen Sie dem [Erstellen Sie eine benutzerdefinierte Entität](../common-data-service/data-platform-create-entity.md) zum Erstellen einer Entität mit der PowerApps.

Nach Schritt 3 in [Erstellen Sie eine Entität](../common-data-service/data-platform-create-entity.md#create-an-entity) stellen Sie vor dem Speichern des Erstellens der Entität sicher, dass Sie Folgendes ausführen:

1. Erweitern vom **Mehr Einstellungen** > **Entitätstyp und Eigentum**.

2. Wählen Sie die Option **Aktivitätsentität** aus der Dropdownliste **Entitätstyp wählen** aus, um eine Entität als Aktivität zu aktivieren.

3. Stellen Sie sicher, dass das Kontrollkästchen **In Aktivitätsmenüs anzeigen** ausgewählt ist.

4. Erweitern **Einstellungen erstellen und aktualisieren**.

5. Wählen Sie das Kontrollkästchen **Aktivieren Sie das schnelle Erstellen von Formularen**.

    > [!div class=mx-imgBorder] 
    > ![Aktivität anzeigen](media/display-activity-pa.png "Aktivität anzeigen")

6. Wählen Sie eine andere erforderliche Option und wählen dann **Erstellen**.

### <a name="step-2-add-entity-to-the-model-driven-app"></a>Schritt 2: Fügen Sie der modellgetriebenen App eine Entität hinzu

Nachdem Sie die Entität erstellt und als Aktivität aktiviert haben, müssen Sie sie der modellgetriebenen App hinzufügen.

1. Melden Sie sich in Ihrer `https://<YourOrgURL>.dynamics.com/apps`-Umgebung an.

2. Wählen Sie die Auslassungspunkte (**..**) auf einer modellgesteuerten App-Kachel. Zum Beispiel App-Kachel **Kundenservice-Hub**.

3. Wählen Sie **IM ANWENDUNGS-DESIGNER ÖFFNEN** aus. Der App-Designer wird in einer neuen Registerkarte geöffnet.

4. Suchen Sie nach der benutzerdefinierten Entität, die Sie unter **Entitätansicht** im Canvas-Bereich erstellt haben.

5. Wählen Sie **Formulare** aus. Die Option wird im Komponentenfenster angezeigt.

6. Wählen Sie das Kontrollkästchen im Bereich **Aktivieren Sie das schnelle Erstellen von Formularen**. Diese Option verwendet das Schnellerstellungsformular, wenn der Benutzer die Schaltfläche **+** in der Steuerung **Zeitskala** auswählt.

    > [!div class=mx-imgBorder] 
    > ![Aktivität anzeigen](media/app-designer-activity.png "Aktivität anzeigen")

7. Wählen Sie **Speichern** aus.

8. Wählen Sie **Veröffentlichen** aus.

## <a name="enable-custom-activities-in-timeline-for-mobile-client"></a>Aktivieren Sie benutzerdefinierte Aktivitäten in der Zeitleiste für mobile Clients

Wenn Sie benutzerdefinierte Aktivitäten haben, die Sie für Benutzer mit Mobilgeräten anzeigen möchten, müssen Sie diese aktivieren. Folgen Sie diesen Schritten zur Aktivierung.

### <a name="enable-for-mobile"></a>Für mobile Nutzung aktivieren 

1.  Melden Sie sich in Ihrer `https://<YourOrgURL>.dynamics.com/apps`-Umgebung an.

2. Öffnen Sie eine modellgesteuerte App und wählen Sie dann in der Befehlsleiste **Einstellungen** ![Einstellungen](../model-driven-apps/media/powerapps-gear.png) > **Erweiterte Einstellungen** aus.

3.  Gehen Sie zu **Einstellungen** > **Anpassung** > **System anpassen**. Die Seite „Projektmappen-Explorer“ wird in einem neuen Browserfenster geöffnet.  

4.  Erweitern Sie **Entitäten** unter **Komponenten** im Standardlösungsbereich.

5.  Wählen Sie ein Entitätsformular aus der Liste aus. Zum Beispiel Konto.

6.  Scrollen Sie nach unten zum **Outlook & Mobile** Abschnitt, und aktivieren Sie das Kontrollkästchen für die folgenden Optionen:

    -   Für Mobile aktivieren (nach Ihren Wünschen)
    -   Schreibgeschützt für Mobile (nach Ihren Wünschen)

7.  Wählen Sie **Speichern** aus.

8.  Wählen Sie **Veröffentlichen** aus, um die Anpassungen zu veröffentlichen.

### <a name="select-the-modules-to-display"></a>Auswählen der Module zum Anzeigen

Nachdem Sie die Optionen **Für Handys aktivieren** und **In Mobilgeräten schreibgeschützt** ausgewählt haben (gemäß Ihren Anforderungen) für eine Entität müssen Sie das Modul auswählen, das in der Zeitleiste angezeigt werden soll. Wählen Sie **alle anzeigen**, wenn Sie alle Module anzeigen möchten oder wählen Sie **Ausgewählte anzeigen**, wenn Sie eines oder mehrere Module gemäß Ihren Geschäftsanforderungen anzeigen möchten. Wenn Sie **Ausgewählte Aktionen anzeigen** auswählen, wählen Sie die Aktionen aus, die Sie anzeigen möchten.
Befolgen Sie die in der Anleitung beschriebenen Schritte 1 bis 8 [Module anpassen](#customize-modules) Abschnitt, und speichern und veröffentlichen Sie die Anpassungen.

   > [!div class=mx-imgBorder] 
   > ![Auswählen der Zeitskala-Modulen zum Anzeigen](media/timeline-activity.png "Auswählen der Zeitskala-Modulen zum Anzeigen")

## <a name="enable-or-disable-rich-text-editor-for-notes-in-timeline"></a>Aktivieren oder Deaktivieren des Rich-Text-Editors für Notizen in der Zeitleiste

Mit dem Rich-Text-Editor können Benutzer reichhaltige und gut formatierte Inhalte für die Notizen mit Betonung erstellen. Der Editor bringt allgemeine Textverarbeitungsfunktionen mit. Weitere Informationen finden Sie unter [Notizen machen](https://docs.microsoft.com/dynamics365/customer-service/customer-service-hub-user-guide-basics#take-a-note).

Die Funktion ist standardmäßig aktiviert. Wenn Sie die Funktionen später für Ihre Benutzer deaktivieren und aktivieren möchten, folgen Sie den Schritten:

1.  Melden Sie sich in Ihrer `https://<YourOrgURL>.dynamics.com/apps`-Umgebung an.

2. Öffnen Sie eine modellgesteuerte App, und wählen Sie dann in der Befehlsleiste **Einstellungen** ![Einstellungen](../model-driven-apps/media/powerapps-gear.png) > **Verwaltung** > **Systemeinstellungen** aus.

3. Blättern Sie im Dialog **Systemeinstellungen** unter **Registerkarte Allgemein** nach unten und aktivieren oder deaktivieren Sie das Kontrollkästchen für **Verwende Rich Text, um die Formatierung der in der Zeitleiste erstellten Notizen zu erleichtern.** Feld.

4. Wählen Sie **OK** aus.

    > [!div class=mx-imgBorder] 
    > ![Rich-Text-Editor aktivieren](media/timeline-note-enable-rich-text-editor.png "Rich-Text-Editor aktivieren")

Der Rich-Text-Editor wird für Ihre Benutzer je nach Auswahl des Kontrollkästchens aktiviert oder deaktiviert. 

## <a name="see-also"></a>Siehe auch

[FAQs für Zeitskala-Steuerelement](faqs-timeline-control.md)

[Zeitskala-Abschnitt in der Kunderservicehub-App](https://docs.microsoft.com/dynamics365/customer-service/customer-service-hub-user-guide-basics#timeline)

[Einen termin, E-Mail, Telefonanruf, Notiz oder Aufgabenaktivität zur Zeitskala hinzufügen](../../user/add-activities.md)
