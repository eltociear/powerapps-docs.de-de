---
title: Testtools für clientseitige Entwicklung (Common Data Service for Apps) | Microsoft Docs
description: Informieren Sie sich über Testframeworks für clientseitige Entwicklung.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: aengusheaney
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="testing-tools-for-client-side-development"></a>Testtools für clientseitige Entwicklung

Microsoft stellt ein automatisiertes Testframework für die Benutzeroberfläche speziell für modellgesteuerte Apps namens [Easy Repro](https://github.com/Microsoft/EasyRepro) bereit. Dies Framework wird mithilfe des Open Source-Projekts zur Browser-Automatisierung [SeleniumHQ](https://www.seleniumhq.org/) erstellt.

Easy Repro stellt einen Satz von Klassen und Methoden bereit, um mit verschiedenen Seiten in modellgesteuerten Apps zu arbeiten, damit Sie die HTML-Elemente der Anwendung nicht analysieren müssen, wenn Sie Testfälle schreiben. Dadurch werden die Tests sicher gegen Änderungen in den HTML-Elementen, aus denen die Anwendungsseiten bestehen.

## <a name="benefits-of-unit-testing"></a>Vorteile des Komponententests

Komponententests werden dringend empfohlen, sind jedoch nicht erforderlich. Wenn Sie erst anfangen, oder wenn die Codemenge in Ihrer Lösung verhältnismäßig überschaubar ist, werden Sie möglicherweise feststellen, dass Sie mehr Zeit für das Schreiben von Tests benötigen, als für die Funktion in Ihrer Lösung.

Die Vorteile des Komponententests greifen, wenn Ihre Lösung größer und komplexer wird. Bei clientseitiger Entwicklung kann Ihnen ein automatisiertes Framework für die Benutzeroberfläche bei der Erkennung von Problemen helfen, die durch Benutzeraktionen hervorgerufen wurden.  

Wenn einer Lösung mit Komponententest entwickelt wird, melden Entwickler bessere Produktivität und Produktqualität.

### <a name="see-also"></a>Siehe auch

[Testtools für serverseitige Entwicklung](../common-data-service/testing-tools-server.md)<br />
[Video: Erstellen und Ausführen von Benutzeroberflächentest](https://youtu.be/ryWgK34Akt0)<br />
[Blogbeitrag: Easy Repro: Was ist das?](http://www.itaintboring.com/dynamics-crm/easy-repro-what-is-it/)<br />
[Video: Einführung in DevOps](https://youtu.be/AorM792M8nY)
