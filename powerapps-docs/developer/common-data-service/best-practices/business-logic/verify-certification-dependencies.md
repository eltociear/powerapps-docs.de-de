---
title: Überprüfen der Zertifizierungsabhängigkeiten für Plug-ins, die ausgehende Aufrufe tätigen | Microsoft Docs
description: Stellen Sie sicher, dass alle Zertifikate, von denen Ihr Code für ausgehende Anrufe abhängt, über eine gültige Kette von Zertifikaten verfügen.
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: ryjones
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 01/08/2020
ms.author: jdaly
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ee8dd188c1b88aea4aedb8330e4a0251216b0bb5
ms.sourcegitcommit: 5e23beed96cc14efae9ff264405956d59fae1e7c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2020
ms.locfileid: "2945031"
---
# <a name="verify-certification-dependencies-for-plug-ins-making-outbound-calls"></a>Verifizieren Sie die Zertifizierungsabhängigkeiten für Plug-ins, die ausgehende Aufrufe tätigen

**Kategorie**: Wartbarkeit, Supportfähigkeit

**Wirkungspotential**: Hoch

<a name='symptoms'></a>

## <a name="symptoms"></a>Symptome

Dieser Fehler kann auftreten, wenn Ihr Plug-In einen https-Aufruf an eine externe Ressource macht:

`WebException: The underlying connection was closed: Could not establish trust relationship for the SSL/TLS secure channel.`


<a name='guidance'></a>

## <a name="guidance"></a>Anleitung

Sie sollten überprüfen, ob die Site, mit der Sie sich verbinden möchten, über eine gültige Kette von Zertifikaten verfügt. Verwenden Sie eines der Online-Test-Tools wie [Qualys SSL Labs SSL Server Test](https://www.ssllabs.com/ssltest/analyze.html), um zu überprüfen, ob die Site eine gültige Zertifikatskette bietet.


<a name='additional'></a>

## <a name="additional-information"></a>Weitere Informationen

Dies kann passieren, wenn Sie zum ersten Mal eine Verbindung zu einem neuen Endpunkt herstellen oder wenn sich etwas am Zertifikat geändert hat.

Wenn der in der Sandbox laufende Code in Ihrem Plug-in versucht, eine Verbindung zu einem externen Endpunkt über https herzustellen, startet die CDS-Sandbox die SSL/TLS-Verhandlung. Der Endpunkt präsentiert ein Zertifikat, das zur Verschlüsselung verwendet werden kann. Wenn das Zertifikat über ein oder mehrere Zwischenzertifikate verfügt, muss es die gesamte Kette darstellen, um die SSL/TLS-Verhandlung erfolgreich abzuschließen. Wenn nicht die gesamte Kette präsentiert wird, kann keine SSL/TLS-Kommunikation aufgebaut werden. 




<a name='seealso'></a>

### <a name="see-also"></a>Siehe auch

[Schreiben eines Plug-Ins](../../write-plug-in.md) <br /> 
[KeepAlive auf falsch setzen, wenn Sie mit externen Hosts in einem Plug-in interagieren](set-keepalive-false-interacting-external-hosts-plugin.md)<br /> 
[Timeout einstellen bei externen Anrufen in einem Plug-in](set-timeout-for-external-calls-from-plug-ins.md)