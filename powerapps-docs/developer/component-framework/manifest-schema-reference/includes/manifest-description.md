---
title: Manifest | Microsoft-Dokumentation
description: ''
keywords: ''
ms.author: nabuthuk
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
ms.assetid: 31af2963-b4ca-4347-98f6-4a3f6277f43a
ms.openlocfilehash: 22750956cea12e1ed17bbc1ee8d4f015cf0ce2c1
ms.sourcegitcommit: 63ea15e2f861d43333aacda19230cd8922d7bdfd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2019
ms.locfileid: "72338917"
---
Ein Manifest ist die Metadatendatei, die eine Komponente definiert. Es handelt sich um eine `XML` Datei, die Folgendes beschreibt:

- Der Namespace der Komponente.
- Die Art der Daten, die konfiguriert werden können, entweder ein Feld oder ein Datenset.
- Alle Eigenschaften, die in der Anwendung konfiguriert werden können, wenn die Komponente hinzugefügt wird.
- Eine Liste von Ressourcen Dateien, die von der Komponente benötigt werden. 
  - Eine davon muss eine JavaScript-Webressource sein. Diese JavaScript-Ressource muss eine Funktion zum Instanziieren eines Objekts enthalten. Dadurch wird eine Schnittstelle implementiert, die die für die Komponente erforderlichen Methoden verfügbar macht. Diese wird als „Komponentenimplementierungsbibliothek“ bezeichnet.
- Der Name einer JavaScript-Funktion in der Komponenten Implementierungs Bibliothek, die ein Objekt zurückgibt, das die erforderliche Komponentenschnittstelle anwendet.

Wenn der Benutzer eine benutzerdefinierte Komponente in einer Canvas-APP oder einer Modell gesteuerten App konfiguriert, werden die verfügbaren Komponenten von den Daten im Manifest herausgefiltert, sodass nur die gültigen Komponenten für den Kontext für die Konfiguration verfügbar sind. Die Eigenschaften, die im Manifest für eine Komponente definiert sind, werden als Konfigurations Felder gerendert, sodass der Benutzer, der die Komponente konfiguriert, Werte angeben kann. Diese Eigenschaftswerte sind dann zur Laufzeit für die Komponenten Funktion verfügbar.
