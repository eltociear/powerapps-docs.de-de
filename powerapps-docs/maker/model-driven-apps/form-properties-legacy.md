---
title: Formulareigenschaften in modellgesteuerten Apps in PowerApps | Microsoft-Dokumentation
description: Grundlegendes zu Hauptformulareigenschaften
Keywords: Hauptformulareigenschaften; Dynamics 365
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 06/27/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 4ed30bb7-dca1-4de8-80f3-842152ea921a
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3a71fe6cf7771a0e15be85e0696e27226e84467e
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2700297"
---
# <a name="model-driven-app-form-properties"></a>Formulareigenschaften in modellgesteuerten Apps. 

Sie können auf **Formulareigenschaften** im Projektmappen-Explorer zugreifen. Erweitern Sie unter **Komponenten** **Entitäten**, und dann die gewünschte Entität, und wählen Sie **Formulare** aus. Öffnen Sie in der Liste der Formulare das Formular des Typs **Haupt**. Klicken Sie dann auf der Registerkarte **Start** auf **Formular-Eigenschaften**.

![Formulareigenschaften](media/form-properties.png)

Die folgende Tabelle führt die Formulareigenschaften auf:  
  
|Registerkarte|Eigenschaft|Beschreibung|  
|---------|--------------|-----------------|  
|**Ereignisse**|**Formularbibliotheken**|Verwalten, welche JavaScript-Webressourcen im Formular verfügbar sind, und in welcher Reihenfolge sie geladen werden.|  
||**Ereignishandler**.|Konfiguration, welche JavaScript-Funktionen aus den Formularbibliotheken für die `OnLoad`- und `OnSave`-Formularereignisse ausgeführt werden, sowie die Reihenfolge, in der sie ausgeführt werden.|  
|**Anzeige**|**Formularname**|Geben Sie einen Namen ein, der für Benutzer sinnvoll ist. Dieser Name wird bei Auswahl des Formulars angezeigt. Wenn mehrere für die Entität konfigurierte Formulare verwendet werden können, wird dieser Name verwendet, um verschiedene Formulare voneinander zu unterscheiden.|  
||**Beschreibung**|Geben Sie eine Beschreibung ein, die erläutert, wodurch sich dieses Formular von anderen Hauptformularen unterscheidet. Diese Beschreibung wird nur in der Liste der Formulare für eine Entität im Lösungs-Explorer angezeigt.|  
||**Formular-Assistent**|Aktivieren Sie die Kontrollkästchen, wenn Sie den Formular-Assistenten aktivieren oder das Formular angezeigt werden soll, das standardmäßig erweitert wird.|
||**Seitennavigation**|Sie können auswählen, dass Navigationselemente nicht angezeigt werden.<br /><br /> In Formularen für aktualisierte Entitäten bedeutet dies, dass der primäre Namenwert für den derzeit angezeigten Datensatz nicht in der Navigationsleiste zur Navigation zu verknüpften Ansichten angezeigt wird.<br /><br /> In Formularen mit der klassischen Präsentation werden die Navigationsoptionen zur Auswahl verknüpfter Ansichten auf der linken Seite des Formulars nicht angezeigt.|  
||**Bild**|Wenn eine Entität ein Bildfeld hat und die Option **Primäres Image** festgelegt ist, ermöglicht diese Einstellung die Anzeige des Bildfelds in der Kopfzeile dieses Formulars.<br /><br /> Siehe [Aktivieren oder Deaktivieren von Entitätsoptionen](../common-data-service/edit-entities.md#enable-or-disable-entity-options) für weitere Informationen zu Entitätsoptionen.|  ||**Anzeige**|**Legen Sie eine Maximale Breite (Pixel) fest**, um die Breite des Formulars zu beschränken. Der Standardwert ist 1900.|  
||**Anzeige**|Geben Sie in Pixeln die maximale Breite ein, die Sie für das Formular hier möchten.|
|**Parameter**|**Parameter**|Jedes Formular kann mit Code mithilfe einer URL geöffnet werden. Die URL enthält auch Daten, die an das Formular mithilfe einer Abfragezeichenfolge übergeben werden können, die an die URL angefügt ist. Abfragezeichenfolgen sehen wie folgt aus:<br />`?p_firstName=Jim&p_lastName=Daly`<br /><br /> Als Sicherheitsmaßnahme nehmen Formulare keine unbekannten Abfragezeichenfolgenparameter an. Verwenden Sie diese Parameterliste, um Parameter anzugeben, die dieses Formular akzeptieren sollte, um Code zu unterstützen, der mithilfe von Abfragezeichenfolgen Daten an die Formulare übergibt.<br /><br /> Name und Typ der Daten werden überprüft, und das Formular wird nicht geöffnet, wenn an es ungültige Abfragezeichenfolgenparameter übergeben werden.<br /><br />**Hinweis:** Der Name kann nicht mit einem Unterstrich (_) oder crm\_ beginnen. Er muss mit alphanumerischen Zeichen beginnen, die von einem Unterstrich (\_) gefolgt werden. Beispielsweise parameter_1 oder 1_parameter. Der Name kann keine Bindestriche (-), Doppelpunkte (:), Strichpunkte (;), Kommas (,) oder Punkte (.) enthalten. <br /><br />|  
|**Nicht ereignisgebundene Abhängigkeiten**|**Abhängige Felder**|Jeder Ereignishandler hat eine ähnliche Eigenschaft **Abhängige Felder**, so dass alle Felder, die für das Skript erforderlich sind, registriert werden können. Die abhängigen Felder können nicht entfernt werden.<br /><br /> Einige Skripts operieren auf dem Formular, sind jedoch nicht in einem Ereignishandler konfiguriert. Skripts, die von der Befehlsleiste initiiert wurden, haben keinen Ort, an dem abhängige Felder registriert werden können. Diese Formulareigenschaft stellt einen Ort für abhängige Felder zur Verfügung, sodass diese Skripts registriert werden können.|  

## <a name="next-steps"></a>Nächste Schritte

[Verwenden des Hauptformulars und seiner Komponenten](use-main-form-and-components.md)
