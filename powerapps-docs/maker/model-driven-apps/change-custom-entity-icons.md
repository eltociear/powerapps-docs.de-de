---
title: Ändern der benutzerdefinierten Entitätssymbole der modellgesteuerten App in PowerApps | Microsoft-Dokumentation
definition: Learn how to change the icon for a custom entity
ms.custom: ''
ms.date: 05/17/2018
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
ms.assetid: 477f9792-8207-49ef-8968-45274b5355a8
caps.latest.revision: 19
ms.author: matp
manager: kvivek
tags:
- Links to topic not migrated
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: f7e23ece0ee37d15ef5401421d078e81dd5d590c
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2700781"
---
# <a name="change-model-driven-app-custom-entity-icons"></a>Ändern der Modell-angetriebenen App der benutzerdefinierten Entität-Symbole 

Wenn Sie eine benutzerdefinierte Entität erstellen, wird dieser automatisch ein Standardsymbol zugewiesen. Alle benutzerdefinierten Entitäten verwenden dasselbe standardmäßig Symbol. Nutzen Sie benutzerdefinierte Symbole, um zu unterscheiden, wie die benutzerdefinierten Entitäten aussehen. Sie können die Symbole, die Systementitäten zugewiesen sind, nicht ändern.  
  
 Sie können drei Arten von Entitätssymbolen für jede benutzerdefinierte Entitä hochladen: 

|Symbol-Typ  |Beschreibung  |
|---------|---------|
|**Symbol mit einheitlicher Oberfläche**|Er muss ein skalierbares Symbol mit Vektor grafik (.svg) sein |
|**Symbol in Webanwendung**|Ein .svg, .GIF, .png oder .jpg Formatbild, 16x16 Pixel.|
|**Symbol für Entitätsformulare**.|Ein .svg, .GIF, .png oder .jpg Formatbild, 32x32 Pixel.|

> [!NOTE]
> Alle Bilddateien dürfen nicht mehr an 10 GB groß sein.
>
> Wenn Sie ein skalierbares Vektorgrafik (.svg) Bild als **Symbol in Webanwendung** oder als **Symbol für Entitätsformulare** verwenden, muss die Standardgröße festgelegt sein. Da SVG ein XML-Dokument ist, können Sie das Element [svg](https://developer.mozilla.org/docs/Web/SVG/Element/svg) und [Breite](https://developer.mozilla.org/docs/Web/SVG/Attribute/width) die Werte [Höhe](https://developer.mozilla.org/docs/Web/SVG/Attribute/height) in einem Texteditor bearbeiten, um die Standardgröße zum Bild definieren.

Jeder Symboltyp wird als Webressource gepeichert. Sie können zuerst die Webressourcen erstellen und Symbole anschließend festlegen, um sie zu verwenden, oder Sie können die neuen Webressourcen des Dialogfelds **Nachschlagedatensatz** erstellen, indem Sie **Neu** aktivieren, wenn Sie den Wert festlegen. Weitere Informationen: [Erstellen oder Bearbeiten von Webressourcen, um eine App zu erweitern](create-edit-web-resources.md)

## <a name="set-the-icons-for-a-custom-entity"></a>Legt die Symbole für eine benutzerdefinierte Entität fest.

Sie müssen Lösungs-Explorer verwenden, um Entitätssymbole festzulegen.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

### <a name="set-entity-icons"></a>Entitätssymbol festlegen

1. Wählen Sie auf der Befehlsleiste **Symbol Aktualisieren** aus.  
  
2. Klicken Sie im Dialogfeld **Neue Symbole auswählen** in der Registerkarte **Webclient**unter **Symbol in Webanwendung** oder **Symbol für Entitätsformulare** rechts von **Neues Symbol** auf die Schaltfläche **Durchsuchen** ![Schaltfläche suchen](media/lookup-button-4.gif).
3. Aktivieren oder erstellen Sie die entsprechende Webressource, und wählen Sie dann **OK** aus. 
4. Auf der Registerkarte **Einheitliche Oberfläche** machen Sie das gleiche für das Feld **Neues Symbol**.
5. Wählen Sie auf **OK** aus, um den Dialog **Neue Symbole auswählen** zu schließen.
6. Wählen Sie auf der Befehlsleiste im Menü **Datei** die Option **Speichern** aus.  
7. Sind die Anpassungen vollständig, können sie veröffentlicht werden. Wählen Sie **Veröffentlichen** in der Befehlsleiste aus, wenn die ausgewählte Entität im Lösungs-Edplorer ausgewählt ist.
  
## <a name="community-tools"></a>Community-Tools

**[Iconator](https://www.xrmtoolbox.com/plugins/MscrmTools.Iconator/)** ist ein Werkzeug, das die XrmToolBox-Community für PowerApps entwickelt hat. Weitere Informationen finden Sie im Thema [Entwicklertools für Common Data Service](/powerapps/developer/common-data-service/developer-tools) für von der Community entwickelte Tools.

> [!NOTE]
> Die Communitytools sind kein Produkt von Microsoft und es wird kein Support für die Communitytools angeboten. Wenn Sie Fragen zu dem Tool haben, setzen Sie sich bitte mit dem Herausgeber in Verbindung. Weitere Informationen: [XrmToolBox](https://www.xrmtoolbox.com).

## <a name="next-steps"></a>Nächste Schritte  
[Erstellen einer Entität](../common-data-service/create-edit-entities.md)<br />
[Bearbeiten einer Entität](../common-data-service/edit-entities.md)
