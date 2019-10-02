---
title: Manifest | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
ms.assetid: 31af2963-b4ca-4347-98f6-4a3f6277f43a
---
Manifest ist die Metadatendatei, in der eine Komponente definiert wird. Es handelt sich um ein `XML`-Dokument, das Folgendes beschriebt:

- Der Namespace der Komponente.
- Die Art der Daten, die konfiguriert werden können, entweder ein Feld oder ein Datensatz.
- Alle Eigenschaften, die in der Anwendung konfiguriert werden können, wenn die Komponente hinzugefügt wird.
- Eine Liste der Ressourcenfelder, die die Komponente benötigt. 
  - Eine davon muss eine JavaScript-Webressource sein. Dies JavaScript muss eine Funktion enthalten, die ein Objekt instanziiert. Dies implementiert eine Schnittstelle, die Methoden zur Verfügung stellt, die obligatorisch sind, damit die Komponente funktioniert. Dies wird als Komponentenimplementierungsbibliothek bezeichnet.
- Der Name einer JavaScript-Funktion in der Komponentenimplementierungsbibliothek, die ein Objekt zurückgibt, das für die Benutzeroberfläche der erforderlichen Komponente gilt.

Wenn eine Komponente in der Anwendung konfiguriert wird, filtern die Daten im Manifest verfügbare Komponenten aus, damit nur gültige Komponenten für den Kontext für die Konfiguration verfügbar sind. Die im Manifest definierten Eigenschaften für eine Komponente werden als Konfigurationsfelder gerendert, sodass die Person, die die Komponente konfiguriert, Werte angeben kann. Diese Eigenschaftswerte sind dann zur Laufzeit in Ihrer Komponentenfunktion verfügbar.