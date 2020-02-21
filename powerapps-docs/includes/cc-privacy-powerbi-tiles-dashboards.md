---
ms.openlocfilehash: 162e914a6753e9fd95a8ec57857c280469308a68
ms.sourcegitcommit: 9576b34403634a8e960eb5f8e320a14c4a03746c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2019
ms.locfileid: "72517334"
---
Wenn die Einbettung von Power BI-Kacheln und -Dashboards aktiviert ist und ein Benutzer eine derartige Einbettung vornimmt, wird für die Authentifizierung beim Power BI-Dienst mit einer impliziten Genehmigung das Benutzerautorisierungstoken [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] für Common Data Service verwendet, sodass sich der Endbenutzer komfortabel anmelden kann (einmaliges Anmelden).  
  
 Ein Administrator kann die Einbettung von Power BI-Kacheln und ‑Dashboards jederzeit deaktivieren, um die Verwendung des [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]-Autorisierungstokens für die Authentifizierung beim Power BI-Dienst zu verhindern. Damit wird bewirkt, dass keine der vorhandenen Kacheln oder Dashboards für den Endbenutzer gerendert werden.  
  
 Die [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Komponente oder der Dienst, die bzw. der bei der Einbettung von Power BI-Kacheln erforderlich ist, wird im folgenden Abschnitt ausführlicher beschrieben.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
 Dieser Dienst stellt das Authentifizierungstoken zur Verfügung, das für die API‑ und UI-Authentifizierung mit dem Power BI-Dienst ausgetauscht wird.
