---
title: 'Ändern Sie das Farbschema oder fügen Sie ein Logo hinzu, entsprechend der Marke Ihrer Organisation  | MicrosoftDocs'
ms.custom: ''
ms.date: 06/18/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
author: Mattp123
ms.assetid: 21a166a0-d25e-4260-a1e4-2ddc528787c2
caps.latest.revision: 17
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-a-theme"></a>Erstellen eines Designs

Sie können ein angepasstes Erscheinungsbild (ein Design) für Ihre App erstellen, indem Sie Änderungen an den Standardfarben und visuellen Elementen im nicht benutzerdefinierten System vornehmen. Sie können beispielsweise Ihr persönliches Produktbranding erstellen, indem Sie ein Unternehmenslogo hinzufügen und einen entitätsspezifischen Farbton zur Verfügung stellen. Ein Design wird erstellt, indem die Anpassungstools in der Benutzeroberfläche verwendet werden, ohne dass ein Entwickler hierfür Code schreiben muss. Sie können Designs, die in Ihrer Organisation verwendet werden, erstellen, ändern oder löschen. Die Designanpassung wird in Webformularen in  Dynamics 365 for Outlook unterstützt. Sie können mehrere Designs definieren, jedoch kann nur eins als das Standarddesign festgelegt und veröffentlicht werden.  
  
<a name="UseThemes"></a>   
## <a name="use-themes-to-enhance-the-user-interface-and-create-your-product-branding"></a>Verwenden von Designs, um die Benutzeroberfläche zu optimieren und ein Produktbranding zu erstellen  
 Designs werden verwendet, um die Benutzeroberfläche der App zu optimieren, nicht um sie erheblich zu verändern. Die Designfarben werden global in der Anwendung angewendet. Beispielsweise können Sie die folgenden visuellen Elemente in der Benutzeroberfläche verbessern:  
  
-   Ändern von Produktlogos und Navigationsfarben, um ein Produktbranding zu erstellen  
  
-   Anpassen von Akzentfarben, beispielsweise Farben für die Bewegung des Mauszeigers oder Auswahlfarben  
  
-   Bereitstellen von entitätsspezifischen Farbtönen  
    
-   Logo  
  
-   Logo-QuickInfo  
  
-   Navigationsleistenfarbe  
  
-   Navigationsleisten-Regalfarbe

-   Hauptbefehlsleistenfarbe in der Einheitlichen Oberfläche
  
-   Überschriftenfarbe  
  
-   Globale Linkfarbe  
  
-   Effekt für verwendeten Link  
  
-   Linkeffekt beim Daraufzeigen  
  
-   Prozesssteuerelementfarbe  
  
-   Standardentitätsfarbe  
  
-   Standardfarbe für benutzerdefinierte Entitäten  
  
-   Steuerelementschattierung  
  
-   Steuerelementrand  
  
<a name="Solution"></a>   
## <a name="solution-awareness"></a>Lösungsbewusstsein  
 Das Design ist nicht lösungsfähig. Änderungen, die für das Design einer Organisation vorgenommen werden, sind nicht in Lösungen enthalten, die von der Organisation exportiert werden. Die Daten werden in der Designentität gespeichert, die in eine andere Umgebung exportiert und erneut importiert werden ann. Das importierte Design muss veröffentlicht werden, um wirksam zu werden.  
  
<a name="CloneAlter"></a>   
## <a name="copy-and-alter-the-existing-theme"></a>Kopieren und Ändern des vorhandenen Designs  
 Der einfachste und schnellste Weg, ein neues Design zu erstellen, ist, ein vorhandenes Design zu klonen und zu ändern, es dann zu speichern, eine Vorschau anzuzeigen und es zu veröffentlichen. 
 
1.  Melden Sie sich bei [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.

2.  Wählen Sie **Modellgesteuert** (unten links) aus. 

3.  Wählen Sie ![Symbol Einstellungen](../model-driven-apps/media/powerapps-gear.png) (oben rechts) > **Erweiterte Anpassungen** 

4. Wählen Sie unter die **Designs** **Alle Designs**. 

5. Klicken Sie auf **CRM-Standard-Design**. 

Der folgende Screenshot enthält einen Teil des standardmäßige Designsetup.  

> [!div class="mx-imgBorder"] 
> ![Standarddesign](media/default-theme.png) 
  
 Wir haben das Standarddesign geklont und die Farben geändert. Folgende Screenshots zeigen die neuen Farben für die Navigation und die Hervorhebung. Sie können auch ein neues Logo für das Produkt auswählen.  
  
 Im folgenden Screenshot wird die neue Navigationsfarbe angezeigt.  
 
 > [!div class="mx-imgBorder"] 
 > ![Leicht grüne Designfarben](media/theme-gentle-green.png "Leicht grüne Designfarben")  
  
 Im folgenden Screenshot wird das Firmaenentitätsraster mit der neuen Hervorhebungsfarbe angezeigt.  
 
 > [!div class="mx-imgBorder"] 
 > ![Leicht grünes Design Firmenraster](media/themes-gentle-green-account-grid.png "Leicht grünes Design Firmenraster")  
  
<a name="Publish"></a>   
## <a name="preview-and-publish-a-theme"></a>Anzeigen und Veröffentlichen eines Designs  
 Um eine Vorschau eines Designs anzuzeigen und ein Design zu veröffentlichen, führen Sie die folgenden Schritte aus:  
  
-   Erstellen Sie ein neues Design oder klonen Sie ein vorhandenes.  
  
-   Zeigen Sie eine Vorschau des neuen Designs an, indem Sie auf der Befehlsleiste **Vorschau** auswählen. Wenn Sie den Vorschaumodus beenden möchten, wählen Sie auf der Befehlsleiste **Vorschau beenden** neben der Schaltfläche **Vorschau** aus.  
  
-   Veröffentlichen Sie ein Design. Wählen Sie auf der Befehlsleiste **Design veröffentlichen** aus.  
  
 Im folgenden Screenshot werden die Schaltflächen der Befehlsleiste für die Vorschau und die Veröffentlichung angezeigt.  
  
 ![Verwenden Sie die Vorschauschaltflächen, um den Vorschaumodus zu aktivieren/verlassen](media/themes-preview-buttons.PNG "Verwenden Sie die Vorschauschaltflächen, um den Vorschaumodus zu aktivieren/verlassen")  
  
<a name="BestPracticies"></a>   
## <a name="best-practices"></a>Bewährte Methoden  
 Nachfolgend erhalten Sie Empfehlungen zum Entwerfen von Designkontrasten und zur Farbauswahl.  
  
### <a name="theme-contrast"></a>Designkontrast  
 Es wird die folgende Methode zur Bereitstellung von Kontrastfarben empfohlen:  
  
-   Wählen Sie die kontrastierenden Farben sorgfältig aus. Der Common Data Service für Apps mit  Standarddesign  hat die richtigen Kontrastverhältnisse, um optimale Benutzerfreundlichkeit sicherzustellen. Verwenden Sie ähnliche Verhältnisse für die neuen Designs.  
  
-   Für den kontrastreichen Modus können Sie die standardmäßige Farbeneinstellungen verwenden.  
  
### <a name="theme-colors"></a>Designfarben  
 Wir empfehlen, nicht zu viele verschiedene Farben zu verwenden. Sie können zwar für die einzelnen Entitäten verschiedene Farben festlegen, wir empfehlen jedoch eines von zwei Mustern:  
  
-   Weisen Sie allen Entitäten neutrale Farben zu und heben Sie die Schlüsselentitäten hervor.  
  
-   Verwenden Sie die gleiche Farbe für ähnliche oder verknüpfte Entitäten, wie die Warteschlangen-, Warteschlangenelement- oder Produktkatalogentitäten. Halten Sie die Gesamtanzahl der Gruppen niedrig.  
  
<a name="Considerations"></a>   
## <a name="custom-theme-considerations"></a>Überlegungen zum benutzerdefinierten Design  
 Sie sollten Folgendes während der Planung der Verwendung benutzerdefinierter Designs beachten:  
  
-   Die meisten aktualisierten Bereiche in der Benutzeroberfläche enthalten benutzerdefinierte Designfarben.  
  
-   Auch wenn die Designfarben global in der Anwendung übernommen werden, behalten einige Vorgängerbereiche, z. B. Farbverlaufsschaltflächen, die Standardfarben bei.  
  
-   Bestimmte Bereiche müssen dunkle oder helle Farben verwenden, um mit den standardmäßigen Symbolfarben zu kontrastieren. Die Symbolfarbe ist nicht anpassbar.  
  
-   Eine Entität kann nicht in verschiedenen Farben unter verschiedenen Sitemap-Knoten angezeigt werden.  
  
-   Die Farben von Sitemap-Knoten können nicht angepasst werden.  
  
## <a name="see-also"></a>Siehe auch  
         
 [Video: Designs in Dynamics 365 Customer Engagement](http://go.microsoft.com/fwlink/p/?LinkId=529568) [Abfragen und Bearbeiten eines Organisationsdesigns](https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/query-and-edit-an-organization-theme)

