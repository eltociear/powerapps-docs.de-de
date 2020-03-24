---
title: Konfigurieren von Kopfzeileneigenschaften im Formulardesigner | MicrosoftDocs
ms.custom: ''
ms.date: 09/30/2019
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
author: Aneesmsft
ms.author: matp
manager: kvivek
tags:
- Power Apps maker portal impact
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 67173c01bc6a96f0ada55c62688db76ca0af0596
ms.sourcegitcommit: 6cffa70358fd2e388d64a01f906c8c196fbbdefb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/17/2020
ms.locfileid: "3069669"
---
# <a name="configure-header-properties-in-the-form-designer"></a>Konfigurieren von Kopfzeileneigenschaften im Formulardesigner

Hersteller können die Dichte der modellgetriebenen App-Formularheader steuern, um die Bedürfnisse aller Benutzer des Formulars zu erfüllen.

## <a name="high-density-header"></a>Kopf mit hoher Dichte

Der hochdichte Kopf stellt sicher, dass die wichtigsten Informationen für den Benutzer jederzeit sichtbar sind. Mit dem Kopf mit hoher Dichte wird der Datensatz-Titel nie abgeschnitten. Sogar lange Datensatztitel werden mit mehreren Zeilen angezeigt. Ebenso stellt der High-Density-Kopf sicher, dass bis zu vier Feldwerte direkt im Kopf sichtbar sind und nie abgeschnitten oder versteckt werden.  

Um sicherzustellen, dass wichtige Informationen immer angezeigt werden, zeigt das Framework schreibgeschützten Feldwerte an und Benutzer können die anzeigten Feldwerte in der Kopfzeile nicht direkt bearbeiten. Visualisierungen wie benutzerdefinierte Komponenten oder Web-Ressourcen sind ebenfalls nicht erlaubt.

Wenn ein Formular keine Kopfdichte angibt oder wenn ein neues Formular erstellt wird, verwendet das Framework standardmäßig den Kopf mit hoher Dichte.

> [!div class="mx-imgBorder"] 
> ![Formularkopf mit hoher Dichte](media/form-header-high-density.png "Formularkopf mit hoher Dichte")
    
## <a name="low-density-header"></a>Kopfzeile mit niedriger Dichte
Formularkopfzeilen mit niedriger Dichte ermöglichen Benutzern, die Feldwerte direkt in der Kopfzeile zu bearbeiten. Es ermöglicht auch Visualisierungen wie kundenspezifische Komponenten und Web-Ressourcen.  
  
Allerdings werden als Folge häufig wichtige Informationen abgeschnitten oder sind nicht wirklich sichtbar. Die Kopfzeile mit niedriger Dichte kürzt den Datensatz-Titel sowie die im Kopf angezeigten Feldwerte. Häufig sind nur ein oder zwei Felder direkt in der Kopfzeile und im Restüberlauf sichtbar und werden in einem Flyout angezeigt, das einen zusätzlichen Klick erfordert.

> [!div class="mx-imgBorder"] 
> ![Formularkopf mit niedriger Dichte](media/form-header-low-density.png "Formularkopf mit niedriger Dichte")

### <a name="configuring-header-density"></a>Konfigurieren von Kopfzeilendichte

Um die Kopfdichte eines modellgetriebenen Formulars zu konfigurieren, gehen Sie wie folgt vor:
1.  Öffnen Sie den Formulardesigner, [um ein Formular zu erstellen oder zu bearbeiten](create-and-edit-forms.md).
2.  Wählen Sie die Formularkopfzeile aus, indem Sie die Kopfzeile in der Formularvorschau auswählen oder mithilfe der [Strukturansicht](using-tree-view-on-form.md).
3.  Wählen Sie im Eigenschaftsfenster **Hohe Dichte**, um einen Formularkopf mit hoher Dichte zu verwenden, oder löschen Sie ihn, um einen Formularkopf mit niedriger Dichte zu verwenden.
4.  Wählen Sie in der Befehlsleiste **Speichern** aus, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** aus, wenn Sie die Änderungen speichern und für Benutzer sichtbar anzeigen möchten.

> [!NOTE]
> Verwenden Sie den neuen Formulardesigner. Der klassische Formulardesigner bietet keine Möglichkeit, die Kopfzeilendichte zu konfigurieren.

## <a name="header-flyout"></a>Kopfzeilenflyout
Das Kopfzeilenflyout wird angezeigt, wenn Benutzer das Chevron in der Formularkopfzeile auswählen. Es ermöglicht dem Benutzer die Bearbeitung von Feldwerten und zeigt auch Visualisierungen wie benutzerdefinierte Komponenten oder Webressourcen an, die Teil des Formularkopfs sind.

Die Verhaltensweisen des Kopfzeilenflyouts ändert sich abhängig von der Kopfzeilendichtekonfiguration.

### <a name="high-density-header-flyout"></a>Flyout für Kopfzeilen mit hoher Dichte
Bei einem hochdichten Formularkopf zeigt der Kopfflyout alle Kopffelder einschließlich der vier Felder, die direkt im Kopf angezeigt werden. Das Framework zeigt standardmäßig den Kopf Flyout an, wenn ein Kopf mit hoher Dichte verwendet wird. Hersteller können die Sichtbarkeit des Kopf-Flyouts mit einem Kopf mit hoher Dichte steuern.

> [!div class="mx-imgBorder"] 
> ![Header-Flyout mit Kopfzeile mit hoher Dichte](media/form-header-flyout-high-density.png "Header-Flyout mit Kopfzeile mit hoher Dichte")

### <a name="low-density-header-flyout"></a>Flyout des Kopfs mit niedriger Dichte
Bei einem Formularkopf mit niedriger Dichte zeigt der Kopf Flyout nur Überlauffelder an, wie beispielsweise Felder, die das Formular aufgrund der Breite des Formulars nicht direkt im Kopf anzeigen kann. Das Kopfzeilenflyout wird zudem automatisch basierend auf der Anzahl von Feldern in der Kopfzeile und der Breite des Formulars angezeigt oder ausgeblendet. Hersteller können die Sichtbarkeit des Kopf-Flyouts bei Verwendung eines Kopfs mit niedriger Dichte nicht kontrollieren.

> [!div class="mx-imgBorder"] 
> ![Header-Flyout mit Kopfzeile mit niedriger Dichte](media/form-header-flyout-low-density.png "Header-Flyout mit Kopfzeile mit niedriger Dichte")

### <a name="show-or-hide-the-header-flyout"></a>Anzeigen oder Ausblenden des Kopfzeilenflyouts
Um den Kopf-Flyout für ein modellgetriebenes Formular ein- oder auszublenden, führen Sie diese Schritte aus:

1.  Öffnen Sie den Formulardesigner, [um ein Formular zu erstellen oder zu bearbeiten](create-and-edit-forms.md).
2.  Wählen Sie die Formularkopfzeile in der Formularvorschau aus oder verwenden Sie die [Strukturansicht](using-tree-view-on-form.md), um sie auszuwählen.
3.  Wählen Sie im Eigenschaftsfenster **Hohe Dichte**, um den Formularkopf mit hoher Dichte zu verwenden. 
4.  Im Eigenschaftenbereich wählen Sie **Kopfzeilenflyout anzeigen** aus, um das Kopfzeilenflyout anzuzeigen, oder löschen Sie die Auswahl, um das Kopfzeilenflyout auszublenden.
5.  Wählen Sie in der Befehlsleiste **Speichern** aus, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** aus, wenn Sie die Änderungen speichern und für Benutzer sichtbar anzeigen möchten.

> [!NOTE]
> - Verwenden Sie den neuen Formulardesigner. Der klassische Formular-Designer bietet keine Möglichkeit, den Kopf-Flyout ein- oder auszublenden.   
> - Die Sichtbarkeit des Kopf-Flyouts kann nur bei Verwendung eines hochdichten Formularkopfs gesteuert werden. Bei Verwendung von Kopfn mit niedriger Dichte wird der Kopf-Flyout abhängig von der Anzahl der Felder im Kopf und der Breite des Formulars automatisch ein- oder ausgeblendet.
> - Ein Bild für eine Entität wird in der Kopfzeile nur dann angezeigt, wenn das Attribut **Primary Imagine** für die Entität definiert ist und die Formulareigenschaft **Bild im Formular anzeigen** aktiviert ist. Mehr Informationen: [Bildfelder](../common-data-service/types-of-fields.md#image-fields). <br />
    Entwickler können ein Bild für eine Entität angeben, indem sie das Attribut [EntityMetadata.PrimaryImageAttribute](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.metadata.entitymetadata.primaryimageattribute?view=dynamics-general-ce-9) verwenden. 


## <a name="form-designer-messages-related-to-form-headers"></a>Formulardesigner-Meldungen in Verbindung mit Formularkopfzeilen
Wenn Sie Formulare mit dem neuen oder klassischen Formulardesigner bearbeiten, werden möglicherweise Nachrichten angezeigt, die sich auf Formularköpfe beziehen. Unten finden Sie Details zu jeder Nachricht und warum Sie sie sehen.

### <a name="weve-upgraded-your-form-to-show-a-high-density-header-that-displays-more-data-you-can-edit-this-setting-in-the-properties-of-the-header"></a>Wir haben Ihr Formular aktualisiert, sodass eine Kopfzeile mit hoher Dichte angezeigt wird, die mehr Daten enthält. Sie können diese Einstellung in den Eigenschaften der Kopfzeile bearbeiten. 
Diese Meldung wird im Formulardesigner angezeigt, wenn ein Ersteller ein neues Hauptformular erstellt (auch über die Aktion Speichern unter) oder ein Hauptformular bearbeitet, das zuvor nicht für die Kopfdichte konfiguriert wurde.  
  
Das Framework ist standardmäßig auf hochdichte Kopf voreingestellt, und diese Nachricht hilft den Erstellern, sich dieses Verhaltens bewusst zu werden. Entwickler können den Frameworkstandard jederzeit überschreiben, indem Sie die Formularkopfzeilendichte manuell konfigurieren, wie weiter oben erläutert.

### <a name="this-form-isnt-using-high-density-header-access-the-setting-in-the-header-properties-high-density-header-helps-display-more-data"></a>In diesem Formular wird keine Kopfzeile mit hoher Dichte verwendet. Greifen Sie auf die Einstellung in den Kopfzeileneigenschaften zu. Bei Kopfzeilen mit hoher Dichte können mehr Daten angezeigt werden. 
Diese Meldung wird im Formulardesigner angezeigt, wenn ein Hersteller ein Hauptformular zur Bearbeitung öffnet, das für die Verwendung von Kopfn mit niedriger Dichte konfiguriert ist. 

Die Botschaft hilft, das Bewusstsein für den hochdichten Kopf und seine Vorteile zu schärfen.

### <a name="field-moved-to-header-flyout-the-header-supports-displaying-up-to-four-read-only-field-values-the-field-field-display-name-will-now-only-be-available-from-the-flyout"></a>Feld wurde in das Kopfzeilenflyout verschoben: Die Kopzeile unterstützt die Anzeige von maximal vier schreibgeschützten Feldwerten. Das Feld *[Feldanzeigename]* ist jetzt nur im Flyout verfügbar.
Diese Meldung wird im Formulardesigner angezeigt, wenn ein Formular eine Kopfzeile mit hoher Dichte verwendet, wobei der Kopfflyout sichtbar ist.  
  
Die Kopfzeile mit hoher Dichte zeigt schreibgeschützte Werte der ersten vier Felder in der Kopfzeile an. Wenn Entwickler ein Feld in der Kopfzeile in den ersten vier Positionen hinzufügen, wird ein vorhandenes Feld, das direkt in der Kopfzeile angezeigt wurde, erweitert und ist nur im Kopfzeilenflyout sichtbar.      

Die Meldung informiert den Ersteller über die Änderung und bestätigt, ob mit der Aktion fortgefahren werden soll.

### <a name="header-field-limit-exceeded-the-header-supports-displaying-up-to-four-read-only-field-values-remove-unused-fields-to-add-more"></a>Der Grenzwert für Kopfzeilenfelder wurde überschritten: Die Kopzeile unterstützt die Anzeige von maximal vier schreibgeschützten Feldwerten. Entfernen Sie nicht verwendete Felder, um weitere hinzuzufügen. 
Diese Meldung wird im Formulardesigner angezeigt, wenn ein Formular eine Kopfzeile mit hoher Dichte verwendet, bei der der Kopfflyout ausgeblendet ist.  
  
Die Kopfzeile mit hoher Dichte zeigt schreibgeschützte Werte von bis zu vier Feldern in der Kopfzeile an. Da der Kopf Flyout ausgeblendet ist, können die Benutzer die zusätzlichen Felder nicht sehen.  

Die Nachricht informiert den Hersteller, dass es bereits vier Felder im Kopf gibt und verhindert, dass zusätzliche Felder im Kopf hinzugefügt werden, die der Benutzer nicht sehen kann.

### <a name="header-does-not-display-custom-components-the-header-supports-displaying-up-to-four-read-only-field-values-remove-the-custom-component-from-the-field-before-adding-it-to-the-header"></a>In der Kopfzeile werden keine benutzerdefinierten Komponenten angezeigt: Die Kopzeile unterstützt die Anzeige von maximal vier schreibgeschützten Feldwerten. Entfernen Sie die benutzerdefinierte Komponente aus dem Feld, bevor Sie sie in der Kopfzeile hinzufügen.  
Diese Meldung wird im Formulardesigner angezeigt, wenn ein Formular eine Kopfzeile mit hoher Dichte verwendet, bei der der Kopfflyout ausgeblendet ist.  
  
Die Kopfzeile mit hoher Dichte zeigt schreibgeschützte Werte von Feldern in der Kopfzeile an. Da der Kopf-Flyout ausgeblendet ist, können Benutzer keine benutzerdefinierten Komponenten sehen, die mit den Feldern im Kopf verknüpft sind.  

Die Nachricht informiert den Hersteller darüber, dass er versucht, ein Feld mit einer zugehörigen benutzerdefinierten Komponente in den Kopf aufzunehmen, und er muss die benutzerdefinierte Komponente entfernen, bevor er das Feld in den Kopf einfügt. Dies ist darauf zurückzuführen, dass es Benutzern nicht möglich sind, die benutzerdefinierte Komponente in der Kopfzeile zu sehen.

### <a name="header-displays-read-only-field-values-the-header-supports-displaying-up-to-four-read-only-field-values-to-provide-editability-to-the-user-add-the-field-to-a-section-in-the-form"></a>In der Kopzeile werden schreibgeschützte Feldwerte angezeigt: Die Kopzeile unterstützt die Anzeige von maximal vier schreibgeschützten Feldwerten. Um dem Benutzer Bearbeitbarkeit zu bieten, fügen Sie das Feld einem Abschnitt im Formular hinzu.  
Diese Meldung wird im Formulardesigner angezeigt, wenn ein Formular eine Kopfzeile mit hoher Dichte mit ausgeblendetem Kopfzeilenflyout verwendet.  
  
Die Kopfzeile mit hoher Dichte zeigt schreibgeschützte Werte von Feldern in der Kopfzeile an. Da der Kopf-Flyout ausgeblendet ist, können Benutzer die Feldwerte nicht bearbeiten.  
  
Die Nachricht informiert den Hersteller darüber, dass alle Felder, die dem Kopf hinzugefügt werden, schreibgeschützt sind und dass alle Felder, die der Benutzer bearbeiten soll, ebenfalls einem Abschnitt im Formular hinzugefügt werden sollten.

### <a name="header-field-values-are-not-editable-moving-a-field-from-the-body-to-the-header-will-display-as-a-read-only-value-to-maintain-editability-copy-the-field-to-the-header"></a>Kopfzeilenfeldwerte werden nicht bearbeitet: Wenn ein Feld aus dem Hauptteil in die Kopfzeile verschoben wird, wird es als schreibgeschützter Wert angezeigt. Um die Bearbeitkeit beizubehalten, kopieren Sie das Feld in die Kopfzeile.  
Diese Meldung wird im Formulardesigner nur bei Formularen mit High-Density-Kopf angezeigt, bei denen der Kopf-Flyout ausgeblendet ist.  
  
Die Kopfzeile mit hoher Dichte zeigt schreibgeschützte Werte von Feldern in der Kopfzeile an. Da der Kopf-Flyout ausgeblendet ist, können Benutzer die Feldwerte nicht bearbeiten.  

Die Nachricht informiert den Ersteller darüber, dass er versucht, ein Feld aus dem Formularkörper in den Formularkopf zu verschieben. Hierdurch wird das Feld zu einem schreibgeschützten Feld. Der Entwickler kann entscheiden, ob er das Feld in die Kopfzeile verschiebt oder der Kopfzeile eine Kopie des Felds hinzufügt. Durch das Verschieben des Felds in die Kopfzeile ist das Feld in der ursprünglichen Position im Formularhauptteil für Benutzer nicht mehr zur Bearbeitung verfügbar. Wenn Sie eine Kopie des Feldes in die Kopfzeile einfügen, bleibt das Feld an der ursprünglichen Position, so dass die Benutzer es weiterhin im Formular bearbeiten können.

### <a name="form-headers-now-default-to-high-density-to-display-more-data-use-the-new-form-designer-to-edit-header-density"></a>Formularkopfzeilen werden jetzt standardmäßig hohe Dichte, um mehr Daten anzuzeigen. Verwenden Sie den neuen Formulardesigner, um die Kopfzeilendichte zu bearbeiten.  
Diese Nachricht wird im klassischen Formulardesigner angezeigt, wenn ein Entwickler ein Hauptformular zum Bearbeiten öffnet, das so konfiguriert ist, dass eine Kopfzeile mit niedriger Dichte verwendet wird.  
  
Diese Nachricht trägt dazu bei, das Bewusstsein für die hohe Header-Dichte und ihre Vorteile zu erhöhen und dass die Hersteller den neuen Formular-Designer zur Konfiguration der Header-Dichte verwenden sollten.  

Diese Nachricht wird im klassischen Formulardesigner angezeigt, wenn ein Entwickler ein Hauptformular zum Bearbeiten öffnet, das so konfiguriert ist, dass eine Kopfzeile mit niedriger Dichte verwendet wird. 

Die Botschaft trägt dazu bei, das Bewusstsein für den High-Density-Kopf und seine Vorteile zu schärfen, und dass Hersteller den neuen Formulardesigner verwenden sollten, um die Kopfdichte zu konfigurieren.  

### <a name="this-form-is-using-high-density-header-for-the-best-authoring-experience-with-this-form-use-the-new-form-designer"></a>Dieses Formular verwendet eine Kopfzeile mit hoher Dichte. Verwenden Sie den neuen Formulardesigner, um eine optimale Erstellung mit diesem Formular zu gewährleisten. 
Diese Meldung wird im klassischen Formulardesigner angezeigt, wenn ein Ersteller ein Hauptformular zur Bearbeitung öffnet und konfiguriert ist, um einen Kopf mit hoher Dichte zu verwenden.  
  
Der klassische Formulardesigner bietet keine WYSIWYG-Authoring-Umgebung. Außerdem erkennt er nicht die Auswirkungen von Änderungen, die Entwickler an der Formularkopfzeile vornehmen, und gibt keine entsprechenden Warnungen aus. Wenn Sie beispielsweise ein Formular bearbeiten, das eine Kopfzeile mit hoher Dichte und ausgeblendetem Kopfflyout verwendet, wird der klassische Formulardesigner die Ersteller nicht daran hindern, mehr als vier Felder zur Kopfzeile hinzuzufügen, obwohl dieses Feld für die Benutzer nicht verfügbar sein wird.  
  
Die Nachricht informiert den Ersteller darüber, dass er bei der Bearbeitung eines Formulars, das einen Kopf mit hoher Dichte verwendet, den neuen Formulardesigner verwenden sollte. Dies stellt sicher, dass der Entwickler die Auswirkungen der Änderungen auf die Formularkopfzeile berücksichtigt.

## <a name="see-also"></a>Siehe auch
[Übersicht über den modellgestützten Formulardesigner](form-designer-overview.md)  
[Erstellen, Bearbeiten oder Konfigurieren von Formularen mit dem Formulardesigner](create-and-edit-forms.md)  
[Hinzufügen, Konfigurieren, Verschieben oder Löschen von Feldern in einem Formular](add-move-or-delete-fields-on-form.md)  
[Hinzufügen, Konfigurieren, Verschieben oder Löschen von Komponenten in einem Formular](add-move-configure-or-delete-components-on-form.md)  
[Hinzufügen, Konfigurieren, Verschieben oder Löschen von Abschnitten in einem Formular](add-move-or-delete-sections-on-form.md)  
[Hinzufügen, Konfigurieren, Verschieben oder Löschen von Registerkarten in einem Formular](add-move-or-delete-tabs-on-form.md)  
[Hinzufügen und Konfigurieren einer Unterraster-Komponente in einem Formular](form-designer-add-configure-subgrid.md)  
[Hinzufügen und Konfigurieren einer Schnellansichts-Komponente in einem Formular](form-designer-add-configure-quickview.md)  
[Konfigurieren einer Suchkomponente in einem Formular](form-designer-add-configure-lookup.md)  
[Verwenden der Strukturansicht im Formulardesigner](using-tree-view-on-form.md)  
[Erstellen und Bearbeiten von Feldern](../common-data-service/create-edit-field-portal.md)  
