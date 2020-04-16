---
title: RDL Sandboxing | MicrosoftDocs
ms.custom: ''
ms.date: 09/30/2017
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 for Customer Engagement (online)
ms.assetid: 8ec72014-9f0c-4964-ac67-24419b054e91
caps.latest.revision: 13
author: Mattp123
ms.author: matp
manager: annbe
tags:
- MigrationHO
search.audienceType:
- customizer
search.app:
- D365CE
ms.openlocfilehash: d5a74785ed33c8c4591717dc062ac741a8dceb87
ms.sourcegitcommit: 5701e7a755fade6c3bac5c4a5774fcc74627e168
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "3115700"
---
# <a name="rdl-sandboxing"></a>RDL-Sandkasten 

Unter Common Data Service laufen Berichte im Sandbox-Modus. Dies geschieht durch Aktivieren von Report Definition Language (RDL) Sandboxing in SQL Server Reporting Services. Mit dem RDL-Sandboxing können Sie die Verwendung bestimmter Typen von Ressourcen entdecken und beschränken. Infolgedessen sind bestimmte Funktionen in Power Apps modellgetriebenen Apps möglicherweise nicht verfügbar. Weitere Informationen finden Sie unter [MSDN: Aktivieren und Deaktivieren von RDL-Sandkasten](https://msdn.microsoft.com/library/ee210591.aspx).  
  
 Die aktuelle RDL-Sandboxingkonfigurationseinstellungen in Common Data Service werden in den folgenden Abschnitten im vorliegenden Thema beschrieben.  
    
<a name="BKMK_Max"></a>   
## <a name="limits-of-the-array-result-length-and-string-result-length"></a>Beschränkungen der Array-Ergebnislänge und der Zeichenfolgen-Ergebnislänge  
 Die maximale Anzahl der Elemente, die in einem Arrayrückgabewert für einen RDL-Ausdruck zulässig sind, kann von 250 auf 102400 erhöht werden. Die maximale Anzahl der Elemente, die in einem Zeichenfolgenrückgabewert für einen RDL-Ausdruck zulässig sind, wird auch von 250 auf 102400 erhöht. Dadurch können Sie Bilder und Logos mit bis zu 75 KB Größe einschließen, die in einer Datenbank mit Base64-Kodierung gespeichert sind.  
  
 Die MaxResourceSize ist auf 2000 festgelegt. Hiermit können Sie externe Bilder bis zu einer Größe von KB 1500 in einen Bericht einfügen. Mehr Informationen: [TechNet: Hinzufügen eines externen Bildes (Report Builder und SSRS)](https://technet.microsoft.com/library/dd220527.aspx)  
  
<a name="BKMK_Allowed"></a>   
## <a name="allowed-types-and-denied-members"></a>Zulässige Typen und abgelehnte Mitglieder  
 Die RDL-Sandboxingfunktio ermöglicht es Ihnen, eine Liste der zulässigen Dateitypen und eine Liste der verweigerten Mitglieder zu erstellen. Die Liste der zulässigen Typen als Zulassungsliste bezeichnet. Die Liste der verweigerten Mitglieder, die nicht in den RDL-Ausdrücken zulässig sind, wird als Blockierliste bezeichnet.  
  
 Die folgende Tabelle enthält eine Liste der zulässigen Typen und verweigerten Mitglieder, die im Sandboxmodus in Common Data Service verfügbar sind.  
  
|Zulässige Typen|Verweigerte Mitglieder|  
|-------------------|--------------------|  
|`System.Array`|CreateInstance|  
||Fertig stellen|  
||GetType|  
||MemberwiseClone|  
||Größe ändern|  
|||  
|`System.DateTime`|FromBinary|  
||GetDateTimeFormats|  
||GreaterThan|  
||GreaterThanOrEqual|  
|||  
|||  
|`System.Object`|GetType|  
||MemberwiseClone|  
||ReferenceEquals|  
|||  
|`System.DbNull`|Fertig stellen|  
||MemberwiseClone|  
||GetObjectData|  
||GetTypeCode|  
|||  
|`System.Math`|BigMul|  
||DivRem|  
||IEEERemainder|  
||E|  
||PI|  
||Pow|  
|`System.String`||  
|`System.TimeSpan`|Stunden|  
||TicksPerDay|  
||TicksPerHour|  
||TicksPerMillisecond|  
||TicksPerMinute|  
||TicksPerSecond|  
||Null|  
||TryParse|  
||TryParseExact|  
|`System.Convert`|ChangeType|  
||IConvertible.ToBoolean|  
||IConvertible.ToByte|  
||IConvertible.ToChar|  
||IConvertible.ToDateTime|  
||IConvertible.ToDecimal|  
||IConvertible.ToDouble|  
||IConvertible.ToInt16|  
||IConvertible.ToInt32|  
||IConvertible.ToInt64|  
||IConvertible.ToSByte|  
||IConvertible.ToSingle|  
||IConvertible.ToType|  
||IConvertible.ToUInt16|  
||IConvertible.ToUInt32|  
||IConvertible.ToUInt64|  
|`System.StringComparer`|Erstellen|  
||Fertig stellen|  
|||  
|`System.TimeZone`|Fertig stellen|  
||GetType|  
||MemberwiseClone|  
|||  
|`System.Uri`|Unescape|  
||Analysieren|  
||ESC|  
||Fertig stellen|  
|||  
|`System.UriBuilder`|Fertig stellen|  
|||  
|`System.Globalization.CultureInfo`|ClearCachedData|  
|||  
|`System.Text.RegularExpressions.Match`|Leer|  
||NextMatch|  
||Ergebnis|  
||Synchronisiert|  
|||  
|||  
|`System.Text.RegularExpressions.Regex`|CacheSize|  
||CompileToAssembly|  
||GetGroupNames|  
||GetGroupNumbers|  
||GetHashCode|  
||Unescape|  
||UseOptionC|  
||UseOptionR|  
||Eigenschaftsnamen|  
||Großbuchstaben|  
||capsize|  
||capslist|  
||roptions|  
||pattern|  
||factory|  
||IsMatch|  
||Matches|  
||Iserializable.GetObjectData|  
||InitializeReferences|  
||RightToLeft|  
||Optionen|  
|||  
|||  
|`Microsoft.VisualBasic.Constants`|vbAbort|  
||vbAbortRetryIgnore|  
||vbApplicationModal|  
||vbArchive|  
||vbBinaryCompare|  
||vbCancel|  
||vbCritical|  
||vbDefaultButton1|  
||vbDefaultButton2|  
||vbDefaultButton3|  
||vbExclamation|  
||vbFormFeed|  
||vbGet|  
||vbHidden|  
||vbHide|  
||vbHiragana|  
||vbIgnore|  
||vbInformation|  
||vbKatakana|  
||vbLet|  
||VbLinguisticCasing|  
||vbMaximizedFocus|  
||vbMinimizedFocus|  
||vbMinimizedNoFocus|  
||vbMsgBoxHelp|  
||vbMsgBoxRight|  
||VbMsgBoxRtlReading|  
||vbMsgBoxSetForeground|  
||vbNo|  
||vbNormal|  
||vbNormalFocus|  
||vbNormalNoFocus|  
||vbObjectError|  
||vbOK|  
||vbOKCancel|  
||vbOKOnly|  
||vbQuestion|  
||vbReadOnly|  
||vbRetry|  
||vbRetryCancel|  
||vbSet|  
||vbSystem|  
||vbSystemModal|  
||VbTypeName|  
||vbVolume|  
||Null|  
|`Microsoft.VisualBasic.ControlChars`|Fertig stellen|  
||GetType|  
||MemberwiseClone|  
|||  
|`Microsoft.VisualBasic.Conversion`|Err|  
||ErrorToString|  
||Fix|  
|||  
|`Microsoft.VisualBasic.DateInterval`|Fertig stellen|  
||GetType|  
||MemberwiseClone|  
|||  
|`Microsoft.VisualBasic.Financial`|Fertig stellen|  
||GetType|  
||MemberwiseClone|  
||IRR|  
||NPV|  
||MIRR|  
|||  
|||  
|`Microsoft.VisualBasic.Interaction`|AppActivate|  
||Signalton|  
||CallByName|  
||Befehl|  
||CreateObject|  
||Environ|  
||Fertig stellen|  
||GetAllSettings|  
||GetObject|  
||GetSetting|  
||GetType|  
||InputBox|  
||MemberwiseClone|  
||MsgBox|  
||SaveSetting|  
||Shell|  
||Auswählen|  
||Wechseln|  
|||  
|||  
|`Microsoft.VisualBasic.Information`|Erl|  
||Err|  
||IsError|  
||IsDBNull|  
||Lbound|  
||Ubound|  
||SystemTypeName|  
|||  
|`Microsoft.VisualBasic.Strings`|Fertig stellen|  
||GetType|  
||MemberwiseClone|  
||Lset|  
||Rset|  
|||  
|`Microsoft.Crm.Reporting.RdlHelper`||  
  
<a name="BKMK_Denied"></a>   
## <a name="common-denied-members"></a>Häufig verweigerte Mitglieder  
 Die folgende Tabelle enthält eine Liste mit den verweigerten Mitgliedern, die in zulässigen Typen häufig sind:  
  
||  
|-|  
|DateString|  
|Dauer|  
|Equality|  
|gleich|  
|Erl|  
|Filter|  
|GetChar|  
|GroupNameFromNumber|  
|GroupNumberFromName|  
|Int|  
|MaxValue|  
|MinValue|  
|Negate|  
|Zeitgeber|  
|TimeString|  
|ToBinary|  
|Fertig stellen|  
|GetType|  
|MemberwiseClone|  
  

