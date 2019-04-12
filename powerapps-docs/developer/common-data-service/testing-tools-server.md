---
title: Testtools für serverseitige Entwicklung (Common Data Service) | Microsoft Docs
description: Informieren Sie sich über Testframeworks für serverseitige Entwicklung.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="testing-tools-for-server-side-development"></a>Testtools für serverseitige Entwicklung

Viele Entwickler plädieren nachdrücklich im Rahmen ihrer Entwicklungsprozesses einen Komponententest durchzuführen. Andere sind nicht sicher. Common Data Service stellt keine Tools für Testframeworks bereit, aber Sie sollten beachten, dass Communitytools erhältlich sind, die Sie verwenden können. Ein beliebtes Framework für serverseitige Entwicklung ist [Fake Xrm Easy](https://dynamicsvalue.com/home). Dieses Framework kann mit den .NET-Framework Testframeworks Ihrer Wahl kombiniert werden. [FakeItEasy](https://fakeiteasy.github.io/) ist eine häufige Wahl.

> [!NOTE]
> Microsoft bietet keinen Support für die Tools von der Community. Bei Problemen mit einem Community-Tool werden können Sie sich an den Herausgeber wenden.

## <a name="benefits-of-unit-testing"></a>Vorteile des Komponententests

Komponententests werden dringend empfohlen, sind jedoch nicht erforderlich. Wenn Sie erst anfangen, oder wenn die Codemenge in Ihrer Lösung verhältnismäßig überschaubar ist, werden Sie möglicherweise feststellen, dass Sie mehr Zeit für das Schreiben von Tests benötigen, als für die Funktion in Ihrer Lösung.

Die Vorteile des Komponententests greifen, wenn Ihre Lösung größer und komplexer wird. Besonders bei serverseitiger Entwicklung kann das lokale Debuggen mit Mock- oder Fake-Daten in einem Testframework vorteilhaft sein, da nicht alle Schritte durchlaufen werden müssen, die in [Debugging von Plug-Ins](debug-plug-in.md) beschrieben werden, um ein Profil zum Debuggen zu erstellen.

Wenn einer Lösung mit Komponententest entwickelt wird, melden Entwickler bessere Produktivität und Produktqualität.

### <a name="see-also"></a>Siehe auch

[Testtools für clientseitige Entwicklung](../model-driven-apps/testing-tools-client.md)<br />
[Video: Einführung in DevOps mit Dynamics 365](https://youtu.be/AorM792M8nY)