---
title: Bearbeiten von Systementitätsmeldungen mit PowerApps | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Systementitätsmeldungen bearbeiten.
ms.custom: ''
ms.date: 05/15/2018
ms.reviewer: ''
ms.service: crm-online
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
ms.openlocfilehash: 797d6855bea421abd90752dd9ae0ad73a9d92f38
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39686705"
---
# <a name="edit-system-entity-messages"></a>Systementitätsmeldungen bearbeiten

Der standardmäßige Anzeigename einiger Systemeinheiten wird im Text der Benutzeroberfläche und in Fehlermeldungen im Common Data Service für Apps verwendet. Wenn Sie den Anzeigenamen ändern, sollten Sie auch alle Meldungen aktualisieren, die den Standardanzeigenamen verwenden. Wenn Sie beispielsweise den Anzeigenamen von *Konto* in *Firma* ändern, könnten dennoch eine Fehlermeldung mit dem alten Namen angezeigt werden.  

Sie können Systemmeldungen nicht über das PowerApps-Portal bearbeiten, Sie müssen den Projektmappen-Explorer verwenden.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

Wenn Sie im Projektmappen-Explorer unterhalb der Entität einen **Meldungen**-Knoten sehen, können Sie bestimmte Texte bearbeiten, die Referenzen auf den ursprünglichen Anzeigenamen der Entität enthalten. 

![Entitätsmeldung](../model-driven-apps/media/entity-messages.png)

Das Bearbeiten dieses Textes ist einfach. Doppelklicken Sie auf die Meldung. um ein Formular mit drei Feldern anzuzeigen:  
  
|Feld|Beschreibung|  
|-----------|-----------------|  
|**Standardanzeigezeichenfolge**|Zeigt den ursprünglichen Text.|  
|**Benutzerdefinierte Anzeigezeichenfolge**|Bearbeiten Sie diesen Text, um die Anzeigezeichenfolge zu ändern.|  
|**Kommentar**|Optional. Fügen Sie einen Kommentar darüber ein, was Sie geändert haben und warum.|  
  
Ein Teil des Meldungstextes kann Platzhalter enthalten. Diese Platzhalter sind Zahlen mit Klammern auf beiden Seiten. Beispiel: `{0}`. Diese Platzhalter ermöglichen das Einfügen von Text in die Meldung. Stellen Sie beim Bearbeiten der Nachrichten sicher, dass Sie diese Platzhalter beibehalten. 

Wählen Sie ![Speichern](media/save-entity-icon-solution-explorer.png) aus, um Ihre Änderungen zu speichern. Klicken Sie auf **Speichern und schließen**, um das Formular beim Speichern zu schließen.

> [!NOTE]
> Obwohl die Benutzeroberfläche, die für die Bearbeitung von Systementitätsmeldungen verfügbar ist, viele Referenzen auf Entitätsnamen enthält, enthält sie nicht alle. Informationen zu einem umfassenderen Ansatz finden Sie unter [Aktualisieren von lokalisierbarem Text in der Basissprache](../model-driven-apps/translate-localizable-text.md#updating-localizable-text-in-the-base-language).

## <a name="programmatically-update-entity-display-strings"></a>Programmgesteuertes Aktualisieren der Entitätsanzeigezeichenfolgen

Für Entwickler, die nach einer Möglichkeit suchen, mit diesen Zeichenfolgen im Code zu arbeiten, werden die Anzeigezeichenfolgen in der Entität [DisplayString](../../developer/common-data-service/reference/entities/displaystring.md) gespeichert. 

Die Entität `DisplayString` enthält nicht die standardmäßigen Anzeigezeichenfolgen. Die beiden Attribute für diese Entität, die Text enthalten, sind [CustomDisplayString](../../developer/common-data-service/reference/entities/displaystring.md#BKMK_CustomDisplayString) und [PublishedDisplayString](../../developer/common-data-service/reference/entities/displaystring.md#BKMK_PublishedDisplayString). Standardmäßig sind diese Attributwerte Null, es sei denn, die Anzeigestruktur wurde angepasst und veröffentlicht. Der Wert `PublishedDisplayString` ist schreibgeschützt und gibt die derzeit veröffentlichte `CustomDisplayString` an.
 
## <a name="see-also"></a>Siehe auch
[Bearbeiten einer Entität](edit-entities.md)<br />
[Übersetzen des lokalisierbaren Textes für modellgesteuerte Apps](../model-driven-apps/translate-localizable-text.md)
