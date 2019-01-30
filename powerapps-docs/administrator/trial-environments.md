---
title: Testumgebungen | Microsoft-Dokumentation
description: Erhalten Sie mit dem PowerApps-Vorschauprogramm vorab Zugriff auf Funktionen.
author: manasmams
manager: kvivek
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 01/09/2019
ms.author: manasma
search.audienceType:
- admin
search.app:
- D365CE
- PowerApps
- Powerplatform
ms.openlocfilehash: bd05c4c1251058d464034de71d9b1c287e714190
ms.sourcegitcommit: 170deba334c922157bbb826c795bed3fa858b85e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2019
ms.locfileid: "54196138"
---
# <a name="about-trial-environments"></a>Testumgebungen

Derzeit können Sie zwei Arten von Common Data Service-Umgebungen (CDS) für Apps erstellen: Testumgebungen oder Produktionsumgebungen. Mit einer Testumgebung können Sie Dynamics 365 Customer Engagement-Apps kostenlos testen. Testumgebungen laufen nach 30 Tagen ab.

Wenn Sie die Umgebungstypen, über die Sie verfügen, und das Ablaufdatum Ihrer Testumgebungen anzeigen möchten, öffnen Sie die Seite **Umgebungen**:

> [!div class="mx-imgBorder"] 
> ![PowerApps-Umgebungen](media/powerapps-environments75b.png "PowerApps-Umgebungen")

## <a name="convert-a-trial-environment-to-production"></a>Konvertieren einer Testumgebung in eine Produktionsumgebung

Wenn Sie bei der Verwendung einer Testumgebung Ressourcen erstellt haben, die länger als 30 Tage zur Verfügung stehen sollen, können Sie die Testumgebung in eine Produktionsumgebung konvertieren.

Folgende Anforderungen müssen Sie erfüllen, wenn Sie in eine Produktionsumgebung konvertieren möchten:

**Ein geeigneter PowerApps-Plan:** Ein Plan, mit dem Sie Produktionsumgebungen erstellen können, z. B. PowerApps-Plan 2. Informationen zu PowerApps-Plänen, die Produktionsumgebungen enthalten, finden Sie unter [Die richtigen Pläne für Ihr Team auswählen](https://powerapps.microsoft.com/pricing/). Informationen zum Bestimmen Ihrer PowerApps-Pläne finden Sie unter [Wie bestimme ich meine Pläne?](#how-do-i-identify-my-plans).
**Verfügbares Kontingent für Produktionsumgebungen:** Mit Ihrem Plan können Sie eine feste Anzahl von Produktionsumgebungen erstellen. Mit PowerApps Plan 2 können Sie z.B. zwei Produktionsumgebungen erstellen. Wenn Sie diese bereits erstellt haben, müssen Sie zunächst eine bereits vorhandene Produktionsumgebung löschen, bevor eine weitere erstellt werden kann. Weitere Informationen finden Sie unter [Erstellen einer Umgebung](environments-overview.md#creating-an-environment).

Gehen Sie zum Konvertieren einer Testumgebung in eine Produktionsumgebung wie folgt vor:

1. Melden Sie sich auf der Seite [https://admin.powerapps.com/environments](https://admin.powerapps.com/environments) als Administrator an.
 
2. Öffnen Sie die Seite **Umgebungen**, und wählen Sie die Testumgebung aus, die Sie in eine Produktionsumgebung konvertieren möchten:

    > [!div class="mx-imgBorder"] 
    > ![Auswählen der Testumgebung](media/powerapps-environments75b-select-trial.png "Auswählen der Testumgebung")

3. Klicken Sie auf der Registerkarte **Details** auf **Konvertieren**:

    > [!div class="mx-imgBorder"] 
    > ![Auswählen der Option „Konvertieren“](media/powerapps-trial-select-convert.png "Auswählen der Option „Konvertieren“")

4. Klicken Sie auf **Bestätigen**:

    > [!div class="mx-imgBorder"] 
    > ![Auswählen der Option „Bestätigen“](media/powerapps-trial-select-confirm.png "Auswählen der Option „Bestätigen“")

Wenn Ihre Umgebung über eine Datenbank verfügt, kann die Konvertierung in eine Produktionsumgebung mehrere Stunden dauern. Der Fortschritt des Konvertierungsvorgangs wird auf der Registerkarte **Details** als Benachrichtigung angezeigt:

  > [!div class="mx-imgBorder"] 
  > ![Konvertierung gestartet](media/powerapps-trial-conversion-started.png "Konvertierung gestartet")

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen

### <a name="who-can-convert-a-trial-environment-to-a-production-environment"></a>Wer kann eine Testumgebung in eine Produktionsumgebung konvertieren?

Sie müssen die folgenden Anforderungen erfüllen, um eine Testumgebung in eine Produktionsumgebung konvertieren zu können:

**Über einen geeigneten PowerApps Plan verfügen:** Sie benötigen einen Plan, mit dem Sie Produktionsumgebungen erstellen können, z.B. PowerApps Plan 2. Informationen zu PowerApps-Plänen, die Produktionsumgebungen enthalten, finden Sie unter [Die richtigen Pläne für Ihr Team auswählen](https://powerapps.microsoft.com/pricing/). Informationen zum Bestimmen Ihrer PowerApps-Pläne finden Sie unter [Wie bestimme ich meine Pläne?](#how-do-i-identify-my-plans).
**Über ein Kontingent für Produktionsumgebungen verfügen:** Mit Ihrem Plan können Sie eine feste Anzahl von Produktionsumgebungen erstellen. Mit PowerApps Plan 2 können Sie z.B. zwei Produktionsumgebungen erstellen. Wenn Sie diese bereits erstellt haben, müssen Sie zunächst eine bereits vorhandene Produktionsumgebung löschen, bevor eine weitere erstellt werden kann.

### <a name="what-if-i-dont-have-available-quota-for-production-environments"></a>Was kann ich tun, wenn ich kein Kontingent für Produktionsumgebungen mehr zur Verfügung habe?

Wenden Sie sich an Ihren globalen Office 365-Administrator oder Azure AD-Mandantenadministrator (Azure Active Directory) für folgende Optionen:
- Ihnen wird PowerApps Plan 2 zugewiesen. 
- Es wird ein anderer Benutzer mit einem verfügbaren Kontingent für Produktionsumgebungen ausfindig gemacht.

Sie können auch einen PowerApps-Plan erwerben.

### <a name="can-every-office-365-global-admin-or-azure-ad-tenant-admin-convert-a-trial-environment-to-a-production-environment"></a>Kann jeder globale Office 365-Administrator oder Azure AD-Mandantenadministrator eine Testumgebung in eine Produktionsumgebung konvertieren?

Nein. Globale Administratoren und Azure AD-Mandantenadministratoren müssen ein Kontingent für Produktionsumgebungen zur Verfügung haben, um eine Testumgebung in eine Produktionsumgebung konvertieren zu können.

### <a name="is-there-a-way-to-recover-a-deleted-trial-environment"></a>Gibt es eine Möglichkeit, eine gelöschte Testumgebung wiederherzustellen?

Die Wiederherstellung einer gelöschten Testumgebung kann nicht garantiert werden. Doch wir werden uns alle Mühe geben, die Testumgebung innerhalb von sieben Tagen nach der Löschung wiederherzustellen. Es ist nicht möglich, die Datenbank der Umgebung wiederherzustellen, doch bei den (mit PowerApps erstellten) Apps und Flows ist es eventuell möglich.

### <a name="how-can-i-retain-my-data-and-resources-if-i-dont-have-a-way-to-convert-the-trial-environment-to-a-production-environment"></a>Wie kann ich meine Daten und Ressourcen beibehalten, wenn ich die Testumgebung nicht in eine Produktionsumgebung konvertieren kann?

Sie können Ihre Ressourcen und Daten in eine andere Umgebung exportieren. Wenn Sie diese für einen längeren Zeitraum beibehalten möchten, wird empfohlen, eine Produktionsumgebung oder eine individuelle Umgebung (mit PowerApps-Communityplan) zu erstellen. Anschließend können Sie Ihre Ressourcen in diese Umgebung exportieren. 

Folgende Richtlinien gelten beim Exportieren von Ressourcen:

|Typ der Ressource in der Umgebung  |Wie exportiere ich die Ressource?  |
|---------|---------|
|Apps (Canvas-Apps und modellgesteuerte Apps) und Flows     |Apps und Flows können aus einer Umgebung mithilfe von [Paketerstellung](environment-and-tenant-migration.md) exportiert werden.         |
|Daten in der Datenbank (Common Data Service-Umgebung (CDS) für Apps)     |Sie haben mehrere Optionen:<br/><ul><li>[Exportieren der Daten nach Excel](../user/export-data-excel.md) und Speichern der Daten. Sie können die Daten in eine andere Umgebung [importieren](../user/import-data.md).</li><br/><li>Sie können die Daten mithilfe von [Data Integrator-Diensten](data-integrator.md) und APIs in eine andere Umgebung exportieren.</li></ul> |

Testumgebungen ohne jegliche Aktivität in den Umgebungsdatenbanken während der letzten 30 Tage werden gelöscht.

### <a name="how-can-i-create-a-production-or-an-individual-environment"></a>Wie kann ich eine Produktionsumgebung oder eine individuelle Umgebung erstellen?

Dazu benötigen Sie einen PowerApps Plan, der das Erstellen von Produktionsumgebungen enthält. Weitere Informationen finden Sie unter [Erstellen einer Umgebung](environments-overview.md#creating-an-environment).

Wenn Sie eine individuelle Umgebung erstellen möchten, registrieren Sie sich für den [PowerApps-Communityplan](https://powerapps.microsoft.com/communityplan/). Beachten Sie, dass bei individuellen Umgebungen für die Freigabe von Apps Einschränkungen gelten, da diese Umgebungen nur zur persönlichen Verwendung gedacht sind.

### <a name="how-do-i-identify-my-plans"></a>Wie bestimme ich meine Pläne?

Klicken Sie zum Bestimmen Ihrer Pläne auf das **Zahnradsymbol** in der oberen rechten Ecke der PowerApps-Website, und klicken Sie dann auf **Pläne**.

> [!div class="mx-imgBorder"] 
> ![Auswählen der Option „Pläne“](media/powerapps-plans.png "Auswählen der Option „Pläne“")

### <a name="see-also"></a>Siehe auch
[Administer environments in PowerApps (Verwalten von Umgebungen in PowerApps)](environments-administration.md)<br/>
[Umgebungen – Übersicht](environments-overview.md)<br/>
[Die richtigen Pläne für Ihr Team auswählen](https://powerapps.microsoft.com/pricing/)<br/>
[Übersicht über die Lizenzierung](pricing-billing-skus.md)<br/>
