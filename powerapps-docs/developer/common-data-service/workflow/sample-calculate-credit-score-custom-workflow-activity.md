---
title: 'Beispiel: Berechnen eines Kreditsatzes mit einer benutzerdefinierten Workflowaktivität (Common Data Service for Apps) | Microsoft Docs'
description: Die folgende Beispielworkflowaktivität berechnet den Kreditscore anhand der Sozialversicherungsnummer (SSN) und des Namens.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: samples
applies_to:
  - Dynamics 365 (online)
ms.assetid: 9cb7eb41-1a73-44a8-ae58-14120e84243f
caps.latest.revision: 19
author: JimDaly
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-calculate-a-credit-score-with-a-custom-workflow-activity"></a>Beispiel: Berechnen Sie mit einer benutzerdefinierten Workflowaktivität einen Kreditscore

Dieser Beispielcode ist für Common Data Service for Apps bestimmt. Laden Sie hier das vollständige Beispiel herunter [Benutzerdefinierte Workflowaktivitätsbeispiele](https://code.msdn.microsoft.com/Custom-Workflow-Activities-eee57285).

## <a name="prerequisites"></a>Voraussetzungen

[!INCLUDE [sdk-prerequisite](../../../includes/sdk-prerequisite.md)]
  
## <a name="requirements"></a>Anforderungen

Die folgenden Anpassungen müssen vorhanden sein, damit diese benutzerdefinierte Workflowaktivität funktioniert:  

-   Entitätsschemaname: `new_loanapplication`  
-   Attribut: `new_loanapplicationid` als Primärschlüssel  
-   Attribut: `new_creditscore` vom Typ `int` mit mindestens 0 und maximal 1000 (falls aktualisiert werden soll)  
-   Attribut: `new_loanamount` des Geld-Typs mit Standard-Minimum und Maximum.  
-   Anpassen des Formulars, um das Attribut `new_loanapplicantid` einzuschließen  
  
Die Kontaktentität muss über die folgenden Anpassungen verfügen:  
  
-   Attribut: `new_ssn` als **Einzelne Textzeile** mit einer maximalen Länge von 15  
-   1:n-Beziehung mit diesen Eigenschaften:  
    -   Schemaname der Beziehungsdefinition: `new_loanapplicant`  
    -   Anzeigename der mit der Beziehungsdefinition verknüpften Entität: Kreditwendung  
    -   Schemaname des Beziehungsnamens: `new_loanapplicantid`  
    -   Beziehungsverhaltenstyp: Referenziell  
  
## <a name="demonstrates"></a>Demonstriert

Die folgende Beispielworkflowaktivität berechnet den Kreditscore anhand der Sozialversicherungsnummer (SSN) und des Namens.  
  
## <a name="example"></a>Beispiel  

```csharp
/// <summary>
/// Calculates the credit score based on the SSN and name. 
/// </summary>
/// <remarks>
/// This depends on a custom entity called Loan Application and customizations to Contact.
/// 
/// Loan Application requires the following properties:
/// <list>
///     <item>Schema Name: new_loanapplication</item>
///     <item>Attribute: new_loanapplicationid as the primary key</item>
///     <item>Attribute: new_creditscore of type int with min of 0 and max of 1000 (if it is to be updated)</item>
///     <item>Attribute: new_loanamount of type money with default min/max</item>
///     <item>Customize the form to include the attribute new_loanapplicantid</item>
/// </list>
/// 
/// Contact Requires the following customizations
/// <list>
///     <item>Attribute: new_ssn as nvarchar with max length of 15</item>
///     <item>One-To-Many Relationship with these properties:
///         <list>
///             <item>Relationship Definition Schema Name: new_loanapplicant</item>
///             <item>Relationship Definition Related Entity Name: Loan Application</item>
///             <item>Relationship Atttribute Schema Name: new_loanapplicantid</item>
///             <item>Relationship Behavior Type: Referential</item>
///         </list>
///     </item>
/// </list>
/// 
/// The activity takes, as input, a EntityReference to the Loan Application and a boolean indicating whether new_creditscore should be updated to the credit score.
/// </remarks>
/// <exception cref=">ArgumentNullException">Thrown when LoanApplication is null</exception>
/// <exception cref=">ArgumentException">Thrown when LoanApplication is not a EntityReference to a LoanApplication entity</exception>
public sealed partial class RetrieveCreditScore : CodeActivity
{
    private const string CustomEntity = "new_loanapplication";

    protected override void Execute(CodeActivityContext executionContext)
    {
        //Check to see if the EntityReference has been set
        EntityReference loanApplication = this.LoanApplication.Get(executionContext);
        if (loanApplication == null)
        {
            throw new InvalidOperationException("Loan Application has not been specified", new ArgumentNullException("Loan Application"));
        }
        else if (loanApplication.LogicalName != CustomEntity)
        {
            throw new InvalidOperationException("Loan Application must reference a Loan Application entity",
                new ArgumentException("Loan Application must be of type Loan Application", "Loan Application"));
        }

        //Retrieve the CrmService so that we can retrieve the loan application
        IWorkflowContext context = executionContext.GetExtension<IWorkflowContext>();
        IOrganizationServiceFactory serviceFactory = executionContext.GetExtension<IOrganizationServiceFactory>();
        IOrganizationService service = serviceFactory.CreateOrganizationService(context.InitiatingUserId);

        //Retrieve the Loan Application Entity
        Entity loanEntity;
        {
            //Create a request
            RetrieveRequest retrieveRequest = new RetrieveRequest();
            retrieveRequest.ColumnSet = new ColumnSet(new string[] { "new_loanapplicationid", "new_loanapplicantid" });
            retrieveRequest.Target = loanApplication;

            //Execute the request
            RetrieveResponse retrieveResponse = (RetrieveResponse)service.Execute(retrieveRequest);

            //Retrieve the Loan Application Entity
            loanEntity = retrieveResponse.Entity as Entity;
        }

        //Retrieve the Contact Entity
        Entity contactEntity;
        {
            //Create a request
            EntityReference loanApplicantId = (EntityReference)loanEntity["new_loanapplicantid"];

            RetrieveRequest retrieveRequest = new RetrieveRequest();
            retrieveRequest.ColumnSet = new ColumnSet(new string[] { "fullname", "new_ssn", "birthdate" });
            retrieveRequest.Target = loanApplicantId;

            //Execute the request
            RetrieveResponse retrieveResponse = (RetrieveResponse)service.Execute(retrieveRequest);

            //Retrieve the Loan Application Entity
            contactEntity = retrieveResponse.Entity as Entity;
        }

        //Retrieve the needed properties
        string ssn = (string)contactEntity["new_ssn"];
        string name = (string)contactEntity[ContactAttributes.FullName];
        DateTime? birthdate = (DateTime?)contactEntity[ContactAttributes.Birthdate];
        int creditScore;

        //This is where the logic for retrieving the credit score would be inserted
        //We are simply going to return a random number
        creditScore = (new Random()).Next(0, 1000);

        //Set the credit score property
        this.CreditScore.Set(executionContext, creditScore);

        //Check to see if the credit score should be saved to the entity
        //If the value of the property has not been set or it is set to true
        if (null != this.UpdateEntity &amp;&amp; this.UpdateEntity.Get(executionContext))
        {
            //Create the entity
            Entity updateEntity = new Entity(loanApplication.LogicalName);
            updateEntity["new_loanapplicationid"] = loanEntity["new_loanapplicationid"];
            updateEntity["new_creditscore"] = this.CreditScore.Get(executionContext);

            //Update the entity
            service.Update(updateEntity);
        }
    }

    //Define the properties
    [Input("Loan Application")]
    [ReferenceTarget(CustomEntity)]
    public InArgument<EntityReference> LoanApplication { get; set; }

    [Input("Update Entity's Credit Score")]
    [Default("true")]
    public InArgument<bool> UpdateEntity { get; set; }

    [Output("Credit Score")]
    [AttributeTarget(CustomEntity, "new_creditscore")]
    public OutArgument<int> CreditScore { get; set; }
}
```
  
### <a name="see-also"></a>Siehe auch

[Workflowerweiterungen](workflow-extensions.md)<br />
[Lernprogramm: Erstellen einer Workflow-Erweiterung](tutorial-create-workflow-extension.md)<br />
[Beispiel: Eine benutzerdefinierte Workflowaktivität erstellen](sample-create-custom-workflow-activity.md)<br />
[Beispiel: Aktualisieren des nächsten Geburtstags mithilfe einer benutzerdefinierten Workflowaktivität](sample-update-next-birthday-using-custom-workflow-activity.md)