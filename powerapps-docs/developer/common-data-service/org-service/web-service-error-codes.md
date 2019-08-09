---
title: Webdienst-Fehlercodes (Common Data Service) | Microsoft Docs
description: 'In diesem Thema werden die Fehlercodes aufgeführt, die möglicherweise auftreten können, wenn Sie den Code debuggen. '
ms.custom: ''
ms.date: 05/09/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="web-service-error-codes"></a>Webdienst-Fehlercodes

In diesem Thema werden die Fehlercodes aufgeführt, die möglicherweise auftreten können, wenn Sie den Code debuggen.

<a name="BKMK_CRMErrors"></a>   

## <a name="common-data-service-errors"></a>Common Data Service-Fehler 

 Die folgende Liste enthält die Fehlercodes, die in Common Data Service verwendet werden. Weitere Informationen finden Sie unter [Behandlung von Ausnahmen in Ihrem Code](handle-exceptions-code.md).  

> [!div class="mx-tdBreakAll"]
>
> |Fehler|Meldung|
> |---|---|
> |**Name**:<br />AccessDenied<br />**Hex**:<br />80048405<br />**Nummer**:<br />-2147187707|Zugriff wurde verweigert.|
> |**Name**:<br />AccessDeniedSharePointRecord<br />**Hex**:<br />80060904<br />**Nummer**:<br />-2147088124|Zugriff auf SharePoint-Datensatz in Dynamics 365 verweigert.|
> |**Name**:<br />AccessTokenExpired<br />**Hex**:<br />8005F101<br />**Nummer**:<br />-2147094271|Die angeforderte Ressource erfordert Authentifizierung.|
> |**Name**:<br />AccountDoesNotExist<br />**Hex**:<br />80040502<br />**Nummer**:<br />-2147220222|Firma ist nicht vorhanden.|
> |**Name**:<br />AccountLoopBeingCreated<br />**Hex**:<br />80040507<br />**Nummer**:<br />-2147220217|Durch das Erstellen dieser übergeordneten Zuordnung würde eine Schleife in der Hierarchie „Firmen” erstellt werden.|
> |**Name**:<br />AccountLoopExists<br />**Hex**:<br />80040506<br />**Nummer**:<br />-2147220218|Schleife ist in der Firmenhierarchie vorhanden.|
> |**Name**:<br />ActionCardDisabledError<br />**Hex**:<br />80071100<br />**Nummer**:<br />-2147020544|Das Feature Aktionskarte ist nicht aktiviert.|
> |**Name**:<br />ActionCardInvalidStateCodeException<br />**Hex**:<br />80071103<br />**Nummer**:<br />-2147020541|In dem Ausdruck wurde ein ungültiger Statusausdruck übergeben.|
> |**Name**:<br />ActionStepInvalidPipelineStageid<br />**Hex**:<br />8006040e<br />**Nummer**:<br />-2147089394|ActionStep verweist auf ungültige Pipeline-Phasen-Id.|
> |**Name**:<br />ActionStepInvalidProcessAction<br />**Hex**:<br />8006041c<br />**Nummer**:<br />-2147089380|ActionStep {0} verweist auf ungültige Prozessaktion {1}.|
> |**Name**:<br />ActionStepInvalidProcessid<br />**Hex**:<br />8006040d<br />**Nummer**:<br />-2147089395|ActionStep verweist auf ungültige Prozess-Id.|
> |**Name**:<br />ActionStepInvalidStageid<br />**Hex**:<br />8006040c<br />**Nummer**:<br />-2147089396|ActionStep verweist auf ungültige Phasen-Id.|
> |**Name**:<br />ActionSupportNotEnabled<br />**Hex**:<br />80060382<br />**Nummer**:<br />-2147089534| Geschäftsprozesse, die eine „Funktionsstufe” umfassen, können nicht exportiert werden, weil die Unterstützung der „Funktionsstufe” immer noch eine Funktion von „Public Preview” ist und aktuell ist sie für diese Organisation nicht aktiviert.|
> |**Name**:<br />ActivePropertyValidationFailed<br />**Hex**:<br />80061001<br />**Nummer**:<br />-2147086335|Sie können keine Eigenschaftinstanz für eine inaktive Eigenschaft erstellen.|
> |**Name**:<br />ActiveQueueItemAlreadyExists<br />**Hex**:<br />80040526<br />**Nummer**:<br />-2147220186|Ein aktives Warteschlangenelement ist bereits für das bestimmte Objekt vorhanden. Es kann höchstens ein aktives Warteschlangenelement für dieses Objekt erstellt werden.|
> |**Name**:<br />ActiveSlaCannotEdit<br />**Hex**:<br />8004F871<br />**Nummer**:<br />-2147157903|Sie können ein aktives SLA nicht bearbeiten. Deaktivieren Sie die SLA und versuchen Sie erneut, sie zu bearbeiten.|
> |**Name**:<br />ActiveStageIdDoesNotMatchLastStageInTraversedPath<br />**Hex**:<br />80060455<br />**Nummer**:<br />-2147089323|Aktive Phasen-ID „{0}” entspricht nicht der letzten Phasen-ID im zurückgelegten Pfad „{1}”. Wenden Sie sich an Ihren Systemadministrator.|
> |**Name**:<br />ActiveStageIDIsNull<br />**Hex**:<br />80060449<br />**Nummer**:<br />-2147089335|Fehler beim Aktualisieren des Geschäftsprozesses: Aktive Phasen-ID darf nicht leer sein.|
> |**Name**:<br />ActiveStageIsNotOnLeadEntity<br />**Hex**:<br />80100002<br />**Nummer**:<br />-2146435070|Aktive Phase ist nicht in der Entität „Lead” enthalten.|
> |**Name**:<br />ActivityAnalysisOrganizationUpdateError<br />**Hex**:<br />80044275<br />**Nummer**:<br />-2147204491|Beziehungsanalyse-Organisation kann nur aktiviert werden, wenn die Beziehungsanalyselösung installiert ist.|
> |**Name**:<br />ActivityCannotHaveRelatedActivities<br />**Hex**:<br />8004F121<br />**Nummer**:<br />-2147159775|Eine als Aktivität definierte benutzerdefinierte Entität darf keine Beziehung zu Aktivitäten haben.|
> |**Name**:<br />ActivityEntityCannotBeActivityParty<br />**Hex**:<br />80048501<br />**Nummer**:<br />-2147187455|Ein Aktivitätsentität kann nicht auch eine Aktivitätspartei sein|
> |**Name**:<br />ActivityInvalidObjectTypeCode<br />**Hex**:<br />80043513<br />**Nummer**:<br />-2147207917|Ein ungültiger Typcode wurde von der auslösenden Methode angegeben|
> |**Name**:<br />ActivityInvalidSessionToken<br />**Hex**:<br />80043512<br />**Nummer**:<br />-2147207918|Ein ungültiges Sitzungstoken wurde an die auslösende Methode übergeben|
> |**Name**:<br />ActivityMetadataUpdate<br />**Hex**:<br />8004F126<br />**Nummer**:<br />-2147159770|Metadaten, die für Aktivität angegeben wurden, sind ungültig.|
> |**Name**:<br />ActivityMustHaveRelatedNotes<br />**Hex**:<br />8004F123<br />**Nummer**:<br />-2147159773|Eine als Aktivität definierte benutzerdefinierte Entität muss standardmäßig eine Beziehung mit Notizen haben.|
> |**Name**:<br />ActivityPartyObjectTypeNotAllowed<br />**Hex**:<br />80043506<br />**Nummer**:<br />-2147207930|Eine Aktivitätspartei des angegebenen Objekttyps kann nicht erstellt werden.|
> |**Name**:<br />AdminProfileCannotBeEditedOrDeleted<br />**Hex**:<br />8004F50C<br />**Nummer**:<br />-2147158772|Das Sicherheitsprofil für das Systemadministratorfeld kann nicht geändert oder gelöscht werden.|
> |**Name**:<br />AdvancedSimilarityAzureSearchUnexpectedError<br />**Hex**:<br />80061696<br />**Nummer**:<br />-2147084650|Während der Suche ist ein unerwarteter Fehler aufgetreten. Versuchen Sie es später noch einmal.|
> |**Name**:<br />AggregateInnerQuery<br />**Hex**:<br />8004D2B1<br />**Nummer**:<br />-2147167567|Die innere Abfrage darf keine Aggregatabfrage sein.|
> |**Name**:<br />AggregateQueryRecordLimitExceeded<br />**Hex**:<br />8004E023<br />**Nummer**:<br />-2147164125|Maximalanzahl an Datensätzen ist überschritten. Reduzieren Sie die Anzahl der Datensätze.|
> |**Name**:<br />AlreadyLinkedToAnotherAttribute<br />**Hex**:<br />8004F0FE<br />**Nummer**:<br />-2147159810|Angegebenes verknüpftes Attribut ist bereits mit einem anderen Attribut verknüpft.|
> |**Name**:<br />AppConfigFeatureNotEnabled<br />**Hex**:<br />80072200<br />**Nummer**:<br />-2147016192|Die In-App-Anpassungs-App-Konfigurationsfunktion ist nicht aktiviert.|
> |**Name**:<br />ApplicationMetadataConverterFailed<br />**Hex**:<br />8005F231<br />**Nummer**:<br />-2147093967|Leider ist ein Fehler aufgetreten. Versuchen Sie es noch einmal oder starten Sie die App neu.|
> |**Name**:<br />ApplicationMetadatadaCreateFailed<br />**Hex**:<br />8005F233<br />**Nummer**:<br />-2147093965|Leider ist ein Fehler aufgetreten. Versuchen Sie es noch einmal oder starten Sie die App neu.|
> |**Name**:<br />ApplicationMetadatadaNullData<br />**Hex**:<br />8005F232<br />**Nummer**:<br />-2147093966|Leider ist ein Fehler aufgetreten. Versuchen Sie es noch einmal oder starten Sie die App neu.|
> |**Name**:<br />ApplicationMetadatadaUpdateFailed<br />**Hex**:<br />8005F234<br />**Nummer**:<br />-2147093964|Leider ist ein Fehler aufgetreten. Versuchen Sie es noch einmal oder starten Sie die App neu.|
> |**Name**:<br />ApplicationMetadataFailedWithContinue<br />**Hex**:<br />8005F241<br />**Nummer**:<br />-2147093951|Es gab Probleme mit den Serverkonfigurationsänderungen.  Die Anwendung kann zwar von den Benutzern weiterhin verwendet werden, unter Umständen treten jedoch Probleme auf. Wenden Sie sich an den Dynamics 365 -Administrator, und teilen Sie ihm die unter "Weitere Informationen" angegebenen Informationen mit.|
> |**Name**:<br />ApplicationMetadataGetPreviewMetadataUnknownError<br />**Hex**:<br />8005F230<br />**Nummer**:<br />-2147093968|Leider ist ein Fehler aufgetreten. Versuchen Sie es noch einmal oder starten Sie die App neu.|
> |**Name**:<br />ApplicationMetadataPrepareCustomizationsAppLock<br />**Hex**:<br />8005F237<br />**Nummer**:<br />-2147093961|Es trafen einige Probleme auf, als wir versuchten, die Anpassungen für Ihre Benutzer vorzubereiten. Benutzer in einigen Clients ist es nicht möglich, Anpassungsupdates herunterzuladen, bis dieses Problem gelöst ist.|
> |**Name**:<br />ApplicationMetadataPrepareCustomizationsRetrieverError<br />**Hex**:<br />8005F235<br />**Nummer**:<br />-2147093963|Es gab Probleme mit den Serverkonfigurationsänderungen.  Die Anwendung kann zwar von den Benutzern weiterhin verwendet werden, unter Umständen treten jedoch Probleme auf.|
> |**Name**:<br />ApplicationMetadataPrepareCustomizationsTimeout<br />**Hex**:<br />8005F236<br />**Nummer**:<br />-2147093962|Leider konnten Ihre Clientanpassungsänderungen nicht verarbeitet werden.  Dies ist unter Umständen aufgrund zu vielee Entitäten, die für Benutzer aktiviert werden, oder der Anzahl der aktivierten Sprachen.  Benutzer erhalten keine Anpassungen, bis dieses Problem gelöst ist.|
> |**Name**:<br />ApplicationMetadataPrepareCustomizationsUnknownError<br />**Hex**:<br />8005F226<br />**Nummer**:<br />-2147093978|Leider ist ein Fehler aufgetreten. Versuchen Sie es noch einmal oder starten Sie die App neu.|
> |**Name**:<br />ApplicationMetadataRetrieveUnknownError<br />**Hex**:<br />8005F229<br />**Nummer**:<br />-2147093975|Leider ist ein Fehler aufgetreten. Versuchen Sie es noch einmal oder starten Sie die App neu.|
> |**Name**:<br />ApplicationMetadataRetrieveUserContextUnknownError<br />**Hex**:<br />8005F227<br />**Nummer**:<br />-2147093977|Leider ist ein Fehler aufgetreten. Versuchen Sie es noch einmal oder starten Sie die App neu.|
> |**Name**:<br />ApplicationMetadataSyncAppLock<br />**Hex**:<br />8005F244<br />**Nummer**:<br />-2147093948|Leider ist Ihr Server möglicherweise ausgelastet, sodass Konfigurationen gegenwärtig nicht heruntergeladen werden können. Änderungen sollten in ein paar Minuten verfügbar werden.  Warten Sie einige Minuten und melden Sie sich noch einmal.|
> |**Name**:<br />ApplicationMetadataSyncAppLockWithContinue<br />**Hex**:<br />8005F245<br />**Nummer**:<br />-2147093947|Leider ist Ihr Server möglicherweise ausgelastet, sodass Konfigurationsänderungen gegenwärtig nicht heruntergeladen werden können. Änderungen sollten in ein paar Minuten verfügbar werden.  In der Zwischenzeit können Sie die App weiterhin verwenden, und Sie werden später erinnert, die Änderungen herunterzuladen. Oder, können einige Minuten warten, die App neu starten und die Eingabeaufforderung akzeptieren, um den Vorgang zu wiederholen.|
> |**Name**:<br />ApplicationMetadataSyncFailed<br />**Hex**:<br />8005F240<br />**Nummer**:<br />-2147093952|Es gab Probleme mit den Serverkonfigurationsänderungen.  Wir können keine Datensätze für die Anwendung laden, wenden sich an Ihren Dynamics 365 Administrator.|
> |**Name**:<br />ApplicationMetadataSyncTimeout<br />**Hex**:<br />8005F242<br />**Nummer**:<br />-2147093950|Leider konnten Ihre Serverkonfigurationsänderungen nicht heruntergeladen werden.  Das ist möglicherweise aufgrund einer zu langsamen Verbindung oder aufgrund vieler Entitäten, die für Mobile verwenden.  Überprüfen Sie Ihre Verbindung und versuchen Sie es erneut.  Falls das Problem weiterhin besteht, wenden Sie sich an Ihren Dynamics 365-Administrator.|
> |**Name**:<br />ApplicationMetadataSyncTimeoutWithContinue<br />**Hex**:<br />8005F243<br />**Nummer**:<br />-2147093949|Leider konnten Ihre Serverkonfigurationsänderungen nicht heruntergeladen werden.  Das ist möglicherweise aufgrund einer zu langsamen Verbindung oder aufgrund vieler Entitäten, die für Mobile verwenden.  Überprüfen Sie Ihre Verbindung und versuchen Sie es erneut. Sie können den Vorgang fortsetzen, um der App mit der älteren Konfiguration  verwenden, führt aber möglicherweise zu Probleme beim Speichern.  Falls das Problem weiterhin besteht, wenden Sie sich an Ihren Dynamics 365-Administrator.|
> |**Name**:<br />ApplicationMetadataSyncUnknownError<br />**Hex**:<br />8005F228<br />**Nummer**:<br />-2147093976|Leider ist ein Fehler aufgetreten. Versuchen Sie es noch einmal oder starten Sie die App neu.|
> |**Name**:<br />ApplicationMetadataUserValidationUnknownError<br />**Hex**:<br />8005F225<br />**Nummer**:<br />-2147093979|Leider ist ein Fehler aufgetreten. Versuchen Sie es noch einmal oder starten Sie die App neu.|
> |**Name**:<br />ApplicationNotRegisteredWithDeployment<br />**Hex**:<br />80041d49<br />**Nummer**:<br />-2147214007|Anwendung muss auf Bereitstellungsebene registriert und aktiviert werden, bevor sie für die Organisation erstellt werden kann|
> |**Name**:<br />ApplicationProfileMustContainEntity<br />**Hex**:<br />80071131<br />**Nummer**:<br />-2147020495|Das Anwendungsprofil muss mindestens eine Entität enthalten.|
> |**Name**:<br />ApplicationUserCannotBeUpdated<br />**Hex**:<br />80041d48<br />**Nummer**:<br />-2147214008|Der Benutzer, der einen OAuth-Anwendung darstellt, kann nicht aktualisiert werden|
> |**Name**:<br />AppLockTimeout<br />**Hex**:<br />8004Ed47<br />**Nummer**:<br />-2147160761|Zeit lief ab, bevor applock abgerufen werden kann.|
> |**Name**:<br />ApplyActiveSLAOnly<br />**Hex**:<br />80055001<br />**Nummer**:<br />-2147135487|Sie können nur aktive Vereinbarungen zum Servicelevel (Service Level Agreements, SLAs) auf Fälle anwenden.|
> |**Name**:<br />AppModuleComponentEntityMustHaveFormOrView<br />**Hex**:<br />80050115<br />**Nummer**:<br />-2147155691|Die Entität "{0}"  muss ein Formular oder Anzeige in der App verfügen.|
> |**Name**:<br />AppModuleFeatureNotEnabled<br />**Hex**:<br />80050117<br />**Nummer**:<br />-2147155689|Die Funktionalität ist nicht für die Organisation aktiviert.|
> |**Name**:<br />AppModuleMustHaveOnlyValidClientEntity<br />**Hex**:<br />8005012A<br />**Nummer**:<br />-2147155670|Die Entität „{0}” ist für den ausgewählten Client nicht gültig und wird zur Laufzeit nicht angezeigt.|
> |**Name**:<br />AppModuleNotContainMOCAEnabledEntity<br />**Hex**:<br />80050118<br />**Nummer**:<br />-2147155688|App-Modul mit MOCA als unterstützter Client sollte mindestens eine MOCA-fähige Entität enthalten|
> |**Name**:<br />AppModuleNotReferEntity<br />**Hex**:<br />8005011D<br />**Nummer**:<br />-2147155683|App-Modul verweist nicht auf mindestens eine Entität|
> |**Name**:<br />AppModulesImportError<br />**Hex**:<br />80050123<br />**Nummer**:<br />-2147155677|Fehler beim Importieren von App-Modulen|
> |**Name**:<br />AppModuleWithClientExists<br />**Hex**:<br />80050127<br />**Nummer**:<br />-2147155673|Die App konnte nicht erstellt werden. Es ist bereits eine App für diesen Client-Typen vorhanden.|
> |**Name**:<br />AppointmentDeleted<br />**Hex**:<br />8004E106<br />**Nummer**:<br />-2147163898|Die Terminentitätsinstanz wurde bereits gelöscht.|
> |**Name**:<br />AppointmentScheduleNotSet<br />**Hex**:<br />80040275<br />**Nummer**:<br />-2147220875|Geplantes Ende und geplanter Beginn müssen für Termine festgelegt werde, um sie mit Outlook zu synchronisieren.|
> |**Name**:<br />ArgumentDirectionMismatch<br />**Hex**:<br />80060388<br />**Nummer**:<br />-2147089528|Es liegt ein Richtungskonflikt für das Argument {0} vor.|
> |**Name**:<br />ArgumentTypeMismatch<br />**Hex**:<br />80060387<br />**Nummer**:<br />-2147089529|Es liegt ein Typenkonflikt für das Argument {0} vor.|
> |**Name**:<br />ArrayMappingFoundForSingletonParameter<br />**Hex**:<br />8004037f<br />**Nummer**:<br />-2147220609|Eine Arraytransformationsparameterzuordnung ist für einen einzelnen Parameter definiert.|
> |**Name**:<br />ArticleIsPublished<br />**Hex**:<br />800404fe<br />**Nummer**:<br />-2147220226|Die Rechnung kann nicht aktualisiert oder storniert werden, da sie sich nicht im veröffentlichten Status befindet.|
> |**Name**:<br />AssociateProductFailureDifferentUom<br />**Hex**:<br />80061040<br />**Nummer**:<br />-2147086272|Das Produkt kann dem Paket nicht hinzugefügt werden. Sie müssen eine Produkteinheit verwenden, die zur Einheitengruppe des Produkts gehört.|
> |**Name**:<br />AssociationRoleOrdinalInvalid<br />**Hex**:<br />80048468<br />**Nummer**:<br />-2147187608|Die Zuordnungsrollen-Ordnungszahl ist ungültig - sie muss 1 oder sein.|
> |**Name**:<br />AsyncCommunicationError<br />**Hex**:<br />80044307<br />**Nummer**:<br />-2147204345|Ein Kommunikationsfehler ist beim Verarbeiten des Async-Vorgangs aufgetreten.|
> |**Name**:<br />AsyncNetworkError<br />**Hex**:<br />80044306<br />**Nummer**:<br />-2147204346|Ein Fehler beim Zugriff auf das Netzwerk ist aufgetreten.|
> |**Name**:<br />AsyncOperationCannotCancel<br />**Hex**:<br />80044F00<br />**Nummer**:<br />-2147201280|Der ausgewählte Systemauftrag kann nicht abgebrochen werden.|
> |**Name**:<br />AsyncOperationCannotDeleteUnlessCompleted<br />**Hex**:<br />8004416a<br />**Nummer**:<br />-2147204758|Der asynchrone Vorgang kann nicht gelöscht werden, bis den Status "Abgeschlossen" annimmt.|
> |**Name**:<br />AsyncOperationCannotPause<br />**Hex**:<br />80044F01<br />**Nummer**:<br />-2147201279|Der ausgewählte Systemauftrag kann nicht unterbrochen werden.|
> |**Name**:<br />AsyncOperationCannotUpdateNonrecurring<br />**Hex**:<br />80044168<br />**Nummer**:<br />-2147204760|Kann Serienmuster für einen Auftrag, der nicht wiederholt wird, nicht aktualisieren.|
> |**Name**:<br />AsyncOperationCannotUpdateRecurring<br />**Hex**:<br />80044169<br />**Nummer**:<br />-2147204759|Kann Serienmuster für einen Auftragstyp, der nicht unterstützt wird, nicht aktualisieren.|
> |**Name**:<br />AsyncOperationInvalidStateChange<br />**Hex**:<br />80044162<br />**Nummer**:<br />-2147204766|Der Soll-Zustand konnte nicht festgelegt werden, weil der Statusübergang ungültig ist.|
> |**Name**:<br />AsyncOperationInvalidStateChangeToComplete<br />**Hex**:<br />80044165<br />**Nummer**:<br />-2147204763|Der Soll-Zustand konnte nicht abgeschlossen werden, weil der Statusübergang ungültig ist.|
> |**Name**:<br />AsyncOperationInvalidStateChangeToReady<br />**Hex**:<br />80044166<br />**Nummer**:<br />-2147204762|Der Soll-Zustand konnte nicht bereitgestellt werden, weil der Statusübergang ungültig ist.|
> |**Name**:<br />AsyncOperationInvalidStateChangeToSuspended<br />**Hex**:<br />80044167<br />**Nummer**:<br />-2147204761|Der Soll-Zustand konnte nicht unterbrochen werden, weil der Statusübergang ungültig ist.|
> |**Name**:<br />AsyncOperationInvalidStateChangeUnexpected<br />**Hex**:<br />80044163<br />**Nummer**:<br />-2147204765|Der Soll-Zustand konnte nicht festgelegt werden, weil der Status von einem anderen Prozess geändert wurde.|
> |**Name**:<br />AsyncOperationMissingId<br />**Hex**:<br />80044164<br />**Nummer**:<br />-2147204764|Das AsyncOperationId ist erforderlich, um das Update durchzuführen.|
> |**Name**:<br />AsyncOperationPostponed<br />**Hex**:<br />80040328<br />**Nummer**:<br />-2147220696|Dieser Vorgang wird hinausgeschoben, weil er für mehr als {0} Zeiten in {1} Minuten fehlschlug|
> |**Name**:<br />AsyncOperationPostponedByExceptionCountThrottle<br />**Hex**:<br />80060917<br />**Nummer**:<br />-2147088105|Momentan können wir diese Aktion nicht abschließen. Dies wurde verschoben. Wir werden es später noch einmal versuchen.|
> |**Name**:<br />AsyncOperationSuspendedOrLocked<br />**Hex**:<br />80040339<br />**Nummer**:<br />-2147220679|>Ein Hintergrundauftrag, der diesen Import zugeordnet ist, ist entweder angehalten oder gesperrt. Wenn Sie diesen Import löschen möchten, klicken Sie im Arbeitsbereich auf "Importe", öffnen Sie den Import, klicken Sie auf "Systemaufträge" setzen Sie sämtliche angehalten Aufträge fort.|
> |**Name**:<br />AsyncOperationTypeIsNotRecognized<br />**Hex**:<br />80044303<br />**Nummer**:<br />-2147204349|Der Vorgangstyp async des Vorgangs wird nicht erkannt.|
> |**Name**:<br />AsyncOperationTypeThrottled<br />**Hex**:<br />80060916<br />**Nummer**:<br />-2147088106|Der Auftrag konnte nicht abgeschlossen werden, da der Server ausgelastet ist. Wir werden bald wieder versuchen, den Auftrag auszuführen.|
> |**Name**:<br />AttachmentBlocked<br />**Hex**:<br />80043e09<br />**Nummer**:<br />-2147205623|Die Anlage ist entweder kein gültiger Typ oder zu groß. Es kann nicht heruntergeladen oder hochgeladen werden.|
> |**Name**:<br />AttachmentInvalidFileName<br />**Hex**:<br />80044a08<br />**Nummer**:<br />-2147202552|Anlagedateiname enthält ungültige Zeichen.|
> |**Name**:<br />AttachmentNotFound<br />**Hex**:<br />80048493<br />**Nummer**:<br />-2147187565|Der Verweis auf die Anlage wurde nicht gefunden.|
> |**Name**:<br />AttachmentNotRelatedToEmail<br />**Hex**:<br />80050006<br />**Nummer**:<br />-2147155962|Diese Anlage ist keiner E-Mail zugeordnet.|
> |**Name**:<br />AttributeCannotBeUpdated<br />**Hex**:<br />80060413<br />**Nummer**:<br />-2147089389|Attribut - {0} kann nicht für einen Geschäftsprozessfluss aktualisiert werden|
> |**Name**:<br />AttributeCannotBeUsedInAggregate<br />**Hex**:<br />80060559<br />**Nummer**:<br />-2147089063|Das {0}-Attribut kann nicht mit einer einer Aggregationsfunktion in einer Formel verwendet werden.|
> |**Name**:<br />AttributeDeprecated<br />**Hex**:<br />80044335<br />**Nummer**:<br />-2147204299|"Attribut ''{0}" auf Entität ''{1}" ist veraltet."|
> |**Name**:<br />AttributeDoesNotSupportLocalizedLabels<br />**Hex**:<br />80044198<br />**Nummer**:<br />-2147204712|Das definierte Attribut unterstützt die lokalisierte Beschriftungen nicht.|
> |**Name**:<br />AttributeFormulaDefinitionIsEmpty<br />**Hex**:<br />80060439<br />**Nummer**:<br />-2147089351|Die Formel ist leer.|
> |**Name**:<br />AttributeIsNotCustomAttribute<br />**Hex**:<br />80047009<br />**Nummer**:<br />-2147192823|Das angegebene Attribut ist kein benutzerdefiniertes Attribut|
> |**Name**:<br />AttributeIsNotFacetable<br />**Hex**:<br />80060305<br />**Nummer**:<br />-2147089659|Kann Facets für Benutzersuche für Entität {0} nicht festlegen, da Attribut {1} nicht klassifizierbar ist. Entfernen Sie es bitte aus der Liste, um fortzufahren.|
> |**Name**:<br />AttributeNotCreatedForOfficeGraphError<br />**Hex**:<br />80044237<br />**Nummer**:<br />-2147204553|Dieses Attribut kann nicht erstellt werden, da keine Unterstützung zum Aktivieren von Attributen für Office Graph verfügbar ist.|
> |**Name**:<br />AttributeNotOfTypePicklist<br />**Hex**:<br />8004033c<br />**Nummer**:<br />-2147220676|Dieses Attribut ist nicht in einer Dropdownliste, um einem Booleschen Wert oder einen Status/einem Attribut Status zugeordnet. Allerdings haben Sie ein ListValueMap-Element dafür eingeschlossen.  Korrigieren Sie diese Unregelmäßigkeit, und importieren Sie dann diese Datenzuordnung erneut.|
> |**Name**:<br />AttributeNotOfTypeReference<br />**Hex**:<br />80040390<br />**Nummer**:<br />-2147220592|Dieses Attribut wird nicht als Verweisattribut zugeordnet. Allerdings haben Sie ein ReferenceMap-Element dafür eingeschlossen.  Korrigieren Sie diese Unregelmäßigkeit, und importieren Sie dann diese Datenzuordnung erneut.|
> |**Name**:<br />AttributeNotSecured<br />**Hex**:<br />8004F508<br />**Nummer**:<br />-2147158776|Ein oder mehrere Felder sind für Feldebenensicherheit nicht verfügbar. Sicherheit auf Feldebene ist nicht aktiviert, bis Sie die Anpassungen veröffentlichen.|
> |**Name**:<br />AttributeNotUpdatedForOfficeGraphError<br />**Hex**:<br />80044238<br />**Nummer**:<br />-2147204552|Dieses Attribut kann nicht aktualisiert werden, da keine Unterstützung zum Aktivieren von Attributen für Office Graph verfügbar ist.|
> |**Name**:<br />AttributePermissionIsInvalid<br />**Hex**:<br />8004F50E<br />**Nummer**:<br />-2147158770|Berechtigung {0}für Feld {1} mit ID = {2} ist ungültig.|
> |**Name**:<br />AttributePermissionReadIsMissing<br />**Hex**:<br />8004F504<br />**Nummer**:<br />-2147158780|Die Benutzer besitzen keine Berechtigungen zum Lesen gesicherter Felder. Die angefrage Ausführung konnte nicht abgeschlossen werden.|
> |**Name**:<br />AttributePermissionUpdateIsMissingDuringShare<br />**Hex**:<br />8004F503<br />**Nummer**:<br />-2147158781|Die Benutzer besitzen keine Berechtigungen zum Aktualisieren gesicherter Felder. Die angefrage Ausführung konnte nicht abgeschlossen werden.|
> |**Name**:<br />AttributePermissionUpdateIsMissingDuringUpdate<br />**Hex**:<br />8004F507<br />**Nummer**:<br />-2147158777|Der Benutzer hat AttributePrivilegeUpdate und nicht bewilligten freigegebenen Zugriff für eines geschützten Attribut nicht während des Aktualisierungsvorgangs|
> |**Name**:<br />AttributePrivilegeCreateIsMissing<br />**Hex**:<br />8004F502<br />**Nummer**:<br />-2147158782|Die Benutzer besitzen keine Berechtigungen zum Erstellen gesicherter Felder. Die angefrage Ausführung konnte nicht abgeschlossen werden.|
> |**Name**:<br />AttributePrivilegeInvalidToUnsecure<br />**Hex**:<br />8004F50D<br />**Nummer**:<br />-2147158771|Sie müssen über ausreichende Berechtigungen für ein gesichertes Feld verfügen, um die Sicherheit auf Feldebene ändern zu können.|
> |**Name**:<br />AttributesExceeded<br />**Hex**:<br />80061501<br />**Nummer**:<br />-2147085055|Es kann höchstens 4 Attribute geben|
> |**Name**:<br />AttributeSharingCreateDuplicate<br />**Hex**:<br />8004F50B<br />**Nummer**:<br />-2147158773|Das Attribut wurde bereits freigegeben.|
> |**Name**:<br />AttributeSharingCreateShouldSetReadOrAndUpdateAccess<br />**Hex**:<br />8004F509<br />**Nummer**:<br />-2147158775|Sie müssen den Zugriff auf Lesen und/oder Aktualisieren setzen, wenn Sie ein gesichertes Attribut teilen. Attribut-ID: {0}|
> |**Name**:<br />AttributeSharingUpdateInvalid<br />**Hex**:<br />8004F50A<br />**Nummer**:<br />-2147158774|Sowohl "readAccess" als auch "updateAccess" sind falsch: Rufen Sie anstelle von "Update" den Befehl "Delete" auf.|
> |**Name**:<br />AttributeTypeNotSupportedForCalculatedField<br />**Hex**:<br />80050221<br />**Nummer**:<br />-2147155423|Das berechnete Feld/Rollupfeld wird nicht für MultiSelectPicklist-Attributtyp unterstützt.|
> |**Name**:<br />AttributeTypeNotSupportedForGroupByOrderByQuery<br />**Hex**:<br />80050224<br />**Nummer**:<br />-2147155420|Die Abfrage GroupBy oder OrderBy wird nicht für den MultiSelectPicklist-Attributtyp unterstützt.|
> |**Name**:<br />AttributeUpdateNotAllowed<br />**Hex**:<br />80060463<br />**Nummer**:<br />-2147089309|Das Geschäftsprozessflow-Update ist fehlgeschlagen. Das Update des Attributs „{0}” im Workflow „{1}” ist nicht zulässig.|
> |**Name**:<br />AuthenticateToServerBeforeRequestingProxy<br />**Hex**:<br />8004D228<br />**Nummer**:<br />-2147167704|Authentifizieren des serverType: {0}, bevor ein Proxy angefordert werden.|
> |**Name**:<br />AutoDataCaptureAuthorizationFailureException<br />**Hex**:<br />80091042<br />**Nummer**:<br />-2146889662|Sie verfügen nicht die richtige Office 365-Lizenz, um nicht nachverfolgte E-Mails zu erhalten. Wenden Sie sich an Ihren Systemadministrator.|
> |**Name**:<br />AutoDataCaptureDisabledError<br />**Hex**:<br />80091041<br />**Nummer**:<br />-2146889663|Automatische Erfassungsfunktion ist nicht aktiviert.|
> |**Name**:<br />AutoDataCaptureResponseRetrievalFailureException<br />**Hex**:<br />80091043<br />**Nummer**:<br />-2146889661|Fehler beim Abrufen von nicht verfolgten E-Mails von Exchange.|
> |**Name**:<br />AzureApplicationIdNotFound<br />**Hex**:<br />8004F510<br />**Nummer**:<br />-2147158768|Wir konnten diese Anwendungs-ID {0} nicht in Ihrem Azure Active Directory (Azure AD) mit CorrelationID {1} finden. Stellen Sie sicher, dass die Anwendung in Azure AD registriert ist.|
> |**Name**:<br />AzureApplicationIdNotFoundInOrgDB<br />**Hex**:<br />8004F512<br />**Nummer**:<br />-2147158766|Azure-Anwendungs-ID wurde nicht gefunden. Wir können die Anwendung ID {0} in der CRM-Datenbank nicht finden. Korrigieren Sie die Anwendungs-ID und senden Sie das Update erneut.|
> |**Name**:<br />AzureOperationResponseTimedOut<br />**Hex**:<br />80061635<br />**Nummer**:<br />-2147084747|Eine Azure-Vorgangsanforderung gab keine Reaktion innerhalb des angegebenen Timeoutzeitraums zurück. Führen Sie das Vorgangs- oder Zunahmetimeout, das für den Vorgang bereitgestellt wurde, erneut aus.|
> |**Name**:<br />AzureRecommendationModelBuildNotExist<br />**Hex**:<br />80061604<br />**Nummer**:<br />-2147084796|Die Azure-Empfehlungsmodells, die der verwendeten Empfehlungsmodellversion ist nicht vorhanden.|
> |**Name**:<br />AzureRecommendationModelNotExist<br />**Hex**:<br />80061603<br />**Nummer**:<br />-2147084797|Das Azure-Empfehlungsmodells existiert nicht.|
> |**Name**:<br />AzureServiceConnectionCascadeDeleteFailed<br />**Hex**:<br />80061636<br />**Nummer**:<br />-2147084746|Mindestens ein Modelle verwendet die Verbindung. Löschen Sie alle Modelle, die diese Verbindung verwenden, und versuchen Sie erneut, die Verbindung zu löschen.|
> |**Name**:<br />AzureServiceConnectionInvalidUri<br />**Hex**:<br />80061630<br />**Nummer**:<br />-2147084752|Geben Sie einen gültigen Service-URL an.|
> |**Name**:<br />AzureSqlDatabaseResourceLimitExceededError<br />**Hex**:<br />80072323<br />**Nummer**:<br />-2147015901|Die Beschränkung der Ressource für die Datenbank wurde erreicht. Überprüfen Sie die Ausnahme, um weitere Informationen zu erhalten.|
> |**Name**:<br />AzureSqlDatabaseStorageQuotaExceededError<br />**Hex**:<br />80072325<br />**Nummer**:<br />-2147015899|Die Speicherbeschränkung für die Datenbank wurde erreicht.|
> |**Name**:<br />AzureSqlMaxConcurrentWorkersLimitExceededError<br />**Hex**:<br />80072324<br />**Nummer**:<br />-2147015900|Zu viele gleichzeitige Anforderungen erkannt.|
> |**Name**:<br />AzureWebAppPluginsDisabled<br />**Hex**:<br />80050241<br />**Nummer**:<br />-2147155391|Auf Azure WebApp basierte Plug-Ins sind für die Organisation deaktiviert.|
> |**Name**:<br />BadAuthTicket<br />**Hex**:<br />8004A102<br />**Nummer**:<br />-2147180286|Das Ticket für die Authentifizierung ist ungültig|
> |**Name**:<br />BadRequest<br />**Hex**:<br />8005F100<br />**Nummer**:<br />-2147094272|Die Anforderung konnte nicht von Server verstanden werden.|
> |**Name**:<br />BaseAttributeNameNotPresentError<br />**Hex**:<br />80044240<br />**Nummer**:<br />-2147204544|BaseAttribute-Name muss in Bedingungs-XML vorhanden sein.|
> |**Name**:<br />BaseCurrencyCannotBeDeactivated<br />**Hex**:<br />80048cf4<br />**Nummer**:<br />-2147185420|Die Basiswährung kann nicht gelöscht werden.|
> |**Name**:<br />BaseCurrencyNotDeletable<br />**Hex**:<br />80048cff<br />**Nummer**:<br />-2147185409|Die Basiswährung der Organisation kann nicht gelöscht werden.|
> |**Name**:<br />BaseCurrencyOverflow<br />**Hex**:<br />80048cec<br />**Nummer**:<br />-2147185428|Der Wechselkurs, der für die in diesem Datensatz angegebene Währung für {0} festgelegt wurde, hat einen Wert für ein Basiswährungsfeld generiert, der größer als der für die Basiswährung ({1}) maximal zulässige Wert ist.|
> |**Name**:<br />BaseCurrencyUnderflow<br />**Hex**:<br />80048ceb<br />**Nummer**:<br />-2147185429|Der Wechselkurs, der für die in diesem Datensatz angegebene Währung für {0} festgelegt wurde, hat einen Wert für ein Basiswährungsfeld generiert, der kleiner als der für die Basiswährung ({1}) minimal zulässige Wert ist.|
> |**Name**:<br />BaseMatchingAttributeNotSameError<br />**Hex**:<br />80044245<br />**Nummer**:<br />-2147204539|Basis- und übereinstimmendes Attribut müssen denselben Typ aufweisen.|
> |**Name**:<br />BaseUnitDoesNotExist<br />**Hex**:<br />80043b1c<br />**Nummer**:<br />-2147206372|Die Basiseinheit ist nicht vorhanden.|
> |**Name**:<br />BaseUnitNotDeletable<br />**Hex**:<br />80043b03<br />**Nummer**:<br />-2147206397|Die Basiseinheit eines Zeitplans kann nicht gelöscht werden.|
> |**Name**:<br />BaseUnitNotNull<br />**Hex**:<br />80043b17<br />**Nummer**:<br />-2147206377|Verwenden Sie keine Basiseinheit als Wert für eine primäre Einheit. Dieser Wert sollte ungültig immer sein.|
> |**Name**:<br />BaseUomNameNotSpecified<br />**Hex**:<br />80043810<br />**Nummer**:<br />-2147207152|baseuomname nicht angegeben|
> |**Name**:<br />BDK_E_ADDRESS_VALIDATION_FAILURE<br />**Hex**:<br />8004B540<br />**Nummer**:<br />-2147175104|{0}  |
> |**Name**:<br />BDK_E_AGREEMENT_ALREADY_SIGNED<br />**Hex**:<br />8004B541<br />**Nummer**:<br />-2147175103|{0}  |
> |**Name**:<br />BDK_E_AUTHORIZATION_FAILED<br />**Hex**:<br />8004B542<br />**Nummer**:<br />-2147175102|{0}  |
> |**Name**:<br />BDK_E_AVS_FAILED<br />**Hex**:<br />8004B543<br />**Nummer**:<br />-2147175101|{0}  |
> |**Name**:<br />BDK_E_BAD_CITYNAME_LENGTH<br />**Hex**:<br />8004B544<br />**Nummer**:<br />-2147175100|{0}  |
> |**Name**:<br />BDK_E_BAD_STATECODE_LENGTH<br />**Hex**:<br />8004B545<br />**Nummer**:<br />-2147175099|{0}  |
> |**Name**:<br />BDK_E_BAD_ZIPCODE_LENGTH<br />**Hex**:<br />8004B546<br />**Nummer**:<br />-2147175098|{0}  |
> |**Name**:<br />BDK_E_BADXML<br />**Hex**:<br />8004B547<br />**Nummer**:<br />-2147175097|{0}  |
> |**Name**:<br />BDK_E_BANNED_PAYMENT_INSTRUMENT<br />**Hex**:<br />8004B548<br />**Nummer**:<br />-2147175096|{0}  |
> |**Name**:<br />BDK_E_BANNEDPERSON<br />**Hex**:<br />8004B549<br />**Nummer**:<br />-2147175095|{0}  |
> |**Name**:<br />BDK_E_CANNOT_EXCEED_MAX_OWNERSHIP<br />**Hex**:<br />8004B54A<br />**Nummer**:<br />-2147175094|{0}  |
> |**Name**:<br />BDK_E_COUNTRY_CURRENCY_PI_MISMATCH<br />**Hex**:<br />8004B54B<br />**Nummer**:<br />-2147175093|{0}  |
> |**Name**:<br />BDK_E_CREDIT_CARD_EXPIRED<br />**Hex**:<br />8004B54C<br />**Nummer**:<br />-2147175092|{0}  |
> |**Name**:<br />BDK_E_DATE_EXPIRED<br />**Hex**:<br />8004B54D<br />**Nummer**:<br />-2147175091|{0}  |
> |**Name**:<br />BDK_E_ERROR_COUNTRYCODE_MISMATCH<br />**Hex**:<br />8004B54E<br />**Nummer**:<br />-2147175090|{0}  |
> |**Name**:<br />BDK_E_ERROR_COUNTRYCODE_REQUIRED<br />**Hex**:<br />8004B54F<br />**Nummer**:<br />-2147175089|{0}  |
> |**Name**:<br />BDK_E_EXTRA_REFERRAL_DATA<br />**Hex**:<br />8004B550<br />**Nummer**:<br />-2147175088|{0}  |
> |**Name**:<br />BDK_E_GUID_EXISTS<br />**Hex**:<br />8004B551<br />**Nummer**:<br />-2147175087|{0}  |
> |**Name**:<br />BDK_E_INVALID_ADDRESS_ID<br />**Hex**:<br />8004B552<br />**Nummer**:<br />-2147175086|{0}  |
> |**Name**:<br />BDK_E_INVALID_BILLABLE_ACCOUNT_ID<br />**Hex**:<br />8004B553<br />**Nummer**:<br />-2147175085|{0}  Das angegebene Fakturierungskonto ist ungültig.  Obohl die objectID der richtige Typ ist, ist das Konto, das identifiziert wird, im System nicht vorhanden.|
> |**Name**:<br />BDK_E_INVALID_BUF_SIZE<br />**Hex**:<br />8004B554<br />**Nummer**:<br />-2147175084|{0}  |
> |**Name**:<br />BDK_E_INVALID_CATEGORY_NAME<br />**Hex**:<br />8004B555<br />**Nummer**:<br />-2147175083|{0}  |
> |**Name**:<br />BDK_E_INVALID_COUNTRY_CODE<br />**Hex**:<br />8004B556<br />**Nummer**:<br />-2147175082|{0}  |
> |**Name**:<br />BDK_E_INVALID_CURRENCY<br />**Hex**:<br />8004B557<br />**Nummer**:<br />-2147175081|{0}  |
> |**Name**:<br />BDK_E_INVALID_CUSTOMER_TYPE<br />**Hex**:<br />8004B558<br />**Nummer**:<br />-2147175080|{0}  |
> |**Name**:<br />BDK_E_INVALID_DATE<br />**Hex**:<br />8004B559<br />**Nummer**:<br />-2147175079|{0}  |
> |**Name**:<br />BDK_E_INVALID_EMAIL_ADDRESS<br />**Hex**:<br />8004B55A<br />**Nummer**:<br />-2147175078|{0}  |
> |**Name**:<br />BDK_E_INVALID_FILTER<br />**Hex**:<br />8004B55B<br />**Nummer**:<br />-2147175077|{0}  |
> |**Name**:<br />BDK_E_INVALID_GUID<br />**Hex**:<br />8004B55C<br />**Nummer**:<br />-2147175076|{0}  |
> |**Name**:<br />BDK_E_INVALID_INPUT_TO_TAXWARE_OR_VERAZIP<br />**Hex**:<br />8004B55D<br />**Nummer**:<br />-2147175075|{0}  |
> |**Name**:<br />BDK_E_INVALID_LOCALE<br />**Hex**:<br />8004B55E<br />**Nummer**:<br />-2147175074|{0}  |
> |**Name**:<br />BDK_E_INVALID_OBJECT_ID<br />**Hex**:<br />8004B55F<br />**Nummer**:<br />-2147175073|{0}  Das Fakturierungssystem kann das Objekt nicht finden (z. B. Firma oder Abonnements oder Angebot).|
> |**Name**:<br />BDK_E_INVALID_OFFERING_GUID<br />**Hex**:<br />8004B560<br />**Nummer**:<br />-2147175072|{0}  |
> |**Name**:<br />BDK_E_INVALID_PAYMENT_INSTRUMENT_STATUS<br />**Hex**:<br />8004B561<br />**Nummer**:<br />-2147175071|{0}  |
> |**Name**:<br />BDK_E_INVALID_PAYMENT_METHOD_ID<br />**Hex**:<br />8004B562<br />**Nummer**:<br />-2147175070|{0}  |
> |**Name**:<br />BDK_E_INVALID_PHONE_TYPE<br />**Hex**:<br />8004B563<br />**Nummer**:<br />-2147175069|{0}  |
> |**Name**:<br />BDK_E_INVALID_POLICY_ID<br />**Hex**:<br />8004B564<br />**Nummer**:<br />-2147175068|{0}  |
> |**Name**:<br />BDK_E_INVALID_REFERRALDATA_XML<br />**Hex**:<br />8004B565<br />**Nummer**:<br />-2147175067|{0}  |
> |**Name**:<br />BDK_E_INVALID_STATE_FOR_COUNTRY<br />**Hex**:<br />8004B566<br />**Nummer**:<br />-2147175066|{0}  |
> |**Name**:<br />BDK_E_INVALID_SUBSCRIPTION_ID<br />**Hex**:<br />8004B567<br />**Nummer**:<br />-2147175065|{0}  Die angegebene Abonnement-ID ist ungültig.  Obwohl die objectID der richtige Typ ist und sich auch auf eine gültige Firma in SCS hinweist, ist das Abonnement, das identifizifert wird, nicht in SCS.|
> |**Name**:<br />BDK_E_INVALID_TAX_EXEMPT_TYPE<br />**Hex**:<br />8004B568<br />**Nummer**:<br />-2147175064|{0}  |
> |**Name**:<br />BDK_E_MEG_CONFLICT<br />**Hex**:<br />8004B569<br />**Nummer**:<br />-2147175063|{0}  |
> |**Name**:<br />BDK_E_MULTIPLE_CITIES_FOUND<br />**Hex**:<br />8004B56A<br />**Nummer**:<br />-2147175062|{0}  |
> |**Name**:<br />BDK_E_MULTIPLE_COUNTIES_FOUND<br />**Hex**:<br />8004B56B<br />**Nummer**:<br />-2147175061|{0}  |
> |**Name**:<br />BDK_E_NON_ACTIVE_ACCOUNT<br />**Hex**:<br />8004B56C<br />**Nummer**:<br />-2147175060|{0}  |
> |**Name**:<br />BDK_E_NOPERMISSION<br />**Hex**:<br />8004B56D<br />**Nummer**:<br />-2147175059|{0}  Der aufrufende Partner hat keinen Zugriff auf diese Methode, oder wenn der Anforderer nicht die Berechtigung zur Suche nach der angegebenen PUID hat.|
> |**Name**:<br />BDK_E_OBJECT_ROLE_LIMIT_EXCEEDED<br />**Hex**:<br />8004B56E<br />**Nummer**:<br />-2147175058|{0}  |
> |**Name**:<br />BDK_E_OFFERING_ACCOUNT_CURRENCY_MISMATCH<br />**Hex**:<br />8004B56F<br />**Nummer**:<br />-2147175057|{0}  |
> |**Name**:<br />BDK_E_OFFERING_COUNTRY_ACCOUNT_MISMATCH<br />**Hex**:<br />8004B570<br />**Nummer**:<br />-2147175056|{0}  |
> |**Name**:<br />BDK_E_OFFERING_NOT_PURCHASEABLE<br />**Hex**:<br />8004B571<br />**Nummer**:<br />-2147175055|{0}  |
> |**Name**:<br />BDK_E_OFFERING_PAYMENT_INSTRUMENT_MISMATCH<br />**Hex**:<br />8004B572<br />**Nummer**:<br />-2147175054|{0}  |
> |**Name**:<br />BDK_E_OFFERING_REQUIRES_PI<br />**Hex**:<br />8004B573<br />**Nummer**:<br />-2147175053|{0}  |
> |**Name**:<br />BDK_E_PARTNERNOTINBILLING<br />**Hex**:<br />8004B574<br />**Nummer**:<br />-2147175052|{0}  |
> |**Name**:<br />BDK_E_PAYMENT_PROVIDER_CONNECTION_FAILED<br />**Hex**:<br />8004B575<br />**Nummer**:<br />-2147175051|{0}  |
> |**Name**:<br />BDK_E_POLICY_DEAL_COUNTRY_MISMATCH<br />**Hex**:<br />8004B577<br />**Nummer**:<br />-2147175049|{0}  |
> |**Name**:<br />BDK_E_PRIMARY_PHONE_REQUIRED<br />**Hex**:<br />8004B576<br />**Nummer**:<br />-2147175050|{0}  |
> |**Name**:<br />BDK_E_PUID_ROLE_LIMIT_EXCEEDED<br />**Hex**:<br />8004B578<br />**Nummer**:<br />-2147175048|{0}  |
> |**Name**:<br />BDK_E_RATING_FAILURE<br />**Hex**:<br />8004B579<br />**Nummer**:<br />-2147175047|{0}  |
> |**Name**:<br />BDK_E_REQUIRED_FIELD_MISSING<br />**Hex**:<br />8004B57A<br />**Nummer**:<br />-2147175046|{0}  |
> |**Name**:<br />BDK_E_STATE_CITY_INVALID<br />**Hex**:<br />8004B57B<br />**Nummer**:<br />-2147175045|{0}  |
> |**Name**:<br />BDK_E_STATE_INVALID<br />**Hex**:<br />8004B57C<br />**Nummer**:<br />-2147175044|{0}  |
> |**Name**:<br />BDK_E_STATE_ZIP_CITY_INVALID<br />**Hex**:<br />8004B57D<br />**Nummer**:<br />-2147175043|{0}  |
> |**Name**:<br />BDK_E_STATE_ZIP_CITY_INVALID2<br />**Hex**:<br />8004B57E<br />**Nummer**:<br />-2147175042|{0}  |
> |**Name**:<br />BDK_E_STATE_ZIP_CITY_INVALID3<br />**Hex**:<br />8004B57F<br />**Nummer**:<br />-2147175041|{0}  |
> |**Name**:<br />BDK_E_STATE_ZIP_CITY_INVALID4<br />**Hex**:<br />8004B580<br />**Nummer**:<br />-2147175040|{0}  |
> |**Name**:<br />BDK_E_STATE_ZIP_COVERS_MULTIPLE_CITIES<br />**Hex**:<br />8004B581<br />**Nummer**:<br />-2147175039|{0}  |
> |**Name**:<br />BDK_E_STATE_ZIP_INVALID<br />**Hex**:<br />8004B582<br />**Nummer**:<br />-2147175038|{0}  |
> |**Name**:<br />BDK_E_TAXID_EXPDATE<br />**Hex**:<br />8004B583<br />**Nummer**:<br />-2147175037|{0}  |
> |**Name**:<br />BDK_E_TOKEN_BLACKLISTED<br />**Hex**:<br />8004B584<br />**Nummer**:<br />-2147175036|{0}  |
> |**Name**:<br />BDK_E_TOKEN_EXPIRED<br />**Hex**:<br />8004B585<br />**Nummer**:<br />-2147175035|{0}  |
> |**Name**:<br />BDK_E_TOKEN_NOT_VALID_FOR_OFFERING<br />**Hex**:<br />8004B586<br />**Nummer**:<br />-2147175034|{0}  |
> |**Name**:<br />BDK_E_TOKEN_RANGE_BLACKLISTED<br />**Hex**:<br />8004B587<br />**Nummer**:<br />-2147175033|{0}  |
> |**Name**:<br />BDK_E_TRANS_BALANCE_TO_PI_INVALID<br />**Hex**:<br />8004B588<br />**Nummer**:<br />-2147175032|{0}  |
> |**Name**:<br />BDK_E_UNKNOWN_SERVER_FAILURE<br />**Hex**:<br />8004B589<br />**Nummer**:<br />-2147175031|{0}  Unbekannter Serverfehler.|
> |**Name**:<br />BDK_E_UNSUPPORTED_CHAR_EXIST<br />**Hex**:<br />8004B58A<br />**Nummer**:<br />-2147175030|{0}  |
> |**Name**:<br />BDK_E_USAGE_COUNT_FOR_TOKEN_EXCEEDED<br />**Hex**:<br />8004B58F<br />**Nummer**:<br />-2147175025|{0}  Abrechnungstoken wurde bereits ausgegeben.|
> |**Name**:<br />BDK_E_VATID_DOESNOTHAVEEXPDATE<br />**Hex**:<br />8004B58B<br />**Nummer**:<br />-2147175029|{0}  |
> |**Name**:<br />BDK_E_ZIP_CITY_MISSING<br />**Hex**:<br />8004B58C<br />**Nummer**:<br />-2147175028|{0}  |
> |**Name**:<br />BDK_E_ZIP_INVALID<br />**Hex**:<br />8004B58D<br />**Nummer**:<br />-2147175027|{0}  Fakturierungspostleitzahlfehler.|
> |**Name**:<br />BDK_E_ZIP_INVALID_FOR_ENTERED_STATE<br />**Hex**:<br />8004B58E<br />**Nummer**:<br />-2147175026|{0}  Fakturierungspostleitzahlfehler.|
> |**Name**:<br />BidsAuthenticationError<br />**Hex**:<br />8005E003<br />**Nummer**:<br />-2147098621|Ein Fehler beim Authentifizieren mit Server {0} ist aufgetreten.|
> |**Name**:<br />BidsAuthenticationFailed<br />**Hex**:<br />8005E006<br />**Nummer**:<br />-2147098618|Authentifizierungsfehler beim Verbindungsversuch mit Server {0}. Der Benutzername oder das Kennwort ist falsch.|
> |**Name**:<br />BidsInvalidConnectionString<br />**Hex**:<br />8005E000<br />**Nummer**:<br />-2147098624|Die Eingangsverbindungszeichenfolge ist ungültig. Gebrauch: ServerUrl[;OrganizationName][;HomeRealmUrl]|
> |**Name**:<br />BidsInvalidUrl<br />**Hex**:<br />8005E001<br />**Nummer**:<br />-2147098623|Eingabe-URL {0} ist ungültig.|
> |**Name**:<br />BidsNoOrganizationsFound<br />**Hex**:<br />8005E004<br />**Nummer**:<br />-2147098620|Für den Benutzer wurden keine Organisationen gefunden.|
> |**Name**:<br />BidsOrganizationNotFound<br />**Hex**:<br />8005E005<br />**Nummer**:<br />-2147098619|Für den Benutzer wurde keine {0} Organisation gefunden.|
> |**Name**:<br />BidsServerConnectionFailed<br />**Hex**:<br />8005E002<br />**Nummer**:<br />-2147098622|Fehler beim Herstellen der Serververbindung {0}.|
> |**Name**:<br />BillingNoSettingError<br />**Hex**:<br />8004B531<br />**Nummer**:<br />-2147175119|Keine Konfigurationseinstellung für Fakturierungsanwendung [{0}] gefunden.|
> |**Name**:<br />BillingPartnerCertificate<br />**Hex**:<br />8004B530<br />**Nummer**:<br />-2147175120|Das richtige Partnerszertifikat zur Verwendung mit der Fakturierung konnte nicht bestimmt werden.  Aussteller: {0}Betreff: {1} Definierte Übereinstimmungen: [{2}]  Namenübereinstimmungen: [{3}]  Alle gültigen Zertifikate: [{4}].|
> |**Name**:<br />BillingRetrieveKeyError<br />**Hex**:<br />8004B538<br />**Nummer**:<br />-2147175112|Der Fakturierungssitzungsschlüssel konnte nicht abgerufen werde: "{0}"|
> |**Name**:<br />BillingTestConnectionError<br />**Hex**:<br />8004B532<br />**Nummer**:<br />-2147175118|Fakturierung ist nicht verfügbar: Aufruf von IsServiceAvailable hat "False" zurückgegeben.|
> |**Name**:<br />BillingTestConnectionException<br />**Hex**:<br />8004B533<br />**Nummer**:<br />-2147175117|Fakturierungs-TestConnection-Ausnahme.|
> |**Name**:<br />BillingUnknownErrorCode<br />**Hex**:<br />8004B536<br />**Nummer**:<br />-2147175114|Fakturierungsfehlercode [{0}] wurde mit Ausnahme {1} ausgelöst|
> |**Name**:<br />BillingUnknownException<br />**Hex**:<br />8004B537<br />**Nummer**:<br />-2147175113|Fakturierungsfehlercode wurde mit Ausnahme {0} ausgelöst|
> |**Name**:<br />BillingUnmappedErrorCode<br />**Hex**:<br />8004B535<br />**Nummer**:<br />-2147175115|Fakturierungsfehlercode [{0}] wurde mit Ausnahme {1} ausgelöst|
> |**Name**:<br />BillingUserPuidNullError<br />**Hex**:<br />8004B534<br />**Nummer**:<br />-2147175116|Benutzer Puid ist erforderlich, ist jedoch ungültig.|
> |**Name**:<br />BookFirstInstanceFailed<br />**Hex**:<br />8004E10E<br />**Nummer**:<br />-2147163890|Fehler beim Buchen der ersten Instanz.|
> |**Name**:<br />BooleanOptionOutOfRange<br />**Hex**:<br />8004431C<br />**Nummer**:<br />-2147204324|Boolesche Attributoptionen müssen einen Wert von 0 oder 1 haben.|
> |**Name**:<br />BothConnectionSidesAreNeeded<br />**Hex**:<br />80048218<br />**Nummer**:<br />-2147188200|Für beide Seiten der Verbindung muss ein Name angegeben oder eine Rolle ausgewählt werden.|
> |**Name**:<br />BPFEntityAlreadyExists<br />**Hex**:<br />80060384<br />**Nummer**:<br />-2147089532|BPF-Entität mit diesem Namen ist bereits vorhanden.|
> |**Name**:<br />BpfEntityServiceIsNull<br />**Hex**:<br />80060446<br />**Nummer**:<br />-2147089338|Fehler beim Erstellen oder Aktualisieren des Geschäftsprozesses: BpfEntityService darf nicht Null sein.|
> |**Name**:<br />BpfFactoryIsNull<br />**Hex**:<br />80060447<br />**Nummer**:<br />-2147089337|Fehler beim Erstellen oder Aktualisieren des Geschäftsprozesses: BpfFactory darf nicht Null sein.|
> |**Name**:<br />BpfInstanceAlreadyExists<br />**Hex**:<br />80060397<br />**Nummer**:<br />-2147089513|Ein Geschäftsprozessfluss ist für den Zieldatensatz bereits vorhanden und kann nicht erstellt werden. Wenden Sie sich an Ihren Systemadministrator.|
> |**Name**:<br />BpfVisitorIsNull<br />**Hex**:<br />80060448<br />**Nummer**:<br />-2147089336|Fehler beim Erstellen oder Aktualisieren des Geschäftsprozesses: BpfVisitor darf nicht Null sein.|
> |**Name**:<br />BulkDeleteChildFailure<br />**Hex**:<br />80048459<br />**Nummer**:<br />-2147187623|Einer der untergeordneten Massenaufträge zum Löschen ist Fehlgeschlagen|
> |**Name**:<br />BulkDeleteRecordDeletionFailure<br />**Hex**:<br />80048435<br />**Nummer**:<br />-2147187659|Der Datensatz kann nicht gelöscht werden.|
> |**Name**:<br />BulkDetectInvalidEmailRecipient<br />**Hex**:<br />80048422<br />**Nummer**:<br />-2147187678|Der E-Mail-Empfänger ist nicht vorhanden, oder die E-Mail-Adresse für den E-Mail Empfänger ist ungültig.|
> |**Name**:<br />BulkMailOperationFailed<br />**Hex**:<br />8004502D<br />**Nummer**:<br />-2147200979|Der Massen-E-Mail-Auftrag hat mit {0} Fehlern abgeschlossen. Der Fehler wird verursacht, weil E-Mail-Adressen fehlen oder weil Sie keine Berechtigung zum Senden einer E-Mail haben. Wenn Sie Datensätze mit fehlende E-Mail-Adressen suchen, nutzen Sie die Erweiterte Suche. Wenn Sie zusätzliche E-Mail-Berechtigungen benötigen, wenden Sie sich an den Systemadministrator.|
> |**Name**:<br />BulkMailServiceNotAccessible<br />**Hex**:<br />80048304<br />**Nummer**:<br />-2147187964|Der Microsoft Dynamics 365-Massen-E-Mail-Dienst wird nicht ausgeführt.|
> |**Name**:<br />BundleCannotContainBundle<br />**Hex**:<br />8004F972<br />**Nummer**:<br />-2147157646|Sie können einem Paket kein Paket hinzufügen.|
> |**Name**:<br />BundleCannotContainProductFamily<br />**Hex**:<br />8004F992<br />**Nummer**:<br />-2147157614|Sie können einem Paket keine Produktfamilie hinzufügen.|
> |**Name**:<br />BundleCannotContainProductKit<br />**Hex**:<br />80061014<br />**Nummer**:<br />-2147086316|Sie können einem Paket keinen Bausatz hinzufügen.|
> |**Name**:<br />BundleMaxPropertyLimitExceeded<br />**Hex**:<br />8008100E<br />**Nummer**:<br />-2146955250|Mit diesem Paket können Anpassungen gelöscht werden, da sie zu viele Eigenschaften haben. Ein Paket in Ihrer Organisation kann maximal {0} Eigenschaften haben.|
> |**Name**:<br />BusinessManagementInvalidUserId<br />**Hex**:<br />80041d1f<br />**Nummer**:<br />-2147214049|Die Benutzer-ID(s) [{0}] ist nicht gültig.|
> |**Name**:<br />BusinessManagementLoopBeingCreated<br />**Hex**:<br />80041d21<br />**Nummer**:<br />-2147214047|Durch das Erstellen dieser übergeordneten Zuordnung würde eine Schleife in der Unternehmenshierarchie erstellt werden.|
> |**Name**:<br />BusinessManagementLoopExists<br />**Hex**:<br />80041d20<br />**Nummer**:<br />-2147214048|Schleife ist in der Unternehmenshierarchie vorhanden.|
> |**Name**:<br />BusinessManagementObjectAlreadyExists<br />**Hex**:<br />8004022a<br />**Nummer**:<br />-2147220950|Ein Objekt mit dem angegebenen Namen ist bereits vorhanden.|
> |**Name**:<br />BusinessNotEnabled<br />**Hex**:<br />8004032c<br />**Nummer**:<br />-2147220692|Die angegebene Organisation ist deaktiviert.|
> |**Name**:<br />BusinessProcessFlowDefinitionOutdated<br />**Hex**:<br />80060375<br />**Nummer**:<br />-2147089547|Diese Aktion kann nicht abgeschlossen werden, da die Geschäftsprozessfluss-Definition mit der Prozessaktion nicht synchron ist. Bitte wenden Sie sich an Ihren Dynamics 365-Systemadministrator, um den Geschäftsprozessfluss zu aktualisieren.|
> |**Name**:<br />BusinessProcessFlowMissingEntityErrorMessage<br />**Hex**:<br />80060440<br />**Nummer**:<br />-2147089344|Fehler beim Importieren von Geschäftsprozess „{0}”, da die Lösung keine entsprechende Geschäftsprozessentität „{1}” umfasst.|
> |**Name**:<br />BusinessProcessFlowStepHasInvalidParent<br />**Hex**:<br />80060405<br />**Nummer**:<br />-2147089403|Übergeordnetes {0} Element ist nicht vom Typ {1}|
> |**Name**:<br />BusinessRuleEditorSupportsOnlyIfConditionBranch<br />**Hex**:<br />80060008<br />**Nummer**:<br />-2147090424|Der Geschäftsregeleditor unterstützt nur eine Bedingung. Korrigieren Sie in der Regel.|
> |**Name**:<br />BusinessUnitCannotBeDisabled<br />**Hex**:<br />80041d59<br />**Nummer**:<br />-2147213991|Unternehmenseinheit kann nicht deaktiviert werden: kein aktiver Benutzer mit der Systemadministratorrolle außerhalb der Unterstruktur der Unternehmenseinheit vorhanden.|
> |**Name**:<br />BusinessUnitDefaultTeamOwnsRecords<br />**Hex**:<br />80041d62<br />**Nummer**:<br />-2147213982|Standardteam der Unternehmenseinheit und besitzt Datensätze. Unternehmenseinheit kann nicht gelöscht werden.|
> |**Name**:<br />BusinessUnitHasChildAndCannotBeDeleted<br />**Hex**:<br />80041d61<br />**Nummer**:<br />-2147213983|Unternehmenseinheit besitzt eine untergeordnete Unternehmenseinheit und kann nicht gelöscht werden.|
> |**Name**:<br />BusinessUnitIsNotDisabledAndCannotBeDeleted<br />**Hex**:<br />80041d60<br />**Nummer**:<br />-2147213984|Nicht deaktivierte Unternehmenseinheit kann nicht gelöscht werden.|
> |**Name**:<br />BusinessUnitQueuesAssociatedWithBU<br />**Hex**:<br />80072526<br />**Nummer**:<br />-2147015386|Es gibt {0}-Warteschlangen, die auf diese BusinessUnit mit ID ={1}, Name = {2} verweisen. Bitte löschen Sie die Warteschlangen, bevor Sie diese Unternehmenseinheit löschen oder weisen Sie sie einer anderen Unternehmenseinheit zu.|
> |**Name**:<br />CalculatedFieldsAssignmentMismatch<br />**Hex**:<br />8006042b<br />**Nummer**:<br />-2147089365|Sie können den Wert {0} vom Typ {1} nicht auf den Typ {2} einstellen.|
> |**Name**:<br />CalculatedFieldsCyclicReference<br />**Hex**:<br />80060431<br />**Nummer**:<br />-2147089359|Das Feld {0} kann im berechneten Feld {1} nicht verwendet werden, da es zu einem Zirkelbezug führen würde.|
> |**Name**:<br />CalculatedFieldsDateOnlyBehaviorTypeMismatch<br />**Hex**:<br />8006043a<br />**Nummer**:<br />-2147089350|Sie können nur den Feldtyp "Nur Datum" verwenden.|
> |**Name**:<br />CalculatedFieldsDepthExceeded<br />**Hex**:<br />80060432<br />**Nummer**:<br />-2147089358|Sie können das Feld {0} nicht erstellen oder aktualisieren, da das Feld {1} bereits eine Kette berechneter Felder mit einer Tiefe von {2} aufweist.|
> |**Name**:<br />CalculatedFieldsDivideByZero<br />**Hex**:<br />8006042d<br />**Nummer**:<br />-2147089363|Sie können nicht nach {0} aufteilen, das auf Null auswertet.|
> |**Name**:<br />CalculatedFieldsEntitiesExceeded<br />**Hex**:<br />80060433<br />**Nummer**:<br />-2147089357|Das Feld {0} kann nicht erstellt oder aktualisiert werden, da das Feld {1} eine weitere Formel enthält, die einen übergeordneten Datensatz verwendet.|
> |**Name**:<br />CalculatedFieldsFeatureNotEnabled<br />**Hex**:<br />80060422<br />**Nummer**:<br />-2147089374|Die Funktion "Berechnetes Feld" ist nicht verfügbar.|
> |**Name**:<br />CalculatedFieldsFunctionMismatch<br />**Hex**:<br />8006042c<br />**Nummer**:<br />-2147089364|Sie können {0} vom Typ {1} nicht mit der aktuellen Funktion verwenden.|
> |**Name**:<br />CalculatedFieldsInvalidAttribute<br />**Hex**:<br />80060428<br />**Nummer**:<br />-2147089368|Das Feld {0} ist nicht vorhanden.|
> |**Name**:<br />CalculatedFieldsInvalidAttributes<br />**Hex**:<br />8006042e<br />**Nummer**:<br />-2147089362|Die Formel verweist auf folgende Attributte, die nicht vorhandene sind: {0}.|
> |**Name**:<br />CalculatedFieldsInvalidEntity<br />**Hex**:<br />80060423<br />**Nummer**:<br />-2147089373|Die Formel enthält einen ungültigen Verweis: {0}.|
> |**Name**:<br />CalculatedFieldsInvalidFunction<br />**Hex**:<br />80060427<br />**Nummer**:<br />-2147089369|Die Funktion {0} ist nicht vorhanden.|
> |**Name**:<br />CalculatedFieldsInvalidSourceTypeMask<br />**Hex**:<br />80060438<br />**Nummer**:<br />-2147089352|Die Formel kann nicht gespeichert werden, da sie Verweise auf folgende Felder mit ungültigen Definitionen enthält: {0}.|
> |**Name**:<br />CalculatedFieldsInvalidValue<br />**Hex**:<br />8006042f<br />**Nummer**:<br />-2147089361|Die Formel verweist auf einen Wert, der nicht vorhanden ist.|
> |**Name**:<br />CalculatedFieldsInvalidValues<br />**Hex**:<br />80060430<br />**Nummer**:<br />-2147089360|Die Formel verweist auf die folgenden Werte, die nicht vorhanden sind: {0}.|
> |**Name**:<br />CalculatedFieldsInvalidXaml<br />**Hex**:<br />80060424<br />**Nummer**:<br />-2147089372|Das {0} Feld weist eine ungültige XAML-Formeldefinition auf.|
> |**Name**:<br />CalculatedFieldsNonCalculatedFieldAssignment<br />**Hex**:<br />80060425<br />**Nummer**:<br />-2147089371|Nur berechnete Felder können eine Formeldefinition haben.|
> |**Name**:<br />CalculatedFieldsPrimitiveOverflow<br />**Hex**:<br />8006042a<br />**Nummer**:<br />-2147089366|Der Wert {0} kann nicht in den Typ {1} konvertiert werden.|
> |**Name**:<br />CalculatedFieldsTimeInvBehaviorTypeMismatch<br />**Hex**:<br />8006043b<br />**Nummer**:<br />-2147089349|Sie können nur den Feldtyp "Datum/Uhrzeit zeitzonenunabhängig" verwenden.|
> |**Name**:<br />CalculatedFieldsTypeMismatch<br />**Hex**:<br />80060426<br />**Nummer**:<br />-2147089370|Sie können {0} vom Typ {1} nicht mit dem aktuellen Operator verwenden.|
> |**Name**:<br />CalculatedFieldsUserLocBehaviorTypeMismatch<br />**Hex**:<br />8006043c<br />**Nummer**:<br />-2147089348|Sie können nur den Feldtyp "Datum/Uhrzeit Ortszeit Benutzer" verwenden.|
> |**Name**:<br />CalculatedFieldUsedInRollupFieldCannotBeComplex<br />**Hex**:<br />80060550<br />**Nummer**:<br />-2147089072|Mindestens ein bestimmtes Rollupfeld hängt von diesem berechneten Feld ab. Der Quellentitätsfilter muss entweder ein einfaches Feld oder ein einfaches berechnetes Feld enthalten. Rollupfelder oder berechnete Felder mit Rollupfeld sind nicht zulässig.|
> |**Name**:<br />CalculateNowOverflowError<br />**Hex**:<br />80060558<br />**Nummer**:<br />-2147089064|Fehler bei der Berechnung aufgrund eines Überlauffehlers.|
> |**Name**:<br />CallerCannotChangeOwnDomainName<br />**Hex**:<br />80044161<br />**Nummer**:<br />-2147204767|Der Anrufer kann den eigenen Domänennamen nicht ändern|
> |**Name**:<br />CalloutException<br />**Hex**:<br />8004025b<br />**Nummer**:<br />-2147220901|Legendenausnahme aufgetreten.|
> |**Name**:<br />CampaignActivityAlreadyPropagated<br />**Hex**:<br />80040326<br />**Nummer**:<br />-2147220698|Diese Kampagnenaktivität wurde bereits verteilt. Kampagnenaktivitäten können maximal einmal verteilt werden.|
> |**Name**:<br />CampaignActivityClosed<br />**Hex**:<br />80040331<br />**Nummer**:<br />-2147220687|Die Kampagnenaktivität  wird abgebrochen oder geschlossen. Kampagnenaktivitäten können nicht verteilt werden, nachdem sie geschlossen oder storniert wurden.|
> |**Name**:<br />CampaignNotSpecifiedForCampaignActivity<br />**Hex**:<br />80040309<br />**Nummer**:<br />-2147220727|Feld "Land/Region" ist ein Pflichtfeld.|
> |**Name**:<br />CampaignNotSpecifiedForCampaignResponse<br />**Hex**:<br />8004030a<br />**Nummer**:<br />-2147220726|Feld "Land/Region" ist ein Pflichtfeld.|
> |**Name**:<br />CanAssociateOnlyMobileOfflineEnabledEntityToProfileItem<br />**Hex**:<br />8006099E<br />**Nummer**:<br />-2147087970|{0} muss für Mobile Offline aktiviert sein.|
> |**Name**:<br />CanAssociateOnlyMobileOfflineEnableEntityToProfileItem<br />**Hex**:<br />8006099C<br />**Nummer**:<br />-2147087972|Diese Entität muss für Mobile Offline aktiviert sein.|
> |**Name**:<br />CanAssociateOnlyOneEntityPerProfileItem<br />**Hex**:<br />8006099D<br />**Nummer**:<br />-2147087971|Sie können einem Mobile Offline-Profildatensatz pro Entität nur einen Mobile Offline-Profilelement-Datensatz hinzufügen. |
> |**Name**:<br />CancelActiveChildCaseFirst<br />**Hex**:<br />8003F451<br />**Nummer**:<br />-2147224495|Brechen Sie die aktive untergeordnete Anfrage ab, bevor Sie die übergeordnete Anfrage abbrechen.|
> |**Name**:<br />CannotAcceptEmail<br />**Hex**:<br />8005E20B<br />**Nummer**:<br />-2147098101|Die E-Mail, die Sie nutzen, kann nicht für Microsoft Dynamics 365 akzeptiert werden. Ursachencode: {0}.|
> |**Name**:<br />CannotAccessExchangeOptinStatus<br />**Hex**:<br />80071110<br />**Nummer**:<br />-2147020528|Exchange-Optionsstatus ist nicht verfügbar.|
> |**Name**:<br />CannotActivateMailboxForDisabledUserOrQueue<br />**Hex**:<br />8005E230<br />**Nummer**:<br />-2147098064|Postfach kann nicht aktiviert werden, da der Benutzer oder die Warteschlange, die dem Postfach zugeordnet ist, im deaktivierten Zustand ist. Postfach kann nur für aktiven Benutzer/Warteschlange aktiviert werden.|
> |**Name**:<br />CannotActivateRecord<br />**Hex**:<br />80081017<br />**Nummer**:<br />-2146955241|Sie können eine zurückgezogene Produktfamilie oder einen zurückgezogenen Paketdatensatz nicht aktivieren. Außerdem können ein zurückgezogenes Produkt, das Teil einer Produktfamilie ist, nicht reaktivieren.|
> |**Name**:<br />CannotActOnBehalfOfAnotherUser<br />**Hex**:<br />8004A110<br />**Nummer**:<br />-2147180272|Der Benutzer erhält keine Berechtigung, im Auftrag eines anderen Benutzer zu handeln.|
> |**Name**:<br />CannotActOnBehalfOfExternalParty<br />**Hex**:<br />80061116<br />**Nummer**:<br />-2147086058|Der Benutzer erhält keine Berechtigung, im Auftrag einer externen Partei zu handeln.|
> |**Name**:<br />CannotAddActivityPartyEntityToMobileOfflineProfileItem<br />**Hex**:<br />800609AD<br />**Nummer**:<br />-2147087955|Sie können die ActivityParty-Entität nicht zum Mobile Offline-Profilelement hinzufügen, da sie automatisch hinzugefügt wird, wenn eine Aktivitätsentität zum Profil hinzugefügt wird.|
> |**Name**:<br />CannotAddBundleToItself<br />**Hex**:<br />80061031<br />**Nummer**:<br />-2147086287|Sie können ein Paket nicht sich selbst hinzufügen.|
> |**Name**:<br />CannotAddBundleToPricelist<br />**Hex**:<br />80061007<br />**Nummer**:<br />-2147086329|Sie können der Preisliste das Paket {0} nicht hinzufügen, da das Paketprodukt {1} nicht in der Preisliste ist.|
> |**Name**:<br />CannotAddBusinessDataLocalizedLabelEntityToMobileOfflineProfileItem<br />**Hex**:<br />800609AC<br />**Nummer**:<br />-2147087956|Sie können die BusinessDataLocalizedLabel-Entität nicht zum Mobile Offline-Profilelement hinzufügen, da sie automatisch hinzugefügt wird, wenn die Produktentität zum Profil hinzugefügt wird.|
> |**Name**:<br />CannotAddDraftFamilyProductBundleToCases<br />**Hex**:<br />8004F984<br />**Nummer**:<br />-2147157628|Sie können keine Produktfamilie, kein Entwurfsprodukt und kein Entwurfspaket hinzufügen.|
> |**Name**:<br />CannotAddIntersectEntityToMobileOfflineProfileItem<br />**Hex**:<br />800609AB<br />**Nummer**:<br />-2147087957|Sie können die überschneidende Entität nicht zum Mobile Offline-Profilelement hinzufügen, da sie automatisch hinzugefügt wird, wenn ihre übergeordneten Entitäten zum Profil hinzugefügt werden.|
> |**Name**:<br />CannotAddKitToItself<br />**Hex**:<br />80061032<br />**Nummer**:<br />-2147086286|Sie können einen Bausatz nicht sich selbst hinzufügen.|
> |**Name**:<br />CannotAddMembersToDefaultTeam<br />**Hex**:<br />8004830B<br />**Nummer**:<br />-2147187957|Kann dem Standardunternehmenseinheitsteam keine Mitglieder hinzufügen.|
> |**Name**:<br />CannotAddNewBooleanValue<br />**Hex**:<br />8004431D<br />**Nummer**:<br />-2147204323|Sie können einer Option kein boolesches Attribut hinzufügen.|
> |**Name**:<br />CannotAddNewStateValue<br />**Hex**:<br />8004431E<br />**Nummer**:<br />-2147204322|Sie können kein Statusoptionen einem Statusattribut hinzufügen.|
> |**Name**:<br />CannotAddNonCustomizableComponent<br />**Hex**:<br />8004F015<br />**Nummer**:<br />-2147160043|Komponente {0} {1} kann nicht zur Lösung hinzugefügt werden, da sie nicht anpassbar ist|
> |**Name**:<br />CannotAddOrActonBehalfAnotherUserPrivilege<br />**Hex**:<br />8004Ed43<br />**Nummer**:<br />-2147160765|"Vorgänge im Namen anderer Benutzer ausführen"-Recht kann nicht hinzugefügt oder entfernt werden.|
> |**Name**:<br />CannotAddParentToAKit<br />**Hex**:<br />80061015<br />**Nummer**:<br />-2147086315|Sie können keinen übergeordneten Datensatz für einen Bausatz festlegen.|
> |**Name**:<br />CannotAddPricelistToProductFamily<br />**Hex**:<br />8004F902<br />**Nummer**:<br />-2147157758|Sie können einer Preisliste keine Produktfamilie hinzufügen.|
> |**Name**:<br />CannotAddProduct<br />**Hex**:<br />8004F908<br />**Nummer**:<br />-2147157752|Sie können nur aktive Produkte hinzufügen.|
> |**Name**:<br />CannotAddProductBundleToKit<br />**Hex**:<br />80061022<br />**Nummer**:<br />-2147086302|Sie können einem Bausatz kein Paket hinzufügen.|
> |**Name**:<br />CannotAddProductFamilyToKit<br />**Hex**:<br />80061023<br />**Nummer**:<br />-2147086301|Sie können einem Bausatz keine Produktfamilie hinzufügen.|
> |**Name**:<br />CannotAddProductToBundle<br />**Hex**:<br />8004F976<br />**Nummer**:<br />-2147157642|Sie können diesem Paket keine Produkte hinzufügen. Der Grenzwert von {0} ist für dieses Paket erreicht worden.|
> |**Name**:<br />CannotAddProductToKit<br />**Hex**:<br />80061024<br />**Nummer**:<br />-2147086300|Sie können kein Produkt, das zu einer Produktfamilie gehört, einem Bausatz hinzufügen.|
> |**Name**:<br />CannotAddProductToRetiredKit<br />**Hex**:<br />80061026<br />**Nummer**:<br />-2147086298|Sie können einem zurückgezogenen Bausatz kein Produkt hinzufügen.|
> |**Name**:<br />CannotAddQueueItemsToInactiveQueue<br />**Hex**:<br />80040522<br />**Nummer**:<br />-2147220190|Der ausgewählte Benutzer verfügt nicht über ausreichende Berechtigungen, um mit Elementen in dieser Warteschlange zu arbeiten.|
> |**Name**:<br />CannotAddRetiredProduct<br />**Hex**:<br />80061033<br />**Nummer**:<br />-2147086285|Sie können keine Produktbeziehung mit einem zurückgezogenen Produkt erstellen.|
> |**Name**:<br />CannotAddRetiredProductToKit<br />**Hex**:<br />80061027<br />**Nummer**:<br />-2147086297|Sie können einem Bausatz kein zurückgezogenes Produkt hinzufügen.|
> |**Name**:<br />CannotAddRetiredProductToPricelist<br />**Hex**:<br />80061009<br />**Nummer**:<br />-2147086327|Zurückgezogenen Produkte können keinen Preislisten hinzugefügt werden.|
> |**Name**:<br />CannotAddSingleQueueEnabledEntityToQueue<br />**Hex**:<br />8004051c<br />**Nummer**:<br />-2147220196|Der Entitätsdatensatz kann nicht zur Warteschlange hinzugefügt werden, da er bereits in anderen Warteschlange vorhanden ist.|
> |**Name**:<br />CannotAddSolutionComponentWithoutRoots <br />**Hex**:<br />8004F018<br />**Nummer**:<br />-2147160040|Dieses Element ist keine gültige Lösungskomponente. Weitere Informationen zu Lösungskomponenten finden Sie in der Microsoft Dynamics 365 SDK-Dokumentation.|
> |**Name**:<br />CannotAddUserToMobileOfflineProfile<br />**Hex**:<br />800609A6<br />**Nummer**:<br />-2147087962|Sie können diesen Benutzer nicht zu diesem Mobile Offline-Profil hinzufügen, da die Rolle des Benutzers entweder fehlt oder nicht über das Recht Dynamics 365 für Mobile verfügt.|
> |**Name**:<br />CannotAddWorkflowActivationToSolution <br />**Hex**:<br />8004F00C<br />**Nummer**:<br />-2147160052|Workflowaktivierung kann der Lösung nicht hinzugefügt werden |
> |**Name**:<br />CannotAssignAddressBookFilters<br />**Hex**:<br />80048448<br />**Nummer**:<br />-2147187640|Adressbuchfilter können nicht zugewiesen werden|
> |**Name**:<br />CannotAssignOfflineFilters<br />**Hex**:<br />800404ff<br />**Nummer**:<br />-2147220225|Offlinefilter können nicht zugewiesen werden|
> |**Name**:<br />CannotAssignOutlookFilters<br />**Hex**:<br />80040264<br />**Nummer**:<br />-2147220892|Outlook-Filter können nicht zugewiesen werden|
> |**Name**:<br />CannotAssignRolesOrProfilesToAccessTeam<br />**Hex**:<br />80048331<br />**Nummer**:<br />-2147187919|Rollen oder Profile können keinem Zugriffsteam zugeiwesen werden.|
> |**Name**:<br />CannotAssignRolesToSupportUser<br />**Hex**:<br />80041d51<br />**Nummer**:<br />-2147213999|Der Supportbenutzer ist schreibgeschützt, ihm können keine anderen Rollen zugewiesen werden.|
> |**Name**:<br />CannotAssignSupportUser<br />**Hex**:<br />80041d44<br />**Nummer**:<br />-2147214012|Ein Support-Benutzer kann keiner Supportbenutzerrolle zugewiesen werden.|
> |**Name**:<br />CannotAssignToAccessTeam<br />**Hex**:<br />80048340<br />**Nummer**:<br />-2147187904|Sie können keinen Datensatz einem Besitzersteam zuweisen. Sie können einen Datensatz einem Besitzersteam zuweisen.|
> |**Name**:<br />CannotAssignToDisabledBusiness<br />**Hex**:<br />8004032d<br />**Nummer**:<br />-2147220691|Definierte Unternehmenseinheiten können nicht der ausgewählten Unternehmenseinheit zugewiesen werden, da sie deaktiviert ist.|
> |**Name**:<br />CannotAssociateExternalPartyItem<br />**Hex**:<br />80061117<br />**Nummer**:<br />-2147086057|Sie können einem Entitätsdatensatz, der als externe Partei aktiviert wurde, nicht mehrere externe Parteielemente zuordnen.|
> |**Name**:<br />CannotAssociateInactiveItemToCampaign<br />**Hex**:<br />80040304<br />**Nummer**:<br />-2147220732|Ein inaktives Element kann nicht einer Kampagne zugeordnet werden.|
> |**Name**:<br />CannotAssociateInvalidEntityToProfileItem<br />**Hex**:<br />8006099B<br />**Nummer**:<br />-2147087973|Ungültiger Objekttypcode|
> |**Name**:<br />CannotAssociateProductFamily<br />**Hex**:<br />8004F999<br />**Nummer**:<br />-2147157607|Sie können keine Beziehung mit einer Produktfamilie erstellen.|
> |**Name**:<br />CannotAssociateRetiredBundles<br />**Hex**:<br />80081011<br />**Nummer**:<br />-2146955247|Sie können keine Produktbeziehung mit einem zurückgezogenen Paket erstellen.|
> |**Name**:<br />CannotAssociateRetiredProducts<br />**Hex**:<br />8004F974<br />**Nummer**:<br />-2147157644|Sie können keine Produktbeziehung mit einem zurückgezogenen Produkt erstellen.|
> |**Name**:<br />CannotBindToSession<br />**Hex**:<br />80040254<br />**Nummer**:<br />-2147220908|Bindung an eine andere Sitzung nicht möglich. Sitzung bereits gebunden.|
> |**Name**:<br />CannotCancelInvoice<br />**Hex**:<br />80100001<br />**Nummer**:<br />-2146435071|Die Rechnung kann nicht storniert werden, da sie sich nicht im aktiven oder bezahlten Status befindet.|
> |**Name**:<br />CannotChangeAccessModeForInternetMarketingUser<br />**Hex**:<br />80045035<br />**Nummer**:<br />-2147200971|Internetmarketing-Benutzer ist ein Systembenutzer. Sie können den Zugriffsmodus nicht ändern.|
> |**Name**:<br />CannotChangeAttributeRequiredLevel<br />**Hex**:<br />8004D293<br />**Nummer**:<br />-2147167597|Die erforderliche Stufe eines Attributes kann nicht aus SystemRequired geändert werden|
> |**Name**:<br />CannotChangeConvertRuleState<br />**Hex**:<br />800608F4<br />**Nummer**:<br />-2147088140|Fehler bei der Aktivierung von "Convert Rule". Überprüfen Sie Ihre Rechte für Workflow,s und versuchen Sie es erneut oder wenden Sie sich an den Systemadministrator.|
> |**Name**:<br />CannotChangeDaysSinceRecordLastModified<br />**Hex**:<br />800609A4<br />**Nummer**:<br />-2147087964|Sie müssen diese Entität für Mobile Offline aktivieren, bevor Sie die Anzahl der Tage seit der letzten Änderung des Datensatzes festlegen oder ändern können.|
> |**Name**:<br />CannotChangeInvitationStatusForInternetMarketingUser<br />**Hex**:<br />80045036<br />**Nummer**:<br />-2147200970|Internetmarketing-Benutzer ist ein Systembenutzer. Sie können den Einladungsstatus nicht ändern.|
> |**Name**:<br />CannotChangeProductRelationship<br />**Hex**:<br />80061013<br />**Nummer**:<br />-2147086317|Sie können die Produktbeziehung eines zurückgezogenen Produkts nicht hinzufügen oder ändern.|
> |**Name**:<br />CannotChangeSelectedBundleToAnotherValue<br />**Hex**:<br />8004F986<br />**Nummer**:<br />-2147157626|Wird ein Paket als vorhandenes Produkt ausgewählt, können Sie den Wert nicht ändern.|
> |**Name**:<br />CannotChangeSelectedProductWithBundle<br />**Hex**:<br />8004F987<br />**Nummer**:<br />-2147157625|Wird ein Produkt als vorhandenes Produkt ausgewählt, können Sie es nicht als Paket festlegen.|
> |**Name**:<br />CannotChangeState<br />**Hex**:<br />8004F863<br />**Nummer**:<br />-2147157917|Fehler bei der Aktivierung der SLA. Überprüfen Sie Ihre Rechte für Workflow,s und versuchen Sie es erneut oder wenden Sie sich an den Systemadministrator.|
> |**Name**:<br />CannotChangeStateOfNonpublicView<br />**Hex**:<br />80040279<br />**Nummer**:<br />-2147220871|Nur öffentliche Ansichten können deaktiviert und aktiviert werden.|
> |**Name**:<br />CannotChangeTeamTypeDueToOwnership<br />**Hex**:<br />80048337<br />**Nummer**:<br />-2147187913|Sie können den Typ eines Teams nicht ändern, weil die Datensätze dem Team gehören.|
> |**Name**:<br />CannotChangeTeamTypeDueToRoleOrProfile<br />**Hex**:<br />80048336<br />**Nummer**:<br />-2147187914|Sie können den Typ eines Teams nicht ändern, weil die Sicherheitsrollen und Feldsicherheitsprofile dem Team zugewiesen werden.|
> |**Name**:<br />CannotClearChannelPropertyGroupFromConvertRule<br />**Hex**:<br />800608ED<br />**Nummer**:<br />-2147088147|Die Kanal-Eigenschaftengruppe durchläuft eine oder mehrere Schritt. Löschen Sie die zunächst Eigenschaften aus den Bedingungen und Schritten, die für den Datensatz verwendet werden, bevor Sie die Regel speichern oder aktivieren.|
> |**Name**:<br />CannotCloneBundleAsProductLimitExceeded<br />**Hex**:<br />8004F985<br />**Nummer**:<br />-2147157627|Sie können dieses neue Paket nicht erstellen, da es mehr als die maximal zulässige Anzahl von {0} Produkten enthält.|
> |**Name**:<br />CannotCloneBundleWithRetiredProducts<br />**Hex**:<br />80061034<br />**Nummer**:<br />-2147086284|Sie können kein Paket klonen, das zurückgezogene Produkte enthält.|
> |**Name**:<br />CannotCloneProductKit<br />**Hex**:<br />80061020<br />**Nummer**:<br />-2147086304|Sie können keinen Bausatz klonen.|
> |**Name**:<br />CannotCloseCase<br />**Hex**:<br />8004F456<br />**Nummer**:<br />-2147158954|Vorgang kann nicht abgeschlossen werden. Mindestens eine untergeordnete Anfrage kann wegen der Regeln für den Statusübergang nicht geschlossen werden, die für Anfragen definiert sind.|
> |**Name**:<br />CannotConnectToSelf<br />**Hex**:<br />80048217<br />**Nummer**:<br />-2147188201|Ein Datensatz kann nicht mit sich selbst verbunden werden.|
> |**Name**:<br />CannotConvertBundleToKit<br />**Hex**:<br />80061030<br />**Nummer**:<br />-2147086288|Sie können ein Paket nicht in einen Bausatz konvertieren.|
> |**Name**:<br />CannotConvertProductAssociatedWithBundleToKit<br />**Hex**:<br />80061018<br />**Nummer**:<br />-2147086312|Sie können kein Produkt, das Teil eines Pakets ist, in einen Bausatz konvertieren.|
> |**Name**:<br />CannotConvertProductAssociatedWithFamilyToKit<br />**Hex**:<br />80061016<br />**Nummer**:<br />-2147086314|Sie können kein Produkt, das zu einer Produktfamilie gehört, in einen Bausatz konvertieren.|
> |**Name**:<br />CannotConvertProductFamilyToKit<br />**Hex**:<br />80061029<br />**Nummer**:<br />-2147086295|Sie können eine Produktfamilie nicht in einen Bausatz konvertieren.|
> |**Name**:<br />CannotCopyIncompatibleListType<br />**Hex**:<br />80040306<br />**Nummer**:<br />-2147220730|Listen verschiedener Typen können nicht kopiert werden.|
> |**Name**:<br />CannotCopyStaticList<br />**Hex**:<br />8004F704<br />**Nummer**:<br />-2147158268|Diese Aktion ist nur für dynamische Liste gültig.|
> |**Name**:<br />CannotCreateActivityRelationship<br />**Hex**:<br />80047006<br />**Nummer**:<br />-2147192826|Beziehungen mit Aktivitäten können mit diesem Vorgang nicht erstellt werden.|
> |**Name**:<br />CannotCreateAddressBookFilters<br />**Hex**:<br />80048447<br />**Nummer**:<br />-2147187641|Adressbuchfilter können nicht erstellt werden|
> |**Name**:<br />CannotCreateCase<br />**Hex**:<br />80060853<br />**Nummer**:<br />-2147088301|Sie können die Anfrage nicht erstellen, da der Standardanspruch für den bestimmten Kunden keine Restlaufzeit hat.|
> |**Name**:<br />CannotCreateComponentDefinition<br />**Hex**:<br />80072001<br />**Nummer**:<br />-2147016703|Die Erstellung einer neuen Komponentendefinition wird nicht unterstützt|
> |**Name**:<br />CannotCreateExternalPartyWithSameCorrelationKey<br />**Hex**:<br />80061112<br />**Nummer**:<br />-2147086062|Ein Datensatz für eine externe Partei ist bereits mit demselben Korrelationsschlüsselwert vorhanden.|
> |**Name**:<br />CannotCreateFromSupportUser<br />**Hex**:<br />80041d46<br />**Nummer**:<br />-2147214010|Aus der Supportbenutzerrolle kann keine Rolle erstellt werden.|
> |**Name**:<br />CannotCreateKitOfTypeFamilyOrBundle<br />**Hex**:<br />80061012<br />**Nummer**:<br />-2147086318|Sie können keinen Bausatz vom Typ "Paket" oder "Produktfamilie" erstellen.|
> |**Name**:<br />CannotCreateOrEnablePositionDueToParentPositionIsDisabled<br />**Hex**:<br />80048344<br />**Nummer**:<br />-2147187900|Es kann unter einer deaktivierten übergeordnete Position keine untergeordnete Position erstellt/aktiviert werden.|
> |**Name**:<br />CannotCreateOutlookFilters<br />**Hex**:<br />80040263<br />**Nummer**:<br />-2147220893|Outlook-Filter können nicht erstellt werden|
> |**Name**:<br />CannotCreatePluginInstance<br />**Hex**:<br />8004A201<br />**Nummer**:<br />-2147180031|Die Instanz eines Plug-Ins konnte nicht erstellt werden. Überprüfen Sie, ob steckbarer Typ nicht definiert wird, da Zusammenfassung und er einen öffentlichen Konstruktor haben, die von Dynamics 365-SDK unterstützt.|
> |**Name**:<br />CannotCreatePropertyOptionSetItem<br />**Hex**:<br />80081013<br />**Nummer**:<br />-2146955245|Sie können nur einen Optionssatzelement-Datensatz für Eigenschaften erstellen, der auf eine Eigenschaft mit dem Datentyp "Optionssatz" verweist.|
> |**Name**:<br />CannotCreateQueueItemInactiveObject<br />**Hex**:<br />8004051e<br />**Nummer**:<br />-2147220194|Ein deaktiviertes Objekt kann der Warteschlange nicht hinzugefügt werden.|
> |**Name**:<br />CannotCreateResponseForTemplate<br />**Hex**:<br />80040312<br />**Nummer**:<br />-2147220718|CampaignResponse kann nicht für Vorlagenkampagne erstellt werden.|
> |**Name**:<br />CannotCreateSLAForEntity<br />**Hex**:<br />80055005<br />**Nummer**:<br />-2147135483|Für diese Entität kann keine Vereinbarung zum Servicelevel (Service Level Agreement, SLA) erstellt werden, da die SLA-Erstellung für die Entität nicht aktiviert ist.|
> |**Name**:<br />CannotCreateSyncUserIsLicensedField<br />**Hex**:<br />80041d4d<br />**Nummer**:<br />-2147214003|Die Eigenschaft IsLicensed kann nicht für Synchronisierungs-Benutzer-Erstellung festgelegt werden.|
> |**Name**:<br />CannotCreateSyncUserObjectMissing<br />**Hex**:<br />80041d4b<br />**Nummer**:<br />-2147214005|Dies ist keine gültige Microsoft Online Services-ID für die Organisation.|
> |**Name**:<br />CannotCreateSystemOrDefaultTheme<br />**Hex**:<br />800608D5<br />**Nummer**:<br />-2147088171|Sie können System- oder Standarddesigns nicht erstellen. System- oder Standarddesign kann nur aus Feld erstellt werden.|
> |**Name**:<br />CannotCreateUpdateSourceAttribute<br />**Hex**:<br />80044804<br />**Nummer**:<br />-2147203068|Quellattribut ungültig für Erstellen/Aktualisieren, wenn Metriktyp Anzahl ist.|
> |**Name**:<br />CannotDeactivateDefaultView<br />**Hex**:<br />8004027a<br />**Nummer**:<br />-2147220870|Die Standardansichten können nicht deaktiviert werden.|
> |**Name**:<br />CannotDeactivateGuestProfile<br />**Hex**:<br />80061105<br />**Nummer**:<br />-2147086075|Sie können dieses Gastkanalzugriffsprofil nicht als inaktiv festlegen.|
> |**Name**:<br />CannotDefineMultipleValuesOnOwnerFieldInProfileItemEntityFilter<br />**Hex**:<br />80071129<br />**Nummer**:<br />-2147020503|Sie können nicht mehrere Werte in diesem Feld definieren.|
> |**Name**:<br />CannotDeleteActiveCaseCreationRule<br />**Hex**:<br />8004F880<br />**Nummer**:<br />-2147157888|Sie können eine aktive Regel nicht löschen. Deaktivieren Sie Datensatzerstellungs- und Aktualisierungsregel, und versuchen Sie dann, sie erneut zu löschen.|
> |**Name**:<br />CannotDeleteActiveRecordCreationRuleItem<br />**Hex**:<br />8004F894<br />**Nummer**:<br />-2147157868|Sie können ein aktives Rekorderstellungs-Regelelement nicht löschen. Deaktivieren Sie die Datensatzerstellungsregel und versuchen Sie dann, sie erneut zu löschen.|
> |**Name**:<br />CannotDeleteActiveRule<br />**Hex**:<br />8004F850<br />**Nummer**:<br />-2147157936|Sie können einen aktiven Weiterleitungsregelsatz nicht löschen. Deaktivieren Sie die Regel, um sie zu löschen.|
> |**Name**:<br />CannotDeleteActiveSla<br />**Hex**:<br />8004F870<br />**Nummer**:<br />-2147157904|Sie können ein aktives SLA nicht löschen. Deaktivieren Sie die SLA und versuchen Sie erneut, sie zu löschen.|
> |**Name**:<br />CannotDeleteAppModuleAdministration<br />**Hex**:<br />80050130<br />**Nummer**:<br />-2147155664|Diese App kann nicht gelöscht werden.|
> |**Name**:<br />CannotDeleteAppModuleClientType<br />**Hex**:<br />80050129<br />**Nummer**:<br />-2147155671|Diese App kann nicht gelöscht werden.|
> |**Name**:<br />CannotDeleteAsBackgroundOperationInProgress<br />**Hex**:<br />8004032b<br />**Nummer**:<br />-2147220693|Dieser Datensatz wird zurzeit von Microsoft Dynamics 365 verwendet und kann nicht gelöscht werden. Versuchen Sie es später noch einmal. Falls das Problem weiterhin besteht, wenden Sie sich an den Systemadministrator.|
> |**Name**:<br />CannotDeleteAsItIsReadOnly<br />**Hex**:<br />80040228<br />**Nummer**:<br />-2147220952|Das Objekt kann nicht gelöscht werden, da es schreibgeschützt ist.|
> |**Name**:<br />CannotDeleteAttributeUsedInWorkflow<br />**Hex**:<br />80045030<br />**Nummer**:<br />-2147200976|Dieses Attribut kann nicht gelöscht werden, da es in einem oder mehreren Workflows verwendet wird. Brechen Sie alle Systemaufträge für Workflows ab, die dieses Attribut verwenden, und löschen oder ändern Sie alle Workflows, die das Attribut verwenden, und versuchen Sie dann, das Attribut erneut zu löschen.|
> |**Name**:<br />CannotDeleteBaseMoneyCalculationAttribute<br />**Hex**:<br />80048cfe<br />**Nummer**:<br />-2147185410|Das Attribut für den Zahlungsberechnung ist ungültig für Löschung|
> |**Name**:<br />CannotDeleteCannedView<br />**Hex**:<br />8004022f<br />**Nummer**:<br />-2147220945|Systemdefinierte Ansichten können nicht gelöscht werden.|
> |**Name**:<br />CannotDeleteCDSUser<br />**Hex**:<br />80041d5a<br />**Nummer**:<br />-2147213990|Die Common Data Service-Benutzerrolle kann nicht gelöscht werden.|
> |**Name**:<br />CannotDeleteChannelAccessProfileRule<br />**Hex**:<br />80061108<br />**Nummer**:<br />-2147086072|Sie können keine aktive Kanalzugriffsprofilregel löschen. Deaktivieren Sie die Regel und löschen Sie sie anschließend.|
> |**Name**:<br />CannotDeleteChannelProperty<br />**Hex**:<br />800608EB<br />**Nummer**:<br />-2147088149|Sie können eine Kanaleigenschaft nicht löschen, die auf eine konvertierte Regel verweist.|
> |**Name**:<br />CannotDeleteChildAttribute<br />**Hex**:<br />80047016<br />**Nummer**:<br />-2147192810|Das untergeordnete Attribut ist ungültig für Löschung|
> |**Name**:<br />CannotDeleteCustomEntityUsedInWorkflow<br />**Hex**:<br />8004502C<br />**Nummer**:<br />-2147200980|Entität kann nicht gelöscht werden, da sie in einem Workflow verwendet wird.|
> |**Name**:<br />CannotDeleteDefaultProfile<br />**Hex**:<br />8006099A<br />**Nummer**:<br />-2147087974|Zum Löschen dieses Profils müssen Sie zunächst festlegen, dass es kein Mobile Offline-Standardprofil mehr ist.|
> |**Name**:<br />CannotDeleteDefaultStatusOption<br />**Hex**:<br />80044341<br />**Nummer**:<br />-2147204287|Optionen des standardmäßigen Status können nicht gelöscht werden.|
> |**Name**:<br />CannotDeleteDefaultTeam<br />**Hex**:<br />80048307<br />**Nummer**:<br />-2147187961|Das Standardteam der Unternehmenseinheit kann nicht gelöscht werden.|
> |**Name**:<br />CannotDeleteDueToAssociation<br />**Hex**:<br />80040227<br />**Nummer**:<br />-2147220953|Das Ziel, das Sie löschen wollten ist einem anderen Objekt zugeordnet und kann nicht gelöscht werden.|
> |**Name**:<br />CannotDeleteDueToBasketEntityAssociation<br />**Hex**:<br />80061612<br />**Nummer**:<br />-2147084782|Sie können eine Empfehlungsentität nicht löschen, wenn eine entsprechende Warenkorbentität existiert.|
> |**Name**:<br />CannotDeleteDynamicPropertyInRetiredState<br />**Hex**:<br />8004F892<br />**Nummer**:<br />-2147157870|Sie können keine Eigenschaft eines zurückgezogenen Produkts löschen.|
> |**Name**:<br />CannotDeleteDynamicPropertyInUse<br />**Hex**:<br />80081003<br />**Nummer**:<br />-2146955261|Eigenschaften die im Ruhestand in Transaktionen verwendet werden, können nicht gelöscht werden.|
> |**Name**:<br />CannotDeleteEnumOptionsFromAttributeType<br />**Hex**:<br />80044323<br />**Nummer**:<br />-2147204317|Sie können Optionswerte nur von Auswahlliste und Statusattributen löschen.|
> |**Name**:<br />CannotDeleteGuestProfile<br />**Hex**:<br />80061104<br />**Nummer**:<br />-2147086076|Sie können dieses Gastkanalzugriffsprofil nicht löschen.|
> |**Name**:<br />CannotDeleteInheritedDynamicProperty<br />**Hex**:<br />80081014<br />**Nummer**:<br />-2146955244|Sie können keine Eigenschaft löschen, die von einer Produktfamilie geerbt wird.|
> |**Name**:<br />CannotDeleteInUseAttribute<br />**Hex**:<br />80048418<br />**Nummer**:<br />-2147187688|Das ausgewählte Attribut kann nicht gelöscht werden, da mindestens eine Duplikaterkennungsregel, die gerade veröffentlicht wird, auf dieses Feld verweist.|
> |**Name**:<br />CannotDeleteInUseComponent<br />**Hex**:<br />8004F01F<br />**Nummer**:<br />-2147160033|Die {0}({1}) Komponente kann nicht gelöscht werden, da sie von {2} oder anderen Komponenten verwiesen wird. Für eine Liste der referenzierten Komponenten verwenden Sie RetrieveDependenciesForDeleteRequest.|
> |**Name**:<br />CannotDeleteInUseEntity<br />**Hex**:<br />80048420<br />**Nummer**:<br />-2147187680|Die ausgewählte Entität kann nicht gelöscht werden, da mindestens eine Duplikaterkennungsregel, die gerade veröffentlicht wird, auf diese Entität verweist.|
> |**Name**:<br />CannotDeleteInUseOptionSet<br />**Hex**:<br />80048417<br />**Nummer**:<br />-2147187689|Dieser Optionssatz kann nicht gelöscht werden. Die aktuellen Entitäten die auf diesen Optionssatz verweisen sind: {0}. Diese Verweise müssen entfernt werden, damit dieser Optionssatz gelöscht werden kann|
> |**Name**:<br />CannotDeleteLastEmailAttribute<br />**Hex**:<br />80046FFF<br />**Nummer**:<br />-2147192833|Sie können das Feld nicht löschen, da der Datensatz für die E-Mail aktiviert wurde.|
> |**Name**:<br />CannotDeleteMetadata<br />**Hex**:<br />8004F032<br />**Nummer**:<br />-2147160014|Der Vorgang {2} auf der aktuellen Komponente{0}(name=, id={1}) ist bei der Verwaltung der Eigenschaftenauswertung der Bedingung fehlgeschlagen: {3}|
> |**Name**:<br />CannotDeleteMetricWithGoals<br />**Hex**:<br />80044800<br />**Nummer**:<br />-2147203072|Diese Zielmetrik wird von mindestens einem Ziel verwendet und kann nicht gelöscht werden.|
> |**Name**:<br />CannotDeleteNonLeafNode<br />**Hex**:<br />8004F200<br />**Nummer**:<br />-2147159552|Nur eine Blattbestimmung kann gelöscht werden. Diese Bestimmung ist einer anderenn Bestimmung übergeordnet.|
> |**Name**:<br />CannotDeleteNotOwnedDynamicProperty<br />**Hex**:<br />80081006<br />**Nummer**:<br />-2146955258|Sie können keine Dynamic Eigenschaft löschen, die von einer Produktfamilie geerbt wird.|
> |**Name**:<br />CannotDeleteOneNoteTableOfContent<br />**Hex**:<br />800608B7<br />**Nummer**:<br />-2147088201|Diese Datei können Sie nicht löschen, da diese Links zu den OneNote-Notebookabschnitten enthält. Klicken Notebookinhalte löschen möchten, öffnen Sie das Notebook in OneNote und löschen Sie die Inhalte von dort. Um ein Notebook zu löschen, öffnen Sie SharePoint und löschen dort das Notebook.|
> |**Name**:<br />CannotDeleteOnlineRecord<br />**Hex**:<br />8005F248<br />**Nummer**:<br />-2147093944|Dieser Datensatz kann nicht gelöscht werden, da er im Offlinemodus nicht vorhanden ist.|
> |**Name**:<br />CannotDeleteOptionSet<br />**Hex**:<br />80048404<br />**Nummer**:<br />-2147187708|Das ausgewählte OptionSet kann nicht gelöscht werden.|
> |**Name**:<br />CannotDeleteOrCancelSystemJobs<br />**Hex**:<br />80044F02<br />**Nummer**:<br />-2147201278|Sie können den Systemauftrag nicht abbrechen oder nicht löschen, da es vom System erforderlich ist. Sie können diesen Auftrag nur fortsetzen, zurückstellen oder anhalten.|
> |**Name**:<br />CannotDeleteOverriddenProperty<br />**Hex**:<br />80081100<br />**Nummer**:<br />-2146955008|Sie können diese Eigenschaft nicht löschen, da sie für eine oder mehrere untergeordnete Datensätze überschrieben ist. Entfernen Sie die überschriebenen Versionen der Eigenschaft, veröffentlichen Sie die Produktfamilienhierarchie, und versuchen Sie dann erneut, die angezeigten zu löschen.|
> |**Name**:<br />CannotDeletePartnerSolutionWithOrganizations<br />**Hex**:<br />8004A10e<br />**Nummer**:<br />-2147180274|Partnerlösung kann nicht gelöscht werden, da mindestens eine Organisation damit verbunden sind|
> |**Name**:<br />CannotDeletePartnerWithPartnerSolutions<br />**Hex**:<br />8004A10d<br />**Nummer**:<br />-2147180275|Partner kann nicht gelöscht werden, da mindestens eine Lösung damit verbunden sind|
> |**Name**:<br />CannotDeletePrimaryUIAttribute<br />**Hex**:<br />80047002<br />**Nummer**:<br />-2147192830|Das primäre UI-Attribut ist ungültig für Löschung|
> |**Name**:<br />CannotDeleteProductFromActiveBundle<br />**Hex**:<br />80061010<br />**Nummer**:<br />-2147086320|Sie können keine Produkte aus einem Paket entfernen, das aktiv ist oder überarbeitet wird.|
> |**Name**:<br />CannotDeleteProductStatusCode<br />**Hex**:<br />80081016<br />**Nummer**:<br />-2146955242|Sie können keinen vom System generierten Statusgrund löschen.|
> |**Name**:<br />CannotDeleteProfileWithExternalPartyItem<br />**Hex**:<br />80061107<br />**Nummer**:<br />-2147086073|Sie können dieses Kanalzugriffsprofil nicht löschen, weil es einem externen Parteielement zugeordnet ist. Entfernen Sie die Zuordnung, und versuchen Sie es anschließend erneut.|
> |**Name**:<br />CannotDeleteProfileWithProfileRules<br />**Hex**:<br />80061106<br />**Nummer**:<br />-2147086074|Sie können dieses Kanalzugriffsprofil nicht löschen, da es von mindestens einer Kanalzugriffsprofilregel verwendet wird. Entfernen Sie das Profil mit den Kanalzugriffsprofilregeln, und versuchen Sie es anschließend erneut.|
> |**Name**:<br />CannotDeletePropertyOverriddenByBundleItem<br />**Hex**:<br />80081015<br />**Nummer**:<br />-2146955243|Sie können diese Eigenschaft nicht löschen, da sie für eine oder mehrere verwandte Produktpakete überschrieben ist. Entfernen Sie die überschriebenen Versionen der Eigenschaft der verknüpften Paketprodukte, veröffentlichen Sie die Pakete, die geändert wurden, und versuchen Sie es anschließend erneut.|
> |**Name**:<br />CannotDeleteQueueWithQueueItems<br />**Hex**:<br />80631117<br />**Nummer**:<br />-2140991209|Sie können diese Warteschlange nicht löschen, da sie Artikel hat, die ihr zugewiesen sind. Weisen Sie diesen Elementen einem anderen Benutzer, Team oder Warteschlange zu und versuchen Sie es erneut.|
> |**Name**:<br />CannotDeleteQueueWithRouteRules<br />**Hex**:<br />80731118<br />**Nummer**:<br />-2139942632|Sie können diese Warteschlange nicht löschen, weil mindestens ein Routingregelsatz diese Warteschlange verwendet. Entfernen Sie die Warteschlange aus den Routingregelsätzen und versuchen Sie es erneut.|
> |**Name**:<br />CannotDeleteRelatedSla<br />**Hex**:<br />8004F859<br />**Nummer**:<br />-2147157927|Der SLA-Datensatz konnte nicht gelöscht werden. Versuchen Sie es erneut, oder wenden Sie sich an den Systemadministrator.|
> |**Name**:<br />CannotDeleteRestrictedPublisher<br />**Hex**:<br />8004F006<br />**Nummer**:<br />-2147160058|Es wird versucht, einen eingeschränkten Herausgeber zu löschen.|
> |**Name**:<br />CannotDeleteRestrictedSolution<br />**Hex**:<br />8004F005<br />**Nummer**:<br />-2147160059|Es wird versucht, eine eingeschränkten Lösung zu löschen.|
> |**Name**:<br />CannotDeleteSupportUser<br />**Hex**:<br />80041d42<br />**Nummer**:<br />-2147214014|Die Supportbenutzerrolle kann nicht gelöscht werden.|
> |**Name**:<br />CannotDeleteSysAdmin<br />**Hex**:<br />80041d2e<br />**Nummer**:<br />-2147214034|Die Systemadministratorrolle kann nicht gelöscht werden.|
> |**Name**:<br />CannotDeleteSystemCustomizer<br />**Hex**:<br />80041d4a<br />**Nummer**:<br />-2147214006|Die Systemanpasser-Rolle kann nicht gelöscht werden.|
> |**Name**:<br />CannotDeleteSystemEmailTemplate<br />**Hex**:<br />80048432<br />**Nummer**:<br />-2147187662|System-E-Mail-Vorlagen können nicht gelöscht werden.|
> |**Name**:<br />CannotDeleteSystemForm<br />**Hex**:<br />8004F652<br />**Nummer**:<br />-2147158446|Systemformulare können nicht gelöscht werden.|
> |**Name**:<br />CannotDeleteSystemTheme<br />**Hex**:<br />800608DA<br />**Nummer**:<br />-2147088166|Das Löschen von Systemdesigns ist nicht möglich.|
> |**Name**:<br />CannotDeleteTeamOwningRecords<br />**Hex**:<br />8004830E<br />**Nummer**:<br />-2147187954|Kann kein Team löschen, das Datensätze besitzt. Weisen Sie die Datensätze erneut zu und versuchen Sie es erneut.|
> |**Name**:<br />CannotDeleteUpdateInUseRule<br />**Hex**:<br />80048428<br />**Nummer**:<br />-2147187672|Die Duplikaterkennungsregel wird zurzeit verwendet und kann nicht aktualisiert oder gelöscht werden. Bitte versuchen Sie es später erneut.|
> |**Name**:<br />CannotDeleteUserMailbox<br />**Hex**:<br />8005E200<br />**Nummer**:<br />-2147098112|Ein Postfach, das einem Benutzer oder einer Warteschlange zugeordnet ist, kann nicht gelöscht werden.|
> |**Name**:<br />CannotDeleteUserProfile<br />**Hex**:<br />800609A3<br />**Nummer**:<br />-2147087965|Sie können ein aktives Mobile Offline Profil nicht löschen. Entfernen Sie alle Benutzer im Profil und versuchen Sie es erneut.|
> |**Name**:<br />CannotDeserializeRequest<br />**Hex**:<br />8004416f<br />**Nummer**:<br />-2147204753|Die SDK-Anforderung konnte nicht deserialisiert werden.|
> |**Name**:<br />CannotDeserializeWorkflowInstance<br />**Hex**:<br />8004501F<br />**Nummer**:<br />-2147200993|Workflowinstanz kann nicht deserialisiert werden. Ein möglicher Grund für diesen Fehler ist ein Workflow, der eine benutzerdefinierte Aktivität verweist, deren Registrierung aufgehoben wurde.|
> |**Name**:<br />CannotDeserializeXamlWorkflow<br />**Hex**:<br />80045020<br />**Nummer**:<br />-2147200992|XAML, due für den Workflows steht, kann nicht in ein DynamicActivity deserialisiert werden.|
> |**Name**:<br />CannotDisableAutoCreateAccessTeams<br />**Hex**:<br />80048338<br />**Nummer**:<br />-2147187912|Sie können die Einstellung zur automatischen Erstellung von Zugriffsteams für eine Entität nicht deaktivieren, wenn zugeordnete Teamvorlagen vorhanden sind.|
> |**Name**:<br />CannotDisableDuplicateDetection<br />**Hex**:<br />80048462<br />**Nummer**:<br />-2147187614|Die Duplikaterkennung kann nicht deaktiviert werden, da gerade ein Duplikaterkennungsauftrag ausgeführt wird. Versuchen Sie es später noch einmal.|
> |**Name**:<br />CannotDisableInternetMarketingUser<br />**Hex**:<br />80045033<br />**Nummer**:<br />-2147200973|Sie können den Internetmarketing-Partnerbenutzer nicht deaktivieren. Der Benutzer vom Typ "Internetmarketingpartner" kann nicht deaktiviert werden. Für diesen Benutzer wird keine Benutzerlizenz benötigt, und er wird Ihrer Organisation nicht in Rechnung gestellt.|
> |**Name**:<br />CannotDisableMobileOfflineFlagForEntity<br />**Hex**:<br />800609A5<br />**Nummer**:<br />-2147087963|Sie können das Kennzeichen der Mobile Offline-Funktion für diese Entität nicht deaktivieren, da sie Mobile Offline-Profilen verwendet wird.|
> |**Name**:<br />CannotDisableMobileOfflineFlagForImportEntity<br />**Hex**:<br />80071111<br />**Nummer**:<br />-2147020527|Sie können Mobile Offline für die Entität {0} nicht mithilfe des Lösungsimports deaktivieren. Wenn Sie diese Entität nicht im Offlinemodus verwenden möchten, entfernen Sie die Flagge für „Für Mobile Offline-Funktion aktivieren” vom Anpassungsbildschirm|
> |**Name**:<br />CannotDisableOrDeletePositionDueToAssociatedUsers<br />**Hex**:<br />80048343<br />**Nummer**:<br />-2147187901|Diese Position kann erst nach dem Entfernen aller zugeordneten Benutzer gelöscht werden.|
> |**Name**:<br />CannotDisableRelevanceSearchManagedProperty<br />**Hex**:<br />80060303<br />**Nummer**:<br />-2147089661|Die {0} Entität synchronisiert gerade einen externen Search-Index.  Sie müssen die Entität aus dem externen Suchindex entfernen, bevor Sie die Eigenschaft "Kann Synchronisierung mit externem Suchindex aktivieren" auf False festlegen.|
> |**Name**:<br />CannotDisableSysAdmin<br />**Hex**:<br />80041d2f<br />**Nummer**:<br />-2147214033|Ein Benutzer kann nicht deaktiviert werden, wenn es sich bei dem Benutzer um den einzigen Benutzer mit der Systemadministratorrolle handelt.|
> |**Name**:<br />CannotDisableTenantAdmin<br />**Hex**:<br />80041d65<br />**Nummer**:<br />-2147213979|Benutzer, denen die Rolle globaler Microsoft Office 365-Administrator oder -Dienstadministrator erteilt wurde, können in Microsoft Dynamics 365 Online nicht deaktiviert werden. Sie müssen die Microsoft Office 365-Rolle zuerst entfernen. Versuchen Sie es dann erneut.|
> |**Name**:<br />CannotEditActiveRule<br />**Hex**:<br />8004F851<br />**Nummer**:<br />-2147157935|Sie können einen aktiven Weiterleitungsregelsatz nicht bearbeiten. Deaktivieren Sie die Regel, um sie zu löschen.|
> |**Name**:<br />CannotEditActiveSla<br />**Hex**:<br />8004F860<br />**Nummer**:<br />-2147157920|Sie können eine aktive Vereinbarung zum Servicelevel (SLA) nicht löschen. Deaktivieren Sie sie, um sie löschen zu können, oder wenden Sie sich an den Systemadministrator.|
> |**Name**:<br />CannotEnableDuplicateDetection<br />**Hex**:<br />80048421<br />**Nummer**:<br />-2147187679|Die Duplikaterkennung kann nicht aktiviert werden, da mindestens eine Regel gerade veröffentlicht wird.|
> |**Name**:<br />CannotEnableEntityForRelevanceSearch<br />**Hex**:<br />80060302<br />**Nummer**:<br />-2147089662|Die Entität {0} kann aufgrund der Konfiguration der verwalteten Eigenschaften nicht für die Relevanzsuche aktiviert werden.|
> |**Name**:<br />CannotExceedFilterLimit<br />**Hex**:<br />8004027c<br />**Nummer**:<br />-2147220868|Synchronisierungsfiltergrenze kann nicht überschritten werden.|
> |**Name**:<br />CannotExecuteRequestBecauseHttpsIsRequired<br />**Hex**:<br />8004852C<br />**Nummer**:<br />-2147187412|HTTPS-Protokoll ist für diesen Typ der Anforderung erforderlich, aktivieren Sie HTTPS-Protokoll, und versuchen Sie es noch einmal.|
> |**Name**:<br />CannotFindDomainAccount<br />**Hex**:<br />80044342<br />**Nummer**:<br />-2147204286|Ungültiges Domänenkonto|
> |**Name**:<br />CannotFindObjectInQueue<br />**Hex**:<br />800404eb<br />**Nummer**:<br />-2147220245|Das Ziel in der betreffenden Warteschlange wurde nicht gefunden|
> |**Name**:<br />CannotFindUserQueue<br />**Hex**:<br />800404ec<br />**Nummer**:<br />-2147220244|Benutzerwarteschlange kann nicht gefunden werden|
> |**Name**:<br />CannotFollowInactiveEntity<br />**Hex**:<br />8004F6A3<br />**Nummer**:<br />-2147158365|Dem inaktiven Datensatz kann nicht gefolgt werden. |
> |**Name**:<br />CannotGrantAccessToAddressBookFilters<br />**Hex**:<br />80048446<br />**Nummer**:<br />-2147187642|Zugriff auf die Adressbuchfilter kann nicht gewährt werden|
> |**Name**:<br />CannotGrantAccessToOfflineFilters<br />**Hex**:<br />80040271<br />**Nummer**:<br />-2147220879|Zugriff auf die Offlinefilter kann nicht gewährt werden|
> |**Name**:<br />CannotGrantAccessToOutlookFilters<br />**Hex**:<br />80040268<br />**Nummer**:<br />-2147220888|Zugriff auf die Outlookfilter kann nicht gewährt werden|
> |**Name**:<br />CannotHaveDuplicateYomi<br />**Hex**:<br />80047018<br />**Nummer**:<br />-2147192808|Ein Attribut kann nur an einen yomi gleichzeitig gebunden werden|
> |**Name**:<br />CannotHaveMultipleDefaultFilterTemplates<br />**Hex**:<br />8004027d<br />**Nummer**:<br />-2147220867|Mehrere Standardsynchronisierungsvorlagen für eine einzelne Entität sind nicht möglich.|
> |**Name**:<br />CannotImportNullStringsForBaseLanguage<br />**Hex**:<br />80044246<br />**Nummer**:<br />-2147204538|Die Ausgangssprachen-Übersetzungszeichenfolge, die im Arbeitsblatt vorhanden ist, {0}Zeile {1}, Spalte {2} ist null.|
> |**Name**:<br />CannotInviteDisabledUser<br />**Hex**:<br />8004D212<br />**Nummer**:<br />-2147167726|Eine Einladung kann einem deaktivierten Benutzer nicht gesendet werden|
> |**Name**:<br />CannotLocateRecordForWorkflowActivity<br />**Hex**:<br />80045031<br />**Nummer**:<br />-2147200975|Ein für diesen Workfolwauftrag erforderlicher Datensatz wurde nicht gefunden.|
> |**Name**:<br />CannotMakeReadOnlyUser<br />**Hex**:<br />80041d38<br />**Nummer**:<br />-2147214024|Einem Benutzer kann nicht nur schreibgeschützter Zugriff gewährt werden wenn es sich bei dem Benutzer um den einzigen Benutzer mit der Systemadministratorrolle handelt.|
> |**Name**:<br />CannotMakeSelfReadOnlyUser<br />**Hex**:<br />80041d39<br />**Nummer**:<br />-2147214023|Sie können auch sich selber zu einem schreibgeschützten Benutzer machen.|
> |**Name**:<br />CannotMergeCase<br />**Hex**:<br />8004F457<br />**Nummer**:<br />-2147158953|Der Seriendruck kann nicht ausgeführt wird. Mindestens eine ausgewählte Anfrage kann wegen der Regeln für den Statusübergang nicht abgebrochen werden, die für Anfragen definiert sind.|
> |**Name**:<br />CannotModifyAccessToAddressBookFilters<br />**Hex**:<br />80048445<br />**Nummer**:<br />-2147187643|Zugriff auf die Adressbuchfilter kann nicht geändert werden|
> |**Name**:<br />CannotModifyAccessToOfflineFilters<br />**Hex**:<br />80040272<br />**Nummer**:<br />-2147220878|Zugriff auf die Offlinefilter kann nicht geändert werden|
> |**Name**:<br />CannotModifyAccessToOutlookFilters<br />**Hex**:<br />80040269<br />**Nummer**:<br />-2147220887|Zugriff auf die Outlookfilter kann nicht geändert werden|
> |**Name**:<br />CannotModifyOldDataFromImport<br />**Hex**:<br />80040376<br />**Nummer**:<br />-2147220618|Der entsprechende Datensatz in Microsoft Dynamics 365 hat aktuellere Daten, sodass dieser Datensatz ignoriert wurde.|
> |**Name**:<br />CannotModifyPatchedSolution<br />**Hex**:<br />80048538<br />**Nummer**:<br />-2147187400|Lösung kann nicht geändert werden, da sie über die folgenden Patches verfügt: {0}.|
> |**Name**:<br />CannotModifyReportOutsideSolutionIfManaged<br />**Hex**:<br />8004F038<br />**Nummer**:<br />-2147160008|Die verwaltete Lösung kann keine Berichte aktualisieren, die nicht im Lösungspaket vorhanden sind.|
> |**Name**:<br />CannotModifyRollupDependentField<br />**Hex**:<br />80060555<br />**Nummer**:<br />-2147089067|Rollupfeld {0} erstellte dieses Feld. Es kann nicht direkt geändert werden.|
> |**Name**:<br />CannotModifySpecialUser<br />**Hex**:<br />80041d33<br />**Nummer**:<br />-2147214029|Keine Änderungen an "SYSTEM"- oder "INTEGRATION"-Benutzer zulässig.|
> |**Name**:<br />CannotModifySupportUser<br />**Hex**:<br />80041d43<br />**Nummer**:<br />-2147214013|Die Supportbenutzerrolle kann nicht geändet werden.|
> |**Name**:<br />CannotModifySysAdmin<br />**Hex**:<br />80041d31<br />**Nummer**:<br />-2147214031|Die Systemadministratorrolle kann nicht bearbeitet werden.|
> |**Name**:<br />CannotOverrideOwnedDynamicProperty<br />**Hex**:<br />80081005<br />**Nummer**:<br />-2146955259|Sie können keine Eigenschaft überschreiben, die von einer Produktfamilie geerbt wird.|
> |**Name**:<br />CannotOverrideProperty<br />**Hex**:<br />8004F887<br />**Nummer**:<br />-2147157881|Sie können diese Eigenschaft nicht als eine andere Version überschreiben, da diese Eigenschaft bereits vorhanden ist. Löschen Sie die zuvor überschriebene Version, und versuchen Sie es anschließend erneut.|
> |**Name**:<br />CannotOverridePropertyFromDifferentHierarchy<br />**Hex**:<br />8004F914<br />**Nummer**:<br />-2147157740|Sie können keine Eigenschaft überschreiben, die zu einer anderen Produkthierarchie gehört.|
> |**Name**:<br />CannotOverwriteActiveComponent<br />**Hex**:<br />8004F016<br />**Nummer**:<br />-2147160042|Eine verwaltete Lösung kann die {0}-Komponent {1} nicht mit Id={2} überschrieben werden, die eine nicht verwalte Basisinstanz hat.  Das höchstwahrscheinliche Szenario für diesen Fehler ist, dass eine nicht verwalte Lösung eine neue nicht verwaltete Komponenten auf {0} dem Zielsystem eingerichtet hat, und nun von einer verwalteten Lösung vom gleichen Herausgeber, dass dasselbe Komponente {0} als verwaltete zu installieren.  Dadurch wird eine ungültige Überlagerung von Lösungen auf dem Zielsystem nicht erlaubt.|
> |**Name**:<br />CannotOverwriteProperty<br />**Hex**:<br />80061036<br />**Nummer**:<br />-2147086282|Sie können diese Eigenschaft nicht als eine andere Version überschreiben, da diese Eigenschaft bereits vorhanden ist. Löschen Sie die zuvor überschriebene Version, und versuchen Sie es anschließend erneut.|
> |**Name**:<br />CannotPayNonActiveInvoice<br />**Hex**:<br />80100000<br />**Nummer**:<br />-2146435072|Die Rechnung kann nicht bezahlt werden, da sie sich nicht im aktiven Status befindet.|
> |**Name**:<br />CannotPropagateCamapaignActivityForTemplate<br />**Hex**:<br />80040311<br />**Nummer**:<br />-2147220719|CampaignActivity kann nicht für eine Vorlagen-Kampagne ausgeführt (bereitgestellt) werden.|
> |**Name**:<br />CannotProvisionPartnerSolution<br />**Hex**:<br />8004A10f<br />**Nummer**:<br />-2147180273|Partnerslösung kann nicht bereitgestellt werden, da diese entweder bereits bereitgestellt ist oder die Bereitstellung derzeit durchläuft.|
> |**Name**:<br />CannotPublishAppModule<br />**Hex**:<br />80050114<br />**Nummer**:<br />-2147155692|Die App konnte aufgrund von Überprüfungsfehlern nicht veröffentlicht werden.|
> |**Name**:<br />CannotPublishBundleWithProductStateDraftOrRetire<br />**Hex**:<br />8004F907<br />**Nummer**:<br />-2147157753|Sie können dieses Paket nicht veröffentlichen, da die zugeordneten Produkte im Entwurfsstatus vorliegen, zurückgezogen wurden oder überarbeitet werden.|
> |**Name**:<br />CannotPublishChildOfNonActiveProductFamily<br />**Hex**:<br />8004F909<br />**Nummer**:<br />-2147157751|Sie können diesen Datensatz nicht veröffentlichen, da er zu einer Produktfamilie gehört, die nicht veröffentlicht wurde.|
> |**Name**:<br />CannotPublishEmptyRule<br />**Hex**:<br />80048414<br />**Nummer**:<br />-2147187692|Es wurden keine Kriterien angegeben. Fügen Sie Kriterien hinzu, und veröffentlichen Sie dann die Duplikaterkennungsregel.|
> |**Name**:<br />CannotPublishInactiveRule<br />**Hex**:<br />80048413<br />**Nummer**:<br />-2147187693|Die ausgewählte Duplikaterkennungsregel ist als inaktiv markiert. Vor der Veröffentlichung müssen Sie die Regel aktivieren.|
> |**Name**:<br />CannotPublishKitWithProductStateDraftOrRetire<br />**Hex**:<br />8004F916<br />**Nummer**:<br />-2147157738|Sie können diesen Bausatz nicht veröffentlichen, da die zugeordneten Produkte im Entwurfsstatus vorliegen, zurückgezogen wurden oder überarbeitet werden.|
> |**Name**:<br />CannotPublishMoreRules<br />**Hex**:<br />80048419<br />**Nummer**:<br />-2147187687|Der ausgewählte Datensatztyp verfügt bereits über die maximale Anzahl von veröffentlichten Regeln. Aufheben der Veröffentlichung oder löschen Sie die vorhandenen Regeln für den Datensatztyp, und versuchen Sie es anschließend erneut.|
> |**Name**:<br />CannotPublishNestedBundle<br />**Hex**:<br />80061011<br />**Nummer**:<br />-2147086319|Sie können kein Paket veröffentlichen, das dieses Paket enthält. Entfernen Sie alle von diesem Download, und versuchen Sie dann, erneut zu veröffentlichen.|
> |**Name**:<br />CannotQualifyLead<br />**Hex**:<br />80081018<br />**Nummer**:<br />-2146955240|Sie können diesen Lead nicht qualifizieren, da Sie nicht berechtigt sind, Firmen zu erstellen. Arbeiten Sie mit Ihrem Systemadministrator, damit das Konto erstellt werden kann und versuchen Sie es erneut.|
> |**Name**:<br />CannotQueryBaseTableWithAggregates<br />**Hex**:<br />8004F00D<br />**Nummer**:<br />-2147160051|Ungültige Abfrage auf Basistabelle.  Aggregate können nicht in der Basistabellenabfrage eingefügt werden.|
> |**Name**:<br />CannotRelateObjectTypeToCampaign<br />**Hex**:<br />80040307<br />**Nummer**:<br />-2147220729|Angegebener Objekttyp wird nicht unterstützt|
> |**Name**:<br />CannotRelateObjectTypeToCampaignActivity<br />**Hex**:<br />8004030d<br />**Nummer**:<br />-2147220723|Angegebener Objekttyp wird nicht unterstützt|
> |**Name**:<br />CannotRemoveComponentFromDefaultSolution<br />**Hex**:<br />8004F000<br />**Nummer**:<br />-2147160064|Eine Lösungskomponente kann nicht aus der Standardlösung entfernt werden.|
> |**Name**:<br />CannotRemoveComponentFromSolution<br />**Hex**:<br />8004F021<br />**Nummer**:<br />-2147160031|Lösungskomponente {0} {1} kann in Lösung {2} nicht gefunden werden.|
> |**Name**:<br />CannotRemoveComponentFromSystemSolution<br />**Hex**:<br />8004F035<br />**Nummer**:<br />-2147160011|Eine Lösungskomponente kann nicht aus der Systemlösung entfernt werden.|
> |**Name**:<br />CannotRemoveFromSupportUser<br />**Hex**:<br />80041d45<br />**Nummer**:<br />-2147214011|Ein Benutzer kann aus der Supportbenutzerrolle nicht entfernt werden.|
> |**Name**:<br />CannotRemoveFromSysAdmin<br />**Hex**:<br />80041d30<br />**Nummer**:<br />-2147214032|Ein Benutzer kann aus der Systemadministratorrolle nicht entfernt werden, wenn es sich bei dem Benutzer um den einzigen Benutzer mit der Rolle handelt.|
> |**Name**:<br />CannotRemoveMembersFromDefaultTeam<br />**Hex**:<br />8004830C<br />**Nummer**:<br />-2147187956|Kann vom Standardunternehmenseinheitsteam keine Mitglieder entfernen.|
> |**Name**:<br />CannotRemoveNonListMember<br />**Hex**:<br />80048458<br />**Nummer**:<br />-2147187624|Das angegebene Element ist kein Mitglied der angegebenen Liste.|
> |**Name**:<br />CannotRemoveProductFromPricelist<br />**Hex**:<br />80061008<br />**Nummer**:<br />-2147086328|Sie können dieses Produkt nicht von der Preisliste entfernen, weil mindestens ein Paket darauf verweist.|
> |**Name**:<br />CannotRemoveSysAdminProfileFromSysAdminUser<br />**Hex**:<br />8004F505<br />**Nummer**:<br />-2147158779|Das sys-Administrator-Profil kann nur von einem Benutzer mit einer Sys-Administrator-Rolle entfernt werden|
> |**Name**:<br />CannotRemoveTenantAdminFromSysAdminRole<br />**Hex**:<br />80041d64<br />**Nummer**:<br />-2147213980|Benutzer, denen die Rolle globaler Microsoft Office 365-Administrator oder -Dienstadministrator erteilt wurde, können nicht aus der Sicherheitsrolle vom Microsoft Dynamics 365-Systemadministrator entfernt werden. Sie müssen die Microsoft Office 365-Rolle zuerst entfernen. Versuchen Sie es dann erneut.|
> |**Name**:<br />CannotResetAppointmentsToDraft<br />**Hex**:<br />8004026a<br />**Nummer**:<br />-2147220886|Termine können nicht in einen Entwurf zurückgesetzt werden.|
> |**Name**:<br />CannotResetSysAdminInvite<br />**Hex**:<br />8004D214<br />**Nummer**:<br />-2147167724|Das Zurücksetzen einer Einladung für einen Benutzer ist nicht möglich, wenn es sich bei dem Benutzer um den einzigen Benutzer mit der Systemadministratorrolle handelt.|
> |**Name**:<br />CannotRetireProduct<br />**Hex**:<br />8004F915<br />**Nummer**:<br />-2147157739|Sie können dieses Produkt nicht zurückziehen, da aktiven Paketen oder Preislisten dazugehören. Entfernen Sie es von allen Paketen oder Preislisten, bevor Sie zurückziehen.|
> |**Name**:<br />CannotRetireProductFromActiveBundle<br />**Hex**:<br />8004F997<br />**Nummer**:<br />-2147157609|Dieses Produkt kann nur storniert werden, da er Teil von aktiven Paketen oder Preislisten ist. Entfernen Sie das Stapelprotokoll von allen Paketen oder Preislisten, bevor Sie zurückziehen.|
> |**Name**:<br />CannotRevokeAccessToAddressBookFilters<br />**Hex**:<br />80048444<br />**Nummer**:<br />-2147187644|Zugriff auf die Adressbuchfilter kann nicht zurückgerufen werden|
> |**Name**:<br />CannotRevokeAccessToOfflineFilters<br />**Hex**:<br />80040273<br />**Nummer**:<br />-2147220877|Zugriff auf die Offlinefilter kann nicht zurückgerufen werden|
> |**Name**:<br />CannotRevokeAccessToOutlookFilters<br />**Hex**:<br />80040270<br />**Nummer**:<br />-2147220880|Zugriff auf die Outlookfilter kann nicht zurückgerufen werden|
> |**Name**:<br />CannotRouteInactiveQueueItem<br />**Hex**:<br />80040527<br />**Nummer**:<br />-2147220185|Sie können kein deaktiviertes Warteschlangenelement weiterleiten.|
> |**Name**:<br />CannotRoutePrivateQueueItemNonmember<br />**Hex**:<br />80631121<br />**Nummer**:<br />-2140991199|Dieses Element der privaten Warteschlange kann nicht dem ausgewählten Benutzer zugewiesen werden.|
> |**Name**:<br />CannotRouteToNonQueueMember<br />**Hex**:<br />80731119<br />**Nummer**:<br />-2139942631|Dieses Element kann nicht an ein Mitglied weitergeleitet werden, das nicht in der Warteschlange enthalten ist.|
> |**Name**:<br />CannotRouteToQueue<br />**Hex**:<br />800404ea<br />**Nummer**:<br />-2147220246|Kann nicht die Warteschlange für Arbeit in Bearbeitung weiterleiten|
> |**Name**:<br />CannotRouteToSameQueue<br />**Hex**:<br />8004051b<br />**Nummer**:<br />-2147220197|Das Warteschlangenelement kann nicht zur selben Warteschlange weitergeleitet werden|
> |**Name**:<br />CannotSecureAttribute<br />**Hex**:<br />8004F501<br />**Nummer**:<br />-2147158783|Das Feld {0} ist nicht sicherungsfähig |
> |**Name**:<br />CannotSecureEntityKeyAttribute<br />**Hex**:<br />80060896<br />**Nummer**:<br />-2147088234|Das Feld {0} ist nicht sicherungsfähig und ist Teil der Entitätsschlüssel ({1}). Entfernen Sie das Feld von allen Entitätsschlüsseln, um es sicherungsfähig zu machen.|
> |**Name**:<br />CannotSelectReadOnlyPublisher<br />**Hex**:<br />8004F034<br />**Nummer**:<br />-2147160012|Es wird versucht, einen zufälligen Herausgeber für Lösung auszuwählen.|
> |**Name**:<br />CannotSendInviteToDuplicateWindowsLiveId<br />**Hex**:<br />8004D215<br />**Nummer**:<br />-2147167723|Es kann keine Einladung gesendet werden, da es mehrere Benutzer mit diesem WLID gibt.|
> |**Name**:<br />CannotSetCaseOnHold<br />**Hex**:<br />80055000<br />**Nummer**:<br />-2147135488|Sie besitzen nicht die Berechtigungen, um für diese Anfrage den Statustyp „Zurückgestellt” festzulegen. Wenden Sie sich an Ihren Systemadministrator.|
> |**Name**:<br />CannotSetEntitlementTermsDecrementBehavior<br />**Hex**:<br />80060851<br />**Nummer**:<br />-2147088303|Sie verfügen nicht über ausreichende Rechte, um festzulegen, ob Berechtigungsbedingungen für diesen Anfragedatensatz verringert werden können.|
> |**Name**:<br />CannotSetEntityOnHold<br />**Hex**:<br />80055004<br />**Nummer**:<br />-2147135484|Sie besitzen keine Berechtigung, diesen Datensatz auf Abwarten zu setzen Wenden Sie sich an den zuständigen Systemadministrator.|
> |**Name**:<br />CannotSetInactiveViewAsDefault<br />**Hex**:<br />8004027b<br />**Nummer**:<br />-2147220869|Inaktive Ansichten können nicht als Standardansicht festgelegt werden.|
> |**Name**:<br />CannotSetParentDefaultTeam<br />**Hex**:<br />80048308<br />**Nummer**:<br />-2147187960|Das Standardteam der Unternehmenseinheit kann nicht festgelegt werden.|
> |**Name**:<br />CannotSetProductAsParent<br />**Hex**:<br />8004F998<br />**Nummer**:<br />-2147157608|Sie können nur eine Produktfamilie als übergeordnet auswählen.|
> |**Name**:<br />CannotSetPublishRetiredProductsToDraft<br />**Hex**:<br />80061035<br />**Nummer**:<br />-2147086283|Sie können einen veröffentlichten oder zurückgezogenen Produktdatensatz nicht in den Entwurfsstatus versetzen.|
> |**Name**:<br />CannotSetSolutionSystemAttributes<br />**Hex**:<br />8004F008<br />**Nummer**:<br />-2147160056|Systemattribute ({0}) können nicht außerhalb der Installation oder des Upgrades festgelegt werden.|
> |**Name**:<br />CannotSetWindowsLiveIdForInternetMarketingUser<br />**Hex**:<br />80045034<br />**Nummer**:<br />-2147200972|Sie können mit Windows Live ID für den Internetmarketing-Partnersbenutzer nicht ändern. Der Benutzer vom Typ "Internetmarketingpartner" kann nicht deaktiviert werden. Für diesen Benutzer wird keine Benutzerlizenz benötigt, und er wird Ihrer Organisation nicht in Rechnung gestellt.|
> |**Name**:<br />CannotShareSystemManagedTeam<br />**Hex**:<br />80048339<br />**Nummer**:<br />-2147187911|Sie können einen Datensatz nicht für ein vom System generiertes Zugriffsteam freigeben oder die Freigabe aufheben.|
> |**Name**:<br />CannotShareWithOwner<br />**Hex**:<br />80040214<br />**Nummer**:<br />-2147220972|Ein Element kann für den zuständigen Benutzer nicht freigegeben werden.|
> |**Name**:<br />CannotSpecifyAttendeeForAppointmentPropagation<br />**Hex**:<br />8004031c<br />**Nummer**:<br />-2147220708|Ein Teilnehmer für die Terminverteilung kann nicht angegeben werden.|
> |**Name**:<br />CannotSpecifyBothProductAndProductDesc<br />**Hex**:<br />80043afb<br />**Nummer**:<br />-2147206405|Sie können nicht sowohl „productid” als auch „productdescription” für denselben Datensatz festlegen.|
> |**Name**:<br />CannotSpecifyBothUomAndProductDesc<br />**Hex**:<br />80043afa<br />**Nummer**:<br />-2147206406|Sie können nicht sowohl „uomid” als auch „productdescription” für denselben Datensatz festlegen.|
> |**Name**:<br />CannotSpecifyCommunicationAttributeOnActivityForPropagation<br />**Hex**:<br />8004031e<br />**Nummer**:<br />-2147220706|Kommunikationsattribut zu Aktivität für Verteilung kann nicht angegeben werden|
> |**Name**:<br />CannotSpecifyOrganizerForAppointmentPropagation<br />**Hex**:<br />8004031a<br />**Nummer**:<br />-2147220710|Kann keinen Organisator für die Terminverteilung angeben|
> |**Name**:<br />CannotSpecifyOwnerForActivityPropagation<br />**Hex**:<br />80040327<br />**Nummer**:<br />-2147220697|Besitzer für Aktivitätsverteilung kann nicht angegeben werden|
> |**Name**:<br />CannotSpecifyRecipientForActivityPropagation<br />**Hex**:<br />8004031d<br />**Nummer**:<br />-2147220707|Ein Empfänger für Aktivitätsverteilung kann nicht angegeben werden|
> |**Name**:<br />CannotSpecifySenderForActivityPropagation<br />**Hex**:<br />8004031b<br />**Nummer**:<br />-2147220709|Ein Sender für die Terminverteilung kann nicht angegeben werden.|
> |**Name**:<br />CannotUndeleteLabel<br />**Hex**:<br />8004F003<br />**Nummer**:<br />-2147160061|Es wird versucht, das Löschen einer Beschriftung rückgängig zu machen, die nicht als Löschung markiert ist.|
> |**Name**:<br />CannotUninstallReferencedProtectedSolution<br />**Hex**:<br />8004F020<br />**Nummer**:<br />-2147160032|Diese Lösung kann nicht deinstalliert werden, da das Element {0} mit der ID {1} für die Lösung {2} erforderlich ist. Deinstallieren Sie die {2} Lösung und versuchen Sie es erneut.|
> |**Name**:<br />CannotUninstallWithDependencies<br />**Hex**:<br />8004F01D<br />**Nummer**:<br />-2147160035|Lösungsabhängigkeiten sind vorhandenm, können nicht deinstalliert.|
> |**Name**:<br />CannotUpdateActiveModernFlow<br />**Hex**:<br />80060466<br />**Nummer**:<br />-2147089306|Eigenschaft „{0}” kann nicht in einem veröffentlichten modernen Flussprozess aktualisiert werden.|
> |**Name**:<br />CannotUpdateAppDefaultValueForStateAttribute<br />**Hex**:<br />80044343<br />**Nummer**:<br />-2147204285|Der Standardwert für ein Attribut für Status (statecode) kann nicht aktualisiert werden.|
> |**Name**:<br />CannotUpdateAppDefaultValueForStatusAttribute<br />**Hex**:<br />80044344<br />**Nummer**:<br />-2147204284|Der Standardwert für ein Statusgrundattribut (statecode) wird nicht verwendet. Der Grund des standardmäßigen Status wird in die zugeordnete Attributoption für Status (statecode) festgelegt.|
> |**Name**:<br />CannotUpdateAppModuleClientType<br />**Hex**:<br />80050128<br />**Nummer**:<br />-2147155672|Der Client-Typ dieser App kann nicht geändert werden.|
> |**Name**:<br />CannotUpdateAppModuleUniqueName<br />**Hex**:<br />80050119<br />**Nummer**:<br />-2147155687|Sie können den eindeutigen Namen nicht ändern.|
> |**Name**:<br />CannotUpdateAzureActiveDirectoryObjectIdField<br />**Hex**:<br />80041d4f<br />**Nummer**:<br />-2147214001|Die Eigenschaft AzureActiveDirectoryObjectId kann nicht geändert werden.|
> |**Name**:<br />CannotUpdateBecauseItIsReadOnly<br />**Hex**:<br />8004022e<br />**Nummer**:<br />-2147220946|Das Objekt kann nicht aktualisiert werden, da es schreibgeschützt ist.|
> |**Name**:<br />CannotUpdateCampaignForCampaignActivity<br />**Hex**:<br />8004030b<br />**Nummer**:<br />-2147220725|Übergeordnete Kampagne kann nicht aktualisiert werden.|
> |**Name**:<br />CannotUpdateCampaignForCampaignResponse<br />**Hex**:<br />8004030c<br />**Nummer**:<br />-2147220724|Übergeordnete Kampagne kann nicht aktualisiert werden.|
> |**Name**:<br />CannotUpdateDeactivatedQueueItem<br />**Hex**:<br />8004051d<br />**Nummer**:<br />-2147220195|Dieses Element ist deaktiviert. Zum Verwenden dieses Element können Sie es erneut aktivieren und versuchen Sie es erneut.|
> |**Name**:<br />CannotUpdateDefaultField<br />**Hex**:<br />800608D8<br />**Nummer**:<br />-2147088168|Sie können das isDefaultTheme-Attribut nicht aktualisieren.|
> |**Name**:<br />CannotUpdateDefaultSolution<br />**Hex**:<br />8004F009<br />**Nummer**:<br />-2147160055|Das Standardlösungsattribut{0} {1} kann nur auf Installation oder Upgrade festgelegt werden.  Dieser Wert{0} kann nicht geändert werden.|
> |**Name**:<br />CannotUpdateDelaySendTimeForEmailWhenEmailIsNotInProperState<br />**Hex**:<br />80050020<br />**Nummer**:<br />-2147155936|Wir können die Verzögerung nicht aktualisieren, da die E-Mail kein Entwurf ist oder nicht zum Senden geplant ist.|
> |**Name**:<br />CannotUpdateDelaySendTimeWhenEEFeatureNotEnabled<br />**Hex**:<br />80050021<br />**Nummer**:<br />-2147155935|Wir können die E-Mail-Sendeverzögerungszeit nicht aktualisieren, weil E-Mail-Engagement für die Organisation deaktiviert ist.|
> |**Name**:<br />CannotUpdateDraftProducts<br />**Hex**:<br />8004F975<br />**Nummer**:<br />-2147157643|Sie können nur Entwurf-Produkte aktualisieren.|
> |**Name**:<br />CannotUpdateEmailStatisticForEmailNotFollowed<br />**Hex**:<br />80050002<br />**Nummer**:<br />-2147155966|Wir können die E-Mail-Statistik nicht aktualisieren, weil die E-Mail nicht nachverfolgt wurde.|
> |**Name**:<br />CannotUpdateEmailStatisticForEmailNotSent<br />**Hex**:<br />80050001<br />**Nummer**:<br />-2147155967|Wir können die E-Mail-Statistik nicht aktualisieren, weil die E-Mail nicht übermittelt wurde.|
> |**Name**:<br />CannotUpdateEmailStatisticWhenEEFeatureNotEnabled<br />**Hex**:<br />80050018<br />**Nummer**:<br />-2147155944|Wir können die E-Mail-Statistik nicht aktualisieren, weil E-Mail-Engagement für die Organisation deaktiviert ist.|
> |**Name**:<br />CannotUpdateEntitlement<br />**Hex**:<br />80060852<br />**Nummer**:<br />-2147088302|Nur aktive Berechtigungsdatensätze können als Standard festgelegt werden.|
> |**Name**:<br />CannotUpdateEntitySetName<br />**Hex**:<br />8004F663<br />**Nummer**:<br />-2147158429|EntitySetName kann für OOB-Entitäten nicht aktualisiert werden|
> |**Name**:<br />CannotUpdateExternalPartyWithSameCorrelationKey<br />**Hex**:<br />80061114<br />**Nummer**:<br />-2147086060|Ein Datensatz für eine externe Partei ist bereits mit demselben Korrelationsschlüsselwert vorhanden.|
> |**Name**:<br />CannotUpdateGoalPeriodInfoChildGoal<br />**Hex**:<br />80044901<br />**Nummer**:<br />-2147202815|Die mit dem Zielzeitraum verknüpften Attribute für ein untergeordnetes Ziel können nicht aktualisiert werden.|
> |**Name**:<br />CannotUpdateGoalPeriodInfoClosedGoal<br />**Hex**:<br />80044910<br />**Nummer**:<br />-2147202800|Der Zeitraum für dieses Ziel kann nicht geändert werden, da mindestens ein geschlossenes untergeordnetes Ziel vorhanden ist.|
> |**Name**:<br />CannotUpdateManagedSolution<br />**Hex**:<br />8004F024<br />**Nummer**:<br />-2147160028|Kann Lösung ''{0}" nicht aktualisieren, da es eine verwaltete Lösung ist.|
> |**Name**:<br />CannotUpdateMetricOnChildGoal<br />**Hex**:<br />80044900<br />**Nummer**:<br />-2147202816|Die Metrik für ein untergeordnetes Ziel kann nicht aktualisiert werden.|
> |**Name**:<br />CannotUpdateMetricOnGoalWithChildren<br />**Hex**:<br />80044902<br />**Nummer**:<br />-2147202814|Die Metrik für ein Ziel mit zugeordneten untergeordneten Zielen kann nicht aktualisiert werden.|
> |**Name**:<br />CannotUpdateMetricWithGoals<br />**Hex**:<br />80044803<br />**Nummer**:<br />-2147203069|Die Änderungen an diesem Datensatz können nicht gespeichert werden, da die verbundene Zielmetrik von mindestens einem geschlossenen Ziel verwendet wird.|
> |**Name**:<br />CannotUpdateNameDefaultTeam<br />**Hex**:<br />8004830A<br />**Nummer**:<br />-2147187958|Das Standardteam der Unternehmenseinheit kann nicht aktualisiert werden.|
> |**Name**:<br />CannotUpdateNonCustomizableString<br />**Hex**:<br />80044247<br />**Nummer**:<br />-2147204537|Die Ausgangssprachen-Übersetzungszeichenfolge, die im Arbeitsblatt vorhanden ist, {0}Zeile {1}, Spalte {2} kann nicht angepasst werden.|
> |**Name**:<br />CannotUpdateObjectBecauseItIsInactive<br />**Hex**:<br />80040230<br />**Nummer**:<br />-2147220944|Das Objekt kann nicht aktualisiert werden, weil es inaktiv ist.|
> |**Name**:<br />CannotUpdateOpportunityCurrency<br />**Hex**:<br />80048479<br />**Nummer**:<br />-2147187591|Die Währung kann nicht geändert werden, da diese Verkaufschance Produkt-Angebote und/oder Aufträge hat, die mit ihm verbunden sind.  Wenn Sie die Währung ändern möchten, deaktivieren Sie alle Produkte/Angebote/Bestellungen und ändern Sie dann die Währung, oder erstellen Sie eine neue Verkaufschance mit den entsprechenden Währungsinformationen.|
> |**Name**:<br />CannotUpdateOrgDBOrgSettingWhenOffline<br />**Hex**:<br />80048515<br />**Nummer**:<br />-2147187435|Organisationseinstellungen, die in der Organisationsdatenbank gespeichert sind können offline nicht eingestellt werden.|
> |**Name**:<br />CannotUpdateParentAndDependents<br />**Hex**:<br />8004480c<br />**Nummer**:<br />-2147203060|Kann Metrik- oder Zeitraumattribute nicht aktualisieren, wenn das übergeordnete Element aktualisiert wird.|
> |**Name**:<br />CannotUpdatePrivateOrWIPQueue<br />**Hex**:<br />800404ee<br />**Nummer**:<br />-2147220242|Die private oder WIP-Containerwarteschlange kann nicht aktualisiert oder gelöscht werden|
> |**Name**:<br />CannotUpdateProductCurrency<br />**Hex**:<br />80048cfa<br />**Nummer**:<br />-2147185414|Die Währung des Produkts kann nicht aktualisiert werden, da sie mit Preiselementen mit Preisberechnungsmethodenprozenten verknüpft sind.|
> |**Name**:<br />CannotUpdateQuoteCurrency<br />**Hex**:<br />8004480e<br />**Nummer**:<br />-2147203058|Die Währung kann nicht geändert werden, da diese Verkaufschance Produkt-Angebote und/oder Aufträge hat, die mit ihm verbunden sind. Wenn Sie die Währung ändern möchten, deaktivieren Sie alle Produkte und ändern Sie dann die Währung, oder erstellen Sie ein neues Angebot mit den entsprechenden Währungsinformationen.|
> |**Name**:<br />CannotUpdateReadOnlyPublisher<br />**Hex**:<br />8004F033<br />**Nummer**:<br />-2147160013|Es wird versucht, einen zufälligen Herausgeber zu aktualisieren.|
> |**Name**:<br />CannotUpdateRestrictedPublisher<br />**Hex**:<br />8004F017<br />**Nummer**:<br />-2147160041|Eingeschränkter Herausgeber ({0}) kann nicht aktualisiert werden.|
> |**Name**:<br />CannotUpdateRestrictedSolution<br />**Hex**:<br />8004F00A<br />**Nummer**:<br />-2147160054|Eingeschränkte Lösung ({0}) kann nicht aktualisiert werden.|
> |**Name**:<br />CannotUpdateRollupAttributeWithClosedGoals<br />**Hex**:<br />80044801<br />**Nummer**:<br />-2147203071|Die Änderungen an der Rollup-Felddefinition können nicht gespeichert werden, da die verbundene Zielmetrik von mindestens einem geschlossenen Ziel verwendet wird.|
> |**Name**:<br />CannotUpdateRollupFields<br />**Hex**:<br />80044911<br />**Nummer**:<br />-2147202799|Sie können nur Rollupfelder schreiben, wenn isoverride nicht auf true im Erstellen/in der Updateanforderung festgelegt ist.|
> |**Name**:<br />CannotUpdateSolutionPatch<br />**Hex**:<br />8004F042<br />**Nummer**:<br />-2147159998|Lösungspatch mit Version {0} ist bereits vorhanden. Das Aktualisieren des Patches wird nicht unterstützt.|
> |**Name**:<br />CannotUpdateSupportUser<br />**Hex**:<br />80041d47<br />**Nummer**:<br />-2147214009|Kann die Supportbenutzerrolle nicht aktualisieren.|
> |**Name**:<br />CannotUpdateSyncUserIsLicensedField<br />**Hex**:<br />80041d4c<br />**Nummer**:<br />-2147214004|Die Eigenschaft IsLIcensed kann nicht geändert werden.|
> |**Name**:<br />CannotUpdateSyncUserIsSyncWithDirectoryField<br />**Hex**:<br />80041d4e<br />**Nummer**:<br />-2147214002|Die Eigenschaft IsSyncUserWithDirectory kann nicht geändert werden.|
> |**Name**:<br />CannotUpdateSystemEntityIcons<br />**Hex**:<br />8004F653<br />**Nummer**:<br />-2147158445|Systementitätssymbole können nicht aktualisiert werden.|
> |**Name**:<br />CannotUpdateSystemTheme<br />**Hex**:<br />800608D6<br />**Nummer**:<br />-2147088170|Sie können keine Systemdesigns ändern.|
> |**Name**:<br />CannotUpdateTemplateIdForEmailInNonDraftState<br />**Hex**:<br />80050017<br />**Nummer**:<br />-2147155945|Wir können die Vorlage nicht aktualisieren, da die E-Mail bereits gesendet wurde oder nicht im Entwurfszustand ist.|
> |**Name**:<br />CannotUpdateTriggerForPublishedRules<br />**Hex**:<br />80060002<br />**Nummer**:<br />-2147090430|Ein Auslöser kann nicht für eine veröffentlichte Regel hinzugefügt/gelöscht/aktualisiert werden.|
> |**Name**:<br />CannotUpdateUnpublishedDeleteInstance<br />**Hex**:<br />8004F00F<br />**Nummer**:<br />-2147160049|Die Komponente, die Sie gerade aktualisieren, wurde gelöscht.|
> |**Name**:<br />CannotUseOpportunitySetStateMessage<br />**Hex**:<br />80100005<br />**Nummer**:<br />-2146435067|Diese Message kann nicht verwendet werden, um den Status der Verkaufschance auf {0} festzulegen. Um den Status der Verkaufschance auf {1} festzulegen, verwenden Sie stattdessen die {1}-Message.|
> |**Name**:<br />CannotUseUserCredentials<br />**Hex**:<br />8005E229<br />**Nummer**:<br />-2147098071|Der E-Mail-Connektor kann die Anmeldeinformationen nicht verwenden, die in der Postfachentität angegeben wurden. Dies kann daran liegen, dass Benutzer dies nicht zulassen. Verwenden Sie einen anderen Modus zur Eingabe der Anmeldeinformationen oder lassen Sie die Verwendung der Anmeldeinformationen über E-Mail-Konnektor zu.|
> |**Name**:<br />CanOnlySetActiveOrDraftProductFamilyAsParent<br />**Hex**:<br />8004F906<br />**Nummer**:<br />-2147157754|Sie können nur Produktfamilien im Entwurfsstatus oder im aktiven Status als übergeordnet festlegen.|
> |**Name**:<br />CantSaveRecordInOffline<br />**Hex**:<br />8005F214<br />**Nummer**:<br />-2147093996|Sie können diesen Datensatz nicht speichern, wenn Sie offline sind.|
> |**Name**:<br />CantSetIsGuestProfile<br />**Hex**:<br />8006111A<br />**Nummer**:<br />-2147086054|Sie können den Wert des IsGuestProfile-Felds nicht festlegen oder ändern, da sie ausschließlich interne Verwendung sind.„”|
> |**Name**:<br />CantUpdateOnlineRecord<br />**Hex**:<br />8005F224<br />**Nummer**:<br />-2147093980|Dieser Datensatz kann nicht aktualisiert werden, da er im Offlinemodus nicht vorhanden ist.|
> |**Name**:<br />CanvasAppsExpectedFileMissing<br />**Hex**:<br />80072356<br />**Nummer**:<br />-2147015850|Die Lösung gab eine erwartete Anlagendatei an, aber die Datei hat gefehlt oder war ungültig.|
> |**Name**:<br />CanvasAppsInvalidSolutionFileContent<br />**Hex**:<br />80072354<br />**Nummer**:<br />-2147015852|Die Anfrage, eine Canvas-App zu importieren, sollte mindestens eine Anlagendatei enthalten.|
> |**Name**:<br />CanvasAppsNotEnabled<br />**Hex**:<br />80072351<br />**Nummer**:<br />-2147015855|Das Erstellen und Bearbeiten von Canvas-Apps ist nicht aktiviert.|
> |**Name**:<br />CanvasAppsServiceRequestClientFailure<br />**Hex**:<br />80072352<br />**Nummer**:<br />-2147015854|Die Anforderung an den PowerApps-Service ist mit einem Client-Fehler fehlgeschlagen.|
> |**Name**:<br />CanvasAppsServiceRequestServerFailure<br />**Hex**:<br />80072353<br />**Nummer**:<br />-2147015853|Die Anforderung an den PowerApps-Service ist mit einem Serverfehler fehlgeschlagen.|
> |**Name**:<br />CanvasAppsUnexpectedCanvasAppId<br />**Hex**:<br />80072355<br />**Nummer**:<br />-2147015851|Die Anforderung an den PowerApps-Service führte zu einer neuen Canvas-App-ID, wenn der bereits vorhandene Wert erwartet wurde.|
> |**Name**:<br />CanvasAppVersionDoesNotMatchLatestPublishedVersion<br />**Hex**:<br />80072358<br />**Nummer**:<br />-2147015848|Die aktuelle veröffentlichte Version der Canvas-App entspricht nicht der bekannten Version des Dynamics-Services.|
> |**Name**:<br />CanvasAppVersionMissingOrInvalid<br />**Hex**:<br />80072357<br />**Nummer**:<br />-2147015849|Die App-Version der Canvas-App wurde nicht festgelegt oder war ein ungültiger Wert.|
> |**Name**:<br />CAPolicyValidationFailedLateBind<br />**Hex**:<br />80072561<br />**Nummer**:<br />-2147015327|Der Benutzer befindet sich in einem Speicherort nur für Administratoren.|
> |**Name**:<br />CascadeDeleteNotAllowDelete<br />**Hex**:<br />80048103<br />**Nummer**:<br />-2147188477|Ziel wird nicht gelöscht werden können|
> |**Name**:<br />CascadeFailToCreateNativeDAWrapper<br />**Hex**:<br />80048108<br />**Nummer**:<br />-2147188472|Fehler bei der Erstellung des nicht verwalteten Datenzugriffswrappers|
> |**Name**:<br />CascadeInvalidExtraConditionValue<br />**Hex**:<br />80048101<br />**Nummer**:<br />-2147188479|Ungültiger Extrabedingungswert|
> |**Name**:<br />CascadeInvalidLinkType<br />**Hex**:<br />80048102<br />**Nummer**:<br />-2147188478|Ungültiger CascadeLink-Typ|
> |**Name**:<br />CascadeInvalidLinkTypeTransition<br />**Hex**:<br />80044155<br />**Nummer**:<br />-2147204779|Ungültiger Linktyp für die kaskadierenden Systementitätaktionen.|
> |**Name**:<br />CascadeMergeInvalidSpecialColumn<br />**Hex**:<br />80048106<br />**Nummer**:<br />-2147188474|Ungültiger Spaltenname für Merge Special Casing|
> |**Name**:<br />CascadeProxyEmptyCallerId<br />**Hex**:<br />8004810b<br />**Nummer**:<br />-2147188469|Leere Anrufer-ID|
> |**Name**:<br />CascadeProxyInvalidNativeDAPtr<br />**Hex**:<br />80048109<br />**Nummer**:<br />-2147188471|Ungültiger Zeiger des nicht verwalteten Datenzugriffsobjekts|
> |**Name**:<br />CascadeProxyInvalidPrincipalType<br />**Hex**:<br />8004810a<br />**Nummer**:<br />-2147188470|Ungültiger Sicherheitsprinzipalstyp|
> |**Name**:<br />CascadeRemoveLinkOnNonNullable<br />**Hex**:<br />80048104<br />**Nummer**:<br />-2147188476|CascadeDelete wird als RemoveLink definiert, solange der Fremdschlüssel nicht auf NULL festlegbar ist|
> |**Name**:<br />CascadeReparentOnNonUserOwned<br />**Hex**:<br />80048107<br />**Nummer**:<br />-2147188473|Kann "Kaskade überordnen" nicht auf nicht UserOwned-Entitäten ausführen|
> |**Name**:<br />CaseAlreadyResolved<br />**Hex**:<br />800404cf<br />**Nummer**:<br />-2147220273|Dieser Fall wurde abgeschlossen. Schließen Sie die Anfrage und öffnen Sie sie erneut, um die Updates anzuzeigen.|
> |**Name**:<br />CaseStateChangeInvalid<br />**Hex**:<br />8006074<br />**Nummer**:<br />134242420|Aufgrund der Statusübergangsregeln können Sie eine Anfrage im aktuellen Status nicht auflösen. Ändern Sie den Anfragestatus, und versuchen Sie ihn dann aufzulösen, oder wenden Sie sich an den Systemadministrator.|
> |**Name**:<br />CategoryDataTypeInvalid<br />**Hex**:<br />8004E01A<br />**Nummer**:<br />-2147164134|Die Datenenbeschreibung für die Visualisierung ist ungültig. Der Attributtyp für die Gruppe von einer der Kategorien ist ungültig. Korrigieren Sie die Datenbeschreibung.|
> |**Name**:<br />CategoryNotSetToBusinessProcessFlow<br />**Hex**:<br />80060404<br />**Nummer**:<br />-2147089404|Kategorie sollte auf BusinessProcessFlow festgelegt werden, solange die Geschäftsprozessflusskategorie erstellt wird|
> |**Name**:<br />CDSOrgNotSupported<br />**Hex**:<br />80044510<br />**Nummer**:<br />-2147203824|Dynamics 365 for Outlook wird für diese Organisation nicht unterstützt.|
> |**Name**:<br />CertificateNotFound<br />**Hex**:<br />8005E239<br />**Nummer**:<br />-2147098055|Das Zertifikat wurde nicht gefunden.|
> |**Name**:<br />ChangeTrackingDisabledForMobileOfflineError<br />**Hex**:<br />800609A1<br />**Nummer**:<br />-2147087967|Sie können die Änderungsnachverfolgung für Entitäten, die für Mobile Offline aktiviert sind, nicht deaktivieren.|
> |**Name**:<br />ChangeTrackingNotEnabledForEntity<br />**Hex**:<br />80072491<br />**Nummer**:<br />-2147015535|Die Entität {0} ist nicht für die Änderungsnachverfolgung aktiviert.|
> |**Name**:<br />ChangeTrackingNotEnabledForRelatedEntities<br />**Hex**:<br />80072492<br />**Nummer**:<br />-2147015534|Änderungen können nicht für die sich überschneidet Entität {0} abgerufen werden, da beide verknüpfte Entitäten nicht für die Änderungsnachverfolgung aktiviert werden.|
> |**Name**:<br />ChannelAccessProfileRuleAlreadyInDraftState<br />**Hex**:<br />80061115<br />**Nummer**:<br />-2147086059|Sie können eine Kanalzugriffsprofilregel im Entwurfszustand nicht deaktivieren.|
> |**Name**:<br />ChannelPropertyGroupAlreadyExistsWithSameSourceType<br />**Hex**:<br />800608EC<br />**Nummer**:<br />-2147088148|Ein Datensatz für den angegebenen Quelltyp ist bereits vorhanden. Sie können keine andere erstellen.|
> |**Name**:<br />ChannelPropertyNameInvalid<br />**Hex**:<br />800608F2<br />**Nummer**:<br />-2147088142|Der Kanaleigenschaftsname ist ungültig. Der Name darf nur alphanumerische Zeichen und Unterstrich enthalten. Wählen Sie einen anderen Namen aus, und versuchen Sie es erneut.|
> |**Name**:<br />ChartAreaCategoryMismatch<br />**Hex**:<br />8004E005<br />**Nummer**:<br />-2147164155|Die Anzahl der Diagrammbereiche und Anzahl der Kategorien sollten identisch sein.|
> |**Name**:<br />ChartTypeNotSupportedForComparisonChart<br />**Hex**:<br />8004E018<br />**Nummer**:<br />-2147164136|Dieser Diagrammtyp wird für Vergleichsdiagramme nicht unterstützt.|
> |**Name**:<br />ChartTypeNotSupportedForMultipleSeriesChart<br />**Hex**:<br />8004E021<br />**Nummer**:<br />-2147164127|Mindestens ein Diagrammtyp {0} unterstützt nicht die Funktion für Mehrfachdiagramme.|
> |**Name**:<br />CheckPrivilegeGroupForUserOnPremiseError<br />**Hex**:<br />80048401<br />**Nummer**:<br />-2147187711|Wählen Sie ein Konto aus, das ein Mitglied der PrivUserGroup-Sicherheitsgruppe ist, und versuchen Sie es erneut.|
> |**Name**:<br />CheckPrivilegeGroupForUserOnSplaError<br />**Hex**:<br />80048400<br />**Nummer**:<br />-2147187712|Wählen Sie ein Dynamics 365-Systemadministratorkonto aus, das der zugrundeliegenden Unternehmenseinheit zugehörig ist, und versuchen Sie es erneut.|
> |**Name**:<br />ChildBusinessDoesNotExist<br />**Hex**:<br />80041d22<br />**Nummer**:<br />-2147214046|Die untergeordnete Unternehmens-ID ist nicht gültig.|
> |**Name**:<br />ChildUserDoesNotExist<br />**Hex**:<br />80041d26<br />**Nummer**:<br />-2147214042|Die untergeordnete Benutzer-ID ist nicht gültig.|
> |**Name**:<br />ChildWorkflowNotFound<br />**Hex**:<br />8004502F<br />**Nummer**:<br />-2147200977|Der Workflow kann nicht ausgeführt werden, da ein oder mehrere untergeordnete Workflows, den sie verwenden, nicht veröffentlicht ist oder gelöscht wurde. Überprüfen Sie die untergeordneten Workflow, und versuchen Sie den Workflow erneut auszuführen.|
> |**Name**:<br />ChildWorkflowParameterMismatch<br />**Hex**:<br />80045048<br />**Nummer**:<br />-2147200952|Dieser Workflow kann nicht ausgeführt werden, da die Anfragen, die vom übergeordneten Workflow bereitgestellt werden, nicht mit den angegebenen Parametern im untergeordneten Workflow entspricht. Überprüfen Sie den Verweis des untergeordneten Workflows im übergeordneten Workflow, und versuchen Sie, den Workflow erneut auszuführen.|
> |**Name**:<br />CircularDependency<br />**Hex**:<br />80071157<br />**Nummer**:<br />-2147020457|Der Lösungsvorgang ist aufgrund einer zirkulären Abhängigkeit mit anderen Lösungen fehlgeschlagen. Überprüfen Sie die Ausnahme, um weitere Informationen zu erhalten: {0}|
> |**Name**:<br />ClientAuthCanceled<br />**Hex**:<br />8004D224<br />**Nummer**:<br />-2147167708|Authentifizierung wurde vom Benutzer abgebrochen.|
> |**Name**:<br />ClientAuthNoConnectivity<br />**Hex**:<br />8004D226<br />**Nummer**:<br />-2147167706|Es sind keine Verbindung.|
> |**Name**:<br />ClientAuthNoConnectivityOffline<br />**Hex**:<br />8004D225<br />**Nummer**:<br />-2147167707|Es gibt keine Verbindung bei der Ausführung im Offlinemodus.|
> |**Name**:<br />ClientAuthOfflineInvalidCallerId<br />**Hex**:<br />8004D227<br />**Nummer**:<br />-2147167705|Offline SDK-Aufrufe müssen im Offlinemodus-Benutzerkontext gemacht werden.|
> |**Name**:<br />ClientAuthSignedOut<br />**Hex**:<br />8004D221<br />**Nummer**:<br />-2147167711|Der Benutzer hat sich abgemeldet.|
> |**Name**:<br />ClientAuthSyncIssue<br />**Hex**:<br />8004D223<br />**Nummer**:<br />-2147167709|Synchronisierung zwischen den Prozesse fehlgeschlagen.|
> |**Name**:<br />ClientServerDateTimeMismatch<br />**Hex**:<br />80044503<br />**Nummer**:<br />-2147203837|Das Datum /Uhrzeit des Computers mit dem Server ist nach dem Abschlusszeitpunkt mehr als 5 Minuten nicht synchron.|
> |**Name**:<br />ClientServerEmailAddressMismatch<br />**Hex**:<br />80044504<br />**Nummer**:<br />-2147203836|E-Mail-Adresse und die Outlook-E-Mail-Adresse von Dynamics 365 stimmen nicht überein.|
> |**Name**:<br />ClientUpdateAvailable<br />**Hex**:<br />8004D294<br />**Nummer**:<br />-2147167596|Für Dynamics 365 for Outlook ist ein Update verfügbar.|
> |**Name**:<br />ClientVersionTooHigh<br />**Hex**:<br />80044501<br />**Nummer**:<br />-2147203839|Diese Version des Outlook-Clients ist mit Ihrer Dynamics 365-Organisation kompatibel (aktuelle Version {0}-ist zu hoch).|
> |**Name**:<br />ClientVersionTooLow<br />**Hex**:<br />80044500<br />**Nummer**:<br />-2147203840|Diese Version des Outlook-Clients ist mit Ihrer Dynamics 365-Organisation kompatibel (aktuelle Version {0}-ist zu niedrig).|
> |**Name**:<br />CloneSolutionException<br />**Hex**:<br />80048539<br />**Nummer**:<br />-2147187399|Der Vorgang in der geklonten Lösung ist fehlgeschlagen.|
> |**Name**:<br />CloneSolutionPatchException<br />**Hex**:<br />80061771<br />**Nummer**:<br />-2147084431|Der Patch "{0}" hat mindestens die gleiche Version ({1}) wie der gerade installierte Patch.|
> |**Name**:<br />CloneTitleTooLong<br />**Hex**:<br />80071112<br />**Nummer**:<br />-2147020526|Ein Validierungsfehler ist aufgetreten. Die Länge des Namensattributs der Entität "mobileofflineprofile" übersteigt die maximal zulässige Länge von 200 Zeichen.|
> |**Name**:<br />CloseActiveChildCaseFirst<br />**Hex**:<br />8003F452<br />**Nummer**:<br />-2147224494|Schließen Sie die aktive untergeordnete Anfrage, bevor Sie die übergeordnete Anfrage schließen.|
> |**Name**:<br />ColorStripAttributesExceeded<br />**Hex**:<br />80061500<br />**Nummer**:<br />-2147085056|Der Abschnitt für den Farbstreifen kann nicht mehr als 1 Attribut aufweisen.|
> |**Name**:<br />ColorStripAttributesInvalid<br />**Hex**:<br />80061502<br />**Nummer**:<br />-2147085054|Der Abschnitt für den Farbstreifen kann nur Attribute der Typen 'Zwei Optionen', 'Optionssatz' und 'Statusgrund' aufweisen.|
> |**Name**:<br />CombinedManagedPropertyFailure<br />**Hex**:<br />8004F027<br />**Nummer**:<br />-2147160025|Die Evaluation der aktuellen Komponente (Name={0}, ID={1}) im aktuellen Vorgang ({2}) ist bei der Verwaltung der Eigenschaftenauswertung der Bedingung fehlgeschlagen: {3}|
> |**Name**:<br />CommandNotSupported<br />**Hex**:<br />80154B52<br />**Nummer**:<br />-2146088110|Der Befehl wird im Offlinemodus nicht unterstützt.|
> |**Name**:<br />CommunicationBlocked<br />**Hex**:<br />80044506<br />**Nummer**:<br />-2147203834|Kommunikation ist aufgrund einer Socketausnahme blockiert.|
> |**Name**:<br />ComponentDefinitionDoesNotExists<br />**Hex**:<br />8004F019<br />**Nummer**:<br />-2147160039|Es ist keine Komponentendefinition für den Komponententyp vorhanden. {0}|
> |**Name**:<br />ConcurrencyVersionMismatch<br />**Hex**:<br />80060882<br />**Nummer**:<br />-2147088254|Die Version des vorhandenen Datensatzes entspricht nicht der RowVersions-Eigenschaft, die bereitgestellt wurde.|
> |**Name**:<br />ConcurrencyVersionNotProvided<br />**Hex**:<br />80060883<br />**Nummer**:<br />-2147088253|Die RowVersions-Eigenschaft muss verfügbar gemacht werden, wenn der Wert in ConcurrencyBehavior IfVersionMatches ist.|
> |**Name**:<br />ConcurrentOperationFailure<br />**Hex**:<br />80071154<br />**Nummer**:<br />-2147020460|Der aktuelle {0}-Vorgang ist wegen eines anderen, gleichzeitig ausgeführten Vorgangs fehlgeschlagen. Versuchen Sie es später noch einmal.|
> |**Name**:<br />ConditionAttributesNotAnSubsetOfStepAttributes<br />**Hex**:<br />80060436<br />**Nummer**:<br />-2147089354|Attribute der Bedingung sind keine Teilmenge der Attribute im Schritt für die Phase: {0}|
> |**Name**:<br />ConditionBranchDoesHaveSetNextStageOnlyChildInXaml<br />**Hex**:<br />80060434<br />**Nummer**:<br />-2147089356|Verzweigungsbedingung kann nur SetNextStage als untergeordnetes Element enthalten.|
> |**Name**:<br />ConditionStepCountInXamlExceedsMaxAllowed<br />**Hex**:<br />80060435<br />**Nummer**:<br />-2147089355|{0} mehr als ein {1} nicht möglich.|
> |**Name**:<br />ConfigDBCannotDeleteDefaultOrganization<br />**Hex**:<br />8004D23B<br />**Nummer**:<br />-2147167685|Die Standardorganisation {0} kann nicht von der MSCRM_CONFIG-Datenbank gelöscht werden.|
> |**Name**:<br />ConfigDBCannotDeleteObjectDueState<br />**Hex**:<br />8004D232<br />**Nummer**:<br />-2147167694|"{0}" mit dem Wert = ({1}) in diesem Status = ({2}) aus der MSCRM_CONFIG-Datenbank kann nicht gelöscht werden|
> |**Name**:<br />ConfigDBCannotUpdateObjectDueState<br />**Hex**:<br />8004D237<br />**Nummer**:<br />-2147167689|"{0}" mit dem Wert = ({1}) in diesem Status = ({2}) aus der MSCRM_CONFIG-Datenbank kann nicht aktualisiert werden|
> |**Name**:<br />ConfigDBCascadeDeleteNotAllowDelete<br />**Hex**:<br />8004D233<br />**Nummer**:<br />-2147167693|"{0}" mit dem Wert = ({1}) kann aufgrund der Verweise des untergeordneten Elements "{2}" der MSCRM_CONFIG-Datenbank nicht gelöscht werden|
> |**Name**:<br />ConfigDBDuplicateRecord<br />**Hex**:<br />8004D231<br />**Nummer**:<br />-2147167695|Doppeltes ''{0}" mit Wert = ({1}) ist in der MSCRM_CONFIG-Datenbank vorhanden|
> |**Name**:<br />ConfigDBObjectDoesNotExist<br />**Hex**:<br />8004D230<br />**Nummer**:<br />-2147167696|''{0}" mit Wert = ({1}) ist in der MSCRM_CONFIG-Datenbank nicht vorhanden|
> |**Name**:<br />ConfigMissingDescription<br />**Hex**:<br />80044197<br />**Nummer**:<br />-2147204713|Eine Beschreibung muss angegeben werden.|
> |**Name**:<br />ConfigNullPrimaryKey<br />**Hex**:<br />80044196<br />**Nummer**:<br />-2147204714|Primärschlüssel kann nicht auf NULL festlegbar sein.|
> |**Name**:<br />ConfigurationPageNotValidForSolution<br />**Hex**:<br />8004701D<br />**Nummer**:<br />-2147192803|Die Lösungskonfigurationsseite muss in der Lösung vorhanden sein, die sie vertritt.|
> |**Name**:<br />ConfigureClaimsBeforeIfd<br />**Hex**:<br />8004D266<br />**Nummer**:<br />-2147167642|Die anspruchsbasierte Authentifizierung muss konfiguriert werden, bevor die Bereitstellung mit Internetzugriff konfiguriert werden kann.|
> |**Name**:<br />ConfiguredUserIsDifferentThanSuppliedUser<br />**Hex**:<br />80044508<br />**Nummer**:<br />-2147203832|Der konfigurierte Benutzer stimmt nicht mit dem angegebenen Benutzer überein.|
> |**Name**:<br />ConflictForOverriddenPropertiesEncountered<br />**Hex**:<br />80081010<br />**Nummer**:<br />-2146955248|Der Datensatz kann nicht veröffentlicht werden. Eine der Eigenschaften, die für diesen Datenkonflikt geändert wurde, verursacht einen Konflikt mit einer geerbten Version. Entfernen Sie die konfliktverursachende Eigenschaft und versuchen Sie es anschließend erneut.|
> |**Name**:<br />ConflictingProvisionTypes<br />**Hex**:<br />8004B02C<br />**Nummer**:<br />-2147176404|Die Servicekomponente {0} hat konfliktverursachende Bestimmungstypen.|
> |**Name**:<br />ConnectionCannotBeEnabledOnThisEntity<br />**Hex**:<br />80048214<br />**Nummer**:<br />-2147188204|Die Verbindungen in dieser {0}-Entität mit der ID {1} können nicht aktiviert werden.|
> |**Name**:<br />ConnectionExists<br />**Hex**:<br />80048208<br />**Nummer**:<br />-2147188216|Verbindung ist bereits vorhanden.|
> |**Name**:<br />ConnectionInvalidStartEndDate<br />**Hex**:<br />80048209<br />**Nummer**:<br />-2147188215|Enddatum / Startdatum ist ungültig.|
> |**Name**:<br />ConnectionNotSupported<br />**Hex**:<br />80048213<br />**Nummer**:<br />-2147188205|Der ausgewählte Datensatz unterstützt keine Verbindungen. Sie können die Verbindung nicht hinzufügen.|
> |**Name**:<br />ConnectionObjectsMissing<br />**Hex**:<br />80048210<br />**Nummer**:<br />-2147188208|Beide miteinander verbundenen Objekte fehlen.|
> |**Name**:<br />ConnectionRoleNotValidForObjectType<br />**Hex**:<br />80048215<br />**Nummer**:<br />-2147188203|Der Datensatztyp {0} ist für die Verwendung mit der Verbindungsrolle {1} nicht definiert.|
> |**Name**:<br />ConnectionTimeOut<br />**Hex**:<br />80071024<br />**Nummer**:<br />-2147020764|Die Dokumente konnten nicht kopiert werden, da bei der Netzwerkverbindung eine Zeitüberschreitung auftrat. Versuchen Sie es später erneut, oder wenden Sie sich an den Systemadministrator.|
> |**Name**:<br />ConnectorNotEnabled<br />**Hex**:<br />80072600<br />**Nummer**:<br />-2147015168|Das Erstellen und Bearbeiten von Connector ist nicht aktiviert.|
> |**Name**:<br />ContactDoesNotExist<br />**Hex**:<br />80040503<br />**Nummer**:<br />-2147220221|Kontakt ist nicht vorhanden.|
> |**Name**:<br />ContactLoopBeingCreated<br />**Hex**:<br />8004050a<br />**Nummer**:<br />-2147220214|Durch das Erstellen dieser übergeordneten Zuordnung würde eine Schleife in der Hierarchie „Kontakte” erstellt werden.|
> |**Name**:<br />ContactLoopExists<br />**Hex**:<br />80040509<br />**Nummer**:<br />-2147220215|Schleife ist in der Kontakthierarchie vorhanden.|
> |**Name**:<br />ContextIsNull<br />**Hex**:<br />80060445<br />**Nummer**:<br />-2147089339|Fehler beim Erstellen oder Aktualisieren des Geschäftsprozesses: Kontext darf nicht Null sein.|
> |**Name**:<br />ContractDetailDiscountAmount<br />**Hex**:<br />80044413<br />**Nummer**:<br />-2147204077|Der Rabatttyp des Vertrags unterstützt nicht „Prozent”-Rabatte.|
> |**Name**:<br />ContractDetailDiscountAmountAndPercent<br />**Hex**:<br />80044414<br />**Nummer**:<br />-2147204076|Weder „Betrag” noch „Prozentsatz” können festgelegt werden.|
> |**Name**:<br />ContractDetailDiscountPercent<br />**Hex**:<br />80044412<br />**Nummer**:<br />-2147204078|Der Rabatttyp des Vertrags unterstützt nicht „Betrag”-Rabatte.|
> |**Name**:<br />ContractInvalidAllotmentTypeCode<br />**Hex**:<br />80043205<br />**Nummer**:<br />-2147208699|Der Zuteilungstypcode ist ungültig.|
> |**Name**:<br />ContractInvalidBillToAddress<br />**Hex**:<br />8004320f<br />**Nummer**:<br />-2147208689|Die Rechnungsadresse des Vertrags ist ungültig.|
> |**Name**:<br />ContractInvalidBillToCustomer<br />**Hex**:<br />80043210<br />**Nummer**:<br />-2147208688|Die Rechnung and en Kunden für den Vertrags ist ungültig.|
> |**Name**:<br />ContractInvalidContract<br />**Hex**:<br />80043213<br />**Nummer**:<br />-2147208685|Der Vertrag ist nicht gültig.|
> |**Name**:<br />ContractInvalidContractTemplate<br />**Hex**:<br />80043211<br />**Nummer**:<br />-2147208687|Die Vertragsvorlage ist ungültig.|
> |**Name**:<br />ContractInvalidCustomer<br />**Hex**:<br />8004320d<br />**Nummer**:<br />-2147208691|Der Kunde des Vertrags ist ungültig.|
> |**Name**:<br />ContractInvalidDatesForRenew<br />**Hex**:<br />80043218<br />**Nummer**:<br />-2147208680|Das Start- oder Enddatum dieses erneuerten Vertrags darf sich nicht mit anderen abgerechneten oder aktiven Verträgen mit derselben Vertragsnummer überschneiden.|
> |**Name**:<br />ContractInvalidDiscount<br />**Hex**:<br />80044193<br />**Nummer**:<br />-2147204717|Rabatt kann nicht größer als der Gesamtpreis sein.|
> |**Name**:<br />ContractInvalidPrice<br />**Hex**:<br />80043215<br />**Nummer**:<br />-2147208683|Der Preis ist ungültig.|
> |**Name**:<br />ContractInvalidServiceAddress<br />**Hex**:<br />8004320e<br />**Nummer**:<br />-2147208690|Die Serviceadresse des Vertrags ist ungültig.|
> |**Name**:<br />ContractInvalidStartEndDate<br />**Hex**:<br />80043202<br />**Nummer**:<br />-2147208702|Start- und Enddatum oder Fakturierungsstartdatum/Fakturierungsenddatum ist ungültig.|
> |**Name**:<br />ContractInvalidState<br />**Hex**:<br />80043203<br />**Nummer**:<br />-2147208701|Der Status des Vertrags ist ungültig.|
> |**Name**:<br />ContractLineInvalidState<br />**Hex**:<br />80043204<br />**Nummer**:<br />-2147208700|Der Status der Vertragszeile ist ungültig.|
> |**Name**:<br />ContractNoLineItems<br />**Hex**:<br />8004320c<br />**Nummer**:<br />-2147208692|Für diesen Vertrag gibt es keine Positionen.|
> |**Name**:<br />ContractTemplateDoesNotExist<br />**Hex**:<br />80043206<br />**Nummer**:<br />-2147208698|Die Vertragsvorlage ist nicht vorhanden.|
> |**Name**:<br />ContractTemplateNoAbbreviation<br />**Hex**:<br />8004320b<br />**Nummer**:<br />-2147208693|Abkürzung kann nicht NULL sein.|
> |**Name**:<br />ControlIdIsNotUnique<br />**Hex**:<br />80060411<br />**Nummer**:<br />-2147089391|Steuerelement-ID {0} in der XAML ist nicht eindeutig|
> |**Name**:<br />ControlIdIsNullOrEmpty<br />**Hex**:<br />80072344<br />**Nummer**:<br />-2147015868|Steuerelement-ID darf nicht Null oder leer sein.|
> |**Name**:<br />ConvertFetchDataSetError<br />**Hex**:<br />8004832e<br />**Nummer**:<br />-2147187922|Unerwarteter Fehler beim Verarbeiten des Fetch-Datensatzes.|
> |**Name**:<br />ConvertReportToCrmError<br />**Hex**:<br />8004832d<br />**Nummer**:<br />-2147187923|Unerwarteter Fehler beim Konvertieren des bereitgestellten Berichts in das Dynamics 365-Format.|
> |**Name**:<br />ConvertRuleActivateDeactivateByNonOwner<br />**Hex**:<br />8004F886<br />**Nummer**:<br />-2147157882|Dieser Konvertierungsregelsatz kann nur vom Besitzer aktiviert oder deaktiviert werden.|
> |**Name**:<br />ConvertRuleAlreadyActive<br />**Hex**:<br />80060731<br />**Nummer**:<br />-2147088591|Ausgewählte ConvertRule ist bereits aktiv. Wählen Sie einen anderen Datensatz aus und versuchen Sie es erneut.|
> |**Name**:<br />ConvertRuleAlreadyInDraftState <br />**Hex**:<br />80060732<br />**Nummer**:<br />-2147088590|Ausgewählte ConvertRule ist bereits im Entwurfstatus. Wählen Sie einen anderen Datensatz aus und versuchen Sie es erneut.|
> |**Name**:<br />ConvertRuleInvalidAutoResponseSettings<br />**Hex**:<br />8004F879<br />**Nummer**:<br />-2147157895|Wählen Sie eine E-Mail-Vorlage für eine automatische Antwort aus, oder legen Sie die Option für automatische Antworten auf "Nein" fest.|
> |**Name**:<br />ConvertRulePermissionToPerformAction<br />**Hex**:<br />80060733<br />**Nummer**:<br />-2147088589|Sie verfügen zum Durchführen dieser Aktion nicht über die erforderlichen Berechtigungen in  ConvertRules.|
> |**Name**:<br />ConvertRuleQueueIdMissingForEmailSource<br />**Hex**:<br />8004F896<br />**Nummer**:<br />-2147157866|Warteschlangenwert erforderlich. Sie müssen einen Wert für die Warteschlange angeben.|
> |**Name**:<br />ConvertRuleResponseTemplateValidity<br />**Hex**:<br />80060730<br />**Nummer**:<br />-2147088592|Wählen Sie entweder eine globale oder eine anfragenbasierte Vorlage aus.|
> |**Name**:<br />CopyGenericError<br />**Hex**:<br />80071027<br />**Nummer**:<br />-2147020761|Ein Fehler beim Kopieren von Dateien ist aufgetreten. Bitte versuchen Sie es später erneut. Falls das Problem weiterhin besteht, wenden Sie sich an den Systemadministrator.|
> |**Name**:<br />CopyNotAllowedForInternetMarketing<br />**Hex**:<br />80048474<br />**Nummer**:<br />-2147187596|Das Duplizieren von Kampagnen, die über Internetmarketing-Kampagnenaktivitäten verfügen, ist nicht zulässig|
> |**Name**:<br />CorruptedHiddensheetData<br />**Hex**:<br />800609B7<br />**Nummer**:<br />-2147087945|Die ausgeblendeten Blattdaten sind beschädigt.|
> |**Name**:<br />CouldNotDecryptOAuthToken<br />**Hex**:<br />8005F110<br />**Nummer**:<br />-2147094256|Das Yammer-OAuth-Token konnte nicht entschlüsselt werden. Versuchen Sie es noch einmal, Yammer umzukonfigurieren.|
> |**Name**:<br />CouldNotFindQueueItemInQueue<br />**Hex**:<br />80040524<br />**Nummer**:<br />-2147220188|Es wurde kein Warteschlangenelement gefunden, das dem Ziel im angegebenen SourceQueueId zugeordnet wurde. Entweder SourceQueueId oder Target ist ungültig, oder das Warteschlangenelement ist nicht vorhanden.|
> |**Name**:<br />CouldNotObtainLockOnResource<br />**Hex**:<br />80044339<br />**Nummer**:<br />-2147204295|Datenbankressourcensperre konnte nicht abgerufen werden. Weitere Informationen finden Sie unter http://docs.microsoft.com/dynamics365/customer-engagement/customize/best-practices-workflow-processes#limit-the-number-of-workflows-that-update-the-same-entity.|
> |**Name**:<br />CouldNotReadAccessToken<br />**Hex**:<br />8005F105<br />**Nummer**:<br />-2147094267|Das System konnte den Benutzern Yammer-Zugriffstoken nicht lesen, obwohl ein leerer Code nicht überschritten wurde.|
> |**Name**:<br />CouldNotSetLocationTypeToOneNote<br />**Hex**:<br />80060905<br />**Nummer**:<br />-2147088123|Der Typ des Speicherorts konnte für den Speicherort des Dokuments nicht auf OneNote festgelegt werden.|
> |**Name**:<br />CountSpecifiedWithoutOrder<br />**Hex**:<br />8004E01F<br />**Nummer**:<br />-2147164129|Die Diagrammbeschreibung für die Visualisierung ist ungültig, da kein Sortierungsknoten für das Anzahlattribut angegeben wird.|
> |**Name**:<br />CreatePropertyError<br />**Hex**:<br />8004F889<br />**Nummer**:<br />-2147157879|Fehler beim Speichern der {0}-Eigenschaft.|
> |**Name**:<br />CreatePropertyInstanceError<br />**Hex**:<br />8004F890<br />**Nummer**:<br />-2147157872|Fehler beim Speichern der {0}-Eigenschaftsinstanz.|
> |**Name**:<br />CreatePublishedWorkflowDefinitionWorkflowDependency<br />**Hex**:<br />8004500A<br />**Nummer**:<br />-2147201014|Eine Workflowabhängigkeit für eine veröffentlichte Workflowdefinition kann nicht erstellt werden.|
> |**Name**:<br />CreateRecurrenceRuleFailed<br />**Hex**:<br />8004E101<br />**Nummer**:<br />-2147163903|Serienregel kann nicht erstellt werden.|
> |**Name**:<br />CreateWorkflowActivationWorkflowDependency<br />**Hex**:<br />80045009<br />**Nummer**:<br />-2147201015|Eine Workflowabhängigkeit, die einer Workflowaktivierung zugeordnet ist, kann nicht erstellt werden.|
> |**Name**:<br />CreateWorkflowDependencyForPublishedTemplate<br />**Hex**:<br />80045019<br />**Nummer**:<br />-2147200999|Eine Workflowabhängigkeit für eine veröffentlichte Workflowvorlage kann nicht erstellt werden.|
> |**Name**:<br />CrmConstraintEvaluationError<br />**Hex**:<br />80040261<br />**Nummer**:<br />-2147220895|Auswertungsfehler bei der CRM-Einschränkung.|
> |**Name**:<br />CrmConstraintParsingError<br />**Hex**:<br />80040262<br />**Nummer**:<br />-2147220894|Analysefehler bei der CRM-Einschränkung.|
> |**Name**:<br />CrmExpressionBodyParsingError<br />**Hex**:<br />8004025e<br />**Nummer**:<br />-2147220898|Analysefehler beim CRM-Ausdruckstext.|
> |**Name**:<br />CrmExpressionEvaluationError<br />**Hex**:<br />80040260<br />**Nummer**:<br />-2147220896|Auswertungsfehler beim CRM-Ausdruck.|
> |**Name**:<br />CrmExpressionParametersParsingError<br />**Hex**:<br />8004025f<br />**Nummer**:<br />-2147220897|Analysefehler beim CRM-Ausdrucksparameter.|
> |**Name**:<br />CrmExpressionParsingError<br />**Hex**:<br />8004025d<br />**Nummer**:<br />-2147220899|Analysefehler beim CRM-Ausdruck.|
> |**Name**:<br />CrmHttpError<br />**Hex**:<br />8006088A<br />**Nummer**:<br />-2147088246|Ein Fehler ist in der Wep Api in Dynamics 365 aufgetreten.|
> |**Name**:<br />CrmImpersonationError<br />**Hex**:<br />80040245<br />**Nummer**:<br />-2147220923|Fehler im CRM-AutoReimpersonator.|
> |**Name**:<br />CrmLiveAddOnAddLicenseLimitReached<br />**Hex**:<br />8004B056<br />**Nummer**:<br />-2147176362|Ihr Abonnement hat die maimal zulässige Anzahl von Benuzterlizenzen erreicht.  Für weitere Lizenzen wenden Sie sich unter 1-877-Dynamics 365-CHOICE (276-2464) telefonisch an Ihre Vertriebsorganisation.|
> |**Name**:<br />CrmLiveAddOnAddStorageLimitReached<br />**Hex**:<br />8004B057<br />**Nummer**:<br />-2147176361|Ihr Speicherverbrauch hat die maximale Speicherbegrenzung erreicht, die für diese Umgebung festgelegt wurde. Testumgebungen werden mit beschränkten Mitteln zugeordnet. Wenn Sie keine Testumgebung verwenden, wenden Sie sich an den Support.|
> |**Name**:<br />CrmLiveAddOnDataChanged<br />**Hex**:<br />8004B05C<br />**Nummer**:<br />-2147176356|Aufgrund der neuen Änderungen, die Sie an die Firma vorgenommen haben, können diese Änderungen derzeit nicht vorgenommen werden.   Schließen Sie den Assistenten, und versuchen Sie es erneut.  Wenn das Problem weiterhin besteht, wenden Sie sich unter 1-877-Dynamics 365-CHOICE (276-2464) telefonisch an Ihre Vertriebsorganisation.|
> |**Name**:<br />CrmLiveAddOnOrgInNoUpdateMode<br />**Hex**:<br />8004B059<br />**Nummer**:<br />-2147176359|Die Änderungen können nicht zur Inanspruchnahme verarbeitet werden. Ihre Organisation wird derzeit aktualisiert.  Es wurden keine Änderungen an Ihrer Firma vorgenommen.  Schließen Sie den Assistenten, und versuchen Sie es erneut.  Wenn das Problem weiterhin besteht, wenden Sie sich unter 1-877-Dynamics 365-CHOICE (276-2464) telefonisch an Ihre Vertriebsorganisation.|
> |**Name**:<br />CrmLiveAddOnRemoveStorageLimitReached<br />**Hex**:<br />8004B058<br />**Nummer**:<br />-2147176360|Ihre Organisation hat die minimale Menge an zulässigem Speicherplatz.  Sie können nur Daten entfernen, die der Organisation hinzugefügt wurden, und nicht verwendet werden.|
> |**Name**:<br />CrmLiveAddOnUnexpectedError<br />**Hex**:<br />8004B055<br />**Nummer**:<br />-2147176363|Es gibt eine Fehlermeldung beim Kontaktieren des Zahlungssystems.  Die Anforderung kann derzeit nicht verarbeitet werden.  Es wurden keine Änderungen an Ihrer Firma vorgenommen.  Schließen Sie den Assistenten, und versuchen Sie es erneut.  Wenn das Problem weiterhin besteht, wenden Sie sich unter 1-877-Dynamics 365-CHOICE (276-2464) telefonisch an Ihre Vertriebsorganisation.|
> |**Name**:<br />CrmLiveCannotFindExternalMessageProvider<br />**Hex**:<br />8004B051<br />**Nummer**:<br />-2147176367|Externer Nachrichtenanbieter konnte nicht gefunden werden für Warteschlangenelementtyp: {0}.|
> |**Name**:<br />CrmLiveDnsDomainAlreadyExists<br />**Hex**:<br />8004B048<br />**Nummer**:<br />-2147176376|Die Domäne befindet sich bereits in der DNS-Tabelle.|
> |**Name**:<br />CrmLiveDnsDomainNotFound<br />**Hex**:<br />8004B047<br />**Nummer**:<br />-2147176377|Die Domäne wurde in der DNS-Tabelle nicht gefunden.|
> |**Name**:<br />CrmLiveDuplicateWindowsLiveId<br />**Hex**:<br />8004B046<br />**Nummer**:<br />-2147176378|Ein Benutzer mit diesem Benutzernamen ist bereits vorhanden.|
> |**Name**:<br />CrmLiveExecuteCustomCodeDisabled<br />**Hex**:<br />8004B063<br />**Nummer**:<br />-2147176349|Ausführung der benutzerdefinierten Codefunktion für die Organisation ist deaktiviert.|
> |**Name**:<br />CrmLiveGenericError<br />**Hex**:<br />8004B000<br />**Nummer**:<br />-2147176448|Ein Fehler beim Verarbeiten der Anforderung ist aufgetreten.|
> |**Name**:<br />CrmLiveInternalProvisioningError<br />**Hex**:<br />8004B003<br />**Nummer**:<br />-2147176445|Unerwarteter Fehler im Bereitstellungssystem.|
> |**Name**:<br />CrmLiveInvalidEmail<br />**Hex**:<br />8004B05D<br />**Nummer**:<br />-2147176355|Ungültige E-Mail-Adresse eingegeben.|
> |**Name**:<br />CrmLiveInvalidExternalMessageData<br />**Hex**:<br />8004B052<br />**Nummer**:<br />-2147176366|Externe Nachrichtendaten haben falsche Daten.  Daten: {0} Externe Meldung: {1}|
> |**Name**:<br />CrmLiveInvalidInvoicingAccountNumber<br />**Hex**:<br />8004B05B<br />**Nummer**:<br />-2147176357|Diese Fakturierungsfirmennummer ist ungültig, da sie ein ungültigen Zeichen enthält.|
> |**Name**:<br />CrmLiveInvalidPhone<br />**Hex**:<br />8004B05E<br />**Nummer**:<br />-2147176354|Ungültige Telefonnummer eingegeben.|
> |**Name**:<br />CrmLiveInvalidQueueItemSchedule<br />**Hex**:<br />8004B039<br />**Nummer**:<br />-2147176391|Das QueueItem hat einen ungültigen Zeitplan für Startzeit {0} und Endzeit {1}.|
> |**Name**:<br />CrmLiveInvalidSetupParameter<br />**Hex**:<br />8004B005<br />**Nummer**:<br />-2147176443|Der Parameter Online zu Setup Dynamics 365 Online Setup ist ungültig oder nicht angegeben.|
> |**Name**:<br />CrmLiveInvalidTaxId<br />**Hex**:<br />8004B064<br />**Nummer**:<br />-2147176348|Ungültige TaxId eingegeben.|
> |**Name**:<br />CrmLiveInvalidZipCode<br />**Hex**:<br />8004B05F<br />**Nummer**:<br />-2147176353|Ungültige Postleitzahl eingegeben.|
> |**Name**:<br />CrmLiveInvoicingAccountIdMissing<br />**Hex**:<br />8004B045<br />**Nummer**:<br />-2147176379|Fakturierungs-Firmennummer (SAP-ID) darf bei einer SKU nicht leer sein.|
> |**Name**:<br />CrmLiveMissingActiveDirectoryGroup<br />**Hex**:<br />8004B002<br />**Nummer**:<br />-2147176446|Die angegebene Active Directory-Gruppe ist nicht vorhanden.|
> |**Name**:<br />CrmLiveMissingServerRolesInScaleGroup<br />**Hex**:<br />8004B007<br />**Nummer**:<br />-2147176441|Der scalegroup fehlt einige erforderliche Serverrollen. 1 Zeugenserver und 2 SQL-Server sind für die Bereitstellung erforderlich.|
> |**Name**:<br />CrmLiveMonitoringOrganizationExistsInScaleGroup<br />**Hex**:<br />8004B026<br />**Nummer**:<br />-2147176410|Nur eine überwachende Organisation ist in einer Scalegruppe zugelassen.|
> |**Name**:<br />CrmLiveMultipleWitnessServersInScaleGroup<br />**Hex**:<br />8004B006<br />**Nummer**:<br />-2147176442|Das ScaleGroup hat mehrere bestimmte Zeugenserver. Hierbei sollte nur ein Zeugenserver in einer Skalierungsgruppe sein.|
> |**Name**:<br />CrmLiveOrganizationDeleteFailed<br />**Hex**:<br />8004B02E<br />**Nummer**:<br />-2147176402|Ein Fehler ist beim Löschen der Organisation aufgetreten.|
> |**Name**:<br />CrmLiveOrganizationDetailsNotFound<br />**Hex**:<br />8004B030<br />**Nummer**:<br />-2147176400|Organisationsdetails nicht gefunden.|
> |**Name**:<br />CrmLiveOrganizationDisableFailed<br />**Hex**:<br />8004B054<br />**Nummer**:<br />-2147176364|Deaktivierung der Organisation ist fehlgeschlagen.|
> |**Name**:<br />CrmLiveOrganizationEnableFailed<br />**Hex**:<br />8004B053<br />**Nummer**:<br />-2147176365|Aktivierung der Organisation ist fehlgeschlagen.|
> |**Name**:<br />CrmLiveOrganizationFriendlyNameTooLong<br />**Hex**:<br />8004B032<br />**Nummer**:<br />-2147176398|Der angegebene Organisationsname ist zu lang.|
> |**Name**:<br />CrmLiveOrganizationFriendlyNameTooShort<br />**Hex**:<br />8004B031<br />**Nummer**:<br />-2147176399|Der angegebene Organisationsname ist zu kurz.|
> |**Name**:<br />CrmLiveOrganizationProvisioningFailed<br />**Hex**:<br />8004B001<br />**Nummer**:<br />-2147176447|Ein Fehler ist bei der Bereitstellung der Organisation aufgetreten.|
> |**Name**:<br />CrmLiveOrganizationUniqueNameInvalid<br />**Hex**:<br />8004B035<br />**Nummer**:<br />-2147176395|Der eindeutige Name ist nicht gültig.|
> |**Name**:<br />CrmLiveOrganizationUniqueNameReserved<br />**Hex**:<br />8004B036<br />**Nummer**:<br />-2147176394|Der eindeutige Name ist bereits vergeben.|
> |**Name**:<br />CrmLiveOrganizationUniqueNameTooLong<br />**Hex**:<br />8004B034<br />**Nummer**:<br />-2147176396|Der eindeutige Name ist zu lang.|
> |**Name**:<br />CrmLiveOrganizationUniqueNameTooShort<br />**Hex**:<br />8004B033<br />**Nummer**:<br />-2147176397|Der eindeutige Name ist zu kurz.|
> |**Name**:<br />CrmLiveOrganizationUpgradeFailed<br />**Hex**:<br />8004B014<br />**Nummer**:<br />-2147176428|Upgrade von Crm-Organisation fehlgeschlagen.|
> |**Name**:<br />CrmLiveQueueItemDoesNotExist<br />**Hex**:<br />8004B004<br />**Nummer**:<br />-2147176444|Das definierte Warteschlangenelement ist in der Warteschlange nicht vorhanden. Es wurde möglicherweise gelöscht, oder seine ID wurde möglicherweise nicht korrekt angegeben|
> |**Name**:<br />CrmLiveQueueItemTimeInPast<br />**Hex**:<br />8004B040<br />**Nummer**:<br />-2147176384|Start oder Ende eines QueueItem kann nicht in der Vergangenheit geplant werden.|
> |**Name**:<br />CrmLiveRegisterCustomCodeDisabled<br />**Hex**:<br />8004B062<br />**Nummer**:<br />-2147176350|Anmeldung der benutzerdefinierten Codefunktion für die Organisation ist deaktiviert.|
> |**Name**:<br />CrmLiveServerCannotHaveWitnessAndDataServerRoles<br />**Hex**:<br />8004B008<br />**Nummer**:<br />-2147176440|Ein Server kann nicht Zeuge- und Datenserverrollen haben.|
> |**Name**:<br />CrmLiveSupportOrganizationExistsInScaleGroup<br />**Hex**:<br />8004B025<br />**Nummer**:<br />-2147176411|Nur eine Support-Organisation ist in einer Scalegruppe zugelassen.|
> |**Name**:<br />CrmLiveUnknownCategory<br />**Hex**:<br />8004B05A<br />**Nummer**:<br />-2147176358|Diese Kategorien ist ungültig.|
> |**Name**:<br />CrmLiveUnknownSku<br />**Hex**:<br />8004B041<br />**Nummer**:<br />-2147176383|Diese SKU-Kategorie ist ungültig.|
> |**Name**:<br />CrmMalformedExpressionError<br />**Hex**:<br />8004025c<br />**Nummer**:<br />-2147220900|Falsch formatierter CRM-Ausdrucksfehler.|
> |**Name**:<br />CrmQueryExpressionNotInitialized<br />**Hex**:<br />8004024d<br />**Nummer**:<br />-2147220915|QueryExpression wurde nicht initialisiert. Verwenden Sie den Konstruktor, der den Entitätsnamen nimmt, um eine Instanz zu initialisieren und ordnungsgemäß zu erstellen|
> |**Name**:<br />CrmSecurityError<br />**Hex**:<br />80040256<br />**Nummer**:<br />-2147220906|Ein Fehler ist in CrmSecurity aufgetreten.|
> |**Name**:<br />CrmSQLCharLengthTooLong<br />**Hex**:<br />80073001<br />**Nummer**:<br />-2147012607|Ein Validierungsfehler ist aufgetreten. Ein bereitgestellter Zeichenfolgenwert ist zu lang.|
> |**Name**:<br />CrmSqlGovernorDatabaseRequestDenied<br />**Hex**:<br />8004A001<br />**Nummer**:<br />-2147180543|Der Server ist ausgelastet und die Anforderung wurde nicht abgeschlossen. Versuchen Sie es später noch einmal.|
> |**Name**:<br />CrmSQLNetworkingError<br />**Hex**:<br />80073000<br />**Nummer**:<br />-2147012608|Ein Netzwerkfehler hat dazu geführt, dass dieser Vorgang fehlgeschlagen ist. Bitte wiederholen Sie den Vorgang.|
> |**Name**:<br />CrmSQLUniqueIndexOrConstraintViolation<br />**Hex**:<br />80073002<br />**Nummer**:<br />-2147012606|Bei dem Vorgang wurde versucht, einen doppelten Wert für ein Attribut mit einer eindeutigen Einschränkung einzufügen.|
> |**Name**:<br />CRMUserDoesNotExist<br />**Hex**:<br />80040354<br />**Nummer**:<br />-2147220652|Es ist kein Microsoft Dynamics 365-Benutzer mit dem angegebenen Domänennamen und der Benutzer-ID vorhanden.|
> |**Name**:<br />CrossEntityRelationshipInvalidOperation<br />**Hex**:<br />80092006<br />**Nummer**:<br />-2146885626|Ungültiger entitätsübergreifender Phasenübergang. Die angegebene Beziehung kann nicht verändert werden.|
> |**Name**:<br />CurrencyCannotBeNullDueToNonNullMoneyFields<br />**Hex**:<br />80048cfb<br />**Nummer**:<br />-2147185413|Die Währung darf nicht NULL sein.|
> |**Name**:<br />CurrencyFieldMissing<br />**Hex**:<br />8004E026<br />**Nummer**:<br />-2147164122|Zum Berechnen des Rollupfelds vom Typ 'Währung' ist eine Datensatzwährung erforderlich. Wählen Sie eine Währung und versuchen Sie es erneut.|
> |**Name**:<br />CurrencyNotEqual<br />**Hex**:<br />80048cea<br />**Nummer**:<br />-2147185430|Die Währung aus {0} entspricht nicht der Währung von {1}.|
> |**Name**:<br />CurrencyRequiredForDiscountTypeAmount<br />**Hex**:<br />80048cf7<br />**Nummer**:<br />-2147185417|Die Währung kann für Rabatttypbetrag nicht Null sein.|
> |**Name**:<br />CustomActionMustBeMarked<br />**Hex**:<br />80060381<br />**Nummer**:<br />-2147089535|Die benutzerdefinierte Aktion muss „Als Geschäftsprozessflow-Aktionsschritt” markiert werden, um sie als BPF-Aktionsschritt zu verwenden.|
> |**Name**:<br />CustomActivityCannotBeMailMergeEnabled<br />**Hex**:<br />8004F124<br />**Nummer**:<br />-2147159772|Bei einer benutzerdefinierten Entität, die als eine Aktivität definiert ist, kann MailMerge nicht aktiviert sein.|
> |**Name**:<br />CustomActivityInvalid<br />**Hex**:<br />8004501D<br />**Nummer**:<br />-2147200995|Ungültige benutzerdefinierte Aktivität.|
> |**Name**:<br />CustomActivityMustHaveOfflineAvailability<br />**Hex**:<br />8004F122<br />**Nummer**:<br />-2147159774|Eine als Aktivität definierte benutzerdefinierte Entität muss über Offlineverfügbarkeit verfügen.|
> |**Name**:<br />CustomControlsDependentPropertyConfiguration<br />**Hex**:<br />80160002<br />**Nummer**:<br />-2146041854|Eigenschaft "{0}" kann nur konfiguriert werden, wenn der Eigenschaft "{1}" ein Wert zugewiesen wurde.|
> |**Name**:<br />CustomControlsImportError<br />**Hex**:<br />80160000<br />**Nummer**:<br />-2146041856|Fehler beim Importieren von angepassten Steuerelementen. Versuchen Sie diese Lösung erneut zu importieren.|
> |**Name**:<br />CustomControlsPropertySetConfiguration<br />**Hex**:<br />80160003<br />**Nummer**:<br />-2146041853|Die Eigenschaft "{0}" kann erst konfiguriert werden, nachdem dem Dataset "{1}" ein Wert zugewiesen wurde.|
> |**Name**:<br />CustomerIsInactive<br />**Hex**:<br />80040517<br />**Nummer**:<br />-2147220201|Ein interaktiver Kunde kann nicht als übergeordnetes Element eines Objekts festgelegt werden.|
> |**Name**:<br />CustomerOpportunityRoleExists<br />**Hex**:<br />80048202<br />**Nummer**:<br />-2147188222|Kundenverkaufschancenrolle ist bereits vorhanden.|
> |**Name**:<br />CustomerRelationshipCannotBeDeleted<br />**Hex**:<br />8004847d<br />**Nummer**:<br />-2147187587|Diese Beziehung {1} wird vom Attribut {0} erforderlich und kann nicht gelöscht werden. Um diese Beziehung zu löschen, löschen Sie zunächst das Suchattribut.|
> |**Name**:<br />CustomerRelationshipExists<br />**Hex**:<br />80048201<br />**Nummer**:<br />-2147188223|Kundenbeziehung ist bereits vorhanden.|
> |**Name**:<br />CustomImageAttributeOnlyAllowedOnCustomEntity<br />**Hex**:<br />80048531<br />**Nummer**:<br />-2147187407|Ein benutzerdefiniertes Bildattribut kann nur einer benutzerdefinierten Entität nur hinzugefügt werden.|
> |**Name**:<br />CustomOperationNotActivated<br />**Hex**:<br />80045052<br />**Nummer**:<br />-2147200942|Die mit diesem Prozess verbundene Prozessaktion ist nicht aktiviert.|
> |**Name**:<br />CustomParentingSystemNotSupported<br />**Hex**:<br />80047102<br />**Nummer**:<br />-2147192574|Eine benutzerdefinierte Entität kann keine übergeordnete Beziehung mit einer Systementität haben|
> |**Name**:<br />CustomPeriodGoalHavingExtraInfo<br />**Hex**:<br />80044904<br />**Nummer**:<br />-2147202812|Ein Ziel des Typs "Benutzerdefinierte Zeitraum" müssen "Geschäftsjahr"- und "Buchhaltungsperiode"-Attribute leer gelassen werden.|
> |**Name**:<br />CustomPeriodGoalMissingInfo<br />**Hex**:<br />80044907<br />**Nummer**:<br />-2147202809|Für ein Ziel mit benutzerdefiniertem Zeitraum müssen die Attribute "goalstartdate" und "goalenddate" Daten enthalten.|
> |**Name**:<br />CustomReflexiveRelationshipNotAllowedForEntity<br />**Hex**:<br />8004432C<br />**Nummer**:<br />-2147204308|Diese Entität ist nicht für eine benutzerdefiniert Reflexivbeziehung gültig|
> |**Name**:<br />CustomWorkflowActivitiesNotSupported<br />**Hex**:<br />80045051<br />**Nummer**:<br />-2147200943|Benutzerdefinierte Workflowaktivitäten sind nicht aktiviert.|
> |**Name**:<br />CyclicalRelationship<br />**Hex**:<br />80047004<br />**Nummer**:<br />-2147192828|Die angegebene Beziehung resultiert in einem Zyklus.|
> |**Name**:<br />CyclicDependency<br />**Hex**:<br />80071156<br />**Nummer**:<br />-2147020458|Zyklische Komponentenabhängigkeit gefunden. Überprüfen Sie die Ausnahme, um weitere Informationen zu erhalten. Beheben Sie die ungültigen Abhängigkeiten und versuchen Sie noch einmal, den Vorgang durchzuführen. Details: {0}|
> |**Name**:<br />CyclicReferencesNotSupported<br />**Hex**:<br />8004417F<br />**Nummer**:<br />-2147204737|Die zyklischen Eingabe enthält einen Verweis, der nicht unterstützt wird.|
> |**Name**:<br />DatabaseCallsBlockedFailure<br />**Hex**:<br />80072401<br />**Nummer**:<br />-2147015679|Dieser Aufruf wird ggf. zu Aufrufen der Datenbank führen, die nicht zulässig sind.|
> |**Name**:<br />DatacenterNotAvailable<br />**Hex**:<br />8004B065<br />**Nummer**:<br />-2147176347|Dieser Datencenterendpunkt ist für die Organisation verfügbar.|
> |**Name**:<br />DataColumnsNumberMismatch<br />**Hex**:<br />80040345<br />**Nummer**:<br />-2147220667|Die Anzahl der Felder stimmt nicht mit der Anzahl der Spaltenüberschriften überein.|
> |**Name**:<br />DataEngineQueryThrottling<br />**Hex**:<br />80048544<br />**Nummer**:<br />-2147187388|Diese Abfrage kann nicht ausgeführt werden, da sie mit der Einschränkungsoptimierung.|
> |**Name**:<br />DatafieldNameShouldBeNull<br />**Hex**:<br />8006041b<br />**Nummer**:<br />-2147089381|ActionStep {0} verweist auf ungültigen DataFieldName {1}.|
> |**Name**:<br />DataMigrationManagerMandatoryUpdatesNotInstalled<br />**Hex**:<br />80044336<br />**Nummer**:<br />-2147204298|Die erstmalige Konfiguration des Datenmigrations-Managers wurde abgebrochen. Es ist nicht möglich, den Datenmigrations-Manager zu verwenden, wenn Konfiguration abgeschlossen ist.|
> |**Name**:<br />DataMigrationManagerUnknownProblem<br />**Hex**:<br />80044333<br />**Nummer**:<br />-2147204301|Der Datenmigrations-Manager fand ein unbekanntes Problem und kann nicht fortgesetzt werden. Starten Sie den Datenmigrationsmanager neu.|
> |**Name**:<br />DatasheetNotAvailable<br />**Hex**:<br />800609B5<br />**Nummer**:<br />-2147087947|Das Datenblatt ist nicht verfügbar.|
> |**Name**:<br />DataSourceInitializeFailedErrorCode<br />**Hex**:<br />8005F210<br />**Nummer**:<br />-2147094000|Wiederholen Sie den Vorgang. Besteht das Problem weiterhin, überprüfen Sie {0} auf Lösungen, oder wenden Sie sich an den {#Brand_CRM}-Administrator in Ihrer Organisation. Schließlich können Sie {1} kontaktieren.|
> |**Name**:<br />DataSourceOfflineErrorCode<br />**Hex**:<br />8005F211<br />**Nummer**:<br />-2147093999|Dieser Vorgang schlug fehl, da Sie offline sind. Stellen Sie die Verbindung wieder her und versuchen Sie es erneut.|
> |**Name**:<br />DataSourceProhibited<br />**Hex**:<br />8004830D<br />**Nummer**:<br />-2147187955|Eine nicht Fetch-basierte Datenquelle wird in diesem Bericht nicht zugelassen|
> |**Name**:<br />DataStoreKeyNotFoundErrorCode<br />**Hex**:<br />8005F21d<br />**Nummer**:<br />-2147093987|Nicht im lokalen Speicher mit Schlüssel "{0}"|
> |**Name**:<br />DataSyncNoContent<br />**Hex**:<br />80072512<br />**Nummer**:<br />-2147015406|Kein Datensynchronisierungsinhalt|
> |**Name**:<br />DataSyncRequestAccepted<br />**Hex**:<br />80072511<br />**Nummer**:<br />-2147015407|Datensynchronisierungsanforderung akzeptiert|
> |**Name**:<br />DataTableNotAvailable<br />**Hex**:<br />800609B0<br />**Nummer**:<br />-2147087952|Die ursprüngliche Datentabelle wurde gelöscht oder umbenannt.|
> |**Name**:<br />DataTypeMismatchForLinkedAttribute<br />**Hex**:<br />8004F0FC<br />**Nummer**:<br />-2147159812|Datentypkonflikt bei verknüpftem Attribut.|
> |**Name**:<br />DateTimeFormatFailed<br />**Hex**:<br />8004025a<br />**Nummer**:<br />-2147220902|Fehler bei der Erstellung eines formatierten Datum-Zeit-Werts.|
> |**Name**:<br />DecimalValueOutOfRange<br />**Hex**:<br />80044330<br />**Nummer**:<br />-2147204304|Ein Validierungsfehler ist aufgetreten. Einer der angegebenen Dezimalwerte liegt außerhalb des Bereichs der zulässigen Werte für dieses Attribut.|
> |**Name**:<br />DecoupleChildEntity<br />**Hex**:<br />80048206<br />**Nummer**:<br />-2147188218|Untergeordnete Entität kann nicht entkoppelt werden.|
> |**Name**:<br />DecoupleUserOwnedEntity<br />**Hex**:<br />80048207<br />**Nummer**:<br />-2147188217|Entitäten im Besitz eines Benutzers können ausschließlich entkoppelt werden.|
> |**Name**:<br />DecreasingDaysWillDeleteOlderData<br />**Hex**:<br />80060992<br />**Nummer**:<br />-2147087982|Wenn die Anzahl der Tage verringert wird, werden Mobile Offline-Daten, die älter als die angegebene Anzahl von Tagen sind, gelöscht.|
> |**Name**:<br />DefaultSiteCollectionUrlChanged<br />**Hex**:<br />8004F100<br />**Nummer**:<br />-2147159808|Die Standard-URL der Websitesammlung hat diese Organisation geändert, nachdem dieser Vorgang erstellt wurde.|
> |**Name**:<br />DefaultSiteMapDeleteFailure<br />**Hex**:<br />80048070<br />**Nummer**:<br />-2147188624|Standardsiteübersicht kann nicht gelöscht werden.|
> |**Name**:<br />DelegatedAdminUserCannotBeCreateNorUpdated<br />**Hex**:<br />80041d67<br />**Nummer**:<br />-2147213977|Die Benutzer des stellvertretenden Administrators kann nicht aktualisiert werden|
> |**Name**:<br />DeleteActiveWorkflowTemplateDependency<br />**Hex**:<br />8004501A<br />**Nummer**:<br />-2147200998|Eine Workflowabhängigkeit von einer veröffentlichten Workflowvorlage kann nicht gelöscht werden.|
> |**Name**:<br />DeletePublishedWorkflowDefinitionWorkflowDependency<br />**Hex**:<br />80045006<br />**Nummer**:<br />-2147201018|Eine Workflowabhängigkeit für eine veröffentlichte Workflowdefinition kann nicht gelöscht werden.|
> |**Name**:<br />DeleteWorkflowActivation<br />**Hex**:<br />80045004<br />**Nummer**:<br />-2147201020|Eine Workflowaktivierung kann nicht gelöscht werden.|
> |**Name**:<br />DeleteWorkflowActivationWorkflowDependency<br />**Hex**:<br />80045005<br />**Nummer**:<br />-2147201019|Eine Workflowabhängigkeit, die einer Workflowaktivierung zugeordnet ist, kann nicht gelöscht werden.|
> |**Name**:<br />DeleteWorkflowActiveDefinition<br />**Hex**:<br />8004500F<br />**Nummer**:<br />-2147201009|Eine aktive Workflowdefinition kann nicht gelöscht werden.|
> |**Name**:<br />DeleteWorkflowActiveTemplate<br />**Hex**:<br />8004501C<br />**Nummer**:<br />-2147200996|Eine aktive Workflowvorlage kann nicht gelöscht werden.|
> |**Name**:<br />DelveActionHubAttributeMissingInResponseException<br />**Hex**:<br />80071002<br />**Nummer**:<br />-2147020798|Das Attribut ist in der oData-Antwort des Austauschs nicht vorhanden.|
> |**Name**:<br />DelveActionHubAuthorizationFailureException<br />**Hex**:<br />80071007<br />**Nummer**:<br />-2147020793|Sie verfügen nicht die richtige Office 365-Lizenz, um Aktionen anzuzeigen. Wenden Sie sich an Ihren Systemadministrator.|
> |**Name**:<br />DelveActionHubDisabledError<br />**Hex**:<br />80071000<br />**Nummer**:<br />-2147020800|Die Delve-Aktivitätshub-Funktion ist nicht aktiviert.|
> |**Name**:<br />DelveActionHubInvalidResponseFormatException<br />**Hex**:<br />80071004<br />**Nummer**:<br />-2147020796|Ungültiges Antwortformat.|
> |**Name**:<br />DelveActionHubInvalidStateCodeException<br />**Hex**:<br />80071003<br />**Nummer**:<br />-2147020797|In dem Ausdruck wurde ein ungültiger Statusausdruck übergeben.|
> |**Name**:<br />DelveActionHubResponseRetievalFailureException<br />**Hex**:<br />80071005<br />**Nummer**:<br />-2147020795|Fehler beim Abrufen der Aktionen von Exchange.|
> |**Name**:<br />DelveActionHubS2SSetupFailureException<br />**Hex**:<br />80071008<br />**Nummer**:<br />-2147020792|Die Server-zu-Server-Authentifizierung mit Exchange ist für den Delve-Aktivitätshub nicht eingerichtet.|
> |**Name**:<br />DependencyAlreadyExists<br />**Hex**:<br />8004F01A<br />**Nummer**:<br />-2147160038|Eine {0} Abhängigkeit ist zwischen {1}({2}) und {3}({4}) bereits vorhanden.  {5}-Abhängigkeit kann nicht auch erstellt werden.|
> |**Name**:<br />DependencyTableNotEmpty<br />**Hex**:<br />8004F01B<br />**Nummer**:<br />-2147160037|Die Abhängigkeitstabelle muss leer sein, sodass die Initialisierung ordnungsgemäß abgeschlossen wird.|
> |**Name**:<br />DependencyTrackingClosed<br />**Hex**:<br />8004F025<br />**Nummer**:<br />-2147160027|Ungültiger Versuch, eine Abhängigkeit zu verarbeiten, nachdem der aktuellen Transaktionskontext geschlossen wurde.|
> |**Name**:<br />DeploymentServiceCannotChangeStateForDeploymentService<br />**Hex**:<br />8004D262<br />**Nummer**:<br />-2147167646|Sie können den Status des Servers nicht ändern, da die Bereitstellungs-Serviceserverrolle enthält.|
> |**Name**:<br />DeploymentServiceCannotDeleteOperationInProgress<br />**Hex**:<br />8004D265<br />**Nummer**:<br />-2147167643|Der Bereitstellungsdienst kann den angegebenen Vorgang nicht gelöscht, da er aktuell am Laufen ist.|
> |**Name**:<br />DeploymentServiceNotAllowOperation<br />**Hex**:<br />8004D261<br />**Nummer**:<br />-2147167647|Der Bereitstellungsdienst für {0} kann den {1}-Vorgang nicht zulassen.|
> |**Name**:<br />DeploymentServiceNotAllowSetToThisState<br />**Hex**:<br />8004D260<br />**Nummer**:<br />-2147167648|Der Bereitstellungsdienst für {0} lässt den Status "Aktiviert" oder "Deaktiviert" zu. Kann Status nicht auf {1} festlegen.|
> |**Name**:<br />DeploymentServiceOperationIdentifierNotFound<br />**Hex**:<br />8004D264<br />**Nummer**:<br />-2147167644|Der Bereitstellungsdienst kann einem zurückgestellten Vorgang nicht finden, der den angegebenen Bezeichner ist.|
> |**Name**:<br />DeploymentServiceRequestValidationFailure<br />**Hex**:<br />8004D263<br />**Nummer**:<br />-2147167645|Der Bereitstellungsdienst kann die Anfrage nicht verarbeiten, da mindestens eine Überprüfungen fehlgeschlagen ist.|
> |**Name**:<br />DeprecatedFormActivation<br />**Hex**:<br />8004F662<br />**Nummer**:<br />-2147158430|Das Formular wurde in der letzten Version abgelehnt und kann nicht mehr verwendet werden. Migrieren Sie bitte die Änderungen in ein anderes Format. Veraltete Formulare werden später vom System entfernt.|
> |**Name**:<br />DeprecatedMobileFormsCreation<br />**Hex**:<br />8004F667<br />**Nummer**:<br />-2147158425|Mobile Formulare wurden eingestellt. Neue Mobile Express-Formulare können nicht erstellt werden.|
> |**Name**:<br />DeprecatedMobileFormsEdit<br />**Hex**:<br />8004F668<br />**Nummer**:<br />-2147158424|Mobile Formulare wurden eingestellt. Der Mobilformulareditor kann nicht geöffnet werden.|
> |**Name**:<br />DeprovisionRIAccessNotAllowed<br />**Hex**:<br />80044274<br />**Nummer**:<br />-2147204492|Beziehungsinformationen können nur von einem Systemadministrator deaktiviert werden.|
> |**Name**:<br />DesignerAccessDenied<br />**Hex**:<br />80050100<br />**Nummer**:<br />-2147155712|Sie verfügen über keine ausreichende Berechtigung, um den angeforderten Vorgang auszuführen. Weitere Informationen erhalten Sie von Ihrem Administrator.|
> |**Name**:<br />DesignerInvalidParameter<br />**Hex**:<br />80050101<br />**Nummer**:<br />-2147155711|Die bereitgestellte {0} fehlt oder ist falsch. Versuchen Sie es noch einmal mit der korrekten {1}|
> |**Name**:<br />DestinationFolderNotExists<br />**Hex**:<br />80071022<br />**Nummer**:<br />-2147020766|Dokumente können nicht kopiert werden. Der Zieldokumentspeicherort ist nicht mehr vorhanden.|
> |**Name**:<br />DialogNameCannotBeNull<br />**Hex**:<br />80060873<br />**Nummer**:<br />-2147088269|"DialogName kann für ein Dialog nicht null ein|
> |**Name**:<br />DisabledCRMAddinLoadFailure<br />**Hex**:<br />80044202<br />**Nummer**:<br />-2147204606|Ein Fehler beim Laden der Microsoft Dynamics 365-Funktion ist aufgetreten. Starten Sie Outlook erneut. Wenden Sie sich an den Systemadministrator, wenn der Fehler weiterhin besteht.|
> |**Name**:<br />DisabledCRMClientVersionHigher<br />**Hex**:<br />80044204<br />**Nummer**:<br />-2147204604|Der Microsoft Dynamics 365 Server muss aktualisiert werden, bevor der Microsoft Dynamics 365-Client verwendet werden kann. Ihren Systemadministrator bei Fragen kontaktieren.|
> |**Name**:<br />DisabledCRMClientVersionLower<br />**Hex**:<br />80044203<br />**Nummer**:<br />-2147204605|Sie führen eine Version von Microsoft Dynamics 365 for Outlook aus, die nicht vom Offlinemodus mit dieser Microsoft Dynamics 365 Organisation {0} unterstützt wird. Sie müssen auf eine kompatiblen Version von Dynamics 365 for Outlook aktualisieren. Stellen Sie sicher, dass die Aktualisierung auf die kompatible Version bei der aktuellen Version von Dynamics 365 for Outlook unterstützt wird.|
> |**Name**:<br />DisabledCRMGoingOffline<br />**Hex**:<br />80044200<br />**Nummer**:<br />-2147204608|Die Microsoft Dynamics 365-Funktionalität ist während der Offlinesynchronisierung nicht verfügbar.|
> |**Name**:<br />DisabledCRMGoingOnline<br />**Hex**:<br />80044201<br />**Nummer**:<br />-2147204607|Die Microsoft Dynamics 365-Funktionalität ist während der Onlinesynchronisierung nicht verfügbar.|
> |**Name**:<br />DisabledCRMOnlineCrmNotAvailable<br />**Hex**:<br />80044206<br />**Nummer**:<br />-2147204602|Der Microsoft Dynamics 365 Server ist nicht verfügbar.|
> |**Name**:<br />DisabledCRMPostOfflineUpgrade<br />**Hex**:<br />80044205<br />**Nummer**:<br />-2147204603|Die Microsoft Dynamics 365-Funktionalität ist erst wieder verfügbar, wenn sich der Microsoft Dynamics 365-Client wieder im Onlinemodus befindet.|
> |**Name**:<br />DisableRIFeatureNotAllowed<br />**Hex**:<br />80044280<br />**Nummer**:<br />-2147204480|Sie benötigen Systemadministratorrechte, um Beziehungsinformationen für Ihre Organisation zu deaktivieren.|
> |**Name**:<br />DiscountAmount<br />**Hex**:<br />80043b20<br />**Nummer**:<br />-2147206368|Der Rabatttyp unterstützt nicht „Prozent”-Rabatte.|
> |**Name**:<br />DiscountAmountAndPercent<br />**Hex**:<br />80043b1f<br />**Nummer**:<br />-2147206369|Weder „Betrag” noch „Prozentsatz” können festgelegt werden.|
> |**Name**:<br />DiscountPercent<br />**Hex**:<br />80043b21<br />**Nummer**:<br />-2147206367|Der Rabatttyp unterstützt nicht „Betrag”-Rabatte.|
> |**Name**:<br />DiscountRangeOverlap<br />**Hex**:<br />80043b02<br />**Nummer**:<br />-2147206398|Die neuen Mengen überschneidet sich miot dem Bereich, der nach vorhandene Mengen abgedeckt ist.|
> |**Name**:<br />DiscountTypeAndPriceLevelCurrencyNotEqual<br />**Hex**:<br />80048cf8<br />**Nummer**:<br />-2147185416|Die Währung der Rabattanforderungen muss der gewünschten Währung der Preisliste für Rabatttypbetrag entsprechen.|
> |**Name**:<br />DiskSpaceNotEnough<br />**Hex**:<br />80050124<br />**Nummer**:<br />-2147155676|Es ist nicht genügend Speicherplatz im Temp-Ordner vorhanden.|
> |**Name**:<br />DistributeListAssociatedVary<br />**Hex**:<br />80048453<br />**Nummer**:<br />-2147187629|Die Kampagnenaktivität kann nicht verteilt werden. Seriendruck-Aktivität kann nur bei Marketinglisten durchgeführt werden, die alle vom gleichen Datensatztyp sind. Für diese Kampagnenaktivität entfernen Sie die Marketinglisten, damit das verbleibenden vom gleichen Datensatztyp sind, und versuchen Sie es anschließend erneut.|
> |**Name**:<br />DistributeNoListAssociated<br />**Hex**:<br />80048454<br />**Nummer**:<br />-2147187628|Die Kampagnenaktivität kann nicht verteilt werden. Dem sind keine Marketinglisten zugeordnet. Fügen Sie mindestens eine Marketingliste hinzu, und versuchen Sie es erneut.|
> |**Name**:<br />DocumentManagementDisabled<br />**Hex**:<br />8004F0FF<br />**Nummer**:<br />-2147159809|Dokumentverwaltung wurde für diese Organisation deaktiviert.|
> |**Name**:<br />DocumentManagementDisabledForEmail<br />**Hex**:<br />80050010<br />**Nummer**:<br />-2147155952|Die Dokumentenverwaltung muss für die E-Mail-Entität aktiviert werden, damit Anlagen verfolgt werden können. Wenden Sie sich an Ihren Administrator um Dokumentenverwaltung zu aktivieren.|
> |**Name**:<br />DocumentManagementDisabledOnEntity<br />**Hex**:<br />80060908<br />**Nummer**:<br />-2147088120|Sie müssen die Dokumentenverwaltung für diese Entität aktivieren, um die OneNote-Integration zu aktivieren.|
> |**Name**:<br />DocumentManagementIsDisabled<br />**Hex**:<br />8004F312<br />**Nummer**:<br />-2147159278|Die Dokumentenverwaltung ist für diese Organisation nicht aktiviert.|
> |**Name**:<br />DocumentManagementIsDisabledOnEntity<br />**Hex**:<br />80071011<br />**Nummer**:<br />-2147020783|Sie müssen die Dokumentenverwaltung für diese Entität aktivieren, um die Dokumentenempfehlungen  zu aktivieren.|
> |**Name**:<br />DocumentManagementNotEnabledNoPrimaryField<br />**Hex**:<br />8004F313<br />**Nummer**:<br />-2147159277|Die Dokumentenverwaltung konnte nicht aktiviert werden, da kein Hauptfeld für diese Entität mit dem Namen {0} und der ID {1} definiert wurde.|
> |**Name**:<br />DocumentRecommendationsFCBOff<br />**Hex**:<br />80071019<br />**Nummer**:<br />-2147020775|Die Dokumentvorschlagsfunktion ist nicht aktiviert.|
> |**Name**:<br />DocumentTemplateFeatureNotEnabled<br />**Hex**:<br />800608C9<br />**Nummer**:<br />-2147088183|Die Dokumentvorlagefunktion ist nicht aktiviert.|
> |**Name**:<br />DocxExportGeneratingWordFailed<br />**Hex**:<br />800608CD<br />**Nummer**:<br />-2147088179|Beim Erstellen des Word-Dokuments ist ein Fehler aufgetreten. Bitte wiederholen Sie den Vorgang.|
> |**Name**:<br />DocxValidationFailed<br />**Hex**:<br />800608CE<br />**Nummer**:<br />-2147088178|Das Hochladen ist fehlgeschlagen, da die ausgewählten Datei nicht mit dem Vorlagenlayout konsistent ist. Bitte versuchen Sie es noch einmal, nachdem Sie eine Datei mit dem Vorlagenlayout ausgewählt haben.|
> |**Name**:<br />DoNotTrackItem<br />**Hex**:<br />80044228<br />**Nummer**:<br />-2147204568|Das ausgewählte Element kann nicht in  nachverfolgt werden.|
> |**Name**:<br />DownloadAllEntityRecordsChangedOrCreatedWithinTheseDays<br />**Hex**:<br />8006098F<br />**Nummer**:<br />-2147087985|Laden Sie alle Entitätsdatensätze herunter, die innerhalb dieser Anzahl von Tagen geändert oder erstellt wurden.|
> |**Name**:<br />DownloadRelatedDataOnlyMustHaveRelationship<br />**Hex**:<br />80071140<br />**Nummer**:<br />-2147020480|Die Entität „{0}” im Profil '„{1}” wurde nur mit den mit dem Filterdownload verknüpften Daten konfiguriert, es wurden jedoch keine Beziehungen für diese Entität in Profilelementzuordnungen angegeben. Wenn eine Entität so eingerichtet wurde, dass nur zugehörige Daten heruntergeladen werden, müssen Sie ein Profilelementzuordnung für diese Entität angeben.|
> |**Name**:<br />DraftBundleToProduct<br />**Hex**:<br />8004F994<br />**Nummer**:<br />-2147157612|Sie können einem Entwurfspaket nur Produkte hinzufügen.|
> |**Name**:<br />DuplicateAliasFound<br />**Hex**:<br />8004E00B<br />**Nummer**:<br />-2147164149|Die Datenbeschreibung ist ungültig. Doppelten Alias gefunden.|
> |**Name**:<br />DuplicateApplicationUser<br />**Hex**:<br />8004F511<br />**Nummer**:<br />-2147158767|Sie versuchen, eine Anwendung = ID erstellen, {0} die zwar bereits vorhanden ist.|
> |**Name**:<br />DuplicateAppModuleUniqueName<br />**Hex**:<br />8005011F<br />**Nummer**:<br />-2147155681|Der eingegebene Name wird bereits verwendet.|
> |**Name**:<br />DuplicateAttributePhysicalName<br />**Hex**:<br />80060304<br />**Nummer**:<br />-2147089660|Das Attribut {0} ist für die Entität {1} bereits vorhanden.|
> |**Name**:<br />DuplicateAttributeSchemaName<br />**Hex**:<br />80047013<br />**Nummer**:<br />-2147192813|Ein Attribut mit dem angegebenen Namen ist bereits vorhanden.|
> |**Name**:<br />DuplicateChannelPropertyName<br />**Hex**:<br />800608F1<br />**Nummer**:<br />-2147088143|Es ist bereits eine Kanaleigenschaft mit dem angegebenen Namen vorhanden. Sie können keine andere erstellen.|
> |**Name**:<br />DuplicateCheckNotEnabled<br />**Hex**:<br />80048412<br />**Nummer**:<br />-2147187694|Die Duplikaterkennung ist nicht aktiviert. Wenn Sie die Duplikaterkennung aktivieren möchten, klicken Sie auf 'Einstellungen', klicken Sie auf 'Datenverwaltung', und klicken Sie dann auf 'Einstellungen für die Duplikaterkennung'.|
> |**Name**:<br />DuplicateCheckNotSupportedOnEntity<br />**Hex**:<br />80048410<br />**Nummer**:<br />-2147187696|Die Duplikaterkennung wird für diesen Datensatztyp nicht unterstützt.|
> |**Name**:<br />DuplicateComponentInSolutionXml<br />**Hex**:<br />80071153<br />**Nummer**:<br />-2147020461|Doppelte Komponente ist im XML vorhanden.|
> |**Name**:<br />DuplicateDetectionNotSupportedOnAttributeType<br />**Hex**:<br />80048430<br />**Nummer**:<br />-2147187664|Die Regelbedingung kann nicht erstellt oder aktualisiert werden, da die Duplikaterkennung nicht auf dem ausgewählten Datentyp des Attributs unterstützt wird.|
> |**Name**:<br />DuplicateDetectionRulesWereUnpublished<br />**Hex**:<br />8004F039<br />**Nummer**:<br />-2147160007|Die Veröffentlichung der Duplikaterkennungsregeln für diese Entität wurde aufgrund möglicher Änderungen an der Entität aufgehoben.|
> |**Name**:<br />DuplicateDetectionTemplateNotFound<br />**Hex**:<br />80048424<br />**Nummer**:<br />-2147187676|Die E-Mail-Benachrichtigungsvorlage konnte von Microsoft Dynamics 365 nicht abgerufen werden.|
> |**Name**:<br />DuplicateDisplayCollectionName<br />**Hex**:<br />80047012<br />**Nummer**:<br />-2147192814|Ein Objekt mit dem angegebenen Anzeigesammlungsname ist bereits vorhanden.|
> |**Name**:<br />DuplicateDisplayName<br />**Hex**:<br />80047011<br />**Nummer**:<br />-2147192815|Ein Objekt mit dem angegebenen Anzeigename ist bereits vorhanden.|
> |**Name**:<br />DuplicatedJobId<br />**Hex**:<br />80071152<br />**Nummer**:<br />-2147020462|Der Parameter ImportJobId muss eindeutig sein.|
> |**Name**:<br />DuplicatedJobIdDueToConcurrency<br />**Hex**:<br />80071155<br />**Nummer**:<br />-2147020459|Der Lösungsauftrag kann nicht mithilfe der angegebenen JobId ({0}) erstellt werden, da sie bereits verwendet wird. Dies kann darauf hindeuten, dass gerade ein anderer Lösungsvorgang ausgeführt wird. Versuchen Sie es später noch einmal.|
> |**Name**:<br />DuplicatedPrivilege<br />**Hex**:<br />8004140f<br />**Nummer**:<br />-2147216369|Recht {0} wird dupliziert.|
> |**Name**:<br />DuplicateFileNamesInZip<br />**Hex**:<br />80048484<br />**Nummer**:<br />-2147187580|Zwei oder mehr Dateien haben denselben Namen. Dateinamen müssen eindeutig sein.|
> |**Name**:<br />DuplicateGroupByFound<br />**Hex**:<br />8004E01B<br />**Nummer**:<br />-2147164133|Die Datenbeschreibung ist ungültig. Das gleiche Attribut kann nicht als eine Gruppe mehrmals verwendet werden.|
> |**Name**:<br />DuplicateHeaderColumn<br />**Hex**:<br />80040338<br />**Nummer**:<br />-2147220680|Es ist eine doppelte Spaltenüberschrift vorhanden.|
> |**Name**:<br />DuplicateIsoCurrencyCode<br />**Hex**:<br />80048cf3<br />**Nummer**:<br />-2147185421|Kann doppelten Währungsdatensatz nicht einfügen. Währung mit demselben Währungscode ist bereits im System vorhanden.|
> |**Name**:<br />DuplicateLookupFound<br />**Hex**:<br />80040352<br />**Nummer**:<br />-2147220654|Ein doppelter Suchverweis wurde gefunden.|
> |**Name**:<br />DuplicateMapName<br />**Hex**:<br />80048443<br />**Nummer**:<br />-2147187645|Es ist bereits eine Datenzuordnung mit dem angegebenen Namen vorhanden.|
> |**Name**:<br />DuplicateName<br />**Hex**:<br />80047010<br />**Nummer**:<br />-2147192816|Ein Objekt mit dem angegebenen Namen ist bereits vorhanden.|
> |**Name**:<br />DuplicateOfflineFilter<br />**Hex**:<br />80048449<br />**Nummer**:<br />-2147187639|Sie können nur einen Datensatztyp für eine lokale Datengruppe erstellen.|
> |**Name**:<br />DuplicateOutlookAppointment<br />**Hex**:<br />80040274<br />**Nummer**:<br />-2147220876|Der Termink der vom Outlook bereitgestellt wird, wird bereits in Dynamics 365 nachverfolgt.|
> |**Name**:<br />DuplicatePrimaryNameAttribute<br />**Hex**:<br />8004701E<br />**Nummer**:<br />-2147192802|Das neue {2} Attritut verfügt bereits über das Hauptnamenattribut für die {1} Entität. Die {1} Entität verfügt bereits das A{0} Attribut, das als primäres Namensattribut festgelegt ist. Eine Entität kann nur ein primäres Namensattribut haben.|
> |**Name**:<br />DuplicatePrivilegeInRolecontrol<br />**Hex**:<br />80061118<br />**Nummer**:<br />-2147086056|Das Kanalzugriffsprofil-Rechtearray enthält doppelte Rechtereferenzen.|
> |**Name**:<br />DuplicateProductPriceLevel<br />**Hex**:<br />80043b08<br />**Nummer**:<br />-2147206392|Diese Kombination aus Produkt und Einheit hat einen Preis für diese Preisliste.|
> |**Name**:<br />DuplicateProductRelationship<br />**Hex**:<br />8004F891<br />**Nummer**:<br />-2147157871|Eine Produktbeziehung mit demselben Produkt und einem verknüpften Produkt ist bereits vorhanden.|
> |**Name**:<br />DuplicateRecord<br />**Hex**:<br />80040237<br />**Nummer**:<br />-2147220937|Vorgang aufgrund einer SQL-Integritätsverletzung fehlgeschlagen.|
> |**Name**:<br />DuplicateRecordEntityKey<br />**Hex**:<br />80060892<br />**Nummer**:<br />-2147088238|Entitätsschlüssel {0} verletzt. Ein Datensatz mit dem gleichen Wert für {1} ist bereits vorhanden. Ein doppelter Datensatz kann nicht erstellt werden. Wählen Sie mindestens einen eindeutigen Werte und versuchen Sie es erneut aus.|
> |**Name**:<br />DuplicateRecordsFound<br />**Hex**:<br />80040333<br />**Nummer**:<br />-2147220685|Ein Datensatz wurde weder erstellt noch aktualisiert, da bereits ein Duplikat des aktuellen Datensatzes vorhanden ist.|
> |**Name**:<br />DuplicateReportVisibility<br />**Hex**:<br />80040495<br />**Nummer**:<br />-2147220331|Ein ReportVisibility mit derselben ReportId und VisibilityCode ist bereits vorhanden. Duplikate sind nicht zulässig.|
> |**Name**:<br />DuplicateSalesTeamMember<br />**Hex**:<br />80048341<br />**Nummer**:<br />-2147187903|Der Benutzer, den Sie hinzufügen möchten, gehört bereits zum Vertriebsteam.|
> |**Name**:<br />DuplicateUIStatementRootsFound<br />**Hex**:<br />8004F201<br />**Nummer**:<br />-2147159551|Es kann nur Stammbestimmung für ein gegebenes uiscript geben.|
> |**Name**:<br />DynamicPropertyDefaultValueNeeded<br />**Hex**:<br />80061038<br />**Nummer**:<br />-2147086280|Sie müssen einen Standardwert angeben, da diese Eigenschaft erforderlich und schreibgeschützt ist.|
> |**Name**:<br />DynamicPropertyInstanceMissingRequiredColumns<br />**Hex**:<br />8008100A<br />**Nummer**:<br />-2146955254|Die Eigenschafteninstanz kann nicht aktualisiert werden. Stellen Sie sicher, dass die folgenden Felder vorhanden sind: dynamicpropertyid, dynamicpropertyoptionsetvalueid und regardingobjectid.|
> |**Name**:<br />DynamicPropertyInstanceUpdateValuesDifferentRegarding<br />**Hex**:<br />8008100B<br />**Nummer**:<br />-2146955253|Die Eigenschafteninstanzen können nicht gespeichert werden, da sie auf ander Produktlinieelemente verweisen.|
> |**Name**:<br />DynamicPropertyInvalidRegardingForUpdate<br />**Hex**:<br />80081004<br />**Nummer**:<br />-2146955260|Sie können eine veröffentlichte Eigenschaften oder zurückgezogenes Produkt nicht erstellen oder ändern.|
> |**Name**:<br />DynamicPropertyInvalidStateChange<br />**Hex**:<br />80081001<br />**Nummer**:<br />-2146955263|Sie können keine inaktive Eigenschaft in einen aktiven Status versetzen.|
> |**Name**:<br />DynamicPropertyInvalidStateForDelete<br />**Hex**:<br />80081002<br />**Nummer**:<br />-2146955262|Sie können keine Eigenschaft im aktiven Zustand löschen.|
> |**Name**:<br />DynamicPropertyInvalidStateForUpdate<br />**Hex**:<br />80081000<br />**Nummer**:<br />-2146955264|Sie können keine Eigenschaft im Entwurfzustand aktualisieren.|
> |**Name**:<br />DynamicPropertyOptionSetInvalidStateForUpdate<br />**Hex**:<br />8008100C<br />**Nummer**:<br />-2146955252|Sie können das Optionssatzelement der Eigenschaft für eine Eigenschaft, die keinen Entwurfsstatus aufweist, nicht ändern.|
> |**Name**:<br />EditorOnlySupportAndOperatorForLogicalConditions<br />**Hex**:<br />80060005<br />**Nummer**:<br />-2147090427|Der Regelausdruck enthält einen logischen Operator, der nicht unterstützt wird. Der Editor unterstützt und betreibt logische Bedingungen.|
> |**Name**:<br />EditQueryInDynamicExcelNotSupported<br />**Hex**:<br />800609B8<br />**Nummer**:<br />-2147087944|Sie können die Abfrage nicht mehr in einer dynamische Tabelle bearbeiten, nachdem die Excel-Datei exportiert wurde. Wenn Sie Änderungen vornehmen möchten, wechseln Sie wieder zu Dynamics 365 und exportieren Sie dann erneut.|
> |**Name**:<br />EESiteDBFetchFailure<br />**Hex**:<br />80050025<br />**Nummer**:<br />-2147155931|Daten können nicht von der Website-Datenbank abgerufen werden.|
> |**Name**:<br />EmailAlreadyExistsInDestinationQueue<br />**Hex**:<br />80040523<br />**Nummer**:<br />-2147220189|Sie können die E-Mail nicht einer ausgewählten …Warteschlange hinzufügen. Ein Warteschlangenelement für diese E-Mail ist bereits in der Warteschlange vorhanden. Sie können Element aus der Warteschlange löschen und es dann erneut versuchen.|
> |**Name**:<br />EmailDoesNotExist<br />**Hex**:<br />80050007<br />**Nummer**:<br />-2147155961|Für die angegebene Anlage ist keine E-Mail vorhanden.|
> |**Name**:<br />EmailEngagementFeatureDisabled<br />**Hex**:<br />80050003<br />**Nummer**:<br />-2147155965|Aktivieren Sie das E-Mail-Nutzungsfeature für die aktuelle Organisation, um der E-Mail-Anlage zu folgen bzw. nicht mehr zu folgen.|
> |**Name**:<br />EmailEngagementFeatureDisabledForAttachmentTracking<br />**Hex**:<br />80050015<br />**Nummer**:<br />-2147155947|Aktivieren Sie das E-Mail-Nutzungsfeature für die aktuelle Organisation, um der E-Mail-Anlage zu folgen bzw. nicht mehr zu folgen.|
> |**Name**:<br />EmailInteractionsFetchFailure<br />**Hex**:<br />80050022<br />**Nummer**:<br />-2147155934|E-Mail-Interaktionen konnten nicht abgerufen werden.|
> |**Name**:<br />EmailMessageSizeExceeded<br />**Hex**:<br />8005E237<br />**Nummer**:<br />-2147098057|Die E-Mail-Größe überschreitet MaximumMessageSizeLimit, das von der Bereitstellung angegeben wird.|
> |**Name**:<br />EmailMonitoringDeProvisionFailed<br />**Hex**:<br />80050014<br />**Nummer**:<br />-2147155948|Fehler beim Deprovisioning der E-Mail-Engagement-Funktion|
> |**Name**:<br />EmailMonitoringNotProvisioned<br />**Hex**:<br />80050011<br />**Nummer**:<br />-2147155951|RI Bereitstellungsdienst fehlgeschlagen.|
> |**Name**:<br />EmailMonitoringProvisionFailed<br />**Hex**:<br />80050012<br />**Nummer**:<br />-2147155950|Fehler beim Bereitstellen der E-Mail-Engagement-Funktion|
> |**Name**:<br />EmailNotFollowed<br />**Hex**:<br />80050008<br />**Nummer**:<br />-2147155960|Dieser Anlage kann nicht gefolgt werden, da der zugehörigen E-Mail nicht gefolgt wird.|
> |**Name**:<br />EmailOpenActionCardCreationFailure<br />**Hex**:<br />80050024<br />**Nummer**:<br />-2147155932|Wir können keine Aktionskarte zum Öffnen von E-Mails erstellen.|
> |**Name**:<br />EmailRecipientNotSpecified<br />**Hex**:<br />80040b04<br />**Nummer**:<br />-2147218684|Es muss mindestens ein Empfänger festgelegt sein, bevor die E-Mail-Nachricht gesendet werden kann.|
> |**Name**:<br />EmailReminderActionCardCreationFailure<br />**Hex**:<br />80050023<br />**Nummer**:<br />-2147155933|Wir können keine Aktionskarte zum Erinnern an E-Mails erstellen.|
> |**Name**:<br />EmailRouterFileTooLargeToProcess<br />**Hex**:<br />8005F031<br />**Nummer**:<br />-2147094479|Mindestens eine Konfigurationsdatei für den E-Mail-Router ist zu groß, um sie zu verarbeiten.|
> |**Name**:<br />EmailServerProfileADBasedAuthenticationProtocolNotAllowed<br />**Hex**:<br />8005E23C<br />**Nummer**:<br />-2147098052|Das Authentifizierungsprotokoll kann nicht auf Verhandeln oder NTLM für Ihre Organisation festgelegt werdenm, da diese ein Active Directory erfordern. Verwenden Sie ein anderes Authentifizierungsprotokoll oder wenden Sie sich an den Administrator, um Standardauthentifizierungsprotokoll in einem nicht gesicherten Kanal zu aktivieren.|
> |**Name**:<br />EmailServerProfileAutoDiscoverNotAllowed<br />**Hex**:<br />8005E204<br />**Nummer**:<br />-2147098108|Automatische Ermittlung der Server-URL kann nur für einen Exchange-E-Mail-Servertyp verwendet werden.|
> |**Name**:<br />EmailServerProfileBasicAuthenticationProtocolNotAllowed<br />**Hex**:<br />8005E23D<br />**Nummer**:<br />-2147098051|Das angegebene Authentifizierungsprotokoll kann nicht verwendet werden, da das Protokoll Senden von Anmeldeinformationen auf einem sicheren Kanal erforderlich. Verwenden Sie ein anderes Authentifizierungsprotokoll oder wenden Sie sich an den Administrator, um Standardauthentifizierungsprotokoll in einem nicht gesicherten Kanal zu aktivieren.|
> |**Name**:<br />EmailServerProfileDelegateAccessNotAllowed<br />**Hex**:<br />8005E235<br />**Nummer**:<br />-2147098059|Bei einem SMTP-E-Mail-Servertyp kann der automatisch erteilte Stellvertretungszugriff kann nicht verwendet werden.|
> |**Name**:<br />EmailServerProfileImpersonationNotAllowed<br />**Hex**:<br />8005E236<br />**Nummer**:<br />-2147098058|Bei einen E-Mail-Server der nicht vom Typ Exchange ist, kann Identitätswechsel nicht verwendet werden.|
> |**Name**:<br />EmailServerProfileInvalidAuthenticationProtocol<br />**Hex**:<br />8005E23B<br />**Nummer**:<br />-2147098053|Das Authentifizierungsprotokoll ist auf dem angegebenen Server und für die Verbindungsart ungültig. Weitere Informationen erhalten Sie vom zuständigen Systemadministrator.|
> |**Name**:<br />EmailServerProfileInvalidCredentialRetrievalForExchange<br />**Hex**:<br />8005E203<br />**Nummer**:<br />-2147098109|Keine Anmeldeinformationen (anonym) können für einen Verbindungstyp für einen Exchange-E-Mail-Servertyp verwendet werden.|
> |**Name**:<br />EmailServerProfileInvalidCredentialRetrievalForOnline<br />**Hex**:<br />8005E202<br />**Nummer**:<br />-2147098110|Sie können „Integrierte Windows-Authentifizierung” oder „Ohne Anmeldeinformationen (anonym)” nicht als Verbindungstyp für Microsoft Dynamics 365 Online auswählen.|
> |**Name**:<br />EmailServerProfileInvalidServerLocation<br />**Hex**:<br />8005E20A<br />**Nummer**:<br />-2147098102|De angegebene Serverstandort {0} ist ungültig. Korrigieren Sie den Serverstandort und versuchen Sie es erneut.|
> |**Name**:<br />EmailServerProfileLocationNotRequired<br />**Hex**:<br />8005E205<br />**Nummer**:<br />-2147098107|Sie können den Serverstandort für eingehenden und ausgehende E-Mails-nicht angeben, wenn Autodiscover-Serverspeicherort auf true festgelegt wurde.|
> |**Name**:<br />EmailServerProfileNotAssociated<br />**Hex**:<br />8005E222<br />**Nummer**:<br />-2147098078|Das E-Mail-Server-Profil ist dem aktuellen Postfach nicht zugeordnet. Ordnen Sie bitte ein gültiges Profil zu, um E-Mails zu senden und zu empfangen.|
> |**Name**:<br />EmailServerProfileSslRequiredForOnline<br />**Hex**:<br />8005E201<br />**Nummer**:<br />-2147098111|Sie können SSL nicht als false für Microsoft Dynamics 365 Online festlegen.|
> |**Name**:<br />EmailServerProfileSslRequiredForOnPremise<br />**Hex**:<br />8005E234<br />**Nummer**:<br />-2147098060|Verwendung von SSL beim Kontakt mit externen E-Mail-Servern ist zwingend mit diese Dynamics 365 Bereitstellung.|
> |**Name**:<br />EmptyCommandOrEntity<br />**Hex**:<br />80154B51<br />**Nummer**:<br />-2146088111|Der Befehl oder Entitätsname darf nicht leer sein.|
> |**Name**:<br />EmptyContent<br />**Hex**:<br />80040365<br />**Nummer**:<br />-2147220635|Die Datei ist leer.|
> |**Name**:<br />EmptyEntityFilterXml<br />**Hex**:<br />80071118<br />**Nummer**:<br />-2147020520|FetchXML ist nicht vorhanden.|
> |**Name**:<br />EmptyFileForImport<br />**Hex**:<br />80048487<br />**Nummer**:<br />-2147187577|Die ausgewählte Datei enthält keine Daten.|
> |**Name**:<br />EmptyFilesInZip<br />**Hex**:<br />80048486<br />**Nummer**:<br />-2147187578|Ein oder mehrere Dateien in der komprimierten (ZIP-Datei) oder CAB-Datei enthalten keine Daten. Überprüfen Sie die Dateien und versuchen Sie es erneut.|
> |**Name**:<br />EmptyHeaderColumn<br />**Hex**:<br />80040337<br />**Nummer**:<br />-2147220681|Die Spaltenüberschrift muss angegeben sein.|
> |**Name**:<br />EmptyHeaderRow<br />**Hex**:<br />80040366<br />**Nummer**:<br />-2147220634|Die erste Zeile der Datei ist leer.|
> |**Name**:<br />EmptyImportFileRow<br />**Hex**:<br />80040347<br />**Nummer**:<br />-2147220665|Leere Zeile.|
> |**Name**:<br />EmptyRecord<br />**Hex**:<br />80040373<br />**Nummer**:<br />-2147220621|Der Datensatz ist leer.|
> |**Name**:<br />EmptySecretInDataSource<br />**Hex**:<br />80044818<br />**Nummer**:<br />-2147203048|Datenquellengeheimnisse sind nicht in Lösungen enthalten. Sie müssen die Datenquellen bearbeiten, um die geheimen Schlüssel nach dem Lösungsimport wieder hinzuzufügen.|
> |**Name**:<br />EmptySiteMapXml<br />**Hex**:<br />8004F402<br />**Nummer**:<br />-2147159038|Sitemap-XML ist leer.|
> |**Name**:<br />EmptyXml<br />**Hex**:<br />80040202<br />**Nummer**:<br />-2147220990|Leere XML.|
> |**Name**:<br />EnableMobileOfflineDisableChangeTrackingError<br />**Hex**:<br />800609A2<br />**Nummer**:<br />-2147087966|Sie müssen die Änderungsnachverfolgung für Entitäten aktivieren, da der Mobile Offline Client aktiviert ist.|
> |**Name**:<br />EnableRIFeatureNotAllowed<br />**Hex**:<br />80044279<br />**Nummer**:<br />-2147204487|Sie benötigen Systemadministratorrechte, um Beziehungsinformationen für die Mandanten zu aktualisieren.|
> |**Name**:<br />EndUserNotificationTypeNotValidForEmail<br />**Hex**:<br />8004D291<br />**Nummer**:<br />-2147167599|Kann E-Mail für EndUserNotifications-Typ nicht senden: {0}.|
> |**Name**:<br />EntitiesExceedMaxAllowed<br />**Hex**:<br />80060415<br />**Nummer**:<br />-2147089387|Sie können maximal fünf Entitäten in einem Prozessfluss abdecken, Entfernen Sie einige benutzerdefinierte Entitäten und versuchen Sie es erneut.|
> |**Name**:<br />EntitiesInViewNotAvailableOffline<br />**Hex**:<br />80071125<br />**Nummer**:<br />-2147020507|Mindestens eine Entität, auf die verwiesen wird, ist nicht für die Offlineverwendung verfügbar.|
> |**Name**:<br />EntitiesInViewNotInProfile<br />**Hex**:<br />80071124<br />**Nummer**:<br />-2147020508|Eine oder mehrere Entitäten in dieser Ansicht sind nicht Teil dieses Profils.|
> |**Name**:<br />EntitlementAlreadyInactiveState<br />**Hex**:<br />80060615<br />**Nummer**:<br />-2147088875|Sie können eine Berechtigung nicht aktivieren, wenn sie sich im aktiven Status befindet.|
> |**Name**:<br />EntitlementAlreadyInCanceledState<br />**Hex**:<br />80044208<br />**Nummer**:<br />-2147204600|Sie können keine Berechtigung mit Status „Aufgehoben” aufheben.|
> |**Name**:<br />EntitlementAlreadyInDraftState<br />**Hex**:<br />80060614<br />**Nummer**:<br />-2147088876|Sie können eine Berechtigung nicht deaktivieren, wenn sie sich im Entwurfsstatus befindet.|
> |**Name**:<br />EntitlementBlankTerms<br />**Hex**:<br />80060622<br />**Nummer**:<br />-2147088862|Gesamte Bedingungen kann nicht leer sein. Geben Sie einen Wert ein, und versuchen Sie es erneut.|
> |**Name**:<br />EntitlementChannelInvalidState<br />**Hex**:<br />80060603<br />**Nummer**:<br />-2147088893|Ein Berechtigungskanalbedingung kann nicht erstellt, geändert oder gelöscht werden, wenn die zugeordnete Berechtigung sich nicht im Entwurfsstatus befindet.|
> |**Name**:<br />EntitlementChannelWithoutEntitlementId<br />**Hex**:<br />80060612<br />**Nummer**:<br />-2147088878|Ordnen Sie den Anspruchskanal einem Anspruch oder einer Anspruchsvorlage zu.|
> |**Name**:<br />EntitlementEditDraft<br />**Hex**:<br />80060613<br />**Nummer**:<br />-2147088877|Sie können einen Anspruch nur im Entwurfsstatus bearbeiten.|
> |**Name**:<br />EntitlementInvalidRemainingTerms<br />**Hex**:<br />80060624<br />**Nummer**:<br />-2147088860|Die Anzahl der verbleibenden Bedingungen darf nicht größer als die Anzahl der gesamten Bedingungen sein.|
> |**Name**:<br />EntitlementInvalidStartEndDate<br />**Hex**:<br />80060600<br />**Nummer**:<br />-2147088896|Startdatum kann nicht nach dem Enddatum liegen.|
> |**Name**:<br />EntitlementInvalidState<br />**Hex**:<br />80060601<br />**Nummer**:<br />-2147088895|Sie können keinen Anspruch im aktiven oder wartenden Status löschen.|
> |**Name**:<br />EntitlementInvalidTerms<br />**Hex**:<br />80060604<br />**Nummer**:<br />-2147088892|Geben Sie einen höheren Wert für die gesamten Bedingungen an, damit die verbleibenden Bedingungen keinen negativen Wert aufweisen.|
> |**Name**:<br />EntitlementNotActiveInAssociationToCase<br />**Hex**:<br />80060616<br />**Nummer**:<br />-2147088874|Sie können keine Anfrage für diesen Anspruch erstellen, weil sich der Anspruch nicht im Status "Aktiv" befindet.|
> |**Name**:<br />EntitlementTemplateTotalTerms<br />**Hex**:<br />80060620<br />**Nummer**:<br />-2147088864|Falls der Zuweisungstyp der Anzahl der Anfragen entspricht, kann die Gesamtzahl der Bedingungen kein Dezimalwert sein. Geben Sie eine ganze Zahl ein.|
> |**Name**:<br />EntitlementTotalTerms<br />**Hex**:<br />80060619<br />**Nummer**:<br />-2147088871|Falls der Zuweisungstyp der Anzahl der Anfragen entspricht, kann die Gesamtzahl der Bedingungen kein Dezimalwert sein. Geben Sie eine ganze Zahl ein.|
> |**Name**:<br />EntityCannotBeChildInCustomRelationship<br />**Hex**:<br />8004432D<br />**Nummer**:<br />-2147204307|Diese Entität ist entweder als untergeordnetes Element in einer benutzerdefinierten übergeordneten Beziehung oder ist bereits ein untergeordnetes Element in einer übergeordneten Beziehung|
> |**Name**:<br />EntityCannotHaveOwnedByMeFilter<br />**Hex**:<br />80071136<br />**Nummer**:<br />-2147020490|Bei der Entität „{0}” im Profil „{1}” wurde OwnedByMe auf „true” festgelegt. Diese Eigenschaft ist keine gültige Eigenschaft für die Entität „{0}”.|
> |**Name**:<br />EntityCannotHaveOwnedByMyTeamFilter<br />**Hex**:<br />80071137<br />**Nummer**:<br />-2147020489|Bei der Entität „{0}” im Profil „{1}” wurde OwnedByMyTeam auf „true” festgelegt. Diese Eigenschaft ist keine gültige Eigenschaft für die Entität „{0}”.|
> |**Name**:<br />EntityCannotParticipateInEntityAssociation<br />**Hex**:<br />80044332<br />**Nummer**:<br />-2147204302|Diese Entität kann nur an einer Entitätszuordnung teilnehmen|
> |**Name**:<br />EntityDupCheckNotSupportedSystemWide<br />**Hex**:<br />80048431<br />**Nummer**:<br />-2147187663|Die Duplikaterkennung wird für ein oder mehrere der ausgewählten Entitäten nicht aktiviert. Der Duplikaterkennungsauftrag kann nicht gestartet werden.|
> |**Name**:<br />EntityExceedsMaxActiveBusinessProcessFlows<br />**Hex**:<br />80060420<br />**Nummer**:<br />-2147089376|Die {0} Entität übersteigt die maximal zulässige Anzahl aktiver Geschäftsprozessflüsse. Der aktuelle Grenzwert ist {1}.|
> |**Name**:<br />EntityFilterContainerMustNotBeNullFormatString<br />**Hex**:<br />80071132<br />**Nummer**:<br />-2147020494|Es wurden keine Filter für die Entität „{0}” angegeben. Wählen Sie mindestens einen Filter aus.|
> |**Name**:<br />EntityGroupNameOrEntityNamesMustBeProvided<br />**Hex**:<br />80060205<br />**Nummer**:<br />-2147089915|Fehlender Parameter. Sie müssen EntityGroupName oder EntityNames angeben.|
> |**Name**:<br />EntityHasNoStateCode<br />**Hex**:<br />80047015<br />**Nummer**:<br />-2147192811|Die angegebene Entität hat keinen statecode.|
> |**Name**:<br />EntityInstanceIsNull<br />**Hex**:<br />80060444<br />**Nummer**:<br />-2147089340|Fehler beim Erstellen oder Aktualisieren des Geschäftsprozesses: Entitätsinstanz darf nicht Null sein.|
> |**Name**:<br />EntityInstantiationFailed<br />**Hex**:<br />80040243<br />**Nummer**:<br />-2147220925|Instanziierung eines Entitätsinstanzdiensts fehlgeschlagen.|
> |**Name**:<br />EntityIsIntersect<br />**Hex**:<br />8004830F<br />**Nummer**:<br />-2147187953|Die definierte Entität ist keine überschneidende Entität.|
> |**Name**:<br />EntityIsLocked<br />**Hex**:<br />80043b1d<br />**Nummer**:<br />-2147206371|Diese Entität wird bereits blockiert.|
> |**Name**:<br />EntityIsNotBusinessProcessFlowEnabled<br />**Hex**:<br />80060421<br />**Nummer**:<br />-2147089375|Die IsBusinessProcessEnabled-Eigenschaft der {0} Entität ist ungültig.|
> |**Name**:<br />EntityIsNotCustomizable<br />**Hex**:<br />80047008<br />**Nummer**:<br />-2147192824|Die defineirte Entität kann nicht angepasst werden|
> |**Name**:<br />EntityIsNotEnabledForExternalParty<br />**Hex**:<br />8006111B<br />**Nummer**:<br />-2147086053|Sie können kein externes Parteielement erstellen oder aktualisieren, das einer Entität zugeordnet ist, die nicht für externe Parteien aktiviert ist.|
> |**Name**:<br />EntityIsNotEnabledForFollow<br />**Hex**:<br />8004F6A2<br />**Nummer**:<br />-2147158366|Diese Entität ist nicht für die Nachverfolgung aktiviert. |
> |**Name**:<br />EntityIsNotEnabledForFollowUser<br />**Hex**:<br />8004F6A1<br />**Nummer**:<br />-2147158367|Diese Entität ist nicht für die Nachverfolgung aktiviert. |
> |**Name**:<br />EntityIsUnlocked<br />**Hex**:<br />80043b1e<br />**Nummer**:<br />-2147206370|Diese Entität wird bereits entsperrt.|
> |**Name**:<br />EntityKeyNameExists<br />**Hex**:<br />80060893<br />**Nummer**:<br />-2147088237|Ein Entitätsschlüssel mit dem Namen {0} ist bereits in der Entität {1} vorhanden.|
> |**Name**:<br />EntityKeyNotDefined<br />**Hex**:<br />80060890<br />**Nummer**:<br />-2147088240|Die angegebenen Schlüsselattribute sind ein definierter Schlüssel für die {0} Entität|
> |**Name**:<br />EntityKeyWithSelectedAttributesExists<br />**Hex**:<br />80060894<br />**Nummer**:<br />-2147088236|Ein Entitätsschlüssel mit den ausgewählten Attributen ist bereits in der Entität vorhanden.|
> |**Name**:<br />EntityLimitExceeded<br />**Hex**:<br />80060200<br />**Nummer**:<br />-2147089920|MultiEntitySearch überschritt das für die Organisation festgelegte Limit für Entitäten.|
> |**Name**:<br />EntityLoopBeingCreated<br />**Hex**:<br />80040387<br />**Nummer**:<br />-2147220601|Durch das Erstellen dieser übergeordneten Zuordnung würde eine Schleife in dieser Entitätshierarchie erstellt werden.|
> |**Name**:<br />EntityLoopExists<br />**Hex**:<br />80040386<br />**Nummer**:<br />-2147220602|Schleife ist in dieser Entitätshierarchie vorhanden.|
> |**Name**:<br />EntityMetadataSyncFailed<br />**Hex**:<br />8005F238<br />**Nummer**:<br />-2147093960|Es gab Probleme mit den Serverkonfigurationen.   Es gab Probleme mit den Serverkonfigurationsänderungen.  Wir können keine Datensätze für die Anwendung laden, wenden sich an Ihren Dynamics 365 Administrator.|
> |**Name**:<br />EntityMetadataSyncFailedWithContinue<br />**Hex**:<br />8005F239<br />**Nummer**:<br />-2147093959|Es gab Probleme mit den Serverkonfigurationsänderungen.  Sie können den Vorgang fortsetzen, um der App mit der älteren Konfiguration  verwenden, führt aber möglicherweise zu Probleme beim Speichern.  Nehmen Sie Kontakt mit Ihrem  Dynamics 365-Anwendungsadministrator auf. |
> |**Name**:<br />EntityNotEnabledForAutoCreatedAccessTeams<br />**Hex**:<br />80048334<br />**Nummer**:<br />-2147187916|Diese Entität wird für automatisch erstellt für Zugriffsteams.|
> |**Name**:<br />EntityNotEnabledForCharts<br />**Hex**:<br />8004E00C<br />**Nummer**:<br />-2147164148|Diagramme sind im angegebenen Typcode der primären Entität nicht aktiviert: {0}.|
> |**Name**:<br />EntityNotEnabledForThisDevice<br />**Hex**:<br />8005F200<br />**Nummer**:<br />-2147094016|Entität wurde nicht für die Anzeige auf diesem Gerät aktiviert|
> |**Name**:<br />EntityNotRule<br />**Hex**:<br />8004E112<br />**Nummer**:<br />-2147163886|Der Sammlungsname ist keine Wiederholungsregel.|
> |**Name**:<br />EntityReferenceArgumentsNotBound<br />**Hex**:<br />80060395<br />**Nummer**:<br />-2147089515|Erforderliche Argumente vom Typ EntityReference müssen an eine Entität gebunden sein.|
> |**Name**:<br />EntityRelationshipRoleCustomLabelsMissing<br />**Hex**:<br />80044328<br />**Nummer**:<br />-2147204312|Benutzerdefinierte Beschriftungen müssen bereitgestellt werden, wenn eine Entitätsbeziehungsrolle über eine Anzeigenoption von UseCustomLabels verfügt|
> |**Name**:<br />EntityRelationshipSchemaNameNotUnique<br />**Hex**:<br />8004432B<br />**Nummer**:<br />-2147204309|Es ist bereits eine Beziehung mit dem angegebenen Namen vorhanden. Geben Sie einen eindeutigen Namen an.|
> |**Name**:<br />EntityRelationshipSchemaNameRequired<br />**Hex**:<br />8004432A<br />**Nummer**:<br />-2147204310|Bei Entitätsbeziehungen ist ein Name erforderlich|
> |**Name**:<br />EntityTypeNotSupported<br />**Hex**:<br />80100008<br />**Nummer**:<br />-2146435064|Die Entität {0} unterstützt diese Message nicht.|
> |**Name**:<br />EntityTypeSpecifiedForDashboard<br />**Hex**:<br />8004E30B<br />**Nummer**:<br />-2147163381|Ein Entitätstyp kann nicht für ein Dashboard angegeben werden.|
> |**Name**:<br />ErrorConnectingToDiscoveryService<br />**Hex**:<br />8004B066<br />**Nummer**:<br />-2147176346|Fehler beim Versuch eine Verbindung mit dem Suchdienst eines Kunden herzustellen.|
> |**Name**:<br />ErrorConnectingToOrganizationService<br />**Hex**:<br />8004B068<br />**Nummer**:<br />-2147176344|Fehler beim Versuch eine Verbindung mit dem Organisationsdienst eines Kunden herzustellen.|
> |**Name**:<br />ErrorDeleteStatementTextIsReferenced<br />**Hex**:<br />8004F203<br />**Nummer**:<br />-2147159549|Sie können den Benutzeroberflächenskript-Anweisungstext nicht löschen, da er von mindestens einem UI Skriptbestimmungen verwiesen wird.|
> |**Name**:<br />ErrorFetchingBaseUrl<br />**Hex**:<br />80044290<br />**Nummer**:<br />-2147204464|Die Basis-URL für die Organisations-ID {0} kann nicht abgerufen werden. Ausnahmedetails {1}|
> |**Name**:<br />ErrorFetchingRIProvisionStatus<br />**Hex**:<br />80044291<br />**Nummer**:<br />-2147204463|Die Bereitstellung für die Organisations-ID {0} kann momentan nicht erfolgen. Ausnahmedetails {1}|
> |**Name**:<br />ErrorGeneratingActionHub<br />**Hex**:<br />80071001<br />**Nummer**:<br />-2147020799|Ein Fehler ist aufgetreten. Bitte versuchen Sie es später erneut.|
> |**Name**:<br />ErrorGeneratingInvitation<br />**Hex**:<br />8004B013<br />**Nummer**:<br />-2147176429|Interner Fehler beim Erstellen des Einladungstokens. Versuchen Sie es später erneut.|
> |**Name**:<br />ErrorImportInvalidForPublishedScript<br />**Hex**:<br />8004F216<br />**Nummer**:<br />-2147159530|Sie können die Daten nicht mit einem veröffentlichten Benutzeroberflächenskript speichern. Aufheben der Benutzeroberflächenskripts und erneut versuchen.|
> |**Name**:<br />ErrorIncreate<br />**Hex**:<br />80040359<br />**Nummer**:<br />-2147220647|Der Microsoft Dynamics 365-Datensatz konnte nicht erstellt werden|
> |**Name**:<br />ErrorInDelete<br />**Hex**:<br />8004035a<br />**Nummer**:<br />-2147220646|Der Microsoft Dynamics 365-Datensatz konnte nicht gelöscht werden|
> |**Name**:<br />ErrorInFetchingEmailEngagementProvisioningStatus<br />**Hex**:<br />80050013<br />**Nummer**:<br />-2147155949|Fehler beim Abruf des Bereitstellungsstatus der E-Mail-Engagementfunktion.|
> |**Name**:<br />ErrorInFieldWidthIncrease<br />**Hex**:<br />80044351<br />**Nummer**:<br />-2147204271|Fehler beim Erhöhen der Feldbreite.|
> |**Name**:<br />ErrorInImportConfig<br />**Hex**:<br />80040323<br />**Nummer**:<br />-2147220701|Kann nicht mit Massenimport verarbeiten, da Import-Konfiguration Fehler enthält.|
> |**Name**:<br />ErrorInParseRow<br />**Hex**:<br />80040346<br />**Nummer**:<br />-2147220666|Die Zeile konnte nicht ausgeführt werden. Die Zeile konnte nicht analysiert werden. In der Regel geschieht dies aufgrund zu langer Zeilen.|
> |**Name**:<br />ErrorInSetState<br />**Hex**:<br />80040357<br />**Nummer**:<br />-2147220649|Der Status oder Statusgrund des Microsoft Dynamics 365-Datensatzes konnte nicht festgelegt werden|
> |**Name**:<br />ErrorInStoringImportFile<br />**Hex**:<br />80048497<br />**Nummer**:<br />-2147187561|Fehler beim Speichern der Importdatei in der Datenbank.|
> |**Name**:<br />ErrorInUnzip<br />**Hex**:<br />80048483<br />**Nummer**:<br />-2147187581|Ein Fehler beim Extrahieren der hochgeladenen komprimierten (ZIP-) oder CAB-Datei ist aufgetreten. Stellen Sie sicher, dass die Datei, die nicht durch ein Passwort geschützt wird, und versuchen Sie dann, die Datei erneut hochzuladen. Falls dieses Problem weiterhin besteht, wenden Sie sich an den Systemadministrator.|
> |**Name**:<br />ErrorInUnzipAlternate<br />**Hex**:<br />80048503<br />**Nummer**:<br />-2147187453|Fehler beim Extrahieren der hochgeladenen komprimierten (ZIP)-Datei. Versuchen Sie erneut, die Datei hochzuladen. Falls das Problem weiterhin besteht, wenden Sie sich an den Systemadministrator.|
> |**Name**:<br />ErrorInUpdate<br />**Hex**:<br />80040358<br />**Nummer**:<br />-2147220648|Der Microsoft Dynamics 365-Datensatz konnte nicht aktualisiert werden|
> |**Name**:<br />ErrorInvalidFileNameChars<br />**Hex**:<br />8004F214<br />**Nummer**:<br />-2147159532|Der Microsoft Excel-Dateiname darf keines der folgenden Zeichen enthalten: * \ : > < | ? " /. Benennen Sie die Datei mithilfe der gültigen Zeichen und versuchen Sie es erneut.|
> |**Name**:<br />ErrorInvalidUIScriptImportFile<br />**Hex**:<br />8004F211<br />**Nummer**:<br />-2147159535|Dateityp wird nicht unterstützt. Wählen Sie eine XML-Datei für Import.|
> |**Name**:<br />ErrorMigrationProcessExcessOnServer<br />**Hex**:<br />8005F034<br />**Nummer**:<br />-2147094476|Der Server ist beschäftigt andere Migrationsvorgänge zu verarbeiten. Versuchen Sie es später erneut.|
> |**Name**:<br />ErrorMimeTypeNullOrEmpty<br />**Hex**:<br />8004F215<br />**Nummer**:<br />-2147159531|Der MimeType-Eigenschaftswert der UploadFromBase64DataUIScriptRequest-Methode darf nicht null oder leer sein. Wählen Sie eine gültige Eigenschaft aus, und versuchen Sie es erneut.|
> |**Name**:<br />ErrorNoActiveRoutingRuleExists<br />**Hex**:<br />8004F874<br />**Nummer**:<br />-2147157900|Derzeit ist keine aktive Regel zum Weiterleiten dieser Anfrage vorhanden.|
> |**Name**:<br />ErrorNoQueryData<br />**Hex**:<br />8004F220<br />**Nummer**:<br />-2147159520|Ein Fehler ist aufgetreten. Entweder sind die Daten nicht vorhanden, oder Sie besitzen keine ausreichenden Rechte zur Anzeige der Daten. Wenden Sie sich für Hilfe an Ihren Systemadministrator.|
> |**Name**:<br />ErrorOnFeatureStatusChange<br />**Hex**:<br />80044289<br />**Nummer**:<br />-2147204471|Es können die Funktion für {0} Organisation ID nicht aktivieren {1}. Ausnahmedetails {2}.|
> |**Name**:<br />ErrorOnGetRecord<br />**Hex**:<br />80044286<br />**Nummer**:<br />-2147204474|Es gibt einen Fehler, einen Datensatz für Tabelle {0} abzurufen. Ausnahmedetails {1}.|
> |**Name**:<br />ErrorOnGetRIProvisionStatus<br />**Hex**:<br />80044282<br />**Nummer**:<br />-2147204478|Der Bereitstellungsstatus für Beziehungsinformationen für die Organisations-ID {0} konnte nicht abgerufen werden. Details der Ausnahme . Ausnahmedetails {1}.|
> |**Name**:<br />ErrorOnGetRITenantEndPoint<br />**Hex**:<br />80044283<br />**Nummer**:<br />-2147204477|Die Mandantenendpunktdaten der Beziehungsinformationen für die Organisations-ID {0} konnte nicht abgerufen werden. Ausnahmedetails {1}.|
> |**Name**:<br />ErrorOnQryPropertyBagCollection<br />**Hex**:<br />80044287<br />**Nummer**:<br />-2147204473|Bei der Abfrage wurden nicht alle {0} Spalten zurückgegeben.|
> |**Name**:<br />ErrorOnStartOfRIProvision<br />**Hex**:<br />80044284<br />**Nummer**:<br />-2147204476|Die Bereitstellung für die Organisations-ID {0} kann momentan nicht erfolgen. Ausnahmedetails {1}.|
> |**Name**:<br />ErrorOnTenantVerifyUpdate<br />**Hex**:<br />80044285<br />**Nummer**:<br />-2147204475|Die Mandanteninformationen für die Organisations-ID {0} können nicht überprüft oder aktualisiert werden. Ausnahmedetails {1}.|
> |**Name**:<br />ErrorPropertyBagCollectionMissedColumn<br />**Hex**:<br />80044288<br />**Nummer**:<br />-2147204472|{0} Spalte für die Tabelle {1} fehlt.|
> |**Name**:<br />ErrorReactivatingComponentInstance<br />**Hex**:<br />8004F004<br />**Nummer**:<br />-2147160060|Nach dem Rückgängigmachen der Löschung einer Beschriftung ist keine zugrunde liegende Beschriftung zum Aktivieren vorhanden.|
> |**Name**:<br />ErrorScriptCannotDeletePublishedScript<br />**Hex**:<br />8004F209<br />**Nummer**:<br />-2147159543|Sie können ein Benutzeroberflächenskript nicht löschen, das veröffentlicht ist. Sie müssen zunächst die Veröffentlichung aufheben.|
> |**Name**:<br />ErrorScriptCannotUpdatePublishedScript<br />**Hex**:<br />8004F213<br />**Nummer**:<br />-2147159533|Sie können ein Benutzeroberflächenskript nicht aktualisieren, das veröffentlicht ist. Sie müssen zunächst die Veröffentlichung aufheben.|
> |**Name**:<br />ErrorScriptFileParse<br />**Hex**:<br />8004F212<br />**Nummer**:<br />-2147159534|Fehler beim Analysieren der XML-Datei.|
> |**Name**:<br />ErrorScriptInitialStatementNotInScript<br />**Hex**:<br />8004F207<br />**Nummer**:<br />-2147159545|Die erste Bestimmung für das Skript gehört nicht dieses Skript.|
> |**Name**:<br />ErrorScriptInitialStatementNotRoot<br />**Hex**:<br />8004F208<br />**Nummer**:<br />-2147159544|Die ursprüngliche Bestimmung sollte die Stammbestimmung sein und darf keine zuvor festgelegte Bestimmung haben.|
> |**Name**:<br />ErrorScriptLanguageNotInstalled<br />**Hex**:<br />8004F206<br />**Nummer**:<br />-2147159546|Die angegebene Sprache wird in Dynamics 365 installiert werden. Überprüfen Sie mit dem Systemadministrator die Liste der "aktivierten Sprachen."|
> |**Name**:<br />ErrorScriptPublishMalformedScript<br />**Hex**:<br />8004F20B<br />**Nummer**:<br />-2147159541|Das ausgewählte Benutzeroberflächenskript kann nicht gelöscht werden. Das Benutzeroberflächenskript enthält mindestens Pfade, die nicht in einem Endskript oder einem nächsten Endskript-Aktionsknoten enden. Korrigieren Sie die Pfade und versuchen Sie, eine erneute Veröffentlichung.|
> |**Name**:<br />ErrorScriptPublishMissingInitialStatement<br />**Hex**:<br />8004F20A<br />**Nummer**:<br />-2147159542|Das ausgewählte Benutzeroberflächenskript kann nicht gelöscht werden. Geben Sie einen Wert für "Erste Anweisungsnummer" ein und versuchen Sie, erneut zu veröffentlichen.|
> |**Name**:<br />ErrorScriptSessionCannotCreateForDraftScript<br />**Hex**:<br />8004F204<br />**Nummer**:<br />-2147159548|Sie können eine Benutzeroberflächenskriptsitzung für ein Benutzeroberflächenskript nicht erstellen, das nicht veröffentlicht werden.|
> |**Name**:<br />ErrorScriptSessionCannotSetStateForDraftScript<br />**Hex**:<br />8004F20D<br />**Nummer**:<br />-2147159539|Sie können einen Status für eine UI Skriptsitzung für ein Benutzeroberflächenskript, das nicht  veröffentlicht wurde, nicht festlegen.|
> |**Name**:<br />ErrorScriptSessionCannotUpdateForDraftScript<br />**Hex**:<br />8004F205<br />**Nummer**:<br />-2147159547|Sie können eine Benutzeroberflächenskriptsitzung für ein Benutzeroberflächenskript nicht aktualisieren, das nicht veröffentlicht wurde.|
> |**Name**:<br />ErrorScriptStatementResponseTypeOnlyForPrompt<br />**Hex**:<br />8004F20E<br />**Nummer**:<br />-2147159538|Sie können den Wartesteuerelementtyp für eine Bestimmung nicht zuordnen, aus den Kriterien einer Eingabeaufforderung stammt.|
> |**Name**:<br />ErrorScriptUnpublishActiveScript<br />**Hex**:<br />8004F20C<br />**Nummer**:<br />-2147159540|Dieses Skript wird verwendet und enthält aktive Sitzungen (Statusgrund - unvollständig). Beenden Sie die aktiven Sitzungen (Ihre status-reason=cancelled.) und versuchen Sie es, um wieder die Veröffentlichung aufheben.|
> |**Name**:<br />ErrorsInEmailRouterMigrationFiles<br />**Hex**:<br />8005F032<br />**Nummer**:<br />-2147094478|Ungültige Datei(en) für E-Mail-Router-Migration|
> |**Name**:<br />ErrorsInImportFiles<br />**Hex**:<br />8004034a<br />**Nummer**:<br />-2147220662|Ungültige Datei(en) für Importvorgang.|
> |**Name**:<br />ErrorsInProfileRuleWorkflowActivation<br />**Hex**:<br />80061119<br />**Nummer**:<br />-2147086055|Sie können diese Profilregel nicht aktivieren. Sie verfügen nicht über die benötigten Berechtigungen auf die Datensatztypen, auf die über diese Profilregel verwiesen werden.|
> |**Name**:<br />ErrorsInSlaWorkflowActivation<br />**Hex**:<br />80048535<br />**Nummer**:<br />-2147187403|Sie können diese Vereinbarungen zum Servicelevel (SLA) nicht aktivieren. Sie verfügen nicht über die benötigten Berechtigungen auf die Datensatztypen, auf die über diese SLA verwiesen werden.|
> |**Name**:<br />ErrorsInWorkflowDefinition<br />**Hex**:<br />80048455<br />**Nummer**:<br />-2147187627|Der ausgewählte Workflow hat Fehler und kann nicht gelöscht werden. Öffnen Sie die Workflows entfernen Sie die Fehler, und wiederholen Sie den Vorgang.|
> |**Name**:<br />ErrorStatementDeleteOnlyForDraftScript<br />**Hex**:<br />8004F210<br />**Nummer**:<br />-2147159536|Sie können keine Benutzeroberflächenskriptsitzung für ein Benutzeroberflächenskript erstellen, das nicht im Entwurf ist.|
> |**Name**:<br />ErrorStatementOnlyForDraftScript<br />**Hex**:<br />8004F20F<br />**Nummer**:<br />-2147159537|Sie können eine Benutzeroberflächenskriptsitzung für ein Benutzeroberflächenskript nicht erstellen, das nicht im Entwurf ist.|
> |**Name**:<br />ErrorTemplate<br />**Hex**:<br />80050102<br />**Nummer**:<br />-2147155710|{0}|
> |**Name**:<br />ErrorUIScriptPromptMissing<br />**Hex**:<br />8004F221<br />**Nummer**:<br />-2147159519|Das Dialogfeld, das aktiviert ist, hat keine sofortige/eine Antwort.|
> |**Name**:<br />ErrorUpdateStatementTextIsReferenced<br />**Hex**:<br />8004F202<br />**Nummer**:<br />-2147159550|Sie können den Benutzeroberflächenskript-Anweisungstext nicht löschen, da er von mindestens einem UI Skriptbestimmungen veröffentlicht ist.|
> |**Name**:<br />ErrorUploadingReport<br />**Hex**:<br />80048298<br />**Nummer**:<br />-2147188072|Fehler beim Versuch, den Bericht zu Microsoft Dynamics 365 hinzuzufügen. Versuchen Sie erneut, den Bericht zu drucken. Falls dieses Problem weiterhin besteht, wenden Sie sich an den Systemadministrator.|
> |**Name**:<br />EventNotSupportedForBusinessRule<br />**Hex**:<br />80060001<br />**Nummer**:<br />-2147090431|Ereignis {0} wird für clientseitige Geschäftsregel nichtunterstützt.|
> |**Name**:<br />EventTypeAndControlNameAreMismatched<br />**Hex**:<br />80060003<br />**Nummer**:<br />-2147090429|Die Kombination des Ereignistyp- und Steuernamens ist unerwartet|
> |**Name**:<br />EvoStsAuthorizationServerRecordCreationFailureException<br />**Hex**:<br />80071006<br />**Nummer**:<br />-2147020794|Datenbankvorgangsfehler beim Erstellen des Autorisierungsdatensatzes für Evo STS.|
> |**Name**:<br />ExceedCustomEntityQuota<br />**Hex**:<br />8004b042<br />**Nummer**:<br />-2147176382|Die benutzerdefinierte Entitätsgrenze wurde erreicht.|
> |**Name**:<br />ExceededLimitForAllowedFacetableAttributes<br />**Hex**:<br />80060306<br />**Nummer**:<br />-2147089658|Kann Facets für Benutzersuche für für Entität {0} nicht festlegen, da die Grenze für zulässige klassifizierbare Attribute 4 ist. Entfernen Sie bitte einige Attribute, um fortzufahren.|
> |**Name**:<br />ExceededNumberOfRecordsCanFollow<br />**Hex**:<br />8004F6A0<br />**Nummer**:<br />-2147158368|Sie haben die Anzahl der Datensätze überschritten, die Sie ausführen können. Folgen Sie sich einigen Datensätze nicht mehr, um Folgendes neu zu starten.|
> |**Name**:<br />ExceededRollupFieldsPerEntityQuota<br />**Hex**:<br />80060543<br />**Nummer**:<br />-2147089085|Sie können kein Rollupfeld mit dem Namen {4} und der ID {3} für die Entität mit dem Namen {2} und der ID {1} hinzufügen. Sie haben die zulässige Höchstanzahl an {0} für diesen Datensatztyp erreicht.|
> |**Name**:<br />ExceededRollupFieldsPerOrgQuota<br />**Hex**:<br />80060542<br />**Nummer**:<br />-2147089086|Sie können kein Rollup-Feld hinzufügen. Sie haben die zulässige Höchstanzahl an {0} für diese Organisation erreicht.|
> |**Name**:<br />ExcelFileNotFound<br />**Hex**:<br />80060805<br />**Nummer**:<br />-2147088379|Die angefragte Datei wurde nicht gefunden.|
> |**Name**:<br />ExcelOnlineNotUpdated<br />**Hex**:<br />80060808<br />**Nummer**:<br />-2147088376|Excel-Online-Datei {0} wurde nicht vom Wopi-Server innerhalb des angegebenen Timeouts aktualisiert.|
> |**Name**:<br />ExchangeAutodiscoverError<br />**Hex**:<br />8004503A<br />**Nummer**:<br />-2147200966|Automatische Ermittlung konnte die Exchange Web Services URL für das angegebene Postfach nicht finden. Überprüfen Sie, ob die Postfachadresse und die Anmeldeinformationen korrekt sind und dass Autodiscover aktiviert ist und ordnungsgemäß konfiguriert wurde.|
> |**Name**:<br />ExchangeCardAttributeMissingInResponseException<br />**Hex**:<br />80071102<br />**Nummer**:<br />-2147020542|Das Attribut ist in der oData-Antwort des Austauschs nicht vorhanden.|
> |**Name**:<br />ExchangeCardInvalidResponseFormatException<br />**Hex**:<br />80071104<br />**Nummer**:<br />-2147020540|Ungültiges Antwortformat.|
> |**Name**:<br />ExchangeCardS2SSetupFailureException<br />**Hex**:<br />80071105<br />**Nummer**:<br />-2147020539|Die Server-zu-Server-Authentifizierung mit Exchange ist für die Aktionskarte nicht eingerichtet.|
> |**Name**:<br />ExchangeOptinNotEnabled<br />**Hex**:<br />80071106<br />**Nummer**:<br />-2147020538|Exchange-Option ist nicht aktiviert.|
> |**Name**:<br />ExchangeRateOfBaseCurrencyNotUpdatable<br />**Hex**:<br />80048cf5<br />**Nummer**:<br />-2147185419|Der Umrechnungskurs der Basiswährung kann nicht geändert werden.|
> |**Name**:<br />ExecuteNotOnDemandWorkflow<br />**Hex**:<br />80045046<br />**Nummer**:<br />-2147200954|Der Workflow muss als bedarfsabhängig oder untergeordnet gekennzeichnet werden.|
> |**Name**:<br />ExecuteUnpublishedWorkflow<br />**Hex**:<br />80045047<br />**Nummer**:<br />-2147200953|Der Workflow muss veröffentlicht sein.|
> |**Name**:<br />ExistingExternalReport<br />**Hex**:<br />80040488<br />**Nummer**:<br />-2147220344|Der Bericht kann nicht für die externe Verwendung veröffentlicht werden, weil kein Bericht des gleichen Namens vorhanden ist. Löschen Sie den Bericht in SQL Server Reporting Services und benennen Sie den Bericht um, und versuchen Sie es erneut.|
> |**Name**:<br />ExistingParentalRelationship<br />**Hex**:<br />80048205<br />**Nummer**:<br />-2147188219|Eine übergeordnete Beziehung ist bereits vorhanden.|
> |**Name**:<br />ExpansionRequestIsOutsideExpansionWindow<br />**Hex**:<br />8004E10C<br />**Nummer**:<br />-2147163892|Die CutOffWindow Serie wurde bereits erweitert.|
> |**Name**:<br />ExpectingAtLeastOneBusinessRuleStep<br />**Hex**:<br />80060011<br />**Nummer**:<br />-2147090415|Sie muss ein Minimum von einem Geschäftsregelschritt geben.|
> |**Name**:<br />ExpiredAuthTicket<br />**Hex**:<br />8004A101<br />**Nummer**:<br />-2147180287|Das Ticket für die Authentifizierung ist abgelaufen|
> |**Name**:<br />ExpiredEntitlementActivate<br />**Hex**:<br />80060617<br />**Nummer**:<br />-2147088873|Sie können keinen abgelaufenen Anspruch aktivieren.|
> |**Name**:<br />ExpiredKey<br />**Hex**:<br />8004A106<br />**Nummer**:<br />-2147180282|Der spezifische Schlüssel für einen Hashwert ist abgelaufen. Nur aktive Schlüssel sind gültig.  Abgelaufener Schlüssel: {0}.|
> |**Name**:<br />ExpiredOAuthToken<br />**Hex**:<br />80041d52<br />**Nummer**:<br />-2147213998|Das OAuth-Token ist abgelaufen|
> |**Name**:<br />ExpiredVersionStamp<br />**Hex**:<br />80044352<br />**Nummer**:<br />-2147204270|Der Versionsstempel, der dem Kunden zugeordnet wurde, ist abgelaufen. Führen Sie eine umfassende Synchronisierung aus.|
> |**Name**:<br />ExportDefaultAsPackagedError<br />**Hex**:<br />80048048<br />**Nummer**:<br />-2147188664|Die Standardlösung kann nicht als Paket exportiert werden.|
> |**Name**:<br />ExportManagedSolutionError<br />**Hex**:<br />80048036<br />**Nummer**:<br />-2147188682|Ein Fehler beim Exportieren einer Lösung ist aufgetreten. Verwaltete Lösungen können nicht exportiert werden.|
> |**Name**:<br />ExportMissingSolutionError<br />**Hex**:<br />80048037<br />**Nummer**:<br />-2147188681|Ein Fehler beim Exportieren einer Lösung ist aufgetreten. Die Lösung ist im System nicht vorhanden.|
> |**Name**:<br />ExportSolutionError<br />**Hex**:<br />80048035<br />**Nummer**:<br />-2147188683|Fehler beim Exportieren einer Lösung.|
> |**Name**:<br />ExportToExcelOnlineFeatureNotEnabled<br />**Hex**:<br />80060804<br />**Nummer**:<br />-2147088380|Funktion zum Exportieren nach Excel Online ist nicht aktiviert.|
> |**Name**:<br />ExportToXlsxFeatureNotEnabled<br />**Hex**:<br />800608C1<br />**Nummer**:<br />-2147088191|Die Funktion zum Exportieren nach Excel ist nicht aktiviert.|
> |**Name**:<br />ExpressionNotSupportedForEditor<br />**Hex**:<br />80060004<br />**Nummer**:<br />-2147090428|Regel enthalten einen Ausdruck, der nicht vom Notepad unterstützt wird.|
> |**Name**:<br />ExternalNameExists<br />**Hex**:<br />80046F8F<br />**Nummer**:<br />-2147192945|Eine Entität mit dem angegebenen Namen für die Datenquelle {0} ist bereits vorhanden. Bitte geben Sie einen neuen externen Namen an.|
> |**Name**:<br />ExternalSearchAttributeLimitExceeded<br />**Hex**:<br />80060300<br />**Nummer**:<br />-2147089664|Die maximal zulässige Anzahl von indexierten Feldern wurde erreicht. Bearbeiten Sie die Konfiguration der Relevanzsuche, um die Gesamtzahl der indizierten Felder {1} unter {0} zu senken.|
> |**Name**:<br />ExtraPartyInformation<br />**Hex**:<br />80040316<br />**Nummer**:<br />-2147220714|Weitere Parteiinformationen sollten für diesen Vorgang nicht bereitgestellt werden.|
> |**Name**:<br />FailedToDeserializeAsyncOperationData<br />**Hex**:<br />80044304<br />**Nummer**:<br />-2147204348|Fehler bei der Deserialisierung der asynchronen Vorgangsdaten.|
> |**Name**:<br />FailedToGetNetworkServiceName<br />**Hex**:<br />80047103<br />**Nummer**:<br />-2147192573|Der lokalisierter Namen für die Netzwerkdienstfirma konnte nicht abgerufen werden|
> |**Name**:<br />FailedToLoadAssembly<br />**Hex**:<br />8004024e<br />**Nummer**:<br />-2147220914|Fehler beim Laden der Assembly|
> |**Name**:<br />FailedToScheduleActivity<br />**Hex**:<br />80047000<br />**Nummer**:<br />-2147192832|Fehler beim Planen der Aktivität.|
> |**Name**:<br />FailToDeleteConnectorFromExternalPartner<br />**Hex**:<br />80072601<br />**Nummer**:<br />-2147015167|Der Ziel-Connector konnte nicht aus dem externen Partner gelöscht werden.|
> |**Name**:<br />FallbackCardFormDeactivation<br />**Hex**:<br />8004F664<br />**Nummer**:<br />-2147158428|Vorgang kann nicht abgeschlossen werden. Es muss mindestens ein Kartenformular aktiv sein.|
> |**Name**:<br />FallbackFormDeactivation<br />**Hex**:<br />8004F661<br />**Nummer**:<br />-2147158431|Vorgang kann nicht abgeschlossen werden. Es muss mindestens ein Hauptformular aktiv sein.|
> |**Name**:<br />FallbackFormDeletion<br />**Hex**:<br />8004F654<br />**Nummer**:<br />-2147158444|Sie können dieses Formular nicht löschen, da das Ausweichformular nur vom Typ für {0} die Entität {1} ist. Jede Entität muss mindestens über ein Ausweichformular für jeden Formulartyp verfügen.|
> |**Name**:<br />FallbackMainInteractionCentricFormDeactivation<br />**Hex**:<br />8004F666<br />**Nummer**:<br />-2147158426|Vorgang kann nicht abgeschlossen werden. Sie müssen über mindestens ein MainInteractionCentric-Formular verfügen.|
> |**Name**:<br />FallbackQuickFormDeactivation<br />**Hex**:<br />8004F665<br />**Nummer**:<br />-2147158427|Vorgang kann nicht abgeschlossen werden. Es muss mindestens eine Schnellerfassung aktiv sein.|
> |**Name**:<br />FaxNoData<br />**Hex**:<br />80043516<br />**Nummer**:<br />-2147207914|Der Fax kann nicht übermittelt werden, weil keine Daten zum Senden da sind. Geben Sie mindestens einen der folgenden Schritte an: ein Deckblatt, eine Faxanlage, eine Faxbeschreibung.|
> |**Name**:<br />FaxNoSupport<br />**Hex**:<br />80043517<br />**Nummer**:<br />-2147207913|Das Fax kann nicht gesendet werden, weil der Anlagetyp nicht zulässig ist oder dieser kein virtuelles Drucken auf einem Faxgerät zulässt.|
> |**Name**:<br />FaxSendBlocked<br />**Hex**:<br />80043510<br />**Nummer**:<br />-2147207920|Der Empfänger ist als 'Kein Fax senden' gekennzeichnet.|
> |**Name**:<br />FaxServiceNotRunning<br />**Hex**:<br />80043511<br />**Nummer**:<br />-2147207919|Der Microsoft Windows-Faxdienst wird nicht ausgeführt oder ist nicht installiert.|
> |**Name**:<br />FeatureNotEnabled<br />**Hex**:<br />80061113<br />**Nummer**:<br />-2147086061|Der Vorgang konnte nicht abgeschlossen werden, da diese Funktion für Ihre Organisation ist nicht aktiviert ist.|
> |**Name**:<br />FederatedEndpointError<br />**Hex**:<br />80044505<br />**Nummer**:<br />-2147203835|Der Endpunkt des Benutzernamens ADFS sit aktiviert, der den zu erreichenden Authentifizierungsendpunkt sperrt.|
> |**Name**:<br />FeedbackFeatureNotEnabled<br />**Hex**:<br />80061770<br />**Nummer**:<br />-2147084432|Feedbackfunktion ist nicht aktiviert.|
> |**Name**:<br />FeedbackMinMaxRequired<br />**Hex**:<br />80061772<br />**Nummer**:<br />-2147084430|Der minimale als auch der maximale Wert sind erforderlich.|
> |**Name**:<br />FeedbackMinRatingValue<br />**Hex**:<br />80061774<br />**Nummer**:<br />-2147084428|Der übermittelte Mindestbewertungswert {0} muss kleiner sein als der übermittelte Höchstbewertungswert {1}.|
> |**Name**:<br />FeedbackRatingValue<br />**Hex**:<br />80061773<br />**Nummer**:<br />-2147084429|Die Bewertung muss ein Wert zwischen {0} und {1} sein.|
> |**Name**:<br />FetchDataSetQueryTimeout<br />**Hex**:<br />8005E00E<br />**Nummer**:<br />-2147098610|Die Abrufdatasetabfrage läuft nach {0} Sekunden ab. Erhöhen Sie das Abfragetimeout, und versuchen Sie es erneut.|
> |**Name**:<br />FieldLevelSecurityNotSupported<br />**Hex**:<br />80044817<br />**Nummer**:<br />-2147203049|Sicherheit auf Feldebene wird nicht für die virtuelle Entität unterstützt.|
> |**Name**:<br />FileInUse<br />**Hex**:<br />80048837<br />**Nummer**:<br />-2147186633|Die Datei konnte nicht gelesen werden, da sie von einer anderen Anwendung verwendet wird.|
> |**Name**:<br />FileNotFound<br />**Hex**:<br />80048440<br />**Nummer**:<br />-2147187648|Die Anlagendatei wurde nicht gefunden.|
> |**Name**:<br />FilePickerErrorApplicationInSnapView<br />**Hex**:<br />8005F20D<br />**Nummer**:<br />-2147094003|Wiederholen Sie den Vorgang. Besteht das Problem weiterhin, überprüfen Sie {0} auf Lösungen, oder wenden Sie sich an den {#Brand_CRM}-Administrator in Ihrer Organisation. Schließlich können Sie {1} kontaktieren.|
> |**Name**:<br />FilePickerErrorAttachmentTypeBlocked<br />**Hex**:<br />8005F204<br />**Nummer**:<br />-2147094012|Wiederholen Sie den Vorgang. Besteht das Problem weiterhin, überprüfen Sie {0} auf Lösungen, oder wenden Sie sich an den {#Brand_CRM}-Administrator in Ihrer Organisation. Schließlich können Sie {1} kontaktieren.|
> |**Name**:<br />FilePickerErrorFileSizeBreached<br />**Hex**:<br />8005F205<br />**Nummer**:<br />-2147094011|Wiederholen Sie den Vorgang. Besteht das Problem weiterhin, überprüfen Sie {0} auf Lösungen, oder wenden Sie sich an den {#Brand_CRM}-Administrator in Ihrer Organisation. Schließlich können Sie {1} kontaktieren.|
> |**Name**:<br />FilePickerErrorFileSizeCannotBeZero<br />**Hex**:<br />8005F206<br />**Nummer**:<br />-2147094010|Wiederholen Sie den Vorgang. Besteht das Problem weiterhin, überprüfen Sie {0} auf Lösungen, oder wenden Sie sich an den {#Brand_CRM}-Administrator in Ihrer Organisation. Schließlich können Sie {1} kontaktieren.|
> |**Name**:<br />FilePickerErrorUnableToOpenFile<br />**Hex**:<br />8005F207<br />**Nummer**:<br />-2147094009|Wiederholen Sie den Vorgang. Besteht das Problem weiterhin, überprüfen Sie {0} auf Lösungen, oder wenden Sie sich an den {#Brand_CRM}-Administrator in Ihrer Organisation. Schließlich können Sie {1} kontaktieren.|
> |**Name**:<br />FileReadError<br />**Hex**:<br />80048437<br />**Nummer**:<br />-2147187657|Es gibt eine Fehlermeldung beim Lesen der Datei vom Dateisystem. Stellen Sie sicher, dass Sie über Leseberechtigung für diese Datei verfügen, und versuchen Sie dann, die Datei erneut zu migrieren.|
> |**Name**:<br />FileSizeExceeded<br />**Hex**:<br />80071026<br />**Nummer**:<br />-2147020762|Dokumente können nicht kopiert werden. Die ausgewählte Datei übersteigt die maximale Größe von 128 MB.|
> |**Name**:<br />FileStoreFeatureNotEnabled<br />**Hex**:<br />80072520<br />**Nummer**:<br />-2147015392|Funktion nicht für diese Organisation aktiviert|
> |**Name**:<br />FileTypeNotSupported<br />**Hex**:<br />800609B4<br />**Nummer**:<br />-2147087948|Der definierte Dateityp wird als Vorlage nicht unterstützt.|
> |**Name**:<br />FilteredDuetoAntiSpam<br />**Hex**:<br />80040325<br />**Nummer**:<br />-2147220699|Dieser Kunde wird aufgrund AntiSpam-Einstellungen gefiltert|
> |**Name**:<br />FilteredDuetoInactiveState<br />**Hex**:<br />8004032a<br />**Nummer**:<br />-2147220694|Dieser Kunde wird aufgrund des inaktiven Status gefiltert.|
> |**Name**:<br />FilteredDuetoMissingEmailAddress<br />**Hex**:<br />8004032e<br />**Nummer**:<br />-2147220690|Dieser Kunde wird aufgrund fehlender E-Mail-Adresse gefiltert|
> |**Name**:<br />FinalMergedEntityIsNull<br />**Hex**:<br />80060443<br />**Nummer**:<br />-2147089341|Fehler beim Erstellen oder Aktualisieren des Geschäftsprozesses: Final zusammengeführte Entität darf nicht Null sein.|
> |**Name**:<br />FirstStageIdInTraversedPathDoesNotMatchFirstStageIdInBusinessProcess<br />**Hex**:<br />80060456<br />**Nummer**:<br />-2147089322|Die ID der ersten Phase im zurückgelegten Pfad „{0}” entspricht nicht der ID der ersten Phase im Geschäftsprozess „{1}”. Wenden Sie sich an Ihren Systemadministrator.|
> |**Name**:<br />FiscalPeriodGoalMissingInfo<br />**Hex**:<br />80044903<br />**Nummer**:<br />-2147202813|Für ein Ziel vom Typ 'Buchhaltungsperiode' muss das Attribut für die Buchhaltungsperiode festgelegt sein.|
> |**Name**:<br />FiscalSettingsAlreadyUpdated<br />**Hex**:<br />80043809<br />**Nummer**:<br />-2147207159|Einstellungen für das Geschäftsjahr wurden bereits aktualisiert. Sie können nur einmal ausgeführt werden.|
> |**Name**:<br />FlowIsNotActive<br />**Hex**:<br />80060469<br />**Nummer**:<br />-2147089303|Der moderne Fluss muss aktiviert sein, um beim Flussschritt verwendet zu werden.|
> |**Name**:<br />FlowMissingRecord<br />**Hex**:<br />80050262<br />**Nummer**:<br />-2147155358|Sie müssen mindestens einen Datensatz zum Auslösen des Flows auswählen.|
> |**Name**:<br />FlowServiceClientError<br />**Hex**:<br />80060467<br />**Nummer**:<br />-2147089305|Fluss-Client-Fehler mit Statuscode „{0}” und den Details „{1}” zurückgegeben.|
> |**Name**:<br />FlowTriggerNotificationDisabled<br />**Hex**:<br />80072342<br />**Nummer**:<br />-2147015870|Fluss-Auslöserbenachrichtigungen werden für die Organisation deaktiviert.|
> |**Name**:<br />FlowTriggerNotificationFailed<br />**Hex**:<br />80072341<br />**Nummer**:<br />-2147015871|Fluss-Auslöserbenachrichtigungsanruf während der HTTP-Nachricht fehlgeschlagen. Überprüfen Sie die Ausnahme, um weitere Informationen zu erhalten.|
> |**Name**:<br />FolderDoesNotExist<br />**Hex**:<br />80060901<br />**Nummer**:<br />-2147088127|Ordner nicht vorhanden.|
> |**Name**:<br />Verboten<br />**Hex**:<br />8005F102<br />**Nummer**:<br />-2147094270|Der Server lehnt ab, die Anforderung zu erfüllen.|
> |**Name**:<br />FormDoesNotExist<br />**Hex**:<br />80048406<br />**Nummer**:<br />-2147187706|Formular nicht vorhanden.|
> |**Name**:<br />FormTransitionError<br />**Hex**:<br />80040242<br />**Nummer**:<br />-2147220926|Der Import ist fehlgeschlagen, da das System das Entitätsformular {0} nicht von unverwaltete zu verwaltetet ändern kann. Fügen Sie der verwalteten Lösung mindestens eine vollständige (Stamm)-Komponente hinzu, und versuchen Sie dann, sie erneut zu importieren.|
> |**Name**:<br />ForwardMailboxCannotAssociateWithUser<br />**Hex**:<br />8005E207<br />**Nummer**:<br />-2147098105|Ein Weiterleitungspostfach kann nicht für einen bestimmten Benutzer oder eine Warteschlange erstellt werden.  Entfernen Sie bitte das entsprechende Feld und versuchen Sie es erneut.|
> |**Name**:<br />ForwardMailboxEmailAddressRequired<br />**Hex**:<br />8005E211<br />**Nummer**:<br />-2147098095|Die E-Mail-Adresse ist bei einem Weiterleitungspostfach ein Pflichtfeld.|
> |**Name**:<br />ForwardMailboxUnexpectedIncomingDeliveryMethod<br />**Hex**:<br />8005E212<br />**Nummer**:<br />-2147098094|Die Bereitstellungsmethode für das eingehende Weiterleitungspostfach kann nur auf "Keine" oder "Router" gesetzt werden.|
> |**Name**:<br />ForwardMailboxUnexpectedOutgoingDeliveryMethod<br />**Hex**:<br />8005E213<br />**Nummer**:<br />-2147098093|Die Bereitstellungsmethode für ausgehendes Weiterleitungspostfach kann nur auf "Keine" gesetzt werden.|
> |**Name**:<br />GenericActiveDirectoryError<br />**Hex**:<br />80041d37<br />**Nummer**:<br />-2147214025|Active Directory-Fehler.|
> |**Name**:<br />GenericAzureActiveDirectoryError<br />**Hex**:<br />80041d54<br />**Nummer**:<br />-2147213996|Azure Active Directory-Fehler.|
> |**Name**:<br />GenericImportTranslationsError<br />**Hex**:<br />80060752<br />**Nummer**:<br />-2147088558|Beim Verarbeiten der Importdatei für die Übersetzungen sind Fehler aufgetreten.|
> |**Name**:<br />GenericManagedPropertyFailure<br />**Hex**:<br />8004F026<br />**Nummer**:<br />-2147160026|Die Evaluation der aktuellen Komponente (Name={0}, ID={1}) im aktuellen Vorgang ({2}) ist bei der Verwaltung der Eigenschaftenauswertung der Bedingung fehlgeschlagen: {3}|
> |**Name**:<br />GenericMetadataSyncFailed<br />**Hex**:<br />8005F246<br />**Nummer**:<br />-2147093946|Leider ist ein Fehler aufgetreten. Versuchen Sie es noch einmal oder starten Sie die App neu.|
> |**Name**:<br />GenericMetadataSyncFailedWithContinue<br />**Hex**:<br />8005F247<br />**Nummer**:<br />-2147093945|Leider ist beim Herunterladen der Serverkonfigurationsänderungen etwas schief gelaufen.  Sie können den Vorgang fortsetzen, um der App mit der älteren Konfiguration  verwenden, führt aber möglicherweise zu Probleme beim Speichern.  Falls das Problem weiterhin, wenden Sie sich an Ihren Dynamics 365-Administrator, und stellen Sie die verfügbaren Informationen zur Verfügung, wenn Sie "Weitere Informationen" auswählen.|
> |**Name**:<br />GenericTransformationInvocationError<br />**Hex**:<br />8004037b<br />**Nummer**:<br />-2147220613|Die Transformationen haben ungültige Daten zurückgegeben.|
> |**Name**:<br />GetPhotoFromGalleryFailed<br />**Hex**:<br />8005F208<br />**Nummer**:<br />-2147094008|Wiederholen Sie den Vorgang. Besteht das Problem weiterhin, überprüfen Sie {0} auf Lösungen, oder wenden Sie sich an den {#Brand_CRM}-Administrator in Ihrer Organisation. Schließlich können Sie {1} kontaktieren.|
> |**Name**:<br />GetTenantIdFailure<br />**Hex**:<br />80071109<br />**Nummer**:<br />-2147020535|Fehler beim Abrufen von TenantId.|
> |**Name**:<br />GoalAttributeAlreadyMapped<br />**Hex**:<br />80044807<br />**Nummer**:<br />-2147203065|Das metrische Detail für bestimmte Ziel-Attribut ist bereits vorhanden.|
> |**Name**:<br />GoalMissingPeriodTypeInfo<br />**Hex**:<br />80044908<br />**Nummer**:<br />-2147202808|Zielzeitraumtyp muss angegeben werden, wenn das Ziel erstellt wird. Das Feld kann nicht Null sein.|
> |**Name**:<br />GoalPercentageAchievedValueOutOfRange<br />**Hex**:<br />8004F682<br />**Nummer**:<br />-2147158398|Der Wert für den erreichten Prozentsatz wurde auf  "0" gesetzt, da sich der errechnete Wert nicht innerhalb des erlaubten Bereichs befindet.|
> |**Name**:<br />GoOfflineBCPFileSize<br />**Hex**:<br />80044224<br />**Nummer**:<br />-2147204572|Client konnte die BCP-Datei nicht herunterladen. Wenden Sie sich an den Systemadministrator, um Unterstützung zu erhalten, und gehen Sie wieder offline.|
> |**Name**:<br />GoOfflineDbSizeLimit<br />**Hex**:<br />80044222<br />**Nummer**:<br />-2147204574|Sie haben das Speicherlimit für Ihre Offline-Datenbank überschritten. Sie müssen die Datenmenge reduzieren, die Sie Offline nehmen möchten, indem Sie Ihre lokale Datengruppen ändern.|
> |**Name**:<br />GoOfflineEmptyFileForDelete<br />**Hex**:<br />80044230<br />**Nummer**:<br />-2147204560|Die Datendatei für das Löschen ist leer.|
> |**Name**:<br />GoOfflineFailedMoveData<br />**Hex**:<br />80044225<br />**Nummer**:<br />-2147204571|Client konnte die Daten nicht herunterladen. Wenden Sie sich an den Systemadministrator, um Unterstützung zu erhalten, und gehen Sie wieder offline.|
> |**Name**:<br />GoOfflineFailedPrepareMsde<br />**Hex**:<br />80044226<br />**Nummer**:<br />-2147204570|Bereiten Sie MSDE fehlgeschlagen vor. Wenden Sie sich an den Systemadministrator, um Unterstützung zu erhalten, und gehen Sie wieder offline.|
> |**Name**:<br />GoOfflineFailedReloadMetadataCache<br />**Hex**:<br />80044227<br />**Nummer**:<br />-2147204569|Das Microsoft Dynamics 365 for Outlook konnte nicht offline gehen. Versuchen Sies, in den Offlinemodus zu wechseln.|
> |**Name**:<br />GoOfflineFileWasDeleted<br />**Hex**:<br />80044229<br />**Nummer**:<br />-2147204567|Die Datendatei wurde auf dem Server gelöscht, bevor sie an den Client gesendet wurde.|
> |**Name**:<br />GoOfflineGetBCPFileException<br />**Hex**:<br />80044221<br />**Nummer**:<br />-2147204575|Die Anforderung konnte vom Dynamics 365 Server nicht verarbeitet werden. Wenden Sie sich an den Systemadministrator, um Unterstützung zu erhalten, und gehen Sie wieder offline.|
> |**Name**:<br />GoOfflineMetadataVersionsMismatch<br />**Hex**:<br />80044220<br />**Nummer**:<br />-2147204576|Client- und Servermetadatenversionen sind aufgrund einer neuen Anpassung auf dem Server unterschiedlich. Versuchen Sies, in den Offlinemodus zu wechseln.|
> |**Name**:<br />GoOfflineServerFailedGenerateBCPFile<br />**Hex**:<br />80044223<br />**Nummer**:<br />-2147204573|Der Dynamics 365 Server konnte die BCP-Datei nicht generieren. Wenden Sie sich an den Systemadministrator, um Unterstützung zu erhalten, und gehen Sie wieder offline.|
> |**Name**:<br />GraphApiS2SSetupFailureException<br />**Hex**:<br />80044260<br />**Nummer**:<br />-2147204512|Die Server-zu-Server-Authentifizierung mit Exchange ist für die Office Graph-API nicht eingerichtet.|
> |**Name**:<br />GuidNotPresent<br />**Hex**:<br />80040362<br />**Nummer**:<br />-2147220638|Der erforderliche Globally Unique Identifier (GUID) in dieser Zeile ist nicht vorhanden|
> |**Name**:<br />HeaderValueDoesNotMatchAttributeDisplayLabel<br />**Hex**:<br />80040370<br />**Nummer**:<br />-2147220624|Die Spaltenüberschrift entspricht nicht der Attributbeschriftung.|
> |**Name**:<br />HiddenPropertyValidationFailed<br />**Hex**:<br />80061000<br />**Nummer**:<br />-2147086336|Sie können keine Eigenschaftinstand für ein verborgene Eigenschaft erstellen.|
> |**Name**:<br />HiddensheetNotAvailable<br />**Hex**:<br />800609B6<br />**Nummer**:<br />-2147087946|Das verborgene Datenblatt ist nicht verfügbar.|
> |**Name**:<br />HierarchicalOperationFailed<br />**Hex**:<br />8008100F<br />**Nummer**:<br />-2146955249|Dieser Vorgang kann nicht in der Hierarchie abgeschlossen wurden. Beim Durchführen dieses Vorgangs für {0} ist ein Fehler aufgetreten. Sie können den Vorgang für dieses Produkt separat ausführen oder den Fehler beheben und dann den Vorgang erneut für die vollständige Hierarchie ausführen.|
> |**Name**:<br />HierarchyCalculateLimitReached<br />**Hex**:<br />80060547<br />**Nummer**:<br />-2147089081|Es können keine Onlineberechnungen durchgeführt werden, da das Tiefenlimit für die Masterdatensatz-Hierarchie ({0}) erreicht wurde.|
> |**Name**:<br />HipInvalidCertificate<br />**Hex**:<br />8004Ed45<br />**Nummer**:<br />-2147160763|Ungültiges Zertifikat zur Verwendung von HIP.|
> |**Name**:<br />HipNoSettingError<br />**Hex**:<br />8004Ed44<br />**Nummer**:<br />-2147160764|Keine HIP-Konfigurationseinstellung [{0}] gefunden.|
> |**Name**:<br />HonorPauseWithoutSLAKPIError<br />**Hex**:<br />80045000<br />**Nummer**:<br />-2147201024|SLA kann so festgelegt werden, das Pausen und Fortsetzen nur erfolgen, wenn SLA KPI auf Ja ausgewählt ist.|
> |**Name**:<br />HybridSSSExchangeOnlineS2SCertActsExpired<br />**Hex**:<br />80131500<br />**Nummer**:<br />-2146233088|Das verwendete Zertifikat für S2S-Authentifizierung von Dynamics 365 On-premises mit Exchange Online ist abgelaufen|
> |**Name**:<br />HybridSSSExchangeOnlineS2SCertExpired<br />**Hex**:<br />80131509<br />**Nummer**:<br />-2146233079|Das verwendete Zertifikat für S2S-Authentifizierung von Dynamics 365 On-premises mit Exchange Online ist abgelaufen|
> |**Name**:<br />ImportArticleTemplateError<br />**Hex**:<br />8004800D<br />**Nummer**:<br />-2147188723|Es gab eine Fehlermeldung beim Parsen der Artikelvorlage in Import XML|
> |**Name**:<br />ImportAttributeNameError<br />**Hex**:<br />80048062<br />**Nummer**:<br />-2147188638|Ungültiger Name für ein {0}-Attribut.  Benutzerdefinierte Attributnamen müssen mit einem gültigen Anpassungspräfix beginnen. Das Präfix für eine Lösungskomponente muss mit dem Präfix übereinstimmen, das für den Herausgeber der Lösung angegeben ist.|
> |**Name**:<br />ImportChannelPropertyGroupError<br />**Hex**:<br />800608F3<br />**Nummer**:<br />-2147088141|Fehler beim Importieren der Kanaleigenschaftsgruppe.|
> |**Name**:<br />ImportComponentDeletedIgnored<br />**Hex**:<br />8004847c<br />**Nummer**:<br />-2147187588|Die Komponente kann nicht aktualisiert werden, da sie in der Microsoft Dynamics 365-Organisation nicht vorhanden ist.|
> |**Name**:<br />ImportConfigNotSpecified<br />**Hex**:<br />80040322<br />**Nummer**:<br />-2147220702|Kann nicht mit Massenimport verarbeiten, da Import-Konfiguration nicht angegeben ist.|
> |**Name**:<br />ImportContractTemplateError<br />**Hex**:<br />8004800B<br />**Nummer**:<br />-2147188725|Es gab eine Fehlermeldung beim Parsen der Vertragsvorlage in Import XML|
> |**Name**:<br />ImportConvertRuleError<br />**Hex**:<br />8004F869<br />**Nummer**:<br />-2147157911|Fehler beim Importieren von Konvertierungsregeln.|
> |**Name**:<br />ImportCustomizationsBadZipFileError<br />**Hex**:<br />80048060<br />**Nummer**:<br />-2147188640|Die Lösungsdatei ist ungültig. Die Übersetzungsdatei ist ungültig. Im Stammverzeichnis der komprimierten Datei müssen sich folgende Dateien befinden: solution.xml, customizations.xml und [Content_Types].xml. Die Anpassungsdateien, die aus früheren Versionen von Microsoft Dynamics 365 exportiert werden, werden nicht unterstützt.|
> |**Name**:<br />ImportDashboardDeletedError<br />**Hex**:<br />8004E308<br />**Nummer**:<br />-2147163384|Ein Dashboard mit derselben ID wird im System als gelöscht gekennzeichnet. Bitte veröffentlichen Sie zuerst die Systemformularentität und importieren Sie wieder.|
> |**Name**:<br />ImportDefaultAsPackageError<br />**Hex**:<br />80048049<br />**Nummer**:<br />-2147188663|Das Paket, das für die Standardlösung angegeben wurde, versucht, sie in verwalteten Modus zu installieren. Die Standardansicht kann nicht verwaltet werden. Im XML für die Standardlösung legen Sie den verwalteten Wert wieder auf "false" fest, und versuchen Sie, die Lösung erneut zu importieren.|
> |**Name**:<br />ImportDependencySolutionError<br />**Hex**:<br />80048034<br />**Nummer**:<br />-2147188684|{0} erfordert Lösungen, die im Augenblick nicht installiert sind. Importieren Sie die folgenden Lösungen, bevor Sie dieses importieren. {1} |
> |**Name**:<br />ImportDuplicateEntity<br />**Hex**:<br />8004810c<br />**Nummer**:<br />-2147188468|Fehler beim Import, da bereits eine andere Entität mit dem gleichen Namen, "{0}", in der Zielorganisation vorhanden ist.|
> |**Name**:<br />ImportEmailTemplateError<br />**Hex**:<br />8004800C<br />**Nummer**:<br />-2147188724|Es gab eine Fehlermeldung beim Parsen der E-Mailvorlage in Import XML|
> |**Name**:<br />ImportEmailTemplateErrorMissingFile<br />**Hex**:<br />8004802B<br />**Nummer**:<br />-2147188693|E-Mail-Vorlage "{0}"-Import: Die Anlage "{1}" wurde nicht in der ZIP-Importdatei gefunden.|
> |**Name**:<br />ImportEmailTemplatePersonalError<br />**Hex**:<br />80048014<br />**Nummer**:<br />-2147188716|E-Mail-Vorlage wurde nicht importiert. Die Vorlage ist eine persönliche Vorlage auf dem Zielsystem; Import kann persönliche Vorlagen nicht überschreiben.|
> |**Name**:<br />ImportEntityCustomResourcesError<br />**Hex**:<br />80048002<br />**Nummer**:<br />-2147188734|Ungültige benutzerdefinierte Ressourcen in der Importdatei|
> |**Name**:<br />ImportEntityCustomResourcesNewStringError<br />**Hex**:<br />80048003<br />**Nummer**:<br />-2147188733|Ungültiger neue Entitätszeichenfolge in den benutzerdefinierten Ressourcen|
> |**Name**:<br />ImportEntityIconError<br />**Hex**:<br />80048001<br />**Nummer**:<br />-2147188735|Ungültiges Symbol in der Importdatei|
> |**Name**:<br />ImportEntityNameMismatchError<br />**Hex**:<br />80048008<br />**Nummer**:<br />-2147188728|Die Anzahl der Formatparametern, die in der Eingabezeichenfolge übergeben wurden, sind ungültig|
> |**Name**:<br />ImportEntitySystemUserLiveMismatchError<br />**Hex**:<br />80048025<br />**Nummer**:<br />-2147188699|Der Entität Benutzer wurde importiert, doch die angepassten Formulare für die Entität werden nicht importiert. Systemuser-Entitätsformulare von lokalen oder gehosteten Versionen von Microsoft Dynamics 365 können nicht in Microsoft Dynamics 365 Online importiert werden.|
> |**Name**:<br />ImportEntitySystemUserOnPremiseMismatchError<br />**Hex**:<br />80048024<br />**Nummer**:<br />-2147188700|Der Entität Benutzer wurde importiert, doch die angepassten Formulare für die Entität werden nicht importiert. Systemuser-Entitätsformulare von Microsoft Dynamics 365 Online können nicht in lokale oder gehostete Versionen von Microsoft Dynamics 365 importiert werden.|
> |**Name**:<br />ImportExportDeprecatedError<br />**Hex**:<br />80048045<br />**Nummer**:<br />-2147188667|Dieses Thema ist nicht mehr verfügbar. Empfehlen Sie bitte das SDK für alternative Nachrichten.|
> |**Name**:<br />ImportFieldSecurityProfileAttributesMissingError<br />**Hex**:<br />80048064<br />**Nummer**:<br />-2147188636|Einige Feldsicherheitsberechtigungen konnten nicht importiert werden, da sich die folgenden Felder nicht im System befinden: '{0}'.|
> |**Name**:<br />ImportFieldSecurityProfileIsSecuredMissingError<br />**Hex**:<br />80048063<br />**Nummer**:<br />-2147188637|Einige Feldsicherheitsberechtigungen konnten nicht importiert werden, da die folgenden Felder nicht gesichert werden können: '{0}'.|
> |**Name**:<br />ImportFieldXmlError<br />**Hex**:<br />80048006<br />**Nummer**:<br />-2147188730|Die Anzahl der Formatparametern, die in der Eingabezeichenfolge übergeben wurden, sind ungültig|
> |**Name**:<br />ImportFileFailed<br />**Hex**:<br />80050125<br />**Nummer**:<br />-2147155675|Import und Extraktion der Datei fehlgeschlagen.|
> |**Name**:<br />ImportFileSignatureInvalid<br />**Hex**:<br />80048065<br />**Nummer**:<br />-2147188635|Die Importdatei hat eine ungültige digitale Signatur.|
> |**Name**:<br />ImportFileTooLargeToUpload<br />**Hex**:<br />80040375<br />**Nummer**:<br />-2147220619|Die Importdatei ist zu groß zum Hochladen.|
> |**Name**:<br />ImportFormXmlError<br />**Hex**:<br />80048007<br />**Nummer**:<br />-2147188729|Die Anzahl der Formatparametern, die in der Eingabezeichenfolge übergeben wurden, sind ungültig|
> |**Name**:<br />ImportGenericEntitiesError<br />**Hex**:<br />80048020<br />**Nummer**:<br />-2147188704|Fehler beim Importieren von generischen Entitäten.|
> |**Name**:<br />ImportGenericError<br />**Hex**:<br />8004801E<br />**Nummer**:<br />-2147188706|Fehler beim Import. Weitere Informationen finden Sie bei den entsprechenden Fehlermeldungen.|
> |**Name**:<br />ImportHierarchyRuleDeletedError<br />**Hex**:<br />8004F9A1<br />**Nummer**:<br />-2147157599|Eine Hierarchieregel mit der gleichen ID ist im System als gelöscht markiert. Veröffentlichen Sie daher zunächst die angepasste Entität, und wiederholen Sie anschließend den Importvorgang.|
> |**Name**:<br />ImportHierarchyRuleExistingError<br />**Hex**:<br />8004F9A2<br />**Nummer**:<br />-2147157598|Kann vorhandene Hierarchieregel nicht erneut verwenden.|
> |**Name**:<br />ImportHierarchyRuleOtcMismatchError<br />**Hex**:<br />8004F9A3<br />**Nummer**:<br />-2147157597|Es gibt eine Fehlermeldung angezeigt, der Hierarchieregeln des gleichen Objekttypcodes verarbeitet. (unlösbarer Systemkonflikt)|
> |**Name**:<br />ImportInvalidFileError<br />**Hex**:<br />80048000<br />**Nummer**:<br />-2147188736|Ungültige Importdatei|
> |**Name**:<br />ImportInvalidXmlError<br />**Hex**:<br />8004802C<br />**Nummer**:<br />-2147188692|Dieses Lösungspaket kann nicht importiert werden, da es ungültiges XML enthält. Sie können versuchen, die Datei manuell zu reparieren, indem Sie die  XML-Inhalte mithilfe der Informationen in den Schemaüberprüfungsfehlern bearbeiten. Alternativ dazu können Sie Ihren Lösungsanbieter kontaktieren.|
> |**Name**:<br />ImportIsvConfigError<br />**Hex**:<br />8004800E<br />**Nummer**:<br />-2147188722|Es ist ein Fehler beim Parsen der IsvConfig beim Import aufgetreten.|
> |**Name**:<br />ImportLanguagesIgnoredError<br />**Hex**:<br />80048026<br />**Nummer**:<br />-2147188698|Die übersetzten Beschriftungen für die folgenden Sprachen konnten nicht importiert werden, da sie für diese Organisation nicht aktiviert wurden: {0}|
> |**Name**:<br />ImportMailMergeTemplateEntityMissingError<br />**Hex**:<br />80048480<br />**Nummer**:<br />-2147187584|Die Seriendruckvorlage "{0}" wurde nicht importiert, da die Entität "{1}", die dieser Vorlage zugeordnet ist, im Zielsystem nicht vorhanden ist.|
> |**Name**:<br />ImportMailMergeTemplateError<br />**Hex**:<br />80048456<br />**Nummer**:<br />-2147187626|Es gab eine Fehlermeldung beim Parsen der Seriendruckvorlage in Import XML|
> |**Name**:<br />ImportMapInUse<br />**Hex**:<br />80048465<br />**Nummer**:<br />-2147187611|Mindestens eine der ausgewählten Datenzuordnungen kann nicht gelöscht werden, da sie zurzeit in einem Datenimportvorgang verwendet wird.|
> |**Name**:<br />ImportMappingsInvalidIdSpecified<br />**Hex**:<br />80048427<br />**Nummer**:<br />-2147187673|Die XML-Datei besitzt mindestens eine ungültige ID. Die angegebene ID kann nicht als eindeutiger Bezeichner verwendet werden.|
> |**Name**:<br />ImportMappingsMissingEntityMapError<br />**Hex**:<br />80048010<br />**Nummer**:<br />-2147188720|Diese Anpassungsdatei enthält einen Verweis auf eine Entitätszuordnung, die nicht auf dem Zielsystem vorhanden ist.|
> |**Name**:<br />ImportMappingsSystemMapError<br />**Hex**:<br />8004800F<br />**Nummer**:<br />-2147188721|Import kann keine Systemattributzuordnungen erstellen|
> |**Name**:<br />ImportMissingComponent<br />**Hex**:<br />8004801F<br />**Nummer**:<br />-2147188705|Eine Stamm-Komponente {0} vom Typ {1} kann nicht hinzugefügt werden, da sie sich nicht im Zielsystem befindet.|
> |**Name**:<br />ImportMissingDependenciesError<br />**Hex**:<br />8004801D<br />**Nummer**:<br />-2147188707|Die folgende verwaltete Lösung kann nicht importier werden: {0}. Einige Abhängigkeiten fehlen.|
> |**Name**:<br />ImportMissingRootComponentEntry<br />**Hex**:<br />8004803A<br />**Nummer**:<br />-2147188678|Der Import ist fehlgeschlagen, da Komponente {0} vom Typ {1} nicht in der Stammkomponente als Lösungsdatei deklariert werden. Um dieses Problem zu beheben, importieren Sie erneut mit der XML-Datei die generiert wurde als Sie die Lösung exportieren.|
> |**Name**:<br />ImportMobileOfflineProfileError<br />**Hex**:<br />8006099F<br />**Nummer**:<br />-2147087969|Beim Importieren von Mobile Offline-Profilen ist ein Fehler aufgetreten.|
> |**Name**:<br />ImportNewPluginTypesError<br />**Hex**:<br />80048071<br />**Nummer**:<br />-2147188623|Vorhandene Plug-In-Typen wurden entfernt. Aktualisieren Sie eine größere oder kleinere Version der Plug-In-Assembly.|
> |**Name**:<br />ImportNonWellFormedFileError<br />**Hex**:<br />80048013<br />**Nummer**:<br />-2147188717|Ungültige Anpassungsdatei Dieses Dateiformat ist nicht gut geformt.|
> |**Name**:<br />ImportNotComplete<br />**Hex**:<br />80048472<br />**Nummer**:<br />-2147187598|Mindestens ein Import ist nicht in abgeschlossenem Status. Importierte Datensätze können nur aus abgeschlossenen Aufträgen gelöscht werden. Warten Sie, bis Auftrag abgeschlossen, und versuchen Sie es anschließend erneut.|
> |**Name**:<br />ImportOperationChildFailure<br />**Hex**:<br />80044334<br />**Nummer**:<br />-2147204300|Mindestens ein untergeordneter Import-Auftrag ist fehlgeschlagen.|
> |**Name**:<br />ImportOptionSetAttributeError<br />**Hex**:<br />80048039<br />**Nummer**:<br />-2147188679|Attribut "{0}" wurde nicht importiert, da es sich auf einen nicht vorhandenen globalen Optionssatz ("{1}") bezieht.|
> |**Name**:<br />ImportOptionSetsError<br />**Hex**:<br />80048030<br />**Nummer**:<br />-2147188688|Fehler beim Importieren von OptionSets.|
> |**Name**:<br />ImportOrgSettingsError<br />**Hex**:<br />80048019<br />**Nummer**:<br />-2147188711|Es ist ein Fehler beim Parsen der Organisationseinstellungen beim Import aufgetreten.|
> |**Name**:<br />ImportPluginTypesError<br />**Hex**:<br />80048012<br />**Nummer**:<br />-2147188718|Fehler beim Importieren von Plug-in-Typen.|
> |**Name**:<br />ImportRelationshipRoleMapsError<br />**Hex**:<br />8004800A<br />**Nummer**:<br />-2147188726|Die Anzahl der Formatparametern, die in der Eingabezeichenfolge übergeben wurden, sind ungültig|
> |**Name**:<br />ImportRelationshipRolesError<br />**Hex**:<br />80048009<br />**Nummer**:<br />-2147188727|Die Anzahl der Formatparametern, die in der Eingabezeichenfolge übergeben wurden, sind ungültig|
> |**Name**:<br />ImportRelationshipRolesPrivilegeError<br />**Hex**:<br />8004802F<br />**Nummer**:<br />-2147188689|{0} kann nicht importiert werden. {1} kann nicht importiert werden. Zum Importieren dieser Komponente wird diese Komponente benötigt.|
> |**Name**:<br />ImportReportsError<br />**Hex**:<br />80048032<br />**Nummer**:<br />-2147188686|Fehler beim Importieren von Berichten.|
> |**Name**:<br />ImportRestrictedSolutionError<br />**Hex**:<br />8004F007<br />**Nummer**:<br />-2147160057|Die beim Importieren angegebene Lösungs-ID unterliegt Einschränkungen und kann nicht importiert werden.|
> |**Name**:<br />ImportRibbonsError<br />**Hex**:<br />80048031<br />**Nummer**:<br />-2147188687|Fehler beim Importieren von Menübändern.|
> |**Name**:<br />ImportRoleError<br />**Hex**:<br />80048017<br />**Nummer**:<br />-2147188713|Kann Sicherheitsrolle nicht importieren. Die Rolle mit angegebener Rollen-ID kann nicht angepasst werden oder der Rollenname ist nicht eindeutig.|
> |**Name**:<br />ImportRolePermissionError<br />**Hex**:<br />80048018<br />**Nummer**:<br />-2147188712|Sie verfügen nicht über die erforderlichen Rechte zum Importieren von Sicherheitsrollen.|
> |**Name**:<br />ImportRoutingRuleError<br />**Hex**:<br />8004F867<br />**Nummer**:<br />-2147157913|Fehler beim Importieren von Routingregelsätzen.|
> |**Name**:<br />ImportSavedQueryDeletedError<br />**Hex**:<br />8004801B<br />**Nummer**:<br />-2147188709|Eine gespeicherte Anfrage mit derselben ID wird im System als gelöscht gekennzeichnet. Bitte veröffentlichen Sie zuerst die Entität und importieren Sie wieder.|
> |**Name**:<br />ImportSavedQueryExistingError<br />**Hex**:<br />80048005<br />**Nummer**:<br />-2147188731|Die Anzahl der Formatparametern, die in der Eingabezeichenfolge übergeben wurden, sind ungültig|
> |**Name**:<br />ImportSavedQueryOtcMismatchError<br />**Hex**:<br />80048004<br />**Nummer**:<br />-2147188732|Es wird eine Fehlermeldung bei der Verarbeitung gespeicherter Anfragen des gleichen Objekttypcodes angezeigt (unlösbarer Systemkonflikt)|
> |**Name**:<br />ImportSdkMessagesError<br />**Hex**:<br />80048016<br />**Nummer**:<br />-2147188714|Fehler beim Importieren von SDK-Nachrichten.|
> |**Name**:<br />ImportSiteMapError<br />**Hex**:<br />80048011<br />**Nummer**:<br />-2147188719|Fehler beim Importieren der Siteübersicht.|
> |**Name**:<br />ImportSlaError<br />**Hex**:<br />8004F868<br />**Nummer**:<br />-2147157912|Fehler beim Importieren von SLAs.|
> |**Name**:<br />ImportSolutionError<br />**Hex**:<br />80048033<br />**Nummer**:<br />-2147188685|Fehler beim Importieren einer Lösung.|
> |**Name**:<br />ImportSolutionIsvConfigWarning<br />**Hex**:<br />80048042<br />**Nummer**:<br />-2147188670|Die ISV-Konfiguration wurde überschrieben.|
> |**Name**:<br />ImportSolutionManagedError<br />**Hex**:<br />80048038<br />**Nummer**:<br />-2147188680|Die Lösung "{0}" ist in diesem System bereits als verwaltete Lösung vorhanden und kann nicht aktualisiert werden.|
> |**Name**:<br />ImportSolutionManagedToUnmanagedMismatch<br />**Hex**:<br />80048040<br />**Nummer**:<br />-2147188672|Die Lösung wurde bereits auf diesem System installiert als eine unverwaltete Lösung und das Paket, das angegeben wurden, versucht, sie in verwalteten Modus zu installieren. Import kann nur Lösungen aktualisieren, wenn die Modi übereinstimmen. Deinstallieren Sie die aktuelle  Lösung und versuchen Sie es erneut.|
> |**Name**:<br />ImportSolutionOrganizationSettingsWarning<br />**Hex**:<br />80048044<br />**Nummer**:<br />-2147188668|Die Organisationseinstellungen wurden überschrieben.|
> |**Name**:<br />ImportSolutionPackageInvalidSku<br />**Hex**:<br />8004806B<br />**Nummer**:<br />-2147188629|Das von Ihnen importierte Lösungspaket wurde mit Microsoft Dynamics 365 Online erstellt. Es kann nicht in lokale oder gehostete Versionen von Microsoft Dynamics 365 importiert werden.|
> |**Name**:<br />ImportSolutionPackageInvalidSolutionPackageVersion<br />**Hex**:<br />80048068<br />**Nummer**:<br />-2147188632|Sie können Lösungen mit einer Paketversion von {0} oder früher in diese Organisation importieren. Außerdem können keine Lösungen in diese Organisation importieren, die aus Microsoft Dynamics 365 2011 oder einer früheren Version exportiert wurden.|
> |**Name**:<br />ImportSolutionPackageMinimumVersionNeeded<br />**Hex**:<br />00000001<br />**Nummer**:<br />1|Veraltet, wird jetzt nicht entfernt, da Probleme während der Integrationen verursacht werden können.|
> |**Name**:<br />ImportSolutionPackageNeedsUpgrade<br />**Hex**:<br />80048067<br />**Nummer**:<br />-2147188633|Das Lösungspaket, das Sie importieren, wurde auf eine anderen Version von Microsoft Dynamics 365 erstellt. Das System versucht, das Import Paket zu transformieren. Paket-Version: {0} {1}, System-Version: {2} {3}.|
> |**Name**:<br />ImportSolutionPackageNotValid<br />**Hex**:<br />80048066<br />**Nummer**:<br />-2147188634|Das zu importierende Lösungspaket wurde in einer Version von Microsoft Dynamics 365 generiert, die nicht in dieses System importiert werden kann. Paket-Version: {0} {1}, System-Version: {2} {3}.|
> |**Name**:<br />ImportSolutionPackageRequiresOptInAvailable<br />**Hex**:<br />80048069<br />**Nummer**:<br />-2147188631|Einige Komponenten im Lösungspaket, die Sie importieren, benötigen ein Abonnement. Opt in verfügbar, bitte kontaktieren Sie Ihren Administrator.|
> |**Name**:<br />ImportSolutionPackageRequiresOptInNotAvailable<br />**Hex**:<br />8004806A<br />**Nummer**:<br />-2147188630|Das Lösungspaket, das Sie importieren, wurde auf eine anderen SKU-Version von Microsoft Dynamics 365 erstellt, die Abonnements unterstützt. Es kann nicht in Ihr System importiert werden.|
> |**Name**:<br />ImportSolutionSiteMapWarning<br />**Hex**:<br />80048043<br />**Nummer**:<br />-2147188669|Die Siteübersicht wurde überschrieben.|
> |**Name**:<br />ImportSolutionUnmanagedToManagedMismatch<br />**Hex**:<br />80048041<br />**Nummer**:<br />-2147188671|Die Lösung wurde bereits auf diesem System installiert als eine verwaltete Lösung und das Paket, das angegeben wurden, versucht, sie in nicht verwalteten Modus zu installieren. Import kann nur Lösungen aktualisieren, wenn die Modi übereinstimmen. Deinstallieren Sie die aktuelle  Lösung und versuchen Sie es erneut.|
> |**Name**:<br />ImportSystemSolutionError<br />**Hex**:<br />80048046<br />**Nummer**:<br />-2147188666|Systemlösung kann nicht importiert werden.|
> |**Name**:<br />ImportTemplateLanguageIgnored<br />**Hex**:<br />8004847a<br />**Nummer**:<br />-2147187590|Die Vorlage kann nicht importiert werden, da die Sprache in der Microsoft Dynamics 365-Organisation nicht aktiviert ist.|
> |**Name**:<br />ImportTemplatePersonalIgnored<br />**Hex**:<br />8004847b<br />**Nummer**:<br />-2147187589|Die Vorlage kann nicht importiert werden, da sie in der Microsoft Dynamics 365-Organisation als „persönlich” festgelegt ist.|
> |**Name**:<br />ImportTranslationMissingSolutionError<br />**Hex**:<br />80048047<br />**Nummer**:<br />-2147188665|Fehler beim Importieren der Übersetzung. Die Lösung, die der Übersetzung zugeordnet ist, ist im System nicht vorhanden.|
> |**Name**:<br />ImportTranslationsBadZipFileError<br />**Hex**:<br />80048061<br />**Nummer**:<br />-2147188639|Die Übersetzungsdatei ist ungültig. Im Stammverzeichnis der komprimierten Datei müssen sich folgende Dateien befinden: {0}, [Content_Types].xml.|
> |**Name**:<br />ImportVisualizationDeletedError<br />**Hex**:<br />8004E013<br />**Nummer**:<br />-2147164141|Eine gespeicherte Abfragevisualisierung mit ID {0} ist zu Löschung im System markiert. Bitte veröffentlichen Sie zuerst die Entität und importieren Sie wieder.|
> |**Name**:<br />ImportVisualizationExistingError<br />**Hex**:<br />8004E014<br />**Nummer**:<br />-2147164140|Eine gespeicherte Abfragevisualisierung mit ID {0} ist bereits im System vorhanden und kann nicht von einer neuen benutzerdefinierten Entität erneut verwendet werden.|
> |**Name**:<br />ImportWillExceedCustomEntityQuota<br />**Hex**:<br />8004b043<br />**Nummer**:<br />-2147176381|Dieser Importvorgang versucht {0} neu benutzerdefinierte Entitäten zu importieren. Dadurch würde die Beschränkungen der benutzerdefinierten Entität für diese Organisation zu groß sein.|
> |**Name**:<br />ImportWorkflowAttributeDependencyError<br />**Hex**:<br />80048022<br />**Nummer**:<br />-2147188702|Kann Workflowdefinition nicht importieren. Abhängigkeit vom erforderlichen Attribut fehlen.|
> |**Name**:<br />ImportWorkflowEntityDependencyError<br />**Hex**:<br />80048023<br />**Nummer**:<br />-2147188701|Kann Workflowdefinition nicht importieren. Abhängigkeit von der erforderlichen Entität fehlt.|
> |**Name**:<br />ImportWorkflowError<br />**Hex**:<br />80048021<br />**Nummer**:<br />-2147188703|Kann Workflowdefinition nicht importieren. Der Workflow mit der definierten Workflow ID kann nicht aktualisiert werden oder der Workflowname ist nicht eindeutig.|
> |**Name**:<br />ImportWorkflowNameConflictError<br />**Hex**:<br />80048027<br />**Nummer**:<br />-2147188697|Workflows {0} können nicht importiert werden, da ein Workflow mit dem gleichem Namen und die eindeutigem Bezeichner im Zielsystem noch vorhanden ist. Ändern Sie den Namen dieser Workflows, und versuchen Sie es anschließend erneut.|
> |**Name**:<br />ImportWorkflowPublishedError<br />**Hex**:<br />80048028<br />**Nummer**:<br />-2147188696|Workflows {0}{1} können nicht importiert werden, da ein Workflow mit dem gleichem Namen und die eindeutigem Bezeichner im Zielsystem noch vorhanden ist. Heben Sie die Veröffentlichung des Workflows im Zielsystem auf, bevor Sie versuchen, den Workflow erneut zu importieren.|
> |**Name**:<br />ImportWrongPublisherError<br />**Hex**:<br />8004801C<br />**Nummer**:<br />-2147188708|Die folgende verwaltete Lösung kann nicht importier werden: {0}. Der Herausgebername kann nicht geändert von {1} auf {2} geändert werden.|
> |**Name**:<br />ImportXsdValidationError<br />**Hex**:<br />8004801A<br />**Nummer**:<br />-2147188710|Ungültige Importdatei XSD-Validierung schlug mit folgendem Fehler fehl: {0}. Die Überprüfung ist fehlgeschlagen bei: '...{1} <<<<<ERROR LOCATION>>>>> {2}...'."|
> |**Name**:<br />InaccessibleSmtpServer<br />**Hex**:<br />8005E227<br />**Nummer**:<br />-2147098073|Kann den smtp-Server nicht erreichen. Stellen Sie sicher, dass der smtp-Server möglich ist.|
> |**Name**:<br />InactiveEmailServerProfile<br />**Hex**:<br />8005E228<br />**Nummer**:<br />-2147098072|Das E-Mail-Server-Profil wird deaktiviert. Kann E-Mail für deaktiviertes Profile nicht verarbeiten.|
> |**Name**:<br />InactiveMailbox<br />**Hex**:<br />8005E219<br />**Nummer**:<br />-2147098087|Das Postfach ist in einem inaktiven Status. Senden/empfangen von E-Mails ist für aktive Postfächer zugelassen.|
> |**Name**:<br />InactiveMetricSetOnGoal<br />**Hex**:<br />8004F686<br />**Nummer**:<br />-2147158394|Eine inaktive Metrik kann nicht als ein Ziel festgelegt werden.|
> |**Name**:<br />InactiveRollupQuerySetOnGoal<br />**Hex**:<br />8004F685<br />**Nummer**:<br />-2147158395|Eine inaktive Rollup-Abfrage kann nicht als ein Ziel festgelegt werden.|
> |**Name**:<br />IncidentCannotCancel<br />**Hex**:<br />8004440e<br />**Nummer**:<br />-2147204082|Der Vorfall kann nicht storniert werden, da offene Aktivitäten für diesen Vorfall vorhanden sind.|
> |**Name**:<br />IncidentContractDoesNotHaveAllotments<br />**Hex**:<br />80044403<br />**Nummer**:<br />-2147204093|Der Vertrag hat nicht genug Zuteilungen. Der Vertrag kann für diesen Fall nicht erstellt werden.|
> |**Name**:<br />IncidentInvalidAllotmentType<br />**Hex**:<br />8004440b<br />**Nummer**:<br />-2147204085|Der Zuteilungstyp für den Vertrag ist ungültig.|
> |**Name**:<br />IncidentInvalidContractLineStateForCreate<br />**Hex**:<br />8004440d<br />**Nummer**:<br />-2147204083|Die Anfrage kann nicht für diese Vertragszeile erstellt werden, da die Vertragszeile storniert wurde oder abgelaufen ist.|
> |**Name**:<br />IncidentInvalidContractStateForCreate<br />**Hex**:<br />80044400<br />**Nummer**:<br />-2147204096|DEr Fall kann für diesen Vertrag nicht erstellt werden wegen dem Vertragsstatus.|
> |**Name**:<br />IncidentIsAlreadyClosedOrCancelled<br />**Hex**:<br />80044411<br />**Nummer**:<br />-2147204079|Bereits abgeschlossen oder abgebrochen|
> |**Name**:<br />IncidentMissingActivityRegardingObject<br />**Hex**:<br />80044409<br />**Nummer**:<br />-2147204087|Die Vorfall-ID fehlt.|
> |**Name**:<br />IncidentMissingContractDetail<br />**Hex**:<br />80044401<br />**Nummer**:<br />-2147204095|Die Vertragsdetail-ID fehlt.|
> |**Name**:<br />IncidentNullSpentTimeOrBilled<br />**Hex**:<br />8004440c<br />**Nummer**:<br />-2147204084|Das Timespent im Vorfall ist Null oder IncidentResolutions-Aktivität IsBilled ist Null.|
> |**Name**:<br />IncomingDeliveryIsForwardMailbox<br />**Hex**:<br />8005E223<br />**Nummer**:<br />-2147098077|Kann E-Mails nicht vom Postfach abrufen. Die eingehende Zustellungsmethode ist das Weiterleitungspostfach.|
> |**Name**:<br />IncomingServerLocationAndSslSetToNo<br />**Hex**:<br />8005E23E<br />**Nummer**:<br />-2147098050|Für die URL, die für den Serverstandort für eingehende E-Mails angegeben ist, wird HTTPS verwendet. Aber die Nutzung von SSL für eingehende Verbindungen ist auf Nein gesetzt. Legen Sie diese Option auf "Ja " fest, und versuchen Sie es anschließend erneut.|
> |**Name**:<br />IncomingServerLocationAndSslSetToYes<br />**Hex**:<br />8005E240<br />**Nummer**:<br />-2147098048|Für die URL, die für den Serverstandort für eingehende E-Mails angegeben ist, wird HTTPS verwendet. Geben Sie einen Serverspeicherort an, der HTTPS verwendet und versuchen Sie es anschließend erneut.|
> |**Name**:<br />IncompatibleStepsEncountered<br />**Hex**:<br />8006088B<br />**Nummer**:<br />-2147088245|Sie können die EnforceReadOnlyPlugins-Einstellung nicht aktivieren, weil Plug-Ins, die Daten ändern, auf SDK-Nachrichten schreibgeschützt registriert werden. {0}|
> |**Name**:<br />IncompleteTransformationParameterMappingsFound<br />**Hex**:<br />8004037d<br />**Nummer**:<br />-2147220611|Mindestens ein erforderlicher Transformationsparameter hat nicht die Zuordnungen, die dafür definiert werden.|
> |**Name**:<br />InconsistentAttributeNameCasing<br />**Hex**:<br />8004F043<br />**Nummer**:<br />-2147159997|Inkonsistenter Groß-/Kleinschreibung des Attributnamens erkannt, erwartet: {0}, tatsächlich: {1}.|
> |**Name**:<br />InconsistentProductRelationshipState<br />**Hex**:<br />8004F996<br />**Nummer**:<br />-2147157610|Die andere Zeile für die Produktbeziehung ist nicht verfügbar.|
> |**Name**:<br />IncorrectActiveStageEntity<br />**Hex**:<br />80060462<br />**Nummer**:<br />-2147089310|Aktive Phase ist nicht in der Entität „{0}“ enthalten.|
> |**Name**:<br />IncorrectAttributeValueType<br />**Hex**:<br />80044354<br />**Nummer**:<br />-2147204268|Ungültiger Attributwerttyp für {0}. Erwartet: {1}, Gefunden: {2}|
> |**Name**:<br />IncorrectEntitySetName<br />**Hex**:<br />8006089C<br />**Nummer**:<br />-2147088228|Der festgelegte Entitätsnamen {0} muss mit einem gültigen Anpassungspräfix beginnen.|
> |**Name**:<br />IncorrectSingleFileMultipleEntityMap<br />**Hex**:<br />80048502<br />**Nummer**:<br />-2147187454|Hierbei sollte zwei oder mehr Entitäts-Zuordnungen definiert werden, wenn die EntitiesPerFile in ImportMap auf mehrere festgelegt wird|
> |**Name**:<br />IncreasingDaysWillResetMobileOfflineData<br />**Hex**:<br />80060991<br />**Nummer**:<br />-2147087983|Wenn die Anzahl der Tage erhöht wird, werden Mobile Offline-Daten zurückgesetzt, und es wird eine erneute Synchronisierung mit mobilen Geräten durchgeführt.|
> |**Name**:<br />IndexOutOfRange<br />**Hex**:<br />8005E008<br />**Nummer**:<br />-2147098616|Der Bereich {0}liegt nicht im Filterindex {1}. Die Anzahl der vorhandenen Elemente lautet {2}.|
> |**Name**:<br />IndexSizeConstraintViolated<br />**Hex**:<br />80060895<br />**Nummer**:<br />-2147088235|Indexgröße überstieg die maximale Größe von {0} Bytes. Der Schlüssel ist zu groß. Versuchen Sie, einige Spalten zu entfernen oder die Zeichenfolgen in den Zeichenfolgenspalten zu kürzen.|
> |**Name**:<br />InitializeErrorNoReadOnSource<br />**Hex**:<br />8004F800<br />**Nummer**:<br />-2147158016|Der Vorgang konnte nicht abgeschlossen werden, da Sie nicht über Lesezugriff für die Felder im {0} Datensatz verfügen.|
> |**Name**:<br />InputParameterFieldIncorrect<br />**Hex**:<br />80060378<br />**Nummer**:<br />-2147089544|Eingabeparameter „{0}” entspricht nicht dem konfigurierten Eingabeparameterfeld. Wenden Sie sich an den Systemadministrator, um die Konfigurationsmetadaten zu überprüfen, wenn der Fehler weiterhin besteht.|
> |**Name**:<br />InsertOptionValueInvalidType<br />**Hex**:<br />80044320<br />**Nummer**:<br />-2147204320|Sie können Optionswerte nur Auswahlliste und Statusattributen hinzufügen.|
> |**Name**:<br />InstanceOutsideEffectiveRange<br />**Hex**:<br />8004E115<br />**Nummer**:<br />-2147163883|Kann den Vorgang nicht ausführen. Eine Instanz liegt außerhalb des effizienten Erweiterungsbereichs der Reihe.|
> |**Name**:<br />InsufficientAccessMode<br />**Hex**:<br />80044502<br />**Nummer**:<br />-2147203838|Nutzer benötigt Schreibzugriff auf die Dynamics 365 Organisation.|
> |**Name**:<br />InsufficientAuthTicket<br />**Hex**:<br />8004A103<br />**Nummer**:<br />-2147180285|Das Ticket, das zur Authentifizierung angegeben wurde, hat die Richtlinie nicht erfüllt.|
> |**Name**:<br />InsufficientColumnsInSubQuery<br />**Hex**:<br />8004E022<br />**Nummer**:<br />-2147164126|Mindestens eine Spalte, die von der äußeren Abfrage erforderlich ist, ist von der Unterabfrage nicht verfügbar.|
> |**Name**:<br />InsufficientCreatePrivilege<br />**Hex**:<br />8006110A<br />**Nummer**:<br />-2147086070|Externe Partei verfügt nicht über ausreichende Rechte zur Erstellung eines neuen Datensatzes mit angegebenen Parametern.|
> |**Name**:<br />InsufficientPrivilegesSupportUser<br />**Hex**:<br />80048345<br />**Nummer**:<br />-2147187899|Der Supportbenutzer besitzt keine Berechtigung zum Ausführen dieses Vorgangs.|
> |**Name**:<br />InsufficientPrivilegeToQueueOwner<br />**Hex**:<br />80040520<br />**Nummer**:<br />-2147220192|Der Besitzer dieser Warteschlange verfügt nicht über ausreichende Rechte, um mit der Warteschlange zu arbeiten.|
> |**Name**:<br />InsufficientRetrievePrivilege<br />**Hex**:<br />80061109<br />**Nummer**:<br />-2147086071|Externe Partei verfügt nicht über ausreichende Rechte zum Abruf des Datensatzes.|
> |**Name**:<br />InsufficientTransformationParameters<br />**Hex**:<br />80048506<br />**Nummer**:<br />-2147187450|Unzureichende Parameter zur Ausführung der Transformationszuordnung.|
> |**Name**:<br />InsufficientUpdatePrivilege<br />**Hex**:<br />8006110B<br />**Nummer**:<br />-2147086069|Externe Partei verfügt nicht über ausreichende Rechte zum Aktualisieren des Datensatzes.|
> |**Name**:<br />IntegerValueOutOfRange<br />**Hex**:<br />8004432F<br />**Nummer**:<br />-2147204305|Ein Validierungsfehler ist aufgetreten. Ein bereitgestellten Ganzzahl liegt außerhalb des Bereichs der zulässigen Werte für dieses Attribut.|
> |**Name**:<br />IntegratedAuthenticationIsNotAllowed<br />**Hex**:<br />80044301<br />**Nummer**:<br />-2147204351|Integrierte Authentifizierung ist nicht zulässig.|
> |**Name**:<br />InvalidAbsoluteUrlFormat<br />**Hex**:<br />80048055<br />**Nummer**:<br />-2147188651|Die absolute URL enthält ungültige Zeichen. Verwenden Sie einen anderen Namen. Gültiges absolute URL kann nicht Enden mit den folgenden Servicebenchmarks Zeichenfolgen: .aspx, .ashx, .asmx, .svc|
> |**Name**:<br />InvalidAccessMaskForTeamTemplate<br />**Hex**:<br />80048335<br />**Nummer**:<br />-2147187915|Ungültige Zugriffsmaske ist als Teamvorlage angegeben.|
> |**Name**:<br />InvalidAccessModeTransition<br />**Hex**:<br />80041d66<br />**Nummer**:<br />-2147213978|Die Clientzugriffslizenz kann nicht geändert werden, da der Benutzer keine Microsoft Dynamics 365 Online-Lizenz hat. Um den Zugriffsmodus zu ändern, müssen Sie eine Lizenz für den Benutzer im Microsoft-Onlinedienstportal zuerst hinzufügen.|
> |**Name**:<br />InvalidAccessRights<br />**Hex**:<br />8004020d<br />**Nummer**:<br />-2147220979|Ungültige Zugriffsrechte.|
> |**Name**:<br />InvalidAccessRightsPassed<br />**Hex**:<br />80048347<br />**Nummer**:<br />-2147187897|Ungültige Zugriffsrechte übergeben.|
> |**Name**:<br />InvalidActivityMimeAttachmentId<br />**Hex**:<br />80050005<br />**Nummer**:<br />-2147155963|Ungültige activityMimeAttachmentId.|
> |**Name**:<br />InvalidActivityOwnershipTypeMask<br />**Hex**:<br />8004F120<br />**Nummer**:<br />-2147159776|Eine als Aktivität konfigurierte benutzerdefinierte Entität muss sich im Besitz eines Benutzers oder Teams befinden.|
> |**Name**:<br />InvalidActivityPartyAddress<br />**Hex**:<br />80043518<br />**Nummer**:<br />-2147207912|Mindestens eine Aktivitätspartei hat ungültige Adressen.|
> |**Name**:<br />InvalidActivityType<br />**Hex**:<br />80040321<br />**Nummer**:<br />-2147220703|Ein ungültiger Objekttyp wurde für das Verteilen der Aktivitäten angezeigt.|
> |**Name**:<br />InvalidActivityTypeForCampaignActivityPropagate<br />**Hex**:<br />8004030f<br />**Nummer**:<br />-2147220721|Es muss eine gültige CommunicationActivity angegeben werden|
> |**Name**:<br />InvalidActivityTypeForList<br />**Hex**:<br />80040305<br />**Nummer**:<br />-2147220731|Aktivitäten des angegebenen Listentyps können nicht erstellt werden.|
> |**Name**:<br />InvalidActivityXml<br />**Hex**:<br />80043514<br />**Nummer**:<br />-2147207916|Ungültige XML in einer Aktivitätskonfigurationsdatei.|
> |**Name**:<br />InvalidAllotmentsCalc<br />**Hex**:<br />800404ef<br />**Nummer**:<br />-2147220241|Zuteilungen: verbleibend + verwendet != Summe|
> |**Name**:<br />InvalidAllotmentsOverage<br />**Hex**:<br />8004430B<br />**Nummer**:<br />-2147204341|Zuteilungsüberschreitung ist ungültig.|
> |**Name**:<br />InvalidAllotmentsRemaining<br />**Hex**:<br />800404f2<br />**Nummer**:<br />-2147220238|Die verbleibenden Zuteilungen sind ungültig|
> |**Name**:<br />InvalidAllotmentsTotal<br />**Hex**:<br />800404f0<br />**Nummer**:<br />-2147220240|Die Gesamtanzahl der Zuteilungen ist ungültig|
> |**Name**:<br />InvalidAllotmentsUsed<br />**Hex**:<br />800404f1<br />**Nummer**:<br />-2147220239|Die verwendeten Zuteilungen sind ungültig|
> |**Name**:<br />InvalidAmountFreeResourceLimit<br />**Hex**:<br />8004B060<br />**Nummer**:<br />-2147176352|Der Ressourcentyp {0} kann keine, freien Betrag ohne Wert von {1} haben.|
> |**Name**:<br />InvalidAmountProvided<br />**Hex**:<br />8004B02D<br />**Nummer**:<br />-2147176403|Die Servicekomponente {0} kann keinen {1} von Ressourcentyp {2} bereitstellen.|
> |**Name**:<br />InvalidAppModuleClientType<br />**Hex**:<br />80050126<br />**Nummer**:<br />-2147155674|Der Clienttypwert, der weitergegeben wurde, ist falsch und liegt nicht im gültigen Bereich.|
> |**Name**:<br />InvalidAppModuleComponent<br />**Hex**:<br />80050113<br />**Nummer**:<br />-2147155693|Die ID {0} ist nicht vorhanden oder nicht für den Komponententyp"{1}gültig.|
> |**Name**:<br />InvalidAppModuleComponentType<br />**Hex**:<br />80050112<br />**Nummer**:<br />-2147155694|Eine App kann nicht den Komponententyp "{0}" verweisen.|
> |**Name**:<br />InvalidAppModuleEventHandlers<br />**Hex**:<br />8005012F<br />**Nummer**:<br />-2147155665|Die Ereignishandler, die für die App bereitgestellt werde, sind ungültig.|
> |**Name**:<br />InvalidAppModuleId<br />**Hex**:<br />80050116<br />**Nummer**:<br />-2147155690|Die App ID ist ungültig, oder Sie besitzen keine Berechtigung der App.|
> |**Name**:<br />InvalidAppModuleSiteMap<br />**Hex**:<br />80050110<br />**Nummer**:<br />-2147155696|Die angepasste Siteübersicht für dieses App-Modul konnte aufgrund einer fehlerhaften Konfiguration nicht verwendet werden. Reparieren Sie die angepasste Siteübersicht, und wiederholen Sie den Importvorgang, um das Problem zu beheben.|
> |**Name**:<br />InvalidAppModuleSiteMapXml<br />**Hex**:<br />80050109<br />**Nummer**:<br />-2147155703|Die App-Modul-SiteMap ist ungültig.|
> |**Name**:<br />InvalidAppModuleUniqueName<br />**Hex**:<br />8005011E<br />**Nummer**:<br />-2147155682|Der eindeutige Name überschreitet die maximale Länge von 40 Zeichen oder enthält ungültige Zeichen. Nur Buchstaben und Zahlen sind zulässig.|
> |**Name**:<br />InvalidAppModuleUrl<br />**Hex**:<br />8005011A<br />**Nummer**:<br />-2147155686|Die App-URL ist nicht eindeutig, oder das Format ist ungültig.|
> |**Name**:<br />InvalidAppointmentInstance<br />**Hex**:<br />8004E104<br />**Nummer**:<br />-2147163900|Ungültige Terminentitätsinstanz.|
> |**Name**:<br />InvalidApproveFromDraftArticle<br />**Hex**:<br />80048dfd<br />**Nummer**:<br />-2147185155|Sie versuchen, einen Artikel zu genehmigen, der den Status "Entwurf" hat. Sie können einen Artikel mit dem Status nicht genehmigt nur genehmigen.|
> |**Name**:<br />InvalidApproveFromPublishedArticle<br />**Hex**:<br />80048dfb<br />**Nummer**:<br />-2147185157|Sie versuchen, einen Artikel zu genehmigen, der den Status "veröffentlicht" hat. Sie können einen Artikel mit dem Status nicht genehmigt nur genehmigen.|
> |**Name**:<br />InvalidArgument<br />**Hex**:<br />80040203<br />**Nummer**:<br />-2147220989|Ungültiges Argument|
> |**Name**:<br />InvalidArticleState<br />**Hex**:<br />800404fb<br />**Nummer**:<br />-2147220229|Der Artikelstatus ist nicht definiert|
> |**Name**:<br />InvalidArticleStateTransition<br />**Hex**:<br />800404fc<br />**Nummer**:<br />-2147220228|Der Artikelstatusübergang ist aufgrund des aktuellen Artikelstatus ungültig.|
> |**Name**:<br />InvalidArticleTemplateState<br />**Hex**:<br />800404fd<br />**Nummer**:<br />-2147220227|Der Artikelvorlagestatus ist nicht definiert|
> |**Name**:<br />InvalidAssemblyProcessorArchitecture<br />**Hex**:<br />8004417E<br />**Nummer**:<br />-2147204738|Das gegebene Plugin-Assembly wurde für nicht unterstützte Zielplattform erstellt und kann nicht geladen werden.|
> |**Name**:<br />InvalidAssemblySourceType<br />**Hex**:<br />8004417D<br />**Nummer**:<br />-2147204739|Der bestimmte Assemblyquelltyp wird für isolierte Plug-In-Assemblys unterstützt.|
> |**Name**:<br />InvalidAssigneeId<br />**Hex**:<br />80040210<br />**Nummer**:<br />-2147220976|Ungültige Zugewiesenen-ID.|
> |**Name**:<br />InvalidAssociatedSavedQuery<br />**Hex**:<br />800609AE<br />**Nummer**:<br />-2147087954|Die ausgewählte gespeicherte Abfrage gehört nicht zur zugeordneten Entität des Mobile Offline-Profilelements.|
> |**Name**:<br />InvalidAttachmentsFolder<br />**Hex**:<br />80048490<br />**Nummer**:<br />-2147187568|Die komprimierte ZIP- oder CAB-Datei kann nicht hochgeladen werden, da der Ordner "Anlagen" mindestens einen Unterordner enthält. Entfernen Sie die Unterordner und versuchen Sie es erneut.|
> |**Name**:<br />InvalidAttribute<br />**Hex**:<br />8005E009<br />**Nummer**:<br />-2147098615|Attribut {0} kann für Entität {1} gefunden werden.|
> |**Name**:<br />InvalidAttributeDataType<br />**Hex**:<br />80044815<br />**Nummer**:<br />-2147203051|Attributdatentyp: {0} ist für diese Entität ungültig.|
> |**Name**:<br />InvalidAttributeFieldType<br />**Hex**:<br />80044816<br />**Nummer**:<br />-2147203050|Attributfeldtyp: {0} ist für diese virtuelle Entität ungültig.|
> |**Name**:<br />InvalidAttributeFound<br />**Hex**:<br />8004E303<br />**Nummer**:<br />-2147163389|Ein Dashboard-Formular-XML kann kein Attribut enthalten: {0}.|
> |**Name**:<br />InvalidAttributeInXaml<br />**Hex**:<br />80060412<br />**Nummer**:<br />-2147089390|Attribut - {0} in XAML ist ungültig|
> |**Name**:<br />InvalidAttributeMap<br />**Hex**:<br />80046203<br />**Nummer**:<br />-2147196413|InvalidAttributeMap-Fehler aufgetreten|
> |**Name**:<br />InvalidAttributeMapping<br />**Hex**:<br />80048438<br />**Nummer**:<br />-2147187656|Mindestens eine Attributzuordnung ist ungültig.|
> |**Name**:<br />InvalidAttributeQuery<br />**Hex**:<br />80072527<br />**Nummer**:<br />-2147015385|Attribute müssen Teil einer der angeforderten EntityMetadata-Eigenschaften sein, wenn AttributeQuery angegeben ist. Erwartete Eigenschaft = {0} in der angeforderten Entitätseigenschaftsliste.|
> |**Name**:<br />InvalidAuth<br />**Hex**:<br />80048516<br />**Nummer**:<br />-2147187434|Organisations-Authentifizierung entspricht nicht der aktuellen Suchdienst-Rolle.|
> |**Name**:<br />InvalidAuthTicket<br />**Hex**:<br />8004A100<br />**Nummer**:<br />-2147180288|Das Ticket, das zur Authentifizierung angegeben wurde, hat die Überprüfung nicht erfüllt.|
> |**Name**:<br />InvalidBaseAttributeError<br />**Hex**:<br />80044242<br />**Nummer**:<br />-2147204542|Ungültiges Basisattribut.|
> |**Name**:<br />InvalidBaseUnit<br />**Hex**:<br />80043b0b<br />**Nummer**:<br />-2147206389|Die Basiseinheit gehört nicht zum Zeitplan.|
> |**Name**:<br />InvalidBehavior<br />**Hex**:<br />800608A1<br />**Nummer**:<br />-2147088223|Der Wert "Verhalten" dieses Attributs kann nicht geändert werden.|
> |**Name**:<br />InvalidBehaviorSelection<br />**Hex**:<br />800608A0<br />**Nummer**:<br />-2147088224|Sie können das Verhalten dieses Felds "Datum und Uhrzeit" nur in "Nur Datum" ändern.|
> |**Name**:<br />InvalidBrowserToConfigureOrganization<br />**Hex**:<br />8004D255<br />**Nummer**:<br />-2147167659|Browser für Organisationskonfiguration nicht kompatibel|
> |**Name**:<br />InvalidBusinessProcess<br />**Hex**:<br />80060389<br />**Nummer**:<br />-2147089527|Ungültiger Geschäftsprozess.|
> |**Name**:<br />InvalidCaller<br />**Hex**:<br />80040257<br />**Nummer**:<br />-2147220905|Kann ExecutionContext nicht zum Systembenutzer wechseln, ohne zuerst den Anrufer festzulegen.|
> |**Name**:<br />InvalidCascadeLinkType<br />**Hex**:<br />80048204<br />**Nummer**:<br />-2147188220|Der Kaskadenlinktyp ist für die Kaskadenaktion ungültig.|
> |**Name**:<br />InvalidCategory<br />**Hex**:<br />8004E009<br />**Nummer**:<br />-2147164151|Kategorie ist ungültig. Keine der Maße in der Kategorie haben entweder die gleiche primäre Gruppierung oder sind eine Mischung aus Aggregats- und nicht Aggregatsdaten.|
> |**Name**:<br />InvalidCertificate<br />**Hex**:<br />8005E23A<br />**Nummer**:<br />-2147098054|Das Zertifikat ist ungültig.|
> |**Name**:<br />InvalidChangeProcess<br />**Hex**:<br />80092002<br />**Nummer**:<br />-2146885630|Ungültige Änderungsprozessstatusanfrage. Aktueller Vorgangsstatus ist {0}. Dies kann nicht zu {1} übergehen.|
> |**Name**:<br />InvalidChannelForCampaignActivityPropagate<br />**Hex**:<br />80040310<br />**Nummer**:<br />-2147220720|Aktivitäten für Kampagnenaktivitäten des angegebenen Kanaltyps können nicht verteilt werden.|
> |**Name**:<br />InvalidChannelOrigin<br />**Hex**:<br />80060602<br />**Nummer**:<br />-2147088894|Eine Berechtigungskanalbedingung mit demselben Kanal ist bereits vorhanden. Geben Sie einen anderen Kanal an und versuchen Sie es erneut.|
> |**Name**:<br />InvalidCharactersInField<br />**Hex**:<br />80040278<br />**Nummer**:<br />-2147220872|Das Feld {0} enthält mindestens ein ungültiges Zeichen.|
> |**Name**:<br />InvalidClassIdInReferencePanelSection<br />**Hex**:<br />80061503<br />**Nummer**:<br />-2147085053|Ein Abschnitt im Bereich "Verweise" kann nur über Webressourcen-Steuerelemente vom Typ "Unterraster", "Schnellansichtsformular", "Suche in der Wissensdatenbank", "I-Frame" und "HTML". Steuerelement mit ungültiger classid {0} gefunden.|
> |**Name**:<br />InvalidCollectionName<br />**Hex**:<br />8006088E<br />**Nummer**:<br />-2147088242|Eine Entität mit diesem Auflistungsnamen ist bereits vorhanden. Geben Sie einen eindeutigen Namen an.|
> |**Name**:<br />InvalidColumnMapping<br />**Hex**:<br />80040377<br />**Nummer**:<br />-2147220617|ColumnMapping ist ungültig. Überprüfen Sie, ob das Zielattribut vorhanden ist.|
> |**Name**:<br />InvalidColumnNumber<br />**Hex**:<br />80040336<br />**Nummer**:<br />-2147220682|Die in der Datenzuordnung angegebene Spaltennummer ist nicht vorhanden.|
> |**Name**:<br />InvalidCommand<br />**Hex**:<br />8005E100<br />**Nummer**:<br />-2147098368|Ungültiger Befehl.|
> |**Name**:<br />InvalidComplexControlId<br />**Hex**:<br />8005E103<br />**Nummer**:<br />-2147098365|Eine komplexe Steuernummer-ID ist ungültig.|
> |**Name**:<br />InvalidConnectionString<br />**Hex**:<br />8004023f<br />**Nummer**:<br />-2147220929|Die Verbindungszeichenfolge wurde nicht gefunden oder ist ungültig.|
> |**Name**:<br />InvalidContractDetailId<br />**Hex**:<br />800404f6<br />**Nummer**:<br />-2147220234|Die Vertragsdetail-ID ist ungültig|
> |**Name**:<br />InvalidControlClass<br />**Hex**:<br />8004E307<br />**Nummer**:<br />-2147163385|Das Formular XML Dashboard darf keine Steuerelemente mit Klassen-ID {0} enthalten.|
> |**Name**:<br />InvalidConversionRule<br />**Hex**:<br />800608F6<br />**Nummer**:<br />-2147088138|Die ConversionRule, die {0} angibt, ist ungültig. Geben Sie ein gültiger ConversionRule an.|
> |**Name**:<br />InvalidCreateOnProtectedComponent<br />**Hex**:<br />8004F011<br />**Nummer**:<br />-2147160047|Das Objekt kann nicht {0}{1} erstellt werden. Erstellung kann ausgeführt werden, falls {0} verwaltet wird.|
> |**Name**:<br />InvalidCredentialTypeForNonExchangeIncomingConnection<br />**Hex**:<br />8005E214<br />**Nummer**:<br />-2147098092|Bei einem POP3-E-Mail-Servertyp können Sie nur mithilfe der Anmeldeinformationen eine Verbindung herstellen, die von einem Benutzer oder einer Warteschlange angegeben werden.|
> |**Name**:<br />InvalidCrmDateTime<br />**Hex**:<br />8004E103<br />**Nummer**:<br />-2147163901|Ungültige CrmDateTime.|
> |**Name**:<br />InvalidCrossEntityOperation<br />**Hex**:<br />80092004<br />**Nummer**:<br />-2146885628|Ungültiger entitätsübergreifender Phasenübergang. Zielentität muss angegeben werden.|
> |**Name**:<br />InvalidCrossEntityTargetOperation<br />**Hex**:<br />80092005<br />**Nummer**:<br />-2146885627|Ungültiger entitätsübergreifender Phasenübergang. Angegebenes Ziel mus übereinstimmen {0}.|
> |**Name**:<br />InvalidCurrency<br />**Hex**:<br />80048cfc<br />**Nummer**:<br />-2147185412|Die Währung ist ungültig.|
> |**Name**:<br />InvalidCustomActivityType<br />**Hex**:<br />8004F125<br />**Nummer**:<br />-2147159771|Eine als Aktivität definierte benutzerdefinierte Entität muss vom Kommunikationsaktivitätstyp sein.|
> |**Name**:<br />InvalidCustomDataDownloadFilters<br />**Hex**:<br />80060996<br />**Nummer**:<br />-2147087978|Sie können keine benutzerdefinierten Downloadfilter festlegen, da "Datensatzverteilungskriterien" nicht auf "Andere Datenfilter" festgelegt ist.|
> |**Name**:<br />InvalidCustomer<br />**Hex**:<br />8004022d<br />**Nummer**:<br />-2147220947|Der Kunde ist ungültig.|
> |**Name**:<br />InvalidCustomReportingWizardXml<br />**Hex**:<br />80040491<br />**Nummer**:<br />-2147220335|Ungültiger Assistent-XML|
> |**Name**:<br />InvalidDataDescription<br />**Hex**:<br />8004E000<br />**Nummer**:<br />-2147164160|Die Datenenbeschreibung für die Visualisierung ist ungültig.|
> |**Name**:<br />InvalidDataDownloadFilterBusinessUnit<br />**Hex**:<br />8005F222<br />**Nummer**:<br />-2147093982|Bei einer Entität im Besitz des Unternehmensinhabers können Sie nur die folgenden Datenendownloadfilter verwenden: "Alle Datensätze" oder "Nur verknüpfte Daten herunterladen".|
> |**Name**:<br />InvalidDataDownloadFilterOrganization<br />**Hex**:<br />8005F223<br />**Nummer**:<br />-2147093981|Bei einer Entität im Besitz der Organisation können Sie nur die folgenden Datenendownloadfilter verwenden: "Alle Datensätze" oder "Nur verknüpfte Daten herunterladen".|
> |**Name**:<br />InvalidDataFiltersForBUOwnedEntities<br />**Hex**:<br />80060994<br />**Nummer**:<br />-2147087980|Sie können "Datensätze in meinem Besitz" oder "Datensätze im Besitz meines Teams" nicht für Entitäten im Besitz von Unternehmenseinheiten festlegen.|
> |**Name**:<br />InvalidDataFiltersForOrgOwnedEntities<br />**Hex**:<br />80060995<br />**Nummer**:<br />-2147087979|Sie können den Filter "Andere Daten" nicht für Entitäten im Besitz der Organisation festlegen.|
> |**Name**:<br />InvalidDataFiltersForUnownedEntities<br />**Hex**:<br />80060993<br />**Nummer**:<br />-2147087981|Sie können die Filter "Alle Datensätze" oder "Andere Daten" nicht für Entitäten festlegen, die nicht in Ihrem Besitz sind.|
> |**Name**:<br />InvalidDataFormat<br />**Hex**:<br />80040356<br />**Nummer**:<br />-2147220650|Die Quelldaten besitzen nicht das erforderliche Format.|
> |**Name**:<br />InvalidDataSourceEndPoint<br />**Hex**:<br />80044826<br />**Nummer**:<br />-2147203034|Ungültige URI: Ein vollqualifizierter URI ohne Abfragezeichenfolge muss angegeben werden.|
> |**Name**:<br />InvalidDataXml<br />**Hex**:<br />8005E101<br />**Nummer**:<br />-2147098367|Ungültige Daten-XML.|
> |**Name**:<br />InvalidDateAttribute<br />**Hex**:<br />80044805<br />**Nummer**:<br />-2147203067|Das angegebene Datumsattribut ist kein Attribut der Quellentität.|
> |**Name**:<br />InvalidDateTime<br />**Hex**:<br />80040239<br />**Nummer**:<br />-2147220935|Das Datum/Uhrzeit-Format ist nicht gültig, oder der Wert liegt außerhalb des unterstützten Bereichs.|
> |**Name**:<br />InvalidDateTimeFormat<br />**Hex**:<br />800608A2<br />**Nummer**:<br />-2147088222|Sie können den Formatwert dieses Attributs nicht in "Datum und Uhrzeit" ändern, wenn das Verhalten "Nur Datum" ist.|
> |**Name**:<br />InvalidDaysInFebruary<br />**Hex**:<br />8004E124<br />**Nummer**:<br />-2147163868|29\. Februar kann nur auftreten, wenn Musterstartdatum in ein Schaltjahr fällt.|
> |**Name**:<br />InvalidDeactivateFormType<br />**Hex**:<br />8004F660<br />**Nummer**:<br />-2147158432|Sie können keine {0} Formulare deaktivieren. Nur Hauptformulare können "Inaktiv" sein.|
> |**Name**:<br />InvalidDeleteModification<br />**Hex**:<br />80048203<br />**Nummer**:<br />-2147188221|Eine kaskadierende Löschaktion einer Systembeziehung kann nicht geändert werden.|
> |**Name**:<br />InvalidDeleteOnProtectedComponent<br />**Hex**:<br />8004F013<br />**Nummer**:<br />-2147160045|Sie können {0}{1} nicht löschen. Löschung kann ausgeführt werden, falls {0} verwaltet wird.|
> |**Name**:<br />InvalidDeleteProcess<br />**Hex**:<br />80060691<br />**Nummer**:<br />-2147088751|Dieser Vorgang kann nicht gelöscht werden, weil es ein vom System generierter Vorgang ist.|
> |**Name**:<br />InvalidDependency<br />**Hex**:<br />8004F036<br />**Nummer**:<br />-2147160010|Die {2}Komponente {1} (Id={0}) ist nicht vorhanden.  Fehler beim Versuch dies {3} (ID={4}) als Abhängigkeit zuzuordnen. Fehlender Abhängigkeitsuchtyp = {5}.|
> |**Name**:<br />InvalidDependencyComponent<br />**Hex**:<br />8004F040<br />**Nummer**:<br />-2147160000|Die erforderlichen Komponente {1} (ID = {0}) die definiert wurde für die {2} kann nicht im System gefunden werden.|
> |**Name**:<br />InvalidDependencyEntity<br />**Hex**:<br />8004F041<br />**Nummer**:<br />-2147159999|Die erforderlichen Komponente {1} (Name = {0}) die definiert wurde für die {2} kann nicht im System gefunden werden.|
> |**Name**:<br />InvalidDependencyFetchXml<br />**Hex**:<br />8004F037<br />**Nummer**:<br />-2147160009|FetchXML ({2}) ist ungültig.  Fehler beim Berechnen von Abhängigkeiten für {1} (ID={0}).|
> |**Name**:<br />InvalidDeviceToConfigureOrganization<br />**Hex**:<br />8004D254<br />**Nummer**:<br />-2147167660|Mobiles Gerät kann in konfigurierter Organisation nicht verwendet werden|
> |**Name**:<br />InvalidDisplayName<br />**Hex**:<br />8004700c<br />**Nummer**:<br />-2147192820|Der angegebene Anzeigename ist nicht gültig|
> |**Name**:<br />InvalidDocumentTemplate<br />**Hex**:<br />800608CB<br />**Nummer**:<br />-2147088181|Ungültige Dokumentvorlage.|
> |**Name**:<br />InvalidDomainName<br />**Hex**:<br />80048015<br />**Nummer**:<br />-2147188715|Die Anmeldung für die Domän für den Benutzer ist ungültig. Wählen Sie einen andere Domän-Anmeldung und versuchen Sie es erneut.|
> |**Name**:<br />InvalidDundasPresentationDescription<br />**Hex**:<br />8004E016<br />**Nummer**:<br />-2147164138|Die Präsentationsbeschreibung ist für dundas Diagramm ungültig.|
> |**Name**:<br />InvalidElementFound<br />**Hex**:<br />8004E300<br />**Nummer**:<br />-2147163392|Ein Dashboard-Formular-XML kann kein Element enthalten: {0}.|
> |**Name**:<br />InvalidEmail<br />**Hex**:<br />8004B016<br />**Nummer**:<br />-2147176426|E-Mail, die aus der Vorlage generiert wird, ist ungültig|
> |**Name**:<br />InvalidEmailAddressFormat<br />**Hex**:<br />80044192<br />**Nummer**:<br />-2147204718|Ungültige E-Mail-Adresse. Weitere Informationen erhalten Sie vom zuständigen Systemadministrator.|
> |**Name**:<br />InvalidEmailAddressInMailbox<br />**Hex**:<br />8005E221<br />**Nummer**:<br />-2147098079|Die E-Mail-Adresse des Postfachs ist nicht korrekt. Geben Sie in der entsprechenden E-Mail-Adresse den Prozesse-mails ein.|
> |**Name**:<br />InvalidEmailServerLocation<br />**Hex**:<br />8005E218<br />**Nummer**:<br />-2147098088|Der Serverspeicherort ist entweder nicht vorhanden oder ungültig. Korrigieren Sie den Serverspeicherort.|
> |**Name**:<br />InvalidEmailTemplate<br />**Hex**:<br />80040313<br />**Nummer**:<br />-2147220717|Es muss eine gültige Vorlagen-ID angegeben werden|
> |**Name**:<br />InvalidEntitlementActivate<br />**Hex**:<br />80060606<br />**Nummer**:<br />-2147088890|Sie können keinen abgelaufenen, wartenden oder abgebrochenen Anspruch aktivieren.|
> |**Name**:<br />InvalidEntitlementAssociationToCase<br />**Hex**:<br />80060609<br />**Nummer**:<br />-2147088887|Sie können keine Anfrage für diesen Anspruch erstellen, da keine verfügbaren Bedingungen vorhanden sind.|
> |**Name**:<br />InvalidEntitlementCancel<br />**Hex**:<br />80060607<br />**Nummer**:<br />-2147088889|Sie können keine Berechtigung im Entwurfsstatus oder abgelaufenen Status aufheben.|
> |**Name**:<br />InvalidEntitlementChannelTerms<br />**Hex**:<br />80060605<br />**Nummer**:<br />-2147088891|Die gesamten Bedingungen für einen speziellen Anfragenursprung für einen Berechtigungskanal können nicht mehr als die gesamten Bedingungen der entsprechenden Berechtigung sein.|
> |**Name**:<br />InvalidEntitlementContacts<br />**Hex**:<br />80044207<br />**Nummer**:<br />-2147204601|Der angegebene Kontakt ist dem ausgewählten Kunden nicht zugeordnet.|
> |**Name**:<br />InvalidEntitlementDeactivate<br />**Hex**:<br />80060608<br />**Nummer**:<br />-2147088888|Sie können nur aktive oder wartende Ansprüche deaktivieren.|
> |**Name**:<br />InvalidEntitlementExpire<br />**Hex**:<br />80060618<br />**Nummer**:<br />-2147088872|Sie können keine Berechtigung dem abgelaufenen Status zuweisen. Aktive Berechtigungen laufen automatisch ab, wenn das Enddatum überschritten wird.|
> |**Name**:<br />InvalidEntitlementForSelectedCustomerOrProduct<br />**Hex**:<br />8004F866<br />**Nummer**:<br />-2147157914|Wählen Sie eine aktive Berechtigung aus, die zum angegebenen Kunden, Kontakt oder Produkt gehört, und wiederholen Sie anschließend den Vorgang.|
> |**Name**:<br />InvalidEntitlementRenew<br />**Hex**:<br />80060610<br />**Nummer**:<br />-2147088880|Sie können nur die Ansprüche erneuern, die abgelaufen sind oder abgebrochen wurden.|
> |**Name**:<br />InvalidEntitlementStateAssociateToCase<br />**Hex**:<br />80060611<br />**Nummer**:<br />-2147088879|Sie können eine Anfrage nur einem aktiven Anspruch zuordnen.|
> |**Name**:<br />InvalidEntitlementTotalTerms<br />**Hex**:<br />800443FF<br />**Nummer**:<br />-2147204097|Die Anzahl der gesamten Bedingungen für einen Anspruch darf nicht kleiner als die Anzahl der gesamten Bedingungen des entsprechenden EntitlementChannels sein.|
> |**Name**:<br />InvalidEntity<br />**Hex**:<br />8005E00C<br />**Nummer**:<br />-2147098612|Entität {0} kann nicht gefunden werden.|
> |**Name**:<br />InvalidEntityClassException<br />**Hex**:<br />80040249<br />**Nummer**:<br />-2147220919|Ungültige Entitätsklasse.|
> |**Name**:<br />InvalidEntityForDateAttribute<br />**Hex**:<br />80044812<br />**Nummer**:<br />-2147203054|"Entität für Datenattribut" kann entweder eine Quellentität oder dessen übergeordnetes Element sein.|
> |**Name**:<br />InvalidEntityForLinkedAttribute<br />**Hex**:<br />8004F0FD<br />**Nummer**:<br />-2147159811|Keine gültige Entität für verknüpftes Attribut.|
> |**Name**:<br />InvalidEntityForRollup<br />**Hex**:<br />80044813<br />**Nummer**:<br />-2147203053|Die Entität {0} gilt nicht für diese Entität für den Rollup.|
> |**Name**:<br />InvalidEntityKeyOperation<br />**Hex**:<br />8006088F<br />**Nummer**:<br />-2147088241|Ungültiger EntityKey-Vorgang durchgeführt: {0}|
> |**Name**:<br />InvalidEntityLogicalName<br />**Hex**:<br />80072493<br />**Nummer**:<br />-2147015533|Der Entitätsname „{0}” ist kein gültiger logischer Name.|
> |**Name**:<br />InvalidEntityName<br />**Hex**:<br />80048416<br />**Nummer**:<br />-2147187690|Der Datensatztyp entspricht nicht dem Datensatztyp und der übereinstimmenden Datensatztyp der Duplikaterkennungsregel.|
> |**Name**:<br />InvalidEntitySetName<br />**Hex**:<br />8006089B<br />**Nummer**:<br />-2147088229|Eine Entität mit dem angegebenen Entitätssatznamen {0} ist bereits vorhanden. Geben Sie einen eindeutigen Namen an.|
> |**Name**:<br />InvalidEntitySpecified<br />**Hex**:<br />800609B1<br />**Nummer**:<br />-2147087951|Die Entität wird in der Vorlage nicht definiert.|
> |**Name**:<br />InvalidExchangeRate<br />**Hex**:<br />80048cfd<br />**Nummer**:<br />-2147185411|Der Umrechnungskurs ist ungültig.|
> |**Name**:<br />InvalidExportProcessFlowNotActivated<br />**Hex**:<br />80060376<br />**Nummer**:<br />-2147089546|Fehler beim Exportieren von Geschäftsprozess „{0}”, da die Lösung keine entsprechende Geschäftsprozessentität „{1}” umfasst. Wenn dies ein neu erstellter Geschäftsprozess im Entwurfstatus ist, aktivieren Sie ihn einmal, um die Geschäftsprozessentität zu generieren und sie in der Lösung zu verwenden. Weitere Informationen finden Sie unter http://support.microsoft.com/kb/4337537.|
> |**Name**:<br />InvalidExternalCollectionName<br />**Hex**:<br />80046BA7<br />**Nummer**:<br />-2147193945|Der angegebene externe Sammlungsname ist nicht gültig.|
> |**Name**:<br />InvalidExternalName<br />**Hex**:<br />80046BC0<br />**Nummer**:<br />-2147193920|Der angegebene externe Name ist nicht gültig.|
> |**Name**:<br />InvalidExternalPartyConfiguration<br />**Hex**:<br />8006110F<br />**Nummer**:<br />-2147086065|Mehrere Elemente externer Parteien sind für Anforderungsparameter vorhanden.|
> |**Name**:<br />InvalidExternalPartyOperation<br />**Hex**:<br />80061111<br />**Nummer**:<br />-2147086063|Externe Partei ist nicht zulässig.|
> |**Name**:<br />InvalidExternalPartyParent<br />**Hex**:<br />80061110<br />**Nummer**:<br />-2147086064|Externe Partei hat ein ungültiges übergeordnetes Attribut.|
> |**Name**:<br />InvalidFeatureType<br />**Hex**:<br />80044272<br />**Nummer**:<br />-2147204494|Der Funktionstyp ist nicht gültig.|
> |**Name**:<br />InvalidFetchCollection<br />**Hex**:<br />8004E019<br />**Nummer**:<br />-2147164135|Die Fetch-Sammlung für die Visualisierung ist ungültig.|
> |**Name**:<br />InvalidFetchXml<br />**Hex**:<br />80040303<br />**Nummer**:<br />-2147220733|Falsch formatiertes FetchXml.|
> |**Name**:<br />InvalidFileBadCharacters<br />**Hex**:<br />80040396<br />**Nummer**:<br />-2147220586|Die Datei konnte nicht hochgeladen werden, da sie ungültige Zeichen enthält|
> |**Name**:<br />InvalidFileType<br />**Hex**:<br />800608CC<br />**Nummer**:<br />-2147088180|Ungültiger Dateityp.|
> |**Name**:<br />InvalidFilterCriteriaForVisualization<br />**Hex**:<br />8004E01E<br />**Nummer**:<br />-2147164130|Die Visualisierung kann für die vorgegebenen Filterkriterien nicht angepasst werden.|
> |**Name**:<br />InvalidFiscalPeriod<br />**Hex**:<br />80044814<br />**Nummer**:<br />-2147203052|Die Buchhaltungsperiode {0} fällt nicht in den Berechtigungsbereich für die Buchhaltungsperiode gemäss den Buchhaltungsperiodeneinstellungen der Organisation.|
> |**Name**:<br />InvalidFlowProcessClientData<br />**Hex**:<br />80060468<br />**Nummer**:<br />-2147089304|Fluss-Client-Daten sind im ungültigen Format. Details: „{0}”.|
> |**Name**:<br />InvalidFormatForControl<br />**Hex**:<br />80060875<br />**Nummer**:<br />-2147088267|Ungültiger Genauigkeits-Parameter für Steuerelement {0} angegeben. Es enthält keinen erwarteten Wert|
> |**Name**:<br />InvalidFormatForDataDelimiter<br />**Hex**:<br />80040355<br />**Nummer**:<br />-2147220651|Falsch zugeordnetes Datentrennzeichen: Es wurde nur ein Trennzeichen gefunden.|
> |**Name**:<br />InvalidFormatForUpdateMode<br />**Hex**:<br />8004F601<br />**Nummer**:<br />-2147158527|Die von Ihnen hochgeladene Datei ist ungültig und kann zum Aktualisieren von Datensätzen nicht verwendet werden.|
> |**Name**:<br />InvalidFormatParameters<br />**Hex**:<br />80047101<br />**Nummer**:<br />-2147192575|Die Anzahl der Formatparametern, die in der Eingabezeichenfolge übergeben wurden, sind ungültig|
> |**Name**:<br />InvalidFormType<br />**Hex**:<br />8004E306<br />**Nummer**:<br />-2147163386|Der Typ des Formulars muss auf {0} in das Formular XML festgelegt werden.|
> |**Name**:<br />InvalidFormTypeCalledThroughSdk<br />**Hex**:<br />80060874<br />**Nummer**:<br />-2147088268|"Ungültiger Formulartyp in Erstellungsaufruf.|
> |**Name**:<br />InvalidForOfficeGraph<br />**Hex**:<br />80044231<br />**Nummer**:<br />-2147204559|Eine oder beide Entitäten sind nicht für officegraph aktiviert und sie können nicht für officegraph verwendet werden.|
> |**Name**:<br />InvalidGoalAttribute<br />**Hex**:<br />8004480b<br />**Nummer**:<br />-2147203061|Zielattribut entspricht nicht dem angegebenen Metriktyp.|
> |**Name**:<br />InvalidGoalManager<br />**Hex**:<br />8004F684<br />**Nummer**:<br />-2147158396|Der Manager eines Ziels kann ein Benutzer und kein Team sein.|
> |**Name**:<br />InvalidGranularityValue<br />**Hex**:<br />8004B038<br />**Nummer**:<br />-2147176392|Der Granularitätsspaltenwert ist ungültig. Jeder Regelteil muss ein Name-Wert-Paar sein, das von einem Gleichheitszeichen (=) getrenntes wird. Beispiel: FREQ=Minuten; INTERVAL=15|
> |**Name**:<br />InvalidGroupByAlias<br />**Hex**:<br />8004E00F<br />**Nummer**:<br />-2147164145|Die Datenbeschreibung ist ungültig. Dieselbe Gruppe durch Alias kann nicht für verschiedene Attribute verwendet werden.|
> |**Name**:<br />InvalidGroupByColumn<br />**Hex**:<br />8004E01D<br />**Nummer**:<br />-2147164131|"Gruppieren nach" bei dem Attribut nicht zulässig.|
> |**Name**:<br />InvalidGuid<br />**Hex**:<br />80040363<br />**Nummer**:<br />-2147220637|Der Globally Unique Identifier (GUID) in dieser Zeile ist ungültig|
> |**Name**:<br />InvalidGuidInXaml<br />**Hex**:<br />80060407<br />**Nummer**:<br />-2147089401|Guid - {0} in XAML ist ungültig|
> |**Name**:<br />InvalidHeaderColumn<br />**Hex**:<br />80040344<br />**Nummer**:<br />-2147220668|Die Spaltenüberschrift enthält eine ungültige Kombination aus Datentrennzeichen.|
> |**Name**:<br />InvalidHexColorValue<br />**Hex**:<br />800608D0<br />**Nummer**:<br />-2147088176|Nur Hexadezimalwerte sind zulässig.|
> |**Name**:<br />InvalidHierarchicalRelationship<br />**Hex**:<br />8004701F<br />**Nummer**:<br />-2147192801|Diese Beziehung verweist nicht auf sich selbst und kann daher nicht hierarchisch gemacht werden.|
> |**Name**:<br />InvalidHierarchicalRelationshipChange<br />**Hex**:<br />8004701a<br />**Nummer**:<br />-2147192806|Sie können die Hierarchie dieser Entität nicht ändern, da die {0} hierarchische Beziehung nicht angepasst werden kann.|
> |**Name**:<br />InvalidImportFileContent<br />**Hex**:<br />80040374<br />**Nummer**:<br />-2147220620|Der Inhalt der Importdatei ist ungültig. Sie müssen eine Textdatei auswählen.|
> |**Name**:<br />InvalidImportFileData<br />**Hex**:<br />80040351<br />**Nummer**:<br />-2147220655|Die Daten besitzen nicht das erforderliche Format.|
> |**Name**:<br />InvalidImportFileParseData<br />**Hex**:<br />80040349<br />**Nummer**:<br />-2147220663|Für diese Datei sind weder Feld- noch Datentrennzeichen angegeben.|
> |**Name**:<br />InvalidImportJobId<br />**Hex**:<br />80044252<br />**Nummer**:<br />-2147204526|Die angeforderte importjob ist nicht vorhanden.|
> |**Name**:<br />InvalidImportJobTemplateFile<br />**Hex**:<br />80044251<br />**Nummer**:<br />-2147204527|Die ImportJobTemplate.xml-Datei ist ungültig.|
> |**Name**:<br />InvalidIncomingDeliveryExpectingEmailConnector<br />**Hex**:<br />8005E224<br />**Nummer**:<br />-2147098076|Die eingehende Zustellungsmethode ist kein E-Mail-Konnektor. Um E-Mails zu empfangen sollte die eingehende Zustellungsmethode E-Mail-Konnektor sein.|
> |**Name**:<br />InvalidInstanceEntityName<br />**Hex**:<br />8004E10D<br />**Nummer**:<br />-2147163891|Ungültiger Instanzentitätsname.|
> |**Name**:<br />InvalidInstanceTypeCode<br />**Hex**:<br />8004E107<br />**Nummer**:<br />-2147163897|Ungültiger Code für Instanztyp.|
> |**Name**:<br />InvalidInteractiveUserQuota<br />**Hex**:<br />8004B049<br />**Nummer**:<br />-2147176375|Sie haben die zulässige Höchstanzahl an interaktiven/vollständigen Benutzern überschritten.|
> |**Name**:<br />InvalidIntersectEntity<br />**Hex**:<br />80072540<br />**Nummer**:<br />-2147015360|Kann nicht mit einer vorhandenen sich nicht überschneidenden Entität {0} als sich überschneidende Entität verwendet werden, um m:n-Beziehungen zu definieren.|
> |**Name**:<br />InvalidInvitationLiveId<br />**Hex**:<br />8004D20E<br />**Nummer**:<br />-2147167730|Ein Benutzer mit dieser E-Mail-Adresse wurde nicht gefunden. Melden Sie sich bei Windows Live ID mit der gleichen E-Mail-Adresse an, mit der Sie die Einladung erhalten haben.  Wenn Sie nicht über eine Windows Live-ID verfügen, erstellen Sie eine mit dieser E-Mail-Adresse.|
> |**Name**:<br />InvalidInvitationToken<br />**Hex**:<br />8004D20D<br />**Nummer**:<br />-2147167731|Der Einladungstoken {0} wird nicht ordnungsgemäß formatiert.|
> |**Name**:<br />InvalidIsFirstRowHeaderForUseSystemMap<br />**Hex**:<br />80040364<br />**Nummer**:<br />-2147220636|Die erste Zeile der Datei enthält keine Spaltenüberschriften.|
> |**Name**:<br />InvalidIsoCurrencyCode<br />**Hex**:<br />80048cf2<br />**Nummer**:<br />-2147185422|Ungültiger ISO Währungscode.|
> |**Name**:<br />InvalidKeyQuery<br />**Hex**:<br />80072529<br />**Nummer**:<br />-2147015383|Schlüssel müssen Teil einer der angeforderten EntityMetadata-Eigenschaften sein, wenn KeyQuery angegeben ist. Erwartete Eigenschaft = {0} in der angeforderten Entitätseigenschaftsliste.|
> |**Name**:<br />InvalidKit<br />**Hex**:<br />80043afd<br />**Nummer**:<br />-2147206403|Das Produkt ist kein Bausatz.|
> |**Name**:<br />InvalidKitProduct<br />**Hex**:<br />80043afe<br />**Nummer**:<br />-2147206402|Sie können einem zurückgezogenen Bausatz kein Produkt hinzufügen. Wählen Sie ein anderes Produkt oder ein Produktkit aus.|
> |**Name**:<br />InvalidLanguageCode<br />**Hex**:<br />80044195<br />**Nummer**:<br />-2147204715|Der Sprachcode für die angegebene Organisation ist ungültig.|
> |**Name**:<br />InvalidLanguageForCreate<br />**Hex**:<br />80060750<br />**Nummer**:<br />-2147088560|Zeilen mit lokalisierbaren Attributen können nur erstellt werden, wenn die Sprache der Benutzeroberfläche für den aktuellen Benutzer auf die Ausgangssprache der Organisation gesetzt ist.|
> |**Name**:<br />InvalidLanguageForProcessConfiguration<br />**Hex**:<br />8005E102<br />**Nummer**:<br />-2147098366|Prozesskonfigurationen sind nicht verfügbar, da Ihre Sprache nicht der Ausgangssprache des Systems entspricht.|
> |**Name**:<br />InvalidLanguageForSolution<br />**Hex**:<br />80047019<br />**Nummer**:<br />-2147192807|Die Lösungs- und Herausgeberoptionen sind nicht verfügbar, da Ihre Sprache nicht der Ausgangssprache des Systems entspricht.|
> |**Name**:<br />InvalidLanguageForUpdate<br />**Hex**:<br />80060751<br />**Nummer**:<br />-2147088559|Lokalisierbare Attribute können nur über die Zeichenfolgeeigenschaft aktualisiert werden, wenn die Sprache der Benutzeroberfläche für den aktuellen Benutzer auf die Ausgangssprache der Organisation gesetzt ist. Verwendung von SetLocLabels um die lokalisierten Werte für die folgenden Attribute zu aktualisieren: [{0}].|
> |**Name**:<br />InvalidLicenseCannotReadMpcFile<br />**Hex**:<br />8004D245<br />**Nummer**:<br />-2147167675|Ungültige Lizenz. MPC-Code kann nicht aus MPC.txt- Dateien mit diesen Pfad {0} lesen.|
> |**Name**:<br />InvalidLicenseKey<br />**Hex**:<br />8004D240<br />**Nummer**:<br />-2147167680|Ungültiger Lizenzschlüssel ({0})|
> |**Name**:<br />InvalidLicenseMpcCode<br />**Hex**:<br />8004D246<br />**Nummer**:<br />-2147167674|Ungültige Lizenz. Ungültiger MPC-Code ({0}).|
> |**Name**:<br />InvalidLicensePid<br />**Hex**:<br />8004D242<br />**Nummer**:<br />-2147167678|Ungültige Lizenz. Ungültige PID (Produkt-ID) ({0}).|
> |**Name**:<br />InvalidLicensePidGenCannotLoad<br />**Hex**:<br />8004D243<br />**Nummer**:<br />-2147167677|Ungültige Lizenz. PidGen.dll kann nicht aus diesen Pfad geladen werden {0}|
> |**Name**:<br />InvalidLicensePidGenOtherError<br />**Hex**:<br />8004D244<br />**Nummer**:<br />-2147167676|Ungültige Lizenz. PID (Produkt-ID) kann nicht vom Lizenzschlüssel erstellt werden. Fehlercode PidGen: ({0}).|
> |**Name**:<br />InvalidLocaleIdForKnowledgeArticle<br />**Hex**:<br />80061400<br />**Nummer**:<br />-2147085312|Sprache mit Gebietsschema-ID {0} ist nicht vorhanden|
> |**Name**:<br />InvalidLogoImageId<br />**Hex**:<br />800608D3<br />**Nummer**:<br />-2147088173|Ungültige Webressourcen-ID für Logobild.|
> |**Name**:<br />InvalidLogoImageWebResourceType<br />**Hex**:<br />800608D9<br />**Nummer**:<br />-2147088167|Ungültiger WebResource-Typ für das Logobild.|
> |**Name**:<br />InvalidLookupMapNode<br />**Hex**:<br />80048481<br />**Nummer**:<br />-2147187583|Die Suchentität ist für das gegebene Zielfeldattribut nicht gültig.|
> |**Name**:<br />InvalidMailbox<br />**Hex**:<br />8005E217<br />**Nummer**:<br />-2147098089|Ungültige MailboxId übergeben. Überprüfen Sie die mailboxid.|
> |**Name**:<br />InvalidManagedPropertyException<br />**Hex**:<br />8004F030<br />**Nummer**:<br />-2147160016|Verwaltete Eigenschaft {0} enthält nicht genug Informationen, um erstellt zu werden.  Bitte stellen Sie Assembly Klasse (,) oder (Entität, Attribut) zur Verfügung oder legen Sie die verwaltete Eigenschaft auf Benutzerdefiniert fest.|
> |**Name**:<br />InvalidManifestFilePath<br />**Hex**:<br />80048533<br />**Nummer**:<br />-2147187405|Die Manifestdatei wurde im angegebenen Speicherort nicht gefunden|
> |**Name**:<br />InvalidMatchingAttributeError<br />**Hex**:<br />80044244<br />**Nummer**:<br />-2147204540|Ungültiges übereinstimmendes Attribut.|
> |**Name**:<br />InvalidMaximumResourceLimit<br />**Hex**:<br />8004B02B<br />**Nummer**:<br />-2147176405|Der Ressourcentyp {0} kann keine Höchstgrenze von {1} haben.|
> |**Name**:<br />InvalidMaxLengthForControl <br />**Hex**:<br />80060879<br />**Nummer**:<br />-2147088263|Für das Steuerelement {0} wurde ein ungültiger MaxLength-Parameter angegeben. Die maximale Länge muss zwischen {1} und {2} liegen.|
> |**Name**:<br />InvalidMaxValueForControl <br />**Hex**:<br />8006087B<br />**Nummer**:<br />-2147088261|Für das Steuerelement {0} wurde ein ungültiger MaxValue-Parameter angegeben. Der Maximalwert muss zwischen {1} und {2} liegen.|
> |**Name**:<br />InvalidMeasureCollection<br />**Hex**:<br />8004E00A<br />**Nummer**:<br />-2147164150|Measure-Sammlung ist ungültig Nicht alle Kennzahlen in der Kennzahlsammlung haben die gleichen GROUP BYs.|
> |**Name**:<br />InvalidMetadata<br />**Hex**:<br />8004023a<br />**Nummer**:<br />-2147220934|Ungültige Metadaten.|
> |**Name**:<br />InvalidMetadataSqlOperation<br />**Hex**:<br />80072343<br />**Nummer**:<br />-2147015869|SQL-Ausnahme wurde in dem aktuellen Metadatenvorgang ausgegeben. Überprüfen Sie die Ausnahme, um weitere Informationen zu erhalten.|
> |**Name**:<br />InvalidMigrationFileContent<br />**Hex**:<br />8005F033<br />**Nummer**:<br />-2147094477|Der Inhalt der Importdatei ist ungültig. Sie müssen eine Textdatei auswählen.|
> |**Name**:<br />InvalidMinAndMaxValueForControl <br />**Hex**:<br />8006087C<br />**Nummer**:<br />-2147088260|Für das Steuerelement {0} wurden ein ungültiger MinValue- und ein ungültiger MaxValue-Parameter angegeben. Der Mindestwert muss kleiner sein als der Maximalwert.|
> |**Name**:<br />InvalidMinimumResourceLimit<br />**Hex**:<br />8004B02A<br />**Nummer**:<br />-2147176406|Der Ressourcentyp {0} kann keine Mindestgrenze von {1} haben.|
> |**Name**:<br />InvalidMinValueForControl <br />**Hex**:<br />8006087A<br />**Nummer**:<br />-2147088262|Für das Steuerelement {0} wurde ein ungültiger MinValue-Parameter angegeben. Der Mindestwert muss zwischen {1} und {2} liegen.|
> |**Name**:<br />InvalidMobileOfflineFiltersFetchXml<br />**Hex**:<br />80071113<br />**Nummer**:<br />-2147020525|XML-Formatkonflikt. Überprüfen Sie die Korrektheit des XML.|
> |**Name**:<br />InvalidMultipleMapping<br />**Hex**:<br />80048498<br />**Nummer**:<br />-2147187560|Ein Quellfeld ist mehreren Nachschlage-/Auswahllistenfeldern von Dynamics 365 zugeordnet.|
> |**Name**:<br />InvalidMultipleSiteMapReferenceSingleAppModule<br />**Hex**:<br />80050111<br />**Nummer**:<br />-2147155695|Eine App kann nicht über mehrere Siteübersichten verfügen.|
> |**Name**:<br />InvalidNamePrefix<br />**Hex**:<br />80044366<br />**Nummer**:<br />-2147204250|Der Schemaname {0} für den Typ {2} ist ungültig oder fehlt- Benutzerdefinierte Namen für Attribute, Entitäten, Entitätsschlüssel, Optionssätue und Beziehungen müssen mit einem gültige Anpassungspräfix beginnen. Das Präfix für eine Lösungskomponente muss dem Präfix entsprechen, das für den Herausgeber der Lösung angegeben ist.|
> |**Name**:<br />InvalidNetPrice<br />**Hex**:<br />800404f3<br />**Nummer**:<br />-2147220237|Der Nettopreis ist ungültig|
> |**Name**:<br />InvalidNonInteractiveUserQuota<br />**Hex**:<br />8004B050<br />**Nummer**:<br />-2147176368|Sie haben die zulässige Höchstanzahl an nicht-interaktiven Benutzern überschritten.|
> |**Name**:<br />InvalidNumberGroupFormat<br />**Hex**:<br />80043700<br />**Nummer**:<br />-2147207424|Ungültige Eingabezeichenfolge für numbergroupformat. Die entsprechenden Hardwarefehlertoleranz sollte als Eingabezeichenfolge ganze Zahlen enthalten. Jedes Element im Wertarray sollte zwischen einem und neun liegen, außer dem letzten Element, das null sein kann.|
> |**Name**:<br />InvalidNumberOfCardFormSections<br />**Hex**:<br />80061505<br />**Nummer**:<br />-2147085051|Die Anzahl der Abschnitte in einem Kartenformular muss 4 betragen. {0} gefunden.|
> |**Name**:<br />InvalidNumberOfPartitions<br />**Hex**:<br />8004E200<br />**Nummer**:<br />-2147163648|Sie können auf den Partitionen Überwachungsdaten nicht löschen, die derzeit verwendet wurden, oder aber die Partitionen löschen, die zum Speichern in Kenntnis Überwachungsdaten erstellt werden.|
> |**Name**:<br />InvalidNumberOfReferencePanelSections<br />**Hex**:<br />80061504<br />**Nummer**:<br />-2147085052|MainInteractionCentric-Formular darf nur über 1 Abschnitt im Bereich "Verweise" verfügen. {0} gefunden.|
> |**Name**:<br />InvalidNumberOfSectionsInTab<br />**Hex**:<br />80060872<br />**Nummer**:<br />-2147088270|Ein XML-Dialogformular kann nicht mehrere Abschnitte enthalten.|
> |**Name**:<br />InvalidNumberOfTabsInDialog<br />**Hex**:<br />80060871<br />**Nummer**:<br />-2147088271|Ein XML-Dialogformular kann nicht mehrere Registerkarten enthalten.|
> |**Name**:<br />InvalidOAuthToken<br />**Hex**:<br />80041d50<br />**Nummer**:<br />-2147214000|Das OAuth-Token ist ungültig|
> |**Name**:<br />InvalidObjectTypes<br />**Hex**:<br />8004021f<br />**Nummer**:<br />-2147220961|Ungültiger Objekttyp.|
> |**Name**:<br />InvalidOccurrenceNumber<br />**Hex**:<br />8004E125<br />**Nummer**:<br />-2147163867|Das Enddatum eines Vertrags kann nicht vor dem Startdatum liegen. Wählen Sie eine gültige Vorkommenszahl aus.|
> |**Name**:<br />InvalidOfflineOperation<br />**Hex**:<br />8004410e<br />**Nummer**:<br />-2147204850|Der Vorgang ist im Offlinemodus ungültig.|
> |**Name**:<br />InvalidOneToManyRelationship<br />**Hex**:<br />80072500<br />**Nummer**:<br />-2147015424|1:n-Entitätsbeziehung mit EntityRelationshipId „{0}” hat Null ReferencingEntityRole|
> |**Name**:<br />InvalidOneToManyRelationshipForRelatedEntitiesQuery<br />**Hex**:<br />8004430F<br />**Nummer**:<br />-2147204337|Ein ungültiges OneToManyRelationship-Element wurde für das RelatedEntitiesQuery-Element angegeben. Referenzierte {0} Entität sollte gleich sein wie die primäre Entität {1}|
> |**Name**:<br />InvalidOperandOnLeftHandSide<br />**Hex**:<br />80072501<br />**Nummer**:<br />-2147015423|Die linke Seite des Operators „{0}” muss eine Eigenschaft der Entität sein.|
> |**Name**:<br />InvalidOperation<br />**Hex**:<br />8004023b<br />**Nummer**:<br />-2147220933|Ungültiger Vorgang ausgeführt.|
> |**Name**:<br />InvalidOperationForClosedOrCancelledCampaignActivity<br />**Hex**:<br />80040314<br />**Nummer**:<br />-2147220716|Der geschlossenen (abgebrochenen) Kampagnenaktivität können keine Elemente hinzugefügt werden.|
> |**Name**:<br />InvalidOperationForDynamicList<br />**Hex**:<br />8004F701<br />**Nummer**:<br />-2147158271|Die Aktion ist für eine dynamische Marketingliste nicht verfügbar.|
> |**Name**:<br />InvalidOperationWhenListIsNotActive<br />**Hex**:<br />8004033a<br />**Nummer**:<br />-2147220678|Liste ist nicht aktiv. Kann diesen Vorgang nicht ausführen.|
> |**Name**:<br />InvalidOperationWhenListLocked<br />**Hex**:<br />80040302<br />**Nummer**:<br />-2147220734|Liste ist gesperrt. Kann die Aktion nicht ausführen.|
> |**Name**:<br />InvalidOperationWhenPartyIsNotActive<br />**Hex**:<br />8004033b<br />**Nummer**:<br />-2147220677|Die Partei ist nicht aktiv. Kann diesen Vorgang nicht ausführen.|
> |**Name**:<br />InvalidOperatorCode<br />**Hex**:<br />80048415<br />**Nummer**:<br />-2147187691|Der Operator ist ungültig, oder wird nicht unterstützt.|
> |**Name**:<br />InvalidOperatorCodeError<br />**Hex**:<br />80044253<br />**Nummer**:<br />-2147204525|Ungültiger Operatortyp.|
> |**Name**:<br />InvalidOptionSetIdForControl<br />**Hex**:<br />80060876<br />**Nummer**:<br />-2147088266|Für das Steuerelement {0} wurde ein ungültiger OptionSetId-Wert angegeben. Die OptionSet-ID ist eine nicht leere GUID.|
> |**Name**:<br />InvalidOptionSetNameChange<br />**Hex**:<br />80048409<br />**Nummer**:<br />-2147187703|OptionSet Name {0}, Id: {1} kann nicht aktualisiert werden, da der für den OptionSet-Name bereitgestellte Wert ({2}) durch ein anderes vorhandenes OptionSet (id: {3}) verwendet wird|
> |**Name**:<br />InvalidOptionSetOperation<br />**Hex**:<br />80048403<br />**Nummer**:<br />-2147187709|Ungültiges OptionSet|
> |**Name**:<br />InvalidOptionSetSchemaName<br />**Hex**:<br />80044345<br />**Nummer**:<br />-2147204283|OptionSet mit dem angegebenen Namen ist bereits vorhanden. Geben Sie einen eindeutigen Namen an.|
> |**Name**:<br />InvalidOrEmptyRelationshipId<br />**Hex**:<br />80071122<br />**Nummer**:<br />-2147020510|Die RelationshipId der Zuordnung des Mobile-Profilelements ist ungültig oder leer.|
> |**Name**:<br />InvalidOrganizationFriendlyName<br />**Hex**:<br />8004D252<br />**Nummer**:<br />-2147167662|Ungültige Anzeigename der Organisation ({0}). Grund: ({1})|
> |**Name**:<br />InvalidOrganizationId<br />**Hex**:<br />80044248<br />**Nummer**:<br />-2147204536|Die Organisations-ID, die in der Übersetzungsdatei vorhanden ist, entspricht der aktuellen Organisations-ID.|
> |**Name**:<br />InvalidOrganizationSettings<br />**Hex**:<br />8006110D<br />**Nummer**:<br />-2147086067|Organisationseinstellungen werden auf der Seite nicht ordnungsgemäß konfiguriert.|
> |**Name**:<br />InvalidOrganizationUniqueName<br />**Hex**:<br />8004D251<br />**Nummer**:<br />-2147167663|Ungültiger eindeutiger Name der Organisation ({0}). Grund: ({1})|
> |**Name**:<br />InvalidOrgDBOrgSetting<br />**Hex**:<br />80048514<br />**Nummer**:<br />-2147187436|Ungültige Organisationseinstellung übergeben. Bitte überprüfen Sie den Datentyp und übergeben Sie einen geeigneten Wert.|
> |**Name**:<br />InvalidOrgOwnedCascadeLinkType<br />**Hex**:<br />80044156<br />**Nummer**:<br />-2147204778|"Kaskadieren, falls gleicher Besitzer" ist kein gültiger Linktyp für Beziehungen von Entitäten im Organisationsbesitz.|
> |**Name**:<br />InvalidOtherDataFilterOptions<br />**Hex**:<br />8006098D<br />**Nummer**:<br />-2147087987|Wählen Sie mindestens eine Option aus "Eigene Datensätze herunterladen", "Teamdatensätze herunterladen" oder "Datensätze der Unternehmenseinheit herunterladen" aus.|
> |**Name**:<br />InvalidOutgoingDeliveryExpectingEmailConnector<br />**Hex**:<br />8005E226<br />**Nummer**:<br />-2147098074|Die ausgehende Zustellungsmethode ist kein E-Mail-Konnektor. Um E-Mails zu senden sollte die eingehende Zustellungsmethode E-Mail-Konnektor sein.|
> |**Name**:<br />InvalidOwnerID<br />**Hex**:<br />80040229<br />**Nummer**:<br />-2147220951|Die Besitzer-ID ist fehlend oder ungültig.|
> |**Name**:<br />InvalidOwnershipTypeMask<br />**Hex**:<br />8004700d<br />**Nummer**:<br />-2147192819|Die angegebene Besitztypmaske ist für diesen Vorgang nicht gültig.|
> |**Name**:<br />InvalidPageResponse<br />**Hex**:<br />8004E00D<br />**Nummer**:<br />-2147164147|Eine ungültige Seitenantwort wurde generiert.|
> |**Name**:<br />InvalidParent<br />**Hex**:<br />80040205<br />**Nummer**:<br />-2147220987|Das übergeordente Objekt ist fehlend oder ungültig.|
> |**Name**:<br />InvalidParentId<br />**Hex**:<br />80040206<br />**Nummer**:<br />-2147220986|Die übergeordente ID ist fehlend oder ungültig.|
> |**Name**:<br />InvalidPartnerSolutionCustomizationProvider<br />**Hex**:<br />8004A109<br />**Nummer**:<br />-2147180279|Ungültiger Anpassungsanbietertyp der Partnerslösung|
> |**Name**:<br />InvalidPartyMapping<br />**Hex**:<br />80043515<br />**Nummer**:<br />-2147207915|Ungültige Parteizuordnung.|
> |**Name**:<br />InvalidPluginAssemblyContent<br />**Hex**:<br />8004418b<br />**Nummer**:<br />-2147204725|Plug-In-Assembly enthält nicht über die benötigten Datensatztypen, oder Assemblyinhalt kann nicht aktualisiert werden.|
> |**Name**:<br />InvalidPluginAssemblyVersion<br />**Hex**:<br />8004417B<br />**Nummer**:<br />-2147204741|Plug-In-Assembly fullnames müssen eindeutig sein (der Versionsbuild und -Revisionsnummer ignorierend).|
> |**Name**:<br />InvalidPluginRegistrationConfiguration<br />**Hex**:<br />80044170<br />**Nummer**:<br />-2147204752|Das die Plug-In-Assemblyregistrierungskonfiguration ist ungültig.|
> |**Name**:<br />InvalidPluginStrongNameRequired<br />**Hex**:<br />80081114<br />**Nummer**:<br />-2146954988|Plug-In-Assembly ist nicht der signierte starke Name.|
> |**Name**:<br />InvalidPluginTypeImplementation<br />**Hex**:<br />8004418c<br />**Nummer**:<br />-2147204724|Plug-In-Typ muss eine der folgenden Schnittstellen oder Klassen exakt implementieren: Microsoft.Crm.Sdk.IPlugin, Microsoft.Xrm.Sdk.IPlugin, System.Activities.Activity und System.Workflow.ComponentModel.Activity.|
> |**Name**:<br />InvalidPointer<br />**Hex**:<br />80040218<br />**Nummer**:<br />-2147220968|Das Ziel ist abgeschafft.|
> |**Name**:<br />InvalidPrecisionForControl <br />**Hex**:<br />8006087D<br />**Nummer**:<br />-2147088259|Für das Steuerelement {0} wurde ein ungültiger Präzisionsparameter angegeben. Der Präzisionsparameter muss zwischen {1} und {2} liegen.|
> |**Name**:<br />InvalidPresentationDescription<br />**Hex**:<br />8004E002<br />**Nummer**:<br />-2147164158|Die Präsentationsbeschreibung ist ungültig.|
> |**Name**:<br />InvalidPreviewModeOperation<br />**Hex**:<br />8005f219<br />**Nummer**:<br />-2147093991|Es ist nicht möglich, diesen Vorgang im Vorschaumodus auszuführen.|
> |**Name**:<br />InvalidPriceLevelCurrencyForPricingMethod<br />**Hex**:<br />80048cf9<br />**Nummer**:<br />-2147185415|Die Währung der Preisliste muss der gewünschten Währung der Preisliste für Rabatttypbetrag entsprechen.|
> |**Name**:<br />InvalidPricePerUnit<br />**Hex**:<br />80043b10<br />**Nummer**:<br />-2147206384|Der Preis pro Einheit ist ungültig.|
> |**Name**:<br />InvalidPrimaryContactBasedOnAccount<br />**Hex**:<br />8004F864<br />**Nummer**:<br />-2147157916|Der gewünschte Kontakt gehört nicht dem Konto an, für das der Kunde aktiviert ist. Geben Sie einen Kontakt an, der der ausgewählten Firma gehört, und versuchen Sie es anschließend erneut.|
> |**Name**:<br />InvalidPrimaryContactBasedOnContact<br />**Hex**:<br />8004F865<br />**Nummer**:<br />-2147157915|Der gewünschte Kontakt gehört nicht zum Kontakt, der im Feld angegeben wurde. Entfernen Sie den Wert im Kontaktfeld, oder wählen Sie einen Kontakt aus, der ausgewählten Kunden zugeordnet ist, und versuchen Sie es anschließend erneut.|
> |**Name**:<br />InvalidPrimaryFieldForActivity<br />**Hex**:<br />8004F127<br />**Nummer**:<br />-2147159769|Bei einer benutzerdefinierten Entität, die als Aktivität definiert wird, kann kein primäres Attribut außer Betreff haben.|
> |**Name**:<br />InvalidPrimaryFieldType<br />**Hex**:<br />8004700e<br />**Nummer**:<br />-2147192818|Benutzeroberfläche Primäres Attribut muss der Typzeichenfolge sein|
> |**Name**:<br />InvalidPrimaryKey<br />**Hex**:<br />80040266<br />**Nummer**:<br />-2147220890|Ungültige primäre Schlüssel.|
> |**Name**:<br />InvalidPrincipalId<br />**Hex**:<br />80048348<br />**Nummer**:<br />-2147187896|Die übergebene Guid ist leer.|
> |**Name**:<br />InvalidPrincipalType<br />**Hex**:<br />80048346<br />**Nummer**:<br />-2147187898|Ungültiger Prinzipaltyp übergeben.|
> |**Name**:<br />InvalidPriv<br />**Hex**:<br />8004024b<br />**Nummer**:<br />-2147220917|Ungültiger Rechtstyp.|
> |**Name**:<br />InvalidPrivilegeDepth<br />**Hex**:<br />8004140b<br />**Nummer**:<br />-2147216373|Ungültige Rechtstiefe.|
> |**Name**:<br />InvalidProcessControlAttribute<br />**Hex**:<br />8005E105<br />**Nummer**:<br />-2147098363|Die prozesskontrollierte Definition enthält ein ungültiges Attribut.|
> |**Name**:<br />InvalidProcessControlEntity<br />**Hex**:<br />8005E104<br />**Nummer**:<br />-2147098364|Die prozesskontrollierte Definiton enthält eine ungültige Entität oder einen ungültigen Entitätsauftrag.|
> |**Name**:<br />InvalidProcessIdOperation<br />**Hex**:<br />80092001<br />**Nummer**:<br />-2146885631|Ungültiger Vorgang. Prozess-ID kann nicht geändert werden.|
> |**Name**:<br />InvalidProcessStateData<br />**Hex**:<br />80045049<br />**Nummer**:<br />-2147200951|ProcessState ist für bestimmte ProcessSessions-Instanz ungültig.|
> |**Name**:<br />InvalidProduct<br />**Hex**:<br />80060623<br />**Nummer**:<br />-2147088861|Sie können keine Produktfamilie hinzufügen.|
> |**Name**:<br />InvalidPublisherUniqueName<br />**Hex**:<br />8004F01C<br />**Nummer**:<br />-2147160036|Herausgeber uniquename ist erforderlich.|
> |**Name**:<br />InvalidPublishOnProtectedComponent<br />**Hex**:<br />8004F014<br />**Nummer**:<br />-2147160044|Sie können {0} {1} nicht veröffentlichen. Veröffentlichung kann nicht ausgeführt werden, falls {0} verwaltet wird.|
> |**Name**:<br />InvalidQuantityDecimalCode<br />**Hex**:<br />80043afc<br />**Nummer**:<br />-2147206404|Ungültiger Mengendezimalcode.|
> |**Name**:<br />InvalidQuery<br />**Hex**:<br />80044183<br />**Nummer**:<br />-2147204733|Die Warteschlange, für diesen Vorgang ist ungültig|
> |**Name**:<br />InvalidQueryForVirtualEntity<br />**Hex**:<br />80044822<br />**Nummer**:<br />-2147203038|Die angegebene Abfrage wird für die virtuelle Entität nicht unterstützt.|
> |**Name**:<br />InvalidRecurrenceInterval<br />**Hex**:<br />8004D2A1<br />**Nummer**:<br />-2147167583|Geben Sie zum Festlegen der Serie ein Intervall zwischen 1 und 365 an.|
> |**Name**:<br />InvalidRecurrenceIntervalForRollupJobs<br />**Hex**:<br />8004D2A2<br />**Nummer**:<br />-2147167582|Zum Festlegen der Serie müssen Sie ein Intervall angeben, das größer als 1 Stunde sein muss.|
> |**Name**:<br />InvalidRecurrencePattern<br />**Hex**:<br />8004E100<br />**Nummer**:<br />-2147163904|Ungültiges Serienmuster.|
> |**Name**:<br />InvalidRecurrenceRule<br />**Hex**:<br />80040246<br />**Nummer**:<br />-2147220922|Fehler bei RecurrencePatternFactory.|
> |**Name**:<br />InvalidRecurrenceRuleForBulkDeleteAndDuplicateDetection<br />**Hex**:<br />8004D2A0<br />**Nummer**:<br />-2147167584|Massenlöschung und Duplikaterkennungswiederholung müssen täglich angegeben werden.|
> |**Name**:<br />InvalidRegardingObjectTypeCode<br />**Hex**:<br />80040319<br />**Nummer**:<br />-2147220711|Der entsprechende Objekttyp-Code ist für den Massenvorgang ungültig.|
> |**Name**:<br />InvalidRegistryKey<br />**Hex**:<br />8004024c<br />**Nummer**:<br />-2147220916|Ungültiger Registrierungsschlüssel angegeben.|
> |**Name**:<br />InvalidRelationshipDescription<br />**Hex**:<br />80047003<br />**Nummer**:<br />-2147192829|Die angegebene Beziehung kann nicht erstellt werden|
> |**Name**:<br />InvalidRelationshipInMOPIAssociation<br />**Hex**:<br />80060999<br />**Nummer**:<br />-2147087975|Diese Beziehung ist für die im übergeordneten Profilelement ausgewählte Entität nicht vorhanden.|
> |**Name**:<br />InvalidRelationshipNameForControl<br />**Hex**:<br />80060877<br />**Nummer**:<br />-2147088265|Für das Steuerelement {0} wurde kein Beziehungsname angegeben. Der Beziehungsname ist ein Pflichtfeld.|
> |**Name**:<br />InvalidRelationshipQuery<br />**Hex**:<br />80072528<br />**Nummer**:<br />-2147015384|Mindestens eine der Beziehungseigenschaften muss Teil einer der angeforderten EntityMetadata-Eigenschaften sein, wenn RelationshipQuery angegeben ist. Sie können mindestens eine Eigenschaft = {0}, {1} oder {2} in der angeforderten Entitätseigenschaftsliste erwarten.|
> |**Name**:<br />InvalidRelationshipType<br />**Hex**:<br />8004700f<br />**Nummer**:<br />-2147192817|Der angegebene Geschäftsbeziehungstyp ist für diesen Vorgang nicht gültig|
> |**Name**:<br />InvalidRelationshipTypeForAccessory<br />**Hex**:<br />8004F989<br />**Nummer**:<br />-2147157623|Eine Zubehör-Beziehung ist stets unilateral und kann nicht geändert werden.|
> |**Name**:<br />InvalidRelationshipTypeForUpSell<br />**Hex**:<br />8004F988<br />**Nummer**:<br />-2147157624|Eine UpSell-Beziehung ist stets unilateral und kann nicht geändert werden.|
> |**Name**:<br />InvalidRelativeUrlFormat<br />**Hex**:<br />80048054<br />**Nummer**:<br />-2147188652|Die relative URL enthält ungültige Zeichen. Verwenden Sie einen anderen Namen. Eine relative URL darf nicht auf ASPX, ASHX, ASMX und SVC enden und darf weder mit einem Punkt oder Schrägstrich (/) beginnen noch auf einen Punkt (.) oder Schrägstrich (/) enden. Sie darf keines der folgenden Zeichen enthalten: ~ " # % & * : < > ? / \ { | }.|
> |**Name**:<br />InvalidRequestBody<br />**Hex**:<br />80072530<br />**Nummer**:<br />-2147015376|Das übergebene Entitätsobjekt darf nicht Null oder leer sein.|
> |**Name**:<br />InvalidRequestDataFormat<br />**Hex**:<br />80044271<br />**Nummer**:<br />-2147204495|Die aktualisierte Konfiguration enthält ungültige Daten.|
> |**Name**:<br />InvalidRequestParameter<br />**Hex**:<br />80044828<br />**Nummer**:<br />-2147203032|Sowohl der Name als auch der Wert sollten für den Abfrageparameter angegeben werden.|
> |**Name**:<br />InvalidRequestParameters<br />**Hex**:<br />8006110E<br />**Nummer**:<br />-2147086066|Anforderungsparameter sind nicht für Server externer Parteianfragen gültig.|
> |**Name**:<br />InvalidResourceType<br />**Hex**:<br />8004B029<br />**Nummer**:<br />-2147176407|Die angeforderte Aktion ist für Ressourcentyp ungültig {0}.|
> |**Name**:<br />InvalidRestore<br />**Hex**:<br />80040258<br />**Nummer**:<br />-2147220904|RestoreCaller muss nach SwitchToSystemUser aufgerufen werden.|
> |**Name**:<br />InvalidRole<br />**Hex**:<br />8004B012<br />**Nummer**:<br />-2147176430|Sie haben für diesen Benutzer keine Rollen zugewiesen|
> |**Name**:<br />InvalidRoleOccurrencesForOneToManyRelationship<br />**Hex**:<br />8006089A<br />**Nummer**:<br />-2147088230|Es kann nicht mehr als zwei Entitätsbeziehungsrollen für eine 1:n-Beziehung geben {0}.|
> |**Name**:<br />InvalidRoleTypeForOneToManyRelationship<br />**Hex**:<br />80060899<br />**Nummer**:<br />-2147088231|Die Geschäftsbeziehungsrolle ist nicht für eine 1: n-Beziehung gültig {0}.|
> |**Name**:<br />InvalidRollupQueryAttributeSet<br />**Hex**:<br />8004F683<br />**Nummer**:<br />-2147158397|Eine Rollupabfrage kann nicht für ein Rollupfeld festgelegt werden, das nicht in der Zielmetrik definiert ist.|
> |**Name**:<br />InvalidRollupType<br />**Hex**:<br />80040234<br />**Nummer**:<br />-2147220940|Der Rollup-Typ ist ungültig.|
> |**Name**:<br />InvalidS2SAuthentication<br />**Hex**:<br />8005E245<br />**Nummer**:<br />-2147098043|Sie können Server-zu-Server-Authentifizierung nur für die E-Mail-Server-Profile verwenden, die für Microsoft Dynamics 365 Online-Organisation erstellt wurden, die für die Microsoft Online Services-Umgebung (Office 365) installiert wurde.|
> |**Name**:<br />InvalidSchemaName<br />**Hex**:<br />8004700b<br />**Nummer**:<br />-2147192821|Ein Eintrag mit dem angegebenen Namen ist bereits vorhanden. Geben Sie einen eindeutigen Namen an.|
> |**Name**:<br />InvalidSearchEntities<br />**Hex**:<br />80060202<br />**Nummer**:<br />-2147089918|Suchen - {0} fand keine gültigen Entitäten.|
> |**Name**:<br />InvalidSearchEntity<br />**Hex**:<br />80060201<br />**Nummer**:<br />-2147089919|Ungültige Suchentität - {0}.|
> |**Name**:<br />InvalidSearchName<br />**Hex**:<br />80060204<br />**Nummer**:<br />-2147089916|Ungültiger Suchbegriff - {0}.|
> |**Name**:<br />InvalidSeriesId<br />**Hex**:<br />8004E105<br />**Nummer**:<br />-2147163899|SeriesId ist Null oder ungültig.|
> |**Name**:<br />InvalidSeriesIdOriginalStart<br />**Hex**:<br />8004E109<br />**Nummer**:<br />-2147163895|Ungültiges seriesid oder original Startdatum.|
> |**Name**:<br />InvalidSeriesStatus<br />**Hex**:<br />8004E10F<br />**Nummer**:<br />-2147163889|Ungültiger Serienstatus.|
> |**Name**:<br />InvalidSharee<br />**Hex**:<br />8004020c<br />**Nummer**:<br />-2147220980|Ungültige Freigabe-ID.|
> |**Name**:<br />InvalidSharePointSiteCollectionUrl<br />**Hex**:<br />80048052<br />**Nummer**:<br />-2147188654|Die URL muss dem Schema "http" oder "https" entsprechen.|
> |**Name**:<br />InvalidSimilarityRuleStateError<br />**Hex**:<br />80044254<br />**Nummer**:<br />-2147204524|Ungültiger Ähnlichkeitsregelstatus.|
> |**Name**:<br />InvalidSingletonResults<br />**Hex**:<br />8004024f<br />**Nummer**:<br />-2147220913|Interne CRM-Ausnahme: Singleton-Abrufabfrage sollte nicht mehr als 1 Datensatz zurückgeben.|
> |**Name**:<br />InvalidSiteRelativeUrlFormat<br />**Hex**:<br />80048053<br />**Nummer**:<br />-2147188653|Die relative URL enthält ungültige Zeichen. Verwenden Sie einen anderen Namen. Eine relative URL darf nicht auf ASPX, ASHX, ASMX und SVC enden und darf weder mit einem Punkt oder Schrägstrich (/) beginnen noch auf einen Punkt (.) oder Schrägstrich (/) enden. Sie darf keines der folgenden Zeichen enthalten: ~ " # % & * : < > ? \ { | }.|
> |**Name**:<br />InvalidSolutionAwarenessDeclaration<br />**Hex**:<br />80072000<br />**Nummer**:<br />-2147016704|Eine Entität kann bei einem Update-Vorgang nicht als lösungsfähig deklariert werden. Entität: {0}|
> |**Name**:<br />InvalidSolutionConfigurationPage<br />**Hex**:<br />8004701B<br />**Nummer**:<br />-2147192805|Die angegebene Konfigurationsseite für diese Lösung ist ungültig.|
> |**Name**:<br />InvalidSolutionUniqueName<br />**Hex**:<br />8004F002<br />**Nummer**:<br />-2147160062|Ungültiges Zeichen für eindeutigen Name der Lösung angegeben. Nur Zeichen innerhalb von Bereichen [ A-Z], [a-z], [0-9] oder _ sind zulässig. Das erste Zeichen darf nur in den Bereichen [A-Z], [a-z] oder _ sein.|
> |**Name**:<br />InvalidSolutionVersion<br />**Hex**:<br />8004F01E<br />**Nummer**:<br />-2147160034|Eine ungültige Lösungsversion wurde angegeben.|
> |**Name**:<br />InvalidSourceAttributeType<br />**Hex**:<br />80044808<br />**Nummer**:<br />-2147203064|Quellattribut-Typ entspricht nicht dem Datentyp-Betrag.|
> |**Name**:<br />InvalidSourceEntityAttribute<br />**Hex**:<br />80044806<br />**Nummer**:<br />-2147203066|Attribut {0} ist kein Attribut der Entität {1}.|
> |**Name**:<br />InvalidSourceStateValue<br />**Hex**:<br />80044810<br />**Nummer**:<br />-2147203056|Der Quellstatus, der für die Entität angezeigt wird, ist ungültig.|
> |**Name**:<br />InvalidSourceStatusValue<br />**Hex**:<br />80044811<br />**Nummer**:<br />-2147203055|Der Quellstatus, der für die Entität angezeigt wird, ist ungültig.|
> |**Name**:<br />InvalidSourceType<br />**Hex**:<br />80060437<br />**Nummer**:<br />-2147089353|Datenquellentyp {0} ist für den Datentyp {1} nicht gültig.|
> |**Name**:<br />InvalidSourceTypeCode<br />**Hex**:<br />800608EA<br />**Nummer**:<br />-2147088150|Wählen Sie gültige Eigenschaftenbehälter für den ausgewählten Quelltyp aus.|
> |**Name**:<br />InvalidStage<br />**Hex**:<br />80060452<br />**Nummer**:<br />-2147089326|Überprüfungsfehler: Ungültige Phase.|
> |**Name**:<br />InvalidStageTransition<br />**Hex**:<br />80092003<br />**Nummer**:<br />-2146885629|Ungültiger Phasenübergang. Übergang zur aktiven Phase {0} ist nicht im ProzessPfad.|
> |**Name**:<br />InvalidStageTransitionOnInactiveInstance<br />**Hex**:<br />80060377<br />**Nummer**:<br />-2147089545|Ungültiger Phasenübergang. Phasenübergang ist bei inaktiven Prozessen nicht erlaubt.|
> |**Name**:<br />InvalidState<br />**Hex**:<br />80040233<br />**Nummer**:<br />-2147220941|Das Objekt ist nicht in einem gültigen Status, um den Vorgang auszuführen.|
> |**Name**:<br />InvalidStateCodeStatusCode<br />**Hex**:<br />80048408<br />**Nummer**:<br />-2147187704|Der Zustandscode ist ungültig, oder der Zustandscode ist zwar gültig, jedoch ist der Statuscode für einen angegebenen Zustandscode ungültig.|
> |**Name**:<br />InvalidStateForPublish<br />**Hex**:<br />8004F90A<br />**Nummer**:<br />-2147157750|Die angegebene Produktfamilie, bzw. das Paket können nur vom status "oder" nur ActiveDraft-Status veröffentlicht werden|
> |**Name**:<br />InvalidStateTransition<br />**Hex**:<br />8004F00E<br />**Nummer**:<br />-2147160050|Die {0} (ID ={1}) Entität oder Komponente hat versucht, von einem ungültigen Status zu wechseln: {2}.|
> |**Name**:<br />InvalidSubmitFromPublishedArticle<br />**Hex**:<br />80048dfa<br />**Nummer**:<br />-2147185158|Sie versuchen, einen Artikel zu übermitteln, der den Status "veröffentlicht" hat. Sie können einen Artikel mit dem Status Entwurf nur übermitteln.|
> |**Name**:<br />InvalidSubmitFromUnapprovedArticle<br />**Hex**:<br />80048dff<br />**Nummer**:<br />-2147185153|Sie versuchen, einen Artikel zu übermitteln, der den Status "nicht genehmigt" hat. Sie können einen Artikel mit dem Status Entwurf nur übermitteln.|
> |**Name**:<br />InvalidSubstituteProduct<br />**Hex**:<br />80043aff<br />**Nummer**:<br />-2147206401|Ein Produkt kann keine Beziehung zu sich selbst haben.|
> |**Name**:<br />InvalidSyncDirectionValueForUpdate<br />**Hex**:<br />80060742<br />**Nummer**:<br />-2147088574|Die Synchronisierungsrichtung ist gemäß der zulässigen Synchronisierungsrichtung für mindestens eine  Attributzuordnung ungültig.|
> |**Name**:<br />InvalidTargetEntity<br />**Hex**:<br />80040369<br />**Nummer**:<br />-2147220631|Der angegebene Zieldatensatztyp ist nicht vorhanden.|
> |**Name**:<br />InvalidTargetEntityTypeForControl<br />**Hex**:<br />80060878<br />**Nummer**:<br />-2147088264|Für das Steuerelement {0} wurde kein Zielentitätstyp angegeben. Die Zielentität ist ein Pflichtfeld.|
> |**Name**:<br />InvalidTargetFrameworkVersion<br />**Hex**:<br />8004420b<br />**Nummer**:<br />-2147204597|Die Plug-In-Assembly zielt auf eine Version von .NET Framework ab, die nicht unterstützt wird.|
> |**Name**:<br />InvalidTaskFlow<br />**Hex**:<br />80060392<br />**Nummer**:<br />-2147089518|Der Aufgabenfluss ist ungültig.|
> |**Name**:<br />InvalidTemplate<br />**Hex**:<br />8004B010<br />**Nummer**:<br />-2147176432|Die Einladungs-E--Mail-Vorlage ist ungültig.|
> |**Name**:<br />InvalidTemplateContent<br />**Hex**:<br />800609B2<br />**Nummer**:<br />-2147087950|Der Vorlageninhalt ist ungültig.|
> |**Name**:<br />InvalidTemplateId<br />**Hex**:<br />80050019<br />**Nummer**:<br />-2147155943|Die ist keine gültige Vorlage.|
> |**Name**:<br />InvalidTenantIDValue<br />**Hex**:<br />8005E25B<br />**Nummer**:<br />-2147098021|Der Exchange Online-Mandanten-ID-Wert ist ungültig. Der Feldwert sollte eine Zeichenfolgen in der Struktur der GUID sein.|
> |**Name**:<br />InvalidThemeDeleteOperation<br />**Hex**:<br />800608D7<br />**Nummer**:<br />-2147088169|Sie können System- oder Standarddesigns nicht löschen.|
> |**Name**:<br />InvalidThemeId<br />**Hex**:<br />800608D4<br />**Nummer**:<br />-2147088172|Ungültige Design-ID.|
> |**Name**:<br />InvalidTimeZoneCode<br />**Hex**:<br />800608F7<br />**Nummer**:<br />-2147088137|Der angegebene Zeitzonen- {0} Code wird nicht erkannt. Geben Sie ein gültiger Zeitzonen-Codewert an.|
> |**Name**:<br />InvalidToken<br />**Hex**:<br />8004B061<br />**Nummer**:<br />-2147176351|Der Token ist ungültig.|
> |**Name**:<br />InvalidTotalDiscount<br />**Hex**:<br />800404f4<br />**Nummer**:<br />-2147220236|Der gesamte Rabatt ist ungültig|
> |**Name**:<br />InvalidTotalPrice<br />**Hex**:<br />800404f5<br />**Nummer**:<br />-2147220235|Der Gesamtpreis ist ungültig|
> |**Name**:<br />InvalidTransformationParameter<br />**Hex**:<br />80040389<br />**Nummer**:<br />-2147220599|Ein Parameter für die Transformation fehlt oder ist ungültig.|
> |**Name**:<br />InvalidTransformationParameterDataType<br />**Hex**:<br />80040380<br />**Nummer**:<br />-2147220608|Der Datentyp aus mindestens einem Transformationsparameter wird nicht unterstützt.|
> |**Name**:<br />InvalidTransformationParameterEmptyCollection<br />**Hex**:<br />80048511<br />**Nummer**:<br />-2147187439|Der Transformations-Parameterwert: {0} hat eine ungültige Länge: {1}. Die Parameterdauer kann keine leeren Sammlung sein.|
> |**Name**:<br />InvalidTransformationParameterMapping<br />**Hex**:<br />80040382<br />**Nummer**:<br />-2147220606|Die definierte Transformationsparameterzuordnung ist ungültig. Überprüfen Sie, ob das Zielattributname vorhanden ist.|
> |**Name**:<br />InvalidTransformationParameterMappings<br />**Hex**:<br />8004037c<br />**Nummer**:<br />-2147220612|Mindestens eine Transformationsparameterzuordnungen ist ungültig oder passt nicht auf die Transformationsparameterbeschreibung zu.|
> |**Name**:<br />InvalidTransformationParameterOutsideRange<br />**Hex**:<br />80048510<br />**Nummer**:<br />-2147187440|Der Transformations-Parameter: {0} hat eine ungültige Länge: {1}. Der Parameter ist außerhalb dem zulässigen Bereich: {2}. |
> |**Name**:<br />InvalidTransformationParameterOutsideRangeGeneric<br />**Hex**:<br />80048512<br />**Nummer**:<br />-2147187438|Mindestens ein Eingabetransformations-Parameterwert liegt außerhalb des zulässigen Bereichs: {0}.|
> |**Name**:<br />InvalidTransformationParametersGeneric<br />**Hex**:<br />80048507<br />**Nummer**:<br />-2147187449|Der Transformations-Parameter: {0} hat eine ungültige Länge: {1}. Der Parameter muss vom Typ sein: {2}.|
> |**Name**:<br />InvalidTransformationParameterString<br />**Hex**:<br />80048508<br />**Nummer**:<br />-2147187448|Der Transformations-Parameter: {0} hat eine ungültige Länge: {1}. Der Parameter muss eine Zeichenfolge sein, die nicht leer ist.|
> |**Name**:<br />InvalidTransformationParameterZeroToRange<br />**Hex**:<br />80048509<br />**Nummer**:<br />-2147187447|Der Transformations-Parameter: {0} hat eine ungültige Länge: {1}. Der Parameterwert muss kleiner als 0 und die Länge des Parameters 1 sein.|
> |**Name**:<br />InvalidTransformationType<br />**Hex**:<br />8004037a<br />**Nummer**:<br />-2147220614|Der angegebene Transformationstyp wird nicht unterstützt.|
> |**Name**:<br />InvalidTranslationsFile<br />**Hex**:<br />80044249<br />**Nummer**:<br />-2147204535|Die Übersetzungsdatei ist ungültig oder entspricht nicht dem erforderlichen Schema.|
> |**Name**:<br />InvalidTraversedPath<br />**Hex**:<br />80092007<br />**Nummer**:<br />-2146885625|Ungültiger zurückgelegter Pfad.|
> |**Name**:<br />InvalidUniqueName<br />**Hex**:<br />80060386<br />**Nummer**:<br />-2147089530|Der eindeutige Name für die Aktion ist ungültig.|
> |**Name**:<br />InvalidUnpublishFromDraftArticle<br />**Hex**:<br />80048dfc<br />**Nummer**:<br />-2147185156|Sie versuchen, einen Artikel von der Veröffentlichung zurückzunehmen, der den Status "Entwurf" hat. Sie können einen Artikel mit dem Status nicht veröffentlicht nur von der Veröffentlichung zurückziehen.|
> |**Name**:<br />InvalidUnpublishFromUnapprovedArticle<br />**Hex**:<br />80048dfe<br />**Nummer**:<br />-2147185154|Sie versuchen, einen Artikel nicht weiter zu veröffentlichen, der den Status "nicht genehmigt" hat. Sie können einen Artikel mit dem Status nicht veröffentlicht nur veröffentlichen.|
> |**Name**:<br />InvalidUpdateOnProtectedComponent<br />**Hex**:<br />8004F012<br />**Nummer**:<br />-2147160046|Das Objekt kann nicht {0}{1} aktualisiert werden. Aktualisierung kann ausgeführt werden, falls {0} verwaltet wird.|
> |**Name**:<br />InvalidUrlConsecutiveSlashes<br />**Hex**:<br />80048056<br />**Nummer**:<br />-2147188650|Die URL enthält Schrägstriche, die darauf folgen, die nicht zulässig sind.|
> |**Name**:<br />InvalidUrlProtocol<br />**Hex**:<br />8004E30F<br />**Nummer**:<br />-2147163377|Die angegebene URL ist ungültig.|
> |**Name**:<br />InvalidUserAuth<br />**Hex**:<br />80040204<br />**Nummer**:<br />-2147220988|Der Benutzer ist nicht berechtigt, diese Aktion durchzuführen.|
> |**Name**:<br />InvalidUserLicenseCount<br />**Hex**:<br />8004B027<br />**Nummer**:<br />-2147176409|Kann {0} Benutzerlizenzen für das Angebot {1} nicht erwerben.|
> |**Name**:<br />InvalidUserName<br />**Hex**:<br />80048095<br />**Nummer**:<br />-2147188587|Geben Sie den Benutzernamen im Format <name>@<domain>. Korrigieren Sie das Format und versuchen Sie es erneut.|
> |**Name**:<br />InvalidUserQuota<br />**Hex**:<br />8004B011<br />**Nummer**:<br />-2147176431|Die maximale Anzahl von Benutzervorgaben wurde erreicht.|
> |**Name**:<br />InvalidUserToImportExcelOnlineFile<br />**Hex**:<br />80060807<br />**Nummer**:<br />-2147088377|Sie besitzen keine Berechtigung, um diese Datei zu importieren. Nur der Benutzer, der die Daten exportiert, kann die Datei importieren.|
> |**Name**:<br />InvalidUserToViewExcelOnlineFile<br />**Hex**:<br />80060806<br />**Nummer**:<br />-2147088378|Sie besitzen keine Berechtigung zum Anzeigen dieser Datei. Nur der Benutzer, der die Daten exportiert, kann die Datei anzeigen.|
> |**Name**:<br />InvalidValueForCountryCode<br />**Hex**:<br />8004B022<br />**Nummer**:<br />-2147176414|Firmen-Landes-/Regionscode darf nicht {0} sein|
> |**Name**:<br />InvalidValueForCurrency<br />**Hex**:<br />8004B023<br />**Nummer**:<br />-2147176413|Firmen-Währungscode darf nicht {0} sein|
> |**Name**:<br />InvalidValueForDataDelimiter<br />**Hex**:<br />80040341<br />**Nummer**:<br />-2147220671|Ungültiges Datentrennzeichen.|
> |**Name**:<br />InvalidValueForFieldDelimiter<br />**Hex**:<br />80040340<br />**Nummer**:<br />-2147220672|Ungültiges Feldtrennzeichen.|
> |**Name**:<br />InvalidValueForFileType<br />**Hex**:<br />80040348<br />**Nummer**:<br />-2147220664|Der Dateityp ist ungültig.|
> |**Name**:<br />InvalidValueForLocale<br />**Hex**:<br />8004B024<br />**Nummer**:<br />-2147176412|Firmen-Gebietsschemacode darf nicht {0} sein|
> |**Name**:<br />InvalidValueProcessEmailAfter<br />**Hex**:<br />8005E244<br />**Nummer**:<br />-2147098044|Das Datum im Feld der ProzesseE-Mail ist niedriger als es in Ihrer Organisation zulässig ist. Geben Sie ein Datum ein, das später als das angegebene liegt, und versuchen Sie es erneut.|
> |**Name**:<br />InvalidVersion<br />**Hex**:<br />8004023c<br />**Nummer**:<br />-2147220932|Es wurde ein nicht verarbeiteter Versionskonflikt gefunden.|
> |**Name**:<br />InvalidViewReference<br />**Hex**:<br />800609B3<br />**Nummer**:<br />-2147087949|Die Ansicht wird ncht angegeben oder ist ungültig.|
> |**Name**:<br />InvalidWebResourceForVisualization<br />**Hex**:<br />8004E017<br />**Nummer**:<br />-2147164137|Webressourcetyp {0} wird für Visualisierungen nicht unterstützt.|
> |**Name**:<br />InvalidWebresourceId<br />**Hex**:<br />8005012B<br />**Nummer**:<br />-2147155669|Die Webressourcen-ID ist ungültig.|
> |**Name**:<br />InvalidWebresourceType<br />**Hex**:<br />8005012D<br />**Nummer**:<br />-2147155667|Die für das App-Symbol bereitgestellte Webressource ist ungültig.|
> |**Name**:<br />InvalidWebToLeadRedirect<br />**Hex**:<br />80048476<br />**Nummer**:<br />-2147187594|Das redirectto ist für web2lead-Umleitung ungültig.|
> |**Name**:<br />InvalidWelcomePageId<br />**Hex**:<br />8005012C<br />**Nummer**:<br />-2147155668|Die ID der Begrüßungsseite ist ungültig.|
> |**Name**:<br />InvalidWelcomePageType<br />**Hex**:<br />8005012E<br />**Nummer**:<br />-2147155666|Die für die App-Begrüßungsseite bereitgestellte Webressource ist ungültig.|
> |**Name**:<br />InvalidWordDocumentTemplate<br />**Hex**:<br />800608EF<br />**Nummer**:<br />-2147088145|Die Dokumentvorlage ist ungültig.|
> |**Name**:<br />InvalidWordFileType<br />**Hex**:<br />800608EE<br />**Nummer**:<br />-2147088146|Der Dateityp wird nicht unterstützt.|
> |**Name**:<br />InvalidWordTemplateContent<br />**Hex**:<br />800608FB<br />**Nummer**:<br />-2147088133|Der Vorlageninhalt ist ungültig.|
> |**Name**:<br />InvalidWordXmlFile<br />**Hex**:<br />80048441<br />**Nummer**:<br />-2147187647|Nur Microsoft Word xml-Formatdateien können hochgeladen werden.|
> |**Name**:<br />InvalidWorkflowOrWorkflowDoesNotExist<br />**Hex**:<br />8006040a<br />**Nummer**:<br />-2147089398|Ungültiger Workflow oder Workflow ist nicht vorhanden.|
> |**Name**:<br />InvalidXaml<br />**Hex**:<br />80060417<br />**Nummer**:<br />-2147089385|XAML für Workflows ist nicht null oder leer|
> |**Name**:<br />InvalidXml<br />**Hex**:<br />80040201<br />**Nummer**:<br />-2147220991|Ungültiger XML-Code.|
> |**Name**:<br />InvalidXmlCollectionNameException<br />**Hex**:<br />80040247<br />**Nummer**:<br />-2147220921|Ungültiger XML-Sammlungsname.|
> |**Name**:<br />InvalidXmlEntityNameException<br />**Hex**:<br />80040248<br />**Nummer**:<br />-2147220920|Ungültiger XML-Entitätsname.|
> |**Name**:<br />InvalidXmlForParameters<br />**Hex**:<br />80060410<br />**Nummer**:<br />-2147089392|Parameterknoten für ControlStep haben ungültiges XML-Datei darin|
> |**Name**:<br />InvalidXmlSSContent<br />**Hex**:<br />80040350<br />**Nummer**:<br />-2147220656|Eine Datendatei kann nicht importiert werden, da sie ungültige Entitätsdaten enthält, oder sie in einem fehlerhaften Format ist. Stellen Sie sicher, dass die Datei, die richtigen Daten enthält, und dass das XML Spreadsheet 2003-Format hat, und versuchen Sie dann, sie erneut hochzuladen.|
> |**Name**:<br />InvalidXrmSdkReference<br />**Hex**:<br />8004419b<br />**Nummer**:<br />-2147204709|Die Plug-In-Assembly verweist auf eine Version von Microsoft.Xrm.Sdk, die höher als die Serverversion ist|
> |**Name**:<br />InvalidZipFileForImport<br />**Hex**:<br />80048482<br />**Nummer**:<br />-2147187582|Die ausgewählte komprimierte Datei (ZIP-Datei) enthält Dateien, die nicht importiert werden können. Eine ZIP-Datei kann nur XLSX, CSV oder XML-Dateien enthalten.|
> |**Name**:<br />InvalidZipFileFormat<br />**Hex**:<br />80048488<br />**Nummer**:<br />-2147187576|Die hochzuladende Datei ist ungültig. Überprüfen Sie die Datei und versuchen Sie es erneut.|
> |**Name**:<br />InvitationBillingAdminUnknown<br />**Hex**:<br />8004D213<br />**Nummer**:<br />-2147167725|Sie sind kein Fakturierungsadministrator für diese Organisation und können keine Einladungen senden.  Sie können entweder den Abrechnungsadministrator kontaktieren und sie bitten, die Einladung zu senden, und Abrechnungsadministrator kann https://billing.microsoft.com besuchen. Sie können dann Einladungen senden.|
> |**Name**:<br />InvitationCannotBeReset<br />**Hex**:<br />8004D210<br />**Nummer**:<br />-2147167728|Der Einladungsstatus für diesen Benutzer kann nicht zurückgesetzt werden.|
> |**Name**:<br />InvitationIsAccepted<br />**Hex**:<br />8004D208<br />**Nummer**:<br />-2147167736|{0} -- Einladung wurde bereits angenommen -- Token={1} Puid={2} "{3} Status={4}|
> |**Name**:<br />InvitationIsExpired<br />**Hex**:<br />8004D207<br />**Nummer**:<br />-2147167737|{0} -- Einladung ist abgelaufen -- Token={1} Puid={2} "{3} Status={4}|
> |**Name**:<br />InvitationIsRejected<br />**Hex**:<br />8004D209<br />**Nummer**:<br />-2147167735|{0} -- Einladung wurde vom neuen Benutzer bereits abgelehnt -- Token={1} Puid={2} "{3} Status={4}|
> |**Name**:<br />InvitationIsRevoked<br />**Hex**:<br />8004D20A<br />**Nummer**:<br />-2147167734|{0} -- Einladung wurde von der Organisation bereits zurückgerufen -- Token={1} Puid={2} "{3} Status={4}|
> |**Name**:<br />InvitationNotFound<br />**Hex**:<br />8004D204<br />**Nummer**:<br />-2147167740|{0} - Die Einladung wurde nicht gefunden oder der Status ist nicht "geöffnet" -- Token={1} Puid={2} "{3} Status={4}|
> |**Name**:<br />InvitationOrganizationNotEnabled<br />**Hex**:<br />8004D217<br />**Nummer**:<br />-2147167721|Die Organisation für die Einladung ist nicht aktiviert.|
> |**Name**:<br />InvitationSendToSelf<br />**Hex**:<br />8004D20F<br />**Nummer**:<br />-2147167729|Die Einladung kann an Sie selber nicht gesandt werden.|
> |**Name**:<br />InvitationStatusError<br />**Hex**:<br />8004D20C<br />**Nummer**:<br />-2147167732|"Die Einladung hat den Status {0}."|
> |**Name**:<br />InvitationWrongUserOrgRelation<br />**Hex**:<br />8004D206<br />**Nummer**:<br />-2147167738|{0} -- Die vorab erstellte userorg-Beziehung {1} ist ungültig.  Authentifizierung {2} wird bereits von anderen Benutzern verwendet|
> |**Name**:<br />InvitedUserAlreadyAdded<br />**Hex**:<br />8004D205<br />**Nummer**:<br />-2147167739|{0} -- Der CRM-Benutzer {1} ist bereits hinzugefügt, aber der Organisation {2} anstelle der einladenden Organisation {3}|
> |**Name**:<br />InvitedUserAlreadyExists<br />**Hex**:<br />8004D202<br />**Nummer**:<br />-2147167742|{0} -- Der eingeladene Benutzer befindet sich bereits in einer Organisation -- {1}|
> |**Name**:<br />InvitedUserIsOrganization<br />**Hex**:<br />8004D203<br />**Nummer**:<br />-2147167741|{0} -- Der Benutzer {1} hat Authentifizierung {2} und wurde bereits der Organisation {3} mit Beziehungs-ID {4} verknüpft|
> |**Name**:<br />InvitedUserMultipleTimes<br />**Hex**:<br />8004D20B<br />**Nummer**:<br />-2147167733|Der Dynamics 365-Benutzer {0} ist mehrmals eingeladen worden.|
> |**Name**:<br />InvitingOrganizationNotFound<br />**Hex**:<br />8004D200<br />**Nummer**:<br />-2147167744|{0} -- Einladende Organisation wurde nicht gefunden -- {1}|
> |**Name**:<br />InvitingUserNotInOrganization<br />**Hex**:<br />8004D201<br />**Nummer**:<br />-2147167743|{0} -- Einladender Benutzer ist nicht in der einladenden Organisation -- {1}|
> |**Name**:<br />IsKitCannotBeNull<br />**Hex**:<br />80044158<br />**Nummer**:<br />-2147204776|Attribut "iskit" darf nicht den Wert null haben|
> |**Name**:<br />IsNotLiveToSendInvitation<br />**Hex**:<br />8004B009<br />**Nummer**:<br />-2147176439|Die Funktionalität ist nicht unterstützt und nur für Online-Lösung unterstützt.|
> |**Name**:<br />IsvAborted<br />**Hex**:<br />80040265<br />**Nummer**:<br />-2147220891|Der Vorgang wurde vom ISV-Code abgebrochen.|
> |**Name**:<br />IsvExtensionsPrivilegeNotPresent<br />**Hex**:<br />80048029<br />**Nummer**:<br />-2147188695|Zum Importieren von 'ISV.Config' muss Ihrem Benutzerkonto eine Sicherheitsrolle zugeordnet sein, die das Recht 'ISV-Erweiterungen' beinhaltet.|
> |**Name**:<br />IsvUnExpected<br />**Hex**:<br />80040224<br />**Nummer**:<br />-2147220956|Unerwarteter Fehler im ISV-Code.|
> |**Name**:<br />JobNameIsEmptyOrNull<br />**Hex**:<br />80048457<br />**Nummer**:<br />-2147187625|Auftragsname darf nicht NULL oder leer sein.|
> |**Name**:<br />KBInvalidCreateAssociation<br />**Hex**:<br />80060861<br />**Nummer**:<br />-2147088287|Dieser Wissensdatenbankartikel ist bereits mit Folgendem verknüpft: {0}.|
> |**Name**:<br />KnowledgeSearchActiveModelsAlreadyExist<br />**Hex**:<br />80061680<br />**Nummer**:<br />-2147084672|Eine aktive Konfiguration ist bereits für Quellentität {0} vorhanden. Nur eine aktive Konfiguration ist pro Quellentität zugelassen.|
> |**Name**:<br />LabelIdDoesNotMatchStepId<br />**Hex**:<br />80060419<br />**Nummer**:<br />-2147089383|Die Beschriftung ID {0} entspricht nicht dem Schritt ID {1}.|
> |**Name**:<br />LanguageProvisioningSrsDataConnectorNotInstalled<br />**Hex**:<br />8004F710<br />**Nummer**:<br />-2147158256|Die Microsoft Dynamics 365 Reporting Extensions müssen installiert werden, bevor die Sprache für die Organisation bereitgestellt werden kann.|
> |**Name**:<br />LeadAlreadyInClosedState<br />**Hex**:<br />80040519<br />**Nummer**:<br />-2147220199|Der Lead ist bereits geschlossen.|
> |**Name**:<br />LeadAlreadyInOpenState<br />**Hex**:<br />80040518<br />**Nummer**:<br />-2147220200|Der Lead ist bereits in geöffnetem Status.|
> |**Name**:<br />LegacyXlsxFileNotSupported<br />**Hex**:<br />800608CF<br />**Nummer**:<br />-2147088177|Veraltete XLSX-Dateien können nicht für Excel-Vorlagen verwendet werden.|
> |**Name**:<br />LicenseConfigFileInvalid<br />**Hex**:<br />8004D250<br />**Nummer**:<br />-2147167664|Die bereitgestellte Konfigurationsdatei {0} enthält ungültige Formatierung.|
> |**Name**:<br />LicenseNotEnoughToActivate<br />**Hex**:<br />80042f14<br />**Nummer**:<br />-2147209452|Es gibt nicht genügend Lizenzen, die für die Anzahl von Benutzern zur Verfügung stehen, die aktiviert werden.|
> |**Name**:<br />LicenseRegistrationExpired<br />**Hex**:<br />8004415d<br />**Nummer**:<br />-2147204771|Der Registrierungszeitraum für Microsoft Dynamics 365 ist abgelaufen.|
> |**Name**:<br />LicenseTampered<br />**Hex**:<br />8004415f<br />**Nummer**:<br />-2147204769|Die Lizenzierung für die Installation von Microsoft Dynamics 365 wurde manipuliert. Das System ist nicht verfügbar. Wenden Sie sich an den Microsoft-Produktsupport.|
> |**Name**:<br />LicenseTrialExpired<br />**Hex**:<br />8004415c<br />**Nummer**:<br />-2147204772|Die Probeinstallation von Microsoft Dynamics 365 ist abgelaufen.|
> |**Name**:<br />LicenseUpgradePathNotAllowed<br />**Hex**:<br />8004D247<br />**Nummer**:<br />-2147167673|Kann nicht zum angegebenen Lizenztyp aktualisieren.|
> |**Name**:<br />LinkedEntitiesAreNotAllowed<br />**Hex**:<br />80071120<br />**Nummer**:<br />-2147020512|Verknüpfte Entitäten sind in dem Filter nicht zulässig|
> |**Name**:<br />LiveAdminUnknownCommand<br />**Hex**:<br />8004D239<br />**Nummer**:<br />-2147167687|Unbekannter Administrationsbefehl {0}|
> |**Name**:<br />LiveAdminUnknownObject<br />**Hex**:<br />8004D238<br />**Nummer**:<br />-2147167688|Unbekanntes Administrationsziel {0}|
> |**Name**:<br />LivePlatformEmailInvalidBody<br />**Hex**:<br />8004B524<br />**Nummer**:<br />-2147175132|Der "Text" Parameter ist leer oder ungültig|
> |**Name**:<br />LivePlatformEmailInvalidFrom<br />**Hex**:<br />8004B522<br />**Nummer**:<br />-2147175134|Der "Von" Parameter ist leer oder ungültig|
> |**Name**:<br />LivePlatformEmailInvalidSubject<br />**Hex**:<br />8004B523<br />**Nummer**:<br />-2147175133|Der "Betreff" Parameter ist leer oder ungültig|
> |**Name**:<br />LivePlatformEmailInvalidTo<br />**Hex**:<br />8004B521<br />**Nummer**:<br />-2147175135|Der "Zu" Parameter ist leer oder ungültig|
> |**Name**:<br />LivePlatformGeneralEmailError<br />**Hex**:<br />8005B520<br />**Nummer**:<br />-2147109600|Ein E-Mail-Fehler ist aufgetreten|
> |**Name**:<br />LocalDataSourceAbortError<br />**Hex**:<br />80072453<br />**Nummer**:<br />-2147015597|Der Browservorgang wurde beendet. Bitte wiederholen Sie den Vorgang.|
> |**Name**:<br />LocalDataSourceDatabaseError<br />**Hex**:<br />80072455<br />**Nummer**:<br />-2147015595|Der Browservorgang ist aufgrund von Browserdatenbankfehlern fehlgeschlagen. Bitte wiederholen Sie den Vorgang. Falls dies nicht funktioniert, versuchen Sie denselben Vorgang erneut, indem Sie sicherstellen, dass Ihr Gerät entsperrt bleibt, bis der Vorgang abgeschlossen ist.|
> |**Name**:<br />LocalDataSourceError<br />**Hex**:<br />80072451<br />**Nummer**:<br />-2147015599|Der Vorgang ist fehlgeschlagen. Bitte wiederholen Sie den Vorgang.|
> |**Name**:<br />LocalDataSourceQuotaExceededError<br />**Hex**:<br />80072452<br />**Nummer**:<br />-2147015598|Der Vorgang ist fehlgeschlagen, weil nicht genügend Speicherplatz in der Browserspeichervorgabe vorhanden war oder weil die Browserspeichervorgabe erreicht wurde, und der Benutzer es abgelehnt hat, mehr Speicherplatz in der Browserdatenbank bereitzustellen.|
> |**Name**:<br />LocalDataSourceTimeOutError<br />**Hex**:<br />80072454<br />**Nummer**:<br />-2147015596|Bei dem Vorgang ist ein Timeout aufgetreten. Bitte versuchen Sie es noch einmal.|
> |**Name**:<br />LockStatusNotValidForDynamicList<br />**Hex**:<br />8004F703<br />**Nummer**:<br />-2147158269|Sperrstatus kann für eine dynamische Liste nicht angegeben werden.|
> |**Name**:<br />LogoImageNodeDoesNotExist<br />**Hex**:<br />800608D2<br />**Nummer**:<br />-2147088174|Der Logobildknoten in den Organisationscache-Designdaten ist nicht vorhanden.|
> |**Name**:<br />LongParseRow<br />**Hex**:<br />80040372<br />**Nummer**:<br />-2147220622|Die Zeile ist zu lang für einen Importvorgang.|
> |**Name**:<br />LookupNotFound<br />**Hex**:<br />80040353<br />**Nummer**:<br />-2147220653|Der Suchverweis konnte nicht aufgelöst werden.|
> |**Name**:<br />LowerVersionUpgrade<br />**Hex**:<br />80048541<br />**Nummer**:<br />-2147187391|Die Importlösung muss eine höhere Version sein als die bestehende Lösung, die aktualisiert wird.|
> |**Name**:<br />LowQuantityGreaterThanHighQuantity<br />**Hex**:<br />80043b01<br />**Nummer**:<br />-2147206399|Die niedrige Menge sollte weniger als die hohe Menge sein.|
> |**Name**:<br />LowQuantityLessThanZero<br />**Hex**:<br />80043b00<br />**Nummer**:<br />-2147206400|Niedrige Menge sollte größer als null sein.|
> |**Name**:<br />MailApp_AppointmentFeatureNotEnabled<br />**Hex**:<br />80061218<br />**Nummer**:<br />-2147085800|Zugriff auf die App wurde für Termine bei dieser Microsoft Dynamics 365-Organisation nicht aktiviert. Wenden Sie sich an Ihren Systemadministrator, um Zugriff auf Termine zu aktivieren.|
> |**Name**:<br />MailApp_DifferentSecurityZoneError<br />**Hex**:<br />80061210<br />**Nummer**:<br />-2147085808|Versuchen Sie, die folgenden URLs zu den vertrauenswürdigen Sites hinzufügen:{0} {1} {2}|
> |**Name**:<br />MailApp_EmailAddressMismatch<br />**Hex**:<br />80061211<br />**Nummer**:<br />-2147085807|Anscheinend versuchen Sie über eine E-Mail-Adresse auf die CRM-App für Outlook zuzugreifen, die wir nicht erkennen. Entweder melden Sie sich mit der E-Mail-Adresse an und ab, die Sie für Dynamics CRM verwenden, oder Sie bitten den Systemadministrator, Ihre E-Mail-Postfacheinstellungen zu aktualisieren, sodass diese E-Mail-Adresse berücksichtigt wird.|
> |**Name**:<br />MailApp_FeatureControlBitDisabled<br />**Hex**:<br />80061204<br />**Nummer**:<br />-2147085820|Zugriff auf die App wurde bei dieser Dynamics 365-Organisation nicht aktiviert. Wenden Sie sich an Ihren Systemadministrator, um Zugriff auf diese App zu aktivieren.|
> |**Name**:<br />MailApp_MailboxNotConfiguredWithServerSideSync<br />**Hex**:<br />80061202<br />**Nummer**:<br />-2147085822|E-Mail-Konto wird mit serverseitiger Synchronisierung für eingehende E-Mails konfiguriert|
> |**Name**:<br />MailApp_MailboxNotConfiguredWithServerSideSyncForACT<br />**Hex**:<br />80061217<br />**Nummer**:<br />-2147085801|E-Mail-Konto wird mit serverseitiger Synchronisierung für Termine, Kontakte und Aufgaben konfiguriert|
> |**Name**:<br />MailApp_MailboxServerSideSyncConfigurationFailure<br />**Hex**:<br />80061220<br />**Nummer**:<br />-2147085792|Die serverseitige Synchronisierung von Microsoft Dynamics 365 ist für eingehende E-Mails fehlgeschlagen.|
> |**Name**:<br />MailApp_MailboxServerSideSyncConfigurationFailureForACT<br />**Hex**:<br />80061221<br />**Nummer**:<br />-2147085791|Die serverseitige Synchronisierung von Microsoft Dynamics 365 ist für Termine fehlgeschlagen.|
> |**Name**:<br />MailApp_MobileBrowserIsNotSupported<br />**Hex**:<br />80061208<br />**Nummer**:<br />-2147085816|Die Version des Mobil-Setups Webbrowsers von Outlook wird derzeit nicht unterstützt. Versuchen Sie es noch einmal von der Outlook-Desktop-Anwendung.|
> |**Name**:<br />MailApp_PermissionsToReadContactRequired<br />**Hex**:<br />80061219<br />**Nummer**:<br />-2147085799|Es kann nicht überprüft werden, ob die Empfänger sich in Dynamics 365 befinden, da der Benutzer nicht über die erforderlichen Rechte verfügt.|
> |**Name**:<br />MailApp_PermissionToUseCrmForOfficeAppsRequired<br />**Hex**:<br />80061205<br />**Nummer**:<br />-2147085819|Der Benutzer hat nicht die Berechtigung, um auf diese App zuzugreifen|
> |**Name**:<br />MailApp_ReadWriteAccessRequired<br />**Hex**:<br />80061203<br />**Nummer**:<br />-2147085821|Der Benutzer hat nur Verwaltungszugriff auf Dynamics 365|
> |**Name**:<br />MailApp_TrackingIsNotSupported<br />**Hex**:<br />80061207<br />**Nummer**:<br />-2147085817|Diese Version von Outlook unterstützt das Nachverfolgen neuer E-Mails nicht.|
> |**Name**:<br />MailApp_UnsupportedBrowser<br />**Hex**:<br />80061201<br />**Nummer**:<br />-2147085823|Der Browser wird derzeit nicht unterstützt.|
> |**Name**:<br />MailApp_UnsupportedDevice<br />**Hex**:<br />80061200<br />**Nummer**:<br />-2147085824|Das Gerät wird derzeit nicht unterstützt.|
> |**Name**:<br />MailApp_UserMailboxInactive<br />**Hex**:<br />80061216<br />**Nummer**:<br />-2147085802|Das Postfach des Benutzers ist inaktiv|
> |**Name**:<br />MailAppLimitedMode<br />**Hex**:<br />80061222<br />**Nummer**:<br />-2147085790|Allgemeiner Fehler, wenn die serverseitige Synchronisierung nicht ordnungsgemäß konfiguriert wurde und MailApp darf nur im LimitedMode geladen werden|
> |**Name**:<br />MailboxCannotDeleteEmails<br />**Hex**:<br />8005E233<br />**Nummer**:<br />-2147098061|Die Löschungs-E-Mails, nachdem der Option verarbeitet hat, können nicht auf Ja für Benutzerpostfächer festgelegt werden.|
> |**Name**:<br />MailboxCannotModifyEmailAddress<br />**Hex**:<br />8005E208<br />**Nummer**:<br />-2147098104|Die E-Mail-Adresse eines Postfachs kann nicht aktualisiert werden, wenn sie einem Benutzer/einer Warteschlange zugeordnet ist.|
> |**Name**:<br />MailboxCredentialNotSpecified<br />**Hex**:<br />8005E209<br />**Nummer**:<br />-2147098103|Benutzername ist nicht angegeben|
> |**Name**:<br />MailboxTrackingFolderMappingCannotBeUpdated<br />**Hex**:<br />8006088C<br />**Nummer**:<br />-2147088244|Die Postfachnachverfolgungs-Ordnerzuordnung kann nicht aktualisiert werden.|
> |**Name**:<br />MailboxUnsupportedEmailServerType<br />**Hex**:<br />8005E247<br />**Nummer**:<br />-2147098041|Serverseitige Synchronisierung für Kontakte, Termine und Aufgaben wird nicht für POP3-/SMTP-Servertypen unterstützt. Wählen Sie einen unterstützten E-Mail-Typ aus oder Ändern Sie die Synchronisierungsmethode für Termine, Kontakte und Aufgaben in keine.|
> |**Name**:<br />ManagedBpfDeletionInvalid<br />**Hex**:<br />80060383<br />**Nummer**:<br />-2147089533| Der Geschäftsprozessfluss ist Teil einer verwalteten Lösung und kann nicht einzeln gelöscht werden. Deinstallieren Sie die übergeordnete Lösung, um den Geschäftsprozessfluss zu entfernen.|
> |**Name**:<br />ManagedProcessDeletionError<br />**Hex**:<br />80072457<br />**Nummer**:<br />-2147015593|Der Prozess ist Teil einer verwalteten Lösung und kann nicht einzeln gelöscht werden. Deinstallieren Sie die übergeordnete Lösung, um den Prozess zu entfernen.|
> |**Name**:<br />ManifestParsingFailure<br />**Hex**:<br />80048534<br />**Nummer**:<br />-2147187404|Die angegebene Manifestdatei konnte nicht analysiert werden, um OrganizationId abzurufen|
> |**Name**:<br />ManifestXsdValidationError<br />**Hex**:<br />80160001<br />**Nummer**:<br />-2146041855|Ungültige Manifestdatei. XSD-Validierung schlug mit folgendem Fehler fehl: '{0}'."|
> |**Name**:<br />ManyToManyVirtualEntityNotSupported<br />**Hex**:<br />80044820<br />**Nummer**:<br />-2147203040|Eine n:n-Beziehung zwischen virtuellen Entitäten wird nicht unterstützt.|
> |**Name**:<br />MappingExistsForTargetAttribute<br />**Hex**:<br />8004033e<br />**Nummer**:<br />-2147220674|Dieses Attribut ist mehrmals zugeordnet. Entfernen Sie die mehrfachen Zuordnungen, und importieren Sie die Datenzuordnung anschließend erneut.|
> |**Name**:<br />MarsConnectorDisableFailure<br />**Hex**:<br />80071108<br />**Nummer**:<br />-2147020536|Fehler beim Deaktivieren des Mars-Connectors.|
> |**Name**:<br />MarsConnectorEnableFailure<br />**Hex**:<br />80071107<br />**Nummer**:<br />-2147020537|Fehler beim Aktivieren des Mars-Connectors.|
> |**Name**:<br />MatchingAttributeNameNotNullError<br />**Hex**:<br />80044243<br />**Nummer**:<br />-2147204541|Übereinstimmender Attributname darf keine einzelne Entitätsregel sein.|
> |**Name**:<br />MaxActiveSLAError<br />**Hex**:<br />8004F897<br />**Nummer**:<br />-2147157865|Sie können diese SLA nicht aktivieren, da sie die maximale Anzahl der Entitäten überschritten haben, die für Ihre Organisation aktive SLAs haben können.|
> |**Name**:<br />MaxActiveSLAKPIError<br />**Hex**:<br />8004F898<br />**Nummer**:<br />-2147157864|Sie können diese SLA nicht aktivieren, da sie die maximale Anzahl der für Ihre Organisation pro Entität zulässigen SLA-KPIs überschritten haben.|
> |**Name**:<br />MaxChildCasesLimitExceeded<br />**Hex**:<br />8003F454<br />**Nummer**:<br />-2147224492|Eine übergeordnete Anfrage kann nicht über mehr als die maximal zulässige Anzahl der untergeordneten Anfragen verfügen. Weitere Details hierzu erhalten Sie bei Ihrem Administrator.|
> |**Name**:<br />MaxConditionsMobileOfflineFilters<br />**Hex**:<br />80071114<br />**Nummer**:<br />-2147020524|Sie können nur drei Mobile Offline-Entitätsfilterbedingungen für jede Entität definieren.|
> |**Name**:<br />MaximumControlsLimitExceeded<br />**Hex**:<br />8004E301<br />**Nummer**:<br />-2147163391|Das Dashboard Formular XML enthält mehr als die maximal zulässige Höchstzahl von Steuerelementen: {0}.|
> |**Name**:<br />MaximumCountForUpdateModeExceeded<br />**Hex**:<br />8004F602<br />**Nummer**:<br />-2147158526|In einem Updatevorgang kann jeweils nur eine Datei importiert werden.|
> |**Name**:<br />MaximumNumberHandlersExceeded<br />**Hex**:<br />80048505<br />**Nummer**:<br />-2147187451|Mit dieser Lösung werden Ereignishandler für Formulare hinzugefügt, sodass die Anzahl der Ereignishandler für ein Formularereignis die maximale Anzahl übersteigt.|
> |**Name**:<br />MaximumNumberOfAttributesForEntityReached<br />**Hex**:<br />8004841A<br />**Nummer**:<br />-2147187686|Die maximale Anzahl von Attributen, die für eine Entität zugelassen sind, wird bereits erreicht. Das Attribut kann nicht erstellt werden.|
> |**Name**:<br />MaxLimitForRollupAttribute<br />**Hex**:<br />8004480a<br />**Nummer**:<br />-2147203062|Nur drei metrische Details pro Metrik können erstellt werden.|
> |**Name**:<br />MaxMatchCodeLengthExceeded<br />**Hex**:<br />80048429<br />**Nummer**:<br />-2147187671|Die Regelbedingung kann nicht erstellt oder aktualisiert werden, da sie die Länge des Matchcodes die Höchstgrenze der Speicherbegrenzung übersteigt.|
> |**Name**:<br />MaxProductsAllowed<br />**Hex**:<br />80071020<br />**Nummer**:<br />-2147020768|Sie können nicht mehrere Produkte als {0} erstellen.|
> |**Name**:<br />MaxprofileItemFilterConditionsAllowed<br />**Hex**:<br />80071116<br />**Nummer**:<br />-2147020522|Sie können nur sechs Mobile Offline-Entitätsfilterbedingungen für jede Entität definieren.|
> |**Name**:<br />MaxUnzipFolderSizeExceeded<br />**Hex**:<br />80048499<br />**Nummer**:<br />-2147187559|Die ausgewählte komprimierte Datei (.zip) kann nicht extrahiert werden, weil sie zu groß ist.|
> |**Name**:<br />MeasureDataTypeInvalid<br />**Hex**:<br />8004E010<br />**Nummer**:<br />-2147164144|Die Datenenbeschreibung für die Visualisierung ist ungültig. Der Attributtyp für eines der nicht gesamten Maße ist ungültig. Korrigieren Sie die Datenbeschreibung.|
> |**Name**:<br />MemberHasAlreadyBeenContacted<br />**Hex**:<br />8004140e<br />**Nummer**:<br />-2147216370|Dieses Mitglied der Marketingliste wurde nicht kontaktiert, da das Mitglied bereits zuvor diese Informationen erhalten hatte.|
> |**Name**:<br />MergeActiveQuoteError<br />**Hex**:<br />80045302<br />**Nummer**:<br />-2147200254|Die Zusammenführung kann nicht auf einer Unterentität mit einem aktiven Angebot ausgeführt werden.|
> |**Name**:<br />MergeCyclicalParentingError<br />**Hex**:<br />80045300<br />**Nummer**:<br />-2147200256|Die Zusammenführung kann zyklische Überordnung erstellen.|
> |**Name**:<br />MergeDifferentlyParentedWarning<br />**Hex**:<br />80045316<br />**Nummer**:<br />-2147200234|Zusammenführungswarnung: Überordnung der Unterentität ist unterschiedlich.|
> |**Name**:<br />MergeEntitiesIdenticalError<br />**Hex**:<br />80045305<br />**Nummer**:<br />-2147200251|Die Zusammenführung kann nicht bei Master- und Unterentitäten ausgeführt werden, die identisch sind.|
> |**Name**:<br />MergeEntityNotActiveError<br />**Hex**:<br />80045304<br />**Nummer**:<br />-2147200252|Die Zusammenführung kann nicht auf einer Entität ausgeführt werden, die deaktiviert ist.|
> |**Name**:<br />MergeLossOfParentingWarning<br />**Hex**:<br />80045317<br />**Nummer**:<br />-2147200233|Zusammenführungswarnung: Unterentität kann die Überordnung verlieren|
> |**Name**:<br />MergeSecurityError<br />**Hex**:<br />80045301<br />**Nummer**:<br />-2147200255|Die Zusammenführung ist nicht zulässig: Aufrufer hat das ausreichende Recht nicht oder keinen Zugriff.|
> |**Name**:<br />MetadataNoMapping<br />**Hex**:<br />80040e01<br />**Nummer**:<br />-2147217919|Die Zuordnung zwischen bestimmten Entitäten ist nicht vorhanden|
> |**Name**:<br />MetadataNotFound<br />**Hex**:<br />8004024a<br />**Nummer**:<br />-2147220918|Metadaten nicht gefunden.|
> |**Name**:<br />MetadataNotSerializable<br />**Hex**:<br />80040e03<br />**Nummer**:<br />-2147217917|Die bestimmte Metadatenentität sind nicht serialisierbar|
> |**Name**:<br />MetadataRecordNotDeletable<br />**Hex**:<br />80044250<br />**Nummer**:<br />-2147204528|Der Metadatendatensatz, der gelöscht wird, kann nicht gelöscht werden vom Endbenutzer|
> |**Name**:<br />MetadataSyncRequired<br />**Hex**:<br />80072510<br />**Nummer**:<br />-2147015408|Metadatensynchronisierung erforderlich|
> |**Name**:<br />MetricEntityOrFieldDeleted<br />**Hex**:<br />8004F687<br />**Nummer**:<br />-2147158393|Eine Entität oder ein Feld, auf den bzw. das in der Zielmetrik verwiesen wird, ist ungültig|
> |**Name**:<br />MetricNameAlreadyExists<br />**Hex**:<br />80044802<br />**Nummer**:<br />-2147203070|Eine Zielmetrik mit demselben Namen ist bereits vorhanden. Wählen Sie einen anderen Namen aus, und versuchen Sie es erneut.|
> |**Name**:<br />MinMaxValidationFailed<br />**Hex**:<br />80061004<br />**Nummer**:<br />-2147086332|Wert liegt außerhalb des gültigen Bereichs.|
> |**Name**:<br />MissingBOWFRules<br />**Hex**:<br />80040329<br />**Nummer**:<br />-2147220695|Auf Massenvorgang bezogene Workflowregeln fehlen.|
> |**Name**:<br />MissingBusinessId<br />**Hex**:<br />8004021a<br />**Nummer**:<br />-2147220966|Die Unternehmens-ID ist fehlend oder ungültig.|
> |**Name**:<br />MissingColumn<br />**Hex**:<br />8004B028<br />**Nummer**:<br />-2147176408|Der Eigenschaftsbehälter fehlt für einen Eintrag von {0}.|
> |**Name**:<br />MissingControlStep<br />**Hex**:<br />80060385<br />**Nummer**:<br />-2147089531|Der erforderliche Kontrollschritt fehlt.|
> |**Name**:<br />MissingCrmAuthenticationToken<br />**Hex**:<br />80044300<br />**Nummer**:<br />-2147204352|CrmAuthenticationToken fehlt.|
> |**Name**:<br />MissingCrmAuthenticationTokenOrganizationName<br />**Hex**:<br />80044308<br />**Nummer**:<br />-2147204344|Organisationsname muss in CrmAuthenticationToken angegeben werden.|
> |**Name**:<br />MissingHierarchicalRelationshipForOperator<br />**Hex**:<br />80047020<br />**Nummer**:<br />-2147192800|Diese Abfrage verwendet einen hierarchischen Oberator, aber die {0} Entität besitzt keine hierarchische Beziehung.|
> |**Name**:<br />MissingOpportunityId<br />**Hex**:<br />80043b15<br />**Nummer**:<br />-2147206379|Die Verkaufschancen-ID ist fehlend oder ungültig.|
> |**Name**:<br />MissingOrganizationFriendlyName<br />**Hex**:<br />8004B00A<br />**Nummer**:<br />-2147176438|Dynamics 365 kann nicht ohne eine Organisationsanzeigenamen installiert werden.|
> |**Name**:<br />MissingOrganizationUniqueName<br />**Hex**:<br />8004B00B<br />**Nummer**:<br />-2147176437|Dynamics 365 kann nicht ohne eine eindeutigen Organisationsnamen installiert werden.|
> |**Name**:<br />MissingOrInvalidRedirectId<br />**Hex**:<br />80048473<br />**Nummer**:<br />-2147187597|Der RedirId-Parameter fehlt für die Partnersumleitung.|
> |**Name**:<br />MissingOwner<br />**Hex**:<br />80040215<br />**Nummer**:<br />-2147220971|Element hat keinen Besitzer.|
> |**Name**:<br />MissingParameter<br />**Hex**:<br />8004031f<br />**Nummer**:<br />-2147220705|Ein erforderlicher Parameter für den Massenvorgang fehlt|
> |**Name**:<br />MissingParameterToMethod<br />**Hex**:<br />8004B021<br />**Nummer**:<br />-2147176415|Fehlender Parameter {0} bei Methode {1}|
> |**Name**:<br />MissingParameterToStoredProcedure<br />**Hex**:<br />8004C000<br />**Nummer**:<br />-2147172352|Fehlender Parameter bei gespeicherten Prozedur: {0}|
> |**Name**:<br />MissingPriceLevelId<br />**Hex**:<br />80043b12<br />**Nummer**:<br />-2147206382|Die Preisebenen-ID ist nicht vorhanden.|
> |**Name**:<br />MissingProductId<br />**Hex**:<br />80043b11<br />**Nummer**:<br />-2147206383|Die Produkt-ID ist nicht vorhanden.|
> |**Name**:<br />MissingQuantity<br />**Hex**:<br />80081012<br />**Nummer**:<br />-2146955246|Die Menge ist nicht vorhanden.|
> |**Name**:<br />MissingQueryType<br />**Hex**:<br />80040235<br />**Nummer**:<br />-2147220939|Die Abfrage-ID ist nicht vorhanden.|
> |**Name**:<br />MissingRecipient<br />**Hex**:<br />8004350d<br />**Nummer**:<br />-2147207923|Zum Senden des Faxes muss ein Empfänger festgelegt sein.|
> |**Name**:<br />MissingRequiredAttributes<br />**Hex**:<br />80061037<br />**Nummer**:<br />-2147086281|Die Eigenschaft konnte nicht erstellt werden oder aktualisiert werden, da regardingobjectid, Datentyp oder Namensattribut fehlen.|
> |**Name**:<br />MissingRequiredComponentAttributes<br />**Hex**:<br />80072002<br />**Nummer**:<br />-2147016702|Erforderliches Attribut darf nicht Null sein. Attribut: {0}|
> |**Name**:<br />MissingTeamName<br />**Hex**:<br />80041d0b<br />**Nummer**:<br />-2147214069|Der Teamname fehlt unerwartet.|
> |**Name**:<br />MissingUomId<br />**Hex**:<br />80043b0d<br />**Nummer**:<br />-2147206387|Die Einheits-ID ist nicht vorhanden.|
> |**Name**:<br />MissingUomScheduleId<br />**Hex**:<br />80043b0a<br />**Nummer**:<br />-2147206390|Die Einheitenzeitplan-ID ist nicht vorhanden.|
> |**Name**:<br />MissingUserId<br />**Hex**:<br />8004021b<br />**Nummer**:<br />-2147220965|Die Benutzer-ID oder die Team-ID ist fehlend oder ungültig.|
> |**Name**:<br />MissingWebToLeadRedirect<br />**Hex**:<br />80048477<br />**Nummer**:<br />-2147187593|Das redirectto ist für fehlende web2lead-Umleitung ungültig.|
> |**Name**:<br />MobileClientLanguageNotSupported<br />**Hex**:<br />8005F201<br />**Nummer**:<br />-2147094015|Die Anwendung kann keine unterstützte Sprache auf dem Server finden. Wenden Sie mit einem Administrator, um eine unterstützte Sprache zu aktivieren|
> |**Name**:<br />MobileClientNotConfiguredForCurrentUser<br />**Hex**:<br />8005F20E<br />**Nummer**:<br />-2147094002|Wiederholen Sie den Vorgang. Besteht das Problem weiterhin, überprüfen Sie {0} auf Lösungen, oder wenden Sie sich an den {#Brand_CRM}-Administrator in Ihrer Organisation. Schließlich können Sie {1} kontaktieren.|
> |**Name**:<br />MobileClientVersionNotSupported<br />**Hex**:<br />8005F202<br />**Nummer**:<br />-2147094014|Mobile Clientversion wird nicht unterstützt|
> |**Name**:<br />MobileExcelFeatureNotEnabled<br />**Hex**:<br />800608CA<br />**Nummer**:<br />-2147088182|Funktion zum mobilen Exportieren nach Excel ist nicht aktiviert.|
> |**Name**:<br />MobileOfflineDaysSinceRecordLastModifiedZero<br />**Hex**:<br />80060990<br />**Nummer**:<br />-2147087984|Im Mobile Offline-Modus sind keine Datensätze verfügbar, wenn der Wert der Anzahl der Tage 0 ist.|
> |**Name**:<br />MobileOfflineProfileItemNameAlreadyExists<br />**Hex**:<br />800609A8<br />**Nummer**:<br />-2147087960|Ein Mobile Offline-Profilelement mit diesem Namen ist für dieses Mobile Offline-Profil bereits vorhanden. Geben Sie einen eindeutigen Namen ein.|
> |**Name**:<br />MobileOfflineProfileItemNameCanNotBeNullOrEmpty<br />**Hex**:<br />800609AA<br />**Nummer**:<br />-2147087958|Der Mobile Offline Profilelementname kann nicht null oder leer sein. Geben Sie einen Namen für dieses Profilelement ein.|
> |**Name**:<br />MobileOfflineProfileNameAlreadyExists<br />**Hex**:<br />800609A7<br />**Nummer**:<br />-2147087961|Ein Mobile Offline-Profil mit diesem Namen ist bereits vorhanden. Geben Sie einen eindeutigen Namen ein.|
> |**Name**:<br />MobileOfflineProfileNameCanNotBeNullOrEmpty<br />**Hex**:<br />800609A9<br />**Nummer**:<br />-2147087959|Der Mobile Offline Profilelementname kann nicht null oder leer sein. Geben Sie einen Namen für dieses Profil ein.|
> |**Name**:<br />MobileOfflineRuleEnhancementFeatureNotAvailaible<br />**Hex**:<br />80071117<br />**Nummer**:<br />-2147020521|Dieses Funktion ist für Ihre Organisation nicht aktiviert. Wenden Sie sich an Ihren Systemadministrator.|
> |**Name**:<br />MobileServiceError<br />**Hex**:<br />8004B070<br />**Nummer**:<br />-2147176336|Fehler bei der Kommunikation mit Mobil-Service|
> |**Name**:<br />ModernFlowProcessesNotEnabled<br />**Hex**:<br />80060464<br />**Nummer**:<br />-2147089308|Die Erstellung moderner Flussprozesse ist nicht aktiviert.|
> |**Name**:<br />ModernFlowProcessesOnlyAvailableOnline<br />**Hex**:<br />80060465<br />**Nummer**:<br />-2147089307|Die Erstellung moderner Flussprozesse ist nur online verfügbar.|
> |**Name**:<br />MoneySizeExceeded<br />**Hex**:<br />80040317<br />**Nummer**:<br />-2147220713|Angegebener Wert hat den Mindest-/Höchstwert des Felds „Zahlungstyp” übertroffen.|
> |**Name**:<br />MOPIAssociationNameCannotBeEmptyOrSpace<br />**Hex**:<br />80060997<br />**Nummer**:<br />-2147087977|Der Name der Mobile Offline-Profilelementzuordnung darf weder ein Leerzeichen noch eine leere Zeichenfolge sein.|
> |**Name**:<br />MoveBothToPrimary<br />**Hex**:<br />8004D234<br />**Nummer**:<br />-2147167692|Mit dem Verschiebevorgang werden beide Instanzen auf denselben Server verschoben: Datenbank = {0}  Altes Primär = {1}  Altes Sekundär = {2}  Neues Sekundär = {3}|
> |**Name**:<br />MoveBothToSecondary<br />**Hex**:<br />8004D235<br />**Nummer**:<br />-2147167691|Mit dem Verschiebevorgang werden beide Instanzen auf denselben Server verschoben: Datenbank = {0}  Altes Primär = {1}  Altes Sekundär = {2}  Neues Sekundär = {3}|
> |**Name**:<br />MoveOrganizationFailedNotDisabled<br />**Hex**:<br />8004D236<br />**Nummer**:<br />-2147167690|Fehler bei Verschiebevorgang, da Organisation {0} nicht deaktiviert ist|
> |**Name**:<br />MultilevelParentChildRelationshipNotAllowed<br />**Hex**:<br />8003F453<br />**Nummer**:<br />-2147224493|Die Zuordnung von untergeordneten Anfragen zur vorhandenen untergeordneten Anfrage ist nicht zulässig.|
> |**Name**:<br />MultipleChartAreasFound<br />**Hex**:<br />8004E008<br />**Nummer**:<br />-2147164152|Mehrere Diagrammbereiche werden nicht unterstützt.|
> |**Name**:<br />MultipleChildPicklist<br />**Hex**:<br />80040250<br />**Nummer**:<br />-2147220912|Interne CRM-Ausnahme: Auswahllisten mit mehr als einem childAttribute werden nicht unterstützt.|
> |**Name**:<br />MultipleFilesFound<br />**Hex**:<br />80048439<br />**Nummer**:<br />-2147187655|Der Name der Anlagendatei ist nicht eindeutig.|
> |**Name**:<br />MultipleFormElementsFound<br />**Hex**:<br />8004E304<br />**Nummer**:<br />-2147163388|Ein Dashboard-Formular-XML kann nur ein Formularelement enthalten.|
> |**Name**:<br />MultipleLabelsInUserDashboard<br />**Hex**:<br />8004E30D<br />**Nummer**:<br />-2147163379|Ein Benutzerdashboard kann höchstens eine Beschriftung für ein Formularelement haben.|
> |**Name**:<br />MultipleMeasureCollectionsFound<br />**Hex**:<br />8004E01C<br />**Nummer**:<br />-2147164132|Mehr als eine Kennzahlsammlung wird für Diagramme mit Unterkategorie, z. B. Vergleichsdiagramme, nicht unterstützt.|
> |**Name**:<br />MultipleMeasuresFound<br />**Hex**:<br />8004E007<br />**Nummer**:<br />-2147164153|Mehr als ein Measure wird für Diagramme mit Unterkategorie, z. B. Vergleichsdiagramme, nicht unterstützt.|
> |**Name**:<br />MultipleOrganizationsNotAllowed<br />**Hex**:<br />80041d35<br />**Nummer**:<br />-2147214027|Nur eine Organisation und ein Stammunternehmen sind zulässig.|
> |**Name**:<br />MultipleParentReportsFound<br />**Hex**:<br />80040485<br />**Nummer**:<br />-2147220347|Mehrere Berichtslinks gefunden. Jeder Bericht kann nur ein übergeordnetes Element haben.|
> |**Name**:<br />MultipleParentsNotSupported<br />**Hex**:<br />80047007<br />**Nummer**:<br />-2147192825|Eine Entität kann nur über eine zugeordnete Beziehung verfügen.|
> |**Name**:<br />MultiplePartnerSecurityRoleWithSameInformation<br />**Hex**:<br />8004A10a<br />**Nummer**:<br />-2147180278|Mehrere Sicherheitsrollen für Partnerbenutzer gefunden|
> |**Name**:<br />MultiplePartnerUserWithSameInformation<br />**Hex**:<br />8004A10b<br />**Nummer**:<br />-2147180277|Mehrere Partnerbenutzer mit denselben Informationen gefunden|
> |**Name**:<br />MultipleQueueItemsFound<br />**Hex**:<br />80040525<br />**Nummer**:<br />-2147220187|Dieses Element tritt in mehreren Warteschlangen auf und kann nicht aus dieser Liste weitergeleitet werden. Suchen Sie das Element in einer Warteschlange, und versuchen Sie, das Element erneut weiterzuleiten.|
> |**Name**:<br />MultipleRecordsFoundByEntityKey<br />**Hex**:<br />8006089D<br />**Nummer**:<br />-2147088227|Mehr als ein Datensatz ist für die Entität {0} mit dem Entitätsschlüssel mit Attributen {1} vorhanden|
> |**Name**:<br />MultipleRelationshipsNotSupported<br />**Hex**:<br />80048200<br />**Nummer**:<br />-2147188224|Mehrerer Beziehungen werden nicht unterstützt|
> |**Name**:<br />MultipleRootBusinessUnit<br />**Hex**:<br />8004A10c<br />**Nummer**:<br />-2147180276|Mehrere Stammunternehmenseinheiten gefunden|
> |**Name**:<br />MultipleSitemapsFound<br />**Hex**:<br />80050120<br />**Nummer**:<br />-2147155680|{0} unveröffentlichte Siteübersichten gefunden, aber nur 1 erwartet|
> |**Name**:<br />MultipleSubcategoriesFound<br />**Hex**:<br />8004E006<br />**Nummer**:<br />-2147164154|Die Daten XML für die Visualisierung dürfen maximal zwei Gruppen B-Klauseln enthalten.|
> |**Name**:<br />MultiValueParameterFound<br />**Hex**:<br />8005E00A<br />**Nummer**:<br />-2147098614|Fetch-XML-Parameter {0} können nicht mehrere Werte abrufen. Ändern Sie den Berichtsparameter {0} auf einen Einzelwert und versuchen Sie es erneut.|
> |**Name**:<br />MustContainAtLeastACharInMention<br />**Hex**:<br />8004F6A4<br />**Nummer**:<br />-2147158364|Der Anzeigename muss mindestens ein Zeichen enthalten, das kein Leerzeichen ist.|
> |**Name**:<br />NavigationPropertyAlreadyExists<br />**Hex**:<br />80072551<br />**Nummer**:<br />-2147015343|NavigationPropertyName {0} ist in einer Entität nicht eindeutig|
> |**Name**:<br />NavigationPropertyNameCannotBeTheSameOnBothSidesOfRel<br />**Hex**:<br />80072550<br />**Nummer**:<br />-2147015344|Navigationseigenschaftsname kann nicht auf beiden Seiten einer auf sich selbst verweisenden Beziehung identisch sein. SchemaName – {0}|
> |**Name**:<br />NavPaneNotCustomizable<br />**Hex**:<br />80044329<br />**Nummer**:<br />-2147204311|Die nav Bereichseigenschaften für diese Beziehung können nicht angepasst werden|
> |**Name**:<br />NavPaneOrderValueNotAllowed<br />**Hex**:<br />80044327<br />**Nummer**:<br />-2147204313|Der bereitgestellte nav Bereich Auftragswert it nicht zulässig|
> |**Name**:<br />NetworkIssue<br />**Hex**:<br />8005F104<br />**Nummer**:<br />-2147094268|Die Anforderung ist wegen unbekannten Netzwerkproblemen oder Gateway-Problemen oder Serverproblemen fehlgeschlagen.|
> |**Name**:<br />NewStatusHasInvalidState<br />**Hex**:<br />80044322<br />**Nummer**:<br />-2147204318|Der Statuswert für diese neue Statusoption ist nicht vorhanden.|
> |**Name**:<br />NewStatusRequiresAssociatedState<br />**Hex**:<br />80044321<br />**Nummer**:<br />-2147204319|Die neue Statusoption muss einen Zustandswert zugeordneten haben.|
> |**Name**:<br />NoActiveLocation<br />**Hex**:<br />80060900<br />**Nummer**:<br />-2147088128|Kein aktives Dokument gefunden.|
> |**Name**:<br />NoAppModuleComponentReferred<br />**Hex**:<br />8005011B<br />**Nummer**:<br />-2147155685|Es wird auf keine Komponente verwiesen|
> |**Name**:<br />NoAttributesForEntityCreate<br />**Hex**:<br />80047014<br />**Nummer**:<br />-2147192812|Keine Attribute für die Aktion "Entität erstellen".|
> |**Name**:<br />NoConditionRuleCreationNotAllowedForSetValueShowError<br />**Hex**:<br />80060013<br />**Nummer**:<br />-2147090413|Die Aktionen "Fehlermeldung anzeigen" und "Wert festlegen" können in einer Geschäftsregel ohne Bedingung nicht verwendet werden.|
> |**Name**:<br />NoConnectionRoleAndObjectTypeCodePairPresent<br />**Hex**:<br />8004F222<br />**Nummer**:<br />-2147159518|Es sind keine ConnectionRoleId- und AssociatedObjectTypeCode-Paare vorhanden. Entitäten, die verknüpft sind: ({0},{1}); Entitätsdatensatz, der verknüpft ist: ({2},{3}); Record1ConnectionRoleName: {4}, Record2ConnectionRoleName: {5}. ConnectionRoleIds: {6}|
> |**Name**:<br />NoConversionRule<br />**Hex**:<br />800608F5<br />**Nummer**:<br />-2147088139|Eine ConversionRule ist zum Ausführen des Tools erforderlich.|
> |**Name**:<br />NoDataFilterSelectedForOtherDataFilter<br />**Hex**:<br />80071138<br />**Nummer**:<br />-2147020488|Die Entität „{0}“ im Profil „{1}“ hat den Datendownloadfilter „Andere Datenfilter“ enthalten, es wurde jedoch keine Datenfilteroption ausgewählt. Die Entität muss eine Datenenfilteroption angeben.|
> |**Name**:<br />NoDataForVisualization<br />**Hex**:<br />8004E011<br />**Nummer**:<br />-2147164143|Es sind keine Daten zum Erstellen dieser Visualisierung vorhanden.|
> |**Name**:<br />NoDefaultValueForOptionSetArgument<br />**Hex**:<br />80060396<br />**Nummer**:<br />-2147089514|Für Argumente vom Typ OptionSet muss ein Standardwert festgelegt werden.|
> |**Name**:<br />NoDefinedRelationshipsForMOPIAssociation<br />**Hex**:<br />80060998<br />**Nummer**:<br />-2147087976|Die Entität für die Profilelementzuordnung verfügt nicht über definierte Beziehungen.|
> |**Name**:<br />NoDialNumber<br />**Hex**:<br />8004350f<br />**Nummer**:<br />-2147207921|Auf dem Fax oder für den Empfänger ist keine Faxnummer angegeben.|
> |**Name**:<br />NoEntitiesForBulkDelete<br />**Hex**:<br />80048442<br />**Nummer**:<br />-2147187646|Der Assistent für die Massenlöschung kann nicht geöffnet werden, da keine gültigen Entitäten zur Löschung vorhanden sind.|
> |**Name**:<br />NoEntitySpecified<br />**Hex**:<br />800608FA<br />**Nummer**:<br />-2147088134|Mindestens eine Entität wird erwartungsgemäß vom Tool verarbeitet.|
> |**Name**:<br />NoFilesSelected<br />**Hex**:<br />80071021<br />**Nummer**:<br />-2147020767|Keine Dokumente zum Kopieren ausgewählt. Wählen Sie eine Dokument aus, und versuchen Sie es noch mal.|
> |**Name**:<br />NoHeaderColumnFound<br />**Hex**:<br />80040368<br />**Nummer**:<br />-2147220632|Eine Spaltenüberschrift fehlt.|
> |**Name**:<br />NoIncidentMergeHavingSameParent<br />**Hex**:<br />8003F450<br />**Nummer**:<br />-2147224496|Untergeordnete Anfragen, denen unterschiedliche übergeordnete Anfragen zugeordnet sind, können nicht zusammengeführt werden.|
> |**Name**:<br />NoLabelsAssociatedWithStep<br />**Hex**:<br />80060408<br />**Nummer**:<br />-2147089400|{0} enthält keine zugeordneten Bezeichnungen|
> |**Name**:<br />NoLanguageProvisioned<br />**Hex**:<br />80044199<br />**Nummer**:<br />-2147204711|Für diese Organisation wird keine Sprache bereitgestellt.|
> |**Name**:<br />NoLicenseInConfigDB<br />**Hex**:<br />8004D241<br />**Nummer**:<br />-2147167679|Keine Lizenz in der MSCRM_CONFIG-Datenbank vorhanden.|
> |**Name**:<br />NoMinimumRequiredPrivilegesForTabletApp<br />**Hex**:<br />8005F20F<br />**Nummer**:<br />-2147094001|Sie verfügen nicht über ausreichende Berechtigungen auf dem Server, um die Anwendung zu laden.\nWenden Sie sich an Ihren Administrator, um Ihre Berechtigungen zu aktualisieren.|
> |**Name**:<br />NoMoreCustomOptionValuesExist<br />**Hex**:<br />8004431F<br />**Nummer**:<br />-2147204321|Alle verfügbaren benutzerdefinierten Optionswerte wurden verwendet.|
> |**Name**:<br />NoncompliantXml<br />**Hex**:<br />80048425<br />**Nummer**:<br />-2147187675|Das Eingabe-XML stimmt nicht mit dem XML-Schema überein.|
> |**Name**:<br />NonCrmUIInteractiveWorkflowNotSupported<br />**Hex**:<br />80045044<br />**Nummer**:<br />-2147200956|Dieser interaktive Workflow kann nicht erstellt, aktualisiert oder veröffentlicht werden, da er außerhalb der Microsoft Dynamics 365-Webanwendung erstellt wurde.|
> |**Name**:<br />NonCrmUIWorkflowsNotSupported<br />**Hex**:<br />80045040<br />**Nummer**:<br />-2147200960|Dieser Workflow kann nicht erstellt, aktualisiert oder veröffentlicht werden, da er außerhalb der Microsoft Dynamics 365-Webanwendung erstellt wurde. Ihre Organisation lässt diese Art von Workflow nicht zu.|
> |**Name**:<br />NonDraftBundleUpdate<br />**Hex**:<br />80061039<br />**Nummer**:<br />-2147086279|Produktzuordnung kann nicht aktualisiert werden, wenn das Paket sich in einem ungültigen Status befindet.|
> |**Name**:<br />NonInteractiveUserCannotAccessUI<br />**Hex**:<br />80044160<br />**Nummer**:<br />-2147204768|Nicht aktive Benutzer können nicht auf die Webbenutzeroberfläche zugreifen. Wenden Sie sich an den Systemadministrator Ihrer Organisation.|
> |**Name**:<br />NonMappableEntity<br />**Hex**:<br />80046200<br />**Nummer**:<br />-2147196416|NonMappableEntity-Fehler aufgetreten|
> |**Name**:<br />NonPrimaryEntityDataDescriptionFound<br />**Hex**:<br />8004E001<br />**Nummer**:<br />-2147164159|Die Datenenbeschreibung für die Visualisierung ist ungültig. Die Datenenbeschreibung für die Visualisierung kann nur Attribute entweder von der primären Entität einer Ansicht oder der verknüpften Entitäten haben.|
> |**Name**:<br />NoOutputTransformationParameterMappingFound<br />**Hex**:<br />80040384<br />**Nummer**:<br />-2147220604|Es ist keine Ausgabe-Transformationsparameterzuordnung definiert. Eine Transformationszuordnung muss mindestens über eine Ausgangstransformations-Parameterzuordnung verfügen.|
> |**Name**:<br />NoPreviewForCustomWebResource<br />**Hex**:<br />8004E020<br />**Nummer**:<br />-2147164128|Dieses Diagramm nutzt eine benutzerdefinierte Webressource. Sie können dieses Diagramm nicht in der Vorschau anzuzeigen.|
> |**Name**:<br />NoPrivilegeToApplyManualSLA<br />**Hex**:<br />80055002<br />**Nummer**:<br />-2147135486|Sie besitzen nicht die erforderlichen Berechtigungen, um eine Vereinbarung zum Servicelevel (SLA) auf diesen Anfragedatensatz anzuwenden.|
> |**Name**:<br />NoPrivilegeToPublishWorkflow<br />**Hex**:<br />80045016<br />**Nummer**:<br />-2147201002|Sie verfügen nicht über die erforderlichen Privilegien zum Veröffentlichen von Workflows.|
> |**Name**:<br />NoPrivilegeToWorker<br />**Hex**:<br />80040521<br />**Nummer**:<br />-2147220191|Sie könnenkeine Artikel einer inaktiven Warteschlange hinzufügen. Wählen Sie eine andere Warteschlange aus, und versuchen Sie es erneut.|
> |**Name**:<br />NoPublishedDuplicateDetectionRules<br />**Hex**:<br />80048436<br />**Nummer**:<br />-2147187658|Es hat nicht veröffentlichte Duplikaterkennungsregeln im System. Um die Duplikaterkennung auszuführen, müssen Sie mindestens eine Regel erstellen und veröffentlichen.|
> |**Name**:<br />NoQuickFindFound<br />**Hex**:<br />80060203<br />**Nummer**:<br />-2147089917|Entität - {0} hatte keine gültige Quickfind-Abfrage.|
> |**Name**:<br />NoRollupAttributesDefined<br />**Hex**:<br />8004F681<br />**Nummer**:<br />-2147158399|Damit das Rollup erfolgreich ist, muss mindestens ein Rollupattribut der Zielmetrik zugeordnet werden|
> |**Name**:<br />NoSettingError<br />**Hex**:<br />8004Ed46<br />**Nummer**:<br />-2147160762|Keine Konfigurationseinstellung für [{0}] gefunden.|
> |**Name**:<br />NoSiteMapReferenceInAppModule<br />**Hex**:<br />8005011C<br />**Nummer**:<br />-2147155684|App-Modul enthält keine Siteübersicht|
> |**Name**:<br />NotAWellFormedXml<br />**Hex**:<br />80048426<br />**Nummer**:<br />-2147187674|Das Eingabezuordnungs-XML ist nicht ordnungsgemäß formatiert.|
> |**Name**:<br />NotEnoughPrivilegesForXamlWorkflows<br />**Hex**:<br />80045041<br />**Nummer**:<br />-2147200959|Keine ausreichenden Rechte, um den Vorgang abzuschließen. Unzureichende Berechtigungen zum Abschließen des Vorgangs. Außerhalb der Microsoft Dynamics 365-Webanwendung erstellte Workflows können ausschließlich vom Bereitstellungsadministrator erstellt oder aktualisiert werden.|
> |**Name**:<br />NoTestEmailAccessPrivilege<br />**Hex**:<br />8005E232<br />**Nummer**:<br />-2147098062|Es gibt keine ausreichenden Berechtigungen, um den Test auszuführen.|
> |**Name**:<br />NotExistArgumentInAction<br />**Hex**:<br />80060393<br />**Nummer**:<br />-2147089517|Das Argument {0} ist in der Aktion nicht vorhanden.|
> |**Name**:<br />NotExistBusinessProcess<br />**Hex**:<br />80060391<br />**Nummer**:<br />-2147089519|Der Geschäftsprozess ist nicht vorhanden.|
> |**Name**:<br />NoTimeZoneCodeForConversionRule<br />**Hex**:<br />800608F9<br />**Nummer**:<br />-2147088135|Die TimeZoneCode-Eigenschaft muss angegeben werden, wenn der Wert der ConversionRul-Eigenschaft SpecificTimeZone lautet.|
> |**Name**:<br />NotImplemented<br />**Hex**:<br />80040219<br />**Nummer**:<br />-2147220967|Die angeforderte Funktionalität ist nicht vorhanden.|
> |**Name**:<br />NotMobileEnabled<br />**Hex**:<br />8005F215<br />**Nummer**:<br />-2147093995|Dieser Datensatztyp kann auf Ihrem Tablet nicht angezeigt werden. Wenden Sie sich an den zuständigen Systemadministrator.|
> |**Name**:<br />NotMobileWriteEnabled<br />**Hex**:<br />8005F21c<br />**Nummer**:<br />-2147093988|Dieser Datensatztyp kann auf Ihrem Gerät nicht erstellt werden. Wenden Sie sich an den zuständigen Systemadministrator.|
> |**Name**:<br />NotSupported<br />**Hex**:<br />80040315<br />**Nummer**:<br />-2147220715|Diese Aktion wird nicht unterstützt.|
> |**Name**:<br />NotVerifiedAdmin<br />**Hex**:<br />8005F106<br />**Nummer**:<br />-2147094266|Sie benötigen ein Unternehmenskonto mit Yammer, um die Installation abzuschließen. Bittel melden Sie sich mit einem Yammer-Administratorkonto an oder wenden Sie sich an einen Yammer-Administrator, um Hilfe zu erhalten.|
> |**Name**:<br />NoUserPrivilege<br />**Hex**:<br />80154B50<br />**Nummer**:<br />-2146088112|Sie besitzen keine ausreichenden Berechtigungen.|
> |**Name**:<br />NoWritePermission<br />**Hex**:<br />80071023<br />**Nummer**:<br />-2147020765|Sie verfügen nicht über Schreibberechtigungen zum Kopieren der Dokumente.|
> |**Name**:<br />NoYammerNetworksFound<br />**Hex**:<br />8005F108<br />**Nummer**:<br />-2147094264|Sie sind nicht für ein Yammer-Netzwerk autorisiert. Bitte autorisieren Sie die Yammer-Einrichtung mit einem Yammer-Administratorkonto oder wenden Sie sich an einen Yammer-Administrator, um Hilfe zu erhalten.|
> |**Name**:<br />NullArticleTemplateFormatXml<br />**Hex**:<br />800404f8<br />**Nummer**:<br />-2147220232|Die formatxml Artikelvorlage kann nicht UNGÜLTIG sein|
> |**Name**:<br />NullArticleTemplateStructureXml<br />**Hex**:<br />800404f9<br />**Nummer**:<br />-2147220231|Die structurexml Artikelvorlage kann nicht UNGÜLTIG sein|
> |**Name**:<br />NullArticleXml<br />**Hex**:<br />800404f7<br />**Nummer**:<br />-2147220233|Der Artikel xml kann nicht UNGÜLTIG sein|
> |**Name**:<br />NullDashboardName<br />**Hex**:<br />8004E305<br />**Nummer**:<br />-2147163387|Der Name eines Dashboards kann nicht Null sein.|
> |**Name**:<br />NullKBArticleTemplateId<br />**Hex**:<br />800404fa<br />**Nummer**:<br />-2147220230|kbarticletemplateid kann nicht Null sein|
> |**Name**:<br />NullOrEmptyAttributeInXaml<br />**Hex**:<br />80060406<br />**Nummer**:<br />-2147089402|Das Attribute – {0} von {1} darf nicht NULL oder leer sein.|
> |**Name**:<br />NumberFormatFailed<br />**Hex**:<br />80040259<br />**Nummer**:<br />-2147220903|Fehler bei der Erstellung eines numerischen Werts.|
> |**Name**:<br />OAuthTokenNotFound<br />**Hex**:<br />8005F109<br />**Nummer**:<br />-2147094263|Das Yammer-OAuth-Token wurde nicht gefunden. Sie sollten Yammer konfigurieren, bevor Sie eine zugehörige Funktion nutzen.|
> |**Name**:<br />ObjectAlreadyExists<br />**Hex**:<br />8004E30A<br />**Nummer**:<br />-2147163382|Ein Objekt mit ID {0} ist bereits vorhanden. Ändern Sie die ID und versuchen Sie es erneut.|
> |**Name**:<br />ObjectDoesNotExist<br />**Hex**:<br />80040217<br />**Nummer**:<br />-2147220969|Das angegebene Objekt wurde nicht gefunden.|
> |**Name**:<br />ObjectNotFoundInAD<br />**Hex**:<br />80041d2a<br />**Nummer**:<br />-2147214038|Das Objekt muss im Active Directory vorhanden sein.|
> |**Name**:<br />ObjectNotRelatedToCampaign<br />**Hex**:<br />8004030e<br />**Nummer**:<br />-2147220722|Angegebenes Objekt ist mit der übergeordneten Kampagne nicht verknüpft.|
> |**Name**:<br />OccurrenceCrossingBoundary<br />**Hex**:<br />8004E120<br />**Nummer**:<br />-2147163872|Zwei Vorkommnisse können sich nicht überschneiden.|
> |**Name**:<br />OccurrenceSkipsOverBackward<br />**Hex**:<br />8004E123<br />**Nummer**:<br />-2147163869|Der Termin der Terminserie darf nicht vor einen früheren Termin derselben Terminserie verlegt werden.|
> |**Name**:<br />OccurrenceSkipsOverForward<br />**Hex**:<br />8004E122<br />**Nummer**:<br />-2147163870|Der Termin der Terminserie darf nicht nach einen späteren Termin derselben Terminserie verlegt werden.|
> |**Name**:<br />OccurrenceTimeSpanTooBig<br />**Hex**:<br />8004E121<br />**Nummer**:<br />-2147163871|Kann den Vorgang nicht ausführen. Eine Instanz liegt außerhalb des effizienten Erweiterungsbereichs der Reihe.|
> |**Name**:<br />OfferingCategoryAndTokenNull<br />**Hex**:<br />8004B00C<br />**Nummer**:<br />-2147176436|Angebotkategorie und Fakturierungs-Token fehlen, aber das ist mindestens erforderlich.|
> |**Name**:<br />OfferingIdNotSupported<br />**Hex**:<br />8004B00D<br />**Nummer**:<br />-2147176435|Diese Version unterstützt Suchen für Angebots-ID nicht.|
> |**Name**:<br />OfficeGraphDisabledError<br />**Hex**:<br />80044239<br />**Nummer**:<br />-2147204551|Dokumentempfehlungen wurden für diese Organisation deaktiviert.|
> |**Name**:<br />OfficeGraphSiteNotConfigured<br />**Hex**:<br />80044257<br />**Nummer**:<br />-2147204521|Kein standardmäßiger SharePoint-Standort wurde konfiguriert.|
> |**Name**:<br />OfficeGroupsExceptionRetrieveSetting<br />**Hex**:<br />800610EB<br />**Nummer**:<br />-2147086101|Office-Gruppen-Ausnahme in RetrieveOfficeGroupsSetting aufgetreten: {0}.|
> |**Name**:<br />OfficeGroupsFeatureNotEnabled<br />**Hex**:<br />800610EA<br />**Nummer**:<br />-2147086102|Office-Gruppen-Funktion ist nicht aktiviert.|
> |**Name**:<br />OfficeGroupsInvalidSettingType<br />**Hex**:<br />800610EC<br />**Nummer**:<br />-2147086100|Ungültiger Einstellungstyp für Office-Gruppenfunktion: {0}.|
> |**Name**:<br />OfficeGroupsNoAuthServersFound<br />**Hex**:<br />800610EE<br />**Nummer**:<br />-2147086098|Office-Gruppenfunktion kann keinen Autorisierungsserver finden.|
> |**Name**:<br />OfficeGroupsNotSupportedCall<br />**Hex**:<br />800610ED<br />**Nummer**:<br />-2147086099|Office-Gruppenfunktion versuchte einen nicht unterstützten Anruf.|
> |**Name**:<br />OfflineFilterNestedDateTimeOR<br />**Hex**:<br />80048450<br />**Nummer**:<br />-2147187632|Sie können geschachtelte Datum-Zeit-Bedingungen in OR-Klauseln in einer lokalen Datengruppe nicht verwenden.|
> |**Name**:<br />OfflineFilterParentDownloaded<br />**Hex**:<br />80048451<br />**Nummer**:<br />-2147187631|Die übergeordnete heruntergeladene Bedingung in einer lokalen Datengruppe kann nicht verwendet werden.|
> |**Name**:<br />OneDriveForBusinessDisabled<br />**Hex**:<br />80050004<br />**Nummer**:<br />-2147155964|Das Nachverfolgen von Anlagen ist bei OneDrive for Business erforderlich. Wenden Sie sich an den Administrator, um OneDrive for Business in der Organisation zu aktivieren.|
> |**Name**:<br />OneDriveForBusinessLocationNotFound<br />**Hex**:<br />80050009<br />**Nummer**:<br />-2147155959|Kein aktiver One Drive for Business-Standort gefunden.|
> |**Name**:<br />OneNoteCreationFailed<br />**Hex**:<br />80060902<br />**Nummer**:<br />-2147088126|OneNote-Erstellung fehlgeschlagen.|
> |**Name**:<br />OneNoteLocationDeactivated<br />**Hex**:<br />80060907<br />**Nummer**:<br />-2147088121|Die Speicherortzuordnung für OneNote ist inaktiv. Wenden Sie sich an Ihren Administrator, um den OneNote-Standortdatensatz für diesen Dynamics 365-Datensatz zu aktivieren.|
> |**Name**:<br />OneNoteLocationNotCreated<br />**Hex**:<br />80060906<br />**Nummer**:<br />-2147088122|OneNote-Speicherort nicht erstellt.|
> |**Name**:<br />OneNoteRenderFailed<br />**Hex**:<br />80060903<br />**Nummer**:<br />-2147088125|OneNote-Rendering fehlgeschlagen.|
> |**Name**:<br />OnlyDisabledOrganizationCanBeDeleted<br />**Hex**:<br />8004B02F<br />**Nummer**:<br />-2147176401|Aktivierte Organisation kann nicht gelöscht werden. Bevor Sie eine Organisation löschen können, müssen Sie sie deaktivieren.|
> |**Name**:<br />OnlyOneSearchParameterMustBeProvided<br />**Hex**:<br />80060206<br />**Nummer**:<br />-2147089914|Zusätzlicher Parameter. Sie müssen nur EntityGroupName oder EntityNames angeben, nicht beides.|
> |**Name**:<br />OnlyOwnerCanRevoke<br />**Hex**:<br />80040223<br />**Nummer**:<br />-2147220957|Nur der Besitzer eines Objekts kann den Zugriff des Besitzers auf das Objekt widerrufen.|
> |**Name**:<br />OnlyOwnerCanSetManagedProperties<br />**Hex**:<br />8004F031<br />**Nummer**:<br />-2147160015|Komponente kann nicht importiert werden {0}: {1} da sich die Eigenschaft {2} mit Wert {3} vom aktuellen Wert {4} unterscheidet und der Herausgeber der Lösung, die importiert wird, entspricht nicht dem Herausgeber der Lösung, die diese Komponente installiert hat.|
> |**Name**:<br />OnlyProductCanBeConvertedToKit<br />**Hex**:<br />80061017<br />**Nummer**:<br />-2147086313|Nur Produkte können in Bausätze konvertiert werden.|
> |**Name**:<br />OnlyStepInPredefinedStagesCanBeModified<br />**Hex**:<br />80044184<br />**Nummer**:<br />-2147204732|Ungültige Plug-In-Registrierungsphase. Ungültige Plug-In-Registrierungsphase. Nur in den folgenden Phasen können Schritte geändert werden: 'BeforeMainOperationOutsideTransaction', 'BeforeMainOperationInsideTransaction', 'AfterMainOperationInsideTransaction' und 'AfterMainOperationOutsideTransaction'.|
> |**Name**:<br />OnlyStepInServerOnlyCanHaveSecureConfiguration<br />**Hex**:<br />80044185<br />**Nummer**:<br />-2147204731|Nur SdkMessageProcessingStep mit ServerOnly unterstützte Bereitstellung kann sichere Konfiguration haben.|
> |**Name**:<br />OnlyStepOutsideTransactionCanCreateCrmService<br />**Hex**:<br />80044186<br />**Nummer**:<br />-2147204730|Nur SdkMessageProcessingStep in der übergeordneten Pipeline und in der äußeren Transaktion der Phasen kann CrmService Deadlock erstellen..|
> |**Name**:<br />OnlyWorkflowDefinitionOrTemplateCanBePublished<br />**Hex**:<br />8004500D<br />**Nummer**:<br />-2147201011|Nur Workflowdefinitions oder Entwurfsworkflowvorlagen können veröffentlicht werden.|
> |**Name**:<br />OnlyWorkflowDefinitionOrTemplateCanBeUnpublished<br />**Hex**:<br />8004500E<br />**Nummer**:<br />-2147201010|Nur Workflowdefinition oder Entwurfsworkflowvorlage können von der Veröffentlichung zurückgezogen werden.|
> |**Name**:<br />OnPremiseRestoreOrganizationManifestFailed<br />**Hex**:<br />80048532<br />**Nummer**:<br />-2147187406|Der configdb-Status des Manifests der Organisation konnte nicht wiederherstellt werden|
> |**Name**:<br />OpenCrmDBConnection<br />**Hex**:<br />8004023e<br />**Nummer**:<br />-2147220930|DB-Verbindung wird geöffnet, wenn sie geschlossen werden soll.|
> |**Name**:<br />OpenDocumentErrorCodeGeneric<br />**Hex**:<br />8005F20C<br />**Nummer**:<br />-2147094004|Wiederholen Sie den Vorgang. Besteht das Problem weiterhin, überprüfen Sie {0} auf Lösungen, oder wenden Sie sich an den {#Brand_CRM}-Administrator in Ihrer Organisation. Schließlich können Sie {1} kontaktieren.|
> |**Name**:<br />OpenDocumentErrorCodeUnableToFindAnActivity<br />**Hex**:<br />8005F20A<br />**Nummer**:<br />-2147094006|Wiederholen Sie den Vorgang. Besteht das Problem weiterhin, überprüfen Sie {0} auf Lösungen, oder wenden Sie sich an den {#Brand_CRM}-Administrator in Ihrer Organisation. Schließlich können Sie {1} kontaktieren.|
> |**Name**:<br />OpenDocumentErrorCodeUnableToFindTheDataId<br />**Hex**:<br />8005F20B<br />**Nummer**:<br />-2147094005|Wiederholen Sie den Vorgang. Besteht das Problem weiterhin, überprüfen Sie {0} auf Lösungen, oder wenden Sie sich an den {#Brand_CRM}-Administrator in Ihrer Organisation. Schließlich können Sie {1} kontaktieren.|
> |**Name**:<br />OpenMailboxException<br />**Hex**:<br />8005E216<br />**Nummer**:<br />-2147098090|Ausnahme beim Öffnen des Postfachs für Exchange-E-Mail-Server.|
> |**Name**:<br />OperationCanBeCalledOnlyOnce<br />**Hex**:<br />80040334<br />**Nummer**:<br />-2147220684|Die angegebene Aktion kann nur einmal ausgeführt werden.|
> |**Name**:<br />OperationCanceled<br />**Hex**:<br />80060912<br />**Nummer**:<br />-2147088110|Die Aktualisierung wurde durch den Benutzer abgebrochen.|
> |**Name**:<br />OperationFailedTryAgain<br />**Hex**:<br />80154B53<br />**Nummer**:<br />-2146088109|Die Aktion konnte nicht ausgeführt werden. Bitte wiederholen Sie den Vorgang.|
> |**Name**:<br />OperationOrganizationNotFullyDisabled<br />**Hex**:<br />8004D23a<br />**Nummer**:<br />-2147167686|Fehler bei {1} Verschiebevorgang, da Organisation {0} nicht vollständig deaktiviert ist.  Verwendung ERZWINGT, um zum Überschreiben|
> |**Name**:<br />OperatorCodeNotPresentError<br />**Hex**:<br />80044241<br />**Nummer**:<br />-2147204543|OperatorCode-Name muss in Bedingungs-XML vorhanden sein.|
> |**Name**:<br />OperatorsInViewNotSupportedOffline<br />**Hex**:<br />80071127<br />**Nummer**:<br />-2147020505|Mindestens ein Operator in dieser Ansicht wird im Offlinemodus nicht unterstützt.|
> |**Name**:<br />OpportunityAlreadyInOpenState<br />**Hex**:<br />8004051a<br />**Nummer**:<br />-2147220198|Die Verkaufschance ist bereits in geöffnetem Status.|
> |**Name**:<br />OpportunityCannotBeClosed<br />**Hex**:<br />80040516<br />**Nummer**:<br />-2147220202|Die Verkaufschance kann nicht geschlossen werden.|
> |**Name**:<br />OpportunityCurrencyComparisonNotPossible<br />**Hex**:<br />80100004<br />**Nummer**:<br />-2146435068|Die Verkaufschance kann nicht aktualisiert werden, der Währungsvergleich konnte nicht vorgenommen werden.|
> |**Name**:<br />OpportunityIsAlreadyClosed<br />**Hex**:<br />80040515<br />**Nummer**:<br />-2147220203|Die Verkaufschance ist bereits geschlossen.|
> |**Name**:<br />OpportunityNotFound<br />**Hex**:<br />80100006<br />**Nummer**:<br />-2146435066|Verkaufschancenentität kann für Update nicht abgerufen werden.|
> |**Name**:<br />OpportunityPreImageNotFound<br />**Hex**:<br />80100007<br />**Nummer**:<br />-2146435065|Ein vorheriges Abbild der Verkaufschance vor dem Update kann nicht gefunden werden.|
> |**Name**:<br />OptimisticConcurrencyNotEnabled<br />**Hex**:<br />8006088D<br />**Nummer**:<br />-2147088243|Optimistische Parallelität wird für Entitätstyp aktiviert. {0} Der IfVersionMatches-Wert von ConcurrencyBehavior kann nur verwendet werden, wenn optimistische Parallelität aktiviert ist.|
> |**Name**:<br />OptionReorderArrayIncorrectLength<br />**Hex**:<br />80044324<br />**Nummer**:<br />-2147204316|Das Array von Optionswerten, die für das neu anordnen bereitgestellt wurden, entspricht nicht der Anzahl von Optionen für das Attribut.|
> |**Name**:<br />OptionSetValidationFailed<br />**Hex**:<br />80061005<br />**Nummer**:<br />-2147086331|Wert liegt außerhalb des gültigen Bereichs.|
> |**Name**:<br />OptionValuePrefixOutOfRange<br />**Hex**:<br />80048402<br />**Nummer**:<br />-2147187710|CustomizationOptionValuePrefix muss eine Zahl zwischen {0} und {1} sein|
> |**Name**:<br />OrganizationDisabled<br />**Hex**:<br />8004A104<br />**Nummer**:<br />-2147180284|Die Dynamics 365-Organisation, auf die Sie zugreifen möchten wird nun deaktiviert.  Wenden Sie sich an Ihren Systemadministrator.|
> |**Name**:<br />OrganizationMigrationUnderway<br />**Hex**:<br />8004B044<br />**Nummer**:<br />-2147176380|Organisationsmigration ist bereits ausgeführt.|
> |**Name**:<br />OrganizationNotConfigured<br />**Hex**:<br />8004D253<br />**Nummer**:<br />-2147167661|Ihre Organisation ist noch nicht konfiguriert|
> |**Name**:<br />OrganizationTakenBySomeoneElse<br />**Hex**:<br />8004B00F<br />**Nummer**:<br />-2147176433|Die Organisation {0} ist bereits wird bereits von einem anderen Kunden erworben.|
> |**Name**:<br />OrganizationTakenByYou<br />**Hex**:<br />8004B00E<br />**Nummer**:<br />-2147176434|Die Organisation {0} ist bereits von Ihnen erworben.|
> |**Name**:<br />OrganizationUIDeprecated<br />**Hex**:<br />80044159<br />**Nummer**:<br />-2147204775|Die OrganizationUI-Entität ist veraltet. Es wurde durch die SystemForm-Entität ersetzt.|
> |**Name**:<br />OrgDoesNotExistInDiscoveryService<br />**Hex**:<br />8004B067<br />**Nummer**:<br />-2147176345|Suchdienst in Organisation nicht gefunden|
> |**Name**:<br />OrgIdNotDetermined<br />**Hex**:<br />80044353<br />**Nummer**:<br />-2147204269|Fehler. Die aktuelle Organisations-ID konnte nicht festgestellt werden|
> |**Name**:<br />OrgsInaccessible<br />**Hex**:<br />8004D24A<br />**Nummer**:<br />-2147167670|Die Ergebnisse für die Clientzugriffslizenz wurden nicht zurückgegeben, da auf mindestens eine Organisation in der Bereitstellung nicht zugegriffen werden kann.|
> |**Name**:<br />OutgoingNotAllowedForForwardMailbox<br />**Hex**:<br />8005E225<br />**Nummer**:<br />-2147098075|Postfach ist ein Weiterleitungspostfach. Ein Weiterleitungspostfach kann die E-Mail nicht senden.|
> |**Name**:<br />OutgoingServerLocationAndSslSetToNo<br />**Hex**:<br />8005E23F<br />**Nummer**:<br />-2147098049|Für die URL, die für den Serverstandort für ausgehende E-Mails angegeben ist, wird HTTPS verwendet. Aber die Nutzung von SSL für ausgehende Verbindungen ist auf Nein gesetzt. Legen Sie diese Option auf "Ja " fest, und versuchen Sie es anschließend erneut.|
> |**Name**:<br />OutgoingServerLocationAndSslSetToYes<br />**Hex**:<br />8005E241<br />**Nummer**:<br />-2147098047|Für die URL, die für den Serverstandort für ausgehende E-Mails angegeben ist, wird SSL für ausgehende Verbindungen auf Ja gesetzt. Geben Sie einen Serverspeicherort an, der HTTPS verwendet und versuchen Sie es anschließend erneut.|
> |**Name**:<br />OutgoingSettingsUpdateNotAllowed<br />**Hex**:<br />8005E238<br />**Nummer**:<br />-2147098056|Verschiedene ausgehende Verbindungseinstellungen können nicht angegeben werden, da die "Gleiche Einstellungen für ausgehende Verbindungen verwenden"-Flag auf "True" festgelegt ist.|
> |**Name**:<br />OutlookClientConfigActionFailed<br />**Hex**:<br />80044509<br />**Nummer**:<br />-2147203831|Aktion zur Konfiguration des Dynamics 365-Outlook-Client ist fehlgeschlagen.|
> |**Name**:<br />OutOfScopeSlug<br />**Hex**:<br />80045050<br />**Nummer**:<br />-2147200944|Die Daten, die erforderlich sind, um die nächste Dialogseite anzuzeigen, können nicht gefunden. Um dieses Problem zu beheben, wenden Sie sich an den Dialogfeldbesitzer oder den Systemadministrator.|
> |**Name**:<br />OverlappingInstances<br />**Hex**:<br />8004E108<br />**Nummer**:<br />-2147163896|Zwei Instanzen der Serie können nicht überschneidet.|
> |**Name**:<br />OverRetrievalUpperLimitWithoutPagingCookie<br />**Hex**:<br />8004430A<br />**Nummer**:<br />-2147204342|Informationen Obergrenze von Datensätzen, die ohne ein Auslagerungscookie angefordert werden können. Ein Auslagerungscookie ist erforderlich, wenn eine hohe Seitenzahl abgerufen wird.|
> |**Name**:<br />OwnerAttributeMissing<br />**Hex**:<br />8006110C<br />**Nummer**:<br />-2147086068|Besitzers-Attribut ist nicht in der Anforderung vorhanden.|
> |**Name**:<br />OwnerMappingExistsWithSourceSystemUserName<br />**Hex**:<br />80040343<br />**Nummer**:<br />-2147220669|Die Datenzuordnung enthält bereits diese Besitzerzuordnung.|
> |**Name**:<br />OwnerValueNotMapped<br />**Hex**:<br />80040361<br />**Nummer**:<br />-2147220639|Der Besitzerwert ist nicht zugeordnet|
> |**Name**:<br />PageNotFound<br />**Hex**:<br />8005F21A<br />**Nummer**:<br />-2147093990|Seite nicht gefunden. Der Datensatz existiert nicht, oder der Link ist möglicherweise ungültig.|
> |**Name**:<br />ParentBusinessDoesNotExist<br />**Hex**:<br />80041d23<br />**Nummer**:<br />-2147214045|Die übergeordnete Unternehmens-ID ist nicht gültig.|
> |**Name**:<br />ParentCaseNotAllowedAsAChildCase<br />**Hex**:<br />8003F455<br />**Nummer**:<br />-2147224491|Sie können eine übergeordnete Anfrage nicht als untergeordnete Anfrage hinzufügen.|
> |**Name**:<br />ParentChildMetricIdDiffers<br />**Hex**:<br />80044905<br />**Nummer**:<br />-2147202811|Die metricid des untergeordneten Ziels sollte gleich sein wie das übergeordnete Ziel.|
> |**Name**:<br />ParentChildPeriodAttributesDiffer<br />**Hex**:<br />80044906<br />**Nummer**:<br />-2147202810|Die Periodeneinstellungen des untergeordneten Ziels sollte gleich sein wie das übergeordnete Ziel.|
> |**Name**:<br />ParentHierarchyExistProperty<br />**Hex**:<br />8004F888<br />**Nummer**:<br />-2147157880|Ein übergeordnetes Objekt muss für jeden Knoten in der Hierarchie außer dem Stammknoten vorhanden sein.|
> |**Name**:<br />ParentReadOnly<br />**Hex**:<br />80043b09<br />**Nummer**:<br />-2147206391|Die übergeordnete Datei ist schreibgeschützt und kann nicht bearbeitet werden.|
> |**Name**:<br />ParentRecordAlreadyExists<br />**Hex**:<br />80048478<br />**Nummer**:<br />-2147187592|Dieser Datensatz kann nicht hinzugefügt werden, da er bereits einen übergeordneten Datensatz besitzt.|
> |**Name**:<br />ParentReportDoesNotReferenceChild<br />**Hex**:<br />80040486<br />**Nummer**:<br />-2147220346|Angegebener übergeordneten Bericht referenziert nicht auf den aktuellen. Nur SQL Reporting Service-Berichte können übergeordnete Berichte verfügen.|
> |**Name**:<br />ParentReportLinksToSameNameChild<br />**Hex**:<br />80040496<br />**Nummer**:<br />-2147220330|Übergeordneter Bericht ist bereits mit einem weiteren Bericht mit dem gleichen Namen verknüpft.|
> |**Name**:<br />ParentReportNotSupported<br />**Hex**:<br />80040487<br />**Nummer**:<br />-2147220345|Übergeordneter Bericht wird für den Typ des Berichts nicht unterstützt. Nur SQL Reporting Service-Berichte können übergeordnete Berichte verfügen.|
> |**Name**:<br />ParentUserDoesNotExist<br />**Hex**:<br />80041d27<br />**Nummer**:<br />-2147214041|Die übergeordnete Benutzer-ID ist nicht gültig.|
> |**Name**:<br />ParseMustBeCalledBeforeTransform<br />**Hex**:<br />80040371<br />**Nummer**:<br />-2147220623|Transformation kann vor der Analyse nicht aufgerufen werden.|
> |**Name**:<br />ParsingMetadataNotFound<br />**Hex**:<br />80040367<br />**Nummer**:<br />-2147220633|Daten, die zum Analysieren der Datei erforderlich sind, z. B. das Datentrennzeichen, Feldtrennzeichen oder Spaltenüberschriften, wurden nicht gefunden.|
> |**Name**:<br />PartialExpansionSettingLoadError<br />**Hex**:<br />8004E102<br />**Nummer**:<br />-2147163902|Teilweise Erweiterungseinstellungen konnten nicht aus der Konfigurationsdatenbank abgerufen werden.|
> |**Name**:<br />PartialHolidayScheduleCreation<br />**Hex**:<br />8004F873<br />**Nummer**:<br />-2147157901|Der Feiertagszeitplan kann nicht teilweise erstellt werden.|
> |**Name**:<br />ParticipatingEntityDoesNotAppearInTraversedPath<br />**Hex**:<br />80060441<br />**Nummer**:<br />-2147089343|Fehler beim Anzeigen des Geschäftsprozess-Steuerelements. Teilnehmende Entität muss Teil eines zurückgelegten Pfads sein, aber die Entität „{0}” erscheint nicht im Pfad „{1}”. Wenden Sie sich an Ihren Systemadministrator.|
> |**Name**:<br />ParticipatingQueryEntityMismatch<br />**Hex**:<br />80044909<br />**Nummer**:<br />-2147202807|Der Entitätstyp der beteiligten Abfrage sollte gleich sein wie die Entität, die in fetchxml angegeben ist.|
> |**Name**:<br />PasswordRequiredForImpersonation<br />**Hex**:<br />8005E24E<br />**Nummer**:<br />-2147098034|Geben Sie ein Kennwort ein und speichern sie erneut|
> |**Name**:<br />PatchMissingBase<br />**Hex**:<br />80048540<br />**Nummer**:<br />-2147187392|Sie können den Patch ({0}) für die Lösung ({1}) nicht importieren, da die Lösung nicht vorhanden ist. Der Speichervorgang wurde abgebrochen.|
> |**Name**:<br />PercentageDiscountCannotHaveCurrency<br />**Hex**:<br />80048cf1<br />**Nummer**:<br />-2147185423|Währung kann nicht festgelegt werden, wenn Rabatttyp "Prozentsatz" ist.|
> |**Name**:<br />PersonalReportFound<br />**Hex**:<br />8004E309<br />**Nummer**:<br />-2147163383|Ein Systemdashboard kann keine persönlichen Berichten enthalten.|
> |**Name**:<br />PickListMappingExistsForTargetValue<br />**Hex**:<br />8004033f<br />**Nummer**:<br />-2147220673|Dieser Listenwert ist mehrmals zugeordnet. Entfernen Sie die mehrfachen Zuordnungen, und importieren Sie die Datenzuordnung anschließend erneut.|
> |**Name**:<br />PickListMappingExistsWithSourceValue<br />**Hex**:<br />80040342<br />**Nummer**:<br />-2147220670|Die Datenzuordnung enthält bereits diese Listenwertzuordnung.|
> |**Name**:<br />PicklistValueNotFound<br />**Hex**:<br />80040393<br />**Nummer**:<br />-2147220589|In der Datei wird ein Listenwert angegeben, der nicht in Microsoft Dynamics 365 vorhanden ist.|
> |**Name**:<br />PicklistValueNotMapped<br />**Hex**:<br />80040360<br />**Nummer**:<br />-2147220640|Der Datensatz konnte nicht verarbeitet werden, da der Optionsatz des Werts nicht zugeordnet werden konnte.|
> |**Name**:<br />PicklistValueNotUnique<br />**Hex**:<br />80044310<br />**Nummer**:<br />-2147204336|Der Auswahlwert ist bereits vorhanden.  Diese Werte müssen eindeutig sein.|
> |**Name**:<br />PicklistValueOutOfRange<br />**Hex**:<br />8004431A<br />**Nummer**:<br />-2147204326|Der Auswahllistenwert ist außerhalb des Bereichs.|
> |**Name**:<br />PingFailureErrorCode<br />**Hex**:<br />8005F212<br />**Nummer**:<br />-2147093998|Das System konnte keine erneute Verbindung mit Ihrem {#Brand_CRM}-Server herstellen.|
> |**Name**:<br />PluginAssemblyContentSizeExceeded<br />**Hex**:<br />8004418f<br />**Nummer**:<br />-2147204721|"Die Assemblyinhaltsgröße "{0} Bytes" hat den maximalen Wert überschritten, der für die isolierte Plug-Ins zulässig ist "{1} Bytes"."|
> |**Name**:<br />PluginAssemblyMustHavePublicKeyToken<br />**Hex**:<br />8004416c<br />**Nummer**:<br />-2147204756|Öffentliche Assembly muss öffentliches Schlüsseltoken haben.|
> |**Name**:<br />PluginDoesNotImplementCorrectInterface<br />**Hex**:<br />8004A200<br />**Nummer**:<br />-2147180032|Das angegebene Plug-In hat die erforderlichen Microsoft.Xrm.Sdk.IPlugin Benutzeroberfläche oder Microsoft.Crm.Sdk.IPlugin nicht implementiert.|
> |**Name**:<br />PluginSecureStoreAdalAcquireToken<br />**Hex**:<br />80091005<br />**Nummer**:<br />-2146889723|AcquireToken für Ressource nicht verfügbar|
> |**Name**:<br />PluginSecureStoreKeyVaultClient<br />**Hex**:<br />80091000<br />**Nummer**:<br />-2146889728|KeyVaultClientProvider unter Sandbox WorkerProcess kann nicht initialisiert werden|
> |**Name**:<br />PluginSecureStoreKeyVaultClientDecrypt<br />**Hex**:<br />80091003<br />**Nummer**:<br />-2146889725|KeyVault konnte nicht entschlüsselt werden|
> |**Name**:<br />PluginSecureStoreKeyVaultClientEncrypt<br />**Hex**:<br />80091004<br />**Nummer**:<br />-2146889724|KeyVault konnte nicht entschlüsselt werden|
> |**Name**:<br />PluginSecureStoreKeyVaultClientGetSecret<br />**Hex**:<br />80091001<br />**Nummer**:<br />-2146889727|GetSecret von KeyVault nicht abrufbar|
> |**Name**:<br />PluginSecureStoreKeyVaultClientSetSecret<br />**Hex**:<br />80091002<br />**Nummer**:<br />-2146889726|GetSecret Key Vault nicht abrufbar|
> |**Name**:<br />PluginSecureStoreKeyVaultServiceCertFormat<br />**Hex**:<br />8009100D<br />**Nummer**:<br />-2146889715|Zertifikat nicht als ein Base64String in KeyVault gespeichert|
> |**Name**:<br />PluginSecureStoreKeyVaultServiceProviderGetData<br />**Hex**:<br />8009100C<br />**Nummer**:<br />-2146889716|Fehlende App-ID / geheime Daten in Key Vault|
> |**Name**:<br />PluginSecureStoreLocalConfigStoreGetData<br />**Hex**:<br />8009100A<br />**Nummer**:<br />-2146889718|LocalConfigStore Daten können nicht abgerufen werden.|
> |**Name**:<br />PluginSecureStoreLocalConfigStoreSetData<br />**Hex**:<br />8009100B<br />**Nummer**:<br />-2146889717|LocalConfigStore Daten können nicht festgelegt werden.|
> |**Name**:<br />PluginSecureStoreNoFullySigned<br />**Hex**:<br />8009100F<br />**Nummer**:<br />-2146889713|Assembly nicht vollständig signiert|
> |**Name**:<br />PluginSecureStoreS2SMissing<br />**Hex**:<br />80091008<br />**Nummer**:<br />-2146889720|S2S Anmeldeinformationen fehlen|
> |**Name**:<br />PluginSecureStoreTPSAssemblyNotRegistered<br />**Hex**:<br />80091007<br />**Nummer**:<br />-2146889721|Assembly ist in TPS nicht registriert|
> |**Name**:<br />PluginSecureStoreTPSClient<br />**Hex**:<br />80091009<br />**Nummer**:<br />-2146889719|TPS Client konnte nicht erstellt werden|
> |**Name**:<br />PluginSecureStoreTPSKeyVaultUnconfigured<br />**Hex**:<br />80091006<br />**Nummer**:<br />-2146889722|KeyVaultURI wurde nicht für eine Assembly in TPS konfiguriert|
> |**Name**:<br />PluginTypeMustBeUnique<br />**Hex**:<br />8004417C<br />**Nummer**:<br />-2147204740|Mehrere Plug-In-Typen von derselben Assembly und mit demselben Typnamen sind nicht zulässig.|
> |**Name**:<br />Pop3UnexpectedException<br />**Hex**:<br />8005E215<br />**Nummer**:<br />-2147098091|Ausnahme beim Abruf von E-Mails mithilfe Pop3-Protokoll.|
> |**Name**:<br />PowerBICannotBeSystemDashboard<br />**Hex**:<br />800608FC<br />**Nummer**:<br />-2147088132|Ein Power BI-Dashboard kann kein Systemdashboard sein.|
> |**Name**:<br />PowerBIDashboardControlLimitation<br />**Hex**:<br />800608FD<br />**Nummer**:<br />-2147088131|Ein Power BI-Dashboard kann nur ein Steuerelement enthalten und dieses Steuerelement muss ein Power BI-Steuerelement sein.|
> |**Name**:<br />PresentParentAccountAndParentContact<br />**Hex**:<br />80040508<br />**Nummer**:<br />-2147220216|Sie können entweder einen übergeordneten Kontakt der Kontakte oder die Firma eingeben, aber nicht beide.|
> |**Name**:<br />PreviousOperationNotComplete<br />**Hex**:<br />80048464<br />**Nummer**:<br />-2147187612|Ein Vorgang, von der dieser Vorgang abhängt, wurde nicht erfolgreich abgeschlossen.|
> |**Name**:<br />PriceLevelNameExists<br />**Hex**:<br />80043b0f<br />**Nummer**:<br />-2147206385|Der Name ist bereits vorhanden.|
> |**Name**:<br />PriceLevelNoName<br />**Hex**:<br />80043b0e<br />**Nummer**:<br />-2147206386|Der Name kann nicht NULL sein.|
> |**Name**:<br />PrimaryEntityInvalid<br />**Hex**:<br />8004501E<br />**Nummer**:<br />-2147200994|Ungültige primäre Entität.|
> |**Name**:<br />PrimaryEntityIsNull<br />**Hex**:<br />80060401<br />**Nummer**:<br />-2147089407|Primäre Entität kann sich nicht beim Erstellen von Geschäftsprozessflusskategorie UNGÜLTIG sein|
> |**Name**:<br />PrimaryNameAttributeNotFound<br />**Hex**:<br />80044355<br />**Nummer**:<br />-2147204267|Das PrimaryName-Attribut wurde nicht für Entität {0} gefunden|
> |**Name**:<br />PrimaryParticipatingEntityIsNotPresent<br />**Hex**:<br />80060453<br />**Nummer**:<br />-2147089325|Überprüfungsfehler: Primäre teilnehmende Entität ist nicht vorhanden und für jeden Geschäftsprozess-Entitätsdatensatz erforderlich.|
> |**Name**:<br />PrincipalPrivilegeDenied<br />**Hex**:<br />80040231<br />**Nummer**:<br />-2147220943|Zielbenutzer oder Team hat keine erforderlichen Berechtigungen.|
> |**Name**:<br />PrivilegeCreateIsDisabledForOrganization<br />**Hex**:<br />80040276<br />**Nummer**:<br />-2147220874|Recht Erstellen für Organisation ist deaktiviert.|
> |**Name**:<br />PrivilegeDenied<br />**Hex**:<br />80040220<br />**Nummer**:<br />-2147220960|Der Benutzer verfügt nicht über die erforderlichen Rechte.|
> |**Name**:<br />ProcessActionDoesNotExist<br />**Hex**:<br />80045054<br />**Nummer**:<br />-2147200940|Die Prozessaktion ist nicht vorhanden.|
> |**Name**:<br />ProcessActionIsNotActive<br />**Hex**:<br />80045053<br />**Nummer**:<br />-2147200941|Die Prozessaktion sollte aktiv sein, damit sie im Aktionsschritt verwendet wird.|
> |**Name**:<br />ProcessActionNameIncorrect<br />**Hex**:<br />80060379<br />**Nummer**:<br />-2147089543|Die Prozessaktion „{0}” entspricht nicht dem konfigurierten Namen: „{1}”. Wenden Sie sich an den Systemadministrator, um die Konfigurationsmetadaten zu überprüfen, wenn der Fehler weiterhin besteht.|
> |**Name**:<br />ProcessActionWithInvalidInputOutputParam<br />**Hex**:<br />80045058<br />**Nummer**:<br />-2147200936|Die Prozessaktion enthält einen Parameter, der nicht unterstützt wird. Name: {0}, Typ: {1}, Richtung: {2}.|
> |**Name**:<br />ProcessActionWithInvalidInputParam<br />**Hex**:<br />80045057<br />**Nummer**:<br />-2147200937|Die Prozessaktion enthält ein Feld im Eingabeparameter, das nicht bei Aktionsschritten unterstützt wird. Siehe {0} |
> |**Name**:<br />ProcessActionWithInvalidOutputParam<br />**Hex**:<br />80045056<br />**Nummer**:<br />-2147200938|Die Prozessaktion enthält ein Feld im Ausgabeparameter, das nicht bei Aktionsschritten unterstützt wird. Siehe {0}.|
> |**Name**:<br />ProcessActionWorkflowNotEnabledForOnDemand<br />**Hex**:<br />80060380<br />**Nummer**:<br />-2147089536|Die Prozessaktion oder der Workflow müssen für die bedarfsabhängige Ausführung aktiviert werden, damit sie für Aktionsschritte verfügbar sind.|
> |**Name**:<br />ProcessEmptyBranches<br />**Hex**:<br />80060399<br />**Nummer**:<br />-2147089511|Dieser Prozess enthält die Verzweigungen. Definieren oder löschen Sie diese Verzweigungen, und versuchen Sie es erneut.|
> |**Name**:<br />ProcessIdDoesNotMatchBusinessProcessDefinition<br />**Hex**:<br />80060460<br />**Nummer**:<br />-2147089312|Überprüfungsfehler: Prozess-ID entspricht nicht der Geschäftsprozessdefinition.|
> |**Name**:<br />ProcessIdIsEmpty<br />**Hex**:<br />80060459<br />**Nummer**:<br />-2147089319|Überprüfungsfehler: Prozess-ID darf nicht leer sein.|
> |**Name**:<br />ProcessImageFailure<br />**Hex**:<br />80072553<br />**Nummer**:<br />-2147015341|Fehler beim Verarbeiten des Bilds. Grund: {0}|
> |**Name**:<br />ProcessNameContainsInvalidCharacters<br />**Hex**:<br />80060398<br />**Nummer**:<br />-2147089512|Der Geschäftsprozessname enthält ungültige Zeichen.|
> |**Name**:<br />ProcessNameIsNullOrEmpty<br />**Hex**:<br />80060418<br />**Nummer**:<br />-2147089384|Der Geschäftsprozessflussname ist Null oder leer. |
> |**Name**:<br />ProcessStageIdIsEmpty<br />**Hex**:<br />80060461<br />**Nummer**:<br />-2147089311|Überprüfungsfehler: Primäre Phasen-ID darf nicht leer sein.|
> |**Name**:<br />ProductCanOnlyBeUpdatedInDraft<br />**Hex**:<br />8004F995<br />**Nummer**:<br />-2147157611|Produkt, Produktfamilie und Paket können nur im Entwurfsstatus aktualisiert werden.|
> |**Name**:<br />ProductCloneFailed<br />**Hex**:<br />80061006<br />**Nummer**:<br />-2147086330|Sie können keinen untergeordneten Datensatz einer zurückgezogenen Produktfamilie klonen.|
> |**Name**:<br />ProductDoesNotExist<br />**Hex**:<br />80043b24<br />**Nummer**:<br />-2147206364|Das Produkt ist nicht vorhanden.|
> |**Name**:<br />ProductFamilyCanCreateDynamicProperty<br />**Hex**:<br />80081007<br />**Nummer**:<br />-2146955257|Eine Eigenschaft kann nur für eine Produktfamilie erstellt werden.|
> |**Name**:<br />ProductFamilyRootParentisLocked<br />**Hex**:<br />8008101F<br />**Nummer**:<br />-2146955233|Der übergeordnete Stammdatensatz der Produktfamilie ist durch einen anderen Prozess gesperrt.|
> |**Name**:<br />ProductFromActiveToActiveState<br />**Hex**:<br />8004F982<br />**Nummer**:<br />-2147157630|Der Produktstatus ist bereits aktiv.|
> |**Name**:<br />ProductFromActiveToDraftState<br />**Hex**:<br />8004F912<br />**Nummer**:<br />-2147157742|Veröffentlichte Produkte können nicht in den Entwurfsstatus versetzt werden.|
> |**Name**:<br />ProductFromDraftToDraftState<br />**Hex**:<br />8004F981<br />**Nummer**:<br />-2147157631|Der Produktstatus ist bereits im Entwurf-Zustand.|
> |**Name**:<br />ProductFromDraftToRetiredState<br />**Hex**:<br />8004F978<br />**Nummer**:<br />-2147157640|Sie können kein Produkt zurückziehen, das den Status "Entwurf" aufweist.|
> |**Name**:<br />ProductFromDraftToRevisedState<br />**Hex**:<br />8004F913<br />**Nummer**:<br />-2147157741|Produkte mit Entwurfsstatus und zurückgezogene Produkte können nicht überarbeitet werden.|
> |**Name**:<br />ProductFromRetiredToActiveState<br />**Hex**:<br />8004F977<br />**Nummer**:<br />-2147157641|Sie können keine zurückgezogene Eigenschaft in einen aktiven Status versetzen.|
> |**Name**:<br />ProductFromRetiredToDraftState<br />**Hex**:<br />8004F979<br />**Nummer**:<br />-2147157639|Es ist nicht möglich, ein Produkt mit dem Status "Zurückgezogen" in "Entwurf" zu ändern.|
> |**Name**:<br />ProductFromRetiredToRetiredState<br />**Hex**:<br />8004F980<br />**Nummer**:<br />-2147157632|Der Produktstatus ist bereits im zurückgezogenen Status.|
> |**Name**:<br />ProductHasUnretiredChild<br />**Hex**:<br />8004F910<br />**Nummer**:<br />-2147157744|Sie können diese Produktfamilie nicht zurückziehen, da mindestens ein untergeordneter Datensatz nicht zurückgezogen wurde.|
> |**Name**:<br />ProductInvalidPriceLevelPercentage<br />**Hex**:<br />80043b0c<br />**Nummer**:<br />-2147206388|Der Preisprozentsatz muss größer oder gleich null und weniger als 100.000 sein.|
> |**Name**:<br />ProductInvalidQuantityDecimal<br />**Hex**:<br />80043b07<br />**Nummer**:<br />-2147206393|Die Anzahl der angezeigten Dezimalstellen der Menge ist ungültig.|
> |**Name**:<br />ProductInvalidUnit<br />**Hex**:<br />80043b14<br />**Nummer**:<br />-2147206380|Die angegebene Einheit ist für dieses Produkt nicht gültig.|
> |**Name**:<br />ProductKitLoopBeingCreated<br />**Hex**:<br />80043b23<br />**Nummer**:<br />-2147206365|Sie können einen Bausatz nicht sich selbst hinzufügen.|
> |**Name**:<br />ProductKitLoopExists<br />**Hex**:<br />80043b22<br />**Nummer**:<br />-2147206366|Schleife ist in der Kithierarchie vorhanden.|
> |**Name**:<br />ProductMaxPropertyLimitExceeded<br />**Hex**:<br />8008100D<br />**Nummer**:<br />-2146955251|Dieses Produkt kann nicht publiziert werde, da es zu viele Eigenschaften hat. Ein Produkt in Ihrer Organisation kann maximal {0} Eigenschaften haben.|
> |**Name**:<br />ProductMissingUomSheduleId<br />**Hex**:<br />80043b13<br />**Nummer**:<br />-2147206381|Der Einheitszeitplan für das Produkt fehlt.|
> |**Name**:<br />ProductNoProductNumber<br />**Hex**:<br />80043b05<br />**Nummer**:<br />-2147206395|Die Produktnummer kann nicht NULL sein.|
> |**Name**:<br />ProductNoSubstitutedProductNumber<br />**Hex**:<br />8004F990<br />**Nummer**:<br />-2147157616|Die Ersatz-Produktnummer darf nicht NULL sein.|
> |**Name**:<br />ProductOrBundleCannotBeAsParent<br />**Hex**:<br />8004F973<br />**Nummer**:<br />-2147157645|Nur Produktfamilien übergeordnete Produkte werden.|
> |**Name**:<br />ProductProductNumberExists<br />**Hex**:<br />80043b06<br />**Nummer**:<br />-2147206394|Die angegebene Produkt-ID steht im Widerspruch mit der Produkt-ID eines vorhandenen Datensatzes. Geben Sie eine andere Produkt-ID an und versuchen Sie es erneut.|
> |**Name**:<br />ProductRecommendationsFeatureNotEnabled<br />**Hex**:<br />80061600<br />**Nummer**:<br />-2147084800|Die Produktempfehlungsfunktion ist nicht aktiviert.|
> |**Name**:<br />ProfileContainsCircularReference<br />**Hex**:<br />80071141<br />**Nummer**:<br />-2147020479|Das Profil „{0}” hat einen Zirkelbezug, der verhindert, dass Ihre Daten heruntergeladen werden. Btte prüfen Sie die Zirkelbezugskette: {1} und entfernen Sie die Profilelementzuordnung, die den Zirkelbezug verursacht.|
> |**Name**:<br />ProfileContainsRelationshipWithoutEntity<br />**Hex**:<br />80071142<br />**Nummer**:<br />-2147020478|Das Profil „{0}“ verfügt über ein Profilelement {1}, das eine Profilelementverknüpfung für {2} enthält, es ist jedoch kein Profilelement für {2} vorhanden. Bitte nehmen Sie das Profilelement auf und veröffentlichen Sie es.|
> |**Name**:<br />ProfileCountUserLimitExceeded<br />**Hex**:<br />80071134<br />**Nummer**:<br />-2147020492|Die Gesamtanzahl der Benutzer („{0}”) in diesem Profil übersteigt das zulässige Limit („{1}”). Bitte begrenzen Sie die Gesamtanzahl von Benutzern, damit sie im unterstützten Bereich liegt.|
> |**Name**:<br />ProfileRuleActivateDeactivateByNonOwner<br />**Hex**:<br />80061102<br />**Nummer**:<br />-2147086078|Diese Profilregel kann nur vom Besitzer aktiviert oder deaktiviert werden.|
> |**Name**:<br />ProfileRuleMissingRuleCriteria<br />**Hex**:<br />80061100<br />**Nummer**:<br />-2147086080|Sie können diese Regel erst aktivieren, wenn Sie fehlende Regelkriterieninformationen in den Regelelementen auflösen.|
> |**Name**:<br />ProfileRulePublishedByOwner<br />**Hex**:<br />80061103<br />**Nummer**:<br />-2147086077|Die Regel kann nicht aktiviert werden, wenn die aktuelle aktive Regel deaktiviert wurde. Die aktive Regel kann nur vom Regelbesitzer deaktiviert werden.|
> |**Name**:<br />ProfileRuleWorkflowAuthorGenericError<br />**Hex**:<br />80061101<br />**Nummer**:<br />-2147086079|Ein Fehler beim Erstellen des Workflows ist aufgetreten. Korrigieren Sie das Stapelprotokoll Workflowdefinition und versuchen Sie es erneut.|
> |**Name**:<br />ProvisioningNotCompleted<br />**Hex**:<br />80091044<br />**Nummer**:<br />-2146889660|Um die Erfassung zu aktivieren, müssen Sie Cortana Intelligence Customer Insights in den Beziehungsinformationeneinstellungen installieren.|
> |**Name**:<br />ProvisionRIAccessNotAllowed<br />**Hex**:<br />80044270<br />**Nummer**:<br />-2147204496|Sie benötigen Systemadministratorrechte, um Beziehungsinformationen für Ihre Organisation zu aktivieren.|
> |**Name**:<br />PublishArticle_TranslationWithMoreThanOneApprovedVersion<br />**Hex**:<br />80061401<br />**Nummer**:<br />-2147085311|Es gibt mehrere genehmigte Versionen der {0} Sprache. Sie können nur eine Version jeder Sprache veröffentlichen.|
> |**Name**:<br />PublishedWorkflowLimitForSkuReached<br />**Hex**:<br />80045015<br />**Nummer**:<br />-2147201003|Diesr Workflow kann nicht gelöscht, weil die Organisation eine Beschränkung für die Anzahl der erreicht Workflows, die gleichzeitig veröffentlicht werden können. (Es gibt keine Einschränkungen bei der Anzahl der Entwurfs-Workflows.) Sie können diesen Workflow veröffentlichen, indem Sie die Veröffentlichung eines anderen Workflows aufheben oder eine Lizenz mit zu einer Lizenz aktualisieren, die mehr Workflows unterstützt.|
> |**Name**:<br />PublishedWorkflowOwnershipChange<br />**Hex**:<br />8004500C<br />**Nummer**:<br />-2147201012|Ein veröffentlichter Workflow kann nur dem Anrufer zugewiesen werden.|
> |**Name**:<br />PublishWorkflowWhileActingOnBehalfOfAnotherUserError<br />**Hex**:<br />80045032<br />**Nummer**:<br />-2147200974|Veröffentlichen von Workflows, während das Fungieren im Auftrag eines anderen Benutzers nicht zulässig ist.|
> |**Name**:<br />PublishWorkflowWhileImpersonatingError<br />**Hex**:<br />80045039<br />**Nummer**:<br />-2147200967|Veröffentlichen von Workflows, während das Annehmen einer anderen Identität nicht zulässig ist.|
> |**Name**:<br />QuantityReadonly<br />**Hex**:<br />80043b18<br />**Nummer**:<br />-2147206376|Das Feld „Menge” darf nicht geändert werden, wenn Sie die primäre Einheit aktualisieren.|
> |**Name**:<br />QueriesForDifferentEntities<br />**Hex**:<br />8004D2B0<br />**Nummer**:<br />-2147167568|Die internen Verwendung und äußeren Abfragen müssen dieselbe Entität sein.|
> |**Name**:<br />QueryBuilderAlias_Does_Not_Exist<br />**Hex**:<br />8004110a<br />**Nummer**:<br />-2147217142|Der angegebener Alias für bestimmte Entitäten in der Bedingung ist nicht vorhanden.|
> |**Name**:<br />QueryBuilderAliasNotAllowedForNonAggregateOrderBy<br />**Hex**:<br />80041132<br />**Nummer**:<br />-2147217102|Ein Alias kann für eine Auftragsklausel für eine nicht Aggregat-Abfrage nicht angegeben werden. Verwenden Sie ein Attribut.|
> |**Name**:<br />QueryBuilderAliasRequiredForAggregateOrderBy<br />**Hex**:<br />80041134<br />**Nummer**:<br />-2147217100|Ein Alias ist für eine Auftragsklausel für eine Aggregat-Abfrage erforderlich.|
> |**Name**:<br />QueryBuilderAttribute_With_Aggregate<br />**Hex**:<br />80041107<br />**Nummer**:<br />-2147217145|Attribute können nicht zurückgegeben werden, wenn ein Aggregatvorgang angegeben ist.|
> |**Name**:<br />QueryBuilderAttributeCannotBeGroupByAndAggregate<br />**Hex**:<br />80041137<br />**Nummer**:<br />-2147217097|Ein Attribut kann ein Aggregat oder ein "Gruppieren nach" aber nicht beides sein|
> |**Name**:<br />QueryBuilderAttributeNotAllowedForAggregateOrderBy<br />**Hex**:<br />80041131<br />**Nummer**:<br />-2147217103|Ein Attribut kann für eine Auftragsklausel für eine Aggregat-Abfrage nicht angegeben werden. Verwenden Sie ein Alias.|
> |**Name**:<br />QueryBuilderAttributeNotFound<br />**Hex**:<br />8004111e<br />**Nummer**:<br />-2147217122|Ein erforderliches Attribut wurde nicht angegeben.|
> |**Name**:<br />QueryBuilderAttributePairMismatch<br />**Hex**:<br />80041111<br />**Nummer**:<br />-2147217135|AttributeFrom und AttributeTo müssen entweder beide angegeben oder weggelassen werden.|
> |**Name**:<br />QueryBuilderAttributeRequiredForNonAggregateOrderBy<br />**Hex**:<br />80041133<br />**Nummer**:<br />-2147217101|Ein Attribut ist für eine Auftragsklausel für eine nicht Aggregat-Abfrage erforderlich.|
> |**Name**:<br />QueryBuilderBad_Condition<br />**Hex**:<br />80041106<br />**Nummer**:<br />-2147217146|Falsche Filterbedingung oder -anforderungen.|
> |**Name**:<br />QueryBuilderByAttributeMismatch<br />**Hex**:<br />8004110f<br />**Nummer**:<br />-2147217137|QueryByAttribute muss ein nicht-leeres Wertarray mit der gleichen Anzahl von Elementen wie im Attributarray angeben.|
> |**Name**:<br />QueryBuilderByAttributeNonEmpty<br />**Hex**:<br />80041110<br />**Nummer**:<br />-2147217136|QueryByAttribute muss ein leeres Attributarray definieren.|
> |**Name**:<br />QueryBuilderColumnSetVersionMissing<br />**Hex**:<br />80041113<br />**Nummer**:<br />-2147217133|Die angegebene Columnset-Version ist ungültig.|
> |**Name**:<br />QueryBuilderDeserializeEmptyXml<br />**Hex**:<br />80041124<br />**Nummer**:<br />-2147217116|XML-Zeichenfolge kann nicht gültig sein.|
> |**Name**:<br />QueryBuilderDeserializeInvalidAggregate<br />**Hex**:<br />8004111a<br />**Nummer**:<br />-2147217126|Fehler beim Verarbeiten von Aggregaten in der Abfrage|
> |**Name**:<br />QueryBuilderDeserializeInvalidDescending<br />**Hex**:<br />80041119<br />**Nummer**:<br />-2147217127|Der einzige gültige Werte für absteigende Attribut sind "True", "false ", "1 "und "0 ".|
> |**Name**:<br />QueryBuilderDeserializeInvalidDistinct<br />**Hex**:<br />80041115<br />**Nummer**:<br />-2147217131|Die einzigen gültigen Werte für ausgewählte Attribute sind "True", "false ", "1 "und "0 ".|
> |**Name**:<br />QueryBuilderDeserializeInvalidGetMinActiveRowVersion<br />**Hex**:<br />8004111b<br />**Nummer**:<br />-2147217125|Die einzigen gültigen Werte für  GetMinActiveRowVersion Attribute sind "True", "false ", "1 "und "0 ".|
> |**Name**:<br />QueryBuilderDeserializeInvalidGroupBy<br />**Hex**:<br />8004112E<br />**Nummer**:<br />-2147217106|Die einzigen gültigen Werte für groupby Attribute sind "True", "false ", "1 "und "0 ".|
> |**Name**:<br />QueryBuilderDeserializeInvalidLinkType<br />**Hex**:<br />80041117<br />**Nummer**:<br />-2147217129|Der einzige gültige Wert für verknüpfte Attribute sind „natürlich”, „innere”, „in”, „vorhanden”, „matchfirstrowusingcrossapply” und „äußere”.|
> |**Name**:<br />QueryBuilderDeserializeInvalidMapping<br />**Hex**:<br />80041116<br />**Nummer**:<br />-2147217130|Der einzige gültige Werte zum Zuordnen sind "logisch"oder "intern", die veraltet sind.|
> |**Name**:<br />QueryBuilderDeserializeInvalidNode<br />**Hex**:<br />8004111c<br />**Nummer**:<br />-2147217124|Der Elementknoten ist ungültig.|
> |**Name**:<br />QueryBuilderDeserializeInvalidNoLock<br />**Hex**:<br />80041118<br />**Nummer**:<br />-2147217128|Die einzigen gültigen Werte für nicht gesperrte Attribute sind "True", "false ", "1 "und "0 ".|
> |**Name**:<br />QueryBuilderDeserializeInvalidUseRawOrderBy<br />**Hex**:<br />800410fd<br />**Nummer**:<br />-2147217155|Der einzige gültige Werte für das Attribut useraworderby sind „true”, „false”, „1” und „0”.|
> |**Name**:<br />QueryBuilderDeserializeInvalidUtcOffset<br />**Hex**:<br />8004111d<br />**Nummer**:<br />-2147217123|Das UTC Offset Attribut wird für Deserialisierung unterstützt.|
> |**Name**:<br />QueryBuilderDeserializeNoDocElemXml<br />**Hex**:<br />80041125<br />**Nummer**:<br />-2147217115|Dokument-Element kann nicht "Null" sein.|
> |**Name**:<br />QueryBuilderDuplicateAlias<br />**Hex**:<br />80041130<br />**Nummer**:<br />-2147217104|FetchXML sollte eindeutige Alias haben.|
> |**Name**:<br />QueryBuilderElementNotFound<br />**Hex**:<br />80041123<br />**Nummer**:<br />-2147217117|Ein erforderliches Element wurde nicht angegeben.|
> |**Name**:<br />QueryBuilderEntitiesDontMatch<br />**Hex**:<br />80041128<br />**Nummer**:<br />-2147217112|Der Entitätsname, der im fetchxml angegeben wurd, entspricht nicht dem Entitätsnamen, der in der Entität oder im Abfrageausdruck angegeben ist.|
> |**Name**:<br />QueryBuilderInvalid_Alias<br />**Hex**:<br />80041109<br />**Nummer**:<br />-2147217143|Ungültiger Alias für der Aggragatvorgang.|
> |**Name**:<br />QueryBuilderInvalid_Value<br />**Hex**:<br />80041108<br />**Nummer**:<br />-2147217144|Ungültiger Wert für Typ angegeben.|
> |**Name**:<br />QueryBuilderInvalidAggregateAttribute<br />**Hex**:<br />8004112F<br />**Nummer**:<br />-2147217105|Aggregat {0} wird nicht für ein Attribut vom Typ {1} unterstützt.|
> |**Name**:<br />QueryBuilderInvalidAttributeValue<br />**Hex**:<br />80041139<br />**Nummer**:<br />-2147217095|Der Wert für das Attribut  ist ungültig.|
> |**Name**:<br />QueryBuilderInvalidColumnSetVersion<br />**Hex**:<br />80041112<br />**Nummer**:<br />-2147217134|Die angegebene Columnset-Version ist ungültig.|
> |**Name**:<br />QueryBuilderInvalidConditionOperator<br />**Hex**:<br />80041120<br />**Nummer**:<br />-2147217120|Nicht unterstützter Bedingungsoperator.|
> |**Name**:<br />QueryBuilderInvalidDateGrouping<br />**Hex**:<br />80041135<br />**Nummer**:<br />-2147217099|Ein ungültiger Wert wurde für die Datumsgruppierung angegeben.|
> |**Name**:<br />QueryBuilderInvalidFilterType<br />**Hex**:<br />80041122<br />**Nummer**:<br />-2147217118|Nicht unterstützter Filtertyp. Gültige Werte sind 'und' oder  'oder .|
> |**Name**:<br />QueryBuilderInvalidJoinOperator<br />**Hex**:<br />80041121<br />**Nummer**:<br />-2147217119|Nicht unterstützter gemeinsamer Operator.|
> |**Name**:<br />QueryBuilderInvalidLogicalOperator<br />**Hex**:<br />800410fe<br />**Nummer**:<br />-2147217154|Nicht unterstützter logischer Operator {0}  Akzeptierte Werte sind ("und", "oder").|
> |**Name**:<br />QueryBuilderInvalidOrderType<br />**Hex**:<br />8004111f<br />**Nummer**:<br />-2147217121|Ein gültiger Auftragstyp muss in der Reihenfolge festgelegt werden, bevor diese Methode aufgerufen werden kann.|
> |**Name**:<br />QueryBuilderInvalidPagingCookie<br />**Hex**:<br />8004112A<br />**Nummer**:<br />-2147217110|Ungültige Seitenzahl im Auslagerungscookie.|
> |**Name**:<br />QueryBuilderInvalidUpdate<br />**Hex**:<br />80041100<br />**Nummer**:<br />-2147217152|Es wurde versucht ein nicht-aktualisierbares Feld zu aktualisieren.|
> |**Name**:<br />QueryBuilderLinkNodeForOrderNotFound<br />**Hex**:<br />80041126<br />**Nummer**:<br />-2147217114|Das Konvertieren von der Abfrage zu EntityExpression ist fehlgeschlagen. Link-Knoten für Auftrag wurde nicht gefunden.|
> |**Name**:<br />QueryBuilderMultipleIntersectEntities<br />**Hex**:<br />8004110e<br />**Nummer**:<br />-2147217138|Mehr als eine überschneidende Entität ist zwischen den beiden angegebenen Entitäten vorhanden.|
> |**Name**:<br />QueryBuilderNoAlias<br />**Hex**:<br />8004110b<br />**Nummer**:<br />-2147217141|Kein Alias für die angegebene Entität in der Bedingung gefunden.|
> |**Name**:<br />QueryBuilderNoAttribute<br />**Hex**:<br />80041103<br />**Nummer**:<br />-2147217149|Das definierte Attribut ist bei dieser Entität nicht vorhanden.|
> |**Name**:<br />QueryBuilderNoAttrsDistinctConflict<br />**Hex**:<br />8004112C<br />**Nummer**:<br />-2147217108|Das no-attrs Tag kann nicht zusammen mit eindeutigem Wert auf true festlegen werden.|
> |**Name**:<br />QueryBuilderNoEntity<br />**Hex**:<br />80041102<br />**Nummer**:<br />-2147217150|Die angegebene Entität wurde nicht gefunden.|
> |**Name**:<br />QueryBuilderNoEntityKey<br />**Hex**:<br />80041140<br />**Nummer**:<br />-2147217088|Der angegebene entitykey wurde nicht gefunden.|
> |**Name**:<br />QueryBuilderPagingOrderBy<br />**Hex**:<br />80041129<br />**Nummer**:<br />-2147217111|Reihenfolge nach Spalten passt nicht zu jenen im anrufenden Cookie.|
> |**Name**:<br />QueryBuilderReportView_Does_Not_Exist<br />**Hex**:<br />8004110d<br />**Nummer**:<br />-2147217139|Eine Berichtsansicht ist nicht für die angegebene Entität vorhanden.|
> |**Name**:<br />QueryBuilderSerializationInvalidIsQuickFindFilter<br />**Hex**:<br />80041138<br />**Nummer**:<br />-2147217096|Die einzigen gültige Werte für isquickfindfields Attribute sind "True", "false ", "1 "und "0 ".|
> |**Name**:<br />QueryBuilderSerialzeLinkTopCriteria<br />**Hex**:<br />80041114<br />**Nummer**:<br />-2147217132|Fetch unterstützt keine "where"-Klausel mit Bedingungen von "linkentity".|
> |**Name**:<br />QueryBuilderUnexpected<br />**Hex**:<br />80041101<br />**Nummer**:<br />-2147217151|Unerwarteter Fehler.|
> |**Name**:<br />QueryBuilderValue_GreaterThanZero<br />**Hex**:<br />8004110c<br />**Nummer**:<br />-2147217140|Ein Wert größer als null muss angegeben werden.|
> |**Name**:<br />QueryContainedSecuredAttributeWithoutAccess<br />**Hex**:<br />8004F506<br />**Nummer**:<br />-2147158778|Die Abfrage enthielt ein geschütztes Attribut, auf das der Anrufer keinen Zugriff hat|
> |**Name**:<br />QueryFilterConditionAttributeNotPresentInExpressionEntity<br />**Hex**:<br />80071119<br />**Nummer**:<br />-2147020519|Die Abfrage verweist auf ein Feld, dass in Dynamics 365 nicht vorhanden ist: "{0}"|
> |**Name**:<br />QueryNotValidForStaticList<br />**Hex**:<br />8004F702<br />**Nummer**:<br />-2147158270|Abfrage kann für eine statische Liste nicht angegeben werden.|
> |**Name**:<br />QueryParameterNotUnique<br />**Hex**:<br />8005E00B<br />**Nummer**:<br />-2147098613|Abfrageparameter {0} muss nur einmal innerhalb des Datensatzes festgelegt werden.|
> |**Name**:<br />QueueIdNotPresent<br />**Hex**:<br />80040528<br />**Nummer**:<br />-2147220184|Sie müssen die Zielwarteschlange eingeben. Geben Sie einen gültigen Wert in die Warteschlange ein, und wiederholen Sie den Vorgang.|
> |**Name**:<br />QueueItemNotPresent<br />**Hex**:<br />80040529<br />**Nummer**:<br />-2147220183|Geben Sie den Namen des Datensatzes an, den Sie der Warteschlangen hinzufügen möchten. Geben Sie einen gültigen Wert im Warteschlangenelement ein, und wiederholen Sie den Vorgang.|
> |**Name**:<br />QueueMailboxUnexpectedDeliveryMethod<br />**Hex**:<br />8005E210<br />**Nummer**:<br />-2147098096|Die Zustellungsmethode für das Postfach, das einer Warteschlange zugeordnet ist, kann nicht Outlook-Client sein.|
> |**Name**:<br />QuickCreateDisabledOnEntity<br />**Hex**:<br />80060911<br />**Nummer**:<br />-2147088111|Die {0}-Entität weist kein Formular für die Schnellerfassung auf, oder die Anzahl der geschachtelten Formulare für die Schnellerfassung überschreitet die zulässige Höchstanzahl.|
> |**Name**:<br />QuickCreateInvalidEntityName<br />**Hex**:<br />80060910<br />**Nummer**:<br />-2147088112|Der entityLogicalName ist ungültig. Der Wert kann Null oder leer sein und muss eine Entität in der Organisation darstellen.|
> |**Name**:<br />QuickFindQueryRecordLimitExceeded<br />**Hex**:<br />8004E024<br />**Nummer**:<br />-2147164124|QuickFindQueryRecordLimit überstiegen. Kann diesen Vorgang nicht ausführen.|
> |**Name**:<br />QuickFindSavedQueryAlreadyExists<br />**Hex**:<br />8004853A<br />**Nummer**:<br />-2147187398|"Nur eine quickfind-gespeicherte Abfrage kann für eine Entität vorhanden sind. Es existiert bereits eine QuickSuche gespeicherte Abfrage für Entität mit objecttypecode: {0}"|
> |**Name**:<br />QuickFormNotCustomizableThroughSdk<br />**Hex**:<br />8004F659<br />**Nummer**:<br />-2147158439|SDK unterstützt das Erstellen von einem Formular des Tpys "Quick" nicht. Dieser Formtyp dient nur zur internen Verwendung.|
> |**Name**:<br />QuoteAndSalesOrderCurrencyNotEqual<br />**Hex**:<br />80048cee<br />**Nummer**:<br />-2147185426|Die Währung des Datensatz aus entspricht nicht der Währung der Preisliste.|
> |**Name**:<br />QuoteReviseExistingActiveQuote<br />**Hex**:<br />80048d00<br />**Nummer**:<br />-2147185408|Angebot kann nicht überarbeitet werden, da bereits ein anderes Angebot im Status „Entwurf/Aktiv” mit derselben Angebotsnummer vorhanden ist.|
> |**Name**:<br />ReactivateEntityKeyOnlyForFailedJobs<br />**Hex**:<br />80060897<br />**Nummer**:<br />-2147088233|Das Reaktivieren des Entitätsschlüssels wird nur für fehlerhafte Aufträge unterstützt.|
> |**Name**:<br />ReadIntentIncompatible<br />**Hex**:<br />80060881<br />**Nummer**:<br />-2147088255|Steckbare Ausführungs-Absicht des aktuellen Ausführungskontexts ist nicht mit den übergeordneten Kontext kompatibel|
> |**Name**:<br />ReadOnlyCreateValidationFailed<br />**Hex**:<br />80061002<br />**Nummer**:<br />-2147086334|Sie können keinen Wert für eine Eigenschafteninstanz für eine schreibgeschützte Eigenschaft erstellen und zuweisen.|
> |**Name**:<br />ReadOnlyUpdateValidationFailed<br />**Hex**:<br />80061003<br />**Nummer**:<br />-2147086333|Sie können keine Eigenschaftinstanz für eine schreibgeschützte Eigenschaft aktualisieren.|
> |**Name**:<br />ReadOnlyUserNotSupported<br />**Hex**:<br />80041d40<br />**Nummer**:<br />-2147214016|Die schreibgeschützten Zugriff wird nicht unterstützt|
> |**Name**:<br />RecalculateNotSupportedOnNonRollupField<br />**Hex**:<br />80060554<br />**Nummer**:<br />-2147089068|Feld {0} vom Typ {1} unterstützt keine "Recalculate"-Aktion. Neuberechnen von Aktion kann nur für Rollupfeld aufgerufen werden.|
> |**Name**:<br />RecommendationAzureConnectionCascadeActivateFailed<br />**Hex**:<br />80061633<br />**Nummer**:<br />-2147084749|Mindestens ein Empfehlungsmodell kann nicht aktiviert werden. Versuchen Sie, die vorhandenen Empfehlungsmodelle separat zu aktivieren von der Azure Service-Verbindung.|
> |**Name**:<br />RecommendationAzureConnectionFailed<br />**Hex**:<br />80061631<br />**Nummer**:<br />-2147084751|Fehler beim Herstellen einer Verbindung mit dem Azure-Dienst "Empfehlungen". Überprüfen Sie, ob die URL und der Azure-Firmenschlüssel gültig sind und das Serviceabonnement aktiv ist.|
> |**Name**:<br />RecommendationModelActivateConnectionMustBeActive<br />**Hex**:<br />80061607<br />**Nummer**:<br />-2147084793|Die Azure Machine Learing Empfehlungs-Service-Empfehlung muss aktiviert sein, bevor ein Modell erstellt werden kann. Aktivieren Sie die Verbindung zu den Service Azure Machine Learning-Empfehlungen und versuchen Sie es erneut.|
> |**Name**:<br />RecommendationModelActiveVersionInvalidStatus<br />**Hex**:<br />80061602<br />**Nummer**:<br />-2147084798|Die Musterversion muss erfolgreich erstellt werden, bevor das Modell aktiviert werden kann.|
> |**Name**:<br />RecommendationModelActiveVersionNotSet<br />**Hex**:<br />80061601<br />**Nummer**:<br />-2147084799|Die  Musterversion, die verwendet wird, ist leer. Um das Modell zu aktivieren, definieren Sie die Modellversion.|
> |**Name**:<br />RecommendationModelBuildConnectionMustBeActive<br />**Hex**:<br />80061606<br />**Nummer**:<br />-2147084794|Die Azure Machine Learing Empfehlungs-Service-Empfehlung muss aktiviert sein, bevor ein Empfehlungsmodell erstellt werden kann. Aktivieren Sie die Verbindung zu den Service Azure Machine Learning-Empfehlungen und versuchen Sie es erneut.|
> |**Name**:<br />RecommendationModelExpired<br />**Hex**:<br />80061608<br />**Nummer**:<br />-2147084792|Das Empfehlungsmodell ist abgelaufen. Ändern Sie das "Gültig bis"-Datum und versuchen Sie, das Model erneut zu aktivieren.|
> |**Name**:<br />RecommendationModelMappingDuplicateRecord<br />**Hex**:<br />80061610<br />**Nummer**:<br />-2147084784|Der Empfehlungsmodell-Zuordnungswerte Kartentyp für Entität, Zuordnungstyp und Version müssen eindeutig sein.|
> |**Name**:<br />RecommendationModelMappingReadOnly<br />**Hex**:<br />80061611<br />**Nummer**:<br />-2147084783|Sie können eine Empfehlungsentität nicht ändern, wenn eine entsprechende Warenkorbentität vorhanden ist.|
> |**Name**:<br />RecommendationModelVersionActive<br />**Hex**:<br />80061620<br />**Nummer**:<br />-2147084768|Die RecommendationModel-Version wird als aktive Version für ein Modell behandelt und kann nicht gelöscht werden.|
> |**Name**:<br />RecommendationModelVersionBuildInProgress<br />**Hex**:<br />80061621<br />**Nummer**:<br />-2147084767|Ein Workflow zum Erstellen des Modells läuft bereits. Sie können keinen anderen Buildworkflow starten, bis der aktuelle Workflows abgeschlossen ist.|
> |**Name**:<br />RecommendationModelVersionDuplicateName<br />**Hex**:<br />80061622<br />**Nummer**:<br />-2147084766|Eine Modelversion mit demselben Namen ist bereits vorhanden. Geben Sie einen anderen Namen an.|
> |**Name**:<br />RecommendationsUnavailable<br />**Hex**:<br />80061605<br />**Nummer**:<br />-2147084795|Produktempfehlungen für Azure-Machine Learning sind vorübergehend nicht verfügbar. Nur Katalogempfehlungen sind verfügbar.|
> |**Name**:<br />RecommendedDocumentsRetrievalFailure<br />**Hex**:<br />80071015<br />**Nummer**:<br />-2147020779|Fehler beim Abrufen von Dokumentvorschlägen aus der Dokumentquelle.|
> |**Name**:<br />RecommendedDocumentsRetrievalFailureWhenSPSiteNotConfigured<br />**Hex**:<br />80071028<br />**Nummer**:<br />-2147020760|Fehler beim Abrufen von Dokumentvorschlägen aus der Dokumentquelle.|
> |**Name**:<br />RecordAndOpportunityCurrencyNotEqual<br />**Hex**:<br />80048cef<br />**Nummer**:<br />-2147185425|Die Währung des Datensatz aus entspricht nicht der Währung der Preisliste.|
> |**Name**:<br />RecordAndPricelistCurrencyNotEqual<br />**Hex**:<br />80048cf6<br />**Nummer**:<br />-2147185418|Die Währung des Datensatz aus entspricht nicht der Währung der Preisliste.|
> |**Name**:<br />RecordCanOnlyBeRevisedFromActiveState<br />**Hex**:<br />8004F883<br />**Nummer**:<br />-2147157885|Sie können nur ein aktives Produkt überarbeiten.|
> |**Name**:<br />RecordCountExceededForExcelOnlineError<br />**Hex**:<br />80072456<br />**Nummer**:<br />-2147015594|Anzahl der erwarteten Datensätze ist {0}. Anzahl der aktuellen Datensätze ist: {1}|
> |**Name**:<br />RecordNotFoundByEntityKey<br />**Hex**:<br />80060891<br />**Nummer**:<br />-2147088239|Ein Datensatz mit den angegebenen Schlüsselwerten befindet sich nicht in der {0} Entität|
> |**Name**:<br />RecordResolutionFailed<br />**Hex**:<br />8004F603<br />**Nummer**:<br />-2147158525|Der Datensatz konnte nicht aktualisiert werden, da der ursprüngliche Datensatz nicht mehr in Microsoft Dynamics 365 vorhanden ist.|
> |**Name**:<br />RecurrenceCalendarTypeNotSupported<br />**Hex**:<br />8004E116<br />**Nummer**:<br />-2147163882|Der Kalendertyp wird nicht unterstützt.|
> |**Name**:<br />RecurrenceEndDateTooBig<br />**Hex**:<br />8004E119<br />**Nummer**:<br />-2147163879|Das Serienmusterenddatum ist ungültig.|
> |**Name**:<br />RecurrenceHasNoOccurrence<br />**Hex**:<br />8004E117<br />**Nummer**:<br />-2147163881|Das Wiederholungsmuster hat keine Einträge.|
> |**Name**:<br />RecurrenceRuleDeleteFailure<br />**Hex**:<br />8004E111<br />**Nummer**:<br />-2147163887|Eine Regel, die einem vorhandenen Regelmaster angefügt ist, kann nicht gelöscht werden. Löschen Sie die Regel, indem Sie die übergeordnete Entität verwenden.|
> |**Name**:<br />RecurrenceRuleUpdateFailure<br />**Hex**:<br />8004E110<br />**Nummer**:<br />-2147163888|Eine Regel, die einem vorhandenen Regelmaster angefügt ist, kann nicht aktualisiert werden. Aktualisieren Sie die Regel, indem Sie die übergeordnete Entität verwenden.|
> |**Name**:<br />RecurrenceStartDateTooSmall<br />**Hex**:<br />8004E118<br />**Nummer**:<br />-2147163880|Das Serienmusterstartdatum ist ungültig.|
> |**Name**:<br />RecurringSeriesCompleted<br />**Hex**:<br />8004E10B<br />**Nummer**:<br />-2147163893|Der ExpansionStateCode hat eine ungültige Serie.|
> |**Name**:<br />RecurringSeriesMasterIsLocked<br />**Hex**:<br />8004E113<br />**Nummer**:<br />-2147163885|Der übergeordnete Stammdatensatz der Wiederholungsregel wird durch einen anderen Prozess gesperrt.|
> |**Name**:<br />RefEntityRelationshipRoleRequired<br />**Hex**:<br />80048470<br />**Nummer**:<br />-2147187600|Die Entitätsbeziehungsrolle der sich darauf beziehenden Datei ist erforderlich, wenn Sie eine neue Ein-zu-Vielen-Entitätsbeziehung erstellen.|
> |**Name**:<br />ReferencedEntityHasLogicalPrimaryNameField<br />**Hex**:<br />8004432E<br />**Nummer**:<br />-2147204306|Die Entität hat ein primäres Feld, das logische ist und deshalb nicht die referenzierte Entität in einer 1: n-Beziehung sein kann.|
> |**Name**:<br />ReferencedEntityMustHaveLookupView<br />**Hex**:<br />80044337<br />**Nummer**:<br />-2147204297|Referenzierte Entitäten eine Beziehung muss eine Suchansicht verfügen|
> |**Name**:<br />ReferencingEntityCannotBeSolutionAware<br />**Hex**:<br />80044350<br />**Nummer**:<br />-2147204272|Auf Entitäten in einer Beziehung zu verweisen kann eine Komponente in einer Lösung werden.|
> |**Name**:<br />ReferencingEntityMustHaveAssociationView<br />**Hex**:<br />80044338<br />**Nummer**:<br />-2147204296|Referenzierte Entitäten einer Beziehung muss über eine Suchansicht verfügen|
> |**Name**:<br />RefferedSolutionIsDifferent<br />**Hex**:<br />80050122<br />**Nummer**:<br />-2147155678|Unveröffentlichte Zeile außerhalb der aktiven Lösung gefunden: SiteMapId = {0}, SolutionId = {1}|
> |**Name**:<br />ReflexiveEntityParentOrChildDoesNotExist<br />**Hex**:<br />80040388<br />**Nummer**:<br />-2147220600|Entweder die übergeordnete oder untergeordnete Entität ist nicht vorhanden|
> |**Name**:<br />RefRoleNavPaneDisplayOptionRequired<br />**Hex**:<br />80060898<br />**Nummer**:<br />-2147088232|Das NavPaneDisplayOptions-Attribut ist für eine verweisende Rolle einer Eins-zu-Vielen-Beziehung erforderlich {0}.|
> |**Name**:<br />RegardingObjectValuesRetrievalFailure<br />**Hex**:<br />80071012<br />**Nummer**:<br />-2147020782|Fehler beim Abrufen der Bezugsobjektwerte.|
> |**Name**:<br />RelatedEntityAlreadyExistsInProfile<br />**Hex**:<br />8005F21e<br />**Nummer**:<br />-2147093986|Die verknüpfte Entität ist bereits in diesem Profil vorhanden.|
> |**Name**:<br />RelatedEntityDoesNotExistInProfileItem<br />**Hex**:<br />8006098E<br />**Nummer**:<br />-2147087986|Die verknüpfte Entität {0} der Mobile Offline-Profilelementzuordnung {1} des Mobile Offline-Profilelements {2} ist in den Profilelementen des Profils {3} nicht vorhanden.|
> |**Name**:<br />RelatedEntityDoesNotExistsInProfile<br />**Hex**:<br />8005F21f<br />**Nummer**:<br />-2147093985|Die verknüpfte Entität ist nicht in den Profilelementen vorhanden.|
> |**Name**:<br />RelatedEntityGenericError<br />**Hex**:<br />8005F220<br />**Nummer**:<br />-2147093984|Während der Erstellung der Profilzuordnung ist ein unerwarteter Fehler aufgetreten. Bitte wiederholen Sie den Vorgang.|
> |**Name**:<br />RelatedRecordsFailure<br />**Hex**:<br />80071013<br />**Nummer**:<br />-2147020781|Fehler beim Abrufen zugehöriger Datensätze.|
> |**Name**:<br />RelationshipGraphLimitExceeded<br />**Hex**:<br />80071139<br />**Nummer**:<br />-2147020487|Sie haben mindestens eine Profilelementzuordnung für die Entitäten festgelegt, die im Profil „{0}” definiert werden. Bitte prüfen Sie die Profilelementzuordnungen, welche die Entität „{1}” beinhalten, die eine Zuordnungsanzahl von {2} haben und das unterstützte Limit von {3} übersteigen.|
> |**Name**:<br />RelationshipInsightsFeatureDisableError<br />**Hex**:<br />80044292<br />**Nummer**:<br />-2147204462|Die Funktion für Beziehungsinformationen kann nicht deaktiviert werden|
> |**Name**:<br />RelationshipInsightsFeatureNotEnabledError<br />**Hex**:<br />80044293<br />**Nummer**:<br />-2147204461|Die Beziehungserkenntnisfunktion ist nicht aktiviert oder das RI-Paket ist nicht installiert|
> |**Name**:<br />RelationshipIntelligenceSDKInvocationError<br />**Hex**:<br />80044276<br />**Nummer**:<br />-2147204490|Für das SDK für Beziehungsinformationen ist Dynamics 365 (online) erforderlich.|
> |**Name**:<br />RelationshipIsNotCustomRelationship<br />**Hex**:<br />8004700a<br />**Nummer**:<br />-2147192822|Die angegebene Beziehung ist keine benutzerdefinierte Beziehung|
> |**Name**:<br />RelationshipNameLengthExceedsLimit<br />**Hex**:<br />8004802A<br />**Nummer**:<br />-2147188694|Bezeichner dürfen aus maximal {1} Zeichen bestehen. Die Länge des angegebenen Namens {0} ist größer als die maximale Länge von {1} Zeichen.|
> |**Name**:<br />RelationshipNotCreatedForOfficeGraphError<br />**Hex**:<br />80044235<br />**Nummer**:<br />-2147204555|Diese Beziehung kann nicht erstellt werden, da keine Entität für Office Graph aktiviert ist.|
> |**Name**:<br />RelationshipNotUpdatedForOfficeGraphError<br />**Hex**:<br />80044236<br />**Nummer**:<br />-2147204554|Diese Beziehung kann für Office Graph nicht aktualisiert werden, da keine Entität für Office Graph aktiviert ist.|
> |**Name**:<br />RelationshipRoleMismatch<br />**Hex**:<br />80048467<br />**Nummer**:<br />-2147187609|Die Geschäftsbeziehungsrollen-Namen {0} entspricht nicht dem erwarteten Entitätsnamen von {1} oder {2}.|
> |**Name**:<br />RelationshipRoleNodeNumberInvalid<br />**Hex**:<br />80048469<br />**Nummer**:<br />-2147187607|Es müssen zwei Knoten mit Entitätsbeziehungen geben, falls eine neue n: n-Entitätsbeziehung erstellt wird.|
> |**Name**:<br />RelatioshipAlreadyExists<br />**Hex**:<br />8005F221<br />**Nummer**:<br />-2147093983|Ausgewählte Beziehung für Entität ist bereits in diesem Profil vorhanden. |
> |**Name**:<br />ReportDoesNotExist<br />**Hex**:<br />80040499<br />**Nummer**:<br />-2147220327|Bericht ist nicht vorhanden. reportid:{0}|
> |**Name**:<br />ReportFileTooBig<br />**Hex**:<br />80048297<br />**Nummer**:<br />-2147188073|Die Datei ist zu groß und kann nicht hochgeladen werden. Verringern Sie die Größe der Datei und versuchen Sie es anschließend erneut.|
> |**Name**:<br />ReportFileZeroLength<br />**Hex**:<br />80048296<br />**Nummer**:<br />-2147188074|Sie haben eine leere Datei hochgeladen.  Wählen Sie eine neue Datei aus, und versuchen Sie es noch mal.|
> |**Name**:<br />ReportImportCategoryOptionNotFound<br />**Hex**:<br />8004F028<br />**Nummer**:<br />-2147160024|Eine Kategorieoption für die Berichte wurde nicht gefunden.|
> |**Name**:<br />ReportingServicesReportExpected<br />**Hex**:<br />80040484<br />**Nummer**:<br />-2147220348|Der Bericht ist kein Reporting Services-Bericht.|
> |**Name**:<br />ReportLocalProcessingError<br />**Hex**:<br />80048310<br />**Nummer**:<br />-2147187952|Fehler beim Anzeigen eines lokal verarbeiteten Berichts. reportid:{0}|
> |**Name**:<br />ReportLoopBeingCreated<br />**Hex**:<br />80040498<br />**Nummer**:<br />-2147220328|Durch das Erstellen dieser übergeordneten Zuordnung würde eine Schleife in der Hierarchie „Berichte” erstellt werden.|
> |**Name**:<br />ReportLoopExists<br />**Hex**:<br />80040497<br />**Nummer**:<br />-2147220329|Schleife ist in der Meldungshierarchie vorhanden.|
> |**Name**:<br />ReportMissingDataSourceCredentialsError<br />**Hex**:<br />80048311<br />**Nummer**:<br />-2147187951|Für eine vom Bericht verwendete Datenquelle wurden keine Anmeldeinformationen angegeben.  reportid:{0}|
> |**Name**:<br />ReportMissingDataSourceError<br />**Hex**:<br />80048312<br />**Nummer**:<br />-2147187950|Eine vom Bericht erwartete Datenquelle wurde nicht bereitgestellt.  reportid:{0}|
> |**Name**:<br />ReportMissingEndpointError<br />**Hex**:<br />80048313<br />**Nummer**:<br />-2147187949|Auf den vom ReportViewer-Steuerelement verwendeten SOAP-Endpunkt konnte nicht zugegriffen werden. |
> |**Name**:<br />ReportMissingParameterError<br />**Hex**:<br />80048314<br />**Nummer**:<br />-2147187948|Ein vom Bericht erwarteter Parameter wurde nicht bereitgestellt. reportid:{0}|
> |**Name**:<br />ReportMissingReportSourceError<br />**Hex**:<br />80048315<br />**Nummer**:<br />-2147187947|Für den Bericht wurde keine Quelle angegeben.  reportid:{0}|
> |**Name**:<br />ReportNotAvailable<br />**Hex**:<br />80048299<br />**Nummer**:<br />-2147188071|Der Bericht ist nicht verfügbar|
> |**Name**:<br />ReportParentChildNotCustomizable<br />**Hex**:<br />8004832f<br />**Nummer**:<br />-2147187921|Der Bericht konnte nicht aktualisiert werden, da entweder der übergeordnete oder der untergeordnete Bericht nicht angepasst werden kann.|
> |**Name**:<br />ReportRdlSandboxing<br />**Hex**:<br />80048293<br />**Nummer**:<br />-2147188077|Berichtsupload ist wegen RDL-Sandkasten-Begrenzung auf dem Berichtsserver fehlgeschlagen.|
> |**Name**:<br />ReportRenderError<br />**Hex**:<br />80040494<br />**Nummer**:<br />-2147220332|Ein Fehler beim Berichtsrendering ist aufgetreten.|
> |**Name**:<br />ReportSecurityError<br />**Hex**:<br />80048316<br />**Nummer**:<br />-2147187946|Im Bericht enthält eine Sicherheitsverletzung. reportid:{0}|
> |**Name**:<br />ReportServerInvalidUrl<br />**Hex**:<br />80048301<br />**Nummer**:<br />-2147187967|Berichtsserver kann von der betreffenden URL nicht kontaktiert werden|
> |**Name**:<br />ReportServerNoPrivilege<br />**Hex**:<br />80048302<br />**Nummer**:<br />-2147187966|Kein ausreichendes Recht zum Konfigurieren des Berichtsservers|
> |**Name**:<br />ReportServerSP2HotFixNotApplied<br />**Hex**:<br />80048309<br />**Nummer**:<br />-2147187959|Berichtsserver SP2-Arbeitsgruppe hat nicht die Hotfix für Rollen-Erstellung|
> |**Name**:<br />ReportServerUnknownException<br />**Hex**:<br />80048300<br />**Nummer**:<br />-2147187968|Unbekannte Ausnahme ausgelöst vom Berichtsserver|
> |**Name**:<br />ReportServerVersionLow<br />**Hex**:<br />80048303<br />**Nummer**:<br />-2147187965|Berichtsserver erfüllt nicht die minimale Versionsbedingung|
> |**Name**:<br />ReportTypeBlocked<br />**Hex**:<br />80048295<br />**Nummer**:<br />-2147188075|Der Bericht ist kein gültiger Typ.  Es kann nicht heruntergeladen oder hochgeladen werden.|
> |**Name**:<br />ReportUploadDisabled<br />**Hex**:<br />80048294<br />**Nummer**:<br />-2147188076|Reporting Services-Berichte können nicht hochgeladen werden. Wenn Sie einen neuen Bericht erstellen möchten, verwenden Sie den Berichts-Assistenten.|
> |**Name**:<br />ReportViewerError<br />**Hex**:<br />8004832c<br />**Nummer**:<br />-2147187924|Ein Fehler beim Berichtsrendering ist aufgetreten. reportid:{0}|
> |**Name**:<br />RequestIsNotAuthenticated<br />**Hex**:<br />80044302<br />**Nummer**:<br />-2147204350|Anforderung ist nicht authentifiziert.|
> |**Name**:<br />RequestLengthTooLarge<br />**Hex**:<br />8004418a<br />**Nummer**:<br />-2147204726|AnforderungsNachrichtenlänge ist zu groß.|
> |**Name**:<br />RequiredBundleItemCannotBeUpdated<br />**Hex**:<br />80081009<br />**Nummer**:<br />-2146955255|Sie können dieses Paketelement nicht löschen, weil es ein erforderliches Produkt im Paket ist.|
> |**Name**:<br />RequiredBundleProductCannotBeDeleted<br />**Hex**:<br />80081008<br />**Nummer**:<br />-2146955256|Sie können diesen Produktdatensatz nicht löschen, weil er ein erforderliches Produkt in einem Paket ist.|
> |**Name**:<br />RequiredChildReportHasOtherParent<br />**Hex**:<br />8004F029<br />**Nummer**:<br />-2147160023|Eine Kategorieoption für die Berichte wurde nicht gefunden.|
> |**Name**:<br />RequiredColumnsNotFoundInImportFile<br />**Hex**:<br />80040383<br />**Nummer**:<br />-2147220605|Mindestens eine Quellspalte, die in der Transformation verwendet wird, existiert nicht in der Quelldatei.|
> |**Name**:<br />RequiredFieldMissing<br />**Hex**:<br />80040200<br />**Nummer**:<br />-2147220992|Fehlendes Pflichtfeld.|
> |**Name**:<br />RequiredProcessStepIsNull<br />**Hex**:<br />8006041a<br />**Nummer**:<br />-2147089382|Führen Sie die erforderlichen Schritte aus, um zur nächsten Phase zu gelangen.|
> |**Name**:<br />RequireValidImportMapForUpdate<br />**Hex**:<br />8004F600<br />**Nummer**:<br />-2147158528|Der Updatevorgang kann nicht beendet werden, da die für das Update verwendete Importzuordnung ungültig ist.|
> |**Name**:<br />RestrictedSolutionName<br />**Hex**:<br />8004F022<br />**Nummer**:<br />-2147160030|Der eindeutige Lösungsname {0} den Sie festlegen möchten, unterliegt Einschränkungen und kann nur von einer internen Lösung verwendet werden.|
> |**Name**:<br />RestrictInheritedRole<br />**Hex**:<br />80044152<br />**Nummer**:<br />-2147204782|Die vererbten Rollen können nicht geändert werden.|
> |**Name**:<br />RetiredProductToBundle<br />**Hex**:<br />8004F993<br />**Nummer**:<br />-2147157613|Sie können einem Paket kein zurückgezogenes Produkt hinzufügen.|
> |**Name**:<br />RetrieveImagePropertiesFail<br />**Hex**:<br />80072552<br />**Nummer**:<br />-2147015342|Eigenschaften für das bereitgestellte Entitätsbild können nicht abgerufen werden|
> |**Name**:<br />RetrieveOrganizationInfoUnexpectedError<br />**Hex**:<br />80072301<br />**Nummer**:<br />-2147015935|Unerwarteter Fehler während des Abrufens der Organisationsinformationen. Die abhängigen Services sind derzeit möglicherweise nicht verfügbar. Bitte versuchen Sie es später erneut.|
> |**Name**:<br />RetrieveRecordOfflineErrorCode<br />**Hex**:<br />8005F213<br />**Nummer**:<br />-2147093997|Dieser Datensatz ist offline nicht verfügbar.  Stellen Sie die Verbindung wieder her und versuchen Sie es erneut.|
> |**Name**:<br />RetrieveUserLicenseUnexpectedError<br />**Hex**:<br />80072300<br />**Nummer**:<br />-2147015936|Unerwarteter Fehler während des Abrufens der Benutzerlizenzinformationen. Die abhängigen Services sind derzeit möglicherweise nicht verfügbar. Bitte versuchen Sie es später erneut.|
> |**Name**:<br />RetryFailed<br />**Hex**:<br />8004F045<br />**Nummer**:<br />-2147159995|Die Aktion ist fehlgeschlagen, nachdem {0} Mal probiert wurde, sie auszuführen. InnerException ist: {1}.|
> |**Name**:<br />RibbonImportDependencyMissingEntity<br />**Hex**:<br />8004F104<br />**Nummer**:<br />-2147159804|Das Menübandelement "{0}" ist von der Entität "{1}" abhängig.|
> |**Name**:<br />RibbonImportDependencyMissingRibbonControl<br />**Hex**:<br />8004F107<br />**Nummer**:<br />-2147159801|Das Menübandelement "{0}" ist vom Menübandsteuerelement mit der ID "{1}" abhängig.|
> |**Name**:<br />RibbonImportDependencyMissingRibbonElement<br />**Hex**:<br />8004F105<br />**Nummer**:<br />-2147159803|Das Menübandelement „{0}” ist von <{1} ID=„{2}” /> abhängig.|
> |**Name**:<br />RibbonImportDependencyMissingWebResource<br />**Hex**:<br />8004F106<br />**Nummer**:<br />-2147159802|Das Menübandelement "{0}" ist von der Webressource mit der ID "{1}" abhängig.|
> |**Name**:<br />RibbonImportDuplicateElementId<br />**Hex**:<br />8004F10B<br />**Nummer**:<br />-2147159797|Das Menübandelement mit der ID "{0}" kann nicht importiert werden, da ein Menüband mit der gleichen ID bereits vorhanden ist.|
> |**Name**:<br />RibbonImportEntityNotSupported<br />**Hex**:<br />8004F103<br />**Nummer**:<br />-2147159805|Die Lösung kann nicht importiert werden, da die {0} Entität eine Menübanddefinition enthält, die für diese Entität unterstützt wird. Entfernen Sie den RibbonDiffXml-Knoten der Entitätsdefinition und klicken Sie erneut, um zu importieren.|
> |**Name**:<br />RibbonImportHidingBasicHomeTab<br />**Hex**:<br />8004F101<br />**Nummer**:<br />-2147159807|Aufgrund der Definition des zu importierenden Menübands wird die Registerkarte „Start” von Microsoft Dynamics 365 entfernt. Wird keine Definition für die Registerkarte „Start” eingeschlossen, wird in den Bereichen der Anwendung mit der Registerkarte „Start” kein Menüband angezeigt.|
> |**Name**:<br />RibbonImportHidingJewel<br />**Hex**:<br />8004F10A<br />**Nummer**:<br />-2147159798|Menübandanpassungen können den <Jewel>-Knoten nicht ausblenden. Alle Menüanpassungen, in denen dieser Knoten ausgeblendet wird, werden beim Importieren ignoriert und auch nicht exportiert.|
> |**Name**:<br />RibbonImportInvalidPrivilegeName<br />**Hex**:<br />8004F102<br />**Nummer**:<br />-2147159806|Das RibbonDiffXml in dieser Lösung enthält einen Verweis für ein ungültiges Recht: {0}. Aktualisieren Sie das RibbonDiffXml, dass ein gültiges Recht aufweisen muss und versuchen Sie es erneut.|
> |**Name**:<br />RibbonImportLocationAndIdDoNotMatch<br />**Hex**:<br />8004F109<br />**Nummer**:<br />-2147159799|"{1}" kann vom CustomAction-Element mit der ID "{0}" nicht überschrieben werden, da "{2}" nicht dem Ortswert des CustomAction-Elements entspricht.|
> |**Name**:<br />RibbonImportModifyingTopLevelNode<br />**Hex**:<br />8004F108<br />**Nummer**:<br />-2147159800|An den folgenden Menübandknoten oberster Ebene können keine Menübandanpassungen vorgenommen werden: <Ribbon>, <ContextualGroups> und <Tabs>.|
> |**Name**:<br />RibbonImportRibbonDiffIdInvalidLength<br />**Hex**:<br />8004F10C<br />**Nummer**:<br />-2147159796|Wir können das Menübandelement nicht importieren, da die ID-Länge die maximale Länge von 128 Zeichen überschreitet: {0}|
> |**Name**:<br />RINotProvisioned<br />**Hex**:<br />80044281<br />**Nummer**:<br />-2147204479|Für Ihre Organisation {0} wurden keine Beziehungsinformationen aktiviert.|
> |**Name**:<br />RoleAlreadyExists<br />**Hex**:<br />80041403<br />**Nummer**:<br />-2147216381|Eine Rolle mit dem angegebenen Namen „{0}” ist bereits in der Unternehmenseinheit {1} und der Lösungs-ID {3} vorhanden. Rollen-ID: {2}|
> |**Name**:<br />RoleNotEnabledForTabletApp<br />**Hex**:<br />8005F203<br />**Nummer**:<br />-2147094013|Sie sind nicht zur Verwendung der App berechtigt.\nWenden Sie sich an den Systemadministrator, und aktualisieren Sie die Einstellungen.|
> |**Name**:<br />RollupAggregateQueryRecordLimitExceeded<br />**Hex**:<br />8004E025<br />**Nummer**:<br />-2147164123|Es können keine Onlineberechnungen durchgeführt werden, da das Berechnungslimit für {0} verknüpfte Datensätze erreicht wurde.|
> |**Name**:<br />RollupCalculationLimitReached<br />**Hex**:<br />80060561<br />**Nummer**:<br />-2147089055|Das Berechnungslimit wurde erreicht. Daher können derzeit keine Berechnungen ausgeführt werden. Bitte warten Sie und versuchen Sie es erneut.|
> |**Name**:<br />RollupDependentFieldNameAlreadyExists<br />**Hex**:<br />80060556<br />**Nummer**:<br />-2147089066|Erforderliches abhängiges Feld {0} für Rollup kann nicht erstell werdent, während ein anderes Feld mit demselben Namen vorhanden ist. Verwenden Sie einen anderen Namen, um dem Rollupfeld erstellen.|
> |**Name**:<br />RollupFieldAggregateFunctionNotAllowed<br />**Hex**:<br />80060546<br />**Nummer**:<br />-2147089082|Die Aggregatfunktion {0} ist nicht zulässig.|
> |**Name**:<br />RollupFieldAggregateFunctionNotAllowedForRollupFieldDataType<br />**Hex**:<br />80060545<br />**Nummer**:<br />-2147089083|Die Aggregatfunktion {0} ist nicht zulässig, wenn das Rollupfeld den Datentyp {1} aufweist.|
> |**Name**:<br />RollupFieldAndAggregateFieldDataTypeFormatMismatch<br />**Hex**:<br />80060544<br />**Nummer**:<br />-2147089084|Der Datentyp {0} mit dem Format {1} ist für das aggregierte Feld nicht zulässig, wenn das Rollupfeld den Datentyp {2} mit dem Format {3} aufweist.|
> |**Name**:<br />RollupFieldDefinitionNotValid<br />**Hex**:<br />80060553<br />**Nummer**:<br />-2147089069|Die Kalkulation ist fehlgeschlagen, weil die Rollupfelddefinition ungültig ist. Wenden Sie sich an den zuständigen Systemadministrator.|
> |**Name**:<br />RollupFieldDependentFieldCannotDeleted<br />**Hex**:<br />80060541<br />**Nummer**:<br />-2147089087|Rollupfeld {0} hängt von diesem Feld ab. Es kann nur gelöscht werden, indem das entsprechende Rollupfeld {0} gelöscht wird.|
> |**Name**:<br />RollupFieldNoWriteAccess<br />**Hex**:<br />8004E027<br />**Nummer**:<br />-2147164121|Benutzer hat keine Schreibberechtigung auf {0} für Datensatz {1} mit ID: {2} Rollupfeld zu berechnen.|
> |**Name**:<br />RollupFieldsAggregateFieldDataTypeNotAllowedSimilarRollupFieldDataType<br />**Hex**:<br />8006053d<br />**Nummer**:<br />-2147089091|Der Datentyp {0} ist für das aggregierte Feld nicht zulässig, wenn das Rollupfeld den Datentyp {1} aufweist.|
> |**Name**:<br />RollupFieldsAggregateFieldNotBelongToRelatedEntity<br />**Hex**:<br />80060540<br />**Nummer**:<br />-2147089088|Das aggregierte Feld {0} gehört nicht zur verknüpften Entität {1}.|
> |**Name**:<br />RollupFieldsAggregateFieldNotBelongToSourceEntity<br />**Hex**:<br />8006053f<br />**Nummer**:<br />-2147089089|Das aggregierte Feld {0} gehört nicht zur Quellentität {1}.|
> |**Name**:<br />RollupFieldsAggregateFieldNotPartOfEntity<br />**Hex**:<br />80060537<br />**Nummer**:<br />-2147089097|Das aggregierte Feld "{0}" gehört nicht zur Entität "{1}"|
> |**Name**:<br />RollupFieldsAggregateFunctionTypeMismatch<br />**Hex**:<br />8006053a<br />**Nummer**:<br />-2147089094|Der Datentyp {0} ist für das aggregierte Feld nicht zulässig, wenn die Aggregatfunktion {1} lautet.|
> |**Name**:<br />RollupFieldsAggregateNotDefined<br />**Hex**:<br />80060536<br />**Nummer**:<br />-2147089098|Für den Rollup müssen eine Aggregatfunktion und ein aggregiertes Feld angegeben werden.|
> |**Name**:<br />RollupFieldsAggregateOnRollupFieldOrComplexCalcFieldNotAllowed<br />**Hex**:<br />8006053c<br />**Nummer**:<br />-2147089092|Das aggregierte Feld muss entweder ein einfaches Feld oder ein grundlegendes berechnetes Feld sein.|
> |**Name**:<br />RollupFieldsDataTypeNotValid<br />**Hex**:<br />8006053e<br />**Nummer**:<br />-2147089090|Der Datentyp {0} ist für das Rollupfeld nicht gültig.|
> |**Name**:<br />RollupFieldsGeneric<br />**Hex**:<br />8006053b<br />**Nummer**:<br />-2147089093|Die Rollupfelddefinition ist ungültig.|
> |**Name**:<br />RollupFieldSourceFilterFieldNotAllowed<br />**Hex**:<br />80060548<br />**Nummer**:<br />-2147089080|Der Quellentitätsfilter muss entweder ein einfaches Feld oder ein grundlegendes berechnetes Feld sein. Es kann kein Rollupfeld und kein berechnetes Feld verwenden, das ein Rollupfeld verwendet.|
> |**Name**:<br />RollupFieldsSourceEntityNotHierarchical<br />**Hex**:<br />80060535<br />**Nummer**:<br />-2147089099|Die Hierarchie für die Quellentität {0} ist nicht vorhanden.|
> |**Name**:<br />RollupFieldsSourceFilterConditionInvalid<br />**Hex**:<br />80060538<br />**Nummer**:<br />-2147089096|Die Filterbedingung {1} für die Quellentität {0} ist ungültig.|
> |**Name**:<br />RollupFieldsTargetEntityNotValid<br />**Hex**:<br />80060552<br />**Nummer**:<br />-2147089070|Die verknüpfte Entität "{0}" ist für Rollups nicht zulässig.|
> |**Name**:<br />RollupFieldsTargetFilterConditionInvalid<br />**Hex**:<br />80060539<br />**Nummer**:<br />-2147089095|Die Filterbedingung {1} für die verknüpfte Entität {0} ist ungültig.|
> |**Name**:<br />RollupFieldsTargetRelationshipNotPartOfOneToNRelationship<br />**Hex**:<br />80060534<br />**Nummer**:<br />-2147089100|Eine 1:n-Beziehung {0} von der Quellentität {1} zur verknüpften Entität {2} ist nicht vorhanden.|
> |**Name**:<br />RollupFieldsTargetRelationshipNull<br />**Hex**:<br />80060533<br />**Nummer**:<br />-2147089101|Name der verknüpften Entität ist leer. Sie muss bereitgestellt werden, wenn die Quellentitätshierarchie nicht für den Rollup verwendet wird.|
> |**Name**:<br />RollupFieldsTargetSameAsSourceEntity<br />**Hex**:<br />80060551<br />**Nummer**:<br />-2147089071|Auf sich selbst verweisende 1:n-Beziehungen sind für das Rollupfeld nicht zulässig.|
> |**Name**:<br />RollupFieldsV2FeatureNotEnabled<br />**Hex**:<br />80060565<br />**Nummer**:<br />-2147089051|Das Feature wird in der aktuellen Produktversion nicht unterstützt.|
> |**Name**:<br />RollupFieldTargetFilterFieldNotAllowed<br />**Hex**:<br />80060549<br />**Nummer**:<br />-2147089079|Der Zielentitätsfilter muss entweder ein einfaches Feld oder ein grundlegendes berechnetes Feld sein. Es kann kein Rollupfeld und kein berechnetes Feld verwenden, das ein Rollupfeld verwendet.|
> |**Name**:<br />RollupFormulaFieldInvalid<br />**Hex**:<br />80060560<br />**Nummer**:<br />-2147089056|Das Formelfeld ist ungültig.|
> |**Name**:<br />RollupInvalidAttributeForFilterCondition<br />**Hex**:<br />80060564<br />**Nummer**:<br />-2147089052|Das {0}-Attribut ist für Filterbedingung nicht zulässig.|
> |**Name**:<br />RollupOrCalcNotAllowedInWorkflowWaitCondition<br />**Hex**:<br />80060557<br />**Nummer**:<br />-2147089065|Das Feld {0} ist entweder ein Rollupfeld oder eine abhängiges Feld oder ein berechnetes Feld. Derartige Felder werden nicht in der Workflowwartebedingung zugelassen.|
> |**Name**:<br />RollupTargetLinkedEntityCanOnlyUsedForActivityPartyEntities<br />**Hex**:<br />80060563<br />**Nummer**:<br />-2147089053|Zielverknüpfte Entität kann nur für {0} Entität für Rollup über {1} Typ Entitäten verwendet werden.|
> |**Name**:<br />RollupTargetLinkedEntityOnlySupportedForActivityEntities<br />**Hex**:<br />80060562<br />**Nummer**:<br />-2147089054|Zielverknüpfte Entität ist nur für Rollup über {0} Typ Entitäten unterstützt.|
> |**Name**:<br />RollupTargetLinkedRelationshipNotValid<br />**Hex**:<br />80060566<br />**Nummer**:<br />-2147089050|Eine ausgewählte Beziehung {0} ist ungültig.|
> |**Name**:<br />RootBusinessUnitCannotBeDisabled<br />**Hex**:<br />80041d63<br />**Nummer**:<br />-2147213981|Stammunternehmenseinheit kann nicht deaktiviert werden.|
> |**Name**:<br />RouterIsDisabled<br />**Hex**:<br />8005E246<br />**Nummer**:<br />-2147098042|Microsoft Dynamics 365 wurde konfiguriert, um serverseitige Synchronisierung zu verwenden, um E-Mails zu verarbeiten. Dieser Fehler tritt auf, da mehrere Clients weiterhin so konfiguriert werden, dass sie den alten E-Mail-Router verwenden. Sie müssen die E-Mail-Router-Client-Anwendung auf allen Servern deinstallieren, auf denen sie installiert wurde.|
> |**Name**:<br />RouteTypeUnsupported<br />**Hex**:<br />800404e9<br />**Nummer**:<br />-2147220247|Der Routentyp wird nicht unterstützt|
> |**Name**:<br />RoutingNotAllowed<br />**Hex**:<br />800404e7<br />**Nummer**:<br />-2147220249|Dieser Objekttyp kann nicht weitergeleitet werden.|
> |**Name**:<br />RoutingRuleActivateDeactivateByNonOwner<br />**Hex**:<br />8004F885<br />**Nummer**:<br />-2147157883|Dieser Routingregelsatz kann nur vom Besitzer aktiviert oder deaktiviert werden.|
> |**Name**:<br />RoutingRuleMissingRuleCriteria<br />**Hex**:<br />8004F877<br />**Nummer**:<br />-2147157897|Sie können diese Regel erst aktivieren, wenn Sie fehlende Regelkriterieninformationen in den Regelelementen auflösen.|
> |**Name**:<br />RoutingRulePublishedByNonOwner<br />**Hex**:<br />8004F878<br />**Nummer**:<br />-2147157896|Dieser Routingregelsatz kann nur vom Besitzer veröffentlicht oder geschlossen werden.|
> |**Name**:<br />RoutingRulePublishedByOwner<br />**Hex**:<br />8004F876<br />**Nummer**:<br />-2147157898|Die Regel kann nicht aktiviert werden, wenn die aktuelle aktive Regel deaktiviert wurde. Die aktive Regel kann nur vom Regelbesitzer deaktiviert werden.|
> |**Name**:<br />RowGuidIsNotValidName<br />**Hex**:<br />80047001<br />**Nummer**:<br />-2147192831|rowguid' ist ein reservierter Name, der nicht als Bezeichner verwendet werden darf.|
> |**Name**:<br />RSCancelBatchError<br />**Hex**:<br />8004831c<br />**Nummer**:<br />-2147187940|Fehler beim Abbrechen des Batchvorgangs. |
> |**Name**:<br />RSCreateBatchError<br />**Hex**:<br />80048320<br />**Nummer**:<br />-2147187936|Fehler beim Erstellen eines Batchvorgangs. |
> |**Name**:<br />RSDeleteItemError<br />**Hex**:<br />80048317<br />**Nummer**:<br />-2147187945|Fehler beim Löschen eines Elements vom Berichtsserver.|
> |**Name**:<br />RSExecuteBatchError<br />**Hex**:<br />8004831d<br />**Nummer**:<br />-2147187939|Fehler beim Durchführen des Batchvorgangs. |
> |**Name**:<br />RSFindItemsError<br />**Hex**:<br />80048318<br />**Nummer**:<br />-2147187944|Fehler beim Suchen eines Elements auf dem Berichtsserver.|
> |**Name**:<br />RSGetDataSourceContentsError<br />**Hex**:<br />8004831a<br />**Nummer**:<br />-2147187942|Fehler beim Abrufen des Inhalts der Datenquelle.|
> |**Name**:<br />RSGetItemDataSourcesError<br />**Hex**:<br />80048321<br />**Nummer**:<br />-2147187935|Fehler beim Abrufen der aktuellen Datenquellen.|
> |**Name**:<br />RSGetItemTypeError<br />**Hex**:<br />8004832b<br />**Nummer**:<br />-2147187925|Fehler beim Abrufen des Berichts. |
> |**Name**:<br />RSGetReportHistoryLimitError<br />**Hex**:<br />8004831e<br />**Nummer**:<br />-2147187938|Fehler beim Abrufen der Anzahl von Momentaufnahmen, die für den Bericht gespeichert sind. |
> |**Name**:<br />RSGetReportParametersError<br />**Hex**:<br />80048323<br />**Nummer**:<br />-2147187933|Fehler beim Abrufen von Parametern.|
> |**Name**:<br />RSListExtensionsError<br />**Hex**:<br />8004831b<br />**Nummer**:<br />-2147187941|Fehler beim Abruf der Liste der Datenerweiterungen, die auf dem Berichtsserver installiert sind.|
> |**Name**:<br />RSListReportHistoryError<br />**Hex**:<br />8004831f<br />**Nummer**:<br />-2147187937|Fehler beim Abrufen der Berichtsverlauf-Snapshots.|
> |**Name**:<br />RSMoveItemError<br />**Hex**:<br />80048330<br />**Nummer**:<br />-2147187920|Kann Berichtselement {0} nicht nach {1} verschieben|
> |**Name**:<br />RSReportParameterTypeMismatchError<br />**Hex**:<br />80048329<br />**Nummer**:<br />-2147187927|Der Parametertyp ist für den Bericht ungültig. |
> |**Name**:<br />RSSetDataSourceContentsError<br />**Hex**:<br />80048319<br />**Nummer**:<br />-2147187943|Fehler beim Festlegen des Inhalts der Datenquelle. |
> |**Name**:<br />RSSetExecutionOptionsError<br />**Hex**:<br />80048325<br />**Nummer**:<br />-2147187931|Fehler beim Festlegen von Ausführungsoptionen.|
> |**Name**:<br />RSSetItemDataSourcesError<br />**Hex**:<br />80048322<br />**Nummer**:<br />-2147187934|Fehler beim Festlegen der Datenquelle.|
> |**Name**:<br />RSSetPropertiesError<br />**Hex**:<br />8004832a<br />**Nummer**:<br />-2147187926|Fehler beim Festlegen von Eigenschaftswerten für den Bericht. |
> |**Name**:<br />RSSetReportHistoryLimitError<br />**Hex**:<br />80048327<br />**Nummer**:<br />-2147187929|Fehler beim Festlegen der Begrenzung der Berichtsverlauf-Snapshots.|
> |**Name**:<br />RSSetReportHistoryOptionsError<br />**Hex**:<br />80048326<br />**Nummer**:<br />-2147187930|Fehler beim Festlegen von Optionen für Berichtsverlauf-Snapshots.|
> |**Name**:<br />RSSetReportParametersError<br />**Hex**:<br />80048324<br />**Nummer**:<br />-2147187932|Fehler beim Festlegen von Parametern.|
> |**Name**:<br />RSUpdateReportExecutionSnapshotError<br />**Hex**:<br />80048328<br />**Nummer**:<br />-2147187928|Fehler beim Erstellen einer Momentaufnahme für einen Bericht.|
> |**Name**:<br />RuleActivationNotAllowedWithDeletedStages<br />**Hex**:<br />80060014<br />**Nummer**:<br />-2147090412|Sie können diese Regel nicht aktivieren, da sie eine gelöschte Phase oder Phasenkategorie enthält. Korrigieren Sie die Regel, und versuchen Sie es noch einmal. Korrigieren Sie die Regel, und versuchen Sie es erneut.|
> |**Name**:<br />RuleAlreadyExistsWithSameQueueAndChannel<br />**Hex**:<br />8004F884<br />**Nummer**:<br />-2147157884|Rekorderstellungsregel für den angegebenen Kanal und die Warteschlange ist bereits vorhanden. Sie können keine andere erstellen.|
> |**Name**:<br />RuleAlreadyInactiveState<br />**Hex**:<br />8004F852<br />**Nummer**:<br />-2147157934|Dieser Weiterleitungsregelsatz befindet sich bereits im Status "Aktiv".|
> |**Name**:<br />RuleAlreadyInDraftState<br />**Hex**:<br />8004F853<br />**Nummer**:<br />-2147157933|Sie können einen Weiterleitungsregelsatz im Entwurfszustand nicht deaktivieren.|
> |**Name**:<br />RuleAlreadyPublishing<br />**Hex**:<br />80048434<br />**Nummer**:<br />-2147187660|Die ausgewählte Duplikaterkennungsregel wird bereits veröffentlicht.|
> |**Name**:<br />RuleCreationNotAllowedForCyclicReferences<br />**Hex**:<br />80060012<br />**Nummer**:<br />-2147090414|Sie können diese Regel nicht erstellen, da sie einen Zirkelbezug enthält. Korrigieren Sie die Regel, und versuchen Sie es erneut.|
> |**Name**:<br />RuleNotFound<br />**Hex**:<br />80048433<br />**Nummer**:<br />-2147187661|Keine Regeln gefunden, die den Kriterien entsprechen.|
> |**Name**:<br />RuleNotSupportedForEditor<br />**Hex**:<br />80060007<br />**Nummer**:<br />-2147090425|Die aktuelle Regeldefinition kann nicht im Geschäftsregeleditor bearbeitet werden.|
> |**Name**:<br />RulesInInconsistentStateFound<br />**Hex**:<br />80048423<br />**Nummer**:<br />-2147187677|Mindestens eine Regel kann die Veröffentlichung nicht aufheben, das sie entweder veröffentlicht werden oder in einem Zustand sind, wo die Veröffentlichung nicht aufgehoben werden kann.|
> |**Name**:<br />RuntimeRibbonXmlValidation<br />**Hex**:<br />8004F671<br />**Nummer**:<br />-2147158415|Das aktuelle benutzerdefinierte Menüband für eine Registerkarte auf dieser Seite kann nicht erstellt werden. Die Version der Multifunktionsleiste wird stattdessen angezeigt.|
> |**Name**:<br />S2SAccessTokenCannotBeAcquired<br />**Hex**:<br />8005E243<br />**Nummer**:<br />-2147098045|Fehler beim Abruf des S2S-Zugriffstokens vom Autorisierungsserver.|
> |**Name**:<br />S2SNotConfigured<br />**Hex**:<br />80044259<br />**Nummer**:<br />-2147204519|Die Office Graph-Integration basiert auf der serverbasierten SharePoint-Integration. Aktivieren Sie die serverbasierte Integration und sorgen Sie dafür, dass Sie mindestens eine aktive SharePoint-Website zum Nutzens dieser Funktion haben.|
> |**Name**:<br />SalesOrderAndInvoiceCurrencyNotEqual<br />**Hex**:<br />80048ced<br />**Nummer**:<br />-2147185427|Die Währung des Datensatz aus entspricht nicht der Währung der Preisliste.|
> |**Name**:<br />SalesPeopleDuplicateCalendarNotAllowed<br />**Hex**:<br />80043803<br />**Nummer**:<br />-2147207165|Geschäftskalender für diesen Vertriebsmitarbeiter/dieses Jahr ist bereits vorhanden|
> |**Name**:<br />SalesPeopleEmptyEffectiveDate<br />**Hex**:<br />80043801<br />**Nummer**:<br />-2147207167|Tatsächliches Datum des Geschäftskalenders kann nicht leer sein|
> |**Name**:<br />SalesPeopleEmptySalesPerson<br />**Hex**:<br />80043800<br />**Nummer**:<br />-2147207168|Der übergeordnete Vertriebsmitarbeiter darf nicht leer sein.|
> |**Name**:<br />SalesPeopleManagerNotAllowed<br />**Hex**:<br />80043805<br />**Nummer**:<br />-2147207163|Gebiets-Manager kann nicht zu anderem Gebiet gehören|
> |**Name**:<br />SandboxClientPluginTimeout<br />**Hex**:<br />80044171<br />**Nummer**:<br />-2147204751|Die Plug-In-Ausführung ist fehlgeschlagen, weil der Vorgang beim Sandbox-Clients abgelaufen ist.|
> |**Name**:<br />SandboxHostNotAvailable<br />**Hex**:<br />8004418e<br />**Nummer**:<br />-2147204722|Die Plug-In-Ausführung ist fehlgeschlagen, weil keine Sandbox-Hosts derzeit verfügbar sind. Überprüfen Sie, ob Sie einen Sandboxserver konfiguriert haben und dass er läuft.|
> |**Name**:<br />SandboxHostPluginTimeout<br />**Hex**:<br />80044172<br />**Nummer**:<br />-2147204750|Die Plug-In-Ausführung ist fehlgeschlagen, weil der Vorgang beim Sandbox-Host abgelaufen ist.|
> |**Name**:<br />SandboxPluginDisabled<br />**Hex**:<br />80081115<br />**Nummer**:<br />-2146954987|Sandbox-Plug-In-Ausführung ist deaktiviert.|
> |**Name**:<br />SandboxSdkListenerStartFailed<br />**Hex**:<br />80044174<br />**Nummer**:<br />-2147204748|Die Plug-In-Ausführung ist fehlgeschlagen, weil beim Sandbox-Client ein Fehler während der Initialisierung auftraf.|
> |**Name**:<br />SandboxWorkerNotAvailable<br />**Hex**:<br />8004418d<br />**Nummer**:<br />-2147204723|Die Plug-In-Ausführung ist fehlgeschlagen, weil keine Sandbox-Worker-Prozesse derzeit verfügbar sind. Bitte wiederholen Sie den Vorgang.|
> |**Name**:<br />SandboxWorkerPluginExecuteTimeout<br />**Hex**:<br />80081111<br />**Nummer**:<br />-2146954991|Keine Reaktion des {0} Plug-Ins innerhalb der 2: 20-Minuten-Begrenzung empfangen.|
> |**Name**:<br />SandboxWorkerPluginTimeout<br />**Hex**:<br />80044173<br />**Nummer**:<br />-2147204749|Die Plug-In-Ausführung ist fehlgeschlagen, weil der Vorgang beim Sandbox-Worker abgelaufen ist.|
> |**Name**:<br />SandboxWorkerThrottleLimit<br />**Hex**:<br />80081116<br />**Nummer**:<br />-2146954986|Die maximale Anzahl der Prozesse, die für die Plug-In-Geschäftslogik zugewiesen wurden, wurde überschritten. Schwerwiegende Fehler bei Plug-Ins für diese Umgebung sind {0} Mal in den letzten {1} Minuten aufgetreten. Alle Fehler erfordern einen zusätzlichen Prozess zur Wiederherstellung. Die Prozesse für Plug-Ins werden wiederverwendet. Alle Plug-Ins für diese Umgebung werden während dieses Zeitraums fehlschlagen. Weitere Informationen: https://go.microsoft.com/fwlink/?linkid=2038718 |
> |**Name**:<br />SaveAsDraftAppointmentNotAllowed<br />**Hex**:<br />8004026b<br />**Nummer**:<br />-2147220885|AllowSaveAsDraftAppointment wird deaktiviert.|
> |**Name**:<br />SaveDataFileErrorOutOfSpace<br />**Hex**:<br />8005F209<br />**Nummer**:<br />-2147094007|Wiederholen Sie den Vorgang. Besteht das Problem weiterhin, überprüfen Sie {0} auf Lösungen, oder wenden Sie sich an den {#Brand_CRM}-Administrator in Ihrer Organisation. Schließlich können Sie {1} kontaktieren.|
> |**Name**:<br />SavedQueryIsNotCustomizable<br />**Hex**:<br />80047017<br />**Nummer**:<br />-2147192809|Die defineirte Ansicht kann nicht angepasst werden|
> |**Name**:<br />SavedQueryValidationError<br />**Hex**:<br />800609A0<br />**Nummer**:<br />-2147087968|Sie können Profil {0} aufgrund eines seiner Profilelemente nicht veröffentlichen: {1} verfügt in der gespeicherten Abfrage {3} über die Entität {2}, die nicht Teil dieses Profils ist.|
> |**Name**:<br />SavePending<br />**Hex**:<br />80060913<br />**Nummer**:<br />-2147088109|Speichervorgang läuft bereits im Hintergrund.|
> |**Name**:<br />SaveRecordBeforeAddingBundle<br />**Hex**:<br />8004F983<br />**Nummer**:<br />-2147157629|Nachdem Sie eine Preisliste ausgewählt haben, müssen Sie den Datensatz speichern, bevor Sie ein Paket mit optionalen Produkten hinzufügen.|
> |**Name**:<br />ScaleGroupDisabled<br />**Hex**:<br />8004A107<br />**Nummer**:<br />-2147180281|Die angegebene scalegroup ist deaktiviert. Zugriff auf Organisationen in dieser Scalegruppe ist nicht zulässig.|
> |**Name**:<br />SchedulingFailedForBookingValidation<br />**Hex**:<br />80060915<br />**Nummer**:<br />-2147088107|Buchungs- oder Neuplanungsvorgang aufgrund der Buchungsüberprüfung fehlgeschlagen.|
> |**Name**:<br />SchedulingFailedForInvalidData<br />**Hex**:<br />80060914<br />**Nummer**:<br />-2147088108|Buchungs- oder Neuplanungsvorgang aufgrund ungültiger Daten fehlgeschlagen.|
> |**Name**:<br />SchemaNameContainsNonAlphaNumericCharacters<br />**Hex**:<br />80044364<br />**Nummer**:<br />-2147204252|Der Bezeichner {0} für den Typ {2} darf nur alphanumerische Zeichen und Unterstriche enthalten.|
> |**Name**:<br />SchemaNameisNotUnique<br />**Hex**:<br />80044363<br />**Nummer**:<br />-2147204253|Der Schemaname {0} für den Typ {1} ist nicht eindeutig. Ein {0} mit identischem Namen ist bereits vorhanden.|
> |**Name**:<br />SchemaNameLengthExceedsLimit<br />**Hex**:<br />80044367<br />**Nummer**:<br />-2147204249|Bezeichner dürfen aus maximal {1} Zeichen bestehen. Die Länge des angegebenen Schemanamens {0} für den Typ {2} ist größer als die maximale Länge von {1} Zeichen.|
> |**Name**:<br />SchemaNameMatchesExistingIdentifier<br />**Hex**:<br />80044361<br />**Nummer**:<br />-2147204255|Bezeichner dürfen nicht mit bestehenden Objektnamen übereinstimmen. Ein Objekt des Typs {1} mit demselben Namen {0} ist bereits vorhanden.|
> |**Name**:<br />SchemaNameMatchesReservedSqlKeywords<br />**Hex**:<br />80044362<br />**Nummer**:<br />-2147204254|Bezeichner dürfen nicht mit reservierten SQL-Schlüsselwörten übereinstimmen. Der angegebene Name {0} für den Typ {1} entspricht dem Schlüsselwort {2}|
> |**Name**:<br />SchemaNameNotStartwithLetter<br />**Hex**:<br />80044365<br />**Nummer**:<br />-2147204251|Bezeichner sollten mit einem Buchstaben beginnen. Der Schemaname {0} für den Typ {2} startet nicht mit einem Buchstaben.|
> |**Name**:<br />ScopeNotSetToGlobal<br />**Hex**:<br />80060403<br />**Nummer**:<br />-2147089405|Kategorie sollte auf Global festgelegt werden, solange die Geschäftsprozessflusskategorie erstellt wird|
> |**Name**:<br />SdkCorrelationTokenDepthTooHigh<br />**Hex**:<br />80044182<br />**Nummer**:<br />-2147204734|Dieser Workflowauftrag wurde abgebrochen, da der Workflow, der ihn darstellte Endlosschleifen enthält. Korrigieren Sie die Workflowlogik, und versuchen Sie es erneut. Informationen zur Workflowlogik finden Sie in der Hilfe.|
> |**Name**:<br />SdkCustomProcessingStepIsNotAllowed<br />**Hex**:<br />80044187<br />**Nummer**:<br />-2147204729|Benutzerdefiniertes SdkMessageProcessingStep ist bei der angegebenen Nachricht und Entität nicht gestattet.|
> |**Name**:<br />SdkEntityDoesNotSupportMessage<br />**Hex**:<br />80040800<br />**Nummer**:<br />-2147219456|Die Methode, die eingesetzt wird, unterstützt keine bereitgestellten Entitätstypen.|
> |**Name**:<br />SdkEntityOfflineQueuePlaybackIsNotAllowed<br />**Hex**:<br />80044188<br />**Nummer**:<br />-2147204728|Entität ''{0}" ist bei der Wiedergabe der Offlinewarteschlange nicht zulässig.|
> |**Name**:<br />SdkInvalidMessagePropertyName<br />**Hex**:<br />8004416b<br />**Nummer**:<br />-2147204757|Meldungseigenschaftenname "{0}" ist bei Meldung {1} ungültig.|
> |**Name**:<br />SdkMessageDoesNotSupportImageRegistration<br />**Hex**:<br />80044189<br />**Nummer**:<br />-2147204727|Meldung "{0}" unterstützt keine Bildregistrierung.|
> |**Name**:<br />SdkMessageDoesNotSupportPostImageRegistration<br />**Hex**:<br />8004416e<br />**Nummer**:<br />-2147204754|PreEvent-Schrittregistrierung unterstützt kein Nachrichten-Bild.|
> |**Name**:<br />SdkMessageInvalidImageTypeRegistration<br />**Hex**:<br />8004416d<br />**Nummer**:<br />-2147204755|Meldung {0} unterstützt diesen Bildtyp nicht.|
> |**Name**:<br />SdkMessageNotImplemented<br />**Hex**:<br />80044824<br />**Nummer**:<br />-2147203036|Die SDK-Message ist nicht implementiert.|
> |**Name**:<br />SdkMessageNotSupportedOnClient<br />**Hex**:<br />80044181<br />**Nummer**:<br />-2147204735|Die angeforderte Nachricht wird nicht vom Clients unterstützt.|
> |**Name**:<br />SdkMessageNotSupportedOnServer<br />**Hex**:<br />80044180<br />**Nummer**:<br />-2147204736|Die angeforderte Nachricht wird nicht vom Server unterstützt.|
> |**Name**:<br />SdkMessagesDeprecatedError<br />**Hex**:<br />8004F903<br />**Nummer**:<br />-2147157757|Dieses Thema ist nicht mehr verfügbar. Empfehlen Sie bitte das SDK für alternative Nachrichten.|
> |**Name**:<br />SdkNotEnoughPrivilegeToSetCallerOriginToken<br />**Hex**:<br />80044309<br />**Nummer**:<br />-2147204343|Anrufer hat nicht genügend Rechte zum Festlegen von CallerOriginToken auf den angegebenen Wert.|
> |**Name**:<br />SearchTextLenExceeded<br />**Hex**:<br />800401ff<br />**Nummer**:<br />-2147220993|Suchen-Text-Dauer überschritten.|
> |**Name**:<br />SelectedFileNotFound<br />**Hex**:<br />80071025<br />**Nummer**:<br />-2147020763|Dokumente können nicht kopiert werden. Die Quelldatei ist nicht mehr vorhanden.|
> |**Name**:<br />SeriesMeasureCollectionMismatch<br />**Hex**:<br />8004E003<br />**Nummer**:<br />-2147164157|Die Anzahl der Serien für den Diagrammbereich und die Anzahl der Sammlungen für die Kategorie sollten identisch sein.|
> |**Name**:<br />ServerLocationAndSSLSetToYes<br />**Hex**:<br />8005E255<br />**Nummer**:<br />-2147098027|Die für den Serverstandort angegebene URL verwendet HTTP, für Exchange Online ist jedoch Secure Sockets Layer (SSL) erforderlich.|
> |**Name**:<br />ServerLocationIsEmpty<br />**Hex**:<br />8005E250<br />**Nummer**:<br />-2147098032|Das Feld "ServerLocation" darf nicht leer sein.|
> |**Name**:<br />ServiceAccountMailboxesCountIsGreaterThanOne<br />**Hex**:<br />8005E24A<br />**Nummer**:<br />-2147098038|Weitere Anzahl der Dienstkontopostfächer ist dem E-Mail-Serverprofil zugeordnet.|
> |**Name**:<br />ServiceAccountMailboxesCountIsZero<br />**Hex**:<br />8005E249<br />**Nummer**:<br />-2147098039|Kein Dienstkontopostfach für das E-Mail-Serverprofil zugeordnet.|
> |**Name**:<br />ServiceBusEndpointNotConfigured<br />**Hex**:<br />80081112<br />**Nummer**:<br />-2146954990|Die Konfiguration der erforderlichen Anmeldeinformationen muss abgeschlossen werden, bevor Nachrichten gesendet werden können.|
> |**Name**:<br />ServiceBusExtendedTokenFailed<br />**Hex**:<br />80044178<br />**Nummer**:<br />-2147204744|Fehler beim Abrufen des zusätzlichen Tokens für die Servicebusnachricht.|
> |**Name**:<br />ServiceBusIssuerCertificateError<br />**Hex**:<br />80044177<br />**Nummer**:<br />-2147204745|Fehler im Dienstintegrationsaussteller.|
> |**Name**:<br />ServiceBusIssuerNotFound<br />**Hex**:<br />80044176<br />**Nummer**:<br />-2147204746|Dienstintegrationsaussteller-Informationen konnten nicht gefunden werden.|
> |**Name**:<br />ServiceBusMaxSizeExceeded<br />**Hex**:<br />80050208<br />**Nummer**:<br />-2147155448|Der Service Bus-Aufruf ist fehlgeschlagen, weil die Anforderungsnutzlast die maximal erlaubte Größe überschritten hat. Bitte reduzieren Sie Ihre Anforderungsgröße und versuchen Sie es noch einmal.|
> |**Name**:<br />ServiceBusPostDisabled<br />**Hex**:<br />8004417A<br />**Nummer**:<br />-2147204742|Servicebusnachricht ist für die Organisation deaktiviert.|
> |**Name**:<br />ServiceBusPostFailed<br />**Hex**:<br />80044175<br />**Nummer**:<br />-2147204747|Die Servicebusnachricht ist fehlgeschlagen.|
> |**Name**:<br />ServiceBusPostPostponed<br />**Hex**:<br />80044179<br />**Nummer**:<br />-2147204743|Servicebusnachricht wird hinausgeschoben.|
> |**Name**:<br />ServiceEndpointAcsAuthNotSupported<br />**Hex**:<br />80050209<br />**Nummer**:<br />-2147155447|Dienstendpunkt mit ACS-Authentifizierungstyp wird nicht länger unterstützt. Bitte ändern Sie Ihre Endpunktkonfiguration, um einen unterstützten Authentifizierungstyp zu verwenden|
> |**Name**:<br />ServiceInstantiationFailed<br />**Hex**:<br />80040244<br />**Nummer**:<br />-2147220924|Instanziierung einer Entität fehlgeschlagen.|
> |**Name**:<br />SessionTokenUnavailable<br />**Hex**:<br />80040253<br />**Nummer**:<br />-2147220909|Sitzungstoken ist nicht verfügbar, es sei denn, es gibt eine Transaktion.|
> |**Name**:<br />SetActiveNotSupportedOnNewRecords<br />**Hex**:<br />80060374<br />**Nummer**:<br />-2147089548|SetActiveProcess wird für neue Datensätze nicht unterstützt.|
> |**Name**:<br />SharePointAbsoluteAndRelativeUrlEmpty<br />**Hex**:<br />80048149<br />**Nummer**:<br />-2147188407|Absolute URL und relative URL dürfen nicht leer sein.|
> |**Name**:<br />SharePointAuthenticationFailure<br />**Hex**:<br />800608B3<br />**Nummer**:<br />-2147088205|Microsoft Dynamics 365 kann den Benutzer {0} nicht authentifizieren. Überprüfen, dass die Informationen für den Benutzer und die Gruppe für stehen und dass die Gruppe in SharePoint ist, und versuchen Sie es anschließend erneut.|
> |**Name**:<br />SharePointAuthorizationFailure<br />**Hex**:<br />800608B4<br />**Nummer**:<br />-2147088204|Microsoft Dynamics 365 kann den Benutzer {0} nicht autorisieren. Überprüfen, dass die Informationen für den Benutzer und die Gruppe für stehen und dass die Gruppe in SharePoint ist, und versuchen Sie es anschließend erneut.|
> |**Name**:<br />SharePointCertificateExpired<br />**Hex**:<br />800608B1<br />**Nummer**:<br />-2147088207|Das verwendete Zertifikat für SharePoint-Überprüfung ist abgelaufen|
> |**Name**:<br />SharePointConnectionFailure<br />**Hex**:<br />800608B5<br />**Nummer**:<br />-2147088203|Microsoft Dynamics 365 kann den Benutzer {0} nicht mit SharePoint verbinden. Überprüfen Sie, dass die Informationen für den Benutzer und die Gruppe für stehen und dass die Gruppe in SharePoint ist, und versuchen Sie es anschließend erneut.|
> |**Name**:<br />SharePointCrmDomainValidator<br />**Hex**:<br />8004F302<br />**Nummer**:<br />-2147159294|Die SharePoint- und Microsoft Dynamics 365 Server sind auf verschiedenen Domänen. Stellen Sie eine Vertrauensstellung zwischen den zwei Domänen sichern.|
> |**Name**:<br />SharePointCrmGridIsInstalledValidator<br />**Hex**:<br />8004F309<br />**Nummer**:<br />-2147159287|Die Microsoft Dynamics 365-Rasterkomponente muss auf dem SharePoint-Server installiert werden. Diese Komponente ist erforderlich, damit die SharePoint-Integration korrekt arbeitet.|
> |**Name**:<br />SharePointErrorAbsoluteUrlClipped<br />**Hex**:<br />8004F314<br />**Nummer**:<br />-2147159276|Die URL überschreitet die maximale Länge von 256 Zeichen. Verwenden Sie kürzere Namen für  Standorte und Ordner und versuchen Sie es erneut.|
> |**Name**:<br />SharePointErrorRetrieveAbsoluteUrl<br />**Hex**:<br />8004F310<br />**Nummer**:<br />-2147159280|Fehler beim Abruf der absoluten und Websitesammlungs-URL für ein SharePoint-Objekt.|
> |**Name**:<br />SharePointInvalidEntityForValidation<br />**Hex**:<br />8004F311<br />**Nummer**:<br />-2147159279|Entität unterstützt keine SharePoint-URL-Überprüfung.|
> |**Name**:<br />SharePointRealmMismatch<br />**Hex**:<br />800608B2<br />**Nummer**:<br />-2147088206|Eingeführter ID SharePoint-Bereich entspricht nicht dem registrierten Bereich auf SharePoint-Seite.|
> |**Name**:<br />SharePointRecordWithDuplicateUrl<br />**Hex**:<br />80048057<br />**Nummer**:<br />-2147188649|Es gibt noch einen Datensatz mit der gleichen URL.|
> |**Name**:<br />SharePointRoleProvisionJobAlreadyExists<br />**Hex**:<br />8004F0FA<br />**Nummer**:<br />-2147159814|Ein Systemauftrag zum Bereitstellen der ausgewählten Sicherheitsrolle steht aus. Alle Änderungen am Datensatz der Sicherheitsrolle bevor der Systemauftrag gestartet wird, werden bei dem Systemauftrag angewendet.|
> |**Name**:<br />SharePointS2SIsDisabled<br />**Hex**:<br />80071017<br />**Nummer**:<br />-2147020777|SharePoint: serverbasierte SharePoint-Integration nicht aktiviert.|
> |**Name**:<br />SharePointServerDiscoveryValidator<br />**Hex**:<br />8004F303<br />**Nummer**:<br />-2147159293|Die URL ist falsch, oder die Website wird nicht ausgeführt.|
> |**Name**:<br />SharePointServerLanguageValidator<br />**Hex**:<br />8004F308<br />**Nummer**:<br />-2147159288|Microsoft Dynamics 365- und Microsoft Office SharePoint-Server müssen die gleiche Ausgangssprache haben.|
> |**Name**:<br />SharePointServerVersionValidator<br />**Hex**:<br />8004F304<br />**Nummer**:<br />-2147159292|Die SharePoint-Websitessammlung muss eine unterstützte Version des Microsoft Office SharePoint-Servers oder der Microsoft Windows SharePoint-Dienste ausführen. Bitte schauen Sie im Implementierungshandbuch.|
> |**Name**:<br />SharePointSiteCollectionIsAccessibleValidator<br />**Hex**:<br />8004F305<br />**Nummer**:<br />-2147159291|Die URL ist falsch, oder die Website wird nicht ausgeführt.|
> |**Name**:<br />SharePointSiteCreationFailure<br />**Hex**:<br />8004F0F8<br />**Nummer**:<br />-2147159816|Fehler bei der Erstellung der Website {0} in SharePoint.|
> |**Name**:<br />SharePointSiteNotConfigured<br />**Hex**:<br />80071014<br />**Nummer**:<br />-2147020780|SharePointSite ist nicht konfiguriert und muss konfiguriert werden.|
> |**Name**:<br />SharePointSiteNotPresentInSharePoint<br />**Hex**:<br />8004F0F3<br />**Nummer**:<br />-2147159821|Website {0} ist in SharePoint nicht vorhanden.|
> |**Name**:<br />SharePointSitePermissionsValidator<br />**Hex**:<br />8004F307<br />**Nummer**:<br />-2147159289|Der aktuelle Benutzer besitzt nicht die erforderlichen Berechtigungen. Sie müssen ein SharePoint-Website-Administrator auf der SharePoint-Website sein.|
> |**Name**:<br />SharePointSiteWideProvisioningJobFailed<br />**Hex**:<br />8004F0FB<br />**Nummer**:<br />-2147159813|Der SharePoint-Bereitstellungsauftrag ist fehlgeschlagen.|
> |**Name**:<br />SharePointTeamProvisionJobAlreadyExists<br />**Hex**:<br />8004F0F9<br />**Nummer**:<br />-2147159815|Ein Systemauftrag zum Bereitstellen des ausgewählten Teams steht aus. Alle Änderungen am Datensatz des Teams bevor der Systemauftrag gestartet wird, werden bei dem Systemauftrag angewendet.|
> |**Name**:<br />SharePointUnableToAclSite<br />**Hex**:<br />8004F0F6<br />**Nummer**:<br />-2147159818|ACL-Website {0} in SharePoint nicht erreichbar.|
> |**Name**:<br />SharePointUnableToAclSiteWithPrivilege<br />**Hex**:<br />8004F0F5<br />**Nummer**:<br />-2147159819|ACL-Website {0} mit Berechtigung {1} in SharePoint nicht erreichbar.|
> |**Name**:<br />SharePointUnableToAddUserToGroup<br />**Hex**:<br />8004F0F1<br />**Nummer**:<br />-2147159823|Microsoft Dynamics 365 kann diesen Benutzer {0} nicht der Gruppe {1} in SharePoint hinzufügen. Überprüfen Sie, dass die Informationen für den Benutzer und die Gruppe für stehen und dass die Gruppe in SharePoint ist, und versuchen Sie es anschließend erneut.|
> |**Name**:<br />SharePointUnableToCreateSiteGroup<br />**Hex**:<br />8004F0F7<br />**Nummer**:<br />-2147159817|Fehler bei der Erstellung der Website-Gruppe {0} in SharePoint.|
> |**Name**:<br />SharePointUnableToRemoveUserFromGroup<br />**Hex**:<br />8004F0F2<br />**Nummer**:<br />-2147159822|Benutzer {0} kann nicht aus der Gruppe {1} in SharePoint entfernt werden.|
> |**Name**:<br />SharePointUnableToRetrieveGroup<br />**Hex**:<br />8004F0F4<br />**Nummer**:<br />-2147159820|Gruppe {0} kann nicht von SharePoint abgerufen werden.|
> |**Name**:<br />SharePointUrlHostValidator<br />**Hex**:<br />8004F301<br />**Nummer**:<br />-2147159295|Die URL kann nicht zu einer IP-Adresse aufgelöst werden.|
> |**Name**:<br />SharePointUrlIsRootWebValidator<br />**Hex**:<br />8004F306<br />**Nummer**:<br />-2147159290|Die URL ist ungültig. Die URL muss eine gültige Websitesammlung sein und kann keine Unterwebsite enthalten. Die URL muss einem gültigen Formular entsprechen, beispielsweise http://SharePointServer/sites/CrmSite.|
> |**Name**:<br />SharePointVersionUnsupported<br />**Hex**:<br />800608B6<br />**Nummer**:<br />-2147088202|Microsoft Dynamics 365 kann keine Verbindung mit SharePoint herstellen, da die SharePoint-Version nicht unterstützt wird. Installieren Sie die richtige Version, und versuchen Sie es anschließend erneut. |
> |**Name**:<br />SimilarityRuleDisabled<br />**Hex**:<br />80071016<br />**Nummer**:<br />-2147020778|Für diese Entität ist keine Ähnlichkeitsregel aktiv.|
> |**Name**:<br />SimilarityRuleFCBOff<br />**Hex**:<br />80071018<br />**Nummer**:<br />-2147020776|Ähnlichkeitsregeln sind nicht aktiviert.|
> |**Name**:<br />SingletonMappingFoundForArrayParameter<br />**Hex**:<br />8004037e<br />**Nummer**:<br />-2147220610|Eine einzelne Transformationsparameterzuordnung ist für einen Arrayparameter definiert.|
> |**Name**:<br />SiteMapMissing<br />**Hex**:<br />80050016<br />**Nummer**:<br />-2147155946|Sie haben entweder keine Berechtigungen für diese Datensätze oder in der Siteübersicht ist ein Fehler aufgetreten. Wenden Sie sich an den -Administrator. Wenden Sie sich an den Systemadministrator. Wenn Sie der Administrator sind, können Sie zur Lösungsseite wechseln und eine andere Lösung importieren.|
> |**Name**:<br />SiteMapXsdValidationError<br />**Hex**:<br />8004F401<br />**Nummer**:<br />-2147159039|XSD Überprüfung für Siteübersichts-XMLs ist mit dem folgenden Fehler fehlgeschlagen: '{0}auf {1} Zeilenposition {2}.|
> |**Name**:<br />SkipValidDateTimeBehavior<br />**Hex**:<br />800608A3<br />**Nummer**:<br />-2147088221|Der Verhaltenswert für dieses Feld wurde ignoriert. Ein Systemanpasser muss den Verhaltenswert für das Feld direkt konfigurieren.|
> |**Name**:<br />SlaActivateDeactivateByNonOwner<br />**Hex**:<br />8004F872<br />**Nummer**:<br />-2147157902|Diese SLA kann nur vom Besitzer aktiviert oder deaktiviert werden.|
> |**Name**:<br />SlaAlreadyInactiveState<br />**Hex**:<br />8004F861<br />**Nummer**:<br />-2147157919|Sie können diesen Datensatz nicht aktivieren, da er bereits aktiv ist.|
> |**Name**:<br />SlaAlreadyInDraftState <br />**Hex**:<br />8004F862<br />**Nummer**:<br />-2147157918|Sie können diesen Datensatz nicht deaktivieren, da sich der ausgewählte Anspruch bereits im Status "Entwurf" befindet.|
> |**Name**:<br />SlaNotEnabledEntity<br />**Hex**:<br />80055003<br />**Nummer**:<br />-2147135485|SLA ist für diese Entität nicht aktiviert.|
> |**Name**:<br />SlaPermissionToPerformAction<br />**Hex**:<br />8004F875<br />**Nummer**:<br />-2147157899|Sie verfügen zum Durchführen dieser Aktion nicht über die erforderlichen Berechtigungen in SLAs und Prozessen.|
> |**Name**:<br />SnapshotReportNotReady<br />**Hex**:<br />80040489<br />**Nummer**:<br />-2147220343|Der ausgewählte Bericht ist nicht zum Anzeigen bereit. Der Bericht wird weiterhin erstellt, oder eine Berichtsmomentaufnahme ist nicht verfügbar. reportid:{0}|
> |**Name**:<br />SocialCareDisabledError<br />**Hex**:<br />80060621<br />**Nummer**:<br />-2147088863|Problem bei der Kommunikation mit Dynamics 365 Organization. Die Organisation ist möglicherweise nicht verfügbar, oder die Funktionen wird so festgelegt, dass sie keine sozialen Daten empfangen kann. Versuchen Sie es später noch einmal. Falls das Problem weiter besteht, wenden Sie sich an Ihren Microsoft Dynamics 365-Administrator.|
> |**Name**:<br />SolutionConcurrencyFailure<br />**Hex**:<br />80071151<br />**Nummer**:<br />-2147020463|Das Installieren oder Entfernen der Lösung ist fehlgeschlagen, da gleichzeitig eine andere Lösung installiert oder entfernt wurde. Versuchen Sie es später noch einmal.|
> |**Name**:<br />SolutionConfigurationPageMustBeHtmlWebResource<br />**Hex**:<br />8004701C<br />**Nummer**:<br />-2147192804|Die Lösungskonfigurationsseite muss in der Lösung vorhanden sein, die sie vertritt.|
> |**Name**:<br />SolutionImportCauseTimeout<br />**Hex**:<br />80048543<br />**Nummer**:<br />-2147187389|Bei dem Vorgang ist ein Timeout aufgetreten. Dies ist möglicherweise der Fall, weil eine Lösung derzeit in diese Umgebung importiert wird. Bitte versuchen Sie es noch einmal, nachdem der Lösungsimport abgeschlossen ist. Lösungen sollten möglicherweise außerhalb der Arbeitszeiten importiert werden, wenn möglich.|
> |**Name**:<br />SolutionRestrictedAttributes<br />**Hex**:<br />80072003<br />**Nummer**:<br />-2147016701|Komponente kann nicht erstellt werden, da sie bereits lösungsfähige Spalten umfasst. Entität: {0}, Vorhandenes Attribut: {1}|
> |**Name**:<br />SolutionUniqueNameViolation<br />**Hex**:<br />8004F023<br />**Nummer**:<br />-2147160029|Der eindeutige Name der Lösung '{0}ist bereits verwendet und kann nicht mehr verwendet werden.|
> |**Name**:<br />SolutionUpgradeFailed<br />**Hex**:<br />8004F046<br />**Nummer**:<br />-2147159994|Die Lösungsupgradeaktion ist fehlgeschlagen, nachdem der Import angehalten wurde. InnerException ist: {1}.|
> |**Name**:<br />SolutionUpgradeNotAvailable<br />**Hex**:<br />8004853B<br />**Nummer**:<br />-2147187397|"Die {0}-Lösung verfügt nicht über ein Upgrade, das zur Anwendung bereit ist."|
> |**Name**:<br />SolutionUpgradeWrongSolutionSelected<br />**Hex**:<br />8004853C<br />**Nummer**:<br />-2147187396|"Zur Verwendung dieser Aktion müssen Sie zuerst die alte Lösung auswählen und es dann erneut versuchen."|
> |**Name**:<br />SourceAttributeHeaderTooBig<br />**Hex**:<br />80044340<br />**Nummer**:<br />-2147204288|Spaltenüberschriften dürfen höchstens 160 Zeichen lang sein. Beheben Sie die Spaltenüberschriften, und führen Sie den Datenmigrations-Manager dann erneut aus.|
> |**Name**:<br />SourceEntityMappedToMultipleTargets<br />**Hex**:<br />8004033d<br />**Nummer**:<br />-2147220675|Diese Quellentität ist als einer Microsoft Dynamics 365-Entität zugeordnet. Entfernen Sie die mehrfachen Zuordnungen, und importieren Sie die Datenzuordnung anschließend erneut.|
> |**Name**:<br />SPAccountNameFetchFailure<br />**Hex**:<br />8006072A<br />**Nummer**:<br />-2147088598|Ausnahme beim Abrufen eines Firmennamens von SharePoint.|
> |**Name**:<br />SPAllFilesErrorScenario<br />**Hex**:<br />80060760<br />**Nummer**:<br />-2147088544|Eine oder mehrere Standorte in der Dateiansicht von SharePointDocument fielen aus.|
> |**Name**:<br />SPBadLockInFileCollectionErrorCode<br />**Hex**:<br />8006070A<br />**Nummer**:<br />-2147088630|Die Datei in der Sammlung hat eine fehlerhafte Sperre. |
> |**Name**:<br />SPCertificationError<br />**Hex**:<br />80060767<br />**Nummer**:<br />-2147088537|S2STokenIssuer-Zertifikat wurde nicht gefunden.|
> |**Name**:<br />SPConnectionFailure<br />**Hex**:<br />80060761<br />**Nummer**:<br />-2147088543|Fehler beim Verbinden mit SharePointSite.|
> |**Name**:<br />SPCurrentDocumentLocationDisabledErrorCode<br />**Hex**:<br />80060720<br />**Nummer**:<br />-2147088608|Aktueller Dokumentspeicherort wurde vom Administrator deaktiviert|
> |**Name**:<br />SPCurrentFolderAlreadyExistErrorCode<br />**Hex**:<br />80060721<br />**Nummer**:<br />-2147088607|Datensatz bereits in Datenbank vorhanden|
> |**Name**:<br />SPDataValidationFiledOnFieldAndListErrorCode<br />**Hex**:<br />80060713<br />**Nummer**:<br />-2147088621|Fehler bei der Datenüberprüfung am Feld und an der Liste|
> |**Name**:<br />SPDataValidationFiledOnFieldErrorCode<br />**Hex**:<br />80060711<br />**Nummer**:<br />-2147088623|Fehler bei der Datenüberprüfung am Feld|
> |**Name**:<br />SPDataValidationFiledOnListErrorCode<br />**Hex**:<br />80060712<br />**Nummer**:<br />-2147088622|Fehler bei der Datenüberprüfung an der Liste|
> |**Name**:<br />SPDefaultSiteNotPresent<br />**Hex**:<br />80060739<br />**Nummer**:<br />-2147088583|Die OneDrive-Aktivierung erfordert eine Standard-SharePoint-Website.|
> |**Name**:<br />SPDocumentMappingFailure<br />**Hex**:<br />80060734<br />**Nummer**:<br />-2147088588|Kann keine Dokumente ihrem Standort zuordnen.|
> |**Name**:<br />SPDuplicateValuesFoundErrorCode<br />**Hex**:<br />80060708<br />**Nummer**:<br />-2147088632|Das Listenelement konnte nicht aktualisiert werden, da doppelte Werte für mindestens ein Feld in der Liste gefunden wurden.|
> |**Name**:<br />SpecifyIncomingPassword<br />**Hex**:<br />8005E253<br />**Nummer**:<br />-2147098029|Für die eingehende Verbindung ist ein Kennwort erforderlich.|
> |**Name**:<br />SpecifyInComingPort<br />**Hex**:<br />8005E24F<br />**Nummer**:<br />-2147098033|Eingehenden Port angeben und erneut speichern|
> |**Name**:<br />SpecifyIncomingServerLocation<br />**Hex**:<br />8005E24B<br />**Nummer**:<br />-2147098037|Geben Sie die URL des Serverstandorts für eingehende E-Mails an|
> |**Name**:<br />SpecifyIncomingUserName<br />**Hex**:<br />8005E251<br />**Nummer**:<br />-2147098031|Für die eingehende Verbindung ist ein Benutzername erforderlich.|
> |**Name**:<br />SpecifyOutgoingPassword<br />**Hex**:<br />8005E254<br />**Nummer**:<br />-2147098028|Für die ausgehende Verbindung ist ein Kennwort erforderlich.|
> |**Name**:<br />SpecifyOutgoingPort<br />**Hex**:<br />8005E256<br />**Nummer**:<br />-2147098026|Ausgehenden Port angeben und erneut speichern|
> |**Name**:<br />SpecifyOutgoingServerLocation<br />**Hex**:<br />8005E24C<br />**Nummer**:<br />-2147098036|Geben Sie die URL des Serverstandorts für ausgehende E-Mails an|
> |**Name**:<br />SpecifyOutgoingUserName<br />**Hex**:<br />8005E252<br />**Nummer**:<br />-2147098030|Für die ausgehende Verbindung ist ein Benutzername erforderlich.|
> |**Name**:<br />SPExclusiveLockOnFileErrorCode<br />**Hex**:<br />80060705<br />**Nummer**:<br />-2147088635|Exklusive Sperre auf der Datei|
> |**Name**:<br />SPFileAlreadyCheckedOutErrorCode<br />**Hex**:<br />80060702<br />**Nummer**:<br />-2147088638|Die Datei ist bereits ausgecheckt.|
> |**Name**:<br />SPFileCheckedOutInvalidArgsErrorCode<br />**Hex**:<br />80060703<br />**Nummer**:<br />-2147088637|Die Argumente für das Auschecken sind nicht gültig.|
> |**Name**:<br />SPFileContentNullErrorCode<br />**Hex**:<br />8006070D<br />**Nummer**:<br />-2147088627|Der Inhalt der Dateierstellungsinformationen darf nicht Null sein.|
> |**Name**:<br />SPFileIsCheckedOutByOtherUser<br />**Hex**:<br />80060728<br />**Nummer**:<br />-2147088600|Die Datei ist an einen Benutzer ausgecheckt, bei dem es sich nicht um den aktuellen Benutzer handelt|
> |**Name**:<br />SPFileIsReadOnlyErrorCode<br />**Hex**:<br />8006070F<br />**Nummer**:<br />-2147088625|Feld ist schreibgeschützt|
> |**Name**:<br />SPFileNameModifiedErrorCode<br />**Hex**:<br />80060729<br />**Nummer**:<br />-2147088599|Die angegebene Ordner wurde nicht gefunden. Wenn Sie den automatisch generierten Ordnernamen für diesen Dokumentspeicherort direkt in SharePoint geändert haben, müssen Sie den Ordnernamen in Dynamics 365 ändern, damit er dem umbenannten Ordner entspricht. Führen Sie hierzu die Schritte aus, die Sie bearbeiten Speicherort und den entsprechenden Namen im gebiet Namen ein.|
> |**Name**:<br />SPFileNotCheckedOutErrorCode<br />**Hex**:<br />80060700<br />**Nummer**:<br />-2147088640|Die Datei ist nicht ausgecheckt.|
> |**Name**:<br />SPFileNotFoundErrorCode<br />**Hex**:<br />80060706<br />**Nummer**:<br />-2147088634|Datei wurde nicht gefunden|
> |**Name**:<br />SPFileNotLockedErrorCode<br />**Hex**:<br />80060707<br />**Nummer**:<br />-2147088633|Die Datei in der Sammlung ist nicht gesperrt.|
> |**Name**:<br />SPFileSizeMismatchErrorCode<br />**Hex**:<br />8006070E<br />**Nummer**:<br />-2147088626|Die Größe des geschriebenen Dokumentdatenstroms stimmt nicht mit der des eingegebenen Dokumentdatenstroms überein.|
> |**Name**:<br />SPFileTooLargeOrInfectedErrorCode<br />**Hex**:<br />80060709<br />**Nummer**:<br />-2147088631|Die Virusprüfung ergibt, dass die Datei mit einem Virus infiziert oder zu groß ist.|
> |**Name**:<br />SPFolderCreationFailure<br />**Hex**:<br />8004F0F0<br />**Nummer**:<br />-2147159824|Ordner mit diesem Namen kann nicht erstellt werden|
> |**Name**:<br />SPFolderNotFoundErrorCode<br />**Hex**:<br />8006071B<br />**Nummer**:<br />-2147088613|Ordner nicht gefunden|
> |**Name**:<br />SPFolderRenameFailure<br />**Hex**:<br />8006072C<br />**Nummer**:<br />-2147088596|Ausnahme beim Bearbeiten von SharePoint-Dokument-Eigenschaften.|
> |**Name**:<br />SPGenericErrorCode<br />**Hex**:<br />80060719<br />**Nummer**:<br />-2147088615|Fehler beim Ausführen dieses Vorgangs mit SharePoint|
> |**Name**:<br />SPIllegalCharactersInFileNameErrorCode<br />**Hex**:<br />8006071F<br />**Nummer**:<br />-2147088609|Ungültige Zeichen im Dateinamen|
> |**Name**:<br />SPIllegalFileTypeErrorCode<br />**Hex**:<br />8006071D<br />**Nummer**:<br />-2147088611|Ungültiger Dateityp|
> |**Name**:<br />SPInstanceOfRecurringEventErrorCode<br />**Hex**:<br />80060716<br />**Nummer**:<br />-2147088618|Das Listenelement ist eine Instanz eines wiederkehrenden Ereignisses, das keine Serienausnahme ist. Das Listenelement ist eine Workflowaufgabe, deren übergeordneter Workflow im Papierkorb ist, oder die übergeordnete Liste ist eine Dokumentbibliothek.|
> |**Name**:<br />SPIntermittentError<br />**Hex**:<br />80060764<br />**Nummer**:<br />-2147088540|Ein zeitweiliger Fehler ist aufgetreten. Bitte aktualisieren Sie das Raster, und versuchen Sie es erneut.|
> |**Name**:<br />SPInvalidDocumentLocation<br />**Hex**:<br />80060762<br />**Nummer**:<br />-2147088542|Ungültiger Sharepoint-Dokumentspeicherort-Typ|
> |**Name**:<br />SPInvalidFieldValueErrorCode<br />**Hex**:<br />8006071E<br />**Nummer**:<br />-2147088610|Ungültiger Feldwert|
> |**Name**:<br />SPInvalidLookupValuesErrorCode<br />**Hex**:<br />8006070B<br />**Nummer**:<br />-2147088629|Das Listenelement konnte nicht aktualisiert werden, da ungültige Nachschlagewerte für mindestens ein Feld in der Liste gefunden wurden.|
> |**Name**:<br />SPInvalidSavedQueryErrorCode<br />**Hex**:<br />80060718<br />**Nummer**:<br />-2147088616|Fehler beim Ausführen dieses Vorgangs mit SharePoint|
> |**Name**:<br />SPInvalidSubSite<br />**Hex**:<br />80060763<br />**Nummer**:<br />-2147088541|Unterwebsite-URL ist falsch formatiert|
> |**Name**:<br />SPItemNotExistErrorCode<br />**Hex**:<br />80060717<br />**Nummer**:<br />-2147088617|Listenelement ist nicht vorhanden|
> |**Name**:<br />SPMalFormedRelativeUrl<br />**Hex**:<br />80060766<br />**Nummer**:<br />-2147088538|Relative URL darf keine voran- oder nachgestellte Leerzeichen haben.|
> |**Name**:<br />SPModifiedOnServerErrorCode<br />**Hex**:<br />80060710<br />**Nummer**:<br />-2147088624|Das Listenelement wurde auf dem Server bearbeitet. Die Änderungen können also nicht bestätigt werden.|
> |**Name**:<br />SPMultipleOdbSitesError<br />**Hex**:<br />8006072D<br />**Nummer**:<br />-2147088595|Mehrere Standorte mit aktiviertem One Drive sind nicht zulässig.|
> |**Name**:<br />SPNoActiveDocumentLocationErrorCode<br />**Hex**:<br />8006071C<br />**Nummer**:<br />-2147088612|Kein aktiver Dokumentspeicherort|
> |**Name**:<br />SPNotAdminError<br />**Hex**:<br />80060765<br />**Nummer**:<br />-2147088539|Nur ein CRM-Administrator, der Mandantenadministrator ist, kann den Erstellungsvorgang ausführen|
> |**Name**:<br />SPNotEnabledError<br />**Hex**:<br />8006073A<br />**Nummer**:<br />-2147088582|Die SharePoint-Integration ist nicht für die Entität aktiviert.|
> |**Name**:<br />SPNotEnabledForEntity<br />**Hex**:<br />8006073B<br />**Nummer**:<br />-2147088581|Die SharePoint- und Microsoft Teams-Integration ist nicht für die Entität aktiviert.|
> |**Name**:<br />SPNullFileUrlErrorCode<br />**Hex**:<br />8006070C<br />**Nummer**:<br />-2147088628|Die URL der Dateierstellungsinformationen darf nicht Null und nicht ungültig sein.|
> |**Name**:<br />SPNullRegardingObjectErrorCode<br />**Hex**:<br />80060723<br />**Nummer**:<br />-2147088605|Bezug-Objekt-ID ist Null|
> |**Name**:<br />SPOdbDisabledError<br />**Hex**:<br />8006072E<br />**Nummer**:<br />-2147088594|Aktivieren Sie unter ODB Funktionen (das Laufwerk für Unternehmen), um ODB-Standort erstellen.|
> |**Name**:<br />SPOdbDuplicateLocationError<br />**Hex**:<br />80060735<br />**Nummer**:<br />-2147088587|Mehr als ein ODB-Speicherort (OneDrive for Business) ist nicht zulässig.|
> |**Name**:<br />SPOdbUpdateDeleteError<br />**Hex**:<br />8006072F<br />**Nummer**:<br />-2147088593|Sie können ODB Website (One Drive for Business) nicht aktualisieren oder löschen.|
> |**Name**:<br />SPOdbUpdateDeleteLocationError<br />**Hex**:<br />80060736<br />**Nummer**:<br />-2147088586|Sie können SharePoint-Dokumentorte vom Typ ODB (OneDrive for Business) weder aktualisieren noch löschen.|
> |**Name**:<br />SPOperationNotSupportedErrorCode<br />**Hex**:<br />80060715<br />**Nummer**:<br />-2147088619|Die Liste unterstützt diesen Vorgang nicht.|
> |**Name**:<br />SPOperatorNotSupportedErrorCode<br />**Hex**:<br />80060724<br />**Nummer**:<br />-2147088604|{0} unterstützt den ausgewählten Operator nicht|
> |**Name**:<br />SPPersonalSiteNotFound<br />**Hex**:<br />8006072B<br />**Nummer**:<br />-2147088597|Persönliche Website nicht gefunden für den Benutzer.|
> |**Name**:<br />SPRequiredColCheckInErrorCode<br />**Hex**:<br />80060725<br />**Nummer**:<br />-2147088603|Ausnahme beim Einchecken des Dokuments, da in SharePoint einige Spalten erforderlich gemacht werden|
> |**Name**:<br />SPSearchOneDriveNotCreated<br />**Hex**:<br />80060737<br />**Nummer**:<br />-2147088585|Der OneDrive-Speicherort ist noch nicht erstellt. Erstellen Sie den Ort, den Sie suchen.|
> |**Name**:<br />SPSharedLockOnFileErrorCode<br />**Hex**:<br />80060704<br />**Nummer**:<br />-2147088636|Gemeinsame Sperre auf der Datei|
> |**Name**:<br />SPSiteNotFoundErrorCode<br />**Hex**:<br />8006071A<br />**Nummer**:<br />-2147088614|Standort nicht gefunden|
> |**Name**:<br />SPSiteProtocolError<br />**Hex**:<br />80060738<br />**Nummer**:<br />-2147088584|Protokollfehler beim Zugriff auf SharePoint|
> |**Name**:<br />SPThrottlingLimitExceededErrorCode<br />**Hex**:<br />80060714<br />**Nummer**:<br />-2147088620|Der Einschränkungsgrenzwert wird mit diesem Vorgang überschritten.|
> |**Name**:<br />SPUnauthorizedAccessErrorCode<br />**Hex**:<br />80060701<br />**Nummer**:<br />-2147088639|Der aktuelle Benutzer hat keine ausreichenden Rechte.|
> |**Name**:<br />SPUploadFailure<br />**Hex**:<br />80060740<br />**Nummer**:<br />-2147088576|Fehler beim Hochladen in SharePoint aufgrund unbekannter Gründe. Wahrscheinlich ist die Datei zu groß.|
> |**Name**:<br />SqlArithmeticOverflowError<br />**Hex**:<br />80041136<br />**Nummer**:<br />-2147217098|Ein arithmetischer SQL-Überlauffehler ist aufgetreten|
> |**Name**:<br />SqlEncryption<br />**Hex**:<br />80048518<br />**Nummer**:<br />-2147187432|Fehler in der Datenverschlüsselung.|
> |**Name**:<br />SqlEncryptionCannotOpenSymmetricKeyBecauseDatabaseMasterKeyDoesNotExistOrIsNotOpened<br />**Hex**:<br />8004851A<br />**Nummer**:<br />-2147187430|Symmetrischen Schlüssel kann nicht geöffnet werden, da der Datenbank-Masterschlüssel nicht in der Datenbank vorhanden ist oder nicht geöffnet wird.|
> |**Name**:<br />SqlEncryptionCertificateDoesNotExist<br />**Hex**:<br />8004851D<br />**Nummer**:<br />-2147187427|Zertifikat mit Name="{0}" befindet sich nicht in der Datenbank.|
> |**Name**:<br />SqlEncryptionChangeEncryptionKeyExceededQuotaForTheInterval<br />**Hex**:<br />80048529<br />**Nummer**:<br />-2147187415|"Änderung"-Schlüssel wurde bereits {0}-mal in den letzten {1} Minuten ausgeführt. Bitte warten Sie ein paar Minuten und versuchen Sie es anschließend erneut.|
> |**Name**:<br />SqlEncryptionCreateCertificateError<br />**Hex**:<br />8004851E<br />**Nummer**:<br />-2147187426|Zertifikat mit Name="{0}" kann erstellt werden, da es bereits vorhanden ist.|
> |**Name**:<br />SqlEncryptionCreateDatabaseMasterKeyError<br />**Hex**:<br />8004851B<br />**Nummer**:<br />-2147187429|Datenbank-Hauptschlüssel kann nicht erstellt werden, da er bereits vorhanden ist.|
> |**Name**:<br />SqlEncryptionCreateSymmetricKeyError<br />**Hex**:<br />80048521<br />**Nummer**:<br />-2147187423|Symmetrischer Schlüssel mit Name="{0}" kann erstellt werden, da es bereits vorhanden ist.|
> |**Name**:<br />SqlEncryptionDatabaseMasterKeyDoesNotExist<br />**Hex**:<br />80048519<br />**Nummer**:<br />-2147187431|Der Datenbank-Masterschlüssel befindet sich nicht in der Datenbank.|
> |**Name**:<br />SqlEncryptionDeleteCertificateError<br />**Hex**:<br />8004851F<br />**Nummer**:<br />-2147187425|Zertifikat mit Name="{0}" kann gelöscht werden, da es nicht vorhanden ist.|
> |**Name**:<br />SqlEncryptionDeleteDatabaseMasterKeyError<br />**Hex**:<br />8004851C<br />**Nummer**:<br />-2147187428|Datenbank-Masterschlüssel kann nicht gelöscht werden, da er nicht vorhanden ist.|
> |**Name**:<br />SqlEncryptionDeleteEncryptionKeyError<br />**Hex**:<br />80048526<br />**Nummer**:<br />-2147187418|Der Schlüssel kann nicht gelöscht werden.|
> |**Name**:<br />SqlEncryptionDeleteSymmetricKeyError<br />**Hex**:<br />80048522<br />**Nummer**:<br />-2147187422|Symmetrischer Schlüssel mit Name="{0}" kann gelöscht werden, da es nicht vorhanden ist.|
> |**Name**:<br />SqlEncryptionEncryptionDecryptionTestError<br />**Hex**:<br />80048523<br />**Nummer**:<br />-2147187421|Fehler beim Testen von Datenverschlüsselung und -entschlüsselung.|
> |**Name**:<br />SqlEncryptionEncryptionKeyValidationError<br />**Hex**:<br />80048528<br />**Nummer**:<br />-2147187416|Der neue Schlüssel erfüllt nicht die Schlüsselbedingungen der starken Verschlüsselung. Der Schlüssel muss zwischen 10 und 100 Zeichen lang sein und mindestens eine Zahl, mindestens einen Buchstaben und mindestens ein Symbol oder Sonderzeichen enthalten. {0}|
> |**Name**:<br />SqlEncryptionIsActiveCannotRestoreEncryptionKey<br />**Hex**:<br />80048525<br />**Nummer**:<br />-2147187419|Kann "Aktivieren"-Schlüssel nicht ausführen, da der Schlüssel bereits festgelegt ist und funktioniert. Mit "Änderungs" Schlüssel werden.|
> |**Name**:<br />SqlEncryptionIsInactiveCannotChangeEncryptionKey<br />**Hex**:<br />80048527<br />**Nummer**:<br />-2147187417|Kann "Ändern"-Schlüssel nicht ausführen, da der Schlüssel nicht festgelegt ist oder nicht funktioniert. Verwenden Sie erst den Schlüssel "Aktivieren" anstatt den korrekten aktuellen Schlüssel festzulegen. Verwenden Sie dann die Verschlüsselung "Änderung", wenn Sie Daten mithilfe eines neuen Schlüssels erneut verschlüsseln möchten.|
> |**Name**:<br />SqlEncryptionKeyCannotDecryptExistingData<br />**Hex**:<br />80048524<br />**Nummer**:<br />-2147187420|Die vorhandenen verschlüsselten Daten können nicht mit dem aktuellen Schlüssel entschlüsselt werden (Entity="{0}, Attribute={1}"). "Rollup "aktiviert Schlüssel", dass den korrekten Schlüssel festlegt.|
> |**Name**:<br />SqlEncryptionRestoreEncryptionKeyCannotDecryptExistingData<br />**Hex**:<br />8004852B<br />**Nummer**:<br />-2147187413|"Aktivieren" kann nicht ausgeführt werden, da der Schlüssel nicht zu dem ursprünglichen Schlüssel passt, mit dem die Daten verschlüsselt wurden.|
> |**Name**:<br />SqlEncryptionSetEncryptionKeyIsAlreadyRunningCannotRunItInParallel<br />**Hex**:<br />8004852A<br />**Nummer**:<br />-2147187414|Vom System wird derzeit einer Anforderung "Ändern "oder "Aktivieren" des Schlüssels ausgeführt. Warten Sie bitte, bevor Sie eine andere Anfrage stellen.|
> |**Name**:<br />SqlEncryptionSymmetricKeyCannotOpenBecauseWrongPassword<br />**Hex**:<br />80048530<br />**Nummer**:<br />-2147187408|Symmetrischer Schlüssel kann nicht geöffnet werden, da das Passwort falsch ist.|
> |**Name**:<br />SqlEncryptionSymmetricKeyDoesNotExist<br />**Hex**:<br />80048520<br />**Nummer**:<br />-2147187424|Symmetrischer Schlüssel mit Name={0} befindet sich nicht in der Datenbank.|
> |**Name**:<br />SqlEncryptionSymmetricKeyDoesNotExistOrNoPermission<br />**Hex**:<br />8004852F<br />**Nummer**:<br />-2147187409|Symmetrischer Schlüssel kann nicht geöffnet werden, weil er nicht in der Datenbank nicht vorhanden ist, oder der Benutzer nicht berechtigt ist.|
> |**Name**:<br />SqlEncryptionSymmetricKeyPasswordDoesNotExistInConfigDB<br />**Hex**:<br />8004852E<br />**Nummer**:<br />-2147187410|Passwort des symmetrischen Schlüssels ist in der Config-Datenbank nicht vorhanden.|
> |**Name**:<br />SqlEncryptionSymmetricKeySourceDoesNotExistInConfigDB<br />**Hex**:<br />8004852D<br />**Nummer**:<br />-2147187411|Quelle des symmetrischen Schlüssels ist in der Config-Datenbank nicht vorhanden.|
> |**Name**:<br />SqlErrorInStoredProcedure<br />**Hex**:<br />8004C001<br />**Nummer**:<br />-2147172351|SQL-Fehler aufgetreten in {0} der gespeicherten Prozeduren auf {1}|
> |**Name**:<br />SqlMaxRecursionExceeded<br />**Hex**:<br />80044157<br />**Nummer**:<br />-2147204777|Die maximale Rekursion wurde vor Anweisungsvervollständigung erreicht.|
> |**Name**:<br />SrsDataConnectorNotInstalled<br />**Hex**:<br />80040492<br />**Nummer**:<br />-2147220334|MSCRM-Daten-Connektor nicht installiert|
> |**Name**:<br />SrsDataConnectorNotInstalledUpload<br />**Hex**:<br />80048292<br />**Nummer**:<br />-2147188078|Dieser Bericht kann nicht hochgeladen werden, da die für die Berichterstellung erforderlichen Komponenten, Dynamics 365 Reporting Extensions, auf dem Server mit Microsoft SQL Server Reporting Services nicht installiert sind.|
> |**Name**:<br />SSM_MaxPCI_Exceeded<br />**Hex**:<br />80072570<br />**Nummer**:<br />-2147015312|Bitte melden Sie sich noch einmal an, um Ihre Sitzung zu aktualisieren.|
> |**Name**:<br />SSM_RefreshToken_Failed<br />**Hex**:<br />80072571<br />**Nummer**:<br />-2147015311|Fehler beim Aktualisieren der Anmeldesitzung.|
> |**Name**:<br />StageEntityIsNull<br />**Hex**:<br />80060451<br />**Nummer**:<br />-2147089327|Überprüfungsfehler: Phasenentität darf nicht Null sein.|
> |**Name**:<br />StageIdIsEmpty<br />**Hex**:<br />80060454<br />**Nummer**:<br />-2147089324|Überprüfungsfehler: Phasen-ID darf nicht leer sein.|
> |**Name**:<br />StageIdIsNotPresentInBusinessProcess<br />**Hex**:<br />80060450<br />**Nummer**:<br />-2147089328|Überprüfungsfehler: Phasen-ID „{0}” ist im Geschäftsprozess nicht vorhanden. Wenden Sie sich an Ihren Systemadministrator.|
> |**Name**:<br />StageIdIsNotValid<br />**Hex**:<br />80060458<br />**Nummer**:<br />-2147089320|Überprüfungsfehler: Phasen-ID ist für den Geschäftsprozess ungültig.|
> |**Name**:<br />StateTransitionActivateNewStatus<br />**Hex**:<br />8004F857<br />**Nummer**:<br />-2147157929|Sie können diesen Datensatz aufgrund der Regeln für den Statusübergang nicht aktivieren. Wenden Sie sich an den Systemadministrator.|
> |**Name**:<br />StateTransitionActiveToCanceled<br />**Hex**:<br />8004F855<br />**Nummer**:<br />-2147157931|Wegen der Regeln für den Statusübergang können Sie Anfragen im aktuellen Status nicht stornieren. Ändern Sie den Anfragenstatus, und versuchen Sie ihn zu stornieren, oder wenden Sie sich an den Systemadministrator.|
> |**Name**:<br />StateTransitionActiveToResolve<br />**Hex**:<br />8004F854<br />**Nummer**:<br />-2147157932|Aufgrund der Regeln für den Statusübergang können Sie eine Anfrage im aktuellen Status nicht lösen. Ändern Sie vor der Auflösung der Anfrage den Anfragenstatus, oder wenden Sie sich an den Systemadministrator.|
> |**Name**:<br />StateTransitionDeactivateNewStatus<br />**Hex**:<br />8004F858<br />**Nummer**:<br />-2147157928|Sie können diesen Datensatz aufgrund der Regeln für den Statusübergang nicht deaktivieren. Wenden Sie sich an den Systemadministrator.|
> |**Name**:<br />StateTransitionResolvedOrCanceledToActive<br />**Hex**:<br />8004F856<br />**Nummer**:<br />-2147157930|Aufgrund der Regeln für den Statusübergang können Sie die Anfrage vom aktuellen Status aus nicht aktivieren. Wenden Sie sich an den Systemadministrator.|
> |**Name**:<br />StepAutomaticallyDisabled<br />**Hex**:<br />80045043<br />**Nummer**:<br />-2147200957|Das ursprüngliche sdkmessageprocessingstep ist deaktiviert oder wurde ersetzt.|
> |**Name**:<br />StepCountInXamlExceedsMaxAllowed<br />**Hex**:<br />80060414<br />**Nummer**:<br />-2147089388|Für {0} {1} in XAML. Das erlaubte Maximum ist {2}.|
> |**Name**:<br />StepDoesNotHaveAnyChildInXaml<br />**Hex**:<br />80060416<br />**Nummer**:<br />-2147089386|{0} hat nicht mindestens ein {1} als untergeordnetes Element.|
> |**Name**:<br />StepNotSupportedForClientBusinessRule<br />**Hex**:<br />80060000<br />**Nummer**:<br />-2147090432|Schritt {0} wird für clientseitige Geschäftsregel nichtunterstützt.|
> |**Name**:<br />StepStepDoesNotHaveAnyControlStepAsItsChildren<br />**Hex**:<br />80060409<br />**Nummer**:<br />-2147089399|StepStep ist kein ControlStep als seine untergeordnetes Element|
> |**Name**:<br />StoredProcedureContext<br />**Hex**:<br />8004C002<br />**Nummer**:<br />-2147172350|Dynamics 365-Fehler {0} in {1}:{2}|
> |**Name**:<br />StringAttributeIndexError<br />**Hex**:<br />8004D292<br />**Nummer**:<br />-2147167598|Eines der Attirbuter der ausgewählten Entität ist Teil des Datenbankindex und kann deshalb maximal 900 Bytes groß sein.|
> |**Name**:<br />StringLengthTooLong<br />**Hex**:<br />80044331<br />**Nummer**:<br />-2147204303|Ein Validierungsfehler ist aufgetreten. Ein bereitgestellter Zeichenfolgenwert ist zu lang.|
> |**Name**:<br />SubcomponentDoesNotExist<br />**Hex**:<br />80048537<br />**Nummer**:<br />-2147187401|Unterkomponente {0} vom Typ {1} können in der Organisation nicht gefunden werden. Sie können nicht auf SolutionComponents hinzugefügt werden.|
> |**Name**:<br />SubcomponentMissingARoot<br />**Hex**:<br />80048536<br />**Nummer**:<br />-2147187402|Unterkomponente {0} kann nicht zur Lösung hinzugefügt werden, da die Stammkomponente fehlen {1}.|
> |**Name**:<br />SubjectDoesNotExist<br />**Hex**:<br />80043e02<br />**Nummer**:<br />-2147205630|Subjekt nicht vorhanden.|
> |**Name**:<br />SubjectLoopBeingCreated<br />**Hex**:<br />80043e01<br />**Nummer**:<br />-2147205631|Durch das Erstellen dieser übergeordneten Zuordnung würde eine Schleife in der Hierarchie „Betreffe” erstellt werden.|
> |**Name**:<br />SubjectLoopExists<br />**Hex**:<br />80043e00<br />**Nummer**:<br />-2147205632|Schleife ist in der Betreffhierarchie vorhanden.|
> |**Name**:<br />SubReportDoesNotExist<br />**Hex**:<br />80040493<br />**Nummer**:<br />-2147220333|Unterbericht ist nicht vorhanden. reportid:{0}|
> |**Name**:<br />SubscriptionGone<br />**Hex**:<br />80072513<br />**Nummer**:<br />-2147015405|Subscription expired|
> |**Name**:<br />SupportLogOnExpired<br />**Hex**:<br />8004A108<br />**Nummer**:<br />-2147180280|Support-Anmeldung ist abgelaufen ist|
> |**Name**:<br />SupportUserCannotBeCreateNorUpdated<br />**Hex**:<br />80041d41<br />**Nummer**:<br />-2147214015|Der Supportbenutzer kann weder erstellt noch aktualisiert werden.|
> |**Name**:<br />SyncAttributeMappingCannotBeUpdated<br />**Hex**:<br />80060741<br />**Nummer**:<br />-2147088575|Die Synchronisierungsattributs-Zuordnung ist nicht möglich.|
> |**Name**:<br />SyncToMsdeFailure<br />**Hex**:<br />80048407<br />**Nummer**:<br />-2147187705|Der Offlinemodus der MSDE-Datenbank konnte nicht gestartet oder verbunden werden.|
> |**Name**:<br />SystemAttributeMap<br />**Hex**:<br />80046205<br />**Nummer**:<br />-2147196411|InvalidAttributeMap-Fehler aufgetreten|
> |**Name**:<br />SystemEntityMap<br />**Hex**:<br />80046202<br />**Nummer**:<br />-2147196414|SystemEntityMap Fehler ist aufgetreten|
> |**Name**:<br />SystemFormCopyUnmatchedEntity<br />**Hex**:<br />8004F656<br />**Nummer**:<br />-2147158442|Die Entität für das Ziel und die SourceId müssen übereinstimmen.|
> |**Name**:<br />SystemFormCopyUnmatchedFormType<br />**Hex**:<br />8004F657<br />**Nummer**:<br />-2147158441|Der Formulartyp der SourceId ist für die Zielentität nicht gültig.|
> |**Name**:<br />SystemFormCreateWithExistingLabel<br />**Hex**:<br />8004F658<br />**Nummer**:<br />-2147158440|Die Beschriftung '{0}, ID: {1}ist bereits vorhanden. Zubehör eindeutige Werte.|
> |**Name**:<br />SystemFormImportMissingRoles<br />**Hex**:<br />8004F655<br />**Nummer**:<br />-2147158443|Diese Aktion ist nicht zulässig, da dadurch das Ausweichformular vom Typ 'XML für die Entität entfernt würde. Alle displaycondition-Attribute, die auf diese Sicherheitsrollen verweisen, werden entfernt.|
> |**Name**:<br />SystemUserDisabled<br />**Hex**:<br />8004A112<br />**Nummer**:<br />-2147180270|Dem Systembenutzer wurde für das abgelaufene Ticket deaktiviert.|
> |**Name**:<br />TamperedAuthTicket<br />**Hex**:<br />8004A105<br />**Nummer**:<br />-2147180283|Das Ticket, das zur Authentifizierung angegeben wurde, wurde manipuliert oder ist ungültig.|
> |**Name**:<br />TargetAttributeInvalidForIgnore<br />**Hex**:<br />80048500<br />**Nummer**:<br />-2147187456|Zielattributname muss leer sein, wenn processcode ignoriert wird.|
> |**Name**:<br />TargetAttributeInvalidForMap<br />**Hex**:<br />80040394<br />**Nummer**:<br />-2147220588|Dieses Attribut ist für die Zuordnung nicht gültig.|
> |**Name**:<br />TargetAttributeNotFound<br />**Hex**:<br />80040392<br />**Nummer**:<br />-2147220590|In der Datei wird ein Attribut angegeben, das nicht in Microsoft Dynamics 365 vorhanden ist.|
> |**Name**:<br />TargetEntityInvalidForMap<br />**Hex**:<br />80040395<br />**Nummer**:<br />-2147220587|In der Datei ist eine Entität angegeben, die für die Datenmigration ungültig ist: .|
> |**Name**:<br />TargetEntityNotFound<br />**Hex**:<br />80040391<br />**Nummer**:<br />-2147220591|In der Datei wird eine Entität angegeben, die nicht in Microsoft Dynamics 365 vorhanden ist.|
> |**Name**:<br />TargetEntityNotMapped<br />**Hex**:<br />80048460<br />**Nummer**:<br />-2147187616|Ziel-Entitätsname nicht für Quell{0} Datei definiert.|
> |**Name**:<br />TargetUserInsufficientPrivileges<br />**Hex**:<br />80048342<br />**Nummer**:<br />-2147187902|Der Benutzer kann dem Team nicht hinzugefügt werden, weil der Benutzer nicht über das Recht "{0}" verfügt.|
> |**Name**:<br />TaskFlowEmptyName<br />**Hex**:<br />80061712<br />**Nummer**:<br />-2147084526|Das Namensfeld darf nicht leer sein. Geben Sie einen Namen ein.|
> |**Name**:<br />TaskFlowEntityAttributeIsNotValid<br />**Hex**:<br />80061717<br />**Nummer**:<br />-2147084521|Ungültiger Attributtyp: {0}.{1}.|
> |**Name**:<br />TaskFlowEntityRelationshipIsNotValid<br />**Hex**:<br />80061716<br />**Nummer**:<br />-2147084522|Ungültiger Geschäftsbeziehungstyp: {0}|
> |**Name**:<br />TaskFlowFormXmlNotFound<br />**Hex**:<br />80061713<br />**Nummer**:<br />-2147084525|Das Systemformular {0} für Aufgabenfluss {1} wurde nicht gefunden.|
> |**Name**:<br />TaskFlowInvalidCharactersInName<br />**Hex**:<br />80061711<br />**Nummer**:<br />-2147084527|Das Feld "Name" darf nur alphanumerische Zeichen enthalten.|
> |**Name**:<br />TaskFlowMaxNumberControls<br />**Hex**:<br />80061719<br />**Nummer**:<br />-2147084519|Der Aufgabenfluss hat die maximal zulässige Anzahl der Steuerelemente überschritten ({0}). Um fortzufahren, müssen Sie einige Steuerelemente entfernen.|
> |**Name**:<br />TaskFlowMaxNumberPages<br />**Hex**:<br />80061718<br />**Nummer**:<br />-2147084520|Der Aufgabenfluss hat die maximal zulässige Anzahl der Seiten überschritten ({0}). Um fortzufahren, müssen Sie einige Seiten entfernen.|
> |**Name**:<br />TaskFlowNameIsNotUnique<br />**Hex**:<br />80061710<br />**Nummer**:<br />-2147084528|Es Aufgabenfluss mit dem angegebenen Namen ist bereits vorhanden.  Geben Sie einen eindeutigen Namen an.|
> |**Name**:<br />TaskFlowNotFound<br />**Hex**:<br />80061720<br />**Nummer**:<br />-2147084512|Ein Aufgabenfluss, der versucht zu starten, ist auf dem Gerät nicht verfügbar. Sie sind möglicherweise nicht berechtigt für den Zugriff, oder er ist in der Organisation nicht verfügbar. Wenden Sie sich an Ihren Systemadministrator.|
> |**Name**:<br />TaskFlowNotValid<br />**Hex**:<br />8006172F<br />**Nummer**:<br />-2147084497|Die Aufgabenflussdefinition ist ungültig.|
> |**Name**:<br />TaskFlowPageMissingFormXmlTab<br />**Hex**:<br />80061714<br />**Nummer**:<br />-2147084524|Die Seiten {0} für Aufgabenflow {1} Schritt {2} wurden nicht gefunden.|
> |**Name**:<br />TaskFlowUnsupportedEntities<br />**Hex**:<br />80061715<br />**Nummer**:<br />-2147084523|Die folgenden Entitäten sind nicht für Aufgabenflüsse aktiviert: {0}.|
> |**Name**:<br />TeamAdministratorMissedPrivilege<br />**Hex**:<br />80041d0a<br />**Nummer**:<br />-2147214070|Der Teamadministrator besitzt keine Rechtsleseteam.|
> |**Name**:<br />TeamInWrongBusiness<br />**Hex**:<br />8004140d<br />**Nummer**:<br />-2147216371|Zum Team mit ID = {0} gehört eine andere Unternehmenseineit = {1} als die Rolle mit roleId = {2} und roleBusinessUnit = {3}.|
> |**Name**:<br />TeamNameTooLong<br />**Hex**:<br />80048305<br />**Nummer**:<br />-2147187963|Der angegebene Name für das Team ist zu lang.|
> |**Name**:<br />TeamNotAssignedRoles<br />**Hex**:<br />80042f0a<br />**Nummer**:<br />-2147209462|Dem Team ist keine Rollen zugewiesen worden.|
> |**Name**:<br />TemplateNotAllowedForInternetMarketing<br />**Hex**:<br />80048475<br />**Nummer**:<br />-2147187595|Das Erstellen von Vorlagen mit Internetmarketing-Kampagnenaktivitäten ist nicht zulässig|
> |**Name**:<br />TemplateTypeNotSupportedForUnsubscribeAcknowledgement<br />**Hex**:<br />80040324<br />**Nummer**:<br />-2147220700|Der Vorlagentyp wird für die Abonnementkündigungsbestätigungs-E-Mail nicht unterstützt.|
> |**Name**:<br />TenantIDIsEmpty<br />**Hex**:<br />8005E25A<br />**Nummer**:<br />-2147098022|Das Feld „Exchange Online-Mandanten-ID” darf nicht leer sein.|
> |**Name**:<br />TenantIDValueChanged<br />**Hex**:<br />8005E25C<br />**Nummer**:<br />-2147098020|Die erkannte tenantId für den Austausch unterscheidet sich von jenem, den Sie gespeichert haben.|
> |**Name**:<br />TestEmailConfigurationScheduledInProgress<br />**Hex**:<br />8005E248<br />**Nummer**:<br />-2147098040|Geplanter E-Mail-Konfigurationstest wird durchgeführt. Bitte Speichern nach Beendigung des Tests.|
> |**Name**:<br />TextAnalyticsAPIActiveConfigurationDoesNotExist<br />**Hex**:<br />80061690<br />**Nummer**:<br />-2147084656|Für die Entität ist keine aktive Konfiguration vorhanden.|
> |**Name**:<br />TextAnalyticsAPIActiveSimilarityConfigurationDoesNotExist<br />**Hex**:<br />80061695<br />**Nummer**:<br />-2147084651|Keine aktive Ähnlichkeitsregel vorhanden. Der Systemadministrator muss eine Ähnlichkeitsregelkonfiguration installieren.|
> |**Name**:<br />TextAnalyticsAPIAllowedOnlyForEnglishLanguage<br />**Hex**:<br />80061691<br />**Nummer**:<br />-2147084655|Die Textanalysefunktion ist für Organisationen mit der Ausgangssprache Englisch verfügbar.|
> |**Name**:<br />TextAnalyticsAPIAzureUnableToConnectWithBuild<br />**Hex**:<br />80061692<br />**Nummer**:<br />-2147084654|Dynamics 365 konnte keine Verbindung mit dem Azure-Textanalyseservice herstellen. Überprüfen Sie, ob die URI und der Azure-Firmenschlüssel gültig sind und das Serviceabonnement aktiv ist.|
> |**Name**:<br />TextAnalyticsAzureConnectionCascadeActivateFailed<br />**Hex**:<br />80061634<br />**Nummer**:<br />-2147084748|Mindestens ein Textanalysemodell kann nicht aktiviert werden. Versuchen Sie, die vorhandenen Textanalysemodelle separat zu aktivieren von der Azure Service-Verbindung.|
> |**Name**:<br />TextAnalyticsAzureConnectionFailed<br />**Hex**:<br />80061650<br />**Nummer**:<br />-2147084720|Verbindung zwischen  und Dienst "Textanalyse" herstellen|
> |**Name**:<br />TextAnalyticsAzureSchedulerError<br />**Hex**:<br />80061693<br />**Nummer**:<br />-2147084653|Dynamics 365 konnte keine Verbindung mit dem Azure-Textanalyseservice herstellen. Versuchen Sie es erneut. Sollte das Problem weiterhin auftreten, wenden Sie sich an den Systemadministrator.|
> |**Name**:<br />TextAnalyticsAzureTestConnectionFailed<br />**Hex**:<br />80061632<br />**Nummer**:<br />-2147084750|Fehler beim Herstellen einer Verbindung mit dem Azure-Dienst "Textanalyse". Überprüfen Sie, ob die URL und der Azure-Firmenschlüssel gültig sind und das Serviceabonnement aktiv ist.|
> |**Name**:<br />TextAnalyticsAzureUnableToConnectWithBuild<br />**Hex**:<br />80061655<br />**Nummer**:<br />-2147084715|Dynamics 365 konnte keine Verbindung mit dem Azure-Textanalyseservice herstellen. Überprüfen Sie, ob die URI und der Azure-Firmenschlüssel gültig sind und das Serviceabonnement aktiv ist.|
> |**Name**:<br />TextAnalyticsFeatureNotEnabled<br />**Hex**:<br />80061652<br />**Nummer**:<br />-2147084718|Die Textanalysefunktion Azure ist nicht aktiviert. Der Systemadministrator muss diese Funktion aktivieren und die erforderliche Konfiguration installieren.|
> |**Name**:<br />TextAnalyticsMappingUsedForActiveConfiguration<br />**Hex**:<br />80061667<br />**Nummer**:<br />-2147084697|Diese Textanalyseentitätszuordnung wird für eine aktive Konfiguration verwendet. Es kann nicht geändert oder gelöscht werden, solange es von einer aktiven Konfiguration verwendet wird.|
> |**Name**:<br />TextAnalyticsMaxLimitForTopicModelReached<br />**Hex**:<br />80061694<br />**Nummer**:<br />-2147084652|Die maximale Anzahl der zulässigen Themenmodelle für Ihre Organisation wurde erreicht.|
> |**Name**:<br />TextAnalyticsModelActivateConnectionMustBeActive<br />**Hex**:<br />80061657<br />**Nummer**:<br />-2147084713|-Die Azure Machine Learing TextanalyseService-Empfehlung muss aktiviert sein, bevor ein Modell erstellt werden kann. Aktivieren Sie die Verbindung zum Textanalyseservice und versuchen Sie es erneut.|
> |**Name**:<br />ThemeIdOrUpdateTimestampIsNull<br />**Hex**:<br />800608D1<br />**Nummer**:<br />-2147088175|In den Designeinstellungen ist keine Design-ID oder kein Aktualisierungszeitstempel vorhanden.|
> |**Name**:<br />Einschränken<br />**Hex**:<br />8005F103<br />**Nummer**:<br />-2147094269|Zu viele Anforderungen.|
> |**Name**:<br />ThrottlingBurstRequestLimitExceededError<br />**Hex**:<br />80072322<br />**Nummer**:<br />-2147015902|Die Anzahl der Anforderungen hat das Limit von {0} in einem Zeitfenster von {1} Sekunden überschritten.|
> |**Name**:<br />ThrottlingConcurrencyLimitExceededError<br />**Hex**:<br />80072326<br />**Nummer**:<br />-2147015898|Die Anzahl gleichzeitig ausgeführter Anforderungen hat das Limit von {0} überschritten.|
> |**Name**:<br />ThrottlingTimeExceededError<br />**Hex**:<br />80072321<br />**Nummer**:<br />-2147015903|Die kombinierte Ausführungszeit von eingehenden Anforderungen hat das Limit von {0} Millisekunden in einem Zeitfenster von {1} Sekunden überschritten. Verringern Sie die Anzahl der gleichzeitigen Anforderungen oder reduzieren Sie die Dauer der Anforderungen und versuchen Sie es später noch einmal.|
> |**Name**:<br />TooManyBytesInInputStream<br />**Hex**:<br />8004F901<br />**Nummer**:<br />-2147157759|Der Stream, der gelesen wird, hat zu viele Bytes.|
> |**Name**:<br />TooManyCalculatedFieldsInQuery<br />**Hex**:<br />80060429<br />**Nummer**:<br />-2147089367|Die Anzahl der berechneten Felder in der Abfrage hat den Höchstwert von {0} überschritten.|
> |**Name**:<br />TooManyConditionParametersInQuery<br />**Hex**:<br />8004430E<br />**Nummer**:<br />-2147204338|Die Anzahl der Parameter in einer Bedingung hat die maximale Anzahl überschritten.|
> |**Name**:<br />TooManyConditionsInQuery<br />**Hex**:<br />8004430C<br />**Nummer**:<br />-2147204340|Die Anzahl der Bedingungen in der Abfrage hat den Höchstwert überschritten.|
> |**Name**:<br />TooManyEntitiesEnabledForAutoCreatedAccessTeams<br />**Hex**:<br />80048332<br />**Nummer**:<br />-2147187918|Zu viele Entitäten aktiviert für automatisch erstellte Zugriffsteams.|
> |**Name**:<br />TooManyLinkEntitiesInQuery<br />**Hex**:<br />8004430D<br />**Nummer**:<br />-2147204339|Die Anzahl der verknüpften Entitäten in der Abfrage hat den Höchstwert überschritten.|
> |**Name**:<br />TooManyMultiSelectConditionParametersInQuery<br />**Hex**:<br />80050223<br />**Nummer**:<br />-2147155421|Die Anzahl der Bedingungsparameter mit Mehrfachauswahl in der Abfrage hat den Höchstwert von {0} überschritten.|
> |**Name**:<br />TooManyPicklistValues<br />**Hex**:<br />80048492<br />**Nummer**:<br />-2147187566|Die Anzahl der eindeutigen Auswahllistenwerte hat die Begrenzung überschreiten.|
> |**Name**:<br />TooManyRecipients<br />**Hex**:<br />8004350e<br />**Nummer**:<br />-2147207922|Das Senden an mehrere Empfänger wird nicht unterstützt.|
> |**Name**:<br />TooManySelectionsForAttributeType<br />**Hex**:<br />80050222<br />**Nummer**:<br />-2147155422|Die Anzahl der Auswahlen für den MultiSelectPicklist-Attributtyp hat die Höchstgrenze überschritten: {0}.|
> |**Name**:<br />TooManyTeamTemplatesForEntityAccessTeams<br />**Hex**:<br />80048333<br />**Nummer**:<br />-2147187917|Aktuelle Zahl der Teams: {0} ist größer ist als die Teamgrenze: {1} für die Entität mit ObjectTypeCode {2}|
> |**Name**:<br />TopicModelActivateWithInvalidConfiguration<br />**Hex**:<br />80061656<br />**Nummer**:<br />-2147084714|Die Konfiguration für den Build ist ungültig. Für die Konfiguration, die für die Themenanalyse verwendet wird, sind Themenbestimmungsfelder erforderlich.|
> |**Name**:<br />TopicModelConfigurationAssociatedModelAlreadyActive<br />**Hex**:<br />80061670<br />**Nummer**:<br />-2147084688|Kann die Themenmodellkonfiguration nicht aktualisieren oder löschen, weil sie einem aktiven Themenmodell zugeordnet ist.|
> |**Name**:<br />TopicModelConfigurationUsedEmpty<br />**Hex**:<br />80061653<br />**Nummer**:<br />-2147084717|Aktivierung erfordert das Angeben der Buildkonfiguration. Geben Sie die für die Erstellung verwendete Konfiguration vor der Aktivierung an.|
> |**Name**:<br />TopicModelScheduleBuildSettingsEmpty<br />**Hex**:<br />80061651<br />**Nummer**:<br />-2147084719|Aktivierung erfordert das Festlegen des Buildzeitplans. Geben Sie die Zeitplanbuildeinstellungen vor der Aktivierung an.|
> |**Name**:<br />TopicModelTestWithoutConfiguration<br />**Hex**:<br />80061654<br />**Nummer**:<br />-2147084716|Geben Sie die für die Erstellung verwendete Konfiguration an.|
> |**Name**:<br />TraceMessageConstructionError<br />**Hex**:<br />8004F900<br />**Nummer**:<br />-2147157760|Der Tracedatensatz hat einen ungültigen Überwachungscode oder eine ungenügende Anzahl von Traceparametern.|
> |**Name**:<br />TransactionAborted<br />**Hex**:<br />80040255<br />**Nummer**:<br />-2147220907|Transaktion abgebrochen.|
> |**Name**:<br />TransactionNotCommited<br />**Hex**:<br />80040252<br />**Nummer**:<br />-2147220910|Transaktion nicht festgelegt.|
> |**Name**:<br />TransactionNotStarted<br />**Hex**:<br />80040251<br />**Nummer**:<br />-2147220911|Transaktion nicht begonnen.|
> |**Name**:<br />TransactionNotSupported<br />**Hex**:<br />8005E007<br />**Nummer**:<br />-2147098617|Der Vorgang, den Sie ausführen möchten, unterstützt keine Transaktionen.|
> |**Name**:<br />TransformationResumeNotSupported<br />**Hex**:<br />80048463<br />**Nummer**:<br />-2147187613|Das Unterbrechen/Fortsetzen des Transformationsauftrags des Imports wird nicht unterstützt.|
> |**Name**:<br />TransformMustBeCalledBeforeImport<br />**Hex**:<br />80040335<br />**Nummer**:<br />-2147220683|Import kann vor der Transformation nicht aufgerufen werden.|
> |**Name**:<br />TranslateArticle_OnlyPrimaryArticlesCanBeTranslated<br />**Hex**:<br />80061402<br />**Nummer**:<br />-2147085310|Dieser Artikel bietet eine Übersetzung des ursprünglichen Artikel. Es kann nicht erneut übersetzt werden. Wenn Sie eine andere Übersetzung möchten, beginnen Sie mit dem ursprünglichen Artikel anstatt mit diesem.|
> |**Name**:<br />TranslateArticle_TranslationCanNotBeCreatedForTheSameLanguage<br />**Hex**:<br />80061403<br />**Nummer**:<br />-2147085309|Für diese Version des Artikels gibt bereits eine Übersetzung in diese Sprache.|
> |**Name**:<br />TrendingDocumentsDataRetrievalFailure<br />**Hex**:<br />80044234<br />**Nummer**:<br />-2147204556|Wir können nicht zu Trending Documents gelangen. Versuchen Sie es später noch einmal.|
> |**Name**:<br />TrendingDocumentsIntegrationDisabledError<br />**Hex**:<br />80044233<br />**Nummer**:<br />-2147204557|Trending Documents sind für Ihr Microsoft Dynamics 365-Konto deaktiviert.|
> |**Name**:<br />TrendingDocumentsIntegrationTurnedOffError<br />**Hex**:<br />80044255<br />**Nummer**:<br />-2147204523|Trending Documents ist deaktiviert. Wenden Sie sich an Ihren Systemadministrator, um diese Funktion in den Systemeinstelllungen zu aktivieren.|
> |**Name**:<br />TrendingDocumentsOfflineModeError<br />**Hex**:<br />80044258<br />**Nummer**:<br />-2147204520|Trending Documents ist im Offlinemodus nicht verfügbar.|
> |**Name**:<br />TrendingDocumentsOnpremiseDeploymentError<br />**Hex**:<br />80044232<br />**Nummer**:<br />-2147204558|Die Dashboard-Komponente „Trending Documents“ wird nicht vom Microsoft Office-Dienst Ihres Unternehmens unterstützt.|
> |**Name**:<br />TriggerFlowFailure<br />**Hex**:<br />80050261<br />**Nummer**:<br />-2147155359|Fehler beim Versuch, diesen Flow auszuführen.|
> |**Name**:<br />TypeNotSetToDefinition<br />**Hex**:<br />80060402<br />**Nummer**:<br />-2147089406|Kategorie sollte auf BusinessProcessFlow festgelegt werden, solange die Geschäftsprozessflusskategorie erstellt wird|
> |**Name**:<br />UIDataGenerationFailed<br />**Hex**:<br />80045037<br />**Nummer**:<br />-2147200969|Fehler beim Abrufen von UIDaten aus XAML.|
> |**Name**:<br />UIDataMissingInWorkflow<br />**Hex**:<br />80048471<br />**Nummer**:<br />-2147187599|Der Workflow enthält keine UIData.|
> |**Name**:<br />UIScriptIdentifierDuplicate<br />**Hex**:<br />8004F217<br />**Nummer**:<br />-2147159529|Es ist bereits eine Variable oder ein Eingabeargument mit diesem Namen vorhanden. Wählen Sie einen anderen Namen aus, und versuchen Sie es erneut.|
> |**Name**:<br />UIScriptIdentifierInvalid<br />**Hex**:<br />8004F218<br />**Nummer**:<br />-2147159528|Die Variable oder der Eingabeargumentname sind ungültig. Der Name darf nur alphanumerische Zeichen und Unterstrich enthalten. Wählen Sie einen anderen Namen aus, und versuchen Sie es erneut.|
> |**Name**:<br />UIScriptIdentifierInvalidLength<br />**Hex**:<br />8004F219<br />**Nummer**:<br />-2147159527|Die Variable oder der Eingabeargumentname sind zu lang. Wählen Sie einen kürzeren Namen aus, und versuchen Sie es erneut.|
> |**Name**:<br />UnableToActivateQuoteNotInDraft<br />**Hex**:<br />80100003<br />**Nummer**:<br />-2146435069|Das Angebot kann nicht aktiviert werden, da es sich nicht im Entwurfsstatus befindet.|
> |**Name**:<br />UnableToLoadCustomActivity<br />**Hex**:<br />8004505A<br />**Nummer**:<br />-2147200934|Die benutzerdefinierte Aktivität kann nicht geladen werden.|
> |**Name**:<br />UnableToLoadPluginAssembly<br />**Hex**:<br />80044191<br />**Nummer**:<br />-2147204719|Die Plug-In-Assembly kann nicht geladen werden.|
> |**Name**:<br />UnableToLoadPluginType<br />**Hex**:<br />80044190<br />**Nummer**:<br />-2147204720|Der Plug-In-Typ kann nicht geladen werden.|
> |**Name**:<br />UnableToLoadTransformationAssembly<br />**Hex**:<br />80040378<br />**Nummer**:<br />-2147220616|Die Transformations-Assembly konnte nicht geladen werden.|
> |**Name**:<br />UnableToLoadTransformationType<br />**Hex**:<br />80040379<br />**Nummer**:<br />-2147220615|Transformationstyp konnte nicht geladen werden.|
> |**Name**:<br />UnableToLogOnUserFromUserNameAndPassword<br />**Hex**:<br />80044311<br />**Nummer**:<br />-2147204335|Der angegebener Benutzername und das Kennwort können nicht anmelden.|
> |**Name**:<br />UnableToSendEmail<br />**Hex**:<br />8004B015<br />**Nummer**:<br />-2147176427|Interner Fehler beim Senden der Einladung. Versuchen Sie es später erneut|
> |**Name**:<br />UnapprovedMailbox<br />**Hex**:<br />8005E220<br />**Nummer**:<br />-2147098080|Das Postfach ist in einem nicht geprüften Status. Senden/empfangen von E-Mails ist für genehmigte Postfächer zugelassen.|
> |**Name**:<br />UnauthorizedAccess<br />**Hex**:<br />80040277<br />**Nummer**:<br />-2147220873|Es wurde versucht, einen ungültigen Vorgang auszuführen.|
> |**Name**:<br />UnExpected<br />**Hex**:<br />80040216<br />**Nummer**:<br />-2147220970|Unerwarteter Fehler.|
> |**Name**:<br />UnexpectedErrorInMailMerge<br />**Hex**:<br />80040330<br />**Nummer**:<br />-2147220688|Es gibt einen unerwarteten Fehler während des Seriendrucks.|
> |**Name**:<br />UnexpectedNullReferenceError<br />**Hex**:<br />8004F044<br />**Nummer**:<br />-2147159996|Unerwarteter Null-Verweisfehler: {0}.|
> |**Name**:<br />UnexpectedRightOperandCount<br />**Hex**:<br />80060006<br />**Nummer**:<br />-2147090426|Das richtige Operandenarray im Ausdruck enthält ein unerwartetes Nein. Operand(en).|
> |**Name**:<br />UnitDoesNotExist<br />**Hex**:<br />80043b1b<br />**Nummer**:<br />-2147206373|Die Einheit ist nicht vorhanden.|
> |**Name**:<br />UnitLoopBeingCreated<br />**Hex**:<br />80043b1a<br />**Nummer**:<br />-2147206374|Durch das Verwenden dieser Basiseinheit würde eine Schleife in der Einheitshierarchie erstellt werden.|
> |**Name**:<br />UnitLoopExists<br />**Hex**:<br />80043b19<br />**Nummer**:<br />-2147206375|Schleife ist in der Einheitshierarchie vorhanden.|
> |**Name**:<br />UnitNoName<br />**Hex**:<br />80043b26<br />**Nummer**:<br />-2147206362|Der Name der Einheit kann nicht NULL sein.|
> |**Name**:<br />UnitNotInSchedule<br />**Hex**:<br />80043b16<br />**Nummer**:<br />-2147206378|Die Einheit ist im angegebenen Einheitenzeitplan nicht vorhanden.|
> |**Name**:<br />UnknownInvalidTransformationParameterGeneric<br />**Hex**:<br />80048513<br />**Nummer**:<br />-2147187437|Mindestens ein Eingabetransformations-Parameterwert ist ungültig: {0}.|
> |**Name**:<br />unManagedchildentityisnotchild<br />**Hex**:<br />800404e6<br />**Nummer**:<br />-2147220250|Die untergeordnete Entität ist keine untergeordnete Entität.|
> |**Name**:<br />unManagedcihldofconditionforoffilefilters<br />**Hex**:<br />800404a9<br />**Nummer**:<br />-2147220311|"Untergeordnetes Element von"-Bedingung sind nur bei Offlinefiltern zulässig.|
> |**Name**:<br />UnmanagedComponentParentsManagedComponent<br />**Hex**:<br />8004803B<br />**Nummer**:<br />-2147188677|{0} Abhängigkeitsdatensätze gefunden, bei denen eine nicht verwaltete Komponente ein übergeordnetes Element einer verwalteten Komponente ist. Erster Datensatz (dependentcomponentobjectid = {1}, Typ = {2}, requiredcomponentobjectid = {3}, Typ= {4}, Lösung = {5}).|
> |**Name**:<br />unManagedemptyprocessliteralcondition<br />**Hex**:<br />800404b0<br />**Nummer**:<br />-2147220304|Keine Daten für ProcessLiteralCondition angegeben.|
> |**Name**:<br />unManagedentityisnotintersect<br />**Hex**:<br />800404aa<br />**Nummer**:<br />-2147220310|Die Entität ist keine überschneidende Enität.|
> |**Name**:<br />unManagederroraddingfiltertoqueryplan<br />**Hex**:<br />800404ca<br />**Nummer**:<br />-2147220278|Ein Fehler beim Hinzufügen eines Filters zum Abfrageplan ist aufgetreten.|
> |**Name**:<br />unManagederrorprocessingfilternodes<br />**Hex**:<br />800404c4<br />**Nummer**:<br />-2147220284|Unerwarteter Fehler beim Verarbeiten der Filterknoten.|
> |**Name**:<br />unManagedfieldnotvalidatedbyplatform<br />**Hex**:<br />800404ae<br />**Nummer**:<br />-2147220306|Ein Feld wurde nicht von der Plattform nicht validiert.|
> |**Name**:<br />unManagedfilterindexoutofrange<br />**Hex**:<br />800404ab<br />**Nummer**:<br />-2147220309|Der Bereich liegt nicht im Filterindex.|
> |**Name**:<br />unManagedIdsAccessDenied<br />**Hex**:<br />80048306<br />**Nummer**:<br />-2147187962|Kein ausreichendes Recht für Zugriff auf das Microsoft Dynamics 365-Objekt oder für die Durchführung des angeforderten Vorgangs.|
> |**Name**:<br />unManagedidsaccounthaschildopportunities<br />**Hex**:<br />80040511<br />**Nummer**:<br />-2147220207|Die Firma hat untergeordnete Verkaufschancen.|
> |**Name**:<br />unManagedidsactivitydurationdoesnotmatch<br />**Hex**:<br />8004350a<br />**Nummer**:<br />-2147207926|Aktivitätsdauer entspricht nicht der Start-/Endzeit|
> |**Name**:<br />unManagedidsactivityinvalidduration<br />**Hex**:<br />80043509<br />**Nummer**:<br />-2147207927|Ungültige Aktivitätsdauer|
> |**Name**:<br />unManagedidsactivityinvalidobjecttype<br />**Hex**:<br />80043503<br />**Nummer**:<br />-2147207933|Aktivität hinsichtlich des Objekttyps ist ungültig|
> |**Name**:<br />unManagedidsactivityinvalidpartyobjecttype<br />**Hex**:<br />80043505<br />**Nummer**:<br />-2147207931|Objekttyp der Aktivitätspartei ist ungültig.|
> |**Name**:<br />unManagedidsactivityinvalidregardingobject<br />**Hex**:<br />80043507<br />**Nummer**:<br />-2147207929|Ungültige Aktivität bezüglich eines Objekts, es ist wahrscheinlich nicht vorhanden|
> |**Name**:<br />unManagedidsactivityinvalidstate<br />**Hex**:<br />80043500<br />**Nummer**:<br />-2147207936|Ungültiger Aktivitätsstatus|
> |**Name**:<br />unManagedidsactivityinvalidtimeformat<br />**Hex**:<br />80043508<br />**Nummer**:<br />-2147207928|Ungültige Aktivitätszeit, Format prüfen|
> |**Name**:<br />unManagedidsactivityinvalidtype<br />**Hex**:<br />80043501<br />**Nummer**:<br />-2147207935|Ungültiger Code für Aktivitätstyp.|
> |**Name**:<br />unManagedidsactivitynotroutable<br />**Hex**:<br />8004350b<br />**Nummer**:<br />-2147207925|Diese Art von Aktivität ist nicht routbar|
> |**Name**:<br />unManagedidsactivityobjectidortypemissing<br />**Hex**:<br />80043502<br />**Nummer**:<br />-2147207934|Fehlende Aktivität hinsichtlich Objekt-Id oder Objekttyp|
> |**Name**:<br />unManagedidsactivitypartyobjectidortypemissing<br />**Hex**:<br />80043504<br />**Nummer**:<br />-2147207932|Fehlende Objekt-Id oder fehlender Objekttyp der Aktivitätspartei|
> |**Name**:<br />unManagedidsanonymousenabled<br />**Hex**:<br />80040226<br />**Nummer**:<br />-2147220954|Der angemeldete Benutzer wurde im Active Directory nicht gefunden.|
> |**Name**:<br />unManagedidsarticletemplatecontainsarticles<br />**Hex**:<br />80043e05<br />**Nummer**:<br />-2147205627|Artikelvorlage kann nicht geändert werden, da sie von Wissensdatenbankartikeln verwendet wird.|
> |**Name**:<br />unManagedidsarticletemplateisnotactive<br />**Hex**:<br />80043e07<br />**Nummer**:<br />-2147205625|Wissensdatenbankartikelvorlage ist inaktiv.|
> |**Name**:<br />unManagedidsattachmentcannotcreatetempfile<br />**Hex**:<br />80044a05<br />**Nummer**:<br />-2147202555|Temporäre Anhangdatei kann nicht erstellt werden.|
> |**Name**:<br />unManagedidsattachmentcannotgetfilesize<br />**Hex**:<br />80044a01<br />**Nummer**:<br />-2147202559|Größe der temporären Anhangdatei kann nicht abgerufen werden.|
> |**Name**:<br />unManagedidsattachmentcannotopentempfile<br />**Hex**:<br />80044a00<br />**Nummer**:<br />-2147202560|Temporäre Anhangdatei kann nicht geöffnet werden.|
> |**Name**:<br />unManagedidsattachmentcannotreadtempfile<br />**Hex**:<br />80044a03<br />**Nummer**:<br />-2147202557|Temporäre Anhangdatei kann nicht gelesen werden.|
> |**Name**:<br />unManagedidsattachmentcannottruncatetempfile<br />**Hex**:<br />80044a07<br />**Nummer**:<br />-2147202553|Temporäre Anhangdatei kann nicht gekürzt werden.|
> |**Name**:<br />unManagedidsattachmentcannotunmaptempfile<br />**Hex**:<br />80044a06<br />**Nummer**:<br />-2147202554|Zuordnung der temporären Anhangdatei kann nicht aufgehoben werden.|
> |**Name**:<br />unManagedidsattachmentinvalidfilesize<br />**Hex**:<br />80044a02<br />**Nummer**:<br />-2147202558|Anlagengröße ist zu groß.|
> |**Name**:<br />unManagedidsattachmentisempty<br />**Hex**:<br />80044a04<br />**Nummer**:<br />-2147202556|Anlage ist leer.|
> |**Name**:<br />unManagedidsbizmgmtbusinessparentdiffmerchant<br />**Hex**:<br />80041d04<br />**Nummer**:<br />-2147214076|Das Unternehmen ist nicht der gleiche Händler wie das übergeordnete Unternehmen.|
> |**Name**:<br />unManagedidsbizmgmtcallernotinpartnerbusiness<br />**Hex**:<br />80041d14<br />**Nummer**:<br />-2147214060|Der Anrufer ist nicht vom Partnerunternehmen.|
> |**Name**:<br />unManagedidsbizmgmtcallernotinprimarybusiness<br />**Hex**:<br />80041d12<br />**Nummer**:<br />-2147214062|Der Anrufer ist nicht von einem Primärunternehmen.|
> |**Name**:<br />unManagedidsbizmgmtcannotaddlocaluser<br />**Hex**:<br />80041d32<br />**Nummer**:<br />-2147214030|Ein lokaler Benutzer kann nicht in Dynamics 365 hinzugefügt werden.|
> |**Name**:<br />unManagedidsbizmgmtcannotdeletebusiness<br />**Hex**:<br />80041d18<br />**Nummer**:<br />-2147214056|Dies ist ein Sub-Unternehmen. Verwenden Sie IBizMerchant::Delete, um dieses Subunternehmen zu löschen.|
> |**Name**:<br />unManagedidsbizmgmtcannotdeleteprovision<br />**Hex**:<br />80041d19<br />**Nummer**:<br />-2147214055|Dies ist ein bereitgestelltes Stamm-Unternehmen. Verwenden Sie IBizProvision::Delete, um dieses Root-Unternehmen zu löschen.|
> |**Name**:<br />unManagedidsbizmgmtcannotdisablebusiness<br />**Hex**:<br />80041d1a<br />**Nummer**:<br />-2147214054|Stammunternehmenseinheit kann nicht deaktiviert werden.|
> |**Name**:<br />unManagedidsbizmgmtcannotdisableprovision<br />**Hex**:<br />80041d1b<br />**Nummer**:<br />-2147214053|Dies ist ein bereitgestelltes Stamm-Unternehmen. Verwenden Sie IBizProvision::Delete, um dieses Root-Unternehmen zu deaktivieren.|
> |**Name**:<br />unManagedidsbizmgmtcannotenablebusiness<br />**Hex**:<br />80041d1c<br />**Nummer**:<br />-2147214052|Dies ist ein Sub-Unternehmen. Verwenden Sie IBizMerchant::Enable, um dieses Subunternehmen zu löschen.|
> |**Name**:<br />unManagedidsbizmgmtcannotenableprovision<br />**Hex**:<br />80041d1d<br />**Nummer**:<br />-2147214051|Dies ist ein bereitgestelltes Stamm-Unternehmen. Verwenden Sie IBizProvision::Enable, um dieses Root-Unternehmen zu aktivieren.|
> |**Name**:<br />unManagedidsbizmgmtcannotmovedefaultuser<br />**Hex**:<br />80041d05<br />**Nummer**:<br />-2147214075|unManagedidsbizmgmtcannotmovedefaultuser|
> |**Name**:<br />unManagedidsbizmgmtcannotreadaccountcontrol<br />**Hex**:<br />80041d2d<br />**Nummer**:<br />-2147214035|Berechtigungen für den angegebenen Active Directory-Benutzer unzureichend. Wenden Sie sich an den Systemadministrator.|
> |**Name**:<br />unManagedidsbizmgmtcannotremovepartnershipdefaultuser<br />**Hex**:<br />80041d17<br />**Nummer**:<br />-2147214057|Der Standardbenutzer der Partnerschaft konnte nicht entfernt werden.|
> |**Name**:<br />unManagedidsbizmgmtcantchangeorgname<br />**Hex**:<br />80041d36<br />**Nummer**:<br />-2147214026|Der Organisations-Name kann nicht geändert werden.|
> |**Name**:<br />unManagedidsbizmgmtdefaultusernotinbusiness<br />**Hex**:<br />80041d03<br />**Nummer**:<br />-2147214077|Der Standardbenutzer gehört nicht zum Unternehmen.|
> |**Name**:<br />unManagedidsbizmgmtdefaultusernotinpartnerbusiness<br />**Hex**:<br />80041d15<br />**Nummer**:<br />-2147214059|Der Standardbenutzer befindet sich nicht im Partnerunternehmen.|
> |**Name**:<br />unManagedidsbizmgmtdefaultusernotinprimarybusiness<br />**Hex**:<br />80041d13<br />**Nummer**:<br />-2147214061|Der Standardbenutzer ist nicht vom Primärunternehmen.|
> |**Name**:<br />unManagedidsbizmgmtmissbusinessname<br />**Hex**:<br />80041d00<br />**Nummer**:<br />-2147214080|Der Name der Geschäftseinheit fehlt unerwartet.|
> |**Name**:<br />unManagedidsbizmgmtmissparentbusiness<br />**Hex**:<br />80041d02<br />**Nummer**:<br />-2147214078|Das übergeordnete Unternehmen fehlt unerwartet.|
> |**Name**:<br />unManagedidsbizmgmtmisspartnerbusiness<br />**Hex**:<br />80041d0f<br />**Nummer**:<br />-2147214065|Das Partnerschafts-Partnerunternehmen fehlt unerwartet.|
> |**Name**:<br />unManagedidsbizmgmtmissprimarybusiness<br />**Hex**:<br />80041d0e<br />**Nummer**:<br />-2147214066|Das primäre Partnerschafts-Partnerunternehmen fehlt unerwartet.|
> |**Name**:<br />unManagedidsbizmgmtmissuserdomainname<br />**Hex**:<br />80041d01<br />**Nummer**:<br />-2147214079|Der Domänenname des Benutzers fehlt unerwartet.|
> |**Name**:<br />unManagedidsbizmgmtnoparentbusiness<br />**Hex**:<br />80041d29<br />**Nummer**:<br />-2147214039|Das angegebene Unternehmen verfügt nicht über ein übergeordnetes Unternehmen.|
> |**Name**:<br />unManagedidsbizmgmtpartnershipalreadyexists<br />**Hex**:<br />80041d11<br />**Nummer**:<br />-2147214063|Eine Partnerschaft zwischen angegebenen primärem Unternehmen und Partnerunternehmen ist bereits vorhanden.|
> |**Name**:<br />unManagedidsbizmgmtpartnershipnotinpendingstatus<br />**Hex**:<br />80041d16<br />**Nummer**:<br />-2147214058|Die Partnerschaft wurde akzeptiert oder abgelehnt.|
> |**Name**:<br />unManagedidsbizmgmtprimarysameaspartner<br />**Hex**:<br />80041d10<br />**Nummer**:<br />-2147214064|Das Primärunternehmen kann nicht das Partnerunternehmen sein.|
> |**Name**:<br />unManagedidsbizmgmtusercannotbeownparent<br />**Hex**:<br />80041d06<br />**Nummer**:<br />-2147214074|Der Benutzer kann nicht der eigene übergeordnete Benutzer sein.|
> |**Name**:<br />unManagedidsbizmgmtuserdoesnothaveparent<br />**Hex**:<br />80041d1e<br />**Nummer**:<br />-2147214050|Dieser Benutzer hat keinen übergeordneten Benutzer.|
> |**Name**:<br />unManagedidsbizmgmtusersettingsnotcreated<br />**Hex**:<br />80041d2b<br />**Nummer**:<br />-2147214037|Die angegebene Einstellungen des Benutzers sind noch nicht erstellt worden.|
> |**Name**:<br />unManagedidscalendarinvalidcalendar<br />**Hex**:<br />80044d00<br />**Nummer**:<br />-2147201792|Der Kalender ist ungültig.|
> |**Name**:<br />unManagedidscalendarruledoesnotexist<br />**Hex**:<br />80045100<br />**Nummer**:<br />-2147200768|Die Kalenderregel wird nicht unterstützt.|
> |**Name**:<br />unManagedidsCalloutException<br />**Hex**:<br />80045f05<br />**Nummer**:<br />-2147197179|Legendencode löst eine Ausnahme aus|
> |**Name**:<br />unManagedidscalloutinvalidconfig<br />**Hex**:<br />80045f03<br />**Nummer**:<br />-2147197181|Ungültige Legendenkonfiguration|
> |**Name**:<br />unManagedidscalloutinvalidevent<br />**Hex**:<br />80045f04<br />**Nummer**:<br />-2147197180|Ungültiges Legendenereignis|
> |**Name**:<br />unManagedidscalloutisvabort<br />**Hex**:<br />80045f01<br />**Nummer**:<br />-2147197183|Legenden-ISV-Code hat den Vorgang abgebrochen|
> |**Name**:<br />unManagedidscalloutisvexception<br />**Hex**:<br />80045f00<br />**Nummer**:<br />-2147197184|Legenden-ISV-Code löst eine Ausnahme aus|
> |**Name**:<br />unManagedidscalloutisvstop<br />**Hex**:<br />80045f02<br />**Nummer**:<br />-2147197182|Legenden-ISV-Code hat den Vorgang angehalten|
> |**Name**:<br />unManagedidscannotassigntobusiness<br />**Hex**:<br />80040221<br />**Nummer**:<br />-2147220959|Ein Objekt kann keinem Händler zugewiesen werden.|
> |**Name**:<br />unManagedidscannotdeactivatepricelevel<br />**Hex**:<br />80043b04<br />**Nummer**:<br />-2147206396|Die Preisstufe kann nicht deaktiviert werden, da sie die Standardpreisstufe einer Firma, eines Kontakts oder des Produkts ist.|
> |**Name**:<br />unManagedidscannotdefaultprivateview<br />**Hex**:<br />80040238<br />**Nummer**:<br />-2147220936|Die privaten Ansichten können nicht deaktiviert werden.|
> |**Name**:<br />unManagedidscannotgrantorrevokeaccesstobusiness<br />**Hex**:<br />8004021e<br />**Nummer**:<br />-2147220962|Zugriffsrechte können einem Händler nicht erteilen oder von ihm widerrufen werden.|
> |**Name**:<br />unManagedidscantdisable<br />**Hex**:<br />80044154<br />**Nummer**:<br />-2147204780|Der Benutzer kann nicht deaktiviert werden, da es Workflowregeln gibt, die unter diesem Kontext ausgeführt werden.|
> |**Name**:<br />unManagedidscascadeemptylinkerror<br />**Hex**:<br />80045602<br />**Nummer**:<br />-2147199486|Der Beziehungslink ist leer|
> |**Name**:<br />unManagedidscascadeinconsistencyerror<br />**Hex**:<br />80045600<br />**Nummer**:<br />-2147199488|Kaskadierzuordnungsinformationenen sind inkonsistent.|
> |**Name**:<br />unManagedidscascadeundefinedrelationerror<br />**Hex**:<br />80045601<br />**Nummer**:<br />-2147199487|Beziehungstyp wird nicht unterstützt|
> |**Name**:<br />unManagedidscascadeunexpectederror<br />**Hex**:<br />80045603<br />**Nummer**:<br />-2147199485|Unerwarteter Fehler aufgetreten im überlappenden Aktionen|
> |**Name**:<br />unManagedidscommunicationsbadsender<br />**Hex**:<br />80040b01<br />**Nummer**:<br />-2147218687|Mehr als ein Absender angegeben|
> |**Name**:<br />unManagedidscommunicationsnoparticipationmask<br />**Hex**:<br />80040b06<br />**Nummer**:<br />-2147218682|Teilnahmetyp fehlt von einer Aktivität|
> |**Name**:<br />unManagedidscommunicationsnopartyaddress<br />**Hex**:<br />80040b00<br />**Nummer**:<br />-2147218688|Objekt-Adresse nicht auf der Partei oder Partei ist als nicht--emailable gekenzeichnet.|
> |**Name**:<br />unManagedidscommunicationsnorecipients<br />**Hex**:<br />80040b05<br />**Nummer**:<br />-2147218683|Mindestens ein Systembenutzer oder eine Warteschlange in der Organisation muss ein Empfänger sein|
> |**Name**:<br />unManagedidscommunicationsnosender<br />**Hex**:<br />80040b02<br />**Nummer**:<br />-2147218686|Keine E-Mail-Adresse wurde angegeben und der aufrufende Benutzer hat keine E-Mail-Adresse festgelegt|
> |**Name**:<br />unManagedidscommunicationsnosenderaddress<br />**Hex**:<br />80040b08<br />**Nummer**:<br />-2147218680|Der angegebene Absender hat keine E-Mail-Adresse.|
> |**Name**:<br />unManagedidscommunicationstemplateinvalidtemplate<br />**Hex**:<br />80040b07<br />**Nummer**:<br />-2147218681|Der Vorlagenkörper ist ungültig.|
> |**Name**:<br />unManagedidscontacthaschildopportunities<br />**Hex**:<br />80040512<br />**Nummer**:<br />-2147220206|Der Kontakt hat untergeordnete Verkaufschancen.|
> |**Name**:<br />unManagedidscontractaccountmissing<br />**Hex**:<br />80043201<br />**Nummer**:<br />-2147208703|Firma erforderlich, um einen Vertrag zu speichern.|
> |**Name**:<br />unManagedidscontractdoesnotexist<br />**Hex**:<br />80043207<br />**Nummer**:<br />-2147208697|Die Vertragsvorlage ist nicht vorhanden.|
> |**Name**:<br />unManagedidscontractinvalidowner<br />**Hex**:<br />80043212<br />**Nummer**:<br />-2147208686|Der Besitzer des Vertrags ist ungültig.|
> |**Name**:<br />unManagedidscontractinvalidstartdateforrenewedcontract<br />**Hex**:<br />80043217<br />**Nummer**:<br />-2147208681|Das Startdatum des erneuerten Vertrags darf nicht vor dem Enddatum des ursprünglichen Vertrags liegen.|
> |**Name**:<br />unManagedidscontractinvalidtotalallotments<br />**Hex**:<br />80043214<br />**Nummer**:<br />-2147208684|Die Gesamtanzahl der Zuteilungen ist ungültig.|
> |**Name**:<br />unManagedidscontractlineitemdoesnotexist<br />**Hex**:<br />80043208<br />**Nummer**:<br />-2147208696|Die Vertragsposition ist nicht vorhanden.|
> |**Name**:<br />unManagedidscontractopencasesexist<br />**Hex**:<br />8004320a<br />**Nummer**:<br />-2147208694|Es gibt unerledigte Anfragen für diese Vertragsposition.|
> |**Name**:<br />unManagedidscontracttemplateabbreviationexists<br />**Hex**:<br />80043216<br />**Nummer**:<br />-2147208682|Der Wert für Abkürzung ist bereits vorhanden.|
> |**Name**:<br />unManagedidscontractunexpected<br />**Hex**:<br />80043200<br />**Nummer**:<br />-2147208704|Unerwarteter Fehler in den Verträgen.|
> |**Name**:<br />unManagedidscpbadpassword<br />**Hex**:<br />80042901<br />**Nummer**:<br />-2147211007|Falsches Passwort für den angegebenen Kundenportalbenutzer.|
> |**Name**:<br />unManagedidscpdecryptfailed<br />**Hex**:<br />80042903<br />**Nummer**:<br />-2147211005|Entschlüsselung des Passworts fehlgeschlagen.|
> |**Name**:<br />unManagedidscpencryptfailed<br />**Hex**:<br />80042902<br />**Nummer**:<br />-2147211006|Die Verschlüsselung des angegebenen Passworts ist fehlgeschlagen.|
> |**Name**:<br />unManagedidscpuserdoesnotexist<br />**Hex**:<br />80042900<br />**Nummer**:<br />-2147211008|Der Kundenportalbenutzer ist nicht vorhanden, oder das Kennwort falsch ist.|
> |**Name**:<br />unManagedidscustomentityalreadyinitialized<br />**Hex**:<br />80045901<br />**Nummer**:<br />-2147198719|Benutzerdefinierte Entitätsschnittstelle wurde auf diesem Thread bereits initialisiert.|
> |**Name**:<br />unManagedidscustomentityambiguousrelationship<br />**Hex**:<br />8004590d<br />**Nummer**:<br />-2147198707|Mehrere Beziehungen zwischen den angeforderten Entitäten vorhanden.|
> |**Name**:<br />unManagedidscustomentityexistingloop<br />**Hex**:<br />80045907<br />**Nummer**:<br />-2147198713|Es gibt einen vorhandene Loop in der Datenbank.|
> |**Name**:<br />unManagedidscustomentityinvalidchild<br />**Hex**:<br />80045909<br />**Nummer**:<br />-2147198711|Die untergeordnete Entität hat keine gültige Entität.|
> |**Name**:<br />unManagedidscustomentityinvalidownership<br />**Hex**:<br />80045903<br />**Nummer**:<br />-2147198717|Besitz-Typmaske der benutzerdefinierten Entität ist nicht ordnungsgemäß festgelegt.|
> |**Name**:<br />unManagedidscustomentityinvalidparent<br />**Hex**:<br />8004590a<br />**Nummer**:<br />-2147198710|Die angegebene übergeordnete Entität hat keine gültige Entität.|
> |**Name**:<br />unManagedidscustomentitynameviolation<br />**Hex**:<br />80045900<br />**Nummer**:<br />-2147198720|Die angegebene gesuchte Entität gefunden, aber es ist keine benutzerdefinierte Entität.|
> |**Name**:<br />unManagedidscustomentitynorelationship<br />**Hex**:<br />8004590c<br />**Nummer**:<br />-2147198708|Keine Beziehung zwischen den angeforderten Entitäten vorhanden.|
> |**Name**:<br />unManagedidscustomentitynotinitialized<br />**Hex**:<br />80045902<br />**Nummer**:<br />-2147198718|Schnittstelle der benutzerdefinierten Entität wurde nicht ordnungsgemäß initialisiert.|
> |**Name**:<br />unManagedidscustomentityparentchildidentical<br />**Hex**:<br />8004590b<br />**Nummer**:<br />-2147198709|Die angegebenen übergeordneten und untergeordneten Entitäten sind identisch.|
> |**Name**:<br />unManagedidscustomentitystackoverflow<br />**Hex**:<br />80045905<br />**Nummer**:<br />-2147198715|MD-Stapelüberlauf bei der benutzerdefinierten Entität.|
> |**Name**:<br />unManagedidscustomentitystackunderflow<br />**Hex**:<br />80045906<br />**Nummer**:<br />-2147198714|MD-Stapelunterlauf bei der benutzerdefinierten Entität.|
> |**Name**:<br />unManagedidscustomentitytlsfailure<br />**Hex**:<br />80045904<br />**Nummer**:<br />-2147198716|MD TLS der benutzerdefinierten Entität wurde nicht initialisiert.|
> |**Name**:<br />unManagedidscustomentitywouldcreateloop<br />**Hex**:<br />80045908<br />**Nummer**:<br />-2147198712|Diese Zuordnung kann eine Schleife in der Datenbank erzeugen.|
> |**Name**:<br />unManagedidscustomeraddresstypeinvalid<br />**Hex**:<br />80040514<br />**Nummer**:<br />-2147220204|Ungültiger Kundenadressentyp.|
> |**Name**:<br />unManagedidscustomizationtransformationnotsupported<br />**Hex**:<br />80044700<br />**Nummer**:<br />-2147203328|Transformationen wird für dieses Objekt nicht unterstützt.|
> |**Name**:<br />unManagedidsdataaccessunexpected<br />**Hex**:<br />80042300<br />**Nummer**:<br />-2147212544|Unerwarteter Datenzugriffsfehler.  DB-Verbindung wurde möglicherweise nicht erfolgreich geöffnet.|
> |**Name**:<br />unManagedidsdataoutofrange<br />**Hex**:<br />8004022c<br />**Nummer**:<br />-2147220948|Daten liegen außerhalb des Bereichs.|
> |**Name**:<br />unManagedidsevalaborted<br />**Hex**:<br />80042c03<br />**Nummer**:<br />-2147210237|Auswertung abgebrochen.|
> |**Name**:<br />unManagedidsevalallaborted<br />**Hex**:<br />80042c02<br />**Nummer**:<br />-2147210238|Auswertung abgebrochen und weitere Verarbeitung angehalten.|
> |**Name**:<br />unManagedidsevalallcompleted<br />**Hex**:<br />80042c0c<br />**Nummer**:<br />-2147210228|Auswertung abgeschlossen und weitere Verarbeitung angehalten.|
> |**Name**:<br />unManagedidsevalassignshouldhave4parameters<br />**Hex**:<br />80042c01<br />**Nummer**:<br />-2147210239|Zuweisungsaktion sollte 4 Parameter aufweisen.|
> |**Name**:<br />unManagedidsevalchangetypeerror<br />**Hex**:<br />80042c0d<br />**Nummer**:<br />-2147210227|Änderungstypfehler.|
> |**Name**:<br />unManagedidsevalcompleted<br />**Hex**:<br />80042c04<br />**Nummer**:<br />-2147210236|Auswertung abgeschlossen.|
> |**Name**:<br />unManagedidsevalcreateshouldhave2parameters<br />**Hex**:<br />80042c3c<br />**Nummer**:<br />-2147210180|Erstellungsaktion sollte 2 Parameter aufweisen.|
> |**Name**:<br />unManagedidsevalerrorabsparameter<br />**Hex**:<br />80042c2c<br />**Nummer**:<br />-2147210196|Fehler bei Auswertung eines WFPM_ABS-Parameters.|
> |**Name**:<br />unManagedidsevalerroractivityattachment<br />**Hex**:<br />80042c18<br />**Nummer**:<br />-2147210216|Fehler bei der Aktion "Aktivitätsanlage".|
> |**Name**:<br />unManagedidsevalerroraddparameter<br />**Hex**:<br />80042c0f<br />**Nummer**:<br />-2147210225|Fehler bei Auswertung eines WFPM_ADD-Parameters.|
> |**Name**:<br />unManagedidsevalerrorappendtoactivityparty<br />**Hex**:<br />80042c3f<br />**Nummer**:<br />-2147210177|unManagedidsevalerrorappendtoactivityparty|
> |**Name**:<br />unManagedidsevalerrorassign<br />**Hex**:<br />80042c22<br />**Nummer**:<br />-2147210206|Fehler bei der Aktion "Zuweisen".|
> |**Name**:<br />unManagedidsevalerrorbeginwithparameter<br />**Hex**:<br />80042c38<br />**Nummer**:<br />-2147210184|Fehler bei Auswertung eines WFPM_BEGIN_WITH-Parameters.|
> |**Name**:<br />unManagedidsevalerrorbetweenparameter<br />**Hex**:<br />80042c33<br />**Nummer**:<br />-2147210189|Fehler bei Auswertung eines WFPM_BETWEEN-Parameters.|
> |**Name**:<br />unManagedidsevalerrorcontainparameter<br />**Hex**:<br />80042c3a<br />**Nummer**:<br />-2147210182|Fehler bei Auswertung eines WFPM_CONTAIN-Parameters.|
> |**Name**:<br />unManagedidsevalerrorcreate<br />**Hex**:<br />80042c3b<br />**Nummer**:<br />-2147210181|Fehler beim Erstellen eines Updates.|
> |**Name**:<br />unManagedidsevalerrorcreateactivity<br />**Hex**:<br />80042c17<br />**Nummer**:<br />-2147210217|Fehler bei der Aktion "Aktivität erstellen".|
> |**Name**:<br />unManagedidsevalerrorcreateincident<br />**Hex**:<br />80042c1d<br />**Nummer**:<br />-2147210211|Fehler bei der Aktion "Vorfall erstellen".|
> |**Name**:<br />unManagedidsevalerrorcreatenote<br />**Hex**:<br />80042c1b<br />**Nummer**:<br />-2147210213|Fehler beim Aktion "Hinweis erstellen".|
> |**Name**:<br />unManagedidsevalerrordividedbyzero<br />**Hex**:<br />80042c16<br />**Nummer**:<br />-2147210218|Dividiert durch null.|
> |**Name**:<br />unManagedidsevalerrordivisionparameter<br />**Hex**:<br />80042c13<br />**Nummer**:<br />-2147210221|Fehler bei Auswertung eines WFPM_DIVISION-Parameters.|
> |**Name**:<br />unManagedidsevalerrordivisionparameters<br />**Hex**:<br />80042c12<br />**Nummer**:<br />-2147210222|Geschäftsbereichsparameter kann nur zwei Unterparameter haben.|
> |**Name**:<br />unManagedidsevalerroremailtemplate<br />**Hex**:<br />80042c21<br />**Nummer**:<br />-2147210207|Fehler bei der Aktion "E-Mail-Vorlage".|
> |**Name**:<br />unManagedidsevalerrorendwithparameter<br />**Hex**:<br />80042c39<br />**Nummer**:<br />-2147210183|Fehler bei Auswertung eines WFPM_END_WITH-Parameters.|
> |**Name**:<br />unManagedidsevalerroreqparameter<br />**Hex**:<br />80042c31<br />**Nummer**:<br />-2147210191|Fehler bei Auswertung eines WFPM_EQ-Parameters.|
> |**Name**:<br />unManagedidsevalerrorexec<br />**Hex**:<br />80042c27<br />**Nummer**:<br />-2147210201|Fehler bei der Aktion "Ausführen".|
> |**Name**:<br />unManagedidsevalerrorformatbooleanparameter<br />**Hex**:<br />80042c45<br />**Nummer**:<br />-2147210171|Fehler bei Auswertung des WFPM_FORMAT_BOOLEAN-Parameters.|
> |**Name**:<br />unManagedidsevalerrorformatdatetimeparameter<br />**Hex**:<br />80042c44<br />**Nummer**:<br />-2147210172|Fehler bei Auswertung des WFPM_FORMAT_DATETIME-Parameters.|
> |**Name**:<br />unManagedidsevalerrorformatdecimalparameter<br />**Hex**:<br />80042c4a<br />**Nummer**:<br />-2147210166|Fehler bei Auswertung des WFPM_FORMAT_DECIMAL-Parameters.|
> |**Name**:<br />unManagedidsevalerrorformatintegerparameter<br />**Hex**:<br />80042c49<br />**Nummer**:<br />-2147210167|Fehler bei Auswertung des WFPM_FORMAT_INTEGER-Parameters.|
> |**Name**:<br />unManagedidsevalerrorformatlookupparameter<br />**Hex**:<br />80042c4c<br />**Nummer**:<br />-2147210164|Fehler bei Auswertung des WFPM_FORMAT_LOOKUP-Parameters.|
> |**Name**:<br />unManagedidsevalerrorformatpicklistparameter<br />**Hex**:<br />80042c46<br />**Nummer**:<br />-2147210170|Fehler bei Auswertung des WFPM_FORMAT_PICKLIST-Parameters.|
> |**Name**:<br />unManagedidsevalerrorformattimezonecodeparameter<br />**Hex**:<br />80042c4b<br />**Nummer**:<br />-2147210165|unManagedidsevalerrorformattimezonecodeparameter|
> |**Name**:<br />unManagedidsevalerrorgeqparameter<br />**Hex**:<br />80042c2e<br />**Nummer**:<br />-2147210194|Fehler bei Auswertung eines WFPM_GEQ-Parameters.|
> |**Name**:<br />unManagedidsevalerrorgtparameter<br />**Hex**:<br />80042c2d<br />**Nummer**:<br />-2147210195|Fehler bei Auswertung eines WFPM_GT-Parameters.|
> |**Name**:<br />unManagedidsevalerrorhalt<br />**Hex**:<br />80042c28<br />**Nummer**:<br />-2147210200|Fehler bei der Aktion "Anhalten".|
> |**Name**:<br />unManagedidsevalerrorhandleactivity<br />**Hex**:<br />80042c19<br />**Nummer**:<br />-2147210215|Fehler bei der Aktion "Aktivität behandeln".|
> |**Name**:<br />unManagedidsevalerrorhandleincident<br />**Hex**:<br />80042c1e<br />**Nummer**:<br />-2147210210|Fehler bei der Aktion "Vorfall behandeln".|
> |**Name**:<br />unManagedidsevalerrorincidentqueue<br />**Hex**:<br />80042c29<br />**Nummer**:<br />-2147210199|Fehler bei der Auswertung von INCIDENT_QUEUE.|
> |**Name**:<br />unManagedidsevalerrorinlistparameter<br />**Hex**:<br />80042c42<br />**Nummer**:<br />-2147210174|unManagedidsevalerrorinlistparameter|
> |**Name**:<br />unManagedidsevalerrorinparameter<br />**Hex**:<br />80042c34<br />**Nummer**:<br />-2147210188|Fehler bei Auswertung eines WFPM_IN-Parameters.|
> |**Name**:<br />unManagedidsevalerrorinvalidparameter<br />**Hex**:<br />80042c2b<br />**Nummer**:<br />-2147210197|Ungültiger Parameter.|
> |**Name**:<br />unManagedidsevalerrorinvalidrecipient<br />**Hex**:<br />80042c35<br />**Nummer**:<br />-2147210187|Ungültiger E-Mail-Empfänger.|
> |**Name**:<br />unManagedidsevalerrorisnulllistparameter<br />**Hex**:<br />80042c43<br />**Nummer**:<br />-2147210173|unManagedidsevalerrorisnulllistparameter|
> |**Name**:<br />unManagedidsevalerrorleqparameter<br />**Hex**:<br />80042c30<br />**Nummer**:<br />-2147210192|Fehler bei Auswertung eines WFPM_LEQ-Parameters.|
> |**Name**:<br />unManagedidsevalerrorltparameter<br />**Hex**:<br />80042c2f<br />**Nummer**:<br />-2147210193|Fehler bei Auswertung eines WFPM_LT-Parameters.|
> |**Name**:<br />unManagedidsevalerrormodulusparameter<br />**Hex**:<br />80042c15<br />**Nummer**:<br />-2147210219|Fehler bei Auswertung eines WFPM_MODULUR-Parameters.|
> |**Name**:<br />unManagedidsevalerrormodulusparameters<br />**Hex**:<br />80042c14<br />**Nummer**:<br />-2147210220|Modulo-Parameter kann nur zwei Unterparameter haben.|
> |**Name**:<br />unManagedidsevalerrormultiplicationparameter<br />**Hex**:<br />80042c11<br />**Nummer**:<br />-2147210223|Fehler bei Auswertung eines WFPM_MULTIPLICATION-Parameters.|
> |**Name**:<br />unManagedidsevalerrorneqparameter<br />**Hex**:<br />80042c32<br />**Nummer**:<br />-2147210190|Fehler bei Auswertung eines WFPM_NEQ-Parameters.|
> |**Name**:<br />unManagedidsevalerrornoteattachment<br />**Hex**:<br />80042c1c<br />**Nummer**:<br />-2147210212|Fehler bei der Aktion "Hinweisanlage".|
> |**Name**:<br />unManagedidsevalerrorobjecttype<br />**Hex**:<br />80042c48<br />**Nummer**:<br />-2147210168|Fehler bei Auswertung des WFPM_GetObjectType-Parameters.|
> |**Name**:<br />unManagedidsevalerrorposturl<br />**Hex**:<br />80042c26<br />**Nummer**:<br />-2147210202|Fehler bei der Aktion "posturl".|
> |**Name**:<br />unManagedidsevalerrorqueueidparameter<br />**Hex**:<br />80042c47<br />**Nummer**:<br />-2147210169|unManagedidsevalerrorqueueidparameter|
> |**Name**:<br />unManagedidsevalerrorremovefromactivityparty<br />**Hex**:<br />80042c40<br />**Nummer**:<br />-2147210176|unManagedidsevalerrorremovefromactivityparty|
> |**Name**:<br />unManagedidsevalerrorroute<br />**Hex**:<br />80042c24<br />**Nummer**:<br />-2147210204|Fehler bei der Aktion "Weiterleiten".|
> |**Name**:<br />unManagedidsevalerrorsendemail<br />**Hex**:<br />80042c20<br />**Nummer**:<br />-2147210208|Fehler bei der Aktion "E-Mail senden".|
> |**Name**:<br />unManagedidsevalerrorsetactivityparty<br />**Hex**:<br />80042c41<br />**Nummer**:<br />-2147210175|unManagedidsevalerrorsetactivityparty|
> |**Name**:<br />unManagedidsevalerrorsetstate<br />**Hex**:<br />80042c25<br />**Nummer**:<br />-2147210203|Fehler bei der Aktion "Status festlegen".|
> |**Name**:<br />unManagedidsevalerrorstrlenparameter<br />**Hex**:<br />80042c37<br />**Nummer**:<br />-2147210185|Fehler bei Auswertung eines WFPM_STRLEN-Parameters.|
> |**Name**:<br />unManagedidsevalerrorsubstrparameter<br />**Hex**:<br />80042c36<br />**Nummer**:<br />-2147210186|Fehler bei Auswertung eines WFPM_SUBSTR-Parameters.|
> |**Name**:<br />unManagedidsevalerrorsubtractionparameter<br />**Hex**:<br />80042c10<br />**Nummer**:<br />-2147210224|Fehler bei Auswertung eines WFPM_SUBTRACTION-Parameters.|
> |**Name**:<br />unManagedidsevalerrorunhandleactivity<br />**Hex**:<br />80042c1a<br />**Nummer**:<br />-2147210214|Fehler bei der Aktion "Aktivitätsbehandlung aufheben".|
> |**Name**:<br />unManagedidsevalerrorunhandleincident<br />**Hex**:<br />80042c1f<br />**Nummer**:<br />-2147210209|Fehler bei der Aktion "Vorfallsbehandlung aufheben".|
> |**Name**:<br />unManagedidsevalerrorupdate<br />**Hex**:<br />80042c23<br />**Nummer**:<br />-2147210205|Fehler bei der Aktion "Aktualisieren".|
> |**Name**:<br />unManagedidsevalgenericerror<br />**Hex**:<br />80042c2a<br />**Nummer**:<br />-2147210198|Auswertungsfehler.|
> |**Name**:<br />unManagedidsevalmetabaseattributenotfound<br />**Hex**:<br />80042c08<br />**Nummer**:<br />-2147210232|Das angegebene Metadatenattribut ist nicht vorhanden.|
> |**Name**:<br />unManagedidsevalmetabaseattributenotmatchquery<br />**Hex**:<br />80042c0b<br />**Nummer**:<br />-2147210229|Das angegebene refattributeid hat keine Abfrage für ein WFPM_SELECT-Parameter.|
> |**Name**:<br />unManagedidsevalmetabaseentitycompoundkeys<br />**Hex**:<br />80042c07<br />**Nummer**:<br />-2147210233|Das angegebene Metabasisobjekt hat Verbundschlüssel. Wir unterstützen Verbund-Schlüsselentitäten nicht mehr.|
> |**Name**:<br />unManagedidsevalmetabaseentitynotmatchquery<br />**Hex**:<br />80042c0a<br />**Nummer**:<br />-2147210230|Das angegebene refentityid hat keine Abfrage für ein WFPM_SELECT-Parameter.|
> |**Name**:<br />unManagedidsevalmissselectquery<br />**Hex**:<br />80042c0e<br />**Nummer**:<br />-2147210226|Abfrageunterparameter fehlt in einem ausgewählten Parameter.|
> |**Name**:<br />unManagedidsevalobjectnotfound<br />**Hex**:<br />80042c05<br />**Nummer**:<br />-2147210235|Das angeforderte Objekt ist nicht vorhanden.|
> |**Name**:<br />unManagedidsevalpropertyisnull<br />**Hex**:<br />80042c09<br />**Nummer**:<br />-2147210231|Die erforderlichen Eigenschaft des Objekts wurde nicht festgelegt.|
> |**Name**:<br />unManagedidsevalpropertynotfound<br />**Hex**:<br />80042c06<br />**Nummer**:<br />-2147210234|Die erforderlichen Eigenschaft des Objekts wurde nicht gefunden.|
> |**Name**:<br />unManagedidsevaltimererrorcalculatescheduletime<br />**Hex**:<br />80042c3e<br />**Nummer**:<br />-2147210178|Die Zeitplanzeit für die Timer-Aktion konnte nicht berechnet werden.|
> |**Name**:<br />unManagedidsevaltimerinvalidparameternumber<br />**Hex**:<br />80042c3d<br />**Nummer**:<br />-2147210179|Ungültige Parameter für Timeraktion.|
> |**Name**:<br />unManagedidsevalupdateshouldhave3parameters<br />**Hex**:<br />80042c00<br />**Nummer**:<br />-2147210240|Aktualisierungsaktion sollte 3 Parameter aufweisen.|
> |**Name**:<br />unManagedidsfailureinittoken<br />**Hex**:<br />8004020f<br />**Nummer**:<br />-2147220977|Fehler beim Abrufen des Benutzertokens.|
> |**Name**:<br />unManagedidsfetchbetweentext<br />**Hex**:<br />80044153<br />**Nummer**:<br />-2147204781|zwischen, nicht-zwischen, in und Nicht-in-Operatoren werden nicht in Attribute vom Typ Text oder ntext zugelassen.|
> |**Name**:<br />unManagedidsfulltextoperationfailed<br />**Hex**:<br />80043e06<br />**Nummer**:<br />-2147205626|Vollständiger Textvorgang fehlgeschlagen.|
> |**Name**:<br />unManagedidsincidentassociatedactivitycorrupted<br />**Hex**:<br />80044405<br />**Nummer**:<br />-2147204091|Die dieser Anfrage zugeordnete Aktivität ist beschädigt.|
> |**Name**:<br />unManagedidsincidentcannotclose<br />**Hex**:<br />8004440a<br />**Nummer**:<br />-2147204086|Der Vorfall kann nicht gescchlossen werden, da offene Aktivitäten für diesen Vorfall vorhanden sind.|
> |**Name**:<br />unManagedidsincidentcontractdetaildoesnotmatchcontract<br />**Hex**:<br />80044402<br />**Nummer**:<br />-2147204094|Die Vertragsposition ist im angegebenen Vertrag nicht vorhanden.|
> |**Name**:<br />unManagedidsincidentinvalidactivitytypecode<br />**Hex**:<br />80044406<br />**Nummer**:<br />-2147204090|Das activitytypecode ist ungültig.|
> |**Name**:<br />unManagedidsincidentinvalidstate<br />**Hex**:<br />80044404<br />**Nummer**:<br />-2147204092|Vorfallstatus ist ungültig.|
> |**Name**:<br />unManagedidsincidentmissingactivityobjecttype<br />**Hex**:<br />80044408<br />**Nummer**:<br />-2147204088|Fehlender Objekttypcode.|
> |**Name**:<br />unManagedidsincidentnullactivitytypecode<br />**Hex**:<br />80044407<br />**Nummer**:<br />-2147204089|Das activitytypecode kann nicht UNGÜLTIG sein.|
> |**Name**:<br />unManagedidsincidentparentaccountandparentcontactnotpresent<br />**Hex**:<br />80044410<br />**Nummer**:<br />-2147204080|Sie sollten einen übergeordneten Kontakt oder eine übergeordnete Firma angeben.|
> |**Name**:<br />unManagedidsincidentparentaccountandparentcontactpresent<br />**Hex**:<br />8004440f<br />**Nummer**:<br />-2147204081|Sie können entweder einen übergeordneten Kontakt der Kontakte oder die Firma eingeben, aber nicht beide.|
> |**Name**:<br />unManagedidsinvalidassociation<br />**Hex**:<br />80040211<br />**Nummer**:<br />-2147220975|Ungültige Zuordnung.|
> |**Name**:<br />unManagedidsinvalidbusinessid<br />**Hex**:<br />80040209<br />**Nummer**:<br />-2147220983|Ungültige Unternehmens-ID.|
> |**Name**:<br />unManagedidsinvaliditemid<br />**Hex**:<br />8004020b<br />**Nummer**:<br />-2147220981|Ungültige Element-ID.|
> |**Name**:<br />unManagedidsinvalidorgid<br />**Hex**:<br />8004020a<br />**Nummer**:<br />-2147220982|Ungültige Organisations-ID.|
> |**Name**:<br />unManagedidsinvalidowninguser<br />**Hex**:<br />80040212<br />**Nummer**:<br />-2147220974|Element hat keinen zuständigen Benutzer.|
> |**Name**:<br />unManagedidsinvalidteamid<br />**Hex**:<br />80040208<br />**Nummer**:<br />-2147220984|Ungültige Team-ID.|
> |**Name**:<br />unManagedidsinvaliduserid<br />**Hex**:<br />80040207<br />**Nummer**:<br />-2147220985|Der Benutzer ID ist fehlend oder ungültig.|
> |**Name**:<br />unManagedidsinvaliduseridorbusinessidorusersbusinessinvalid<br />**Hex**:<br />8004021d<br />**Nummer**:<br />-2147220963|Eine der folgenden Komponenten ist aufgetreten: Ungültige Benutzer-ID, ungültige Unternehmens-ID oder der Benutzer gehört nicht zum Unternehmen.|
> |**Name**:<br />unManagedidsinvalidvisibility<br />**Hex**:<br />8004020e<br />**Nummer**:<br />-2147220978|Ungültige Sichtbarkeit.|
> |**Name**:<br />unManagedidsinvalidvisibilitymodificationaccess<br />**Hex**:<br />80040213<br />**Nummer**:<br />-2147220973|Der Benutzer erhält keinen Zugriff, um die Sichtbarkeit dieses Elements zu ändern.|
> |**Name**:<br />unManagedidsinvoicecloseapideprecated<br />**Hex**:<br />80043b25<br />**Nummer**:<br />-2147206363|Die API Rechnungs-Abschluss ist veraltet. Es wurde durch die Zahlungs- und Stornierungs-APIs ersetzt.|
> |**Name**:<br />unManagedidsjournalinginvalideventtype<br />**Hex**:<br />80040803<br />**Nummer**:<br />-2147219453|Ungültiger Ereignistyp.|
> |**Name**:<br />unManagedidsjournalingmissingaccountid<br />**Hex**:<br />80040806<br />**Nummer**:<br />-2147219450|Firmen-ID fehlt.|
> |**Name**:<br />unManagedidsjournalingmissingcontactid<br />**Hex**:<br />80040808<br />**Nummer**:<br />-2147219448|Kontakt-ID fehlt.|
> |**Name**:<br />unManagedidsjournalingmissingeventdirection<br />**Hex**:<br />80040802<br />**Nummer**:<br />-2147219454|Ereignisrichtungscode fehlt.|
> |**Name**:<br />unManagedidsjournalingmissingeventtype<br />**Hex**:<br />80040804<br />**Nummer**:<br />-2147219452|Ereignistyp fehlt.|
> |**Name**:<br />unManagedidsjournalingmissingincidentid<br />**Hex**:<br />80040809<br />**Nummer**:<br />-2147219447|Vorfall-ID fehlt.|
> |**Name**:<br />unManagedidsjournalingmissingleadid<br />**Hex**:<br />80040805<br />**Nummer**:<br />-2147219451|Lead-ID fehlt.|
> |**Name**:<br />unManagedidsjournalingmissingopportunityid<br />**Hex**:<br />80040807<br />**Nummer**:<br />-2147219449|Verkaufschancen-ID fehlt.|
> |**Name**:<br />unManagedidsjournalingunsupportedobjecttype<br />**Hex**:<br />80040801<br />**Nummer**:<br />-2147219455|Nicht unterstützter Typ von Objekten in Betrieb.|
> |**Name**:<br />unManagedidsleaddoesnotexist<br />**Hex**:<br />80040501<br />**Nummer**:<br />-2147220223|Lead ist nicht vorhanden.|
> |**Name**:<br />unManagedidsleadnoparent<br />**Hex**:<br />8004050b<br />**Nummer**:<br />-2147220213|Der angeforderte Lead hat kein übergeordnetes Ziel.|
> |**Name**:<br />unManagedidsleadnotassigned<br />**Hex**:<br />8004050c<br />**Nummer**:<br />-2147220212|Der Lead wurde nicht zugewiesen.|
> |**Name**:<br />unManagedidsleadnotassignedtocaller<br />**Hex**:<br />80040513<br />**Nummer**:<br />-2147220205|Der Lead wird dem Anrufer nicht für Abnahme zugewiesen.|
> |**Name**:<br />unManagedidsleadoneaccount<br />**Hex**:<br />80040510<br />**Nummer**:<br />-2147220208|Ein Lead kann nicht mehreren Firmen zugeordnet werden.|
> |**Name**:<br />unManagedidsleadusercannotreject<br />**Hex**:<br />8004050d<br />**Nummer**:<br />-2147220211|Der Benutzer besitzt nicht über das erforderliche Recht, Leads abzulehnen, sodass ihm Lead für zum Akzeptieren nicht zugewiesen werden können.|
> |**Name**:<br />unManagedidsmergedifferentbizorgerror<br />**Hex**:<br />80045303<br />**Nummer**:<br />-2147200253|Die Zusammenführung kann nicht bei Entitäten aus einer anderen Geschäftsentität ausgeführt werden.|
> |**Name**:<br />unManagedidsmetadatanoentity<br />**Hex**:<br />80040e00<br />**Nummer**:<br />-2147217920|Die angegebene Entität ist nicht vorhanden|
> |**Name**:<br />unManagedidsmetadatanorelationship<br />**Hex**:<br />80040e02<br />**Nummer**:<br />-2147217918|Beziehung ist nicht vorhanden.|
> |**Name**:<br />unManagedidsnorelationship<br />**Hex**:<br />80040236<br />**Nummer**:<br />-2147220938|Keine Beziehung zwischen den angegebenen Objekten vorhanden.|
> |**Name**:<br />unManagedidsnotesalreadyattached<br />**Hex**:<br />80041701<br />**Nummer**:<br />-2147215615|Die angegebene Notiz wird bereits als ein Objekt angefügt.|
> |**Name**:<br />unManagedidsnotesloopbeingcreated<br />**Hex**:<br />80041703<br />**Nummer**:<br />-2147215613|Durch das Erstellen dieser übergeordneten Zuordnung würde eine Schleife in der Anmerkungshierarchie erstellt werden.|
> |**Name**:<br />unManagedidsnotesloopexists<br />**Hex**:<br />80041702<br />**Nummer**:<br />-2147215614|Eine Schleife ist in der Anmerkungshierarchie vorhanden.|
> |**Name**:<br />unManagedidsnotesnoattachment<br />**Hex**:<br />80041704<br />**Nummer**:<br />-2147215612|Die angegebene Notiz hat keine Anlagen.|
> |**Name**:<br />unManagedidsnotesnotedoesnotexist<br />**Hex**:<br />80041700<br />**Nummer**:<br />-2147215616|Die angeforderte Notiz ist nicht vorhanden.|
> |**Name**:<br />unManagedidsopportunitydoesnotexist<br />**Hex**:<br />80040500<br />**Nummer**:<br />-2147220224|Verkaufschance ist nicht vorhanden.|
> |**Name**:<br />unManagedidsopportunityinvalidparent<br />**Hex**:<br />80040504<br />**Nummer**:<br />-2147220220|Das übergeordnete Objekt einer Verkaufschance muss eine Firma oder ein Kontakt sein.|
> |**Name**:<br />unManagedidsopportunitymissingparent<br />**Hex**:<br />80040505<br />**Nummer**:<br />-2147220219|Das übergeordnete Objekt einer Verkaufschance fehlt.|
> |**Name**:<br />unManagedidsopportunityoneaccount<br />**Hex**:<br />8004050e<br />**Nummer**:<br />-2147220210|Eine Verkaufschance kann nicht mehreren Firmen zugeordnet werden.|
> |**Name**:<br />unManagedidsopportunityorphan<br />**Hex**:<br />8004050f<br />**Nummer**:<br />-2147220209|Durch Entfernen der Zuordnung werden Verkaufschance verwaist.|
> |**Name**:<br />unManagedidsoutofmemory<br />**Hex**:<br />80040222<br />**Nummer**:<br />-2147220958|Nicht genügend Arbeitsspeicher|
> |**Name**:<br />unManagedidsownernotenabled<br />**Hex**:<br />8004022b<br />**Nummer**:<br />-2147220949|Der angegebene Besitzer ist deaktiviert worden.|
> |**Name**:<br />unManagedidspresentuseridandteamid<br />**Hex**:<br />8004021c<br />**Nummer**:<br />-2147220964|Die Benutzer-ID und die Team-ID sind vorhanden. Nur eine sollte vorhanden sein.|
> |**Name**:<br />unManagedidspropbagattributealreadyset<br />**Hex**:<br />8004203f<br />**Nummer**:<br />-2147213249|Eines der übergebenen Attribute ist bereits festgelegt worden|
> |**Name**:<br />unManagedidspropbagattributenotnullable<br />**Hex**:<br />8004203e<br />**Nummer**:<br />-2147213250|Eines der übergebenen Attribute kann nicht NULL sein|
> |**Name**:<br />unManagedidspropbagcolloutofrange<br />**Hex**:<br />8004201e<br />**Nummer**:<br />-2147213282|Der Behälterindex in der Sammlung war außerhalb des Bereichs.|
> |**Name**:<br />unManagedidspropbagnointerface<br />**Hex**:<br />80042001<br />**Nummer**:<br />-2147213311|Der Eigenschaftschnittstellenbehälter wurde nicht gefunden.|
> |**Name**:<br />unManagedidspropbagnullproperty<br />**Hex**:<br />80042002<br />**Nummer**:<br />-2147213310|Die definierte Eigenschaft im Eigenschaftsbehälter war Null.|
> |**Name**:<br />unManagedidspropbagpropertynotfound<br />**Hex**:<br />80042000<br />**Nummer**:<br />-2147213312|Die definierte Eigenschaft wurde nicht im Eigenschaftsbehälter gefunden.|
> |**Name**:<br />unManagedidsqueuemissingbusinessunitid<br />**Hex**:<br />80043e03<br />**Nummer**:<br />-2147205629|Fehlende businessunitid.|
> |**Name**:<br />unManagedidsqueueorganizationidnotmatch<br />**Hex**:<br />80043e04<br />**Nummer**:<br />-2147205628|Organisations-ID des Anrufers entspricht nicht der Organisations-ID der Unternehmenseinheit.|
> |**Name**:<br />unManagedidsrcsyncfilternoaccess<br />**Hex**:<br />8004410f<br />**Nummer**:<br />-2147204849|Kann nicht in den Offlinemodus wechseln: Zugriffsrechte für erforderlich Entität fehlen.|
> |**Name**:<br />unManagedidsrcsyncinvalidfiltererror<br />**Hex**:<br />8004410d<br />**Nummer**:<br />-2147204851|Ungültiger Filter angegeben.|
> |**Name**:<br />unManagedidsrcsyncinvalidsubscription<br />**Hex**:<br />80044109<br />**Nummer**:<br />-2147204855|Das angegebene Abonnement ist nicht vorhanden.|
> |**Name**:<br />unManagedidsrcsyncinvalidsynctime<br />**Hex**:<br />80044100<br />**Nummer**:<br />-2147204864|Die angegebene Synchronisierungszeit ist ungültig.  Einphaszeiten dürfen nicht vor jenen der vorherigen Synchronisierung liegen. Bitte Initialisieren Sie Ihr Abonnement neu.|
> |**Name**:<br />unManagedidsrcsyncmethodnone<br />**Hex**:<br />80044114<br />**Nummer**:<br />-2147204844|Auf diesem Computer können keine Synchronisierungsaufgaben ausgeführt werden, da die Synchronisierungsmethode auf "Keine" festgelegt ist.|
> |**Name**:<br />unManagedidsrcsyncmsxmlfailed<br />**Hex**:<br />80044101<br />**Nummer**:<br />-2147204863|unManagedidsrcsyncmsxmlfailed|
> |**Name**:<br />unManagedidsrcsyncnoclient<br />**Hex**:<br />80044113<br />**Nummer**:<br />-2147204845|Der Client ist nicht vorhanden.|
> |**Name**:<br />unManagedidsrcsyncnoprimary<br />**Hex**:<br />80044112<br />**Nummer**:<br />-2147204846|Kein primärer Client vorhanden.|
> |**Name**:<br />unManagedidsrcsyncnotprimary<br />**Hex**:<br />80044111<br />**Nummer**:<br />-2147204847|Kann nicht synchronisiert werden: nicht der primäre OutlookSync-Client.|
> |**Name**:<br />unManagedidsrcsyncsoapconnfailed<br />**Hex**:<br />80044103<br />**Nummer**:<br />-2147204861|unManagedidsrcsyncsoapconnfailed|
> |**Name**:<br />unManagedidsrcsyncsoapfaulterror<br />**Hex**:<br />80044106<br />**Nummer**:<br />-2147204858|unManagedidsrcsyncsoapfaulterror|
> |**Name**:<br />unManagedidsrcsyncsoapgenfailed<br />**Hex**:<br />80044102<br />**Nummer**:<br />-2147204862|unManagedidsrcsyncsoapgenfailed|
> |**Name**:<br />unManagedidsrcsyncsoapparseerror<br />**Hex**:<br />80044108<br />**Nummer**:<br />-2147204856|unManagedidsrcsyncsoapparseerror|
> |**Name**:<br />unManagedidsrcsyncsoapreaderror<br />**Hex**:<br />80044107<br />**Nummer**:<br />-2147204857|unManagedidsrcsyncsoapreaderror|
> |**Name**:<br />unManagedidsrcsyncsoapsendfailed<br />**Hex**:<br />80044104<br />**Nummer**:<br />-2147204860|unManagedidsrcsyncsoapsendfailed|
> |**Name**:<br />unManagedidsrcsyncsoapservererror<br />**Hex**:<br />80044105<br />**Nummer**:<br />-2147204859|unManagedidsrcsyncsoapservererror|
> |**Name**:<br />unManagedidsrcsyncsqlgenericerror<br />**Hex**:<br />80044110<br />**Nummer**:<br />-2147204848|unManagedidsrcsyncsqlgenericerror|
> |**Name**:<br />unManagedidsrcsyncsqlpausederror<br />**Hex**:<br />8004410c<br />**Nummer**:<br />-2147204852|unManagedidsrcsyncsqlpausederror|
> |**Name**:<br />unManagedidsrcsyncsqlstoppederror<br />**Hex**:<br />8004410b<br />**Nummer**:<br />-2147204853|unManagedidsrcsyncsqlstoppederror|
> |**Name**:<br />unManagedidsrcsyncsubscriptionowner<br />**Hex**:<br />8004410a<br />**Nummer**:<br />-2147204854|Die Anrufer-ID stimmt nicht mit der Abonnementbesitzer-ID überein. Nur Abonnementbesitzer dürfen Abonnementvorgänge ausführen.|
> |**Name**:<br />unManagedidsrolesdeletenonparentrole<br />**Hex**:<br />8004140c<br />**Nummer**:<br />-2147216372|Eine Rolle, die aus dem übergeordneten Unternehmen geerbt wird, kann nicht gelöscht werden.|
> |**Name**:<br />unManagedidsrolesinvalidroledata<br />**Hex**:<br />80041400<br />**Nummer**:<br />-2147216384|Rollendaten sind ungültig.|
> |**Name**:<br />unManagedidsrolesinvalidroleid<br />**Hex**:<br />80041401<br />**Nummer**:<br />-2147216383|Ungültige Rollen-ID.|
> |**Name**:<br />unManagedidsrolesinvalidrolename<br />**Hex**:<br />8004140a<br />**Nummer**:<br />-2147216374|Der Rollenname ist ungültig.|
> |**Name**:<br />unManagedidsrolesinvalidtemplateid<br />**Hex**:<br />80041404<br />**Nummer**:<br />-2147216380|Ungültige Rollenvorlagen-ID.|
> |**Name**:<br />unManagedidsrolesmissbusinessid<br />**Hex**:<br />80041406<br />**Nummer**:<br />-2147216378|Die Rollengeschäftseinheits-ID fehlt unerwartet.|
> |**Name**:<br />unManagedidsrolesmissprivid<br />**Hex**:<br />80041408<br />**Nummer**:<br />-2147216376|Die Recht-ID fehlt unerwartet.|
> |**Name**:<br />unManagedidsrolesmissroleid<br />**Hex**:<br />80041405<br />**Nummer**:<br />-2147216379|Die Rollen-ID fehlt unerwartet.|
> |**Name**:<br />unManagedidsrolesmissrolename<br />**Hex**:<br />80041407<br />**Nummer**:<br />-2147216377|De Rollenname fehlt unerwartet.|
> |**Name**:<br />unManagedidsrolesroledoesnotexist<br />**Hex**:<br />80041402<br />**Nummer**:<br />-2147216382|Das angegebene Rolle ist nicht vorhanden.|
> |**Name**:<br />unManagedidsrspropbagdbinfoalreadyset<br />**Hex**:<br />8004203d<br />**Nummer**:<br />-2147213251|Die DB-Informationen für den Datensatzeigenschaftenbehälter wurde bereits festgelegt.|
> |**Name**:<br />unManagedidsrspropbagdbinfonotset<br />**Hex**:<br />8004203c<br />**Nummer**:<br />-2147213252|Die DB-Informationen für den Datensatzeigenschaftenbehälter wurde noch nicht festgelegt.|
> |**Name**:<br />unManagedidssalespeopleduplicatecalendarfound<br />**Hex**:<br />80043802<br />**Nummer**:<br />-2147207166|Doppelte Geschäftskalender für diesen Vertriebsmitarbeiter/dieses Jahr gefunden|
> |**Name**:<br />unManagedidssalespeopleinvalidfiscalcalendartype<br />**Hex**:<br />80043808<br />**Nummer**:<br />-2147207160|Ungültiger Geschäftskalendertyp|
> |**Name**:<br />unManagedidssalespeopleinvalidfiscalperiodindex<br />**Hex**:<br />80043807<br />**Nummer**:<br />-2147207161|Ungültiger Buchhaltungsperiodenindex|
> |**Name**:<br />unManagedidssalespeopleinvalidterritoryobjecttype<br />**Hex**:<br />80043804<br />**Nummer**:<br />-2147207164|Gebiete können nicht über diese Art des Objekts abgerufen werden|
> |**Name**:<br />unManagedidssqlerror<br />**Hex**:<br />80044150<br />**Nummer**:<br />-2147204784|Allgemeiner SQL-Fehler.|
> |**Name**:<br />unManagedidssqltimeouterror<br />**Hex**:<br />80044151<br />**Nummer**:<br />-2147204783|SQL Server-Timeout abgelaufen.|
> |**Name**:<br />unManagedidsstatedoesnotexist<br />**Hex**:<br />80043af9<br />**Nummer**:<br />-2147206407|Die angegebene Status ist für dieses Produkt nicht gültig.|
> |**Name**:<br />unManagedidsusernotenabled<br />**Hex**:<br />80040225<br />**Nummer**:<br />-2147220955|Der angegebene Benutzer ist entweder deaktiviert oder kein Mitglied einer Unternehmenseinheit.|
> |**Name**:<br />unManagedidsviewisnotsharable<br />**Hex**:<br />80040232<br />**Nummer**:<br />-2147220942|Diese Ansicht kann nicht freigegeben werden.|
> |**Name**:<br />unManagedidsxmlinvalidcollectionname<br />**Hex**:<br />80041a03<br />**Nummer**:<br />-2147214845|Der angegebene Auflistungsname ist falsch|
> |**Name**:<br />unManagedidsxmlinvalidcreate<br />**Hex**:<br />80041a01<br />**Nummer**:<br />-2147214847|Ein für die Erstellung ungültiges Feld wurde angegeben.|
> |**Name**:<br />unManagedidsxmlinvalidentityattributes<br />**Hex**:<br />80041a06<br />**Nummer**:<br />-2147214842|Ungültige Attribute|
> |**Name**:<br />unManagedidsxmlinvalidentityname<br />**Hex**:<br />80041a00<br />**Nummer**:<br />-2147214848|Der angegebene Entitätsname ist falsch|
> |**Name**:<br />unManagedidsxmlinvalidfield<br />**Hex**:<br />80041a07<br />**Nummer**:<br />-2147214841|Ein ungültiger Wert wurde für ein Feld übergeben|
> |**Name**:<br />unManagedidsxmlinvalidread<br />**Hex**:<br />80041a08<br />**Nummer**:<br />-2147214840|Ein für das Lesen ungültiges Feld wurde angegeben|
> |**Name**:<br />unManagedidsxmlinvalidupdate<br />**Hex**:<br />80041a02<br />**Nummer**:<br />-2147214846|Ein für die Aktualisierung ungültiges Feld wurde angegeben|
> |**Name**:<br />unManagedidsxmlparseerror<br />**Hex**:<br />80041a04<br />**Nummer**:<br />-2147214844|Ein Parsingfehler ist im XML aufgetreten|
> |**Name**:<br />unManagedidsxmlunexpected<br />**Hex**:<br />80041a05<br />**Nummer**:<br />-2147214843|Unerwarteter Fehler|
> |**Name**:<br />unManagedinvalddbtimefield<br />**Hex**:<br />800404d9<br />**Nummer**:<br />-2147220263|Die Plattform kann keine dbtime-Felder behandeln.|
> |**Name**:<br />unManagedinvalidargumentsforcondition<br />**Hex**:<br />800404b7<br />**Nummer**:<br />-2147220297|Eine ungültige Anzahl der Argumente wurde einer Bedingung bereitgestellt.|
> |**Name**:<br />unManagedinvalidbinaryfield<br />**Hex**:<br />800404dc<br />**Nummer**:<br />-2147220260|Die Plattform kann keine Binärfelder behandeln.|
> |**Name**:<br />unManagedinvalidbusinessunitid<br />**Hex**:<br />800404a7<br />**Nummer**:<br />-2147220313|Die Unternehmens-ID ist fehlend oder ungültig.|
> |**Name**:<br />unManagedinvalidcharacterdataforaggregate<br />**Hex**:<br />800404de<br />**Nummer**:<br />-2147220258|Zeichendaten sind ungültig, wenn sie ein Aggregat löschen.|
> |**Name**:<br />unManagedinvalidcountvalue<br />**Hex**:<br />800404c1<br />**Nummer**:<br />-2147220287|Der Zählwert ist fehlend oder ungültig.|
> |**Name**:<br />unManagedinvaliddbdatefield<br />**Hex**:<br />800404da<br />**Nummer**:<br />-2147220262|Die Plattform kann keine dbdate-Felder behandeln.|
> |**Name**:<br />unManagedinvaliddynamicparameteraccessor<br />**Hex**:<br />800404d5<br />**Nummer**:<br />-2147220267|SetParam ist bei der Verarbeitung von DynamicParameterAccessor fehlgeschlagen.|
> |**Name**:<br />unManagedinvalidequalityoperand<br />**Hex**:<br />800404ac<br />**Nummer**:<br />-2147220308|Nur QB_LITERAL wird für Gleichheitsoperanden unterstützt.|
> |**Name**:<br />unManagedinvalidescapedxml<br />**Hex**:<br />800404a1<br />**Nummer**:<br />-2147220319|XML-Größe mit Markierungszeichen nicht erwartungsgemäß.|
> |**Name**:<br />unManagedinvalidfieldtype<br />**Hex**:<br />800404d8<br />**Nummer**:<br />-2147220264|Die Plattform kann den Feldtyp nicht bearbeiten.|
> |**Name**:<br />unManagedinvalidlinkobjects<br />**Hex**:<br />800404ba<br />**Nummer**:<br />-2147220294|Ungültige Linkentität, Link zum Attribut oder Link vom Attribut.|
> |**Name**:<br />unManagedinvalidoperator<br />**Hex**:<br />800404c7<br />**Nummer**:<br />-2147220281|Der bereitgestellte Operator ist nicht gültig.|
> |**Name**:<br />unManagedinvalidorganizationid<br />**Hex**:<br />800404be<br />**Nummer**:<br />-2147220290|Die Unternehmens-ID ist fehlend oder ungültig.|
> |**Name**:<br />unManagedinvalidowningbusinessunit<br />**Hex**:<br />800404a8<br />**Nummer**:<br />-2147220312|Die owningbusinessunit ist fehlend oder ungültig.|
> |**Name**:<br />unManagedinvalidowningbusinessunitorbusinessunitid<br />**Hex**:<br />800404bc<br />**Nummer**:<br />-2147220292|Die owningbusinessunit oder businessunitidist fehlend oder ungültig.|
> |**Name**:<br />unManagedinvalidowninguser<br />**Hex**:<br />800404bd<br />**Nummer**:<br />-2147220291|Der owninguser ist fehlend oder ungültig.|
> |**Name**:<br />unManagedinvalidpagevalue<br />**Hex**:<br />800404c2<br />**Nummer**:<br />-2147220286|Der Seitenwert ist fehlend oder ungültig.|
> |**Name**:<br />unManagedinvalidparametertypeforparameterizedquery<br />**Hex**:<br />800404d6<br />**Nummer**:<br />-2147220266|Eine parametrisierte Abfrage wird nicht auf dem angegebenen Parametertyp unterstützt.|
> |**Name**:<br />unManagedinvalidprincipal<br />**Hex**:<br />8004049e<br />**Nummer**:<br />-2147220322|Die Haupt-ID ist fehlend oder ungültig.|
> |**Name**:<br />unManagedinvalidprivilegeedepth<br />**Hex**:<br />800404bb<br />**Nummer**:<br />-2147220293|Ungültige Rechtstiefe für Benutzer.|
> |**Name**:<br />unManagedinvalidprivilegeid<br />**Hex**:<br />800404ce<br />**Nummer**:<br />-2147220274|Die Recht-ID ist fehlend oder ungültig.|
> |**Name**:<br />unManagedinvalidprivilegeusergroup<br />**Hex**:<br />800404cd<br />**Nummer**:<br />-2147220275|Die Recht-Benutzergruppe ist fehlend oder ungültig.|
> |**Name**:<br />unManagedinvalidprocesschildofcondition<br />**Hex**:<br />800404b4<br />**Nummer**:<br />-2147220300|ProcessChildOfCondition wurde mit Nicht-Elementvon Condition bezeichnet.|
> |**Name**:<br />unManagedinvalidprocessliternalcondition<br />**Hex**:<br />800404b1<br />**Nummer**:<br />-2147220303|ProcessLiteralCondition ist nur mit Rollupabfragen gültig.|
> |**Name**:<br />unManagedinvalidsecurityprincipal<br />**Hex**:<br />800404d2<br />**Nummer**:<br />-2147220270|Der Sicherheitsprinizpal ist fehlend oder ungültig.|
> |**Name**:<br />unManagedinvalidstreamfield<br />**Hex**:<br />800404d7<br />**Nummer**:<br />-2147220265|Die Plattform kann keine Stream-Felder behandeln.|
> |**Name**:<br />unManagedinvalidtlsmananger<br />**Hex**:<br />800404a2<br />**Nummer**:<br />-2147220318|Fehler beim Abrufen des TLS-Managers.|
> |**Name**:<br />unManagedinvalidtrxcountforcommit<br />**Hex**:<br />800404e2<br />**Nummer**:<br />-2147220254|Die Transaktionsanzahl wurde erwartet, um ein Testkonto 1 festzulegen.|
> |**Name**:<br />unManagedinvalidtrxcountforrollback<br />**Hex**:<br />800404e1<br />**Nummer**:<br />-2147220255|Die Transaktionsanzahl wurde mit 1 erwartet, um einen Rollback zu machen.|
> |**Name**:<br />unManagedinvalidvaluettagoutsideconditiontag<br />**Hex**:<br />800404bf<br />**Nummer**:<br />-2147220289|Ein Tag mit ungültigem Wert außerhalb von dessen Bedingungstag gefunden.|
> |**Name**:<br />unManagedinvalidversionvalue<br />**Hex**:<br />800404c0<br />**Nummer**:<br />-2147220288|Der Versionswert ist fehlend oder ungültig.|
> |**Name**:<br />unManagedinvaludidispatchfield<br />**Hex**:<br />800404db<br />**Nummer**:<br />-2147220261|Die Plattform kann keine idispatch-Felder behandeln.|
> |**Name**:<br />unManagedmissingaddressentity<br />**Hex**:<br />800404cb<br />**Nummer**:<br />-2147220277|Die Adressentität wurde nicht gefunden.|
> |**Name**:<br />unManagedmissingattributefortag<br />**Hex**:<br />800404c5<br />**Nummer**:<br />-2147220283|Ein erwartetes Attribut wurde für das angegebene Tag nicht gefunden.|
> |**Name**:<br />unManagedmissingdataaccess<br />**Hex**:<br />800404df<br />**Nummer**:<br />-2147220257|Die Daten können nicht von ExecutionContext abgerufen werden.|
> |**Name**:<br />unManagedmissingfilterattribute<br />**Hex**:<br />800404ad<br />**Nummer**:<br />-2147220307|Fehlendes Filterattribut.|
> |**Name**:<br />unManagedmissinglinkentity<br />**Hex**:<br />800404b2<br />**Nummer**:<br />-2147220302|Unerwarteter Fehler der Suche der Linkentität.|
> |**Name**:<br />unManagedMissingObjectType<br />**Hex**:<br />80042003<br />**Nummer**:<br />-2147213309|Objekttyp muss für eines der Attribute angegeben werden.|
> |**Name**:<br />unManagedmissingparentattributeonentity<br />**Hex**:<br />800404b5<br />**Nummer**:<br />-2147220299|Das übergeordnete Attribut wurde nicht für die erwartete Entität gefunden.|
> |**Name**:<br />unManagedmissingparententity<br />**Hex**:<br />800404e5<br />**Nummer**:<br />-2147220251|Die übergeordnete Entität konnte nicht gefunden werden.|
> |**Name**:<br />unManagedmissingpreviousownertype<br />**Hex**:<br />800404d0<br />**Nummer**:<br />-2147220272|Typ des bisherigen Besitzers konnte nicht ermittelt werden.|
> |**Name**:<br />unManagedmissingreferencesfromrelationship<br />**Hex**:<br />800404c9<br />**Nummer**:<br />-2147220279|Die, um eine Beziehung im ReferencesFrom-Sammlung eine Entität zugreifen.|
> |**Name**:<br />unManagedmissingreferencingattribute<br />**Hex**:<br />800404c8<br />**Nummer**:<br />-2147220280|Das ReferencingAttribute ist fehlend oder ungültig.|
> |**Name**:<br />unManagedmorethanonesortattribute<br />**Hex**:<br />800404a6<br />**Nummer**:<br />-2147220314|Mehrere Sortierattribute wurden definiert.|
> |**Name**:<br />unManagedObjectTypeUnexpected<br />**Hex**:<br />80042004<br />**Nummer**:<br />-2147213308|Objekttyp wurde für eines der Attribute angegeben, das dies jedoch nicht zulässt.|
> |**Name**:<br />unManagedparentattributenotfound<br />**Hex**:<br />800404a4<br />**Nummer**:<br />-2147220316|Das übergeordnete Attribut wurde nicht für das untergeordnete Attribut gefunden.|
> |**Name**:<br />unManagedpartylistattributenotsupported<br />**Hex**:<br />800404b8<br />**Nummer**:<br />-2147220296|Attribute vom Typ "Partylist" werden nicht unterstützt.|
> |**Name**:<br />unManagedpendingtrxexists<br />**Hex**:<br />800404e3<br />**Nummer**:<br />-2147220253|Eine ausstehende Transaktion ist bereits vorhanden.|
> |**Name**:<br />unManagedproxycreationfailed<br />**Hex**:<br />8004049f<br />**Nummer**:<br />-2147220321|Eine Instanz des verwalteten Proxys kann nicht erstellt werden.|
> |**Name**:<br />unManagedtrxinterophandlerset<br />**Hex**:<br />800404dd<br />**Nummer**:<br />-2147220259|Der TrxInteropHandler wurde bereits festgelegt.|
> |**Name**:<br />unManagedunablegetexecutioncontext<br />**Hex**:<br />800404e4<br />**Nummer**:<br />-2147220252|Fehler beim Abrufen des Ausführungskontexts (TLS).|
> |**Name**:<br />unManagedunablegetsessiontoken<br />**Hex**:<br />800404d3<br />**Nummer**:<br />-2147220269|Sitzungstoken kann nicht abgerufen werden.|
> |**Name**:<br />unManagedunablegetsessiontokennotrx<br />**Hex**:<br />800404d4<br />**Nummer**:<br />-2147220268|Sitzungstoken kann nicht abgerufen werden, da keine pendente Transaktlion vorhanden ist.|
> |**Name**:<br />unManagedunableswitchusercontext<br />**Hex**:<br />800404e0<br />**Nummer**:<br />-2147220256|Kann nicht auf einem anderen Benutzerkontext festlegen.|
> |**Name**:<br />unManagedunabletoaccessqueryplan<br />**Hex**:<br />800404a5<br />**Nummer**:<br />-2147220315|Auf Abfrageplan kann nicht zugegriffen werden.|
> |**Name**:<br />unManagedunabletoaccessqueryplanfilter<br />**Hex**:<br />800404c6<br />**Nummer**:<br />-2147220282|Auf Filter im Abfrageplan kann nicht zugegriffen werden.|
> |**Name**:<br />unManagedunabletolocateconditionfilter<br />**Hex**:<br />800404c3<br />**Nummer**:<br />-2147220285|Unerwarteter Fehler, der den Filter für die Bedingung lokalisiert.|
> |**Name**:<br />unManagedunabletoretrieveprivileges<br />**Hex**:<br />800404a0<br />**Nummer**:<br />-2147220320|Fehler beim Abrufen der Rechte.|
> |**Name**:<br />unManagedunexpectedpropertytype<br />**Hex**:<br />800404cc<br />**Nummer**:<br />-2147220276|Unerwarteter Typ für die Eigenschaft.|
> |**Name**:<br />unManagedunexpectedrimarykey<br />**Hex**:<br />800404b3<br />**Nummer**:<br />-2147220301|Primärschlüsselattribut wurde nicht erwartet.|
> |**Name**:<br />unManagedunknownaggregateoperation<br />**Hex**:<br />800404b6<br />**Nummer**:<br />-2147220298|Ein unbekannter Aggregatsvorgang wurde angegeben.|
> |**Name**:<br />unManagedunusablevariantdata<br />**Hex**:<br />800404af<br />**Nummer**:<br />-2147220305|Die angegebene Variante enthält Daten in einem unbrauchbaren Format.|
> |**Name**:<br />UnmappedTransformationOutputDataFound<br />**Hex**:<br />80040381<br />**Nummer**:<br />-2147220607|Mindestens eine Ausgabe, die durch die Transformation zurückgegeben wird, wird nicht den Zielfeldern zugeordnet.|
> |**Name**:<br />UnpopulatedPrimaryKey<br />**Hex**:<br />8004023d<br />**Nummer**:<br />-2147220931|Primärschlüssel muss für Anrufe zur Plattform auf Rich Clients im Offlinemodus aufgefüllt werden.|
> |**Name**:<br />UnrelatedConnectionRoles<br />**Hex**:<br />80048216<br />**Nummer**:<br />-2147188202|Die Verbindungsrollen können nicht verknüpft werden.|
> |**Name**:<br />UnrestrictedIFrameInUserDashboard<br />**Hex**:<br />8004E30C<br />**Nummer**:<br />-2147163380|Bei einem Benutzerdashboard-Formular-XML kann die Sicherheit nicht = false lauten.|
> |**Name**:<br />UnspecifiedActivityXmlForCampaignActivityPropagate<br />**Hex**:<br />80040318<br />**Nummer**:<br />-2147220712|Es muss eine Aktivitäts-XML für die Ausführung/Verteilung von CampaignActivity angegeben werden|
> |**Name**:<br />UnsupportedActionType<br />**Hex**:<br />80060390<br />**Nummer**:<br />-2147089520|Fehlender Steuerelementschritt.|
> |**Name**:<br />UnsupportedArgumentsMarkedRequired<br />**Hex**:<br />80060394<br />**Nummer**:<br />-2147089516|Nicht unterstützte Argumente dürfen nicht als erforderlich gekennzeichnet werden.|
> |**Name**:<br />UnsupportedAttributeForEditor<br />**Hex**:<br />80060010<br />**Nummer**:<br />-2147090416|Die Regel enthält ein Attribut, das nicht unterstützt wird.|
> |**Name**:<br />UnsupportedAttributeInInProfileItemEntityFilters<br />**Hex**:<br />80071123<br />**Nummer**:<br />-2147020509|Das Attribut {0} wird in der Filterabfrageoption nicht unterstützt.|
> |**Name**:<br />UnsupportedAttributeOrOperatorMobileOfflineFilters<br />**Hex**:<br />80071115<br />**Nummer**:<br />-2147020523|Attribut oder Operator "{0}" wird für Mobile Offline Org-Filter nicht unterstützt.|
> |**Name**:<br />UnsupportedAttributeType<br />**Hex**:<br />8005E00D<br />**Nummer**:<br />-2147098611|Attributstyp "{0}" wird nicht unterstützt. Entfernen Sie Attribut {1} von der Abfrage vom und versuchen Sie es erneut.|
> |**Name**:<br />UnsupportedComponentOperation<br />**Hex**:<br />8004F010<br />**Nummer**:<br />-2147160048|{0} wird als nicht unterstützter Vorgang erkannt.|
> |**Name**:<br />UnsupportedCudOperationForDynamicProperties<br />**Hex**:<br />80061019<br />**Nummer**:<br />-2147086311|Sie können keine Eigenschaft für einen Bausatz erstellen.|
> |**Name**:<br />UnsupportedDashboardInEditor<br />**Hex**:<br />8004E30E<br />**Nummer**:<br />-2147163378|Das Dashboard konnte nicht geöffnet werden. |
> |**Name**:<br />UnsupportedEmailServer<br />**Hex**:<br />8005E242<br />**Nummer**:<br />-2147098046|Der E-Mail-Server wird nicht unterstützt.|
> |**Name**:<br />UnsupportedImportComponent<br />**Hex**:<br />80061302<br />**Nummer**:<br />-2147085566|Leider ist ein Fehler beim Importieren aufgetreten, weil die Komponente {0} nicht für Import und Export unterstützt wird.|
> |**Name**:<br />UnsupportedListMemberType<br />**Hex**:<br />80040301<br />**Nummer**:<br />-2147220735|Nicht unterstützter Listenmitgliedstyp.|
> |**Name**:<br />UnsupportedOperatorForAttributeInProfileItemEntityFilters<br />**Hex**:<br />80071121<br />**Nummer**:<br />-2147020511|Der Operator {0} wird mit dem Attribut {1} in der Filterabfrageoption nicht unterstützt.|
> |**Name**:<br />UnsupportedParameter<br />**Hex**:<br />80040320<br />**Nummer**:<br />-2147220704|Ein angegebener Parameter wird vom Massenvorgang nicht unterstützt|
> |**Name**:<br />UnsupportedProcessCode<br />**Hex**:<br />80040385<br />**Nummer**:<br />-2147220603|Der Prozesscode wird für diese Entität nicht unterstützt.|
> |**Name**:<br />UnsupportedSdkMessageForBundles<br />**Hex**:<br />80061025<br />**Nummer**:<br />-2147086299|Diese Nachricht wird für Produkte vom Typ "Paket" nicht unterstützt.|
> |**Name**:<br />UnsupportedStepForBusinessRuleEditor<br />**Hex**:<br />80060009<br />**Nummer**:<br />-2147090423|Regel enthält einen Schritt, der nicht vom Notepad unterstützt wird.|
> |**Name**:<br />UnsupportedZipFileForImport<br />**Hex**:<br />80048495<br />**Nummer**:<br />-2147187563|Die ZIP- oder CAB-Datei konnte nicht hochgeladen werden, da sie entweder beschädigt ist oder keine gültigen importierbaren Dateien enthält.|
> |**Name**:<br />UnzipProcessCountLimitReached<br />**Hex**:<br />80048494<br />**Nummer**:<br />-2147187564|Kann keinen neuen Vorgang zum Entzippen starten.|
> |**Name**:<br />UnzipTimeout<br />**Hex**:<br />80048496<br />**Nummer**:<br />-2147187562|Timeout geschah beim Entpacken der die ZIP-Datei, die zum Import hochgeladen werden.|
> |**Name**:<br />UpdateAttributeMap<br />**Hex**:<br />80046204<br />**Nummer**:<br />-2147196412|InvalidAttributeMap-Fehler aufgetreten|
> |**Name**:<br />UpdateEntityMap<br />**Hex**:<br />80046201<br />**Nummer**:<br />-2147196415|UpdateEntityMap Fehler ist aufgetreten|
> |**Name**:<br />UpdateNonCustomReportFromTemplate<br />**Hex**:<br />80040490<br />**Nummer**:<br />-2147220336|Kann einen Bericht aus einer Vorlage nicht aktualisieren, wenn der Bericht nicht anhand einer Vorlage erstellt wurde|
> |**Name**:<br />UpdatePublishedWorkflowDefinition<br />**Hex**:<br />80045002<br />**Nummer**:<br />-2147201022|Kann eine veröffentlichte Workflowdefinition nicht aktualisieren.|
> |**Name**:<br />UpdatePublishedWorkflowDefinitionWorkflowDependency<br />**Hex**:<br />80045008<br />**Nummer**:<br />-2147201016|Eine Workflowabhängigkeit für eine veröffentlichte Workflowdefinition kann nicht aktualisiert werden.|
> |**Name**:<br />UpdatePublishedWorkflowTemplate<br />**Hex**:<br />8004501B<br />**Nummer**:<br />-2147200997|Kann eine veröffentlichte Workflowvorlage nicht aktualisieren.|
> |**Name**:<br />UpdateRecurrenceRuleFailed<br />**Hex**:<br />8004E114<br />**Nummer**:<br />-2147163884|Die Serienregel konnte nicht aktualisiert werden. Eine entsprechende Wiederholungsregel wurde nicht gefunden.|
> |**Name**:<br />UpdateRIOrganizationDataAccessNotAllowed<br />**Hex**:<br />80044273<br />**Nummer**:<br />-2147204493|Diese Funktionskonfiguration kann nur von einem Systemadministrator aktualisiert werden.|
> |**Name**:<br />UpdateWorkflowActivation<br />**Hex**:<br />80045003<br />**Nummer**:<br />-2147201021|Eine Workflowaktivierung kann nicht aktualisiert werden.|
> |**Name**:<br />UpdateWorkflowActivationWorkflowDependency<br />**Hex**:<br />80045007<br />**Nummer**:<br />-2147201017|Eine Workflowabhängigkeit, die einer Workflowaktivierung zugeordnet ist, kann nicht aktualisiert werden.|
> |**Name**:<br />UserAlreadyExists<br />**Hex**:<br />80041d2c<br />**Nummer**:<br />-2147214036|Der angegebene Active Directory-Benutzer ist bereits als Dynamics 365 Benutzer vorhanden.|
> |**Name**:<br />UserCancelledMailMerge<br />**Hex**:<br />8004032f<br />**Nummer**:<br />-2147220689|Der Seriendruck wurde vom Benutzer abgebrochen.|
> |**Name**:<br />UserCannotEnableWithoutLicense<br />**Hex**:<br />8004D24C<br />**Nummer**:<br />-2147167668|Ein nicht lizenzierter Benutzer kann nicht aktiviert werden|
> |**Name**:<br />UserDataNotFound<br />**Hex**:<br />8004D211<br />**Nummer**:<br />-2147167727|Die Benutzerdaten wurden nicht gefunden.|
> |**Name**:<br />UserDoesNotHaveAccessToTheTenant<br />**Hex**:<br />80044507<br />**Nummer**:<br />-2147203833|Der Benutzer hat keine Zugriffsberechtigung zum Installieren des Mandanten.|
> |**Name**:<br />UserDoesNotHaveAdminOnlyModePermissions<br />**Hex**:<br />8004A113<br />**Nummer**:<br />-2147180269|Der Benutzer erhält keinen erforderlichen Berechtigungen hinzufügen (oder anfügen) Rolle Mitgliedschaft der Organisation zugreifen, wenn sie im Modus für Administratoren nur ist.|
> |**Name**:<br />UserDoesNotHavePrivilegesToRunTheTool<br />**Hex**:<br />800608F8<br />**Nummer**:<br />-2147088136|Sie müssen ein Systemadministrator sein, um diese Anforderung auszuführen.|
> |**Name**:<br />UserDoesNotHaveSendAsAllowed<br />**Hex**:<br />8004480d<br />**Nummer**:<br />-2147203059|Der Benutzer hat kein Sende-Recht|
> |**Name**:<br />UserDoesNotHaveSendAsForQueue<br />**Hex**:<br />8004480f<br />**Nummer**:<br />-2147203057|Sie verfügen nicht über ausreichende Rechte, E-Mail als ausgewählte Warteschlange zu senden. Ihren Systemadministrator bei Fragen kontaktieren.|
> |**Name**:<br />UserIdOrQueueNotSet<br />**Hex**:<br />800404e8<br />**Nummer**:<br />-2147220248|Primärer Benutzer-ID- oder Zielwarteschlangen-Typcode nicht festgelegt|
> |**Name**:<br />UserInviteDisabled<br />**Hex**:<br />8004D216<br />**Nummer**:<br />-2147167722|Einladung kann nicht übermittelt werden, da Benutzereinladungen deaktiviert sind.|
> |**Name**:<br />UserInWrongBusiness<br />**Hex**:<br />80041409<br />**Nummer**:<br />-2147216375|Zum Benutzer mit ID = {0} gehört eine andere Unternehmenseineit = {1} als die Rolle mit roleId = {2} und rolebusinessUnit = {3}.|
> |**Name**:<br />UserIsNotSystemAdminInOrganization<br />**Hex**:<br />8004B069<br />**Nummer**:<br />-2147176343|Der aktuelle Benutzer ist kein Systemadministrator in der Organisation des Kunden|
> |**Name**:<br />UserLoopBeingCreated<br />**Hex**:<br />80041d25<br />**Nummer**:<br />-2147214043|Der ausgewählte Benutzer kann nicht als Manager für diesen Benutzer festgelegt werden, da der ausgewählte Benutzer entweder bereits Manager ist oder sich in der unmittelbaren Verwaltungshierarchie des Benutzers befindet.   Entweder wählen Sie einen anderen Benutzer als Manager aus, oder Sie aktualisieren den Datensatz nicht.|
> |**Name**:<br />UserLoopExists<br />**Hex**:<br />80041d24<br />**Nummer**:<br />-2147214044|Ein Manager für diesen Benutzer kann nicht festgelegt werden, da eine vorhandene Beziehung in der Verwaltungshierarchie eine zirkuläre Beziehung verursacht.  Dies wird in der Regel über eine manuelle Bearbeiten der Microsoft Dynamics 365-Datenbank verursacht. Um dieses Problem zu beheben, muss die Hierarchie in der Datenbank geändert werden um die zirkuläre Beziehung zu entfernen.|
> |**Name**:<br />UserNameRequiredForImpersonation<br />**Hex**:<br />8005E24D<br />**Nummer**:<br />-2147098035|Geben Sie einen Benutzernamen ein und speichern sie erneut|
> |**Name**:<br />UserNeverLoggedIntoYammer<br />**Hex**:<br />8005F111<br />**Nummer**:<br />-2147094255|Um anderen Benutzern zu folgen, müssen Sie bei Yammer angemeldet sein. Melden Sie sich in Ihrem Yammer-Konto an und versuchen Sie es erneut.|
> |**Name**:<br />UserNotAssignedLicense<br />**Hex**:<br />8004D24B<br />**Nummer**:<br />-2147167669|Dem Benutzer keine Lizenz zugewiesen worden.|
> |**Name**:<br />UserNotAssignedRoles<br />**Hex**:<br />80042f09<br />**Nummer**:<br />-2147209463|Dem Benutzer ist keine Rollen zugewiesen worden.|
> |**Name**:<br />UserNotInParentHierarchy<br />**Hex**:<br />80041d07<br />**Nummer**:<br />-2147214073|Der Benutzer ist nicht in der übergeordneten Unternehmenshierarchie des Benutzers.|
> |**Name**:<br />UserNotMemberOfOrg<br />**Hex**:<br />80072560<br />**Nummer**:<br />-2147015328|Der Benutzer ist kein Mitglied der Organisation.|
> |**Name**:<br />UserSettingsInvalidAdvancedFindStartupMode<br />**Hex**:<br />80041d34<br />**Nummer**:<br />-2147214028|Ungültiger Startmodus für erweiterte Suche.|
> |**Name**:<br />UserSettingsInvalidSearchExperienceValue<br />**Hex**:<br />80041d53<br />**Nummer**:<br />-2147213997|Ungültiger Sucherfahrungswert.|
> |**Name**:<br />UserSettingsOverMaxPagingLimit<br />**Hex**:<br />80044305<br />**Nummer**:<br />-2147204347|Auslagerungsbeschränkung über maximal konfiguriertem Wert.|
> |**Name**:<br />UserTimeConvertException<br />**Hex**:<br />80040241<br />**Nummer**:<br />-2147220927|Fehler bei der Konvertierung der Benutzerzeitzoneninformationen.|
> |**Name**:<br />UserTimeZoneException<br />**Hex**:<br />80040240<br />**Nummer**:<br />-2147220928|Fehler beim Abrufen der Benutzerzeitzoneninformationen.|
> |**Name**:<br />UserViewsOrVisualizationsFound<br />**Hex**:<br />8004E302<br />**Nummer**:<br />-2147163390|Ein Systemdashboard kann keine Benutzeransichten und Visualisierungen enthalten.|
> |**Name**:<br />ValidateNotSupported<br />**Hex**:<br />8004E10A<br />**Nummer**:<br />-2147163894|Validierte Mthode ist nicht bür wiederkehrende Serienterminmaster unterstützt.|
> |**Name**:<br />ValidationContextIsNull<br />**Hex**:<br />80060442<br />**Nummer**:<br />-2147089342|Fehler beim Erstellen oder Aktualisieren des Geschäftsprozesses: Überprüfungskontext darf nicht Null sein.|
> |**Name**:<br />ValidationFailedForDynamicProperty<br />**Hex**:<br />80061021<br />**Nummer**:<br />-2147086303|Fehler beim Speichern der {0}-Eigenschaft.|
> |**Name**:<br />ValidDateTimeBehaviorExportAsWarning<br />**Hex**:<br />800608A5<br />**Nummer**:<br />-2147088219|Das Feld {0} enthält das Datum und die Uhrzeit in der Ortszeit des Benutzers, da die Verhalten "Nur Datum" und "Zeitzonenunabhängig" nicht mit früheren Versionen von Dynamics 365 kompatibel sind.|
> |**Name**:<br />ValidDateTimeBehaviorWarning<br />**Hex**:<br />800608A4<br />**Nummer**:<br />-2147088220|Die Verhaltensweisen dieses Felds hat geändert. Prüfen Sie alle Abhängigkeiten dieses Felds wie Geschäftsregeln, Workflows und berechnete oder Rollupfelder, um sicherzustellen, dass keine Probleme auftreten. Attribut: {0}|
> |**Name**:<br />ValidOnlyForDynamicsOnline<br />**Hex**:<br />80072302<br />**Nummer**:<br />-2147015934|Diese API gilt nur für Dynamics 365 Online.|
> |**Name**:<br />ValueMissingInOptionOrderArray<br />**Hex**:<br />80044325<br />**Nummer**:<br />-2147204315|Dem Optionsarray fehlt ein Wert.|
> |**Name**:<br />ValueParsingError<br />**Hex**:<br />8004B037<br />**Nummer**:<br />-2147176393|Fehleranalyseparameter {0} vom Typ {1} mit Wert {2}|
> |**Name**:<br />VersionedRowNotFoundInTempDB<br />**Hex**:<br />80048542<br />**Nummer**:<br />-2147187390|Erforderliche Versionszeile wurde nicht in TempDB gefunden; das TempDB hat wahrscheinlich keine Leerzeichen; versuchen Sie es zu einem späteren Zeitpunkt noch einmal.|
> |**Name**:<br />VersionMismatch<br />**Hex**:<br />8004B020<br />**Nummer**:<br />-2147176416|Nicht unterstütze Version - Dies ist {0} Version {1}, aber Version {2} wurde angefordert.|
> |**Name**:<br />VeryLargeFileInZipImport<br />**Hex**:<br />80048491<br />**Nummer**:<br />-2147187567|Eine der Dateien in der zu importierenden ZIP- oder CAB-Datei ist zu groß.|
> |**Name**:<br />ViewConditionTypeNotSupportedOffline<br />**Hex**:<br />80071130<br />**Nummer**:<br />-2147020496|Die Bedingung {0} wird nicht unterstützt.|
> |**Name**:<br />ViewForDuplicateDetectionNotDefined<br />**Hex**:<br />80048838<br />**Nummer**:<br />-2147186632|Erforderliche Ansicht zum Anzeigen der Duplikaterkennung einer Entität nicht definiert.|
> |**Name**:<br />ViewNotAvailableForMobileOffline<br />**Hex**:<br />8005F21b<br />**Nummer**:<br />-2147093989|Aktuelle Ansicht ist im Offlinemodus nicht verfügbar. Versuchen Sie es erneut, oder wenden Sie sich an den Administrator.|
> |**Name**:<br />ViewNotAvailableOnMobile<br />**Hex**:<br />80071126<br />**Nummer**:<br />-2147020506|Diese Ansicht ist im Mobilmodus nicht verfügbar.|
> |**Name**:<br />ViewNotSupportedInCalendarModeOffline<br />**Hex**:<br />80071128<br />**Nummer**:<br />-2147020504|Diese Ansicht wird nur offline im Rastermodus unterstützt. Dies wird offline im Kalendermodus nicht unterstützt.|
> |**Name**:<br />VirtualEntitiesNotSupported<br />**Hex**:<br />80073020<br />**Nummer**:<br />-2147012576|Virtuellen Entitäten werden nicht unterstützt.|
> |**Name**:<br />VirtualEntityFailure<br />**Hex**:<br />80050263<br />**Nummer**:<br />-2147155357|Vorgang der virtuellen Entität ist fehlgeschlagen.|
> |**Name**:<br />VirtualEntityFCBOFF<br />**Hex**:<br />80081113<br />**Nummer**:<br />-2146954989|Die Funktion „Bit für virtuelle Entität” ist nicht aktiviert.|
> |**Name**:<br />VirtualEntityNotSupportedInMobileOffline<br />**Hex**:<br />80044821<br />**Nummer**:<br />-2147203039|Entität {0} ist eine virtuelle Entität, die in Mobile offline nicht zur Verfügung steht.|
> |**Name**:<br />VisualizationModuleNotFound<br />**Hex**:<br />8004E012<br />**Nummer**:<br />-2147164142|Kein Visualisierungsmodul mit dem angegebenen Namen gefunden.|
> |**Name**:<br />VisualizationOtcNotFoundError<br />**Hex**:<br />8004E015<br />**Nummer**:<br />-2147164139|Objekttypcode wird für die Visualisierung angegeben.|
> |**Name**:<br />VisualizationRenderingError<br />**Hex**:<br />8004E00E<br />**Nummer**:<br />-2147164146|Fehler beim Rendern des Diagramms.|
> |**Name**:<br />WebhooksHttpRequestTimedOut<br />**Hex**:<br />80050202<br />**Nummer**:<br />-2147155454|Der Webhook-Aufruf ist fehlgeschlagen, weil bei der HTTP-Anforderung ein Timout auf Client-Seite aufgetreten ist. Überprüfen Sie Ihren Webhook-Anforderungshandler.|
> |**Name**:<br />WebhooksInvalidHttpHeaders<br />**Hex**:<br />80050203<br />**Nummer**:<br />-2147155453|Der Webhook-Aufruf ist aufgrund ungültiger HTTP-Kopfzeilen in authValue fehlgeschlagen. Überprüfen Sie, ob das authValue-Format, Überschriftennamen und Werte für Ihre Service-Endpunkt-Entität gültig sind.|
> |**Name**:<br />WebhooksInvalidHttpQueryParams<br />**Hex**:<br />80050204<br />**Nummer**:<br />-2147155452|Der Webhook-Aufruf ist aufgrund ungültiger HTTP-Abfrageparameter in authValue fehlgeschlagen. Überprüfen Sie, ob das authValue-Format, Abfrageparameternamen und Werte für Ihre Service-Endpunkt-Entität gültig sind.|
> |**Name**:<br />WebhooksMaxSizeExceeded<br />**Hex**:<br />80050207<br />**Nummer**:<br />-2147155449|Der Webhook-Aufruf ist fehlgeschlagen, weil die HTTP-Anforderungsnutzlast die maximal erlaubte Größe überschritten hat. Bitte reduzieren Sie Ihre Anforderungsgröße und versuchen Sie es noch einmal.|
> |**Name**:<br />WebhooksNonSuccessHttpResponse<br />**Hex**:<br />80050201<br />**Nummer**:<br />-2147155455|Der Webhook-Aufruf ist fehlgeschlagen, weil die HTTP-Anforderung einen nicht erfolgreichen httpStatus-Code empfangen hat. Überprüfen Sie Ihren Webhook-Anforderungshandler.|
> |**Name**:<br />WebhooksPostDisabled<br />**Hex**:<br />80050206<br />**Nummer**:<br />-2147155450|Die Webhook-Nachricht ist für die Organisation deaktiviert.|
> |**Name**:<br />WebhooksPostRequestFailed<br />**Hex**:<br />80050205<br />**Nummer**:<br />-2147155451|Der Webhook-Aufruf ist während der HTTP-Nachricht fehlgeschlagen. Überprüfen Sie die Ausnahme, um weitere Informationen zu erhalten.|
> |**Name**:<br />WebResourceContentSizeExceeded<br />**Hex**:<br />8004F114<br />**Nummer**:<br />-2147159788|Webresourcen-Inhalt der Webressource ist zu groß.|
> |**Name**:<br />WebResourceDuplicateName<br />**Hex**:<br />8004F115<br />**Nummer**:<br />-2147159787|Eine Webressource mit demselben Namen ist bereits vorhanden. Verwenden Sie einen anderen Namen.|
> |**Name**:<br />WebResourceEmptyName<br />**Hex**:<br />8004F116<br />**Nummer**:<br />-2147159786|Der Name der Webressource darf nicht NULL oder leer sein.|
> |**Name**:<br />WebResourceEmptySilverlightVersion<br />**Hex**:<br />8004F112<br />**Nummer**:<br />-2147159790|Die Silverlight-Version darf bei Silverlight-Webressourcen nicht leer sein.|
> |**Name**:<br />WebResourceImportError<br />**Hex**:<br />8004F11B<br />**Nummer**:<br />-2147159781|Fehler beim Importieren einer Webressource. Versuchen Sie diese Lösung erneut zu importieren. Weitere Unterstützung erhalten Sie vom technischen Support für Microsoft Dynamics 365.|
> |**Name**:<br />WebResourceImportMissingFile<br />**Hex**:<br />8004F11A<br />**Nummer**:<br />-2147159782|Die Datei für diese Webressource ist in der Lösungsdatei nicht vorhanden.|
> |**Name**:<br />WebResourceInvalidSilverlightVersion<br />**Hex**:<br />8004F113<br />**Nummer**:<br />-2147159789|Die Silverlight-Version muss im Format xx.xx[.xx.xx] angegeben werden.|
> |**Name**:<br />WebResourceInvalidType<br />**Hex**:<br />8004F111<br />**Nummer**:<br />-2147159791|Ein ungültiger Webressourcentyp wurde angegeben.|
> |**Name**:<br />WebResourceNameInvalidCharacters<br />**Hex**:<br />8004F117<br />**Nummer**:<br />-2147159785|Webressourcennamen dürfen nur Buchstaben, Zahlen, Punkte und einzelne Schrägstriche enthalten.|
> |**Name**:<br />WebResourceNameInvalidFileExtension<br />**Hex**:<br />8004F119<br />**Nummer**:<br />-2147159783|Eine Webressource darf keine der folgenden Dateierweiterungen besitzen: "ASPX", "ASCX", "ASMX" oder "ASHX".|
> |**Name**:<br />WebResourceNameInvalidPrefix<br />**Hex**:<br />8004F118<br />**Nummer**:<br />-2147159784|Der Name der Webressource enthält kein gültiges Präfix.|
> |**Name**:<br />WopiApplicationUrl<br />**Hex**:<br />80060802<br />**Nummer**:<br />-2147088382|Fehler beim Abruf von Informationen von der WOPI-Anwendungs-URL.|
> |**Name**:<br />WopiDiscoveryFailed<br />**Hex**:<br />80060800<br />**Nummer**:<br />-2147088384|Anforderung zum Abrufen der WOPI-Discovery XML ist fehlgeschlagen.|
> |**Name**:<br />WopiMaxFileSizeExceeded<br />**Hex**:<br />80060803<br />**Nummer**:<br />-2147088381|{0} Datei überstieg die Größenbeschränkung von {1}.|
> |**Name**:<br />WordTemplateFeatureNotEnabled<br />**Hex**:<br />800608DB<br />**Nummer**:<br />-2147088165|Die Dokumentvorlagefunktion ist nicht aktiviert.|
> |**Name**:<br />WorkflowActivityNotSupported<br />**Hex**:<br />80045045<br />**Nummer**:<br />-2147200955|Dieser Workflow kann nicht erstellt, aktualisiert oder veröffentlicht werden, da er auf einen nicht unterstützten Workflowschritt verweist.|
> |**Name**:<br />WorkflowAutomaticallyDeactivated<br />**Hex**:<br />80045042<br />**Nummer**:<br />-2147200958|Die ursprüngliche Workflowdefinition wurde deaktiviert oder ersetzt.|
> |**Name**:<br />WorkflowCompileFailure<br />**Hex**:<br />80045001<br />**Nummer**:<br />-2147201023|Ein Fehler ist bei die Zusammenstellung des Workflows aufgetreten.|
> |**Name**:<br />WorkflowConditionIncorrectBinaryOperatorFormation<br />**Hex**:<br />80045011<br />**Nummer**:<br />-2147201007|Falsche Bildung des binären Operators.|
> |**Name**:<br />WorkflowConditionIncorrectUnaryOperatorFormation<br />**Hex**:<br />80045010<br />**Nummer**:<br />-2147201008|Falsche Bildung des unären Operators.|
> |**Name**:<br />WorkflowConditionOperatorNotSupported<br />**Hex**:<br />80045012<br />**Nummer**:<br />-2147201006|Bedingungsoperator wird für den angegebenen Typ nicht unterstützt.|
> |**Name**:<br />WorkflowConditionTypeNotSupport<br />**Hex**:<br />80045013<br />**Nummer**:<br />-2147201005|Ungültiger Typ bei Bedingung angegeben.|
> |**Name**:<br />WorkflowDoesNotExist<br />**Hex**:<br />8006040b<br />**Nummer**:<br />-2147089397|Workflow ist nicht vorhanden.|
> |**Name**:<br />WorkflowExpressionOperatorNotSupported<br />**Hex**:<br />8004502E<br />**Nummer**:<br />-2147200978|Ausdrucksoperator wird für den angegebenen Typ nicht unterstützt.|
> |**Name**:<br />WorkflowIdIsNull<br />**Hex**:<br />80060400<br />**Nummer**:<br />-2147089408|Workflow-ID kann nicht Null sein beim Erstellen von Geschäftsprozessflusskategorie.|
> |**Name**:<br />WorkflowIsNotActive<br />**Hex**:<br />80045055<br />**Nummer**:<br />-2147200939|Der Workflow muss für die Verwendung in einem Aktionsschritt aktiviert sein.|
> |**Name**:<br />WorkflowIsNotOnDemand<br />**Hex**:<br />80045059<br />**Nummer**:<br />-2147200935|Der Workflow muss als bedarfsabhängig gekennzeichnet werden.|
> |**Name**:<br />WorkflowPublishedByNonOwner<br />**Hex**:<br />8004500B<br />**Nummer**:<br />-2147201013|Dieser Workflow kann nur vom Besitzer veröffentlicht oder geschlossen werden.|
> |**Name**:<br />WorkflowPublishNoActivationParameters<br />**Hex**:<br />80045018<br />**Nummer**:<br />-2147201000|Automatischer Workflow kann nicht veröffentlicht werden, wenn keine Aktivierungsparameter angegeben wurden.|
> |**Name**:<br />WorkflowReferencesInvalidActivity<br />**Hex**:<br />80045038<br />**Nummer**:<br />-2147200968|Die Workflowdefinition enthält einen Schritt, der sich auf eine ungültige benutzerdefinierte Aktivität bezieht. Entfernen Sie die ungültige Referenz und versuchen Sie es anschließend erneut.|
> |**Name**:<br />WorkflowSystemPaused<br />**Hex**:<br />80045017<br />**Nummer**:<br />-2147201001|Workflow soll von Systems angehalten werden.|
> |**Name**:<br />WorkflowValidationFailure<br />**Hex**:<br />80045014<br />**Nummer**:<br />-2147201004|Fehler bei der Datenüberprüfung im Workflow.|
> |**Name**:<br />WrongNumberOfBooleanOptions<br />**Hex**:<br />8004431B<br />**Nummer**:<br />-2147204325|Boolesche Attribute müssen genau zwei Optionswerte haben.|
> |**Name**:<br />XamlNotFound<br />**Hex**:<br />80154B4F<br />**Nummer**:<br />-2146088113|Diese Funktion ist im Offlinemodus nicht verfügbar.|
> |**Name**:<br />XlsxExportGeneratingExcelFailed<br />**Hex**:<br />800608C7<br />**Nummer**:<br />-2147088185|Fehler beim Generieren von Excel.|
> |**Name**:<br />XlsxImportColumnHeadersInvalid<br />**Hex**:<br />800608C6<br />**Nummer**:<br />-2147088186|Ungültige Spalten.|
> |**Name**:<br />XlsxImportExcelFailed<br />**Hex**:<br />800608C8<br />**Nummer**:<br />-2147088184|Fehler beim Importieren von Daten.|
> |**Name**:<br />XlsxImportHiddenColumnAbsent<br />**Hex**:<br />800608C4<br />**Nummer**:<br />-2147088188|Erforderliche Spalten fehlen.|
> |**Name**:<br />XlsxImportInvalidColumnCount<br />**Hex**:<br />800608C5<br />**Nummer**:<br />-2147088187|Konflikt bei Spalten.|
> |**Name**:<br />XlsxImportInvalidExcelDocument<br />**Hex**:<br />800608C2<br />**Nummer**:<br />-2147088190|Ungültige zu importierende Datei.|
> |**Name**:<br />XlsxImportInvalidFileData<br />**Hex**:<br />800608C3<br />**Nummer**:<br />-2147088189|Ungültiges Format in Importdatei|
> |**Name**:<br />YammerAuthTimedOut<br />**Hex**:<br />8005F107<br />**Nummer**:<br />-2147094265|Sie haben zu lange gewartet, um die Yammer-Autorisierung abzuschließen. Bitte wiederholen Sie den Vorgang.|
> |**Name**:<br />YValuesPerPointMeasureMismatch<br />**Hex**:<br />8004E004<br />**Nummer**:<br />-2147164156|Die Anzahl der YValuesPerPoint für Serien und die Anzahl der Kennzahlen für die Kennzahlsammlung sollten identisch sein.|
> |**Name**:<br />ZeroEmailReceived<br />**Hex**:<br />8005E231<br />**Nummer**:<br />-2147098063|Es gibt keine E-Mail-Nachricht, die im Postfach verfügbar ist oder abgerufen werden kann.|
> |**Name**:<br />ZipFileHasMixOfCsvAndXmlFiles<br />**Hex**:<br />80048485<br />**Nummer**:<br />-2147187579|Die ZIP-Datei, die Sie hochladen möchten, enthält mehr als eine Dateiart. Die Datei kann Dateien (.xlsx), durch Trennzeichen getrennte Dateien (CSV-Dateien) Dateien oder XML-Kalkulationstabelle 2003 (XML-Dateien), jedoch kein Kombination von Dateitypen enthalten.|
> |**Name**:<br />ZipInsideZip<br />**Hex**:<br />80048489<br />**Nummer**:<br />-2147187575|Die ZIP-Datei, die Sie hochladen möchten, enthält eine weitere ZIP-Datei.|

### <a name="see-also"></a>Siehe auch

[Behandlung von Ausnahmen in Ihrem Code](handle-exceptions-code.md)