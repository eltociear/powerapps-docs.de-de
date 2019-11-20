Die PowerShell-Dateien für das Package Deployer-Tool sind als [NuGet-Paket](https://go.microsoft.com/fwlink/?linkid=859211) erhältlich. Um sie verwenden zu können, laden Sie sie herunter, und extrahieren Sie sie mithilfe von **nuget.exe.** auf Ihrem Computer.<br/><br/>

Laden Sie **nuget.exe** von <https://www.nuget.org/downloads> herunter, und speichern Sie die Datei beispielsweise unter **d:\\** auf Ihrem Computer. Um den Paketinhalt in einen Ordner auf dem Computer zu extrahieren, wie beispielsweise **PD-PowerShell**, führen Sie in der Eingabeaufforderung folgenden Befehl aus:<br/>

`d:\nuget install Microsoft.CrmSdk.XrmTooling.PackageDeployment.PowerShell -Version [VERSION] -O d:\PD-PowerShell`<br/><br/>
    
Nachdem Sie die PowerShell-Dateien für das Package Deployer-Tool extrahiert haben, gehen Sie zum Ordner `[ExtractedLocation]\tools`, und suchen Sie die erforderlichen Dateien. 
