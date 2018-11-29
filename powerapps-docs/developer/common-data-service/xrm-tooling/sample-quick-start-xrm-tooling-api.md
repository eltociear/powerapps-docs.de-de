---
title: 'Beispiel: Schnellstart für XRM Tooling API (Common Data Service for Apps)| Microsoft-Docs'
description: ''
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: samples
applies_to:
  - Dynamics 365 (online)
ms.assetid: 060d45bb-b7fd-48bd-ab8f-629c1b8bc1dc
caps.latest.revision: 20
author: MattB-msft
ms.author: kvivek
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-quick-start-for-xrm-tooling-api"></a>Beispiel: Schnellstart für XRM Tooling API

Das QuickStart-Beispiel ist ein verwaltetes .NET Framework-Codebeispiel, das zeigt, wie eine Verbindung zu einer Common Data Service for Apps-Instanz hergestellt wird, indem die XRM Tooling APIs verwendet werden, und wie grundlegende Erstellungs-, Aktualisierungs-, Abruf- und Löschvorgänge für eine Entität ausgeführt werden. Weitere Informationen zur XRM-Tooling finden Sie unter [Erstellen von Windows-Client-Anwendungen mithilfe der XRM-Tools](build-windows-client-applications-xrm-tools.md).

Laden Sie das Beispiel: [Arbeiten mit der XRM Tooling-API](https://code.msdn.microsoft.com/XRM-Tooling-Sample-24a5c55c) herunter.

## <a name="prerequisites"></a>Voraussetzungen

[!INCLUDE [sdk-prerequisite](../../../includes/sdk-prerequisite.md)]
  
## <a name="requirements"></a>Anforderungen

Sie müssen Zugriff auf eine CDS for Apps-Umgebung haben.

## <a name="demonstrates"></a>Demonstriert

- Der Beispielcode wird mithilfe der **WPF-Anwendung für CRM**-SDK-Vorlage erstellt, die ein allgemeines Anmeldungssteuerelement mit integrierter Unterstützung für Zwischenspeicherung und Wiederverwendung von Authentifizierungs- und Anmeldeinformationen bietet. Weitere Informationen zum allgemeinen Anmeldungssteuerelement und wie die SDK-Vorlage in Visual Studio verwendet wird, finden Sie in [Verwendung des allgemeinen XRM Tooling-Anmeldungssteuerelements](use-xrm-tooling-common-login-control-client-applications.md).  
- Zum Einrichten einer Verbindung mit CDS for Apps wird kein Hilfscode verwendet.  
- Nach der Verbindung mit CDS for Apps führt das Beispiel grundlegende Erstellungs-, Aktualisierungs-, Abruf- und Löschvorgänge an einer Account-Entität aus.  
- Speichert Benutzeranmeldeinformationen in einer Konfigurationsdatei (`Default_QuickStartXRMToolingWPFClient.exe.config`) im Ordner `c:\Users\`*`<username>`*`\AppData\Roaming\Microsoft\QuickStartXRMToolingWPFClient`, wenn das Beispiel zum ersten Mal ausgeführt wird, und fordert danach den Benutzer auf, entweder die gespeicherten Anmeldeinformationen zu verwenden oder in der Laufzeit neue anzugeben, um sich bei CDS for Apps anzumelden.  
- Generiert, wenn Probleme auftreten, die folgenden Protokolldateien, um die Problembehandlung zu unterstützen:  
- Login_ErrorLog.log: Um Anmeldungsfehler zu melden. Diese Datei ist unter `C:\Users\`*`<username>`*`\AppData\Roaming\Microsoft\QuickStartXRMToolingWPFClient` verfügbar.  
- QuickStartXRMToolingWPFClient.log: Um Betriebsfehler zu melden. Diese Datei ist am gleichen Ort verfügbar wie die ausführbare Datei, d. h. im Debuggen-Ordner Ihres Visual Studio-Projekts.  

## <a name="to-run-the-sample"></a>Um das Beispiel auszuführen

1. Laden Sie das Beispiel herunter und extrahieren Sie es.  
1. Öffnen Sie die Datei `Quick start for XRM Tooling\C#\QuickStartXRMToolingWPFClient.sln` in Visual Studio.  
2. Drücken Sie **F5**, um das Programm zu kompilieren und auszuführen.  

## <a name="example"></a>Beispiel

```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Documents;  
using System.Windows.Input;  
using System.Windows.Media;  
using System.Windows.Media.Imaging;  
using System.Windows.Navigation;  
using System.Windows.Shapes;  
  
// This namespace is automatically added for using   
// components in LoginWindow\CrmLogin.xaml (common login control).  
using QuickStartXRMToolingWPFClient.LoginWindow;  
  
// Add this namespace for performing   
// various operations in CRM.  
using Microsoft.Xrm.Tooling.Connector;  
  
namespace QuickStartXRMToolingWPFClient  
{  
    /// <summary>  
    /// Demonstrates how to do basic entity operations like create, retrieve,  
    /// update, and delete using the XRM Tooling APIs and the common login  
    /// control.</summary>  
    /// <remarks>  
    /// At run-time, you will be given the option to delete all the  
    /// database records created by this program.</remarks>  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
            btnDelete.Visibility = Visibility.Hidden;  
        }  
  
        #region Class Level Members  
  
        private CrmLogin _ctrl = null;  
        private Guid _accountId;  
  
        #endregion Class Level Members  
  
        #region How To Sample Code  
  
        /// <summary>  
        /// Connect to Microsoft CRM, and get an instance of CRMServiceClient   
        /// </summary>  
  
        private void LoginButton_Click(object sender, RoutedEventArgs e)  
        {  
            // Create an instance of the XRM Tooling common login control  
            _ctrl = new CrmLogin();  
  
            /// Wire event to the CRM sign-in response.   
            _ctrl.ConnectionToCrmCompleted += ctrl_ConnectionToCrmCompleted;  
            UpdateStatus("Initiating connection to CRM...");  
  
            /// Show the XRM Tooling common login control.   
            _ctrl.ShowDialog();  
  
            /// Validate if you are connected to CRM   
            if (_ctrl.CrmConnectionMgr != null && _ctrl.CrmConnectionMgr.CrmSvc != null && _ctrl.CrmConnectionMgr.CrmSvc.IsReady)  
            {  
                UpdateStatus("Connected to CRM! (Version: " + _ctrl.CrmConnectionMgr.CrmSvc.ConnectedOrgVersion.ToString() +   
                    "; Org: " + _ctrl.CrmConnectionMgr.CrmSvc.ConnectedOrgUniqueName.ToString() + ")");  
                UpdateStatus("***************************************");  
                UpdateStatus("Click Start to create, retrieve, update, and delete (optional) an account record.");  
                btnSignIn.IsEnabled = false;  
                btnCRUD.IsEnabled = true;  
            }  
            // If you are not connected to CRM; display the last error and last CRM excption  
            else  
            {  
                UpdateStatus("The connection to CRM failed or was cancelled by the user.");              
            }              
        }  
  
        private void btnCRUD_Click(object sender, RoutedEventArgs e)  
        {  
            // Create an account record  
            Dictionary<string, CrmDataTypeWrapper> inData = new Dictionary<string, CrmDataTypeWrapper>();  
            inData.Add("name", new CrmDataTypeWrapper("Sample Account Name", CrmFieldType.String));  
            inData.Add("address1_city", new CrmDataTypeWrapper("Redmond", CrmFieldType.String));  
            inData.Add("telephone1", new CrmDataTypeWrapper("555-0160", CrmFieldType.String));  
            _accountId = _ctrl.CrmConnectionMgr.CrmSvc.CreateNewRecord("account", inData);  
  
            // Validate if the account is created, and then retrieve it  
            if (_accountId != Guid.Empty)  
            {  
                UpdateStatus("***************************************");  
                UpdateStatus(DateTime.Now.ToString() + ": Created an account with the following" + "\n" + "details, and retrieved it:");  
                Dictionary<string, object> data = _ctrl.CrmConnectionMgr.CrmSvc.GetEntityDataById("account", _accountId, null);  
                foreach (var pair in data)  
                {  
                    if ((pair.Key == "name") || (pair.Key == "address1_city") || (pair.Key == "telephone1"))  
                    {  
                        UpdateStatus(pair.Key.ToUpper() + ": " + pair.Value);  
                    }  
                }  
                btnCRUD.IsEnabled = false;  
            }  
            else  
            {  
                UpdateStatus("***************************************");  
                UpdateStatus("Could not create the account.");  
            }  
  
            // Update the account record  
            Dictionary<string, CrmDataTypeWrapper> updateData = new Dictionary<string, CrmDataTypeWrapper>();  
            updateData.Add("name", new CrmDataTypeWrapper("Updated Sample Account Name", CrmFieldType.String));  
            updateData.Add("address1_city", new CrmDataTypeWrapper("Boston", CrmFieldType.String));  
            updateData.Add("telephone1", new CrmDataTypeWrapper("555-0161", CrmFieldType.String));   
            bool updateAccountStatus = _ctrl.CrmConnectionMgr.CrmSvc.UpdateEntity("account","accountid",_accountId,updateData);  
  
            // Validate if the the account record was updated successfully, and then display the updated information  
            if (updateAccountStatus == true)  
            {  
                UpdateStatus("***************************************");  
                UpdateStatus(DateTime.Now.ToString() + ": Updated the account details as follows:");  
                Dictionary<string, object> data = _ctrl.CrmConnectionMgr.CrmSvc.GetEntityDataById("account", _accountId, null);  
                foreach (var pair in data)  
                {  
                    if ((pair.Key == "name") || (pair.Key == "address1_city") || (pair.Key == "telephone1"))  
                    {  
                        UpdateStatus(pair.Key.ToUpper() + ": " + pair.Value);  
                    }  
                }  
            }  
            else  
            {  
                UpdateStatus("***************************************");  
                UpdateStatus("Could not update the account.");  
            }  
  
            // Prompt the user to delete the account record created in the sample  
            UpdateStatus("***************************************");  
            UpdateStatus("To delete the account record created by the sample, click Delete Record.");  
            UpdateStatus("Otherwise, click Exit to close the sample application.");  
            btnDelete.Visibility = Visibility.Visible;          
        }  
  
        // Delete the account record created in this sample.  
        private void btnDelete_Click(object sender, RoutedEventArgs e)  
        {  
            btnDelete.IsEnabled = false;  
            _ctrl.CrmConnectionMgr.CrmSvc.DeleteEntity("account", _accountId);  
            UpdateStatus("***************************************");  
            UpdateStatus(DateTime.Now.ToString() + ": Deleted the account record.");  
            UpdateStatus("Click Exit to close the sample application.");  
        }  
  
        // Exit the sample application  
        private void btnExit_Click(object sender, RoutedEventArgs e)  
        {  
            this.Close();  
        }  
  
        /// <summary>  
        /// Progressively displays the status messages about the actions  
        /// performed during the running of the sample.  
        /// <param name="updateText">Indicates the status string that needs to be   
        /// displayed to the user.</param>  
        /// </summary>  
        public void UpdateStatus(string updateText)  
        {  
            if (lblStatus.Content.ToString() != String.Empty)  
            {  
                lblStatus.Content = lblStatus.Content + "\n" + updateText;  
            }  
            else  
            {  
                lblStatus.Content = updateText;  
            }  
        }  
  
        /// <summary>  
        /// Raised when the login process is completed.  
        /// </summary>  
        private void ctrl_ConnectionToCrmCompleted(object sender, EventArgs e)  
        {  
            if (sender is CrmLogin)  
            {  
                this.Dispatcher.Invoke(() =>  
                {  
                    ((CrmLogin)sender).Close();  
                });  
            }  
        }  
    }  
    #endregion How To Sample Code  
  
}  
```

### <a name="see-also"></a>Siehe auch

[Verwenden Sie das allgemeine XRM Toolinng-Anmeldungssteuerelement](use-xrm-tooling-common-login-control-client-applications.md)<br />
[Erstellen von Windows-Client-Anwendungen mithilfe der XRM-Tools](build-windows-client-applications-xrm-tools.md)<br />
<!-- TODO:
[Tutorials for Learning About CDS for Apps Development](../tutorials-resources-sdk.md)<br /> -->
