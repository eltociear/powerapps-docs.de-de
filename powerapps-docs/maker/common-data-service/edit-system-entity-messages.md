---
title: Bearbeiten von Systementitätsnachrichten mit PowerApps | MicrosoftDocs
description: 'Erfahren Sie, wie Systementitätsnachrichten bearbeitet werden'
ms.custom: ''
ms.date: 05/15/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: 3ccbd8de-8d6f-4058-87f7-15463667cfc6
caps.latest.revision: 41
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="edit-system-entity-messages"></a>Bearbeiten von Systementitätenmeldungen

Der standardmäßige Anzeigename einiger Systementitäten wird in den Text- und Fehlermeldungen der Benutzeroberfläche im Common Data Service verwendet. Wenn Sie den Anzeigenamen ändern, sollten Sie auch alle Meldungen ändern, die den Standard-Anzeigenamen verwenden. Wenn Sie zum Beispiel den Anzeigenamen von *Firma* zu *Unternehmen* ändern, könnten Sie immer noch eine Fehlermeldung mit dem alten Namen sehen.  

Sie können Systemmeldungen nicht über das PowerApps-Portal bearbeiten, Sie müssen den Lösungs-Explorer verwenden.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

Wenn Sie im Lösungsexplorer -Explorer unter der Entität einen **Nachrichten**-Knoten sehen, können Sie Text mit Bezug zum Originalanzeigenamen der Entität ändern. 

![Entitätsmeldungen](../model-driven-apps/media/entity-messages.png)

Die Bearbeitung dieses Textes ist ganz einfach. Doppelklicken Sie auf die Nachricht, um ein Formular mit drei Felder anzuzeigen:  
  
|Feld|Beschreibung|  
|-----------|-----------------|  
|**Standardanzeigezeichenfolge**|Zeigt den Originaltext an.|  
|**Benutzerdefinierte Anzeigezeichenfolge**|Bearbeiten Sie diesen Text, um die Anzeigezeichenfolge zu ändern.|  
|**Kommentar**|(Optional). Geben Sie einen Kommentar zu Ihren Änderungen und den Gründen dafür ein.|  
  
Der Meldungstext kann Platzhalter enthalten. Dies sind Zahlen in geschweiften Klammern. Beispiel: `{0}`. Diese Platzhalter ermöglichen das Einfügen von Text in der Meldung. Achten Sie beim Bearbeiten von Meldungen darauf, diese Platzhalter stehen zu lassen. 

Wählen Sie ![Speichern](media/save-entity-icon-solution-explorer.png) aus, um Ihre Änderungen zu speichern. Wählen Sie **Speichern und Schließen**, um das Formular beim Speichern zu schließen.

> [!NOTE]
> Obwohl die Benutzeroberfläche, die zum Bearbeiten von System-Entitätsnachrichten verwendet wird, viele Verweise auf Entitätsnamen enthält, enthält sie nicht alle. Eine umfassendere Methode finden Sie unter [Aktualisieren des lokalisierbaren Texts in der Ausgangssprache](../model-driven-apps/translate-localizable-text.md#updating-localizable-text-in-the-base-language)

## <a name="programmatically-update-entity-display-strings"></a>Programmgesteuertes Aktualisieren von Entitätsanzeigezeichenfolgen

Für Entwickler, die nach einer Möglichkeit suchen, mit diesen im Code zu arbeiten, werden die Anzeigezeichenfolgen in der Entität [DisplayString](../../developer/common-data-service/reference/entities/displaystring.md) gespeichert. 

Die `DisplayString` Entität enthält nicht die standardmäßigen Anzeigezeichenfolgen. Die beiden Attribute für die Entität, die Text enthalten, sind [CustomDisplayString](../../developer/common-data-service/reference/entities/displaystring.md#BKMK_CustomDisplayString) und [PublishedDisplayString](../../developer/common-data-service/reference/entities/displaystring.md#BKMK_PublishedDisplayString) . Standardmäßig sind diese Attributwerte Null , es sei denn, die Anzeigezeichenfolge wurde angepasst und veröffentlicht. Der `PublishedDisplayString`-Wert ist schreibgeschützt und entspricht der aktuell veröffentlichten `CustomDisplayString`.
 
## <a name="see-also"></a>Siehe auch
[Bearbeiten einer Entität](edit-entities.md)<br />
[Übersetzen von lokalisierbarem Text für modellgesteuerte Anwendungen](../model-driven-apps/translate-localizable-text.md)
