---
title: 'Kundenentitäten (Firma, Kontakt) (Common Data Service) | Microsoft Docs'
description: 'Die Entitäten Firma und Kontakt in Dynamics 365 werden für das Identifizieren und Verwalten von Kunden, für den Verkauf von Produkten und Services und für die Bereitstellung eines hervorragenden Kundenservice benötigt. Eine Kundenadressenentität wird verwendet, um die Adresse und Lieferinformationen für einen Kunden zu speichern.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="customer-entities-account-contact"></a>Kundenentitäten (Firma, Kontakt)

<!-- 
Was Mike Carter

https://docs.microsoft.com/dynamics365/customer-engagement/developer/customer-entities-account-contact

Refactor so that the links to entity reference are in the body, not just in the See allso.
Add some h2 sections so it is skimmable
 -->

Die Entitäten *Firma* und *Kontakt* in Common Data Service werden für das Identifizieren und Verwalten von Kunden, für den Verkauf von Produkten und Services und für die Bereitstellung eines hervorragenden Kundenservice benötigt. Eine *Kundenadressen*entität wird verwendet, um die Adresse und Lieferinformationen für einen Kunden zu speichern.  
  
## <a name="account-entity"></a>Firmenentität
 
Die Firmenentität ist eine der Entitäten in Common Data Service, denen die meisten anderen Entitäten angefügt oder untergeordnet werden. In Common Data Service steht eine Firma für ein Unternehmen, mit dem die Unternehmenseinheit eine Geschäftsbeziehung unterhält. Informationen, die zu einer Firma erfasst werden, sind alle relevanten Kontaktinformationen, Unternehmensinformationen, Kategorien, Beziehungstypen und Adresseinformationen. Weitere Informationen, die verwendet werden können, sind die folgenden Elemente:  
  
- Eine Firma kann fast jeder anderen Entität übergeordnet sein. Hierzu zählt auch eine andere Firma.  
  
- Eine Firma kann eine eigenständige Entität sein.  
  
- Eine Firma kann nur eine einzige Firma als übergeordnetes Element haben.  
  
- Firmen können mehrere untergeordnete Firmen und untergeordnete Kontakte aufweisen.  
  
Die Verwaltung von Firmen ist eine der wichtigen Konzepte in der Business-to-Business-Kundenbeziehungsverwaltung (Dynamics 365), weil eine Organisation den Überblick über alle ihre Aktivitäten mit einer anderen Firma behalten will. All diese Aktivitäten werden auf der Ebene eines Firmenkontos zusammengeführt.  

Weitere Informationen: [Firmenentität](reference/entities/account.md)
  
## <a name="contact-entity"></a>Kontakt Entität

In Common Data Service kann ein Kontakt eine Person, in der Regel ein Individuum, mit dem eine Unternehmenseinheit eine Geschäftsbeziehung wie Kunde, Lieferant oder Kollege unterhält, darstellen. Die Kontaktentität ist eine der Entitäten, mit der die meisten anderen Entitäten verknüpft werden. Ein Kontakt kann eine eigenständige Entität sein. In dieser Entität können Informationen zu beruflichen, persönlichen und familiären Verhältnissen sowie mehrere Adressen enthalten sein. Weitere Informationen: [Kontakt-Entität](reference/entities/contact.md)
  
Firmen und Kontakte sind Bestandteil der Verwaltung von Kunden und stehen folgendermaßen in Beziehungen zueinander:  
  
- Ein Kontakt kann jeder anderen Entität übergeordnet sein, außer Firmen und Kontakten.  
  
- Ein Kontakt kann nur eine einzige Firma als übergeordnetes Element haben.  
  
- Ein Kontakt kann als primäre Kontaktperson für eine Firma gekennzeichnet werden, indem die Methode <xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*> verwendet wird.  
  
Die Kontaktentität speichert alle Informationen zu einer Person wie E-Mail-Adresse, Postadresse, Telefonnummern und weitere zugehörige Informationen wie Geburtstage oder Jahrestage. Je nach Kundentyp einer Unternehmenseinheit werden entweder nur Kontakte oder Kontakte und Firmen benötigt, um einen vollständigen Überblick über ihre Kunden bereitzustellen.  
  
Die wesentliche Vorgängen, die Sie mit einem Kontakt ausführen können, umfassen das Erstellen, Lesen, Aktualisieren und Löschen.  
  
Das Verknüpfen von Entitäten wie Aktivitäten und Notizen mit der Kontaktentität ermöglicht es Benutzern, ihre gesamte Kommunikation mit einem Kunden anzuzeigen, sowie alle Aktionen, die im Auftrag des Kunden durchgeführt wurden, und alle Informationen, die der Benutzer zu dem Kunden benötigt.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Firmenentität](reference/entities/account.md)  
  
 [Kontaktentität](reference/entities/contact.md)  
  
 [CustomerAddress-Entität](reference/entities/customeraddress.md)  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Geschäftsdaten modellieren mit Dynamics 365](/dynamics365/customer-engagement/developer/model-business-data)  
  
 [Unternehmensmanagement-Entitäten](/dynamics365/customer-engagement/developer/business-management-entities)
