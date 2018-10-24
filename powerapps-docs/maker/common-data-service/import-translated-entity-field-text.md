---
title: Importieren von übersetztem Entitäts- und Feldtext mit PowerApps | Microsoft-Dokumentation
description: Erfahren Sie, wie übersetzten Entitäts- und Feldtext importieren.
ms.custom: ''
ms.date: 06/19/2018
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
ms.assetid: 3d77d149-819b-45e6-8e70-1fbe54d5c153
caps.latest.revision: 19
ms.author: matp
manager: kvivek
ms.openlocfilehash: e2417f7ad75e327fdfc54d4cd4fdd3f62395326b
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39689642"
---
# <a name="import-translated-entity-and-field-text-back-into-an-app"></a>Importieren von übersetztem Entitäts- und Feldtext in eine App

Wenn Sie einen Entitäts- oder Feldtext wie Feldbezeichnungen oder Dropdown-Listenwerte angepasst haben, können Sie Benutzern in Ihrer Organisation, die nicht mit der Basissprachversion Ihrer Umgebung arbeiten, diesen angepassten Text in ihrer Sprache bereitstellen. Exportieren Sie dazu die Textzeichenfolgen für alle Anpassungen, damit sie in die Sprachen übersetzt werden können, die Sie in Ihrer Organisation verwenden.  
  
 Nach der Übersetzung müssen Sie die übersetzten Texte in Ihre Umgebung importieren, bevor Benutzer die Änderungen nutzen können.  
  
> [!IMPORTANT]
> - Die Datei, die Sie importieren, muss eine komprimierte Datei sein, die die Dateien „CrmTranslations.xml“ und „[Content_Types].xml“ im Stammverzeichnis enthält.  
> - Sie können nur übersetzte Texte importieren, der weniger als 500 Zeichen enthalten. Wenn mindestens ein Element in Ihrer Übersetzungsdatei über 500 Zeichen verfügt, schlägt der Importvorgang fehl. Wenn der Importvorgang fehlschlägt, überprüfen Sie in der Datei die Zeile, die den Fehler verursacht hat, reduzieren Sie die Anzahl von Zeichen, und starten Sie den Importvorgang erneut. Beachten Sie außerdem, dass Sie nach dem Import von übersetztem Text Anpassungen erneut veröffentlichen müssen.  
  
1. Öffnen Sie den [Projektmappen-Explorer](../model-driven-apps/advanced-navigation.md#solution-explorer).  
  
2. Wählen Sie im Projektmappen-Explorer in der Aktionssymbolleiste **Übersetzungen importieren** aus.  
3.  Geben Sie im Dialogfeld **Übersetzten Text importieren** die Datei an, die den übersetzten Text enthält, und wählen Sie dann **Importieren** aus.  
  
4.  Wenn der Importvorgang abgeschlossen ist, wählen Sie **Schließen** aus.  
  
> [!NOTE]
>  Die Veröffentlichung von Anpassungen kann den normalen Systembetrieb beeinträchtigen. Es wird empfohlen, die Veröffentlichung zu einem Zeitpunkt zu planen, an dem sie die Benutzer am wenigsten stört.  

## <a name="community-tools"></a>Communitytools

[Easy Translator](https://www.xrmtoolbox.com/plugins/MsCrmTools.Translator/) ist ein Tool, das die XrmToolBox-Community für Dynamics 365 Customer Engagement entwickelt hat. Verwenden Sie Easy Translator zum Exportieren und Importieren von Übersetzungen mit Kontextinformationen. 

> [!NOTE]
> Die Communitytools werden von Microsoft nicht unterstützt. Wenn Sie Fragen zum Tool haben, wenden Sie sich bitte an den Herausgeber. Weitere Informationen finden Sie unter [XrmToolBox](https://www.xrmtoolbox.com).

## <a name="next-steps"></a>Nächste Schritte  
 [Exportieren von benutzerdefiniertem Entitäts- und Feldtext zur Übersetzung](export-customized-entity-field-text-translation.md)
