---
title: Lizenz Bezeichnung für eine APP | Microsoft-Dokumentation
description: Erläutert, wie die Lizenz Bezeichnung für die ausgewählte APP überprüft wird.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/24/2020
ms.author: alaug
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 95478501e6ca5af36ef993637b3612cdf1ea0196
ms.sourcegitcommit: 77e00640a59a7db9d67d3ac52f74d264cbe3a494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2020
ms.locfileid: "80328776"
---
# <a name="how-to-check-license-designation-for-an-app"></a>Überprüfen der Lizenz Bezeichnung für eine APP

Ab dem 2019 werden mehrere Connectors von Standard zu Premium neu klassifiziert.

Häufig gestellte Fragen zur [powerapps-Lizenzierung](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#office-365) umklassifizierte Connectors. Apps, die diese Connectors vor der Neuklassifizierung verwenden, wurde ein längerer Zeitraum gewährt, sodass Benutzer ohne Premium-Lizenz auf diese apps zugreifen können.

In der folgenden Tabelle werden die Bezeichnungen und die Lizenz erläutert, die ein Endbenutzer für den Zugriff auf eine APP benötigen muss.

| **Kennzeichnungs** | **Definition**
|-|-|
| Standard | Eine APP, die nur Standardconnectors verwendet. Ein Endbenutzer muss über einen powerapps für Office 365-Plan, pro App-Plan oder einen pro-Benutzer-Plan verfügen, um auf diese APP zuzugreifen.
| Erweitert | Eine APP, die Connectors verwenden darf, die am 1. Oktober 2019 auf Premium herauf gestuft wurden. Ein Endbenutzer muss über einen powerapps für Office 365-Plan, pro App-Plan oder pro Benutzer Plan verfügen. Häufig gestellte Fragen zur  [powerapps-Lizenzierung](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#office-365) , welche Connectors am 1. Oktober 2019 zu Premium herauf gestuft wurden.
| Premium | Eine APP, die mindestens einen Premium-Connector verwendet. Ein Endbenutzer muss über einen pro-App-Plan oder einen Benutzer Plan verfügen, auf den zugegriffen werden soll.

## <a name="check-app-license-designation-from-app-settings"></a>App-Lizenz Bezeichnung über App-Einstellungen überprüfen

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.

1. Wählen Sie **apps** von Links aus.

1. Wählen Sie eine APP aus der APP-Liste aus. Verwenden Sie die Option **Einstellungen** von oben oder, verwenden Sie die **weiteren Befehle** (**...**) und dann **Einstellungen** aus dem Dropdown Menü:

    ![Einstellungs Option](media/license-designation/app-settings.png)

1. Wählen Sie **Einstellungen** aus, um die Informationen zur Lizenz Bezeichnung anzuzeigen:

    ![Lizenz Bezeichnung aus Einstellungen](media/license-designation/settings-license-designation.png)

## <a name="check-app-license-designation-from-app-details"></a>App-Lizenz Bezeichnung über App-Details überprüfen

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.

1. Wählen Sie **apps** von Links aus.

1. Wählen Sie eine APP aus der APP-Liste aus. Sie können die Option **Details** von oben oder aus verwenden. verwenden Sie dazu die **weiteren Befehle** (**...**) und dann **Details** aus dem Dropdown Menü:

    ![App-Details](media/license-designation/app-details.png)

1. **Details**auswählen:

    ![App-Bezeichnung in Details](media/license-designation/app-details-page.png)

## <a name="pass-assignment"></a>Pass Zuweisung

Weitere Informationen zur Pass Zuweisung finden Sie unter [powerapps pro App-Pläne](https://docs.microsoft.com/power-platform/admin/about-powerapps-perapp#step-three-set-up-apps-to-use-per-app-plans).

## <a name="next-steps"></a>Nächste Schritte

- [FAQ zu powerapps-Lizenzierung](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq)

### <a name="see-also"></a>Siehe auch

- [Bearbeiten einer APP](edit-app.md)
- [Eine App löschen](delete-app.md)
