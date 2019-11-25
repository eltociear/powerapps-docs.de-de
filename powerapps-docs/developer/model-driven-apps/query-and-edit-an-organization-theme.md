---
title: Abfragen und Bearbeiten eines Organisationsdesigns (modellgestützte Apps) | MicrosoftDocs
description: Infos zum Definieren und Anwenden von Sichtdesignen für eine Organisation. Dies bietet eine unterstützte Methode, um das Logo und die Farbauswahl einer Organisation für die Anwendung zu übernehmen.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8abda26be50d31f734d3143c9cfa79b38fd3f130
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753598"
---
# <a name="query-and-edit-an-organization-theme"></a>Abfragen und Bearbeiten eines Organisationsdesigns

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/query-and-edit-an-organization-theme -->

Sie können visuelle Designs für eine Organisation definieren und anwenden. Dies bietet eine unterstützte Methode, um das Logo und die Farbauswahl einer Organisation für die Anwendung zu übernehmen. Sie können ein angepasstes Design für Ihre Anwendung erstellen, indem Sie Änderungen an den Standardfarben und visuellen Elementen im nicht benutzerdefinierten System modellgestützter Apps vornehmen. Sie können beispielsweise Ihr persönliches Produktbranding erstellen, ein Unternehmenslogo hinzufügen und entitätsspezifischen Farbton zur Verfügung stellen. Die Designfarben werden global bei der Anwendung übernommen, mit Ausnahme einiger Vorgängerbereiche.  
  
<!-- [!NOTE]
> [!INCLUDE[cc_feature_included_with_2015_update_1_admins](../../includes/cc-feature-included-with-2015-update-1-admins.md)]  -->
  
 Die Designanpassung wird in dieser Version nur für die Webanwendung unterstützt. Änderungen, die für das Design einer Organisation vorgenommen werden, sind nicht in Lösungen enthalten, die von der Organisation exportiert werden. Sie können mehrere Designs definieren, jedoch kann nur eins als das Standarddesign festgelegt und veröffentlicht werden.  
  
 Video: [Designs](https://go.microsoft.com/fwlink/p/?LinkId=529568)  
  
<a name="BKMK_QueryTheme"></a>

## <a name="query-the-current-theme"></a>Abfrage des aktuellen Designs
 Möglicherweise müssen Sie das aktuelle Design mithilfe des clientseitigen Codes abfragen, wenn Sie eine Lösung mit HTML-Webressourcen haben, die Sie für die Designauswahl für eine Organisation anpassen möchten. Sie können die folgende Abfrage mit dem Web-API verwenden, um diese Informationen abzurufen.  

 **Anforderung:** 

```http
GET [Organization URI]/api/data/v9.0/themes?$filter=isdefaulttheme eq true&$select=defaultentitycolor,defaultcustomentitycolor,controlborder,controlshade,selectedlinkeffect,globallinkcolor,processcontrolcolor,headercolor,logotooltip,hoverlinkeffect,navbarshelfcolor,navbarbackgroundcolor
```

 **Antwort:**

```json
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0

{  
    "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#themes(defaultentitycolor,defaultcustomentitycolor,controlborder,controlshade,selectedlinkeffect,globallinkcolor,processcontrolcolor,headercolor,logotooltip,hoverlinkeffect,navbarshelfcolor,navbarbackgroundcolor)",  
    "value": [  
        {  
            "defaultentitycolor": "#001CA5",  
            "defaultcustomentitycolor": "#006551",  
            "controlborder": "#CCCCCC",  
            "controlshade": "#F3F1F1",  
            "selectedlinkeffect": "#B1D6F0",  
            "globallinkcolor": "#1160B7",  
            "processcontrolcolor": "#D24726",  
            "headercolor": "#1160B7",  
            "logotooltip": "Model-driven apps",  
            "hoverlinkeffect": "#D7EBF9",  
            "navbarshelfcolor": "#DFE2E8",  
            "navbarbackgroundcolor": "#002050",  
            "themeid": "f499443d-2082-4938-8842-e7ee62de9a23"  
        }  
    ]  
}  
```

 Mehr Informationen: [Datenabfrage über die Web-API](../common-data-service/webapi/query-data-web-api.md).
  
<a name="BKMK_EditAndPublish"></a>

## <a name="edit-and-publish-theme-data"></a>Bearbeiten und Veröffentlichen von Sie Designdaten

 Ein Design wird erstellt, indem die Anpassungstools in der Benutzeroberfläche verwendet werden, ohne dass ein Entwickler hierfür Code schreiben muss. Informationen zur Anwendung dieser Anpassungen finden Sie in [Ändern des Farbschemas oder Hinzufügen eines Logos entsprechend der Marke Ihrer Organisation](/dynamics365/customer-engagement/customize/change-color-scheme-add-logo-match-organizations-brand).  

 Die meisten Designdaten werden innerhalb der Designentität gespeichert. Benutzerdefinierte Farben für bestimmte Entitäten sind in der <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.EntityColor> -Eigenschaft verfügbar. Diese Daten werden mit der Entität exportiert, wenn die Entität einer Lösung hinzugefügt wurde.

 Die folgende Tabelle beschreibt die `Theme`-Entitätsattribute, die zulässig sind für Updates und Daten enthalten, die vom Design angewendet wurden:  

|Schemaname|Typ|Der Wert des Standarddesigns|Beschreibung|  
|-----------------|----------|----------------------------|-----------------| 
|AccentColor|String|#E83D0F|Das sekundäre Farbdesign für die einheitliche Oberfläche auswählen, das in Prozesssteuerelementen verwendet wird.| 
|BackgroundColor|String|#FFFFFF|Nur zur internen Verwendung|
|ControlBorder|String|#BDC3C7|Die Farbe, die Steuerelemente für Ränder auswählen.|  
|ControlShade|String|#FFFFFF|Die Farbe für Steuerelemente, die angibt, dass auf ein Element gezeigt wird.|  
|DefaultCustomEntityColor|String|#00CCA3|Die Standardfarbe für benutzerdefinierte Entitäten, wenn keine Farbe zugewiesen ist.|  
|DefaultEntityColor|String|#666666|Die Standardfarbe für Systementitäten aus, wenn keine Farbe zugewiesen ist.|  
|GlobalLinkColor|String|#1160B7|Die Farbe für Links wie E-Mail-Adressen oder Suchbegriffe|  
|HeaderColor|String|#1160B7|Die Farbe für Überschriftentext (also beispielsweise für die Beschriftung von Formularregisterkarten).|  
|HoverLinkEffect|String|#E7EFF7|Die Farbe, die in Befehlen oder Listen verwendet wird, wenn Sie auf Elemente zeigen.|  
|ImportSequenceNumber|Integer|NULL|Sequenznummer des Imports, mit dem der Datensatz erstellt wurde.|
|IsDefaultTheme|Boolean|Wahr|Der Standardwert für ein benutzerdefiniertes Design ist ungültig.|
|LogoId|String|NULL|Der Name einer als Logo zu verwendende Webressource. Empfohlene Dimensionen sind eine Höhe von 50 Pixel und eine maximale Breite von 400 Pixel.|  
|LogoToolTip|String|Modellgestützte Apps|Der Text, der als QuickInfo und alternativer Text für das Logo verwendet wird.| 
|MainColor|String|#3B79B7|Das primäre Farbdesign für die einheitliche Oberfläche auswählen, das in der Hauptbefehlsleiste, auf Schaltflächen und Registerkarten verwendet wird.| 
|Name|String|Standard-MDA-Design|Der Name der Designentität.|  
|NavBarBackgroundColor|String|#002050|Die Primärfarbe für die Navigationsleiste.|  
|NavBarShelfColor|String|#DFE2E8|Die Sekundärfarbe für die Navigationsleiste.|  
|OverriddenCreatedOn|DateTime|NULL|Datum und Uhrzeit der Datensatzmigration|  
|PageHeaderBackgroundColor|String|#E0E0E0|Hintergrundfarbe für Kopfzeile auswählen.|  
|PageHeaderBackgroundColor|String|#F3F3F3|Hintergrundfarbe für Bereichskopfzeile auswählen.|  
|ProcessControlColor|String|#41A053|Die Primärfarbe für Prozesssteuerelemente.|  
|SelectedLinkEffect|String|#F8FAFC|Die Farbe, die in Befehlen oder Listen für ausgewählte Elemente verwendet wird.| 
|transactionCurrencyId|Suche|NULL|Wechselkurs für die Währung, die dem Design im Hinblick auf die Basiswährung zugeordnet ist.| 
 
 Nachdem Sie Änderungen übernommen haben, verwenden Sie die <xref href="Microsoft.Dynamics.CRM.PublishTheme?text=PublishTheme Action" /> oder <xref:Microsoft.Crm.Sdk.Messages.PublishThemeRequest>, um einen der Designdatensätze zum aktuellen Design zu machen.  

<a name="BKMK_ExportingAndImportingThemes"></a>

## <a name="exporting-and-importing-themes"></a>Exportieren und Importieren von Designs

 Da Designs nicht als Teil einer Lösung enthalten sind, können Sie, wenn Sie Designs von einer Organisation in die andere übertragen möchten, das Configuration Migration-Tool verwenden, um ein Schema zu generieren, Designdaten zu exportieren und sie in eine andere Organisation zu importieren. Weitere Informationen dazu, wie Sie das Tool verwenden, finden Sie unter [Konfigurationsdaten mithilfe des Configuration Migration tool verschieben](/dynamics365/customer-engagement/admin/manage-configuration-data).  

### <a name="see-also"></a>Siehe auch

 [Designentität](../common-data-service/reference/entities/theme.md) <br/>
 [Design erstellen](/dynamics365/customer-engagement/customize/change-color-scheme-add-logo-match-organizations-brand) <br/>
 [Entwicklerhandbuch zur Anpassung](/dynamics365/customer-engagement/developer/customize-dev/customize-applications)
