---
title: Eigenschaften von Formularen einer modellgesteuerten App in PowerApps | Microsoft-Dokumentation
description: Verstehen Sie die Eigenschaften des Hauptformulars
Keywords: Main form properties; Dynamics 365
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 06/27/2018
ms.service: crm-online
ms.topic: article
ms.assetid: 4ed30bb7-dca1-4de8-80f3-842152ea921a
ms.openlocfilehash: 4aec7fd8a117257d4f21ac2f692643785fd21791
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39685194"
---
# <a name="model-driven-app-form-properties"></a>Eigenschaften des Formulars für die modellgesteuerte App 

Sie können im Projektmappen-Explorer auf die **Formulareigenschaften** zugreifen. Erweitern Sie unter **Komponenten** die Option **Einheiten**, erweitern Sie die gewünschte Entität, und wählen Sie dann **Formulare**. Öffnen Sie in der Liste der Formulare den Formulartyp **Haupt**. Wählen Sie auf der Registerkarte **Start** die **Formulareigenschaften**.

![Formular-Eigenschaften](media/form-properties.png)

Die folgende Tabelle enthält die Formulareigenschaften:  
  
|Registerkarte|Eigenschaft|Beschreibung|  
|---------|--------------|-----------------|  
|**Ereignisse**|**Formularbibliotheken**|Verwalten Sie, welche JavaScript-Webressourcen im Formular verfügbar sind, und in welcher Reihenfolge sie geladen werden.|  
||**Ereignishandler**|Konfigurieren Sie, welche JavaScript-Funktionen aus den Formularbibliotheken für die Formularereignisse `OnLoad` und `OnSave` ausgeführt werden, und in welcher Reihenfolge sie ausgeführt werden.|  
|**Anzeige**|**Formularname**|Geben Sie einen Namen ein, die für Benutzer aussagekräftig ist. Dieser Name wird den Benutzern bei der Verwendung des Formulars angezeigt. Wenn sie mehrere für die Entität konfigurierte Formulare verwenden können, können sie verfügbaren Formulare anhand dieses Namens unterscheiden.|  
||**Beschreibung**|Geben Sie eine Beschreibung ein, die erklärt, wie sich dieses Formular von anderen Hauptformularen unterscheidet. Diese Beschreibung wird nur in der Liste der Formulare für eine Entität im Projektmappen-Explorer angezeigt.|  
||**Formularassistent**|Wählen Sie über das Kontrollkästchen, ob Sie den Formularassistenten aktivieren oder das Formular standardmäßig erweitert anzeigen möchten.|
||**Seitennavigation**|Sie können auswählen, dass die nicht Navigationselemente nicht angezeigt werden sollen.<br /><br /> In Formularen für aktualisierte Objekte bedeutet dies, dass der primäre Namenswert für den aktuell angezeigten Datensatz nicht in der Navigationsleiste angezeigt wird, um die Navigation zu den zugehörigen Ansichten zu ermöglichen.<br /><br /> In Formularen, die die klassische Darstellung verwenden, werden die Navigationsmöglichkeiten zur Auswahl der zugehörigen Ansichten auf der linken Seite des Formulars nicht angezeigt.|  
||**Image**|Wenn eine Entität ein Imagefeld hat und die Option **Primäres Image** der Entitäten festgelegt ist, ermöglicht diese Einstellung die Anzeige des Imagefeldes im Kopf dieses Formulars.<br /><br /> Weitere Informationen zu den Entitätsoptionen finden Sie unter [Aktivieren oder deaktivieren von Entitätsoptionen](../common-data-service/edit-entities.md#enable-or-disable-entity-options).|  ||**Anzeige**|**Legen Sie eine maximale Breite (in Pixeln)** fest, um die Breite des Formulars zu begrenzen. Der Standardwert ist 1.900.|  
||**Anzeige**|Geben Sie hier in Pixel die maximale Breite ein, die Sie für das Formular verwenden möchten.|
|**Parameter**|**Parameter**|Jedes Formular kann mit Code über eine URL geöffnet werden. Die URL kann auch Daten enthalten, die über eine Abfragezeichenfolge, die an die URL angehängt wird, an das Formular übergeben werden können. Die Abfragezeichenfolge sieht wie in diesem Beispiel aus:<br />`?p_firstName=Jim&p_lastName=Daly`<br /><br /> Aus Sicherheitsgründen akzeptieren Formulare keine unbekannten Parameter für Abfragezeichenfolgen. Verwenden Sie diese Parameterliste, um Parameter anzugeben, die dieses Formular akzeptieren soll, um Code zu unterstützen, der Daten an die Formulare über eine Abfragezeichenfolge übergibt.<br /><br /> Der Name und Typ der Daten werden überprüft und das Formular wird nicht geöffnet, wenn ungültige Parameter für die Abfragezeichenfolge an das Formular übergeben werden.<br /><br />**Hinweis:** Der Name darf nicht mit einem Unterstrich (_) oder Crm beginnen\_. Er muss mit einem alphanumerischen Zeichen gefolgt von einem Unterstrich beginnen (\_). Beispielsweise parameter_1 oder 1_parameter. Der Name darf keine Bindestriche (-), Doppelpunkte (:), Semikolons (;), Kommas (,) oder Punkte (.) enthalten. <br /><br />|  
|**Nicht-Ereignis-Abhängigkeiten**|**Abhängige Felder**|Jeder Ereignishandler hat eine ähnliche Eigenschaft **Abhängige Felder**, sodass alle Felder, die vom Skript benötigt werden, registriert werden können. Jeder, der versucht, die abhängigen Felder zu entfernen, wird dies nicht können.<br /><br /> Einige Skripte werden auf dem Formular ausgeführt, sind aber nicht in einem Ereignishandler konfiguriert. Skripte, die von der Befehlsleiste aus gestartet werden, haben keine Stelle, an der abhängige Felder registriert werden können. Diese Formulareigenschaft bietet einen Platz für abhängige Felder für die zu registrierenden Skripte.|  

## <a name="next-steps"></a>Nächste Schritte

[Verwenden des Hauptformulars und seiner Komponenten](use-main-form-and-components.md)