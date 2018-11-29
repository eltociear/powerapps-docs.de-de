---
title: Xrm.WebApi.offline (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 848c277b-bd44-4388-852a-0f59a3a15538
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="xrmwebapioffline-client-api-reference"></a>Xrm.WebApi.offline (Client-API-Referenz)



[!INCLUDE[./includes/offline-description.md](./includes/offline-description.md)] 

Informationen zur Mobile offline Funktion finden Sie unter [Konfigurieren Sie Mobile offline Synchronisierung, um Benutzer die Verwendung im Offlinemodus auf einem Mobilgerät zu ermöglichen](/dynamics365/customer-engagement/mobile-app/configure-mobile-offline-synchronization-dynamics-365-phones-tablets)

`var offlineWebApi = Xrm.WebApi.offline;`

> [!NOTE]
> Sie müssen **Xrm.WebApi.offline** anstelle der [veralteten](/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming#some-client-apis-are-deprecated) **Xrm.Mobile.Offline** verwenden, um Datensätze in mobilen Clients zu erstellen und zu verwalten, während Sie im Offlinemodus arbeiten.

Das **offlineWebApi**-Objekt stellt die folgenden Methoden bereit. Wenn Sie im Offlinemodus arbeiten, gehen diese Methoden nur für Entitäten, die für Mobile offline Synchronisierung aktiviert und im Mobile offline Profil des aktuellen Benutzers verfügbar sind.

- [createRecord](createRecord.md)
- [deleteRecord](deleteRecord.md)
- [isAvailableOffline](isAvailableOffline.md)
- [retrieveRecord](retrieveRecord.md)
- [retrieveMultipleRecords](retrieveMultipleRecords.md)
- [updateRecord](updateRecord.md)

> [!IMPORTANT]
> Beim Erstellen oder Aktualisieren des Datensatzes im Offlinemodus werden nur grundlegende Überprüfungen für die eingegebenen Daten durchgeführt. Grundlegende Überprüfung umfasst Dinge wie Sicherstellen, dass der Entitätsattributname in Kleinbuchstaben angegeben und für eine Entität vorhanden ist, Überprüfung auf Datentypkonflikt für den angegebenen Attributwert, Verhindern, dass Datensätze mit demselben GUID-Wert erstellt werden, Überprüfen, ob die verknüpfte Entität offline aktiviert ist, wenn verknüpfte Entitätsdatensätze abgerufen werden, und prüfen, ob der Datensatz, den Sie anzeigen, überprüfen, aktualisieren oder löschen möchten, tatsächlich im Offlinedatenspeicher vorhanden ist. Überprüfungen auf Geschäftsebene finden nur statt, wenn Sie mit dem Server verbunden sind und die Daten synchronisiert werden. Ein Datensatz wird erstellt oder aktualisiert, wenn die Eingabedaten vollständig gültig sind.

### <a name="related-topics"></a>Verwandte Themen

[Xrm.WebApi.online](online.md)

[Xrm.WebApi](../xrm-webapi.md)



