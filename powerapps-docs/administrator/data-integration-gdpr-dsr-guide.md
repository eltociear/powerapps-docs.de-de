---
title: Datenintegration für Administratorkundendaten
description: Ermitteln, Exportieren und Löschen von personenbezogenen Daten bei der Datenintegration für Administratoren für CDS für Apps
author: sabinn-msft
ms.service: powerapps
ms.topic: how-to
ms.component: cds
ms.date: 05/20/2018
ms.author: sabinn
search.audienceType:
- admin
search.app:
- D365CE
- PowerApps
- Powerplatform
ms.openlocfilehash: 4a0cb3dfedfcc79c2c68575c8c001af6a800c269
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "42862131"
---
# <a name="responding-to-data-subject-rights-dsr-requests-for-data-integration-for-common-data-service-for-apps-customer-data"></a>Reagieren auf DSR-Anforderungen (Data Subject Rights) für die Integration von Kundendaten in Common Data Service für Apps

## <a name="introduction-to-dsr-requests"></a>Einführung in DSR-Anforderungen

Die Datenschutz-Grundverordnung (DSGVO) der Europäischen Union gibt den Menschen (in dieser Verordnung als „Datensubjekte“ bezeichnet) das Recht, ihre personenbezogenen Daten zu verwalten, die von einem Arbeitgeber, einer Agentur oder einer Organisation („Für die Verarbeitung Verantwortlicher“ oder „Verantwortlicher“) erfasst werden. Personenbezogene Daten sind in der DSGVO sehr umfassend definiert als alle Informationen, die sich auf eine identifizierte oder identifizierbare natürliche Person beziehen. Die DSGVO erteilt betroffenen Personen folgende Rechte bezüglich ihrer personenbezogenen Daten:

- Recht auf das Erhalten einer Kopie
- Recht auf Berichtigung
- Recht auf Einschränkung der Verarbeitung
- Recht auf Löschung
- Recht auf Datenübertragbarkeit

Eine betroffene Person kann bei einem Verantwortlichen mit einem formellen Antrag die Einschränkung der Verarbeitung von personenbezogenen Daten verlangen. Dieser Antrag wird auch DSR-Anforderung (Data Subject Rights, Rechte betroffener Personen) genannt.

In diesem Artikel wird beschrieben, welche Vorbereitungen Microsoft bezüglich der Datenschutz-Grundverordnung trifft. Darüber hinaus gibt der Artikel einen Überblick über Maßnahmen, die Sie ergreifen können, um den Bestimmungen der DSGVO nachzukommen, wenn Sie die Datenintegration für Administratoren über das Administratorportal in CDS für Apps verwenden. Sie erfahren, wie Sie als Verantwortlicher mit Microsoft-Produkten, -Diensten und -Verwaltungstools im Rahmen einer DSR-Anforderung personenbezogene Daten in der Microsoft-Cloud finden, darauf zugreifen und diese behandeln können.

### <a name="searching-for-and-identifying-personal-data"></a>Suchen nach und Ermitteln von personenbezogenen Daten

Die Datenintegration für Administratoren in CDS für Apps ermöglicht es sämtlichen Benutzern der Integratoranwendung, ihre Daten über die Registerkarte „Datenintegration“ abzurufen:

[https://admin.powerapps.com/dataintegration](https://admin.powerapps.com/dataintegration)

Die für den Benutzer gespeicherten Daten werden im Portal angezeigt. Alle Projekte werden auf der Registerkarte „Projekte“ aufgeführt:

![Projekte über die Registerkarte „Projekte“ abrufen](./media/data-integration-gdpr-dsr/projects-tab.png)

Alle Verbindungsgruppen werden auf der Registerkarte „Verbindungsgruppen“ angezeigt:

![Verbindungsgruppen auf der Registerkarte „Verbindungsgruppen“ abrufen](./media/data-integration-gdpr-dsr/connections-tab.png)

Alle Vorlagen sind auf der Registerkarte „Vorlagen“ aufgeführt:

![Vorlagen auf der Registerkarte „Vorlagen“ abrufen](./media/data-integration-gdpr-dsr/templates-tab.png)

## <a name="securing-and-controlling-access-to-personal-information"></a>Sichern und Kontrollieren des Zugriffs auf personenbezogene Informationen

Im Rahmen der Datenintegration für Administratoren in CDS für Apps kann auf Daten, die von der Datenintegrationsanwendung gespeichert werden, nur über das Administratorportal zugegriffen werden.

## <a name="deleting-personal-data"></a>Löschen von persönlichen Daten

Im Rahmen der Datenintegration für Administratoren in CDS für Apps kann der Benutzer die von ihm erstellten Daten, Projekte und Verbindungsgruppen löschen. Zum Löschen von personenbezogenen Daten können sich die Benutzer im Administratorportal anmelden: [https://admin.powerapps.com](https://admin.powerapps.com).

Benutzer können Projekte löschen, indem sie zur Registerkarte „Projekte“ navigieren, auf die Auslassungspunkte neben dem Projekt klicken und dann die Option „Löschen“ auswählen:

![Projekte mit einem Klick auf die Auslassungspunkte löschen](./media/data-integration-gdpr-dsr/projects-del.png)

Benutzer können Vorlagen löschen, indem sie zur Registerkarte „Vorlagen“ navigieren, auf die Auslassungspunkte neben der Vorlage klicken und dann die Option „Löschen“ auswählen:

![Vorlagen mit einem Klick auf die Auslassungspunkte löschen](./media/data-integration-gdpr-dsr/templates-del.png)

Benutzer können Verbindungsgruppen löschen, indem sie zur Registerkarte „Verbindungsgruppen“ navigieren, auf die Auslassungspunkte neben der Verbindungsgruppe klicken und die Option löschen auswählen:

![Verbindungsgruppen mit einem Klick auf die Auslassungspunkte löschen](./media/data-integration-gdpr-dsr/connsets-del.png)

## <a name="exporting-personal-data"></a>Exportieren von persönlichen Daten

Im Rahmen der Datenintegration für Administratoren in CDS für Apps kann der Benutzer die von ihm erstellten Daten exportieren. Zum Exportieren von personenbezogenen Daten können sich Benutzer im Administratorportal anmelden:

[https://admin.powerapps.com](https://admin.powerapps.com)

Zum Exportieren von Projekten (mit Ausführungsverlauf) können Benutzer zur Registerkarte „Projekte“ navigieren und auf die Auslassungspunkte neben dem Projekt klicken. Anschließend können sie die gewünschte Exportoption auswählen:

![Projekte mit einem Klick auf die Auslassungspunkte exportieren](./media/data-integration-gdpr-dsr/projects-exp.png)

Benutzer können Vorlagen exportieren, indem sie zur Registerkarte „Vorlagen“ navigieren, auf die Auslassungspunkte neben der Vorlage klicken und dann die Option „Exportieren“ auswählen:

![Vorlagen mit einem Klick auf die Auslassungspunkte exportieren](./media/data-integration-gdpr-dsr/templates-exp.png)

Benutzer können Verbindungsgruppen exportieren, indem sie zur Registerkarte „Verbindungsgruppen“ navigieren, auf die Auslassungspunkte neben der Verbindungsgruppe klicken und dann die Option „Exportieren“ auswählen:

![Verbindungsgruppen mit einem Klick auf die Auslassungspunkte exportieren](./media/data-integration-gdpr-dsr/connsets-exp.png)
