---
title: Durchsuchen der Metadaten für Ihre Organisation (Common Data Service) | Microsoft-Dokumentation
description: Sie können den Entitätsmetadaten-Browser verwenden, um Entitäten und ihre Eigenschaften in Common Data Service anzuzeigen. Der Entitätsmetadaten-Browser ist eine verwaltete Lösung, die Sie in Ihrer Organisation herunterladen und installieren können.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 50a7c59ac5655fdcf6928f626c5714a75fe3f57e
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753054"
---
# <a name="browse-the-metadata-for-your-environment"></a>Durchsuchen Sie Metadaten für die Organisation

Sie können den Entitätsmetadaten-Browser verwenden, um Entitäten und ihre Eigenschaften in Common Data Service anzuzeigen. Der Entitätsmetadatenbrowser ist eine verwaltete Lösung, die Sie mithilfe der Links unten herunterladen können.


|                                                                                               Version                                                                                                |                                                                                     Download                                                                                      |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Common Data Service | [Microsoft-Downloads: MetadataBrowser_3_0_0_5_managed.zip](https://download.microsoft.com/download/8/E/3/8E3279FE-7915-48FE-A68B-ACAFB86DA69C/MetadataBrowser_3_0_0_5_managed.zip) |

Nach dem Download der Lösung müssen Sie sie installieren. Weitere Informationen dazu, wie eine verwaltete Lösungen installiert wird, finden Sie unter [Importieren, aktualisieren und exportieren von Lösungen](/dynamics365/customer-engagement/developer/customize/import-update-export-solutions)  

## <a name="open-as-an-app"></a>Öffnet eine App
Common Data Service wird als App konfiguriert. Nachdem Sie die **Entitätsmetadaten-Browser**-Lösung installiert haben, suchen Sie die **Metadaten-Tools**-App und öffnen Sie sie. **Entitäten** ist die Standardansicht. Im Navigationsbereich **Tools** können Sie **Entitätsmetadaten** auswählen, um einzelne Entitäten zu überprüfen.

## <a name="open-from-the-solution-configuration-page"></a>Öffnen aus der Lösungskonfigurationsseite
Bei früheren Versionen müssen Sie die folgenden Schritte verwenden, diese funktionieren aber auch für die aktuelle Version.  

Nachdem Sie den **Entitätsmetadaten-Browser** installiert haben, öffnen Sie die verwaltete Lösung, indem sie in die Zeile in der Lösungsliste klicken, und zeigen Sie die Seite **Konfiguration** an, um Informationen zum Entitätsmetadaten-Browser und Schaltflächen zum Aufrufen von zwei unterschiedlichen Ansichten anzuzeigen.
- **Browser für Metadaten** ist der Ansicht **Entitäten** in der App äquivalent.
- **Entitätsmetadaten-Browser** ist der Ansicht **Entitätsmetadaten** in der App äquivalent.

## <a name="entities-view"></a>Entitätenansicht
Sie können die folgenden Aktionen ausführen:

- **Entitätsdetails anzeigen**: Wählen Sie eine Entität aus, um sie mithilfe der Ansicht **Entitätsmetadaten** anzuzeigen.
- **Entität bearbeiten**: Öffnen Sie das ausgewählte Entitätsbearbeitungsformular in der Standardorganisation, wenn die Entität dies unterstützt.
- **Textsuche**: Führen Sie eine Textsuche aus, um die angezeigten Entitäten mithilfe der folgenden Entitätseigenschaften zu filtern: <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.SchemaName>, <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.LogicalName>, <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.DisplayName>, <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.ObjectTypeCode> oder <xref:Microsoft.Xrm.Sdk.Metadata.MetadataBase.MetadataId>.
- **Entitäten filtern**: Festlegen von einfachen Kriterien, um eine Teilmenge der Entitäten anzuzeigen. Alle Kriterien werden ausgewertete unter Anwendung der UND-Logik.
- **Eigenschaften filtern**: Filtern Sie die angezeigten Eigenschaften für eine beliebige ausgewählte Entität. Es gibt nahezu 100 Eigenschaften in der Liste. Verwenden Sie dies, um diejenigen auswählen, an denen Sie interessiert sind.

## <a name="entity-metadata-view"></a>Entitätsmetadatenansicht

Die folgenden Aktionen können Sie für eine einzelne Entität ausführen:

- **Entität**: Ändern Sie die Entität, die Sie anzeigen möchten.
- **Eigenschaften**: Zeigen Sie alle Eigenschaften für die Entität an und filtern Sie die angezeigten Eigenschaften.

    - **Entität bearbeiten**: Öffnen Sie das ausgewählte Entitätsbearbeitungsformular in der Standardorganisation, wenn die Entität dies unterstützt.
    - **Eigenschaften filtern**: Filtern Sie die angezeigten Eigenschaften für eine beliebige ausgewählte Entität. Es gibt nahezu 100 Eigenschaften in der Liste. Verwenden Sie dies, um diejenigen auswählen, an denen Sie interessiert sind.

- **Attribute**: Zeigen Sie die Entitätsattribute in einer Master-/Detailansicht an. Mit dieser Ansicht können Sie Folgendes durchführen:

    - **Attribut bearbeiten**: Öffnen Sie das ausgewählte Attributsformular in der Standardorganisation, wenn das Attribut dies unterstützt.
    - **Textsuche**: Führen Sie eine Textsuche aus, um die angezeigten Attribute mithilfe der folgenden Attributseigenschaften zu filtern: <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.SchemaName>, <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.LogicalName>, <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.DisplayName> oder <xref:Microsoft.Xrm.Sdk.Metadata.MetadataBase.MetadataId>.
    - **Attribute filtern**: Filtern Sie Attribute nach beliebigen Attributeigenschaftswerten.
    - **Eigenschaften filtern**: Filtern Sie die angezeigten Eigenschaften für ein beliebiges ausgewähltes Attribut.

- **Schlüssel**: Wenn Alternativschlüssel für eine Entität aktiviert sind, können Sie deren Konfiguration untersuchen.

- **Beziehungen**: Zeigen Sie die drei Typen von Entitätsbeziehungen an: 1: N, n: 1 und n: n-Beziehungen. Mit diesen Ansichten können Sie Folgendes durchführen:  
    - **Beziehung bearbeiten**: Öffnen Sie das ausgewählte Beziehungsformular in der Standardorganisation, wenn die Beziehung dies unterstützt.  
    - **Textsuche**: Führen Sie eine Textsuche aus, um die angezeigten Beziehungen mithilfe von für den Beziehungstyp relevanten Werten zu filtern.  
    - **Eigenschaften filtern**: Filtern Sie die Beziehung nach einem beliebigen Beziehungseigenschaftswert.

- **Rechte**: Zeigen Sie Entitätsrechte an. Mit dieser Ansicht können Sie Folgendes durchführen:  
    - Filtern Sie die angezeigten Rechte mithilfe der `PrivilegeId`.

> [!NOTE]
> Wenn Sie die Entitätsdetaileigenschaften anzeigen, sehen Sie, dass viele komplexen Eigenschaften erweiterbar sind. Der nützlichste Wert wird mit einem Link angezeigt, der das Umschalten zu einer detaillierten Ansicht ermöglicht. Die detaillierte Ansicht zeigt die Struktur der Daten an, wenn diese programmgesteuert abgerufen werden. Die detaillierte Ansicht zeigt auch andere relevante Daten an, die in demselben Bereich abgerufen werden können, beispielsweise wenn lokalisierte Beschriftungen für **Anzeigename**-Eigenschaften vorhanden sind.

> [!TIP]
> Wenn Sie Text aus der Seite kopieren möchten, wählen Sie einfach den Text aus und verwenden Sie die Tastenkombination Strg+C oder den Kontextmenübefehl **Kopieren**.

## <a name="community-tools"></a>Community-Tools

**Metadaten-Browser** ist ein Tool, das die XrmToolbox-Community für Common Data Service entwickelt hat. Weitere Informationen finden Sie im Thema [Entwicklertools](developer-tools.md) für von der Community entwickelte Tools.

> [!NOTE]
> Die Communitytools sind kein Produkt von Common Data Service. Es wird kein Support für die Communitytools angeboten. Wenn Sie Fragen zu dem Tool haben, setzen Sie sich bitte mit dem Herausgeber in Verbindung. Weitere Informationen: [XrmToolBox](https://www.xrmtoolbox.com).

### <a name="see-also"></a>Siehe auch

 [Entwicklertools für Common Data Service](developer-tools.md)<br />
 [Anpassen von Entitätsmetadaten](customize-entity-metadata.md)<br />
 