---
ms.openlocfilehash: 215a6d9fb0890bd6d93843b0b649ada4203e5600
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2019
ms.locfileid: "67224201"
---
Die PowerShell-Dateien für das Package Deployer-Tool sind als [NuGet-Paket](https://go.microsoft.com/fwlink/?linkid=859211) erhältlich. Um die Dateien verwenden zu können, laden Sie sie herunter, und extrahieren Sie sie mithilfe von **nuget.exe** auf Ihrem Computer.<br/><br/>

Laden Sie **nuget.exe** von <https://www.nuget.org/downloads> herunter, und speichern Sie die Datei beispielsweise unter **d:\\** auf Ihrem Computer. Um den Paketinhalt in einen Ordner auf dem Computer zu extrahieren, wie beispielsweise **PD-PowerShell**, führen Sie in der Eingabeaufforderung folgenden Befehl aus:<br/>

`d:\nuget install Microsoft.CrmSdk.XrmTooling.PackageDeployment.PowerShell -Version [VERSION] -O d:\PD-PowerShell`<br/><br/>
    
Nachdem Sie die PowerShell-Dateien für das Package Deployer-Tool extrahiert haben, suchen Sie im Ordner `[ExtractedLocation]\tools` nach den erforderlichen Dateien. 
