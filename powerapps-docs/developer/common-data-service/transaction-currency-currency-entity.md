---
title: Entität der Transaktionswährung (Währung) (Common Data Service) | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Transaktionswährung, die eine Mehrfachwährungsfunktion ist und es Benutzern ermöglicht, finanzielle Transaktionen in mehreren Währungen auszuführen. Mehrere Datensätze in verschiedenen Transaktionswährungen können in einer einheitlichen Währung aggregiert, verglichen oder analysiert werden, indem die Basiswährung verwendet wird.
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
ms.openlocfilehash: 28dac174671b4577a42e488afa4e007f7e0d9212
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748635"
---
# <a name="transaction-currency-currency-entity"></a>Entität der Transaktionswährung (Währung)

Common Data Service ist ein Mehrfachwährungssystem, in dem jeder Datensatz seiner eigenen Währung zugeordnet werden kann. Diese Währung wird als *Transaktionswährung* bezeichnet. Mit den Mehrfachwährungsfunktionen können Benutzer finanzielle Transaktionen wie Verkaufschancen, Angebote, Aufträge und Rechnungen in mehreren Währungen ausführen. Diese Funktion bietet außerdem eine Währungsauswahl für den Endbenutzer, wenn eine finanzielle Transaktion auftritt.  
  
 Mehrere Datensätze in verschiedenen Transaktionswährungen können hinsichtlich einer einheitlichen Währung aggregiert, verglichen oder analysiert werden, indem ein Wechselkurs verwendet wird. Dies wird als *Basiswährung* bezeichnet. Sie definieren zuerst eine Basiswährung für die Organisation und definieren dann die Wechselkurse, um die Basiswährung den Transaktionswährungen zuzuordnen. Die Basiswährung ist die Währung, in der andere Währungen angeboten werden. Der Umrechnungskurs ist der Wert einer Transaktionswährung gleich einer Basiswährung.  
  
 Wenn Sie die Transaktionswährungseigenschaften verwenden, können Sie die folgenden Schritte ausführen:  
  
- Wählen Sie die Währung aus, in der Sie Verkaufschancen, Angebote, Aufträge und Rechnungen definieren und abwickeln möchten.  
  
- Definieren Sie die Währungsumrechnungskurse relativ zur Basiswährung.  
  
- Definieren Sie die Transaktionswährungen, und definieren Sie einen Wechselkurs, um die Basiswährung der Transaktionswährung zuzuordnen.  
  
- Erfassen Sie den Wert der Transaktion in der Basiswährung und in der Transaktionswährung bei allen finanziellen Transaktionen.  
  
- Definieren Sie Produktpreislisten für jede Währung.  
  
Um mehrere Währungen verwenden zu können, muss die Basiswährung für eine Organisation während der Serverinstallation und des Organisationssetups definiert werden. Nachdem die Basiswährung für eine Organisation festgelegt wurde, kann sie nicht mehr geändert werden. Dieser Wert ist im `Organization.BaseCurrencyID`-Attribut gespeichert.  
  
Transaktionswährungen werden als Teil der Systemeinstellungen definiert. Eine unbegrenzte Anzahl an Transaktionswährungen kann definiert werden. Transaktionswährungen beziehen sich auf die Basiswährung mit der Definition eines Wechselkurses.  
  
Nach der Definition von Basis- und Transaktionswährungen müssen die Preislisten definiert werden. Eine Organisation kann mehrere Preislisten haben, die in der Regel auch für einen geografischen Zielmarkt in der Landeswährung definiert werden.  
  
Alle Entitäten, die an finanziellen Transaktionen beteiligt sind, unterstützen die Transaktionswährung. Die Währung wird in der Regel von dem Konto, der Verkaufschancen usw. übernommen, kann jedoch nach Bedarf geändert werden.  
  
Sie können die Dezimalgenauigkeit für die Transaktionswährung bestimmen, indem Sie das `TransactionCurrency.CurrencyPrecision`-Attribut verwenden. Um die Quelle der Genauigkeit für die Attribute vom Typ Geld anzugeben, verwenden Sie <xref:Microsoft.Xrm.Sdk.Metadata.MoneyAttributeMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.MoneyAttributeMetadata.PrecisionSource>-. -Attribut zugeordnet ist.  
  
Alle Geldeigenschaften in einem Datensatz teilen dieselbe Transaktionswährung, siehe zum Beispiel das `Account.CreditLimit`-Attribut. Für jedes money-Attribut in einer Entität erstellt Common Data Service automatisch ein entsprechendes, schreibgeschütztes money-Attribut, das vom System berechnet wurde und als "Basis" bezeichnet wird. Dies ist ein money-Attribut, das den Wert des entsprechenden Attributs in einer Basiswährungsentsprechung speichert, siehe zum Beispiel das `Account.CreditLimit_Base`-Attribut.  
  
Die folgende Formel wird verwendet, um den Basiswert zu berechnen:  
  
```csharp  
creditlimit_base = creditlimit / exchangerate  
```  
  
Nachfolgend finden Sie die Entitäten, für die die Transaktionswährung definiert werden kann.  
  
-   Konto  
  
-   AnnualFiscalCalendar  
  
-   Kampagne  
  
-   CampaignActivity  
  
-   Mitbewerber  
  
-   Kontakt  
  
-   Vertrag  
  
-   ContractDetail  
  
-   Rabatt  
  
-   DiscountType  
  
-   FixedMonthlyFiscalCalendar  
  
-   Rechnung  
  
-   InvoiceDetail  
  
-   Lead  
  
-   Liste  
  
-   MonthlyFiscalCalendar  
  
-   Verkaufschance  
  
-   OpportunityClose  
  
-   Verkaufschance (Produkt)  
  
-   PriceLevel  
  
-   Produkt  
  
-   ProductPriceLevel  
  
-   QuarterlyFiscalCalendar  
  
-   Angebot  
  
-   QuoteDetail  
  
-   Vertriebsauftrag  
  
-   SalesOrderDetail  
  
-   SemiAnnualFiscalCalendar  
  
-   UserSettings  
  
### <a name="see-also"></a>Siehe auch  
 [TransactionCurrency-Entität](reference/entities/transactioncurrency.md)   
 [Beispiel: Abrufen von Wechselkursen](org-service/samples/retrieve-currency-exchange-rate.md)   
 [Unternehmensmanagement-Entitäten](/dynamics365/customer-engagement/developer/business-management-entities)