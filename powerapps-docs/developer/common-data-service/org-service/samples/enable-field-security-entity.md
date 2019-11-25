---
title: 'Beispiel: Feldsicherheit für eine Entität aktivieren (Common Data Service) Microsoft-Dokumentation'
description: Dieses Beispiel zeigt die Aktivierung der Feldsicherheit für eine Entität
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 6121c32e74c0c302fe9370a67f960eee2d498033
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748748"
---
# <a name="sample-enable-field-security-for-an-entity"></a>Beispiel: Aktivierung der Feldsicherheit für eine Entität

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-enable-field-security-entity -->

Dieses Beispiel zeigt die Aktivierung der Feldsicherheit für eine Entität.  Sie können das Beispiel herunterladen von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/FieldSecurity). 

Dieses Beispiel benötigt weitere Benutzer, die nicht in Ihrem System sind. Legen Sie die erforderlichen Benutzer manuell in **Office 365** an, um das Beispiel fehlerfrei auszuführen. Erstellen Sie für dieses Beispiel ein Benutzerprofil **wie** unten gezeigt. 

**Vorname**: Samantha<br/>
**Nachname**: Smith<br/>
**Sicherheitsrolle**: Marketing Manager<br/>
**Benutzername**: ssmith@yourorg.onmicrosoft.com<br/>

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das oben beschriebene Beispiel zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Ruft den Benutzer ab, den Sie manuell **Office 365** erstellt haben.
3. Rufen Sie die Sicherheitsrolle ab, die erforderlich ist, um dem Benutzer zuzuweisen. 
4. Rufen Sie die Standardunternehmenseinheit ab, die benötigt wird, um das Team zu erstellen.
5. Instanziieren Sie einen Teamentitätsdatensatz und legen Sie die Eigenschaftswerte fest. 

### <a name="demonstrate"></a>Demonstrieren

1. Erstellt Feldsicherheitsprofil und erstellt das Anforderungsobjekt und legt die Moniker mit der Beziehung teamprofiles_assocation fest.
2. Erstellt benutzerdefinierte Aktivitätsentität und Attribute mithilfe der `CreateAttributeRequest` und `CreateEntityRequest` Message.
3. Erstellen Sie geschäftsentscheidende Feldberechtigung für das Identitätsattribut.

### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um die Datensätze in [Einrichtung](#setup) zu löschen.

    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
