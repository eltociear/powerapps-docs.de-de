---
title: Aktivieren und Verwenden anpassbarer Hilfe (modellgesteuerte Apps) | Microsoft-Dokumentation
description: ''
keywords: ''
ms.date: 10/22/2019
ms.service: powerapps
ms.topic: article
author: Mattp123
ms.author: matp
manager: kvivek
topic-status: Drafting
search.audienceType:
- customizer
search.app:
- PowerApps
ms.openlocfilehash: 3e6b593a30044c6a2c8cfc3e4867cb18156208f5
ms.sourcegitcommit: 7411b4cf9e30e71052fe932dfd3276e969854af4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2019
ms.locfileid: "2768417"
---
# <a name="enable-and-use-customizable-help"></a>Aktivieren und Verwenden anpassbarer Hilfe
Mit anpassbarer Hilfe können Sie eigene kontextbezogene Informationen für modellgesteuerte App-Benutzern bereitstellen, die Formulare ausfüllen. 

> [!NOTE]
> Statt ein eigenes Hilfe-System erstellen und verwalten zu müssen, stehen benutzerdefinierte Hilfebereiche und Aufgabenhilfen zur Verfügung, die Sie verwenden können, um Hilfe zu erstellen, die der Einheitliche Oberfläche-Anwendung eine benutzerdefinierte, im Produkt enthaltene Hilfeerfahrung bietet, die an Ihre Organisation angepasst ist. Weitere Informationen: [Erstellen Sie einen interaktiven Begleiter für Ihre App Einheitliche Oberfläche](../common-data-service/create-custom-help-pages.md)

Mit modellgesteuerten Apps können Sie die Standard-Hilfe durch eine benutzerdefinierte Hilfe eigener Wahl auf der globalen (Umgebungs-) Ebene oder Entitätsebene ersetzen. Benutzerdefinierte Hilfe macht den Inhalt, der durch die Hilfelinks verfügbar gemacht wird, für Ihre benutzerdefinierten oder anpassbaren Entitäten relevanter. Mit einer einzelnen, globalne URl können Sie die Standard-Hilfelinks für alle anpassbaren Entitäten überschreiben. Pro-Entität-URLs überschreiben die standardmäßigen Hilfelinks auf Rastern und Formularen für eine bestimmte anpassbare Entität. Sie können zusätzliche Parameter in die URL einschließen, z. b: Sprachcode UND Entitätsnamen. Diese Parameter ermöglichen es einem Entwickler, Funktionalität hinzufügen, um den Benutzer auf eine Seite umzuleiten, die für die Sprache oder den Entitätskontext in der Anwendung relevant ist. Die benutzerdefinierten Hilfeeinstellungen auf Entitätsebene sind lösungsspezifisch, daher können Sie sie im Rahmen einer Lösung verpacken und zwischen Umgebungen übertragen oder in Lösungen verteilen. 

## <a name="set-up-customizable-help"></a>Anpassbare Hilfe einrichten
Anpassbare Hilfe kann auf globalen und Entitätsebenen festgelegt werden. 

### <a name="set-customizable-help-at-the-global-level"></a>Festlegen anpassbarer Hilfe auf globaler Ebene
Personen mit der Systemadministrator-Sicherheitsrolle können die Einstellungen verwenden, um die Standardhilfe auf der globalen Ebene zu überschreiben. 
1. Öffnen Sie eine modellgesteuerte App und wählen Sie dann in der Befehlsleiste **Einstellungen** ![Einstellungen](../model-driven-apps/media/powerapps-gear.png) > **Erweiterte Einstellungen** aus.
2. Gehen Sie zu **Einstellungen** > **Verwaltung**.
3. Wählen Sie **Systemeinstellungen** und dann die Registerkarte **Allgemein** aus. 
4. Wählen Sie unter **URL für benutzerdefinierte Hilfe festlegen** die folgenden globalen Einstellungen für die anpassbaren Hilfe aus und definieren Sie sie: 
     - **Benutzerdefinierte Hilfe für anpassbare Entitäten verwenden**. Zur Aktivierung wählen Sie diese aus.  
     - **URL für globale benutzerdefinierte Hilfe**. Geben Sie die URL für die benutzerdefinierte Hilfe ein. 
     - **Parameter an URL anfügen**. Wählen Sie **Ja** aus, damit Parameter wie Sprachcode oder Entitätsname an die **Hilfe-URL** angefügt werden können, die Sie in der Entitätsdefinition angeben. Weitere Informationen: [Parameter an URL anfügen](#append-parameters-to-url)  

    > [!div class="mx-imgBorder"] 
    > ![Globale Einstellungen für die anpassbare Hilfe](media/customizable-help-global-setting.png)

5. Wählen Sie **OK** aus.

### <a name="set-customizable-help-for-a-specific-entity"></a>Festlegen anpassbarer Hilfe für eine bestimmte Entität
Wenn Sie benutzerdefinierte Hilfe auf globaler Ebene aktiviert haben, können Systemanpasser die globale Hilfe-URL für eine Entität in der Entitätsdefinition überschreiben. 

1. Öffnen Sie den Projektmappen-Explorer.
2. Erweitern Sie **Entitäten**, und wählen Sie dann die gewünschte Entität aus. 
3. Geben Sie auf der Registerkarte **Allgemein** unter dem Abschnitt **Hilfe** der Entitätsdefinition im Feld **Hilfe-URL** die URL Ihrer benutzerdefinierten Hilfeseite ein. 

    > [!div class="mx-imgBorder"] 
    > ![Entitätseinstellungen für die anpassbare Hilfe](media/customizable-help-entity-setting.png)

#### <a name="append-parameters-to-url"></a>Parameter an URL anfügen
Wie zuvor beschrieben, um das Anfügen von Parametern an die **Hilfe-URL** für die Entitätsdefinition zuzulassen, legen Sie **Parameter an URL anfügen** in den **Systemeinstellungen** > **Allgemein**-Registerkarte auf **Ja** fest. 

Beispiele der Parameter, die an die URL angefügt werden können:

- Benutzersprachcode: userlcid
- Name der Entität: Entität
- Einstiegspunkt: Hierarchiediagramm oder Formular
- Formular-ID: formid

