---
title: Erkennen von doppelten Daten mithilfe von Code (Common Data Service) | Microsoft-Dokumenten
description: Mit der Duplikaterkennung können Organisationen Duplikaterkennungsrichtlinien festlegen und Duplikaterkennungsegeln für Geschäfts- sowie benutzerdefinierte Entitäten erstellen
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e2a1b6d37f458cbd2f2b78818184e00f1bdd784a
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156250"
---
# <a name="detect-duplicate-data-using-code"></a>Erkennen von doppelten Daten mit Code

Mit der Duplikaterkennung können Organisationen Duplikaterkennungsrichtlinien festlegen und Duplikaterkennungsegeln für Geschäfts- sowie benutzerdefinierte Entitäten erstellen. Diese Regeln können auf verschiedene Datensatztypen in Common Data Service angewendet werden. Beispielsweise kann eine Organisation definieren, dass ein Lead ein Duplikat eines Kontakts ist, falls sie denselben Namen und dieselbe Telefonnummer haben. Anhand der Duplikaterkennungsregeln, die vom Administrator festgelegt werden, alarmiert das System den Benutzer über potenzielle Duplikate, wenn der Benutzer versucht, neue Datensätze zu erstellen oder vorhandene Datensätze zu aktualisieren. Zur Wahrung der Datenqualität, können Sie jederzeit einen Duplikaterkennungsauftrag planen, um nach Duplikaten für alle Datensätze zu prüfen, die bestimmten Kriterien entsprechen. Sie können die Daten bereinigen, indem Sie Duplikate, die von einem Duplikaterkennungsauftrag berichtet werden, löschen, deaktivieren oder zusammenführen.

> [!NOTE]
> Informationen dazu, wie Ausführungssystemaufträge für Regeln und das Erkennen von doppelten Daten mithilfe der Benutzeroberfläche (UI) erstellt werden [Erkennen von doppelten Daten, sodass Sie diese beheben oder entfernen](/dynamics365/customer-engagement/admin/detect-duplicate-data).

Sie können den Web-API- oder Organisationsservice verwenden, um doppelte Daten zu erkennen. Die Themen in diesem Abschnitt enthalten Informationen darüber, wie Sie doppelte Daten über beide Webservices erkennen können. 

### <a name="see-also"></a>Siehe auch

[Aktivieren und Deaktivieren der Duplikaterkennung](enable-disable-duplicate-detection.md)<br/>
[Duplikaterkennung ausführen](run-duplicate-detection.md)<br/>
[Duplikaterkennungsmeldungen](duplicate-detection-messages.md)<br/>
[Duplikatregelentitäten](duplicaterule-entities.md)

