---
ms.openlocfilehash: 41ec7aed42a950e5adf0b87783fc568dbe9d02af
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61581192"
---
Ist die Einbettung der Power BI-Kacheln und ‑Dashboards aktiviert und ein Benutzer nimmt eine derartige Einbettung vor, wird für die Authentifizierung beim Power BI-Dienst mit einer impliziten Genehmigung das [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)]-Autorisierungstoken für [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] verwendet. Damit wird Endbenutzern eine Oberfläche für einmaliges Anmelden bereitgestellt.  
  
 Ein Administrator kann die Einbettung von Power BI-Kacheln und ‑Dashboards jederzeit deaktivieren, um die Verwendung des [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]-Autorisierungstokens für die Authentifizierung beim Power BI-Dienst zu verhindern. Damit wird bewirkt, dass keine der vorhandenen Kacheln oder Dashboards für den Endbenutzer gerendert werden.  
  
 Die [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Komponente oder der Dienst, die bzw. der bei der Einbettung von Power BI-Kacheln erforderlich ist, wird im folgenden Abschnitt ausführlicher beschrieben.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
 Dieser Dienst stellt das Authentifizierungstoken zur Verfügung, das für die API‑ und UI-Authentifizierung mit dem Power BI-Dienst ausgetauscht wird.