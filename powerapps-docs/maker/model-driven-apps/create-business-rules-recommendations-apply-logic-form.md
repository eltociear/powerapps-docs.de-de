---
title: Erstellen von Modell-angetriebenen Geschäftsregeln und Empfehlungen | MicrosoftDocs
ms.custom: ''
ms.date: 03/15/2019
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
caps.latest.revision: 31
author: Mattp123
ms.author: matp
manager: kvivek
tags:
- Power Apps maker portal impact
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: eff15d356b1ec37e0a2528f11b73d7ee99ea5af1
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2863334"
---
# <a name="create-business-rules-and-recommendations-to-apply-logic-in-a-model-driven-app-form"></a>Erstellen von Geschäftsregeln und Empfehlungen zur Anwendung eines Modell-getriebenen App-Formulars

Dieses Thema zeigt, wie Sie Geschäftsregeln und Empfehlungen erstellen, um Formularlogik in einer modellgesteuerten App anzuwenden, ohne JavaScript-Codes zu schreiben oder Plug-ins zu erstellen. Geschäftsregeln bieten eine einfache Schnittstelle, um sich schnell ändernden und häufig verwendeten Regeln zu implementieren und zu verwalten. Sie können auf Haupt- und Schnellerfassungsformulare angewendet werden, und sie funktionieren in modellgesteuerten Apps, alten Web-Apps, Dynamics 365 für Tablets und Dynamics 365 for Outlook (Online- oder Offlinemodus).

> [!NOTE]
> Um eine Geschäftsregel für eine Entität zu definieren, damit diese für alle Formulare und Server angewendet wird, siehe [Geschäftsregel für eine Enität erstellen](/powerapps/maker/common-data-service/data-platform-create-business-rule).
  
 Indem Sie Bedingungen und Aktionen kombinieren können Sie folgende Aktionen mit Geschäftsregeln ausführen:  
  
-   Feldwerte festlegen  
  
-   Klare Feldwerte  
  
-   Festlegen von Felderforderlichkeitsstufen  
  
-   Ein- oder Ausblenden von Feldern  
  
-   Aktivieren oder Deaktivieren von Feldern  
  
-   Überprüfen von Daten und Anzeigen von Fehlermeldungen  
  
-   Erstellen von Geschäftsempfehlungen basierend auf Business Intelligence-Daten.  
  
## <a name="create-a-business-rule-or-business-recommendation"></a>Erstellen einer Geschäftsregel oder Geschäftsempfehlung
  
1. Öffnen Sie den [Lösungs-Explorer](advanced-navigation.md#solution-explorer).  
  
2.  Öffnen Sie die Entität, für die Sie die Geschäftsregel erstellen möchten (öffnen Sie z.B. die Entität **Konto**), und doppelklicken Sie dann auf **Geschäftsregeln**.  
  
 ![Erstellen einer Geschäftsregel in der Standardlösung](media/create-business-rule-the-default-solution.png "Erstellen einer Geschäftsregel in der Standardlösung")  
  
3.  Wählen Sie **Neu** aus.  
  
     Das Geschäftsregeldesignerfenster wird mit einer einzelnen Bedingung geöffnet, die bereits für Sie erstellt wurde. Jede Regel startet mit einer Bedingung. Die Geschäftsregel führt eine oder mehrere diese Aktionen basierend auf der Bedingung durch.  
  
 ![Geschäftsregelentwurfsfenster](media/business-rules-design-window.png "Geschäftsregelentwurfsfenster")  
  
   > [!TIP]
> Wenn Sie eine vorhandene Geschäftsregel ändern möchten, müssen Sie sie deaktivieren, bevor Sie sie bearbeiten können.

4.  Fügen Sie eine Beschreibung im Beschreibungsfeld in der oberen linken Ecke des Fensters hinzu.  
  
5.  Legen Sie den Bereich nach folgendem Bedingungen fest:  
  
    |||  
    |-|-|  
    |**Wenn Sie dieses Element auswählen...**|**Ist der Bereich...**|  
    |**Entität**|Alle Formulare und Server|  
    |**Alle Formulare**|Alle Formulare|  
    |Bestimmtes Formular (z. B. **Firma**-Formular)|Nur dieses Formular|  
  
6. **Bedingungen hinzufügen.** Um Ihrer Geschäftsregel weitere Bedingungen hinzuzufügen:  
  
    1.  Ziehen Sie die **Bedingung**-Komponente von der Registerkarte **Komponenten** auf ein Pluszeichen (+) zwischen im Designer.  
  
        ![Eine Bedingung in einer Geschäftsregel hinzufügen](media/add-condition-business-rule.png "Eine Bedingung in einer Geschäftsregel hinzufügen")  
  
    2.  Sie können die Eigenschaften der Bedingung festlegen. Klicken Sie dazu auf die **Bedingung**-Komponente im Design, und legen Sie die Eigenschaften auf der Registerkarte **Eigenschaften** auf der rechten Seite des Bildschirms fest. Wenn Sie Eigenschaften festlegen, wird ein Ausdruck unten auf der Registerkarte **Eigenschaften** erstellt.  
  
    3.  Um eine Zusatzbestimmung (UND oder ODER) der Bedingung hinzuzufügen, klicken Sie auf **Neu** auf der Registerkarte **Eigenschaften**, um eine neue Regel zu erstellen, und legen Sie dann Eigenschaften für diese Regel fest. Im Feld **Regel-Logik** können Sie angeben, ob die neue Regel als UND oder ODER hinzugefügt werden soll.  
  
        ![Eine neue Regel zu einer Bedingung hinzufügen](media/add-new-rule-condition.png "Eine neue Regel zu einer Bedingung hinzufügen")  
  
    4.  Wenn Sie die Eigenschaften für die Bedingung festgelegt haben, klicken Sie auf **Übernehmen**.  
  
7. **Aktionen hinzufügen.** Eine Aktion hinzufügen:  
  
    1.  Ziehen Sie eine der Aktionskomponenten von der **Komponenten**-Registerkarte auf ein Pluszeichen neben **Bedingung**-Komponente. Ziehen Sie die Aktionen auf ein Pluszeichen neben ein Häkchen, wenn die Geschäftsregel die Aktion ausführen soll, sofern die Bedingung erfüllt wird, oder auf ein Pluszeichen neben einem x, wenn Sie die Geschäftsregel die Aktion ausführen soll, sofern die Bedingung nicht erfüllt ist.  
  
        ![Ziehen Sie eine Aktion zu einer Geschäftsregel](media/drag-an-action-business-rule.png "Ziehen Sie eine Aktion zu einer Geschäftsregel")  
  
    2.  Sie können die Eigenschaften der Aktion festlegen. Klicken Sie dazu auf die **Aktion**-Komponente im Design, und legen Sie die Eigenschaften auf der Registerkarte **Eigenschaften**.  
  
    3.  Wenn Sie die Eigenschaften festgelegt haben, klicken Sie auf **Übernehmen**.  
  
8. **Eine Unternehmensempfehlung hinzufügen.** Eine Unternehmensempfehlung hinzufügen:  
  
    1.  Ziehen Sie eine der **Empfehlung**-Komponente von der **Komponenten**-Registerkarte auf eine **Bedingung**-Komponente. Ziehen Sie die **Empfehlung** -Komponente auf ein Pluszeichen neben ein Häkchen, wenn die Geschäftsregel die Aktion ausführen soll, sofern die Bedingung erfüllt wird, oder auf ein Pluszeichen neben einem x, wenn Sie die Geschäftsregel die Aktion ausführen soll, sofern die Bedingung nicht erfüllt ist.  
  
    2.  Sie können die Eigenschaften der Empfehlung festlegen. Klicken Sie dazu auf die **Empfehlung**-Komponente im Designer, und legen Sie die Eigenschaften auf der Registerkarte **Eigenschaften**.  
  
    3.  Um weitere Aktionen zur Empfehlung hinzuzufügen, ziehen Sie sie auf die Registerkarte **Komponenten**, und legen Sie dann auf Eigenschaften für jede Aktion auf der Registerkarte **Eigenschaften** fest.  
  
        > [!NOTE]
        >  Wenn Sie eine Empfehlung erstellen, wird standardmäßig eine einzelne Aktion hinzugefügt. Um alle Aktionen in einer Empfehlung anzuzeigen, klicken Sie auf der Seite **Details** auf die **Empfehlung**-Komponente.  
  
    4.  Wenn Sie die Eigenschaften festgelegt haben, klicken Sie auf **Übernehmen**.  
  
9. Um die Geschäftsregel zu überprüfen, klicken Sie auf **Überprüfen** auf der Aktionsleiste.  
  
10. Um die Geschäftsregel zu speichern, klicken Sie auf **Speichern** auf der Aktionsleiste.  
  
11. Um die Geschäftsregel zu aktivieren, wählen Sie sie im Lösungsexplorer-Fenster aus, und klicken Sie dann auf **Aktivieren**. Sie können die Geschäftsregel nicht über das Designer-Fenster aktivieren.  
  
> [!TIP]
>  Hier sind ein paar Tipps für die Arbeit mit den Geschäftsregeln im Designerfenster:  
>   
> - Um eine Momentaufnahme aller Elemente im Geschäftsregelnfenster durchzuführen, klicken Sie auf **Momentaufnahme** in der Aktionsleiste. Dies ist beispielsweise hilfreich, wenn Sie die Geschäftsregel freigeben und Kommentare von Teammitgliedern haben möchten.  
> - Verwenden Sie die Minimap, um schnell zu anderen Teilen des Prozesses zu navigieren. Dies ist hilfreich, wenn Sie einen komplizierten Prozess haben, der nicht komplett angezeigt wird.  
> - Wenn Sie Bedingungen, Aktionen und Unternehmensempfehlungen der Geschäftsregel hinzufügen, wird Code für die Geschäftsregel am unteren Rand des Designerfensters erstellt und angezeigt. Dieser Code ist nur lesbar.  
  
<a name="BKMK_LocalizingErrorMessages"></a>   
## <a name="localize-error-messages-used-in-business-rules"></a>Lokalisieren der Fehlermeldungen in Geschäftsregeln  
 Sind mehrere Sprache für Ihre Organisation bereitgestellt, können Sie Ihre Fehlermeldungen lokalisieren. Bei jeder Meldung generiert das System eine Beschriftung. Wenn Sie die Übersetzungen in Ihrer Organisation exportieren, können Sie lokalisierte Versionen Ihrer Meldungen hinzufügen und diese Beschriftungen wieder in das System importieren, so dass Personen, die andere Sprachen als Ihre Ausgangssprache verwenden, die übersetzten Meldungen sehen.  

## <a name="common-issues"></a>Allgemeine Probleme
Dieser Abschnitt beschreibt allgemeine Probleme, die auftreten können, wenn Sie Unternehmensregeln verwenden. 

### <a name="full-name-field-not-supported-with-unified-interface-apps"></a>Das Feld "Name" wird für Apps mit einheitlicher Oberfläche nicht unterstützt.
Aktionen oder Bedingungen, die ein Feld vom Typ **Vollständiger Name** verwenden, werden in Apps mit einheitlicher Oberfläche nicht unterstützt.  Alternativ können Sie Aktionen oder Bedingungen mit den Feldern **Vorname** (firstname) und **Nachname** (lastname) verwenden. 

### <a name="is-your-business-rule-not-firing-for-a-form"></a>Löst ihre Geschäftsregel kein Ereignis eines Formulars aus?
Eine Geschäftsregel darf nicht ausgeführt werden, weil das in der Geschäftsregel referenzierte Feld nicht im Formular enthalten ist. 
1.  Öffnen Sie den Projektmappen-Explorer. Erweitern Sie die gewünschte Entität, und wählen Sie dann **Formulare**. 
2.  Öffnen Sie das gewünschte Formular und wählen Sie dann im Formulardesigner-Menüband **Geschäftsregeln**. 
3.  Im Formulardesigner öffnen Sie die Geschäftsregel. 
4.  Wählen Sie im Geschäftsregeldesigner jede Bedingung und Aktion aus, um alle Felder zu überprüfen, auf die in jeder Bedingung und Aktion verwiesen wird. 

     > [!div class="mx-imgBorder"] 
     > ![](media/business-rule-field.png "Field referenced in business rule exists in entity")

 5. Stellen Sie sicher, dass jedes Feld, auf das in der Geschäftsregel verwiesen wird, auch auf dem Formular enthalten ist. Falls nicht, fügen Sie das fehlenden Feld dem Formular hinzu.

     > [!div class="mx-imgBorder"] 
     > ![](media/account-name-on-form.png "Account name field on form")

## <a name="frequently-asked-questions-faq"></a>Häufig gestellte Fragen (FAQ)
*Können Geschäftsregeln Felder in einem schreibgeschützten Formular entsperren?*
- Ja, eine Geschäftsregel kann Felder entsperren und Aktionen in einem schreibgeschützten Formular bearbeiten.

*Wie behandle ich Probleme bei einer Geschäftsregel, die nicht funktioniert?* 
- Sehen Sie [Löst ihre Geschäftsregel kein Ereignis eines Formulars aus?](#is-your-business-rule-not-firing-for-a-form) in diesem Thema.

## <a name="see-also"></a>Siehe auch  
 [Erstellen benutzerdefinierter Geschäftslogik durch Prozesse](guide-staff-through-common-tasks-processes.md)   
 [Erstellen eines Geschäftsprozessflusses](/flow/create-business-process-flow)   

