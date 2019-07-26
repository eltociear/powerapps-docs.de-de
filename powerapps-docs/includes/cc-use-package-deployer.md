---
ms.openlocfilehash: a108a9ee6f9033851b2f55beb071a1e7cae254dd
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2019
ms.locfileid: "67224242"
---
Das Package Deployer-Tool ist als [NuGet-Paket](https://go.microsoft.com/fwlink/?linkid=859205) erhältlich. Um das Tool verwenden zu können, laden Sie es herunter, und extrahieren Sie es mithilfe von **nuget.exe** auf Ihrem Computer.<br/><br/>

Laden Sie **nuget.exe** von <https://www.nuget.org/downloads> herunter, und speichern Sie die Datei beispielsweise unter **d:\\** auf Ihrem Computer. Um den Paketinhalt in einen Ordner auf dem Computer zu extrahieren, wie beispielsweise **PD**, führen Sie in der Eingabeaufforderung folgenden Befehl aus:<br/>

`d:\nuget install Microsoft.CrmSdk.XrmTooling.PackageDeployment.Wpf -Version [VERSION] -O d:\PD`<br/><br/>
    
Nachdem Sie das Package Deployer-Tool extrahiert haben, suchen Sie im Ordner `[ExtractedLocation]\tools` nach der Datei **PackageDeployer.exe**. 
