---
title: " Deaktivieren oder Aktivieren eines Benutzers (Common Data Service) | Microsoft Docs"
description: In diesem Beispiel wird gezeigt, wie Sie einen Systembenutzer deaktivieren und aktivieren.
ms.custom: ''
ms.date: 1/27/2020
ms.reviewer: pehecke
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
ms.openlocfilehash: 03cd88528ee3851fc1eae44dab94bcb961af9e59
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155822"
---
# <a name="sample-disable-or-enable-a-user"></a>Beispiel: Aktivieren oder Deaktivieren eines Benutzers

Dieses Beispiel zeigt, wie ein Systembenutzerkonto in einer Online- oder Vor-Ort-/IFD-Umgebung deaktiviert und aktiviert werden kann.

Sie können das Beispiel [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/DisableOrEnableUser) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

Das Benutzerkonto für die Customer Engagement, unter dem Sie dieses Programm ausführen, muss die Rolle des Systemadministrators haben, um einen Systembenutzer zu aktivieren/deaktivieren.

Bevor Sie dieses Beispiel erstellen, öffnen Sie die Lösung in Visual Studio und wählen Sie **Ansicht** > **Aufgabenliste**. Es gibt zwei TODO-Kommentare, die Sie befolgen müssen, um die erforderlichen Informationen über einen bestehenden Systembenutzer in Ihrer Organisation bereitzustellen.

Weitere Informationen unter [Wie man Beispiele lässt](https://github.com/microsoft/PowerApps-Samples/blob/master/cds/README.md) zum Ausführen dieses Beispiels.

## <a name="what-this-sample-does"></a>Funktionsweise:

Das Beispiel ruft den Bezeichner eines vorhandenen Systembenutzers ab und deaktiviert oder aktiviert dieses Benutzerkonto.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichtung

Ruft den Bezeichner eines vorhandenen Systembenutzers ab, den Sie angeben (siehe [Ausführen dieses Beispiels](#how-to-run-this-sample)).

### <a name="demonstrate"></a>Demonstrieren

Veranschaulicht`SetStateRequest` die Verwendung zum Deaktivieren und Aktivieren eines Systembenutzers. Zeigt auch, wie Sie Informationen über einen Systembenutzer abrufen können.

Um die Zusammenfassung des angegebenen Systembenutzers unter Customer Engagement anzuzeigen, navigieren Sie zu **Einstellungen** > **Sicherheit** > **Benutzer** und wählen Sie das Zielsystembenutzerkonto in der Liste aus. Falls gewünscht, wählen Sie die Systemansicht **Deaktivierte Benutzer**, um die Liste aller Benutzer zu filtern. Der Status des Benutzers sollte "Deaktiviert" lauten.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option zum Aktivieren des Benutzerkontos an, das in der `Main()` Methode deaktiviert wurde.

Die Antwort Ja ist optional, falls Sie das deaktivierte Benutzerkonto in Customer Engagement untersuchen möchten. Sie können das Benutzerkonto in Active Directory oder Office 365 manuell aktivieren, um dasselbe Ergebnis zu erzielen.