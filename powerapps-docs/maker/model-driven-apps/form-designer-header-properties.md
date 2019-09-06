---
title: Konfigurieren von Kopfzeileneigenschaften im Formulardesigner | MicrosoftDocs
ms.custom: ''
ms.date: 08/02/2019
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
  - PowerApps maker portal impact
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="configure-header-properties-in-the-form-designer"></a>Konfigurieren von Kopfzeileneigenschaften im Formulardesigner
Entwickler können die Dichte modellgesteuerter App-Formularkopfzeilen steuern, um die Anforderungen von Benutzern zu erfüllen, die ein Formular verwenden.

## <a name="high-density-header"></a>Kopfzeile mit hoher Dichte
Formularkopfzeilen mit hoher Dichte stellen sicher, dass wichtige Informationen immer für die Benutzer sichtbar sind. Bei Verwendung einer Kopfzeile mit hoher Dichte werden Datensatztitel niemals abgeschnitten. Sogar lange Datensatztitel werden mit mehreren Zeilen angezeigt. Entsprechend stellen Kopfzeilen mit hoher Dichte ebenfalls sicher, dass vier Feldwerte direkt in der Kopfzeile sichtbar sind und nicht abgeschnitten oder ausgeblendet werden.  

Um sicherzustellen, dass wichtige Informationen immer angezeigt werden, zeigt das Framework schreibgeschützten Feldwerte an und Benutzer können die anzeigten Feldwerte in der Kopfzeile nicht direkt bearbeiten. Visualisierungen wie benutzerdefinierte Steuerelemente oder Webressourcen sind auch nicht zulässig.

Wenn ein Formular keine Kopfzeilendichte angibt oder wenn ein neues Formular erstellt wird, wird vom Framework standardmäßig eine Kopfzeile mit hoher Dichte verwendet.

> [!div class="mx-imgBorder"] 
> ![Kopfzeile mit hoher Dichte](media/form-header-high-density.png "Kopfzeile mit hoher Dichte")
    
## <a name="low-density-header"></a>Kopfzeile mit niedriger Dichte
Formularkopfzeilen mit niedriger Dichte ermöglichen Benutzern, die Feldwerte direkt in der Kopfzeile zu bearbeiten. Visualisierungen wie benutzerdefinierte Steuerelemente oder Webressourcen sind auch zulässig.  
  
Allerdings werden als Folge häufig wichtige Informationen abgeschnitten oder sind nicht wirklich sichtbar. Kopfzeilen mit niedriger Dichte schneiden den Datensatztitel sowie die Feldwerte ab, die in der Kopfzeile angezeigt werden. Häufig sind nur ein oder zwei Felder direkt in der Kopfzeile und im Restüberlauf sichtbar und werden in einem Flyout angezeigt, das einen zusätzlichen Klick erfordert.

> [!div class="mx-imgBorder"] 
> ![Kopfzeile mit niedriger Dichte](media/form-header-low-density.png "Kopfzeile mit niedriger Dichte")

### <a name="configuring-header-density"></a>Konfigurieren von Kopfzeilendichte

Um die Kopfzeilendichte eines modellgesteuerten Formular zu konfigurieren, führen Sie die folgenden Schritte aus.
1.  Öffnen Sie den Formulardesigner, [um ein Formular zu erstellen oder zu bearbeiten](create-and-edit-forms.md).
2.  Wählen Sie die Formularkopfzeile aus, indem Sie die Kopfzeile in der Formularvorschau auswählen oder mithilfe der [Strukturansicht](using-tree-view-on-form.md).
3.  Im Eigenschaftenbereich wählen Sie **Hohe Dichte**, um die Formularkopfzeile mit hoher Dichte zu verwenden, oder löschen Sie die Auswahl, um eine Formularkopfzeile mit niedriger Dichte zu verwenden.
4.  Wählen Sie in der Befehlsleiste **Speichern** aus, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** aus, wenn Sie die Änderungen speichern und für Benutzer sichtbar anzeigen möchten.

> [!NOTE]
> Verwenden Sie den neuen Formulardesigner. Der klassische Formulardesigner bietet keine Möglichkeit, die Kopfzeilendichte zu konfigurieren.

## <a name="header-flyout"></a>Kopfzeilenflyout
Das Kopfzeilenflyout wird angezeigt, wenn Benutzer das Chevron in der Formularkopfzeile auswählen. Benutzer können die Eingabefeldwerte bearbeiten. Zudem zeigt es Visualisierungen wie benutzerdefinierte Steuerelemente oder Webressourcen an, die Teil der Formularkopfzeile sind.

Die Verhaltensweisen des Kopfzeilenflyouts ändert sich abhängig von der Kopfzeilendichtekonfiguration.

### <a name="high-density-header-flyout"></a>Kopfzeilenflyout mit hoher Dichte
Bei einer Formularkopfzeile mit hoher Dichte zeigt das Kopfzeilenflyout alle Kopfzeilenfelder einschließlich der vier Felder an, die direkt in der Kopfzeile angezeigt werden. Das Framework werden standardmäßig das Kopfzeilenflyout, wenn eine Kopfzeile mit hoher Dichte verwendet wird. Entwickler können die Sichtbarkeit des Kopfzeilenflyouts mit einer Kopfzeile mit hoher Dichte steuern.

> [!div class="mx-imgBorder"] 
> ![Kopfzeilenflyout mit Kopfzeile mit hoher Dichte](media/form-header-flyout-high-density.png "Kopfzeilenflyout mit Kopfzeile mit hoher Dichte")

### <a name="low-density-header-flyout"></a>Kopfzeilenflyout mit niedriger Dichte
Bei einer Formularkopfzeile mit niedriger Dichte zeigt das Kopfzeilenflyout nur Überlauffelder an, z. B. Felder, die das Formular basierend auf der Breite des Formulars nicht direkt in der Kopfzeile anzeigen kann. Das Kopfzeilenflyout wird zudem automatisch basierend auf der Anzahl von Feldern in der Kopfzeile und der Breite des Formulars angezeigt oder ausgeblendet. Entwickler können die Sichtbarkeit des Kopfzeilenflyouts mit einer Kopfzeile mit niedriger Dichte nicht steuern.

> [!div class="mx-imgBorder"] 
> ![Kopfzeilenflyout mit Kopfzeile mit niedriger Dichte](media/form-header-flyout-low-density.png "Kopfzeilenflyout mit Kopfzeile mit niedriger Dichte")

### <a name="show-or-hide-the-header-flyout"></a>Anzeigen oder Ausblenden des Kopfzeilenflyouts
Wenn Sie das Kopfzeilenflyout für ein modellgesteuertes Formular ein- oder ausblenden möchten, führen Sie die folgenden Schritte aus.

1.  Öffnen Sie den Formulardesigner, [um ein Formular zu erstellen oder zu bearbeiten](create-and-edit-forms.md).
2.  Wählen Sie die Formularkopfzeile in der Formularvorschau aus oder verwenden Sie die [Strukturansicht](using-tree-view-on-form.md), um sie auszuwählen.
3.  Im Eigenschaftenbereich wählen Sie **Hohe Dichte** aus, um die Formularkopfzeile mit hoher Dichte zu verwenden. 
4.  Im Eigenschaftenbereich wählen Sie **Kopfzeilenflyout anzeigen** aus, um das Kopfzeilenflyout anzuzeigen, oder löschen Sie die Auswahl, um das Kopfzeilenflyout auszublenden.
5.  Wählen Sie in der Befehlsleiste **Speichern** aus, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** aus, wenn Sie die Änderungen speichern und für Benutzer sichtbar anzeigen möchten.

> [!NOTE]
> - Verwenden Sie den neuen Formulardesigner, der klassische Formulardesigner bietet keine Möglichkeit, das Kopfzeilenflyout ein- oder auszublenden.   
> - Die Sichtbarkeit des Kopfzeilenflyouts kann nur gesteuert werden, wenn Sie eine Formularkopfzeile mit hoher Dichte verwenden. Bei Verwendung einer Kopfzeile mit niedriger Dichte wird das Kopfzeilenflyout zudem automatisch basierend auf der Anzahl von Feldern in der Kopfzeile und der Breite des Formulars angezeigt oder ausgeblendet.

## <a name="form-designer-messages-related-to-form-headers"></a>Formulardesigner-Meldungen in Verbindung mit Formularkopfzeilen
Wenn Sie Formulare mit dem neuen oder klassischen Formulardesigner bearbeiten, werden mehrere Meldungen in Verbindung mit Formularkopfzeilen . Unten können Sie die Details jeder Meldung finden und den Grund für die Meldung.

### <a name="weve-upgraded-your-form-to-show-a-high-density-header-that-displays-more-data-you-can-edit-this-setting-in-the-properties-of-the-header"></a>Wir haben Ihr Formular aktualisiert, sodass eine Kopfzeile mit hoher Dichte angezeigt wird, die mehr Daten enthält. Sie können diese Einstellung in den Eigenschaften der Kopfzeile bearbeiten. 
Diese Meldung wird im Formulardesigner angezeigt, wenn ein Entwickler ein neues Hauptformular (über die Aktion „Speichern als“) erstellt oder bearbeitet, das nicht bereit für die Kopfzeilendichte konfiguriert wurde.  
  
Das Framework verwendet standardmäßig eine Kopfzeile mit hoher Dichte und diese Meldung informiert Entwickler über dieses Verhalten. Entwickler können den Frameworkstandard jederzeit überschreiben, indem Sie die Formularkopfzeilendichte manuell konfigurieren, wie weiter oben erläutert.

### <a name="this-form-isnt-using-high-density-header-access-the-setting-in-the-header-properties-high-density-header-helps-display-more-data"></a>In diesem Formular wird keine Kopfzeile mit hoher Dichte verwendet. Greifen Sie auf die Einstellung in den Kopfzeileneigenschaften zu. Bei Kopfzeilen mit hoher Dichte können mehr Daten angezeigt werden. 
Diese Nachricht wird im Formulardesigner angezeigt, wenn ein Entwickler ein Hauptformular zum Bearbeiten öffnet, das so konfiguriert ist, dass eine Kopfzeile mit niedriger Dichte verwendet wird.      
  
Diese Meldung unterstützt das Bewusstsein über Kopfzeilen mit hoher Dichte und ihre Vorteile.

### <a name="field-moved-to-header-flyout-the-header-supports-displaying-up-to-four-read-only-field-values-the-field-field-display-name-will-now-only-be-available-from-the-flyout"></a>Feld wurde in das Kopfzeilenflyout verschoben: Die Kopzeile unterstützt die Anzeige von maximal vier schreibgeschützten Feldwerten. Das Feld *[Feldanzeigename]* ist jetzt nur im Flyout verfügbar.
Diese Meldung wird im Formulardesigner angezeigt, wenn ein Formular eine Kopfzeile mit hoher Dichte mit sichtbarem Kopfzeilenflyout verwendet.  
  
Kopfzeilen mit hoher Dichte zeigen schreibgeschützte Werte für die ersten vier Felder in der Kopfzeile an. Wenn Entwickler ein Feld in der Kopfzeile in den ersten vier Positionen hinzufügen, wird ein vorhandenes Feld, das direkt in der Kopfzeile angezeigt wurde, erweitert und ist nur im Kopfzeilenflyout sichtbar.      
  
Diese Meldung informiert den Entwickler über die Änderung und bestätigt, ob die Aktion fortgesetzt werden soll.

### <a name="header-field-limit-exceeded-the-header-supports-displaying-up-to-four-read-only-field-values-remove-unused-fields-to-add-more"></a>Der Grenzwert für Kopfzeilenfelder wurde überschritten: Die Kopzeile unterstützt die Anzeige von maximal vier schreibgeschützten Feldwerten. Entfernen Sie nicht verwendete Felder, um weitere hinzuzufügen. 
Diese Meldung wird im Formulardesigner angezeigt, wenn ein Formular eine Kopfzeile mit hoher Dichte mit ausgeblendetem Kopfzeilenflyout verwendet.  
  
Kopfzeilen mit hoher Dichte zeigen schreibgeschützte Werte für bis zu vier Feldern in der Kopfzeile an. Da das Kopfzeilenflyout ausgeblendet ist, können Benutzer keine zusätzlichen Felder sehen.  
  
Diese Nachricht informiert den Entwickler darüber, dass bereits vier Felder in der Kopfzeile enthalten sind, und verhindert das Hinzufügen von zusätzlichen Felder in der Kopfzeile, die Benutzer nicht anzeigen können.

### <a name="header-does-not-display-custom-components-the-header-supports-displaying-up-to-four-read-only-field-values-remove-the-custom-component-from-the-field-before-adding-it-to-the-header"></a>In der Kopfzeile werden keine benutzerdefinierten Komponenten angezeigt: Die Kopzeile unterstützt die Anzeige von maximal vier schreibgeschützten Feldwerten. Entfernen Sie die benutzerdefinierte Komponente aus dem Feld, bevor Sie sie in der Kopfzeile hinzufügen.  
Diese Meldung wird im Formulardesigner angezeigt, wenn ein Formular eine Kopfzeile mit hoher Dichte mit ausgeblendetem Kopfzeilenflyout verwendet.  
  
Kopfzeilen mit hoher Dichte zeigen schreibgeschützte Werte von Feldern in der Kopfzeile an. Da das Kopfzeilenflyout ausgeblendet ist, können Benutzer keine benutzerdefinierten Komponenten sehen, die den Feldern in der Kopfzeile zugeordnet werden.  
  
Diese Nachricht informiert den Entwickler darüber, dass versucht wird, ein Feld mit einer zugeordneten benutzerdefinierte Komponente zur Kopfzeile hinzufügen, und dass er die benutzerdefinierte Komponente entfernen muss, bevor er das Feld der Kopfzeile hinzufügt. Dies ist darauf zurückzuführen, dass es Benutzern nicht möglich sind, die benutzerdefinierte Komponente in der Kopfzeile zu sehen.

### <a name="header-displays-read-only-field-values-the-header-supports-displaying-up-to-four-read-only-field-values-to-provide-editability-to-the-user-add-the-field-to-a-section-in-the-form"></a>In der Kopzeile werden schreibgeschützte Feldwerte angezeigt: Die Kopzeile unterstützt die Anzeige von maximal vier schreibgeschützten Feldwerten. Um dem Benutzer Bearbeitbarkeit zu bieten, fügen Sie das Feld einem Abschnitt im Formular hinzu.  
Diese Meldung wird im Formulardesigner angezeigt, wenn ein Formular eine Kopfzeile mit hoher Dichte mit ausgeblendetem Kopfzeilenflyout verwendet.  
  
Kopfzeilen mit hoher Dichte zeigen schreibgeschützte Werte von Feldern in der Kopfzeile an. Da das Kopfzeilenflyout ausgeblendet ist, können Benutzer keine Feldwerte bearbeiten.  
  
Diese Meldung informiert den Entwickler, dass alle Felder, die der Kopfzeile hinzugefügt werden, schreibgeschützt sind und dass alle Felder, die Benutzer bearbeiten sollen, auch einem Abschnitt im Formular hinzugefügt werden sollen.

### <a name="header-field-values-are-not-editable-moving-a-field-from-the-body-to-the-header-will-display-as-a-read-only-value-to-maintain-editability-copy-the-field-to-the-header"></a>Kopfzeilenfeldwerte werden nicht bearbeitet: Wenn ein Feld aus dem Hauptteil in die Kopfzeile verschoben wird, wird es als schreibgeschützter Wert angezeigt. Um die Bearbeitkeit beizubehalten, kopieren Sie das Feld in die Kopfzeile.  
Diese Meldung wird im Formulardesigner angezeigt nur für Formulare angezeigt, die eine Kopfzeile mit hoher Dichte mit ausgeblendetem Kopfzeilenflyout verwenden.  
  
Kopfzeilen mit hoher Dichte zeigen schreibgeschützte Werte von Feldern in der Kopfzeile an. Da das Kopfzeilenflyout ausgeblendet ist, können Benutzer keine Feldwerte bearbeiten.  
  
Diese Meldung informiert den Entwickler darüber, dass versucht wird, ein Feld aus dem Formularhauptteil in die Formularkopfzeile zu verschieben. Hierdurch wird das Feld zu einem schreibgeschützten Feld. Der Entwickler kann entscheiden, ob er das Feld in die Kopfzeile verschiebt oder der Kopfzeile eine Kopie des Felds hinzufügt. Durch das Verschieben des Felds in die Kopfzeile ist das Feld in der ursprünglichen Position im Formularhauptteil für Benutzer nicht mehr zur Bearbeitung verfügbar. Wenn Kopie des Felds der Kopfzeile hinzugefügt wird, bleibt das Feld in der ursprünglichen Position unverändert, sodass sichergestellt wird, dass Benutzer es im Formularhauptteil weiterhin bearbeiten können.

### <a name="form-headers-now-default-to-high-density-to-display-more-data-use-the-new-form-designer-to-edit-header-density"></a>Formularkopfzeilen werden jetzt standardmäßig hohe Dichte, um mehr Daten anzuzeigen. Verwenden Sie den neuen Formulardesigner, um die Kopfzeilendichte zu bearbeiten.  
Diese Nachricht wird im klassischen Formulardesigner angezeigt, wenn ein Entwickler ein Hauptformular zum Bearbeiten öffnet, das so konfiguriert ist, dass eine Kopfzeile mit niedriger Dichte verwendet wird.  
  
Diese Meldung steigert das Bewusstsein über die Kopfzeile mit hoher Dichte und ihre Vorteile und darüber, dass Entwickler den neuen Formulardesigner verwenden sollen, um Kopfzeilendichte zu konfigurieren.  

### <a name="this-form-is-using-high-density-header-for-the-best-authoring-experience-with-this-form-use-the-new-form-designer"></a>Dieses Formular verwendet eine Kopfzeile mit hoher Dichte. Verwenden Sie den neuen Formulardesigner, um eine optimale Erstellung mit diesem Formular zu gewährleisten. 
 Diese Meldung wird im klassischen Formulardesigner angezeigt, wenn ein Entwickler ein Hauptformular zum Bearbeiten öffnet, das so konfiguriert ist, dass eine Kopfzeile mit hoher Dichte verwendet wird.  
  
Der klassische Formulardesigner bietet keine WYSIWYG-Authoring-Umgebung. Außerdem erkennt er nicht die Auswirkungen von Änderungen, die Entwickler an der Formularkopfzeile vornehmen, und gibt keine entsprechenden Warnungen aus. Wenn Sie beispielsweise ein Formular bearbeiten, das Kopfzeilen mit hoher Dichte mit ausgeblendetem Kopfzeilenflyout verwendet, verhindert der klassische Formulardesigner nicht, dass Entwickler mehr als vier Felder zur Kopfzeile hinzufügen, obwohl diese Felder den Benutzern nicht zur Verfügung stehen.  
  
Diese Meldung informiert den Entwickler, dass er beim Bearbeiten eines Formulars, das eine Kopfzeile mit hoher Dichte verwendet, den neuen Formulardesigner verwenden soll. Dies stellt sicher, dass der Entwickler die Auswirkungen der Änderungen auf die Formularkopfzeile berücksichtigt.

## <a name="see-also"></a>Siehe auch
[Übersicht über den modellgestützten Formulardesigner](form-designer-overview.md)  
[Erstellen oder Bearbeiten von Formularen mit dem Formulardesigner](create-and-edit-forms.md)  
[Ergänzen, Verschieben oder Löschen von Feldern in einem Formular mithilfe des Formulardesigners](add-move-or-delete-fields-on-form.md)  
[Hinzufügen, Verschieben oder Löschen von Abschnitten in einem Formular mithilfe des Formulardesigners](add-move-or-delete-sections-on-form.md)  
[Hinzufügen, Verschieben oder Löschen von Registerkarten in einem Formular mithilfe des Formulardesigners](add-move-or-delete-tabs-on-form.md)  
[Im Formulardesigner verfügbare Eigenschaften](form-designer-properties.md)  
[Konfigurieren von Kopfzeileneigenschaften im Formulardesigner](form-designer-header-properties.md)  
[Verwenden der Strukturansicht im Formulardesigner](using-tree-view-on-form.md)  
[Erstellen und Bearbeiten von Feldern](../common-data-service/create-edit-field-portal.md)
