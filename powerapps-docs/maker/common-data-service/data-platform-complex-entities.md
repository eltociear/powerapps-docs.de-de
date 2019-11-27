---
title: Komplexe Entitäten, die PowerApps Plan 2 Lizenzen erfordern | Microsoft Docs
description: Eine Liste der komplexen Entitäten in Common Data Service, die eine Lizenz für PowerApps Plan 2 benötigen.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: reference
ms.date: 09/26/2019
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: f5ec7419ea7369a57308e046ae820557303f0d15
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2706633"
---
# <a name="complex-entities-and-licensing"></a>Komplexe Entitäten und Lizenzierung

> [!IMPORTANT]
> Dieses Thema ist veraltet und wird in Kürze aktualisiert, um die neuesten Lizenzierungsänderungen zu berücksichtigen, die ab dem 1. Oktober 2019 gelten. Aktuelle Informationen zu den Lizenzbestimmungen für Unternehmen finden Sie im [PowerApps Lizenzhandbuch](https://go.microsoft.com/fwlink/?linkid=2085130).

Entitäten, die die folgende komplexe serverseitige Logik beinhalten, erfordern, dass Benutzer einer App oder eines Flow, die diese Entitäten verwendet, eine PowerApps Plan 2 oder Microsoft Flow Plan 2 Lizenz besitzen:

* Code-Plug-Ins. Weitere Informationen: [Plug-In-Entwicklung](/powerapps/developer/common-data-service/plug-ins)
* Echtzeitworkflows Weitere Informationen: [Workflowprozesse](/flow/workflow-processes)

    > [!IMPORTANT]
    >  Nur Workflows, die in einen Echtzeitworkflow konvertiert werden, werden als in Echtzeit und synchron betrachtet. Workflows, die im Hintergrund laufen, können weiterhin mit dem entsprechenden PowerApps-Plan verwendet werden und benötigen keine zusätzlichen Lizenzen.

Um zu wissen ob Sie Ihren Entitäten komplexere Geschäftslogik hinzugefügt haben, oder nicht, überprüfen Sie die Liste der Plug-In-Assemblys und Workflows, die in Ihrer Umgebung konfiguriert sind.

## <a name="complex-entities-installed-with-dynamics-365-apps"></a>Komplexe Entitäten, die mit Dynamics 365 Apps installiert wurden.
Die folgende Tabelle listet Entitäten auf, die im Rahmen der Installation von modellgetriebenen Anwendungen in Dynamics 365, wie beispielsweise Dynamics 365 Sales und Dynamics 365 Customer Service, komplexe serverseitige Logik out-of-the-box enthalten. Diese Liste ist als Leitfaden vorgesehen. Je nachdem, welche Dynamics 365-Anwendungen und -Versionen in Ihrer Umgebung installiert sind, kann die Liste der komplexen Entitäten variieren.

> [!NOTE]
>  Wenn Sie die Common Data Service verwenden und keine Dynamics 365-Anwendung oder Drittanbieterlösung installiert haben, verfügt Ihre Umgebung nicht über Entitäten, die komplexe serverseitige Logik enthalten.

* Firma
* Vereinbarung
* Vereinbarungsbuchungsdatum
* Vereinbarungsbuchungsvorfall
* Vereinbarungsbuchungsprodukt
* Vereinbarungsbuchungsservice
* Vereinbarungsbuchungsservice-Aufgabe
* Vereinbarungsbuchungssetup
* Vereinbarungsrechnungsdatum
* Vereinbarungsrechnungsprodukt
* Vereinbarungsrechnungssetup
* Substatus der Vereinbarung
* Buchbare Ressource
* Buchbare Ressourcenbuchung
* Kopfzeile für buchbare Ressourcenbuchungen
* Buchbare Ressourcenkategorie
* Zuordnung der buchbaren Ressourcenkategorie
* Merkmal der buchbaren Ressource
* Buchbare Ressourcengruppe
* Buchungswarnung
* Buchungswarnungsstatus
* Buchungsstatus
* Merkmal
* Kompetenzanforderung (veraltet)
* Mitbewerber
* Kontakt
* Kundenanlage
* Delegierung
* Expense
* Feldermittlung
* Field Service-Preislistenelement
* Filter
* Folgen
* Vorfalltyp
* Vorfalltypprodukt
* Vorfalltypservice
* Vorfalltyp-Serviceaufgabe
* Integrationsauftrag
* Detail zum Integrationsauftrag
* Bestandsanpassung
* Bestandsanpassungsprodukt
* Bestandsübertragung
* Rechnung
* Rechnungshäufigkeit
* Rechnungsposition
* Rechnungsposition
* Journal
* Erfassungsposition
* Lead
* Hinweise
* OData v4-Datenquelle
* Verkaufschance
* Verkaufschancenposition
* Verkaufschancenposition
* Auftrag
* Auftragsrechnungsprodukt
* Auftragsrechnungssetup
* Auftragsposition
* Zahlung
* Zahlungsdetails
* Beitragskonfiguration
* Beitragsregelkonfiguration
* PLZ
* Preisliste
* Preislistenelement
* Produkt
* Projekt
* Projektgenehmigung
* Projektvertragsposition
* Projektvertragszeilenmeilenstein
* Ressourcenkategorie für die Projektvertragszeile
* Transaktionskategorie für die Projektvertragszeile
* Projektparameter
* Projektphasen
* Statusbenutzer für Projektaufgabe
* Registrierung eines Projektteammitglieds
* Bestellung
* Bestellungsrechnung
* Bestellungsprodukt
* Bestellungszugang
* Bestellungsquittung Produkt
* Substatus der Bestellung
* Warteschlangenelement
* Angebot
* Angebotsbuchungsvorfall
* Angebotsbuchungsprodukt
* Angebotsbuchungsservice
* Angebotsbuchungsserviceaufgabe
* Angebotsbuchungssetup
* Angebotsrechnungsprodukt
* Angebotsrechnungssetup
* Angebotsposition
* Detailinformationen zur Angebotsposition
* Meilenstein der Angebotsposition
* Ressourcenkategorie für die Angebotsposition
* Transaktionskategorie der Angebotsposition
* Projektpreisliste des Angebots
* Bewertungsmodell
* Bewertungswert
* Anforderungsmerkmal
* Anforderungsressourcenkategorie
* Einstellung der Anforderungsressource
* Anforderungsstatus
* Ressourcenanfrage
* Ressourcenanforderung
* Ressourcenanforderungsdetail
* RMA
* RMA-Produkt
* RMA-Zugang
* RMA-Zugangsprodukt
* RMA-Substatus
* Rollenkompetenzanforderung
* Rollenpreis
* RTV
* RTV-Produkt
* RTV-Substatus
* Steuercode
* Steuercodedetail
* Zeiteintrag
* Zeitgruppe
* Zeitgruppendetail
* Anforderung von arbeitsfreier Zeit
* Transaktionskategoriepreis
* Benutzer
* Ansicht
* Pinnwandansicht
* Lagerort
* Arbeitsauftrag
* Arbeitsauftragsvorfall
* Arbeitsauftragsprodukt
* Arbeitsauftragsservice
* Arbeitsauftragsserviceaufgabe
* Substatus des Arbeitsauftrags
* Arbeitsvorlage


## <a name="licensing"></a>Lizenzierung
Weitere Informationen zu PowerApps und Dynamics 365 Lizenzen finden Sie auf der Seite [Lizenzübersicht](../../administrator/pricing-billing-skus.md).

