---
title: Entwicklung von IPlugin-Implementierungen als zustandslos | MicrosoftDocs
description: 'Mitglieder von Klassen, die IPlugin implementieren, sind potenziellen Thread-Sicherheitsproblemen ausgesetzt, die zu Dateninkonsistenz- oder Performanceproblemen führen können.'
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 1/15/2019
ms.author: jowells
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="develop-iplugin-implementations-as-stateless"></a>Entwicklung von IPlugin-Implementierungen als zustandslose Systeme

**Kategorie**: Design, Leistung

**Wirkungspotential**: Hoch

<a name='symptoms'></a>

## <a name="symptoms"></a>Symptome

Mitglieder von Klassen, die die <xref href="Microsoft.Xrm.Sdk.IPlugin?text=IPlugin interface" /> implementieren, sind potenziellen Thread-Sicherheitsproblemen ausgesetzt, die zu folgenden führen können:

- Dateninkonsistenzen
- Langsamere Plugin-Ausführungen

<a name='guidance'></a>

## <a name="guidance"></a>Anleitung

Verwenden Sie bei der Implementierung von <xref:Microsoft.Xrm.Sdk.IPlugin> keine Memberfelder und -eigenschaften und schreiben Sie die Methode <xref:Microsoft.Xrm.Sdk.IPlugin.Execute*> als zustandslose Operation.  Alle Informationen über den Zustand pro Aufruf sollten nur über den Ausführungskontext abgerufen werden.  Versuchen Sie nicht, Ausführungszustandsdaten in Elementfeldern oder Eigenschaften zu speichern, die während des aktuellen oder nächsten Plugin-Aufrufs verwendet werden, es sei denn, diese Daten wurden aus dem Konfigurationsparameter gewonnen, der dem überladenen Konstruktor zur Verfügung gestellt wurde.

Leserechte, statische und konstante Elemente sind von Natur aus threadsicher und können auch innerhalb einer Plugin-Klasse zuverlässig verwendet werden. Im Folgenden finden Sie einige Beispiele, wie Sie threadsichere Plug-Ins pflegen können:

- Konstante Feldmitglieder

    ```csharp
    public class Valid_ClassConstantMember : IPlugin
    {
        public const string validConstantMember = "Plugin registration not valid for {0} message.";

        public void Execute(IServiceProvider serviceProvider)
        {
            var context = (IPluginExecutionContext)serviceProvider.GetService(typeof(IPluginExecutionContext));

            if (context.MessageName.ToLower() != "create")
                throw new InvalidPluginExecutionException(String.Format(Valid_ClassConstantMember.validConstantMember, context.MessageName));
        }
    }
    ```

- Speichern von Konfigurationsdaten, die im Plugin-Klassenkonstruktor zugewiesen oder gesetzt wurden.
    ```csharp
    public class Valid_ClassFieldConfigMember : IPlugin
    {
        private string validConfigField;

        public Valid_ClassFieldConfigMember(string unsecure, string secure)
        {
            this.validConfigField = !String.IsNullOrEmpty(secure)
                ? unsecure
                : secure;
        }

        public void Execute(IServiceProvider serviceProvider)
        {
            if (!String.IsNullOrEmpty(this.validConfigField))
            {
                var message = ValidHelperMethod();
            }
        }

        private string ValidHelperMethod()
        {
            return String.Format("{0} is the config value.", this.validConfigField);
        }
    }
    ```

- Zustandslose Methodenimplementierung

    ```csharp
    public class Valid_ClassStatelessMethodMember : IPlugin
    {
        public void Execute(IServiceProvider serviceProvider)
        {
            var context = (IPluginExecutionContext)serviceProvider.GetService(typeof(IPluginExecutionContext));
    
            if (ValidMemberMethod(context))
            {
                //Then continue with execution
            }
        }
    
        private bool ValidMemberMethod(IPluginExecutionContext context)
        {
            if (context.MessageName.ToLower() == "create")
                return true;
            else
                return false;
        }
    }
    ```

<a name='problem'></a>

## <a name="problematic-patterns"></a>Problematische Muster

> [!WARNING]
> Diese Muster sollten vermieden werden.

- Zuweisung von Feldmitgliedern der Plugin-Klasse während der Ausführung des Plugins
 
    ```csharp
    public class Violation_ClassAssignFieldMember : IPlugin
    {
        //The instance member used in multiple violation patterns
        internal IOrganizationService service = null;
        internal IPluginExecutionContext context = null;
    
        public void Execute(IServiceProvider serviceProvider)
        {
            this.context = (IPluginExecutionContext)serviceProvider.GetService(typeof(IPluginExecutionContext));
            var factory = (IOrganizationServiceFactory)serviceProvider.GetService(typeof(IOrganizationServiceFactory));
    
            //The violation
            this.service = factory.CreateOrganizationService(this.context.UserId);
    
            //Invoke another violation in method member
            AccessViolationProperties();
        }
    
        private void AccessViolationProperties()
        {
            //Accessing the context and service fields exposes this IPlugin implementation to thread-safety issues
            var entity = new Entity("task");
            entity["regardingid"] = new EntityReference(this.context.PrimaryEntityName, this.context.PrimaryEntityId);
    
            var id = this.service.Create(entity);
        }
    }
    ```

- Einstellen des Eigenschaftselements der Plugin-Klasse während der Ausführung des Plugins

    ```csharp
    public class Violation_ClassAssignPropertyMember : IPlugin
    {
        //The instance member used in multiple violation patterns
        internal IOrganizationService Service { get; set; }
        internal IPluginExecutionContext Context { get; set; }
    
        public void Execute(IServiceProvider serviceProvider)
        {
            this.Context = (IPluginExecutionContext)serviceProvider.GetService(typeof(IPluginExecutionContext));
            var factory = (IOrganizationServiceFactory)serviceProvider.GetService(typeof(IOrganizationServiceFactory));
    
            //The violation
            this.Service = factory.CreateOrganizationService(context.UserId);
    
            //Invoke another violation in method member
            AccessViolationProperties();
        }
    
        private void AccessViolationProperties()
        {
            //Accessing the Context and Service properties exposes this IPlugin implementation to thread-safety issues
            var entity = new Entity("task");
            entity["regardingid"] = new EntityReference(this.Context.PrimaryEntityName, this.Context.PrimaryEntityId);
    
            var id = this.Service.Create(entity);
        }
    }
    ```

<a name='additional'></a>

## <a name="additional-information"></a>Weitere Informationen

Nachdem Common Data Services die Plugin-Klasse instanziiert hat, speichert die Plattform diese Plugin-Instanz aus Performancegründen zwischen. Die Zeitspanne, in der eine Plug-Instanz im Cache gehalten wird, wird von der Plattform verwaltet.  Bestimmte Vorgänge, wie das Ändern der Registrierungseigenschaften eines Plug-Ins, lösen eine Benachrichtigung an die Plattform aus, um den Cache zu aktualisieren.  In diesen Szenarien wird das Plug-in neu initialisiert.

Da die Plattform Plugin-Klasseninstanzen zwischenspeichert, wird der Konstruktor nicht bei jedem Aufruf der Plugin-Ausführung aufgerufen.  Aus diesem Grund sollten IPlugin-Implementierungen nicht vom Zeitpunkt der Operationen im Konstruktor abhängen, abgesehen vom Erhalten statischer Konfigurationsdaten. 

Ein weiterer Grund, warum IPlugins zustandslos sein sollten, ist, dass mehrere System-Threads die gleiche, gemeinsam genutzte Plugin-Instanz gleichzeitig ausführen können.  Dadurch werden Mitglieder von Klassen, die das IPlugin implementieren, für potenzielle Thread-Sicherheitsprobleme geöffnet, die zu Dateninkonsistenz- oder Performanceproblemen führen können.

<a name='seealso'></a>

### <a name="see-also"></a>Siehe auch

[Schreiben eines Plug-Ins](../../write-plug-in.md)<br />
[CRM Team Blog: Thread-Sicherheit in Plug-Ins](http://blogs.msdn.com/b/crm/archive/2008/11/18/member-static-variable-and-thread-safety-in-plug-in-for-crm-4-0.aspx)<br />