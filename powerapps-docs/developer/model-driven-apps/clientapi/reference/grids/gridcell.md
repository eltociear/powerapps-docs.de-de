---
title: Rasterzelle (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 8139c622-e4d9-478f-9510-414d140e5556
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="gridcell-client-api-reference"></a>GridCell (Client-API-Referenz)



GridCell wird nur für bearbeitbare Raster unterstützt.

GridCell einer ausgewählten Rasterzeile ist ein vergleichbares Steuerelement in einem Formular, das mit einem Attribut in einem bearbeitbaren Raster zusammenhängt. Soehe [Sammlungen (Client-API-Referenz)](../collections.md) für Informationen zu Methoden zum Zugreifen auf Daten in einer Sammlung.

## <a name="methods"></a>Methoden

GridCell unterstützt die folgenden Methoden.

|Name |Beschreibung |
|--|--|
|[clearNotification](../controls/clearNotification.md)| Löscht Benachrichtigungen für eine Zelle.|
|[getDisabled](../controls/getDisabled.md)| Gibt zurück, ob die Zelle deaktiviert ist (schreibgeschützt).|
|[setDisabled](../controls/setDisabled.md)| Legt fest, ob die Zelle deaktiviert ist.<br/><br/>**HINWEIS**: Durch die Aktivierung einer schreibgeschützten Zelle zum Bearbeiten kann ein Fehler verursacht werden, wenn der Datensatz gespeichert wird. Wenn das Feld vom Server als schreibgeschützt betrachtet wird, kann unter Umständen ein Fehler angezeigt werden, wenn der Wert geändert wird. Dies tritt möglicherweise in den Szenarien auf, für die der Benutzer keine Schreibrechte für den Datensatz besitzt, der Datensatz deaktiviert ist, oder der Benutzer nicht über die erforderlichen Feldebenen-Sicherheitsrechte verfügt.| 
|[setNotification](../controls/setNotification.md)|Zeigt eine Fehlermeldung für eine Zelle an, um anzugeben, dass Daten ungültig sind.|
|[getLabel](../controls/getLabel.md)|Gibt die Beschriftung der Spalte zurück, die die Zelle enthält.|


### <a name="related-topics"></a>Verwandte Themen

[Raster und Unterraster in modellgestützten Apps](../grids.md)

[Steuerelemente](../controls.md)


