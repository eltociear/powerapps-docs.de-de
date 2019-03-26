---
title: Filterattribute mit Plugin-Registrierung einbinden | MicrosoftDocs
description: 'Wenn für einen Registrierungsschritt des Plugins keine Filterattribute festgelegt sind, wird das Plug-in jedes Mal ausgeführt, wenn eine Update-Meldung für dieses Ereignis auftritt.'
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 1/15/2019
ms.author: jowells
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="include-filtering-attributes-with-plug-in-registration"></a>Einbeziehen von Filterattributen mit Plugin-Registrierung

**Kategorie**: Leistung

**Wirkungspotential**: Mittel

<a name='symptoms'></a>

## <a name="symptoms"></a>Symptome

Wenn für einen Registrierungsschritt des Plugins keine Filterattribute festgelegt sind, wird das Plug-in jedes Mal ausgeführt, wenn eine Update-Meldung für dieses Ereignis auftritt.  Eine Kombination aus fehlenden Filterattributen und automatischer Speicherfunktionalität kann zu unnötigen Plugin-Ausführungen führen, die unerwünschtes Verhalten verursachen und die Leistung beeinträchtigen.

<a name='guidance'></a>

## <a name="guidance"></a>Anleitung

Die meisten Plugins, die für die Update-Meldung einer Entität registriert sind, müssen nicht bei allen Updates ausgeführt werden. Normalerweise ist es nur dann notwendig, eine bestimmte Logik zu verarbeiten, wenn sich ein bestimmtes Attribut oder bestimmte Attribute geändert haben. Um zusätzliche Verarbeitungen in der Umgebung zu vermeiden, die Logik, die in einem Plug-in benötigt wird, zu minimieren und die Aktualisierung so schnell wie möglich abzuschließen, wird dringend empfohlen, dass die Registrierung von Plug-in-Schritten auch Filterattribute für Update-Meldungen beinhaltet.

![Plug-in-Registrierungsschritt mit Filterattributen](../media/plugin-registration-step-with-filtering-attributes.png)

<a name='additional'></a>

## <a name="additional-information"></a>Weitere Informationen

Filterattribute sind eine Liste von Entity-Attributen, die bei einer Änderung die Ausführung des Plugins bewirken.  Diese Attribute können bei der Registrierung des Plugins mit dem Plug-in-Registrierungstool festgelegt werden. Wenn keine Attribute gesetzt sind, wird das Plug-in jedes Mal ausgeführt, wenn eine Update-Meldung erscheint. Aktualisierungen können aus verschiedenen Gründen erfolgen. Wenn die automatische Speicherung in der Umgebung aktiviert ist, kann sie mehrmals während der Sitzung des Benutzers in einem Entitätsformular erfolgen. Wenn keine Filterattribute angegeben sind, wird das Plug-in bei jeder Attributänderung an der entworfenen Entität ausgeführt.

<a name='seealso'></a>

### <a name="see-also"></a>Siehe auch

[Registrieren Sie ein Plug-in](../../register-plug-in.md)
[Deaktivieren Sie die automatische Speicherung in einer modellgesteuerten Anwendung.](/powerapps/maker/model-driven-apps/manage-auto-save)