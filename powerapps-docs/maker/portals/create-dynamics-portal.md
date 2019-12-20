---
title: Erstellen eines Portals in einer Umgebung die modellgesteuerte Apps in Dynamics 365 enthält | Microsoft-Dokumentation
description: Anweisungen zum Erstellen eines Portals in einer Umgebung, die modellgesteuerte Apps in Dynamics 365 enthält.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 896f6cfe9fabf08606e69b68b9957835a0147aee
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "2873395"
---
# <a name="create-a-portal-in-an-environment-containing-model-driven-apps-in-dynamics-365"></a>Erstellen Sie ein Portal in einer Umgebung, die modellgesteuerte Apps in Dynamics 365 enthält

Wenn Sie eine Umgebung auswählen, die modellgesteuerte Apps in Dynamics 365 (wie zum Beispiel Dynamics 365 Sales, Dynamics 365 Customer Service) enthält, können Sie die in [Portalvorlagen](portal-templates.md) erwähnten Portale erstellen.

1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.

2.  Wählen Sie im linken Bereich **Erstellen** aus und geben Sie **Portal** in das Feld **Suchvorlagen** ein, um alle Dynamics 365-Portalvorlagen anzuzeigen.

    > [!div class=mx-imgBorder]
    > ![Dynamics 365-Portalvorlagen](media/dynamics-portals.png "Dynamics 365-Portalvorlagen")  

3.  Wählen Sie die erforderliche Portalvorlage aus.

4.  Geben Sie im Fenster "Portal erstellen" einen Namen für das Portal und die Adresse für die Website ein, und wählen Sie eine Sprache aus der Dropdownliste aus. Wählen Sie **Erstellen** aus, wenn Sie fertig sind. Der Erstellungsprozess ist der gleiche wie im Abschnitt [Erstellen eines Common Data Service-Starterportal](create-portal.md) beschrieben.

> [!NOTE]
> - Wenn Sie ein früheres Portal-Add-On erworben haben und ein Portal mit dem Add-On bereitstellen möchten, müssen Sie zur **Dynamics 365 Admin Center**-Seite gehen. Weitere Informationen: [Bereitstellen eines Portals mit dem früheren Portal-Add-On](provision-portal-add-on.md)
> - Wenn Sie ein Portal mit dem früheren Portal-Add-On bereitgestellt haben, können Sie es trotzdem noch anpassen und verwalten aus [make.powerapps.com](https://make.powerapps.com).
> - Die Bereitstellung von Portalen von [make.powerapps.com](https://make.powerapps.com) verbraucht nicht die vorherigen Portal-Add-Ons. Außerdem sind diese Portale werden nicht auf der Registerkarte **Anwendungen** auf der **Dynamics 365-Verwaltungscenter** Seite aufgelistet.
> - Ein Common Data Service Starterportal kann nicht von der **Dynamics 365-Verwaltungscenter** Seite erstellt werden.
> - Um die Portalerstellung in einem Mandanten zu deaktivieren, siehe [Portalerstellung in einem Mandanten deaktivieren](create-portal.md#disable-portal-creation-in-a-tenant).
> - Wenn Sie ein Portal erstellen, werden einige Lösungen installiert und Beispieldaten importiert.

