---
title: Sicherheitsmodell (Common Data Service for Apps) | Microsoft Docs
description: 'PowerApps bietet ein Sicherheitsmodell, mit dem die Datenintegrität geschützt und die Geheimhaltung von Daten gewährleistet wird. Außerdem wird damit ein effizienter Datenzugriff und eine effiziente Zusammenarbeit unterstützt.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: paulliew
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="security-model"></a>Sicherheitsmodell

PowerApps bietet ein Sicherheitsmodell, mit dem die Datenintegrität geschützt und die Geheimhaltung von Daten gewährleistet wird. Außerdem wird damit ein effizienter Datenzugriff und eine effiziente Zusammenarbeit unterstützt. Die Ziele des Modells sind:
- Ermöglichung von Benutzerzugriff ausschließlich auf die Informationsebenen, die Benutzer zum Ausführen ihrer Aufgaben benötigen
- Kategorisierung von Benutzern nach Rolle und Beschränkung des Zugriffs basierend auf diesen Rollen
- Unterstützung der Datenfreigabe, sodass Benutzern und Teams der Zugriff auf Datensätze, die sie nicht besitzen, für eine bestimmte Zusammenarbeitsfunktion gewährt werden kann
- Vermeidung des Benutzerzugriffs auf Datensätze, die der Benutzer nicht besitzt oder freigibt

**Rollenbasierte Sicherheit** gruppiert einen Satz von Berechtigungen zusammen, der die Zuständigkeiten (oder Aufgaben, die ausgeführt werden können) für einen Benutzer definiert. PowerApps enthält einen Satz vorab definierter Sicherheitsrollen. Jede aggregiert einen Satz von Benutzerrechten, um die Verwaltung der Benutzersicherheit zu vereinfachen. Jede Anwendungsbereitstellung kann auch eigene Rollen definieren, um den Anforderungen der verschiedenen Benutzer gerecht zu werden. Sicherheitsrollen sind einer [Unternehmenseinheit](businessunit-entity.md) zugeordnet.

**Datensatzbasierte Sicherheit** konzentriert sich auf die Zugriffsrechte für bestimmte Datensätze.

**Feldbasierte Sicherheit** schränkt den Zugriff auf bestimmte Felder mit hoher Auswirkung auf das Unternehmen in einer Entität nur auf bestimmte Benutzer oder Teams ein.
Kombinieren Sie rollenbasierte Sicherheit, datensatzbasierte Sicherheit und feldbasierte Sicherheit, um die Gesamtsicherheitsrechte zu definieren, über die Benutzer in der benutzerdefinierten Dynamics 365-Anwendung verfügen.

Als Entwickler sollten Sie wissen, dass Ihre Abfragen in dem Kontext eines Benutzers ausgeführt werden und nur die Datensätze zurückgeben, für die der Benutzer über Leseberechtigungen verfügt.
Außerdem können Sie nur Vorgänge basierend auf Berechtigungen ausführen, die Ihrem Konto über die Sicherheitsrollen zugewiesen sind.

Ausführliche Informationen zu Sicherheitskonzepten finden Sie unter [Sicherheitskonzepte](/dynamics365/customer-engagement/admin/security-concepts)

### <a name="see-also"></a>Siehe auch

[BusinessUnit-Entität](businessunit-entity.md)