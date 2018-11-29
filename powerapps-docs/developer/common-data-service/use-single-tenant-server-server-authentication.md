---
title: Verwenden der Einzel-Mandanten-Server-zu-Server-Authentifizierung (Common Data Service für Apps) | Microsoft Docs
description: <Description>
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: paulliew
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-single-tenant-server-to-server-authentication"></a>Verwenden der Einzel-Mandanten-Server-zu-Server-Authentifizierung


Die Einzel-Mandanten-Server-zu-Server-Authentifizierung wird normalerweise bei Unternehmensorganisationen verwendet, die mehrere Common Data Service (CDS) für Apps-Umgebungen haben und die Active Directory Federation Services (AD FS) für die Authentifizierung verwenden. Allerdings kann es auch von Umgebungen angewendet werden, wenn die Anwendung nicht an andere Umgebungen verteilt wird.  
  
 Eine Firma kann eine Webanwendung oder einen Service erstellen, um alle CDS für Apps-Umgebungen für den einzelnen Mandanten zu verbinden.  
  
## <a name="differences-from-multi-tenant-scenario"></a>Unterschiede von mehrinstanzenfähigen Szenarien  
 Eine Webanwendung oder einen Service für eine Einzelmandanten-Server-zu-Server-Authentifizierung zu erstellen ist gleich wie jene, die für eine mehrinstanzenfähige Organisation verwendet wird, aber es gibt einige wichtige Unterschiede.  
  
-   Da sich alle Organisationen im gleichen Mandanten befinden, muss ein Mandantenadministrator keine Übereinstimmung erreichen. Die Anwendung ist bereits auf dem Mandanten registriert.  
  
-   Wenn Sie es bevorzugen, haben die Möglichkeit, anstelle von Schlüsseln Zertifikate zu verwenden.  
  
### <a name="see-also"></a>Siehe auch  
 [Verwenden Sie mehrinstanzenfähige Server-zu-Server-Authentifizierung](use-multi-tenant-server-server-authentication.md)   
 [Erstellen von Webanwendungen mit Server-to-Server-Authentifizierung (S2S)](build-web-applications-server-server-s2s-authentication.md)

<!--

 Can this scenario be hightlighted here: https://crmtipoftheday.com/767/server-to-server-authentication-is-here/

-->