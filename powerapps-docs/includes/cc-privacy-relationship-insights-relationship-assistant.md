---
ms.openlocfilehash: 40dcde544894751da2696defc76819892659cb25
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61577531"
---
Nach dem Aktivieren des Beziehungsassistenten werden Exchange-Daten in begrenztem Umfang, wie etwa der Name und die E-Mail-Adresse eines Absenders sowie Auszüge aus dem E-Mail-Text, abgerufen (in [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] jedoch nicht gespeichert), um relevante Informationen über Ihre E-Mails anzeigen zu können. Darüber hinaus kann der Beziehungsassistent so konfiguriert werden, dass Nachrichten, Finanzinformationen und Fluginformationen durch Senden von Anforderungen an externe Komponenten wie MSN Finanzen und Bing (die nicht als Basisdienste von [!INCLUDE[pn_ms_dyn_365](pn-ms-dyn-365.md)] gelten) abgerufen werden. Administratoren können den Beziehungsassistenten aktivieren und deaktivieren, indem sie zu **Einstellungen** > **Intelligenzkonfiguration** navigieren, auf die Registerkarte **Beziehungsassistent** klicken und die entsprechende Auswahl treffen.  
  
 Die externen Komponenten in Verbindung mit dem Beziehungsassistenten werden in den folgenden Abschnitten ausführlich dargestellt.  
  
 **[!INCLUDE[pn_bing](pn-bing.md)]**  
  
 Der Beziehungsassistent verwendet [!INCLUDE[pn_bing](pn-bing.md)] für die Suche nach relevanten Neuigkeiten, die einem Benutzer angezeigt werden. Dazu werden die Kontonamen aus den [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]-Daten dieses Benutzers verwendet.  
  
 **[!INCLUDE[pn_ms_MSN_Money](pn-ms-msn-money.md)]**  
  
 Der Beziehungsassistent verwendet [!INCLUDE[pn_ms_MSN_Money](pn-ms-msn-money.md)], um einem Benutzer relevante Börseninformationen anzuzeigen. Dazu wird das Kontotickersymbol aus den [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]-Daten dieses Benutzers verwendet.