---
title: 'Komplexe Entitäten, die PowerApps-Plans 2-Lizenzen benötigen | Microsoft Docs'
description: 'Eine Liste der komplexen Entitäten in Common Data Service, für die eine PowerApps-Plans 2-Lizenz erforderlich ist.'
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: reference
ms.date: 07/17/2018
ms.author: lanced
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="complex-entities-and-licensing"></a>Komplexe Entitäten und Lizenzierung
Für Entitäten, die die folgende komplexe serverseitige Logik enthalten, benötigen Benutzer einer App oder eines Flows, der diese Entitäten verwendet, eine PowerApps-Plan 2- oder Microsoft Flow Plan 2-Lizenz:

* Code-Plug-Ins. Weitere Informationen: [Plug-In-Entwicklung](https://docs.microsoft.com/dynamics365/customer-engagement/developer/plugin-development)
* Echtzeitworkflows Weitere Informationen: [Workflowprozesse](https://docs.microsoft.com/dynamics365/customer-engagement/customize/workflow-processes)

    > [!IMPORTANT]
    >  Nur Workflows, die in einen Echtzeitworkflow konvertiert werden, werden als in Echtzeit und synchron betrachtet. Workflows, die im Hintergrund ausgeführt werden, können mit dem entsprechenden PowerApps-Plan weiterhin verwendet werden und erfordern keine zusätzlichen Lizenzen.

Um zu wissen ob Sie Ihren Entitäten komplexere Geschäftslogik hinzugefügt haben, oder nicht, überprüfen Sie die Liste der Plug-In-Assemblys und Workflows, die in Ihrer Umgebung konfiguriert sind.

## <a name="complex-entities-installed-with-dynamics-365"></a>Mit Dynamics 365 installierte komplexe Entitäten
Die folgende Tabelle gibt Aufschluss über die Entitäten, die standardmäßig komplexer serverseitige Logik im Rahmen einer Dynamics 365-Anwendungsinstallation enthalten. Diese Liste ist als Leitfaden vorgesehen. Je nachdem, welche Dynamics 365-Anwendungen und -Versionen in Ihrer Umgebung installiert sind, kann sich die Liste der komplexen Entitäten unterscheiden.

> [!NOTE]
>  Wenn Sie den Common Data Service verwenden und keine Dynamics 365-Anwendung oder Lösung von Drittanbietern installiert haben, hat Ihre Umgebung keine Entitäten, die komplexe serverseitige Logik enthalten.

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
Weitere Informationen zu PowerApps und Dynamics 365-Lizenzen finden Sie unter [Lizenzierungsübersicht](../../administrator/pricing-billing-skus.md).

