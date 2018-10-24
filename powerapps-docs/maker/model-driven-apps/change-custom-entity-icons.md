---
title: Ändern von benutzerdefinierten Entitätssymbolen in modellgesteuerten Apps in PowerApps | Microsoft-Dokumentation
definition: Learn how to change the icon for a custom entity
ms.custom: ''
ms.date: 05/17/2018
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
ms.assetid: 477f9792-8207-49ef-8968-45274b5355a8
caps.latest.revision: 19
ms.author: matp
manager: kvivek
tags:
- Links to topic not migrated
ms.openlocfilehash: c625ac14905e49879eb6dc93eff706a7dab18433
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39688630"
---
# <a name="change-model-driven-app-custom-entity-icons"></a>Ändern von benutzerdefinierten Entitätssymbolen in modellgesteuerten Apps 

Wenn Sie eine benutzerdefinierte Entität erstellen, wird ihr automatisch ein Standardsymbol zugewiesen. Alle benutzerdefinierten Entitäten verwenden standardmäßig das gleiche Symbol. Mit benutzerdefinierten Symbolen können Sie unterscheiden, wie Ihre benutzerdefinierten Entitäten aussehen. Sie können nicht die Symbole ändern, die Systementitäten zugeordnet sind.  
  
 Für jede benutzerdefinierte Entität lassen sich drei Typen von Entitätssymbolen hochladen. 

|Symboltyp  |Beschreibung  |
|---------|---------|
|**Symbol „Einheitliche Oberfläche“**|Skalierbares Vektorgrafiksymbol im SVG-Format |
|**Symbol in Webanwendung**|Bild im Format SVG, GIF, PNG oder JPG mit der Größe 16x16 Pixel|
|**Symbol für Entitätsformulare**|Bild im Format SVG, GIF, PNG oder JPG mit der Größe 32x32 Pixel|

> [!NOTE]
> Bilddateien dürfen nicht größer als 10 Kilobyte sein.
>
> Wenn Sie ein skalierbares Vektorgrafikbild (SVG) als **Symbol in Webanwendung** oder **Symbol für Entitätsformulare** verwenden, muss die Standardgröße festgelegt sein. Da SVG ein XML-Dokument ist, können Sie die Werte für die [Breite](https://developer.mozilla.org/docs/Web/SVG/Attribute/width) und [Höhe](https://developer.mozilla.org/docs/Web/SVG/Attribute/height) des [SVG](https://developer.mozilla.org/docs/Web/SVG/Element/svg)-Elements mit einem Text-Editor bearbeiten, um die Standardgröße für das Bild festzulegen.

Jeder Symboltyp wird als Webressource gespeichert. Sie können entweder zuerst die Webressourcen erstellen und dann die Symbole festlegen, die sie verwenden, oder die neue Webressource im Dialogfeld **Suchdatensatz** erstellen, indem Sie beim Festlegen des Werts **Neu** auswählen. Weitere Informationen finden Sie unter [Erstellen oder Bearbeiten von Webressourcen zum Erweitern einer App](create-edit-web-resources.md).

## <a name="set-the-icons-for-a-custom-entity"></a>Festlegen von Symbolen für eine benutzerdefinierte Entität

Sie müssen Entitätssymbole im Projektmappen-Explorer festlegen.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

### <a name="set-entity-icons"></a>Festlegen von Entitätssymbolen

1. Wählen Sie in der Befehlsleiste **Symbole aktualisieren** aus.  
  
2. Wählen Sie im Dialogfeld **Neue Symbole auswählen** auf der Registerkarte **Webclient** unter **Symbol in Webanwendung** oder **Symbol für Entitätsformulare** rechts neben **Neues Symbol** die Schaltfläche **Durchsuchen** und die ![Suchschaltfläche](media/lookup-button-4.gif) aus.
3. Wählen oder erstellen Sie die entsprechende Webressource, und wählen Sie dann **OK**. 
4. Gehen Sie auf der Registerkarte **Einheitliche Oberfläche** genauso vor wie für das Feld **Neues Symbol**.
5. Wählen Sie **OK** zum Schließen des Dialogfelds **Neue Symbole auswählen** aus.
6. Wählen Sie in der Befehlsleiste im Menü **Datei** **Speichern** aus.  
7. Wenn Ihre Änderungen abgeschlossen sind, veröffentlichen Sie sie. Wählen Sie in der Befehlsleiste **Veröffentlichen** aus, während die Entität im Projektmappen-Explorer ausgewählt ist.
  
## <a name="community-tools"></a>Communitytools

**[Iconator](https://www.xrmtoolbox.com/plugins/MscrmTools.Iconator/)** ist ein Tool, das die XrmToolBox-Community für Dynamics 365 Customer Engagement entwickelt hat. [Entwicklertools für Common Data Service für Apps](https://docs.microsoft.com/dynamics365/customer-engagement/developer/developer-tools) bietet eine Übersicht über Tools, die die Community entwickelt hat.

> [!NOTE]
> Communitytools sind kein Produkt von Microsoft, sodass der Support diese nicht abdeckt. Wenn Sie Fragen zum Tool haben, wenden Sie sich bitte an den Herausgeber. Weitere Informationen finden Sie unter [XrmToolBox](https://www.xrmtoolbox.com).

## <a name="next-steps"></a>Nächste Schritte  
[Erstellen einer Entität](../common-data-service/create-edit-entities.md)<br />
[Bearbeiten einer Entität](../common-data-service/edit-entities.md)
